---
title: MRTK-Standard-Shader
description: Dokumentation für MRTKStandardShader
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Material Shader
ms.openlocfilehash: 0a92388bc9be7c11967501709031f559f17f8966
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176445"
---
# <a name="mrtk-standard-shader"></a>MRTK-Standard-Shader

![Beispiele für Standard-Shader](../images/mrtk-standard-shader/MRTK_StandardShader.jpg)

Das MRTK Standard-Schattierungssystem verwendet einen einzelnen, flexiblen Shader, der Visuals ähnlich dem Standard-Shader von Unity erreichen, Fluent Design System-Prinzipien implementieren und auf Mixed [Reality-Geräten](https://www.microsoft.com/design/fluent/) leistunglich bleiben kann.

## <a name="example-scenes"></a>Beispielszenen

Die Shadermaterialbeispiele finden Sie in der **MaterialGallery-Szene** unter `MRTK/Examples/Demos/StandardShader/Scenes/` . Alle Materialien in dieser Szene verwenden den MRTK/Standard-Shader.

![Material Gallery](../images/mrtk-standard-shader/MRTK_MaterialGallery.jpg)

Eine Vergleichsszene zum Vergleichen und Testen des MRTK/Standard-Shaders mit dem Unity/Standard-Shaderbeispiel finden Sie in der **StandardMaterialComparison-Szene** unter `MRTK/Examples/Demos/StandardShader/Scenes/` .

![Materialvergleich](../images/mrtk-standard-shader/MRTK_StandardMaterialComparison.gif)

## <a name="architecture"></a>Aufbau

Das MRTK/Standard-Schattierungssystem ist ein "Uber-Shader", der die [Shaderprogramm-Variante](https://docs.unity3d.com/Manual/SL-MultipleProgramVariants.html) von Unity verwendet, um automatisch optimalen Shadercode basierend auf Materialeigenschaften zu generieren. Wenn ein Benutzer Materialeigenschaften im Materialinspektor auswählt, entstehen nur Leistungskosten für aktivierte Features.

## <a name="material-inspector"></a>Materialinspektor

Für den MRTK-/Standard-Shader mit dem Namen ist ein benutzerdefinierter Materialinspektor [`MixedRealityStandardShaderGUI.cs`](xref:Microsoft.MixedReality.Toolkit.Editor.MixedRealityStandardShaderGUI) vorhanden. Der Inspektor aktiviert/deaktiviert automatisch Shaderfeatures, basierend auf der Benutzerauswahl und gestützte Unterstützung beim Einrichten des Renderzustands. Um weitere Informationen zu den einzelnen Features zu erhalten, zeigen Sie im Unity-Editor auf jede **Eigenschaft, um eine QuickInfo zu erhalten.**

![Material Inspector](../images/mrtk-standard-shader/MRTK_MaterialInspector.jpg)

Der erste Teil des Inspektors steuert den Renderzustand des Materials. *Der Renderingmodus* bestimmt, wann und wie ein Material gerendert wird. Das Ziel des MRTK/Standard-Shaders ist es, die Renderingmodi im [Unity/Standard-Shader zu spiegeln.](https://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html) Der MRTK/Standard-Shader enthält auch einen *additiven Renderingmodus* und einen *benutzerdefinierten* Renderingmodus für die vollständige Benutzersteuerung.

| Renderingmodus |         Beschreibung                                                       |
|----------------|---------------------------------------------------------------------------|
| Nicht transparent         | (Standard) Geeignet für normale Vollwertobjekte ohne transparente Bereiche.    |
| Ausschnitt         | Ermöglicht die Erstellung von transparenten Effekten, die harte Kanten zwischen den nicht transparenten und transparenten Bereichen haben. In diesem Modus gibt es keine halbtransparenten Bereiche, die Textur ist entweder zu 100 % deckend oder unsichtbar. Dies ist nützlich, wenn Transparenz verwendet wird, um die Form von Materialien zu erstellen, z. B. Einess. |
| Einblenden           | Ermöglicht es den Transparenzwerten, ein Objekt vollständig ausblenden, einschließlich aller glanzlichen Highlights oder Reflexionen, die es haben kann. Dieser Modus ist nützlich, wenn Sie ein Objekt animieren möchten, das ein- oder ausfing. Sie eignet sich nicht für das Rendern realistischer transparenter Materialien wie klares Licht oder Wasserglas, da die Reflexionen und Highlights ebenfalls ausgeblendet werden. |
| Transparent    | Geeignet zum Rendern realistischer transparenter Materialien, z. B. klares Wasser oder Glass. In diesem Modus nimmt das Material selbst Transparenzwerte an (basierend auf dem Alphakanal der Textur und dem Alpha des Farbtons). Reflektionen und Beleuchtungslichter bleiben jedoch bei voller Klarheit sichtbar, wie dies bei echten transparenten Materialien der Fall ist. |
| Additiv       | Aktiviert einen additiven Überblendungsmodus, der die vorherige Pixelfarbe mit der aktuellen Pixelfarbe addiert. Dies ist der bevorzugte Transparenzmodus, um Probleme bei der Transparenzsortierung zu vermeiden.     |
| Benutzerdefiniert         | Ermöglicht die manuelle Kontrolle aller Aspekte des Renderingmodus. Nur für die erweiterte Verwendung.   |

![Renderingmodi](../images/mrtk-standard-shader/MRTK_RenderingModes.jpg)

| Cull-Modus |             Beschreibung                                                                                                                                                                       |
|-----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Aus       | Deaktiviert die Gesichtserkennung. Culling sollte nur auf Off festgelegt werden, wenn ein zweiseitiges Gitter erforderlich ist.                                                                                        |
| Front     | Ermöglicht das Culling der Vorderseite.                                                                                                                                                        |
| Zurück      | (Standard) Ermöglicht das [Zurück-Gesichts-Culling.](https://en.wikipedia.org/wiki/Back-face_culling) Back Face culling sollte so oft wie möglich aktiviert werden, um die Renderingleistung zu verbessern. |

## <a name="performance"></a>Leistung

Einer der Hauptvorteile bei der Verwendung des MRTK Standard-Shaders gegenüber dem Unity-Standard-Shader ist die Leistung. Der MRTK-Standard-Shader ist erweiterbar, um nur die aktivierten Features zu nutzen. Der MRTK Standard-Shader wurde jedoch auch geschrieben, um vergleichbare ergebnisse zu liefern wie der Unity Standard-Shader, aber zu viel geringeren Kosten. Eine einfache Möglichkeit zum Vergleichen der Shaderleistung ist die Anzahl der Vorgänge, die auf der GPU ausgeführt werden müssen. Natürlich kann das Ausmaß der Berechnungen nach aktivierten Features und anderen Renderingkonfigurationen schwanken. Im Allgemeinen führt der MRTK Standard-Shader jedoch deutlich weniger Berechnungen durch als der Unity Standard-Shader.

Unity Standard-Shader-Statistikbeispiel

![Unity-Standard-Shaderstatistik](../images/performance/UnityStandardShader-Stats.PNG)

MrTK Standard-Shaderstatistikbeispiel

![MRTK-Standard-Shaderstatistik](../images/performance/MRTKStandardShader-Stats.PNG)

> [!NOTE]
> Diese Ergebnisse können generiert werden, indem Sie ein [Shader-Objekt](https://docs.unity3d.com/Manual/class-Shader.html) im Unity-Inspektor auswählen und anzeigen und dann auf die Schaltfläche Kompilieren und *Code anzeigen* klicken.

## <a name="lighting"></a>Beleuchtung

Das MRTK/Standard verwendet eine einfache Näherung für die Beleuchtung. Da dieser Shader nicht auf physische Korrektheit und Energieversorgung berechnet, wird er schnell und effizient gerendert. Blinn-Phong ist die primäre Beleuchtungstechnik, die mit Fresnel und bildbasierter Beleuchtung kombiniert wird, um eine ungefähre physische Beleuchtung zu erstellen. Der Shader unterstützt die folgenden Beleuchtungstechniken:

### <a name="directional-light"></a>Gerichtetes Licht

Der Shader beachtet die Richtung, Farbe und Intensität des ersten direktionalen Unity-Lichts in der Szene (sofern aktiviert). Dynamische Punktlichter, Spot-Licht oder ein anderes Unity-Licht werden bei der Echtzeitbeleuchtung nicht berücksichtigt.

### <a name="spherical-harmonics"></a>Pherical-Trophäen

Der Shader verwendet Lichtsonden, um Licht in der Szene mithilfe von [pherischen](https://docs.unity3d.com/Manual/LightProbes-TechnicalInformation.html)Glühbirnen zu ungefähren, sofern aktiviert. Pherical-Berechnungen werden pro Scheitelpunkt ausgeführt, um die Berechnungskosten zu reduzieren.

### <a name="lightmapping"></a>Lightmapping

Bei statischer Beleuchtung beachtet der Shader Lightmaps, die vom [Lightmapping-System](https://docs.unity3d.com/Manual/Lightmapping.html)von Unity erstellt wurden. Markieren Sie den Renderer einfach als statisch (oder lightmap static), um Lightmaps zu verwenden.

### <a name="hover-light"></a>Licht mit Der Hover

* Siehe [Hover Light](hover-light.md)

### <a name="proximity-light"></a>Näherungslicht

* Siehe [Näherungslicht](proximity-light.md)

## <a name="lightweight-scriptable-render-pipeline-support"></a>Lightweight-Unterstützung für skriptfähige Renderpipeline

Das MRTK enthält einen Upgradepfad, mit dem Entwickler die Lightweight Scriptable Render Pipeline (LWRP) von Unity mit MRTK-Shadern verwenden können. Getestet im Unity 2019.1.1f1- und Lightweight RP 5.7.2-Paket. Anweisungen zu den ersten Schritte mit LWRP finden Sie [auf dieser Seite.](https://docs.unity3d.com/Packages/com.unity.render-pipelines.lightweight@5.10/manual/getting-started-with-lwrp.html)

Um das MRTK-Upgrade durchzuführen, wählen Sie Mixed Reality **Toolkit -> Utilities -> Upgrade MRTK Standard Shader for Lightweight Render Pipeline (MRTK-Standard-Shader für lightweight Renderpipeline aktualisieren) aus.**

![lwrp-Upgrade](../images/mrtk-standard-shader/MRTK_LWRPUpgrade.jpg)

Nach dem Upgrade wird der MRTK-/Standard-Shader geändert, und alle Magentamaterialien (Shaderfehler) sollten behoben werden. Um zu überprüfen, ob das Upgrade erfolgreich durchgeführt wurde, überprüfen Sie die Konsole auf: **Aktualisierte Objekte/MixedRealityToolkit/StandardAssets/Shaders/MixedRealityStandard.shader** für die Verwendung mit der Lightweight-Renderpipeline.

## <a name="ugui-support"></a>UGUI-Unterstützung

Das MRTK Standard-Schattierungssystem funktioniert mit [](https://docs.unity3d.com/Manual/UISystem.html)dem integrierten Benutzeroberflächensystem von Unity. Bei Unity-Benutzeroberflächenkomponenten ist unity_ObjectToWorld Matrix nicht die Transformationsmatrix der lokalen Transformation, auf der sich die Grafikkomponente befindet, sondern die des übergeordneten Zeichenbereichs. Viele MRTK-/Standard-Shadereffekte erfordern, dass die Objektskala bekannt ist. Um dieses Problem zu beheben, werden die Skalierungsinformationen während der Konstruktion des [`ScaleMeshEffect.cs`](xref:Microsoft.MixedReality.Toolkit.Input.Utilities.ScaleMeshEffect) Benutzeroberflächengitters in UV-Kanalattributen gespeichert.

Beachten Sie, dass bei Verwendung einer Unity-Imagekomponente empfohlen wird, "None (Sprite)" für das Quellbild anzugeben, um zu verhindern, dass die Unity-Benutzeroberfläche zusätzliche Scheitelelemente generiert.

Ein Zeichenbereich innerhalb des MRTK fordert sie auf, ein -Zeichen hinzu zu [`ScaleMeshEffect.cs`](xref:Microsoft.MixedReality.Toolkit.Input.Utilities.ScaleMeshEffect) erhalten, wenn eine erforderlich ist:

![Skalierungsgittereffekt](../images/mrtk-standard-shader/MRTK_ScaleMeshEffect.jpg)

## <a name="texture-combiner"></a>Textur-Combiner

Um die Parität mit dem Unity Standard-Shader pro Pixelpixel zu verbessern, können die Werte für Glätte, Glätte und Okklusion alle über kanalgesteuertes Packen [gesteuert werden.](http://wiki.polycount.com/wiki/ChannelPacking) Beispiel:

![Kanalzuordnungsbeispiel](../images/mrtk-standard-shader/MRTK_ChannelMap.gif)

Wenn Sie die Kanalpackung verwenden, müssen Sie nur eine Textur abtast und in den Arbeitsspeicher laden, anstatt vier separate Texturen zu verwenden. Wenn Sie Ihre Texturzuordnungen in einem Programm wie "100000" oder "Antivirus" schreiben, können Sie sie wie folgt handpacken:

| Kanal | Eigenschaft             |
|---------|----------------------|
| Red     | Metallischen             |
| Grün   | Okklusion            |
| Blau    | Mission (Graustufen) |
| Alpha   | Glätte           |

Sie können auch das MRTK-Textur-Combiner-Tool verwenden. Um das Tool zu öffnen, wählen Sie: **Mixed Reality Toolkit -> Utilities -> Texture Combiner** aus, wodurch das folgende Fenster geöffnet wird:

![Beispiel für Textur-Combiner](../images/mrtk-standard-shader/MRTK_TextureCombiner.jpg)

Dieses Fenster kann automatisch ausgefüllt werden, indem Sie einen Unity Standard-Shader auswählen und auf "Aus Standardmaterial automatisch auffüllen" klicken. Sie können auch manuell eine Textur (oder einen konstanten Wert) pro Rot-, Grün-, Blau- oder Alphakanal angeben. Die Texturkombination wird durch GPU beschleunigt und erfordert keinen CPU-Zugriff auf die Eingabetextur.

## <a name="additional-feature-documentation"></a>Zusätzliche Featuredokumentation

Im Folgenden finden Sie zusätzliche Details zu einer Reihe von Featuredetails, die mit dem MRTK/Standard-Shader verfügbar sind.

### <a name="primitive-clipping"></a>Primitives Clipping

![Primitives Clipping](../images/mrtk-standard-shader/MRTK_PrimitiveClipping.gif)

* Weitere Informationen finden [Sie unter Clipping Primitive](clipping-primitive.md)

### <a name="mesh-outlines"></a>Gitternetzgliederungen

Viele Gitternetzgliederungstechniken werden mithilfe einer [Nachbearbeitungstechnik](https://docs.unity3d.com/Manual/PostProcessingOverview.html) durchgeführt. Die Nachbearbeitung bietet qualitativ hochwertige Gliederungen, kann aber auf vielen Geräten mit hohen kostenintensiven Mixed Reality werden. Eine Szene, die die Verwendung von Gitternetzgliederungen veranschaulicht, finden Sie in der  **OutlineExamples-Szene** unter `MRTK/Examples/Demos/StandardShader/Scenes/` .

<img src="../images/mrtk-standard-shader/MRTK_MeshOutline.jpg" width="900" alt="Mesh Outline">

[`MeshOutline.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshOutline) und [`MeshOutlineHierarchy.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshOutlineHierarchy) können verwendet werden, um eine Kontur um einen Gitternetzrenderer zu rendern. Wenn Sie diese Komponente aktivieren, wird ein zusätzlicher Renderlauf des objekts, das umrissen wird, ermöglicht jedoch eine performante Ausführung auf mobilen Mixed Reality-Geräten und verwendet keine Postprozesse. Zu den Einschränkungen dieses Effekts gehört, dass er nicht gut für Objekte funktioniert, die nicht wasserdicht sind (oder zweiseitig sein müssen), und Probleme bei der Tiefensortierung können bei überlappenden Objekten auftreten.

Die Konturverhaltensverhalten sind für die Verwendung in Verbindung mit dem MRTK/Standard-Shader konzipiert. Konturmaterialien sind in der Regel eine volltonlose Farbe, können aber so konfiguriert werden, dass sie eine Vielzahl von Effekten erzielen. Die Standardkonfiguration eines Gliederungsmaterials lautet wie folgt:

<img src="../images/mrtk-standard-shader/MRTK_OutlineMaterial.jpg" width="450" alt="Mesh Outline Material">

1. Tiefenschreiben: Sollte für Konturmaterialien deaktiviert werden, um sicherzustellen, dass die Kontur nicht verhindert, dass andere Objekte gerendert werden.
2. Vertexextrusion: Muss aktiviert werden, um die Kontur zu rendern.
3. Smooth Normals verwenden: Diese Einstellung ist für einige Gitternetze optional. DieExtrusion erfolgt, indem ein Scheitelpunkt entlang einer Scheitelpunktnorm normal bewegt wird. Bei einigen Gittern, die sich entlang der Standardnormleerungen bewegen, kommt es zu Diskontinuitäten in der Kontur. Um diese Diskontinuitäten zu beheben, können Sie dieses Kontrollkästchen aktivieren, um einen weiteren Satz geglätteter Normal normaler Zu verwenden, die von generiert werden. [`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother)

[`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother) ist eine Komponente, die verwendet werden kann, um automatisch geglättete Normal normaler Daten in einem Gitternetz zu generieren. Diese Methode gruppen Scheitelräume in einem Gitternetz, die dieselbe Position im Raum gemeinsam haben, und durchschnittlicht dann die Normalwerte dieser Scheitelungen. Dieser Prozess erstellt eine Kopie des zugrunde liegenden Gitters und sollte nur bei Bedarf verwendet werden.

<img src="../images/mrtk-standard-shader/MRTK_SmoothNormals.jpg" width="450" alt="Smooth Normals Outline">

1. Smooth Normals, die über generiert [`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother) werden.
2. Verwendete Standardnorm normals. Beachten Sie die Artefakte um die Würfelecken.

### <a name="stencil-testing"></a>Schablonentests

Integrierte konfigurierbare Unterstützung für Schablonentests, um eine Vielzahl von Effekten zu erzielen. z. B. Portale:

![Schablonentest](../images/mrtk-standard-shader/MRTK_StencilTest.gif)

### <a name="instanced-color-support"></a>Unterstützung für Instanzfarben

Unterstützung von Instanzfarben, um Tausenden von GPU-Instanzgittern eindeutige Materialeigenschaften zu geben:

![Instanzeigenschaften](../images/mrtk-standard-shader/MRTK_InstancedProperties.gif)

### <a name="triplanar-mapping"></a>Triplanare Zuordnung

Die triplanare Zuordnung ist eine Technik zum programmgesteuerten Texturieren eines Gitters. Wird häufig in Gelände, Gittermodell ohne UVs oder schwierig zu entpackende Formen verwendet. Diese Implementierung unterstützt die Welt- oder Lokale Raumprojektion, die Spezifikation der Mischungsglättung und die Normale Kartenunterstützung. Beachten Sie, dass jede verwendete Textur drei Texturbeispiele erfordert. Verwenden Sie daher in leistungskritischen Situationen nur wenig.

![triplanar](../images/mrtk-standard-shader/MRTK_TriplanarMapping.gif)

### <a name="vertex-extrusion"></a>Vertexextrusion

Vertexextrusion im Weltraum. Nützlich zum Visualisieren von verleerten Begrenzungsvolumes oder Übergängen in/aus Gittern.

![Normale Kartenskala 1](../images/mrtk-standard-shader/MRTK_VertexExtrusion.gif)

### <a name="miscellaneous"></a>Sonstiges

Ein Kontrollkästchen zum Steuern von Albedo-Optimierungen. Als Optimierung werden Albedo-Vorgänge deaktiviert, wenn keine Albedo-Textur angegeben ist. Dies ist nützlich, um das Laden [von Remotetextur zu steuern.](http://dotnetbyexample.blogspot.com/2018/10/workaround-remote-texture-loading-does.html)

Aktivieren Sie einfach dieses Kontrollkästchen:

![Albedo-Zuweisung](../images/mrtk-standard-shader/MRTK_AlbedoAssignment.jpg)

Clippingtexturen pro Pixel, lokale Edge-basierte Antialiasing und normale Kartenskalierung werden unterstützt.

![Normale Kartenskala 2](../images/mrtk-standard-shader/MRTK_NormalMapScale.gif)

## <a name="see-also"></a>Siehe auch

* [Interaktionsfähig](../ux-building-blocks/interactable.md)
* [Schwebelicht](hover-light.md)
* [Näherungslicht](proximity-light.md)
* [Zuschnitt-Primitiv](clipping-primitive.md)
