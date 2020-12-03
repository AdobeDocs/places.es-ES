---
title: 'Información general sobre la API de servicios Web '
description: Places Service es el conjunto de servicios que facilita a los clientes de Adobe la hidratación de las soluciones Adobe Experience Cloud y Adobe Experience Platform con datos de ubicación y la experiencia adecuada para la persona adecuada en el momento y en el lugar adecuados.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 1%

---


# Información general sobre la API de servicios Web {#places-web-services-api}

Places Service es el conjunto de servicios que facilita a los clientes de Adobe la hidratación de las soluciones Adobe Cloud Platform y Adobe Experience Platform con datos de ubicación y la experiencia adecuada para la persona adecuada en el momento y en el lugar adecuados.

Las API de servicios Web le permiten hacer lo siguiente:

* Administrar geofences
* Mida la ubicación de los usuarios incluso cuando la aplicación está en segundo plano
* Usar datos en tiempo real cuando sea importante

Esta sección proporciona información sobre cómo utilizar las API de REST y la base de datos de POI, que contiene los datos de POI de la organización.

## API de REST

La API de REST del servicio de lugares le permite trabajar mediante programación con los puntos de interés de su organización. Estas API le permiten crear, actualizar y eliminar sus bibliotecas y los puntos de interés de dichas bibliotecas. Estas API utilizan los estándares de notación de objetos JavaScript (JSON) para dar formato a los datos que se envían y reciben. Una de las principales ventajas de JSON es que facilita la escritura, lectura y análisis de consultas de API por parte de desarrolladores y equipos.

Antes de utilizar la API de servicios Web, asegúrese de que se cumplen los siguientes requisitos:

* El servicio de lugares está aprovisionado en su organización y tiene el acceso adecuado como usuario.

   Para obtener más información, consulte Requisitos *previos para el acceso* del usuario en Información general sobre [la integración y requisitos previos](/help/web-service-api/adobe-i-o-integration.md).

* Una vez que el servicio de lugares esté aprovisionado en su organización y tenga acceso, cree una integración de Adobe para el servicio de lugares.

   Para obtener más información, consulte *Creación de una integración* de servicio de lugares en Información general y requisitos previos [de](/help/web-service-api/adobe-i-o-integration.md)integración.

Más información:

* Para obtener más información sobre las API disponibles y cómo utilizarlas, consulte [Administrar bibliotecas](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) y [Administrar puntos de interés](/help/web-service-api/api-usage/manage-pois/manage-pois.md).
* Para obtener más información sobre los encabezados y parámetros de estas API, consulte [Encabezados y parámetros](/help/web-service-api/api-usage/headers-and-parameters.md).