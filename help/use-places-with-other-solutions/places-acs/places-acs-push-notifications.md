---
title: Notificaciones push
seo-title: Notificaciones push
description: En esta sección se proporciona información sobre cómo utilizar los lugares con notificaciones push en Campaign Standard.
seo-description: 'En esta sección se proporciona información sobre cómo utilizar los lugares con notificaciones push en Campaign Standard. '
translation-type: tm+mt
source-git-commit: a76e91775efd92ce56f2dc5cbdcc65786855b5c3

---


# Notificaciones push con el servicio de ubicación de la plataforma de experiencia {#push-notifications}

En esta guía, mostraremos cómo puede utilizar la información de ubicación geográfica histórica para dirigir las notificaciones push enviadas a través de Adobe Campaign Standard.

## Requisitos previos

Antes de comenzar, complete las siguientes tareas:

* Tenga una aplicación móvil configurada con el SDK de Adobe Experience Platform Mobile, incluida la extensión [de](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)Adobe Campaign Standard.

* Integre el SDK [de](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) Adobe Experience Platform Mobile en la aplicación.
* Agregue [Adobe Campaign Standard Extension](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) a la configuración de la aplicación móvil.

* [Cree un punto de interés](/help/poi-mgmt-ui/create-a-poi-ui.md) en la interfaz de administración del punto de interés de lugares.

* Habilite e instale la extensión [Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).


## Creación de elementos de datos en el lanzamiento de la plataforma de experiencia

Después de comprobar que el Monitor de lugares y ubicaciones para las extensiones de servicio de ubicación funciona correctamente en la aplicación, cree elementos de datos en el Inicio de plataforma de experiencia. Los elementos de datos le permiten leer la información proporcionada por las extensiones que provienen del centro de eventos del SDK móvil y actuar como alias para recuperar datos de la aplicación cliente. Para recuperar datos de las extensiones Lugares y enviar la información Lugares a Campaign, debe crear algunos elementos de datos.

Para crear un elemento de datos:

1. En la propiedad móvil Inicio de plataforma de experiencia, haga clic en la **[!UICONTROL Data Elements]** ficha y, a continuación, en **[!UICONTROLAAgregar elemento]** de datos.
2. En la lista **[!UICONTROL Extension]** desplegable, seleccione **[!UICONTROL Places]**.
3. En la lista **[!UICONTROL Data Element Type]** desplegable, seleccione **[!UICONTROL Name]**.
4. En el panel del lado derecho, puede seleccionar **[!UICONTROL Current POI]** qué recupera el nombre del punto de interés en el que se encuentra el usuario.

   **[!UICONTROL Last Entered]** recupera el nombre del punto de interés que el usuario introdujo por última vez y **[!UICONTROL Last Exited]** proporciona el nombre del último punto de interés que dejó el usuario. Para este ejemplo, seleccionaremos **[!UICONTROL Last Entered]** y escribiremos un nombre para el elemento de datos, como **[!UICONTROL Last Entered POI Name]** y se hará clic en él **[!UICONTROL Save]**.

   !["Mensajería push en Campaign Standard"](/help/assets/ACS_Push1.png)

5. Repita los pasos 1 a 4 anteriores y cree elementos de datos para *Última latitud* de puntos de interés introducida, Longitud *de puntos de interés*&#x200B;última entrada y Radio *de puntos de interés*&#x200B;última entrada.

Además de los elementos de datos del servicio de ubicación, asegúrese de crear elementos de datos principales de Mobile para el ID *de* aplicación y el ID *de* Experience Cloud.

## Crear una regla para enviar datos de ubicación a Adobe Campaign Standard

Las reglas de Inicio de plataforma de experiencia le permiten crear flujos de trabajo complejos con varias soluciones basados en desencadenadores de eventos. Con las reglas, puede crear nuevas reglas o modificar las existentes y hacer que las actualizaciones se implementen de forma dinámica en las aplicaciones móviles. En el siguiente ejemplo, la regla se activará cuando un usuario entre en un punto de interés protegido geográficamente. Después de activar la regla, se envía una actualización a Campaign Standard para registrar una entrada en un punto de interés específico para un usuario en particular según el ID de Experience Cloud.

1. En la propiedad móvil de Launch, en la **[!UICONTROL Rules]** ficha, haga clic en **[!UICONTROL Add Rule]**.
2. En la **[!UICONTROL Events]** sección, haga clic **[!UICONTROL +]** y seleccione **[!UICONTROL Places]** como extensión.
3. For the **[!UICONTROL Event Type]**, select **[!UICONTROL Enter POI]**.
4. Asigne un nombre a la regla; por ejemplo, **el usuario ha introducido un punto de interés**.
5. Haga clic en **[!UICONTROL Keep Changes]**.
6. Deje la **[!UICONTROL Conditions]** sección en blanco.

   Esta sección le permite filtrar o establecer restricciones en el momento en que esta regla debe activarse.

7. En la **[!UICONTROL Actions]** sección, haga clic en **[!UICONTROL +]**.
8. En la lista **[!UICONTROL Extension]** desplegable, seleccione **[!UICONTROL Mobile Core]** y, en la lista **[!UICONTROL Action Type]** desplegable, seleccione **[!UICONTROL Send Postback]**.
9. En **[!UICONTROL URL]**, debe construir el punto final de ubicaciones de Campaign Standard.

   La dirección URL debe tener un aspecto similar a `https:///rest/head/mobileAppV5//locations/`.
Asegúrese de utilizar los elementos de datos correctos que creó anteriormente para el servidor de Campaign y la clave.

10. Haga clic en el cuadro para agregar un cuerpo de anuncio y enviar lo siguiente:

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

11. Asegúrese de utilizar los elementos de datos que creó en la sección anterior.
12. En **[!UICONTROL Content Type]**, escriba **[!UICONTROL application/json]**.
13. Haga clic en **[!UICONTROL Keep Changes]**.

>[!IMPORTANT]
>
>* Podría ser útil tener una configuración de enlace web de Slack como acción adicional para validar que las entradas se estén activando y que se estén recopilando los datos correctos.


>* Recuerde publicar los cambios recientes en la aplicación para asegurarse de que la regla y todos los elementos de datos se implementan como parte de la configuración. Tras la publicación, debe volver a iniciar la aplicación móvil para obtener las últimas actualizaciones de configuración.


## Utilizar los datos de ubicación para dirigir los mensajes de campaña

Ahora que los datos de ubicación se han rellenado en Campaign, podemos utilizar los puntos de interés como herramienta de segmentos de audiencia.

1. En la instancia de Adobe Campaign Standard, haga clic en **[!UICONTROL Create Push Notification]**.
2. Para el tipo de notificación push, seleccione **[!UICONTROL Send push to Campaign profiles]**.
3. Haga clic **[!UICONTROL Next]** y escriba los detalles generales.
4. En la pantalla Audiencia, haga clic **[!UICONTROL Count]** para determinar cuántos usuarios estimados se enviarán las notificaciones push.

   >[!TIP]
   >
   >En este ejemplo, el recuento será 3, porque hay tres dispositivos instalados en los que se está probando la aplicación.

5. En el panel izquierdo, expanda la **[!UICONTROL Profile]** ficha y arrastre el **[!UICONTROL POI location]** filtro al área principal.
6. En la ventana de filtro de puntos de interés, introduzca el nombre exacto del punto de interés que desea establecer como objetivo.

   >[!TIP]
   >
   >Puede realizar selecciones adicionales para determinar el período de tiempo transcurrido desde la visita anterior del usuario a este punto de interés.

   !["Mensajería push 2 en ACS"](/help/assets/ACS_push2.png)

7. Haga clic en **[!UICONTROL Confirm]**.
8. Vuelva a ejecutar el recuento en la parte superior para ver cómo cambia el tamaño de la audiencia.

   Si no ve la actualización de recuento, es posible que haya introducido un nombre de punto de interés para el que ningún dispositivo ha activado una entrada. Tener el enlace web Slack se vuelve valioso en esta situación, ya que puede ver una lista de entradas de POI de varios dispositivos de prueba.
9. Puede arrastrar filtros de ubicación de puntos de interés adicionales para incluir varios puntos de interés en el mensaje.
10. Haga clic **[!UICONTROL Next]** para finalizar la creación de la notificación push para la entrega.

   !["Mensajería push 3 en ACS"](/help/assets/ACS_push3.html)

El uso del servicio de ubicación con Adobe Campaign Standard le proporciona una poderosa herramienta para segmentar y dirigir sus mensajes a los usuarios en función de las entradas y salidas de la valla geográfica. Esta integración le ayuda a crear casos de uso más personalizados y contextuales.