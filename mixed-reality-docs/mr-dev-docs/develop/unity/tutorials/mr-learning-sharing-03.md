---
title: Verbinden mehrerer Benutzer
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie mehrere Benutzer in einer HoloLens 2-Mixed Reality-Anwendung verbinden.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, Mehrbenutzerfunktionen, Photon, MRTK, Mixed Reality Toolkit, UWP, Azure Spatial Anchors
ms.localizationpriority: high
ms.openlocfilehash: 0c6bf0871836ad7aae9c3906b2042f97ae003ebf
ms.sourcegitcommit: 3dad2adfdb5bdb8100d8d864f7845e34a3ef912d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/22/2021
ms.locfileid: "98699064"
---
# <a name="3-connecting-multiple-users"></a><span data-ttu-id="f3f80-104">3. Verbinden mehrerer Benutzer</span><span class="sxs-lookup"><span data-stu-id="f3f80-104">3. Connecting multiple users</span></span>

<span data-ttu-id="f3f80-105">In diesem Tutorial lernen Sie, wie Sie mehrere Benutzer im Rahmen einer freigegebenen Live-Benutzererfahrung verbinden.</span><span class="sxs-lookup"><span data-stu-id="f3f80-105">In this tutorial, you will learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="f3f80-106">Am Ende des Tutorials können Sie die App auf mehreren Geräten ausführen, und jedem Benutzer wird der bewegte Avatar anderer Benutzer in Echtzeit angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f3f80-106">By the end of the tutorial, you will be able to run the app on multiple devices and have each user see the avatar of other users move in real-time.</span></span>

## <a name="objectives"></a><span data-ttu-id="f3f80-107">Ziele</span><span class="sxs-lookup"><span data-stu-id="f3f80-107">Objectives</span></span>

* <span data-ttu-id="f3f80-108">Erlernen des Verbindens mehrerer Benutzer in einer freigegebenen Umgebung</span><span class="sxs-lookup"><span data-stu-id="f3f80-108">Learn how to connect multiple users in a shared experience</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="f3f80-109">Vorbereiten der Szene</span><span class="sxs-lookup"><span data-stu-id="f3f80-109">Preparing the scene</span></span>

<span data-ttu-id="f3f80-110">In diesem Abschnitt bereiten Sie die Szene vor, indem Sie einige der Tutorial-Prefabs hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="f3f80-110">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="f3f80-111">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs**, klicken Sie auf die folgenden Prefabs, und ziehen Sie sie dann in das Hierarchiefenster, um sie Ihrer Szene hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="f3f80-111">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder, then click-and-drag the following prefabs into the Hierarchy window to add them to your scene:</span></span>

* <span data-ttu-id="f3f80-112">**NetworkLobby**-Prefab</span><span class="sxs-lookup"><span data-stu-id="f3f80-112">**NetworkLobby** prefab</span></span>
* <span data-ttu-id="f3f80-113">**SharedPlayground**-Prefab</span><span class="sxs-lookup"><span data-stu-id="f3f80-113">**SharedPlayground** prefab</span></span>

![Unity mit neu hinzugefügten, ausgewählten NetworkLobby- und SharedPlayground-Prefabs](images/mr-learning-sharing/sharing-03-section1-step1-1.png)

<span data-ttu-id="f3f80-115">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs**, klicken Sie auf das folgende Prefab, und ziehen Sie es in das Hierarchiefenster, um es Ihrer Szene hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="f3f80-115">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder, then click-and-drag the following prefab into the Hierarchy window to add it to your scene:</span></span>

* <span data-ttu-id="f3f80-116">**DebugWindow**-Prefab</span><span class="sxs-lookup"><span data-stu-id="f3f80-116">**DebugWindow** prefab</span></span>

![Unity mit neu hinzugefügtem, ausgewähltem DebugWindow-Prefab](images/mr-learning-sharing/sharing-03-section1-step1-2.png)

## <a name="creating-the-user-prefab"></a><span data-ttu-id="f3f80-118">Erstellen des Benutzerprefabs</span><span class="sxs-lookup"><span data-stu-id="f3f80-118">Creating the user prefab</span></span>

<span data-ttu-id="f3f80-119">In diesem Abschnitt erstellen Sie ein Prefab, das verwendet wird, um auf der freigegebenen Benutzeroberfläche die Benutzer darzustellen.</span><span class="sxs-lookup"><span data-stu-id="f3f80-119">In this section, you will create a prefab that will be used to represent the users in the shared experience.</span></span>

### <a name="1-create-and-configure-the-user"></a><span data-ttu-id="f3f80-120">1. Erstellen und Konfigurieren des Benutzers</span><span class="sxs-lookup"><span data-stu-id="f3f80-120">1. Create and configure the user</span></span>

<span data-ttu-id="f3f80-121">Klicken Sie im Hierarchiefenster mit der rechten Maustaste auf einen leeren Bereich, wählen Sie **Create Empty** (Leer erstellen) aus, um Ihrer Szene ein leeres Objekt hinzuzufügen, benennen Sie das Objekt **PhotonUser**, und konfigurieren Sie es folgendermaßen:</span><span class="sxs-lookup"><span data-stu-id="f3f80-121">In the Hierarchy window, right-click on an empty area and select **Create Empty** to add an empty object to your scene, name the object **PhotonUser**, and configure it as follows:</span></span>

* <span data-ttu-id="f3f80-122">Vergewissern Sie sich, dass die **Transformationsposition** auf X = 0, Y = 0, Z = 0 festgelegt ist:</span><span class="sxs-lookup"><span data-stu-id="f3f80-122">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0:</span></span>

![Unity mit neu erstelltem, ausgewähltem PhotonUser-Objekt](images/mr-learning-sharing/sharing-03-section2-step1-1.png)

<span data-ttu-id="f3f80-124">Wählen Sie im Hierarchiefenster das **PhotonUser**-Objekt aus, und verwenden Sie dann im Inspektor-Fenster die Schaltfläche **Add Component** (Komponente hinzufügen), um dem PhotonUser-Objekt die Komponente **Photon User (Script)** hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="f3f80-124">In the Hierarchy window, select the **PhotonUser** object, then in the Inspector window, use the **Add Component** button to add the **Photon User (Script)** component to the PhotonUser object:</span></span>

![Unity mit hinzugefügter Photon User-Komponente](images/mr-learning-sharing/sharing-03-section2-step1-2.png)

<span data-ttu-id="f3f80-126">Verwenden Sie im Inspektorfenster die Schaltfläche **Add Component** (Komponente hinzufügen), um dem PhotonUser-Objekt die Komponente **Generic Net Sync (Script)** hinzuzufügen, und konfigurieren Sie sie wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f3f80-126">In the Inspector window, use the **Add Component** button to add the **Generic Net Sync (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="f3f80-127">Aktivieren Sie das Kontrollkästchen **Is User** (Ist Benutzer)</span><span class="sxs-lookup"><span data-stu-id="f3f80-127">Check the **Is User** checkbox</span></span>

![Unity mit hinzugefügter und konfigurierter Generic Net Sync-Komponente](images/mr-learning-sharing/sharing-03-section2-step1-3.png)

<span data-ttu-id="f3f80-129">Verwenden Sie im Inspektorfenster die Schaltfläche **Add Component** (Komponente hinzufügen), um dem PhotonUser-Objekt die Komponente **Photon View (Script)** hinzuzufügen, und konfigurieren Sie sie wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f3f80-129">In the Inspector window, use the **Add Component** button to add the **Photon View (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="f3f80-130">Stellen Sie sicher, dass die Komponente **Generic Net Sync (Script)** dem Feld **Observed Components** (Beobachtete Komponenten) zugewiesen ist.</span><span class="sxs-lookup"><span data-stu-id="f3f80-130">Ensure that the **Observed Components** field is assigned with the **Generic Net Sync (Script)** component</span></span>

![Unity mit hinzugefügter und konfigurierter Photon View-Komponente](images/mr-learning-sharing/sharing-03-section2-step1-4.png)

### <a name="2-create-the-avatar"></a><span data-ttu-id="f3f80-132">2. Erstellen des Avatars</span><span class="sxs-lookup"><span data-stu-id="f3f80-132">2. Create the avatar</span></span>

<span data-ttu-id="f3f80-133">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK** > **StandardAssets** > **Materials**, um nach den MRTK-Materialien zu suchen.</span><span class="sxs-lookup"><span data-stu-id="f3f80-133">In the Project window, navigate to the **Assets** > **MRTK** > **StandardAssets** > **Materials** folder to locate the MRTK materials.</span></span>

<span data-ttu-id="f3f80-134">Klicken Sie dann im Hierarchiefenster mit der rechten Maustaste auf das **PhotonUser**-Objekt, wählen Sie **3D Object** > **Sphere** (3D-Objekt > Kugel) aus, um ein Kugelobjekt als untergeordnetes Objekt des PhotonUser-Objekts zu erstellen, und konfigurieren Sie es folgendermaßen:</span><span class="sxs-lookup"><span data-stu-id="f3f80-134">Then, in the Hierarchy window, right-click on the **PhotonUser** object and select **3D Object** > **Sphere** to create a sphere object as a child of the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="f3f80-135">Vergewissern Sie sich, dass die **Transformationsposition** auf X = 0, Y = 0, Z = 0 festgelegt ist</span><span class="sxs-lookup"><span data-stu-id="f3f80-135">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="f3f80-136">Ändern Sie den **Transformationsmaßstab** auf eine passende Größe beispielsweise X = 0,15, Y = 0,15, Z = 0,15</span><span class="sxs-lookup"><span data-stu-id="f3f80-136">Change the Transform **Scale** to a suitable size, for example, X = 0.15, Y = 0.15, Z = 0.15</span></span>
* <span data-ttu-id="f3f80-137">Weisen Sie dem Feld „MeshRenderer > Materials > **Element 0**“ das Material **MRTK_Standard_White** zu.</span><span class="sxs-lookup"><span data-stu-id="f3f80-137">To the MeshRenderer > Materials > **Element 0** field, assign the **MRTK_Standard_White** material</span></span>

![Unity mit neu erstellter und konfigurierter Avatar-Kugel](images/mr-learning-sharing/sharing-03-section2-step2-1.png)

### <a name="3-create-the-prefab"></a><span data-ttu-id="f3f80-139">3. Erstellen der Prefab</span><span class="sxs-lookup"><span data-stu-id="f3f80-139">3. Create the prefab</span></span>

<span data-ttu-id="f3f80-140">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources**:</span><span class="sxs-lookup"><span data-stu-id="f3f80-140">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder:</span></span>

![Unity-Projektfenster mit ausgewähltem Ordner „Ressource“](images/mr-learning-sharing/sharing-03-section2-step3-1.png)

<span data-ttu-id="f3f80-142">**Klicken und ziehen** Sie bei noch ausgewähltem Ordner „Resources“ das **PhotonUser**-Objekt aus dem Hierarchiefenster in den **Resources**-Ordner, um aus dem PhotonUser-Objekt ein Prefab zu machen:</span><span class="sxs-lookup"><span data-stu-id="f3f80-142">With the Resources folder still selected, **click-and-drag** the **PhotonUser** object from the Hierarchy window into the **Resources** folder to make the PhotonUser object a prefab:</span></span>

![Unity mit neu erstelltem, ausgewähltem PhotonUser-Prefab](images/mr-learning-sharing/sharing-03-section2-step3-2.png)

<span data-ttu-id="f3f80-144">Klicken Sie im Hierarchiefenster mit der rechten Maustaste auf das **PhotonUser**-Objekt, und wählen Sie **Löschen** aus, um es aus der Szene zu entfernen:</span><span class="sxs-lookup"><span data-stu-id="f3f80-144">In the Hierarchy window, right-click on the **PhotonUser** object and select **Delete** to remove it from the scene:</span></span>

![Unity mit neu erstelltem, aus der Szene entferntem PhotonUser-Prefab-Objekt](images/mr-learning-sharing/sharing-03-section2-step3-3.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a><span data-ttu-id="f3f80-146">Konfigurieren von PUN zum Instanziieren des Benutzerprefabs</span><span class="sxs-lookup"><span data-stu-id="f3f80-146">Configuring PUN to instantiate the user prefab</span></span>

<span data-ttu-id="f3f80-147">In diesem Abschnitt konfigurieren Sie das Projekt für die Verwendung des PhotonUser-Prefabs, das Sie im vorherigen Abschnitt erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="f3f80-147">In this section, you will configure the project to use the PhotonUser prefab you created in the previous section.</span></span>

<span data-ttu-id="f3f80-148">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources**.</span><span class="sxs-lookup"><span data-stu-id="f3f80-148">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder.</span></span>

<span data-ttu-id="f3f80-149">Klappen Sie im Hierarchiefenster das **NetworkLobby**-Objekt auf, wählen Sie das untergeordnete Objekt **NetworkRoom** aus, und suchen Sie dann im Inspektorfenster die Komponente **Photon Room (Script)** , um sie wie folgt zu konfigurieren:</span><span class="sxs-lookup"><span data-stu-id="f3f80-149">In the Hierarchy window, expand the **NetworkLobby** object and select the **NetworkRoom** child object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="f3f80-150">Weisen Sie das **PhotonUser**-Prefab aus dem Ordner „Resources“ dem **Photon User Prefab**-Feld zu</span><span class="sxs-lookup"><span data-stu-id="f3f80-150">To the **Photon User Prefab** field, assign the **PhotonUser** prefab from the Resources folder</span></span>

![Unity mit teilweise konfigurierter Photon Room-Komponente](images/mr-learning-sharing/sharing-03-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a><span data-ttu-id="f3f80-152">Ausprobieren der Benutzeroberfläche mit mehreren Benutzern</span><span class="sxs-lookup"><span data-stu-id="f3f80-152">Trying the experience with multiple users</span></span>

<span data-ttu-id="f3f80-153">Wenn Sie das Unity-Projekt jetzt für Ihr HoloLens-Gerät erstellen und bereitstellen und zurück in Unity in den Spielmodus wechseln, während die App auf Ihrem HoloLens-Gerät ausgeführt wird, sehen Sie, wie sich der HoloLens-Benutzeravatar bewegt, wenn Sie Ihren Kopf (HoloLens) bewegen:</span><span class="sxs-lookup"><span data-stu-id="f3f80-153">If you now build and deploy the Unity project to your HoloLens, then, back in Unity, enter Game mode while the app is running on your HoloLens, you will see the HoloLens user avatar move when you move your head (HoloLens) around:</span></span>

![Animation, die Unity mit vernetzten Benutzern zeigt.](images/mr-learning-sharing/sharing-03-section4-step1-1.gif)

> [!TIP]
> <span data-ttu-id="f3f80-155">Falls Sie eine Auffrischung zum Erstellen und Bereitstellen Ihres Unity-Projekts auf HoloLens 2 benötigen, lesen Sie die Anweisungen unter [Erstellen Ihrer App auf dem HoloLens 2-Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="f3f80-155">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

> [!CAUTION]
> <span data-ttu-id="f3f80-156">Die App muss eine Verbindung mit Photon herstellen, achten Sie also darauf, dass Ihr Computer/Gerät mit dem Internet verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="f3f80-156">The app needs to connect to Photon, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="f3f80-157">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="f3f80-157">Congratulations</span></span>

<span data-ttu-id="f3f80-158">Sie haben Ihr Projekt erfolgreich so konfiguriert, dass es mehreren Benutzern ermöglicht, Verbindungen mit der gleichen Benutzeroberfläche herzustellen und die Bewegungen der anderen Teilnehmer zu sehen.</span><span class="sxs-lookup"><span data-stu-id="f3f80-158">You have successfully configured your project to allow multiple users to connect to the same experience and see each other's movements.</span></span> <span data-ttu-id="f3f80-159">Im nächsten Tutorial implementieren Sie die Funktionalität zum Teilen der Bewegungen von Objekten unter mehreren Geräten.</span><span class="sxs-lookup"><span data-stu-id="f3f80-159">In the next tutorial, you will implement functionality so that the movements of objects are also shared across multiple devices.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f3f80-160">Nächstes Tutorial: 4. Freigeben von Objektbewegungen für mehrere Benutzer</span><span class="sxs-lookup"><span data-stu-id="f3f80-160">Next Tutorial: 4. Sharing object movements with multiple users</span></span>](mr-learning-sharing-04.md)
