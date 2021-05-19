---
title: Übersicht über das Teleport-System
description: Übersicht über das Aktivieren und Deaktivieren des Teleport-Systems in MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Teleport-System,
ms.openlocfilehash: a44ad1827597dd0b27bc88a9420a3b251f934afd
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144148"
---
# <a name="teleport-system"></a><span data-ttu-id="8a981-104">Teleportiersystem</span><span class="sxs-lookup"><span data-stu-id="8a981-104">Teleport System</span></span>

<span data-ttu-id="8a981-105">Das Teleportsystem ist ein Untersystem des MRTK, das die Teleportierung des Benutzers verarbeitet, wenn die Anwendung eine nicht transparente Anzeige verwendet.</span><span class="sxs-lookup"><span data-stu-id="8a981-105">The teleport system is a sub-system of the MRTK that handles teleporting the user when the application is using an opaque display.</span></span> <span data-ttu-id="8a981-106">Bei AR-Erfahrungen (z. B. HoloLens) ist das Teleportierungssystem nicht aktiv.</span><span class="sxs-lookup"><span data-stu-id="8a981-106">For AR experiences (like HoloLens), the teleportation system is not active.</span></span> <span data-ttu-id="8a981-107">Für immersive HMD-Umgebungen (OpenVR, WMR) kann das Teleportsystem aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="8a981-107">For immersive HMD experiences (OpenVR, WMR) the teleport system can be enabled.</span></span>

## <a name="enabling-and-disabling"></a><span data-ttu-id="8a981-108">Aktivieren und Deaktivieren</span><span class="sxs-lookup"><span data-stu-id="8a981-108">Enabling and disabling</span></span>

<span data-ttu-id="8a981-109">Das Teleportsystem kann aktiviert oder deaktiviert werden, indem das Kontrollkästchen in seinem Profil umgeschaltet wird.</span><span class="sxs-lookup"><span data-stu-id="8a981-109">The teleport system can be enabled or disabled by toggling the checkbox in its profile.</span></span>
<span data-ttu-id="8a981-110">Hierzu können Sie das MixedRealityToolkit-Objekt in der Szene auswählen, auf "Teleport" klicken und dann das Kontrollkästchen "Teleport-System aktivieren" aktivieren.</span><span class="sxs-lookup"><span data-stu-id="8a981-110">This can be done by selecting the MixedRealityToolkit object in the scene, clicking "Teleport" and then toggling the "Enable Teleport System" checkbox.</span></span>

<span data-ttu-id="8a981-111">Dies kann auch zur Laufzeit erfolgen:</span><span class="sxs-lookup"><span data-stu-id="8a981-111">This can also be done at runtime:</span></span>

```c#
void DisableTeleportSystem()
{
    CoreServices.TeleportSystem.Disable();
}

void EnableTeleportSystem()
{
    CoreServices.TeleportSystem.Enable();
}
```

## <a name="events"></a><span data-ttu-id="8a981-112">Ereignisse</span><span class="sxs-lookup"><span data-stu-id="8a981-112">Events</span></span>

<span data-ttu-id="8a981-113">Das Teleportsystem macht Ereignisse über die Schnittstelle verfügbar, um Signale zu geben, wann [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) Teleportaktionen beginnen, enden oder abgebrochen werden.</span><span class="sxs-lookup"><span data-stu-id="8a981-113">The teleport system exposes events through the [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) interface to provide signals on when teleport actions begin, end, or get cancelled.</span></span>
<span data-ttu-id="8a981-114">Weitere Informationen zur Funktionsweise der Ereignisse und der zugehörigen Nutzlast finden Sie in der verknüpften API-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="8a981-114">See the linked API documentation for more details on the mechanics of the events and their associated payload.</span></span>

## <a name="usage"></a><span data-ttu-id="8a981-115">Verwendung</span><span class="sxs-lookup"><span data-stu-id="8a981-115">Usage</span></span>

### <a name="how-to-register-for-teleportation-events"></a><span data-ttu-id="8a981-116">Registrieren für Teleportationsereignisse</span><span class="sxs-lookup"><span data-stu-id="8a981-116">How to register for teleportation events</span></span>

<span data-ttu-id="8a981-117">Der folgende Code zeigt, wie Sie ein MonoBehaviour-System erstellen, das auf Teleportierungsereignisse lausiert.</span><span class="sxs-lookup"><span data-stu-id="8a981-117">The code below shows how to create a MonoBehaviour that will listen for teleportation events.</span></span> <span data-ttu-id="8a981-118">In diesem Code wird davon ausgegangen, dass das Teleportsystem aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="8a981-118">This code assumes that the teleport system is enabled.</span></span>

```c#
using Microsoft.MixedReality.Toolkit;
using Microsoft.MixedReality.Toolkit.Teleport;
using UnityEngine;

public class TeleportHandlerExample : MonoBehaviour, IMixedRealityTeleportHandler
{
    public void OnTeleportCanceled(TeleportEventData eventData)
    {
        Debug.Log("Teleport Cancelled");
    }

    public void OnTeleportCompleted(TeleportEventData eventData)
    {
        Debug.Log("Teleport Completed");
    }

    public void OnTeleportRequest(TeleportEventData eventData)
    {
        Debug.Log("Teleport Request");
    }

    public void OnTeleportStarted(TeleportEventData eventData)
    {
        Debug.Log("Teleport Started");
    }

    void OnEnable()
    {
        // This is the critical call that registers this class for events. Without this
        // class's IMixedRealityTeleportHandler interface will not be called.
        CoreServices.TeleportSystem.RegisterHandler<IMixedRealityTeleportHandler>(this);
    }

    void OnDisable()
    {
        // Unregistering when disabled is important, otherwise this class will continue
        // to receive teleportation events.
        CoreServices.TeleportSystem.UnregisterHandler<IMixedRealityTeleportHandler>(this);
    }
}
```

## <a name="teleporting-on-mrtk"></a><span data-ttu-id="8a981-119">Teleporting auf MRTK</span><span class="sxs-lookup"><span data-stu-id="8a981-119">Teleporting on MRTK</span></span>

<span data-ttu-id="8a981-120">Verwenden Sie zum Teleportieren mit einem Controller auf MR-Geräten mit Standardkonfigurationen den Fingerabdruck.</span><span class="sxs-lookup"><span data-stu-id="8a981-120">To teleport with a controller on MR devices with default configurations, use the thumbstick.</span></span> <span data-ttu-id="8a981-121">Um mit artikulierten Händen zu teleportieren, erstellen Sie eine Geste, bei der die Handfläche nach oben mit dem Index und dem Daumen nach außen ausgerichtet ist, und härten Sie den Teleport durch Krümmen des Zeigefingers.</span><span class="sxs-lookup"><span data-stu-id="8a981-121">To teleport with articulated hands, make a gesture with your palm facing up with the index and thumb sticking outwards, completing the teleport by curling the index finger.</span></span> <span data-ttu-id="8a981-122">Informationen zum Teleportieren mit der Eingabesimulation finden Sie in unserer aktualisierten [Dokumentation zum Eingabesimulationsdienst.](../input-simulation/input-simulation-service.md)</span><span class="sxs-lookup"><span data-stu-id="8a981-122">To teleport with input simulation, please see our updated [Input Simulation Service documentation](../input-simulation/input-simulation-service.md).</span></span>

  ![Teleportgeste](../images/teleport/handteleport.gif)