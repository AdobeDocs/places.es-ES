---
title: Puntos de interés de carga masiva
seo-title: Puntos de interés de carga masiva
description: Esta sección proporciona información sobre cómo cargar los puntos de interés de forma masiva.
seo-description: Esta sección proporciona información sobre cómo cargar los puntos de interés de forma masiva.
translation-type: tm+mt
source-git-commit: 3a9653dcc7f5d18b717c4bb59424b8cad7104dd7

---


# Carga masiva de puntos de interés {#bulk-upload-pois}

Se ha creado un conjunto de secuencias de comandos Python para simplificar la importación por lotes de puntos de interés desde un archivo .csv a una base de datos de puntos de interés mediante las API de servicios Web. Estos scripts se pueden descargar desde esta repo [git](https://github.com/adobe/places-scripts)de código abierto.

Antes de ejecutar estas secuencias de comandos, para asegurarse de que tiene acceso a las API de servicio Web, consulte Requisitos *previos para el acceso* del usuario en la descripción general [de la integración de](/help/web-service-api/adobe-i-o-integration.md)Adobe I/O.

A continuación se proporciona información sobre los scripts:

>[!TIP]
>
>Esta información también se incluye en un archivo léame de la repo [git](https://github.com/adobe/places-scripts).

## CSV

Un archivo .csv de ejemplo `places_sample.csv`, forma parte de este paquete e incluye los encabezados necesarios y una fila de datos de ejemplo. Todos estos encabezados están en minúsculas y corresponden a las claves de metadatos reservadas que se utilizan en la base de datos de lugares. Al agregar encabezados, las columnas adicionales se agregan a la base de datos de puntos de interés en una sección de metadatos independiente para cada punto de interés como pares clave/valor.

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

      Los valores corresponden a azul, púrpura, fuschia, naranja, naranja claro, amarillo, verde claro, verde claro y azul claro, respectivamente.

* icono, que se utiliza como icono en el pin que representa la ubicación del punto de interés en el mapa de la interfaz de usuario del servicio de ubicación
   * Los valores válidos son "", anclaje, panadero, campana, examinar, libro, pincel, construir, calculadora, cámara, carro de compras, reloj, caja, linterna, seguir, puja, cinta, educación, martillo, corazón, hogar, llave, buzón, hombre, promocionar, dinero, trampa, juego, regalo, lanzamiento, estrella, bombilla, pin, objetivo, tetera, thumbDown, thumbUp, maletín, trofeo, hembra y llave inglesa.
   * Si el valor se deja en blanco, la interfaz de usuario utiliza la estrella como icono predeterminado.

* Las columnas que no se mencionan pueden dejarse en blanco.

## Ejecución del script

1. Descargue archivos en el directorio correspondiente.
1. En un editor de texto, abra el `config.py` archivo y realice las siguientes tareas:

   a. Edite los siguientes valores de variables como cadenas:

   * `csv_file_path`

      Ruta de acceso al `.csv` archivo.

   * `access_code`

      Este es el código de acceso que obtuvo de la llamada a Adobe IMS.

   * `org_id`

      El identificador de organización de Experience Cloud en el que se importarán los puntos de interés.

   * `api_key`

      Esta es la clave de API de Places REST que se obtuvo de la integración de Adobe I/O Places.
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



