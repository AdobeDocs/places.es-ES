---
title: Preguntas frecuentes
description: En este tema se proporciona información adicional acerca de algunas preguntas más frecuentes.
exl-id: cee9f447-5e50-4ed8-b37b-baecbc0e9b7b
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 1%

---

# Preguntas frecuentes

A continuación encontrará información y las preguntas más frecuentes sobre el servicio de Places.

## Migración desde trackLocation en el SDK v4

Si está migrando desde el SDK v4 y busca un reemplazo al `trackLocation` API, consulte el tema [Usar el servicio de Places sin supervisión de región activa](use-places-without-active-monitoring.md).

## Tamaño y fiabilidad

Importante tenerlo en cuenta para todas las geovallas que se utilizan en la monitorización de regiones desde una aplicación móvil, independientemente del uso del Adobe o de algún otro servicio. Los sistemas operativos recomiendan algunos parámetros que se deben tener en cuenta al crear geovallas. Para lograr la máxima fiabilidad, las geovallas deben tener un radio de al menos 100 metros. Es aceptable crear geoperímetros más pequeños, pero es posible que no se generen eventos de entrada y salida, o que se generen después de que el usuario deje de moverse durante un periodo.

Además, la precisión y la fiabilidad pueden reducirse en función de las condiciones del hardware, como que el wi-fi esté apagado o no disponible, y también en función de la ubicación del dispositivo en relación con la obstrucción de las señales GPS. Por ejemplo, las áreas montañosas, los entornos urbanos y las áreas interiores pueden reducir la precisión de ubicación de los sistemas operativos iOS y Android.

## ¿Cómo entra en déclencheur un evento de salida?

El monitor de región implementado debe solicitar una lista de puntos de interés cercanos. Una vez recibida, se debe registrar una región con el sistema operativo para cada punto de interés. El sistema operativo ahora es responsable de notificar al SDK cuando el dispositivo cruza un límite (de entrada o salida) para una de las regiones monitorizadas. El SDK solo almacena en déclencheur un evento de salida cuando el sistema operativo notifica al SDK que se ha producido el evento. El motivo principal de esta notificación es la distinción de tiempo de los datos de ubicación.

Si el sistema operativo no puede entregar un evento de salida cuando el dispositivo abandona una región, es más seguro para el SDK omitir simplemente el evento de salida. Si el SDK fabrica un evento de salida sin que el sistema operativo active el evento, existe el riesgo de que el evento de salida se procese mucho más allá del período de tiempo durante el cual el dispositivo estuvo cerca del punto de interés.

## Número de puntos de interés

En la interfaz de administración de puntos de interés del servicio de Places, los clientes pueden añadir hasta 150 000 puntos de interés en una biblioteca específica. Los clientes pueden definir varias bibliotecas para segmentar las agrupaciones de puntos de interés si lo desean.

## Algunas notas sobre el cambio de ubicación y la monitorización activa de la región

La monitorización de una región geográfica comienza inmediatamente después del registro para aplicaciones autorizadas. Sin embargo, no espere recibir un evento de inmediato, ya que solo los cruces fronterizos generan un evento. En concreto, si la ubicación del usuario ya está dentro de la región en el momento del registro, el administrador de ubicaciones no genera automáticamente un evento. En su lugar, la aplicación debe esperar a que el usuario cruce el límite de la región para que se genere un evento y se envíe al delegado.

Tenga cuidado al especificar el conjunto de regiones que desea supervisar. Las regiones son un recurso compartido del sistema y el número total de regiones disponibles en todo el sistema es limitado. Por este motivo, la ubicación principal limita a 20 el número de regiones que una sola aplicación puede monitorizar simultáneamente. Para solucionar este límite, considere la posibilidad de registrar solo aquellas regiones en las inmediaciones del usuario.

[Consulte información adicional en el sitio para desarrolladores de Apple] (https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/LocationAwarenessPG/RegionMonitoring/RegionMonitoring.html#//apple_ref/doc/uid/TP40009497-CH9-SW11)
