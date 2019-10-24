---
title: Referencia de la API de lugares
seo-title: Referencia de la API de lugares
description: Información sobre las referencias de API en Lugares.
seo-description: Información sobre las referencias de API en Lugares.
translation-type: tm+mt
source-git-commit: fd1b37a0f50d93de1efff4cb38fc23253f02d517

---


# Referencia de la API de lugares {#places-api-reference}

Esta es la información sobre las referencias de API en Lugares:

## Procesamiento de un evento de región

Cuando un dispositivo cruza uno de los límites predefinidos de la región Lugares de la aplicación, la región y el tipo de evento se pasan al SDK para su procesamiento.

### ProcessGeofence (Android)

Procesar un evento de `Geofence` región para el `transitionType`.

Pasa el `transitionType` de `GeofencingEvent.getGeofenceTransition()`. Actualmente `Geofence.GEOFENCE_TRANSITION_ENTER` y `Geofence.GEOFENCE_TRANSITION_EXIT` son compatibles.

**Sintaxis**

Esta es la sintaxis para este método:

```java
public static void processGeofence(final Geofence geofence, final int transitionType);
```

**Ejemplo**

Llame a este método en el `IntentService` que esté registrado para recibir eventos de geofence de Android.

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

Se debe llamar a este método en el `CLLocationManager` delegado, que indica si el usuario ha entrado o salido de una región específica.

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

### ProcessGeofencingEvent (Android)

Procesar todo `Geofences` al `GeofencingEvent` mismo tiempo.

**Sintaxis**

```java
public static void processGeofenceEvent(final GeofencingEvent geofencingEvent);
```

**Ejemplo**

Llame a este método en el `IntentService` que esté registrado para recibir eventos de geofence de Android

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

Devuelve una lista ordenada de puntos de interés cercanos en una llamada de retorno.

### GetNearbyPointsOfInterest (Android)

Esta es la sintaxis para este método:

**Sintaxis**

```java
public static void getNearbyPointsOfInterest(final Location location,
    final int limit, final AdobeCallback<List<PlacesPOI>> callback);
```

**Ejemplo**

Este es un ejemplo de código para este método:

```java
Places.getNearbyPlaces(currentLocation, 10, new AdobeCallback<List<PlacesPOI>>() {
    @Override
    public void call(List<PlacesPOI> pois) {
        // do required processing with the returned nearbyPoi array
        startMonitoringPois(pois);
    }
});
```

### GetNearbyPointsOfInterest (iOS)

**Sintaxis**

```objectivec
+ (void) getNearbyPointsOfInterest: (nonnull CLLocation*) currentLocation
                             limit: (NSUInteger) limit
                          callback: (nullable void (^) (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi)) callback;
```

**Ejemplo**

```objectivec
[ACPPlaces getNearbyPointsOfInterest:location
                               limit:10     
                            callback:^(NSArray<ACPPlacesPoi*>* nearbyPoi) {
    // do required processing with the returned nearbyPoi array
    [self startMonitoringPois:nearbyPOI];
}];
```

## Recuperar puntos de interés actuales del dispositivo

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

Solicita la ubicación del dispositivo, como se conoce anteriormente, mediante la extensión Places.

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

Borra los datos del lado del cliente para los lugares en estado compartido, almacenamiento local y en memoria.

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

### clear (iOS)

Borra los datos del lado del cliente para los lugares en estado compartido, almacenamiento local y en memoria.

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
