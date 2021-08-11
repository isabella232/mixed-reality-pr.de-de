---
title: Installieren der Tools
description: Beginnen Sie hier mit den aktuellsten Versionen von Unity, Visual Studio und den Tools, die für die Entwicklung für HoloLens und VR empfohlen werden.
author: thetuvix
ms.author: alexturn
ms.date: 05/11/2021
ms.topic: article
ms.localizationpriority: high
keywords: Aktuell, Tools, Erste Schritte, Grundlagen, Unity, Visual Studio, Toolkit, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Installation, Windows, HoloLens, Emulator, Unreal, OpenXR
ms.openlocfilehash: e0acc696a1109a29bcbfc99555a3b91708ccbd3c5b71db30183a085a19cd6c28
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210585"
---
# <a name="install-the-tools"></a>Installieren der Tools

Holen Sie sich die Tools, die Sie benötigen, um Anwendungen für Microsoft HoloLens und immersive Windows Mixed Reality-Headsets (VR) zu entwickeln. Es gibt kein separates SDK für die Entwicklung für Windows Mixed Reality. Sie verwenden Visual Studio mit dem Windows 10 SDK.

Sie besitzen kein Mixed Reality-Gerät? Sie können den [HoloLens-Emulator](platform-capabilities-and-apis/using-the-hololens-emulator.md) installieren, um einige Funktionen von Mixed Reality-Anwendungen ohne eine HoloLens zu testen. Sie können auch den [Windows Mixed Reality-Simulator](platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) verwenden, um Ihre Mixed Reality-Anwendungen für immersive Headsets zu testen.

Wir empfehlen die Installation entweder der Unity- oder der Unreal-Spielengine – dies ist die einfachste Möglichkeit, mit dem Erstellen von Mixed Reality-Apps zu beginnen. DirectX kann auch verwendet werden, wenn eine benutzerdefinierte Engine gewünscht ist.

Wenn Sie Unity verwenden, können Sie die Eingabesimulation des [Mixed Reality-Toolkits für Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) nutzen, um verschiedene Arten von Eingabeinteraktionen zu testen, wie die Eingabe per Handtracking und Eye Tracking. Verwenden Sie für Unreal-Projekte das [UX Tools-Plug-In](https://github.com/microsoft/MixedReality-UXTools-Unreal), um häufig verwendete Eingabeinteraktionen und Funktionen der Benutzererfahrung zu testen.

>[!TIP]
>Fügen Sie diese Seite als Lesezeichen hinzu und überprüfen Sie sie regelmäßig, um über die neueste Version der einzelnen Tools auf dem Laufenden zu bleiben, die für die Mixed Reality-Entwicklung empfohlen werden.

<br>

## <a name="installation-checklist"></a>Checkliste für die Installation

| Tool | Hinweise |
|---------|---------|
| ![Windows-Logo](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10** (Link zur manuellen Installation)</a><br><br>Installieren Sie die neueste Version von Windows 10, damit das Betriebssystem Ihres PCs mit der Plattform übereinstimmt, für die Sie Mixed Reality-Anwendungen entwickeln.  | **Installieren von Windows 10** <br> Sie können die neueste Version von Windows 10 über Windows Update in den Einstellungen oder durch Erstellen von Installationsmedien (über den Link in der linken Spalte) installieren. <br><br>Informationen zu den neuesten Mixed Reality-Features, die mit den jeweiligen Versionen von Windows 10 verfügbar sind, finden Sie unter [Aktuelle Versionshinweise](/windows/mixed-reality/enthusiast-guide/release-notes-october-2018.md). **Aktivieren Sie den Entwicklermodus auf Ihrem PC** unter „Einstellungen > Update und Sicherheit > Für Entwickler“. <br><br> **Hinweis für PCs in Unternehmen**<br>Wenn Ihr PC von der IT-Abteilung Ihres Unternehmens verwaltet wird, müssen Sie sich möglicherweise an diese wenden, um ein Update durchzuführen. <br><br> **„N“-Versionen von Windows**<br> Immersive Windows Mixed Reality-Headsets (VR) werden von „N“-Versionen von Windows nicht unterstützt. |
| ![Abbildung des Visual Studio-Logos](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2019 (16.8 oder höher)** (Installationslink)</a> <br><br>Voll funktionsfähige integrierte Entwicklungsumgebung (IDE) für Windows und mehr. Sie verwenden Visual Studio, um Code zu schreiben, zu debuggen, zu testen und bereitzustellen. | **Installieren von Visual Studio 2019** <br> Installieren Sie unbedingt die folgenden Workloads: <br><br>*● Desktop-Entwicklung mit C++*<br>*● Entwicklung für die Universelle Windows-Plattform (UWP)*<br>*● Spieleentwicklung mit Unity (**falls die Verwendung von Unity geplant ist**)*<br><br>Stellen Sie innerhalb der UWP-Workload sicher, **dass die folgenden Komponenten zur Installation enthalten sind**:<br><br>*● Windows 10 SDK, Version 10.0.19041.0 oder 10.0.18362.0*<br>*● USB-Gerätekonnektivität (zum Bereitstellen/Debuggen auf HoloLens über USB erforderlich)*<br>*● C++ (v142) Universelle Windows-Plattformtools (erforderlich bei Verwendung von Unity)*<br><br>**Hinweis zu HoloLens (1. Generation) und Windows Mixed Reality-Desktopheadsets**<br>Wenn Sie nur Anwendungen für Windows Mixed Reality-Desktopheadsets oder HoloLens (1. Generation) entwickeln, können Sie Visual Studio 2017 und das davon installierte Windows SDK verwenden.<br><br>**Bekannte Probleme**<br>Es gibt derzeit einige bekannte Probleme beim Debuggen von Mixed Reality-Anwendungen in Visual Studio 2019, Version 16.0.  Stellen Sie sicher, dass Sie auf **Visual Studio 2019, Version 16.8 oder höher**, aktualisieren. |
| ![Visual Studio-Logo](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2167725" target="_blank">**HoloLens 2-Emulator (Windows Holographic, Version 21H1 mit Update aus Juli 2021)** (Installationslink: 10.0.20348.1010)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**HoloLens-Emulator (1. Generation)** (Link zur Installation: 10.0.17763.134)</a> <br><br>Mit dem optionalen Emulator können Sie Anwendungen auf dem HoloLens-Image eines virtuellen Computers ohne physische HoloLens ausführen.<br> <br> | Weitere Informationen zu den ersten Schritten mit dem optionalen Emulator finden Sie unter [Verwendung des HoloLens-Emulators](../develop/platform-capabilities-and-apis/using-the-hololens-emulator.md).<br> <br> **Ihr System muss Hyper-V** unterstützen, damit die Installation des Emulators erfolgreich ist. Weitere Informationen finden Sie unten im Abschnitt zu den Systemanforderungen. <br> <br> **Hinweis zum HoloLens-Emulator (1. Generation)** <br>  Visual Studio 2017 ist erforderlich, damit die Installation erfolgreich abgeschlossen werden kann. Wenn Sie den HoloLens-Emulator (1. Generation) mit Visual Studio 2019 installieren, müssen Sie die VS-Vorlagen deaktivieren und [sie aus dem Visual Studio Marketplace installieren](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX). |

## <a name="install-your-engine-of-choice"></a>Installieren der Engine Ihrer Wahl

Nachdem Sie nun Windows 10, Visual Studio und das Windows 10 SDK vorbereitet haben, können Sie die Engine Ihrer Wahl installieren und einrichten.

> [!div class="nextstepaction"]
> [Auswählen Ihrer Engine](choosing-an-engine.md)

## <a name="troubleshooting"></a>Problembehandlung

### <a name="setting-developer-mode-is-grayed-out"></a>Einstellung „Entwicklermodus“ ist abgeblendet

Wenn beim Aktivieren des Entwicklermodus auf Ihrem Gerät Probleme auftreten, sind Sie möglicherweise nicht der [Gerätebesitzer](/hololens/security-adminless-os). Im Mehrbenutzermodus ist die Person, die das Gerät als Erster verwendet, der Gerätebesitzer. Alle nachfolgenden Benutzer verfügen nicht über die erforderlichen Berechtigungen, um den Entwicklermodus zu aktivieren oder andere Konfigurationsänderungen vorzunehmen. Es gibt jedoch eine Ausnahme, bei der der erste Benutzer in einer Autopilot-Umgebung möglicherweise nicht der Besitzer des Geräts ist, die detailliert in der [HoloLens-Sicherheitsdokumentation](/hololens/security-adminless-os#device-owner) beschrieben ist.

Folgende Lösungen sind möglich:

* Bitten Sie den Gerätebesitzer, den Entwicklermodus zu aktivieren, bevor das Gerät an andere Benutzer oder Entwickler übergeben wird.
* Schlagen Sie vor, dass Ihr IT-/MDM-Administrator die CSP-[Richtlinie ApplicationManagement/ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) für das spezifische Gerät oder eine Entwicklergerätegruppe aktiviert.
    * Diese Richtlinie kann über [Bereitstellungspakete](/hololens/hololens-provisioning) oder über [MDM für HoloLens-Geräte](/hololens/hololens-mdm-configure) festgelegt werden.
* Verwenden des [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery) (Begleiter für erweiterte Wiederherstellung)

> [!NOTE]
> Weitere Informationen zur Geräteverwaltung finden Sie in der Übersicht der **[HoloLens-Geräteverwaltung](/hololens/hololens-csp-policy-overview)** .

#### <a name="i-cant-deploy-over-usb"></a>Bereitstellen über USB nicht möglich

Wenn Sie eine Anwendung nicht direkt über USB bereitstellen können, stellen Sie sicher, dass Sie alle oben aufgeführten Installationsanforderungen erfüllt haben, und befolgen Sie unsere [schrittweise Anleitung](unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2).
