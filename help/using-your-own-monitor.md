---
title: Uso de su propio monitor
seo-title: Uso de su propio monitor
description: 'También puede utilizar sus servicios de supervisión e integrarse con Places mediante las API de extensión Places. '
seo-description: 'También puede utilizar sus servicios de supervisión e integrarse con Places mediante las API de extensión Places. '
translation-type: tm+mt
source-git-commit: a2e30282789d9834e5c65502e28ddb25f3c55dfa

---


# Uso de su propio monitor {#using-your-monitor}

También puede utilizar sus servicios de supervisión e integrarse con Places mediante las API de extensión Places.

## Registro de geofences

Si decide utilizar sus servicios de monitoreo, registre las geofences de los puntos de interés en su ubicación actual siguiendo estos pasos:

### iOS

En iOS, complete los siguientes pasos:

1. Pase las actualizaciones de ubicación obtenidas de los servicios de ubicación principales de iOS a la extensión Places.

1. Utilice la API de extensión `getNearbyPointsOfInterest` Places para obtener la matriz de *n* `ACPPlacesPoi` objetos alrededor de la ubicación actual.

   ```objective-c
   - (void) locationManager: (CLLocationManager*) manager didUpdateLocations: (NSArray<CLLocation*>*) locations {
   
          [ACPPlaces getNearbyPointsOfInterest:currentLocation limit:10 callback: ^ (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi) {
              [self startMonitoringGeoFences:nearbyPoi];
      }];
   
   }
   ```

1. Extraiga la información de los `ACPPlacesPOI` objetos obtenidos y comience a monitorear dichos puntos de interés.

   ```objective-c
   - (void) startMonitoringGeoFences: (NSArray*) newGeoFences {
       // verify if the device supports monitoring geofences
       // check for location permission
   
       for (ACPPlacesPoi * currentRegion in newGeoFences) {
           // make the circular region
           CLLocationCoordinate2D center = CLLocationCoordinate2DMake(currentRegion.latitude, currentRegion.longitude);
           CLCircularRegion* currentCLRegion = [[CLCircularRegion alloc] initWithCenter:center                                                                                                                              radius:currentRegion.radius                                                                                                                    identifier:currentRegion.identifier];
           currentCLRegion.notifyOnExit = YES;
           currentCLRegion.notifyOnEntry = YES;
   
           // start monitoring the new region
           [_locationManager startMonitoringForRegion:currentCLRegion];
   
       }
   }
   ```

### Android

1. Pase las actualizaciones de ubicación obtenidas de los servicios Google Play o de los servicios de ubicación de Android a Places Extension.

1. Utilice la API de `getNearbyPointsOfInterest` ubicación para obtener la lista de n `PlacesPoi` objetos alrededor de la ubicación actual.

   ```java
       LocationCallback callback = new LocationCallback() {
               @Override
               public void onLocationResult(LocationResult locationResult) {
                   super.onLocationResult(locationResult);
   
                   Places.getNearbyPointsOfInterest(currentLocation, 10, new            AdobeCallback<List<PlacesPOI>>() {
               @Override
               public void call(List<PlacesPOI> pois)
                   starMonitoringGeofence(pois);
               }
           });
   
               }
           };
   ```

1. Extraiga los datos de los `PlacesPOI` objetos obtenidos y comience a monitorear dichos puntos de interés.

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


Al llamar a la `getNearbyPointsOfInterest` API se produce una llamada de red que obtiene la ubicación alrededor de la ubicación actual.

>[!IMPORTANT]
>
>Debe llamar a la API con moderación o solo cuando haya un cambio significativo en la ubicación del usuario.

## Anuncio de eventos de geofencia

### iOS

En iOS, llame a la API de `processGeofenceEvent` lugares en el `CLLocationManager` delegado. Esta API le notifica si el usuario ha entrado o salido de una región específica.

```objective-c
- (void) locationManager:(CLLocationManager *)manager didEnterRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
}

- (void) locationManager:(CLLocationManager *)manager didExitRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeExit];
}
```
