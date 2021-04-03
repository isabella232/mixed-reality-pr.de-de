---
title: Verwenden der integrierten Unterstützung von XR
description: Erfahren Sie, wie Sie Ihre Unity-Projekte mit und ohne mrtk mithilfe der vordefinierten Unterstützung von XR einrichten.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, gemischte Realität, Entwicklung, Einstieg, neues Projekt, Windows Mixed Reality, UWP, XR, Leistung, Legacy, mrtk
ms.openlocfilehash: 09989b3b2b7fa1d351235a2cc9b885d4795dc2b6
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/31/2021
ms.locfileid: "106088529"
---
# <a name="using-legacy-built-in-xr-support"></a><span data-ttu-id="6d8af-104">Verwenden der integrierten Unterstützung von XR</span><span class="sxs-lookup"><span data-stu-id="6d8af-104">Using Legacy built-in XR support</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="6d8af-105">Einrichten Ihres Projekts mit mrtk</span><span class="sxs-lookup"><span data-stu-id="6d8af-105">Setting up your project with MRTK</span></span>

<span data-ttu-id="6d8af-106">MRTK für Unity bietet ein plattformübergreifendes Eingabesystem, Grundlagenkomponenten und gemeinsame Bausteine für räumliche Interaktionen.</span><span class="sxs-lookup"><span data-stu-id="6d8af-106">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="6d8af-107">MRTK, Version 2, soll die Anwendungsentwicklung für Microsoft HoloLens, für immersive Windows Mixed Reality-Headsets (VR) und für die OpenVR-Plattform beschleunigen.</span><span class="sxs-lookup"><span data-stu-id="6d8af-107">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="6d8af-108">Das Projekt ist darauf ausgerichtet, die Einstiegshürden zum Erstellen von Mixed Reality-Anwendungen zu verringern, und einen Beitrag für die Community auf diesem stetig wachsenden Gebiet zu leisten.</span><span class="sxs-lookup"><span data-stu-id="6d8af-108">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6d8af-109">Testen Sie unsere mrtk-Tutorials</span><span class="sxs-lookup"><span data-stu-id="6d8af-109">Try out our MRTK tutorials</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=wsa)

<span data-ttu-id="6d8af-110">Weitere Featuredetails finden Sie in [der Dokumentation zu mrtk](/windows/mixed-reality/mrtk-unity) .</span><span class="sxs-lookup"><span data-stu-id="6d8af-110">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="6d8af-111">Manuelles Setup ohne mrtk</span><span class="sxs-lookup"><span data-stu-id="6d8af-111">Manual setup without MRTK</span></span>

<span data-ttu-id="6d8af-112">Wenn Sie auf Desktop VR abzielen, empfiehlt es sich, die eigenständige PC-Plattform zu verwenden, die für ein neues Unity-Projekt standardmäßig ausgewählt ist:</span><span class="sxs-lookup"><span data-stu-id="6d8af-112">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor mit PC, Mac & eigenständige Plattform hervorgehoben](images/wmr-config-img-3.png)

<span data-ttu-id="6d8af-114">Wenn Sie hololens 2 als Ziel verwenden, müssen Sie zum universelle Windows-Plattform wechseln:</span><span class="sxs-lookup"><span data-stu-id="6d8af-114">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="6d8af-115">**Datei > Buildeinstellungen auswählen...**</span><span class="sxs-lookup"><span data-stu-id="6d8af-115">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="6d8af-116">Wählen Sie in der Platt Form Liste **universelle Windows-Plattform** aus, und wählen Sie **Plattform wechseln**</span><span class="sxs-lookup"><span data-stu-id="6d8af-116">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="6d8af-117">**Architektur** auf **Arm 64** festlegen</span><span class="sxs-lookup"><span data-stu-id="6d8af-117">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="6d8af-118">**Zielgerät** auf **hololens** festlegen</span><span class="sxs-lookup"><span data-stu-id="6d8af-118">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="6d8af-119">**Buildtyp** auf **D3D** festlegen</span><span class="sxs-lookup"><span data-stu-id="6d8af-119">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="6d8af-120">**UWP SDK** auf **Letztes installiert** festlegen</span><span class="sxs-lookup"><span data-stu-id="6d8af-120">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="6d8af-121">**Buildkonfiguration** auf **Release** festlegen, da beim Debuggen bekannte Leistungsprobleme auftreten</span><span class="sxs-lookup"><span data-stu-id="6d8af-121">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor öffnen mit hervorgehobener universelle Windows-Plattform](images/wmr-config-img-4.png)

<span data-ttu-id="6d8af-123">Nachdem Sie Ihre Plattform festgelegt haben, müssen Sie Unity mitteilen, dass Sie beim Exportieren eine [immersive Ansicht](../../design/app-views.md) anstelle einer 2D-Ansicht erstellen soll.</span><span class="sxs-lookup"><span data-stu-id="6d8af-123">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

> [!CAUTION]
> <span data-ttu-id="6d8af-124">Legacy XR ist in Unity 2019 veraltet und wurde in Unity 2020 entfernt.</span><span class="sxs-lookup"><span data-stu-id="6d8af-124">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

1. <span data-ttu-id="6d8af-125">**Player Einstellungen** öffnen... aus den **Buildeinstellungen... Fenster** und erweitern Sie die Gruppe " **XR-Einstellungen** ".</span><span class="sxs-lookup"><span data-stu-id="6d8af-125">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="6d8af-126">Wählen Sie im Abschnitt " **XR-Einstellungen** " die Option **virtuelle Realität unterstützt** aus, um die Liste Virtual Reality-Geräte</span><span class="sxs-lookup"><span data-stu-id="6d8af-126">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="6d8af-127">Festlegen des **tiefen Formats** auf eine **16-Bit-Tiefe** und Aktivieren der **tiefen Puffer Freigabe**</span><span class="sxs-lookup"><span data-stu-id="6d8af-127">Set **Depth Format** to **16-bit Depth** and enable **Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="6d8af-128">Festlegen des **Stereo Renderingmodus** auf eine **Einzel Pass Instanz**</span><span class="sxs-lookup"><span data-stu-id="6d8af-128">Set **Stereo Rendering Mode** to **Single Pass Instance**</span></span>
5. <span data-ttu-id="6d8af-129">Wählen Sie **WSA Holographic Remoting unterstützt** aus, wenn Sie Holographic Remoting verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="6d8af-129">Select **WSA Holographic Remoting Supported** if you'd like to use Holographic remoting</span></span> 

![Screenshot des Fensters "Projekteinstellungen" im Unity-Editor mit hervorgehobenem Abschnitt "Player Einstellungen"](images/wmr-config-img-9.png)