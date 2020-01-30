---
title: Probar y validar el servicio de lugares
description: Esta sección proporciona información sobre cómo probar y validar el servicio de lugares.
translation-type: tm+mt
source-git-commit: 5a21e734c0ef56c815389a9f08b445bedaae557a

---


# Recomendaciones para probar el servicio de lugares {#test-validate-loc-svc}

Muchos clientes y organizaciones definirán puntos de interés en todo el mundo, por lo que es importante tener una manera de simular y probar cómo interactúa el servicio de lugares con su aplicación. Esta información le ayuda a comprender cómo probar y validar las entradas y salidas del servicio de lugares que se activan correctamente en función de los puntos de interés definidos y la ubicación actual del usuario.

Dado que las variables ambientales pueden ser un factor en la precisión y la señal de ubicación, recomendamos que primero establezca los resultados de línea de base trabajando localmente con herramientas de desarrollador y entradas de ubicación simuladas. El objetivo es validar que todos los eventos de ubicación funcionen correctamente. Una vez validados correctamente los eventos de ubicación, se pueden probar las integraciones de soluciones (por ejemplo, Analytics, Target y Campaign). Para ayudar a sus actividades de prueba, debe configurar los Webhooks Slack con un postback y cargar archivos GPX en su entorno de desarrollo individual.

>[!IMPORTANT]
>
>Este plan supone que los puntos de interés se han creado en la interfaz de usuario [del servicio](https://places.adobe.com) Lugares y que las últimas versiones de la extensión Lugares y de la extensión Monitor de lugares están instaladas y configuradas correctamente. Para obtener más información, consulte Extensión [de](/help/places-ext-aep-sdks/places-extension/places-extension.md) lugares y extensión [de monitor de](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)lugares.

| Paso | Descripción | Resultado esperado |
|--- |--- |--- |
| 1 | Confirme que se han introducido las claves de manifiesto correctas para Android a fin de conceder acceso a la ubicación de seguimiento. Para obtener más información, consulte [Adición de permisos al manifiesto](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.html#add-permissions-to-the-manifest). | Confirmado |
| 1a | Confirme que las actualizaciones de ubicación están configuradas en iOS. Asegúrese también de que tiene las claves plist adecuadas configuradas en iOS para solicitar permiso de usuario para rastrear la ubicación. Para obtener más información, consulte [Habilitar actualizaciones de ubicación en segundo plano.](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.html#enable-location-updates-background) | Confirmado |
| 2 | Confirme qué modo de supervisión está establecido para iOS. El modo continuo permite una mayor precisión y persistencia, pero también reduce considerablemente la duración de la batería. Para obtener más información, consulte Modo [de supervisión (solo iOS).](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/places-monitor-api-reference.html#monitoring-mode-ios-only) | Cambios significativos o continuos |
| 3 | Si utiliza más de una biblioteca de puntos de interés, confirme que se han seleccionado las bibliotecas correspondientes en la extensión Lugares para el lanzamiento de la plataforma de experiencia. | Confirmado |
| 4 | Confirme que las versiones más recientes de las extensiones Mobile Core y Places/Places Monitor se han incluido con la aplicación mediante Gradle o CocoaPods. | Confirmado: para obtener más información sobre actualizaciones recientes, consulte las notas de la [versión.](/help/release-notes.md) |
| 5 | Confirme que los entornos correctos están configurados para pruebas. La ID del entorno de Launch debe coincidir con el entorno de desarrollo de Launch. | Confirmado |
| 6 | Cree archivos GPX para cada punto de interés que desee probar. Los archivos GPX se pueden utilizar en el entorno de desarrollo local para simular una entrada de ubicación. Para obtener información sobre la creación y el uso de archivos GPX, consulte lo siguiente: Archivos <br>[GPX para el simulador de iOS [cerrados]](https://stackoverflow.com/questions/17292783/gpx-files-for-ios-simulator)<br>[https://mapstogpx.com/mobiledev.](https://mapstogpx.com/mobiledev.php)<br>[phpPRUEBAS DE UBICACIÓN EN APLICACIONES MÓVILES](https://qacumtester.wordpress.com/2014/02/27/location-testing-in-mobile-apps/) | Los archivos GPX se crean y se cargan en el proyecto de la aplicación. |
| 7 | Sin hacer nada más, debería poder iniciar la aplicación desde Android Studio o XCode y ver la alerta adecuada para solicitar acceso para la ubicación de seguimiento. Haga clic en el permiso *Permitir* siempre.<br><br>Le recomendamos que utilice un dispositivo real conectado al equipo en lugar de usar el simulador de dispositivos. | El mensaje de solicitud de ubicación debe mostrarse en la aplicación cargada mediante IDE |
| 8 | Una vez aceptado el permiso de ubicación. El SDK de Places recuperará la ubicación actual del dispositivo y la extensión del monitor de lugares comenzará a supervisar los 20 puntos de interés más cercanos desde la ubicación actual | Consulte el ejemplo de registro debajo de la tabla. |
| 9 | Cambiar entre diferentes ubicaciones en XCode o estudio de Android debería producir eventos de entrada para puntos de interés específicos. Los siguientes registros se esperan al entrar en un punto de interés. | Consulte el ejemplo de registro debajo de la tabla. |
| 10 | Después de ver que el Monitor de lugares encuentra puntos de interés cercanos, debe realizar la prueba enviando pings de ubicación. En Iniciar, cree una nueva regla que utilice la extensión Lugares para activarla en función de una entrada de reja geográfica. A continuación, cree una nueva acción utilizando Mobile Core para enviar un postback. La creación de una aplicación de Slack Weblink ayuda a ver las entradas y salidas de la ubicación. Para obtener más información sobre la creación de una aplicación de Slack Webhooks, consulte [Envío de mensajes mediante Webhooks entrantes.](https://api.slack.com/messaging/webhooks) |  |
| 10a | En Launch, asegúrese de que ha agregado elementos de datos para la extensión Places, incluidos los siguientes: <br>Nombre de punto de interés actual<br>Nombre de punto de interés actual<br>latÚltimo punto de interés actual<br>largo Último<br>nombre especificado Último<br>último<br>último<br>nombre de salida Última salida<br>última salida última<br>marca de tiempo de salida |  |
| 10b | Crear una nueva regla con un Evento = Lugares → Introducir punto de interés |  |
| 10c | Crear una acción = Núcleo móvil → Postback |  |
| 10d | Utilice la URL de Weblink para su aplicación de Slack, por ejemplo, https://hooks.slack.com/services/TKN5FKS68/BNFP7SVD..... |  |
| 10e | El cuerpo de correos sería similar a: `{text: User is in POI -  {%%Last Entered POI Name%%} in {%%Last Entered POI City%%} additional information: Radius:{%%Last Entered POI Radius%%} Timestamp: {%%timestamp%%}}`. <br>Asegúrese de utilizar los elementos de datos específicos que ha creado aquí. |  |
| 10f | Asegúrese de publicar todos los cambios de reglas y elementos de datos nuevos en Launch. (Debe seleccionar una biblioteca de desarrollo que funcione en la parte superior derecha de la interfaz de Launch). |  |
| 11 | Inicie y vuelva a probar la aplicación cambiando entre las ubicaciones de GPX en el IDE de desarrollador. | Ahora debería ver las notificaciones de demora que muestran entradas para cada punto de interés a medida que selecciona distintas ubicaciones en su entorno de desarrollo. |
|  | **RESUMEN RÁPIDO**<br> POINTAtodas estas pruebas pueden realizarse localmente sin tener que ir a una ubicación de puntos de interés específica. La prueba de validación ayuda a garantizar que la aplicación está correctamente configurada y que ha recibido los permisos correctos para la ubicación. <br><br>Esta validación también le ofrece la confianza de que los puntos de interés definidos funcionan correctamente con la extensión Monitor de lugares.  Después de este paso, empezaremos a probar los mensajes en Campaign para ver si los mensajes adecuados aparecen en función de las entradas y salidas de puntos de interés. |  |
|  | **Prueba de la mensajería en la aplicación estándar de Adobe Campaign con el servicio de lugares.** |  |
| 12 | En el tablero de campañas principal, configure un nuevo mensaje en la aplicación (tipo = difusión) |  |
| 12a | En los activadores, seleccione **Colocaciones tipo de evento - Entrada como activador**. |  |
| 12b | Seleccione **[UICONTROL Coloca los metadatos]** personalizados como un filtro adicional; use el tipo de punto de interés = último punto de interés especificado.<br>Utilizamos **[!UICONTROL Last Entered]** como tipo de punto de interés porque en la mayoría de los casos **[!UICONTROL Last Entered]** será el mismo que **[!UICONTROL Current POI]**. <br><br>**[!UICONTROL Current POI]** solo debe utilizarse en casos en los que haya rejas geográficas de puntos de interés superpuestas. En este caso, estos puntos de interés deben clasificarse y, a continuación, el **[!UICONTROL Current POI]** mostrará el punto de interés de mayor clasificación de las 2 o 3 rejas geográficas en las que un usuario podría estar actualmente. |  |
| 12c | Seleccione una clave de metadatos personalizada que le ayudará a reducir los puntos de interés que recibirán un mensaje. |  |
| 12d | Para la frecuencia y la duración, mantenga sólo uno o dos días, de modo que si no le gustan los criterios, puede caducar el activador en un período de tiempo más corto. |  |
| 12e | Para pulsaciones Siempre/Una o Hasta, seleccione *SIEMPRE* para que pueda realizar pruebas en varias ubicaciones. | SIEMPRE se muestra un mensaje en la aplicación cuando simula un cambio de ubicación que cumple los criterios de metadatos correspondientes. |
| 12f | Para la visualización, seleccione una opción que no sea Notificación local. Esto facilita la visualización al realizar pruebas con la aplicación en primer plano). |  |
| 12g | Prepare/confirme e implemente el mensaje en la aplicación. |  |
| 13 | En el entorno de desarrollo, para asegurarse de que se descargan nuevas reglas de campaña, cierre la aplicación y vuelva a iniciarla. | No olvide que las aplicaciones deben volver a iniciarse completamente para que el nuevo archivo de reglas de campaña se descargue en el dispositivo. |
| 14 | En la aplicación de desarrollo, cambie de ubicación utilizando los archivos GPX creados anteriormente. | Debería ver el mensaje en la aplicación en función de los criterios anteriores establecidos. |
| 15 | Para la siguiente prueba, básicamente copiaremos los mismos pasos que antes, pero esta vez probaremos NOTIFICACIÓN LOCAL. | El resultado esperado es que las notificaciones locales se muestran cada vez que se cumplen los criterios coincidentes. |
| 16 | Configure un nuevo mensaje en la aplicación (tipo = difusión). |  |
| 16a | En activadores, seleccione **[!UICONTROL Places event type]**-**[!UICONTROL Entry as the trigger]**. |  |
| 16b | Seleccione los metadatos personalizados de lugares como filtro adicional; use **[!UICONTROL POI type]**=**[!UICONTROL Last Entered POI]**. |  |
| 16c | Seleccione una clave de metadatos personalizada que le ayudará a reducir los puntos de interés que recibirán un mensaje. |  |
| 16d | Para la frecuencia y la duración, mantenga solo uno o dos días, de modo que si no le gustan los criterios, puede caducar el activador en un período de tiempo más corto. |  |
| 16e | Para pulsaciones Siempre/Una o Hasta, **[!UICONTROL ALWAYS]**. |  |
| 16f | Para el tipo de visualización, seleccione **[!UICONTROL Local Notification]**. |  |
| 16g | Prepare/confirme e implemente el mensaje en la aplicación. |  |
| 17 | En el entorno de desarrollo, conecte el dispositivo y pulse **[!UICONTROL Play]**&#x200B;en la compilación. Una vez que haya establecido que la ubicación funciona, ponga en segundo plano la aplicación y continúe cambiando de ubicación en Xcode o Android Studio. Aún debe ver las lecturas de la consola que indican el cambio de ubicación y también debería ver notificaciones locales en función de los criterios establecidos en el activador. (Puede haber un retraso de 1 a 2 segundos). | El resultado esperado es que se muestran las notificaciones locales cada vez que se cumplen los criterios coincidentes. |
|  | **PUNTO** DE RESUMEN <br>En esta etapa, deberíamos ver entradas de puntos de interés en nuestro entorno local. También deberíamos ver mensajes de Campaign basados en el trabajo de POI. Si hay errores, compruebe si no se ha producido una notificación de demora. Si no hay ningún mensaje de demora, compruebe la consola de la aplicación, ya que es posible que no se haya grabado una nueva entrada de ubicación. Si los resultados son satisfactorios, podemos estar bastante seguros de que la aplicación está funcionando correctamente y de que el servicio de mensajería de Places y Campaign también está funcionando correctamente. |  |
|  | **PRUEBAS** EN EL SITIO <br>No hay mucho que cambiar al realizar pruebas en el lugar. Mantener el postback flojo activo debería ayudar a comprender si el dispositivo está obteniendo una entrada y salida para la ubicación. |  |
| 18 | Lleve a cabo pruebas con dispositivos que empiecen por Wi-Fi y dispositivos móviles deshabilitados y, a continuación, active una vez en la región de POI. | Si se produce un error, tenga en cuenta si está recibiendo una entrada y una notificación de la valla geográfica en Slack. ¿Cuál es la marca de tiempo de la notificación Slack? |
| 19 | Lleve a cabo la prueba solo con la conexión móvil habilitada y con la conexión inalámbrica desactivada. |  |
| 20 | Realice la prueba con el dispositivo móvil y Wi-Fi activado. |  |
|  | **PUNTO** DE RESUMEN Las pruebas <br>in situ deben coincidir estrechamente con las pruebas de desarrollo. Tenga en cuenta que existen algunos factores ambientales que pueden entrar en juego al determinar la ubicación del usuario, como la duración del tiempo empleado en una cerca geográfica de puntos de interés, la disponibilidad de señales celulares y la fuerza de los puntos de acceso Wi-Fi cercanos. |  |

## Muestras de registro

**** Paso 8: Registros esperados de iOS y Android durante una actualización de ubicación

**iOS**

```
[AdobeExperienceSDK DEBUG <com.adobe.placesMonitor>]: Authorization status changed: Always
[AdobeExperienceSDK DEBUG <Places>]: Requesting 20 nearby POIs for device location (<lat>, <longitude>)
[AdobeExperienceSDK DEBUG <Places>]: Response from Places Query Service contained <n> nearby POIs
[AdobeExperienceSDK DEBUG <com.adobe.placesMonitor>]: Received a new list of POIs from Places: (
<ACPPlacePoi: 0x600002b75a40> Name: <poi name>; ID:<poi id>; Center: (<lat>, <long>); Radius: <radius>
..
..)   
```

**Android**

```
PlacesMonitor - All location settings are satisfied to monitor location
PlacesMonitor - PlacesMonitorInternal : New location obtained: <latitude> <longitude> Attempting to get the near by pois
PlacesExtension - Dispatching nearby places event with n POIs
PlacesMonitor - Attempting to Monitor POI with id <poi id> name <poi name> latitude <lat> longitude <longitude>
PlacesMonitor - Attempting to Monitor POI with id <poi id> name <poi name> latitude <lat> longitude <longitude>
PlacesMonitor - Attempting to Monitor POI with id <poi id> name <poi name> latitude <lat> longitude <longitude>
...
...
PlacesMonitor - Successfully added n fences for monitoring
```

**** Paso 9: Registros esperados de iOS y Android durante un evento

**iOS**

```
[AdobeExperienceSDK TRACE <Places>]: Dispatching Places region entry event for place ID <poiId>
```

**Android**

```
PlacesExtension -  Dispatching Places Region Event for <poi name> with eventType entry
```
