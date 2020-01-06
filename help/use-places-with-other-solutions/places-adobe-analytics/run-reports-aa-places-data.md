---
title: Agregar contexto de ubicación a solicitudes de Analytics
description: Esta sección proporciona información sobre cómo agregar contexto de ubicación a solicitudes de Analytics.
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Agregar contexto de ubicación a solicitudes de Analytics {#run-reports-aa-locserv-data}

>[!IMPORTANT]
>
>Este documento asume que tiene Adobe Places implementados en la aplicación. Para obtener más información sobre la implementación de Adobe Places, consulte [Extensiones](/help/places-ext-aep-sdks/places-extension/places-extension.md)de lugares.

Después de que Places envíe los eventos de entrada y salida, puede crear reglas en Inicio de plataforma de experiencia y adjuntar los datos de Lugares a todos los eventos de Adobe Analytics. Para crear este tipo de regla, seleccione su propiedad en Iniciar y complete los siguientes pasos:

## 1. Crear una regla

1. En la **[!UICONTROL Rules]**ficha, haga clic en**[!UICONTROL Create New Rule]**.

   Recuerde la información siguiente:
   * Si no tiene reglas existentes para esta propiedad, el **[!UICONTROL Create New Rule]**botón estará en medio de la pantalla.
   * Si la propiedad tiene reglas, el **[!UICONTROL Create New Rule]**botón estará en la parte superior derecha de la pantalla.

## 2. Seleccionar un evento

1. Asigne un nombre significativo a la regla para que se pueda reconocer fácilmente en la lista de reglas.

   En este ejemplo, el nombre de la regla es **[!UICONTROL Attach Places Data to Analytics Track Action Events]**.

1. En la **[!UICONTROL Events]**sección, haga clic en**[!UICONTROL Add]**.

1. En la lista **[!UICONTROL Extension]**desplegable, seleccione**[!UICONTROL Mobile Core]**.

1. En la lista **[!UICONTROL Event Type]**desplegable, seleccione**[!UICONTROL Track Action]**.

Ahora puede determinar los activadores que desea incluir para esta regla. En este ejemplo, el activador se basa en todas las `TrackAction` llamadas. Después de configurar el evento, haga clic en **[!UICONTROL Keep Changes]**.

![&quot;crear un evento&quot;](/help/assets/ad-setEvent_use-analytics-data.png)


## 3. Agregar condiciones

>[!IMPORTANT]
>
>Complete este procedimiento para agregar condiciones a la regla. De lo contrario, vaya a la sección *Definir la acción* que aparece a continuación.

En este ejemplo, se crea una condición que hace que la regla se active solo para clientes de AT&amp;T.

1. En la **[!UICONTROL Conditions]**sección, haga clic en**[!UICONTROL Add]**.

1. En la lista **[!UICONTROL Extension]**desplegable, seleccione**[!UICONTORL  Mobile Core]**.

1. En la lista **[!UICONTROL Condition Type]**desplegable, seleccione**[!UICONTROL Carrier Name]**.

1. En la ventana de la derecha, seleccione la casilla de verificación **[!UICONTROL AT&T]**.

1. Haga clic en **[!UICONTROL Keep Changes]**.

![&quot;crear una condición&quot;](/help/assets/ad-setCondition_use-analytics-data.png)

## 4. Definir la acción

1. En la **[!UICONTROL Actions]**sección, haga clic en**[!UICONTROL Add]**.

1. En la lista **[!UICONTROL Extension]**desplegable, seleccione**[!UICONTROL Mobile Core]**.

1. En la lista **[!UICONTROL Action Type]**desplegable, seleccione**[!UICONTROL Attach Data]**.

1. En el panel derecho, en el **[!UICONTROL JSON Payload]**campo, escriba los datos que se agregarán a este evento.

1. Haga clic en **[!UICONTROL Keep Changes]**.

En el panel derecho, puede agregar una carga útil JSON improvisada que agregue datos a un evento SDK antes de que una extensión que esté escuchando este evento pueda oír el evento. En este ejemplo, se agregan algunos datos de contexto a este evento antes de que la extensión de Analytics lo procese. Los datos de contexto agregados estarán ahora en la visita saliente de Analytics.

En el ejemplo siguiente, se añaden `poi.city` y `poi.name` valores a los datos de contexto del evento de Analytics. El SDK determina de forma dinámica los valores de las nuevas claves cuando se procesa este evento.

![&quot;crear una acción&quot;](/help/assets/ad-setAction_use-analytics-data.png)

## 5. Guarde la regla y vuelva a crear la propiedad

Después de completar la configuración, compruebe que la regla tenga el aspecto de la siguiente imagen:

![&quot;la regla está completa.&quot;](/help/assets/ad-ruleComplete_use-analytics-data.png)

1. Haga clic en **[!UICONTROL Save]**

1. Vuelva a compilar la propiedad Launch e impleméntelo en el entorno correcto.
