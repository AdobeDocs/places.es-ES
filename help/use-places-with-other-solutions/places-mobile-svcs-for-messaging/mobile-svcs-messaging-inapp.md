---
title: Notificaciones en la aplicación
description: Esta sección muestra cómo utilizar el servicio de Places con la mensajería en la aplicación.
exl-id: c655e64b-0737-44d5-b453-2ac02fb9cbcc
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 4%

---

# Notificaciones en la aplicación {#places-push-messaging}

La siguiente información muestra cómo configurar los mensajes en la aplicación para almacenar en déclencheur los eventos del servicio de Places.

>[!IMPORTANT]
>
>Los mensajes deben estar en una visita de Analytics.

## Mensaje en la aplicación

Mobile Services le permite utilizar datos de ubicación que se envían a Analytics como eventos de déclencheur o condiciones para un mensaje en la aplicación. Si los mensajes en la aplicación se activan desde el SDK y no necesitan esperar a que Analytics procese los datos, los mensajes pueden aparecer en tiempo real en cuanto se produce el déclencheur.

### Notificaciones locales

Esta es una lista de los tipos de mensajería en la aplicación disponibles:

* Pantalla completa
* Alerta
* Notificaciones locales

Estos tipos son mensajes en la aplicación porque los activa el SDK. Las notificaciones locales tienen el aspecto de notificaciones push, ya que aparecen cuando la aplicación se encuentra en segundo plano. Estas notificaciones también envían notificaciones en tiempo real a medida que los usuarios entran o salen de sus puntos de interés mientras la aplicación se encuentra en segundo plano.

### Requisitos previos

Antes de empezar, debe saber cómo enviar y crear un mensaje en la aplicación en Mobile Services y cómo funcionan los déclencheur. Para obtener más información, consulte [Crear un mensaje en la aplicación.](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.html)

## Reglas en Experience Platform Launch

Puede crear reglas de Experience Platform Launch que envíen a Analytics los datos que desea poder utilizar como parte de las reglas de Déclencheur de mensajes en la aplicación. Puede utilizar los datos de las extensiones Places en las reglas de Experience Platform Launch como eventos o condiciones, según el caso de uso.

* Usar datos de ubicación como evento de activación.

  Por ejemplo, puede enviar datos a Analytics cuando un usuario introduzca un punto de interés (POI).

* El uso de datos de ubicación como condición para un evento de activación.

  Por ejemplo, si ha creado una etiqueta de metadatos personalizada en el servicio Places para el tiempo en diferentes puntos de interés, puede utilizar esos metadatos como parámetro para la condición de regla. Aunque puede utilizar esta condición con un evento de entrada de punto de interés descrito anteriormente, también puede utilizar la condición como contexto para cualquier evento.

Una vez configurada la regla con los parámetros de evento y condición adecuados, complete la configuración de reglas configurando la acción para enviar datos a Analytics.

## Creación de una acción

Para crear una acción:

1. Seleccione el **[!UICONTROL Adobe Analytics]** extensión.
1. En el **[!UICONTROL Tipo de acción]** , seleccione la opción **[!UICONTROL Seguimiento.]**
1. Escriba un nombre para la acción.
1. En el panel derecho, en **[!UICONTROL Datos de contexto]**, seleccione el par clave-valor para establecer los datos de contexto que se enviarán a Analytics.

Por ejemplo, puede seleccionar `poiname` como clave y `{%%Last Entered POI Name}` como el valor.

>[!TIP]
>
>Se pueden configurar reglas de procesamiento de Analytics para recoger estos datos de contexto. Para obtener más información, consulte [Reglas de procesamiento](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules.html). En el ejemplo de *Crear una acción*, la acción enviará el `poiname` como el contexto para describir el evento de entrada de punto de interés que se envía a Analytics.

![creación de una acción](/help/assets/configure-action.png)

Este es un ejemplo de la regla completa:

![regla completada](/help/assets/create-a-rule.png)

## Creación de un mensaje en la aplicación en Mobile Services

Como parte de los parámetros de Déclencheur, puede crear la audiencia del mensaje con datos del servicio Places de una de las siguientes maneras:

* Uso de acciones específicas de la ubicación, como una entrada o una salida.
* El uso de metadatos de puntos de interés que se envían como datos de contexto para reducir el destinatario de la audiencia.

  Esta opción se puede utilizar con una acción específica de la ubicación, como una entrada, o se puede utilizar como contexto para otro evento, como un inicio o un clic en un botón.

  A continuación, se muestra un ejemplo de cómo configurar un mensaje en la aplicación para dar la bienvenida a los usuarios que introduzcan un punto de interés que tenga **[!UICONTROL Adobe]** en el nombre:

  ![Parámetros de déclencheur](/help/assets/trigger-parameters.png)

* Parámetros en los encabezados de servicio de Places en la variable *Déclencheur y características* Las páginas de en Mobile Services no funcionan con datos del servicio Places.

  Estos parámetros solo son para la base de datos heredada de Places Service que se creó en Mobile Services.
