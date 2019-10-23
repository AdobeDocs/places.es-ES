---
title: Referencia de eventos de lugares
seo-title: Referencia de eventos de lugares
description: 'Lista de los eventos que gestiona la extensión Places. '
seo-description: 'Lista de los eventos que gestiona la extensión Places.  '
translation-type: tm+mt
source-git-commit: ef720c112bc0de386e070094629c5bab69938e76

---


# Referencia de eventos de lugares {#places-event-reference}

Esta es una lista de los eventos que gestiona la extensión Places.

## GetCurrentPointsOfInterest

**Detalles del evento**

| Tipo | Fuente | Nombre | Emparejados |
| :--- | :--- | :--- | :--- |
| LUGARES | REQUEST_CONTENT | `requestgetuserwithinplaces` | True |

**Descripción del evento**

Este evento es una solicitud para recuperar los puntos de interés en los que se encuentra el dispositivo.

**Definición de carga de datos**

n.d.

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
| latitude | double | true | n.d. | Contiene el valor de latitud del centro de la búsqueda de puntos de interés cercanos. |
| longitud | double | true | n.d. | Contiene el valor de longitud del centro de la búsqueda de puntos de interés cercanos. |
| radio | integer | false | n.d. | Radio, en metros, utilizado por la búsqueda de puntos de interés cercanos. |
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
| regioneventtype | int | true | Tipo de evento de región que se está generando. 1 para la entrada y 2 para la salida. |

## Eventos enviados por la extensión Places

Esta información está en curso.

