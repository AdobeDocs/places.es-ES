---
title: Notificaciones push con el servicio Places
description: En esta sección se proporciona información sobre cómo utilizar el servicio Places con notificaciones push en Campaign Standard.
exl-id: 4b50f552-deb8-49cd-9221-fbbf33aaa5f9
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '1005'
ht-degree: 4%

---

# Servicio de notificaciones push con Places {#push-notifications}

En esta sección, aprenderá a utilizar la información de geolocalización histórica para dirigir las notificaciones push que se envían a través de Adobe Campaign Standard.

## Requisitos previos

Antes de comenzar, complete las siguientes tareas:

* Tener una aplicación móvil configurada con el SDK de Adobe Experience Platform Mobile, incluido el [Extensión de Adobe Campaign Standard](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard).

* Integrar el [SDK de Adobe Experience Platform Mobile](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) en su aplicación.
* Agregue la variable [Extensión de Adobe Campaign Standard](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) a la configuración de la aplicación móvil.

* [Crear un punto de interés](/help/poi-mgmt-ui/create-a-poi-ui.md) en la interfaz de administración de puntos de interés de Places Service.

* Habilitar e instalar el [Extensión Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).


## Creación de elementos de datos en el Experience Platform Launch

Después de comprobar que la extensión Places y una solución de monitorización de región ([Documentación de CoreLocation](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) para iOS, o [Documentación de la ubicación de Android](https://developer.android.com/training/location/geofencing)) funcionan correctamente en la aplicación, debe crear elementos de datos en Experience Platform Launch. Los elementos de datos le permiten leer la información proporcionada por las extensiones que pasan por el centro de eventos del SDK móvil y actuar como un alias para recuperar datos de la aplicación cliente. Para recuperar datos de las extensiones Places y enviar la información del servicio Places a Campaign, debe crear algunos elementos de datos.

Para crear un elemento de datos:

1. En la propiedad móvil de Experience Platform Launch, haga clic en el botón **[!UICONTROL Elementos de datos]** y haga clic en **[!UICONTROL Añadir elemento de datos]**.
1. En el **[!UICONTROL Extensión]** lista desplegable, seleccione **[!UICONTROL Servicio de Places]**.
1. En el **[!UICONTROL Tipo de elemento de datos]** lista desplegable, seleccione **[!UICONTROL Nombre]**.
1. En el panel lateral derecho, puede seleccionar **[!UICONTROL Punto de interés actual]** que recupera el nombre del punto de interés en el que se encuentra el usuario.

   **[!UICONTROL Última entrada]** recupera el nombre del punto de interés que el usuario introdujo por última vez, y **[!UICONTROL Última salida]** proporciona el nombre del punto de interés que dejó el usuario por última vez. En este ejemplo, seleccionamos **[!UICONTROL Última entrada]** y escriba un nombre para el elemento de datos, como **[!UICONTROL Nombre de punto de interés especificado por última vez]** y en los que se hizo clic **[!UICONTROL Guardar]**.

   ![&quot;Mensajería push en Campaign Standard&quot;](/help/assets/ACS_Push1.png)

1. Repita los pasos 1-4 anteriores y cree elementos de datos para *Última latitud de punto de interés introducida*, *Última longitud de punto de interés introducida* y *Último radio de punto de interés introducido*.

Además de los elementos de datos para el servicio Places, asegúrese de crear elementos de datos principales de Mobile para *ID de la aplicación* y *ID de Experience Cloud*.

## Crear una regla para enviar datos de ubicación a Adobe Campaign Standard

Las reglas en el Experience Platform Launch permiten crear flujos de trabajo complejos con varias soluciones basadas en déclencheur de eventos. Con las reglas, puede crear nuevas reglas o modificar las existentes y tener las actualizaciones implementadas dinámicamente en las aplicaciones móviles. En el siguiente ejemplo, la regla se activará cuando un usuario introduzca un punto de interés con delimitación geográfica. Una vez activada la regla, se envía una actualización al Campaign Standard para registrar una entrada en un punto de interés específico para un usuario en particular en función del ID del Experience Cloud.

1. En la propiedad móvil de Experience Platform Launch, en la variable **[!UICONTROL Reglas]** , haga clic en **[!UICONTROL Agregar regla]**.
1. En el **[!UICONTROL Eventos]** , haga clic en **[!UICONTROL +]** y seleccione **[!UICONTROL Servicio de Places]** como extensión.
1. Para la variable **[!UICONTROL Tipo de evento]**, seleccione **[!UICONTROL Introducir punto de interés]**.
1. Asigne un nombre a la regla, por ejemplo, **El usuario ha introducido el punto de interés**.
1. Haga clic en **[!UICONTROL Mantener cambios]**.
1. Deje el **[!UICONTROL Condiciones]** en blanco.

   Esta sección le permite filtrar o colocar restricciones sobre cuándo se debe activar esta regla.

1. En el **[!UICONTROL Acciones]** , haga clic en **[!UICONTROL +]**.
1. En el **[!UICONTROL Extensión]** lista desplegable, seleccione **[!UICONTROL Núcleo móvil]** y en el **[!UICONTROL Tipo de acción]** lista desplegable, seleccione **[!UICONTROL Enviar postback]**.
1. En **[!UICONTROL URL]**, debe construir el punto final de sus ubicaciones de Campaign Standard.

   La dirección URL debería ser similar a `https:///rest/head/mobileAppV5//locations/`.
Asegúrese de utilizar los elementos de datos correctos que creó anteriormente para el servidor y la clave de Campaign.

1. Haga clic en el cuadro para añadir un cuerpo de anuncio y enviar lo siguiente:

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
1. En **[!UICONTROL Tipo de contenido]**, escriba **[!UICONTROL application/json]**.
1. Haga clic en **[!UICONTROL Mantener cambios]**.

>[!IMPORTANT]
>
>* Podría resultar útil configurar un enlace web de Slack como una acción adicional para validar que las entradas se están activando y que se están recopilando los datos adecuados.
>* Recuerde publicar los cambios recientes en la aplicación para asegurarse de que la regla y todos los elementos de datos se implementen como parte de la configuración. Después de publicar, vuelva a iniciar la aplicación móvil para obtener las últimas actualizaciones de configuración.


## Usar datos de ubicación para dirigir los mensajes de campaña

Ahora que los datos de ubicación se rellenan en Campaign, podemos utilizar los puntos de interés como herramienta de segmentos de audiencia.

1. En la instancia de Adobe Campaign Standard, haga clic en **[!UICONTROL Crear notificación push]**.
1. Para el tipo de notificación push, seleccione **[!UICONTROL Enviar push a perfiles de Campaign]**.
1. Haga clic en **[!UICONTROL Siguiente]** y escriba los detalles generales.
1. En la pantalla Audiencia , haga clic en **[!UICONTROL Recuento]** para determinar la cantidad de usuarios estimados que se enviarán las notificaciones push.

   >[!TIP]
   >
   >En este ejemplo, el recuento será 3, ya que hay tres dispositivos instalados en los que se está probando la aplicación.

1. En el panel izquierdo, expanda el **[!UICONTROL Perfil]** y arrastre el **[!UICONTROL Ubicación del punto de interés]** filtre al área principal.
1. En la ventana de filtro de puntos de interés, introduzca el nombre exacto del punto de interés al que desea dirigirse.

   >[!TIP]
   >
   >Puede realizar más selecciones para determinar el periodo de tiempo desde la visita anterior del usuario a este punto de interés.

   ![&quot;Mensajería push 2 en ACS&quot;](/help/assets/ACS_push2.png)

1. Haga clic en **[!UICONTROL Confirm]**.
1. Vuelva a ejecutar el recuento en la parte superior para ver el cambio en el tamaño de la audiencia.

   Si no ve la actualización de su recuento, es posible que haya introducido un nombre de punto de interés para el que ningún dispositivo haya activado una entrada. Tener el vínculo web del Slack resulta valioso en esta situación, ya que puede ver una lista de entradas de puntos de interés de varios dispositivos de prueba.

1. Puede arrastrar filtros de ubicación de puntos de interés adicionales para incluir varios puntos de interés en el mensaje.
1. Haga clic en **[!UICONTROL Siguiente]** para terminar de crear la notificación push para la entrega.

   ![&quot;Mensajería push 3 en ACS&quot;](/help/assets/ACS_push3.png)

El uso del servicio Places con Adobe Campaign Standard le proporciona una potente herramienta para segmentar y dirigir sus mensajes a los usuarios en función de las entradas y salidas de la valla geográfica. Esta integración ayuda a crear casos de uso más personalizados y contextuales.
