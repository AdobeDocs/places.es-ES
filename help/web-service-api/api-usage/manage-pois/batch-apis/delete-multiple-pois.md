---
title: Eliminar varios POI
description: Utilice las API por lotes para eliminar varios puntos de interés.
exl-id: f170b722-e6f4-42a2-b3a6-1bf56965eb17
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: d8704da9c84a066f72471421290d4b46c65f41e1
workflow-type: tm+mt
source-wordcount: '56'
ht-degree: 5%
---
# Eliminar varios POI {#delete-multiple-pois}

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
>Reemplazar `<API KEY>`, `<TOKEN>`, `<ORGID>` y `<PATHTOBATCHDELETEJSONFILE>` por valores reales.

## Archivo JSON de muestra

Este es un ejemplo de archivo JSON para la API `batchDelete`:

```text
{​"ids":["31a49d5c-c6ad-46ae-b88d-a6912a8a6b2f","6a78a729-7973-4373-9199-36da18cc5b8c","74eaa3da-2464-4298-9b6d-5376fa7ea00f"]​}
```
