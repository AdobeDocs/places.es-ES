---
title: Puntos de interés de carga masiva
seo-title: Puntos de interés de carga masiva
description: Esta sección proporciona información sobre cómo cargar los puntos de interés de forma masiva.
seo-description: Esta sección proporciona información sobre cómo cargar los puntos de interés de forma masiva.
translation-type: tm+mt
source-git-commit: 31462861efa807583c245963d8496eecdd3cf92e

---


# Carga masiva de puntos de interés {#bulk-upload-pois}

Se ha creado un conjunto de secuencias de comandos Python para simplificar la importación por lotes de puntos de interés desde un archivo .csv a una base de datos de puntos de interés mediante las API de servicios Web. Estos scripts se pueden descargar desde esta repo [git](https://github.com/adobe/places-scripts)de código abierto.

Antes de ejecutar estas secuencias de comandos, para acceder a las API de servicio web, consulte Requisitos *previos para el acceso* de los usuarios en la descripción general [de la integración de](/help/web-service-api/adobe-i-o-integration.md)Adobe I/O.

A continuación se proporciona información sobre los scripts:

>[!TIP]
>
>Esta información también se incluye en un archivo léame de la repo [git](https://github.com/adobe/places-scripts).

## CSV

Un archivo .csv de ejemplo `places_sample.csv`, forma parte de este paquete e incluye los encabezados necesarios y una fila de datos de ejemplo. Todos estos encabezados están en minúsculas y corresponden a las claves de metadatos reservadas que se utilizan en la base de datos de lugares. Las columnas que agregue al archivo .csv se agregarán a la base de datos de puntos de interés en una sección de metadatos independiente para cada punto de interés como pares clave/valor, y el valor del encabezado se utilizará como clave.

Esta es una lista de las columnas y los valores que debe utilizar:

* `lib_id`

   ID de biblioteca válido obtenido de la base de datos de puntos de interés.

* `type`

   Actualmente, Point es el único valor válido.

* `longitude`

   Un valor entre -180 y 180.

* `latitude`

   Un valor entre -85 y 85.

* `radius`

   Un valor entre 10 y 2000.

### Valores de columna

Los valores de las siguientes columnas se utilizan en la interfaz de usuario del servicio de ubicación:

* color, que se utiliza como color del pin que representa la ubicación del punto de interés en el mapa de la interfaz de usuario del servicio de ubicación.
   * Los valores válidos son "", #3E76D0, #AA99E8, #DC2ABA, #FC685B, #FC962E, #F6C436, #BECE5D, #61B56B y #3DC8DE.
   * Si el valor se deja en blanco, la interfaz de usuario del servicio de ubicación utiliza el azul como color predeterminado.

      Los valores corresponden a azul (#3E76D0), púrpura (#AA99E8), fuschia (#DC2ABA), naranja (#FC685B), naranja claro (#FC962E), amarillo (#F6C436), verde claro (#BECE5D), verde (#61E 56B) y azul claro (#3DC8DE), respectivamente.

* icono, que se utiliza como icono en el pin que representa la ubicación del punto de interés en el mapa de la interfaz de usuario del servicio de ubicación

   * Los valores válidos son "", tienda, hotelbed, auto, avión, tren, barco, estadio, parque de atracciones, anclaje, panadero, campana, puja, libro, caja, maletín, examinar, cepillo, edificio, calculadora, cámara, reloj, educación, linterna, seguir, juego, mujer, hombre, regalo, martillo, corazón, hogar, llave, lanzamiento, bombilla, buzón, dinero, pin, promoción, cinta comprasCarro, estrella, objetivo, tetera, thumbDown, thumbUp, trampa, trofeo, llave.
   * Si el valor se deja en blanco, la interfaz de usuario utiliza la estrella como icono predeterminado.

* Las columnas que no se mencionan pueden dejarse en blanco.

## Ejecución del script

1. Descargue archivos de la repo [git](https://github.com/adobe/places-scripts) en su directorio local.
1. En un editor de texto, abra el `config.py` archivo y realice las siguientes tareas:

   a. Edite los siguientes valores de variables como cadenas:

   * `csv_file_path`

      Ruta de acceso al `.csv` archivo.

   * `access_code`

      Este es el código de acceso que obtuvo de la llamada a Adobe IMS. Para obtener información sobre cómo obtener este código de acceso, consulte [Requisitos previos para el acceso](/help/web-service-api/adobe-i-o-integration.md) del usuario.

   * `org_id`

      El identificador de organización de Experience Cloud en el que se importarán los puntos de interés. Para obtener información sobre cómo obtener el identificador de organización, consulte [Requisitos previos para el acceso del usuario.](/help/web-service-api/adobe-i-o-integration.md).

   * `api_key`

      Esta es la clave de API de Places REST que obtuvo de la integración de Adobe I/O Places. Para obtener información sobre cómo obtener la clave de API, consulte Requisitos [previos para el acceso del usuario.](/help/web-service-api/adobe-i-o-integration.md).
   b.Guarde los cambios.

1. En una ventana de terminal, vaya al `…/places-scripts/import/` directorio.
1. Introduzca `python ./places_import.py` y pulse la **[!UICONTROL enter]** (**[!UICONTROL return]**) tecla.


## Comprobaciones CSV previas a la importación

La secuencia de comandos inicialmente completa las siguientes comprobaciones en el archivo .csv:

* Indica si se ha especificado un `.csv` archivo.
* Indica si la ruta del archivo es válida.
* Indica si se incluyen los encabezados de metadatos reservados.

   Los encabezados de metadatos reservados son lib_id, nombre, descripción, tipo, longitud, latitud, radio, país, estado, ciudad, calle, categoría, icono y color.

   >[!TIP]
   >
   >Todos los encabezados están en minúsculas y pueden aparecer en cualquier orden.

* Verifica los valores de las columnas especificadas en la sección del archivo CSV.

Si se encuentran errores, la secuencia de comandos imprime los errores y se anula. Si no se encuentran errores, la secuencia de comandos intenta importar los puntos de interés en lotes de 1000. Si el lote se importa correctamente, la secuencia de comandos muestra un código de estado de 200. Si el lote no se importa correctamente, se notifican errores.

## Pruebas unitarias

Las pruebas unitarias están en el `tests.py` archivo, deben ejecutarse antes de cada solicitud de extracción y deben pasar todas. Deben agregarse pruebas adicionales con el nuevo código. Para ejecutar las pruebas, vaya al `…/places-scripts/import/` directorio e introduzca `python ./places_import.py` en terminal.
