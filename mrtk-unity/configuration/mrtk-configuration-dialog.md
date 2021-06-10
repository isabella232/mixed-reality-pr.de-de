---
title: MRTK-Konfigurationsdialogfeld
description: Konfigurieren von MRTK im Unity-Projekt
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Unity
ms.openlocfilehash: fd05f7f3b579522a1225e11b0411b255a43e1e3f
ms.sourcegitcommit: bb9f54f3e872a5464a5d9ba88b7ab5b8896efd82
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2021
ms.locfileid: "110345093"
---
# <a name="mrtk-project-configuration-dialog"></a><span data-ttu-id="96f06-104">MRTK-Projektkonfigurationsdialogfeld</span><span class="sxs-lookup"><span data-stu-id="96f06-104">MRTK project configuration dialog</span></span>

<span data-ttu-id="96f06-105">Das MRTK-Konfigurationsdialogfeld wird angezeigt, wenn Unity ein Projekt lädt, und es wird festgestellt, dass eine oder mehrere Konfigurationsoptionen die Aufmerksamkeit des Entwicklers erfordern.</span><span class="sxs-lookup"><span data-stu-id="96f06-105">The MRTK configuration dialog is displayed when Unity loads a project and it is determined that one or more configuration options needs the attention of the developer.</span></span>

![Später anwenden Ignorieren](../features/images/configuration-dialog/ConfigurationDialogHeader.png)

<span data-ttu-id="96f06-107">Klicken Sie auf die Schaltfläche **Übernehmen,** um die Änderungen zu übernehmen.</span><span class="sxs-lookup"><span data-stu-id="96f06-107">To apply the changes, click the **Apply** button.</span></span> <span data-ttu-id="96f06-108">Mit der Schaltfläche **Später** werden die Änderungen zurückgesetzt, bis das Projekt zu einem späteren Zeitpunkt erneut geladen wird.</span><span class="sxs-lookup"><span data-stu-id="96f06-108">The **Later** button will defer the changes until the project is reloaded at a future time.</span></span>

> [!NOTE]
> <span data-ttu-id="96f06-109">Das Konfigurationsdialogfeld wird erneut angezeigt, wenn mindestens eine der empfohlenen Einstellungen deaktiviert bleibt.</span><span class="sxs-lookup"><span data-stu-id="96f06-109">The configuration dialog will reappear if one or more of the recommended settings is left unchecked.</span></span> <span data-ttu-id="96f06-110">Um dies zu verhindern, wenden Sie die gewünschten Optionen an, starten Sie dann das Dialogfeld über **Mixed Reality**  >  **Toolkit-Hilfsprogramme**  >  **Unity-Projekt konfigurieren** neu, und klicken Sie auf **Ignorieren.**</span><span class="sxs-lookup"><span data-stu-id="96f06-110">To prevent this from occurring, apply the desired options, then relaunch the dialog via  **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** and click **Ignore**.</span></span> <span data-ttu-id="96f06-111">Dadurch wird verhindert, dass das Konfigurationsdialogfeld automatisch erneut angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="96f06-111">This will prevent the configuration dialog from reappearing automatically.</span></span>

## <a name="common-settings"></a><span data-ttu-id="96f06-112">Allgemeine Einstellungen</span><span class="sxs-lookup"><span data-stu-id="96f06-112">Common settings</span></span>

<span data-ttu-id="96f06-113">Alle Buildziele teilen sich eine Sammlung allgemeiner Optionen.</span><span class="sxs-lookup"><span data-stu-id="96f06-113">All build targets share a collection of common options.</span></span>

![Allgemeine Einstellungen](../features/images/configuration-dialog/ConfigurationDialogCommonSettings.png)

### <a name="force-text-asset-serialization-and-enable-visible-meta-files"></a><span data-ttu-id="96f06-115">Erzwingen der Serialisierung von Textobjekten und Aktivieren sichtbarer Metadateien</span><span class="sxs-lookup"><span data-stu-id="96f06-115">Force text asset serialization and Enable visible meta files</span></span>

<span data-ttu-id="96f06-116">Diese Einstellungen vereinfachen die Arbeit mit Unity-Projekten und Quellcodeverwaltungssystemen (z. B. Git).</span><span class="sxs-lookup"><span data-stu-id="96f06-116">These settings help simplify working with Unity projects and source control systems (ex: Git).</span></span>

### <a name="enable-vr-supported"></a><span data-ttu-id="96f06-117">Vr-Unterstützung aktivieren</span><span class="sxs-lookup"><span data-stu-id="96f06-117">Enable VR supported</span></span>

<span data-ttu-id="96f06-118">**Unity 2018**</span><span class="sxs-lookup"><span data-stu-id="96f06-118">**Unity 2018**</span></span>

<span data-ttu-id="96f06-119">Konfiguriert die Optionen Virtual Reality Supported und Virtual Reality SDK unter **Player Settings**  >  **XR Settings (XR-Einstellungen für Playereinstellungen).**</span><span class="sxs-lookup"><span data-stu-id="96f06-119">Configures the Virtual Reality Supported and Virtual Reality SDK options in **Player Settings** > **XR Settings**.</span></span>

### <a name="set-single-pass-instanced-rendering-path"></a><span data-ttu-id="96f06-120">Festlegen des Renderingpfads "Single Pass Instanced"</span><span class="sxs-lookup"><span data-stu-id="96f06-120">Set Single Pass Instanced rendering path</span></span>

<span data-ttu-id="96f06-121">Konfiguriert den   >    >  **XR Settings Stereo Rendering Mode (XR-Renderingmodus** für Playereinstellungen) auf **Single Pass Instanced (Einzeldurchlaufinstanz).**</span><span class="sxs-lookup"><span data-stu-id="96f06-121">Configures the **Player Settings** > **XR Settings** > **Stereo Rendering Mode** to **Single Pass Instanced**.</span></span>

### <a name="set-default-spatial-awareness-layer"></a><span data-ttu-id="96f06-122">Festlegen der Standardebene für räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="96f06-122">Set default Spatial Awareness layer</span></span>

<span data-ttu-id="96f06-123">Registriert räumliche Wahrnehmung als Ebene 31, um eine einfache und konsistente Konfiguration von Raycast- und Physikalischen Optionen zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="96f06-123">Registers Spatial Awareness as layer 31 to enable easy and consistent configuration of raycast and physics options.</span></span>

### <a name="audio-spatializer"></a><span data-ttu-id="96f06-124">Audio spatializer</span><span class="sxs-lookup"><span data-stu-id="96f06-124">Audio spatializer</span></span>

<span data-ttu-id="96f06-125">Audio spatializers sind die Komponenten, die die Leistungsfähigkeit von Räumlichem Sound und Positionsaudio nutzen, um Mixed Reality-Erfahrungen wirklich immersiver zu gestalten.</span><span class="sxs-lookup"><span data-stu-id="96f06-125">Audio spatializers are the components that unlock the power of Spatial Sound and positional audio to make mixed reality experiences truly immersive.</span></span>

> [!NOTE]
> <span data-ttu-id="96f06-126">Wenn Sie den Audio spatializer auf None festlegen, werden die Positionsaudiofeatures deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="96f06-126">Setting the audio spatializer to None will disable positional audio features.</span></span>

#### <a name="common-spatializers"></a><span data-ttu-id="96f06-127">Allgemeine Spatializer</span><span class="sxs-lookup"><span data-stu-id="96f06-127">Common spatializers</span></span>

- <span data-ttu-id="96f06-128">Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="96f06-128">Microsoft Spatializer</span></span>

<span data-ttu-id="96f06-129">Microsoft hat einen Spatializer bereitgestellt, der die Nutzung der Hardwarebeschleunigung auf HoloLens 2 unterstützt.</span><span class="sxs-lookup"><span data-stu-id="96f06-129">Microsoft provided spatializer that supports utilization of hardware acceleration on HoloLens 2.</span></span>

<span data-ttu-id="96f06-130">Dieser Spatializer ist über [NuGet](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/) und [GitHub](https://github.com/microsoft/spatialaudio-unity)verfügbar.</span><span class="sxs-lookup"><span data-stu-id="96f06-130">This spatializer is available via [NuGet](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/) and [GitHub](https://github.com/microsoft/spatialaudio-unity).</span></span>

<span data-ttu-id="96f06-131">Weitere Informationen zu Microsoft Spatializer finden Sie in der [Spatial Sound-Dokumentation.](/windows/mixed-reality/spatial-sound-in-unity)</span><span class="sxs-lookup"><span data-stu-id="96f06-131">More details on Microsoft Spatializer can be found in the [Spatial Sound documentation](/windows/mixed-reality/spatial-sound-in-unity).</span></span>

- <span data-ttu-id="96f06-132">MS HRTF Spatializer</span><span class="sxs-lookup"><span data-stu-id="96f06-132">MS HRTF Spatializer</span></span>

<span data-ttu-id="96f06-133">Microsoft Windows Spatializer, der von Unity als Teil der Pakete Windows Mixed Reality und Windows XR Platform bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="96f06-133">Microsoft Windows spatializer that is provided by Unity as part of the Windows Mixed Reality and Windows XR Platform packages.</span></span>

- <span data-ttu-id="96f06-134">Audioaudio</span><span class="sxs-lookup"><span data-stu-id="96f06-134">Resonance Audio</span></span>

<span data-ttu-id="96f06-135">Ein plattformübergreifender Spatializer von Google, der von Unity bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="96f06-135">A cross platform spatializer from Google that is provided by Unity.</span></span>

<span data-ttu-id="96f06-136">Weitere Informationen finden Sie auf der [Dokumentationswebsite für die Audiodokumentation.](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started)</span><span class="sxs-lookup"><span data-stu-id="96f06-136">More information can be found on the [Resonance Audio documentation](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started) site.</span></span>

## <a name="universal-windows-platform-settings"></a><span data-ttu-id="96f06-137">Universelle Windows-Plattform-Einstellungen</span><span class="sxs-lookup"><span data-stu-id="96f06-137">Universal Windows Platform settings</span></span>

![UWP-Einstellungen](../features/images/configuration-dialog/ConfigurationDialogUWPSettings.png)

### <a name="uwp-capabilities"></a><span data-ttu-id="96f06-139">UWP-Funktionen</span><span class="sxs-lookup"><span data-stu-id="96f06-139">UWP Capabilities</span></span>

<span data-ttu-id="96f06-140">Aktiviert bestimmte Anwendungsfunktionen für Universelle Windows-Plattform Anwendung.</span><span class="sxs-lookup"><span data-stu-id="96f06-140">Enables specific application capabilities for Universal Windows Platform application.</span></span> <span data-ttu-id="96f06-141">Mit diesen Funktionen kann die Plattform informieren und die Berechtigung anfordern, um bestimmte Funktionen zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="96f06-141">These capabilities enable the platform to inform and request permission to enable specific functionality.</span></span>

- <span data-ttu-id="96f06-142">Mikrofon</span><span class="sxs-lookup"><span data-stu-id="96f06-142">Microphone</span></span>

  <span data-ttu-id="96f06-143">Ermöglicht die Erfassung von Sound über das Mikrofon.</span><span class="sxs-lookup"><span data-stu-id="96f06-143">Enables capturing sound via the microphone.</span></span>

- <span data-ttu-id="96f06-144">Internetclient</span><span class="sxs-lookup"><span data-stu-id="96f06-144">Internet Client</span></span>

  <span data-ttu-id="96f06-145">Ermöglicht die Unterstützung für den Zugriff auf Ressourcen im Internet.</span><span class="sxs-lookup"><span data-stu-id="96f06-145">Enables support for accessing resources on the internet.</span></span>

- <span data-ttu-id="96f06-146">Räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="96f06-146">Spatial Perception</span></span>

  <span data-ttu-id="96f06-147">Ermöglicht die Unterstützung für die Verwendung der realen Umgebung.</span><span class="sxs-lookup"><span data-stu-id="96f06-147">Enables support for using the real-world environment.</span></span>

- <span data-ttu-id="96f06-148">Anväuten mit den Augen</span><span class="sxs-lookup"><span data-stu-id="96f06-148">Eye Gaze</span></span>

  <span data-ttu-id="96f06-149">**Unity 2019.3 und neuer**</span><span class="sxs-lookup"><span data-stu-id="96f06-149">**Unity 2019.3 and newer**</span></span>

  <span data-ttu-id="96f06-150">Ermöglicht die Unterstützung für die Nachverfolgung des Anverfolgens der Augen des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="96f06-150">Enables support for tracking the user's eye gaze.</span></span>

### <a name="avoid-unity-playersettingsgraphicsjob-crash"></a><span data-ttu-id="96f06-151">Vermeiden des Absturzes von Unity "PlayerSettings.graphicsJob"</span><span class="sxs-lookup"><span data-stu-id="96f06-151">Avoid Unity 'PlayerSettings.graphicsJob' crash</span></span>

<span data-ttu-id="96f06-152">**Unity 2019.3 und neuer**</span><span class="sxs-lookup"><span data-stu-id="96f06-152">**Unity 2019.3 and newer**</span></span>

<span data-ttu-id="96f06-153">In der neuesten Version von Unity 2019 stürzt die App ab, wenn "Grafikaufträge" aktiviert ist, wenn sie auf einem HoloLens 2 bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="96f06-153">In the latest version of Unity 2019, when "Graphics Jobs" is enabled, the app will crash when deployed to a HoloLens 2.</span></span>
<span data-ttu-id="96f06-154">Diese Einstellung ist in Unity standardmäßig aktiviert. Während dieser Fehler vorhanden ist (siehe [Unity-Fehler),](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)legt der Konfigurator standardmäßig Grafikaufträge auf "false" fest (sodass Apps, die für HoloLens 2 bereitgestellt wurden, nicht abstürzten).</span><span class="sxs-lookup"><span data-stu-id="96f06-154">This setting is enabled by default in Unity - while this bug exists (see [Unity bug](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)), the configurator will default to setting Graphics Jobs to 'false' (thus allowing apps deployed to HoloLens 2 not to crash).</span></span>

## <a name="android-settings"></a><span data-ttu-id="96f06-155">Einstellungen für Android</span><span class="sxs-lookup"><span data-stu-id="96f06-155">Android settings</span></span>

<span data-ttu-id="96f06-156">Konfigurationseinstellungen zur Unterstützung von AR-Anwendungen auf Android-Geräten.</span><span class="sxs-lookup"><span data-stu-id="96f06-156">Configuration settings to support AR applications on Android powered devices.</span></span>

![Android-Einstellungen](../features/images/configuration-dialog/ConfigurationDialogAndroidSettings.png)

### <a name="disable-multi-threaded-rendering"></a><span data-ttu-id="96f06-158">Deaktivieren des Multithread-Renderings</span><span class="sxs-lookup"><span data-stu-id="96f06-158">Disable Multi-Threaded Rendering</span></span>

<span data-ttu-id="96f06-159">Deaktiviert **player settings**  >  **Other Settings**  >  **Multithreaded Rendering (Weitere Einstellungen für Multithread-Rendering),** wie dies für die AR-Unterstützung von Android erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="96f06-159">Disables **Player Settings** > **Other Settings** > **Multithreaded Rendering** as required by Android's AR support.</span></span>

### <a name="set-minimum-api-level"></a><span data-ttu-id="96f06-160">Festlegen der API-Mindestebene</span><span class="sxs-lookup"><span data-stu-id="96f06-160">Set Minimum API Level</span></span>

<span data-ttu-id="96f06-161">Legt den Wert von **Player Settings**  >  **Other Settings** Minimum API Level  >  fest, um Betriebssystemanforderungen für **AR-Anwendungen** zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="96f06-161">Sets the value of **Player Settings** > **Other Settings** > **Minimum API Level** to enforce operating system requirements for AR applications.</span></span>

## <a name="ios-settings"></a><span data-ttu-id="96f06-162">Einstellungen für iOS</span><span class="sxs-lookup"><span data-stu-id="96f06-162">iOS settings</span></span>

<span data-ttu-id="96f06-163">Konfigurationseinstellungen zur Unterstützung von AR-Anwendungen auf iOS-geräten.</span><span class="sxs-lookup"><span data-stu-id="96f06-163">Configuration settings to support AR applications on iOS powered devices.</span></span>

![iOS-Einstellungen](../features/images/configuration-dialog/ConfigurationDialogiOSSettings.png)

### <a name="set-required-os-version"></a><span data-ttu-id="96f06-165">Festlegen der erforderlichen Betriebssystemversion</span><span class="sxs-lookup"><span data-stu-id="96f06-165">Set Required OS Version</span></span>

<span data-ttu-id="96f06-166">Legt den Wert von **Playereinstellungen**  >  **Andere Einstellungen** Auf die  >  **iOS-Mindestversion** fest, um Betriebssystemanforderungen für AR-Anwendungen zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="96f06-166">Sets the value of **Player Settings** > **Other Settings** > **Target minimum iOS Version** to enforce operating system requirements for AR applications.</span></span>

### <a name="set-required-architecture"></a><span data-ttu-id="96f06-167">Festlegen der erforderlichen Architektur</span><span class="sxs-lookup"><span data-stu-id="96f06-167">Set Required Architecture</span></span>

<span data-ttu-id="96f06-168">Legt den Wert von Andere Einstellungsarchitektur für **Playereinstellungen**  >    >   fest, um Plattformanforderungen für AR-Anwendungen zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="96f06-168">Sets the value of **Player Settings** > **Other Settings** > **Architecture** to enforce platform requirements for AR applications.</span></span>

### <a name="set-camera-usage-descriptions"></a><span data-ttu-id="96f06-169">Festlegen von Kameranutzungsbeschreibungen</span><span class="sxs-lookup"><span data-stu-id="96f06-169">Set Camera Usage Descriptions</span></span>

<span data-ttu-id="96f06-170">Legt den Wert von **Playereinstellungen**  >  **Andere Einstellungen**  >  **Kameraverwendungsbeschreibung** fest, die verwendet wird, um die Berechtigung zum Verwenden der Kamera des Geräts anzufordern.</span><span class="sxs-lookup"><span data-stu-id="96f06-170">Sets the value of **Player Settings** > **Other Settings** > **Camera Usage Description** used to request permission to use the device's camera.</span></span>