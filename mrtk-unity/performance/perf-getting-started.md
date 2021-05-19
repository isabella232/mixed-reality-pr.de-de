---
title: Leistungsindikatoren Erste Schritte
description: Dokumentation zum Verstehen und Anpassen der Vorform in MRTK.
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 1ddc057c7f3966375d512a5e4a714dce093412e6
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144864"
---
# <a name="performance"></a>Leistung

## <a name="getting-started"></a>Erste Schritte

Die einfachste Möglichkeit, die Leistung zu rationalisieren, ist die Framerate oder wie oft Ihre Anwendung ein Bild pro Sekunde rendern kann. Es ist wichtig, die Zielframerate zu erfüllen, wie von der Zielplattform (d. h. [Windows Mixed Reality](/windows/mixed-reality/understanding-performance-for-mixed-reality), [Oculus](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-guidelines/)usw.). Auf HoloLens beträgt die Zielframerate beispielsweise 60 FPS. Anwendungen mit niedriger Framerate können zu benutzerfreundlicheren Benutzeroberflächen führen, wie z. B. der Hologrammsstabilisierung, der Weltverfolgung, der Handverfolgung und mehr. [](../performance/hologram-stabilization.md) Das Mixed Reality Toolkit bietet eine Vielzahl von Tools und Skripts, um Entwicklern das Nachverfolgen und Erreichen einer qualitativ hochwertigen Framerate zu ermöglichen.

### <a name="visual-profiler"></a>Visueller Profiler

Um die Leistung über die Lebensdauer der Entwicklung kontinuierlich nachverfolgung zu können, wird dringend empfohlen, beim Debuggen einer Anwendung immer ein Visuelles mit Framerate & ausführen. Das Mixed Reality Toolkit stellt das [Visual Profiler-Diagnosetool](../features/diagnostics/using-visual-profiler.md) bereit, das Echtzeitinformationen zur aktuellen FPS- und Speicherauslastung in der Anwendungsansicht liefert. Der Visual Profiler kann über die Diagnosesystemeinstellungen [unter](../features/diagnostics/diagnostics-system-getting-started.md) dem [MRTK-Profilinspektor konfiguriert werden.](../configuration/mixed-reality-configuration-guide.md)

Darüber hinaus ist es besonders wichtig, den Visual Profiler zum Nachverfolgen der Framerate zu verwenden, wenn er auf dem Gerät ausgeführt wird, im Gegensatz zur Ausführung im Unity-Editor oder einem Emulator. Die genauesten Leistungsergebnisse werden dargestellt, wenn auf dem Gerät mit [Releasekonfigurations-Builds ausgeführt wird.](/visualstudio/debugger/how-to-set-debug-and-release-configurations?preserve-view=true&view=vs-2019)

> [!NOTE]
> Wenn Sie für Windows Mixed Reality erstellen, stellen Sie die Bereitstellung mit [MASTER-Konfigurations-Builds vor.](/windows/mixed-reality/exporting-and-building-a-unity-visual-studio-solution#building_and_deploying_a_unity_visual_studio_solution)

![Visual Profiler-Schnittstelle](../features/images/Diagnostics/VisualProfiler.png)

### <a name="optimize-window"></a>Fenster "Optimieren"

Das [MRTK-Optimierungsfenster](../features/tools/optimize-window.md) bietet Informationen und Automatisierungstools, mit deren Hilfe Mixed Reality-Entwickler ihre Umgebung für die leistungsstärksten Ergebnisse einrichten und potenzielle Engpässe in ihren Szenenressourcen & können. Bestimmte Schlüsselkonfigurationen in Unity können dabei helfen, wesentlich optimierte Ergebnisse für Mixed Reality-Projekte zu liefern.

Im Allgemeinen umfassen diese Einstellungen Renderingkonfigurationen, die ideal für Mixed Reality sind. Mixed Reality-Anwendungen sind im Vergleich zur herkömmlichen 3D-Grafikentwicklung einzigartig, da es zwei Bildschirme gibt (d. h. zwei Augen), die für die gesamte Szene gerendert werden sollen.

Die empfohlenen Einstellungen, auf die unten verwiesen wird, können in einem Unity-Projekt mithilfe des MRTK-Optimierungsfensters automatisch konfiguriert werden.

![MRTK Optimize Window Settings](../features/images/performance/OptimizeWindow_Settings.png)

### <a name="unity-profiler"></a>Unity Profiler

Der [Unity Profiler](https://docs.unity3d.com/Manual/ProfilerWindow.html) ist ein nützliches Tool, um Details zur Anwendungsleistung auf Frame-by-Frame-Ebene zu untersuchen.

#### <a name="time-spent-on-the-cpu"></a>Für die CPU aufgewendete Zeit

![Unity Profiler-Beispieldiagramm](../features/images/performance/UnityProfilerGraph.png)

Um komfortable Frameraten (in der Regel 60 Frames pro Sekunde) zu gewährleisten, müssen Anwendungen eine maximale Framezeit von 16,6 Millisekunden CPU-Zeit erreichen. Um die Kosten der MRTK-Funktionalität zu ermitteln, enthält das Microsoft Mixed Reality Toolkit Marker für Codepfade der inneren Schleife (pro Frame). Diese Marker verwenden das folgende Format, um das Verständnis der jeweiligen verwendeten Funktionalität zu erleichtern:

```
[MRTK] className.methodName
```

> [!Note]
> Nach dem Methodennamen können weitere Daten vorhanden sein. Dies wird verwendet, um bedingt ausgeführte, potenziell teure Funktionen zu identifizieren, die durch kleine Änderungen am Anwendungscode vermieden werden können.

![Beispielhierarchie für Unity Profiler](../features/images/performance/UnityProfilerHierarchy.png)

In diesem Beispiel wurde die Hierarchie erweitert, um zu zeigen, dass die UpdateHandData-Methode der WindowsMixedRealityArticulatedHand-Klasse während des analysierten Frames 0,44 ms CPU-Zeit verbraucht. Anhand dieser Daten kann ermittelt werden, ob ein Leistungsproblem mit Anwendungscode oder von einem anderen System aus zusammenhängt.

Entwicklern wird dringend empfohlen, Anwendungscode auf ähnliche Weise zu instrumentieren. Der Hauptfokus für die Instrumentierung von Anwendungscode liegt innerhalb von Ereignishandlern, da diese Methoden der MRTK-Updateschleife in Rechnung gestellt werden, wenn Ereignisse ausgelöst werden. Hohe Framezeiten innerhalb der MRTK-Updateschleife können auf teuren Code in Ereignishandlermethoden hindeuten.

## <a name="recommended-settings-for-unity"></a>Empfohlene Einstellungen für Unity

### <a name="single-pass-instanced-rendering"></a>Single-Pass Instanzrendering

Die Standardmäßige Renderingkonfiguration für XR in Unity ist [Multipass.](https://docs.unity3d.com/ScriptReference/StereoRenderingPath.MultiPass.html) Diese Einstellung weist Unity an, die gesamte Renderpipeline zweimal für jedes Auge auszuführen. Dies kann optimiert werden, indem Sie stattdessen [Single Pass Instanced Rendering](https://docs.unity3d.com/Manual/SinglePassInstancing.html) auswählen. Diese Konfiguration nutzt [Renderzielarrays,](https://en.wikipedia.org/wiki/Multiple_Render_Targets) um einen einzelnen Zeichnen-Aufruf ausführen zu können, der Instanzen in das entsprechende Renderziel [für](https://en.wikipedia.org/wiki/Render_Target) jedes Auge einbetten kann. Darüber hinaus ermöglicht dieser Modus, dass das ganze Rendering in einer einzigen Ausführung der Renderingpipeline erfolgt. Daher kann die Auswahl des Single Pass Instanced-Renderings als Renderingpfad für eine Mixed Reality-Anwendung erhebliche Zeit für die [CPU-&-GPU](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/) sparen und ist die empfohlene Renderingkonfiguration.

Um jedoch einen einzelnen Zeichnen-Aufruf für jedes Gitter für jedes Auge aus geben zu können, muss [die GPU-Instancing](https://docs.unity3d.com/Manual/GPUInstancing.html) von allen Shadern unterstützt werden. Durch die Instancing kann die GPU Multiplex-Zeichnen-Aufrufe über beide Augen hinweg ausführen. Integrierte Unity-Shader sowie der [MRTK Standard-Shader](../features/rendering/mrtk-standard-shader.md) enthalten standardmäßig die erforderlichen Anweisungen für die Instancing im Shadercode. Wenn Sie jedoch benutzerdefinierte Shader für Unity schreiben, müssen diese Shader möglicherweise aktualisiert werden, um single pass Instanced-Rendering zu unterstützen.

#### <a name="example-code-for-custom-shader"></a>[Beispielcode für benutzerdefinierten Shader](https://docs.unity3d.com/Manual/SinglePassInstancing.html)

```
struct appdata
{
    float4 vertex : POSITION;
    float2 uv : TEXCOORD0;

    UNITY_VERTEX_INPUT_INSTANCE_ID //Insert
};

struct v2f
{
    float2 uv : TEXCOORD0;
    float4 vertex : SV_POSITION;

    UNITY_VERTEX_OUTPUT_STEREO //Insert
};

v2f vert (appdata v)
{
    v2f o;

    UNITY_SETUP_INSTANCE_ID(v); //Insert
    UNITY_INITIALIZE_OUTPUT(v2f, o); //Insert
    UNITY_INITIALIZE_VERTEX_OUTPUT_STEREO(o); //Insert

    o.vertex = UnityObjectToClipPos(v.vertex);

    o.uv = v.uv;

    return o;
}
```

### <a name="quality-settings"></a>Qualitätseinstellungen

Unity bietet [Voreinstellungen, um die Qualität des](https://docs.unity3d.com/Manual/class-QualitySettings.html) Renderings für jeden Plattformendpunkt zu steuern. Diese Voreinstellungen steuern, welche grafischen Features aktiviert werden können, z. B. Schatten, Antialiasing, globale Benutzeroberfläche und mehr. Es wird empfohlen, diese Einstellungen zu senken und die Anzahl von Berechnungen zu optimieren, die während des Renderings ausgeführt werden.

*Schritt 1:* Aktualisieren von Mixed Reality-Unity-Projekten für die Verwendung der *Einstellung "Low Quality"*  
**Bearbeiten**  >  **Projekteinstellungen**, und wählen Sie dann die **Kategorie Qualität** aus, > für *die* UWP-Plattform niedrige Qualität auswählen.

*Schritt 2:* Deaktivieren Sie für jede Unity-Szenendatei [globale Echtzeit-Benachrichtigungen.](https://docs.unity3d.com/Manual/LightMode-Realtime.html)  
**Fenster**  >  **Rendering**  >  **Beleuchtungseinstellungen**  >  [Deaktivieren Der *globale Echtzeitausgehungs-Kontrollkästchen*](https://docs.unity3d.com/Manual/GlobalIllumination.html)

### <a name="depth-buffer-sharing-hololens"></a>Tiefenpufferfreigabe (HoloLens)

Wenn Sie für die Windows Mixed Reality Plattform und insbesondere HoloLens entwickeln, kann die Aktivierung *der Tiefenpufferfreigabe* unter *XR-Einstellungen* bei der [Hologrammunterstärkung](../performance/hologram-stabilization.md)helfen. Die Verarbeitung des Tiefenpuffers kann jedoch Leistungskosten verursachen, insbesondere bei Verwendung des [24-Bit-Tiefenformats.](https://docs.unity3d.com/ScriptReference/PlayerSettings.VRWindowsMixedReality-depthBufferFormat.html) Daher wird *dringend empfohlen,* den Tiefenpuffer auf 16-Bit-Genauigkeit zu konfigurieren.

Wenn [Z-Fighting](https://en.wikipedia.org/wiki/Z-fighting) aufgrund des niedrigeren Bitformats auftritt, vergewissern Sie sich, dass die [entfernte Clipebene](https://docs.unity3d.com/Manual/class-Camera.html) aller Kameras auf den niedrigsten möglichen Wert für die Anwendung festgelegt ist. Unity legt standardmäßig eine entfernte Clipebene von 1.000 m fest. Auf HoloLens ist eine weit entfernte Clipebene von 50 m in der Regel für die meisten Anwendungsszenarien mehr als ausreichend.

> [!NOTE]
> Bei Verwendung des *16-Bit-Tiefenformats* funktionieren die erforderlichen Auswirkungen des Schablonenpuffers nicht, da Unity in dieser Einstellung [keinen Schablonenpuffer erstellt.](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) Wenn Sie umgekehrt das *24-Bit-Tiefenformat* auswählen, wird in der Regel ein 8-Bit-Schablonenpuffer erstellt, sofern dies auf der Endpunktgrafikplattform anwendbar ist.
>
> Wenn Sie eine [Mask-Komponente](https://docs.unity3d.com/Manual/script-Mask.html) verwenden, die den Schablonenpuffer erfordert, erwägen Sie stattdessen die Verwendung von [RectMask2D,](https://docs.unity3d.com/Manual/script-RectMask2D.html) die den Schablonenpuffer nicht benötigt und daher in Verbindung mit einem *16-Bit-Tiefenformat* verwendet werden kann.

> [!NOTE]
> Um schnell zu bestimmen, welche Objekte in einer Szene nicht visuell in den Tiefenpuffer schreiben, können Sie das [ *Hilfsprogramm Tiefenpuffer rendern*](../configuration/mixed-reality-configuration-guide.md#editor-utilities) unter den *Editoreinstellungen* im MRTK-Konfigurationsprofil verwenden.

### <a name="optimize-mesh-data"></a>Optimieren von Meshdaten

Mit den Einstellungen zum Optimieren von [Gitternetzdaten](https://docs.unity3d.com/ScriptReference/PlayerSettings-stripUnusedMeshComponents.html) wird versucht, nicht verwendete Scheitelpunktattribute in Ihrer Anwendung zu entfernen. Die Einstellung führt dies durch Ausführung über jeden Shaderdurchlauf in jedem Material aus, das sich in jedem Gitternetz im Build befindet. Dies ist gut für die Größe der Spieldaten und die Laufzeitleistung geeignet, kann aber die Buildzeiten erheblich beeinträchtigen.

Es wird empfohlen, diese Einstellung während der Entwicklung zu deaktivieren und während der Erstellung des Masterbuilds erneut zu aktivieren. Die Einstellung finden **Sie** unter  >  **Projekteinstellungen** bearbeiten  >  **Player**  >  **Andere Einstellungen**  >  **Gitternetzdaten optimieren**.

## <a name="general-recommendations"></a>Allgemeine Empfehlungen

Die Leistung kann eine mehrdeutige und sich ständig ändernde Herausforderung für Mixed Reality-Entwickler sein, und das Wissensspektrum zur Rationalisierung der Leistung ist sehr umfangreich. Es gibt jedoch einige allgemeine Empfehlungen, um zu verstehen, wie die Leistung einer Anwendung an den Ansatz geht.

Es ist hilfreich, die Ausführung einer Anwendung in die Teile zu vereinfachen, die auf der *CPU* oder *GPU* ausgeführt werden, und so zu ermitteln, ob eine App durch eine der komponentengebundenen Komponenten gebunden ist.  Es kann Engpässe geben, die sich sowohl auf Verarbeitungseinheiten als auch auf einige eindeutige Szenarien erstrecken, die sorgfältig untersucht werden müssen. Für die ersten Schritte ist es jedoch gut zu verstehen, wo eine Anwendung für die meiste Zeit ausgeführt wird.

### <a name="gpu-bounded"></a>GPU gebunden

Da die meisten Plattformen für Mixed Reality-Anwendungen [stereokopiertes Rendering](https://en.wikipedia.org/wiki/Stereoscopy)verwenden, ist es aufgrund der Art des Renderns eines "doppelweiten" Bildschirms sehr häufig gpugebunden. Futhermore: Mobile Mixed Reality-Plattformen wie HoloLens oder Oculus Quest werden durch cpu-& GPU-Verarbeitungsleistung für Mobilgeräte eingeschränkt.

Wenn Sie sich auf die GPU konzentrieren, gibt es im Allgemeinen zwei wichtige Phasen, in denen eine Anwendung jeden Frame abschließen muss.

1. Ausführen des [Vertex-Shaders](https://en.wikipedia.org/wiki/Shader#Vertex_shaders)
2. Führen Sie den [Pixelshader](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) (auch als Fragment-Shader bezeichnet) aus.

Ohne einen tieferen Einblick in das komplexe Feld der Computergrafiken & [Renderingpipelines](https://en.wikipedia.org/wiki/Graphics_pipeline)ist jede Shaderphase ein Programm, das auf der GPU ausgeführt wird, um Folgendes zu erzeugen.

1. Vertex-Shader transformieren Netzvertices in Koordinaten im Bildschirmbereich (d. h. Pro Scheitelpunkt ausgeführter Code)
2. Pixel-Shader berechnen die Farbe, die für ein bestimmtes Pixel- und Gitternetzfragment gezeichnet werden soll (d. h. Codeausführung pro Pixel)

In Bezug auf die Leistungsoptimierung ist es in der Regel schwieriger, sich auf die Optimierung der Vorgänge im Pixel-Shader zu konzentrieren. Eine Anwendung muss möglicherweise nur einen Cube zeichnen, der nur acht Scheitelsteine enthält. Der Bildschirmraum, den der Cube belegt, liegt jedoch wahrscheinlich in der Reihenfolge von Millionen von Pixeln. Daher kann die Reduzierung von Shadercode um z. B. 10 Vorgänge erheblich mehr Arbeit sparen, wenn der Pixel-Shader reduziert wird als der Vertex-Shader.

Dies ist einer der Hauptgründe für die Nutzung des [MRTK Standard-Shaders,](../features/rendering/mrtk-standard-shader.md) da dieser Shader im Allgemeinen viel weniger Anweisungen pro Pixel & Scheitelpunkt als der Unity Standard-Shader ausführen und gleichzeitig vergleichbare ergebnisse erzielen kann.

|    CPU-Optimierungen      |             GPU-Optimierungen              |
|---------------------------|--------------------------------------------|
| Logik der App-Simulation      | Renderingvorgänge |
| Vereinfachen der Physik          | Reduzieren von Beleuchtungsberechnungen |
| Vereinfachen von Animationen       | Reduzieren der Polygonanzahl & Anzahl von ziehbaren Objekten |
| Verwalten der Garbage Collection | Reduzieren der Anzahl von transparenten Objekten |
| Cacheverweise          | Vermeiden von Nachverarbeitungs-/Vollbildeffekten  |

### <a name="draw-call-instancing"></a>Draw-Aufrufinstancing

Einer der häufigsten Fehler in Unity, der die Leistung verringert, ist das Klonen von Materialien zur Laufzeit. Wenn GameObjects dasselbe Material gemeinsam nutzen und/oder dasselbe Gitternetz sind, können sie *[](https://docs.unity3d.com/Manual/DrawCallBatching.html)* mit Techniken wie statischer Batchverarbeitung, *[](https://docs.unity3d.com/Manual/DrawCallBatching.html)* dynamischer Batchverarbeitung und GPU-Instanzion *[für](https://docs.unity3d.com/Manual/GPUInstancing.html)* einzelne Zeichnen-Aufrufe optimiert werden. Wenn der Entwickler jedoch die Eigenschaften eines [Renderermaterials](https://docs.unity3d.com/ScriptReference/Renderer-material.html) zur Laufzeit ändert, erstellt Unity eine Klonkopie des zugewiesenen Materials.

Wenn z. B. 100 Cubes in einer Szene vorhanden sind, möchte ein Entwickler zur Laufzeit jedem Cube eine eindeutige Farbe zuweisen. Durch den Zugriff auf [*renderer.material.color*](https://docs.unity3d.com/ScriptReference/Material-color.html) in C# erstellt Unity ein neues Material im Arbeitsspeicher für diesen bestimmten Renderer/GameObject. Jeder der 100 Cubes verfügt über ein eigenes Material und kann daher nicht zu einem Zeichnen-Aufruf zusammengeführt werden, sondern zu 100 Zeichnen-Aufrufanforderungen von der CPU an die GPU.

Um dieses Hindernis zu überwinden und dennoch eine eindeutige Farbe pro Cube zuzuweisen, sollten Entwickler [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html)nutzen.

```c#
private PropertyBlock m_PropertyBlock ;
private Renderer myRenderer;

private void Start()
{
     myRenderer = GetComponent<Renderer>();
     m_PropertyBlock = new MaterialPropertyBlock();
}

private void ChangeColor()
{
    // Creates a copy of the material once for this renderer
    myRenderer.material.color = Color.red;

    // vs.

    // Retains instancing capability for renderer
    m_PropertyBlock.SetColor("_Color", Color.red);
    myRenderer.SetPropertyBlock(m_PropertyBlock);
}
```

## <a name="unity-performance-tools"></a>Unity-Leistungstools

Unity bietet hervorragende Leistungstools, die in den Editor integriert sind.

- [Unity Profiler](https://docs.unity3d.com/Manual//Profiler.html)
- [Unity-Framedebugger](https://docs.unity3d.com/Manual/FrameDebugger.html)

Wenn Sie den groben Leistungskomparfall zwischen einem Shader und einem anderen schätzen, ist es hilfreich, jeden Shader zu kompilieren und die Anzahl der Vorgänge pro Shaderstufe anzuzeigen. Wählen Sie hierzu ein [Shaderobjekt](https://docs.unity3d.com/Manual/class-Shader.html) aus, und klicken Sie auf die Schaltfläche *Code kompilieren und anzeigen.* Dadurch werden alle Shadervarianten kompiliert und Visual Studio mit den Ergebnissen geöffnet. Hinweis: Die erzeugten Statistikergebnisse können variieren, je nachdem, welche Features für Materialien mit dem angegebenen Shader aktiviert wurden. Unity kompiliert nur die Shadervarianten, die direkt im aktuellen Projekt verwendet werden.

Beispiel für Unity Standard-Shaderstatistik

![Unity Standard Shader Statistics 1](../features/images/performance/UnityStandardShader-Stats.PNG)

MRTK Standard-Shaderstatistikbeispiel

![MRTK Standard Shader Statistics 2](../features/images/performance/MRTKStandardShader-Stats.PNG)

## <a name="see-also"></a>Weitere Informationen

### <a name="unity"></a>Unity

- [Unity-Leistungsoptimierung für Einsteiger](https://www.youtube.com/watch?v=1e5WY2qf600)
- [Tutorials zur Unity-Leistungsoptimierung](https://unity3d.com/learn/tutorials/topics/performance-optimization)
- [Bewährte Methoden für die Unity-Optimierung](https://docs.unity3d.com/Documentation/Manual/BestPracticeUnderstandingPerformanceInUnity.html)
- [Optimieren der Grafikleistung](https://docs.unity3d.com/Manual/OptimizingGraphicsPerformance.html)
- [Praktische Anleitung zur Optimierung mobiler Geräte](https://docs.unity3d.com/Manual/MobileOptimizationPracticalGuide.html)

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

- [Empfohlene Einstellungen für Unity](/windows/mixed-reality/recommended-settings-for-unity)
- [Grundlegendes zur Leistung Mixed Reality](/windows/mixed-reality/understanding-performance-for-mixed-reality)
- [Leistungsempfehlungen für Unity](/windows/mixed-reality/performance-recommendations-for-unity)
- [Leitfaden zur Ereignisablaufverfolgung für Windows Unity](https://docs.unity3d.com/uploads/ExpertGuides/Analyzing_your_game_performance_using_Event_Tracing_for_Windows.pdf)

### <a name="oculus"></a>Oculus

- [Leistungsrichtlinien](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-guidelines/)
- [Leistungstools](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-tools/)

### <a name="mesh-optimization"></a>Mesh-Optimierung

- [Optimieren von 3D-Modellen](/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets)
- [Bewährte Methoden zum Konvertieren und Optimieren von 3D-Echtzeitmodellen](/dynamics365/mixed-reality/import-tool/best-practices)