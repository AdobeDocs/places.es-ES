---
title: Obtener acceso al servicio Places
description: En esta sección se proporciona información sobre cómo añadir un usuario al servicio Places y a Experience Platform Launch para que pueda acceder al servicio Places.
exl-id: f388945e-cf26-4694-9697-9fe564ae4b69
TQID: https://experienceleague.adobe.com/EYg1wjQJZeHqX7vPnJ1VUZzojqG6ANjS8-VBXV3y51c
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
  - id: f7bdf6be-dd3b-4d2d-ac52-0e62ed0d3102
feature_v2:
  - id: c132d929-fa62-4271-803e-b823be07b914
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: b64298cc-90cc-46b7-8917-ee391f1c7516
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
  - id: f5efb499-54f9-432b-ac5c-599dbac103af
  - id: f6ff4d13-7b5c-4533-8556-95e76673d4cb
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 919
ht-degree: 1%

---

# Obtener acceso al servicio Places {#adding-user-launch-places}

El servicio Places ya está disponible en la IU de recopilación de datos. Puede acceder a la recopilación de datos desde el menú de acceso rápido de [inicio de Adobe Experience Cloud](https://experience.adobe.com).

![menú de acceso rápido](/help/assets/quickaccess.png)

También puede acceder a la recopilación de datos desde el menú Adobe Experience Platform:

![menú Experience Platform](/help/assets/solutionaccessmenu.png)

Si su ID de usuario tiene acceso, verá el icono de Places Service en el panel izquierdo, debajo de Administración de datos, en Recopilación de datos, como se indica a continuación:

![Panel izquierdo de recopilación de datos](/help/assets/places_in_data_collection.png)

Si no ve el servicio Places en esta ubicación, póngase en contacto con un administrador de su organización para agregar su ID de usuario a Adobe Experience Platform en Admin Console.

## Añadir un usuario para acceder al servicio Places y a la recopilación de datos de Experience Adobe Experience Platform

Places ahora se incluye con Adobe Experience Platform. Para permitir que los usuarios tengan acceso al [Servicio Places](https://experience.adobe.com/#/data-collection/places), deben agregarse a Adobe Experience Platform en Admin Console como usuarios. Para permitir que los usuarios tengan acceso a la recopilación de datos de Experience Platform con los permisos necesarios para configurar propiedades móviles y utilizar Places con Adobe Experience Platform SDK, también deben añadirse a la recopilación de datos de Adobe Experience Platform en Admin Console y se les deben otorgar los siguientes permisos para la recopilación de datos de Adobe Experience Platform:

* Todos los permisos en Derechos de propiedad:
   * Aprobar
   * Desarrollo
   * Editar propiedad
   * Administrar entornos
   * Administración de extensiones
   * Publicación
* Permiso Administrar propiedades en Derechos de compañía

Si es la primera vez que añade un usuario, complete los siguientes pasos para añadir usuarios a la recopilación de datos de Adobe Experience Platform y a Adobe Experience Platform. Si ya ha agregado usuarios anteriormente, es posible que se muestren varios perfiles, por lo que debe asegurarse de seleccionar el perfil correcto.

>[!IMPORTANT]
>
>Solo los administradores de organización pueden acceder a Admin Console y añadir a los usuarios.

### &#x200B;1. Compruebe que la recopilación de datos de Adobe Experience Platform y Adobe Experience Platform esté aprovisionada

1. Inicie sesión en su organización de Experience Cloud, [hogar de Adobe Experience Cloud](https://experience.adobe.com).
1. En el lado superior derecho, haga clic en el conmutador de shell de Experience Cloud para mostrar un menú desplegable.

   ![conmutador de shell](/help/assets/places_shell_switcher1.png)

1. Al final de la lista, haz clic en **[!UICONTROL Admin Console]**. (También se puede encontrar un vínculo a **[!UICONTROL Admin Console]** en la sección Acceso rápido).

   Si no ve **[!UICONTROL Admin Console]** en la lista, no es administrador. Debe ponerse en contacto con el administrador de su organización para completar este procedimiento.

1. En Admin Console, si tiene acceso a varias organizaciones, compruebe que la organización correcta esté seleccionada en la parte superior derecha de la página.

   Esta es la organización a la que agregará los usuarios. Si no se ha seleccionado la organización correcta, haga clic en la organización y seleccione la organización correcta en la lista desplegable.

   >[!IMPORTANT]
   >
   >Si la organización deseada no está en la lista desplegable, significa que no tiene acceso de administrador a esa organización.

1. En Admin Console, haga clic en la ficha Productos y compruebe que se muestran las tarjetas de **[!UICONTROL recopilación de datos de Adobe Experience Platform]** y **[!UICONTROL Adobe Experience Platform]**.

   ![](/help/assets/places_provisioned1.png)

   Estos 2 productos se aprovisionan automáticamente para todas las organizaciones, por lo que deben estar presentes.


### &#x200B;2. Añadir usuario a estos productos

#### Añadir usuario para proporcionar acceso a la IU del servicio Places

1. En la ficha Productos, haga clic en la tarjeta **[!UICONTROL Adobe Experience Platform]**.
2. Se puede agregar un usuario a cualquier perfil dentro de **[!UICONTROL Adobe Experience Platform]** para obtener acceso a Places; no es necesario establecer permisos específicos.
3. Elija un perfil (si hay más de uno) y haga clic en él para abrirlo.
4. Haga clic en el botón azul **Agregar usuario**, rellene el usuario con su Adobe ID y su nombre y, a continuación, haga clic en Guardar para completar la adición.

#### Añadir un usuario a la recopilación de datos

1. En la pestaña Productos, haga clic en la tarjeta **[!UICONTROL Recopilación de datos de Adobe Experience Platform]**.
2. De manera predeterminada, se habrá creado un perfil con el nombre **Recopilación de datos predeterminada para todo el acceso**. Añadir un usuario a este perfil garantizará que tiene los permisos adecuados para trabajar con el servicio Places y la recopilación de datos. Si se elige un perfil diferente, asegúrese de que se incluyen los permisos mencionados anteriormente.
3. Elija un perfil (si hay más de uno) y haga clic en él para abrirlo.
4. Haga clic en el botón azul **Agregar usuario**, rellene el usuario con su Adobe ID y su nombre y, a continuación, haga clic en Guardar para completar la adición.

#### Añada un usuario como desarrollador para el servicio Places.

Para los usuarios que también necesitan acceder a la API de REST del servicio Places, debe añadirlos como Desarrollador.
1. En la ficha Productos, haga clic en la tarjeta **[!UICONTROL Adobe Experience Platform]**.
2. Si el usuario ya se agregó a la tarjeta **[!UICONTROL Adobe Experience Platform]** a través de las instrucciones anteriores, elija el mismo perfil utilizado anteriormente y haga clic en él.
3. En el perfil, haga clic en la ficha **Desarrolladores**
4. Haga clic en el botón azul **Agregar desarrollador**, rellene el usuario con su Adobe ID y su nombre y, a continuación, haga clic en Guardar para completar la adición.

Una vez completados los pasos anteriores, el usuario recibirá un correo electrónico que le notificará que tiene acceso a **[!UICONTROL Adobe Experience Platform]** y a **[!UICONTROL Recopilación de datos de Adobe Experience Platform]**. Luego pueden iniciar sesión en [Adobe Experience Cloud](https://experience.adobe.com) para esta organización y acceder al servicio Places y a la recopilación de datos. Si también completa los pasos **[!UICONTROL Agregar un desarrollador]**, el usuario también puede iniciar sesión en [Adobe Developer Console](https://developer.adobe.com/console/home) para crear un proyecto que proporcionaría acceso a la API de REST del servicio de Places.
