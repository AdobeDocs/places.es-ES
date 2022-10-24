---
title: Notas de la versión
description: Notas de la versión del servicio Places.
exl-id: 76da9548-4e32-4b23-9a15-7012973915f3
source-git-commit: 2b5c53887c9ed0f2a672c377121a39537ee58f01
workflow-type: tm+mt
source-wordcount: '1492'
ht-degree: 3%

---

# Notas de la versión {#release-notes}

## 8 de julio de 2020

* **Extensiones de monitor de Places y Places**

   * Se han agregado extensiones de seguimiento de Places y Places para [React Aplicaciones nativas](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#react-native)
   * Se han agregado extensiones de seguimiento de Places y Places para [Aplicaciones de Cordova](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#cordova)
   * Para obtener más información, consulte: [Uso de la extensión Places](https://docs.adobe.com/content/help/es-ES/places/using/places-ext-aep-sdks/places-extension/places-extension.html)


## 12 de mayo de 2020

* **Servicio de Places**

   * Importación masiva de puntos de interés desde un archivo CSV mediante el botón &quot;Importar puntos de interés&quot;
   * Seleccionar varios puntos de interés y editar o añadir valores de metadatos de forma masiva

## 6 de mayo de 2020

* **PlacesMonitor 2.2.1**

   * **Android**

      * Registro mejorado

## 5 de mayo de 2020


* **PlacesMonitor 2.1.3**

   * **iOS**

      * Registro mejorado

## 20 de febrero de 2020

* **ACPPlaces 1.3.1 (iOS)**

   * La extensión Places ahora informa de la información de la versión al centro de eventos en el SDK principal.
   * La información de pertenencia al punto de interés del dispositivo ahora tiene un tiempo de vida predeterminado de una hora desde el momento en que se recopila. Para obtener más información, consulte [Modificación del tiempo de permanencia de Places](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)


* **Places 1.4.1 (Android)**

   * La extensión Places ahora informa de la información de la versión al centro de eventos en el SDK principal.
   * La información de pertenencia al punto de interés del dispositivo ahora tiene un tiempo de vida predeterminado de una hora desde el momento en que se recopila. Para obtener más información, consulte [Modificación del tiempo de permanencia de Places](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)

## 27 de enero de 2020

* **PlacesMonitor 2.2.0**

   * **Android**

      * Llame a la nueva API de Places para recopilar el estado de autorización de ubicación cuando la aplicación se inicie y cuando la autorización cambie mientras la aplicación se está ejecutando.
      * Se ha añadido la API setRequestLocationPermission y la API setLocationPermission obsoleta.

## 9 de enero de 2020

* **Places 1.4.0**

   * **Android**

      * Se ha añadido una nueva API, `setAuthorizationStatus`, para establecer el estado de autorización del dispositivo para Servicios de Places. El valor se almacena y se utiliza en el estado compartido de Places.

## 4 de diciembre de 2019

* **PlacesMonitor 2.1.2**

   * **iOS**

      * Llame a la API de Places para recopilar CLAuthorizationStatus del dispositivo cuando cambie.

## 3 de diciembre de 2019

* **ACPPlaces 1.3.0**

   * **iOS**

      * Se ha añadido una nueva API, `setAuthorizationStatus`, para establecer el estado de autorización del dispositivo para Servicios de Places. El valor se almacena y se utiliza en el estado compartido de Places.

## 25 de noviembre de 2019

* **PlacesMonitor 2.1.1**

   * **iOS**

      * Se corrigieron las instrucciones de importación para proyectos de Cocoapods que usan la opción de varios proyectos de pod.

## 22 de noviembre de 2019

* **PlacesMonitor 2.1.1**

   * **Android**

      * El monitor ahora reconoce el inicio de un dispositivo Android y, si es necesario, vuelve a registrar las geovallas con el sistema operativo en función de la ubicación actual del dispositivo.
      * Se ha corregido una condición de carrera que a veces provocaba que se descartaran los eventos de entrada y salida.

## 9 de octubre de 2019

* **PlacesMonitor 2.1.0**

   * **iOS**

      * Se ha añadido una nueva API, `setRequestAuthorizationLevel`, para establecer el tipo de solicitud de autorización de ubicación para la que se solicitará al usuario.
   * **Android**

      * Se ha añadido una nueva API, `setLocationPermission`, para definir el tipo de solicitud de permiso de ubicación para la que se solicitará al usuario.
      * El monitor de Places ahora es compatible con Android 10.



## 8 de agosto de 2019

En esta versión se realizaron las siguientes actualizaciones:

### Actualizaciones de la interfaz de usuario

Esta es una lista de las actualizaciones de la interfaz de usuario de Places:

#### Nuevas características

* Se ha añadido una nueva vista de lista que muestra los puntos de interés sin el mapa.
* Se agregaron opciones de filtrado de puntos de interés para la ciudad, el estado, el país y los metadatos.
* La primera biblioteca de una organización se crea automáticamente.
* Se ha añadido la ordenación de puntos de interés a la vista de lista.

#### Actualizaciones de la interfaz de usuario

* Se ha movido el panel de lista y detalles a la derecha de la interfaz de usuario.
* Se ha agregado un nuevo panel de búsqueda en la parte superior de la interfaz de usuario.
* Si solo hay una biblioteca presente, esta biblioteca se selecciona automáticamente al crear un punto de interés.
* Se ha movido la administración de la biblioteca a una ventana emergente.
* Se ha añadido un recuento de puntos de interés junto a los filtros.

## 6 de agosto de 2019

En esta versión se realizaron las siguientes actualizaciones:

### Supervisar la extensión de Launch 2.0.0

* Se han actualizado las instrucciones de instalación de Android y iOS para el Monitor de Places 2.0.

## 31 de julio de 2019

En esta versión se realizaron las siguientes actualizaciones:

### Monitor de lugares 2.0.0

* El estado de supervisión ahora se mantiene entre inicios.
* La gestión de la llamada de retorno resultante de una solicitud de permiso de ubicación ya no requiere que amplíe PlacesActivity.
* Se ha cambiado una API existente, lo que permite a los desarrolladores borrar todos los datos de Places del dispositivo:

   API anterior: `public static void stop();`

   Nueva API: `public static void stop (final boolean clearData);`

* Se ha actualizado el uso de la variable `getNearbyPointsOfInterest` API para gestionar los escenarios de error de forma más eficaz.

## 25 de julio de 2019

En esta versión se realizaron las siguientes actualizaciones:

### ACPPlacesMonitor 2.0.0

* Para borrar todos los datos de Places del dispositivo,

   en ACPPlacesMonitor, se reemplazó una API existente `+ (void) stop;` con`+ (void) stop: (BOOL) clearData;`.

* Se ha actualizado el uso de ACPPlaces `getNearbyPointsOfInterest` API para gestionar los escenarios de error de forma más eficaz.

## 22 de julio de 2019

En esta versión se realizaron las siguientes actualizaciones:

### Android Places 1.3.0

* Se ha añadido una nueva API que borra todos los datos relacionados con Places del estado compartido, la memoria en la aplicación y la preferencia compartida.
* Se ha corregido un problema por el cual el estado compartido no se actualizaba durante el inicio de la aplicación.
* Se ha corregido un error por el que `getNearbyPointsOfInterest` llamada de retorno devolvía código de error `SERVER_RESPONSE_ERROR instead of CONNECTIVITY_ERROR` sin internet.
* `getNearbyPointsOfInterest` (sin errorCallback) tendrá la variable `successCallback` llamada con lista de puntos de interés vacía, en caso de error al recuperar los puntos de interés cercanos.

## 19 de julio de 2019

En esta versión se realizaron las siguientes actualizaciones:

**iOS Places 1.2.0**

Se ha añadido una nueva API que borra todos los datos relacionados con Places del estado compartido, la memoria en la aplicación y `NSUserDefaults`.

## 25 de junio de 2019

En esta versión se realizaron las siguientes actualizaciones:

**Monitor de iOS Places 1.0.2**

* Mejoras de calidad de vida, incluida una mejor documentación y registro en el código.

## 17 de junio de 2019

En esta versión se realizaron las siguientes actualizaciones:

**iOS Places 1.1.0**

* Se ha añadido una nueva API para devolver un código de error cuando hay un error al recuperar lugares cercanos.
* Cuando el estado de privacidad cambia a opt-out, todos los datos relacionados con Places ahora se eliminan del dispositivo.
* Se ha corregido un problema que, después de un primer inicio, a veces provocaba la pérdida de eventos de Places debido a condiciones de red incorrectas.
* Se ha corregido un problema en el cual, al procesar eventos de entrada de puntos de interés en sucesión rápida, el reemplazo de tokens mediante el motor de reglas a veces hacía referencia al punto de interés incorrecto.

## 30 de mayo de 2019

**Monitor de Android Places 1.0.1**

* Se ha corregido un problema que impedía un evento de entrada para puntos de interés al iniciar la supervisión de Places.

## 28 de mayo de 2019

Se han corregido los siguientes problemas en la interfaz de usuario de Places:

* Se ha actualizado el conmutador de soluciones en Places para alinearlo con el resto del Experience Cloud.
* Se ha corregido un problema por el cual la clasificación se guardaba en los casos en los que no se realizaban cambios de clasificación.
* Se ha aumentado el radio mínimo permitido en la interfaz de usuario a 10 metros.
* Se ha corregido un problema en el cual, si se eliminaban todos los números del campo, el campo radio se restauraba a 20 metros.

## 17 de mayo de 2019

En esta versión se realizaron las siguientes actualizaciones:

**Android Places 1.2.0**

* Se ha añadido una nueva API para procesar una geovalla individual.
* Corrección de errores para evitar varios eventos de entrada consecutivos.

**Monitor de Android Places 1.0.0**

Versión inicial del monitor de Places para Android.

El monitor de Places administra las API de ubicación de nivel de sistema operativo y se comunica directamente con la extensión Places. Con ambas extensiones instaladas, los clientes pueden tener una supervisión de región predeterminada en su aplicación.
Para obtener más información sobre el Monitor de Places, haga clic aquí.


## 2 de mayo de 2019

**Android Places 1.1.0**

* Se ha introducido una nueva API para getNearByPlaces, que tiene un errorCallback y se llama con un errorCode que indica el motivo del error.
* La extensión Places ahora pone en cola los eventos hasta obtener una configuración.
* Se ha agregado compatibilidad con configuraciones que tienen en cuenta el entorno.
* Corrección de errores : se corrigieron las claves de los eventos de entrada y salida de región
* El almacenamiento de la última ubicación conocida ahora respeta correctamente el estado de privacidad del usuario


## 9 de abril de 2019

En esta versión se realizaron las siguientes actualizaciones:

**Monitor de iOS Places 1.0.1**

* Se ha añadido la cobertura completa de la prueba unitaria.
* Integración de CI (CircleCI)
* Integración de cobertura de código (código)

## 25 de marzo de 2019

Monitor de iOS Places 1.0.0

Versión inicial del monitor de Places para iOS.

El monitor de Places administra las API de ubicación de nivel de sistema operativo y se comunica directamente con la extensión Places. Con ambas extensiones instaladas, los clientes pueden tener una supervisión de región predeterminada en su aplicación.

## 28 de febrero de 2019

### Versión beta

Esta es la primera versión de Places Service, un conjunto de herramientas que permite a los clientes enriquecer las experiencias de sus usuarios con datos de ubicación en el mundo real. Para la primera versión, nuestro caso de uso principal es permitir que las aplicaciones móviles recuperen datos de ubicación personalizados y actúen sobre esos datos a través de Adobe Experience Platform Launch.

### Funciones principales

Estas son las funciones clave de esta versión:

#### Interfaz de usuario del servicio de Places

Hemos lanzado una interfaz de usuario de administración en la que puede ver y administrar sus puntos de interés (POI). También puede organizar los puntos de interés en bibliotecas. Además de los metadatos estándar como ciudad, estado y categoría, también admitimos la posibilidad de agregar metadatos personalizados a sus puntos de interés.

* Para ver la interfaz de usuario, vaya a [https://places.adobe.com](https://places.adobe.com).
* Para empezar a usar la interfaz de usuario, consulte [Introducción](/help/getting-started.md).

#### Extensión de Places

Con la extensión Places, puede agregar sus bibliotecas de servicios de Places a su aplicación móvil y actuar en sus puntos de interés. Con el generador de reglas en Experience Platform Launch, puede almacenar en déclencheur las acciones que se activan cuando los usuarios entran y salen de los puntos de interés.

En la extensión Places:

* Puede elegir qué bibliotecas de puntos de interés incluir en la aplicación.
* Eventos de regla que entran en déclencheur al entrar o salir del punto de interés.
* Cree elementos de datos que apunten al punto de interés actual del usuario.

Para obtener más información sobre la extensión Places, consulte [Extensión Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

#### API de Places

Puede utilizar las API de Places para hacer lo siguiente:

* Permita a los desarrolladores rellenar y actualizar su lista de puntos de interés.
* Cree su propia interfaz de usuario o integre con una base de datos de puntos de interés existente.
* Utilice los extremos de lote de la API de Places para realizar una importación masiva de puntos de interés.

   Puede utilizar la utilidad Python proporcionada para completar la importación masiva.

Para obtener más información sobre las API de Places, consulte [API de servicio web](/help/web-service-api/places-web-services.md).

### Próximamente

#### Analytics  de CRM

La extensión de Analytics se está actualizando para añadir automáticamente datos de contexto de ubicación de la base de datos de Places Service a todas las llamadas de Analytics salientes cuando un usuario está en un punto de interés (llamadas pasivas). Esta actualización también permitirá que la creación de reglas active llamadas de seguimiento de Analytics directamente al entrar o salir del punto de interés (llamadas activas).
