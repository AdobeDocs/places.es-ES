---
title: Mensajes en la aplicación con el servicio Places
description: En esta sección se proporciona información sobre cómo utilizar la mensajería push en el Campaign Standard con mensajes en la aplicación en el Campaign Standard.
exl-id: c80727b8-20c9-4ca0-9f2c-20ec646bb7fa
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 4%

---

# Mensajería en la aplicación con el servicio Places {#in-app-messages-loc-service}

Esta información le ayuda a comprender cómo puede utilizar la información del servicio de Places para enviar mensajes en la aplicación o notificaciones locales.

## Requisitos previos

Antes de comenzar, complete las siguientes tareas:

* Tener una aplicación móvil configurada con el SDK de Adobe Experience Platform Mobile, incluido el [Extensión de Adobe Campaign Standard](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard).

* Integrar el [SDK de Adobe Experience Platform Mobile](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) en su aplicación.
* Agregue la variable [Extensión de Adobe Campaign Standard](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) a la configuración de la aplicación móvil.

* [Crear un punto de interés](/help/poi-mgmt-ui/create-a-poi-ui.md) en la interfaz de administración de puntos de interés de Places Service.

* Instale y configure el [Extensión Places](/help/places-ext-aep-sdks/places-extension/places-extension.md) y una solución de monitorización de región ([Documentación de CoreLocation](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) para iOS, o [Documentación de la ubicación de Android](https://developer.android.com/training/location/geofencing)) en la aplicación móvil.

## Envío de un mensaje en la aplicación basado en una entrada o salida de geo-valla

1. En la instancia de Adobe Campaign Standard, haga clic en **[!UICONTROL Crear mensaje en la aplicación]**.
1. Para el tipo de mensaje, seleccione **[!UICONTROL Dirigirse a todos los usuarios de una aplicación móvil]**.
1. Haga clic en **[!UICONTROL Siguiente]** y escriba los detalles generales.
1. En el panel izquierdo, compruebe que puede utilizar varios déclencheur relacionados con Servicios de Places.

   * Puede elegir que se muestre el mensaje en la aplicación si el usuario ha introducido un punto de interés geográfico.
   * También puede utilizar metadatos definidos en la interfaz de usuario de Servicios de Places para filtrar la audiencia.

   En el siguiente ejemplo, puede crear un déclencheur de un mensaje en la aplicación que se muestre únicamente a los usuarios que entren en uno de los complejos de vacaciones que participan en un programa de bebidas gratuitas y desea enviar un cupón a esos usuarios cuando lleguen.

   ![&quot;Metadatos de lugares de mensajes en la aplicación&quot;](/help/assets/last-entered-vacation.png)

1. Haga clic en el **[!UICONTROL Siguiente]** para terminar de crear el mensaje en la aplicación para la entrega.

   ![&quot;crear un evento&quot;](/help/assets/prepare-ACS.png)

   Para probar la entrega de mensajes en la aplicación, inicie la aplicación en Xcode o en Android Studio y utilice el simulador de ubicación para seleccionar un punto de interés que se ajuste a los criterios de mensajería.

   ![&quot;cupón de bebida&quot;](/help/assets/drink-coupon-on-app.png)

El uso de Places Services con Adobe Campaign Standard le proporciona una potente herramienta para segmentar y dirigir sus mensajes a los usuarios en función de las entradas y salidas de la valla geográfica. Esta integración le permite crear casos de uso más personalizados y contextuales.

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

[Servicio de ubicación de Adobe Experience Platform con mensajería de Campaign](https://www.youtube.com/watch?v=ikiTTQw9c-o)
