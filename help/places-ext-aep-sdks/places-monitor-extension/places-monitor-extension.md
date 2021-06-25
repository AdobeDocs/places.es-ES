---
title: Extensión de seguimiento de Places
description: La extensión de seguimiento de Places gestiona las interacciones con el sistema operativo para registrar y monitorizar los puntos de interés más cercanos al usuario.
exl-id: 254b33a0-79c4-4d51-8835-16e60f5c055e
source-git-commit: 8dcd777acf5d578b748afae9aa609c2349ea94a9
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 0%

---

# Extensión de seguimiento de Places {#places-monitor-extension}

La extensión de seguimiento de Places gestiona las interacciones con el sistema operativo para registrar y monitorizar los puntos de interés más cercanos al usuario. Esta extensión recupera los puntos de interés que deben registrarse desde la extensión Places y pasa las notificaciones de entrada y salida a la extensión Places. Estas notificaciones estarán disponibles en reglas de Experience Platform Launch como eventos.

La extensión Monitor es opcional, ya que es posible que algunos clientes ya estén monitorizando regiones con el sistema operativo. En este caso, asegúrese de añadir las API de extensión Places para recibir los puntos de interés más cercanos de la base de datos del servicio Places y también pasar los eventos de entrada y salida para poder realizar las acciones adecuadas.

## Finalización del monitor de Places

El 31 de agosto de 2021, la extensión del monitor Places para los SDK de Adobe Experience Platform Mobile dejará de usarse. La extensión Places Monitor no recibirá más actualizaciones ni asistencia después del 31 de agosto.

Los clientes que actualmente utilizan la extensión de seguimiento de Places pueden seguir utilizando esta extensión con el entendimiento de que no habrá actualizaciones ni asistencia adicionales disponibles a través del Adobe.

La desaprobación de la extensión del Monitor de Places no tiene ningún impacto negativo o negativo en la extensión del Servicio de Places, que se seguirá admitiendo con mejoras y actualizaciones.

Los clientes que buscan pasar de la extensión Places Monitor a su propia solución de monitorización deben revisar la documentación para: [Utilice el servicio Places con su propia solución de monitorización](https://experienceleague.adobe.com/docs/places/using/using-your-own-monitor.html?lang=en). En este documento se explica cómo interactuar con el servicio Places mediante la implementación de [Servicios de ubicación principal](https://developer.apple.com/documentation/corelocation) en iOS o [Servicios de ubicación](https://developers.google.com/android/reference/com/google/android/gms/location/package-summary) desde Google Play.
