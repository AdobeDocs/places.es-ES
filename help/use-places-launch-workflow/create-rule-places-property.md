---
title: Creación de una regla para la propiedad Places
seo-title: Creación de una regla para la propiedad Places
description: 'El SDK de Places realiza un seguimiento de la ubicación actual, supervisa los puntos de interés configurados en torno a la ubicación actual y rastrea los eventos de entrada y salida de estos puntos de interés. '
seo-description: 'El SDK de Places realiza un seguimiento de la ubicación actual, supervisa los puntos de interés configurados en torno a la ubicación actual y rastrea los eventos de entrada y salida de estos puntos de interés. '
translation-type: tm+mt
source-git-commit: 9feb88f1ccec83c96d08ac5bd48e43d7d9c247c8

---


# Crear reglas de entrada y salida {#create-entry-exit-rules}

Con las extensiones del monitor de lugares y lugares instaladas en la aplicación móvil, puede crear reglas en Adobe Experience Platform Launch que se activen o condicionen los datos de ubicación, incluidos los eventos de entrada y salida de ubicación de lugares.

## Reglas

Puede configurar una regla, compuesta por un evento, una condición y una acción. Cada regla se compone de lo siguiente:

* Uno o más eventos
* (Opcional) condiciones
* Una o más acciones

### Coloca eventos

Places ofrece los siguientes eventos en los que puede ejecutar una regla:

* **Introduzca el punto de interés**, que se activa con el SDK de lugares cuando el cliente entra en el punto de interés configurado.
* **Salir del punto de interés**, que se activa mediante el SDK de lugares cuando el cliente sale del punto de interés que ha configurado.

### Condiciones de ubicación

Las condiciones definen los criterios que deben cumplir los datos asociados con el evento o el estado compartido de una extensión en esa instancia para que se realice la acción. Por ejemplo, puede establecer una condición para activar una acción en una entrada a una cafetería solo en la ciudad de San Francisco.

El SDK de lugares mantiene los siguientes estados:

* El punto de interés actual, que hace referencia al punto de interés en el que se encuentra su cliente.
* Último punto de interés de salida, que hace referencia al punto de interés más reciente que salió su cliente.
* Último punto de interés especificado, que hace referencia al punto de interés más reciente que ha introducido el cliente.

Cada punto de interés contiene los siguientes elementos de datos:

* ID
* Nombre:
* Latitud/longitud
* Radio
* Metadatos como ciudad, país, estado, categoría

### Acciones

Las acciones definen lo que la aplicación hará en respuesta a la condición de que la regla se cumpla para el evento activado. Por ejemplo, cuando el cliente entra en el punto de interés, puede configurar un mensaje de bienvenida para que se muestre en el dispositivo móvil.

## Crear una regla: un ejemplo

>[!CAUTION]
>
>En este ejemplo se asume que ha creado una biblioteca de puntos de interés de todas las cafeterías de Estados Unidos. Para obtener más información sobre la creación de puntos de interés y bibliotecas, consulte [Creación de un punto de interés](https://placesdocs.com/places-services-by-adobe-documentation/places-database-management-1/managing-pois-in-the-places-ui#create-a-poi) y [Creación de una biblioteca](https://placesdocs.com/places-services-by-adobe-documentation/places-database-management-1/manage-libraries#create-a-library).

El siguiente procedimiento es un ejemplo de cómo crear una regla que devuelve un anuncio a Slack cuando se entra en una cafetería en San Francisco.

El evento, la condición y la acción se definen de las siguientes maneras:

* **Evento**: Coloca el evento de entrada.
* **Condición**: Ciudad para el **actual punto de interés** es San Francisco
* **Acción**: Envíe un postback a Slack el nombre de la cafetería en la que entró su cliente.

### Requisitos previos

Antes de crear una regla, debe crear un elemento de datos en Adobe Experience Platform Launch. Los elementos de datos rellenan automáticamente la información necesaria sobre el punto de interés en el mensaje de postback.

Para crear un elemento de datos en Inicio de plataforma de experiencia:

1. Haga clic en la ficha Elementos **de datos** .
2. Click **Add Data Element**.
3. Escriba un nombre, por ejemplo, **Nombre** de la cafetería actual.
4. En la lista desplegable **Extensión** , seleccione **Lugares - Beta**.
5. En Elemento **** de datos, seleccione **Ciudad**.
6. En el panel derecho, seleccione el punto de interés **actual**.
7. Haga clic en **Guardar**.

### Crear una regla en Inicio de plataforma de experiencia para lugares

![el proceso de creación de una regla](/help/assets/placesrule.png)

1. En Inicio de plataforma de experiencia, haga clic en la **[!UICONTROL Rules]** ficha .
2. Haga clic en **[!UICONTROL Add Rule]**.
3. Escriba un nombre para la regla, por ejemplo **[!UICONTROL Track entry for coffee shop in SF]**.

### Cree un evento

1. En la sección Eventos, haga clic en **[!UICONTROL + Add]**. Los eventos determinan cuándo desea que se active la regla.
2. En la lista **[!UICONTROL Extension]** desplegable, seleccione **[!UICONTROL Places – Beta]**.
3. En la lista **[!UICONTROL Event Type]** desplegable, seleccione **[!UICONTROL Enter POI]**.
4. En **[!UICONTROL Name]**, introduzca un nombre para el evento, por ejemplo, **[!UICONTROL Entering a coffee shop]**.
5. Haga clic en **[!UICONTROL Keep Changes]**.

### Creación de una condición

1. En la sección Condiciones, haga clic en **[!UICONTROL +Add]**. Las condiciones determinan los criterios que deben cumplirse para la adopción de medidas.
2. En **[!UICONTROL Logic Type]**, seleccione Regular, que permite que las acciones se ejecuten si se cumple la condición.
3. En la lista **[!UICONTROL Extension]** desplegable, seleccione **[!UICONTROL Places – Beta]**.
4. En **[!UICONTROL Condition Type]**, seleccione **[!UICONTROL City]**.
5. Type a condition name, for example, **[!UICONTROL Coffee shop in SF]**.
6. En el panel derecho, haga clic en **[!UICONTROL Current POI]** y, en la lista desplegable, seleccione **[!UICONTROL San Francisco]** como una de sus ciudades.
7. Haga clic en **[!UICONTROL Keep Changes]**.

### Creación de una acción

1. In the **[!UICONTROL Actions]** section, click **[!UICONTROL + Add]**.
2. En la lista **[!UICONTROL Extension]** desplegable, deje seleccionada la **[!UICONTROL Mobile Core]** opción predeterminada.
3. Seleccione un tipo de acción, por ejemplo **[!UICONTROL Send Postback]**.

   a. En **[!UICONTROL URL]**, escriba la URL de postback para Slack, por ejemplo, `https://hooks.slack.com/services/`.

   b. Para enviar un cuerpo de anuncio, active la **[!UICONTROL Add Post Body]** casilla de verificación.

   c. En **[!UICONTROL Post Body]**, agregue el cuerpo de la publicación, por ejemplo: `{ "text": "A customer has entered" }`

   c. Escriba un tipo de contenido, por ejemplo **[!UICONTROL application/json]**.

   d. Seleccione un valor de tiempo de espera, por ejemplo, **[!UICONTROL 5]**.

4. Haga clic en **[!UICONTROL Keep Changes]**.

### Publicar la regla

1. Para activar la regla, debe publicarla. Para obtener más información sobre la publicación de la regla en Inicio de plataforma de experiencia, consulte [Publicación](https://docs.adobelaunch.com/launch-reference/publishing).

### Pensar más allá de las entradas y salidas

El uso de entradas y salidas de geo-valla de Lugares para activar reglas en Launch es increíblemente potente, pero también puede utilizar los datos de ubicación como condición para que otros eventos se activen. Por ejemplo, puede tener un activador de evento de seguimiento de Mobile Core Action listo para activarse en función de un evento de llamada trackAction concreto dentro de la aplicación. En función de este evento, puede colocar condiciones de ubicación adicionales en el evento antes de realizar una acción. Por ejemplo, abra un estudio en la aplicación cuando se produzca un evento de compra, pero `trackAction` solo **** si la ubicación actual del usuario incluye metadatos específicos del servicio de ubicación.

![crear una condición](/help/assets/places-condition.png)