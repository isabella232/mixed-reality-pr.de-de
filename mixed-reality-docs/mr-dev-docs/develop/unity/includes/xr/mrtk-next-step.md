---
ms.openlocfilehash: dbaace96246f28050ff6fb189d9b626be6b0ec9e
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603714"
---
# <a name="openxr"></a>[<span data-ttu-id="ede57-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="ede57-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="ede57-102">Beginnen Sie mit Schritt 2 im MRTK-Tutorial, um mit einem neuen **Unity-Projekt** mit MRTK zu beginnen:</span><span class="sxs-lookup"><span data-stu-id="ede57-102">To get started with a **new Unity project** using MRTK, start from step 2 in the MRTK tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ede57-103">Einrichten eines neuen OpenXR-Projekts mit MRTK</span><span class="sxs-lookup"><span data-stu-id="ede57-103">Set up a new OpenXR project with MRTK</span></span>](../../tutorials/mr-learning-base-02.md?tabs=openxr)

<span data-ttu-id="ede57-104">Wenn Sie ein vorhandenes **MRTK-Projekt auf OpenXR** aktualisieren, sollten Sie zuerst ein Upgrade von MRTK-Unity auf die neueste Version (Version 2.7.2 oder höher) durchführen, um wichtige Fehlerbehebungen für die Kompatibilität mit dem Mixed Reality OpenXR-Plug-In zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="ede57-104">If you're upgrading an **existing MRTK project to OpenXR**, you'll first want to upgrade MRTK-Unity to the latest version (version 2.7.2 or later) to get key fixes for compatibility with the Mixed Reality OpenXR plugin.</span></span>  <span data-ttu-id="ede57-105">Verwenden Sie [das Mixed Reality-Featuretool,](../../welcome-to-mr-feature-tool.md) um ein Upgrade auf die neueste Version von MRTK zu durchführen, und führen Sie dann die schritte zum manuellen [OpenXR-Setup unter aus.](#manual-setup-without-mrtk)</span><span class="sxs-lookup"><span data-stu-id="ede57-105">Use the [Mixed Reality Feature Tool](../../welcome-to-mr-feature-tool.md) to upgrade to the latest version of MRTK and then follow the [manual OpenXR setup steps below](#manual-setup-without-mrtk).</span></span> <span data-ttu-id="ede57-106">In der MRTK-Dokumentation finden Sie detailliertere Informationen zum Migrieren eines vorhandenen [MRTK-Projekts zu OpenXR.](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)</span><span class="sxs-lookup"><span data-stu-id="ede57-106">See the MRTK documentation for [more in-depth information on migrating an existing MRTK project to OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span></span>

> [!NOTE]
> <span data-ttu-id="ede57-107">Stellen Sie beim Upgrade von einer früheren Version von MRTK vor **2.5.3** sicher, dass sich die folgende Zeile in der Datei **Assets/MixedRealityToolkit.Generated/link.xml** befindet:</span><span class="sxs-lookup"><span data-stu-id="ede57-107">When upgrading from a previous version of MRTK older than **2.5.3**, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="ede57-108">Diese Zeile wird standardmäßig hinzugefügt, wenn Sie mit MRTK 2.5.4 oder neuer begonnen haben.</span><span class="sxs-lookup"><span data-stu-id="ede57-108">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="ede57-109">Windows Xr</span><span class="sxs-lookup"><span data-stu-id="ede57-109">Windows XR</span></span>](#tab/windowsxr)

<span data-ttu-id="ede57-110">Beginnen Sie mit Schritt 2 im MRTK-Tutorial, um mit einem neuen **Unity-Projekt** mit MRTK zu beginnen:</span><span class="sxs-lookup"><span data-stu-id="ede57-110">To get started with a **new Unity project** using MRTK, start from step 2 in the MRTK tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ede57-111">Einrichten eines neuen XR Windows projekts mit MRTK</span><span class="sxs-lookup"><span data-stu-id="ede57-111">Set up a new Windows XR project with MRTK</span></span>](../../tutorials/mr-learning-base-02.md?tabs=winxr)

# <a name="legacy-xr"></a>[<span data-ttu-id="ede57-112">Legacy-XR</span><span class="sxs-lookup"><span data-stu-id="ede57-112">Legacy XR</span></span>](#tab/legacy)

<span data-ttu-id="ede57-113">Beginnen Sie mit Schritt 2 im MRTK-Tutorial, um mit einem neuen **Unity-Projekt** mit MRTK zu beginnen:</span><span class="sxs-lookup"><span data-stu-id="ede57-113">To get started with a **new Unity project** using MRTK, start from step 2 in the MRTK tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ede57-114">Einrichten eines neuen Legacy-XR-Projekts mit MRTK</span><span class="sxs-lookup"><span data-stu-id="ede57-114">Set up a new Legacy XR project with MRTK</span></span>](../../tutorials/mr-learning-base-02.md?tabs=wsa)