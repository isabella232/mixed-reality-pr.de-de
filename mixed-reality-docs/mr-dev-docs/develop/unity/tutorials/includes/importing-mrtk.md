---
ms.openlocfilehash: 7c86356a960929839f36cf326c5dd1a1005e64d2
ms.sourcegitcommit: 95fbb851336b6c5977a2ce4d4ac10f0eeb0df31f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2021
ms.locfileid: "107984289"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="f969b-101">Unity 2019/2020 und Windows-XR-Plugin</span><span class="sxs-lookup"><span data-stu-id="f969b-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="f969b-102">Klicken Sie nach dem Öffnen von **MixedRealityFeatureTool** auf „Start“ um mit dem Mixed Reality-Featuretool loszulegen.</span><span class="sxs-lookup"><span data-stu-id="f969b-102">Once **MixedRealityFeatureTool** is opened click on start to get started with Mixed Reality Feature Tool.</span></span>

![MixedRealityFeatureTool-Fenster für Windows XR-Plug-In](../images/mr-learning-base/base-02-section4-step1-2.png)

<span data-ttu-id="f969b-104">Die Features sind nach Kategorie gruppiert, damit sie leichter zu finden sind. Klicken Sie auf das Dropdownmenü **Mixed Reality-Toolkit**, um Pakete im Zusammenhang mit dem Mixed Reality-Toolkit zu finden.</span><span class="sxs-lookup"><span data-stu-id="f969b-104">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit.</span></span>

![MixedRealityFeatureTool-Fenster](../images/mr-learning-base/base-02-section4-step1-3.png)

<span data-ttu-id="f969b-106">Aktivieren Sie **Mixed Reality Toolkit Foundation**, und klicken Sie auf die Dropdownliste daneben, um die aktuelle MRTK-Version auszuwählen. Klicken Sie dann auf die Schaltfläche **Features abrufen**, um die ausgewählten Pakete herunterzuladen.</span><span class="sxs-lookup"><span data-stu-id="f969b-106">check the **Mixed Reality Toolkit Foundation**, and click on the dropdown next to it to select the latest MRTK version, then click on **Get features** button to download the selected packages.</span></span>

![Auswählen von Mixed Reality Foundation](../images/mr-learning-base/base-02-section4-step1-4.png)


<span data-ttu-id="f969b-108">Sie müssen darüber hinaus den Speicherort des Unity-Zielprojekts festlegen. Zum Angeben des **Projektpfads** klicken Sie auf die **Drei Punkte** neben dem Projektpfad, und wechseln Sie im Explorer zu Ihrem Projektordner, beispielsweise _D:\MixedRealityLearning\MRTK Tutorials_.</span><span class="sxs-lookup"><span data-stu-id="f969b-108">You also need to set the location of the target unity project to provide the **Project path**, click on the **Three dots** next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

> [!NOTE]
> <span data-ttu-id="f969b-109">Das Dialogfeld, das angezeigt wird, wenn Sie das Dateisystem nach dem Unity-Projektordner durchsuchen, enthält '_' als den Dateinamen.</span><span class="sxs-lookup"><span data-stu-id="f969b-109">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="f969b-110">Es muss ein Wert für den Dateinamen vorhanden sein, um die Auswahl des Ordners zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="f969b-110">There must be a value for the file name to enable the folder to be selected.</span></span>

<span data-ttu-id="f969b-111">Klicken Sie dann auf die Schaltfläche **Validate** (Überprüfen), um das ausgewählte Paket zu überprüfen, Es wird ein Popupfenster mit der Nachricht **No validation issues were detected** (Bei der Überprüfung wurden keine Probleme erkannt) angezeigt. Klicken Sie auf **OK**, um das Popup zu schließen, und klicken Sie auf die Schaltfläche **Import** (Importieren).</span><span class="sxs-lookup"><span data-stu-id="f969b-111">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

![Überprüfen der Mixed Reality Foundation](../images/mr-learning-base/base-02-section4-step1-5.png)

<span data-ttu-id="f969b-113">Klicken Sie auf die Schalftläche **Approve** (Genehmigen), um dem Projekt das **Mixed Reality-Toolkit** hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="f969b-113">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

![Genehmigen von Mixed Reality Foundation](../images/mr-learning-base/base-02-section4-step1-6.png)

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="f969b-115">Unity 2020 und OpenXR</span><span class="sxs-lookup"><span data-stu-id="f969b-115">Unity 2020 + OpenXR</span></span>](#tab/openxr)
<span data-ttu-id="f969b-116">Klicken Sie im Fenster unten links auf das Zahnradsymbol, um das Einstellungsmenü zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="f969b-116">In the bottom left hand of the window, click on the gear symbol to open the settings menu.</span></span>

![MixedRealityFeatureTool](../images/mr-learning-base/base-02-section4-step1-2.png)

<span data-ttu-id="f969b-118">Aktivieren Sie unter **Featureeinstellungen** das Kontrollkästchen **Vorabversionen einschließen**, und klicken Sie dann auf die Schaltfläche **OK**.</span><span class="sxs-lookup"><span data-stu-id="f969b-118">Under **Feature Settings**, check the **Include preview releases** box and then click the **OK** button.</span></span>

![Fenster mit MixedRealityFeatureTool-Einstellungen](../images/mrft-settings.png)

> [!NOTE]
><span data-ttu-id="f969b-120">Wenn keine Option zum Einschließen von Vorabversionen angezeigt wird, vergewissern Sie sich, dass Sie die aktuelle Version des MR-Featuretools verwenden.</span><span class="sxs-lookup"><span data-stu-id="f969b-120">If you do not see an option to include preview releases, make sure you're using the latest version of the MR Feature Tool.</span></span>

<span data-ttu-id="f969b-121">Nachdem Sie Ihre Einstellungen konfiguriert haben, klicken Sie auf **Start**, um mit dem Featuretool für Mixed Reality beginnen.</span><span class="sxs-lookup"><span data-stu-id="f969b-121">Now that your settings are configured, click on **Start** to get started with Mixed Reality Feature Tool.</span></span>

![Startbildschirm des MixedRealityFeatureTool-Fensters](../images/mr-learning-base/base-02-section4-step1-2.png)

<span data-ttu-id="f969b-123">Die Features sind nach Kategorie gruppiert, damit sie leichter zu finden sind. Klicken Sie auf das Dropdownmenü **Mixed Reality-Toolkit**, um Pakete im Zusammenhang mit dem Mixed Reality-Toolkit zu finden.</span><span class="sxs-lookup"><span data-stu-id="f969b-123">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit.</span></span>
<span data-ttu-id="f969b-124">Aktivieren Sie die **Mixed Reality Toolkit Foundation**, und klicken Sie auf die Dropdownliste daneben, um die erforderliche MRTK-Version auszuwählen. Wählen Sie für diese Tutorialreihe das aktuelle **Vorschaupaket 2.7** aus.</span><span class="sxs-lookup"><span data-stu-id="f969b-124">Check the **Mixed Reality Toolkit Foundation**, and click on the dropdown next to it to select the required MRTK version, for this tutorial series please select the latest **2.7 preview package**.</span></span>

![MixedRealityFeatureTool-Fenster für Unity 2020 und OpenXR](../images/mrft-mrtk.png)

<span data-ttu-id="f969b-126">Wählen Sie in der Dropdownliste **Plattformunterstützung** das **Mixed Reality OpenXR-Plug-In** aus.</span><span class="sxs-lookup"><span data-stu-id="f969b-126">Under the **Platform Support** dropdown, select **Mixed Reality OpenXR Plugin**.</span></span> <span data-ttu-id="f969b-127">Achten Sie darauf, dass in der Dropdownliste die aktuelle Version ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="f969b-127">Make sure the latest version is selected in the dropdown.</span></span>
<span data-ttu-id="f969b-128">![Auswählen des Mixed Reality OpenXR-Plug-Ins](../images/mrft-openxr.png)</span><span class="sxs-lookup"><span data-stu-id="f969b-128">![Selecting Mixed Reality OpenXR Plugin](../images/mrft-openxr.png)</span></span>

<span data-ttu-id="f969b-129">Klicken Sie auf die Schaltfläche **Features abrufen**, um die ausgewählten Pakete herunterzuladen.</span><span class="sxs-lookup"><span data-stu-id="f969b-129">Click on the **Get features** button to download the selected packages.</span></span>

<span data-ttu-id="f969b-130">Sie müssen darüber hinaus den Speicherort des Unity-Zielprojekts festlegen. Zum Angeben des **Projektpfads** klicken Sie auf die **Drei Punkte** neben dem Projektpfad, und wechseln Sie im Explorer zu Ihrem Projektordner, beispielsweise _D:\MixedRealityLearning\MRTK Tutorials_.</span><span class="sxs-lookup"><span data-stu-id="f969b-130">You also need to set the location of the target unity project to provide the **Project path**, click on the **Three dots** next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

> [!NOTE]
> <span data-ttu-id="f969b-131">Das Dialogfeld, das angezeigt wird, wenn Sie das Dateisystem nach dem Unity-Projektordner durchsuchen, enthält '_' als den Dateinamen.</span><span class="sxs-lookup"><span data-stu-id="f969b-131">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="f969b-132">Es muss ein Wert für den Dateinamen vorhanden sein, um die Auswahl des Ordners zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="f969b-132">There must be a value for the file name to enable the folder to be selected.</span></span>

<span data-ttu-id="f969b-133">Klicken Sie dann auf die Schaltfläche **Validate** (Überprüfen), um das ausgewählte Paket zu überprüfen, Es wird ein Popupfenster mit der Nachricht **No validation issues were detected** (Bei der Überprüfung wurden keine Probleme erkannt) angezeigt. Klicken Sie auf **OK**, um das Popup zu schließen, und klicken Sie auf die Schaltfläche **Import** (Importieren).</span><span class="sxs-lookup"><span data-stu-id="f969b-133">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

![Überprüfen der Mixed Reality Foundation](../images/mrft-openxr-validate2.png)

<span data-ttu-id="f969b-135">Klicken Sie auf die Schalftläche **Genehmigen**, um dem Projekt das **Mixed Reality-Toolkit** hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="f969b-135">Click on the **Approve** button to add the **Mixed Reality Toolkit** into the project.</span></span>

![Genehmigen von Mixed Reality Foundation](../images/mrft-openxr-import.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="f969b-137">Legacy-WSA</span><span class="sxs-lookup"><span data-stu-id="f969b-137">Legacy WSA</span></span>](#tab/wsa)
<span data-ttu-id="f969b-138">Klicken Sie nach dem Öffnen von **MixedRealityFeatureTool** auf „Start“ um mit dem Mixed Reality-Featuretool loszulegen.</span><span class="sxs-lookup"><span data-stu-id="f969b-138">Once **MixedRealityFeatureTool** is opened click on start to get started with Mixed Reality Feature Tool.</span></span>

![MixedRealityFeatureTool für Legacy-WSA](../images/mr-learning-base/base-02-section4-step1-2.png)

<span data-ttu-id="f969b-140">Die Features sind nach Kategorie gruppiert, damit sie leichter zu finden sind. Klicken Sie auf das Dropdownmenü **Mixed Reality-Toolkit**, um Pakete im Zusammenhang mit dem Mixed Reality-Toolkit zu finden.</span><span class="sxs-lookup"><span data-stu-id="f969b-140">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit.</span></span>

![MixedRealityFeatureTool-Fenster](../images/mr-learning-base/base-02-section4-step1-3.png)

<span data-ttu-id="f969b-142">Aktivieren Sie **Mixed Reality Toolkit Foundation**, und klicken Sie auf die Dropdownliste daneben, um die aktuelle MRTK-Version auszuwählen. Klicken Sie dann auf die Schaltfläche **Features abrufen**, um die ausgewählten Pakete herunterzuladen.</span><span class="sxs-lookup"><span data-stu-id="f969b-142">check the **Mixed Reality Toolkit Foundation**, and click on the dropdown next to it to select the latest MRTK version, then click on **Get features** button to download the selected packages.</span></span>

![Auswählen von Mixed Reality Foundation](../images/mr-learning-base/base-02-section4-step1-4.png)

<span data-ttu-id="f969b-144">Sie müssen darüber hinaus den Speicherort des Unity-Zielprojekts festlegen. Zum Angeben des **Projektpfads** klicken Sie auf die **Drei Punkte** neben dem Projektpfad, und wechseln Sie im Explorer zu Ihrem Projektordner, beispielsweise _D:\MixedRealityLearning\MRTK Tutorials_.</span><span class="sxs-lookup"><span data-stu-id="f969b-144">You also need to set the location of the target unity project to provide the **Project path**, click on the **Three dots** next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

> [!NOTE]
> <span data-ttu-id="f969b-145">Das Dialogfeld, das angezeigt wird, wenn Sie das Dateisystem nach dem Unity-Projektordner durchsuchen, enthält '_' als den Dateinamen.</span><span class="sxs-lookup"><span data-stu-id="f969b-145">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="f969b-146">Es muss ein Wert für den Dateinamen vorhanden sein, um die Auswahl des Ordners zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="f969b-146">There must be a value for the file name to enable the folder to be selected.</span></span>

<span data-ttu-id="f969b-147">Klicken Sie dann auf die Schaltfläche **Validate** (Überprüfen), um das ausgewählte Paket zu überprüfen, Es wird ein Popupfenster mit der Nachricht **No validation issues were detected** (Bei der Überprüfung wurden keine Probleme erkannt) angezeigt. Klicken Sie auf **OK**, um das Popup zu schließen, und klicken Sie auf die Schaltfläche **Import** (Importieren).</span><span class="sxs-lookup"><span data-stu-id="f969b-147">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

![Überprüfen der Mixed Reality Foundation](../images/mr-learning-base/base-02-section4-step1-5.png)

<span data-ttu-id="f969b-149">Klicken Sie auf die Schalftläche **Approve** (Genehmigen), um dem Projekt das **Mixed Reality-Toolkit** hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="f969b-149">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

![Genehmigen von Mixed Reality Foundation](../images/mr-learning-base/base-02-section4-step1-6.png)

