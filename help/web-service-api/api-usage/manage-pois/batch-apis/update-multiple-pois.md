---
title: Actualizar varios puntos de interés
description: Utilice las API por lotes para actualizar varios puntos de interés.
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2
workflow-type: tm+mt
source-wordcount: '56'
ht-degree: 5%

---


# Actualizar varios puntos de interés {#update-multiple-pois}

Un método POST que permite actualizar varios puntos de interés.

## Solicitud

```text
POST https://api-places.adobe.io/places/placesapi/v1/pois/batchUpdate
```

## Encabezados

```text
-H' Content-Type: application/json'  -H 'Authorization: Bearer <TOKEN>'  -H 'x-api-key: <API KEY>'  -H 'x-gw-ims-org-id: <ORGID>'  -H 'Accept-Language: en-US'
```

## Cuerpo

```text
{    "updates": [        {            "id": "<POIID>,            ""lib_id": "<lIBRARYID>",            "name": "string",            "description": "string",            "location": {                "type": "Point",                "coordinates": [<LONGITUDE>, <LATITUDE>]            },            "radius": integer,            "country": "string",            "state": "string",            "city": "string",            "street": "string",            "category": "string",            "icon": "string",            "color": "string",            "metadata": {                "ownership": "string",                "brand": "string"            }        },        {            "id": "<POIID>,            "lib_id": "<lIBRARYID>",            "name": "string",            "description": "string",            "location": {                "type": "Point",                "coordinates": [<LONGITUDE>, <LATITUDE>]            },            "radius": integer,            "country": "string",            "state": "string",            "city": "string",            "street": "string",            "category": "string",            "icon": "string",            "color": "string",            "metadata": {                "ownership": "string",                "brand": "string"            }        },        .        .        .        {            "id": "<POIID>,            "lib_id": "<lIBRARYID>",            "name": "string",            "description": "string",            "location": {                "type": "Point",                "coordinates": [<LONGITUDE>, <LATITUDE>]            },            "radius": integer,            "country": "string",            "state": "string",            "city": "string",            "street": "string",            "category": "string",            "icon": "string",            "color": "string",            "metadata": {                "ownership": "string",                "brand": "string"            }        },        {            "id": "<POIID>,            "lib_id": "<lIBRARYID>",            "name": "string",            "description": "string",            "location": {                "type": "Point",                "coordinates": [<LONGITUDE>, <LATITUDE>]            },            "radius": integer,            "country": "string",            "state": "string",            "city": "string",            "street": "string",            "category": "string",            "icon": "string",            "color": "string",            "metadata": {                "ownership": "string",                "brand": "string"            }        }    ]}
```

## Respuesta de ejemplo

```text
{    "ids": [        "558360b5-5b4b-4c8a-777f-5e3f4b60e4cb",        "ac01c21c-6274-4922-86d5-7777b59dc9b0",        .        .        .        "acf0fde0-22ee-470a-bfa9-b760777cefdc",        "d3cf8338-520f-49a5-8ee7-3777df69be91"    ],    "_links": {        "pois": {            "href": "https://api-places-dev.adobe.io/places/placesapi/v1/pois/{poi_id}",            "templated": true        }    }}
```

## CURL, comando

Utilice el siguiente comando CURL para probar la API:

```text
curl -X POST 'https://api-places.adobe.io/places/placesapi/v1/pois/batchUpdate' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' --data-binary "@<PATHTOBATCHUPDATEJSONFILE>" -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>Reemplazar `<API KEY>`, `<TOKEN>`, `<ORGID>`y `<PATHTOBATCHUPDATEJSONFILE>` con valores reales.

## Archivo JSON de muestra

Este es el archivo JSON de muestra para la `batchUpdate` API:

```text
updates":[{"id":"31a49d5c-c6ad-46ae-b88d-a6912a8a6b2f","name":"Updated POI 1","description":"1","location":{"type":"Point","coordinates":[0.0000000,0.0000000]},"radius":25.0,"country":"Ghana","state":"Ghana","city":"Accra","street":"","category":"cafe","icon":"nice","color":"red","metadata":{"region":"Equator"},"lib_id":"42b4d03c-672c-4deb-83e0-134ef070c2af"},{"id":"6a78a729-7973-4373-9199-36da18cc5b8c","name":"Updated POI 2","description":"2","location":{"type":"Point","coordinates":[0.0250000,0.0250000]},"radius":50.0,"country":"Ghana","state":"Ghana","city":"Accra","street":"","category":"cafe","icon":"nice","color":"red","metadata":{"region":"Equator"},"lib_id":"42b4d03c-672c-4deb-83e0-134ef070c2af"},{"id":"74eaa3da-2464-4298-9b6d-5376fa7ea00f","name":"Updated POI 3","description":"3","location":{"type":"Point","coordinates":[0.0500000,0.0500000]},"radius":100.0,"country":"Ghana","state":"Ghana","city":"Accra","street":"","category":"cafe","icon":"nice","color":"red","metadata":{"region":"Equator"},"lib_id":"42b4d03c-672c-4deb-83e0-134ef070c2af"}]}
```
