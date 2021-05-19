---
title: Oculus Quest MRTK
description: Dokumentation zum Konfigurieren für Oculus Quest im MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Oculus Quest,
ms.openlocfilehash: c0eccd0b366d39529eafc51d23031fc30144b1ae
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143963"
---
# <a name="how-to-configure-oculus-quest-in-mrtk-using-the-xr-sdk-pipeline"></a><span data-ttu-id="511fb-104">Konfigurieren von Oculus Quest in MRTK mithilfe der XR SDK-Pipeline</span><span class="sxs-lookup"><span data-stu-id="511fb-104">How to configure Oculus Quest in MRTK using the XR SDK pipeline</span></span>

<span data-ttu-id="511fb-105">Eine [Oculus Quest](https://www.oculus.com/quest/) ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="511fb-105">A [Oculus Quest](https://www.oculus.com/quest/) is required.</span></span>

<span data-ttu-id="511fb-106">Die MRTK-Unterstützung für Oculus Quest wird über zwei verschiedene Quellen unterstützt: die XR-Pipeline von Unity und das Oculus Integration Unity-Paket.</span><span class="sxs-lookup"><span data-stu-id="511fb-106">MRTK's support for the Oculus Quest comes via two different sources, Unity's XR pipeline and the Oculus Integration Unity package.</span></span> <span data-ttu-id="511fb-107">Das **Oculus XRSDK Datenanbieter** ermöglicht die Verwendung beider Quellen und muss für die Verwendung von MRTK in Oculus Quest verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="511fb-107">The **Oculus XRSDK Data Provider** enables the use of both sources and must be used to use MRTK on the Oculus Quest.</span></span>

<span data-ttu-id="511fb-108">Die [XR-Pipeline von Unity](https://docs.unity3d.com/Manual/XR.html) ermöglicht die Verwendung von Oculus Touch-Controllern und head tracking mit oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="511fb-108">The [Unity's XR Pipeline](https://docs.unity3d.com/Manual/XR.html) enables the use of Oculus Touch controllers and head tracking with the Oculus Quest.</span></span>
<span data-ttu-id="511fb-109">Diese Pipeline ist der Standard für die Entwicklung von XR-Anwendungen in Unity 2019.3 und darüber hinaus.</span><span class="sxs-lookup"><span data-stu-id="511fb-109">This pipeline is the standard for developing XR applications in Unity 2019.3 and beyond.</span></span> <span data-ttu-id="511fb-110">Um diese Pipeline zu verwenden, stellen Sie sicher, dass **Sie Unity 2019.3 oder eine neuere verwenden.**</span><span class="sxs-lookup"><span data-stu-id="511fb-110">To use this pipeline, make sure that you using **Unity 2019.3 or newer**.</span></span>

<span data-ttu-id="511fb-111">Das [Unity-Paket für die Oculus-Integration](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) ermöglicht die Verwendung der Handverfolgung **mit** oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="511fb-111">The [Oculus Integration Unity package](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) allows for the use of **hand tracking** with the Oculus Quest.</span></span>
<span data-ttu-id="511fb-112">Dieser Datenanbieter  verwendet NICHT die **XR-Pipeline** von Unity oder die **Legacy-XR-Pipeline.** Da Controller und Die Nachverfolgung jedoch von der XR-Pipeline von Unity verarbeitet werden, müssen die Schritte unter Einrichten des Projekts für **oculus Quest** befolgt werden, um sicherzustellen, dass Sie die **XR-Pipeline** und nicht die veraltete **Legacy-XR-Pipeline verwenden.**</span><span class="sxs-lookup"><span data-stu-id="511fb-112">This data provider does **NOT** use Unity's **XR Pipeline** or **Legacy XR Pipeline**, but because controllers and headtracking are handled by the Unity's XR Pipeline, the steps in **Setting up project for the Oculus Quest** must be followed to ensure that you are using the **XR Pipeline** and not the to-be-deprecated **Legacy XR Pipeline**.</span></span>

## <a name="setting-up-project-for-the-oculus-quest"></a><span data-ttu-id="511fb-113">Einrichten des Projekts für die Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="511fb-113">Setting up project for the Oculus Quest</span></span>

1. <span data-ttu-id="511fb-114">Führen [Sie diese Schritte](https://developer.oculus.com/documentation/unity/book-unity-gsg/) aus, um sicherzustellen, dass Ihr Projekt für die Bereitstellung in Oculus Quest bereit ist.</span><span class="sxs-lookup"><span data-stu-id="511fb-114">Follow [these steps](https://developer.oculus.com/documentation/unity/book-unity-gsg/) to ensure that your project is ready to deploy on Oculus Quest.</span></span>

1. <span data-ttu-id="511fb-115">Stellen Sie [sicher, dass der Entwicklermodus](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) auf Ihrem Gerät aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="511fb-115">Ensure that [developer mode](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) is enabled on your device.</span></span> <span data-ttu-id="511fb-116">Die Installation der Oculus-ADB-Treiber ist optional.</span><span class="sxs-lookup"><span data-stu-id="511fb-116">Installing the Oculus ADB Drivers is optional.</span></span>

## <a name="setting-up-the-xr-pipeline-for-oculus-quest"></a><span data-ttu-id="511fb-117">Einrichten der XR-Pipeline für Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="511fb-117">Setting up the XR Pipeline for Oculus Quest</span></span>

1. <span data-ttu-id="511fb-118">Stellen Sie **sicher, dass das Oculus XR-Plug-In** unter **Window --> Paket-Manager**</span><span class="sxs-lookup"><span data-stu-id="511fb-118">Ensure that the **Oculus XR Plugin** is installed under **Window --> Package Manager**</span></span>

    ![Oculus XR-Plug-In-Paket](../images/cross-platform/oculus-quest/OculusXRPluginPackage.png)

1. <span data-ttu-id="511fb-120">Stellen Sie sicher, dass der Oculus-Plug-In-Anbieter in Ihrem Projekt enthalten ist, indem Sie zu Bearbeiten **-->-Projekteinstellungen --> XR-Plug-In-Verwaltung --> Plug-In-Anbieter gehen.**</span><span class="sxs-lookup"><span data-stu-id="511fb-120">Make sure that the Oculus Plug-in Provider is included in your project by going to **Edit --> Project Settings --> XR Plug-in Management --> Plug-in Providers**</span></span>

    ![Oculus-Plug-In-Anbieter](../images/cross-platform/oculus-quest/OculusPluginProvider.png)

## <a name="setting-up-the-oculus-integration-unity-package-to-enable-handtracking"></a><span data-ttu-id="511fb-122">Einrichten des Oculus Integration Unity-Pakets zum Aktivieren der Handtracking</span><span class="sxs-lookup"><span data-stu-id="511fb-122">Setting up the Oculus Integration Unity package to enable handtracking</span></span>

1. <span data-ttu-id="511fb-123">Laden Sie [Oculus Integration](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) aus dem Unity Asset Store herunter, und importieren Sie sie.</span><span class="sxs-lookup"><span data-stu-id="511fb-123">Download and import [Oculus Integration](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) from the Unity Asset Store.</span></span> <span data-ttu-id="511fb-124">Die neueste Version, die getestet wurde, ist 20.0.0.</span><span class="sxs-lookup"><span data-stu-id="511fb-124">The latest version tested to work is 20.0.0.</span></span> <span data-ttu-id="511fb-125">Ältere Versionen finden Sie in diesem [Archiv.](https://developer.oculus.com/downloads/package/unity-integration-archive/)</span><span class="sxs-lookup"><span data-stu-id="511fb-125">Older versions can be found from this [archive](https://developer.oculus.com/downloads/package/unity-integration-archive/)</span></span>

1. <span data-ttu-id="511fb-126">Navigieren Sie zu Mixed Reality Toolkit > Utilities > Oculus > Integrate Oculus Integration Unity Modules(Oculus Integration Unity-Module integrieren).</span><span class="sxs-lookup"><span data-stu-id="511fb-126">Navigate to Mixed Reality Toolkit > Utilities > Oculus > Integrate Oculus Integration Unity Modules.</span></span> <span data-ttu-id="511fb-127">Dadurch werden die asmdefs mit Definitionen und Verweisen aktualisiert, die für die Funktion des relevanten Oculus Quest-Codes erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="511fb-127">Doing this will update the asmdefs with definitions and references needed for the relevant Oculus Quest code to function.</span></span> <span data-ttu-id="511fb-128">Außerdem wird die csc-Datei aktualisiert, um die veralteten Warnungen herauszufiltern, die von den Oculus-Integrationsressourcen erzeugt werden.</span><span class="sxs-lookup"><span data-stu-id="511fb-128">It will also update the csc file to filter out the obsolete warnings produced by the Oculus Integration assets.</span></span> <span data-ttu-id="511fb-129">Das MRTK-Repository enthält eine csc-Datei, die Warnungen in Fehler konvertiert. Diese Konvertierung hält den MRTK-Quest Konfigurationsprozess an.</span><span class="sxs-lookup"><span data-stu-id="511fb-129">The MRTK repo contains a csc file that converts warnings to errors, this conversion halts the MRTK-Quest configuration process.</span></span>

    ![Oculus Integration Asmdef](../images/cross-platform/oculus-quest/OculusIntegrationAsmdef.png)

1. <span data-ttu-id="511fb-131">Im importierten Oculus-Ordner (er sollte sich unter Assets/Oculus befinden) befindet sich ein skriptfähiges Objekt namens OculusProjectConfig.</span><span class="sxs-lookup"><span data-stu-id="511fb-131">In the imported Oculus folder (It should be found at Assets/Oculus), there is a scriptable object called OculusProjectConfig.</span></span> <span data-ttu-id="511fb-132">In dieser Konfigurationsdatei müssen Sie HandTrackingSupport auf "Controllers and Hands" festlegen.</span><span class="sxs-lookup"><span data-stu-id="511fb-132">In that config file, you need to set HandTrackingSupport to "Controllers and Hands".</span></span>

    ![Oculus-Integrationscontroller und -Hände](../images/cross-platform/oculus-quest/OculusIntegrationControllerAndHands.png)

## <a name="setting-up-the-scene"></a><span data-ttu-id="511fb-134">Einrichten der Szene</span><span class="sxs-lookup"><span data-stu-id="511fb-134">Setting up the scene</span></span>

1. <span data-ttu-id="511fb-135">Erstellen einer neuen Unity-Szene oder Öffnen einer bereits vorhandenen Szene wie HandInteractionExamples</span><span class="sxs-lookup"><span data-stu-id="511fb-135">Create a new Unity scene or open a pre-existing scene like HandInteractionExamples</span></span>
1. <span data-ttu-id="511fb-136">Fügen Sie mrtk zur Szene hinzu, indem Sie zu **Mixed Reality Toolkit** Add to  >  **Scene (Zur Szene hinzufügen) navigieren und konfigurieren.**</span><span class="sxs-lookup"><span data-stu-id="511fb-136">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**</span></span>

## <a name="using-the-oculus-xr-sdk-data-provider"></a><span data-ttu-id="511fb-137">Verwenden des Oculus XR SDK Datenanbieter</span><span class="sxs-lookup"><span data-stu-id="511fb-137">Using the Oculus XR SDK Data Provider</span></span>

1. <span data-ttu-id="511fb-138">Konfigurieren Ihres Profils für die Verwendung des **Oculus XR SDK Datenanbieter**</span><span class="sxs-lookup"><span data-stu-id="511fb-138">Configure your profile to use the **Oculus XR SDK Data Provider**</span></span>
    - <span data-ttu-id="511fb-139">Wenn sie nicht beabsichtigen, die Konfigurationsprofile zu ändern</span><span class="sxs-lookup"><span data-stu-id="511fb-139">If not intending to modify the configuration profiles</span></span>
        - <span data-ttu-id="511fb-140">Ändern Sie Ihr Profil in DefaultXRSDKConfigurationProfile, und wechseln Sie zu [Erstellen und Bereitstellen Ihres Projekts in Oculus Quest.](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)</span><span class="sxs-lookup"><span data-stu-id="511fb-140">Change your profile to DefaultXRSDKConfigurationProfile and go to [Build and deploy your project to Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)</span></span>

    - <span data-ttu-id="511fb-141">Andernfalls gehen Sie wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="511fb-141">Otherwise follow the following:</span></span>
        - <span data-ttu-id="511fb-142">Wählen Sie das MixedRealityToolkit-Spielobjekt in der Hierarchie aus, und wählen Sie Kopieren und **Anpassen aus,** um das Mixed Reality-Standardprofil zu klonen.</span><span class="sxs-lookup"><span data-stu-id="511fb-142">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

        ![Profil klonen](../images/cross-platform/CloneProfile.png)

        - <span data-ttu-id="511fb-144">Auswählen des **Eingabekonfigurationsprofils**</span><span class="sxs-lookup"><span data-stu-id="511fb-144">Select the **Input** Configuration Profile</span></span>

        ![Eingabekonfigurationsprofil](../images/cross-platform/InputConfigurationProfile.png)

        - <span data-ttu-id="511fb-146">Wählen **Sie im** Eingabesystemprofil Klonen aus, um die Änderung zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="511fb-146">Select **Clone** in the input system profile to enable modification.</span></span>

        ![Klonen des Eingabesystemprofils](../images/cross-platform/CloneInputSystemProfile.png)

        - <span data-ttu-id="511fb-148">Öffnen Sie **den Abschnitt Eingabedatenanbieter,** wählen Sie oben **Datenanbieter** Hinzufügen aus, und am Ende der Liste wird ein neuer Datenanbieter hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="511fb-148">Open the **Input Data Providers** section, select **Add Data Provider** at the top, and new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="511fb-149">Öffnen Sie den neuen Datenanbieter, und legen Sie **type** auf **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager fest.**</span><span class="sxs-lookup"><span data-stu-id="511fb-149">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager**</span></span>

        ![Oculus Add XRSDK Datenanbieter](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)

1. <span data-ttu-id="511fb-151">Das Oculus XR SDK Datenanbieter enthält ein OVR Camera Oc Prefab, das das Projekt automatisch mit einem OVR-Kameragerät und OVR-Händen konfiguriert, um Eingaben ordnungsgemäß weiter zu routen.</span><span class="sxs-lookup"><span data-stu-id="511fb-151">The Oculus XR SDK Data Provider includes an OVR Camera Rig Prefab which automatically configures the project with an OVR Camera Rig and OVR Hands to properly route input.</span></span> <span data-ttu-id="511fb-152">Das manuelle Hinzufügen eines OVR-Kamerageräts zur Szene erfordert eine manuelle Konfiguration von Einstellungen und Eingaben.</span><span class="sxs-lookup"><span data-stu-id="511fb-152">Manually adding an OVR Camera Rig to the scene will require manual configuration of settings and input.</span></span>

## <a name="build-and-deploy-your-project-to-oculus-quest"></a><span data-ttu-id="511fb-153">Erstellen und Bereitstellen Ihres Projekts in Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="511fb-153">Build and deploy your project to Oculus Quest</span></span>

1. <span data-ttu-id="511fb-154">Schließen Sie Oculus Quest über ein USB 3.0-> USB C-Kabel an.</span><span class="sxs-lookup"><span data-stu-id="511fb-154">Plug in your Oculus Quest via a USB 3.0 -> USB C cable</span></span>
1. <span data-ttu-id="511fb-155">Navigieren Sie **zu Datei- > Buildeinstellungen.**</span><span class="sxs-lookup"><span data-stu-id="511fb-155">Navigate to **File > Build Settings**</span></span>
1. <span data-ttu-id="511fb-156">Ändern der Bereitstellung in **Android**</span><span class="sxs-lookup"><span data-stu-id="511fb-156">Change the deployment to **Android**</span></span>
1. <span data-ttu-id="511fb-157">Stellen Sie sicher, dass Oculus Quest als anwendbares Ausführungsgerät ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="511fb-157">Ensure that the Oculus Quest is selected as the applicable run device</span></span>

    ![Oculus Run Device](../images/cross-platform/oculus-quest/OculusRunDevice.png)

1. <span data-ttu-id="511fb-159">Wählen Sie Erstellen und ausführen aus.</span><span class="sxs-lookup"><span data-stu-id="511fb-159">Select Build and Run</span></span>
    - <span data-ttu-id="511fb-160">Die folgenden Buildfehler treten wahrscheinlich auf, wenn Sie Beim ersten Mal *erstellen und* ausführen auswählen.</span><span class="sxs-lookup"><span data-stu-id="511fb-160">You will likely encounter the following set of build errors when you select *Build and Run* the first time.</span></span> <span data-ttu-id="511fb-161">Sie sollten die Bereitstellung erfolgreich ausführen können, wenn Sie *Erneut erstellen und ausführen* auswählen.</span><span class="sxs-lookup"><span data-stu-id="511fb-161">You should be able to successfully deploy upon selecting *Build and Run* again.</span></span>

    ![Oculus: Erwartete Buildfehler](../images/cross-platform/oculus-quest/OculusExpectedBuildErrors.png)

1. <span data-ttu-id="511fb-163">Akzeptieren Sie die Eingabeaufforderung _USB-Debuggen zulassen_ aus der Aufgabe heraus.</span><span class="sxs-lookup"><span data-stu-id="511fb-163">Accept the _Allow USB Debugging_ prompt from inside the quest</span></span>
1. <span data-ttu-id="511fb-164">Sehen Sie sich Ihre Szene in der Oculus Quest an.</span><span class="sxs-lookup"><span data-stu-id="511fb-164">See your scene inside the Oculus Quest</span></span>

## <a name="removing-oculus-integration-from-the-project"></a><span data-ttu-id="511fb-165">Entfernen der Oculus-Integration aus dem Projekt</span><span class="sxs-lookup"><span data-stu-id="511fb-165">Removing Oculus Integration from the Project</span></span>

1. <span data-ttu-id="511fb-166">Navigieren Sie zum Mixed Reality Toolkit > Oculus > Separate Oculus Integration Unity Modules  ![ Oculus Separation Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span><span class="sxs-lookup"><span data-stu-id="511fb-166">Navigate to the Mixed Reality Toolkit > Oculus > Separate Oculus Integration Unity Modules  ![Oculus Separation Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span></span>
1. <span data-ttu-id="511fb-167">Lassen Sie Unity als Verweise in Microsoft.MixedReality.Toolkit.Providers.Oculus.asmdef aktualisieren, und andere Dateien werden in diesem Schritt geändert.</span><span class="sxs-lookup"><span data-stu-id="511fb-167">Let Unity refresh as references in the Microsoft.MixedReality.Toolkit.Providers.Oculus.asmdef and other files are modified in this step</span></span>
1. <span data-ttu-id="511fb-168">Schließen von Unity</span><span class="sxs-lookup"><span data-stu-id="511fb-168">Close Unity</span></span>
1. <span data-ttu-id="511fb-169">Schließen Sie Visual Studio, wenn es geöffnet ist.</span><span class="sxs-lookup"><span data-stu-id="511fb-169">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="511fb-170">Öffnen Sie den Datei-Explorer, und navigieren Sie zum Stamm des MRTK-Unity-Projekts.</span><span class="sxs-lookup"><span data-stu-id="511fb-170">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
1. <span data-ttu-id="511fb-171">Löschen des UnityProjectName/Library-Verzeichnisses</span><span class="sxs-lookup"><span data-stu-id="511fb-171">Delete the UnityProjectName/Library directory</span></span>
1. <span data-ttu-id="511fb-172">Löschen des Verzeichnisses UnityProjectName/Assets/Oculus</span><span class="sxs-lookup"><span data-stu-id="511fb-172">Delete the UnityProjectName/Assets/Oculus directory</span></span>
1. <span data-ttu-id="511fb-173">Löschen sie die Datei UnityProjectName/Assets/Oculus.meta.</span><span class="sxs-lookup"><span data-stu-id="511fb-173">Delete the UnityProjectName/Assets/Oculus.meta file</span></span>
1. <span data-ttu-id="511fb-174">Unity erneut öffnen</span><span class="sxs-lookup"><span data-stu-id="511fb-174">Reopen Unity</span></span>

## <a name="common-errors"></a><span data-ttu-id="511fb-175">Häufige Fehler</span><span class="sxs-lookup"><span data-stu-id="511fb-175">Common errors</span></span>

### <a name="quest-not-recognized-by-unity"></a><span data-ttu-id="511fb-176">Quest wird von Unity nicht erkannt</span><span class="sxs-lookup"><span data-stu-id="511fb-176">Quest not recognized by Unity</span></span>

<span data-ttu-id="511fb-177">Stellen Sie sicher, dass Ihre Android-Pfade ordnungsgemäß konfiguriert sind.</span><span class="sxs-lookup"><span data-stu-id="511fb-177">Make sure your Android paths are properly configured.</span></span> <span data-ttu-id="511fb-178">Wenn weiterhin Probleme auftreten, befolgen Sie diese [Anleitung.](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span><span class="sxs-lookup"><span data-stu-id="511fb-178">If you continue to encounter problems, follow this [guide](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span></span>

<span data-ttu-id="511fb-179">**Bearbeiten > Einstellungen > externen Tools > Android**</span><span class="sxs-lookup"><span data-stu-id="511fb-179">**Edit > Preferences > External Tools > Android**</span></span>

![Android Tools-Konfiguration](../images/cross-platform/oculus-quest/AndroidToolsConfig.png)
