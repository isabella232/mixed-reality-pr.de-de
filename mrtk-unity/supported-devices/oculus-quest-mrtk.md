---
title: Oculus Quest MRTK
description: Dokumentation zum Konfigurieren von Oculus Quest im MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Oculus Quest,
ms.openlocfilehash: 0892e0d416cd07d1bedbeea0ddb316e3eb012b94
ms.sourcegitcommit: 4c1dd5c22af69eeb192425118c2bfb95344b8dd9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2021
ms.locfileid: "110441172"
---
# <a name="building-and-deploying-mrtk-to-oculus-quest-using-the-xr-sdk-pipeline"></a><span data-ttu-id="2aa47-104">Erstellen und Bereitstellen von MRTK für Oculus Quest mithilfe der XR SDK-Pipeline</span><span class="sxs-lookup"><span data-stu-id="2aa47-104">Building and deploying MRTK to Oculus Quest using the XR SDK pipeline</span></span>

<span data-ttu-id="2aa47-105">Eine [Oculus Quest](https://www.oculus.com/quest/) ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="2aa47-105">An [Oculus Quest](https://www.oculus.com/quest/) is required.</span></span>

<span data-ttu-id="2aa47-106">Die MRTK-Unterstützung für Oculus Quest wird über zwei verschiedene Quellen bereitgestellt: die XR SDK-Pipeline von Unity und das Oculus Integration Unity-Paket.</span><span class="sxs-lookup"><span data-stu-id="2aa47-106">MRTK's support for the Oculus Quest comes via two different sources, Unity's XR SDK pipeline and the Oculus Integration Unity package.</span></span> <span data-ttu-id="2aa47-107">Das **Oculus XRSDK Datenanbieter** ermöglicht die Verwendung beider Quellen und muss zum Bereitstellen von MRTK auf der Oculus Quest verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="2aa47-107">The **Oculus XRSDK Data Provider** enables the use of both sources and must be used to deploy MRTK on the Oculus Quest.</span></span>

<span data-ttu-id="2aa47-108">Die [Unity XR SDK-Pipeline](https://docs.unity3d.com/Manual/XR.html) ermöglicht die Verwendung von Oculus Touch-Controllern und der Kopfverfolgung mit oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="2aa47-108">The [Unity XR SDK Pipeline](https://docs.unity3d.com/Manual/XR.html) enables the use of Oculus Touch controllers and head tracking with the Oculus Quest.</span></span>
<span data-ttu-id="2aa47-109">Diese Pipeline ist der Standard für die Entwicklung von XR-Anwendungen in Unity 2019.3 und darüber hinaus.</span><span class="sxs-lookup"><span data-stu-id="2aa47-109">This pipeline is the standard for developing XR applications in Unity 2019.3 and beyond.</span></span> <span data-ttu-id="2aa47-110">Um diese Pipeline zu verwenden, stellen Sie sicher, dass **Sie Unity 2019.3 oder eine neuere verwenden.**</span><span class="sxs-lookup"><span data-stu-id="2aa47-110">To use this pipeline, make sure that you using **Unity 2019.3 or newer**.</span></span> <span data-ttu-id="2aa47-111">Dies **ist erforderlich,** um MRTK-Anwendungen für Oculus Quest bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="2aa47-111">This is **required** to deploy MRTK applications to the Oculus Quest.</span></span> 

<span data-ttu-id="2aa47-112">Das [Unity-Paket für die Oculus-Integration](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) ermöglicht die Verwendung der Handverfolgung **mit** oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="2aa47-112">The [Oculus Integration Unity package](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) allows for the use of **hand tracking** with the Oculus Quest.</span></span> <span data-ttu-id="2aa47-113">Dieser Datenanbieter verwendet **NICHT** die **XR SDK-Pipeline** von Unity oder **die Ältere XR-Pipeline.**</span><span class="sxs-lookup"><span data-stu-id="2aa47-113">This data provider does **NOT** use Unity's **XR SDK Pipeline** or **Legacy XR Pipeline**.</span></span>

## <a name="setting-up-project-for-the-oculus-quest"></a><span data-ttu-id="2aa47-114">Einrichten des Projekts für die Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="2aa47-114">Setting up project for the Oculus Quest</span></span>

1. <span data-ttu-id="2aa47-115">Führen [Sie diese Schritte](https://developer.oculus.com/documentation/unity/book-unity-gsg/) aus, um sicherzustellen, dass Ihr Projekt für die Bereitstellung in Oculus Quest bereit ist.</span><span class="sxs-lookup"><span data-stu-id="2aa47-115">Follow [these steps](https://developer.oculus.com/documentation/unity/book-unity-gsg/) to ensure that your project is ready to deploy on Oculus Quest.</span></span>

1. <span data-ttu-id="2aa47-116">Stellen Sie [sicher, dass der Entwicklermodus](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) auf Ihrem Gerät aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="2aa47-116">Ensure that [developer mode](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) is enabled on your device.</span></span> <span data-ttu-id="2aa47-117">Die Installation der Oculus-ADB-Treiber ist optional.</span><span class="sxs-lookup"><span data-stu-id="2aa47-117">Installing the Oculus ADB Drivers is optional.</span></span>

## <a name="setting-up-the-xr-sdk-pipeline-for-oculus-quest"></a><span data-ttu-id="2aa47-118">Einrichten der XR SDK-Pipeline für Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="2aa47-118">Setting up the XR SDK Pipeline for Oculus Quest</span></span>

1. <span data-ttu-id="2aa47-119">Stellen Sie **sicher, dass das Oculus XR-Plug-In** unter **Window --> Paket-Manager**</span><span class="sxs-lookup"><span data-stu-id="2aa47-119">Ensure that the **Oculus XR Plugin** is installed under **Window --> Package Manager**</span></span>

    ![Oculus XR-Plug-In-Paket](../images/cross-platform/oculus-quest/OculusXRPluginPackage.png)

1. <span data-ttu-id="2aa47-121">Stellen Sie sicher, dass der Oculus-Plug-In-Anbieter in Ihrem Projekt enthalten ist, indem Sie zu Bearbeiten **-->-Projekteinstellungen --> XR-Plug-In-Verwaltung --> Plug-In-Anbieter gehen.**</span><span class="sxs-lookup"><span data-stu-id="2aa47-121">Make sure that the Oculus Plug-in Provider is included in your project by going to **Edit --> Project Settings --> XR Plug-in Management --> Plug-in Providers**</span></span>

    ![Oculus-Plug-In-Anbieter](../images/cross-platform/oculus-quest/OculusPluginProvider.png)

## <a name="setting-up-the-oculus-integration-unity-package-to-enable-handtracking"></a><span data-ttu-id="2aa47-123">Einrichten des Unity-Pakets für die Oculus-Integration zum Aktivieren der Handtracking</span><span class="sxs-lookup"><span data-stu-id="2aa47-123">Setting up the Oculus Integration Unity package to enable handtracking</span></span>

1. <span data-ttu-id="2aa47-124">Laden Sie die [Oculus-Integration aus](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) dem Unity Asset Store herunter, und importieren Sie sie.</span><span class="sxs-lookup"><span data-stu-id="2aa47-124">Download and import [Oculus Integration](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) from the Unity Asset Store.</span></span> <span data-ttu-id="2aa47-125">Die neueste getestete Version ist 20.0.0.</span><span class="sxs-lookup"><span data-stu-id="2aa47-125">The latest version tested to work is 20.0.0.</span></span> <span data-ttu-id="2aa47-126">Ältere Versionen finden Sie in diesem [Archiv.](https://developer.oculus.com/downloads/package/unity-integration-archive/)</span><span class="sxs-lookup"><span data-stu-id="2aa47-126">Older versions can be found from this [archive](https://developer.oculus.com/downloads/package/unity-integration-archive/)</span></span>

1. <span data-ttu-id="2aa47-127">Navigieren Sie Mixed Reality Toolkit > Utilities > Oculus > Integration Oculus Integration Unity Modules (Oculus-Integrationsmodule integrieren).</span><span class="sxs-lookup"><span data-stu-id="2aa47-127">Navigate to Mixed Reality Toolkit > Utilities > Oculus > Integrate Oculus Integration Unity Modules.</span></span> <span data-ttu-id="2aa47-128">Dadurch werden die Asmdefs mit Definitionen und Verweisen aktualisiert, die erforderlich sind, damit der relevante Oculus Quest-Code funktioniert.</span><span class="sxs-lookup"><span data-stu-id="2aa47-128">Doing this will update the asmdefs with definitions and references needed for the relevant Oculus Quest code to function.</span></span> <span data-ttu-id="2aa47-129">Außerdem wird die csc-Datei aktualisiert, um die veralteten Warnungen herausfiltern zu können, die von den Oculus Integration-Ressourcen erzeugt werden.</span><span class="sxs-lookup"><span data-stu-id="2aa47-129">It will also update the csc file to filter out the obsolete warnings produced by the Oculus Integration assets.</span></span> <span data-ttu-id="2aa47-130">Das MRTK-Repository enthält eine csc-Datei, die Warnungen in Fehler konvertiert. Diese Konvertierung hält den MRTK-Quest an.</span><span class="sxs-lookup"><span data-stu-id="2aa47-130">The MRTK repo contains a csc file that converts warnings to errors, this conversion halts the MRTK-Quest configuration process.</span></span>

    ![Oculus Integration Asmdef](../images/cross-platform/oculus-quest/OculusIntegrationAsmdef.png)

1. <span data-ttu-id="2aa47-132">Im importierten Ordner Oculus (unter Assets/Oculus) befindet sich ein skriptfähiges Objekt namens OculusProjectConfig.</span><span class="sxs-lookup"><span data-stu-id="2aa47-132">In the imported Oculus folder (It should be found at Assets/Oculus), there is a scriptable object called OculusProjectConfig.</span></span> <span data-ttu-id="2aa47-133">In dieser Konfigurationsdatei müssen Sie HandTrackingSupport auf "Controller und Hände" festlegen.</span><span class="sxs-lookup"><span data-stu-id="2aa47-133">In that config file, you need to set HandTrackingSupport to "Controllers and Hands".</span></span>

    ![Oculus Integration Controller And Hands](../images/cross-platform/oculus-quest/OculusIntegrationControllerAndHands.png)

## <a name="setting-up-the-scene"></a><span data-ttu-id="2aa47-135">Einrichten der Szene</span><span class="sxs-lookup"><span data-stu-id="2aa47-135">Setting up the scene</span></span>

1. <span data-ttu-id="2aa47-136">Erstellen sie eine neue Unity-Szene, oder öffnen Sie eine bereits vorhandene Szene wie HandInteractionExamples.</span><span class="sxs-lookup"><span data-stu-id="2aa47-136">Create a new Unity scene or open a pre-existing scene like HandInteractionExamples</span></span>
1. <span data-ttu-id="2aa47-137">Fügen Sie der Szene MRTK hinzu, indem Sie zu Mixed Reality **Toolkit**  >  **Hinzufügen zur Szene und Konfigurieren navigieren.**</span><span class="sxs-lookup"><span data-stu-id="2aa47-137">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**</span></span>

## <a name="using-the-oculus-xr-sdk-data-provider"></a><span data-ttu-id="2aa47-138">Verwenden des Oculus XR SDK Datenanbieter</span><span class="sxs-lookup"><span data-stu-id="2aa47-138">Using the Oculus XR SDK Data Provider</span></span>

1. <span data-ttu-id="2aa47-139">Konfigurieren Ihres Profils für die Verwendung **des Oculus XR SDK Datenanbieter**</span><span class="sxs-lookup"><span data-stu-id="2aa47-139">Configure your profile to use the **Oculus XR SDK Data Provider**</span></span>
    - <span data-ttu-id="2aa47-140">Wenn die Konfigurationsprofile nicht geändert werden sollen</span><span class="sxs-lookup"><span data-stu-id="2aa47-140">If not intending to modify the configuration profiles</span></span>
        - <span data-ttu-id="2aa47-141">Ändern Sie Ihr Profil in DefaultXRSDKConfigurationProfile, und wechseln Sie zu Erstellen und Bereitstellen Ihres Projekts [in Oculus Quest.](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)</span><span class="sxs-lookup"><span data-stu-id="2aa47-141">Change your profile to DefaultXRSDKConfigurationProfile and go to [Build and deploy your project to Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)</span></span>

    - <span data-ttu-id="2aa47-142">Gehen Sie andernfalls wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="2aa47-142">Otherwise follow the following:</span></span>
        - <span data-ttu-id="2aa47-143">Wählen Sie das MixedRealityToolkit-Spielobjekt in der Hierarchie aus, und wählen Sie Kopieren und **Anpassen aus,** um das Mixed Reality-Standardprofil zu klonen.</span><span class="sxs-lookup"><span data-stu-id="2aa47-143">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

        ![Profil klonen](../images/cross-platform/CloneProfile.png)

        - <span data-ttu-id="2aa47-145">Auswählen des **Eingabekonfigurationsprofils**</span><span class="sxs-lookup"><span data-stu-id="2aa47-145">Select the **Input** Configuration Profile</span></span>

        ![Eingabekonfigurationsprofil](../images/cross-platform/InputConfigurationProfile.png)

        - <span data-ttu-id="2aa47-147">Wählen **Sie im** Eingabesystemprofil Klonen aus, um die Änderung zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="2aa47-147">Select **Clone** in the input system profile to enable modification.</span></span>

        ![Klonen des Eingabesystemprofils](../images/cross-platform/CloneInputSystemProfile.png)

        - <span data-ttu-id="2aa47-149">Öffnen Sie **den Abschnitt Eingabedatenanbieter,** wählen Sie oben **Datenanbieter** Hinzufügen aus, und am Ende der Liste wird ein neuer Datenanbieter hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="2aa47-149">Open the **Input Data Providers** section, select **Add Data Provider** at the top, and new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="2aa47-150">Öffnen Sie den neuen Datenanbieter, und legen Sie **type** auf **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager fest.**</span><span class="sxs-lookup"><span data-stu-id="2aa47-150">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager**</span></span>

        ![Oculus Add XRSDK Datenanbieter](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)

1. <span data-ttu-id="2aa47-152">Das Oculus XR SDK Datenanbieter enthält ein OVR Camera Rig Prefab, das das Projekt automatisch mit einem OVR-Kameragerät und OVR-Händen konfiguriert, um Eingaben ordnungsgemäß weiter zu routen.</span><span class="sxs-lookup"><span data-stu-id="2aa47-152">The Oculus XR SDK Data Provider includes an OVR Camera Rig Prefab which automatically configures the project with an OVR Camera Rig and OVR Hands to properly route input.</span></span> <span data-ttu-id="2aa47-153">Das manuelle Hinzufügen eines OVR-Kamerageräts zur Szene erfordert eine manuelle Konfiguration von Einstellungen und Eingaben.</span><span class="sxs-lookup"><span data-stu-id="2aa47-153">Manually adding an OVR Camera Rig to the scene will require manual configuration of settings and input.</span></span>

## <a name="build-and-deploy-your-project-to-oculus-quest"></a><span data-ttu-id="2aa47-154">Erstellen und Bereitstellen Ihres Projekts in Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="2aa47-154">Build and deploy your project to Oculus Quest</span></span>

1. <span data-ttu-id="2aa47-155">Schließen Sie Oculus Quest über ein USB 3.0-> USB C-Kabel an.</span><span class="sxs-lookup"><span data-stu-id="2aa47-155">Plug in your Oculus Quest via a USB 3.0 -> USB C cable</span></span>
1. <span data-ttu-id="2aa47-156">Navigieren Sie **zu Datei- > Buildeinstellungen.**</span><span class="sxs-lookup"><span data-stu-id="2aa47-156">Navigate to **File > Build Settings**</span></span>
1. <span data-ttu-id="2aa47-157">Ändern der Bereitstellung in **Android**</span><span class="sxs-lookup"><span data-stu-id="2aa47-157">Change the deployment to **Android**</span></span>
1. <span data-ttu-id="2aa47-158">Stellen Sie sicher, dass Oculus Quest als anwendbares Ausführungsgerät ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="2aa47-158">Ensure that the Oculus Quest is selected as the applicable run device</span></span>

    ![Oculus Run Device](../images/cross-platform/oculus-quest/OculusRunDevice.png)

1. <span data-ttu-id="2aa47-160">Wählen Sie Erstellen und ausführen aus.</span><span class="sxs-lookup"><span data-stu-id="2aa47-160">Select Build and Run</span></span>
    - <span data-ttu-id="2aa47-161">Die folgenden Buildfehler treten wahrscheinlich auf, wenn Sie Beim ersten Mal *erstellen und* ausführen auswählen.</span><span class="sxs-lookup"><span data-stu-id="2aa47-161">You will likely encounter the following set of build errors when you select *Build and Run* the first time.</span></span> <span data-ttu-id="2aa47-162">Sie sollten die Bereitstellung erfolgreich ausführen können, wenn Sie *Erneut erstellen und ausführen* auswählen.</span><span class="sxs-lookup"><span data-stu-id="2aa47-162">You should be able to successfully deploy upon selecting *Build and Run* again.</span></span>

    ![Oculus Erwartete Buildfehler](../images/cross-platform/oculus-quest/OculusExpectedBuildErrors.png)

1. <span data-ttu-id="2aa47-164">Akzeptieren Sie die _Eingabeaufforderung USB-Debuggen_ zulassen innerhalb der Suche.</span><span class="sxs-lookup"><span data-stu-id="2aa47-164">Accept the _Allow USB Debugging_ prompt from inside the quest</span></span>
1. <span data-ttu-id="2aa47-165">Sehen Sie sich Ihre Szene innerhalb der Oculus-Suche an.</span><span class="sxs-lookup"><span data-stu-id="2aa47-165">See your scene inside the Oculus Quest</span></span>

## <a name="removing-oculus-integration-from-the-project"></a><span data-ttu-id="2aa47-166">Entfernen der Oculus-Integration aus dem Projekt</span><span class="sxs-lookup"><span data-stu-id="2aa47-166">Removing Oculus Integration from the Project</span></span>

1. <span data-ttu-id="2aa47-167">Navigieren Sie zum Mixed Reality Toolkit > Oculus > Separate Oculus Integration Unity Modules  ![ Oculus Separation Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span><span class="sxs-lookup"><span data-stu-id="2aa47-167">Navigate to the Mixed Reality Toolkit > Oculus > Separate Oculus Integration Unity Modules  ![Oculus Separation Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span></span>
1. <span data-ttu-id="2aa47-168">Lassen Sie Unity als Verweise in microsoft.MixedReality.Toolkit.Providers.Oculus.asmdef aktualisieren, und andere Dateien werden in diesem Schritt geändert.</span><span class="sxs-lookup"><span data-stu-id="2aa47-168">Let Unity refresh as references in the Microsoft.MixedReality.Toolkit.Providers.Oculus.asmdef and other files are modified in this step</span></span>
1. <span data-ttu-id="2aa47-169">Schließen von Unity</span><span class="sxs-lookup"><span data-stu-id="2aa47-169">Close Unity</span></span>
1. <span data-ttu-id="2aa47-170">Schließen Visual Studio, wenn sie geöffnet ist</span><span class="sxs-lookup"><span data-stu-id="2aa47-170">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="2aa47-171">Öffnen Sie den Datei-Explorer, und navigieren Sie zum Stamm des MRTK-Unity-Projekts.</span><span class="sxs-lookup"><span data-stu-id="2aa47-171">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
1. <span data-ttu-id="2aa47-172">Löschen des Verzeichnisses UnityProjectName/Library</span><span class="sxs-lookup"><span data-stu-id="2aa47-172">Delete the UnityProjectName/Library directory</span></span>
1. <span data-ttu-id="2aa47-173">Löschen des Verzeichnisses UnityProjectName/Assets/Oculus</span><span class="sxs-lookup"><span data-stu-id="2aa47-173">Delete the UnityProjectName/Assets/Oculus directory</span></span>
1. <span data-ttu-id="2aa47-174">Löschen Sie die Datei UnityProjectName/Assets/Oculus.meta.</span><span class="sxs-lookup"><span data-stu-id="2aa47-174">Delete the UnityProjectName/Assets/Oculus.meta file</span></span>
1. <span data-ttu-id="2aa47-175">Unity erneut öffnen</span><span class="sxs-lookup"><span data-stu-id="2aa47-175">Reopen Unity</span></span>

## <a name="common-errors"></a><span data-ttu-id="2aa47-176">Häufige Fehler</span><span class="sxs-lookup"><span data-stu-id="2aa47-176">Common errors</span></span>

### <a name="quest-not-recognized-by-unity"></a><span data-ttu-id="2aa47-177">Quest wird von Unity nicht erkannt</span><span class="sxs-lookup"><span data-stu-id="2aa47-177">Quest not recognized by Unity</span></span>

<span data-ttu-id="2aa47-178">Stellen Sie sicher, dass Ihre Android-Pfade ordnungsgemäß konfiguriert sind.</span><span class="sxs-lookup"><span data-stu-id="2aa47-178">Make sure your Android paths are properly configured.</span></span> <span data-ttu-id="2aa47-179">Wenn weiterhin Probleme auftreten, befolgen Sie diese [Anleitung.](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span><span class="sxs-lookup"><span data-stu-id="2aa47-179">If you continue to encounter problems, follow this [guide](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span></span>

<span data-ttu-id="2aa47-180">**Bearbeiten > Einstellungen > externen Tools > Android**</span><span class="sxs-lookup"><span data-stu-id="2aa47-180">**Edit > Preferences > External Tools > Android**</span></span>

![Konfiguration der Android-Tools](../images/cross-platform/oculus-quest/AndroidToolsConfig.png)
