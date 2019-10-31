---
title: Notificaciones en la aplicación
seo-title: Notificaciones en la aplicación
description: Esta sección muestra cómo utilizar los mensajes en la aplicación en lugares.
seo-description: Esta sección muestra cómo utilizar los mensajes en la aplicación en lugares.
translation-type: tm+mt
source-git-commit: a76e91775efd92ce56f2dc5cbdcc65786855b5c3

---


# Notificaciones en la aplicación (#places-push-messaging)

La siguiente información muestra cómo configurar los mensajes en la aplicación para que se activen desde los eventos de lugares.

>[!IMPORTANT]
>
>Los mensajes deben estar en una visita de Analytics.

## Mensaje en la aplicación

Mobile Services le permite utilizar datos de ubicación que se envían a Analytics como evento o condición desencadenador de un mensaje en la aplicación. Si los mensajes en la aplicación se activan desde el SDK y no es necesario esperar a que Analytics procese los datos, los mensajes pueden aparecer en tiempo real en cuanto se produce el activador.

### Notificaciones locales

Esta es una lista de los tipos de mensajería en la aplicación disponibles:

* Pantalla completa
* Alerta
* Notificaciones locales

Estos tipos son mensajes en la aplicación porque los activa el SDK. Las notificaciones locales parecen notificaciones push porque aparecen cuando la aplicación está en segundo plano. Estas notificaciones también envían notificaciones en tiempo real cuando los usuarios entran o salen de los puntos de interés mientras la aplicación está en segundo plano. Para obtener más información, consulte [Extensión](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)del monitor de lugares.

### Requisitos previos

Antes de empezar, debe saber cómo enviar y crear un mensaje en la aplicación en Mobile Services y cómo funcionan los activadores. Para obtener más información, consulte [Crear un mensaje en la aplicación.](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/inapp-messages/t-in-app-message.html)

## Reglas en Experience Platform Launch

Puede crear reglas de lanzamiento que envíen a Analytics los datos que desea poder usar como parte de las reglas de activación de mensajes en la aplicación. Puede utilizar los datos de las extensiones Lugares en las reglas de lanzamiento como eventos y/o condiciones según el caso de uso.

* Uso de los datos de ubicación como evento desencadenador.

   Por ejemplo, puede enviar datos a Analytics cuando un usuario introduce un punto de interés.

* Uso de datos de ubicación como condición para un evento de activación.

   Por ejemplo, si ha creado una etiqueta de metadatos personalizada en el servicio de ubicación para el tiempo en diferentes puntos de interés, puede usar esos metadatos como parámetro para la condición Regla. Aunque puede utilizar esta condición con un evento de entrada de puntos de interés descrito anteriormente, también puede usar la condición como contexto para cualquier evento.

Una vez configurada la regla con los parámetros de condición y evento adecuados, complete la configuración de la regla configurando la acción para enviar datos a Analytics.

## Creación de una acción

Para crear una acción:

1. Seleccione la extensión **.[!UICONTROL Adobe Analytics]**
1. En la lista **[!UICONTROL Action type]** desplegable, seleccione **[!UICONTROL Track.]**
1. Escriba un nombre para la acción.
1. En el panel derecho, en **[!UICONTROL Context Data]**, seleccione el par clave-valor para establecer los datos de contexto que se enviarán a Analytics.

Por ejemplo, puede seleccionar `poiname` como clave y `{%%Last Entered POI Name}` como valor.

>[!TIP]
>
>Las reglas de procesamiento de Analytics se pueden configurar para recoger estos datos de contexto. For more information, see [Processing Rules](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-processing-rules.html). En el ejemplo de *Crear una acción*, la acción enviará el `poiname` como contexto para describir el evento de entrada de puntos de interés que se está enviando a Analytics.

![creación de una acción](/help/assets/configure-action.png)

Este es un ejemplo de la regla completa:

![regla completada](/help/assets/create-a-rule.png)

## Creación de un mensaje en la aplicación en Mobile Services

Como parte de los parámetros de activador, puede crear la audiencia del mensaje con datos del servicio de ubicación de una de las siguientes formas:

* Uso de acciones específicas de la ubicación, como una entrada o una salida.
* Uso de metadatos de puntos de interés que se envían como datos de contexto para reducir el destino de la audiencia.

   Esta opción se puede utilizar con una acción específica de una ubicación, como entrada, o bien como contexto para otro evento, como un inicio o un clic de botón.

   A continuación se muestra un ejemplo de cómo configurar un mensaje en la aplicación para dar la bienvenida a los usuarios que especifican un punto de interés que tiene **[!UICONTROL Adobe]** el nombre:

   ![parámetros desencadenadores](/help/assets/trigger-parameters.png)

* Los parámetros de los encabezados Lugares de la página *Activadores y características* de Mobile Services no funcionan con los datos del servicio de ubicación.

   Estos parámetros son solo para la base de datos heredada de Places que se creó en Mobile Services.