---
title: Referencia de API de Places
description: Información sobre las referencias de la API en Places.
feature: Mobile SDK
exl-id: ce1a113c-dee0-49df-8d2f-789ccc1c8322
source-git-commit: f521d5e3b0b69977877d88382ce41fcb7d1c54b9
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 32%

---

# Referencia de API de Places {#places-api-reference}

Esta es la información sobre las referencias de API en la extensión Places:

## Procesamiento de un evento de región

Cuando un dispositivo cruza uno de los límites de región del servicio Places predefinidos de la aplicación, la región y el tipo de evento se pasan al SDK para su procesamiento.

### ProcessGeoperimetral (Android)

Procesar un evento de región `Geofence` para el elemento `transitionType` proporcionado.

Pasar `transitionType` de `GeofencingEvent.getGeofenceTransition()`. Actualmente `Geofence.GEOFENCE_TRANSITION_ENTER` y `Geofence.GEOFENCE_TRANSITION_EXIT` son compatibles.

**Sintaxis**

Esta es la sintaxis para este método:

```java
public static void processGeofence(final Geofence geofence, final int transitionType);
```

**Ejemplo**

Llame a este método en su `IntentService` que esté registrado para recibir eventos de geovalla de Android.

Este es un ejemplo de código para este método:

```java
public class GeofenceTransitionsIntentService extends IntentService {

    public GeofenceTransitionsIntentService() {
        super("GeofenceTransitionsIntentService");
    }

    protected void onHandleIntent(Intent intent) {
        GeofencingEvent geofencingEvent = GeofencingEvent.fromIntent(intent);

        List<Geofence> geofences = geofencingEvent.getTriggeringGeofences();

        if (geofences.size() > 0) {
          // Call the Places API to process information
          Places.processGeofence(geofences.get(0), geofencingEvent.getGeofenceTransition());
        }
    }
}
```

### ProcessRegionEvent (iOS)

Se debe llamar a este método en el delegado `CLLocationManager`, que indica si el usuario ha entrado o salido de una región específica.

**Sintaxis**

Esta es la sintaxis para este método:

```objectivec
+ (void) processRegionEvent: (nonnull CLRegion*) region forRegionEventType: (ACPRegionEventType) eventType;
```

**Ejemplo**

Este es un ejemplo de código para este método:


```objectivec
- (void) locationManager:(CLLocationManager *)manager didEnterRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
}

- (void) locationManager:(CLLocationManager *)manager didExitRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeExit];
}
```

### ProcessGeoperencingEvent (Android)

Procesar todos(as) los/las `Geofences` en `GeofencingEvent` al mismo tiempo.

**Sintaxis**

```java
public static void processGeofenceEvent(final GeofencingEvent geofencingEvent);
```

**Ejemplo**

Llame a este método en su `IntentService` que esté registrado para recibir eventos de geovalla de Android

```java
public class GeofenceTransitionsIntentService extends IntentService {

    public GeofenceTransitionsIntentService() {
        super("GeofenceTransitionsIntentService");
    }

    protected void onHandleIntent(Intent intent) {
        GeofencingEvent geofencingEvent = GeofencingEvent.fromIntent(intent);
        // Call the Places API to process information
        Places.processGeofenceEvent(geofencingEvent);
    }
}
```

## Recuperar puntos de interés cercanos

Devuelve una lista ordenada de puntos de interés cercanos en una llamada de retorno. Una versión sobrecargada de este método devuelve un código de error si algo salió mal con la llamada de red resultante.

### GetNearbyPointsOfInterest (Android)

Esta es la sintaxis para este método:

**Sintaxis**

```java
public static void getNearbyPointsOfInterest(final Location location, final int limit,
                                             final AdobeCallback<List<PlacesPOI>> callback);

public static void getNearbyPointsOfInterest(final Location location, final int limit,
                                             final AdobeCallback<List<PlacesPOI>> callback,
                                             final AdobeCallback<PlacesRequestError> errorCallback);
```

**Ejemplo**

Este es un ejemplo de código para este método:

```java
// getNearbyPointsOfInterest without an error callback
Places.getNearbyPointsOfInterest(currentLocation, 10, new AdobeCallback<List<PlacesPOI>>() {
    @Override
    public void call(List<PlacesPOI> pois) {
        // do required processing with the returned nearbyPoi array
        startMonitoringPois(pois);
    }
});

// getNearbyPointsOfInterest with an error callback
Places.getNearbyPointsOfInterest(currentLocation, 10,
    new AdobeCallback<List<PlacesPOI>>() {
        @Override
        public void call(List<PlacesPOI> pois) {
            // do required processing with the returned nearbyPoi array
            startMonitoringPois(pois);
        }
    }, new AdobeCallback<PlacesRequestError>() {
        @Override
        public void call(PlacesRequestError placesRequestError) {
            // look for the placesRequestError and handle the error accordingly
            handleError(placesRequestError);
        }
    }
);
```

### GetNearbyPointsOfInterest (iOS)

**Sintaxis**

```objectivec
+ (void) getNearbyPointsOfInterest: (nonnull CLLocation*) currentLocation
                             limit: (NSUInteger) limit
                          callback: (nullable void (^) (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi)) callback;

+ (void) getNearbyPointsOfInterest: (nonnull CLLocation*) currentLocation
                             limit: (NSUInteger) limit
                          callback: (nullable void (^) (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi)) callback
                     errorCallback: (nullable void (^) (ACPPlacesRequestError result)) errorCallback;
```

**Ejemplo**

```objectivec
// getNearbyPointsOfInterest without an error callback
[ACPPlaces getNearbyPointsOfInterest:location
                               limit:10     
                            callback:^(NSArray<ACPPlacesPoi*>* nearbyPoi) {
    // do required processing with the returned nearbyPoi array
    [self startMonitoringPois:nearbyPOI];
}];

// getNearbyPointsOfInterest with an error callback
[ACPPlaces getNearbyPointsOfInterest:location limit:10
    callback:^(NSArray<ACPPlacesPoi *> * _Nullable nearbyPoi) {
        // do required processing with the returned nearbyPoi array
        [self startMonitoringPois:nearbyPOI];
    } errorCallback:^(ACPPlacesRequestError result) {
        // look for the error and handle accordingly
        [self handleError:result];
    }
];
```

## Recuperar puntos de interés del dispositivo actual

Solicita una lista de puntos de interés en los que se sabe que se encuentra el dispositivo y los devuelve en una llamada de retorno.

### GetCurrentPointsOfInterest (Android)

Esta es la sintaxis para este método:

**Sintaxis**

```java
public static void getCurrentPointsOfInterest(final AdobeCallback<List<PlacesPOI>> callback);
```

**Ejemplo**

Este es un ejemplo de código para este método:

```java
Places.getCurrentPointsOfInterest(new AdobeCallback<List<PlacesPOI>>() {
    @Override
    public void call(List<PlacesPOI> pois) {
        // use the obtained POIs that the device is within
        processUserWithinPois(pois);        
    }
});
```

### GetCurrentPointsOfInterest (iOS)

**Sintaxis**

Esta es la sintaxis para este método:

```objectivec
+ (void) getCurrentPointsOfInterest: (nullable void (^) (NSArray<ACPPlacesPoi*>* _Nullable userWithinPoi)) callback;
```

**Ejemplo**

Este es un ejemplo de código para este método:

```objectivec
[ACPPlaces getCurrentPointsOfInterest:^(NSArray<ACPPlacesPoi*>* userWithinPoi) {
    // do required processing with the returned userWithinPoi array
    [self processUserWithinPois:userWithinPoi];
}];
```


## Obtener la ubicación del dispositivo

Solicita la ubicación del dispositivo, como se conocía anteriormente, por la extensión Places.

>[!TIP]
>
>La extensión Places solo conoce las ubicaciones que se le proporcionaron mediante llamadas a `GetNearbyPointsOfInterest`.


### GetLastKnownLocation (Android)

**Sintaxis**

Esta es la sintaxis para este método:

```java
public static void getLastKnownLocation(final AdobeCallback<Location> callback);
```

**Ejemplo**

Este es un ejemplo de código para este método:

```java
Places.getLastKnownLocation(new AdobeCallback<Location>() {
    @Override
    public void call(Location lastLocation) {
        // do something with the last known location
        processLastKnownLocation(lastLocation);        
    }
});
```

### GetLastKnownLocation (iOS)

**Sintaxis**

Esta es la sintaxis para este método:

```objectivec
+ (void) getLastKnownLocation: (nullable void (^) (CLLocation* _Nullable lastLocation)) callback;
```

**Ejemplo**

Este es un ejemplo de código para este método:

```objectivec
[ACPPlaces getLastKnownLocation:^(CLLocation* lastLocation) {
    // do something with the last known location
    [self processLastKnownLocation:lastLocation];
}];
```

## Borrar datos del lado del cliente


### Borrar (Android)

Borra los datos del lado del cliente para la extensión Places en estado compartido, almacenamiento local y en memoria.

**Sintaxis**

Esta es la sintaxis para este método:

```java
public static void clear();
```

**Ejemplo**

Este es un ejemplo de código para este método:

```java
Places.clear();
```

### borrar (iOS)

Borra los datos del lado del cliente para la extensión Places en estado compartido, almacenamiento local y en memoria.

**Sintaxis**

Esta es la sintaxis para este método:

```objectivec
+ (void) clear;
```

**Ejemplo**

Este es un ejemplo de código para este método:

```objectivec
[ACPPlaces clear];
```

## Establecer estado de autorización de ubicación

### setAuthorizationStatus (Android)

*Disponible a partir de Places v1.4.0*

Establece el estado de autorización en la extensión Places.

El estado proporcionado se almacena en el estado compartido de Places y es solo de referencia.
Llamar a este método no afecta al estado real de autorización de ubicación de este dispositivo.

**Sintaxis**

Esta es la sintaxis para este método:

```java
public static void setAuthorizationStatus(final PlacesAuthorizationStatus status);
```

**Ejemplo**

Este es un ejemplo de código para este método:

```java
Places.setAuthorizationStatus(PlacesAuthorizationStatus.ALWAYS);
```

### setAuthorizationStatus (iOS)

*Disponible a partir de CAPPlaces v1.3.0*

Establece el estado de autorización en la extensión Places.

El estado proporcionado se almacena en el estado compartido de Places y es solo de referencia.
Llamar a este método no afecta al estado real de autorización de ubicación de este dispositivo.

Cuando cambia el estado de autorización del dispositivo, se invoca el método `locationManager:didChangeAuthorizationStatus:` de su `CLLocationManagerDelegate`. Desde este método, debe pasar el nuevo valor `CLAuthorizationStatus` a la API `setAuthorizationStatus:` de ACPlaces.

**Sintaxis**

Esta es la sintaxis para este método:

```objectivec
+ (void) setAuthorizationStatus: (CLAuthorizationStatus) status;
```

**Ejemplo**

Este es un ejemplo de código para este método:

```objectivec
- (void) locationManager: (CLLocationManager*) manager didChangeAuthorizationStatus: (CLAuthorizationStatus) status {    
    [ACPPlaces setAuthorizationStatus:status];
}
```
