---
title: Konfigurieren der Begrenzungsvisualisierung
description: Details zum Konfigurieren des Begrenzungssystems im MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Boundary System,
ms.openlocfilehash: 0f1a9edd9f9a31e7ba20f630406b299909a4864c
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121248"
---
# <a name="configuring-the-boundary-visualization"></a><span data-ttu-id="a53cf-104">Konfigurieren der Begrenzungsvisualisierung</span><span class="sxs-lookup"><span data-stu-id="a53cf-104">Configuring the boundary visualization</span></span>

<span data-ttu-id="a53cf-105">Das *Profil für die Begrenzungsvisualisierung* bietet Optionen zum Konfigurieren der visuellen Darstellungen und anderer verwandter Parameter für das Begrenzungssystem.</span><span class="sxs-lookup"><span data-stu-id="a53cf-105">The *Boundary Visualization Profile* provides options for configuring the visual aesthetics and other related parameters for the Boundary system.</span></span> <span data-ttu-id="a53cf-106">Begrenzungsvisualisierungen werden an Mixed Reality Playspace-Objekt in der Szene angefügt und mit dem Benutzer übertragen.</span><span class="sxs-lookup"><span data-stu-id="a53cf-106">Boundary visualizations are attached to the Mixed Reality Playspace object in the scene and teleport with the user.</span></span>

## <a name="general-settings"></a><span data-ttu-id="a53cf-107">Allgemeine Einstellungen</span><span class="sxs-lookup"><span data-stu-id="a53cf-107">General settings</span></span>

![Allgemeine Einstellungen für die Begrenzungsvisualisierung](../images/boundary/BoundaryVisualizationGeneralSettings.png)

### <a name="boundary-height"></a><span data-ttu-id="a53cf-109">Begrenzungshöhe</span><span class="sxs-lookup"><span data-stu-id="a53cf-109">Boundary height</span></span>

<span data-ttu-id="a53cf-110">Die Begrenzungshöhe gibt den Abstand über der Bodenebene an, an dem die Begrenzungsgrenze gerendert werden soll.</span><span class="sxs-lookup"><span data-stu-id="a53cf-110">The boundary height indicates the distance above the floor plane at which the boundary ceiling should be rendered.</span></span> <span data-ttu-id="a53cf-111">Der Standardwert ist 3 Meter.</span><span class="sxs-lookup"><span data-stu-id="a53cf-111">The default value is 3 meters.</span></span>

## <a name="floor-settings"></a><span data-ttu-id="a53cf-112">Einstellungen für den Boden</span><span class="sxs-lookup"><span data-stu-id="a53cf-112">Floor settings</span></span>

![Begrenzungsvisualisierung – Grundeinstellungen](../images/boundary/BoundaryVisualizationFloorSettings.png)

<span data-ttu-id="a53cf-114">**Anzeigen**</span><span class="sxs-lookup"><span data-stu-id="a53cf-114">**Show**</span></span>

<span data-ttu-id="a53cf-115">Gibt an, ob eine Bodenebene erstellt und der Szene hinzugefügt werden soll.</span><span class="sxs-lookup"><span data-stu-id="a53cf-115">Indicates whether or not a floor plane is to be created and added to the scene.</span></span> <span data-ttu-id="a53cf-116">Der Standardwert lautet „true“.</span><span class="sxs-lookup"><span data-stu-id="a53cf-116">The default value is true.</span></span>

<span data-ttu-id="a53cf-117">**Material**</span><span class="sxs-lookup"><span data-stu-id="a53cf-117">**Material**</span></span>

<span data-ttu-id="a53cf-118">Gibt das Material an, das beim Erstellen der Bodenebene verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="a53cf-118">Indicates the material that should be used when creating the floor plane.</span></span>

<span data-ttu-id="a53cf-119">**Skalieren**</span><span class="sxs-lookup"><span data-stu-id="a53cf-119">**Scale**</span></span>

<span data-ttu-id="a53cf-120">Gibt die Größe der zu erstellenden Bodenebene in Metern an.</span><span class="sxs-lookup"><span data-stu-id="a53cf-120">Indicates the size, in meters, of the floor plane to be created.</span></span> <span data-ttu-id="a53cf-121">Die Standardskala ist ein Quadrat mit 3 x 3 Meter.</span><span class="sxs-lookup"><span data-stu-id="a53cf-121">The default scale is a 3 meter x 3 meter square.</span></span>

<span data-ttu-id="a53cf-122">**Physikschicht**</span><span class="sxs-lookup"><span data-stu-id="a53cf-122">**Physics Layer**</span></span>

<span data-ttu-id="a53cf-123">Die Ebene, auf der die Bodenebene festgelegt werden soll.</span><span class="sxs-lookup"><span data-stu-id="a53cf-123">The layer on which the floor plane should be set.</span></span> <span data-ttu-id="a53cf-124">Der Standardwert ist die *Standardebene.*</span><span class="sxs-lookup"><span data-stu-id="a53cf-124">The default value is the *Default* layer.</span></span>

## <a name="play-area-settings"></a><span data-ttu-id="a53cf-125">Wiedergabebereichseinstellungen</span><span class="sxs-lookup"><span data-stu-id="a53cf-125">Play area settings</span></span>

![Wiedergabebereichseinstellungen für Die Begrenzungsvisualisierung](../images/boundary/BoundaryVisualizationPlayAreaSettings.png)

<span data-ttu-id="a53cf-127">**Anzeigen**</span><span class="sxs-lookup"><span data-stu-id="a53cf-127">**Show**</span></span>

<span data-ttu-id="a53cf-128">Gibt an, ob ein Wiedergabebereichrechteck erstellt und der Szene hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="a53cf-128">Indicates whether or not a play area rectangle is be created and added to the scene.</span></span> <span data-ttu-id="a53cf-129">Der Standardwert lautet „true“.</span><span class="sxs-lookup"><span data-stu-id="a53cf-129">The default value is true.</span></span>

<span data-ttu-id="a53cf-130">**Material**</span><span class="sxs-lookup"><span data-stu-id="a53cf-130">**Material**</span></span>

<span data-ttu-id="a53cf-131">Gibt das Material an, das beim Erstellen des Play Area-Objekts verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="a53cf-131">Indicates the material that should be used when creating the play area object.</span></span>

<span data-ttu-id="a53cf-132">**Physikschicht**</span><span class="sxs-lookup"><span data-stu-id="a53cf-132">**Physics Layer**</span></span>

<span data-ttu-id="a53cf-133">Die Ebene, auf der der Wiedergabebereich festgelegt werden soll.</span><span class="sxs-lookup"><span data-stu-id="a53cf-133">The layer on which the play area should be set.</span></span> <span data-ttu-id="a53cf-134">Der Standardwert ist die *Raycastebene ignorieren.*</span><span class="sxs-lookup"><span data-stu-id="a53cf-134">The default value is the *Ignore Raycast* layer.</span></span>

## <a name="tracked-area-settings"></a><span data-ttu-id="a53cf-135">Einstellungen für nachverfolgten Bereich</span><span class="sxs-lookup"><span data-stu-id="a53cf-135">Tracked area settings</span></span>

![Einstellungen für nachverfolgte Flächen der Begrenzungsvisualisierung](../images/boundary/BoundaryVisualizationTrackedAreaSettings.png)

<span data-ttu-id="a53cf-137">**Anzeigen**</span><span class="sxs-lookup"><span data-stu-id="a53cf-137">**Show**</span></span>

<span data-ttu-id="a53cf-138">Gibt an, ob die Kontur des nachverfolgten Bereichs erstellt und der Szene hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="a53cf-138">Indicates whether or not the outline of the tracked area is be created and added to the scene.</span></span> <span data-ttu-id="a53cf-139">Der Standardwert lautet „true“.</span><span class="sxs-lookup"><span data-stu-id="a53cf-139">The default value is true.</span></span>

<span data-ttu-id="a53cf-140">**Material**</span><span class="sxs-lookup"><span data-stu-id="a53cf-140">**Material**</span></span>

<span data-ttu-id="a53cf-141">Gibt das Material an, das beim Erstellen der nachverfolgten Bereichsgliederung verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="a53cf-141">Indicates the material that should be used when creating the tracked area outline.</span></span>

<span data-ttu-id="a53cf-142">**Physikschicht**</span><span class="sxs-lookup"><span data-stu-id="a53cf-142">**Physics Layer**</span></span>

<span data-ttu-id="a53cf-143">Die Ebene, auf der der nachverfolgte Bereich bestimmt werden soll.</span><span class="sxs-lookup"><span data-stu-id="a53cf-143">The layer on which the tracked area should be sets.</span></span> <span data-ttu-id="a53cf-144">Der Standardwert ist die *Raycastebene ignorieren.*</span><span class="sxs-lookup"><span data-stu-id="a53cf-144">The default value is the *Ignore Raycast* layer.</span></span>

## <a name="boundary-wall-settings"></a><span data-ttu-id="a53cf-145">Begrenzungswandeinstellungen</span><span class="sxs-lookup"><span data-stu-id="a53cf-145">Boundary wall settings</span></span>

![Begrenzungsvisualisierung– Begrenzungswandeinstellungen](../images/boundary/BoundaryVisualizationWallSettings.png)

<span data-ttu-id="a53cf-147">**Anzeigen**</span><span class="sxs-lookup"><span data-stu-id="a53cf-147">**Show**</span></span>

<span data-ttu-id="a53cf-148">Gibt an, ob Begrenzungswandebenen erstellt und der Szene hinzugefügt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="a53cf-148">Indicates whether or not boundary wall planes are to be created and added to the scene.</span></span> <span data-ttu-id="a53cf-149">Der Standardwert ist „FALSE“.</span><span class="sxs-lookup"><span data-stu-id="a53cf-149">The default value is false.</span></span>

<span data-ttu-id="a53cf-150">**Material**</span><span class="sxs-lookup"><span data-stu-id="a53cf-150">**Material**</span></span>

<span data-ttu-id="a53cf-151">Gibt das Material an, das beim Erstellen der Begrenzungswandebenen verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="a53cf-151">Indicates the material that should be used when creating the boundary wall planes.</span></span>

<span data-ttu-id="a53cf-152">**Physikschicht**</span><span class="sxs-lookup"><span data-stu-id="a53cf-152">**Physics Layer**</span></span>

<span data-ttu-id="a53cf-153">Die Ebene, auf der die Begrenzungswand festgelegt werden soll.</span><span class="sxs-lookup"><span data-stu-id="a53cf-153">The layer on which the boundary walls should be set.</span></span> <span data-ttu-id="a53cf-154">Der Standardwert ist die *Raycastebene ignorieren.*</span><span class="sxs-lookup"><span data-stu-id="a53cf-154">The default value is the *Ignore Raycast* layer.</span></span>

> [!NOTE]
> <span data-ttu-id="a53cf-155">Wenn Sie die Begrenzungswandkomponente auf eine andere physikalische Ebene als *Raycast* ignorieren festlegen, können Benutzer möglicherweise nicht mit Objekten innerhalb der Szene interagieren.</span><span class="sxs-lookup"><span data-stu-id="a53cf-155">Setting the boundary wall component to a physics layer other than *Ignore Raycast* may prevent users from interacting with objects within the scene.</span></span>

## <a name="boundary-ceiling-settings"></a><span data-ttu-id="a53cf-156">Einstellungen für die Begrenzungsobergrenze</span><span class="sxs-lookup"><span data-stu-id="a53cf-156">Boundary ceiling settings</span></span>

![Begrenzungsvisualisierung– Begrenzungsbegrenzungseinstellungen](../images/boundary/BoundaryVisualizationCeilingSettings.png)

<span data-ttu-id="a53cf-158">**Anzeigen**</span><span class="sxs-lookup"><span data-stu-id="a53cf-158">**Show**</span></span>

<span data-ttu-id="a53cf-159">Gibt an, ob eine Begrenzungsbegrenzungsebene erstellt und der Szene hinzugefügt werden soll.</span><span class="sxs-lookup"><span data-stu-id="a53cf-159">Indicates whether or not a boundary ceiling plane is to be created and added to the scene.</span></span> <span data-ttu-id="a53cf-160">Der Standardwert ist „FALSE“.</span><span class="sxs-lookup"><span data-stu-id="a53cf-160">The default value is false.</span></span>

<span data-ttu-id="a53cf-161">**Material**</span><span class="sxs-lookup"><span data-stu-id="a53cf-161">**Material**</span></span>

<span data-ttu-id="a53cf-162">Gibt das Material an, das beim Erstellen der Begrenzungsbegrenzungsebene verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="a53cf-162">Indicates the material that should be used when creating the boundary ceiling plane.</span></span>

<span data-ttu-id="a53cf-163">**Physikschicht**</span><span class="sxs-lookup"><span data-stu-id="a53cf-163">**Physics Layer**</span></span>

<span data-ttu-id="a53cf-164">Die Ebene, auf der die Begrenzungswand festgelegt werden soll.</span><span class="sxs-lookup"><span data-stu-id="a53cf-164">The layer on which the boundary walls should be set.</span></span> <span data-ttu-id="a53cf-165">Der Standardwert ist die *Raycastebene ignorieren.*</span><span class="sxs-lookup"><span data-stu-id="a53cf-165">The default value is the *Ignore Raycast* layer.</span></span>

> [!NOTE]
> <span data-ttu-id="a53cf-166">Das Festlegen der Begrenzungsbegrenzungskomponente auf eine andere physikalische Ebene als *Raycast ignorieren* kann verhindern, dass Benutzer mit Objekten innerhalb der Szene interagieren.</span><span class="sxs-lookup"><span data-stu-id="a53cf-166">Setting the boundary ceiling component to a physics layer other than *Ignore Raycast* may prevent users from interacting with objects within the scene.</span></span>

## <a name="see-also"></a><span data-ttu-id="a53cf-167">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="a53cf-167">See also</span></span>

- [<span data-ttu-id="a53cf-168">Dokumentation zur Begrenzungs-API</span><span class="sxs-lookup"><span data-stu-id="a53cf-168">Boundary API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [<span data-ttu-id="a53cf-169">Begrenzungs- system</span><span class="sxs-lookup"><span data-stu-id="a53cf-169">Boundary System</span></span>](boundary-system-getting-started.md)
