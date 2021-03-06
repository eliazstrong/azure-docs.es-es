---
title: Azure SQL Data Warehouse Gen2 admite niveles de proceso inferiores | Microsoft Docs
description: Azure SQL Data Warehouse Gen2 ahora admite niveles de proceso inferiores
author: antvgski
manager: craigg
ms.service: sql-data-warehouse
ms.topic: conceptual
ms.subservice: design
ms.date: 12/03/2018
ms.author: anvang
ms.reviewer: igorstan
ms.openlocfilehash: 22993395d60df23533b67ec48d0ea7f979d73e22
ms.sourcegitcommit: a65b424bdfa019a42f36f1ce7eee9844e493f293
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2019
ms.locfileid: "55692469"
---
# <a name="azure-sql-data-warehouse-gen2-support-for-lower-compute-tiers"></a>Azure SQL Data Warehouse Gen2 admite niveles de proceso inferiores

Microsoft ayuda a reducir el costo de nivel de entrada de la ejecución de un almacén de datos capaz de manejar exigentes consultas mediante la adición de niveles inferiores de proceso para el servicio ultrarrápido Azure SQL Data Warehouse Gen2. Los clientes pueden experimentar las principales características de rendimiento, flexibilidad y seguridad de Azure SQL Data Warehouse desde 100 cDWU (unidades de almacenamiento de datos) y escalar a 30 000 cDWU en cuestión de minutos. Los clientes pueden beneficiarse del rendimiento y la flexibilidad de Gen2 con niveles de proceso inferiores. 

Al eliminar el punto de entrada para el almacenamiento de datos de próxima generación, Microsoft abre las puertas a los clientes que desean evaluar todos los beneficios de un almacenamiento de datos seguro y de alto rendimiento sin tener que adivinar cuál es el mejor entorno de pruebas para ellos.  Los clientes podrán comenzar desde 100 cDWU, por debajo del punto de entrada actual de 500 cDWU.  SQL Data Warehouse Gen2 sigue admitiendo las operaciones de pausa y reanudación y va más allá de la flexibilidad en el proceso.  Gen2 también admite la capacidad de almacenamiento ilimitado de almacén de columnas junto con 2,5 veces más memoria por consulta, hasta 128 consultas simultáneas y características de almacenamiento en caché adaptativo, aportando experiencias con un rendimiento cinco veces mayor en comparación con la misma unidad de almacenamiento de datos de Gen1 por el mismo precio.  Las copias de seguridad con redundancia geográfica son estándar para Gen2 con protección de datos garantizada integrada. Azure SQL Data Warehouse Gen2 está listo para escalar cuando lo esté el usuario.

El portal actualmente no admite la implementación o el escalado de instancias de Gen2 de nivel inferior. Estamos trabajando duro para habilitar esta funcionalidad; mientras tanto, [envíe una incidencia](sql-data-warehouse-get-started-create-support-ticket.md) si desea aprovechar las ventajas de este nuevo nivel.

## <a name="getting-started-with-azure-sql-data-warehouse-gen2"></a>Introducción a Azure SQL Data Warehouse Gen2 

Los clientes pueden elegir implementar una nueva instancia de Gen2 o actualizar una instancia existente de almacenamiento de datos de Gen1 para experimentar la flexibilidad y el rendimiento de almacenamiento de datos de próxima generación. 

Pruebe el [nivel Gen2 optimizado para proceso de Azure SQL Data Warehouse](https://azure.microsoft.com/services/sql-data-warehouse/?v=17.44).
Actualice [Gen1 optimizado para proceso de Azure SQL Data Warehouse a Gen2](https://docs.microsoft.com/azure/sql-data-warehouse/upgrade-to-latest-generation) Vea Azure SQL Data Warehouse Gen2 en acción en este [vídeo de Microsoft Mechanics](https://www.youtube.com/watch?v=Ap8I3UZonzI&feature=youtu.be).


## <a name="supported-regions-for-lower-compute-tiers"></a>Regiones admitidas para niveles de proceso inferiores

- Este de EE. UU. 1 
- Este de EE. UU. 2
- Europa occidental
- Europa del Norte
- Oeste de EE. UU. 2
- Sudeste asiático
- Centro-Sur de EE. UU.
- Centro de EE. UU. 
- Asia oriental
- Este de Japón
- India central
- Este de Australia
- Sudeste de Australia
- Centro de Canadá
- Oeste de Japón 
- Centro de Canadá

## <a name="next-steps"></a>Pasos siguientes

- [Obtenga información](upgrade-to-latest-generation.md) sobre el rendimiento optimizado para proceso con la actualización de SQL Data Warehouse. 
