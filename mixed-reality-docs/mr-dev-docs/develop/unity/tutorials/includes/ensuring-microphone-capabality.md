---
ms.openlocfilehash: 202d96435c437bc7630e82ea99a61f3c2a91c826
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097824"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="3637c-101">Unity 2019/2020 und Windows-XR-Plugin</span><span class="sxs-lookup"><span data-stu-id="3637c-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

## <a name="ensuring-microphone-capability-and-adding-speech-input-data-provider"></a><span data-ttu-id="3637c-102">Sicherstellen der Mikrofonfunktion und Hinzufügen eines Datenanbieters für Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="3637c-102">Ensuring Microphone capability and adding Speech Input data provider</span></span>

<span data-ttu-id="3637c-103">Wählen Sie im Unity-Menü „Mixed Reality Toolkit > Utilities > **Configure Unity Project**“ (Mixed Reality Toolkit > Hilfsprogramme > Unity-Projekt konfigurieren) aus, um das Fenster **MRTK Project Configurator** (MRTK-Projektkonfigurator) zu öffnen, und überprüfen Sie dann im Abschnitt **UWP Capabilities** (UWP-Funktionen), ob die Funktion **Enable Microphone Capability** (Mikrofonfunktion aktivieren) grau dargestellt wird:</span><span class="sxs-lookup"><span data-stu-id="3637c-103">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Microphone Capability** is greyed out:</span></span>

![Aktivieren der Mikrofonfunktion](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="3637c-105">Die Mikrofonfunktion hätte im Rahmen der Anweisungen zum [Übernehmen der Einstellungen des MRTK-Projektkonfigurators](../mr-learning-base-02.md#configuring-the-unity-project) aktiviert werden sollen, während der ursprünglichen Konfiguration des Unity-Projekts zu Beginn dieser Tutorialreihe.</span><span class="sxs-lookup"><span data-stu-id="3637c-105">The Microphone capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#configuring-the-unity-project) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="3637c-106">Sollte sie nicht aktiviert sein, achten Sie darauf, sie jetzt zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="3637c-106">However, if it is not enabled, make sure you enable it now.</span></span>

<span data-ttu-id="3637c-107">Wählen Sie im Hierarchiefenster das MixedRealityToolkit-Objekt aus, und navigieren Sie dann im Inspektorfenster zur Registerkarte „Eingabe“:</span><span class="sxs-lookup"><span data-stu-id="3637c-107">In the Hierarchy window, select the MixedRealityToolkit object, then in the Inspector window, navigate to the Input tab:</span></span>

* <span data-ttu-id="3637c-108">Erweitern Sie die **Eingabedatenanbieter**, und klicken Sie auf die Schaltfläche **+ Datenanbieter hinzufügen**, um einen neuen Datenanbieter hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="3637c-108">Expand the **Input Data Providers** , click the **+ Add Data Provider** button to add a new Data Provider</span></span>

![Datenanbieter zum Hinzufügen neuer Sprachbefehle](../images/mr-learning-base/base-09-section1-step1-2.png)

<span data-ttu-id="3637c-110">Weisen Sie **Microsoft.MixedReality.ToolKit.Windows.Input** > **WindowsSpeechInputProvider** dem Feld **Typ** des neuen Datenanbieters zu.</span><span class="sxs-lookup"><span data-stu-id="3637c-110">Assign **Microsoft.MixedReality.ToolKit.Windows.Input** > **WindowsSpeechInputProvider** to the **Type** field of the new Data Provider.</span></span>

![Hinzufügen neuer Einstellungen für Sprachbefehle](../images/mr-learning-base/base-09-section1-step1-3.png)

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="3637c-112">Unity 2020 und OpenXR</span><span class="sxs-lookup"><span data-stu-id="3637c-112">Unity 2020 + OpenXR</span></span>](#tab/openxr)

## <a name="ensuring-microphone-capability-and-adding-speech-input-data-provider"></a><span data-ttu-id="3637c-113">Sicherstellen der Mikrofonfunktion und Hinzufügen eines Datenanbieters für Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="3637c-113">Ensuring Microphone capability and adding Speech Input data provider</span></span>

<span data-ttu-id="3637c-114">Wählen Sie im Unity-Menü „Mixed Reality Toolkit > Utilities > **Configure Unity Project**“ (Mixed Reality Toolkit > Hilfsprogramme > Unity-Projekt konfigurieren) aus, um das Fenster **MRTK Project Configurator** (MRTK-Projektkonfigurator) zu öffnen, und überprüfen Sie dann im Abschnitt **UWP Capabilities** (UWP-Funktionen), ob die Funktion **Enable Microphone Capability** (Mikrofonfunktion aktivieren) grau dargestellt wird:</span><span class="sxs-lookup"><span data-stu-id="3637c-114">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Microphone Capability** is greyed out:</span></span>

![Aktivieren der Mikrofonfunktion für OpenXR](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="3637c-116">Die Mikrofonfunktion hätte im Rahmen der Anweisungen zum [Übernehmen der Einstellungen des MRTK-Projektkonfigurators](../mr-learning-base-02.md#configuring-the-unity-project) aktiviert werden sollen, während der ursprünglichen Konfiguration des Unity-Projekts zu Beginn dieser Tutorialreihe.</span><span class="sxs-lookup"><span data-stu-id="3637c-116">The Microphone capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#configuring-the-unity-project) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="3637c-117">Sollte sie nicht aktiviert sein, achten Sie darauf, sie jetzt zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="3637c-117">However, if it is not enabled, make sure you enable it now.</span></span>

<span data-ttu-id="3637c-118">Wählen Sie im Hierarchiefenster das MixedRealityToolkit-Objekt aus, und navigieren Sie dann im Inspektorfenster zur Registerkarte „Eingabe“:</span><span class="sxs-lookup"><span data-stu-id="3637c-118">In the Hierarchy window, select the MixedRealityToolkit object, then in the Inspector window, navigate to the Input tab:</span></span>

* <span data-ttu-id="3637c-119">Erweitern Sie die **Eingabedatenanbieter**, und klicken Sie auf die Schaltfläche **+ Datenanbieter hinzufügen**, um einen neuen Datenanbieter hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="3637c-119">Expand the **Input Data Providers** , click the **+ Add Data Provider** button to add a new Data Provider</span></span>

![Hinzufügen neuer Sprachbefehle für OpenXR](../images/mr-learning-base/base-09-section1-step1-2.png)

<span data-ttu-id="3637c-121">Weisen Sie **Microsoft.MixedReality.ToolKit.Windows.Input** > **WindowsSpeechInputProvider** dem Feld **Typ** des neuen Datenanbieters zu.</span><span class="sxs-lookup"><span data-stu-id="3637c-121">Assign **Microsoft.MixedReality.ToolKit.Windows.Input** > **WindowsSpeechInputProvider** to the **Type** field of the new Data Provider.</span></span>

![Hinzufügen neuer Sprachbefehle für OpenXR-Einstellungen](../images/mr-learning-base/base-09-section1-step1-3.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="3637c-123">Legacy-WSA</span><span class="sxs-lookup"><span data-stu-id="3637c-123">Legacy WSA</span></span>](#tab/wsa)

## <a name="ensuring-the-microphone-capability-is-enabled"></a><span data-ttu-id="3637c-124">Sicherstellen, dass die Mikrofonfunktion aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="3637c-124">Ensuring the Microphone capability is enabled</span></span>

<span data-ttu-id="3637c-125">Wählen Sie im Unity-Menü „Mixed Reality Toolkit > Utilities > **Configure Unity Project**“ (Mixed Reality Toolkit > Hilfsprogramme > Unity-Projekt konfigurieren) aus, um das Fenster **MRTK Project Configurator** (MRTK-Projektkonfigurator) zu öffnen, und überprüfen Sie dann im Abschnitt **UWP Capabilities** (UWP-Funktionen), ob die Funktion **Enable Microphone Capability** (Mikrofonfunktion aktivieren) grau dargestellt wird:</span><span class="sxs-lookup"><span data-stu-id="3637c-125">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Microphone Capability** is greyed out:</span></span>

![Aktivieren der Mikrofonfunktion](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="3637c-127">Die Mikrofonfunktion hätte im Rahmen der Anweisungen zum [Übernehmen der Einstellungen des MRTK-Projektkonfigurators](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) aktiviert werden sollen, während der ursprünglichen Konfiguration des Unity-Projekts zu Beginn dieser Tutorialreihe.</span><span class="sxs-lookup"><span data-stu-id="3637c-127">The Microphone capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="3637c-128">Sollte sie nicht aktiviert sein, achten Sie darauf, sie jetzt zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="3637c-128">However, if it is not enabled, make sure you enable it now.</span></span>
