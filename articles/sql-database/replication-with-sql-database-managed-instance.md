---
title: Configuración de la replicación con Instancia administrada de Azure SQL Database | Microsoft Docs
description: Más información sobre cómo configurar la replicación transaccional en Instancia administrada de Azure SQL Database
services: sql-database
ms.service: sql-database
ms.subservice: data-movement
ms.custom: ''
ms.devlang: ''
ms.topic: howto
author: allenwux
ms.author: xiwu
ms.reviewer: mathoma
manager: craigg
ms.date: 01/25/2019
ms.openlocfilehash: b0188a0983ea18490f3997b857386e313daa58ed
ms.sourcegitcommit: 698a3d3c7e0cc48f784a7e8f081928888712f34b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/31/2019
ms.locfileid: "55467670"
---
# <a name="configure-replication-in-azure-sql-database-managed-instance"></a>Configuración de la replicación con Instancia administrada de Azure SQL Database

La replicación transaccional le permite replicar datos de las bases de datos de SQL Server o Instancia administrada de Azure SQL Database en la Instancia administrada, así como insertar los cambios realizados en las bases de datos de Instancia administrada en otra instancia de SQL Server, base de datos única o grupo elástico de SQL Database, u otra Instancia administrada. La replicación está disponible en su versión preliminar pública en [Instancia administrada de Azure SQL Database](sql-database-managed-instance.md). Una Instancia administrada puede hospedar las bases de datos del publicador, distribuidor y suscriptor. Consulte [Transactional replication configurations](sql-database-managed-instance-transactional-replication.md#common-configurations) (Configuraciones de replicación transaccional) para ver las configuraciones disponibles.

## <a name="requirements"></a>Requisitos

Se requiere el publicador y el distribuidor en Azure SQL Database:

- Instancia administrada de Azure SQL Database no debe estar en la configuración de recuperación ante desastres geográfica.

   >[!NOTE]
   >Las bases de datos de SQL Azure Database que no están configuradas con Instancia administrada solo pueden ser suscriptores.

- Todas las instancias de SQL Server deben estar en la misma red virtual.

- La conectividad usa la autenticación de SQL entre los participantes de la replicación.

- Un recurso compartido de cuenta de Azure Storage para el directorio de trabajo de replicación.

- El puerto 445 (salida TCP) debe estar abierto en las reglas de seguridad de la subred de Instancia administrada para obtener acceso al recurso compartido de archivos de Azure

## <a name="features"></a>Características

Admite:

- Mezcla de replicación de instantáneas y transaccional de instancias locales y de Instancia administrada de Azure SQL Database.

- Los suscriptores pueden ser bases de datos únicas y locales de Azure SQL Database, o bases de datos agrupadas en grupos elásticos de Azure SQL Database.

- Replicación unidireccional o bidireccional.

No se admiten las siguientes características:

- Suscripciones actualizables.

- Replicación geográfica activa.

## <a name="configure-publishing-and-distribution-example"></a>Configuración del ejemplo de publicación y distribución

1. [Cree una Instancia administrada de Azure SQL Database](sql-database-managed-instance-create-tutorial-portal.md) en el portal.
2. [Cree una cuenta de Azure Storage](https://docs.microsoft.com/azure/storage/common/storage-create-storage-account#create-a-storage-account) para el directorio de trabajo.

   Asegúrese de copiar las claves de almacenamiento. Consulte [Visualización y copia de las claves de acceso de almacenamiento](../storage/common/storage-account-manage.md#access-keys
).
3. Cree una base de datos para el publicador.

   En los scripts de ejemplo siguientes, reemplace `<Publishing_DB>` por el nombre de esta base de datos.

4. Cree un usuario de base de datos con autenticación de SQL para el distribuidor. Utilice una contraseña segura.

   En los scripts de ejemplo siguientes, use `<SQL_USER>` y `<PASSWORD>` con el usuario y la contraseña de la base de datos de esta cuenta de SQL Server.

5. [Conéctese a Instancia administrada de Azure SQL Database](sql-database-connect-query-ssms.md).

6. Ejecute la consulta siguiente para agregar el distribuidor y la base de datos de distribución.

   ```sql
   USE [master]
   GO
   EXEC sp_adddistributor @distributor = @@ServerName;
   EXEC sp_adddistributiondb @database = N'distribution';
   ```

7. Para configurar un editor para usar una base de datos de distribución especificada, actualice y ejecute la siguiente consulta.

   Reemplace `<SQL_USER>` y `<PASSWORD>` por la cuenta y la contraseña de SQL Server.

   Reemplace `\\<STORAGE_ACCOUNT>.file.core.windows.net\<SHARE>` por el valor de la cuenta de almacenamiento.  

   Reemplace `<STORAGE_CONNECTION_STRING>` por la cadena de conexión de la pestaña **Claves de acceso** de la cuenta de almacenamiento de Microsoft Azure.

   Después de actualizar la consulta siguiente, ejecútela.

   ```sql
   USE [master]
   EXEC sp_adddistpublisher @publisher = @@ServerName,
                @distribution_db = N'distribution',
                @security_mode = 0,
                @login = N'<SQL_USER>',
                @password = N'<PASSWORD>',
                @working_directory = N'\\<STORAGE_ACCOUNT>.file.core.windows.net\<SHARE>',
                @storage_connection_string = N'<STORAGE_CONNECTION_STRING>';
   GO
   ```

8. Configure el publicador de la replicación.

    En la siguiente consulta, reemplace `<Publishing_DB>` por el nombre de la base de datos del publicador.

    Reemplace `<Publication_Name>` por el nombre para la publicación.

    Reemplace `<SQL_USER>` y `<PASSWORD>` por la cuenta y la contraseña de SQL Server.

    Después de actualizar la consulta, ejecútela para crear la publicación.

   ```sql
   USE [<Publishing_DB>]
   EXEC sp_replicationdboption @dbname = N'<Publishing_DB>',
                @optname = N'publish',
                @value = N'true';

   EXEC sp_addpublication @publication = N'<Publication_Name>',
                @status = N'active';

   EXEC sp_changelogreader_agent @publisher_security_mode = 0,
                @publisher_login = N'<SQL_USER>',
                @publisher_password = N'<PASSWORD>',
                @job_login = N'<SQL_USER>',
                @job_password = N'<PASSWORD>';

   EXEC sp_addpublication_snapshot @publication = N'<Publication_Name>',
                @frequency_type = 1,
                @publisher_security_mode = 0,
                @publisher_login = N'<SQL_USER>',
                @publisher_password = N'<PASSWORD>',
                @job_login = N'<SQL_USER>',
                @job_password = N'<PASSWORD>'
   ```

9. Agregue el artículo, la suscripción y el agente de la suscripción de inserción.

   Para agregar estos objetos, actualice el script siguiente.

   - Reemplace `<Object_Name>` por el nombre del objeto de publicación.
   - Reemplace `<Object_Schema>` por el nombre del esquema de origen.
   - Reemplace los otros parámetros entre corchetes angulares `<>` para que coincidan con los valores de los scripts anteriores.

   ```sql
   EXEC sp_addarticle @publication = N'<Publication_Name>',
                @type = N'logbased',
                @article = N'<Object_Name>',
                @source_object = N'<Object_Name>',
                @source_owner = N'<Object_Schema>'

   EXEC sp_addsubscription @publication = N'<Publication_Name>',
                @subscriber = @@ServerName,
                @destination_db = N'<Subscribing_DB>',
                @subscription_type = N'Push'

   EXEC sp_addpushsubscription_agent @publication = N'<Publication_Name>',
                @subscriber = @@ServerName,
                @subscriber_db = N'<Subscribing_DB>',
                @subscriber_security_mode = 0,
                @subscriber_login = N'<SQL_USER>',
                @subscriber_password = N'<PASSWORD>',
                @job_login = N'<SQL_USER>',
                @job_password = N'<PASSWORD>'
   GO
   ```
   
## <a name="see-also"></a>Otras referencias

- [Replicación transaccional](sql-database-managed-instance-transactional-replication.md)
- [¿Qué es la Instancia administrada?](sql-database-managed-instance.md)
