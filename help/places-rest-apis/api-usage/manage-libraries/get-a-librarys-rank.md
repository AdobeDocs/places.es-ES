---
title: Obtener la clasificación de una biblioteca
seo-title: Obtener la clasificación de una biblioteca
description: Obtenga la clasificación de una biblioteca mediante la API de REST de lugares.
seo-description: Obtenga la clasificación de una biblioteca mediante la API de REST de lugares.
translation-type: tm+mt
source-git-commit: ef3d77eba407013e1f701ed001ef9ab7b3818e07

---


# Obtener la clasificación de una biblioteca

Método GET que permite clasificar las bibliotecas.

## Solicitud

`GET https://api-places.adobe.io/places/placesapi/v1/libraries/rank`

## Encabezados

```
-H Content-Type: application/JSON  
-H 'Authorization: Bearer <TOKEN>'  
-H 'x-api-key: <API KEY>'  
-H 'x-gw-ims-org-id: <ORGID>'  
-H 'Accept-Language: en-US'
```

## Respuesta de ejemplo

```
{"library_rank_order":["ea45781f-26af-44b1-b4f8-43baf5f0fe28","dfcc5270-1d6d-4bc9-9cd9-85ecd5ebc12b"]}
```

## CURL, comando

```
curl -X GET 'https://api-places.adobe.io/places/placesapi/v1/libraries/rank ' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>Reemplazar variables como `<API KEY>`, `<TOKEN>`, y `<ORGID>` con valores reales.
