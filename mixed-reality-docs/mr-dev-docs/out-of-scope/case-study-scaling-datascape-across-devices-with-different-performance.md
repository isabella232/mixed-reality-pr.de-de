---
title: 'Fallstudie: Skalieren von Datascape auf verschiedenen Geräten mit unterschiedlicher Leistung'
description: Diese Fallstudie bietet Einblicke in die Optimierung der Datascape-App durch Microsoft-Entwickler, um eine überzeugende Benutzererfahrung auf verschiedenen Geräten mit einer Reihe von Leistungsfunktionen zu bieten.
author: danandersson
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Immersives Headset, Leistungsoptimierung, VR, Fallstudie
ms.openlocfilehash: d1c54f5fbe6843f9bf61af20b611c6aeb22b0704c209bfdb555fe57b95805cf9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115195759"
---
# <a name="case-study---scaling-datascape-across-devices-with-different-performance"></a>Fallstudie: Skalieren von Datascape auf verschiedenen Geräten mit unterschiedlicher Leistung

Datascape ist eine Windows Mixed Reality anwendung, die intern bei Microsoft entwickelt wurde und bei der wir uns auf die Anzeige von Wetterdaten über Geländedaten konzentriert haben. Die Anwendung untersucht die einzigartigen Erkenntnisse, die Benutzer durch das Entdecken von Daten in Mixed Reality gewinnen, indem sie den Benutzer mit holografischer Datenvisualisierung umhing.

Für Datascape wollten wir eine Vielzahl von Plattformen mit unterschiedlichen Hardwarefunktionen als Ziel verwenden– von Microsoft HoloLens bis Windows Mixed Reality immersive Headsets und von PCs mit geringerer Leistung bis hin zu den neuesten PCs mit High-End-GPU. Die größte Herausforderung bestand darin, unsere Szene visuell ansprechender auf Geräten mit stark unterschiedlichen Grafikfunktionen zu rendern, während sie mit hoher Framerate ausgeführt wurde.

In dieser Fallstudie werden der Prozess und die Techniken beschrieben, mit denen einige unserer GPU-intensiven Systeme erstellt werden. Sie beschreibt die aufgetretenen Probleme und deren Behebung.

## <a name="transparency-and-overdraw"></a>Transparenz und Überzeichnung

Unser Hauptrendering hat Probleme mit Transparenz, da Transparenz auf einer GPU teuer sein kann.

Die Vollformatgeometrie kann beim Schreiben in den Tiefenpuffer von vorn nach hinten gerendert werden, um zu verhindern, dass alle zukünftigen Pixel hinter diesem Pixel verworfen werden. Dadurch wird verhindert, dass ausgeblendete Pixel den Pixel-Shader ausführen, was den Prozess erheblich beschleunigt. Wenn die Geometrie optimal sortiert ist, wird jedes Pixel auf dem Bildschirm nur einmal gezeichnet.

Die transparente Geometrie muss nach vorne sortiert werden und basiert darauf, dass die Ausgabe des Pixels shaders mit dem aktuellen Pixel auf dem Bildschirm kombiniert wird. Dies kann dazu führen, dass jedes Pixel auf dem Bildschirm mehrmals pro Frame gezeichnet wird, was als Überzeichnung bezeichnet wird.

Für HoloLens- und Standard-PCs kann der Bildschirm nur einige Male gefüllt werden, was das transparente Rendering problematisch macht.

## <a name="introduction-to-datascape-scene-components"></a>Einführung in Datascape-Szenenkomponenten

Wir hatten drei Hauptkomponenten für unsere Szene: **die Benutzeroberfläche, die Karte** und **das Wetter**. Wir wussten schon früh, dass unsere Wettereffekte die ganze GPU-Zeit erfordern würden, die sie erhalten konnte. Daher haben wir die Benutzeroberfläche und das Gelände so entworfen, dass jede Überzeichnung reduziert wird.

Wir haben die Benutzeroberfläche mehrmals überarbeitet, um die Menge der zu erzeugenden Überzeichnung zu minimieren. Wir haben uns auf der Seite einer komplexeren Geometrie geerbt, anstatt transparente Artefakte für Komponenten wie leuchtende Schaltflächen und Kartenübersichten übereinander zu überlagern.

Für die Karte haben wir einen benutzerdefinierten Shader verwendet, der Unity-Standardfeatures wie Schatten und komplexe Beleuchtung entfernt und durch ein einfaches einzelnes Sonnenlichtmodell und eine benutzerdefinierte Berechnung ersetzt. Dies erzeugte einen einfachen Pixel-Shader und gibt GPU-Zyklen frei.

Wir haben sowohl die Benutzeroberfläche als auch die Karte für das Rendering im Budget erhalten, bei dem je nach Hardware keine Änderungen an ihnen erforderlich waren. die Wettervisualisierung, insbesondere das Cloudrendering, hat sich jedoch als eher eine Herausforderung erwiesen!

## <a name="background-on-cloud-data"></a>Hintergrund zu Clouddaten

Unsere Clouddaten wurden von NOAA-Servern heruntergeladen ( und sind in drei unterschiedlichen 2D-Ebenen zu uns gekommen, die jeweils die obere und untere Höhe der Cloud sowie die Dichte der Cloud für jede Zelle des Rasters https://nomads.ncep.noaa.gov/) aufweisen. Die Daten wurden in eine Cloudinformationstextur verarbeitet, in der jede Komponente in der roten, grünen und blauen Komponente der Textur gespeichert wurde, um den Zugriff auf die GPU zu ermöglichen.

## <a name="geometry-clouds"></a>Geometriewolken

Um sicherzustellen, dass unsere weniger betriebenen Computer unsere Clouds rendern können, haben wir uns entschieden, mit einem Ansatz zu beginnen, bei dem eine solide Geometrie verwendet wird, um die Überzeichnung zu minimieren.

Wir haben zuerst versucht, Clouds zu erzeugen, indem wir ein solides Höhenbildgitter für jede Ebene mithilfe des Radius der Cloudinformationstextur pro Scheitelpunkt generieren, um die Form zu generieren. Wir haben einen Geometrie-Shader verwendet, um die Scheitelpunkts am oberen und unteren Rand der Cloud zu erzeugen, die solide Cloudformen generieren. Wir haben den Dichtewert aus der Textur verwendet, um die Wolke mit dunkleren Farben für dichtere Clouds zu färben.

**Shader zum Erstellen der Scheitelungen:**

```
v2g vert (appdata v)
{
    v2g o;
    o.height = tex2Dlod(_MainTex, float4(v.uv, 0, 0)).x;
    o.vertex = v.vertex;
    return o;
}
 
g2f GetOutput(v2g input, float heightDirection)
{
    g2f ret;
    float4 newBaseVert = input.vertex;
    newBaseVert.y += input.height * heightDirection * _HeigthScale;
    ret.vertex = UnityObjectToClipPos(newBaseVert);
    ret.height = input.height;
    return ret;
}
 
[maxvertexcount(6)]
void geo(triangle v2g p[3], inout TriangleStream<g2f> triStream)
{
    float heightTotal = p[0].height + p[1].height + p[2].height;
    if (heightTotal > 0)
    {
        triStream.Append(GetOutput(p[0], 1));
        triStream.Append(GetOutput(p[1], 1));
        triStream.Append(GetOutput(p[2], 1));
 
        triStream.RestartStrip();
 
        triStream.Append(GetOutput(p[2], -1));
        triStream.Append(GetOutput(p[1], -1));
        triStream.Append(GetOutput(p[0], -1));
    }
}
fixed4 frag (g2f i) : SV_Target
{
    clip(i.height - 0.1f);
 
    float3 finalColor = lerp(_LowColor, _HighColor, i.height);
    return float4(finalColor, 1);
}
```

Wir haben ein kleines Rauschmuster eingeführt, um mehr Details zu den tatsächlichen Daten zu erhalten. Um runde Cloudränder zu erzeugen, haben wir die Pixel im Pixel-Shader abgeschnitten, wenn der interpolierte Radiuswert einen Schwellenwert erreicht hat, um Werte nahezu null zu verwerfen.

![Geometriewolken](images/datascape-geometry-clouds-700px.jpg)

Da es sich bei den Clouds um eine solide Geometrie handelt, können sie vor dem Gelände gerendert werden, um darunter teure Kartenpixel auszublenden, um die Bildrate weiter zu verbessern. Diese Lösung funktionierte gut auf allen Grafikkarten von min-spec bis high-end-Grafikkarten sowie auf HoloLens aufgrund des Solid Geometry Rendering-Ansatzes.

## <a name="solid-particle-clouds"></a>Volumenteilchenwolken

Wir hatten jetzt eine Sicherungslösung, die eine gute Darstellung unserer Clouddaten erzeugte, aber im Wow-Faktor etwas fehlte und nicht das volumetrischen Gefühl vermittelte, das wir für unsere High-End-Computer wollten.

Unser nächster Schritt war das Erstellen der Clouds, indem wir sie mit ungefähr 100.000 Partikeln darstellen, um ein eher bio- und volumetrischen Aussehen zu erzeugen.

Wenn Partikel fest bleiben und von vorne nach hinten sortiert werden, können wir dennoch von der Tiefenpuffer-Culling der Pixel hinter den zuvor gerenderten Partikeln profitieren, was die Überzeichnung reduziert. Außerdem können wir mit einer partikelbasierten Lösung die Menge der Partikel ändern, die für unterschiedliche Hardware verwendet werden. Allerdings müssen weiterhin alle Pixel ausführlich getestet werden, was zu zusätzlichem Mehraufwand führt.

Zuerst haben wir Partikelpositionen um den Mittelpunkt der Erfahrung beim Start erstellt. Wir verteilten die Partikel dichter um den Mittelpunkt und weniger in der Entfernung. Wir haben alle Partikel von der Mitte nach der Rückseite vorab sortiert, sodass die nächstgelegenen Partikel zuerst gerendert werden.

Ein Compute-Shader würde die Cloudinformationstextur abtasten, um jeden Partikel in einer richtigen Höhe zu positionieren und basierend auf der Dichte zu färben.

Wir haben *DrawProcedural verwendet,* um ein Quad pro Partikel zu rendern, sodass die Partikeldaten jederzeit auf der GPU bleiben können.

Jeder Partikel enthielt sowohl eine Höhe als auch einen Radius. Die Höhe basierte auf den Clouddaten, die aus der Cloudinformationstextur entnommen wurden, und der Radius basierte auf der anfänglichen Verteilung, bei der berechnet wurde, um die horizontale Entfernung zum nächsten Nachbarn zu speichern. Die Quads verwenden diese Daten, um sich nach der Höhe zu orientieren, sodass die Höhe angezeigt wird, wenn Benutzer sie horizontal betrachten, und wenn Benutzer sie von oben nach unten betrachten, wird der Bereich zwischen den Nachbarn abgedeckt.

![Partikelform](images/particle-shape-700px.png)

**Shadercode mit der Verteilung:**

```
ComputeBuffer cloudPointBuffer = new ComputeBuffer(6, quadPointsStride);
cloudPointBuffer.SetData(new[]
{
    new Vector2(-.5f, .5f),
    new Vector2(.5f, .5f),
    new Vector2(.5f, -.5f),
    new Vector2(.5f, -.5f),
    new Vector2(-.5f, -.5f),
    new Vector2(-.5f, .5f)
});
 
StructuredBuffer<float2> quadPoints;
StructuredBuffer<float3> particlePositions;
v2f vert(uint id : SV_VertexID, uint inst : SV_InstanceID)
{
    // Find the center of the quad, from local to world space
    float4 centerPoint = mul(unity_ObjectToWorld, float4(particlePositions[inst], 1));
 
    // Calculate y offset for each quad point
    float3 cameraForward = normalize(centerPoint - _WorldSpaceCameraPos);
    float y = dot(quadPoints[id].xy, cameraForward.xz);
 
    // Read out the particle data
    float radius = ...;
    float height = ...;
 
    // Set the position of the vert
    float4 finalPos = centerPoint + float4(quadPoints[id].x, y * height, quadPoints[id].y, 0) * radius;
    o.pos = mul(UNITY_MATRIX_VP, float4(finalPos.xyz, 1));
    o.uv = quadPoints[id].xy + 0.5;
 
    return o;
}
```

Da wir die Partikel front-to-back sortieren und trotzdem einen Solid-Style-Shader verwendet haben, um transparente Pixel zu beschneiden (nicht zu überblenden), verarbeitet diese Technik eine überraschende Menge an Partikeln und vermeidet auch auf den weniger betriebenen Computern teures Überladen.

## <a name="transparent-particle-clouds"></a>Transparente Partikelwolken

Die festen Partikel sorgten für ein gutes Bio-Gefühl für die Form der Clouds, benötigten aber trotzdem etwas, um die Flaffiness der Clouds zu verkaufen. Wir haben uns entschieden, eine benutzerdefinierte Lösung für die High-End-Grafikkarten auszuprobieren, in der wir Transparenz einführen können.

Dazu haben wir einfach die anfängliche Sortierreihenfolge der Partikel geändert und den Shader so geändert, dass der Textur alpha verwendet wird.

![Flaffy Clouds](images/fluffy-clouds-700px.jpg)

Es sieht gut aus, hat sich aber als zu stark für selbst die schwierigsten Computer erwiesen, da dies dazu führen würde, dass jedes Pixel auf dem Bildschirm hunderte Male gerendert würde!

## <a name="render-off-screen-with-lower-resolution"></a>Rendern aus dem Bildschirm mit niedrigerer Auflösung

Um die Anzahl der von den Clouds gerenderten Pixel zu reduzieren, haben wir damit begonnen, sie in einem Puffer mit Quartalsauflösung (im Vergleich zum Bildschirm) zu rendern und das Endergebnis wieder auf den Bildschirm zu strecken, nachdem alle Partikel gezeichnet wurden. Dies hat uns ungefähr eine vier fache Beschleunigung ermöglicht, aber es gab einige Einschränkungen.

**Code für das Rendern aus dem Bildschirm:**

```
cloudBlendingCommand = new CommandBuffer();
Camera.main.AddCommandBuffer(whenToComposite, cloudBlendingCommand);
 
cloudCamera.CopyFrom(Camera.main);
cloudCamera.rect = new Rect(0, 0, 1, 1);    //Adaptive rendering can set the main camera to a smaller rect
cloudCamera.clearFlags = CameraClearFlags.Color;
cloudCamera.backgroundColor = new Color(0, 0, 0, 1);
 
currentCloudTexture = RenderTexture.GetTemporary(Camera.main.pixelWidth / 2, Camera.main.pixelHeight / 2, 0);
cloudCamera.targetTexture = currentCloudTexture;
 
// Render clouds to the offscreen buffer
cloudCamera.Render();
cloudCamera.targetTexture = null;
 
// Blend low-res clouds to the main target
cloudBlendingCommand.Blit(currentCloudTexture, new RenderTargetIdentifier(BuiltinRenderTextureType.CurrentActive), blitMaterial);
```

Erstens haben wir beim Rendern in einen Off-Screen-Puffer alle Tiefeninformationen aus unserer Hauptszene verloren, was zu Partikeln hinter dem Rendern von Tafeln auf dem Gebirg führt.

Zweitens führte das Strecken des Puffers auch zu Artefakten an den Rändern unserer Clouds, wo die Auflösungsänderung spürbar war. In den nächsten beiden Abschnitten wird erläutert, wie wir diese Probleme gelöst haben.

## <a name="particle-depth-buffer"></a>Partikeltiefenpuffer

Damit die Partikel zusammen mit der Geometrie der Welt vorhanden sind, in der ein Bzw. ein Objekt Partikel hinter sich bedecken könnte, haben wir den Off-Screen-Puffer mit einem Tiefenpuffer aufgefüllt, der die Geometrie der Hauptszene enthält. Um einen solchen Tiefenpuffer zu erzeugen, haben wir eine zweite Kamera erstellt, die nur die Vollbildgeometrie und -tiefe der Szene rendert.

Anschließend haben wir die neue Textur im Pixel-Shader der Clouds verwendet, um Pixel zu verdecken. Wir haben dieselbe Textur verwendet, um den Abstand zur Geometrie hinter einem Cloudpixel zu berechnen. Indem wir diese Entfernung verwendet und auf das Alpha des Pixels anwenden, haben wir nun den Effekt, dass Die Clouds ausfingen, wenn sie dem Gelände nahe kommen, und alle harte Schnitte entfernt, wo Partikel und Gelände zusammentreffen.

![Clouds blended into gelände](images/clouds-blended-to-terrain-700px.jpg)

## <a name="sharpening-the-edges"></a>Schärfen der Ränder

Die gestreckten Clouds wirkten fast identisch mit den normalen Größenwolken in der Mitte der Partikel oder wo sie sich überlappen, zeigten jedoch einige Artefakte an den Cloudrändern. Andernfalls wirkten spitze Ränder unscharf, und Aliaseffekte wurden eingeführt, wenn die Kamera bewegt wurde.

Wir haben dies gelöst, indem wir einen einfachen Shader auf dem Off-Screen-Puffer ausgeführt haben, um zu bestimmen, wo große Änderungen im Kontrast aufgetreten sind (1). Wir setzen die Pixel mit großen Änderungen in einen neuen Schablonenpuffer (2). Anschließend haben wir den Schablonenpuffer verwendet, um diese Bereiche mit hohem Kontrast zu maskieren, wenn der Off-Screen-Puffer wieder auf den Bildschirm angewendet wird, was zu Lücken in und um die Clouds führt (3).

Anschließend haben wir alle Partikel erneut im Vollbildmodus gerendert, aber dieses Mal wurde der Schablonenpuffer verwendet, um alles außer den Kanten zu maskieren, was zu einem minimalen Satz von berührten Pixeln (4) führt. Da der Befehlspuffer bereits für die Partikel erstellt wurde, musste er einfach wieder für die neue Kamera gerendert werden.

![Fortschritt des Renderings von Cloudrändern](images/cloud-steps-1-4-700px.jpg)

Das Endergebnis waren spitze Kanten mit kostengünstigen zentriert Abschnitten der Clouds.

Dies war zwar viel schneller als das Rendern aller Partikel im Vollbildmodus, aber es entstehen immer noch Kosten für das Testen eines Pixels mit dem Schablonenpuffer, sodass eine große Menge an Überzeichnung immer noch mit Kosten verbunden war.

## <a name="culling-particles"></a>Cullingteilchen

Für unseren Windeffekt haben wir lange Dreiecksstreifen in einem Compute-Shader generiert, wodurch viele Wisps von Wind auf der Welt erzeugt wurden. Obwohl der Windeffekt aufgrund der generierten Skinny Strips nicht stark auf die Füllrate antraten, erzeugte er viele Hunderttausend Scheitelpunkte, was zu einer hohen Last für den Vertex-Shader führt.

Wir haben Anfügepuffer für den Compute-Shader eingeführt, um eine Teilmenge der zu ziehenden Windstreifen zu befeeden. Mit einer einfachen Logik zur Frustum-Cullingansicht im Compute-Shader könnten wir ermitteln, ob sich ein Strip außerhalb der Kameraansicht befängt, und verhindern, dass er dem Pushpuffer hinzugefügt wird. Dadurch wurde die Anzahl der Strips erheblich reduziert, was einige benötigte Zyklen auf der GPU freit.

**Code, der einen Anfügepuffer zeigt:**

*Compute-Shader:*

```
AppendStructuredBuffer<int> culledParticleIdx;
 
if (show)
    culledParticleIdx.Append(id.x);
```

*C#-Code:*

```
protected void Awake() 
{
    // Create an append buffer, setting the maximum size and the contents stride length
    culledParticlesIdxBuffer = new ComputeBuffer(ParticleCount, sizeof(int), ComputeBufferType.Append);
 
    // Set up Args Buffer for Draw Procedural Indirect
    argsBuffer = new ComputeBuffer(4, sizeof(int), ComputeBufferType.IndirectArguments);
    argsBuffer.SetData(new int[] { DataVertCount, 0, 0, 0 });
}
 
protected void Update()
{
    // Reset the append buffer, and dispatch the compute shader normally
    culledParticlesIdxBuffer.SetCounterValue(0);
 
    computer.Dispatch(...)
 
    // Copy the append buffer count into the args buffer used by the Draw Procedural Indirect call
    ComputeBuffer.CopyCount(culledParticlesIdxBuffer, argsBuffer, dstOffset: 1);
    ribbonRenderCommand.DrawProceduralIndirect(Matrix4x4.identity, renderMaterial, 0, MeshTopology.Triangles, dataBuffer);
}
```

Wir haben versucht, die gleiche Technik für die Cloudteilchen zu verwenden, bei der wir sie auf dem Compute-Shader entfernen und nur die sichtbaren Partikel zum Rendern pushen. Diese Technik hat uns tatsächlich nicht viel auf der GPU sparen, da der größte Engpass die Anzahl der auf dem Bildschirm gerenderten Pixel und nicht die Kosten für die Berechnung der Scheitelpunkte war.

Das andere Problem bei dieser Technik war, dass der Anfügepuffer in zufälliger Reihenfolge aufgefüllt wurde, da die Partikel parallelisiert werden, sodass die sortierten Partikel nicht sortiert wurden, was zu flackernden Cloudteilchen führt.

Es gibt Techniken zum Sortieren des Pushpuffers, aber die begrenzte Menge an Leistungssteigerungen, die wir aus dem Culling von Partikeln erhalten haben, würde wahrscheinlich mit einer zusätzlichen Sortierung versetzt werden, daher haben wir uns entschieden, diese Optimierung nicht zu verfolgen.

## <a name="adaptive-rendering"></a>Adaptives Rendering

Um eine stabile Framerate für eine App mit unterschiedlichen Renderingbedingungen wie einer cloudbasierten oder einer klaren Ansicht sicherzustellen, haben wir adaptives Rendering für unsere App eingeführt.

Der erste Schritt des adaptiven Renderings besteht im Messen der GPU. Hierzu haben wir benutzerdefinierten Code am Anfang und Ende eines gerenderten Frames in den GPU-Befehlspuffer eingefügt und die Zeit des linken und rechten Blickbildschirms erfasst.

Indem wir die Zeit für das Rendering messen und mit der gewünschten Aktualisierungsrate vergleichen, haben wir ein Gefühl dafür bekommen, wie nah wir am Löschen von Frames waren.

Wenn sie sich dem Löschen von Frames naht, passen wir unser Rendering an, um es schneller zu machen. Eine einfache Möglichkeit zur Anpassung besteht in der Änderung der Viewportgröße des Bildschirms, die weniger Pixel erfordert, um gerendert zu werden.

Mit *UnityEngine.XR.XRSettings.renderViewportScale* verkleinert das System den zielorientierten Viewport und streckt das Ergebnis automatisch wieder nach oben, damit es dem Bildschirm passt. Eine kleine Skalierungsänderung ist in der Geometrie der Welt spürbar, und ein Skalierungsfaktor von 0,7 erfordert, dass die Hälfte der Pixel gerendert wird.

![70 % Skalierung, die Hälfte der Pixel](images/datascape-scaling-700px.jpg)

Wenn wir feststellen, dass wir Frames ablegen möchten, senken wir die Skala um eine feste Zahl und erhöhen sie wieder, wenn wir wieder schnell genug ausgeführt werden.

Wir haben uns zwar entschieden, welche Cloudtechnik basierend auf den Grafikfunktionen der Hardware beim Start verwendet werden soll, aber es ist möglich, sie auf Daten der GPU-Messung zu basieren, um zu verhindern, dass das System lange Zeit eine niedrige Auflösung aufhält. Dies war jedoch etwas, das wir in Datascape nicht untersuchen mussten.

## <a name="final-thoughts"></a>Schlussbemerkungen

Die Ausrichtung auf eine Vielzahl von Hardware ist eine Herausforderung und erfordert einige Planungen.

Es wird empfohlen, mit der Ausrichtung auf weniger betriebene Computer zu beginnen, um sich mit dem Problembereich vertraut zu machen und eine Sicherungslösung zu entwickeln, die auf allen Ihren Computern ausgeführt wird. Entwerfen Sie Ihre Lösung mit Füllrate, da Pixel die beliebtesten Ressourcen sind. Vollwertgeometrie über Transparenz als Ziel.

Mit einer Sicherungslösung können Sie dann mit einer komplexeren Schichtung für High-End-Computer beginnen oder die Auflösung Ihrer Sicherungslösung verbessern.

Entwerfen Sie für ungünstigste Szenarien, und erwägen Sie möglicherweise die Verwendung von adaptivem Rendering für große Situationen.

## <a name="about-the-authors"></a>Über die Autoren

<table style="border:0">
<tr>
<td style="border:0" width="60px"><img alt="Picture of Robert Ferrese" width="60" height="60" src="images/robert-ferrese-60px.jpg"></td>
<td style="border:0"><b>Robert Mussese</b><br>Anwendungsentwickler @Microsoft</td>
</tr>
<tr>
<td style="border:0" width="60px"><img alt="Picture of Dan Andersson" width="60" height="60" src="images/dan-andersson-60px.jpg"></td>
<td style="border:0"><b>Dan Andersson</b><br>Anwendungsentwickler @Microsoft</td>
</tr>
</table>


## <a name="see-also"></a>Siehe auch
* [Grundlegendes zur Leistung Mixed Reality](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Leistungsindikatoren Empfehlungen Unity](../develop/unity/performance-recommendations-for-unity.md)

 
