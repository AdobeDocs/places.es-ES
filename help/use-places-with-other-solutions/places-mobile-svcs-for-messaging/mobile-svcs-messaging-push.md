---
title: Notificaciones push
seo-title: Notificaciones push
description: Esta sección le muestra cómo utilizar los lugares con notificaciones push.
seo-description: Esta sección le muestra cómo utilizar los lugares con notificaciones push.
translation-type: tm+mt
source-git-commit: 95c29df19f61e7854e39b47e39471f7f1e94b736

---


# Notificaciones push (#places-push-messaging)

Mobile Services permite enviar notificaciones push a segmentos de Adobe Analytics. En el servicio de ubicación, puede segmentar la audiencia del mensaje push según sus interacciones históricas con sus puntos de interés. Por ejemplo, puede enviar un mensaje a los usuarios que hayan estado en una de sus tiendas en los últimos 30 días.

Antes de comenzar, asegúrese de haber completado las siguientes tareas:

* Adobe Analytics ha procesado los datos del servicio de ubicación.

   Esto significa que la aplicación móvil ha enviado correctamente los datos del servicio de ubicación a un grupo de informes y que los datos están disponibles para la segmentación.

* El canal de notificaciones push en Mobile Services está configurado.

   Para obtener más información, consulte [Crear un mensaje en la aplicación](https://docs.adobe.com/content/help/en/mobile-services/using/manage-app-settings-ug/configuring-app/prerequisites-push-messaging.html).

* Obtenga información sobre cómo enviar una notificación push a un segmento de Analytics en Mobile Services.

   Para obtener más información, consulte [Crear un mensaje en la aplicación](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/push-messages/t-create-push-message.html).

## Enviar una notificación

En la **[!UICONTROL Audience]** ficha del flujo de trabajo *Crear notificación* push, puede crear la audiencia para este mensaje de una de las siguientes formas:

* En la lista **[!UICONTROL Analytics Segments]** desplegable, seleccione un segmento de Adobe Analytics creado anteriormente.

* En la **[!UICONTROL Custom Segment]** sección, cree una audiencia utilizando los parámetros de segmento personalizados disponibles.

![configuración de un mensaje push](/help/assets/push-set-up.png)

