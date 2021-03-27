---
ms.openlocfilehash: 5f990569ae4052377cba717b5526bb8ba51b8016
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636383"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Verwenden Sie die [mixedrealityplayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) -Klasse von mrtk für Unity, und legen Sie die **zielskala** entweder auf **Raum** oder auf **Stand** fest:

![Fenster "mrtk-Einstellungen"](../../images/mrtk-target-scale.png)

Mrtk sollte die Position von Playspace und Kamera automatisch verarbeiten, aber es ist gut, eine Überprüfung durchzuführen:

![Mrtk-Playspace](../../images/mrtk-playspace.png)

1. Erweitern Sie im Bereich **Hierarchie** das " **mixedrealityplayspace** "-gameobject, und suchen Sie nach dem untergeordneten Objekt der **Hauptkamera** .
2. Suchen Sie im **Inspektor** -Panel die **Transformations** Komponente, und ändern Sie die **Position** in **(X: 0, Y: 0, Z: 0)** .

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Legen Sie den nach Verfolgungs Ursprungs Modus für das [xrinputsubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html)fest. Nachdem Sie das Subsystem erhalten haben, wenden Sie sich an [trysettrackingoriginmode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Floor);
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

Für eine **Dauer-** oder **Raum Skalierung** müssen Sie Inhalte in Relation zum Boden platzieren. Sie haben eine Begründung für den Benutzer, der die **[räumliche Phase](../../../../design/coordinate-systems.md#spatial-coordinate-systems)** verwendet, die den definierten Ursprung und die optionale Raumgrenze des Benutzers darstellt, die während der ersten Durchführung eingerichtet wird.

Um sicherzustellen, dass Unity mit dem globalen Koordinatensystem auf Grundebene betrieben wird, können Sie festlegen und testen, ob Unity den Bereich für die nach Verfolgungs Fläche von roomscale verwendet:

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```

* Wenn settrackingspacetype true zurückgibt, hat Unity das World-Koordinatensystem erfolgreich umgestellt, um den [stagingframe des Verweises](../../../../design/coordinate-systems.md#spatial-coordinate-systems)nachzuverfolgen.
* Wenn settrackingspacetype false zurückgibt, konnte Unity nicht in den stagingframe des Verweises wechseln. Dies liegt wahrscheinlich daran, dass der Benutzer keine Etage in der Umgebung eingerichtet hat. Obwohl ein falscher Rückgabewert nicht häufig vorkommt, kann dies vorkommen, wenn die Stufe in einem anderen Raum eingerichtet ist und das Gerät in den aktuellen Raum verschoben wird, ohne dass der Benutzer eine neue Stufe einrichten muss.

Nachdem Ihre APP den Typ für die Nachverfolgung von roomscale festgelegt hat, wird der Inhalt auf der Ebene "y = 0" auf der Etage angezeigt. Der Ursprung bei 0, 0, 0 ist die spezifische Stelle auf dem Boden, an der der Benutzer während der Raumeinrichtung Stand, wobei-Z die Vorwärtsrichtung darstellt, die während des Setups aufgetreten ist.