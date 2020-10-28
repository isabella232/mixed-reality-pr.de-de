---
title: OpenXR
description: Erstellen Sie eine Engine mithilfe des portablen openxr-API-Standards, und stellen Sie Sie für Windows Mixed Reality-und hololens 2-Headsets bereit.
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: Openxr, Khronos, basicxrapp, DirectX, Native, Native APP, benutzerdefinierte Engine, Middleware
ms.openlocfilehash: 519d363c49f86a47eeaa5872c6f7911e12276c99
ms.sourcegitcommit: c199872c11adae7de24929ed043ea90dea087b3e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903102"
---
# <a name="openxr"></a>OpenXR

<img align="right" src="images/openxr.png" alt="OpenXR logo">

Openxr ist ein offener, kostenloser API-Standard von <a href="https://www.khronos.org/" target="_blank">Khronos</a> , der Modulen systemeigenen Zugriff auf eine große Bandbreite von Geräten von vielen Anbietern ermöglicht, die sich über das [gemischte Reality-Spektrum](../../discover/mixed-reality.md)erstrecken.

Sie können mit OpenXR auf einem immersiven HoloLens 2- oder Windows Mixed Reality-Headset auf dem Desktop entwickeln.  Wenn Sie keinen Zugriff auf ein Headset haben, können Sie stattdessen den hololens 2-Emulator oder den Windows Mixed Reality-Simulator verwenden.

## <a name="why-openxr"></a>Gründe für openxr

Mit openxr können Sie Engines entwickeln, die sowohl auf Holographic-Geräte (wie hololens 2) abzielen, die digitale Inhalte in der realen Welt platzieren, als wären Sie tatsächlich vorhanden, als auch immersive Geräte (z. b. Windows Mixed Reality-Headsets für Desktop-PCs), die die physische Welt ausblenden und durch eine digitale Umgebung ersetzen.  Mit openxr können Sie Code einmal schreiben, der dann über eine große Bandbreite von Hardwareplattformen portabel ist.

Die openxr-API verwendet ein Lade Modul, das Ihre Anwendung direkt mit der nativen Platt Form Unterstützung Ihres Headsets verbindet.  Dies bietet Endbenutzern maximale Leistung und minimale Latenzzeit, unabhängig davon, ob Sie ein Windows Mixed Reality-Headset oder ein anderes Headset verwenden.

## <a name="what-is-openxr"></a>Was ist OpenXR?

Die openxr-API stellt die Kernfunktionen für Vorhersage, Frame Timing und räumliche Eingaben bereit, die Sie zum Erstellen eines Moduls benötigen, das sowohl Holographic-Geräte als auch hololens 2 und immersive Geräte wie Windows Mixed Reality-Headsets als Ziel hat.

Informationen zur openxr-API finden Sie in der openxr 1,0- <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">Spezifikation</a>, der <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">API-Referenz</a> und der <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">kurz Referenzanleitung</a>.  Weitere Informationen finden Sie auf der <a href="https://www.khronos.org/openxr/" target="_blank">Seite zu Khronos openxr</a>.

Um den vollständigen Feature-Satz von hololens 2 als Ziel festzulegen, verwenden Sie auch herstellerübergreifende und herstellerspezifische openxr-Erweiterungen, die über openxr 1,0 Core hinausgehende Features ermöglichen, wie z. b. die Nachverfolgung von Hand, die Augen Verfolgung, die räumliche Zuordnung und räumliche Anker.  Weitere Informationen zu den weiter unten in diesem Jahr anstehenden Erweiterungen finden Sie im nachfolgenden [Abschnitt Roadmap](#roadmap) .

Beachten Sie, dass openxr nicht selbst ein gemischtes Reality-Engine ist.  Stattdessen ermöglicht openxr Modulen wie Unity und Unreal das einmalige Schreiben von portablen Code, der dann auf die nativen Plattformfunktionen des Holographic-oder immersiven Geräts des Benutzers zugreifen kann, unabhängig davon, welcher Anbieter diese Plattform erstellt hat.

## <a name="roadmap"></a>Roadmap

Die openxr-Spezifikation definiert einen Erweiterungsmechanismus, mit dem Lauf Zeit Implementierungen zusätzliche Funktionen über die in der Basisversion von <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">openxr 1,0</a>definierten [Kernfunktionen](#what-is-openxr) hinaus verfügbar machen können.

Es gibt drei Arten von openxr-Erweiterungen:
* **Lieferanten Erweiterungen (z. b. `MSFT` ):** ermöglicht die herstellerspezifische Innovation in Hardware-oder Software Features.  Alle Lauf Zeit Hersteller können jederzeit eine Anbieter Erweiterung einführen und versenden.
  * **Experimentelle Lieferanten Erweiterungen (z. b. `MSFT_preview` ):** experimentelle Lieferanten Erweiterungen, die in der Vorschau angezeigt werden.  `MSFT_preview` Erweiterungen sind nur für Entwickler Geräte vorgesehen und werden entfernt, wenn die tatsächliche Erweiterung ausgeliefert wird.  Um mit Ihnen zu experimentieren, können Sie [Vorschau Erweiterungen auf Ihrem Entwickler Gerät aktivieren](openxr-getting-started.md#using-preview-extensions).
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

Während einige dieser Erweiterungen als anbieterspezifische Erweiterungen gestartet werden können `MSFT` , arbeiten Microsoft und andere openxr-Lauf Zeit Anbieter zusammen, um Anbieter übergreifende Erweiterungen `EXT` oder `KHR` Erweiterungen für viele dieser Featurebereiche zu entwerfen.  Dadurch kann der Code, den Sie für diese Funktionen schreiben, über Lauf Zeit Anbieter hinweg portabel sein, ebenso wie bei der Kern Spezifikation.

## <a name="get-started-with-openxr"></a>Erste Schritte mit OpenXR

Sie können mit OpenXR auf einem immersiven HoloLens 2- oder Windows Mixed Reality-Headset auf dem Desktop entwickeln.  Wenn Sie keinen Zugriff auf ein Headset haben, können Sie stattdessen den hololens 2-Emulator oder den Windows Mixed Reality-Simulator verwenden.

Informationen zum Einstieg in die Entwicklung von openxr-Anwendungen für hololens 2 oder immersive Windows Mixed Reality-Headsets finden Sie unter Erste Schritte [mit der openxr-Entwicklung](openxr-getting-started.md).

Eine Einführung in die Hauptkomponenten der openxr-API sowie Beispiele der realen Anwendungen, die openxr heute verwenden, finden Sie in diesem 60-minütigen exemplarischen Vorgehensweise:

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/OpenXR-Cross-platform-native-mixed-reality/player?format=ny]

## <a name="see-also"></a>Weitere Informationen

* <a href="https://www.khronos.org/openxr/" target="_blank">Weitere Informationen zu openxr</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">Openxr 1,0-Spezifikation</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">Openxr 1,0-API-Referenz</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">Openxr 1,0 kurz Referenzhandbuch</a>
