---
title: Coloca la referencia del evento
description: 'Lista de los eventos que gestiona la extensión Places. '
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 24%

---


# Coloca la referencia del evento {#places-event-reference}

Esta es una lista de los eventos que gestiona la extensión Places.

## GetCurrentPointsOfInterest

**Detalles del evento**

| Tipo | Fuente | Nombre | Emparejados |
| :--- | :--- | :--- | :--- |
| LUGARES | REQUEST_CONTENT | `requestgetuserwithinplaces` | True |

**Descripción del evento**

Este evento es una solicitud para recuperar los puntos de interés en los que se encuentra actualmente el dispositivo.

**Definición de carga de datos**

n/a

## GetNearbyPointsOfInterest

**Detalles del evento**

| Tipo | Fuente | Nombre | Emparejados |
| :--- | :--- | :--- | :--- |
| LUGARES | REQUEST_CONTENT | `requestgetnearbyplaces` | True |

**Descripción del evento**

Este evento es una solicitud para obtener los puntos de interés cercanos teniendo en cuenta la ubicación actual del dispositivo y las bibliotecas de lugares configuradas.

**Definición de carga de datos**

| Clave | Tipo de valor | Requerido | Valor predeterminado | Descripción |
| :--- | :--- | :--- | :--- | :--- |
| latitude | doble | true | n/a | Contiene el valor de latitud para el centro de la búsqueda de puntos de interés cercanos. |
| longitude | doble | true | n/a | Contiene el valor de longitud del centro de la búsqueda de puntos de interés cercanos. |
| radio | integer | false | n/a | Radio, en metros, utilizado por la búsqueda de puntos de interés cercanos. |
| count | integer | false | 10 | Número máximo de puntos de interés que se devuelven en el evento de respuesta resultante. |

## ProcessRegionEvent

**Detalles del evento**

| Tipo | Fuente | Nombre | Emparejados |
| :--- | :--- | :--- | :--- |
| LUGARES | REQUEST_CONTENT | `requestprocessregionevent` | False |

**Descripción del evento**

Este evento hace que la extensión Places procese un evento de entrada o salida de geofence.

**Definición de carga de datos**

| Clave | Tipo de valor | Requerido | Descripción |
| :--- | :--- | :--- | :--- |
| regionid | string | true | ID de la región que genera el evento. |
| regioneventtype | int | true | Tipo de evento de región que se genera. 1 para la entrada y 2 para la salida. |

## Eventos enviados por la extensión Places

Esta información está en curso.

