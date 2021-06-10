---
ms.openlocfilehash: 6e751f5376110ddc6ae92c75b4182fba8240a356
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748482"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Befolgen Sie dieses [Schritt-für-Schritt-Tutorial,](../../tutorials/mr-learning-base-01.md) um Mixed Reality Toolkit in Ihrem Unity-Projekt hinzuzufügen und automatisch zu konfigurieren. Es ist auch möglich, direkt mit der [MixedRealityPlayspace-Klasse](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) von MRTK für Unity zu arbeiten und die **Zielskala** auf **World** festzulegen:

![MRTK-Einstellungsfenster](../../images/mrtk-target-scale.png)

MRTK sollte die Position des Playspace und der Kamera automatisch behandeln, aber es ist gut, folgendes zu überprüfen:

![MRTK-Playspace](../../images/mrtk-playspace.png)

1. Erweitern Sie im **Hierarchiebereich** das **GameObject MixedRealityPlayspace,** und suchen Sie nach dem untergeordneten **Hauptkameraobjekt.**
2. Suchen Sie im **Inspektorbereich** nach der **Komponente Transformieren,** und ändern Sie die **Position** in **(X: 0, Y: 0, Z: 0).**

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Legen Sie den Nachverfolgungsursprungsmodus im [XRInputSubsystem fest.](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html) Rufen Sie nach dem Abrufen des Subsystems [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html)auf:

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Unbounded); // Recommendation for OpenXR
```

Sie können [ARSession](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) für HoloLens-Anwendungen verwenden, was mit Ankern und ARKit/ARCore besser funktioniert.

![AR-Sitzung in der Hierarchie](../../images/xrsdk-arsession.png)

> [!IMPORTANT]
> AR-Sitzung und zugehörige Features müssen AR Foundation installiert sein.

Es ist auch möglich, die Kameraänderungen manuell anzuwenden, ohne ARSession zu verwenden:

1. Auswählen der **Hauptkamera** im **Hierarchiebereich**
1. Suchen Sie im **Inspektorbereich** nach der **Komponente Transformieren,** und ändern Sie die **Position** in **(X: 0, Y: 0, Z: 0).**

   ![Kamera im Inspektorbereich in Unity](../../images/maincamera-350px.png)  
   *Kamera im Inspektorbereich in Unity*

1. Hinzufügen eines **TrackedPoseDriver** zur **Hauptkamera**

# <a name="legacy-wsa"></a>[Legacy-WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. Auswählen der **Hauptkamera** im **Hierarchiebereich**
1. Suchen Sie im **Inspektorbereich** nach der **Komponente Transformieren,** und ändern Sie die **Position** in **(X: 0, Y: 0, Z: 0).**

   ![Kamera im Inspektorbereich in Unity](../../images/maincamera-350px.png)  
   *Kamera im Inspektorbereich in Unity*

1. Wechseln Sie zum Abschnitt **Andere Einstellungen** der Windows **Store Player-Einstellungen.**
1. Wählen Sie **Windows Mixed Reality** als Gerät aus, das in älteren Versionen von Unity als **Windows Holographic** aufgeführt werden kann.
1. Wählen Sie **Virtual Reality Supported (Unterstützte Virtuelle Realität) aus.**

Da das Hauptkameraobjekt automatisch als Kamera gekennzeichnet wird, unterstützt Unity alle Bewegungen und Übersetzungen.

>[!NOTE]
>Diese Einstellungen müssen in jeder Szene Ihrer App auf die Kamera angewendet werden.
>
>Wenn Sie eine neue Szene in Unity erstellen, enthält sie standardmäßig ein Hauptkamera-GameObject in der Hierarchie, das die Kamerakomponente enthält, aber möglicherweise nicht ordnungsgemäß auf die Einstellungen angewendet wird.