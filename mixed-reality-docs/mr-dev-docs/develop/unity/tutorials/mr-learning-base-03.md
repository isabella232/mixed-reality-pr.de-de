---
title: 'Tutorials zu den ersten Schritten: 3 Konfigurieren der MRTK-Profile'
description: In diesem Kurs erfahren Sie, wie Sie die MRTK-Profile (Mixed Reality Toolkit) konfigurieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, MRTK, Mixed Reality Toolkit, UWP, räumliche Wahrnehmung
ms.localizationpriority: high
ms.openlocfilehash: 0a8beb647516ebcb5bc07cb58d0193e8fe71e9fc
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2021
ms.locfileid: "101760016"
---
# <a name="3-configuring-the-mrtk-profiles"></a><span data-ttu-id="86aae-105">3. Konfigurieren der MRTK-Profile</span><span class="sxs-lookup"><span data-stu-id="86aae-105">3. Configuring the MRTK profiles</span></span>

## <a name="overview"></a><span data-ttu-id="86aae-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="86aae-106">Overview</span></span>

<span data-ttu-id="86aae-107">In diesem Tutorial erfahren Sie, wie die MRTK-Profile angepasst und konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="86aae-107">In this tutorial, you will learn how to customize and configure the MRTK profiles.</span></span>

<span data-ttu-id="86aae-108">Bei den <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/profiles/profiles.md" target="_blank">MRTK-Profilen</a> handelt es sich um eine Struktur geschachtelter Profile, aus denen die Konfigurationsinformationen für die Initialisierung der MRTK-Systeme und -Funktionen bestehen.</span><span class="sxs-lookup"><span data-stu-id="86aae-108">The <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/profiles/profiles.md" target="_blank">MRTK profiles</a> is a tree of nested profiles that make up the configuration information for how the MRTK systems and features should be initialized.</span></span> <span data-ttu-id="86aae-109">Das Profil der obersten Ebene, das Konfigurationsprofil, enthält für jedes der primären Kernsysteme geschachtelte Profile.</span><span class="sxs-lookup"><span data-stu-id="86aae-109">The top-level profile, the Configuration Profile, contains nested profiles for each of the primary core systems.</span></span> <span data-ttu-id="86aae-110">Jedes geschachtelte Profil ist so konzipiert, dass das Verhalten des entsprechenden Systems konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="86aae-110">Each nested profile is designed to configure the behavior of their corresponding system.</span></span>

<span data-ttu-id="86aae-111">Dieses Beispiel veranschaulicht insbesondere, wie das Gittermodell zur räumlichen Wahrnehmung durch Ändern der Einstellungen des Betrachters für räumliche Gittermodelle ausgeblendet wird.</span><span class="sxs-lookup"><span data-stu-id="86aae-111">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="86aae-112">Jedoch können Sie dieselben Prinzipien befolgen, um beliebige Einstellungen oder Werte in den MRTK-Profilen anzupassen.</span><span class="sxs-lookup"><span data-stu-id="86aae-112">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

<span data-ttu-id="86aae-113">Wie Sie bei der Bereitstellung Ihres Projekts in Ihrer HoloLens 2 während des [vorherigen Tutorials](mr-learning-base-02.md#congratulations) gesehen haben, ist das <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/spatial-awareness/spatial-awareness-getting-started.md" target="_blank">Spatial Awareness</a>-Gittermodell (für räumliche Wahrnehmung) eine Sammlung von Gittermodellen, die die Geometrie der Umgebung darstellen.</span><span class="sxs-lookup"><span data-stu-id="86aae-113">As you experienced when you deployed your project to your HoloLens 2 during the [previous tutorial](mr-learning-base-02.md#congratulations), the <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/spatial-awareness/spatial-awareness-getting-started.md" target="_blank">Spatial Awareness</a> mesh is a collection of meshes representing the geometry of the environment.</span></span> <span data-ttu-id="86aae-114">Es ist eine hilfreiche Visualisierung für die anfängliche Anzeige, die jedoch in der Regel deaktiviert ist, um die visuelle Ablenkung und die zusätzliche Leistungseinbuße durch die Aktivierung zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="86aae-114">It's a helpful visualization to see initially but it's typically turned off to avoid the visual distraction and the additional performance hit of having it on.</span></span>

## <a name="objectives"></a><span data-ttu-id="86aae-115">Ziele</span><span class="sxs-lookup"><span data-stu-id="86aae-115">Objectives</span></span>

* <span data-ttu-id="86aae-116">Erfahren, wie MRTK-Profile angepasst und konfiguriert werden</span><span class="sxs-lookup"><span data-stu-id="86aae-116">Learn how to customize and configure MRTK profiles</span></span>
* <span data-ttu-id="86aae-117">Ausblenden des Gittermodells für räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="86aae-117">Hide the spatial awareness mesh</span></span>

## <a name="changing-the-spatial-awareness-display-option"></a><span data-ttu-id="86aae-118">Ändern der Anzeigeoptionen für räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="86aae-118">Changing the Spatial Awareness Display Option</span></span>

<span data-ttu-id="86aae-119">Dies sind die wichtigsten Schritte, die Sie ausführen, um das Gittermodell zur räumlichen Wahrnehmung auszublenden:</span><span class="sxs-lookup"><span data-stu-id="86aae-119">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="86aae-120">Klonen des Standardkonfigurationsprofils</span><span class="sxs-lookup"><span data-stu-id="86aae-120">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="86aae-121">Aktivieren des Systems für räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="86aae-121">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="86aae-122">Klonen des Standardprofils des Systems für räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="86aae-122">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="86aae-123">Klonen des Standardprofils des Betrachters für räumliche Gittermodelle</span><span class="sxs-lookup"><span data-stu-id="86aae-123">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="86aae-124">Ändern der Sichtbarkeit des Gittermodells zur räumlichen Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="86aae-124">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="86aae-125">Standardmäßig können die MRTK-Profile nicht bearbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="86aae-125">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="86aae-126">Es handelt sich um Standardprofilvorlagen, die Sie zuerst klonen müssen, um sie bearbeiten zu können.</span><span class="sxs-lookup"><span data-stu-id="86aae-126">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="86aae-127">Es gibt mehrere verschachtelte Profilebenen.</span><span class="sxs-lookup"><span data-stu-id="86aae-127">There are several nested layers of profiles.</span></span> <span data-ttu-id="86aae-128">Es ist daher gängige Praxis, mehrere Profile zu klonen und zu bearbeiten, wenn Einstellungen konfiguriert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="86aae-128">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="86aae-129">1. Klonen des Standardkonfigurationsprofils</span><span class="sxs-lookup"><span data-stu-id="86aae-129">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="86aae-130">Das Konfigurationsprofil ist das Profil der obersten Ebene.</span><span class="sxs-lookup"><span data-stu-id="86aae-130">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="86aae-131">Folglich müssen Sie, um andere Profile bearbeiten zu können, zuerst das Konfigurationsprofil klonen.</span><span class="sxs-lookup"><span data-stu-id="86aae-131">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="86aae-132">Wählen Sie im Hierarchiefenster das **MixedRealityToolkit**-Objekt aus, und ändern Sie dann im Inspektorfenster das Konfigurationsprofil des **Mixed Reality-Toolkits** in **DefaultHoloLens2ConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="86aae-132">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, change the **MixedRealityToolkit** Configuration Profile to the **DefaultHoloLens2ConfigurationProfile**:</span></span>

![MixedRealityToolkit-Komponente von Unity mit ausgewähltem DefaultHoloLens2ConfigurationProfile](images/mr-learning-base/base-03-section1-step1-1.png)

<span data-ttu-id="86aae-134">Klicken Sie mit immer noch ausgewähltem **MixedRealityToolkit**-Objekt im Inspektor-Fenster auf die Schaltfläche **Copy & Customize** (Kopieren und Anpassen), um das Fenster „Clone Profile“ (Profil klonen) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="86aae-134">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![„Copy & Paste“-Schaltfläche der MixedRealityToolkit-Komponente von Unity](images/mr-learning-base/base-03-section1-step1-2.png)

<span data-ttu-id="86aae-136">Geben Sie im Fenster „Clone Profile“ (Profil klonen) einen passenden **Profilnamen** ein, beispielsweise _GettingStarted_HoloLens2ConfigurationProfile_, und klicken Sie dann auf die Schaltfläche **Clone** (Klonen), um eine bearbeitbare Kopie des **DefaultHololens2ConfigurationProfile** zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="86aae-136">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_HoloLens2ConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![Popupfenster „Konfigurationsprofil klonen“ des MixedRealityToolkit von Unity](images/mr-learning-base/base-03-section1-step1-3.png)

<span data-ttu-id="86aae-138">Das neu erstellte Konfigurationsprofil wird jetzt als Konfigurationsprofil für Ihre Szene zugewiesen:</span><span class="sxs-lookup"><span data-stu-id="86aae-138">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![MixedRealityToolkit-Komponente von Unity mit neu erstelltem, angewendetem benutzerdefiniertem HoloLens2ConfigurationProfile](images/mr-learning-base/base-03-section1-step1-4.png)

<span data-ttu-id="86aae-140">Wählen Sie im Unity-Menü **File** > **Save** (Datei > Speichern) aus, um Ihre Szene zu speichern.</span><span class="sxs-lookup"><span data-stu-id="86aae-140">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="86aae-141">Denken Sie daran, Ihre Arbeit während der Tutorials zu speichern.</span><span class="sxs-lookup"><span data-stu-id="86aae-141">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="86aae-142">2. Aktivieren des Systems für räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="86aae-142">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="86aae-143">Wählen Sie im Hierarchiefenster das **MixedRealityToolkit**-Objekt, dann im Inspektorfenster die Registerkarte **Spatial Awareness** (Räumliche Wahrnehmung) aus, und aktivieren Sie dann das Kontrollkästchen **Enable Spatial Awareness System** (System für räumliche Wahrnehmung aktivieren):</span><span class="sxs-lookup"><span data-stu-id="86aae-143">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![MixedRealityToolkit-Komponente von Unity mit aktiviertem Spatial Awareness-System](images/mr-learning-base/base-03-section1-step2-1.png)

> [!NOTE]
> <span data-ttu-id="86aae-145">Für zukünftige Projekte empfiehlt es sich, wenn Ihre App nicht auf die Umgebung reagieren oder mit dieser interagieren muss, „Spatial Awareness“ (räumliche Wahrnehmung) deaktiviert zu lassen, um die Leistungskosten zu senken.</span><span class="sxs-lookup"><span data-stu-id="86aae-145">For future projects, if your app doesn't need to respond to or interact with the environment, it's recommended to keep the spatial awareness turned off to reduce performance cost.</span></span>

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="86aae-146">3. Klonen Sie das Standardprofil des Systems für räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="86aae-146">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="86aae-147">Klicken Sie auf der Registerkarte **Spatial Awareness** (Räumliche Wahrnehmung) auf die Schaltfläche **Clone** (Klonen), um das Fenster „Clone Profile“ (Profil klonen) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="86aae-147">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![MixedRealityToolkit-Komponente von Unity mit ausgewählter Registerkarte „Spatial Awareness“ (räumliche Wahrnehmung)](images/mr-learning-base/base-03-section1-step3-1.png)

<span data-ttu-id="86aae-149">Geben Sie im Fenster „Clone Profile“ (Profil klonen) einen passenden **Profilnamen** ein, beispielsweise _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, und klicken Sie dann auf die Schaltfläche **Clone** (Klonen), um eine bearbeitbare Kopie des **DefaultMixedRealitySpatialAwarenessSystemProfile** zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="86aae-149">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![Popupfenster „Spatial Awareness-Systemprofil klonen“ des MixedRealityToolkit von Unity](images/mr-learning-base/base-03-section1-step3-2.png)

<span data-ttu-id="86aae-151">Das neu erstellte Profil des Systems für räumliche Wahrnehmung wird Ihrem Konfigurationsprofil nun automatisch zugewiesen:</span><span class="sxs-lookup"><span data-stu-id="86aae-151">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![MixedRealityToolkit-Komponente von Unity mit neu erstelltem, angewendetem benutzerdefiniertem MixedRealitySpatialAwarenessSystemProfile](images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="86aae-153">4. Klonen des Standardprofils des Betrachters für räumliche Gittermodelle</span><span class="sxs-lookup"><span data-stu-id="86aae-153">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="86aae-154">Erweitern Sie bei immer noch ausgewählter Registerkarte **Spatial Awareness** (Räumliche Wahrnehmung) den Abschnitt **Windows Mixed Reality Spatial Mesh Observer** (Betrachter für das räumliche Gittermodell von Windows Mixed Reality), und klicken Sie dann auf die Schaltfläche **Clone** (Klonen), um das Clone Profile-Fenster (Profil klonen) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="86aae-154">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![MixedRealityToolkit-Komponente von Unity mit erweitertem Abschnitt „Windows Mixed Reality Raum-Mesh-Betrachter“](images/mr-learning-base/base-03-section1-step4-1.png)

<span data-ttu-id="86aae-156">Geben Sie im Fenster „Clone Profile“ (Profil klonen) einen passenden **Profilnamen** ein, beispielsweise _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, und klicken Sie dann auf die Schaltfläche **Clone** (Klonen), um eine bearbeitbare Kopie von **DefaultMixedRealitySpatialAwarenessMeshObserverProfile** zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="86aae-156">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![Popupfenster „Raum-Mesh-Betrachterprofil klonen“ des MixedRealityToolkit von Unity](images/mr-learning-base/base-03-section1-step4-2.png)

<span data-ttu-id="86aae-158">Das neu erstellte Profil des Betrachters für das räumliche Gittermodell wird jetzt automatisch Ihrem Profil für das räumliche Wahrnehmungssystem zugewiesen:</span><span class="sxs-lookup"><span data-stu-id="86aae-158">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![MixedRealityToolkit-Komponente von Unity mit neu erstelltem, angewendetem benutzerdefiniertem MixedRealitySpatialAwarenessMeshObserverProfile](images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="86aae-160">5. Ändern der Sichtbarkeit des Gittermodells zur räumlichen Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="86aae-160">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="86aae-161">Ändern Sie in den **Spatial Mesh Observer Settings** (Einstellungen des Betrachters für das räumliche Gittermodell) die **Display Option** (Anzeigeoption) in **Occlusion** (Verdeckung), um das Gittermodell zur räumlichen Abbildung unsichtbar zu machen, ohne seine Funktion aufzuheben:</span><span class="sxs-lookup"><span data-stu-id="86aae-161">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![MixedRealityToolkit-Komponente von Unity mit auf „Occlusion“ festgelegter Anzeigeoption „Raum-Mesh-Betrachter“](images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="86aae-163">Das räumliche Gittermodell ist zwar nicht sichtbar, es ist aber trotzdem vorhanden und funktioniert.</span><span class="sxs-lookup"><span data-stu-id="86aae-163">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="86aae-164">Beispielsweise sind eventuelle Hologramme hinter dem Gittermodell für die räumliche Abbildung nicht sichtbar, ganz wie ein Hologramm hinter einer physischen Wand.</span><span class="sxs-lookup"><span data-stu-id="86aae-164">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="86aae-165">Sie haben soeben erfahren, wie Sie eine Einstellung im MRTK-Profil ändern können.</span><span class="sxs-lookup"><span data-stu-id="86aae-165">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="86aae-166">Wie Sie sehen können, müssen Sie zum Anpassen der MRTK-Einstellungen zuerst Kopien der Standardprofile erstellen.</span><span class="sxs-lookup"><span data-stu-id="86aae-166">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="86aae-167">Da die Standardprofile nicht bearbeitbar sind, stehen sie Ihnen jederzeit als Referenz zur Verfügung, wenn Sie zu den Standardeinstellungen zurückkehren möchten.</span><span class="sxs-lookup"><span data-stu-id="86aae-167">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="86aae-168">Weitere Informationen zu MRTK-Profilen und ihrer Architektur finden Sie im [MRTK-Leitfaden zur Profilkonfiguration](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/configuration/mixed-reality-configuration-guide.md) im [MRTK-Dokumentationsportal](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs).</span><span class="sxs-lookup"><span data-stu-id="86aae-168">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/configuration/mixed-reality-configuration-guide.md) in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs).</span></span>

## <a name="congratulations"></a><span data-ttu-id="86aae-169">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="86aae-169">Congratulations</span></span>

<span data-ttu-id="86aae-170">In diesem Tutorial haben Sie gelernt, wie Sie MRTK-Profile und Einstellungen klonen, anpassen und konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="86aae-170">In this tutorial, you learned how to clone, customize, and configure MRTK profiles and settings.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="86aae-171">Nächstes Tutorial: 4. Positionieren von Objekten in der Szene</span><span class="sxs-lookup"><span data-stu-id="86aae-171">Next Tutorial: 4. Positioning objects in the scene</span></span>](mr-learning-base-04.md)
