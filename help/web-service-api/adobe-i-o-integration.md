---
title: Información general sobre la integración de Adobe I/O
seo-title: Información general sobre la integración de Adobe I/O
description: Información sobre la creación de una integración de Adobe I/O.
seo-description: Información sobre la creación de una integración de Adobe I/O.
translation-type: tm+mt
source-git-commit: f99930325a3d94bcc60595e69306c51d6b81caa6

---


# Integración de Adobe I/O {#adobeio-integration}

Esta información le muestra cómo crear una integración de Adobe I/O y Places.

## Requisitos previos para el acceso de los usuarios

Compruebe con el administrador del sistema de su organización que se han completado las siguientes tareas:

* Los lugares de servicio principal aparecen en la consola de administración de la organización.
* Ha sido agregado a la organización.
* Se le ha agregado como usuario al servicio principal de lugares de su organización.

   Para obtener más información, consulte *Agregar un usuario o un desarrollador a los perfiles* Servicio de ubicación y Inicio de plataforma de experiencia en preguntas [](/help/places-faqs.md)frecuentes.

* Ha sido agregado como desarrollador a los servicios principales de lugares de su organización.

   Para obtener más información sobre cómo agregar desarrolladores, consulte *Agregar un usuario o un desarrollador a sus perfiles* Servicio de ubicación y Lanzamiento de plataforma de experiencia en preguntas [](/help/places-faqs.md)más frecuentes.

   Para obtener más información sobre la función de desarrollador, consulte [Administrar desarrolladores](https://helpx.adobe.com/enterprise/using/manage-developers.html).

### Solicitudes de API REST

Cada solicitud a la API de REST de lugares requiere los siguientes elementos:

* Un ID de organización
* Clave de API
* Un distintivo al portador

Una integración con Adobe I/O proporciona estos elementos y una forma de solicitar el token de portador mediante un token web JSON (JWT).

* Para obtener más información sobre JWT, consulte [Introducción a los tokens](https://jwt.io/introduction/)web JSON.
* Para crear una integración para lugares, consulte la sección *Creación de una integración* de lugares más abajo.
* Para comprender la integración de claves de API, la generación de un JWT y los certificados de claves públicas, consulte Información general sobre la autenticación de [Adobe I/O](https://www.adobe.io/apis/cloudplatform/console/authentication/gettingstarted.html).

>[!IMPORTANT]
>
>Si no puede iniciar sesión en la consola de Adobe I/O o si el servicio de ubicación de la plataforma de experiencia no es una opción de la página ** Crear integraciones, consulte Requisitos *de* organización en Información general [de la API de servicios](/help/web-service-api/places-web-services.md)Web.

## Creación de una integración de lugares

Para crear una integración de lugares, realice las siguientes tareas:

### Generar un par de claves pública y privada

Para crear una integración de lugares, necesita un par de claves pública y privada. Estos pares se pueden comprar o puede generar sus propias claves con firma personal.

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

2. Escriba la información solicitada por OpenSSL:

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

3. Desplácese al directorio donde se encuentran los `.key` archivos y `.crt` los archivos.

   Por ejemplo, en iOS, vaya a **[!UICONTROL Macintosh HD]** &gt; **[!UICONTROL users]** &gt; **[!UICONTROL (your user name)]** &gt; **[!UICONTROL Keys]**.

El siguiente vídeo le guía a través del proceso de generación del par de claves:

![vídeo de integración](/help/assets/places_integration_video.gif)

### Creación de una integración de Places en la consola de Adobe I/O

Para crear una integración de lugares:

1. Vaya a [https://console.adobe.io](https://console.adobe.io) e inicie sesión con su Adobe ID.
2. en la sección Inicio **** rápido, haga clic en **Crear integración**.
3. Seleccione **[!UICONTROL Access an API]** y haga clic en **[!UICONTROL Continue]**.

   **[!UICONTROL Access an API]** es la ubicación predeterminada.

4. Si tiene acceso a más de una organización de Experience Cloud, seleccione la organización en la lista desplegable de la parte superior derecha.
5. En **[!UICONTROL Experience Cloud]**, seleccione **[!UICONTROL Places]** el servicio de Adobe al que desea integrar y haga clic en **[!UICONTROL Continue]**.
6. Seleccione **[!UICONTROL New integration]** y haga clic en **[!UICONTROL Continue]**.
7. En la pantalla Crear una nueva integración, escriba un nombre y una descripción.
8. Arrastre y suelte el `xxxx_public.crt` archivo que ha creado arriba en la zona de **[!UICONTROL Public keys certificates]** colocación.
9. Seleccione un perfil de producto.

   Si no está seguro de qué perfil seleccionar, póngase en contacto con el administrador del sistema.
10. At the bottom of the page, click **[!UICONTROL Create integration]**.
11. Después de unos segundos, en la pantalla *Integración creada* , compruebe que aparece el siguiente mensaje:

   `Your integration has been created.`

12. La página de detalles de la integración aparece con el nombre de la integración en la parte superior.

   La ficha **[!UICONTROL Overview]** aparece de forma predeterminada y muestra la clave de API, el ID de organización, el ID de cuenta técnica y otros detalles sobre las integraciones.

### Registrar el ID de organización y la clave de API

1. En la página de detalles de la integración, haga clic en la **[!UICONTROL Services]** ficha y confirme que **[!UICONTROL Places]** se muestra en **[!UICONTROL Configured Services]**.
2. En la **[!UICONTROL Overview]** ficha, busque y registre la clave de API (ID de cliente) y el identificador de organización.

   Estos ID son necesarios para cada solicitud de API de Places REST.

![](/help/assets/places_orgid_api-key.png)

### Generar un token de JWT

En la página de detalles de la integración, haga clic en la **[!UICONTROL JWT]** ficha para poder probar la integración generando un JWT y proporcionando la URL de intercambio.

Para generar un token de JWT:

1. En un editor de texto, abra el `private.key` archivo creado anteriormente.
2. En la **[!UICONTROL JWT]** ficha, copie el contenido de la clave y péguela en el **[!UICONTROL Paste private key]** campo.
3. Haga clic en **[!UICONTROL Generate JWT]**.
4. En la **[!UICONTROL Sample CURL command]** sección , haga clic **[!UICONTROL Copy]** y pegue el contenido en el símbolo del sistema o en la ventana de terminal.
5. Ejecute el comando presionando **[!UICONTROL Enter]** el teclado.
6. Busque el `"token_type": "bearer"` y el `"access_token"` .

   El valor del autentificador de acceso al portador es lo que utilizará en las solicitudes de la API de lugares.

>[!IMPORTANT]
>
>Los tokens de acceso de Adobe **solo** son válidos durante 24 horas, por lo que guarde el comando CURL de ejemplo (paso 5). Si el autentificador de acceso ya no es válido, debe volver a generar el autentificador.