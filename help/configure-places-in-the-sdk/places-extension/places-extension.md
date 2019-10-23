---
title: Extensión de lugares
seo-title: Extensión de lugares
description: La extensión Lugares permite actuar en función de la ubicación de los usuarios.
seo-description: La extensión Lugares permite actuar en función de la ubicación de los usuarios.
translation-type: tm+mt
source-git-commit: 1fb87285d2ccd581ee59ab1b1efbec4af04a0fab

---


# Extensión de lugares {#places-extension}

La extensión Lugares permite actuar en función de la ubicación de los usuarios. Esta extensión es la interfaz de las API de servicio de consulta de lugares. Al escuchar eventos que contienen coordenadas GPS y eventos de región de geofence, esta extensión distribuye nuevos eventos que son procesados por el motor de reglas. La extensión Places también recupera y entrega una lista del punto de interés más cercano para los datos de la aplicación que se recuperan de las API. Las regiones devueltas por las API se almacenan en caché y en persistencia, lo que permite un procesamiento sin conexión limitado.

## Instalación de la extensión Places en Adobe Experience Platform Launch

1. En Inicio de plataforma de experiencia, haga clic en la **[!UICONTROL Extensions]** ficha .
2. En la **[!UICONTROL Catalog]** ficha, busque la **[!UICONTROL Adobe Places]** extensión y haga clic en **[!UICONTROL Install]**.
3. Seleccione las bibliotecas Lugares que desee utilizar en esta propiedad. Estas son las bibliotecas a las que se podrá acceder desde la aplicación.
4. Haga clic en **[!UICONTROL Save]**.

   Al hacer clic en **[!UICONTROL Save]**, el SDK de la plataforma de experiencia busca en los servicios de lugares puntos de interés en las bibliotecas seleccionadas. Los datos de puntos de interés no se incluyen en la descarga de la biblioteca al compilar la aplicación, pero se descarga un subconjunto de puntos de interés basado en la ubicación en el dispositivo del usuario final en tiempo de ejecución y se basa en las coordenadas GPS del usuario.

5. Complete el proceso de publicación para actualizar la configuración del SDK.

   Para obtener más información sobre la publicación en el lanzamiento de la plataforma de experiencia, consulte [Publicación](https://docs.adobelaunch.com/launch-reference/publishing).

### Configurar la extensión Places {#configure-places-extension}

![](//help/assets/places-extension.png)

## Agregar la extensión Places a la aplicación {#add-places-to-app}

Puede agregar la extensión Lugares a sus aplicaciones de Android e iOS.

### Android

Para agregar la extensión Places a la aplicación mediante Java:

1. Agregue la extensión Lugares al proyecto mediante el archivo de gradle de la aplicación.

   ```java
   implementation 'com.adobe.marketing.mobile:places:1.+'
   implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
   ```

2. Importe la extensión Places en la actividad principal de la aplicación.

   ```java
   import com.adobe.marketing.mobile.Places;
   ```


### iOS

Para agregar la extensión Places a la aplicación mediante Objective-C o Swift:

1. Añada las bibliotecas principales [de lugares y](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core) móviles al proyecto. Deberá agregar los siguientes pods a su `Podfile`:

   ```objective-c
   pod 'ACPPlaces', '~> 1.0'
   pod 'ACPCore', '~> 2.0'    # minimum Core version for Places is 2.0.3
   ```

   Como alternativa, si no utiliza Cocoapods, puede incluir manualmente las bibliotecas Mobile Core y Places de la página [de](https://github.com/Adobe-Marketing-Cloud/acp-sdks/releases/) versiones en Github.

2. Actualice sus copápodos:

   ```objective-c
   pod update
   ```

3. Abra Xcode y, en la clase AppDelegate, importe los encabezados Core y Places:

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

### Registrar lugares con Mobile Core {#register-places-mobile-core}

Debe registrar los sitios con Mobile Core en Android e iOS.

#### Android

En el `OnCreate` método de la aplicación, registre las extensiones de los servicios de ubicación:

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

## Claves de configuración

Para actualizar la configuración del SDK mediante programación durante la ejecución, utilice la siguiente información para cambiar los valores de configuración de Places. Para obtener más información, consulte Referencia [de API de](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/configuration/configuration-api-reference)configuración.

| Clave | Requerido | Descripción |
| :--- | :--- | :--- |
| `places.libraries` | Sí | Coloca bibliotecas para la aplicación móvil. Especifica el ID de biblioteca y el nombre de la biblioteca que admite la aplicación móvil. |
| `places.endpoint` | Sí | Extremo predeterminado del servicio de consulta de ubicación de la plataforma de experiencias, que se utiliza para obtener información sobre bibliotecas y puntos de interés. |
