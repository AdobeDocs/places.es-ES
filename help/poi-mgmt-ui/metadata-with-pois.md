---
title: Uso de metadatos con puntos de interés
description: Esta sección proporciona información y estrategias sobre cómo utilizar los metadatos con los puntos de interés.
exl-id: e669e560-a999-43ff-aeb4-06e6308b0d5c
TQID: https://experienceleague.adobe.com/wTzahAs7MMSv0q-cEhkNObBpALUJXqDXlOcqjitezwY
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 296
ht-degree: 0%

---

# Estrategias para usar metadatos con puntos de interés {#using-metadata-pois}

En el servicio de Places, al crear un nuevo punto de interés, los únicos elementos necesarios son Nombre, Radio, Latitud y Longitud. Para obtener más información sobre cómo crear un punto de interés, consulte [Crear un punto de interés](/help/poi-mgmt-ui/create-a-poi-ui.md). Sin embargo, si solo introduce la información mínima, perderá la oportunidad de crear un valor adicional.

Los metadatos de puntos de interés se pueden utilizar de varias formas. Desde el punto de vista de la administración de puntos de interés, añadir valores de metadatos puede ayudar a buscar o filtrar una lista de miles de puntos de interés. La creación de metadatos para atributos clave relacionados con un punto de interés puede proporcionar valor en flujos de trabajo descendentes. Por ejemplo, una cadena de hoteles que crea puntos de interés para cada propiedad puede querer incluir metadatos como, por ejemplo, si el hotel tiene piscina o no, o un restaurante y bar, o si tiene un gimnasio. Estos metadatos se pueden incluir como datos de contexto en Analytics y también se pueden utilizar para ofertas o mensajes de destino.

## Coloca los metadatos del servicio en Launch

En Experience Platform Launch, puede crear elementos de datos para cada campo de metadatos del servicio Places que sea importante para el seguimiento o la mensajería.

![elemento de datos para el gimnasio](/help/assets/gymfacility.png)

A continuación, puede crear una acción con la extensión de Analytics para crear una nueva visita que incluya los metadatos que desee como datos de contexto.

![acción para el gimnasio](/help/assets/Analytics-gym.png)

## Mensajería en la aplicación en Adobe Campaign

Los metadatos se pueden utilizar como filtro para las notificaciones locales y los mensajes en la aplicación definidos en Adobe Campaign Standard. El uso de los metadatos como filtro ofrece la oportunidad de crear un mensaje más relevante que sea contextual para la ubicación real.

![filtrado de notificaciones locales y mensajes en la aplicación en ACS](/help/assets/ACS_gym_metadata.png)
