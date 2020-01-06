---
title: Encabezados y parámetros
description: Encabezados y parámetros disponibles en las API de REST de Places.
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Encabezados y parámetros {#headers-and-parameters}

A continuación se proporcionan detalles sobre los encabezados y parámetros disponibles en la API de REST de lugares:

## Encabezados admitidos

| Encabezado | Descripción | Método | Ejemplo |
| :--- | :--- | :--- | :--- |
| `Authorization` | Su token portador | Todas |  |
| `x-api-key` | Su clave de API | Todas | `19776964b4cde49e08d8f62e5824f777b` |
| `x-gw-ims-org-id` | Su ID de organización | Todas | `18FB61145BAC2FFB0A494777@AdobeOrg` |
| `Content-Type` | Formato del contenido enviado o recibido | PUT, POST | `application/json` |
| `Accept-Language` | Lenguaje utilizado para mensajes de error | Opcional | `en-US` |

## Parámetros de biblioteca

| Parámetro | Descripción | Tipo | Límite | Solicitud o respuesta | Ejemplo |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `id` | ID de la biblioteca | asignado | n.d. | Respuesta | `"id": "b2488788-2d2a-462b-b1a2-305272777dda"` |
| `name` | Nombre de la biblioteca | string | 256 caracteres | ambos, requeridos en la solicitud | `"name": "Amazing Places"` |
| `orgID` | ID de organización de Experience Cloud de la organización | asignado | n.d. | Respuesta | `"orgID": "777F20F55BACA09E0A495D8F@AdobeOrg"` |
| `poiCount` | Número de puntos de interés de la biblioteca | integer | 150.000 máx. | Respuesta | `"poiCount": 25149` |
| `metadataDescriptors` | Recuento para cada par de valor clave de metadatos de punto de interés único | mixto | n.d. | Respuesta |  |
| `poiCountInCities` | Recuento para cada valor de ciudad de punto de interés único | mixto | n.d. | Respuesta |  |

## Parámetros de POI

| Parámetro | Descripción | Tipo | Límite | Solicitud o respuesta | Ejemplo |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `data` | Datos de anuncio | Matriz de detalles de puntos de interés | n.d. | both |  |
| `id` | ID del punto de interés | asignado | n.d. | response | `"id": "1455462b-7f9c-4220-9f42-5bbce777a0d1"` |
| `name` | Nombre del punto de interés | string | 512 caracteres | ambos, opcional\* | `"name": "My Favorite Place"` |
| `description` | Descripción del punto de interés | string | 512 caracteres | ambos, opcional\* | `"description": "This is a very good place."` |
| `location` | Matriz de tipos y coordenadas de puntos de interés | matriz (mixto) | n.d. | both | `"location": {"type": "Point", "coordinates": [-122.201007, 37.604713]` |
| `type` | Tipo de POI | string | solo se admite actualmente &quot;Point&quot; | ambos, requeridos en la solicitud | `"type": "Point"` |
| `coordinates` | Matriz de longitud y latitud del punto de interés | array (float) | longitud: -180 a 180, latitud -85 a 85 | ambos, requeridos en la solicitud | `"coordinates": [-122.201007, 37.604713]` |
| `radius` | Tamaño de la geofencia circular alrededor del punto de interés | float | 10 - 2000 metros | ambos, requeridos en la solicitud | `"radius": 100` |
| `country` | País para el punto de interés | string | 32 caracteres | ambos, opcional* | `"country": "United States"` |
| `state` | Estado del índice de precios de consumo | string | 32 caracteres | ambos, opcional* | `"state": "California"` |
| `city` | Ciudad para el punto de interés | string | 32 caracteres | ambos, opcional* | `"city": "San Jose"` |
| `street` | Dirección de la calle del punto de interés | string | 256 caracteres | ambos, opcional* | `"street": "122 Woz Way"` |
| `category` | Categoría del punto de interés | string | 100 caracteres | ambos, opcional* | `"category": "cafe"` |
| `icon` | Icono para el punto de interés | string | 50 caracteres | ambos, opcional* | `"icon": "star"` |
| `color` | Color del punto de interés | string | 8 caracteres | ambos, opcional* | `"color": "blue"` |
| `metadata` | Matriz de pares clave/valor para el punto de interés | array(string) | key: 256 caracteres, valor: 256 caracteres, máximo de 10 pares | ambos, opcional* | `"metadata": {"region": "Equator"}` |
| `lib_id` | ID de la biblioteca en la que está el punto de interés | n.d. | n.d. | ambas, requerido | `"lib_id": "ac7a0b25-c6c2-43ba-bbc6-2b1777b80fe9"` |

* Si no se incluye el valor del parámetro, el valor se establece `empty` en la base de datos. Si no se incluye el par clave/valor existente, el par clave/valor se elimina para ese punto de interés en la base de datos.

