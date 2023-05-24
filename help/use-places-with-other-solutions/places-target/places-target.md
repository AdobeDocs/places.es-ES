---
title: Adobe Target
description: Esta sección proporciona información sobre cómo utilizar el servicio Places con Adobe Target.
exl-id: 6ee91fca-ea48-4de2-8dcf-87981813c678
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 3%

---

# Uso del servicio Places con Adobe Target {#places-target}

Este documento supone que la extensión Places está implementada en la aplicación. Si necesita ayuda para implementar la extensión Places, consulte [Extensiones de Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Una vez que la extensión Places envía eventos para entradas y salidas, puede aprovechar Reglas en Launch para adjuntar los datos del servicio Places a los eventos del SDK de Adobe Target. Con la propiedad deseada seleccionada en Launch, puede crear este tipo de regla realizando las siguientes tareas:

## 1. Crear una regla

1. En el **[!UICONTROL Reglas]** pestaña, haga clic en **[!UICONTROL Crear nueva regla]**.

   Recuerde la información siguiente:

   * Si no tiene reglas existentes para esta propiedad, el botón estará en medio de la pantalla.
   * Si la propiedad tiene reglas, el botón se encuentra en la parte superior derecha de la pantalla.

## 2. Seleccionar un evento

1. Asigne un nombre significativo a la regla para que sea fácilmente reconocible en la lista de reglas.

   En este ejemplo, la regla se denomina **[!UICONTROL Adjuntar datos de servicio de Places al contenido de destino solicitado]**.

1. En el **[!UICONTROL Eventos]** , haga clic en **[!UICONTROL Añadir]**.
1. Desde el **[!UICONTROL Extensión]** , seleccione la opción **[!UICONTROL Adobe Target]**.
1. Desde el **[!UICONTROL Tipo de evento]** , seleccione la opción **[!UICONTROL Contenido solicitado]**.
1. Haga clic en **[!UICONTROL Mantener cambios]**.

![añadir un evento](/help/assets/ad-setEvent_target.png)

## 3. Añadir condiciones

>[!IMPORTANT]
>
>Complete este paso si desea agregar condiciones a la regla. De lo contrario, vaya al *Defina la acción* más abajo.

En el ejemplo siguiente, se crea una condición que hace que la regla se almacene en déclencheur solo para los usuarios que han iniciado la aplicación cinco veces o más.

1. En el **[!UICONTROL Condiciones]** , haga clic en **[!UICONTROL Añadir]**.
1. Desde el **[!UICONTROL Extensión]** , seleccione la opción **[!UICONTROL Mobile Core]**.
1. Desde el **[!UICONTROL Tipo de condición]** , seleccione la opción **[!UICONTROL Lanzamientos]**.
1. En el panel derecho, modifique la lista desplegable y los controles numéricos para que la condición se lea **[!UICONTROL El usuario ha iniciado la aplicación un número bueno o igual a 5 veces]**.
1. Haga clic en **[!UICONTROL Mantener cambios]**.

![añadir una condición](/help/assets/ad-setCondition_target.png)

## 4. Defina la acción

1. En el **[!UICONTROL Acciones]** , haga clic en **[!UICONTROL Añadir]**.
1. Desde el **[!UICONTROL Extensión]** , seleccione la opción **[!UICONTROL Mobile Core]**.
1. Desde el **[!UICONTROL Tipo de acción]** , seleccione la opción **[!UICONTROL Adjuntar datos]**.
1. En el panel derecho, en el **[!UICONTROL Carga útil JSON]** , escriba los datos que se agregarán a este evento.
1. Haga clic en **[!UICONTROL Mantener cambios]**.

En el panel derecho, puede añadir una carga útil JSON de forma libre que añada datos a un evento del SDK antes de que las extensiones que escuchan este evento lo oigan.

En el ejemplo siguiente, `poiCity` y `poiName` Los valores de se añaden a **[!UICONTROL mboxparameters]** para cada solicitud que se procesa en el evento de Target. El SDK determina dinámicamente los valores de las nuevas claves en el momento en que se procesa este evento.

>[!TIP]
>
>Esta carga útil JSON utiliza una notación especial para `request` objeto. En el evento original, `request` es una matriz de objetos anónimos. Al adjuntar datos a todos los objetos de una matriz mediante Adjuntar datos, la variable `[*]` La notación en una clave que se sabe que contiene una matriz hace que la carga útil se aplique a todos los objetos de esa matriz.
>
>La notación de `request[*]` puede leerse en voz alta como _para cada objeto de `request` matriz_.

![definir la acción](/help/assets/ad-setAction-target.png)

## 5. Guarde la regla y vuelva a generar la propiedad

Una vez completada la configuración, compruebe que la regla tiene el aspecto siguiente:

![regla completada](/help/assets/ad-ruleComplete-target.png)

1. Haga clic en **[!UICONTROL Guardar]**.
1. Vuelva a compilar la propiedad de Launch e impleméntela en el entorno correcto.
