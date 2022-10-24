---
audience: end-user
user-guide-title: Guía del servicio de Places
user-guide-description: El servicio de Places es un sistema de localización geográfica que permite a las aplicaciones móviles con funciones de ubicación conocer el contexto de la ubicación de los usuarios.
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 20%

---


# Servicio de Places {#using}

+ [Información general del servicio Places](home.md)
+ [Notas de la versión](release-notes.md)
+ [Primeros pasos](getting-started.md)
+ [Obtener acceso al servicio Places](places-gain-access.md)
+ Interfaz de usuario del servicio de Places {#poi-mgmt-ui}
   + [Información general sobre la interfaz de usuario del servicio de Places](poi-mgmt-ui/poi-mgmt-ui-overview.md)
   + [Crear un punto de interés](poi-mgmt-ui/create-a-poi-ui.md)
   + [Administrar los puntos de interés creados anteriormente](poi-mgmt-ui/managing-pois-in-the-places-ui.md)
   + [Estrategias para usar metadatos con puntos de interés](poi-mgmt-ui/metadata-with-pois.md)
   + [Carga masiva de puntos de interés](poi-mgmt-ui/bulk-upload-pois.md)
   + [Administrar varias bibliotecas](poi-mgmt-ui/manage-libraries-in-the-places-ui.md)
+ API de servicio web {#web-service-api}
   + [Información general sobre la API del servicio web](web-service-api/places-web-services.md)
   + [Requisitos previos de integración](web-service-api/adobe-i-o-integration.md)
   + Uso de API {#api-usage}
      + [Información general sobre el uso de API](web-service-api/api-usage/api-usage-overview.md)
      + [Encabezados y parámetros](web-service-api/api-usage/headers-and-parameters.md)
      + Administrar bibliotecas {#manage-libraries}
         + [Información general sobre la administración de bibliotecas](web-service-api/api-usage/manage-libraries/manage-libraries.md)
         + [Crear una biblioteca.](web-service-api/api-usage/manage-libraries/create-a-library.md)
         + [Leer una biblioteca](web-service-api/api-usage/manage-libraries/read-a-library.md)
         + [Actualizar una biblioteca](web-service-api/api-usage/manage-libraries/update-a-library.md)
         + [Eliminar una biblioteca](web-service-api/api-usage/manage-libraries/delete-a-library.md)
         + [Lea todas las bibliotecas de su organización](web-service-api/api-usage/manage-libraries/read-all-libraries-in-your-organization.md)
         + [Establecer una clasificación en las bibliotecas](web-service-api/api-usage/manage-libraries/set-a-ran-on-your-libraries.md)
         + [Obtener la clasificación de una biblioteca](web-service-api/api-usage/manage-libraries/get-a-librarys-rank.md)
      + Administrar puntos de interés {#manage-pois}
         + [Información general sobre la administración de puntos de interés](web-service-api/api-usage/manage-pois/manage-pois.md)
         + [Crear un punto de interés](web-service-api/api-usage/manage-pois/create-a-poi.md)
         + [Leer un punto de interés](web-service-api/api-usage/manage-pois/read-a-poi.md)
         + [Actualizar un punto de interés](web-service-api/api-usage/manage-pois/update-a-poi.md)
         + [Eliminar un punto de interés](web-service-api/api-usage/manage-pois/delete-a-poi.md)
         + [Leer todos los puntos de interés de una biblioteca](web-service-api/api-usage/manage-pois/read-all-pois-in-a-library.md)
         + [Lea todos los puntos de interés de su organización](web-service-api/api-usage/manage-pois/read-all-pois-in-your-organization.md)
         + API por lotes {#batch-apis}
            + [Información general sobre las API por lotes](web-service-api/api-usage/manage-pois/batch-apis/batch-apis.md)
            + [Crear varios puntos de interés](web-service-api/api-usage/manage-pois/batch-apis/create-multiple-pois.md)
            + [Actualizar varios puntos de interés](web-service-api/api-usage/manage-pois/batch-apis/update-multiple-pois.md)
            + [Eliminar varios puntos de interés](web-service-api/api-usage/manage-pois/batch-apis/delete-multiple-pois.md)
      + [API de consulta](web-service-api/api-usage/query-apis.md)
+ Extensiones para los SDK de Mobile {#places-ext-aep-sdks}
   + Extensión Places {#places-extension}
      + [Extensión Places](places-ext-aep-sdks/places-extension/places-extension.md)
      + [Referencia de la API de Places](places-ext-aep-sdks/places-extension/places-api-reference.md)
      + [Referencia de evento de Places](places-ext-aep-sdks/places-extension/places-event-ref.md)
      + [Objetos de Lugares personalizados](places-ext-aep-sdks/places-extension/cust-places-objects.md)
+ [Utilice Places Service con su propia solución de monitorización](using-your-own-monitor.md)
+ [Usar el servicio Places sin supervisión de región activa](use-places-without-active-monitoring.md)
+ Utilizar el servicio Places como parte del flujo de trabajo del Experience Platform Launch {#use-places-launch-workflow}
   + [Utilizar el servicio Places como parte del flujo de trabajo del Experience Platform Launch](use-places-launch-workflow/places-launch-workflow.md)
   + [Definir elementos de datos](use-places-launch-workflow/define-data-elements.md)
   + [Crear reglas de entrada y salida](use-places-launch-workflow/create-rule-places-property.md)
+ Usar el servicio de Places con otras soluciones de Adobe {#use-places-with-other-solutions}
   + Adobe Analytics {#places-adobe-analytics}
      + [Uso del servicio Places con Adobe Analytics](use-places-with-other-solutions/places-adobe-analytics/use-places-analytics-overview.md)
      + [Envío de datos de entrada y salida de puntos de interés a Analytics](use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md)
      + [Añadir contexto de ubicación a solicitudes de Analytics](use-places-with-other-solutions/places-adobe-analytics/run-reports-aa-places-data.md)
      + [Informar sobre los datos de ubicación en Analytics Workspace](use-places-with-other-solutions/places-adobe-analytics/places-in-workspace.md)
   + Adobe Mobile Services {#places-mobile-svcs-messaging}
      + [Adobe Mobile Services](use-places-with-other-solutions/places-mobile-svcs-for-messaging/use-places-mobie-svcs-messaging.md)
      + [Notificaciones push](use-places-with-other-solutions/places-mobile-svcs-for-messaging/mobile-svcs-messaging-push.md)
      + [Notificaciones en la aplicación](use-places-with-other-solutions/places-mobile-svcs-for-messaging/mobile-svcs-messaging-inapp.md)
   + Adobe Campaign Standard {#places-acs}
      + [Uso del servicio Places con Adobe Campaign Standard](use-places-with-other-solutions/places-acs/places-acs-overview.md)
      + [Notificaciones push](use-places-with-other-solutions/places-acs/places-acs-push-notifications.md)
      + [Mensajes en la aplicación](use-places-with-other-solutions/places-acs/places-acs-in-app-messages.md)
   + Adobe Target {#places-target}
      + [Uso del servicio Places con Adobe Target](use-places-with-other-solutions/places-target/places-target.md)
+ Pruebas y validación {#places-testing-validation}
   + [Probar y validar el servicio Places](places-testing-validation/test-validate-places.md)
+ [Preguntas frecuentes](places-faqs.md)
