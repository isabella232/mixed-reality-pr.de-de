---
title: Screenshot-Hilfsprogramm
description: Dokumentation zur Verwendungsweise des Screenshot-Tools in MRTKL
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 59bf0df2a32030281c8bf0a1a8574b4dd9bf4607
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143791"
---
# <a name="screenshot-utility"></a>Screenshot-Hilfsprogramm

Häufig gestaltet sich das Erstellen von Screenshots in Unity zu Dokumentationszwecken und für Werbebilder als mühsam, und das Ergebnis sieht häufig weniger wünschenswert aus. An dieser Stelle kommt die `ScreenshotUtility`-Klasse (xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.ScreenshotUtility) ins Spiel.

Die ScreenshotUtility-Klasse hilft beim Erstellen von Screenshots über Menüelemente und öffentliche APIs im Unity-Editor. Screenshots können in verschiedenen Auflösungen aufgezeichnet werden sowie mit transparenten klaren Farben zur Verwendung bei der einfachen Nachmontage von Bildern. Das Erstellen von Screenshots von einem eigenständigen Build wird von diesem Tool nicht unterstützt.

## <a name="taking-screenshots"></a>Erstellen von Screenshots

Screenshots lassen sich problemlos im Editor aufzeichnen, indem Sie zuerst *Mixed Reality Toolkit->Hilfsprogramme->Screenshot erstellen* auswählen und dann die gewünschte Option. Stellen Sie sicher, dass die Registerkarte mit dem Spielfenster sichtbar ist, wenn Sie einen Screenshot erstellen, während Sie nicht spielen, da der Screenshot sonst möglicherweise nicht gespeichert wird.

Standardmäßig werden alle Screenshots in Ihrem [temporären Cachepfad](https://docs.unity3d.com/ScriptReference/Application-temporaryCachePath.html) gespeichert. Der Pfad zum Screenshot wird in der Unity-Konsole angezeigt.

![Menüelement des Screenshot-Hilfsprogramms](../images/screenshot-utility/MRTK_ScreenshotUtility_Menu_Item.png)

## <a name="example-screenshot-capture"></a>Aufzeichnung eines Beispielscreenshots

Der folgende Screenshot wurde mit der Option *„4x-Auflösung (transparenter Hintergrund)“* aufgezeichnet. Dies ergibt ein Bild mit hoher Auflösung, bei dem alle Pixel, die normalerweise durch die klare Farbe dargestellt werden, als transparente Pixel gespeichert werden. Diese Methode hilft Entwicklern dabei, ihre Anwendung für den Store oder andere Medien-Outlets zu präsentieren, indem andere Bilder mit diesem Bild überlagert werden.

![Beispiel für Aufnahme mit dem Screenshot-Hilfsprogramm](../images/screenshot-utility/MRTK_ScreenshotUtility_Example_Capture.png)
