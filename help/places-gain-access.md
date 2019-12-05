---
title: Acceso al servicio de ubicación de Adobe Experience Platform
seo-title: Acceso al servicio de ubicación de Adobe Experience Platform
description: En esta sección se proporciona información sobre cómo agregar un usuario al servicio de ubicación y al inicio de la plataforma de experiencia para que el usuario pueda acceder al servicio de ubicación.
seo-description: En esta sección se proporciona información sobre cómo agregar un usuario al servicio de ubicación y al inicio de la plataforma de experiencia para que el usuario pueda acceder al servicio de ubicación.
translation-type: tm+mt
source-git-commit: 1b4482c8e4cf825c0182421fe00f8b86b411c11b

---


# Acceso al servicio de ubicación de Adobe Experience Platform {#adding-user-launch-places}

Puede acceder al servicio de ubicación de plataforma desde el menú de acceso rápido de la página principal de [Adobe Experience Cloud](https://experience.adobe.com).
Si su ID de usuario tiene acceso, verá el icono del servicio de ubicación como se indica a continuación:

![menú de acceso rápido](/help/assets/quick-access.png)

También puede acceder al servicio de ubicación de plataforma desde el menú Adobe Experience Platform:

![Menú Plataforma de experiencia](/help/assets/exp-platform-menu-sm.png)

Si no ve el servicio de ubicación de plataforma en ninguno de estos menús, deberá ponerse en contacto con un administrador de su organización para agregar su ID de usuario al servicio principal de lugares en la Consola de administración.

## Adición de un usuario al servicio de ubicación y al inicio de la plataforma de experiencia

Para permitir que los usuarios tengan acceso a la interfaz de usuario [del servicio de](https://places.adobe.com)inicio, deben agregarse a Places Core Service en Admin Console como usuarios. Para permitir que los usuarios tengan acceso al lanzamiento de la plataforma de experiencia, configurar propiedades móviles y utilizar Lugares con el SDK de la plataforma de experiencia de Adobe, deben agregarse al inicio de la plataforma de experiencia en Admin Console y se les deben otorgar los siguientes permisos para el lanzamiento de la plataforma de experiencia:

* Todos los derechos de propiedad:
   * Desarrollo
   * Aprobar
   * Publicar
   * Administrar extensiones
   * Administrar entornos
* Administrar el permiso Propiedades en Derechos de la empresa

Si es la primera vez que agrega un usuario, complete los siguientes pasos para agregar usuarios al servicio de inicio y ubicación de la plataforma de experiencia. Si ya ha agregado usuarios, es posible que se muestren varios perfiles, por lo que debe seleccionar el perfil correcto.

>[!IMPORTANT]
>
>Solo los administradores de organización pueden acceder a Admin Console y agregar los usuarios.

### 1. Compruebe que el servicio de ubicación y el inicio de la plataforma de experiencia están aprovisionados

Para verificar que el servicio de ubicación y el inicio de la plataforma de experiencia están aprovisionados:

1. Inicie sesión en su organización de Experience Cloud.
1. En la parte superior derecha, haga clic en el conmutador de shell de Experience Cloud.

   ![conmutador de shell](/help/assets/places_shell_switcher1.png)

1. En **[!UICONTROL Platform]**, haga clic en **[!UICONTROL Administration]**.

   Si no ve **Administración** en la lista, no es administrador. Debe ponerse en contacto con el administrador de su organización para completar este procedimiento.

1. En la página Administración de Experience Cloud, en la **[!UICONTROL Admin Console]** tarjeta, haga clic en **[!UICONTROL Take me there]**.

1. En Admin Console, si tiene acceso a varias organizaciones, compruebe que la organización correcta esté seleccionada en la parte superior derecha de la página.

   Ésta es la organización a la que agregará los usuarios. Si no se ha seleccionado la organización correcta, haga clic en la organización y selecciónela en la lista desplegable.

   >[!IMPORTANT]
   >
   >Si no tiene acceso a una organización, significa que no tiene acceso de administrador a esa organización.

1. Verifique que se muestren las tarjetas para **[!UICONTROL Adobe Experience Platform Launch]** y **[!UICONTROL Places Core Services]** .

   ![](/help/assets/places_provisioned1.png)

   Si se muestran, el servicio de ubicación y el inicio de la plataforma de experiencia se han aprovisionado para su organización. Si no se muestran, deben aprovisionarse para su organización.


### 2. Configure el perfil y agregue los permisos

Para configurar el perfil y agregar los permisos:

1. Configure un perfil de inicio de plataforma de experiencia, que permite a los usuarios que se han agregado al perfil utilizar Inicio de plataforma de experiencia y sus propiedades móviles con el SDK de plataforma de experiencia.

    a. En la barra de menús, haga clic en **[!UICONTROL Product]**.

   b. En el panel izquierdo, en la lista de productos, haga clic en **[!UICONTROL Adobe Experience Platform Launch]**.

   * Los perfiles de inicio de la plataforma de experiencia aparecen a la derecha.
   * Experience Platform Launch tiene un perfil predeterminado llamado *Launch - (nombre de la organización)* .

      Si agregó usuarios anteriormente a Inicio de plataforma de experiencia, es posible que vea varios perfiles en la lista.

1. Seleccione el perfil correcto:

    a. Haga clic en el nombre del perfil predeterminado.

   b. Haga clic en la **[!UICONTROL Permissions]** ficha.

   c. Haga clic en **[!UICONTROL Edit]** junto a **[!UICONTROL Property Rights]**.

   d. En el panel izquierdo, haga clic en **[!UICONTROL + Add all]**.

   Este paso mueve todos los permisos disponibles a la lista de permisos incluidos.

   e.Haga clic en **[!UICONTROL Company Rights]**.

   f. En el panel izquierdo, haga clic en **[!UICONTROL + Manage Properties]**.

   g.Haga clic en **[!UICONTROL Save]**.

>[!IMPORTANT]
>
>Para el servicio de ubicación, hay un perfil predeterminado, pero no tiene que agregar permisos.

Ha agregado permisos correctamente al perfil que ha creado.

### 3. Agregue un usuario o un desarrollador a sus perfiles Servicio de ubicación y Inicio de plataforma de experiencia

Puede agregar un usuario y/o un desarrollador a sus perfiles de Servicio de ubicación e Inicio de plataforma de experiencia.

### Agregación de un usuario

Para agregar un usuario a sus perfiles de Servicio de ubicación y Inicio de plataforma de experiencia:

1. Agregue un usuario al perfil Inicio de plataforma de experiencia.

    a. En la barra de menús, haga clic en **[!UICONTROL Overview]**.

   b. En la **[!UICONTROL Adobe Experience Platform Launch]** tarjeta, compruebe lo siguiente:

   * En la parte inferior de la tarjeta se muestran dos puntos.
   * El punto de la izquierda es negro.

      Si el punto de la derecha es negro, solo puede agregar desarrolladores. Para agregar un usuario, haga clic en el punto de la izquierda.
   c.Haga clic en **[!UICONTROL + Add Users]**.

   d. Introduzca el Adobe ID del usuario.

   e. Complete uno de los siguientes pasos:

   * Si va a agregar un usuario nuevo, haga clic en **[!UICONTROL New user]** y escriba el nombre y los apellidos del usuario.
   * Si va a agregar un usuario existente, haga clic en el nombre del usuario que se muestra.
   f. En la lista **[!UICONTROL Please select a profile for this product]** desplegable, seleccione el perfil que ha editado anteriormente.

   g.Haga clic en **[!UICONTROL Save]**.

1. Agregue un usuario a **[!UICONTROL Places Core Services]**.

   >[!TIP]
   >
   >Actualmente, todos los usuarios del servicio de ubicación tienen los mismos permisos, por lo que no es necesario editarlos.

    a. En la **[!UICONTROL Places Core Services]** tarjeta, compruebe lo siguiente:

   * En la parte inferior de la tarjeta se muestran dos puntos.
   * El punto de la izquierda es negro.
   b.Haga clic en **[!UICONTROL + Assign Users]**.

   c. Introduzca el Adobe ID del usuario.

   d. Complete uno de los siguientes pasos:

   * Si va a agregar un usuario nuevo, haga clic en **[!UICONTROL New user]** y escriba el nombre y los apellidos del usuario.
   * Si va a agregar un usuario existente, haga clic en el nombre del usuario que se muestra.
   e. En la lista **[!UICONTROL Please select a profile for this product]** desplegable, seleccione el perfil Lugares.

   f.Haga clic en **[!UICONTROL Save]**.

### Agregar un desarrollador

Para los usuarios que también necesitan acceder a la API de servicio Web, debe agregarlos como programadores.

Para agregar un desarrollador:

1.  En la **[!UICONTROL Places Core Services]** tarjeta, compruebe lo siguiente:

   * En la parte inferior de la tarjeta se muestran dos puntos.
   * Haga clic en el punto de la derecha para que **[!UICONTROL Assign Developers]** aparezca en la parte inferior de la tarjeta.

1. Haga clic en **[!UICONTROL + Assign Developers]**.

1. Introduzca el Adobe ID del usuario.

1. Complete uno de los siguientes pasos:

   * Si va a agregar un usuario nuevo, haga clic en **[!UICONTROL New user]** y escriba el nombre y los apellidos del usuario.
   * Si va a agregar un usuario existente, haga clic en el nombre del usuario que se muestra.

1. En la lista **[!UICONTROL Please select a profile for this product]** desplegable, seleccione el perfil del servicio de ubicación.

1. Haga clic en **Guardar**.

Los usuarios reciben un correo electrónico que les informa de que tienen acceso a Experience Platform Launch. Pueden iniciar sesión en [Experience Platform Launch](https://launch.adobe.com) o en las IU de [Places](https://places.adobe.com) de esta organización. Si completa el paso 4 del procedimiento **Añadir un desarrollador**, el usuario también puede iniciar sesión en la [consola de Adobe I/O](https://console.adobe.io) para crear una integración de Places y utilizar la API de REST de Places.
