---
title: 'Obtener acceso al servicio de lugares '
description: Esta sección proporciona información sobre cómo agregar un usuario al servicio y Experience Platform Launch de lugares para que el usuario pueda acceder al servicio de lugares.
translation-type: tm+mt
source-git-commit: 26538602a73e806a4822705c7a3aa44d76351030
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 7%

---

# Obtener acceso al servicio de lugares {#adding-user-launch-places}

Puede acceder al servicio de lugares desde el menú de acceso rápido de [Adobe Experience Cloud Home](https://experience.adobe.com).
Si su ID de usuario tiene acceso, verá el icono Servicio de lugares como se indica a continuación:

![menú de acceso rápido](/help/assets/quickaccess.png)

También puede acceder al servicio de lugares desde el menú de Adobe Experience Platform:

![menú Experience Platform](/help/assets/solutionaccessmenu.png)

Si no ve el servicio de lugares en ninguno de estos menús, póngase en contacto con un administrador de su organización para agregar su ID de usuario al servicio principal de lugares del Admin Console.

## Añadir un usuario al servicio y Experience Platform Launch de lugares

Para permitir que los usuarios tengan acceso a la interfaz de usuario [del](https://launch.adobe.com)Experience Platform Launch, deben agregarse a Places Core Service en el Admin Console como usuario. Para permitir que los usuarios tengan acceso al Experience Platform Launch, configurar propiedades móviles y utilizar Lugares con el SDK de Adobe Experience Platform, deben agregarse al Experience Platform Launch en el Admin Console y se les deben otorgar los siguientes permisos para el Experience Platform Launch:

* Todos los derechos de propiedad:
   * Desarrollo
   * Aprobar
   * Publicar
   * Administrar extensiones
   * Administrar entornos
* Administrar propiedades, permiso en Derechos de Compañía

Si es la primera vez que agrega un usuario, complete los siguientes pasos para agregar usuarios a Experience Platform Launch y Servicio de lugares. Si ya ha agregado usuarios, es posible que se muestren varios perfiles, por lo que debe seleccionar el perfil correcto.

>[!IMPORTANT]
>
>Solo los administradores de organización pueden acceder al Admin Console y agregar los usuarios.

### 1. Verifique que el servicio y el Experience Platform Launch de lugares estén aprovisionados

1. Inicie sesión en su organización Experience Cloud.
1. En la parte superior derecha, haga clic en el conmutador de shell del Experience Cloud.

   ![conmutador de shell](/help/assets/places_shell_switcher1.png)

1. En **[!UICONTROL Platform]**, haga clic en **[!UICONTROL Administration]**.

   Si no ve **Administración** en la lista, no es administrador. Debe ponerse en contacto con el administrador de su organización para completar este procedimiento.

1. En la página Administración de Experience Cloud, en la **[!UICONTROL Admin Console]** tarjeta, haga clic en **[!UICONTROL Take me there]**.

1. En el Admin Console, si tiene acceso a varias organizaciones, compruebe que la organización correcta esté seleccionada en la parte superior derecha de la página.

   Ésta es la organización a la que agregará los usuarios. Si no se ha seleccionado la organización correcta, haga clic en la organización y seleccione la organización en la lista desplegable.

   >[!IMPORTANT]
   >
   >Si no tiene acceso a una organización, significa que no tiene acceso de administrador a esa organización.

1. Verifique que se muestren las tarjetas para **[!UICONTROL Adobe Experience Platform Launch]** y **[!UICONTROL Places Core Services]** .

   ![](/help/assets/places_provisioned1.png)

   Si se muestran, el servicio de lugares y el Experience Platform Launch se han aprovisionado para su organización. Si no se muestran, deben aprovisionarse para su organización.


### 2. Configure el perfil y agregue los permisos

1. Configure un perfil de Experience Platform Launch que permita a los usuarios que se han agregado al perfil utilizar Experience Platform Launch y sus propiedades móviles con el SDK de Experience Platform.

   a. En la barra de menús, haga clic en **[!UICONTROL Product]**.

   b. En el panel izquierdo, en la lista de productos, haga clic en **[!UICONTROL Adobe Experience Platform Launch]**.

   * Los perfiles del Experience Platform Launch aparecen a la derecha.
   * Experience Platform Launch tiene un perfil predeterminado llamado *Launch - (nombre de la organización)* .

      Si agregó usuarios anteriormente a Experience Platform Launch, es posible que vea varios perfiles en la lista.

1. Seleccione el perfil correcto:

   a. Haga clic en el nombre del perfil predeterminado.

   b. Click the **[!UICONTROL Permissions]** tab.

   c. Haga clic en **[!UICONTROL Edit]** junto a **[!UICONTROL Property Rights]**.

   d. En el panel izquierdo, haga clic en **[!UICONTROL + Add all]**.

   Este paso mueve todos los permisos disponibles a la lista de permisos incluida.

   e. Haga clic en **[!UICONTROL Company Rights]**.

   f. En el panel izquierdo, haga clic en **[!UICONTROL + Manage Properties]**.

   g. Haga clic en **[!UICONTROL Save]**.

>[!IMPORTANT]
>
>Para el servicio de lugares, existe un perfil predeterminado, pero no es necesario agregar permisos.

Ha agregado correctamente permisos al perfil que ha creado.

### 3. Añadir un usuario o un programador a los perfiles de Experience Platform Launch y del servicio de lugares

Puede agregar un usuario y/o un desarrollador a sus perfiles de Experience Platform Launch y Servicio de lugares.

### Añadir un usuario

Para agregar un usuario a sus perfiles de Experience Platform Launch y Servicio de lugares:

1. Añada un usuario al perfil de Experience Platform Launch.

   a. En la barra de menús, haga clic en **[!UICONTROL Overview]**.

   b. En la **[!UICONTROL Adobe Experience Platform Launch]** tarjeta, compruebe lo siguiente:

   * En la parte inferior de la tarjeta se muestran dos puntos.
   * El punto de la izquierda es negro.

      Si el punto de la derecha es negro, solo puede agregar desarrolladores. Para agregar un usuario, haga clic en el punto de la izquierda.
   c. Haga clic en **[!UICONTROL + Add Users]**.

   d. Introduzca el Adobe ID del usuario.

   e. Complete uno de los siguientes pasos:

   * Si va a agregar un usuario nuevo, haga clic en **[!UICONTROL New user]** y escriba el nombre y los apellidos del usuario.
   * Si va a agregar un usuario existente, haga clic en el nombre del usuario que se muestra.

   f. En la lista **[!UICONTROL Please select a profile for this product]** desplegable, seleccione el perfil que ha editado anteriormente.

   g. Haga clic en **[!UICONTROL Save]**.

1. Añada un usuario a **[!UICONTROL Places Core Services]**.

   >[!TIP]
   >
   >Actualmente, todos los usuarios de Places Service tienen los mismos permisos, por lo que no es necesario editar los permisos.

   a. En la **[!UICONTROL Places Core Services]** tarjeta, compruebe lo siguiente:

   * En la parte inferior de la tarjeta se muestran dos puntos.
   * El punto de la izquierda es negro.

   b. Haga clic en **[!UICONTROL + Assign Users]**.

   c. Introduzca el Adobe ID del usuario.

   d. Complete uno de los siguientes pasos:

   * Si va a agregar un usuario nuevo, haga clic en **[!UICONTROL New user]** y escriba el nombre y los apellidos del usuario.
   * Si va a agregar un usuario existente, haga clic en el nombre del usuario que se muestra.

   e. En la lista **[!UICONTROL Please select a profile for this product]** desplegable, seleccione el perfil Lugares.

   f. Haga clic en **[!UICONTROL Save]**.

### Añadir un desarrollador

Para los usuarios que también necesitan acceder a la API de servicio Web, debe agregarlos como programadores.

Para agregar un desarrollador:

1. En la **[!UICONTROL Places Core Services]** tarjeta, compruebe lo siguiente:

   * En la parte inferior de la tarjeta se muestran dos puntos.
   * Haga clic en el punto de la derecha para que **[!UICONTROL Assign Developers]** aparezca en la parte inferior de la tarjeta.

1. Haga clic en **[!UICONTROL + Assign Developers]**.

1. Introduzca el Adobe ID del usuario.

1. Complete uno de los siguientes pasos:

   * Si va a agregar un usuario nuevo, haga clic en **[!UICONTROL New user]** y escriba el nombre y los apellidos del usuario.
   * Si va a agregar un usuario existente, haga clic en el nombre del usuario que se muestra.

1. En la lista **[!UICONTROL Please select a profile for this product]** desplegable, seleccione el perfil de servicio Lugares.

1. Haga clic en **Guardar**.

Los usuarios reciben un correo electrónico que les informa de que tienen acceso a Experience Platform Launch. They can can log in to the [Experience Platform Launch](https://launch.adobe.com) or the [Places Service](https://places.adobe.com) UIs for this organization. Si completa el paso 4 del procedimiento **Añadir un desarrollador**, el usuario también puede iniciar sesión en la [consola de Adobe I/O](https://console.adobe.io) para crear una integración de Places y utilizar la API de REST de Places.
