---
title: Notas de la versión
description: Notas de la versión de Places Service.
exl-id: 76da9548-4e32-4b23-9a15-7012973915f3
source-git-commit: 2b5c53887c9ed0f2a672c377121a39537ee58f01
workflow-type: tm+mt
source-wordcount: '1492'
ht-degree: 3%

---

# Notas de la versión {#release-notes}

## 8 de julio de 2020

* **Extensiones de supervisión de Places y Places**

   * Se han añadido extensiones de Monitor de lugares y lugares para [Aplicaciones nativas de React](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#react-native)
   * Se han añadido extensiones de Monitor de lugares y lugares para [Aplicaciones Cordova](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#cordova)
   * Para obtener más información, consulte: [Uso de la extensión Places](https://docs.adobe.com/content/help/es-ES/places/using/places-ext-aep-sdks/places-extension/places-extension.html)


## 12 de mayo de 2020

* **Servicio de Places**

   * Importación masiva de puntos de interés desde un archivo CSV con el botón &quot;Importar POI&quot;
   * Seleccione varios puntos de interés y edite o agregue valores de metadatos de forma masiva

## 6 de mayo de 2020

* **PlacesMonitor 2.2.1**

   * **Android**

      * Registro mejorado

## 5 de mayo de 2020


* **PlacesMonitor 2.1.3**

   * **iOS**

      * Registro mejorado

## 20 de febrero de 2020

* **ACPlaces 1.3.1 (iOS)**

   * La extensión Places ahora informa de la información de la versión al centro de eventos en el SDK principal.
   * La información de pertenencia al punto de interés del dispositivo ahora tiene un tiempo de vida predeterminado de una hora desde el momento en que se recopila. Para obtener más información, consulte [Modificación del tiempo de vida de la pertenencia a Places](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)


* **Places 1.4.1 (Android)**

   * La extensión Places ahora informa de la información de la versión al centro de eventos en el SDK principal.
   * La información de pertenencia al punto de interés del dispositivo ahora tiene un tiempo de vida predeterminado de una hora desde el momento en que se recopila. Para obtener más información, consulte [Modificación del tiempo de vida de la pertenencia a Places](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)

## 27 de enero de 2020

* **PlacesMonitor 2.2.0**

   * **Android**

      * Llame a la nueva API de Places para recopilar el estado de autorización de la ubicación cuando se inicia la aplicación y cuando cambia la autorización mientras se ejecuta la aplicación.
      * Se añadieron la API setRequestLocationPermission y la API setLocationPermission obsoleta.

## 9 de enero de 2020

* **Places 1.4.0**

   * **Android**

      * Se ha añadido una nueva API, `setAuthorizationStatus`, para establecer el estado de autorización del dispositivo para Servicios de Places. El valor se almacena y utiliza en el estado compartido de Places.

## 4 de diciembre de 2019

* **PlacesMonitor 2.1.2**

   * **iOS**

      * Llamar a la API de Places para recopilar CLAuthorizationStatus del dispositivo cuando cambia.

## 3 de diciembre de 2019

* **ACPPlaces 1.3.0**

   * **iOS**

      * Se ha añadido una nueva API, `setAuthorizationStatus`, para establecer el estado de autorización del dispositivo para Servicios de Places. El valor se almacena y utiliza en el estado compartido de Places.

## 25 de noviembre de 2019

* **PlacesMonitor 2.1.1**

   * **iOS**

      * Se corrigieron instrucciones de importación para proyectos de Cocoapods que utilizan la opción de varios proyectos de pod.

## 22 de noviembre de 2019

* **PlacesMonitor 2.1.1**

   * **Android**

      * El monitor reconoce ahora el inicio de un dispositivo Android y, si es necesario, vuelve a registrar las geovallas con el sistema operativo en función de la ubicación actual del dispositivo.
      * Se ha corregido una condición de carrera que a veces provocaba que se descartaran eventos de entrada y salida.

## 9 de octubre de 2019

* **PlacesMonitor 2.1.0**

   * **iOS**

      * Se ha añadido una nueva API, `setRequestAuthorizationLevel`, para establecer el tipo de solicitud de autorización de ubicación que se solicitará al usuario.
   * **Android**

      * Se ha añadido una nueva API, `setLocationPermission`, para establecer el tipo de solicitud de permiso de ubicación que se solicitará al usuario.
      * El Monitor de Places ahora es compatible con Android 10.



## 8 de agosto de 2019

En esta versión se realizaron las siguientes actualizaciones:

### Actualizaciones de IU

Esta es una lista de las actualizaciones de la interfaz de usuario de Places:

#### Nuevas características

* Se ha añadido una nueva vista de lista que muestra los puntos de interés sin el mapa.
* Se han añadido opciones de filtrado de puntos de interés para la ciudad, el estado, el país y los metadatos.
* La primera biblioteca de una organización se crea automáticamente.
* Se ha añadido la ordenación de POI a la vista de lista.

#### Actualizaciones de IU

* Se han movido la lista y el panel de detalles al lado derecho de la interfaz de usuario.
* Se ha añadido un nuevo panel de búsqueda en la parte superior de la interfaz de usuario.
* Si solo hay una biblioteca presente, esta se selecciona automáticamente al crear un punto de interés.
* Se ha movido la administración de bibliotecas a una ventana emergente.
* Se ha añadido un recuento de puntos de interés junto a los filtros.

## 6 de agosto de 2019

En esta versión se realizaron las siguientes actualizaciones:

### Monitorización de la extensión de Launch 2.0.0

* Se han actualizado las instrucciones de instalación de Android y iOS para Places Monitor 2.0.

## 31 de julio de 2019

En esta versión se realizaron las siguientes actualizaciones:

### Places Monitor 2.0.0

* El estado de monitorización ahora persiste entre inicios.
* La administración de la llamada de retorno, que resultó de una solicitud de permiso de ubicación, ya no requiere que amplíe PlacesActivity.
* Se ha cambiado una API existente, lo que permite a los desarrolladores borrar todos los datos de Places del dispositivo:

   API antigua: `public static void stop();`

   Nueva API: `public static void stop (final boolean clearData);`

* Se ha actualizado el uso del `getNearbyPointsOfInterest` API para gestionar los escenarios de error de forma más eficaz.

## 25 de julio de 2019

En esta versión se realizaron las siguientes actualizaciones:

### ACPPlacesMonitor 2.0.0

* Para borrar todos los datos de Places del dispositivo,

   en ACPlacesMonitor, reemplazó una API existente `+ (void) stop;` con`+ (void) stop: (BOOL) clearData;`.

* Se ha actualizado el uso de las API de Places `getNearbyPointsOfInterest` API para gestionar los escenarios de error de forma más eficaz.

## 22 de julio de 2019

En esta versión se realizaron las siguientes actualizaciones:

### Android Places 1.3.0

* Se ha añadido una nueva API que borra todos los datos relacionados con Places del estado compartido, la memoria en la aplicación y las preferencias compartidas.
* Se ha corregido un problema en el cual el estado compartido no se actualizaba durante el inicio de la aplicación.
* Se ha corregido un error por el que `getNearbyPointsOfInterest` la llamada de retorno devolvía el código de error `SERVER_RESPONSE_ERROR instead of CONNECTIVITY_ERROR` no hay internet.
* `getNearbyPointsOfInterest` API (sin errorCallback) tendrá el `successCallback` se llama con la lista de puntos de interés vacía en caso de error al recuperar los puntos de interés cercanos.

## 19 de julio de 2019

En esta versión se realizaron las siguientes actualizaciones:

**iOS Places 1.2.0**

Se ha añadido una nueva API que borra todos los datos relacionados con Places del estado compartido, la memoria en la aplicación y `NSUserDefaults`.

## 25 de junio de 2019

En esta versión se realizaron las siguientes actualizaciones:

**iOS Places Monitor 1.0.2**

* Mejoras en la calidad de vida, incluida una mejor documentación en el código y registro.

## 17 de junio de 2019

En esta versión se realizaron las siguientes actualizaciones:

**iOS Places 1.1.0**

* Se ha añadido una nueva API para devolver un código de error cuando hay un error en la recuperación de lugares cercanos.
* Cuando el estado de privacidad cambie a Opt-out, todos los datos relacionados con Places ahora se borrarán del dispositivo.
* Se ha corregido un problema que, después de un primer inicio, a veces provocaba que los eventos de Places se perdieran debido a condiciones de red incorrectas.
* Se ha corregido un problema en el cual, al procesar eventos de entrada de puntos de interés en sucesión rápida, el reemplazo de tokens mediante el motor de reglas a veces hacía referencia al punto de interés incorrecto.

## 30 de mayo de 2019

**Android Places Monitor 1.0.1**

* Se ha corregido un problema que impedía un evento de entrada para puntos de interés cuando se iniciaba la monitorización de Places.

## 28 de mayo de 2019

Se han corregido los siguientes problemas en la IU de Places:

* Se ha actualizado el conmutador de soluciones en Places para que se alinee con el resto del Experience Cloud.
* Se ha corregido un problema por el cual la clasificación se guardaba en instancias en las que no se realizaban cambios de clasificación.
* Se ha aumentado el radio mínimo permitido en la IU a 10 metros.
* Se ha corregido un problema en el cual, si se eliminaban todos los números del campo, el campo de radio se restablecía a 20 metros.

## 17 de mayo de 2019

En esta versión se realizaron las siguientes actualizaciones:

**Android Places 1.2.0**

* Se ha añadido una nueva API para procesar un geoperímetro individual.
* Se han corregido errores para evitar varios eventos de entrada consecutivos.

**Android Places Monitor 1.0.0**

Lanzamiento inicial del monitor Places para Android.

El Monitor de lugares administra las API de ubicación de nivel del sistema operativo y se comunica directamente con la extensión Places. Con ambas extensiones instaladas, los clientes pueden tener una monitorización de región predeterminada en su aplicación.
Para obtener más información sobre el Monitor de Places, haga clic aquí.


## 2 de mayo de 2019

**Android Places 1.1.0**

* Se ha introducido una nueva API para getNearByPlaces, que tiene un errorCallback y al que se llama con un errorCode que indica el motivo del error.
* La extensión Places ahora pone en cola los eventos hasta que se obtiene una configuración.
* Se ha agregado compatibilidad con configuraciones según el entorno.
* Corrección de errores : se corrigieron las claves de los eventos de entrada y salida de la región
* El almacenamiento de la última ubicación conocida ahora respeta correctamente el estado de privacidad del usuario


## 9 de abril de 2019

En esta versión se realizaron las siguientes actualizaciones:

**iOS Places Monitor 1.0.1**

* Se agregó la cobertura de prueba unitaria completa.
* Integración de CI (CircleCI)
* Integración de la cobertura de código (codecov)

## 25 de marzo de 2019

iOS Places Monitor 1.0.0

Versión inicial del Monitor de Places para iOS.

El Monitor de lugares administra las API de ubicación de nivel del sistema operativo y se comunica directamente con la extensión Places. Con ambas extensiones instaladas, los clientes pueden tener una monitorización de región predeterminada en su aplicación.

## 28 de febrero de 2019

### Lanzamiento beta

Esta es la primera versión de Places Service, un conjunto de herramientas que permite a los clientes enriquecer las experiencias de sus usuarios con datos de ubicación del mundo real. En la primera versión, nuestro caso de uso principal es permitir que las aplicaciones móviles recuperen datos de ubicación personalizados y actúen con esos datos a través de Adobe Experience Platform Launch.

### Funciones principales

Estas son las funciones clave de esta versión:

#### IU del servicio Places

Hemos lanzado una interfaz de usuario de administración donde puede ver y administrar sus puntos de interés (POI). También puede organizar los puntos de interés en bibliotecas. Además de los metadatos estándar, como ciudad, estado y categoría, también podemos añadir metadatos personalizados a sus puntos de interés.

* Para ver la IU de, vaya a [https://places.adobe.com](https://places.adobe.com).
* Para empezar con la interfaz de usuario de, consulte [Primeros pasos](/help/getting-started.md).

#### Extensión de Places

Con la extensión Places, puede añadir las bibliotecas del servicio Places a su aplicación móvil y actuar en sus puntos de interés. Con el generador de reglas en Experience Platform Launch, puede almacenar en déclencheur las acciones que se activan cuando los usuarios entran y salen de los puntos de interés.

En la extensión Places:

* Puede elegir qué bibliotecas de POI incluir en la aplicación.
* Eventos de regla que entran en déclencheur al entrar o salir del punto de interés.
* Cree elementos de datos que apunten al punto de interés actual del usuario.

Para obtener más información sobre la extensión Places, consulte [Extensión Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

#### API de Places

Puede utilizar las API de Places para lo siguiente:

* Permita que los desarrolladores rellenen y actualicen su lista de puntos de interés.
* Cree su propia interfaz de usuario o integre con una base de datos de puntos de interés existente.
* Utilice los extremos del lote de la API de Places para realizar una importación masiva de puntos de interés.

   Puede utilizar la utilidad Python que se proporciona para completar la importación masiva.

Para obtener más información sobre las API de Places, consulte [API de servicio web](/help/web-service-api/places-web-services.md).

### Próximamente

#### Analytics  de CRM

La extensión de Analytics se está actualizando para agregar automáticamente datos de contexto de ubicación de la base de datos del servicio Places a todas las llamadas de Analytics salientes cuando un usuario está en un punto de interés (llamadas pasivas). Esta actualización también permite crear reglas para activar llamadas de seguimiento de Analytics directamente a la entrada o salida de puntos de interés (llamadas activas).
