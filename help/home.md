---
title: Servicio de Places
description: El servicio de Places es un contexto importante para comprender la participación de los usuarios móviles. Con este contexto, los desarrolladores de aplicaciones móviles pueden mejorar el diseño de la aplicación y convertirla en una experiencia más personalizada y atractiva.
exl-id: 7369176f-c072-437a-9ee3-b463c5ff1d12
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 10%

---

# Servicio de Places {#home}

La ubicación es un contexto importante para comprender y interactuar con los usuarios móviles. Con este contexto, los desarrolladores de aplicaciones móviles pueden mejorar el diseño de la aplicación y convertirla en una experiencia más personalizada y atractiva.

El servicio Places, anteriormente conocido como servicio de ubicación de Adobe Experience Platform, es un servicio de ubicación geográfica que permite a las aplicaciones móviles con conocimiento de ubicación comprender el contexto de ubicación mediante el uso de interfaces de SDK enriquecidas y fáciles de usar, acompañadas de una base de datos flexible de puntos de interés (POI).

El servicio de Places le permite lograr lo siguiente:

* Cree y administre una base de datos de puntos de interés que se pueda aprovechar con otras soluciones de Adobe Experience Cloud.
* Adjunte metadatos personalizados a los puntos de interés para hacerlos más ricos y significativos al especificar atributos adicionales.
* Visualice los puntos de interés en un mapa para comprender fácilmente el contexto espacial y añadir/editar atributos de metadatos.
* Configure el SDK en Adobe Experience Platform Launch para definir las reglas activadas por la ubicación y las condiciones basadas en metadatos.
* Reduzca el código que necesita escribir para monitorizar la ubicación de un dispositivo y utilice la extensión Places para almacenar en déclencheur automáticamente las reglas específicas de la ubicación.

Esto le permitirá realizar acciones desde las señales de ubicación en tiempo real, cuando y donde importe. El contexto adecuado ofrece una experiencia de participación móvil más enriquecedora.

Estas son algunas de las formas de usar Places:

* Enviar una notificación en tiempo real cuando alguien entre en un punto de interés, *&quot;Oye...bienvenidos al estadio&quot;.*
* Analice el tráfico de pie de sus propias tiendas en comparación con las de su competencia.
* Segmente una audiencia según el comportamiento sin conexión mediante perfiles de audiencia con contexto de ubicación.
* Si procede, establezca como objetivo a un usuario con una experiencia en la tienda.

## Componentes de Places Service

El servicio de Places consta de los siguientes componentes:

* **Servicio web**

   Puede crear y administrar puntos de interés mediante las API de REST de Places. Para obtener más información sobre las API de REST, consulte [Administrar bibliotecas](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) y [Administrar puntos de interés](/help/web-service-api/api-usage/manage-pois/manage-pois.md).

* **Interfaz de administración de puntos de interés**

   Visualice los puntos de interés en un mapa para comprender el contexto espacial y añadir/editar los puntos de interés y sus metadatos personalizados.

* **Extensión Places**

   La interfaz de API móvil multiplataforma para integrar el contexto de ubicación en sus aplicaciones móviles. Para obtener más información sobre los SDK, consulte [Extensión Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

* **Reglas de Launch**

   Reglas de Launch geointeligentes que permiten almacenar en déclencheur acciones con eventos de entrada y salida. Las reglas también permiten utilizar atributos geográficos en condiciones para personalizar la experiencia.

## Terminología

Estos son algunos términos comunes que se utilizan en esta documentación:

* A **punto de interés (POI)** es una ubicación geográfica que interesa a su organización.

   Puede definir puntos de interés con atributos como nombre, radio, dirección, categoría y etiquetas de metadatos.

* A **geovalencia** es un tipo de punto de interés.

   Este tipo de punto de interés es un límite geográfico virtual definido por coordenadas de latitud y longitud.

* A **señalización** es un tipo de punto de interés.

   Este tipo de punto de interés es un dispositivo físico que representa una ubicación mediante la emisión de una señal Bluetooth de baja potencia. La compatibilidad con Beacons estará disponible en una versión futura.

* Una **biblioteca** es una recopilación de puntos de interés, que se agrupan para adjuntar fácilmente reglas a un conjunto en lugar de un punto de interés.

* Un **Extensión** es la extensión de Experience Platform Launch necesaria para integrar el SDK de Places en sus aplicaciones móviles.

   Extensión utilizada con otros SDK para móviles para añadir contexto de ubicación a las experiencias.

* Una **organización** es la entidad de Adobe que identifica a su compañía en Adobe Experience Cloud.

   Normalmente, una organización es el nombre de su empresa. Sin embargo, una empresa puede tener más de una organización. El administrador de la organización puede configurar grupos y usuarios y la funcionalidad de inicio de sesión único.

* El **orgID** es el ID que representa a su organización en Adobe Experience Platform.

   Para obtener más información, consulte [Búsqueda del orgID](https://forums.adobe.com/thread/2339895).

* La variable **ID de Experience Cloud** ofrece un identificador universal y persistente que identifica a los visitantes en todas las soluciones del Experience Cloud.

   Para obtener más información, consulte [Información general](https://docs.adobe.com/content/help/es-ES/id-service/using/intro/overview.html).
