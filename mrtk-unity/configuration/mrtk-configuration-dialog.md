---
title: Dialogfeld „MRTFK-Konfiguration“
description: Konfigurieren des MRTK im Unity-Projekt
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Unity
ms.openlocfilehash: ef326a4e4c9e34479cebacf3f3f575cd902ff24e
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144830"
---
# <a name="mrtk-project-configuration-dialog"></a>MRTK-Projektkonfigurationsdialogfeld

Das Dialogfeld MRTK-Konfiguration wird angezeigt, wenn Unity ein Projekt lädt, und es wird festgestellt, dass eine oder mehrere Konfigurationsoptionen die Aufmerksamkeit des Entwicklers erfordern.

![Später anwenden Ignorieren](../features/images/configuration-dialog/ConfigurationDialogHeader.png)

Klicken Sie auf die Schaltfläche Übernehmen, um die **Änderungen** zu übernehmen. Die **Schaltfläche Später** wird die Änderungen zurückverlangen, bis das Projekt zu einem späteren Zeitpunkt erneut geladen wird.

> [!NOTE]
> Das Konfigurationsdialogfeld wird erneut angezeigt, wenn mindestens eine der empfohlenen Einstellungen deaktiviert bleibt. Um dies zu verhindern, wenden Sie die gewünschten Optionen an, starten Sie das Dialogfeld dann über Mixed Reality Toolkit-Hilfsprogramme Unity-Projekt konfigurieren neu, und klicken Sie   >    >   **auf Ignorieren.** Dadurch wird verhindert, dass das Konfigurationsdialogfeld automatisch wieder angezeigt wird.

## <a name="common-settings"></a>Allgemeine Einstellungen

Alle Buildziele verwenden eine Sammlung gängiger Optionen.

![Allgemeine Einstellungen](../features/images/configuration-dialog/ConfigurationDialogCommonSettings.png)

### <a name="force-text-asset-serialization-and-enable-visible-meta-files"></a>Erzwingen der Serialisierung von Text-Assets und Aktivieren sichtbarer Metadateien

Diese Einstellungen vereinfachen die Arbeit mit Unity-Projekten und Quellcodeverwaltungssystemen (z.B. Git).

### <a name="enable-vr-supported"></a>Vr-Unterstützung aktivieren

**Unity 2018**

Konfiguriert die Virtual Reality Supported- und Virtual Reality SDK-Optionen unter **Player Settings**  >  **XR Settings (XR-Einstellungen für Playereinstellungen).**

### <a name="set-single-pass-instanced-rendering-path"></a>Festlegen des Single Pass Instanced-Renderingpfads

Konfiguriert den **Stereorenderingmodus**  >  **"Player Settings XR Settings" (Playereinstellungen XR-Einstellungen)**  >   auf Single **Pass Instanced**.

### <a name="set-default-spatial-awareness-layer"></a>Festlegen der standardmäßigen Ebene für räumliche Wahrnehmung

Registriert Spatial Awareness als Ebene 31, um eine einfache und konsistente Konfiguration von Raycast- und physikalischen Optionen zu ermöglichen.

### <a name="audio-spatializer"></a>Audio spatializer

Audio spatializers sind die Komponenten, die die Leistungsfähigkeit von Räumlichem Sound und Positionsaudio nutzen, um Mixed Reality-Erfahrungen wirklich immersiver zu machen.

> [!NOTE]
> Wenn Sie den Audio spatializer auf None festlegen, werden die Positionsaudiofeatures deaktiviert.

#### <a name="common-spatializers"></a>Allgemeine Spatializer

- Microsoft Spatializer

Microsoft hat einen Spatializer bereitgestellt, der die Nutzung der Hardwarebeschleunigung auf HoloLens 2 unterstützt.

Dieser Spatializer ist über [NuGet](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/) und [GitHub](https://github.com/microsoft/spatialaudio-unity)verfügbar.

Weitere Informationen zu Microsoft Spatializer finden Sie in der [Spatial Sound-Dokumentation.](/windows/mixed-reality/spatial-sound-in-unity)

- MS HRTF Spatializer

Microsoft Windows Spatializer, der von Unity als Teil der Pakete Windows Mixed Reality und Windows XR Platform bereitgestellt wird.

- Audioaudio

Ein plattformübergreifender Spatializer von Google, der von Unity bereitgestellt wird.

Weitere Informationen finden Sie auf der [Dokumentationswebsite zu 1000 Audio.](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started)

## <a name="universal-windows-platform-settings"></a>Universelle Windows-Plattform-Einstellungen

![UWP-Einstellungen](../features/images/configuration-dialog/ConfigurationDialogUWPSettings.png)

### <a name="uwp-capabilities"></a>UWP-Funktionen

Aktiviert bestimmte Anwendungsfunktionen für Universelle Windows-Plattform Anwendung. Mit diesen Funktionen kann die Plattform informieren und die Berechtigung anfordern, um bestimmte Funktionen zu aktivieren.

- Mikrofon

  Ermöglicht die Erfassung von Sound über das Mikrofon.

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
Diese Einstellung ist in Unity standardmäßig aktiviert. [](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)Solange dieser Fehler vorhanden ist (siehe Unity-Fehler), wird der Konfigurator grafikaufträge standardmäßig auf "false" festgelegt (sodass Apps, die in bereitgestellt werden, HoloLens 2 nicht abstürzen).

## <a name="android-settings"></a>Einstellungen für Android

Konfigurationseinstellungen zur Unterstützung von AR-Anwendungen auf Android-Geräten.

![Android-Einstellungen](../features/images/configuration-dialog/ConfigurationDialogAndroidSettings.png)

### <a name="disable-multi-threaded-rendering"></a>Deaktivieren des Multithreadrenderings

Deaktiviert **Playereinstellungen**  >  **Andere Einstellungen**  >  **Multithreadrendering,** wie für die AR-Unterstützung von Android erforderlich.

### <a name="set-minimum-api-level"></a>Festlegen der API-Mindestebene

Legt den Wert von **Playereinstellungen** Andere Einstellungen  >    >  **Mindest-API-Ebene fest,** um Betriebssystemanforderungen für AR-Anwendungen zu erzwingen.

## <a name="ios-settings"></a>Einstellungen für iOS

Konfigurationseinstellungen zur Unterstützung von AR-Anwendungen auf iOS-Geräten.

![iOS-Einstellungen](../features/images/configuration-dialog/ConfigurationDialogiOSSettings.png)

### <a name="set-required-os-version"></a>Festlegen der erforderlichen Betriebssystemversion

Legt den Wert player **settings** Other Settings Target minimum iOS Version fest, um Betriebssystemanforderungen für  >    >   AR-Anwendungen zu erzwingen.

### <a name="set-required-architecture"></a>Festlegen der erforderlichen Architektur

Legt den Wert von **Player settings Other** Settings  >  **Architecture**  >  **fest,** um Plattformanforderungen für AR-Anwendungen zu erzwingen.

### <a name="set-camera-usage-descriptions"></a>Festlegen von Kameranutzungsbeschreibungen

Legt den Wert von **Playereinstellungen**  >  **Andere Einstellungen**  >  **Kameraverwendungsbeschreibung** fest, die verwendet wird, um die Berechtigung zum Verwenden der Kamera des Geräts anzufordern.