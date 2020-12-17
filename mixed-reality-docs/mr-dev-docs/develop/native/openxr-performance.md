---
title: OpenXR – Leistung
description: Debuggen Sie die GPU-Leistung Ihrer openxr-Anwendungen.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: Openxr, Khronos, basicxrapp, DirectX, Native, Native APP, benutzerdefiniertes Modul, Middleware, Leistung, Optimierung, GPU-Debugging, renderdoc, pix
ms.openlocfilehash: 7199b29067094d402348f00a9d26b93cf7e5393e
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613174"
---
# <a name="openxr-performance"></a>OpenXR – Leistung

Auf hololens 2 gibt es eine Reihe von Möglichkeiten, Kompositions Daten über zu übermitteln `xrEndFrame` , was zu einer Nachbearbeitung und spürbaren Leistungseinbußen führen kann.
Um eine schlechte Leistung zu vermeiden, [senden `XrCompositionProjectionLayer` Sie eine einzelne](openxr-best-practices.md#use-a-single-projection-layer) mit den folgenden Merkmalen:
* [Verwenden eines Textur Arrays vorhandenes SwapChain](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [Verwenden des Haupt Farb-vorhandenes SwapChain-Formats](openxr-best-practices.md#select-a-swapchain-format)
* [Empfohlene Anzeige Dimensionen verwenden](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* Legen Sie das Flag nicht fest. `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT`
* Legen `XrCompositionLayerDepthInfoKHR` `minDepth` Sie auf 0,0 f und `maxDepth` auf 1.0 f fest.

Für eine bessere Leistung sollten Sie Folgendes beachten:
* [Verwenden des 16-Bit-Tiefen Formats](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [Erstellen von instanziierten zeichnen-aufrufen](openxr-best-practices.md#render-with-texture-array-and-vprt)
