---
title: Probar y validar el servicio Places
description: Esta sección proporciona información sobre cómo probar y validar el servicio de Places.
exl-id: 8dad6619-566b-4aea-b29c-a89192a66441
source-git-commit: 2b5c53887c9ed0f2a672c377121a39537ee58f01
workflow-type: tm+mt
source-wordcount: '1731'
ht-degree: 2%

---

# Recommendations para probar el servicio de Places {#test-validate-loc-svc}

Muchos clientes y organizaciones definirán puntos de interés en todo el mundo, por lo que es importante disponer de una forma de simular y probar cómo el servicio Places interactúa con su aplicación. Esta información le ayuda a comprender cómo probar y validar las entradas y salidas del servicio de Places que se activan correctamente en función de los puntos de interés definidos y la ubicación actual de un usuario.

Dado que las variables ambientales pueden ser un factor en la señal y precisión de ubicación, recomendamos que primero establezca los resultados de línea de base trabajando localmente con herramientas para desarrolladores y entradas de ubicación simuladas. El objetivo es validar que todos los eventos de ubicación funcionan correctamente. Una vez validados los eventos de ubicación correctamente, se pueden probar las integraciones de soluciones (por ejemplo, Analytics, Target y Campaign). Para ayudar a sus actividades de prueba, debe configurar Webhooks Slack con un postback y cargar archivos GPX en su entorno de desarrollo individual.

>[!IMPORTANT]
>
>Este plan supone que los puntos de interés se han creado en la variable [Interfaz de usuario del servicio de Places](https://places.adobe.com) y las últimas versiones de la extensión Places están instaladas y configuradas correctamente. Si se realiza una monitorización activa de la región, también se supone que se implementa una solución de monitorización de la región. Para obtener más información, consulte [Extensión Places](/help/places-ext-aep-sdks/places-extension/places-extension.md), [Documentación de CoreLocation](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) para iOS, o [Documentación de la ubicación de Android](https://developer.android.com/training/location/geofencing).

| Paso | Descripción | Resultado esperado |
|--- |--- |--- |
| 1 | Confirme que se han introducido las claves de manifiesto correctas para que Android conceda acceso a la ubicación de seguimiento. | Confirmado |
| 1a | Confirme que las actualizaciones de ubicación están configuradas en iOS. Asegúrese también de que ha configurado las claves plist adecuadas en iOS para solicitar permiso de usuario para rastrear la ubicación. | Confirmado |
| 2 | Confirme qué modo de monitorización está configurado para iOS. El modo continuo permite una buena precisión y persistencia, pero también reduce considerablemente la duración de la batería. | Cambios importantes o continuos |
| 3 | Si utiliza más de una biblioteca de puntos de interés, confirme que se han seleccionado las bibliotecas adecuadas en el Experience Platform Launch de la extensión Places . | Confirmado |
| 4 | Confirme que las versiones más recientes de las extensiones Mobile Core y Places se hayan incluido con la aplicación a través de Gradle o CocoaPods. | Confirmado : para obtener más información sobre las actualizaciones recientes, consulte la [notas de la versión.](/help/release-notes.md) |
| 5 | Confirme que los entornos correctos están configurados para realizar pruebas. El ID de entorno de Launch debe coincidir con el entorno de desarrollo de Launch. | Confirmado |
| 6 | Cree archivos GPX para cada punto de interés que desee probar. Los archivos GPX se pueden utilizar en el entorno de desarrollo local para simular una entrada de ubicación. Para obtener información sobre la creación y el uso de archivos GPX, consulte lo siguiente: <br>[Archivos GPX para el simulador de iOS [cerrado]](https://stackoverflow.com/questions/17292783/gpx-files-for-ios-simulator)<br>[https://mapstogpx.com/mobiledev.php](https://mapstogpx.com/mobiledev.php)<br>[PRUEBA DE UBICACIÓN EN APLICACIONES MÓVILES](https://qacumtester.wordpress.com/2014/02/27/location-testing-in-mobile-apps/) | Los archivos GPX se crean y cargan en el proyecto de la aplicación. |
| 7 | Sin hacer nada más, debería poder iniciar la aplicación desde Android Studio o XCode y ver la alerta adecuada para solicitar acceso a la ubicación de seguimiento. Haga clic en el *Permitir siempre* permiso.<br><br>Se recomienda utilizar un dispositivo real conectado al equipo en lugar de usar el simulador de dispositivos. | El mensaje de solicitud de ubicación debe mostrarse en la aplicación cargada a través de IDE |
| 8 | Una vez aceptado el permiso de ubicación. El SDK de Places recuperará la ubicación actual del dispositivo y el código de monitorización de región debe empezar a monitorizar los 20 puntos de interés más cercanos desde la ubicación actual | Consulte el ejemplo de registro en la tabla . |
| 9 | Cambiar entre diferentes ubicaciones en XCode o Android Studio debe producir eventos de entrada para puntos de interés específicos. Se esperan los siguientes registros al entrar en un punto de interés. | Consulte el ejemplo de registro en la tabla . |
| 10 | Una vez que el monitor de región encuentre puntos de interés cercanos, debe probar enviando pings de ubicación. En Launch, cree una regla nueva que utilice la extensión Places para almacenar en déclencheur en función de una entrada de geovalla. A continuación, cree una nueva acción utilizando Mobile Core para enviar un Postback. La creación de una aplicación de Weblock para Slack le ayuda a ver las entradas y salidas de la ubicación. Para obtener más información sobre la creación de una aplicación de Weblock de Slack, consulte [Envío de mensajes mediante Webhooks entrantes.](https://api.slack.com/messaging/webhooks) |  |
| 10 bis | En Launch, asegúrese de que ha agregado elementos de datos para la extensión Places, que incluye lo siguiente: <br>Nombre de punto de interés actual<br>Punto de interés actual<br>Punto de interés actual largo<br>Nombre introducido por última vez<br>Última entrada<br>Última entrada larga<br>Apellido de salida<br>Última salida<br>Última salida larga<br>Marca de tiempo |  |
| 10b | Crear una regla nueva con un Evento = Places → Introducir punto de interés |  |
| 10c | Crear una acción = Mobile Core → Postback |  |
| 10d | Utilice la URL de Weblock para su aplicación de Slack, por ejemplo, https://hooks.slack.com/services/TKN5FKS68/BNFP7SVD... |  |
| 10e | El cuerpo del correo sería similar a: `{text: User is in POI -  {%%Last Entered POI Name%%} in {%%Last Entered POI City%%} additional information: Radius:{%%Last Entered POI Radius%%} Timestamp: {%%timestamp%%}}`. <br>Asegúrese de utilizar los elementos de datos específicos que ha creado aquí. |  |
| 10f | Asegúrese de publicar todos los nuevos elementos de datos y cambios de reglas en Launch. (Debe seleccionar una biblioteca de desarrollo en funcionamiento en la parte superior derecha de la interfaz de Launch). |  |
| 11 | Inicie y vuelva a probar la aplicación cambiando entre las ubicaciones GPX del IDE para desarrolladores. | Ahora debería ver notificaciones del Slack que muestran entradas para cada punto de interés a medida que selecciona diferentes ubicaciones en su entorno de desarrollo. |
|  | **PUNTO DE RESUMEN RÁPIDO**<br> Todas estas pruebas se pueden realizar localmente sin tener que ir a una ubicación de puntos de interés específica. Las pruebas de validación ayudan a garantizar que la aplicación esté correctamente configurada y que haya recibido los permisos correctos para la ubicación. <br><br>Esta validación también le ofrece la confianza de que los puntos de interés definidos funcionan correctamente con la implementación de supervisión de la región.  Después de este paso, empezaremos a probar la mensajería en Campaign para ver si los mensajes adecuados aparecen en función de las entradas y salidas de puntos de interés. |  |
|  | **Prueba de la mensajería en la aplicación de Adobe Campaign Standard con el servicio Places.** |  |
| 12 | En el panel principal de Campaign, configure un nuevo mensaje en la aplicación (tipo = difusión) |  |
| 12 bis | En déclencheur, seleccione **Tipo de evento Places : entrada como déclencheur**. |  |
| 12b | Select **[!UICONTROL Metadatos personalizados de Places]** como filtro adicional: use POI type = Último punto de interés especificado.<br>Usamos **[!UICONTROL Última entrada]** como tipo de punto de interés porque, en la mayoría de los casos, **[!UICONTROL Última entrada]** será igual que **[!UICONTROL Punto de interés actual]**. <br><br>**[!UICONTROL Punto de interés actual ]**solo debe usarse en casos en los que haya geovallas de puntos de interés superpuestas. En este caso, estos puntos de interés deben clasificarse y luego**[!UICONTROL  Punto de interés actual ]**mostrará el punto de interés de mayor clasificación de las dos o tres geovallas en las que podría estar un usuario actualmente. |  |
| 12c | Seleccione una clave de metadatos personalizada que le ayude a reducir los puntos de interés que recibirán un mensaje. |  |
| 12d | Para la frecuencia y la duración, conserve hasta uno o dos días, de modo que si no le gustan los criterios, puede caducar el déclencheur en un período de tiempo más breve. |  |
| 12e | Para pulsaciones Siempre/Una o Hasta, seleccione *SIEMPRE* para que pueda realizar pruebas en varias ubicaciones. | Se muestra SIEMPRE un mensaje en la aplicación cuando simula un cambio de ubicación que cumple los criterios de metadatos adecuados. |
| 12f | Para la visualización, seleccione una opción que no sea Notificación local. Esto facilita la visualización al realizar pruebas con la aplicación en primer plano). |  |
| 12g  | Prepare/confirme e implemente el mensaje en la aplicación. |  |
| 13 | En el entorno de desarrollo, para asegurarse de que se descargan nuevas reglas de campaña, cierre y vuelva a iniciar la aplicación. | No olvide que las aplicaciones deben volver a iniciarse completamente para que el nuevo archivo de reglas de Campaign se descargue en el dispositivo. |
| 14 | En la aplicación de desarrollo, cambie las ubicaciones utilizando los archivos GPX creados anteriormente. | Debería ver el mensaje en la aplicación en función de los criterios anteriores establecidos. |
| 15 | Para la siguiente prueba, básicamente copiaremos los mismos pasos que antes, pero esta vez probaremos la NOTIFICACIÓN LOCAL. | El resultado esperado es que se muestren las notificaciones locales cada vez que se cumplan los criterios coincidentes. |
| 16 | Configure un nuevo mensaje en la aplicación (tipo = difusión). |  |
| 16a | En déclencheur, seleccione **[!UICONTROL Tipo de evento Places]** - **[!UICONTROL Entrada como déclencheur]**. |  |
| 16b | Seleccione los metadatos personalizados de Places como filtro adicional: utilice **[!UICONTROL Tipo de punto de interés]** = **[!UICONTROL Último punto de interés especificado]**. |  |
| 16c | Seleccione una clave de metadatos personalizada que le ayude a reducir los puntos de interés que recibirán un mensaje. |  |
| 16d | Para la frecuencia y la duración, conserve solo uno o dos días, de modo que si no le gustan los criterios, pueda caducar el déclencheur en un período de tiempo más breve. |  |
| 16e | Para pulsaciones Siempre/Una o Hasta, **[!UICONTROL SIEMPRE]**. |  |
| 16f | Para el tipo de visualización, seleccione **[!UICONTROL Notificación local]**. |  |
| 16g  | Prepare/confirme e implemente el mensaje en la aplicación. |  |
| 17 | En el entorno de desarrollo, conecte el dispositivo y pulse **[!UICONTROL Play]** en la compilación. Después de establecer que la ubicación funciona, ponga en segundo plano la aplicación y continúe cambiando de ubicación en Xcode o Android Studio. Debería ver las lecturas de la consola que indican el cambio de ubicación y también debería ver las notificaciones locales que se muestran según los criterios establecidos en el déclencheur. (Puede haber un retraso de entre uno y dos segundos). | El resultado esperado es que se muestren notificaciones locales cada vez que se cumplan los criterios coincidentes. |
|  | **PUNTO DE RESUMEN** <br>En esta fase, deberíamos ver entradas de puntos de interés en nuestro entorno local. También deberíamos ver la mensajería de Campaign en función del trabajo del POI. Si hay errores, compruebe si no se ha producido una notificación del Slack. Si no hay ningún mensaje de Slack, compruebe la consola de la aplicación, ya que es posible que no se haya registrado una nueva entrada de ubicación. Si los resultados son correctos, podemos estar bastante seguros de que la aplicación está funcionando correctamente y que el servicio de mensajería de Places y Campaign también está funcionando correctamente. |  |
|  | **PRUEBAS IN SITU** <br>No es mucho lo que debería cambiar al realizar pruebas en la ubicación. Mantener activo el postback de la demora ayudará a comprender si el dispositivo está obteniendo una entrada y salida para la ubicación. |  |
| 18 | Lleve a cabo pruebas con dispositivos que empiecen por wifi y móvil deshabilitados y, a continuación, active una vez en la región de puntos de interés. | Si se produce un error, tenga en cuenta si obtiene una entrada de geoperímetro y una notificación en el Slack. ¿Cuál es la marca de tiempo de la notificación del Slack? |
| 19 | Lleve a cabo la prueba sólo con la móvil habilitada y con la Wi-Fi desactivada. |  |
| 20 | Realice la prueba con el móvil y el Wi-Fi activados. |  |
|  | **PUNTO DE RESUMEN** <br>Las pruebas in situ deben coincidir estrechamente con las pruebas de desarrollo. Tenga en cuenta que hay algunos factores ambientales que pueden entrar en juego al determinar la ubicación de un usuario, como la duración del tiempo empleado en una geolocalización de punto de interés, la disponibilidad de la señal celular y la fuerza de los puntos de acceso Wi-Fi cercanos. |  |

## Muestras de registro

**Paso 8 :** Registros esperados de iOS y Android durante una actualización de ubicación

**iOS**

```
[AdobeExperienceSDK DEBUG <Places>]: Requesting 20 nearby POIs for device location (<lat>, <longitude>)
[AdobeExperienceSDK DEBUG <Places>]: Response from Places Query Service contained <n> nearby POIs   
```

**Android**

```
PlacesExtension - Dispatching nearby places event with n POIs   
```

**Paso 9 :** Registros esperados de iOS y Android durante un evento

**iOS**

```
[AdobeExperienceSDK TRACE <Places>]: Dispatching Places region entry event for place ID <poiId>
```

**Android**

```
PlacesExtension -  Dispatching Places Region Event for <poi name> with eventType entry
```
