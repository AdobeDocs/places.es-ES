---
title: Eliminar varios puntos de interés
description: Utilice las API por lotes para eliminar varios puntos de interés.
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---



# Eliminar varios puntos de interés {#delete-multiple-pois}

Método POST que permite eliminar varios puntos de interés.

## Solicitud

```text
POST https://api-places.adobe.io/places/placesapi/v1/pois/batchDelete
```

## Encabezados

```text
-H' Content-Type: application/json'  -H 'Authorization: Bearer <TOKEN>'  -H 'x-api-key: <API KEY>'  -H 'x-gw-ims-org-id: <ORGID>'  -H 'Accept-Language: en-US'
```

## Cuerpo

```text
{  "ids": [    "<POIID>",    "<POIID>",    .    .    .    "<POIID>",    "<POIID>"  ]}
```

## Respuesta de ejemplo

```text
If successful a Status of "204 No Content" is returned.
```

## CURL, comando

Utilice el siguiente comando CURL para probar esta API:

```text
curl -X POST 'https://api-places.adobe.io/places/placesapi/v1/pois/batchDelete' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' --data-binary "@<PATHTOBATCHDELETEJSONFILE>" -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>Reemplazar `<API KEY>`, `<TOKEN>`, `<ORGID>`y `<PATHTOBATCHDELETEJSONFILE>` con valores reales.

## Archivo JSON de muestra

Este es el archivo JSON de muestra para la `batchDelete` API:

```text
{​"ids":["31a49d5c-c6ad-46ae-b88d-a6912a8a6b2f","6a78a729-7973-4373-9199-36da18cc5b8c","74eaa3da-2464-4298-9b6d-5376fa7ea00f"]​}
```
