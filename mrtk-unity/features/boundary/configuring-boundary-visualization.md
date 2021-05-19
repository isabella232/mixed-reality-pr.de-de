---
title: Konfigurieren der Begrenzungsvisualisierung
description: Details zum Konfigurieren des Begrenzungssystems im MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Boundary System,
ms.openlocfilehash: 36717493107b129a7200dd3f912bcbdc3337b9a1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144490"
---
# <a name="configuring-the-boundary-visualization"></a><span data-ttu-id="fbc59-104">Konfigurieren der Begrenzungsvisualisierung</span><span class="sxs-lookup"><span data-stu-id="fbc59-104">Configuring the boundary visualization</span></span>

<span data-ttu-id="fbc59-105">Das *Profil für die Begrenzungsvisualisierung* bietet Optionen zum Konfigurieren der visuellen Darstellungen und anderer verwandter Parameter für das Begrenzungssystem.</span><span class="sxs-lookup"><span data-stu-id="fbc59-105">The *Boundary Visualization Profile* provides options for configuring the visual aesthetics and other related parameters for the Boundary system.</span></span> <span data-ttu-id="fbc59-106">Begrenzungsvisualisierungen werden an Mixed Reality Playspace-Objekt in der Szene angefügt und mit dem Benutzer übertragen.</span><span class="sxs-lookup"><span data-stu-id="fbc59-106">Boundary visualizations are attached to the Mixed Reality Playspace object in the scene and teleport with the user.</span></span>

## <a name="general-settings"></a><span data-ttu-id="fbc59-107">Allgemeine Einstellungen</span><span class="sxs-lookup"><span data-stu-id="fbc59-107">General settings</span></span>

![Allgemeine Einstellungen für die Begrenzungsvisualisierung](../images/boundary/BoundaryVisualizationGeneralSettings.png)

### <a name="boundary-height"></a><span data-ttu-id="fbc59-109">Begrenzungshöhe</span><span class="sxs-lookup"><span data-stu-id="fbc59-109">Boundary height</span></span>

<span data-ttu-id="fbc59-110">Die Begrenzungshöhe gibt den Abstand über der Bodenebene an, an dem die Begrenzungsgrenze gerendert werden soll.</span><span class="sxs-lookup"><span data-stu-id="fbc59-110">The boundary height indicates the distance above the floor plane at which the boundary ceiling should be rendered.</span></span> <span data-ttu-id="fbc59-111">Der Standardwert ist 3 Meter.</span><span class="sxs-lookup"><span data-stu-id="fbc59-111">The default value is 3 meters.</span></span>

## <a name="floor-settings"></a><span data-ttu-id="fbc59-112">Einstellungen für den Boden</span><span class="sxs-lookup"><span data-stu-id="fbc59-112">Floor settings</span></span>

![Begrenzungsvisualisierung – Grundeinstellungen](../images/boundary/BoundaryVisualizationFloorSettings.png)

<span data-ttu-id="fbc59-114">**Anzeigen**</span><span class="sxs-lookup"><span data-stu-id="fbc59-114">**Show**</span></span>

<span data-ttu-id="fbc59-115">Gibt an, ob eine Bodenebene erstellt und der Szene hinzugefügt werden soll.</span><span class="sxs-lookup"><span data-stu-id="fbc59-115">Indicates whether or not a floor plane is to be created and added to the scene.</span></span> <span data-ttu-id="fbc59-116">Der Standardwert lautet „true“.</span><span class="sxs-lookup"><span data-stu-id="fbc59-116">The default value is true.</span></span>

<span data-ttu-id="fbc59-117">**Material**</span><span class="sxs-lookup"><span data-stu-id="fbc59-117">**Material**</span></span>

<span data-ttu-id="fbc59-118">Gibt das Material an, das beim Erstellen der Bodenebene verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="fbc59-118">Indicates the material that should be used when creating the floor plane.</span></span>

<span data-ttu-id="fbc59-119">**Skalieren**</span><span class="sxs-lookup"><span data-stu-id="fbc59-119">**Scale**</span></span>

<span data-ttu-id="fbc59-120">Gibt die Größe der zu erstellenden Bodenebene in Metern an.</span><span class="sxs-lookup"><span data-stu-id="fbc59-120">Indicates the size, in meters, of the floor plane to be created.</span></span> <span data-ttu-id="fbc59-121">Die Standardskala ist ein Quadrat mit 3 x 3 Meter.</span><span class="sxs-lookup"><span data-stu-id="fbc59-121">The default scale is a 3 meter x 3 meter square.</span></span>

<span data-ttu-id="fbc59-122">**Physikschicht**</span><span class="sxs-lookup"><span data-stu-id="fbc59-122">**Physics Layer**</span></span>

<span data-ttu-id="fbc59-123">Die Ebene, auf der die Bodenebene festgelegt werden soll.</span><span class="sxs-lookup"><span data-stu-id="fbc59-123">The layer on which the floor plane should be set.</span></span> <span data-ttu-id="fbc59-124">Der Standardwert ist die *Standardebene.*</span><span class="sxs-lookup"><span data-stu-id="fbc59-124">The default value is the *Default* layer.</span></span>

## <a name="play-area-settings"></a><span data-ttu-id="fbc59-125">Wiedergabebereichseinstellungen</span><span class="sxs-lookup"><span data-stu-id="fbc59-125">Play area settings</span></span>

![Wiedergabebereichseinstellungen für Die Begrenzungsvisualisierung](../images/boundary/BoundaryVisualizationPlayAreaSettings.png)

<span data-ttu-id="fbc59-127">**Anzeigen**</span><span class="sxs-lookup"><span data-stu-id="fbc59-127">**Show**</span></span>

<span data-ttu-id="fbc59-128">Gibt an, ob ein Rechteck für den Wiedergabebereich erstellt und der Szene hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="fbc59-128">Indicates whether or not a play area rectangle is be created and added to the scene.</span></span> <span data-ttu-id="fbc59-129">Der Standardwert lautet „true“.</span><span class="sxs-lookup"><span data-stu-id="fbc59-129">The default value is true.</span></span>

<span data-ttu-id="fbc59-130">**Material**</span><span class="sxs-lookup"><span data-stu-id="fbc59-130">**Material**</span></span>

<span data-ttu-id="fbc59-131">Gibt das Material an, das beim Erstellen des Wiedergabebereichsobjekts verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="fbc59-131">Indicates the material that should be used when creating the play area object.</span></span>

<span data-ttu-id="fbc59-132">**Physikalische Schicht**</span><span class="sxs-lookup"><span data-stu-id="fbc59-132">**Physics Layer**</span></span>

<span data-ttu-id="fbc59-133">Die Ebene, auf der der Wiedergabebereich festgelegt werden soll.</span><span class="sxs-lookup"><span data-stu-id="fbc59-133">The layer on which the play area should be set.</span></span> <span data-ttu-id="fbc59-134">Der Standardwert ist die *Ignore Raycast-Schicht.*</span><span class="sxs-lookup"><span data-stu-id="fbc59-134">The default value is the *Ignore Raycast* layer.</span></span>

## <a name="tracked-area-settings"></a><span data-ttu-id="fbc59-135">Einstellungen für nachverfolgte Bereiche</span><span class="sxs-lookup"><span data-stu-id="fbc59-135">Tracked area settings</span></span>

![Einstellungen für nachverfolgte Bereiche der Begrenzungsvisualisierung](../images/boundary/BoundaryVisualizationTrackedAreaSettings.png)

<span data-ttu-id="fbc59-137">**Anzeigen**</span><span class="sxs-lookup"><span data-stu-id="fbc59-137">**Show**</span></span>

<span data-ttu-id="fbc59-138">Gibt an, ob der Umriss des nachverfolgten Bereichs erstellt und der Szene hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="fbc59-138">Indicates whether or not the outline of the tracked area is be created and added to the scene.</span></span> <span data-ttu-id="fbc59-139">Der Standardwert lautet „true“.</span><span class="sxs-lookup"><span data-stu-id="fbc59-139">The default value is true.</span></span>

<span data-ttu-id="fbc59-140">**Material**</span><span class="sxs-lookup"><span data-stu-id="fbc59-140">**Material**</span></span>

<span data-ttu-id="fbc59-141">Gibt das Material an, das beim Erstellen der nachverfolgten Bereichsgliederung verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="fbc59-141">Indicates the material that should be used when creating the tracked area outline.</span></span>

<span data-ttu-id="fbc59-142">**Physikalische Schicht**</span><span class="sxs-lookup"><span data-stu-id="fbc59-142">**Physics Layer**</span></span>

<span data-ttu-id="fbc59-143">Die Ebene, auf der der nachverfolgte Bereich festgelegt werden soll.</span><span class="sxs-lookup"><span data-stu-id="fbc59-143">The layer on which the tracked area should be sets.</span></span> <span data-ttu-id="fbc59-144">Der Standardwert ist die *Ignore Raycast-Schicht.*</span><span class="sxs-lookup"><span data-stu-id="fbc59-144">The default value is the *Ignore Raycast* layer.</span></span>

## <a name="boundary-wall-settings"></a><span data-ttu-id="fbc59-145">Begrenzungswandeinstellungen</span><span class="sxs-lookup"><span data-stu-id="fbc59-145">Boundary wall settings</span></span>

![Begrenzungsvisualisierung – Begrenzungswandeinstellungen](../images/boundary/BoundaryVisualizationWallSettings.png)

<span data-ttu-id="fbc59-147">**Anzeigen**</span><span class="sxs-lookup"><span data-stu-id="fbc59-147">**Show**</span></span>

<span data-ttu-id="fbc59-148">Gibt an, ob Begrenzungsebenen erstellt und der Szene hinzugefügt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="fbc59-148">Indicates whether or not boundary wall planes are to be created and added to the scene.</span></span> <span data-ttu-id="fbc59-149">Der Standardwert ist „FALSE“.</span><span class="sxs-lookup"><span data-stu-id="fbc59-149">The default value is false.</span></span>

<span data-ttu-id="fbc59-150">**Material**</span><span class="sxs-lookup"><span data-stu-id="fbc59-150">**Material**</span></span>

<span data-ttu-id="fbc59-151">Gibt das Material an, das beim Erstellen der Begrenzungswandebenen verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="fbc59-151">Indicates the material that should be used when creating the boundary wall planes.</span></span>

<span data-ttu-id="fbc59-152">**Physikalische Schicht**</span><span class="sxs-lookup"><span data-stu-id="fbc59-152">**Physics Layer**</span></span>

<span data-ttu-id="fbc59-153">Die Schicht, auf der die Begrenzungswand festgelegt werden soll.</span><span class="sxs-lookup"><span data-stu-id="fbc59-153">The layer on which the boundary walls should be set.</span></span> <span data-ttu-id="fbc59-154">Der Standardwert ist die *Ignore Raycast-Schicht.*</span><span class="sxs-lookup"><span data-stu-id="fbc59-154">The default value is the *Ignore Raycast* layer.</span></span>

> [!NOTE]
> <span data-ttu-id="fbc59-155">Das Festlegen der Begrenzungswandkomponente auf eine andere Physikalische Schicht als *Raycast ignorieren* kann Benutzer daran hindern, mit Objekten innerhalb der Szene zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="fbc59-155">Setting the boundary wall component to a physics layer other than *Ignore Raycast* may prevent users from interacting with objects within the scene.</span></span>

## <a name="boundary-ceiling-settings"></a><span data-ttu-id="fbc59-156">Einstellungen für die Begrenzungsobergrenze</span><span class="sxs-lookup"><span data-stu-id="fbc59-156">Boundary ceiling settings</span></span>

![Begrenzungsvisualisierung– Begrenzungsbegrenzungseinstellungen](../images/boundary/BoundaryVisualizationCeilingSettings.png)

<span data-ttu-id="fbc59-158">**Anzeigen**</span><span class="sxs-lookup"><span data-stu-id="fbc59-158">**Show**</span></span>

<span data-ttu-id="fbc59-159">Gibt an, ob eine Begrenzungsbegrenzungsebene erstellt und der Szene hinzugefügt werden soll.</span><span class="sxs-lookup"><span data-stu-id="fbc59-159">Indicates whether or not a boundary ceiling plane is to be created and added to the scene.</span></span> <span data-ttu-id="fbc59-160">Der Standardwert ist „FALSE“.</span><span class="sxs-lookup"><span data-stu-id="fbc59-160">The default value is false.</span></span>

<span data-ttu-id="fbc59-161">**Material**</span><span class="sxs-lookup"><span data-stu-id="fbc59-161">**Material**</span></span>

<span data-ttu-id="fbc59-162">Gibt das Material an, das beim Erstellen der Begrenzungsbegrenzungsebene verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="fbc59-162">Indicates the material that should be used when creating the boundary ceiling plane.</span></span>

<span data-ttu-id="fbc59-163">**Physikschicht**</span><span class="sxs-lookup"><span data-stu-id="fbc59-163">**Physics Layer**</span></span>

<span data-ttu-id="fbc59-164">Die Ebene, auf der die Begrenzungswand festgelegt werden soll.</span><span class="sxs-lookup"><span data-stu-id="fbc59-164">The layer on which the boundary walls should be set.</span></span> <span data-ttu-id="fbc59-165">Der Standardwert ist die *Raycastebene ignorieren.*</span><span class="sxs-lookup"><span data-stu-id="fbc59-165">The default value is the *Ignore Raycast* layer.</span></span>

> [!NOTE]
> <span data-ttu-id="fbc59-166">Das Festlegen der Begrenzungsbegrenzungskomponente auf eine andere physikalische Ebene als *Raycast ignorieren* kann verhindern, dass Benutzer mit Objekten innerhalb der Szene interagieren.</span><span class="sxs-lookup"><span data-stu-id="fbc59-166">Setting the boundary ceiling component to a physics layer other than *Ignore Raycast* may prevent users from interacting with objects within the scene.</span></span>

## <a name="see-also"></a><span data-ttu-id="fbc59-167">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="fbc59-167">See also</span></span>

- [<span data-ttu-id="fbc59-168">Dokumentation zur Begrenzungs-API</span><span class="sxs-lookup"><span data-stu-id="fbc59-168">Boundary API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [<span data-ttu-id="fbc59-169">Begrenzungs- system</span><span class="sxs-lookup"><span data-stu-id="fbc59-169">Boundary System</span></span>](boundary-system-getting-started.md)
