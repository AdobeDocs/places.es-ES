---
title: Eliminar una biblioteca
description: Eliminar una biblioteca mediante las API de REST de Places.
exl-id: ad45ea38-9e12-43d7-b05f-17d3e40abaf5
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: d8704da9c84a066f72471421290d4b46c65f41e1
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 4%
---
# Eliminar una biblioteca {#delete-a-library}

Método de DELETE que permite eliminar una biblioteca.

## Solicitud

```text
DELETE https://api-places.adobe.io/places/placesapi/v1/libraries/<lIBRARYID>
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

Utilice el siguiente comando CURL para probar esta API:

```text
curl -X DELETE 'https://api-places.adobe.io/places/placesapi/v1/libraries/<LIBRARYID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>Reemplace variables como `<lIBRARYID>`, `<API KEY>`, `<TOKEN>` y `<ORGID>`con valores reales.
