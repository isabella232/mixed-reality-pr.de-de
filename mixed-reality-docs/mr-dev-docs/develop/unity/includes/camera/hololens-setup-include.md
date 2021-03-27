---
ms.openlocfilehash: 7470690a96380184ead7319d4461005042c6db82
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636301"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Führen Sie dieses [Schritt-für-Schritt-Tutorial](../../tutorials/mr-learning-base-01.md) aus, um das Mixed Reality Toolkit in Ihrem Unity-Projekt hinzuzufügen und automatisch zu konfigurieren. Es ist auch möglich, direkt mit der [mixedrealityplayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) -Klasse von mrtk für Unity zu arbeiten und die **zielskala** auf **World** festzulegen:

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
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Unbounded); // Recommendation for OpenXR
```

Sie können [arsession](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) für hololens-Anwendungen verwenden, die mit Anker und Arkit/Arcore besser funktionieren.

![AR-Sitzung in der Hierarchie](../../images/xrsdk-arsession.png)

> [!IMPORTANT]
> Für AR-Sitzung und verwandte Funktionen muss AR Foundation installiert sein.

Es ist auch möglich, die Kamera Änderungen manuell ohne die Verwendung von "arsession" anzuwenden:

1. Auswählen der **Hauptkamera** im **Hierarchie** Panel
1. Suchen Sie im **Inspektor** -Panel die **Transformations** Komponente, und ändern Sie die **Position** in **(X: 0, Y: 0, Z: 0)** .

   ![Kamera im Inspektor-Bereich in Unity](../../images/maincamera-350px.png)  
   *Kamera im Inspektor-Bereich in Unity*

1. Hinzufügen eines **trackedtargedriver** zur **Hauptkamera**

# <a name="legacy-wsa"></a>[Legacy-WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. Auswählen der **Hauptkamera** im **Hierarchie** Panel
1. Suchen Sie im **Inspektor** -Panel die **Transformations** Komponente, und ändern Sie die **Position** in **(X: 0, Y: 0, Z: 0)** .

   ![Kamera im Inspektor-Bereich in Unity](../../images/maincamera-350px.png)  
   *Kamera im Inspektor-Bereich in Unity*

1. Wechseln Sie zum Abschnitt **andere Einstellungen** der **Windows Store-Player-Einstellungen** .
1. Wählen Sie **Windows Mixed Reality** als Gerät aus, das in älteren Versionen von Unity als **Windows Holographic** aufgeführt werden kann.
1. **Unterstützte virtuelle Realität** auswählen

Da das Hauptkamera Objekt automatisch als Kamera gekennzeichnet wird, ermöglicht Unity die gesamte Bewegung und Übersetzung.

>[!NOTE]
>Diese Einstellungen müssen in jeder Szene der APP auf die Kamera angewendet werden.
>
>Wenn Sie in Unity eine neue Szene erstellen, enthält diese standardmäßig ein Hauptkamera-gameobject in der Hierarchie, die die Kamera Komponente enthält, die Einstellungen aber möglicherweise nicht ordnungsgemäß angewendet werden.