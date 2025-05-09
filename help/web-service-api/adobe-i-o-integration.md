---
title: Información general del proyecto Adobe Developer
description: Información sobre la creación de un proyecto de API de Adobe Developer.
exl-id: d7d31938-6c0e-40f8-a9d3-30af96043119
source-git-commit: 3d477c6133b74a7e6380d0db1af5125aaa844035
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 1%

---

# Requisitos previos y descripción general del acceso a API Places {#developer-prereqs}

Esta información muestra cómo crear un proyecto en Adobe Developer Console y generar un token de acceso para utilizarlo en las solicitudes de API de Places.

## Requisitos previos para el acceso de usuarios

Compruebe con el administrador del sistema de su organización que se han completado las siguientes tareas:

* Se le ha añadido a la organización.
* Se le ha añadido a un perfil dentro de Adobe Experience Platform.

  Para obtener más información, consulte *Agregar un usuario o un desarrollador a los perfiles del servicio y del Experience Platform Launch de Places* en [Obtener acceso al servicio de Places](/help/places-gain-access.md).

### Solicitudes de API de REST

Cada solicitud a la API de REST del servicio Places requiere los siguientes elementos:

* ID de organización de
* Una clave de API (también denominada ID de cliente)
* Secreto del cliente
* Un token de portador

Un proyecto con la [consola Adobe Developer](https://developer.adobe.com/console) proporciona estos elementos.

* Para crear un proyecto para la API del servicio Places, consulte la sección *Creación de un proyecto del servicio Places* a continuación.

>[!IMPORTANT]
>
>Si no puede iniciar sesión en la [consola de Adobe Developer](https://developer.adobe.com/console) o si el servicio Places no es una opción de la página *Crear integraciones*, consulte *Requisitos de la organización* en [Información general de la API de servicios web](/help/web-service-api/places-web-services.md).

## Creación de un proyecto de API de servicio de Places

Para crear un proyecto para la API del servicio Places, complete lo siguiente:

1. Inicie sesión en el [sitio web de Adobe Developer](https://developer.adobe.com) con su Adobe ID.
2. Haga clic en **[!UICONTROL Consola]** en la esquina superior derecha de la página.
3. Si se le asigna más de una organización de Adobe, seleccione la organización correcta en la lista desplegable de la esquina superior derecha de la página.
4. Haga clic en el botón **[!UICONTROL Crear nuevo proyecto]**.
5. Haga clic en el botón **[!UICONTROL Agregar API]** en la sección Introducción a su nuevo proyecto.
6. Para seleccionar la API de Places, desplácese hacia abajo por la página hasta la tarjeta Places y haga clic en la casilla de verificación situada en la esquina superior derecha de la tarjeta.
7. Haga clic en el botón **[!UICONTROL Next]**.
8. Seleccione la opción OAuth Server-to-Server (si hay otra opción).
9. Asigne un nombre a la credencial y haga clic en **[!UICONTROL Siguiente]**.
10. Seleccione un perfil (cualquiera debería funcionar si hay más de uno).
11. Haga clic en **[!UICONTROL Guardar y configurar API]**.
12. En el panel izquierdo, haga clic en el vínculo **[!UICONTROL Servidor a servidor de OAuth]** en CREDENCIALES
13. Esta página proporciona lo siguiente:
    * Una forma de generar un token de acceso para utilizarlo en las solicitudes de API de REST del servicio de Places.
    * Vea un comando curl para ver un ejemplo de cómo puede generar un token de acceso a partir de su propio código.
    * Ver el ID de cliente (también denominado clave de API)
    * Ver el secreto del cliente
    * Visualización del ID de organización
    * Todos ellos son obligatorios en las solicitudes a la API de REST del servicio Places.
14. Puede cambiar el nombre del proyecto por otro más descriptivo haciendo clic en el nombre del proyecto en la ruta de la parte superior izquierda de la ventana
15. A continuación, haga clic en el botón **[!UICONTROL Editar proyecto]** en la parte superior derecha de la página.

>[!IMPORTANT]
>
>Los tokens de acceso a la Adobe son válidos **solo** durante 24 horas, por lo que guarde el comando CURL de ejemplo (paso 5). Si el token de acceso ya no es válido, debe volver a generarlo.
