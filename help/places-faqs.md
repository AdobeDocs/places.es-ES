---
title: Preguntas frecuentes
description: En este tema se proporciona información adicional acerca de algunas preguntas más frecuentes.
exl-id: cee9f447-5e50-4ed8-b37b-baecbc0e9b7b
TQID: https://experienceleague.adobe.com/LL9eLMDJaq8ZmeiZxv28QZoqXL1A0QKZ-DvTDUx4Gnw
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: dc5cf79d-43c4-4731-bffa-1df5d7549cb1
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 557
ht-degree: 1%

---

# Preguntas frecuentes

A continuación encontrará información y las preguntas más frecuentes sobre el servicio de Places.

## Migración desde trackLocation en SDK v4

Si está migrando desde la versión 4 de SDK y busca un reemplazo a la API `trackLocation`, consulte el tema [Usar el servicio Places sin supervisión de región activa](use-places-without-active-monitoring.md).

## Tamaño y fiabilidad

Importante tenerlo en cuenta para todas las geovallas que se utilizan en la monitorización de regiones desde una aplicación móvil, independientemente de si utiliza Adobe o algún otro servicio. Los sistemas operativos recomiendan algunos parámetros que se deben tener en cuenta al crear geovallas. Para lograr la máxima fiabilidad, las geovallas deben tener un radio de al menos 100 metros. Es aceptable crear geoperímetros más pequeños, pero es posible que no se generen eventos de entrada y salida, o que se generen después de que el usuario deje de moverse durante un periodo.

Además, la precisión y la fiabilidad pueden reducirse en función de las condiciones del hardware, como que el wi-fi esté apagado o no disponible, y también en función de la ubicación del dispositivo en relación con la obstrucción de las señales GPS. Por ejemplo, las áreas montañosas, los entornos urbanos y las áreas interiores pueden reducir la precisión de ubicación de los sistemas operativos iOS y Android.

## ¿Cómo entra en déclencheur un evento de salida?

El monitor de región implementado debe solicitar una lista de puntos de interés cercanos. Una vez recibida, se debe registrar una región con el sistema operativo para cada punto de interés. El sistema operativo ahora es responsable de notificar al SDK cuando el dispositivo cruza un límite (entrada o salida) para una de las regiones monitorizadas. SDK solo almacena en déclencheur un evento de salida cuando el sistema operativo notifica a SDK de que se ha producido el evento. El motivo principal de esta notificación es la distinción de tiempo de los datos de ubicación.

Si el sistema operativo no puede entregar un evento de salida cuando el dispositivo abandona una región, es más seguro para SDK omitir simplemente el evento de salida. Si SDK fabrica un evento de salida sin que el sistema operativo active el evento, existe el riesgo de que el evento de salida se procese mucho más allá del período de tiempo durante el cual el dispositivo estuvo cerca del punto de interés.

## Número de puntos de interés

En la interfaz de administración de puntos de interés del servicio de Places, los clientes pueden añadir hasta 150 000 puntos de interés en una biblioteca específica. Los clientes pueden definir varias bibliotecas para segmentar las agrupaciones de puntos de interés si lo desean.

## Algunas notas sobre el cambio de ubicación y la monitorización activa de la región

La monitorización de una región geográfica comienza inmediatamente después del registro para aplicaciones autorizadas. Sin embargo, no espere recibir un evento de inmediato, ya que solo los cruces fronterizos generan un evento. En concreto, si la ubicación del usuario ya está dentro de la región en el momento del registro, el administrador de ubicaciones no genera automáticamente un evento. En su lugar, la aplicación debe esperar a que el usuario cruce el límite de la región para que se genere un evento y se envíe al delegado.

Tenga cuidado al especificar el conjunto de regiones que desea supervisar. Las regiones son un recurso compartido del sistema y el número total de regiones disponibles en todo el sistema es limitado. Por este motivo, la ubicación principal limita a 20 el número de regiones que una sola aplicación puede monitorizar simultáneamente. Para solucionar este límite, considere la posibilidad de registrar solo aquellas regiones en las inmediaciones del usuario.

[Vea información adicional en el sitio para desarrolladores de Apple] (https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/LocationAwarenessPG/RegionMonitoring/RegionMonitoring.html#//apple_ref/doc/uid/TP40009497-CH9-SW11)
