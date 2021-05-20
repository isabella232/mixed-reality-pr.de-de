---
title: 'Eyetracking (Blickverfolgung): Navigation'
description: Verwenden der Eye-Targeting für die Navigation im MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, EyeTracking,
ms.openlocfilehash: d966bbe1d3a256e55c62532e8101c1f2846e1136
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145275"
---
# <a name="eye-supported-navigation-in-mrtk"></a>Durch die Augen unterstützte Navigation in MRTK

![MRTK](../../images/eye-tracking/mrtk_et_navigation.png)

Stellen Sie sich vor, Sie lesen Informationen zu einem Schiefer, und wenn Sie das Ende des angezeigten Texts erreichen, scrollt der Text automatisch nach oben, um weitere Inhalte anzuzeigen. Oder Sie können den Bereich, in dem Sie sich gerade befinden, problemlos vergrößern. Die Karte passt auch automatisch den Inhalt an, um die interessanten Dinge in Ihrem Sichtfeld beizubehalten. Eine weitere interessante Anwendung ist die freihändige Beobachtung von 3D-Hologrammen, indem die Teile des Hologramms, die Sie betrachten, automatisch nach vorne verschoben werden. Dies sind einige der Beispiele, die auf dieser Seite im Kontext der durch die Augen unterstützten Navigation beschrieben werden.

In den folgenden Beschreibungen wird davon ausgegangen, dass Sie bereits mit der Einrichtung der [Eyetracking in Ihrer MRTK-Szene](eye-tracking-basic-setup.md) und mit den Grundlagen des [Zugriffs auf Eyetrackingdaten](eye-tracking-target-selection.md) in MRTK Unity vertraut sind.
Die im Folgenden beschriebenen Beispiele sind alle Teil der `EyeTrackingDemo-03-Navigation` Szene (Assets/MRTK/Examples/Demos/EyeTracking/Scenes/EyeTrackingDemo-03-Navigation).

**Zusammenfassung:** Automatisches Scrollen von Text, von den Augen anvisierter Schwenk und Zoom einer virtuellen Karte, freihändige anvisierter 3D-Drehung.

## <a name="auto-scroll"></a>Automatisch scrollen

Der automatische Bildlauf ermöglicht es dem Benutzer, durch Texte zu scrollen, ohne einen Finger zu heben.
Fahren Sie einfach mit dem Lesen fort, und der Text scrollt automatisch nach oben oder unten, je nachdem, wo sich der Benutzer befindet.
Sie können mit dem Beispiel beginnen, das in `EyeTrackingDemo-03-Navigation` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes) angegeben ist.
In diesem Beispiel wird eine [TextMesh-Komponente](https://docs.unity3d.com/ScriptReference/TextMesh.html) verwendet, um das flexible Laden und Formatieren von neuem Text zu ermöglichen.
Fügen Sie der Colliderkomponente des Textfelds einfach die folgenden beiden Skripts hinzu, um das automatische Scrollen zu aktivieren:

### <a name="scrollrecttransf"></a>ScrollRectTransf

Um einen Bildlauf durch eine [TextMesh-Komponente](https://docs.unity3d.com/ScriptReference/TextMesh.html) oder allgemeiner ausgedrückt durch eine [RectTransform-Komponente](https://docs.unity3d.com/ScriptReference/RectTransform.html) durchzuführen, können Sie das [ScrollRectTransf-Skript](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollRectTransf) verwenden.
Wenn Sie anstelle von [RectTransform](https://docs.unity3d.com/ScriptReference/RectTransform.html)durch eine Textur scrollen möchten, verwenden Sie [ScrollTexture](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollTexture) anstelle von [ScrollRectTransf.](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollRectTransf)
Im Folgenden werden die Parameter von [ScrollRectTransf,](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollRectTransf) die im Unity-Editor verfügbar sind, ausführlicher erläutert:

Parameter | BESCHREIBUNG
:---- | :----
LimitPanning | Wenn diese Option aktiviert ist, wird der bildlauffähige Inhalt an seiner Grenze beendet.
RectTransfToNavigate | Verweis auf die [RectTransform,](https://docs.unity3d.com/ScriptReference/RectTransform.html) in der ein Bildlauf durchgeführt werden soll.
RefToViewport | Verweis auf das übergeordnete [RectTransform-Element](https://docs.unity3d.com/ScriptReference/RectTransform.html) des bildlauffähigen Inhalts, um den richtigen Offset und die richtige Grenze zu bestimmen.
AutoGazeScrollIsActive | Wenn diese Option aktiviert ist, führt der Text automatisch einen Bildlauf durch, wenn der Benutzer einen *aktiven Bereich* ansieht (z. B. den oberen und unteren Teil des Bildlaufbereichs, wenn die vertikale Bildlaufgeschwindigkeit nicht 0 (null) ist).
ScrollSpeed_x | Wenn ein Wert ungleich 0 (null) festgelegt ist, wird der horizontale Bildlauf aktiviert. Negative Werte bedeuten eine Änderung der Bildlaufrichtung: Von links nach rechts gegenüber von rechts nach links.
ScrollSpeed_y | Wenn ein Wert ungleich 0 (null) festgelegt ist, wird der vertikale Bildlauf aktiviert. Negative Werte bedeuten eine Änderung der Bildlaufrichtung: Nach oben nach unten oder nach oben.
MinDistFromCenterForAutoScroll | Normalisierter minimaler Abstand in x und y vom Mittelpunkt des Trefferfelds des Ziels (0, 0), um zu scrollen. Daher müssen werte zwischen 0 (immer scrollen) und 0,5 (kein Scrollen) liegen.
UseSkim Ausschn. | Wenn diese Option aktiviert ist, werden plötzliche Bildlaufbewegungen verhindert, wenn sie sich schnell um die Suche herumbehindern. Dies kann jedoch dazu führen, dass scrollen weniger reaktionsfähig ist. Sie kann mit dem Wert *SkimUpdateSpeed optimiert* werden.
SkimUpdateUpdateSpeed | Je niedriger der Wert, desto langsamer wird der Bildlauf nach dem Skimming beschleunigt. Empfohlener Wert: 5.

![Bildlaufeinrichtung mit Blick in Unity](../../images/eye-tracking/mrtk_et_nav_scroll.jpg)

### <a name="eyetrackingtarget"></a>EyeTrackingTarget

Das Anfügen der _EyeTrackingTarget-Komponente_ ermöglicht eine flexible Handhabung von Ereignissen im Zusammenhang mit dem Anvisierungsziel mit den Augen.
Im Bildlaufbeispiel wird das Scrollen  von Text veranschaulicht, der beginnt, wenn der Benutzer den Bereich ansieht und beendet wird, wenn der Benutzer *davon* wegsieht.
![Bildlaufeinrichtung mit Eye-Unterstützung in Unity: EyeTrackingTarget](../../images/eye-tracking/mrtk_et_nav_scroll_ettarget.jpg)

## <a name="gaze-supported-pan-and-zoom"></a>Schwenken und Zoomen durch Anving

Wer hat noch keine virtuelle Karte verwendet, um nach seinem Haus zu suchen oder völlig neue Orte zu erkunden? Eyetracking ermöglicht es Ihnen, genau die Teile zu untersuchen, an denen Sie interessiert sind, und nach dem Vergrößern können Sie dem Weg einer Straße folgen, um Ihre Umgebung zu erkunden!
Dies ist nicht nur nützlich für die Untersuchung geografischer Karten, sondern auch zum Auschecken von Details in Fotos, Datenvisualisierungen oder sogar im Livestream übertragenen medizinischen Bildern. Die Verwendung dieser Funktion in Ihrer App ist einfach! Fügen Sie für Inhalte, die in einer [Textur]( https://docs.unity3d.com/ScriptReference/Texture.html) gerendert werden (z. B. ein Foto, gestreamte Daten), einfach das [Skript PanZoomTexture](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.PanZoomTexture) hinzu.
Verwenden Sie [für eine RectTransform-Datei](https://docs.unity3d.com/ScriptReference/RectTransform.html) [PanZoomRectTransf.](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.PanZoomRectTransf) Durch Die Erweiterung [der](#auto-scroll) Funktion "Automatischer Bildlauf" wird im Wesentlichen aktiviert, um gleichzeitig vertikal und horizontal zu scrollen und den Inhalt direkt um den aktuellen Fokuspunkt des Benutzers zu vergrößern.

Parameter | BESCHREIBUNG
:---- | :----
LimitPanning | Wenn diese Option aktiviert ist, wird der bildlauffähige Inhalt an seiner Grenze beendet.
HandZoomEnabledOnStartup | Gibt an, ob Handgesten automatisch aktiviert werden, um eine Zoomgeste auszuführen. Möglicherweise möchten Sie es zunächst deaktivieren, um zu vermeiden, dass versehentlich Zoomaktionen ausgelöst werden.
RendererOfTextureToBeNavigated | Renderer der Textur, in der navigiert werden soll, auf die verwiesen wird.
Zoom_Acceleration | Zoombeschleunigung, die die Steigung der Logistischen Geschwindigkeitsfunktionszuordnung definiert.
Zoom_SpeedMax | Maximale Zoomgeschwindigkeit.
Zoom_MinScale | Minimale Skala der Textur für das Vergrößern, z.B. 0,5f (hälfte der ursprünglichen Größe).
Zoom_MaxScale | Maximale Skala der Textur zum Verkleinern, z. B. 1f (ursprüngliche Größe) oder 2,0f (doppelt so groß wie die ursprüngliche Größe).
Zoom_TimeInSecToZoom | Timed zoom (Zoomzeitfaktor): Nach dem Auslösen wird für die angegebene Zeit in Sekunden ein Zoomen/Verkleinern durchgeführt.
Zoom_Gesture | Typ der Handgeste, die zum Vergrößern/Verkleinern verwendet werden soll.
--- | ---
Pan_AutoScrollIsActive | Wenn diese Option aktiviert ist, führt der Text automatisch einen Bildlauf durch, wenn der Benutzer einen *aktiven Bereich* ansieht (z. B. den oberen und unteren Teil des Bildlaufbereichs, wenn die vertikale Bildlaufgeschwindigkeit nicht 0 (null) ist).
Pan_Speed_x | Wenn ein Wert ungleich 0 (null) festgelegt ist, wird der horizontale Bildlauf aktiviert. Negative Werte bedeuten eine Änderung der Bildlaufrichtung: Von links nach rechts gegenüber von rechts nach links.
Pan_Speed_y | Wenn ein Wert ungleich 0 (null) festgelegt ist, wird der vertikale Bildlauf aktiviert. Negative Werte bedeuten eine Änderung der Bildlaufrichtung: Nach oben nach unten oder nach oben.
Pan_MinDistFromCenter | Normalisierter minimaler Abstand in x und y vom Mittelpunkt des Trefferfelds des Ziels (0, 0), um zu scrollen. Daher müssen werte zwischen 0 (immer scrollen) und 0,5 (kein Scrollen) liegen.
UseSkim Ausschn. | Wenn diese Option aktiviert ist, werden plötzliche Bildlaufbewegungen verhindert, wenn Sie sich schnell umsehen. Dies kann dazu führen, dass das Scrollen weniger reaktionsfähig ist. Sie kann mit dem *Wert SkimSpeedUpdateSpeed* optimiert werden.
SkimSpeedUpdateSpeed | Je niedriger der Wert, desto langsamer wird das Scrollen nach dem Überspringen beschleunigt. Empfohlener Wert: 5.

![Von den Augen unterstützte Einrichtung von Schwenken und Zoomen in Unity](../../images/eye-tracking/mrtk_et_nav_panzoom.jpg)

## <a name="attention-based-3d-rotation"></a>Aufmerksamkeitsbasierte 3D-Drehung

Stellen Sie sich vor, Sie sehen sich ein 3D-Objekt an, und die Teile, die Sie sehen möchten, drehen sich auf Sie zu – so als würde das System Ihre Meinung lesen und wissen, dass das Element ihnen zuwendet!
Dies ist die Idee für aufmerksamkeitsbasierte 3D-Drehungen, mit denen Sie alle Seiten eines Hologramms untersuchen können, ohne einen Finger zu heben.
Um dieses Verhalten zu aktivieren, fügen Sie einfach das [OnLookAtRotateByEyeGaze-Skript](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze) dem Teil Ihres GameObject mit einer [Collider-Komponente](https://docs.unity3d.com/ScriptReference/Collider.html) hinzu.
Sie können mehrere unten aufgeführte Parameter optimieren, um zu begrenzen, wie schnell und in welche Richtung das Hologramm drehen wird.

Wie Sie sich vorstellen können, kann es in einer verzeilten Szene schnell störend sein, wenn dieses Verhalten jederzeit aktiv ist.
Aus diesem Grund empfiehlt es sich, mit deaktivierten Verhaltensweisen zu beginnen und es dann schnell mit sprachgesteuerten Befehlen zu aktivieren.
Alternativ haben wir ein Beispiel in `EyeTrackingDemo-03-Navigation` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes) hinzugefügt, um [TargetMoveToCamera](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.TargetMoveToCamera) zu verwenden, für das Sie ein fokussiertes Ziel auswählen können, und es vor Ihnen steht. Sagen Sie einfach *"Komm zu mir".*

Sobald sie sich im Near-Modus befinden, wird der Automatische Drehungsmodus automatisch aktiviert.
In diesem Modus können Sie ihn von allen Seiten beobachten, indem Sie sich einfach zurückbewegen und ihn betrachten, um ihn herumgehen oder ihn erreichen, um ihn mit der Hand zu greifen und zu drehen. Wenn Sie das Ziel verwerfen (& zusammendrücken oder *"Zurücksenden"* sagen), kehrt es zu seinem ursprünglichen Speicherort zurück und reagiert nicht mehr aus der Entfernung auf Sie.

Parameter | BESCHREIBUNG
:---- | :----
SpeedX | Horizontale Drehgeschwindigkeit.
Schnelle | Vertikale Drehgeschwindigkeit.
InverseX | Um die Richtung der horizontalen Drehung zu umkehren.
Inversey | Zum Umkehren der vertikalen Drehrichtung.
RotationThreshInDegrees | Wenn der Winkel zwischen "Anvischen nach Ziel" und "Kamera zu Ziel" kleiner als dieser Wert ist, tun Sie nichts. Dadurch werden kleine Jitteryrotationen verhindert.
MinRotX | Minimaler horizontaler Drehwinkel. Dies soll die Drehung in verschiedene Richtungen einschränken.
MaxRotX | Maximaler horizontaler Drehwinkel. Dies soll die Drehung in verschiedene Richtungen einschränken.
MinRotY | Minimaler vertikaler Drehwinkel, um die Drehung um die x-Achse zu begrenzen.
MaxRoty | Maximaler vertikaler Drehwinkel, um die Drehung um die y-Achse zu begrenzen.

![Einrichten der 3D-Drehung mit Blick in Unity](../../images/eye-tracking/mrtk_et_nav_rotate.jpg)

Zusammenfassend sollten die oben genannten Skripts ihnen die Verwendung des Anvierens mit den Augen für verschiedene Eingabenavigationsaufgaben ermöglichen, z. B. das Scrollen von Texten, Zoomen und Schwenken von Texturen sowie das Rotieren der Untersuchung von 3D-Hologrammen.

### <a name="see-also"></a>Weitere Informationen

- [Grundlegende MRTK-Einrichtung für die Verwendung der Eyetracking](eye-tracking-basic-setup.md)
- [Durch die Augen unterstützte Zielauswahl](eye-tracking-target-selection.md)

---
[Zurück zu "Eye tracking in the MixedRealityToolkit"](eye-tracking-main.md)
