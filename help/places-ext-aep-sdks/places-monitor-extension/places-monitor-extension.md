---
title: Extensión de monitor de lugares
seo-title: Extensión de monitor de lugares
description: La extensión Monitor de lugares gestiona las interacciones con el sistema operativo para registrar y supervisar los puntos de interés más cercanos al usuario.
seo-description: 'La extensión Monitor de lugares gestiona las interacciones con el sistema operativo para registrar y supervisar los puntos de interés más cercanos al usuario. '
translation-type: tm+mt
source-git-commit: ef720c112bc0de386e070094629c5bab69938e76

---


# Extensión de monitor de lugares {#places-monitor-extension}

La extensión Monitor de lugares gestiona las interacciones con el sistema operativo para registrar y supervisar los puntos de interés más cercanos al usuario. Esta extensión recupera los puntos de interés que deben registrarse desde la extensión Places y pasa las notificaciones de entrada y salida a la extensión Places. Estas notificaciones estarán disponibles como eventos en las reglas de inicio de la plataforma de experiencia.

La extensión Monitor es opcional, ya que es posible que algunos clientes ya estén monitoreando regiones con el sistema operativo. Si este es el caso, asegúrese de agregar las API de extensión de lugares para recibir los puntos de interés más cercanos de la base de datos de lugares y también pasar los eventos de entrada y salida para poder realizar las acciones adecuadas.
