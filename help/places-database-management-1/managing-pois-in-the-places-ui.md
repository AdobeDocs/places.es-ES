---
title: Administrar puntos de interés en la interfaz de usuario de lugares
seo-title: Administrar puntos de interés en la interfaz de usuario de lugares
description: Utilice la IU de lugares para administrar los puntos de interés.
seo-description: Utilice la IU de lugares para administrar los puntos de interés.
translation-type: tm+mt
source-git-commit: 01617e4e1658f92234803baf1e57282777d04b13

---


# Administrar puntos de interés en la interfaz de usuario de lugares

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

## Crear un POI {#create-a-poi}

Un punto de interés (POI) es una ubicación o un punto en un mapa que le interesa. Puede incluir ubicaciones como cafeterías, restaurantes, etc.

1. Inicie sesión en Adobe Places con su Adobe ID.
2. En la parte superior derecha, haga clic en el icono que parece una lista con viñetas y, a continuación, haga clic en **[!UICONTROL New]**.
3. Escriba un nombre para el punto de interés.
4. Seleccione o agregue una biblioteca.
5. Introduzca o seleccione un radio.

   a. Seleccione un icono para el punto de interés.
b.b. Seleccione un color para el icono.

6. Expanda la **[!UICONTROL Location]** sección.

   a. Escriba una dirección.

   b. Escriba la ciudad.

   c. Escriba el nombre del estado.

   d. Escriba el nombre del país.

   e. Seleccione o introduzca una latitud o longitud.

   f.Haga clic en **[!UICONTROL Drop Pin on Map]**.

7. Expanda la **[!UICONTROL Metadata]** sección y haga clic en **[!UICONTROL Add Metadata]**.

   a. Escriba el nombre de la clave.

   b. Escriba el valor clave.

8. Haga clic **[!UICONTROL Confirm]** y luego **[!UICONTROL  Save]**.

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

