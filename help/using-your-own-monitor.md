---
title: Uso de su propio monitor
description: También puede utilizar los servicios de monitorización e integrarse con el servicio de Places mediante las API de extensión del servicio de Places.
exl-id: 8ca4d19b-0f23-4291-b335-af47f03179fa
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 1%

---

# Uso de su propio monitor {#using-your-monitor}

También puede utilizar los servicios de monitorización e integrarse con el servicio de Places mediante las API de extensión de Places.

## Registro de geoperímetros

Si decide utilizar los servicios de monitorización, registre las geovallas de los puntos de interés alrededor de su ubicación actual completando los siguientes pasos:

### iOS

En iOS, complete los siguientes pasos:

1. Pase las actualizaciones de ubicación obtenidas de los servicios de ubicación principales de iOS a la extensión Places.

1. Utilice la API de extensión `getNearbyPointsOfInterest` Places para obtener la matriz de `ACPPlacesPoi` objetos alrededor de la ubicación actual.

   ```objective-c
   - (void) locationManager: (CLLocationManager*) manager didUpdateLocations: (NSArray<CLLocation*>*) locations {
       [ACPPlaces getNearbyPointsOfInterest:currentLocation limit:10 callback: ^ (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi) {
           [self startMonitoringGeoFences:nearbyPoi];
       }];
   }
   ```

1. Extraiga la información de los objetos `ACPPlacesPOI` obtenidos y comience a monitorizar esos puntos de interés.

   ```objective-c
   - (void) startMonitoringGeoFences: (NSArray*) newGeoFences {
       // verify if the device supports monitoring geofences
       // check for location permission
   
       for (ACPPlacesPoi * currentRegion in newGeoFences) {
           // make the circular region
           CLLocationCoordinate2D center = CLLocationCoordinate2DMake(currentRegion.latitude, currentRegion.longitude);
           CLCircularRegion* currentCLRegion = [[CLCircularRegion alloc] initWithCenter:center
                                                                                 radius:currentRegion.radius
                                                                             identifier:currentRegion.identifier];
           currentCLRegion.notifyOnExit = YES;
           currentCLRegion.notifyOnEntry = YES;
   
           // start monitoring the new region
           [_locationManager startMonitoringForRegion:currentCLRegion];
       }
   }
   ```

### Android

1. Pase las actualizaciones de ubicación obtenidas de los servicios de Google Play o de los servicios de ubicación de Android a la extensión Places.

1. Utilice la API de extensión de `getNearbyPointsOfInterest` Places para obtener la lista de `PlacesPoi` objetos alrededor de la ubicación actual.

   ```java
   LocationCallback callback = new LocationCallback() {
       @Override
       public void onLocationResult(LocationResult locationResult) {
           super.onLocationResult(locationResult);
   
           Places.getNearbyPointsOfInterest(currentLocation, 10, new AdobeCallback<List<PlacesPOI>>() {
               @Override
               public void call(List<PlacesPOI> pois) {
                   starMonitoringGeofence(pois);
               }
           });
       }
   };
   ```

1. Extraiga los datos de los objetos `PlacesPOI` obtenidos y comience a monitorizar esos puntos de interés.

   ```java
   private void startMonitoringFences(final List<PlacesPOI> nearByPOIs) {
       // check for location permission
       for (PlacesPOI poi : nearByPOIs) {
           final Geofence fence = new Geofence.Builder()
               .setRequestId(poi.getIdentifier())
               .setCircularRegion(poi.getLatitude(), poi.getLongitude(), poi.getRadius())
               .setExpirationDuration(Geofence.NEVER_EXPIRE)
               .setTransitionTypes(Geofence.GEOFENCE_TRANSITION_ENTER |
                                   Geofence.GEOFENCE_TRANSITION_EXIT)
               .build();
           geofences.add(fence);
       }
   
       GeofencingRequest.Builder builder = new GeofencingRequest.Builder();
       builder.setInitialTrigger(GeofencingRequest.INITIAL_TRIGGER_ENTER);
       builder.addGeofences(geofences);
       builder.build();
       geofencingClient.addGeofences(builder.build(), geoFencePendingIntent)
   }
   ```


Llamar a la API `getNearbyPointsOfInterest` da como resultado una llamada de red que obtiene la ubicación alrededor de la ubicación actual.

>[!IMPORTANT]
>
>Debe llamar a la API con moderación o solo cuando haya un cambio de ubicación significativo del usuario.

## Contabilización de eventos de geoperímetro

### iOS

En iOS, llame a la API `processGeofenceEvent` Places en el delegado `CLLocationManager`. Esta API le notifica si el usuario ha entrado o salido de una región específica.

```objective-c
- (void) locationManager:(CLLocationManager *)manager didEnterRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
}

- (void) locationManager:(CLLocationManager *)manager didExitRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeExit];
}
```

### Android

En Android, llame al método `processGeofence` junto con el evento de transición correspondiente en el receptor de difusión de Geoperímetro. Es posible que desee depurar la lista de geovallas recibidas para evitar entradas/salidas duplicadas.

```java
void onGeofenceReceived(final Intent intent) {
    // do appropriate validation steps for the intent
    ...

    // get GeofencingEvent from intent
    GeofencingEvent geoEvent = GeofencingEvent.fromIntent(intent);

    // get the transition type (entry or exit)
    int transitionType = geoEvent.getGeofenceTransition();

    // validate your geoEvent and get the necessary Geofences from the list
    List<Geofence> myGeofences = geoEvent.getTriggeringGeofences();

    // process region events for your geofences
    for (Geofence geofence : myGeofences) {
        Places.processGeofence(geofence, transitionType);
    }
}
```
