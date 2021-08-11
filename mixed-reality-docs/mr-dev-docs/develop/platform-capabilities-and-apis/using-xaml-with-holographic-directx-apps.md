---
title: Verwenden von XAML mit holographischen DirectX-Apps
description: Erläutert die Auswirkungen des Wechsels zwischen 2D-XAML-Ansichten und immersiven Ansichten in Ihrer DirectX-App sowie die effiziente Verwendung einer XAML-Ansicht und einer immersiven Ansicht.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, UWP, App-Ansichtsverwaltung, XAML, Tastatur, exemplarische Vorgehensweise, DirectX
ms.openlocfilehash: 3c7edfdf4ff2ed629699dca0514efabc9ce7241cb1781e4b9c914ad4bff1f900
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220946"
---
# <a name="using-xaml-with-holographic-directx-apps"></a>Verwenden von XAML mit holographischen DirectX-Apps

> [!NOTE]
> Dieser Artikel bezieht sich auf die nativen WinRT-Legacy-APIs.  Für neue native App-Projekte wird die Verwendung der **[OpenXR-API](../native/openxr-getting-started.md)** empfohlen.

In diesem Thema werden die Auswirkungen des Wechsels zwischen [2D-XAML-Ansichten und immersiven Ansichten](../../design/app-views.md) in Ihrer DirectX-App sowie die effiziente Verwendung einer XAML-Ansicht und einer immersiven Ansicht erläutert.

## <a name="xaml-view-switching-overview"></a>Übersicht über den Wechsel der XAML-Ansicht

Auf HoloLens muss eine immersive App, die später eine 2D-XAML-Ansicht anzeigen kann, diese XAML-Ansicht zuerst initialisieren und sofort von dort aus zu einer immersiven Ansicht wechseln. XAML wird geladen, bevor Ihre App etwas tun kann, wodurch sich die Startzeit geringfügig erhöht. XAML belegt weiterhin Speicherplatz in Ihrem App-Prozess, während es im Hintergrund bleibt. Die Menge der Startverzögerung und Speicherauslastung hängt davon ab, wie Ihre App mit XAML vor dem Wechsel zur nativen Ansicht vorgeht. Wenn Sie im XAML-Startcode zunächst nichts tun, außer die immersive Ansicht zu starten, sollten die Auswirkungen geringfügig sein. Da Ihr holografisches Rendering direkt in der immersiven Ansicht erfolgt, vermeiden Sie außerdem XAML-bezogene Einschränkungen für dieses Rendering.

Die Anzahl der Arbeitsspeicherauslastungen für CPU und GPU. Direct3D 11 kann den virtuellen Grafikspeicher austauschen, aber möglicherweise können einige oder alle XAML-GPU-Ressourcen nicht ausgetauscht werden, und es kann zu einer spürbaren Leistungssteigerung kommen. In beiden Fällen lässt das Laden von XAML-Features, die Sie nicht benötigen, mehr Platz für Ihre App und bietet eine bessere Benutzererfahrung.

## <a name="xaml-view-switching-workflow"></a>Workflow zum Wechseln der XAML-Ansicht

Der Workflow für eine App, die direkt von XAML in den immersiven Modus wechselt, sieht wie folgt aus:
* Die App wird in der 2D-XAML-Ansicht gestartet.
* Die XAML-Startsequenz der App erkennt, ob das aktuelle System holografisches Rendering unterstützt:
* Wenn ja, erstellt die App die immersive Ansicht und versetzt sie sofort in den Vordergrund. XAML-Ladevorgänge werden für alles übersprungen, was auf Windows Mixed Reality Geräten nicht erforderlich ist, einschließlich Renderingklassen und Laden von Medienobjekten in der XAML-Ansicht. Wenn die App XAML für Tastatureingaben verwendet, sollte diese Eingabeseite weiterhin erstellt werden.
* Falls nicht, kann die XAML-Ansicht wie gewohnt fortgesetzt werden.

## <a name="tip-for-rendering-graphics-across-both-views"></a>Tipp zum Rendern von Grafiken in beiden Ansichten

Wenn Ihre App ein gewisses Maß an Rendering in DirectX für die XAML-Ansicht in Windows Mixed Reality implementieren muss, ist es am besten, einen Renderer zu erstellen, der mit beiden Ansichten arbeiten kann. Der Renderer sollte eine Instanz sein, auf die von beiden Ansichten aus zugegriffen werden kann, und er sollte zwischen 2D- und holografischem Rendering wechseln. Auf diese Weise werden GPU-Ressourcen nur einmal geladen, wodurch ladezeiten, Arbeitsspeicherauswirkungen und die Menge der ausgetauschten Ressourcen beim Wechseln von Ansichten reduziert werden.
