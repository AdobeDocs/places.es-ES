---
title: Notificaciones en la aplicación
description: Esta sección le muestra cómo utilizar el servicio Places con mensajería en la aplicación.
exl-id: c655e64b-0737-44d5-b453-2ac02fb9cbcc
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 4%

---

# Notificaciones en la aplicación {#places-push-messaging}

La siguiente información muestra cómo configurar los mensajes en la aplicación para el déclencheur de eventos del servicio de Places.

>[!IMPORTANT]
>
>Los mensajes deben estar en una visita de Analytics.

## Mensaje en la aplicación

Mobile Services le permite utilizar datos de ubicación que se envían a Analytics como los eventos de déclencheur o condición para un mensaje en la aplicación. Si los mensajes en la aplicación se activan desde el SDK y no es necesario esperar a que Analytics procese los datos, estos pueden aparecer en tiempo real en cuanto se produzca el déclencheur.

### Notificaciones locales

Esta es una lista de los tipos de mensajería en la aplicación disponibles:

* Pantalla completa
* Alerta
* Notificaciones locales

Estos tipos son mensajes en la aplicación porque los activa el SDK. Las notificaciones locales parecen notificaciones push porque aparecen cuando la aplicación está en segundo plano. Estas notificaciones también envían notificaciones en tiempo real cuando los usuarios entran o salen de sus puntos de interés mientras la aplicación está en segundo plano.

### Requisitos previos

Antes de empezar, debe saber cómo enviar y crear un mensaje en la aplicación en Mobile Services y cómo funcionan los déclencheur. Para obtener más información, consulte [Crear un mensaje en la aplicación.](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/inapp-messages/t-in-app-message.html)

## Reglas en Experience Platform Launch

Puede crear reglas de Experience Platform Launch que envíen a Analytics los datos que desea poder usar como parte de sus reglas de Déclencheur de mensajes en la aplicación. Puede utilizar los datos de las extensiones Places en las reglas de Experience Platform Launch como eventos o condiciones, según el caso de uso.

* Uso de datos de ubicación como evento de activación.

   Por ejemplo, puede enviar datos a Analytics cuando un usuario introduce un punto de interés.

* Uso de datos de ubicación como condición para un evento de activación.

   Por ejemplo, si ha creado una etiqueta de metadatos personalizada en el servicio Places para el tiempo en diferentes puntos de interés, puede utilizar esos metadatos como parámetro para la condición de regla. Aunque puede utilizar esta condición con un evento de entrada de punto de interés descrito anteriormente, también puede utilizar la condición como contexto para cualquier evento.

Una vez configurada la regla con los parámetros de condición y evento adecuados, complete la configuración de regla configurando la acción para enviar datos a Analytics.

## Creación de una acción

Para crear una acción:

1. Seleccione el **[!UICONTROL Adobe Analytics]** extensión.
1. En el **[!UICONTROL Tipo de acción]** lista desplegable, seleccione **[!UICONTROL Rastrear.]**
1. Escriba un nombre para la acción.
1. En el panel derecho, en **[!UICONTROL Datos de contexto]**, seleccione el par clave-valor para establecer los datos de contexto que se enviarán a Analytics.

Por ejemplo, puede seleccionar `poiname` como clave y `{%%Last Entered POI Name}` como valor.

>[!TIP]
>
>Se pueden configurar reglas de procesamiento de Analytics para recoger estos datos de contexto. Para obtener más información, consulte [Reglas de procesamiento](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-processing-rules.html). En el ejemplo de *Crear una acción*, la acción enviará la variable `poiname` como contexto para describir el evento de entrada de puntos de interés que se envía a Analytics.

![creación de una acción](/help/assets/configure-action.png)

Este es un ejemplo de la regla completa:

![regla completada](/help/assets/create-a-rule.png)

## Creación de un mensaje en la aplicación en Mobile Services

Como parte de los parámetros de Déclencheur, puede crear la audiencia para el mensaje con datos del servicio Places de una de las siguientes maneras:

* Uso de acciones específicas de la ubicación, como una entrada o una salida.
* Uso de metadatos de puntos de interés que se envían como datos de contexto para reducir el público objetivo.

   Esta opción se puede utilizar con una acción específica de la ubicación, como una entrada, o puede utilizarse como contexto para otro evento, como un inicio o un clic en un botón.

   Este es un ejemplo de cómo configurar un mensaje en la aplicación para dar la bienvenida a los usuarios que especifican un punto de interés que tiene **[!UICONTROL Adobe]** en el nombre:

   ![parámetros de déclencheur](/help/assets/trigger-parameters.png)

* Parámetros en los encabezados Servicio de Places en la *Déclencheur y rasgos* en Mobile Services no funcionan con los datos del servicio Places.

   Estos parámetros solo son para la base de datos heredada de Places Service creada en Mobile Services.
