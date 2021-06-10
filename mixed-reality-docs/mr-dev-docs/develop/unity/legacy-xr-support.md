---
title: Verwenden der integrierten Legacy-XR-Unterstützung
description: Erfahren Sie, wie Sie Ihre Unity-Projekte mit und ohne MRTK mithilfe der integrierten Legacy-XR-Unterstützung einrichten.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, Mixed Reality, Entwicklung, erste Schritte, neues Projekt, Windows Mixed Reality, UWP, XR, Leistung, Legacy, mrtk
ms.openlocfilehash: b5faa48ec913c5095b12361318729b6f14276f30
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743502"
---
# <a name="using-legacy-built-in-xr-support"></a><span data-ttu-id="93e20-104">Verwenden der integrierten Legacy-XR-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="93e20-104">Using Legacy built-in XR support</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="93e20-105">Einrichten Ihres Projekts mit MRTK</span><span class="sxs-lookup"><span data-stu-id="93e20-105">Setting up your project with MRTK</span></span>

<span data-ttu-id="93e20-106">MRTK für Unity bietet ein plattformübergreifendes Eingabesystem, Grundlagenkomponenten und gemeinsame Bausteine für räumliche Interaktionen.</span><span class="sxs-lookup"><span data-stu-id="93e20-106">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="93e20-107">MRTK, Version 2, soll die Anwendungsentwicklung für Microsoft HoloLens, für immersive Windows Mixed Reality-Headsets (VR) und für die OpenVR-Plattform beschleunigen.</span><span class="sxs-lookup"><span data-stu-id="93e20-107">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="93e20-108">Das Projekt ist darauf ausgerichtet, die Einstiegshürden zum Erstellen von Mixed Reality-Anwendungen zu verringern, und einen Beitrag für die Community auf diesem stetig wachsenden Gebiet zu leisten.</span><span class="sxs-lookup"><span data-stu-id="93e20-108">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="93e20-109">Probieren Sie unsere MRTK-Tutorials aus</span><span class="sxs-lookup"><span data-stu-id="93e20-109">Try out our MRTK tutorials</span></span>](./tutorials/mr-learning-base-02.md?tabs=wsa)

<span data-ttu-id="93e20-110">Weitere Details zu Features finden Sie in der [MRTK-Dokumentation](/windows/mixed-reality/mrtk-unity).</span><span class="sxs-lookup"><span data-stu-id="93e20-110">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="93e20-111">Manuelle Einrichtung ohne MRTK</span><span class="sxs-lookup"><span data-stu-id="93e20-111">Manual setup without MRTK</span></span>

<span data-ttu-id="93e20-112">Wenn Sie desktop VR als Ziel verwenden möchten, empfehlen wir, die pc Standalone Platform zu verwenden, die standardmäßig für ein neues Unity-Projekt ausgewählt ist:</span><span class="sxs-lookup"><span data-stu-id="93e20-112">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Screenshot des Fensters "Buildeinstellungen", das im Unity-Editor geöffnet ist, wobei PC, Mac & eigenständige Plattform hervorgehoben ist](images/wmr-config-img-3.png)

<span data-ttu-id="93e20-114">Wenn Sie HoloLens 2 als Ziel haben, müssen Sie zum Universelle Windows-Plattform wechseln:</span><span class="sxs-lookup"><span data-stu-id="93e20-114">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="93e20-115">Wählen Sie **Datei > Buildeinstellungen... aus.**</span><span class="sxs-lookup"><span data-stu-id="93e20-115">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="93e20-116">Wählen Sie **Universelle Windows-Plattform** in der Liste Plattform und dann **Plattform wechseln** aus.</span><span class="sxs-lookup"><span data-stu-id="93e20-116">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="93e20-117">Legen Sie **Architektur** auf **ARM 64** fest</span><span class="sxs-lookup"><span data-stu-id="93e20-117">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="93e20-118">Legen Sie **Zielgerät** auf **HoloLens** fest</span><span class="sxs-lookup"><span data-stu-id="93e20-118">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="93e20-119">Legen Sie **Buildtyp** auf **D3D** fest</span><span class="sxs-lookup"><span data-stu-id="93e20-119">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="93e20-120">Legen Sie **UWP SDK** auf **Zuletzt installiert** fest</span><span class="sxs-lookup"><span data-stu-id="93e20-120">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="93e20-121">Legen Sie **Buildkonfiguration** auf **Release** fest, da beim Debuggen bekannte Leistungsprobleme auftreten.</span><span class="sxs-lookup"><span data-stu-id="93e20-121">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor mit hervorgehobener Universelle Windows-Plattform](images/wmr-config-img-4.png)

<span data-ttu-id="93e20-123">Nachdem Sie Ihre Plattform festgelegt haben, müssen Sie Unity mitteilen, dass beim Exportieren eine [immersive Ansicht](../../design/app-views.md) anstelle einer 2D-Ansicht erstellt werden soll.</span><span class="sxs-lookup"><span data-stu-id="93e20-123">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

> [!CAUTION]
> <span data-ttu-id="93e20-124">Legacy-XR ist in Unity 2019 veraltet und wurde in Unity 2020 entfernt.</span><span class="sxs-lookup"><span data-stu-id="93e20-124">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

1. <span data-ttu-id="93e20-125">Öffnen **Sie Playereinstellungen...** aus den **Buildeinstellungen... Fenster** und Erweitern der Gruppe **"XR-Einstellungen"**</span><span class="sxs-lookup"><span data-stu-id="93e20-125">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="93e20-126">Wählen Sie im Abschnitt **XR-Einstellungen** die Option **Virtual Reality Unterstützt** aus, um die Liste Virtual Reality-Geräte hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="93e20-126">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="93e20-127">Festlegen des **Tiefenformats** auf **16-Bit-Tiefe** und Aktivieren der **Tiefenpufferfreigabe**</span><span class="sxs-lookup"><span data-stu-id="93e20-127">Set **Depth Format** to **16-bit Depth** and enable **Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="93e20-128">Festlegen **des Stereorenderingmodus** auf **eine Einzeldurchlaufinstanz**</span><span class="sxs-lookup"><span data-stu-id="93e20-128">Set **Stereo Rendering Mode** to **Single Pass Instance**</span></span>
5. <span data-ttu-id="93e20-129">Wählen Sie **WSA Holographic Remoting Supported (Unterstütztes WSA Holographic Remoting)** aus, wenn Sie Holographic Remoting verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="93e20-129">Select **WSA Holographic Remoting Supported** if you'd like to use Holographic remoting</span></span> 

![Screenshot: Geöffnetes Fenster "Projekteinstellungen" im Unity-Editor mit hervorgehobenen Player-Einstellungen](images/wmr-config-img-9.png)