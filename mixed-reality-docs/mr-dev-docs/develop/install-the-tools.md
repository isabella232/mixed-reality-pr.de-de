---
title: Installieren der Tools
description: Beginnen Sie hier mit den aktuellsten Versionen von Unity, Visual Studio und den Tools, die für die Entwicklung für HoloLens und VR empfohlen werden.
author: thetuvix
ms.author: alexturn
ms.date: 04/13/2021
ms.topic: article
ms.localizationpriority: high
keywords: Aktuell, Tools, Erste Schritte, Grundlagen, Unity, Visual Studio, Toolkit, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Installation, Windows, HoloLens, Emulator, Unreal, OpenXR
ms.openlocfilehash: 40bf9930124e6f64197aaa5daca8b332dc741546
ms.sourcegitcommit: be79d8e9ebac553aabec7c57c44eee56123aa00e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "107369873"
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
| ![Windows-Logo](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10** (Link zur manuellen Installation)</a><br><br>Installieren Sie die neueste Version von Windows 10, damit das Betriebssystem Ihres PCs mit der Plattform übereinstimmt, für die Sie Mixed Reality-Anwendungen entwickeln.  | **Installieren von Windows 10** <br> Sie können die neueste Version von Windows 10 über Windows Update in den Einstellungen oder durch Erstellen von Installationsmedien (über den Link in der linken Spalte) installieren. <br><br>Informationen zu den neuesten Mixed Reality-Features, die mit den jeweiligen Versionen von Windows 10 verfügbar sind, finden Sie unter [Aktuelle Versionshinweise](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-october-2018.md). **Aktivieren Sie den Entwicklermodus auf Ihrem PC** unter „Einstellungen > Update und Sicherheit > Für Entwickler“. <br><br> **Hinweis für PCs in Unternehmen**<br>Wenn Ihr PC von der IT-Abteilung Ihres Unternehmens verwaltet wird, müssen Sie sich möglicherweise an diese wenden, um ein Update durchzuführen. <br><br> **„N“-Versionen von Windows**<br> Immersive Windows Mixed Reality-Headsets (VR) werden von „N“-Versionen von Windows nicht unterstützt. |
| ![Abbildung des Visual Studio-Logos](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2019 (16.8 oder höher)** (Installationslink)</a> <br><br>Voll funktionsfähige integrierte Entwicklungsumgebung (IDE) für Windows und mehr. Sie verwenden Visual Studio, um Code zu schreiben, zu debuggen, zu testen und bereitzustellen. | **Installieren von Visual Studio 2019** <br> Installieren Sie unbedingt die folgenden Workloads: <br><br>*● Desktop-Entwicklung mit C++*<br>*● Entwicklung für die Universelle Windows-Plattform (UWP)*<br><br>Achten Sie innerhalb der UWP-Workload darauf, die folgende optionale Komponente zu aktivieren, wenn Sie für HoloLens entwickeln:<br><br>*● USB-Gerätekonnektivität*<br><br>**Anmerkung zur USB-Konnektivität**<br>Während der Installation muss das Kontrollkästchen **IP über USB** aktiviert sein, das nicht standardmäßig aktiviert ist. Dies ist erforderlich, um mit einer HoloLens über USB zu kommunizieren.<br><br>**Hinweis zu Unity**<br>Sofern Sie nicht bewusst versuchen, eine neuere (Nicht-LTS-) Version von Unity zu installieren, empfehlen wir, die Installation der Unity-Workload *nicht* im Rahmen der Visual Studio-Installation durchzuführen und stattdessen den **Unity 2019 LTS**-Stream zu installieren.<br><br>**Bekannte Probleme**<br>Es gibt derzeit einige bekannte Probleme beim Debuggen von Mixed Reality-Anwendungen in Visual Studio 2019, Version 16.0.  Stellen Sie sicher, dass Sie auf **Visual Studio 2019, Version 16.8 oder höher**, aktualisieren. |
| ![Windows-Logo](images/Windows10_logo.png)<br><br><a href="https://developer.microsoft.com//windows/downloads/windows-10-sdk" target="_blank">**Windows 10 SDK (10.0.18362.0)** (Link zur manuellen Installation)</a> <br><br>Enthält die neuesten Header, Bibliotheken, Metadaten und Tools zum Erstellen von Apps für Windows 10 für HoloLens 2. | **Sie müssen das Windows SDK, Build 18362 oder höher, installieren, um HoloLens 2-Apps zu entwickeln.**<br> <br> Wenn Sie nur Anwendungen für Windows Mixed Reality-Desktopheadsets oder HoloLens (1. Generation) entwickeln, können Sie das von Visual Studio 2017 installierte Windows SDK verwenden. |
| ![Visual Studio-Logo](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2160829" target="_blank">**HoloLens 2-Emulator (Windows Holographic, Version 20H2, Update aus April 2021)** (Installationslink: 10.0.19041.1144)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**HoloLens-Emulator (1. Generation)** (Link zur Installation: 10.0.17763.134)</a> <br><br>Mit dem Emulator können Sie Anwendungen auf dem HoloLens-Image eines virtuellen Computers ohne physische HoloLens ausführen.<br> <br> | Weitere Informationen zu den ersten Schritten mit dem Emulator finden Sie unter [Verwendung des HoloLens-Emulators](../develop/platform-capabilities-and-apis/using-the-hololens-emulator.md).<br> <br> **Ihr System muss Hyper-V** unterstützen, damit die Installation des Emulators erfolgreich ist. Weitere Informationen finden Sie unten im Abschnitt zu den Systemanforderungen. <br> <br> **Hinweis zum HoloLens-Emulator (1. Generation)** <br>  Visual Studio 2017 ist erforderlich, damit die Installation erfolgreich abgeschlossen werden kann. Wenn Sie den HoloLens-Emulator (1. Generation) mit Visual Studio 2019 installieren, müssen Sie die VS-Vorlagen deaktivieren und [sie aus dem Visual Studio Marketplace installieren](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX). |

## <a name="install-your-engine-of-choice"></a>Installieren der Engine Ihrer Wahl

Nachdem Sie nun Windows 10, Visual Studio und das Windows 10 SDK vorbereitet haben, können Sie die Engine Ihrer Wahl installieren und einrichten. 

Wenn Sie Ihre Engine noch nicht gewählt haben, finden Sie weitere Informationen unter [Einführung in die Mixed Reality-Entwicklung](./development.md?tabs=unity#what-technology-path-are-you-interested-in). 

[!INCLUDE[](includes/tools-overview.md)]