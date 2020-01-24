---
title: Uso de Places Service con Mobile Services para mensajes
description: Esta sección muestra cómo utilizar el servicio de lugares con Mobile Services para los mensajes.
translation-type: tm+mt
source-git-commit: 5a21e734c0ef56c815389a9f08b445bedaae557a

---


# Adobe Mobile Services {#places-mobile-services}

Antes de poder usar la extensión Mobile Services para la mensajería, revise los siguientes requisitos previos:

* Se han creado puntos de interés en el Servicio de lugares. For more information, see [Create a POI](/help/poi-mgmt-ui/create-a-poi-ui.md).

   >[!IMPORTANT]
   >
   >El servicio de lugares incluye una base de datos de puntos de interés nueva y mejorada para su organización que existe fuera de la interfaz de usuario heredada de Mobile Services. Los puntos de interés ubicados en la navegación de la página *Administrar ubicaciones* de Mobile Service solo funcionarán en la versión 4 del SDK.

* Esta es la página de administración del punto de interés de *Administrar lugares* en la interfaz de usuario heredada de Mobile Services para versiones anteriores del SDK:

   ![Interfaz de usuario heredada](/help/assets/legacy-location-v4-ui.png)

* Esta es la interfaz de usuario del servicio de lugares:

   ![Interfaz de usuario de administración de puntos de interés del servicio de lugares](/help/assets/places-ui.png)

* El SDK de ACP está configurado correctamente con las extensiones Servicio de lugares y/o Monitor de lugares.

   Esto significa que los datos están disponibles como eventos o condiciones en el motor de reglas de inicio de la plataforma de experiencia para su aplicación móvil. Para obtener más información, consulte Extensión [de](/help/places-ext-aep-sdks/places-extension/places-extension.md) lugares o Extensión [de monitor de](/help/places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.md)lugares.

* Familiarícese con la creación y publicación de reglas de inicio de plataforma de experiencia en el SDK ACP en su aplicación móvil.

   For more information, see [Rules engine](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine).

* Los elementos de datos de inicio de la plataforma de experiencia se crean a partir de los datos de la extensión Lugares que se utilizarán en el motor de reglas.

   For more information, see [Data elements](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine#data-elements).

## Informes

Antes de utilizar los informes, complete los siguientes requisitos previos:

* Los datos del servicio de lugares se envían correctamente al grupo de informes de Adobe Analytics.

   Para obtener más información, consulte [Uso del servicio de lugares con Adobe Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md).

* Familiarícese con los informes de Mobile Services.

   For more information, see [Reports](https://docs.adobe.com/content/help/en/mobile-services/using/reports-ug/usage.html).

## Visualización de informes

Puede ejecutar informes de Mobile Service utilizando los datos de Places Service que se envían a Adobe Analytics. En el siguiente ejemplo, los eventos se envían cuando los usuarios tienen entradas en uno de los puntos de interés. En este informe se ha agregado un filtro del evento de entrada de puntos de interés sobre el informe de usuario predeterminado:

![Visualización de informes](/help/assets/report-visualize.png)

En las interfaces de Adobe Analytics hay disponible una flexibilidad adicional para visualizar datos del servicio de lugares.

