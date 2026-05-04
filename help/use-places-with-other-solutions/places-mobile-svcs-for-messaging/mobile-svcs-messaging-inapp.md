---
title: Notificaciones en la aplicación
description: Esta sección muestra cómo utilizar el servicio de Places con la mensajería en la aplicación.
exl-id: c655e64b-0737-44d5-b453-2ac02fb9cbcc
TQID: https://experienceleague.adobe.com/Z39ybIytDRlCbkMthWjvk5F-oexy0C9gtqgK1mmyMxM
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 689
ht-degree: 2%

---

# Notificaciones en la aplicación {#places-push-messaging}

La siguiente información muestra cómo configurar los mensajes en la aplicación para almacenar en déclencheur los eventos del servicio de Places.

>[!IMPORTANT]
>
>Los mensajes deben estar en una visita de Analytics.

## Mensaje en la aplicación

Mobile Services le permite utilizar datos de ubicación que se envían a Analytics como eventos de déclencheur o condiciones para un mensaje en la aplicación. Si los mensajes en la aplicación se activan desde SDK y no necesitan esperar a que Analytics procese los datos, los mensajes pueden aparecer en tiempo real en cuanto se produce el déclencheur.

### Notificaciones locales

Esta es una lista de los tipos de mensajería en la aplicación disponibles:

* Pantalla completa
* Alerta
* Notificaciones locales

Estos tipos son mensajes en la aplicación porque se activan mediante SDK. Las notificaciones locales tienen el aspecto de notificaciones push, ya que aparecen cuando la aplicación se encuentra en segundo plano. Estas notificaciones también envían notificaciones en tiempo real a medida que los usuarios entran o salen de sus puntos de interés mientras la aplicación se encuentra en segundo plano.

### Requisitos previos

Antes de empezar, debe saber cómo enviar y crear un mensaje en la aplicación en Mobile Services y cómo funcionan los déclencheur. Para obtener más información, consulte [Crear un mensaje en la aplicación.](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.html?lang=es)

## Reglas en Experience Platform Launch

Puede crear reglas de Experience Platform Launch que envíen a Analytics los datos que desea poder utilizar como parte de las reglas de Déclencheur de mensajes en la aplicación. Puede utilizar los datos de las extensiones Places en las reglas de Experience Platform Launch como eventos o condiciones según el caso de uso.

* Usar datos de ubicación como evento de activación.

  Por ejemplo, puede enviar datos a Analytics cuando un usuario introduzca un punto de interés (POI).

* El uso de datos de ubicación como condición para un evento de activación.

  Por ejemplo, si ha creado una etiqueta de metadatos personalizada en el servicio Places para el tiempo en diferentes puntos de interés, puede utilizar esos metadatos como parámetro para la condición de regla. Aunque puede utilizar esta condición con un evento de entrada de punto de interés descrito anteriormente, también puede utilizar la condición como contexto para cualquier evento.

Una vez configurada la regla con los parámetros de evento y condición adecuados, complete la configuración de reglas configurando la acción para enviar datos a Analytics.

## Creación de una acción

Para crear una acción:

1. Seleccione la extensión **[!UICONTROL Adobe Analytics]**.
1. En la lista desplegable **[!UICONTROL Tipo de acción]**, seleccione **[!UICONTROL Rastrear.]**
1. Escriba un nombre para la acción.
1. En el panel derecho, en **[!UICONTROL Datos de contexto]**, seleccione el par clave-valor para establecer los datos de contexto que se enviarán a Analytics.

Por ejemplo, puede seleccionar `poiname` como clave y `{%%Last Entered POI Name}` como valor.

>[!TIP]
>
>Se pueden configurar reglas de procesamiento de Analytics para recoger estos datos de contexto. Para obtener más información, consulte [Reglas de procesamiento](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules.html). En el ejemplo de *Crear una acción*, la acción enviará `poiname` como contexto para describir el evento de entrada de punto de interés que se envía a Analytics.

![creando una acción](/help/assets/configure-action.png)

Este es un ejemplo de la regla completa:

![regla completada](/help/assets/create-a-rule.png)

## Creación de un mensaje en la aplicación en Mobile Services

Como parte de los parámetros de Déclencheur, puede crear la audiencia del mensaje con datos del servicio Places de una de las siguientes maneras:

* Uso de acciones específicas de la ubicación, como una entrada o una salida.
* El uso de metadatos de puntos de interés que se envían como datos de contexto para reducir el destinatario de la audiencia.

  Esta opción se puede utilizar con una acción específica de la ubicación, como una entrada, o se puede utilizar como contexto para otro evento, como un inicio o un clic en un botón.

  A continuación se muestra un ejemplo de cómo configurar un mensaje en la aplicación para dar la bienvenida a los usuarios que introduzcan un punto de interés que tenga **[!UICONTROL Adobe]** en el nombre:

  ![parámetros de déclencheur](/help/assets/trigger-parameters.png)

* Los parámetros de los encabezados del servicio Places en la página *Déclencheur y características* de Mobile Services no funcionan con los datos del servicio Places.

  Estos parámetros solo son para la base de datos heredada de Places Service que se creó en Mobile Services.
