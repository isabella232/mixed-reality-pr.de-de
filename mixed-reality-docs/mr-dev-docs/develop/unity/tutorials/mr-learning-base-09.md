---
title: Verwenden von Sprachbefehlen
description: In diesem Kurs erfahren Sie, wie Sie Sprachbefehle in Mixed Reality-Apps mit dem Mixed Reality Toolkit (MRTK) einrichten, erstellen und verwenden.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, MRTK, Mixed Reality Toolkit, UWP, Sprachbefehle, Spracheingabe
ms.localizationpriority: high
ms.openlocfilehash: c052c3501ab34811f33f1f6464c8394669eebe77
ms.sourcegitcommit: 04927427226928bd9178da0049d4cef626a6b0bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/21/2021
ms.locfileid: "98635449"
---
# <a name="9-using-speech-commands"></a><span data-ttu-id="b419e-104">9. Verwenden von Sprachbefehlen</span><span class="sxs-lookup"><span data-stu-id="b419e-104">9. Using speech commands</span></span>

<span data-ttu-id="b419e-105">In diesem Tutorial erfahren Sie, wie Sie Sprachbefehle erstellen und diese global steuern.</span><span class="sxs-lookup"><span data-stu-id="b419e-105">In this tutorial, you will learn how to create speech commands and how to control them globally.</span></span> <span data-ttu-id="b419e-106">Außerdem erfahren Sie, wie Sie lokale Sprachbefehle steuern, die es erfordern, dass der Benutzer das Objekt ansieht, das den Sprachbefehl steuert.</span><span class="sxs-lookup"><span data-stu-id="b419e-106">You will also learn how to control local speech commands that require the user to look at the object that controls the speech command.</span></span>

## <a name="objectives"></a><span data-ttu-id="b419e-107">Ziele</span><span class="sxs-lookup"><span data-stu-id="b419e-107">Objectives</span></span>

* <span data-ttu-id="b419e-108">Erfahren, wie Sprachbefehle erstellt werden</span><span class="sxs-lookup"><span data-stu-id="b419e-108">Learn how to create speech commands</span></span>
* <span data-ttu-id="b419e-109">Erfahren, wie Sie Sprachbefehle global und lokal gesteuert werden</span><span class="sxs-lookup"><span data-stu-id="b419e-109">Learn how to control speech commands globally and locally</span></span>

## <a name="ensuring-the-microphone-capability-is-enabled"></a><span data-ttu-id="b419e-110">Sicherstellen, dass die Mikrofonfunktion aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="b419e-110">Ensuring the Microphone capability is enabled</span></span>

<span data-ttu-id="b419e-111">Wählen Sie im Unity-Menü „Mixed Reality Toolkit > Utilities > **Configure Unity Project**“ (Mixed Reality Toolkit > Hilfsprogramme > Unity-Projekt konfigurieren) aus, um das Fenster **MRTK Project Configurator** (MRTK-Projektkonfigurator) zu öffnen, und überprüfen Sie dann im Abschnitt **UWP Capabilities** (UWP-Funktionen), ob die Funktion **Enable Microphone Capability** (Mikrofonfunktion aktivieren) grau dargestellt wird:</span><span class="sxs-lookup"><span data-stu-id="b419e-111">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Microphone Capability** is greyed out:</span></span>

![Aktivieren der Mikrofonfunktion](images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="b419e-113">Die Mikrofonfunktion hätte im Rahmen der Anweisungen zum [Übernehmen der Einstellungen des MRTK-Projektkonfigurators](mr-learning-base-02.md#creating-and-configuring-the-scene) aktiviert werden sollen, während der ursprünglichen Konfiguration des Unity-Projekts zu Beginn dieser Tutorialreihe.</span><span class="sxs-lookup"><span data-stu-id="b419e-113">The Microphone capability should have been enabled during the [Apply the MRTK Project Configurator settings](mr-learning-base-02.md#creating-and-configuring-the-scene) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="b419e-114">Sollte sie nicht aktiviert sein, achten Sie darauf, sie jetzt zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="b419e-114">However, if it is not enabled, make sure you enable it now.</span></span>

## <a name="creating-speech-commands"></a><span data-ttu-id="b419e-115">Erstellen von Sprachbefehlen</span><span class="sxs-lookup"><span data-stu-id="b419e-115">Creating speech commands</span></span>

<span data-ttu-id="b419e-116">Wählen Sie im Hierarchiefenster das **MixedRealityToolkit**-Objekt und dann im Inspektorfenster die Registerkarte „MixedRealityToolkit > **Input**“ (MixedRealityToolkit > Eingabe) aus. Führen Sie dann die folgenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="b419e-116">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the MixedRealityToolkit > **Input** tab and take the following steps:</span></span>

* <span data-ttu-id="b419e-117">Klappen Sie den Abschnitt **Speech** (Sprache) auf</span><span class="sxs-lookup"><span data-stu-id="b419e-117">Expand the **Speech** section</span></span>
* <span data-ttu-id="b419e-118">Klonen Sie das Profil **DefaultMixedRealitySpeechCommandsProfile**, und geben Sie ihm einen passenden Namen, beispielsweise _GettingStarted_MixedRealitySpeechCommandsProfile_</span><span class="sxs-lookup"><span data-stu-id="b419e-118">Clone the **DefaultMixedRealitySpeechCommandsProfile** and give it a suitable name, for example, _GettingStarted_MixedRealitySpeechCommandsProfile_</span></span>
* <span data-ttu-id="b419e-119">Vergewissern Sie sich, dass **Start Behaviour** (Startverhalten) auf **Auto Start** (Automatischer Start) festgelegt ist</span><span class="sxs-lookup"><span data-stu-id="b419e-119">Verify that **Start Behaviour** is set to **Auto Start**</span></span>

![Erstellen von Sprachbefehlen](images/mr-learning-base/base-09-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="b419e-121">Wenn Sie eine Auffrischung zum Klonen von MRTK-Profilen benötigen, lesen Sie die Anweisungen in [Konfigurieren der MRTK-Profile](mr-learning-base-03.md).</span><span class="sxs-lookup"><span data-stu-id="b419e-121">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the MRTK profiles](mr-learning-base-03.md) instructions.</span></span>

<span data-ttu-id="b419e-122">Klicken Sie im Abschnitt „Speech > **Speech Commands**“ (Sprache > Sprachbefehle) vier Mal auf die Schaltfläche **+ Add a New Speech Command** (Neuen Sprachbefehl hinzufügen), um unten in der Liste der vorhandenen Sprachbefehle einen neuen Sprachbefehl hinzuzufügen, und geben Sie dann in den **Keyword**-Feldern (Schlüsselwort) die folgenden Ausdrücke ein:</span><span class="sxs-lookup"><span data-stu-id="b419e-122">In the Speech > **Speech Commands** section, click the **+ Add a New Speech Command** button four times to add four new speech commands to the list of the existing speech commands, then in the **Keyword** fields enter the following phrases:</span></span>

* <span data-ttu-id="b419e-123">Enable Indicator (Indikator aktivieren)</span><span class="sxs-lookup"><span data-stu-id="b419e-123">Enable Indicator</span></span>
* <span data-ttu-id="b419e-124">Enable Tap to Place (Zum Platzieren tippen aktivieren)</span><span class="sxs-lookup"><span data-stu-id="b419e-124">Enable Tap to Place</span></span>
* <span data-ttu-id="b419e-125">Enable Bounding Box (Begrenzungsrahmen aktivieren)</span><span class="sxs-lookup"><span data-stu-id="b419e-125">Enable Bounding Box</span></span>
* <span data-ttu-id="b419e-126">Disable Bounding Box (Begrenzungsrahmen deaktivieren)</span><span class="sxs-lookup"><span data-stu-id="b419e-126">Disable Bounding Box</span></span>

![Hinzufügen neuer Sprachbefehle](images/mr-learning-base/base-09-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="b419e-128">Wenn Ihr Computer nicht über ein Mikrofon verfügt, können Sie den Sprachbefehlen einen Tastencode zuweisen, sodass Sie sie durch Drücken der entsprechenden Taste auslösen können.</span><span class="sxs-lookup"><span data-stu-id="b419e-128">If your computer does not have a microphone you can assign a KeyCode to the speech commands, which will let you trigger them when the corresponding key is pressed.</span></span>

## <a name="controlling-speech-commands"></a><span data-ttu-id="b419e-129">Steuern von Sprachbefehlen</span><span class="sxs-lookup"><span data-stu-id="b419e-129">Controlling speech commands</span></span>

<span data-ttu-id="b419e-130">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** (Medienobjekte > MRTK > SDK > Features > UX > Prefabs > QuickInfo), um die QuickInfo-Prefabs zu suchen:</span><span class="sxs-lookup"><span data-stu-id="b419e-130">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** folder to locate the tooltip prefabs:</span></span>

![Öffnen des QuickInfo-Ordners](images/mr-learning-base/base-09-section3-step1-1.png)

<span data-ttu-id="b419e-132">Klicken Sie im Hierarchiefenster mit der rechten Maustaste auf eine leere Stelle, und wählen Sie **Create Empty** (Leer erstellen) aus, um Ihrer Szene ein leeres Objekt hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="b419e-132">In the Hierarchy window, right-click on an empty spot and select **Create Empty** to add an empty object to your scene.</span></span>

<span data-ttu-id="b419e-133">Benennen Sie das Objekt **SpeechInputHandler_Global**, verwenden Sie dann im Inspektorfenster die Schaltfläche **Add Component** (Komponente hinzufügen), um die **SpeechInputHandler**-Komponente hinzuzufügen, und konfigurieren Sie sie dann wie folgt:</span><span class="sxs-lookup"><span data-stu-id="b419e-133">Name the object **SpeechInputHandler_Global**, then in the Inspector window, use the **Add Component** button to add the **SpeechInputHandler** component and configure it as follows:</span></span>

* <span data-ttu-id="b419e-134">**Deaktivieren** Sie das Kontrollkästchen **Is Focus Required** (Ist Fokus erforderlich), damit der Benutzer das Objekt nicht anblicken muss, um den Sprachbefehl mit der SpeechInputHandler-Komponente auszulösen</span><span class="sxs-lookup"><span data-stu-id="b419e-134">**Uncheck** the **Is Focus Required** checkbox, so the user is not required to look at the object with the SpeechInputHandler component to trigger the speech command</span></span>
* <span data-ttu-id="b419e-135">Weisen Sie im Projektfenster das Prefab **SpeechConfirmation Tooltip** dem Feld **Speech Confirmation Tooltip Prefab** zu, damit dieses Prefab angezeigt wird, wenn ein Sprachbefehl erkannt wird</span><span class="sxs-lookup"><span data-stu-id="b419e-135">From the Project window, assign the **SpeechConfirmation Tooltip** prefab to the **Speech Confirmation Tooltip Prefab** field, to have this prefab appear when a speech command is recognized</span></span>

![Konfigurieren der Spracheingabe-Handlerkomponente](images/mr-learning-base/base-09-section3-step1-2.png)

<span data-ttu-id="b419e-137">Klicken Sie in der SpeechInputHandler-Komponente drei Mal auf das kleine **+** -Symbol, um drei Schlüsselwortelemente hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="b419e-137">On the SpeechInputHandler component, click the small **+** icon three times to add three keyword elements:</span></span>

![Hinzufügen von Schlüsselwortelementen zum Spracheingabehandler](images/mr-learning-base/base-09-section3-step1-3.png)

<span data-ttu-id="b419e-139">Klappen Sie **Element 0** auf, und konfigurieren Sie es wie folgt:</span><span class="sxs-lookup"><span data-stu-id="b419e-139">Expand **Element 0** and configure it as follows:</span></span>

* <span data-ttu-id="b419e-140">Geben Sie im Feld **Keyword** (Schlüsselwort) **Enable Indicator** (Indikator aktivieren) ein, um auf den Sprachbefehl „Enable Indicator“ (Indikator aktivieren) zu verweisen, den Sie im vorherigen Abschnitt erstellt haben</span><span class="sxs-lookup"><span data-stu-id="b419e-140">In the **Keyword** field, enter **Enable Indicator**, to reference the Enable Indicator speech command you created in the previous section</span></span>
* <span data-ttu-id="b419e-141">Klicken Sie auf das kleine **+** -Symbol, um ein Ereignis hinzuzufügen</span><span class="sxs-lookup"><span data-stu-id="b419e-141">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="b419e-142">Weisen Sie im Hierarchiefenster das **Indicator**-Objekt (Indikator) dem Feld **None (Object)** (Ohne (Objekt)) zu</span><span class="sxs-lookup"><span data-stu-id="b419e-142">From the Hierarchy window, assign the **Indicator** object to the **None (Object)** field</span></span>
* <span data-ttu-id="b419e-143">Wählen Sie in der Dropdownliste **No Function** (Keine Funktion) **GameObject** > **SetActive (bool)** aus, um diese Funktion als die beim Auslösen des Ereignisses auszuführende Aktion festzulegen</span><span class="sxs-lookup"><span data-stu-id="b419e-143">From the **No Function** dropdown, select **GameObject** > **SetActive (bool)** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="b419e-144">Aktivieren Sie das Argumentkontrollkästchen, so dass es **aktiviert** ist</span><span class="sxs-lookup"><span data-stu-id="b419e-144">Check the argument checkbox, so it is **checked**</span></span>

![Konfigurieren von Schlüsselwortelement 0](images/mr-learning-base/base-09-section3-step1-4.png)

<span data-ttu-id="b419e-146">Klappen Sie **Element 1** auf, und konfigurieren Sie es wie folgt:</span><span class="sxs-lookup"><span data-stu-id="b419e-146">Expand **Element 1** and configure it as follows:</span></span>

* <span data-ttu-id="b419e-147">Geben Sie im Feld **Keyword** (Schlüsselwort) **Enable Bounding Box** (Begrenzungsrahmen aktivieren) ein, um auf den Sprachbefehl „Enable Bounding Box“ (Begrenzungsrahmen aktivieren) zu verweisen, den Sie im vorherigen Abschnitt erstellt haben</span><span class="sxs-lookup"><span data-stu-id="b419e-147">In the **Keyword** field, enter **Enable Bounding Box**, to reference the Enable Bounding Box command you created in the previous section</span></span>
* <span data-ttu-id="b419e-148">Klicken Sie auf das kleine **+** -Symbol, um ein Ereignis hinzuzufügen</span><span class="sxs-lookup"><span data-stu-id="b419e-148">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="b419e-149">Weisen Sie im Hierarchiefenster das **RoverExplorer**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu</span><span class="sxs-lookup"><span data-stu-id="b419e-149">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="b419e-150">Wählen Sie in der Dropdownliste **No Function** (Ohne Funktion) **BoundingBox** > **bool Enabled** aus, um diesen Eigenschaftswert zu aktualisieren, wenn das Ereignis ausgelöst wird</span><span class="sxs-lookup"><span data-stu-id="b419e-150">From the **No Function** dropdown, select **BoundingBox** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="b419e-151">Aktivieren Sie das Argumentkontrollkästchen, so dass es **aktiviert** ist</span><span class="sxs-lookup"><span data-stu-id="b419e-151">Check the argument checkbox, so it is **checked**</span></span>
* <span data-ttu-id="b419e-152">Klicken Sie auf das kleine **+** -Symbol, um ein weiteres Ereignis hinzuzufügen</span><span class="sxs-lookup"><span data-stu-id="b419e-152">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="b419e-153">Weisen Sie im Hierarchiefenster das **RoverExplorer**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu</span><span class="sxs-lookup"><span data-stu-id="b419e-153">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="b419e-154">Wählen Sie in der Dropdownliste **No Function** (Ohne Funktion) **ObjectManipulator** > **bool Enabled** aus, um diesen Eigenschaftswert zu aktualisieren, wenn das Ereignis ausgelöst wird</span><span class="sxs-lookup"><span data-stu-id="b419e-154">From the **No Function** dropdown, select **ObjectManipulator** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="b419e-155">Aktivieren Sie das Argumentkontrollkästchen, so dass es **aktiviert** ist</span><span class="sxs-lookup"><span data-stu-id="b419e-155">Check the argument checkbox, so it is **checked**</span></span>

![Konfigurieren von Schlüsselwortelement 1](images/mr-learning-base/base-09-section3-step1-5.png)

<span data-ttu-id="b419e-157">Klappen Sie **Element 2** auf, und konfigurieren Sie es wie folgt:</span><span class="sxs-lookup"><span data-stu-id="b419e-157">Expand **Element 2** and configure it as follows:</span></span>

* <span data-ttu-id="b419e-158">Geben Sie im Feld **Keyword** (Schlüsselwort) **Disable Bounding Box** (Begrenzungsrahmen deaktivieren) ein, um auf den Sprachbefehl „Disable Bounding Box“ (Begrenzungsrahmen deaktivieren) zu verweisen, den Sie im vorherigen Abschnitt erstellt haben</span><span class="sxs-lookup"><span data-stu-id="b419e-158">In the **Keyword** field, enter **Disable Bounding Box**, to reference the Disable Bounding Box command you created in the previous section</span></span>
* <span data-ttu-id="b419e-159">Klicken Sie auf das kleine **+** -Symbol, um ein Ereignis hinzuzufügen</span><span class="sxs-lookup"><span data-stu-id="b419e-159">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="b419e-160">Weisen Sie im Hierarchiefenster das **RoverExplorer**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu</span><span class="sxs-lookup"><span data-stu-id="b419e-160">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="b419e-161">Wählen Sie in der Dropdownliste **No Function** (Ohne Funktion) **BoundingBox** > **bool Enabled** aus, um diesen Eigenschaftswert zu aktualisieren, wenn das Ereignis ausgelöst wird</span><span class="sxs-lookup"><span data-stu-id="b419e-161">From the **No Function** dropdown, select **BoundingBox** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="b419e-162">Vergewissern Sie sich, dass das Argumentkontrollkästchen **deaktiviert** ist</span><span class="sxs-lookup"><span data-stu-id="b419e-162">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="b419e-163">Klicken Sie auf das kleine **+** -Symbol, um ein weiteres Ereignis hinzuzufügen</span><span class="sxs-lookup"><span data-stu-id="b419e-163">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="b419e-164">Weisen Sie im Hierarchiefenster das **RoverExplorer**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu</span><span class="sxs-lookup"><span data-stu-id="b419e-164">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="b419e-165">Wählen Sie in der Dropdownliste **No Function** (Ohne Funktion) **ObjectManipulator** > **bool Enabled** aus, um diesen Eigenschaftswert zu aktualisieren, wenn das Ereignis ausgelöst wird</span><span class="sxs-lookup"><span data-stu-id="b419e-165">From the **No Function** dropdown, select **ObjectManipulator** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="b419e-166">Vergewissern Sie sich, dass das Argumentkontrollkästchen **deaktiviert** ist</span><span class="sxs-lookup"><span data-stu-id="b419e-166">Verify that the argument checkbox is **unchecked**</span></span>

![Konfigurieren von Schlüsselwortelement 2](images/mr-learning-base/base-09-section3-step1-6.png)

<span data-ttu-id="b419e-168">Wählen Sie im Hierarchiefenster das Objekt RoverExplorer > **RoverAssembly** aus, verwenden Sie dann im Inspektorfenster die Schaltfläche **Add Component** (Komponente hinzufügen), um die Komponente **SpeechInputHandler** hinzuzufügen, und konfigurieren Sie sie wie folgt:</span><span class="sxs-lookup"><span data-stu-id="b419e-168">In the Hierarchy window, select the RoverExplorer > **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the **SpeechInputHandler** component and configure it as follows:</span></span>

* <span data-ttu-id="b419e-169">Vergewissern Sie sich, dass das Kontrollkästchen **Is Focus Required** (Ist Fokus erforderlich) **aktiviert** ist, damit der Benutzer das Objekt nicht anblicken muss, um den Sprachbefehl mit der SpeechInputHandler-Komponente, d. h. der RoverAssembly, auszulösen</span><span class="sxs-lookup"><span data-stu-id="b419e-169">Verify that the **Is Focus Required** checkbox is **check**, so the user is required to look at the object with the SpeechInputHandler component, i.e., the RoverAssembly, to trigger the speech command</span></span>
* <span data-ttu-id="b419e-170">Weisen Sie im Projektfenster das Prefab **SpeechConfirmation Tooltip** dem Feld **Speech Confirmation Tooltip Prefab** zu, damit dieses Prefab angezeigt wird, wenn ein Sprachbefehl erkannt wird</span><span class="sxs-lookup"><span data-stu-id="b419e-170">From the Project window, assign the **SpeechConfirmation Tooltip** prefab to the **Speech Confirmation Tooltip Prefab** field, to have this prefab appear when a speech command is recognized</span></span>

![Hinzufügen des Spracheingabehandlers zur Rover-Baugruppe](images/mr-learning-base/base-09-section3-step1-7.png)

<span data-ttu-id="b419e-172">Klicken Sie in der SpeechInputHandler-Komponente auf das kleine **+** -Symbol, um ein Stichwortelement hinzuzufügen, klappen Sie das neu erstellte Element auf, und konfigurieren Sie es wie folgt:</span><span class="sxs-lookup"><span data-stu-id="b419e-172">On the SpeechInputHandler component, click the small **+** icon to add a keyword element, expand the newly created element, then configure it as follows:</span></span>

* <span data-ttu-id="b419e-173">Geben Sie im Feld **Keyword** (Schlüsselwort) **Enable Tap to Place** (Zum Platzieren tippen aktivieren) ein, um auf den Sprachbefehl „Enable Tap to Place“ (Zum Platzieren tippen aktivieren) zu verweisen, den Sie im vorherigen Abschnitt erstellt haben</span><span class="sxs-lookup"><span data-stu-id="b419e-173">In the **Keyword** field, enter **Enable Tap to Place**, to reference the Enable Tap to Place command you created in the previous section</span></span>
* <span data-ttu-id="b419e-174">Klicken Sie auf das kleine **+** -Symbol, um ein Ereignis hinzuzufügen</span><span class="sxs-lookup"><span data-stu-id="b419e-174">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="b419e-175">Weisen Sie im Hierarchiefenster das Objekt selbst, d. h. das gleiche **RoverAssembly**-Objekt, dem Feld **None (Object)** (Ohne (Objekt)) zu</span><span class="sxs-lookup"><span data-stu-id="b419e-175">From the Hierarchy window, assign the object itself, i.e., the same **RoverAssembly** object, to the **None (Object)** field</span></span>
* <span data-ttu-id="b419e-176">Wählen Sie in der Dropdownliste **No Function** (Ohne Funktion) **TapToPlace** > **bool Enabled** aus, um diesen Eigenschaftswert zu aktualisieren, wenn das Ereignis ausgelöst wird</span><span class="sxs-lookup"><span data-stu-id="b419e-176">From the **No Function** dropdown, select **TapToPlace** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="b419e-177">Aktivieren Sie das Argumentkontrollkästchen, so dass es **aktiviert** ist</span><span class="sxs-lookup"><span data-stu-id="b419e-177">Check the argument checkbox, so it is **checked**</span></span>

![Konfigurieren des Spracheingabehandlers in der Rover-Baugruppe](images/mr-learning-base/base-09-section3-step1-8.png)

## <a name="congratulations"></a><span data-ttu-id="b419e-179">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="b419e-179">Congratulations</span></span>

<span data-ttu-id="b419e-180">In diesem Tutorial haben Sie erfahren, wie Sie Sprachbefehle erstellen und diese global steuern.</span><span class="sxs-lookup"><span data-stu-id="b419e-180">In this tutorial, you learned how to create speech commands and how to control them globally.</span></span> <span data-ttu-id="b419e-181">Außerdem haben Sie erfahren, wie Sie lokale Sprachbefehle steuern, die es erfordern, dass der Benutzer das Objekt ansieht, das den Sprachbefehl steuert.</span><span class="sxs-lookup"><span data-stu-id="b419e-181">You also learned how to control local speech commands that require the user to look at the object that controls the speech command.</span></span>

<span data-ttu-id="b419e-182">Damit ist die Reihe der [Tutorials zu den ersten Schritten](mr-learning-base-01.md) zugleich abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="b419e-182">This also concludes the [Getting started tutorials](mr-learning-base-01.md) series.</span></span> <span data-ttu-id="b419e-183">Im Lauf dieser Tutorials haben Sie erfolgreich von Grund auf ein vollständiges Mixed Reality-Erlebnis mithilfe des MRTK erstellt.</span><span class="sxs-lookup"><span data-stu-id="b419e-183">Through these tutorials, you have successfully built a complete mixed reality experience from scratch using the MRTK.</span></span>

<span data-ttu-id="b419e-184">In den beiden nächsten Tutorialreihen, den [Azure Spatial Anchors-Tutorials](mr-learning-asa-01.md) und den [Tutorials zu den Mehrbenutzerfunktionen](mr-learning-sharing-01.md), erfahren Sie zunächst, wie Sie Azure Spatial Anchors in Ihr Projekt integrieren, um das von Ihnen erstellte Rover Explorer-Erlebnis in der realen Welt zu verankern.</span><span class="sxs-lookup"><span data-stu-id="b419e-184">In the next two tutorial series, [Azure Spatial Anchors tutorials](mr-learning-asa-01.md) and [Multi-user capabilities tutorials](mr-learning-sharing-01.md), you will first learn how to integrate Azure Spatial Anchors into your project to anchor the Rover Explorer experience you created in the real world.</span></span> <span data-ttu-id="b419e-185">Anschließend erfahren Sie, wie Sie Ihrem Projekt Mehrbenutzerfunktionen hinzufügen, um Benutzer- und Objektbewegungen in Echtzeit zu teilen.</span><span class="sxs-lookup"><span data-stu-id="b419e-185">Then, you will learn how to add multi-user capabilities to your project to share user and object movements in real-time.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="b419e-186">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="b419e-186">Next Development Checkpoint</span></span>

<span data-ttu-id="b419e-187">Wenn Sie dem Weg der Unity-Entwicklungsprüfpunkte folgen, den wir entworfen haben, besteht Ihre nächste Aufgabe darin, sich mit den Grundbausteinen von Mixed Reality-Anwendungen vertraut zu machen.</span><span class="sxs-lookup"><span data-stu-id="b419e-187">If you're following the Unity development checkpoint journey we've laid out, your next task is to familiarize yourself with core building blocks of Mixed Reality apps.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b419e-188">Grundlegende Interaktionen</span><span class="sxs-lookup"><span data-stu-id="b419e-188">Basic interactions</span></span>](../mrtk-101.md)

<span data-ttu-id="b419e-189">Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](../unity-development-overview.md#1-getting-started) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="b419e-189">You can always go back to the [Unity development checkpoints](../unity-development-overview.md#1-getting-started) at any time.</span></span>
