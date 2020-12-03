---
title: Añadir contexto de ubicación a solicitudes de Analytics
description: Esta sección proporciona información sobre cómo agregar contexto de ubicación a solicitudes de Analytics.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 1%

---


# Añadir contexto de ubicación a solicitudes de Analytics {#run-reports-aa-locserv-data}

>[!IMPORTANT]
>
>Este documento supone que se ha implementado el servicio de lugares en la aplicación. Para obtener más información sobre la implementación del servicio de lugares, consulte [Extensiones](/help/places-ext-aep-sdks/places-extension/places-extension.md)de lugares.

Después de que el servicio de lugares envíe los eventos de entrada y salida, puede crear reglas en Experience Platform Launch y adjuntar los datos del servicio de lugares a todos los eventos de Adobe Analytics. Para crear este tipo de regla, seleccione su propiedad en Iniciar y complete los siguientes pasos:

## 1. Crear una regla

1. On the **[!UICONTROL Rules]** tab, click **[!UICONTROL Create New Rule]**.

   Recuerde la información siguiente:
   * Si no tiene reglas existentes para esta propiedad, el **[!UICONTROL Create New Rule]** botón estará en medio de la pantalla.
   * Si la propiedad tiene reglas, el **[!UICONTROL Create New Rule]** botón estará en la parte superior derecha de la pantalla.

## 2. Seleccionar un evento

1. Asigne un nombre significativo a la regla para que sea fácilmente reconocible en su lista de reglas.

   En este ejemplo, el nombre de la regla es **[!UICONTROL Attach Places Service Data to Analytics Track Action Events]**.

1. Under the **[!UICONTROL Events]** section, click **[!UICONTROL Add]**.

1. En la lista **[!UICONTROL Extension]** desplegable, seleccione **[!UICONTROL Mobile Core]**.

1. En la lista **[!UICONTROL Event Type]** desplegable, seleccione **[!UICONTROL Track Action]**.

Ahora puede determinar los activadores que desea incluir para esta regla. En este ejemplo, el activador se basa en todas las `TrackAction` llamadas. Después de configurar el Evento, haga clic en **[!UICONTROL Keep Changes]**.

![&quot;crear un evento&quot;](/help/assets/ad-setEvent_use-analytics-data.png)


## 3. Añadir condiciones

>[!IMPORTANT]
>
>Complete este procedimiento para agregar condiciones a la regla. De lo contrario, vaya a la sección *Definir la acción* que aparece a continuación.

En este ejemplo, se crea una condición que hace que la regla se active solo para clientes de AT&amp;T.

1. Under the **[!UICONTROL Conditions]** section, click **[!UICONTROL Add]**.

1. En la lista **[!UICONTROL Extension]** desplegable, seleccione **[!UICONTROL Mobile Core]**.

1. En la lista **[!UICONTROL Condition Type]** desplegable, seleccione **[!UICONTROL Carrier Name]**.

1. En la ventana de la derecha, seleccione la casilla de verificación **[!UICONTROL AT&T]** .

1. Haga clic en **[!UICONTROL Keep Changes]**.

![&quot;crear una condición&quot;](/help/assets/ad-setCondition_use-analytics-data.png)

## 4. Definir la acción

1. Under the **[!UICONTROL Actions]** section, click **[!UICONTROL Add]**.

1. En la lista **[!UICONTROL Extension]** desplegable, seleccione **[!UICONTROL Mobile Core]**.

1. En la lista **[!UICONTROL Action Type]** desplegable, seleccione **[!UICONTROL Attach Data]**.

1. En el panel derecho, en el **[!UICONTROL JSON Payload]** campo, escriba los datos que se agregarán a este Evento.

1. Haga clic en **[!UICONTROL Keep Changes]**.

En el panel derecho, puede agregar una carga útil JSON de forma libre que agregue datos a un evento SDK antes de que una extensión que esté escuchando este evento pueda oír el evento. En este ejemplo, se agregan algunos datos de contexto a este evento antes de que la extensión de Analytics los procese. Los datos de contexto agregados estarán ahora en la visita saliente de Analytics.

En el siguiente ejemplo, `poi.city` se agregan valores y `poi.name` a los datos de contexto del evento de Analytics. El SDK determina de forma dinámica los valores de las nuevas claves cuando se procesa este evento.

![&quot;crear una acción&quot;](/help/assets/ad-setAction_use-analytics-data.png)

## 5. Guarde la regla y vuelva a crear la propiedad

Después de completar la configuración, compruebe que la regla tenga el aspecto de la siguiente imagen:

![&quot;la regla está completa.&quot;](/help/assets/ad-ruleComplete_use-analytics-data.png)

1. Haga clic en **[!UICONTROL Save]**

1. Vuelva a compilar la propiedad Launch e impleméntelo en el Entorno correcto.
