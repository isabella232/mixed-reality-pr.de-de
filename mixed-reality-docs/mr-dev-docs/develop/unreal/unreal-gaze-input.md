---
title: Blick Eingabe in Unreal
description: Tutorial zum Einrichten von Blick Eingaben für hololens und Unreal Engine
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, holograms, hololens 2, Eye Tracking, Blick Eingaben, Head-eingebundene Anzeige, Unreal Engine, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 2ea55e3c53275f6150ca7f2def10d71634119e2e
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679049"
---
# <a name="gaze-input"></a><span data-ttu-id="d70d2-104">Blick Eingabe</span><span class="sxs-lookup"><span data-stu-id="d70d2-104">Gaze Input</span></span>

## <a name="overview"></a><span data-ttu-id="d70d2-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="d70d2-105">Overview</span></span>

<span data-ttu-id="d70d2-106">Das [Windows Mixed Reality-Plug](https://docs.unrealengine.com/Platforms/VR/WMR/index.html) -in bietet keine integrierten Funktionen für die Überblicks Eingabe, aber hololens 2 unterstützt die Eye-Nachverfolgung.</span><span class="sxs-lookup"><span data-stu-id="d70d2-106">The [Windows Mixed Reality plugin](https://docs.unrealengine.com/Platforms/VR/WMR/index.html) doesn’t provide any built-in functions for gaze input, but HoloLens 2 does support eye tracking.</span></span> <span data-ttu-id="d70d2-107">Die eigentlichen Überwachungsfunktionen werden von Unreal mit den von Unreal bereitgestellten **Anzeige** -und **Eye Tracking** -APIs bereitgestellt und umfassen Folgendes:</span><span class="sxs-lookup"><span data-stu-id="d70d2-107">The actual tracking features are provided by Unreal's **Head Mounted Display** and **Eye Tracking** APIs and include:</span></span>

- <span data-ttu-id="d70d2-108">Geräteinformationen</span><span class="sxs-lookup"><span data-stu-id="d70d2-108">Device information</span></span>
- <span data-ttu-id="d70d2-109">Nach Verfolgungs Sensoren</span><span class="sxs-lookup"><span data-stu-id="d70d2-109">Tracking sensors</span></span>
- <span data-ttu-id="d70d2-110">Ausrichtung und Position</span><span class="sxs-lookup"><span data-stu-id="d70d2-110">Orientation and position</span></span>
- <span data-ttu-id="d70d2-111">Clipping-Bereiche</span><span class="sxs-lookup"><span data-stu-id="d70d2-111">Clipping panes</span></span>
- <span data-ttu-id="d70d2-112">Daten-und Überwachungsinformationen für den Blick</span><span class="sxs-lookup"><span data-stu-id="d70d2-112">Gaze data and tracking information</span></span>

<span data-ttu-id="d70d2-113">Die vollständige Liste der Features finden Sie in [der Dokumentation zu](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) den Köpfen in der Head-bereit [Stellung](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) von Unreal.</span><span class="sxs-lookup"><span data-stu-id="d70d2-113">You can find the full list of features in Unreal's [Head Mounted Display](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) and [Eye Tracking](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) documentation.</span></span>

<span data-ttu-id="d70d2-114">Zusätzlich zu den Unreal-APIs sehen Sie sich die Dokumentation zu den [Augenblick-basierten Interaktionen](../../design/eye-gaze-interaction.md) für hololens 2 an, und informieren Sie sich darüber, wie die [Augen Verfolgung auf hololens 2](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) funktioniert.</span><span class="sxs-lookup"><span data-stu-id="d70d2-114">In addition to the Unreal APIs, check out the documentation on [eye-gaze-based interaction](../../design/eye-gaze-interaction.md) for HoloLens 2 and read up on how [eye tracking on HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) works.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d70d2-115">Die Eye-Nachverfolgung wird nur auf hololens 2 unterstützt.</span><span class="sxs-lookup"><span data-stu-id="d70d2-115">Eye tracking is only supported on HoloLens 2.</span></span>

## <a name="enabling-eye-tracking"></a><span data-ttu-id="d70d2-116">Aktivieren der Eye-Überwachung</span><span class="sxs-lookup"><span data-stu-id="d70d2-116">Enabling eye tracking</span></span>
<span data-ttu-id="d70d2-117">Die Überblicks Eingabe muss in den hololens-Projekteinstellungen aktiviert werden, bevor Sie eine der Unreal-APIs verwenden können.</span><span class="sxs-lookup"><span data-stu-id="d70d2-117">Gaze input needs to be enabled in the HoloLens project settings before you can use any of Unreal's APIs.</span></span> <span data-ttu-id="d70d2-118">Wenn die Anwendung gestartet wird, wird im folgenden Screenshot eine Zustimmungsaufforderung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d70d2-118">When the application starts you'll see a consent prompt shown in the screenshot below.</span></span>

- <span data-ttu-id="d70d2-119">Wählen Sie **Ja** aus, um die Berechtigung festzulegen, und erhalten Sie Zugriff auf die Eingaben.</span><span class="sxs-lookup"><span data-stu-id="d70d2-119">Select **Yes** to set the permission and get access to gaze input.</span></span> <span data-ttu-id="d70d2-120">Wenn Sie diese Einstellung jederzeit ändern müssen, finden Sie Sie in der App " **Einstellungen** ".</span><span class="sxs-lookup"><span data-stu-id="d70d2-120">If you need to change this setting at any time, it can be found in the **Settings** app.</span></span>

![Eye-Eingabe Berechtigungen](images/unreal/eye-input-permissions.png)

> [!NOTE] 
> <span data-ttu-id="d70d2-122">Hololens Eye Tracking in Unreal hat nur einen einzelnen Blick Strahl für beide Augen und nicht die zwei Strahlen, die für die Stereoskopie erforderlich sind, was nicht unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="d70d2-122">HoloLens eye tracking in Unreal only has a single gaze ray for both eyes instead of the two rays needed for stereoscopic tracking, which is not supported.</span></span>

<span data-ttu-id="d70d2-123">Das ist alles, was Sie tun müssen, um Ihre hololens 2-apps in Unreal mit Blick Eingaben zu versehen.</span><span class="sxs-lookup"><span data-stu-id="d70d2-123">That's all the setup you'll need to start adding gaze input to your HoloLens 2 apps in Unreal.</span></span> <span data-ttu-id="d70d2-124">Weitere Informationen zu Blick Eingaben und deren Auswirkungen auf Benutzer in gemischter Realität finden Sie unter den folgenden Links.</span><span class="sxs-lookup"><span data-stu-id="d70d2-124">More information on gaze input and how it affects users in mixed reality can be found at the links below.</span></span> <span data-ttu-id="d70d2-125">Berücksichtigen Sie diese bei der Erstellung interaktiver Umgebungen.</span><span class="sxs-lookup"><span data-stu-id="d70d2-125">Be sure to think about these when building your interactive experiences.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="d70d2-126">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="d70d2-126">Next Development Checkpoint</span></span>

<span data-ttu-id="d70d2-127">Wenn Sie dem Weg der Unreal-Entwicklungsprüfpunkte folgen, den wir entworfen haben, befinden Sie sich mitten im Kennenlernen der MRTK-Grundbausteine.</span><span class="sxs-lookup"><span data-stu-id="d70d2-127">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="d70d2-128">Von hier aus können Sie mit dem nächsten Baustein fortfahren:</span><span class="sxs-lookup"><span data-stu-id="d70d2-128">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="d70d2-129">Handtracking</span><span class="sxs-lookup"><span data-stu-id="d70d2-129">Hand tracking</span></span>](unreal-hand-tracking.md)

<span data-ttu-id="d70d2-130">Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:</span><span class="sxs-lookup"><span data-stu-id="d70d2-130">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d70d2-131">HoloLens-Kamera</span><span class="sxs-lookup"><span data-stu-id="d70d2-131">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="d70d2-132">Sie können jederzeit zu den [Prüfpunkten für die Unreal-Entwicklung](unreal-development-overview.md#2-core-building-blocks) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="d70d2-132">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="d70d2-133">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="d70d2-133">See also</span></span>
* [<span data-ttu-id="d70d2-134">Kalibrierung</span><span class="sxs-lookup"><span data-stu-id="d70d2-134">Calibration</span></span>](../../calibration.md)
* [<span data-ttu-id="d70d2-135">Komfort</span><span class="sxs-lookup"><span data-stu-id="d70d2-135">Comfort</span></span>](../../design/comfort.md)
* [<span data-ttu-id="d70d2-136">Anvisieren und Ausführen</span><span class="sxs-lookup"><span data-stu-id="d70d2-136">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="d70d2-137">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="d70d2-137">Voice input</span></span>](../../out-of-scope/voice-design.md)
