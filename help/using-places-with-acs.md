---
title: Uso de lugares con Adobe Campaign Standard
seo-title: Uso de lugares con Adobe Campaign Standard
description: Conocer en profundidad las preferencias y hábitos de sus clientes es clave para cualquier campaña de mercadotecnia exitosa. Saber si un usuario ha visitado una ubicación física también puede añadir un contexto muy valioso para formar una relación con el consumidor.
seo-description: Conocer en profundidad las preferencias y hábitos de sus clientes es clave para cualquier campaña de mercadotecnia exitosa. Saber si un usuario ha visitado una ubicación física también puede añadir un contexto muy valioso para formar una relación con el consumidor.
translation-type: tm+mt
source-git-commit: d7c5fe5d7a20a647240114d25307373b493ae2f5

---


# Uso de lugares con Adobe Campaign Standard {#places-with-acs}

*Gracias por visitarnos la semana pasada, nos encantaría darle una sorpresa para su uso en su próxima visita.*

Conocer en profundidad las preferencias y hábitos de sus clientes es clave para cualquier campaña de mercadotecnia exitosa. Los elementos que ha buscado un usuario y el historial de compras anterior juegan un papel importante en la segmentación de audiencias. Saber si un usuario ha visitado una ubicación física también puede añadir un contexto muy valioso para formar una relación con el consumidor.

Según un informe reciente de eMarketer, el 85% de los minoristas de alto rendimiento cree que la ubicación es muy importante para sus esfuerzos de mercadotecnia. Además, más del 58% de los minoristas en Norteamérica planean invertir en tecnologías de proximidad/ubicación para mejorar sus experiencias con los clientes.

![](/help/assets/using-loc-services-acs_0.png)

Piense en la ubicación crítica en su experiencia de uso de smartphones. ¿Con qué frecuencia pide a su teléfono inteligente que encuentre restaurantes, gasolineras, tiendas de comestibles u otros servicios cercanos?

Por lo tanto, tiene sentido que, como marca, esté pensando en formas de aprovechar la ubicación en las campañas de marketing. En esta guía se muestra cómo puede aprovechar el poder del servicio de ubicación de la plataforma de experiencia de Adobe Experience Platform para añadir contexto de ubicación a los mensajes a través de Adobe Campaign Standard, lo que le permite descartar las notificaciones push personalizadas o los mensajes en la aplicación en función de la entrada del punto de interés histórico (POI).

Antes de empezar, en esta guía se asume que tiene una aplicación móvil configurada con el SDK de Adobe Experience Platform Mobile con la extensión Adobe Campaign Standard. Además del SDK de Adobe Experience Platform Mobile y Campaign Standard, debe tener acceso al servicio de ubicación de la plataforma de experiencia.

## Requisitos previos 

1. Integre el SDK [de](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) Adobe Experience Platform Mobile en la aplicación.
1. Agregue [Adobe Campaign Standard Extension](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) a la configuración de la aplicación móvil.
1. [Cree uno o varios puntos de interés](/help/places-database-management-1/managing-pois-in-the-places-ui.md).

>[!TIP]
>
>Si está buscando formas de cargar o administrar puntos de interés de forma masiva, consulte esta [secuencia de comandos para cargar puntos de interés desde un archivo CSV](https://github.com/adobe/places-scripts) . Además, las API de [lugares](/help/places-rest-apis/api-usage/api-usage.md) pueden utilizarse para crear o administrar puntos de interés.

Si no tiene acceso a Places, puede [solicitar acceso aquí](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4fkr821yYptFo-ghlnlXCyhUM0dQVkJCSzVDMFNGWEFXWUUwNEJWSjhSRS4u).

### Habilitar e instalar las extensiones de lugares en la aplicación

Después de crear puntos de interés en la interfaz de Lugares, deberá agregar la funcionalidad Lugares a la aplicación.

1. Siga las instrucciones para activar las extensiones del monitor de lugares y lugares en la aplicación.
1. En la extensión Lugares, asegúrese de haber seleccionado la biblioteca adecuada de puntos de interés que ha creado anteriormente.

   Se pueden agregar bibliotecas adicionales a la configuración de la extensión en cualquier momento.

1. Asegúrese de agregar estas configuraciones a una biblioteca y de publicar los cambios de configuración en Launch.
1. En la ficha Entornos **[]** UICONTROL Launch, haga clic en el icono de instrucciones de instalación para ver las instrucciones sobre cómo descargar los archivos CocoaPod y Gradle correspondientes en su proyecto de aplicación.
1. En la aplicación, siga las instrucciones para agregar el modo de fondo Ubicación a la aplicación e inicie el Monitor de ubicación Lugares.
1. Pruebe la aplicación a través de un simulador de dispositivo para ver la solicitud de aplicación en puntos de interés cercanos en función de la falsificación de la ubicación del dispositivo.

### Crear elementos de datos en el lanzamiento de la plataforma de experiencia

Después de comprobar que las extensiones de Places y Places Monitor funcionan correctamente en la aplicación, cree elementos de datos en Inicio de plataforma de experiencia para leer la información proporcionada por las extensiones y que llega a través del centro de eventos de Mobile SDK. Los elementos de datos actúan esencialmente como alias para recuperar datos de la aplicación cliente. Vamos a crear algunos elementos de datos para recuperar datos de las extensiones de lugares.

1. En la propiedad móvil Inicio de plataforma de experiencia, en la **[!UICONTROL Data Elements]** ficha y haga clic en **[!UICONTROL Add Data Element]**.
1. En el menú de extensión, seleccione **[!UICONTROL Places]**.
1. En la lista **[!UICONTROL Data Element]** desplegable, seleccione **[!UICONTROL Name}**.
1. En la ventana de la derecha, puede seleccionar **[!UICONTROL Current POI]** cuál recuperará el nombre del punto de interés en el que se encuentra el usuario.

   * **[!UICONTROL Last Entered]** recupera el nombre del punto de interés que el usuario introdujo por última vez en un
   * **[!UICONTROL Last Exited]** proporcionará el nombre del punto de interés que el usuario dejó por última vez.

1. Seleccione **[!UICONTROL Last Entered]**.
1. Escriba un nombre para el elemento de datos, como **[!UICONTROL Last Entered POI Name]** y haga clic en **[!UICONTROL Save]**.


   ![](/help/assets/using-loc-services-acs_1.png)

1. Repita los mismos pasos anteriores y cree elementos de datos para Latitud *de punto de interés de*&#x200B;última entrada, Longitud *de punto de*&#x200B;última entrada y Radio *de punto de interés de*&#x200B;última entrada.

Además de los elementos de datos de los lugares, asegúrese de que también ha creado elementos de datos de Mobile Core para el ID *de* aplicación y el ID *de* Experience Cloud.

### Crear una regla para enviar datos de ubicación a Adobe Campaign Standard

Las reglas de Inicio de plataforma de experiencia le permiten crear flujos de trabajo complejos de varias soluciones basados en desencadenadores de eventos. Puede crear otras nuevas o realizar cambios en las reglas existentes y hacer que las actualizaciones se implementen de forma dinámica en las aplicaciones móviles. En este ejemplo, crearemos una regla que se activa cuando un usuario entra en un punto de interés con una ubicación geográfica. Después de activar la regla, se envía una actualización a Campaign Standard para registrar una entrada en un punto de interés específico para el usuario. Este punto de interés se basa en Experience Cloud ID.

1. En la propiedad móvil Inicio de plataforma de experiencia, haga clic en la **[!UICONTROL Rules]** ficha y, a continuación, en **[!UICONTROL Add Rule]**.
1. En la **[!UICONTROL Events]** sección, haga clic en **[!UICONTROL +]** y seleccione **[!UICONTROL Places]**.
1. En **[!UICONTROL Event Type]**, seleccione **[!UICONTROL Enter POI]**.
1. Escriba un nombre para la regla, por ejemplo, **[!UICONTROL User entered POI]**.
1. Haga clic en **[!UICONTROL Keep Changes]**.
1. Deje la **[!UICONTROL Conditions]** sección en blanco.

   Esta sección le permite filtrar o establecer restricciones en el momento en que esta regla debe activarse.

1. In the **[!UICONTROL Actions]** section, click **[!UICONTROL +]**.
1. En **[!UICONTROL Extension]**, seleccione **[!UICONTROL Mobile Core]** y, en **[!UICONTROL Action Type]**, seleccione **[!UICONTROL Send Postback]**.

1. Para la dirección URL, debe construir el extremo de ubicaciones de Campaign Standard.

   La dirección URL debe ser similar a la que aparece a continuación. Asegúrese de utilizar los elementos de datos correctos que creó anteriormente para el servidor de Campaign y la clave.

   `https://{%%camp-server%%}/rest/head/mobileAppV5/{%%pkey%%}/locations/`

1. Haga clic en el cuadro para agregar un cuerpo de anuncio y enviar lo siguiente:

   ```text
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

1. Utilice los elementos de datos específicos que creó en la sección anterior.
1. En **[!UICONTROL Content Type]**, escriba **[!UICONTROL application/json]**.
1. Haga clic **[!UICONTROL Keep Changes]** después de configurar esta opción.

   Podría ser útil configurar un enlace web de Slack como una acción adicional para validar que mi acción se está activando y que se están recopilando los datos correctos.

   >[!IMPORTANT]
   >
   >Recuerde publicar los cambios recientes en la aplicación para asegurarse de que la regla y todos los elementos de datos se implementan como parte de la configuración. Después de la publicación, debe volver a iniciar la aplicación móvil para obtener las últimas actualizaciones de configuración.

### Utilizar los datos de ubicación para dirigir los mensajes de Campaign Standard

Ahora que los datos de ubicación se han rellenado en Campaign, podemos usar puntos de interés como herramienta de segmentos de audiencia.

1. Dentro de la instancia de Adobe Campaign Standard, haga clic en **[UICONTROL Crear notificación]** push.
1. Para el tipo de notificación push, seleccione **[UICONTROL Send push to app subscribers]**.

   Este tipo de push se dirigirá a todos los usuarios de la aplicación. Si los usuarios móviles están conectados a un perfil de campaña, también puede seleccionar **[UICONTROL Enviar push a los perfiles]** de campaña i.

1. Haga clic **[!UICONTROL Next]** y escriba los detalles generales en la siguiente pantalla.
1. En la pantalla Audiencia, haga clic **[!UICONTROL Count]** para ver cuántos usuarios estimados se enviarán las notificaciones Push.

   En este caso, el recuento es de tres, ya que hay tres dispositivos instalados en la aplicación de prueba.

1. En la barra lateral izquierda, expanda la **[!UICONTROL Profile]** ficha y arrastre el **[!UICONTROL POI location]** filtro en el área principal.
1. En la ventana de filtro de puntos de interés, introduzca el nombre exacto del punto de interés que desea dirigir.

   Puede realizar selecciones adicionales para determinar el intervalo de tiempo desde la última visita del usuario a este punto de interés.

   ![](/help/assets/using-loc-services-acs_2.png)

1. Haga clic en [!**Confirmación]de UICONTROL**.
1. Vuelva a ejecutar el recuento en la parte superior para ver cómo cambia el tamaño de la audiencia.

   Si no ve la actualización del recuento, es posible que haya introducido un nombre de punto de interés para el que ningún dispositivo ha activado una entrada. Aquí es donde el gancho web Slack resulta valioso, ya que puede ver una lista de entradas de POI de varios dispositivos de prueba.
1. Puede arrastrar filtros de ubicación de puntos de interés adicionales para incluir varios puntos de interés en el mensaje.
1. Haga clic **[!UICONTROL Next]** para finalizar la creación de la notificación push para la entrega.

   ![](/help/assets/using-loc-services-acs_3.png)

Además de las notificaciones push, también puede utilizar los datos de ubicación para segmentar qué usuarios desea recibir un mensaje en la aplicación.

1. En la instancia de Adobe Campaign Standard, haga clic en **[!UICONTROL Create In-App message]**.
1. Para el tipo de mensaje, seleccione **[!UICONTROL Target all users of a Mobile application]**.
1. Haga clic **[!UICONTROL Next]** y escriba los detalles generales en la siguiente pantalla.
1. En el panel izquierdo, compruebe que ahora puede utilizar una variedad de activadores relacionados con los lugares.
1. Si el usuario ha especificado una reja geográfica de puntos de interés, puede elegir que se muestre el mensaje en la aplicación.

   También puede utilizar los metadatos definidos en la interfaz de usuario de Lugares para filtrar la audiencia. En este ejemplo, quiero activar un mensaje en la aplicación que se muestre solamente a los usuarios que salieron por última vez de un punto de interés que también tenía una función de gimnasio. Tal vez quiera enviarles una encuesta para ver si usaban o les gustaba el gimnasio.

1. Haga clic en **[!UICONTROL Next]** para finalizar la creación del mensaje en la aplicación para su envío.

   ![](/help/assets/using-loc-services-acs_4.png)

El uso de Lugares con Adobe Campaign Standard le proporciona una herramienta muy potente para segmentar y dirigir sus mensajes a los usuarios en función de la ubicación histórica. Esta sencilla integración abre la puerta para crear casos de uso más personalizados y contextuales.

Estamos mejorando constantemente los lugares y las soluciones integradas para incorporar el contexto de ubicación a los flujos de trabajo móviles. Un producto que aprovechará Places es la solución del próximo Viaje Trigado que permitirá a los clientes crear flujos de trabajo en tiempo real basados en desencadenantes de eventos como la ubicación.

## Vínculos recomendados

Para obtener más información, consulte:

* [Servicio de ubicación de Adobe Experience](https://www.adobe.com/experience-platform/location-service.html)
* [Adobe Campaign Standard](https://www.adobe.com/marketing/campaign.html)
* [Regístrese para obtener acceso a Adobe Places Beta](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4fkr821yYptFo-ghlnlXCyhUM0dQVkJCSzVDMFNGWEFXWUUwNEJWSjhSRS4u)
* [SDK de Adobe Experience Platform Mobile](https://sdkdocs.com/)
* [Integración de Adobe Campaign con el SDK de la plataforma de experiencia](https://helpx.adobe.com/campaign/kb/configuring-app-sdk.html)
