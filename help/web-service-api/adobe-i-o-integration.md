---
title: Resumen de integración de Adobe I/O
description: Información sobre la creación de una integración de Adobe I/O.
exl-id: d7d31938-6c0e-40f8-a9d3-30af96043119
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '879'
ht-degree: 5%

---

# Requisitos previos y descripción general de integración {#integration-prereqs}

Esta información muestra cómo crear un Adobe I/O y una integración de Places Service.

## Requisitos previos para el acceso de usuarios

Compruebe con el administrador del sistema de su organización que se han completado las siguientes tareas:

* El servicio principal de Places aparece en Admin Console de su organización.
* Se le ha añadido a la organización.
* Se le ha añadido como usuario al servicio principal Places de su organización.

   Para obtener más información, consulte *Añadir un usuario o un desarrollador a los perfiles de Experience Platform Launch y del servicio Places* in [Obtener acceso al servicio Places](/help/places-gain-access.md).

* Se le ha añadido como desarrollador al servicio principal Places de su organización.

   Para obtener más información sobre cómo añadir desarrolladores, consulte *Añadir un usuario o un desarrollador a los perfiles de Experience Platform Launch y del servicio Places* in [Obtener acceso al servicio Places](/help/places-gain-access.md).

   Para obtener más información sobre la función de desarrollador, consulte [Administración de desarrolladores](https://helpx.adobe.com/es/enterprise/using/manage-developers.html).

### Solicitudes de API de REST

Cada solicitud a la API de REST del servicio Places requiere los siguientes elementos:

* ID de organización de
* Una clave de API
* Un token de portador

Una integración con Adobe I/O de proporciona estos elementos y una forma de solicitar el token de portador mediante un token web JSON (JWT).

* Para obtener más información sobre los JWT, consulte [Introducción a los tokens web JSON](https://jwt.io/introduction/).
* Para crear una integración para el servicio de Places, consulte la *Creación de una integración de Places Service* más abajo.
* Para comprender la integración de claves API, la generación de un JWT y los certificados de claves públicas, consulte [Resumen de autenticación de Adobe I/O](https://www.adobe.io/apis/cloudplatform/console/authentication/gettingstarted.html).

>[!IMPORTANT]
>
>Si no puede iniciar sesión en la consola de Adobe I/O o si Places Service no es una opción de *Página Crear Integraciones*, consulte *Requisitos de organización* in [Información general sobre API de servicios web](/help/web-service-api/places-web-services.md).

## Creación de una integración de Places Service

Para crear una integración de servicios de Places, complete las siguientes tareas:

### Generar un par de claves pública y privada

Para crear una integración de servicios de Places, necesita un par de claves pública y privada. Estos pares se pueden comprar o puede generar sus propias claves autofirmadas.

Para generar sus propias claves autofirmadas:

1. En una ventana de terminal, copie y pegue cada una de las siguientes líneas y pulse **[!UICONTROL Entrar]** después de pegar cada línea:

   ```text
      mkdir keys
      cd keys
      openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout places_integration_test_private.key -out    places_integration_test_public.crt
   ```

   >[!IMPORTANT]
   >
   >Le recomendamos que asigne un nombre a las claves para facilitar la referencia y que las almacene en una carpeta. Si crea varias integraciones, puede identificar y administrar fácilmente qué claves pertenecen a cada integración.

1. Escriba la información que solicita OpenSSL:

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
   >La información que proporcione se incorpora a las claves.

1. Vaya al directorio en el que la variable `.key` y `.crt` se encuentran los archivos.

   Por ejemplo, en MacOS, vaya a **[!UICONTROL Macintosh HD]** > **[!UICONTROL usuarios]** > **[!UICONTROL (su nombre de usuario)]** > **[!UICONTROL Claves]**.

El siguiente vídeo le guía a través del proceso de generación del par de claves:

![vídeo de integración](/help/assets/places_integration_video.gif)

### Creación de una integración de servicios de Places en la consola de Adobe I/O

Para crear una integración de Places Service:

1. Ir a [https://console.adobe.io](https://console.adobe.io) e inicie sesión con su Adobe ID.
1. En el **Inicio rápido** , haga clic en **Crear integración**.
1. Seleccionar **[!UICONTROL Acceso a una API]** y haga clic en **[!UICONTROL Continuar]**.

   **[!UICONTROL Acceso a una API]** es la ubicación predeterminada.

1. Si tiene acceso a más de una organización Experience Cloud, seleccione la organización en la lista desplegable de la parte superior derecha.
1. En **[!UICONTROL Experience Cloud]**, seleccione **[!UICONTROL Servicio de lugares]** como el servicio de Adobe al que desea integrar y haga clic en **[!UICONTROL Continuar]**.
1. Seleccionar **[!UICONTROL Nueva integración]** y haga clic en **[!UICONTROL Continuar]**.
1. En la pantalla Crear una nueva integración, introduzca un nombre y una descripción.
1. Arrastre y suelte su `xxxx_public.crt` , que creó anteriormente, a la variable **[!UICONTROL Certificados de claves públicas]** zona de colocación.
1. Seleccione un perfil de producto.

   Si no está seguro del perfil que desea seleccionar, póngase en contacto con el administrador del sistema.
1. En la parte inferior de la página, haga clic en **[!UICONTROL Crear integración]**.
1. Después de unos segundos, en el *Integración creada* , compruebe que aparece el siguiente mensaje:

   `Your integration has been created.`

1. La página de detalles de la integración aparece con el nombre de la integración en la parte superior.

   El **[!UICONTROL Información general]** Esta pestaña aparece de forma predeterminada y muestra la clave de API, su ID de organización, el ID de cuenta técnica y otros detalles acerca de sus integraciones.

### Registre el ID de organización y la clave de API

1. En la página de detalles de la integración, haga clic en **[!UICONTROL Servicios]** y confirme que **[!UICONTROL Servicio de lugares]** se muestra debajo de **[!UICONTROL Servicios configurados]**.
1. En el **[!UICONTROL Información general]** , busque y registre la clave de API (ID de cliente) y el ID de organización.

   Estos ID son necesarios para cada solicitud de API de REST del servicio Places.

![](/help/assets/places_orgid_api-key.png)

### Generar un token JWT

En la página de detalles de la integración, haga clic en **[!UICONTROL JWT]** para que pueda probar la integración generando un JWT y proporcionando la URL de intercambio.

Para generar un token JWT:

1. En un editor de texto, abra su `private.key` archivo creado que creó anteriormente.
1. En la pestaña **[!UICONTROL JWT]**, copie el contenido de la clave y péguela en el campo **[!UICONTROL Pegar clave privada]**.
1. Clic **[!UICONTROL Generar JWT]**.
1. En la sección **[!UICONTROL Ejemplo de comando CURL]**, haga clic en **[!UICONTROL Copiar]** y pegue el contenido en el símbolo del sistema o en la ventana de terminal.
1. Ejecute el comando pulsando **[!UICONTROL Entrar]** en el teclado.
1. Busque el `"token_type": "bearer"` y el `"access_token"` valor.

   El valor del token de acceso al portador es el que utilizará en las solicitudes de la API del servicio de Places.

>[!IMPORTANT]
>
>Los tokens de acceso de Adobe son válidos **solamente** durante 24 horas, guarde el ejemplo de comando CURL (paso 5). Si el token de acceso ya no es válido, debe volver a generarlo.
