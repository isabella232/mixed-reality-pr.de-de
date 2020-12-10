---
title: Verfolgbarkeitsverlust in Unity
description: Behandeln von nach Verfolgungs Verlusten in einer Unity-app.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, Nachverfolgung von Verlusten, Abbild Verlust, Abruf, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 1df9f579abf43576284d065afa091bb26c631482
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010051"
---
# <a name="tracking-loss-in-unity"></a>Verfolgbarkeitsverlust in Unity

Wenn das Gerät sich nicht auf der ganzen Welt finden kann, kann der APP-Verlust nachverfolgt werden. Standardmäßig hält Unity die Update Schleife an und zeigt dem Benutzer jedes Mal ein Begrüßungs Bild an, wenn die Nachverfolgung verloren geht. Nachdem die Nachverfolgung wieder hergestellt wurde, wird das Begrüßungs Bild entfernt, und die Update-Schleife wird fortgesetzt.

Als Alternative kann der Benutzer diesen Übergang manuell durchführen, indem er die Einstellung auslässt. Der gesamte Inhalt wird beim Nachverfolgen des Verlusts als Text gesperrt angezeigt, wenn er nicht verarbeitet wird.

## <a name="default-handling"></a>Standardbehandlung

Die Update Schleife und alle Meldungen und Ereignisse werden für die Dauer der standardmäßigen Nachverfolgung von Verlusten angehalten. Gleichzeitig wird dem Benutzer ein Bild angezeigt. Sie können dieses Bild anpassen, indem Sie zu Edit->Settings->Player wechseln, auf Begrüßungs Bild klicken und das Image der Holographic-nach Verfolgungs Verluste festlegen.

## <a name="manual-handling"></a>Manuelle Behandlung

Um den nach Verfolgungs Verlust manuell zu behandeln, müssen Sie **Edit** mit  >  **Projekteinstellungen** bearbeiten  >  **Player**  >  **universelle Windows-Plattform Registerkarte "Einstellungen**"  >  **Splash Image**  >  **Windows Holographic** auf der Registerkarte "Einstellungen" die Option "bei Nachverfolgung von Verlusten anhalten und Bild anzeigen" deaktivieren. Danach müssen Sie die Nachverfolgung von Änderungen mit den unten angegebenen APIs verarbeiten.

**Namespace:** *unityengine. XR. WSA*<br>
**Typ:** *worldmanager*

* World Manager macht ein Ereignis verfügbar, um die Nachverfolgung verlorener/ermittelter Objekte (*worldmanager. onpositionzudnorstatechanged*) und eine Eigenschaft zum Abfragen des aktuellen Zustands ("*worldmanager. State*") zu erkennen.
* Wenn der Überwachungs Status nicht aktiv ist, wird die Kamera anscheinend nicht in der virtuellen Welt übersetzt, auch wenn der Benutzer Sie übersetzt. Objekte entsprechen keinem physischen Speicherort, und alle werden als gesperrt angezeigt.

Wenn Sie nach Verfolgungs Änderungen allein behandeln, müssen Sie entweder die State-Eigenschaft jedes Frames abrufen oder das *onpositionzuonorstatechanged* -Ereignis behandeln.

### <a name="polling"></a>Abrufen

Der wichtigste Status ist *positionzustatusorstate. Active*, was bedeutet, dass die Nachverfolgung voll funktionsfähig ist. Jeder andere Status führt nur zu Rotations Delta-zu-Haupt-Kameras. Beispiel:

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

### <a name="handling-the-onpositionallocatorstatechanged-event"></a>Behandeln des onpositiondeponorstatechanged-Ereignisses

Bequemer ist, dass Sie *onpositiondepingorstatechanged* auch abonnieren können, um die Übergänge zu handhaben:

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

## <a name="see-also"></a>Weitere Informationen
* [Behandeln von nach Verfolgungs Verlusten in DirectX](../native/coordinate-systems-in-directx.md#handling-tracking-loss)
