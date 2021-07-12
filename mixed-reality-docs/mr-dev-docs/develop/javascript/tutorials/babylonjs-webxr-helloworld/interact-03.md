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
# <a name="tutorial-interact-with-3d-object"></a>Tutorial: Interagieren mit einem 3D-Objekt

Erfahren Sie, wie Sie mithilfe von „babylon.js“ 3D-Objekte und Interaktionen für eine Mixed Reality-Erfahrung erstellen. In diesem Abschnitt beginnen Sie mit etwas Einfachem, z. B. dem Zeichnen der Flächen eines Würfels (cube), wenn Sie das Objekt auswählen.

Dieses Tutorial behandelt die folgenden Themen:

> [!div class="checklist"]
> * Hinzufügen von Interaktionen
> * Aktivieren des immersiven WebXR-Modus
> * Ausführen der App im Windows Mixed Reality-Simulator
> * Ausführen und Debuggen der App in Android Chrome

## <a name="before-you-begin"></a>Vorbereitung

Im vorherigen Schritt des Tutorials wurde eine einfache Webseite mit einer Szene erstellt. Lassen Sie die Hostingwebseite zur Bearbeitung geöffnet.

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

## <a name="add-interaction"></a>Hinzufügen einer Interaktion

1. Zunächst aktualisieren wir unseren Code, der den Würfel erstellt, sodass der Würfel mit einer zufälligen Farbe gezeichnet wird. Dazu fügen wir unserem Würfel [Material](https://doc.babylonjs.com/divingDeeper/materials/using/materials_introduction) hinzu. Material ermöglicht es uns, Farbe und Texturen anzugeben, und es kann verwendet werden, um andere Objekte zu bedecken. Wie ein Material angezeigt wird, hängt vom Licht oder den Beleuchtungen ab, die in der Szene verwendet werden, und davon, wie seine Reaktionen festgelegt sind. „diffuseColor“ verteilt beispielsweise die Farbe über das gesamte Gittermodell, an die sie angefügt ist. Fügen Sie den folgenden Code hinzu:

    ```javascript
    const boxMaterial = new BABYLON.StandardMaterial("material", scene);
    boxMaterial.diffuseColor = BABYLON.Color3.Random();
    box.material = boxMaterial;
    ```

1. Nachdem der Würfel nun mit einer zufälligen Farbe gezeichnet wurde, fügen wir eine Interaktion für Folgendes hinzu:

    * Ändern der Farbe beim Klicken auf den Würfel
    * Bewegen des Würfels nach dem Ändern der Farbe

    Zum Hinzufügen von Interaktionen sollten wir [Aktionen](https://doc.babylonjs.com/divingDeeper/events/actions) verwenden. Eine Aktion wird als Reaktion auf den Ereignistrigger gestartet. Beispielsweise, wenn der Benutzer auf den Würfel klickt. Alles, was wir tun müssen, ist „BABYLON.ActionManager“ zu instanziieren und eine Aktion für einen bestimmten Trigger zu registrieren. Die [BABYLON.ExecuteCodeAction](https://doc.babylonjs.com/typedoc/classes/babylon.executecodeaction) führt unsere JavaScript-Funktion aus, wenn jemand auf den Würfel klickt:

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

1. Der endgültige Code der Webseite sieht wie folgt aus:

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

## <a name="enable-webxr-immersive-experience"></a>Aktivieren der immersiven WebXR-Benutzeroberfläche

Nachdem sich die Farbe des Würfels nun ändert, können wir die immersive Erfahrung ausprobieren.

1. In diesem Schritt führen wir einen [Boden](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/ground) ein. Der Würfel hängt in der Luft, und unten sehen wir einen Boden. Fügen Sie den Boden wie folgt hinzu:

    ```javascript
    const ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 4, height: 4});
    ```

    Hierdurch wird ein einfacher 4x4-Meter-Boden erstellt.

1. Um WebXR-Unterstützung hinzuzufügen, müssen wir *createDefaultXRExperienceAsync* aufrufen, das ein *Zusage*-Ergebnis (promise) aufweist. Fügen Sie diesen Code am Ende der *createScene*-Funktion anstelle von *return scene* (Szene zurückgeben) hinzu:

    ```javascript
    const xrPromise = scene.createDefaultXRExperienceAsync({
        floorMeshes: [ground]
    });
    return xrPromise.then((xrExperience) => {
        console.log("Done, WebXR is enabled.");
        return scene;
    });
    ```

1. Da die *createScene*-Funktion jetzt eine Zusage anstelle einer Szene zurückgibt, müssen wir ändern, wie *createScene* und *engine.runRenderLoop* aufgerufen werden. Ersetzen Sie die aktuellen Aufrufe dieser Funktionen, die sich direkt vor dem *\</script>* -Tag befinden, durch den folgenden Code:

    ```javascript
    createScene().then(sceneToRender => {
        engine.runRenderLoop(() => sceneToRender.render());
    });
    ```

1. Der endgültige Code der Webseite sieht wie folgt aus:

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

1. Der obige Code generiert die folgende Ausgabe im Browserfenster: ![WebXR-Szene](../images/hello-world-webxr-scene.png)

## <a name="run-on-a-windows-mixed-reality-simulator"></a>Ausführen in einem Windows Mixed Reality-Simulator

1. [Aktivieren Sie den Windows Mixed Reality-Simulator](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md), wenn Sie dies in der Vergangenheit noch nicht getan haben.

1. Wählen Sie die Schaltfläche „Immersive VR“ in der unteren rechten Ecke aus: ![Schaltfläche „Immersive VR“](../images/immersive-vr-button.png)

1. Mit dieser Aktion wird das Fenster „Windows Mixed Reality-Simulator“ wie unten dargestellt gestartet: ![ Mixed Reality-Portal](../images/mixed-reality-portal.png)

1. Verwenden Sie die Tasten W, A, S und D auf ihrer Tastatur, um entsprechend vorwärts, zurück, links und rechts zu gehen. Verwenden Sie die simulierte Hand, um den Würfel anzuvisieren, und drücken Sie die EINGABETASTE auf der Tastatur, um die Klickaktion auszuführen. Der Würfel ändert seine Farbe und bewegt sich an eine neue Position.

> [!NOTE]
> Stellen Sie beim Anvisieren des Würfels sicher, dass sich das Ende des Handstrahls (weißer Kreis) wie in der Abbildung oben gezeigt mit dem Würfel überschneidet. Erfahren Sie mehr über [Zeigen und Ausführen mit den Händen](../../../../design/point-and-commit.md).

## <a name="run-and-debug-on-android-device"></a>Ausführen und Debuggen auf einem Android-Gerät

Führen Sie die folgenden Schritte aus, um das Debuggen auf Ihrem Android-Gerät zu aktivieren:

### <a name="prerequisites"></a>Voraussetzungen

* Ein Webserver, der statische HTML-Seiten im sicheren Kontext („https://“ oder über Portweiterleitung auf dem „localhost“) auf dem Entwicklungscomputer bereitstellt. Nutzen Sie beispielsweise das npm-Paket *serve* als einfachen, schlanken Webserver, der statische HTML-Dateien bereitstellt. Weitere Informationen finden Sie unter [npm serve](https://github.com/vercel/serve#readme).
* Das Gerät wurde ursprünglich über den Google Play Store ausgeliefert und muss Android 7.0 oder höher ausführen.
* Die neueste Version von [Google Chrome](https://support.google.com/chrome/answer/95346) sowohl auf der Entwicklungsarbeitsstation als auch auf dem Gerät
* Um zu überprüfen, ob das Gerät ordnungsgemäß für die Ausführung von WebXR konfiguriert ist, wechseln Sie zu einer [WebXR-Beispielseite](https://immersive-web.github.io/webxr-samples/) auf dem Gerät. Ungefähr die folgende Meldung sollte angezeigt werden:

    > Ihr Browser unterstützt WebXR und kann Virtual Reality- und Augmented Reality-Erfahrungen ausführen, wenn Sie über die entsprechende Hardware verfügen.

1. Aktivieren sie den Entwicklermodus und USB-Debugging auf einem Android-Gerät. Informationen zur Vorgehensweise für Ihre Android-Version finden Sie auf der offiziellen Dokumentationsseite [Konfigurieren von Entwickleroptionen auf dem Gerät](https://developer.android.com/studio/debug/dev-options).
1. Verbinden Sie als Nächstes das Android-Gerät über ein USB-Kabel mit Ihrem Entwicklungscomputer oder Laptop.
1. Stellen Sie sicher, dass der Webserver auf dem Entwicklungscomputer ausgeführt wird. Navigieren Sie beispielsweise zum Stammordner, der Ihre Webhostingseite (index.html) enthält, und führen Sie den folgenden Code aus (vorausgesetzt, Sie verwenden das npm-Paket „serve“):

    ```bash
    serve
    ```

1. Öffnen Sie Google Chrome auf Ihrem Entwicklungscomputer, und geben Sie den folgenden Text in die Adressleiste ein:
    > chrome://inspect#devices ![Chrome-Fenster „USB-Debugging“](../images/chrome-usb-debug.png)
1. Stellen Sie sicher, dass das Kontrollkästchen *USB-Geräte ermitteln* aktiviert ist.
1. Klicken Sie auf die Schaltfläche *Portweiterleitung,* und stellen Sie sicher, dass die *Portweiterleitung* aktiviert ist und den Eintrag *localhost:5000* enthält, wie unten dargestellt: ![Chrome-Fenster „Portweiterleitung“](../images/chrome-port-forwarding.png).
1. Öffnen Sie auf Ihrem verbundenen Android-Gerät ein Google Chrome-Fenster, und navigieren Sie zu *http://localhost:5000* , woraufhin Sie den Würfel sehen sollten.
1. Auf Ihrem Entwicklungscomputer in Chrome werden Ihr Gerät und eine Liste der Webseiten angezeigt, die derzeit dort geöffnet sind: ![Chrome-Fenster „Untersuchen“](../images/chrome-inspect.png).
1. Klicken Sie auf die Schaltfläche *Untersuchen* neben einem *http://localhost:5000* -Eintrag: ![ Fenster „Chrome DevTools Debug“](../images/chrome-debug.png).
1. Verwenden der [Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools) zum Debuggen der Seite

## <a name="takeaways"></a>Wesentliche Punkte

Im Folgenden finden Sie die wichtigsten Erkenntnisse aus diesem Tutorial:
* „Babylon.js“ erleichtert das Erstellen immersiver Erfahrungen mit JavaScript.
* Um virtuelle Szenen zu erstellen, müssen Sie keinen Low-Level-Code schreiben oder eine neue Technologie erlernen.
* Sie können Mixed Reality-Anwendungen mit einem von WebXR unterstützten Browser erstellen, ohne ein Headset kaufen zu müssen.

## <a name="next-steps"></a>Nächste Schritte

Glückwunsch! Sie haben unsere „babylon.js“-Tutorialreihe abgeschlossen und Folgendes gelernt:
> [!div class="checklist"]
> * Einrichten einer Entwicklungsumgebung
> * Erstellen einer neuen Webseite zum Anzeigen von Ergebnissen
> * Die „babylon.js“-API zum Erstellen und Interagieren mit einfachen 3D-Elementen
> * Ausführen und Testen der Anwendung in einem Windows Mixed Reality-Simulator

Weitere Informationen zur Mixed Reality-Entwicklung mit JavaScript finden Sie unter [Übersicht über die JavaScript-Entwicklung](/javascript-development-overview.md).
