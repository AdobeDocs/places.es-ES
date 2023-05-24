---
title: Información general
description: Explicación y uso de las API de consulta.
exl-id: cc61a49c-1cf2-407f-b81a-3d38fcb622cc
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 3%

---

# API de consulta

Método de GET que le permite consultar los puntos de interés más cercanos al llamador.

## Solicitud

```text
GET https://query.places.adobe.com/placesedgequery
```

Con la siguiente entrada, el servicio devuelve una lista de los puntos de interés más cercanos al llamador:

* La posición de quien llama (latitud, longitud).
* Los ID de las bibliotecas de PDI que se incluirán en la búsqueda.
* Número máximo de puntos de interés que se van a devolver.  El valor predeterminado es 100.

   La distancia entre el autor de la llamada y el punto de interés se define como la distancia desde el autor de la llamada hasta el borde de la geovalla del punto de interés. En la respuesta, los puntos de interés que contienen al llamador se marcan como teniendo al llamador.

Los argumentos se proporcionan como los siguientes parámetros de consulta:

* (**Requerido**) `latitude`

   Latitud del llamador, que debe estar entre -85 y 85.
* (**Requerido**) `longitude`

   Longitud del llamador, que debe estar entre -180 y 180.

* (**Opcional**) `limit`

   Número máximo de puntos de interés que se van a devolver.

* (**Requerido**) `library`

   El ID de la biblioteca que se va a consultar. Para consultar varias bibliotecas, asegúrese de incluir varias copias del parámetro de biblioteca en la consulta.

Este es un ejemplo del formato JSON devuelto correctamente:

```markup
{
    "places": {
        "userWithin": [
            {
                "p": [
                    "poi id",
                    "poi name",
                    "poi center's latitude",
                    "poi center's longitude",
                    poiRadius,
                    rank
                ],
                "x": {
                    "country": "US",
                    "city": "Fremont",
                    "street": "Vineyard Heights",
                    "Color": "Blue",
                    "state": "CA",
                    <other POI metadata>
                }
            }
        ],
        "pois": [
            {
                "p": [
                    "poi id",
                    "poi name",
                    "poi center's latitude",
                    "poi center's longitude",
                    poiRadius,
                    rank
                ],
                "x": {
                    "country": "US",
                    "city": "Milpitas",
                    "street": null,
                    "state": "CA"
                }
            },
            {
                "p": [
                    "poi id",
                    "poi name",
                    "poi center's latitude",
                    "poi center's longitude",
                    poiRadius,
                    rank
                ],
                "x": {
                    "country": "US",
                    "city": "Fremont",
                    "street": null,
                    "state": "CA"
                }
            }
        ]
    }
}
```

Puntos de interés en `places.pois` se ordenan por la distancia desde el llamador hasta el borde de los puntos de interés. Puntos de interés en `places.userWithin` contiene el llamador, y estos puntos de interés se ordenan por rango y luego por radio creciente.

## Llamada de ejemplo

A continuación, se muestra un ejemplo de la llamada de:

```text
GET https://query.places.adobe.com/placesedgequery?latitude=<userLatitude>&longitude=<userLongitude>&library=<libID1>&library=<libID2>&limit=20
```
