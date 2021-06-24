---
title: Mixed Reality-Konfigurationshandbuch
description: Dokumentation zum Konfigurieren des MRTK in Unity.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: a8aca05b4a4bc154061d6f7594e5128ab91d5f0e
ms.sourcegitcommit: c08997a75acfe4ac1d044c0fb9112e6817eb3d45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/24/2021
ms.locfileid: "112588865"
---
# <a name="mixed-reality-toolkit-profile-configuration-guide"></a><span data-ttu-id="8310f-104">Mixed Reality Toolkit für die Profilkonfiguration</span><span class="sxs-lookup"><span data-stu-id="8310f-104">Mixed Reality Toolkit profile configuration guide</span></span>

<span data-ttu-id="8310f-105">Das Mixed Reality Toolkit zentralisiert so viel wie möglich der Konfiguration, die für die Verwaltung des Toolkits erforderlich ist (mit Ausnahme echter Runtime-"Dinge").</span><span class="sxs-lookup"><span data-stu-id="8310f-105">The Mixed Reality Toolkit centralizes as much of the configuration required to manage the toolkit as possible (except for true runtime "things").</span></span>

<span data-ttu-id="8310f-106">Dieser Leitfaden ist eine einfache exemplarische Vorgehensweise für jeden der Konfigurationsprofilbildschirme, die derzeit für das Toolkit verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="8310f-106">This guide is a simple walkthrough for each of the configuration profile screens currently available for the toolkit.</span></span>

## <a name="the-main-mixed-reality-toolkit-configuration-profile"></a><span data-ttu-id="8310f-107">Das Hauptkonfigurationsprofil Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="8310f-107">The main Mixed Reality Toolkit configuration profile</span></span>

<span data-ttu-id="8310f-108">Das Hauptkonfigurationsprofil, das an *das MixedRealityToolkit* GameObject in Ihrer Szene angefügt ist, stellt den Haupteinstiegspunkt für das Toolkit in Ihrem Projekt bereit.</span><span class="sxs-lookup"><span data-stu-id="8310f-108">The main configuration profile, which is attached to the *MixedRealityToolkit* GameObject in your Scene, provides the main entry point for the Toolkit in your project.</span></span>

> [!NOTE]
> <span data-ttu-id="8310f-109">Das Mixed Reality Toolkit sperrt die Standardkonfigurationsbildschirme, um sicherzustellen, dass Sie immer über einen gemeinsamen Startpunkt für Ihr Projekt verfügen, und es wird empfohlen, mit der Definition eigener Einstellungen zu beginnen, während Sich Ihr Projekt weiterentwickelt.</span><span class="sxs-lookup"><span data-stu-id="8310f-109">The Mixed Reality Toolkit "locks" the default configuration screens to ensure you always have a common start point for your project and it is encouraged to start defining your own settings as your project evolves.</span></span> <span data-ttu-id="8310f-110">Die MRTK-Konfiguration kann während des Wiedergabemodus nicht bearbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="8310f-110">The MRTK configuration is not editable during play-mode.</span></span>

![MRTK-Konfigurationsprofil](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ActiveConfiguration.png)

<span data-ttu-id="8310f-112">Alle Standardprofile für das Mixed Reality Toolkit finden Sie im SDK-Projekt im Ordner Assets/MRTK/SDK/Profiles.</span><span class="sxs-lookup"><span data-stu-id="8310f-112">All the "default" profiles for the Mixed Reality Toolkit can be found in the SDK project in the folder Assets/MRTK/SDK/Profiles.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8310f-113">DefaultHoloLens2ConfigurationProfile ist für HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="8310f-113">DefaultHoloLens2ConfigurationProfile is optimized for HoloLens 2.</span></span> <span data-ttu-id="8310f-114">Weitere [Informationen finden](../features/profiles/profiles.md) Sie unter Profile.</span><span class="sxs-lookup"><span data-stu-id="8310f-114">See [Profiles](../features/profiles/profiles.md) for the details.</span></span>

<span data-ttu-id="8310f-115">Wenn Sie das Hauptkonfigurationsprofil Mixed Reality Toolkit öffnen, wird der folgende Bildschirm im Inspektor angezeigt:</span><span class="sxs-lookup"><span data-stu-id="8310f-115">When you open the main Mixed Reality Toolkit Configuration Profile, you will see the following screen in the inspector:</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_MixedRealityToolkitConfigurationScreen.png" width="650px" alt="MRTK configuration scene" style="display:block;">

<span data-ttu-id="8310f-116">Wenn Sie ein MixedRealityToolkitConfigurationProfile-Objekt ohne das MixedRealityToolkit in der Szene auswählen, werden Sie gefragt, ob das MRTK die Szene automatisch für Sie einrichten soll.</span><span class="sxs-lookup"><span data-stu-id="8310f-116">If you select a MixedRealityToolkitConfigurationProfile asset without the MixedRealityToolkit in the scene, it will ask you if you want the MRTK to automatically setup the scene for you.</span></span> <span data-ttu-id="8310f-117">Dies ist optional, es muss jedoch ein aktives MixedRealityToolkit-Objekt in der Szene geben, um auf alle Konfigurationsbildschirme zugreifen zu können.</span><span class="sxs-lookup"><span data-stu-id="8310f-117">This is optional, however, there must be an active MixedRealityToolkit object in the scene to access all the configuration screens.</span></span>

<span data-ttu-id="8310f-118">Dies ist die aktuelle aktive Laufzeitkonfiguration für das Projekt.</span><span class="sxs-lookup"><span data-stu-id="8310f-118">This houses the current active runtime configuration for the project.</span></span>

<span data-ttu-id="8310f-119">Von hier aus können Sie zu allen Konfigurationsprofilen für das MRTK navigieren, einschließlich:</span><span class="sxs-lookup"><span data-stu-id="8310f-119">From here you can navigate to all the configuration profiles for the MRTK, including:</span></span>

- [<span data-ttu-id="8310f-120">Mixed Reality Toolkit für die Profilkonfiguration</span><span class="sxs-lookup"><span data-stu-id="8310f-120">Mixed Reality Toolkit profile configuration guide</span></span>](#mixed-reality-toolkit-profile-configuration-guide)
  - [<span data-ttu-id="8310f-121">Das Hauptkonfigurationsprofil Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="8310f-121">The main Mixed Reality Toolkit configuration profile</span></span>](#the-main-mixed-reality-toolkit-configuration-profile)
  - [<span data-ttu-id="8310f-122">Einstellungen für die Benutzererfahrung</span><span class="sxs-lookup"><span data-stu-id="8310f-122">Experience settings</span></span>](#experience-settings)
  - [<span data-ttu-id="8310f-123">Kameraeinstellungen</span><span class="sxs-lookup"><span data-stu-id="8310f-123">Camera settings</span></span>](#camera-settings)
  - [<span data-ttu-id="8310f-124">Eingabesystemeinstellungen</span><span class="sxs-lookup"><span data-stu-id="8310f-124">Input system settings</span></span>](#input-system-settings)
  - [<span data-ttu-id="8310f-125">Einstellungen für die Begrenzungsvisualisierung</span><span class="sxs-lookup"><span data-stu-id="8310f-125">Boundary visualization settings</span></span>](#boundary-visualization-settings)
  - [<span data-ttu-id="8310f-126">Teleportation-Systemauswahl</span><span class="sxs-lookup"><span data-stu-id="8310f-126">Teleportation system selection</span></span>](#teleportation-system-selection)
  - [<span data-ttu-id="8310f-127">Einstellungen für räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="8310f-127">Spatial awareness settings</span></span>](#spatial-awareness-settings)
  - [<span data-ttu-id="8310f-128">Diagnoseeinstellungen</span><span class="sxs-lookup"><span data-stu-id="8310f-128">Diagnostics settings</span></span>](#diagnostics-settings)
  - [<span data-ttu-id="8310f-129">Szenensystemeinstellungen</span><span class="sxs-lookup"><span data-stu-id="8310f-129">Scene system settings</span></span>](#scene-system-settings)
  - [<span data-ttu-id="8310f-130">Zusätzliche Diensteinstellungen</span><span class="sxs-lookup"><span data-stu-id="8310f-130">Additional services settings</span></span>](#additional-services-settings)
  - [<span data-ttu-id="8310f-131">Einstellungen für Eingabeaktionen</span><span class="sxs-lookup"><span data-stu-id="8310f-131">Input actions settings</span></span>](#input-actions-settings)
  - [<span data-ttu-id="8310f-132">Regeln für Eingabeaktionen</span><span class="sxs-lookup"><span data-stu-id="8310f-132">Input actions rules</span></span>](#input-actions-rules)
  - [<span data-ttu-id="8310f-133">Zeigerkonfiguration</span><span class="sxs-lookup"><span data-stu-id="8310f-133">Pointer configuration</span></span>](#pointer-configuration)
  - [<span data-ttu-id="8310f-134">Gestenkonfiguration</span><span class="sxs-lookup"><span data-stu-id="8310f-134">Gestures configuration</span></span>](#gestures-configuration)
  - [<span data-ttu-id="8310f-135">Speech-Befehle</span><span class="sxs-lookup"><span data-stu-id="8310f-135">Speech commands</span></span>](#speech-commands)
  - [<span data-ttu-id="8310f-136">Konfiguration der Controllerzuordnung</span><span class="sxs-lookup"><span data-stu-id="8310f-136">Controller mapping configuration</span></span>](#controller-mapping-configuration)
  - [<span data-ttu-id="8310f-137">Einstellungen für controllervisualisierung</span><span class="sxs-lookup"><span data-stu-id="8310f-137">Controller visualization settings</span></span>](#controller-visualization-settings)
  - [<span data-ttu-id="8310f-138">Editor-Hilfsprogramme</span><span class="sxs-lookup"><span data-stu-id="8310f-138">Editor utilities</span></span>](#editor-utilities)
    - [<span data-ttu-id="8310f-139">Dienstinspektoren</span><span class="sxs-lookup"><span data-stu-id="8310f-139">Service inspectors</span></span>](#service-inspectors)
    - [<span data-ttu-id="8310f-140">Tiefenpufferrenderer</span><span class="sxs-lookup"><span data-stu-id="8310f-140">Depth buffer renderer</span></span>](#depth-buffer-renderer)
  - [<span data-ttu-id="8310f-141">Ändern von Profilen zur Laufzeit</span><span class="sxs-lookup"><span data-stu-id="8310f-141">Changing profiles at runtime</span></span>](#changing-profiles-at-runtime)
    - [<span data-ttu-id="8310f-142">Pre MRTK-Initialisierungsprofilschalter</span><span class="sxs-lookup"><span data-stu-id="8310f-142">Pre MRTK initialization profile switch</span></span>](#pre-mrtk-initialization-profile-switch)
    - [<span data-ttu-id="8310f-143">Aktiver Profilschalter</span><span class="sxs-lookup"><span data-stu-id="8310f-143">Active profile switch</span></span>](#active-profile-switch)
  - [<span data-ttu-id="8310f-144">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="8310f-144">See also</span></span>](#see-also)

<span data-ttu-id="8310f-145">Diese Konfigurationsprofile werden unten in den entsprechenden Abschnitten ausführlich beschrieben:</span><span class="sxs-lookup"><span data-stu-id="8310f-145">These configuration profiles are detailed below in their relevant sections:</span></span>

---
<a name="experience"></a>

## <a name="experience-settings"></a><span data-ttu-id="8310f-146">Einstellungen für die Benutzererfahrung</span><span class="sxs-lookup"><span data-stu-id="8310f-146">Experience settings</span></span>

<span data-ttu-id="8310f-147">Auf der Hauptseite Mixed Reality Toolkit-Konfiguration definiert diese Einstellung den Standardvorgang der [Mixed Reality-Umgebungsskalierung](/windows/mixed-reality/coordinate-systems-in-unity) für Ihr Projekt.</span><span class="sxs-lookup"><span data-stu-id="8310f-147">Located on the main Mixed Reality Toolkit configuration page, this setting defines the default operation of the [Mixed Reality environment scale](/windows/mixed-reality/coordinate-systems-in-unity) for your project.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ExperienceSettings.png" width="650px" alt="Experiance settings" style="display:block;">

---
<a name="camera"></a>

## <a name="camera-settings"></a><span data-ttu-id="8310f-148">Kameraeinstellungen</span><span class="sxs-lookup"><span data-stu-id="8310f-148">Camera settings</span></span>

<span data-ttu-id="8310f-149">Die Kameraeinstellungen definieren, wie die Kamera für Ihr Mixed Reality-Projekt eingerichtet wird, und definieren die allgemeinen Einstellungen für Clipping, Qualität und Transparenz.</span><span class="sxs-lookup"><span data-stu-id="8310f-149">The camera settings define how the camera will be setup for your Mixed Reality project, defining the generic clipping, quality and transparency settings.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_CameraProfile.png" width="650px" alt="Camera Profile" style="display:block;">

---
<a name="inputsystem"></a>

## <a name="input-system-settings"></a><span data-ttu-id="8310f-150">Eingabesystemeinstellungen</span><span class="sxs-lookup"><span data-stu-id="8310f-150">Input system settings</span></span>

<span data-ttu-id="8310f-151">Das Mixed Reality-Projekt bietet ein stabiles und gut trainiertes Eingabesystem zum Weiterleiten aller Eingabeereignisse um das Projekt herum, das standardmäßig ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="8310f-151">The Mixed Reality Project provides a robust and well-trained input system for routing all the input events around the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemSelection.png" width="650px" alt="Input System settings 1" style="display:block;">

<span data-ttu-id="8310f-152">Hinter dem vom MRTK bereitgestellten Eingabesystem befinden sich mehrere andere Systeme, die dazu beitragen, die komplexen Inter-Reality-Aufgaben zu steuern und zu verwalten, die erforderlich sind, um die Komplexität eines Multiplattform-/Mixed Reality-Frameworks zu abstrahieren.</span><span class="sxs-lookup"><span data-stu-id="8310f-152">Behind the Input System provided by the MRTK are several other systems, these help to drive and manage the complex inter-weavings required to abstract out the complexities of a multi-platform / mixed reality framework.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemProfile.png" width="650px" alt="Input System settings 2" style="display:block;">

<span data-ttu-id="8310f-153">Die einzelnen Profile werden im Folgenden ausführlich beschrieben:</span><span class="sxs-lookup"><span data-stu-id="8310f-153">Each of the individual profiles are detailed below:</span></span>

- <span data-ttu-id="8310f-154">Fokuseinstellungen</span><span class="sxs-lookup"><span data-stu-id="8310f-154">Focus Settings</span></span>
- [<span data-ttu-id="8310f-155">Einstellungen für Eingabeaktionen</span><span class="sxs-lookup"><span data-stu-id="8310f-155">Input actions settings</span></span>](#input-actions-settings)
- [<span data-ttu-id="8310f-156">Regeln für Eingabeaktionen</span><span class="sxs-lookup"><span data-stu-id="8310f-156">Input actions rules</span></span>](#input-actions-rules)
- [<span data-ttu-id="8310f-157">Zeigerkonfiguration</span><span class="sxs-lookup"><span data-stu-id="8310f-157">Pointer configuration</span></span>](#pointer-configuration)
- [<span data-ttu-id="8310f-158">Gestenkonfiguration</span><span class="sxs-lookup"><span data-stu-id="8310f-158">Gestures configuration</span></span>](#gestures-configuration)
- [<span data-ttu-id="8310f-159">Speech-Befehle</span><span class="sxs-lookup"><span data-stu-id="8310f-159">Speech commands</span></span>](#speech-commands)
- [<span data-ttu-id="8310f-160">Konfiguration der Controllerzuordnung</span><span class="sxs-lookup"><span data-stu-id="8310f-160">Controller mapping configuration</span></span>](#controller-mapping-configuration)
- [<span data-ttu-id="8310f-161">Einstellungen für controllervisualisierung</span><span class="sxs-lookup"><span data-stu-id="8310f-161">Controller visualization settings</span></span>](#controller-visualization-settings)

---
<a name="boundary"></a>

## <a name="boundary-visualization-settings"></a><span data-ttu-id="8310f-162">Einstellungen für die Begrenzungsvisualisierung</span><span class="sxs-lookup"><span data-stu-id="8310f-162">Boundary visualization settings</span></span>

<span data-ttu-id="8310f-163">Das Begrenzungssystem übersetzt die wahrgenommene Grenze, die von der Zugrunde liegenden Plattformgrenze/dem Wächtersystem gemeldet wird.</span><span class="sxs-lookup"><span data-stu-id="8310f-163">The boundary system translates the perceived boundary reported by the underlying platforms boundary / guardian system.</span></span> <span data-ttu-id="8310f-164">Mit der Konfiguration der Begrenzungs-Schnellansicht können Sie die aufgezeichnete Grenze innerhalb Ihrer Szene relativ zur Position des Benutzers automatisch anzeigen. Die Grenze reagiert bzw. aktualisiert auch basierend darauf, wo der Benutzer innerhalb der Szene teleportiert.</span><span class="sxs-lookup"><span data-stu-id="8310f-164">The Boundary visualizer configuration gives you the ability to automatically show the recorded boundary within your scene relative to the user's position.The boundary will also react / update based on where the user teleports within the scene.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_BoundaryVisualizationProfile.png" width="650px" alt="Boundry Visualization Settings" style="display:block;">

---
<a name="teleportation"></a>

## <a name="teleportation-system-selection"></a><span data-ttu-id="8310f-165">Teleportation-Systemauswahl</span><span class="sxs-lookup"><span data-stu-id="8310f-165">Teleportation system selection</span></span>

<span data-ttu-id="8310f-166">Das Mixed Reality-Projekt bietet ein umfassendes Teleportation-System zum Verwalten von Teleportationsereignissen im Projekt, das standardmäßig ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="8310f-166">The Mixed Reality Project provides a full featured Teleportation system for managing teleportation events in the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_TeleportationSystemSelection.png" width="650px" alt="Teleport System settings" style="display:block;">

---
<a name="spatialawareness"></a>

## <a name="spatial-awareness-settings"></a><span data-ttu-id="8310f-167">Einstellungen für räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="8310f-167">Spatial awareness settings</span></span>

<span data-ttu-id="8310f-168">Das Mixed Reality-Projekt stellt ein neu erstelltes Räumliches Bewusstseinssystem für die Arbeit mit Raumscansystemen im Projekt zur Verfügung, das standardmäßig ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="8310f-168">The Mixed Reality Project provides a rebuilt spatial awareness system for working with spatial scanning systems in the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessSystemSelection.png" width="650px" alt="Spatial Awareness settings 1" style="display:block;">

<span data-ttu-id="8310f-169">Mit der Mixed Reality Toolkit-Konfiguration für räumliche Wahrnehmung können Sie anpassen, wie das System gestartet wird, ob es automatisch erfolgt, wenn die Anwendung gestartet wird oder später programmgesteuert gestartet wird, sowie die Extents für das Sichtfeld festlegen.</span><span class="sxs-lookup"><span data-stu-id="8310f-169">The Mixed Reality Toolkit spatial awareness configuration lets you tailor how the system starts, whether it is automatically when the application starts or later programmatically as well as setting the extents for the field of view.</span></span>

<span data-ttu-id="8310f-170">Außerdem können Sie die Gitternetz- und Oberflächeneinstellungen konfigurieren und weiter anpassen, wie Ihr Projekt die Umgebung um Sie herum versteht.</span><span class="sxs-lookup"><span data-stu-id="8310f-170">It also lets you configure the mesh and surface settings, further customizing how your project understands the environment around you.</span></span>

<span data-ttu-id="8310f-171">Dies gilt nur für Geräte, die eine gescannte Umgebung bereitstellen können.</span><span class="sxs-lookup"><span data-stu-id="8310f-171">This is only applicable for devices that can provide a scanned environment.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessProfile.png" width="650px" alt="Spatial Awareness settings 2" style="display:block;">

---
<a name="diagnostic"></a>

## <a name="diagnostics-settings"></a><span data-ttu-id="8310f-172">Diagnoseeinstellungen</span><span class="sxs-lookup"><span data-stu-id="8310f-172">Diagnostics settings</span></span>

<span data-ttu-id="8310f-173">Ein optionales, aber äußerst nützliches Feature des MRTK ist die Plug-In-Diagnosefunktion.</span><span class="sxs-lookup"><span data-stu-id="8310f-173">An optional but highly useful feature of the MRTK is the plugin diagnostics functionality.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsSystemSelection.png" width="650px" alt="Diagnostics settings" style="display:block;">

<span data-ttu-id="8310f-174">Das Diagnoseprofil bietet mehrere einfache Systeme, die während der Ausführung des Projekts überwacht werden können, einschließlich eines praktischen Ein-/Aus-Schalters zum Aktivieren/Deaktivieren des Anzeigebereichs in der Szene.</span><span class="sxs-lookup"><span data-stu-id="8310f-174">The diagnostics profile provides several simple systems to monitor whilst the project is running, including a handy On/Off switch to enable / disable the display panel in the scene.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsProfile.png" width="650px" alt="Diagnostics settings System settings 2" style="display:block;">

---
<a name="scenesystem"></a>

## <a name="scene-system-settings"></a><span data-ttu-id="8310f-175">Szenensystemeinstellungen</span><span class="sxs-lookup"><span data-stu-id="8310f-175">Scene system settings</span></span>

<span data-ttu-id="8310f-176">Das MRTK bietet diesen optionalen Dienst, mit dem Sie komplexe additive Szenen beim Laden/Entladen verwalten können.</span><span class="sxs-lookup"><span data-stu-id="8310f-176">The MRTK provides this optional service to help you manage complex additive scene loading / unloading.</span></span> <span data-ttu-id="8310f-177">Um zu entscheiden, ob das Szenensystem für Ihr Projekt geeignet ist, lesen Sie den Leitfaden zum [Szenensystem Erste Schritte.](../features/scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="8310f-177">To decide if the Scene System would be a good fit for your project, read the [Scene System Getting Started Guide.](../features/scene-system/scene-system-getting-started.md)</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SceneSystemProfile.png" width="650px" alt="Scene System settings 1" style="display:block;">

---
<a name="services"></a>

## <a name="additional-services-settings"></a><span data-ttu-id="8310f-178">Zusätzliche Diensteinstellungen</span><span class="sxs-lookup"><span data-stu-id="8310f-178">Additional services settings</span></span>

<span data-ttu-id="8310f-179">Einer der fortgeschritteneren Bereiche des Mixed Reality Toolkits ist die Implementierung des Dienstlocatormusters, die die Registrierung eines beliebigen "Diensts" beim Framework ermöglicht. [](https://en.wikipedia.org/wiki/Service_locator_pattern)</span><span class="sxs-lookup"><span data-stu-id="8310f-179">One of the more advanced areas of the Mixed Reality Toolkit is its [service locator pattern](https://en.wikipedia.org/wiki/Service_locator_pattern) implementation which allows the registering of any "Service" with the framework.</span></span> <span data-ttu-id="8310f-180">Dadurch kann das Framework problemlos um neue Features/Systeme erweitert werden, aber auch Projekte können diese Funktionen nutzen, um ihre eigenen Laufzeitkomponenten zu registrieren.</span><span class="sxs-lookup"><span data-stu-id="8310f-180">This allows the framework to be both extended with new features / systems easily but also allows for projects to take advantage of these capabilities to register their own runtime components.</span></span>

<span data-ttu-id="8310f-181">Jeder registrierte Dienst erhält weiterhin den vollen Vorteil aller Unity-Ereignisse, ohne den Aufwand und die Kosten für die Implementierung eines MonoBehaviour- oder clunky-Singletonmusters.</span><span class="sxs-lookup"><span data-stu-id="8310f-181">Any registered service still gets the full advantage of all of the Unity events, without the overhead and cost of implementing a MonoBehaviour or clunky singleton patterns.</span></span> <span data-ttu-id="8310f-182">Dies ermöglicht reine C#-Komponenten ohne Szenenaufwand für die Ausführung von Vordergrund- und Hintergrundprozessen, z. B. Lawningsysteme, Laufzeitspiellogik oder praktisch alles andere.</span><span class="sxs-lookup"><span data-stu-id="8310f-182">This allows for pure C# components with no scene overhead for running both foreground and background processes, e.g. spawning systems, runtime game logic, or practically anything else.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_RegisteredServiceProvidersProfile.png" width="650px" alt="additional System settings" style="display:block;">

---
<a name="inputactions"></a>

## <a name="input-actions-settings"></a><span data-ttu-id="8310f-183">Einstellungen für Eingabeaktionen</span><span class="sxs-lookup"><span data-stu-id="8310f-183">Input actions settings</span></span>

<span data-ttu-id="8310f-184">Eingabeaktionen bieten eine Möglichkeit, physische Interaktionen und Eingaben aus einem Laufzeitprojekt zu abstrahieren.</span><span class="sxs-lookup"><span data-stu-id="8310f-184">Input actions provide a way to abstract any physical interactions and input from a runtime project.</span></span> <span data-ttu-id="8310f-185">Alle physischen Eingaben (von Controllern/ Händen/ Maus usw.) werden in eine logische Eingabeaktion übersetzt, die in Ihrem Laufzeitprojekt verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="8310f-185">All physical input (from controllers / hands / mouse / etc) is translated in to a logical input action for use in your runtime project.</span></span> <span data-ttu-id="8310f-186">Dadurch wird sichergestellt, dass Ihr Projekt unabhängig davon, woher die Eingabe stammt, diese Aktionen einfach als "Zu tunde Dinge" oder "Interagieren mit" in Ihren Szenen implementiert.</span><span class="sxs-lookup"><span data-stu-id="8310f-186">This ensures no matter where the input comes from, your project simply implements these actions as "Things to do" or "Interact with" in your scenes.</span></span>

<span data-ttu-id="8310f-187">Um eine neue Eingabeaktion zu erstellen, klicken Sie einfach auf die Schaltfläche "Neue Aktion hinzufügen", und geben Sie einen benutzerfreundlichen Textnamen für das ein, was sie darstellt.</span><span class="sxs-lookup"><span data-stu-id="8310f-187">To create a new input action, simply click the "Add a new Action" button and enter a friendly text name for what it represents.</span></span> <span data-ttu-id="8310f-188">Sie müssen dann nur eine Achse (den Datentyp) auswählen, die die Aktion vermitteln soll, oder im Fall von physischen Controllern den physischen Eingabetyp, an den sie angefügt werden kann, z. B.:</span><span class="sxs-lookup"><span data-stu-id="8310f-188">You then only need select an axis (the type of data) the action is meant to convey, or in the case of physical controllers, the physical input type it can be attached to, for example:</span></span>

| <span data-ttu-id="8310f-189">Achseneinschränkung</span><span class="sxs-lookup"><span data-stu-id="8310f-189">Axis Constraint</span></span> | <span data-ttu-id="8310f-190">Datentyp</span><span class="sxs-lookup"><span data-stu-id="8310f-190">Data Type</span></span> | <span data-ttu-id="8310f-191">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8310f-191">Description</span></span> | <span data-ttu-id="8310f-192">Beispiel für die Verwendung</span><span class="sxs-lookup"><span data-stu-id="8310f-192">Example use</span></span> |
| :--- | :--- | :--- | :--- |
| <span data-ttu-id="8310f-193">Keine</span><span class="sxs-lookup"><span data-stu-id="8310f-193">None</span></span> | <span data-ttu-id="8310f-194">Keine Daten</span><span class="sxs-lookup"><span data-stu-id="8310f-194">No data</span></span> | <span data-ttu-id="8310f-195">Wird für eine leere Aktion oder ein leeres Ereignis verwendet.</span><span class="sxs-lookup"><span data-stu-id="8310f-195">Used for an empty action or event</span></span> | <span data-ttu-id="8310f-196">Ereignistrigger</span><span class="sxs-lookup"><span data-stu-id="8310f-196">Event Trigger</span></span> |
| <span data-ttu-id="8310f-197">Rohdaten (reserviert)</span><span class="sxs-lookup"><span data-stu-id="8310f-197">Raw (reserved)</span></span> | <span data-ttu-id="8310f-198">object</span><span class="sxs-lookup"><span data-stu-id="8310f-198">object</span></span> | <span data-ttu-id="8310f-199">Für die zukünftige Verwendung reserviert</span><span class="sxs-lookup"><span data-stu-id="8310f-199">Reserved for future use</span></span> | <span data-ttu-id="8310f-200">–</span><span class="sxs-lookup"><span data-stu-id="8310f-200">N/A</span></span> |
| <span data-ttu-id="8310f-201">Digital</span><span class="sxs-lookup"><span data-stu-id="8310f-201">Digital</span></span> | <span data-ttu-id="8310f-202">bool</span><span class="sxs-lookup"><span data-stu-id="8310f-202">bool</span></span> | <span data-ttu-id="8310f-203">Ein boolescher Wert für bzw. aus Typdaten</span><span class="sxs-lookup"><span data-stu-id="8310f-203">A boolean on or off type data</span></span> | <span data-ttu-id="8310f-204">Controllerschaltfläche</span><span class="sxs-lookup"><span data-stu-id="8310f-204">A controller button</span></span> |
| <span data-ttu-id="8310f-205">Einzelne Achse</span><span class="sxs-lookup"><span data-stu-id="8310f-205">Single Axis</span></span> | <span data-ttu-id="8310f-206">float</span><span class="sxs-lookup"><span data-stu-id="8310f-206">float</span></span> | <span data-ttu-id="8310f-207">Ein Einzelner Genauigkeitsdatenwert</span><span class="sxs-lookup"><span data-stu-id="8310f-207">A single precision data value</span></span> | <span data-ttu-id="8310f-208">Eine Bereichseingabe, z. B. ein Trigger</span><span class="sxs-lookup"><span data-stu-id="8310f-208">A ranged input, e.g. a trigger</span></span> |
| <span data-ttu-id="8310f-209">Duale Achse</span><span class="sxs-lookup"><span data-stu-id="8310f-209">Dual Axis</span></span> | <span data-ttu-id="8310f-210">Vector2</span><span class="sxs-lookup"><span data-stu-id="8310f-210">Vector2</span></span> | <span data-ttu-id="8310f-211">Ein Datum vom Typ "Dual Float" für mehrere Achsen</span><span class="sxs-lookup"><span data-stu-id="8310f-211">A dual float type date for multiple axis</span></span> | <span data-ttu-id="8310f-212">Ein Dpad oder Thumbstick</span><span class="sxs-lookup"><span data-stu-id="8310f-212">A Dpad or Thumbstick</span></span> |
| <span data-ttu-id="8310f-213">Drei Dof-Position</span><span class="sxs-lookup"><span data-stu-id="8310f-213">Three Dof Position</span></span> | <span data-ttu-id="8310f-214">Vector3</span><span class="sxs-lookup"><span data-stu-id="8310f-214">Vector3</span></span> | <span data-ttu-id="8310f-215">Positionstypdaten aus mit 3 Gleitkommaachsen</span><span class="sxs-lookup"><span data-stu-id="8310f-215">Positional type data from with 3 float axis</span></span> | <span data-ttu-id="8310f-216">Nur 3D-Positionsformatcontroller</span><span class="sxs-lookup"><span data-stu-id="8310f-216">3D position style only controller</span></span> |
| <span data-ttu-id="8310f-217">Drei Dof-Drehungen</span><span class="sxs-lookup"><span data-stu-id="8310f-217">Three Dof Rotation</span></span> | <span data-ttu-id="8310f-218">Quaternion</span><span class="sxs-lookup"><span data-stu-id="8310f-218">Quaternion</span></span> | <span data-ttu-id="8310f-219">Nur Drehungseingabe mit 4 Gleitkommaachsen</span><span class="sxs-lookup"><span data-stu-id="8310f-219">Rotational only input with 4 float axis</span></span> | <span data-ttu-id="8310f-220">Ein Drei-Grad-Stilcontroller, z. B. Oculus Go-Controller</span><span class="sxs-lookup"><span data-stu-id="8310f-220">A Three degrees style controller, e.g. Oculus Go controller</span></span> |
| <span data-ttu-id="8310f-221">Sechs Dof</span><span class="sxs-lookup"><span data-stu-id="8310f-221">Six Dof</span></span> | <span data-ttu-id="8310f-222">Mixed Reality Pose (Vector3, Quaternion)</span><span class="sxs-lookup"><span data-stu-id="8310f-222">Mixed Reality Pose (Vector3, Quaternion)</span></span> | <span data-ttu-id="8310f-223">Eine Eingabe im Positions- und Drehformat mit Vector3- und Quaternion-Komponenten</span><span class="sxs-lookup"><span data-stu-id="8310f-223">A position and rotation style input with both Vector3 and Quaternion components</span></span> | <span data-ttu-id="8310f-224">Ein Bewegungscontroller oder Zeiger</span><span class="sxs-lookup"><span data-stu-id="8310f-224">A motion controller or Pointer</span></span> |

<span data-ttu-id="8310f-225">Ereignisse, die Eingabeaktionen verwenden, sind nicht auf physische Controller beschränkt und können weiterhin innerhalb des Projekts verwendet werden, damit Laufzeiteffekte neue Aktionen generieren.</span><span class="sxs-lookup"><span data-stu-id="8310f-225">Events utilizing input actions are not limited to physical controllers and can still be utilized within the project to have runtime effects generate new actions.</span></span>

> [!NOTE]
> <span data-ttu-id="8310f-226">Eingabeaktionen sind eine der wenigen Komponenten, die zur Laufzeit nicht bearbeitet werden können, sondern nur eine Entwurfszeitkonfiguration.</span><span class="sxs-lookup"><span data-stu-id="8310f-226">Input actions are one of the few components which is not editable at runtime, they are a design time configuration only.</span></span> <span data-ttu-id="8310f-227">Dieses Profil sollte aufgrund der Abhängigkeit des Frameworks (und Ihrer Projekte) von den für jede Aktion generierten IDs nicht ausgetauscht werden, während das Projekt ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="8310f-227">This profile should not be swapped out whilst the project is running due to the framework (and your projects) dependency on the ID's generated for each action.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionsProfile.png" width="650px" alt="Configuration Profile" style="display:block;">

---
<a name="inputactionrules"></a>

## <a name="input-actions-rules"></a><span data-ttu-id="8310f-228">Regeln für Eingabeaktionen</span><span class="sxs-lookup"><span data-stu-id="8310f-228">Input actions rules</span></span>

<span data-ttu-id="8310f-229">Eingabeaktionsregeln bieten eine Möglichkeit, ein Ereignis, das für eine Eingabeaktion ausgelöst wird, automatisch in verschiedene Aktionen basierend auf seinem Datenwert zu übersetzen.</span><span class="sxs-lookup"><span data-stu-id="8310f-229">Input action rules provide a way to automatically translate an event raised for one input action in to different actions based on its data value.</span></span> <span data-ttu-id="8310f-230">Diese werden nahtlos innerhalb des Frameworks verwaltet und verursachen keine Leistungskosten.</span><span class="sxs-lookup"><span data-stu-id="8310f-230">These are managed seamlessly within the framework and do not incur any performance costs.</span></span>

<span data-ttu-id="8310f-231">Konvertieren Sie z. B. das Eingabeereignis mit einer einzelnen dualen Achse von einem DPad in die 4 entsprechenden Aktionen "Dpad Nach oben", "DPad Nach unten" / "Dpad Links" / "Dpad Rechts" (wie in der folgenden Abbildung dargestellt).</span><span class="sxs-lookup"><span data-stu-id="8310f-231">For example, converting the single dual axis input event from a DPad in to the 4 corresponding "Dpad Up" / "DPad Down" / "Dpad Left" / "Dpad Right" actions (as shown in the image below).</span></span>

<span data-ttu-id="8310f-232">Dies kann auch in Ihrem eigenen Code erfolgen.</span><span class="sxs-lookup"><span data-stu-id="8310f-232">This could also be done in your own code.</span></span> <span data-ttu-id="8310f-233">Da dies jedoch ein sehr gängiges Muster war, bietet das Framework einen Mechanismus, um dies "vor der Box" zu tun.</span><span class="sxs-lookup"><span data-stu-id="8310f-233">However, seeing as this was a very common pattern, the framework provides a mechanism to do this "out of the box"</span></span>

<span data-ttu-id="8310f-234">EingabeaktionSregeln können für jede der verfügbaren Eingabeachsen konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="8310f-234">Input action Rules can be configured for any of the available input axis.</span></span> <span data-ttu-id="8310f-235">Eingabeaktionen eines Achsentyps können jedoch in eine andere Eingabeaktion desselben Achsentyps übersetzt werden.</span><span class="sxs-lookup"><span data-stu-id="8310f-235">However, input actions from one axis type can be translated to another input action of the same axis type.</span></span> <span data-ttu-id="8310f-236">Sie können eine Aktion mit zwei Achsen einer anderen Aktion mit zwei Achsen zuordnen, jedoch nicht einer digitalen oder keiner Aktion.</span><span class="sxs-lookup"><span data-stu-id="8310f-236">You can map a dual axis action to another dual axis action, but not to a digital or none action.</span></span>

![Profil für Eingabeaktionsregeln](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionRulesProfile.png)

---
<a name="pointer"></a>

## <a name="pointer-configuration"></a><span data-ttu-id="8310f-238">Zeigerkonfiguration</span><span class="sxs-lookup"><span data-stu-id="8310f-238">Pointer configuration</span></span>

<span data-ttu-id="8310f-239">Zeiger werden verwendet, um die Interaktivität in der Szene von jedem Eingabegerät aus zu bewegen, was sowohl einen Richtungs- als auch einen Treffertest mit jedem Objekt in einer Szene (das einen Collider angefügt hat oder eine Benutzeroberflächenkomponente ist) gibt.</span><span class="sxs-lookup"><span data-stu-id="8310f-239">Pointers are used to drive interactivity in the scene from any input device, giving both a direction and hit test with any object in a scene (that has a collider attached, or is a UI component).</span></span> <span data-ttu-id="8310f-240">Zeiger werden standardmäßig automatisch für Controller, Headsets (Anvieren/Fokus) und Maus-/Toucheingaben konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="8310f-240">Pointers are by default automatically configured for controllers, headsets (gaze / focus) and mouse / touch input.</span></span>

<span data-ttu-id="8310f-241">Zeiger können auch innerhalb der aktiven Szene mithilfe einer der vielen Vom Mixed Reality Toolkit bereitgestellten Linienkomponenten visualisiert werden, oder mit einer ihrer eigenen, wenn sie die MRTK IMixedRealityPointer-Schnittstelle implementieren.</span><span class="sxs-lookup"><span data-stu-id="8310f-241">Pointers can also be visualized within the active scene using one of the many line components provided by the Mixed Reality Toolkit, or any of your own if they implement the MRTK IMixedRealityPointer interface.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputPointerProfile.png" width="650px" alt="Input Pointer Profile" style="display:block;">

- <span data-ttu-id="8310f-242">Zeigende Extent:Bestimmt den globalen Zeigendpunkt für alle Zeiger, einschließlich Anvieren.</span><span class="sxs-lookup"><span data-stu-id="8310f-242">Pointing Extent: Determines the global pointing extent for all pointers, including gaze.</span></span>
- <span data-ttu-id="8310f-243">Zeigende Raycastebenenmasken: Bestimmt, für welche Ebenen Zeiger raycasten.</span><span class="sxs-lookup"><span data-stu-id="8310f-243">Pointing Raycast Layer Masks: Determines which layers pointers will raycast against.</span></span>
- <span data-ttu-id="8310f-244">Debuggen von Draw Pointing Ray: Ein Debug-Hilfsgerät zum Visualisieren der für Raycasting verwendeten Lichtstrahle.</span><span class="sxs-lookup"><span data-stu-id="8310f-244">Debug Draw Pointing Rays: A debug helper for visualizing the rays used for raycasting.</span></span>
- <span data-ttu-id="8310f-245">Debuggen von Farben für Zeichnen zeigender Lichtstrahle: Eine Reihe von Farben, die für die Visualisierung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="8310f-245">Debug Draw Pointing Rays Colors: A set of colors to use for visualizing.</span></span>
- <span data-ttu-id="8310f-246">Prefab für Anvistikcursor: Erleichtert die Angabe eines globalen Anvistikcursors für jede Szene.</span><span class="sxs-lookup"><span data-stu-id="8310f-246">Gaze cursor prefab: Makes it easy to specify a global gaze cursor for any scene.</span></span>

<span data-ttu-id="8310f-247">Es gibt eine zusätzliche Hilfsschaltfläche, mit der Sie schnell zum Anvinganbieter springen können, um bei Bedarf einige bestimmte Werte für das Anvieren zu überschreiben.</span><span class="sxs-lookup"><span data-stu-id="8310f-247">There's an additional helper button to quickly jump to the Gaze Provider to override some specific values for Gaze if needed.</span></span>

---
<a name="gestures"></a>

## <a name="gestures-configuration"></a><span data-ttu-id="8310f-248">Gestenkonfiguration</span><span class="sxs-lookup"><span data-stu-id="8310f-248">Gestures configuration</span></span>

<span data-ttu-id="8310f-249">Gesten sind eine systemspezifische Implementierung, mit der Sie eingabeaktionen den verschiedenen Eingabemethoden "Gesten" zuweisen können, die von verschiedenen SDKs (z. B. HoloLens) bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="8310f-249">Gestures are a system specific implementation allowing you to assign input actions to the various "Gesture" input methods provided by various SDKs (e.g. HoloLens).</span></span>

> [!NOTE]
> <span data-ttu-id="8310f-250">Die aktuelle Gestenimplementierung gilt nur für HoloLens und wird für andere Systeme verbessert, wenn sie dem Toolkit in Zukunft hinzugefügt werden (noch keine Datumsangaben).</span><span class="sxs-lookup"><span data-stu-id="8310f-250">The current Gestures implementation is for the HoloLens only and will be enhanced for other systems as they are added to the Toolkit in the future (no dates yet).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_GesturesProfile.png" width="650px" alt="Gesture configuration" style="display:block;">

---
<a name="speech"></a>

## <a name="speech-commands"></a><span data-ttu-id="8310f-251">Speech-Befehle</span><span class="sxs-lookup"><span data-stu-id="8310f-251">Speech commands</span></span>

<span data-ttu-id="8310f-252">Wie Gesten bieten einige Laufzeitplattformen auch intelligente "Spracherkennung" mit der Möglichkeit, Befehle zu generieren, die von einem Unity-Projekt empfangen werden können.</span><span class="sxs-lookup"><span data-stu-id="8310f-252">Like gestures, some runtime platforms also provide intelligent "Speech to Text" functionality with the ability to generate commands that can be received by a Unity project.</span></span> <span data-ttu-id="8310f-253">Mit diesem Konfigurationsprofil können Sie Folgendes konfigurieren:</span><span class="sxs-lookup"><span data-stu-id="8310f-253">This configuration profile allows you to configure the following:</span></span>

1. <span data-ttu-id="8310f-254">Allgemeine Einstellungen: Wenn "Startverhalten" auf "Automatischer Start" oder "Manueller Start" festgelegt ist, wird festgelegt, ob KeywordRecognizer beim Start des Eingabesystems initialisiert werden soll oder ob das Projekt entscheiden kann, wann das KeywordRecognizer initialisiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="8310f-254">General Settings - "Start Behavior" set to Auto Start or Manual Start determines whether to initialize KeywordRecognizer at input system startup or let the project decide when to initialize the KeywordRecognizer.</span></span> <span data-ttu-id="8310f-255">"Recognition Confidence Level" wird verwendet, um die [KeywordRecognizer-API](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html) von Unity zu initialisieren.</span><span class="sxs-lookup"><span data-stu-id="8310f-255">"Recognition Confidence Level" is used to initialize Unity's [KeywordRecognizer API](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html)</span></span>
2. <span data-ttu-id="8310f-256">Sprachbefehle: Registriert "Wörter" und übersetzt sie in Eingabeaktionen, die von Ihrem Projekt empfangen werden können.</span><span class="sxs-lookup"><span data-stu-id="8310f-256">Speech Commands - Registers "words" and translates them in to input actions that can be received by your project.</span></span> <span data-ttu-id="8310f-257">Sie können bei Bedarf auch an Tastaturaktionen angefügt werden.</span><span class="sxs-lookup"><span data-stu-id="8310f-257">They can also be attached to keyboard actions if required.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8310f-258">Das System unterstützt derzeit nur Sprache, wenn es auf Windows 10-Plattformen ausgeführt wird, z. B. HoloLens und Windows 10 Desktop, und wird für andere Systeme verbessert, da sie in Zukunft dem MRTK hinzugefügt werden (noch keine Datumsangaben).</span><span class="sxs-lookup"><span data-stu-id="8310f-258">The system currently only supports speech when running on Windows 10 platforms, e.g. HoloLens and Windows 10 desktop and will be enhanced for other systems as they are added to MRTK in the future (no dates yet).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpeechCommandsProfile.png" width="650px" alt="Configuration Profile screens" style="display:block;">

---
<a name="mapping"></a>

## <a name="controller-mapping-configuration"></a><span data-ttu-id="8310f-259">Konfiguration der Controllerzuordnung</span><span class="sxs-lookup"><span data-stu-id="8310f-259">Controller mapping configuration</span></span>

<span data-ttu-id="8310f-260">Einer der Hauptkonfigurationsbildschirme für das Mixed Reality Toolkit ist die Möglichkeit, die verschiedenen Controllertypen zu konfigurieren und zu zuordnen, die von Ihrem Projekt verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="8310f-260">One of the core configuration screens for the Mixed Reality Toolkit is the ability to configure and map the various types of controllers that can be utilized by your project.</span></span>

<span data-ttu-id="8310f-261">Auf dem folgenden Konfigurationsbildschirm können Sie alle Controller konfigurieren, die derzeit vom Toolkit erkannt werden.</span><span class="sxs-lookup"><span data-stu-id="8310f-261">The configuration screen below allows you to configure any of the controllers currently recognized by the toolkit.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerMappingProfile.png" width="650px" alt="Controller Mapping" style="display:block;">

<span data-ttu-id="8310f-262">Das MRTK stellt eine Standardkonfiguration für die folgenden Controller/Systeme zur Verfügung:</span><span class="sxs-lookup"><span data-stu-id="8310f-262">The MRTK provides a default configuration for the following controllers / systems:</span></span>

- <span data-ttu-id="8310f-263">Maus (einschließlich Unterstützung räumlicher 3D-Maus)</span><span class="sxs-lookup"><span data-stu-id="8310f-263">Mouse (including 3D spatial mouse support)</span></span>
- <span data-ttu-id="8310f-264">Touch Screen</span><span class="sxs-lookup"><span data-stu-id="8310f-264">Touch Screen</span></span>
- <span data-ttu-id="8310f-265">Xbox-Controller</span><span class="sxs-lookup"><span data-stu-id="8310f-265">Xbox controllers</span></span>
- <span data-ttu-id="8310f-266">Windows Mixed Reality Controller</span><span class="sxs-lookup"><span data-stu-id="8310f-266">Windows Mixed Reality controllers</span></span>
- <span data-ttu-id="8310f-267">HoloLens-Gesten</span><span class="sxs-lookup"><span data-stu-id="8310f-267">HoloLens Gestures</span></span>
- <span data-ttu-id="8310f-268">VSV-Wandcontroller</span><span class="sxs-lookup"><span data-stu-id="8310f-268">HTC Vive wand controllers</span></span>
- <span data-ttu-id="8310f-269">Oculus Touch-Controller</span><span class="sxs-lookup"><span data-stu-id="8310f-269">Oculus Touch controllers</span></span>
- <span data-ttu-id="8310f-270">Oculus-Remotecontroller</span><span class="sxs-lookup"><span data-stu-id="8310f-270">Oculus Remote controller</span></span>
- <span data-ttu-id="8310f-271">Generische OpenVR-Geräte (nur fortgeschrittene Benutzer)</span><span class="sxs-lookup"><span data-stu-id="8310f-271">Generic OpenVR devices (advanced users only)</span></span>

<span data-ttu-id="8310f-272">Wenn Sie auf das Image für eines der vorgefertigten Controllersysteme klicken, können Sie eine einzelne Eingabeaktion für alle entsprechenden Eingaben konfigurieren, z. B. siehe den Konfigurationsbildschirm des Oculus Touch-Controllers unten:</span><span class="sxs-lookup"><span data-stu-id="8310f-272">Clicking on the Image for any of the pre-built controller systems allows you to configure a single input action for all its corresponding inputs, for example, see the Oculus Touch controller configuration screen below:</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_WindowsMixedRealityControllerConfigScreen.png" width="650px" alt="Controller config screen" style="display:block;">

<span data-ttu-id="8310f-273">Es gibt auch einen erweiterten Bildschirm zum Konfigurieren anderer OpenVR- oder Unity-Eingabecontroller, die oben nicht identifiziert werden.</span><span class="sxs-lookup"><span data-stu-id="8310f-273">There is also an advanced screen for configuring other OpenVR or Unity input controllers that are not identified above.</span></span>

---
<a name="visualization"></a>

## <a name="controller-visualization-settings"></a><span data-ttu-id="8310f-274">Einstellungen für controllervisualisierung</span><span class="sxs-lookup"><span data-stu-id="8310f-274">Controller visualization settings</span></span>

<span data-ttu-id="8310f-275">Zusätzlich zur Controllerzuordnung wird ein separates Konfigurationsprofil bereitgestellt, um anzupassen, wie Ihre Controller innerhalb Ihrer Szenen dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="8310f-275">In addition to the controller mapping, a separate configuration profile is provided to customize how your controllers are presented within your scenes.</span></span>

<span data-ttu-id="8310f-276">Dies kann auf einem "globalen" (alle Instanzen eines Controllers für eine bestimmte Hand) oder spezifisch für einen einzelnen Controllertyp/eine einzelne Hand konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="8310f-276">This can be configured at a "Global" (all instances of a controller for a specific hand) or specific to an individual controller type / hand.</span></span>

<span data-ttu-id="8310f-277">Das MRTK unterstützt auch native SDK-Controllermodelle für Windows Mixed Reality und OpenVR.</span><span class="sxs-lookup"><span data-stu-id="8310f-277">The MRTK also supports native SDK controller models for Windows Mixed Reality and OpenVR.</span></span> <span data-ttu-id="8310f-278">Diese werden als GameObjects in Ihre Szene geladen und mithilfe der Controllernachverfolgung der Plattform positioniert.</span><span class="sxs-lookup"><span data-stu-id="8310f-278">These are loaded as GameObjects in your scene and positioned using the platform's controller tracking.</span></span>

<span data-ttu-id="8310f-279">Wenn Ihre Controllerdarstellung in der Szene von der Position des physischen Controllers versetzt werden muss, legen Sie diesen Offset einfach auf das Prefab des Controllermodells fest (z. B. Festlegen der Transformationsposition des Controller-Prefabs mit einer Offsetposition).</span><span class="sxs-lookup"><span data-stu-id="8310f-279">If your controller representation in the scene needs to be offset from the physical controller position, then simply set that offset against the controller model's prefab (e.g. setting the transform position of the controller prefab with an offset position).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerVisualizationProfile.png" width="650px" alt="Visualization profile" style="display:block;">

<a name="editor-utilities"></a>

## <a name="editor-utilities"></a><span data-ttu-id="8310f-280">Editor-Hilfsprogramme</span><span class="sxs-lookup"><span data-stu-id="8310f-280">Editor utilities</span></span>

<span data-ttu-id="8310f-281">Die folgenden Hilfsprogramme funktionieren nur im Editor und sind nützlich, um die Entwicklungsproduktivität zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="8310f-281">The following utilities work only in the editor and are useful to improve development productivity.</span></span>

![MRTK-Editor-Konfigurationsprogramme](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_EditorConfiguration.png)

### <a name="service-inspectors"></a><span data-ttu-id="8310f-283">Dienstinspektoren</span><span class="sxs-lookup"><span data-stu-id="8310f-283">Service inspectors</span></span>

<span data-ttu-id="8310f-284">Dienstinspektoren sind ein Nur-Editor-Feature, das Szenenobjekte generiert, die aktive Dienste darstellen.</span><span class="sxs-lookup"><span data-stu-id="8310f-284">Service Inspectors are an editor-only feature that generates in-scene objects representing active services.</span></span> <span data-ttu-id="8310f-285">Wenn Sie diese Objekte auswählen, werden Inspektoren angezeigt, die Dokumentationslinks, die Kontrolle über Editorvisualisierungen und Einblicke in den Zustand des Diensts bieten.</span><span class="sxs-lookup"><span data-stu-id="8310f-285">Selecting these objects displays inspectors which offer documentation links, control over editor visualizations and insight into the state of the service.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ServiceInspectors.PNG" width="350px" alt="Service Inspectors" style="display:block;">

<span data-ttu-id="8310f-286">Sie können Dienstinspektoren aktivieren, indem Sie *im* Konfigurationsprofil unter *Editoreinstellungen* die Option Dienstinspektoren verwenden aktivieren.</span><span class="sxs-lookup"><span data-stu-id="8310f-286">You can enable service inspectors by checking *Use Service Inspectors* under *Editor Settings* in the Configuration Profile.</span></span>

### <a name="depth-buffer-renderer"></a><span data-ttu-id="8310f-287">Tiefenpufferrenderer</span><span class="sxs-lookup"><span data-stu-id="8310f-287">Depth buffer renderer</span></span>

<span data-ttu-id="8310f-288">Die Gemeinsame Nutzung des Tiefenpuffers mit einigen Mixed Reality-Plattformen kann die [Hologrammstabilisierung verbessern.](../performance/hologram-stabilization.md)</span><span class="sxs-lookup"><span data-stu-id="8310f-288">Sharing the depth buffer with some mixed reality platforms can improve [hologram stabilization](../performance/hologram-stabilization.md).</span></span> <span data-ttu-id="8310f-289">Beispielsweise kann die Windows Mixed Reality-Plattform die gerenderte Szene pro Pixel ändern, um während der Zeit, die zum Rendern eines Frames gezeitet hat, kleine Kopfbewegungen zu berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="8310f-289">For example, the Windows Mixed Reality platform can modify the rendered scene per-pixel to account for subtle head movements during the time it took to render a frame.</span></span> <span data-ttu-id="8310f-290">Diese Techniken erfordern jedoch Tiefenpuffer mit genauen Daten, um zu wissen, wo und wie weit die Geometrie vom Benutzer entfernt ist.</span><span class="sxs-lookup"><span data-stu-id="8310f-290">However, these techniques require depth buffers with accurate data to know where and how far geometry is from the user.</span></span>

<span data-ttu-id="8310f-291">Um sicherzustellen, dass eine Szene alle erforderlichen Daten im Tiefenpuffer rendert, können Entwickler im Konfigurationsprofil unter *Editoreinstellungen* das Feature *Render depth buffer* (Tiefenpuffer rendern) umschalten.</span><span class="sxs-lookup"><span data-stu-id="8310f-291">To ensure a scene renders all necessary data to the depth buffer, developers can toggle the *Render Depth Buffer* feature under *Editor Settings* in the Configuration Profile.</span></span> <span data-ttu-id="8310f-292">Dadurch wird der aktuelle Tiefenpuffer als Farbe für die Szenenansicht gerendert, indem der Nachbearbeitungseffekt auf die [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer) Hauptkamera anwenden wird.</span><span class="sxs-lookup"><span data-stu-id="8310f-292">This will take the current depth buffer and render it as color to the scene view by applying a post-processing effect, [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer), to the main camera.</span></span>

<span data-ttu-id="8310f-293">![Hilfsprogramm für Tiefenpuffer rendern Der blaue Zylinder in der Szene verfügt über ein Material mit ](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
 <sup>deaktiviertem ZWrite, sodass keine Tiefendaten geschrieben werden</sup></span><span class="sxs-lookup"><span data-stu-id="8310f-293">![Render Depth Buffer Utility](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
<sup>The blue cylinder in the scene has a material with ZWrite off so no depth data is written</sup></span></span>

## <a name="changing-profiles-at-runtime"></a><span data-ttu-id="8310f-294">Ändern von Profilen zur Laufzeit</span><span class="sxs-lookup"><span data-stu-id="8310f-294">Changing profiles at runtime</span></span>

<span data-ttu-id="8310f-295">Es ist möglich, Profile zur Laufzeit zu aktualisieren, und es gibt in der Regel zwei verschiedene Szenarien und Zeiten, in denen dies hilfreich ist:</span><span class="sxs-lookup"><span data-stu-id="8310f-295">It is possible to update profiles at runtime, and there are generally two different scenarios and times in which in this is helpful:</span></span>

1. <span data-ttu-id="8310f-296">Schalter für das Pre MRTK-Initialisierungsprofil: Ersetzen Sie beim Start, bevor das MRTK initialisiert und das Profil aktiv wird, das noch nicht in Gebrauch war, um verschiedene Features basierend auf den Gerätefunktionen zu aktivieren/deaktivieren. </span><span class="sxs-lookup"><span data-stu-id="8310f-296">**Pre MRTK initialization profile switch**: At startup, before the MRTK is initialized and profile becomes active, replacing the not-yet-in-use profile to enable/disable different features based on the device capabilities.</span></span> <span data-ttu-id="8310f-297">Wenn die Umgebung beispielsweise in VR ohne Hardware für die räumliche Zuordnung ausgeführt wird, ist es wahrscheinlich nicht sinnvoll, die Komponente für die räumliche Zuordnung zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="8310f-297">For example, if the experience is running in VR that doesn't have spatial mapping hardware it probably doesn't make sense to have spatial mapping component enabled.</span></span>
1. <span data-ttu-id="8310f-298">**Aktiver Profilwechsel:** Tauschen Sie nach dem Start, nachdem das MRTK initialisiert und ein Profil aktiv wurde, das aktuell verwendete Profil aus, um das Verhalten bestimmter Features zu ändern.</span><span class="sxs-lookup"><span data-stu-id="8310f-298">**Active profile switch**: After startup, after the MRTK is initialized and a profile has become active, swapping the profile currently in use to change the way certain features behave.</span></span> <span data-ttu-id="8310f-299">Es kann z. B. eine bestimmte untergeordnete Beerfahrung in der Anwendung geben, die möchte, dass die zeigerweiten Zeiger vollständig entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="8310f-299">For example, there may be a specific sub-experience in the application that wants far hand pointers completely removed.</span></span>

### <a name="pre-mrtk-initialization-profile-switch"></a><span data-ttu-id="8310f-300">Pre MRTK-Initialisierungsprofilschalter</span><span class="sxs-lookup"><span data-stu-id="8310f-300">Pre MRTK initialization profile switch</span></span>

<span data-ttu-id="8310f-301">Dies kann erreicht werden, indem Ein MonoBehaviour (Beispiel unten) angefügt wird, das vor der MRTK-Initialisierung ausgeführt wird (d. h. Awake()).</span><span class="sxs-lookup"><span data-stu-id="8310f-301">This can be accomplished by attaching a MonoBehaviour (example below) which runs before MRTK initialization (i.e. Awake()).</span></span> <span data-ttu-id="8310f-302">Beachten Sie, dass das Skript (d. h. der Aufruf von ) vor dem Skript ausgeführt werden muss. Dies `SetProfileBeforeInitialization` kann durch Festlegen der `MixedRealityToolkit` [Skriptausführungsreihenfolge-Einstellungen](https://docs.unity3d.com/Manual/class-MonoManager.html)erreicht werden.</span><span class="sxs-lookup"><span data-stu-id="8310f-302">Note the script (i.e. call to `SetProfileBeforeInitialization`) have to be executed earlier than the `MixedRealityToolkit` script, which can be achieved by setting [Script Execution Order settings](https://docs.unity3d.com/Manual/class-MonoManager.html).</span></span>

```csharp
using Microsoft.MixedReality.Toolkit;
using UnityEngine;

/// <summary>
/// Sample MonoBehaviour that will run before the MixedRealityToolkit object, and change
/// the profile, so that when the MRTK initializes it uses the profile specified below
/// rather than the one that is saved in its scene.
/// </summary>
/// <remarks>
/// Note that this script must have a higher priority in the script execution order compared
/// to that of MixedRealityToolkit.cs. See https://docs.unity3d.com/Manual/class-MonoManager.html
/// for more information on script execution order.
/// </remarks>
public class PreInitProfileSwapper : MonoBehaviour
{

    [SerializeField]
    private MixedRealityToolkitConfigurationProfile profileToUse = null;

    private void Awake()
    {
        // Here you could choose any arbitrary MixedRealityToolkitConfigurationProfile (for example, you could
        // add some platform checking code here to determine which profile to load).
        MixedRealityToolkit.SetProfileBeforeInitialization(profileToUse);
    }
}
```

<span data-ttu-id="8310f-303">Anstelle von "profileToUse" ist es möglich, über einen beliebigen Satz von Profilen zu verfügen, die für bestimmte Plattformen gelten (z. B. eine für HoloLens 1, eine für VR, eine für HoloLens 2 usw.).</span><span class="sxs-lookup"><span data-stu-id="8310f-303">Instead of "profileToUse", it's possible to have some arbitrary set of profiles which apply to specific platforms (for example, one for HoloLens 1, one for VR, one for HoloLens 2, etc).</span></span> <span data-ttu-id="8310f-304">Es ist möglich, verschiedene andere Indikatoren (z. B. oder ob https://docs.unity3d.com/ScriptReference/SystemInfo.html die Kamera deckend/transparent ist) zu verwenden, um herauszufinden, welches Profil geladen werden soll.</span><span class="sxs-lookup"><span data-stu-id="8310f-304">It's possible to use various other indicators (e.g. https://docs.unity3d.com/ScriptReference/SystemInfo.html, or whether or not the camera is opaque/transparent), to figure out which profile to load.</span></span>

### <a name="active-profile-switch"></a><span data-ttu-id="8310f-305">Aktiver Profilschalter</span><span class="sxs-lookup"><span data-stu-id="8310f-305">Active profile switch</span></span>

<span data-ttu-id="8310f-306">Dies kann erreicht werden, indem die -Eigenschaft auf ein neues Profil festgelegt wird, `MixedRealityToolkit.Instance.ActiveProfile` das das aktive Profil ersetzt.</span><span class="sxs-lookup"><span data-stu-id="8310f-306">This can be accomplished by setting the `MixedRealityToolkit.Instance.ActiveProfile` property to a new profile replacing the active profile.</span></span>

```csharp
MixedRealityToolkit.Instance.ActiveProfile = profileToUse;
```

<span data-ttu-id="8310f-307">Beachten Sie, dass beim Festlegen `ActiveProfile` während der Laufzeit die Zerstörung der derzeit ausgeführten Dienste nach dem letzten LateUpdate() aller Dienste erfolgt, und die Instanziierung und Initialisierung der Dienste, die dem neuen Profil zugeordnet sind, erfolgt vor dem ersten Update() aller Dienste.</span><span class="sxs-lookup"><span data-stu-id="8310f-307">Note when setting `ActiveProfile` during runtime, the destroy of the currently running services will happen after the last LateUpdate() of all services, and the instantiation and initialization of the services associated with the new profile will happen before the first Update() of all services.</span></span>

<span data-ttu-id="8310f-308">Während dieses Prozesses kann es zu einer merklichen Anwendungsbeendigung kommen.</span><span class="sxs-lookup"><span data-stu-id="8310f-308">A noticeable application hesitation may occur during this process.</span></span> <span data-ttu-id="8310f-309">Außerdem kann jedes Skript mit höherer Priorität als das `MixedRealityToolkit` Skript sein Update eingeben, bevor das neue Profil ordnungsgemäß eingerichtet wird.</span><span class="sxs-lookup"><span data-stu-id="8310f-309">Also any script with higher priority than the `MixedRealityToolkit` script can enter its Update before the new profile is properly setup.</span></span> <span data-ttu-id="8310f-310">Weitere Informationen zur Skriptpriorität finden Sie unter [Skriptausführungsreihenfolgeeinstellungen.](https://docs.unity3d.com/Manual/class-MonoManager.html)</span><span class="sxs-lookup"><span data-stu-id="8310f-310">See [Script Execution Order settings](https://docs.unity3d.com/Manual/class-MonoManager.html) for more information on script priority.</span></span>

<span data-ttu-id="8310f-311">Im Prozess zum Wechseln des Profils bleibt die vorhandene UI-Kamera unverändert, um sicherzustellen, dass Komponenten der Unity-Benutzeroberfläche, die Canvas erfordern, nach dem Wechsel weiterhin funktionieren.</span><span class="sxs-lookup"><span data-stu-id="8310f-311">In the profile switching process the existing UI camera will remain unchanged, ensuring Unity UI components that require canvas still work after the switch.</span></span>

## <a name="see-also"></a><span data-ttu-id="8310f-312">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="8310f-312">See also</span></span>

- [<span data-ttu-id="8310f-313">Hologrammstabilisierung</span><span class="sxs-lookup"><span data-stu-id="8310f-313">Hologram Stabilization</span></span>](../performance/hologram-stabilization.md)