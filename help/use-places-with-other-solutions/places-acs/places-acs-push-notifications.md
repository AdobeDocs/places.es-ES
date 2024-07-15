---
title: Notificaciones push con el servicio Places
description: Esta sección proporciona información sobre cómo utilizar el servicio Places con notificaciones push en Campaign Standard.
exl-id: 4b50f552-deb8-49cd-9221-fbbf33aaa5f9
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 1%

---

# Notificaciones push con el servicio Places {#push-notifications}

En esta sección, aprenderá a utilizar la información de ubicación geográfica histórica para dirigirse a las notificaciones push que se envían a través de Adobe Campaign Standard.

## Requisitos previos

Antes de empezar, complete las siguientes tareas:

* Tenga una aplicación móvil configurada con el SDK de Adobe Experience Platform Mobile, incluida la [extensión de Adobe Campaign Standard](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard).

* Integre el [SDK de Adobe Experience Platform Mobile](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) en su aplicación.
* Agregue la [extensión de Adobe Campaign Standard](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) a la configuración de su aplicación móvil.

* [Crear un punto de interés](/help/poi-mgmt-ui/create-a-poi-ui.md) en la interfaz de administración de puntos de interés del servicio Places.

* Habilite e instale la extensión [Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).


## Creación de elementos de datos en un Experience Platform Launch

Después de comprobar que la extensión Places y una solución de supervisión de región ([Documentación de CoreLocation](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) para iOS o [Documentación de ubicación de Android](https://developer.android.com/training/location/geofencing)) funcionan correctamente en la aplicación, debe crear elementos de datos en Experience Platform Launch. Los elementos de datos permiten leer la información proporcionada por las extensiones a través del centro de eventos del SDK móvil y actuar como un alias para recuperar datos de la aplicación cliente. Para recuperar datos de las extensiones de Places y enviar la información del servicio de Places a Campaign, debe crear algunos elementos de datos.

Para crear un elemento de datos:

1. En la propiedad móvil del Experience Platform Launch, haga clic en la ficha **[!UICONTROL Elementos de datos]** y luego en **[!UICONTROL Agregar elemento de datos]**.
1. En la lista desplegable **[!UICONTROL Extensión]**, seleccione **[!UICONTROL Servicio Places]**.
1. En la lista desplegable **[!UICONTROL Tipo de elemento de datos]**, seleccione **[!UICONTROL Nombre]**.
1. En el panel lateral derecho, puede seleccionar **[!UICONTROL Punto de interés actual]** que recupera el nombre del punto de interés en el que se encuentra el usuario.

   **[!UICONTROL Última entrada]** recupera el nombre del punto de interés que el usuario especificó por última vez, y **[!UICONTROL Última salida]** proporciona el nombre del punto de interés que el usuario dejó por última vez. En este ejemplo, seleccionamos **[!UICONTROL Última entrada]** y escribimos un nombre para el elemento de datos, como **[!UICONTROL Último nombre de punto de interés]** y hacemos clic en **[!UICONTROL Guardar]**.

   ![&quot;Mensajería push en el Campaign Standard&quot;](/help/assets/ACS_Push1.png)

1. Repita los pasos del 1 al 4 anteriores y cree elementos de datos para *Última latitud de punto de interés*, *Última longitud de punto de interés* y *Último radio de punto de interés*.

Además de los elementos de datos para el servicio Places, asegúrese de crear elementos de datos principales móviles para *App ID* y *ID de Experience Cloud*.

## Creación de una regla para enviar datos de ubicación a Adobe Campaign Standard

Las reglas de Experience Platform Launch permiten crear flujos de trabajo complejos de varias soluciones basados en déclencheur de eventos. Con las reglas, puede crear nuevas reglas o modificar las existentes y hacer que las actualizaciones se implementen dinámicamente en las aplicaciones móviles. En el ejemplo siguiente, la regla se activará cuando un usuario introduzca un punto de interés delimitado geográficamente. Una vez activada la regla, se envía una actualización al Campaign Standard para registrar una entrada en un punto de interés específico para un usuario en particular en función del ID de Experience Cloud.

1. En la propiedad móvil del Experience Platform Launch, en la ficha **[!UICONTROL Reglas]**, haga clic en **[!UICONTROL Agregar regla]**.
1. En la sección **[!UICONTROL Events]**, haga clic en **[!UICONTROL +]** y seleccione **[!UICONTROL Places Service]** como extensión.
1. Para el **[!UICONTROL Tipo de evento]**, seleccione **[!UICONTROL Introducir punto de interés]**.
1. Asigne un nombre a la regla como, por ejemplo, **El usuario ingresó el punto de interés**.
1. Haga clic en **[!UICONTROL Conservar cambios]**.
1. Deje la sección **[!UICONTROL Condiciones]** en blanco.

   Esta sección le permite filtrar o establecer restricciones sobre cuándo se debe activar esta regla.

1. En la sección **[!UICONTROL Acciones]**, haga clic en **[!UICONTROL +]**.
1. En la lista desplegable **[!UICONTROL Extension]**, selecciona **[!UICONTROL Mobile Core]** y en la lista desplegable **[!UICONTROL Action Type]**, selecciona **[!UICONTROL Send Postback]**.
1. En **[!UICONTROL URL]**, debe construir el extremo de las ubicaciones del Campaign Standard.

   La dirección URL debe ser similar a `https:///rest/head/mobileAppV5//locations/`.
Asegúrese de utilizar los elementos de datos correctos creados anteriormente para el servidor de Campaign y la clave.

1. Haga clic en el cuadro para añadir un cuerpo de publicación y enviar lo siguiente:

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

1. Asegúrese de utilizar los elementos de datos creados en la sección anterior.
1. En **[!UICONTROL Tipo de contenido]**, escriba **[!UICONTROL application/json]**.
1. Haga clic en **[!UICONTROL Conservar cambios]**.

>[!IMPORTANT]
>
>* Puede resultar útil configurar un enlace web de Slack como acción adicional para validar que se están activando las entradas y que se están recopilando los datos correctos.
>* Recuerde publicar los cambios recientes en la aplicación para asegurarse de que la regla y todos los elementos de datos se implementen como parte de la configuración. Tras la publicación, vuelva a iniciar la aplicación móvil para obtener las últimas actualizaciones de configuración.

## Uso de los datos de ubicación para segmentar los mensajes de Campaign

Ahora que los datos de ubicación se han rellenado en Campaign, podemos usar los puntos de interés como herramienta de segmento de audiencia.

1. En su instancia de Adobe Campaign Standard, haga clic en **[!UICONTROL Crear notificación push]**.
1. Para el tipo de notificación push, seleccione **[!UICONTROL Enviar notificación push a los perfiles de Campaign]**.
1. Haga clic en **[!UICONTROL Siguiente]** y escriba los detalles generales.
1. En la pantalla Audiencia, haga clic en **[!UICONTROL Recuento]** para determinar cuántos usuarios estimados recibirá la notificación push.

   >[!TIP]
   >
   >En este ejemplo, el recuento será 3, ya que hay tres dispositivos instalados en los que se está probando la aplicación.

1. En el panel izquierdo, expanda la ficha **[!UICONTROL Perfil]** y arrastre el filtro **[!UICONTROL Ubicación del punto de interés]** al área principal.
1. En la ventana Filtro de puntos de interés, introduzca el nombre exacto del punto de interés al que desea dirigirse.

   >[!TIP]
   >
   >Puede realizar selecciones adicionales para determinar el período de tiempo desde la visita anterior del usuario a este punto de interés.

   ![&quot;Mensajería push 2 en ACS&quot;](/help/assets/ACS_push2.png)

1. Haga clic en **[!UICONTROL Confirmar]**.
1. Vuelva a ejecutar el recuento en la parte superior para ver cómo cambia el tamaño de la audiencia.

   Si no ve la actualización de su recuento, es posible que haya introducido un nombre de punto de interés para el cual ningún dispositivo haya activado una entrada. En esta situación, es útil tener el enlace web del Slack, ya que puede ver una lista de entradas de puntos de interés de varios dispositivos de prueba.

1. Puede arrastrar filtros de ubicación de puntos de interés adicionales para incluir varios puntos de interés en el mensaje.
1. Haga clic en **[!UICONTROL Siguiente]** para terminar de crear la notificación push para la entrega.

   ![&quot;Mensajería push 3 en ACS&quot;](/help/assets/ACS_push3.png)

El uso del servicio de Places con Adobe Campaign Standard le ofrece una potente herramienta para segmentar y dirigir los mensajes a los usuarios en función de las entradas y salidas del geoperímetro. Esta integración le ayuda a crear casos de uso más personalizados y contextuales.
