---
ms.openlocfilehash: d7232ca645c2a8cfb2508b090fdb7ae02c2ab010
ms.sourcegitcommit: 95fbb851336b6c5977a2ce4d4ac10f0eeb0df31f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2021
ms.locfileid: "107984414"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="7e27f-101">Unity 2019/2020 und Windows-XR-Plugin</span><span class="sxs-lookup"><span data-stu-id="7e27f-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="7e27f-102">Wählen Sie im Unity-Menü **File** > **Build Settings...** (Datei > Buildeinstellungen...) aus, um das Fenster Build Settings (Buildeinstellungen) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="7e27f-102">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Unity: Build Settings... Menüpfad](../images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="7e27f-104">Wählen Sie im Build Settings-Fenster **Universal Windows Platform** (Universelle Windows-Plattform) aus, und klicken Sie auf die Schaltfläche **Switch Platform** (Plattform wechseln):</span><span class="sxs-lookup"><span data-stu-id="7e27f-104">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![Unity-Fenster „Build Settings“ mit ausgewählter UWP, um von der Plattform „Eigenständig“ zu wechseln](../images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="7e27f-106">Warten Sie, bis Unity den Wechsel der Plattform abgeschlossen hat:</span><span class="sxs-lookup"><span data-stu-id="7e27f-106">Wait for Unity to finish switching the platform:</span></span>

![Unity: Wechsel der Plattform in Bearbeitung](../images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="7e27f-108">Wenn Unity den Plattformwechsel abgeschlossen hat, klicken Sie auf das rote **x**-Symbol, um das Build Settings-Fenster zu schließen:</span><span class="sxs-lookup"><span data-stu-id="7e27f-108">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![Unity-Fenster „Build“ mit hervorgehobenem Symbol zum Schließen](../images/mr-learning-base/base-02-section2-step1-4.png)

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="7e27f-110">Unity 2020 und OpenXR</span><span class="sxs-lookup"><span data-stu-id="7e27f-110">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="7e27f-111">Wählen Sie im Unity-Menü **File** > **Build Settings...** (Datei > Buildeinstellungen...) aus, um das Fenster Build Settings (Buildeinstellungen) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="7e27f-111">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Unity: Build Settings... Menüpfad](../images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="7e27f-113">Wählen Sie im Build Settings-Fenster **Universelle Windows-Plattform** aus, und:</span><span class="sxs-lookup"><span data-stu-id="7e27f-113">In the Build Settings window, select **Universal Windows Platform** and:</span></span>
1.  <span data-ttu-id="7e27f-114">Legen Sie **Zielgerät** auf **HoloLens** fest</span><span class="sxs-lookup"><span data-stu-id="7e27f-114">Set **Target device** to **HoloLens**</span></span>
2.  <span data-ttu-id="7e27f-115">Legen Sie **Architektur** auf **ARM 64** fest</span><span class="sxs-lookup"><span data-stu-id="7e27f-115">Set **Architecture** to **ARM 64**</span></span>
3.  <span data-ttu-id="7e27f-116">Legen Sie **Build Type** (Buildtyp) auf **D3D Project** (D3D-Projekt) fest.</span><span class="sxs-lookup"><span data-stu-id="7e27f-116">Set **Build Type** to **D3D Project**</span></span>
4.  <span data-ttu-id="7e27f-117">Legen Sie **SDK-Zielversion** auf **Zuletzt installiert** fest</span><span class="sxs-lookup"><span data-stu-id="7e27f-117">Set **Target SDK Version** to **Latest Installed**</span></span>
5.  <span data-ttu-id="7e27f-118">Legen Sie **Minimale Plattformversion** auf **10.0.18362** fest</span><span class="sxs-lookup"><span data-stu-id="7e27f-118">Set **Minimum Platform Version** to **10.0.18362**</span></span>
6.  <span data-ttu-id="7e27f-119">Legen Sie **Visual Studio-Version** auf **Zuletzt installiert** fest</span><span class="sxs-lookup"><span data-stu-id="7e27f-119">Set **Visual Studio Version** to **Latest installed**</span></span>
7.  <span data-ttu-id="7e27f-120">Legen Sie **Build and Run on** (Erstellen und Ausführen auf) auf **USB-Gerät** fest</span><span class="sxs-lookup"><span data-stu-id="7e27f-120">Set **Build and Run on** to **USB Device**</span></span>
8.  <span data-ttu-id="7e27f-121">Legen Sie **Buildkonfiguration** auf **Release** fest, da beim Debuggen bekannte Leistungsprobleme auftreten.</span><span class="sxs-lookup"><span data-stu-id="7e27f-121">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>
9.  <span data-ttu-id="7e27f-122">Klicken Sie auf die Schaltfläche „Plattform wechseln“.</span><span class="sxs-lookup"><span data-stu-id="7e27f-122">Click the Switch Platform button</span></span>


![Unity-Buildeinstellungen mit festgelegten Einstellungen für die Universelle Windows-Plattform](../images/mr-learning-base/base-02-section2-step1-2-openxr.png)

<span data-ttu-id="7e27f-124">Wenn Unity den Plattformwechsel abgeschlossen hat, klicken Sie auf das rote **x**-Symbol, um das Fenster mit den Buildeinstellungen zu schließen.</span><span class="sxs-lookup"><span data-stu-id="7e27f-124">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="7e27f-125">Legacy-WSA</span><span class="sxs-lookup"><span data-stu-id="7e27f-125">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="7e27f-126">Wählen Sie im Unity-Menü **File** > **Build Settings...** (Datei > Buildeinstellungen...) aus, um das Fenster Build Settings (Buildeinstellungen) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="7e27f-126">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Unity: Build Settings... Menüpfad](../images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="7e27f-128">Wählen Sie im Build Settings-Fenster **Universal Windows Platform** (Universelle Windows-Plattform) aus, und klicken Sie auf die Schaltfläche **Switch Platform** (Plattform wechseln):</span><span class="sxs-lookup"><span data-stu-id="7e27f-128">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![Unity-Fenster „Build Settings“ mit ausgewählter UWP, um von der Plattform „Eigenständig“ zu wechseln](../images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="7e27f-130">Warten Sie, bis Unity den Wechsel der Plattform abgeschlossen hat:</span><span class="sxs-lookup"><span data-stu-id="7e27f-130">Wait for Unity to finish switching the platform:</span></span>

![Unity: Wechsel der Plattform in Bearbeitung](../images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="7e27f-132">Wenn Unity den Plattformwechsel abgeschlossen hat, klicken Sie auf das rote **x**-Symbol, um das Build Settings-Fenster zu schließen:</span><span class="sxs-lookup"><span data-stu-id="7e27f-132">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![Unity-Fenster „Build“ mit hervorgehobenem Symbol zum Schließen](../images/mr-learning-base/base-02-section2-step1-4.png)
