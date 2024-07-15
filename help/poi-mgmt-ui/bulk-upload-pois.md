---
title: Puntos de interés de carga masiva
description: Esta sección proporciona información sobre cómo cargar de forma masiva los puntos de interés.
exl-id: 72704bfc-5837-4439-bdb2-e77ddf935639
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 0%

---

# Carga masiva de puntos de interés {#bulk-upload-pois}

El botón **Importar puntos de interés** del servicio Places se puede usar para cargar nuevos puntos de interés de forma masiva mediante un archivo CSV. Se proporciona una plantilla de hoja de cálculo de ejemplo para mostrar qué columnas de datos son necesarias y cómo agregar metadatos personalizados opcionales.

![Pantalla de importación masiva](/help/assets/Bulk-import.png)

Consulte este vídeo que muestra el proceso de importación y edición por lotes:

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

[Importación y edición masiva de servicios de Places](https://www.youtube.com/watch?v=75qVtirsXhg)

## Scripts de API de Python

Se ha creado un conjunto de scripts en Python para simplificar la importación por lotes de puntos de interés desde un archivo .csv a una base de datos de puntos de interés mediante las API de servicio web. Estos scripts se pueden descargar de este repositorio de código abierto [git](https://github.com/adobe/places-scripts).

Antes de ejecutar estos scripts, para acceder a las API del servicio web, consulta *Requisitos previos para el acceso de usuarios* en [Resumen general y requisitos previos de la integración](/help/web-service-api/adobe-i-o-integration.md).

A continuación se proporciona información sobre los scripts:

>[!TIP]
>
>Esta información también se incluye en un archivo léame en el [repositorio git](https://github.com/adobe/places-scripts).

## Archivo CSV

Un archivo .csv de ejemplo, `places_sample.csv`, forma parte de este paquete e incluye los encabezados necesarios y una fila de datos de ejemplo. Todos estos encabezados están en minúsculas y corresponden a las claves de metadatos reservadas que se utilizan en la base de datos de Places. Las columnas que agregue al archivo .csv se agregarán a la base de datos de puntos de interés en una sección de metadatos independiente para cada punto de interés como pares clave/valor, y el valor del encabezado se utilizará como clave.

Esta es una lista de las columnas y los valores que debe utilizar:

* `lib_id`

  ID de biblioteca válido obtenido de la base de datos de puntos de interés.

* `type`

  Point es actualmente el único valor válido.

* `longitude`

  Un valor entre -180 y 180.

* `latitude`

  Un valor entre -85 y 85.

* `radius`

  Un valor entre 10 y 20 000.

### Valores de columna

Los valores de las siguientes columnas se utilizan en la interfaz de usuario del servicio de Places:

* color, que se utiliza como el color del pin que representa la ubicación del punto de interés en el mapa de la interfaz de usuario del servicio de Places.
   * Los valores válidos son &quot;&quot;, #3E76D0, #AA99E8, #DC2ABA, #FC685B, #FC962E, #F6C436, #BECE5D, #61B56B y #3DC8DE, y &quot;&quot;.
   * Si se deja en blanco, la interfaz de usuario del servicio de Places utiliza el azul como color predeterminado.

     Los valores corresponden a azul (#3E76D0), púrpura (#AA99E8), fucsia (#DC2ABA), naranja (#FC685B), naranja claro (#FC962E), amarillo (#F6C436), verde claro (#BECE5D), verde (#61B56B) y azul claro (#3DC8DE), respectivamente.

* , que se utiliza como icono en el pin que representa la ubicación del punto de interés en el mapa de la interfaz de usuario del servicio de Places.

   * Los valores válidos son &quot;&quot;, tienda, cama de hotel, coche, avión, tren, barco, estadio, parque de atracciones, ancla, vaso de precipitados, campana, oferta, libro, caja, maletín, examinar, pincel, edificio, calculadora, cámara, reloj, educación, linterna, seguir, juego, mujer, hombre, regalo, martillo, corazón, hogar, llave, lanzamiento, bombilla, buzón, dinero, pin, promover, cinta, carro de compras, estrella, objetivo, tetera, thumbDown, thumbUp, trampa, trofeo, llave inglesa.

     Los valores de icono se muestran en el orden en que aparecen en la siguiente ilustración:

     ![iconos en la interfaz de usuario](/help/assets/UI_icons.png)

   * Si se deja en blanco, la interfaz de usuario utiliza asterisco como icono predeterminado.

* Las columnas que no se mencionan pueden dejarse en blanco.

## Ejecución del script

1. Descargue los archivos del [repositorio git](https://github.com/adobe/places-scripts) a su directorio local.
1. En un editor de texto, abra el archivo `config.py` y complete las tareas siguientes:

   a. Edite los siguientes valores de variables como cadenas:

   * `csv_file_path`

     Esta es la ruta al archivo `.csv`.

   * `access_code`

     Este es su código de acceso que se obtuvo de la llamada a Adobe IMS. Para obtener información sobre cómo obtener este código de acceso, consulte *Requisitos previos para el acceso de usuarios* en [Información general y requisitos previos de la integración](/help/web-service-api/adobe-i-o-integration.md).

   * `org_id`

     El orgID del Experience Cloud en el que se importarán los POI. Para obtener información sobre cómo obtener el identificador de organización, consulte *Requisitos previos para el acceso de usuarios* en [Información general y requisitos previos de la integración](/help/web-service-api/adobe-i-o-integration.md).

   * `api_key`

     Esta es la clave de API de REST de Places que se obtiene de la integración de Places de Adobe I/O. Para obtener información sobre cómo obtener la clave de API, consulte *Requisitos previos para el acceso de usuarios* en [Información general y requisitos previos de la integración](/help/web-service-api/adobe-i-o-integration.md).

   b. Guarde los cambios.

1. En una ventana de terminal, vaya al directorio `…/places-scripts/import/`.
1. Escriba `python ./places_import.py` y presione la tecla **[!UICONTROL entrar]** (**[!UICONTROL regresar]**).


## Comprobaciones previas a la importación de CSV

La secuencia de comandos completa inicialmente las siguientes comprobaciones en el archivo .csv:

* Si se especificó un archivo de `.csv`.
* Indica si la ruta de archivo es válida.
* Si se incluyen los encabezados de metadatos reservados.

  Los encabezados de metadatos reservados son lib_id, nombre, descripción, tipo, longitud, latitud, radio, país, estado, ciudad, calle, categoría, icono y color.

  >[!TIP]
  >
  >Los encabezados están todos en minúsculas y se pueden enumerar en cualquier orden.

* Comprueba los valores de las columnas especificadas en la sección del archivo CSV.

Si se encuentran errores, la secuencia de comandos los imprime y se anula. Si no se encuentran errores, la secuencia de comandos intenta importar los puntos de interés en lotes de 1000. Si el lote se importa correctamente, el script informa de un código de estado de 200. Si el lote no se importa correctamente, se informa de los errores.

## Pruebas unitarias

Las pruebas unitarias se encuentran en el archivo `tests.py`, deben ejecutarse antes de cada solicitud de extracción y deben aprobarse todas. Se deben añadir pruebas adicionales con el nuevo código. Para ejecutar las pruebas, vaya al directorio `…/places-scripts/import/` e introduzca `python ./places_import.py` en el terminal.
