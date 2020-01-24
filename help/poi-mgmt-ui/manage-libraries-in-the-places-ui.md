---
title: Administrar bibliotecas en la interfaz de usuario del servicio de lugares
description: Administre sus bibliotecas mediante la interfaz de usuario del servicio de lugares.
translation-type: tm+mt
source-git-commit: 5a21e734c0ef56c815389a9f08b445bedaae557a

---


# Manage libraries {#manage-libraries-places-ui}

Una biblioteca es una colección de puntos de interés. Puede tener hasta 150.000 puntos de interés en una biblioteca y puede haber hasta 100 bibliotecas por organización de Experience Cloud.

Existen varias formas de organizar los puntos de interés en bibliotecas, según lo que resulte más útil para su organización. Algunos clientes pueden preferir crear una biblioteca independiente para cada aplicación móvil, mientras que otros pueden usar bibliotecas para agrupar tipos específicos de puntos de interés como cafeterías, parques, hoteles, etc. Por ejemplo, una gran empresa de entretenimiento podría tener una biblioteca que comprenda sus locales al aire libre en una biblioteca y sus tiendas minoristas en otra biblioteca. Un gobierno municipal podría tener una biblioteca que comprenda todos los edificios de la ciudad y otra biblioteca que incluya todos los parques de la ciudad.

Las bibliotecas se definen de la siguiente manera:

| Claves: | Descripción: |
| :--- | :--- |
| ID | un identificador único asignado a la biblioteca en el momento de la creación |
| Nombre | un nombre descriptivo asignado a una biblioteca |
| Clasificación | Estas clasificaciones se pueden ignorar si no hay geofences superpuestas en la organización. Si hay puntos de interés superpuestos, le recomendamos que coloque cada una de las geovallas en bibliotecas independientes para que se puedan ponderar entre sí. Un usuario solo puede estar en una sola geovalla a la vez. <br><br>La clasificación más alta de las geovallas en las que se encuentra un usuario determina su pertenencia a la geovalla actual. Si hay geofences que tienen la misma clasificación de biblioteca, la geofence más pequeña es la geofence actual del usuario. <br><br>El SDK también tiene conocimiento de los puntos de interés de *Última entrada* y de *Última salida*, por lo que dispone de un control completo de cómo desea que se activen las reglas en función de la interacción del usuario con los puntos de interés. |

## Crear una biblioteca

1. Inicie sesión en lugares con su Adobe ID.
1. En la parte superior derecha, haga clic en **[!UICONTROL ...]**>**[!UICONTROL Manage Libraries]**.
1. Haga clic en **[!UICONTROL New]**.
1. Escriba el nombre.
1. Haga clic en **[!UICONTROL Confirm]**.

## Cambiar la clasificación de una biblioteca en la interfaz de usuario de Lugares

1. Inicie sesión en lugares con su Adobe ID.
1. En la parte superior derecha, haga clic en **[!UICONTROL ...]**>**[!UICONTROL Manage Libraries]**.
1. Haga clic en el icono a la izquierda del nombre de la biblioteca y arrastre la biblioteca a la nueva clasificación.

## Cambio del nombre de una biblioteca

1. Inicie sesión en lugares con su Adobe ID.
1. En la parte superior derecha, haga clic en **[!UICONTROL ...]**>**[!UICONTROL Manage Libraries]**.
1. Busque la biblioteca que desee eliminar.
1. Haga clic **[!UICONTROL ...]**y seleccione**[!UICONTROL Rename]**.
1. Actualice el nombre y haga clic en **[!UICONTROL Save]**.

## Eliminar una biblioteca

1. Inicie sesión en lugares con su Adobe ID.
1. En la parte superior derecha, haga clic en **[!UICONTROL ...]**>**[!UICONTROL Manage Libraries]**.
1. Busque la biblioteca que desee eliminar.
1. Haga clic **[!UICONTROL ...]**y seleccione**[!UICONTROL Delete]**.

