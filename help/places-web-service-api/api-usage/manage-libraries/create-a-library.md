---
title: Crear una biblioteca
seo-title: Crear una biblioteca
description: Cree una biblioteca mediante la API de REST de lugares.
seo-description: Cree una biblioteca mediante la API de REST de lugares.
translation-type: tm+mt
source-git-commit: 26b0cab7bdada26a7598b20623095b72f7c8d334

---


# Crear una biblioteca

Método POST que permite crear una biblioteca.

## Solicitud

```text
POST https://api-places.adobe.io/places/placesapi/v1/libraries
```

## Encabezados

```text
-H' Content-Type: application/json'  -H 'Authorization: Bearer <TOKEN>'  -H 'x-api-key: <API KEY>'  -H 'x-gw-ims-org-id: <ORGID>'  -H 'Accept-Language: en-US'
```

## Cuerpo

```text
{"name": "<LIBRARY_NAME>"}
```

## Respuesta de ejemplo

```text
{       "id": "449f08f3-eff5-4658-9329-2d9687af777e",       "name": "Facinating places",      "customerID": "777F20F55BACA09E0A495D8F@AdobeOrg",       "poiCount": 0  }
```

## CURL, comando

Utilice el siguiente comando CURL para probar esta API:

```text
curl -X POST 'https://api-places.adobe.io/places/placesapi/v1/libraries' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' -d '{"name":"New Library Name"}' -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>Reemplazar variables como `<API KEY>`, `<TOKEN>`, y `<ORGID>` con valores reales.

