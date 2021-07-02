---
title: Hand-Joint-Verfolger
description: Hand-Joint-Verfolger in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 0beac2dae5aa12cf07f193dab9a6db7bc7ddf2e5
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175360"
---
# <a name="hand-joint-chaser"></a><span data-ttu-id="cbfff-104">Hand-Joint-Verfolger</span><span class="sxs-lookup"><span data-stu-id="cbfff-104">Hand joint chaser</span></span>

<span data-ttu-id="cbfff-105">![Hand-Joint-Verfolger In dieser Beispielszene wird veranschaulicht, wie Sie Solver verwenden, um Objekte ](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) an die Handgelenke zu anfügen.</span><span class="sxs-lookup"><span data-stu-id="cbfff-105">![Hand joint chasers](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) This example scene demonstrates how to use Solver to attach objects to the hand joints.</span></span>

## <a name="example-scene"></a><span data-ttu-id="cbfff-106">Beispielszene</span><span class="sxs-lookup"><span data-stu-id="cbfff-106">Example scene</span></span>

<span data-ttu-id="cbfff-107">Sie finden die Beispielszene **HandJointChaserExample-Szene** im `Assets/MRTK/Examples` Ordner unter `Demos/Input/Scenes/` .</span><span class="sxs-lookup"><span data-stu-id="cbfff-107">You can find the example scene **HandJointChaserExample** scene in the `Assets/MRTK/Examples` folder under `Demos/Input/Scenes/`.</span></span>

## <a name="solver-handler"></a><span data-ttu-id="cbfff-108">Solverhandler</span><span class="sxs-lookup"><span data-stu-id="cbfff-108">Solver handler</span></span>

<span data-ttu-id="cbfff-109">Klicken Sie **auf Nachverfolgte Objekte, auf die verwiesen werden soll,** und wählen Sie **Hand joint left oder** Hand Joint Right **aus.**</span><span class="sxs-lookup"><span data-stu-id="cbfff-109">Click **Tracked Object To Reference** and select **Hand Joint Left** or **Hand Joint Right**.</span></span> <span data-ttu-id="cbfff-110">Die Dropdownliste **Tracked Hand Joint (Tracked Hand Joint) wird** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="cbfff-110">You will be able to see **Tracked Hand Joint** drop down.</span></span> <span data-ttu-id="cbfff-111">In der Dropdownliste können Sie ein bestimmtes nachverfolgungsspezifisches Joint auswählen. In dieser Beispielszene wird der Radial View Solver verwendet, damit ein Objekt dem Zielobjekt folgt.</span><span class="sxs-lookup"><span data-stu-id="cbfff-111">From the drop down list, you can select specific joint to track. This example scene uses Radial View Solver to make an object follow the target object.</span></span> <span data-ttu-id="cbfff-112">Weitere Informationen finden Sie auf der Seite [Solver.](../ux-building-blocks/solvers/solver.md)</span><span class="sxs-lookup"><span data-stu-id="cbfff-112">See [Solver](../ux-building-blocks/solvers/solver.md) page for more details.</span></span>

![Hand-Fugen-Solver](../images/hand-joint-chaser/MRTK_Solver_HandJoint.jpg)
