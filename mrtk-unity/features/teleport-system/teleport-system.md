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
# <a name="teleport-system"></a>Teleportiersystem

Das Teleportsystem ist ein Untersystem des MRTK, das die Teleportierung des Benutzers übernimmt, wenn die Anwendung eine nicht transparente Anzeige verwendet. Für AR-Funktionen (z. B. HoloLens) ist das Teleportierungssystem nicht aktiv. Für immersive HMD-Erfahrungen (OpenVR, WMR) kann das Teleportsystem aktiviert werden.

## <a name="enabling-and-disabling"></a>Aktivieren und Deaktivieren

Das Teleportsystem kann aktiviert oder deaktiviert werden, indem das Kontrollkästchen im Profil umgeschaltet wird.
Hierzu können Sie das MixedRealityToolkit-Objekt in der Szene auswählen, auf "Teleport" klicken und dann das Kontrollkästchen "Teleportsystem aktivieren" aktivieren.

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

Das Teleportsystem macht Ereignisse über die [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) -Schnittstelle verfügbar, um Signale zu geben, wenn Teleportaktionen beginnen, enden oder abgebrochen werden.
Weitere Informationen zu den Mechanismen der Ereignisse und der zugehörigen Nutzlast finden Sie in der verknüpften API-Dokumentation.

## <a name="usage"></a>Verwendung

### <a name="how-to-register-for-teleportation-events"></a>Registrieren für Teleportierungsereignisse

Der folgende Code zeigt, wie Sie einen MonoBehaviour erstellen, der auf Teleportierungsereignisse lauscht. In diesem Code wird davon ausgegangen, dass das Teleportsystem aktiviert ist.

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

## <a name="teleporting-on-mrtk"></a>Teleportierung auf MRTK

Verwenden Sie zum Teleportieren mit einem Controller auf MR-Geräten mit Standardkonfigurationen den Fingerabdruck. Um mit artikulierten Händen teleportieren zu können, erstellen Sie eine Geste, bei der ihre Handfläche mit dem Index nach oben zeigt und der Daumen nach außen schneidet, indem Sie den Teleport durch Curling des Zeigefingers vervollständigen. Informationen zum Teleportieren mit Eingabesimulation finden Sie in der aktualisierten Dokumentation des [Eingabesimulationsdiensts](../input-simulation/input-simulation-service.md).

  ![Teleportgeste](../images/teleport/handteleport.gif)
