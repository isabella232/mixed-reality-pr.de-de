---
title: Weltsperren und Raumanker in Unity
description: Erfahren Sie, wie Sie World Locking Tools und Raumanker in Unity Mixed Reality-Anwendungen verwenden.
author: hferrone
ms.author: v-hferrone
ms.date: 04/7/2021
ms.topic: article
keywords: Unity, Raumanker, Ankerspeicher, HoloLens, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Weltsperrtools, Hologramme
ms.openlocfilehash: 34ef74ab968bff04188b1010eb4c863fd73d76ee6b1dd8a0bd89c7d4232a2be9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208847"
---
# <a name="world-locking-and-spatial-anchors-in-unity"></a>Weltsperren und Raumanker in Unity

![Herobild der Weltsperrtools](images/wlt-img-01.jpeg)

Das Abrufen ihrer Hologramme, um mit Ihnen zu bleiben, sich mit Ihnen zu bewegen oder sich in einigen Fällen relativ zu anderen Hologrammen zu positionieren, ist ein großer Teil der Erstellung Mixed Reality Anwendungen. Dieser Artikel führt Sie durch unsere empfohlene Lösung mithilfe von World Locking Tools, aber wir behandeln auch das manuelle Einrichten von Raumankern in Ihren Unity-Projekten. Bevor wir in code einsteigen, ist es wichtig zu verstehen, wie Unity Koordinatenraum und Anker in seiner eigenen Engine behandelt.

## <a name="world-scale-coordinate-systems"></a>Koordinatensysteme auf Weltrang

Heute besteht der typische Ansatz beim Schreiben von Spielen, Datenvisualisierungs-Apps oder Virtual Reality-Apps darin, ein absolutes **Weltkoordinatensystem** einzurichten, dem alle anderen Koordinaten zuverlässig zugeordnet werden können. In dieser Umgebung finden Sie immer eine stabile Transformation, die eine Beziehung zwischen zwei beliebigen Objekten in dieser Welt definiert. Wenn Sie diese Objekte nicht verschoben haben, bleiben ihre relativen Transformationen immer gleich. Diese Art von globalem Koordinatensystem ist leicht zu erreichen, wenn Sie eine rein virtuelle Welt rendern, in der Sie die gesamte Geometrie im Voraus kennen. Raumbezogene VR-Apps richten heutzutage in der Regel diese Art absoluter Raumkoordinatensysteme mit ihrem Ursprung auf der Etage ein.

Im Gegensatz dazu verfügt ein nicht weiter entferntes Mixed Reality-Gerät wie HoloLens über ein dynamisches sensorgesteuertes Verständnis der Welt und passt sein Wissen im Laufe der Zeit kontinuierlich an die Umgebung des Benutzers an, während es viele Meter über eine gesamte Etage eines Gebäudes führt. Wenn Sie all Ihre Hologramme in einem naiven starren Koordinatensystem platzieren, würden diese Hologramme im Laufe der Zeit im Laufe der Zeit driften, entweder basierend auf der Welt oder relativ zueinander.

Beispielsweise könnte das Headset derzeit davon ausgehen, dass zwei Standorte auf der Welt 4 Meter voneinander entfernt sind, und dann später dieses Verständnis verfeinern und lernen, dass die Standorte tatsächlich 3,9 Meter voneinander entfernt sind. Wenn diese Hologramme anfänglich 4 Meter voneinander in einem einzelnen festen Koordinatensystem entfernt platziert worden wären, würde eines von ihnen immer 0,1 Meter von der realen Welt entfernt angezeigt werden.

Sie können **Raumanker** manuell in Unity platzieren, um die Position eines Hologramms in der physischen Welt aufrechtzuerhalten, wenn der Benutzer mobil ist. Dadurch wird jedoch die Selbstkonsistenz innerhalb der virtuellen Welt umgangen. Verschiedene Anker bewegen sich ständig in Beziehung zueinander und bewegen sich auch durch den globalen Koordinatenraum. In diesem Szenario werden einfache Aufgaben wie das Layout schwierig, und die Physikalische Simulation ist problematisch.

**Die World Locking Tools** bieten Ihnen das Beste aus beiden Welten und stabilisieren ein einzelnes festes Koordinatensystem mithilfe einer internen Bereitstellung von Raumankern, die auf die virtuelle Szene verteilt sind, während sich der Benutzer bewegt. Die Tools analysieren die Koordinaten der Kamera und diese Raumanker für jeden Frame. Anstatt die Koordinaten aller Koordinaten auf der Welt zu ändern, um die Korrekturen in den Koordinaten des Kopfes des Benutzers zu kompensieren, korrigieren die Tools stattdessen nur die Koordinaten des Kopfs.

## <a name="choosing-your-world-locking-approach"></a>Auswählen Ihres weltweiten Sperransatzes

* Es wird **empfohlen,** **World Locking Tools** für alle Ihre Hologrammpositionierungsanforderungen zu verwenden. 
    * World Locking Tools bietet ein stabiles Koordinatensystem, das die sichtbaren Inkonsistenzen zwischen virtuellen und realen Markern minimiert. Anders ausgedrückt: Sie sperrt die gesamte Szene mit einem freigegebenen Pool von Ankern, anstatt jede Gruppe von Objekten mit dem eigenen individuellen Anker der Gruppe zu sperren.
* **Für Unity 2019/2020 mit OpenXR oder dem Windows XR-Plug-In** müssen Sie **ARAnchorManager** verwenden.
* **Für ältere Unity-Versionen oder WSA-Projekte** müssen Sie **WorldAnchor** verwenden.

## <a name="setting-up-world-locking"></a>Einrichten von World Locking 

[!INCLUDE[](includes/world-locking/world-locking-setup.md)]

## <a name="persistent-world-locking"></a>Permanente Weltsperrung

Raumanker speichern Hologramme im realen Raum zwischen Anwendungssitzungen. Nachdem sie im Ankerspeicher der HoloLens gespeichert wurden, können sie in verschiedenen Sitzungen gefunden und geladen werden und sind ein idealer Fallback, wenn keine Internetverbindung besteht.

> [!IMPORTANT]
> Lokale Anker werden auf dem Gerät gespeichert, während Azure-Raumanker in der Cloud gespeichert werden. Wenn Sie Azure Cloud Services zum Speichern Ihrer Anker verwenden möchten, verfügen wir über ein Dokument, in dem Sie durch den Integrationsprozess für [Azure-Raumanker](../mixed-reality-cloud-services.md#azure-spatial-anchors) geführt werden. Beachten Sie, dass Sie sowohl lokale als auch Azure-Anker im selben Projekt haben können, ohne dass Konflikte auftreten.

[!INCLUDE[](includes/world-locking/world-locking-persistence.md)]

## <a name="sharing-coordinate-spaces"></a>Freigeben von Koordinatenbereichen 

Wenn Sie einen weltweit gesperrten Koordinatenraum freigeben möchten, sehen Sie sich unsere umfassende [Dokumentation zur gemeinsamen Erfahrung](shared-experiences-in-unity.md)an.

Beachten Sie, dass Azure Spatial Anchors noch nicht direkt in World Locking Tools unterstützt wird. Daher müssen Sie für freigegebene Erfahrungen manuell Raumanker erstellen.

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie die von uns festgelegte Unity-Entwicklungsprüfpunkt-Journey verfolgen, können Sie die Mixed Reality wichtigsten Bausteine erkunden. Von hier aus können Sie mit dem nächsten Baustein fortfahren:

> [!div class="nextstepaction"]
> [Räumliche Abbildung](spatial-mapping-in-unity.md)

Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:

> [!div class="nextstepaction"]
> [Gemeinsame Erfahrung](shared-experiences-in-unity.md)

Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#2-core-building-blocks) zurückkehren.

## <a name="see-also"></a>Weitere Informationen
* [Einführung in die World Locking Tools](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/IntroFAQ.html)
* [Schnellstarthandbücher](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/QuickStart.html)
* [Tutorials](https://microsoft.github.io/MixedReality-WorldLockingTools-Samples/Tutorial/01_Minimal/01_Minimal.html)
* [Beispiele](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/SampleApplications.html)
* [Persistenz des Raumankers](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK für Unity</a>
* [Erfahrungsskala](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [Räumliche Phase](../../design/coordinate-systems.md#stage-frame-of-reference)
* [Verfolgbarkeitsverlust in Unity](tracking-loss-in-unity.md)
* [Raumanker](../../design/spatial-anchors.md)
* [Gemeinsame Erlebnisse in Unity](shared-experiences-in-unity.md)
