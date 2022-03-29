---
title: Extensión Places
description: La extensión Places permite actuar en función de la ubicación de los usuarios.
exl-id: 09c02753-09b3-4e07-82b2-b6c72c4e0e42
source-git-commit: 795808b38851d5afcedc03f58e9a1d6342830934
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Extensión Places {#places-extension}

La extensión Places permite actuar en función de la ubicación de los usuarios. Esta extensión es la interfaz de las API del servicio de consulta de Places. Al escuchar eventos que contienen coordenadas GPS y eventos de región de geovalla, esta extensión distribuye nuevos eventos que son procesados por el motor de reglas. La extensión Places también recupera y envía una lista del punto de interés más cercano para los datos de la aplicación que se recuperan de las API. Las regiones que devuelven las API se almacenan en caché y en persistencia, lo que permite un procesamiento sin conexión limitado.

## Instalación de la extensión Places en Adobe Experience Platform Launch

1. En el Experience Platform Launch, haga clic en el botón **[!UICONTROL Extensiones]** pestaña .
1. En el **[!UICONTROL Catálogo]** , busque **[!UICONTROL Lugares]** y haga clic en **[!UICONTROL Instalar]**.
1. Seleccione las bibliotecas de Places que desee utilizar en esta propiedad. Estas son las bibliotecas a las que se puede acceder desde la aplicación.
1. Haga clic en **[!UICONTROL Guardar]**.

   Al hacer clic en **[!UICONTROL Guardar]**, el SDK de Experience Platform busca en Servicios de Places puntos de interés en las bibliotecas seleccionadas. Los datos de puntos de interés no se incluyen en la descarga de la biblioteca al crear la aplicación, pero se descarga un subconjunto de puntos de interés basado en la ubicación al dispositivo del usuario final durante la ejecución y se basa en las coordenadas GPS del usuario.

1. Complete el proceso de publicación para actualizar la configuración del SDK.

   Para obtener más información sobre la publicación en Experience Platform Launch, consulte [Publicación](https://docs.adobe.com/content/help/es-ES/launch/using/reference/publish/overview.html).

### Configurar la extensión Places {#configure-places-extension}

![](/help/assets/places-extension.png)

## Añada la extensión Places a la aplicación {#add-places-to-app}

Puede añadir la extensión Places a sus aplicaciones de Android y iOS. A continuación se pueden ver los pasos para agregar Places a la aplicación de iOS o Android. Las extensiones Places también están disponibles para las plataformas siguientes. Para añadir Places a la aplicación cuando se desarrolle con una de estas plataformas, consulte los vínculos que le acompañan:

**[Complemento Cordova Places](https://github.com/adobe/cordova-acpplaces/blob/master/README.md)**

**[Complemento React Native Places](https://github.com/adobe/react-native-acpplaces/blob/master/README.md)**

**[Complemento Flutter Places](https://github.com/adobe/flutter-acpplaces_monitor)**

**[Complemento Xamarin Places](https://github.com/adobe/xamarin-acpcore)**


### Android

Para añadir la extensión Places a la aplicación mediante Java:

1. Agregue la extensión Places al proyecto mediante el archivo de gradle de la aplicación.

   ```java
   implementation 'com.adobe.marketing.mobile:places:1.+'
   implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
   ```

1. Importe la extensión Places en la actividad principal de la aplicación.

   ```java
   import com.adobe.marketing.mobile.Places;
   ```


### iOS

Para añadir la extensión Places a la aplicación mediante Objective-C o Swift:

1. Agregue los Places y [Mobile Core](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core) bibliotecas en el proyecto. Tendrá que agregar los siguientes pods a su `Podfile`:

   ```objective-c
   pod 'ACPPlaces', '~> 1.0'
   pod 'ACPCore', '~> 2.0'    # minimum Core version for Places is 2.0.3
   ```

   Alternativamente, si no utiliza Cocoapods, puede incluir manualmente las bibliotecas Mobile Core y Places de nuestra [página versiones](https://github.com/Adobe-Marketing-Cloud/acp-sdks/releases/) en Github.

1. Actualice sus Cocoapods:

   ```objective-c
   pod update
   ```

1. Abra Xcode y, en la clase AppDelegate , importe los encabezados Core y Places :

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

### Registre la extensión Places con Mobile Core {#register-places-mobile-core}

Debe registrar la extensión Places con Mobile Core en Android y iOS.

#### Android

En la aplicación `OnCreate` registrar las extensiones de Places :

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

En la aplicación `application:didFinishLaunchingWithOptions:` registrar la extensión Places con sus otras llamadas de registro de SDK:

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

Los datos de ubicación pueden quedar obsoletos rápidamente, especialmente si el dispositivo no está recibiendo actualizaciones de ubicación en segundo plano.

Controle el tiempo de vida de los datos de pertenencia de Places en el dispositivo configurando la variable `places.membershipttl` configuración. El valor pasado representa el número de segundos que el estado Places seguirá siendo válido para el dispositivo.

#### Android

Dentro de la rellamada de `MobileCore.start()` actualice la configuración con los cambios necesarios antes de llamar a `lifecycleStart`:

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

En la primera línea de la rellamada de `ACPCore`&#39;s `start:` método, llamada `updateConfiguration:`

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

Para actualizar la configuración del SDK de forma programada durante la ejecución, utilice la siguiente información para cambiar los valores de configuración de la extensión Places. Para obtener más información, consulte [Referencia de API de configuración](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/configuration/configuration-api-reference).

| Clave | Requerido | Descripción |
| :--- | :--- | :--- |
| `places.libraries` | Sí | Bibliotecas de extensión Places para la aplicación móvil. Especifica el ID de biblioteca y el nombre de la biblioteca que admite la aplicación móvil. |
| `places.endpoint` | Sí | El extremo predeterminado del servicio de consulta de Places, que se utiliza para obtener información sobre bibliotecas y puntos de interés. |
| `places.membershipttl` | No | Valor predeterminado de 3600 (segundos en una hora). Indica cuánto tiempo, en segundos, seguirá siendo válida la información de pertenencia de Places para el dispositivo. |
