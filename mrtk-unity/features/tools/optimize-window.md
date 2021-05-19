---
title: Optimierungsfenster
description: Fenster "Dokumentationsoptimierung" im MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 7ffc2173cc55c83f126f66002d9240cb349d7f59
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144318"
---
# <a name="optimize-window"></a>Fenster "Optimieren"

Das MRTK-Optimierungsfenster ist ein Hilfsprogramm zum Automatisieren und Informieren beim Konfigurieren eines Mixed Reality-Projekts für optimale [Leistung](../../performance/perf-getting-started.md) in Unity. Dieses Tool konzentriert sich in der Regel auf Renderingkonfigurationen, die bei der richtigen Voreinstellung Millisekunden an Verarbeitung sparen können.

Das *aktive Buildziel* ist die [Buildplattform, auf die](https://docs.unity3d.com/Manual/BuildSettings.html) das Projekt derzeit für die Kompilierung ausgerichtet ist.

Das *Leistungsziel weist* das Optimierungstool an, welche Art von Geräteendpunkten als Ziel verwendet werden soll.

- *AR-Headsets* sind Geräte mit mobiler Klasse, z. B. HoloLens
- *VR Standalone* sind Geräte mit mobiler Klasse, z. B. Oculus Go oder Quest.
- *VR Tethered sind* PC-fähige Geräte, z. B. Samsung Samsung- oder Oculus Rift- oder OCULUS Vive-Geräte.

![MRTK Optimize Window Performance Target](../images/performance/OptimizeWindowPerformanceTarget.jpg)

## <a name="setting-optimizations"></a>Festlegen von Optimierungen

Auf der Registerkarte "Optimierung der Einstellungen" werden einige der wichtigen Renderingkonfigurationen für ein Unity-Projekt behandelt. Dieser Abschnitt hilft Ihnen bei der Automatisierung und informiert Sie darüber, welche Einstellungen geändert werden sollten, um optimale Ergebnisse zu erzielen.

Ein grünes Häkungssymbol bedeutet, dass im Projekt bzw. in der Szene für diese bestimmte Einstellung ein optimaler Wert konfiguriert wurde. Ein gelbes Warnsymbol gibt an, dass die aktuelle Konfiguration verbessert werden kann. Durch Klicken auf die zugeordnete Schaltfläche in einem bestimmten Abschnitt wird diese Einstellung im Unity-Projekt bzw. in der Unity-Szene automatisch auf einen besseren Wert konfiguriert.

![MRTK-Fenstereinstellungen optimieren](../images/performance/OptimizeWindow_Settings.png)

### <a name="single-pass-instanced-rendering"></a>Rendering mit Einzelpassinstanz

[Single Pass Instanced Rendering](https://docs.unity3d.com/Manual/SinglePassInstancing.html) ist der effizienteste Renderingpfad für Mixed Reality-Anwendungen. Diese Konfiguration stellt sicher, dass die Renderpipeline nur einmal für beide Augen ausgeführt wird und dass Zeichnen-Aufrufe über beide Augen hinweg ausgeführt werden.

### <a name="depth-buffer-sharing"></a>Tiefenpufferfreigabe

Zur Verbesserung [der Hologramms-Stabilität](../../performance/hologram-Stabilization.md)können Entwickler den Tiefenpuffer der Anwendung freigeben, der der Plattform Informationen darüber liefert, wo und welche Hologramme in der gerenderten Szene sich stabilisiert.

### <a name="depth-buffer-format"></a>Tiefenpufferformat

Darüber hinaus wird für *AR-Headsets* empfohlen, beim Aktivieren der Tiefenpufferfreigabe im Vergleich zu 24-Bit ein 16-Bit-Tiefenformat zu verwenden. Dies bedeutet eine geringere Genauigkeit, spart aber die Leistung. Wenn [Z-Fighting](https://en.wikipedia.org/wiki/Z-fighting) auftritt, weil es weniger Genauigkeit bei der Berechnung der [](https://docs.unity3d.com/Manual/class-Camera.html) Tiefe für Pixel gibt, wird empfohlen, die entfernte Clipebene näher an die Kamera zu verschieben (z. B. 50 m anstelle von 1.000 m).

> [!NOTE]
> Bei Verwendung *des 16-Bit-Tiefenformats* funktionieren die erforderlichen Effekte des Schablonenpuffers nicht, da Unity in dieser Einstellung keinen Schablonenpuffer erstellt. [](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) Wenn Sie *umgekehrt das 24-Bit-Tiefenformat* auswählen, wird in der Regel ein [8-Bit-Schablonenpuffer](https://docs.unity3d.com/Manual/SL-Stencil.html)erstellt, sofern dies auf der Endpunktgrafikplattform zu finden ist.
>
> Wenn Sie eine [Mask-Komponente](https://docs.unity3d.com/Manual/script-Mask.html) verwenden, die den Schablonenpuffer erfordert, sollten Sie stattdessen [RectMask2D](https://docs.unity3d.com/Manual/script-RectMask2D.html) verwenden. Dies erfordert keinen Schablonenpuffer und kann daher in Verbindung mit einem *16-Bit-Tiefenformat* verwendet werden.

### <a name="real-time-global-illumination"></a>Globale Real-Time-Stadt

[Globale Echtzeit-Beleuchtung](https://docs.unity3d.com/Manual/GIIntro.html) in Unity kann hervorragende Ergebnisse liefern, aber zu einem sehr hohen Preis. Die beleuchtungsintensive Globale Beleuchtung ist in Mixed Reality sehr teuer. Daher wird empfohlen, dieses Feature in der Entwicklung zu deaktivieren.

> [!NOTE]
> Globale Einstellungen für Musik in Unity werden pro Szene und nicht einmal im gesamten Projekt festgelegt.

## <a name="scene-analysis"></a>Szenenanalyse

Die *Registerkarte Szenenanalyse* dient dazu, Entwickler darüber zu informieren, welche Elemente, die sich derzeit in der Szene befindet, wahrscheinlich die größten Auswirkungen auf die Leistung haben.

![MRTK– Optimieren der Szenenanalyse für Fenstereinstellungen](../images/performance/OptimizeWindow_SceneAnalysis.png)

### <a name="lighting-analysis"></a>Beleuchtungsanalyse

In diesem Abschnitt werden die Anzahl der derzeit in der Szene verfügbaren Lichtlichter sowie alle Beleuchtungslichter untersucht, die Schatten deaktivieren sollten. Schattencasting ist ein sehr aufwendiger Vorgang.

### <a name="polygon-count-analysis"></a>Polygonanzahlanalyse

Das Tool stellt auch Statistiken zur Polygonanzahl bereit. Es kann sehr hilfreich sein, schnell zu ermitteln, welche GameObjects in einer bestimmten Szene die höchste Polygonkomplexität aufweisen, um optimierungszielend zu sein.

### <a name="unity-ui-raycast-analysis"></a>Raycastanalyse der Unity-Benutzeroberfläche

Grafik-Raycastvorgänge werden pro Zeiger im MRTK ausgeführt, um zu bestimmen, ob Unity-Benutzeroberflächenelemente im Fokus stehen. Diese Raycasts können sehr teuer sein. Um die Leistung zu verbessern, sollten Benutzeroberflächenelemente, die nicht in den Ergebnissen zurückgegeben werden müssen, als Raycastziele deaktiviert werden. Jedes [Graphic-Element](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/UI.Graphic.html) verfügt über eine [`Graphic.raycastTarget`](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/UI.Graphic-raycastTarget.html) -Eigenschaft. Dieses Tool sucht nach Text-UI-Elementen, für die diese Eigenschaft aktiviert ist und die daher wahrscheinlich deaktiviert werden können.

## <a name="shader-analysis"></a>Shaderanalyse

Der [Unity Standard-Shader](https://docs.unity3d.com/Manual/shader-StandardShader.html) kann sehr hochwertige visuelle Ergebnisse für Spiele erzeugen, eignet sich jedoch im Allgemeinen nicht für die Leistungsanforderungen von Mixed Reality-Anwendungen, insbesondere da solche Anwendungen im Allgemeinen GPU-gebunden sind. Daher wird Entwicklern empfohlen, den [MRTK Standard-Shader](../rendering/mrtk-standard-shader.md) zu verwenden, um Dies & grafischen Features mit der Leistung in Einklang zu bringen.

Die Registerkarte *Shaderanalyse* scannt den Ressourcenordner des aktuellen Projekts nach Materialien, die den Unity Standard-Shader verwenden, oder, falls gewünscht, alle Materialien, die nicht Mixed Reality Toolkit bereitgestellte Shader verwenden. Nach derEntdeckung können Entwickler alle Materialien konvertieren oder einzeln mit den entsprechenden Schaltflächen konvertieren.

![MRTK Optimize Window Settings shader analysis (MRTK Optimize Window Settings Shader-Analyse)](../images/performance/OptimizeWindow_ShaderAnalysis.png)

## <a name="see-also"></a>Siehe auch

- [Leistung](../../performance/perf-getting-started.md)
- [Hologrammstabilisierung](../../performance/hologram-stabilization.md)
