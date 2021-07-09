---
title: „Babylon.js“-Tutorial zum Vorbereiten einer Szene mit einfachen 3D-Objekten
description: Erfahren Sie, wie Sie „babylon.js“ verwenden und einer Szene einfache 3D-Objekte hinzufügen.
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: Mixed Reality, JavaScript, Tutorial,BabylonJS, HoloLens, Mixed Reality, UWP, Windows 10, WebXR, immersives Web
ms.localizationpriority: high
ms.openlocfilehash: 8213c445da9c1bbf0eeb591b7995fb61bc6d5b5f
ms.sourcegitcommit: 29a43366d5969f1a895bd184ebe272168d9be1e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2021
ms.locfileid: "110584504"
---
# <a name="tutorial-prepare-a-scene"></a><span data-ttu-id="bb7da-104">Tutorial: Vorbereiten einer Szene</span><span class="sxs-lookup"><span data-stu-id="bb7da-104">Tutorial: Prepare a scene</span></span>

<span data-ttu-id="bb7da-105">Erfahren Sie, wie Sie eine Szene vorbereiten und ihr einige einfache 3D-Elemente hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="bb7da-105">Learn how to prepare a scene, and add some basic 3D elements to it.</span></span>

<span data-ttu-id="bb7da-106">In diesem Tutorial lernen Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="bb7da-106">In this tutorial, learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="bb7da-107">Erstellen einer Szene</span><span class="sxs-lookup"><span data-stu-id="bb7da-107">Create a scene</span></span>
> * <span data-ttu-id="bb7da-108">Hinzufügen einer Kamera</span><span class="sxs-lookup"><span data-stu-id="bb7da-108">Add a camera</span></span>
> * <span data-ttu-id="bb7da-109">Hinzufügen von Licht</span><span class="sxs-lookup"><span data-stu-id="bb7da-109">Add light</span></span>
> * <span data-ttu-id="bb7da-110">Hinzufügen einfacher 3D-Elemente</span><span class="sxs-lookup"><span data-stu-id="bb7da-110">Add basic 3D elements</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="bb7da-111">Vorbereitung</span><span class="sxs-lookup"><span data-stu-id="bb7da-111">Before you begin</span></span>

<span data-ttu-id="bb7da-112">Im vorherigen Schritt des Tutorials wurde eine einfache Webseite erstellt.</span><span class="sxs-lookup"><span data-stu-id="bb7da-112">In previous tutorial step a basic web page was created.</span></span> <span data-ttu-id="bb7da-113">Lassen Sie die Webseite zur Bearbeitung geöffnet.</span><span class="sxs-lookup"><span data-stu-id="bb7da-113">Have the web page open for editing.</span></span>

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

## <a name="create-a-scene"></a><span data-ttu-id="bb7da-114">Erstellen einer Szene</span><span class="sxs-lookup"><span data-stu-id="bb7da-114">Create a scene</span></span>

<span data-ttu-id="bb7da-115">Eine Szene ist der Ort, an dem alle Inhalte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="bb7da-115">A scene is where all the contents will be displayed.</span></span> <span data-ttu-id="bb7da-116">Es kann mehrere Szenen geben, und es ist möglich, zwischen Szenen zu wechseln.</span><span class="sxs-lookup"><span data-stu-id="bb7da-116">There might be multiple scenes and it is possible to switch between scenes.</span></span> <span data-ttu-id="bb7da-117">Weitere Informationen zur [„babylon.js“-Szene](https://doc.babylonjs.com/divingDeeper/scene).</span><span class="sxs-lookup"><span data-stu-id="bb7da-117">Read more about [babylon.js Scene](https://doc.babylonjs.com/divingDeeper/scene).</span></span>

1. <span data-ttu-id="bb7da-118">Fügen Sie das Skripttag hinter dem „canvas“-HTML-Element hinzu, und fügen Sie den folgenden Code hinzu, um eine mit schwarzer Farbe ausgefüllte Szene zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="bb7da-118">Add the script tag after the canvas html element and add the following code to create a scene filled in black color:</span></span>

    ```html
    <script type="text/javascript">
        const canvas = document.getElementById("renderCanvas");
        const engine = new BABYLON.Engine(canvas, true);
        
        const createScene = function() {
            const scene = new BABYLON.Scene(engine);
            scene.clearColor = new BABYLON.Color3.Black;
            return scene;
        }

        const sceneToRender = createScene();
    </script>
    ```

    <span data-ttu-id="bb7da-119">Im obigen Code müssen wir eine Instanz der Webrendering-Engine von „babylon.js“ erstellen, die eine Szene rendert und Ereignisse im Zeichenbereich verankert.</span><span class="sxs-lookup"><span data-stu-id="bb7da-119">In the code above we have to create an instance of babylon.js web rendering engine that renders a scene and hooks events on the canvas.</span></span> <span data-ttu-id="bb7da-120">Weitere Informationen zu der Engine finden Sie auf der Dokumentationsseite [babylon.engine](https://doc.babylonjs.com/typedoc/classes/babylon.engine).</span><span class="sxs-lookup"><span data-stu-id="bb7da-120">For more information about the engine, check the documentation page [babylon.engine](https://doc.babylonjs.com/typedoc/classes/babylon.engine)</span></span>

1. <span data-ttu-id="bb7da-121">Die Szene wird nicht standardmäßig gerendert.</span><span class="sxs-lookup"><span data-stu-id="bb7da-121">The scene is not rendered by default.</span></span> <span data-ttu-id="bb7da-122">Denken Sie daran, dass es möglicherweise mehrere Szenen gibt, und Sie steuern, welche Szene angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="bb7da-122">Remember, there might be multiple scenes and you control which scene is displayed.</span></span> <span data-ttu-id="bb7da-123">Um die Szene wiederholt in jedem Frame zu rendern, führen Sie den folgenden Code nach dem Aufrufen der *createScene*-Funktion aus:</span><span class="sxs-lookup"><span data-stu-id="bb7da-123">To render the scene repeatedly on every frame, execute the following code after the call to *createScene* function:</span></span>

    ```javascript
    engine.runRenderLoop(function () {
        sceneToRender.render();
    });
    ```

## <a name="add-basic-3d-element"></a><span data-ttu-id="bb7da-124">Hinzufügen einfacher 3D-Elemente</span><span class="sxs-lookup"><span data-stu-id="bb7da-124">Add basic 3D element</span></span>

1. <span data-ttu-id="bb7da-125">Fügen wir unsere erste 3D-Form hinzu.</span><span class="sxs-lookup"><span data-stu-id="bb7da-125">Let's add our first 3D shape.</span></span> <span data-ttu-id="bb7da-126">In der virtuellen 3D-Welt werden Formen aus *Gittermodellen* erstellt, wobei viele dreieckige Facets miteinander verknüpft werden und jedes Facet aus drei Scheitelpunkten (vertices) besteht.</span><span class="sxs-lookup"><span data-stu-id="bb7da-126">In the 3D virtual world shapes are built from *meshes*, lots of triangular facets joined together, each facet made from three vertices.</span></span> <span data-ttu-id="bb7da-127">Sie können entweder ein vordefiniertes Gittermodell verwenden oder ein eigenes benutzerdefiniertes Gittermodell erstellen.</span><span class="sxs-lookup"><span data-stu-id="bb7da-127">You can either use a predefined mesh or create your own custom mesh.</span></span> <span data-ttu-id="bb7da-128">Hier verwenden wir ein vordefiniertes Box-Gittermodell, d. h. einen Würfel (Cube).</span><span class="sxs-lookup"><span data-stu-id="bb7da-128">Here we will be using a predefined box mesh, i.e. a cube.</span></span> <span data-ttu-id="bb7da-129">Verwenden Sie zum Erstellen der Box [BABYLON.MeshBuilder.CreateBox](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/box).</span><span class="sxs-lookup"><span data-stu-id="bb7da-129">To create the box use [BABYLON.MeshBuilder.CreateBox](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/box).</span></span> <span data-ttu-id="bb7da-130">Die Parameter sind „name“ und „options“ (die Optionen unterscheiden sich je nach Typ des Gittermodells).</span><span class="sxs-lookup"><span data-stu-id="bb7da-130">The parameters are name, and options (options are different according to the type of mesh).</span></span> <span data-ttu-id="bb7da-131">Fügen Sie den folgenden Code an die Funktion *createScene* an:</span><span class="sxs-lookup"><span data-stu-id="bb7da-131">Append the following code to the function *createScene*:</span></span>

    ```javascript
    const box = BABYLON.MeshBuilder.CreateBox("box", {});
    box.position.x = 0.5;
    box.position.y = 1;
    ```

1. <span data-ttu-id="bb7da-132">Öffnen Sie die Webseite im Microsoft Edge-Browser, und überprüfen Sie die Ausgabe.</span><span class="sxs-lookup"><span data-stu-id="bb7da-132">Open the web page in the Microsoft Edge browser and check the output.</span></span> <span data-ttu-id="bb7da-133">Im Browserfenster wird eine leere Seite angezeigt.</span><span class="sxs-lookup"><span data-stu-id="bb7da-133">The browser window shows a blank page.</span></span> <span data-ttu-id="bb7da-134">Öffnen Sie DevTools über die Tastatur, und drücken Sie F12 oder STRG+UMSCHALT+I (Windows, Linux) oder BEFEHL+WAHL+I (macOS).</span><span class="sxs-lookup"><span data-stu-id="bb7da-134">Open DevTools by using the keyboard and select F12 or Control+Shift+I (Windows, Linux) or Command+Option+I (macOS).</span></span> <span data-ttu-id="bb7da-135">Nachdem Sie die Registerkarte *Konsole* geöffnet haben, können Sie nach Fehlern suchen.</span><span class="sxs-lookup"><span data-stu-id="bb7da-135">After opening the *Console* tab, you can start looking for errors.</span></span> <span data-ttu-id="bb7da-136">Es wird ein Fehler angezeigt: „Uncaught Error: No camera defined.“ (Nicht abgefangener Fehler: Keine Kamera definiert.)</span><span class="sxs-lookup"><span data-stu-id="bb7da-136">There will be an error displayed: 'Uncaught Error: No camera defined'.</span></span> <span data-ttu-id="bb7da-137">Nun müssen wir der Szene eine Kamera hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="bb7da-137">Now we have to add a camera to the scene.</span></span>

## <a name="add-a-camera"></a><span data-ttu-id="bb7da-138">Hinzufügen einer Kamera</span><span class="sxs-lookup"><span data-stu-id="bb7da-138">Add a camera</span></span>

1. <span data-ttu-id="bb7da-139">Um die virtuelle Welt sehen und damit interagieren zu können, muss dem Zeichenbereich eine Kamera angefügt werden.</span><span class="sxs-lookup"><span data-stu-id="bb7da-139">In order to view the virtual world and interact with it, a camera must be attached to the canvas.</span></span> <span data-ttu-id="bb7da-140">Fügen Sie die Kamera vom Typ [BABYLON.ArcRotateCamera](https://doc.babylonjs.com/divingDeeper/cameras/camera_introduction#arc-rotate-camera) hinzu, die um ein Ziel herum gedreht werden kann.</span><span class="sxs-lookup"><span data-stu-id="bb7da-140">Let's add the camera of type [BABYLON.ArcRotateCamera](https://doc.babylonjs.com/divingDeeper/cameras/camera_introduction#arc-rotate-camera), which can be rotated around a target.</span></span> <span data-ttu-id="bb7da-141">Folgende Parameter sind erforderlich, um eine Instanz der Kamera zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="bb7da-141">The parameters required to create an instance of the camera are:</span></span>
    1. <span data-ttu-id="bb7da-142">**name**: Name der Kamera.</span><span class="sxs-lookup"><span data-stu-id="bb7da-142">**name**: name of the camera</span></span>
    1. <span data-ttu-id="bb7da-143">**alpha**: Winkelposition entlang der Längsachse (im Bogenmaß).</span><span class="sxs-lookup"><span data-stu-id="bb7da-143">**alpha**: angular position along the longitudinal axis (in radians)</span></span>
    1. <span data-ttu-id="bb7da-144">**beta**: Winkelposition entlang der Querachse (im Bogenmaß).</span><span class="sxs-lookup"><span data-stu-id="bb7da-144">**beta**: angular position along the latitudinal axis (in radians)</span></span>
    1. <span data-ttu-id="bb7da-145">**radius**: Entfernung vom Ziel.</span><span class="sxs-lookup"><span data-stu-id="bb7da-145">**radius**: distance from the target</span></span>
    1. <span data-ttu-id="bb7da-146">**target**: Der Punkt, auf den die Kamera immer gerichtet ist (definiert durch x-y-z-Koordinaten).</span><span class="sxs-lookup"><span data-stu-id="bb7da-146">**target**: the point that the camera would always face towards (defined by x-y-z coordinates)</span></span>
    1. <span data-ttu-id="bb7da-147">**scene**: Die Szene, in der sich die Kamera befindet.</span><span class="sxs-lookup"><span data-stu-id="bb7da-147">**scene**: the scene that the camera is in</span></span>

    <span data-ttu-id="bb7da-148">„alpha“, „beta“, „radius“ und „target“ zusammen definieren die Position der Kamera im Raum, wie im folgenden Diagramm dargestellt:</span><span class="sxs-lookup"><span data-stu-id="bb7da-148">Alpha, beta, radius, and target together define the camera's position in the space, as shown in the diagram below:</span></span>

    ![Kamera alpha beta radius](../images/camera-alpha-beta-radius.jpg)

    <span data-ttu-id="bb7da-150">Fügen Sie der Funktion *createScene* den folgenden Code an:</span><span class="sxs-lookup"><span data-stu-id="bb7da-150">Add the following code to the *createScene* function:</span></span>

    ```javascript
    const alpha =  Math.PI/4;
    const beta = Math.PI/3;
    const radius = 8;
    const target = new BABYLON.Vector3(0, 0, 0);
    
    const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
    camera.attachControl(canvas, true);
    ```

1. <span data-ttu-id="bb7da-151">Wenn Sie die Ausgabe im Browser überprüfen, wird ein schwarzer Zeichenbereich angezeigt.</span><span class="sxs-lookup"><span data-stu-id="bb7da-151">If you check the output in the browser, you will see a black canvas.</span></span> <span data-ttu-id="bb7da-152">Uns fehlt das Licht.</span><span class="sxs-lookup"><span data-stu-id="bb7da-152">We are missing the light.</span></span>

## <a name="add-light"></a><span data-ttu-id="bb7da-153">Hinzufügen von Licht</span><span class="sxs-lookup"><span data-stu-id="bb7da-153">Add light</span></span>

1. <span data-ttu-id="bb7da-154">Es gibt vier Arten von Lichtern, die mit einer Reihe von Beleuchtungseigenschaften verwendet werden können: Point (Punkt), Directional (gerichtet), Spot und Hemispheric (hemisphärisch/Halbkugel).</span><span class="sxs-lookup"><span data-stu-id="bb7da-154">There are four types of lights that can be used with a range of lighting properties: Point, Directional, Spot and Hemispheric Light.</span></span> <span data-ttu-id="bb7da-155">Fügen Sie das Umgebungslicht vom Typ [HemisphericLight](https://doc.babylonjs.com/typedoc/classes/babylon.hemisphericlight) wie folgt hinzu:</span><span class="sxs-lookup"><span data-stu-id="bb7da-155">Let's add the ambient light [HemisphericLight](https://doc.babylonjs.com/typedoc/classes/babylon.hemisphericlight), as follows:</span></span>

    ```javascript
    const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(1, 1, 0));
    ```

1. <span data-ttu-id="bb7da-156">Der endgültige Code der Webseite sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="bb7da-156">The final code of the web page will look as follows:</span></span>

    ```html
    <html>
    <head>
        <script src="https://cdn.babylonjs.com/babylon.js"></script>
        <style>
            body,#renderCanvas { width: 100%; height: 100%;}
        </style>
    </head>
    <body>
        <canvas id="renderCanvas"></canvas>
        <script>
            const canvas = document.getElementById("renderCanvas");
            const engine = new BABYLON.Engine(canvas, true);
            
            const createScene = function() {
                const scene = new BABYLON.Scene(engine);
                scene.clearColor = new BABYLON.Color3.Black;
                
                const alpha =  Math.PI/4;
                const beta = Math.PI/3;
                const radius = 8;
                const target = new BABYLON.Vector3(0, 0, 0);
                
                const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
                camera.attachControl(canvas, true);
                
                const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(1, 1, 0));
                
                const box = BABYLON.MeshBuilder.CreateBox("box", {});
                box.position.x = 0.5;
                box.position.y = 1;
                
                return scene;
            };
            
            const sceneToRender = createScene();
            engine.runRenderLoop(function(){
                sceneToRender.render();
            });
        </script>
    </body>
    </html>
    ```

1. <span data-ttu-id="bb7da-157">Überprüfen Sie die Ausgabe im Browser.</span><span class="sxs-lookup"><span data-stu-id="bb7da-157">Check the output in the browser.</span></span> <span data-ttu-id="bb7da-158">Der Würfel sollte zu sehen sein, und mit der Maus können Sie die Kamera um den Würfel herum drehen und so die verschiedenen Flächen des Würfels sehen:</span><span class="sxs-lookup"><span data-stu-id="bb7da-158">You should see the cube and using the mouse you can rotate the camera around the cube and see the different faces of the cube:</span></span>

![Einfache Szene mit Würfel (Cube)](../images/hello-world-basic-scene.png)

## <a name="next-steps"></a><span data-ttu-id="bb7da-160">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="bb7da-160">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bb7da-161">Nächstes Tutorial: 3. Interagieren mit einem 3D-Objekt</span><span class="sxs-lookup"><span data-stu-id="bb7da-161">Next Tutorial: 3. Interact with 3D object</span></span>](interact-03.md)
