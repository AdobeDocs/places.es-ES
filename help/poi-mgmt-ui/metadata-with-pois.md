---
title: Uso de metadatos con puntos de interés
description: Esta sección proporciona información y estrategias sobre cómo utilizar metadatos con puntos de interés.
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Estrategias para utilizar metadatos con puntos de interés {#using-metadata-pois}

En el servicio de ubicación, al crear un nuevo punto de interés, los únicos elementos necesarios son Nombre, Radio, Latitud y Longitud. Para obtener más información sobre la creación de un punto de interés, consulte [Creación de un punto de interés](/help/poi-mgmt-ui/create-a-poi-ui.md). Sin embargo, si solo está introduciendo la información mínima, perderá la oportunidad de crear un valor adicional.

Los metadatos del punto de interés se pueden utilizar de diversas maneras. Desde el punto de vista de la administración de puntos de interés, la adición de valores de metadatos puede ayudar a buscar o filtrar una lista de posibles miles de puntos de interés. La creación de metadatos para atributos clave relacionados con un punto de interés puede generar valor en flujos de trabajo descendentes. Por ejemplo, una cadena de hoteles que crea puntos de interés para cada propiedad puede querer incluir metadatos como si el hotel tiene una piscina o no, o un restaurante y bar, o si tienen un gimnasio. Estos metadatos se pueden incluir como datos de contexto en Analytics y también se pueden usar para ofertas o mensajes de destino.

## Metadatos del servicio de ubicación en Launch

En Adobe Experience Platform Launch puede crear elementos de datos para cada campo de metadatos del servicio de ubicación que sea importante para el seguimiento o la mensajería.

![elemento de datos del gimnasio](/help/assets/gymfacility.png)

A continuación, puede crear una acción con la extensión Analytics para crear una nueva visita que incluya los metadatos que desee como datos de contexto.

![acción para el gimnasio](/help/assets/Analytics-gym.png)

## Mensajería en la aplicación en Adobe Campaign

Los metadatos se pueden utilizar como filtro para las notificaciones locales y los mensajes en la aplicación definidos en Adobe Campaign Standard. El uso de metadatos como filtro ofrece la oportunidad de crear un mensaje más relevante que sea contextual para la ubicación real.

![filtrado de notificaciones locales y mensajes en la aplicación en ACS](/help/assets/ACS_gym_metadata.png)