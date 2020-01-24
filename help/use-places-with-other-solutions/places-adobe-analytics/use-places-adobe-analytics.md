---
title: Envío de datos de entrada y salida de puntos de interés a Analytics
description: Esta sección proporciona información sobre cómo enviar datos de entrada y salida de puntos de interés a Analytics.
translation-type: tm+mt
source-git-commit: 8a84fe2dc5a0efe94ce3121e589524e3c7a80c5e

---


# Envío de datos de entrada y salida de puntos de interés a Analytics {#places-data-analytics}


>[!IMPORTANT]
>
>En esta sección se asume que se ha implementado el servicio de lugares en la aplicación. Para obtener más información sobre la implementación del servicio de lugares, consulte [Extensiones](/help/places-ext-aep-sdks/places-extension/places-extension.md)de lugares.

Después de que el servicio de lugares envíe los eventos de entrada y salida, puede crear reglas en Inicio de plataforma de experiencia para enviar datos del servicio de lugares a Adobe Analytics. Para crear este tipo de regla, seleccione su propiedad en Iniciar y complete los siguientes pasos:

## 1. Crear una regla

1. En la **[!UICONTROL Rules]**ficha, haga clic en**[!UICONTROL Create New Rule]**.

   Recuerde la información siguiente:

   * Si no tiene reglas existentes para esta propiedad, el **[!UICONTROL Create New Rule]**botón estará en medio de la pantalla.
   * Si la propiedad tiene reglas, el **[!UICONTROL Create New Rule]**botón estará en la parte superior derecha de la pantalla.

## 2. Seleccionar un evento

1. Escriba un nombre significativo para la regla.

   De este modo, la regla será fácilmente reconocible en la lista de reglas. En este ejemplo, el nombre de la regla es **[!UICONTROL Send Data to Analytics]**.

1. In the **[!UICONTROL Events]**section, click**[!UICONTROL Add]**.

1. En la lista **[!UICONTROL Extension]**desplegable, seleccione**[!UICONTROL Places Service]**.

1. En la lista **[!UICONTROL Event Type]**desplegable, seleccione**[!UICONTROL Enter POI]**.

1. Haga clic en **[!UICONTROL Keep Changes]**.

   ![&quot;seleccionar un evento&quot;](/help/assets/pt-selectEvent.png)


## 3. Agregar condiciones

>[!IMPORTANT]
>
>Complete este paso para agregar condiciones a la regla. De lo contrario, vaya a *Definir la acción* a continuación.

En este ejemplo, se crea una condición que hace que la regla se active solo cuando el nombre del punto de interés actual es igual a **[!UICONTROL My POI]**.

1. En la **[!UICONTROL Conditions]**sección, haga clic en**[!UICONTROL Add]**.

1. En la lista **[!UICONTROL Extension]**desplegable, seleccione**[!UICONTROL Places Service]**.

1. En la lista **[!UICONTROL Condition Type]**desplegable, seleccione**[!UICONTROL Name]**.

1. En el panel derecho, en el campo de texto, introduzca **[!UICONTROL My POI]**.

1. Haga clic en **[!UICONTROL Keep Changes]**.

   ![&quot;establecer una condición&quot;](/help/assets/pt-setCondition.png)


## 4. Definir la acción

1. En la **[!UICONTROL Actions]**sección, haga clic en**[!UICONTROL Add]**.

1. En la lista **[!UICONTROL Extension]**desplegable, seleccione**[!UICONTROL Adobe Analytics]**.

1. En la lista **[!UICONTROL Action Type]**desplegable, seleccione**[!UICONTROL Track]**.

1. En el panel derecho, agregue la acción o el estado que desee enviar a Analytics.

   También puede elegir agregar cualquier dato de contexto adicional a esta solicitud. Recuerde que puede utilizar elementos de datos para obtener estos datos de forma dinámica desde el SDK.

1. Haga clic en **[!UICONTROL Keep Changes]**.

   En el ejemplo siguiente, se envía una `TrackAction` llamada a Analytics con datos de contexto adicionales `poi.name` iguales al nombre del punto de interés que activó este evento de entrada:

   ![&quot;establecer una acción&quot;](/help/assets/pt-setAction.png)

## 5. Guarde la regla y vuelva a crear la propiedad

Después de completar la configuración, compruebe que la regla tenga el aspecto de la siguiente imagen:

![&quot;la regla se crea&quot;](/help/assets/pt-ruleComplete.png)

1. Haga clic en **[!UICONTROL Save]**

1. Vuelva a compilar la propiedad Launch e impleméntelo en el entorno correcto.
