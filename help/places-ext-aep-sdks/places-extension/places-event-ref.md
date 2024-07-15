---
title: Referencia de evento de Places
description: Una lista de los eventos que gestiona la extensión Places.
feature: Mobile SDK
exl-id: 98210ef4-5ff1-4792-b97b-2845ce02e78a
source-git-commit: f521d5e3b0b69977877d88382ce41fcb7d1c54b9
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 13%

---

# Referencia de evento de Places {#places-event-reference}

Esta es una lista de los eventos que gestiona la extensión Places.

## GetCurrentPointsOfInterest

**Detalles del evento**

| Tipo | Fuente | Nombre | Emparejado |
| :--- | :--- | :--- | :--- |
| LUGARES | REQUEST_CONTENT | `requestgetuserwithinplaces` | True |

**Descripción del evento**

Este evento es una solicitud para recuperar los puntos de interés en los que se encuentra actualmente el dispositivo.

**Definición de carga de datos**

n/a

## GetNearbyPointsOfInterest

**Detalles del evento**

| Tipo | Fuente | Nombre | Emparejado |
| :--- | :--- | :--- | :--- |
| LUGARES | REQUEST_CONTENT | `requestgetnearbyplaces` | True |

**Descripción del evento**

Este evento es una solicitud para obtener los puntos de interés cercanos teniendo en cuenta la ubicación actual del dispositivo y las bibliotecas de Places configuradas.

**Definición de carga de datos**

| Clave | Tipo de valor | Requerido | Valor predeterminado | Descripción |
| :--- | :--- | :--- | :--- | :--- |
| latitude | doble | true | n/a | Contiene el valor de latitud del centro de la búsqueda de puntos de interés cercanos. |
| longitud | doble | true | n/a | Contiene el valor de longitud del centro de la búsqueda de puntos de interés cercanos. |
| radio | entero | false | n/a | Radio, en metros, utilizado por la búsqueda de puntos de interés cercanos. |
| recuento | entero | false | 10 | Número máximo de puntos de interés que se devolverán en el evento de respuesta resultante. |

## ProcessRegionEvent

**Detalles del evento**

| Tipo | Fuente | Nombre | Emparejado |
| :--- | :--- | :--- | :--- |
| LUGARES | REQUEST_CONTENT | `requestprocessregionevent` | False |

**Descripción del evento**

Este evento hace que la extensión Places procese un evento de entrada o salida de geovalla.

**Definición de carga de datos**

| Clave | Tipo de valor | Requerido | Descripción |
| :--- | :--- | :--- | :--- |
| regionid | cadena | true | ID de la región que genera el evento. |
| regioneventtype | int | true | Tipo de evento de región que se genera. 1 para entrada y 2 para salida. |

## Eventos distribuidos por la extensión Places

Esta información está actualmente en curso.
