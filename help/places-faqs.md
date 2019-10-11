---
title: Preguntas más frecuentes sobre lugares
seo-title: Preguntas más frecuentes sobre lugares
description: En este tema se proporciona información adicional sobre algunas preguntas más frecuentes sobre los lugares.
seo-description: En este tema se proporciona información adicional sobre algunas preguntas más frecuentes sobre los lugares.
translation-type: tm+mt
source-git-commit: ef3d77eba407013e1f701ed001ef9ab7b3818e07

---


# Preguntas más frecuentes sobre lugares

A continuación encontrará información y preguntas más frecuentes sobre los lugares.

## Tamaño y fiabilidad

Es importante tener en cuenta que todas las geofences que se utilizan en la supervisión regional desde una aplicación móvil, independientemente de que se utilice Adobe o algún otro servicio. Los sistemas operativos recomiendan algunos parámetros que deben tenerse en cuenta al crear geofences. Para una máxima fiabilidad, las geofences deben tener un radio de al menos 100 metros. Está bien crear geofences más pequeñas, pero es posible que los eventos de entrada y salida no se generen o que se generen después de que el usuario deje de moverse durante un período.

Además, la precisión y la fiabilidad pueden reducirse en función de las condiciones de hardware, como que la conexión Wi-Fi esté apagada o no esté disponible, y también en función de la ubicación del dispositivo en relación con la obstrucción de las señales GPS. Por ejemplo, las áreas montañosas, los entornos urbanos y las áreas interiores pueden reducir la precisión de ubicación de los sistemas operativos iOS y Android.

## ¿Cómo se desencadena un evento de salida?

Cuando el Monitor de lugares (SDK) obtiene una nueva lista de puntos de interés cercanos, registra una región con el sistema operativo para cada punto de interés. El sistema operativo ahora es responsable de notificar al SDK cuando el dispositivo cruza un límite (de entrada o salida) para una de las regiones monitoreadas. El SDK solo activa un evento de salida cuando el sistema operativo notifica al SDK que el evento se ha producido. El motivo principal de esta notificación es la diferencia horaria entre los datos de ubicación.

Si el sistema operativo no puede entregar un evento de salida cuando el dispositivo abandona una región, es más seguro que el SDK simplemente omita el evento de salida. Si el SDK fabrica un evento de salida sin que el sistema operativo active el evento, existe el riesgo de que el evento de salida se procese bien fuera del período de tiempo durante el cual el dispositivo estaba cerca del punto de interés.
