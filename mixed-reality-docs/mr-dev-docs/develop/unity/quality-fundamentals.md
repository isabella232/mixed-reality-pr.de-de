---
title: Qualitätsgrundlagen
description: Erfahren Sie mehr über die Qualitätsstandards beim Entwerfen von Mixed Reality-Anwendungen.
author: qianw211
ms.author: v-qianwen
ms.date: 07/15/2021
ms.topic: article
keywords: Qualitätssicherung, Fallstudie, Projekt, Beispiel, MRTK, Mixed Reality Toolkit, Unity, Beispiel-Apps, Beispiel-Apps, Open Source, Microsoft Store, HoloLens, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 69c6a55b95937c0c6af4920f6ffe0929eebe76ee
ms.sourcegitcommit: 82f7db75d8ecc7ac89c76b0db504126cbcb8f16d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2021
ms.locfileid: "129647530"
---
# <a name="quality-fundamentals"></a>Qualitätsgrundlagen

Quality Fundamentals ist eine HoloLens 2-App, die die Grundlagen der Entwicklung einer großartigen Mixed Reality-Erfahrung veranschaulicht.  Anstatt einfach nur die Qualitätsprobleme in Mixed Reality zu erlernen und zu lesen, können wir jetzt häufigen Umgebungs-, Entwurfs- und Leistungsprobleme und Lösungen aus erster Hand erleben, indem wir die in der App bereitgestellten Optionen auswählen.

Um die App herunterzuladen und zu installieren, wechseln Sie zur Downloadseite der App:

> [!div class="nextstepaction"]
> [Qualitätsgrundlagen](https://www.microsoft.com/p/quality-fundamentals/9mwz852q88fw?activetab=pivot:overviewtab)

![Homepage der Qualitätssicherung](images\qf-homepage.jpg)

In dieser Beispiel-App erfahren Sie mehr über:

>[!div class = "checklist"]
> * [Geräte-E/A und Umgebung:](#device-io-and-environment)Wie sich die Umgebungsfaktoren auf die HoloLens auswirken können.
> * [Spatial Anchors:](#anchor-fundamentals)Ausrichten von Hologrammen an einem physischen Raum mithilfe von Raumankern.
> * [Holographic stability and fidelity (Holografische](#stability-and-fidelity)Stabilität und Genauigkeit): Untersuchen Sie Techniken, um die Stabilität und Genauigkeit der Hologramme.
> * [Grundlagen zu 3D-Medienressourcen:](#3d-asset-fundamentals)Optimieren von 3D-Medienressourcen, um eine hohe visuelle Genauigkeit zu erhalten. 

## <a name="device-io-and-environment"></a>Geräte-E/A und Umgebung

Starten Sie die Quality Fundamentals-App auf HoloLens. Sobald die Startseite der App angezeigt wird, wählen Sie **Geräte-E/A und Umgebung aus.**  Wir untersuchen, wie sich die HoloLens und die umgebungsbezogene Umgebung auf die räumliche Zuordnung, Nachverfolgung und Platzierung von Hologrammen auswirken. 

### <a name="surfaces"></a>Oberflächen

Spiegel oder Oberflächen mit gespiegelten Oberflächen können die HoloLens der Form des Objekts verwirren.  Objekte, die auf der Oberfläche reflektiert werden, können vom Gerät als sich ändernde Umgebung interpretiert werden, was dazu führen kann, dass das Gerät die Nachverfolgung verliert.  Wenn gespiegelte Oberflächen Herausforderungen für HoloLens verursachen, sollten Sie einen Bildschirm oder versetzbare Blinds hinzufügen.

Weitere Informationen finden Sie unter [Oberflächen in einem Raum](/hololens/hololens-environment-considerations#surfaces-in-a-space) in HoloLens Überlegungen zur [Umgebung](/hololens/hololens-environment-considerations).

### <a name="lighting"></a>Beleuchtung

HoloLens leistung kann sich entweder durch sehr niedrige oder sehr helle Lichtbedingungen negativ auswirken.  Die Nachverfolgungssensoren HoloLens 500 bis 1.000 Lux Licht benötigen, um optimal arbeiten zu können. Sie können einen Luxmeter oder eine mobile App verwenden, um die Lichtmenge in Ihrem Raum zu messen.

Weitere Informationen finden Sie unter [Beleuchtung](/hololens/hololens-environment-considerations?branch=pr-en-us-3071#lighting) in HoloLens [Überlegungen zur Umgebung.](/hololens/hololens-environment-considerations)

## <a name="anchor-fundamentals"></a>Grundlagen des Ankers

Um zu erfahren, wie Sie hologramme Spatial Anchors einem physischen Raum ausrichten können, wählen Sie auf der Startseite der App **Anchor Fundametals** aus.

In diesem Teil der App werden die folgenden Benutzerszenarien untersucht:

>[!div class = "checklist"]
> * Was geschieht, wenn kein Anker auf ein Objekt angewendet wird?
> * Wenn mehrere Spatial Anchors für eine Gruppe von -Objekten verwendet werden.
> * Freigeben eines Raumanker für mehrere Projektmitarbeiter mithilfe eines QR-Codes.
> * Ankerplatzierung für sehr große Objekte in einem Raum.

Weitere Informationen finden Sie unter [Spatial Anchors](../../design/spatial-anchors.md) in der [Mixed Reality Dokumentation.](../../design/spatial-anchors.md)

## <a name="stability-and-fidelity"></a>Stabilität und Genauigkeit

Wählen Sie auf der Startseite der Anwendung **Stabilität und Fidelity** aus, um zu erfahren, wie Sie die Hologrammstabilität verbessern können.

Wir untersuchen die folgenden schlüsseln Konzepte:

>[!div class = "checklist"]
> * [Framerate](#frame-rate).
> * [Late Stage Reprojection (LSR)](#late-stage-reprojection-lsr).
> * [Z-Fighting](#z-fighting).
> * [Antialiasing](#anti-aliasing).

### <a name="frame-rate"></a>Bildfrequenz

Um die bestmögliche Hologrammerfahrung zu bieten, müssen Anwendungsentwickler 60 Frames pro Sekunde (FPS) verwalten.  In diesem Teil der App können Sie zwischen verschiedenen Optionen für die Dreiecksanzahl umschalten, um den Unterschied bei verschiedenen Frameraten zu erkennen.

![Optimierung der Dreiecksanzahl](images\qf-triangle-count-optimization.png)

Weitere Informationen finden Sie im Artikel zur [Hologrammstabilität](../platform-capabilities-and-apis/hologram-stability.md) unter Bildfrequenz. [](../platform-capabilities-and-apis/hologram-stability.md#frame-rate)

### <a name="late-stage-reprojection-lsr"></a>Neuprojektion in später Phase (LSR)

Die Neuprojektion wird verwendet, um Hologramme zu stabilisiert, wenn sich Benutzer um ihren Raum bewegen.  Probieren Sie die verschiedenen Neuprojektionsoptionen aus, die von diesem Teil der App bereitgestellt werden, um den Unterschied in der Hologrammqualität zu erkennen.

![Probieren Sie die verschiedenen Optionen für die Neuprojektion aus, um den Unterschied zu erkennen.](images\qf-lsr-modes.jpg)

Ausführliche Informationen finden Sie im [Artikel zur](../platform-capabilities-and-apis/hologram-stability.md#reprojection) [Hologrammstabilität](../platform-capabilities-and-apis/hologram-stability.md) unter Neuprojektion.

### <a name="z-fighting"></a>Z-Fighting

Z-Fighting tritt auf, wenn die Mixed Reality-Anwendung nicht erkennen kann, welches Objekt sich vor dem anderen befindet.  Sie werden feststellen, dass die holografischen Objekte flackern, wenn sie denselben Z-Tiefenwert erhalten.  Erleben Sie die Auswirkungen von Z-Fighting in der App, indem Sie die Platzierung eines holografischen Objekts ändern, in diesem Fall das Logo auf einem Fahrrad.

![Erleben Sie Z-Fighting mit Objektplatzierungen.](images\qf-z-fighting.jpg)

Ausführliche Informationen zu Z-Fighting finden Sie im Artikel [Aktivieren der Tiefenpufferfreigabe](./recommended-settings-for-unity.md#enable-depth-buffer-sharing) im Artikel empfohlene Einstellungen [für Unity.](./recommended-settings-for-unity.md)

### <a name="anti-aliasing"></a>Antialiasing

Antialiasing ist eine Technik, die verwendet wird, um verkrümmte Kanten an gekrümmten Linien und Diagonalen in Hologrammen zu glätten.  In diesem Teil der App werden die Auswirkungen des Aliasings für angezeigten Text und Fahrrad-Spokes angezeigt.  

## <a name="3d-asset-fundamentals"></a>Grundlagen zu 3D-Ressourcen

Wählen Sie auf der Startseite der Anwendung **3D Asset Fundamentals (Grundlagen** von 3D-Medienressourcen) aus, um zu erfahren, wie Sie 3D-Objekte optimieren können, um die Anforderungen an die Bildfrequenz zu erfüllen und gleichzeitig eine hohe visuelle Genauigkeit zu erhalten.

Wir untersuchen die folgenden schlüsseln Konzepte:

>[!div class = "checklist"]
> * [Dreiecksanzahl](#triangle-count).
> * [Shader übergibt](#shader-passes).
> * [Zeichnen von Aufrufen](#draw-calls)von .
> * [Final](#finale).

### <a name="triangle-count"></a>Dreiecksanzahl

Wählen Sie die Anzahl und Komplexität von Fahrradmodellen aus, um den visuellen Unterschied basierend auf FPS zu erkennen.

![Wählen Sie verschiedene Optionen für die Anzahl von Dreiecken aus, um die Auswirkungen auf die Bildfrequenz zu sehen.](images\qf-3d-asset-visible-triangles.jpg)

Weitere Informationen finden Sie unter [Erstellungsprozess für Ressourcen.](../../design/asset-creation-process.md)

### <a name="shader-passes"></a>Shader-Durchläufe

Wählen Sie die Anzahl der Fahrräder und verschiedene Shaderoptionen aus, um den visuellen Unterschied basierend auf FPS zu erkennen.

![Wählen Sie verschiedene Shaderoptionen aus, um die Auswirkungen auf die Bildfrequenz zu sehen.](images\qf-3d-asset-shader-complexity.jpg)

Weitere Informationen finden Sie unter [MRTK Standard Shader](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader).

### <a name="draw-calls"></a>Zeichnen von Aufrufen

Zeichnen-Aufrufe sind ressourcenintensive Aufrufe der Grafikkarte.  In diesem Teil der App sehen Sie den visuellen Unterschied aus erster Hand, da sich die Anzahl der Zeichnen-Aufrufe auf FPS auswirken.

![Zeichnen-Aufrufe sollten optimiert werden, um die Leistung zu steigern.](images\qf-3d-asset-draw-calls.jpg)

Siehe [CPU-zu-GPU-Leistungsempfehlungen.](./performance-recommendations-for-unity.md#cpu-to-gpu-performance-recommendations)

### <a name="finale"></a>Final

Hier können wir untersuchen, wie viele vollständig optimierte Fahrräder angezeigt werden können und welche Genauigkeit bei den Optimierungstechniken möglich ist.

![Verwendete Optimierungstechniken.](images\qf-3d-asset-finale.jpg)

## <a name="next-steps"></a>Nächste Schritte

Erkunden Sie andere Mixed Reality-Beispielszenarien:

   > [!div class="nextstepaction"]
   > [Beispiele und Feature-Apps](../features-and-samples.md)