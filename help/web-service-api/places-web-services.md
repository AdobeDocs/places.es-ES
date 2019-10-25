---
title: 'Información general sobre la API de servicios Web '
seo-title: 'Información general sobre la API de servicios Web '
description: Places es el conjunto de servicios que facilita a los clientes de Adobe la hidratación de las soluciones Adobe Experience Cloud y Adobe Experience Platform con datos de ubicación y la experiencia adecuada para la persona adecuada en el momento y en el lugar adecuados.
seo-description: Places es el conjunto de servicios que facilita a los clientes de Adobe la hidratación de las soluciones Adobe Experience Cloud y Adobe Experience Platform con datos de ubicación y la experiencia adecuada para la persona adecuada en el momento y en el lugar adecuados.
translation-type: tm+mt
source-git-commit: e204958ac3acbf5fb45d2347987f35557be70e43

---


# Información general sobre la API de servicios Web {#places-web-services-api}

Places es el conjunto de servicios que facilita a los clientes de Adobe la hidratación de las soluciones Adobe Cloud Platform y Adobe Experience Platform con datos de ubicación y la experiencia adecuada para la persona adecuada en el momento y en el lugar adecuados.

Las API de servicios Web le permiten hacer lo siguiente:

* Administrar geofences
* Mida la ubicación de los usuarios incluso cuando la aplicación está en segundo plano
* Usar datos en tiempo real cuando sea importante

Esta sección proporciona información sobre cómo utilizar las API de REST y la base de datos de POI, que contiene los datos de POI de la organización.

## API de REST

La API de Places REST le permite trabajar mediante programación con los puntos de interés de su organización. Estas API le permiten crear, actualizar y eliminar sus bibliotecas y los puntos de interés de dichas bibliotecas. Estas API utilizan los estándares de notación de objetos JavaScript (JSON) para dar formato a los datos que se envían y reciben. Una de las principales ventajas de JSON es que hace que las consultas de API sean fáciles de escribir, leer y analizar por parte de desarrolladores y equipos.

Antes de utilizar la API de servicios Web, asegúrese de que se cumplen los siguientes requisitos:

* Los lugares están aprovisionados en su organización y usted tiene acceso adecuado como usuario.

   Para obtener más información, consulte la sección sobre los requisitos *de* la organización que figura a continuación.

* Después de aprovisionar Lugares en su organización y de tener acceso, cree una integración de Adobe para Lugares.

   Para obtener más información, consulte *Creación de la integración* de lugares en la integración de E/S de [Adobe](/help/web-service-api/adobe-i-o-integration.md).

Información adicional:

* Para obtener más información sobre las API disponibles y cómo utilizarlas, consulte [Administrar bibliotecas](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) y [Administrar puntos de interés](/help/web-service-api/api-usage/manage-pois/manage-pois.md).
* Para obtener más información sobre los encabezados y parámetros de estas API, consulte [Encabezados y parámetros](/help/web-service-api/api-usage/headers-and-parameters.md).

## Requisitos de organización {#org-requirements}

Para acceder a las API de REST de servicios Web, compruebe con el administrador del sistema que se han completado las siguientes tareas:

* Los lugares se han aprovisionado y aparecen en la organización.
* Ha sido agregado a la organización.
* Ha sido agregado a Lugares en su organización.

   Para obtener más información, consulte *Adición de un usuario a lugares y al inicio* de la plataforma de experiencia en preguntas [más](/help/places-faqs.md)frecuentes.

* Ha sido agregado como desarrollador de Places a su organización.

   Para obtener más información sobre la función de desarrollador, consulte [Administrar desarrolladores](https://helpx.adobe.com/enterprise/using/manage-developers.html).