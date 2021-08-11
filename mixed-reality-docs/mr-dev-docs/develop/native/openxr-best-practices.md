---
title: 'OpenXR: Bewährte Methoden'
description: Lernen Sie die bewährten Methoden für visuelle Qualität, Stabilität und Leistung für Ihre OpenXR-Anwendungen kennen.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Ronronos, BasicXRApp, DirectX, nativ, native App, benutzerdefinierte Engine, Middleware, bewährte Methoden, Leistung, Qualität, Stabilität
ms.openlocfilehash: 2cbd05417f62f7380b048f692295bbbe98ceba5bce69c4f1dae21aec812ec450
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207848"
---
# <a name="openxr-app-best-practices"></a>Bewährte Methoden für OpenXR-Apps

Ein Beispiel für die bewährten Methoden finden Sie unten in der Datei OpenXRProgram.cpp von <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp.</a> Die Run()-Funktion am Anfang erfasst einen typischen OpenXR-App-Codefluss von der Initialisierung bis zur Ereignis- und Renderingschleife.

## <a name="best-practices-for-visual-quality-and-stability"></a>Bewährte Methoden für visuelle Qualität und Stabilität

In den bewährten Methoden in diesem Abschnitt wird beschrieben, wie Sie die beste visuelle Qualität und Stabilität in jeder OpenXR-Anwendung erzielen.

Weitere Leistungsempfehlungen für HoloLens 2 finden Sie im Abschnitt [Best Practices for performance on HoloLens 2](#best-practices-for-performance-on-hololens-2) weiter unten.

### <a name="gamma-correct-rendering"></a>Gamma-korrektes Rendering

Achten Sie darauf, dass Ihre Renderingpipeline gamma-korrekt ist. Beim Rendern in eine Swapkette sollte das Renderziel-Ansichtsformat mit dem Swapchain-Format übereinstimmen. Beispielsweise `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` sowohl für das Swapchainformat als auch für die Renderzielansicht.
Es gibt eine Ausnahme, wenn die Renderingpipeline der App eine manuelle SRGB-Konvertierung im Shadercode vorsetzt. Die App sollte ein sRGB-Swapchainformat anfordern, aber das lineare Format für die Renderzielansicht verwenden. Fordern Sie beispielsweise als Swapchainformat an, `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` verwenden Sie jedoch als `DXGI_FORMAT_B8G8R8A8_UNORM` Renderzielansicht, um zu verhindern, dass Inhalte doppelt gamma korrigiert werden.

### <a name="submit-depth-buffer-for-projection-layers"></a>Übermitteln eines Tiefenpuffers für Projektionsebenen

Verwenden Sie immer `XR_KHR_composition_layer_depth` die Erweiterung, und übermitteln Sie den Tiefenpuffer zusammen mit der Projektionsebene, wenn Sie einen Frame an `xrEndFrame` übermitteln.
Das Aktivieren der Hardwaretiefe-Neuprojektion auf HoloLens 2 verbessert die Hologrammstabilität.

### <a name="choose-a-reasonable-depth-range"></a>Auswählen eines angemessenen Tiefenbereichs

Bevorzugen Sie einen engeren Tiefenbereich, um den Bereich des virtuellen Inhalts zu beschränken, um die Hologrammstabilität auf HoloLens zu unterstützen.
Das OpenXrProgram.cpp-Beispiel verwendet beispielsweise 0,1 bis 20 Meter.
Verwenden Sie [reversed-Z](https://developer.nvidia.com/content/depth-precision-visualized) für eine einheitlichere Tiefenauflösung.
Auf HoloLens 2 trägt die Verwendung des bevorzugten `DXGI_FORMAT_D16_UNORM` Tiefenformats zu einer besseren Bildfrequenz und Leistung bei, obwohl 16-Bit-Tiefenpuffer eine geringere Tiefenauflösung als 24-Bit-Tiefenpuffer bieten.
Die Verwendung dieser bewährten Methoden, um die Tiefenauflösung optimal zu nutzen, wird wichtiger.

### <a name="prepare-for-different-environment-blend-modes"></a>Vorbereiten auf verschiedene Umgebungsmischungsmodi

Wenn Ihre Anwendung auch auf immersiven Headsets ausgeführt wird, die die Welt vollständig blockieren, achten Sie darauf, unterstützte Umgebungsmischungsmodi mithilfe der API aufzuzählen `xrEnumerateEnvironmentBlendModes` und Ihre Renderinginhalte ordnungsgemäß vorzubereiten.
Beispielsweise sollte die App für ein System mit `XR_ENVIRONMENT_BLEND_MODE_ADDITIVE` wie dem HoloLens transparent als klare Farbe verwenden, während die App für ein System mit eine nicht transparente Farbe oder einen `XR_ENVIRONMENT_BLEND_MODE_OPAQUE` virtuellen Raum im Hintergrund rendern sollte.

### <a name="choose-unbounded-reference-space-as-applications-root-space"></a>Auswählen eines nicht gebundenen Referenzraums als Stammbereich der Anwendung

Anwendungen richten in der Regel einen Koordinatenraum in der Stammwelt ein, um Ansichten, Aktionen und Hologramme miteinander zu verbinden.
Verwenden Sie `XR_REFERENCE_SPACE_TYPE_UNBOUNDED_MSFT` , wenn die Erweiterung unterstützt wird, um ein [koordinatenbasiertes Weltkoordinatensystem](../../design/coordinate-systems.md#building-a-world-scale-experience)einzurichten, sodass Ihre App unerwünschte Hologrammabweichungen vermeiden kann, wenn sich der Benutzer weit vom Startort der App bewegt (z. B. 5 Meter).
Verwenden Sie `XR_REFERENCE_SPACE_TYPE_LOCAL` als Fallback, wenn die Erweiterung für unbegrenzten Speicherplatz nicht vorhanden ist.

### <a name="associate-hologram-with-spatial-anchor"></a>Zuordnen eines Hologramms zu einem Raumanker

Wenn Sie einen unbegrenzten Referenzraum verwenden, können Hologramme, die Sie direkt in diesem Referenzraum platzieren, [abweichen, wenn der Benutzer zu entfernten Räumen führt und dann zurückkommt.](../../design/coordinate-systems.md#building-a-world-scale-experience)
Wenn Hologrammbenutzer an einer diskreten Position auf der Welt platzieren, erstellen Sie mithilfe der Erweiterungsfunktion [einen Raumanker,](../../design/spatial-anchors.md#best-practices) `xrCreateSpatialAnchorSpaceMSFT` und positionieren Sie das Hologramm am Ursprung. Dadurch bleibt das Hologramm im Laufe der Zeit unabhängig stabil.

### <a name="support-mixed-reality-capture"></a>Unterstützung der Mixed Reality-Erfassung

Obwohl HoloLens 2 primäre Anzeige additive Umgebungsmischung verwendet, wird beim Starten der [Mixed Reality-Erfassung](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md)der Renderinginhalt der App alphageblendet mit dem Umgebungsvideostream.
Um die beste visuelle Qualität in Mixed Reality-Aufnahmevideos zu erzielen, ist es am besten, in der Projektionsebene von `XR_COMPOSITION_LAYER_BLEND_TEXTURE_SOURCE_ALPHA_BIT` `layerFlags` festzulegen.

## <a name="best-practices-for-performance-on-hololens-2"></a>Bewährte Methoden für die Leistung bei HoloLens 2

Als mobiles Gerät mit Hardware-Reprojection-Unterstützung hat HoloLens 2 strengere Anforderungen für eine optimale Leistung.  Es gibt eine Reihe von Möglichkeiten, Kompositionsdaten über zu übermitteln, was zu einer Nachverarbeitung mit spürbaren Leistungseinbußen führt.

### <a name="select-a-swapchain-format"></a>Auswählen eines Swapchainformats

Aufzählen Sie unterstützte Pixelformate immer `xrEnumerateSwapchainFormats` mithilfe von , und wählen Sie das erste Farb- und Tiefenpixelformat aus der Laufzeit aus, das die App unterstützt, da die Runtime dies für eine optimale Leistung bevorzugt. Beachten Sie, dass auf HoloLens 2 `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` und in der Regel die erste Wahl `DXGI_FORMAT_D16_UNORM` ist, um eine bessere Renderingleistung zu erzielen. Diese Einstellung kann bei VR-Headsets, die auf einem Desktop-PC ausgeführt werden, unterschiedlich sein, wobei 24-Bit-Tiefenpuffer weniger Auswirkungen auf die Leistung haben.
  
**Leistungswarnung:** Die Verwendung eines anderen Formats als das primäre Swapchain-Farbformat führt zur Nachverarbeitung der Laufzeit, was zu erheblichen Leistungseinbußen führt.

### <a name="render-with-recommended-rendering-parameters-and-frame-timing"></a>Rendern mit empfohlenen Renderingparametern und Framezeit

Rendern Sie immer mit der empfohlenen Breite/Höhe der Ansichtskonfiguration ( `recommendedImageRectWidth` und von ), und verwenden Sie vor dem `recommendedImageRectHeight` `XrViewConfigurationView` Rendern immer die `xrLocateViews` API, um die empfohlene Ansichtshaltung, FOV und andere Renderingparameter abzufragen.
Verwenden Sie immer den `XrFrameEndInfo.predictedDisplayTime` aus dem letzten `xrWaitFrame` Aufruf, wenn Sie Posen und Ansichten abfragen.
Dadurch können HoloLens das Rendering anpassen und die visuelle Qualität für die Person optimieren, die die HoloLens trägt.

### <a name="use-a-single-projection-layer"></a>Verwenden einer einzelnen Projektionsebene

HoloLens 2 verfügt über eine begrenzte GPU-Leistung für das Rendern von Inhalten und einen Hardware-Compositor, der für eine einzelne Projektionsschicht optimiert ist.
Die Verwendung einer einzelnen Projektionsschicht kann die Framerate, Hologrammstabilität und visuelle Qualität der Anwendung unterstützen.  
  
**Leistungswarnung:** Die Übermittlung einer einzigen Schutzebene führt zur Nachverarbeitung der Laufzeit, was zu erheblichen Leistungseinbußen führt.

### <a name="render-with-texture-array-and-vprt"></a>Rendern mit Texturarray und VPRT

Erstellen Sie eine `xrSwapchain` für das linke und rechte Auge mithilfe von `arraySize=2` für den Farbaustausch und einen für die Tiefe.
Rendern Sie das linke Auge in Slice 0 und das rechte Auge in Slice 1.
Verwenden Sie einen Shader mit VPRT und instanzierten Zeichnen-Aufrufen für stereoskopisches Rendering, um die GPU-Last zu minimieren.
Dies ermöglicht auch die Optimierung der Laufzeit, um die beste Leistung auf HoloLens 2 zu erzielen.
Alternativen zur Verwendung eines Texturarrays, z. B. doppeltes Rendering oder eine separate Swapkette pro Auge, führen zur Nachverarbeitung der Laufzeit, was zu erheblichen Leistungseinbußen führt.

### <a name="avoid-quad-layers"></a>Vermeiden von Quad-Ebenen

Anstatt Quad-Ebenen als Kompositionsebenen mit zu `XrCompositionLayerQuad` übermitteln, rendern Sie den Quad-Inhalt direkt in die Projektionstauschkette.

**Leistungswarnung:** Die Bereitstellung zusätzlicher Ebenen über eine einzelne Projektionsschicht hinaus, z. B. Quad-Ebenen, führt zur Nachverarbeitung der Laufzeit, was zu erheblichen Leistungseinbußen führt.