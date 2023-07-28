---
title: Notificaciones push
description: Esta sección muestra cómo utilizar el servicio de Places con notificaciones push.
exl-id: c094fe9c-6148-45ba-850a-f4c520d3362c
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 8%

---

# Notificaciones push

Mobile Services le permite enviar notificaciones push a segmentos de Adobe Analytics. En Places Service, puede segmentar la audiencia de su mensaje push mediante sus interacciones históricas con los puntos de interés. Por ejemplo, puede enviar un mensaje a los usuarios que hayan estado en una de sus tiendas en los últimos 30 días.

Antes de empezar, asegúrese de haber completado las siguientes tareas:

* Adobe Analytics ha procesado los datos del servicio Places.

  Esto significa que la aplicación móvil ha enviado correctamente los datos del servicio Places a un grupo de informes y que los datos están disponibles para la segmentación.

* El canal de notificaciones push de Mobile Services está configurado.

  Para obtener más información, consulte [Crear un mensaje en la aplicación](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.html).

* Obtenga información sobre cómo enviar una notificación push a un segmento de Analytics en Mobile Services.

  Para obtener más información, consulte [Crear un mensaje en la aplicación](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.html).

## Enviar una notificación

En el **[!UICONTROL Audiencia]** de la pestaña *Crear notificación push* flujo de trabajo, puede crear la audiencia para este mensaje de una de las siguientes maneras:

* En el **[!UICONTROL Segmentos de Analytics]** , seleccione un segmento de Adobe Analytics creado anteriormente.

* En el **[!UICONTROL Segmento personalizado]** , cree una audiencia utilizando los parámetros de segmento personalizados disponibles.

![configuración de un mensaje push](/help/assets/push-set-up.png)
