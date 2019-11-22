---
title: Notas de la versión
seo-title: Notas de la versión
description: Notas de la versión del servicio de ubicación de Adobe Experience Platform.
seo-description: Notas de la versión del servicio de ubicación de Adobe Experience Platform.
translation-type: tm+mt
source-git-commit: 7fd44ab0135ec77f4b235cc65b943b40d535717c

---


# Notas de la versión {#release-notes}

## 22 de noviembre de 2019

* **PlacesMonitor 2.1.1**

   * **Android**

      * El monitor ahora reconoce el inicio de un dispositivo Android y, si es necesario, vuelve a registrar las geofences con el sistema operativo en función de la ubicación actual del dispositivo.
      * Se corrigió una condición de carrera que en ocasiones causaba que se descartaran los eventos de entrada y salida.

## 9 de octubre de 2019

* **PlacesMonitor 2.1.0**

   * **iOS**

      * Se ha agregado una nueva API `setRequestAuthorizationLevel`, para establecer el tipo de solicitud de autorización de ubicación para la que se solicitará al usuario.
   * **Android**

      * Se ha agregado una nueva API `setLocationPermission`, para establecer el tipo de solicitud de permiso de ubicación para la que se solicitará al usuario.
      * El monitor de lugares ahora es compatible con Android 10.



## 8 de agosto de 2019

En esta versión se realizaron las siguientes actualizaciones:

### Actualizaciones de la interfaz de usuario

Esta es una lista de las actualizaciones de la interfaz de usuario de Lugares:

#### Nuevas características

* Se ha agregado una nueva vista de lista que muestra los puntos de interés sin el mapa.
* Se agregaron opciones de filtrado de puntos de interés para la ciudad, el estado, el país y los metadatos.
* La primera biblioteca de una organización se crea automáticamente.
* Se ha añadido la ordenación de puntos de interés a la vista de lista.

#### Actualizaciones de la interfaz de usuario

* Se ha movido el panel de lista y detalles al lado derecho de la interfaz de usuario.
* Se ha agregado un nuevo panel de búsqueda en la parte superior de la interfaz de usuario.
* Si solo hay una biblioteca presente, esta biblioteca se selecciona automáticamente al crear un punto de interés.
* Se ha movido la administración de biblioteca a una ventana emergente.
* Se ha agregado un recuento de puntos de interés junto a los filtros.

## 6 de agosto de 2019

En esta versión se realizaron las siguientes actualizaciones:

### Monitor Launch Extension 2.0.0

* Se han actualizado las instrucciones de instalación de Android e iOS para Places Monitor 2.0.

## 31 de julio de 2019

En esta versión se realizaron las siguientes actualizaciones:

### Monitor de lugares 2.0.0

* El estado de supervisión ahora persiste entre inicios.
* La gestión de la llamada de retorno, que se deriva de una solicitud de permiso de ubicación, ya no requiere que extienda PlacesActivity.
* Se ha cambiado una API existente, lo que permite a los desarrolladores borrar todos los datos de Places del dispositivo:

   API antigua: `public static void stop();`

   Nueva API: `public static void stop (final boolean clearData);`

* Se ha actualizado el uso de la `getNearbyPointsOfInterest` API para gestionar los escenarios de error de forma más eficaz.

## jueves, 25 de julio de 2019

En esta versión se realizaron las siguientes actualizaciones:

### ACPPlacesMonitor 2.0.0

* Para borrar todos los datos de lugares del dispositivo,

   en ACPPlacesMonitor, se reemplazó una API existente `+ (void) stop;` con`+ (void) stop: (BOOL) clearData;`.

* Se ha actualizado el uso de la API de ACPPlaces `getNearbyPointsOfInterest` para gestionar los escenarios de error de forma más eficaz.

## jueves, 22 de julio de 2019

En esta versión se realizaron las siguientes actualizaciones:

### Android Places 1.3.0

* Se ha agregado una nueva API que borra todos los datos relacionados con Lugares del estado compartido, la memoria en la aplicación y la preferencia compartida.
* Se corrigió un problema en el cual el estado compartido no se actualizaba durante el inicio de la aplicación.
* Se corrigió un error en el que `getNearbyPointsOfInterest` la llamada de retorno devolvía código de error `SERVER_RESPONSE_ERROR instead of CONNECTIVITY_ERROR` en Internet.
* `getNearbyPointsOfInterest` La API (sin errorCallback) tendrá la `successCallback` llamada con una lista poi vacía, en caso de error al recuperar los puntos de interés cercanos.

## jueves, 19 de julio de 2019

En esta versión se realizaron las siguientes actualizaciones:

**iOS Places 1.2.0**

Se ha agregado una nueva API que borra todos los datos relacionados con Lugares del estado compartido, la memoria en la aplicación y `NSUserDefaults`.

## 25 de junio de 2019

En esta versión se realizaron las siguientes actualizaciones:

**iOS Places Monitor 1.0.2**

* Mejoras en la calidad de vida, incluida una mejor documentación y registro en el código.

## 17 de junio de 2019

En esta versión se realizaron las siguientes actualizaciones:

**iOS Places 1.1.0**

* Se ha agregado una nueva API para devolver un código de error cuando se produce un error al recuperar lugares cercanos.
* Cuando el estado de privacidad cambia a opt-out, todos los datos relacionados con Places se borrarán del dispositivo.
* Se ha corregido un problema que, después de un primer inicio, a veces provocaba que los eventos de Lugares se perdieran debido a las malas condiciones de la red.
* Se corrigió un problema en el cual, al procesar eventos de entrada de puntos de interés en una sucesión rápida, el reemplazo de tokens mediante el motor de reglas a veces hacía referencia al punto de interés incorrecto.

## 30 de mayo de 2019 (Lugares)

**Monitor de lugares de Android 1.0.1**

* Se ha corregido un problema que impedía un evento de entrada para puntos de interés cuando se iniciaba la supervisión de lugares.

## 28 de mayo de 2019

Se han corregido los siguientes problemas en la interfaz de usuario de Lugares:

* Se ha actualizado el conmutador de soluciones en lugares para que se alinee con el resto de Experience Cloud.
* Se corrigió un problema en el cual la clasificación se guardaba en instancias en las que no se realizaban cambios de clasificación.
* Se ha aumentado el radio mínimo permitido en la interfaz de usuario a 10 metros.
* Se corrigió un problema en el cual, si se eliminan todos los números del campo, el campo de radio se restablecía a 20 metros.

## 17 de mayo de 2019 (Lugares)

En esta versión se realizaron las siguientes actualizaciones:

**Android Places 1.1.0**

* Se ha añadido una nueva API para procesar una Geofence individual.
* Corrección de errores para evitar varios eventos de entrada consecutivos.

**Monitor de lugares de Android 1.0.0**

Versión inicial del Monitor de lugares para Android.

El monitor de lugares administra las API de ubicación de nivel de SO y se comunica directamente con la extensión Lugares. Con ambas extensiones instaladas, los clientes pueden tener una supervisión de región lista para usar en su aplicación.
Para obtener más información sobre el Monitor de lugares, haga clic aquí.


## 2 de mayo de 2019

**Android Places 1.1.0**

* Se ha introducido una nueva API para getNearByPlaces, que tiene un errorCallback y se llama con un errorCode que indica el motivo del error.
* La extensión Places ahora coloca los eventos en la cola hasta que se obtiene una configuración.
* Se agregó compatibilidad con configuraciones compatibles con el entorno.
* Corrección de errores: se corrigieron las claves de los eventos de entrada y salida de región
* El almacenamiento de la última ubicación conocida ahora respeta correctamente el estado de privacidad del usuario


## 9 de abril de 2019

En esta versión se realizaron las siguientes actualizaciones:

**iOS Places Monitor 1.0.1**

* Se ha añadido una cobertura de prueba unitaria completa.
* Integración de CI (CircleCI)
* Integración de cobertura de código (código)

## 25 de marzo de 2019

iOS Places Monitor 1.0.0

Versión inicial del monitor de lugares para iOS.

El monitor de lugares administra las API de ubicación de nivel de SO y se comunica directamente con la extensión Lugares. Con ambas extensiones instaladas, los clientes pueden tener una supervisión de región lista para usar en su aplicación. Para obtener más información sobre el Monitor de lugares, consulte Extensión [Monitor de](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)lugares.

## 28 de febrero de 2019

### Versión beta

Esta es la primera versión de Places, un conjunto de herramientas que permite a los clientes enriquecer las experiencias de sus usuarios con datos de ubicación en el mundo real. Para la primera versión, nuestro caso de uso principal es permitir que las aplicaciones móviles recuperen datos de ubicación personalizados y actúen en función de esos datos a través de Adobe Experience Platform Launch.

### Funciones principales

Estas son las funciones clave de esta versión:

#### Interfaz de usuario del servicio de ubicación

Hemos lanzado una interfaz de usuario de administración en la que puede ver y administrar sus puntos de interés (POI). También puede organizar sus puntos de interés en bibliotecas. Además de los metadatos estándar como ciudad, estado y categoría, también se admite la capacidad de agregar metadatos personalizados a los puntos de interés.

* Para ver la interfaz de usuario, vaya a [https://places.adobe.com](https://places.adobe.com).
* Para empezar a usar la interfaz de usuario, consulte [Introducción](/help/getting-started.md).

#### Extensión de lugares

Con la extensión de lugares, puede añadir las bibliotecas de lugares a su aplicación móvil y actuar en función de sus puntos de interés. Con el generador de reglas en Inicio de plataforma de experiencia, puede activar acciones para que se activen cuando los usuarios entren y salgan de puntos de interés.

En la extensión Places:

* Puede elegir qué bibliotecas de puntos de interés incluir en la aplicación.
* Eventos de regla que se activan al entrar o salir del punto de interés.
* Cree elementos de datos que apunten al punto de interés actual del usuario.

For more information about the Places extension, see [Places extension](/help/places-ext-aep-sdks/places-extension/places-extension.md).

#### API de lugares

Puede utilizar las API de Places para lo siguiente:

* Permita que los desarrolladores rellenen y actualicen su lista de puntos de interés.
* Cree su propia interfaz de usuario o integre una base de datos de puntos de interés existente.
* Utilice los extremos de lote de la API de lugares para realizar una importación masiva de puntos de interés.

   Las API proporcionan una utilidad python.

Para obtener más información sobre las API de lugares, consulte API [de servicio](/help/web-service-api/places-web-services.md)web.

### Muy pronto

#### Analytics  de CRM

La extensión de Analytics se está actualizando para agregar automáticamente datos de contexto de ubicación de la base de datos de lugares a todas las llamadas salientes de Analytics cuando un usuario se encuentra dentro de un punto de interés (llamadas pasivas). Esta actualización también permitirá que la creación de reglas active las llamadas de seguimiento de Analytics directamente en la entrada o salida del punto de interés (llamadas activas).

