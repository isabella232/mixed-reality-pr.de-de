---
title: Versionshinweise für das OpenXR-Plug-In für Mixed Reality
description: Bleiben Sie über die neuesten Versionshinweise und Upgrades für das OpenXR-Plug-In für Mixed Reality auf dem Laufenden.
author: hferrone
ms.author: v-hferrone
ms.date: 06/18/2021
ms.topic: article
ms.localizationpriority: high
keywords: Aktuell, Tools, Erste Schritte, Grundlagen, Unity, Visual Studio, Toolkit, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Installation, Windows, HoloLens, Emulator, Unreal, OpenXR
ms.openlocfilehash: c926fbb758d7cfaa2e73b5357cacdab7a5d15e27
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394629"
---
# <a name="mixed-reality-openxr-plugin-release-notes"></a><span data-ttu-id="cc9bc-104">Versionshinweise für das OpenXR-Plug-In für Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="cc9bc-104">Mixed Reality OpenXR plugin release notes</span></span>

## <a name="100---current-release"></a><span data-ttu-id="cc9bc-105">1.0.0 – Aktuelle Version</span><span class="sxs-lookup"><span data-stu-id="cc9bc-105">1.0.0 - Current release</span></span>

* <span data-ttu-id="cc9bc-106">Ein Fehler wurde behoben, bei dem das XRAnchorSubsystem beim Starten der App immer gestartet wurde, unabhängig davon, ob ARAnchorManager vorhanden war.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-106">Fixed a bug where a the XRAnchorSubsystem was always started on app start regardless ARAnchorManager’s present.</span></span>
* <span data-ttu-id="cc9bc-107">Ein Fehler wurde behoben, bei dem der Neuprojektionsmodus nicht ordnungsgemäß funktionierte.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-107">Fixed a bug where the reprojection mode didn’t work properly.</span></span>

## <a name="100-preview2---2021-06-14"></a><span data-ttu-id="cc9bc-108">1.0.0-preview.2 – 2021-06-14</span><span class="sxs-lookup"><span data-stu-id="cc9bc-108">1.0.0-preview.2 - 2021-06-14</span></span>

* <span data-ttu-id="cc9bc-109">Abhängig vom OpenXR 1.2.2-Plug-In von Unity.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-109">Depends on Unity’s 1.2.2 OpenXR plugin.</span></span>
* <span data-ttu-id="cc9bc-110">Holographic Remoting-Features wurden in einzelne Featuregruppen geändert.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-110">Changed Holographic Remoting features in to individual feature groups.</span></span>
* <span data-ttu-id="cc9bc-111">Ein Fehler wurde behoben, bei dem „HoloLens 2-Projekteinstellungen anwenden“ den Farbraum des Projekts geändert hat.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-111">Fixed a bug where “Apply HoloLens 2 project settings” changes project color space.</span></span> <span data-ttu-id="cc9bc-112">Dies ist seit dem OpenXR 1.2.0-Plug-In von Unity nicht mehr erforderlich.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-112">This is no longer needed after Unity OpenXR 1.2.0 plugin.</span></span>
* <span data-ttu-id="cc9bc-113">Ein Fehler wurde behoben, bei dem ein Eingabegerät verbunden wurde, ohne die Verbindung zu trennen, nachdem die Anwendung angehalten und wieder fortgesetzt wurde.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-113">Fixed a bug where a input device get connected without disconnect after application suspended and resumed.</span></span>
* <span data-ttu-id="cc9bc-114">Unterstützung für die Erkennung von Plug-Ins und aktuellen Nachverfolgungszuständen über ARSession wurde hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-114">Added support for detecting plugin and current tracking states via ARSession.</span></span>
* <span data-ttu-id="cc9bc-115">Ein Fehler wurde behoben, bei dem das ARFoundation-Prefab „AR Default Plane“ (AR-Standardebene) nicht sichtbar war.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-115">Fixed a bug where the “AR Default Plane” ARFoundation prefab wouldn’t be visible.</span></span>

## <a name="100-preview1---2021-06-02"></a><span data-ttu-id="cc9bc-116">1.0.0-preview.1 – 2021-06-02</span><span class="sxs-lookup"><span data-stu-id="cc9bc-116">1.0.0-preview.1 - 2021-06-02</span></span>

* <span data-ttu-id="cc9bc-117">Unterstützt MSFT-Erweiterungen für OpenXR-Szenenverständnis anstelle von Vorschauerweiterungen.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-117">Supports OpenXR scene understanding MSFT extensions instead of preview extensions.</span></span>
* <span data-ttu-id="cc9bc-118">Die Ebenenerkennung von HoloLens 2 erfordert keine Vorschauversionen der OpenXR-Runtimes für Mixed Reality mehr.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-118">Plane detection on HoloLens 2 no longer requires preview versions of the Mixed Reality OpenXR runtimes.</span></span>

## <a name="095---2021-05-21"></a><span data-ttu-id="cc9bc-119">0.9.5 – 2021-05-21</span><span class="sxs-lookup"><span data-stu-id="cc9bc-119">0.9.5 - 2021-05-21</span></span>

* <span data-ttu-id="cc9bc-120">Abhängig vom OpenXR-Plug-In 1.2.0 von Unity</span><span class="sxs-lookup"><span data-stu-id="cc9bc-120">Depends on Unity’s 1.2.0 OpenXR Plugin</span></span>
* <span data-ttu-id="cc9bc-121">Angepasst an die neue Featurebenutzeroberfläche (in OpenXR-Plug-In 1.2.0) für die Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-121">Adapted to the new feature UI (in OpenXR Plugin 1.2.0) for configuration.</span></span>
* <span data-ttu-id="cc9bc-122">Ein Fehler wurde behoben, bei dem die Registrierung des Anbieters für auffindbare Kameras nicht ordnungsgemäß aufgehoben wurde.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-122">Fixed a bug where the locatable camera provider wasn’t properly unregistering.</span></span>
* <span data-ttu-id="cc9bc-123">Einige zusätzliche Verwendungen von [Preserve] (Beibehalten) wurden bereinigt.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-123">Cleaned up some extra usages of [Preserve].</span></span>
* <span data-ttu-id="cc9bc-124">Der Name „HP Reverb G2 Controller (OpenXR)“ in der Benutzeroberfläche des Eingabesystems wurde aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-124">Update “HP Reverb G2 Controller (OpenXR)” name in the input system UI.</span></span>

## <a name="094---2021-05-20"></a><span data-ttu-id="cc9bc-125">0.9.4 – 2021-05-20</span><span class="sxs-lookup"><span data-stu-id="cc9bc-125">0.9.4 - 2021-05-20</span></span>

* <span data-ttu-id="cc9bc-126">Abhängig vom OpenXR-Plug-In 1.2.0 von Unity.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-126">Depends on Unity’s 1.2.0 OpenXR Plugin.</span></span>
* <span data-ttu-id="cc9bc-127">Neue C#-API zum Abrufen des glTF-Modells für den Motion-Controller hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-127">Added new C# API to get motion controller glTF model.</span></span>
* <span data-ttu-id="cc9bc-128">Neue C#-API zum Abrufen aktivierter Ansichtskonfigurationen und zum Festlegen von Neuprojektionseinstellungen hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-128">Added new C# API to get enabled view configurations and set reprojection settings.</span></span>
* <span data-ttu-id="cc9bc-129">Neue C#-API zum Festlegen zusätzlicher Einstellungen für die Berechnung von Gittermodellen mit XRMeshSubsystem hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-129">Added new C# API to set additional settings for computing meshes with XRMeshSubsystem.</span></span>
* <span data-ttu-id="cc9bc-130">Neue C#-API zum Konfigurieren und Abonnieren von Gestenerkennungsereignissen hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-130">Added new C# API to configure and subscribe to gesture recognition events.</span></span>
* <span data-ttu-id="cc9bc-131">Dialogfeld mit „Windows->XR->Editor Remoting settings“ (Editor-Remoting-Einstellungen) hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-131">Added Windows->XR->Editor Remoting settings dialog.</span></span>
* <span data-ttu-id="cc9bc-132">ARM-Unterstützung für HoloLens UWP-Anwendungen hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-132">Added ARM support for HoloLens UWP applications.</span></span>

## <a name="093---2021-04-29"></a><span data-ttu-id="cc9bc-133">0.9.3 – 2021-04-29</span><span class="sxs-lookup"><span data-stu-id="cc9bc-133">0.9.3 - 2021-04-29</span></span>

* <span data-ttu-id="cc9bc-134">Ein Fehler wurde behoben, bei dem die Holographic Remoting-Verbindung nicht zuverlässig ist.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-134">Fixed a bug where Holographic remoting connection is not reliable</span></span>
* <span data-ttu-id="cc9bc-135">Ein Fehler wurde behoben, bei dem die VR-Renderingleistung nach dem Upgrade auf das OpenXR-Plug-In 1.1.1 von Unity suboptimal ist.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-135">Fixed a bug where the VR rendering performance is sub-optimum after upgrade to Unity’s 1.1.1 OpenXR plugin.</span></span>

## <a name="092---2021-04-21"></a><span data-ttu-id="cc9bc-136">0.9.2 0 – 2021-04-21</span><span class="sxs-lookup"><span data-stu-id="cc9bc-136">0.9.2 - 2021-04-21</span></span>

* <span data-ttu-id="cc9bc-137">Die Ebenenerkennung von HoloLens 2 in Plug-In-Version 0.9.1 funktioniert mit Version 105 der OpenXR-Vorschaulaufzeit für Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-137">Plane detection on HoloLens 2 in plugin version 0.9.1 will work with version 105 of the Mixed Reality OpenXR preview runtime.</span></span>
* <span data-ttu-id="cc9bc-138">Die Ebenenerkennung von HoloLens 2 in Plug-In-Version 0.9.2 funktioniert mit Version 106 der OpenXR-Vorschaulaufzeit für Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-138">Plane detection on HoloLens 2 in plugin version 0.9.2 will work with version 106 of the Mixed Reality OpenXR preview runtime.</span></span>
* <span data-ttu-id="cc9bc-139">Einige nicht verwendete Rückrufe wurden aus InputProvider entfernt, um zu verhindern, dass Aufrufe wie „XRInputSubsystem.\* GetTrackingOriginMode“ (die nicht von unserem Eingabesystem verwaltet werden) erfolgreich mit irreführenden Werten zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-139">Removed some unused callbacks from InputProvider to prevent calls like XRInputSubsystem.\* GetTrackingOriginMode (which aren’t managed by our input system) from returning success with misleading values.</span></span>
* <span data-ttu-id="cc9bc-140">Die veraltete Version von XRAnchorStore wurde in eine eigene Datei ausgegliedert, um Unity-Konsolenwarnungen zu verhindern.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-140">Split out deprecated version of XRAnchorStore into its own file to prevent Unity console warning.</span></span>

## <a name="091---2021-04-20"></a><span data-ttu-id="cc9bc-141">0.9.1 – 2021-04-20</span><span class="sxs-lookup"><span data-stu-id="cc9bc-141">0.9.1 - 2021-04-20</span></span>

* <span data-ttu-id="cc9bc-142">Abhängig vom OpenXR-Plug-In 1.1.1 von Unity.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-142">Depends on Unity’s 1.1.1 OpenXR Plugin.</span></span>
* <span data-ttu-id="cc9bc-143">Unterstützung für eine Holographic Remoting-Anwendung für die UWP-Plattform hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-143">Added support for Holographic Remoting application for UWP platform.</span></span>
* <span data-ttu-id="cc9bc-144">UnityException wurde behoben, bei der XRAnchorStore versuchte, eine Instanz der Einstellungen außerhalb des Hauptthreads abzurufen.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-144">Fix UnityException where XRAnchorStore was trying to get a settings instance outside the main thread.</span></span>

## <a name="090---2021-03-29"></a><span data-ttu-id="cc9bc-145">0.9.0 – 2021-03-29</span><span class="sxs-lookup"><span data-stu-id="cc9bc-145">0.9.0 - 2021-03-29</span></span>

* <span data-ttu-id="cc9bc-146">Unterstützung für räumliche Abbildung über XRMeshSubsystem und ARMeshManager wurde hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-146">Added support for spatial mapping via XRMeshSubsystem and ARMeshManager.</span></span>
* <span data-ttu-id="cc9bc-147">Neue C#-API zum Abrufen von OpenXR-Handles zur Unterstützung anderer Unity-Pakete, die OpenXR-Erweiterungen nutzen, hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-147">Added new C# API to get OpenXR handles to support other Unity packages consumes OpenXR extensions.</span></span>
* <span data-ttu-id="cc9bc-148">Neue C#-API für Interoperabilität mit Windows.Perception-APIs zur Unterstützung anderer Unity-Pakete, die Perception WinRT-APIs nutzen, hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-148">Added new C# API to interop with Windows.Perception APIs to support other Unity packages consuming Perception WinRT APIs.</span></span>
* <span data-ttu-id="cc9bc-149">Interaktionsprofile aus erforderlichen Features im Windows Mixed Reality-Featuresatz entfernt, sodass Entwickler die Motion-Controller auswählen können, mit denen sie Tests durchführen.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-149">Removed interaction profiles from required features in Windows Mixed Reality feature set, so developers can choose the motion controllers they tested with.</span></span>
* <span data-ttu-id="cc9bc-150">Eine Validierung des Remotingfeatures des Holographic-Editors wurde hinzugefügt, um Benutzern die ordnungsgemäße Einrichtung des Editor-Remotings zu erleichtern.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-150">Added Holographic editor remoting feature validator to help users to setup editor remoting properly.</span></span>
* <span data-ttu-id="cc9bc-151">Ein Fehler wurde behoben, bei dem der Unity-Editor abstürzte, wenn der Remotingmodus des Holographic-Editors nach einem Verbindungsfehler beendet wurde.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-151">Fixed a bug where Unity editor crashes when exiting Holographic editor remoting mode after connection failure.</span></span>
* <span data-ttu-id="cc9bc-152">Ein Fehler wurde behoben, bei dem nicht vorab vervielfältigte Alphatexturen zu suboptimaler Leistung bei HoloLens 2 geführt haben.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-152">Fixed a bug where unpremultipled alpha textures leads to sub-optimum performance on HoloLens 2.</span></span>
* <span data-ttu-id="cc9bc-153">Ein Fehler wurde behoben, bei dem die Handverfolgung nicht ordnungsgemäß positioniert war, wenn sich der Szenenursprung auf Höhe des Bodens befand.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-153">Fixed a bug where hand tracking was not located correctly when the scene origin was at floor level.</span></span>
* <span data-ttu-id="cc9bc-154">Ein Fehler wurde behoben, bei dem die Hand-Mesh-Verfolgung nach dem Verlassen und Laden einer neuen Szene verschwunden ist.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-154">Fixed a bug where hand mesh tracking disappear after leaving and loading a new scene.</span></span>
* <span data-ttu-id="cc9bc-155">Ein Fehler wurde behoben, bei dem der Anbieter für auffindbare Kameras nicht ordnungsgemäß bereinigt wurde.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-155">Fixed a bug where locatable camera provider didn’t properly clean up.</span></span>
* <span data-ttu-id="cc9bc-156">Der Namespace der XRAnchorStore-API wurde zu „Microsoft.MixedReality.OpenXR“ überarbeitet.</span><span class="sxs-lookup"><span data-stu-id="cc9bc-156">Revised the namespace of XRAnchorStore API into Microsoft.MixedReality.OpenXR.</span></span>