---
title: In-App-Käufe
description: Erfahren Sie mehr über die Verwendung von in-App-Käufen in ihren Mixed Reality-apps mit 2D-XAML-Ansichten und Windows-Betriebssystem-Popup.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: in-App-Käufe, hololens, XAML, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: dfc5a0cfcc7a4d63147a753c8892d65dfae5e495
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582955"
---
# <a name="in-app-purchases"></a>In-App-Käufe

In-App-Käufe werden in hololens unterstützt, aber es gibt einige Aufgaben, die Sie einrichten müssen.

Zum Verwenden der in App-Purchase-Funktionalität müssen Sie die folgenden Schritte ausführen:
* Erstellen einer XAML- [2D-Ansicht](../design/app-views.md) , die als Slate angezeigt wird
* Wechseln Sie zu dieser Option, um die Platzierung zu aktivieren, die die immersive Ansicht verlässt.
* Aufrufen der API: warten auf [currentapp. requestproductpurchaseasync ("durableitemiapname");](/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)

Diese API öffnet das Windows-Betriebssystem-Popup Fenster, das den Namen, die Beschreibung und den Preis in der APP anzeigt. Der Benutzer kann dann die Option Kaufoptionen auswählen. Nachdem die Aktion abgeschlossen ist, muss die APP die Benutzeroberfläche anzeigen, sodass der Benutzer wieder zu seiner [immersiven Ansicht](../design/app-views.md)wechseln kann.

Für apps, die auf Desktop basierte Windows Mixed Reality-Produkte abzielen, ist es nicht erforderlich, manuell zu einer XAML-Ansicht zu wechseln, bevor die requestproductpurchaseasync-API aufgerufen wird.