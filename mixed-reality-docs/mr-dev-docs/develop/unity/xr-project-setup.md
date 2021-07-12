---
title: Einrichten ihrer XR-Konfiguration
description: Bleiben Sie über die neuesten Unity XR-Konfigurationsempfehlungen für HoloLens Anwendungsentwicklung auf dem Laufenden.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Unity
ms.openlocfilehash: d2904b9ea4771286b7091a8d5b7c599fcbd1244a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603715"
---
# <a name="setting-up-your-xr-configuration"></a><span data-ttu-id="7cdce-104">Einrichten ihrer XR-Konfiguration</span><span class="sxs-lookup"><span data-stu-id="7cdce-104">Setting up your XR configuration</span></span>

<span data-ttu-id="7cdce-105">Nachdem Sie [eine Unity-Version ausgewählt](choosing-unity-version.md)haben, besteht der nächste Schritt darin, die XR-Konfiguration auszuwählen, die Sie zum Erstellen Ihrer Mixed Reality-App verwenden:</span><span class="sxs-lookup"><span data-stu-id="7cdce-105">Once you've [chosen a Unity version](choosing-unity-version.md), the next step is to select the XR configuration you'll use to build your mixed reality app:</span></span>

## <a name="choosing-an-xr-configuration"></a><span data-ttu-id="7cdce-106">Auswählen einer XR-Konfiguration</span><span class="sxs-lookup"><span data-stu-id="7cdce-106">Choosing an XR configuration</span></span>

<span data-ttu-id="7cdce-107">Wenn Sie ein neues Unity-Projekt starten, verfügen Sie über verschiedene XR-Konfigurationen, die Sie auswählen können: das **Mixed Reality OpenXR-Plug-In,** das **Windows XR-Plug-In** und **legacy built-in XR**.</span><span class="sxs-lookup"><span data-stu-id="7cdce-107">When you start a new Unity project, you have various XR configurations you can select from: the **Mixed Reality OpenXR plugin**, the **Windows XR plugin** and **Legacy Built-in XR**.</span></span>

[!INCLUDE[](includes/xr/intro.md)]

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="7cdce-108">Einrichten Ihres Projekts mit MRTK</span><span class="sxs-lookup"><span data-stu-id="7cdce-108">Setting up your project with MRTK</span></span>

<span data-ttu-id="7cdce-109">Die einfachste Möglichkeit, Ihr Unity-Projekt für Mixed Reality einzurichten, ist das Mixed Reality Toolkit (MRTK).</span><span class="sxs-lookup"><span data-stu-id="7cdce-109">The easiest way to get your Unity project set up for mixed reality is with the Mixed Reality Toolkit (MRTK).</span></span>  <span data-ttu-id="7cdce-110">MRTK für Unity ist ein plattformübergreifendes Open-Source-Development Kit, das die Erstellung beeindruckender Mixed Reality-Anwendungen erleichtert.</span><span class="sxs-lookup"><span data-stu-id="7cdce-110">MRTK for Unity is an open-source, cross-platform development kit designed to make it easy to build amazing mixed reality applications.</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="7cdce-112">MRTK bietet ein plattformübergreifendes Eingabesystem, Grundlagenkomponenten und gemeinsame Bausteine für räumliche Interaktionen.</span><span class="sxs-lookup"><span data-stu-id="7cdce-112">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span>  <span data-ttu-id="7cdce-113">Mit MRTK Version 2 können Sie ihre Anwendungsentwicklung für Microsoft HoloLens, Windows Mixed Reality immersive Headsets (VR) und viele andere VR/AR-Geräte beschleunigen.</span><span class="sxs-lookup"><span data-stu-id="7cdce-113">With MRTK version 2, you can speed up your application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and many other VR/AR devices.</span></span> <span data-ttu-id="7cdce-114">Das Projekt zielt darauf ab, Einstiegsbarrieren zu verringern, sodass jeder Mixed Reality-Anwendungen erstellen und bei jedem Wachstum zur Community beitragen kann.</span><span class="sxs-lookup"><span data-stu-id="7cdce-114">The project is aimed at reducing barriers to entry, enabling everyone to build mixed reality applications and contribute back to the community as we all grow.</span></span>

[!INCLUDE[](includes/xr/mrtk-next-step.md)]

<span data-ttu-id="7cdce-115">Weitere Informationen zum Mixed Reality Toolkit finden Sie in der [MRTK-Dokumentation.](/windows/mixed-reality/mrtk-unity)</span><span class="sxs-lookup"><span data-stu-id="7cdce-115">To learn more about the Mixed Reality Toolkit, check out the [MRTK documentation](/windows/mixed-reality/mrtk-unity).</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="7cdce-116">Manuelle Einrichtung ohne MRTK</span><span class="sxs-lookup"><span data-stu-id="7cdce-116">Manual setup without MRTK</span></span>

<span data-ttu-id="7cdce-117">Während Microsoft und die Community Open Source-Tools wie das [Mixed Reality Toolkit (MRTK)](/windows/mixed-reality/mrtk-unity) erstellt haben, mit denen Ihre Umgebung automatisch für Mixed Reality eingerichtet wird, möchten einige Entwickler ihre Erfahrungen möglicherweise von Grund auf erstellen.</span><span class="sxs-lookup"><span data-stu-id="7cdce-117">While Microsoft and the community have created open source tools such as the [Mixed Reality Toolkit (MRTK)](/windows/mixed-reality/mrtk-unity) that will automatically set up your environment for mixed reality, some developers may wish to build their experiences from the ground up.</span></span>

[!INCLUDE[](includes/xr/manual-setup.md)]