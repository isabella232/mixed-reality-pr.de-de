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
# <a name="teleport-system"></a>Teleportiersystem

Das Teleportsystem ist ein Untersystem des MRTK, das die Teleportierung des Benutzers verarbeitet, wenn die Anwendung eine nicht transparente Anzeige verwendet. Bei AR-Erfahrungen (z. B. HoloLens) ist das Teleportierungssystem nicht aktiv. Für immersive HMD-Umgebungen (OpenVR, WMR) kann das Teleportsystem aktiviert werden.

## <a name="enabling-and-disabling"></a>Aktivieren und Deaktivieren

Das Teleportsystem kann aktiviert oder deaktiviert werden, indem das Kontrollkästchen in seinem Profil umgeschaltet wird.
Hierzu können Sie das MixedRealityToolkit-Objekt in der Szene auswählen, auf "Teleport" klicken und dann das Kontrollkästchen "Teleport-System aktivieren" aktivieren.

Dies kann auch zur Laufzeit erfolgen:

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

## <a name="events"></a>Ereignisse

Das Teleportsystem macht Ereignisse über die Schnittstelle verfügbar, um Signale zu geben, wann [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) Teleportaktionen beginnen, enden oder abgebrochen werden.
Weitere Informationen zur Funktionsweise der Ereignisse und der zugehörigen Nutzlast finden Sie in der verknüpften API-Dokumentation.

## <a name="usage"></a>Verwendung

### <a name="how-to-register-for-teleportation-events"></a>Registrieren für Teleportationsereignisse

Der folgende Code zeigt, wie Sie ein MonoBehaviour-System erstellen, das auf Teleportierungsereignisse lausiert. In diesem Code wird davon ausgegangen, dass das Teleportsystem aktiviert ist.

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

## <a name="teleporting-on-mrtk"></a>Teleporting auf MRTK

Verwenden Sie zum Teleportieren mit einem Controller auf MR-Geräten mit Standardkonfigurationen den Fingerabdruck. Um mit artikulierten Händen zu teleportieren, erstellen Sie eine Geste, bei der die Handfläche nach oben mit dem Index und dem Daumen nach außen ausgerichtet ist, und härten Sie den Teleport durch Krümmen des Zeigefingers. Informationen zum Teleportieren mit der Eingabesimulation finden Sie in unserer aktualisierten [Dokumentation zum Eingabesimulationsdienst.](../input-simulation/input-simulation-service.md)

  ![Teleportgeste](../images/teleport/handteleport.gif)