---
title: Hologrammstabilisierung
description: Leistung von Hologrammen unter unterschiedlichen Umgebungs- und Bildfrequenzbedingungen.
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Umgebungsnachverfolgung, TMP,
ms.openlocfilehash: 48841ee02e5208dcf8363b62c03415797017215c3a52231b3417103978ffc66e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213426"
---
# <a name="hologram-stabilization"></a>Hologrammstabilisierung

## <a name="performance"></a>Leistung

Damit die zugrunde liegende Mixed Reality-Plattform und das Gerät die besten Ergebnisse erzielen, ist es wichtig, Bildraten zu erzielen. Die Zielframerate (z. B. 60 FPS oder 90 FPS) variiert je nach Plattform und Gerät. Mixed Reality-Anwendungen, die die Framerate treffen, verfügen jedoch über stabile Hologramme sowie effiziente Kopfnachverfolgung, Handverfolgung und mehr.  

## <a name="environment-tracking"></a>Umgebungsnachverfolgung

Stabiles holografisches Rendering basiert stark auf der Nachverfolgung von Kopfposen durch die Plattform & Gerät. Unity rendert die Szene mit jedem Frame aus der Kamerapose, die von der zugrunde liegenden Plattform geschätzt und bereitgestellt wird. Wenn diese Nachverfolgung der tatsächlichen Kopfbewegung nicht ordnungsgemäß folgt, erscheinen Hologramme visuell ungenau. Dies ist besonders offensichtlich und wichtig für AR-Geräte wie HoloLens, bei denen Benutzer virtuelle Hologramme mit der realen Welt in Beziehung stellen können. Die Leistung ist für die zuverlässige Kopfverfolgung von Bedeutung, aber es kann auch [andere wichtige](/windows/mixed-reality/environment-considerations-for-hololens)Features geben. Die Typen von Umgebungselementen, die sich auf die Benutzerfreundlichkeit auswirken, hängen von den spezifischen Zielplattformdaten ab.

## <a name="windows-mixed-reality"></a>Windows Mixed Reality

Die Windows Mixed Reality-Plattform stellt [Referenzmaterial für](/windows/mixed-reality/hologram-stability) die Entwicklung von Hologrammen auf der Plattform zur Verfügung. Es gibt jedoch einige wichtige Tools, die Entwickler verwenden können, um die visuelle Hologrammerfahrung für Benutzer zu verbessern.

### <a name="depth-buffer-sharing"></a>Tiefenpufferfreigabe

Unity-Entwickler haben die Möglichkeit, den Tiefenpuffer der Anwendung mit der Plattform zu teilen. Dies liefert Informationen, bei denen Hologramme für einen aktuellen Frame vorhanden sind, die die Plattform verwenden kann, um Hologramme über einen hardwareunterstützten Prozess zu stabilen, der als Late-Stage Reprojection bezeichnet wird.

#### <a name="late-stage-reprojection"></a>Neuprojektion in später Phase

Am Ende des Renderns eines Frames verwendet die Windows Mixed Reality-Plattform die von der Anwendung erzeugten Farb- &-Tiefenrenderingziele und transformiert die endgültige Bildschirmausgabe, um jede geringfügige Kopfbewegung seit der letzten Kopfstellungsvorhersage zu berücksichtigen. Die Ausführung der Spielschleife einer Anwendung dauert eine Zeit. Bei 60 FPS bedeutet dies beispielsweise, dass die Anwendung ca. 16,667 ms zum Rendern eines Frames verwendet. Obwohl dies wie eine kleine Zeit erscheinen mag, ändern sich die Position und Ausrichtung des Kopfs des Benutzers, was zu neuen Projektionsmatrizen für die Kamera beim Rendering führt. Bei der Neuprojektion in später Phase werden die Pixel im endgültigen Bild transformiert, um diese neue Perspektive zu berücksichtigen.

#### <a name="per-pixel-vs-stabilization-plane-lsr"></a>LSR pro Pixel im Vergleich zur Stabilisierungsebene

Abhängig vom Geräteendpunkt und der Betriebssystemversion, die auf einem Windows Mixed Reality-Gerät ausgeführt werden, wird der Late-StageLate-Stage-Neuprojektionsalgorithmus entweder pro Pixel oder über eine [Stabilitätsebene ausgeführt.](/windows/mixed-reality/hologram-stability#stabilization-plane)

##### <a name="per-pixel-depth-based"></a>Tiefenbasierte Pixelgröße

Bei der tiefenbasierten Neuprojektion pro Pixel wird der Tiefenpuffer verwendet, um die Bildausgabe pro Pixel zu ändern und somit Hologramme in verschiedenen Entfernungen zu stabilisiert. Beispielsweise kann eine Kugel 1 m entfernt vor einer Säule stehen, die 10 m entfernt ist. Die Pixel, die die Kugel darstellen, haben eine andere Transformation als die weit entfernten Pixel, die die Säule darstellen, wenn der Benutzer den Kopf leicht gekippt hat. Bei der Neuprojektion pro Pixel wird dieser Abstandsunterschied bei jedem Pixel berücksichtigt, um eine genauere Neuprojektion zu erreichen.

##### <a name="stabilization-plane"></a>Stabilitätsebene

Wenn es nicht möglich ist, einen genauen Tiefenpuffer zu erstellen, der mit der Plattform gemeinsam genutzt werden kann, verwendet eine andere Form von LSR eine Stabilitätsebene. Alle Hologramme in einer Szene erhalten eine gewisse Stabilität, aber Hologramme, die auf der gewünschten Ebene gespeichert sind, erhalten die maximale Hardwarestabilisierung. Der Punkt und der Normalwert für die Ebene können über die von Unity bereitgestellte *HolographicSettings.SetFocusPointForFrame-API* für [die Plattform bereitgestellt werden.](/windows/mixed-reality/focus-point-in-unity)

#### <a name="depth-buffer-format"></a>Tiefenpufferformat

Wenn Sie HoloLens entwickeln möchten, wird dringend empfohlen, das 16-Bit-Tiefenpufferformat im Vergleich zu 24-Bit zu verwenden. Dies kann zu erheblichen Leistungssteigerungen führen, obwohl Tiefenwerte eine geringere Genauigkeit haben. Um die geringere Genauigkeit zu kompensieren und [Z-Fighting](https://en.wikipedia.org/wiki/Z-fighting) [](https://docs.unity3d.com/Manual/class-Camera.html) zu vermeiden, wird empfohlen, die Clipebene von dem von Unity festgelegten Standardwert von 1.000 m zu verringern.

> [!NOTE]
> Bei Verwendung *des 16-Bit-Tiefenformats* funktionieren die erforderlichen Effekte des Schablonenpuffers nicht, da Unity in dieser Einstellung keinen Schablonenpuffer erstellt. [](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) Wenn Sie *umgekehrt das 24-Bit-Tiefenformat* auswählen, wird in der Regel ein [8-Bit-Schablonenpuffer](https://docs.unity3d.com/Manual/SL-Stencil.html)erstellt, sofern dies auf der Endpunktgrafikplattform zu finden ist.

#### <a name="depth-buffer-sharing-in-unity"></a>Gemeinsame Nutzung des Tiefenpuffers in Unity

Um die tiefenbasierte LSR nutzen zu können, müssen Entwickler zwei wichtige Schritte ausführen.

1. Aktivieren **Sie**  >  **Project Einstellungen**  >  **des** XR-Einstellungen Virtual Reality SDKs unter Edit Project Einstellungen Player  >  **XR**  >   > Depth Buffer **Sharing (Tiefenpufferfreigabe aktivieren).**
    1. Wenn sie HoloLens, wird empfohlen, auch **das 16-Bit-Tiefenformat** auszuwählen.
1. Wenn Sie Farbe auf dem Bildschirm rendern, rendern Sie auch die Tiefe.

[Opake GameObjects](https://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html) in Unity schreiben in der Regel automatisch in die Tiefe. Allerdings schreiben transparente & Textobjekte in der Regel nicht standardmäßig in die Tiefe. Wenn Sie den MRTK-Standard-Shader oder Pro verwenden, kann dies problemlos behoben werden.

> [!NOTE]
> Um schnell zu bestimmen, welche Objekte in einer Szene nicht visuell in den Tiefenpuffer schreiben, können Sie das Hilfsprogramm Render [ *Depth Buffer*](../configuration/mixed-reality-configuration-guide.md#editor-utilities) unter dem *Editor Einstellungen* im MRTK-Konfigurationsprofil verwenden.

##### <a name="transparent-mrtk-standard-shader"></a>Transparent MRTK Standard-Shader

Wählen Sie für transparente Materialien, die [den MRTK Standard-Shader](../features/rendering/MRTK-standard-shader.md)verwenden, das Material aus, um es im Inspektorfenster *anzuzeigen.* Klicken Sie dann auf die *Schaltfläche Fix Now* (Jetzt korrigieren), um das zu schreibende Material in die Tiefe zu konvertieren (d. h. Z-Write On).

Vorher

![Tiefenpuffer vor Korrektur des MRTK-Standard-Shaders](../features/images/performance/DepthBufferFixNow_Before.PNG)

Nach

![MrTK-Standard-Shader mit festem Tiefenpuffer](../features/images/performance/DepthBufferFixNow_After.PNG)

##### <a name="text-mesh-pro"></a>Text Mesh-Pro

Wählen Sie für Text Mesh Pro-Objekte das TMP-GameObject aus, um es im Inspektor zu sehen. Wechseln Sie unter der Materialkomponente den Shader für das zugewiesene Material, um den MRTK TextMeshPro-Shader zu verwenden.

![Text mesh Pro Depth Buffer Fix](../features/images/performance/TextMeshPro-DepthBuffer-Fix.PNG)

##### <a name="custom-shader"></a>Benutzerdefinierter Shader

Wenn Sie einen benutzerdefinierten Shader schreiben, fügen Sie das [ZWrite-Flag](https://docs.unity3d.com/Manual/SL-CullAndDepth.html) oben in der *Pass-Blockdefinition* hinzu, um den Shader für das Schreiben in den Tiefenpuffer zu konfigurieren.

```
Shader "Custom/MyShader"
{
    SubShader
    {
        Pass
        {
            ...
            ZWrite On
            ...
        }
    }
}
```

##### <a name="opaque-backings"></a>Nicht transparente Backings

Wenn die oben genannten Methoden für ein bestimmtes Szenario nicht funktionieren (d. h. Mithilfe der Unity-Benutzeroberfläche ist es möglich, dass ein anderes Objekt in den Tiefenpuffer schreibt. Ein gängiges Beispiel ist die Verwendung von Unity UI Text in einem unverankerten Panel in einer Szene. Wenn der Bereich undurchsichtig ist oder zumindest in die Tiefe geschrieben wird, wird der Text & dem Bereich durch die Plattform stabilisiert, da sich die Z-Werte so nah beieinander befinden.

### <a name="worldanchors-hololens"></a>WorldAnchors (HoloLens)

Neben der Sicherstellung, dass die richtigen Konfigurationen erfüllt werden, um die visuelle Stabilität sicherzustellen, ist es wichtig, sicherzustellen, dass Hologramme an ihren richtigen physischen Positionen stabil bleiben. Um die Plattform über wichtige Orte in einem physischen Raum zu informieren, können Entwickler [WorldAnchors](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) auf GameObjects nutzen, die an einem Ort bleiben müssen. Ein [WorldAnchor ist](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) eine Komponente, die einem GameObject hinzugefügt wird und die absolute Kontrolle über die Transformation dieses Objekts übernimmt.

Geräte wie HoloLens werden ständig gescannt und lernen die Umgebung. Wenn der HoloLens die Bewegung & position im Raum verfolgt, werden seine Schätzungen aktualisiert und das [Unity-Koordinatensystem angepasst.](/windows/mixed-reality/coordinate-systems-in-unity) Wenn beispielsweise ein GameObject 1 m von der Kamera zu Beginn platziert wird, während das HoloLens die Umgebung verfolgt, kann es erkennen, dass der physische Punkt, an dem sich das GameObject befindet, tatsächlich 1,1 m entfernt ist. Dies würde zu einem Hologrammdrift führen. Durch anwenden eines WorldAnchor auf ein GameObject kann der Anker die Transformation des Objekts steuern, sodass das Objekt an der richtigen physischen Position verbleibt (d. h. zur Laufzeit auf 1,1 m statt auf 1 m aktualisiert). Um [WorldAnchors über](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) App-Sitzungen hinweg zu speichern, können Entwickler [worldAnchorStore](https://docs.unity3d.com/ScriptReference/XR.WSA.Persistence.WorldAnchorStore.html) verwenden, um [WorldAnchors zu](/windows/mixed-reality/persistence-in-unity)speichern und zu laden.

> [!NOTE]
> Nachdem einem GameObject eine WorldAnchor-Komponente hinzugefügt wurde, ist es nicht mehr möglich, die Transformation dieses GameObject zu ändern (d. h. transform.position = x). Ein Entwickler muss worldAnchor entfernen, um die Transformation zu bearbeiten.

```c#
WorldAnchor m_anchor;

public void AddAnchor()
{
    this.m_anchor = this.gameObject.AddComponent<WorldAnchor>();
}

public void RemoveAnchor()
{
    DestroyImmediate(m_anchor);
}
```

Wenn Sie eine Alternative zur manuellen Arbeit mit Anchors wünschen, sehen Sie sich die Microsoft World Locking Tools an. 

> [!div class="nextstepaction"]
> [Installieren mit dem MR-Featuretool](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/WLTviaMRFeatureTool.html)

## <a name="see-also"></a>Siehe auch

- [Leistung](../performance/perf-getting-started.md)
- [Überlegungen zur Umgebung für HoloLens](/windows/mixed-reality/environment-considerations-for-hololens)
- [Hologrammstabilitäts-Windows Mixed Reality](/windows/mixed-reality/hologram-stability)
- [Fokuspunkt in Unity](/windows/mixed-reality/focus-point-in-unity)
- [Koordinatensysteme in Unity](/windows/mixed-reality/coordinate-systems-in-unity)
- [Persistenz in Unity](/windows/mixed-reality/persistence-in-unity)
- [Grundlegendes zur Leistung Mixed Reality](/windows/mixed-reality/understanding-performance-for-mixed-reality)
- [Leistungsempfehlungen für Unity](/windows/mixed-reality/performance-recommendations-for-unity)
