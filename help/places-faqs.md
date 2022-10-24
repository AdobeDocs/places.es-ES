---
title: Preguntas frecuentes
description: En este tema se proporciona información adicional sobre algunas preguntas más frecuentes.
exl-id: cee9f447-5e50-4ed8-b37b-baecbc0e9b7b
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 1%

---

# Preguntas frecuentes

A continuación encontrará información y las preguntas más frecuentes sobre el servicio Places.

## Migración desde trackLocation en el SDK v4

Si está migrando del SDK v4 y está buscando un reemplazo para el `trackLocation` API, consulte el tema [Usar el servicio de Places sin supervisión de región activa](use-places-without-active-monitoring.md).

## Tamaño y fiabilidad

Es importante tener en cuenta que todas las geovallas que se usan en la supervisión regional desde una aplicación móvil independientemente del uso del Adobe o de otro servicio. Los sistemas operativos recomiendan algunos parámetros que deben tenerse en cuenta al crear geovallas. Para obtener la máxima fiabilidad, las geovallas deben tener un radio mínimo de 100 metros. Se pueden crear geovallas más pequeñas, pero es posible que los eventos de entrada y salida no se generen o que se generen después de que el usuario deje de moverse durante un período.

Además, la precisión y la fiabilidad pueden reducirse en función de las condiciones de hardware, como que la conexión wi-fi esté apagada o no esté disponible, y también en función de la ubicación del dispositivo en relación con la obstaculización de las señales GPS. Por ejemplo, las áreas montañosas, la configuración urbana y las áreas interiores pueden reducir la precisión de ubicación de los sistemas operativos iOS y Android.

## ¿Cómo déclencheur un evento de salida?

El monitor de región implementado debe solicitar una lista de puntos de interés cercanos. Una vez recibida, una región debe registrarse con el sistema operativo para cada punto de interés. El sistema operativo ahora es responsable de notificar al SDK cuando el dispositivo cruza un límite (de entrada o salida) para una de las regiones monitorizadas. El SDK solo déclencheur un evento de salida cuando el sistema operativo notifica al SDK de que se ha producido el evento. El motivo principal de esta notificación es la distinción horaria de los datos de ubicación.

Si el sistema operativo no puede entregar un evento de salida cuando el dispositivo abandona una región, es más seguro que el SDK simplemente omita el evento de salida. Si el SDK fabrica un evento de salida sin que el sistema operativo active el evento, existe el riesgo de que el evento de salida se procese bien fuera del período de tiempo durante el cual el dispositivo estaba cerca del punto de interés.

## Número de puntos de interés

En la interfaz de administración de puntos de interés de Places Service, los clientes pueden añadir hasta 150 000 puntos de interés en una biblioteca específica. Si lo desea, los clientes pueden definir varias bibliotecas para segmentar agrupaciones de puntos de interés.

## Algunas notas sobre cambio de ubicación y supervisión de regiones activas

La supervisión de una región geográfica comienza inmediatamente después del registro para aplicaciones autorizadas. Sin embargo, no espere recibir un evento de inmediato, ya que solo los cruces fronterizos generan un evento. En concreto, si la ubicación del usuario ya está dentro de la región en el momento del registro, el administrador de ubicaciones no genera automáticamente un evento. En su lugar, la aplicación debe esperar a que el usuario cruce los límites de la región antes de que se genere un evento y se envíe al delegado.

Sea prudente al especificar el conjunto de regiones que se van a supervisar. Las regiones son un recurso del sistema compartido y el número total de regiones disponibles en todo el sistema es limitado. Por este motivo, la ubicación principal limita a 20 el número de regiones que una sola aplicación puede supervisar simultáneamente. Para solucionar este límite, considere la posibilidad de registrar solo aquellas regiones en las inmediaciones del usuario.

[Consulte información adicional en el sitio para desarrolladores de Apple] (https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/LocationAwarenessPG/RegionMonitoring/RegionMonitoring.html#//apple_ref/doc/uid/TP40009497-CH9-SW11)
