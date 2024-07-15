---
title: Uso de metadatos con puntos de interés
description: Esta sección proporciona información y estrategias sobre cómo utilizar los metadatos con los puntos de interés.
exl-id: e669e560-a999-43ff-aeb4-06e6308b0d5c
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# Estrategias para usar metadatos con puntos de interés {#using-metadata-pois}

En el servicio de Places, al crear un nuevo punto de interés, los únicos elementos necesarios son Nombre, Radio, Latitud y Longitud. Para obtener más información sobre cómo crear un punto de interés, consulte [Crear un punto de interés](/help/poi-mgmt-ui/create-a-poi-ui.md). Sin embargo, si solo introduce la información mínima, perderá la oportunidad de crear un valor adicional.

Los metadatos de puntos de interés se pueden utilizar de varias formas. Desde el punto de vista de la administración de puntos de interés, añadir valores de metadatos puede ayudar a buscar o filtrar una lista de miles de puntos de interés. La creación de metadatos para atributos clave relacionados con un punto de interés puede proporcionar valor en flujos de trabajo descendentes. Por ejemplo, una cadena de hoteles que crea puntos de interés para cada propiedad puede querer incluir metadatos como, por ejemplo, si el hotel tiene piscina o no, o un restaurante y bar, o si tiene un gimnasio. Estos metadatos se pueden incluir como datos de contexto en Analytics y también se pueden utilizar para ofertas o mensajes de destino.

## Coloca los metadatos del servicio en Launch

En Experience Platform Launch, puede crear elementos de datos para cada campo de metadatos de servicio de Places que sea importante para fines de seguimiento o mensajería.

![elemento de datos para el gimnasio](/help/assets/gymfacility.png)

A continuación, puede crear una acción con la extensión de Analytics para crear una nueva visita que incluya los metadatos que desee como datos de contexto.

![acción para el gimnasio](/help/assets/Analytics-gym.png)

## Mensajería en la aplicación en Adobe Campaign

Los metadatos se pueden utilizar como filtro para las notificaciones locales y los mensajes en la aplicación definidos en Adobe Campaign Standard. El uso de los metadatos como filtro ofrece la oportunidad de crear un mensaje más relevante que sea contextual para la ubicación real.

![filtrado de notificaciones locales y mensajes en la aplicación en ACS](/help/assets/ACS_gym_metadata.png)
