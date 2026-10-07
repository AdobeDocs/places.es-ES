---
title: Eliminar un POI
description: Eliminar un punto de interés mediante las API de REST de Places.
exl-id: 0325eb3b-f9b2-4b21-bed8-e318e8072a69
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: d8704da9c84a066f72471421290d4b46c65f41e1
workflow-type: tm+mt
source-wordcount: '44'
ht-degree: 4%
---
# Eliminar un POI {#delete-a-poi}

Método de DELETE que permite eliminar un punto de interés (POI).

## Solicitud

```text
DELETE https://api-places.adobe.io/places/placesapi/v1/pois/<POIID>
```

## Encabezados

```text
-H' Content-Type: application/json'  
-H 'Authorization: Bearer <TOKEN>'  
-H 'x-api-key: <API KEY>'  
-H 'x-gw-ims-org-id: <ORGID>'  
-H 'Accept-Language: en-US'
```

## Respuesta de ejemplo

```text
If successful a Status of "204 No Content" is returned.
```

## CURL, comando

Utilice el siguiente comando CURL para probar la API:

```text
curl -X DELETE 'https://api-places.adobe.io/places/placesapi/v1/pois/<POIID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>Reemplazar `<POIID>`, `<API KEY>`, `<TOKEN>` y `<ORGID>` con valores reales.
