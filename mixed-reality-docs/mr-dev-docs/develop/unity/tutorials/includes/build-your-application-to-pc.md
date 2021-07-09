---
ms.openlocfilehash: be4a3243bc00f29f992957de0dfa29416c13284d
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392613"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="750bc-101">Unity 2020 und OpenXR</span><span class="sxs-lookup"><span data-stu-id="750bc-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

### <a name="1-switching-build-platform"></a><span data-ttu-id="750bc-102">1. Wechseln der Buildplattform</span><span class="sxs-lookup"><span data-stu-id="750bc-102">1. Switching Build Platform</span></span>

<span data-ttu-id="750bc-103">Wählen Sie im Unity-Menü „File > Build Settings“ (Datei > Buildeinstellungen) aus, um das Fenster „Build Settings“ (Buildeinstellungen) zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="750bc-103">In the Unity menu, select File > Build Settings to open the Build Settings window.</span></span>

<span data-ttu-id="750bc-104">Wählen Sie im Fenster „Build Settings“ (Buildeinstellungen) die Plattform **PC, Mac & Linux Standalone** aus, und klicken Sie auf die Schaltfläche **Switch Platform** (Plattform wechseln), um die Buildplattform zu ändern:</span><span class="sxs-lookup"><span data-stu-id="750bc-104">In the Build Settings window, select **PC, Mac & Linux Standalone** Platform and click the **Switch Platform** button to change the Build Platform:</span></span>

![Wechseln der Buildplattform](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-1.PNG)

<span data-ttu-id="750bc-106">Wenn Unity den Plattformwechsel abgeschlossen hat, klicken Sie auf das x-Symbol, um das Fenster mit den Buildeinstellungen zu schließen.</span><span class="sxs-lookup"><span data-stu-id="750bc-106">When Unity has finished switching the platform, click the x icon to close the Build Settings window.</span></span>

### <a name="2-set-the-project-settings"></a><span data-ttu-id="750bc-107">2. Festlegen der Projekteinstellungen</span><span class="sxs-lookup"><span data-stu-id="750bc-107">2. Set the project settings</span></span>

<span data-ttu-id="750bc-108">Wählen Sie im Unity-Menü **Edit** > **Project Settings** > **XR Plug-In Management** aus, stellen Sie sicher, dass Sie sich auf der Registerkarte „Windows Standalone“ (Windows eigenständig) befinden, und aktivieren Sie das Kontrollkästchen **OpenXR** und **Windows Mixed Reality Feature set** (Windows Mixed Reality-Featuresatz).</span><span class="sxs-lookup"><span data-stu-id="750bc-108">In the Unity menu, select **Edit** > **Project Settings** > **XR Plug-in Management** ensure that you are in Windows Standalone tab and check the **OpenXR** and **Windows Mixed Reality feature set** checkbox.</span></span>

![Aktivieren von OpenXR und Windows Mixed Reality-Featuresatz](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-2.PNG)

<span data-ttu-id="750bc-110">Wählen Sie im Fenster „Project Settings“ (Projekteinstellungen) **OpenXR** aus, und stellen Sie sicher, dass Sie sich auf der Registerkarte „Windows Standalone“ (Windows eigenständig) befinden, und ändern Sie den **Depth sumission mode** (Tiefenübermittlungsmodus) von „None“ (Ohne) in **Depth 16 Bit** (16 Bit Tiefe).</span><span class="sxs-lookup"><span data-stu-id="750bc-110">In Project Settings window, select **OpenXR** and ensure that you are in Windows Standalone tab and change the **Depth submission mode** from None to **Depth 16 Bit**.</span></span>

<span data-ttu-id="750bc-111">Fügen Sie auf der Registerkarte „Interaction profiles“ (Interaktionsprofile) das **Eye Gaze Interaction Profile** („Anvisieren mit den Augen“-Interaktionsprofil) und das **Microsoft Hand Interaction Profile** (Microsoft-Handinteraktions-Profil) hinzu, indem Sie auf das Symbol „+“ klicken.</span><span class="sxs-lookup"><span data-stu-id="750bc-111">In interaction profiles tab add **Eye Gaze Interaction Profile** and **Microsoft Hand Interaction Profile** by clicking on the + symbol.</span></span>

![Hinzufügen des Interaktionsprofils „Anvisieren mit den Augen" und des Microsoft-Handinteraktionsprofils](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-3.PNG)

<span data-ttu-id="750bc-113">Aktivieren Sie unter **Open XR feature groups** > **All features** (XR-Featuregruppen öffnen > Alle Features) das Kontrollkästchen **Holographic App Remoting**.</span><span class="sxs-lookup"><span data-stu-id="750bc-113">Under **Open XR feature groups** > **All features** > check the **Holographic App Remoting** checkbox.</span></span>

![Aktivieren von Holographic App Remoting](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-4.PNG)

<span data-ttu-id="750bc-115">Aktivieren Sie als Nächstes das Kontrollkästchen **Windows Mixed Reality**, und aktivieren Sie unter der Gruppe „Windows Mixed Reality“ das Kontrollkästchen **Holographic App Remoting**.</span><span class="sxs-lookup"><span data-stu-id="750bc-115">next select the **Windows Mixed Reality**  check box and under Windows Mixed Reality group select the  **Holographic App Remoting** checkbox.</span></span>

![Aktivieren von Windows Mixed Reality Holographic App Remoting](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-5.PNG)

### <a name="3-build-the-unity-project"></a><span data-ttu-id="750bc-117">3. Erstellen des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="750bc-117">3. Build the Unity Project</span></span>

<span data-ttu-id="750bc-118">Wählen Sie im Unity-Menü „File > Build Settings“ (Datei > Buildeinstellungen) aus, um das Fenster „Build Settings“ (Buildeinstellungen) zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="750bc-118">In the Unity menu, select File > Build Settings to open the Build Settings window.</span></span>

<span data-ttu-id="750bc-119">Klicken Sie im Fenster „Build Settings“ (Buildeinstellungen) auf die Schaltfläche \***Add Open Scenes** _ (Geöffnete Szenen hinzufügen), um den Szenen die aktuelle Szene hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="750bc-119">In the Build Settings window, click the \***Add Open Scenes** _ button to add your current scene to the Scenes.</span></span> <span data-ttu-id="750bc-120">Klicken Sie in der Build-Liste dann auf die Schaltfläche _ \*Build\*\*:</span><span class="sxs-lookup"><span data-stu-id="750bc-120">In the Build list, then click the _ *Build*\* button:</span></span>

![Unity-Fenster „Build Settings“ mit hinzugefügter Szene](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-6.PNG)

<span data-ttu-id="750bc-122">Wählen Sie einen geeigneten Speicherort zum Speichern Ihres Builds aus, z. B. „Documents\MixedRealityLearning“.</span><span class="sxs-lookup"><span data-stu-id="750bc-122">choose a suitable location to store your build, for example, Documents\MixedRealityLearning.</span></span> <span data-ttu-id="750bc-123">Erstellen Sie einen neuen Ordner, und geben Sie ihm einen geeigneten Namen, z. B. „PCHolographicRemoting“.</span><span class="sxs-lookup"><span data-stu-id="750bc-123">Create a new folder and give it a suitable name, for example, PCHolographicRemoting.</span></span> <span data-ttu-id="750bc-124">Klicken Sie dann auf die Schaltfläche ***Select Folder*** (Ordner auswählen), um den Buildprozess zu starten:</span><span class="sxs-lookup"><span data-stu-id="750bc-124">Then click the ***Select Folder*** button to start the build process:</span></span>

![Unity-Fenster „Build Settings“ mit Aufforderungsfenster zum Auswählen eines Ordners](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-7.png)

<span data-ttu-id="750bc-126">Warten Sie, bis Unity den Buildvorgang abgeschlossen hat.</span><span class="sxs-lookup"><span data-stu-id="750bc-126">Wait for Unity to finish the build process.</span></span>

![Unity: Buildvorgang wird ausgeführt](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-8.png)

<span data-ttu-id="750bc-128">Doppelklicken Sie auf die ausführbare Datei, um die PC Holographic Remoting-Anwendung auf Ihrem PC zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="750bc-128">double click on the Executable file to open the PC Holographic Remoting Application in your PC.</span></span>

> [!NOTE]
> <span data-ttu-id="750bc-129">Aufgrund einiger bekannter Probleme in der als UWP erstellten Holographic Remoting für PC-App erstellen wir die PC-App als Windows Standalone für OpenXR.</span><span class="sxs-lookup"><span data-stu-id="750bc-129">Due to some known issues in Holographic Remoting for PC app Built as UWP we are Building the PC App as Windows Standalone for OpenXR.</span></span>


# <a name="legacy-wsa"></a>[<span data-ttu-id="750bc-130">Legacy-WSA</span><span class="sxs-lookup"><span data-stu-id="750bc-130">Legacy WSA</span></span>](#tab/wsa)

### <a name="1-set-the-player-settings"></a><span data-ttu-id="750bc-131">1. Festlegen der Playereinstellungen</span><span class="sxs-lookup"><span data-stu-id="750bc-131">1. Set the player settings</span></span>

<span data-ttu-id="750bc-132">Aktivieren Sie im Abschnitt **XR Settings** (XR-Einstellungen) das Kontrollkästchen **WSA Holographic Remoting Supported** (WSA Holographic Remoting unterstützt), und aktivieren Sie Holographic Remoting.</span><span class="sxs-lookup"><span data-stu-id="750bc-132">In the **XR Settings** section, select the **WSA Holographic Remoting Supported** checkbox and enable the Holographic Remoting.</span></span>

![Unity-Fenster XR-Einstellungen mit aktiviertem „WSA Holographic Remoting Supported“](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step1-1.png)

### <a name="2-build-the-unity-project"></a><span data-ttu-id="750bc-134">2. Erstellen des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="750bc-134">2. Build the Unity Project</span></span>

<span data-ttu-id="750bc-135">Wählen Sie im Unity-Menü „File > Build Settings“ (Datei > Buildeinstellungen) aus, um das Fenster „Build Settings“ (Buildeinstellungen) zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="750bc-135">In the Unity menu, select File > Build Settings to open the Build Settings window.</span></span>

<span data-ttu-id="750bc-136">Klicken Sie im Fenster „Build Settings“ (Buildeinstellungen) auf die Schaltfläche \***Add Open Scenes** _ (Geöffnete Szenen hinzufügen), um den Szenen die aktuelle Szene hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="750bc-136">In the Build Settings window, click the \***Add Open Scenes** _ button to add your current scene to the Scenes.</span></span> <span data-ttu-id="750bc-137">Klicken Sie in der Liste „Build“ auf die Schaltfläche _ \*_Build_\*\*, um das Fenster „Build Universal Windows Platform“ (Universelle Windows-Plattform erstellen) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="750bc-137">In the Build list, then click the _ *_Build button_*\* to open the Build Universal Windows Platform window:</span></span>

![Unity-Fenster „Build Settings“ mit hinzugefügter Szene](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-1.png)

<span data-ttu-id="750bc-139">Wählen Sie im Fenster „Build Universal Windows Platform“ einen passenden Speicherort zum Speichern Ihres Builds aus, z. B. „Documents\MixedRealityLearning“.</span><span class="sxs-lookup"><span data-stu-id="750bc-139">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, Documents\MixedRealityLearning.</span></span> <span data-ttu-id="750bc-140">Erstellen Sie einen neuen Ordner, und geben Sie ihm einen geeigneten Namen, z. B. „PCHolographicRemoting“.</span><span class="sxs-lookup"><span data-stu-id="750bc-140">Create a new folder and give it a suitable name, for example, PCHolographicRemoting.</span></span> <span data-ttu-id="750bc-141">Klicken Sie dann auf die Schaltfläche ***Select Folder*** (Ordner auswählen), um den Buildprozess zu starten:</span><span class="sxs-lookup"><span data-stu-id="750bc-141">Then click the ***Select Folder*** button to start the build process:</span></span>

![Unity-Fenster „Build Settings“ mit Aufforderungsfenster zum Auswählen eines Ordners](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-2.png)

<span data-ttu-id="750bc-143">Warten Sie, bis Unity den Buildvorgang abgeschlossen hat.</span><span class="sxs-lookup"><span data-stu-id="750bc-143">Wait for Unity to finish the build process.</span></span>

![Unity: Buildvorgang wird ausgeführt](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-3.png)

### <a name="3-build-and-deploy-the-application"></a><span data-ttu-id="750bc-145">3. Erstellen und Bereitstellen der Anwendung</span><span class="sxs-lookup"><span data-stu-id="750bc-145">3. Build and deploy the application</span></span>

<span data-ttu-id="750bc-146">Wenn der Buildvorgang abgeschlossen ist, fordert Unity den Windows Datei-Explorer auf, den Speicherort zu öffnen, in dem Sie den Build gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="750bc-146">When the build process is completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="750bc-147">Navigieren Sie im Ordner, und doppelklicken Sie auf die SLN-Datei, um sie in Visual Studio zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="750bc-147">Navigate inside the folder, and double-click the .sln file to open it in Visual Studio:</span></span>

![Windows-Explorer mit neu erstellter, ausgewählter Visual Studio-Projektmappe](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-1.png)

> [!NOTE]
> <span data-ttu-id="750bc-149">Wenn Sie von Visual Studio zur Installation neuer Komponenten aufgefordert werden, nehmen Sie sich einen Moment Zeit, um zu überprüfen, ob alle erforderlichen Komponenten (wie in der Dokumentation „Installieren der Tools“ angegeben) installiert sind.</span><span class="sxs-lookup"><span data-stu-id="750bc-149">If Visual Studio asks you to install new components, take a moment to ensure that all prerequisite components are installed as specified in the Install the Tools documentation.</span></span>

<span data-ttu-id="750bc-150">Konfigurieren Sie Visual Studio für den PC, indem Sie die Releasekonfiguration, die x64-Architektur und einen lokalen Computer als Ziel auswählen:</span><span class="sxs-lookup"><span data-stu-id="750bc-150">Configure Visual Studio for PC by selecting the Release configuration, the x64 architecture, and Local Machine as target:</span></span>

![Visual Studio, konfiguriert für den lokalen Computer](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-2.png)

<span data-ttu-id="750bc-152">Klicken Sie auf die Schaltfläche ***Lokaler Computer***.</span><span class="sxs-lookup"><span data-stu-id="750bc-152">Click the button that says ***Local Machine***.</span></span> <span data-ttu-id="750bc-153">Die Anwendung wird auf Ihrem PC erstellt und bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="750bc-153">It starts to build and deploy the application on to your PC.</span></span> <span data-ttu-id="750bc-154">Die Anwendung wird standardmäßig auf Ihrem PC installiert.</span><span class="sxs-lookup"><span data-stu-id="750bc-154">The application will be installed in your PC by default.</span></span>
