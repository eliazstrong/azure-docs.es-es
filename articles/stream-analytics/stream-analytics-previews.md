---
title: Características en vista previa (GB) de Azure Stream Analytics
description: En este artículo se enumeran las características de Azure Stream Analytics que están actualmente en versión preliminar.
services: stream-analytics
author: mamccrea
ms.author: mamccrea
ms.reviewer: jasonh
ms.service: stream-analytics
ms.topic: conceptual
ms.date: 02/05/2019
ms.openlocfilehash: 09f1bdfa4c9a7a179bddf9473b553924bfb58fb7
ms.sourcegitcommit: 415742227ba5c3b089f7909aa16e0d8d5418f7fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/06/2019
ms.locfileid: "55768569"
---
# <a name="azure-stream-analytics-preview-features"></a>Características en vista previa (GB) de Azure Stream Analytics

En este artículo se resumen todas las características actualmente en versión preliminar de Azure Stream Analytics. No se recomienda el uso de características en vista previa en un entorno de producción.

## <a name="public-previews"></a>Versiones preliminares públicas

Las características siguientes se encuentran en la versión preliminar pública. Puede aprovechar las ventajas de estas características hoy mismo, pero no las use en su entorno de producción.

### <a name="sql-database-reference-data"></a>Datos de referencia de SQL Database

Azure Stream Analytics admite Azure SQL Database como origen de la entrada de datos de referencia. Puede usar SQL Database como datos de referencia para su trabajo de Stream Analytics en Azure Portal y en Visual Studio con herramientas de Stream Analytics. Para más información, visite [Use reference data from a SQL Database for an Azure Stream Analytics job](sql-reference-data.md) (Uso de datos de referencia de una instancia de SQL Database para un trabajo de Azure Stream Analytics).

### <a name="integration-with-azure-machine-learning"></a>Integración con Azure Machine Learning

Puede escalar los trabajos de Stream Analytics con las funciones de Machine Learning (ML). Para obtener más información acerca de cómo puede usar las funciones de Machine Learning en un trabajo de Stream Analytics, visite [Escalado del trabajo de Análisis de transmisiones con funciones de Azure Machine Learning](stream-analytics-scale-with-machine-learning-functions.md). Eche un vistazo a un escenario realista con [Análisis de opiniones mediante Azure Stream Analytics y Azure Machine Learning](stream-analytics-machine-learning-integration-tutorial.md).

### <a name="javascript-user-defined-aggregate"></a>Agregado definido por el usuario en JavaScript

Azure Stream Analytics admite agregados definidos por el usuario (UDA) escritos en JavaScript, que le permiten implementar lógica empresarial con estado compleja. Obtenga información sobre cómo usar los UDA en la documentación de [Agregados definidos por el usuario en JavaScript para Azure Stream Analytics](stream-analytics-javascript-user-defined-aggregates.md). 

### <a name="live-data-testing-in-visual-studio"></a>Prueba de datos activos en Visual Studio

Las herramientas de Visual Studio para Azure Stream Analytics mejoran la función de pruebas locales que le permite realizar pruebas en las consultas en comparación con los flujos de datos de eventos activos desde fuentes en la nube como un centro de eventos o un centro de IoT. Aprenda cómo realizar una [Prueba local de datos activos mediante herramientas de Azure Stream Analytics para Visual Studio](stream-analytics-live-data-local-testing.md).

### <a name="net-user-defined-functions-on-iot-edge"></a>Funciones definidas por el usuario de .NET en IoT Edge

Con las funciones definidas por el usuario de . NET Standard, puede ejecutar código de .NET Standard como parte de la canalización de transmisiones de datos. Puede crear clases de C# simples o importar bibliotecas y proyectos completos. Las funciones de creación y depuración completas se admiten en Visual Studio. Para obtener más información, visite [Desarrollar funciones definidas por el usuario de .NET Standard para trabajos perimetrales de Azure Stream Analytics](stream-analytics-edge-csharp-udf-methods.md).

## <a name="private-previews"></a>Versiones preliminares privadas

Las características siguientes se encuentran en la versión preliminar privada.

### <a name="anomaly-detection"></a>Detección de anomalías

Azure Stream Analytics introduce nuevos modelos de aprendizaje automático con compatibilidad para a detección de *picos* y *caídas*, además de detección de tendencias bidireccionales, positivas lentas y negativas lentas.

### <a name="c-custom-deserializer-for-azure-stream-analytics-on-iot-edge"></a>Deserializador personalizado en C# para Azure Stream Analytics en IoT Edge

Los desarrolladores ahora pueden implementar deserializadores personalizados en C# para deserializar los eventos recibidos por Azure Stream Analytics. Parquet, Protobuf, XML y todos los formatos binarios son algunos ejemplos de formatos que se pueden deserializar.

### <a name="managed-identities-for-azure-resource-authentication-to-azure-data-lake-storage"></a>Identidades administradas en la autenticación de recursos de Azure en Azure Data Lake Storage

Ahora puede utilizar las canalizaciones en tiempo real con la autenticación basada en identidades administradas para los recursos de Azure mientras escribe en Azure Data Lake Storage Gen1, lo que permite crear trabajos mediante programación. Para obtener más información, visite [Uso de identidades administradas para autenticar trabajos de Azure Stream Analytics en la salida de Azure Data Lake Storage Gen1](stream-analytics-managed-identities-adls.md).

### <a name="visual-studio-code-for-azure-stream-analytics"></a>Visual Studio Code para Azure Stream Analytics

Los trabajos de Azure Stream Analytics se pueden crear en Visual Studio Code.

## <a name="next-steps"></a>Pasos siguientes

* [Eight new features in Azure Stream Analytics](https://azure.microsoft.com/blog/eight-new-features-in-azure-stream-analytics/) (Ocho nuevas características de Azure Stream Analytics)

* [Four new features now available in Azure Stream Analytics](https://azure.microsoft.com/blog/4-new-features-now-available-in-azure-stream-analytics/) (Cuatro nuevas características disponibles en Azure Stream Analytics)
