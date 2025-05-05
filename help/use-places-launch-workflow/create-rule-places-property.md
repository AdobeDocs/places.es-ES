---
title: Creación de una regla para la propiedad del servicio de Places
description: El SDK de Places realiza un seguimiento de la ubicación actual, supervisa los puntos de interés configurados en torno a la ubicación actual y realiza un seguimiento de los eventos de entrada y salida de estos puntos de interés.
exl-id: dd5aa7ac-55f9-44dc-8632-e483ef3b91a0
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '911'
ht-degree: 12%

---

# Crear reglas de entrada y salida {#create-entry-exit-rules}

Con la extensión Places y una solución de monitorización de región instalada en la aplicación móvil, puede crear reglas en Adobe Experience Platform Launch que se activen o condicionen datos de ubicación, incluidos eventos de entrada y salida de ubicación.

## Reglas

Puede configurar una regla, que está compuesta por un evento, una condición y una acción. Cada regla consta de lo siguiente:

* Uno o más eventos
* Condiciones (opcionales)
* Una o más acciones

### Eventos de servicio de Places

El servicio Places ofrece los siguientes eventos en los que puede ejecutar una regla:

* **Especifique el punto de interés**, que el SDK de Places activa cuando el cliente introduce el punto de interés que configuró.
* **Punto de interés de salida**, que se activa mediante el SDK de Places cuando el cliente sale del punto de interés que configuró.

### Condiciones del servicio de Places

Las condiciones definen los criterios que deben cumplir los datos asociados con el evento o el estado compartido de una extensión en esa instancia para que se realice la acción. Por ejemplo, puede establecer una condición para almacenar en déclencheur una acción en una entrada a una cafetería solo en la ciudad de San Francisco.

El SDK de Places mantiene los siguientes estados:

* Punto de interés actual, que hace referencia al punto de interés en el que se encuentra actualmente su cliente.
* Último punto de interés de salida, que hace referencia al punto de interés más reciente del que salió su cliente.
* Último punto de interés, que hace referencia al punto de interés más reciente introducido por el cliente.

Cada POI contiene los siguientes elementos de datos:

* ID
* Nombre
* Latitud/longitud
* Radio
* Metadatos como ciudad, país, estado y categoría

### Acciones

Las acciones definen qué hará la aplicación en respuesta a la condición de que la regla se cumpla para el evento activado. Por ejemplo, cuando el cliente introduce el punto de interés, puede configurar un mensaje de bienvenida para que se muestre en su dispositivo móvil.

## Creación de una regla: un ejemplo

>[!CAUTION]
>
>En este ejemplo se entiende que ha creado una biblioteca de puntos de interés de todos los cafés de Estados Unidos. Para obtener más información sobre cómo crear puntos de interés y bibliotecas, consulte [Crear un punto de interés](/help/poi-mgmt-ui/create-a-poi-ui.md) y *Crear una biblioteca* en [Administrar varias bibliotecas](https://experienceleague.adobe.com/docs/places/using/poi-mgmt-ui/manage-libraries-in-the-places-ui.html?lang=es).

El siguiente procedimiento es un ejemplo de cómo crear una regla que devuelve una publicación a Slack cuando se entra en una cafetería de San Francisco.

El evento, la condición y la acción se definen de las siguientes maneras:

* **Evento**: Evento de entrada de Places.
* **Condición**: La ciudad del **Punto de interés actual** es San Francisco
* **Acción**: envía un postback al Slack con el nombre de la cafetería que tu cliente ingresó.

### Requisito previo

Antes de crear una regla, debe crear un elemento de datos en Adobe Experience Platform Launch. Los elementos de datos rellenan automáticamente la información necesaria sobre su punto de interés en el mensaje de postback.

Para crear un elemento de datos en Experience Platform Launch:

1. Haga clic en la ficha **Elementos de datos**.
1. Haga clic en **Agregar elemento de datos**.
1. Escriba un nombre, por ejemplo, **Nombre actual de la cafetería**.
1. En la lista desplegable **Extensión**, seleccione **Places - Beta**.
1. En **Elemento de datos**, seleccione **Ciudad**.
1. En el panel derecho, seleccione **Punto de interés actual**.
1. Haga clic en **Guardar**.

### Creación de una regla en Experience Platform Launch para el servicio de Places

![creando una regla](/help/assets/placesrule.png)

1. En Experience Platform Launch, haga clic en la pestaña **[!UICONTROL Reglas]**.
1. Haga clic en **[!UICONTROL Agregar regla]**.
1. Escriba un nombre para la regla, por ejemplo, **[!UICONTROL Rastrear entrada para café en SF]**.

### Creación de un evento

1. En la sección Eventos, haga clic en **[!UICONTROL + Agregar]**. Los eventos determinan cuándo desea que se active la regla.
1. En la lista desplegable **[!UICONTROL Extensión]**, seleccione **[!UICONTROL Places - Beta]**.
1. En la lista desplegable **[!UICONTROL Tipo de evento]**, seleccione **[!UICONTROL Introducir punto de interés]**.
1. En **[!UICONTROL Nombre]**, escriba un nombre para el evento, por ejemplo, **[!UICONTROL Entrar en un café]**.
1. Haga clic en **[!UICONTROL Conservar cambios]**.

### Creación de una condición

1. En la sección Condiciones, haga clic en **[!UICONTROL +Agregar]**. Las condiciones determinan qué criterios deben cumplirse para que se realice la acción.
1. En **[!UICONTROL Tipo de lógica]**, seleccione Normal, que permite que las acciones se ejecuten si se cumple la condición.
1. En la lista desplegable **[!UICONTROL Extensión]**, seleccione **[!UICONTROL Places - Beta]**.
1. En **[!UICONTROL Tipo de condición]**, seleccione **[!UICONTROL Ciudad]**.
1. Escriba un nombre de condición, por ejemplo, **[!UICONTROL Café en SF]**.
1. En el panel derecho, haga clic en el **[!UICONTROL Punto de interés actual]** y, en la lista desplegable, seleccione **[!UICONTROL San Francisco]** como una de sus ciudades.
1. Haga clic en **[!UICONTROL Conservar cambios]**.

### Creación de una acción

1. En la sección **[!UICONTROL Acciones]**, haga clic en **[!UICONTROL + Agregar]**.
1. En la lista desplegable **[!UICONTROL Extension]**, deje seleccionada la opción predeterminada **[!UICONTROL Mobile Core]**.
1. Seleccione un tipo de acción, por ejemplo, **[!UICONTROL Enviar postback]**.

   a. En **[!UICONTROL URL]**, escriba la URL de postback para el Slack, por ejemplo, `https://hooks.slack.com/services/`.

   b. Para enviar un cuerpo de publicación, active la casilla **[!UICONTROL Agregar cuerpo de Post]**.

   c. En **[!UICONTROL Post Body]**, agregue el cuerpo del anuncio, por ejemplo: `{ "text": "A customer has entered" }`

   c. Escriba un tipo de contenido, por ejemplo **[!UICONTROL application/json]**.

   d. Seleccione un valor de tiempo de espera, por ejemplo, **[!UICONTROL 5]**.

1. Haga clic en **[!UICONTROL Conservar cambios]**.

### Publish la regla

1. Para activar la regla, debe publicarla. Para obtener más información sobre cómo publicar la regla en Experience Platform Launch, consulte [Publicación](https://experienceleague.adobe.com/docs/experience-platform/tags/publish/overview.html?lang=es).

### Pensar más allá de entradas y salidas

El uso de entradas y salidas de geoperímetro del servicio Places en las reglas de déclencheur en Experience Platform Launch es increíblemente eficaz, pero también puede utilizar los datos de ubicación como condición para que se activen otros eventos. Por ejemplo, puede tener un déclencheur de eventos de seguimiento de acciones principal móvil listo para activarse en función de un evento de llamada trackAction concreto dentro de la aplicación. En función de este evento, puede colocar condiciones de ubicación adicionales al evento antes de que se realice una acción. Por ejemplo, abra una encuesta en la aplicación cuando se produzca un evento purchase `trackAction`, pero **solo** si la ubicación actual del usuario incluye metadatos específicos de Places Service.

![crear una condición](/help/assets/places-condition.png)
