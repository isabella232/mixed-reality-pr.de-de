---
title: Erste Schritte mit Azure Spatial Anchors
description: In diesem Kurs erfahren Sie, wie Sie Azure Spatial Anchors zum Verankern von Objekten in einer Mixed Reality-Anwendung verwenden.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, MRTK, Mixed Reality Toolkit, UWP, Azure Spatial Anchors
ms.localizationpriority: high
ms.openlocfilehash: 9c3ae23c39bf4d0b32d8a5d82716f93fee48b6db
ms.sourcegitcommit: fd1964ec6c645e8088ec120661f73739bb7775a9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/13/2021
ms.locfileid: "113656643"
---
# <a name="2-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="2b0cd-104">2. Erste Schritte mit Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="2b0cd-104">2. Getting started with Azure Spatial Anchors</span></span>

<span data-ttu-id="2b0cd-105">In diesem Tutorial erkunden Sie die verschiedenen Schritte, die zum Starten und Beenden einer Azure Spatial Anchors-Sitzung und zum Erstellen, Hochladen und Herunterladen von Azure Spatial Anchors auf einem Einzelgerät erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="2b0cd-105">In this tutorial, you will explore the various steps required to start and stop an Azure Spatial Anchors session and to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

## <a name="objectives"></a><span data-ttu-id="2b0cd-106">Ziele</span><span class="sxs-lookup"><span data-stu-id="2b0cd-106">Objectives</span></span>

* <span data-ttu-id="2b0cd-107">Erlernen der Grundlagen des Entwickelns mit Azure Spatial Anchors für HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="2b0cd-107">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="2b0cd-108">Erfahren, wie Raumanker erstellt und aus Azure abgerufen werden</span><span class="sxs-lookup"><span data-stu-id="2b0cd-108">Learn how to create spatial anchors and fetch them from Azure</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="2b0cd-109">Erstellen und Vorbereiten des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="2b0cd-109">Creating and preparing the Unity project</span></span>

<span data-ttu-id="2b0cd-110">In diesem Abschnitt erstellen Sie ein neues Unity-Projekt und bereiten es für die MRTK-Entwicklung vor.</span><span class="sxs-lookup"><span data-stu-id="2b0cd-110">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="2b0cd-111">Befolgen Sie zunächst die Anweisungen unter [Initialisieren Ihres Projekts und Bereitstellen Ihrer ersten Anwendung](mr-learning-base-02.md) – jedoch ohne die Anweisungen zum [Erstellen Ihrer Anwendung auf Ihrem Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2) – die die folgenden Schritte beinhalten:</span><span class="sxs-lookup"><span data-stu-id="2b0cd-111">First, follow the [Initializing your project and deploying your first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="2b0cd-112">[Erstellen eines neuen Unity-Projekts](mr-learning-base-02.md#creating-the-unity-project), das mit einem passenden Namen bezeichnet wird, beispielsweise *MRTK-Tutorials*</span><span class="sxs-lookup"><span data-stu-id="2b0cd-112">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
2. [<span data-ttu-id="2b0cd-113">Wechseln der Buildplattform</span><span class="sxs-lookup"><span data-stu-id="2b0cd-113">Switching the build platform</span></span>](mr-learning-base-02.md#switching-the-build-platform)
3. [<span data-ttu-id="2b0cd-114">Importieren der TextMeshPro Essential-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="2b0cd-114">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="2b0cd-115">Importieren des Mixed Reality Toolkits und Konfigurieren des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="2b0cd-115">Importing the Mixed Reality Toolkit and Configuring the Unity project</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. <span data-ttu-id="2b0cd-116">[Erstellen und Konfigurieren der Szene](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) und Bezeichnen der Szene mit einem passenden Namen, z. B. *AzureSpatialAnchors*</span><span class="sxs-lookup"><span data-stu-id="2b0cd-116">[Creating and configuring the scene](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

<span data-ttu-id="2b0cd-117">Befolgen Sie dann die Anweisungen unter [Ändern der Anzeigeoption der räumlichen Wahrnehmung](mr-learning-base-03.md#changing-the-spatial-awareness-display-option), um sicherzustellen, dass das MRTK-Konfigurationsprofil für Ihre Szene **DefaultHoloLens2ConfigurationProfile** ist, und ändern Sie die Anzeigeoptionen für das Gittermodell zur räumlichen Wahrnehmung in **Occlusion** (Verdeckung).</span><span class="sxs-lookup"><span data-stu-id="2b0cd-117">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to ensure the MRTK configuration profile for your scene is **DefaultHoloLens2ConfigurationProfile**  and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="installing-inbuilt-unity-packages-and-importing-the-tutorial-assets"></a><span data-ttu-id="2b0cd-118">Installieren von integrierten Unity-Paketen und Importieren der Tutorialressourcen</span><span class="sxs-lookup"><span data-stu-id="2b0cd-118">Installing inbuilt Unity packages and Importing the tutorial assets</span></span>

[!INCLUDE[](includes/installing-packages-for-asa.md)]

## <a name="preparing-the-scene"></a><span data-ttu-id="2b0cd-119">Vorbereiten der Szene</span><span class="sxs-lookup"><span data-stu-id="2b0cd-119">Preparing the scene</span></span>

<span data-ttu-id="2b0cd-120">In diesem Abschnitt bereiten Sie die Szene vor, indem Sie einige der Tutorial-Prefabs hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="2b0cd-120">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="2b0cd-121">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs**, klicken Sie auf die folgenden Prefabs, und ziehen Sie sie in das Hierarchiefenster, um sie Ihrer Szene hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="2b0cd-121">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder, then click-and-drag the following prefabs into the Hierarchy window to add them to your scene:</span></span>

* <span data-ttu-id="2b0cd-122">**ButtonParent**-Prefabs</span><span class="sxs-lookup"><span data-stu-id="2b0cd-122">**ButtonParent** prefabs</span></span>
* <span data-ttu-id="2b0cd-123">**DebugWindow**-Prefabs</span><span class="sxs-lookup"><span data-stu-id="2b0cd-123">**DebugWindow** prefabs</span></span>
* <span data-ttu-id="2b0cd-124">**Instructions**-Prefabs</span><span class="sxs-lookup"><span data-stu-id="2b0cd-124">**Instructions** prefabs</span></span>
* <span data-ttu-id="2b0cd-125">**ParentAnchor**-Prefabs</span><span class="sxs-lookup"><span data-stu-id="2b0cd-125">**ParentAnchor** prefabs</span></span>

![Unity mit neu hinzugefügten, ausgewählten Prefabs](images/mr-learning-asa/asa-02-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="2b0cd-127">Wenn Sie die großen Symbole in Ihrer Szene, beispielsweise die mit großen Rahmen umgebenen ‚T‘-Symbole, irritierend finden, können Sie diese ausblenden, indem Sie <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">die Gizmos umschalten</a> (in die Aus-Position), wie in der Abbildung oben dargestellt.</span><span class="sxs-lookup"><span data-stu-id="2b0cd-127">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position, as shown in the image above.</span></span>

<span data-ttu-id="2b0cd-128">Wählen Sie im Hierarchiefenster das **MixedRealityToolkit**-Objekt aus, und verwenden Sie die Schaltfläche **Add Component** (Komponente hinzufügen) im Inspektorfenster, um die folgenden Komponenten hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="2b0cd-128">Select **MixedRealityToolkit** object in the Hierarchy window, use the **Add Component** button in the Inspector window to add the following components:</span></span>

* <span data-ttu-id="2b0cd-129">AR Anchor Manager (Script)</span><span class="sxs-lookup"><span data-stu-id="2b0cd-129">AR Anchor Manager (Script)</span></span>
* <span data-ttu-id="2b0cd-130">DisableDiagnosticsSystem (Script)</span><span class="sxs-lookup"><span data-stu-id="2b0cd-130">DisableDiagnosticsSystem (Script)</span></span>

![<span data-ttu-id="2b0cd-131">Unity-Objekt „MixedRealityToolkit“ mit hinzugefügten AR Anchor Manager- und DisableDiagnosticsSystem-Komponenten</span><span class="sxs-lookup"><span data-stu-id="2b0cd-131">Unity MixedRealityToolkit object with AR Anchor Manager and DisableDiagnosticsSystem components added</span></span> ](images/mr-learning-asa/asa-02-section4-step1-2.PNG)

> [!WARNING]
> <span data-ttu-id="2b0cd-132">Es gibt ein bekanntes Problem mit ASA v2.9.0 und v2.10.0-preview.1, bei dem zwei zusätzliche Objekte in der Szene platziert werden müssen.</span><span class="sxs-lookup"><span data-stu-id="2b0cd-132">There is a known issue with ASA v2.9.0 and v2.10.0-preview.1 that requires two additional objects to be placed in the scene.</span></span> <span data-ttu-id="2b0cd-133">Verwenden Sie die Schaltfläche **Add Component** (Komponente hinzufügen) im Inspektorfenster, um dem **MixedRealityToolkit**-Objekt einen AR-Kamera-Manager (Skript) und eine AR-Sitzung (Skript) hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="2b0cd-133">Please use the **Add Component** button in the inspector window to add an AR Camera Manager (Script) and an AR Session (Script) to the **MixedRealityToolkit** object.</span></span> <span data-ttu-id="2b0cd-134">Stellen Sie sicher, dass Sie die Kamera deaktivieren, die beim Hinzufügen des AR-Kamera-Managers (Skript) automatisch erstellt wird, indem Sie das Kontrollkästchen neben dem Camera-Objekt im Inspektorfenster deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="2b0cd-134">Be sure to disable the Camera that is created automatically while adding the AR Camera Manager (Script) by unchecking the checkbox next to the Camera object in the inspector window.</span></span> <span data-ttu-id="2b0cd-135">Dieses Problem wird im vollständigen Release von ASA v2.10.0 behoben.</span><span class="sxs-lookup"><span data-stu-id="2b0cd-135">This issue will be addressed in the full release of ASA v2.10.0.</span></span>
>

> [!NOTE]
> <span data-ttu-id="2b0cd-136">Wenn Sie die Komponente „AR Anchor Manager (Script)“ hinzufügen, wird die Komponente „AR Session Origin (Script)“ automatisch hinzugefügt, da sie von der Komponente „AR Anchor Manager (Script)“ benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="2b0cd-136">When you add the AR Anchor Manager (Script) component, the AR Session Origin (Script) component is automatically added because it is required by the AR Anchor Manager (Script) component.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="2b0cd-137">Konfigurieren der Schaltflächen zum Betreiben der Szene</span><span class="sxs-lookup"><span data-stu-id="2b0cd-137">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="2b0cd-138">In diesem Abschnitt fügen Sie Skripts in die Szene ein, um eine Reihe von Schaltflächenereignissen zu erstellen, mit denen die Grundlagen des Verhaltens beider lokaler Anker und der Azure Spatial Anchors in einer Anwendung veranschaulicht werden.</span><span class="sxs-lookup"><span data-stu-id="2b0cd-138">In this section, you will add scripts to the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an app.</span></span>

<span data-ttu-id="2b0cd-139">Klappen Sie im Hierarchiefenster das **ButtonParent**-Objekt auf, und wählen Sie im Inspektorfenster das erste untergeordnete Objekt mit dem Namen **StartAzureSession** aus. Konfigurieren Sie dann das **On Click ()** -Ereignis der **Button Config Helper (Script)** -Komponente wie folgt:</span><span class="sxs-lookup"><span data-stu-id="2b0cd-139">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession**, in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="2b0cd-140">Weisen Sie das **ParentAnchor**-Objekt als Listener für das „On Click ()“-Ereignis zu, indem Sie es aus dem Hierarchiefenster auf das **None (Object)** -Feld (Ohne (Objekt)) ziehen.</span><span class="sxs-lookup"><span data-stu-id="2b0cd-140">Assign the **ParentAnchor** object as a listener for the On Click () event by dragging it from the Hierarchy window into the **None (Object)** field</span></span>
* <span data-ttu-id="2b0cd-141">Wählen Sie in der Dropdownliste **No Function** (Keine Funktion) **AnchorModuleScript** > **StartAzureSession ()** aus, um diese Funktion als die beim Auslösen des Ereignisses auszuführende Aktion festzulegen.</span><span class="sxs-lookup"><span data-stu-id="2b0cd-141">From the **No Function** dropdown, select **AnchorModuleScript** > **StartAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity mit konfiguriertem OnClick-Ereignis für die StartAzureSession-Schaltfläche](images/mr-learning-asa/asa-02-section5-step1-1.png)

<span data-ttu-id="2b0cd-143">Wählen Sie im Hierarchiefenster die nächste Schaltfläche mit dem Namen **StopAzureSession** aus, und konfigurieren Sie dann im Inspektorfenster das **On Click ()** -Ereignis der **Button Config Helper (Script)** -Komponente wie folgt:</span><span class="sxs-lookup"><span data-stu-id="2b0cd-143">In the Hierarchy window, select the next button named **StopAzureSession**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="2b0cd-144">Weisen Sie das **ParentAnchor**-Objekt als Listener für das „On Click ()“-Ereignis zu, indem Sie es aus dem Hierarchiefenster auf das **None (Object)** -Feld (Ohne (Objekt)) ziehen.</span><span class="sxs-lookup"><span data-stu-id="2b0cd-144">Assign the **ParentAnchor** object as a listener for the On Click () event by dragging it from the Hierarchy window into the **None (Object)** field</span></span>
* <span data-ttu-id="2b0cd-145">Wählen Sie in der Dropdownliste **No Function** (Keine Funktion) **AnchorModuleScript** > **StopAzureSession ()** aus, um diese Funktion als die beim Auslösen des Ereignisses auszuführende Aktion festzulegen.</span><span class="sxs-lookup"><span data-stu-id="2b0cd-145">From the **No Function** dropdown, select **AnchorModuleScript** > **StopAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity mit konfiguriertem OnClick-Ereignis für die StopAzureSession-Schaltfläche](images/mr-learning-asa/asa-02-section5-step1-2.png)

<span data-ttu-id="2b0cd-147">Wählen Sie im Hierarchiefenster die nächste Schaltfläche mit dem Namen **CreateAzureAnchor** aus, und konfigurieren Sie dann im Inspektorfenster das **On Click ()** -Ereignis der **Button Config Helper (Script)** -Komponente wie folgt:</span><span class="sxs-lookup"><span data-stu-id="2b0cd-147">In the Hierarchy window, select the next button named **CreateAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="2b0cd-148">Weisen Sie das **ParentAnchor**-Objekt als Listener für das „On Click ()“-Ereignis zu, indem Sie es aus dem Hierarchiefenster auf das **None (Object)** -Feld (Ohne (Objekt)) ziehen.</span><span class="sxs-lookup"><span data-stu-id="2b0cd-148">Assign the **ParentAnchor** object as a listener for the On Click () event by dragging it from the Hierarchy window into the **None (Object)** field</span></span>
* <span data-ttu-id="2b0cd-149">Wählen Sie in der Dropdownliste **No Function** (Keine Funktion) **AnchorModuleScript** > **CreateAzureAnchor ()** aus, um diese Funktion als die beim Auslösen des Ereignisses auszuführende Aktion festzulegen.</span><span class="sxs-lookup"><span data-stu-id="2b0cd-149">From the **No Function** dropdown, select **AnchorModuleScript** > **CreateAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="2b0cd-150">Weisen Sie das **ParentAnchor**-Objekt dem leeren Feld **None (Game Object)** (Ohne (Spielobjekt)) zu, um es als Argument für die Funktion „CreateAzureAnchor ()“ festzulegen</span><span class="sxs-lookup"><span data-stu-id="2b0cd-150">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the CreateAzureAnchor () function</span></span>

![Unity mit konfiguriertem OnClick-Ereignis für die CreateAzureAnchor-Schaltfläche](images/mr-learning-asa/asa-02-section5-step1-3.png)

<span data-ttu-id="2b0cd-152">Wählen Sie im Hierarchiefenster die nächste Schaltfläche mit dem Namen **RemoveLocalAnchor** aus, und konfigurieren Sie dann im Inspektorfenster das **On Click ()** -Ereignis der **Button Config Helper (Script)** -Komponente wie folgt:</span><span class="sxs-lookup"><span data-stu-id="2b0cd-152">In the Hierarchy window, select the next button named **RemoveLocalAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="2b0cd-153">Weisen Sie das **ParentAnchor**-Objekt als Listener für das „On Click ()“-Ereignis zu, indem Sie es aus dem Hierarchiefenster auf das **None (Object)** -Feld (Ohne (Objekt)) ziehen.</span><span class="sxs-lookup"><span data-stu-id="2b0cd-153">Assign the **ParentAnchor** object as a listener for the On Click () event by dragging it from the Hierarchy window into the **None (Object)** field</span></span>
* <span data-ttu-id="2b0cd-154">Wählen Sie in der Dropdownliste **No Function** (Keine Funktion) **AnchorModuleScript** > **RemoveLocalAnchor ()** aus, um diese Funktion als die beim Auslösen des Ereignisses auszuführende Aktion festzulegen.</span><span class="sxs-lookup"><span data-stu-id="2b0cd-154">From the **No Function** dropdown, select **AnchorModuleScript** > **RemoveLocalAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="2b0cd-155">Weisen Sie das **ParentAnchor**-Objekt dem leeren Feld **None (Game Object)** (Ohne (Spielobjekt)) zu, um es als Argument für die Funktion „RemoveLocalAnchor ()“ festzulegen</span><span class="sxs-lookup"><span data-stu-id="2b0cd-155">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the RemoveLocalAnchor () function</span></span>

![Unity mit konfiguriertem OnClick-Ereignis für die RemoveLocalAnchor-Schaltfläche](images/mr-learning-asa/asa-02-section5-step1-4.png)

<span data-ttu-id="2b0cd-157">Wählen Sie im Hierarchiefenster die nächste Schaltfläche mit dem Namen **FindAzureAnchor** aus, und konfigurieren Sie dann im Inspektorfenster das **On Click ()** -Ereignis der **Button Config Helper (Script)** -Komponente wie folgt:</span><span class="sxs-lookup"><span data-stu-id="2b0cd-157">In the Hierarchy window, select the next button named **FindAzureAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="2b0cd-158">Weisen Sie das **ParentAnchor**-Objekt als Listener für das „On Click ()“-Ereignis zu, indem Sie es aus dem Hierarchiefenster auf das **None (Object)** -Feld (Ohne (Objekt)) ziehen.</span><span class="sxs-lookup"><span data-stu-id="2b0cd-158">Assign the **ParentAnchor** object as a listener for the On Click () event by dragging it from the Hierarchy window into the **None (Object)** field</span></span>
* <span data-ttu-id="2b0cd-159">Wählen Sie in der Dropdownliste **No Function** (Keine Funktion) **AnchorModuleScript** > **FindAzureAnchor ()** aus, um diese Funktion als die beim Auslösen des Ereignisses auszuführende Aktion festzulegen.</span><span class="sxs-lookup"><span data-stu-id="2b0cd-159">From the **No Function** dropdown, select **AnchorModuleScript** > **FindAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity mit konfiguriertem OnClick-Ereignis für die FindAzureAnchor-Schaltfläche](images/mr-learning-asa/asa-02-section5-step1-5.png)

<span data-ttu-id="2b0cd-161">Wählen Sie im Hierarchiefenster die nächste Schaltfläche mit dem Namen **DeleteAzureAnchor** aus, und konfigurieren Sie dann im Inspektorfenster das **On Click ()** -Ereignis der **Button Config Helper (Script)** -Komponente wie folgt:</span><span class="sxs-lookup"><span data-stu-id="2b0cd-161">In the Hierarchy window, select the next button named **DeleteAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="2b0cd-162">Weisen Sie das **ParentAnchor**-Objekt als Listener für das „On Click ()“-Ereignis zu, indem Sie es aus dem Hierarchiefenster auf das **None (Object)** -Feld (Ohne (Objekt)) ziehen.</span><span class="sxs-lookup"><span data-stu-id="2b0cd-162">Assign the **ParentAnchor** object as a listener for the On Click () event by dragging it from the Hierarchy window into the **None (Object)** field</span></span>
* <span data-ttu-id="2b0cd-163">Wählen Sie in der Dropdownliste **No Function** (Keine Funktion) **AnchorModuleScript** > **DeleteAzureAnchor ()** aus, um diese Funktion als die beim Auslösen des Ereignisses auszuführende Aktion festzulegen.</span><span class="sxs-lookup"><span data-stu-id="2b0cd-163">From the **No Function** dropdown, select **AnchorModuleScript** > **DeleteAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity mit konfiguriertem OnClick-Ereignis für die DeleteAzureAnchor-Schaltfläche](images/mr-learning-asa/asa-02-section5-step1-6.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a><span data-ttu-id="2b0cd-165">Verbinden der Szene mit der Azure-Ressource</span><span class="sxs-lookup"><span data-stu-id="2b0cd-165">Connecting the scene to the Azure resource</span></span>

<span data-ttu-id="2b0cd-166">Wählen Sie im Hierarchiefenster das **ParentAnchor**-Objekt aus, und suchen Sie dann im Inspektorfenster die Komponente **Spatial Anchor Manager (Script)** .</span><span class="sxs-lookup"><span data-stu-id="2b0cd-166">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, locate the **Spatial Anchor Manager (Script)** component.</span></span> <span data-ttu-id="2b0cd-167">Konfigurieren Sie den Abschnitt **Credentials** (Anmeldeinformationen) mit den Anmeldeinformationen aus dem Azure Spatial Anchors-Konto, das Sie im Rahmen der [Voraussetzungen](mr-learning-asa-01.md#prerequisites) für diese Tutorialreihe erstellt haben:</span><span class="sxs-lookup"><span data-stu-id="2b0cd-167">Configure the **Credentials** section with the credentials from the Azure Spatial Anchors account created as part of the [Prerequisites](mr-learning-asa-01.md#prerequisites) for this tutorial series:</span></span>

* <span data-ttu-id="2b0cd-168">Fügen Sie in das Feld **Spatial Anchors Account ID** die **Konto-ID** Ihres Azure Spatial Anchors-Kontos ein</span><span class="sxs-lookup"><span data-stu-id="2b0cd-168">In the **Spatial Anchors Account ID** field, paste the **Account ID** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="2b0cd-169">Fügen Sie in das Feld **Spatial Anchors Account Key** (Spatial Anchors-Kontoschlüssel) den primären oder sekundären **Zugriffsschlüssel** aus Ihrem Azure Spatial Anchors-Konto ein</span><span class="sxs-lookup"><span data-stu-id="2b0cd-169">In the **Spatial Anchors Account Key** field, paste the primary or secondary **Access Key** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="2b0cd-170">Fügen Sie im Feld **Spatial Anchors Account Domain** die **Kontodomäne** Ihres Azure Spatial Anchors-Kontos ein</span><span class="sxs-lookup"><span data-stu-id="2b0cd-170">In the **Spatial Anchors Account Domain** field, paste the **Account Domain** from your Azure Spatial Anchors account</span></span>

![Unity mit konfiguriertem Spatial Anchor-Manager](images/mr-learning-asa/asa-02-section6-step1-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="2b0cd-172">Testen der grundlegenden Verhaltensweisen von Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="2b0cd-172">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="2b0cd-173">Azure Spatial Anchors können nicht in Unity ausgeführt werden, daher müssen Sie das Projekt erstellen und die App auf Ihrem Gerät bereitstellen, um die Azure Spatial Anchors-Funktionalität zu testen.</span><span class="sxs-lookup"><span data-stu-id="2b0cd-173">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to build the project and deploy the app to your device.</span></span>

> [!TIP]
> <span data-ttu-id="2b0cd-174">Falls Sie eine Auffrischung zum Erstellen und Bereitstellen Ihres Unity-Projekts auf HoloLens 2 benötigen, lesen Sie die Anweisungen unter [Erstellen Ihrer Anwendung für das HoloLens 2-Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="2b0cd-174">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your application to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

<span data-ttu-id="2b0cd-175">Wenn die App auf Ihrem Gerät ausgeführt wird, befolgen Sie die Anweisungen auf dem Bildschirm, die im Anweisungsbereich des Azure Spatial Anchor-Tutorials angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="2b0cd-175">When the app runs on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

1. <span data-ttu-id="2b0cd-176">Bewegen Sie den Würfel an einen anderen Ort</span><span class="sxs-lookup"><span data-stu-id="2b0cd-176">Move the cube to a different location</span></span>
2. <span data-ttu-id="2b0cd-177">Starten Sie die Azure-Sitzung</span><span class="sxs-lookup"><span data-stu-id="2b0cd-177">Start Azure Session</span></span>
3. <span data-ttu-id="2b0cd-178">Erstellen Sie einen Azure-Anker (erstellt einen Anker an der Position des Würfels).</span><span class="sxs-lookup"><span data-stu-id="2b0cd-178">Create Azure Anchor (creates an anchor at the location of the cube).</span></span>
4. <span data-ttu-id="2b0cd-179">Beenden Sie die Azure-Sitzung</span><span class="sxs-lookup"><span data-stu-id="2b0cd-179">Stop Azure Session</span></span>
5. <span data-ttu-id="2b0cd-180">Entfernen Sie den lokalen Anker (ermöglicht es dem Benutzer, den Würfel zu bewegen)</span><span class="sxs-lookup"><span data-stu-id="2b0cd-180">Remove Local Anchor (allows the user to move the cube)</span></span>
6. <span data-ttu-id="2b0cd-181">Bewegen Sie den Würfel an eine andere Stelle</span><span class="sxs-lookup"><span data-stu-id="2b0cd-181">Move the cube somewhere else</span></span>
7. <span data-ttu-id="2b0cd-182">Starten Sie die Azure-Sitzung</span><span class="sxs-lookup"><span data-stu-id="2b0cd-182">Start Azure Session</span></span>
8. <span data-ttu-id="2b0cd-183">Suchen Sie einen Azure Anchor (positioniert den Würfel am Ort aus Schritt 3)</span><span class="sxs-lookup"><span data-stu-id="2b0cd-183">Find Azure Anchor (positions the cube at the location from step 3)</span></span>
9. <span data-ttu-id="2b0cd-184">Löschen Sie den Azure Anchor</span><span class="sxs-lookup"><span data-stu-id="2b0cd-184">Delete Azure Anchor</span></span>
10. <span data-ttu-id="2b0cd-185">Beenden Sie die Azure-Sitzung</span><span class="sxs-lookup"><span data-stu-id="2b0cd-185">Stop Azure session</span></span>

![Unity mit ausgewähltem Instructions-Objekt](images/mr-learning-asa/asa-02-section7-step1-1.png)

> [!CAUTION]
> <span data-ttu-id="2b0cd-187">Azure Spatial Anchors verwendet das Internet zum Speichern und Laden der Ankerdaten, achten Sie also darauf, dass Ihr Gerät über eine Internetverbindung verfügt.</span><span class="sxs-lookup"><span data-stu-id="2b0cd-187">Azure Spatial Anchors uses the internet to save and load the anchor data, so make sure your device is connected to the internet.</span></span>

## <a name="anchoring-an-experience"></a><span data-ttu-id="2b0cd-188">Verankern eines Benutzererlebnisses</span><span class="sxs-lookup"><span data-stu-id="2b0cd-188">Anchoring an experience</span></span>

<span data-ttu-id="2b0cd-189">In den vorherigen Abschnitten haben Sie die Grundlagen von Azure Spatial Anchors kennengelernt.</span><span class="sxs-lookup"><span data-stu-id="2b0cd-189">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="2b0cd-190">Wir haben einen Würfel verwendet, um das übergeordnete Spielobjekt mit dem angefügten Anker dazustellen und zu visualisieren.</span><span class="sxs-lookup"><span data-stu-id="2b0cd-190">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="2b0cd-191">In diesem Abschnitt erfahren Sie, wie Sie ein gesamtes Benutzererlebnis verankern, indem Sie es als untergeordnetes Objekt des ParentAnchor-Objekts platzieren.</span><span class="sxs-lookup"><span data-stu-id="2b0cd-191">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

<span data-ttu-id="2b0cd-192">Wählen Sie im Hierarchiefenster das **ParentAnchor**-Objekt aus, und konfigurieren Sie dann im Inspektorfenster die **Transform**-Komponenten (Transformieren) wie folgt:</span><span class="sxs-lookup"><span data-stu-id="2b0cd-192">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, configure the **Transform** components as follows:</span></span>

* <span data-ttu-id="2b0cd-193">Ändern Sie die **Scale X** (X-Skalierung) in 1,1</span><span class="sxs-lookup"><span data-stu-id="2b0cd-193">Change **Scale X** to 1.1</span></span>
* <span data-ttu-id="2b0cd-194">Ändern Sie die **Scale Z** (Z-Skalierung) in 1,1</span><span class="sxs-lookup"><span data-stu-id="2b0cd-194">Change **Scale Z** to 1.1</span></span>

![Unity mit ausgewähltem, positioniertem und skaliertem ParentAnchor-Objekt](images/mr-learning-asa/asa-02-section8-step1-1.png)

<span data-ttu-id="2b0cd-196">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **Rover** (Medienobjekte > MRTK.Tutorials.GettingStarted > Prefabs > Rover), klicken Sie dann auf das Prefab **RoverExplorer_Complete**, und ziehen Sie es auf das Hierarchiefenster, um es der Szene hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="2b0cd-196">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **Rover** folder, then click-and-drag the **RoverExplorer_Complete** prefab into the Hierarchy window to add it to the scene:</span></span>

![Unity mit neu hinzugefügtem, ausgewähltem RoverExplorer_Complete-Prefab](images/mr-learning-asa/asa-02-section8-step1-2.png)

<span data-ttu-id="2b0cd-198">Ziehen Sie das noch im Hierarchiefenster ausgewählte neu hinzugefügte RoverModule_Complete-Objekt auf das **ParentAnchor**-Objekt, um es zu einem untergeordneten Objekt des ParentAnchor-Objekts zu machen:</span><span class="sxs-lookup"><span data-stu-id="2b0cd-198">With the newly added RoverModule_Complete object still selected in the Hierarchy window, drag it onto the **ParentAnchor** object to make it a child of the ParentAnchor object:</span></span>

![Unity mit RoverExplorer_Complete-Objekt, das als untergeordnetes Element von ParentAnchor festgelegt ist](images/mr-learning-asa/asa-02-section8-step1-3.png)

<span data-ttu-id="2b0cd-200">Wenn Sie das Projekt jetzt neu erstellen und die App auf Ihrem Gerät bereitstellen, können Sie jetzt die gesamte Rover Explorer-Erfahrung neu positionieren, indem Sie den in der Größe veränderten Würfel bewegen.</span><span class="sxs-lookup"><span data-stu-id="2b0cd-200">If you now rebuild the project and deploy the app to your device, you can now reposition the entire Rover Explorer experience by moving the resized cube.</span></span>

> [!TIP]
> <span data-ttu-id="2b0cd-201">Es gibt eine Vielzahl von Benutzererlebnisabläufen für die Neupositionierung von Erlebnissen, einschließlich der Verwendung eines Neupositionierungsobjekts (wie des Würfels, der in diesem Tutorial verwendet wird), der Verwendung einer Schaltfläche zum Umschalten eines Begrenzungssteuerelements, das das Erlebnis umgibt, der Verwendung von Gizmos für Position und Drehung und mehr.</span><span class="sxs-lookup"><span data-stu-id="2b0cd-201">A variety of user experience flows for repositioning experiences, including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounds control that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="2b0cd-202">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="2b0cd-202">Congratulations</span></span>

<span data-ttu-id="2b0cd-203">In diesem Tutorial haben Sie die Grundlagen von Azure Spatial Anchors kennengelernt.</span><span class="sxs-lookup"><span data-stu-id="2b0cd-203">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="2b0cd-204">Dieses Tutorial hat Ihnen verschiedene Schaltflächen an die Hand gegeben, um die verschiedenen Schritte zu erkunden, die zum Starten und Beenden einer Azure-Spatial Anchors-Sitzung erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="2b0cd-204">This tutorial provided you with several buttons to let you explore the various steps required to start and stop an Azure Spatial Anchors session.</span></span> <span data-ttu-id="2b0cd-205">Ferner zum Erstellen, Hochladen und Herunterladen von Azure Spatial Anchors auf einem Einzelgerät.</span><span class="sxs-lookup"><span data-stu-id="2b0cd-205">Also, to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="2b0cd-206">Im nächsten Tutorial erfahren Sie, wie Azure Anchor-IDs für den Abruf auf Ihrer HoloLens 2 gespeichert werden, auch nach einem Neustart der App, und wie Anchor-IDs zwischen mehreren Geräten übertragen werden, um räumliche Ausrichtung zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="2b0cd-206">In the next tutorial, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the app is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2b0cd-207">Nächstes Tutorial: 3. Speichern, Abrufen und Freigeben von Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="2b0cd-207">Next Tutorial: 3. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mr-learning-asa-03.md)
