---
title: Teleportsystem
description: Übersicht über das Aktivieren und Deaktivieren des Teleport-Systems in MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Teleport-System,
ms.openlocfilehash: 7a49b1fea36eb1809c57abee4cede1216c07d5bf
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176178"
---
# <a name="teleport-system"></a><span data-ttu-id="e5ad8-104">Teleportiersystem</span><span class="sxs-lookup"><span data-stu-id="e5ad8-104">Teleport system</span></span>

<span data-ttu-id="e5ad8-105">Das Teleportsystem ist ein Untersystem des MRTK, das die Teleportierung des Benutzers übernimmt, wenn die Anwendung eine nicht transparente Anzeige verwendet.</span><span class="sxs-lookup"><span data-stu-id="e5ad8-105">The teleport system is a sub-system of the MRTK that handles teleporting the user when the application is using an opaque display.</span></span> <span data-ttu-id="e5ad8-106">Für AR-Funktionen (z. B. HoloLens) ist das Teleportierungssystem nicht aktiv.</span><span class="sxs-lookup"><span data-stu-id="e5ad8-106">For AR experiences (like HoloLens), the teleportation system is not active.</span></span> <span data-ttu-id="e5ad8-107">Für immersive HMD-Erfahrungen (OpenVR, WMR) kann das Teleportsystem aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="e5ad8-107">For immersive HMD experiences (OpenVR, WMR) the teleport system can be enabled.</span></span>

## <a name="enabling-and-disabling"></a><span data-ttu-id="e5ad8-108">Aktivieren und Deaktivieren</span><span class="sxs-lookup"><span data-stu-id="e5ad8-108">Enabling and disabling</span></span>

<span data-ttu-id="e5ad8-109">Das Teleportsystem kann aktiviert oder deaktiviert werden, indem das Kontrollkästchen im Profil umgeschaltet wird.</span><span class="sxs-lookup"><span data-stu-id="e5ad8-109">The teleport system can be enabled or disabled by toggling the checkbox in its profile.</span></span>
<span data-ttu-id="e5ad8-110">Hierzu können Sie das MixedRealityToolkit-Objekt in der Szene auswählen, auf "Teleport" klicken und dann das Kontrollkästchen "Teleportsystem aktivieren" aktivieren.</span><span class="sxs-lookup"><span data-stu-id="e5ad8-110">This can be done by selecting the MixedRealityToolkit object in the scene, clicking "Teleport" and then toggling the "Enable Teleport System" checkbox.</span></span>

<span data-ttu-id="e5ad8-111">Dies kann auch zur Laufzeit erfolgen:</span><span class="sxs-lookup"><span data-stu-id="e5ad8-111">This can also be done at runtime:</span></span>

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

## <a name="events"></a><span data-ttu-id="e5ad8-112">Ereignisse</span><span class="sxs-lookup"><span data-stu-id="e5ad8-112">Events</span></span>

<span data-ttu-id="e5ad8-113">Das Teleportsystem macht Ereignisse über die [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) -Schnittstelle verfügbar, um Signale zu geben, wenn Teleportaktionen beginnen, enden oder abgebrochen werden.</span><span class="sxs-lookup"><span data-stu-id="e5ad8-113">The teleport system exposes events through the [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) interface to provide signals on when teleport actions begin, end, or get cancelled.</span></span>
<span data-ttu-id="e5ad8-114">Weitere Informationen zu den Mechanismen der Ereignisse und der zugehörigen Nutzlast finden Sie in der verknüpften API-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="e5ad8-114">See the linked API documentation for more details on the mechanics of the events and their associated payload.</span></span>

## <a name="usage"></a><span data-ttu-id="e5ad8-115">Verwendung</span><span class="sxs-lookup"><span data-stu-id="e5ad8-115">Usage</span></span>

### <a name="how-to-register-for-teleportation-events"></a><span data-ttu-id="e5ad8-116">Registrieren für Teleportierungsereignisse</span><span class="sxs-lookup"><span data-stu-id="e5ad8-116">How to register for teleportation events</span></span>

<span data-ttu-id="e5ad8-117">Der folgende Code zeigt, wie Sie einen MonoBehaviour erstellen, der auf Teleportierungsereignisse lauscht.</span><span class="sxs-lookup"><span data-stu-id="e5ad8-117">The code below shows how to create a MonoBehaviour that will listen for teleportation events.</span></span> <span data-ttu-id="e5ad8-118">In diesem Code wird davon ausgegangen, dass das Teleportsystem aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="e5ad8-118">This code assumes that the teleport system is enabled.</span></span>

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

## <a name="teleporting-on-mrtk"></a><span data-ttu-id="e5ad8-119">Teleportierung auf MRTK</span><span class="sxs-lookup"><span data-stu-id="e5ad8-119">Teleporting on MRTK</span></span>

<span data-ttu-id="e5ad8-120">Verwenden Sie zum Teleportieren mit einem Controller auf MR-Geräten mit Standardkonfigurationen den Fingerabdruck.</span><span class="sxs-lookup"><span data-stu-id="e5ad8-120">To teleport with a controller on MR devices with default configurations, use the thumbstick.</span></span> <span data-ttu-id="e5ad8-121">Um mit artikulierten Händen teleportieren zu können, erstellen Sie eine Geste, bei der ihre Handfläche mit dem Index nach oben zeigt und der Daumen nach außen schneidet, indem Sie den Teleport durch Curling des Zeigefingers vervollständigen.</span><span class="sxs-lookup"><span data-stu-id="e5ad8-121">To teleport with articulated hands, make a gesture with your palm facing up with the index and thumb sticking outwards, completing the teleport by curling the index finger.</span></span> <span data-ttu-id="e5ad8-122">Informationen zum Teleportieren mit Eingabesimulation finden Sie in der aktualisierten Dokumentation des [Eingabesimulationsdiensts](../input-simulation/input-simulation-service.md).</span><span class="sxs-lookup"><span data-stu-id="e5ad8-122">To teleport with input simulation, please see our updated [Input Simulation Service documentation](../input-simulation/input-simulation-service.md).</span></span>

  ![Teleportgeste](../images/teleport/handteleport.gif)
