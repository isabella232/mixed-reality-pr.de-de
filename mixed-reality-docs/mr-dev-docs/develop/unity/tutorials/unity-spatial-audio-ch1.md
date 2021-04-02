---
title: Lernprogramme für räumliche Audiodaten-1. Hinzufügen räumlicher Audiodaten zu Ihrem Projekt
description: Fügen Sie das Microsoft spatializer-Plug-in zu Ihrem Unity-Projekt hinzu, um auf hololens 2 HRTF Hardware Offload zuzugreifen.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, hololens2, Spatial Audiodatei, mrtk, Mixed Reality Toolkit, UWP, Windows 10, HRTF, Head-Related Transfer Function, Reverb, Microsoft spatializer
ms.openlocfilehash: 7964ecdc8adee7c61c4c7086b8d04983f6e3903f
ms.sourcegitcommit: 4fb961beeebd158e2f65b7c714c5e471454400a3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2021
ms.locfileid: "105982793"
---
# <a name="1-adding-spatial-audio-to-your-unity-project"></a>1. hinzufügen räumlicher Audiodaten zu Ihrem Unity-Projekt

## <a name="overview"></a>Übersicht

Willkommen beim Tutorial zu räumlichen Audiodaten für Unity auf HoloLens2. In dieser tutorialreihe erfahren Sie, wie Sie die Start bezogene Übertragungsfunktion (Head-Related Transfer Function, HRTF) auf hololens 2 verwenden und wie Sie den Reverb bei Verwendung der HRTF-Auslagerung aktivieren.

Das [GitHub-Repository für Microsoft spatializer](https://github.com/microsoft/spatialaudio-unity) verfügt über ein abgeschlossenes Unity-Projekt für diese tutorialsequenz.

Ein Verständnis der Bedeutung von Sounds mithilfe von HRTF-basierten spatialisierungs Technologien und Empfehlungen für den Fall, dass es hilfreich sein kann, finden Sie unter [Spatial Sound Design](/windows/mixed-reality/spatial-sound-design).

## <a name="what-is-hrtf-offload"></a>Was ist HRTF Offload?

Die Verarbeitung von Audiodaten mithilfe von HRTF-basierten Algorithmen erfordert eine große Menge an spezieller Berechnung. Hololens 2 umfasst dedizierte Hardware, die verwendet werden kann, um die Belastung des Anwendungs Prozessors zu vermeiden und so die Verarbeitung von HRTF-basierten Algorithmen zu verlagern.  Das Microsoft spatializer-Plug-in ist eine einfache Möglichkeit für Ihre Anwendung, die dedizierte HRTF-Hardware zu nutzen, damit Ihre Anwendung mehr Anwendungs Prozessor für andere Vorgänge als räumliche Audiodaten verwenden kann.

## <a name="objectives"></a>Ziele

* Importieren und Aktivieren des Microsoft spatializer-Plug-ins
* Aktivieren räumlicher Audiodaten auf Ihrer Entwickler Arbeitsstation

## <a name="prerequisites"></a>Voraussetzungen

* Ein Windows 10-PC, der mit den richtigen [Tools konfiguriert](../../install-the-tools.md) ist
* Gundkenntnisse der C#-Programmierung
* Ein für die [Entwicklung konfiguriertes](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) HoloLens 2-Gerät
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> mit installiertem Unity 2019 LTS und hinzugefügtem Buildunterstützungsmodul für die Universelle Windows-Plattform

Wir **empfehlen Ihnen dringend** , die Reihe "Tutorials für die ersten Schritte" auszuführen oder einige grundlegende Erfahrung mit Unity und mrtk zu [erhalten](mr-learning-base-01.md) , bevor Sie fortfahren

> [!IMPORTANT]
>
> * Die empfohlene Unity-Version für diese Tutorialserie ist Unity 2019 LTS. Sie ersetzt alle Anforderungen oder Empfehlungen bezüglich der Unity-Version, die in den oben verknüpften Voraussetzungen genannt werden.

## <a name="creating-and-preparing-the-unity-project"></a>Erstellen und Vorbereiten des Unity-Projekts

In diesem Abschnitt erstellen Sie ein neues Unity-Projekt und bereiten es für die MRTK-Entwicklung vor.

Befolgen Sie zu diesem Zweck zunächst die Anweisungen unter [Initialisieren des Projekts und der ersten Anwendung](mr-learning-base-02.md), jedoch ohne die Anweisungen zum [Erstellen Ihrer Anwendung auf Ihrem Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2), die die folgenden Schritte beinhalten:

1. [Erstellen eines neuen Unity-Projekts](mr-learning-base-02.md#creating-the-unity-project), das mit einem passenden Namen bezeichnet wird, beispielsweise *MRTK-Tutorials*

1. [Wechseln der Buildplattform](mr-learning-base-02.md#configuring-the-unity-project)

1. [Importieren der TextMeshPro Essential-Ressourcen](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

1. [Importieren des Mixed Reality-Toolkits](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)

1. [Konfigurieren des Unity-Projekts](mr-learning-base-02.md#configuring-the-unity-project)

1. [Erstellen und Festlegen der Szene](mr-learning-base-02.md#creating-and-configuring-the-scene) und versehen eines geeigneten namens für die Szene, z. b. *spatialaudio*

Befolgen Sie dann die Anweisungen unter [Ändern der Anzeige Option räumliches Bewusstsein](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) , um sicherzustellen, dass das mrtk-Konfigurations Profil für Ihre Szene **DefaultHoloLens2ConfigurationProfile** ist, und ändern Sie die Anzeigeoptionen für das Mesh Spatial Awareness in **oksion**.

## <a name="adding-microsoft-spatializer-to-the-project"></a>Hinzufügen von Microsoft spatializer zum Projekt

Herunterladen und Importieren von Microsoft spatializer  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft. spatialaudio. spatializer. Unity. 1.0.18. unitypackage </a>

>[!TIP]
> Wenn Sie eine Auffrischung zum Importieren eines benutzerdefinierten Unity-Pakets benötigen, lesen Sie die Anweisungen unter [Importieren der Tutorialressourcen](mr-learning-base-02.md#importing-the-tutorial-assets).

## <a name="enable-the-microsoft-spatializer-plugin"></a>Aktivieren des Microsoft spatializer-Plug-ins

Nachdem Sie den **Microsoft spatializer** importiert haben, müssen Sie ihn aktivieren. Öffnen Sie die **Projekteinstellungen bearbeiten-> > Audiodatei**, und ändern Sie das **spatializer-Plug** -in in "Microsoft spatializer".

![Projekteinstellungen mit dem spatializer-Plug-in](images/spatial-audio/spatial-audio-01-section3-step1-1.png)

## <a name="enable-spatial-audio-on-your-workstation"></a>Aktivieren räumlicher Audiodaten auf Ihrer Arbeitsstation

Unter Desktop Versionen von Windows ist das räumliche Audioformat standardmäßig deaktiviert. Aktivieren Sie diese Option, indem Sie in der Taskleiste mit der rechten Maustaste auf das Volume-Symbol klicken. Um die beste Darstellung von hololens 2 zu erhalten, wählen Sie **räumliches Sound-> Windows-Sonic für Kopfhörer aus**.

![Desktop Einstellungen für räumliche Desktops](images/spatial-audio/spatial-audio-01-section4-step1-1.png)

> [!NOTE]
> Diese Einstellung ist nur erforderlich, wenn Sie Vorhaben, das Projekt im Unity-Editor zu testen.

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie erfahren, wie Sie das Microsoft spatializer-Plug-in importieren und aktivieren sowie das räumliche Audiomaterial auf Ihrer Arbeitsstation aktivieren.
Im nächsten Tutorial erfahren Sie, wie Sie räumliche Audiodaten im Unity-Projekt hinzufügen.

> [!div class="nextstepaction"]
> [Nächstes Tutorial: 2. spatialisieren von Schaltflächen-Interaktions Sounds](unity-spatial-audio-ch2.md)
