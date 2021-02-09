---
title: Einrichten des Verständnisses von Absichten und natürlicher Sprache
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Absichten und Verstehen natürlicher Sprache in Mixed-Reality-Anwendungen eingerichtet werden.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, MRTK, Mixed Reality Toolkit, UWP, Azure Spatial Anchors, Spracherkennung, Windows 10, LUIS, LUIS-Portal, Absicht, Entitäten, Äußerungen, Verstehen natürlicher Sprache
ms.localizationpriority: high
ms.openlocfilehash: 49e2b44000add22e924d9552f60b63ac1ac30288
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590362"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a><span data-ttu-id="65c8f-104">4. Einrichten des Verstehens von Absichten und natürlicher Sprache</span><span class="sxs-lookup"><span data-stu-id="65c8f-104">4. Setting up intent and natural language understanding</span></span>

<span data-ttu-id="65c8f-105">In diesem Tutorial untersuchen wir die Absichtserkennung des Azure-Sprachdiensts.</span><span class="sxs-lookup"><span data-stu-id="65c8f-105">In this tutorial, you will explore the Azure Speech Service's intent recognition.</span></span> <span data-ttu-id="65c8f-106">Die Absichtserkennung ermöglicht es Ihnen, Ihre Anwendung mit KI-gestützten Sprachbefehlen auszustatten. In diesem Fall können Benutzer unspezifische Sprachbefehle äußern, und ihre Absicht wird trotzdem vom System verstanden.</span><span class="sxs-lookup"><span data-stu-id="65c8f-106">The intent recognition allows you to equip our application with AI-powered speech commands, where users can say non-specific speech commands and still have their intent understood by the system.</span></span>

## <a name="objectives"></a><span data-ttu-id="65c8f-107">Ziele</span><span class="sxs-lookup"><span data-stu-id="65c8f-107">Objectives</span></span>

* <span data-ttu-id="65c8f-108">Das Erlernen der Einrichtung von Absicht, Entitäten und Äußerungen im LUIS-Portal</span><span class="sxs-lookup"><span data-stu-id="65c8f-108">Learn how to set up intent, entities, and utterances in the LUIS portal</span></span>
* <span data-ttu-id="65c8f-109">Erlernen der Implementierung des Erkennens von Absichten und des Verstehens natürlicher Sprache in unserer Anwendung</span><span class="sxs-lookup"><span data-stu-id="65c8f-109">Learn how to implement intent and natural language understanding in our application</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="65c8f-110">Vorbereiten des Szenarios</span><span class="sxs-lookup"><span data-stu-id="65c8f-110">Preparing the scene</span></span>

<span data-ttu-id="65c8f-111">Wählen Sie im Hierarchiefenster das **Lunarcom**-Objekt aus, und verwenden Sie dann im Inspektorfenster die Schaltfläche **Komponente hinzufügen**, um dem Lunarcom-Objekt die Komponente **Lunarcom Intent Recognizer (Script)** hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="65c8f-111">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Intent Recognizer (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-1.png)

<span data-ttu-id="65c8f-113">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher**, ziehen Sie das Prefab **RocketLauncher_Complete** in Ihr Hierarchiefenster, und platzieren Sie es an einem passenden Ort vor der Kamera, beispielsweise:</span><span class="sxs-lookup"><span data-stu-id="65c8f-113">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder, drag the **RocketLauncher_Complete** prefab into your Hierarchy window, and place it at a suitable location in front of the camera, for example:</span></span>

* <span data-ttu-id="65c8f-114">**Transformationsposition** X = 0, Y = -0,4, Z = 1</span><span class="sxs-lookup"><span data-stu-id="65c8f-114">Transform **Position** X = 0, Y = -0.4, Z = 1</span></span>
* <span data-ttu-id="65c8f-115">**Transformationsrotation** X = 0, Y = 90, Z = 0</span><span class="sxs-lookup"><span data-stu-id="65c8f-115">Transform **Rotation** X = 0, Y = 90, Z = 0</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-2.png)

<span data-ttu-id="65c8f-117">Wählen Sie im Hierarchiefenster das **Lunarcom**-Objekt erneut aus, klappen Sie dann das Objekt **RocketLauncher_Complete** > **Button** auf, und weisen Sie jedem untergeordneten Objekt des **Buttons**-Objekts das entsprechende **Lunar Launcher Buttons**-Feld zu:</span><span class="sxs-lookup"><span data-stu-id="65c8f-117">In the Hierarchy window, select the **Lunarcom** object again, then expand the **RocketLauncher_Complete** > **Button** object and assign each of the **Buttons** object's child objects to the corresponding **Lunar Launcher Buttons** field:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-3.png)

## <a name="creating-the-azure-language-understanding-resource"></a><span data-ttu-id="65c8f-119">Erstellen der Azure Language Understanding-Ressource</span><span class="sxs-lookup"><span data-stu-id="65c8f-119">Creating the Azure Language Understanding resource</span></span>

<span data-ttu-id="65c8f-120">In diesem Abschnitt erstellen Sie eine Azure-Vorhersageressource für die LUIS-App (Language Understanding Intelligent Service), die Sie im nächsten Abschnitt erstellen.</span><span class="sxs-lookup"><span data-stu-id="65c8f-120">In this section, you will create an Azure prediction resource for the Language Understanding Intelligent Service (LUIS) app you will create in the next section.</span></span>

<span data-ttu-id="65c8f-121">Melden Sie sich bei <a href="https://portal.azure.com" target="_blank">Azure</a> an, und klicken Sie auf **Ressource erstellen**.</span><span class="sxs-lookup"><span data-stu-id="65c8f-121">Sign in to <a href="https://portal.azure.com" target="_blank">Azure</a> and click **Create a resource**.</span></span> <span data-ttu-id="65c8f-122">Suchen Sie dann nach **Language Understanding**, und wählen Sie es aus:</span><span class="sxs-lookup"><span data-stu-id="65c8f-122">Then search for and select **Language Understanding**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-1.png)

<span data-ttu-id="65c8f-124">Klicken Sie auf die Schaltfläche **Erstellen**, um eine Instanz dieses Diensts zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="65c8f-124">Click the **Create** button to create an instance of this service:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-2.png)

<span data-ttu-id="65c8f-126">Klicken Sie auf der Seite „Erstellen“ auf die Option **Vorhersage**, und geben Sie die folgenden Werte ein:</span><span class="sxs-lookup"><span data-stu-id="65c8f-126">On the Create page, click the **Prediction** option and enter the following values:</span></span>

* <span data-ttu-id="65c8f-127">Wählen Sie unter **Abonnement** **Kostenlose Testversion** aus, wenn Sie über ein Testabonnement verfügen, und wählen Sie andernfalls eins Ihrer anderen Abonnements aus</span><span class="sxs-lookup"><span data-stu-id="65c8f-127">For **Subscription**, select **Free Trail** if you have a trial subscription, otherwise, select one of your other subscriptions</span></span>
* <span data-ttu-id="65c8f-128">Klicken Sie für die **Ressourcengruppe** auf den Link **Neue erstellen**, geben Sie einen passenden Namen ein, beispielsweise *MRKT-Tutorials*, und klicken Sie dann auf **OK**</span><span class="sxs-lookup"><span data-stu-id="65c8f-128">For the **Resource group**, click the **Create new** link, enter a suitable name, for example, *MRKT-Tutorials*, and then click on **OK**</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="65c8f-130">Zum Zeitpunkt der Entstehung dieses Artikels muss nicht eigens eine Erstellungsressource erstellt werden, da in LUIS automatisch ein Erstellungs-Testschlüssel generiert wird, wenn Sie im nächsten Abschnitt den Language Understanding Intelligent Service (LUIS) erstellen.</span><span class="sxs-lookup"><span data-stu-id="65c8f-130">As of the time of this writing, you do not need to create an authoring resource because an authoring trial key will automatically be generated within LUIS when you create the Language Understanding Intelligent Service (LUIS) in the next section.</span></span>

> [!TIP]
> <span data-ttu-id="65c8f-131">Wenn Sie bereits über eine andere geeignete Ressourcengruppe in Ihrem Azure-Konto verfügen, beispielsweise, wenn Sie das [Azure Spatial Anchor](mr-learning-asa-01.md)-Tutorial abgeschlossen haben, können Sie diese Ressourcengruppe verwenden, statt eine neue zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="65c8f-131">If you already have another suitable resource group in your Azure account, for example, if you completed the [Azure Spatial Anchors](mr-learning-asa-01.md) tutorial, you may use this resource group instead of creating a new one.</span></span>

<span data-ttu-id="65c8f-132">Geben Sie noch auf der Seite „Erstellen“ die folgenden Werte ein:</span><span class="sxs-lookup"><span data-stu-id="65c8f-132">While still on the Create page, enter the following values:</span></span>

* <span data-ttu-id="65c8f-133">Geben Sie für **Name** einen passenden Namen für den Dienst ein, z. B. *MRTK-Tutorials-AzureSpeechServices*</span><span class="sxs-lookup"><span data-stu-id="65c8f-133">For **Name**, enter a suitable name for the service, for example, *MRTK-Tutorials-AzureSpeechServices*</span></span>
* <span data-ttu-id="65c8f-134">Wählen Sie als **Speicherort für die Vorhersage** einen Speicherort in der Nähe des Standorts Ihres App-Benutzers aus, z. B. *(USA) USA, Westen*</span><span class="sxs-lookup"><span data-stu-id="65c8f-134">For **Prediction location**, choose a location close to your app users' physical location, for example, *(US) West US*</span></span>
* <span data-ttu-id="65c8f-135">Wählen Sie als **Tarif für Vorhersage** im Rahmen dieses Tutorials **F0 (5 Aufrufe pro Sekunde, 10.000 Aufrufe pro Monat)** aus</span><span class="sxs-lookup"><span data-stu-id="65c8f-135">For **Prediction pricing tier**, for the purpose of this tutorial, select **F0 (5 Calls per second, 10K Calls per month)**</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-4.png)

<span data-ttu-id="65c8f-137">Klicken Sie als Nächstes auf die Registerkarte **Überprüfen + Erstellen**, überprüfen Sie die Details, und klicken Sie dann auf die Schaltfläche **Erstellen** am unteren Rand der Seite, um die Ressource sowie die neue Ressourcengruppe zu erstellen, falls Sie die Erstellung einer Ressourcengruppe konfiguriert haben:</span><span class="sxs-lookup"><span data-stu-id="65c8f-137">Next, click on **Review + create** tab, review the details, and then click the **Create** button, located at the bottom of the page, to create the resource, as well as, the new resource group if you configured one to be created:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-5.png)

> [!NOTE]
> <span data-ttu-id="65c8f-139">Nachdem Sie auf die Schaltfläche „Erstellen“ geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. Dies kann einige Minuten in Anspruch nehmen.</span><span class="sxs-lookup"><span data-stu-id="65c8f-139">After you click the Create button, you will have to wait for the service to be created, which might take a few minutes.</span></span>

<span data-ttu-id="65c8f-140">Nachdem der Vorgang zum Erstellen der Ressource abgeschlossen ist, wird die Meldung angezeigt **Ihre Bereitstellung wurde abgeschlossen.** :</span><span class="sxs-lookup"><span data-stu-id="65c8f-140">Once the resource creation process is completed, you will see the message **Your deployment is complete**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-6.png)

## <a name="creating-the-language-understanding-intelligent-service-luis"></a><span data-ttu-id="65c8f-142">Erstellen des Language Understanding Intelligent Service (LUIS)</span><span class="sxs-lookup"><span data-stu-id="65c8f-142">Creating the Language Understanding Intelligent Service (LUIS)</span></span>

<span data-ttu-id="65c8f-143">In diesem Abschnitt erstellen Sie eine LUIS-App, konfigurieren und trainieren ihr Vorhersagemodell und verbinden es mit der Azure-Vorhersageressource, die Sie im vorherigen Schritt erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="65c8f-143">In this section, you will create a LUIS app, configure and train its prediction model, and connect it to the Azure prediction resource you created in the previous step.</span></span>

<span data-ttu-id="65c8f-144">Insbesondere erstellen Sie eine Absicht, die, falls der Benutzer sagt, dass eine Aktion ausgeführt werden soll, das Interactable.OnClick()-Ereignis für eine der drei roten Schaltflächen im Szenario auslöst, je nachdem, auf welche Schaltfläche der Benutzer verweist.</span><span class="sxs-lookup"><span data-stu-id="65c8f-144">Specifically, you will create an intent that if the user says an action should be taken, the app will trigger the Interactable.OnClick() event on one of the three red buttons in the scene, depending on which button the user references.</span></span>

<span data-ttu-id="65c8f-145">Wenn der Benutzer beispielsweise sagt **Fahre fort, starte die Rakete**, sagt die App vorher, dass **Fahre fort** bedeutet, dass eine **Aktion** ausgeführt werden soll, und dass das **anzuzielende** Interactable.OnClick()-Ereignis sich auf der Schaltfläche **Starten** befindet.</span><span class="sxs-lookup"><span data-stu-id="65c8f-145">For example, if the user says **go ahead and launch the rocket**, the app will predict that **go ahead** means some **action** should be taken, and that the Interactable.OnClick() event to **target** is on the **launch** button.</span></span>

<span data-ttu-id="65c8f-146">Dies sind die wichtigsten Schritte, die Sie durchführen müssen:</span><span class="sxs-lookup"><span data-stu-id="65c8f-146">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="65c8f-147">Erstellen einer LUIS-App</span><span class="sxs-lookup"><span data-stu-id="65c8f-147">Create a LUIS app</span></span>
2. <span data-ttu-id="65c8f-148">Erstellen von Absichten</span><span class="sxs-lookup"><span data-stu-id="65c8f-148">Create intents</span></span>
3. <span data-ttu-id="65c8f-149">Erstellen von Beispieläußerungen</span><span class="sxs-lookup"><span data-stu-id="65c8f-149">Create example utterances</span></span>
4. <span data-ttu-id="65c8f-150">Erstellen von Entitäten</span><span class="sxs-lookup"><span data-stu-id="65c8f-150">Create entities</span></span>
5. <span data-ttu-id="65c8f-151">Zuweisen von Entitäten zu den Beispieläußerungen</span><span class="sxs-lookup"><span data-stu-id="65c8f-151">Assign entities to the example utterances</span></span>
6. <span data-ttu-id="65c8f-152">Trainieren, Testen und Veröffentlichen der App</span><span class="sxs-lookup"><span data-stu-id="65c8f-152">Train, test, and publish the app</span></span>
7. <span data-ttu-id="65c8f-153">Zuweisen einer Azure-Vorhersageressource zur App</span><span class="sxs-lookup"><span data-stu-id="65c8f-153">Assign an Azure prediction resource to the app</span></span>

### <a name="1-create-a-luis-app"></a><span data-ttu-id="65c8f-154">1. Erstellen einer LUIS-App</span><span class="sxs-lookup"><span data-stu-id="65c8f-154">1. Create a LUIS app</span></span>

<span data-ttu-id="65c8f-155">Melden Sie sich bei <a href="https://www.luis.ai" target="_blank">LUIS</a> mit demselben Benutzerkonto an, das Sie zum Erstellen der Azure-Ressource im vorherigen Abschnitt verwendet haben, wählen Sie Ihr Land/Ihre Region aus, und stimmen Sie den Nutzungsbedingungen zu.</span><span class="sxs-lookup"><span data-stu-id="65c8f-155">Using the same user account you used when creating the Azure resource in the previous section, sign in to <a href="https://www.luis.ai" target="_blank">LUIS</a>, select your country, and agree to the terms of use.</span></span> <span data-ttu-id="65c8f-156">Wenn Sie im nächsten Schritt aufgefordert werden, **Ihr Azure-Konto zu verknüpfen**, wählen Sie **Weiterhin den Testschlüssel verwenden** aus, um stattdessen eine Azure-Erstellungsressource zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="65c8f-156">In the next step, when asked to **Link your Azure account**, choose **Continue using your trial key**, to use an Azure authoring resource instead.</span></span>

> [!NOTE]
> <span data-ttu-id="65c8f-157">Wenn Sie sich bereits für LUIS registriert haben und Ihr Erstellungs-Testschlüssel abgelaufen ist, finden Sie Informationen zum Umstellen Ihrer LUIS-Erstellungsressource auf Azure in der [Migrieren zu einem Azure-Ressourcen-Erstellungsschlüssel](/azure/cognitive-services/luis/luis-migration-authoring)-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="65c8f-157">If you have already signed up for LUIS and your authoring trial key has expired, you can refer to the [Migrate to an Azure resource authoring key](/azure/cognitive-services/luis/luis-migration-authoring) documentation to switch your LUIS authoring resource to Azure.</span></span>

<span data-ttu-id="65c8f-158">Klicken Sie nach der Anmeldung auf **Neue App**, und geben Sie folgende Werte in das Popupfenster **Neue App erstellen** ein:</span><span class="sxs-lookup"><span data-stu-id="65c8f-158">Once signed in, click **New app** and enter the following values in the **Create new app** popup window:</span></span>

* <span data-ttu-id="65c8f-159">Geben Sie für **Name** einen passenden Namen ein, z. B. *MRTK-Tutorials – AzureSpeechServices*</span><span class="sxs-lookup"><span data-stu-id="65c8f-159">For **Name**, enter a suitable name, for example, *MRTK Tutorials - AzureSpeechServices*</span></span>
* <span data-ttu-id="65c8f-160">Wählen Sie für **Kultur** die Option **Englisch** aus</span><span class="sxs-lookup"><span data-stu-id="65c8f-160">For **Culture**, select **English**</span></span>
* <span data-ttu-id="65c8f-161">Geben Sie für **Beschreibung** optional eine passende Beschreibung ein</span><span class="sxs-lookup"><span data-stu-id="65c8f-161">For **Description**, optionally enter a suitable description</span></span>
* <span data-ttu-id="65c8f-162">Wählen Sie als **Vorhersageressource** die Vorhersageressource in der Dropdownliste aus, die im Azure-Portal erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="65c8f-162">For **Prediction resource**, select the prediction resource by dropdown list that had been created azure portal.</span></span>

<span data-ttu-id="65c8f-163">Klicken Sie dann auf die Schaltfläche **Erstellen**, um die neue App zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="65c8f-163">Then click the **Done** button to create the new app:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step1-1.png)

<span data-ttu-id="65c8f-165">Wenn die neue App erstellt wurde, werden Sie zur **Dashboard** Seite der App geleitet:</span><span class="sxs-lookup"><span data-stu-id="65c8f-165">When the new app has been created, you will be taken to that app's **Dashboard** page:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step1-2.png)

### <a name="2-create-intents"></a><span data-ttu-id="65c8f-167">2. Erstellen von Absichten</span><span class="sxs-lookup"><span data-stu-id="65c8f-167">2. Create intents</span></span>

<span data-ttu-id="65c8f-168">Navigieren Sie von der Dashboard-Seite zur Seite „Build > App Assets > **Intents**“ (Erstellen > App-Ressourcen > Absichten), klicken Sie dann auf **Create** (Erstellen), und geben Sie den folgenden Wert im Popupfenster **Create new intent** (Neue Absicht erstellen) ein:</span><span class="sxs-lookup"><span data-stu-id="65c8f-168">From the Dashboard page, navigate to the Build > App Assets > **Intents** page, then click **Create** and enter the following value in the **Create new intent** popup window:</span></span>

* <span data-ttu-id="65c8f-169">Geben Sie als **Absichtsname** **PressButton** ein</span><span class="sxs-lookup"><span data-stu-id="65c8f-169">For **Intent name**, enter **PressButton**</span></span>

<span data-ttu-id="65c8f-170">Klicken Sie dann auf die Schaltfläche **Done** (Fertig), um die neue Ansicht zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="65c8f-170">Then click the **Done** button to create the new intent:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step2-1.png)

> [!CAUTION]
> <span data-ttu-id="65c8f-172">Im Rahmen dieses Tutorials verweist Ihr Unity-Projekt anhand des Namens auf diese Absicht, d. h. ‚PressButton‘.</span><span class="sxs-lookup"><span data-stu-id="65c8f-172">For the purpose of this tutorial, your Unity project will reference this intent by its name, i.e. 'PressButton'.</span></span> <span data-ttu-id="65c8f-173">Es ist daher äußerst wichtig, dass Sie Ihre Absicht genau gleich benennen.</span><span class="sxs-lookup"><span data-stu-id="65c8f-173">Consequently, it is extremely important that you name your intent exactly the same.</span></span>

<span data-ttu-id="65c8f-174">Wenn die neue Absicht erstellt wurde, werden Sie zu der Seite dieser Absicht geleitet:</span><span class="sxs-lookup"><span data-stu-id="65c8f-174">When the new intent has been created, you will be taken to that intent's page:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step2-2.png)

### <a name="3-create-example-utterances"></a><span data-ttu-id="65c8f-176">3. Erstellen von Beispieläußerungen</span><span class="sxs-lookup"><span data-stu-id="65c8f-176">3. Create example utterances</span></span>

<span data-ttu-id="65c8f-177">Fügen Sie der Liste mit **Beispieläußerungen** der Absicht **PressButton** die folgenden Beispieläußerungen hinzu:</span><span class="sxs-lookup"><span data-stu-id="65c8f-177">To the **PressButton** intent's **Example utterance** list, add the following example utterances:</span></span>

* <span data-ttu-id="65c8f-178">Startsequenz aktivieren</span><span class="sxs-lookup"><span data-stu-id="65c8f-178">activate launch sequence</span></span>
* <span data-ttu-id="65c8f-179">Platzierungshinweis anzeigen</span><span class="sxs-lookup"><span data-stu-id="65c8f-179">show me a placement hint</span></span>
* <span data-ttu-id="65c8f-180">Startsequenz einleiten</span><span class="sxs-lookup"><span data-stu-id="65c8f-180">initiate the launch sequence</span></span>
* <span data-ttu-id="65c8f-181">Schaltflächen für Platzierungshinweise drücken</span><span class="sxs-lookup"><span data-stu-id="65c8f-181">press placement hints button</span></span>
* <span data-ttu-id="65c8f-182">Gib mit einen Hinweis</span><span class="sxs-lookup"><span data-stu-id="65c8f-182">give me a hint</span></span>
* <span data-ttu-id="65c8f-183">Startschaltfläche drücken</span><span class="sxs-lookup"><span data-stu-id="65c8f-183">push the launch button</span></span>
* <span data-ttu-id="65c8f-184">Ich brauche einen Hinweis</span><span class="sxs-lookup"><span data-stu-id="65c8f-184">i need a hint</span></span>
* <span data-ttu-id="65c8f-185">Taste „Zurücksetzen“ drücken</span><span class="sxs-lookup"><span data-stu-id="65c8f-185">press the reset button</span></span>
* <span data-ttu-id="65c8f-186">Zeit zum Zurücksetzen des Experiments</span><span class="sxs-lookup"><span data-stu-id="65c8f-186">time to reset the experience</span></span>
* <span data-ttu-id="65c8f-187">Fahre fort, starte die Rakete</span><span class="sxs-lookup"><span data-stu-id="65c8f-187">go ahead and launch the rocket</span></span>

<span data-ttu-id="65c8f-188">Wenn alle Beispieläußerungen hinzugefügt wurden, sollte die Seite Ihrer Absicht PressButton so ähnlich aussehen:</span><span class="sxs-lookup"><span data-stu-id="65c8f-188">When all the example utterances have been added, your PressButton intent page should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step3-1.png)

> [!CAUTION]
> <span data-ttu-id="65c8f-190">Im Rahmen dieses Tutorials verweist Ihr Unity-Projekt auf die Wörter „Hinweis“, „Hinweise“, „Zurücksetzen“ und „Starten“.</span><span class="sxs-lookup"><span data-stu-id="65c8f-190">For the purpose of this tutorial, your Unity project will reference the words 'hint', 'hints', 'reset', and 'launch'.</span></span> <span data-ttu-id="65c8f-191">Daher ist es äußerst wichtig, dass Sie diese Wörter in genau der gleichen Weise schreiben.</span><span class="sxs-lookup"><span data-stu-id="65c8f-191">Consequently, it is extremely important that you spell these words in the exact same way.</span></span>

### <a name="4-create-entities"></a><span data-ttu-id="65c8f-192">4. Erstellen von Entitäten</span><span class="sxs-lookup"><span data-stu-id="65c8f-192">4. Create entities</span></span>

<span data-ttu-id="65c8f-193">Navigieren Sie von der Seite der Absicht PressButton zur Seite Erstellen > App-Ressourcen > **Entitäten**, klicken Sie dann auf **Erstellen**, und geben Sie die folgenden Werte im Popupfenster **Neue Entität erstellen** ein:</span><span class="sxs-lookup"><span data-stu-id="65c8f-193">From the PressButton intent page, navigate to the Build > App Assets > **Entities** page, then click **Create** and enter the following values in the **Create new entity** popup window:</span></span>

* <span data-ttu-id="65c8f-194">Geben Sie als **Entitätsname** **Aktion** ein</span><span class="sxs-lookup"><span data-stu-id="65c8f-194">For **Entity name**, enter **Action**</span></span>
* <span data-ttu-id="65c8f-195">Wählen Sie als **Entitätstyp** **Maschinell gelernt** aus.</span><span class="sxs-lookup"><span data-stu-id="65c8f-195">For **Entity type**, select **Machine learned**</span></span>

<span data-ttu-id="65c8f-196">Klicken Sie dann auf die Schaltfläche **Erstellen**, um die neue Entität zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="65c8f-196">Then click the **Create** button to create the new entity:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step4-1.png)

<span data-ttu-id="65c8f-198">**Wiederholen** Sie den vorhergehenden Schritt, um eine weitere Entität mit dem Namen **Ziel** zu erstellen, sodass Sie über zwei Entitäten verfügen, mit den Namen „Aktion“ und „Ziel“:</span><span class="sxs-lookup"><span data-stu-id="65c8f-198">**Repeat** the previous step to create another entity named **Target**, so you have two entities named Action and Target:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step4-2.png)

> [!CAUTION]
> <span data-ttu-id="65c8f-200">Im Rahmen dieses Tutorials verweist Ihr Unity-Projekt anhand des Namens auf diese Entitäten, d. h. „Aktion“ und „Ziel“.</span><span class="sxs-lookup"><span data-stu-id="65c8f-200">For the purpose of this tutorial, your Unity project will reference these entities by their names, i.e. 'Action' and 'Target'.</span></span> <span data-ttu-id="65c8f-201">Es ist daher äußerst wichtig, dass Sie Ihre Entitäten genau gleich benennen.</span><span class="sxs-lookup"><span data-stu-id="65c8f-201">Consequently, it is extremely important that you name your entities exactly the same.</span></span>

### <a name="5-assign-entities-to-the-example-utterances"></a><span data-ttu-id="65c8f-202">5. Zuweisen von Entitäten zu den Beispieläußerungen</span><span class="sxs-lookup"><span data-stu-id="65c8f-202">5. Assign entities to the example utterances</span></span>

<span data-ttu-id="65c8f-203">Navigieren Sie auf der Seite Entitäten zurück zur Seite der Absicht **PressButton**.</span><span class="sxs-lookup"><span data-stu-id="65c8f-203">From the Entities page, navigate back to the **PressButton** intent page.</span></span>

<span data-ttu-id="65c8f-204">Sobald Sie sich wieder auf der Seite der Absicht PressButton befinden, klicken Sie auf das Wort **Fahre**, dann auf das Wort **fort**, und wählen Sie dann im Kontext-Popupmenü **Aktion (Einfach)** aus, um **Fahre fort** als einen Entitätswert für **Aktion**-zu bezeichnen:</span><span class="sxs-lookup"><span data-stu-id="65c8f-204">Once back on the the PressButton intent page, click on the word **go** and then on the word **ahead**, and then select **Action (Simple)** from the contextual popup menu to label **go ahead** as an **Action** entity value:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-1.png)

<span data-ttu-id="65c8f-206">Der Ausdruck **Fahre fort** ist jetzt als Entitätswert für **Aktion** definiert.</span><span class="sxs-lookup"><span data-stu-id="65c8f-206">The **go ahead** phrase is now defined as an **Action** entity value.</span></span> <span data-ttu-id="65c8f-207">Nun wird der Aktionsentitätswert unter dem Ausdruck „Fahre fort“ angezeigt:</span><span class="sxs-lookup"><span data-stu-id="65c8f-207">Now you can notice the action entity value under the word go ahead:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-2.png)

> [!NOTE]
> <span data-ttu-id="65c8f-209">Die rote Linie, die unter der Bezeichnung in der Abbildung oben angezeigt wird, weist darauf hin, dass der Entitätswert nicht vorhergesagt wurde. Dies wird behoben, wenn Sie das Modell im nächsten Abschnitt trainieren.</span><span class="sxs-lookup"><span data-stu-id="65c8f-209">The red line you see under the label in the image above indicates that the entity value has not been predicted, this will be resolved when you train the model in the next section.</span></span>

<span data-ttu-id="65c8f-210">Klicken Sie als nächstes auf das Wort **starte**, und wählen Sie dann im Kontext-Popupmenü **Ziel (Einfach)** aus, um **starte** als einen **Ziel**-Entitätswert zu bezeichnen:</span><span class="sxs-lookup"><span data-stu-id="65c8f-210">Next, click on the word **launch**, and then select **Target (Simple)** from the contextual popup menu to label **launch** as a **Target** entity value:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-3.png)

<span data-ttu-id="65c8f-212">Das Wort **starte** ist jetzt als Entitätswert für **Ziel** definiert. Nun wird der Entitätswert von „Ziel“ unter dem Wort „starte“ angezeigt:</span><span class="sxs-lookup"><span data-stu-id="65c8f-212">The **launch** word is now defined as a **Target** entity value.Now you can notice the Target entity value under the word launch :</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-4.png)

<span data-ttu-id="65c8f-214">Die Beispieläußerung „Fahre fort, starte die Rakete“ für die PressButton-Absicht ist jetzt dafür konfiguriert, in folgender Weise vorhergesagt zu werden :</span><span class="sxs-lookup"><span data-stu-id="65c8f-214">The PressButton intent example utterance 'go ahead and launch the rocket' is now configured to be predicted as follows:</span></span>

* <span data-ttu-id="65c8f-215">Absicht: PressButton</span><span class="sxs-lookup"><span data-stu-id="65c8f-215">Intent: PressButton</span></span>
* <span data-ttu-id="65c8f-216">Action-Entität: Fahre fort</span><span class="sxs-lookup"><span data-stu-id="65c8f-216">Action entity: go ahead</span></span>
* <span data-ttu-id="65c8f-217">Zielentität: starte</span><span class="sxs-lookup"><span data-stu-id="65c8f-217">Target entity: launch</span></span>

<span data-ttu-id="65c8f-218">**Wiederholen** Sie die vorhergehenden zwei Schritte, um jeder der Beispieläußerungen eine Aktions- und eine Zielentitätsbezeichnung zuzuweisen, und behalten Sie dabei im Blick, dass die folgenden Wörter als **Ziel**-Entitäten bezeichnet werden sollen:</span><span class="sxs-lookup"><span data-stu-id="65c8f-218">**Repeat** the previous two-step process to assign an Action and a Target entity label to each of the example utterances, keeping in mind that the following words should be labeled as **Target** entities:</span></span>

* <span data-ttu-id="65c8f-219">**Hinweis** (zielt auf die HintsButton-Schaltfläche im Unity-Projekt ab)</span><span class="sxs-lookup"><span data-stu-id="65c8f-219">**hint** (targets the HintsButton in the Unity project)</span></span>
* <span data-ttu-id="65c8f-220">**Hinweise** (zielt auf die HintsButton-Schaltfläche im Unity-Projekt ab)</span><span class="sxs-lookup"><span data-stu-id="65c8f-220">**hints** (targets HintsButton in the Unity project)</span></span>
* <span data-ttu-id="65c8f-221">**Zurücksetzen** (zielt auf die ResetButton-Schaltfläche im Unity-Projekt ab)</span><span class="sxs-lookup"><span data-stu-id="65c8f-221">**reset** (targets the ResetButton in the Unity project)</span></span>
* <span data-ttu-id="65c8f-222">**starte** (zielt auf die LaunchButton-Schaltfläche im Unity-Projekt ab)</span><span class="sxs-lookup"><span data-stu-id="65c8f-222">**launch** (targets the LaunchButton in the Unity project)</span></span>

<span data-ttu-id="65c8f-223">Wenn alle Beispieläußerungen bezeichnet wurden, sollte die Seite Ihrer Absicht PressButton so ähnlich aussehen:</span><span class="sxs-lookup"><span data-stu-id="65c8f-223">When all the example utterances have been labeled, your PressButton intent page should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-5.png)

### <a name="6-train-test-and-publish-the-app"></a><span data-ttu-id="65c8f-225">6. Trainieren, Testen und Veröffentlichen der App</span><span class="sxs-lookup"><span data-stu-id="65c8f-225">6. Train, test, and publish the app</span></span>

<span data-ttu-id="65c8f-226">Um die App zu trainieren, klicken Sie auf die Schaltfläche **Trainieren**, und warten Sie, bis der Trainingsprozess abgeschlossen ist:</span><span class="sxs-lookup"><span data-stu-id="65c8f-226">To train the app, click the **Train** button and wait for the training process to complete:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-1.png)

> [!NOTE]
> <span data-ttu-id="65c8f-228">Wie Sie in der Abbildung oben sehen können, wurden die roten Linien unter allen Bezeichnungen entfernt, was darauf hinweist, dass alle Entitätswerte vorhergesagt wurden.</span><span class="sxs-lookup"><span data-stu-id="65c8f-228">As you can see in the image above, the red lines under all the labels have been removed, indicating that all the entity values have been predicted.</span></span> <span data-ttu-id="65c8f-229">Beachten Sie außerdem, dass das Statussymbol links auf der Trainieren-Schaltfläche die Farbe von rot zu grün gewechselt hat.</span><span class="sxs-lookup"><span data-stu-id="65c8f-229">Also notice that the status icon to the left of the Train button has changed color from red to green.</span></span>

<span data-ttu-id="65c8f-230">Wenn die Verarbeitung des Trainings abgeschlossen ist, klicken Sie auf die Schaltfläche **Testen**, geben Sie dann **Fahre fort, starte die Rakete** ein, und drücken Sie die EINGABETASTE:</span><span class="sxs-lookup"><span data-stu-id="65c8f-230">When the training is finished processing, click the **Test** button, then type in **go ahead and launch the rocket** and press the Enter key:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-2.png)

<span data-ttu-id="65c8f-232">Wenn die Testäußerung verarbeitet wurde, klicken Sie auf **Prüfen**, um das Testergebnis anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="65c8f-232">When the test utterance has been processed, click **Inspect** to see the test result:</span></span>

* <span data-ttu-id="65c8f-233">Absicht: PressButton (mit einer Sicherheit von 98,5 %)</span><span class="sxs-lookup"><span data-stu-id="65c8f-233">Intent: PressButton (with a 98.5% certainty)</span></span>
* <span data-ttu-id="65c8f-234">Aktion-Entität:Fahre fort</span><span class="sxs-lookup"><span data-stu-id="65c8f-234">Action entity: go ahead</span></span>
* <span data-ttu-id="65c8f-235">Ziel-Entität: starte</span><span class="sxs-lookup"><span data-stu-id="65c8f-235">Target entity: launch</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-3.png)

<span data-ttu-id="65c8f-237">Um die App zu veröffentlichen, klicken Sie oben rechts auf die Schaltfläche **Publish** (Veröffentlichen), wählen Sie dann im Popupfenster **Choose your publishing slot and settings** (Wählen Sie Ihren Veröffentlichungsslot und Ihre Einstellungen) **Production** (Produktion) aus, und klicken Sie auf die Schaltfläche **Fertig**:</span><span class="sxs-lookup"><span data-stu-id="65c8f-237">To publish the app, click the **Publish** button in the top right, then in the **Choose your publishing slot and settings** popup window, select **Production** and click the **Done** button:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-4.png)

<span data-ttu-id="65c8f-239">Warten Sie auf den Abschluss des Veröffentlichungsprozesses:</span><span class="sxs-lookup"><span data-stu-id="65c8f-239">Wait for the publishing process to complete:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-5.png)

<span data-ttu-id="65c8f-241">Navigieren Sie zur Seite „Verwalten > Anwendungseinstellungen > **Azure-Ressourcen**“. Ihre Seite „Azure-Ressourcen“ sollte ungefähr wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="65c8f-241">Navigate to the Manage > Application Settings > **Azure Resources** page, your Azure Resources page should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-6.png)

## <a name="connecting-the-unity-project-to-the-luis-app"></a><span data-ttu-id="65c8f-243">Verbinden des Unity-Projekts mit der LUIS-App</span><span class="sxs-lookup"><span data-stu-id="65c8f-243">Connecting the Unity project to the LUIS app</span></span>

<span data-ttu-id="65c8f-244">Klicken Sie auf der Seite Verwalten > Anwendungseinstellungen > **Azure-Ressourcen** auf das Symbol **Kopieren**, um die **Beispielabfrage** zu kopieren:</span><span class="sxs-lookup"><span data-stu-id="65c8f-244">On the Manage > Application Settings > **Azure Resources** page, click the **copy** icon to copy the **Example Query**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section4-step1-1.png)

<span data-ttu-id="65c8f-246">Wählen Sie wieder in Ihrem Unity-Projekt im Hierarchiefenster das Objekt **Lunarcom** aus, suchen Sie dann im Inspektor-Fenster die Komponente **Lunarcom Intent Recognizer (Script)** aus, und konfigurieren Sie sie wie folgt:</span><span class="sxs-lookup"><span data-stu-id="65c8f-246">Back in your Unity project, in the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, locate the **Lunarcom Intent Recognizer (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="65c8f-247">Fügen Sie in das Feld **LUIS-Endpunkt** die **Beispielabfrage** ein, die Sie im vorherigen Schritt kopiert hatten:</span><span class="sxs-lookup"><span data-stu-id="65c8f-247">In the **LUIS Endpoint** field, past the **Example Query** you copied in the previous step:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section4-step1-2.png)

## <a name="testing-and-improving-the-intent-recognition"></a><span data-ttu-id="65c8f-249">Testen und Verbessern der Absichtserkennung</span><span class="sxs-lookup"><span data-stu-id="65c8f-249">Testing and improving the intent recognition</span></span>

<span data-ttu-id="65c8f-250">Um Absichtserkennung direkt im Unity-Editor zu verwenden, müssen Sie Ihrem Entwicklungscomputer die Verwendung der Diktatfunktion erlauben.</span><span class="sxs-lookup"><span data-stu-id="65c8f-250">To use intent recognition directly in the Unity editor, you must allow your development computer to use dictation.</span></span> <span data-ttu-id="65c8f-251">Um diese Einstellung zu überprüfen, öffnen Sie Windows **Einstellungen**, wählen Sie dann **Datenschutz** > **Sprache** aus, und vergewissern Sie sich, dass **Online-Spracherkennung** aktiviert ist:</span><span class="sxs-lookup"><span data-stu-id="65c8f-251">To verify this setting, open Windows **Settings** then choose **Privacy** > **Speech** and ensure **Online speech recognition** is turned on:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-1.png)

<span data-ttu-id="65c8f-253">Wenn Sie jetzt in den Spielmodus wechseln, können Sie die Absichtserkennung testen, indem Sie zuerst auf die Raketenschaltfläche klicken.</span><span class="sxs-lookup"><span data-stu-id="65c8f-253">If you now enter Game mode, you can test the intent recognition by first pressing the rocket button.</span></span> <span data-ttu-id="65c8f-254">Angenommen, dass Ihr Computer über ein Mikrofon verfügt, sehen Sie dann, wenn Sie die erste Beispieläußerung **Fahre fort, starte die Rakete** sprechen, dass das LunarModule in den Weltraum abhebt:</span><span class="sxs-lookup"><span data-stu-id="65c8f-254">Then, assuming your computer has a microphone, when you say the first example utterance, **go ahead and launch the rocket**, you will see the LunarModule launch into space:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-2.png)

<span data-ttu-id="65c8f-256">Probieren Sie alle **Beispieläußerungen** und dann ebenso einige **Variationen der Beispieläußerungen** sowie einige **zufällige Äußerungen** aus.</span><span class="sxs-lookup"><span data-stu-id="65c8f-256">Try all the **example utterances**, then some **variation of the example utterances**, as well as, a few **random utterances**.</span></span>

<span data-ttu-id="65c8f-257">Kehren Sie als nächstes zu <a href="https://www.luis.ai" target="_blank">LUIS</a> zurück, navigieren Sie zur Seite Erstellen > App-Leistung verbessern > **Endpunktäußerungen überprüfen**, verwenden Sie die **Umschalt**-Schaltfläche, um von der Standardansicht „Entitäten“ zur **Tokenansicht** zu wechseln, und überprüfen Sie dann die Äußerungen:</span><span class="sxs-lookup"><span data-stu-id="65c8f-257">Next, return to <a href="https://www.luis.ai" target="_blank">LUIS</a> and navigate to Build > Improve app performance > **Review endpoint utterances** page, use the **toggle** button to switch from the default Entities View to **Tokens View**, and then review the utterances:</span></span>

* <span data-ttu-id="65c8f-258">Ändern und entfernen Sie in der Spalte **Äußerungen** die zugewiesenen Bezeichnungen nach Bedarf, sodass sie sich an Ihrer Absicht orientieren</span><span class="sxs-lookup"><span data-stu-id="65c8f-258">In the **Utterance** column, change and remove the assigned labels as needed so they align with your intent</span></span>
* <span data-ttu-id="65c8f-259">Überprüfen Sie in der Spalte **Zugeordnete Absicht**, ob die Absicht richtig ist</span><span class="sxs-lookup"><span data-stu-id="65c8f-259">In the **Aligned intent** column, verify that the intent is correct</span></span>
* <span data-ttu-id="65c8f-260">Klicken Sie in der Spalte **Hinzufügen/Löschen** auf die Schaltfläche mit dem grünen Markierungshäkchen, um die Äußerung hinzuzufügen, oder auf die Schaltfläche mit dem roten X, um sie zu löschen</span><span class="sxs-lookup"><span data-stu-id="65c8f-260">In the **Add/Delete** column, click the green check mark button to add the utterance or the red x button to delete it</span></span>

<span data-ttu-id="65c8f-261">Wenn Sie so viele Äußerungen überprüft haben, wie Sie möchten, klicken Sie auf die Schaltfläche **Trainieren**, um das Modell erneut zu trainieren, und dann auf die Schaltfläche **Veröffentlichen**, um die aktualisierte App erneut zu veröffentlichen:</span><span class="sxs-lookup"><span data-stu-id="65c8f-261">When you have reviewed as many utterances as you like, click the **Train** button to retrain the model, then the **Publish** button to republish the updated app:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-3.png)

> [!NOTE]
> <span data-ttu-id="65c8f-263">Wenn sich eine Endpunktäußerung nicht an der PressButton-Absicht orientiert, Sie aber möchten, dass für die Äußerung keine Absicht gilt, können Sie die zugewiesene Absicht in Keine ändern.</span><span class="sxs-lookup"><span data-stu-id="65c8f-263">If an endpoint utterance does not align with the PressButton intent, but you would like your model to know that the utterance has no intent, you can change the Aligned intent to None.</span></span>

<span data-ttu-id="65c8f-264">**Wiederholen** Sie diesen Vorgang so oft, wie Sie möchten, um Ihr App-Modell zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="65c8f-264">**Repeat** this process as many times as you like to improve your app model.</span></span>

## <a name="congratulations"></a><span data-ttu-id="65c8f-265">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="65c8f-265">Congratulations</span></span>

<span data-ttu-id="65c8f-266">Ihr Projekt verfügt jetzt über KI-gestützte Sprachbefehle, die es Ihrer Anwendung ermöglichen, die Absicht der Benutzer auch dann zu erkennen, wenn sie keine präzisen Befehle äußern.</span><span class="sxs-lookup"><span data-stu-id="65c8f-266">Your project now have AI-powered speech commands, allowing your application to recognize the users' intent even if they do not utter precise commands.</span></span> <span data-ttu-id="65c8f-267">Führen Sie die Anwendung auf Ihrem Gerät aus, um sicherzustellen, dass das Feature ordnungsgemäß funktioniert.</span><span class="sxs-lookup"><span data-stu-id="65c8f-267">Run the application on your device to ensure the feature is working properly.</span></span>