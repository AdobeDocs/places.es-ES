---
title: Servicio de Places
description: El servicio de Places es un contexto importante para comprender la participación de los usuarios móviles. Con este contexto, los desarrolladores de aplicaciones móviles pueden mejorar el diseño de la aplicación y convertirlo en una experiencia más personalizada y atractiva.
exl-id: 7369176f-c072-437a-9ee3-b463c5ff1d12
source-git-commit: e78e3c5ee6623d6cdf2a33c0582667a70283fdc6
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 9%

---

# Servicio de Places {#home}

La ubicación es un contexto importante para comprender y relacionarse con los usuarios de dispositivos móviles. Con este contexto, los desarrolladores de aplicaciones móviles pueden mejorar el diseño de la aplicación y convertirlo en una experiencia más personalizada y atractiva.

El servicio Places, anteriormente conocido como servicio de ubicación de Adobe Experience Platform, es un servicio de localización geográfica que permite a las aplicaciones móviles que ofrecen reconocimiento de ubicación comprender el contexto de ubicación mediante el uso de interfaces de SDK enriquecidas y fáciles de usar, acompañadas de una base de datos flexible de puntos de interés (POI).

El servicio Places le permite lograr lo siguiente:

* Cree y administre una base de datos de puntos de interés que se puedan aprovechar con otras soluciones de Adobe Experience Cloud.
* Adjunte metadatos personalizados a los puntos de interés para que sean más completos y significativos especificando atributos adicionales.
* Visualice los puntos de interés en un mapa para comprender fácilmente el contexto espacial y añadir o editar atributos de metadatos.
* Configure el SDK en Adobe Experience Platform Launch para definir las reglas activadas por la ubicación y las condiciones basadas en metadatos.
* Reduzca el código que necesita escribir para supervisar la ubicación de un dispositivo y utilice la extensión Places para almacenar en déclencheur automáticamente las reglas específicas de la ubicación.

Esto le permitirá realizar acciones a partir de señales de ubicación en tiempo real, cuando y donde sea importante. El contexto adecuado ofrece una experiencia de participación móvil más enriquecedora.

A continuación se indican algunas formas de utilizar Places:

* Enviar una notificación en tiempo real cuando alguien entre en un punto de interés, *&quot;Oye..bienvenido al estadio.&quot;*
* Analice el tráfico de sus propias tiendas en comparación con las de su competencia.
* Segmente una audiencia en función del comportamiento sin conexión mediante perfiles de audiencia con contexto de ubicación.
* Segmente a un usuario con una experiencia en la tienda cuando sea relevante.

## Componentes del servicio Places

El servicio de Places consta de los siguientes componentes:

* **Servicio web**

  Puede crear y administrar puntos de interés mediante las API de REST de Places. Para obtener más información sobre las API de REST, consulte [Administrar bibliotecas](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) y [Administrar puntos de interés](/help/web-service-api/api-usage/manage-pois/manage-pois.md).

* **Interfaz de administración de POI**

  Visualice los puntos de interés en un mapa para comprender el contexto espacial y añadir o editar puntos de interés y sus metadatos personalizados.

* **Extensión Places**

  Interfaz de API móvil multiplataforma para integrar el contexto de ubicación en sus aplicaciones móviles. Para obtener más información sobre los SDK, consulte [Extensión Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

* **Reglas de lanzamiento**

  Reglas de Launch geo-inteligentes que permiten almacenar en déclencheur las acciones con eventos de entrada y salida. Las reglas también le permiten utilizar atributos geográficos en condiciones para personalizar la experiencia.

## Terminología

Estos son algunos términos comunes que se utilizan en esta documentación:

* Un **punto de interés (PDI)** es una ubicación geográfica de interés para su organización.

  Puede definir puntos de interés con atributos como nombre, radio, dirección, categoría y etiquetas de metadatos.

* Un **geoperímetro** es un tipo de punto de interés (POI).

  Este tipo de punto de interés es un límite geográfico virtual definido por las coordenadas de latitud y longitud.

* Una **señalización** es un tipo de punto de interés (POI).

  Este tipo de punto de interés es un dispositivo físico que representa una ubicación emitiendo una señal Bluetooth de baja potencia. La compatibilidad con señalizaciones estará disponible en una versión futura.

* Una **biblioteca** es una recopilación de puntos de interés, que se agrupan para adjuntar fácilmente reglas a un conjunto en lugar de un punto de interés.

* Una **extensión** es la extensión de Experience Platform Launch necesaria para integrar el SDK de Places en tus aplicaciones móviles.

  Extensión utilizada con otros SDK móviles para añadir contexto de ubicación a las experiencias.

* Una **organización** es la entidad de Adobe que identifica a su compañía en Adobe Experience Cloud.

  Normalmente, la organización es el nombre de la empresa. Sin embargo, una compañía puede tener más de una organización. El administrador de la organización puede configurar grupos y usuarios, así como la funcionalidad de inicio de sesión único.

* El **orgID** es el ID que representa a su organización en Adobe Experience Platform.

  Para obtener más información, consulte [Búsqueda del orgID](https://forums.adobe.com/thread/2339895).

* El servicio **ID de Experience Cloud** proporciona un identificador universal y persistente que identifica a los visitantes en todas las soluciones del Experience Cloud.

  Para obtener más información, consulte [Información general](https://experienceleague.adobe.com/docs/id-service/using/intro/overview.html?lang=es).

