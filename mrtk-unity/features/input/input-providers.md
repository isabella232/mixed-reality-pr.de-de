---
title: Eingabeanbieter
description: Dokumentation zu verschiedenen Typen von Eingabeanbietern in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: f53932b5e12e60b3638c1d6c31e569016de983ee
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176752"
---
# <a name="input-providers"></a><span data-ttu-id="939d9-104">Eingabeanbieter</span><span class="sxs-lookup"><span data-stu-id="939d9-104">Input providers</span></span>

<span data-ttu-id="939d9-105">Eingabeanbieter werden im **Profil registrierte Dienstanbieter** in der Komponente Mixed Reality Toolkit registriert:</span><span class="sxs-lookup"><span data-stu-id="939d9-105">Input providers are registered in the **Registered Service Providers Profile**, found in the Mixed Reality Toolkit component:</span></span>

<img src="../images/input/RegisteredServiceProviders.PNG" width="650px" style="display:block;" alt="Service providers">

<span data-ttu-id="939d9-106">Dies sind die voreindingen verfügbaren Eingabeanbieter zusammen mit den entsprechenden Controllern:</span><span class="sxs-lookup"><span data-stu-id="939d9-106">These are the input providers available out of the box, together with their corresponding controllers:</span></span>

| <span data-ttu-id="939d9-107">Eingabeanbieter</span><span class="sxs-lookup"><span data-stu-id="939d9-107">Input Provider</span></span> | <span data-ttu-id="939d9-108">Controller</span><span class="sxs-lookup"><span data-stu-id="939d9-108">Controllers</span></span> |
| --- | --- |
| [`Input Simulation Service`](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) | <span data-ttu-id="939d9-109">Simulierte Hand</span><span class="sxs-lookup"><span data-stu-id="939d9-109">Simulated Hand</span></span> |
| [`Mouse Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) | <span data-ttu-id="939d9-110">Maus</span><span class="sxs-lookup"><span data-stu-id="939d9-110">Mouse</span></span>  |
| [`OpenVR Device Manager`](xref:Microsoft.MixedReality.Toolkit.OpenVR.Input.OpenVRDeviceManager) | <span data-ttu-id="939d9-111">Generic OpenVR, Vive Wand, Vive Knuckles, Oculus Touch, Oculus Remote, Windows Mixed Reality OpenVR</span><span class="sxs-lookup"><span data-stu-id="939d9-111">Generic OpenVR, Vive Wand, Vive Knuckles, Oculus Touch, Oculus Remote, Windows Mixed Reality OpenVR</span></span>  |
| [`Unity Joystick Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) | <span data-ttu-id="939d9-112">Generischer Manding</span><span class="sxs-lookup"><span data-stu-id="939d9-112">Generic Joystick</span></span>  |
| [`Unity Touch Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityTouchDeviceManager) | <span data-ttu-id="939d9-113">Unity Touch Controller</span><span class="sxs-lookup"><span data-stu-id="939d9-113">Unity Touch Controller</span></span>  |
| [`Windows Dictation Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsDictationInputProvider) | <span data-ttu-id="939d9-114">*Keine*</span><span class="sxs-lookup"><span data-stu-id="939d9-114">*None*</span></span>  |
| [`Windows Mixed Reality Device Manager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) | <span data-ttu-id="939d9-115">ARTIkulierte WMR-Hand, WMR-Controller, WMR-GGV-Hand (Anvieren, Geste und Stimme)</span><span class="sxs-lookup"><span data-stu-id="939d9-115">WMR Articulated Hand, WMR Controller, WMR GGV (Gaze, Gesture, and Voice) Hand</span></span> |
| [`Windows Speech Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsSpeechInputProvider) | <span data-ttu-id="939d9-116">*Keine*</span><span class="sxs-lookup"><span data-stu-id="939d9-116">*None*</span></span> |

<span data-ttu-id="939d9-117">Diktat- und Sprachanbieter erstellen keine Controller, sie richten ihre eigenen speziellen Eingabeereignisse direkt aus.</span><span class="sxs-lookup"><span data-stu-id="939d9-117">Dictation and Speech providers don't create any controllers, they raise their own specialized input events directly.</span></span>

<span data-ttu-id="939d9-118">Benutzerdefinierte Eingabeanbieter können durch Implementieren der -Schnittstelle erstellt [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) werden.</span><span class="sxs-lookup"><span data-stu-id="939d9-118">Custom input providers can be created by implementing the [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) interface.</span></span>

<span data-ttu-id="939d9-119">Weitere Informationen finden Sie unter [Erstellen eines Eingabesystemdatenanbieters.](create-data-provider.md)</span><span class="sxs-lookup"><span data-stu-id="939d9-119">For more information, please see [creating an input system data provider](create-data-provider.md).</span></span>
