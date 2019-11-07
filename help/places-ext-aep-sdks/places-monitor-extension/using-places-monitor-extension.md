---
title: Uso de la extensión Monitor de lugares
seo-title: Uso de la extensión Monitor de lugares
description: Información sobre cómo instalar, configurar y utilizar la extensión Monitor de lugares.
seo-description: Información sobre cómo instalar, configurar y utilizar la extensión Monitor de lugares.
translation-type: tm+mt
source-git-commit: 419df41a0abeac1ac2a77f32bfa818b4edf3baeb

---


# Uso de la extensión Monitor de lugares {#using-places-monitor-extension}

Para utilizar la extensión Monitor de lugares, realice las siguientes tareas:

## Instalación de la extensión Places Monitor en Experience Platform Launch

1. In Experience Platform Launch, click the **[!UICONTROL Extensions]** tab.
1. En la **[!UICONTROL Catalog]** ficha, busque la **[!UICONTROL Places Monitor]** extensión y haga clic en **Instalar**.
1. Haga clic en **[!UICONTROL Save]**.
1. Siga el proceso de publicación para actualizar la configuración del SDK.

### Configurar la extensión del monitor de lugares {#configure-places-monitor-extension}

No hay tareas de configuración para la extensión Places Monitor.

![configurar la ‌ del Monitor](/help/assets/configure_places_monitor.png)de lugares

## Agregar la extensión del monitor de lugares a la aplicación {#add-monitor-extension-to-app}

Debe agregar la extensión del monitor de lugares a la aplicación de Android o iOS.

### Android

En Android, complete los siguientes pasos:

#### Java

1. Añada la extensión Places Monitor y la extensión Places al proyecto mediante el archivo de gradle de la aplicación.

1. También incluya los servicios de ubicación de Google más recientes en el archivo de gradle.

   ```java
   implementation 'com.adobe.marketing.mobile:places:1.+'
   implementation 'com.adobe.marketing.mobile:places-monitor:1.+'
   implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
   implementation 'com.google.android.gms:play-services-location:16.0.0'
   ```

1. Importe la extensión del monitor de lugares en la actividad principal de la aplicación.

   ```java
   import com.adobe.marketing.mobile.PlacesMonitor;
   ```

### iOS

En iOS, complete los siguientes pasos:

1. Añada la biblioteca al proyecto a través de los cocoápodos `Podfile` agregando `pod 'ACPPlacesMonitor'`.
1. Importar las bibliotecas del Monitor de lugares y lugares:

#### Objective-C

```objectivec
#import "ACPCore.h"
#import "ACPPlaces.h"
#import "ACPPlacesMonitor.h"
```

#### Swift

```swift
import ACPCore
import ACPPlaces
import ACPPlacesMonitor
```


## Registro e inicio del monitor de lugares {#register-start-places-monitor}

Debe registrarse e iniciar el Monitor de lugares en Android o iOS.

## Android

En Android, complete los siguientes pasos:

### Java

En el `OnCreate` método de la aplicación, registre las extensiones del monitor de lugares:

```java
public class MobileApp extends Application {
    @Override
    public void onCreate() {
        super.onCreate();
        MobileCore.setApplication(this);
        MobileCore.ConfigureWithAppId("yourAppId");
        try {
            PlacesMonitor.registerExtension(); //Register PlacesMonitor with Mobile Core
            Places.registerExtension(); //Register Places with Mobile Core
            MobileCore.start(null);
        } catch (Exception e) {
            //Log the exception
         }
    }
}
```

>[!IMPORTANT]
>
>La supervisión de lugares depende de la extensión Places. Cuando instale manualmente la extensión de seguimiento de Places, asegúrese de agregar también la biblioteca `places.aar` al proyecto.

## iOS

En las aplicaciones`application:didFinishLaunchingWithOptions`de iOS, regístrese `PlacesMonitor` y coloque con Mobile Core:

### Objective-C

```objectivec
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary*)launchOptions {
    [ACPCore configureWithAppId:@"yourAppId"];
    [ACPPlaces registerExtension];
    [ACPPlacesMonitor registerExtension];
    [ACPCore start:^{            
        // do other initialization required for the SDK
        [ACPPlacesMonitor start];
    }];

    return YES;
}
```

#### Swift

```swift
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
    ACPCore.configure(withAppId: "yourAppId")
    ACPPlaces.registerExtension()       
    ACPPlacesMonitor.registerExtension()
    ACPCore.start({
        // do other initialization required for the SDK
        ACPPlacesMonitor.start()
    })

    // Override point for customization after application launch.        
    return true
}
```

>[!IMPORTANT]
>
>La supervisión de lugares depende de la extensión Places. When manually installing the Places Monitor extension, ensure that you also add the `libACPPlaces_iOS.a` library to your project.


## Agregar permisos al manifiesto

### Android

**Java**

Para todas las versiones de Android, para declarar que la aplicación necesita permisos de ubicación, agregue un `<uses-permission>` elemento en el manifiesto de la aplicación, como elemento secundario del `<manifest>` elemento de nivel superior. Para las aplicaciones de Android que tienen como objetivo el nivel de API 29 y superior, para permitir que la aplicación tenga acceso a la ubicación en segundo plano, incluya el permiso ACCESS_BACKGROUND_LOCATION.

```java
<manifest xmlns:android="http://schemas.android.com/apk/res/android" package="com.adobe.placesapp">
  <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
    // Only for Android apps targeting API level 29 and above
  <uses-permission android:name="android.permission.ACCESS_BACKGROUND_LOCATION" />
  <application>        
    ...    
  </application>
</manifest>
```


## Habilitar las actualizaciones de ubicación en segundo plano {#enable-location-updates-background}

iOS admite la entrega de eventos de ubicación a aplicaciones que están suspendidas o que ya no se están ejecutando. Para recibir actualizaciones de ubicación en segundo plano para la extensión Monitor de lugares, configure la capacidad de actualizaciones de ubicación para la aplicación en `Xcode.background-location-updates`.

![uso del Monitor de lugares](/help/assets/using-the-places-monitor_1.png)

## Configuración de las claves plist

Se deben incluir las siguientes claves en el `Info.plist` archivo de la aplicación:

* `NSLocationWhenInUseUsageDescription` - el texto debe describir por qué la aplicación solicita acceso a la información de ubicación del usuario mientras se ejecuta en primer plano.
* `NSLocationAlwaysAndWhenInUseUsageDescription` - el texto debe describir por qué la aplicación solicita acceso a la información de ubicación del usuario en todo momento.

>[!TIP]
>
>Si la aplicación admite iOS 10 y versiones anteriores, también se requiere la `NSLocationAlwaysUsageDescription` clave.

![](/help/assets/using-the-places-monitor_2.png)
