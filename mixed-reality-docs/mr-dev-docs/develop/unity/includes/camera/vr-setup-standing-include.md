---
ms.openlocfilehash: 61fe8754192c1fbd0634fd9d1e1994327599321b
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748521"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Verwenden Sie [die MixedRealityPlayspace-Klasse](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) von MRTK für Unity, und legen Sie die **Zielskala** entweder **auf Room oder** Standing **fest:**

![MRTK-Einstellungsfenster](../../images/mrtk-target-scale.png)

MRTK sollte die Position des Playspace und der Kamera automatisch verarbeiten, aber es ist gut, dies zu überprüfen:

![MRTK-Playspace](../../images/mrtk-playspace.png)

1. Erweitern Sie **im Bereich Hierarchie** das **GameObject MixedRealityPlayspace,** und suchen Sie nach dem **untergeordneten Hauptkameraobjekt.**
2. Suchen Sie **im Inspektorbereich** nach der **Komponente Transformieren,** und ändern Sie die **Position** in **(X: 0, Y: 0, Z: 0).**

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Legen Sie den Ursprungsmodus für die Nachverfolgung auf [dem XRInputSubsystem fest.](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html) Rufen Sie nach dem Abrufen des Subsystems [TrySetTrackingOriginMode auf:](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html)

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Floor);
```

Und arbeiten mit [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)von Unity.

![XR-Warte in der Hierarchie](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[Legacy-WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. Wechseln Sie **in den Einstellungen des** Windows **Store-Players** zum Abschnitt Andere Einstellungen.
2. Wählen **Windows Mixed Reality** als Gerät aus, das in älteren Versionen von Unity möglicherweise als **Windows Holographic** aufgeführt wird.
3. Wählen Sie **Virtual Reality Supported (Unterstützte virtuelle Realität) aus.**

Da das Hauptkameraobjekt automatisch als Kamera gekennzeichnet wird, wird unity für alle Bewegungen und Übersetzungen verwendet.

>[!NOTE]
>Diese Einstellungen müssen auf die Kamera in jeder Szene Ihrer App angewendet werden.
>
>Wenn Sie eine neue Szene in Unity erstellen, enthält sie standardmäßig ein Hauptkamera-GameObject in der Hierarchie, das die Kamerakomponente enthält, aber die unten aufgeführten Einstellungen nicht ordnungsgemäß angewendet haben.

**Namespace:** *UnityEngine.XR*<br>
**Typ:** *XRDevice*

Für eine **Erfahrung im Stehend-** oder **Raummaßstab** müssen Sie Inhalte relativ zum Boden platzieren. Sie können den Grund für **[](../../../../design/coordinate-systems.md#spatial-coordinate-systems)** den Boden des Benutzers mithilfe der räumlichen Stufe festlegen, die den vom Benutzer definierten Ursprung auf Bodenebene und die optionale Raumgrenze darstellt, die während der ersten Ausführung eingerichtet wurde.

Um sicherzustellen, dass Unity mit seinem Weltkoordinatensystem auf Bodenebene ausgeführt wird, können Sie festlegen und testen, ob Unity den Raumtyp RoomScale-Nachverfolgung verwendet:

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

* Wenn SetTrackingSpaceType TRUE zurückgibt, hat Unity sein Weltkoordinatensystem erfolgreich umgeschaltet, um den Stageframe [des Verweises nachverfolgung zu können.](../../../../design/coordinate-systems.md#spatial-coordinate-systems)
* Wenn SetTrackingSpaceType false zurückgibt, konnte Unity nicht zum Stageframe des Verweises wechseln, wahrscheinlich weil der Benutzer in seiner Umgebung keinen Boden eingerichtet hat. Obwohl ein falscher Rückgabewert nicht üblich ist, kann dies passieren, wenn die Phase in einem anderen Raum eingerichtet wird und das Gerät in den aktuellen Raum verschoben wird, ohne dass der Benutzer eine neue Stufe eingerichtet hat.

Nachdem Ihre App den Raumtyp RoomScale-Nachverfolgung erfolgreich gesetzt hat, werden Inhalte auf der Ebene y=0 im Boden angezeigt. Der Ursprung bei 0, 0, 0 ist der spezifische Ort im Boden, an dem der Benutzer während der Einrichtung des Raums mit -Z für die Vorwärtsrichtung steht, die er während des Setups hatte.