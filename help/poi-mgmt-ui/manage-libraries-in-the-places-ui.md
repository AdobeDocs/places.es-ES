---
title: Administrar bibliotecas en la IU del servicio Places
description: Administre sus bibliotecas mediante la interfaz de usuario del servicio de Places.
exl-id: 2fb999b4-854a-430f-bb89-4c786d1a89cc
TQID: https://experienceleague.adobe.com/PP7P3aOL3EKSEPJWedHtfyHRzbCueMtNS-J7Ao4mawo
product_v2:
  - id: cb954087-f4fc-4456-afb9-e939cabcdc79
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: dc5cf79d-43c4-4731-bffa-1df5d7549cb1
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 434
ht-degree: 14%

---

# Administrar bibliotecas {#manage-libraries-places-ui}

Una biblioteca es una colección de puntos de interés. Puede tener hasta 150 000 puntos de interés en una biblioteca y puede haber hasta 100 bibliotecas por organización de Experience Cloud.

Existen varias formas de organizar los puntos de interés en bibliotecas, según lo que resulte más útil para su organización. Es posible que algunos clientes prefieran crear una biblioteca independiente para cada aplicación móvil, mientras que otros clientes podrían utilizar bibliotecas para agrupar tipos específicos de puntos de interés, como cafeterías, parques, hoteles, etc. Por ejemplo, una gran empresa de entretenimiento puede tener una biblioteca que incluya sus recintos al aire libre en una biblioteca y sus tiendas minoristas en otra biblioteca. Un gobierno de la ciudad podría tener una biblioteca que abarque todos los edificios de la ciudad y otra biblioteca que abarque todos los parques de la ciudad.

Las bibliotecas se definen de la siguiente manera:

| Claves: | Descripción: |
| :--- | :--- |
| ID | un identificador único asignado a la biblioteca en el momento de la creación |
| Nombre | un nombre descriptivo para una biblioteca |
| Clasificación | Estas clasificaciones se pueden ignorar si no hay geovallas superpuestas en su organización. Si hay puntos de interés superpuestos, le recomendamos que coloque cada una de las geovallas en bibliotecas independientes para que se puedan ponderar entre sí. Un usuario solo puede estar en una sola geovalla a la vez. <br><br>La clasificación más alta de las geovallas en las que se encuentra un usuario determina su pertenencia a la geovalla actual. Si hay geovallas que tienen la misma clasificación de biblioteca, la geovalla más pequeña es la actual del usuario. <br><br>SDK también tiene conocimiento de los puntos de interés *Última entrada* y *Última salida*, por lo que tiene control total sobre cómo desea que se activen las reglas en función de la interacción del usuario con los puntos de interés. |

## Crear una biblioteca.

1. Inicie sesión en Places con su Adobe ID.
1. En el lado superior derecho, haga clic en **[!UICONTROL ...]** > **[!UICONTROL Administrar bibliotecas]**.
1. Haga clic en **[!UICONTROL Nuevo]**.
1. Escriba el nombre.
1. Haga clic en **[!UICONTROL Confirmar]**.

## Cambio de la clasificación de una biblioteca en la IU de Places

1. Inicie sesión en Places con su Adobe ID.
1. En el lado superior derecho, haga clic en **[!UICONTROL ...]** > **[!UICONTROL Administrar bibliotecas]**.
1. Haga clic en el icono a la izquierda del nombre de la biblioteca y arrastre la biblioteca a la nueva clasificación.

## Cambiar el nombre de una biblioteca

1. Inicie sesión en Places con su Adobe ID.
1. En el lado superior derecho, haga clic en **[!UICONTROL ...]** > **[!UICONTROL Administrar bibliotecas]**.
1. Busque la biblioteca que desee eliminar.
1. Haga clic en **[!UICONTROL ...]** y seleccione **[!UICONTROL Cambiar nombre]**.
1. Actualice el nombre y haga clic en **[!UICONTROL Guardar]**.

## Eliminar una biblioteca

1. Inicie sesión en Places con su Adobe ID.
1. En el lado superior derecho, haga clic en **[!UICONTROL ...]** > **[!UICONTROL Administrar bibliotecas]**.
1. Busque la biblioteca que desee eliminar.
1. Haga clic en **[!UICONTROL ...]** y seleccione **[!UICONTROL Eliminar]**.
