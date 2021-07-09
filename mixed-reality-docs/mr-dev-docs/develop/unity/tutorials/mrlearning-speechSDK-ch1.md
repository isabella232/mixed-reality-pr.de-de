---
title: 'Tutorials zu Azure Speech-Diensten: 1 Integrieren und Verwenden von Spracherkennung und Transkription'
description: In diesem Kurs erfahren Sie, wie Sie das Azure Speech SDK in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, MRTK, Mixed Reality Toolkit, UWP, Azure Spatial Anchors, Spracherkennung, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: a728e3520539723c4b38849eeb60524995e572eb
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175451"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a><span data-ttu-id="f2556-105">1. Integrieren und Verwenden von Spracherkennung und Transkription</span><span class="sxs-lookup"><span data-stu-id="f2556-105">1. Integrating and using speech recognition and transcription</span></span>

## <a name="overview"></a><span data-ttu-id="f2556-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="f2556-106">Overview</span></span>

<span data-ttu-id="f2556-107">In dieser Tutorialreihe erstellen Sie eine Mixed Reality-Anwendung, die die Verwendung von Azure Speech Services mit der HoloLens 2 untersucht.</span><span class="sxs-lookup"><span data-stu-id="f2556-107">In this tutorial series, you will create a Mixed Reality application that explores the use of Azure Speech Services with the HoloLens 2.</span></span> <span data-ttu-id="f2556-108">Wenn Sie diese Tutorialreihe durcharbeiten, können Sie das Mikrofon Ihres Geräts verwenden, um Spracheingaben in Echtzeit in Text zu übertragen, Ihre Sprache in andere Sprachen zu übersetzen und die Funktion zur Absichtserkennung nutzen, um Sprachbefehle mithilfe von künstlicher Intelligenz zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="f2556-108">When you complete this tutorial series, you will be able to use your device's microphone to transcribe speech to text in real time, translate your speech into other languages, and leverage the Intent recognition feature to understand voice commands using artificial intelligence.</span></span>

## <a name="objectives"></a><span data-ttu-id="f2556-109">Ziele</span><span class="sxs-lookup"><span data-stu-id="f2556-109">Objectives</span></span>

* <span data-ttu-id="f2556-110">Lernen, wie sich die Azure Speech Services in eine HoloLens 2-Anwendung integrieren lassen</span><span class="sxs-lookup"><span data-stu-id="f2556-110">Learn how to integrate Azure Speech Services with a HoloLens 2 application</span></span>
* <span data-ttu-id="f2556-111">Lernen, wie die Spracherkennung zum Umwandeln in Text verwendet werden kann</span><span class="sxs-lookup"><span data-stu-id="f2556-111">Learn how to use speech recognition to transcribe text</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f2556-112">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="f2556-112">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="f2556-113">Wenn Sie die Reihe [Tutorials zu den ersten Schritten](mr-learning-base-01.md) noch nicht abgeschlossen haben, empfiehlt es sich, zunächst diese Tutorials abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="f2556-113">If you have not completed the [Getting started tutorials](mr-learning-base-01.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="f2556-114">Ein Windows 10-PC, der mit den richtigen [Tools konfiguriert](../../install-the-tools.md) ist</span><span class="sxs-lookup"><span data-stu-id="f2556-114">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="f2556-115">Windows 10 SDK (10.0.18362.0 oder höher)</span><span class="sxs-lookup"><span data-stu-id="f2556-115">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="f2556-116">Grundlagenkenntnisse in der C#-Programmierung</span><span class="sxs-lookup"><span data-stu-id="f2556-116">Some basic C# programming ability</span></span>
* <span data-ttu-id="f2556-117">Ein für die [Entwicklung konfiguriertes](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) HoloLens 2-Gerät</span><span class="sxs-lookup"><span data-stu-id="f2556-117">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="f2556-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> mit installiertem Unity 2020/2019 LTS und hinzugefügtem Buildunterstützungsmodul für die Universelle Windows-Plattform</span><span class="sxs-lookup"><span data-stu-id="f2556-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2020/2019 LTS installed and the Universal Windows Platform Build Support module added</span></span>

> [!Important]
> <span data-ttu-id="f2556-119">Diese Tutorialreihe unterstützt Unity 2020 LTS (derzeit 2020.3.x), wenn Sie Open XR oder Windows XR-Plug-In und auch Unity 2019 LTS (derzeit 2019.4.x) verwenden, wenn Sie Legacy WSA oder das Windows XR-Plug-In verwenden.</span><span class="sxs-lookup"><span data-stu-id="f2556-119">This tutorial series supports Unity 2020 LTS(currently 2020.3.x) if you are using Open XR or Windows XR Plugin and also Unity 2019 LTS (currently 2019.4.x) if you are using Legacy WSA or Windows XR Plugin.</span></span> <span data-ttu-id="f2556-120">Diese Information hat Vorrang vor allen Unity-Versionsanforderungen, die in den oben verlinkten Voraussetzungen angegeben sind.</span><span class="sxs-lookup"><span data-stu-id="f2556-120">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="f2556-121">Erstellen und Vorbereiten des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="f2556-121">Creating and preparing the Unity project</span></span>

<span data-ttu-id="f2556-122">In diesem Abschnitt erstellen Sie ein neues Unity-Projekt und bereiten es für die MRTK-Entwicklung vor.</span><span class="sxs-lookup"><span data-stu-id="f2556-122">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="f2556-123">Befolgen Sie zu diesem Zweck zunächst die Anweisungen unter [Initialisieren des Projekts und der ersten Anwendung](mr-learning-base-02.md), jedoch ohne die Anweisungen zum [Erstellen Ihrer Anwendung auf Ihrem Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2), die die folgenden Schritte beinhalten:</span><span class="sxs-lookup"><span data-stu-id="f2556-123">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="f2556-124">[Erstellen eines neuen Unity-Projekts](mr-learning-base-02.md#creating-the-unity-project), das mit einem passenden Namen bezeichnet wird, beispielsweise *MRTK-Tutorials*</span><span class="sxs-lookup"><span data-stu-id="f2556-124">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
2. [<span data-ttu-id="f2556-125">Wechseln der Buildplattform</span><span class="sxs-lookup"><span data-stu-id="f2556-125">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
3. [<span data-ttu-id="f2556-126">Importieren der TextMeshPro Essential-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="f2556-126">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="f2556-127">Importieren des Mixed Reality Toolkits und Konfigurieren des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="f2556-127">Importing the Mixed Reality Toolkit and Configuring the Unity project</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. <span data-ttu-id="f2556-128">[Erstellen und Konfigurieren der Szene](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) und Bezeichnen der Szene mit einem passenden Namen, z. B. *AzureSpeechServices*</span><span class="sxs-lookup"><span data-stu-id="f2556-128">[Creating and configuring the scene](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) and give the scene a suitable name, for example, *AzureSpeechServices*</span></span>

<span data-ttu-id="f2556-129">Befolgen Sie dann die Anweisungen unter [Ändern der Anzeigeoption der räumlichen Wahrnehmung](mr-learning-base-03.md#changing-the-spatial-awareness-display-option), um sicherzustellen, dass das MRTK-Konfigurationsprofil für Ihre Szene **DefaultHoloLens2ConfigurationProfile** ist, und ändern Sie die Anzeigeoptionen für das Gittermodell zur räumlichen Wahrnehmung in **Occlusion** (Verdeckung).</span><span class="sxs-lookup"><span data-stu-id="f2556-129">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to ensure the MRTK configuration profile for your scene is **DefaultHoloLens2ConfigurationProfile**  and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="configuring-the-speech-commands-start-behavior"></a><span data-ttu-id="f2556-130">Konfigurieren des Startverhaltens der Sprachbefehle</span><span class="sxs-lookup"><span data-stu-id="f2556-130">Configuring the speech commands start behavior</span></span>

<span data-ttu-id="f2556-131">Da Sie das Speech SDK für die Spracherkennung und -Transkription verwenden, müssen Sie die MRTK-Sprachbefehle so konfigurieren, dass sie die Funktionalität des Speech SDKs nicht beeinträchtigen.</span><span class="sxs-lookup"><span data-stu-id="f2556-131">Because you will use the Speech SDK for speech recognition and transcription you need to configure the MRTK Speech Commands so they do not interfere with the Speech SDK functionality.</span></span> <span data-ttu-id="f2556-132">Um dies zu erreichen, können Sie das Startverhalten der Sprachbefehle vom automatischen Start auf manuellen Start umstellen.</span><span class="sxs-lookup"><span data-stu-id="f2556-132">To achieve this you can change the speech commands start behavior from Auto Start to Manual Start.</span></span>

<span data-ttu-id="f2556-133">Wählen Sie bei im Hierarchiefenster ausgewähltem **MixedRealityToolkit**-Objekt im Inspektorfenster die Registerkarte **Input** (Eingabe) aus, klonen Sie das **DefaultHoloLens2InputSystemProfile** und das **DefaultMixedRealitySpeechCommandsProfile**, und ändern Sie dann die Sprachbefehle **Start Behavior** (Startverhalten) in **Manual Start** (Manueller Start):</span><span class="sxs-lookup"><span data-stu-id="f2556-133">With the **MixedRealityToolkit** object selected in the Hierarchy window, in the Inspector window, select the **Input** tab, clone the **DefaultHoloLens2InputSystemProfile** and the **DefaultMixedRealitySpeechCommandsProfile**, and then change the speech commands **Start Behavior** to **Manual Start**:</span></span>

![mrlearning-speech 1](images/mrlearning-speech/tutorial1-section2-step1-1.png)

## <a name="configuring-the-capabilities"></a><span data-ttu-id="f2556-135">Konfigurieren der Funktionen</span><span class="sxs-lookup"><span data-stu-id="f2556-135">Configuring the capabilities</span></span>

<span data-ttu-id="f2556-136">Wählen Sie im Unity-Menü **Edit** > **Project Settings...** (Bearbeiten > Projekteinstellungen) aus, um das Fenster mit den Player-Einstellungen zu öffnen, und suchen Sie dann den Abschnitt **Player** >  **Publishing Settings** (Player > Veröffentlichungseinstellungen):</span><span class="sxs-lookup"><span data-stu-id="f2556-136">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Publishing Settings** section:</span></span>

![mrlearning-speech 2](images/mrlearning-speech/tutorial1-section3-step1-1.png)

<span data-ttu-id="f2556-138">Scrollen Sie in den **Publishing Settings** nach unten zum Abschnitt **Capabilities** (Funktionen), und vergewissern Sie sich, dass die Funktionen **InternetClient**, **Microphone** und **SpatialPerception**, die im Rahmen der Erstellung des Projekts zu Beginn des Tutorials erstellt wurden, aktiviert sind.</span><span class="sxs-lookup"><span data-stu-id="f2556-138">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which was enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="f2556-139">Aktivieren Sie dann die Funktionen **InternetClientServer** und **PrivateNetworkClientServer**:</span><span class="sxs-lookup"><span data-stu-id="f2556-139">Then, enable the **InternetClientServer** and **PrivateNetworkClientServer** capabilities:</span></span>

![mrlearning-speech 3](images/mrlearning-speech/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="f2556-141">Importieren der Tutorialressourcen</span><span class="sxs-lookup"><span data-stu-id="f2556-141">Importing the tutorial assets</span></span>

<span data-ttu-id="f2556-142">Laden Sie die folgenden benutzerdefinierten Unity-Pakete herunter, und **importieren** Sie sie **in der Reihenfolge, in der sie aufgelistet sind**:</span><span class="sxs-lookup"><span data-stu-id="f2556-142">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="f2556-143">[Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage) (latest version)</span><span class="sxs-lookup"><span data-stu-id="f2556-143">[Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage) (latest version)</span></span>
* [<span data-ttu-id="f2556-144">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="f2556-144">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [<span data-ttu-id="f2556-145">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.5.2.unitypackage</span><span class="sxs-lookup"><span data-stu-id="f2556-145">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.5.2.unitypackage</span></span>](https://github.com/onginnovations/MixedRealityLearning/releases/download/azure-speech-services-v2.5.2/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.5.2.unitypackage)

> [!TIP]
> <span data-ttu-id="f2556-146">Wenn Sie eine Auffrischung zum Importieren eines benutzerdefinierten Unity-Pakets benötigen, lesen Sie die Anweisungen unter [Importieren des Mixed Reality-Toolkits](mr-learning-base-04.md#importing-the-tutorial-assets).</span><span class="sxs-lookup"><span data-stu-id="f2556-146">For a reminder on how to import a Unity custom package, you can refer to the [Importing the Mixed Reality Toolkit](mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>

<span data-ttu-id="f2556-147">Nach dem Importieren der Tutorialressourcen sollte Ihr Projektfenster ähnlich wie die folgende Abbildung aussehen:</span><span class="sxs-lookup"><span data-stu-id="f2556-147">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-speech 4](images/mrlearning-speech/tutorial1-section4-step1-1.png)

<span data-ttu-id="f2556-149">Sie müssen das Unity-Projekt einrichten, um die Azure Speech-Plug-Ins für ARM64 zu veröffentlichen. Navigieren Sie hierzu im Project-Fenster zu **Assets** > **SpeechSDK** > **Plugins** > **WSA** > **ARM64**, und wählen Sie das **Microsoft.CognitiveServices.Speech.core**-Plug-In aus.</span><span class="sxs-lookup"><span data-stu-id="f2556-149">You need to setup the Unity project to publish the Azure Speech plugins for ARM64,to do this in the Project window, navigate to **Assets** > **SpeechSDK** > **Plugins** > **WSA** > **ARM64** and select **Microsoft.CognitiveServices.Speech.core** plugin.</span></span>

![mrlearning-speech 5](images/mrlearning-speech/tutorial1-section4-step1-2.PNG)

<span data-ttu-id="f2556-151">Aktivieren Sie bei immer noch ausgewähltem **Microsoft.CognitiveServices.Speech.core**-Plug-In im Insptktorfenster den **WSA Player**, wählen Sie dann unter **Plattformeinstellungen** die Option **UWP** für SDK und **ARM64** für CPU aus, und klicken Sie auf „Übernehmen“, um diese Einstellungen auf das Plug-In anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="f2556-151">with **Microsoft.CognitiveServices.Speech.core** plugin still selected, in the inspector window Enable **WSA Player** then under **Platform settings** select **UWP** for SDK, **ARM64** for CPU and click on Apply to apply these settings to the plugin.</span></span>

![mrlearning-speech 6](images/mrlearning-speech/tutorial1-section4-step1-3.PNG)

<span data-ttu-id="f2556-153">Wiederholen Sie diese Schritte für jedes der verbleibenden Plug-Ins:</span><span class="sxs-lookup"><span data-stu-id="f2556-153">Repeat this steps for each of the remaining plugins:</span></span>

* <span data-ttu-id="f2556-154">**Microsoft.CognitiveServices.Speech.extension.audio.sys**</span><span class="sxs-lookup"><span data-stu-id="f2556-154">**Microsoft.CognitiveServices.Speech.extension.audio.sys**</span></span>
* <span data-ttu-id="f2556-155">**Microsoft.CognitiveServices.Speech.extension.kws**</span><span class="sxs-lookup"><span data-stu-id="f2556-155">**Microsoft.CognitiveServices.Speech.extension.kws**</span></span>
* <span data-ttu-id="f2556-156">**Microsoft.CognitiveServices.Speech.extension.lu**</span><span class="sxs-lookup"><span data-stu-id="f2556-156">**Microsoft.CognitiveServices.Speech.extension.lu**</span></span>
* <span data-ttu-id="f2556-157">**Microsoft.CognitiveServices.Speech.extension.silk_codec**</span><span class="sxs-lookup"><span data-stu-id="f2556-157">**Microsoft.CognitiveServices.Speech.extension.silk_codec**</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="f2556-158">Vorbereiten der Szene</span><span class="sxs-lookup"><span data-stu-id="f2556-158">Preparing the scene</span></span>

<span data-ttu-id="f2556-159">In diesem Abschnitt bereiten Sie die Szene vor, indem Sie das Prefab für das Tutorial hinzufügen und die Komponente „Lunarcom Controller (Skript)“ konfigurieren, um Ihre Szene zu steuern.</span><span class="sxs-lookup"><span data-stu-id="f2556-159">In this section, you will prepare the scene by adding the tutorial prefab and configure the Lunarcom Controller (Script) component to control your scene.</span></span>

<span data-ttu-id="f2556-160">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.AzureSpeechServices** > **Prefabs**, und ziehen Sie das **Lunarcom**-Prefab auf das Hierarchiefenster, um es Ihrer Szene hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="f2556-160">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpeechServices** > **Prefabs** folder and drag the **Lunarcom** prefab into the Hierarchy window to add it to your scene:</span></span>

![mrlearning-speech 7](images/mrlearning-speech/tutorial1-section5-step1-1.png)

<span data-ttu-id="f2556-162">Verwenden Sie bei im Hierarchiefenster ausgewähltem **Lunarcom**-Objekt im Inspektorfenster die Schaltfläche **Komponente hinzufügen**, um die Komponente **Lunarcom Controller (Script)** zum Lunarcom-Objekt hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="f2556-162">With the **Lunarcom** object still selected in the Hierarchy window, in the Inspector window, use the **Add Component** button to add the **Lunarcom Controller (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech 8](images/mrlearning-speech/tutorial1-section5-step1-2.png)

> [!NOTE]
> <span data-ttu-id="f2556-164">Die Komponente „Lunarcom Controller (Script)“ ist kein Bestandteil des MRTK.</span><span class="sxs-lookup"><span data-stu-id="f2556-164">The Lunarcom Controller (Script) component is not part of MRTK.</span></span> <span data-ttu-id="f2556-165">Sie wurde zusammen mit den Ressourcen für dieses Tutorial zur Verfügung gestellt.</span><span class="sxs-lookup"><span data-stu-id="f2556-165">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="f2556-166">Klappen Sie das noch ausgewählte **Lunarcom**-Objekt auf, um seine untergeordneten Objekte anzuzeigen, und ziehen Sie dann das **Terminal**-Objekt auf das **Terminal**-Feld der Lunarcom Controller (Script)-Komponente:</span><span class="sxs-lookup"><span data-stu-id="f2556-166">With the **Lunarcom** object still selected, expand it to reveal its child objects, then drag the **Terminal** object into the Lunarcom Controller (Script) component's **Terminal** field:</span></span>

![mrlearning-speech 9](images/mrlearning-speech/tutorial1-section5-step1-3.png)

<span data-ttu-id="f2556-168">Klappen Sie bei noch ausgewähltem **Lunarcom**-Objekt das Terminal-Objekt auf, um seine untergeordneten Objekte anzuzeigen, ziehen Sie dann das **ConnectionLight**-Objekt auf das **ConnectionLight**-Feld der Lunarcom Controller (Script)-Komponente und das **OutputText**-Objekt auf das **Output Text**-Feld:</span><span class="sxs-lookup"><span data-stu-id="f2556-168">With the **Lunarcom** object still selected, expand the Terminal object to reveal its child objects, then drag the **ConnectionLight** object into the Lunarcom Controller (Script) component's **Connection Light** field and the **OutputText** object into the **Output Text** field:</span></span>

![mrlearning-speech 10](images/mrlearning-speech/tutorial1-section5-step1-4.png)

<span data-ttu-id="f2556-170">Klappen Sie bei noch ausgewähltem **Lunarcom**-Objekt das Buttons-Objekt auf, um seine untergeordneten Objekte anzuzeigen, und klappen Sie dann im Inspektorfenster die **Buttons**-Liste auf, legen Sie seine **Size** (Größe) auf 3 fest, und ziehen Sie die Objekte **MicButton**, **SatelliteButton** und **RocketButton** auf die **Element**-Felder 0, 1 bzw. 2:</span><span class="sxs-lookup"><span data-stu-id="f2556-170">With the **Lunarcom** object still selected, expand the Buttons object to reveal its child objects, and then in the Inspector window, expand the **Buttons** list, set its **Size** to 3, and drag the **MicButton**, **SatelliteButton**, and **RocketButton** objects into the **Element** 0, 1, and 2 fields respectively:</span></span>

![mrlearning-speech 11](images/mrlearning-speech/tutorial1-section5-step1-5.png)

## <a name="connecting-the-unity-project-to-the-azure-resource"></a><span data-ttu-id="f2556-172">Verbinden des Unity-Projekts mit der Azure-Ressource</span><span class="sxs-lookup"><span data-stu-id="f2556-172">Connecting the Unity project to the Azure resource</span></span>

<span data-ttu-id="f2556-173">Um Azure Speech Services zu verwenden, müssen Sie eine Azure-Ressource erstellen und einen API-Schlüssel für den Speech Service abrufen.</span><span class="sxs-lookup"><span data-stu-id="f2556-173">To use Azure Speech Services, you need to create an Azure resource and obtain an API key for the Speech Service.</span></span> <span data-ttu-id="f2556-174">Befolgen Sie die Anweisungen unter [Speech Service kostenlos testen](/azure/cognitive-services/speech-service/get-started), und notieren Sie sich Ihre Dienstregion (auch als Standort bezeichnet) und den API-Schlüssel (auch als Schlüssel1 oder Schlüssel2 bezeichnet).</span><span class="sxs-lookup"><span data-stu-id="f2556-174">Follow the [Try the Speech service for free](/azure/cognitive-services/speech-service/get-started) instructions and make a note of your service region (also known as Location) and API key (also known as Key1 or Key2).</span></span>

<span data-ttu-id="f2556-175">Wählen Sie in Ihrem Hierarchiefenster das **Lunarcom**-Objekt aus, suchen Sie dann im Inspektorfenster den Abschnitt **Speech SDK Credentials** der **Lunarcom Controller (Script)** -Komponente, und konfigurieren Sie ihn wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f2556-175">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, locate the **Lunarcom Controller (Script)** component's **Speech SDK Credentials** section and configure it as follows:</span></span>

* <span data-ttu-id="f2556-176">Geben Sie im Feld **Speech Service API Key** Ihren API-Schlüssel (Schlüssel1 oder Schlüssel2) ein</span><span class="sxs-lookup"><span data-stu-id="f2556-176">In the **Speech Service API Key** field, enter your API key (Key1 or Key2)</span></span>
* <span data-ttu-id="f2556-177">Geben Sie im Feld **Speech Service Region** Ihre Dienstregion (Standort) ein. Verwenden Sie dazu Kleinbuchstaben, und entfernen Sie alle Leerzeichen.</span><span class="sxs-lookup"><span data-stu-id="f2556-177">In the **Speech Service Region** field, enter your service region (Location) using lowercase letters and spaces removed</span></span>

![mrlearning-speech 12](images/mrlearning-speech/tutorial1-section6-step1-1.png)

## <a name="using-speech-recognition-to-transcribe-speech"></a><span data-ttu-id="f2556-179">Verwenden der Spracherkennung zum Transkribieren von Sprache</span><span class="sxs-lookup"><span data-stu-id="f2556-179">Using speech recognition to transcribe speech</span></span>

<span data-ttu-id="f2556-180">Wählen Sie im Hierarchiefenster das **Lunarcom**-Objekt aus, und verwenden Sie dann im Inspektorfenster die Schaltfläche **Komponente hinzufügen**, um dem Lunarcom-Objekt die Komponente **Lunarcom Speech Recognizer (Script)** hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="f2556-180">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Speech Recognizer (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech 13](images/mrlearning-speech/tutorial1-section7-step1-1.png)

> [!NOTE]
> <span data-ttu-id="f2556-182">Die Komponente „Lunarcom Speech Recognizer (Script)“ ist kein Bestandteil des MRTK.</span><span class="sxs-lookup"><span data-stu-id="f2556-182">The Lunarcom Speech Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="f2556-183">Sie wurde zusammen mit den Ressourcen für dieses Tutorial zur Verfügung gestellt.</span><span class="sxs-lookup"><span data-stu-id="f2556-183">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="f2556-184">Wenn Sie jetzt in den Spielmodus wechseln, können Sie die Spracherkennung testen, indem Sie zuerst auf die Mikrofonschaltfläche klicken.</span><span class="sxs-lookup"><span data-stu-id="f2556-184">If you now enter Game mode, you can test the speech recognition by first pressing the microphone button:</span></span>

![mrlearning-speech 14](images/mrlearning-speech/tutorial1-section7-step1-2.png)

<span data-ttu-id="f2556-186">Falls Ihr Computer über ein Mikrofon verfügt, wird Ihre Sprache dann, wenn Sie etwas sagen, im Terminalbereich transkribiert:</span><span class="sxs-lookup"><span data-stu-id="f2556-186">Then, assuming your computer has a microphone, when you say something, your speech will be transcribed on the terminal panel:</span></span>

![mrlearning-speech 15](images/mrlearning-speech/tutorial1-section7-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="f2556-188">Die Anwendung muss eine Verbindung mit Azure herstellen, achten Sie also darauf, dass Ihr Computer/Gerät mit dem Internet verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="f2556-188">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="f2556-189">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="f2556-189">Congratulations</span></span>

<span data-ttu-id="f2556-190">Sie haben die von Azure unterstützte Spracherkennung implementiert.</span><span class="sxs-lookup"><span data-stu-id="f2556-190">You have implemented speech recognition powered by Azure.</span></span> <span data-ttu-id="f2556-191">Führen Sie die Anwendung auf Ihrem Gerät aus, um sicherzustellen, dass das Feature ordnungsgemäß funktioniert.</span><span class="sxs-lookup"><span data-stu-id="f2556-191">Run the application on your device to ensure the feature is working properly.</span></span>

<span data-ttu-id="f2556-192">Im nächsten Tutorial erfahren Sie, wie Sie Befehle mit der Azure-Spracherkennung ausführen.</span><span class="sxs-lookup"><span data-stu-id="f2556-192">In the next tutorial, you will learn how to execute commands using Azure speech recognition.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f2556-193">Nächstes Tutorial: 2. Verwenden der Spracherkennung zum Ausführen von Befehlen</span><span class="sxs-lookup"><span data-stu-id="f2556-193">Next tutorial: 2. Using speech recognition to execute commands</span></span>](mrlearning-speechSDK-ch2.md)
