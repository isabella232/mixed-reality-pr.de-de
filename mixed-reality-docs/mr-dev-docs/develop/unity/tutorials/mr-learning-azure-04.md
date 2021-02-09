---
title: Integrieren von Azure Spatial Anchors
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie Azure Spatial Anchors innerhalb einer HoloLens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, HoloLens 2, Azure Spatial Anchors, Azure Cloud Services, Azure Custom Vision, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 0837ebd9d34ba12d660098fc765824da3c561d07
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590542"
---
# <a name="4-integrating-azure-spatial-anchors"></a><span data-ttu-id="ed2e8-104">4. Integrieren von Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="ed2e8-104">4. Integrating Azure Spatial Anchors</span></span>

<span data-ttu-id="ed2e8-105">In diesem Tutorial erfahren Sie, wie Sie **Azure Spatial Anchors** verwenden.</span><span class="sxs-lookup"><span data-stu-id="ed2e8-105">In this tutorial, you will learn how to use **Azure Spatial Anchors**.</span></span> <span data-ttu-id="ed2e8-106">Sie speichern die Position eines **nachverfolgten Objekts** als Azure Spatial Anchor.</span><span class="sxs-lookup"><span data-stu-id="ed2e8-106">You will store the location of a **Tracked Object** as an Azure Spatial Anchor.</span></span> <span data-ttu-id="ed2e8-107">Sobald Sie eine Abfrage für den Anker ausführen, wird ein Pfeil angezeigt, der Sie zu der Position leitet.</span><span class="sxs-lookup"><span data-stu-id="ed2e8-107">Once you query for the anchor, an arrow will appear to guide you toward the location.</span></span>

## <a name="objectives"></a><span data-ttu-id="ed2e8-108">Ziele</span><span class="sxs-lookup"><span data-stu-id="ed2e8-108">Objectives</span></span>

* <span data-ttu-id="ed2e8-109">Erlernen Sie die Grundlagen von Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="ed2e8-109">Learn the basics of Azure Spatial Anchors.</span></span>
* <span data-ttu-id="ed2e8-110">Erfahren Sie, wie Sie die Szene einrichten, um Azure Spatial Anchors in diesem Projekt zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="ed2e8-110">Learn how to set up the scene to use Azure Spatial Anchors in this project.</span></span>
* <span data-ttu-id="ed2e8-111">Erfahren Sie, wie Sie Speicher- und Abfragespositionen integrieren.</span><span class="sxs-lookup"><span data-stu-id="ed2e8-111">Learn how to integrate storing and querying locations.</span></span>

## <a name="understanding-azure-spatial-anchors"></a><span data-ttu-id="ed2e8-112">Grundlegendes zu Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="ed2e8-112">Understanding Azure Spatial Anchors</span></span>

 <span data-ttu-id="ed2e8-113">**Azure Spatial Anchors** ist Teil der Azure Cloud Services-Produktfamilie und wird zum Speichern von Ankerpositionen verwendet.</span><span class="sxs-lookup"><span data-stu-id="ed2e8-113">**Azure Spatial Anchors** is part of the Azure Cloud Services family and is used to save anchor locations.</span></span> <span data-ttu-id="ed2e8-114">Die gespeicherten Ankerpositionen können basierend auf der *Anker-ID* aus der Cloud abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="ed2e8-114">The saved anchor locations can be retrieved based on the *anchor ID* from the cloud.</span></span> <span data-ttu-id="ed2e8-115">Diese Ankerposition kann von Multi-Plattformgeräten wie HoloLens-, iOS- und Android-Geräten gemeinsam genutzt werden.</span><span class="sxs-lookup"><span data-stu-id="ed2e8-115">This anchor location can be shared and accessed by multi-platform devices like HoloLens, iOS, and Android devices.</span></span>

<span data-ttu-id="ed2e8-116">Weitere Informationen zu [Azure Spatial Anchors](/azure/spatial-anchors/overview).</span><span class="sxs-lookup"><span data-stu-id="ed2e8-116">Learn more about [Azure Spatial Anchors](/azure/spatial-anchors/overview).</span></span>

## <a name="preparing-azure-spatial-anchors"></a><span data-ttu-id="ed2e8-117">Vorbereiten von Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="ed2e8-117">Preparing Azure Spatial Anchors</span></span>

<span data-ttu-id="ed2e8-118">Bevor Sie beginnen können, müssen Sie im Azure-Portal eine räumliche Ankerressource erstellen.</span><span class="sxs-lookup"><span data-stu-id="ed2e8-118">Before you can start, you have to create a spatial anchor resource in your Azure portal.</span></span>
<span data-ttu-id="ed2e8-119">Erfahren Sie, wie Sie eine [räumliche Ankerressource](/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource) erstellen können.</span><span class="sxs-lookup"><span data-stu-id="ed2e8-119">Learn how to make a [spatial anchor resource](/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource).</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="ed2e8-120">Vorbereiten der Szene</span><span class="sxs-lookup"><span data-stu-id="ed2e8-120">Preparing the scene</span></span>

<span data-ttu-id="ed2e8-121">In diesem Abschnitt erfahren Sie, wie Sie die Szene konfigurieren und die erforderlichen Änderungen vornehmen.</span><span class="sxs-lookup"><span data-stu-id="ed2e8-121">In this section, you will learn how to configure the scene and make the necessary changes.</span></span>

<span data-ttu-id="ed2e8-122">Navigieren Sie im Projektfenster zu **Assets > MRTK.Tutorials.AzureCloudServices > Prefabs > Manager**.</span><span class="sxs-lookup"><span data-stu-id="ed2e8-122">In the Project window, navigate to the **Assets > MRTK.Tutorials.AzureCloudServices > Prefabs > Manager**</span></span>

![Unity mit ausgewähltem AnchorManager-Prefab](images/mr-learning-azure/tutorial4-section1-step1-1.png)

<span data-ttu-id="ed2e8-124">Ziehen Sie das Prefab **Anchor Manager** (Anker-Manager) aus dem Ordner **Manager** mithilfe von Drag & Drop in die Hierarchie der Szene.</span><span class="sxs-lookup"><span data-stu-id="ed2e8-124">From the **Manager** folder, drag and drop the prefab **Anchor Manager** into the scene Hierarchy.</span></span>

<span data-ttu-id="ed2e8-125">Wählen Sie „**Anchor Manager** GameObject“ in der Hierarchie aus. Im Abschnitt „Inspector“ finden Sie **Spatial Anchor Manager (Script)** .</span><span class="sxs-lookup"><span data-stu-id="ed2e8-125">Select **Anchor Manager** GameObject in the Hierarchy, and in the Inspector section, you will find **Spatial Anchor Manager** (Script).</span></span> <span data-ttu-id="ed2e8-126">Suchen Sie nach der Konto-ID und dem Schlüsselfeld, und fügen Sie die Anmeldeinformationen hinzu, die Sie in der vorherigen Phase als Voraussetzung erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="ed2e8-126">Find account ID and key field and add the credentials which you had created in the prerequisite in the earlier stage.</span></span>

![Unity mit neu hinzugefügtem, noch ausgewähltem AnchorManager-Prefab](images/mr-learning-azure/tutorial4-section1-step2-1.png)

<span data-ttu-id="ed2e8-128">Suchen Sie nun das **Scene Controller**-Objekt (Szenencontroller) in der Hierarchie Ihrer Szene, und wählen Sie es aus.</span><span class="sxs-lookup"><span data-stu-id="ed2e8-128">Now find the **Scene Controller** object in your scene Hierarchy and select it.</span></span> <span data-ttu-id="ed2e8-129">Der **Scene Controller**-Inspektor wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ed2e8-129">You will see the **Scene Controller** Inspector.</span></span>

![Unity mit konfigurierter SceneController-Skriptkomponente](images/mr-learning-azure/tutorial4-section1-step3-1.png)

<span data-ttu-id="ed2e8-131">Sie sehen, dass das Feld **Anchor Manager** in der Komponente **Scene Controller** leer ist. Ziehen Sie **Anchor Manager** mithilfe von Drag & Drop aus der Hierarchie in der Szene in dieses Feld, und speichern Sie die Szene.</span><span class="sxs-lookup"><span data-stu-id="ed2e8-131">You will observe that the **Anchor Manager** field in the **Scene Controller** component is empty, drag and drop the **Anchor Manager** from the Hierarchy in the scene into that field and save the scene.</span></span>

## <a name="build-and-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="ed2e8-132">Erstellen und Bereitstellen der App auf dem HoloLens 2-Gerät</span><span class="sxs-lookup"><span data-stu-id="ed2e8-132">Build and Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="ed2e8-133">Azure Spatial Anchors können nicht in Unity ausgeführt werden, daher müssen Sie das Projekt auf Ihrem Gerät bereitstellen, um die Azure Spatial Anchors-Funktionalität zu testen.</span><span class="sxs-lookup"><span data-stu-id="ed2e8-133">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to deploy the project to your device.</span></span>

> [!TIP]
> <span data-ttu-id="ed2e8-134">Falls Sie eine Auffrischung zum Erstellen und Bereitstellen Ihres Unity-Projekts auf HoloLens 2 benötigen, lesen Sie die Anweisungen unter [Erstellen Ihrer Anwendung für das HoloLens 2-Gerät](mr-learning-base-02.md#building-and-deploying-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="ed2e8-134">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your application to your HoloLens 2]((mr-learning-base-02.md#building-and-deploying-to-your-hololens-2) instructions.</span></span>

## <a name="run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="ed2e8-135">Führen Sie die App auf Ihrer HoloLens 2 aus, und folgen Sie den Anweisungen in der App</span><span class="sxs-lookup"><span data-stu-id="ed2e8-135">Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

### <a name="create-an-anchor-to-store-a-location"></a><span data-ttu-id="ed2e8-136">Erstellen eines Ankers zum Speichern einer Position</span><span class="sxs-lookup"><span data-stu-id="ed2e8-136">Create an anchor to store a location</span></span>

<span data-ttu-id="ed2e8-137">In diesem Abschnitt erfahren Sie, wie Sie die Objektposition speichern.</span><span class="sxs-lookup"><span data-stu-id="ed2e8-137">In this section you will see how to save the object location.</span></span>

<span data-ttu-id="ed2e8-138">Führen Sie die Anwendung aus, und klicken Sie im Hauptmenü der Benutzeroberfläche auf **Set Object** (Objekt festlegen).</span><span class="sxs-lookup"><span data-stu-id="ed2e8-138">Run the application and click on **Set Object** in the main menu of the experience.</span></span>

<span data-ttu-id="ed2e8-139">Geben Sie den **Namen** des Objekts an, das Sie speichern möchten, und klicken Sie auf **Set Object** (Objekt festlegen), um den Vorgang fortzusetzen.</span><span class="sxs-lookup"><span data-stu-id="ed2e8-139">Give the **name** of the object you want to save and click on **Set Object** to continue.</span></span> <span data-ttu-id="ed2e8-140">Wenn Sie weitere Informationen zum Objekt hinzufügen möchten, wählen Sie das **Bild** aus, und beschreiben Sie das Objekt.</span><span class="sxs-lookup"><span data-stu-id="ed2e8-140">To add more information about the object, select the **image**, and describe the object.</span></span>

<span data-ttu-id="ed2e8-141">Um die Position zu speichern, klicken Sie auf **Save Location** (Position speichern).</span><span class="sxs-lookup"><span data-stu-id="ed2e8-141">To save the location, click on **Save Location**</span></span>

<span data-ttu-id="ed2e8-142">Sie sehen einen **Ankerzeiger**, den Sie verschieben und an der Position platzieren können, die Sie speichern möchten.</span><span class="sxs-lookup"><span data-stu-id="ed2e8-142">You will see an **anchor pointer** that you can move and place on the location you want to save.</span></span> <span data-ttu-id="ed2e8-143">Anschließend wird ein Bestätigungspopupfenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ed2e8-143">After that, you will get a confirmation popup.</span></span> <span data-ttu-id="ed2e8-144">Wenn Sie die Position bestätigen und speichern möchten, klicken Sie auf **Yes** (Ja). Andernfalls können Sie die Position ändern, indem Sie auf **No** (Nein) klicken und die Position erneut auswählen.</span><span class="sxs-lookup"><span data-stu-id="ed2e8-144">If you want to confirm and save the location, click on **Yes**; otherwise, you can change the location by clicking on **No** and selecting the location again.</span></span>

<span data-ttu-id="ed2e8-145">Nachdem Sie die Position durch Klicken auf **Yes** bestätigt haben, werden die Position und die Anker-ID im Azure-Cloudspeicher gespeichert.</span><span class="sxs-lookup"><span data-stu-id="ed2e8-145">Once you confirm the location by clicking on **Yes**, the location and the Anchor ID will be saved in the Azure cloud storage.</span></span> <span data-ttu-id="ed2e8-146">Nach dem Speichern wird das **Objekttag** im Anker mit dem Namen des Objekts angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ed2e8-146">Once it is saved, you will see the **Object tag**  in the anchor with the object's name.</span></span>

<span data-ttu-id="ed2e8-147">Die Objektposition wurde nun erfolgreich gespeichert.</span><span class="sxs-lookup"><span data-stu-id="ed2e8-147">Now the object location is saved successfully.</span></span>

### <a name="query-for-finding-an-anchor-location"></a><span data-ttu-id="ed2e8-148">Abfrage zum Suchen nach einer Ankerposition</span><span class="sxs-lookup"><span data-stu-id="ed2e8-148">Query for finding an anchor location</span></span>

<span data-ttu-id="ed2e8-149">Nachdem Sie die Ankerposition ein Mal erfolgreich gespeichert haben, können Sie die Ankerposition nun durch Auswählen von **Search Object** (Nach Objekt suchen) im Hauptmenü ermitteln.</span><span class="sxs-lookup"><span data-stu-id="ed2e8-149">Once after you successfully saved the anchor location, now you can find the anchor location by selecting **Search Object** in the main menu.</span></span>

<span data-ttu-id="ed2e8-150">Nachdem Sie auf **Search Object** (Nach Objekt suchen) geklickt haben, wird ein neues Fenster geöffnet, in dem Sie den Namen des zu suchenden Objekts angeben.</span><span class="sxs-lookup"><span data-stu-id="ed2e8-150">After clicking on **Search Object**, a new window will pop up in which you should give the name of the object you want to search.</span></span>

<span data-ttu-id="ed2e8-151">Geben Sie den Namen des Objekts ein, und klicken Sie auf **Search Object** (Nach Objekt suchen).</span><span class="sxs-lookup"><span data-stu-id="ed2e8-151">Enter the name of the object and click on **Search Object**.</span></span> <span data-ttu-id="ed2e8-152">Wenn das Objekt zuvor gespeichert wurde und in der Datenbank gefunden wird, erhalten Sie die Objektkarte mit allen Details des Objekts, das Sie zuvor gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="ed2e8-152">If the object is saved previously and is found in the database, you will get the object card with all the details of the object you would have saved earlier.</span></span>

<span data-ttu-id="ed2e8-153">Nun können Sie auf **Show Location** (Position anzeigen) klicken, um nach dem Objekt zu suchen.</span><span class="sxs-lookup"><span data-stu-id="ed2e8-153">Now you can click on **Show Location** to find the object.</span></span> <span data-ttu-id="ed2e8-154">Wenn Sie auf **Show Location** (Position anzeigen) klicken, fragt das System die Objektadresse im Cloudspeicher ab.</span><span class="sxs-lookup"><span data-stu-id="ed2e8-154">Once you click on **Show Location**, the system will query the object address from the cloud storage.</span></span>

<span data-ttu-id="ed2e8-155">Nachdem Sie die Position erfolgreich abgerufen haben, weist ein **Pfeil** auf die Position des Objekts hin.</span><span class="sxs-lookup"><span data-stu-id="ed2e8-155">After successfully retrieving the location, an **arrow** will direct you towards the location of the object.</span></span> <span data-ttu-id="ed2e8-156">Folgen Sie der Pfeilmarkierung, bis Sie die Position des Objekts gefunden haben.</span><span class="sxs-lookup"><span data-stu-id="ed2e8-156">Follow the arrow mark until you find the location of the object.</span></span>

<span data-ttu-id="ed2e8-157">Nachdem Sie das Objekt gefunden haben, wird der Objektname oben angezeigt, und die Pfeilmarkierung wird ausgeblendet. Sie können nun auf das **Objekttag** klicken, um die Details des Objekts anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="ed2e8-157">Once you find the object, the object name will appear at the top, and the arrow mark will disappear, and now you can click on the **object tag** to see the details of the object.</span></span>

## <a name="congratulations"></a><span data-ttu-id="ed2e8-158">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="ed2e8-158">Congratulations</span></span>

<span data-ttu-id="ed2e8-159">In diesem Tutorial haben Sie erfahren, wie Azure Spatial Anchors die Objektposition auf HoloLens 2 speichern und abrufen kann.</span><span class="sxs-lookup"><span data-stu-id="ed2e8-159">In this tutorial, you learned how Azure Spatial Anchors could save and retrieve the object location on Hololense 2.</span></span>

<span data-ttu-id="ed2e8-160">Im letzten Tutorial erfahren Sie, wie Sie **Azure Bot Service** verwenden, um natürliche Sprache als neue Interaktionsmethode für die Anwendung hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="ed2e8-160">In the final tutorial, you will learn how to use the **Azure Bot Service** to add natural language as a new interaction method for our application.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ed2e8-161">Nächstes Tutorial: 5. Integrieren von Azure Bot Service in LUIS</span><span class="sxs-lookup"><span data-stu-id="ed2e8-161">Next tutorial: 5. Integrating Azure Bot Service with LUIS</span></span>](mr-learning-azure-05.md)