---
title: JavaScript-Entwicklung – Übersicht
description: Übersicht über Mixed Reality Entwicklung mit JavaScript für immersive Headsets für Web, Mobilgeräte und Windows.
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: JavaScript, WebXR, WinMR, WebAR, WebVR, WindowsMixedReality, HoloLens, Windows Mixed Reality, Web Vr, Web xr, Web mr, web ar, 360, 360 Video, 360 Videos, 360 Foto, 360 Fotos, 360 Inhalte, immersives Web, immersives Web, IW, immersiveweb
ms.openlocfilehash: de6314b5651740eca23a9078d4b05e1d92344d1742ea433d7b924cbde4457b8c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210506"
---
# <a name="javascript-development-overview"></a>JavaScript-Entwicklung – Übersicht

JavaScript ist eine der beliebtesten Programmiersprachen der Welt! Es ist einfach, einfach und wird im Web häufig verwendet. Nutzen Sie die Leistungsfähigkeit Ihrer JavaScript- und Webkenntnisse, um ansprechendere Funktionen Mixed Reality erstellen.

## <a name="mixed-reality-applications-on-the-web"></a>Mixed Reality von Anwendungen im Web

Mixed Reality Features sind im Web mit [webXR verfügbar.](webxr-overview.md) Sie können Inhalte von Virtual Reality (VR) und Augmented Reality (AR) in einem kompatiblen WebXR-fähigen Browser anzeigen, ohne zusätzliche Software oder Plug-Ins zu installieren. Sie können denselben Browser mit einem physischen Gerät wie dem HoloLens 2. Weitere Informationen finden [Sie in unserer WebXR-Dokumentation.](webxr-overview.md)

> [!NOTE]
> **WebVR** ist veraltet und in aktuellen Browsern nicht verfügbar. Daher sollte es nicht für neue Entwicklungen verwendet werden. Sie müssen alle vorhandenen **WebVR-Implementierungen** zu **WebXR migrieren.**

## <a name="what-can-i-use-to-develop-immersive-web-experiences"></a>Was kann ich verwenden, um immersive Weberfahrungen zu entwickeln?

Die folgende Liste zeigt die JavaScript-Frameworks und -APIs zum Erstellen von immersiven Umgebungen, die derzeit den Markt überschreiben und von JavaScript-Entwicklern allgemein akzeptiert und Mixed Reality werden:

|  |  |
| --- | --- |
|[**Babylon.js**](https://doc.babylonjs.com/)<br/><br/> Dabei handelt es sich um eine JavaScript-3D-Engine, die die Entwicklung von 3D-Inhalten und immersiven Anwendungen vereinfacht. Bevor Sie mit immersiven Anwendungen beginnen, sollten Sie sich mit den Grundlagen der entwicklung Babylon.js machen.<br/><br/>– Erfahren Sie, wie Sie 3D-Anwendungen mit babylon.js [Erste Schritte erstellen.](https://doc.babylonjs.com/start)<br/>– Play with 3D examples and their source code using babylon.js [Playground](https://doc.babylonjs.com/examples/)<br/>– Tiefere Einblicke in [WebXR](https://doc.babylonjs.com/divingDeeper/webXR)<br/>– Informationen zu den ersten Schritte mit unseren Tutorials [Erstellen Ihrer ersten "Hallo Welt!"-App](tutorials/babylonjs-webxr-helloworld/introduction-01.md)|![Js-Logo](images/babylon.js.example.png) |
|[**A-Frame**](https://aframe.io/) <br/><br/>A-Frame ist ein deklaratives JavaScript-Framework für die ersten Schritte mit Virtual Reality im Web. Weitere Informationen finden Sie in der [A-Frame-Dokumentation.](https://aframe.io/docs/1.2.0/introduction/) |![A-Frame](images/a-frame.example.png)  |
|[**Three.js**](https://threejs.org) <br/><br/>Three.js ist eine beliebte 3D-Bibliothek zum Erstellen von immersiven Umgebungen. Weitere Informationen [ zu ](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene)three.jsfinden Sie auf der Dokumentationsseite und in den [Beispielen](https://threejs.org/examples/#webgl_animation_cloth). |![Three.js](images/three.js.example.png)  |
|[**WebGL**](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)  <br/><br/>Sie können direkt über WebGL-APIs auf die WebXR-Geräte-APIs zugreifen. WebGL (Web Graphics Library) ist eine JavaScript-API zum Rendern leistungsstarker interaktiver 3D- und 2D-Grafiken in jedem kompatiblen Webbrowser ohne Verwendung von Plug-Ins. |![WebGL](images/webgl.example.png)  |

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie mehr über die ersten Schritte mit unseren Tutorials.

> [!div class="nextstepaction"]
> [Erstellen Ihrer ersten "Hallo Welt!"-App](tutorials/babylonjs-webxr-helloworld/introduction-01.md)

## <a name="see-also"></a>Weitere Informationen

* [Übersicht über WebXR](webxr-overview.md)
* [WebXR-Geräte-API-Spezifikation](https://immersive-web.github.io/webxr/)
* [Dokumentation zur WebXR-Geräte-API](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [Immersiveweb.dev](https://immersiveweb.dev/)
* [WebXR-Beispiele](https://immersive-web.github.io/webxr-samples/)
* [Verwenden Babylon.js zum Erstellen von WebXR-Erfahrungen](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [Windows Mixed Reality und die neue Microsoft Edge](/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [Immersive Web W3C Github](https://github.com/immersive-web)
* [WebGL-API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))
* [Gamepad-API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) und [Gamepad-Erweiterungen](https://w3c.github.io/gamepad/extensions.html)
