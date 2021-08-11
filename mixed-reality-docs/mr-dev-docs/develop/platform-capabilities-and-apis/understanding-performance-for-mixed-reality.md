---
title: Grundlegendes zur Leistung Mixed Reality
description: Erfahren Sie mehr über erweiterte Informationen und Details zum Analysieren und Optimieren Windows Mixed Reality App-Leistung.
author: hferrone
ms.author: v-hferrone
ms.date: 3/26/2019
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Leistung, Optimierung, CPU, GPU
ms.openlocfilehash: 394198011c40f0b90e2c5579f7e0ad8c4019b2a8cefcb1859c544afcbce47df6
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193558"
---
# <a name="understanding-performance-for-mixed-reality"></a>Grundlegendes zur Leistung für Mixed Reality

Dieser Artikel ist eine Einführung in das Verständnis der Bedeutung der Leistung für Ihre Mixed Reality App.  Die Benutzerfreundlichkeit kann stark beeinträchtigt werden, wenn Ihre Anwendung nicht mit optimaler Bildfrequenz ausgeführt wird. Hologramme wird instabil erscheinen, und die Nachverfolgung der Umgebung mit dem Kopf ist ungenau, was zu einer schlechten Benutzerfreundlichkeit führt. Leistung muss als erstklassiges Feature für die Mixed Reality-Entwicklung und nicht als eine gute Aufgabe betrachtet werden.

Wir haben vor Kurzem eine Anwendung namens Quality Fundamentals veröffentlicht, die allgemeine Leistungs-, Entwurfs- und Umgebungsprobleme und Lösungen für HoloLens 2 behandelt. Diese App ist eine hervorragende visuelle Demo für die folgenden Inhalte.

> [!div class="nextstepaction"]
> [Herunterladen der Quality Fundamentals-App](https://www.microsoft.com/en-us/p/quality-fundamentals/9mwz852q88fw)

Die performanten Frameratewerte für jede Zielplattform sind unten aufgeführt.

| Plattform | Zielframerate |
|----------|-------------------|
| [HoloLens](/hololens/hololens1-hardware) | 60 FPS |
| [Windows Mixed Reality Ultra Pcs](../../discover/immersive-headset-hardware-details.md) | 90 FPS |
| [Windows Mixed Reality Pcs](../../discover/immersive-headset-hardware-details.md) | 60 FPS |

Im folgenden Framework werden bewährte Methoden für das Erreichen von Zielframeraten beschrieben. Es wird empfohlen, den Artikel [Leistungsempfehlungen für Unity](../unity/performance-recommendations-for-unity.md) zu lesen, um Tipps zum Messen und Verbessern der Framerate in der Unity-Umgebung zu erhalten.

## <a name="understanding-performance-bottlenecks"></a>Grundlegendes zu Leistungsengpässen

Wenn Ihre App über eine unterdurchschnittliche Framerate verfügt, besteht der erste Schritt im Analysieren und Verstehen, wo Ihre Anwendung rechenintensiv ist. Es gibt zwei primäre Prozessoren, die für die Arbeit zum Rendern Ihrer Szene verantwortlich sind: die CPU und die GPU, die jeweils unterschiedliche Aspekte Ihrer Mixed Reality behandeln. Die drei wichtigsten Stellen, an denen Engpässe auftreten können, sind: 

1. **App-Thread – CPU** -
    Verantwortlich für Ihre App-Logik, einschließlich der Verarbeitung von Eingaben, Animationen, Physik und anderer App-Logik.
2. **Renderthread – CPU zu GPU** – Verantwortlich für die Übermittlung Ihrer Zeichnen-Aufrufe an die GPU. Wenn Ihre App ein Objekt wie einen Cube oder ein Modell rendern möchte, sendet dieser Thread eine Anforderung an die GPU, um die Vorgänge durchzuführen.
3. **GPU:** Verarbeitet in der Regel die Grafikpipeline Ihrer Anwendung, um 3D-Daten (Modelle, Texturen und so weiter) in Pixel zu transformieren. Es erzeugt letztendlich ein 2D-Bild, das an den Bildschirm Ihres Geräts übermittelt werden kann.

![Lebensdauer eines Frames](images/lifetime-of-a-frame.png)

Im Allgemeinen HoloLens Anwendungen GPU-gebunden, aber nicht immer. Verwenden Sie die unten angegebenen Tools und Techniken, um zu verstehen, wo Ihre bestimmte App Engpässe auft.

## <a name="how-to-analyze-your-application"></a>Analysieren Ihrer Anwendung

Es gibt viele Tools, mit denen Sie das Leistungsprofil und potenzielle Engpässe in Ihrer Mixed Reality-Anwendung verstehen können. 

Im Folgenden finden Sie einige gängige Tools, mit deren Hilfe Sie tiefe Profilerstellungsinformationen für Ihre Anwendung sammeln können:
- [Intel Graphics Performance Analyzers](https://software.intel.com/gpa)
- [Visual Studio Grafikdebugger](/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics)
- [Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)
- [Unity-Framedebugger](https://docs.unity3d.com/Manual/FrameDebugger.html)
- [Unreal Insights](../unreal/unreal-insights.md)
- [Pix](https://devblogs.microsoft.com/pix/)
- [GPU-Pofiling in Unreal](https://docs.unrealengine.com/en-US/TestingAndOptimization/PerformanceAndProfiling/GPU/index.html)

### <a name="how-to-profile-in-any-environment"></a>Erstellen eines Profils in einer beliebigen Umgebung

Eine Möglichkeit, um zu bestimmen, ob Ihre App GPU- oder CPU-gebunden ist, besteht im Senken der Auflösung der Renderzielausgabe. Indem Sie die Anzahl der zu berechnenden Pixel reduzieren, verringern Sie die GPU-Last. Das Gerät wird in einer kleineren Textur gerendert und dann in der Stichprobe angezeigt, um ihr endgültiges Bild anzuzeigen.

Nach dem Senken der Renderingauflösung, wenn:
1) Die Anwendungsframerate **erhöht** sich, dann sind Sie wahrscheinlich **GPU-gebunden.**
1) Anwendungsframerate **unverändert,** dann sind Sie wahrscheinlich **CPU-gebunden**

>[!NOTE]
>Unity bietet die Möglichkeit, die Renderzielauflösung Ihrer Anwendung zur Laufzeit über die *[XRSettings.renderViewportScale-Eigenschaft einfach zu](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* ändern. Das endgültige Bild, das auf dem Gerät angezeigt wird, hat eine feste Auflösung. Die Plattform verwendet Stichproben für die Ausgabe mit niedrigerer Auflösung, um ein Bild mit höherer Auflösung zum Rendern auf Displays zu erstellen. 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a>Verbessern Ihrer Anwendung

### <a name="cpu-performance-recommendations"></a>CPU-Leistungsempfehlungen

Im Allgemeinen umfasst die meiste Arbeit in einer Mixed Reality-Anwendung auf der CPU die "Simulation" der Szene und die Verarbeitung Ihrer Anwendungslogik. Die folgenden Bereiche sind für die Optimierung ausgerichtet:

- Animationen
- Physische Effekte
- Speicherzuweisungen
- Komplexe Algorithmen (d. h. Inverse Kinematik, Pfadsuche)

### <a name="gpu-performance-recommendations"></a>GPU-Leistungsempfehlungen

#### <a name="understanding-bandwidth-vs-fill-rate"></a>Grundlegendes zur Bandbreite im Vergleich zur Füllrate
Beim Rendern eines Frames auf der GPU wird eine Anwendung entweder durch die Arbeitsspeicherbandbreite oder die Füllrate gebunden.

- **Arbeitsspeicherbandbreite** ist die Rate von Lese- und Schreibvorgängen, die die GPU aus dem Arbeitsspeicher ausführen kann.
    - Um Bandbreiteneinschränkungen zu identifizieren, verringern Sie die Texturqualität, und überprüfen Sie, ob sich die Framerate verbessert hat.
    - Ändern Sie in Unity **texturqualität** in **Bearbeiten Project Einstellungen**  >    >  **[Quality Einstellungen](https://docs.unity3d.com/Manual/class-QualitySettings.html)**.
- **Die Füllrate** bezieht sich auf die Pixel, die von der GPU pro Sekunde gezeichnet werden können.
    - Um Füllrateneinschränkungen zu identifizieren, senken Sie die Anzeigeauflösung, und überprüfen Sie, ob die Framerate verbessert wurde. 
    - Verwenden Sie in Unity die *[XRSettings.renderViewportScale-Eigenschaft.](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)*

Die Arbeitsspeicherbandbreite umfasst in der Regel Optimierungen für:
1) Niedrigere Texturauflösungen
2) Verwenden Sie weniger Texturen (Normal, Specular und so weiter).

Die Füllrate konzentriert sich auf die Reduzierung der Anzahl von Vorgängen, die für ein endgültiges gerenderte Pixel berechnet werden müssen, einschließlich:
1) Anzahl der zu rendernden/zu verarbeitenden Objekte
2) Anzahl von Vorgängen pro Shader
3) Anzahl der GPU-Phasen bis zum Endergebnis (Geometrie-Shader, Nachbearbeitungseffekte und so weiter)
4) Anzahl der zu rendernden Pixel (Anzeigeauflösung)

#### <a name="reduce-polygon-count"></a>Reduzieren der Polygonanzahl

Eine höhere Polygonanzahl führt zu mehr Vorgängen für die GPU, sodass die Reduzierung der Anzahl von [Polygonen](/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets) in Ihrer Szene die Renderzeit reduziert. Es gibt andere Faktoren, die die Schattierung der Geometrie teuer machen, aber die Polygonanzahl ist die einfachste Metrik, um zu bestimmen, wie viel Arbeit zum Rendern einer Szene in Frage kommt.

#### <a name="limit-overdraw"></a>Einschränken des Überzeichnens

Eine hohe Überzeichnung tritt auf, wenn mehrere Objekte gerendert, aber nicht auf dem Bildschirm angezeigt werden, da sie durch ein umschließendes Objekt ausgeblendet werden. Imagine an einer Wand, die Objekte hinter sich hat. Die gesamte Geometrie würde für das Rendering verarbeitet, aber nur die nicht transparente Wand muss gerendert werden, was zu unnötigen Vorgängen führt.

#### <a name="shaders"></a>Shader

Shader sind kleine Programme, die auf der GPU ausgeführt werden und zwei wichtige Schritte beim Rendern ausführen:
1) Bestimmen, welche Scheitelpunkte gezeichnet werden sollen und wo sie sich im Bildschirmbereich befinden (Vertex-Shader)
    - Der Vertex-Shader wird pro Scheitelpunkt für jedes Gitternetz ausgeführt.
2) Bestimmen der Farbe jedes Pixels (der Pixels shader)
    - Der Pixels shader wird pro Pixel ausgeführt und von der Geometrie in der Zielrendertextur gerendert.

In der Regel nehmen Shader viele Transformationen und Beleuchtungsberechnungen vor. Obwohl komplexe Beleuchtungsmodelle, Schatten und andere Vorgänge ergebnisse erzeugen können, haben sie auch einen Preis. Das Reduzieren der Anzahl von Vorgängen, die in Shadern berechnet werden, kann die für die GPU pro Frame benötigte Arbeit deutlich reduzieren.

##### <a name="shader-coding-recommendations"></a>Shadercodierungsempfehlungen

- Verwenden Sie nach Möglichkeit die bilineare Filterung.
- Neuanordnung von Ausdrücken zur Verwendung von systeminternen SYSTEM-Intrinsiken zum Gleichzeitigen Multiplizieren und Hinzufügen
- So viel wie möglich auf der CPU vorausberechnen und als Konstanten an das Material übergeben
- **Verschieben von Vorgängen vom Pixel-Shader zum Vertex-Shader bevorzugen**
    - Im Allgemeinen ist die Anzahl der Scheitelpunkte viel kleiner als die Anzahl der Pixel (720p ist 921.600 Pixel, 1080p ist 2.073.600 Pixel und so weiter).

#### <a name="remove-gpu-stages"></a>Entfernen von GPU-Phasen

Nachbearbeitungseffekte können teuer sein und die Füllrate Ihrer Anwendung erhöhen, einschließlich Antialiasingtechniken wie MSAA. Auf HoloLens empfohlen, diese Techniken und zusätzliche Shaderstufen wie Geometrie, Hülle und Compute-Shader zu vermeiden.

## <a name="memory-recommendations"></a>Empfehlungen zum Arbeitsspeicher

Übermäßige Speicherzuordnungs- und Freigabevorgänge können zu inkonsistenter Leistung, fixierten Frames und anderem schädlichem Verhalten führen. Es ist besonders wichtig, die Überlegungen zum Arbeitsspeicher bei der Entwicklung in Unity zu verstehen, da die Speicherverwaltung vom Garbage Collector gesteuert wird.

#### <a name="object-pooling"></a>Objektpooling

Objektpooling ist ein gängiges Verfahren, um die Kosten für fortlaufende Zuordnungen und Freigaben von Objekten zu reduzieren. Dies erfolgt durch Zuordnen eines großen Pools identischer Objekte und Wiederverwendung inaktiver, verfügbarer Instanzen aus diesem Pool, statt im Lauf der Zeit ständig neue Objekte zu erstellen und zu entfernen. Objektpools eignen sich hervorragend für wiederverwendbare Komponenten, die im Rahmen einer App eine variable Lebensdauer haben.

## <a name="see-also"></a>Siehe auch
- [Leistungsempfehlungen für Unity](../unity/performance-recommendations-for-unity.md)
- [Empfohlene Einstellungen für Unity](../unity/recommended-settings-for-unity.md)
- [Leistungsempfehlungen für Unreal](../unreal/performance-recommendations-for-unreal.md)
- [Materialempfehlungen in Unreal](../unreal/unreal-materials.md)
- [Optimieren von 3D-Modellen](/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets)
- [Bewährte Methoden zum Konvertieren und Optimieren von 3D-Echtzeitmodellen](/dynamics365/mixed-reality/import-tool/best-practices)
- [Leistungsrichtlinien für Designer und Designer für Unreal](https://docs.unrealengine.com/en-US/TestingAndOptimization/PerformanceAndProfiling/Guidelines/index.html)
- [Bewährte VR-Methoden für Unreal](https://docs.unrealengine.com/en-US/SharingAndReleasing/XRDevelopment/VR/DevelopVR/ContentSetup/index.html)