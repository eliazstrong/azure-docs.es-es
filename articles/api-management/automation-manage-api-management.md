---
title: Administración de Azure API Management mediante Azure Automation
description: Obtenga información acerca de cómo puede usarse el servicio de Azure Automation para administrar Azure API Management.
services: api-management, automation
documentationcenter: ''
author: vladvino
manager: eamono
editor: ''
ms.assetid: 2e53c9af-f738-47f8-b1b6-593050a7c51b
ms.service: api-management
ms.workload: mobile
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 02/13/2018
ms.author: apimpm
ms.openlocfilehash: c2c23b6709552d053ca8db5e32a045b416c1acfc
ms.sourcegitcommit: 3aa0fbfdde618656d66edf7e469e543c2aa29a57
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/05/2019
ms.locfileid: "55733423"
---
# <a name="managing-azure-api-management-using-azure-automation"></a>Administración de Azure API Management mediante Azure Automation
Esta guía presenta el servicio Azure Automation y cómo se puede usar para simplificar la administración de Azure API Management.

## <a name="what-is-azure-automation"></a>¿Qué es Azure Automation?
[Azure Automation](https://azure.microsoft.com/services/automation/) es un servicio de Azure para simplificar la administración en la nube mediante la automatización de procesos. Mediante Azure Automation, se pueden automatizar las tareas de ejecución prolongada, manuales, propensas a errores y que se repiten para aumentar la confiabilidad, la eficiencia y el valioso tiempo para su organización.

Azure Automation proporciona un motor de ejecución de flujo de trabajo altamente confiable y de alta disponibilidad que se adapta para satisfacer sus necesidades. En Azure Automation, los sistemas de terceros pueden interrumpir los procesos manualmente o en intervalos programados para que las tareas se realicen justo cuando sea necesario.

Reduzca la sobrecarga operativa y libere al personal de TI/DevOps para concentrarse en el trabajo que proporciona valor al negocio trasladando las tareas de administración en la nube para que se ejecuten automáticamente mediante Azure Automation.

## <a name="how-can-azure-automation-help-manage-azure-api-management"></a>¿Cómo puede ayudar Azure Automation a administrar Azure API Management?
API Management se puede administrar en Azure Automation mediante el uso de [cmdlets de Windows PowerShell para la API de Azure API Management](https://docs.microsoft.com/powershell/module/azurerm.apimanagement/?view=azurermps-5.5.0). En Azure Automation, puede escribir scripts de flujo de trabajo de PowerShell para llevar a cabo muchas de las tareas de API Management con los cmdlets. También puede emparejar estos cmdlets en Azure Automation con los cmdlets para otros servicios de Azure, para automatizar tareas complejas a través de los servicios de Azure y sistemas de terceros.

Estos son algunos ejemplos del uso de API Management con PowerShell:

* [Ejemplos de Azure PowerShell para API Management](https://docs.microsoft.com/azure/api-management/powershell-samples)

## <a name="next-steps"></a>Pasos siguientes
Ahora que ha aprendido los aspectos básicos de Azure Automation y cómo se puede usar para administrar Azure API Management, siga estos vínculos para obtener más información.

* Consulte el [tutorial de introducción](../automation/automation-first-runbook-graphical.md) de Azure Automation.

