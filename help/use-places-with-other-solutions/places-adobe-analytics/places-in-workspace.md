---
title: Informe sobre los datos de ubicación en Analytics Workspace
seo-title: Informe sobre los datos de ubicación en Analytics Workspace
description: En esta sección se proporciona información sobre cómo generar informes sobre datos de ubicación en Analysis Workspace.
seo-description: En esta sección se proporciona información sobre cómo generar informes sobre datos de ubicación en Analysis Workspace.
translation-type: tm+mt
source-git-commit: 4ee8adb73f6dec15030a160c27edbeca71d3507b

---


# Informe sobre los datos de ubicación en el espacio de trabajo de Analytics {#places-in-workspace}

Este documento muestra un ejemplo de cómo informar sobre los datos de ubicación en el espacio de trabajo de Analytics. Cada paso contendrá un resumen de alto nivel, con detalles proporcionados por referencias a otras páginas de documentación.

## Requisitos previos

Este documento asume lo siguiente:

1. Adobe Places está implementada en la aplicación. Para obtener más información sobre la implementación de Adobe Places, consulte [Extensiones](/help/places-ext-aep-sdks/places-extension/places-extension.md)de lugares.

1. El usuario de Adobe Analytics es administrador y tiene acceso a las reglas de procesamiento. Para obtener más información sobre las reglas de procesamiento, consulte [Información general sobre las reglas de procesamiento](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html).

1. En la propiedad Launch, se han creado elementos de datos para las variables del servicio de ubicación que desee. Para obtener más información sobre los elementos de datos en Launch, consulte [Definición de un elemento](/help/use-places-launch-workflow/define-data-elements.md)de datos.


## 1. Crear una regla de lanzamiento

Cree una regla que haga que el SDK envíe datos a Analytics cuando el dispositivo entre en un punto de interés. La creación de este tipo de regla se describe en la página [Enviar datos de entrada y salida de puntos de interés a Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md) .

En este ejemplo, la acción de la regla tiene los siguientes valores definidos para la solicitud de Analytics:

* **[!UICONTROL Action]** se proporciona un valor de **[!UICONTROL Places Entry]**.

* La clave de datos de contexto **[!UICONTROL poi.name]** se establece en el valor del elemento de datos **[!UICONTROL {%%POI Name%%}]**.

!["establecer una acción"](/help/assets/pt-setAction.png)

## 2. Creación de variables de Analytics

Para asignar los datos de contexto (enviados en el paso 1), primero se deben crear variables para el grupo de informes de Analytics. Para obtener más información sobre la creación de variables en Analytics, consulte Variables [de conversión \(eVars\)](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-conversion-variables-evar.html).

En este ejemplo, se ha creado una variable de conversión **[!UICONTROL Evar2]**, con el nombre **[!UICONTROL Places POI Name]**. Será necesario crear variables adicionales para cada variable de ubicación que desee exponer en los informes.

!["crear una variable de análisis"](/help/assets/aa-evar.png)

## 3. Crear reglas de procesamiento

Este paso es necesario para asignar datos de contexto (paso 1) a variables de Analytics (paso 2). For more information on creating processing rules, see [Processing rules overview](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html).

En este ejemplo, se ha creado una regla de procesamiento para asignar el valor de datos de contexto **[!UICONTROL poi.name]** a **[!UICONTROL Places POI Name \(eVar2\)]**. Será necesario crear reglas de procesamiento adicionales para cada variable de ubicación creada.

!["crear una regla de procesamiento"](/help/assets/aa-processing-rule.png)

## 4. Generar un informe en Workspace

Este paso muestra un informe básico en Espacio de trabajo de Analytics para ver los datos recopilados en los pasos 1 a 3. Para obtener más información sobre cómo utilizar Espacio de trabajo de Analytics, consulte Información general [de Espacio de trabajo](https://docs.adobe.com/content/help/en/analytics/analyze/analysis-workspace/analysis-workspace-features.html)de Analytics.

En este ejemplo, el informe tiene la siguiente configuración:

* Metric - **[!UICONTROL Occurrences]**

* Dimension - **[!UICONTROL Action Name]**

   * Desglosado por dimensión - **[!UICONTROL Places POI Name]**

!["crear un informe en el espacio de trabajo"](/help/assets/aa-workspace.png)
