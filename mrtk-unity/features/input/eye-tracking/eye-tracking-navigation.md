---
title: 'Eyetracking (Blickverfolgung): Navigation'
description: Verwenden der Blickadressierung für die Navigation im MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, EyeTracking,
ms.openlocfilehash: e1ca34054a019e26bebf14282cd351467e5c65e2c2c3fa4f35647dd5aba680ee
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197116"
---
# <a name="eye-supported-navigation-in-mrtk"></a>Eye-supported navigation in MRTK

![MRTK](../../images/eye-tracking/mrtk_et_navigation.png)

Imagine Sie Informationen auf einer Tafel lesen und wenn Sie das Ende des angezeigten Texts erreichen, scrollt der Text automatisch nach oben, um weitere Inhalte anzuzeigen. Oder Sie können den Ort, an dem Sie sich befinden, fluent vergrößern. Die Karte passt den Inhalt auch automatisch an, um die für Sie interessanten Dinge in Ihrem Sichtfeld zu behalten. Eine weitere interessante Anwendung ist die freihnde Beobachtung von 3D-Hologrammen, indem automatisch die Teile des Hologramms, die Sie an den Anfang bringen, an den Anfang gebracht werden. Dies sind einige der Beispiele, die auf dieser Seite im Kontext der navigationsgestützten Navigation beschrieben werden.

Bei den folgenden Beschreibungen wird davon ausgegangen, dass Sie bereits mit der Einrichtung von [EyeTracking in Ihrer MRTK-Szene](eye-tracking-basic-setup.md) und mit den Grundlagen des Zugriffs auf [Eyetrackingdaten](eye-tracking-target-selection.md) in MRTK Unity vertraut sind.
Die folgenden Beispiele sind Teil der Szene `EyeTrackingDemo-03-Navigation` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes/EyeTrackingDemo-03-Navigation).

**Zusammenfassung:** Automatisches Scrollen von Text, Schwenken mit Anvisierten mit den Augen und Zoomen einer virtuellen Karte, 3D-Drehung mit anvisierten Händen.

## <a name="auto-scroll"></a>Automatischer Bildlauf

Automatisches Scrollen ermöglicht es dem Benutzer, durch Texte zu scrollen, ohne einen Finger zu heben.
Fahren Sie einfach mit dem Lesen fort, und der Text scrollt automatisch nach oben oder unten, je nachdem, wo der Benutzer sucht.
Sie können mit dem Beispiel beginnen, das in `EyeTrackingDemo-03-Navigation` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes) bereitgestellt wird.
In diesem Beispiel wird eine [TextMesh-Komponente](https://docs.unity3d.com/ScriptReference/TextMesh.html) verwendet, um das flexible Laden und Formatieren von neuem Text zu ermöglichen.
Um den automatischen Bildlauf zu aktivieren, fügen Sie ihrer Colliderkomponente des Textfelds einfach die folgenden beiden Skripts hinzu:

### <a name="scrollrecttransf"></a>ScrollRectTransf

Um durch ein [TextMesh-Element](https://docs.unity3d.com/ScriptReference/TextMesh.html) oder eine [RectTransform-Komponente](https://docs.unity3d.com/ScriptReference/RectTransform.html) zu scrollen, können Sie das [Skript ScrollRectTransf](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollRectTransf) verwenden.
Wenn Sie durch eine Textur anstelle einer [RectTransform](https://docs.unity3d.com/ScriptReference/RectTransform.html)scrollen möchten, verwenden Sie [ScrollTexture](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollTexture) anstelle von [ScrollRectTransf.](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollRectTransf)
Im Folgenden werden die Parameter von [ScrollRectTransf,](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollRectTransf) die im Unity-Editor verfügbar sind, ausführlicher erläutert:

Parameter | Beschreibung
:---- | :----
LimitPanning | Wenn diese Option aktiviert ist, wird der bildlauffähige Inhalt an seiner Grenze stoppt.
RectTransfToNavigate | Verweis auf das [RectTransform-Format,](https://docs.unity3d.com/ScriptReference/RectTransform.html) in das gescrollt werden soll.
RefToViewport | Verweis auf das übergeordnete [RectTransform-Element](https://docs.unity3d.com/ScriptReference/RectTransform.html) des scrollbaren Inhalts, um den richtigen Offset und die richtige Begrenzung zu bestimmen.
AutoGrammScrollIsActive | Wenn diese Option aktiviert ist, führt der  Text automatisch einen Bildlauf durch, wenn der Benutzer einen aktiven Bereich ansieht (z. B. den oberen und unteren Teil des Bildlaufbereichs, wenn die vertikale Bildlaufgeschwindigkeit nicht 0 (null) ist).
ScrollSpeed_x | Wenn der Wert ungleich 0 (null) festgelegt ist, wird der horizontale Bildlauf aktiviert. Negative Werte bedeuten eine Änderung der Bildlaufrichtung: Von links nach rechts und von rechts nach links.
ScrollSpeed_y | Wenn der Wert ungleich 0 (null) ist, wird der vertikale Bildlauf aktiviert. Negative Werte bedeuten eine Änderung in der Bildlaufrichtung: Nach oben oder nach unten nach oben.
MinDistFromCenterForAutoScroll | Normalisierter minimaler Abstand in x und y vom Mittelpunkt des Trefferfelds des Ziels (0, 0) zum Scrollen. Daher müssen die Werte zwischen 0 (immer scrollen) und 0,5 (kein Bildlauf) liegen.
UseSkim Machen | Wenn diese Option aktiviert ist, werden plötzliche Bildlaufbewegungen verhindert, wenn sie sich schnell um die Suche herumbehindern. Dies kann jedoch dazu führen, dass scrollen weniger reaktionsfähig ist. Sie kann mit dem *SkimUpdateSpeed-Wert optimiert* werden.
SkimUpdateUpdateSpeed | Je niedriger der Wert, desto langsamer wird das Scrollen nach dem Skimming. Empfohlener Wert: 5.

![Bildlaufeinrichtung mit Eye-Unterstützung in Unity](../../images/eye-tracking/mrtk_et_nav_scroll.jpg)

### <a name="eyetrackingtarget"></a>EyeTrackingTarget

Das Anfügen der _EyeTrackingTarget-Komponente_ ermöglicht eine flexible Handhabung von Ereignissen im Zusammenhang mit dem Anvisierungsziel mit den Augen.
Das Bildlaufbeispiel veranschaulicht das Scrollen  von Text, der beginnt, wenn der Benutzer den Bereich ansieht und beendet wird, wenn der Benutzer *davon* wegsieht.
![Bildlaufeinrichtung mit Blick in Unity: EyeTrackingTarget](../../images/eye-tracking/mrtk_et_nav_scroll_ettarget.jpg)

## <a name="gaze-supported-pan-and-zoom"></a>Schwenken und Zoomen durch Anving

Wer bisher noch keine virtuelle Karte verwendet hat, um nach ihrem Haus zu suchen oder völlig neue Orte zu erkunden? Eyetracking ermöglicht es Ihnen, genau die Teile zu untersuchen, an denen Sie interessiert sind, und nach dem Vergrößern können Sie dem Weg einer Straße folgen, um Ihre Umgebung zu erkunden!
Dies ist nicht nur nützlich für die Untersuchung geografischer Karten, sondern auch zum Auschecken von Details in Fotos, Datenvisualisierungen oder sogar im Livestream übertragenen medizinischen Bildern. Die Verwendung dieser Funktion in Ihrer App ist einfach! Fügen Sie für Inhalte, die in einer [Textur]( https://docs.unity3d.com/ScriptReference/Texture.html) gerendert werden (z. B. ein Foto, gestreamte Daten), einfach das [Skript PanZoomTexture](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.PanZoomTexture) hinzu.
Verwenden Sie [für eine RectTransform-Datei](https://docs.unity3d.com/ScriptReference/RectTransform.html) [PanZoomRectTransf.](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.PanZoomRectTransf) Durch Die Erweiterung [der](#auto-scroll) Funktion "Automatischer Bildlauf" wird im Wesentlichen aktiviert, um gleichzeitig vertikal und horizontal zu scrollen und den Inhalt direkt um den aktuellen Fokuspunkt des Benutzers zu vergrößern.

Parameter | Beschreibung
:---- | :----
LimitPanning | Wenn diese Option aktiviert ist, wird der bildlauffähige Inhalt an seiner Grenze stoppt.
HandZoomEnabledOnStartup | Gibt an, ob Handgesten automatisch aktiviert werden, um eine Zoombewegung durchzuführen. Möglicherweise möchten Sie es zuerst deaktivieren, um zu vermeiden, dass versehentlich Zoomaktionen ausgelöst werden.
RendererOfTextureToBeNavigated | Der Renderer, auf den verwiesen wird, der durch die Textur navigiert werden soll.
Zoom_Acceleration | Zoombeschleunigung, die die Schärfe der Zuordnung der Logistischen Geschwindigkeitsfunktion definiert.
Zoom_SpeedMax | Maximale Zoomgeschwindigkeit.
Zoom_MinScale | Mindestskala der Textur zum Vergrößern, z. B. 0,5f (halb so groß wie die ursprüngliche Größe).
Zoom_MaxScale | Maximale Skalierung der Textur für das Verkleinern, z. B. 1f (ursprüngliche Größe) oder 2,0f (doppelte Ursprüngliche Größe).
Zoom_TimeInSecToZoom | Timed zoom (Timed Zoom): Nach dem Auslösen wird ein Vergrößern/Verkleinern für den angegebenen Zeitraum in Sekunden durchgeführt.
Zoom_Gesture | Typ der Handgeste, die zum Vergrößern/Verkleinern verwendet werden soll.
--- | ---
Pan_AutoScrollIsActive | Wenn diese Option aktiviert ist, führt der  Text automatisch einen Bildlauf durch, wenn der Benutzer einen aktiven Bereich ansieht (z. B. den oberen und unteren Teil des Bildlaufbereichs, wenn die vertikale Bildlaufgeschwindigkeit nicht 0 (null) ist).
Pan_Speed_x | Wenn der Wert ungleich 0 (null) festgelegt ist, wird der horizontale Bildlauf aktiviert. Negative Werte bedeuten eine Änderung der Bildlaufrichtung: Von links nach rechts und von rechts nach links.
Pan_Speed_y | Wenn der Wert ungleich 0 (null) ist, wird der vertikale Bildlauf aktiviert. Negative Werte bedeuten eine Änderung in der Bildlaufrichtung: Nach oben oder nach unten nach oben.
Pan_MinDistFromCenter | Normalisierter minimaler Abstand in x und y vom Mittelpunkt des Trefferfelds des Ziels (0, 0) zum Scrollen. Daher müssen die Werte zwischen 0 (immer scrollen) und 0,5 (kein Bildlauf) liegen.
UseSkim Machen | Wenn diese Option aktiviert ist, werden plötzliche Bildlaufbewegungen verhindert, wenn sie sich schnell um die Suche herumbehindern. Dies kann jedoch dazu führen, dass scrollen weniger reaktionsfähig ist. Sie kann mit dem *SkimUpdateSpeed-Wert optimiert* werden.
SkimUpdateUpdateSpeed | Je niedriger der Wert, desto langsamer wird das Scrollen nach dem Skimming. Empfohlener Wert: 5.

![Von den Augen unterstützte Schwenk- und Zoomeinrichtung in Unity](../../images/eye-tracking/mrtk_et_nav_panzoom.jpg)

## <a name="attention-based-3d-rotation"></a>Aufmerksamkeitsbasierte 3D-Drehung

Imagine sich ein 3D-Objekt und die Teile ansehen, die Sie genauer sehen möchten, drehen sich auf Sie zu – als ob das System Ihren Kopf lesen und wissen würde, dass das Element ihnen zuwendet!
Dies ist die Idee für aufmerksamkeitsbasierte 3D-Drehungen, mit denen Sie alle Seiten eines Hologramms untersuchen können, ohne einen Finger zu heben.
Um dieses Verhalten zu aktivieren, fügen Sie einfach das [Skript OnLookAtRotateByEyeGaze](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze) dem Teil Ihres GameObject mit einer [Collider-Komponente](https://docs.unity3d.com/ScriptReference/Collider.html) hinzu.
Sie können mehrere unten aufgeführte Parameter optimieren, um zu begrenzen, wie schnell und in welche Richtung das Hologramm drehen wird.

Wie Sie sich vorstellen können, kann es in einer verzeilten Szene schnell störend sein, wenn dieses Verhalten jederzeit aktiv ist.
Aus diesem Grund empfiehlt es sich, mit deaktivierten Verhaltensweisen zu beginnen und es dann schnell mit sprachgesteuerten Befehlen zu aktivieren.
Alternativ haben wir ein Beispiel in `EyeTrackingDemo-03-Navigation` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes) hinzugefügt, um [TargetMoveToCamera](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.TargetMoveToCamera) zu verwenden, für das Sie ein fokussiertes Ziel auswählen können, und es vor Ihnen steht. Sagen Sie einfach *"Komm zu mir".*

Im Near-Modus wird der Automatische Drehungsmodus automatisch aktiviert.
In diesem Modus können Sie ihn von allen Seiten beobachten, indem Sie sich einfach zurückbewegen und ihn betrachten, um ihn herumgehen oder auf ihn stoßen, um ihn mit der Hand zu greifen und zu drehen. Wenn Sie das Ziel verwerfen (& zusammendrücken oder *"Zurücksenden"* sagen), kehrt es zu seinem ursprünglichen Speicherort zurück und reagiert nicht mehr aus der Entfernung auf Sie.

Parameter | Beschreibung
:---- | :----
SpeedX | Horizontale Drehgeschwindigkeit.
Schnelle | Vertikale Drehgeschwindigkeit.
InverseX | Um die Richtung der horizontalen Drehung zu umkehren.
Inversey | Zum Umkehren der vertikalen Drehrichtung.
RotationThreshInDegrees | Wenn der Winkel zwischen "Anverweise auf Ziel" und "Kamera zu Ziel" kleiner als dieser Wert ist, tun Sie nichts. Dies dient dazu, kleine Jitteryrotationen zu verhindern.
MinRotX | Minimaler horizontaler Drehwinkel. Dies dient dazu, die Drehung in verschiedene Richtungen zu beschränken.
MaxRotX | Maximaler horizontaler Drehwinkel. Dies dient dazu, die Drehung in verschiedene Richtungen zu beschränken.
MinRoty | Minimaler vertikaler Drehwinkel, um die Drehung um die x-Achse einzuschränken.
MaxRotY | Maximaler vertikaler Drehwinkel, um die Drehung um die y-Achse einzuschränken.

![3D-Drehungseinrichtung mit Eye-Unterstützung in Unity](../../images/eye-tracking/mrtk_et_nav_rotate.jpg)

Zusammenfassend sollten die obigen Skripts Ihnen den Einstieg in die Verwendung des Anvierens mit den Augen für verschiedene Eingabenavigationsaufgaben ermöglichen, z. B. das Scrollen von Texten, das Zoomen und Schwenken von Texturen sowie das Drehen der Untersuchung von 3D-Hologrammen.

### <a name="see-also"></a>Siehe auch

- [Grundlegende MRTK-Einrichtung zur Verwendung von Eyetracking](eye-tracking-basic-setup.md)
- [Durch die Augen unterstützte Zielauswahl](eye-tracking-target-selection.md)

---
[Zurück zu "Eye tracking in the MixedRealityToolkit" (Blickverfolgung im MixedRealityToolkit)](eye-tracking-main.md)
