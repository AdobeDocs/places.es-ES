---
title: Adobe Target
seo-title: Adobe Target
description: Esta sección proporciona información sobre cómo utilizar el servicio de ubicación con Adobe Target.
seo-description: Esta sección proporciona información sobre cómo utilizar el servicio de ubicación con Adobe Target.
translation-type: tm+mt
source-git-commit: 95dd010db8a860ebf489d04c7a70ec9cda8b3fb1

---


# Adobe Target {#places-target}

En este documento se asume que tiene implementada la extensión Places en la aplicación. Si necesita ayuda para implementar la extensión Lugares, consulte [Extensiones](/help/places-ext-aep-sdks/places-extension/places-extension.md)de lugares.

Una vez que la extensión Places envía eventos para entradas y salidas, puede aprovechar las reglas en Launch para adjuntar los datos de Lugares a los eventos del SDK de Adobe Target. Con la propiedad que desee seleccionada en Iniciar, puede crear este tipo de regla completando las siguientes tareas:

## 1. Crear una regla

1. En la **[!UICONTROL Rules]** ficha, haga clic en **[!UICONTROL Create New Rule]**.

   Recuerde la información siguiente:

   * Si no tiene reglas existentes para esta propiedad, el botón estará en medio de la pantalla.
   * Si la propiedad tiene reglas, el botón estará en la parte superior derecha de la pantalla.

## 2. Seleccionar un evento

1. Asigne un nombre significativo a la regla para que se pueda reconocer fácilmente en la lista de reglas.

   En este ejemplo, el nombre de la regla es **[!UICONTROL Attach Places Data to Target Content Requested]**.

1. En la **[!UICONTROL Events]** sección, haga clic en **[!UICONTROL Add]**.

1. En la lista **[!UICONTROL Extension]** desplegable, seleccione **[!UICONTROL Adobe Target]**.

1. En la lista **[!UICONTROL Event Type]** desplegable, seleccione **[!UICONTROL Content Requested]**.

1. Haga clic en **[!UICONTROL Keep Changes]**.

![agregar un evento](/help/assets/ad-setEvent_target.png)

## 3. Agregar condiciones

>[!IMPORTANT]
>
>Complete este paso si desea agregar Condiciones a la regla. De lo contrario, vaya a *Definir la acción* a continuación.

En el ejemplo siguiente, se crea una condición que hace que la regla se active solo para los usuarios que han iniciado la aplicación cinco o más veces.

1. En la **[!UICONTROL Conditions]** sección, haga clic en **[!UICONTROL Add]**.

1. En la lista **[!UICONTROL Extension]** desplegable, seleccione **[!UICONTROL Mobile Core]**.

1. En la lista **[!UICONTROL Condition Type]** desplegable, seleccione **[!UICONTROL Launches]**.

1. En el panel derecho, modifique la lista desplegable y los controles numéricos para que la condición se lea **[!UICONTROL User has launched the app greater than or equal to 5 times]**.

1. Haga clic en **[!UICONTROL Keep Changes]**.

![agregar un evento](/help/assets/ad-setCondition_target.png)

## 4. Definir la acción

1. En la **[!UICONTROL Actions]** sección, haga clic en **[!UICONTROL Add]**.

1. En la lista **[!UICONTROL Extension]** desplegable, seleccione **[!UICONTROL Mobile Core]**.

1. En la lista **[!UICONTROL Action Type]** desplegable, seleccione **[!UICONTROL Attach Data]**.

1. En el panel derecho, en el **[!UICONTROL JSON Payload]** campo, escriba los datos que se agregarán a este evento.

1. Haga clic en **[!UICONTROL Keep Changes]**.

En el panel derecho, puede agregar una carga útil JSON de forma libre que agregue datos a un evento SDK antes de que las extensiones que escuchen este evento lo oigan.

En el siguiente ejemplo, `poiCity` se agregan valores y `poiName` valores a la solicitud **[!UICONTROL mboxparameters]** para cada solicitud procesada en el evento de Target. El SDK determina los valores de las nuevas claves de forma dinámica en el momento en que se procesa este evento.

>[!TIP]
>
>Esta carga útil JSON utiliza una notación especial para el `request` objeto. En el evento original, `request` es una matriz de objetos anónimos. Cuando se adjuntan datos a todos los objetos de una matriz mediante Adjuntar datos, la `[*]` anotación en una clave que contenga una matriz hace que la carga útil se aplique a todos los objetos de esa matriz.
>
>La notación de `request[*]` puede leerse en voz alta como _para cada objeto de la`request`matriz_.

![agregar un evento](/help/assets/ad-setAction_target.png)

## 5. Guarde la regla y vuelva a crear la propiedad

Después de completar la configuración, compruebe que la regla tenga el aspecto de la siguiente imagen:

![regla completada](/help/assets/ad-ruleComplete_target.png)

1. Haga clic en **[!UICONTROL Save]**

1. Vuelva a compilar la propiedad Launch e impleméntelo en el entorno correcto.
