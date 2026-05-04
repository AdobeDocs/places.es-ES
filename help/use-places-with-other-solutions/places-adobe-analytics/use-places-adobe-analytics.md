---
title: Envío de datos de entrada y salida de puntos de interés a Analytics
description: Esta sección proporciona información sobre cómo enviar datos de entrada y salida de puntos de interés a Analytics.
exl-id: 69e96261-4902-47dd-a930-a8f3d19c179c
TQID: https://experienceleague.adobe.com/H-NkwK7KNSGPjEKYuWNc8F0f3MIu3wBr5FGjypxnqng
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: b069d60e-95f3-44d6-95a8-ddc862a4bc38
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 443
ht-degree: 3%

---

# Envío de datos de entrada y salida de puntos de interés a Analytics {#places-data-analytics}


>[!IMPORTANT]
>
>En esta sección se da por hecho que el servicio Places está implementado en la aplicación. Para obtener más información acerca de la implementación del servicio Places, consulte [Extensiones de Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Después de que el servicio Places envíe los eventos de entrada y salida, puede crear reglas en Experience Platform Launch para enviar los datos del servicio Places a Adobe Analytics. Para crear este tipo de regla, seleccione la propiedad en Launch y complete los siguientes pasos:

## &#x200B;1. Crear una regla

1. En la ficha **[!UICONTROL Reglas]**, haga clic en **[!UICONTROL Crear nueva regla]**.

   Recuerde la información siguiente:

   * Si no tiene reglas existentes para esta propiedad, el botón **[!UICONTROL Crear nueva regla]** estará en medio de la pantalla.
   * Si su propiedad tiene reglas, el botón **[!UICONTROL Crear nueva regla]** estará en la parte superior derecha de la pantalla.

## &#x200B;2. Seleccione un evento

1. Escriba un nombre significativo para la regla.

   De este modo, la regla será fácilmente reconocible en su lista de reglas. En este ejemplo, la regla se denomina **[!UICONTROL Enviar datos a Analytics]**.

1. En la sección **[!UICONTROL Eventos]**, haga clic en **[!UICONTROL Agregar]**.

1. En la lista desplegable **[!UICONTROL Extensión]**, seleccione **[!UICONTROL Servicio Places]**.

1. En la lista desplegable **[!UICONTROL Tipo de evento]**, seleccione **[!UICONTROL Introducir punto de interés]**.

1. Haga clic en **[!UICONTROL Conservar cambios]**.

   ![&quot;seleccionar un evento&quot;](/help/assets/pt-selectEvent.png)


## &#x200B;3. Adición de condiciones

>[!IMPORTANT]
>
>Complete este paso para agregar condiciones a la regla. De lo contrario, saltarse a *Defina la acción* a continuación.

En este ejemplo, se crea una condición que hace que la regla entre en déclencheur únicamente cuando el nombre del punto de interés actual es igual a **[!UICONTROL Mi punto de interés]**.

1. En la sección **[!UICONTROL Condiciones]**, haga clic en **[!UICONTROL Agregar]**.

1. En la lista desplegable **[!UICONTROL Extensión]**, seleccione **[!UICONTROL Servicio Places]**.

1. En la lista desplegable **[!UICONTROL Tipo de condición]**, seleccione **[!UICONTROL Nombre]**.

1. En el panel derecho, en el campo de texto, escriba **[!UICONTROL Mi punto de interés]**.

1. Haga clic en **[!UICONTROL Conservar cambios]**.

   ![&quot;estableció una condición&quot;](/help/assets/pt-setCondition.png)


## &#x200B;4. Defina la acción

1. En la sección **[!UICONTROL Acciones]**, haga clic en **[!UICONTROL Agregar]**.

1. En la lista desplegable **[!UICONTROL Extensión]**, seleccione **[!UICONTROL Adobe Analytics]**.

1. En la lista desplegable **[!UICONTROL Tipo de acción]**, seleccione **[!UICONTROL Seguimiento]**.

1. En el panel derecho, añada la acción o el estado que desee enviar a Analytics.

   También puede añadir datos de contexto adicionales a esta solicitud. Recuerde que puede utilizar elementos de datos para obtener estos datos de forma dinámica desde SDK.

1. Haga clic en **[!UICONTROL Conservar cambios]**.

   En el ejemplo siguiente, se envía una llamada de `TrackAction` a Analytics con datos de contexto adicionales de `poi.name` iguales al nombre del punto de interés que activó este evento de entrada:

   ![&quot;estableció una acción&quot;](/help/assets/pt-setAction.png)

## &#x200B;5. Guarde la regla y vuelva a generar la propiedad

Una vez completada la configuración, compruebe que la regla tiene el aspecto siguiente:

![&quot;Se ha creado la regla&quot;](/help/assets/pt-ruleComplete.png)

1. Haga clic en **[!UICONTROL Guardar]**

1. Vuelva a compilar la propiedad de Launch e impleméntela en el entorno correcto.
