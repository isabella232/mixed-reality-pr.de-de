---
title: Darstellung
description: Erfahren Sie, wie holografisches Rendering es Ihrer App ermöglicht, ein Hologramm an einem präzisen Ort auf der Ganzen Welt um den Benutzer zu zeichnen.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Rendering, Hologramm
ms.openlocfilehash: d01a5911ad8b479197bd38e8ed7825feef1f69dc51d2c2dc2f8e500e93880955
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193666"
---
# <a name="rendering"></a>Darstellung

Holografisches Rendering ermöglicht Es Ihrer Anwendung, ein Hologramm an einem präzisen Ort auf der Welt um den Benutzer zu zeichnen, unabhängig davon, ob es genau in der physischen Welt oder in einem virtuellen Bereich platziert ist, den Sie erstellt haben. [Hologramme](../../discover/hologram.md) sind Objekte, die aus Sound und Licht bestehen. Durch das Rendering kann Ihre Anwendung das Licht hinzufügen.

## <a name="device-support"></a>Geräteunterstützung

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Feature</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (erste Generation)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
    </tr>
     <tr>
        <td>Darstellung</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="holographic-rendering"></a>Holographisches Rendern

Der Schlüssel zum holografischen Rendering besteht darin, zu wissen, welche Art von Gerät verwendet wird. Geräte mit **Anzeigeanzeigen**, z. [B. HoloLens](/hololens/hololens1-hardware), fügen der Welt Licht hinzu. Schwarze Pixel sind vollständig transparent, während bessere Pixel zunehmend deckend sind. Da das Licht aus den Displays dem Licht aus der realen Welt hinzugefügt wird, sind die weißen Pixel durchscheinend.

Das stereokopische Rendering bietet zwar einen Tiefenhinweise für Ihre Hologramme, aber das Hinzufügen von [Erdungseffekten](../../design/interaction-fundamentals.md) kann Benutzern helfen, einfacher zu sehen, welche Oberfläche sich ein Hologramm in der Nähe befindet. Eine Erdungstechnik besteht darin, ein Leuchtlicht um ein Hologramm auf der Oberfläche in der Nähe hinzuzufügen und dann einen Schatten gegen diesen Leuchtstrahl zu rendern. Auf diese Weise scheint Ihr Schatten Licht von der Umgebung zu subtrahieren. [Räumlicher Sound](../../design/spatial-sound.md) ist ein weiterer wichtiger Tiefenhinweise, mit dem Benutzer über die Entfernung und die relative Position eines Hologramms nachdenken können.

Geräte mit **nicht transparenten Displays** wie [Windows Mixed Reality immersiven Headsets](../../discover/immersive-headset-hardware-details.md)blockieren die Welt. Schwarze Pixel sind vollschwarz, und jede andere Farbe wird dem Benutzer als diese Farbe angezeigt. Ihre Anwendung ist dafür verantwortlich, alles zu rendern, was dem Benutzer angezeigt wird. Dies macht es noch wichtiger, eine konstante Aktualisierungsrate aufrechtzuerhalten, damit Benutzer eine komfortable Erfahrung haben.

## <a name="predicted-rendering-parameters"></a>Vorhergesagte Renderingparameter

Mixed Reality-Headsets (sowohl HoloLens als auch immersive Headsets) verfolgen kontinuierlich die Position und Ausrichtung des Kopfes des Benutzers relativ zu seiner Umgebung. Wenn Ihre Anwendung mit der Vorbereitung des nächsten Frames beginnt, sagt das System vorher, wo sich der Kopf des Benutzers in Der Zukunft befindet, genau zu dem Zeitpunkt, zu dem der Frame auf den Bildschirmen angezeigt wird. Basierend auf dieser Vorhersage berechnet das System die Ansicht und die Projektionstransformationen, die für diesen Frame verwendet werden sollen. Ihre Anwendung **muss diese Transformationen verwenden, um die richtigen Ergebnisse zu erzielen.** Wenn vom System bereitgestellte Transformationen nicht verwendet werden, wird das resultierende Bild nicht an der realen Welt ausgerichtet, was zu Benutzerbehinderungen führt.

> [!NOTE]
> Um genau vorherzusagen, wann ein neuer Frame die Displays erreicht, misst das System ständig die effektive End-to-End-Latenz der Renderingpipeline Ihrer Anwendung. Während sich das System an die Länge der Renderingpipeline anpasst, können Sie die Hologrammstabilität verbessern, indem Sie diese Pipeline so kurz wie möglich halten.

Anwendungen, die erweiterte Techniken verwenden, um die Systemvorhersage zu erweitern, können die Transformationen der Systemansicht und Projektion überschreiben. Diese Anwendungen müssen weiterhin vom System bereitgestellte Transformationen als Grundlage für ihre benutzerdefinierten Transformationen verwenden, um sinnvolle Ergebnisse zu erzielen.

## <a name="other-rendering-parameters"></a>Andere Renderingparameter

Beim Rendern eines Frames gibt das System den Backpuffer-Viewport an, in dem die Anwendung zeichnen soll. Dieser Viewport ist häufig kleiner als die vollständige Größe des Rahmenpuffers. Unabhängig von der Viewportgröße sobald der Frame von der Anwendung gerendert wurde, skaliert das System das Bild so hoch, dass es die gesamte Anzeige auffüllt.

Für Anwendungen, die nicht mit der erforderlichen Aktualisierungsrate gerendert [werden können, können Systemrenderingparameter so konfiguriert werden,](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration) dass die Arbeitsspeicherauslastung und die Renderingkosten auf Kosten eines erhöhten Pixelaliasings reduziert werden. Das Backpufferformat kann auch geändert werden, was bei einigen Apps zur Verbesserung der Speicherbandbreite und des Pixeldurchsatzes beitragen kann.

Das Rendering von Frustum, Auflösung und Framerate, in dem Ihre App zum Rendern aufgefordert wird, kann sich auch von Frame zu Frame ändern und sich über das linke und rechte Auge unterscheiden. Wenn z. B. [Mixed Reality Capture](/hololens/holographic-photos-and-videos) (MRC) aktiv ist und die Konfiguration der [Foto-/Videokameraansicht](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind) nicht aktiviert ist, kann ein Auge mit einem größeren FOV oder einer größeren Auflösung gerendert werden.

Für einen bestimmten Frame *muss* Ihre App mithilfe der vom System bereitgestellten Ansichtstransformation, Projektionstransformation und Viewportauflösung gerendert werden. Darüber hinaus darf Ihre Anwendung nie davon ausgehen, dass rendering- oder view-Parameter von Frame zu Frame korrigiert bleiben. Engines wie Unity verarbeiten all diese Transformationen für Sie in ihren eigenen Kameraobjekten, sodass die physische Bewegung Ihrer Benutzer und der Zustand des Systems immer berücksichtigt werden. Wenn Ihre Anwendung eine virtuelle Bewegung des Benutzers durch die Welt zulässt (z. B. mit dem Thumbstick auf einem Gamepad), können Sie ein übergeordnetes Objekt über der Kamera hinzufügen, das ihn bewegt. Dadurch spiegelt die Kamera sowohl die virtuelle als auch die physische Bewegung des Benutzers wider. Wenn Ihre Anwendung die vom System bereitgestellte Ansichtstransformation, Projektionstransformation oder Viewportdimension ändert, muss sie das System informieren, indem sie die entsprechende [Überschreibungs-API](/uwp/api/Windows.Graphics.Holographic.HolographicCameraPose#Windows_Graphics_Holographic_HolographicCameraPose)aufruft.

Um die Stabilität Ihres holografischen Renderings zu verbessern, sollte Ihre App Windows jedem Frame den Tiefenpuffer bereitstellen, den sie für das Rendering verwendet. Wenn Ihre App einen Tiefenpuffer bereitstellt, sollte sie über konsistente Tiefenwerte verfügen, wobei die Tiefe in Metern von der Kamera ausgedrückt wird. Auf diese Weise kann das System Ihre Pixel-Tiefendaten verwenden, um inhalte besser zu stabilieren, wenn der Kopf des Benutzers am Ende etwas vom vorhergesagten Standort abrückt. Wenn Sie Ihren Tiefenpuffer nicht bereitstellen können, können Sie einen Fokuspunkt und normal bereitstellen und eine Ebene definieren, die den Großteil Ihres Inhalts durchschneidet. Wenn sowohl der Tiefenpuffer als auch eine Fokusebene bereitgestellt werden, kann das System beides verwenden. Insbesondere ist es hilfreich, sowohl den Tiefenpuffer als auch einen Fokuspunkt bereitzustellen, der einen Geschwindigkeitsvektor enthält, wenn Ihre Anwendung Hologramme anzeigt, die sich in Bewegung befinden.

Ausführliche Informationen zu diesem Thema finden Sie im Artikel [Rendering in DirectX.](../native/rendering-in-directx.md)

## <a name="holographic-cameras"></a>Holografische Kameras

Windows Mixed Reality führt das Konzept einer **holografischen Kamera** ein. Holografische Kameras ähneln der herkömmlichen Kamera in 3D-Grafiktexten. sie definieren sowohl die extrinsische (Position und Ausrichtung) als auch die systeminternen Kameraeigenschaften. (Beispielsweise wird ein Sichtfeld verwendet, um eine virtuelle 3D-Szene anzuzeigen.) Im Gegensatz zu herkömmlichen 3D-Kameras steuert die Anwendung nicht die Position, Ausrichtung und systeminternen Eigenschaften der Kamera. Stattdessen wird die Position und Ausrichtung der holografischen Kamera implizit durch die Bewegung des Benutzers gesteuert. Die Bewegung des Benutzers wird über eine Ansichtstransformation frameweise an die Anwendung weitergeleitet. Ebenso werden die systeminternen Eigenschaften der Kamera durch die kalibrierte Brille des Geräts und die weitergeleitete Frame-für-Frame-Übertragung über die Projektionstransformation definiert.

Im Allgemeinen wird Ihre Anwendung für eine einzelne Stereokamera gerendert. Eine stabile Renderingschleife unterstützt mehrere Kameras und sowohl Mono- als auch Stereokameras. Beispielsweise könnte das System Ihre Anwendung auffordern, aus einer alternativen Perspektive zu rendern, wenn der Benutzer je nach Headsetform ein Feature wie [Mixed Reality Capture](/hololens/holographic-photos-and-videos) (MRC) aktiviert. Anwendungen, die mehrere Kameras unterstützen können, erhalten sie, indem sie sich für die [Art](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind) von Kameras [entscheiden,](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration) die sie unterstützen können.

## <a name="volume-rendering"></a>Volumengrafik

Beim Rendern von medizinischen MRIs oder technischen Volumes in 3D werden häufig [Volumerenderingtechniken](volume-rendering.md) verwendet. Diese Techniken können in Mixed Reality interessant sein, bei der Benutzer ein solches Volumen natürlich aus wichtigen Winkeln betrachten können, indem sie einfach den Kopf bewegen.

## <a name="supported-resolutions-on-hololens-first-gen"></a>Unterstützte Lösungen für HoloLens (erste Generation)

* Die maximale Viewportgröße ist eine Eigenschaft von [HolographicDisplay.](/uwp/api/windows.graphics.holographic.holographicdisplay) HoloLens ist standardmäßig auf die maximale Viewportgröße von 720p (1268 x 720) festgelegt.
* Die Viewportgröße kann durch Festlegen von ViewportScaleFactor auf holographicCamera geändert werden. Dieser Skalierungsfaktor liegt im Bereich von 0 bis 1.
* Die niedrigste unterstützte Viewportgröße auf HoloLens (erste Generation) beträgt 50 % von 720p, was 360p (634 x 360) entspricht. Dies ist ein ViewportScaleFactor von 0.5.
* Alles, was kleiner als 540p ist, wird aufgrund einer visuellen Beeinträchtigung nicht empfohlen, kann aber verwendet werden, um Engpässe bei der Pixelfüllrate zu identifizieren.

## <a name="supported-resolutions-on-hololens-2"></a>Unterstützte Lösungen für HoloLens 2

* Die aktuellen und maximalen unterstützten Renderzielgrößen sind Eigenschaften der [Ansichtskonfiguration](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration). HoloLens 2 ist standardmäßig auf die maximale Renderzielgröße (1440 x 936) festgelegt.
* Apps können die Größe von Renderzielpuffern ändern, indem sie die RequestRenderTargetSize-Methode aufrufen, um eine neue Renderzielgröße anzufordern. Es wird eine neue Renderzielgröße ausgewählt, die die angeforderte Renderzielgröße erfüllt oder überschreitet. Diese API ändert die Größe des Renderzielpuffers, der eine Neuzuordnung des Arbeitsspeichers auf der GPU erfordert. Dies hat folgende Auswirkungen: Die Renderzielgröße kann herunterskaliert werden, um die Arbeitsspeicherauslastung der GPU zu verringern, und diese Methode sollte nicht mit hoher Häufigkeit aufgerufen werden.
* Apps können die Viewportgröße weiterhin auf die gleiche Weise ändern wie bei HoloLens 1. Es gibt keine zusätzliche Speicherzuordnung auf der GPU, sodass sie mit hoher Frequenz geändert werden kann, aber nicht verwendet werden kann, um die Arbeitsspeicherauslastung der GPU zu reduzieren.
* Die niedrigste unterstützte Viewportgröße auf HoloLens 2 ist 634 x 412, ein ViewportScaleFactor von ungefähr 0,44, wenn die Standardmäßige Renderzielgröße verwendet wird.
* Wenn eine Renderzielgröße bereitgestellt wird, die kleiner als die niedrigste unterstützte Viewportgröße ist, wird der Viewportskalierfaktor ignoriert.
* Alles, was kleiner als 540p ist, wird aufgrund einer visuellen Beeinträchtigung nicht empfohlen, kann aber verwendet werden, um Engpässe bei der Pixelfüllrate zu identifizieren.



## <a name="see-also"></a>Siehe auch
* [Hologrammstabilität](hologram-stability.md)
* [Rendern in DirectX](../native/rendering-in-directx.md)