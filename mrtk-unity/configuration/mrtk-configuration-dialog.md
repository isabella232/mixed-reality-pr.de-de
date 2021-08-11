---
title: Dialogfeld „MRTK-Konfiguration“
description: Konfigurieren von MRTK in Unity Project
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Unity
ms.openlocfilehash: c2ee07ee061eb66aef58e28b2d893f6902775e77d4aa2f77039fd422fa01d6aa
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219020"
---
# <a name="mrtk-configuration-dialog"></a>Dialogfeld „MRTK-Konfiguration“

Das MRTK-Konfigurationsdialogfeld wird angezeigt, wenn Unity ein Projekt lädt, und es wird festgestellt, dass eine oder mehrere Konfigurationsoptionen die Aufmerksamkeit des Entwicklers erfordern.

![Später anwenden Ignorieren](../features/images/configuration-dialog/ConfigurationDialogHeader.png)

Um die Änderungen anzuwenden, klicken Sie auf die Schaltfläche **Übernehmen.** Mit der Schaltfläche **Später** werden die Änderungen zurückgesetzt, bis das Projekt zu einem späteren Zeitpunkt erneut geladen wird.

> [!NOTE]
> Das Konfigurationsdialogfeld wird erneut angezeigt, wenn mindestens eine der empfohlenen Einstellungen deaktiviert bleibt. Um dies zu verhindern, wenden Sie die gewünschten Optionen an, starten Sie dann das Dialogfeld über **Mixed Reality Toolkit** Utilities Configure Unity Project neu, und klicken Sie auf  >    >   **Ignorieren.** Dadurch wird verhindert, dass das Konfigurationsdialogfeld automatisch erneut angezeigt wird.

## <a name="common-settings"></a>Allgemeine Einstellungen

Alle Buildziele teilen sich eine Sammlung allgemeiner Optionen.

![Allgemeine Einstellungen](../features/images/configuration-dialog/ConfigurationDialogCommonSettings.png)

### <a name="force-text-asset-serialization-and-enable-visible-meta-files"></a>Erzwingen der Serialisierung von Textobjekten und Aktivieren sichtbarer Metadateien

Diese Einstellungen vereinfachen die Arbeit mit Unity-Projekten und Quellcodeverwaltungssystemen (z. B. Git).

### <a name="enable-vr-supported"></a>Vr-Unterstützung aktivieren

**Unity 2018**

Konfiguriert die Optionen Virtual Reality Supported und Virtual Reality SDK in **Player Einstellungen**  >  **XR Einstellungen**.

### <a name="set-single-pass-instanced-rendering-path"></a>Festlegen des Renderingpfads "Single Pass Instanced"

Konfiguriert den **Player Einstellungen**  >  **XR Einstellungen** Stereo Rendering  >  **Mode** in Single Pass **Instanced**.

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

Microsoft Windows Spatializer, der von Unity als Teil der pakete Windows Mixed Reality und Windows XR Platform bereitgestellt wird.

- Audioaudio

Ein plattformübergreifender Spatializer von Google, der von Unity bereitgestellt wird.

Weitere Informationen finden Sie auf der [Dokumentationswebsite zu 1000 Audio.](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started)

## <a name="universal-windows-platform-settings"></a>Universal Windows Platform-Einstellungen

![UWP-Einstellungen](../features/images/configuration-dialog/ConfigurationDialogUWPSettings.png)

### <a name="uwp-capabilities"></a>UWP-Funktionen

Aktiviert bestimmte Anwendungsfunktionen für die Universelle Windows Plattformanwendung. Mit diesen Funktionen kann die Plattform informieren und die Berechtigung anfordern, um bestimmte Funktionen zu aktivieren.

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

In der neuesten Version von Unity 2019 stürzt die App ab, wenn "Grafikaufträge" aktiviert ist, wenn sie in einem HoloLens 2 bereitgestellt wird.
Diese Einstellung ist in Unity standardmäßig aktiviert. Während dieser Fehler vorhanden ist (siehe [Unity-Fehler),](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)legt der Konfigurator standardmäßig Grafikaufträge auf "false" fest (sodass Apps, die für HoloLens 2 bereitgestellt wurden, nicht abstürzten).

## <a name="android-settings"></a>Einstellungen für Android

Konfigurationseinstellungen zur Unterstützung von AR-Anwendungen auf Android-Geräten.

![Android Einstellungen](../features/images/configuration-dialog/ConfigurationDialogAndroidSettings.png)

### <a name="disable-multi-threaded-rendering"></a>Deaktivieren des Multithread-Renderings

Deaktiviert **player Einstellungen**  >  **Other Einstellungen**  >  **Multithreaded Rendering** gemäß der AR-Unterstützung von Android.

### <a name="set-minimum-api-level"></a>Festlegen der MINDEST-API-Ebene

Legt den Wert von **Player Einstellungen**  >  **Other Einstellungen** Minimum API Level  >  fest, um Betriebssystemanforderungen für **AR-Anwendungen** zu erzwingen.

## <a name="ios-settings"></a>Einstellungen für iOS

Konfigurationseinstellungen zur Unterstützung von AR-Anwendungen auf iOS-geräten.

![iOS-Einstellungen](../features/images/configuration-dialog/ConfigurationDialogiOSSettings.png)

### <a name="set-required-os-version"></a>Festlegen der erforderlichen Betriebssystemversion

Legt den Wert von **Player Einstellungen**  >  **Other Einstellungen** Target minimum  >  **iOS Version (Mindestens erforderliche iOS-Zielversion)** fest, um Betriebssystemanforderungen für AR-Anwendungen zu erzwingen.

### <a name="set-required-architecture"></a>Festlegen der erforderlichen Architektur

Legt den Wert von **Player Einstellungen**  >  **Other Einstellungen**  >  **Architecture** fest, um Plattformanforderungen für AR-Anwendungen zu erzwingen.

### <a name="set-camera-usage-descriptions"></a>Festlegen von Kameranutzungsbeschreibungen

Legt den Wert von **Player Einstellungen** Other Einstellungen Camera Usage Description fest, der verwendet wird, um die Berechtigung zum Verwenden der Kamera des  >    >   Geräts anzufordern.
