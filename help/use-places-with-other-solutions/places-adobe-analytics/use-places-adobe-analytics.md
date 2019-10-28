---
title: Enviar datos de lugares a Adobe Analytics
seo-title: Enviar datos de lugares a Adobe Analytics
description: Esta sección proporciona información sobre cómo enviar datos de lugares a Analytics.
seo-description: 'Esta sección proporciona información sobre cómo enviar datos de lugares a Analytics. '
translation-type: tm+mt
source-git-commit: fd98249c01fba93250dc7111798c76f3c96c6e20

---


# Enviar datos de lugares a Adobe Analytics {#places-data-analytics}


>[!IMPORTANT]
>
>En este documento se asume que tiene colocaciones implementadas en la aplicación. Para obtener más información sobre la implementación de Lugares, consulte [Colocaciones Extensiones](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Después de que Places envíe los eventos de entrada y salida, puede crear reglas en Inicio de plataforma de experiencia para enviar datos de Lugares a Adobe Analytics. Para crear este tipo de regla, seleccione su propiedad en Iniciar y complete los siguientes pasos:

## 1. Crear una regla

1. En la **[!UICONTROL Rules]** ficha, haga clic en **[!UICONTROL Create New Rule]**.

   Recuerde la información siguiente:

   * Si no tiene reglas existentes para esta propiedad, el botón estará en medio de la pantalla.
   * Si la propiedad tiene reglas, el botón estará en la parte superior derecha de la pantalla.

## 2. Seleccionar un evento

1. Asigne un nombre significativo a la regla para que se pueda reconocer fácilmente en la lista de reglas. En este ejemplo, el nombre de la regla es **Enviar datos a Analytics**.

2. In the **[!UICONTROL Events]** section, click **[!UICONTROL Add]**.

3. En la lista **[!UICONTROL Extension]** desplegable, seleccione **[!UICONTROL Places]**.

4. En la lista **[!UICONTROL Event Type]** desplegable, seleccione **[!UICONTROL Enter POI]**.

5. Haga clic en **[!UICONTROL Keep Changes]**.

   !["seleccionar un evento"](/help/assets/pt-selectEvent.png)


## 3. Agregar condiciones

>[!IMPORTANT]
>
>Complete este paso si desea agregar Condiciones a la regla. De lo contrario, vaya a *Definir la acción* a continuación.


En este ejemplo, se crea una condición que hace que la regla se active solo cuando el nombre del punto de interés actual es igual a **[!UICONTROL My POI]**.

1. En la **[!UICONTROL Conditions]** sección, haga clic en **[!UICONTROL Add]**.

2. En la lista **[!UICONTROL Extension]** desplegable, seleccione **[!UICONTROL Places]**.

3. En la lista **[!UICONTROL Condition Type]** desplegable, seleccione **[!UICONTROL Name]**.

4. En la ventana de la derecha, en el campo de texto, introduzca **[!UICONTROL My POI]**.

5. Haga clic en **[!UICONTROL Keep Changes]**.

   !["establecer una condición"](/help/assets/ad-setCondition.png)


## 4. Definir la acción

1. En la **[!UICONTROL Actions]** sección, haga clic en **[!UICONTROL Add]**.

2. En la lista **[!UICONTROL Extension]** desplegable, seleccione **[!UICONTROL Adobe Analytics]**.

3. En la lista **[!UICONTROL Action Type]** desplegable, seleccione **[!UICONTROL Track]**.

4. En el panel derecho, agregue la acción o el estado que desee enviar a Analytics. También puede elegir agregar cualquier dato de contexto adicional a esta solicitud. Recuerde que puede utilizar elementos de datos para obtener estos datos de forma dinámica desde el SDK.

5. Haga clic en **[!UICONTROL Keep Changes]**.

En el ejemplo siguiente, se envía una `TrackAction` llamada a Analytics con datos de contexto adicionales de **poi.name** iguales al nombre del punto de interés que activó este evento de entrada:

!["establecer una acción"](/help/assets/pt-setAction.png)

## 5. Guardar la regla y volver a generar la propiedad

Después de completar la configuración, compruebe que la regla tenga el aspecto de la siguiente imagen:

!["la regla se crea"](/help/assets/pt-ruleComplete.png)


1. Haga clic en **[!UICONTROL Save]**

2. Vuelva a compilar la propiedad Launch e impleméntelo en el entorno correcto.

