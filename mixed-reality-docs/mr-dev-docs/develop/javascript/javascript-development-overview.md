---
title: Übersicht über die JavaScript-Entwicklung
description: Übersicht über Mixed Reality Entwicklung mit JavaScript für immersive Headsets für Web, Mobilgeräte und Windows.
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: JavaScript, WebXR, WinMR, WebAR, WebVR, WindowsMixedReality, HoloLens, Windows Mixed Reality, Web VR, Web xr, Web mr, web ar, 360, 360 Video, 360 Videos, 360 Foto, 360 Fotos, 360 Inhalte, immersives Web, immersives Web, IW, immersiveweb
ms.openlocfilehash: 311241d9dec6f5d086a45766c040b1b2b9eb4128
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394344"
---
# <a name="javascript-development-overview"></a>JavaScript-Entwicklung – Übersicht

JavaScript ist eine der beliebtesten Programmiersprachen der Welt! Es ist einfach, einfach und im Web weit verbreitet. Nutzen Sie die Leistungsfähigkeit Ihrer JavaScript- und Webkenntnisse, um ansprechendere Mixed Reality zu schaffen.

## <a name="mixed-reality-applications-on-the-web"></a>Mixed Reality Anwendungen im Web

Mixed Reality Features sind im Web mithilfe von [WebXR](webxr-overview.md)verfügbar. Sie können Virtual Reality-Inhalte (VR) und Augmented Reality-Inhalte (AR) in einem kompatiblen WebXR-fähigen Browser anzeigen, ohne zusätzliche Software oder Plug-Ins zu installieren. Sie können denselben Browser mit einem physischen Gerät wie dem HoloLens 2 verwenden. Weitere Informationen finden Sie in unserer [WebXR-Dokumentation.](webxr-overview.md)

> [!NOTE]
> **WebVR** ist veraltet und in aktuellen Browsern nicht verfügbar und sollte daher nicht für neue Entwicklungen verwendet werden. Sie müssen alle vorhandenen **WebVR-Implementierungen** zu **WebXR** migrieren.

## <a name="what-can-i-use-to-develop-immersive-web-experiences"></a>Was kann ich verwenden, um immersive Weberfahrungen zu entwickeln?

Die folgende Liste zeigt die JavaScript-Frameworks und -APIs zum Erstellen immersiver Erfahrungen, die derzeit den Markt bestimmen und von Mixed Reality JavaScript-Entwicklern allgemein akzeptiert und übernommen werden:

|  |  |
| --- | --- |
|[**Babylon.js**](https://doc.babylonjs.com/)<br/><br/> Javascript ist eine JavaScript-3D-Engine, die die Entwicklung von 3D-Inhalten und immersiven Anwendungen vereinfacht. Bevor Sie mit immersiven Anwendungen beginnen, empfiehlt es sich, sich mit den Grundlagen der Babylon.js Entwicklung zu informieren.<br/><br/>– Erfahren Sie, wie Sie 3D-Anwendungen mit babylon.js [Erste Schritte](https://doc.babylonjs.com/start)erstellen.<br/>– Play with 3D examples and their source code using babylon.js Playground (Wiedergeben mit 3D-Beispielen und dem zugehörigen Quellcode mithilfe von babylon.js [Playground)](https://doc.babylonjs.com/examples/)<br/>– Tieferer Einblick in [WebXR](https://doc.babylonjs.com/divingDeeper/webXR)<br/>– Erfahren Sie, wie Sie mit unseren Tutorials [Ihre erste "Hallo Welt!"-App erstellen.](tutorials/babylonjs-webxr-helloworld/introduction-01.md)|![Js-Logo](images/babylon.js.example.png) |
|[**A-Frame**](https://aframe.io/) <br/><br/>A-frame ist ein deklaratives JavaScript-Framework für die ersten Schritte mit Virtual Reality im Web. Weitere Informationen finden Sie in der [A-Frame-Dokumentation.](https://aframe.io/docs/1.2.0/introduction/) |![A-Frame](images/a-frame.example.png)  |
|[**Three.js**](https://threejs.org) <br/><br/>Three.js ist eine beliebte 3D-Bibliothek zum Erstellen immersiver Benutzererlebnisse. Weitere Informationen [ zuthree.js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) finden Sie auf der Dokumentationsseite und in den [Beispielen](https://threejs.org/examples/#webgl_animation_cloth). |![Three.js](images/three.js.example.png)  |
|[**WebGL**](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)  <br/><br/>Sie können direkt über WebGL-APIs auf die WebXR-Geräte-APIs zugreifen. WebGL (Web Graphics Library) ist eine JavaScript-API zum Rendern leistungsstarker interaktiver 3D- und 2D-Grafiken in jedem kompatiblen Webbrowser ohne Plug-Ins. |![WebGL](images/webgl.example.png)  |

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
* [Verwenden von Babylon.js zum Erstellen von WebXR-Funktionen](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [Windows Mixed Reality und die neue Microsoft Edge](/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [Immersive Web W3C Github](https://github.com/immersive-web)
* [WebGL-API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))
* [Gamepad-API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) und [Gamepad-Erweiterungen](https://w3c.github.io/gamepad/extensions.html)
