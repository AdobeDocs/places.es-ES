---
title: Añadir contexto de ubicación a las solicitudes de Analytics
description: Esta sección proporciona información sobre cómo añadir contexto de ubicación a las solicitudes de Analytics.
exl-id: bee7b6e3-a75b-4a07-b6e2-f93ce33aa042
TQID: https://experienceleague.adobe.com/NR-CowJgzUBMVWcbV-EvdyBDsiwLi72yxM-Vjx5oNwk
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
source-wordcount: 512
ht-degree: 2%

---

# Añadir contexto de ubicación a las solicitudes de Analytics {#run-reports-aa-locserv-data}

>[!IMPORTANT]
>
>Este documento supone que el servicio Places está implementado en la aplicación. Para obtener más información acerca de la implementación del servicio Places, consulte [Extensiones de Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Una vez que el servicio Places envíe los eventos de entrada y salida, puede crear reglas en Experience Platform Launch y adjuntar los datos del servicio Places a todos los eventos de Adobe Analytics. Para crear este tipo de regla, seleccione la propiedad en Launch y complete los siguientes pasos:

## &#x200B;1. Crear una regla

1. En la ficha **[!UICONTROL Reglas]**, haga clic en **[!UICONTROL Crear nueva regla]**.

   Recuerde la información siguiente:
   * Si no tiene reglas existentes para esta propiedad, el botón **[!UICONTROL Crear nueva regla]** estará en medio de la pantalla.
   * Si su propiedad tiene reglas, el botón **[!UICONTROL Crear nueva regla]** estará en la parte superior derecha de la pantalla.

## &#x200B;2. Seleccione un evento

1. Asigne un nombre significativo a la regla para que sea fácilmente reconocible en la lista de reglas.

   En este ejemplo, la regla se denomina **[!UICONTROL Adjuntar datos de servicio de Places a eventos de acción de seguimiento de Analytics]**.

1. En la sección **[!UICONTROL Eventos]**, haga clic en **[!UICONTROL Agregar]**.

1. En la lista desplegable **[!UICONTROL Extension]**, seleccione **[!UICONTROL Mobile Core]**.

1. En la lista desplegable **[!UICONTROL Tipo de evento]**, seleccione **[!UICONTROL Rastrear acción]**.

Ahora puede determinar los déclencheur que desea incluir para esta regla. En este ejemplo, el déclencheur se basa en todas las llamadas a `TrackAction`. Después de configurar el evento, haga clic en **[!UICONTROL Conservar cambios]**.

![&quot;crear un evento&quot;](/help/assets/ad-setEvent_use-analytics-data.png)


## &#x200B;3. Adición de condiciones

>[!IMPORTANT]
>
>Complete este procedimiento para añadir condiciones a la regla. De lo contrario, vaya a la sección *Definir la acción* que aparece a continuación.

En este ejemplo, se crea una condición que hace que la regla déclencheur solo para clientes de AT&amp;T.

1. En la sección **[!UICONTROL Condiciones]**, haga clic en **[!UICONTROL Agregar]**.

1. En la lista desplegable **[!UICONTROL Extension]**, seleccione **[!UICONTROL Mobile Core]**.

1. En la lista desplegable **[!UICONTROL Tipo de condición]**, seleccione **[!UICONTROL Nombre de operador]**.

1. En la ventana de la derecha, selecciona la casilla **[!UICONTROL AT&amp;T]**.

1. Haga clic en **[!UICONTROL Conservar cambios]**.

![&quot;crear una condición&quot;](/help/assets/ad-setCondition_use-analytics-data.png)

## &#x200B;4. Defina la acción

1. En la sección **[!UICONTROL Acciones]**, haga clic en **[!UICONTROL Agregar]**.

1. En la lista desplegable **[!UICONTROL Extension]**, seleccione **[!UICONTROL Mobile Core]**.

1. En la lista desplegable **[!UICONTROL Tipo de acción]**, seleccione **[!UICONTROL Adjuntar datos]**.

1. En el panel derecho, en el campo **[!UICONTROL Carga útil JSON]**, escriba los datos que se agregarán a este evento.

1. Haga clic en **[!UICONTROL Conservar cambios]**.

En el panel derecho, puede añadir una carga útil JSON de forma libre que añada datos a un evento de SDK antes de que una extensión que escucha este evento pueda oír el evento. En este ejemplo, algunos datos de contexto se añaden a este evento antes de que la extensión de Analytics lo procese. Los datos de contexto añadidos ahora estarán en la visita saliente de Analytics.

En el ejemplo siguiente, los valores `poi.city` y `poi.name` se agregan a los datos de contexto del evento de Analytics. SDK determina dinámicamente los valores de las claves nuevas cuando se procesa este evento.

![&quot;crear una acción&quot;](/help/assets/ad-setAction_use-analytics-data.png)

## &#x200B;5. Guarde la regla y vuelva a generar la propiedad

Una vez completada la configuración, compruebe que la regla tiene el aspecto siguiente:

![&quot;la regla se ha completado.&quot;](/help/assets/ad-ruleComplete_use-analytics-data.png)

1. Haga clic en **[!UICONTROL Guardar]**

1. Vuelva a compilar la propiedad de Launch e impleméntela en el entorno correcto.
