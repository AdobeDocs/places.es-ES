---
title: Notificaciones push
description: Esta sección muestra cómo utilizar el servicio de Places con notificaciones push.
exl-id: c094fe9c-6148-45ba-850a-f4c520d3362c
TQID: https://experienceleague.adobe.com/aaTMSoOkVUfbPDpPiRm7P3-8d8JSO9N0Ga12Hlmf-go
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: e55547f1-a1ff-40c6-8978-026e40ab7fa4id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2: id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2: id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 229
ht-degree: 14%

---

# Notificaciones push

Mobile Services le permite enviar notificaciones push a segmentos de Adobe Analytics. En Places Service, puede segmentar la audiencia de su mensaje push mediante sus interacciones históricas con los puntos de interés. Por ejemplo, puede enviar un mensaje a los usuarios que hayan estado en una de sus tiendas en los últimos 30 días.

Antes de empezar, asegúrese de haber completado las siguientes tareas:

* Adobe Analytics ha procesado los datos del servicio Places.

  Esto significa que la aplicación móvil ha enviado correctamente los datos del servicio Places a un grupo de informes y que los datos están disponibles para la segmentación.

* El canal de notificaciones push de Mobile Services está configurado.

  Para obtener más información, consulte [Crear un mensaje en la aplicación](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.html?lang=es).

* Obtenga información sobre cómo enviar una notificación push a un segmento de Analytics en Mobile Services.

  Para obtener más información, consulte [Crear un mensaje en la aplicación](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.html?lang=es).

## Enviar una notificación

En la ficha **[!UICONTROL Audiencia]** del flujo de trabajo *Crear notificación push*, puede crear la audiencia para este mensaje de una de las siguientes maneras:

* En la lista desplegable **[!UICONTROL Segmentos de Analytics]**, seleccione un segmento de Adobe Analytics creado anteriormente.

* En la sección **[!UICONTROL Segmento personalizado]**, cree una audiencia utilizando los parámetros de segmento personalizados disponibles.

![configurando un mensaje push](/help/assets/push-set-up.png)
