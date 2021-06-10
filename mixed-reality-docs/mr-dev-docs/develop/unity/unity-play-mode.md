---
title: Unity-Wiedergabemodus
description: Erfahren Sie, wie Sie den Wiedergabemodus im Unity-Editor verwenden, um eine Vorschau Ihrer Anwendungsänderungen auf einem Gerät anzuzeigen, ohne eine App bereitzustellen.
author: keveleigh
ms.author: kurtie
ms.date: 05/21/2021
ms.topic: article
keywords: Unity, Remoting, holografisches Remoting, Holographic Remoting-Player, HoloLens, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Unity-Wiedergabemodus
ms.openlocfilehash: caa9d7bf11104ee168fda24fc369de490feb7817
ms.sourcegitcommit: 5617575cf550dd03fba0bfd5263e97972dcc646b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547101"
---
# <a name="unity-play-mode"></a><span data-ttu-id="471cb-104">Unity-Wiedergabemodus</span><span class="sxs-lookup"><span data-stu-id="471cb-104">Unity Play Mode</span></span>

<span data-ttu-id="471cb-105">Eine schnelle Möglichkeit, an Ihrem Unity-Projekt zu arbeiten, ist die Verwendung des "Wiedergabemodus", der Ihre App lokal im Unity-Editor auf Ihrem PC ausführt.</span><span class="sxs-lookup"><span data-stu-id="471cb-105">A fast way to work on your Unity project is to use "Play Mode", which runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="471cb-106">Unity verwendet Holographic Remoting, um eine schnelle Möglichkeit zum Anzeigen einer Vorschau Ihrer Inhalte auf einem echten HoloLens-Gerät bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="471cb-106">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span> <span data-ttu-id="471cb-107">Der Wiedergabemodus kann auch mit einem Windows Mixed Reality Headset verwendet werden, das an Ihren Entwicklungs-PC angefügt ist.</span><span class="sxs-lookup"><span data-stu-id="471cb-107">Play Mode can also be used with a Windows Mixed Reality headset attached to your development PC.</span></span>

## <a name="holographic-remoting-setup"></a><span data-ttu-id="471cb-108">Holographic Remoting-Setup</span><span class="sxs-lookup"><span data-stu-id="471cb-108">Holographic Remoting setup</span></span>

1. <span data-ttu-id="471cb-109">Zunächst müssen Sie [die Holographic Remoting Player-App](https://www.microsoft.com/store/productId/9NBLGGH4SV40) über die Microsoft Store auf Ihrem HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="471cb-109">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from the Microsoft Store on your HoloLens 2</span></span>
2. <span data-ttu-id="471cb-110">Führen Sie die Holographic Remoting Player-App auf HoloLens 2 aus, und Sie sehen die Versionsnummer und die IP-Adresse für die Verbindungsherstellung.</span><span class="sxs-lookup"><span data-stu-id="471cb-110">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="471cb-111">Sie benötigen Version 2.4 oder höher, um mit dem OpenXR-Plug-In arbeiten zu können.</span><span class="sxs-lookup"><span data-stu-id="471cb-111">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

    ![Screenshot des Holographic Remoting-Players, der in holoLens ausgeführt wird](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a><span data-ttu-id="471cb-113">Holographic Remoting im Wiedergabemodus des Unity-Editors</span><span class="sxs-lookup"><span data-stu-id="471cb-113">Holographic Remoting in Unity Editor play mode</span></span>

<span data-ttu-id="471cb-114">Das Erstellen eines UWP-Unity-Projekts in Visual Studio Projekt und das anschließende Packen und Bereitstellen auf einem HoloLens 2 Gerät kann einige Zeit in Anspruch nehmen.</span><span class="sxs-lookup"><span data-stu-id="471cb-114">Building a UWP Unity project in Visual Studio project and then packaging and deploying it to a HoloLens 2 device can take some time.</span></span> <span data-ttu-id="471cb-115">Eine Lösung besteht darin, das Remotingfeature des Holographic Editor zu aktivieren, mit dem Sie Ihr C#-Skript im Wiedergabemodus direkt auf einem HoloLens 2 Gerät über Ihr Netzwerk debuggen können.</span><span class="sxs-lookup"><span data-stu-id="471cb-115">One solution is to enable the Holographic Editor Remoting feature, which lets you debug your C# script using “Play” mode directly to a HoloLens 2 device over your network.</span></span> <span data-ttu-id="471cb-116">In diesem Szenario wird der Mehraufwand für das Erstellen und Bereitstellen eines UWP-Pakets auf einem Remotegerät vermieden.</span><span class="sxs-lookup"><span data-stu-id="471cb-116">This scenario avoids the overhead of building and deploying a UWP package to remote device.</span></span>

1. <span data-ttu-id="471cb-117">Führen Sie die Schritte unter [Holographic Remoting setup (Holographic Remoting-Setup)](#holographic-remoting-setup) aus.</span><span class="sxs-lookup"><span data-stu-id="471cb-117">Follow the steps in [Holographic Remoting setup](#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="471cb-118">Öffnen Sie **windows > XR > OpenXR Editor Remoting**:</span><span class="sxs-lookup"><span data-stu-id="471cb-118">Open **Windows > XR > OpenXR Editor Remoting**:</span></span>

    ![Screenshot: Geöffneter Bereich "Projekteinstellungen" im Unity-Editor mit hervorgehobener XR-Plug-In-Verwaltung](images/openxr-features-img-02.png)

3. <span data-ttu-id="471cb-120">Geben Sie die IP-Adresse ein, die Sie aus der Holographic Remoting-App erhalten, und wählen **Sie Editor-Remoting aktivieren** aus.</span><span class="sxs-lookup"><span data-stu-id="471cb-120">Input the IP address you get from the Holographic Remoting app, and select **Enable Editor Remoting**</span></span>

    ![Screenshot: Geöffneter Bereich "Projekteinstellungen" im Unity-Editor mit hervorgehobenen Features](images/openxr-features-img-03.png)

<span data-ttu-id="471cb-122">Jetzt können Sie auf die Schaltfläche "Wiedergeben" klicken, um Ihre Unity-App in der Holographic Remoting-App auf Ihrer HoloLens wiederzugeben.</span><span class="sxs-lookup"><span data-stu-id="471cb-122">Now you can click the “Play” button to play your Unity app into the Holographic Remoting app on your HoloLens.</span></span> <span data-ttu-id="471cb-123">Sie können auch [Visual Studio an Unity anfügen,](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) um C#-Skripts im Wiedergabemodus zu debuggen.</span><span class="sxs-lookup"><span data-stu-id="471cb-123">You can also [attach Visual Studio to Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) to debug C# scripts in the play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="471cb-124">Ab Version 0.1.0 unterstützt die Holographic Remoting-Runtime Anchors nicht mehr, und ARAnchorManager-Funktionen funktionieren nicht über Remoting.</span><span class="sxs-lookup"><span data-stu-id="471cb-124">As of version 0.1.0, the Holographic Remoting runtime doesn’t support Anchors, and ARAnchorManager functionalities will not work through remoting.</span></span>  <span data-ttu-id="471cb-125">Dieses Feature wird in zukünftigen Versionen veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="471cb-125">This feature is coming in future releases.</span></span>

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="471cb-126">Unity-Wiedergabemodus mit Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="471cb-126">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="471cb-127">Mit Holographic Remoting können Sie Ihre App auf der HoloLens erleben, während sie im Unity-Editor auf Ihrem PC ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="471cb-127">With Holographic Remoting, you can experience your app on the HoloLens while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="471cb-128">Eingaben für Anvieren, Gesten, Stimmen und räumliche Zuordnungen werden von Ihrer HoloLens an Ihren PC gesendet.</span><span class="sxs-lookup"><span data-stu-id="471cb-128">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="471cb-129">Gerenderte Frames werden dann an Ihre HoloLens zurückgesendet.</span><span class="sxs-lookup"><span data-stu-id="471cb-129">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="471cb-130">Dies ist eine hervorragende Möglichkeit, Ihre App schnell zu debuggen, ohne ein vollständiges Projekt zu erstellen und bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="471cb-130">This is a great way to quickly debug your app without building and deploying a full project.</span></span>

[!INCLUDE[](includes/unity-play-mode.md)]

<span data-ttu-id="471cb-131">Holographic Remoting erfordert einen schnellen PC und Wi-Fi Verbindung.</span><span class="sxs-lookup"><span data-stu-id="471cb-131">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="471cb-132">Weitere Informationen finden Sie in der [Holographic Remoting](../platform-capabilities-and-apis/holographic-remoting-player.md) Player-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="471cb-132">You can find more details in the [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) documentation.</span></span>

<span data-ttu-id="471cb-133">Um optimale Ergebnisse zu erzielen, stellen Sie sicher, dass Ihre App den [Fokuspunkt](focus-point-in-unity.md)ordnungsgemäß festlegt.</span><span class="sxs-lookup"><span data-stu-id="471cb-133">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="471cb-134">Dies hilft Holographic Remoting dabei, Ihre Szene am besten an die Latenz Ihrer Funkverbindung anzupassen.</span><span class="sxs-lookup"><span data-stu-id="471cb-134">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="471cb-135">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="471cb-135">See Also</span></span>

* [<span data-ttu-id="471cb-136">Holographic Remoting-Player</span><span class="sxs-lookup"><span data-stu-id="471cb-136">Holographic Remoting Player</span></span>](../platform-capabilities-and-apis/holographic-remoting-player.md)
