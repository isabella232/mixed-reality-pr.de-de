---
title: In-App-Käufe
description: Erfahren Sie, wie Sie In-App-Käufe in Ihren Mixed Reality-Apps mit 2D-XAML-Ansichten und einem Windows Betriebssystem-Popup verwenden.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: In-App-Käufe, HoloLens, XAML, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: fbb957d1044a5c76c19691b875de8f9513bfc4b49bc4cb0dbb98d045d615f1a4
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196148"
---
# <a name="in-app-purchases"></a>In-App-Käufe

In-App-Käufe werden in HoloLens unterstützt, aber es gibt einige Arbeit, sie zu einrichten.

Um die In-App-Kauffunktion zu verwenden, müssen Sie:
* Erstellen einer [XAML-2D-Ansicht,](../design/app-views.md) die als Tafel angezeigt wird
* Wechseln Sie zu ihr, um die Platzierung zu aktivieren, wodurch die immersive Ansicht verlassen wird.
* Aufrufen der API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)

Diese API öffnet das Popupfenster des Windows Betriebssystems, das den Namen, die Beschreibung und den Preis des In-App-Kaufs enthält. Der Benutzer kann dann Kaufoptionen auswählen. Sobald die Aktion abgeschlossen ist, muss die App eine Benutzeroberfläche präsentieren, die es dem Benutzer ermöglicht, zurück zu seiner immersiven [Ansicht zu wechseln.](../design/app-views.md)

Für Apps, die auf desktopbasierte Windows Mixed Reality immersive Headsets abzielen, ist es nicht erforderlich, manuell zu einer XAML-Ansicht zu wechseln, bevor die RequestProductPurchaseAsync-API aufgerufen wird.