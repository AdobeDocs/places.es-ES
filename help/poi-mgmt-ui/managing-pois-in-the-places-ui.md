---
title: Administrar POI existentes
description: En la interfaz de usuario del servicio de Places, puede editar, eliminar o filtrar los puntos de interés existentes.
exl-id: a4cf28ae-1e3c-4724-bca3-ac1d0cd6da09
TQID: https://experienceleague.adobe.com/2VnBQ5-flpx5cyeK3n5b3AOKqnt7RVkdqFBXYa9O5Ys
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: dc5cf79d-43c4-4731-bffa-1df5d7549cb1id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2: id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2: id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 408
ht-degree: 6%

---

# Administrar POI existentes {#managing-existing-pois}

Los puntos de interés y las bibliotecas se crean y administran en la base de datos de Places mediante la interfaz de usuario de Places.

## Editar un POI

1. Inicie sesión en Places con su Adobe ID.
1. Inicie sesión en el servicio de Places con su Adobe ID.
1. En la parte superior derecha, haga clic en el icono que parece una lista con viñetas.
1. Busque el punto de interés que desee editar.
1. Haga clic en **[!UICONTROL ...]** y seleccione **[!UICONTROL Ver detalles]**.
1. Actualice la información y haga clic en **[!UICONTROL Guardar]**.

## Eliminar un POI

1. Inicie sesión en Places con su Adobe ID.
1. Inicie sesión en el servicio de Places con su Adobe ID.
1. En la parte superior derecha, haga clic en el icono que parece una lista con viñetas.
1. Busque el punto de interés que desee eliminar.
1. Haga clic en **[!UICONTROL ...]** y seleccione **[!UICONTROL Eliminar]**.

## Filtrar puntos de interés por ciudad, estado, país o metadatos

![filtrar un punto de interés](/help/assets/filter_poi.png)

1. Inicie sesión en la interfaz de usuario del servicio de Places con su Adobe ID.
1. En la parte superior derecha, haga clic en el icono de filtrado.
1. Puede filtrar los puntos de interés de una de las siguientes maneras:

   * Por biblioteca:

     a. Seleccione una biblioteca.

   * Por propiedad:

     a. En la lista desplegable Propiedad, seleccione **[!UICONTROL País]**, **[!UICONTROL Estado]** o **[!UICONTROL Ciudad]**.

     b. En la línea siguiente, introduzca un valor.

     Por ejemplo, puede seleccionar **[!UICONTROL Estado]** y escribir **[!UICONTROL California]**.

   * Con metadatos:

     a. Introduzca una clave y un valor.

## Definición de un punto de interés geográfico

Las geovallas son un tipo de punto de interés y se definen en la base de datos en función de las siguientes claves:

| Claves | Descripción | ¿Requerido? |
| :--- | :--- | :--- |
| ID | Identificador único asignado a cada POI | Sí |
| Nombre | Nombre descriptivo proporcionado al PDI. | Sí |
| Biblioteca | A cada punto de interés se le debe asignar una biblioteca para la organización. | Sí |
| Radio | El radio del punto de interés en metros. | Sí |
| Icono | Ayude con las visualizaciones de los puntos de interés. | Sí (asignado de forma predeterminada) |
| Color | Ayude con las visualizaciones de los puntos de interés. | Sí (asignado de forma predeterminada) |
| Categoría | Asigne un marco común de categorías que sean comunes en todos los puntos de interés de todas las bibliotecas. | No |
| Dirección | Dirección de la calle. | No |
| Ciudad | Ciudad del PDI. | No |
| Estado/Región | Estado o región del PDI. | No |
| País | País del PDI. | No |
| Latitud | Coordenada de latitud para el centro del punto de interés. | Sí |
| Longitud | Coordenada de longitud para el centro del PDI. | Sí |
| Metadatos | Pares de clave y valor personalizados que se pueden asignar a puntos de interés. Estos metadatos optimizan los flujos de trabajo futuros al permitirle agrupar los puntos de interés en varias bibliotecas para que cada uno utilice reglas y filtros en flujos de trabajo descendentes, como enviar una notificación push cuando alguien introduce un punto de interés con el tipo = competidor. | No |
