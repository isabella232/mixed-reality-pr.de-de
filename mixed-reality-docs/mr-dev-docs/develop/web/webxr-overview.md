---
title: Verwenden von webxr mit Windows Mixed Reality
description: Erlernen Sie die Grundlagen der Verwendung und Entwicklung für webxr-Anwendungen, die auf Windows Mixed Reality-immersiven Headsets ausgeführt werden.
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: Webxr, winmr, webar, webvr, windowsmixedreality, hololens, Windows Mixed Reality, Web VR, Web XR, Web Mr, Web AR, 360, 360 Video, 360 Videos, 360 Photo, 360 Fotos, 360 Content, immersives Web, immersiveweb, IW
ms.openlocfilehash: 99cf5cf151c41252e43c6051c0d6281d33fe695a
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582905"
---
# <a name="webxr-overview"></a>Übersicht über webxr

## <a name="what-is-webxr"></a>Was ist webxr?

Die **webxr-Geräte-API** ist für den Zugriff auf die Geräte der **virtuellen Realität (VR)** und der **erweiterten Realität (AR)** , einschließlich **Sensoren** und auf dem **Web** **eingebundenes anzeigen** . Die webxr-Geräte-API ist zurzeit auf Microsoft Edge verfügbar, und die Chrome-Version 79 und höhere Versionen unterstützen webxr als Standard. Den neuesten Browser-Support Status für webxr finden Sie unter [caniuse.com](https://caniuse.com/#search=webxr).

Erfahren Sie mehr über die [gemischte Windows-Realität und den neuen Microsoft Edge](/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)in den [Neuerungen](/windows/mixed-reality/mrtk-porting-guide) .

## <a name="viewing-webxr"></a>Anzeigen von webxr

> [!IMPORTANT]
> Microsoft Edge (Legacy) unterstützt nur webvr, eine veraltete API, die in den aktuellen Browsern nicht verfügbar ist. Der neue Windows Server **[-Edge-Browser](../../whats-new/new-microsoft-edge.md)** unterstützt jedoch webxr und ist für die VR-Prototypen in Windows Mixed Reality verfügbar. Webvr ist nicht im neuen, auf dem Server verwendeten Edge-Browser verfügbar.
> 
> Wenn Sie noch heute eine Methode zum Prototypen von webxr auf hololens 2 suchen, informieren Sie sich in [Firefox Reality](https://mixedreality.mozilla.org/firefox-reality/).

Um zu testen, ob Ihr Browser webxr unterstützt, können Sie in Ihrem Browser zu [webxr-Beispielen](https://immersive-web.github.io/webxr-samples/) navigieren.

## <a name="see-also"></a>Weitere Informationen

* [Webxr-Geräte-API-Spezifikation](https://immersive-web.github.io/webxr/)
* [Dokumentation zur webxr-Geräte-API](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [Immersiveweb. dev](https://immersiveweb.dev/)
* [Webxr-Beispiele](https://immersive-web.github.io/webxr-samples/)
* [Windows Mixed Reality und die neue Microsoft Edge](/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [Immersives Web-W3C GitHub](https://github.com/immersive-web)
* [WebGL-API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))
* [Gamepad-API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) -und [Gamepad-Erweiterungen](https://w3c.github.io/gamepad/extensions.html)
* [Umgang mit verlorenem Kontext in WebGL](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [Pointerlock](https://www.w3.org/TR/pointerlock/)
* [glTF](https://www.khronos.org/gltf)
* [Verwenden von Babylon.js zum Erstellen von webxr-Erfahrungen](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [Immersive Web-Community-Gruppe](https://www.w3.org/community/immersive-web/)