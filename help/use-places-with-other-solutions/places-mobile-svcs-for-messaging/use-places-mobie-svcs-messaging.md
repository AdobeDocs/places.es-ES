---
title: Uso de lugares con Mobile Services para mensajes
seo-title: Uso de lugares con Mobile Services para mensajes
description: En esta sección se muestra cómo utilizar los mensajes en lugares con Mobile Services.
seo-description: En esta sección se muestra cómo utilizar los mensajes en lugares con Mobile Services.
translation-type: tm+mt
source-git-commit: accfa6ba009ad3419481d9bd3b498143228099fc

---


# Adobe Mobile Services {#places-mobile-services}

Antes de poder usar la extensión Mobile Services para la mensajería, revise los siguientes requisitos previos:

* Se han creado puntos de interés en el servicio de ubicación. Consulte Documentación si es necesario. (vínculo para crear un punto de interés)Nota: El servicio de ubicación incluye una nueva y mejorada base de datos de puntos de interés para su organización que existe fuera de la interfaz AMS heredada. Los puntos de interés encontrados en la navegación "Gestionar lugares" de AMS solo funcionarán en la versión 4 del SDK.
   * Esta es la interfaz de administración de puntos de interés de Places heredada en AMS para versiones anteriores del SDK:

      ![Interfaz de usuario heredada](/help/assets/legacy-location-v4-ui.png)

   * Esta es la interfaz de administración de puntos de interés del servicio de ubicación:

      ![Interfaz de usuario de administración de puntos de interés del servicio de ubicación](/help/assets/places-ui.png)

* El SDK de ACP está configurado correctamente con extensiones Places y/o Places Monitor. Esto significa que los datos están disponibles como eventos y/o condiciones en el motor de reglas de lanzamiento de la aplicación móvil. Consulte la documentación si es necesario. (https://aep-sdks.gitbook.io/docs/beta/adobe-places)

* Familiarizarse con la creación y publicación de reglas de inicio en el SDK de ACP en la aplicación móvil. Consulte la documentación si es necesario. (https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine)

* Los elementos de datos de inicio se crean a partir de los datos de extensión del SDK de Lugares que se utilizarán en las reglas. Consulte la documentación (https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine#data-elements)

## Informes

Antes de utilizar los informes, complete los siguientes requisitos previos:

* Se han enviado correctamente los datos del servicio de ubicación al grupo de informes de Adobe Analytics. Si es necesario, visite la documentación de Adobe Analytics (vínculo a los documentos de Steve).
* Familiarizado con los informes de AMS. Si es necesario, visite la documentación (https://docs.adobe.com/content/help/en/mobile-services/using/reports-ug/usage.html)

## Visualización de informes

Puede ejecutar informes de AMS mediante los datos del servicio de ubicación que se envían a Adobe Analytics. Por ejemplo, he enviado eventos cuando los usuarios tienen entradas en uno de mis puntos de interés. En este informe he agregado un filtro del evento de entrada de puntos de interés sobre mi informe de usuario predeterminado:

![Visualización de informes](/help/assets/report-visualize.png)

En las interfaces de Adobe Analytics hay disponible flexibilidad adicional para visualizar datos del servicio de ubicación.

