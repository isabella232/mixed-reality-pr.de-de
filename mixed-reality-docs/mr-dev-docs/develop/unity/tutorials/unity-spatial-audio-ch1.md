---
title: 'Tutorials zu räumlichen Audioinhalten: 1. Hinzufügen räumlicher Audiodaten zu Ihrem Projekt'
description: Fügen Sie Ihrem Unity-Projekt das Microsoft Spatializer-Plug-In hinzu, um auf HoloLens 2 HRTF-Hardwareabladung zuzugreifen.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, Hololens2, räumliche Audiodaten, MRTK, Mixed Reality-Toolkit, UWP, Windows 10, HRTF, kopfbezogene Übertragungsfunktion, Hall, Microsoft Spatializer
ms.openlocfilehash: 112531a3248461a5b380ad4b93de34545a2f2c3f
ms.sourcegitcommit: b4fd969b9c2e6313aa728b0dbee4b25014668720
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2021
ms.locfileid: "111403361"
---
# <a name="1-adding-spatial-audio-to-your-unity-project"></a>1. Hinzufügen räumlicher Audiodaten zu Ihrem Unity-Projekt

## <a name="overview"></a>Übersicht

Willkommen beim Tutorial zu räumlichen Audiodaten für Unity auf HoloLens2. In dieser Tutorialreihe erfahren Sie, wie Sie die HRTF-Auslagerung (Head-Related Transfer Function) für HoloLens 2 verwenden und wie Sie hallen, wenn Sie HRTF-Auslagerung verwenden.

Das [GitHub-Repository Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity) verfügt über ein abgeschlossenes Unity-Projekt dieser Tutorialsequenz.

Ein Verständnis dafür, was es bedeutet, Sounds mit HRTF-basierten Spatialization-Technologien zu spatialisieren, und Empfehlungen dazu, wann es hilfreich sein kann, finden Sie unter [Spatial Sound Design](/windows/mixed-reality/spatial-sound-design).

## <a name="what-is-hrtf-offload"></a>Was ist HRTF-Auslagerung?

Die Verarbeitung von Audio mit HRTF-basierten Algorithmen erfordert eine große Menge spezieller Berechnungen. HoloLens 2 enthält dedizierte Hardware, die verwendet werden kann, um eine Belastung des Anwendungsprozessors zu vermeiden und so die Verarbeitung von HRTF-basierten Algorithmen zu "auslagern".  Das Microsoft Spatializer-Plug-In bietet Eine einfache Möglichkeit für Ihre Anwendung, die dedizierte HRTF-Hardware zu nutzen, sodass Ihre Anwendung einen größeren Teil des Anwendungsprozessors für andere Vorgänge als räumliche Audiodaten verwenden kann.

## <a name="objectives"></a>Ziele

* Importieren und Aktivieren des Microsoft Spatializer-Plug-Ins
* Aktivieren von räumlichem Audio auf Ihrer Entwicklerarbeitsstation

## <a name="prerequisites"></a>Voraussetzungen

* Ein Windows 10-PC, der mit den richtigen [Tools konfiguriert](../../install-the-tools.md) ist
* Gundkenntnisse der C#-Programmierung
* Ein für die [Entwicklung konfiguriertes](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) HoloLens 2-Gerät
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> mit eingebundener Unity 2020/2019 LTS und hinzugefügtes modul "Universelle Windows-Plattform Buildunterstützung"

Es **wird dringend empfohlen,** die Reihe [Erste Schritte](mr-learning-base-01.md) mit Tutorials abzuschließen oder einige grundlegende Vorherige Erfahrungen mit Unity und MRTK zu sammeln, bevor Sie fortfahren.

> [!Important]
> Diese Tutorialreihe unterstützt Unity 2020 LTS (derzeit 2020.3.x), wenn Sie Open XR oder Das Windows XR-Plug-In sowie Unity 2019 LTS (derzeit 2019.4.x) verwenden, wenn Sie ältere WSA- oder Windows XR-Plug-Ins verwenden. Diese Information hat Vorrang vor allen Unity-Versionsanforderungen, die in den oben verlinkten Voraussetzungen angegeben sind.

## <a name="creating-and-preparing-the-unity-project"></a>Erstellen und Vorbereiten des Unity-Projekts

In diesem Abschnitt erstellen Sie ein neues Unity-Projekt und bereiten es für die MRTK-Entwicklung vor.

Befolgen Sie zu diesem Zweck zunächst die Anweisungen unter [Initialisieren des Projekts und der ersten Anwendung](mr-learning-base-02.md), jedoch ohne die Anweisungen zum [Erstellen Ihrer Anwendung auf Ihrem Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2), die die folgenden Schritte beinhalten:

1. [Erstellen eines neuen Unity-Projekts](mr-learning-base-02.md#creating-the-unity-project), das mit einem passenden Namen bezeichnet wird, beispielsweise *MRTK-Tutorials*

1. [Wechseln der Buildplattform](mr-learning-base-02.md#configuring-the-unity-project)

1. [Importieren der TextMeshPro Essential-Ressourcen](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

1. [Importieren des Mixed Reality Toolkits und Konfigurieren des Unity-Projekts](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)

1. [Erstellen und Konfigurieren der Szene](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) und Benennen der Szene, z. B. *SpatialAudio*

Befolgen Sie dann die Anweisungen [unter Ändern der Anzeigeoption](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) für räumliche Wahrnehmung, um sicherzustellen, dass das MRTK-Konfigurationsprofil für Ihre Szene **DefaultHoloLens2ConfigurationProfile** lautet, und ändern Sie die Anzeigeoptionen für das Gitternetz für räumliche Wahrnehmung in **Verdeckung.**

## <a name="adding-microsoft-spatializer-to-the-project"></a>Hinzufügen von Microsoft Spatializer zum Projekt

Laden Sie Microsoft Spatializer <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage</a> herunter, und importieren Sie es.

>[!TIP]
> Wenn Sie eine Auffrischung zum Importieren eines benutzerdefinierten Unity-Pakets benötigen, lesen Sie die Anweisungen unter [Importieren der Tutorialressourcen](mr-learning-base-02.md#importing-the-tutorial-assets).

## <a name="enable-the-microsoft-spatializer-plugin"></a>Aktivieren des Microsoft Spatializer-Plug-Ins

Nachdem Sie Microsoft Spatializer in Ihr Unity-Projekt importiert haben, wird das Fenster **MRTK Project Configurator** angezeigt. Wählen Sie in der Dropdownliste **Audio spatializer** den **Microsoft Spatializer** aus, und klicken Sie dann auf die Schaltfläche Übernehmen, um die Einstellung anzuwenden:

![MRTK-Projektkonfigurator](images/spatial-audio/spatial-audio-01-section3-step1-1.PNG)

Sie können den Microsoft Spatializer auch manuell aktivieren: **Bearbeiten -> Projekteinstellungen -> Audio** öffnen und **das Spatializer-Plug-In** in "Microsoft Spatializer" ändern.

![Projekteinstellungen mit Spatializer-Plug-In](images/spatial-audio/spatial-audio-01-section3-step1-2.PNG)

## <a name="enable-spatial-audio-on-your-workstation"></a>Aktivieren von räumlichem Audio auf Ihrer Arbeitsstation

In Desktopversionen von Windows ist räumliches Audio standardmäßig deaktiviert. Aktivieren Sie es, indem Sie mit der rechten Maustaste auf das Volumesymbol in der Taskleiste klicken. Wählen Sie **Räumlicher Sound -> Windows Sonic für Kopfhörer** aus, um die beste Darstellung des Hörens auf HoloLens 2 zu erhalten.

![Desktopeinstellungen für räumliche Audiodaten](images/spatial-audio/spatial-audio-01-section4-step1-1.PNG)

> [!NOTE]
> Diese Einstellung ist nur erforderlich, wenn Sie das Projekt im Unity-Editor testen möchten.

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie erfahren, wie Sie das Microsoft Spatializer-Plug-In importieren und aktivieren sowie das räumliche Audio auf Ihrer Arbeitsstation aktivieren.
Im nächsten Tutorial erfahren Sie, wie Sie räumliche Audiodaten im Unity-Projekt hinzufügen.

> [!div class="nextstepaction"]
> [Nächstes Tutorial: 2. Spatializing button interaction sounds](unity-spatial-audio-ch2.md)
