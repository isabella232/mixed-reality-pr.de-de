---
title: In-App-Käufe
description: Erfahren Sie mehr über die Verwendung von in-App-Käufen in ihren Mixed Reality-apps mit 2D-XAML-Ansichten und Windows-Betriebssystem-Popup.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: in-App-Käufe, hololens, XAML, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: a87cc68f67def1d46a3a6ba352e723d356f51fa2
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008670"
---
# <a name="in-app-purchases"></a><span data-ttu-id="1f531-104">In-App-Käufe</span><span class="sxs-lookup"><span data-stu-id="1f531-104">In-app purchases</span></span>

<span data-ttu-id="1f531-105">In-App-Käufe werden in hololens unterstützt, aber es gibt einige Aufgaben, die Sie einrichten müssen.</span><span class="sxs-lookup"><span data-stu-id="1f531-105">In-app purchases are supported in HoloLens, but there's some work to set them up.</span></span>

<span data-ttu-id="1f531-106">Zum Verwenden der in App-Purchase-Funktionalität müssen Sie die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="1f531-106">To use the in app-purchase functionality, you must:</span></span>
* <span data-ttu-id="1f531-107">Erstellen einer XAML- [2D-Ansicht](../design/app-views.md) , die als Slate angezeigt wird</span><span class="sxs-lookup"><span data-stu-id="1f531-107">Create a XAML [2D view](../design/app-views.md) to appear as a slate</span></span>
* <span data-ttu-id="1f531-108">Wechseln Sie zu dieser Option, um die Platzierung zu aktivieren, die die immersive Ansicht verlässt.</span><span class="sxs-lookup"><span data-stu-id="1f531-108">Switch to it to activate placement, which leaves the immersive view</span></span>
* <span data-ttu-id="1f531-109">Aufrufen der API: warten auf [currentapp. requestproductpurchaseasync ("durableitemiapname");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span><span class="sxs-lookup"><span data-stu-id="1f531-109">Call the API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span></span>

<span data-ttu-id="1f531-110">Diese API öffnet das Windows-Betriebssystem-Popup Fenster, das den Namen, die Beschreibung und den Preis in der APP anzeigt.</span><span class="sxs-lookup"><span data-stu-id="1f531-110">This API will bring up the stock Windows OS popup that shows the in-app purchase name, description, and price.</span></span> <span data-ttu-id="1f531-111">Der Benutzer kann dann die Option Kaufoptionen auswählen.</span><span class="sxs-lookup"><span data-stu-id="1f531-111">The user can then choose purchase options.</span></span> <span data-ttu-id="1f531-112">Nachdem die Aktion abgeschlossen ist, muss die APP die Benutzeroberfläche anzeigen, sodass der Benutzer wieder zu seiner [immersiven Ansicht](../design/app-views.md)wechseln kann.</span><span class="sxs-lookup"><span data-stu-id="1f531-112">Once the action is completed, the app will need to present UI, which allows the user to switch back to its [immersive view](../design/app-views.md).</span></span>

<span data-ttu-id="1f531-113">Für apps, die auf Desktop basierte Windows Mixed Reality-Produkte abzielen, ist es nicht erforderlich, manuell zu einer XAML-Ansicht zu wechseln, bevor die requestproductpurchaseasync-API aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="1f531-113">For apps targeting desktop-based Windows Mixed Reality immersive headsets, it isn't required to manually switch to a XAML view before calling the RequestProductPurchaseAsync API.</span></span>
