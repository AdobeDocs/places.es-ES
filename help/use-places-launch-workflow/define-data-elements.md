---
title: Definición de elementos de datos
description: Esta sección proporciona información sobre cómo crear, utilizar y publicar elementos de datos en Experience Platform Launch para Places.
exl-id: 57e88a37-0b0b-4064-ab72-382a36a0d01d
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 1%

---

# Definición de un elemento de datos {#define-data-elements}

La siguiente información le ayuda a comprender los elementos de datos y cómo crearlos y publicarlos.

## Acerca de los elementos de datos

Los elementos de datos son los componentes básicos del diccionario de datos de la aplicación y se utilizan para recopilar, organizar y entregar datos a través de la tecnología de marketing y publicidad.

Un elemento de datos es una variable en la que el valor se puede asignar a un ID de visitante, un nombre de operador, un ID de publicidad, un ID push, etc. En Experience Platform Launch, puede hacer referencia a este valor por su nombre de variable. Esta colección de elementos de datos se convierte en el diccionario de los datos definidos que puede utilizar para crear reglas (eventos, condiciones y acciones). Este Experience Platform Launch se comparte en un entorno de, donde se puede utilizar con cualquier extensión de la propiedad.

Con la extensión Places, puede hacer referencia a valores de los siguientes destinos:

* Punto de interés actual, que hace referencia al punto de interés en el que se encuentra actualmente su cliente.

   Si el usuario se encuentra en varios puntos de interés, se selecciona el que pertenezca a la biblioteca con una clasificación más alta. Si varios puntos de interés pertenecen a la biblioteca de clasificación más alta, se selecciona la que tenga el radio más pequeño.
* Último punto de interés de salida, que hace referencia al punto de interés más reciente del que salió el usuario.
* Último punto de interés, que hace referencia al punto de interés más reciente introducido por el usuario.

Cada punto de interés contiene las siguientes referencias de datos:

* **[!UICONTROL Categoría]**: categoría del PDI
* **[!UICONTROL Ciudad]**: ciudad del PDI
* **[!UICONTROL País]**: país del PDI
* **[!UICONTROL Latitud]**: latitud del PDI
* **[!UICONTROL Longitud]**: longitud del PDI
* **[!UICONTROL Metadatos]**: metadatos personalizados del PDI
* **[!UICONTROL Nombre]**: nombre del PDI
* **[!UICONTROL Radio]**: radio del PDI
* **[!UICONTROL ID de región]**: ID del PDI
* **[!UICONTROL Región o estado]**: región, provincia o estado del PDI

### Crear un elemento de datos

1. En la página de propiedades de la aplicación, haga clic en **[!UICONTROL Elementos de datos]** pestaña.

1. Haga clic en **[!UICONTROL Crear nuevo elemento de datos]**.

1. En la lista de extensiones instaladas, busque **[!UICONTROL Places]**.

1. En el **[!UICONTROL Tipo de elemento de datos]** , seleccione una referencia de datos para este elemento de datos.

1. Seleccione un objetivo de PDI.

1. Si este elemento de datos es una referencia de metadatos personalizada, seleccione una clave de metadatos.

1. Escriba un nombre para el elemento de datos y haga clic en **[!UICONTROL Guardar]**.

   ![Crear elemento de datos](/help/assets/create-de-7-v3.png)


## Uso de un elemento de datos

Después de crear un elemento de datos, si hay un selector de elementos de datos, puede utilizar el elemento de datos de cualquier componente de regla.

![Uso del elemento de datos](/help/assets/use-de-v2.png)

Si un selector de elementos de datos no está presente en el componente de regla, puede utilizar el elemento de datos ajustando el nombre del elemento de datos con la variable **[!UICONTROL %%]** tokens.
Por ejemplo, si el nombre del elemento de datos es **[!UICONTROL Última ciudad del PDI]**, puede añadir **[!UICONTROL ÚLTIMA ciudad del PDI]** a una entrada de texto.


## Publicación de elementos de datos

Si los elementos de datos se utilizan en cualquiera de los componentes de regla, estos elementos de datos también deben incluirse en la biblioteca y publicarse.
