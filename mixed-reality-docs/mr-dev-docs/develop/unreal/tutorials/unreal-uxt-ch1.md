---
title: 1. Erste Schritte
description: Teil 1 von 6 einer Tutorialreihe zum Erstellen einer Schach-App mit der Unreal Engine 4 und dem UX Tools-Plug-In des Mixed Reality-Toolkits
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Tutorial, Erste Schritte, MRTK, UXT, UX-Tools, Dokumentation, Mixed Reality-Headset Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: a46b9fef96f75f3d80b9ebbd5cbd724730374b41
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580568"
---
# <a name="1-getting-started"></a>1. Erste Schritte

Einsteigern in die Welt der Mixed Reality ebenso wie erfahrenen Experten wird hier gleichermaßen der ideale Ausgangspunkt geboten, um ihre [HoloLens 2](../../../index.yml)- und [Unreal Engine](https://www.unrealengine.com/en-US/)-Journey zu beginnen. In dieser Tutorialreihe erhalten Sie eine ausführliche Anleitung zum Erstellen einer interaktiven Schach-App mit dem [UX Tools-Plug-In](https://github.com/microsoft/MixedReality-UXTools-Unreal), das Teil des [Mixed Reality Toolkit für Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal) ist. Das Plug-in unterstützt Sie beim Hinzufügen allgemeiner UX-Features zu Ihren Projekten anhand von Code, Blaupausen und Beispielen. 

![Fertige Szene im Viewport](images/unreal-uxt/5-endscene.PNG)

Am Ende der Reihe haben Sie Erfahrungen mit folgenden Aufgaben gesammelt:
* Erstellen eines neuen Projekts
* Einrichtung für Mixed Reality
* Arbeiten mit Benutzereingaben
* Hinzufügen von Schaltflächen
* Wiedergabe in einem Emulator oder auf einem Gerät

## <a name="prerequisites"></a>Voraussetzungen

Achten Sie darauf, dass Sie die folgenden Produkte installiert haben, bevor Sie einsteigen:
* Windows 10 (1809 oder höher)
* Windows 10 SDK (10.0.18362.0 oder höher)
* [Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 oder höher
* [Für die Entwicklung](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) oder einen [Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-2-emulator-overview) konfiguriertes Microsoft HoloLens 2-Gerät
* Visual Studio 2019 mit den folgenden Workloads

### <a name="installing-visual-studio-2019"></a>Installieren von Visual Studio 2019

Stellen Sie zunächst sicher, dass Ihre Einrichtung über alle erforderlichen Visual Studio-Pakete verfügt:
1. Installieren Sie die aktuelle Version von [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/).
1. Installieren Sie die folgenden [Workloads](/visualstudio/install/modify-visual-studio#modify-workloads):
    * Desktopentwicklung mit C++
    * .NET-Desktopentwicklung
    * Entwicklung für die universelle Windows-Plattform
1. Klappen Sie die Entwicklung für die Universelle Windows-Plattform auf, und wählen Sie Folgendes aus: 
    * USB-Gerätekonnektivität
    * UWP-Tools (Universelle Windows-Plattform) für C++ (v142)

1. Installieren Sie die folgenden [Komponenten](/visualstudio/install/modify-visual-studio#modify-individual-components):
    * „Compiler, Buildtools und Runtimes“ > „MSVC v142 – VS 2019 C++-ARM64-Buildtools“ (neueste Version)

Sie können die Installation mit der folgenden Abbildung bestätigen

![Wichtige Optionen im VS-Installationsprogramm](images/unreal-uxt/1-install-the-tools.png)

Das war's. Jetzt haben Sie alle Vorbereitungen getroffen, um mit dem Schach-Projekt beginnen zu können.

[Nächster Abschnitt: 2. Initialisieren des Projekts und der ersten Anwendung](unreal-uxt-ch2.md)