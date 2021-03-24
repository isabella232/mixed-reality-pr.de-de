---
title: ScreenshotUtility
description: Dokumentation zur Verwendungsweise des Screenshot-Tools in MRTKL
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 2f5110e0ad4cbad42dcbfef93a21dc34644bfe8d
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2021
ms.locfileid: "104694667"
---
# <a name="screenshot-utility"></a><span data-ttu-id="1a9cf-104">Screenshot-Hilfsprogramm</span><span class="sxs-lookup"><span data-stu-id="1a9cf-104">Screenshot utility</span></span>

<span data-ttu-id="1a9cf-105">Häufig gestaltet sich das Erstellen von Screenshots in Unity zu Dokumentationszwecken und für Werbebilder als mühsam, und das Ergebnis sieht häufig weniger wünschenswert aus.</span><span class="sxs-lookup"><span data-stu-id="1a9cf-105">Often taking screenshots in Unity for documentation and promotional imagery can be burdensome and the output often looks less than desirable.</span></span> <span data-ttu-id="1a9cf-106">An dieser Stelle kommt die `ScreenshotUtility`-Klasse (xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.ScreenshotUtility) ins Spiel.</span><span class="sxs-lookup"><span data-stu-id="1a9cf-106">This is where the `ScreenshotUtility` (xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.ScreenshotUtility) class comes into play.</span></span>

<span data-ttu-id="1a9cf-107">Die ScreenshotUtility-Klasse hilft beim Erstellen von Screenshots über Menüelemente und öffentliche APIs im Unity-Editor.</span><span class="sxs-lookup"><span data-stu-id="1a9cf-107">The ScreenshotUtility class aides in taking screenshots via menu items and public APIs within the Unity editor.</span></span> <span data-ttu-id="1a9cf-108">Screenshots können in verschiedenen Auflösungen aufgezeichnet werden sowie mit transparenten klaren Farben zur Verwendung bei der einfachen Nachmontage von Bildern.</span><span class="sxs-lookup"><span data-stu-id="1a9cf-108">Screenshots can be captured at various resolutions and with transparent clear colors for use in easy post compositing of images.</span></span> <span data-ttu-id="1a9cf-109">Das Erstellen von Screenshots von einem eigenständigen Build wird von diesem Tool nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="1a9cf-109">Taking screenshots from a standalone build is not supported by this tool.</span></span>

## <a name="taking-screenshots"></a><span data-ttu-id="1a9cf-110">Erstellen von Screenshots</span><span class="sxs-lookup"><span data-stu-id="1a9cf-110">Taking screenshots</span></span>

<span data-ttu-id="1a9cf-111">Screenshots lassen sich problemlos im Editor aufzeichnen, indem Sie zuerst *Mixed Reality Toolkit->Hilfsprogramme->Screenshot erstellen* auswählen und dann die gewünschte Option.</span><span class="sxs-lookup"><span data-stu-id="1a9cf-111">Screenshots can be easily capture while in the editor by selecting *Mixed Reality Toolkit->Utilities->Take Screenshot* and then selecting your desired option.</span></span> <span data-ttu-id="1a9cf-112">Stellen Sie sicher, dass die Registerkarte mit dem Spielfenster sichtbar ist, wenn Sie einen Screenshot erstellen, während Sie nicht spielen, da der Screenshot sonst möglicherweise nicht gespeichert wird.</span><span class="sxs-lookup"><span data-stu-id="1a9cf-112">Make sure to have the game window tab visible if capturing while not playing, or a screenshot may not be saved.</span></span>

<span data-ttu-id="1a9cf-113">Standardmäßig werden alle Screenshots in Ihrem [temporären Cachepfad](https://docs.unity3d.com/ScriptReference/Application-temporaryCachePath.html) gespeichert. Der Pfad zum Screenshot wird in der Unity-Konsole angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1a9cf-113">By default, all screenshots are saved to your [temporary cache path](https://docs.unity3d.com/ScriptReference/Application-temporaryCachePath.html), the path to the screenshot will be displayed in the Unity console.</span></span>

![Menüelement des Screenshot-Hilfsprogramms](../Images/ScreenshotUtility/MRTK_ScreenshotUtility_Menu_Item.png)

## <a name="example-screenshot-capture"></a><span data-ttu-id="1a9cf-115">Aufzeichnung eines Beispielscreenshots</span><span class="sxs-lookup"><span data-stu-id="1a9cf-115">Example screenshot capture</span></span>

<span data-ttu-id="1a9cf-116">Der folgende Screenshot wurde mit der Option *„4x-Auflösung (transparenter Hintergrund)“* aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="1a9cf-116">The below screenshot was captured with the *"4x Resolution (Transparent Background)"* option.</span></span> <span data-ttu-id="1a9cf-117">Dies ergibt ein Bild mit hoher Auflösung, bei dem alle Pixel, die normalerweise durch die klare Farbe dargestellt werden, als transparente Pixel gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="1a9cf-117">This outputs a high-resolution image with whatever pixels normally represented by the clear color saved as transparent pixels.</span></span> <span data-ttu-id="1a9cf-118">Diese Methode hilft Entwicklern dabei, ihre Anwendung für den Store oder andere Medien-Outlets zu präsentieren, indem andere Bilder mit diesem Bild überlagert werden.</span><span class="sxs-lookup"><span data-stu-id="1a9cf-118">This technique helps developers showcase their application for the store, or other media outlets, by overlaying this image on top of other imagery.</span></span>

![Beispiel für Aufnahme mit dem Screenshot-Hilfsprogramm](../Images/ScreenshotUtility/MRTK_ScreenshotUtility_Example_Capture.png)
