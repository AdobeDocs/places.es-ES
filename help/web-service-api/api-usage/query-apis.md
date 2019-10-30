---
title: Información general
seo-title: API de consulta
description: Explicación y uso de las API de consulta.
seo-description: Explicación y uso de las API de consulta.
translation-type: tm+mt
source-git-commit: e2070c629b5a4e4bcf3a364023e0f87b526ed4cb

---



# API de consulta

Método GET que permite consultar los puntos de interés más cercanos al llamador.

## Solicitud

```text
GET https://query.places.adobe.com/placesedgequery
```

Con la siguiente entrada, el servicio devuelve una lista de los puntos de interés más cercanos al llamador:

* La posición del llamador \(latitud, longitud\).
* ID de las bibliotecas de puntos de interés que se incluirán en la búsqueda.
* Número máximo de puntos de interés que se van a devolver.  El valor predeterminado es 100.

   La distancia entre el llamante y el punto de interés se define como la distancia desde el llamante hasta el borde de la geofence del punto de interés. En la respuesta, los puntos de interés que contengan el llamador se marcarán como si tuvieran el llamador.

Los argumentos se proporcionan como los siguientes parámetros de consulta:

* (**Requerido**) `latitude`

   La latitud del llamador, que debe estar entre -85 y 85.
* (**Requerido**) `longitude`

   Longitud del llamador, que debe estar entre -180 y 180.

* (**Opcional**) `limit`

   Número máximo de puntos de interés que se van a devolver.

* (**Requerido**) `library`

   ID de la biblioteca que se va a consultar. Para consultar varias bibliotecas, asegúrese de incluir varias copias del parámetro library en la consulta.

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

Los puntos de interés en `places.pois` se ordenan por distancia del llamador al borde de los puntos de interés. Los puntos de interés de debajo `places.userWithin` contienen el llamador y estos puntos de interés se ordenan por clasificación y, a continuación, por radio creciente.

## Llamada de muestra

Este es un ejemplo de la llamada:

```text
GET https://query.places.adobe.com/placesedgequery?latitude=<userLatitude>&longitude=<userLongitude>&library=<libID1>&library=<libID2>&limit=20
```
