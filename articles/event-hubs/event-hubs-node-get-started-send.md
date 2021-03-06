---
title: 'Envío de eventos mediante Node.js: Azure Event Hubs | Microsoft Docs'
description: En este artículo se ofrece un tutorial para crear una aplicación de Node.js que envía eventos de Azure Event Hubs.
services: event-hubs
author: ShubhaVijayasarathy
manager: kamalb
ms.service: event-hubs
ms.workload: core
ms.topic: article
ms.custom: seodec18
ms.date: 12/06/2018
ms.author: shvija
ms.openlocfilehash: 7281e6bb2dda5dc3fddb5f39bf271293ebb88a73
ms.sourcegitcommit: 3aa0fbfdde618656d66edf7e469e543c2aa29a57
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/05/2019
ms.locfileid: "55732026"
---
# <a name="send-events-to-azure-event-hubs-using-nodejs"></a>Envío de eventos a Azure Event Hubs mediante Node.js

Azure Event Hubs es una plataforma de streaming de macrodatos y servicio de ingesta de eventos de gran escalabilidad capaz de recibir y procesar millones de eventos por segundo. Event Hubs puede procesar y almacenar eventos, datos o telemetría generados por dispositivos y software distribuido. Los datos enviados a un centro de eventos se pueden transformar y almacenar con cualquier proveedor de análisis en tiempo real o adaptadores de procesamiento por lotes y almacenamiento. Para más información sobre Event Hubs, consulte [Introducción a Event Hubs](event-hubs-about.md) y [Características de Event Hubs](event-hubs-features.md).

En este tutorial se describe cómo enviar eventos a un centro de eventos desde una aplicación escrita en Node.js.

> [!NOTE]
> Puede descargar esta guía de inicio rápido como un ejemplo desde [GitHub](https://github.com/Azure/azure-event-hubs-node/tree/master/client), reemplazar las cadenas `EventHubConnectionString` y `EventHubName` por los valores del centro de eventos, y ejecutarlo. También puede seguir los pasos de este tutorial para crear el suyo propio.

## <a name="prerequisites"></a>Requisitos previos

Para completar este tutorial, debe cumplir los siguientes requisitos previos:

- Node.js versión 8.x y posteriores. Descargue la versión LTS más reciente en [https://nodejs.org](https://nodejs.org).
- Visual Studio Code (recomendado) o cualquier otro IDE

## <a name="create-an-event-hubs-namespace-and-an-event-hub"></a>Creación de un espacio de nombres de Event Hubs y un centro de eventos
El primer paso consiste en usar [Azure Portal](https://portal.azure.com) para crear un espacio de nombres de tipo Event Hubs y obtener las credenciales de administración que la aplicación necesita para comunicarse con el centro de eventos. Para crear un espacio de nombres y un centro de eventos, siga el procedimiento de [este artículo](event-hubs-create.md) y después continúe con los pasos siguientes de este tutorial.

Obtenga la cadena de conexión para el espacio de nombres del centro de eventos siguiendo las instrucciones del artículo: [Obtención de la cadena de conexión](event-hubs-get-connection-string.md#get-connection-string-from-the-portal). Utilizará la cadena de conexión más adelante en el tutorial.

## <a name="clone-the-sample-git-repository"></a>Clonación del repositorio de Git de ejemplo
Clone el repositorio de Git de ejemplo de [GitHub](https://github.com/Azure/azure-event-hubs-node) en la máquina. 

## <a name="install-nodejs-package"></a>Instalación del paquete de Node.js
Instale el paquete de Node.js para Azure Event Hubs en la máquina. 

```shell
npm install @azure/event-hubs
```

## <a name="clone-the-git-repository"></a>Clonación del repositorio de Git
Descargue o clone el [ejemplo](https://github.com/Azure/azure-event-hubs-node/tree/master/client/examples) desde GitHub. 

## <a name="send-events"></a>Envío de eventos
El SDK que clonó contiene varios ejemplos que muestran cómo enviar eventos a un centro de eventos mediante Node.js. En esta guía de inicio rápido, usará el ejemplo **simpleSender.js**. Para observar los eventos que se reciben, abra otro terminal y reciba los eventos con el [ejemplo de recepción](event-hubs-node-get-started-receive.md).

1. Abra el proyecto en Visual Studio Code. 
2. Cree un archivo denominado **.env** bajo la carpeta **client**. Copie y pegue las variables de entorno de ejemplo desde **sample.env** en la carpeta raíz.
3. Configure la cadena de conexión del centro de eventos, el nombre del centro de eventos y el punto de conexión de almacenamiento. Puede copiar la cadena de conexión para el centro de eventos desde la clave **Connection string-primary** en **RootManageSharedAccessKey** en la página del centro de eventos en Azure Portal. Para ver los pasos detallados, consulte [Obtención de la cadena de conexión](event-hubs-create.md#create-an-event-hubs-namespace).
4. En la CLI de Azure, vaya a la ruta de acceso de la carpeta **client**. Instale los paquetes de nodos y compile el proyecto mediante la ejecución de estos comandos:

    ```shell
    npm i
    npm run build
    ```
5. Inicie el envío de eventos mediante la ejecución del siguiente comando: 

    ```shell
    node dist/examples/simpleSender.js
    ```


## <a name="review-the-sample-code"></a>Revisión del código de ejemplo 
Este es el código de ejemplo para enviar eventos a un centro de eventos mediante Node.js. Puede crear manualmente un archivo sampleSender.js y ejecutarlo para enviar eventos a un centro de eventos. 


```javascript
const { EventHubClient, EventPosition } = require('@azure/event-hubs');

const client = EventHubClient.createFromConnectionString(process.env["EVENTHUB_CONNECTION_STRING"], process.env["EVENTHUB_NAME"]);

async function main() {
    // NOTE: For receiving events from Azure Stream Analytics, please send Events to an EventHub where the body is a JSON object/array.
    // const eventData = { body: { "message": "Hello World" } };
    const data = { body: "Hello World 1" };
    const delivery = await client.send(data);
    console.log("message sent successfully.");
}

main().catch((err) => {
    console.log(err);
});

```

Recuerde establecer las variables de entorno antes de ejecutar el script. Puede configurar esto en la línea de comandos tal como se muestra en el ejemplo siguiente, o bien usar el [paquete dotenv](https://www.npmjs.com/package/dotenv#dotenv). 

```shell
// For windows
set EVENTHUB_CONNECTION_STRING="<your-connection-string>"
set EVENTHUB_NAME="<your-event-hub-name>"

// For linux or macos
export EVENTHUB_CONNECTION_STRING="<your-connection-string>"
export EVENTHUB_NAME="<your-event-hub-name>"
```

## <a name="next-steps"></a>Pasos siguientes
En esta guía de inicio rápido, ha enviado mensajes a un centro de eventos mediante Node.js. Para saber cómo recibir eventos de un centro de eventos mediante Node.js, consulte [Recepción de eventos de Azure Event Hubs mediante Node.js](event-hubs-node-get-started-receive.md).

Consulte otros ejemplos de Node.js para Event Hubs en [GitHub](https://github.com/Azure/azure-event-hubs-node/tree/master/client/examples/).
