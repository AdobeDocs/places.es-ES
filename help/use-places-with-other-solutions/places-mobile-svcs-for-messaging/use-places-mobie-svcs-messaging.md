---
title: Uso del servicio Places con Mobile Services para la mensajería
description: Esta sección muestra cómo utilizar Places Service con Mobile Services para la mensajería.
exl-id: dfa6b8bb-6bf2-44eb-8bfc-87294807ec3b
TQID: https://experienceleague.adobe.com/-axuli6p-QHthMkucGLCcgyHCqrwudXmif-dZwpGli4
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: b069d60e-95f3-44d6-95a8-ddc862a4bc38
  - id: c20d46e7-1c7d-476c-a50e-3961d4dce35f
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 359
ht-degree: 3%

---

# Adobe Mobile Services {#places-mobile-services}

Antes de poder usar la extensión de Mobile Services para la mensajería, revise los siguientes requisitos previos:

* Se han creado puntos de interés en Places Service. Para obtener más información, consulte [Crear un punto de interés](/help/poi-mgmt-ui/create-a-poi-ui.md).

  >[!IMPORTANT]
  >
  >El servicio Places incluye una base de datos de puntos de interés nueva y mejorada para su organización que existe fuera de la interfaz de usuario heredada de Mobile Services. Los puntos de interés que se encuentran en la navegación de páginas de *Administrar lugares* de Mobile Services solo funcionarán para la versión 4 de SDK.

* Esta es la página de administración de puntos de interés *Administrar lugares* en la interfaz de usuario heredada de Mobile Services para versiones anteriores de SDK:

  ![IU heredada](/help/assets/legacy-location-v4-ui.png)

* Esta es la interfaz de usuario del servicio de Places:

  ![IU de administración de puntos de interés de Places Service](/help/assets/places-ui.png)

* La SDK de ACP está correctamente configurada con la extensión Places.

  Esto significa que los datos están disponibles como eventos o condiciones en el motor de reglas de Experience Platform Launch para su aplicación móvil. Para obtener más información, consulte [Extensión Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

* Familiarícese con la creación y publicación de reglas de Experience Platform Launch en SDK de ACP en su aplicación móvil.

  Para obtener más información, consulte [Motor de reglas](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine).

* Los elementos de datos de Experience Platform Launch se crean a partir de los datos de la extensión Places que se utilizarán en el motor de reglas.

  Para obtener más información, consulte [Elementos de datos](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine#data-elements).

## Creación de informes

Antes de poder usar los informes, complete los siguientes requisitos previos:

* Los datos del servicio de Places se han enviado correctamente al grupo de informes de Adobe Analytics.

  Para obtener más información, consulte [Usar el servicio Places con Adobe Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md).

* Familiarícese con los informes de Mobile Services.

  Para obtener más información, consulte [Informes](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.html?lang=es).

## Visualización de informes

Puede ejecutar informes de Mobile Services usando los datos de Places Service que se envían a Adobe Analytics. En el ejemplo siguiente, los eventos se envían cuando los usuarios tienen entradas en uno de los puntos de interés. En este informe se ha añadido un filtro del evento de entrada de punto de interés sobre el informe de usuario predeterminado:

![Visualización de informes](/help/assets/report-visualize.png)

Hay una flexibilidad adicional disponible en las interfaces de Adobe Analytics para visualizar los datos del servicio de Places.
