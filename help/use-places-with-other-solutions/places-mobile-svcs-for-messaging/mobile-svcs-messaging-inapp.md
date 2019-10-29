---
title: Mensajería en la aplicación
seo-title: Mensajería en la aplicación
description: Esta sección muestra cómo utilizar los mensajes en la aplicación en lugares.
seo-description: Esta sección muestra cómo utilizar los mensajes en la aplicación en lugares.
translation-type: tm+mt
source-git-commit: 7985943cef606525401983c4c80862c277f41bf0

---


# Notificaciones en la aplicación (#places-push-messaging)

Cómo configurar los mensajes en la aplicación para que se activen desde los eventos de lugares; los mensajes deben estar en una visita de Analytics.

## Mensaje en la aplicación

AMS le permite utilizar los datos de ubicación que se envían a Analytics como evento o condición desencadenador de un mensaje en la aplicación. Los mensajes en la aplicación pueden aparecer para el usuario en tiempo real tan pronto como el activador se active desde el SDK y no es necesario esperar a que Analytics procese los datos.

Notificaciones locales: La mensajería en la aplicación tiene tres tipos diferentes:

* Pantalla completa
* Alerta
* Notificaciones locales.

Estos tipos se consideran mensajes en la aplicación porque los activa el SDK, pero es importante tener en cuenta que las notificaciones locales parecen notificaciones push, ya que aparecen mientras la aplicación no está en primer plano. Las notificaciones locales son una excelente opción para enviar notificaciones en tiempo real a los usuarios a medida que entran o salen de los puntos de interés mientras la aplicación está en segundo plano. Consulte la documentación de la extensión del monitor de lugares para conocer la supervisión de la ubicación (https://placesdocs.com/places-services-by-adobe-documentation/configure-places-in-the-sdk/places-monitor-extension).

### Requisitos previos

* Conozca cómo enviar y crear un mensaje en la aplicación en AMS y cómo funcionan los activadores.

   Para obtener más información, consulte [Crear un mensaje en la aplicación](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/inapp-messages/t-in-app-message.html).


## Creación de una regla en Inicio de plataforma de experiencia

Cree reglas de inicio que envíen los datos correctos a Analytics que desee que puedan utilizarse como parte de las reglas de activador de mensajes en la aplicación. Puede utilizar los datos de las extensiones Lugares en las reglas de lanzamiento como eventos y/o condiciones según el caso de uso.

* Uso de los datos de ubicación como evento desencadenador. Por ejemplo, si desea enviar datos a Analytics cuando un usuario introduce un punto de interés.

* Uso de datos de ubicación como condición para un evento de activación. Por ejemplo, si ha creado una etiqueta de metadatos personalizada en el servicio de ubicación para el tiempo en diferentes puntos de interés, puede usar esos metadatos como parámetro para la condición Regla, como se muestra a continuación. Aunque puede usar esta condición para con el evento de entrada de puntos de interés descrito anteriormente, también puede utilizarlo como contexto para cualquier evento.

Una vez configurada la regla con los parámetros de condición y evento adecuados, finalice la configuración de la regla configurando la acción para enviar datos a Analytics. Para ello:

* Seleccione Adobe Analytics como extensión
* Elija "Track" como tipo de acción
* Determinar un nombre para la acción
* Configure los datos de contexto para que se envíen con el evento. Utilice la interfaz de datos de contexto para asignar elementos de datos de inicio a los nombres clave que desee enviar a Analytics.

Tenga en cuenta que las reglas de procesamiento de Analytics se pueden configurar para recoger estos datos de contexto. Consulte Reglas de procesamiento de Analytics, si es necesario (https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-processing-rules.html)Por ejemplo, esta acción está enviando el nombre del punto como contexto para describir el evento POIentry que se está enviando a Analytics.

![creación de una acción](/help/assets/configure-action.png)

Este es un ejemplo de cómo podría verse la regla terminada.

![regla completada](/help/assets/create-a-rule.png)

## Creación de un mensaje en la aplicación en AMS:

Creará la audiencia para el mensaje con datos del servicio de ubicación como parte de los parámetros de activación.

* Uso de acciones específicas de ubicación como entrada o salida
* Uso de metadatos de puntos de interés que se envían como datos de contexto para reducir el destino de la audiencia. Se puede utilizar con una acción específica de una ubicación, como entrada, o como contexto para otro evento, como un lanzamiento o un clic de botón.

   A continuación se muestra un ejemplo de cómo configurar un mensaje en la aplicación para acoger a los usuarios que introducen un punto de interés que tenga "Adobe" en el nombre:

   ![parámetros desencadenadores](/help/assets/trigger-parameters.png)

* Los parámetros que se encuentran en los encabezados "Lugares" de los activadores y características de AMS no funcionan con los datos del servicio de ubicación. Estos parámetros son para la base de datos heredada Places creada en AMS.