---
title: „Babylon.js“-Tutorial zur Interaktion mit 3D-Objekten
description: Erfahren Sie, wie Sie „babylon.js“ verwenden und mit 3D-Objekten zu interagieren.
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: Mixed Reality, JavaScript, Tutorial,BabylonJS, HoloLens, Mixed Reality, UWP, Windows 10, WebXR, immersives Web
ms.localizationpriority: high
ms.openlocfilehash: a3dbab0572cd50105dac3d877a0d72c5cbc504b6
ms.sourcegitcommit: 29a43366d5969f1a895bd184ebe272168d9be1e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2021
ms.locfileid: "110584519"
---
# <a name="tutorial-interact-with-3d-object"></a><span data-ttu-id="fdb1f-104">Tutorial: Interagieren mit einem 3D-Objekt</span><span class="sxs-lookup"><span data-stu-id="fdb1f-104">Tutorial: Interact with 3D object</span></span>

<span data-ttu-id="fdb1f-105">Erfahren Sie, wie Sie mithilfe von „babylon.js“ 3D-Objekte und Interaktionen für eine Mixed Reality-Erfahrung erstellen.</span><span class="sxs-lookup"><span data-stu-id="fdb1f-105">Learn how to create 3D objects and interactions for a Mixed Reality experience using babylon.js.</span></span> <span data-ttu-id="fdb1f-106">In diesem Abschnitt beginnen Sie mit etwas Einfachem, z. B. dem Zeichnen der Flächen eines Würfels (cube), wenn Sie das Objekt auswählen.</span><span class="sxs-lookup"><span data-stu-id="fdb1f-106">In this section, you'll start with something simple, like painting the faces of a cube when you select the object.</span></span>

<span data-ttu-id="fdb1f-107">Dieses Tutorial behandelt die folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="fdb1f-107">This tutorial covers the following topics:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="fdb1f-108">Hinzufügen von Interaktionen</span><span class="sxs-lookup"><span data-stu-id="fdb1f-108">How to add interactions</span></span>
> * <span data-ttu-id="fdb1f-109">Aktivieren des immersiven WebXR-Modus</span><span class="sxs-lookup"><span data-stu-id="fdb1f-109">Enable WebXR immersive mode</span></span>
> * <span data-ttu-id="fdb1f-110">Ausführen der App im Windows Mixed Reality-Simulator</span><span class="sxs-lookup"><span data-stu-id="fdb1f-110">Run the app on Windows Mixed Reality Simulator</span></span>
> * <span data-ttu-id="fdb1f-111">Ausführen und Debuggen der App in Android Chrome</span><span class="sxs-lookup"><span data-stu-id="fdb1f-111">Run and debug the app on Android Chrome</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="fdb1f-112">Vorbereitung</span><span class="sxs-lookup"><span data-stu-id="fdb1f-112">Before you begin</span></span>

<span data-ttu-id="fdb1f-113">Im vorherigen Schritt des Tutorials wurde eine einfache Webseite mit einer Szene erstellt.</span><span class="sxs-lookup"><span data-stu-id="fdb1f-113">In previous tutorial step a basic web page with a scene was created.</span></span> <span data-ttu-id="fdb1f-114">Lassen Sie die Hostingwebseite zur Bearbeitung geöffnet.</span><span class="sxs-lookup"><span data-stu-id="fdb1f-114">Have the hosting web page open for editing.</span></span>

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

## <a name="add-interaction"></a><span data-ttu-id="fdb1f-115">Hinzufügen einer Interaktion</span><span class="sxs-lookup"><span data-stu-id="fdb1f-115">Add interaction</span></span>

1. <span data-ttu-id="fdb1f-116">Zunächst aktualisieren wir unseren Code, der den Würfel erstellt, sodass der Würfel mit einer zufälligen Farbe gezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="fdb1f-116">First, let's update our code that creates the cube, so that the cube is painted with a random color.</span></span> <span data-ttu-id="fdb1f-117">Dazu fügen wir unserem Würfel [Material](https://doc.babylonjs.com/divingDeeper/materials/using/materials_introduction) hinzu.</span><span class="sxs-lookup"><span data-stu-id="fdb1f-117">To do that, we will add [material](https://doc.babylonjs.com/divingDeeper/materials/using/materials_introduction) to our cube.</span></span> <span data-ttu-id="fdb1f-118">Material ermöglicht es uns, Farbe und Texturen anzugeben, und es kann verwendet werden, um andere Objekte zu bedecken.</span><span class="sxs-lookup"><span data-stu-id="fdb1f-118">Material allows us to specify color and textures and can be used to cover other objects.</span></span> <span data-ttu-id="fdb1f-119">Wie ein Material angezeigt wird, hängt vom Licht oder den Beleuchtungen ab, die in der Szene verwendet werden, und davon, wie seine Reaktionen festgelegt sind.</span><span class="sxs-lookup"><span data-stu-id="fdb1f-119">How a material appears depends on the light or lights used in the scene and how it is set to react.</span></span> <span data-ttu-id="fdb1f-120">„diffuseColor“ verteilt beispielsweise die Farbe über das gesamte Gittermodell, an die sie angefügt ist.</span><span class="sxs-lookup"><span data-stu-id="fdb1f-120">For example, the diffuseColor spreads the color all over the mesh to which it is attached.</span></span> <span data-ttu-id="fdb1f-121">Fügen Sie den folgenden Code hinzu:</span><span class="sxs-lookup"><span data-stu-id="fdb1f-121">Add the following code:</span></span>

    ```javascript
    const boxMaterial = new BABYLON.StandardMaterial("material", scene);
    boxMaterial.diffuseColor = BABYLON.Color3.Random();
    box.material = boxMaterial;
    ```

1. <span data-ttu-id="fdb1f-122">Nachdem der Würfel nun mit einer zufälligen Farbe gezeichnet wurde, fügen wir eine Interaktion für Folgendes hinzu:</span><span class="sxs-lookup"><span data-stu-id="fdb1f-122">Now that the cube is painted with a random color, let's add an interaction to:</span></span>

    * <span data-ttu-id="fdb1f-123">Ändern der Farbe beim Klicken auf den Würfel</span><span class="sxs-lookup"><span data-stu-id="fdb1f-123">Change the color when the cube is clicked</span></span>
    * <span data-ttu-id="fdb1f-124">Bewegen des Würfels nach dem Ändern der Farbe</span><span class="sxs-lookup"><span data-stu-id="fdb1f-124">Move the cube after the color is changed</span></span>

    <span data-ttu-id="fdb1f-125">Zum Hinzufügen von Interaktionen sollten wir [Aktionen](https://doc.babylonjs.com/divingDeeper/events/actions) verwenden.</span><span class="sxs-lookup"><span data-stu-id="fdb1f-125">To add interactions we should be using [actions](https://doc.babylonjs.com/divingDeeper/events/actions).</span></span> <span data-ttu-id="fdb1f-126">Eine Aktion wird als Reaktion auf den Ereignistrigger gestartet.</span><span class="sxs-lookup"><span data-stu-id="fdb1f-126">An action is launched in response to the event trigger.</span></span> <span data-ttu-id="fdb1f-127">Beispielsweise, wenn der Benutzer auf den Würfel klickt.</span><span class="sxs-lookup"><span data-stu-id="fdb1f-127">For example, when the user clicks on the cube.</span></span> <span data-ttu-id="fdb1f-128">Alles, was wir tun müssen, ist „BABYLON.ActionManager“ zu instanziieren und eine Aktion für einen bestimmten Trigger zu registrieren.</span><span class="sxs-lookup"><span data-stu-id="fdb1f-128">All we need to do is instantiate BABYLON.ActionManager and register an action for certain trigger.</span></span> <span data-ttu-id="fdb1f-129">Die [BABYLON.ExecuteCodeAction](https://doc.babylonjs.com/typedoc/classes/babylon.executecodeaction) führt unsere JavaScript-Funktion aus, wenn jemand auf den Würfel klickt:</span><span class="sxs-lookup"><span data-stu-id="fdb1f-129">The [BABYLON.ExecuteCodeAction](https://doc.babylonjs.com/typedoc/classes/babylon.executecodeaction) will run our JavaScript function when someone clicks on the cube:</span></span>

    ```javascript
    box.actionManager = new BABYLON.ActionManager(scene);
    box.actionManager.registerAction(new BABYLON.ExecuteCodeAction(
        BABYLON.ActionManager.OnPickTrigger, 
        function (evt) {
            const sourceBox = evt.meshUnderPointer;
            
            //move the box upright
            sourceBox.position.x += 0.1;
            sourceBox.position.y += 0.1;

            //update the color
            boxMaterial.diffuseColor = BABYLON.Color3.Random();
        }));
    ```

1. <span data-ttu-id="fdb1f-130">Der endgültige Code der Webseite sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="fdb1f-130">The final code of the web page will look as follows:</span></span>

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

                const boxMaterial = new BABYLON.StandardMaterial("material", scene);
                boxMaterial.diffuseColor = BABYLON.Color3.Random();
                box.material = boxMaterial;
 
                box.actionManager = new BABYLON.ActionManager(scene);
                box.actionManager.registerAction(
                    new BABYLON.ExecuteCodeAction(BABYLON.ActionManager.OnPickTrigger, 
                    function (evt) {
                        const sourceBox = evt.meshUnderPointer;
                        sourceBox.position.x += 0.1;
                        sourceBox.position.y += 0.1;

                        boxMaterial.diffuseColor = BABYLON.Color3.Random();
                    }));

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

## <a name="enable-webxr-immersive-experience"></a><span data-ttu-id="fdb1f-131">Aktivieren der immersiven WebXR-Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="fdb1f-131">Enable WebXR immersive experience</span></span>

<span data-ttu-id="fdb1f-132">Nachdem sich die Farbe des Würfels nun ändert, können wir die immersive Erfahrung ausprobieren.</span><span class="sxs-lookup"><span data-stu-id="fdb1f-132">Now that our cube is changing colors, we're ready to try the immersive experience.</span></span>

1. <span data-ttu-id="fdb1f-133">In diesem Schritt führen wir einen [Boden](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/ground) ein.</span><span class="sxs-lookup"><span data-stu-id="fdb1f-133">In this step we're going to introduce a [ground](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/ground).</span></span> <span data-ttu-id="fdb1f-134">Der Würfel hängt in der Luft, und unten sehen wir einen Boden.</span><span class="sxs-lookup"><span data-stu-id="fdb1f-134">The cube will be hanging in the air and we will see a floor at the bottom.</span></span> <span data-ttu-id="fdb1f-135">Fügen Sie den Boden wie folgt hinzu:</span><span class="sxs-lookup"><span data-stu-id="fdb1f-135">Add the ground as follows:</span></span>

    ```javascript
    const ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 4, height: 4});
    ```

    <span data-ttu-id="fdb1f-136">Hierdurch wird ein einfacher 4x4-Meter-Boden erstellt.</span><span class="sxs-lookup"><span data-stu-id="fdb1f-136">This creates a simple 4x4-meter floor.</span></span>

1. <span data-ttu-id="fdb1f-137">Um WebXR-Unterstützung hinzuzufügen, müssen wir *createDefaultXRExperienceAsync* aufrufen, das ein *Zusage*-Ergebnis (promise) aufweist.</span><span class="sxs-lookup"><span data-stu-id="fdb1f-137">In order to add WebXR support, we need to call *createDefaultXRExperienceAsync*, which has a *Promise* result.</span></span> <span data-ttu-id="fdb1f-138">Fügen Sie diesen Code am Ende der *createScene*-Funktion anstelle von *return scene* (Szene zurückgeben) hinzu:</span><span class="sxs-lookup"><span data-stu-id="fdb1f-138">Add this code at the end of *createScene* function instead of *return scene;*:</span></span>

    ```javascript
    const xrPromise = scene.createDefaultXRExperienceAsync({
        floorMeshes: [ground]
    });
    return xrPromise.then((xrExperience) => {
        console.log("Done, WebXR is enabled.");
        return scene;
    });
    ```

1. <span data-ttu-id="fdb1f-139">Da die *createScene*-Funktion jetzt eine Zusage anstelle einer Szene zurückgibt, müssen wir ändern, wie *createScene* und *engine.runRenderLoop* aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="fdb1f-139">Since the *createScene* function is now returning a promise instead of a scene, we need to modify how *createScene* and *engine.runRenderLoop* are called.</span></span> <span data-ttu-id="fdb1f-140">Ersetzen Sie die aktuellen Aufrufe dieser Funktionen, die sich direkt vor dem *\</script>* -Tag befinden, durch den folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="fdb1f-140">Replace the current calls of these functions, which are located right before the *\</script>* tag, with the code below:</span></span>

    ```javascript
    createScene().then(sceneToRender => {
        engine.runRenderLoop(() => sceneToRender.render());
    });
    ```

1. <span data-ttu-id="fdb1f-141">Der endgültige Code der Webseite sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="fdb1f-141">The final code of the web page will look as follows:</span></span>

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

                const boxMaterial = new BABYLON.StandardMaterial("material", scene);
                boxMaterial.diffuseColor = BABYLON.Color3.Random();
                box.material = boxMaterial;
 
                box.actionManager = new BABYLON.ActionManager(scene);
                box.actionManager.registerAction(
                    new BABYLON.ExecuteCodeAction(BABYLON.ActionManager.OnPickTrigger, 
                    function (evt) {
                        const sourceBox = evt.meshUnderPointer;
                        sourceBox.position.x += 0.1;
                        sourceBox.position.y += 0.1;

                        boxMaterial.diffuseColor = BABYLON.Color3.Random();
                    }));
                    
                const ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 4, height: 4});
                
                const xrPromise = scene.createDefaultXRExperienceAsync({
                    floorMeshes: [ground]
                });
                
                return xrPromise.then((xrExperience) => {
                    console.log("Done, WebXR is enabled.");
                    return scene;
                });
            };
            
            createScene().then(sceneToRender => {
                engine.runRenderLoop(() => sceneToRender.render());
            });
        </script>
    </body>
    </html>
    ```

1. <span data-ttu-id="fdb1f-142">Der obige Code generiert die folgende Ausgabe im Browserfenster: ![WebXR-Szene](../images/hello-world-webxr-scene.png)</span><span class="sxs-lookup"><span data-stu-id="fdb1f-142">The above code generates the following output in the browser window: ![WebXR scene](../images/hello-world-webxr-scene.png)</span></span>

## <a name="run-on-a-windows-mixed-reality-simulator"></a><span data-ttu-id="fdb1f-143">Ausführen in einem Windows Mixed Reality-Simulator</span><span class="sxs-lookup"><span data-stu-id="fdb1f-143">Run on a Windows Mixed Reality Simulator</span></span>

1. <span data-ttu-id="fdb1f-144">[Aktivieren Sie den Windows Mixed Reality-Simulator](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md), wenn Sie dies in der Vergangenheit noch nicht getan haben.</span><span class="sxs-lookup"><span data-stu-id="fdb1f-144">[Enable the Windows Mixed Reality Simulator](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) if you have not done so in the past.</span></span>

1. <span data-ttu-id="fdb1f-145">Wählen Sie die Schaltfläche „Immersive VR“ in der unteren rechten Ecke aus: ![Schaltfläche „Immersive VR“](../images/immersive-vr-button.png)</span><span class="sxs-lookup"><span data-stu-id="fdb1f-145">Select the Immersive-VR button on the bottom right corner: ![Immersive VR Button](../images/immersive-vr-button.png)</span></span>

1. <span data-ttu-id="fdb1f-146">Mit dieser Aktion wird das Fenster „Windows Mixed Reality-Simulator“ wie unten dargestellt gestartet: ![ Mixed Reality-Portal](../images/mixed-reality-portal.png)</span><span class="sxs-lookup"><span data-stu-id="fdb1f-146">This action will launch the Windows Mixed Reality Simulator window as shown below: ![Mixed Reality Portal](../images/mixed-reality-portal.png)</span></span>

1. <span data-ttu-id="fdb1f-147">Verwenden Sie die Tasten W, A, S und D auf ihrer Tastatur, um entsprechend vorwärts, zurück, links und rechts zu gehen.</span><span class="sxs-lookup"><span data-stu-id="fdb1f-147">Use the W,A,S, and D keys on your keyboard to walk forward, back left and right accordingly.</span></span> <span data-ttu-id="fdb1f-148">Verwenden Sie die simulierte Hand, um den Würfel anzuvisieren, und drücken Sie die EINGABETASTE auf der Tastatur, um die Klickaktion auszuführen.</span><span class="sxs-lookup"><span data-stu-id="fdb1f-148">Use simulated hand to target the cube and press the Enter key on your keyboard to perform the click action.</span></span> <span data-ttu-id="fdb1f-149">Der Würfel ändert seine Farbe und bewegt sich an eine neue Position.</span><span class="sxs-lookup"><span data-stu-id="fdb1f-149">The cube will change its color and move to a new position.</span></span>

> [!NOTE]
> <span data-ttu-id="fdb1f-150">Stellen Sie beim Anvisieren des Würfels sicher, dass sich das Ende des Handstrahls (weißer Kreis) wie in der Abbildung oben gezeigt mit dem Würfel überschneidet.</span><span class="sxs-lookup"><span data-stu-id="fdb1f-150">When targeting the cube, make sure that the end of hand ray (white circle) intersects with the cube as shown on the picture above.</span></span> <span data-ttu-id="fdb1f-151">Erfahren Sie mehr über [Zeigen und Ausführen mit den Händen](../../../../design/point-and-commit.md).</span><span class="sxs-lookup"><span data-stu-id="fdb1f-151">Learn more about [Point and commit with hands](../../../../design/point-and-commit.md).</span></span>

## <a name="run-and-debug-on-android-device"></a><span data-ttu-id="fdb1f-152">Ausführen und Debuggen auf einem Android-Gerät</span><span class="sxs-lookup"><span data-stu-id="fdb1f-152">Run and debug on Android device</span></span>

<span data-ttu-id="fdb1f-153">Führen Sie die folgenden Schritte aus, um das Debuggen auf Ihrem Android-Gerät zu aktivieren:</span><span class="sxs-lookup"><span data-stu-id="fdb1f-153">Perform the following steps to enable debugging on your Android device:</span></span>

### <a name="prerequisites"></a><span data-ttu-id="fdb1f-154">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="fdb1f-154">Prerequisites</span></span>

* <span data-ttu-id="fdb1f-155">Ein Webserver, der statische HTML-Seiten im sicheren Kontext („https://“ oder über Portweiterleitung auf dem „localhost“) auf dem Entwicklungscomputer bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="fdb1f-155">A web server that serves static html page in secure context (https:// or via Port forwarding on localhost) on development machine.</span></span> <span data-ttu-id="fdb1f-156">Nutzen Sie beispielsweise das npm-Paket *serve* als einfachen, schlanken Webserver, der statische HTML-Dateien bereitstellt. Weitere Informationen finden Sie unter [npm serve](https://github.com/vercel/serve#readme).</span><span class="sxs-lookup"><span data-stu-id="fdb1f-156">For example leverage *serve* npm package as simple lightweight web server that serves static html files, check more [npm serve](https://github.com/vercel/serve#readme)</span></span>
* <span data-ttu-id="fdb1f-157">Das Gerät wurde ursprünglich über den Google Play Store ausgeliefert und muss Android 7.0 oder höher ausführen.</span><span class="sxs-lookup"><span data-stu-id="fdb1f-157">The device originally shipped with the Google Play Store and must be running Android 7.0 or newer</span></span>
* <span data-ttu-id="fdb1f-158">Die neueste Version von [Google Chrome](https://support.google.com/chrome/answer/95346) sowohl auf der Entwicklungsarbeitsstation als auch auf dem Gerät</span><span class="sxs-lookup"><span data-stu-id="fdb1f-158">The latest version of [Google Chrome](https://support.google.com/chrome/answer/95346) on both the development workstation and on the device</span></span>
* <span data-ttu-id="fdb1f-159">Um zu überprüfen, ob das Gerät ordnungsgemäß für die Ausführung von WebXR konfiguriert ist, wechseln Sie zu einer [WebXR-Beispielseite](https://immersive-web.github.io/webxr-samples/) auf dem Gerät.</span><span class="sxs-lookup"><span data-stu-id="fdb1f-159">To verify that the device is correctly configured to run WebXR, browse to a [sample WebXR page](https://immersive-web.github.io/webxr-samples/) on the device.</span></span> <span data-ttu-id="fdb1f-160">Ungefähr die folgende Meldung sollte angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="fdb1f-160">You should see the message, such as:</span></span>

    > <span data-ttu-id="fdb1f-161">Ihr Browser unterstützt WebXR und kann Virtual Reality- und Augmented Reality-Erfahrungen ausführen, wenn Sie über die entsprechende Hardware verfügen.</span><span class="sxs-lookup"><span data-stu-id="fdb1f-161">Your browser supports WebXR and can run Virtual Reality and Augmented Reality experiences if you have the appropriate hardware.</span></span>

1. <span data-ttu-id="fdb1f-162">Aktivieren sie den Entwicklermodus und USB-Debugging auf einem Android-Gerät.</span><span class="sxs-lookup"><span data-stu-id="fdb1f-162">Enable developer mode and USB debugging on an Android device.</span></span> <span data-ttu-id="fdb1f-163">Informationen zur Vorgehensweise für Ihre Android-Version finden Sie auf der offiziellen Dokumentationsseite [Konfigurieren von Entwickleroptionen auf dem Gerät](https://developer.android.com/studio/debug/dev-options).</span><span class="sxs-lookup"><span data-stu-id="fdb1f-163">See how to do this for your version of Android at the official documentation page [Configure on-device developer options](https://developer.android.com/studio/debug/dev-options)</span></span>
1. <span data-ttu-id="fdb1f-164">Verbinden Sie als Nächstes das Android-Gerät über ein USB-Kabel mit Ihrem Entwicklungscomputer oder Laptop.</span><span class="sxs-lookup"><span data-stu-id="fdb1f-164">Next, connect Android device to your development machine or laptop via USB cable</span></span>
1. <span data-ttu-id="fdb1f-165">Stellen Sie sicher, dass der Webserver auf dem Entwicklungscomputer ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="fdb1f-165">Ensure that the web server on the development machine is running.</span></span> <span data-ttu-id="fdb1f-166">Navigieren Sie beispielsweise zum Stammordner, der Ihre Webhostingseite (index.html) enthält, und führen Sie den folgenden Code aus (vorausgesetzt, Sie verwenden das npm-Paket „serve“):</span><span class="sxs-lookup"><span data-stu-id="fdb1f-166">For example, navigate to the root folder containing your web hosting page (index.html) and execute the following code (assuming you use serve npm package):</span></span>

    ```bash
    serve
    ```

1. <span data-ttu-id="fdb1f-167">Öffnen Sie Google Chrome auf Ihrem Entwicklungscomputer, und geben Sie den folgenden Text in die Adressleiste ein:</span><span class="sxs-lookup"><span data-stu-id="fdb1f-167">Open Google Chrome on your development machine and enter in the address bar the following text:</span></span>
    > <span data-ttu-id="fdb1f-168">chrome://inspect#devices ![Chrome-Fenster „USB-Debugging“](../images/chrome-usb-debug.png)</span><span class="sxs-lookup"><span data-stu-id="fdb1f-168">chrome://inspect#devices ![Chrome USB debugging window](../images/chrome-usb-debug.png)</span></span>
1. <span data-ttu-id="fdb1f-169">Stellen Sie sicher, dass das Kontrollkästchen *USB-Geräte ermitteln* aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="fdb1f-169">Ensure that the *Discover USB devices* checkbox is enabled</span></span>
1. <span data-ttu-id="fdb1f-170">Klicken Sie auf die Schaltfläche *Portweiterleitung,* und stellen Sie sicher, dass die *Portweiterleitung* aktiviert ist und den Eintrag *localhost:5000* enthält, wie unten dargestellt: ![Chrome-Fenster „Portweiterleitung“](../images/chrome-port-forwarding.png).</span><span class="sxs-lookup"><span data-stu-id="fdb1f-170">Click the button *Port forwarding* and ensure that *Port forwarding* is enabled and contains an entry *localhost:5000* as shown below:  ![Chrome Port Forwarding window](../images/chrome-port-forwarding.png)</span></span>
1. <span data-ttu-id="fdb1f-171">Öffnen Sie auf Ihrem verbundenen Android-Gerät ein Google Chrome-Fenster, und navigieren Sie zu *http://localhost:5000* , woraufhin Sie den Würfel sehen sollten.</span><span class="sxs-lookup"><span data-stu-id="fdb1f-171">In your connected Android device open a Google Chrome window and browse to *http://localhost:5000* and you should see the cube</span></span>
1. <span data-ttu-id="fdb1f-172">Auf Ihrem Entwicklungscomputer in Chrome werden Ihr Gerät und eine Liste der Webseiten angezeigt, die derzeit dort geöffnet sind: ![Chrome-Fenster „Untersuchen“](../images/chrome-inspect.png).</span><span class="sxs-lookup"><span data-stu-id="fdb1f-172">On your development machine, in Chrome, you will see your device and a list of web pages currently opened in there:  ![Chrome Inspect window](../images/chrome-inspect.png)</span></span>
1. <span data-ttu-id="fdb1f-173">Klicken Sie auf die Schaltfläche *Untersuchen* neben einem *http://localhost:5000* -Eintrag: ![ Fenster „Chrome DevTools Debug“](../images/chrome-debug.png).</span><span class="sxs-lookup"><span data-stu-id="fdb1f-173">Click the button *Inspect* next to an entry *http://localhost:5000*:  ![Chrome DevTools Debug window](../images/chrome-debug.png)</span></span>
1. <span data-ttu-id="fdb1f-174">Verwenden der [Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools) zum Debuggen der Seite</span><span class="sxs-lookup"><span data-stu-id="fdb1f-174">Use the [Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools) to debug the page</span></span>

## <a name="takeaways"></a><span data-ttu-id="fdb1f-175">Wesentliche Punkte</span><span class="sxs-lookup"><span data-stu-id="fdb1f-175">Takeaways</span></span>

<span data-ttu-id="fdb1f-176">Im Folgenden finden Sie die wichtigsten Erkenntnisse aus diesem Tutorial:</span><span class="sxs-lookup"><span data-stu-id="fdb1f-176">The following are the most important takeaways from this tutorial:</span></span>
* <span data-ttu-id="fdb1f-177">„Babylon.js“ erleichtert das Erstellen immersiver Erfahrungen mit JavaScript.</span><span class="sxs-lookup"><span data-stu-id="fdb1f-177">Babylon.js makes it easy to create immersive experiences using JavaScript</span></span>
* <span data-ttu-id="fdb1f-178">Um virtuelle Szenen zu erstellen, müssen Sie keinen Low-Level-Code schreiben oder eine neue Technologie erlernen.</span><span class="sxs-lookup"><span data-stu-id="fdb1f-178">To create virtual scenes you don't need to write low-level code or learn a new technology</span></span>
* <span data-ttu-id="fdb1f-179">Sie können Mixed Reality-Anwendungen mit einem von WebXR unterstützten Browser erstellen, ohne ein Headset kaufen zu müssen.</span><span class="sxs-lookup"><span data-stu-id="fdb1f-179">You can build Mixed Reality applications with WebXR-supported browser without need to buy a headset</span></span>

## <a name="next-steps"></a><span data-ttu-id="fdb1f-180">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="fdb1f-180">Next steps</span></span>

<span data-ttu-id="fdb1f-181">Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="fdb1f-181">Congratulations!</span></span> <span data-ttu-id="fdb1f-182">Sie haben unsere „babylon.js“-Tutorialreihe abgeschlossen und Folgendes gelernt:</span><span class="sxs-lookup"><span data-stu-id="fdb1f-182">You've completed our series of babylon.js tutorials and learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="fdb1f-183">Einrichten einer Entwicklungsumgebung</span><span class="sxs-lookup"><span data-stu-id="fdb1f-183">Set up a development environment</span></span>
> * <span data-ttu-id="fdb1f-184">Erstellen einer neuen Webseite zum Anzeigen von Ergebnissen</span><span class="sxs-lookup"><span data-stu-id="fdb1f-184">Create a new web page to display results</span></span>
> * <span data-ttu-id="fdb1f-185">Die „babylon.js“-API zum Erstellen und Interagieren mit einfachen 3D-Elementen</span><span class="sxs-lookup"><span data-stu-id="fdb1f-185">The babylon.js API to create and interact with basic 3D elements</span></span>
> * <span data-ttu-id="fdb1f-186">Ausführen und Testen der Anwendung in einem Windows Mixed Reality-Simulator</span><span class="sxs-lookup"><span data-stu-id="fdb1f-186">Run and test the application in a Windows Mixed Reality Simulator</span></span>

<span data-ttu-id="fdb1f-187">Weitere Informationen zur Mixed Reality-Entwicklung mit JavaScript finden Sie unter [Übersicht über die JavaScript-Entwicklung](/javascript-development-overview.md).</span><span class="sxs-lookup"><span data-stu-id="fdb1f-187">For more information on Mixed Reality JavaScript development see [JavaScript development overview](/javascript-development-overview.md).</span></span>
