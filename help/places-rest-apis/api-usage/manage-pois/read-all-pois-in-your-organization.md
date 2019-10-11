---
title: Leer todos los puntos de interés de su organización
seo-title: Leer todos los puntos de interés de su organización
description: Lea todos los puntos de interés de su organización mediante las API de Places REST.
seo-description: Lea todos los puntos de interés de su organización mediante las API de Places REST.
translation-type: tm+mt
source-git-commit: ef3d77eba407013e1f701ed001ef9ab7b3818e07

---


# Leer todos los puntos de interés de su organización

Método GET que devuelve todos los puntos de interés de la organización.

## Solicitud

```text
GET https://api-places.adobe.io/places/placesapi/v1/pois
```

## Encabezados

```text
-H' Content-Type: application/json'  -H 'Authorization: Bearer <TOKEN>'  -H 'x-api-key: <API KEY>'  -H 'x-gw-ims-org-id: <ORGID>'  -H 'Accept-Language: en-US'
```

## Respuesta de ejemplo

```text
{    "data": [        {            "id": "66e3c0fb-12fe-4af2-863e-16e0e578d777",            "name": "Train Station Road",            "description": "18827",            "location": {                "type": "Point",                "coordinates": [                    -121.902498,                    37.331087                ]            },            "radius": 66,            "country": "PH",            "state": "41",            "city": "Quezon City",            "street": "No. 10 Train Station Road",            "category": "",            "icon": "",            "color": "",            "metadata": {                "ownership": "LS",                "brand": "Train station"            },            "lib_id": "6efd87bc-c9c4-4ff3-9503-051bfbc81777"        },        {            "id": "8ad7f853-a8d5-4974-8826-73777c91d8b8",            "name": "'Garden Street",            "description": "1013806",            "location": {                "type": "Point",                "coordinates": [                    -121.928548,                    37.333891                ]            },            "radius": 90,            "country": "JP",            "state": "21",            "city": "Gifu",            "street": "42 Garden Street",            "category": "",            "icon": "",            "color": "",            "metadata": {                "ownership": "CO",                "brand": "Gardens"            },            "lib_id": "6efd87bc-c9c4-4ff3-9503-051bfbc81777"        },        .        .        .        {            "id": "e7c2f300-2dc4-46e8-b832-8fd01777cf2e",            "name": "Rifle Road",            "description": "11045",            "location": {                "type": "Point",                "coordinates": [                    -121.950859,                    37.320300                ]            },            "radius": 50,            "country": "US",            "state": "UT",            "city": "Riverdale",            "street": "1140 W Rifle Rd",            "category": "",            "icon": "",            "color": "",            "metadata": {                "ownership": "CO",                "brand": "Westfield"            },            "lib_id": "6efd87bc-c9c4-4ff3-9503-051bfbc81777"        },        {            "id": "04b103e6-bee6-474d-8acf-df7a86781777",            "name": "11400 Sandy Street",            "description": "1006767",            "location": {                "type": "Point",                "coordinates": [                    -122.496794,                    37.495625                ]            },            "radius": 78,            "country": "US",            "state": "UT",            "city": "Sandy",            "street": "26 West 555 Sandy",            "category": "",            "icon": "",            "color": "",            "metadata": {                "ownership": "CO",                "brand": Beach"            },            "lib_id": "6efd87bc-c9c4-4ff3-9503-051bfbc81777"        }    ],    "_page": {        "orderBy": "name",        "page": 1,        "count": 100    },    "_links": {        "next": {            "href": "https://api-places.adobe.io/places/placesapi/v1/pois?orderby=name&limit=100&page=2"        },        "page": {            "href": "https://api-places.adobe.io/places/placesapi/v1/pois{?orderby,limit,page,property}",            "templated": true        }    },    "page_count": 252,    "total_count": 25182}
```

## CURL, comando

Utilice el siguiente comando CURL para probar esta API:

```text
curl -X GET 'https://api-places.adobe.io/places/placesapi/v1/pois' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>Reemplazar `<API KEY>`, `<TOKEN>`y `<ORGID>` por valores reales.