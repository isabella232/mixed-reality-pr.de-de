---
title: Verwenden von Sprachbefehlen
description: In diesem Kurs erfahren Sie, wie Sie Sprachbefehle in Mixed Reality-Apps mit dem Mixed Reality Toolkit (MRTK) einrichten, erstellen und verwenden.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, MRTK, Mixed Reality Toolkit, UWP, Sprachbefehle, Spracheingabe
ms.localizationpriority: high
ms.openlocfilehash: 3aea23d5a259e555f47ca9ea41d77f345c977aeb
ms.sourcegitcommit: 4fb961beeebd158e2f65b7c714c5e471454400a3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2021
ms.locfileid: "105982935"
---
# <a name="9-using-speech-commands"></a><span data-ttu-id="e05f7-104">9. Verwenden von Sprachbefehlen</span><span class="sxs-lookup"><span data-stu-id="e05f7-104">9. Using speech commands</span></span>

<span data-ttu-id="e05f7-105">In diesem Tutorial erfahren Sie, wie Sie Sprachbefehle erstellen und diese global steuern.</span><span class="sxs-lookup"><span data-stu-id="e05f7-105">In this tutorial, you will learn how to create speech commands and how to control them globally.</span></span> <span data-ttu-id="e05f7-106">Außerdem erfahren Sie, wie Sie lokale Sprachbefehle steuern, die es erfordern, dass der Benutzer das Objekt ansieht, das den Sprachbefehl steuert.</span><span class="sxs-lookup"><span data-stu-id="e05f7-106">You will also learn how to control local speech commands that require the user to look at the object that controls the speech command.</span></span>

## <a name="objectives"></a><span data-ttu-id="e05f7-107">Ziele</span><span class="sxs-lookup"><span data-stu-id="e05f7-107">Objectives</span></span>

* <span data-ttu-id="e05f7-108">Erfahren, wie Sprachbefehle erstellt werden</span><span class="sxs-lookup"><span data-stu-id="e05f7-108">Learn how to create speech commands</span></span>
* <span data-ttu-id="e05f7-109">Erfahren, wie Sie Sprachbefehle global und lokal gesteuert werden</span><span class="sxs-lookup"><span data-stu-id="e05f7-109">Learn how to control speech commands globally and locally</span></span>

[!INCLUDE[](includes/ensuring-microphone-capabality.md)]

## <a name="creating-speech-commands"></a><span data-ttu-id="e05f7-110">Erstellen von Sprachbefehlen</span><span class="sxs-lookup"><span data-stu-id="e05f7-110">Creating speech commands</span></span>

<span data-ttu-id="e05f7-111">Wählen Sie im Hierarchiefenster das **MixedRealityToolkit**-Objekt und dann im Inspektorfenster die Registerkarte „MixedRealityToolkit > **Input**“ (MixedRealityToolkit > Eingabe) aus. Führen Sie dann die folgenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="e05f7-111">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the MixedRealityToolkit > **Input** tab and take the following steps:</span></span>

* <span data-ttu-id="e05f7-112">Klappen Sie den Abschnitt **Speech** (Sprache) auf</span><span class="sxs-lookup"><span data-stu-id="e05f7-112">Expand the **Speech** section</span></span>
* <span data-ttu-id="e05f7-113">Klonen Sie das Profil **DefaultMixedRealitySpeechCommandsProfile**, und geben Sie ihm einen passenden Namen, beispielsweise _GettingStarted_MixedRealitySpeechCommandsProfile_</span><span class="sxs-lookup"><span data-stu-id="e05f7-113">Clone the **DefaultMixedRealitySpeechCommandsProfile** and give it a suitable name, for example, _GettingStarted_MixedRealitySpeechCommandsProfile_</span></span>
* <span data-ttu-id="e05f7-114">Vergewissern Sie sich, dass **Start Behaviour** (Startverhalten) auf **Auto Start** (Automatischer Start) festgelegt ist</span><span class="sxs-lookup"><span data-stu-id="e05f7-114">Verify that **Start Behaviour** is set to **Auto Start**</span></span>

![Erstellen von Sprachbefehlen](images/mr-learning-base/base-09-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="e05f7-116">Wenn Sie eine Auffrischung zum Klonen von MRTK-Profilen benötigen, lesen Sie die Anweisungen in [Konfigurieren der MRTK-Profile](mr-learning-base-03.md).</span><span class="sxs-lookup"><span data-stu-id="e05f7-116">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the MRTK profiles](mr-learning-base-03.md) instructions.</span></span>

<span data-ttu-id="e05f7-117">Klicken Sie im Abschnitt „Speech > **Speech Commands**“ (Sprache > Sprachbefehle) vier Mal auf die Schaltfläche **+ Add a New Speech Command** (Neuen Sprachbefehl hinzufügen), um unten in der Liste der vorhandenen Sprachbefehle einen neuen Sprachbefehl hinzuzufügen, und geben Sie dann in den **Keyword**-Feldern (Schlüsselwort) die folgenden Ausdrücke ein:</span><span class="sxs-lookup"><span data-stu-id="e05f7-117">In the Speech > **Speech Commands** section, click the **+ Add a New Speech Command** button four times to add four new speech commands to the list of the existing speech commands, then in the **Keyword** fields enter the following phrases:</span></span>

* <span data-ttu-id="e05f7-118">Enable Indicator (Indikator aktivieren)</span><span class="sxs-lookup"><span data-stu-id="e05f7-118">Enable Indicator</span></span>
* <span data-ttu-id="e05f7-119">Enable Tap to Place (Zum Platzieren tippen aktivieren)</span><span class="sxs-lookup"><span data-stu-id="e05f7-119">Enable Tap to Place</span></span>
* <span data-ttu-id="e05f7-120">Aktivieren des Begrenzungssteuerelements</span><span class="sxs-lookup"><span data-stu-id="e05f7-120">Enable Bounds Control</span></span>
* <span data-ttu-id="e05f7-121">Deaktivieren des Begrenzungssteuerelements</span><span class="sxs-lookup"><span data-stu-id="e05f7-121">Disable Bounds Control</span></span>

![Hinzufügen neuer Sprachbefehle](images/mr-learning-base/base-09-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="e05f7-123">Wenn Ihr Computer nicht über ein Mikrofon verfügt, können Sie den Sprachbefehlen einen Tastencode zuweisen, sodass Sie sie durch Drücken der entsprechenden Taste auslösen können.</span><span class="sxs-lookup"><span data-stu-id="e05f7-123">If your computer does not have a microphone you can assign a KeyCode to the speech commands, which will let you trigger them when the corresponding key is pressed.</span></span>

## <a name="controlling-speech-commands"></a><span data-ttu-id="e05f7-124">Steuern von Sprachbefehlen</span><span class="sxs-lookup"><span data-stu-id="e05f7-124">Controlling speech commands</span></span>

<span data-ttu-id="e05f7-125">Navigieren Sie im Projektfenster zum Ordner **Package** > **Mixed Reality Toolkit Foundation** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** (Paket > Mixed Reality Toolkit Foundation > SDK > Features > UX > Prefabs > QuickInfo), um die QuickInfo-Prefabs zu suchen:</span><span class="sxs-lookup"><span data-stu-id="e05f7-125">In the Project window, navigate to the **Package** > **Mixed Reality Toolkit Foundation** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** folder to locate the tooltip prefabs:</span></span>

![Öffnen des QuickInfo-Ordners](images/mr-learning-base/base-09-section3-step1-1.png)

<span data-ttu-id="e05f7-127">Klicken Sie im Hierarchiefenster mit der rechten Maustaste auf eine leere Stelle, und wählen Sie **Create Empty** (Leer erstellen) aus, um Ihrer Szene ein leeres Objekt hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="e05f7-127">In the Hierarchy window, right-click on an empty spot and select **Create Empty** to add an empty object to your scene.</span></span>

<span data-ttu-id="e05f7-128">Benennen Sie das Objekt **SpeechInputHandler_Global**, verwenden Sie dann im Inspektorfenster die Schaltfläche **Add Component** (Komponente hinzufügen), um die **SpeechInputHandler**-Komponente hinzuzufügen, und konfigurieren Sie sie dann wie folgt:</span><span class="sxs-lookup"><span data-stu-id="e05f7-128">Name the object **SpeechInputHandler_Global**, then in the Inspector window, use the **Add Component** button to add the **SpeechInputHandler** component and configure it as follows:</span></span>

* <span data-ttu-id="e05f7-129">**Deaktivieren** Sie das Kontrollkästchen **Is Focus Required** (Ist Fokus erforderlich), damit der Benutzer das Objekt nicht anblicken muss, um den Sprachbefehl mit der SpeechInputHandler-Komponente auszulösen</span><span class="sxs-lookup"><span data-stu-id="e05f7-129">**Uncheck** the **Is Focus Required** checkbox, so the user is not required to look at the object with the SpeechInputHandler component to trigger the speech command</span></span>
* <span data-ttu-id="e05f7-130">Weisen Sie im Projektfenster das Prefab **SpeechConfirmation Tooltip** dem Feld **Speech Confirmation Tooltip Prefab** zu, damit dieses Prefab angezeigt wird, wenn ein Sprachbefehl erkannt wird</span><span class="sxs-lookup"><span data-stu-id="e05f7-130">From the Project window, assign the **SpeechConfirmation Tooltip** prefab to the **Speech Confirmation Tooltip Prefab** field, to have this prefab appear when a speech command is recognized</span></span>

![Konfigurieren der Spracheingabe-Handlerkomponente](images/mr-learning-base/base-09-section3-step1-2.png)

<span data-ttu-id="e05f7-132">Klicken Sie in der SpeechInputHandler-Komponente drei Mal auf das kleine **+** -Symbol, um drei Schlüsselwortelemente hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="e05f7-132">On the SpeechInputHandler component, click the small **+** icon three times to add three keyword elements:</span></span>

![Hinzufügen von Schlüsselwortelementen zum Spracheingabehandler](images/mr-learning-base/base-09-section3-step1-3.png)

<span data-ttu-id="e05f7-134">Klappen Sie **Element 0** auf, und konfigurieren Sie es wie folgt:</span><span class="sxs-lookup"><span data-stu-id="e05f7-134">Expand **Element 0** and configure it as follows:</span></span>

* <span data-ttu-id="e05f7-135">Geben Sie im Feld **Keyword** (Schlüsselwort) **Enable Indicator** (Indikator aktivieren) ein, um auf den Sprachbefehl „Enable Indicator“ (Indikator aktivieren) zu verweisen, den Sie im vorherigen Abschnitt erstellt haben</span><span class="sxs-lookup"><span data-stu-id="e05f7-135">In the **Keyword** field, enter **Enable Indicator**, to reference the Enable Indicator speech command you created in the previous section</span></span>
* <span data-ttu-id="e05f7-136">Klicken Sie auf das kleine **+** -Symbol, um ein Ereignis hinzuzufügen</span><span class="sxs-lookup"><span data-stu-id="e05f7-136">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="e05f7-137">Weisen Sie im Hierarchiefenster das **Indicator**-Objekt (Indikator) dem Feld **None (Object)** (Ohne (Objekt)) zu</span><span class="sxs-lookup"><span data-stu-id="e05f7-137">From the Hierarchy window, assign the **Indicator** object to the **None (Object)** field</span></span>
* <span data-ttu-id="e05f7-138">Wählen Sie in der Dropdownliste **No Function** (Keine Funktion) **GameObject** > **SetActive (bool)** aus, um diese Funktion als die beim Auslösen des Ereignisses auszuführende Aktion festzulegen</span><span class="sxs-lookup"><span data-stu-id="e05f7-138">From the **No Function** dropdown, select **GameObject** > **SetActive (bool)** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="e05f7-139">Aktivieren Sie das Argumentkontrollkästchen, so dass es **aktiviert** ist</span><span class="sxs-lookup"><span data-stu-id="e05f7-139">Check the argument checkbox, so it is **checked**</span></span>

![Konfigurieren von Schlüsselwortelement 0](images/mr-learning-base/base-09-section3-step1-4.png)

<span data-ttu-id="e05f7-141">Klappen Sie **Element 1** auf, und konfigurieren Sie es wie folgt:</span><span class="sxs-lookup"><span data-stu-id="e05f7-141">Expand **Element 1** and configure it as follows:</span></span>

* <span data-ttu-id="e05f7-142">Geben Sie im Feld **Keyword** (Schlüsselwort) **Enable Bounds Control**  (Begrenzungssteuerelement aktivieren) ein, um auf den Sprachbefehl „Enable Bounds Control“ (Begrenzungssteuerelement aktivieren) zu verweisen, den Sie im vorherigen Abschnitt erstellt haben</span><span class="sxs-lookup"><span data-stu-id="e05f7-142">In the **Keyword** field, enter **Enable Bounds Control**, to reference the Enable Bounds Control command you created in the previous section</span></span>
* <span data-ttu-id="e05f7-143">Klicken Sie auf das kleine **+** -Symbol, um ein Ereignis hinzuzufügen</span><span class="sxs-lookup"><span data-stu-id="e05f7-143">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="e05f7-144">Weisen Sie im Hierarchiefenster das **RoverExplorer**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu</span><span class="sxs-lookup"><span data-stu-id="e05f7-144">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="e05f7-145">Wählen Sie in der Dropdownliste **No Function** (Ohne Funktion) **BoundsControl** > **bool enabled** aus, um diesen Eigenschaftswert zu aktualisieren, wenn das Ereignis ausgelöst wird</span><span class="sxs-lookup"><span data-stu-id="e05f7-145">From the **No Function** dropdown, select **BoundsControl** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="e05f7-146">Aktivieren Sie das Argumentkontrollkästchen, so dass es **aktiviert** ist</span><span class="sxs-lookup"><span data-stu-id="e05f7-146">Check the argument checkbox, so it is **checked**</span></span>
* <span data-ttu-id="e05f7-147">Klicken Sie auf das kleine **+** -Symbol, um ein weiteres Ereignis hinzuzufügen</span><span class="sxs-lookup"><span data-stu-id="e05f7-147">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="e05f7-148">Weisen Sie im Hierarchiefenster das **RoverExplorer**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu</span><span class="sxs-lookup"><span data-stu-id="e05f7-148">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="e05f7-149">Wählen Sie in der Dropdownliste **No Function** (Ohne Funktion) **ObjectManipulator** > **bool Enabled** aus, um diesen Eigenschaftswert zu aktualisieren, wenn das Ereignis ausgelöst wird</span><span class="sxs-lookup"><span data-stu-id="e05f7-149">From the **No Function** dropdown, select **ObjectManipulator** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="e05f7-150">Aktivieren Sie das Argumentkontrollkästchen, so dass es **aktiviert** ist</span><span class="sxs-lookup"><span data-stu-id="e05f7-150">Check the argument checkbox, so it is **checked**</span></span>

![Konfigurieren von Schlüsselwortelement 1](images/mr-learning-base/base-09-section3-step1-5.png)

<span data-ttu-id="e05f7-152">Klappen Sie **Element 2** auf, und konfigurieren Sie es wie folgt:</span><span class="sxs-lookup"><span data-stu-id="e05f7-152">Expand **Element 2** and configure it as follows:</span></span>

* <span data-ttu-id="e05f7-153">Geben Sie im Feld **Keyword** (Schlüsselwort) **Disable Bounds Control**  (Begrenzungssteuerelement deaktivieren) ein, um auf den Sprachbefehl „Disable Bounds Control“ (Begrenzungssteuerelement deaktivieren) zu verweisen, den Sie im vorherigen Abschnitt erstellt haben</span><span class="sxs-lookup"><span data-stu-id="e05f7-153">In the **Keyword** field, enter **Disable Bounds Control**, to reference the Disable Bounds Control command you created in the previous section</span></span>
* <span data-ttu-id="e05f7-154">Klicken Sie auf das kleine **+** -Symbol, um ein Ereignis hinzuzufügen</span><span class="sxs-lookup"><span data-stu-id="e05f7-154">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="e05f7-155">Weisen Sie im Hierarchiefenster das **RoverExplorer**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu</span><span class="sxs-lookup"><span data-stu-id="e05f7-155">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="e05f7-156">Wählen Sie in der Dropdownliste **No Function** (Ohne Funktion) **BoundsControl** > **bool enabled** aus, um diesen Eigenschaftswert zu aktualisieren, wenn das Ereignis ausgelöst wird</span><span class="sxs-lookup"><span data-stu-id="e05f7-156">From the **No Function** dropdown, select **BoundsControl** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="e05f7-157">Vergewissern Sie sich, dass das Argumentkontrollkästchen **deaktiviert** ist</span><span class="sxs-lookup"><span data-stu-id="e05f7-157">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="e05f7-158">Klicken Sie auf das kleine **+** -Symbol, um ein weiteres Ereignis hinzuzufügen</span><span class="sxs-lookup"><span data-stu-id="e05f7-158">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="e05f7-159">Weisen Sie im Hierarchiefenster das **RoverExplorer**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu</span><span class="sxs-lookup"><span data-stu-id="e05f7-159">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="e05f7-160">Wählen Sie in der Dropdownliste **No Function** (Ohne Funktion) **ObjectManipulator** > **bool Enabled** aus, um diesen Eigenschaftswert zu aktualisieren, wenn das Ereignis ausgelöst wird</span><span class="sxs-lookup"><span data-stu-id="e05f7-160">From the **No Function** dropdown, select **ObjectManipulator** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="e05f7-161">Vergewissern Sie sich, dass das Argumentkontrollkästchen **deaktiviert** ist</span><span class="sxs-lookup"><span data-stu-id="e05f7-161">Verify that the argument checkbox is **unchecked**</span></span>

![Konfigurieren von Schlüsselwortelement 2](images/mr-learning-base/base-09-section3-step1-6.png)

<span data-ttu-id="e05f7-163">Wählen Sie im Hierarchiefenster das Objekt RoverExplorer > **RoverAssembly** aus, verwenden Sie dann im Inspektorfenster die Schaltfläche **Add Component** (Komponente hinzufügen), um die Komponente **SpeechInputHandler** hinzuzufügen, und konfigurieren Sie sie wie folgt:</span><span class="sxs-lookup"><span data-stu-id="e05f7-163">In the Hierarchy window, select the RoverExplorer > **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the **SpeechInputHandler** component and configure it as follows:</span></span>

* <span data-ttu-id="e05f7-164">Vergewissern Sie sich, dass das Kontrollkästchen **Is Focus Required** (Ist Fokus erforderlich) **aktiviert** ist, damit der Benutzer das Objekt nicht anblicken muss, um den Sprachbefehl mit der SpeechInputHandler-Komponente, d. h. der RoverAssembly, auszulösen</span><span class="sxs-lookup"><span data-stu-id="e05f7-164">Verify that the **Is Focus Required** checkbox is **check**, so the user is required to look at the object with the SpeechInputHandler component, i.e., the RoverAssembly, to trigger the speech command</span></span>
* <span data-ttu-id="e05f7-165">Weisen Sie im Projektfenster das Prefab **SpeechConfirmation Tooltip** dem Feld **Speech Confirmation Tooltip Prefab** zu, damit dieses Prefab angezeigt wird, wenn ein Sprachbefehl erkannt wird</span><span class="sxs-lookup"><span data-stu-id="e05f7-165">From the Project window, assign the **SpeechConfirmation Tooltip** prefab to the **Speech Confirmation Tooltip Prefab** field, to have this prefab appear when a speech command is recognized</span></span>

![Hinzufügen des Spracheingabehandlers zur Rover-Baugruppe](images/mr-learning-base/base-09-section3-step1-7.png)

<span data-ttu-id="e05f7-167">Klicken Sie in der SpeechInputHandler-Komponente auf das kleine **+** -Symbol, um ein Stichwortelement hinzuzufügen, klappen Sie das neu erstellte Element auf, und konfigurieren Sie es wie folgt:</span><span class="sxs-lookup"><span data-stu-id="e05f7-167">On the SpeechInputHandler component, click the small **+** icon to add a keyword element, expand the newly created element, then configure it as follows:</span></span>

* <span data-ttu-id="e05f7-168">Geben Sie im Feld **Keyword** (Schlüsselwort) **Enable Tap to Place** (Zum Platzieren tippen aktivieren) ein, um auf den Sprachbefehl „Enable Tap to Place“ (Zum Platzieren tippen aktivieren) zu verweisen, den Sie im vorherigen Abschnitt erstellt haben</span><span class="sxs-lookup"><span data-stu-id="e05f7-168">In the **Keyword** field, enter **Enable Tap to Place**, to reference the Enable Tap to Place command you created in the previous section</span></span>
* <span data-ttu-id="e05f7-169">Klicken Sie auf das kleine **+** -Symbol, um ein Ereignis hinzuzufügen</span><span class="sxs-lookup"><span data-stu-id="e05f7-169">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="e05f7-170">Weisen Sie im Hierarchiefenster das Objekt selbst, d. h. das gleiche **RoverAssembly**-Objekt, dem Feld **None (Object)** (Ohne (Objekt)) zu</span><span class="sxs-lookup"><span data-stu-id="e05f7-170">From the Hierarchy window, assign the object itself, i.e., the same **RoverAssembly** object, to the **None (Object)** field</span></span>
* <span data-ttu-id="e05f7-171">Wählen Sie in der Dropdownliste **No Function** (Ohne Funktion) **TapToPlace** > **bool Enabled** aus, um diesen Eigenschaftswert zu aktualisieren, wenn das Ereignis ausgelöst wird</span><span class="sxs-lookup"><span data-stu-id="e05f7-171">From the **No Function** dropdown, select **TapToPlace** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="e05f7-172">Aktivieren Sie das Argumentkontrollkästchen, so dass es **aktiviert** ist</span><span class="sxs-lookup"><span data-stu-id="e05f7-172">Check the argument checkbox, so it is **checked**</span></span>

![Konfigurieren des Spracheingabehandlers in der Rover-Baugruppe](images/mr-learning-base/base-09-section3-step1-8.png)

## <a name="congratulations"></a><span data-ttu-id="e05f7-174">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="e05f7-174">Congratulations</span></span>

<span data-ttu-id="e05f7-175">In diesem Tutorial haben Sie erfahren, wie Sie Sprachbefehle erstellen und diese global steuern.</span><span class="sxs-lookup"><span data-stu-id="e05f7-175">In this tutorial, you learned how to create speech commands and how to control them globally.</span></span> <span data-ttu-id="e05f7-176">Außerdem haben Sie erfahren, wie Sie lokale Sprachbefehle steuern, die es erfordern, dass der Benutzer das Objekt ansieht, das den Sprachbefehl steuert.</span><span class="sxs-lookup"><span data-stu-id="e05f7-176">You also learned how to control local speech commands that require the user to look at the object that controls the speech command.</span></span>

<span data-ttu-id="e05f7-177">Damit ist die Reihe der [Tutorials zu den ersten Schritten](mr-learning-base-01.md) zugleich abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="e05f7-177">This also concludes the [Getting started tutorials](mr-learning-base-01.md) series.</span></span> <span data-ttu-id="e05f7-178">Im Lauf dieser Tutorials haben Sie erfolgreich von Grund auf ein vollständiges Mixed Reality-Erlebnis mithilfe des MRTK erstellt.</span><span class="sxs-lookup"><span data-stu-id="e05f7-178">Through these tutorials, you have successfully built a complete mixed reality experience from scratch using the MRTK.</span></span>

<span data-ttu-id="e05f7-179">In den beiden nächsten Tutorialreihen, den [Azure Spatial Anchors-Tutorials](mr-learning-asa-01.md) und den [Tutorials zu den Mehrbenutzerfunktionen](mr-learning-sharing-01.md), erfahren Sie zunächst, wie Sie Azure Spatial Anchors in Ihr Projekt integrieren, um das von Ihnen erstellte Rover Explorer-Erlebnis in der realen Welt zu verankern.</span><span class="sxs-lookup"><span data-stu-id="e05f7-179">In the next two tutorial series, [Azure Spatial Anchors tutorials](mr-learning-asa-01.md) and [Multi-user capabilities tutorials](mr-learning-sharing-01.md), you will first learn how to integrate Azure Spatial Anchors into your project to anchor the Rover Explorer experience you created in the real world.</span></span> <span data-ttu-id="e05f7-180">Anschließend erfahren Sie, wie Sie Ihrem Projekt Mehrbenutzerfunktionen hinzufügen, um Benutzer- und Objektbewegungen in Echtzeit zu teilen.</span><span class="sxs-lookup"><span data-stu-id="e05f7-180">Then, you will learn how to add multi-user capabilities to your project to share user and object movements in real-time.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="e05f7-181">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="e05f7-181">Next Development Checkpoint</span></span>

<span data-ttu-id="e05f7-182">Wenn Sie dem Weg der Unity-Entwicklungsprüfpunkte folgen, den wir entworfen haben, besteht Ihre nächste Aufgabe darin, sich mit den Grundbausteinen von Mixed Reality-Anwendungen vertraut zu machen.</span><span class="sxs-lookup"><span data-stu-id="e05f7-182">If you're following the Unity development checkpoint journey we've laid out, your next task is to familiarize yourself with core building blocks of Mixed Reality apps.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e05f7-183">Grundlegende Interaktionen</span><span class="sxs-lookup"><span data-stu-id="e05f7-183">Basic interactions</span></span>](../../../out-of-scope/mrtk-101.md)

<span data-ttu-id="e05f7-184">Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](../unity-development-overview.md#1-getting-started) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="e05f7-184">You can always go back to the [Unity development checkpoints](../unity-development-overview.md#1-getting-started) at any time.</span></span>