---
title: Eliminar un punto de interés
seo-title: Eliminar un punto de interés
description: Elimine un punto de interés mediante las API de Places REST.
seo-description: Elimine un punto de interés mediante las API de Places REST.
translation-type: tm+mt
source-git-commit: ef3d77eba407013e1f701ed001ef9ab7b3818e07

---


# Eliminar un punto de interés

Método DELETE que permite eliminar un punto de interés.

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
>Reemplazar `<POIID>`, `<API KEY>`, `<TOKEN>`y `<ORGID>` por valores reales.

