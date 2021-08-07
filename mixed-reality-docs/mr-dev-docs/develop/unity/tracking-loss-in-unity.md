---
title: Verfolgbarkeitsverlust in Unity
description: Erfahren Sie, wie Sie manuelle und standardmäßige Nachverfolgungsverluste in einer Unity Mixed Reality-App behandeln.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, Nachverfolgungsverlust, Nachverfolgung von Verlustbildern, Abruf, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: fe11c88bec60042901bd7ebb5c55116da97b6e28f0e44e889ef517a03d67245a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211352"
---
# <a name="tracking-loss-in-unity"></a>Verfolgbarkeitsverlust in Unity

Wenn sich das Gerät nicht auf der Welt platzieren kann, kommt es in der App zu "Nachverfolgungsverlust". Standardmäßig hält Unity die Updateschleife an und zeigt dem Benutzer jedes Mal ein Begrüßungsbild an, wenn die Nachverfolgung verloren geht. Sobald die Nachverfolgung wiederherzustellen ist, wird das Begrüßungsimage entfernt, und die Updateschleife wird fortgesetzt.

Alternativ kann der Benutzer diesen Übergang manuell behandeln, indem er die Einstellung abschalten kann. Der gesamte Inhalt scheint während des Nachverfolgungsverlusts gesperrt zu werden, wenn nichts zur Behandlung des Inhalts unternommen wird.

## <a name="default-handling"></a>Standardbehandlung

Die Updateschleife und alle Nachrichten und Ereignisse werden standardmäßig für die Dauer der Nachverfolgung von Verlusten beendet. Gleichzeitig wird dem Benutzer ein Bild angezeigt. Sie können dieses Bild anpassen, indem Sie zu >Einstellungen->Player bearbeiten, auf Begrüßungsbild klicken und das Bild Holographic Tracking Loss festlegen.

## <a name="manual-handling"></a>Manuelle Verarbeitung

Zum manuellen Behandeln von Nachverfolgungsverlusten müssen Sie zur Registerkarte **Einstellungen** für die universelle Project Einstellungen Windows Plattform von Player bearbeiten Windows Holographic wechseln und  >    >    >    >    >   "Bei Nachverfolgungsverlust anhalten und Bild anzeigen" deaktivieren. Danach müssen Sie die Nachverfolgung von Änderungen mit den unten angegebenen APIs verarbeiten.

**Namespace:** *UnityEngine.XR.WSA*<br>
**Typ:** *WorldManager*

* World Manager macht ein Ereignis verfügbar, um verlorene/gewonnene Nachverfolgungen zu erkennen (*WorldManager.OnPositionalLocatorStateChanged*) und eine Eigenschaft zum Abfragen des aktuellen Zustands (*WorldManager.state*).
* Wenn der Nachverfolgungszustand nicht aktiv ist, scheint die Kamera nicht in der virtuellen Welt zu übersetzen, selbst wenn der Benutzer übersetzt. Objekte entsprechen nicht mehr jeder physischen Position, und alle werden als textgesperrt angezeigt.

Wenn Sie die Nachverfolgung von Änderungen selbst verarbeiten, müssen Sie entweder die Zustandseigenschaft für jeden Frame abfragen oder das *OnPositionalLocatorStateChanged-Ereignis* behandeln.

### <a name="polling"></a>Abruf

Der wichtigste Zustand ist *PositionalLocatorState.Active.* Dies bedeutet, dass die Nachverfolgung voll funktionsfähig ist. Jeder andere Zustand führt nur zu Drehdelta zur Hauptkamera. Beispiel:

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

### <a name="handling-the-onpositionallocatorstatechanged-event"></a>Behandeln des OnPositionalLocatorStateChanged-Ereignisses

Sie können *onPositionalLocatorStateChanged* auch abonnieren, um die Übergänge zu verarbeiten:

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

## <a name="see-also"></a>Siehe auch

* [Behandeln von Nachverfolgungsverlusten in DirectX](../native/coordinate-systems-in-directx.md#handling-tracking-loss)
