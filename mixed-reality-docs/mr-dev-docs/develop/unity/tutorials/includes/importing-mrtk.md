---
ms.openlocfilehash: 2420e68a0753739111fc2c5eecfbd1da563f52c2
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175991"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="53b8c-101">Unity 2020 und OpenXR</span><span class="sxs-lookup"><span data-stu-id="53b8c-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="53b8c-102">Klicken Sie nach dem Öffnen von **MixedRealityFeatureTool** auf **Start**, um mit dem Mixed Reality-Featuretool loszulegen.</span><span class="sxs-lookup"><span data-stu-id="53b8c-102">Once **MixedRealityFeatureTool** is opened, click on **Start** to get started with Mixed Reality Feature Tool.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

<span data-ttu-id="53b8c-103">Der erste Schritt besteht im Verweisen des Mixed Reality-Featuretools auf Ihren **Projektpfad** mithilfe der Schaltfläche mit den **Auslassungspunkten**. Klicken Sie auf die Schaltfläche mit den drei Auslassungspunkten neben dem Projektpfad, und navigieren Sie im Explorer zu Ihrem Projektordner, z. B. _D:\MixedRealityLearning\MRTK Tutorials_.</span><span class="sxs-lookup"><span data-stu-id="53b8c-103">The first step is to point the Mixed Reality Feature Tool to your **Project path** using the **ellipsis** button, click on the Three dots ellipsis button next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">

<span data-ttu-id="53b8c-104">Wenn Sie den Ordner Ihres Projekts gefunden haben, klicken Sie auf die Schaltfläche „Öffnen“, um zum Mixed Reality-Featuretool zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="53b8c-104">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span> <span data-ttu-id="53b8c-105">Klicken Sie dann auf **Discover Features** (Features ermitteln).</span><span class="sxs-lookup"><span data-stu-id="53b8c-105">Then click on **Discover Features**.</span></span>

> [!NOTE]
> <span data-ttu-id="53b8c-106">Das Dialogfeld, das angezeigt wird, wenn Sie das Dateisystem nach dem Unity-Projektordner durchsuchen, enthält '_' als den Dateinamen.</span><span class="sxs-lookup"><span data-stu-id="53b8c-106">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="53b8c-107">Es muss ein Wert für den Dateinamen vorhanden sein, um die Auswahl des Ordners zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="53b8c-107">There must be a value for the file name to enable the folder to be selected.</span></span>

> [!Important]
> <span data-ttu-id="53b8c-108">Das Mixed Reality-Featuretool führt eine Überprüfung durch, um sicherzustellen, dass die Weiterleitung an einen Unity-Projektordner erfolgt.</span><span class="sxs-lookup"><span data-stu-id="53b8c-108">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="53b8c-109">Der Ordner muss die Ordner „Assets“, „Packages“ und „Project Settings“ enthalten.</span><span class="sxs-lookup"><span data-stu-id="53b8c-109">The folder must contain Assets, Packages and Project Settings folders.</span></span>

<span data-ttu-id="53b8c-110">Die Features sind nach Kategorie gruppiert, um die Suche zu erleichtern. Klicken Sie auf die Dropdownliste **Mixed Reality Toolkit**, um Pakete im Zusammenhang mit dem Mixed Reality Toolkit zu finden, und klicken Sie auf die Dropdownliste **Plattformunterstützung**, um Pakete für verschiedene unterstützende Plattformen zu finden.</span><span class="sxs-lookup"><span data-stu-id="53b8c-110">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit and click on **Platform Support** dropdown to find packages relating various supporting platforms.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-4-openxr.png" width="650px" alt="MixedRealityFeatureTool Discover Features">

<span data-ttu-id="53b8c-111">Überprüfen Sie **die Mixed Reality Toolkit Foundation**, und klicken Sie auf die Dropdownliste daneben, um **MRTK 2.7.2** auszuwählen. Überprüfen Sie auch das **Mixed Reality OpenXR-Plug-In 1.0.0,** , und klicken Sie auf die Dropdownliste daneben, um die neueste verfügbare Version auszuwählen. Klicken Sie dann auf die Schaltfläche **Get features** (Features abrufen), um die ausgewählten Pakete herunterzuladen.</span><span class="sxs-lookup"><span data-stu-id="53b8c-111">Check the **Mixed Reality Toolkit Foundation** and click on the dropdown next to it to select **MRTK 2.7.2**, also check the **Mixed Reality OpenXR Plugin 1.0.0** and click on the dropdown next to it to select most recent version available, then click on **Get features** button to download the selected packages.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-5-openxr.png" width="650px" alt="MixedRealityFeatureTool Open MixedReality">

<span data-ttu-id="53b8c-112">Klicken Sie dann auf die Schaltfläche **Validate** (Überprüfen), um das ausgewählte Paket zu überprüfen, Es wird ein Popupfenster mit der Nachricht **No validation issues were detected** (Bei der Überprüfung wurden keine Probleme erkannt) angezeigt. Klicken Sie auf **OK**, um das Popup zu schließen, und klicken Sie auf die Schaltfläche **Import** (Importieren).</span><span class="sxs-lookup"><span data-stu-id="53b8c-112">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-6-openxr.png" width="650px" alt="MixedRealityFeatureTool Select required package">


<span data-ttu-id="53b8c-113">Klicken Sie auf die Schalftläche **Approve** (Genehmigen), um dem Projekt das **Mixed Reality-Toolkit** hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="53b8c-113">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-7-openxr.png" width="650px" alt="MixedRealityFeatureTool Validate package">

## <a name="configuring-the-unity-project"></a><span data-ttu-id="53b8c-114">Konfigurieren des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="53b8c-114">Configuring the Unity project</span></span>

<span data-ttu-id="53b8c-115">Nachdem Unity den Import des Pakets aus dem vorherigen Abschnitt abgeschlossen hat, wird eine Warnmeldung angezeigt, um den Unity-Editor neu zu starten, um Back-Ends für das neue Plug-In-System zu aktivieren. Klicken Sie auf **Ja**.</span><span class="sxs-lookup"><span data-stu-id="53b8c-115">After Unity has finished importing the package from the previous section, a warning message appears to restart the unity editor to enable to backends for new plugin system, click on **Yes**</span></span>

<img src="../images/mr-learning-base/base-02-section5-step1-1-openxr.png" width="650px" alt="Unity Restart Option">

<span data-ttu-id="53b8c-116">Sobald Unity neu startet, sollte das Fenster „MRTK Project Configurator“ (MRTK-Projektkonfigurator) angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="53b8c-116">Once the Unity restarts MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="53b8c-117">Wenn das nicht der Fall ist, öffnen Sie es, indem Sie zu **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK** (Mixed Reality > Toolkit > Hilfsprogramme > Projekt für MRTK konfigurieren) wechseln:</span><span class="sxs-lookup"><span data-stu-id="53b8c-117">If it doesn't, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**:</span></span>

![Öffnen des Fensters „MRTK Project Configurator“](../images/mr-learning-base/base-02-section5-step1-2-openxr.png)

<span data-ttu-id="53b8c-119">Klicken Sie auf **Unity OpenXR-Plug-In**, um die XR-Plug-In-Verwaltung zu aktivieren und ihrem Projekt die erforderlichen Pakete hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="53b8c-119">Click on **Unity OpenXR Plugin** to Enable XR Plugin Management and add its required packages into your project.</span></span>

![<span data-ttu-id="53b8c-120">Hinzufügen des Unity OpenXR-Plug-Ins (Add Unity OpenXR Plugin)</span><span class="sxs-lookup"><span data-stu-id="53b8c-120">Add Unity OpenXR Plugin</span></span> ](../images/mr-learning-base/base-02-section5-step1-3-openxr.png)

<span data-ttu-id="53b8c-121">Dadurch werden die erforderlichen Unity-Pakete für die XR-Plug-In-Verwaltung importiert. Sobald Sie fertig sind, klicken Sie im MRTK-Projektkonfigurator auf **Show XR Plug-In Management Settings** (XR-Plug-In-Verwaltungseinstellungen anzeigen).</span><span class="sxs-lookup"><span data-stu-id="53b8c-121">This will import required unity packages for XR Plugin Management, once done click on **Show XR Plug-In Management Settings** in MRTK project Configurator.</span></span>

![<span data-ttu-id="53b8c-122">Anzeigen der XR-Plug-In-Verwaltungseinstellungen (Show XR Plug-In Management Settings)</span><span class="sxs-lookup"><span data-stu-id="53b8c-122">Show XR Plug-In Management Settings</span></span> ](../images/mr-learning-base/base-02-section5-step1-4-openxr.png)

<span data-ttu-id="53b8c-123">Dadurch wird das Fenster **Project Settings** (Projekteinstellungen) geöffnet.</span><span class="sxs-lookup"><span data-stu-id="53b8c-123">This opens **Project Settings window**.</span></span> <span data-ttu-id="53b8c-124">Stellen Sie im Fenster mit den Projekteinstellungen unter **XR Plug-In Management** (XR-Plug-In-Verwaltung) sicher, dass Sie sich in den Einstellungen der universellen Windows Plattform befinden (Registerkarte mit dem Windows-Logo).</span><span class="sxs-lookup"><span data-stu-id="53b8c-124">In the Project Settings window under **XR Plug-in Management** Ensure that you are in Universal Windows Platform settings (Windows logo tab).</span></span> <span data-ttu-id="53b8c-125">Stellen Sie außerdem sicher, dass **Initialize XR on Startup** (XR beim Start initialisieren) aktiviert ist, klicken Sie dann auf die Kontrollkästchen **OpenXR** und **Microsoft HoloLens feature set** (Microsoft HoloLens-Featuresatz), um sie zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="53b8c-125">Also Ensure **Initialize XR on Startup** is checked, then click **OpenXR** checkbox and **Microsoft HoloLens feature set** checkbox to enable them.</span></span>

![Aktivieren von Open XR (Enable Open XR)](../images/mr-learning-base/base-02-section5-step1-5-openxr.png)

<span data-ttu-id="53b8c-127">Sobald Sie das Kontrollkästchen „OpenXR“ aktiviert haben, wird im „MRTK Project Configurator“-Fenster die aktualisierte Meldung mit der Schaltfläche **Apply Settings** (Einstellungen anwenden) angezeigt.</span><span class="sxs-lookup"><span data-stu-id="53b8c-127">Once you check OpenXR checkbox, MRTK Project Configurator window will show updated message with **Apply Settings** button.</span></span> <span data-ttu-id="53b8c-128">Klicken Sie auf die Schaltfläche **Apply Settings** (Einstellungen anwenden).</span><span class="sxs-lookup"><span data-stu-id="53b8c-128">Click **Apply Settings** button.</span></span> 

![Fenster 1 mit Projekteinstellungen](../images/mr-learning-base/base-02-section5-step1-6-openxr.png)

<span data-ttu-id="53b8c-130">Wenn Sie auf „Apply Settings“ (Einstellungen anwenden) klicken, wird diese Fehlermeldung möglicherweise in der Konsole angezeigt.</span><span class="sxs-lookup"><span data-stu-id="53b8c-130">When you click Apply Settings, you might see this error message in the Console.</span></span> <span data-ttu-id="53b8c-131">Sie können fortfahren, wenn dies der einzige Fehler oder gar kein Fehler vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="53b8c-131">You can proceed if this is the only error or there is no error.</span></span>

![OpenXR-Remoting-Fehlermeldung](../images/mr-learning-base/base-02-section5-step1-6-openxr-Error.png)

<span data-ttu-id="53b8c-133">Klicken Sie zum Überprüfen der OpenXR-Konfiguration unter **XR Plug-in Management** (XR-Plug-In-Verwaltung) auf **OpenXR**, und überprüfen Sie die folgenden Elemente:</span><span class="sxs-lookup"><span data-stu-id="53b8c-133">To validate OpenXR configuration, click **OpenXR** under **XR Plug-in Management** and check these items:</span></span>
* <span data-ttu-id="53b8c-134">Tiefenübermittlungsmodus: **Tiefe 16 Bit**</span><span class="sxs-lookup"><span data-stu-id="53b8c-134">Depth Submission Mode: **Depth 16 Bit**</span></span>
* <span data-ttu-id="53b8c-135">Interaktionsprofile: **Microsoft-Handinteraktionsprofil**</span><span class="sxs-lookup"><span data-stu-id="53b8c-135">Interaction Profiles: **Microsoft Hand Interaction Profile**</span></span>

![Fenster 2 mit Projekteinstellungen](../images/mr-learning-base/base-02-section5-step1-7-openxr.png)

> [!TIP]
> <span data-ttu-id="53b8c-137">Das Verringern des Tiefenformats auf 16 Bit ist optional, kann aber bei der Verbesserung der Grafikleistung in Ihrem Projekt helfen.</span><span class="sxs-lookup"><span data-stu-id="53b8c-137">Reducing the Depth Format to 16-bit is optional but may help improve graphics performance in your project.</span></span> <span data-ttu-id="53b8c-138">Weitere Informationen zu diesem Thema finden Sie im Abschnitt <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Tiefenpufferfreigabe (HoloLens)</a> der Leistungsdokumentation zum MRTK.</span><span class="sxs-lookup"><span data-stu-id="53b8c-138">To learn more about this topic, you can refer to the <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> section of MRTK's Performance documentation.</span></span>


<span data-ttu-id="53b8c-139">Klicken Sie im Fenster **MRTK Project Configurator** auf **Weiter**, und klicken Sie dann auf die Schaltfläche **Anwenden**, um die Einstellungen anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="53b8c-139">In the **MRTK Project Configurator** window, click on **Next**, then click the **Apply** button to apply the settings.</span></span> <span data-ttu-id="53b8c-140">(Wenn Sie das Fenster geschlossen hatten, können Sie es manuell öffnen, indem Sie zu **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK** (Mixed Reality > Toolkit > Hilfsprogramme > Projekt für MRTK konfigurieren) wechseln.)</span><span class="sxs-lookup"><span data-stu-id="53b8c-140">(If you closed it, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**)</span></span>

![Fenster 3 mit Projekteinstellungen](../images/mr-learning-base/base-02-section5-step1-8-openxr.png)

![Fenster 4 mit Projekteinstellungen](../images/mr-learning-base/base-02-section5-step1-9-openxr.png)

<span data-ttu-id="53b8c-143">Nachdem Sie auf „Anwenden“ geklickt haben, versucht Unity einen Neustart, damit das Eingabesystem wirksam wird. Klicken Sie auf **Anwenden**, um den Unity-Editor neu zu starten.</span><span class="sxs-lookup"><span data-stu-id="53b8c-143">Once you click on Apply, Unity will try to restart for the input system to take into effect, click on **Apply** to restart the Unity editor</span></span>

### <a name="configure-additional-project-settings"></a><span data-ttu-id="53b8c-144">Konfigurieren zusätzlicher Projekteinstellungen</span><span class="sxs-lookup"><span data-stu-id="53b8c-144">Configure additional project settings</span></span>

<span data-ttu-id="53b8c-145">Wählen Sie im Unity-Menü **Bearbeiten** > **Projekteinstellungen...** aus, um das Fenster Projekteinstellungen zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="53b8c-145">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window.</span></span>

<span data-ttu-id="53b8c-146">Wählen Sie im Fenster „Project Settings“ (Projekteinstellungen) **Player** > **Publishing Settings** (Player > Veröffentlichungseinstellungen) aus, geben Sie dann im Feld **Package name** (Paketname) einen passenden Namen ein, beispielsweise _MRTKTutorials-GettingStarted_:</span><span class="sxs-lookup"><span data-stu-id="53b8c-146">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Veröffentlichungseinstellungen in Unity.](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> <span data-ttu-id="53b8c-149">Der Paketname stellt den eindeutigen Bezeichner für die App dar.</span><span class="sxs-lookup"><span data-stu-id="53b8c-149">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="53b8c-150">Sie sollten diesen Bezeichner ändern, bevor Sie die App bereitstellen, um das Überschreiben zuvor installierter Apps zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="53b8c-150">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="53b8c-151">Der „Product Name“ (Produktname) ist der Name, der im HoloLens-Startmenü angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="53b8c-151">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="53b8c-152">Um das Auffinden der App während der Entwicklung zu erleichtern, fügen Sie vor dem Namen einen Unterstrich hinzu, sodass sie in Listen oben einsortiert wird.</span><span class="sxs-lookup"><span data-stu-id="53b8c-152">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="53b8c-153">Unity 2019/2020 und Windows-XR-Plugin</span><span class="sxs-lookup"><span data-stu-id="53b8c-153">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="53b8c-154">Klicken Sie nach dem Öffnen von **MixedRealityFeatureTool** auf **Start**, um mit dem Mixed Reality-Featuretool loszulegen.</span><span class="sxs-lookup"><span data-stu-id="53b8c-154">Once **MixedRealityFeatureTool** is opened, click on **Start** to get started with Mixed Reality Feature Tool.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

<span data-ttu-id="53b8c-155">Der erste Schritt besteht im Verweisen des Mixed Reality-Featuretools auf Ihren **Projektpfad** mithilfe der Schaltfläche mit den **Auslassungspunkten**. Klicken Sie auf die Schaltfläche mit den drei Auslassungspunkten neben dem Projektpfad, und navigieren Sie im Explorer zu Ihrem Projektordner, z. B. _D:\MixedRealityLearning\MRTK Tutorials_.</span><span class="sxs-lookup"><span data-stu-id="53b8c-155">The first step is to point the Mixed Reality Feature Tool to your **Project path** using the **ellipsis** button, click on the Three dots ellipsis button next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">


<span data-ttu-id="53b8c-156">Wenn Sie den Ordner Ihres Projekts gefunden haben, klicken Sie auf die Schaltfläche „Öffnen“, um zum Mixed Reality-Featuretool zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="53b8c-156">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span> <span data-ttu-id="53b8c-157">Klicken Sie dann auf **Discover Features** (Features ermitteln).</span><span class="sxs-lookup"><span data-stu-id="53b8c-157">Then click on **Discover Features**.</span></span>

> [!NOTE]
> <span data-ttu-id="53b8c-158">Das Dialogfeld, das angezeigt wird, wenn Sie das Dateisystem nach dem Unity-Projektordner durchsuchen, enthält '_' als den Dateinamen.</span><span class="sxs-lookup"><span data-stu-id="53b8c-158">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="53b8c-159">Es muss ein Wert für den Dateinamen vorhanden sein, um die Auswahl des Ordners zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="53b8c-159">There must be a value for the file name to enable the folder to be selected.</span></span>

> [!Important]
> <span data-ttu-id="53b8c-160">Das Mixed Reality-Featuretool führt eine Überprüfung durch, um sicherzustellen, dass die Weiterleitung an einen Unity-Projektordner erfolgt.</span><span class="sxs-lookup"><span data-stu-id="53b8c-160">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="53b8c-161">Der Ordner muss die Ordner „Assets“, „Packages“ und „Project Settings“ enthalten.</span><span class="sxs-lookup"><span data-stu-id="53b8c-161">The folder must contain Assets, Packages and Project Settings folders.</span></span>

<span data-ttu-id="53b8c-162">Die Features sind nach Kategorie gruppiert, damit sie leichter zu finden sind. Klicken Sie auf das Dropdownmenü **Mixed Reality-Toolkit**, um Pakete im Zusammenhang mit dem Mixed Reality-Toolkit zu finden.</span><span class="sxs-lookup"><span data-stu-id="53b8c-162">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-4.PNG" width="650px" alt="MixedRealityFeatureTool Discover Features">

<span data-ttu-id="53b8c-163">Aktivieren Sie das Kontrollkästchen **Mixed Reality Toolkit Foundation**, und klicken Sie auf die Dropdownliste daneben, um **MRTK 2.7.0** auszuwählen. Klicken Sie dann auf die Schaltfläche **Get Features** (Features abrufen), um die ausgewählten Pakete herunterzuladen.</span><span class="sxs-lookup"><span data-stu-id="53b8c-163">Check the box for **Mixed Reality Toolkit Foundation**, and click on the dropdown next to it to select **MRTK 2.7.0**, then click on **Get features** button to download the selected packages.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-5.PNG" width="650px" alt="MixedRealityFeatureTool Open Mixed Reality">

<span data-ttu-id="53b8c-164">Klicken Sie dann auf die Schaltfläche **Validate** (Überprüfen), um das ausgewählte Paket zu überprüfen, Es wird ein Popupfenster mit der Nachricht **No validation issues were detected** (Bei der Überprüfung wurden keine Probleme erkannt) angezeigt. Klicken Sie auf **OK**, um das Popup zu schließen, und klicken Sie auf die Schaltfläche **Import** (Importieren).</span><span class="sxs-lookup"><span data-stu-id="53b8c-164">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-6.PNG" width="650px" alt="MixedRealityFeatureTool Select required package">


<span data-ttu-id="53b8c-165">Klicken Sie auf die Schalftläche **Approve** (Genehmigen), um dem Projekt das **Mixed Reality-Toolkit** hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="53b8c-165">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-7.PNG" width="650px" alt="MixedRealityFeatureTool Validate package">


## <a name="configuring-the-unity-project"></a><span data-ttu-id="53b8c-166">Konfigurieren des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="53b8c-166">Configuring the Unity project</span></span>

<span data-ttu-id="53b8c-167">Nachdem Unity das Importieren des Pakets aus dem vorherigen Abschnitt abgeschlossen hat, sollte das Fenster des MRTK-Projektkonfigurators angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="53b8c-167">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="53b8c-168">Wenn das nicht der Fall ist, öffnen Sie es, indem Sie zu **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK** (Mixed Reality > Toolkit > Hilfsprogramme > Projekt für MRTK konfigurieren) wechseln:</span><span class="sxs-lookup"><span data-stu-id="53b8c-168">If it doesn't, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**:</span></span>

![Öffnen des MRTK-Konfiguratortools](../images/mr-learning-base/base-02-section5-step1-1xrsdk.PNG)

<span data-ttu-id="53b8c-170">Klicken Sie auf **Built-in Unity Plugin (non-OpenXR)** (Integriertes Unity-Plug-In (nicht OpenXR)), um die XR-Plug-In-Verwaltung zu aktivieren und ihrem Projekt die erforderlichen Pakete hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="53b8c-170">Click on **Built-in Unity Plugin(non-OpenXR)** to Enable XR Plugin Management and add its required packages into your project.</span></span>

![ <span data-ttu-id="53b8c-171">MRTK-Konfiguratortool</span><span class="sxs-lookup"><span data-stu-id="53b8c-171">MRTK configurator tool</span></span>](../images/mr-learning-base/base-02-section5-step1-2xrsdk.PNG)

> [!NOTE]
> <span data-ttu-id="53b8c-172">Der obige Screenshot stammt aus Unity 2020. Wenn Sie Unity 2019 verwenden, wählen Sie **XR SDK/XR Management** aus.</span><span class="sxs-lookup"><span data-stu-id="53b8c-172">The above screenshot is from Unity 2020, if you using Unity 2019 please select **XR SDK/XR Management**</span></span>

<span data-ttu-id="53b8c-173">Dadurch werden die erforderlichen Unity-Pakete für die XR-Plug-In-Verwaltung importiert. Sobald Sie fertig sind, klicken Sie im MRTK-Projektkonfigurator auf **Show Settings** (Einstellungen anzeigen).</span><span class="sxs-lookup"><span data-stu-id="53b8c-173">This will import required unity packages for XR Plugin Management, once done click on **Show Settings** in MRTK project Configurator.</span></span>

![Fenster mit Player-Einstellungen](../images/mr-learning-base/base-02-section5-step1-3xrsdk.PNG)

<span data-ttu-id="53b8c-175">Hierdurch wird das Fenster **Project Settings** (Projekteinstellungen) geöffnet. Stellen Sie im Fenster „Project Settings“ unter **XR Plug-In Management** sicher, dass Sie sich in den Einstellungen der universellen Windows-Plattform befinden. Stellen Sie außerdem sicher, dass **Initialize XR on Startup** (XR beim Start initialisieren) aktiviert ist, und aktivieren Sie das Kontrollkästchen **Windows Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="53b8c-175">This opens **Project Settings window**, In the Project Settings window under **XR Plug-in Management** Ensure that you are in Universal Windows Platform settings also Ensure **Initialize XR on Startup** is checked, and check **Windows Mixed Reality** checkbox.</span></span>

![Fenster mit Player-Einstellungen, „Mixed Reality-xrsdk“ aktivieren](../images/mr-learning-base/base-02-section5-step1-4xrsdk.PNG)

<span data-ttu-id="53b8c-177">Nachdem Unity das Importieren des Windows Mixed Reality SDK abgeschlossen hat, sollte wieder das Fenster des MRTK-Projektkonfigurators angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="53b8c-177">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="53b8c-178">Wenn dies nicht der Fall ist, verwenden Sie das Unity-Menü, um es zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="53b8c-178">If it doesn't, use the Unity menu to open it.</span></span>

<span data-ttu-id="53b8c-179">Klicken Sie im Fenster des MRTK-Projektkonfigurators auf **Weiter**, und verwenden Sie dann die Dropdownliste „Audio spatializer“ (Räumliche Audiowiedergabe), um den **MS HRTF Spatializer** auszuwählen, und klicken Sie dann auf die Schaltfläche **Übernehmen**, um die Einstellung zu übernehmen:</span><span class="sxs-lookup"><span data-stu-id="53b8c-179">In the MRTK Project Configurator window, click on **next** then use the Audio spatializer dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![MRTK-Projektkonfigurator-xrsdk](../images/mr-learning-base/base-02-section5-step1-5xrsdk.PNG)

> [!TIP]
> <span data-ttu-id="53b8c-181">Die Anwendung der MRTK-Standardeinstellungen ist optional, wird aber dringend empfohlen, weil es bei der Konfiguration einiger empfohlener Unity-Einstellungen hilfreich ist:</span><span class="sxs-lookup"><span data-stu-id="53b8c-181">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>

> * <span data-ttu-id="53b8c-182">Legen Sie den Single Pass-instanziierten Renderingpfad fest: Verbessert die Grafikleistung, indem die Renderpipeline für beide Augen im selben Zeichnen-Aufruf ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="53b8c-182">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="53b8c-183">Weitere Informationen zu diesem Thema finden Sie im Abschnitt [Single Pass-instanziiertes Rendering](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) der [Leistung](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering)sdokumentation von MRTK.</span><span class="sxs-lookup"><span data-stu-id="53b8c-183">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) section of MRTK's [Performance](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) documentation.</span></span>
> * <span data-ttu-id="53b8c-184">Standardebene für Spatial Awareness (räumliche Wahrnehmung) festlegen: Erstellt eine Unity-Ebene namens „Spatial Awareness“ und konfiguriert MRTK für die Verwendung dieser Ebene für das Gittermodell für räumliche Wahrnehmung.</span><span class="sxs-lookup"><span data-stu-id="53b8c-184">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="53b8c-185">Weitere Informationen zu Unity-Ebenen finden Sie in der Unity-Dokumentation zum <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Anpassen Ihres Arbeitsbereichs</a>.</span><span class="sxs-lookup"><span data-stu-id="53b8c-185">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

> [!TIP]
> <span data-ttu-id="53b8c-186">Das Festlegen der „Audio Spatializer“-Eigenschaft ist optional, kann aber die Audioerfahrung in Ihrem Projekt verbessern.</span><span class="sxs-lookup"><span data-stu-id="53b8c-186">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="53b8c-187">Wenn Sie sie auf „MS HRTF Spatializer“ festlegen, wird dieses Spatializer-Plug-In verwendet, wenn die Eigenschaft „AudioSource.spatialize“ von Unity aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="53b8c-187">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="53b8c-188">Weitere Informationen zu diesem Thema finden Sie in den <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">Tutorials zur räumlichen Audiowiedergabe</a>.</span><span class="sxs-lookup"><span data-stu-id="53b8c-188">To learn more about this topic, you can refer to the  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="53b8c-189">Klicken Sie auf **Weiter** und dann im Fenster des MRTK-Projektkonfigurators auf **Fertig**, um die Unity-Projektkonfiguration für XRSDK fertig zu stellen.</span><span class="sxs-lookup"><span data-stu-id="53b8c-189">Click on **Next** then click on **Done** in the MRTK Project Configurator window to finish the Unity project configuration for XRSDK.</span></span>

### <a name="configure-additional-project-settings"></a><span data-ttu-id="53b8c-190">Konfigurieren zusätzlicher Projekteinstellungen</span><span class="sxs-lookup"><span data-stu-id="53b8c-190">Configure additional project settings</span></span>

<span data-ttu-id="53b8c-191">Wählen Sie im Unity-Menü **Edit** > **Project Settings...** (Bearbeiten > Projekteinstellungen...) aus, um das Fenster „Project Settings“ (Projekteinstellungen) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="53b8c-191">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

<span data-ttu-id="53b8c-192">Wählen Sie im Fenster „Projekteinstellungen“ **XR-Plug-In-Verwaltung** > **Windows Mixed Reality** > **Laufzeiteinstellungen** aus, und verwenden Sie dann die Dropdownliste **Tiefenpufferformat**, um **16-Bit Tiefe** auszuwählen:</span><span class="sxs-lookup"><span data-stu-id="53b8c-192">In the Project Settings window, select **XR Plug-in Management** > **Windows Mixed Reality** > **Runtime Settings**, then use the **Depth Buffer Format** dropdown to select **16-bit depth**:</span></span>

![Unity: Tiefe 16 aktivieren](../images/mr-learning-base/base-02-section5-step2-1xrsdk.PNG)

> [!TIP]
> <span data-ttu-id="53b8c-194">Das Verringern des Tiefenformats auf 16 Bit ist optional, kann aber bei der Verbesserung der Grafikleistung in Ihrem Projekt helfen.</span><span class="sxs-lookup"><span data-stu-id="53b8c-194">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="53b8c-195">Weitere Informationen zu diesem Thema finden Sie im Abschnitt <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Tiefenpufferfreigabe (HoloLens)</a> der Leistungsdokumentation zum MRTK.</span><span class="sxs-lookup"><span data-stu-id="53b8c-195">To learn more about this topic, you can refer to the <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> section of MRTK's Performance documentation.</span></span>

<span data-ttu-id="53b8c-196">Wählen Sie im Fenster „Project Settings“ (Projekteinstellungen) **Player** > **Publishing Settings** (Player > Veröffentlichungseinstellungen) aus, geben Sie dann im Feld **Package name** (Paketname) einen passenden Namen ein, beispielsweise _MRTKTutorials-GettingStarted_:</span><span class="sxs-lookup"><span data-stu-id="53b8c-196">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Veröffentlichungseinstellungen in Unity.](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> <span data-ttu-id="53b8c-199">Der Paketname stellt den eindeutigen Bezeichner für die App dar.</span><span class="sxs-lookup"><span data-stu-id="53b8c-199">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="53b8c-200">Sie sollten diesen Bezeichner ändern, bevor Sie die App bereitstellen, um das Überschreiben zuvor installierter Apps zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="53b8c-200">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="53b8c-201">Der „Product Name“ (Produktname) ist der Name, der im HoloLens-Startmenü angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="53b8c-201">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="53b8c-202">Um das Auffinden der App während der Entwicklung zu erleichtern, fügen Sie vor dem Namen einen Unterstrich hinzu, sodass sie in Listen oben einsortiert wird.</span><span class="sxs-lookup"><span data-stu-id="53b8c-202">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="53b8c-203">Legacy-WSA</span><span class="sxs-lookup"><span data-stu-id="53b8c-203">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="53b8c-204">Klicken Sie nach dem Öffnen von **MixedRealityFeatureTool** auf **Start**, um mit dem Mixed Reality-Featuretool loszulegen.</span><span class="sxs-lookup"><span data-stu-id="53b8c-204">Once **MixedRealityFeatureTool** is opened, click on **Start** to get started with Mixed Reality Feature Tool.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

<span data-ttu-id="53b8c-205">Der erste Schritt besteht im Verweisen des Mixed Reality-Featuretools auf Ihren **Projektpfad** mithilfe der Schaltfläche mit den **Auslassungspunkten**. Klicken Sie auf die Schaltfläche mit den drei Auslassungspunkten neben dem Projektpfad, und navigieren Sie im Explorer zu Ihrem Projektordner, z. B. _D:\MixedRealityLearning\MRTK Tutorials_.</span><span class="sxs-lookup"><span data-stu-id="53b8c-205">The first step is to point the Mixed Reality Feature Tool to your **Project path** using the **ellipsis** button, click on the Three dots ellipsis button next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">

<span data-ttu-id="53b8c-206">Wenn Sie den Ordner Ihres Projekts gefunden haben, klicken Sie auf die Schaltfläche „Öffnen“, um zum Mixed Reality-Featuretool zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="53b8c-206">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span> <span data-ttu-id="53b8c-207">Klicken Sie dann auf **Discover Features** (Features ermitteln).</span><span class="sxs-lookup"><span data-stu-id="53b8c-207">Then click on **Discover Features**.</span></span>

> [!NOTE]
> <span data-ttu-id="53b8c-208">Das Dialogfeld, das angezeigt wird, wenn Sie das Dateisystem nach dem Unity-Projektordner durchsuchen, enthält '_' als den Dateinamen.</span><span class="sxs-lookup"><span data-stu-id="53b8c-208">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="53b8c-209">Es muss ein Wert für den Dateinamen vorhanden sein, um die Auswahl des Ordners zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="53b8c-209">There must be a value for the file name to enable the folder to be selected.</span></span>

> [!Important]
> <span data-ttu-id="53b8c-210">Das Mixed Reality-Featuretool führt eine Überprüfung durch, um sicherzustellen, dass die Weiterleitung an einen Unity-Projektordner erfolgt.</span><span class="sxs-lookup"><span data-stu-id="53b8c-210">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="53b8c-211">Der Ordner muss die Ordner „Assets“, „Packages“ und „Project Settings“ enthalten.</span><span class="sxs-lookup"><span data-stu-id="53b8c-211">The folder must contain Assets, Packages and Project Settings folders.</span></span>

<span data-ttu-id="53b8c-212">Die Features sind nach Kategorie gruppiert, damit sie leichter zu finden sind. Klicken Sie auf das Dropdownmenü **Mixed Reality-Toolkit**, um Pakete im Zusammenhang mit dem Mixed Reality-Toolkit zu finden.</span><span class="sxs-lookup"><span data-stu-id="53b8c-212">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-4.PNG" width="650px" alt="MixedRealityFeatureTool Discover Features">

<span data-ttu-id="53b8c-213">Aktivieren Sie das Kontrollkästchen **Mixed Reality Toolkit Foundation**, und klicken Sie auf die Dropdownliste daneben, um **MRTK 2.7.0** auszuwählen. Klicken Sie dann auf die Schaltfläche **Get Features** (Features abrufen), um die ausgewählten Pakete herunterzuladen.</span><span class="sxs-lookup"><span data-stu-id="53b8c-213">check the **Mixed Reality Toolkit Foundation**, and click on the dropdown next to it to select **MRTK 2.7.0**, then click on **Get features** button to download the selected packages.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-5.PNG" width="650px" alt="MixedRealityFeatureTool Open Mixed Reality">

<span data-ttu-id="53b8c-214">Klicken Sie dann auf die Schaltfläche **Validate** (Überprüfen), um das ausgewählte Paket zu überprüfen, Es wird ein Popupfenster mit der Nachricht **No validation issues were detected** (Bei der Überprüfung wurden keine Probleme erkannt) angezeigt. Klicken Sie auf **OK**, um das Popup zu schließen, und klicken Sie auf die Schaltfläche **Import** (Importieren).</span><span class="sxs-lookup"><span data-stu-id="53b8c-214">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-6.PNG" width="650px" alt="MixedRealityFeatureTool Select required package">

<span data-ttu-id="53b8c-215">Klicken Sie auf die Schalftläche **Approve** (Genehmigen), um dem Projekt das **Mixed Reality-Toolkit** hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="53b8c-215">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-7.PNG" width="650px" alt="MixedRealityFeatureTool Validate package">


## <a name="configuring-the-unity-project"></a><span data-ttu-id="53b8c-216">Konfigurieren des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="53b8c-216">Configuring the Unity project</span></span>

<span data-ttu-id="53b8c-217">Nachdem Unity das Importieren des Pakets aus dem vorherigen Abschnitt abgeschlossen hat, sollte das Fenster des MRTK-Projektkonfigurators angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="53b8c-217">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="53b8c-218">Wenn das nicht der Fall ist, öffnen Sie es, indem Sie zu **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK** (Mixed Reality > Toolkit > Hilfsprogramme > Projekt für MRTK konfigurieren) wechseln:</span><span class="sxs-lookup"><span data-stu-id="53b8c-218">If it doesn't, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**:</span></span>

![Unity: Menüpfad für „Configure Unity Project“](../images/mr-learning-base/base-02-section5-step1-1.png)

<span data-ttu-id="53b8c-220">Klicken Sie auf **Legacy XR**, um Legacy-XR zu aktivieren und ihrem Projekt die erforderlichen Pakete hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="53b8c-220">Click on **Legacy XR** to enable Legacy XR and to add its required packages  into your project.</span></span>

![s](../images/mr-learning-base/base-02-section5-step1-2.png)

<span data-ttu-id="53b8c-222">Klicken Sie auf die Schaltfläche „Weiter“, um XR-Pipelineeinstellungen für Legacy-XR zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="53b8c-222">Click on next button to enable XR pipeline settings for Legacy XR.</span></span>

![Unity MRTK-Konfigurationsfenster](../images/mr-learning-base/base-02-section5-step1-3.PNG)

<span data-ttu-id="53b8c-224">Stellen Sie im Fenster des MRTK-Projektkonfigurators sicher, dass alle Optionen aktiviert sind, und verwenden Sie außerdem die Dropdownliste **Audio spatializer** (Räumliche Audiowiedergabe), um den **MS HRTF Spatializer** auszuwählen, und klicken Sie dann auf die Schaltfläche **Übernehmen**, um die Einstellung zu übernehmen:</span><span class="sxs-lookup"><span data-stu-id="53b8c-224">In the MRTK Project Configurator window, ensure all options are checked and also use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![MRTK-Konfigurationsfenster](../images/mr-learning-base/base-02-section5-step1-4.PNG)

> [!TIP]
> <span data-ttu-id="53b8c-226">Die Anwendung der MRTK-Standardeinstellungen ist optional, wird aber dringend empfohlen, weil es bei der Konfiguration einiger empfohlener Unity-Einstellungen hilfreich ist:</span><span class="sxs-lookup"><span data-stu-id="53b8c-226">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>

> * <span data-ttu-id="53b8c-227">Legen Sie den Single Pass-instanziierten Renderingpfad fest: Verbessert die Grafikleistung, indem die Renderpipeline für beide Augen im selben Zeichnen-Aufruf ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="53b8c-227">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="53b8c-228">Weitere Informationen zu diesem Thema finden Sie im Abschnitt [Single Pass-instanziiertes Rendering](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) der [Leistung](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering)sdokumentation von MRTK.</span><span class="sxs-lookup"><span data-stu-id="53b8c-228">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) section of MRTK's [Performance](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) documentation.</span></span>
> * <span data-ttu-id="53b8c-229">Standardebene für Spatial Awareness (räumliche Wahrnehmung) festlegen: Erstellt eine Unity-Ebene namens „Spatial Awareness“ und konfiguriert MRTK für die Verwendung dieser Ebene für das Gittermodell für räumliche Wahrnehmung.</span><span class="sxs-lookup"><span data-stu-id="53b8c-229">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="53b8c-230">Weitere Informationen zu Unity-Ebenen finden Sie in der Unity-Dokumentation zum <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Anpassen Ihres Arbeitsbereichs</a>.</span><span class="sxs-lookup"><span data-stu-id="53b8c-230">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

> [!TIP]
> <span data-ttu-id="53b8c-231">Das Festlegen der „Audio Spatializer“-Eigenschaft ist optional, kann aber die Audioerfahrung in Ihrem Projekt verbessern.</span><span class="sxs-lookup"><span data-stu-id="53b8c-231">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="53b8c-232">Wenn Sie sie auf „MS HRTF Spatializer“ festlegen, wird dieses Spatializer-Plug-In verwendet, wenn die Eigenschaft „AudioSource.spatialize“ von Unity aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="53b8c-232">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="53b8c-233">Weitere Informationen zu diesem Thema finden Sie in den <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">Tutorials zur räumlichen Audiowiedergabe</a>.</span><span class="sxs-lookup"><span data-stu-id="53b8c-233">To learn more about this topic, you can refer to the  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="53b8c-234">Klicken Sie auf **Weiter** und dann im Fenster des MRTK-Projektkonfigurators auf die Schaltfläche **Fertig**, um die Unity-Projektkonfiguration für Legacy-XR fertig zu stellen.</span><span class="sxs-lookup"><span data-stu-id="53b8c-234">Click on **Next** then click on **Done** button in MRTK Project Configurator window to finish the Unity project configuration for Legacy XR.</span></span>

### <a name="configure-additional-project-settings"></a><span data-ttu-id="53b8c-235">Konfigurieren zusätzlicher Projekteinstellungen</span><span class="sxs-lookup"><span data-stu-id="53b8c-235">Configure additional project settings</span></span>

<span data-ttu-id="53b8c-236">Wählen Sie im Unity-Menü **Edit** > **Project Settings...** (Bearbeiten > Projekteinstellungen...) aus, um das Fenster „Project Settings“ (Projekteinstellungen) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="53b8c-236">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

<span data-ttu-id="53b8c-237">Wählen Sie im Fenster „Project Settings“ (Projekteinstellungen) **Player** > **XR Settings** (Player > XR-Einstellungen) aus, und verwenden Sie dann die Dropdownliste **Depth Format** (Tiefenformat), um **16-Bit Tiefe** auszuwählen:</span><span class="sxs-lookup"><span data-stu-id="53b8c-237">In the Project Settings window, select **Player** > **XR Settings**, then use the **Depth Format** dropdown to select **16-bit depth**:</span></span>

![Unity: Tiefe 16 aktivieren](../images/mr-learning-base/base-02-section5-step2-1.png)

> [!TIP]
> <span data-ttu-id="53b8c-239">Das Verringern des Tiefenformats auf 16 Bit ist optional, kann aber bei der Verbesserung der Grafikleistung in Ihrem Projekt helfen.</span><span class="sxs-lookup"><span data-stu-id="53b8c-239">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="53b8c-240">Weitere Informationen zu diesem Thema finden Sie im Abschnitt <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Tiefenpufferfreigabe (HoloLens)</a> der Leistungsdokumentation zum MRTK.</span><span class="sxs-lookup"><span data-stu-id="53b8c-240">To learn more about this topic, you can refer to the <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> section of MRTK's Performance documentation.</span></span>

<span data-ttu-id="53b8c-241">Wählen Sie im Fenster „Project Settings“ (Projekteinstellungen) **Player** > **Publishing Settings** (Player > Veröffentlichungseinstellungen) aus, geben Sie dann im Feld **Package name** (Paketname) einen passenden Namen ein, beispielsweise _MRTKTutorials-GettingStarted_:</span><span class="sxs-lookup"><span data-stu-id="53b8c-241">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Veröffentlichungseinstellungen in Unity.](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> <span data-ttu-id="53b8c-244">Der Paketname stellt den eindeutigen Bezeichner für die App dar.</span><span class="sxs-lookup"><span data-stu-id="53b8c-244">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="53b8c-245">Sie sollten diesen Bezeichner ändern, bevor Sie die App bereitstellen, um das Überschreiben zuvor installierter Apps zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="53b8c-245">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="53b8c-246">Der „Product Name“ (Produktname) ist der Name, der im HoloLens-Startmenü angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="53b8c-246">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="53b8c-247">Um das Auffinden der App während der Entwicklung zu erleichtern, fügen Sie vor dem Namen einen Unterstrich hinzu, sodass sie in Listen oben einsortiert wird.</span><span class="sxs-lookup"><span data-stu-id="53b8c-247">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>
