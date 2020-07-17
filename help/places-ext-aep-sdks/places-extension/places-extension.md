---
title: Extensión Places
description: La extensión Lugares permite actuar en función de la ubicación de los usuarios.
translation-type: tm+mt
source-git-commit: a7dddb78e1e00a0bde01ea668334932759a9dae8
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 5%

---


# Extensión Places {#places-extension}

La extensión Lugares permite actuar en función de la ubicación de los usuarios. Esta extensión es la interfaz de las API de servicio de Consulta de lugares. Al escuchar eventos que contienen coordenadas GPS y eventos de región de geofencia, esta extensión distribuye nuevos eventos que son procesados por el motor de reglas. La extensión Places también recupera y entrega una lista del punto de interés más cercano para los datos de la aplicación que se recuperan de las API. Las regiones devueltas por las API se almacenan en caché y en persistencia, lo que permite un procesamiento sin conexión limitado.

## Instalación de la extensión Places en Inicio de Adobe Experience Platform

1. In Experience Platform Launch, click the **[!UICONTROL Extensions]** tab.
1. En la **[!UICONTROL Catalog]** ficha, ubique la **[!UICONTROL Places]** extensión y haga clic en **[!UICONTROL Install]**.
1. Seleccione las bibliotecas Lugares que desee utilizar en esta propiedad. Estas son las bibliotecas a las que se podrá acceder desde la aplicación.
1. Haga clic en **[!UICONTROL Save]**.

   Al hacer clic en **[!UICONTROL Save]**, el SDK de Experience Platform busca en los servicios de lugares puntos de interés en las bibliotecas seleccionadas. Los datos de puntos de interés no se incluyen en la descarga de la biblioteca al compilar la aplicación, pero se descarga un subconjunto de puntos de interés basado en la ubicación en el dispositivo del usuario final en tiempo de ejecución y se basa en las coordenadas de GPS del usuario.

1. Complete el proceso de publicación para actualizar la configuración del SDK.

   Para obtener más información sobre la publicación en Experience Platform Launch, consulte [Publicación](https://docs.adobe.com/content/help/es-ES/launch/using/reference/publish/overview.html).

### Configure the Places extension {#configure-places-extension}

![](//help/assets/places-extension.png)

## Añadir la extensión Places en la aplicación {#add-places-to-app}

Puede agregar la extensión Lugares a sus aplicaciones de Android e iOS. A continuación se muestran los pasos para agregar Lugares a la aplicación de iOS o Android. Las extensiones de lugares también están disponibles para las siguientes plataformas. Para agregar Lugares a la aplicación cuando se desarrolle con una de estas plataformas, consulte los vínculos correspondientes:

**[Complemento Cordova Places](https://github.com/adobe/cordova-acpplaces/blob/master/README.md)**

**[Complemento React Native Places](https://github.com/adobe/react-native-acpplaces/blob/master/README.md)**

**[Complemento Lutter Places](https://github.com/adobe/flutter-acpplaces_monitor)**

**[Complemento Xamarin Places](https://github.com/adobe/xamarin-acpcore)**


### Android

Para agregar la extensión Places a la aplicación mediante Java:

1. Añada la extensión Places al proyecto mediante el archivo de gradle de la aplicación.

   ```java
   implementation 'com.adobe.marketing.mobile:places:1.+'
   implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
   ```

1. Importe la extensión Places en la actividad principal de la aplicación.

   ```java
   import com.adobe.marketing.mobile.Places;
   ```


### iOS

Para agregar la extensión Places a la aplicación mediante Objective-C o Swift:

1. Añada las bibliotecas principales [de lugares y](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core) móviles en su proyecto. Deberá agregar los siguientes pods a su `Podfile`:

   ```objective-c
   pod 'ACPPlaces', '~> 1.0'
   pod 'ACPCore', '~> 2.0'    # minimum Core version for Places is 2.0.3
   ```

   Como alternativa, si no utiliza Cocoapods, puede incluir manualmente las bibliotecas Mobile Core y Places desde la página [de](https://github.com/Adobe-Marketing-Cloud/acp-sdks/releases/) versiones en Github.

1. Actualice sus copápodos:

   ```objective-c
   pod update
   ```

1. Abra Xcode y, en la clase AppDelegate, importe los encabezados Core y Places:

   **Objective-C**

   ```objective-c
   #import "ACPCore.h"
   #import "ACPPlaces.h"
   ```

   **Swift**

   ```swift
   import ACPCore
   import ACPPlaces
   ```

### Registrar la extensión Places con Mobile Core {#register-places-mobile-core}

Debe registrar la extensión Places con Mobile Core en Android e iOS.

#### Android

En el `OnCreate` método de la aplicación, registre las extensiones de lugares:

```java
public class PlacesTestApp extends Application {

    @Override
    public void onCreate() {
        super.onCreate();
        MobileCore.setApplication(this);

        try {
            Places.registerExtension();
            MobileCore.start(null);
        } catch (Exception e) {
            Log.e("PlacesTestApp", e.getMessage());
        }
    }
}
```

#### iOS

En el `application:didFinishLaunchingWithOptions:` método de la aplicación, registre la extensión Places con las demás llamadas de registro del SDK:

**Objective-C**

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    // make other sdk registration calls
    [ACPPlaces registerExtension];    
    return YES;
}
```

**Swift**

```swift
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
    // make other sdk registration calls
    ACPPlaces.registerExtension();
    return true;
}
```

### Modificación del tiempo de permanencia de Places {#places-ttl}

Los datos de ubicación pueden quedar obsoletos rápidamente, especialmente si el dispositivo no recibe actualizaciones de ubicación en segundo plano.

Controle el tiempo de vida útil de los datos de pertenencia a Places en el dispositivo estableciendo la configuración del `places.membershipttl` . El valor pasado representa el número de segundos que el estado Lugares seguirá siendo válido para el dispositivo.

#### Android

Dentro de la llamada de retorno de `MobileCore.start()` actualizar la configuración con los cambios necesarios antes de llamar `lifecycleStart`:

```java
public class PlacesTestApp extends Application {

    @Override
    public void onCreate() {
        super.onCreate();
        MobileCore.setApplication(this);

        try {
            Places.registerExtension();
            MobileCore.start(new AdobeCallback() {
                @Override
                public void call(Object o) {
                    // switch to your App ID from Launch
                    MobileCore.configureWithAppID("my-app-id");

                    final Map<String, Object> config = new HashMap<>();
                    config.put("places.membershipttl", 30);
                    MobileCore.updateConfiguration(config);

                    MobileCore.lifecycleStart(null);
                }
            });
        } catch (Exception e) {
            Log.e("PlacesTestApp", e.getMessage());
        }
    }
}
```

#### iOS

En la primera línea de la rellamada del `ACPCore`método `start:` de `updateConfiguration:`

**Objective-C**

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    // make other sdk registration calls

    const UIApplicationState appState = application.applicationState;
    [ACPCore start:^{
        [ACPCore updateConfiguration:@{@"places.membershipttl":@(30)}];

        if (appState != UIApplicationStateBackground) {
            [ACPCore lifecycleStart:nil];            
        }
    }];

    return YES;
}
```

**Swift**

```swift
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
    // make other sdk registration calls

    let appState = application.applicationState;            
    ACPCore.start {
        ACPCore.updateConfiguration(["places.membershipttl" : 30])

        if appState != .background {
            ACPCore.lifecycleStart(nil)
        }    
    }

    return true;
}
```

## Claves de configuración

Para actualizar la configuración del SDK mediante programación en tiempo de ejecución, utilice la siguiente información para cambiar los valores de configuración de la extensión Places. Para obtener más información, consulte Referencia [de API de](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/configuration/configuration-api-reference)configuración.

| Clave | Requerido | Descripción |
| :--- | :--- | :--- |
| `places.libraries` | Sí | Bibliotecas de extensiones Places para la aplicación móvil. Especifica el ID de biblioteca y el nombre de la biblioteca que admite la aplicación móvil. |
| `places.endpoint` | Sí | Extremo predeterminado del servicio de Consulta de lugares, que se utiliza para obtener información sobre bibliotecas y puntos de interés. |
| `places.membershipttl` | No | Valor predeterminado de 3600 (segundos en una hora). Indica cuánto tiempo, en segundos, seguirá siendo válida la información de pertenencia de Places para el dispositivo. |
