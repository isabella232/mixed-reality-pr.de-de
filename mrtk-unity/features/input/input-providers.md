---
title: Eingabeanbieter
description: Dokumentation zu verschiedenen Typen von Eingabeanbietern in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: ad4a643d0fb46cdb15cee3c37edaffb4f51ed44b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145264"
---
# <a name="input-providers"></a><span data-ttu-id="6eeba-104">Eingabeanbieter</span><span class="sxs-lookup"><span data-stu-id="6eeba-104">Input providers</span></span>

<span data-ttu-id="6eeba-105">Eingabeanbieter werden im Profil **"Registrierte Dienstanbieter"** registriert, das sich in der Mixed Reality Toolkit-Komponente finden:</span><span class="sxs-lookup"><span data-stu-id="6eeba-105">Input providers are registered in the **Registered Service Providers Profile**, found in the Mixed Reality Toolkit component:</span></span>

<img src="../images/input/RegisteredServiceProviders.PNG" width="650px" style="display:block;" alt="Service providers">

<span data-ttu-id="6eeba-106">Dies sind die eingabeanbieter, die zusammen mit den entsprechenden Controllern sofort verfügbar sind:</span><span class="sxs-lookup"><span data-stu-id="6eeba-106">These are the input providers available out of the box, together with their corresponding controllers:</span></span>

| <span data-ttu-id="6eeba-107">Eingabeanbieter</span><span class="sxs-lookup"><span data-stu-id="6eeba-107">Input Provider</span></span> | <span data-ttu-id="6eeba-108">Controller</span><span class="sxs-lookup"><span data-stu-id="6eeba-108">Controllers</span></span> |
| --- | --- |
| [`Input Simulation Service`](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) | <span data-ttu-id="6eeba-109">Simulierte Hand</span><span class="sxs-lookup"><span data-stu-id="6eeba-109">Simulated Hand</span></span> |
| [`Mouse Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) | <span data-ttu-id="6eeba-110">Maus</span><span class="sxs-lookup"><span data-stu-id="6eeba-110">Mouse</span></span>  |
| [`OpenVR Device Manager`](xref:Microsoft.MixedReality.Toolkit.OpenVR.Input.OpenVRDeviceManager) | <span data-ttu-id="6eeba-111">Generic OpenVR, Vive Wand, Vive Knuckles, Oculus Touch, Oculus Remote, Windows Mixed Reality OpenVR</span><span class="sxs-lookup"><span data-stu-id="6eeba-111">Generic OpenVR, Vive Wand, Vive Knuckles, Oculus Touch, Oculus Remote, Windows Mixed Reality OpenVR</span></span>  |
| [`Unity Joystick Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) | <span data-ttu-id="6eeba-112">Generic Joystick</span><span class="sxs-lookup"><span data-stu-id="6eeba-112">Generic Joystick</span></span>  |
| [`Unity Touch Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityTouchDeviceManager) | <span data-ttu-id="6eeba-113">Unity Touch Controller</span><span class="sxs-lookup"><span data-stu-id="6eeba-113">Unity Touch Controller</span></span>  |
| [`Windows Dictation Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsDictationInputProvider) | <span data-ttu-id="6eeba-114">*None*</span><span class="sxs-lookup"><span data-stu-id="6eeba-114">*None*</span></span>  |
| [`Windows Mixed Reality Device Manager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) | <span data-ttu-id="6eeba-115">WMR Articulated Hand, WMR Controller, WMR GGV (Gaze, Gesture, and Voice) Hand</span><span class="sxs-lookup"><span data-stu-id="6eeba-115">WMR Articulated Hand, WMR Controller, WMR GGV (Gaze, Gesture, and Voice) Hand</span></span> |
| [`Windows Speech Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsSpeechInputProvider) | <span data-ttu-id="6eeba-116">*None*</span><span class="sxs-lookup"><span data-stu-id="6eeba-116">*None*</span></span> |

<span data-ttu-id="6eeba-117">Diktat- und Sprachanbieter erstellen keine Controller, sondern erstellen ihre eigenen speziellen Eingabeereignisse direkt.</span><span class="sxs-lookup"><span data-stu-id="6eeba-117">Dictation and Speech providers don't create any controllers, they raise their own specialized input events directly.</span></span>

<span data-ttu-id="6eeba-118">Benutzerdefinierte Eingabeanbieter können durch Implementieren der -Schnittstelle erstellt [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) werden.</span><span class="sxs-lookup"><span data-stu-id="6eeba-118">Custom input providers can be created by implementing the [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) interface.</span></span>

<span data-ttu-id="6eeba-119">Weitere Informationen finden Sie unter [Erstellen eines Eingabesystemdatenanbieters.](create-data-provider.md)</span><span class="sxs-lookup"><span data-stu-id="6eeba-119">For more information, please see [creating an input system data provider](create-data-provider.md).</span></span>
