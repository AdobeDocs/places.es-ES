---
title: Referencia de la API de Places Monitor
seo-title: Referencia de la API de Places Monitor
description: 'Una lista de las API para el Monitor de lugares. '
seo-description: 'Una lista de las API para el Monitor de lugares.  '
translation-type: tm+mt
source-git-commit: 01617e4e1658f92234803baf1e57282777d04b13

---


# Referencia de la API de Places Monitor {#places-api-reference}

## Extensión del monitor de lugares de registro

Registra la extensión del monitor de lugares con el centro de eventos principal.

### RegisterExtension (Android)

Esta es la sintaxis y el código de ejemplo de esta API:

#### Sintaxis

Esta es la sintaxis en Java:

```java
public static void registerExtension();
```

#### Ejemplo

Llame a este método en el `onCreate` método donde se inicializa el resto del SDK de la plataforma de experiencia.

```java
public class MobileApp extends Application {
  @Override
  public void onCreate(){
     super.onCreate();
     MobileCore.setApplication(this);
     try {
        PlacesMonitor.registerExtension();
     } catch (Exception e) {
       //Log the exception
       }
    }
 }
```

### RegisterExtension (iOS)

Esta es la sintaxis y el código de ejemplo de esta API:

#### Sintaxis

Esta es la sintaxis de Objective-C:

```objective-c
+ (void) registerExtension;
```

#### Ejemplo

This method should be called in the `didFinishLaunchingWithOptions` delegate method of the `AppDelegate`.

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {

    [ACPCore configureWithAppId:@"launch-appID"];    
    [ACPPlaces registerExtension];    
    [ACPPlacesMonitor registerExtension];

    [ACPCore start:^{
        // do other initialization of the SDK
    }];

    return YES;
}
```

## Versión de extensión

Devuelve la versión actual de la extensión Monitor de lugares

### ExtensionVersion (Android)

Esta es la sintaxis y el código de ejemplo de esta API:

#### Sintaxis

```java
public static String extensionVersion();
```

#### Ejemplo

```java
String placesMonitorVersion = PlacesMonitor.extensionVersion();
```

### ExtensionVersion (iOS)

Esta es la sintaxis y el código de ejemplo de esta API:

#### Sintaxis

```objective-c
+ (nonnull NSString*) extensionVersion;
```

#### Ejemplo

```objective-c
NSString *placesMonitorVersion = [ACPPlacesMonitor extensionVersion];
```

## Iniciar supervisión de dispositivos

Comience el seguimiento de la ubicación del dispositivo y la supervisión de lugares cercanos.

### Inicio (Android)

Si el usuario no ha concedido autorización para utilizar la ubicación del dispositivo, la primera llamada a la `start` API solicita permiso al usuario.

Esta es la sintaxis y el código de ejemplo de esta API:

#### Sintaxis

```java
public static void start();
```

#### Ejemplo

```java
PlacesMonitor.start();
```

### Inicio (iOS)

>[!IMPORTANT]
>
>Para comenzar la supervisión, el servicio de ubicación debe tener la autorización necesaria:
>
>* Si no se ha proporcionado la autorización para el servicio de ubicación a la aplicación, la primera llamada a la `start` API solicita la autorización para utilizar el servicio de ubicación configurado para la aplicación.
>* Según las capacidades del dispositivo, si se ha proporcionado la autorización, el Monitor de lugares rastrea la ubicación del usuario en función del conjunto actual `ACPPlacesMonitorMode`. De forma predeterminada, el monitor utiliza `ACPPlacesMonitorModeSignificantChanges`.


>[!CAUTION]
>
>Si la llamada para iniciar la supervisión se realiza antes de que el SDK haya terminado de inicializarse, puede que se ignore.

Puede asegurarse de que el SDK ha finalizado la inicialización llamando `start` desde la llamada de retorno proporcionada a `ACPCore::start:`.

Esta es la sintaxis y el código de ejemplo de esta API:

#### Sintaxis

```objectivec
+ (void) start;
```

#### Ejemplo

Inicio del Monitor de lugares cuando se está inicializando el SDK:

```objective-c
[ACPCore start:^{
    [ACPPlacesMonitor start];
}];
```

Inicio del monitor de lugares más adelante en la ejecución de la aplicación:

```objective-c
[ACPPlacesMonitor start];
```

## Detener supervisión de dispositivos

Detiene el seguimiento de la ubicación del dispositivo.

### Detener (Android)

Esta es la sintaxis y el código de ejemplo de esta API:

#### Sintaxis

```java
public static void stop();
```

#### Ejemplo

```java
PlacesMonitor.stop();
```

### Detener (iOS)

Esta es la sintaxis y el código de ejemplo de esta API:

#### Sintaxis

```objectivec
+ (void) stop;
```

#### Ejemplo

```objective-c
[ACPPlacesMonitor stop];
```

## Actualizar ubicación

Utilice esta API para una actualización inmediata de la ubicación del dispositivo. Cuando llama a esta API, el dispositivo intenta determinar la ubicación con el nivel de precisión que especificó. Este proceso también actualiza los puntos de interés cercanos supervisados por la extensión.

### UpdateLocation (Android)

Esta es la sintaxis y el código de ejemplo de esta API:

#### Sintaxis

```java
public static void updateLocation();
```

#### Ejemplo

```java
PlacesMonitor.updateLocation();
```

### UpdateLocationNow (iOS)

#### Sintaxis

```objective-c
+ (void) updateLocationNow;
```

#### Ejemplo

```objective-c
[ACPPlacesMonitor updateLocationNow];
```

## Permiso de ubicación de la aplicación

Puede utilizar esta API para establecer el tipo de permiso de ubicación que se solicita al usuario y que se le autoriza a utilizar para los servicios de ubicación.

### SetLocationPermission (Android)

Esta API establece el tipo de solicitud de permiso de ubicación para la que se solicita al usuario que seleccione.

>[!TIP]
>
>Esta API solo es efectiva para dispositivos con Android 10 y versiones posteriores.
>
>Para configurar el mensaje de autorización adecuado para que se muestre al usuario, llame a esta API antes de la `PlacesMonitor.start()`. Al llamar a este método, mientras se supervisa activamente, se actualiza el nivel de permisos de ubicación al valor de permiso solicitado. Si el usuario de la aplicación ya ha proporcionado o denegado el nivel de autorización solicitado, o si intenta reducir el permiso de `ALWAYS_ALLOW` a `WHILE_USING_APP`, este método no tiene ningún efecto.

El permiso de ubicación se puede establecer en uno de los siguientes valores:

* `PlacesMonitorLocationPermission.WHILE_USING_APP`

   Este valor solicita al usuario que acceda a la ubicación del dispositivo solo mientras utiliza la aplicación. Se considera que una aplicación está en uso cuando el usuario está mirando la aplicación en la pantalla del dispositivo, por ejemplo, se está ejecutando una actividad en primer plano.

   >[!TIP]
   >
   >Asegúrese de que el permiso de usuario de ACCESS_FINE_LOCATION está establecido en el archivo de manifiesto de la aplicación.

* `PlacesMonitorLocationPermission.ALWAYS_ALLOW`

   Este valor indica al usuario que acceda a la ubicación del dispositivo incluso cuando la aplicación está en segundo plano.

   >[!TIP]
   >
   >Asegúrese de que los permisos de usuario de ACCESS_BACKGROUND_LOCATION y ACCESS_FINE_LOCATION están configurados en el archivo de manifiesto de la aplicación.

   `PlacesMonitorLocationPermission.ALWAYS_ALLOW` es el valor de permiso de ubicación predeterminado.

>[!IMPORTANT]
>
>Si se concede el permiso al usuario de la aplicación, las geofences no se registrarán en el sistema operativo. `WHILE_USING_APP` Como resultado, la extensión del monitor de lugares no activará eventos de entrada y salida en las regiones que están teniendo lugar en segundo plano.

Esta es la sintaxis y el código de ejemplo de esta API:

#### Sintaxis

```java
public static void setLocationPermission(final PlacesMonitorLocationPermission placesMonitorLocationPermission)
```

#### Ejemplo

Para solicitar el `WHILE_USING_APP` permiso:

```java
// set the location permission
PlacesMonitor.setLocationPermission(PlacesMonitorLocationPermission.WHILE_USING_APP);
// start monitoring
PlacesMonitor.start()
```

Para actualizar a `ALWAYS_ALLOW` permiso:

```java
// upgrade the permission level
PlacesMonitor.setLocationPermission(PlacesMonitorLocationPermission.ALWAYS_ALLOW);
```

### SetRequestAuthorizationLevel (iOS)

Esta API establece el tipo de solicitud de autorización de ubicación para la que se solicitará al usuario.

Para configurar que el mensaje de autorización correspondiente se muestre al usuario, llame `SetRequestAuthorizationLevel` antes de llamar `[ACPPlacesMonitor start]`. Para configurar el mensaje de autorización adecuado para que se muestre al usuario, llame a esta API antes del `[ACPPlacesMonitor start]`. Al llamar a este método mientras se supervisa activamente, se actualizará el nivel de autorización de ubicación al valor de autorización solicitado. Si el nivel de autorización solicitado ya ha sido proporcionado o denegado por el usuario de la aplicación o si hay una rebaja del permiso de `ACPPlacesRequestAuthorizationLevelAlways` `ACPPlacesRequestAuthorizationLevelWhenInUse` a la autorización, este método no tiene ningún efecto.

El nivel de autorización se puede establecer en uno de los siguientes valores:

* `ACPPlacesRequestAuthorizationLevelWhenInUse`

   Solicita el permiso del usuario para utilizar los servicios de ubicación mientras la aplicación está en uso. El mensaje del usuario contiene el texto de la `NSLocationWhenInUseUsageDescription` clave en el archivo Info.plist de la aplicación y se requiere la presencia de esa clave al llamar a este método. Para obtener más información, consulte la documentación de [Apple en requestWhenInUseAuthorization](https://developer.apple.com/documentation/corelocation/cllocationmanager/1620562-requestwheninuseauthorization).

* `ACPPlacesRequestMonitorAuthorizationLevelAlways`

   Utilice esta enumeración para solicitar servicios de ubicación incluso cuando la aplicación esté en segundo plano. Debe tener las `NSLocationAlwaysUsageDescription` teclas y `NSLocationWhenInUseUsageDescription` en Info.plist de la aplicación. Estas teclas definen el texto que aparecerá durante el mensaje del usuario. Para obtener más información, consulte la documentación de [Apple sobre requestalwayspermission](https://developer.apple.com/documentation/corelocation/cllocationmanager/1620551-requestalwaysauthorization).

`ACPPlacesRequestAuthorizationLevelAlways` es el valor de autorización de solicitud predeterminado.

>[!IMPORTANT]
>
>La aplicación que autorizó el uso del `ACPPlacesRequestAuthorizationLevelWhenInUse` permiso no podrá activar eventos de entrada y salida en regiones que se encuentren en segundo plano.

Esta es la sintaxis y el código de ejemplo de esta API:

#### Sintaxis

```objective-c
+ (void) setRequestAuthorizationLevel: (ACPPlacesRequestAuthorizationLevel) requestAuthorizationLevel
```

#### Ejemplo

Para solicitar el `ACPPlacesRequestAuthorizationLevelWhenInUse` permiso:

```objective-c
// set the request authorization level
[ACPPlacesMonitor setRequestAuthorizationLevel: ACPPlacesRequestAuthorizationLevelWhenInUse];
// start monitoring
[ACPPlacesMonitor start];
```

Para actualizar a `ACPPlacesRequestAuthorizationLevelAlways` autorización:

```objective-c
// set the request authorization level
[ACPPlacesMonitor setRequestAuthorizationLevel: ACPPlacesRequestAuthorizationLevelAlways]
```

## Modo de supervisión (solo iOS)

La supervisión se puede establecer en uno de los siguientes valores:

* `ACPPlacesMonitorModeContinuous`

   La extensión de supervisión recibe y procesa las ubicaciones con mayor frecuencia. Esta estrategia de monitoreo consume mucha energía pero proporciona mayor precisión. Para obtener más información, consulte la documentación de [Apple sobre supervisión](https://developer.apple.com/documentation/corelocation/cllocationmanager/1423750-startupdatinglocation)continua.

* `ACPPlacesMonitorModeSignificantChanges`

   La extensión de supervisión solo recibe y procesa actualizaciones de ubicación después de que el dispositivo se haya desplazado una distancia significativa desde la ubicación procesada anteriormente. Esta estrategia de monitoreo consume menos energía que la estrategia de monitoreo continuo. Para obtener más información, consulte la documentación de [Apple sobre supervisión significativa](https://developer.apple.com/documentation/corelocation/cllocationmanager/1423531-startmonitoringsignificantlocati)

### SetPlacesMonitorMode (iOS)

Esta es la sintaxis y el código de ejemplo de esta API:

#### Sintaxis

```objective-c
+ (void) setPlacesMonitorMode: (ACPPlacesMonitorMode) monitorMode;
```

#### Ejemplo

```objective-c
[ACPPlacesMonitor setPlacesMonitorMode:ACPPlacesMonitorModeSignificantChanges];
```
