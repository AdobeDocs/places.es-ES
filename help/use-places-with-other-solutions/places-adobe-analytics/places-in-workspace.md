---
title: Informar sobre datos de ubicación en Analytics Workspace
description: Esta sección proporciona información sobre cómo informar sobre los datos de ubicación en Analytics Workspace.
exl-id: 45ca3c80-71b7-41de-9b00-645504061935
TQID: https://experienceleague.adobe.com/Xym9Ko8czyd3wYWVo22sQoK6gk-VvftGVHfIDUys06E
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: b069d60e-95f3-44d6-95a8-ddc862a4bc38
  - id: c20d46e7-1c7d-476c-a50e-3961d4dce35f
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 483
ht-degree: 6%

---

# Informar sobre los datos de ubicación en Analytics Workspace {#places-in-workspace}

Este documento muestra un ejemplo de cómo informar sobre los datos de ubicación en Analytics Workspace. Cada paso contendrá un resumen de alto nivel, con detalles proporcionados haciendo referencia a otras páginas de documentación.

## Requisitos previos

Este documento supone lo siguiente:

1. La extensión Places se implementa en la aplicación.

   Para obtener más información sobre cómo implementar la extensión Places, consulte [Extensiones Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

1. El usuario de Adobe Analytics es administrador y tiene acceso a las reglas de procesamiento.

   Para obtener más información sobre las reglas de procesamiento, consulte [Información general sobre las reglas de procesamiento](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules.html?lang=es).

1. En la propiedad de Launch, se han creado elementos de datos para las variables del servicio de Places que desee.

   Para obtener más información sobre los elementos de datos en Launch, consulte [Definir un elemento de datos](/help/use-places-launch-workflow/define-data-elements.md).


## &#x200B;1. Creación de una regla de Launch

Cree una regla que haga que SDK envíe datos a Analytics cuando el dispositivo entre en un punto de interés (POI). La creación de este tipo de regla se describe en la página [Enviar datos de entrada y salida de puntos de interés a Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md).

En este ejemplo, la acción de la regla tiene los siguientes valores definidos para la solicitud de Analytics:

* **[!UICONTROL Acción]** ha proporcionado un valor de **[!UICONTROL Entrada de lugares]**.

* La clave de datos de contexto **[!UICONTROL poi.name]** se ha establecido en el valor del elemento de datos **[!UICONTROL {%%POI Name%%}]**.

![&quot;estableció una acción&quot;](/help/assets/pt-setAction.png)

## &#x200B;2. Creación de variables de Analytics

Para asignar los datos de contexto (enviados en el paso 1), primero se deben crear variables para el grupo de informes de Analytics. Para obtener más información acerca de cómo crear variables en Analytics, consulte [Variables de conversión (eVars)](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/evar.html?lang=es).

En este ejemplo, se ha creado una variable de conversión **[!UICONTROL Evar2]** con el nombre **[!UICONTROL Places POI Name]**. Se deberán crear variables adicionales para cada variable de ubicación que desee exponer en los informes.

![&quot;crear una variable de analytics&quot;](/help/assets/aa-evar.png)

## &#x200B;3. Creación de reglas de procesamiento

Este paso es necesario para asignar datos de contexto (paso 1) a variables de Analytics (paso 2). Para obtener más información sobre la creación de reglas de procesamiento, consulte [Información general sobre las reglas de procesamiento](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules.html?lang=es).

En este ejemplo, se ha creado una regla de procesamiento para asignar el valor de datos de contexto **[!UICONTROL poi.name]** a **[!UICONTROL Places POI Name (eVar2)]**. Será necesario crear reglas de procesamiento adicionales para cada variable de ubicación creada.

![&quot;crear una regla de procesamiento&quot;](/help/assets/aa-processing-rule.png)

## &#x200B;4. Generación de informes en Workspace

Este paso muestra un informe básico en Analytics Workspace para ver los datos recopilados en los pasos 1-3. Para obtener más información sobre cómo usar Analytics Workspace, consulte [Resumen de Analytics Workspace](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/home.html?lang=es).

En este ejemplo, el informe tiene la siguiente configuración:

* Métrica: **[!UICONTROL Ocurrencias]**

* Dimension - **[!UICONTROL Nombre de la acción]**

   * Desglosado por Dimension - **[!UICONTROL Lugares Nombre POI]**

![&quot;crear un informe en el espacio de trabajo&quot;](/help/assets/aa-workspace.png)
