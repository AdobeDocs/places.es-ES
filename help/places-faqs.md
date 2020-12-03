---
title: Preguntas frecuentes
description: Este tema proporciona información adicional sobre algunas preguntas más frecuentes.
translation-type: tm+mt
source-git-commit: 5846577f10eb1d570465ad7f888feba6dd958ec9
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 1%

---


# Preguntas frecuentes

A continuación encontrará información y preguntas más frecuentes sobre el servicio de lugares.

## Migración desde trackLocation en el SDK v4

Si va a realizar la migración desde el SDK v4 y está buscando un reemplazo para la `trackLocation` API, consulte el tema [Usar el servicio de lugares sin supervisión](use-places-without-active-monitoring.md)de región activa.

## Tamaño y fiabilidad

Es importante tener en cuenta que todas las geofences que se utilizan en la supervisión regional desde una aplicación móvil, independientemente de que se utilice Adobe o algún otro servicio. Los sistemas operativos recomiendan algunos parámetros que deben tenerse en cuenta al crear geofences. Para una máxima fiabilidad, las geofences deben tener un radio de al menos 100 metros. Está bien crear geofences más pequeñas, pero es posible que no se generen eventos de entrada y salida o que se generen después de que el usuario deje de moverse durante un período.

Además, la precisión y la fiabilidad pueden reducirse en función de las condiciones de hardware, como que la conexión Wi-Fi esté apagada o no esté disponible, y también en función de la ubicación del dispositivo en relación con la obstrucción de las señales GPS. Por ejemplo, las áreas montañosas, los entornos urbanos y las áreas interiores pueden reducir la precisión de ubicación de los sistemas operativos iOS y Android.

## ¿Cómo se desencadena un evento de salida?

Cuando el Monitor de lugares (SDK) obtiene una nueva lista de puntos de interés cercanos, registra una región con el sistema operativo para cada punto de interés. El sistema operativo ahora es responsable de notificar al SDK cuando el dispositivo cruza un límite (de entrada o salida) para una de las regiones monitoreadas. El SDK solo activa un evento de salida cuando el sistema operativo notifica al SDK que se ha producido el evento. El motivo principal de esta notificación es la diferencia horaria entre los datos de ubicación.

Si el sistema operativo no puede entregar un evento de salida cuando el dispositivo abandona una región, es más seguro que el SDK simplemente omita el evento de salida. Si el SDK fabrica un evento de salida sin que el sistema operativo active el evento, existe el riesgo de que el evento de salida se procese bastante fuera del período de tiempo durante el cual el dispositivo estaba cerca del punto de interés.

## Número de puntos de interés

En la interfaz de administración de puntos de interés del servicio de lugares, los clientes pueden añadir hasta 150 000 puntos de interés en una biblioteca específica. Si lo desea, los clientes pueden definir varias bibliotecas para segmentar grupos de puntos de interés.

## Algunas notas sobre el cambio de ubicación y la supervisión de región activa

La supervisión de una región geográfica comienza inmediatamente después del registro de las aplicaciones autorizadas. Sin embargo, no espere recibir un evento de inmediato, ya que sólo los cruces fronterizos generan un evento. En concreto, si la ubicación del usuario ya está dentro de la región en el momento del registro, el administrador de ubicaciones no genera automáticamente un evento. En su lugar, la aplicación debe esperar a que el usuario cruce el límite de la región antes de que se genere un evento y se envíe al delegado.

Sea prudente al especificar el conjunto de regiones que se deben supervisar. Las regiones son un recurso del sistema compartido y el número total de regiones disponibles en todo el sistema es limitado. Por este motivo, la ubicación principal limita a 20 el número de regiones que una sola aplicación puede supervisar simultáneamente. Para evitar este límite, considere la posibilidad de registrar solo las regiones cercanas al usuario.

[Consulte información adicional en el sitio] para desarrolladores de Apple (https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/LocationAwarenessPG/RegionMonitoring/RegionMonitoring.html#//apple_ref/doc/uid/TP40009497-CH9-SW11)
