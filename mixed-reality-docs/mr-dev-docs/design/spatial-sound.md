---
title: Audio in Mixed Reality
description: Audio in Mixed Reality kann das Vertrauen der Benutzer in Interaktionen mit der Benutzeroberfläche erhöhen und benutzerfreundlicher machen.
author: kegodin
ms.author: v-hferrone
ms.date: 11/07/2019
ms.topic: article
keywords: Raumklang, Umschließen von Sound, 3D-Audio, 3D-Sound, räumliche Audiodaten, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit, Fallstudien, Akustik
ms.openlocfilehash: 75b87098f90611140d2c43bb596e7c5d50dab9c47fc49426d5bcbbe0095c3847
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188820"
---
# <a name="audio-in-mixed-reality"></a>Audio in Mixed Reality

Audio ist ein wesentlicher Bestandteil von Design und Produktivität in Mixed Reality. Sound kann:
* Erhöhen Sie das Vertrauen der Benutzer in Gesten- und Sprachinteraktionen.
* Führen Sie Benutzer zu den nächsten Schritten.
* Kombinieren Sie virtuelle Objekte effektiv mit der realen Welt.

Die Kopfnachverfolgung von Mixed Reality-Headsets mit geringer Latenz, einschließlich HoloLens, unterstützt hochwertige HRTF-basierte Räumliche Raumisierung. Sie können audio in Ihrer Anwendung spatialisieren, um:
* Achten Sie auf visuelle Elemente.
* Helfen Sie Benutzern, das Bewusstsein für ihre reale Umgebung zu behalten.

Akustik verbindet Hologramme tiefer mit der Mixed Reality-Welt. Sie enthält Hinweise zum Umgebungs- und Objektzustand.

Sehen Sie sich [ausführliche Beispiele für den Entwurf an, der Audio verwendet.](spatial-sound-design.md)

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/PTPvx7mDon4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

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
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
    </tr>
     <tr>
        <td>Raumklang</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
     <tr>
        <td>Hardwarebeschleunigung für räumliche Raumbeschleunigung</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="use-of-sounds-in-mixed-reality"></a>Verwendung von Sounds in Mixed Reality

[Die Verwendung von Sounds in Mixed Reality](spatial-sound-design.md) erfordert einen anderen Ansatz als bei Touch- und Tastatur- und Mausanwendungen. Wichtige Entwurfsentscheidungen für Sound sind u. a. die zu räumlichen Töne und interaktionen, die vertont werden müssen. Diese Entscheidungen wirken sich stark auf die Benutzervertrauens-, Produktivitäts- und Lernkurve aus.

### <a name="case-studies"></a>Fallstudien

HoloTour führt Benutzer virtuell zu Sehenswürdigkeiten und historischen Standorten auf der ganzen Welt. Weitere Informationen finden [Sie im Sound-Design für die](case-study-spatial-sound-design-for-holotour.md) HoloTour-Fallstudie. Ein spezielles Mikrofon- und Renderingsetup wurde verwendet, um die Betreffräume zu erfassen.

RoboRaid ist ein Hochleistungs-Energieverbrauchser für HoloLens. Im [Sound-Entwurf für die RoboRaid-Fallstudie](case-study-using-spatial-sound-in-roboraid.md) werden die Entwurfsentscheidungen beschrieben, die getroffen wurden, um sicherzustellen, dass räumliche Audiodaten mit der höchsten drastischen Wirkung verwendet wurden.

## <a name="spatialization"></a>Raumklang

Spatialization ist die direktionale Komponente räumlicher Audiodaten. Bei einer 7.1-Heimordnungseinrichtung ist die Räumliche Veranschaulichung so einfach wie das Schwenken zwischen Nerdungen. Für Mixed Reality-Menschen ist es jedoch wichtig, eine HRTF-basierte Technologie zu verwenden, um Genauigkeit und Komfort zu gewährleisten. Windows bietet HRTF-basierte Räumliche Raumisierung, und diese Unterstützung wird hardwarebeschleunigt auf HoloLens 2.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="should-i-spatialize"></a>Sollte ich raumisieren?

Die Räumliche Raumisierung kann viele Sounds in Mixed Reality-Anwendungen verbessern. Die Raumklangisierung nimmt einen Sound aus dem Kopf des Listeners und platziert ihn in der Welt. Vorschläge zur effektiven Verwendung der Räumlichen Raumisierung in Ihrer Anwendung finden Sie unter [Raumklangentwurf](spatial-sound-design.md).

### <a name="spatializer-personalization"></a>Spatializer-Personalisierung

HRTFs ändern die Unterschiede zwischen Denk- und Phasenunterschieden zwischen Denk- und Häufigkeitsspektrum. Sie basieren auf physischen Modellen und Messungen von menschlichen Kopf-, Torso- und Gehörformen (Pinnae). Unsere Gehirne reagieren auf diese Unterschiede, um eine wahrgenommene Richtung im Sound zu ermöglichen.

Jede Person verfügt über eine eindeutige Form des Kopfs und der Position des Kopfes. Daher entsprechen ihnen die besten HRTFs. Um die Genauigkeit der Räumlichen Vergrößerung zu erhöhen, verwendet HoloLens ipd-Entfernung (Inter-Ary Distance, IPD) von den Headsetanzeigen, um die HRTFs für Ihre Kopfgröße anzupassen.

### <a name="spatializer-platform-support"></a>Unterstützung der Spatializer-Plattform

Windows bietet raumbezogene Funktionen, einschließlich HRTFs, über die [ISpatialAudioClient-API.](/windows/win32/coreaudio/spatial-sound) Diese API macht die HoloLens 2 HRTF-Hardwarebeschleunigung für Anwendungen verfügbar.

### <a name="spatializer-middleware-support"></a>Spatializer-Middlewareunterstützung

Unterstützung für Windows HRTFs ist für die folgenden Audio-Engines von Drittanbietern verfügbar.
* Ein [Unity-Audio-Engine-Plug-In](../develop/unity/spatial-sound-in-unity.md)
* Ein [Wwise-Audio-Engine-Plug-In](https://www.audiokinetic.com/products/plug-ins/msspatial/)

## <a name="acoustics"></a>Akustik

Bei räumlichen Audiodaten geht es um mehr als nur um die Richtung. Andere Dimensionen sind Okklusion, Hindernisse, Hall, Portal und Quellmodellierung. Zusammen werden diese Dimensionen als *Akustik bezeichnet.* Ohne Akustik fehlt raumisierten Tönen der wahrgenommene Abstand.

Die Akustik-Akustik reicht von einfach bis komplex. Sie können einen Hall verwenden, der von jeder Audio-Engine unterstützt wird, um spatialisierte Sounds in die Umgebung des Listeners zu pushen. Akustiksysteme wie [Project Akustik](/gaming/acoustics/what-is-acoustics) bieten eine vielfältigere und ansprechendere Akustikbehandlung. Project Akustik kann die Wirkung von Wänden, Türen und anderer Szenengeometrie auf einem Sound modellieren. Dies ist eine effektive Option für Fälle, in denen die relevante Szenengeometrie zur Entwicklungszeit bekannt ist.

## <a name="next-steps"></a>Nächste Schritte

- [Raumklang in Unity](../develop/unity/spatial-sound-in-unity.md)
- [Verwenden von Sound in Mixed Reality-Anwendungen](spatial-sound-design.md)