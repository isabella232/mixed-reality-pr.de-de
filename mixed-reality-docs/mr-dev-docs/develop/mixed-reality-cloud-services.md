---
layout: LandingPage
title: Übersicht der Azure Mixed Reality-Clouddienste
description: Erfahren Sie mehr über alle Azure Mixed Reality-Clouddienste, die Sie in Ihre Unity- oder Unreal-Anwendungen integrieren können.
author: hferrone
ms.author: v-haferr
ms.date: 12/9/2020
ms.topic: overview
ms.localizationpriority: high
keywords: Mixed Reality, entwickeln, Entwicklung, HoloLens, Clouddienste, Azure, Remote Rendering, Raumanker, Cognitive Services, Kognition, Unity, Machine Learning, Sprachübersetzung, maschinelles Sehen, Microsoft Graph
ms.openlocfilehash: e4ddfd5951945cc6a5bc9d7b71cad86a296fe725
ms.sourcegitcommit: cd2987467044fde1e2eb227e6c25d00e744aabfc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "98923810"
---
# <a name="azure-mixed-reality-cloud-services-overview"></a>Übersicht der Azure Mixed Reality-Clouddienste

![ Abbildung von Azure Spatial Anchors](../design/images/AzureSpatialAnchors.jpg)

Setzen Sie mit Azure Mixed Reality-Diensten frei, worin jeder Mensch Experte ist: die dreidimensionale physische Welt, in der wir leben. Helfen Sie Benutzern, durch das Erfassen und Anzeigen digitaler Informationen innerhalb des Kontexts ihrer Arbeit und ihrer Welt effektiver zu schaffen, zu lernen und zusammenzuarbeiten. Bringen Sie 3D auf mobile Geräte, in Headsets und auf andere nicht verbundene Geräte. Helfen Sie mit Azure, sicherzustellen, dass Ihre vertraulichsten Informationen geschützt sind.

## <a name="mixed-reality-services"></a>Mixed Reality-Dienste

Mixed Reality-Clouddienste, wie **Azure Remote Rendering** und **Azure Spatial Anchors**, unterstützen Entwickler beim Erstellen fesselnder immersiver Erfahrungen auf einer Vielzahl von Plattformen. Mithilfe dieser Dienste können Sie räumliche Wahrnehmung in Ihre Projekte integrieren, wenn Sie Anwendungen für 3D-Schulungen, die vorausschauende Wartung von Ausrüstungen und das Design Review erstellen, all das im Kontext der Umgebungen Ihrer Benutzer.

### <a name="azure-remote-rendering"></a>Azure Remote Rendering

[Azure Remote Rendering](https://docs.microsoft.com/azure/remote-rendering/) (ARR) ist ein Dienst, mit dem Sie hochgradig komplexe 3D-Modelle in Echtzeit rendern und auf ein Gerät streamen können. ARR ist zurzeit als öffentliche Vorschauversion erhältlich und kann Ihren Unity- oder nativen C++-Projekten für die Zielplattformen HoloLens 2 oder Windows Desktop-PC hinzugefügt werden.

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-Azure-Mixed-Reality-Services-Azure-Remote-Rendering/player]

ARR ist eine wesentliche Komponente jeder Mixed Reality-Anwendung, die auf einem nicht verbundenen Gerät ausgeführt wird, da diese weniger Rechenleistung für das Rendering aufweisen. Nehmen Sie die folgende Gegenüberstellung von Enginemodellen als Beispiel: Das hochauflösende Modell links weist mehr als 18 Millionen Dreiecke auf, während das reduzierte Modell auf der rechten Seite nur aus um die 200.000 besteht. In Szenarien, in denen es auf jedes Detail ankommt – Verwaltung von Industrieanlagen, Entwurfsrevision für Ressourcen wie LKW-Motoren, präoperative Planung von medizinischen Eingriffen – erfüllt 3D-Visualisierung diese Details mit Leben. Das ist es, was Entwicklern, Ingenieuren, Ärzten und Studenten hilft, komplexe Informationen besser zu verstehen und die richtige Entscheidung zu treffen. Diese Vereinfachung kann jedoch zu einem Verlust wichtiger Details führen, die für kritische Geschäfts- und Entwicklungsentscheidungen erforderlich sind.

![Beispiel für Azure Remote Rendering in einer Unity-Showcase-App](images/arr-engine.png)

ARR löst dieses Problem, indem es die Renderingworkloads auf High-End-GPUs in der Cloud auslagert. Dann übernimmt eine in der Cloud gehostete Grafik-Engine und rendert das Bild, codiert es als Videostream und streamt das Modell direkt auf das Zielgerät. 

* Bei komplexen Modellen, die auch eine High-End-GPU überfordern, verteilt ARR die Workload auf mehrere GPUs und führt das Ergebnis in einem einzelnen Bild zusammen, wodurch der Prozess für den Benutzer vollständig transparent wird. 

Als zusätzlicher Bonus schränkt ARR die Auswahl der Benutzeroberflächen, die Sie in Ihrer App verwenden können, nicht ein. Am Ende eines Frames wird Ihr lokal gerenderter Inhalt automatisch mit dem Remotebild kombiniert, wie in der Abbildung unten dargestellt:

![Beispiel für Azure Remote Rendering in einer Unity-Showcase-App](images/showcase-app.png)

### <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

[Azure Spatial Anchors](https://docs.microsoft.com /azure/spatial-anchors/) oder ASA ist ein plattformübergreifender Dienst, der es Ihnen ermöglicht, Mixed Reality-Anwendungen mit räumlicher Wahrnehmung zu erstellen. Mithilfe von Azure Spatial Anchors können Sie holografische Inhalte über mehrere Geräte und im realen Maßstab hinweg zuordnen, speichern und teilen. 

ASA ist eine einzigartige, maßgeschneiderte Lösung für gängige Anwendungsfälle in Mixed Reality, darunter:
* **Wegermittlung**: Hierbei können zwei oder mehr Raumanker verbunden werden, um eine Aufgabenliste oder Points-of-Interest zu erstellen, mit denen ein Benutzer interagieren muss.
* **Erfahrungen für mehrere Benutzer**: Hier können Benutzer Bewegungen vom einen zum anderen übergeben, indem sie mit Objekten im gleichen virtuellen Raum interagieren.
* **Dauerhafte virtuelle Inhalte in der realen Welt**: Hierbei können Benutzer virtuelle Objekte in der realen Welt platzieren, die auf anderen unterstützen Geräte sichtbar sind.

![Beispiel für Azure Spatial Anchors](images/persistence.gif)

Der Dienst kann in einer Vielzahl von Umgebungen und auf einer großen Gruppe von Geräten und Plattformen bereitgestellt werden. Dadurch erhalten sie eine besondere Freiheit gegenüber der eigenen Liste der verfügbaren Plattformen:
* Unity für HoloLens
* Unity für iOS
* Unity für Android
* iOS (nativ)
* Android (nativ)
* C++/WinRT und DirectX für HoloLens
* Xamarin für iOS
* Xamarin für Android

## <a name="cognitive-services"></a>Cognitive Services

:::row:::
    :::column:::
       [![Spracherkennung](../whats-new/images/speech.jpg)](/azure/cognitive-services/speech-service/)
    :::column-end:::
    :::column span="2":::
        ### <a name="speech"></a>[Speech](/azure/cognitive-services/speech-service/)
        Entdecken Sie, wie Speech die Integration von Funktionen zur Sprachverarbeitung in beliebige Apps oder Dienste ermöglicht. Konvertieren Sie gesprochene Sprache in Text, oder erzeugen Sie natürlich klingende Sprache aus Text mithilfe standardmäßiger (oder anpassbarer) Voicefonts. Probieren Sie jeden Dienst kostenlos aus – und erstellen Sie in kurzer Zeit Apps und Dienste mit Sprachunterstützung und den folgenden Funktionen.
    :::column-end:::
:::row-end:::

---

:::row:::
    :::column:::
       [![Bildanalyse](../whats-new/images/vision.jpg)](/azure/cognitive-services/computer-vision/)
    :::column-end:::
    :::column span="2":::
        ### <a name="vision"></a>[Bildanalyse](/azure/cognitive-services/computer-vision/)
        Erkennen, identifizieren, untertiteln, indizieren und moderieren Sie Ihre Inhalte in Bildern, Videos und digitalen Freihandzeichnungen. Erfahren Sie, wie die Bildanalyse es Apps und Diensten ermöglicht, Inhalte in Bildern, Videos und digitalen Freihandzeichnungen genau zu identifizieren und analysieren.
    :::column-end:::
:::row-end:::


## <a name="standalone-unity-services"></a>Eigenständige Unity-Dienste

Die unten aufgeführten eigenständigen Dienste betreffen nicht Mixed Reality, sie können aber in einer Vielzahl von Entwicklungskontexten nützlich sein. Wenn Sie in Unity entwickeln, kann jeder dieser Dienste in Ihre neuen oder vorhandenen Projekte integriert werden.

### <a name="device-support"></a>Geräteunterstützung
<table>
    <tr>
        <td><strong>Azure-Clouddienst</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1. Generation)</strong></a></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
    </tr>
     <tr>
        <td><a href="unity/tutorials/mr-azure-301.md">Sprachübersetzung</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-302.md">Maschinelles Sehen</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-302b.md">Custom Vision</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-303.md">Geräteübergreifende Benachrichtigungen</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-304.md">Gesichtserkennung</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-305.md">Funktionen und Speicher</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-306.md">Streamen von Video</a></td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-307.md">Maschinelles Lernen</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-308.md"mr-azure-308.md">Funktionen und Speicher</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-309.md">Application Insights</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-310.md">Objekterkennung</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-311.md">Microsoft Graph</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-312.md">Bot-Integration</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="see-also"></a>Siehe auch

* Tutorials zu Azure Spatial Anchors für HoloLens 2: [1 von 3 Erste Schritte mit Azure Spatial Anchors](./unity/tutorials/mr-learning-asa-02.md)
* Tutorials zu Azure Speech Services für HoloLens 2: [1 von 4 Integrieren und Verwenden von Spracherkennung und Transkription](../develop/unity/tutorials/mrlearning-speechSDK-ch1.md)