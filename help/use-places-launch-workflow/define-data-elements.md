---
title: Definición de elementos de datos
description: Esta sección proporciona información sobre cómo crear, utilizar y publicar elementos de datos en Experience Platform Launch para Places.
exl-id: 57e88a37-0b0b-4064-ab72-382a36a0d01d
TQID: https://experienceleague.adobe.com/NQ83uUZJtNglAcxD6HNl4Gw1Y8-0-uqfu-hH8H0EITg
product_v2: id: a829a185-511f-4bf8-8dcf-9e684f8011cfid: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: e43347a8-f2c5-4aa4-8623-6f13875d7e3aid: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2: id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2: id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0id: f9a2105e-7a47-4e85-9193-31a519a2cb83
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 486
ht-degree: 1%

---

# Definición de un elemento de datos {#define-data-elements}

La siguiente información le ayuda a comprender los elementos de datos y cómo crearlos y publicarlos.

## Acerca de los elementos de datos

Los elementos de datos son los componentes básicos del diccionario de datos de la aplicación y se utilizan para recopilar, organizar y entregar datos a través de la tecnología de marketing y publicidad.

Un elemento de datos es una variable en la que el valor se puede asignar a un ID de visitante, un nombre de operador, un ID de Advertising, un ID push, etc. En Experience Platform Launch, puede hacer referencia a este valor por su nombre de variable. Esta colección de elementos de datos se convierte en el diccionario de los datos definidos que puede utilizar para crear reglas (eventos, condiciones y acciones). Este diccionario se comparte en Experience Platform Launch, donde se puede utilizar con cualquier extensión de la propiedad.

Con la extensión Places, puede hacer referencia a valores de los siguientes destinos:

* Punto de interés actual, que hace referencia al punto de interés en el que se encuentra actualmente su cliente.

  Si el usuario se encuentra en varios puntos de interés, se selecciona el que pertenezca a la biblioteca con una clasificación más alta. Si varios puntos de interés pertenecen a la biblioteca de clasificación más alta, se selecciona la que tenga el radio más pequeño.
* Último punto de interés de salida, que hace referencia al punto de interés más reciente del que salió el usuario.
* Último punto de interés, que hace referencia al punto de interés más reciente introducido por el usuario.

Cada punto de interés contiene las siguientes referencias de datos:

* **[!UICONTROL Categoría]**: categoría del punto de interés
* **[!UICONTROL Ciudad]**: ciudad del PDI
* **[!UICONTROL País]**: país del PDI
* **[!UICONTROL Latitud]**: latitud del punto de interés
* **[!UICONTROL Longitud]**: longitud del punto de interés
* **[!UICONTROL Metadatos]**: metadatos personalizados del punto de interés
* **[!UICONTROL Nombre]**: nombre del POI
* **[!UICONTROL Radio]**: radio del punto de interés
* **[!UICONTROL ID de región]**: ID del punto de interés
* **[!UICONTROL Región/Estado]**: región, provincia o estado del punto de interés (POI)

### Crear un elemento de datos

1. En la página Propiedad de la aplicación, haga clic en la ficha **[!UICONTROL Elementos de datos]**.

1. Haga clic en **[!UICONTROL Crear nuevo elemento de datos]**.

1. En la lista de extensiones instaladas, busque **[!UICONTROL Places]**.

1. En la lista desplegable **[!UICONTROL Tipo de elemento de datos]**, seleccione una referencia de datos para este elemento de datos.

1. Seleccione un objetivo de PDI.

1. Si este elemento de datos es una referencia de metadatos personalizada, seleccione una clave de metadatos.

1. Escriba un nombre para el elemento de datos y haga clic en **[!UICONTROL Guardar]**.

   ![Crear elemento de datos](/help/assets/create-de-7-v3.png)


## Uso de un elemento de datos

Después de crear un elemento de datos, si hay un selector de elementos de datos, puede utilizar el elemento de datos de cualquier componente de regla.

![Usar el elemento de datos](/help/assets/use-de-v2.png)

Si un selector de elementos de datos no está presente en el componente de regla, puede utilizarlo ajustando el nombre del elemento de datos con los tokens **[!UICONTROL %%]**.
Por ejemplo, si el nombre del elemento de datos es **[!UICONTROL Última ciudad del punto de interés]**, puede agregar **[!UICONTROL ÚLTIMA ciudad del punto de interés]** a una entrada de texto.


## Publicación de elementos de datos

Si los elementos de datos se utilizan en cualquiera de los componentes de regla, estos elementos de datos también deben incluirse en la biblioteca y publicarse.
