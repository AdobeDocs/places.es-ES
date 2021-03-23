---
title: 'Obtener acceso al servicio Places '
description: En esta sección se proporciona información sobre cómo agregar un usuario al servicio y al Experience Platform Launch de Places para que el usuario pueda acceder al servicio de Places.
translation-type: tm+mt
source-git-commit: ecf50d67d4c08e79d9c3be64480f27d435fd7fcb
workflow-type: tm+mt
source-wordcount: '1160'
ht-degree: 9%

---

# Obtener acceso al servicio Places {#adding-user-launch-places}

Puede acceder al servicio Places desde el menú de acceso rápido de [Adobe Experience Cloud home](https://experience.adobe.com).
Si su ID de usuario tiene acceso, verá el icono del servicio de Places como se indica a continuación:

![menú acceso rápido](/help/assets/quickaccess.png)

También puede acceder al servicio Places desde el menú de Adobe Experience Platform:

![menú Experience Platform](/help/assets/solutionaccessmenu.png)

Si no ve el servicio de Places en ninguno de estos menús, póngase en contacto con un administrador de su organización para agregar su ID de usuario al servicio principal de Places en el Admin Console.

## Adición de un usuario al servicio y al Experience Platform Launch de Places

Para permitir que los usuarios accedan a la [IU del Experience Platform Launch](https://launch.adobe.com), deben agregarse al servicio principal de Places en el Admin Console como usuario. Para permitir que los usuarios tengan acceso al Experience Platform Launch, configurar propiedades móviles y utilizar Places con el SDK de Adobe Experience Platform, deben agregarse al Experience Platform Launch en el Admin Console y recibir los siguientes permisos para el Experience Platform Launch:

* Todos los derechos de propiedad:
   * Desarrollo
   * Aprobar
   * Publicar
   * Administrar extensiones
   * Administrar entornos
* Permiso Administrar propiedades en Derechos de compañía

Si es la primera vez que agrega un usuario, complete los siguientes pasos para agregar usuarios a Experience Platform Launch y Servicio de Places. Si ha añadido usuarios anteriormente, es posible que se muestren varios perfiles, por lo que debe seleccionar el perfil correcto.

>[!IMPORTANT]
>
>Solo los administradores de organización pueden acceder al Admin Console y añadir a los usuarios.

### 1. Compruebe que el servicio y el Experience Platform Launch de Places están aprovisionados

1. Inicie sesión en su organización Experience Cloud.
1. En el lado superior derecho, haga clic en el selector de shell del Experience Cloud.

   ![alternador de shell](/help/assets/places_shell_switcher1.png)

1. En **[!UICONTROL Platform]**, haga clic en **[!UICONTROL Administration]**.

   Si no ve **[!UICONTROL Administration]** en la lista, no es administrador. Debe ponerse en contacto con el administrador de organización para completar este procedimiento.

1. En la página Administración del Experience Cloud, en la tarjeta **[!UICONTROL Admin Console]**, haga clic en **[!UICONTROL Llévame allí]**.

1. En el Admin Console, si tiene acceso a varias organizaciones, compruebe que la organización correcta esté seleccionada en la parte superior derecha de la página.

   Esta es la organización a la que agregará a los usuarios. Si no se ha seleccionado la organización correcta, haga clic en la organización y seleccione la organización en la lista desplegable.

   >[!IMPORTANT]
   >
   >Si no tiene acceso a una organización, significa que no tiene acceso de administrador a esa organización.

1. Compruebe que se muestran las tarjetas de **[!UICONTROL Adobe Experience Platform Launch]** y **[!UICONTROL Servicios principales de Places]**.

   ![](/help/assets/places_provisioned1.png)

   Si se muestran, el servicio de Places y el Experience Platform Launch se han aprovisionado para su organización. Si no se muestran, deben aprovisionarse para su organización.


### 2. Configure el perfil y añada los permisos

1. Configure un perfil de Experience Platform Launch, que permite a los usuarios añadidos al perfil utilizar Experience Platform Launch y sus propiedades móviles con el SDK de Experience Platform.

   a. En la barra de menús, haga clic en **[!UICONTROL Product]**.

   b. En el panel izquierdo, en la lista de productos, haga clic en **[!UICONTROL Adobe Experience Platform Launch]**.

   * Los perfiles del Experience Platform Launch aparecen a la derecha.
   * El Experience Platform Launch tiene un perfil predeterminado llamado *Launch - (nombre de organización)* .

      Si agregó usuarios anteriormente a Experience Platform Launch, es posible que vea varios perfiles en la lista.

1. Seleccione el perfil correcto:

   a. Haga clic en el nombre del perfil predeterminado.

   b. Haga clic en la pestaña **[!UICONTROL Permissions]**.

   c. Haga clic en **[!UICONTROL Editar]** junto a **[!UICONTROL Derechos de propiedad]**.

   d. En el panel izquierdo, haga clic en **[!UICONTROL + Agregar todo]**.

   Este paso mueve todos los permisos disponibles a la lista de permisos incluidos.

   e. Haga clic en **[!UICONTROL Derechos de compañía]**.

   f. En el panel izquierdo, haga clic en **[!UICONTROL + Administrar propiedades]**.

   g. Haga clic en **[!UICONTROL Guardar]**.

>[!IMPORTANT]
>
>Para el servicio de Places, hay un perfil predeterminado, pero no tiene que añadir permisos.

Ha agregado correctamente permisos al perfil que ha creado.

### 3. Agregue un usuario o un desarrollador a sus perfiles de Servicio de Places y Experience Platform Launch

Puede agregar un usuario o un desarrollador a sus perfiles de Experience Platform Launch y servicio de Places.

### Agregar un usuario

Para agregar un usuario a sus perfiles de Servicio de Places y Experience Platform Launch:

1. Agregue un usuario al perfil del Experience Platform Launch.

   a. En la barra de menús, haga clic en **[!UICONTROL Información general]**.

   b. En la tarjeta **[!UICONTROL Adobe Experience Platform Launch]**, compruebe lo siguiente:

   * En la parte inferior de la tarjeta se muestran dos puntos.
   * El punto de la izquierda es negro.

      Si el punto del lado derecho es negro, solo puede añadir desarrolladores. Para agregar un usuario, haga clic en el punto de la izquierda.
   c. Haga clic en **[!UICONTROL + Agregar usuarios]**.

   d. Introduzca el Adobe ID del usuario.

   e. Complete uno de los siguientes pasos:

   * Si va a agregar un nuevo usuario, haga clic en **[!UICONTROL Nuevo usuario]** e introduzca el nombre y los apellidos del usuario.
   * Si va a agregar un usuario existente, haga clic en el nombre del usuario que se muestra.

   f. En la lista desplegable **[!UICONTROL Seleccione un perfil para este producto]**, seleccione el perfil que ha editado anteriormente.

   g. Haga clic en **[!UICONTROL Guardar]**.

1. Agregue un usuario a **[!UICONTROL Servicios principales de Places]**.

   >[!TIP]
   >
   >Actualmente, todos los usuarios del Servicio de Places tienen los mismos permisos, por lo que no es necesario que edite los permisos.

   a. En la tarjeta **[!UICONTROL Places Core Services]**, compruebe lo siguiente:

   * En la parte inferior de la tarjeta se muestran dos puntos.
   * El punto de la izquierda es negro.

   b. Haga clic en **[!UICONTROL + Asignar usuarios]**.

   c. Introduzca el Adobe ID del usuario.

   d. Complete uno de los siguientes pasos:

   * Si va a agregar un nuevo usuario, haga clic en **[!UICONTROL Nuevo usuario]** e introduzca el nombre y los apellidos del usuario.
   * Si va a agregar un usuario existente, haga clic en el nombre del usuario que se muestra.

   e. En la lista desplegable **[!UICONTROL Seleccione un perfil para este producto]**, seleccione el perfil Places .

   f. Haga clic en **[!UICONTROL Guardar]**.

### Agregar un desarrollador

Para los usuarios que también necesitan acceso a la API de servicio web, debe agregarlos como Desarrollador.

Para agregar un desarrollador:

1. En la tarjeta **[!UICONTROL Servicios principales de Places]**, compruebe lo siguiente:

   * En la parte inferior de la tarjeta se muestran dos puntos.
   * Haga clic en el punto de la derecha para que **[!UICONTROL Assign Developers]** aparezca en la parte inferior de la tarjeta.

1. Haga clic en **[!UICONTROL + Asignar desarrolladores]**.

1. Introduzca el Adobe ID del usuario.

1. Complete uno de los siguientes pasos:

   * Si va a agregar un nuevo usuario, haga clic en **[!UICONTROL Nuevo usuario]** e introduzca el nombre y los apellidos del usuario.
   * Si va a agregar un usuario existente, haga clic en el nombre del usuario que se muestra.

1. En la lista desplegable **[!UICONTROL Seleccione un perfil para este producto]**, seleccione el perfil del servicio de Places.

1. Haga clic en **[!UICONTROL Guardar]**.

Los usuarios reciben un correo electrónico que les informa de que tienen acceso a Experience Platform Launch. Pueden iniciar sesión en la [Experience Platform Launch](https://launch.adobe.com) o en las [IU del servicio Places](https://places.adobe.com) de esta organización. Si completa el paso 4 del procedimiento **[!UICONTROL Añadir un desarrollador]**, el usuario también puede iniciar sesión en la [consola de Adobe I/O](https://console.adobe.io) para crear una integración de Places y utilizar la API de REST de Places.
