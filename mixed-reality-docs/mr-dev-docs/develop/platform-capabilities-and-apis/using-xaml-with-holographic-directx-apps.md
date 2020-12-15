---
title: Verwenden von XAML mit holographischen DirectX-Apps
description: Erläutert die Auswirkungen des Wechsels zwischen 2D-XAML-Ansichten und immersiven Sichten in Ihrer DirectX-App sowie die effiziente Verwendung einer XAML-Ansicht und einer immersiven Ansicht.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, UWP, App-Ansichts Verwaltung, XAML, Tastatur, Exemplarische Vorgehensweise, DirectX
ms.openlocfilehash: b062efadca9ccfe2e2caeb054f662becc0807b50
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530276"
---
# <a name="using-xaml-with-holographic-directx-apps"></a>Verwenden von XAML mit holographischen DirectX-Apps

> [!NOTE]
> Dieser Artikel bezieht sich auf die älteren WinRT-APIs.  Bei neuen nativen App-Projekten wird die Verwendung der **[openxr-API](../native/openxr-getting-started.md)** empfohlen.

In diesem Thema wird erläutert, wie sich der Wechsel zwischen [2D-XAML-Ansichten und immersiven Sichten](../../design/app-views.md) in Ihrer DirectX-APP und die effiziente Verwendung einer XAML-Ansicht und der immersiven Ansicht Unternehmen.

## <a name="xaml-view-switching-overview"></a>Übersicht über das Wechseln der XAML-Ansicht

Bei hololens muss eine immersive APP, die später eine 2D-XAML-Ansicht anzeigen kann, die XAML-Ansicht zunächst initialisieren und sofort zu einer immersiven Ansicht wechseln. XAML wird geladen, bevor Ihre APP etwas Unternehmen kann, was zu einer geringen Erhöhung der Startzeit führt. XAML belegt weiterhin Speicherplatz in Ihrem App-Prozess, während er im Hintergrund bleibt. Die Menge der Startverzögerung und Speicherauslastung hängt davon ab, was Ihre APP mit XAML durchführt, bevor Sie zur systemeigenen Ansicht gewechselt wird. Wenn Sie zuerst in Ihrem XAML-Startcode mit Ausnahme des Starts der immersiven Ansicht Vorgehen, sollte die Auswirkung gering sein. Da Ihr holografisches Rendering direkt in der immersiven Ansicht erfolgt, vermeiden Sie außerdem alle XAML-bezogenen Einschränkungen für dieses Rendering.

Die Anzahl der Arbeitsspeicher Auslastung für CPU und GPU. Direct3D 11 kann den virtuellen Grafikspeicher austauschen, kann jedoch möglicherweise einige oder alle XAML-GPU-Ressourcen nicht austauschen, und es kann zu einem spürbaren Leistungseinbußen kommen. In beiden Fällen bleibt das Laden von XAML-Features, die Sie nicht benötigen, für Ihre APP mehr Platz und bietet eine bessere Benutzer Leistung.

## <a name="xaml-view-switching-workflow"></a>Workflow für die XAML-Ansichts Umstellung

Der Workflow für eine APP, die direkt von XAML in den immersiven Modus wechselt, sieht wie folgt aus:
* Die APP startet in der 2D-XAML-Ansicht.
* Die XAML-Startsequenz der APP erkennt, ob das aktuelle System Holographic-Rendering unterstützt:
* Wenn dies der Fall ist, erstellt die APP die immersive Ansicht und bringt Sie sofort in den Vordergrund. Das Laden von XAML wird für alles, was auf Windows Mixed Reality-Geräten nicht erforderlich ist, ausgelassen, einschließlich aller Renderingklassen und Laden von Assets in der XAML-Ansicht. Wenn die APP XAML für Tastatureingaben verwendet, sollte diese Eingabe Seite weiterhin erstellt werden.
* Andernfalls kann die XAML-Ansicht das Unternehmen wie gewohnt fortsetzen.

## <a name="tip-for-rendering-graphics-across-both-views"></a>Tipp zum Rendern von Grafiken in beiden Ansichten

Wenn Ihre APP eine gewisse Menge an Rendering in DirectX für die XAML-Ansicht in Windows Mixed Reality implementieren muss, besteht die beste Lösung darin, einen Renderer zu erstellen, der mit beiden Ansichten arbeiten kann. Der Renderer muss eine Instanz sein, auf die von beiden Ansichten aus zugegriffen werden kann, und es sollte zwischen 2D-und Holographic-Rendering gewechselt werden. Auf diese Weise werden GPU-Assets nur einmal geladen, wodurch Ladezeiten, Arbeitsspeicher Auswirkungen und die Menge der austauschten Ressourcen beim Wechseln von Sichten reduziert werden.
