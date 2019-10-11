---
title: Establecer una clasificación en las bibliotecas
seo-title: Establecer una clasificación en las bibliotecas
description: Defina una clasificación en las bibliotecas mediante la API de REST de lugares.
seo-description: Defina una clasificación en las bibliotecas mediante la API de REST de lugares.
translation-type: tm+mt
source-git-commit: ef3d77eba407013e1f701ed001ef9ab7b3818e07

---


# Establecer una clasificación en las bibliotecas

Método PUT que permite definir un orden de clasificación en todas las bibliotecas.

## Solicitud

`PUT https://api-places-dev.adobe.io/places/placesapi/v1/libraries/rank`

## Encabezados

```-H Content-Type: application/json'
-H 'Authorization: Bearer <TOKEN>`  
-H 'x-api-key: <API KEY>'  
-H 'x-gw-ims-org-id: <ORGID>'  
-H 'Accept-Language: en-US'
```

## Datos PUT

```
"library_rank_order": ["dfcc5270-1d6d-4bc9-9cd9-85ecd5ebc12b","ea45781f-26af-44b1-b4f8-43baf5f0fe28"]  
}
```

## Respuesta de ejemplo

```
{"library_rank_order" ["dfcc5270-1d6d-4bc9-9cd9-85ecd5ebc12b","ea45781f-26af-44b1-b4f8-43baf5f0fe28"]}
```

## CURL, comando

```
curl -X PUT 'https://api-places.adobe.io/places/placesapi/v1/libraries/rank' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' -d '{"library_rank_order": ["dfcc5270-1d6d-4bc9-9cd9-85ecd5ebc12b","ea45781f-26af-44b1-b4f8-43baf5f0fe28"]}' -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>Reemplazar variables como `<API KEY>`, `<TOKEN>`, y `<ORGID>` con valores reales.
