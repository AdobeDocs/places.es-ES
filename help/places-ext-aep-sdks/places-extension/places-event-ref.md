---
title: Referencia de evento de Places
description: Una lista de los eventos que gestiona la extensión Places.
exl-id: 98210ef4-5ff1-4792-b97b-2845ce02e78a
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 28%

---

# Referencia de evento de Places {#places-event-reference}

Esta es una lista de los eventos que gestiona la extensión Places.

## GetCurrentPointsOfInterest

**Detalles del evento**

| Tipo | Fuente | Nombre | Emparejados |
| :--- | :--- | :--- | :--- |
| LUGARES | REQUEST_CONTENT | `requestgetuserwithinplaces` | True |

**Descripción del evento**

Este evento es una solicitud para recuperar los puntos de interés en los que se encuentra actualmente el dispositivo.

**Definición de carga de datos**

N/D

## GetNearbyPointsOfInterest

**Detalles del evento**

| Tipo | Fuente | Nombre | Emparejados |
| :--- | :--- | :--- | :--- |
| LUGARES | REQUEST_CONTENT | `requestgetnearbyplaces` | True |

**Descripción del evento**

Este evento es una solicitud para obtener los puntos de interés cercanos teniendo en cuenta la ubicación actual del dispositivo y las bibliotecas de Places configuradas.

**Definición de carga de datos**

| Clave | Tipo de valor | Requerido | Valor predeterminado | Descripción |
| :--- | :--- | :--- | :--- | :--- |
| latitude | doble | true | N/D | Contiene el valor de latitud del centro de la búsqueda de puntos de interés cercanos. |
| longitude | doble | true | N/D | Contiene el valor de longitud del centro de la búsqueda de puntos de interés cercanos. |
| radio | entero | false | N/D | Radio, en metros, utilizado por la búsqueda de puntos de interés cercanos. |
| count | entero | false | 10 | Número máximo de puntos de interés que se devolverán en el evento de respuesta resultante. |

## ProcessRegionEvent

**Detalles del evento**

| Tipo | Fuente | Nombre | Emparejados |
| :--- | :--- | :--- | :--- |
| LUGARES | REQUEST_CONTENT | `requestprocessregionevent` | False |

**Descripción del evento**

Este evento hace que la extensión Places procese un evento de entrada o salida de geovalla.

**Definición de carga de datos**

| Clave | Tipo de valor | Requerido | Descripción |
| :--- | :--- | :--- | :--- |
| regionid | string | true | ID de la región que genera el evento. |
| regioneventtype | int | true | Tipo de evento de región que se genera. 1 para entrada y 2 para salida. |

## Eventos distribuidos por la extensión Places

Esta información está actualmente en curso.
