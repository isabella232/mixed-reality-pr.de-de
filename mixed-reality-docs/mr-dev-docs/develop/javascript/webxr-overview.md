---
title: Verwenden von WebXR mit Windows Mixed Reality
description: Erfahren Sie mehr über die Grundlagen der Verwendung und Entwicklung für WebXR-Anwendungen, die auf Windows Mixed Reality immersive Headsets ausgeführt werden.
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebXR, WinMR, WebAR, WebVR, WindowsMixedReality, HoloLens, Windows Mixed Reality, Web Vr, Web xr, Web MR, Web ar, 360, 360 Video, 360 Videos, 360 Foto, 360 Fotos, 360 Inhalte, immersives Web, immersivesWeb, IW
ms.openlocfilehash: e670135cb00db26082b73f8465390a686de6a3e946bbffa561f9df90085970f8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115216266"
---
# <a name="webxr-overview"></a>Übersicht über WebXR

## <a name="javascript-development"></a>JavaScript-Entwicklung

JavaScript ist eine der beliebtesten Programmiersprachen der Welt! Es ist einfach, einfach und wird im Web häufig verwendet. Nutzen Sie die Leistungsfähigkeit Ihrer JavaScript- und Webkenntnisse, um ansprechendere Funktionen Mixed Reality erstellen.

## <a name="mixed-reality-applications-on-the-web"></a>Mixed Reality von Anwendungen im Web

Mixed Reality Features sind mit [webXR](webxr-overview.md)im Web verfügbar. Sie können Inhalte von Virtual Reality (VR) und Augmented Reality (AR) in einem kompatiblen WebXR-fähigen Browser anzeigen, ohne zusätzliche Software oder Plug-Ins zu installieren. Sie können denselben Browser mit einem physischen Gerät wie dem HoloLens 2.

Die [**WebXR-Geräte-API**](https://www.w3.org/TR/webxr/) ist für den Zugriff auf Virtual Reality-Geräte  **(VR)** und Augmented **Reality-Geräte** **(Augmented Reality, AR)** wie Sensoren und mit dem Kopf bereitgestellte Displays im **Web.** Die WebXR-Geräte-API ist derzeit auf Microsoft Edge chrome Version 79 und höher unterstützt WebXR als Standard. Sie können den aktuellen Browserunterstützungsstatus für WebXR unter [caniuse.com.](https://caniuse.com/#search=webxr)

> [!NOTE]
> **WebVR** ist veraltet und in aktuellen Browsern nicht verfügbar. Daher sollte es nicht für neue Entwicklungen verwendet werden. Sie müssen alle vorhandenen **WebVR-Implementierungen** zu **WebXR migrieren.**

### <a name="viewing-webxr"></a>Anzeigen von WebXR

Sie können WebXR-Erweiterungen [](../../whats-new/new-microsoft-edge.md) auf Windows Mixed Reality und den neuen Microsoft Edge [und Firefox Reality anzeigen.](https://mixedreality.mozilla.org/firefox-reality/)
Um zu testen, ob Ihr Browser WebXR unterstützt, können Sie in Ihrem Browser [zu WebXR-Beispielen](https://immersive-web.github.io/webxr-samples/) navigieren.

## <a name="what-can-i-use-to-develop-immersive-web-experiences"></a>Was kann ich verwenden, um immersive Weberfahrungen zu entwickeln?

Die folgende Liste zeigt die JavaScript-Frameworks und -APIs zum Erstellen von immersiven Umgebungen, die derzeit den Markt überschreiben und von JavaScript-Entwicklern allgemein akzeptiert und Mixed Reality werden:

|  |  |
| --- | --- |
|[**Babylon.js**](https://doc.babylonjs.com/)<br/><br/> Dabei handelt es sich um eine JavaScript-3D-Engine, die die Entwicklung von 3D-Inhalten und immersiven Anwendungen vereinfacht. Bevor Sie mit immersiven Anwendungen beginnen, sollten Sie sich mit den Grundlagen der entwicklung Babylon.js machen.<br/><br/>– Erfahren Sie, wie Sie 3D-Anwendungen mit babylon.js [Erste Schritte erstellen.](https://doc.babylonjs.com/start)<br/>– Play with 3D examples and their source code using babylon.js [Playground](https://doc.babylonjs.com/examples/)<br/>– Tiefere Einblicke in [WebXR](https://doc.babylonjs.com/divingDeeper/webXR)<br/>– Informationen zu den ersten Schritte mit unseren Tutorials [Erstellen Ihrer ersten "Hallo Welt!"-App](tutorials/babylonjs-webxr-helloworld/introduction-01.md)|![Js-Logo](images/babylon.js.example.png) |
|[**A-Frame**](https://aframe.io/) <br/><br/>A-frame ist ein deklaratives JavaScript-Framework für die ersten Schritte mit Virtual Reality im Web. Weitere Informationen finden Sie in der [A-Frame-Dokumentation.](https://aframe.io/docs/1.2.0/introduction/) |![A-Frame](images/a-frame.example.png)  |
|[**Three.js**](https://threejs.org) <br/><br/>Three.js ist eine beliebte 3D-Bibliothek zum Erstellen von immersiven Umgebungen. Weitere Informationen [ zu ](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene)three.jsfinden Sie auf der Dokumentationsseite und in den [Beispielen](https://threejs.org/examples/#webgl_animation_cloth). |![Three.js](images/three.js.example.png)  |
|[**WebGL**](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)  <br/><br/>Sie können direkt über WebGL-APIs auf die WebXR-Geräte-APIs zugreifen. WebGL (Web Graphics Library) ist eine JavaScript-API zum Rendern leistungsstarker interaktiver 3D- und 2D-Grafiken in jedem kompatiblen Webbrowser ohne Verwendung von Plug-Ins. |![WebGL](images/webgl.example.png)  |

## <a name="see-also"></a>Weitere Informationen

* [Übersicht über WebXR](webxr-overview.md)
* [WebXR-Geräte-API-Spezifikation](https://immersive-web.github.io/webxr/)
* [Dokumentation zur WebXR-Geräte-API](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [WebXR-Beispiele](https://immersive-web.github.io/webxr-samples/)
* [Immersiveweb.dev](https://immersiveweb.dev/)
* [Verwenden Babylon.js zum Erstellen von WebXR-Erfahrungen](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [WebGL-API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))
* [Gamepad-API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) und [Gamepad-Erweiterungen](https://w3c.github.io/gamepad/extensions.html)
* [Windows Mixed Reality und die neue Microsoft Edge](../../whats-new/new-microsoft-edge.md)
* [Behandeln von verloren gegangenen Kontexten in WebGL](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [Pointerlock](https://www.w3.org/TR/pointerlock/)
* [glTF](https://www.khronos.org/gltf)
* [Immersive Web-Communitygruppe](https://www.w3.org/community/immersive-web/)
* [Immersive Web W3C Github](https://github.com/immersive-web)