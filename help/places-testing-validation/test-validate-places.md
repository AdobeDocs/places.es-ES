---
title: Prueba y validación del servicio Places
description: Esta sección proporciona información sobre cómo probar y validar el servicio de Places.
exl-id: 8dad6619-566b-4aea-b29c-a89192a66441
source-git-commit: 2b5c53887c9ed0f2a672c377121a39537ee58f01
workflow-type: tm+mt
source-wordcount: '1731'
ht-degree: 2%

---

# Recommendations para probar el servicio de Places {#test-validate-loc-svc}

Muchos clientes y organizaciones definirán puntos de interés en todo el mundo, por lo que es importante tener una forma de simular y probar cómo el servicio Places interactúa con la aplicación. Esta información le ayuda a comprender cómo probar y validar las entradas y salidas del servicio de Places que se activan correctamente en función de los puntos de interés definidos y la ubicación actual de un usuario.

Dado que las variables de entorno pueden ser un factor en la señal de ubicación y la precisión, recomendamos que establezca primero los resultados de línea de base trabajando localmente con herramientas de desarrollador y entradas de ubicación simuladas. El objetivo es validar que todos los eventos de ubicación funcionan correctamente. Una vez validados correctamente los eventos de ubicación, se pueden probar las integraciones de la solución (por ejemplo, Analytics, Target y Campaign). Para ayudarle en sus actividades de prueba, debe configurar Webhooks de Slack con un postback y cargar archivos GPX en su entorno de desarrollo individual.

>[!IMPORTANT]
>
>Este plan supone que los puntos de interés se han creado en [IU del servicio Places](https://places.adobe.com) y las últimas versiones de la extensión Places están instaladas y configuradas correctamente. Si se realiza una monitorización de región activa, también se supone que se ha implementado una solución de monitorización de región. Para obtener más información, consulte [Extensión Places](/help/places-ext-aep-sdks/places-extension/places-extension.md), [Documentación de CoreLocation](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) para iOS, o [Documentación de ubicación de Android](https://developer.android.com/training/location/geofencing).

| Paso | Descripción | Resultado esperado |
|--- |--- |--- |
| 1 | Confirme que se han introducido las claves de manifiesto adecuadas para que Android conceda acceso a la ubicación de seguimiento. | Confirmado |
| 1a | Confirme que las actualizaciones de ubicación estén configuradas en iOS. Asegúrese también de que tiene las claves de lista desglosada adecuadas configuradas en iOS para solicitar permiso al usuario para rastrear la ubicación. | Confirmado |
| 2 | Confirme qué modo de monitorización está configurado para iOS. El modo continuo permite una buena precisión y persistencia, pero también reduce considerablemente la duración de la batería. | Cambios significativos o continuos |
| 3 | Si utiliza más de una biblioteca de puntos de interés, confirme que se han seleccionado las bibliotecas adecuadas en la extensión Places para Experience Platform Launch. | Confirmado |
| 4 | Confirme que las últimas versiones de las extensiones Mobile Core y Places se han incorporado a la aplicación a través de Gradle o CocoaPods. | Confirmado: para obtener más información sobre las actualizaciones recientes, consulte la [Notas de la versión.](/help/release-notes.md) |
| 5 | Confirme que los entornos correctos están configurados para la prueba. El ID del entorno de Launch debe coincidir con el entorno de desarrollo de Launch. | Confirmado |
| 6 | Cree archivos GPX para cada punto de interés que desee probar. Los archivos GPX se pueden utilizar en el entorno de desarrollo local para simular una entrada de ubicación. Para obtener información acerca de cómo crear y utilizar archivos GPX, vea los temas siguientes: <br>[Archivos GPX para el simulador de iOS [cerrado]](https://stackoverflow.com/questions/17292783/gpx-files-for-ios-simulator)<br>[https://mapstogpx.com/mobiledev.php](https://mapstogpx.com/mobiledev.php)<br>[PRUEBAS DE UBICACIÓN EN APLICACIONES MÓVILES](https://qacumtester.wordpress.com/2014/02/27/location-testing-in-mobile-apps/) | Los archivos GPX se crean y cargan en el proyecto de la aplicación. |
| 7 | Sin hacer nada más, debería poder iniciar la aplicación desde Android Studio o XCode y ver la alerta adecuada para solicitar acceso a la ubicación de seguimiento. Haga clic en *Permitir siempre* permiso.<br><br>Se recomienda usar un dispositivo real conectado al equipo en lugar de usar el simulador de dispositivos. | El mensaje de solicitud de ubicación debe mostrarse en la aplicación cargada a través del IDE |
| 8 | Una vez aceptado el permiso de ubicación. El SDK de Places intentará recuperar la ubicación actual del dispositivo y el código de monitorización de región debe comenzar a monitorizar los 20 puntos de interés más cercanos desde la ubicación actual | Consulte la muestra de registro debajo de la tabla. |
| 9 | Cambiar entre diferentes ubicaciones en XCode o Android Studio debería producir eventos de entrada para puntos de interés específicos. Se esperan los siguientes registros al entrar en un punto de interés. | Consulte la muestra de registro debajo de la tabla. |
| 10 | Una vez que el monitor de región encuentre los puntos de interés cercanos, debe probar enviando pings de ubicación. En Launch, cree una nueva regla que utilice la extensión Places para almacenar en déclencheur en función de una entrada de geoperímetro. A continuación, cree una nueva acción con Mobile Core para enviar un Postback. La creación de una aplicación de webhook de Slack le ayuda a ver las entradas y salidas de la ubicación. Para obtener información sobre la creación de una aplicación de webhook de Slack, consulte [Envío de mensajes mediante Webhooks entrantes.](https://api.slack.com/messaging/webhooks) |  |
| 10a | En Launch, asegúrese de añadir elementos de datos para la extensión Places, incluidos los siguientes: <br>Nombre del PDI actual<br>Último punto de interés actual<br>Punto de interés actual largo<br>Último nombre introducido<br>Última entrada última<br>Última entrada larga<br>Apellido de salida<br>Última salida última<br>Última salida larga<br>Marca de tiempo |  |
| 10b | Crear una regla nueva con un Evento = Lugares → Introducir punto de interés |  |
| 10c | Crear una acción = Mobile Core → Postback |  |
| 10d | Utilice la URL de webhook para su aplicación de Slack, por ejemplo, https://hooks.slack.com/services/TKN5FKS68/BNFP7SVD.... |  |
| 10e | El cuerpo del mensaje sería similar al siguiente: `{text: User is in POI -  {%%Last Entered POI Name%%} in {%%Last Entered POI City%%} additional information: Radius:{%%Last Entered POI Radius%%} Timestamp: {%%timestamp%%}}`. <br>Asegúrese de utilizar los elementos de datos específicos que ha creado aquí. |  |
| 10f | Asegúrese de publicar todos los cambios nuevos de elementos de datos y reglas en Launch. (Debe seleccionar una biblioteca de desarrollo en funcionamiento en la parte superior derecha de la interfaz de Launch). |  |
| 11 | Inicie y vuelva a probar la aplicación cambiando entre las ubicaciones de GPX en el IDE de desarrollador. | Ahora debería ver las notificaciones del Slack que muestran las entradas de cada POI al seleccionar diferentes ubicaciones en el entorno de desarrollo. |
|  | **PUNTO DE RESUMEN RÁPIDO**<br> Todas estas pruebas se pueden realizar localmente sin tener que ir a una ubicación de punto de interés específica. Las pruebas de validación ayudan a garantizar que la aplicación esté configurada correctamente y que haya recibido los permisos correctos para la ubicación. <br><br>Esta validación también le ofrece la seguridad de que los puntos de interés definidos funcionan correctamente con la implementación de monitorización de su región.  Después de este paso, empezaremos a probar la mensajería en Campaign para ver si aparecen los mensajes adecuados en función de las entradas y salidas de los puntos de interés. |  |
|  | **Prueba de la mensajería en la aplicación de Adobe Campaign Standard con el servicio Places.** |  |
| 12 | En el panel principal de Campaign, configure un nuevo mensaje en la aplicación (type = broadcast) |  |
| 12a | En déclencheur, seleccione **Tipo de evento de Places: entrada como déclencheur**. |  |
| 12b | Seleccionar **[!UICONTROL Coloca metadatos personalizados]** como filtro adicional, utilice el tipo de punto de interés = Último punto de interés introducido.<br>Utilizamos **[!UICONTROL Última entrada]** como el tipo de punto de interés, porque en la mayoría de los casos, **[!UICONTROL Última entrada]** será el mismo que **[!UICONTROL Punto de interés actual]**. <br><br>**[!UICONTROL Punto de interés actual ]**solo debe utilizarse en casos en los que haya geoperímetros de puntos de interés superpuestos. En este caso, estos puntos de interés deben CLASIFICARSE y, a continuación, la variable**[!UICONTROL  Punto de interés actual ]**mostrará el punto de interés de mayor clasificación de los dos o tres geoperímetros en los que podría encontrarse un usuario. |  |
| 12c | Seleccione una clave de metadatos personalizada que le ayude a reducir los puntos de interés que recibirán un mensaje. |  |
| 12d | Para la frecuencia y la duración, manténgase a solo uno o dos días, de modo que si no le gustan los criterios, puede caducar el déclencheur en un período de tiempo más corto. |  |
| 12e | Para una pulsación Always/Once o Until, seleccione *SIEMPRE* para poder realizar pruebas en varias ubicaciones. | Se muestra SIEMPRE un mensaje en la aplicación cuando simula un cambio de ubicación que cumple los criterios de metadatos adecuados. |
| 12f | Para la visualización, seleccione una opción distinta a Notificación local. Esto facilita la visualización al realizar pruebas con la aplicación en primer plano). |  |
| 12g  | Prepare/confirme e implemente el mensaje en la aplicación. |  |
| 13 | En el entorno de desarrollo, para asegurarse de que se descargan nuevas reglas de campaña, salga de la aplicación y vuelva a iniciarla. | No olvide que las aplicaciones deben volver a iniciarse por completo para que el nuevo archivo de reglas de Campaign se descargue en el dispositivo. |
| 14 | En la aplicación de desarrollo, cambie las ubicaciones utilizando los archivos GPX creados anteriormente. | Debería ver que el mensaje en la aplicación aparece en función de los criterios anteriores establecidos. |
| 15 | Para la siguiente prueba, copiaremos esencialmente los mismos pasos que antes, pero esta vez probaremos LOCAL NOTIFICATION. | El resultado esperado es que las notificaciones locales se muestren cada vez que se cumplan los criterios coincidentes. |
| 16 | Configure un nuevo mensaje en la aplicación (type = broadcast). |  |
| 16a | En déclencheur, seleccione **[!UICONTROL Tipo de evento de Places]** - **[!UICONTROL Entrada como déclencheur]**. |  |
| 16b | Seleccione los metadatos personalizados de Places como filtro adicional: usar **[!UICONTROL Tipo de PDI]** = **[!UICONTROL Último punto de interés]**. |  |
| 16c | Seleccione una clave de metadatos personalizada que le ayude a reducir los puntos de interés que recibirán un mensaje. |  |
| 16d | Para la frecuencia y la duración, mantenga solo uno o dos días, de modo que si no le gustan los criterios, puede caducar el déclencheur en un período de tiempo más corto. |  |
| 16e | Para una pulsación Always/Once o Until, **[!UICONTROL SIEMPRE]**. |  |
| 16f | Para el tipo de visualización, seleccione **[!UICONTROL Notificación local]**. |  |
| 16g  | Prepare/confirme e implemente el mensaje en la aplicación. |  |
| 17 | En el entorno de desarrollo, conecte el dispositivo y pulse **[!UICONTROL Reproducir]** en la compilación. Después de establecer que la ubicación funciona, ponga en segundo plano la aplicación y continúe cambiando de ubicación en Xcode o Android Studio. Debería seguir viendo las lecturas de la consola que indican el cambio de ubicación, y también debería ver las notificaciones locales mostradas según los criterios establecidos en el déclencheur. (Podría haber un retraso de 1 a 2 segundos). | El resultado esperado es que las notificaciones locales se muestren cada vez que se cumplan los criterios coincidentes. |
|  | **PUNTO DE RESUMEN** <br>En esta fase, deberíamos ver las entradas de puntos de interés en nuestro entorno local. También deberíamos ver los mensajes de Campaign basados en el trabajo del PDI. Si hay errores, compruebe si no se ha emitido una notificación al Slack. Si no hay ningún mensaje del Slack, compruebe la consola de aplicaciones, ya que es posible que no se haya registrado una nueva entrada de ubicación. Si los resultados son correctos, podemos estar bastante seguros de que la aplicación funciona correctamente y de que el servicio de mensajería de Places Service y Campaign también funciona correctamente. |  |
|  | **PRUEBAS A DOMICILIO** <br>No debería cambiar mucho al realizar pruebas in situ. Mantener el postback de Slack activo debería ayudar a comprender si el dispositivo recibe una entrada y salida para la ubicación. |  |
| 18 | Realice pruebas con dispositivos que empiecen con wifi y dispositivos móviles deshabilitados y luego habilite una vez en la región del PDI. | Si se produce un error, anote si obtiene una entrada de límite geográfico y una notificación en Slack. ¿Cuál es la marca de tiempo de la notificación al Slack? |
| 19 | Realiza la prueba solo con el móvil habilitado y con el wifi apagado. |  |
| 20 | Realice la prueba con el teléfono móvil y el WiFi activados. |  |
|  | **PUNTO DE RESUMEN** <br>Las pruebas in situ deben coincidir estrechamente con las pruebas de desarrollo. Tenga en cuenta que hay algunos factores ambientales que pueden entrar en juego al determinar la ubicación de un usuario, como la duración del tiempo invertido en una geoperímetro de PDI, la disponibilidad de la señal celular y la fuerza de los puntos de acceso wifi cercanos. |  |

## Muestras de registro

**Paso 8:** Registros esperados de iOS y Android durante una actualización de ubicación

**iOS**

```
[AdobeExperienceSDK DEBUG <Places>]: Requesting 20 nearby POIs for device location (<lat>, <longitude>)
[AdobeExperienceSDK DEBUG <Places>]: Response from Places Query Service contained <n> nearby POIs   
```

**Android**

```
PlacesExtension - Dispatching nearby places event with n POIs   
```

**Paso 9:** Registros esperados de iOS y Android durante un evento

**iOS**

```
[AdobeExperienceSDK TRACE <Places>]: Dispatching Places region entry event for place ID <poiId>
```

**Android**

```
PlacesExtension -  Dispatching Places Region Event for <poi name> with eventType entry
```
