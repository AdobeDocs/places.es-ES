---
title: Eliminar un POI
description: Eliminar un punto de interés mediante las API de REST de Places.
exl-id: 0325eb3b-f9b2-4b21-bed8-e318e8072a69
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '44'
ht-degree: 9%

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
>Reemplazar `<POIID>`, `<API KEY>`, `<TOKEN>`, y `<ORGID>` con valores reales.
