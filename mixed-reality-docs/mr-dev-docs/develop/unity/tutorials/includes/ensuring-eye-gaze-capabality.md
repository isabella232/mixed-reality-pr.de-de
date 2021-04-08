---
ms.openlocfilehash: 4b42b669e45181dec45cab2337d01488c77f77cb
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/31/2021
ms.locfileid: "106096991"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="2603c-101">Unity 2019/2020 und Windows-XR-Plugin</span><span class="sxs-lookup"><span data-stu-id="2603c-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

## <a name="ensuring-eye-gaze-input-capability-and-adding-eye-gaze-data-provider"></a><span data-ttu-id="2603c-102">Sicherstellen der Funktion der Eingabe durch Anvisieren mit den Augen Hinzufügen eines Eye Gaze-Datenanbieters</span><span class="sxs-lookup"><span data-stu-id="2603c-102">Ensuring Eye Gaze Input capability and adding Eye Gaze Data Provider</span></span>

<span data-ttu-id="2603c-103">Wählen Sie im Unity-Menü „Mixed Reality Toolkit > Utilities > **Configure Unity Project**“ (Mixed Reality Toolkit > Hilfsprogramme > Unity-Projekt konfigurieren) aus, um das Fenster **MRTK Project Configurator** (MRTK-Projektkonfigurator) zu öffnen, und überprüfen Sie dann im Abschnitt **UWP Capabilities** (UWP-Funktionen), ob die Funktion **Enable Eye Gaze Input** (Eingabe durch Anvisieren mit den Augen) grau dargestellt wird:</span><span class="sxs-lookup"><span data-stu-id="2603c-103">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Eye Gaze Input Capability** is greyed out:</span></span>

![Unity MRTK-Projektkonfigurator-Fenster](../images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="2603c-105">Die Funktion zur Eingabe durch Anvisieren hätte im Rahmen der Anweisungen zum [Übernehmen der Einstellungen des MRTK-Projektkonfigurators](../mr-learning-base-02.md#configuring-the-unity-project) aktiviert werden sollen, während der ursprünglichen Konfiguration des Unity-Projekts zu Beginn dieser Tutorialreihe.</span><span class="sxs-lookup"><span data-stu-id="2603c-105">The Gaze Input capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#configuring-the-unity-project) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="2603c-106">Sollte sie nicht aktiviert sein, achten Sie darauf, sie jetzt zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="2603c-106">However, if it is not enabled, make sure you enable it now.</span></span>

<span data-ttu-id="2603c-107">Wählen Sie im Hierarchiefenster das MixedRealityToolkit-Objekt aus, und navigieren Sie dann im Inspektorfenster zur Registerkarte „Eingabe“:</span><span class="sxs-lookup"><span data-stu-id="2603c-107">In the Hierarchy window, select the MixedRealityToolkit object, then in the Inspector window, navigate to the Input tab:</span></span>

* <span data-ttu-id="2603c-108">Erweitern Sie die **Eingabedatenanbieter**, und klicken Sie auf die Schaltfläche **+ Datenanbieter hinzufügen**, um einen neuen Datenanbieter hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="2603c-108">Expand the **Input Data Providers** , click the **+ Add Data Provider** button to add a new Data Provider</span></span>

![Hinzufügen von Augendatenanbieter 1](../images/mr-learning-base/base-08-section1-step1-2.png)

<span data-ttu-id="2603c-110">Weisen Sie **Microsoft.MixedReality.ToolKit.WindowsMixedReality.Input** > **WindowsMixedRealityEyeGazeProvider** dem Feld **Typ** des neuen Datenanbieters zu.</span><span class="sxs-lookup"><span data-stu-id="2603c-110">Assign **Microsoft.MixedReality.ToolKit.WindowsMixedReality.Input** > **WindowsMixedRealityEyeGazeProvider** to the **Type** field of the new Data Provider.</span></span>

![Hinzufügen von Augendatenanbieter 2](../images/mr-learning-base/base-08-section1-step1-3.png)

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="2603c-112">Unity 2020 und OpenXR</span><span class="sxs-lookup"><span data-stu-id="2603c-112">Unity 2020 + OpenXR</span></span>](#tab/openxr)

## <a name="ensuring-eye-gaze-input-capability-and-adding-eye-gaze-data-provider"></a><span data-ttu-id="2603c-113">Sicherstellen der Funktion der Eingabe durch Anvisieren mit den Augen Hinzufügen eines Eye Gaze-Datenanbieters</span><span class="sxs-lookup"><span data-stu-id="2603c-113">Ensuring Eye Gaze Input capability and adding Eye Gaze Data Provider</span></span>

<span data-ttu-id="2603c-114">Wählen Sie im Hierarchiefenster das MixedRealityToolkit-Objekt aus, und navigieren Sie dann im Inspektorfenster zur Registerkarte „Eingabe“:</span><span class="sxs-lookup"><span data-stu-id="2603c-114">In the Hierarchy window, select the MixedRealityToolkit object, then in the Inspector window, navigate to the Input tab:</span></span>

* <span data-ttu-id="2603c-115">Erweitern Sie die **Eingabedatenanbieter**, und klicken Sie auf die Schaltfläche **+ Datenanbieter hinzufügen**, um einen neuen Datenanbieter hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="2603c-115">Expand the **Input Data Providers** , click the **+ Add Data Provider** button to add a new Data Provider</span></span>

![Hinzufügen von Augendatenanbieter 1](../images/mr-learning-base/base-08-section1-step1-2openxr.png)

<span data-ttu-id="2603c-117">Weisen Sie **Microsoft.MixedReality.ToolKit.XRSDK.OpenXR.Input** > **WindowsMixedRealityEyeGazeProvider** dem Feld **Typ** des neuen Datenanbieters zu.</span><span class="sxs-lookup"><span data-stu-id="2603c-117">Assign **Microsoft.MixedReality.ToolKit.XRSDK.OpenXR.Input** > **WindowsMixedRealityEyeGazeProvider** to the **Type** field of the new Data Provider.</span></span>

![Hinzufügen von Augendatenanbieter 2](../images/mr-learning-base/base-08-section1-step1-3openxr.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="2603c-119">Legacy-WSA</span><span class="sxs-lookup"><span data-stu-id="2603c-119">Legacy WSA</span></span>](#tab/wsa)

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a><span data-ttu-id="2603c-120">Sicherstellen, dass die Eingabe durch Anvisieren mit den Augen aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="2603c-120">Ensuring the Eye Gaze Input capability is enabled</span></span>

<span data-ttu-id="2603c-121">Wählen Sie im Unity-Menü „Mixed Reality Toolkit > Utilities > **Configure Unity Project**“ (Mixed Reality Toolkit > Hilfsprogramme > Unity-Projekt konfigurieren) aus, um das Fenster **MRTK Project Configurator** (MRTK-Projektkonfigurator) zu öffnen, und überprüfen Sie dann im Abschnitt **UWP Capabilities** (UWP-Funktionen), ob die Funktion **Enable Eye Gaze Input** (Eingabe durch Anvisieren mit den Augen) grau dargestellt wird:</span><span class="sxs-lookup"><span data-stu-id="2603c-121">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Eye Gaze Input Capability** is greyed out:</span></span>

![Unity MRTK-Projektkonfigurator-Fenster](../images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="2603c-123">Die Funktion zur Eingabe durch Anvisieren hätte im Rahmen der Anweisungen zum [Übernehmen der Einstellungen des MRTK-Projektkonfigurators](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) aktiviert werden sollen, während der ursprünglichen Konfiguration des Unity-Projekts zu Beginn dieser Tutorialreihe.</span><span class="sxs-lookup"><span data-stu-id="2603c-123">The Gaze Input capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="2603c-124">Sollte sie nicht aktiviert sein, achten Sie darauf, sie jetzt zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="2603c-124">However, if it is not enabled, make sure you enable it now.</span></span>
