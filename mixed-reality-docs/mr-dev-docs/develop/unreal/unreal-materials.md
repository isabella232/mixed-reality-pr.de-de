---
title: Materialempfehlungen in Unreal
description: Übersicht über Materialien in der Unreal Engine.
author: hferrone
ms.author: v-hferrone
ms.date: 09/18/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, hololens, hololens 2, Entwicklung, Materialien, Dokumentation, Leitfäden, Features, holograms, Spieleentwicklung, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 11c10577bd3946facb96fd77b09265ab5ca26f24
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609571"
---
# <a name="material-recommendations-in-unreal"></a>Materialempfehlungen in Unreal

Die Materialien, die Sie verwenden, können direkt beeinflussen, wie gut Ihre Projekte in der Unreal Engine ausgeführt werden. Diese Seite fungiert als Schnellstart für die grundlegenden Einstellungen, die Sie verwenden sollten, um die optimale Leistung Ihrer gemischten Reality-Anwendungen zu erzielen.

## <a name="using-customizeduvs"></a>Verwenden von customizeduvs

Wenn Sie eine UV-tisierung für Ihr Material durchführen müssen, verwenden Sie stattdessen customizeduvs, anstatt die UV-Struktur des Textur Knotens direkt zu ändern. Mit customizeduvs können Sie benutzerdefinierte Benutzerkonten in den Vertex-Shadern und nicht im Pixelshader bearbeiten.

![Material Einstellungen in Unreal](images/unreal-materials-img-01c.png)

Material Details finden Sie in der [Unreal Engine-Dokumentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html) und in den bewährten Beispielen in den folgenden Screenshots:

[ ![ Empfohlene Material Einstellungen in der ](images/unreal-materials-img-01.png) von Unreal ](images/unreal-materials-img-01.png#lightbox) 
 *empfohlenen Material Einrichtung*

[ ![ Nicht empfohlene Material Einstellungen in Unreal ](images/unreal-materials-img-01b.png) ](images/unreal-materials-img-01b.png#lightbox) 
 *Non-Recommended Material Setup*

## <a name="changing-blend-mode"></a>Ändern des Blend-Modus

Es wird empfohlen, den Blend-Modus auf "undurchsichtig" festzulegen, es sei denn, es gibt einen starken Grund dafür Maskierte und durchlässiges Material sind langsam. Weitere Details zu den Materialien finden Sie in der [Unreal Engine-Dokumentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).

![Ändern des Blend-Modus](images/unreal-materials-img-02.jpg)

## <a name="updating-lighting-for-mobile"></a>Aktualisieren der Beleuchtung für mobile Geräte

Die vollständige Genauigkeit sollte deaktiviert werden. Lightmap-Beleuchtung kann durch das Einschalten von direktionalen Informationen abgewählt werden. Wenn diese Option deaktiviert ist, ist die Beleuchtung aus lightmaps flach, aber günstiger.

![Mobile Material Einstellungen in Unreal](images/unreal-materials-img-03.jpg)

## <a name="adjusting-forward-shading"></a>Anpassen der vorwärts Schattierung

Diese Optionen verbessern die visuelle Genauigkeit auf Kosten der Leistung. Sie sollten für maximale Leistung ausgeschaltet werden.

![Weiterleiten von Schattierungs Material-Einstellungen in Unreal](images/unreal-materials-img-04.jpg)

## <a name="setting-material-translucency"></a>Festlegen der Material Durchlässigkeit

Gibt an, dass das lichtdurchlässiges Material nicht von der Blüte oder von DOF beeinflusst werden soll. Da beide Effekte in Mr selten vorkommen, sollte diese Einstellung standardmäßig auf ON festgelegt sein.

![Einstellung "Mobile separate Transluzenz" in Unreal](images/unreal-materials-img-05.jpg)

## <a name="optional-settings"></a>Optionale Einstellungen

Die folgenden Einstellungen können die Leistung verbessern, aber beachten Sie, dass Sie bestimmte Funktionen deaktivieren. Verwenden Sie diese Einstellungen nur, wenn Sie sicher sind, dass Sie die betreffenden Features nicht benötigen.

![Optionale Material Einstellungen in Unreal](images/unreal-materials-img-06.jpg)

Wenn Ihr Material keine Reflektionen oder glänzen erfordert, kann das Festlegen dieser Option zu einer enormen Leistungssteigerung führt. Bei internen Tests ist es so schnell wie "nicht beleuchtet", während Beleuchtungs Informationen bereitgestellt werden.

## <a name="best-practices"></a>Bewährte Methoden

Die folgenden Einstellungen sind nicht "Einstellungen", wie Sie die bewährten Methoden für Materialien betreffen.

Wenn Sie Parameter erstellen, bevorzugen Sie die Verwendung von "statischen Parametern", sofern möglich. Statische Switches können verwendet werden, um einen vollständigen Branch eines Materials ohne Lauf Zeit Kosten zu entfernen. Instanzen können unterschiedliche Werte aufweisen, sodass es möglich ist, einen Vorlagen basierten Shader ohne Leistungseinbußen einzurichten. Der Nachteil ist, dass mehrere Permutationen erstellt werden, die eine erneute Shader-Kompilierung bewirken. Versuchen Sie, die Anzahl der statischen Parameter im Material und die Anzahl der Permutationen der verwendeten statischen Parameter zu minimieren. Weitere Informationen zum Rendern von Materialparametern finden Sie in der [Unreal Engine-Dokumentation](https://docs.unrealengine.com/Engine/Rendering/Materials/ExpressionReference/Parameters/index.html#staticswitchparameter).

![Bewährte Methoden für Material Einstellungen](images/unreal-materials-img-07.jpg)

Beim Erstellen von Material Instanzen sollte die-Einstellung für die **Material Instanz-Konstante** über die dynamische Material Instanz bevorzugt werden. Die **materialinstanzkonstante** ist ein instanziziertes Material, das nur einmal vor der Laufzeit berechnet.

Die über den Inhalts Browser erstellte Material Instanz (mit der **rechten Maustaste auf > Create Material instance**) ist eine Material Instanz-Konstante. Die dynamische Material Instanz wird über Code erstellt. Weitere Informationen zu Material Instanzen finden Sie in der [Unreal Engine-Dokumentation](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html).

![Erstellen von Material Instanzen in Unreal](images/unreal-materials-img-08.png)

Beobachten Sie die Komplexität ihrer Materialien/Shader. Sie können die Kosten für Ihr Material auf verschiedenen Plattformen anzeigen, indem Sie auf das Platt Form Statistik-Symbol klicken. Weitere Informationen zu Materialien finden Sie auch in der [Unreal Engine-Dokumentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).

![Erstellen von dynamischen Einstellungen für Material Instanzen in Unreal](images/unreal-materials-img-09.png)

Sie erhalten einen kurzen Überblick über die relative Komplexität Ihres Shaders über den Shader-Komplexitäts [Ansichtsmodus](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html).

* Hotkey im Ansichtsmodus: alt + 8
* Konsolen Befehl: ViewMode shaderkomplexität

![Komplexität von Material in Unreal](images/unreal-materials-img-10.png)

## <a name="see-also"></a>Weitere Informationen
* [Mobile Materialien](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)
* [Ansichtsmodi](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)
* [Material Instanzen](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html)
