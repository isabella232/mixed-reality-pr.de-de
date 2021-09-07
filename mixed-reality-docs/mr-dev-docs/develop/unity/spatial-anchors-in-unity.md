---
title: Weltsperren und Raumanker in Unity
description: Erfahren Sie, wie Sie World Locking Tools und Raumanker in Unity Mixed Reality-Anwendungen verwenden.
author: hferrone
ms.author: v-hferrone
ms.date: 04/7/2021
ms.topic: article
keywords: Unity, Raumanker, Ankerspeicher, HoloLens, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, World Locking Tools, Hologramme
ms.openlocfilehash: 1de3571d0ad43308acad459021f2c2e9a1a6e1e7
ms.sourcegitcommit: 6f3b3aa31cc3acefba5fa3ac3ba579d9868a4fe4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2021
ms.locfileid: "123244269"
---
# <a name="world-locking-and-spatial-anchors-in-unity"></a>Weltsperren und Raumanker in Unity

![Herobild der Weltsperrtools](images/wlt-img-01.jpeg)

Die Hologramme an Ort und Stelle zu halten, sich mit Ihnen zu bewegen oder sich in einigen Fällen relativ zu anderen Hologrammen zu positionieren, ist ein großer Teil der Erstellung Mixed Reality Anwendungen. In diesem Artikel wird die empfohlene Lösung mithilfe von World Locking Tools beschrieben, aber wir behandeln auch das manuelle Einrichten von Raumankern in Ihren Unity-Projekten. Bevor wir uns mit Code befasst, ist es wichtig zu verstehen, wie Unity den Koordinatenraum und Anker in seiner eigenen Engine behandelt.

## <a name="world-scale-coordinate-systems"></a>Koordinatensysteme auf Weltskala

Heute besteht der typische Ansatz beim Schreiben von Spielen, Datenvisualisierungs-Apps oder Virtual Reality-Apps in der Einrichtung eines **absoluten** Weltkoordinatensystems, dem alle anderen Koordinaten zuverlässig wieder zuordnen können. In dieser Umgebung finden Sie immer eine stabile Transformation, die eine Beziehung zwischen zwei beliebigen Objekten in dieser Welt definiert. Wenn Sie diese Objekte nicht verschieben würden, bleiben ihre relativen Transformationen immer gleich. Diese Art von globalem Koordinatensystem ist leicht zu finden, wenn Sie eine rein virtuelle Welt rendern, in der Sie die gesamte Geometrie im Voraus kennen. VR-Apps im Raummaßstab richten diese Art von absolutem Raumkoordinatensystem in der Regel mit dem Ursprung im Boden ein.

Im Gegensatz dazu verfügt ein nicht gesteuertes Mixed Reality-Gerät wie HoloLens über ein dynamisches sensorgesteuertes Verständnis der Welt und passt sein Wissen über die Umgebung des Benutzers im Laufe der Zeit kontinuierlich an, während es viele Meter über eine ganze Fläche eines Gebäudes läuft. Wenn Sie all Ihre Hologramme in einem naiven starren Koordinatensystem platziert haben, würden diese Hologramme im Laufe der Zeit abdriften, entweder basierend auf der Welt oder relativ zueinander.

Beispielsweise könnte das Headset derzeit glauben, dass zwei Standorte auf der Welt 4 Meter voneinander entfernt sind, und verfeinern später dieses Verständnis, da es lernt, dass die Standorte tatsächlich 3,9 Meter voneinander entfernt sind. Wenn diese Hologramme anfänglich 4 Meter voneinander entfernt in einem einzigen festen Koordinatensystem platziert worden wären, würde eines davon immer 0,1 Meter von der realen Welt entfernt erscheinen.

Sie können raumbezogene Anker manuell in Unity platzieren, um die Position eines Hologramms in der physischen Welt zu erhalten, wenn der Benutzer mobil ist. Dies führt jedoch zu einer **Selbstkonsistenz** innerhalb der virtuellen Welt. Verschiedene Anker bewegen sich ständig in Beziehung zueinander und bewegen sich auch durch den globalen Koordinatenraum. In diesem Szenario werden einfache Aufgaben wie Layout schwierig und die Physikalische Simulation problematisch.

**Die World Locking Tools** bieten Ihnen das Beste aus beiden Welten, indem sie ein einzelnes starres Koordinatensystem mit einer internen Bereitstellung von Raumankern über die virtuelle Szene verteilen, während sich der Benutzer bewegt. Die Tools analysieren die Koordinaten der Kamera und diese Raumanker in jedem Frame. Anstatt die Koordinaten aller Koordinaten auf der Welt zu ändern, um die Korrekturen in den Koordinaten des Kopfs des Benutzers zu kompensieren, korrigieren die Tools stattdessen einfach die Koordinaten des Kopfs.

## <a name="choosing-your-world-locking-approach"></a>Auswählen ihres weltweiten Sperransatzes

* Es wird empfohlen, die **World Locking Tools für** alle Ihre Hologrammpositionierungsanforderungen zu verwenden.
    * World Locking Tools bietet ein stabiles Koordinatensystem, das die sichtbaren Inkonsistenzen zwischen virtuellen und realen Markern minimiert. Anders ausgedrückt: Sie sperrt die gesamte Szene mit einem gemeinsam genutzten Pool von Ankern, anstatt jede Gruppe von Objekten mit dem eigenen individuellen Anker der Gruppe zu sperren.
    * World Locking Tools übernimmt automatisch die erstellung und Verwaltung von Raumankern intern. Sie müssen nicht mit **ARAnchorManager** oder **WorldAnchor** interagieren, um Ihre Hologramme weltweit gesperrt zu halten.
* **Für Unity 2019/2020 mit OpenXR oder dem Windows XR-Plug-In** müssen Sie **ARAnchorManager verwenden.**
* **Für ältere Unity-Versionen oder WSA-Projekte** müssen Sie **WorldAnchor verwenden.**

## <a name="setting-up-world-locking"></a>Einrichten von Weltsperren

[!INCLUDE[](includes/world-locking/world-locking-setup.md)]

## <a name="persistent-world-locking"></a>Persistente Weltsperren

Raumanker speichern Hologramme im realen Raum zwischen Anwendungssitzungen. Nachdem sie im Ankerspeicher des HoloLens gespeichert wurden, können sie in verschiedenen Sitzungen gefunden und geladen werden und sind ein idealer Fallback, wenn keine Internetverbindung besteht.

> [!IMPORTANT]
> Lokale Anker werden auf dem Gerät gespeichert, während Azure-Raumanker in der Cloud gespeichert werden. Wenn Sie Azure Cloud Services zum Speichern Ihrer Anker verwenden möchten, verfügen wir über ein Dokument, in dem Sie durch den Integrationsprozess für [Azure-Raumanker](../mixed-reality-cloud-services.md#azure-spatial-anchors) geführt werden. Beachten Sie, dass Sie sowohl lokale als auch Azure-Anker im selben Projekt haben können, ohne dass Konflikte auftreten.

[!INCLUDE[](includes/world-locking/world-locking-persistence.md)]

## <a name="sharing-coordinate-spaces"></a>Freigeben von Koordinatenräumen

Wenn Sie einen weltweit gesperrten Koordinatenraum freigeben möchten, sehen Sie sich unsere umfassende Dokumentation [zur gemeinsamen Nutzung an.](shared-experiences-in-unity.md)

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie die von uns 2017 an den Unity-Entwicklungsprüfpunkt 2017 2016 2016 2016 durchgeführte Prüfpunkt-Journey für die Unity-Entwicklung fortsetzen, sind Sie gerade dabei, sich mit den Mixed Reality bausteinen zu beginnen. Von hier aus können Sie mit dem nächsten Baustein fortfahren:

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
* [Raumankerpersistenz](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK für Unity</a>
* [Erfahrungsskala](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [Räumliche Stufe](../../design/coordinate-systems.md#stage-frame-of-reference)
* [Verfolgbarkeitsverlust in Unity](tracking-loss-in-unity.md)
* [Raumanker](../../design/spatial-anchors.md)
* [Gemeinsame Erlebnisse in Unity](shared-experiences-in-unity.md)
