---
title: Qualitätsgrundlagen
description: Erfahren Sie mehr über die Qualitätsgrundlagen beim Entwerfen von Mixed Reality-Anwendungen.
author: qianw211
ms.author: v-qianwen
ms.date: 07/15/2021
ms.topic: article
keywords: Qualitätsgrundlagen, Fallstudie, Projekt, Beispiel, MRTK, Mixed Reality Toolkit, Unity, Beispiel-Apps, Beispiel-Apps, Open Source, Microsoft Store, HoloLens, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: e91ea1c69aeafaafa9c9bae30af6e5a288754764
ms.sourcegitcommit: cf8df1720ddb8236207ab581bc149edcc76e6199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/26/2021
ms.locfileid: "114702919"
---
# <a name="quality-fundamentals"></a>Qualitätsgrundlagen

Quality Fundamentals ist eine HoloLens 2-App, die die Grundlagen der Erstellung einer hervorragenden Mixed Reality-Erfahrung veranschaulicht.  Anstatt nur mit Qualitätsproblemen in Mixed Reality zu lernen und zu lesen, können wir nun allgemeine Umgebungs-, Entwurfs- und Leistungsprobleme und Lösungen aus erster Hand erleben, indem wir die in der App bereitgestellten Optionen auswählen.

Um die App herunterzuladen und zu installieren, wechseln Sie zur Downloadseite der App:

> [!div class="nextstepaction"]
> [Qualitätsgrundlagen](https://www.microsoft.com/p/quality-fundamentals/9mwz852q88fw?activetab=pivot:overviewtab)

![Startseite der Qualitätsgrundlagen](images\qf-homepage.jpg)

In dieser Beispiel-App erfahren Sie mehr über:

>[!div class = "checklist"]
> * [Geräte-E/A und -Umgebung:](#device-io-and-environment)Wie sich die Umgebungsfaktoren auf die Leistung HoloLens auswirken können.
> * [Spatial Anchors:](#anchor-fundamentals)Ausrichten von Hologrammen an einem physischen Raum mithilfe von Raumankern.
> * [Holografische Stabilität und Genauigkeit:](#stability-and-fidelity)Erkunden Sie Techniken, um die Stabilität und Genauigkeit von Hologramme zu verbessern.
> * Grundlagen zu [3D-Medienobjekten:](#3d-asset-fundamentals)Optimieren von 3D-Ressourcen, um eine hohe visuelle Genauigkeit zu gewährleisten. 

## <a name="device-io-and-environment"></a>Geräte-E/A und -Umgebung

Starten Sie die Quality Fundamentals-App auf HoloLens. Sobald die Startseite der App angezeigt wird, wählen Sie **Geräte-E/A und Umgebung** aus.  Wir untersuchen, wie sich die HoloLens Sensoren und die Umgebung auf die räumliche Zuordnung, Nachverfolgung und Platzierung von Hologrammen auswirken. 

### <a name="surfaces"></a>Oberflächen

Spiegel oder Oberflächen mit gespiegelten Oberflächen können die HoloLens Sensoren hinsichtlich der Form des Objekts verwechseln.  Objekte, die auf der Oberfläche reflektiert werden, können vom Gerät als sich ändernde Umgebung interpretiert werden, was dazu führen kann, dass das Gerät die Nachverfolgung verliert.  Wenn gespiegelte Oberflächen Herausforderungen für HoloLens verursachen, erwägen Sie das Hinzufügen eines Bildschirms oder verleumderter Blinde.

Weitere Informationen finden Sie unter [Oberflächen in einem Raum](/hololens/hololens-environment-considerations#surfaces-in-a-space) in HoloLens [Umgebungsüberlegungen.](/hololens/hololens-environment-considerations)

### <a name="lighting"></a>Beleuchtung

HoloLens Leistung kann durch sehr niedrige oder sehr helle Lichtbedingungen beeinträchtigt werden.  Die Nachverfolgungssensoren auf dem HoloLens benötigen etwa 500-1000 Lux Licht, um optimal zu funktionieren. Sie können ein Luxmeter oder eine mobile App verwenden, um die Lichtmenge in Ihrem Raum zu messen.

Weitere Informationen finden Sie unter [Überlegungen zur Beleuchtung](/hololens/hololens-environment-considerations?branch=pr-en-us-3071#lighting) in [HoloLens Umgebung.](/hololens/hololens-environment-considerations)

## <a name="anchor-fundamentals"></a>Grundlagen des Ankers

Um zu erfahren, wie Sie Spatial Anchors verwenden, um Hologramme an einem physischen Raum auszurichten, wählen Sie **anchor Fundametals** auf der Startseite der App aus.

In diesem Teil der App untersuchen wir die folgenden Benutzerszenarien:

>[!div class = "checklist"]
> * Was geschieht, wenn kein Anker auf ein Objekt angewendet wird.
> * Wenn mehrere Spatial Anchors für eine Gruppe von -Objekten verwendet werden.
> * Freigeben eines Raumankers zwischen mehreren Projektmitarbeitern mithilfe eines QR-Codes.
> * Ankerplatzierung für sehr große Objekte in einem Raum.

Weitere Informationen finden Sie unter [Spatial Anchors](/windows/mixed-reality/design/spatial-anchors) in der [Mixed Reality-Dokumentation.](/windows/mixed-reality/design/spatial-anchors)

## <a name="stability-and-fidelity"></a>Stabilität und Genauigkeit

Wählen Sie auf der Startseite der Anwendung **Stabilität und Genauigkeit** aus, um zu erfahren, wie Sie die Hologrammstabilität verbessern können.

Wir untersuchen die folgenden Schlüsselkonzepte:

>[!div class = "checklist"]
> * [Bildfrequenz](#frame-rate).
> * [Late Stage Reprojection (LSR)](#late-stage-reprojection-lsr).
> * [Z-Fighting](#z-fighting).
> * [Antialiasing](#anti-aliasing).

### <a name="frame-rate"></a>Bildfrequenz

Um die bestmögliche Hologrammerfahrung zu bieten, müssen Anwendungsentwickler 60 Frames pro Sekunde (FPS) beibehalten.  Wechseln Sie in diesem Teil der App zwischen verschiedenen Optionen für die Dreiecksanzahl, um den Unterschied mit verschiedenen Frameraten zu erleben.

![Optimierung der Dreiecksanzahl](images\qf-triangle-count-optimization.png)

Weitere Informationen finden Sie im Artikel [zur Hologrammstabilität](/windows/mixed-reality/develop/platform-capabilities-and-apis/hologram-stability) unter [Framerate.](/windows/mixed-reality/develop/platform-capabilities-and-apis/hologram-stability#frame-rate)

### <a name="late-stage-reprojection-lsr"></a>Late Stage Reprojection (LSR)

Die Neuprojektion wird verwendet, um Hologramme zu stabilen, wenn sich Benutzer in ihrem Raum bewegen.  Probieren Sie die verschiedenen Projektionsoptionen aus, die von diesem Teil der App bereitgestellt werden, um den Unterschied in der Hologrammqualität zu sehen.

![Testen Sie die verschiedenen Optionen für die Neuprojektion, um den Unterschied zu erleben.](images\qf-lsr-modes.jpg)

Ausführliche Informationen finden Sie im Artikel [Zur Neuprojektion](/windows/mixed-reality/develop/platform-capabilities-and-apis/hologram-stability#reprojection) im Artikel [Zur Hologrammstabilität.](/windows/mixed-reality/develop/platform-capabilities-and-apis/hologram-stability)

### <a name="z-fighting"></a>Z-Fighting

Z-Fighting tritt auf, wenn die Mixed Reality-Anwendung nicht erkennen kann, welches Objekt sich vor dem anderen befindet.  Sie werden das Flackern der holografischen Objekte bemerken, da sie für denselben Z-Tiefenwert blättern.  Erleben Sie die Auswirkungen von Z-Fighting in der App, indem Sie die Platzierung eines holografischen Objekts ändern, in diesem Fall das Logo auf einem Fahrrad.

![Erleben Sie Z-Fighting mit Objektplatzierungen.](images\qf-z-fighting.jpg)

Ausführliche Informationen zum Z-Fighting finden Sie im Artikel Empfohlene [Einstellungen für Unity](/windows/mixed-reality/develop/unity/recommended-settings-for-unity) unter Aktivieren der [Tiefenpufferfreigabe.](/windows/mixed-reality/develop/unity/recommended-settings-for-unity#enable-depth-buffer-sharing)

### <a name="anti-aliasing"></a>Antialiasing

Antialiasing ist eine Technik, die verwendet wird, um verzweigte Kanten auf gekrümmten Linien und Diagonalen in Hologrammen zu glätten.  In diesem Teil der App können Sie die Auswirkungen des Aliasings auf angezeigten Text und Fahrradspeichen erleben.  

## <a name="3d-asset-fundamentals"></a>Grundlagen zu 3D-Medienobjekten

Wählen Sie auf der Startseite der Anwendung **3D Asset Fundamentals (Grundlagen zu 3D-Medienobjekten)** aus, um zu erfahren, wie Sie 3D-Ressourcen optimieren können, um die Anforderungen an die Bildfrequenz zu erfüllen und gleichzeitig eine hohe visuelle Genauigkeit zu gewährleisten.

Wir untersuchen die folgenden Schlüsselkonzepte:

>[!div class = "checklist"]
> * [Dreiecksanzahl](#triangle-count).
> * [Shader übergibt](#shader-passes).
> * [Draw ruft auf.](#draw-calls)
> * [Final](#finale).

### <a name="triangle-count"></a>Dreiecksanzahl

Wählen Sie die Anzahl und Komplexität von Fahrradmodellen aus, um den visuellen Unterschied basierend auf FPS zu erleben.

![Wählen Sie verschiedene Optionen für die Dreiecksanzahl aus, um die Auswirkungen auf die Bildfrequenz anzuzeigen.](images\qf-3d-asset-visible-triangles.jpg)

Weitere Informationen finden Sie unter [Medienobjekterstellungsprozess.](/windows/mixed-reality/design/asset-creation-process)

### <a name="shader-passes"></a>Shaderdurchläufe

Wählen Sie die Anzahl der Fahrräder und verschiedene Shaderoptionen aus, um den visuellen Unterschied basierend auf FPS zu erleben.

![Wählen Sie verschiedene Shaderoptionen aus, um die Auswirkungen auf die Bildfrequenz anzuzeigen.](images\qf-3d-asset-shader-complexity.jpg)

Weitere Informationen finden Sie unter [MRTK Standard Shader](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader).

### <a name="draw-calls"></a>Zeichnen von Aufrufen

Draw-Aufrufe sind ressourcenintensive Aufrufe der Grafikkarte.  In diesem Teil der App können Sie den visuellen Unterschied aus erster Hand erleben, da sich die Anzahl der Zeichnen-Aufrufe auf FPS auswirkt.

![Zeichnen-Aufrufe sollten optimiert werden, um die Leistung zu steigern.](images\qf-3d-asset-draw-calls.jpg)

Weitere Informationen finden Sie [unter Empfehlungen zur CPU-zu-GPU-Leistung.](/windows/mixed-reality/develop/unity/performance-recommendations-for-unity#cpu-to-gpu-performance-recommendations)

### <a name="finale"></a>Finale

Hier können wir untersuchen, wie viele vollständig optimierte Fahrräder angezeigt werden können, und wie genau die Optimierungstechniken möglich sind.

![Verwendete Optimierungstechniken.](images\qf-3d-asset-finale.jpg)

## <a name="next-steps"></a>Nächste Schritte

Erkunden Sie andere Mixed Reality-Beispielszenarien:

   > [!div class="nextstepaction"]
   > [Beispiele und Feature-Apps](../features-and-samples.md)