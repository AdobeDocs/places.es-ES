---
title: Información general sobre la integración de Adobe I/O
description: Información sobre la creación de una integración de Adobe I/O.
translation-type: tm+mt
source-git-commit: c22efc36f2eac6b20fc555d998c3988d8c31169e
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 1%

---


# Integration overview and prerequisites {#integration-prereqs}

Esta información le muestra cómo crear una integración de Adobe I/O y un servicio de lugares.

## Requisitos previos para el acceso de los usuarios

Compruebe con el administrador del sistema de su organización que se han completado las siguientes tareas:

* Los lugares de servicio principal aparecen en la consola de administración de la organización.
* Ha sido agregado a la organización.
* Se le ha agregado como usuario al servicio principal de lugares de su organización.

   Para obtener más información, consulte *Añadir un usuario o un desarrollador a los perfiles* del servicio de lugares y Experience Platform Launch en [Obtener acceso al servicio](/help/places-gain-access.md)de lugares.

* Se le ha agregado como desarrollador a los servicios principales de lugares de su organización.

   Para obtener más información sobre cómo agregar desarrolladores, consulte *Añadir un usuario o un desarrollador a sus perfiles* de Servicio de lugares y Experience Platform Launch en [Obtener acceso a Servicio](/help/places-gain-access.md)de lugares.

   Para obtener más información sobre la función de desarrollador, consulte [Administrar desarrolladores](https://helpx.adobe.com/es/enterprise/using/manage-developers.html).

### Solicitudes de API REST

Cada solicitud a la API de REST del servicio de lugares requiere los siguientes elementos:

* Un ID de organización
* Clave de API
* Un distintivo al portador

Una integración con Adobe I/O proporciona estos elementos y una manera de solicitar el token del portador mediante un token web JSON (JWT).

* Para obtener más información sobre JWT, consulte [Introducción a los tokens](https://jwt.io/introduction/)web JSON.
* Para crear una integración para el servicio de lugares, consulte la sección *Creación de una integración* del servicio de lugares más abajo.
* Para comprender la integración de claves de API, la generación de un JWT y los certificados de claves públicas, consulte [Adobe I/O Authentication Overview](https://www.adobe.io/apis/cloudplatform/console/authentication/gettingstarted.html).

>[!IMPORTANT]
>
>Si no puede iniciar sesión en la consola de Adobe I/O o si el servicio de lugares no es una opción de la página ** Crear integraciones, consulte Requisitos *de* organización en Información general [de la API de servicios](/help/web-service-api/places-web-services.md)Web.

## Crear una integración de servicio de lugares

Para crear una integración de servicio de lugares, complete las siguientes tareas:

### Generar un par de claves pública y privada

Para crear una integración de servicio de lugares, necesita un par de claves pública y privada. Estos pares se pueden comprar o puede generar sus propias claves con firma personal.

Para generar sus propias claves con firma personal:

1. En una ventana de terminal, copie y pegue cada una de las líneas siguientes y pulse **[!UICONTROL Enter]** después de pegar cada línea:

   ```text
      mkdir keys
      cd keys
      openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout places_integration_test_private.key -out    places_integration_test_public.crt
   ```

   >[!IMPORTANT]
   >
   >Le recomendamos que asigne un nombre a las claves para facilitar su consulta y almacenarlas en una carpeta. Si crea varias integraciones, puede identificar y administrar fácilmente qué claves pertenecen a cada integración.

1. Escriba la información solicitada por OpenSSL:

   ```text
   Country Name (2 letter code:  // Example: US
   State or Province Name (full name):  // Example: California
   Locality Name (eg, city):  // Example: San Jose
   Organization Name (eg, company):  // Example: Places
   Organizational Unit Name (eg, section):  // Example: Engineering
   Common Name (eg, fully qualified host name):  // Example: places.com
   Email Address:  // Example:  poi@places.com
   ```

   Para obtener más información sobre OpenSSL, consulte [OpenSSL](https://www.openssl.org/).

   >[!IMPORTANT]
   >
   >La información proporcionada se incorpora a las claves.

1. Desplácese al directorio donde se encuentran los `.key` archivos y `.crt` los archivos.

   Por ejemplo, en MacOS, vaya a **[!UICONTROL Macintosh HD]** > **[!UICONTROL users]** > **[!UICONTROL (your user name)]** > **[!UICONTROL Keys]**.

El siguiente vídeo le guía a través del proceso de generación del par de claves:

![vídeo de integración](/help/assets/places_integration_video.gif)

### Creación de una integración de servicio de lugares en la consola de Adobe I/O

Para crear una integración de servicio de lugares:

1. Vaya a [https://console.adobe.io](https://console.adobe.io) e inicie sesión con su Adobe ID.
1. En la sección Inicio **** rápido, haga clic en **Crear integración**.
1. Seleccione **[!UICONTROL Access an API]** y haga clic en **[!UICONTROL Continue]**.

   **[!UICONTROL Access an API]** es la ubicación predeterminada.

1. Si tiene acceso a más de una organización Experience Cloud, seleccione la organización en la lista desplegable de la parte superior derecha.
1. Under **[!UICONTROL Experience Cloud]**, select **[!UICONTROL Places Service]** as the Adobe service to which you want to integrate and click **[!UICONTROL Continue]**.
1. Seleccione **[!UICONTROL New integration]** y haga clic en **[!UICONTROL Continue]**.
1. En la pantalla Crear una nueva integración, escriba un nombre y una descripción.
1. Arrastre y suelte el `xxxx_public.crt` archivo que ha creado arriba en la zona de **[!UICONTROL Public keys certificates]** colocación.
1. Seleccione un perfil de producto.

   Si no está seguro de qué perfil seleccionar, póngase en contacto con el administrador del sistema.
1. En la parte inferior de la página, haga clic en **[!UICONTROL Create integration]**.
1. Después de unos segundos, en la pantalla *Integración creada* , compruebe que aparece el siguiente mensaje:

   `Your integration has been created.`

1. La página de detalles de la integración aparece con el nombre de la integración en la parte superior.

   La ficha **[!UICONTROL Overview]** aparece de forma predeterminada y muestra la clave de API, el ID de organización, el ID de cuenta técnica y otros detalles sobre las integraciones.

### Registrar el ID de organización y la clave de API

1. En la página de detalles de la integración, haga clic en la **[!UICONTROL Services]** ficha y confirme que **[!UICONTROL Places Service]** se muestra en **[!UICONTROL Configured Services]**.
1. En la **[!UICONTROL Overview]** ficha, busque y registre la clave de API (ID de cliente) y el identificador de organización.

   Estos ID son necesarios para cada solicitud de API de REST del servicio de lugares.

![](/help/assets/places_orgid_api-key.png)

### Generar un token de JWT

En la página de detalles de la integración, haga clic en la **[!UICONTROL JWT]** ficha para poder probar la integración generando un JWT y proporcionando la URL de intercambio.

Para generar un token de JWT:

1. En un editor de texto, abra el `private.key` archivo creado anteriormente.
1. On the **[!UICONTROL JWT]** tab, copy the contents of the key and paste it in the **[!UICONTROL Paste private key]** field.
1. Haga clic en **[!UICONTROL Generate JWT]**.
1. In the **[!UICONTROL Sample CURL command]** section, click **[!UICONTROL Copy]** and paste the contents in your command prompt or terminal window.
1. Ejecute el comando presionando **[!UICONTROL Enter]** el teclado.
1. Localice el `"token_type": "bearer"` y el `"access_token"` .

   El valor del token de acceso al portador es lo que utilizará en las solicitudes de la API de servicio de lugares.

>[!IMPORTANT]
>
>Los tokenes de acceso de Adobe **solo** son válidos durante 24 horas, por lo que guarde el comando CURL de ejemplo (paso 5). Si el token de acceso ya no es válido, debe volver a generar el token.