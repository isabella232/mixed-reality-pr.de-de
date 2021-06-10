---
title: Oculus Quest MRTK
description: Dokumentation zum Konfigurieren für Oculus Quest im MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Oculus Quest,
ms.openlocfilehash: 6b9c3a8f51388785f685714ef02be680bb98e14c
ms.sourcegitcommit: 2f69fb62eb81f91e655d7b55306b0550a1162496
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/10/2021
ms.locfileid: "111908394"
---
# <a name="building-and-deploying-mrtk-to-oculus-quest-using-the-xr-sdk-pipeline"></a><span data-ttu-id="a410b-104">Erstellen und Bereitstellen von MRTK für Oculus Quest mithilfe der XR SDK-Pipeline</span><span class="sxs-lookup"><span data-stu-id="a410b-104">Building and deploying MRTK to Oculus Quest using the XR SDK pipeline</span></span>

<span data-ttu-id="a410b-105">Eine [Oculus Quest](https://www.oculus.com/quest/) ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="a410b-105">An [Oculus Quest](https://www.oculus.com/quest/) is required.</span></span>

<span data-ttu-id="a410b-106">Die MRTK-Unterstützung für Oculus Quest wird über zwei verschiedene Quellen bereitgestellt: die XR SDK-Pipeline von Unity und das Oculus Integration Unity-Paket.</span><span class="sxs-lookup"><span data-stu-id="a410b-106">MRTK's support for the Oculus Quest comes via two different sources, Unity's XR SDK pipeline and the Oculus Integration Unity package.</span></span> <span data-ttu-id="a410b-107">Das **Oculus XRSDK Datenanbieter** ermöglicht die Verwendung beider Quellen und muss zum Bereitstellen von MRTK auf der Oculus Quest verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a410b-107">The **Oculus XRSDK Data Provider** enables the use of both sources and must be used to deploy MRTK on the Oculus Quest.</span></span>

<span data-ttu-id="a410b-108">Die [Unity XR SDK-Pipeline](https://docs.unity3d.com/Manual/XR.html) ermöglicht die Verwendung von Oculus Touch-Controllern und head tracking mit oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="a410b-108">The [Unity XR SDK Pipeline](https://docs.unity3d.com/Manual/XR.html) enables the use of Oculus Touch controllers and head tracking with the Oculus Quest.</span></span>
<span data-ttu-id="a410b-109">Diese Pipeline ist der Standard für die Entwicklung von XR-Anwendungen in Unity 2019.3 und darüber hinaus.</span><span class="sxs-lookup"><span data-stu-id="a410b-109">This pipeline is the standard for developing XR applications in Unity 2019.3 and beyond.</span></span> <span data-ttu-id="a410b-110">Um diese Pipeline zu verwenden, stellen Sie sicher, dass **Sie Unity 2019.3 oder eine neuere verwenden.**</span><span class="sxs-lookup"><span data-stu-id="a410b-110">To use this pipeline, make sure that you using **Unity 2019.3 or newer**.</span></span> <span data-ttu-id="a410b-111">Dies **ist erforderlich,** um MRTK-Anwendungen in Oculus Quest bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="a410b-111">This is **required** to deploy MRTK applications to the Oculus Quest.</span></span>

<span data-ttu-id="a410b-112">Das [Unity-Paket für die Oculus-Integration](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) ermöglicht die Verwendung der Handverfolgung **mit** oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="a410b-112">The [Oculus Integration Unity package](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) allows for the use of **hand tracking** with the Oculus Quest.</span></span> <span data-ttu-id="a410b-113">Dieser Datenanbieter verwendet **NICHT** die **XR SDK-Pipeline** von Unity oder **die Legacy-XR-Pipeline**.</span><span class="sxs-lookup"><span data-stu-id="a410b-113">This data provider does **NOT** use Unity's **XR SDK Pipeline** or **Legacy XR Pipeline**.</span></span>

## <a name="setting-up-project-for-the-oculus-quest"></a><span data-ttu-id="a410b-114">Einrichten des Projekts für die Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="a410b-114">Setting up project for the Oculus Quest</span></span>

1. <span data-ttu-id="a410b-115">Führen [Sie diese Schritte](https://developer.oculus.com/documentation/unity/book-unity-gsg/) aus, um sicherzustellen, dass Ihr Projekt für die Bereitstellung in Oculus Quest bereit ist.</span><span class="sxs-lookup"><span data-stu-id="a410b-115">Follow [these steps](https://developer.oculus.com/documentation/unity/book-unity-gsg/) to ensure that your project is ready to deploy on Oculus Quest.</span></span>

1. <span data-ttu-id="a410b-116">Stellen Sie [sicher, dass der Entwicklermodus](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) auf Ihrem Gerät aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="a410b-116">Ensure that [developer mode](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) is enabled on your device.</span></span> <span data-ttu-id="a410b-117">Die Installation der Oculus-ADB-Treiber ist optional.</span><span class="sxs-lookup"><span data-stu-id="a410b-117">Installing the Oculus ADB Drivers is optional.</span></span>

## <a name="setting-up-the-xr-sdk-pipeline-for-oculus-quest"></a><span data-ttu-id="a410b-118">Einrichten der XR SDK-Pipeline für Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="a410b-118">Setting up the XR SDK Pipeline for Oculus Quest</span></span>

1. <span data-ttu-id="a410b-119">Stellen Sie **sicher, dass das Oculus XR-Plug-In** unter **Window --> Paket-Manager**</span><span class="sxs-lookup"><span data-stu-id="a410b-119">Ensure that the **Oculus XR Plugin** is installed under **Window --> Package Manager**</span></span>

    ![Oculus XR-Plug-In-Paket](../images/cross-platform/oculus-quest/OculusXRPluginPackage.png)

1. <span data-ttu-id="a410b-121">Stellen Sie sicher, dass der Oculus-Plug-In-Anbieter in Ihrem Projekt enthalten ist, indem Sie zu Bearbeiten **-->-Projekteinstellungen --> XR-Plug-In-Verwaltung --> Plug-In-Anbieter gehen.**</span><span class="sxs-lookup"><span data-stu-id="a410b-121">Make sure that the Oculus Plug-in Provider is included in your project by going to **Edit --> Project Settings --> XR Plug-in Management --> Plug-in Providers**</span></span>

    ![Oculus-Plug-In-Anbieter](../images/cross-platform/oculus-quest/OculusPluginProvider.png)

## <a name="setting-up-the-oculus-integration-unity-package-to-enable-handtracking"></a><span data-ttu-id="a410b-123">Einrichten des Oculus Integration Unity-Pakets zum Aktivieren der Handtracking</span><span class="sxs-lookup"><span data-stu-id="a410b-123">Setting up the Oculus Integration Unity package to enable handtracking</span></span>

1. <span data-ttu-id="a410b-124">Laden Sie die [Oculus-Integration aus](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) dem Unity Asset Store herunter, und importieren Sie sie.</span><span class="sxs-lookup"><span data-stu-id="a410b-124">Download and import [Oculus Integration](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) from the Unity Asset Store.</span></span> <span data-ttu-id="a410b-125">Die neueste getestete Version ist 20.0.0.</span><span class="sxs-lookup"><span data-stu-id="a410b-125">The latest version tested to work is 20.0.0.</span></span> <span data-ttu-id="a410b-126">Ältere Versionen finden Sie in diesem [Archiv.](https://developer.oculus.com/downloads/package/unity-integration-archive/)</span><span class="sxs-lookup"><span data-stu-id="a410b-126">Older versions can be found from this [archive](https://developer.oculus.com/downloads/package/unity-integration-archive/).</span></span>

1. <span data-ttu-id="a410b-127">Navigieren Sie zu Mixed Reality Toolkit > Utilities > Oculus > Integrate Oculus Integration Unity Modules(Oculus-Integrations-Unity-Module integrieren).</span><span class="sxs-lookup"><span data-stu-id="a410b-127">Navigate to Mixed Reality Toolkit > Utilities > Oculus > Integrate Oculus Integration Unity Modules.</span></span> <span data-ttu-id="a410b-128">Dadurch werden die Asmdefs mit Definitionen und Verweisen aktualisiert, die erforderlich sind, damit der relevante Oculus Quest-Code funktioniert.</span><span class="sxs-lookup"><span data-stu-id="a410b-128">Doing this will update the asmdefs with definitions and references needed for the relevant Oculus Quest code to function.</span></span> <span data-ttu-id="a410b-129">Außerdem wird die csc-Datei aktualisiert, um die veralteten Warnungen herausfiltern zu können, die von den Oculus Integration-Ressourcen erzeugt werden.</span><span class="sxs-lookup"><span data-stu-id="a410b-129">It will also update the csc file to filter out the obsolete warnings produced by the Oculus Integration assets.</span></span> <span data-ttu-id="a410b-130">Das MRTK-Repository enthält eine csc-Datei, die Warnungen in Fehler konvertiert. Diese Konvertierung hält den MRTK-Quest an.</span><span class="sxs-lookup"><span data-stu-id="a410b-130">The MRTK repo contains a csc file that converts warnings to errors, this conversion halts the MRTK-Quest configuration process.</span></span>

    ![Oculus Integration Asmdef](../images/cross-platform/oculus-quest/OculusIntegrationAsmdef.png)

1. <span data-ttu-id="a410b-132">Im importierten Ordner Oculus (der sich unter Assets/Oculus befindet) befindet sich ein skriptfähiges Objekt namens OculusProjectConfig.</span><span class="sxs-lookup"><span data-stu-id="a410b-132">In the imported Oculus folder (It should be found at Assets/Oculus), there is a scriptable object called OculusProjectConfig.</span></span> <span data-ttu-id="a410b-133">In dieser Konfigurationsdatei müssen Sie HandTrackingSupport auf "Controller und Hände" festlegen.</span><span class="sxs-lookup"><span data-stu-id="a410b-133">In that config file, you need to set HandTrackingSupport to "Controllers and Hands".</span></span>

    ![Oculus Integration Controller And Hands](../images/cross-platform/oculus-quest/OculusIntegrationControllerAndHands.png)

## <a name="setting-up-the-scene"></a><span data-ttu-id="a410b-135">Einrichten der Szene</span><span class="sxs-lookup"><span data-stu-id="a410b-135">Setting up the scene</span></span>

1. <span data-ttu-id="a410b-136">Erstellen Sie eine neue Unity-Szene, oder öffnen Sie eine bereits vorhandene Szene wie HandInteractionExamples.</span><span class="sxs-lookup"><span data-stu-id="a410b-136">Create a new Unity scene or open a pre-existing scene like HandInteractionExamples.</span></span>
1. <span data-ttu-id="a410b-137">Fügen Sie der Szene MRTK hinzu, indem Sie zu Mixed Reality **Toolkit** zur Szene hinzufügen  >  **und konfigurieren.**</span><span class="sxs-lookup"><span data-stu-id="a410b-137">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**.</span></span>

## <a name="using-the-oculus-xr-sdk-data-provider"></a><span data-ttu-id="a410b-138">Verwenden des Oculus XR SDK Datenanbieter</span><span class="sxs-lookup"><span data-stu-id="a410b-138">Using the Oculus XR SDK Data Provider</span></span>

::: moniker range=">= mrtkunity-2021-05"

1. <span data-ttu-id="a410b-139">Konfigurieren Ihres Profils für die Verwendung **des Oculus XR SDK Datenanbieter**</span><span class="sxs-lookup"><span data-stu-id="a410b-139">Configure your profile to use the **Oculus XR SDK Data Provider**</span></span>
    - <span data-ttu-id="a410b-140">Wenn sie die Konfigurationsprofile nicht ändern möchten</span><span class="sxs-lookup"><span data-stu-id="a410b-140">If not intending to modify the configuration profiles</span></span>
        - <span data-ttu-id="a410b-141">Verwenden Sie eines der MRTK-Standardprofile, die alle über die XR-Pipelines von Unity konfiguriert sind.</span><span class="sxs-lookup"><span data-stu-id="a410b-141">Use any of the default MRTK profiles, which are all configured across Unity's XR pipelines.</span></span> <span data-ttu-id="a410b-142">Das vorherige DefaultXRSDKConfigurationProfile ist jetzt als veraltet gekennzeichnet.</span><span class="sxs-lookup"><span data-stu-id="a410b-142">The previous DefaultXRSDKConfigurationProfile is now labeled obsolete.</span></span>
        - <span data-ttu-id="a410b-143">Wechseln Sie zu Build and deploy your project to Oculus Quest (Erstellen und [Bereitstellen Ihres Projekts in Oculus Quest).](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)</span><span class="sxs-lookup"><span data-stu-id="a410b-143">Go to [Build and deploy your project to Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest).</span></span>
    - <span data-ttu-id="a410b-144">Gehen Sie andernfalls wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="a410b-144">Otherwise follow the following:</span></span>
        - <span data-ttu-id="a410b-145">Wählen Sie das MixedRealityToolkit-Spielobjekt in der Hierarchie aus, und wählen Sie Kopieren und **Anpassen aus,** um das Mixed Reality-Standardprofil zu klonen.</span><span class="sxs-lookup"><span data-stu-id="a410b-145">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

        ![Profil klonen](../images/cross-platform/CloneProfile.png)

        - <span data-ttu-id="a410b-147">Wählen Sie das **Eingabekonfigurationsprofil** aus.</span><span class="sxs-lookup"><span data-stu-id="a410b-147">Select the **Input** Configuration Profile.</span></span>

        ![Eingabekonfigurationsprofil](../images/cross-platform/InputConfigurationProfile.png)

        - <span data-ttu-id="a410b-149">Wählen **Sie im** Eingabesystemprofil Klonen aus, um die Änderung zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="a410b-149">Select **Clone** in the input system profile to enable modification.</span></span>

        ![Klonen des Eingabesystemprofils](../images/cross-platform/CloneInputSystemProfile.png)

        - <span data-ttu-id="a410b-151">Öffnen Sie **den Abschnitt Eingabedatenanbieter,** wählen Sie oben **Datenanbieter** Hinzufügen aus, und am Ende der Liste wird ein neuer Datenanbieter hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="a410b-151">Open the **Input Data Providers** section, select **Add Data Provider** at the top, and new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="a410b-152">Öffnen Sie den neuen Datenanbieter, und legen Sie **type** auf **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager fest.**</span><span class="sxs-lookup"><span data-stu-id="a410b-152">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager**.</span></span>

        ![Oculus Add XRSDK Datenanbieter](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)
::: moniker-end
::: moniker range="< mrtkunity-2021-05"

1. <span data-ttu-id="a410b-154">Konfigurieren Ihres Profils für die Verwendung **des Oculus XR SDK Datenanbieter**</span><span class="sxs-lookup"><span data-stu-id="a410b-154">Configure your profile to use the **Oculus XR SDK Data Provider**</span></span>
    - <span data-ttu-id="a410b-155">Wenn sie die Konfigurationsprofile nicht ändern möchten</span><span class="sxs-lookup"><span data-stu-id="a410b-155">If not intending to modify the configuration profiles</span></span>
        - <span data-ttu-id="a410b-156">Ändern Sie Ihr Profil in DefaultXRSDKConfigurationProfile.</span><span class="sxs-lookup"><span data-stu-id="a410b-156">Change your profile to DefaultXRSDKConfigurationProfile.</span></span>
        - <span data-ttu-id="a410b-157">Wechseln Sie zu Build and deploy your project to Oculus Quest (Erstellen und [Bereitstellen Ihres Projekts in Oculus Quest).](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)</span><span class="sxs-lookup"><span data-stu-id="a410b-157">Go to [Build and deploy your project to Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest).</span></span>
    - <span data-ttu-id="a410b-158">Gehen Sie andernfalls wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="a410b-158">Otherwise follow the following:</span></span>
        - <span data-ttu-id="a410b-159">Wählen Sie das MixedRealityToolkit-Spielobjekt in der Hierarchie aus, und wählen Sie Kopieren und **Anpassen aus,** um das Mixed Reality-Standardprofil zu klonen.</span><span class="sxs-lookup"><span data-stu-id="a410b-159">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

        ![Profil klonen](../images/cross-platform/CloneProfile.png)

        - <span data-ttu-id="a410b-161">Wählen Sie das **Eingabekonfigurationsprofil** aus.</span><span class="sxs-lookup"><span data-stu-id="a410b-161">Select the **Input** Configuration Profile.</span></span>

        ![Eingabekonfigurationsprofil](../images/cross-platform/InputConfigurationProfile.png)

        - <span data-ttu-id="a410b-163">Wählen **Sie im** Eingabesystemprofil Klonen aus, um die Änderung zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="a410b-163">Select **Clone** in the input system profile to enable modification.</span></span>

        ![Klonen des Eingabesystemprofils](../images/cross-platform/CloneInputSystemProfile.png)

        - <span data-ttu-id="a410b-165">Öffnen Sie **den Abschnitt Eingabedatenanbieter,** wählen Sie oben **Datenanbieter** Hinzufügen aus, und am Ende der Liste wird ein neuer Datenanbieter hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="a410b-165">Open the **Input Data Providers** section, select **Add Data Provider** at the top, and new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="a410b-166">Öffnen Sie den neuen Datenanbieter, und legen Sie **type** auf **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager fest.**</span><span class="sxs-lookup"><span data-stu-id="a410b-166">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager**.</span></span>

        ![Oculus Add XRSDK Datenanbieter](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)
::: moniker-end

1. <span data-ttu-id="a410b-168">Das Oculus XR SDK Datenanbieter enthält ein OVR Camera Rig Prefab, das das Projekt automatisch mit einem OVR-Kameragerät und OVR-Händen konfiguriert, um Eingaben ordnungsgemäß weiter zu routen.</span><span class="sxs-lookup"><span data-stu-id="a410b-168">The Oculus XR SDK Data Provider includes an OVR Camera Rig Prefab which automatically configures the project with an OVR Camera Rig and OVR Hands to properly route input.</span></span> <span data-ttu-id="a410b-169">Das manuelle Hinzufügen eines OVR-Kamerageräts zur Szene erfordert eine manuelle Konfiguration von Einstellungen und Eingaben.</span><span class="sxs-lookup"><span data-stu-id="a410b-169">Manually adding an OVR Camera Rig to the scene will require manual configuration of settings and input.</span></span>

## <a name="build-and-deploy-your-project-to-oculus-quest"></a><span data-ttu-id="a410b-170">Erstellen und Bereitstellen Ihres Projekts in Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="a410b-170">Build and deploy your project to Oculus Quest</span></span>

1. <span data-ttu-id="a410b-171">Schließen Sie Oculus Quest über ein USB 3.0-> USB C-Kabel an.</span><span class="sxs-lookup"><span data-stu-id="a410b-171">Plug in your Oculus Quest via a USB 3.0 -> USB C cable</span></span>
1. <span data-ttu-id="a410b-172">Navigieren Sie **zu Datei- > Buildeinstellungen.**</span><span class="sxs-lookup"><span data-stu-id="a410b-172">Navigate to **File > Build Settings**</span></span>
1. <span data-ttu-id="a410b-173">Ändern der Bereitstellung in **Android**</span><span class="sxs-lookup"><span data-stu-id="a410b-173">Change the deployment to **Android**</span></span>
1. <span data-ttu-id="a410b-174">Stellen Sie sicher, dass Oculus Quest als anwendbares Ausführungsgerät ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="a410b-174">Ensure that the Oculus Quest is selected as the applicable run device</span></span>

    ![Oculus Run Device](../images/cross-platform/oculus-quest/OculusRunDevice.png)

1. <span data-ttu-id="a410b-176">Wählen Sie Erstellen und ausführen aus.</span><span class="sxs-lookup"><span data-stu-id="a410b-176">Select Build and Run</span></span>
    - <span data-ttu-id="a410b-177">Die folgenden Buildfehler treten wahrscheinlich auf, wenn Sie Beim ersten Mal *erstellen und* ausführen auswählen.</span><span class="sxs-lookup"><span data-stu-id="a410b-177">You will likely encounter the following set of build errors when you select *Build and Run* the first time.</span></span> <span data-ttu-id="a410b-178">Sie sollten die Bereitstellung erfolgreich ausführen können, wenn Sie *Erneut erstellen und ausführen* auswählen.</span><span class="sxs-lookup"><span data-stu-id="a410b-178">You should be able to successfully deploy upon selecting *Build and Run* again.</span></span>

    ![Oculus Erwartete Buildfehler](../images/cross-platform/oculus-quest/OculusExpectedBuildErrors.png)

1. <span data-ttu-id="a410b-180">Akzeptieren Sie die _Eingabeaufforderung USB-Debuggen_ zulassen innerhalb der Suche.</span><span class="sxs-lookup"><span data-stu-id="a410b-180">Accept the _Allow USB Debugging_ prompt from inside the quest</span></span>
1. <span data-ttu-id="a410b-181">Sehen Sie sich Ihre Szene innerhalb der Oculus Quest an.</span><span class="sxs-lookup"><span data-stu-id="a410b-181">See your scene inside the Oculus Quest</span></span>

## <a name="removing-oculus-integration-from-the-project"></a><span data-ttu-id="a410b-182">Entfernen der Oculus-Integration aus dem Projekt</span><span class="sxs-lookup"><span data-stu-id="a410b-182">Removing Oculus Integration from the Project</span></span>

1. <span data-ttu-id="a410b-183">Navigieren Sie zum Mixed Reality Toolkit > Oculus > Separate Oculus Integration Unity Modules  ![ Oculus Separation Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span><span class="sxs-lookup"><span data-stu-id="a410b-183">Navigate to the Mixed Reality Toolkit > Oculus > Separate Oculus Integration Unity Modules  ![Oculus Separation Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span></span>
1. <span data-ttu-id="a410b-184">Lassen Sie Unity als Verweise in microsoft.MixedReality.Toolkit.Providers.Oculus.asmdef aktualisieren, und andere Dateien werden in diesem Schritt geändert.</span><span class="sxs-lookup"><span data-stu-id="a410b-184">Let Unity refresh as references in the Microsoft.MixedReality.Toolkit.Providers.Oculus.asmdef and other files are modified in this step</span></span>
1. <span data-ttu-id="a410b-185">Schließen von Unity</span><span class="sxs-lookup"><span data-stu-id="a410b-185">Close Unity</span></span>
1. <span data-ttu-id="a410b-186">Schließen Visual Studio, wenn sie geöffnet ist</span><span class="sxs-lookup"><span data-stu-id="a410b-186">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="a410b-187">Öffnen Sie den Datei-Explorer, und navigieren Sie zum Stamm des MRTK-Unity-Projekts.</span><span class="sxs-lookup"><span data-stu-id="a410b-187">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
1. <span data-ttu-id="a410b-188">Löschen des Verzeichnisses UnityProjectName/Library</span><span class="sxs-lookup"><span data-stu-id="a410b-188">Delete the UnityProjectName/Library directory</span></span>
1. <span data-ttu-id="a410b-189">Löschen des Verzeichnisses UnityProjectName/Assets/Oculus</span><span class="sxs-lookup"><span data-stu-id="a410b-189">Delete the UnityProjectName/Assets/Oculus directory</span></span>
1. <span data-ttu-id="a410b-190">Löschen Sie die Datei UnityProjectName/Assets/Oculus.meta.</span><span class="sxs-lookup"><span data-stu-id="a410b-190">Delete the UnityProjectName/Assets/Oculus.meta file</span></span>
1. <span data-ttu-id="a410b-191">Unity erneut öffnen</span><span class="sxs-lookup"><span data-stu-id="a410b-191">Reopen Unity</span></span>

## <a name="common-errors"></a><span data-ttu-id="a410b-192">Häufige Fehler</span><span class="sxs-lookup"><span data-stu-id="a410b-192">Common errors</span></span>

### <a name="quest-not-recognized-by-unity"></a><span data-ttu-id="a410b-193">Quest wird von Unity nicht erkannt</span><span class="sxs-lookup"><span data-stu-id="a410b-193">Quest not recognized by Unity</span></span>

<span data-ttu-id="a410b-194">Stellen Sie sicher, dass Ihre Android-Pfade ordnungsgemäß konfiguriert sind.</span><span class="sxs-lookup"><span data-stu-id="a410b-194">Make sure your Android paths are properly configured.</span></span> <span data-ttu-id="a410b-195">Wenn weiterhin Probleme auftreten, befolgen Sie diese [Anleitung.](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span><span class="sxs-lookup"><span data-stu-id="a410b-195">If you continue to encounter problems, follow this [guide](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span></span>

<span data-ttu-id="a410b-196">**Bearbeiten > Einstellungen > externen Tools > Android**</span><span class="sxs-lookup"><span data-stu-id="a410b-196">**Edit > Preferences > External Tools > Android**</span></span>

![Konfiguration der Android-Tools](../images/cross-platform/oculus-quest/AndroidToolsConfig.png)
