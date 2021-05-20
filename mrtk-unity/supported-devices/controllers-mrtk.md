---
title: Controller in MRTK
description: Dokumentation zur Verwendung verschiedener Controller mit MRTK
author: RogPodge
ms.author: roliu
ms.date: 05/13/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Controller, HP Reverb, Oculus, UNITY Vive, Hands
ms.openlocfilehash: 953b1cd56dbf7d7a548a3aba8da07ce5875fec74
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145470"
---
# <a name="controllers-in-mrtk"></a><span data-ttu-id="33393-104">Controller in MRTK</span><span class="sxs-lookup"><span data-stu-id="33393-104">Controllers in MRTK</span></span>

<span data-ttu-id="33393-105">MRTK bietet Unterstützung für viele verschiedene Controller.</span><span class="sxs-lookup"><span data-stu-id="33393-105">MRTK has support for many different controllers.</span></span> <span data-ttu-id="33393-106">Viele Controller, wie z. B. BLEND Vive Knuckles und BLEND Vive Wands, funktionieren nativ, sobald eine mit MRTK konstruierte Anwendung auf dem kompatiblen Gerät gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="33393-106">Many controllers, such as HTC Vive Knuckles and HTC Vive Wands, will work natively once an application built with MRTK is launched on the compatible device.</span></span> <span data-ttu-id="33393-107">Andere Controller, z. B. die artikulierten Hände auf oculus Quest und den HP Reverb G2-Controllern, erfordern zusätzliche Pakete, bevor sie vom MRTK erkannt werden.</span><span class="sxs-lookup"><span data-stu-id="33393-107">Other controllers, such as articulated hands on the Oculus Quest and the HP Reverb G2 Controllers, require additional packages before they are recognized by MRTK.</span></span>

<span data-ttu-id="33393-108">In diesem Dokument werden die gängigen Szenarien beschrieben, in denen zusätzliche Pakete installiert werden müssen.</span><span class="sxs-lookup"><span data-stu-id="33393-108">This document will describe the common scenarios where extra packages need to be installed.</span></span> <span data-ttu-id="33393-109">Weitere Informationen zu Controllern finden Sie auf der Seite mit den [**Features.**](../features/input/controllers.md)</span><span class="sxs-lookup"><span data-stu-id="33393-109">For additional information about controllers, visit the [**features page**](../features/input/controllers.md).</span></span> <span data-ttu-id="33393-110">Informationen zum Debuggen von Problemen mit Controllern finden Sie unter [ **Controllerzuordnungstool.**](../features/tools/controller-mapping-tool.md)</span><span class="sxs-lookup"><span data-stu-id="33393-110">To debug issues with controllers, see the [**Controller mapping tool**](../features/tools/controller-mapping-tool.md)</span></span>

## <a name="hp-reverb-g2-controllers"></a><span data-ttu-id="33393-111">HP Reverb G2-Controller</span><span class="sxs-lookup"><span data-stu-id="33393-111">HP Reverb G2 Controllers</span></span>

<span data-ttu-id="33393-112">Führen Sie zum Erkennen und Anzeigen der HP Reverb G2-Controller bei Verwendung des MRTK die folgenden Schritte aus, um das [**Paket Microsoft.MixedReality.Input**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) zu installieren.</span><span class="sxs-lookup"><span data-stu-id="33393-112">To detect and show the HP Reverb G2 controllers when using MRTK, follow these steps to install the [**Microsoft.MixedReality.Input**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) package.</span></span> <span data-ttu-id="33393-113">Nach der Installation dieses Pakets müssen keine weiteren Änderungen an den Standardprofilen vorgenommen werden, damit die Controller auf dem HP Reverb angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="33393-113">Once this package is installed, no other changes to the default profiles need to be made to have the controllers show up on the HP Reverb.</span></span> 

<span data-ttu-id="33393-114">Um die Controller im Editor anzuzeigen, müssen Sie sicherstellen, dass Sie mit dem [**OpenXR-Plug-In**](/windows/mixed-reality/develop/unity/openxr-getting-started)verwenden.</span><span class="sxs-lookup"><span data-stu-id="33393-114">In order to display the controllers in editor, you need to ensure that you are using the using the [**OpenXR Plugin**](/windows/mixed-reality/develop/unity/openxr-getting-started).</span></span>

## <a name="oculus-controllers"></a><span data-ttu-id="33393-115">Oculus-Controller</span><span class="sxs-lookup"><span data-stu-id="33393-115">Oculus Controllers</span></span> 

<span data-ttu-id="33393-116">Befolgen Sie die Anweisungen zur Oculus Quest-Bereitstellung, um Oculus-Controllermodelle zu visualisieren.</span><span class="sxs-lookup"><span data-stu-id="33393-116">To visualize Oculus controller models, follow the Oculus Quest deployment instructions.</span></span> <span data-ttu-id="33393-117">Wenn Sie virtuelle Hände anzeigen möchten, wenn Sie die Controller verwenden, stellen Sie sicher, dass **Render Avatar Hands Instead Of Controllers** unter dem XR SDK Oculus Geräte-Manager aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="33393-117">If you wish to show virtual hands when using the controllers, make sure that **Render Avatar Hands Instead Of Controllers** is checked under the XR SDK Oculus Device Manager.</span></span> <span data-ttu-id="33393-118">Deaktivieren Sie andernfalls diese Option.</span><span class="sxs-lookup"><span data-stu-id="33393-118">Otherwise, uncheck this option.</span></span>

![OculusDeviceManagerVisualizationSettings](../images/cross-platform/oculus-quest/OculusDeviceManager.png)
