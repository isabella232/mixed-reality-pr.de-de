---
title: Erstellen eines Anbieters für Kameraeinstellungen
description: Datenanbieter für Kameraeinstellungen in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 2151887a6162239e993634d5d346065362f1c428
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2021
ms.locfileid: "114282033"
---
# <a name="creating-a-camera-settings-provider"></a><span data-ttu-id="21292-104">Erstellen eines Anbieters für Kameraeinstellungen</span><span class="sxs-lookup"><span data-stu-id="21292-104">Creating a camera settings provider</span></span>

<span data-ttu-id="21292-105">Das Kamerasystem ist ein erweiterbares System für die Unterstützung plattformspezifischer Kamerakonfigurationen.</span><span class="sxs-lookup"><span data-stu-id="21292-105">The Camera system is an extensible system for providing support for platform specific camera configurations.</span></span> <span data-ttu-id="21292-106">Um Unterstützung für eine neue Kamerakonfiguration hinzuzufügen, ist möglicherweise ein benutzerdefinierter Einstellungsanbieter erforderlich.</span><span class="sxs-lookup"><span data-stu-id="21292-106">To add support for a new camera configuration, a custom settings provider may be required.</span></span>

> [!NOTE]
> <span data-ttu-id="21292-107">Den vollständigen Quellcode, der in diesem Beispiel verwendet wird, finden Sie im Ordner **MRTK/Providers/UnityAR.**</span><span class="sxs-lookup"><span data-stu-id="21292-107">The complete source code used in this example can be found in the **MRTK/Providers/UnityAR** folder.</span></span>

## <a name="namespace-and-folder-structure"></a><span data-ttu-id="21292-108">Namespace- und Ordnerstruktur</span><span class="sxs-lookup"><span data-stu-id="21292-108">Namespace and folder structure</span></span>

<span data-ttu-id="21292-109">Datenanbieter können auf zwei Arten verteilt werden:</span><span class="sxs-lookup"><span data-stu-id="21292-109">Data providers can be distributed in one of two ways:</span></span>

1. <span data-ttu-id="21292-110">Add-Ons von Drittanbietern</span><span class="sxs-lookup"><span data-stu-id="21292-110">Third party add-ons</span></span>
1. <span data-ttu-id="21292-111">Teil des Microsoft Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="21292-111">Part of the Microsoft Mixed Reality Toolkit</span></span>

<span data-ttu-id="21292-112">Der Genehmigungsprozess für die Übermittlung neuer Datenanbieter an das MRTK variiert von Fall zu Fall und wird zum Zeitpunkt des ursprünglichen Vorschlags kommuniziert.</span><span class="sxs-lookup"><span data-stu-id="21292-112">The approval process for submissions of new data providers to the MRTK will vary on a case-by-case basis and will be communicated at the time of the initial proposal.</span></span> <span data-ttu-id="21292-113">Vorschläge können übermittelt werden, indem ein neues Problem vom Typ [ *Featureanforderung*](https://github.com/microsoft/MixedRealityToolkit-Unity/issues)erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="21292-113">Proposals can be submitted by creating a new [*Feature Request* type issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span></span>

### <a name="third-party-add-ons"></a><span data-ttu-id="21292-114">Add-Ons von Drittanbietern</span><span class="sxs-lookup"><span data-stu-id="21292-114">Third party add-ons</span></span>

<span data-ttu-id="21292-115">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="21292-115">**Namespace**</span></span>

<span data-ttu-id="21292-116">Datenanbieter müssen über einen Namespace verfügen, um potenzielle Namenskonflikte zu minimieren.</span><span class="sxs-lookup"><span data-stu-id="21292-116">Data providers are required to have a namespace to mitigate potential name collisions.</span></span> <span data-ttu-id="21292-117">Es wird empfohlen, dass der Namespace die folgenden Komponenten enthält.</span><span class="sxs-lookup"><span data-stu-id="21292-117">It is recommended that the namespace includes the following components.</span></span>

- <span data-ttu-id="21292-118">Firmenname, der das Add-On erzeugt</span><span class="sxs-lookup"><span data-stu-id="21292-118">Company name producing the add-on</span></span>
- <span data-ttu-id="21292-119">Featurebereich</span><span class="sxs-lookup"><span data-stu-id="21292-119">Feature area</span></span>

<span data-ttu-id="21292-120">Ein Anbieter für Kameraeinstellungen, der vom Contoso-Unternehmen erstellt und ausgeliefert wird, kann beispielsweise *"Contoso.MixedReality.Toolkit.Camera" sein.*</span><span class="sxs-lookup"><span data-stu-id="21292-120">For example, a camera settings provider created and shipped by the Contoso company may be *"Contoso.MixedReality.Toolkit.Camera"*.</span></span>

<span data-ttu-id="21292-121">**Ordnerstruktur**</span><span class="sxs-lookup"><span data-stu-id="21292-121">**Folder structure**</span></span>

<span data-ttu-id="21292-122">Es wird empfohlen, den Quellcode für Datenanbieter in einer Ordnerhierarchie zu erstellen, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="21292-122">It is recommended that the source code for data providers be layed out in a folder hierarchy as shown in the following image.</span></span>

![Beispiel für die Paketordnerstruktur](../images/camera-system/ExampleProviderFolderStructure.png)

<span data-ttu-id="21292-124">Wenn der Ordner *ContosoCamera* die Implementierung des Datenanbieters enthält, enthält der *Ordner Editor* den Inspektor (und jeglichen anderen Unity-Editor-spezifischen Code), und der Ordner *Profile* enthält ein oder mehrere vorgefertigte Profile, die skriptfähig sind.</span><span class="sxs-lookup"><span data-stu-id="21292-124">Where the *ContosoCamera* folder contains the implementation of the data provider, the *Editor* folder contains the inspector (and any other Unity editor specific code), and the *Profiles* folder contains one or more pre-made profile scriptable objects.</span></span>

### <a name="mrtk-submission"></a><span data-ttu-id="21292-125">MRTK-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="21292-125">MRTK submission</span></span>

<span data-ttu-id="21292-126">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="21292-126">**Namespace**</span></span>

<span data-ttu-id="21292-127">Wenn ein Kameraeinstellungsanbieter an das [Mixed Reality Toolkit-Repository](https://github.com/Microsoft/MixedRealityToolkit-Unity)übermittelt wird, **muss** der Namespace mit Microsoft.MixedReality.Toolkit (z.B. *Microsoft.MixedReality.Toolkit.CameraSystem)* beginnen.</span><span class="sxs-lookup"><span data-stu-id="21292-127">If a camera settings provider is being submitted to the [Mixed Reality Toolkit repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), the namespace **must** begin with Microsoft.MixedReality.Toolkit (ex: *Microsoft.MixedReality.Toolkit.CameraSystem*).</span></span>

<span data-ttu-id="21292-128">**Ordnerstruktur**</span><span class="sxs-lookup"><span data-stu-id="21292-128">**Folder structure**</span></span>

<span data-ttu-id="21292-129">Der gesamte Code muss sich in einem Ordner unter MRTK/Providers (z.B. MRTK/Providers/UnityAR) befinden.</span><span class="sxs-lookup"><span data-stu-id="21292-129">All code must be located in a folder beneath MRTK/Providers (ex: MRTK/Providers/UnityAR).</span></span>

## <a name="define-the-camera-settings-object"></a><span data-ttu-id="21292-130">Definieren des Kameraeinstellungsobjekts</span><span class="sxs-lookup"><span data-stu-id="21292-130">Define the camera settings object</span></span>

<span data-ttu-id="21292-131">Der erste Schritt beim Erstellen eines Kameraeinstellungsanbieters besteht darin, den Typ der Daten (z. B. Gitternetze oder Ebenen) zu bestimmen, die für Anwendungen zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="21292-131">The first step in creating a camera settings provider is determining the type of data (ex: meshes or planes) it will provide to applications.</span></span>

<span data-ttu-id="21292-132">Alle räumlichen Datenobjekte müssen die [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) -Schnittstelle implementieren.</span><span class="sxs-lookup"><span data-stu-id="21292-132">All spatial data objects must implement the [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) interface.</span></span>

## <a name="implement-the-settings-provider"></a><span data-ttu-id="21292-133">Implementieren des Einstellungsanbieters</span><span class="sxs-lookup"><span data-stu-id="21292-133">Implement the settings provider</span></span>

### <a name="specify-interface-andor-base-class-inheritance"></a><span data-ttu-id="21292-134">Angeben der Schnittstellen- und/oder Basisklassenvererbung</span><span class="sxs-lookup"><span data-stu-id="21292-134">Specify interface and/or base class inheritance</span></span>

<span data-ttu-id="21292-135">Alle Kameraeinstellungsanbieter müssen die [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) -Schnittstelle implementieren, die die mindest erforderliche Funktionalität des Kamerasystems angibt.</span><span class="sxs-lookup"><span data-stu-id="21292-135">All camera settings providers must implement the [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) interface, which specifies the minimum functionality required by the camera system.</span></span> <span data-ttu-id="21292-136">Die MRTK-Grundlage enthält die [`BaseCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider) -Klasse, die eine Standardimplementierung der erforderlichen Funktionalität bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="21292-136">The MRTK foundation includes the [`BaseCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider) class which provides a default implementation of the required functionality.</span></span>

```c#
namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    public class UnityARCameraSettings : BaseCameraSettingsProvider
    { }
}
```

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a><span data-ttu-id="21292-137">Anwenden des MixedRealityDataProvider-Attributs</span><span class="sxs-lookup"><span data-stu-id="21292-137">Apply the MixedRealityDataProvider attribute</span></span>

<span data-ttu-id="21292-138">Ein wichtiger Schritt beim Erstellen eines Kameraeinstellungsanbieters besteht darin, das [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) -Attribut auf die -Klasse anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="21292-138">A key step in creating a camera settings provider is to apply the [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) attribute to the class.</span></span> <span data-ttu-id="21292-139">Mit diesem Schritt können Sie das Standardprofil und die Plattformen für den Datenanbieter festlegen, wenn sie im Kamerasystemprofil ausgewählt sind, sowie Name, Ordnerpfad usw.</span><span class="sxs-lookup"><span data-stu-id="21292-139">This step enables setting the default profile and platform(s) for the data provider, when selected in the Camera System profile as well as name, folder path, and more.</span></span>

```c#
    [MixedRealityDataProvider(
        typeof(IMixedRealityCameraSystem),
        SupportedPlatforms.Android | SupportedPlatforms.IOS,
        "Unity AR Foundation Camera Settings",
        "UnityAR/Profiles/DefaultUnityARCameraSettingsProfile.asset",
        "MixedRealityToolkit.Providers")]
    public class UnityARCameraSettings : BaseCameraSettingsProvider
    { }
```

### <a name="implement-the-imixedrealitydataprovider-methods"></a><span data-ttu-id="21292-140">Implementieren der IMixedRealityDataProvider-Methoden</span><span class="sxs-lookup"><span data-stu-id="21292-140">Implement the IMixedRealityDataProvider methods</span></span>

<span data-ttu-id="21292-141">Nachdem die -Klasse definiert wurde, besteht der nächste Schritt darin, die Implementierung der [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) -Schnittstelle bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="21292-141">Once the class has been defined, the next step is to provide the implementation of the [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span></span>

> [!NOTE]
> <span data-ttu-id="21292-142">Die [`BaseDataProvider`](xref:Microsoft.MixedReality.Toolkit.BaseDataProvider`1) -Klasse stellt über die [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) -Klasse leere Implementierungen für [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) Methoden bereit.</span><span class="sxs-lookup"><span data-stu-id="21292-142">The [`BaseDataProvider`](xref:Microsoft.MixedReality.Toolkit.BaseDataProvider`1) class, via the [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) class, provides empty implementations for [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) methods.</span></span> <span data-ttu-id="21292-143">Die Details dieser Methoden sind im Allgemeinen datenanbieterspezifisch.</span><span class="sxs-lookup"><span data-stu-id="21292-143">The details of these methods are generally data provider specific.</span></span>

<span data-ttu-id="21292-144">Der Datenanbieter sollte folgende Methoden implementieren:</span><span class="sxs-lookup"><span data-stu-id="21292-144">The methods that should be implemented by the data provider are:</span></span>

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

> [!NOTE]
> <span data-ttu-id="21292-145">Nicht alle Einstellungsanbieter erfordern Implementierungen für alle diese Methoden.</span><span class="sxs-lookup"><span data-stu-id="21292-145">Not all settings providers will require implementations for all of these methods.</span></span> <span data-ttu-id="21292-146">Es wird dringend empfohlen, `Destroy()` dass und mindestens implementiert `Initialize()` werden.</span><span class="sxs-lookup"><span data-stu-id="21292-146">It is highly recommended that `Destroy()` and `Initialize()` be implemented at a minimum.</span></span>

### <a name="implement-the-data-provider-logic"></a><span data-ttu-id="21292-147">Implementieren der Datenanbieterlogik</span><span class="sxs-lookup"><span data-stu-id="21292-147">Implement the data provider logic</span></span>

<span data-ttu-id="21292-148">Im nächsten Schritt fügen Sie die Logik des Einstellungsanbieters hinzu, indem Sie [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) implementieren.</span><span class="sxs-lookup"><span data-stu-id="21292-148">The next step is to add the logic of the settings provider by implementing [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider).</span></span> <span data-ttu-id="21292-149">Dieser Teil des Datenanbieters ist in der Regel kamerakonfigurationsspezifisch.</span><span class="sxs-lookup"><span data-stu-id="21292-149">This portion of the data provider will typically be camera configuration specific.</span></span>

## <a name="create-the-profile-and-inspector"></a><span data-ttu-id="21292-150">Erstellen des Profils und des Inspektors</span><span class="sxs-lookup"><span data-stu-id="21292-150">Create the profile and inspector</span></span>

<span data-ttu-id="21292-151">Im Mixed Reality Toolkit werden Datenanbieter mithilfe von [Profilen](../profiles/profiles.md)konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="21292-151">In the Mixed Reality Toolkit, data providers are configured using [profiles](../profiles/profiles.md).</span></span>

### <a name="define-the-profile"></a><span data-ttu-id="21292-152">Definieren des Profils</span><span class="sxs-lookup"><span data-stu-id="21292-152">Define the profile</span></span>

<span data-ttu-id="21292-153">Profilinhalte sollten die vom Entwickler auswählbaren Konfigurationsoptionen widerspiegeln.</span><span class="sxs-lookup"><span data-stu-id="21292-153">Profile contents should mirror the developer selectable configuration options.</span></span> <span data-ttu-id="21292-154">Alle vom Benutzer konfigurierbaren Eigenschaften, die in jeder Schnittstelle definiert sind, sollten auch im Profil enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="21292-154">Any user configurable properties defined in each interface should also be contained with the profile.</span></span>

```c#
using UnityEngine.SpatialTracking;

namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    [CreateAssetMenu(
        menuName = "Mixed Reality Toolkit/Profiles/Unity AR Camera Settings Profile",
        fileName = "UnityARCameraSettingsProfile",
        order = 100)]
    public class UnityARCameraSettingsProfile : BaseCameraSettingsProfile
    {
        [SerializeField]
        [Tooltip("The portion of the device (ex: color camera) from which to read the pose.")]
        private ArTrackedPose poseSource = TrackedPoseDriver.TrackedPose.ColorCamera;

        /// <summary>
        /// The portion of the device (ex: color camera) from which to read the pose.
        /// </summary>
        public ArTrackedPose PoseSource => poseSource;

        [SerializeField]
        [Tooltip("The type of tracking (position and/or rotation) to apply.")]
        private ArTrackingType trackingType = TrackedPoseDriver.TrackingType.RotationAndPosition;

        /// <summary>
        /// The type of tracking (position and/or rotation) to apply.
        /// </summary>
        public ArTrackingType TrackingType => trackingType;

        [SerializeField]
        [Tooltip("Specifies when (during Update and/or just before rendering) to update the tracking of the pose.")]
        private ArUpdateType updateType = TrackedPoseDriver.UpdateType.UpdateAndBeforeRender;

        /// <summary>
        /// Specifies when (during Update and/or just before rendering) to update the tracking of the pose.
        /// </summary>
        public ArUpdateType UpdateType => updateType;
    }
}
```

<span data-ttu-id="21292-155">Das `CreateAssetMenu` -Attribut kann auf die Profilklasse angewendet werden, damit Kunden mithilfe des  >  Menüs **Objekte**  >  **Mixed Reality Toolkitprofile** erstellen eine Profilinstanz erstellen  >   können.</span><span class="sxs-lookup"><span data-stu-id="21292-155">The `CreateAssetMenu` attribute can be applied to the profile class to enable customers to create a profile instance using the **Create** > **Assets** > **Mixed Reality Toolkit** > **Profiles** menu.</span></span>

### <a name="implement-the-inspector"></a><span data-ttu-id="21292-156">Implementieren des Inspektors</span><span class="sxs-lookup"><span data-stu-id="21292-156">Implement the inspector</span></span>

<span data-ttu-id="21292-157">Profilinspektoren sind die Benutzeroberfläche zum Konfigurieren und Anzeigen von Profilinhalten.</span><span class="sxs-lookup"><span data-stu-id="21292-157">Profile inspectors are the user interface for configuring and viewing profile contents.</span></span> <span data-ttu-id="21292-158">Jeder Profilinspektor sollte die [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) -Klasse erweitern.</span><span class="sxs-lookup"><span data-stu-id="21292-158">Each profile inspector should extend the [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) class.</span></span>

<span data-ttu-id="21292-159">Das `CustomEditor` -Attribut informiert Unity über den Typ des Medienobjekts, für das der Inspektor gilt.</span><span class="sxs-lookup"><span data-stu-id="21292-159">The `CustomEditor` attribute informs Unity the type of asset to which the inspector applies.</span></span>

```c#
namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    [CustomEditor(typeof(UnityARCameraSettingsProfile))]
    public class UnityARCameraSettingsProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
    { }
}
```

## <a name="create-assembly-definitions"></a><span data-ttu-id="21292-160">Erstellen von Assemblydefinitionen</span><span class="sxs-lookup"><span data-stu-id="21292-160">Create assembly definition(s)</span></span>

<span data-ttu-id="21292-161">Das Mixed Reality Toolkit verwendet Assemblydefinitionsdateien[(ASMDEF-Dateien),](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)um Abhängigkeiten zwischen Komponenten anzugeben und Unity bei der Reduzierung der Kompilierungszeit zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="21292-161">The Mixed Reality Toolkit uses assembly definition ([.asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) files to specify dependencies between components as well as to assist Unity in reducing compilation time.</span></span>

<span data-ttu-id="21292-162">Es wird empfohlen, Assemblydefinitionsdateien für alle Datenanbieter und deren Editorkomponenten zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="21292-162">It is recommended that assembly definition files are created for all data providers and their editor components.</span></span>

<span data-ttu-id="21292-163">Wenn Sie die [Ordnerstruktur](#namespace-and-folder-structure) im vorherigen Beispiel verwenden, gibt es zwei ASMDEF-Dateien für den ContosoCamera-Datenanbieter.</span><span class="sxs-lookup"><span data-stu-id="21292-163">Using the [folder structure](#namespace-and-folder-structure) in the earlier example, there would be two .asmdef files for the ContosoCamera data provider.</span></span>

<span data-ttu-id="21292-164">Die erste Assemblydefinition ist für den Datenanbieter.</span><span class="sxs-lookup"><span data-stu-id="21292-164">The first assembly definition is for the data provider.</span></span> <span data-ttu-id="21292-165">In diesem Beispiel heißt sie ContosoCamera und befindet sich im Ordner *ContosoCamera* des Beispiels.</span><span class="sxs-lookup"><span data-stu-id="21292-165">For this example, it will be called ContosoCamera and will be located in the example's *ContosoCamera* folder.</span></span> <span data-ttu-id="21292-166">Diese Assemblydefinition muss eine Abhängigkeit von Microsoft.MixedReality.Toolkit und allen anderen Assemblys angeben, von denen sie abhängt.</span><span class="sxs-lookup"><span data-stu-id="21292-166">This assembly definition must specify a dependency on Microsoft.MixedReality.Toolkit and any other assemblies upon which it depends.</span></span>

<span data-ttu-id="21292-167">Die Assemblydefinition ContosoCameraEditor gibt den Profilinspektor und jeden editorspezifischen Code an.</span><span class="sxs-lookup"><span data-stu-id="21292-167">The ContosoCameraEditor assembly definition will specify the profile inspector and any editor specific code.</span></span> <span data-ttu-id="21292-168">Diese Datei muss sich im Stammordner des Editorcodes befinden.</span><span class="sxs-lookup"><span data-stu-id="21292-168">This file must be located in the root folder of the editor code.</span></span> <span data-ttu-id="21292-169">In diesem Beispiel befindet sich die Datei im Ordner *ContosoCamera\Editor.*</span><span class="sxs-lookup"><span data-stu-id="21292-169">In this example, the file will be located in the *ContosoCamera\Editor* folder.</span></span> <span data-ttu-id="21292-170">Diese Assemblydefinition enthält einen Verweis auf die ContosoCamera-Assembly sowie:</span><span class="sxs-lookup"><span data-stu-id="21292-170">This assembly definition will contain a reference to the ContosoCamera assembly as well as:</span></span>

- <span data-ttu-id="21292-171">Microsoft.MixedReality.Toolkit</span><span class="sxs-lookup"><span data-stu-id="21292-171">Microsoft.MixedReality.Toolkit</span></span>
- <span data-ttu-id="21292-172">Microsoft.MixedReality.Toolkit.Editor.Inspectors</span><span class="sxs-lookup"><span data-stu-id="21292-172">Microsoft.MixedReality.Toolkit.Editor.Inspectors</span></span>
- <span data-ttu-id="21292-173">Microsoft.MixedReality.Toolkit.Editor.Utilities</span><span class="sxs-lookup"><span data-stu-id="21292-173">Microsoft.MixedReality.Toolkit.Editor.Utilities</span></span>

## <a name="register-the-data-provider"></a><span data-ttu-id="21292-174">Registrieren des Datenanbieters</span><span class="sxs-lookup"><span data-stu-id="21292-174">Register the data provider</span></span>

<span data-ttu-id="21292-175">Nach der Erstellung kann der Datenanbieter beim Kamerasystem registriert werden, das in der Anwendung verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="21292-175">Once created, the data provider can be registered with the Camera system to be used in the application.</span></span>

![Auswählen des Anbieters für Kameraeinstellungen](../images/camera-system/SelectUnityArSettings.png)

## <a name="packaging-and-distribution"></a><span data-ttu-id="21292-177">Verpacken und Verteilen</span><span class="sxs-lookup"><span data-stu-id="21292-177">Packaging and distribution</span></span>

<span data-ttu-id="21292-178">Datenanbieter, die als Drittanbieterkomponenten verteilt werden, verfügen über die spezifischen Details der Paketierung und Verteilung, die dem Entwickler überlassen werden.</span><span class="sxs-lookup"><span data-stu-id="21292-178">Data providers that are distributed as third party components have the specific details of packaging and distribution left to the preference of the developer.</span></span> <span data-ttu-id="21292-179">Wahrscheinlich ist die gängigste Lösung die Generierung eines UNITYPACKAGE-Pakets und das Verteilen über das Unity-Medienobjekt Store.</span><span class="sxs-lookup"><span data-stu-id="21292-179">Likely, the most common solution will be to generate a .unitypackage and distribute via the Unity Asset Store.</span></span>

<span data-ttu-id="21292-180">Wenn ein Datenanbieter als Teil des Microsoft Mixed Reality Toolkit-Pakets übermittelt und akzeptiert wird, packt und verteilt das Microsoft MRTK-Team ihn im Rahmen der MRTK-Angebote.</span><span class="sxs-lookup"><span data-stu-id="21292-180">If a data provider is submitted and accepted as a part of the Microsoft Mixed Reality Toolkit package, the Microsoft MRTK team will package and distribute it as part of the MRTK offerings.</span></span>

## <a name="see-also"></a><span data-ttu-id="21292-181">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="21292-181">See also</span></span>

- [<span data-ttu-id="21292-182">Übersicht über das Kamerasystem</span><span class="sxs-lookup"><span data-stu-id="21292-182">Camera System Overview</span></span>](camera-system-overview.md)
- [<span data-ttu-id="21292-183">`BaseCameraSettingsProvider`-Klasse</span><span class="sxs-lookup"><span data-stu-id="21292-183">`BaseCameraSettingsProvider` class</span></span>](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider)
- [<span data-ttu-id="21292-184">`IMixedRealityCameraSettingsProvider` Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="21292-184">`IMixedRealityCameraSettingsProvider` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider)
- [<span data-ttu-id="21292-185">`IMixedRealityDataProvider` Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="21292-185">`IMixedRealityDataProvider` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
