---
title: Administrar puntos de interés en la interfaz de usuario de lugares
seo-title: Administrar puntos de interés en la interfaz de usuario de lugares
description: Utilice la IU de lugares para administrar los puntos de interés.
seo-description: Utilice la IU de lugares para administrar los puntos de interés.
translation-type: tm+mt
source-git-commit: fdfeb8c17820c4eb0eae249da39be4eebece22d3

---


# Administrar puntos de interés existentes en la interfaz de usuario de lugares

Los puntos de interés y las bibliotecas se crean y administran en la base de datos de Lugares mediante la interfaz de usuario de Lugares.

## Definición de un punto de interés de geofence

Las geofences son un tipo de POI y se definen en la base de datos según las siguientes claves:

| Claves | Descripción | Requerido? |
| :--- | :--- | :--- |
| ID | Identificador único asignado a cada punto de interés | Sí |
| Nombre | Nombre práctico dado al punto de interés | Sí |
| Biblioteca | A cada punto de interés se le debe asignar una biblioteca para la organización | Sí |
| Icono | Asistencia con visualizaciones de los puntos de interés | Sí (valor predeterminado asignado) |
| Color | Asistencia con visualizaciones de los puntos de interés | Sí (valor predeterminado asignado) |
| Categoría | Asignar un marco común de categorías que son comunes a todos los puntos de interés de todas las bibliotecas | No |
| Dirección | Dirección | No |
| Ciudad | ciudad de POI | No |
| Estado/Región | estado o región del punto de interés | No |
| País | país del POI | No |
| Latitud | Coordenada Latitude para el centro del punto de interés | Sí |
| Longitud | Coordenada de longitud para el centro del punto de interés | Sí |
| Metadatos | pares de clave + valor personalizados que se pueden asignar a puntos de interés. Estos metadatos simplifican los futuros flujos de trabajo al permitirle agrupar puntos de interés entre bibliotecas para que cada uno utilice reglas y filtros en los flujos de trabajo descendentes, como enviar una notificación push siempre que alguien introduzca un punto de interés con tipo = competidor. | No |


## Editar un punto de interés

1. Inicie sesión en lugares con su Adobe ID.
1. Inicie sesión en el servicio Adobe Places con su Adobe ID.
1. En la parte superior derecha, haga clic en el icono que parece una lista con viñetas.
1. Busque el punto de interés que desea editar.
1. Haga clic **[!UICONTROL ...]** y seleccione **[!UICONTROL View Details]**.
1. Actualice la información y haga clic en **[!UICONTROL Save]**.

## Eliminar un punto de interés

1. Inicie sesión en lugares con su Adobe ID.
1. Inicie sesión en el servicio Adobe Places con su Adobe ID.
1. En la parte superior derecha, haga clic en el icono que parece una lista con viñetas.
1. Busque el punto de interés que desea eliminar.
1. Haga clic **[!UICONTROL ...]** y seleccione **[!UICONTROL Delete]**.

## Filtrar puntos de interés por ciudad, estado, país o metadatos

1. Inicie sesión en el servicio Adobe Places con su Adobe ID.
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
