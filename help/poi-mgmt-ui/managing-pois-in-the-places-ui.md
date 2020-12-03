---
title: Administrar puntos de interés existentes
description: En la interfaz de usuario del servicio de lugares, puede editar, eliminar o filtrar los puntos de interés existentes.
translation-type: tm+mt
source-git-commit: 5a21e734c0ef56c815389a9f08b445bedaae557a
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 6%

---


# Administrar puntos de interés existentes {#managing-existing-pois}

Los puntos de interés y las bibliotecas se crean y administran en la base de datos de Lugares mediante la interfaz de usuario de Lugares.

## Editar un punto de interés

1. Inicie sesión en Lugares con su Adobe ID.
1. Inicie sesión en el servicio de lugares con su Adobe ID.
1. En la parte superior derecha, haga clic en el icono que parece una lista con viñetas.
1. Busque el punto de interés que desea editar.
1. Click **[!UICONTROL ...]** and select **[!UICONTROL View Details]**.
1. Actualice la información y haga clic en **[!UICONTROL Save]**.

## Eliminar un punto de interés

1. Inicie sesión en Lugares con su Adobe ID.
1. Inicie sesión en el servicio de lugares con su Adobe ID.
1. En la parte superior derecha, haga clic en el icono que parece una lista con viñetas.
1. Busque el punto de interés que desea eliminar.
1. Click **[!UICONTROL ...]** and select **[!UICONTROL Delete]**.

## Filtrar puntos de interés por ciudad, estado, país o metadatos

![filtrar un punto de interés](/help/assets/filter_poi.png)

1. Inicie sesión en la interfaz de usuario del servicio de lugares con su Adobe ID.
1. En la parte superior derecha, haga clic en el icono de filtrado.
1. Puede filtrar los puntos de interés de una de las siguientes formas:

   * Por biblioteca:

      a. Seleccione una biblioteca.

   * Por propiedad:

      a. En la lista desplegable Propiedad, seleccione **[!UICONTROL Country]**, **[!UICONTROL State]** o **[!UICONTROL City]**.

      b. En la línea siguiente, introduzca un valor.

      Por ejemplo, puede seleccionar **[!UICONTROL State]** y escribir **[!UICONTROL California]**.

   * Con metadatos:

      a. Introduzca una clave y un valor.

## Definición de un punto de interés de geofence

Las geofences son un tipo de punto de interés y se definen en la base de datos según las siguientes claves:

| Teclas | Descripción | Requerido? |
| :--- | :--- | :--- |
| ID | Identificador único asignado a cada punto de interés | Sí |
| Nombre | Nombre práctico dado al punto de interés. | Sí |
| Biblioteca | A cada punto de interés se le debe asignar una biblioteca para la organización. | Sí |
| Radio | El radio de su POI en metros. | Sí |
| Icono | Ayudar con visualizaciones de los puntos de interés. | Sí (valor predeterminado asignado) |
| Color | Ayudar con visualizaciones de los puntos de interés. | Sí (valor predeterminado asignado) |
| Categoría | Asigne un marco común de categorías que sean comunes a todos los puntos de interés de todas las bibliotecas. | No |
| Dirección | Dirección. | No |
| Ciudad | Ciudad del POI. | No |
| Estado o región | Estado o región del punto de interés. | No |
| País | País del POI. | No |
| Latitud | Coordenada de latitud para el centro del punto de interés. | Sí |
| Longitud | Coordenada de longitud para el centro del punto de interés. | Sí |
| Metadatos | Par de clave y valor personalizados que se pueden asignar a puntos de interés. Estos metadatos simplifican los flujos de trabajo futuros al permitirle agrupar puntos de interés entre bibliotecas para que cada uno utilice reglas y filtros en flujos de trabajo descendentes, como enviar una notificación push cuando alguien introduce un punto de interés con el tipo = Competidora. | No |
