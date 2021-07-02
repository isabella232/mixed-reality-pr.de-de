---
title: MRTK-Konfigurationsdialogfeld
description: Konfigurieren des MRTK in Unity Project
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Unity
ms.openlocfilehash: 50a0f40723c05e96f79eefab933942044afb22f1
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177329"
---
# <a name="mrtk-configuration-dialog"></a>MRTK-Konfigurationsdialogfeld

Das Dialogfeld MRTK-Konfiguration wird angezeigt, wenn Unity ein Projekt lädt, und es wird festgestellt, dass eine oder mehrere Konfigurationsoptionen die Aufmerksamkeit des Entwicklers erfordern.

![Später anwenden Ignorieren](../features/images/configuration-dialog/ConfigurationDialogHeader.png)

Klicken Sie auf die Schaltfläche Übernehmen, um die **Änderungen** zu übernehmen. Die **Schaltfläche Später** wird die Änderungen zurückverlangen, bis das Projekt zu einem späteren Zeitpunkt erneut geladen wird.

> [!NOTE]
> Das Konfigurationsdialogfeld wird erneut angezeigt, wenn mindestens eine der empfohlenen Einstellungen deaktiviert bleibt. Um dies zu verhindern, wenden Sie die gewünschten Optionen an, starten Sie das Dialogfeld dann über **Mixed Reality Toolkit** Utilities Configure Unity Project und klicken Sie  >    >   auf **Ignore (Ignorieren).** Dadurch wird verhindert, dass das Konfigurationsdialogfeld automatisch wieder angezeigt wird.

## <a name="common-settings"></a>Allgemeine Einstellungen

Alle Buildziele verwenden eine Sammlung gängiger Optionen.

![Allgemeine Einstellungen](../features/images/configuration-dialog/ConfigurationDialogCommonSettings.png)

### <a name="force-text-asset-serialization-and-enable-visible-meta-files"></a>Erzwingen der Serialisierung von Text-Assets und Aktivieren sichtbarer Metadateien

Diese Einstellungen vereinfachen die Arbeit mit Unity-Projekten und Quellcodeverwaltungssystemen (z.B. Git).

### <a name="enable-vr-supported"></a>Vr-Unterstützung aktivieren

**Unity 2018**

Konfiguriert die Virtual Reality Supported- und Virtual Reality SDK-Optionen in **Player Einstellungen**  >  **XR Einstellungen**.

### <a name="set-single-pass-instanced-rendering-path"></a>Festlegen des Renderingpfads für Single Pass Instanced

Konfiguriert den **Player Einstellungen**  >  **XR Einstellungen** Stereo Rendering Mode  >  **in** Single Pass **Instanced**.

### <a name="set-default-spatial-awareness-layer"></a>Festlegen der standardmäßigen Ebene für räumliche Wahrnehmung

Registriert Spatial Awareness als Ebene 31, um eine einfache und konsistente Konfiguration von Raycast- und physikalischen Optionen zu ermöglichen.

### <a name="audio-spatializer"></a>Audioraumisierer

Audioraumisierer sind die Komponenten, die die Leistung von Raumklang und positionsbezogenem Audio nutzen, um Mixed Reality-Umgebungen wirklich immersiver zu machen.

> [!NOTE]
> Wenn Sie den Audioraumisierer auf Keine festlegen, werden positionsbezogene Audiofeatures deaktiviert.

#### <a name="common-spatializers"></a>Gängige Spatializer

- Microsoft Spatializer

Microsoft hat spatializer bereitgestellt, der die Nutzung der Hardwarebeschleunigung auf HoloLens 2.

Dieser Spatializer ist über [NuGet](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/) [und](https://github.com/microsoft/spatialaudio-unity)GitHub.

Weitere Informationen zu Microsoft Spatializer finden Sie in der [Spatial Sound-Dokumentation.](/windows/mixed-reality/spatial-sound-in-unity)

- MS HRTF Spatializer

Microsoft Windows Spatializer, der von Unity als Teil der XR-Plattformpakete Windows Mixed Reality und Windows bereitgestellt wird.

- Audio zu Audioinhalten

Ein plattformübergreifender Spatializer von Google, der von Unity bereitgestellt wird.

Weitere Informationen finden Sie auf der [Dokumentationswebsite zu Audioinhalten.](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started)

## <a name="universal-windows-platform-settings"></a>Einstellungen Windows universellen Plattform

![UWP-Einstellungen](../features/images/configuration-dialog/ConfigurationDialogUWPSettings.png)

### <a name="uwp-capabilities"></a>UWP-Funktionen

Aktiviert bestimmte Anwendungsfunktionen für die universelle Windows Plattformanwendung. Mit diesen Funktionen kann die Plattform bestimmte Funktionen informieren und berechtigungen anfordern.

- Mikrofon

  Ermöglicht das Erfassen von Sound über das Mikrofon.

- Internetclient

  Ermöglicht die Unterstützung für den Zugriff auf Ressourcen im Internet.

- Räumliche Wahrnehmung

  Ermöglicht die Unterstützung für die Verwendung der realen Umgebung.

- Anvingen mit den Augen

  **Unity 2019.3 und neuer**

  Ermöglicht die Unterstützung für die Nachverfolgung des Anvings mit den Augen des Benutzers.

### <a name="avoid-unity-playersettingsgraphicsjob-crash"></a>Vermeiden des Absturzes von Unity "PlayerSettings.graphicsJob"

**Unity 2019.3 und neuer**

Wenn in der neuesten Version von Unity 2019 "Grafikaufträge" aktiviert ist, stürzt die App ab, wenn sie in einer HoloLens 2.
Diese Einstellung ist in Unity standardmäßig aktiviert. [](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)Solange dieser Fehler vorhanden ist (siehe Unity-Fehler), wird der Konfigurator grafikaufträge standardmäßig auf "false" festgelegt (sodass Apps, die in HoloLens 2 bereitgestellt werden, nicht abstürzen können).

## <a name="android-settings"></a>Einstellungen für Android

Konfigurationseinstellungen zur Unterstützung von AR-Anwendungen auf Android-Geräten.

![Android-Einstellungen](../features/images/configuration-dialog/ConfigurationDialogAndroidSettings.png)

### <a name="disable-multi-threaded-rendering"></a>Deaktivieren des Multithreadrenderings

Deaktiviert **player Einstellungen**  >  **Andere Einstellungen**  >  **Multithread-Rendering,** wie es für die AR-Unterstützung von Android erforderlich ist.

### <a name="set-minimum-api-level"></a>Festlegen der API-Mindestebene

Legt den Wert von **Player Einstellungen**  >  **Andere Einstellungen**  >  **API-Mindestebene fest,** um Betriebssystemanforderungen für AR-Anwendungen zu erzwingen.

## <a name="ios-settings"></a>Einstellungen für iOS

Konfigurationseinstellungen zur Unterstützung von AR-Anwendungen auf iOS-Geräten.

![iOS-Einstellungen](../features/images/configuration-dialog/ConfigurationDialogiOSSettings.png)

### <a name="set-required-os-version"></a>Festlegen der erforderlichen Betriebssystemversion

Legt den Wert von **Player Einstellungen**  >  **Andere Einstellungen**  >  **iOS-Mindestversion fest,** um Betriebssystemanforderungen für AR-Anwendungen zu erzwingen.

### <a name="set-required-architecture"></a>Festlegen der erforderlichen Architektur

Legt den Wert von **Player Einstellungen**  >  **Other Einstellungen** Architecture  >  **fest,** um Plattformanforderungen für AR-Anwendungen zu erzwingen.

### <a name="set-camera-usage-descriptions"></a>Festlegen von Kameraverwendungsbeschreibungen

Legt den Wert von **Player Einstellungen**  >  **Other Einstellungen** Camera Usage Description  >  **fest,** der zum Anfordern der Berechtigung zum Verwenden der Kamera des Geräts verwendet wird.
