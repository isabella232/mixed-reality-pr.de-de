---
title: Grundlegendes zur Leistung für gemischte Realität
description: Erweiterte Informationen und Details zur Optimierung der Leistung der Windows Mixed Reality-app.
author: hferrone
ms.author: v-hferrone
ms.date: 3/26/2019
ms.topic: article
keywords: Gemischte Windows-Realität, gemischte Realität, Virtual Reality, VR, Mr, Leistung, Optimierung, CPU, GPU
ms.openlocfilehash: fc7b6385acda9079a649131b9e6eccf5ac067819
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530071"
---
# <a name="understanding-performance-for-mixed-reality"></a>Grundlegendes zur Leistung für gemischte Realität

Dieser Artikel ist eine Einführung in das Verständnis der Bedeutung der Leistung für ihre gemischte Reality-app.  Die Benutzer Leistung kann erheblich beeinträchtigt werden, wenn Ihre Anwendung nicht mit optimaler Framerate ausgeführt wird. Holograms werden instabil angezeigt, und die Kopf Nachverfolgung der Umgebung ist ungenau, was zu einem schlechten Benutzer Verhalten führt. Die Leistung muss als erstklassige Funktion für die Entwicklung in gemischter Realität und nicht als polnische Aufgabe angesehen werden.

Die leistungsstarken Framerate-Werte für jede Zielplattform sind unten aufgeführt.

| Plattform | Zielframe Rate |
|----------|-------------------|
| [HoloLens](../../hololens-hardware-details.md) | 60 FPS |
| [Windows Mixed Reality Ultra PCs](../../discover/immersive-headset-hardware-details.md) | 90 fps |
| [Windows Mixed Reality-PCs](../../discover/immersive-headset-hardware-details.md) | 60 FPS |

Im folgenden Framework werden bewährte Methoden zum Erreichen von Ziel Frameraten beschrieben. Informationen zum Messen und verbessern der Framerate in der Unity-Umgebung finden Sie im [Artikel Leistungs Empfehlungen für Unity](../unity/performance-recommendations-for-unity.md) .

## <a name="understanding-performance-bottlenecks"></a>Grundlegendes zu Leistungs Engpässen

Wenn Ihre APP einen leistungsstarken Framerate hat, besteht der erste Schritt darin, zu analysieren und zu verstehen, wo Ihre Anwendung Rechen intensiv ist. Es gibt zwei primäre Prozessoren, die für die Arbeit zum Rendering Ihrer Szene verantwortlich sind: die CPU und die GPU, die jeweils unterschiedliche Aspekte ihrer Mixed Reality-App verarbeiten. Die drei wichtigsten Punkte, auf denen Engpässe auftreten können, sind: 

1. **App-Thread-CPU** -
    Verantwortlich für Ihre APP-Logik, einschließlich der Verarbeitung von Eingaben, Animationen, Physik und anderer App-Logik.
2. **Renderthread-CPU zu GPU** -verantwortlich für das übermitteln der Draw-Aufrufe an die GPU. Wenn Ihre APP ein Objekt (z. b. einen Cube oder ein Modell) renderren, sendet dieser Thread eine Anforderung an die GPU, um die Vorgänge durchzuführen.
3. **GPU** : in der Regel wird die Grafik Pipeline der Anwendung verarbeitet, um 3D-Daten (Modelle, Texturen usw.) in Pixel umzuwandeln. Letztendlich wird ein 2D-Image erstellt, das an den Bildschirm Ihres Geräts gesendet wird.

![Lebensdauer eines Frames](images/lifetime-of-a-frame.png)

Im Allgemeinen werden hololens-Anwendungen GPU-gebunden, aber nicht immer. Verwenden Sie die unten aufgeführten Tools und Verfahren, um zu verstehen, wo ihre jeweilige App Engpässe hat.

## <a name="how-to-analyze-your-application"></a>Analysieren der Anwendung

Es gibt viele Tools, mit denen Sie das Leistungsprofil und potenzielle Engpässe in ihrer gemischten Reality-Anwendung nachvollziehen können. 

Im folgenden finden Sie einige gängige Tools, die Ihnen helfen, umfassende Profil Erstellungs Informationen für Ihre Anwendung zu erfassen:
- [Intel Graphics Performance Analyzer](https://software.intel.com/gpa)
- [Visual Studio-Grafik-Debuggers](https://docs.microsoft.com/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics)
- [Unity-Profiler](https://docs.unity3d.com/Manual/Profiler.html)
- [Unity-Frame Debugger](https://docs.unity3d.com/Manual/FrameDebugger.html)

### <a name="how-to-profile-in-any-environment"></a>Profilerstellung in einer beliebigen Umgebung

Eine Möglichkeit, um zu ermitteln, ob Ihre APP GPU oder CPU-gebunden ist, besteht darin, die Auflösung der renderzielausgabe zu verringern. Indem Sie die Anzahl der zu berechnenden Pixel verringern, verringern Sie die GPU-Auslastung. Das Gerät wird in eine kleinere Textur und dann up-Sample angezeigt, um das endgültige Bild anzuzeigen.

Nach dem verringern der renderinglösung:
1) Anwendungs Framerate **erhöht** sich, und Sie sind wahrscheinlich **an GPU gebunden** .
1) Die Anwendungs Framerate ist **unverändert**, und Sie sind wahrscheinlich **CPU-gebunden** .

>[!NOTE]
>Unity bietet die Möglichkeit, die renderzielauflösung Ihrer Anwendung zur Laufzeit mithilfe der *[xrsettings. renderviewportscale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* -Eigenschaft problemlos zu ändern. Das endgültige Bild, das auf dem Gerät angezeigt wird, hat eine Fehlerbehebung. Die Plattform zeigt eine Stichprobe der Ausgabe mit niedrigerer Auflösung an, um ein höheres Auflösungs Bild für das Rendering in anzeigen zu erstellen. 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a>So verbessern Sie Ihre Anwendung

### <a name="cpu-performance-recommendations"></a>CPU-Leistungsempfehlungen

Im allgemeinen umfasst die meiste Arbeit in einer Mixed Reality-Anwendung auf der CPU die Simulation der Szene und die Verarbeitung der Anwendungslogik. Die folgenden Bereiche sind für die Optimierung bestimmt:

- Animationen
- Physische Effekte
- Speicher Belegungen
- Komplexe Algorithmen (d. h. umgekehrte Kinematik, Pfad Suche)

### <a name="gpu-performance-recommendations"></a>GPU-Leistungsempfehlungen

#### <a name="understanding-bandwidth-vs-fill-rate"></a>Grundlegendes zur Bandbreite im Vergleich zu Füll Raten
Beim Rendern eines Frames auf der GPU wird eine Anwendung entweder durch die Arbeitsspeicher Bandbreite oder die Füllrate gebunden.

- Die Arbeits **Speicherbandbreite** ist die Rate der Lese-und Schreibvorgänge, die die GPU aus dem Arbeitsspeicher
    - Um Bandbreiten Einschränkungen zu identifizieren, verringern Sie die Texturqualität, und prüfen Sie, ob die Framerate verbessert wurde.
    - Ändern Sie in Unity die **Texturqualität** in "   >  **Projekteinstellungen** bearbeiten"  >  **[Qualitätseinstellungen](https://docs.unity3d.com/Manual/class-QualitySettings.html)**.
- **Füllrate** bezieht sich auf die Pixel, die pro Sekunde von der GPU gezeichnet werden können.
    - Um die Einschränkungen der Füllrate zu identifizieren, verringern Sie die Bildschirmauflösung, und prüfen Sie, ob Framerate verbessert wurde 
    - Verwenden Sie in Unity die  *[xrsettings. renderviewportscale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* -Eigenschaft.

Die Speicherbandbreite umfasst in der Regel Optimierungen für:
1) Niedrigere Textur Auflösungen
2) Verwenden Sie weniger Texturen (normale, Glanz usw.).

Die Füllrate konzentriert sich auf das Reduzieren der Anzahl von Vorgängen, die für ein letztes gerendertes Pixel berechnet werden müssen, einschließlich:
1) Anzahl der zu Rendering/zu verarbeitenden Objekte
2) Anzahl von Vorgängen pro Shader
3) Anzahl von GPU-Phasen bis zum Endergebnis (Geometry-Shader, nach Verarbeitungs Effekte usw.)
4) Anzahl der zu Rendering enden Pixel (Anzeige Auflösung)

#### <a name="reduce-polygon-count"></a>Reduzieren der Polygon Anzahl

Höhere Polygon Zahlen führen zu weiteren Vorgängen für die GPU, sodass die [Anzahl von Polygonen](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets) in der Szene die Rendering-Zeit reduziert. Es gibt weitere Faktoren, die das Schattieren der Geometrie teuer machen, aber die Polygon Anzahl ist die einfachste Metrik, um zu bestimmen, wie viel Arbeit für das Rendern einer Szene benötigt wird.

#### <a name="limit-overdraw"></a>Einschränken des Überzeichnens

Ein hoher Alphablendings tritt auf, wenn mehrere Objekte gerendert, aber nicht auf dem Bildschirm angezeigt werden, da Sie durch ein okding Objekt ausgeblendet werden. Stellen Sie sich vor, eine Wand mit Objekten dahinter zu betrachten. Die gesamte Geometrie würde zum Rendern verarbeitet, aber nur die nicht transparente Wand muss gerendert werden, was zu unnötigen Vorgängen führt.

#### <a name="shaders"></a>Shader

Shader sind kleine Programme, die auf der GPU ausgeführt werden und zwei wichtige Schritte zum Rendern ausführen:
1) Bestimmen, welche Scheitel Punkte gezeichnet werden sollen und wo Sie sich im Bildschirmbereich befinden (der Vertexshader)
    - Der Vertex-Shader wird für jedes Mesh pro Scheitelpunkt ausgeführt.
2) Bestimmen der Farbe jedes Pixels (Pixelshader)
    - Der Pixelshader wird pro Pixel ausgeführt und von der Geometrie in der zielrendertextur gerendert.

In der Regel führen Shader viele Transformationen und Beleuchtungsberechnungen durch. Obwohl komplexe Beleuchtungs Modelle, Schatten und andere Vorgänge tolle Ergebnisse erzeugen können, erhalten Sie auch einen Preis. Durch das Reduzieren der Anzahl von Vorgängen, die in Shadern berechnet werden, kann die für die GPU pro Frame benötigte Arbeit erheblich reduziert werden.

##### <a name="shader-coding-recommendations"></a>Codierungs Empfehlungen für Shader

- Verwenden der bilinearen Filterung, wann immer möglich
- Neuanordnung von Ausdrücken zur Verwendung von verrückten intrinsischen Funktionen zum gleich zeigenden multiplizieren und hinzufügen
- So weit wie möglich auf der CPU vorab berechnen und als Konstanten an das Material übergeben
- **Verschieben von Vorgängen vom Pixelshader zum Vertex-Shader bevorzugen**
    - Im Allgemeinen ist die Anzahl der Scheitel Punkte wesentlich kleiner als die Anzahl der Pixel (720p beträgt 921.600 Pixel, 1080p beträgt 2.073.600 Pixel usw.).

#### <a name="remove-gpu-stages"></a>Entfernen von GPU-Stufen

Die Auswirkungen nach der Verarbeitung können teuer sein und die Füllrate Ihrer Anwendung erhöhen, einschließlich Antialiasing-Techniken wie MSAA. Bei hololens empfiehlt es sich, diese Techniken und zusätzlichen shaderphasen wie Geometrie, Hülle und Compute-Shader zu vermeiden.

## <a name="memory-recommendations"></a>Empfehlungen zum Arbeitsspeicher

Übermäßig hohe Speicher Belegungs-und Aufteilungs Vorgänge können zu inkonsistenter Leistung, fixierten Frames und anderem schädlichen Verhalten führen. Es ist besonders wichtig, die Arbeitsspeicher Aspekte bei der Entwicklung in Unity zu verstehen, da die Speicherverwaltung durch die Garbage Collector gesteuert wird.

#### <a name="object-pooling"></a>Objektpooling

Objekt Pooling ist ein gängiges Verfahren, um die Kosten von kontinuierlichen Zuordnungen und Aufhebungen von Objekten zu verringern. Dies erfolgt durch die Zuordnung eines großen Pools identischer Objekte und die Wiederverwendung inaktiver, verfügbarer Instanzen aus diesem Pool, anstatt ständig Objekte im Zeitverlauf zu erzeugen und zu zerstören. Objekt Pools eignen sich hervorragend für wiederverwendbare Komponenten, die während einer APP über eine Variablen Lebensdauer verfügen.

## <a name="see-also"></a>Weitere Informationen
- [Leistungsempfehlungen für Unity](../unity/performance-recommendations-for-unity.md)
- [Empfohlene Einstellungen für Unity](../unity/recommended-settings-for-unity.md)
- [Optimieren von 3D-Modellen](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets)
- [Bewährte Methoden zum umrechnen und Optimieren von Echt Zeit 3D-Modellen](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/best-practices)

