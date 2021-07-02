---
title: Screenshot-Hilfsprogramm
description: Dokumentation zur Verwendungsweise des Screenshot-Tools in MRTKL
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 936126214f9e6d93ccbb871b9c80a2c93acf5a86
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176424"
---
# <a name="screenshot-utility"></a>Screenshot-Hilfsprogramm

Häufig gestaltet sich das Erstellen von Screenshots in Unity zu Dokumentationszwecken und für Werbebilder als mühsam, und das Ergebnis sieht häufig weniger wünschenswert aus. An dieser Stelle kommt die `ScreenshotUtility`-Klasse (xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.ScreenshotUtility) ins Spiel.

Die ScreenshotUtility-Klasse hilft beim Erstellen von Screenshots über Menüelemente und öffentliche APIs im Unity-Editor. Screenshots können in verschiedenen Auflösungen aufgezeichnet werden sowie mit transparenten klaren Farben zur Verwendung bei der einfachen Nachmontage von Bildern. Das Erstellen von Screenshots von einem eigenständigen Build wird von diesem Tool nicht unterstützt.

## <a name="taking-screenshots"></a>Erstellen von Screenshots

Screenshots können einfach im Editor erfasst werden, indem Sie **Mixed Reality** Toolkit Utilities Take Screenshot (Screenshot der  >    >  **Toolkit-Hilfsprogramme)**  >   auswählen und dann die gewünschte Option auswählen. Stellen Sie sicher, dass die Registerkarte mit dem Spielfenster sichtbar ist, wenn Sie einen Screenshot erstellen, während Sie nicht spielen, da der Screenshot sonst möglicherweise nicht gespeichert wird.

Standardmäßig werden alle Screenshots in Ihrem [temporären Cachepfad](https://docs.unity3d.com/ScriptReference/Application-temporaryCachePath.html) gespeichert. Der Pfad zum Screenshot wird in der Unity-Konsole angezeigt.

![Menüelement des Screenshot-Hilfsprogramms](../images/screenshot-utility/MRTK_ScreenshotUtility_Menu_Item.png)

## <a name="example-screenshot-capture"></a>Aufzeichnung eines Beispielscreenshots

Der folgende Screenshot wurde mit der Option *„4x-Auflösung (transparenter Hintergrund)“* aufgezeichnet. Dies ergibt ein Bild mit hoher Auflösung, bei dem alle Pixel, die normalerweise durch die klare Farbe dargestellt werden, als transparente Pixel gespeichert werden. Diese Methode hilft Entwicklern dabei, ihre Anwendung für den Store oder andere Medien-Outlets zu präsentieren, indem andere Bilder mit diesem Bild überlagert werden.

![Beispiel für Aufnahme mit dem Screenshot-Hilfsprogramm](../images/screenshot-utility/MRTK_ScreenshotUtility_Example_Capture.png)
