---
title: HP-Reverb-G2-Controller in Unreal
description: Anweisungen zur Verwendung der HP-Reverb-G2-Controller in openxr und steamvr
author: hferrone
ms.author: jacksonf
ms.date: 10/9/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, Reverb, Reverb G2, HP-Simulator G2, gemischte Realität, Entwicklung, Bewegungs Controller, Benutzereingabe, Features, neues Projekt, Emulator, Dokumentation, Anleitungen, Features, Hologramme, Spieleentwicklung
ms.openlocfilehash: c9d3ea3a8dd52ed0712f9df5c1a789121a68fd35
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638720"
---
# <a name="hp-reverb-g2-controllers-in-unreal"></a><span data-ttu-id="ee29d-104">HP-Reverb-G2-Controller in Unreal</span><span class="sxs-lookup"><span data-stu-id="ee29d-104">HP Reverb G2 Controllers in Unreal</span></span> 

## <a name="getting-started"></a><span data-ttu-id="ee29d-105">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="ee29d-105">Getting started</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ee29d-106">Unreal Engine 4,26 und openxr oder steamvr sind für den Zugriff auf das HP Motion Controller-Plug-in erforderlich, um mit den HP-Reverb-Controllern arbeiten zu können.</span><span class="sxs-lookup"><span data-stu-id="ee29d-106">Unreal Engine 4.26 and either OpenXR or SteamVR is required to access the HP Motion Controller plugin you'll need to work with the HP Reverb G2 controllers.</span></span>

[!INCLUDE[](includes/tabs-g2-controllers-in-unreal.md)]

## <a name="porting-an-existing-openxr-app"></a><span data-ttu-id="ee29d-107">Portieren einer vorhandenen openxr-App</span><span class="sxs-lookup"><span data-stu-id="ee29d-107">Porting an existing OpenXR app</span></span> 

<span data-ttu-id="ee29d-108">Wenn im Spiel für den HP Mixed Reality-Controller keine Controller Bindungen vorhanden sind, versucht die openxr-Laufzeit, die vorhandenen Bindungen dem aktiven Controller zuzuordnen.</span><span class="sxs-lookup"><span data-stu-id="ee29d-108">If no controller bindings exist in the game for the HP Mixed Reality Controller, the OpenXR runtime will attempt to remap the existing bindings to the active controller.</span></span>  <span data-ttu-id="ee29d-109">In diesem Fall verfügt das Spiel über eine Oculus-Berührungs Bindung und keine HP Mixed Reality Controller-Bindungen.</span><span class="sxs-lookup"><span data-stu-id="ee29d-109">In this case, the game has Oculus Touch bindings and no HP Mixed Reality Controller bindings.</span></span>

![Neuzuordnen vorhandener Bindungen, wenn keine Controller Bindungen vorhanden sind](images/reverb-g2-img-04.png)

<span data-ttu-id="ee29d-111">Die Ereignisse werden weiterhin ausgelöst, aber wenn das Spielcontroller spezifische Bindungen verwenden muss, wie die Rechte Menü Schaltfläche, muss das HP Mixed Reality-Interaktions Profil verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="ee29d-111">The events will still fire, but if the game needs to make use of controller specific bindings, like the right menu button, the HP Mixed Reality interaction profile must be used.</span></span>  <span data-ttu-id="ee29d-112">Mehrere Controller Bindungen können pro Aktion angegeben werden, um unterschiedliche Geräte besser zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="ee29d-112">Multiple controller bindings can be specified per action to better support different devices.</span></span>
   
![Verwenden mehrerer Controller Bindungen](images/reverb-g2-img-05.png)

## <a name="adding-input-action-mappings"></a><span data-ttu-id="ee29d-114">Hinzufügen von Eingabe Aktions Zuordnungen</span><span class="sxs-lookup"><span data-stu-id="ee29d-114">Adding input action mappings</span></span> 

<span data-ttu-id="ee29d-115">Definieren Sie eine neue Aktion, und ordnen Sie Sie einem der Tastendruck im HP Mixed Reality Controller-Abschnitt zu.</span><span class="sxs-lookup"><span data-stu-id="ee29d-115">Define a new action and map to one of the key presses in the HP Mixed Reality Controller section.</span></span>

![Definieren neuer Aktionen und Zuordnungen](images/reverb-g2-img-02.png)

<span data-ttu-id="ee29d-117">Der HP-Reverb-G2-Controller verfügt auch über einen analogen Zieh Punkt, der in den Achsen Zuordnungen mit der Bindung "Achsen Achse" verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="ee29d-117">The HP Reverb G2 controller also has an analog grip, which can be used in the axis mappings with the “Squeeze Axis” binding.</span></span>  <span data-ttu-id="ee29d-118">Es gibt eine separate Press-Bindung, die für Aktions Zuordnungen verwendet werden sollte, wenn die Zieh Fläche gedrückt wird.</span><span class="sxs-lookup"><span data-stu-id="ee29d-118">There is a separate Squeeze binding, which should be used for action mappings when the grip button is fully pressed.</span></span> 

![Verwenden der Zuordnungs Achsen Bindungen](images/reverb-g2-img-03.png)

## <a name="adding-input-events"></a><span data-ttu-id="ee29d-120">Hinzufügen von Eingabe Ereignissen</span><span class="sxs-lookup"><span data-stu-id="ee29d-120">Adding input events</span></span>

<span data-ttu-id="ee29d-121">Klicken Sie mit der rechten Maustaste auf einen Blueprint, und suchen Sie im Eingabe System nach den neuen Aktions Namen, um Ereignisse für diese Aktionen hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="ee29d-121">Right click on a Blueprint and search for the new action names from the input system to add events for these actions.</span></span>  <span data-ttu-id="ee29d-122">Hier antwortet der Blueprint auf die Ereignisse mit einer Druck Zeichenfolge, die die aktuelle Schaltfläche und den Achsen Zustand ausstellt.</span><span class="sxs-lookup"><span data-stu-id="ee29d-122">Here the Blueprint is responding to the events with a print string outputting the current button and axis state.</span></span>

![Blaupause, die auf Ereignisse reagiert und den aktuellen Schaltflächen-und Achsen Zustand ausstellt](images/reverb-g2-img-06.png)

### <a name="using-input"></a><span data-ttu-id="ee29d-124">Verwenden von Eingaben</span><span class="sxs-lookup"><span data-stu-id="ee29d-124">Using input</span></span> 

[!INCLUDE[](includes/tabs-g2-controller-mapping-in-unreal.md)]

## <a name="see-also"></a><span data-ttu-id="ee29d-125">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="ee29d-125">See also</span></span>
* [<span data-ttu-id="ee29d-126">Steamvr-Eingabe</span><span class="sxs-lookup"><span data-stu-id="ee29d-126">SteamVR Input</span></span>](https://docs.unrealengine.com/Platforms/VR/SteamVR/HowTo/SteamVRInput/index.html)
* [<span data-ttu-id="ee29d-127">Verwenden von "steamvr" mit Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ee29d-127">Using SteamVR with Windows Mixed Reality</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)
* [<span data-ttu-id="ee29d-128">Unreal Player Kamera</span><span class="sxs-lookup"><span data-stu-id="ee29d-128">Unreal Player Camera</span></span>](https://docs.unrealengine.com/Programming/Tutorials/PlayerCamera/3/index.html)