---
title: Verwenden von Eye Tracking
description: In diesem Kurs erfahren Sie, wie Sie Eye Tracking in Ihren Mixed Reality-Apps mit dem Mixed Reality Toolkit (MRTK) verwenden.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, MRTK, Mixed Reality Toolkit, UWP, Eye Tracking
ms.localizationpriority: high
ms.openlocfilehash: bf7bd266eb471193979c588d97d14dd37aed175e
ms.sourcegitcommit: 4fb961beeebd158e2f65b7c714c5e471454400a3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2021
ms.locfileid: "105982885"
---
# <a name="8-using-eye-tracking"></a><span data-ttu-id="bff80-104">8. Verwenden von Eye Tracking</span><span class="sxs-lookup"><span data-stu-id="bff80-104">8. Using eye-tracking</span></span>

<span data-ttu-id="bff80-105">In diesem Tutorial erfahren Sie, wie Sie Eye Tracking für HoloLens 2 aktivieren und Objekten Eye Tracking hinzufügen, um Aktionen auszulösen, wenn der Benutzer die Objekte ansieht.</span><span class="sxs-lookup"><span data-stu-id="bff80-105">In this tutorial, you will learn how to enable eye-tracking for HoloLens 2 and add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

> [!NOTE]
> <span data-ttu-id="bff80-106">Wenn Sie dieses Projekt auch in HoloLens (1. Generation) bereitstellen, beachten Sie, dass Eye Tracking nur in HoloLens 2 unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="bff80-106">If you are also deploying this project to HoloLens (1st generation), note that eye-tracking is only supported on HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="bff80-107">Ziele</span><span class="sxs-lookup"><span data-stu-id="bff80-107">Objectives</span></span>

* <span data-ttu-id="bff80-108">Erfahren, wie Eye Tracking für HoloLens 2 aktiviert wird</span><span class="sxs-lookup"><span data-stu-id="bff80-108">Learn how to enable eye-tracking for HoleLens 2</span></span>
* <span data-ttu-id="bff80-109">Erfahren, wie Eye Tracking zum Auslösen von Aktionen verwendet wird</span><span class="sxs-lookup"><span data-stu-id="bff80-109">Learn how to use eye-tracking to trigger action</span></span>

[!INCLUDE[](includes/ensuring-eye-gaze-capabality.md)]

## <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a><span data-ttu-id="bff80-110">Aktivieren des Anvisierens mit den Augen im Blickanbieter</span><span class="sxs-lookup"><span data-stu-id="bff80-110">Enabling eye based gaze in the gaze provider</span></span>

<span data-ttu-id="bff80-111">Wählen Sie im Hierarchiefenster das Objekt **MixedRealityToolkit** aus, wählen Sie dann im Inspektorfenster die Registerkarte „MixedRealityToolkit > **Input**“ aus, und führen Sie die folgenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="bff80-111">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the MixedRealityToolkit > **Input** tab and take the following steps:</span></span>

* <span data-ttu-id="bff80-112">Klonen Sie das Profil **DefaultHoloLens2InputSystemProfile**, und geben Sie ihm einen passenden Namen, beispielsweise _GettingStarted_HoloLens2InputSystemProfile_</span><span class="sxs-lookup"><span data-stu-id="bff80-112">Clone the **DefaultHoloLens2InputSystemProfile** and give it a suitable name, for example, _GettingStarted_HoloLens2InputSystemProfile_</span></span>
* <span data-ttu-id="bff80-113">Erweitern Sie den Abschnitt **Pointers** (Zeiger)</span><span class="sxs-lookup"><span data-stu-id="bff80-113">Expand the **Pointers** section</span></span>
* <span data-ttu-id="bff80-114">Klonen Sie das Profil **DefaultMixedRealityPointerProfile**, und geben Sie ihm einen passenden Namen, beispielsweise _GettingStarted_MixedRealityPointerProfile_</span><span class="sxs-lookup"><span data-stu-id="bff80-114">Clone the **DefaultMixedRealityPointerProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityPointerProfile_</span></span>
* <span data-ttu-id="bff80-115">Suchen Sie den Abschnitt **Gaze Settings** (Blickeinstellungen), und aktivieren Sie das Kontrollkästchen **Is Eye Tracking Enabled** (Ist Eye Tracking aktiviert)</span><span class="sxs-lookup"><span data-stu-id="bff80-115">Locate the **Gaze Settings** section and check the **Is Eye Tracking Enabled** checkbox</span></span>

![Unity MixedRealityToolkit-Komponente mit neu erstellten, angewendeten Profilen und aktiviertem Eye Tracking](images/mr-learning-base/base-08-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="bff80-117">Wenn Sie eine Auffrischung zum Klonen von MRTK-Profilen benötigen, lesen Sie die Anweisungen in [Konfigurieren der MRTK-Profile](mr-learning-base-03.md).</span><span class="sxs-lookup"><span data-stu-id="bff80-117">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the MRTK profiles](mr-learning-base-03.md) instructions.</span></span>

## <a name="enabling-simulated-eye-tracking-for-the-unity-editor"></a><span data-ttu-id="bff80-118">Aktivieren von simuliertem Eye Tracking für den Unity-Editor</span><span class="sxs-lookup"><span data-stu-id="bff80-118">Enabling simulated eye-tracking for the Unity editor</span></span>

<span data-ttu-id="bff80-119">Wählen Sie im Hierarchiefenster das **MixedRealityToolkit**-Objekt aus, und navigieren Sie dann im Inspektorfenster zur Registerkarte **Input** (Eingabe). Führen Sie dann Folgendes aus:</span><span class="sxs-lookup"><span data-stu-id="bff80-119">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, navigate to the **Input** tab, then:</span></span>

* <span data-ttu-id="bff80-120">Klappen Sie den Abschnitt **Input Data Providers** > **Input Simulation Service** (Eingabedatenanbieter > Eingabesimulationsdienst) auf</span><span class="sxs-lookup"><span data-stu-id="bff80-120">Expand the **Input Data Providers** > **Input Simulation Service** section</span></span>
* <span data-ttu-id="bff80-121">Klonen Sie das Profil **DefaultMixedRealityInputSimulationProfile**, und geben Sie ihm einen passenden Namen, beispielsweise _GettingStarted_MixedRealityInputSimulationProfile_</span><span class="sxs-lookup"><span data-stu-id="bff80-121">Clone the **DefaultMixedRealityInputSimulationProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityInputSimulationProfile_</span></span>
* <span data-ttu-id="bff80-122">Suchen Sie die **„Anvisieren mit den Augen“-Simulation**, und legen Sie den **Standardmodus für die „Anvisieren mit den Augen“-Simulation** auf **Vorwärts gerichtete Kameraachse** fest.</span><span class="sxs-lookup"><span data-stu-id="bff80-122">Locate **Eye Gaze Simulation** and set the **Default Eye Gaze Simulation Mode** to **Camera Forward Axis**</span></span>

![Unity mit ausgewähltem TextMeshPro-Objekt](images/mr-learning-base/base-08-section3-step1-1.png)

## <a name="adding-eye-tracking-to-objects"></a><span data-ttu-id="bff80-124">Hinzufügen von Eye Tracking zu Objekten</span><span class="sxs-lookup"><span data-stu-id="bff80-124">Adding eye-tracking to objects</span></span>

<span data-ttu-id="bff80-125">Erweitern Sie im Hierarchie Fenster **RoverExplorer** > **Buttons**, und wählen Sie dann alle drei untergeordneten Schaltflächenobjekte aus:</span><span class="sxs-lookup"><span data-stu-id="bff80-125">In the Hierarchy window, expand the **RoverExplorer** > **Buttons**, then select all three of the child button objects:</span></span>

![Unity mit ausgewähltem Button-Objekt](images/mr-learning-base/base-08-section4-step1-1.png)

<span data-ttu-id="bff80-127">Während die drei Button-Objekte noch ausgewählt sind, verwenden Sie im Inspektorfenster die Schaltfläche **Add Component** (Komponente hinzufügen), um allen ausgewählten Objekten die **EyeTrackingTarget**-Komponente hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="bff80-127">With all three Button objects still selected, in the Inspector window use the **Add Component** button to add the **EyeTrackingTarget** component to all the selected objects:</span></span>

![Unity mit ausgewähltem TextMeshPro-Objekt und hinzugefügten Komponenten](images/mr-learning-base/base-08-section4-step1-2.png)

<span data-ttu-id="bff80-129">Klappen Sie im Hierarchiefenster **RoverExplorer** > **Buttons** > **Hints** > **SeeItSayItLabel** > **TextMeshPro** auf</span><span class="sxs-lookup"><span data-stu-id="bff80-129">In the Hierarchy window, expand **RoverExplorer** > **Buttons** > **Hints** > **SeeItSayItLabel** > **TextMeshPro**</span></span>

<span data-ttu-id="bff80-130">Wählen Sie anschließend im Hierarchiefenster das Schaltflächenobjekt **Hints** (Hinweise) aus, und konfigurieren Sie die **EyeTrackingTarget**-Komponente wie folgt:</span><span class="sxs-lookup"><span data-stu-id="bff80-130">Then in the Hierarchy window, select the **Hints** button object , and configure the **EyeTrackingTarget** component as follows:</span></span>

* <span data-ttu-id="bff80-131">Im Ereignisabschnitt **On Look At Start ()**</span><span class="sxs-lookup"><span data-stu-id="bff80-131">In the **On Look At Start ()** event section</span></span>
  * <span data-ttu-id="bff80-132">Klicken Sie auf das kleine **+** -Symbol, um ein weiteres Ereignis hinzuzufügen</span><span class="sxs-lookup"><span data-stu-id="bff80-132">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="bff80-133">Weisen Sie das **TextMeshPro**-Objekt von der Schaltfläche **Hints** (Hinweise) dem Feld **None (Object)** (Ohne (Objekt)) zu</span><span class="sxs-lookup"><span data-stu-id="bff80-133">Assign the  **TextMeshPro** object from the **Hints** button to the **None (Object)** field</span></span>
  * <span data-ttu-id="bff80-134">Wählen Sie in der Dropdownliste **No Function** (Ohne Funktion) **TextMeshPro** > **float fontSize** aus, um diesen Eigenschaftswert zu aktualisieren, wenn das Ereignis ausgelöst wird</span><span class="sxs-lookup"><span data-stu-id="bff80-134">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="bff80-135">Legen Sie das Argument auf **0,06** fest, um den aktuellen Schriftgrad von 0,04 um 50 % zu erhöhen</span><span class="sxs-lookup"><span data-stu-id="bff80-135">Set the argument to **0.06** to increase the current font size of 0.04 by 50%</span></span>
* <span data-ttu-id="bff80-136">Im Ereignisabschnitt **On Look Away ()**</span><span class="sxs-lookup"><span data-stu-id="bff80-136">In the **On Look Away ()** event section</span></span>
  * <span data-ttu-id="bff80-137">Klicken Sie auf das kleine **+** -Symbol, um ein weiteres Ereignis hinzuzufügen</span><span class="sxs-lookup"><span data-stu-id="bff80-137">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="bff80-138">Weisen Sie das **TextMeshPro**-Objekt von der Schaltfläche **Hints** (Hinweise) dem Feld **None (Object)** (Ohne (Objekt)) zu</span><span class="sxs-lookup"><span data-stu-id="bff80-138">Assign the  **TextMeshPro** object from the **Hints** button to the **None (Object)** field</span></span>
  * <span data-ttu-id="bff80-139">Wählen Sie in der Dropdownliste **No Function** (Ohne Funktion) **TextMeshPro** > **float fontSize** aus, um diesen Eigenschaftswert zu aktualisieren, wenn das Ereignis ausgelöst wird</span><span class="sxs-lookup"><span data-stu-id="bff80-139">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="bff80-140">Legen Sie das Argument auf **0,04** fest, um den Schriftgrad wieder auf 0,04 zurückzusetzen</span><span class="sxs-lookup"><span data-stu-id="bff80-140">Set the argument to **0.04** to reset the font size back to 0.04</span></span>

![Unity mit ausgewähltem Hints TextMeshPro-Objekt und konfigurierter EyeTrackingTarget-Komponente](images/mr-learning-base/base-08-section4-step1-3.png)

<span data-ttu-id="bff80-142">**Wiederholen** Sie diesen Schritt für die Schaltflächenobjekte **Explode** (Explodieren) und **Reset** (Zurücksetzen), um Eyetracking für die verbleibenden Schaltflächen zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="bff80-142">**Repeat** this step for **Explode** and **Reset** button object to configure eye tracking for remaining buttons.</span></span>

<span data-ttu-id="bff80-143">Wenn Sie jetzt in den Spielmodus wechseln, dann die rechte Maustaste drücken und sie gedrückt halten, während Sie die Maus bewegen, bis der Blick auf eine der Schaltflächen trifft, sehen Sie, dass sich der Schriftgrad des Texts um 50 % vergrößert und wieder zur normalen Größe zurückkehrt, wenn Sie den Blick abwenden:</span><span class="sxs-lookup"><span data-stu-id="bff80-143">If you now enter Game mode and then press-and-hold the right mouse button while moving your mouse until the gaze hit's one of the buttons, you will see the text font size increase by 50% and reset back to its original size when looking away:</span></span>

![Geteilte Ansicht des Unity-Wiedergabemodus mit Anvisier-Zugriff per Eye Tracking auf Ziel und Schaltflächenbezeichnung „Explode“](images/mr-learning-base/base-08-section4-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="bff80-145">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="bff80-145">Congratulations</span></span>

<span data-ttu-id="bff80-146">In diesem Tutorial haben Sie erfahren, wie Sie Eye Tracking für HoloLens 2 aktivieren und Objekten Eye Tracking hinzufügen, um Aktionen auszulösen, wenn der Benutzer die Objekte ansieht.</span><span class="sxs-lookup"><span data-stu-id="bff80-146">In this tutorial, you learned how to enable eye-tracking for HoloLens 2 and how to add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bff80-147">Nächstes Tutorial: 9. Verwenden von Sprachbefehlen</span><span class="sxs-lookup"><span data-stu-id="bff80-147">Next Tutorial: 9. Using speech commands</span></span>](mr-learning-base-09.md)
