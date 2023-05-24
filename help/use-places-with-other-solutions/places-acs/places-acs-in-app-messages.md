---
title: Mensajes en la aplicación con el servicio Places
description: Esta sección proporciona información sobre cómo utilizar la mensajería push en Campaign Standard con mensajes en la aplicación en Campaign Standard.
exl-id: c80727b8-20c9-4ca0-9f2c-20ec646bb7fa
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 4%

---

# Mensajería en la aplicación con el servicio Places {#in-app-messages-loc-service}

Esta información le ayuda a comprender cómo puede utilizar la información del servicio Places para enviar mensajes en la aplicación o notificaciones locales.

## Requisitos previos

Antes de empezar, complete las siguientes tareas:

* Tener una aplicación móvil configurada con el SDK de Adobe Experience Platform Mobile, incluido el [Extensión de Adobe Campaign Standard](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard).

* Integración de [SDK de Adobe Experience Platform Mobile](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) en la aplicación.
* Añada el [Extensión de Adobe Campaign Standard](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) a la configuración de su aplicación móvil.

* [Crear un POI](/help/poi-mgmt-ui/create-a-poi-ui.md) en la interfaz de administración de puntos de interés de Places Service.

* Instalación y configuración de [Extensión Places](/help/places-ext-aep-sdks/places-extension/places-extension.md) y una solución de monitorización de regiones ([Documentación de CoreLocation](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) para iOS, o [Documentación de ubicación de Android](https://developer.android.com/training/location/geofencing)) en su aplicación móvil.

## Envío de un mensaje en la aplicación en función de una entrada o salida de geoperímetro

1. En la instancia de Adobe Campaign Standard, haga clic en **[!UICONTROL Crear mensaje en la aplicación]**.
1. Para el tipo de mensaje, seleccione **[!UICONTROL Segmentar a todos los usuarios de una aplicación móvil]**.
1. Clic **[!UICONTROL Siguiente]** y escriba los detalles generales.
1. En el panel izquierdo, compruebe que puede utilizar varios déclencheur relacionados con Places Services.

   * Puede elegir que se muestre el mensaje en la aplicación si el usuario ha introducido un límite geográfico de puntos de interés.
   * También puede utilizar metadatos definidos en la interfaz de usuario de Places Services para filtrar la audiencia.

   En el siguiente ejemplo, puede almacenar en déclencheur un mensaje en la aplicación que se muestra solo a los usuarios que entran en uno de los centros turísticos que participan en un programa de bebidas gratuitas y que desea enviar a esos usuarios un cupón cuando lleguen.

   ![&quot;Metadatos de lugares de mensajes en la aplicación&quot;](/help/assets/last-entered-vacation.png)

1. Haga clic en **[!UICONTROL Siguiente]** para terminar de crear el mensaje en la aplicación para la entrega.

   ![&quot;crear un evento&quot;](/help/assets/prepare-ACS.png)

   Para probar el envío de mensajes en la aplicación, inicie la aplicación en Xcode o Android Studio y utilice el simulador de ubicación para seleccionar un punto de interés que se ajuste a los criterios de mensajería.

   ![&quot;cupón de bebida&quot;](/help/assets/drink-coupon-on-app.png)

El uso de Servicios de Places con Adobe Campaign Standard le ofrece una potente herramienta para segmentar y dirigir los mensajes a usuarios en función de las entradas y salidas del geoperímetro. Esta integración le permite crear casos de uso más personalizados y contextuales.

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

[Servicio de ubicación de Adobe Experience Platform con mensajería de Campaign](https://www.youtube.com/watch?v=ikiTTQw9c-o)
