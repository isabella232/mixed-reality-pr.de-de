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
# <a name="tracking-loss-in-unity"></a>Verfolgbarkeitsverlust in Unity

Wenn sich das Gerät nicht selbst in der Welt finden kann, kann der APP-Verlust nachverfolgt werden. Standardmäßig hält Unity die Update Schleife an und zeigt dem Benutzer ein Begrüßungs Bild an. Wenn die Nachverfolgung wieder hergestellt wird, geht das Begrüßungs Bild Weg, und die Update-Schleife wird fortgesetzt.

Als Alternative kann der Benutzer diesen Übergang manuell durchführen, indem er die Einstellung auslässt. Der gesamte Inhalt wird beim Nachverfolgen des Verlusts als Text gesperrt angezeigt, wenn er nicht verarbeitet wird.

## <a name="default-handling"></a>Standardbehandlung

Standardmäßig wird die Update-Schleife der APP sowie alle Nachrichten und Ereignisse für die Dauer des nach Verfolgungs Verlusts angehalten. Gleichzeitig wird dem Benutzer ein Bild angezeigt. Sie können dieses Bild anpassen, indem Sie zu Edit->Settings->Player wechseln, auf Begrüßungs Bild klicken und das Image der Holographic-nach Verfolgungs Verluste festlegen.

## <a name="manual-handling"></a>Manuelle Behandlung

Um den nach Verfolgungs Verlust manuell zu behandeln, müssen Sie **Edit** mit  >  **Projekteinstellungen** bearbeiten  >  **Player**  >  **universelle Windows-Plattform Registerkarte "Einstellungen**"  >  **Splash Image**  >  **Windows Holographic** auf der Registerkarte "Einstellungen" die Option "bei Nachverfolgung von Verlusten anhalten und Bild anzeigen" deaktivieren. Danach müssen Sie die Nachverfolgung von Änderungen mit den unten angegebenen APIs verarbeiten.

**Namespace:** *unityengine. XR. WSA*<br>
**Typ:** *worldmanager*

* World Manager macht ein Ereignis verfügbar, um die Nachverfolgung verlorener/ermittelter Objekte (*worldmanager. onpositionzudnorstatechanged*) und eine Eigenschaft zum Abfragen des aktuellen Zustands ("*worldmanager. State*") zu erkennen.
* Wenn der Überwachungs Status nicht aktiv ist, wird die Kamera anscheinend nicht in der virtuellen Welt übersetzt, auch wenn der Benutzer Sie übersetzt. Dies bedeutet, dass Objekte keinem physischen Speicherort mehr entsprechen und alle als gesperrt angezeigt werden.

Bei der Behandlung von nach Verfolgungs Änderungen müssen Sie entweder die State-Eigenschaft jedes Frames Abfragen oder das *onpositionzuonorstatechanged* -Ereignis behandeln.

### <a name="polling"></a>Abrufen

Der wichtigste Status ist *positionzustatusorstate. Active.* Dies bedeutet, dass die Nachverfolgung voll funktionsfähig ist. Jeder andere Status führt nur zu Rotations Delta-zu-Haupt-Kameras. Beispiel:

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

Alternativ dazu können Sie auch *onpositiondepingorstatechanged* abonnieren, um die Übergänge zu behandeln:

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
* [Behandeln von nach Verfolgungs Verlusten in DirectX](../native/coordinate-systems-in-directx.md#handling-tracking-loss)
