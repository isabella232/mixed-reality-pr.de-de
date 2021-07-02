---
title: 'Tutorials zu räumlichen Audioinhalten : 1. Hinzufügen räumlicher Audiodaten zu Ihrem Projekt'
description: Fügen Sie ihrem Unity-Projekt das Microsoft Spatializer-Plug-In hinzu, um HoloLens 2 HRTF-Hardware-Ausladung zu erhalten.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens2, räumliche Audiodaten, MRTK, Mixed Reality-Toolkit, UWP, Windows 10, HRTF, kopfbezogene Übertragungsfunktion, Hall, Microsoft Spatializer
ms.openlocfilehash: a61e709f24c2162bc6e6e1248de658128674d49e
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175371"
---
# <a name="1-adding-spatial-audio-to-your-unity-project"></a>1. Hinzufügen räumlicher Audiodaten zu Ihrem Unity-Projekt

## <a name="overview"></a>Übersicht

Willkommen beim Tutorial zu räumlichen Audioinhalten für Unity auf HoloLens2. In dieser Tutorialreihe erfahren Sie, wie Sie die HRTF-Auslagerung (Head-Related Transfer Function, kopfbezogene Übertragungsfunktion) auf HoloLens 2 und wie Sie Hall bei Verwendung der HRTF-Auslagerung aktivieren.

Das [Microsoft Spatializer GitHub-Repository](https://github.com/microsoft/spatialaudio-unity) verfügt über ein abgeschlossenes Unity-Projekt dieser Tutorialsequenz.

Ein Verständnis dafür, was es bedeutet, Sounds mit HRTF-basierten Räumlichen Raumisierungstechnologien zu raumisieren, und Empfehlungen dazu, wann dies hilfreich sein kann, finden Sie unter [Raumklangentwurf](/windows/mixed-reality/spatial-sound-design).

## <a name="what-is-hrtf-offload"></a>Was ist HRTF-Ausladung?

Die Verarbeitung von Audiodaten mit HRTF-basierten Algorithmen erfordert eine große Menge an spezialisierter Berechnung. HoloLens 2 umfasst dedizierte Hardware, die verwendet werden kann, um eine Belastung des Anwendungsprozessors zu vermeiden, wodurch die Verarbeitung von HRTF-basierten Algorithmen "ausgeladen" wird.  Das Microsoft Spatializer-Plug-In bietet Ihrer Anwendung eine einfache Möglichkeit, die dedizierte HRTF-Hardware zu nutzen, damit Ihre Anwendung mehr anwendungsprozessoren für andere Vorgänge als räumliche Audiodaten verwenden kann.

## <a name="objectives"></a>Ziele

* Importieren und Aktivieren des Microsoft Spatializer-Plug-Ins
* Aktivieren von räumlicher Audiowiedergabe auf Ihrer Entwicklerarbeitsstation

## <a name="prerequisites"></a>Voraussetzungen

* Ein Windows 10-PC, der mit den richtigen [Tools konfiguriert](../../install-the-tools.md) ist
* Gundkenntnisse der C#-Programmierung
* Ein für die [Entwicklung konfiguriertes](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) HoloLens 2-Gerät
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> mit bereitgestelltem Unity 2020/2019 LTS und hinzugefügtem Modul "Universal Windows Platform Build Support"

Es **wird dringend empfohlen,** die Tutorials [zu](mr-learning-base-01.md) den ersten Schritte zu absolvieren oder grundlegende Erfahrungen mit Unity und MRTK zu sammeln, bevor Sie fortfahren.

> [!Important]
> Diese Tutorialreihe unterstützt Unity 2020 LTS (derzeit 2020.3.x), wenn Sie Open XR oder Windows XR-Plug-In und auch Unity 2019 LTS (derzeit 2019.4.x) verwenden, wenn Sie Legacy-WSA oder Windows XR-Plug-In verwenden. Diese Information hat Vorrang vor allen Unity-Versionsanforderungen, die in den oben verlinkten Voraussetzungen angegeben sind.

## <a name="creating-and-preparing-the-unity-project"></a>Erstellen und Vorbereiten des Unity-Projekts

In diesem Abschnitt erstellen Sie ein neues Unity-Projekt und bereiten es für die MRTK-Entwicklung vor.

Befolgen Sie zu diesem Zweck zunächst die Anweisungen unter [Initialisieren des Projekts und der ersten Anwendung](mr-learning-base-02.md), jedoch ohne die Anweisungen zum [Erstellen Ihrer Anwendung auf Ihrem Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2), die die folgenden Schritte beinhalten:

1. [Erstellen eines neuen Unity-Projekts](mr-learning-base-02.md#creating-the-unity-project), das mit einem passenden Namen bezeichnet wird, beispielsweise *MRTK-Tutorials*
2. [Wechseln der Buildplattform](mr-learning-base-02.md#configuring-the-unity-project)
3. [Importieren der TextMeshPro Essential-Ressourcen](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [Importieren des Mixed Reality Toolkits und Konfigurieren des Unity-Projekts](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. [Erstellen und Konfigurieren der Szene](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) und Benennen der Szene, z. B. *SpatialAudio*

Befolgen Sie [](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) dann die Anweisungen unter Ändern der Anzeigeoption für räumliche Wahrnehmung, um sicherzustellen, dass das MRTK-Konfigurationsprofil für Ihre Szene **DefaultHoloLens2ConfigurationProfile** lautet, und ändern Sie die Anzeigeoptionen für das Gitternetz für räumliche Wahrnehmung in **Okklusion**.

## <a name="adding-microsoft-spatializer-to-the-project"></a>Hinzufügen von Microsoft Spatializer zum Project

Laden Sie Microsoft Spatializer <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage</a> herunter, und importieren Sie es.

>[!TIP]
> Wenn Sie eine Auffrischung zum Importieren eines benutzerdefinierten Unity-Pakets benötigen, lesen Sie die Anweisungen unter [Importieren der Tutorialressourcen](mr-learning-base-04.md#importing-the-tutorial-assets).

## <a name="enable-the-microsoft-spatializer-plugin"></a>Aktivieren des Microsoft Spatializer-Plug-Ins

Nachdem Sie den Microsoft Spatializer in Ihr Unity-Projekt importiert haben, wird das **Fenster MRTK Project Configurator** angezeigt. Verwenden Sie die Dropdownliste **Audio spatializer,** um **den Microsoft Spatializer** auszuwählen, und klicken Sie dann auf die Schaltfläche Anwenden, um die Einstellung anzuwenden:

![MRTK Project Configurator](images/spatial-audio/spatial-audio-01-section3-step1-1.PNG)

Sie können den Microsoft Spatializer auch manuell aktivieren: Öffnen Sie **Bearbeiten -> Project Einstellungen -> Audio,** und ändern Sie **spatializer Plugin** in "Microsoft Spatializer".

![Project Einstellungen des Spatializer-Plug-Ins](images/spatial-audio/spatial-audio-01-section3-step1-2.PNG)

## <a name="enable-spatial-audio-on-your-workstation"></a>Aktivieren räumlicher Audiodaten auf Ihrer Arbeitsstation

Auf Desktopversionen Windows ist räumliche Audiowiedergabe standardmäßig deaktiviert. Aktivieren Sie sie, indem Sie mit der rechten Maustaste auf das Volumesymbol in der Taskleiste klicken. Wählen Sie Räumlicher Sound -HoloLens 2 aus, um die beste Darstellung des zu erhaltenden **> Windows Sonic für Kopfhörer.**

![Einstellungen für räumliche Desktopaudiodaten](images/spatial-audio/spatial-audio-01-section4-step1-1.PNG)

> [!NOTE]
> Diese Einstellung ist nur erforderlich, wenn Sie ihr Projekt im Unity-Editor testen möchten.

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie gelernt, wie Sie das Microsoft Spatializer-Plug-In importieren und aktivieren sowie die räumliche Audiowiedergabe auf Ihrer Arbeitsstation aktivieren.
Im nächsten Tutorial erfahren Sie, wie Sie räumliche Audiodaten zum Unity-Projekt hinzufügen.

> [!div class="nextstepaction"]
> [Nächstes Tutorial: 2. Raumisieren von Schaltflächeninteraktionsgeräuschen](unity-spatial-audio-ch2.md)
