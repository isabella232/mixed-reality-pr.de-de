---
title: TeleportSystemOverview
description: Übersicht zum Aktivieren und Deaktivieren des Teleportiersystems in MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Teleportiersystem,
ms.openlocfilehash: ee56f62d6e0206249db62d8e7e93cf97cdf8bcc40c35ec0284ebae319870f8ee
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197640"
---
# <a name="teleport-system"></a>Teleportiersystem

Das Teleportiersystem ist ein Untersystem des MRTK, das die Teleportierung des Benutzers verarbeitet, wenn die Anwendung eine nicht transparente Anzeige verwendet. Bei AR-Erlebnissen (wie HoloLens) ist das Teleportiersystem nicht aktiv. Für immersive HMD-Umgebungen (OpenVR, WMR) kann das Teleportiersystem aktiviert werden.

## <a name="enabling-and-disabling"></a>Aktivieren und Deaktivieren

Das Teleportiersystem kann durch Umschalten des Kontrollkästchens in seinem Profil aktiviert oder deaktiviert werden.
Dazu können Sie das MixedRealityToolkit-Objekt in der Szene auswählen, auf „Teleportieren“ klicken und dann das Kontrollkästchen „Teleportiersystem aktivieren“ umschalten.

Dies kann auch zur Laufzeit geschehen:

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

Das Teleportiersystem macht Ereignisse über die Schnittstelle [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) verfügbar, um Signale zum Beginn, Ende oder Abbruch von Teleportieraktionen zu geben.
Weitere Informationen zur Funktionsweise der Ereignisse und der zugehörigen Nutzlast finden Sie in der verknüpften API-Dokumentation.

## <a name="usage"></a>Verwendung

### <a name="how-to-register-for-teleportation-events"></a>Registrieren für Teleportationsereignisse

Der Code unten zeigt, wie Sie ein MonoBehaviour-System erstellen, das nach Teleportationsereignissen lauscht. In diesem Code wird davon ausgegangen, dass das Teleportiersystem aktiviert ist.

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
