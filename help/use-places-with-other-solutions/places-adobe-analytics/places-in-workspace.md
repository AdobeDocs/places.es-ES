---
title: Informar sobre datos de ubicación en Analytics Workspace
description: Esta sección proporciona información sobre cómo informar sobre los datos de ubicación en Analytics Workspace.
exl-id: 45ca3c80-71b7-41de-9b00-645504061935
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 3%

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


## 1. Crear una regla de Launch

Cree una regla que haga que el SDK envíe datos a Analytics cuando el dispositivo entre en un punto de interés (POI). La creación de este tipo de regla se describe en la página [Enviar datos de entrada y salida de puntos de interés a Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md).

En este ejemplo, la acción de la regla tiene los siguientes valores definidos para la solicitud de Analytics:

* **[!UICONTROL Acción]** ha proporcionado un valor de **[!UICONTROL Entrada de lugares]**.

* La clave de datos de contexto **[!UICONTROL poi.name]** se ha establecido en el valor del elemento de datos **[!UICONTROL {%%POI Name%%}]**.

![&quot;estableció una acción&quot;](/help/assets/pt-setAction.png)

## 2. Crear variables de Analytics

Para asignar los datos de contexto (enviados en el paso 1), primero se deben crear variables para el grupo de informes de Analytics. Para obtener más información acerca de cómo crear variables en Analytics, consulte [Variables de conversión (eVars)](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/evar.html?lang=es).

En este ejemplo, se ha creado una variable de conversión **[!UICONTROL Evar2]** con el nombre **[!UICONTROL Places POI Name]**. Se deberán crear variables adicionales para cada variable de ubicación que desee exponer en los informes.

![&quot;crear una variable de analytics&quot;](/help/assets/aa-evar.png)

## 3. Crear reglas de procesamiento

Este paso es necesario para asignar datos de contexto (paso 1) a variables de Analytics (paso 2). Para obtener más información sobre la creación de reglas de procesamiento, consulte [Información general sobre las reglas de procesamiento](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules.html?lang=es).

En este ejemplo, se ha creado una regla de procesamiento para asignar el valor de datos de contexto **[!UICONTROL poi.name]** a **[!UICONTROL Places POI Name (eVar 2)]**. Será necesario crear reglas de procesamiento adicionales para cada variable de ubicación creada.

![&quot;crear una regla de procesamiento&quot;](/help/assets/aa-processing-rule.png)

## 4. Generar un informe en Workspace

Este paso muestra un informe básico en Analytics Workspace para ver los datos recopilados en los pasos 1-3. Para obtener más información sobre cómo usar Analytics Workspace, consulte [Resumen de Analytics Workspace](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/home.html?lang=es).

En este ejemplo, el informe tiene la siguiente configuración:

* Métrica: **[!UICONTROL Ocurrencias]**

* Dimension - **[!UICONTROL Nombre de la acción]**

   * Desglosado por Dimension - **[!UICONTROL Lugares Nombre POI]**

![&quot;crear un informe en el espacio de trabajo&quot;](/help/assets/aa-workspace.png)
