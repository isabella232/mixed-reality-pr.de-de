---
ms.openlocfilehash: f55de39af8c9bc59bb23136203bfc093a4e29f1ea9ddc5ccd147f8c81d6f0020
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212314"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Verwenden Sie die [MixedRealityPlayspace-Klasse](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) von MRTK für Unity, und legen **Sie die Zielskala** auf **Seated fest:**

![MRTK-Einstellungsfenster](../../images/mrtk-target-scale.png)

MRTK sollte die Position des Playspace und der Kamera automatisch verarbeiten, aber es ist gut, folgendes zu überprüfen:

![MRTK-Playspace](../../images/mrtk-playspace.png)

1. Erweitern Sie im **Hierarchiebereich** das **GameObject MixedRealityPlayspace,** und suchen Sie nach dem untergeordneten **Objekt Hauptkamera.**
2. Suchen Sie im **Inspektorbereich** nach der **Komponente Transformieren,** und ändern Sie die **Position** in **(X: 0, Y: 0, Z: 0).**

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Legen Sie den Nachverfolgungsursprungsmodus im [XRInputSubsystem fest.](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html) Rufen Sie nach dem Abrufen des Subsystems [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html)auf:

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
```

Und arbeiten Sie mit [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)von Unity.

![XR-Struktur in der Hierarchie](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[Legacy-WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. Wechseln Sie zum Abschnitt **Andere Einstellungen** der **Windows Store Player-Einstellungen**
2. Wählen Sie **Windows Mixed Reality** als Gerät aus, das in älteren Versionen von Unity als **Windows Holographic** aufgeführt werden kann.
3. Wählen Sie **Virtual Reality Supported (Unterstützte Virtuelle Realität) aus.**

Da das Hauptkameraobjekt automatisch als Kamera gekennzeichnet wird, unterstützt Unity alle Bewegungen und Übersetzungen.

>[!NOTE]
>Diese Einstellungen müssen auf die Kamera in jeder Szene Ihrer App angewendet werden.
>
>Wenn Sie eine neue Szene in Unity erstellen, enthält sie standardmäßig ein Hauptkamera-GameObject in der Hierarchie, das die Kamerakomponente enthält, aber die unten angegebenen Einstellungen nicht ordnungsgemäß angewendet werden.

**Namespace:** *UnityEngine.XR*<br>
**Typ:** *XRDevice*

Zum Erstellen einer **reinen ausrichtungsbasierten** oder **besetzen Benutzeroberfläche** müssen Sie Unity auf den Typ Stationärer Nachverfolgungsbereich festlegen. Der ortsaufstärkungsraum legt das Weltkoordinatensystem von Unity fest, um den [stationären Bezugsrahmen](../../../../design/coordinate-systems.md#spatial-coordinate-systems)nachzuverfolgen. Im Nachverfolgungsmodus "Stationär" werden Inhalte, die im Editor direkt vor der Standardposition der Kamera platziert werden (forward ist -Z), vor dem Benutzer angezeigt, wenn die App gestartet wird.

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

**Namespace:** *UnityEngine.XR*<br>
**Typ:** *InputTracking*

Für eine reine **Ausrichtungserfahrung** wie einen 360-Grad-Videoviewer (bei dem Positionskopfupdates die Vorstellungen verfälschen würden), können Sie dann [XR festlegen. InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) auf TRUE:

```cs
InputTracking.disablePositionalTracking = true;
```

Für eine **benutzerdefinierte Benutzeroberfläche** können Sie XR aufrufen, um dem Benutzer später den ursprungigen Platz zu [geben. InputTracking.Recenter-Methode:](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)

```cs
InputTracking.Recenter();
```

Wenn Sie eine [benutzerdefinierte Benutzeroberfläche](../../../../design/coordinate-systems.md)erstellen, können Sie den weltweiten Ursprung von Unity an der aktuellen Kopfposition des Benutzers durch Aufrufen von **[XR aufrufen. InputTracking.Recenter-Methode.](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)**