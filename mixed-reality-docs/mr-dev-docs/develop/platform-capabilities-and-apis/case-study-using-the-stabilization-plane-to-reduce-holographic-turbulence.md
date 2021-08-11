---
title: 'Fallstudie: Verwenden der Stabilisierungsebene'
description: Erfahren Sie, wie unser Entwicklungsteam die Stabilisierungsebene verwendet hat, um holografische Schwankungen in einer Mixed Reality-Anwendung zu reduzieren.
author: bstrukus
ms.author: bestruku
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Hologramme, Stabilisierung, Fallstudie, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 4227be39c18e43ad712a14dd61217994a8fc761f41f9416b95b511be5396712a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202360"
---
# <a name="case-study---using-the-stabilization-plane-to-reduce-holographic-turbulence"></a>Fallstudie: Verwenden der Stabilisierungsebene zur Reduzierung holografischer Schwankungen

Das Arbeiten mit Hologrammen ist oft schwierig. Das Bewegen eines Raumes und das Betrachten von Hologrammen aus allen unterschiedlichen Winkeln bietet ein Immersionsniveau, das auf einem normalen Computerbildschirm nicht verfügbar ist. Diese Hologramme an Ort und Stelle zu halten und realistisch zu sein, ist eine technische Leistung, die sowohl durch die Microsoft HoloLens Hardware als auch durch das intelligente Design holografischer Apps erzielt wird.

## <a name="the-tech"></a>Die Technologie

Damit Hologramme so aussehen, als ob sie den Raum tatsächlich für Sie freigeben, sollten sie ordnungsgemäß ohne Farbtrennung gerendert werden. Dies wird teilweise durch die in die HoloLens Hardware integrierte Technologie erreicht, die Hologramme auf einer sogenannten [Stabilisierungsebene](hologram-stability.md#reprojection)verankert hält.

Eine Ebene wird durch einen Punkt und eine Normale definiert. Da wir immer möchten, dass die Ebene der Kamera entspricht, müssen wir den Punkt der Ebene festlegen. Wir können HoloLens mitteilen, auf welchen Punkt sich die Verarbeitung konzentrieren soll, um alles verankert und stabil zu halten. Das Festlegen dieses Fokuspunkts ist jedoch app-spezifisch und kann Ihre App abhängig vom Inhalt machen oder unterbrechen.

Hologramme am besten funktionieren, wenn die Stabilisierungsebene ordnungsgemäß angewendet wird, aber was dies tatsächlich bedeutet, hängt vom Typ der Anwendung ab, die Sie erstellen. Sehen wir uns an, wie einige der Apps, die derzeit für HoloLens verfügbar sind, dieses Problem lösen.

## <a name="behind-the-scenes"></a>Abläufe im Hintergrund

Bei der Entwicklung der folgenden Apps haben wir bemerkt, dass Objekte, wenn wir die Ebene nicht verwendet haben, sich bewegen würden, wenn sich der Kopf bewegte. Wir würden auch farbliche Trennung mit schnellen Kopf- oder Hologrammbewegungen sehen. Am Ende haben wir anhand von Testversionen und Fehlern gelernt, wie wir die Stabilisierungsebene am besten verwenden und unsere Apps um die Probleme herum entwerfen, die nicht behoben werden können.

### <a name="galaxy-explorer-stationary-content-3d-interactivity"></a>Galaxy Explorer: Stationärer Inhalt, 3D-Interaktivität

[Galaxy Explorer](../unity/galaxy-explorer.md) verfügt über zwei Hauptelemente in der Szene: die Hauptansicht des Inhalts der Oberfläche und die kleine Ui-Symbolleiste, die Ihrem Anvieren folgt. Für die Stabilisierungslogik sehen wir uns an, was ihr aktueller Anvisiertvektor in jedem Frame überschneidet, um zu bestimmen, ob er auf einer angegebenen Kollisionsebene trifft. In diesem Fall sind die Schichten, an denen wir interessiert sind, die Planeten. Wenn Ihr Anverweise also auf einen Planeten fällt, wird die Stabilisierungsebene dort platziert. Wenn keines der Objekte in der Zielkollisionsschicht erreicht wird, verwendet die App eine sekundäre Ebene "Plan B". Wenn nichts anviert wird, bleibt die Stabilisierungsebene auf dem gleichen Abstand wie beim Auffahren des Inhalts. Die Benutzeroberflächentools werden als Ebenenziel weggelassen, da der Sprung zwischen nah und weit die Stabilität der gesamten Szene reduziert hat.

Das Design von Galaxy Explorer eignet sich gut, um die Stabilität der Dinge zu halten und die Auswirkungen der Farbtrennung zu reduzieren. Dem Benutzer wird empfohlen, den Inhalt zu umkreisen und zu umkreisen, anstatt ihn von Seite zu Seite zu bewegen, und die Planeten laufen langsam genug um, sodass die Farbtrennung nicht wahrnehmbar ist. Darüber hinaus wird eine Konstante von 60 FPS beibehalten, die eine Farbtrennung verhindert.

Um dies selbst zu überprüfen, suchen Sie im [Galaxy Explorer-Code auf GitHub](https://github.com/Microsoft/GalaxyExplorer/tree/master/Assets/Scripts/Utilities)nach einer Datei namens LSRPlaneModifier.cs.

### <a name="holostudio-stationary-content-with-a-ui-focus"></a>HoloStudio: Stationärer Inhalt mit Benutzeroberflächenfokus

In HoloStudio verbringen Sie die meiste Zeit damit, dasselbe Modell zu betrachten, an dem Sie arbeiten. Ihr Anvischen bewegt sich nur dann erheblich, wenn Sie ein neues Tool auswählen oder in der Benutzeroberfläche navigieren möchten, sodass wir die Ebeneneinstellungslogik einfach halten können. Wenn Sie sich die Benutzeroberfläche ansehen, wird die Ebene auf das Benutzeroberflächenelement festgelegt, an dem Ihr Anvischen ausgerichtet ist. Beim Betrachten des Modells ist die Ebene ein festgelegter Abstand, der dem Standardabstand zwischen Ihnen und dem Modell entspricht.

![Die Stabilisierungsebene, die in HoloStudio visualisiert wird, während der Benutzer auf die Schaltfläche Home anviert](images/holostudio-stabilization-plane-500px.png)

### <a name="holotour-and-3d-viewer-stationary-content-with-animation-and-movies"></a>HoloTour und 3D-Viewer: Stationärer Inhalt mit Animationen und Filmen

In HoloTour und 3D-Viewer betrachten Sie ein einsames animiertes Objekt oder einen Film, auf dem 3D-Effekte hinzugefügt werden. Die Stabilisierung in diesen Apps ist auf das festgelegt, was Sie gerade anzeigen.

HoloTour verhindert auch, dass Sie zu weit von Ihrer virtuellen Welt abweichen, indem sie mit Ihnen verschoben wird, anstatt an einem festen Ort zu bleiben. Dadurch wird sichergestellt, dass Sie nicht weit genug von anderen Hologrammen entfernt sind, um Stabilitätsprobleme zu beheben.

![In diesem Beispiel von HoloTour wird die Stabilisierungsebene auf diesen Film von Pantheon von Hadrian festgelegt.](images/holotour-stabilization-plane-500px.jpg)

### <a name="roboraid-dynamic-content-and-environmental-interactions"></a>RoboRaid: Dynamische Inhalte und Umgebungsinteraktionen

Das Festlegen der Stabilisierungsebene in RoboRaid ist überraschend einfach, obwohl es sich um die App handelt, die die plötzlichste Bewegung erfordert. Die Ebene ist darauf ausgerichtet, an den Wänden oder den umgebenden Objekten zu bleiben, und gleitet in einem festen Abstand vor Ihnen, wenn Sie weit genug entfernt sind.

RoboRaid wurde unter Berücksichtigung der Stabilisierungsebene entwickelt. Das Reticle, das sich am meisten verschiebt, da es kopfgesperrt ist, umgeht dies, indem nur Rot und Blau verwendet werden, wodurch jegliche Farbverschiebung minimiert wird. Sie enthält auch ein kleines Maß an Tiefe zwischen den Teilen, wodurch jede Farbblendung minimiert wird, die auftreten würde, indem sie mit einem bereits erwarteten Paralaxeffekt maskiert wird. Die Roboter bewegen sich nicht schnell und fahren nur kurze Entfernungen in regelmäßigen Abständen zurück. Sie bleiben in der Regel etwa 2 Meter vor Ihnen, wo die Stabilisierung standardmäßig festgelegt ist.

### <a name="fragments-and-young-conker-dynamic-content-with-environmental-interaction"></a>Fragmente und Young Conker: Dynamischer Inhalt mit Umgebungsinteraktion

Von Asobo Studio in C++ geschrieben, verwenden Fragmente und Young Conker einen anderen Ansatz zum Festlegen der Stabilisierungsebene. Points of Interest (POI) werden im Code definiert und nach Priorität sortiert. POIs sind In-Game-Inhalte, z. B. das Conker-Modell in Young Conker, Menüs, das zielorientierte Reticle und Logos. Die POIs werden durch das Anvieren des Benutzers überschneidet, und die Ebene wird auf die Mitte des Objekts mit der höchsten Priorität festgelegt. Wenn keine Schnittmenge auftritt, wird die Ebene auf den Standardabstand festgelegt.

Fragmente und Young Conker entwerfen auch um Sie herum, die zu weit von den Hologrammen abweichen, indem sie die App anhalten, wenn Sie sich außerhalb des zuvor überprüften Spielbereichs bewegen. Daher halten sie Sie innerhalb der Grenzen, die gefunden werden, um die stabilste Erfahrung zu bieten.

## <a name="do-it-yourself"></a>Aufzeichnung in Eigenregie

Wenn Sie über eine HoloLens verfügen und die Konzepte in diesem Artikel ausprobieren möchten, können Sie eine Testszene herunterladen, um die folgenden Übungen auszuprobieren. In der Testszene wird die integrierte Unity-Api "jsmo" verwendet, um zu visualisieren, wo Ihre Ebene festgelegt wird. Der Code wurde auch verwendet, um die Screenshots in dieser Fallstudie zu erfassen.
1. Synchronisieren Sie die neueste Version von [MixedRealityToolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity).
2. Öffnen Sie die Szene [HoloToolkit-Examples/Utilities/Scenes/StabilizationPlaneSetting.unity.](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Utilities/Scenes/StabilizationPlaneSetting.unity)
3. Erstellen und konfigurieren Sie das generierte Projekt.
4. Führen Sie auf Ihrem Gerät aus.

### <a name="exercise-1"></a>Übung 1

Es werden mehrere weiße Punkte um Sie herum an unterschiedlichen Ausrichtungen angezeigt. Vor Ihnen werden drei Punkte in unterschiedlichen Tiefen angezeigt. Tippen Sie in die Luft, um zu ändern, auf welchen Punkt die Ebene festgelegt ist. Bewegen Sie sich für diese Übung und für die anderen beiden in Ihrem Raum, während Sie sich an den Punkten bewegen. Drehen Sie den Kopf nach links, rechts, nach oben und unten. Bewegen Sie sich näher an und weiter von den Punkten. Erfahren Sie, wie sie reagieren, wenn die Stabilisierungsebene auf verschiedene Ziele festgelegt ist.

### <a name="exercise-2"></a>Übung 2

Kehren Sie nun nach rechts, bis zwei sich bewegende Punkte angezeigt werden, einer oszilliert auf einem horizontalen Pfad und einer auf einem vertikalen Pfad. Tippen Sie erneut auf die Luft, um zu ändern, auf welchen Punkt die Ebene festgelegt ist. Beachten Sie, dass die Farbtrennung verringert wird und auf dem Punkt angezeigt wird, der mit der Ebene verbunden ist. Tippen Sie erneut, um die Geschwindigkeit des Punkts in der Ebeneneinstellungsfunktion zu verwenden. Dieser Parameter gibt einen Hinweis auf HoloLens über die beabsichtigte Bewegung des Objekts. Es ist wichtig zu wissen, wann dies verwendet werden sollte, da Sie feststellen werden, wenn die Geschwindigkeit an einem Punkt verwendet wird, der andere sich bewegende Punkt eine größere Farbtrennung zeigt. Beachten Sie dies beim Entwerfen Ihrer Apps. Wenn Sie einen zusammenhängenden Fluss zur Bewegung Ihrer Objekte haben, können Sie verhindern, dass Artefakte angezeigt werden.

### <a name="exercise-3"></a>Übung 3

Kehren Sie erneut nach rechts, bis eine neue Konfiguration von Punkten angezeigt wird. In diesem Fall gibt es Punkte in der Entfernung und einen Punkt, der ein- und ausgehend vor ihnen lädt. Tippen Sie in die Luft, um den Punkt zu ändern, auf den die Ebene festgelegt ist, und wechseln Sie zwischen den Punkten im Hintergrund und dem Punkt in Bewegung. Beachten Sie, dass Artefakte überall angezeigt werden, indem Sie die Position der Ebene und die Geschwindigkeit auf die Desortierungspunkte festlegen.

**Tipps**
* Halten Sie ihre Ebeneneinstellungslogik einfach. Wie Sie gesehen haben, benötigen Sie keine komplexen Algorithmen zum Festlegen von Ebenen, um ein immersives Erlebnis zu schaffen. Die Stabilisierungsebene ist nur ein Teil des Mosaiks.
* Verschieben Sie die Ebene nach Möglichkeit immer reibungslos zwischen den Zielen. Das sofortige Wechseln entfernter Ziele kann die Szene visuell stören.
* Erwägen Sie, eine Option in ihrer Ebeneneinstellungslogik zu verwenden, um ein bestimmtes Ziel zu sperren. Auf diese Weise kann die Ebene bei Bedarf für ein Objekt gesperrt werden, z. B. ein Logo oder ein Titelbildschirm.

## <a name="about-the-author"></a>Informationen zum Autor

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Ben Strukus" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Ben Strukus</b><br>Anwendungsentwickler @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Siehe auch
* [MR-Grundlagen 100: Erste Schritte mit Unity](../unity/tutorials/holograms-100.md)
* [Fokuspunkt in Unity](../unity/focus-point-in-unity.md)
* [Hologrammstabilität](hologram-stability.md)
