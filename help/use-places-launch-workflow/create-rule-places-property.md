---
title: Creación de una regla para la propiedad Servicio de lugares
description: 'El SDK de lugares realiza un seguimiento de la ubicación actual, supervisa los puntos de interés configurados en la ubicación actual y realiza un seguimiento de los eventos de entrada y salida de estos puntos de interés. '
translation-type: tm+mt
source-git-commit: c22efc36f2eac6b20fc555d998c3988d8c31169e
workflow-type: tm+mt
source-wordcount: '866'
ht-degree: 7%

---


# Crear reglas de entrada y salida {#create-entry-exit-rules}

Con la extensión Places y las extensiones Places Monitor instaladas en la aplicación móvil, puede crear reglas en Adobe Experience Platform Launch que se activen o acondicionen los datos de ubicación, incluidos los eventos de entrada y salida de ubicación.

## Reglas

Puede configurar una regla, compuesta por un evento, una condición y una acción. Cada regla se compone de lo siguiente:

* Uno o más eventos
* (Opcional) condiciones
* Una o más acciones

### Eventos de servicio de lugares

Coloca las ofertas del servicio en los siguientes eventos en los que puede ejecutar una regla:

* **Introduzca el punto de interés**, que se activa con el SDK de lugares cuando el cliente entra en el punto de interés configurado.
* **Salir del punto de interés**, que se activa mediante el SDK de lugares cuando el cliente sale del punto de interés que ha configurado.

### Condiciones de servicio de lugares

Las condiciones definen los criterios que deben cumplir los datos asociados con el evento, o el estado compartido de una extensión en ese caso, para que se realice la acción. Por ejemplo, puede establecer una condición para activar una acción en una entrada a una cafetería solo en la ciudad de San Francisco.

El SDK de lugares mantiene los siguientes estados:

* El punto de interés actual, que hace referencia al punto de interés en el que se encuentra su cliente.
* Último punto de interés de salida, que hace referencia al punto de interés más reciente que salió su cliente.
* Último punto de interés especificado, que hace referencia al punto de interés más reciente que ha introducido el cliente.

Cada punto de interés contiene los siguientes elementos de datos:

* ID
* Nombre
* Latitud/longitud
* Radio
* Metadatos como ciudad, país, estado, categoría

### Acciones

Las acciones definen lo que la aplicación hará en respuesta a la condición de que la regla se cumpla para el evento activado. Por ejemplo, cuando el cliente entra en el punto de interés, puede configurar un mensaje de bienvenida para que se muestre en el dispositivo móvil.

## Crear una regla: un ejemplo

>[!CAUTION]
>
>En este ejemplo se entiende que ha creado una biblioteca de puntos de interés de todos los cafés de Estados Unidos. For more information about creating POIs and libraries, see [Create a POI](/help/poi-mgmt-ui/create-a-poi-ui.md) and *Create a Library* in [Manage multiple libraries](https://docs.adobe.com/content/help/en/places/using/poi-mgmt-ui/manage-libraries-in-the-places-ui.html).

El siguiente procedimiento es un ejemplo de cómo crear una regla que devuelve un anuncio al Slack al entrar en una cafetería de San Francisco.

El evento, la condición y la acción se definen de las siguientes maneras:

* **Evento**: Coloca el evento de entrada.
* **Condición**: La ciudad del **Punto de interés actual** es San Francisco
* **Acción**: Envíe un postback al Slack con el nombre de la cafetería en la que ha ingresado el cliente.

### Requisitos previos

Antes de crear una regla, debe crear un elemento de datos en Adobe Experience Platform Launch. Los elementos de datos rellenan automáticamente la información necesaria sobre el punto de interés en el mensaje de postback.

Para crear un elemento de datos en el Experience Platform Launch:

1. Haga clic en la ficha Elementos **de datos** .
1. Click **Add Data Element**.
1. Escriba un nombre, por ejemplo, **Nombre** de la cafetería actual.
1. En la lista desplegable **Extensión** , seleccione **Lugares - Beta**.
1. En **Elemento de datos**, seleccione **Ciudad**.
1. En el panel derecho, seleccione el punto de interés **actual**.
1. Haga clic en **Guardar**.

### Crear una regla en Experience Platform Launch para el servicio de lugares

![creación de una regla](/help/assets/placesrule.png)

1. In Experience Platform Launch, click the **[!UICONTROL Rules]** tab.
1. Haga clic en **[!UICONTROL Add Rule]**.
1. Escriba un nombre para la regla, por ejemplo **[!UICONTROL Track entry for coffee shop in SF]**.

### Cree un evento

1. En la sección Eventos, haga clic en **[!UICONTROL + Add]**. Los eventos determinan cuándo desea que se active la regla.
1. En la lista **[!UICONTROL Extension]** desplegable, seleccione **[!UICONTROL Places – Beta]**.
1. En la lista **[!UICONTROL Event Type]** desplegable, seleccione **[!UICONTROL Enter POI]**.
1. En **[!UICONTROL Name]**, introduzca un nombre para el evento, por ejemplo, **[!UICONTROL Entering a coffee shop]**.
1. Haga clic en **[!UICONTROL Keep Changes]**.

### Creación de una condición

1. En la sección Condiciones, haga clic en **[!UICONTROL +Add]**. Las condiciones determinan los criterios que deben cumplirse para la adopción de medidas.
1. In **[!UICONTROL Logic Type]**, select Regular, which allows actions to execute if the condition is met.
1. En la lista **[!UICONTROL Extension]** desplegable, seleccione **[!UICONTROL Places – Beta]**.
1. En **[!UICONTROL Condition Type]**, seleccione **[!UICONTROL City]**.
1. Escriba un nombre de condición, por ejemplo **[!UICONTROL Coffee shop in SF]**.
1. In the right pane, click **[!UICONTROL Current POI]**, and in the drop-down list, select **[!UICONTROL San Francisco]** as one of your cities.
1. Haga clic en **[!UICONTROL Keep Changes]**.

### Creación de una acción

1. In the **[!UICONTROL Actions]** section, click **[!UICONTROL + Add]**.
1. En la lista **[!UICONTROL Extension]** desplegable, deje seleccionada la **[!UICONTROL Mobile Core]** opción predeterminada.
1. Seleccione un tipo de acción, por ejemplo **[!UICONTROL Send Postback]**.

   a. En **[!UICONTROL URL]**, escriba la URL de postback para Slack, por ejemplo, `https://hooks.slack.com/services/`.

   b. Para enviar un cuerpo de anuncio, active la **[!UICONTROL Add Post Body]** casilla de verificación.

   c. En **[!UICONTROL Post Body]**, agregue el cuerpo de la publicación, por ejemplo: `{ "text": "A customer has entered" }`

   c. Escriba un tipo de contenido, por ejemplo **[!UICONTROL application/json]**.

   d. Seleccione un valor de tiempo de espera, por ejemplo, **[!UICONTROL 5]**.

1. Haga clic en **[!UICONTROL Keep Changes]**.

### Publicar la regla

1. Para activar la regla, debe publicarla. Para obtener más información sobre la publicación de la regla en Experience Platform Launch, consulte [Publicación](https://docs.adobe.com/content/help/es-ES/launch/using/reference/publish/overview.html).

### Pensar más allá de las entradas y salidas

El uso de las entradas y salidas de la cerca geográfica del servicio de lugares para activar reglas en Experience Platform Launch es increíblemente potente, pero también puede utilizar los datos de ubicación como condición para que otros eventos se activen. Por ejemplo, puede tener un activador de evento de seguimiento de Mobile Core listo para activarse en función de un evento de llamada trackAction concreto dentro de la aplicación. En función de este evento, puede colocar condiciones de ubicación adicionales en el evento antes de realizar una acción. Por ejemplo, abra una encuesta en la aplicación cuando se produzca un evento de compra, pero `trackAction` solo **** si la ubicación actual del usuario incluye metadatos específicos de Places Service.

![crear una condición](/help/assets/places-condition.png)