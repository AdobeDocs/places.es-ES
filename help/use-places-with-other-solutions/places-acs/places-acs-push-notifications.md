---
title: Notificaciones push con el servicio de lugares
description: Esta sección proporciona información sobre cómo utilizar el servicio de lugares con notificaciones push en Campaign Standard.
translation-type: tm+mt
source-git-commit: 5a21e734c0ef56c815389a9f08b445bedaae557a

---


# Notificaciones push con el servicio de lugares {#push-notifications}

En esta sección, aprenderá a utilizar la información de ubicación geográfica histórica para dirigir las notificaciones push que se envían a través de Adobe Campaign Standard.

## Requisitos previos

Antes de comenzar, complete las siguientes tareas:

* Tenga una aplicación móvil configurada con el SDK de Adobe Experience Platform Mobile, incluida la extensión [de](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)Adobe Campaign Standard.

* Integre el SDK [de](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) Adobe Experience Platform Mobile en la aplicación.
* Agregue [Adobe Campaign Standard Extension](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) a la configuración de la aplicación móvil.

* [Cree un punto de interés](/help/poi-mgmt-ui/create-a-poi-ui.md) en la interfaz de administración de puntos de interés del servicio de lugares.

* Habilite e instale la extensión [Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).


## Creación de elementos de datos en el lanzamiento de la plataforma de experiencia

Después de comprobar que la extensión Lugares y la extensión Monitor de lugares funcionan correctamente en la aplicación, debe crear elementos de datos en Inicio de plataforma de experiencia. Los elementos de datos le permiten leer la información proporcionada por las extensiones que provienen del centro de eventos del SDK móvil y actuar como alias para recuperar datos de la aplicación cliente. Para recuperar datos de las extensiones de lugares y enviar la información del servicio de lugares a Campaign, debe crear algunos elementos de datos.

Para crear un elemento de datos:

1. En la propiedad móvil Inicio de plataforma de experiencia, haga clic en la **[!UICONTROL Data Elements]**ficha y, a continuación, en**[!UICONTROLA Agregar elemento]**de datos.
1. En la lista **[!UICONTROL Extension]**desplegable, seleccione**[!UICONTROL Places Service]**.
1. En la lista **[!UICONTROL Data Element Type]**desplegable, seleccione**[!UICONTROL Name]**.
1. En el panel del lado derecho, puede seleccionar **[!UICONTROL Current POI]**qué recupera el nombre del punto de interés en el que se encuentra el usuario.

   **[!UICONTROL Last Entered]**recupera el nombre del punto de interés que el usuario introdujo por última vez y**[!UICONTROL Last Exited]** proporciona el nombre del punto de interés que el usuario dejó por última vez. En este ejemplo, hemos seleccionado **[!UICONTROL Last Entered]**y escrito un nombre para el elemento de datos, como**[!UICONTROL Last Entered POI Name]** y hemos hecho clic en **[!UICONTROL Save]**.

   ![&quot;Mensajería push en Campaign Standard&quot;](/help/assets/ACS_Push1.png)

1. Repeat the steps 1-4 above and create data elements for *Last Entered POI Latitude*, *Last Entered POI Longitude*, and *Last Entered POI Radius*.

Además de los elementos de datos para el servicio de lugares, asegúrese de crear elementos de datos de Mobile Core para el ID *de* aplicación y el ID *de* Experience Cloud.

## Crear una regla para enviar datos de ubicación a Adobe Campaign Standard

Las reglas de Inicio de plataforma de experiencia le permiten crear flujos de trabajo complejos con varias soluciones basados en desencadenadores de eventos. Con las reglas, puede crear nuevas reglas o modificar las existentes y hacer que las actualizaciones se implementen de forma dinámica en las aplicaciones móviles. En el siguiente ejemplo, la regla se activará cuando un usuario entre en un punto de interés protegido geográficamente. Después de activar la regla, se envía una actualización a Campaign Standard para registrar una entrada en un punto de interés específico para un usuario en particular según el ID de Experience Cloud.

1. En la propiedad móvil de inicio de plataforma de experiencia, en la **[!UICONTROL Rules]**ficha, haga clic en**[!UICONTROL Add Rule]**.
1. En la **[!UICONTROL Events]**sección, haga clic**[!UICONTROL +]** y seleccione **[!UICONTROL Places Service]**como extensión.
1. For the **[!UICONTROL Event Type]**, select**[!UICONTROL Enter POI]**.
1. Asigne un nombre a la regla; por ejemplo, **el usuario ha introducido un punto de interés**.
1. Haga clic en **[!UICONTROL Keep Changes]**.
1. Deje la **[!UICONTROL Conditions]**sección en blanco.

   Esta sección le permite filtrar o establecer restricciones en el momento en que esta regla debe activarse.

1. En la **[!UICONTROL Actions]**sección, haga clic en**[!UICONTROL +]**.
1. En la lista **[!UICONTROL Extension]**desplegable, seleccione**[!UICONTROL Mobile Core]** y, en la lista **[!UICONTROL Action Type]**desplegable, seleccione**[!UICONTROL Send Postback]**.
1. En **[!UICONTROL URL]**, debe construir el punto final de ubicaciones de Campaign Standard.

   La dirección URL debe tener un aspecto similar a `https:///rest/head/mobileAppV5//locations/`.
Asegúrese de utilizar los elementos de datos correctos que creó anteriormente para el servidor de Campaign y la clave.

1. Haga clic en el cuadro para agregar un cuerpo de anuncio y enviar lo siguiente:

   ```
   {
    "locationData": {
    "distances": "{%%Last Entered POI Radius%%}",
    "poiLabel": "{%%Last Entered POI Name%%}",
    "latitude": "{%%Last Entered POI Lat%%}",
    "longitude": "{%%Last Entered POI Long%%}",
    "appId": "{%%AppID%%}",
    "marketingCloudId": “{%%ecid%%}”
    }
   }
   ```

1. Asegúrese de utilizar los elementos de datos que creó en la sección anterior.
1. En **[!UICONTROL Content Type]**, escriba**[!UICONTROL application/json]**.
1. Haga clic en **[!UICONTROL Keep Changes]**.

>[!IMPORTANT]
>
>* Podría resultar útil configurar un enlace web de Slack como una acción adicional para validar que las entradas se están activando y que se están recopilando los datos correctos.
>* Recuerde publicar los cambios recientes en la aplicación para asegurarse de que la regla y todos los elementos de datos se implementan como parte de la configuración. Después de publicar, vuelva a iniciar la aplicación móvil para obtener las últimas actualizaciones de configuración.


## Utilizar los datos de ubicación para dirigir los mensajes de campaña

Ahora que los datos de ubicación se han rellenado en Campaign, podemos utilizar los puntos de interés como herramienta de segmentos de audiencia.

1. En la instancia de Adobe Campaign Standard, haga clic en **[!UICONTROL Create Push Notification]**.
1. Para el tipo de notificación push, seleccione **[!UICONTROL Send push to Campaign profiles]**.
1. Haga clic **[!UICONTROL Next]**y escriba los detalles generales.
1. En la pantalla Audiencia, haga clic **[!UICONTROL Count]**para determinar cuántos usuarios estimados se enviarán las notificaciones push.

   >[!TIP]
   >
   >En este ejemplo, el recuento será 3, porque hay tres dispositivos instalados en los que se está probando la aplicación.

1. En el panel izquierdo, expanda la **[!UICONTROL Profile]**ficha y arrastre el**[!UICONTROL POI location]** filtro al área principal.
1. En la ventana de filtro de puntos de interés, introduzca el nombre exacto del punto de interés que desea establecer como objetivo.

   >[!TIP]
   >
   >Puede realizar selecciones adicionales para determinar el período de tiempo transcurrido desde la visita anterior del usuario a este punto de interés.

   ![&quot;Mensajería push 2 en ACS&quot;](/help/assets/ACS_push2.png)

1. Haga clic en **[!UICONTROL Confirm]**.
1. Vuelva a ejecutar el recuento en la parte superior para ver cómo cambia el tamaño de la audiencia.

   Si no ve la actualización de recuento, es posible que haya introducido un nombre de punto de interés para el que ningún dispositivo ha activado una entrada. Tener el enlace web Slack se vuelve valioso en esta situación, ya que puede ver una lista de entradas de POI de varios dispositivos de prueba.

1. Puede arrastrar filtros de ubicación de puntos de interés adicionales para incluir varios puntos de interés en el mensaje.
1. Click **[!UICONTROL Next]**to finish creating the push notification for delivery.

   ![&quot;Mensajería push 3 en ACS&quot;](/help/assets/ACS_push3.png)

El uso del servicio de lugares con Adobe Campaign Standard le proporciona una poderosa herramienta para segmentar y dirigir sus mensajes a los usuarios en función de las entradas y salidas de la valla geográfica. Esta integración le ayuda a crear casos de uso más personalizados y contextuales.