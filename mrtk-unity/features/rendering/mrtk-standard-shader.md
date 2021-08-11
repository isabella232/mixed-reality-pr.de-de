---
title: MRTK-Standard-Shader
description: Dokumentation für MRTKStandardShader
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Material Shader
ms.openlocfilehash: e740c1cb662f88f7ce925482de9ed758d5f18ee152363a663aa678056ba2825f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115191157"
---
# <a name="mrtk-standard-shader"></a>MRTK-Standard-Shader

![Beispiele für Standard-Shader](../images/mrtk-standard-shader/MRTK_StandardShader.jpg)

Das MRTK Standard-Schattierungssystem verwendet einen einzelnen, flexiblen Shader, der Visuals ähnlich dem Standard-Shader von Unity erreichen, [Fluent Design System](https://www.microsoft.com/design/fluent/) Prinzipien implementieren und auf Mixed Reality-Geräten fähig bleiben kann.

## <a name="example-scenes"></a>Beispielszenen

Die Beispiele für Shadermaterial finden Sie in der **MaterialGallery-Szene** unter `MRTK/Examples/Demos/StandardShader/Scenes/` . Alle Materialien in dieser Szene verwenden den MRTK-/Standard-Shader.

![Materialkatalog](../images/mrtk-standard-shader/MRTK_MaterialGallery.jpg)

Sie finden eine Vergleichsszene zum Vergleichen und Testen des MRTK-/Standard-Shaders mit dem Unity/Standard-Shaderbeispiel in der **StandardMaterialComparison-Szene** unter `MRTK/Examples/Demos/StandardShader/Scenes/` .

![Materialvergleich](../images/mrtk-standard-shader/MRTK_StandardMaterialComparison.gif)

## <a name="architecture"></a>Architektur

Das MRTK-/Standard-Schattierungssystem ist ein "Uber-Shader", der das [Variant-Feature des Unity-Shaderprogramms](https://docs.unity3d.com/Manual/SL-MultipleProgramVariants.html) verwendet, um automatisch optimalen Shadercode basierend auf Materialeigenschaften zu generieren. Wenn ein Benutzer Materialeigenschaften im Materialinspektor auswählt, fallen nur Leistungskosten für aktivierte Features an.

## <a name="material-inspector"></a>Materialinspektor

Für den MRTK-/Standard-Shader mit dem Namen ist ein benutzerdefinierter Materialinspektor [`MixedRealityStandardShaderGUI.cs`](xref:Microsoft.MixedReality.Toolkit.Editor.MixedRealityStandardShaderGUI) vorhanden. Der Inspektor aktiviert/deaktiviert automatisch Shaderfunktionen basierend auf der Benutzerauswahl und unterstützt sie beim Einrichten des Renderzustands. Weitere Informationen zu den einzelnen Features **finden Sie im Unity-Editor für eine QuickInfo.**

![Materialinspektor](../images/mrtk-standard-shader/MRTK_MaterialInspector.jpg)

Der erste Teil des Inspektors steuert den Renderzustand des Materials. *Der Renderingmodus* bestimmt, wann und wie ein Material gerendert wird. Das Ziel des MRTK/Standard-Shaders besteht darin, die [Renderingmodi im Unity/Standard-Shader](https://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html)zu spiegeln. Der MRTK-/Standard-Shader enthält auch einen *additiven* Renderingmodus und einen *benutzerdefinierten* Renderingmodus für die vollständige Benutzersteuerung.

| Renderingmodus |         Beschreibung                                                       |
|----------------|---------------------------------------------------------------------------|
| Nicht transparent         | (Standard) Geeignet für normale vollständige Objekte ohne transparente Bereiche.    |
| Ausschnitt         | Ermöglicht die Erstellung von transparenten Effekten, die harte Kanten zwischen den deckenden und transparenten Bereichen aufweisen. In diesem Modus gibt es keine halbtransparenten Bereiche, die Textur ist entweder zu 100 % deckend oder unsichtbar. Dies ist nützlich, wenn Transparenz verwendet wird, um die Form von Materialien zu erstellen, z. B. Materials. |
| Einblenden           | Ermöglicht es den Transparenzwerten, ein Objekt vollständig auszublenden, einschließlich aller Glanzlichter oder Reflektionen, die es haben kann. Dieser Modus ist nützlich, wenn Sie ein ein- oder ausgehendes Objekt animieren möchten. Es eignet sich nicht für das Rendern realistischer transparenter Materialien wie klarem Brillen oder Brillen, da die Reflexionen und Highlights ebenfalls ausgeblendet werden. |
| Transparent    | Geeignet für das Rendern realistischer transparenter Materialien wie klarem Brillen oder Glass. In diesem Modus übernimmt das Material selbst Transparenzwerte (basierend auf dem Alphakanal der Textur und dem Alpha der Tönungsfarbe). Reflektionen und Beleuchtungslichter bleiben jedoch bei voller Klarheit sichtbar, wie dies bei echten transparenten Materialien der Fall ist. |
| Additiv       | Aktiviert einen additiven Mischungsmodus, der die vorherige Pixelfarbe mit der aktuellen Pixelfarbe summiert. Dies ist der bevorzugte Transparenzmodus, um Probleme beim Sortieren der Transparenz zu vermeiden.     |
| Benutzerdefiniert         | Ermöglicht die manuelle Steuerung aller Aspekte des Renderingmodus. Nur für erweiterte Verwendung.   |

![Renderingmodi](../images/mrtk-standard-shader/MRTK_RenderingModes.jpg)

| Cull-Modus |             Beschreibung                                                                                                                                                                       |
|-----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Aus       | Deaktiviert die Gesichtskeulung. Culling sollte nur auf Aus festgelegt werden, wenn ein zweiseitiges Gitternetz erforderlich ist.                                                                                        |
| Front     | Aktiviert das Culling der Vorderseite.                                                                                                                                                        |
| Zurück      | (Standard) Aktiviert [die Gesichtskeulung](https://en.wikipedia.org/wiki/Back-face_culling)im Hintergrund. Das Back face culling sollte so oft wie möglich aktiviert werden, um die Renderingleistung zu verbessern. |

## <a name="performance"></a>Leistung

Einer der Hauptvorteile bei der Verwendung des MRTK Standard-Shaders gegenüber dem Unity-Standard-Shader ist die Leistung. Der MRTK-Standard-Shader ist erweiterbar, um nur die aktivierten Features zu nutzen. Der MRTK Standard-Shader wurde jedoch auch so geschrieben, dass er vergleichbare ansprechende Ergebnisse wie der Unity Standard-Shader liefert, jedoch zu deutlich geringeren Kosten. Eine einfache Möglichkeit zum Vergleichen der Shaderleistung ist die Anzahl der Vorgänge, die auf der GPU ausgeführt werden müssen. Natürlich kann die Größe der Berechnungen durch aktivierte Features und andere Renderingkonfigurationen schwanken. Im Allgemeinen führt der MRTK Standard-Shader jedoch deutlich weniger Berechnungen aus als der Unity Standard-Shader.

Beispiel für Unity Standard-Shaderstatistik

![Unity-Standard-Shader-Statistik](../images/performance/UnityStandardShader-Stats.PNG)

MRTK Standard-Shaderstatistikbeispiel

![MRTK-Standard-Shaderstatistiken](../images/performance/MRTKStandardShader-Stats.PNG)

> [!NOTE]
> Diese Ergebnisse können generiert werden, indem Sie ein [Shaderobjekt](https://docs.unity3d.com/Manual/class-Shader.html) im Unity-Inspektor auswählen und anzeigen und dann auf die Schaltfläche *Code kompilieren und anzeigen* klicken.

## <a name="lighting"></a>Beleuchtung

Das MRTK/Standard verwendet eine einfache Näherung für die Beleuchtung. Da dieser Shader nicht auf physische Richtigkeit und Energieversorgung berechnet wird, wird er schnell und effizient gerendert. Blinn-Phong ist die primäre Beleuchtungstechnik, die mit Fresnel- und bildbasierter Beleuchtung kombiniert wird, um eine ungefähre physische Beleuchtung zu verwenden. Der Shader unterstützt die folgenden Beleuchtungstechniken:

### <a name="directional-light"></a>Gerichtetes Licht

Der Shader beachtet die Richtung, Farbe und Intensität des ersten Unity Directional Light in der Szene (sofern aktiviert). Dynamische Punktlichter, Spotlichter oder ein anderes Unity-Licht werden in Echtzeitlicht nicht berücksichtigt.

### <a name="spherical-harmonics"></a>Sphärische Schwingungen

Der Shader verwendet Lichtsonden, um die Beleuchtung in der Szene mithilfe von [sphärischen Veraltungen anzunähern,](https://docs.unity3d.com/Manual/LightProbes-TechnicalInformation.html)sofern aktiviert. Sphärische Berechnungen werden pro Scheitelpunkt ausgeführt, um die Berechnungskosten zu senken.

### <a name="lightmapping"></a>Lightmapping

Bei statischer Beleuchtung beachtet der Shader Lightmaps, die vom [Lightmapping-System](https://docs.unity3d.com/Manual/Lightmapping.html)von Unity erstellt wurden. Markieren Sie den Renderer einfach als statisch (oder lightmap static), um Lightmaps zu verwenden.

### <a name="hover-light"></a>Schwebelicht

* Siehe [Hover Light](hover-light.md)

### <a name="proximity-light"></a>Näherungslicht

* Siehe [Näherungslicht](proximity-light.md)

## <a name="lightweight-scriptable-render-pipeline-support"></a>Unterstützung für einfache Skripterstellungs-Renderpipelines

Das MRTK enthält einen Upgradepfad, mit dem Entwickler die Lightweight Scriptable Render Pipeline (LWRP) von Unity mit MRTK-Shadern verwenden können. Getestet im Unity 2019.1.1f1- und Lightweight RP 5.7.2-Paket. Anweisungen zu den ersten Schritte mit LWRP finden Sie auf [dieser Seite.](https://docs.unity3d.com/Packages/com.unity.render-pipelines.lightweight@5.10/manual/getting-started-with-lwrp.html)

Wählen Sie zum Durchführen des MRTK-Upgrades folgende Option aus: **Mixed Reality Toolkit -> Utilities -> Upgrade MRTK Standard Shader for Lightweight Render Pipeline (MRTK-Standard-Shader für Lightweight-Renderpipeline** aktualisieren).

![lwrp-Upgrade](../images/mrtk-standard-shader/MRTK_LWRPUpgrade.jpg)

Nach dem Upgrade wird der MRTK-/Standard-Shader geändert, und alle Magentamaterialien (Shaderfehler) sollten korrigiert werden. Um zu überprüfen, ob das Upgrade erfolgreich durchgeführt wurde, überprüfen Sie die Konsole auf: **Aktualisierte Assets/MixedRealityToolkit/StandardAssets/Shaders/MixedRealityStandard.shader für die Verwendung mit der Lightweight-Renderpipeline.**

## <a name="ugui-support"></a>UGUI-Unterstützung

Das MRTK Standard-Schattierungssystem funktioniert mit dem integrierten [UI-System](https://docs.unity3d.com/Manual/UISystem.html)von Unity. Bei Komponenten der Unity-Benutzeroberfläche ist die unity_ObjectToWorld Matrix nicht die Transformationsmatrix der lokalen Transformation, auf der sich die Grafikkomponente befindet, sondern die der übergeordneten Canvas. Viele MRTK-/Standard-Shadereffekte erfordern, dass die Objektskala bekannt ist. Um dieses Problem zu beheben, [`ScaleMeshEffect.cs`](xref:Microsoft.MixedReality.Toolkit.Input.Utilities.ScaleMeshEffect) speichert skalierungsinformationen während der Erstellung von UI-Gitternetzen in UV-Kanalattributen.

Beachten Sie, dass es bei Verwendung einer Unity Image-Komponente empfohlen wird, "None (Sprite)" für das Quellbild anzugeben, um zu verhindern, dass die Unity-Benutzeroberfläche zusätzliche Scheitelpunkte generiert.

Ein Zeichenbereich innerhalb des MRTK fordert zur Hinzufügung einer [`ScaleMeshEffect.cs`](xref:Microsoft.MixedReality.Toolkit.Input.Utilities.ScaleMeshEffect) auf, wenn eine erforderlich ist:

![Scale Mesh-Effekt](../images/mrtk-standard-shader/MRTK_ScaleMeshEffect.jpg)

## <a name="texture-combiner"></a>Textur-Combiner

Um die Parität mit dem Unity Standard-Shader pro Pixel zu verbessern, können Smoothness-, emissive- und Occlusion-Werte alle über [kanalgesteuertes Packen](http://wiki.polycount.com/wiki/ChannelPacking)gesteuert werden. Beispiel:

![Kanalzuordnungsbeispiel](../images/mrtk-standard-shader/MRTK_ChannelMap.gif)

Wenn Sie channel packing verwenden, müssen Sie nur eine Textur anstatt vier separater Texturen in den Arbeitsspeicher laden. Wenn Sie Ihre Texturzuordnungen in einem Programm wie 16000000000000000000000000000000000000000000000 schreiben, können Sie sie wie folgt packen:

| Kanal | Eigenschaft             |
|---------|----------------------|
| Red     | Metallischen             |
| Grün   | Okklusion            |
| Blau    | Ausgabe (Graustufen) |
| Alpha   | Glätte           |

Alternativ können Sie auch das MRTK Texture Combiner Tool verwenden. Um das Tool zu öffnen, wählen Sie **Mixed Reality Toolkit -> Utilities -> Texture Combiner** aus, um das folgende Fenster zu öffnen:

![Textur-Kombiniererbeispiel](../images/mrtk-standard-shader/MRTK_TextureCombiner.jpg)

Dieses Fenster kann automatisch ausgefüllt werden, indem Sie einen Unity Standard-Shader auswählen und auf "Automatisch aus Standardmaterial auffüllen" klicken. Alternativ können Sie manuell eine Textur (oder einen konstanten Wert) pro Rot-, Grün-, Blau- oder Alphakanal angeben. Die Texturkombination wird durch GPU beschleunigt und erfordert keinen CPU-Zugriff auf die Eingabetextur.

## <a name="additional-feature-documentation"></a>Dokumentation zu zusätzlichen Features

Im Folgenden finden Sie zusätzliche Details zu einigen Featuredetails, die mit dem MRTK-/Standard-Shader verfügbar sind.

### <a name="primitive-clipping"></a>Primitives Clipping

![Primitives Clipping](../images/mrtk-standard-shader/MRTK_PrimitiveClipping.gif)

* Weitere Informationen finden Sie unter [Clipping Primitive](clipping-primitive.md)

### <a name="mesh-outlines"></a>Gitternetzgliederungen

Viele Verfahren zur Gitternetzgliederung werden mithilfe einer [Nachbearbeitungsmethode](https://docs.unity3d.com/Manual/PostProcessingOverview.html) durchgeführt. Die Nachverarbeitung bietet hervorragende Qualität, kann aber auf vielen Mixed Reality Geräten unerzüglich teuer sein. Eine Szene, die die Verwendung von Gitternetzgliederungen veranschaulicht, finden Sie in der  **OutlineExamples-Szene** unter `MRTK/Examples/Demos/StandardShader/Scenes/` .

<img src="../images/mrtk-standard-shader/MRTK_MeshOutline.jpg" width="900" alt="Mesh Outline">

[`MeshOutline.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshOutline) und [`MeshOutlineHierarchy.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshOutlineHierarchy) können verwendet werden, um eine Kontur um einen Gitternetzrenderer zu rendern. Durch aktivieren dieser Komponente wird ein zusätzlicher Renderdurchlauf des objekts eingeführt, das konturiert wird, ist jedoch für die ausführung auf mobilen Mixed Reality Geräten konzipiert und nutzt keine Postprozesse. Einschränkungen dieses Effekts umfassen, dass er nicht gut für Objekte funktioniert, die nicht überdehnt sind (oder zweiseitig sein müssen), und Probleme bei der Tiefensortierung können bei überlappenden Objekten auftreten.

Die Konturverhalten sind so konzipiert, dass sie in Verbindung mit dem MRTK-/Standard-Shader verwendet werden. Konturmaterialien sind in der Regel eine volltonigen, unbelichteten Farbe, können jedoch so konfiguriert werden, dass sie eine vielzahl von Effekten erzielen. Die Standardkonfiguration eines Gliederungsmaterials lautet wie folgt:

<img src="../images/mrtk-standard-shader/MRTK_OutlineMaterial.jpg" width="450" alt="Mesh Outline Material">

1. Tiefenschreibvorgang: Sollte für Konturmaterialien deaktiviert werden, um sicherzustellen, dass die Kontur nicht verhindert, dass andere Objekte gerendert werden.
2. Vertexextrusion: Muss aktiviert werden, um die Kontur zu rendern.
3. Smooth Normals verwenden: Diese Einstellung ist für einige Gitternetze optional. DieExtrusion erfolgt durch Verschieben eines Scheitelpunkts entlang einer Scheitelpunktnormalität. Bei einigen Gitternetzen, die entlang der Standardnormalitäten ausgeführt werden, treten Diskontinuitäten in der Kontur auf. Um diese Diskontinuitäten zu beheben, können Sie dieses Kontrollkästchen aktivieren, um einen anderen Satz geglätteter Normalitäten zu verwenden, die von generiert werden. [`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother)

[`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother) ist eine Komponente, die verwendet werden kann, um automatisch geglättete Normalitäten in einem Gitternetz zu generieren. Diese Methode gruppiert Scheitelpunkte in einem Gitternetz, das die gleiche Position im Raum hat, und durchschnittst dann die Normalwerte dieser Scheitelpunkte. Dieser Prozess erstellt eine Kopie des zugrunde liegenden Gitternetzes und sollte nur bei Bedarf verwendet werden.

<img src="../images/mrtk-standard-shader/MRTK_SmoothNormals.jpg" width="450" alt="Smooth Normals Outline">

1. Smooth Normals, die über generiert [`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother) werden.
2. Standardnorm normal verwendet, beachten Sie die Artefakte um die Ecken des Cubes.

### <a name="stencil-testing"></a>Schablonentests

Integrierte konfigurierbare Schablonentestunterstützung, um eine Vielzahl von Effekten zu erzielen. Beispielsweise Portale:

![Schablonentest](../images/mrtk-standard-shader/MRTK_StencilTest.gif)

### <a name="instanced-color-support"></a>Instanzierte Farbunterstützung

Unterstützung von Instanzfarben, um Tausenden von gpu-instanzierten Gitternetzen eindeutige Materialeigenschaften zu geben:

![Instanzeigenschaften](../images/mrtk-standard-shader/MRTK_InstancedProperties.gif)

### <a name="triplanar-mapping"></a>Triplanare Zuordnung

Die triplanare Zuordnung ist eine Technik zum programmgesteuerten Strukturieren eines Gitternetzes. Wird häufig in Gelände, Gitternetzen ohne UVs oder schwierig zu entpackenden Formen verwendet. Diese Implementierung unterstützt die Projektion von Welt- oder lokalem Raum, die Spezifikation der Mischungsglättung und die normale Kartenunterstützung. Beachten Sie, dass jede verwendete Textur drei Texturbeispiele erfordert. Verwenden Sie daher in leistungskritischen Situationen nur selten.

![triplanar](../images/mrtk-standard-shader/MRTK_TriplanarMapping.gif)

### <a name="vertex-extrusion"></a>Vertexextrusion

Vertexextrusion im Weltraum. Nützlich zum Visualisieren von volumengebundenen Begrenzungsvolumes oder Übergängen in/ausgehenden Gitternetzen.

![normale Kartenskala 1](../images/mrtk-standard-shader/MRTK_VertexExtrusion.gif)

### <a name="miscellaneous"></a>Verschiedenes

Ein Kontrollkästchen zum Steuern von Albedo-Optimierungen. Als Optimierung werden albedo-Vorgänge deaktiviert, wenn keine Albedo-Textur angegeben wird. Dies ist nützlich, um das Laden von [Remotetexturn](http://dotnetbyexample.blogspot.com/2018/10/workaround-remote-texture-loading-does.html)zu steuern.

Aktivieren Sie einfach dieses Kontrollkästchen:

![Albedo-Zuweisung](../images/mrtk-standard-shader/MRTK_AlbedoAssignment.jpg)

Clippingtexturen pro Pixel, lokales Edge-basiertes Antialiasing und normale Kartenskalierung werden unterstützt.

![normale Kartenskala 2](../images/mrtk-standard-shader/MRTK_NormalMapScale.gif)

## <a name="see-also"></a>Siehe auch

* [Interaktionsfähig](../ux-building-blocks/interactable.md)
* [Mit dem Mauszeiger auf Licht zeigen](hover-light.md)
* [Näherungslicht](proximity-light.md)
* [Clipping Primitive](clipping-primitive.md)
