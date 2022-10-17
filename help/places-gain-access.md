---
title: Obtener acceso al servicio Places
description: En esta sección se proporciona información sobre cómo agregar un usuario al servicio y al Experience Platform Launch de Places para que el usuario pueda acceder al servicio de Places.
exl-id: f388945e-cf26-4694-9697-9fe564ae4b69
source-git-commit: c9058e9b70c2ef97151078f43913963471730bd2
workflow-type: tm+mt
source-wordcount: '913'
ht-degree: 1%

---

# Obtener acceso al servicio Places {#adding-user-launch-places}

El servicio de Places ya está disponible en la interfaz de usuario de la recopilación de datos. Puede acceder a la Recopilación de datos desde el menú de acceso rápido situado en [Inicio de Adobe Experience Cloud](https://experience.adobe.com).

![menú acceso rápido](/help/assets/quickaccess.png)

También puede acceder a la Recopilación de datos desde el menú de Adobe Experience Platform:

![menú Experience Platform](/help/assets/solutionaccessmenu.png)

Si su ID de usuario tiene acceso, verá el icono Servicio de Places en el panel izquierdo, en Gestión de datos, en Recopilación de datos, como se indica a continuación:

![Panel izquierdo de recopilación de datos](/help/assets/places_in_data_collection.png)

Si no ve el servicio de Places en esta ubicación, póngase en contacto con un administrador de su organización para agregar su ID de usuario a Adobe Experience Platform en el Admin Console.

## Añadir un usuario para acceder al servicio Places y a la recopilación de datos de Experience Adobe Experience Platform

Places ahora se incluye con Adobe Experience Platform. Para permitir que los usuarios accedan al [Servicio de Places](https://experience.adobe.com/#/recopilación de datos/lugares), deben añadirse a Adobe Experience Platform en el Admin Console como usuario. Para permitir que los usuarios tengan acceso a la recopilación de datos de Experience Platform con los permisos necesarios para configurar propiedades móviles y utilizar Places con el SDK de Adobe Experience Platform, también deben agregarse a la recopilación de datos de Adobe Experience Platform en el Admin Console y se les deben otorgar los siguientes permisos para la recopilación de datos de Adobe Experience Platform:

* Todos los permisos en Derechos de propiedad:
   * Aprobar
   * Desarrollo
   * Editar propiedad
   * Administrar entornos
   * Administrar extensiones
   * Publicar
* Permiso Administrar propiedades en Derechos de compañía

Si es la primera vez que agrega un usuario, complete los siguientes pasos para agregar usuarios a la recopilación de datos de Adobe Experience Platform y Adobe Experience Platform. Si ha añadido usuarios anteriormente, es posible que se muestren varios perfiles, por lo que debe seleccionar el perfil correcto.

>[!IMPORTANT]
>
>Solo los administradores de organización pueden acceder al Admin Console y añadir a los usuarios.

### 1. Compruebe que la recopilación de datos de Adobe Experience Platform y Adobe Experience Platform esté aprovisionada

1. Inicie sesión en su organización de Experience Cloud. [Inicio de Adobe Experience Cloud](https://experience.adobe.com).
1. En el lado superior derecho, haga clic en el selector de shell del Experience Cloud para mostrar un menú desplegable.

   ![alternador de shell](/help/assets/places_shell_switcher1.png)

1. En la parte inferior de la lista, haga clic en **[!UICONTROL Admin Console]**. (Un vínculo a la **[!UICONTROL Admin Console]** también se encuentra en la sección Acceso rápido ).

   Si no ve **[!UICONTROL Admin Console]** en la lista, no es administrador. Debe ponerse en contacto con el administrador de organización para completar este procedimiento.

1. En el Admin Console, si tiene acceso a varias organizaciones, compruebe que la organización correcta esté seleccionada en la parte superior derecha de la página.

   Esta es la organización a la que agregará a los usuarios. Si no se ha seleccionado la organización correcta, haga clic en la organización y seleccione la organización correcta en la lista desplegable.

   >[!IMPORTANT]
   >
   >Si la organización deseada no está en la lista desplegable, significa que no tiene acceso de administrador a esa organización.

1. En el Admin Console, haga clic en la pestaña Productos y compruebe que las tarjetas de **[!UICONTROL Recopilación de datos de Adobe Experience Platform]** y **[!UICONTROL Adobe Experience Platform]** se muestran.

   ![](/help/assets/places_provisioned1.png)

   Estos 2 productos se aprovisionan automáticamente a todas las organizaciones, por lo que deben estar presentes.


### 2. Agregar usuario a estos productos

#### Agregar usuario para proporcionar acceso a la interfaz de usuario del servicio de Places

1. En la pestaña Productos , haga clic en el **[!UICONTROL Adobe Experience Platform]** tarjeta.
2. Se puede agregar un usuario a cualquier perfil dentro de **[!UICONTROL Adobe Experience Platform]** para obtener acceso a Places, no es necesario configurar ningún permiso específico.
3. Elija un perfil (si hay más de uno) y haga clic en él para abrirlo.
4. Haga clic en el icono azul **Agregar usuario** , rellene el usuario con su Adobe ID y nombre y, a continuación, haga clic en Guardar para completar la adición.

#### Agregar usuario a la recopilación de datos

1. En la pestaña Productos , haga clic en el **[!UICONTROL Recopilación de datos de Adobe Experience Platform]** tarjeta.
2. De forma predeterminada, un perfil denominado **Acceso a la recopilación de datos predeterminada** se habrá creado. Al agregar un usuario a este perfil, se asegurará de que tenga los permisos adecuados para trabajar con el servicio de Places y la recopilación de datos. Si se elige un perfil diferente, asegúrese de que se incluyen los permisos mencionados anteriormente.
3. Elija un perfil (si hay más de uno) y haga clic en él para abrirlo.
4. Haga clic en el icono azul **Agregar usuario** , rellene el usuario con su Adobe ID y nombre y, a continuación, haga clic en Guardar para completar la adición.

#### Agregue un usuario como desarrollador para el servicio Places.

Para los usuarios que también necesitan acceso a la API de REST del servicio Places, debe agregarlos como Desarrollador.
1. En la pestaña Productos , haga clic en el **[!UICONTROL Adobe Experience Platform]** tarjeta.
2. Si el usuario ya se ha agregado a **[!UICONTROL Adobe Experience Platform]** a través de las instrucciones anteriores, elija el mismo perfil utilizado anteriormente y haga clic en él.
3. Dentro del perfil, haga clic en el **Desarrolladores** ficha
4. Haga clic en el icono azul **Agregar desarrollador** , rellene el usuario con su Adobe ID y nombre y, a continuación, haga clic en Guardar para completar la adición.

Después de completar los pasos anteriores, el usuario recibirá un correo electrónico que le notifica que tiene acceso a **[!UICONTROL Adobe Experience Platform]** y **[!UICONTROL Recopilación de datos de Adobe Experience Platform]**. A continuación, pueden iniciar sesión en el [Adobe Experience Cloud](https://experience.adobe.com) para esta organización y acceda a Servicio de Places y Recopilación de datos. Si también completa los pasos **[!UICONTROL Agregar un desarrollador]**, el usuario también puede iniciar sesión en la [Consola de Adobe Developer](https://developer.adobe.com/console/home) para crear un proyecto que proporcione acceso a la API de REST del servicio Places.
