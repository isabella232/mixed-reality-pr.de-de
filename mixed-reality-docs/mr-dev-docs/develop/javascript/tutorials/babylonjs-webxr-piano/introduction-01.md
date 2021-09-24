---
title: Erstellen eines Klaviers in WebXR mithilfe von BabylonJS
description: Absolvieren Sie diese Tutorialreihe, um zu erfahren, wie Sie mithilfe von BabylonJS eine funktionsfähige Klaviatur mit 88 Tasten in WebXR erstellen.
author: JING1201
ms.author: v-vtieto
ms.prod: mixed-reality
ms.topic: tutorial
ms.date: 09/10/2021
keywords: Mixed Reality, JavaScript, Tutorial,BabylonJS, HoloLens, Mixed Reality, UWP, Windows 10, WebXR, immersives Web
ms.localizationpriority: high
ms.openlocfilehash: 93a3896b081e736bb62bceb6c8ae609685d7c5b5
ms.sourcegitcommit: 645608f33d2d02625484c29586f42d21c442aaa9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/18/2021
ms.locfileid: "127932491"
---
# <a name="tutorial-build-a-piano-in-webxr-using-babylonjs"></a>Tutorial: Erstellen eines Klaviers in WebXR mithilfe von Babylon.js

Das Bauen eines echten Klaviers erfordert in der Realität viel Zeit, Fertigkeiten und Materialien. Wie sieht es mit dem Erstellen eines Klaviers für die VR/AR-Welt aus?

In dieser Tutorialreihe erfahren Sie, wie Sie Babylon.js verwenden, um eine Mixed Reality Web-App zu erstellen, die ein funktionierendes Klavier mit 88-Tasten in der virtuellen Welt enthält. In der fertigen App können Sie sich zum Klavier teleportieren und die Tasten mit Ihren Mixed Reality-Controllern spielen.

In dieser Tutorialreihe lernen Sie Folgendes:

> [!div class="checklist"]
> * Erstellen, Positionieren und Zusammenführen von Gittermodellen zum Erstellen einer Klaviatur
> * Importieren eines Babylon.js-Modells eines Klavierrahmens
> * Hinzufügen von Zeigerinteraktionen zu jeder Klaviertaste
> * Aktivieren von Teleportierungs- und Multizeigerunterstützung in WebXR

## <a name="prerequisites"></a>Voraussetzungen

* Ein mit dem Internet verbundener Computer
* JavaScript-Grundkenntnisse
* [WebXR Javascript Hallo Welt-Tutorial](../babylonjs-webxr-helloworld/introduction-01.md)
* Von WebXR unterstützter Browser, z. B. [Microsoft Edge](../../../../whats-new/new-microsoft-edge.md)
* [Babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 4.2 oder höher
* Beliebiges [VR-Headset](../../../../discover/immersive-headset-hardware-details.md) oder [Windows Mixed Reality-Simulator](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)
* Optional: [Windows 10 Creator Update](https://www.microsoft.com/software-download/windows10), wenn Sie einen Windows Mixed Reality-Simulator verwenden möchten

## <a name="getting-started"></a>Erste Schritte

Beginnen wir damit, die HTML-Webseite einzurichten, die die Babylon.js-Szene enthalten soll.

1. Erstellen Sie einen Ordner mit dem Namen *babylonjs-piano-tutorial*, und öffnen Sie den Ordner in Visual Studio Code.

    > [!NOTE]
    > Zwar können Sie das Tutorial in einem beliebigen Code-Editor nachvollziehen, wir verwenden aber aus Gründen der Bequemlichkeit durchgängig Visual Studio Code.

1. Erstellen Sie im Ordner eine Datei mit dem Namen *index.html*, und fügen Sie die Vorlage unten in die Datei ein:

    ```html
    <html>
        <head>
            <title>Piano in BabylonJS</title>
            <script src="https://cdn.babylonjs.com/babylon.js"></script>
            <style>
                body,#renderCanvas { width: 100%; height: 100%;}
            </style>
        </head>
        <body>
            <canvas id="renderCanvas"></canvas>
            <script type="text/javascript">
                const canvas = document.getElementById("renderCanvas"); 
                const engine = new BABYLON.Engine(canvas, true); 

                createScene(engine).then(sceneToRender => {
                    engine.runRenderLoop(() => sceneToRender.render());
                });
        
                // Watch for browser/canvas resize events
                window.addEventListener("resize", function () {
                    engine.resize();
                });
            </script>
        </body>
    </html>
    ```

    Weitere Informationen zum Inhalt dieser Vorlage finden Sie im [Hallo Welt-Tutorial](../babylonjs-webxr-helloworld/introduction-01.md), das eine Voraussetzung für dieses Tutorial ist.

1. Wenn Sie versuchen, diese Datei in einem Browser zu öffnen, zeigt die Konsole einen Fehler an, der angibt, dass die Funktion `createScene()` nicht gefunden wurde. Lassen Sie uns diesen Fehler beheben, indem wir die Funktion `createScene()` im nächsten Abschnitt implementieren.

## <a name="setup-the-scene"></a>Einrichten der Szene

1. Erstellen Sie im gleichen Ordner wie *index.html* eine weitere Datei mit dem Namen *scene.js*. Wir speichern den gesamten JavaScript-Code, der sich auf das Einrichten der Szene und das Erstellen des Klaviers bezieht, in dieser Datei.

1. Fügen Sie die Funktion `createScene()` zu *scene.js* hinzu:

    ```javascript
    const createScene = async function(engine) {
        const scene = new BABYLON.Scene(engine);
        return scene;
    }
    ```

    Beachten Sie, dass wir aus `createScene()` eine asynchrone Funktion machen. Lesen Sie weiter, um herauszufinden, warum.

1. Als Nächstes benötigen wir eine Lichtquelle und eine Kamera, um die Szene für uns sichtbar zu machen. Aktualisieren der Funktion `createScene()`:

    ```javascript
    const createScene = async function(engine) {
        const scene = new BABYLON.Scene(engine);

        const alpha =  3*Math.PI/2;
        const beta = Math.PI/50;
        const radius = 220;
        const target = new BABYLON.Vector3(0, 0, 0);
        
        const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
        camera.attachControl(canvas, true);
        
        const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(0, 1, 0), scene);
        light.intensity = 0.6;

        return scene;
    }
    ```

    Hier haben wir eine [ArcRotateCamera](https://doc.babylonjs.com/divingDeeper/cameras/camera_introduction#arc-rotate-camera) erstellt, die fast direkt nach unten zeigt und den Ursprungspunkt des Raums anzielt. Die Lichtquelle, die wir erstellt haben, ist ein [HemisphericLight](https://doc.babylonjs.com/divingDeeper/lights/lights_introduction#the-hemispheric-light), das auf den Himmel zeigt und zum Simulieren eines Umgebungsbereichs nützlich ist. Außerdem haben wir das Licht ein bisschen abgeblendet, indem wir seine Intensität verringert haben.

    Wenn Sie eine Auffrischung zum Erstellen einer Kamera und einer Lichtquelle benötigen, sehen Sie sich noch einmal den [Abschnitt „Vorbereiten der Szene“ in der Hallo Welt-Tutorialreihe](../babylonjs-webxr-helloworld/prepare-scene-02.md#add-a-camera) an, bevor Sie mit dem nächsten Schritt fortfahren.

1. Da wir für eine WebXR-Plattform entwickeln, müssen wir schließlich in der Szene [die XR-Benutzerumgebung aktivieren](https://doc.babylonjs.com/divingDeeper/webXR/introToWebXR), indem wir vor `return scene;` die folgende Zeile einfügen:

    ```javascript
    const xrHelper = await scene.createDefaultXRExperienceAsync();
    ```

    Damit wir in Javascript die `await`Tastatur für eine `async`-Funktion innerhalb einer Funktion verwenden können, muss auch die übergeordnete Funktion `async` sein, was der Grund ist, warum wir die Funktion `createScene` zuvor als asynchron definiert haben. Später in dieser Tutorialreihe verwenden wir diesen `xrHelper`, um verschiedene von Babylon.js unterstützte WebXR-Features zu aktivieren und zu konfigurieren.

1. Die vollständige *scene.js* sollte folgendermaßen aussehen:

    ```javascript
    const createScene = async function(engine) {
        const scene = new BABYLON.Scene(engine);
        
        const alpha =  3*Math.PI/2;
        const beta = Math.PI/50;
        const radius = 220;
        const target = new BABYLON.Vector3(0, 0, 0);
        
        const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
        camera.attachControl(canvas, true);
        
        const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(0, 1, 0), scene);
        light.intensity = 0.6;
    
        const xrHelper = await scene.createDefaultXRExperienceAsync();
    
        return scene;
    }
    ```

1. Nachdem wir nun über eine funktionierende `createScene()`-Funktion verfügen, lassen wir die *scene.js*-Datei von *index.html* als Skript laden, sodass die Funktion `createScene()` in *index.html* erkannt wird. Fügen Sie diese Codezeile innerhalb des `<header>`-Abschnitts der HTML-Datei hinzu:

    ```html
    <html>
        <head>
            <title>Piano in BabylonJS</title>
            <script src="https://cdn.babylonjs.com/babylon.js"></script>
            <script src="scene.js"></script>
            <style>
                body,#renderCanvas { width: 100%; height: 100%;}
            </style>
        </head>
        <body>
            <canvas id="renderCanvas"></canvas>
            <script type="text/javascript">
                const canvas = document.getElementById("renderCanvas");
                const engine = new BABYLON.Engine(canvas, true); 

                createScene(engine).then(sceneToRender => {
                    engine.runRenderLoop(() => sceneToRender.render());
                });
                
                // Watch for browser/canvas resize events
                window.addEventListener("resize", function () {
                    engine.resize();
                });
            </script>
        </body>
    </html>
    ```

1. Öffnen Sie *index.html* in Ihrem Browser – Sie werden feststellen, dass die zuvor angezeigte Fehlermeldung nicht mehr vorhanden ist und wir eine leere Babylon.js-Szene auf der Seite sehen.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Nächstes Tutorial: Erstellen eines 3D-Klaviermodells](keyboard-model-02.md)
