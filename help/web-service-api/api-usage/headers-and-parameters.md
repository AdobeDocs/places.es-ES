---
title: Encabezados y parámetros
description: Encabezados y parámetros disponibles en las API de REST del servicio Places.
exl-id: 3c7e76de-f0ff-4966-a3ec-7f64d819c140
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 19%

---

# Encabezados y parámetros {#headers-and-parameters}

Estos son los detalles sobre los encabezados y los parámetros disponibles en la API de REST del servicio Places:

## Encabezados admitidos

| Encabezado | Descripción | Método | Ejemplo |
| :--- | :--- | :--- | :--- |
| `Authorization` | Su token de portador | Todas |  |
| `x-api-key` | Su clave de API | Todas | `19776964b4cde49e08d8f62e5824f777b` |
| `x-gw-ims-org-id` | Su ID de organización | Todas | `18FB61145BAC2FFB0A494777@AdobeOrg` |
| `Content-Type` | Formato del contenido enviado o recibido | PUT, POST | `application/json` |
| `Accept-Language` | Idioma utilizado para los mensajes de error | Opcional | `en-US` |

## Parámetros de biblioteca

| Parámetro | Descripción | Tipo | Límite | Solicitud o respuesta | Ejemplo |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `id` | ID de biblioteca | asignado | n/a | Respuesta | `"id": "b2488788-2d2a-462b-b1a2-305272777dda"` |
| `name` | Nombre de la biblioteca | cadena | 256 caracteres | ambos, requeridos en la solicitud | `"name": "Amazing Places"` |
| `orgID` | ID de organización de Experience Cloud de la organización | asignado | n/a | Respuesta | `"orgID": "777F20F55BACA09E0A495D8F@AdobeOrg"` |
| `poiCount` | Número de puntos de interés en la biblioteca | entero | 150.000 máx. | Respuesta | `"poiCount": 25149` |
| `metadataDescriptors` | Recuento de cada par de valor clave y metadatos de punto de interés único | mixto | n/a | Respuesta |  |
| `poiCountInCities` | Recuento de cada valor de ciudad de punto de interés único | mixto | n/a | Respuesta |  |

## Parámetros de PDI

| Parámetro | Descripción | Tipo | Límite | Solicitud o respuesta | Ejemplo |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `data` | Datos del PDI | Matriz de detalles del PDI | n/a | ambos |  |
| `id` | ID del PDI | asignado | n/a | respuesta | `"id": "1455462b-7f9c-4220-9f42-5bbce777a0d1"` |
| `name` | Nombre del PDI | cadena | 512 caracteres | ambos, opcional\* | `"name": "My Favorite Place"` |
| `description` | Descripción del PDI | cadena | 512 caracteres | ambos, opcional\* | `"description": "This is a very good place."` |
| `location` | Matriz de tipo y coordenadas de punto de interés | matriz (mixta) | n/a | ambos | `"location": {"type": "Point", "coordinates": [-122.201007, 37.604713]` |
| `type` | Tipo de PDI | cadena | solo se admite actualmente &quot;Point&quot; | ambos, requeridos en la solicitud | `"type": "Point"` |
| `coordinates` | Matriz de longitud y latitud del punto de interés | matriz (flotante) | longitud: de -180 a 180, latitud: de -85 a 85 | ambos, requeridos en la solicitud | `"coordinates": [-122.201007, 37.604713]` |
| `radius` | Tamaño de la geovalla circular alrededor del PDI | flotante | 10 - 2000 metros | ambos, requeridos en la solicitud | `"radius": 100` |
| `country` | País para el PDI | cadena | 32 caracteres | ambos, opcionales* | `"country": "United States"` |
| `state` | Estado del PDI | cadena | 32 caracteres | ambos, opcionales* | `"state": "California"` |
| `city` | Ciudad para el PDI | cadena | 32 caracteres | ambos, opcionales* | `"city": "San Jose"` |
| `street` | Dirección de la calle del PDI | cadena | 256 caracteres | ambos, opcionales* | `"street": "122 Woz Way"` |
| `category` | Categoría del PDI | cadena | 100 caracteres | ambos, opcionales* | `"category": "cafe"` |
| `icon` | Icono del POI | cadena | 50 caracteres | ambos, opcionales* | `"icon": "star"` |
| `color` | Color del punto de interés | cadena | 8 caracteres | ambos, opcionales* | `"color": "blue"` |
| `metadata` | Matriz de pares de clave/valor para el PDI | array(cadena) | clave: 256 caracteres, valor: 256 caracteres, máximo de 10 pares | ambos, opcionales* | `"metadata": {"region": "Equator"}` |
| `lib_id` | ID de la biblioteca en la que se encuentra el punto de interés | n/a | n/a | ambos, obligatorio | `"lib_id": "ac7a0b25-c6c2-43ba-bbc6-2b1777b80fe9"` |

* Si no se incluye el valor del parámetro, el valor se establece en `empty` en la base de datos. Si no se incluye el par clave/valor existente, se elimina el par clave/valor para ese punto de interés de la base de datos.
