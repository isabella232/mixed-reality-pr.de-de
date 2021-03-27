---
ms.openlocfilehash: c7e5be36420ef14fe5aaeaafb49c0a990942339f
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636380"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Verwenden Sie die [mixedrealityplayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) -Klasse von mrtk für Unity, und legen Sie die **zielskala** auf " **sitzend**" fest:

![Fenster "mrtk-Einstellungen"](../../images/mrtk-target-scale.png)

Mrtk sollte die Position von Playspace und Kamera automatisch verarbeiten, aber es ist gut, eine Überprüfung durchzuführen:

![Mrtk-Playspace](../../images/mrtk-playspace.png)

1. Erweitern Sie im Bereich **Hierarchie** das " **mixedrealityplayspace** "-gameobject, und suchen Sie nach dem untergeordneten Objekt der **Hauptkamera** .
2. Suchen Sie im **Inspektor** -Panel die **Transformations** Komponente, und ändern Sie die **Position** in **(X: 0, Y: 0, Z: 0)** .

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Legen Sie den nach Verfolgungs Ursprungs Modus für das [xrinputsubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html)fest. Nachdem Sie das Subsystem erhalten haben, wenden Sie sich an [trysettrackingoriginmode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
```

Und arbeiten mit dem [xrrig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)von Unity.

![XR-rig in der Hierarchie](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[Legacy-WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. Wechseln Sie zum Abschnitt **andere Einstellungen** der **Windows Store-Player-Einstellungen** .
2. Wählen Sie **Windows Mixed Reality** als Gerät aus, das in älteren Versionen von Unity als **Windows Holographic** aufgeführt werden kann.
3. **Unterstützte virtuelle Realität** auswählen

Da das Hauptkamera Objekt automatisch als Kamera gekennzeichnet wird, ermöglicht Unity die gesamte Bewegung und Übersetzung.

>[!NOTE]
>Diese Einstellungen müssen in jeder Szene der APP auf die Kamera angewendet werden.
>
>Wenn Sie in Unity eine neue Szene erstellen, enthält diese standardmäßig ein Hauptkamera-gameobject in der Hierarchie, die die Kamera Komponente enthält, aber die unten aufgeführten Einstellungen sind nicht ordnungsgemäß angewendet.

**Namespace:** *unityengine. XR*<br>
**Typ:** *xrdevice*

Zum Erstellen einer reinen **Orientierung** oder einer **Skalierungs** Funktion müssen Sie Unity auf den Typ des stationären nach Verfolgungs Raums festlegen. Stationärer nach Verfolgungs Raum legt das World-Koordinatensystem von Unity fest, um den [stationären Verweis Rahmen](../../../../design/coordinate-systems.md#spatial-coordinate-systems)zu verfolgen. Im Modus der stationären Nachverfolgung wird der Inhalt, der direkt vor dem Standard Speicherort der Kamera (vorwärts ist-Z) im Editor eingefügt wird, vor dem Benutzer angezeigt, wenn die APP gestartet wird.

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

**Namespace:** *unityengine. XR*<br>
**Typ:** *inputtracking*

Bei einer reinen **Orientierung** , z. b. bei einem Video Viewer mit einem 360-Grad (bei dem Positions Aktualisierungen die Illusion zerstören würden), können Sie "XR" festlegen [. Inputtracking. disablepositionaltracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) auf true:

```cs
InputTracking.disablePositionalTracking = true;
```

Um dem Benutzer die Möglichkeit zu geben, den sitzenden Ursprung zu einem späteren Zeitpunkt wieder einzugeben, können Sie den XR-Vorgang für eine Benutzer **freundliche Skalierung** durchführen [. Inputtracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) -Methode:

```cs
InputTracking.Recenter();
```

Wenn Sie eine Umgebung mit [sitzender Skalierung](../../../../design/coordinate-systems.md)entwickeln, können Sie den Welt Ursprung von Unity an der aktuellen Hauptposition des Benutzers wiederholen, indem Sie den **[XR aufrufen. Inputtracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** -Methode.