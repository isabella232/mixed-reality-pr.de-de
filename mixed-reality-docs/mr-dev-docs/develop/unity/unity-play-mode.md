---
title: Unity-Wiedergabemodus
description: Erfahren Sie, wie Sie den Wiedergabemodus im Unity-Editor verwenden, um eine Vorschau Ihrer Anwendungsänderungen auf einem Gerät anzuzeigen, ohne eine App bereitzustellen.
author: keveleigh
ms.author: kurtie
ms.date: 05/21/2021
ms.topic: article
keywords: Unity, Remoting, holografisches Remoting, holografischer Remotingplayer, HoloLens, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Unity-Wiedergabemodus
ms.openlocfilehash: b998233fda34beee0c98795a1efa2c86a53541ba
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392291"
---
# <a name="unity-play-mode"></a><span data-ttu-id="363d8-104">Unity-Wiedergabemodus</span><span class="sxs-lookup"><span data-stu-id="363d8-104">Unity Play Mode</span></span>

<span data-ttu-id="363d8-105">Eine schnelle Möglichkeit, an Ihrem Unity-Projekt zu arbeiten, ist die Verwendung des "Wiedergabemodus", der Ihre App lokal im Unity-Editor auf Ihrem PC ausführen kann.</span><span class="sxs-lookup"><span data-stu-id="363d8-105">A fast way to work on your Unity project is to use "Play Mode", which runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="363d8-106">Unity verwendet Holographic Remoting, um eine schnelle Möglichkeit zur Vorschau Ihrer Inhalte auf einem echten HoloLens-Gerät zu bieten.</span><span class="sxs-lookup"><span data-stu-id="363d8-106">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span> <span data-ttu-id="363d8-107">Der Wiedergabemodus kann auch mit einem Windows Mixed Reality Headset verwendet werden, das an Ihren Entwicklungs-PC angeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="363d8-107">Play Mode can also be used with a Windows Mixed Reality headset attached to your development PC.</span></span>

## <a name="holographic-remoting-setup"></a><span data-ttu-id="363d8-108">Holographic Remoting-Setup</span><span class="sxs-lookup"><span data-stu-id="363d8-108">Holographic Remoting setup</span></span>

1. <span data-ttu-id="363d8-109">Zunächst müssen Sie die [Holographic Remoting Player-App](https://www.microsoft.com/store/productId/9NBLGGH4SV40) aus dem Microsoft Store auf Ihrem Computer HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="363d8-109">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from the Microsoft Store on your HoloLens 2</span></span>
2. <span data-ttu-id="363d8-110">Führen Sie die Holographic Remoting Player-App auf HoloLens 2, und Die Versionsnummer und die IP-Adresse für die Verbindung werden angezeigt.</span><span class="sxs-lookup"><span data-stu-id="363d8-110">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="363d8-111">Sie benötigen Version 2.4 oder höher, um mit dem OpenXR-Plug-In arbeiten zu können.</span><span class="sxs-lookup"><span data-stu-id="363d8-111">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

    ![Screenshot des Holographic Remoting-Players, der in HoloLens ausgeführt wird](images/openxr-features-img-01.png)

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="363d8-113">Unity-Wiedergabemodus mit Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="363d8-113">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="363d8-114">Mit Holographic Remoting können Sie Ihre App auf der HoloLens erleben, während sie im Unity-Editor auf Ihrem PC ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="363d8-114">With Holographic Remoting, you can experience your app on the HoloLens while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="363d8-115">Eingaben für Anvieren, Gesten, Sprache und räumliche Abbildung werden von Ihrer HoloLens an Ihren PC gesendet.</span><span class="sxs-lookup"><span data-stu-id="363d8-115">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="363d8-116">Gerenderte Frames werden dann zurück an Ihre HoloLens gesendet.</span><span class="sxs-lookup"><span data-stu-id="363d8-116">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="363d8-117">Dies ist eine hervorragende Möglichkeit, Ihre App schnell zu debuggen, ohne ein vollständiges Projekt zu erstellen und bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="363d8-117">This is a great way to quickly debug your app without building and deploying a full project.</span></span>

[!INCLUDE[](includes/unity-play-mode.md)]

<span data-ttu-id="363d8-118">Holographic Remoting erfordert einen schnellen PC und eine Wi-Fi Verbindung.</span><span class="sxs-lookup"><span data-stu-id="363d8-118">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="363d8-119">Weitere Informationen finden Sie in der [Dokumentation zu Holographic Remoting Player.](../platform-capabilities-and-apis/holographic-remoting-player.md)</span><span class="sxs-lookup"><span data-stu-id="363d8-119">You can find more details in the [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) documentation.</span></span>

<span data-ttu-id="363d8-120">Um optimale Ergebnisse zu erzielen, stellen Sie sicher, dass Ihre App den [Fokuspunkt ordnungsgemäß fest legt.](focus-point-in-unity.md)</span><span class="sxs-lookup"><span data-stu-id="363d8-120">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="363d8-121">Dies hilft Holographic Remoting dabei, Ihre Szene am besten an die Latenz Ihrer Drahtlosverbindung anzupassen.</span><span class="sxs-lookup"><span data-stu-id="363d8-121">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="363d8-122">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="363d8-122">See Also</span></span>

* [<span data-ttu-id="363d8-123">Holographic Remoting-Player</span><span class="sxs-lookup"><span data-stu-id="363d8-123">Holographic Remoting Player</span></span>](../platform-capabilities-and-apis/holographic-remoting-player.md)
