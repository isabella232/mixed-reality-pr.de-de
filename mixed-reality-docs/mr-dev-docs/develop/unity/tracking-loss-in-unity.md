---
title: Verfolgbarkeitsverlust in Unity
description: Behandeln von nach Verfolgungs Verlusten in einer Unity-app.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, Nachverfolgung von Verlusten, Abbild Verlust, Abruf, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 52b81069e6b9f94a2a6a4fb552be4234cf43d1f0
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678419"
---
# <a name="tracking-loss-in-unity"></a><span data-ttu-id="95c14-104">Verfolgbarkeitsverlust in Unity</span><span class="sxs-lookup"><span data-stu-id="95c14-104">Tracking loss in Unity</span></span>

<span data-ttu-id="95c14-105">Wenn sich das Gerät nicht selbst in der Welt finden kann, kann der APP-Verlust nachverfolgt werden.</span><span class="sxs-lookup"><span data-stu-id="95c14-105">When the device cannot locate itself in the world, the app experiences "tracking loss".</span></span> <span data-ttu-id="95c14-106">Standardmäßig hält Unity die Update Schleife an und zeigt dem Benutzer ein Begrüßungs Bild an.</span><span class="sxs-lookup"><span data-stu-id="95c14-106">By default, Unity will pause the update loop and display a splash image to the user.</span></span> <span data-ttu-id="95c14-107">Wenn die Nachverfolgung wieder hergestellt wird, geht das Begrüßungs Bild Weg, und die Update-Schleife wird fortgesetzt.</span><span class="sxs-lookup"><span data-stu-id="95c14-107">When tracking is regained, the splash image goes away and the update loop continues.</span></span>

<span data-ttu-id="95c14-108">Als Alternative kann der Benutzer diesen Übergang manuell durchführen, indem er die Einstellung auslässt.</span><span class="sxs-lookup"><span data-stu-id="95c14-108">As an alternative, the user can manually handle this transition by opting out of the setting.</span></span> <span data-ttu-id="95c14-109">Der gesamte Inhalt wird beim Nachverfolgen des Verlusts als Text gesperrt angezeigt, wenn er nicht verarbeitet wird.</span><span class="sxs-lookup"><span data-stu-id="95c14-109">All content will seem to become body locked during tracking loss if nothing is done to handle it.</span></span>

## <a name="default-handling"></a><span data-ttu-id="95c14-110">Standardbehandlung</span><span class="sxs-lookup"><span data-stu-id="95c14-110">Default Handling</span></span>

<span data-ttu-id="95c14-111">Standardmäßig wird die Update-Schleife der APP sowie alle Nachrichten und Ereignisse für die Dauer des nach Verfolgungs Verlusts angehalten.</span><span class="sxs-lookup"><span data-stu-id="95c14-111">By default, the update loop of the app as well as all messages and events will stop for the duration of tracking loss.</span></span> <span data-ttu-id="95c14-112">Gleichzeitig wird dem Benutzer ein Bild angezeigt.</span><span class="sxs-lookup"><span data-stu-id="95c14-112">At that same time, an image will be displayed to the user.</span></span> <span data-ttu-id="95c14-113">Sie können dieses Bild anpassen, indem Sie zu Edit->Settings->Player wechseln, auf Begrüßungs Bild klicken und das Image der Holographic-nach Verfolgungs Verluste festlegen.</span><span class="sxs-lookup"><span data-stu-id="95c14-113">You can customize this image by going to Edit->Settings->Player, clicking Splash Image, and setting the Holographic Tracking Loss image.</span></span>

## <a name="manual-handling"></a><span data-ttu-id="95c14-114">Manuelle Behandlung</span><span class="sxs-lookup"><span data-stu-id="95c14-114">Manual Handling</span></span>

<span data-ttu-id="95c14-115">Um den nach Verfolgungs Verlust manuell zu behandeln, müssen Sie **Edit** mit  >  **Projekteinstellungen** bearbeiten  >  **Player**  >  **universelle Windows-Plattform Registerkarte "Einstellungen**"  >  **Splash Image**  >  **Windows Holographic** auf der Registerkarte "Einstellungen" die Option "bei Nachverfolgung von Verlusten anhalten und Bild anzeigen" deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="95c14-115">To manually handle tracking loss, you need to go to **Edit** > **Project Settings** > **Player** > **Universal Windows Platform settings tab** > **Splash Image** > **Windows Holographic** and uncheck "On Tracking Loss Pause and Show Image".</span></span> <span data-ttu-id="95c14-116">Danach müssen Sie die Nachverfolgung von Änderungen mit den unten angegebenen APIs verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="95c14-116">After which, you need to handle tracking changes with the APIs specified below.</span></span>

<span data-ttu-id="95c14-117">**Namespace:** *unityengine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="95c14-117">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="95c14-118">**Typ:** *worldmanager*</span><span class="sxs-lookup"><span data-stu-id="95c14-118">**Type:** *WorldManager*</span></span>

* <span data-ttu-id="95c14-119">World Manager macht ein Ereignis verfügbar, um die Nachverfolgung verlorener/ermittelter Objekte (*worldmanager. onpositionzudnorstatechanged*) und eine Eigenschaft zum Abfragen des aktuellen Zustands ("*worldmanager. State*") zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="95c14-119">World Manager exposes an event to detect tracking lost/gained (*WorldManager.OnPositionalLocatorStateChanged*) and a property to query the current state (*WorldManager.state*)</span></span>
* <span data-ttu-id="95c14-120">Wenn der Überwachungs Status nicht aktiv ist, wird die Kamera anscheinend nicht in der virtuellen Welt übersetzt, auch wenn der Benutzer Sie übersetzt.</span><span class="sxs-lookup"><span data-stu-id="95c14-120">When the tracking state is not active, the camera will not appear to translate in the virtual world even as the user translates.</span></span> <span data-ttu-id="95c14-121">Dies bedeutet, dass Objekte keinem physischen Speicherort mehr entsprechen und alle als gesperrt angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="95c14-121">This means objects will no longer correspond to any physical location and all will appear body locked.</span></span>

<span data-ttu-id="95c14-122">Bei der Behandlung von nach Verfolgungs Änderungen müssen Sie entweder die State-Eigenschaft jedes Frames Abfragen oder das *onpositionzuonorstatechanged* -Ereignis behandeln.</span><span class="sxs-lookup"><span data-stu-id="95c14-122">When handling tracking changes on your own you either need to poll for the state property each frame or handle the *OnPositionalLocatorStateChanged* event.</span></span>

### <a name="polling"></a><span data-ttu-id="95c14-123">Abrufen</span><span class="sxs-lookup"><span data-stu-id="95c14-123">Polling</span></span>

<span data-ttu-id="95c14-124">Der wichtigste Status ist *positionzustatusorstate. Active.* Dies bedeutet, dass die Nachverfolgung voll funktionsfähig ist.</span><span class="sxs-lookup"><span data-stu-id="95c14-124">The most important state is *PositionalLocatorState.Active* which means tracking is fully functional.</span></span> <span data-ttu-id="95c14-125">Jeder andere Status führt nur zu Rotations Delta-zu-Haupt-Kameras.</span><span class="sxs-lookup"><span data-stu-id="95c14-125">Any other state will result in only rotational deltas to the main camera.</span></span> <span data-ttu-id="95c14-126">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="95c14-126">For example:</span></span>

```cs
void Update()
{
    switch (UnityEngine.XR.WSA.WorldManager.state)
    {
        case PositionalLocatorState.Active:
            // handle active
            break;
        case PositionalLocatorState.Activating:
        case PositionalLocatorState.Inhibited:
        case PositionalLocatorState.OrientationOnly:
        case PositionalLocatorState.Unavailable:
        default:
            // only rotational information is available
            break;
    }
}
```

### <a name="handling-the-onpositionallocatorstatechanged-event"></a><span data-ttu-id="95c14-127">Behandeln des onpositiondeponorstatechanged-Ereignisses</span><span class="sxs-lookup"><span data-stu-id="95c14-127">Handling the OnPositionalLocatorStateChanged event</span></span>

<span data-ttu-id="95c14-128">Alternativ dazu können Sie auch *onpositiondepingorstatechanged* abonnieren, um die Übergänge zu behandeln:</span><span class="sxs-lookup"><span data-stu-id="95c14-128">Alternatively and more conveniently, you can also subscribe to *OnPositionalLocatorStateChanged* to handle the transitions:</span></span>

```cs
void Start()
{
    UnityEngine.XR.WSA.WorldManager.OnPositionalLocatorStateChanged += WorldManager_OnPositionalLocatorStateChanged;
}

private void WorldManager_OnPositionalLocatorStateChanged(PositionalLocatorState oldState, PositionalLocatorState newState)
{
    if (newState == PositionalLocatorState.Active)
    {
        // Handle becoming active
    }
    else
    {
        // Handle becoming rotational only
    }
}
```

## <a name="see-also"></a><span data-ttu-id="95c14-129">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="95c14-129">See also</span></span>
* [<span data-ttu-id="95c14-130">Behandeln von nach Verfolgungs Verlusten in DirectX</span><span class="sxs-lookup"><span data-stu-id="95c14-130">Handling tracking loss in DirectX</span></span>](../native/coordinate-systems-in-directx.md#handling-tracking-loss)
