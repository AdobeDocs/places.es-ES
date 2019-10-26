---
title: Notificaciones push
seo-title: Notificaciones push
description: En esta sección se proporciona información sobre cómo utilizar los lugares con notificaciones push en Campaign Standard.
seo-description: 'En esta sección se proporciona información sobre cómo utilizar los lugares con notificaciones push en Campaign Standard. '
translation-type: tm+mt
source-git-commit: 0612e2fb06e45ff25ad580e3336be3eb48bb39b9

---


# Notificaciones push con el servicio de ubicación de la plataforma de experiencia {#push-notifications}

En esta guía, mostraremos cómo puede utilizar la información de ubicación geográfica histórica para dirigir las notificaciones push enviadas a través de Adobe Campaign Standard.

>[!IMPORTANT]
>
>Antes de comenzar, complete las siguientes tareas:
>
>* Tenga una aplicación móvil configurada con el SDK de Adobe Experience Platform Mobile, incluida la extensión [de](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)Adobe Campaign Standard.
   >
   >
* Integre el SDK [de](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) Adobe Experience Platform Mobile en la aplicación.
>* Agregue [Adobe Campaign Standard Extension](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) a la configuración de la aplicación móvil.
   >
   >
* [Cree un punto de interés](/help/poi-mgmt-ui/create-a-poi-ui.md) en la interfaz de administración del punto de interés de lugares.
   >
   >
* Habilite e instale la extensión [Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).



## Creación de elementos de datos en el lanzamiento de la plataforma de experiencia

Después de comprobar que el Monitor de lugares y ubicaciones para las extensiones de servicio de ubicación funciona correctamente en la aplicación, cree elementos de datos en el Inicio de plataforma de experiencia. Los elementos de datos le permiten leer la información proporcionada por las extensiones que provienen del centro de eventos del SDK móvil y actuar como alias para recuperar datos de la aplicación cliente. Vamos a crear algunos elementos de datos para recuperar datos de las extensiones de lugares, de modo que podamos enviar la información de lugares a Campaign.

1. En la propiedad móvil Inicio de plataforma de experiencia, haga clic en la ficha Elementos **** de datos y, a continuación, en **Agregar elemento** de datos.
2. En la lista desplegable **Extensión** , seleccione **Lugares**.
3. En la lista desplegable Tipo **de elemento de** datos, seleccione **Nombre**.
4. En el panel del lado derecho, puede seleccionar el punto de interés **actual** que recupera el nombre del punto de interés en el que se encuentra el usuario.

   **Última entrada** recupera el nombre del punto de interés que el usuario introdujo por última vez y **Última salida** proporciona el nombre del punto de interés que el usuario dejó por última vez. Para este ejemplo, seleccionaremos **Última entrada** y escribiremos un nombre para el elemento de datos, como **Último nombre** de punto de interés especificado y haremos clic en **Guardar**.

   !["Mensajería push en Campaign Standard"](/help/assets/ACS_Push1.png)


5. Repita los mismos pasos anteriores y cree elementos de datos para _Última latitud_ de puntos de interés introducida, Longitud _de puntos de interés_&#x200B;última entrada y Radio _de puntos de interés_&#x200B;última entrada.

Además de los elementos de datos del servicio de ubicación, asegúrese de crear elementos de datos principales de Mobile para el ID _de_ aplicación y el ID _de_ Experience Cloud.

## Crear una regla para enviar datos de ubicación a Adobe Campaign Standard

Las reglas de Inicio de plataforma de experiencia le permiten crear flujos de trabajo complejos con varias soluciones basados en desencadenadores de eventos. Lo mejor de las reglas es que puede crear nuevas reglas o modificar las existentes y hacer que las actualizaciones se implementen dinámicamente en las aplicaciones móviles. En este ejemplo, crearemos una regla que se activará cuando un usuario entre en un punto de interés con grietas geográficas. Después de activar la regla, se envía una actualización a Campaign para registrar una entrada en un punto de interés específico para un usuario concreto según el ID de Experience Cloud.

1. En la propiedad móvil Launch, haga clic en la ficha **Reglas** y luego en **Agregar regla**.
2. En la sección **Eventos** , haga clic en **+** y seleccione **Lugares** como extensión.
3. Para el tipo **de** evento, seleccione **Introducir punto de interés**.
4. Asigne un nombre a la regla; por ejemplo, **el usuario ha introducido un punto de interés**.
5. Click **Keep Changes**.
6. La sección **Condiciones** le permite filtrar o establecer restricciones sobre cuándo se debe activar esta regla.  Por ahora dejaremos esto en blanco.
7. En la sección **Acciones** , haga clic **+** para crear una nueva acción
8. En la lista desplegable **Extensión** , seleccione **Mobile Core,** y en la lista desplegable Tipo **de** acción, seleccione **Enviar postback**.
9. Para la **dirección URL**, debe construir el extremo de ubicaciones de Campaign Standard.  La dirección URL debe ser similar a la que aparece a continuación. Asegúrese de utilizar los elementos de datos correctos que creó anteriormente para el servidor de Campaign y la clave. `https:///rest/head/mobileAppV5//locations/`
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

11. Asegúrese de que está utilizando los elementos de datos específicos que creó en la sección anterior.
12. En Tipo **** de contenido, escriba **application/json**.
13. Haga clic en **Mantener cambios** después de haber configurado esta opción.
14. Puede resultar útil disponer de una configuración de enlace web Slack como acción adicional para validar que las entradas se están activando y que se están recopilando los datos correctos.


>No olvide publicar los cambios recientes en la aplicación para asegurarse de que la regla y todos los elementos de datos se implementan como parte de la configuración. Tras la publicación, debe volver a iniciar la aplicación móvil para obtener las últimas actualizaciones de configuración.

## Utilizar los datos de ubicación para dirigir los mensajes de campaña

Ahora que los datos de ubicación se han rellenado en Campaign, podemos utilizar los puntos de interés como herramienta de segmentos de audiencia.

1. En la instancia de Adobe Campaign Standard, haga clic en **Crear notificación** push.
2. Para el tipo de notificación push, seleccione **Enviar push a perfiles** de campaña.
3. Haga clic en **Siguiente** y escriba los detalles generales en la siguiente pantalla.
4. En la pantalla Audiencia, haga clic en **Recuento** para ver cuántos usuarios estimados se enviarán las notificaciones Push.

   *En este caso, mi recuento será igual a tres, ya que tengo tres dispositivos instalados en los que probar la aplicación.*

5. En la barra lateral izquierda, expanda la ficha **Perfil** y arrastre el filtro de ubicación **de** puntos de interés al área principal
6. En la ventana de filtro de puntos de interés, introduzca el nombre exacto del punto de interés que desea establecer como objetivo.

   *Puede realizar selecciones adicionales para determinar el intervalo de tiempo desde la última visita del usuario a este punto de interés.*

   !["Mensajería push 2 en ACS"](/help/assets/ACS_push2.png)


7.  Haga clic en **Confirmar**.  
8. Vuelva a ejecutar el recuento en la parte superior para ver cómo cambia el tamaño de la audiencia.  Si no ve la actualización de recuento, es posible que haya introducido un nombre de punto de interés para el que ningún dispositivo ha activado una entrada. Aquí es donde el gancho web Slack resulta valioso, ya que puede ver una lista de entradas de POI de varios dispositivos de prueba.
9. Puede arrastrar filtros de ubicación de puntos de interés adicionales para incluir varios puntos de interés en el mensaje.
10. Haga clic en **Siguiente** para terminar de crear la notificación push para la entrega.

   !["Mensajería push 3 en ACS"](/help/assets/ACS_push3.html)

El uso del servicio de ubicación con Adobe Campaign Standard le proporciona una poderosa herramienta para segmentar y dirigir sus mensajes a los usuarios en función de las entradas y salidas de la valla geográfica. Esta sencilla integración abre la puerta para crear casos de uso más personalizados y contextuales.