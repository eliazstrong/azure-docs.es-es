---
title: Reacción ante eventos de Azure Media Services | Microsoft Docs
description: Use Azure Event Grid para suscribirse a los eventos de Media Services.
services: media-services
documentationcenter: ''
author: Juliako
manager: femila
editor: ''
ms.service: media-services
ms.workload: ''
ms.topic: article
ms.date: 10/16/2018
ms.author: juliako
ms.openlocfilehash: 3541a5b33aa0bb98d9381b51caefc63b6aa677ad
ms.sourcegitcommit: 3a7c1688d1f64ff7f1e68ec4bb799ba8a29a04a8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/17/2018
ms.locfileid: "49377555"
---
# <a name="handling-event-grid-events"></a>Control de eventos de Event Grid

Los eventos de Media Services permiten que las aplicaciones reaccionen a distintos eventos (por ejemplo, el evento de cambio del estado del trabajo) a través de modernas arquitecturas sin servidor. Esto se consigue sin necesidad de código complejo ni de servicios de sondeo costosos e ineficientes. En su lugar, se insertan eventos a través de [Azure Event Grid](https://azure.microsoft.com/services/event-grid/) a los controladores de eventos como [Azure Functions](https://azure.microsoft.com/services/functions/), [Azure Logic Apps](https://azure.microsoft.com/services/logic-apps/) o incluso a su propio webhook y solo se paga por lo que se usa. Para información sobre los precios, consulte [Precios de Event Grid](https://azure.microsoft.com/pricing/details/event-grid/).

La disponibilidad de los eventos de Media Services está asociada a la [disponibilidad](../../event-grid/overview.md) de Event Grid. Estarán disponibles en otras regiones cuando lo esté Event Grid.  

## <a name="available-media-services-events"></a>Eventos disponibles de Media Services

Event Grid usa las [suscripciones a eventos](../../event-grid/concepts.md#event-subscriptions) para enrutar los mensajes de eventos a los suscriptores.  Actualmente, las suscripciones a eventos de Media Services pueden incluir los eventos siguientes:  

|Nombre del evento|DESCRIPCIÓN|
|----------|-----------|
| Microsoft.Media.JobStateChange| Se produce cuando cambia un estado del trabajo. |
| Microsoft.Media.LiveEventConnectionRejected | Se rechazó el intento de conexión del codificador. |
| Microsoft.Media.LiveEventEncoderConnected | El codificador se conectó al evento en directo. |
| Microsoft.Media.LiveEventEncoderDisconnected | El codificador se desconecta. |
| Microsoft.Media.LiveEventIncomingDataChunkDropped | El servidor multimedia elimina el fragmento de datos porque es demasiado tarde o porque tiene una marca de tiempo superpuesta (la marca de tiempo del nuevo fragmento de datos es menor que el tiempo de finalización del fragmento de datos anterior). |
| Microsoft.Media.LiveEventIncomingStreamReceived | El servidor multimedia recibe el primer fragmento de datos de cada pista en la transmisión o la conexión. |
| Microsoft.Media.LiveEventIncomingStreamsOutOfSync | El servidor multimedia detecta que las transmisiones de audio y vídeo no están sincronizadas. Se usa como advertencia porque la experiencia del usuario no se verá afectada. |
| Microsoft.Media.LiveEventIncomingVideoStreamsOutOfSync | El servidor multimedia detecta que cualquiera de las dos transmisiones de vídeo provenientes del codificador externo no está sincronizada. Se usa como advertencia porque la experiencia del usuario no se verá afectada. |
| Microsoft.Media.LiveEventIngestHeartbeat | Se publica cada 20 segundos para cada pista cuando se está ejecutando el evento en directo. Proporciona resumen de mantenimiento de la ingesta. |
| Microsoft.Media.LiveEventTrackDiscontinuityDetected | El servidor multimedia detecta una discontinuidad en la pista entrante. |

## <a name="event-schema"></a>Esquema de eventos

Los eventos de Media Services contienen toda la información necesaria para responder a cualquier cambio que se produzca en los datos.  Puede identificar un evento de Media Services porque la propiedad eventType comienza por "Microsoft.Media".

Para más información, consulte el artículo sobre los [esquemas de eventos de Media Services](media-services-event-schemas.md).

## <a name="practices-for-consuming-events"></a>Prácticas para consumir eventos

Las aplicaciones que controlan los eventos de Media Services deben seguir algunos procedimientos recomendados:

* Dado que se pueden configurar varias suscripciones para enrutar eventos al mismo controlador de eventos, es importante no asumir que los eventos provienen de un origen determinado, sino comprobar el tema del mensaje para asegurarse de que proviene de la cuenta de almacenamiento esperable.
* De igual forma, compruebe que eventType es uno de los que está preparado para procesar y no asuma que todos los eventos que reciba van a ser los tipos que espera.
* Ignore los campos que no comprenda.  Esta práctica le ayudará a mantenerse resistente a las nuevas características que puedan agregarse en el futuro.
* Use las coincidencias de prefijo y sufijo "subject" para limitar los eventos a un evento determinado.

## <a name="next-steps"></a>Pasos siguientes

[Obtención de eventos de estado del trabajo](job-state-events-cli-how-to.md)
