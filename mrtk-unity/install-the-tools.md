---
title: Installieren der Tools
description: MRTK-Unity, Dokumentationsseite „Installieren der Tools“
author: polar-kev
ms.author: kesemple
ms.date: 03/02/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Mixed Reality-Toolkit, Installieren, aktuell, Tools, Erste Schritte, Grundlagen, Unity, Visual Studio, Toolkit, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Installation, Windows, HoloLens, Emulator
ms.openlocfilehash: a22a032261f3734167b229618f40db112b43c0f7
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2021
ms.locfileid: "102236961"
---
# <a name="install-the-tools"></a>Installieren der Tools

Holen Sie sich die Tools, die Sie benötigen, um Anwendungen für Microsoft HoloLens und immersive Windows Mixed Reality-Headsets (VR) zu entwickeln. Es gibt kein separates SDK für die Entwicklung für Windows Mixed Reality. Sie verwenden Visual Studio mit dem Windows 10 SDK.

Sie besitzen kein Mixed Reality-Gerät? Sie können den [HoloLens-Emulator](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator) installieren, um einige Funktionen von Mixed Reality-Anwendungen ohne eine HoloLens zu testen. Sie können außerdem den [Windows Mixed Reality-Simulator](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator) verwenden, um Ihre Mixed Reality-Anwendungen für immersive Headsets zu testen.

Diese Seite führt Sie durch die Installation der Tools, die Sie für die Verwendung von MRTK mit Unity benötigen. Wenn Sie daran interessiert sind, weitere Entwicklungsplattformen für Mixed Reality kennenzulernen, lesen Sie die Seite [Einführung in die Mixed Reality-Entwicklung](https://docs.microsoft.com/windows/mixed-reality/develop/development?tabs=unity).

Sie können Sie die Eingabesimulation des [Mixed Reality-Toolkits für Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) nutzen, um verschiedene Arten von Eingabeinteraktionen zu testen, wie Handtracking und Eyetracking.

|HINWEIS: Fügen Sie diese Seite als Lesezeichen hinzu, und überprüfen Sie sie regelmäßig, um über die neueste Version der einzelnen Tools auf dem Laufenden zu bleiben, die für die Mixed Reality-Entwicklung empfohlen werden.|
|---|

## <a name="installation-checklist"></a>Checkliste für die Installation

| Tool | Hinweise |
|---------|---------|
| ![Windows-Logo](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10** (Link zur manuellen Installation)</a><br><br>Installieren Sie die neueste Version von Windows 10, damit das Betriebssystem Ihres PCs mit der Plattform übereinstimmt, für die Sie Mixed Reality-Anwendungen entwickeln.  | **Installieren von Windows 10** <br> Sie können die neueste Version von Windows 10 über Windows Update in den Einstellungen oder durch Erstellen von Installationsmedien (über den Link in der linken Spalte) installieren. <br><br>Informationen zu den neuesten Mixed Reality-Features, die mit den jeweiligen Versionen von Windows 10 verfügbar sind, finden Sie unter [Aktuelle Versionshinweise](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software). **Aktivieren Sie den Entwicklermodus auf Ihrem PC** unter „Einstellungen > Update und Sicherheit > Für Entwickler“. <br><br> **Hinweis für PCs in Unternehmen**<br>Wenn Ihr PC von der IT-Abteilung Ihres Unternehmens verwaltet wird, müssen Sie sich möglicherweise an diese wenden, um ein Update durchzuführen. <br><br> **„N“-Versionen von Windows**<br> Immersive Windows Mixed Reality-Headsets (VR) werden von „N“-Versionen von Windows nicht unterstützt. |
| ![Abbildung des Visual Studio-Logos](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2019 (16.8 oder höher)** (Installationslink)</a> <br><br>Voll funktionsfähige integrierte Entwicklungsumgebung (IDE) für Windows und mehr. Sie verwenden Visual Studio, um Code zu schreiben, zu debuggen, zu testen und bereitzustellen. | **Installieren von Visual Studio 2019** <br> Installieren Sie unbedingt die folgenden Workloads: <br><br>*● Desktop-Entwicklung mit C++*<br>*● Entwicklung für die Universelle Windows-Plattform (UWP)*<br><br>Achten Sie innerhalb der UWP-Workload darauf, die folgende optionale Komponente zu aktivieren, wenn Sie für HoloLens entwickeln:<br><br>*● USB-Gerätekonnektivität*<br><br>**Hinweis zu Unity**<br>Sofern Sie nicht bewusst versuchen, eine neuere (Nicht-LTS-) Version von Unity für einen bestimmten Zweck zu installieren, empfehlen wir, die Installation der Unity-Workload *nicht* im Rahmen der Visual Studio-Installation durchzuführen und stattdessen den **Unity 2019 LTS**-Stream zu installieren, wie unten beschrieben.<br><br>**Bekannte Probleme**<br>Es gibt derzeit einige bekannte Probleme beim Debuggen von Mixed Reality-Anwendungen in Visual Studio 2019, Version 16.0.  Stellen Sie sicher, dass Sie auf **Visual Studio 2019, Version 16.8 oder höher**, aktualisieren. |
| ![Windows-Logo](images/Windows10_logo.png)<br><br><a href="https://developer.microsoft.com//windows/downloads/windows-10-sdk" target="_blank">**Windows 10 SDK (10.0.18362.0)** (Link zur manuellen Installation)</a> <br><br>Enthält die neuesten Header, Bibliotheken, Metadaten und Tools zum Erstellen von Apps für Windows 10 für HoloLens 2. | **Sie müssen das Windows SDK, Build 18362 oder höher, installieren, um HoloLens 2-Apps zu entwickeln.**<br> <br> Wenn Sie nur Anwendungen für Windows Mixed Reality-Desktopheadsets oder HoloLens (1. Generation) entwickeln, können Sie das von Visual Studio 2019 installierte Windows SDK verwenden. |
| ![Visual Studio-Logo](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2154784" target="_blank">**HoloLens 2 Emulator (Windows Holographic, Version 20H2, Update aus Februar 2021)** (Installationslink: 10.0.19041.1134)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**HoloLens-Emulator (1. Generation)** (Link zur Installation: 10.0.17763.134)</a> <br><br>Mit dem Emulator können Sie Anwendungen auf dem HoloLens-Image eines virtuellen Computers ohne physische HoloLens ausführen.<br> <br> | Weitere Informationen zu den ersten Schritten mit dem Emulator finden Sie unter [Verwendung des HoloLens-Emulators](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator).<br> <br> **Ihr System muss Hyper-V** unterstützen, damit die Installation des Emulators erfolgreich ist. Weitere Informationen finden Sie unten im Abschnitt zu den Systemanforderungen. <br> <br> **Hinweis zum HoloLens-Emulator (1. Generation)** <br>. Wenn Sie den HoloLens-Emulator (1. Generation) mit Visual Studio 2019 installieren, müssen Sie die VS-Vorlagen deaktivieren und [sie aus dem Visual Studio Marketplace installieren](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX). |

## <a name="unity"></a>Unity

Nachdem nun Ihr Windows 10, Visual Studio und Windows 10 SDK einsatzbereit sind, lassen Sie uns Unity als Engine für unsere Entwicklung nutzen.

### <a name="1-download-the-latest-version"></a>1. Herunterladen der aktuellen Version

Wir empfehlen den [Unity LTS-Stream (Long Term Support)](https://unity3d.com/unity/qa/lts-releases) als beste Version, um neue Projekte zu starten und auf die neueste Version zu aktualisieren, um die neuesten stabilen Korrekturen zu erhalten.

* Aktuell wird die Verwendung von Version [Unity 2019.4 LTS](https://unity3d.com/unity/qa/lts-releases?version=2019.4) empfohlen. Unity 2018.4 LTS wird ebenfalls unterstützt.
* Wenn Sie die [Mixed Reality OpenXR](https://docs.microsoft.com/windows/mixed-reality/develop/unity/openxr-getting-started)-Previewfunktionen mit MRTK verwenden möchten, benötigen Sie Unity 2020.2 oder höher.
* Wenn Sie aus bestimmten Gründen eine andere Version von Unity verwenden müssen, unterstützt Unity parallele Installationen unterschiedlicher Versionen.

### <a name="2-install-the-mixed-reality-feature-tool"></a>2. Installieren des Mixed Reality-Featuretools

Das [Mixed Reality-Featuretool](https://docs.microsoft.com/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) ist eine neue Möglichkeit für Entwickler, Mixed Reality-Featurepakete in Unity-Projekten zu ermitteln und hinzuzufügen.

Sie können Pakete vor dem Importieren nach Name oder Kategorie durchsuchen, ihre Abhängigkeiten anzeigen und sogar Änderungsvorschläge für Ihre Projektmanifestdatei anzeigen. Nachdem Sie die gewünschten Pakete überprüft haben, lädt das Mixed Reality-Featuretool sie in das Unity-Projekt Ihrer Wahl herunter.

#### <a name="importing-the-mixed-reality-toolkit"></a>Importieren des Mixed Reality-Toolkits

Sie können das Mixed Reality Toolkit-Paket herunterladen, indem Sie den [Installations- und Verwendungsanweisungen](https://docs.microsoft.com/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#system-requirements) folgen und das Mixed Reality Toolkit Foundation-Paket auswählen.

Wenn Sie den manuellen Download von MRTK-Paketen von GitHub vorziehen, suchen Sie die Releaseseite unter [Mixed Reality Toolkit-Unity (GitHub)](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) auf.

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a>3. Einrichten Ihres PCs für die Mixed Reality-Entwicklung

Das Windows SDK funktioniert am besten unter dem Betriebssystem Windows 10. Das SDK wird auch unter folgenden Betriebssystemen unterstützt: Windows 8.1, Windows 8, Windows 7, Windows Server 2012 und Windows Server 2008 R2. Beachten Sie, dass nicht alle Tools unter älteren Betriebssystemen unterstützt werden.

| Hinweis: Sie können Ihre Apps für HoloLens, für immersive Headsets (VR) oder beides entwickeln und bereitstellen. Stellen Sie sicher, dass Sie die unten aufgeführten Anforderungen abhängig von Ihren Anforderungen erfüllen. |
|---|

#### <a name="for-hololens-development"></a>HoloLens-Entwicklung

Wenn Sie Ihren Entwicklungs-PC für die HoloLens-Entwicklung einrichten, stellen Sie sicher, dass er die Systemanforderungen sowohl für [Unity](https://docs.unity3d.com/Manual/system-requirements.html) als auch für Visual Studio erfüllt. Wenn Sie Ihre App auf einem HoloLens-Gerät ausführen möchten, müssen Sie die [Einrichtungsanweisungen im Windows-Geräteportal](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal#setting-up-hololens-to-use-windows-device-portal) befolgen. Wenn Sie planen, den [HoloLens-Emulator](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator) zu verwenden, sollten Sie sicherstellen, dass Ihr PC auch die [Systemanforderungen des HoloLens-Emulators](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator#hololens-emulator-system-requirements) erfüllt.

Informationen zu den ersten Schritten mit dem HoloLens-Emulator finden Sie unter [Verwendung des HoloLens-Emulators](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator).

Wenn Sie planen, sowohl für HoloLens als auch für immersive Windows Mixed Reality-Headsets (VR) zu entwickeln, verwenden Sie die Systemempfehlungen und Anforderungen im folgenden Abschnitt.

### <a name="hololens-troubleshooting"></a>HoloLens-Problembehandlung

Einstellung „Entwicklermodus“ ist abgeblendet

Wenn beim Aktivieren des Entwicklermodus auf Ihrem Gerät Probleme auftreten, sind Sie möglicherweise nicht der [Gerätebesitzer](https://docs.microsoft.com/hololens/security-adminless-os). Im Mehrbenutzermodus ist die Person, die das Gerät als Erster verwendet, der Gerätebesitzer. Alle nachfolgenden Benutzer verfügen nicht über die erforderlichen Berechtigungen, um den Entwicklermodus zu aktivieren oder andere Konfigurationsänderungen vorzunehmen. Es gibt jedoch eine Ausnahme, bei der der erste Benutzer in einer Autopilot-Umgebung möglicherweise nicht der Besitzer des Geräts ist, die detailliert in der [HoloLens-Sicherheitsdokumentation](https://docs.microsoft.com/hololens/hololens2-compliance) beschrieben ist.

Folgende Lösungen sind möglich:

* Bitten Sie den Gerätebesitzer, den Entwicklermodus zu aktivieren, bevor das Gerät an andere Benutzer oder Entwickler übergeben wird.
* Schlagen Sie vor, dass Ihr IT-/MDM-Administrator die [CSP-Richtlinie ApplicationManagement/AllowDeveloperUnlock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) für das spezifische Gerät oder eine Entwicklergerätegruppe aktiviert.
Diese Richtlinie kann über [Bereitstellungspakete](https://docs.microsoft.com/hololens/hololens-provisioning) oder über [MDM für HoloLens-Geräte](https://docs.microsoft.com/hololens/hololens-mdm-configure) festgelegt werden.
* Verwenden des [Advanced Recovery Companion (ARC)](https://docs.microsoft.com/hololens/hololens-recovery) (Begleiter für erweiterte Wiederherstellung)

| Hinweis: Weitere Informationen zur Geräteverwaltung finden Sie in der Übersicht der HoloLens-Geräteverwaltung.|
|---|

Bereitstellen über USB nicht möglich

Wenn Sie eine Anwendung nicht direkt über USB bereitstellen können, stellen Sie sicher, dass Sie alle oben aufgeführten Installationsanforderungen erfüllt haben, und befolgen Sie unsere [schrittweise Anleitung](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02#building-your-application-to-your-hololens-2).

Anforderungen an immersive Headsets (VR)

| Hinweis: Die folgenden Richtlinien sind die derzeit empfohlenen Mindestanforderungen und Spezifikationen für Ihren Entwicklungs-PC für immersive Headsets (VR) und werden regelmäßig aktualisiert.|
|---|

| Warnung: Verwechseln Sie dies nicht mit den [Richtlinien zur minimalen PC-Hardwarekompatibilität](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), die die Spezifikationen von Endverbraucher-PCs umreißen, auf die Sie Ihre immersive Headset-App (VR) oder Ihr Spiel ausrichten sollten.|
|---|

Wenn Ihr Entwicklungs-PC für immersive Headsets nicht über vollwertige HDMI- und/oder USB 3.0-Anschlüsse verfügt, benötigen Sie [Adapter](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs), um Ihr Headset anzuschließen.

Es gibt derzeit [bekannte Probleme](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) bei einigen Hardwarekonfigurationen, insbesondere bei Notebooks mit Hybridgrafik.

. | Minimum | Empfohlen
--- |--- |---
Prozessor | Notebook: Intel Mobile Core i5-CPU der 7. Generation, Dual-Core mit Hyperthreading Desktop: Intel Desktop i5-CPU der 6. Generation, Dual-Core mit Hyperthreading ODER AMD FX4350 mit 4,2 GHz und vier Kernen| Desktop: Intel Desktop i7 der 6. Generation (6 Kerne) ODER AMD Ryzen 5 1600 (6 Kerne, 12 Threads) GPU | Notebook: NVIDIA GTX 965M, AMD RX 460M (2 GB) – gleichwertig oder höher, DX12-fähige GPU Desktop: NVIDIA GTX 960/1050, AMD Radeon RX 460 (2 GB) – gleichwertig oder höher, DX12-fähige GPU | Desktop: NVIDIA GTX 980/1060, AMD Radeon RX 480 (2 GB) – gleichwertig oder höher, DX12-fähige GPU
GPU-Treiber (WDDM-Version) | WDDM 2.2-Treiber
Wärmeleistung | 15 W oder höher
Anschlüsse der Grafikanzeige | Ein verfügbarer Grafikanzeigeanschluss für Headset (HDMI 1.4 oder DisplayPort 1.2 für Headsets mit 60 Hz, HDMI 2.0 oder DisplayPort 1.2 für Headsets mit 90 Hz)
Anzeigeauflösung | Auflösung: SVGA (800 x 600) oder höhere Bittiefe: Farbe: 32 Bit pro Pixel
Memory | 8 GB RAM oder mehr | 16 GB RAM oder mehr
Speicher | >10 GB zusätzlicher freier Speicherplatz
USB-Anschlüsse | Ein verfügbare USB-Anschluss für Headset (USB-3.0 Type-A) Hinweis: USB muss mindestens 900 mA bereitstellen
Bluetooth | Bluetooth 4.0 (für den Anschluss von Zubehör)

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Nachdem Sie die Tools installiert haben, empfehlen wir Ihnen, sich nach unserer MRTK HoloLens 2-Tutorialreihe zu richten.
> [!div class="nextstepaction"]
> [HoloLens 2-Tutorialreihe](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02)