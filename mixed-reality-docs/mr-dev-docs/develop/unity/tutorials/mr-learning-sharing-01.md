---
title: Einführung in die Tutorials zu Mehrbenutzerfunktionen
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Mehrbenutzerumgebungen in einer HoloLens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, Mehrbenutzerfunktionen, Photon, MRTK, Mixed Reality Toolkit, UWP, Azure Spatial Anchors
ms.localizationpriority: high
ms.openlocfilehash: 3db488cc31d6ef7746aae67b3a84c42dc91985b586e907d2172346fe0952876f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197694"
---
# <a name="1-introduction-to-the-multi-user-capabilities-tutorials"></a>1. Einführung in die Tutorials zu Mehrbenutzerfunktionen

Willkommen bei den Tutorials zu Mehrbenutzerfunktionen! In dieser Tutorialreihe erlernen Sie die Grundlagen zum Entwickeln einer Mehrbenutzerumgebung mithilfe von <a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity Networking</a> (PUN). PUN ist eine von mehreren Netzwerkoptionen, die Mixed Reality-Entwicklern zum Erstellen gemeinsamer Benutzererfahrungen zur Verfügung stehen.

Tutorials in dieser Reihe:

* [Einrichten von Photon Unity Networking](mr-learning-sharing-02.md)
* [Verbinden mehrerer Benutzer](mr-learning-sharing-03.md)
* [Freigeben von Objektbewegungen für mehrere Benutzer](mr-learning-sharing-04.md)
* [Integrieren von Azure Spatial Anchors in eine gemeinsam genutzte Umgebung](mr-learning-sharing-05.md)

## <a name="objectives"></a>Ziele

* Erfahren, wie PUN-App erstellt und eine Verbindung Ihres Unity-Projekts mit ihr hergestellt wird
* Erlernen des Verbindens mehrerer Benutzer in einer freigegebenen Umgebung
* Erfahren, wie Objektbewegungen mit anderen Benutzern geteilt werden können
* Erfahren, wie räumliche Ausrichtung zwischen mehreren Geräten erreicht werden kann

## <a name="prerequisites"></a>Voraussetzungen

* Ein Windows 10-Computer, auf dem die richtigen [Tools installiert](../../install-the-tools.md) sind
* Windows 10 SDK (10.0.18362.0 oder höher)
* Ein für die [Entwicklung konfiguriertes](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) HoloLens 2-Gerät
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> mit installiertem Unity 2020 LTS und hinzugefügtem Buildunterstützungsmodul für die Universelle Windows-Plattform
* Durchgearbeiteter Abschnitt [Erstellen einer Spatial Anchors-Ressource](/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) des Tutorials [Schnellstart: Erstellen einer Unity HoloLens-App, die Azure Spatial Anchors verwendet](/azure/spatial-anchors/quickstarts/get-started-unity-hololens).
* Durchgearbeitete Tutorialserie [Erste Schritte](mr-learning-base-01.md) oder vorherige grundlegende Erfahrung mit Unity und MRTK
* Durchgearbeitete [Tutorialserie „Azure Spatial Anchors“](mr-learning-asa-01.md) oder vorherige Erfahrung im Erstellen eines Azure Spatial Anchors-Kontos
* Wenn Sie unter Android sowie HoloLens bereitstellen möchten
  * Ein Android-Gerät mit <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">Entwicklerunterstützung</a> und <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore-Unterstützung</a> mit USB-Verbindung zu Ihrem Windows- oder macOS-Computer
  * <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> mit installiertem Unity 2020 LTS und hinzugefügtem Buildunterstützungsmodul für Android
* Wenn Sie unter iOS sowie HoloLens bereitstellen möchten
  * Ein macOS-Computer mit installierter neuester Version von <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> und <a href="https://cocoapods.org" target="_blank">CocoaPods</a>
  * Ein iOS-Gerät mit <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit-Unterstützung</a> und USB-Verbindung mit Ihrem macOS-Computer
  * <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> mit installiertem Unity 2020 LTS und hinzugefügtem Buildunterstützungsmodul für iOS

> [!IMPORTANT]
> Die empfohlene Mixed Reality Toolkit-Version für diese Tutorialreihe ist MRTK 2.7.

> [!IMPORTANT]
> Die empfohlene Unity-Version für diese Tutorialreihe ist Unity 2020 LTS. Diese Informationen besitzen Vorrang vor allen Unity-Versionsanforderungen, die in den oben verlinkten Voraussetzungen angegeben sind.

> [!div class="nextstepaction"]
> [Nächstes Tutorial: 2. Einrichten von Photon Unity Networking](mr-learning-sharing-02.md)