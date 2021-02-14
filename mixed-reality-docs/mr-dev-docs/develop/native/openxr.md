---
title: OpenXR
description: Erstellen Sie eine Engine mithilfe des portablen openxr-API-Standards, und stellen Sie Sie für Windows Mixed Reality-und hololens 2-Headsets bereit.
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: Openxr, Khronos, basicxrapp, DirectX, Native, Native APP, benutzerdefinierte Engine, Middleware
ms.openlocfilehash: afb0627a0fb29ff63ea2174676fc2fdfbd252de6
ms.sourcegitcommit: 029f247a6c33068360d3a06f2a473a12586017e1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100496058"
---
# <a name="openxr"></a>OpenXR

<img align="right" src="images/openxr.png" alt="OpenXR logo">

Openxr ist ein offener, kostenloser API-Standard von <a href="https://www.khronos.org/" target="_blank">Khronos</a>, der Engines den systemeigenen Zugriff auf eine Vielzahl von Geräten über das [gemischte Reality-Spektrum](../../discover/mixed-reality.md)hinweg bereitstellt.

Sie können mit OpenXR auf einem immersiven HoloLens 2- oder Windows Mixed Reality-Headset auf dem Desktop entwickeln.  Wenn Sie keinen Zugriff auf ein Headset haben, können Sie stattdessen den hololens 2-Emulator oder den Windows Mixed Reality-Simulator verwenden.

## <a name="why-openxr"></a>Gründe für openxr

Mit openxr können Sie Engines entwickeln, die sowohl auf Holographic-Geräte als auch auf hololens 2 abzielen, und auf immersive Geräte wie Windows Mixed Reality-Headsets für Desktop-PCs. Mit openxr können Sie Code einmal schreiben, der dann über eine große Bandbreite von Hardwareplattformen portabel ist.

Die openxr-API verwendet ein Lade Modul, um Ihre Anwendung direkt mit der nativen Platt Form Unterstützung Ihres Headsets zu verbinden. Endbenutzer erhalten maximale Leistung und minimale Latenz, unabhängig davon, ob Sie eine gemischte Windows-Realität oder ein anderes Headset verwenden.

## <a name="what-is-openxr"></a>Was ist OpenXR?

Die openxr-API stellt die Kernfunktionen für die Vorhersage, den Frame und die räumliche Eingabe bereit, die Sie benötigen, um ein Modul zu erstellen, das sowohl Holographic als auch immersive Geräte als Ziel hat.

Weitere Informationen zur openxr-API finden Sie in der openxr 1,0- <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">Spezifikation</a>, <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">API-Referenz</a>und <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">kurz Referenzanleitung</a>.  Weitere Informationen finden Sie auf der <a href="https://www.khronos.org/openxr/" target="_blank">Seite zu Khronos openxr</a>.

Um den vollständigen Feature-Satz von hololens 2 als Ziel festzulegen, verwenden Sie auch herstellerübergreifende und herstellerspezifische openxr-Erweiterungen, die über openxr 1,0 Core hinausgehende Funktionen ermöglichen, wie z. b. die Nachverfolgung von Hand, die Augen Verfolgung, die räumliche Zuordnung und räumliche Anker. Weitere Informationen finden Sie im nachfolgenden [Abschnitt Roadmap](#roadmap) zu den weiter unten in diesem Jahr kommenden Erweiterungen.

Openxr ist nicht selbst ein gemischtes Reality-Engine.  Stattdessen ermöglicht openxr Modulen wie Unity und Unreal das einmalige Schreiben von portablen Code, der dann auf die nativen Plattformfunktionen des Holographic-oder immersiven Geräts des Benutzers zugreifen kann, je nachdem, welcher Anbieter diese Plattform erstellt hat.

## <a name="roadmap"></a>Roadmap

Die openxr-Spezifikation definiert einen Erweiterungsmechanismus, mit dem Lauf Zeit Implementierungen zusätzliche Funktionen über die in der Basisversion von <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">openxr 1,0</a>definierten [Kernfunktionen](#what-is-openxr) hinaus verfügbar machen können.

Es gibt drei Arten von openxr-Erweiterungen:
* **Hersteller Erweiterungen (z. b. `MSFT` ):** ermöglicht die herstellerspezifische Innovation in Hardware-oder Software Features.  Alle Lauf Zeit Hersteller können jederzeit eine Anbieter Erweiterung einführen und versenden.
  * **Experimental Vendor Extensions (z. b. `MSFT_preview` ):** experimentelle Lieferanten Erweiterungen, die in der Vorschau angezeigt werden, um Feedback zu erfassen.  `MSFT_preview` Erweiterungen sind nur für Entwickler Geräte vorgesehen und werden entfernt, wenn die tatsächliche Erweiterung ausgeliefert wird.  Um mit Ihnen zu experimentieren, können Sie [Vorschau Erweiterungen auf Ihrem Entwickler Gerät aktivieren](openxr-getting-started.md#using-preview-extensions).
* **Anbieter übergreifende `EXT` Erweiterungen:** Anbieter übergreifende Erweiterungen, die von mehreren Unternehmen definiert und implementiert werden.  Gruppen von Interessen Unternehmen können jederzeit ext-Erweiterungen einführen.
* **Offizielle `KHR` Erweiterungen:** offizielle Khronos-Erweiterungen, die im Rahmen einer Core-Spezifikation-Version ratifiziert wurden.  KHR-Erweiterungen werden durch dieselbe Lizenz abgedeckt wie die Kern Spezifikation selbst.

Ab Juli 2020 unterstützt die openxr-Laufzeit von Windows Mixed Reality eine Reihe von `MSFT` -und- `EXT` Erweiterungen, die den vollständigen Satz von hololens 2-Funktionen zu openxr-Anwendungen bringt:

| Featurebereich | Verfügbarkeit der Erweiterung |
|--------------|------------------------|
| Systeme und Sitzungen | **Openxr 1,0 Core-Spezifikation:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#instance" target="_blank">XrInstance</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#system" target="_blank">XrSystemId</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#session" target="_blank">XrSession</a></code> |
| [Verweis Plätze (Ansicht, lokal, Phase)](../../design/coordinate-systems.md) | **Openxr 1,0 Core-Spezifikation:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#spaces" target="_blank">XrSpace</a></code> |
| Konfigurationen anzeigen (Mono, Stereo) | **Openxr 1,0 Core-Spezifikation:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#view_configurations" target="_blank">XrView...</a></code> |
| [SwapChain](../platform-capabilities-and-apis/rendering.md)  +  [Frame zeitliche Steuerung](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) | **Openxr 1,0 Core-Spezifikation:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#rendering" target="_blank">XrSwapchain...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-synchronization" target="_blank">xrWaitFrame</a></code> |
| Kompositions Ebenen<br />(Projektion, Quad) | **Openxr 1,0 Core-Spezifikation:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#compositing" target="_blank">XrCompositionLayer...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-submission" target="_blank">xrEndFrame</a></code> |
| [Eingabe und Haptik](../../design/interaction-fundamentals.md) | **Openxr 1,0 Core-Spezifikation:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#input" target="_blank">XrAction...</a></code> |
| Integration von Direct3D 11 | **Offizielle `KHR` Erweiterung veröffentlicht:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D11_enable" target="_blank">XR_KHR_D3D11_enable</a></code> |
| Direct3D 12-Integration | **Offizielle `KHR` Erweiterung veröffentlicht:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D12_enable" target="_blank">XR_KHR_D3D12_enable</a></code> |
| [Ungebundener Referenzraum <br /> (weltweit skalierbar)](../../design/coordinate-systems.md#building-a-world-scale-experience) | **`MSFT` Erweiterung veröffentlicht:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_unbounded_reference_space" target="_blank">XR_MSFT_unbounded_reference_space</a></code> |
| [Raumanker](../../design/spatial-anchors.md) | **`MSFT` Erweiterung veröffentlicht:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_anchor">XR_MSFT_spatial_anchor</a></code> |
| [Hand Interaktion <br /> (Ziehpunkt/Ziel darstellen, Luft tippen, Reichweite)](../../design/hands-and-tools.md)<p>*Nur hololens 2*</p> | **`MSFT` Erweiterung veröffentlicht:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_interaction">XR_MSFT_hand_interaction</a></code> |
| [Handgelenke und Hand Mesh](../../design/hands-and-tools.md)<p>*Nur hololens 2*</p> | <p>**`EXT` Erweiterung in Laufzeit 102 veröffentlicht:**<code><br /><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_hand_tracking">XR_EXT_hand_tracking</a></code></p>**`MSFT` Erweiterung in Laufzeit 102 veröffentlicht:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_tracking_mesh">XR_MSFT_hand_tracking_mesh</a></code> |
| [Anvisieren mit den Augen](../../design/eye-tracking.md)<p>*Nur hololens 2*</p> | **`EXT` Erweiterung veröffentlicht:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_eye_gaze_interaction" target="_blank">XR_EXT_eye_gaze_interaction</a></code> |
| Interop mit anderen hololens-sdchen<br />(z. b. [QR](../platform-capabilities-and-apis/qr-code-tracking.md))<p>*Nur hololens 2*</p> | <p>**`MSFT` Erweiterung in Laufzeit 102 veröffentlicht:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_graph_bridge">XR_MSFT_spatial_graph_bridge</a></code></p><p>**`MSFT` Erweiterung in [Preview Runtime 104](openxr-getting-started.md#using-preview-extensions):**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_perception_anchor_interop_preview">XR_MSFT_perception_anchor_interop_preview</a></code></p> |
| [Transformation für gemischte Realität <br /> (drittes Rendering von PV-Kamera)](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)<p>*Nur hololens 2*</p> | **`MSFT` Erweiterungen, die in Laufzeit 102 veröffentlicht wurden:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_secondary_view_configuration">XR_MSFT_secondary_view_configuration</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_first_person_observer">XR_MSFT_first_person_observer</a></code> |
| Interop mit UWP-corewindow-API<br />(z. b. für Tastatur/Maus) | **`MSFT` Erweiterung in Laufzeit 103 veröffentlicht:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_holographic_window_attachment">XR_MSFT_holographic_window_attachment</a></code>
| Interaktions Profile für Motion Controller (Samsung Odyssee und HP Reverb G2) | **`MSFT` Erweiterungen, die in Laufzeit 103 veröffentlicht wurden:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_samsung_odyssey_controller">XR_EXT_samsung_odyssey_controller</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_hp_mixed_reality_controller">XR_EXT_hp_mixed_reality_controller</a></code> |
| [Bewegungs Controller-Rendering-Modelle](../../design/motion-controllers.md#rendering-the-motion-controller-model) | **`MSFT` Erweiterung in [Preview Runtime 104](openxr-getting-started.md#using-preview-extensions):**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_controller_model">XR_MSFT_controller_model</a></code> |
| [Szenen Verständnis (Flächen, Netze)](../../design/scene-understanding.md)<p>*Nur hololens 2*</p> | <p>**In der [Vorschau Laufzeit 102 oder](openxr-getting-started.md#using-preview-extensions)höher:**<br />Verwenden <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_graph_bridge">XR_MSFT_spatial_graph_bridge</a></code> mit [Scene Understanding SDK](../platform-capabilities-and-apis/scene-understanding-sdk.md)</p><p>**`MSFT_preview` Erweiterung in der Zukunft Vorschau Laufzeit** *(geplant)*</p> |
| Weitere herstellerübergreifende Erweiterungen | <p>**Offizielle `KHR` Erweiterungen veröffentlicht:**</p><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_composition_layer_depth" target="_blank">XR_KHR_composition_layer_depth</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_visibility_mask" target="_blank">XR_KHR_visibility_mask</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_win32_convert_performance_counter_time" target="_blank">XR_KHR_win32_convert_performance_counter_time</a></code><p>**`EXT` veröffentlichte Erweiterungen:**</p><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_win32_appcontainer_compatible" target="_blank">XR_EXT_win32_appcontainer_compatible</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_debug_utils" target="_blank">XR_EXT_debug_utils</a></code> |

Während einige dieser Erweiterungen als anbieterspezifische Erweiterungen gestartet werden können `MSFT` , arbeiten Microsoft und andere openxr-Lauf Zeit Anbieter zusammen, um Anbieter übergreifende Erweiterungen `EXT` oder `KHR` Erweiterungen für viele dieser Featurebereiche zu entwerfen. Mithilfe von herstellerübergreifenden Erweiterungen wird der Code, den Sie für diese Funktionen schreiben, für alle Lauf Zeit Hersteller übertragbar, wie bei der Kern Spezifikation.

## <a name="getting-started-with-openxr"></a>Erste Schritte mit OpenXR

![Screenshot von minecraft, der von einem Benutzer mit einem Mixed Reality-Headset abgespielt wird](images/openxr-minecraft.jpg)

*Die neue renderdragon-Engine von minecraft baut ihre Desktop-VR-Unterstützung mit openxr auf.*

Microsoft hat mit Unity-und Epic-spielen zusammengearbeitet, um sicherzustellen, dass die Zukunft der gemischten Realität offen ist, nicht nur für hololens 2, sondern auch für die gesamte Bandbreite von PC VR, einschließlich des [neuen Reverb G2-Headsets von HP](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).  Weitere Informationen zum Entwickeln von hololens (1. Gen) finden Sie in den [Anmerkungen](/hololens/hololens1-release-notes)zu dieser Version.

Weitere Informationen zu den ersten Schritten mit openxr in Unity, Unreal Engine oder ihrer eigenen Engine finden Sie unter!

### <a name="openxr-in-unity"></a>Openxr in Unity

Der unterstützte Unity-Entwicklungspfad für hololens 2, hololens (1 St Gen) und Windows Mixed Reality-Headsets ist **Unity 2019 LTS** mit dem vorhandenen WinRT-API-Back-End.  Sie können in [openxr mit Unity](../unity/openxr-getting-started.md)springen. Wenn Sie den neuen HP-Reverb-G2-Controller in einer Unity 2019-App als Ziel verwenden, lesen Sie die Dokumentation zu [HP-Reverb-G2](../unity/unity-reverb-g2-controllers.md).

Ab **Unity 2020 LTS** sendet [Unity ein openxr-Backend](https://forum.unity.com/threads/unitys-plans-for-openxr.993225/) , das hololens 2-und Windows Mixed Reality-Headsets unterstützt.  Dies umfasst die Unterstützung für openxr-Erweiterungen, die die [vollständigen Funktionen von hololens 2-und Windows Mixed Reality-Headsets](#roadmap)enthalten, einschließlich der Hand-/Uhrzeit-nach Verfolgung, räumlicher Anker und HP-Reverb-G2  MRTK-Unity Unterstützung für openxr befindet sich zurzeit in der [mrtk_development Verzweigung](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development) und steht neben diesem openxr-Vorschau Paket zur Verfügung.

Ab **Unity 2021** wird openxr das einzige unterstützte Unity-Back-End für hololens 2-und Windows Mixed Reality-Headsets als Ziel haben.

### <a name="openxr-in-unreal-engine"></a>Openxr in Unreal Engine

Ab **Unreal Engine 4,23** stehen die vollständige Unterstützung für hololens 2-und Windows Mixed Reality-Headsets über das Windows Mixed Reality (WinRT)-Plug-in zur Verfügung.

Unreal Engine 4,23 war außerdem die erste Haupt-Engine-Version für die Bereitstellung von Vorschau Unterstützung für openxr 1,0!  In der **Unreal Engine 4,26** sind Unterstützung für hololens 2, Windows Mixed Reality und andere Desktop-VR-Headsets über [das integrierte openxr-Plug-in von Unreal Engine](https://github.com/microsoft/Microsoft-OpenXR-Unreal)verfügbar.  Unreal Engine 4,26 wird auch mit dem ersten Satz von openxr-Erweiterungs-Plug-ins ausgeliefert, die Hand Interaktion und die Unterstützung von HP Reverb G2-Controllern ermöglichen, um den [vollständigen Featuresatz von hololens 2 und Windows Mixed Reality-Headsets](#roadmap)  Unreal Engine 4,26 ist heute in der Vorschauversion des [Epic Games Launcher](https://www.unrealengine.com/download/creators)verfügbar, wobei die offizielle Version später in diesem Jahr verfügbar ist.  MRTK-Unreal-Unterstützung für openxr steht neben diesem Release ebenfalls zur Verfügung.


### <a name="openxr-for-native-development"></a>Openxr für Native Entwicklung

Sie können mit OpenXR auf einem immersiven HoloLens 2- oder Windows Mixed Reality-Headset auf dem Desktop entwickeln.  Wenn Sie keinen Zugriff auf ein Headset haben, können Sie stattdessen den hololens 2-Emulator oder den Windows Mixed Reality-Simulator verwenden.

Informationen zum Einstieg in die Entwicklung von openxr-Anwendungen für hololens 2 oder immersive Windows Mixed Reality-Headsets finden Sie unter Erste Schritte [mit der openxr-Entwicklung](openxr-getting-started.md).

Eine Einführung in die Hauptkomponenten der openxr-API sowie Beispiele der realen Anwendungen, die openxr heute verwenden, finden Sie in diesem 60-minütigen exemplarischen Vorgehensweise:

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/OpenXR-Cross-platform-native-mixed-reality/player?format=ny]

## <a name="see-also"></a>Weitere Informationen

* <a href="https://www.khronos.org/openxr/" target="_blank">Weitere Informationen zu openxr</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">Openxr 1,0-Spezifikation</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">Openxr 1,0-API-Referenz</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">Openxr 1,0 kurz Referenzhandbuch</a>