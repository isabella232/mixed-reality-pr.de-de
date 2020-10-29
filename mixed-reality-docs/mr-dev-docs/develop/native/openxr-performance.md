---
title: OpenXR – Leistung
description: Debuggen Sie die GPU-Leistung Ihrer openxr-Anwendungen.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: Openxr, Khronos, basicxrapp, DirectX, Native, Native APP, benutzerdefiniertes Modul, Middleware, Leistung, Optimierung, GPU-Debugging, renderdoc, pix
ms.openlocfilehash: 717dc2d534773bd28f5ad2d5c3720bf4177a1480
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2020
ms.locfileid: "91683830"
---
# <a name="openxr-performance"></a>OpenXR – Leistung

Auf hololens 2 gibt es eine Reihe von Möglichkeiten, Kompositions Daten übermitteln zu können `xrEndFrame` . Dies führt zu einer Nachbearbeitung, bei der eine spürbare Leistungs Einbuße vorliegt.
Um Leistungsdaten zu vermeiden, [Senden Sie eine `XrCompositionProjectionLayer` einzelne](openxr-best-practices.md#use-a-single-projection-layer) mit den folgenden Merkmalen:
* [Verwenden eines Textur Arrays vorhandenes SwapChain](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [Verwenden des Haupt Farb-vorhandenes SwapChain-Formats](openxr-best-practices.md#select-a-swapchain-format)
* [Empfohlene Anzeige Dimensionen verwenden](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* Flag nicht festlegen `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT`
* Legen `XrCompositionLayerDepthInfoKHR` `minDepth` Sie auf 0,0 f und `maxDepth` auf 1.0 f fest.

Weitere Überlegungen führen zu einer besseren Leistung:
* [Verwenden des 16-Bit-Tiefen Formats](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [Erstellen von instanziierten zeichnen-aufrufen](openxr-best-practices.md#render-with-texture-array-and-vprt)
