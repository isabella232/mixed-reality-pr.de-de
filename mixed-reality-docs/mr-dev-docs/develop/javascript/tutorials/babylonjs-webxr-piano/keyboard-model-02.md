---
title: Erstellen eines 3D-Klaviermodells
description: Erfahren Sie, wie Sie ein 3D-Modell eines Klaviers erstellen, indem Sie in Babylon.js programmieren
author: JING1201
ms.author: v-vtieto
ms.prod: mixed-reality
ms.topic: tutorial
ms.date: 09/10/2021
keywords: Mixed Reality, JavaScript, Tutorial,BabylonJS, HoloLens, Mixed Reality, UWP, Windows 10, WebXR, immersives Web
ms.localizationpriority: high
ms.openlocfilehash: e5c3dd6206566f781ceb52e5d13a49a0c9ab1018
ms.sourcegitcommit: 645608f33d2d02625484c29586f42d21c442aaa9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/18/2021
ms.locfileid: "127932508"
---
# <a name="tutorial-build-a-3d-piano-model"></a>Tutorial: Erstellen eines 3D-Klaviermodells

Im vorhergehenden Tutorial der Reihe haben wir eine Webseite eingerichtet, die eine Babylon.js-Szene mit einer Kamera und einer Lichtquelle enthält. In diesem Tutorial erstellen wir ein Klaviermodell und fügen es der Szene hinzu.

![Gittermodell eines aufrecht stehenden Klaviers](./images/standup-piano-mesh.png)

In diesem Tutorial lernen Sie Folgendes:

> [!div class="checklist"]
> * Erstellen, Positionieren und Zusammenführen von Gitternetzen
> * Erstellen einer Klaviatur aus Box-Gittermodellen
> * Importieren eines 3D-Modells eines Klavierrahmens

## <a name="before-you-begin"></a>Vorbereitung

Vergewissern Sie sich, dass Sie das [vorhergehende Tutorial in der Reihe](introduction-01.md) durchgegangen und bereit sind, mit dem Hinzufügen von Code fortzufahren.

*index.html*

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

*scene.js*

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

## <a name="getting-started"></a>Erste Schritte

Lassen Sie uns zunächst eine einfache Klaviatur erstellen, die die folgende Struktur besitzt:

![Beschreibung eines Klavierregisters](./images/piano-register.jpg)

In dieser Abbildung sind 7 weiße Tasten und 5 schwarze Tasten zu sehen, von denen jede mit der Bezeichnung der Note beschriftet ist. Eine vollständige Klaviatur mit 88 Tasten enthält 7 vollständige Wiederholungen dieser Tastenauswahl (auch als Register bezeichnet) und 4 zusätzliche Tasten. Jedes Register weist die doppelte Frequenz des vorherigen Registers auf. Zum Beispiel ist die Tonfrequenz von C5 (also der Note „C“ im fünften Register) doppelt so hoch wie die von C4, die Tonfrequenz von D5 ist die doppelte von D4 usw.

Visuell entspricht jedes Register genau jedem anderen, sodass wir mit der Untersuchung beginnen können, wie wir eine einfache Klaviatur mit dieser Tastenauswahl erstellen können. Später können wir eine Möglichkeit suchen, den Umfang auf eine vollständige 88-Tasten-Klaviatur zu erweitern.

## <a name="build-a-simple-piano-keyboard"></a>Erstellen einer einfachen Klaviatur

> [!NOTE]
> Es ist zwar möglich, vorgefertigte 3D-Modelle von Klaviaturen in Onlinequellen zu finden und sie in unsere Website zu importieren, wir erstellen in diesem Tutorial die Klaviatur aber von Grund auf, um maximale Anpassungsmöglichkeiten zu bieten und zu zeigen, wie 3D-Modelle mithilfe von Babylon.js erstellt werden können.

1. Bevor wir damit beginnen, Gitternetze zum Bauen der Klaviatur zu erstellen, beachten Sie, dass nicht jede schwarze Taste perfekt an der Mitte der beiden sie umgebenden weißen Tasten ausgerichtet ist und nicht jede Taste die gleiche Breite hat. Dies bedeutet, dass wir das Gitternetz für jede Taste einzeln erstellen und positionieren müssen.

    ![Ausrichtung der schwarzen Tasten](./images/black-key-position.png)

1. Bei den weißen Tasten können wir die Beobachtung machen, dass sich jede weiße Taste aus zwei Teilen zusammensetzt: (1) dem unteren Teil unter den schwarzen Tasten und (2) dem oberen Teil neben den schwarzen Tasten. Die beiden Teile haben unterschiedliche Abmessungen, bilden jedoch erst zusammen eine vollständige weiße Taste.

    ![Form der weißen Tasten](./images/white-key-shape-label.png)

1. Hier ist der Code zum Erstellen einer einzelnen weißen Taste für die Note C (Sie brauchen sich noch keine Gedanken darüber zu machen, wie Sie das zu *scene.js* hinzufügen):

    ```javascript
    const whiteKeyBottom = BABYLON.MeshBuilder.CreateBox("whiteKeyBottom", {width: 2.3, height: 1.5, depth: 4.5}, scene);
    const whiteKeyTop = BABYLON.MeshBuilder.CreateBox("whiteKeyTop", {width: 1.4, height: 1.5, depth: 5}, scene);
    whiteKeyTop.position.z += 4.75;
    whiteKeyTop.position.x -= 0.45;

    // Parameters of BABYLON.Mesh.MergeMeshes:
    // (arrayOfMeshes, disposeSource, allow32BitsIndices, meshSubclass, subdivideWithSubMeshes, multiMultiMaterials)
    const whiteKeyV1 = BABYLON.Mesh.MergeMeshes([whiteKeyBottom, whiteKeyTop], true, false, null, false, false);
    whiteKeyV1.material = whiteMat;
    whiteKeyV1.name = "C4";
    ```

    Hier haben wir zwei [Box](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/box#box-mesh)-Gitternetze erstellt, eins für den unteren Teil und eins für den oberen Teil der weißen Taste. Anschließend ändern wir die Position des oberen Teils, um ihn auf den unteren Teil zu stecken und ihn nach links zu verschieben, um Platz für die benachbarte schwarze Taste (Cis) zu lassen.

    Schließlich wurden diese beiden Teile mithilfe der [MergeMeshes](https://doc.babylonjs.com/divingDeeper/mesh/mergeMeshes)-Funktion zusammengeführt, um zu einer vollständigen weißen Taste zu werden. Dies ist das resultierende Gittermodell, das dieser Code erzeugen würde:

    ![Weiße Taste „C“](./images/white-key-c.png)

1. Das Erstellen einer schwarzen Taste ist einfacher. Da alle schwarzen Tasten die Form eines Kastens haben, können wir eine schwarze Taste erstellen, indem wir einfach ein Gitternetz mit einem schwarzfarbigen [Standardmaterial](https://doc.babylonjs.com/divingDeeper/materials/using/materials_introduction#color) erstellen.

    > [!NOTE]
    > Da die Standardgitternetzfarbe hellgrau ist und weiß ähnelt, enthält dieses Tutorial keine Schritte zum Hinzufügen eines weißen Farbmaterials zu den weißen Tasten. Sie können das Material jedoch selbst hinzufügen, wenn Sie eine realistische helle weiße Farbe auf den weißen Tasten wünschen.

    Hier ist der Code zum Erstellen der schwarzen Taste Cis (Sie brauchen sich auch hier keine Gedanken zu machen, wie Sie dies zu *scene.js* hinzufügen):

    ```javascript
    const blackMat = new BABYLON.StandardMaterial("black");
    blackMat.diffuseColor = new BABYLON.Color3(0, 0, 0);

    const blackKey = BABYLON.MeshBuilder.CreateBox("C#4", {width: 1.4, height: 2, depth: 5}, scene);
    blackKey.position.z += 4.75;
    blackKey.position.y += 0.25;
    blackKey.position.x += 0.95;
    blackKey.material = blackMat;
    ```

    Die von diesem Code erzeugte schwarze Taste (zusammen mit der vorherigen weißen Taste) würde wie folgt aussehen:

    ![Schwarze Taste „Cis“](./images/black-key-csharp.png)

1. Wie Sie sehen, kann das Erstellen jeder Taste zu viel ähnlichem Code führen, da wir jede ihrer Abmessungen und Positionen angeben müssen. Versuchen wir im nächsten Abschnitt, den Erstellungsprozess effizienter zu gestalten.

## <a name="build-a-simple-piano-keyboard-efficiently"></a>Effizientes Erstellen einer einfachen Klaviatur

1. Jede weiße Taste hat zwar eine etwas andere Form als jede andere, aber alle können durch Kombinieren eines oberen und eines unteren Teils erstellt werden. Implementieren wir eine allgemeine Funktion zum Erstellen und Positionieren beliebiger weißer Tasten.

    Fügen Sie die Funktion unten zu *scene.js* hinzu, außerhalb der Funktion `createScene()`:

    ```javascript
    const buildKey = function (scene, parent, props) {
        if (props.type === "white") {
            /*
            Props for building a white key should contain: 
            note, topWidth, bottomWidth, topPositionX, wholePositionX, register, referencePositionX
    
            As an example, the props for building the middle C white key would be
            {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4, register: 4, referencePositionX: 0}
            */
    
            // Create bottom part
            const bottom = BABYLON.MeshBuilder.CreateBox("whiteKeyBottom", {width: props.bottomWidth, height: 1.5, depth: 4.5}, scene);
    
            // Create top part
            const top = BABYLON.MeshBuilder.CreateBox("whiteKeyTop", {width: props.topWidth, height: 1.5, depth: 5}, scene);
            top.position.z =  4.75;
            top.position.x += props.topPositionX;
    
            // Merge bottom and top parts
            // Parameters of BABYLON.Mesh.MergeMeshes: (arrayOfMeshes, disposeSource, allow32BitsIndices, meshSubclass, subdivideWithSubMeshes, multiMultiMaterials)
            const key = BABYLON.Mesh.MergeMeshes([bottom, top], true, false, null, false, false);
            key.position.x = props.referencePositionX + props.wholePositionX;
            key.name = props.note + props.register;
            key.parent = parent;
    
            return key;
        }
    }
    ```

    In diesem Codeblock haben wir eine Funktion namens `buildKey()` erstellt, die eine weiße Taste erstellt und zurückgibt, wenn `props.type` gleich `"white"` ist. Indem wir den Typ der Taste im Parameter `props` identifizieren, können wir in derselben Funktion sowohl schwarze als auch weiße Tasten erzeugen, indem mithilfe einer if-Anweisung eine Verzweigung erstellen.

    Die Parameter von `buildKey()` sind:
    * **scene**: Szene, in der sich die Taste befindet
    * **parent**: übergeordnetes Element des Gitternetzes (dadurch können wir alle Tasten zu einem einzigen übergeordneten Element gruppieren)
    * **props**: Eigenschaften der zu erstellenden Taste

    Die `props` für eine weiße Taste enthält die folgenden Elemente:
    * **type**: „weiß“
    * **name**: Der Name der Note, die die Taste darstellt
    * **topWidth**: Breite des oberen Teils
    * **bottomWidth**: Breite des unteren Teils
    * **topPositionX**: x-Position des oberen Teils relativ zum unteren Teil
    * **wholePositionX**: x-Position der ganzen Taste relativ zum Endpunkt des Registers (dem rechten Rand von Taste „H“).
    * **register**: Register, zu dem die Taste gehört (eine Zahl zwischen 0 und 8)
    * **referencePositionX**: x-Koordinate des Endpunkts des Registers (wird als Referenzpunkt verwendet).

    Durch die Trennung von `wholePositionX` und `referencePositionX` können wir die `props`-Parameter initialisieren, die zum Erstellen eines bestimmten Tastentyps (z. B. „C“) innerhalb eines beliebigen Registers erforderlich sind, und dann damit fortfahren, den `props` `register` und `referencePositionX` hinzuzufügen, wenn wir diese Taste in einem bestimmten Register (z. B. C4, C5) erstellen.

1. Analog dazu können wir auch eine allgemeine Funktion zum Erzeugen einer schwarzen Taste schreiben. Erweitern wir die Funktion `buildKey()` um die betreffende Logik:

    ```javascript
    const buildKey = function (scene, parent, props) {
        if (props.type === "white") {
            /*
            Props for building a white key should contain: 
            note, topWidth, bottomWidth, topPositionX, wholePositionX, register, referencePositionX
    
            As an example, the props for building the middle C white key would be
            {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4, register: 4, referencePositionX: 0}
            */
    
            // Create bottom part
            const bottom = BABYLON.MeshBuilder.CreateBox("whiteKeyBottom", {width: props.bottomWidth, height: 1.5, depth: 4.5}, scene);
    
            // Create top part
            const top = BABYLON.MeshBuilder.CreateBox("whiteKeyTop", {width: props.topWidth, height: 1.5, depth: 5}, scene);
            top.position.z =  4.75;
            top.position.x += props.topPositionX;
    
            // Merge bottom and top parts
            // Parameters of BABYLON.Mesh.MergeMeshes: (arrayOfMeshes, disposeSource, allow32BitsIndices, meshSubclass, subdivideWithSubMeshes, multiMultiMaterials)
            const key = BABYLON.Mesh.MergeMeshes([bottom, top], true, false, null, false, false);
            key.position.x = props.referencePositionX + props.wholePositionX;
            key.name = props.note + props.register;
            key.parent = parent;
    
            return key;
        }
        else if (props.type === "black") {
            /*
            Props for building a black key should contain: 
            note, wholePositionX, register, referencePositionX
    
            As an example, the props for building the C#4 black key would be
            {type: "black", note: "C#", wholePositionX: -13.45, register: 4, referencePositionX: 0}
            */
    
            // Create black color material
            const blackMat = new BABYLON.StandardMaterial("black");
            blackMat.diffuseColor = new BABYLON.Color3(0, 0, 0);
    
            // Create black key
            const key = BABYLON.MeshBuilder.CreateBox(props.note + props.register, {width: 1.4, height: 2, depth: 5}, scene);
            key.position.z += 4.75;
            key.position.y += 0.25;
            key.position.x = props.referencePositionX + props.wholePositionX;
            key.material = blackMat;
            key.parent = parent;
    
            return key;
        }
    }
    ```

    Die `props` für eine schwarze Taste enthält die folgenden Elemente:

    * **type**: „schwarz“
    * **name**: Der Name der Note, die die Taste darstellt
    * **wholePositionX**: x-Position der ganzen Taste relativ zum Endpunkt des Registers (dem rechten Rand von Taste „H“)
    * **register**: Register, zu dem die Taste gehört (eine Zahl zwischen 0 und 8)
    * **referencePositionX**: x-Koordinate des Endpunkts des Registers (wird als Referenzpunkt verwendet).

    Die `props` zum Erstellen einer schwarzen Taste ist viel einfacher, da das Erstellen einer schwarzen Taste nur das Erstellen eines Kastens umfasst und die Breite und Z-Position jeder schwarzen Taste identisch sind.

1. Nachdem wir nun eine effizientere Möglichkeit zum Erstellen der Tasten haben, initialisieren wir ein Array, das die `props` für jede Taste speichert, die einer Note in einem Register entspricht, und rufen dann die `buildKey()`-Funktion für jede von ihnen auf, um eine einfache Klaviatur im 4. Register zu erstellen.

    Außerdem erstellen wir einen [TransformNode](https://doc.babylonjs.com/divingDeeper/mesh/transforms/parent_pivot/transform_node#a-transformnode) mit dem Namen `keyboard`, der als [übergeordnetes Element](https://doc.babylonjs.com/divingDeeper/mesh/transforms/parent_pivot/parent#overview-of-a-parent) aller Klaviertasten fungiert. Da jede Änderung der Position oder Skalierung, die auf das übergeordnete Element angewendet wird, auch auf die untergeordneten Elemente angewendet wird, können die Tasten durch Gruppierung in dieser Weise als Ganzes skaliert oder verschoben werden.

    Fügen Sie der `createScene()`-Funktion die folgenden Codezeilen an:

    ```javascript
    const keyParams = [
        {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4},
        {type: "black", note: "C#", wholePositionX: -13.45},
        {type: "white", note: "D", topWidth: 1.4, bottomWidth: 2.4, topPositionX: 0, wholePositionX: -12},
        {type: "black", note: "D#", wholePositionX: -10.6},
        {type: "white", note: "E", topWidth: 1.4, bottomWidth: 2.3, topPositionX: 0.45, wholePositionX: -9.6},
        {type: "white", note: "F", topWidth: 1.3, bottomWidth: 2.4, topPositionX: -0.55, wholePositionX: -7.2},
        {type: "black", note: "F#", wholePositionX: -6.35},
        {type: "white", note: "G", topWidth: 1.3, bottomWidth: 2.3, topPositionX: -0.2, wholePositionX: -4.8},
        {type: "black", note: "G#", wholePositionX: -3.6},
        {type: "white", note: "A", topWidth: 1.3, bottomWidth: 2.3, topPositionX: 0.2, wholePositionX: -2.4},
        {type: "black", note: "A#", wholePositionX: -0.85},
        {type: "white", note: "B", topWidth: 1.3, bottomWidth: 2.4, topPositionX: 0.55, wholePositionX: 0},
    ]

    // Transform Node that acts as the parent of all piano keys
    const keyboard = new BABYLON.TransformNode("keyboard");

    keyParams.forEach(key => {
        buildKey(scene, keyboard, Object.assign({register: 4, referencePositionX: 0}, key));
    })
    ```

    Wie Sie wahrscheinlich bemerkt haben, platzieren wir in diesem Codeblock alle Tasten relativ zum Ursprung des Raumes.

1. Dies ist der Code, den *scene.js* bisher enthält:

    ```javascript
    const buildKey = function (scene, parent, props) {
        if (props.type === "white") {
            /*
            Props for building a white key should contain: 
            note, topWidth, bottomWidth, topPositionX, wholePositionX, register, referencePositionX
    
            As an example, the props for building the middle C white key would be
            {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4, register: 4, referencePositionX: 0}
            */
    
            // Create bottom part
            const bottom = BABYLON.MeshBuilder.CreateBox("whiteKeyBottom", {width: props.bottomWidth, height: 1.5, depth: 4.5}, scene);
    
            // Create top part
            const top = BABYLON.MeshBuilder.CreateBox("whiteKeyTop", {width: props.topWidth, height: 1.5, depth: 5}, scene);
            top.position.z =  4.75;
            top.position.x += props.topPositionX;
    
            // Merge bottom and top parts
            // Parameters of BABYLON.Mesh.MergeMeshes: (arrayOfMeshes, disposeSource, allow32BitsIndices, meshSubclass, subdivideWithSubMeshes, multiMultiMaterials)
            const key = BABYLON.Mesh.MergeMeshes([bottom, top], true, false, null, false, false);
            key.position.x = props.referencePositionX + props.wholePositionX;
            key.name = props.note + props.register;
            key.parent = parent;
    
            return key;
        }
        else if (props.type === "black") {
            /*
            Props for building a black key should contain: 
            note, wholePositionX, register, referencePositionX
    
            As an example, the props for building the C#4 black key would be
            {type: "black", note: "C#", wholePositionX: -13.45, register: 4, referencePositionX: 0}
            */
    
            // Create black color material
            const blackMat = new BABYLON.StandardMaterial("black");
            blackMat.diffuseColor = new BABYLON.Color3(0, 0, 0);
    
            // Create black key
            const key = BABYLON.MeshBuilder.CreateBox(props.note + props.register, {width: 1.4, height: 2, depth: 5}, scene);
            key.position.z += 4.75;
            key.position.y += 0.25;
            key.position.x = props.referencePositionX + props.wholePositionX;
            key.material = blackMat;
            key.parent = parent;
    
            return key;
        }
    }

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
    
        // Transform Node that acts as the parent of all piano keys
        const keyboard = new BABYLON.TransformNode("keyboard");
    
        const keyParams = [
            {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4},
            {type: "black", note: "C#", wholePositionX: -13.45},
            {type: "white", note: "D", topWidth: 1.4, bottomWidth: 2.4, topPositionX: 0, wholePositionX: -12},
            {type: "black", note: "D#", wholePositionX: -10.6},
            {type: "white", note: "E", topWidth: 1.4, bottomWidth: 2.3, topPositionX: 0.45, wholePositionX: -9.6},
            {type: "white", note: "F", topWidth: 1.3, bottomWidth: 2.4, topPositionX: -0.55, wholePositionX: -7.2},
            {type: "black", note: "F#", wholePositionX: -6.35},
            {type: "white", note: "G", topWidth: 1.3, bottomWidth: 2.3, topPositionX: -0.2, wholePositionX: -4.8},
            {type: "black", note: "G#", wholePositionX: -3.6},
            {type: "white", note: "A", topWidth: 1.3, bottomWidth: 2.3, topPositionX: 0.2, wholePositionX: -2.4},
            {type: "black", note: "A#", wholePositionX: -0.85},
            {type: "white", note: "B", topWidth: 1.3, bottomWidth: 2.4, topPositionX: 0.55, wholePositionX: 0},
        ]

        // Transform Node that acts as the parent of all piano keys
        const keyboard = new BABYLON.TransformNode("keyboard");
    
        keyParams.forEach(key => {
            buildKey(scene, keyboard, Object.assign({register: 4, referencePositionX: 0}, key));
        })

        const xrHelper = await scene.createDefaultXRExperienceAsync();

        return scene;
    }
    ```

1. So würde die resultierende Klaviatur aussehen:

    ![Klaviatur mit einem Register](./images/piano-one-register.png)

## <a name="expanding-to-an-88-key-piano"></a>Erweitern auf ein Klavier mit 88 Tasten

Lassen Sie uns in diesem Abschnitt die Verwendung der Funktionen zur Tastenerstellung erweitern, um eine vollständige Klaviatur mit 88 Tasten zu generieren.

1. Wie bereits erwähnt, enthält eine vollständige Klaviatur mit 88 Tasten 7 wiederholte Register und vier weitere Noten. 3 dieser zusätzlichen Notizen befinden sich im Register 0 (am linken Ende der Klaviatur), und 1 befindet sich in Register 8 (am rechten Ende der Klaviatur).

    ![Klaviaturlayout mit 88 Tasten](./images/88-key-piano-keyboard-layout.jpg)

1. Wir arbeiten zunächst an der Erstellung der 7 vollständigen Wiederholungen, indem wir eine zusätzliche Schleife um die Schleife hinzufügen, die wir zuvor geschrieben hatten. Ersetzen Sie die vorhergehende Schleife für die `buildKey()`-Funktion durch den folgenden Code:

    ```javascript
    // Register 1 through 7
    var referencePositionX = -2.4*14;
    for (let register = 1; register <= 7; register++) {
        keyParams.forEach(key => {
            buildKey(scene, keyboard, Object.assign({register: register, referencePositionX: referencePositionX}, key));
        })
        referencePositionX += 2.4*7;
    }
    ```

    In dieser Schleife erstellen wir die Tasten für die Register 1 bis 7 und erhöhen jedes Mal, wenn wir zum nächsten Register wechseln, die Referenzposition.

1. Anschließend erstellen wir die restlichen Tasten. Fügen Sie der Funktion `createScene()` den folgenden Codeausschnitt hinzu:

    ```javascript
    // Register 0
    buildKey(scene, keyboard, {type: "white", note: "A", topWidth: 1.9, bottomWidth: 2.3, topPositionX: -0.20, wholePositionX: -2.4, register: 0, referencePositionX: -2.4*21});
    keyParams.slice(10, 12).forEach(key => {
        buildKey(scene, keyboard, Object.assign({register: 0, referencePositionX: -2.4*21}, key));
    })

    // Register 8
    buildKey(scene, keyboard, {type: "white", note: "C", topWidth: 2.3, bottomWidth: 2.3, topPositionX: 0, wholePositionX: -2.4*6, register: 8, referencePositionX: 84});
    ```

    Beachten Sie, dass die äußerste linke und die äußerste rechte Taste der Klaviatur nicht in die Abmessungen der in `keyParams` definierten Eigenschaften passen, (da sie sich an der Kante nicht neben einer schwarzen Taste befinden). Daher müssen wir für jede von ihnen ein neues `props`-Objekt definieren, um ihre spezielle Form anzugeben.

1. Nachdem die Änderungen vorgenommen wurden, sollte die erstellte Klaviatur so aussehen:

    ![Vollständiges Klaviatur-Gittermodell](./images/full-keyboard-mesh.png)

## <a name="adding-a-piano-frame"></a>Hinzufügen eines Klavierrahmens

1. Die Szene sieht etwas seltsam aus, wenn nur eine Klaviatur im Raum schwebt. Fügen wir einen Klavierrahmen um die Klaviatur hinzu, um das Aussehen eines aufrecht stehenden Klaviers zu erzielen.

1. Ähnlich wie bei der Erstellung der Tasten können wir auch den Rahmen erstellen, indem wir eine Gruppe von Box-Gittermodellen positionieren und kombinieren.

    Allerdings lassen wir Ihnen die Herausforderung für eigene Versuche in stillen Stunden und verwenden stattdessen [BABYLON.SceneLoader.ImportMesh](https://doc.babylonjs.com/divingDeeper/importers/loadingFileTypes#sceneloaderimportmesh), um ein vorgefertigtes Gittermodell eines stehenden Klavierrahmens zu importieren. Fügen Sie dieses Stück Code an `createScene()` an:

    ```javascript
    // Transform node that acts as the parent of all piano components
    const piano = new BABYLON.TransformNode("piano");
    keyboard.parent = piano;

    // Import and scale piano frame
    BABYLON.SceneLoader.ImportMesh("frame", "https://docs.microsoft.com/windows/mixed-reality/develop/javascript/tutorials/babylonjs-webxr-piano/files", "pianoFrame.babylon", scene, function(meshes) {
        const frame = meshes[0];
        frame.parent = piano;
    });
    ```

    Beachten Sie, dass wir wiederum ein übergeordnetes Element `TransformNode` mit dem Namen `piano` erstellen, um die Klaviatur und den Rahmen als Ganzes zu gruppieren. Dadurch wird das Bewegen oder Skalieren des gesamten Klaviers sehr viel einfacher, sollte es jemals erforderlich sein.

1. Beachten Sie, dass nach dem Importieren des Rahmens die Klaviatur unten auf dem Rahmen liegt (da die Y-Koordinaten der Tasten standardmäßig bei 0 liegen). Heben wir die Klaviatur so an, dass sie in den aufrechten Klavierrahmen passt:

    ```javascript
    // Lift piano keys
    keyboard.position.y += 80;
    ```

    Da `keyboard` das übergeordnete Element aller Klaviertasten ist, können wir alle Klaviertasten anheben, indem wir einfach die Y-Position von `keyboard` ändern.

1. Der endgültige Code von *scene.js* sollte wie folgt aussehen:

    ```javascript
    const buildKey = function (scene, parent, props) {
        if (props.type === "white") {
            /*
            Props for building a white key should contain: 
            note, topWidth, bottomWidth, topPositionX, wholePositionX, register, referencePositionX
    
            As an example, the props for building the middle C white key would be
            {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4, register: 4, referencePositionX: 0}
            */
    
            // Create bottom part
            const bottom = BABYLON.MeshBuilder.CreateBox("whiteKeyBottom", {width: props.bottomWidth, height: 1.5, depth: 4.5}, scene);
    
            // Create top part
            const top = BABYLON.MeshBuilder.CreateBox("whiteKeyTop", {width: props.topWidth, height: 1.5, depth: 5}, scene);
            top.position.z =  4.75;
            top.position.x += props.topPositionX;
    
            // Merge bottom and top parts
            // Parameters of BABYLON.Mesh.MergeMeshes: (arrayOfMeshes, disposeSource, allow32BitsIndices, meshSubclass, subdivideWithSubMeshes, multiMultiMaterials)
            const key = BABYLON.Mesh.MergeMeshes([bottom, top], true, false, null, false, false);
            key.position.x = props.referencePositionX + props.wholePositionX;
            key.name = props.note + props.register;
            key.parent = parent;
    
            return key;
        }
        else if (props.type === "black") {
            /*
            Props for building a black key should contain: 
            note, wholePositionX, register, referencePositionX
    
            As an example, the props for building the C#4 black key would be
            {type: "black", note: "C#", wholePositionX: -13.45, register: 4, referencePositionX: 0}
            */
    
            // Create black color material
            const blackMat = new BABYLON.StandardMaterial("black");
            blackMat.diffuseColor = new BABYLON.Color3(0, 0, 0);
    
            // Create black key
            const key = BABYLON.MeshBuilder.CreateBox(props.note + props.register, {width: 1.4, height: 2, depth: 5}, scene);
            key.position.z += 4.75;
            key.position.y += 0.25;
            key.position.x = props.referencePositionX + props.wholePositionX;
            key.material = blackMat;
            key.parent = parent;
    
            return key;
        }
    }

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

        const keyParams = [
            {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4},
            {type: "black", note: "C#", wholePositionX: -13.45},
            {type: "white", note: "D", topWidth: 1.4, bottomWidth: 2.4, topPositionX: 0, wholePositionX: -12},
            {type: "black", note: "D#", wholePositionX: -10.6},
            {type: "white", note: "E", topWidth: 1.4, bottomWidth: 2.3, topPositionX: 0.45, wholePositionX: -9.6},
            {type: "white", note: "F", topWidth: 1.3, bottomWidth: 2.4, topPositionX: -0.55, wholePositionX: -7.2},
            {type: "black", note: "F#", wholePositionX: -6.35},
            {type: "white", note: "G", topWidth: 1.3, bottomWidth: 2.3, topPositionX: -0.2, wholePositionX: -4.8},
            {type: "black", note: "G#", wholePositionX: -3.6},
            {type: "white", note: "A", topWidth: 1.3, bottomWidth: 2.3, topPositionX: 0.2, wholePositionX: -2.4},
            {type: "black", note: "A#", wholePositionX: -0.85},
            {type: "white", note: "B", topWidth: 1.3, bottomWidth: 2.4, topPositionX: 0.55, wholePositionX: 0},
        ]
    
        // Transform Node that acts as the parent of all piano keys
        const keyboard = new BABYLON.TransformNode("keyboard");
    
        // Register 1 through 7
        var referencePositionX = -2.4*14;
        for (let register = 1; register <= 7; register++) {
            keyParams.forEach(key => {
                buildKey(scene, keyboard, Object.assign({register: register, referencePositionX: referencePositionX}, key));
            })
            referencePositionX += 2.4*7;
        }
    
        // Register 0
        buildKey(scene, keyboard, {type: "white", note: "A", topWidth: 1.9, bottomWidth: 2.3, topPositionX: -0.20, wholePositionX: -2.4, register: 0, referencePositionX: -2.4*21});
        keyParams.slice(10, 12).forEach(key => {
            buildKey(scene, keyboard, Object.assign({register: 0, referencePositionX: -2.4*21}, key));
        })
    
        // Register 8
        buildKey(scene, keyboard, {type: "white", note: "C", topWidth: 2.3, bottomWidth: 2.3, topPositionX: 0, wholePositionX: -2.4*6, register: 8, referencePositionX: 84});
    
        // Transform node that acts as the parent of all piano components
        const piano = new BABYLON.TransformNode("piano");
        keyboard.parent = piano;
    
        // Import and scale piano frame
        BABYLON.SceneLoader.ImportMesh("frame", "https://docs.microsoft.com/windows/mixed-reality/develop/javascript/tutorials/babylonjs-webxr-piano/files", "pianoFrame.babylon", scene, function(meshes) {
            const frame = meshes[0];
            frame.parent = piano;
        });
    
        // Lift the piano keyboard
        keyboard.position.y += 80;
    
        const xrHelper = await scene.createDefaultXRExperienceAsync();
    
        return scene;
    }
    ```

1. Nun sollten wir ein aufrechtes Klavier haben, das so aussieht ![Stehendes Klavier-Gittermodell](./images/standup-piano-mesh.png)

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Nächstes Tutorial: Spielen des 3D-Klaviers](keyboard-interaction-03.md)
