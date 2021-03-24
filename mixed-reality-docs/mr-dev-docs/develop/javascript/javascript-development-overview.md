---
title: JavaScript-Entwicklungs Übersicht
description: Übersicht über die Entwicklung gemischter Realität mithilfe von JavaScript für Web-, Mobile und Windows-immersive Headsets.
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: JavaScript, webxr, winmr, webar, webvr, windowsmixedreality, hololens, Windows Mixed Reality, Web VR, Web XR, Web Mr, Web AR, 360, 360 Video, 360 Videos, 360 Photo, 360 Fotos, 360 Content, immersives Web, immersive-Web, IW, immersiveweb
ms.openlocfilehash: 051c6079da939224c88d6414978b2b4b0e67f87c
ms.sourcegitcommit: cbfd1c37612aa6904fa41642ede6281d491e478d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/23/2021
ms.locfileid: "104909055"
---
# <a name="javascript-development-overview"></a>JavaScript-Entwicklung – Übersicht

JavaScript ist eine der beliebtesten Programmiersprachen auf der Welt. Es ist einfach, einfach und im Web häufig verwendet. Profitieren Sie von der Leistungsfähigkeit Ihrer JavaScript-und Webkenntnisse, um ansprechender gemischte Umgebungen zu entwickeln.

## <a name="mixed-reality-applications-on-the-web"></a>Gemischte Reality-Anwendungen im Web

Mixed Reality-Features sind im Web mit [webxr](webxr-overview.md)verfügbar. Sie können den Inhalt der virtuellen Realität (VR) und der erweiterten Realität (AR) in einem kompatiblen webxr-fähigen Browser sehen, ohne zusätzliche Software oder Plug-ins zu installieren. Sie können denselben Browser mit einem physischen Gerät wie hololens 2 verwenden. Weitere Informationen finden Sie in unserer [webxr](webxr-overview.md) -Dokumentation.

> [!NOTE]
> **Webvr** ist veraltet und in aktuellen Browsern nicht verfügbar. Daher sollte es nicht für neue Entwicklungen verwendet werden. Sie müssen alle vorhandenen **webvr** -Implementierungen in **webxr** migrieren.

## <a name="what-can-i-use-to-develop-immersive-web-experiences"></a>Was kann ich verwenden, um immersive Weberlebnisse zu entwickeln?

In der folgenden Liste werden die JavaScript-Frameworks und APIs zum Entwickeln von immersiven Erfahrungen gezeigt, die derzeit den Markt dominieren und von gemischten Reality-JavaScript-Entwicklern weitgehend akzeptiert und übernommen werden:

|  |  |
| --- | --- |
|[**Babylon.js**](https://doc.babylonjs.com/)<br/><br/> Babylon ist ein JavaScript-3D-Modul, das die Entwicklung von 3D-Inhalten und immersiven Anwendungen erleichtert. Vor den ersten Schritten mit immersiven Anwendungen empfiehlt es sich, die Grundlagen der Babylon.js Entwicklung zu erlernen.<br/><br/>: Erfahren Sie, wie Sie 3D-Anwendungen [mit babylon.js ersten](https://doc.babylonjs.com/start)Schritten erstellen.<br/>-Wiedergabe mit 3D-Beispielen und deren Quellcode mit babylon.js [Playground](https://doc.babylonjs.com/examples/)<br/>-Tiefer Einblick in [webxr](https://doc.babylonjs.com/divingDeeper/webXR)<br/>-Erfahren Sie mehr über die ersten Schritte mit unseren Tutorials [Erstellen Ihrer ersten "Hallo Welt!"-App](tutorials/babylonjs-webxr-helloworld/introduction-01.md)|![Babylonjs-Logo](images/babylon.js.example.png) |
|[**A-Frame**](https://aframe.io/) <br/><br/>Ein-Frame ist ein deklaratives JavaScript-Framework für den Einstieg in die virtuelle Realität im Web. Weitere Informationen finden Sie in der [Dokumentation zum A-Frame](https://aframe.io/docs/1.2.0/introduction/) . |![A-Frame](images/a-frame.example.png)  |
|[**Three.js**](https://threejs.org) <br/><br/>Three.js ist eine beliebte 3D-Bibliothek zum Erstellen von immersiven Erfahrungen. Weitere Informationen zu [three.js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) finden Sie auf der Dokumentationsseite und in den [Beispielen](https://threejs.org/examples/#webgl_animation_cloth). |![Three.js](images/three.js.example.png)  |
|[**WebGL**](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)  <br/><br/>Mithilfe von WebGL-APIs können Sie direkt auf die webxr-Geräte-APIs zugreifen. WebGL (Webgrafik Bibliothek) ist eine JavaScript-API zum Rendern von hochleistungsfähigen interaktiven 3D-und 2D-Grafiken innerhalb eines kompatiblen Webbrowsers ohne Verwendung von Plug-ins. |![WebGL](images/webgl.example.png)  |

## <a name="next-steps"></a>Nächste Schritte

Informieren Sie sich über die ersten Schritte mit unseren Tutorials.

> [!div class="nextstepaction"]
> [Erstellen Ihrer ersten "Hallo Welt!"-App](tutorials/babylonjs-webxr-helloworld/introduction-01.md)

## <a name="see-also"></a>Weitere Informationen

* [Übersicht über webxr](webxr-overview.md)
* [Webxr-Geräte-API-Spezifikation](https://immersive-web.github.io/webxr/)
* [Dokumentation zur webxr-Geräte-API](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [Immersiveweb.dev](https://immersiveweb.dev/)
* [Webxr-Beispiele](https://immersive-web.github.io/webxr-samples/)
* [Verwenden von Babylon.js zum Erstellen von webxr-Erfahrungen](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [Windows Mixed Reality und die neue Microsoft Edge](/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [Immersives Web-W3C GitHub](https://github.com/immersive-web)
* [WebGL-API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))
* [Gamepad-API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) -und [Gamepad-Erweiterungen](https://w3c.github.io/gamepad/extensions.html)
