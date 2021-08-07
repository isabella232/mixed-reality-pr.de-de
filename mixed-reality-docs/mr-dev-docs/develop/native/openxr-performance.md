---
title: OpenXR – Leistung
description: Erfahren Sie, wie Sie die GPU-Leistung Ihrer OpenXR Mixed Reality-Anwendungen debuggen.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Pieronos, BasicXRApp, DirectX, native, native App, benutzerdefinierte Engine, Middleware, Leistung, Optimierung, GPU-Debuggen, RenderDoc, PIX
ms.openlocfilehash: f4462da954a3b6093e47f03e75b460671e7638f406b761ad6e05689ab97b3ddc
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213174"
---
# <a name="openxr-performance"></a>OpenXR – Leistung

Auf HoloLens 2 gibt es eine Reihe von Möglichkeiten, Kompositionsdaten über zu übermitteln, was zu nach der Verarbeitung und zu spürbaren Leistungsvergefässen `xrEndFrame` führen kann.

Um eine schlechte Leistung zu vermeiden, [übermitteln Sie eine einzelne `XrCompositionProjectionLayer` ](openxr-best-practices.md#use-a-single-projection-layer) mit den folgenden Merkmalen:

* [Verwenden einer Texturarray-Swapchain](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [Verwenden des Primären Farbtauschbundformats](openxr-best-practices.md#select-a-swapchain-format)
* [Verwenden der empfohlenen Ansichtsdimensionen](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* Legen Sie das Flag nicht `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` fest.
* Legen Sie `XrCompositionLayerDepthInfoKHR` `minDepth` auf 0,0f und `maxDepth` 1,0f fest.

Um eine bessere Leistung zu erzielen, sollten Sie Folgendes in Betracht ziehen:

* [Verwenden des 16-Bit-Tiefenformats](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [Erstellen von Instanz-Zeichnen-Aufrufen](openxr-best-practices.md#render-with-texture-array-and-vprt)
