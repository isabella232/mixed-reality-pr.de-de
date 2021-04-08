---
ms.openlocfilehash: 5d3f5b1dd0600404e534023e3bf7b6fcaf7fe8f6
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097895"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="0d432-101">Unity 2019/2020 und Windows-XR-Plugin</span><span class="sxs-lookup"><span data-stu-id="0d432-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="0d432-102">1. Klonen des Standardkonfigurationsprofils</span><span class="sxs-lookup"><span data-stu-id="0d432-102">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="0d432-103">Das Konfigurationsprofil ist das Profil der obersten Ebene.</span><span class="sxs-lookup"><span data-stu-id="0d432-103">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="0d432-104">Folglich müssen Sie, um andere Profile bearbeiten zu können, zuerst das Konfigurationsprofil klonen.</span><span class="sxs-lookup"><span data-stu-id="0d432-104">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="0d432-105">Wählen Sie im Hierarchiefenster das **MixedRealityToolkit**-Objekt aus, und überprüfen Sie dann im Inspektorfenster, ob das Konfigurationsprofil **MixedRealityToolkit** auf **DefaultXRSDKConfigurationProfile** festgelegt ist:</span><span class="sxs-lookup"><span data-stu-id="0d432-105">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, verify that the **MixedRealityToolkit** Configuration Profile is set to the **DefaultXRSDKConfigurationProfile**:</span></span>

![MixedRealityToolkit-Komponente von Unity mit ausgewähltem DefaultHoloLens2ConfigurationProfile](../images/mr-learning-base/base-03-section1-step1-1xrsdk.png)

<span data-ttu-id="0d432-107">Klicken Sie mit immer noch ausgewähltem **MixedRealityToolkit**-Objekt im Inspektor-Fenster auf die Schaltfläche **Copy & Customize** (Kopieren und Anpassen), um das Fenster „Clone Profile“ (Profil klonen) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="0d432-107">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![„Copy & Paste“-Schaltfläche der MixedRealityToolkit-Komponente von Unity](../images/mr-learning-base/base-03-section1-step1-2xrsdk.png)

<span data-ttu-id="0d432-109">Geben Sie im Fenster „Profil klonen“ einen passenden **Profilnamen** ein, beispielsweise _GettingStarted_XRSDKConfigurationProfile_, und klicken Sie dann auf die Schaltfläche **Clone** (Klonen), um eine bearbeitbare Kopie des **DefaultXRSDKConfigurationProfile** zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="0d432-109">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_XRSDKConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultXRSDKConfigurationProfile**:</span></span>

![Popupfenster „Konfigurationsprofil klonen“ des MixedRealityToolkit von Unity](../images/mr-learning-base/base-03-section1-step1-3xrsdk.png)

<span data-ttu-id="0d432-111">Das neu erstellte Konfigurationsprofil wird jetzt als Konfigurationsprofil für Ihre Szene zugewiesen:</span><span class="sxs-lookup"><span data-stu-id="0d432-111">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![MixedRealityToolkit-Komponente von Unity mit neu erstelltem, angewendetem benutzerdefiniertem HoloLens2ConfigurationProfile](../images/mr-learning-base/base-03-section1-step1-4xrsdk.png)

<span data-ttu-id="0d432-113">Wählen Sie im Unity-Menü **File** > **Save** (Datei > Speichern) aus, um Ihre Szene zu speichern.</span><span class="sxs-lookup"><span data-stu-id="0d432-113">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="0d432-114">Denken Sie daran, Ihre Arbeit während der Tutorials zu speichern.</span><span class="sxs-lookup"><span data-stu-id="0d432-114">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="0d432-115">2. Aktivieren des Systems für räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="0d432-115">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="0d432-116">Wählen Sie im Hierarchiefenster das **MixedRealityToolkit**-Objekt, dann im Inspektorfenster die Registerkarte **Spatial Awareness** (Räumliche Wahrnehmung) aus, und aktivieren Sie dann das Kontrollkästchen **Enable Spatial Awareness System** (System für räumliche Wahrnehmung aktivieren):</span><span class="sxs-lookup"><span data-stu-id="0d432-116">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![MixedRealityToolkit-Komponente von Unity mit aktiviertem Spatial Awareness-System](../images/mr-learning-base/base-03-section1-step2-1xrsdk.png)

> [!NOTE]
> <span data-ttu-id="0d432-118">Für zukünftige Projekte empfiehlt es sich, wenn Ihre App nicht auf die Umgebung reagieren oder mit dieser interagieren muss, „Spatial Awareness“ (räumliche Wahrnehmung) deaktiviert zu lassen, um die Leistungskosten zu senken.</span><span class="sxs-lookup"><span data-stu-id="0d432-118">For future projects, if your app doesn't need to respond to or interact with the environment, it's recommended to keep the spatial awareness turned off to reduce performance cost.</span></span>

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="0d432-119">3. Klonen Sie das Standardprofil des Systems für räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="0d432-119">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="0d432-120">Klicken Sie auf der Registerkarte **Spatial Awareness** (Räumliche Wahrnehmung) auf die Schaltfläche **Clone** (Klonen), um das Fenster „Clone Profile“ (Profil klonen) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="0d432-120">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![MixedRealityToolkit-Komponente von Unity mit ausgewählter Registerkarte „Spatial Awareness“ (räumliche Wahrnehmung)](../images/mr-learning-base/base-03-section1-step3-1xrsdk.png)

<span data-ttu-id="0d432-122">Geben Sie im Fenster „Profil klonen“ einen passenden **Profilnamen** ein, beispielsweise _GettingStarted_XRSDKSpatialAwarenessSystemProfile_, und klicken Sie dann auf die Schaltfläche **Clone** (Klonen), um eine bearbeitbare Kopie des **DefaultXRSDKSpatialAwarenessSystemProfile** zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="0d432-122">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_XRSDKSpatialAwarenessSystemProfile_, then click the **Clone** button to create an editable copy of the **DefaultXRSDKSpatialAwarenessSystemProfile**:</span></span>

![Popupfenster „Spatial Awareness-Systemprofil klonen“ des MixedRealityToolkit von Unity](../images/mr-learning-base/base-03-section1-step3-2xrsdk.png)

<span data-ttu-id="0d432-124">Das neu erstellte Profil des Systems für räumliche Wahrnehmung wird Ihrem Konfigurationsprofil nun automatisch zugewiesen:</span><span class="sxs-lookup"><span data-stu-id="0d432-124">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![MixedRealityToolkit-Komponente von Unity mit neu erstelltem, angewendetem benutzerdefiniertem MixedRealitySpatialAwarenessSystemProfile](../images/mr-learning-base/base-03-section1-step3-3xrsdk.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="0d432-126">4. Klonen des Standardprofils des Betrachters für räumliche Gittermodelle</span><span class="sxs-lookup"><span data-stu-id="0d432-126">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="0d432-127">Erweitern Sie bei immer noch ausgewählter Registerkarte **Spatial Awareness** (Räumliche Wahrnehmung) den Abschnitt **XR SDK Windows Mixed Reality Spatial Mesh Observer** (Betrachter für das räumliche Gittermodell von XR SDK Windows Mixed Reality), und klicken Sie dann auf die Schaltfläche **Clone** (Klonen), um das Clone Profile-Fenster (Profil klonen) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="0d432-127">With the **Spatial Awareness** tab still selected, expand the **XR SDK Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![MixedRealityToolkit-Komponente von Unity mit erweitertem Abschnitt „Windows Mixed Reality Raum-Mesh-Betrachter“](../images/mr-learning-base/base-03-section1-step4-1xrsdk.png)

<span data-ttu-id="0d432-129">Geben Sie im Fenster „Clone Profile“ (Profil klonen) einen passenden **Profilnamen** ein, beispielsweise _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, und klicken Sie dann auf die Schaltfläche **Clone** (Klonen), um eine bearbeitbare Kopie von **DefaultMixedRealitySpatialAwarenessMeshObserverProfile** zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="0d432-129">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![Popupfenster „Raum-Mesh-Betrachterprofil klonen“ des MixedRealityToolkit von Unity](../images/mr-learning-base/base-03-section1-step4-2xrsdk.png)

<span data-ttu-id="0d432-131">Das neu erstellte Profil des Betrachters für das räumliche Gittermodell wird jetzt automatisch Ihrem Profil für das räumliche Wahrnehmungssystem zugewiesen:</span><span class="sxs-lookup"><span data-stu-id="0d432-131">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![MixedRealityToolkit-Komponente von Unity mit neu erstelltem, angewendetem benutzerdefiniertem MixedRealitySpatialAwarenessMeshObserverProfile](../images/mr-learning-base/base-03-section1-step4-3xrsdk.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="0d432-133">5. Ändern der Sichtbarkeit des Gittermodells zur räumlichen Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="0d432-133">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="0d432-134">Ändern Sie in den **Spatial Mesh Observer Settings** (Einstellungen des Betrachters für das räumliche Gittermodell) die **Display Option** (Anzeigeoption) in **Occlusion** (Verdeckung), um das Gittermodell zur räumlichen Abbildung unsichtbar zu machen, ohne seine Funktion aufzuheben:</span><span class="sxs-lookup"><span data-stu-id="0d432-134">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![MixedRealityToolkit-Komponente von Unity mit auf „Occlusion“ festgelegter Anzeigeoption „Raum-Mesh-Betrachter“](../images/mr-learning-base/base-03-section1-step5-1xrsdk.png)

> [!NOTE]
> <span data-ttu-id="0d432-136">Das räumliche Gittermodell ist zwar nicht sichtbar, es ist aber trotzdem vorhanden und funktioniert.</span><span class="sxs-lookup"><span data-stu-id="0d432-136">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="0d432-137">Beispielsweise sind eventuelle Hologramme hinter dem Gittermodell für die räumliche Abbildung nicht sichtbar, ganz wie ein Hologramm hinter einer physischen Wand.</span><span class="sxs-lookup"><span data-stu-id="0d432-137">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="0d432-138">Sie haben soeben erfahren, wie Sie eine Einstellung im MRTK-Profil ändern können.</span><span class="sxs-lookup"><span data-stu-id="0d432-138">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="0d432-139">Wie Sie sehen können, müssen Sie zum Anpassen der MRTK-Einstellungen zuerst Kopien der Standardprofile erstellen.</span><span class="sxs-lookup"><span data-stu-id="0d432-139">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="0d432-140">Da die Standardprofile nicht bearbeitbar sind, stehen sie Ihnen jederzeit als Referenz zur Verfügung, wenn Sie zu den Standardeinstellungen zurückkehren möchten.</span><span class="sxs-lookup"><span data-stu-id="0d432-140">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="0d432-141">Weitere Informationen zu MRTK-Profilen und ihrer Architektur finden Sie im [MRTK-Leitfaden zur Profilkonfiguration](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) im [MRTK-Dokumentationsportal](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span><span class="sxs-lookup"><span data-stu-id="0d432-141">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span></span>

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="0d432-142">Unity 2020 und OpenXR</span><span class="sxs-lookup"><span data-stu-id="0d432-142">Unity 2020 + OpenXR</span></span>](#tab/openxr)

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="0d432-143">1. Klonen des Standardkonfigurationsprofils</span><span class="sxs-lookup"><span data-stu-id="0d432-143">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="0d432-144">Das Konfigurationsprofil ist das Profil der obersten Ebene.</span><span class="sxs-lookup"><span data-stu-id="0d432-144">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="0d432-145">Folglich müssen Sie, um andere Profile bearbeiten zu können, zuerst das Konfigurationsprofil klonen.</span><span class="sxs-lookup"><span data-stu-id="0d432-145">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="0d432-146">Wählen Sie im Hierarchiefenster das **MixedRealityToolkit**-Objekt aus, und überprüfen Sie dann im Inspektorfenster, ob das Konfigurationsprofil **MixedRealityToolkit** auf **DefaultOpenXRConfigurationProfile** festgelegt ist:</span><span class="sxs-lookup"><span data-stu-id="0d432-146">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, verify that the **MixedRealityToolkit** Configuration Profile is set to the **DefaultOpenXRConfigurationProfile**:</span></span>

![Unity: MixedRealityToolkit-Komponente mit ausgewähltem OpenXR-Standardprofil](../images/mr-learning-base/base-03-section1-step1-1openxr.png)

<span data-ttu-id="0d432-148">Klicken Sie mit immer noch ausgewähltem **MixedRealityToolkit**-Objekt im Inspektor-Fenster auf die Schaltfläche **Copy & Customize** (Kopieren und Anpassen), um das Fenster „Clone Profile“ (Profil klonen) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="0d432-148">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![Unity: Schaltfläche zum Kopieren und Anpassen für das OpenXR-Profil der MixedRealityToolkit-Komponente](../images/mr-learning-base/base-03-section1-step1-2openxr.png)

<span data-ttu-id="0d432-150">Geben Sie im Fenster „Profil klonen“ einen passenden **Profilnamen** ein, beispielsweise _GettingStarted_OpenXRConfigurationProfile_, und klicken Sie dann auf die Schaltfläche **Klonen**, um eine bearbeitbare Kopie des **DefaultOpenXRConfigurationProfile** zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="0d432-150">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_OpenXRConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultOpenXRConfigurationProfile**:</span></span>

![Unity: Popupfenster „Konfigurationsprofil klonen“ des MixedRealityToolkit für das OpenXR-Profil](../images/mr-learning-base/base-03-section1-step1-3openxr.png)

<span data-ttu-id="0d432-152">Das neu erstellte Konfigurationsprofil wird jetzt als Konfigurationsprofil für Ihre Szene zugewiesen:</span><span class="sxs-lookup"><span data-stu-id="0d432-152">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![Unity: MixedRealityToolkit-Komponente mit neu erstelltem benutzerdefinierten OpenXR angewendet](../images/mr-learning-base/base-03-section1-step1-4openxr.png)

<span data-ttu-id="0d432-154">Wählen Sie im Unity-Menü **File** > **Save** (Datei > Speichern) aus, um Ihre Szene zu speichern.</span><span class="sxs-lookup"><span data-stu-id="0d432-154">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="0d432-155">Denken Sie daran, Ihre Arbeit während der Tutorials zu speichern.</span><span class="sxs-lookup"><span data-stu-id="0d432-155">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="0d432-156">2. Aktivieren des Systems für räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="0d432-156">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="0d432-157">Wählen Sie im Hierarchiefenster das **MixedRealityToolkit**-Objekt, dann im Inspektorfenster die Registerkarte **Spatial Awareness** (Räumliche Wahrnehmung) aus, und aktivieren Sie dann das Kontrollkästchen **Enable Spatial Awareness System** (System für räumliche Wahrnehmung aktivieren):</span><span class="sxs-lookup"><span data-stu-id="0d432-157">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![MixedRealityToolkit-Komponente von Unity mit aktiviertem Spatial Awareness-System](../images/mr-learning-base/base-03-section1-step2-1xrsdk.png)

> [!NOTE]
> <span data-ttu-id="0d432-159">Für zukünftige Projekte empfiehlt es sich, wenn Ihre App nicht auf die Umgebung reagieren oder mit dieser interagieren muss, „Spatial Awareness“ (räumliche Wahrnehmung) deaktiviert zu lassen, um die Leistungskosten zu senken.</span><span class="sxs-lookup"><span data-stu-id="0d432-159">For future projects, if your app doesn't need to respond to or interact with the environment, it's recommended to keep the spatial awareness turned off to reduce performance cost.</span></span>

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="0d432-160">3. Klonen Sie das Standardprofil des Systems für räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="0d432-160">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="0d432-161">Klicken Sie auf der Registerkarte **Spatial Awareness** (Räumliche Wahrnehmung) auf die Schaltfläche **Clone** (Klonen), um das Fenster „Clone Profile“ (Profil klonen) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="0d432-161">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![MixedRealityToolkit-Komponente von Unity mit ausgewählter Registerkarte „Spatial Awareness“ (räumliche Wahrnehmung)](../images/mr-learning-base/base-03-section1-step3-1xrsdk.png)

<span data-ttu-id="0d432-163">Geben Sie im Fenster „Profil klonen“ einen passenden **Profilnamen** ein, beispielsweise „GettingStarted_OpenXRSpatialAwarenessSystemProfile“, und klicken Sie dann auf die Schaltfläche **Klonen**, um eine bearbeitbare Kopie des **DefaultXRSDKSpatialAwarenessSystemProfile** zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="0d432-163">In the Clone Profile window, enter a suitable **Profile Name**, for example, GettingStarted_OpenXRSpatialAwarenessSystemProfile, then click the **Clone** button to create an editable copy of the **DefaultXRSDKSpatialAwarenessSystemProfile**:</span></span>

![Popupfenster „Spatial Awareness-Systemprofil klonen“ des MixedRealityToolkit von Unity](../images/mr-learning-base/base-03-section1-step3-2xrsdk.png)

<span data-ttu-id="0d432-165">Das neu erstellte Profil des Systems für räumliche Wahrnehmung wird Ihrem Konfigurationsprofil nun automatisch zugewiesen:</span><span class="sxs-lookup"><span data-stu-id="0d432-165">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![MixedRealityToolkit-Komponente von Unity mit neu erstelltem, angewendetem benutzerdefiniertem MixedRealitySpatialAwarenessSystemProfile](../images/mr-learning-base/base-03-section1-step3-3xrsdk.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="0d432-167">4. Klonen des Standardprofils des Betrachters für räumliche Gittermodelle</span><span class="sxs-lookup"><span data-stu-id="0d432-167">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="0d432-168">Erweitern Sie bei immer noch ausgewählter Registerkarte **Spatial Awareness** (Räumliche Wahrnehmung) den Abschnitt **XR SDK Windows Mixed Reality Spatial Mesh Observer** (Betrachter für das räumliche Gittermodell von XR SDK Windows Mixed Reality), und klicken Sie dann auf die Schaltfläche **Clone** (Klonen), um das Clone Profile-Fenster (Profil klonen) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="0d432-168">With the **Spatial Awareness** tab still selected, expand the **XR SDK Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![MixedRealityToolkit-Komponente von Unity mit erweitertem Abschnitt „Windows Mixed Reality Raum-Mesh-Betrachter“](../images/mr-learning-base/base-03-section1-step4-1xrsdk.png)

<span data-ttu-id="0d432-170">Geben Sie im Fenster „Clone Profile“ (Profil klonen) einen passenden **Profilnamen** ein, beispielsweise _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, und klicken Sie dann auf die Schaltfläche **Clone** (Klonen), um eine bearbeitbare Kopie von **DefaultMixedRealitySpatialAwarenessMeshObserverProfile** zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="0d432-170">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![Popupfenster „Raum-Mesh-Betrachterprofil klonen“ des MixedRealityToolkit von Unity](../images/mr-learning-base/base-03-section1-step4-2xrsdk.png)

<span data-ttu-id="0d432-172">Das neu erstellte Profil des Betrachters für das räumliche Gittermodell wird jetzt automatisch Ihrem Profil für das räumliche Wahrnehmungssystem zugewiesen:</span><span class="sxs-lookup"><span data-stu-id="0d432-172">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![MixedRealityToolkit-Komponente von Unity mit neu erstelltem, angewendetem benutzerdefiniertem MixedRealitySpatialAwarenessMeshObserverProfile](../images/mr-learning-base/base-03-section1-step4-3xrsdk.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="0d432-174">5. Ändern der Sichtbarkeit des Gittermodells zur räumlichen Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="0d432-174">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="0d432-175">Ändern Sie in den **Spatial Mesh Observer Settings** (Einstellungen des Betrachters für das räumliche Gittermodell) die **Display Option** (Anzeigeoption) in **Occlusion** (Verdeckung), um das Gittermodell zur räumlichen Abbildung unsichtbar zu machen, ohne seine Funktion aufzuheben:</span><span class="sxs-lookup"><span data-stu-id="0d432-175">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![MixedRealityToolkit-Komponente von Unity mit auf „Occlusion“ festgelegter Anzeigeoption „Raum-Mesh-Betrachter“](../images/mr-learning-base/base-03-section1-step5-1xrsdk.png)

> [!NOTE]
> <span data-ttu-id="0d432-177">Das räumliche Gittermodell ist zwar nicht sichtbar, es ist aber trotzdem vorhanden und funktioniert.</span><span class="sxs-lookup"><span data-stu-id="0d432-177">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="0d432-178">Beispielsweise sind eventuelle Hologramme hinter dem Gittermodell für die räumliche Abbildung nicht sichtbar, ganz wie ein Hologramm hinter einer physischen Wand.</span><span class="sxs-lookup"><span data-stu-id="0d432-178">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="0d432-179">Sie haben soeben erfahren, wie Sie eine Einstellung im MRTK-Profil ändern können.</span><span class="sxs-lookup"><span data-stu-id="0d432-179">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="0d432-180">Wie Sie sehen können, müssen Sie zum Anpassen der MRTK-Einstellungen zuerst Kopien der Standardprofile erstellen.</span><span class="sxs-lookup"><span data-stu-id="0d432-180">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="0d432-181">Da die Standardprofile nicht bearbeitbar sind, stehen sie Ihnen jederzeit als Referenz zur Verfügung, wenn Sie zu den Standardeinstellungen zurückkehren möchten.</span><span class="sxs-lookup"><span data-stu-id="0d432-181">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="0d432-182">Weitere Informationen zu MRTK-Profilen und ihrer Architektur finden Sie im [MRTK-Leitfaden zur Profilkonfiguration](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) im [MRTK-Dokumentationsportal](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span><span class="sxs-lookup"><span data-stu-id="0d432-182">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span></span>


# <a name="legacy-wsa"></a>[<span data-ttu-id="0d432-183">Legacy-WSA</span><span class="sxs-lookup"><span data-stu-id="0d432-183">Legacy WSA</span></span>](#tab/wsa)

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="0d432-184">1. Klonen des Standardkonfigurationsprofils</span><span class="sxs-lookup"><span data-stu-id="0d432-184">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="0d432-185">Das Konfigurationsprofil ist das Profil der obersten Ebene.</span><span class="sxs-lookup"><span data-stu-id="0d432-185">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="0d432-186">Folglich müssen Sie, um andere Profile bearbeiten zu können, zuerst das Konfigurationsprofil klonen.</span><span class="sxs-lookup"><span data-stu-id="0d432-186">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="0d432-187">Wählen Sie im Hierarchiefenster das **MixedRealityToolkit**-Objekt aus, und ändern Sie dann im Inspektorfenster das Konfigurationsprofil des **Mixed Reality-Toolkits** in **DefaultHoloLens2ConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="0d432-187">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, change the **MixedRealityToolkit** Configuration Profile to the **DefaultHoloLens2ConfigurationProfile**:</span></span>

![MixedRealityToolkit-Komponente von Unity mit ausgewähltem DefaultHoloLens2ConfigurationProfile](../images/mr-learning-base/base-03-section1-step1-1.png)

<span data-ttu-id="0d432-189">Klicken Sie mit immer noch ausgewähltem **MixedRealityToolkit**-Objekt im Inspektor-Fenster auf die Schaltfläche **Copy & Customize** (Kopieren und Anpassen), um das Fenster „Clone Profile“ (Profil klonen) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="0d432-189">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![„Copy & Paste“-Schaltfläche der MixedRealityToolkit-Komponente von Unity](../images/mr-learning-base/base-03-section1-step1-2.png)

<span data-ttu-id="0d432-191">Geben Sie im Fenster „Clone Profile“ (Profil klonen) einen passenden **Profilnamen** ein, beispielsweise _GettingStarted_HoloLens2ConfigurationProfile_, und klicken Sie dann auf die Schaltfläche **Clone** (Klonen), um eine bearbeitbare Kopie des **DefaultHololens2ConfigurationProfile** zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="0d432-191">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_HoloLens2ConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![Popupfenster „Konfigurationsprofil klonen“ des MixedRealityToolkit von Unity](../images/mr-learning-base/base-03-section1-step1-3.png)

<span data-ttu-id="0d432-193">Das neu erstellte Konfigurationsprofil wird jetzt als Konfigurationsprofil für Ihre Szene zugewiesen:</span><span class="sxs-lookup"><span data-stu-id="0d432-193">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![MixedRealityToolkit-Komponente von Unity mit neu erstelltem, angewendetem benutzerdefiniertem HoloLens2ConfigurationProfile](../images/mr-learning-base/base-03-section1-step1-4.png)

<span data-ttu-id="0d432-195">Wählen Sie im Unity-Menü **File** > **Save** (Datei > Speichern) aus, um Ihre Szene zu speichern.</span><span class="sxs-lookup"><span data-stu-id="0d432-195">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="0d432-196">Denken Sie daran, Ihre Arbeit während der Tutorials zu speichern.</span><span class="sxs-lookup"><span data-stu-id="0d432-196">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="0d432-197">2. Aktivieren des Systems für räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="0d432-197">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="0d432-198">Wählen Sie im Hierarchiefenster das **MixedRealityToolkit**-Objekt, dann im Inspektorfenster die Registerkarte **Spatial Awareness** (Räumliche Wahrnehmung) aus, und aktivieren Sie dann das Kontrollkästchen **Enable Spatial Awareness System** (System für räumliche Wahrnehmung aktivieren):</span><span class="sxs-lookup"><span data-stu-id="0d432-198">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![MixedRealityToolkit-Komponente von Unity mit aktiviertem Spatial Awareness-System](../images/mr-learning-base/base-03-section1-step2-1.png)

> [!NOTE]
> <span data-ttu-id="0d432-200">Für zukünftige Projekte empfiehlt es sich, wenn Ihre App nicht auf die Umgebung reagieren oder mit dieser interagieren muss, „Spatial Awareness“ (räumliche Wahrnehmung) deaktiviert zu lassen, um die Leistungskosten zu senken.</span><span class="sxs-lookup"><span data-stu-id="0d432-200">For future projects, if your app doesn't need to respond to or interact with the environment, it's recommended to keep the spatial awareness turned off to reduce performance cost.</span></span>

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="0d432-201">3. Klonen Sie das Standardprofil des Systems für räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="0d432-201">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="0d432-202">Klicken Sie auf der Registerkarte **Spatial Awareness** (Räumliche Wahrnehmung) auf die Schaltfläche **Clone** (Klonen), um das Fenster „Clone Profile“ (Profil klonen) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="0d432-202">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![MixedRealityToolkit-Komponente von Unity mit ausgewählter Registerkarte „Spatial Awareness“ (räumliche Wahrnehmung)](../images/mr-learning-base/base-03-section1-step3-1.png)

<span data-ttu-id="0d432-204">Geben Sie im Fenster „Clone Profile“ (Profil klonen) einen passenden **Profilnamen** ein, beispielsweise _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, und klicken Sie dann auf die Schaltfläche **Clone** (Klonen), um eine bearbeitbare Kopie des **DefaultMixedRealitySpatialAwarenessSystemProfile** zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="0d432-204">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![Popupfenster „Spatial Awareness-Systemprofil klonen“ des MixedRealityToolkit von Unity](../images/mr-learning-base/base-03-section1-step3-2.png)

<span data-ttu-id="0d432-206">Das neu erstellte Profil des Systems für räumliche Wahrnehmung wird Ihrem Konfigurationsprofil nun automatisch zugewiesen:</span><span class="sxs-lookup"><span data-stu-id="0d432-206">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![MixedRealityToolkit-Komponente von Unity mit neu erstelltem, angewendetem benutzerdefiniertem MixedRealitySpatialAwarenessSystemProfile](../images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="0d432-208">4. Klonen des Standardprofils des Betrachters für räumliche Gittermodelle</span><span class="sxs-lookup"><span data-stu-id="0d432-208">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="0d432-209">Erweitern Sie bei immer noch ausgewählter Registerkarte **Spatial Awareness** (Räumliche Wahrnehmung) den Abschnitt **Windows Mixed Reality Spatial Mesh Observer** (Betrachter für das räumliche Gittermodell von Windows Mixed Reality), und klicken Sie dann auf die Schaltfläche **Clone** (Klonen), um das Clone Profile-Fenster (Profil klonen) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="0d432-209">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![MixedRealityToolkit-Komponente von Unity mit erweitertem Abschnitt „Windows Mixed Reality Raum-Mesh-Betrachter“](../images/mr-learning-base/base-03-section1-step4-1.png)

<span data-ttu-id="0d432-211">Geben Sie im Fenster „Clone Profile“ (Profil klonen) einen passenden **Profilnamen** ein, beispielsweise _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, und klicken Sie dann auf die Schaltfläche **Clone** (Klonen), um eine bearbeitbare Kopie von **DefaultMixedRealitySpatialAwarenessMeshObserverProfile** zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="0d432-211">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![Popupfenster „Raum-Mesh-Betrachterprofil klonen“ des MixedRealityToolkit von Unity](../images/mr-learning-base/base-03-section1-step4-2.png)

<span data-ttu-id="0d432-213">Das neu erstellte Profil des Betrachters für das räumliche Gittermodell wird jetzt automatisch Ihrem Profil für das räumliche Wahrnehmungssystem zugewiesen:</span><span class="sxs-lookup"><span data-stu-id="0d432-213">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![MixedRealityToolkit-Komponente von Unity mit neu erstelltem, angewendetem benutzerdefiniertem MixedRealitySpatialAwarenessMeshObserverProfile](../images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="0d432-215">5. Ändern der Sichtbarkeit des Gittermodells zur räumlichen Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="0d432-215">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="0d432-216">Ändern Sie in den **Spatial Mesh Observer Settings** (Einstellungen des Betrachters für das räumliche Gittermodell) die **Display Option** (Anzeigeoption) in **Occlusion** (Verdeckung), um das Gittermodell zur räumlichen Abbildung unsichtbar zu machen, ohne seine Funktion aufzuheben:</span><span class="sxs-lookup"><span data-stu-id="0d432-216">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![MixedRealityToolkit-Komponente von Unity mit auf „Occlusion“ festgelegter Anzeigeoption „Raum-Mesh-Betrachter“](../images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="0d432-218">Das räumliche Gittermodell ist zwar nicht sichtbar, es ist aber trotzdem vorhanden und funktioniert.</span><span class="sxs-lookup"><span data-stu-id="0d432-218">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="0d432-219">Beispielsweise sind eventuelle Hologramme hinter dem Gittermodell für die räumliche Abbildung nicht sichtbar, ganz wie ein Hologramm hinter einer physischen Wand.</span><span class="sxs-lookup"><span data-stu-id="0d432-219">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="0d432-220">Sie haben soeben erfahren, wie Sie eine Einstellung im MRTK-Profil ändern können.</span><span class="sxs-lookup"><span data-stu-id="0d432-220">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="0d432-221">Wie Sie sehen können, müssen Sie zum Anpassen der MRTK-Einstellungen zuerst Kopien der Standardprofile erstellen.</span><span class="sxs-lookup"><span data-stu-id="0d432-221">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="0d432-222">Da die Standardprofile nicht bearbeitbar sind, stehen sie Ihnen jederzeit als Referenz zur Verfügung, wenn Sie zu den Standardeinstellungen zurückkehren möchten.</span><span class="sxs-lookup"><span data-stu-id="0d432-222">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="0d432-223">Weitere Informationen zu MRTK-Profilen und ihrer Architektur finden Sie im [MRTK-Leitfaden zur Profilkonfiguration](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) im [MRTK-Dokumentationsportal](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span><span class="sxs-lookup"><span data-stu-id="0d432-223">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span></span>
