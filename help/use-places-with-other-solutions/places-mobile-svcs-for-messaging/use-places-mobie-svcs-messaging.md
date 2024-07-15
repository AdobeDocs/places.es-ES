---
title: Uso del servicio Places con Mobile Services para la mensajería
description: Esta sección muestra cómo utilizar Places Service con Mobile Services para la mensajería.
exl-id: dfa6b8bb-6bf2-44eb-8bfc-87294807ec3b
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 1%

---

# Adobe Mobile Services {#places-mobile-services}

Antes de poder usar la extensión de Mobile Services para la mensajería, revise los siguientes requisitos previos:

* Se han creado puntos de interés en Places Service. Para obtener más información, consulte [Crear un punto de interés](/help/poi-mgmt-ui/create-a-poi-ui.md).

  >[!IMPORTANT]
  >
  >El servicio Places incluye una base de datos de puntos de interés nueva y mejorada para su organización que existe fuera de la interfaz de usuario heredada de Mobile Services. Los puntos de interés que se encuentran en la navegación de páginas de *Administrar lugares* de Mobile Services solo funcionarán para la versión 4 del SDK.

* Esta es la página de administración de puntos de interés *Administrar lugares* en la interfaz de usuario heredada de Mobile Services para versiones anteriores del SDK:

  ![IU heredada](/help/assets/legacy-location-v4-ui.png)

* Esta es la interfaz de usuario del servicio de Places:

  ![IU de administración de puntos de interés de Places Service](/help/assets/places-ui.png)

* El SDK de ACP está correctamente configurado con la extensión Places.

  Esto significa que los datos están disponibles como eventos o condiciones en el motor de reglas del Experience Platform Launch para su aplicación móvil. Para obtener más información, consulte [Extensión Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

* Familiarícese con la creación y publicación de reglas de Experience Platform Launch en el SDK de ACP en su aplicación móvil.

  Para obtener más información, consulte [Motor de reglas](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine).

* Los elementos de datos del Experience Platform Launch se crean a partir de los datos de la extensión Places que se utilizarán en el motor de reglas.

  Para obtener más información, consulte [Elementos de datos](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine#data-elements).

## Informes

Antes de poder usar los informes, complete los siguientes requisitos previos:

* Los datos del servicio de Places se han enviado correctamente al grupo de informes de Adobe Analytics.

  Para obtener más información, consulte [Usar el servicio Places con Adobe Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md).

* Familiarícese con los informes de Mobile Services.

  Para obtener más información, consulte [Informes](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.html?lang=es).

## Visualización de informes

Puede ejecutar informes de Mobile Services usando los datos de Places Service que se envían a Adobe Analytics. En el ejemplo siguiente, los eventos se envían cuando los usuarios tienen entradas en uno de los puntos de interés. En este informe se ha añadido un filtro del evento de entrada de punto de interés sobre el informe de usuario predeterminado:

![Visualización de informes](/help/assets/report-visualize.png)

Hay una flexibilidad adicional disponible en las interfaces de Adobe Analytics para visualizar los datos del servicio de Places.
