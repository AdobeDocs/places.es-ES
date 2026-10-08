---
title: Referencia de evento de Places
description: Una lista de los eventos que gestiona la extensión Places.
feature: Mobile SDK
exl-id: 98210ef4-5ff1-4792-b97b-2845ce02e78a
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
  - id: a8a79b8d-fdca-499c-a5ef-f88a099d8eb9
    internal-label: Mobile SDK
source-git-commit: d8704da9c84a066f72471421290d4b46c65f41e1
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 17%
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
| latitude | doble | verdadero | n/a | Contiene el valor de latitud del centro de la búsqueda de puntos de interés cercanos. |
| longitud | doble | verdadero | n/a | Contiene el valor de longitud del centro de la búsqueda de puntos de interés cercanos. |
| radio | entero | falso | n/a | Radio, en metros, utilizado por la búsqueda de puntos de interés cercanos. |
| recuento | entero | falso | 10 | Número máximo de puntos de interés que se devolverán en el evento de respuesta resultante. |

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
| regionid | cadena | verdadero | ID de la región que genera el evento. |
| regioneventtype | int | verdadero | Tipo de evento de región que se genera. 1 para entrada y 2 para salida. |

## Eventos distribuidos por la extensión Places

Esta información está actualmente en curso.
