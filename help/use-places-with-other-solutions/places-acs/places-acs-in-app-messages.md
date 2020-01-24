---
title: Mensajes en la aplicación con el servicio de lugares
description: Esta sección proporciona información sobre cómo utilizar la mensajería push en Campaign Standard con mensajes en la aplicación en Campaign Standard.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b

---


# Mensajería en la aplicación con el servicio de lugares {#in-app-messages-loc-service}

Esta información le ayuda a comprender cómo puede utilizar la información del servicio de lugares para enviar mensajes en la aplicación o notificaciones locales.

## Requisitos previos

Antes de comenzar, complete las siguientes tareas:

* Tenga una aplicación móvil configurada con el SDK de Adobe Experience Platform Mobile, incluida la extensión [de](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)Adobe Campaign Standard.

* Integre el SDK [de](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) Adobe Experience Platform Mobile en la aplicación.
* Agregue [Adobe Campaign Standard Extension](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) a la configuración de la aplicación móvil.

* [Cree un punto de interés](/help/poi-mgmt-ui/create-a-poi-ui.md) en la interfaz de administración de puntos de interés del servicio de lugares.

* Instale y configure las extensiones [](/help/places-ext-aep-sdks/places-extension/places-extension.md) Places y [Places Monitor](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md) en la aplicación móvil.

## Envío de un mensaje en la aplicación basado en una entrada o salida de una cerca geográfica

1. En la instancia de Adobe Campaign Standard, haga clic en **[!UICONTROL Create In-App message]**.
1. Para el tipo de mensaje, seleccione **[!UICONTROL Target all users of a Mobile application]**.
1. Haga clic **[!UICONTROL Next]**y escriba los detalles generales.
1. En el panel izquierdo, compruebe que puede utilizar varios activadores relacionados con los servicios de lugares.

   * Puede elegir que se muestre el mensaje en la aplicación si el usuario ha introducido una cerca geográfica de puntos de interés.
   * También puede utilizar metadatos definidos en la interfaz de usuario de los servicios de lugar para filtrar la audiencia.
   En el ejemplo siguiente, puede activar un mensaje en la aplicación que se muestra únicamente a los usuarios que acceden a uno de los centros de vacaciones que participan en un programa de bebidas gratuitas y desea enviar un cupón a esos usuarios cuando lleguen.

   ![&quot;Metadatos de lugares de mensajes en la aplicación&quot;](/help/assets/last-entered-vacation.png)

1. Click the **[!UICONTROL Next]**to finish creating the In-app message for delivery.

   ![&quot;crear un evento&quot;](/help/assets/prepare-ACS.png)

   Para probar la entrega de mensajes en la aplicación, inicie la aplicación en el estudio Xcode o Android y utilice el simulador de ubicación para seleccionar un punto de interés que se ajuste a los criterios de mensajería.

   ![&quot;cupón de bebida&quot;](/help/assets/drink-coupon-on-app.png)

El uso de los servicios de lugares con Adobe Campaign Standard le proporciona una poderosa herramienta para segmentar y dirigir sus mensajes a los usuarios en función de las entradas y salidas de la valla geográfica. Esta integración le permite crear casos de uso más personalizados y contextuales.

>[!VIDEO](https://www.youtube.com/watch?v=ikiTTQw9c-o)