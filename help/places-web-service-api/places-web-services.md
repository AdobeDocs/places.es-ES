---
title: 'Visión general de los servicios Web '
seo-title: 'Visión general de los servicios Web '
description: Places es el conjunto de servicios que facilita a los clientes de Adobe la hidratación de las soluciones Adobe Experience Cloud y Adobe Experience Platform con datos de ubicación y la experiencia adecuada para la persona adecuada en el momento y en el lugar adecuados.
seo-description: Places es el conjunto de servicios que facilita a los clientes de Adobe la hidratación de las soluciones Adobe Experience Cloud y Adobe Experience Platform con datos de ubicación y la experiencia adecuada para la persona adecuada en el momento y en el lugar adecuados.
translation-type: tm+mt
source-git-commit: f6c92bbd4fb21999f5c96ea0df8ede6919d1bc79

---


# Visión general de los servicios Web {#places-web-services-api}

Places es el conjunto de servicios que facilita a los clientes de Adobe la hidratación de las soluciones Adobe Cloud Platform y Adobe Experience Platform con datos de ubicación y la experiencia adecuada para la persona adecuada en el momento y en el lugar adecuados.

Los lugares le permiten hacer lo siguiente:

* Administrar geofences
* Mida la ubicación de los usuarios incluso cuando la aplicación está en segundo plano
* Usar datos en tiempo real cuando sea importante

Esta sección proporciona información sobre cómo utilizar las API de REST y la base de datos de lugares, que contiene los datos de POI de la organización.

## Coloca la API REST

La API de Places REST le permite trabajar mediante programación con los puntos de interés de su organización. Estas API le permiten crear, actualizar y eliminar sus bibliotecas y los puntos de interés de dichas bibliotecas. Estas API utilizan los estándares de notación de objetos JavaScript (JSON) para dar formato a los datos que se envían y reciben. Una de las principales ventajas de JSON es que hace que las consultas de API sean fáciles de escribir, leer y analizar por parte de desarrolladores y equipos.

Antes de utilizar la API de lugares, asegúrese de que se cumplen los siguientes requisitos:

* Los lugares están aprovisionados en su organización y usted tiene acceso adecuado como usuario.

   For more information, see the *Organization requirements* section below.

* Después de aprovisionar Lugares en su organización y de tener acceso, cree una integración de Adobe para Lugares.

   Para obtener más información, consulte *Creación de la integración* de lugares en la integración de E/S de [Adobe](/help/places-web-service-api/adobe-i-o-integration.md).

Información adicional:

* Para obtener más información sobre las API disponibles y cómo utilizarlas, consulte [Administrar bibliotecas](/help/places-web-service-api/api-usage/manage-libraries/manage-libraries.md) y [Administrar puntos de interés](/help/places-web-service-api/api-usage/manage-pois/manage-pois.md).
* Para obtener más información sobre los encabezados y parámetros de estas API, consulte [Encabezados y parámetros](/help/places-web-service-api/api-usage/headers-and-parameters.md).

## Requisitos de organización {#org-requirements}

Para acceder a las API de REST de Places, compruebe con el administrador del sistema que se han completado las siguientes tareas:

* Los lugares se han aprovisionado y aparecen en la organización.
* Ha sido agregado a la organización.
* Ha sido agregado a Lugares en su organización.

   Para obtener más información, consulte *Adición de un usuario a lugares e inicio* de plataforma de experiencia en [lugares Preguntas más frecuentes](/help/places-faqs.md).

* Ha sido agregado como desarrollador de Places a su organización.

   Para obtener más información sobre la función de desarrollador, consulte [Administrar desarrolladores](https://helpx.adobe.com/enterprise/using/manage-developers.html).