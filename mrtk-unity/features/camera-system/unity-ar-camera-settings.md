---
title: Unity AR-Kameraeinstellungen
description: Dokumentation zur Verwendung der AR-Kamera in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, AR-Kamera,
ms.openlocfilehash: e1c032805bc4b733cfcc51e1ceac5096c73715cf
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121198"
---
# <a name="unity-ar-camera-settings-provider"></a><span data-ttu-id="b87d1-104">Unity AR-Kameraeinstellungsanbieter</span><span class="sxs-lookup"><span data-stu-id="b87d1-104">Unity AR camera settings provider</span></span>

<span data-ttu-id="b87d1-105">Der Unity AR-Kameraeinstellungsanbieter ist eine experimentelle MRTK-Komponente, mit der Mixed Reality-Anwendungen auf Android- und iOS-Geräten ausgeführt werden können.</span><span class="sxs-lookup"><span data-stu-id="b87d1-105">The Unity AR camera settings provider is an experimental MRTK component that enables mixed reality applications to run on Android and iOS devices.</span></span>

## <a name="unity-ar-camera-settings-provider-options"></a><span data-ttu-id="b87d1-106">Optionen des Unity AR-Kameraeinstellungsanbieters</span><span class="sxs-lookup"><span data-stu-id="b87d1-106">Unity AR camera settings provider options</span></span>

![Konfiguration der Unity AR-Kameraeinstellungen](../images/camera-system/UnityArSettingsConfiguration.png)

<span data-ttu-id="b87d1-108">Eine Anleitung zum Hinzufügen des Anbieters zu Ihrer Szene: [Konfigurieren von MRTK für iOS und Android](../../supported-devices/using-ar-foundation.md)</span><span class="sxs-lookup"><span data-stu-id="b87d1-108">For a guide on how to add the provider to your scene: [How to configure MRTK for iOS and Android](../../supported-devices/using-ar-foundation.md)</span></span>

### <a name="tracking-settings"></a><span data-ttu-id="b87d1-109">Nachverfolgungseinstellungen</span><span class="sxs-lookup"><span data-stu-id="b87d1-109">Tracking settings</span></span>

<span data-ttu-id="b87d1-110">Der Unity AR-Kameraeinstellungsanbieter ermöglicht Konfigurationsoptionen für die Nachverfolgung.</span><span class="sxs-lookup"><span data-stu-id="b87d1-110">The Unity AR camera settings provider allows configuration options for how tracking is performed.</span></span> <span data-ttu-id="b87d1-111">Diese Einstellungen sind spezifisch für die Implementierung des Unity AR-Kameraeinstellungsanbieters.</span><span class="sxs-lookup"><span data-stu-id="b87d1-111">These settings are specific to the Unity AR camera settings provider implementation.</span></span>

<span data-ttu-id="b87d1-112">**Pose-Quelle**</span><span class="sxs-lookup"><span data-stu-id="b87d1-112">**Pose Source**</span></span>

<span data-ttu-id="b87d1-113">Die Posenquelle definiert die verfügbaren Typen von Augmented Reality-Nachverfolgungsposen.</span><span class="sxs-lookup"><span data-stu-id="b87d1-113">The pose source defines the available types of augmented reality tracking poses.</span></span> <span data-ttu-id="b87d1-114">Im Allgemeinen werden diese Werte einer Komponente des Geräts zugeordnet, auf dem die Anwendung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="b87d1-114">In general, these values map to a component of the device on which the application is running.</span></span>

<span data-ttu-id="b87d1-115">Die verfügbaren Optionen werden in der folgenden Tabelle beschrieben.</span><span class="sxs-lookup"><span data-stu-id="b87d1-115">The available options are described in the following table.</span></span>

| <span data-ttu-id="b87d1-116">Option</span><span class="sxs-lookup"><span data-stu-id="b87d1-116">Option</span></span> | <span data-ttu-id="b87d1-117">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b87d1-117">Description</span></span> |
| --- | --- |
| <span data-ttu-id="b87d1-118">Zentrum</span><span class="sxs-lookup"><span data-stu-id="b87d1-118">Center</span></span> | <span data-ttu-id="b87d1-119">Das mittlere Auge eines mit dem Kopf bestückten Geräts.</span><span class="sxs-lookup"><span data-stu-id="b87d1-119">The center eye of a head mounted device.</span></span> |
| <span data-ttu-id="b87d1-120">Farbkamera</span><span class="sxs-lookup"><span data-stu-id="b87d1-120">Color Camera</span></span> | <span data-ttu-id="b87d1-121">Die Farbkamera eines mobilen Geräts.</span><span class="sxs-lookup"><span data-stu-id="b87d1-121">The color camera of a mobile device.</span></span> |
| <span data-ttu-id="b87d1-122">Head</span><span class="sxs-lookup"><span data-stu-id="b87d1-122">Head</span></span> | <span data-ttu-id="b87d1-123">Das Kopfauge eines mit dem Kopf bestückten Geräts, häufig etwas über dem mittleren Auge.</span><span class="sxs-lookup"><span data-stu-id="b87d1-123">The head eye of a head mounted device, often slightly above the center eye.</span></span> |
| <span data-ttu-id="b87d1-124">Linkes Auge</span><span class="sxs-lookup"><span data-stu-id="b87d1-124">Left Eye</span></span> | <span data-ttu-id="b87d1-125">Das linke Auge eines auf dem Kopf installierten Geräts.</span><span class="sxs-lookup"><span data-stu-id="b87d1-125">The left eye of a head mounted device.</span></span> |
| <span data-ttu-id="b87d1-126">Linke Pose</span><span class="sxs-lookup"><span data-stu-id="b87d1-126">Left Pose</span></span> | <span data-ttu-id="b87d1-127">Die linke Controllerpose.</span><span class="sxs-lookup"><span data-stu-id="b87d1-127">The left hand controller pose.</span></span> |
| <span data-ttu-id="b87d1-128">Rechtes Auge</span><span class="sxs-lookup"><span data-stu-id="b87d1-128">Right Eye</span></span> | <span data-ttu-id="b87d1-129">Das rechte Auge eines am Kopf eingebauten Geräts.</span><span class="sxs-lookup"><span data-stu-id="b87d1-129">The right eye of a head mounted device.</span></span> |
| <span data-ttu-id="b87d1-130">Rechte Pose</span><span class="sxs-lookup"><span data-stu-id="b87d1-130">Right Pose</span></span> | <span data-ttu-id="b87d1-131">Die rechte Controllerpose.</span><span class="sxs-lookup"><span data-stu-id="b87d1-131">The right hand controller pose.</span></span> |

<span data-ttu-id="b87d1-132">Der Standardwert für die Posenquelle ist **Farbkamera**, um eine transparente Anzeige auf mobilen Geräten wie einem Smartphone oder Tablet zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="b87d1-132">The default value for pose source is **Color Camera**, to enable a transparent display on mobile devices, such as a phone or tablet.</span></span>

<span data-ttu-id="b87d1-133">**Überwachungstyp**</span><span class="sxs-lookup"><span data-stu-id="b87d1-133">**Tracking Type**</span></span>

<span data-ttu-id="b87d1-134">Der Nachverfolgungstyp definiert die Teile der Pose, die für die Nachverfolgung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="b87d1-134">The tracking type defines the portion(s) of the pose that will be used for tracking.</span></span>

<span data-ttu-id="b87d1-135">Die verfügbaren Optionen werden in der folgenden Tabelle beschrieben.</span><span class="sxs-lookup"><span data-stu-id="b87d1-135">The available options are described in the following table.</span></span>

| <span data-ttu-id="b87d1-136">Option</span><span class="sxs-lookup"><span data-stu-id="b87d1-136">Option</span></span> | <span data-ttu-id="b87d1-137">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b87d1-137">Description</span></span> |
| --- | --- |
| <span data-ttu-id="b87d1-138">Position</span><span class="sxs-lookup"><span data-stu-id="b87d1-138">Position</span></span> | <span data-ttu-id="b87d1-139">Die Position des Geräts.</span><span class="sxs-lookup"><span data-stu-id="b87d1-139">The position of the device.</span></span> |
| <span data-ttu-id="b87d1-140">Drehung</span><span class="sxs-lookup"><span data-stu-id="b87d1-140">Rotation</span></span> | <span data-ttu-id="b87d1-141">Die Drehung des Geräts.</span><span class="sxs-lookup"><span data-stu-id="b87d1-141">The rotation of the device.</span></span> |
| <span data-ttu-id="b87d1-142">Drehung und Position</span><span class="sxs-lookup"><span data-stu-id="b87d1-142">Rotation And Position</span></span> | <span data-ttu-id="b87d1-143">Die Position und Drehung des Geräts.</span><span class="sxs-lookup"><span data-stu-id="b87d1-143">The position and rotation of the device.</span></span> |

<span data-ttu-id="b87d1-144">Der Standardwert für den Nachverfolgungstyp ist **Drehung und Position**, um die größtmögliche Nachverfolgungserfahrung zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="b87d1-144">The default value for tracking type is **Rotation And Position**, to enable the richest tracking experience.</span></span>

<span data-ttu-id="b87d1-145">**Updatetyp**</span><span class="sxs-lookup"><span data-stu-id="b87d1-145">**Update Type**</span></span>

<span data-ttu-id="b87d1-146">Der Updatetyp definiert, an welchen Punkten während der Frameverarbeitung die Pose-Daten entnommen werden.</span><span class="sxs-lookup"><span data-stu-id="b87d1-146">The update type defines at what points, during frame processing, the pose data will be sampled.</span></span>

<span data-ttu-id="b87d1-147">Die verfügbaren Optionen werden in der folgenden Tabelle beschrieben.</span><span class="sxs-lookup"><span data-stu-id="b87d1-147">The available options are described in the following table.</span></span>

| <span data-ttu-id="b87d1-148">Option</span><span class="sxs-lookup"><span data-stu-id="b87d1-148">Option</span></span> | <span data-ttu-id="b87d1-149">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b87d1-149">Description</span></span> |
| --- | --- |
| <span data-ttu-id="b87d1-150">Vor dem Rendern</span><span class="sxs-lookup"><span data-stu-id="b87d1-150">Before Render</span></span> | <span data-ttu-id="b87d1-151">Direkt vor dem Rendern.</span><span class="sxs-lookup"><span data-stu-id="b87d1-151">Just before rendering.</span></span> |
| <span data-ttu-id="b87d1-152">Aktualisieren</span><span class="sxs-lookup"><span data-stu-id="b87d1-152">Update</span></span> | <span data-ttu-id="b87d1-153">Während der Aktualisierungsphase des Frames.</span><span class="sxs-lookup"><span data-stu-id="b87d1-153">During the update phase of the frame.</span></span> |
| <span data-ttu-id="b87d1-154">Aktualisieren von und vor dem Rendern</span><span class="sxs-lookup"><span data-stu-id="b87d1-154">Update And Before Render</span></span> | <span data-ttu-id="b87d1-155">Während der Aktualisierungsphase und direkt vor dem Rendern.</span><span class="sxs-lookup"><span data-stu-id="b87d1-155">During the update phase and just before rendering.</span></span> |

<span data-ttu-id="b87d1-156">Der Standardwert für den Nachverfolgungstyp lautet **Update and Before Render**, um die niedrigste Nachverfolgungslatenz zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="b87d1-156">The default value for tracking type is **Update And Before Render**, to enable the lowest tracking latency.</span></span>

## <a name="see-also"></a><span data-ttu-id="b87d1-157">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b87d1-157">See also</span></span>

- [<span data-ttu-id="b87d1-158">Kamerasystemübersicht</span><span class="sxs-lookup"><span data-stu-id="b87d1-158">Camera System Overview</span></span>](camera-system-overview.md)
- [<span data-ttu-id="b87d1-159">Erstellen eines Kameraeinstellungsanbieters</span><span class="sxs-lookup"><span data-stu-id="b87d1-159">Creating a Camera Settings Provider</span></span>](create-settings-provider.md)
