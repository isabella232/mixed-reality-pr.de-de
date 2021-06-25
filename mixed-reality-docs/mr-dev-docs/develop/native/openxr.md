---
title: OpenXR
description: Erstellen Sie eine Engine mithilfe des portablen OpenXR-API-Standards, und stellen Sie sie für Windows Mixed Reality und HoloLens 2 Headsets bereit.
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: OpenXR, Roadmap, Erweiterungen, Sollronos, BasicXRApp, DirectX, nativ, native App, benutzerdefinierte Engine, Middleware
ms.openlocfilehash: 8374cda738cc5b257338728f7d777f546768e71b
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906836"
---
# <a name="openxr"></a>OpenXR

<img align="right" src="images/openxr.png" alt="OpenXR logo">

OpenXR ist ein offener lizenzfreier API-Standard von <a href="https://www.khronos.org/" target="_blank">Mixronos,</a>der Engines nativen Zugriff auf eine Reihe von Geräten im [Mixed Reality-Spektrum](../../discover/mixed-reality.md)bietet.

Sie können mit OpenXR auf einem immersiven HoloLens 2- oder Windows Mixed Reality-Headset auf dem Desktop entwickeln.  Wenn Sie keinen Zugriff auf ein Headset haben, können Sie stattdessen den HoloLens 2 Emulator oder den Windows Mixed Reality Simulator verwenden.

## <a name="why-openxr"></a>Warum OpenXR?

Mit OpenXR können Sie Engines erstellen, die sowohl holografische Geräte wie HoloLens 2 als auch immersive Geräte wie Windows Mixed Reality Headsets für Desktop-PCs als Ziel verwenden. Mit OpenXR können Sie Code schreiben, der dann über eine Vielzahl von Hardwareplattformen portiert ist.

Die OpenXR-API verwendet ein Ladeprogramm, um Ihre Anwendung direkt mit der nativen Plattformunterstützung Ihres Headsets zu verbinden. Endbenutzer erhalten maximale Leistung und minimale Latenz, unabhängig davon, ob sie ein Windows Mixed Reality oder ein anderes Headset verwenden.

## <a name="what-is-openxr"></a>Was ist OpenXR?

Die OpenXR-API stellt die Kernfunktionen für die Vorhersage der Pose, die Framezeit und die räumliche Eingabe bereit, die Sie benötigen, um eine Engine zu erstellen, die sowohl holografische als auch immersive Geräte als Ziel verwenden kann.

Informationen zur OpenXR-API finden Sie in der OpenXR 1.0-Spezifikation, in der <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">API-Referenz</a>und in der <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank"></a> <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">Kurzübersicht.</a>  Weitere Informationen finden Sie auf der <a href="https://www.khronos.org/openxr/" target="_blank">OpenXR-Seite von Ronronos.</a>

Um den vollständigen Featuresatz von HoloLens 2 als Ziel festzulegen, verwenden Sie auch herstellerübergreifende und herstellerspezifische OpenXR-Erweiterungen, die zusätzliche Features über den OpenXR 1.0-Kern hinaus ermöglichen, z. B. artikulierte Handverfolgung, Blickverfolgung, räumliche Zuordnung und Raumanker. Weitere Informationen zu den Erweiterungen, die später in diesem Jahr folgen, finden Sie weiter unten im [Abschnitt Roadmap.](#roadmap)

OpenXR ist selbst keine Mixed Reality-Engine.  Stattdessen ermöglicht OpenXR Es Engines wie Unity und Unreal, einmal portablen Code zu schreiben, der dann auf die nativen Plattformfeatures des holografischen oder immersiven Geräts des Benutzers zugreifen kann, unabhängig davon, welcher Anbieter diese Plattform erstellt hat.

## <a name="roadmap"></a>Roadmap

Die OpenXR-Spezifikation definiert einen Erweiterungsmechanismus, mit dem Laufzeit implementer zusätzliche Funktionen über die [kernigen Features](#what-is-openxr) hinaus verfügbar machen können, die in der <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0-Basisspezifikation</a>definiert sind.

Es gibt drei Arten von OpenXR-Erweiterungen:
* **Anbietererweiterungen (z. B. `MSFT` ):** Ermöglicht herstellerspezifische Innovationen in Hardware- oder Softwarefeatures.  Jeder Runtimeanbieter kann jederzeit eine Anbietererweiterung einführen und versenden.
  * **Experimentelle Anbietererweiterungen (z. B. `MSFT_preview` ):** Experimentelle Anbietererweiterungen, die in der Vorschau angezeigt werden, um Feedback zu sammeln.  `MSFT_preview` -Erweiterungen sind nur für Entwicklergeräte vorgesehen und werden entfernt, wenn die echte Erweiterung ausgeliefert wird.  Um mit ihnen zu experimentieren, können Sie [Vorschauerweiterungen auf Ihrem Entwicklergerät aktivieren.](openxr-getting-started.md#using-preview-extensions)
* **Herstellerübergreifende `EXT` Erweiterungen:** Herstellerübergreifende Erweiterungen, die von mehreren Unternehmen definiert und implementiert werden.  Gruppen interessierter Unternehmen können EXT-Erweiterungen jederzeit einführen.
* **Offizielle `KHR` Erweiterungen:** Offizielle Erweiterungen von Ronronos, die als Teil eines Kernspezifikations-Release veröffentlicht wurden.  DIE LIZENZR-Erweiterungen werden durch die gleiche Lizenz abgedeckt wie die Kernspezifikation selbst.

Die Windows Mixed Reality OpenXR Runtime unterstützt eine Reihe von `MSFT` - und `EXT` -Erweiterungen, die den vollständigen Satz von HoloLens 2 Features für OpenXR-Anwendungen bieten:

| Featurebereich | Verfügbarkeit von Erweiterungen |
|--------------|------------------------|
| Systeme + Sitzungen | **OpenXR 1.0-Kernspezifikation:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#instance" target="_blank">XrInstance</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#system" target="_blank">XrSystemId</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#session" target="_blank">XrSession</a></code> |
| [Verweisräume (View, Local, Stage)](../../design/coordinate-systems.md) | **OpenXR 1.0-Kernspezifikation:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#spaces" target="_blank">XrSpace</a></code> |
| Anzeigen von Konfigurationen (Mono, Stereo) | **OpenXR 1.0-Kernspezifikation:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#view_configurations" target="_blank">XrView...</a></code> |
| [Swapchains](../platform-capabilities-and-apis/rendering.md)  +  [Frame-Zeitsteuerung](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) | **OpenXR 1.0-Kernspezifikation:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#rendering" target="_blank">XrSwapchain...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-synchronization" target="_blank">xrWaitFrame</a></code> |
| Kompositionsebenen<br />(Projektion, Quader) | **OpenXR 1.0-Kernspezifikation:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#compositing" target="_blank">XrCompositionLayer...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-submission" target="_blank">xrEndFrame</a></code> |
| [Eingabe und Haptik](../../design/interaction-fundamentals.md) | **OpenXR 1.0-Kernspezifikation:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#input" target="_blank">XrAction...</a></code> |
| Direct3D 11-Integration | **Offizielle `KHR` Erweiterung veröffentlicht:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D11_enable" target="_blank">XR_KHR_D3D11_enable</a></code> |
| Direct3D 12-Integration | **Offizielle `KHR` Erweiterung veröffentlicht:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D12_enable" target="_blank">XR_KHR_D3D12_enable</a></code> |
| [Ungebundener Referenzraum <br /> (Welterfahrungen)](../../design/coordinate-systems.md#building-a-world-scale-experience) | **`MSFT` Erweiterung veröffentlicht:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_unbounded_reference_space" target="_blank">XR_MSFT_unbounded_reference_space</a></code> |
| [Raumanker](../../design/spatial-anchors.md) | **`MSFT` Erweiterung veröffentlicht:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_anchor">XR_MSFT_spatial_anchor</a></code> |
| [Handinteraktion <br /> (Klammer/Zielpose, Tippen in die Luft, Greifen)](../../design/hands-and-tools.md)<p>*nur HoloLens 2*</p> | **`MSFT` Erweiterung veröffentlicht:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_interaction">XR_MSFT_hand_interaction</a></code> |
| [Handartikulation + Handgitter](../../design/hands-and-tools.md)<p>*nur HoloLens 2*</p> | <p>**`EXT` Erweiterung, die in Runtime 102 veröffentlicht wurde:**<code><br /><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_hand_tracking">XR_EXT_hand_tracking</a></code></p>**`MSFT` Erweiterung, die in Runtime 102 veröffentlicht wurde:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_tracking_mesh">XR_MSFT_hand_tracking_mesh</a></code> |
| [Anvisieren mit den Augen](../../design/eye-tracking.md)<p>*nur HoloLens 2*</p> | **`EXT` Erweiterung veröffentlicht:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_eye_gaze_interaction" target="_blank">XR_EXT_eye_gaze_interaction</a></code> |
| Interop mit anderen HoloLens SDKs<br />(z. B. [QR)](../platform-capabilities-and-apis/qr-code-tracking.md)<p>*nur HoloLens 2*</p> | <p>**`MSFT` Erweiterung, die in Runtime 102 veröffentlicht wurde:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_graph_bridge">XR_MSFT_spatial_graph_bridge</a></code></p><p>**`MSFT` -Erweiterung in Runtime 105:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_perception_anchor_interop">XR_MSFT_perception_anchor_interop</a></code></p> |
| [Mixed Reality-Aufnahme <br /> (drittes Rendern von PV-Kameras)](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)<p>*nur HoloLens 2*</p> | **`MSFT` Erweiterungen, die in Runtime 102 veröffentlicht wurden:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_secondary_view_configuration">XR_MSFT_secondary_view_configuration</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_first_person_observer">XR_MSFT_first_person_observer</a></code> |
| Interop mit der UWP CoreWindow-API<br />(z. B. für Tastatur/Maus) | **`MSFT` Erweiterung, die in Runtime 103 veröffentlicht wurde:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_holographic_window_attachment">XR_MSFT_holographic_window_attachment</a></code>
| Interaktionsprofile für Motion-Controller<br />(Samsung Odyssey und HP Reverb G2) | **`MSFT` Erweiterungen, die in Runtime 103 veröffentlicht wurden:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_samsung_odyssey_controller">XR_EXT_samsung_odyssey_controller</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_hp_mixed_reality_controller">XR_EXT_hp_mixed_reality_controller</a></code> |
| [Rendermodelle des Motion-Controllers](../../design/motion-controllers.md#rendering-the-motion-controller-model) | **`MSFT` Erweiterung, die in Runtime 104 veröffentlicht wurde:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_controller_model">XR_MSFT_controller_model</a></code> |
| [Szenenverständnis (Ebenen, Gitternetze)](../../design/scene-understanding.md)<p>*nur HoloLens 2*</p> | <p>**Ab Runtime 102:**<br />Verwenden <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_graph_bridge">XR_MSFT_spatial_graph_bridge</a></code> mit dem Scene Understanding [SDK](../platform-capabilities-and-apis/scene-understanding-sdk.md)</p><p>**`MSFT` -Erweiterung in [preview runtime 105](openxr-getting-started.md#using-preview-extensions):**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_scene_understanding_preview2">XR_MSFT_scene_understanding_preview2</a></code><br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_scene_understanding_serialization_preview">XR_MSFT_scene_understanding_serialization_preview</a></code></p> |
| [Neuprojektionsmodi der Kompositionsebene <br /> (automatische Planar- oder nur Ausrichtungsreprojektion)](../platform-capabilities-and-apis/hologram-stability.md#reprojection) | **`MSFT` -Erweiterung in [preview runtime 105](openxr-getting-started.md#using-preview-extensions):**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_composition_layer_reprojection_preview">XR_MSFT_composition_layer_reprojection_preview</a></code> |
| Andere herstellerübergreifende Erweiterungen | <p>**Offizielle `KHR` Erweiterungen veröffentlicht:**</p><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_composition_layer_depth" target="_blank">XR_KHR_composition_layer_depth</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_visibility_mask" target="_blank">XR_KHR_visibility_mask</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_win32_convert_performance_counter_time" target="_blank">XR_KHR_win32_convert_performance_counter_time</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_composition_layer_color_scale_bias" target="_blank">XR_KHR_composition_layer_color_scale_bias</a></code><p>**`EXT` Erweiterungen veröffentlicht:**</p><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_win32_appcontainer_compatible" target="_blank">XR_EXT_win32_appcontainer_compatible</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_debug_utils" target="_blank">XR_EXT_debug_utils</a></code> |

Während einige dieser Erweiterungen als herstellerspezifische Erweiterungen beginnen `MSFT` können, arbeiten Microsoft und andere OpenXR-Runtimeanbieter zusammen, um herstellerübergreifende `EXT` oder `KHR` Erweiterungen für viele dieser Featurebereiche zu entwerfen. Herstellerübergreifende Erweiterungen machen den Code, den Sie für diese Features schreiben, wie bei der Kernspezifikation für Laufzeitanbieter portierbar.

## <a name="getting-started-with-openxr"></a>Erste Schritte mit OpenXR

![Screenshot: Wird von einem Benutzer mit einem Mixed Reality-Headset wiedergegeben](images/openxr-minecraft.jpg)

*Die neue RenderDragon-Engine von Mine hat ihre Desktop-VR-Unterstützung mit OpenXR erstellt!*

Microsoft hat mit Unity und Epic Games gearbeitet, um sicherzustellen, dass die Zukunft von Mixed Reality offen ist, nicht nur für HoloLens 2, sondern auch für die gesamte Breite des PC-VR, einschließlich des [neuen Reverb G2-Headsets](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)von HP.  OpenXR unterstützt die herstellerübergreifende VR-Unterstützung für den heute ausgelieferten Haupttitel, z. B. "Apk" und "Microsoft Flight Simulator".  Weitere Informationen zum Entwickeln für HoloLens (1. Generation) finden Sie in den [Versionshinweisen.](/hololens/hololens1-release-notes)

Lesen Sie weiter, um zu erfahren, wie Sie mit OpenXR in Unity, Unreal Engine oder Ihrer eigenen Engine beginnen können.

### <a name="openxr-in-unity"></a>OpenXR in Unity

Der unterstützte Unity-Entwicklungspfad für HoloLens 2, HoloLens (1. Generation) und Windows Mixed Reality-Headsets ist **unity 2019 LTS** mit dem vorhandenen WinRT-API-Back-End.  Sie können mit [Unity zu OpenXR springen.](../unity/xr-project-setup.md) Wenn Sie den neuen HP Reverb G2-Controller in einer Unity 2019-App als Ziel verwenden, lesen Sie unsere [HP Reverb G2-Eingabedokumenten.](../unity/unity-reverb-g2-controllers.md)

Ab **Unity 2020 LTS** liefert Unity ein [OpenXR-Back-End,](https://forum.unity.com/threads/unitys-plans-for-openxr.993225/) das HoloLens 2 und Windows Mixed Reality unterstützt.  Dies umfasst unterstützung für die OpenXR-Erweiterungen, die alle Funktionen von HoloLens 2- und [Windows Mixed Reality-Headsets](#roadmap)wie Hand/Eye-Tracking, Raumanker und HP Reverb G2-Controllern aufspüren.  MRTK-Unity unterstützt OpenXR ab [MRTK 2.7.](../unity/tutorials/mr-learning-base-02.md?tabs=openxr#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)  Weitere Informationen zum aktuellen Status der Unity 2020 LTS-Unterstützung für HoloLens 2 finden Sie unter [Auswählen einer Unity-Version.](../unity/choosing-unity-version.md)

Ab **Unity 2021** wird OpenXR zum einzigen unterstützten Unity-Back-End für HoloLens 2 und Windows Mixed Reality Headsets.

### <a name="openxr-in-unreal-engine"></a>OpenXR in Unreal Engine

Ab **Unreal Engine 4.23** ist vollständige Unterstützung für HoloLens 2- und Windows Mixed Reality-Headsets über das Windows Mixed Reality-Plug-In (WinRT) verfügbar.

Unreal Engine 4.23 war auch das erste große Spiel-Engine-Release, das Vorschauunterstützung für OpenXR 1.0 bietet!  Ab **Unreal Engine 4.26** ist die Unterstützung für HoloLens 2, Windows Mixed Reality und andere VR-Desktop-Headsets über die integrierte OpenXR-Unterstützung der Unreal Engine verfügbar.  Die Unreal Engine 4.26 unterstützt auch das OpenXR-Erweiterungs-Plug-In von [Microsoft,](https://github.com/microsoft/Microsoft-OpenXR-Unreal)das Handinteraktion und HP Reverb G2-Controllerunterstützung ermöglicht und den gesamten Funktionssatz von HoloLens 2- und [Windows Mixed Reality-Headsets](#roadmap)aktiviert.  Unreal Engine 4.26 ist heute im [Epic Games Launcher](https://www.unrealengine.com/download/creators)verfügbar, und MRTK-Unreal im April verfügbar.


### <a name="openxr-for-native-development"></a>OpenXR für die native Entwicklung

Sie können mit OpenXR auf einem immersiven HoloLens 2- oder Windows Mixed Reality-Headset auf dem Desktop entwickeln.  Wenn Sie keinen Zugriff auf ein Headset haben, können Sie stattdessen den HoloLens 2 Emulator oder den Windows Mixed Reality Simulator verwenden.

Informationen zum Einstieg in die Entwicklung von OpenXR-Anwendungen für HoloLens 2 oder immersive Windows Mixed Reality-Headsets finden Sie unter Erste Schritte mit [der OpenXR-Entwicklung.](openxr-getting-started.md)

Einen Tour durch alle Hauptkomponenten der OpenXR-API sowie Beispiele für reale Anwendungen, die OpenXR heute verwenden, finden Sie in diesem 60-minütigen Video mit exemplarischer Vorgehensweise:

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/OpenXR-Cross-platform-native-mixed-reality/player?format=ny]

## <a name="see-also"></a>Siehe auch

* <a href="https://www.khronos.org/openxr/" target="_blank">Weitere Informationen zu OpenXR</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0-Spezifikation</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">OpenXR 1.0-API-Referenz</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">Kurzanleitung zu OpenXR 1.0</a>