---
title: MRTK-Konfigurationsdialogfeld
description: Konfigurieren von MRTK im Unity-Projekt
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Unity
ms.openlocfilehash: fd05f7f3b579522a1225e11b0411b255a43e1e3f
ms.sourcegitcommit: bb9f54f3e872a5464a5d9ba88b7ab5b8896efd82
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2021
ms.locfileid: "110345093"
---
# <a name="mrtk-project-configuration-dialog"></a>MRTK-Projektkonfigurationsdialogfeld

Das MRTK-Konfigurationsdialogfeld wird angezeigt, wenn Unity ein Projekt lädt, und es wird festgestellt, dass eine oder mehrere Konfigurationsoptionen die Aufmerksamkeit des Entwicklers erfordern.

![Später anwenden Ignorieren](../features/images/configuration-dialog/ConfigurationDialogHeader.png)

Klicken Sie auf die Schaltfläche **Übernehmen,** um die Änderungen zu übernehmen. Mit der Schaltfläche **Später** werden die Änderungen zurückgesetzt, bis das Projekt zu einem späteren Zeitpunkt erneut geladen wird.

> [!NOTE]
> Das Konfigurationsdialogfeld wird erneut angezeigt, wenn mindestens eine der empfohlenen Einstellungen deaktiviert bleibt. Um dies zu verhindern, wenden Sie die gewünschten Optionen an, starten Sie dann das Dialogfeld über **Mixed Reality**  >  **Toolkit-Hilfsprogramme**  >  **Unity-Projekt konfigurieren** neu, und klicken Sie auf **Ignorieren.** Dadurch wird verhindert, dass das Konfigurationsdialogfeld automatisch erneut angezeigt wird.

## <a name="common-settings"></a>Allgemeine Einstellungen

Alle Buildziele teilen sich eine Sammlung allgemeiner Optionen.

![Allgemeine Einstellungen](../features/images/configuration-dialog/ConfigurationDialogCommonSettings.png)

### <a name="force-text-asset-serialization-and-enable-visible-meta-files"></a>Erzwingen der Serialisierung von Textobjekten und Aktivieren sichtbarer Metadateien

Diese Einstellungen vereinfachen die Arbeit mit Unity-Projekten und Quellcodeverwaltungssystemen (z. B. Git).

### <a name="enable-vr-supported"></a>Vr-Unterstützung aktivieren

**Unity 2018**

Konfiguriert die Optionen Virtual Reality Supported und Virtual Reality SDK unter **Player Settings**  >  **XR Settings (XR-Einstellungen für Playereinstellungen).**

### <a name="set-single-pass-instanced-rendering-path"></a>Festlegen des Renderingpfads "Single Pass Instanced"

Konfiguriert den   >    >  **XR Settings Stereo Rendering Mode (XR-Renderingmodus** für Playereinstellungen) auf **Single Pass Instanced (Einzeldurchlaufinstanz).**

### <a name="set-default-spatial-awareness-layer"></a>Festlegen der Standardebene für räumliche Wahrnehmung

Registriert räumliche Wahrnehmung als Ebene 31, um eine einfache und konsistente Konfiguration von Raycast- und Physikalischen Optionen zu ermöglichen.

### <a name="audio-spatializer"></a>Audio spatializer

Audio spatializers sind die Komponenten, die die Leistungsfähigkeit von Räumlichem Sound und Positionsaudio nutzen, um Mixed Reality-Erfahrungen wirklich immersiver zu gestalten.

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

Weitere Informationen finden Sie auf der [Dokumentationswebsite für die Audiodokumentation.](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started)

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

- Anväuten mit den Augen

  **Unity 2019.3 und neuer**

  Ermöglicht die Unterstützung für die Nachverfolgung des Anverfolgens der Augen des Benutzers.

### <a name="avoid-unity-playersettingsgraphicsjob-crash"></a>Vermeiden des Absturzes von Unity "PlayerSettings.graphicsJob"

**Unity 2019.3 und neuer**

In der neuesten Version von Unity 2019 stürzt die App ab, wenn "Grafikaufträge" aktiviert ist, wenn sie auf einem HoloLens 2 bereitgestellt wird.
Diese Einstellung ist in Unity standardmäßig aktiviert. Während dieser Fehler vorhanden ist (siehe [Unity-Fehler),](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)legt der Konfigurator standardmäßig Grafikaufträge auf "false" fest (sodass Apps, die für HoloLens 2 bereitgestellt wurden, nicht abstürzten).

## <a name="android-settings"></a>Einstellungen für Android

Konfigurationseinstellungen zur Unterstützung von AR-Anwendungen auf Android-Geräten.

![Android-Einstellungen](../features/images/configuration-dialog/ConfigurationDialogAndroidSettings.png)

### <a name="disable-multi-threaded-rendering"></a>Deaktivieren des Multithread-Renderings

Deaktiviert **player settings**  >  **Other Settings**  >  **Multithreaded Rendering (Weitere Einstellungen für Multithread-Rendering),** wie dies für die AR-Unterstützung von Android erforderlich ist.

### <a name="set-minimum-api-level"></a>Festlegen der API-Mindestebene

Legt den Wert von **Player Settings**  >  **Other Settings** Minimum API Level  >  fest, um Betriebssystemanforderungen für **AR-Anwendungen** zu erzwingen.

## <a name="ios-settings"></a>Einstellungen für iOS

Konfigurationseinstellungen zur Unterstützung von AR-Anwendungen auf iOS-geräten.

![iOS-Einstellungen](../features/images/configuration-dialog/ConfigurationDialogiOSSettings.png)

### <a name="set-required-os-version"></a>Festlegen der erforderlichen Betriebssystemversion

Legt den Wert von **Playereinstellungen**  >  **Andere Einstellungen** Auf die  >  **iOS-Mindestversion** fest, um Betriebssystemanforderungen für AR-Anwendungen zu erzwingen.

### <a name="set-required-architecture"></a>Festlegen der erforderlichen Architektur

Legt den Wert von Andere Einstellungsarchitektur für **Playereinstellungen**  >    >   fest, um Plattformanforderungen für AR-Anwendungen zu erzwingen.

### <a name="set-camera-usage-descriptions"></a>Festlegen von Kameranutzungsbeschreibungen

Legt den Wert von **Playereinstellungen**  >  **Andere Einstellungen**  >  **Kameraverwendungsbeschreibung** fest, die verwendet wird, um die Berechtigung zum Verwenden der Kamera des Geräts anzufordern.