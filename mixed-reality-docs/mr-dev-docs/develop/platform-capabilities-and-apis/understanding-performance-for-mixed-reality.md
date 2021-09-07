---
title: Grundlegendes zur Leistung für Mixed Reality
description: Erfahren Sie mehr über erweiterte Informationen und Details zum Analysieren und Optimieren Windows Mixed Reality App-Leistung.
author: hferrone
ms.author: v-vtieto
ms.date: 08/16/2021
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Leistung, Optimierung, CPU, GPU
ms.openlocfilehash: 9304e4cd80f0929b87a29873ad07329700ec463f
ms.sourcegitcommit: 6f3b3aa31cc3acefba5fa3ac3ba579d9868a4fe4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2021
ms.locfileid: "123244214"
---
# <a name="understanding-performance-for-mixed-reality"></a>Grundlegendes zur Leistung für Mixed Reality

Dieser Artikel enthält eine Einführung in das Verständnis der Bedeutung der Leistung für Ihre Mixed Reality-App.  Die Benutzerfreundlichkeit kann erheblich beeinträchtigt werden, wenn Ihre Anwendung nicht mit optimaler Bildfrequenz ausgeführt wird. Hologramme erscheint instabil, und die Nachverfolgung des Kopfes der Umgebung ist ungenau, was zu einer schlechten Benutzerfreundlichkeit führt. Die Leistung muss als erstklassiges Feature für die Mixed Reality-Entwicklung und nicht als eine ansprechende Aufgabe angesehen werden.

Wir haben vor Kurzem eine Anwendung namens Quality Fundamentals veröffentlicht, die allgemeine Leistungs-, Entwurfs- und Umgebungsprobleme sowie Lösungen für HoloLens 2-Apps behandelt. Diese App ist eine hervorragende visuelle Demo für die folgenden Inhalte.

> [!div class="nextstepaction"]
> [Herunterladen der Quality Fundamentals-App](https://www.microsoft.com/en-us/p/quality-fundamentals/9mwz852q88fw)

Die performanten Frameratenwerte für jede Zielplattform sind unten aufgeführt.

| Plattform | Zielbildrate |
|----------|-------------------|
| [HoloLens](/hololens/hololens1-hardware) | 60 FPS |
| [Windows Mixed Reality Ultra Pcs](../../discover/immersive-headset-hardware-details.md) | 90 FPS |
| [Windows Mixed Reality Pcs](../../discover/immersive-headset-hardware-details.md) | 60 FPS |

Im folgenden Framework werden bewährte Methoden zum Erreichen der Zielframeraten beschrieben. Tipps zum Messen und Verbessern der Framerate in der Unity-Umgebung finden Sie im [Artikel Leistungsempfehlungen für Unity.](../unity/performance-recommendations-for-unity.md) 

## <a name="understanding-performance-bottlenecks"></a>Grundlegendes zu Leistungsengpässen

Wenn Ihre App über eine unterdurchschnittliche Framerate verfügt, besteht der erste Schritt darin, zu analysieren und zu verstehen, wo Ihre Anwendung rechenintensiv ist. Es gibt zwei primäre Prozessoren, die für die Arbeit zum Rendern Ihrer Szene verantwortlich sind: die CPU und die GPU, die jeweils verschiedene Aspekte Ihrer Mixed Reality-App verarbeiten. Die drei wichtigsten Stellen, an denen Engpässe auftreten können, sind: 

1. **App-Thread – CPU** -
    Verantwortlich für Ihre App-Logik, einschließlich der Verarbeitung von Eingaben, Animationen, Physik und anderer App-Logik.
2. **Renderthread – CPU an GPU** – Verantwortlich für die Übermittlung Ihrer Draw-Aufrufe an die GPU. Wenn Ihre App ein Objekt wie einen Cube oder ein Modell rendern möchte, sendet dieser Thread eine Anforderung an die GPU, um die Vorgänge durchzuführen.
3. **GPU:** Am häufigsten wird die Grafikpipeline Ihrer Anwendung verarbeitet, um 3D-Daten (Modelle, Texturen usw.) in Pixel zu transformieren. Es erzeugt letztendlich ein 2D-Image, das an den Bildschirm Ihres Geräts übermittelt werden kann.

![Lebensdauer eines Frames](images/lifetime-of-a-frame.png)

Im Allgemeinen sind HoloLens Anwendungen GPU-gebunden, aber nicht immer. Verwenden Sie die unten angegebenen Tools und Techniken, um zu verstehen, wo Ihre jeweilige App einen Engpass auf sich hat.

## <a name="how-to-analyze-your-application"></a>Analysieren Ihrer Anwendung

Es gibt viele Tools, mit denen Sie das Leistungsprofil und potenzielle Engpässe in Ihrer Mixed Reality-Anwendung verstehen können. 

Im Folgenden finden Sie einige gängige Tools, mit denen Sie umfassende Profilerstellungsinformationen für Ihre Anwendung sammeln können:
- [Intel Graphics Performance Analyzers](https://software.intel.com/gpa)
- [Visual Studio Grafikdebugger](/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics)
- [Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)
- [Unity-Framedebugger](https://docs.unity3d.com/Manual/FrameDebugger.html)
- [Unreal Insights](../unreal/unreal-insights.md)
- [PIX](https://devblogs.microsoft.com/pix/)
- [GPU-Pofileing in Unreal](https://docs.unrealengine.com/en-US/TestingAndOptimization/PerformanceAndProfiling/GPU/index.html)

### <a name="how-to-profile-in-any-environment"></a>Erstellen eines Profils in einer beliebigen Umgebung

Eine Möglichkeit, zu bestimmen, ob Ihre App GPU- oder CPU-gebunden ist, besteht darin, die Auflösung der Renderzielausgabe zu verringern. Indem Sie die Anzahl der zu berechnende Pixel reduzieren, verringern Sie die GPU-Auslastung. Das Gerät wird in einer kleineren Textur gerendert und dann nach oben geworfen, um Ihr endgültiges Bild anzuzeigen.

Nach dem Verringern der Renderingauflösung, wenn:
1) Die Framerate der Anwendung **erhöht sich,** dann sind Sie wahrscheinlich **GPU-gebunden.**
1) Unveränderte Anwendungsrahmenrate, dann sind Sie wahrscheinlich **CPU-gebunden.**

>[!NOTE]
>Unity bietet die Möglichkeit, die Renderzielauflösung Ihrer Anwendung zur Laufzeit über die *[XRSettings.renderViewportScale-Eigenschaft](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* einfach zu ändern. Das endgültige Bild, das auf dem Gerät angezeigt wird, weist eine feste Auflösung auf. Die Plattform erstellt eine Stichprobe der Ausgabe mit niedrigerer Auflösung, um ein Bild mit höherer Auflösung zum Rendern auf Displays zu erstellen. 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a>Verbessern Ihrer Anwendung

### <a name="cpu-performance-recommendations"></a>CPU-Leistungsempfehlungen

Im Allgemeinen umfassen die meisten Arbeiten in einer Mixed Reality-Anwendung auf der CPU die "Simulation" der Szene und die Verarbeitung Ihrer Anwendungslogik. Die folgenden Bereiche sind für die Optimierung vorgesehen:

- Animationen
- Physische Effekte
- Speicherbelegungen
- Komplexe Algorithmen (d.h. Inverse Kinematik, Pfadsuche)

### <a name="gpu-performance-recommendations"></a>GPU-Leistungsempfehlungen

#### <a name="understanding-bandwidth-vs-fill-rate"></a>Grundlegendes zur Bandbreite im Vergleich zur Füllrate
Beim Rendern eines Frames auf der GPU ist eine Anwendung entweder an die Arbeitsspeicherbandbreite oder die Füllrate gebunden.

- **Arbeitsspeicherbandbreite** ist die Rate der Lese- und Schreibvorgänge, die die GPU aus dem Arbeitsspeicher durchführen kann.
    - Reduzieren Sie die Texturqualität, und überprüfen Sie, ob sich die Framerate verbessert hat, um Bandbreiteneinschränkungen zu ermitteln.
    - Ändern Sie **in** Unity texture quality in **Edit**  >  **Project Einstellungen**  >  **[Quality Einstellungen](https://docs.unity3d.com/Manual/class-QualitySettings.html)**.
- **Füllrate** bezieht sich auf die Pixel, die pro Sekunde von der GPU gezeichnet werden können.
    - Um Einschränkungen bei der Füllrate zu ermitteln, verringern Sie die Anzeigeauflösung, und überprüfen Sie, ob sich die Framerate verbessert hat. 
    - Verwenden Sie in Unity die *[XRSettings.renderViewportScale-Eigenschaft.](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)*

Die Arbeitsspeicherbandbreite umfasst im Allgemeinen Optimierungen für Folgendes:
1) Niedrigere Texturauflösungen
2) Weniger Texturen verwenden (Normal, Glanz usw.)

Die Füllrate konzentriert sich auf die Reduzierung der Anzahl von Vorgängen, die für ein endgültiges gerenderte Pixel berechnet werden müssen, einschließlich:
1) Anzahl der zu rendern/zu verarbeitende Objekte
2) Anzahl von Vorgängen pro Shader
3) Anzahl der GPU-Phasen bis zum Endergebnis (Geometrie-Shader, Nachbearbeitungseffekte usw.)
4) Anzahl der zu rendernde Pixel (Anzeigeauflösung)

#### <a name="reduce-polygon-count"></a>Reduzieren der Polygonanzahl

Eine höhere Polygonanzahl führt zu mehr Vorgängen für die GPU, [sodass die Reduzierung der Anzahl von Polygonen](/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets) in Ihrer Szene die Renderzeit reduziert. Es gibt andere Faktoren, die die Schattierung der Geometrie teuer machen, aber die Polygonanzahl ist die einfachste Metrik, um zu bestimmen, wie viel Arbeit zum Rendern einer Szene erforderlich ist.

#### <a name="limit-overdraw"></a>Einschränken des Überzeichnens

Eine hohe Überzeichnung tritt auf, wenn mehrere Objekte gerendert, aber nicht auf dem Bildschirm angezeigt werden, da sie durch ein verdeckendes Objekt ausgeblendet werden. Imagine an einer Wand, die Objekte enthält. Die gesamte Geometrie würde zum Rendern verarbeitet, aber nur die deckende Wand muss gerendert werden, was zu unnötigen Operationen führt.

#### <a name="shaders"></a>Shader

Shader sind kleine Programme, die auf der GPU ausgeführt werden und zwei wichtige Schritte beim Rendern ausführen:
1) Bestimmen, welche Scheitelpunkte gezeichnet werden sollen und wo sie sich im Bildschirmbereich befinden (der Vertex-Shader)
    - Der Vertex-Shader wird pro Scheitelpunkt für jedes Gitter ausgeführt.
2) Bestimmen der Farbe der einzelnen Pixel (Pixelshader)
    - Der Pixelshader wird pro Pixel ausgeführt und von der Geometrie in die Zielrendertextur gerendert.

In der Regel werden von Shadern viele Transformationen und Beleuchtungsberechnungen durchgeführt. Obwohl komplexe Beleuchtungsmodelle, Schatten und andere Vorgänge zu hervorragenden Ergebnissen führen können, haben sie auch einen Preis. Die Reduzierung der Anzahl von Vorgängen, die in Shadern berechnet werden, kann die für die GPU pro Frame erforderliche Arbeit erheblich reduzieren.

##### <a name="shader-coding-recommendations"></a>Shader-Codierungsempfehlungen

- Verwenden Sie nach Möglichkeit die bilineare Filterung.
- Neu anordnen von Ausdrücken zur Verwendung von intrinsischen MAD-Funktionen zum gleichzeitigen Multiplizieren und Hinzufügen
- Berechnen Sie die CPU so weit wie möglich voraus, und übergeben Sie sie als Konstanten an das Material.
- **Verschieben von Vorgängen vom Pixelshader zum Vertex-Shader bevorzugen**
    - Im Allgemeinen ist die Anzahl der Scheitelpunkte viel kleiner als die Anzahl der Pixel (720p ist 921.600 Pixel, 1080p ist 2.073.600 Pixel usw.).

#### <a name="remove-gpu-stages"></a>Entfernen von GPU-Phasen

Nachbearbeitungseffekte können teuer sein und die Füllrate Ihrer Anwendung erhöhen, einschließlich Antialiasingtechniken wie MSAA. Auf HoloLens empfehlen wir, diese Techniken und zusätzliche Shaderstufen wie Geometrie, Hülle und Compute-Shader zu vermeiden.

## <a name="memory-recommendations"></a>Empfehlungen zum Arbeitsspeicher

Übermäßige Speicherbelegungs- und Freigabevorgänge können zu inkonsistenter Leistung, fixierten Frames und anderem schädlichem Verhalten führen. Es ist besonders wichtig, die Überlegungen zum Arbeitsspeicher bei der Entwicklung in Unity zu verstehen, da die Speicherverwaltung vom Garbage Collector gesteuert wird.

#### <a name="object-pooling"></a>Objektpooling

Objektpooling ist eine beliebte Technik, um die Kosten für kontinuierliche Zuordnungen und Freigaben von Objekten zu reduzieren. Dies erfolgt durch Zuordnen eines großen Pools identischer Objekte und Wiederverwendung inaktiver, verfügbarer Instanzen aus diesem Pool, statt im Lauf der Zeit ständig neue Objekte zu erstellen und zu entfernen. Objektpools eignen sich hervorragend für wiederverwendbare Komponenten, die im Rahmen einer App eine variable Lebensdauer haben.

## <a name="see-also"></a>Siehe auch
- [Leistungsempfehlungen für Unity](../unity/performance-recommendations-for-unity.md)
- [Empfohlene Einstellungen für Unity](../unity/recommended-settings-for-unity.md)
- [Leistungsempfehlungen für Unreal](../unreal/performance-recommendations-for-unreal.md)
- [Materialempfehlungen in Unreal](../unreal/unreal-materials.md)
- [Optimieren von 3D-Modellen](/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets)
- [Bewährte Methoden zum Konvertieren und Optimieren von 3D-Echtzeitmodellen](/dynamics365/mixed-reality/import-tool/best-practices)
- [Leistungsrichtlinien für Interpreten und Designer für Unreal](https://docs.unrealengine.com/en-US/TestingAndOptimization/PerformanceAndProfiling/Guidelines/index.html)
- [Bewährte Methoden für VR für Unreal](https://docs.unrealengine.com/en-US/SharingAndReleasing/XRDevelopment/VR/DevelopVR/ContentSetup/index.html)