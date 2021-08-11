---
title: Einführung in die Tutorials zu „babylon.js“ und WebXR
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie „babylon.js“ verwenden und eine einfache Mixed Reality-Anwendung erstellen.
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: Mixed Reality, JavaScript, Tutorial,BabylonJS, HoloLens, Mixed Reality, UWP, Windows 10, WebXR, immersives Web
ms.localizationpriority: high
ms.openlocfilehash: e2006e911ad9dae00252c929c7739ff2209f4bf7796f1c49e713cfaf53267cd2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196824"
---
# <a name="tutorial-create-your-first-webxr-application-using-babylonjs"></a>Tutorial: Erstellen Ihrer ersten WebXR-Anwendung mit „babylon.js“

In diesem Tutorial erfahren Sie, wie Sie mithilfe von „babylon.js“ und Visual Studio Code eine einfache Mixed Reality-App erstellen. Die App, die Sie erstellen werden, rendert einen Cube, ermöglicht es Ihnen, ihn zu drehen, um die anderen Flächen sichtbar zu machen, und Interaktionen hinzuzufügen. In diesem Tutorial lernen Sie Folgendes:

> [!div class="checklist"]
> * Einrichten einer Entwicklungsumgebung
> * Die „babylon.js“-API zum Erstellen einfacher 3D-Elemente  
> * Erstellen einer neuen Webseite
> * Interagieren mit einem 3D-Objekt
> * Ausführen der Anwendung in einem Windows Mixed Reality-Simulator

## <a name="prerequisites"></a>Voraussetzungen

* Von WebXR unterstützter Browser, z. B. [Microsoft Edge](../../../../whats-new/new-microsoft-edge.md)
* [Babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 4.2 oder höher
* [NodeJS](https://nodejs.org/)
* Optional: [Windows 10 Creator Update](https://www.microsoft.com/software-download/windows10), wenn Sie einen Windows Mixed Reality-Simulator verwenden möchten
* [Windows Mixed Reality-Simulator](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="getting-started"></a>Erste Schritte

Um dieses Projekt von Grund auf neu zu erstellen, beginnen Sie mit einem Visual Studio Code-Projekt (VSCode).

> [!NOTE]
> Die Verwendung von VSCode ist nicht obligatorisch, aber wir verwenden sie aus Gründen der Bequemlichkeit während des gesamten Tutorials. Erfahrenere JavaScript-Entwickler können einen beliebigen anderen Editor ihrer Wahl verwenden, sogar den einfachsten Editor.

1. Laden Sie entweder die Einzeldatei [babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) herunter, oder verwenden Sie eine Onlineversion, die auf der [offiziellen „babylon.js“-Website](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) zu finden ist. Sie können auch das gesamte „babylon.js“-Projekt von [GitHub](https://github.com/BabylonJS/Babylon.js) klonen.
1. Erstellen Sie eine leere Datei, und speichern Sie sie als HTML-Seite, z. B. „index.html“.
1. Erstellen Sie ein einfaches HTML-Markup, und verweisen Sie auf die JavaScript-Datei „babylon.js“. Der endgültige Code sieht wie folgt aus:

    ```html
    <html>
        <head>
            <title>Babylon.js sample code</title>
            <script src="https://cdn.babylonjs.com/babylon.js"></script>
        </head>
    <body>
    </body>
    </html>
    ```

1. Fügen Sie innerhalb des Textkörpers ein *canvas*-HTML-Element hinzu, um den Inhalt von „babylon.js“ zu rendern. Beachten Sie, dass der Zeichenbereich (canvas) ein ID-Attribut besitzt, mit dem Sie später aus JavaScript auf dieses HTML-Element zugreifen können.

    ```html
    <html>
        <head>
            <title>Babylon.js sample code</title>
            <script src="https://cdn.babylonjs.com/babylon.js"></script>
            <style>
                body,#renderCanvas { width: 100%; height: 100%;}
            </style>
        </head>
    <body>
        <canvas id="renderCanvas"></canvas>
    </body>
    </html>
    ```

1. Der Zeichenbereich nimmt die gesamte Webseite ein. Damit ist unsere Webseite abgeschlossen. An diesem Punkt ist die Webseite fertig. Sie können sie in jedem Browser öffnen und sicherstellen, dass keine Fehler angezeigt werden, obwohl noch keine immersive Benutzeroberfläche vorhanden ist.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Nächstes Tutorial: 2. Vorbereiten einer Szene](prepare-scene-02.md)