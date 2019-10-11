---
title: Actualizar una biblioteca
seo-title: Actualizar una biblioteca
description: Actualice una biblioteca mediante la API de REST de lugares.
seo-description: Actualice una biblioteca mediante la API de REST de lugares.
translation-type: tm+mt
source-git-commit: ef3d77eba407013e1f701ed001ef9ab7b3818e07

---


# Actualizar una biblioteca

Método PUT que permite actualizar una biblioteca.

## Solicitud

```text
PUT https://api-places.adobe.io/places/placesapi/v1/libraries/<lIBRARYID>
```

## Encabezados

```text
-H' Content-Type: application/json'  -H 'Authorization: bearer <TOKEN>'  -H 'x-api-key: <API KEY>'  -H 'x-gw-ims-org-id: <ORGID>'  -H 'Accept-Language: en-US'
```

## Cuerpo

```text
{"name": "<NEW_LIBRARY_NAME>"}
```

## Respuesta de ejemplo

```text
{       "id": "449f08f3-eff5-4658-9329-2d9687af777e",       "name": "Really facinating places",      "customerID": "777F20F55BACA09E0A495D8F@AdobeOrg",       "poiCount": 0  }
```

## CURL, comando

Utilice el siguiente comando CURL para probar esta API:

```text
curl -X PUT 'https://api-places.adobe.io/places/placesapi/v1/libraries/<LIBRARYID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' -d '{"name":"Updated Library Name"}' -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>Reemplazar variables como `<lIBRARYID>`, `<API KEY>`, `<TOKEN>`y `<ORGID>` por valores reales.

