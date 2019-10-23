---
title: Administrar bibliotecas en la interfaz de usuario de Lugares
seo-title: Administrar bibliotecas en la interfaz de usuario de Lugares
description: Administre sus bibliotecas mediante la IU de lugares.
seo-description: Administre sus bibliotecas mediante la IU de lugares.
translation-type: tm+mt
source-git-commit: fdfeb8c17820c4eb0eae249da39be4eebece22d3

---


# Administrar bibliotecas en la interfaz de usuario de Lugares {#manage-libraries-places-ui}

Una biblioteca es una colección de puntos de interés. Puede tener hasta 150.000 puntos de interés en una biblioteca y puede haber hasta 100 bibliotecas por organización de Experience Cloud.

Existen varias formas de organizar los puntos de interés en bibliotecas, según lo que resulte más útil para su organización. Algunos clientes pueden preferir crear una biblioteca independiente para cada aplicación móvil, mientras que otros pueden usar bibliotecas para agrupar tipos específicos de puntos de interés como cafeterías, parques, hoteles, etc. Por ejemplo, una gran empresa de entretenimiento podría tener una biblioteca que comprenda sus locales al aire libre en una biblioteca y sus tiendas minoristas en otra biblioteca. Un gobierno municipal podría tener una biblioteca que comprenda todos los edificios de la ciudad y otra biblioteca que incluya todos los parques de la ciudad.

Las bibliotecas se definen de la siguiente manera:

| Claves: | Descripción: |
| :--- | :--- |
| ID | un identificador único asignado a la biblioteca en el momento de la creación |
| Nombre | un nombre descriptivo asignado a una biblioteca |
| Clasificación | Estas clasificaciones se pueden ignorar si no hay geofences superpuestas en la organización. Si hay puntos de interés superpuestos, le recomendamos que coloque cada una de las geofences en bibliotecas independientes para que se puedan ponderar entre sí. Un usuario solo puede estar en una sola geofencia a la vez. <br><br>La clasificación más alta de las geofences en las que se encuentra un usuario determina su pertenencia a la geografía actual. Si hay geofences con la misma clasificación de biblioteca, la geofence más pequeña es la geofence actual del usuario. <br><br>El SDK también tiene conocimiento de los puntos de interés de *última entrada* y de *última salida* , por lo que dispone de un control completo de cómo desea que se activen las reglas en función de la interacción del usuario con los puntos de interés. |

## Crear una biblioteca

1. Inicie sesión en Adobe Places con su Adobe ID.
2. En la parte superior derecha, haga clic en **[!UICONTROL ...]** &gt; **[!UICONTROL Manage Libraries]**.
3. Haga clic en **[!UICONTROL New]**.
4. Escriba el nombre.
5. Haga clic en **[!UICONTROL Confirm]**.

## Cambiar la clasificación de una biblioteca en la interfaz de usuario de Lugares

1. Inicie sesión en Adobe Places con su Adobe ID.
2. En la parte superior derecha, haga clic en **[!UICONTROL ...]** &gt; **[!UICONTROL Manage Libraries]**.
3. Haga clic en el icono a la izquierda del nombre de la biblioteca y arrastre la biblioteca a la nueva clasificación.

## Cambio del nombre de una biblioteca

1. Inicie sesión en Adobe Places con su Adobe ID.
2. En la parte superior derecha, haga clic en **[!UICONTROL ...]** &gt; **[!UICONTROL Manage Libraries]**.
3. Busque la biblioteca que desee eliminar.
4. Haga clic **[!UICONTROL ...]** y seleccione **[!UICONTROL Rename]**.
5. Actualice el nombre y haga clic en **[!UICONTROL Save]**.

## Eliminar una biblioteca

1. Inicie sesión en Adobe Places con su Adobe ID.
2. En la parte superior derecha, haga clic en **[!UICONTROL ...]** &gt; **[!UICONTROL Manage Libraries]**.
3. Busque la biblioteca que desee eliminar.
4. Haga clic **[!UICONTROL ...]** y seleccione **[!UICONTROL Delete]**.
