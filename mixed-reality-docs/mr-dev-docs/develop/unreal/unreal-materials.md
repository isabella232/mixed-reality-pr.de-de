---
title: Materialempfehlungen in Unreal
description: Übersicht über Materialien in der Unreal-Engine.
author: hferrone
ms.author: safarooq
ms.date: 09/18/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Entwicklung, Materialien, Dokumentation, Leitfäden, Features, Hologramme, Spieleentwicklung, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: d5ce702495c95e8ca6d07a0209a4bc7d02f5d4d682415b028d63995e8910a7e6
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187698"
---
# <a name="material-recommendations-in-unreal"></a>Materialempfehlungen in Unreal

Die materialien, die Sie verwenden, können sich direkt darauf auswirken, wie gut Ihre Projekte in der Unreal-Engine ausgeführt werden. Diese Seite dient als Schnellstart für die grundlegenden Einstellungen, die Sie verwenden sollten, um die beste Leistung Ihrer Mixed Reality-Anwendungen zu erzielen.

## <a name="using-customizeduvs"></a>Verwenden von customizedUVs

Wenn Sie UV-Kacheln für Ihr Material bereitstellen müssen, verwenden Sie CustomizedUVs, anstatt das UV des Texturknotens direkt zu ändern. Mit customizedUVs können Sie UVs in den Vertex-Shadern und nicht im Pixel-Shader bearbeiten.

![Materialeinstellungen in Unreal](images/unreal-materials-img-01c.png)

Ausführliche Informationen finden Sie in der [Unreal Engine-Dokumentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html) und beispiele für bewährte Methoden in den folgenden Screenshots:

[ ![ Empfohlene Materialeinstellungen in ](images/unreal-materials-img-01.png) Unreal ](images/unreal-materials-img-01.png#lightbox) 
 *– Setup empfohlener Materialien*

[ ![ Nicht empfohlene Materialeinstellungen ](images/unreal-materials-img-01b.png) in Unreal– ](images/unreal-materials-img-01b.png#lightbox) 
 *Nicht empfohlene Materialeinrichtung*

## <a name="changing-blend-mode"></a>Ändern des Blend-Modus

Es wird empfohlen, den Blend-Modus auf nicht transparent festzulegen, es sei denn, es gibt einen starken Grund, dies andernfalls zu tun. Maskierte und transluzente Materialien sind langsam. Weitere Informationen zu Materialien finden Sie in der [Unreal Engine-Dokumentation.](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)

![Ändern des Blendmodus](images/unreal-materials-img-02.jpg)

## <a name="updating-lighting-for-mobile"></a>Aktualisieren der Beleuchtung für Mobilgeräte

Die vollständige Genauigkeit sollte deaktiviert werden. Die Beleuchtung von Lightmaps kann durch Drehen von Richtungsinformationen heruntergewählt werden. Wenn diese Option deaktiviert ist, ist die Beleuchtung von Lightmaps flach, aber kostengünstiger.

![Einstellungen für mobiles Material in Unreal](images/unreal-materials-img-03.jpg)

## <a name="adjusting-forward-shading"></a>Anpassen der Vorwärtsschattierung

Diese Optionen verbessern die Visuelle Genauigkeit auf Kosten der Leistung. Sie sollten für maximale Leistung deaktiviert werden.

![Einstellungen für Das Schattierungsmaterial in Unreal weiterleiten](images/unreal-materials-img-04.jpg)

## <a name="setting-material-translucency"></a>Festlegen der Materialtransluzenz

Gibt an, dass das durchscheinende Material nicht von Derb oder DOF beeinflusst werden soll. Da beide Auswirkungen im MR selten sind, sollte diese Einstellung standardmäßig aktiviert sein.

![Mobile separate Transparenzeinstellung in Unreal](images/unreal-materials-img-05.jpg)

## <a name="optional-settings"></a>Optionale Einstellungen

Die folgenden Einstellungen können die Leistung verbessern, aber beachten Sie, dass sie bestimmte Features deaktivieren. Verwenden Sie diese Einstellungen nur, wenn Sie sicher sind, dass Sie die betreffenden Features nicht benötigen.

![Optionale Materialeinstellungen in Unreal](images/unreal-materials-img-06.jpg)

Wenn Ihr Material keine Reflektionen oder Leuchtmittel erfordert, kann das Festlegen dieser Option eine enorme Leistungssteigerung bieten. Bei internen Tests ist es so schnell wie "unbelichtet", während Beleuchtungsinformationen zur Verfügung stehen.

## <a name="best-practices"></a>Bewährte Methoden

Im Folgenden sind nicht so viele "Einstellungen" enthalten wie bewährte Methoden im Zusammenhang mit Materialien.

Beim Erstellen von Parametern sollten Sie nach Möglichkeit "Statische Parameter" verwenden. Statische Switches können verwendet werden, um eine gesamte Verzweigung eines Materials ohne Laufzeitkosten zu entfernen. Instanzen können unterschiedliche Werte aufweisen, sodass ein Shader mit Vorlagen ohne Leistungseinbußen eingerichtet werden kann. Der Nachteil besteht darin, dass mehrere Permutationen erstellt werden, die zu einer Neukompilierung des Shaders führen. Versuchen Sie, die Anzahl der statischen Parameter im Material und die Anzahl der Permutationen dieser verwendeten statischen Parameter zu minimieren. Weitere Informationen zum Rendern von Materialparametern finden Sie in der [Unreal Engine-Dokumentation.](https://docs.unrealengine.com/Engine/Rendering/Materials/ExpressionReference/Parameters/index.html#staticswitchparameter)

![Bewährte Methoden für Materialeinstellungen](images/unreal-materials-img-07.jpg)

Beim Erstellen von Material Instances sollte Material **Instance Constant** gegenüber Material Instance Dynamic bevorzugt werden. **Material Instance Constant** ist ein instanziertes Material, das vor der Laufzeit nur einmal berechnet wird.

Die über den Inhaltsbrowser erstellte Materialinstanz (**Rechtsklick > Materialinstanz erstellen)** ist eine Material Instance-Konstante. Material Instance Dynamic wird über Code erstellt. Weitere Informationen zu materialen Instanzen finden Sie in der [Unreal Engine-Dokumentation.](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html)

![Erstellen von Materialinstanzen in Unreal](images/unreal-materials-img-08.png)

Behalten Sie die Komplexität Ihrer Materialien/Shader im Auge. Sie können die Kosten für Ihr Material auf verschiedenen Plattformen anzeigen, indem Sie auf das Symbol Plattformstatistik klicken. Weitere Informationen zu Materialien finden Sie auch in der [Unreal Engine-Dokumentation.](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)

![Erstellen dynamischer Einstellungen für Materialinstanzen in Unreal](images/unreal-materials-img-09.png)

Sie können sich einen schnellen Überblick über die relative Komplexität [](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)Ihres Shaders über den Shader-Komplexitätsansichtsmodus verschaffen.

* Hotkey im Ansichtsmodus: ALT + 8
* Konsolenbefehl: viewmode shadercomplexity

![Materialkomplexität in Unreal](images/unreal-materials-img-10.png)

## <a name="see-also"></a>Weitere Informationen
* [Mobile Materialien](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)
* [Ansichtsmodi](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)
* [Material instances (Materialinstanzen)](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html)
