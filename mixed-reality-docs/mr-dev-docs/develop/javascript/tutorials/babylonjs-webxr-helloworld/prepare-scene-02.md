---
title: „Babylon.js“-Tutorial zum Vorbereiten einer Szene mit einfachen 3D-Objekten
description: Erfahren Sie, wie Sie „babylon.js“ verwenden und einer Szene einfache 3D-Objekte hinzufügen.
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: Mixed Reality, JavaScript, Tutorial,BabylonJS, HoloLens, Mixed Reality, UWP, Windows 10, WebXR, immersives Web
ms.localizationpriority: high
ms.openlocfilehash: 9d74104924aa859f5ab18248a487a7e80392809adb09361e84c5ad386f1321c4
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212386"
---
# <a name="tutorial-prepare-a-scene"></a>Tutorial: Vorbereiten einer Szene

Erfahren Sie, wie Sie eine Szene vorbereiten und ihr einige einfache 3D-Elemente hinzufügen.

In diesem Tutorial lernen Sie Folgendes:

> [!div class="checklist"]
> * Erstellen einer Szene
> * Hinzufügen einer Kamera
> * Hinzufügen von Licht
> * Hinzufügen einfacher 3D-Elemente

## <a name="before-you-begin"></a>Vorbereitung

Im vorherigen Schritt des Tutorials wurde eine einfache Webseite erstellt. Lassen Sie die Webseite zur Bearbeitung geöffnet.

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

## <a name="create-a-scene"></a>Erstellen einer Szene

Eine Szene ist der Ort, an dem alle Inhalte angezeigt werden. Es kann mehrere Szenen geben, und es ist möglich, zwischen Szenen zu wechseln. Weitere Informationen zur [„babylon.js“-Szene](https://doc.babylonjs.com/divingDeeper/scene).

1. Fügen Sie das Skripttag hinter dem „canvas“-HTML-Element hinzu, und fügen Sie den folgenden Code hinzu, um eine mit schwarzer Farbe ausgefüllte Szene zu erstellen:

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

    Im obigen Code müssen wir eine Instanz der Webrendering-Engine von „babylon.js“ erstellen, die eine Szene rendert und Ereignisse im Zeichenbereich verankert. Weitere Informationen zu der Engine finden Sie auf der Dokumentationsseite [babylon.engine](https://doc.babylonjs.com/typedoc/classes/babylon.engine).

1. Die Szene wird nicht standardmäßig gerendert. Denken Sie daran, dass es möglicherweise mehrere Szenen gibt, und Sie steuern, welche Szene angezeigt wird. Um die Szene wiederholt in jedem Frame zu rendern, führen Sie den folgenden Code nach dem Aufrufen der *createScene*-Funktion aus:

    ```javascript
    engine.runRenderLoop(function () {
        sceneToRender.render();
    });
    ```

## <a name="add-basic-3d-element"></a>Hinzufügen einfacher 3D-Elemente

1. Fügen wir unsere erste 3D-Form hinzu. In der virtuellen 3D-Welt werden Formen aus *Gittermodellen* erstellt, wobei viele dreieckige Facets miteinander verknüpft werden und jedes Facet aus drei Scheitelpunkten (vertices) besteht. Sie können entweder ein vordefiniertes Gittermodell verwenden oder ein eigenes benutzerdefiniertes Gittermodell erstellen. Hier verwenden wir ein vordefiniertes Box-Gittermodell, d. h. einen Würfel (Cube). Verwenden Sie zum Erstellen der Box [BABYLON.MeshBuilder.CreateBox](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/box). Die Parameter sind „name“ und „options“ (die Optionen unterscheiden sich je nach Typ des Gittermodells). Fügen Sie den folgenden Code an die Funktion *createScene* an:

    ```javascript
    const box = BABYLON.MeshBuilder.CreateBox("box", {});
    box.position.x = 0.5;
    box.position.y = 1;
    ```

1. Öffnen Sie die Webseite im Microsoft Edge-Browser, und überprüfen Sie die Ausgabe. Im Browserfenster wird eine leere Seite angezeigt. Öffnen Sie DevTools über die Tastatur, und drücken Sie F12 oder STRG+UMSCHALT+I (Windows, Linux) oder BEFEHL+WAHL+I (macOS). Nachdem Sie die Registerkarte *Konsole* geöffnet haben, können Sie nach Fehlern suchen. Es wird ein Fehler angezeigt: „Uncaught Error: No camera defined.“ (Nicht abgefangener Fehler: Keine Kamera definiert.) Nun müssen wir der Szene eine Kamera hinzufügen.

## <a name="add-a-camera"></a>Hinzufügen einer Kamera

1. Um die virtuelle Welt sehen und damit interagieren zu können, muss dem Zeichenbereich eine Kamera angefügt werden. Fügen Sie die Kamera vom Typ [BABYLON.ArcRotateCamera](https://doc.babylonjs.com/divingDeeper/cameras/camera_introduction#arc-rotate-camera) hinzu, die um ein Ziel herum gedreht werden kann. Folgende Parameter sind erforderlich, um eine Instanz der Kamera zu erstellen:
    1. **name**: Name der Kamera.
    1. **alpha**: Winkelposition entlang der Längsachse (im Bogenmaß).
    1. **beta**: Winkelposition entlang der Querachse (im Bogenmaß).
    1. **radius**: Entfernung vom Ziel.
    1. **target**: Der Punkt, auf den die Kamera immer gerichtet ist (definiert durch x-y-z-Koordinaten).
    1. **scene**: Die Szene, in der sich die Kamera befindet.

    „alpha“, „beta“, „radius“ und „target“ zusammen definieren die Position der Kamera im Raum, wie im folgenden Diagramm dargestellt:

    ![Kamera alpha beta radius](../images/camera-alpha-beta-radius.jpg)

    Fügen Sie der Funktion *createScene* den folgenden Code an:

    ```javascript
    const alpha =  Math.PI/4;
    const beta = Math.PI/3;
    const radius = 8;
    const target = new BABYLON.Vector3(0, 0, 0);
    
    const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
    camera.attachControl(canvas, true);
    ```

1. Wenn Sie die Ausgabe im Browser überprüfen, wird ein schwarzer Zeichenbereich angezeigt. Uns fehlt das Licht.

## <a name="add-light"></a>Hinzufügen von Licht

1. Es gibt vier Arten von Lichtern, die mit einer Reihe von Beleuchtungseigenschaften verwendet werden können: Point (Punkt), Directional (gerichtet), Spot und Hemispheric (hemisphärisch/Halbkugel). Fügen Sie das Umgebungslicht vom Typ [HemisphericLight](https://doc.babylonjs.com/typedoc/classes/babylon.hemisphericlight) wie folgt hinzu:

    ```javascript
    const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(1, 1, 0));
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

1. Überprüfen Sie die Ausgabe im Browser. Der Würfel sollte zu sehen sein, und mit der Maus können Sie die Kamera um den Würfel herum drehen und so die verschiedenen Flächen des Würfels sehen:

![Einfache Szene mit Würfel (Cube)](../images/hello-world-basic-scene.png)

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Nächstes Tutorial: 3. Interagieren mit einem 3D-Objekt](interact-03.md)
