---
title: Habilitación del registro de diagnóstico en Azure Traffic Manager
description: Aprenda a habilitar el registro de diagnóstico para su perfil de Traffic Manager y acceda a los archivos de registro que se crean como resultado.
services: traffic-manager
author: KumudD
manager: twooley
ms.service: traffic-manager
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: infrastructure-services
ms.date: 01/25/2019
ms.author: kumud
ms.openlocfilehash: abdc50d6d3d27ab7611994089345a997afc72cae
ms.sourcegitcommit: 58dc0d48ab4403eb64201ff231af3ddfa8412331
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2019
ms.locfileid: "55082647"
---
# <a name="enable-diagnostic-logging-in-azure-traffic-manager"></a>Habilitación del registro de diagnóstico en Azure Traffic Manager

En este artículo se describe cómo habilitar el registro de diagnóstico y acceder a los datos de registro para un perfil de Traffic Manager.

Los registros de diagnóstico de Azure Traffic Manager pueden proporcionar conclusiones sobre el comportamiento del recurso del perfil de Traffic Manager. Por ejemplo, puede usar los datos de registro del perfil para determinar porqué determinados sondeos han agotado el tiempo de espera en un punto de conexión.

## <a name="enable-diagnostic-logging"></a>Activación del registro de diagnóstico

Puede ejecutar los comandos siguientes en [Azure Cloud Shell](https://shell.azure.com/powershell), o mediante la ejecución de PowerShell en el equipo. Azure Cloud Shell es un shell interactivo gratuito. Tiene las herramientas comunes de Azure preinstaladas y configuradas para usarlas en la cuenta. Si ejecuta PowerShell desde el equipo, necesita el módulo *AzureRM* de PowerShell, versión 6.13.1 o posterior. Puede ejecutar `Get-Module -ListAvailable AzureRM` para encontrar la versión instalada. Si necesita instalarla o actualizarla, consulte el artículo sobre [cómo instalar el módulo de Azure PowerShell](/powershell/azure/azurerm/install-azurerm-ps). Si ejecuta PowerShell localmente, también debe ejecutar `Login-AzureRmAccount` para iniciar sesión en Azure.

1. **Recupere el perfil de Traffic Manager:**

    Para habilitar el registro de diagnóstico, necesita el identificador de un perfil de Traffic Manager. Recupere el perfil de Traffic Manager para el que quiere habilitar el registro de diagnóstico con [Get-AzureRmTrafficManagerProfile](/powershell/module/AzureRM.TrafficManager/Get-AzureRmTrafficManagerProfile). La salida incluye la información del identificador del perfil de Traffic Manager.

    ```azurepowershell-interactive
    Get-AzureRmTrafficManagerProfile -Name <TrafficManagerprofilename> -ResourceGroupName <resourcegroupname>
    ```

2. **Habilite el registro de diagnóstico para el perfil de Traffic Manager:**

    Habilite el registro de diagnóstico para el perfil de Traffic Manager con el identificador obtenido en el paso anterior con [Set-AzureRmDiagnosticSetting](https://docs.microsoft.com/powershell/module/azurerm.insights/set-azurermdiagnosticsetting?view=latest). El comando siguiente almacena los registros detallados del perfil de Traffic Manager en una cuenta de Azure Storage especificada. 

      ```azurepowershell-interactive
    Set-AzureRmDiagnosticSetting -ResourceId <TrafficManagerprofileResourceId> -StorageAccountId <storageAccountId> -Enabled $true
      ``` 
3. **Compruebe la configuración de diagnóstico:**

      Compruebe la configuración de diagnóstico del perfil de Traffic Manager mediante [Get-AzureRmDiagnosticSetting](https://docs.microsoft.com/powershell/module/azurerm.insights/get-azurermdiagnosticsetting?view=latest). El siguiente comando muestra las categorías que se registran para un recurso.

     ```azurepowershell-interactive
     Get-AzureRmDiagnosticSetting -ResourceId <TrafficManagerprofileResourceId>
     ```  
      Asegúrese de que todas las categorías de registro asociadas con el recurso del perfil de Traffic Manager se muestran como habilitadas. También, compruebe que la cuenta de almacenamiento está configurada correctamente.

## <a name="access-log-files"></a>Acceso a los archivos de registro
1. Inicie sesión en el [Azure Portal](https://portal.azure.com). 
1. Vaya a la cuenta de Azure Storage en el portal.
2. En la página **Información general** de su cuenta de Azure Storage, en **Servicios**, seleccione **Blobs**.
3. En **Contenedores**, seleccione **insights-logs-probehealthstatusevents** y vaya al archivo PT1H.json y haga clic en **Descargar** para descargar y guardar una copia de este archivo de registro.

    ![Acceso a los archivos de registro del perfil de Traffic Manager desde un almacenamiento de blobs](./media/traffic-manager-logs/traffic-manager-logs.png)


## <a name="traffic-manager-log-schema"></a>Esquema de registro de Traffic Manager

Todos los registros de diagnóstico disponibles a través de Azure Monitor comparten un esquema común de nivel superior, con flexibilidad para que cada servicio emita propiedades únicas para sus propios eventos. Para ver el esquema de registros de diagnóstico de nivel superior, consulte [Supported services, schemas, and categories for Azure Diagnostic Logs](../azure-monitor/platform/tutorial-dashboards.md) (Esquemas, categorías y servicios admitidos para registros de diagnóstico de Azure).

En la tabla siguiente se incluye el esquema de registros específico del recurso del perfil de Azure Traffic Manager.

|||||
|----|----|---|---|
|**Nombre del campo**|**Tipo de campo**|**Definición**|**Ejemplo**|
|EndpointName|string|El nombre del punto de conexión de Traffic Manager cuyo mantenimiento se está registrando.|*myPrimaryEndpoint*|
|Status|string|El estado de mantenimiento del punto de conexión de Traffic Manager que se sondeó. El estado puede ser **Up** (Arriba) o **Down** (Abajo).|**Up** (Arriba)|
|||||

## <a name="next-steps"></a>Pasos siguientes

* Más información sobre la [supervisión de Traffic Manager](traffic-manager-monitoring.md)

