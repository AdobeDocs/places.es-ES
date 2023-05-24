---
title: Información general sobre API de servicios web
description: Places Service es el conjunto de servicios que facilita a los clientes de Adobe la hidratación de las soluciones de Adobe Experience Cloud y Adobe Experience Platform con datos de ubicación y la experiencia adecuada para la persona adecuada, en el momento y en el lugar adecuados.
exl-id: 9e7358d1-3ba0-4304-aeb2-fed7162afb57
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 1%

---

# Información general de API de servicios web {#places-web-services-api}

Places Service es el conjunto de servicios que facilita a los clientes de Adobe la hidratación de las soluciones de Adobe Cloud Platform y Adobe Experience Platform con datos de ubicación y la experiencia adecuada para la persona adecuada, en el momento y en el lugar adecuados.

Las API de servicios web le permiten hacer lo siguiente:

* Administrar geovallas
* Mida la ubicación de los usuarios incluso cuando la aplicación esté en segundo plano
* Utilice datos en tiempo real cuando importen

Esta sección proporciona información sobre cómo utilizar las API de REST y la base de datos de puntos de interés, que contiene los datos de puntos de interés de su organización.

## API de REST

La API de REST del servicio Places le permite trabajar de manera programática con los puntos de interés de su organización. Estas API le permiten crear, actualizar y eliminar sus bibliotecas y los puntos de interés de esas bibliotecas. Estas API utilizan los estándares de Notación de objetos JavaScript (JSON) para dar formato a los datos que se envían y reciben. Una ventaja principal de JSON es que facilita a los desarrolladores y a los equipos la escritura, la lectura y el análisis de consultas de API.

Antes de utilizar la API de servicios web, asegúrese de que se hayan cumplido los siguientes requisitos:

* El servicio Places está aprovisionado en su organización y usted tiene el acceso adecuado como usuario.

   Para obtener más información, consulte *Requisitos previos para el acceso de usuarios* in [Requisitos previos y descripción general de integración](/help/web-service-api/adobe-i-o-integration.md).

* Una vez que el servicio Places esté aprovisionado en su organización y usted tenga acceso, cree una integración de Adobe para el servicio Places.

   Para obtener más información, consulte *Creación de una integración de Places Service* in [Requisitos previos y descripción general de integración](/help/web-service-api/adobe-i-o-integration.md).

Más información:

* Para obtener más información sobre las API disponibles y cómo utilizarlas, consulte [Administrar bibliotecas](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) y [Administrar POI](/help/web-service-api/api-usage/manage-pois/manage-pois.md).
* Para obtener más información sobre los encabezados y parámetros de estas API, consulte [Encabezados y parámetros](/help/web-service-api/api-usage/headers-and-parameters.md).
