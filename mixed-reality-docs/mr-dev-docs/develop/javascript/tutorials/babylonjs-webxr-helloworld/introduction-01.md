---
title: Einführung in die Tutorials zu „babylon.js“ und WebXR
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie „babylon.js“ verwenden und eine einfache Mixed Reality-Anwendung erstellen.
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: Mixed Reality, JavaScript, Tutorial,BabylonJS, HoloLens, Mixed Reality, UWP, Windows 10, WebXR, immersives Web
ms.localizationpriority: high
ms.openlocfilehash: 2d3f59b2769f99a756c4f0c10df1d8a8604a595e
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600119"
---
# <a name="tutorial-create-your-first-webxr-application-using-babylonjs"></a><span data-ttu-id="8049f-104">Tutorial: Erstellen Ihrer ersten WebXR-Anwendung mit „babylon.js“</span><span class="sxs-lookup"><span data-stu-id="8049f-104">Tutorial: Create your first WebXR application using babylon.js</span></span>

<span data-ttu-id="8049f-105">In diesem Tutorial erfahren Sie, wie Sie mithilfe von „babylon.js“ und Visual Studio Code eine einfache Mixed Reality-App erstellen.</span><span class="sxs-lookup"><span data-stu-id="8049f-105">This tutorial will show you how to create a basic Mixed Reality app using babylon.js and Visual Studio Code.</span></span> <span data-ttu-id="8049f-106">Die App, die Sie erstellen werden, rendert einen Cube, ermöglicht es Ihnen, ihn zu drehen, um die anderen Flächen sichtbar zu machen, und Interaktionen hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="8049f-106">The app you're going to build will render a cube, let you rotate it to bring the other faces into view, and add interactions.</span></span> <span data-ttu-id="8049f-107">In diesem Tutorial lernen Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="8049f-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="8049f-108">Einrichten einer Entwicklungsumgebung</span><span class="sxs-lookup"><span data-stu-id="8049f-108">Set up a development environment</span></span>
> * <span data-ttu-id="8049f-109">Die „babylon.js“-API zum Erstellen einfacher 3D-Elemente</span><span class="sxs-lookup"><span data-stu-id="8049f-109">The babylon.js API to create basic 3D elements</span></span>  
> * <span data-ttu-id="8049f-110">Erstellen einer neuen Webseite</span><span class="sxs-lookup"><span data-stu-id="8049f-110">Create a new web page</span></span>
> * <span data-ttu-id="8049f-111">Interagieren mit einem 3D-Objekt</span><span class="sxs-lookup"><span data-stu-id="8049f-111">Interact with 3D elements</span></span>
> * <span data-ttu-id="8049f-112">Ausführen der Anwendung in einem Windows Mixed Reality-Simulator</span><span class="sxs-lookup"><span data-stu-id="8049f-112">Run the application in a Windows Mixed Reality Simulator</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8049f-113">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="8049f-113">Prerequisites</span></span>

* <span data-ttu-id="8049f-114">Von WebXR unterstützter Browser, z. B. [Microsoft Edge](../../../../whats-new/new-microsoft-edge.md)</span><span class="sxs-lookup"><span data-stu-id="8049f-114">WebXR-supported browser, for example [Microsoft Edge](../../../../whats-new/new-microsoft-edge.md)</span></span>
* <span data-ttu-id="8049f-115">[Babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 4.2 oder höher</span><span class="sxs-lookup"><span data-stu-id="8049f-115">[Babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 4.2 or higher</span></span>
* [<span data-ttu-id="8049f-116">NodeJS</span><span class="sxs-lookup"><span data-stu-id="8049f-116">NodeJS</span></span>](https://nodejs.org/)
* <span data-ttu-id="8049f-117">Optional: [Windows 10 Creator Update](https://www.microsoft.com/software-download/windows10), wenn Sie einen Windows Mixed Reality-Simulator verwenden möchten</span><span class="sxs-lookup"><span data-stu-id="8049f-117">Optional: [Windows 10 Creator Update](https://www.microsoft.com/software-download/windows10) if you want to use a Windows Mixed Reality Simulator</span></span>
* <span data-ttu-id="8049f-118">[Windows Mixed Reality-Simulator](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span><span class="sxs-lookup"><span data-stu-id="8049f-118">Optional: [Windows Mixed Reality simulator](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span></span>

## <a name="getting-started"></a><span data-ttu-id="8049f-119">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="8049f-119">Getting started</span></span>

<span data-ttu-id="8049f-120">Um dieses Projekt von Grund auf neu zu erstellen, beginnen Sie mit einem Visual Studio Code-Projekt (VSCode).</span><span class="sxs-lookup"><span data-stu-id="8049f-120">To create this project from scratch, start with a Visual Studio Code (VSCode) project.</span></span>

> [!NOTE]
> <span data-ttu-id="8049f-121">Die Verwendung von VSCode ist nicht obligatorisch, aber wir verwenden sie aus Gründen der Bequemlichkeit während des gesamten Tutorials.</span><span class="sxs-lookup"><span data-stu-id="8049f-121">Using VSCode isn't mandatory, but we'll be using it for convenience throughout the tutorial.</span></span> <span data-ttu-id="8049f-122">Erfahrenere JavaScript-Entwickler können einen beliebigen anderen Editor ihrer Wahl verwenden, sogar den einfachsten Editor.</span><span class="sxs-lookup"><span data-stu-id="8049f-122">More experienced JavaScript developers can use any other editor of their choice, even the simplest Notepad.</span></span>

1. <span data-ttu-id="8049f-123">Laden Sie entweder die Einzeldatei [babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) herunter, oder verwenden Sie eine Onlineversion, die auf der [offiziellen „babylon.js“-Website](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) zu finden ist.</span><span class="sxs-lookup"><span data-stu-id="8049f-123">Either download the [babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) single file or use an online version that can be found on the [official babylon.js web site](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers).</span></span> <span data-ttu-id="8049f-124">Sie können auch das gesamte „babylon.js“-Projekt von [GitHub](https://github.com/BabylonJS/Babylon.js) klonen.</span><span class="sxs-lookup"><span data-stu-id="8049f-124">You can also clone the entire babylon.js project from [GitHub](https://github.com/BabylonJS/Babylon.js)</span></span>
1. <span data-ttu-id="8049f-125">Erstellen Sie eine leere Datei, und speichern Sie sie als HTML-Seite, z. B. „index.html“.</span><span class="sxs-lookup"><span data-stu-id="8049f-125">Create an empty file and save it as html page, for example index.html</span></span>
1. <span data-ttu-id="8049f-126">Erstellen Sie ein einfaches HTML-Markup, und verweisen Sie auf die JavaScript-Datei „babylon.js“.</span><span class="sxs-lookup"><span data-stu-id="8049f-126">Create a basic html markup and reference the babylon.js javascript file.</span></span> <span data-ttu-id="8049f-127">Der endgültige Code sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="8049f-127">The final code is as shown below:</span></span>

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

1. <span data-ttu-id="8049f-128">Fügen Sie innerhalb des Textkörpers ein *canvas*-HTML-Element hinzu, um den Inhalt von „babylon.js“ zu rendern.</span><span class="sxs-lookup"><span data-stu-id="8049f-128">Add a *canvas* HTML element inside the body to render the contents of babylon.js.</span></span> <span data-ttu-id="8049f-129">Beachten Sie, dass der Zeichenbereich (canvas) ein ID-Attribut besitzt, mit dem Sie später aus JavaScript auf dieses HTML-Element zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="8049f-129">Note that the canvas has an id attribute, which lets you access this HTML element from JavaScript later on.</span></span>

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

1. <span data-ttu-id="8049f-130">Der Zeichenbereich nimmt die gesamte Webseite ein.</span><span class="sxs-lookup"><span data-stu-id="8049f-130">The canvas occupies the entire web page.</span></span> <span data-ttu-id="8049f-131">Damit ist unsere Webseite abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="8049f-131">That completes our web page.</span></span> <span data-ttu-id="8049f-132">An diesem Punkt ist die Webseite fertig.</span><span class="sxs-lookup"><span data-stu-id="8049f-132">At this point, the web page is ready.</span></span> <span data-ttu-id="8049f-133">Sie können sie in jedem Browser öffnen und sicherstellen, dass keine Fehler angezeigt werden, obwohl noch keine immersive Benutzeroberfläche vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="8049f-133">You can open it in any browser and ensure there are no errors shown, though there is no immersive experience yet.</span></span>

## <a name="next-steps"></a><span data-ttu-id="8049f-134">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="8049f-134">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8049f-135">Nächstes Tutorial: 2. Vorbereiten einer Szene</span><span class="sxs-lookup"><span data-stu-id="8049f-135">Next Tutorial: 2. Prepare a scene</span></span>](prepare-scene-02.md)