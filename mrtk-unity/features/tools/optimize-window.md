---
title: Optimierungsfenster
description: Fenster "Dokumentationsoptimierung" in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 8b8928e9c723ffa9fd08d22866b8ee5748e38ace
ms.sourcegitcommit: 78746bef0e1ffe1480e89fed8cd30f6f8b389e8d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2021
ms.locfileid: "114713582"
---
# <a name="optimize-window"></a>Optimierungsfenster

Das MRTK-Optimierungsfenster ist ein Hilfsprogramm zum Automatisieren und Informieren bei der Konfiguration eines Mixed Reality-Projekts, um eine optimale [Leistung](../../performance/perf-getting-started.md) in Unity zu erzielen. Dieses Tool konzentriert sich im Allgemeinen auf Renderingkonfigurationen, die bei Festlegung auf die richtige Voreinstellung Millisekunden an Verarbeitung sparen können.

> [!NOTE]
> Das **Fenster "Optimieren"** kann geöffnet werden, indem Sie im Unity-Editor über das Menü der oberen Leiste zu **Mixed Reality** Fenster  >  **"Hilfsprogramme**  >  **optimieren"** navigieren.

Das *aktive Buildziel* ist die [Buildplattform,](https://docs.unity3d.com/Manual/BuildSettings.html) auf die derzeit das Projekt für die Kompilierung abzielt.

Das *Leistungsziel* weist das Optimierungstool an, welche Art von Geräteendpunkten als Ziel verwendet werden soll.

- *AR-Headsets* sind Geräte der mobilen Klasse, z. B. HoloLens
- *VR Standalone* sind Geräte der Mobilen Klasse, z. B. Oculus Go oder Quest.
- *VR Tethered* sind PC-gestützte Geräte, z. B. Samsung Odyssey, Oculus Rift oder LG Vive usw.

![MRTK Optimize Window Performance Target](../images/performance/OptimizeWindowPerformanceTarget.jpg)

## <a name="setting-optimizations"></a>Festlegen von Optimierungen

Auf der Registerkarte "Optimierung der Einstellungen" werden einige der wichtigen Renderingkonfigurationen für ein Unity-Projekt behandelt. Dieser Abschnitt kann Sie bei der Automatisierung unterstützen und Sie darüber informieren, welche Einstellungen für die leistungsfähigsten Ergebnisse geändert werden sollten.

Ein grünes Häkchen bedeutet, dass ein optimaler Wert im Projekt/in der Szene für diese bestimmte Einstellung konfiguriert wurde. Ein gelbes Warnsymbol gibt an, dass die aktuelle Konfiguration verbessert werden kann. Wenn Sie in einem bestimmten Abschnitt auf die zugeordnete Schaltfläche klicken, wird diese Einstellung im Unity-Projekt bzw. in der Unity-Szene automatisch auf einen optimaleren Wert konfiguriert.

![MRTK Optimize Window Einstellungen](../images/performance/OptimizeWindow_Settings.png)

### <a name="single-pass-instanced-rendering"></a>Rendering mit Einzeldurchlaufinstanz

[Single-Pass-Instanzrendering](https://docs.unity3d.com/Manual/SinglePassInstancing.html) ist der effizienteste Renderingpfad für Mixed Reality-Anwendungen. Durch diese Konfiguration wird sichergestellt, dass die Renderpipeline nur einmal für beide Augen ausgeführt wird und dass Zeichnen-Aufrufe über beide Augen hinweg instanziert werden.

### <a name="depth-buffer-sharing"></a>Gemeinsame Nutzung von Tiefenpuffern

Um die [Hologrammstabilität](../../performance/hologram-Stabilization.md)zu verbessern, können Entwickler den Tiefenpuffer der Anwendung freigeben, der der Plattform Informationen darüber liefert, wo und welche Hologramme in der gerenderten Szene stabil werden sollen.

### <a name="depth-buffer-format"></a>Tiefenpufferformat

Darüber hinaus wird für *AR-Headsets* empfohlen, ein 16-Bit-Tiefenformat zu verwenden, wenn Die Tiefenpufferfreigabe im Vergleich zu 24-Bit aktiviert wird. Dies bedeutet eine geringere Genauigkeit, spart aber die Leistung. Wenn [Z-Fighting](https://en.wikipedia.org/wiki/Z-fighting) auftritt, weil die Genauigkeit bei der Berechnung der Tiefe für Pixel geringer ist, empfiehlt es sich, die [weit entfernte Clipebene](https://docs.unity3d.com/Manual/class-Camera.html) näher an die Kamera zu verschieben (z.B. 50m anstelle von 1000m).

> [!NOTE]
> Bei Verwendung des *16-Bit-Tiefenformats* funktionieren die erforderlichen Auswirkungen des Schablonenpuffers nicht, da Unity in dieser Einstellung [keinen Schablonenpuffer erstellt.](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) Wenn Sie umgekehrt das *24-Bit-Tiefenformat* auswählen, wird in der Regel ein [8-Bit-Schablonenpuffer](https://docs.unity3d.com/Manual/SL-Stencil.html)erstellt, falls zutreffend auf der Endpunktgrafikplattform.
>
> Wenn Sie eine [Mask-Komponente](https://docs.unity3d.com/Manual/script-Mask.html) verwenden, die den Schablonenpuffer erfordert, erwägen Sie stattdessen die Verwendung von [RectMask2D,](https://docs.unity3d.com/Manual/script-RectMask2D.html) die den Schablonenpuffer nicht benötigt und daher in Verbindung mit einem *16-Bit-Tiefenformat* verwendet werden kann.

### <a name="real-time-global-illumination"></a>Globale Echtzeiteinordnung

[Globale Echtzeitlichter](https://docs.unity3d.com/Manual/GIIntro.html) in Unity können ansprechende, aber sehr hohe Kosten liefern. Globale Beleuchtung ist in Mixed Reality sehr teuer und daher wird empfohlen, dieses Feature in der Entwicklung zu deaktivieren.

> [!NOTE]
> Globale Einstellungen in Unity werden pro Szene und nicht einmal im gesamten Projekt festgelegt.

## <a name="scene-analysis"></a>Szenenanalyse

Die Registerkarte *Szenenanalyse* soll Entwickler darüber informieren, welche Elemente derzeit in der Szene wahrscheinlich die meisten Auswirkungen auf die Leistung haben werden.

![MRTK Optimize Window Einstellungen scene Analysis](../images/performance/OptimizeWindow_SceneAnalysis.png)

### <a name="lighting-analysis"></a>Beleuchtungsanalyse

In diesem Abschnitt werden die Anzahl der derzeit in der Szene enthaltenen Beleuchtung sowie alle Beleuchtungen untersucht, die Schatten deaktivieren sollten. Schattencasting ist ein sehr aufwendiger Vorgang.

### <a name="polygon-count-analysis"></a>Polygonanzahlanalyse

Das Tool stellt auch Statistiken zur Polygonanzahl bereit. Es kann sehr hilfreich sein, schnell zu ermitteln, welche GameObjects in einer bestimmten Szene die höchste Polygonkomplexität aufweisen, um optimierungszielend zu sein.

### <a name="unity-ui-raycast-analysis"></a>Raycastanalyse der Unity-Benutzeroberfläche

Grafik-Raycastvorgänge werden pro Zeiger im MRTK ausgeführt, um zu bestimmen, ob Unity-Benutzeroberflächenelemente im Fokus stehen. Diese Raycasts können sehr teuer sein. Um die Leistung zu verbessern, sollten Benutzeroberflächenelemente, die nicht in den Ergebnissen zurückgegeben werden müssen, als Raycastziele deaktiviert werden. Jedes [Graphic-Element](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/UI.Graphic.html) verfügt über eine [`Graphic.raycastTarget`](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/UI.Graphic-raycastTarget.html) -Eigenschaft. Dieses Tool sucht nach Text-UI-Elementen, für die diese Eigenschaft aktiviert ist und die daher wahrscheinlich deaktiviert werden können.

## <a name="shader-analysis"></a>Shaderanalyse

Der [Unity Standard-Shader](https://docs.unity3d.com/Manual/shader-StandardShader.html) kann sehr hochwertige visuelle Ergebnisse für Spiele erzeugen, eignet sich jedoch im Allgemeinen nicht für die Leistungsanforderungen von Mixed Reality-Anwendungen, insbesondere da solche Anwendungen im Allgemeinen GPU-gebunden sind. Daher wird Entwicklern empfohlen, den [MRTK Standard-Shader](../rendering/mrtk-standard-shader.md) zu verwenden, um Dies & grafischen Features mit der Leistung in Einklang zu bringen.

Auf der Registerkarte *Shaderanalyse* wird der Ressourcenordner des aktuellen Projekts mithilfe des Unity Standard-Shaders auf Materialien überprüft, oder bei Bedarf werden alle Materialien überprüft, die nicht Mixed Reality Toolkit bereitgestellte Shader verwenden. Nach derEntdeckung können Entwickler alle Materialien konvertieren oder einzeln mit den entsprechenden Schaltflächen konvertieren.

![MRTK Optimize Window Einstellungen Shader-Analyse](../images/performance/OptimizeWindow_ShaderAnalysis.png)

## <a name="see-also"></a>Siehe auch

- [Leistung](../../performance/perf-getting-started.md)
- [Hologramm-Stabilisierung](../../performance/hologram-stabilization.md)
