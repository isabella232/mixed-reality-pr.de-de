---
title: Einrichten Ihres Unreal-Projekts
description: Erfahren Sie, wie Sie Ihr Projekt mit der neuesten Version der Unreal-Engine und dem Mixed Reality-Featuretool einrichten.
author: hferrone
ms.author: v-hferrone
ms.date: 4/28/2021
ms.topic: tutorial
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, Mixed Reality, Entwicklung, Features, neues Projekt, Emulator, Dokumentation, Leitfäden, Hologramme, Spieleentwicklung, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 8201e97ed35d11404928c1dfe94ad9b7e626e51b
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394613"
---
# <a name="setting-up-your-unreal-project"></a><span data-ttu-id="13c14-104">Einrichten Ihres Unreal-Projekts</span><span class="sxs-lookup"><span data-stu-id="13c14-104">Setting up your Unreal project</span></span>

<span data-ttu-id="13c14-105">Es wird empfohlen, die [Unreal-Engine, Version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) oder höher, zu installieren, um die integrierte Unterstützung von HoloLens in vollem Umfang nutzen zu können.</span><span class="sxs-lookup"><span data-stu-id="13c14-105">We recommend installing [Unreal Engine version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) or later to take full advantage of built-in HoloLens support.</span></span>

<span data-ttu-id="13c14-106">Wechseln Sie im Epic Games-Startprogramm zur Registerkarte **Bibliothek**, klicken Sie neben **Starten** auf den Dropdownpfeil und dann auf **Optionen**.</span><span class="sxs-lookup"><span data-stu-id="13c14-106">Go to the **Library** tab in the Epic Games Launcher, select the dropdown arrow next to **Launch** and click **Options**.</span></span> <span data-ttu-id="13c14-107">Wählen Sie unter **Target Platforms** (Zielplattformen) **HoloLens 2** aus, und klicken Sie auf **Apply** (Übernehmen).</span><span class="sxs-lookup"><span data-stu-id="13c14-107">Under **Target Platforms**, select **HoloLens 2** and click **Apply**.</span></span>
<span data-ttu-id="13c14-108">![HoloLens 2-Installationsoption für Unreal](../images/Unreal_Install_Option_HoloLens2.png)</span><span class="sxs-lookup"><span data-stu-id="13c14-108">![Unreal Install Option HoloLens 2](../images/Unreal_Install_Option_HoloLens2.png)</span></span>

## <a name="import-mixed-reality-toolkit-for-unreal"></a><span data-ttu-id="13c14-109">Importieren des Mixed Reality-Toolkits für Unreal</span><span class="sxs-lookup"><span data-stu-id="13c14-109">Import Mixed Reality Toolkit for Unreal</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="13c14-111">Mixed Reality Toolkit (MRTK) ist ein plattformübergreifendes Open Source-Entwicklungskit für Mixed Reality-Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="13c14-111">Mixed Reality Toolkit (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="13c14-112">MRTK bietet ein plattformübergreifendes Eingabesystem, Grundlagenkomponenten und gemeinsame Bausteine für räumliche Interaktionen.</span><span class="sxs-lookup"><span data-stu-id="13c14-112">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="13c14-113">Das Toolkit soll die Entwicklung von Anwendungen für Microsoft HoloLens, für immersive Windows Mixed Reality-Headsets (VR) und für die OpenVR-Plattform beschleunigen.</span><span class="sxs-lookup"><span data-stu-id="13c14-113">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="13c14-114">Für die Installation empfehlen wir, den Abschnitt [Erste Schritte](unreal-development-overview.md#1-getting-started) Ihrer zusammengestellten [Unreal-Entwicklungsreise](unreal-development-overview.md) auszuführen.</span><span class="sxs-lookup"><span data-stu-id="13c14-114">For installation, we recommend completing the [Getting Started section](unreal-development-overview.md#1-getting-started) of our curated [Unreal development journey](unreal-development-overview.md).</span></span> <span data-ttu-id="13c14-115">Wenn Sie sich bereits auf der Unreal-Entwicklungsreise befinden, beenden Sie die unten aufgelisteten restlichen Setupschritte, und fahren sie mit den [HoloLens 2-Einstiegstutorials](tutorials/unreal-uxt-ch1.md) fort.</span><span class="sxs-lookup"><span data-stu-id="13c14-115">If you're already following the Unreal development journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](tutorials/unreal-uxt-ch1.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="13c14-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity-Logobild](../images/MRTK-Unreal-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="13c14-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity logo image](../images/MRTK-Unreal-Banner.png)</span></span><br><span data-ttu-id="13c14-117">**Mixed Reality Toolkit-Unreal (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="13c14-117">**Mixed Reality Toolkit-Unreal (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> <span data-ttu-id="13c14-118">Wenn Sie MRTK für Unreal nicht verwenden möchten, müssen Sie für alle Interaktionen und Verhaltensweisen selber Skripts erstellen.</span><span class="sxs-lookup"><span data-stu-id="13c14-118">If you don't want to use MRTK for Unreal, you'll need to script all interactions and behaviors yourself.</span></span>