---
title: Creación de una regla para la propiedad Servicio de Places
description: El SDK de Places realiza un seguimiento de la ubicación actual, supervisa los puntos de interés configurados en torno a la ubicación actual y rastrea los eventos de entrada y salida para estos puntos de interés.
exl-id: dd5aa7ac-55f9-44dc-8632-e483ef3b91a0
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '927'
ht-degree: 15%

---

# Crear reglas de entrada y salida {#create-entry-exit-rules}

Con la extensión Places y una solución de monitorización de región instalada en la aplicación móvil, puede crear reglas en Adobe Experience Platform Launch que se activen o condicionen los datos de ubicación, incluidos los eventos de entrada y salida de ubicación.

## Reglas

Puede configurar una regla, que está compuesta por un evento, una condición y una acción. Cada regla está compuesta por lo siguiente:

* Uno o más eventos
* (Opcional) condiciones
* Una o más acciones

### Eventos de servicio de Places

El servicio de Places ofrece los siguientes eventos en los que puede ejecutar una regla:

* **Introducir punto de interés**, que se activa mediante el SDK de Places cuando su cliente introduce el punto de interés que ha configurado.
* **Punto de interés de salida**, que se activa mediante el SDK de Places cuando el cliente abandona el punto de interés configurado.

### Condiciones de servicio de Places

Las condiciones definen los criterios que los datos asociados al evento o el estado compartido de una extensión en esa instancia deben cumplir para que se realice la acción. Por ejemplo, puede establecer una condición para almacenar en déclencheur una acción en una entrada a una cafetería solo en la ciudad de San Francisco.

El SDK de Places mantiene los siguientes estados:

* Punto de interés actual, que hace referencia al punto de interés en el que se encuentra su cliente actualmente.
* Último punto de interés de salida, que hace referencia al punto de interés más reciente que salió su cliente.
* Último punto de interés introducido, que hace referencia al punto de interés más reciente en el que entró su cliente.

Cada punto de interés contiene los siguientes elementos de datos:

* ID
* Nombre
* Latitud y longitud
* Radio
* Metadatos como ciudad, país, estado, categoría

### Acciones

Las acciones definen lo que la aplicación hará en respuesta a la condición de que la regla se cumpla para el evento activado. Por ejemplo, cuando el cliente introduce el punto de interés, puede configurar un mensaje de bienvenida para que se muestre en su dispositivo móvil.

## Crear una regla: un ejemplo

>[!CAUTION]
>
>En este ejemplo se entiende que ha creado una biblioteca de puntos de interés de todos los cafés de Estados Unidos. Para obtener más información sobre la creación de puntos de interés y bibliotecas, consulte [Crear un punto de interés](/help/poi-mgmt-ui/create-a-poi-ui.md) y *Crear una biblioteca* en [Administrar varias bibliotecas](https://docs.adobe.com/content/help/en/places/using/poi-mgmt-ui/manage-libraries-in-the-places-ui.html).

El siguiente procedimiento es un ejemplo de cómo crear una regla que envíe una publicación de vuelta al Slack cuando entre en una cafetería de San Francisco.

El evento, la condición y la acción se definen de las siguientes maneras:

* **Evento**: Coloca el evento de entrada.
* **Condición**: La ciudad del **Punto de interés actual** es San Francisco
* **Acción**: Envíe un postback al Slack con el nombre del café que ingresó su cliente.

### Requisitos previos

Antes de crear una regla, debe crear un elemento de datos en Adobe Experience Platform Launch. Los elementos de datos rellenan automáticamente la información necesaria sobre el punto de interés en el mensaje de postback.

Para crear un elemento de datos en el Experience Platform Launch:

1. Haga clic en el **Elementos de datos** pestaña .
1. Haga clic en **Añadir elemento de datos**.
1. Escriba un nombre, por ejemplo, **Nombre de la cafetería actual**.
1. En el **Extensión** lista desplegable, seleccione **Places: beta**.
1. En **Elemento de datos**, seleccione **Ciudad**.
1. En el panel derecho, seleccione **Punto de interés actual**.
1. Haga clic en **Guardar**.

### Crear una regla en Experience Platform Launch para el servicio Places

![creación de una regla](/help/assets/placesrule.png)

1. En Experience Platform Launch, haga clic en la pestaña **[!UICONTROL Reglas]**.
1. Haga clic en **[!UICONTROL Añadir regla]**.
1. Escriba un nombre para la regla, por ejemplo, **[!UICONTROL Track entry para café en SF]**.

### Cree un evento

1. En la sección Eventos , haga clic en **[!UICONTROL + Agregar]**. Los eventos determinan cuándo desea que se active la regla.
1. En el **[!UICONTROL Extensión]** lista desplegable, seleccione **[!UICONTROL Places: beta]**.
1. En la lista desplegable **[!UICONTROL Tipo de evento]**, seleccione **[!UICONTROL Introducir punto de interés]**.
1. En **[!UICONTROL Nombre]**, escriba un nombre para el evento, por ejemplo, **[!UICONTROL Entrar en un café]**.
1. Haga clic en **[!UICONTROL Mantener cambios]**.

### Creación de una condición

1. En la sección Condiciones , haga clic en **[!UICONTROL +Añadir]**. Las condiciones determinan qué criterios deben cumplirse para que se realice la acción.
1. En **[!UICONTROL Tipo de lógica]**, seleccione Normal, que permite que las acciones se ejecuten si se cumple la condición.
1. En el **[!UICONTROL Extensión]** lista desplegable, seleccione **[!UICONTROL Places: beta]**.
1. En **[!UICONTROL Tipo de condición]**, seleccione **[!UICONTROL Ciudad]**.
1. Escriba un nombre de condición, por ejemplo, **[!UICONTROL Cafetería en SF]**.
1. En el panel derecho, haga clic en el **[!UICONTROL Punto de interés actual]** y, en la lista desplegable, seleccione **[!UICONTROL San Francisco]** como una de sus ciudades.
1. Haga clic en **[!UICONTROL Mantener cambios]**.

### Creación de una acción

1. En el **[!UICONTROL Acciones]** , haga clic en **[!UICONTROL + Agregar]**.
1. En el **[!UICONTROL Extensión]** lista desplegable, deje el valor predeterminado **[!UICONTROL Núcleo móvil]** seleccionada.
1. Seleccione un tipo de acción, por ejemplo, **[!UICONTROL Enviar postback]**.

   a. En **[!UICONTROL URL]**, escriba la URL de postback para el Slack, por ejemplo, `https://hooks.slack.com/services/`.

   b. Para enviar un cuerpo de anuncio, seleccione la opción **[!UICONTROL Agregar cuerpo del anuncio]** en el Navegador.

   c. En **[!UICONTROL Cuerpo del anuncio]**, añada el cuerpo del anuncio, por ejemplo: `{ "text": "A customer has entered" }`

   c. Escriba un tipo de contenido, por ejemplo **[!UICONTROL application/json]**.

   d. Seleccione un valor de tiempo de espera, por ejemplo, **[!UICONTROL 5]**.

1. Haga clic en **[!UICONTROL Mantener cambios]**.

### Publicar la regla

1. Para activar la regla, debe publicarla. Para obtener más información sobre la publicación de la regla en Experience Platform Launch, consulte [Publicación](https://docs.adobe.com/content/help/es-ES/launch/using/reference/publish/overview.html).

### Más allá de las entradas y salidas

El uso en Experience Platform Launch de entradas y salidas de geoperímetro del servicio Places a las reglas de déclencheur es increíblemente potente, pero también puede utilizar los datos de ubicación como condición para que otros eventos se activen. Por ejemplo, podría tener un déclencheur de evento de seguimiento principal de Mobile listo para activarse en función de un evento de llamada trackAction en particular dentro de la aplicación. En función de este evento, se pueden colocar condiciones de ubicación adicionales en el evento antes de realizar una acción. Por ejemplo, abra un estudio en la aplicación cuando realice una compra `trackAction` tiene lugar, pero **only** si la ubicación actual del usuario incluye metadatos específicos de Places Service.

![crear una condición](/help/assets/places-condition.png)
