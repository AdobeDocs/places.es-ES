---
title: Prueba y validación del servicio Places
description: Esta sección proporciona información sobre cómo probar y validar el servicio de Places.
exl-id: 8dad6619-566b-4aea-b29c-a89192a66441
TQID: https://experienceleague.adobe.com/nO4tOQW9rp3zjkHT6aJ5IcXHcD9heOaRAJiEchiz1Fk
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: dc5cf79d-43c4-4731-bffa-1df5d7549cb1id: dfc56824-e8b9-499e-85d4-21aedb507314id: e43347a8-f2c5-4aa4-8623-6f13875d7e3aid: e55547f1-a1ff-40c6-8978-026e40ab7fa4id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2: id: c93393a4-e558-47e1-992e-c91ed4d480ceid: d5ef99fa-df0c-4153-bf94-105ad0724167id: daec7ead-f475-492a-a3b3-02ae08565d6fid: e08599ea-8888-4294-ba74-3ba0a7762a46id: eb9732ab-8232-4b21-bc4c-89de86dbe4d7id: ed0d8d0e-04b9-4326-be72-a0fbca265377id: f7c7de77-382f-4f48-8b36-61a170f06d3did: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
subfeature_v2: id: c3bf7e1e-1db5-4c72-9293-e2f0b1ab73d0id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 1748
ht-degree: 2%

---

# Recomendaciones para probar el servicio Places {#test-validate-loc-svc}

Muchos clientes y organizaciones definirán puntos de interés en todo el mundo, por lo que es importante tener una forma de simular y probar cómo el servicio Places interactúa con la aplicación. Esta información le ayuda a comprender cómo probar y validar las entradas y salidas del servicio de Places que se activan correctamente en función de los puntos de interés definidos y la ubicación actual de un usuario.

Dado que las variables de entorno pueden ser un factor en la señal de ubicación y la precisión, recomendamos que establezca primero los resultados de línea de base trabajando localmente con herramientas de desarrollador y entradas de ubicación simuladas. El objetivo es validar que todos los eventos de ubicación funcionan correctamente. Una vez validados correctamente los eventos de ubicación, se pueden probar las integraciones de la solución (por ejemplo, Analytics, Target y Campaign). Para ayudarle en sus actividades de prueba, debe configurar los webhooks de Slack con un postback y cargar los archivos GPX en su entorno de desarrollo individual.

>[!IMPORTANT]
>
>Este plan supone que los puntos de interés se han creado en la interfaz de usuario de [Places Service](https://places.adobe.com) y que las versiones más recientes de la extensión Places están instaladas y configuradas correctamente. Si se realiza una monitorización de región activa, también se supone que se ha implementado una solución de monitorización de región. Para obtener más información, consulte [Extensión Places](/help/places-ext-aep-sdks/places-extension/places-extension.md), [Documentación de CoreLocation](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) para iOS o [Documentación de ubicación de Android](https://developer.android.com/training/location/geofencing).

| Paso | Descripción | Resultado esperado |
|--- |--- |--- |
| 1 | Confirme que se han introducido las claves de manifiesto adecuadas para que Android conceda acceso a la ubicación de seguimiento. | Confirmado |
| 1a | Confirme que las actualizaciones de ubicación estén configuradas en iOS. Asegúrese también de que tiene las claves de lista desglosada adecuadas configuradas en iOS para solicitar permiso al usuario para rastrear la ubicación. | Confirmado |
| 2 | Confirme qué modo de monitorización está configurado para iOS. El modo continuo permite una mayor precisión y persistencia, pero también una mayor duración de la batería. | Cambios significativos o continuos |
| 3 | Si utiliza más de una biblioteca de puntos de interés, confirme que las bibliotecas adecuadas se hayan seleccionado en la extensión Places de Experience Platform Launch. | Confirmado |
| 4 | Confirme que las últimas versiones de las extensiones Mobile Core y Places se han incorporado a la aplicación a través de Gradle o CocoaPods. | Confirmado: para obtener más información sobre actualizaciones recientes, consulte las [notas de la versión.](/help/release-notes.md) |
| 5 | Confirme que los entornos correctos están configurados para la prueba. El ID del entorno de Launch debe coincidir con el entorno de desarrollo de Launch. | Confirmado |
| 6 | Cree archivos GPX para cada punto de interés que desee probar. Los archivos GPX se pueden utilizar en el entorno de desarrollo local para simular una entrada de ubicación. Para obtener información acerca de cómo crear y usar archivos GPX, consulte: <br>[Archivos GPX para el simulador de iOS [cerrado]](https://stackoverflow.com/questions/17292783/gpx-files-for-ios-simulator)<br>[https://mapstogpx.com/mobiledev.php](https://mapstogpx.com/mobiledev.php)<br>[PRUEBAS DE UBICACIÓN EN APLICACIONES MÓVILES](https://qacumtester.wordpress.com/2014/02/27/location-testing-in-mobile-apps/) | Los archivos GPX se crean y cargan en el proyecto de la aplicación. |
| 7 | Sin hacer nada más, debería poder iniciar la aplicación desde Android Studio o XCode y ver la alerta adecuada para solicitar acceso a la ubicación de seguimiento. Haga clic en el permiso *Permitir siempre*.<br><br>Se recomienda usar un dispositivo real conectado al equipo en lugar de usar el simulador de dispositivos. | El mensaje de solicitud de ubicación debe mostrarse en la aplicación cargada a través del IDE |
| 8 | Una vez aceptado el permiso de ubicación. La SDK de Places recuperará la ubicación actual del dispositivo y el código de monitorización de región debe comenzar a monitorizar los 20 puntos de interés más cercanos desde la ubicación actual | Consulte la muestra de registro debajo de la tabla. |
| 9 | Cambiar entre diferentes ubicaciones en XCode o Android Studio debería producir eventos de entrada para puntos de interés específicos. Se esperan los siguientes registros al entrar en un punto de interés. | Consulte la muestra de registro debajo de la tabla. |
| 10 | Una vez que el monitor de región encuentre los puntos de interés cercanos, debe probar enviando pings de ubicación. En Launch, cree una nueva regla que utilice la extensión Places para almacenar en déclencheur en función de una entrada de geoperímetro. A continuación, cree una nueva acción con Mobile Core para enviar un Postback. La creación de una aplicación de webhook de Slack le ayuda a ver entradas y salidas de ubicación. Para obtener información sobre cómo crear una aplicación de webhook de Slack, consulte [Envío de mensajes mediante webhooks entrantes.](https://api.slack.com/messaging/webhooks) |  |
| 10a | En Launch, asegúrese de agregar elementos de datos para la extensión Places, entre los que se incluyen los siguientes: <br>Nombre del punto de interés actual<br>Nombre del punto de interés actual lat<br>Longitud del punto de interés actual<br>Último nombre introducido<br>Último nombre introducido lat<br>Último nombre introducido long<br>Último nombre saliente<br>Último nombre saliente lat<br>Último largo saliente<br>Marca de tiempo |  |
| 10b | Crear una regla nueva con un Evento = Lugares → Introducir punto de interés |  |
| 10c | Crear una acción = Mobile Core → Postback |  |
| 10d | Utilice la URL de webhook para su aplicación de Slack, por ejemplo, https://hooks.slack.com/services/TKN5FKS68/BNFP7SVD.... |  |
| 10e | El cuerpo del mensaje sería similar a: `{text: User is in POI -  {%%Last Entered POI Name%%} in {%%Last Entered POI City%%} additional information: Radius:{%%Last Entered POI Radius%%} Timestamp: {%%timestamp%%}}`. <br>Asegúrese de utilizar los elementos de datos específicos que creó aquí. |  |
| 10f | Asegúrese de publicar todos los cambios nuevos de elementos de datos y reglas en Launch. (Debe seleccionar una biblioteca de desarrollo en funcionamiento en la parte superior derecha de la interfaz de Launch). |  |
| 11 | Inicie y vuelva a probar la aplicación cambiando entre las ubicaciones de GPX en el IDE de desarrollador. | Ahora debería ver las notificaciones de Slack que muestran las entradas de cada POI al seleccionar diferentes ubicaciones en el entorno de desarrollo. |
|  | **PUNTO DE RESUMEN RÁPIDO**<br> Todas estas pruebas se pueden realizar localmente sin tener que ir a una ubicación de punto de interés específica. Las pruebas de validación ayudan a garantizar que la aplicación esté configurada correctamente y que haya recibido los permisos correctos para la ubicación. <br><br>Esta validación también le da la seguridad de que los puntos de interés definidos funcionan correctamente con la implementación de supervisión de su región.  Después de este paso, empezaremos a probar la mensajería en Campaign para ver si aparecen los mensajes adecuados en función de las entradas y salidas de los puntos de interés. |  |
|  | **Probando la mensajería en la aplicación de Adobe Campaign Standard con el servicio Places.** |  |
| 12 | En el panel principal de Campaign, configure un nuevo mensaje en la aplicación (type = broadcast) |  |
| 12a | En déclencheur, seleccione **Tipo de evento de lugares - Entrada como déclencheur**. |  |
| 12b | Seleccione **[!UICONTROL Metadatos personalizados de Places]** como filtro adicional. Use el tipo de punto de interés = Último punto de interés (POI).<br>Utilizamos **[!UICONTROL Última entrada]** como tipo de punto de interés (POI) porque, en la mayoría de los casos, **[!UICONTROL Última entrada]** será igual que **[!UICONTROL Punto de interés actual]**. <br><br>**[!UICONTROL El punto de interés actual ]**solo debe usarse en instancias donde haya geoperímetros de punto de interés superpuestos. En este caso, estos puntos de interés deben estar EN LA CLASIFICACIÓN y, a continuación, el**[!UICONTROL  punto de interés actual ]**mostrará el punto de interés de mayor clasificación de los 2 o 3 geoperímetros en los que podría estar un usuario en ese momento. |  |
| 12c | Seleccione una clave de metadatos personalizada que le ayude a reducir los puntos de interés que recibirán un mensaje. |  |
| 12d | Para la frecuencia y la duración, manténgase a solo uno o dos días, de modo que si no le gustan los criterios, puede caducar el déclencheur en un período de tiempo más corto. |  |
| 12e | Para Pulsaciones siempre/una vez o hasta, seleccione *SIEMPRE* para poder realizar pruebas en varias ubicaciones. | Se muestra SIEMPRE un mensaje en la aplicación cuando simula un cambio de ubicación que cumple los criterios de metadatos adecuados. |
| 12f | Para la visualización, seleccione una opción distinta a Notificación local. Esto facilita la visualización al realizar pruebas con la aplicación en primer plano). |  |
| 12g | Prepare/confirme e implemente el mensaje en la aplicación. |  |
| 13 | En el entorno de desarrollo, para asegurarse de que se descargan nuevas reglas de campaña, salga de la aplicación y vuelva a iniciarla. | No olvide que las aplicaciones deben volver a iniciarse por completo para que el nuevo archivo de reglas de Campaign se descargue en el dispositivo. |
| 14 | En la aplicación de desarrollo, cambie las ubicaciones utilizando los archivos GPX creados anteriormente. | Debería ver que el mensaje en la aplicación aparece en función de los criterios anteriores establecidos. |
| 15 | Para la siguiente prueba, copiaremos esencialmente los mismos pasos que antes, pero esta vez probaremos LOCAL NOTIFICATION. | El resultado esperado es que las notificaciones locales se muestren cada vez que se cumplan los criterios coincidentes. |
| 16 | Configure un nuevo mensaje en la aplicación (type = broadcast). |  |
| 16a | En déclencheur, seleccione **[!UICONTROL Tipo de evento de Places]** - **[!UICONTROL Entrada como déclencheur]**. |  |
| 16b | Seleccione los metadatos personalizados de Places como filtro adicional - usar **[!UICONTROL tipo de punto de interés]** = **[!UICONTROL Último punto de interés]**. |  |
| 16c | Seleccione una clave de metadatos personalizada que le ayude a reducir los puntos de interés que recibirán un mensaje. |  |
| 16d | Para la frecuencia y la duración, mantenga solo uno o dos días, de modo que si no le gustan los criterios, puede caducar el déclencheur en un período de tiempo más corto. |  |
| 16e | Para siempre/una vez o hasta que se haga clic, **[!UICONTROL SIEMPRE]**. |  |
| 16f | Para el tipo de presentación, seleccione **[!UICONTROL Notificación local]**. |  |
| 16g | Prepare/confirme e implemente el mensaje en la aplicación. |  |
| 17 | En el entorno de desarrollo, conecta tu dispositivo y pulsa **[!UICONTROL Reproducir]** en la compilación. Después de establecer que la ubicación funciona, ponga en segundo plano la aplicación y continúe cambiando de ubicación en Xcode o Android Studio. Debería seguir viendo las lecturas de la consola que indican el cambio de ubicación, y también debería ver las notificaciones locales mostradas según los criterios establecidos en el déclencheur. (Podría haber un retraso de 1 a 2 segundos). | El resultado esperado es que las notificaciones locales se muestren cada vez que se cumplan los criterios coincidentes. |
|  | **PUNTO DE RESUMEN** <br>En este momento, deberíamos ver las entradas de puntos de interés en nuestro entorno local. También deberíamos ver los mensajes de Campaign basados en el trabajo del PDI. Si hay errores, compruebe si no se ha emitido una notificación de Slack. Si no hay ningún mensaje de Slack, compruebe la consola de aplicaciones, ya que es posible que no se haya registrado una nueva entrada de ubicación. Si los resultados son correctos, podemos estar bastante seguros de que la aplicación funciona correctamente y de que el servicio de mensajería de Places Service y Campaign también funciona correctamente. |  |
|  | **PRUEBAS IN SITU** <br>No debería haber grandes cambios al realizar pruebas in situ. Mantener el postback de Slack activo debería ayudar a comprender si el dispositivo recibe una entrada y salida para la ubicación. |  |
| 18 | Realice pruebas con dispositivos que empiecen con wifi y dispositivos móviles deshabilitados y luego habilite una vez en la región del PDI. | Si se produce un error, anote si obtiene una entrada de límite geográfico y una notificación en Slack. ¿Cuál es la marca de tiempo de la notificación de Slack? |
| 19 | Realiza la prueba solo con el móvil habilitado y con el wifi apagado. |  |
| 20 | Realice la prueba con el teléfono móvil y el WiFi activados. |  |
|  | **PUNTO DE RESUMEN** <br>Las pruebas in situ deben coincidir con las pruebas de desarrollo. Tenga en cuenta que hay algunos factores ambientales que pueden entrar en juego al determinar la ubicación de un usuario, como la duración del tiempo invertido en una geoperímetro de PDI, la disponibilidad de la señal celular y la fuerza de los puntos de acceso wifi cercanos. |  |

## Muestras de registro

**Paso 8 :** Se esperaban registros de iOS y Android durante una actualización de ubicación

**iOS**

```
[AdobeExperienceSDK DEBUG <Places>]: Requesting 20 nearby POIs for device location (<lat>, <longitude>)
[AdobeExperienceSDK DEBUG <Places>]: Response from Places Query Service contained <n> nearby POIs   
```

**Android**

```
PlacesExtension - Dispatching nearby places event with n POIs   
```

**Paso 9 :** Se esperaban registros de iOS y Android durante un evento

**iOS**

```
[AdobeExperienceSDK TRACE <Places>]: Dispatching Places region entry event for place ID <poiId>
```

**Android**

```
PlacesExtension -  Dispatching Places Region Event for <poi name> with eventType entry
```
