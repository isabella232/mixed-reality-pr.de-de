---
title: OpenXR
description: Erstellen Sie eine Engine mit dem portablen OpenXR-API-Standard, und stellen Sie sie für Windows Mixed Reality und HoloLens 2 bereit.
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: OpenXR, Roadmap, Erweiterungen,Mapronos, BasicXRApp, DirectX, native, native App, benutzerdefinierte Engine, Middleware
ms.openlocfilehash: e9071f8b15f19be564b7c246244a5b7561aa5968
ms.sourcegitcommit: 12ea3fb2df4664c5efd07dcbb9040c2ff173afb6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2021
ms.locfileid: "113042241"
---
# <a name="openxr"></a>OpenXR

<img align="right" src="images/openxr.png" alt="OpenXR logo">

OpenXR ist ein offener, lizenzgebührenfreier API-Standard <a href="https://www.khronos.org/" target="_blank">vonIgenronos,</a>der Engines nativen Zugriff auf eine Reihe von Geräten im [Mixed Reality-Spektrum bietet.](../../discover/mixed-reality.md)

Sie können mit OpenXR auf einem virtuellen Computer HoloLens 2 oder Windows Mixed Reality immersives VR-Headset auf dem Desktop entwickeln.  Wenn Sie keinen Zugriff auf ein Headset haben, können Sie stattdessen den HoloLens 2 Emulator oder den Windows Mixed Reality Simulator verwenden.

## <a name="why-openxr"></a>Gründe für OpenXR

Mit OpenXR können Sie Engines für holografische Geräte wie HoloLens 2 und immersive VR-Geräte erstellen, z. B. Windows Mixed Reality Headsets für Desktop-PCs. Mit OpenXR können Sie Code schreiben, sobald dieser dann auf einer Vielzahl von Hardwareplattformen portierbar ist.

Die OpenXR-API verwendet ein Lader, um Ihre Anwendung direkt mit der Native Platform-Unterstützung Ihres Headsets zu verbinden. Endbenutzer erhalten maximale Leistung und minimale Latenz, unabhängig davon, ob sie ein Windows Mixed Reality oder ein anderes Headset verwenden.

## <a name="what-is-openxr"></a>Was ist OpenXR?

Die OpenXR-API bietet die wichtigsten Funktionen für die Vorhersage von Posen, frame-Timing und räumliche Eingabe, die Sie benötigen, um eine Engine zu erstellen, die sowohl holografische als auch immersive Geräte als Ziel verwenden kann.

Informationen zur OpenXR-API finden Sie in der OpenXR 1.0-Spezifikation, in der <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">API-Referenz</a>und in <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">der Kurzanleitung</a>. <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank"></a>  Weitere Informationen finden Sie auf der <a href="https://www.khronos.org/openxr/" target="_blank">OpenXR-Seite von Sollronos.</a>

Um den vollständigen Funktionssatz von HoloLens 2 als Ziel zu verwenden, verwenden Sie auch herstellerübergreifende und herstellerspezifische OpenXR-Erweiterungen, die zusätzliche Features über den OpenXR 1.0-Kern hinaus ermöglichen, z. B. artikulierte Handverfolgung, Eyetracking, räumliche Zuordnung und Raumanker. Weitere Informationen finden Sie im Abschnitt [Roadmap weiter](#roadmap) unten zu den Erweiterungen, die später in diesem Jahr verfügbar sind.

OpenXR ist selbst keine Mixed Reality-Engine.  Stattdessen ermöglicht OpenXR Engines wie Unity und Unreal, einmal portablen Code zu schreiben, der dann auf die nativen Plattformfeatures des holografischen oder immersiven Geräts des Benutzers zugreifen kann, unabhängig davon, welcher Anbieter diese Plattform erstellt hat.

## <a name="roadmap"></a>Roadmap

Die OpenXR-Spezifikation definiert einen Erweiterungsmechanismus, mit dem Laufzeit-Implementierer zusätzliche Funktionen verfügbar machen können, die über die in der <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0-Basisspezifikation definierten Kernfeatures hinausgehen.</a> [](#what-is-openxr)

Es gibt drei Arten von OpenXR-Erweiterungen:
* **Anbietererweiterungen (z. B. `MSFT` ):** Ermöglicht herstellerspezifische Innovationen in Hardware- oder Softwarefeatures.  Jeder Laufzeitanbieter kann jederzeit eine Anbietererweiterung einführen und versenden.
  * **Experimentelle Anbietererweiterungen (z. `MSFT_preview` B.):** Experimentelle Anbietererweiterungen, die in der Vorschau angezeigt werden, um Feedback zu erhalten.  `MSFT_preview` -Erweiterungen sind nur für Entwicklergeräte und werden entfernt, wenn die echte Erweiterung im Versand ist.  Um damit zu experimentieren, können Sie [Vorschauerweiterungen auf Ihrem Entwicklergerät aktivieren.](openxr-getting-started.md#using-preview-extensions)
* **Anbieterübergreifende `EXT` Erweiterungen:** Anbieterübergreifende Erweiterungen, die von mehreren Unternehmen definiert und implementiert werden.  Gruppen interessierter Unternehmen können jederzeit EXT-Erweiterungen einführen.
* **Offizielle `KHR` Erweiterungen:** Offizielle Versionserweiterungen für Versionserglosungen werden als Teil einer Kernversion von Spezifikationen veröffentlicht.  DIER-Erweiterungen werden durch die gleiche Lizenz abgedeckt wie die Kernspezifikation selbst.

Die Windows Mixed Reality OpenXR Runtime unterstützt eine Reihe von Erweiterungen und , die alle Funktionen HoloLens 2 `MSFT` `EXT` OpenXR-Anwendungen bieten:

| Featurebereich | Verfügbarkeit von Erweiterungen |
|--------------|------------------------|
| Systeme und Sitzungen | **OpenXR 1.0-Kernspezifikation:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#instance" target="_blank">XrInstance</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#system" target="_blank">XrSystemId</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#session" target="_blank">XrSession</a></code> |
| [Verweisräume (Ansicht, lokal, Phase)](../../design/coordinate-systems.md) | **OpenXR 1.0-Kernspezifikation:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#spaces" target="_blank">XrSpace</a></code> |
| Anzeigen von Konfigurationen (Mono, Stereo) | **OpenXR 1.0-Kernspezifikation:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#view_configurations" target="_blank">XrView...</a></code> |
| [Swapchains](../platform-capabilities-and-apis/rendering.md)  +  [Frame-Zeitsteuerung](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) | **OpenXR 1.0-Kernspezifikation:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#rendering" target="_blank">XrSwapchain...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-synchronization" target="_blank">xrWaitFrame</a></code> |
| Kompositionsebenen<br />(Projektion, Quad) | **OpenXR 1.0-Kernspezifikation:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#compositing" target="_blank">XrCompositionLayer...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-submission" target="_blank">xrEndFrame</a></code> |
| [Eingaben und Tonkodikate](../../design/interaction-fundamentals.md) | **OpenXR 1.0-Kernspezifikation:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#input" target="_blank">XrAction...</a></code> |
| Direct3D 11-Integration | **Offizielle `KHR` Veröffentlichte Erweiterung:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D11_enable" target="_blank">XR_KHR_D3D11_enable</a></code> |
| Direct3D 12-Integration | **Offizielle `KHR` Veröffentlichte Erweiterung:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D12_enable" target="_blank">XR_KHR_D3D12_enable</a></code> |
| [Ungebundener Referenzraum <br /> (Welterfahrungen)](../../design/coordinate-systems.md#building-a-world-scale-experience) | **`MSFT` Erweiterung veröffentlicht:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_unbounded_reference_space" target="_blank">XR_MSFT_unbounded_reference_space</a></code> |
| [Raumanker](../../design/spatial-anchors.md) | <p>**`MSFT` Erweiterung veröffentlicht:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_anchor">XR_MSFT_spatial_anchor</a></code></p><p>**`MSFT_preview`-Erweiterung in [der Vorschaulaufzeit 107:](openxr-getting-started.md#using-preview-extensions)**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_spatial_anchor_persistence_preview">XR_MSFT_spatial_anchor_persistence_preview</a></code></p> |
| [<br />Handinteraktion (Greif/Ziel-Pose, Tippen in die Luft, Greif)](../../design/hands-and-tools.md)<p>*nur HoloLens 2*</p> | **`MSFT` Erweiterung veröffentlicht:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_interaction">XR_MSFT_hand_interaction</a></code> |
| [Handartikulation + Handgitter](../../design/hands-and-tools.md)<p>*nur HoloLens 2*</p> | <p>**`EXT` Erweiterung veröffentlicht:**<code><br /><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_hand_tracking">XR_EXT_hand_tracking</a></code></p>**`MSFT` Erweiterung veröffentlicht:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_tracking_mesh">XR_MSFT_hand_tracking_mesh</a></code> |
| [Anvisieren mit den Augen](../../design/eye-tracking.md)<p>*nur HoloLens 2*</p> | **`EXT` Erweiterung veröffentlicht:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_eye_gaze_interaction" target="_blank">XR_EXT_eye_gaze_interaction</a></code> |
| [Mixed Reality-Aufnahme <br /> (drittes Rendern von der PV-Kamera)](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)<p>*nur HoloLens 2*</p> | **`MSFT` Erweiterungen veröffentlicht:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_secondary_view_configuration">XR_MSFT_secondary_view_configuration</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_first_person_observer">XR_MSFT_first_person_observer</a></code> |
| Interop mit anderen Mixed Reality SDKs<br />(z. B. [QR](../platform-capabilities-and-apis/qr-code-tracking.md)) | <p>**`MSFT` Erweiterung veröffentlicht:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_graph_bridge">XR_MSFT_spatial_graph_bridge</a></code></p><p>**`MSFT` Erweiterung, die in Runtime 105 veröffentlicht wurde:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_perception_anchor_interop">XR_MSFT_perception_anchor_interop</a></code></p> |
| Interop mit UWP CoreWindow-API<br />(z. B. für Tastatur/Maus) | **`MSFT` Erweiterung, die in Runtime 103 veröffentlicht wurde:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_holographic_window_attachment">XR_MSFT_holographic_window_attachment</a></code>
| Bewegungscontroller-Interaktionsprofile<br />(SamsungIgey und HP Reverb G2) | **`MSFT` Erweiterungen, die in Runtime 103 veröffentlicht wurden:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_samsung_odyssey_controller">XR_EXT_samsung_odyssey_controller</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_hp_mixed_reality_controller">XR_EXT_hp_mixed_reality_controller</a></code> |
| [Rendermodelle des Bewegungscontrollers](../../design/motion-controllers.md#rendering-the-motion-controller-model) | **`MSFT` Erweiterung, die in Runtime 104 veröffentlicht wurde:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_controller_model">XR_MSFT_controller_model</a></code> |
| [Szenenverständnis (Ebenen, Gitter)](../../design/scene-understanding.md)<p>*nur HoloLens 2*</p> | <p>**`MSFT` Erweiterung, die in Runtime 106 veröffentlicht wurde:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_scene_understanding">XR_MSFT_scene_understanding</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_scene_understanding_serialization">XR_MSFT_scene_understanding_serialization</a></code></p> |
| [Neuprojektionsmodi für Kompositionsebenen (Neuprojektion mit automatischer Planung oder ausschließlicher <br /> Ausrichtung)](../platform-capabilities-and-apis/hologram-stability.md#reprojection) | **`MSFT` Erweiterung, die in Runtime 106 veröffentlicht wurde:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_composition_layer_reprojection">XR_MSFT_composition_layer_reprojection</a></code> |
| Andere anbieterübergreifende Erweiterungen | <p>**Offizielle `KHR` Erweiterungen veröffentlicht:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_composition_layer_depth" target="_blank">XR_KHR_composition_layer_depth</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_visibility_mask" target="_blank">XR_KHR_visibility_mask</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_win32_convert_performance_counter_time" target="_blank">XR_KHR_win32_convert_performance_counter_time</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_composition_layer_color_scale_bias" target="_blank">XR_KHR_composition_layer_color_scale_bias</a></code></p><p>**`EXT` Erweiterungen veröffentlicht:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_win32_appcontainer_compatible" target="_blank">XR_EXT_win32_appcontainer_compatible</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_debug_utils" target="_blank">XR_EXT_debug_utils</a></code></p> |

Während einige dieser Erweiterungen als anbieterspezifische Erweiterungen beginnen können, arbeiten Microsoft und andere OpenXR-Laufzeitanbieter zusammen, um anbieterübergreifende Erweiterungen für viele dieser `MSFT` `EXT` `KHR` Featurebereiche zu entwerfen. Durch anbieterübergreifende Erweiterungen wird der Code, den Sie für diese Features schreiben, wie bei der Kernspezifikation für Laufzeitanbieter portabel.

## <a name="getting-started-with-openxr"></a>Erste Schritte mit OpenXR

![Screenshot: Minecraft, die von einem Benutzer mit einem Mixed Reality-Headset abgespielt wird](images/openxr-minecraft.jpg)

*Die neue RenderDragon-Engine von Minecraft hat die VR-Desktopunterstützung mit OpenXR erstellt.*

Microsoft hat mit Unity und Epic Games zusammengearbeit, um sicherzustellen, dass die Zukunft von Mixed Reality nicht nur für HoloLens 2, sondern auch für die gesamte Bandbreite von PC VR offen ist, einschließlich des neuen [Reverb G2-Headsets](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)von HP.  OpenXR unterstützt die herstellerübergreifende VR-Unterstützung für wichtige Titel, die heute versenden, z. B. Minecraft und Microsoft Flight Simulator!  Weitere Informationen zum Entwickeln für HoloLens (1. Generation) finden Sie in den [Versionshinweisen.](/hololens/hololens1-release-notes)

Lesen Sie weiter, um zu erfahren, wie Sie mit OpenXR in Unity, Unreal Engine oder Ihrer eigenen Engine beginnen können.

### <a name="openxr-in-unity"></a>OpenXR in Unity

Die aktuelle empfohlene Unity-Konfiguration von Microsoft für HoloLens 2 und Windows Mixed Reality Entwicklung ist **Unity 2020.3 LTS** mit dem neuesten Mixed Reality OpenXR-Plug-In.  Dieses Plug-In bietet Unterstützung für die OpenXR-Erweiterungen, die die [vollständigen Funktionen von HoloLens 2 und Windows Mixed Reality Headsets](#roadmap)aufleuchten, einschließlich Hand/Eye-Tracking, Raumanker und HP Reverb G2-Controller.  MRTK-Unity unterstützt OpenXR ab [MRTK 2.7.](../unity/tutorials/mr-learning-base-02.md?tabs=openxr#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)  Weitere Informationen zu den ersten Schritte mit Unity 2020 und OpenXR finden Sie unter [Auswählen einer Unity-Version.](../unity/choosing-unity-version.md)

Wenn Sie für HoloLens (1. Generation) entwickeln, müssen Sie **Unity 2019.4 LTS** weiterhin mit dem älteren WinRT-API-Back-End verwenden.  Wenn Sie den neuen HP Reverb G2-Controller in einer Unity 2019-App als Ziel verwenden, lesen Sie unsere [HP Reverb G2-Eingabedokumente.](../unity/unity-reverb-g2-controllers.md)

Ab **Unity 2021.2** ist OpenXR das einzige unterstützte Unity-Back-End für HoloLens 2 und Windows Mixed Reality Headsets.

### <a name="openxr-in-unreal-engine"></a>OpenXR in der Unreal-Engine

Unreal Engine 4.23 war die erste Hauptversion der Spiele-Engine, die Vorschauunterstützung für OpenXR 1.0 geliefert hat!  Ab **Unreal Engine 4.26** ist die Unterstützung für HoloLens 2, Windows Mixed Reality und andere VR-Desktop-Headsets über die integrierte OpenXR-Unterstützung der Unreal-Engine verfügbar.  Unreal Engine 4.26 unterstützt auch [das OpenXR-Erweiterungs-Plug-In](https://github.com/microsoft/Microsoft-OpenXR-Unreal)von Microsoft, wodurch Handinteraktion und HP Reverb G2-Controllerunterstützung ermöglicht werden, wodurch der [gesamte Funktionssatz von HoloLens 2 und Windows Mixed Reality Headsets entfacht](#roadmap)wird.  Unreal Engine 4.26 ist derzeit auf dem [Epic Games Launcher](https://www.unrealengine.com/download/creators)verfügbar, wobei MRTK-Unreal 0.12 OpenXR-Projekte unterstützt.

### <a name="openxr-for-native-development"></a>OpenXR für native Entwicklung

Sie können mit OpenXR auf einem HoloLens 2 oder Windows Mixed Reality immersive VR-Headset auf dem Desktop entwickeln.  Wenn Sie keinen Zugriff auf ein Headset haben, können Sie stattdessen den HoloLens 2 Emulator oder den Windows Mixed Reality Simulator verwenden.

Informationen zum Einstieg in die Entwicklung von OpenXR-Anwendungen für HoloLens 2 oder Windows Mixed Reality VR-Headsets finden Sie unter Erste Schritte mit der [OpenXR-Entwicklung.](openxr-getting-started.md)

Eine Tour durch alle Hauptkomponenten der OpenXR-API sowie Beispiele für die realen Anwendungen, die OpenXR heute verwenden, finden Sie in diesem 60-minütigen Video mit exemplarischen Vorgehensweisen:

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/OpenXR-Cross-platform-native-mixed-reality/player?format=ny]

## <a name="see-also"></a>Siehe auch

* <a href="https://www.khronos.org/openxr/" target="_blank">Weitere Informationen zu OpenXR</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0-Spezifikation</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">OpenXR 1.0-API-Referenz</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">OpenXR 1.0- Kurzübersicht</a>