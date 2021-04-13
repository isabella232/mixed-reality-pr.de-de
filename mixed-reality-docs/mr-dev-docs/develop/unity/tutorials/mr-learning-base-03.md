---
title: 'Tutorials zu den ersten Schritten: 3 Konfigurieren der MRTK-Profile'
description: In diesem Kurs erfahren Sie, wie Sie die MRTK-Profile (Mixed Reality Toolkit) konfigurieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, MRTK, Mixed Reality Toolkit, UWP, räumliche Wahrnehmung
ms.localizationpriority: high
ms.openlocfilehash: f6c17dc361846808ec10f1d94932e3089072e642
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300455"
---
# <a name="3-configuring-the-mrtk-profiles"></a><span data-ttu-id="36f12-105">3. Konfigurieren der MRTK-Profile</span><span class="sxs-lookup"><span data-stu-id="36f12-105">3. Configuring the MRTK profiles</span></span>

## <a name="overview"></a><span data-ttu-id="36f12-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="36f12-106">Overview</span></span>

<span data-ttu-id="36f12-107">In diesem Tutorial erfahren Sie, wie die MRTK-Profile angepasst und konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="36f12-107">In this tutorial, you will learn how to customize and configure the MRTK profiles.</span></span>

<span data-ttu-id="36f12-108">Bei den <a href="/windows/mixed-reality/mrtk-unity/features/profiles/profiles" target="_blank">MRTK-Profilen</a> handelt es sich um eine Struktur geschachtelter Profile, aus denen die Konfigurationsinformationen für die Initialisierung der MRTK-Systeme und -Funktionen bestehen.</span><span class="sxs-lookup"><span data-stu-id="36f12-108">The <a href="/windows/mixed-reality/mrtk-unity/features/profiles/profiles" target="_blank">MRTK profiles</a> is a tree of nested profiles that make up the configuration information for how the MRTK systems and features should be initialized.</span></span> <span data-ttu-id="36f12-109">Das Profil der obersten Ebene, das Konfigurationsprofil, enthält für jedes der primären Kernsysteme geschachtelte Profile.</span><span class="sxs-lookup"><span data-stu-id="36f12-109">The top-level profile, the Configuration Profile, contains nested profiles for each of the primary core systems.</span></span> <span data-ttu-id="36f12-110">Jedes geschachtelte Profil ist so konzipiert, dass das Verhalten des entsprechenden Systems konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="36f12-110">Each nested profile is designed to configure the behavior of their corresponding system.</span></span>

<span data-ttu-id="36f12-111">Dieses Beispiel veranschaulicht insbesondere, wie das Gittermodell zur räumlichen Wahrnehmung durch Ändern der Einstellungen des Betrachters für räumliche Gittermodelle ausgeblendet wird.</span><span class="sxs-lookup"><span data-stu-id="36f12-111">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="36f12-112">Jedoch können Sie dieselben Prinzipien befolgen, um beliebige Einstellungen oder Werte in den MRTK-Profilen anzupassen.</span><span class="sxs-lookup"><span data-stu-id="36f12-112">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

<span data-ttu-id="36f12-113">Wie Sie bei der Bereitstellung Ihres Projekts in Ihrer HoloLens 2 während des [vorherigen Tutorials](mr-learning-base-02.md#congratulations) gesehen haben, ist das <a href="/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started" target="_blank">Spatial Awareness</a>-Gittermodell (für räumliche Wahrnehmung) eine Sammlung von Gittermodellen, die die Geometrie der Umgebung darstellen.</span><span class="sxs-lookup"><span data-stu-id="36f12-113">As you experienced when you deployed your project to your HoloLens 2 during the [previous tutorial](mr-learning-base-02.md#congratulations), the <a href="/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started" target="_blank">Spatial Awareness</a> mesh is a collection of meshes representing the geometry of the environment.</span></span> <span data-ttu-id="36f12-114">Es ist eine hilfreiche Visualisierung für die anfängliche Anzeige, die jedoch in der Regel deaktiviert ist, um die visuelle Ablenkung und die zusätzliche Leistungseinbuße durch die Aktivierung zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="36f12-114">It's a helpful visualization to see initially but it's typically turned off to avoid the visual distraction and the additional performance hit of having it on.</span></span>

## <a name="objectives"></a><span data-ttu-id="36f12-115">Ziele</span><span class="sxs-lookup"><span data-stu-id="36f12-115">Objectives</span></span>

* <span data-ttu-id="36f12-116">Erfahren, wie MRTK-Profile angepasst und konfiguriert werden</span><span class="sxs-lookup"><span data-stu-id="36f12-116">Learn how to customize and configure MRTK profiles</span></span>
* <span data-ttu-id="36f12-117">Ausblenden des Gittermodells für räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="36f12-117">Hide the spatial awareness mesh</span></span>

## <a name="changing-the-spatial-awareness-display-option"></a><span data-ttu-id="36f12-118">Ändern der Anzeigeoptionen für räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="36f12-118">Changing the Spatial Awareness Display Option</span></span>

<span data-ttu-id="36f12-119">Dies sind die wichtigsten Schritte, die Sie ausführen, um das Gittermodell zur räumlichen Wahrnehmung auszublenden:</span><span class="sxs-lookup"><span data-stu-id="36f12-119">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="36f12-120">Klonen des Standardkonfigurationsprofils</span><span class="sxs-lookup"><span data-stu-id="36f12-120">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="36f12-121">Aktivieren des Systems für räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="36f12-121">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="36f12-122">Klonen des Standardprofils des Systems für räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="36f12-122">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="36f12-123">Klonen des Standardprofils des Betrachters für räumliche Gittermodelle</span><span class="sxs-lookup"><span data-stu-id="36f12-123">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="36f12-124">Ändern der Sichtbarkeit des Gittermodells zur räumlichen Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="36f12-124">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="36f12-125">Standardmäßig können die MRTK-Profile nicht bearbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="36f12-125">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="36f12-126">Es handelt sich um Standardprofilvorlagen, die Sie zuerst klonen müssen, um sie bearbeiten zu können.</span><span class="sxs-lookup"><span data-stu-id="36f12-126">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="36f12-127">Es gibt mehrere verschachtelte Profilebenen.</span><span class="sxs-lookup"><span data-stu-id="36f12-127">There are several nested layers of profiles.</span></span> <span data-ttu-id="36f12-128">Es ist daher gängige Praxis, mehrere Profile zu klonen und zu bearbeiten, wenn Einstellungen konfiguriert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="36f12-128">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

[!INCLUDE[](includes/configuring-profile.md)]

## <a name="congratulations"></a><span data-ttu-id="36f12-129">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="36f12-129">Congratulations</span></span>

<span data-ttu-id="36f12-130">In diesem Tutorial haben Sie gelernt, wie Sie MRTK-Profile und Einstellungen klonen, anpassen und konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="36f12-130">In this tutorial, you learned how to clone, customize, and configure MRTK profiles and settings.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="36f12-131">Nächstes Tutorial: 4. Positionieren von Objekten in der Szene</span><span class="sxs-lookup"><span data-stu-id="36f12-131">Next Tutorial: 4. Positioning objects in the scene</span></span>](mr-learning-base-04.md)