---
title: Servicio de Places
description: 'El servicio de lugares es un contexto importante para comprender la participación de los usuarios móviles. Con este contexto, los desarrolladores de aplicaciones móviles pueden mejorar el diseño de la aplicación y convertirla en una experiencia más personalizada y atractiva. '
translation-type: tm+mt
source-git-commit: 05b4d29aa7925f7a43e70c644e3cb88045cbe446
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 10%

---


# Servicio de Places {#home}

![&quot;Servicio de Places&quot;](/help/assets/places-service-header.png)

La ubicación es un contexto importante para comprender y relacionarse con los usuarios móviles. Con este contexto, los desarrolladores de aplicaciones móviles pueden mejorar el diseño de la aplicación y convertirla en una experiencia más personalizada y atractiva.

Places Service, anteriormente conocido como Adobe Experience Platform Location Service, es un servicio de ubicación geográfica que permite a las aplicaciones móviles con reconocimiento de ubicación comprender el contexto de ubicación mediante el uso de interfaces SDK enriquecidas y fáciles de usar, acompañadas de una base de datos flexible de puntos de interés (POI).

El servicio de lugares le permite lograr lo siguiente:

* Cree y administre una base de datos de puntos de interés que se pueda aprovechar con otras soluciones de Adobe Experience Cloud.
* Adjunte metadatos personalizados a los puntos de interés para hacerlos más ricos y significativos mediante la especificación de atributos adicionales.
* Visualice los puntos de interés en un mapa para comprender fácilmente el contexto espacial y añadir/editar atributos de metadatos.
* Configure el SDK en Adobe Experience Platform Launch para definir las reglas activadas por la ubicación y las condiciones basadas en metadatos.
* Reduzca el código que necesita escribir para supervisar la ubicación de un dispositivo y utilice la extensión Places para activar automáticamente las reglas específicas de la ubicación.

Esto le permitirá realizar acciones desde las señales de ubicación en tiempo real, cuándo y dónde es importante. El contexto adecuado ofrece una experiencia de compromiso móvil más enriquecedora.

Estas son algunas de las formas en que puede utilizar Lugares:

* Enviar una notificación en tiempo real cuando alguien entre en un POI, *&quot;Oye...bienvenidos al estadio&quot;.*
* Analice el tráfico de pies de sus propias tiendas en comparación con las tiendas de competidoras.
* Segmentar una audiencia según el comportamiento sin conexión mediante perfiles de audiencia con contexto de ubicación.
* Destinatario a un usuario con una experiencia en el almacén cuando sea pertinente.

## Componentes de Places Service

El servicio de lugares comprende los siguientes componentes:

* **Servicio Web**

   Puede crear y administrar puntos de interés mediante las API de Places REST. Para obtener más información sobre las API de REST, consulte [Administrar bibliotecas](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) y [Administrar puntos de interés](/help/web-service-api/api-usage/manage-pois/manage-pois.md).

* **Interfaz de administración de puntos de interés**

   Visualice los puntos de interés en un mapa para comprender el contexto espacial y añadir/editar los puntos de interés y sus metadatos personalizados.

* **Extensión Places**

   Interfaz de API móvil multiplataforma para integrar el contexto de ubicación en sus aplicaciones móviles. Para obtener más información sobre los SDK, consulte Extensión [](/help/places-ext-aep-sdks/places-extension/places-extension.md)Places.

* **Reglas de inicio**

   Reglas de inicio geointeligente que permiten activar acciones con eventos de entrada y salida. Las reglas también le permiten usar atributos geográficos en condiciones para personalizar la experiencia.

* **Extensión de monitor de lugares**

   El SDK móvil multiplataforma que se puede integrar en la aplicación móvil para supervisar automáticamente los cambios de ubicación del usuario y activar las reglas de lugares. Para obtener más información, consulte [Extensión](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)del monitor de lugares.

## Terminología

Estos son algunos términos comunes que se utilizan en esta documentación:

* Un **punto de interés (POI)** es una ubicación geográfica que interesa a su organización.

   Puede definir puntos de interés con atributos como nombre, radio, dirección, categoría y etiquetas de metadatos.

* Una **geofence** es un tipo de POI.

   Este tipo de punto de interés es un límite geográfico virtual definido por coordenadas de latitud y longitud.

* Una **señalización** es un tipo de punto de interés.

   Este tipo de POI es un dispositivo físico que representa una ubicación emitiendo una señal Bluetooth de baja potencia. La compatibilidad con las señalizaciones estará disponible en una versión futura.

* Una **biblioteca** es una recopilación de puntos de interés, que se agrupan para adjuntar fácilmente reglas a un conjunto en lugar de un punto de interés.

* Una **extensión** es la extensión de Experience Platform Launch necesaria para integrar el SDK de Places en sus aplicaciones móviles.

   Extensión utilizada con otros SDK móviles para añadir contexto de ubicación a sus experiencias.

* Una **organización** es la entidad de Adobe que identifica a su compañía en Adobe Experience Cloud.

   Normalmente, una organización es el nombre de su compañía. Sin embargo, una compañía puede tener más de una organización. El administrador de la organización puede configurar grupos y usuarios y la funcionalidad de inicio de sesión único.

* El **orgID** es el ID que representa a su organización en Adobe Experience Platform.

   Para obtener más información, consulte [Búsqueda de su orgID](https://forums.adobe.com/thread/2339895).

* The **Experience Cloud ID** service provides a universal, persistent ID that identifies your visitors across all the solutions in the Experience Cloud.

   Para obtener más información, consulte [Información general](https://docs.adobe.com/content/help/es-ES/id-service/using/intro/overview.html).
