---
title: Servicio de ubicación de Adobe Experience Platform
seo-title: Servicio de ubicación de Adobe Experience Platform
description: 'El servicio de ubicación es un contexto importante para comprender la participación de los usuarios móviles. Con este contexto, los desarrolladores de aplicaciones móviles pueden mejorar el diseño de la aplicación y convertirla en una experiencia más personalizada y atractiva. '
seo-description: 'El servicio de ubicación es un contexto importante para comprender la participación de los usuarios móviles. Con este contexto, los desarrolladores de aplicaciones móviles pueden mejorar el diseño de la aplicación y convertirla en una experiencia más personalizada y atractiva. '
translation-type: tm+mt
source-git-commit: 85ce31329ad155e5c835be286c18e6609b88167b

---


# Información general {#home}

El servicio de ubicación de Adobe Experience Platform (servicio de ubicación) es un contexto importante para comprender la participación de los usuarios móviles. Con este contexto, los desarrolladores de aplicaciones móviles pueden mejorar el diseño de la aplicación y convertirla en una experiencia más personalizada y atractiva. Places es un servicio de geolocalización que permite a los desarrolladores de aplicaciones móviles comprender el contexto de la ubicación mediante el uso de interfaces de SDK enriquecidas y fáciles de usar, acompañadas de una base de datos flexible de puntos de interés (POI).

El servicio de ubicación le permite lograr lo siguiente:

* Cree y administre una base de datos de puntos de interés que se puede aprovechar con otras soluciones de Adobe Experience Cloud.
* Adjunte metadatos personalizados a los puntos de interés para hacerlos más ricos y significativos mediante la especificación de atributos adicionales.
* Visualice los puntos de interés en un mapa para comprender fácilmente el contexto espacial y añadir/editar atributos de metadatos.
* Configure el SDK en Adobe Experience Platform Launch para definir las reglas activadas por la ubicación y las condiciones basadas en metadatos.
* Reduzca el código que necesita escribir en la ubicación de un dispositivo de supervisión y utilice el monitor de ubicación de Adobe para activar automáticamente las reglas específicas de la ubicación.

Esto le permitirá realizar acciones desde las señales de ubicación en tiempo real, cuándo y dónde es importante. El contexto adecuado ofrece una experiencia de compromiso móvil más enriquecedora.

Estas son algunas de las formas en que puede utilizar Lugares:

* Enviar una notificación en tiempo real cuando alguien entre en un POI, *"Oye...bienvenidos al estadio".*
* Analizar el tráfico de pies de sus propias tiendas en comparación con las de su competidor.
* Segmente una audiencia según su comportamiento sin conexión mediante perfiles de audiencia con contexto de ubicación.
* Diríjase a un usuario con una experiencia en la tienda cuando sea pertinente.

## Adición de un marcador de posición para el vídeo "Introducción al servicio de ubicación" de Brandon

## Casos de uso del servicio de ubicación

Mejore esta sección con

## Componentes del servicio de ubicación

El servicio de ubicación comprende los siguientes componentes:

* **Servicio Web de lugares**

   Puede crear y administrar puntos de interés mediante las API de Places REST. Para obtener más información sobre las API de REST, consulte [Administrar bibliotecas](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) y [Administrar puntos de interés](/help/web-service-api/api-usage/manage-pois/manage-pois.md).

* **Interfaz de usuario del servicio de ubicación**

   Visualice los puntos de interés en un mapa para comprender el contexto espacial y añadir/editar los puntos de interés y sus metadatos personalizados.

* **SDK de lugares**

   Interfaz de API móvil multiplataforma para integrar el contexto de ubicación en sus aplicaciones móviles. Para obtener más información sobre los SDK, consulte Extensión [](/help/places-ext-aep-sdks/places-extension/places-extension.md)Places.

* **Coloca las reglas**

   Reglas de inicio geointeligente que permiten activar acciones con eventos de entrada y salida. Las reglas también le permiten usar atributos geográficos en condiciones para personalizar la experiencia.

* **Monitor de lugares**

   El SDK móvil multiplataforma que se puede integrar en la aplicación móvil para supervisar automáticamente los cambios de ubicación del usuario y activar las reglas de lugares. Para obtener más información, consulte [Extensión](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)del monitor de lugares.

## Terminología

Estos son algunos términos comunes que se utilizan en esta documentación:

* Un **punto de interés (POI)** es una ubicación geográfica que interesa a su organización.

   Puede definir puntos de interés con atributos como nombre, radio, dirección, categoría y etiquetas de metadatos.

* Una **geofence** es un tipo de POI.

   Este tipo de punto de interés es un límite geográfico virtual definido por coordenadas de latitud y longitud.

* Una **señalización** es un tipo de punto de interés.

   Este tipo de POI es un dispositivo físico que representa una ubicación emitiendo una señal Bluetooth de baja potencia. La compatibilidad con las señalizaciones estará disponible en una versión futura.

* Una **biblioteca** es una colección de puntos de interés, que se agrupan para adjuntar fácilmente reglas a un conjunto en lugar de un punto de interés.

* Una **extensión** SDK es la extensión Inicio de plataforma de experiencia necesaria para integrar el SDK de lugares en las aplicaciones móviles.

   Extensión utilizada con otros SDK móviles para añadir contexto de ubicación a sus experiencias.

* Una **organización** es la entidad de Adobe que identifica a su empresa en Adobe Experience Cloud.

   Normalmente, una organización es el nombre de su empresa. Sin embargo, una empresa puede tener más de una organización. El administrador de la organización puede configurar grupos y usuarios y la funcionalidad de inicio de sesión único.

* El **orgID** es el ID que representa a su organización en la plataforma de Adobe Experience.

   Para obtener más información, consulte [Búsqueda de su orgID](https://forums.adobe.com/thread/2339895).

* The **Experience Cloud ID** service provides a universal, persistent ID that identifies your visitors across all the solutions in the Experience Cloud.

   For more information, see [Overview](https://docs.adobe.com/content/help/en/id-service/using/intro/overview.html).