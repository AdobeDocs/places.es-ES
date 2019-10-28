---
title: Definir elementos de datos
seo-title: Definir elementos de datos
description: Esta sección proporciona información sobre cómo crear, utilizar y publicar elementos de datos en Inicio de plataforma de experiencia para lugares.
seo-description: 'Esta sección proporciona información sobre cómo crear, utilizar y publicar elementos de datos en Inicio de plataforma de experiencia para lugares. '
translation-type: tm+mt
source-git-commit: 573f2bb368bd8384f5b465819600a1668b0bdda8

---


# Define a data element {#define-data-elements}

La siguiente información le ayuda a comprender los elementos de datos y cómo crearlos y publicarlos.

## Acerca de los elementos de datos

Los elementos de datos son los componentes básicos del diccionario de datos de la aplicación y se utilizan para recopilar, organizar y entregar datos en toda la tecnología de publicidad y mercadotecnia.

Un elemento de datos es una variable donde el valor se puede asignar a una ID de visitante, un nombre de portadora, una ID de publicidad, una ID push, etc. En Inicio de plataforma de experiencia, puede hacer referencia a este valor por su nombre de variable. Esta colección de elementos de datos se convierte en el diccionario de datos definidos que puede utilizar para crear reglas (eventos, condiciones y acciones) y este diccionario se comparte en Experience Platform Launch, donde se puede utilizar con cualquier extensión de su propiedad.

Con la extensión Places, puede hacer referencia a valores de los siguientes destinos:

* El punto de interés actual, que hace referencia al punto de interés en el que se encuentra su cliente.

   Si el usuario está ubicado en varios puntos de interés, se elige el que pertenece a la biblioteca con mayor clasificación. Si varios puntos de interés pertenecen a la biblioteca de clasificación más alta, se selecciona el que tenga el radio más pequeño.
* Último punto de interés de salida, que hace referencia al punto de interés más reciente que ha salido el usuario.
* Último punto de interés especificado, que hace referencia al punto de interés más reciente que ha introducido el usuario.

Cada punto de interés contiene las siguientes referencias de datos:

* **[!UICONTROL Category]**:: categoría del POI
* **[!UICONTROL City]**:: ciudad del POI
* **[!UICONTROL Country]**:: país del POI
* **[!UICONTROL Latitude]**:: latitud del POI
* **[!UICONTROL Longitude]**:: longitud del punto de interés
* **[!UICONTROL Metadata]**:: metadatos personalizados del punto de interés
* **[!UICONTROL Name]**:: región del POI
* **[!UICONTROL Radius]**:: radio del punto de interés
* **[!UICONTROL Region ID]**:: ID del POI
* **[!UICONTROL Region/State]**:: región, provincia o estado del POI

### Crear un elemento de datos

1. En la página Propiedad de la aplicación, haga clic en la **[!UICONTROL Data Elements]** ficha.

2. Haga clic en **[!UICONTROL Create New Data Element]**.

   ![Crear elemento de datos](/help/assets/create-de-2-v3.png)

3. En la lista de extensiones instaladas, busque **[!UICONTROL Places]**.

4. En la lista **[!UICONTROL Data Element Type]** desplegable, seleccione una referencia de datos para este elemento de datos.

5. Seleccione un objetivo de puntos de interés.

6. Si este elemento de datos es una referencia de metadatos personalizada, seleccione una clave de metadatos.

7. Escriba un nombre para el elemento de datos y haga clic en **[!UICONTROL Save]**.

   ![Crear elemento de datos](/help/assets/create-de-7-v3.png)


## Utilizar un elemento de datos

Después de crear un elemento de datos, si hay un selector de elementos de datos presente, puede utilizar el elemento de datos de cualquier componente de regla.

![Usar el elemento de datos](/help/assets/use-de-v2.png)

Si un selector de elementos de datos no está presente en el componente de regla, puede utilizar el elemento de datos ajustando el nombre del elemento de datos con los **[!UICONTROL %%]** tokens.
Por ejemplo, si el nombre del elemento de datos es **[!UICONTROL Last POI City]**, puede agregarlo **[!UICONTROL LAST POI City]** a una entrada de texto.


## Publicación de elementos de datos

Si se utilizan elementos de datos en cualquiera de los componentes de la regla, estos elementos de datos también deben incluirse en la biblioteca y publicarse.
