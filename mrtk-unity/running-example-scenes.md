---
title: Beispielszenen
description: Erfahren Sie, wie Sie mrtk-Beispielszenen abrufen und verwenden.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/07/2021
ms.topic: article
keywords: Mixed Reality-Toolkit, MRTK, Beispiele, HoloLens, HoloLens 2, Shader, QuickInfos, Handinteraktion, Clipping, Begrenzungsfelder, Schaltflächen, Handmenüs, Schiefer, Schieberegler
ms.openlocfilehash: d8d2bb40ff1c95e01cb051f36de04beb93829ba1
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177468"
---
# <a name="example-scenes"></a><span data-ttu-id="ec20e-104">Beispielszenen</span><span class="sxs-lookup"><span data-stu-id="ec20e-104">Example scenes</span></span>

<span data-ttu-id="ec20e-105">MRTK bietet verschiedene Arten von Beispielszenen, die die Features und Bausteine von MRTK für die räumliche Benutzererfahrung veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="ec20e-105">MRTK provides various types of example scenes that demonstrate MRTK's features and building blocks for spatial user experience.</span></span> <span data-ttu-id="ec20e-106">Das Erleben und Aufschneiden von Beispielszenen kann hilfreich sein, um die Features zu verstehen und auf Ihre Projekte anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="ec20e-106">Experiencing and dissecting example scenes could be helpful to understand the features and apply them to your projects.</span></span> 

## <a name="how-to-acquire-example-scenes"></a><span data-ttu-id="ec20e-107">Abrufen von Beispielszenen</span><span class="sxs-lookup"><span data-stu-id="ec20e-107">How to acquire example scenes</span></span>

### <a name="using-mixed-reality-feature-tool-and-unity-package-manager"></a><span data-ttu-id="ec20e-108">Verwenden Mixed Reality Featuretools und des Unity-Paket-Managers</span><span class="sxs-lookup"><span data-stu-id="ec20e-108">Using Mixed Reality Feature Tool and Unity package manager</span></span>

<span data-ttu-id="ec20e-109">Sie können **Mixed Reality Toolkit-Beispielpaket** über [Mixed Reality Featuretool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) herunterladen und importieren.</span><span class="sxs-lookup"><span data-stu-id="ec20e-109">You can download and import **Mixed Reality Toolkit Examples** package through [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)</span></span>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_MRFT.png" width="550" alt="Example Package 1"><br/>

<span data-ttu-id="ec20e-110">Verwenden Sie in Unity das Menü **Fenster > Paket-Manager > In Project > Benutzerdefiniert,** und wählen Sie Mixed Reality **Toolkitbeispiele aus.**</span><span class="sxs-lookup"><span data-stu-id="ec20e-110">In Unity, use the menu **Window > Package Manager > In Project > Custom** and select **Mixed Reality Toolkit Examples**.</span></span> 

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_2.png" width="300" alt="Example Package 2"><br/>

<span data-ttu-id="ec20e-111">Klicken Sie in der Liste auf der rechten Seite des Bereichs auf In Project Schaltfläche neben den Beispielszenennamen **importieren.**</span><span class="sxs-lookup"><span data-stu-id="ec20e-111">From the list on the right side of the panel, click **Import into Project** button next to the example scene names.</span></span>  <span data-ttu-id="ec20e-112">Sie können z. **B.** neben Demos – **HandTracking** auf die Schaltfläche In Project importieren klicken.</span><span class="sxs-lookup"><span data-stu-id="ec20e-112">For example, you can click **Import into Project** button next to **Demos - HandTracking**.</span></span> 

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_3.png" width="650" alt="Example Package 3"><br/>

<span data-ttu-id="ec20e-113">Nach dem Import können Sie sie im Ordner **Assets > Samples (Ressourcen > Beispiele)** finden.</span><span class="sxs-lookup"><span data-stu-id="ec20e-113">Once imported, you will be able to find them under **Assets > Samples** folder.</span></span>
<span data-ttu-id="ec20e-114">**Die HandInteractionExamples-Szene** ist ein hervorragender Ort, um die räumlichen Interaktionen und Ui-Bausteine des MRTK zu erleben.</span><span class="sxs-lookup"><span data-stu-id="ec20e-114">**HandInteractionExamples** scene is a great place to start experiencing MRTK's spatial interactions and UI building blocks.</span></span>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_4.png" width="650" alt="Example Package 4"><br/>

### <a name="directly-downloading-and-importing-packages-from-github"></a><span data-ttu-id="ec20e-115">Direktes Herunterladen und Importieren von Paketen aus GitHub</span><span class="sxs-lookup"><span data-stu-id="ec20e-115">Directly downloading and importing packages from GitHub</span></span>

<span data-ttu-id="ec20e-116">Wenn Sie Mixed Reality Feature Tool nicht verwenden, können Sie **Microsoft.MixedReality.Toolkit.Unity.Examples.unitypackage** direkt von der Releaseseite von [MRTK GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) herunterladen und importieren.</span><span class="sxs-lookup"><span data-stu-id="ec20e-116">If you don't use Mixed Reality Feature Tool, you can directly download and import **Microsoft.MixedReality.Toolkit.Unity.Examples.unitypackage** from [MRTK GitHub's release page](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)</span></span>

<span data-ttu-id="ec20e-117">Verwenden Sie das Menü Assets > Import Package > Custom Package ( **Benutzerdefiniertes Paket),** um heruntergeladenes UNITYPACKAGE zu importieren.</span><span class="sxs-lookup"><span data-stu-id="ec20e-117">Use **Assets > Import Package > Custom Package** menu to import downloaded .unitypackage.</span></span> <span data-ttu-id="ec20e-118">Nach dem Import finden Sie Beispielszenen unter **Assets > MRTK > Examples > Demos**.</span><span class="sxs-lookup"><span data-stu-id="ec20e-118">Once it is imported, you will be able to find example scenes under **Assets > MRTK > Examples > Demos**.</span></span>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_Manual1.png" width="650" alt="Example Manual 1"><br/>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_Manual2.png" width="650" alt="Example Manual 2"><br/>
