---
title: Verwenden von WebXR mit Windows Mixed Reality
description: Lernen Sie die Grundlagen der Verwendung und Entwicklung für WebXR-Anwendungen kennen, die auf Windows Mixed Reality immersiven Headsets ausgeführt werden.
author: yonet
ms.author: v-vtieto
ms.date: 09/24/2021
ms.topic: article
keywords: WebXR, WinMR, WebAR, WebVR, WindowsMixedReality, HoloLens, Windows Mixed Reality, Web VR, Web xr, Web mr, web ar, 360, 360 Video, 360 Videos, 360 Foto, 360 Fotos, 360 Inhalte, immersives Web, immersiveweb, IW
ms.openlocfilehash: b0ab1eab5f1c3e546dde367c2cdb992fba7b452d
ms.sourcegitcommit: 3176df29fb0c9508751bd370f1211031d50d2c14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2021
ms.locfileid: "129148697"
---
# <a name="javascript-development-with-webxr"></a>JavaScript-Entwicklung mit WebXR

JavaScript ist eine der beliebtesten Programmiersprachen der Welt! Es ist einfach, einfach und im Web weit verbreitet. Nutzen Sie die Leistungsfähigkeit Ihrer JavaScript- und Webkenntnisse, um ansprechendere Mixed Reality zu schaffen.

## <a name="mixed-reality-applications-on-the-web"></a>Mixed Reality Anwendungen im Web

Mixed Reality Features sind im Web über [WebXR](webxr-overview.md)verfügbar. Sie können Virtual Reality-Inhalte (VR) und Augmented Reality-Inhalte (AR) in einem kompatiblen WebXR-fähigen Browser anzeigen, ohne zusätzliche Software oder Plug-Ins zu installieren. Sie können denselben Browser mit einem physischen Gerät wie dem HoloLens 2 verwenden.

Die [**WebXR-Geräte-API**](https://www.w3.org/TR/webxr/) ist für den Zugriff auf Virtual Reality-Geräte (VR) und Augmented Reality-Geräte (AR) im Web vorgesehen, einschließlich Sensoren und Bildschirme mit Kopfaufbewahrung. Die WebXR-Geräte-API ist in Microsoft Edge und Chrome Version 79 verfügbar, und höhere Versionen unterstützen WebXR standardmäßig. Den aktuellen Browserunterstützungsstatus für WebXR finden Sie unter [caniuse.com](https://caniuse.com/#search=webxr).

> [!NOTE]
> **WebVR** ist veraltet und in aktuellen Browsern nicht verfügbar und sollte daher nicht für neue Entwicklungen verwendet werden. Sie müssen alle vorhandenen **WebVR-Implementierungen** zu **WebXR** migrieren.

| WebXR-Feature | Verfügbarkeit |
|---------|---------|
|[WebXR-Geräte-API (w3.org)](https://www.w3.org/TR/webxr/) | Edge 81 auf Windows Desktop <br>Edge 91 auf Hololens 2|
|[WebXR Augmented Reality-Modul – Ebene 1 (w3.org)](https://www.w3.org/TR/webxr-ar-module-1/)|Edge 91. Nur Hololens 2|
|[WebXR-Handeingabemodul – Ebene 1 (w3.org)](https://www.w3.org/TR/webxr-hand-input-1/)|Edge 93. Nur Hololens 2|
|[WebXR Anchors-Modul (immersive-web.github.io)](https://immersive-web.github.io/anchors/)|Edge 93. Nur Hololens 2|
|[WebXR-Treffertestmodul (immersive-web.github.io)](https://immersive-web.github.io/hit-test/)|Edge 93. Nur Hololens 2 |

### <a name="viewing-webxr"></a>Anzeigen von WebXR

Sie können WebXR-Funktionen in Windows Mixed Reality mit [den neuen Browsern Microsoft Edge](../../whats-new/new-microsoft-edge.md) und [Firefox Reality](https://mixedreality.mozilla.org/firefox-reality/) anzeigen.
Um zu testen, ob Ihr Browser WebXR unterstützt, können Sie in Ihrem Browser zu [WebXR-Beispiele](https://immersive-web.github.io/webxr-samples/) navigieren.

## <a name="what-can-i-use-to-develop-immersive-web-experiences"></a>Was kann ich verwenden, um immersive Weberfahrungen zu entwickeln?

Die folgende Liste zeigt die JavaScript-Frameworks und -APIs zum Erstellen immersiver Erfahrungen, die derzeit den Markt bestimmen und von Mixed Reality-JavaScript-Entwicklern allgemein akzeptiert und übernommen werden:

|  |  |
| --- | --- |
|[**Babylon.js**](https://doc.babylonjs.com/)<br/><br/> Javascript ist eine JavaScript-3D-Engine, die die Entwicklung von 3D-Inhalten und immersiven Anwendungen vereinfacht. Bevor Sie mit immersiven Anwendungen beginnen, sollten Sie sich mit den Grundlagen der Babylon.js-Entwicklung auskennen.<br/><br/>– Informationen zum Erstellen von 3D-Anwendungen mit babylon.js: [Erste Schritte](https://doc.babylonjs.com/start)<br/>– Play with 3D examples and their source code using babylon.js: Playground (Wiedergeben mit 3D-Beispielen und dem zugehörigen Quellcode mithilfe von babylon.js: [Playground)](https://doc.babylonjs.com/examples/)<br/>– Tieferer Einblick in [WebXR](https://doc.babylonjs.com/divingDeeper/webXR)<br/>– Erste Schritte mit unseren Tutorials: [Erstellen Ihrer ersten "Hallo Welt!"-App](tutorials/babylonjs-webxr-helloworld/introduction-01.md)|![Js-Logo](images/babylon.js.example.png) |
|[**A-Frame**](https://aframe.io/) <br/><br/>A-frame ist ein deklaratives JavaScript-Framework, das Sie für die ersten Schritte mit Virtual Reality im Web verwenden können. Weitere Informationen finden Sie in der [A-Frame-Dokumentation.](https://aframe.io/docs/1.2.0/introduction/) |![A-Frame](images/a-frame.example.png)  |
|[**Three.js**](https://threejs.org) <br/><br/>Three.js ist eine beliebte 3D-Bibliothek zum Erstellen immersiver Benutzererlebnisse. Erfahren Sie mehr über [three.js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) und [sehen Sie sich Beispiele an.](https://threejs.org/examples/#webgl_animation_cloth) |![Three.js](images/three.js.example.png)  |
|[**WebGL**](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)  <br/><br/>Sie können direkt über WebGL-APIs auf die WebXR-Geräte-APIs zugreifen. WebGL (Web Graphics Library) ist eine JavaScript-API zum Rendern leistungsstarker interaktiver 3D- und 2D-Grafiken in jedem kompatiblen Webbrowser ohne Plug-Ins. |![WebGL](images/webgl.example.png)  |

## <a name="see-also"></a>Weitere Informationen

* [WebXR-Geräte-API-Spezifikation](https://immersive-web.github.io/webxr/)
* [Dokumentation zur WebXR-Geräte-API](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [WebXR-Beispiele](https://immersive-web.github.io/webxr-samples/)
* [Immersiveweb.dev](https://immersiveweb.dev/)
* [Verwenden von Babylon.js zum Erstellen von WebXR-Funktionen](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [WebGL-API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))
* [Gamepad-API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) und [Gamepad-Erweiterungen](https://w3c.github.io/gamepad/extensions.html)
* [Windows Mixed Reality und die neue Microsoft Edge](../../whats-new/new-microsoft-edge.md)
* [Behandeln von verloren gegangenen Kontexten in WebGL](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [Pointerlock](https://www.w3.org/TR/pointerlock/)
* [glTF](https://www.khronos.org/gltf)
* [Immersive Webcommunitygruppe](https://www.w3.org/community/immersive-web/)
* [Immersive Web W3C Github](https://github.com/immersive-web)

## <a name="next-steps--tutorials"></a>Nächste Schritte– Tutorials

> [!div class="nextstepaction"]
> [Erstellen Ihrer ersten WebXR-Anwendung mit Babylon.js](tutorials/babylonjs-webxr-helloworld/introduction-01.md)

> [!div class="nextstepaction"]
> [Erstellen eines Builds in WebXR mithilfe von Babylon.js](tutorials/babylonjs-webxr-piano/introduction-01.md)
