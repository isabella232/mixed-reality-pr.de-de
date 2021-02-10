---
title: Einrichten von Photon Unity Networking
description: In diesem Kurs lernen Sie, wie Sie Photon Unity Network in einer HoloLens 2-Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, Mehrbenutzerfunktionen, Photon, MRTK, Mixed Reality Toolkit, UWP, Azure Spatial Anchors, PUN
ms.localizationpriority: high
ms.openlocfilehash: 372cb7c9516a994cb7c3da1efb6cade792e862d1
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590312"
---
# <a name="2-setting-up-photon-unity-networking"></a><span data-ttu-id="72451-104">2. Einrichten von Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="72451-104">2. Setting up Photon Unity Networking</span></span>

<span data-ttu-id="72451-105">In diesem Tutorial bereiten Sie sich mithilfe des Photon Unity-Netzwerks (PUN) auf das Erstellen einer gemeinsamen Benutzeroberfläche vor.</span><span class="sxs-lookup"><span data-stu-id="72451-105">In this tutorial, you will prepare for creating a shared experience using Photon Unity Networking (PUN).</span></span> <span data-ttu-id="72451-106">Sie erfahren, wie Sie eine PUN-App erstellen, PUN-Ressourcen in Ihr Unity-Projekt importieren und Ihr Unity-Projekt mit der PUN-App verbinden.</span><span class="sxs-lookup"><span data-stu-id="72451-106">You will learn how to create a PUN app, import PUN assets into your Unity project, and connect your Unity project to the PUN app.</span></span>

## <a name="objectives"></a><span data-ttu-id="72451-107">Ziele</span><span class="sxs-lookup"><span data-stu-id="72451-107">Objectives</span></span>

* <span data-ttu-id="72451-108">Erfahren, wie eine PUN-App erstellt wird</span><span class="sxs-lookup"><span data-stu-id="72451-108">Learn how to create a PUN app</span></span>
* <span data-ttu-id="72451-109">Erfahren, wie die PUN-Ressourcen gesucht und importiert werden</span><span class="sxs-lookup"><span data-stu-id="72451-109">Learn how to find and import the PUN assets</span></span>
* <span data-ttu-id="72451-110">Erfahren, wie eine Verbindung Ihres Unity-Projekts mit der PUN-App hergestellt wird</span><span class="sxs-lookup"><span data-stu-id="72451-110">Learn how to connect your Unity project to the PUN app</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="72451-111">Erstellen und Vorbereiten des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="72451-111">Creating and preparing the Unity project</span></span>

<span data-ttu-id="72451-112">In diesem Abschnitt erstellen Sie ein neues Unity-Projekt und bereiten es für die MRTK-Entwicklung vor.</span><span class="sxs-lookup"><span data-stu-id="72451-112">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="72451-113">Befolgen Sie zunächst die Anweisungen unter [Initialisieren Ihres Projekts und Bereitstellen Ihrer ersten Anwendung](mr-learning-base-02.md) – jedoch ohne die Anweisungen zum [Erstellen Ihrer Anwendung auf Ihrem Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2) –, die die folgenden Schritte beinhalten:</span><span class="sxs-lookup"><span data-stu-id="72451-113">First, follow the [Initializing your project and deploying your first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="72451-114">[Erstellen eines neuen Unity-Projekts](mr-learning-base-02.md#creating-the-unity-project), das mit einem passenden Namen bezeichnet wird, beispielsweise *MRTK-Tutorials*</span><span class="sxs-lookup"><span data-stu-id="72451-114">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
2. [<span data-ttu-id="72451-115">Wechseln der Buildplattform</span><span class="sxs-lookup"><span data-stu-id="72451-115">Switching the build platform</span></span>](mr-learning-base-02.md#switching-the-build-platform)
3. [<span data-ttu-id="72451-116">Importieren der TextMeshPro Essential-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="72451-116">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="72451-117">Importieren des Mixed Reality-Toolkits</span><span class="sxs-lookup"><span data-stu-id="72451-117">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
5. [<span data-ttu-id="72451-118">Konfigurieren des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="72451-118">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
6. <span data-ttu-id="72451-119">[Erstellen und Konfigurieren der Szene](mr-learning-base-02.md#creating-and-configuring-the-scene) und Bezeichnen der Szene mit einem passenden Namen, z. B. *MultiUserCapabilities*</span><span class="sxs-lookup"><span data-stu-id="72451-119">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *MultiUserCapabilities*</span></span>

<span data-ttu-id="72451-120">Befolgen Sie dann die Anweisungen unter [Ändern der Anzeigeoptionen für räumliche Wahrnehmung](mr-learning-base-03.md#changing-the-spatial-awareness-display-option), um die folgenden Aufgaben auszuführen:</span><span class="sxs-lookup"><span data-stu-id="72451-120">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to:</span></span>

1. <span data-ttu-id="72451-121">Ändern des **MRTK-Konfigurationsprofils** in **DefaultHoloLens2ConfigurationProfile**.</span><span class="sxs-lookup"><span data-stu-id="72451-121">Change the **MRTK configuration profile** for to the **DefaultHoloLens2ConfigurationProfile**</span></span>
1. <span data-ttu-id="72451-122">Ändern der **Anzeigeoptionen für das Gittermodell für räumliche Wahrnehmung** in **Occlusion** (Verdeckung).</span><span class="sxs-lookup"><span data-stu-id="72451-122">Change the **spatial awareness mesh display options** to **Occlusion**.</span></span>

## <a name="enabling-additional-capabilities"></a><span data-ttu-id="72451-123">Aktivieren zusätzlicher Funktionen</span><span class="sxs-lookup"><span data-stu-id="72451-123">Enabling additional capabilities</span></span>

<span data-ttu-id="72451-124">Wählen Sie im Unity-Menü **Edit** > **Project Settings...** (Bearbeiten > Projekteinstellungen) aus, um das Fenster mit den Player-Einstellungen zu öffnen, und suchen Sie dann den Abschnitt **Player** >  **Publishing Settings** (Player > Veröffentlichungseinstellungen):</span><span class="sxs-lookup"><span data-stu-id="72451-124">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Publishing Settings** section:</span></span>

![Unity: Player-Einstellungen](images/mr-learning-sharing/sharing-02-section2-step1-1.png)

<span data-ttu-id="72451-126">Scrollen Sie in **Publishing Settings** (Veröffentlichungseinstellungen) nach unten zum Abschnitt **Capabilities** (Funktionen), und vergewissern Sie sich, dass die Funktionen **InternetClient**, **Microphone**, **SpatialPerception** und **GazeInput**, die Sie im Schritt [Konfigurieren des Unity-Projekts](mr-learning-base-02.md#configuring-the-unity-project) weiter oben aktiviert haben, aktiviert sind.</span><span class="sxs-lookup"><span data-stu-id="72451-126">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, **SpatialPerception**, and **GazeInput** capabilities, which you enabled during the [Configuring the Unity project](mr-learning-base-02.md#configuring-the-unity-project) step above, are enabled.</span></span>

<span data-ttu-id="72451-127">Aktivieren Sie dann die folgenden zusätzlichen Funktionen:</span><span class="sxs-lookup"><span data-stu-id="72451-127">Then enable the following additional capabilities:</span></span>

* <span data-ttu-id="72451-128">**InternetClientServer**-Funktion</span><span class="sxs-lookup"><span data-stu-id="72451-128">**InternetClientServer** capability</span></span>
* <span data-ttu-id="72451-129">**PrivateNetworkClientServer**-Funktion</span><span class="sxs-lookup"><span data-stu-id="72451-129">**PrivateNetworkClientServer** capability</span></span>

![Einstellungen für Unity-Funktionen](images/mr-learning-sharing/sharing-02-section2-step1-2.png)

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="72451-131">Installieren von integrierten Unity-Paketen</span><span class="sxs-lookup"><span data-stu-id="72451-131">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="72451-132">Wählen Sie im Unity-Menü **Fenster** > **Package Manager** (Paket-Manager) aus, um das Fenster „Package Manager“ zu öffnen, wählen Sie **AR Foundation** aus, und klicken Sie auf die Schaltfläche **Install** (Installieren), um das Paket zu installieren:</span><span class="sxs-lookup"><span data-stu-id="72451-132">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** and click the **Install** button to install the package:</span></span>

![Unity-Paket-Manager mit ausgewählter AR Foundation](images/mr-learning-sharing/sharing-02-section3-step1-1.png)

> [!NOTE]
> <span data-ttu-id="72451-134">Sie installieren das AR Foundation-Paket, da es für das Azure Spatial Anchor SDK erforderlich ist, das Sie im nächsten Abschnitt importieren.</span><span class="sxs-lookup"><span data-stu-id="72451-134">You are installing the AR Foundation package because it is required by the Azure Spatial Anchors SDK you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="72451-135">Importieren der Tutorialressourcen</span><span class="sxs-lookup"><span data-stu-id="72451-135">Importing the tutorial assets</span></span>

<span data-ttu-id="72451-136">Fügen Sie Ihrem Unity-Projekt das AzurespatialAnchors SDK V2.7.1 hinzu. Um die Pakete hinzuzufügen, befolgen Sie dieses [Tutorial](https://docs.microsoft.com/en-us/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage).</span><span class="sxs-lookup"><span data-stu-id="72451-136">Add AzurespatialAnchors SDK V2.7.1 into your unity project, to add the packages please follow this [tutorial](https://docs.microsoft.com/en-us/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span></span>


<span data-ttu-id="72451-137">Laden Sie die folgenden benutzerdefinierten Unity-Pakete herunter, und **importieren** Sie sie **in der Reihenfolge, in der sie aufgelistet sind**:</span><span class="sxs-lookup"><span data-stu-id="72451-137">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>
 
* [<span data-ttu-id="72451-138">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="72451-138">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [<span data-ttu-id="72451-139">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="72451-139">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage)
* [<span data-ttu-id="72451-140">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="72451-140">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage)

<span data-ttu-id="72451-141">Nach dem Importieren der Tutorialressourcen sollte Ihr Projektfenster ähnlich wie die folgende Abbildung aussehen:</span><span class="sxs-lookup"><span data-stu-id="72451-141">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![Unity-Fenster „Hierarchie“, „Szene“ und „Projekt“ nach dem Importieren der Tutorialressourcen](images/mr-learning-sharing/sharing-02-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="72451-143">Wenn Sie eine Auffrischung zum Importieren eines benutzerdefinierten Unity-Pakets benötigen, lesen Sie die Anweisungen unter [Importieren der Tutorialressourcen](mr-learning-base-04.md#importing-the-tutorial-assets).</span><span class="sxs-lookup"><span data-stu-id="72451-143">For a reminder on how to import a Unity custom package, you can refer to the [Importing the tutorial assets](mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>

> [!NOTE]
> <span data-ttu-id="72451-144">Nach dem Importieren des Pakets mit den MultiUserCapabilities-Tutorialressourcen werden im Konsolenfenster mehrere [CS0246](/dotnet/csharp/language-reference/compiler-messages/cs0246)-Fehler angezeigt, die besagen, dass der Typ oder Namespace fehlt.</span><span class="sxs-lookup"><span data-stu-id="72451-144">After importing the MultiUserCapabilities tutorial assets package, you will see several [CS0246](/dotnet/csharp/language-reference/compiler-messages/cs0246) errors in the Console window stating that the type or namespace is missing.</span></span> <span data-ttu-id="72451-145">Dies ist das erwartungsgemäße Verhalten, das im nächsten Abschnitt durch das Importieren der PUN-Ressourcen behoben wird.</span><span class="sxs-lookup"><span data-stu-id="72451-145">This is expected and will be resolved in the next section when you import the PUN assets.</span></span>

## <a name="importing-the-pun-assets"></a><span data-ttu-id="72451-146">Importieren der PUN-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="72451-146">Importing the PUN assets</span></span>

<span data-ttu-id="72451-147">Wählen Sie im Unity-Menü **Window** > **Asset Store** (Fenster > Asset Store) aus, um das Asset Store-Fenster zu öffnen, suchen Sie unter „Exit Games“ **PUN 2 - FREE** aus, und klicken Sie dann auf die Schaltfläche **Download**, um das Ressourcenpaket in Ihr Unity-Konto herunterzuladen.</span><span class="sxs-lookup"><span data-stu-id="72451-147">In the Unity menu, select **Window** > **Asset Store** to open the Asset Store window, search for and select **PUN 2 - FREE** from Exit Games, click the **Download** button to download the asset package to your Unity account.</span></span>

<span data-ttu-id="72451-148">Wenn der Download abgeschlossen ist, klicken Sie auf die **Import**-Schaltfläche, um das Fenster Import Unity Package (Unity-Paket importieren) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="72451-148">When the download is complete, click the **Import** button to open the Import Unity Package window:</span></span>

![Unity Asset Store mit „PUN 2 – Free“](images/mr-learning-sharing/sharing-02-section5-step1-1.png)

<span data-ttu-id="72451-150">Klicken Sie im Import Unity Package-Fenster (Unity-Paket importieren) auf die Schaltfläche **All** (Alle), um sicherzustellen, dass alle Assets ausgewählt sind, und klicken Sie dann auf die Schaltfläche **Import** (Importieren), um die Assets zu importieren:</span><span class="sxs-lookup"><span data-stu-id="72451-150">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![Unity mit Fenster zum Importieren von PUN 2](images/mr-learning-sharing/sharing-02-section5-step1-2.png)

<span data-ttu-id="72451-152">Nachdem Unity den Importvorgang abgeschlossen hat, wird das Fenster des PUN-Assistenten mit geöffnetem PUN-Setupmenü geladen. Für den Augenblick können Sie dieses Fenster ignorieren oder schließen:</span><span class="sxs-lookup"><span data-stu-id="72451-152">Once Unity has completed the import process, the Pun Wizard window will appear with the PUN Setup menu loaded, you can ignore or close this window for now:</span></span>

![Unity mit Fenster zum Einrichten von PUN 2](images/mr-learning-sharing/sharing-02-section5-step1-3.png)

## <a name="creating-the-pun-application"></a><span data-ttu-id="72451-154">Erstellen der PUN-Anwendung</span><span class="sxs-lookup"><span data-stu-id="72451-154">Creating the PUN application</span></span>

<span data-ttu-id="72451-155">In diesem Abschnitt erstellen Sie ein Photon-Konto, falls dies noch nicht geschehen ist, und Sie erstellen eine neue PUN-App.</span><span class="sxs-lookup"><span data-stu-id="72451-155">In this section, you will create a Photon account, if you don't already have one, and create a new PUN app.</span></span>

<span data-ttu-id="72451-156">Navigieren Sie zum Photon-<a href="https://dashboard.photonengine.com/account/signin" target="_blank">Dashboard</a>, und melden Sie sich an, wenn Sie bereits über ein Konto verfügen, das Sie verwenden möchten, oder klicken Sie andernfalls auf den Link **Create One** (Konto erstellen), und befolgen Sie die Anweisungen zum Registrieren eines neuen Kontos:</span><span class="sxs-lookup"><span data-stu-id="72451-156">Navigate to the Photon <a href="https://dashboard.photonengine.com/account/signin" target="_blank">dashboard</a> and sign in if you already have an account you want to use, otherwise, click the **Create One** link and follow the instructions to register a new account:</span></span>

![Photon-Anmeldeseite](images/mr-learning-sharing/sharing-02-section6-step1-1.png)

<span data-ttu-id="72451-158">Nachdem Sie sich angemeldet haben, klicken Sie auf die Schaltfläche **Create a New App** (Neue App erstellen):</span><span class="sxs-lookup"><span data-stu-id="72451-158">Once signed in, click the **Create a New App** button:</span></span>

![Die Seite „Willkommen“ des Photon-Dashboards](images/mr-learning-sharing/sharing-02-section6-step1-2.png)

<span data-ttu-id="72451-160">Geben Sie auf der Seite „Create a New Application“ (Neue Anwendung erstellen) die folgenden Werte ein:</span><span class="sxs-lookup"><span data-stu-id="72451-160">On the Create a New Application page, enter the following values:</span></span>

* <span data-ttu-id="72451-161">Wählen Sie als Photon-Typ „PUN“ aus.</span><span class="sxs-lookup"><span data-stu-id="72451-161">For Photon Type, select PUN</span></span>
* <span data-ttu-id="72451-162">Geben Sie als Namen einen passenden Namen ein, beispielsweise _MRTK-Tutorials_</span><span class="sxs-lookup"><span data-stu-id="72451-162">For Name, enter a suitable name, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="72451-163">Geben Sie als Beschreibung optional eine passende Beschreibung ein</span><span class="sxs-lookup"><span data-stu-id="72451-163">For Description, optionally enter a suitable description</span></span>
* <span data-ttu-id="72451-164">Lassen Sie das Feld „URL“ leer</span><span class="sxs-lookup"><span data-stu-id="72451-164">For Url, leave the field empty</span></span>

<span data-ttu-id="72451-165">Klicken Sie dann auf die Schaltfläche **Create** (Erstellen), um die neue App zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="72451-165">Then click the **Create** button to create the new app:</span></span>

![Photon-Seite „Anwendung erstellen“](images/mr-learning-sharing/sharing-02-section6-step1-3.png)

<span data-ttu-id="72451-167">Nachdem Photon den Erstellungsvorgang abgeschlossen hat, wird die neue PUN-App auf Ihrem Dashboard angezeigt:</span><span class="sxs-lookup"><span data-stu-id="72451-167">Once Photon has finished the creation process, the new PUN app will appear on your dashboard:</span></span>

![Photon-Seite „Anwendung“](images/mr-learning-sharing/sharing-02-section6-step1-4.png)

## <a name="connecting-the-unity-project-to-the-pun-application"></a><span data-ttu-id="72451-169">Verbinden des Unity-Projekts mit der PUN-Anwendung</span><span class="sxs-lookup"><span data-stu-id="72451-169">Connecting the Unity project to the PUN application</span></span>

<span data-ttu-id="72451-170">In diesem Abschnitt verbinden Sie Ihr Unity-Projekt mit der PUN-App, die Sie im vorherigen Abschnitt erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="72451-170">In this section, you will connect your Unity project to the PUN app you created in the previous section.</span></span>

<span data-ttu-id="72451-171">Klicken Sie auf dem Photon-Dashboard auf das Feld **App-ID**, um die App-ID anzuzeigen, und kopieren Sie sie dann in die Zwischenablage:</span><span class="sxs-lookup"><span data-stu-id="72451-171">On the Photon dashboard, click the **App ID** field to reveal the app ID, then copy it to your clipboard:</span></span>

![Photon-Seite „Anwendung“ mit ausgewählter App-ID](images/mr-learning-sharing/sharing-02-section7-step1-1.png)

<span data-ttu-id="72451-173">Wählen Sie im Unity-Menü **Window** > **Photon Unity Networking** > **PUN Wizard** (Fenster > Photon Unity-Netzwerk > PUN-Assistent) aus, um das Fenster des Pun-Assistenten zu öffnen, klicken Sie auf die Schaltfläche **Setup Project** (Projekt einrichten), um das PUN-Setupmenü zu öffnen, und konfigurieren Sie es wie folgt:</span><span class="sxs-lookup"><span data-stu-id="72451-173">In the Unity menu, select **Window** > **Photon Unity Networking** > **PUN Wizard** to open the Pun Wizard window, click the **Setup Project** button to open the PUN Setup menu, and configure it as follows:</span></span>

* <span data-ttu-id="72451-174">Fügen Sie im Feld **AppId or Email** (AppID oder E-Mail) die PUN-App-ID ein, die Sie im vorherigen Schritt kopiert hatten</span><span class="sxs-lookup"><span data-stu-id="72451-174">In the **AppId or Email** field, paste the PUN app ID you copied in the previous step</span></span>

<span data-ttu-id="72451-175">Klicken Sie anschließend auf die Schaltfläche **Setup Project** (Projekt einrichten), um die AppID zu übernehmen:</span><span class="sxs-lookup"><span data-stu-id="72451-175">Then click the **Setup Project** button to apply the app ID:</span></span>

![Unity-Fenster zum Einrichten von PUN mit eingetragener AppID](images/mr-learning-sharing/sharing-02-section7-step1-2.png)

<span data-ttu-id="72451-177">Nachdem Unity den PUN-Setupvorgang abgeschlossen hat, wird im PUN-Setupmenü die Meldung **Done!** (Fertig!) angezeigt</span><span class="sxs-lookup"><span data-stu-id="72451-177">Once Unity has finished the PUN setup process, the PUN Setup menu will display the message **Done!**</span></span> <span data-ttu-id="72451-178">und automatisch im Projektfenster die Ressource **PhotonServerSettings** ausgewählt, sodass deren Eigenschaften im Inspektorfenster angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="72451-178">and automatically select the **PhotonServerSettings** asset in the Project window, so its properties are displayed in the Inspector window:</span></span>

![Unity-Fenster zum Einrichten von PUN mit angewendetem „Setup Project“](images/mr-learning-sharing/sharing-02-section7-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="72451-180">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="72451-180">Congratulations</span></span>

<span data-ttu-id="72451-181">Sie haben erfolgreich eine PUN-Anwendung erstellt und sie mit Ihrem Unity-Projekt verbunden.</span><span class="sxs-lookup"><span data-stu-id="72451-181">You have successfully created a PUN app and connected it to your Unity project.</span></span> <span data-ttu-id="72451-182">Der nächste Schritt besteht im Zulassen von Verbindungen mit anderen Benutzern, sodass sich mehrere Benutzer gegenseitig sehen können.</span><span class="sxs-lookup"><span data-stu-id="72451-182">Your next step is to allow connections with other users so that multiple users can see each other.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="72451-183">Nächstes Tutorial: 3. Verbinden mehrerer Benutzer</span><span class="sxs-lookup"><span data-stu-id="72451-183">Next Tutorial: 3. Connecting multiple users</span></span>](mr-learning-sharing-03.md)