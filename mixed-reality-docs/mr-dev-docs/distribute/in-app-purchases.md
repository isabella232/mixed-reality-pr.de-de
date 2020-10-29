---
title: In-App-Käufe
description: In-App-Käufe werden in Mixed Reality-Apps unterstützt, aber es gibt einige Aufgaben, die Sie einrichten müssen.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: in-App-Käufe, hololens
ms.openlocfilehash: 7174fe555322216b7e547055aaaf7879c01d8f23
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2020
ms.locfileid: "91684846"
---
# <a name="in-app-purchases"></a><span data-ttu-id="511ed-104">In-App-Käufe</span><span class="sxs-lookup"><span data-stu-id="511ed-104">In-app purchases</span></span>

<span data-ttu-id="511ed-105">In-App-Käufe werden in hololens unterstützt, aber es gibt einige Aufgaben, die Sie einrichten müssen.</span><span class="sxs-lookup"><span data-stu-id="511ed-105">In-app purchases are supported in HoloLens, but there is some work to set them up.</span></span>

<span data-ttu-id="511ed-106">Um die in App-Purchase-Funktionalität nutzen zu können, müssen Sie folgende Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="511ed-106">In order to leverage the in app-purchase functionality, you must:</span></span>
* <span data-ttu-id="511ed-107">Erstellen einer XAML- [2D-Ansicht](../design/app-views.md) , die als Slate angezeigt wird</span><span class="sxs-lookup"><span data-stu-id="511ed-107">Create a XAML [2D view](../design/app-views.md) to appear as a slate</span></span>
* <span data-ttu-id="511ed-108">Wechseln Sie zu dieser Option, um die Platzierung zu aktivieren, die die immersive Ansicht verlässt.</span><span class="sxs-lookup"><span data-stu-id="511ed-108">Switch to it to activate placement, which leaves the immersive view</span></span>
* <span data-ttu-id="511ed-109">Aufrufen der API: warten auf [currentapp. requestproductpurchaseasync ("durableitemiapname");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span><span class="sxs-lookup"><span data-stu-id="511ed-109">Call the API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span></span>

<span data-ttu-id="511ed-110">Diese API öffnet das Windows-Betriebssystem-Popup Fenster, das den Namen, die Beschreibung und den Preis in der APP anzeigt.</span><span class="sxs-lookup"><span data-stu-id="511ed-110">This API will bring up the stock Windows OS popup that shows the in-app purchase name, description, and price.</span></span> <span data-ttu-id="511ed-111">Der Benutzer kann dann die Option Kaufoptionen auswählen.</span><span class="sxs-lookup"><span data-stu-id="511ed-111">The user can then choose purchase options.</span></span> <span data-ttu-id="511ed-112">Nachdem die Aktion abgeschlossen ist, muss die APP die Benutzeroberfläche anzeigen, sodass der Benutzer wieder zu seiner [immersiven Ansicht](../design/app-views.md)wechseln kann.</span><span class="sxs-lookup"><span data-stu-id="511ed-112">Once the action is completed, the app will need to present UI which allows the user to switch back to its [immersive view](../design/app-views.md).</span></span>

<span data-ttu-id="511ed-113">Für apps, die auf Desktop basierte Windows Mixed Reality-dashboardend abzielen, ist es nicht erforderlich, manuell zu einer XAML-Ansicht zu wechseln, bevor die requestproductpurchaseasync-API aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="511ed-113">For apps targeting desktop-based Windows Mixed Reality immersive headsets, it is not required to manually switch to a XAML view before calling the RequestProductPurchaseAsync API.</span></span>
