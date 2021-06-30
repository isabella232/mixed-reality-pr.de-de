---
title: Elastisches System
description: Dokumentation zur Simulation elastischer Datenbanken im MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, ElasticsSystem,
ms.openlocfilehash: 1f90864ee6d3b6756b863de600ade8423a44cacc
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121238"
---
# <a name="elastic-system-experimental"></a><span data-ttu-id="cdc5b-104">Elastisches System (experimentell)</span><span class="sxs-lookup"><span data-stu-id="cdc5b-104">Elastic system (experimental)</span></span>

![Elastisches System](../images/elastics/Elastics_Main1.gif)

<span data-ttu-id="cdc5b-106">MRTK verfügt über ein elastisches Simulationssystem, das eine Vielzahl von erweiterbaren und flexiblen Unterklassen enthält und Bindungen für vierdimensionale Quaternionsmaße, dreidimensionale Volumenmaße und einfache lineare Springsysteme bietet.</span><span class="sxs-lookup"><span data-stu-id="cdc5b-106">MRTK comes with an elastic simulation system that includes a wide variety of extensible and flexible subclasses, offering bindings for 4-dimensional quaternion springs, 3-dimensional volume springs and simple linear spring systems.</span></span>

<span data-ttu-id="cdc5b-107">Derzeit können die folgenden MRTK-Komponenten, die den [Elastics Manager](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) unterstützen, die Funktionalität für elastische Datenbanken nutzen:</span><span class="sxs-lookup"><span data-stu-id="cdc5b-107">Currently the following MRTK components supporting the [elastics manager](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) can leverage elastics functionality:</span></span>

- [<span data-ttu-id="cdc5b-108">Begrenzungssteuerelement</span><span class="sxs-lookup"><span data-stu-id="cdc5b-108">Bounds control</span></span>](../ux-building-blocks/bounds-control.md)
- [<span data-ttu-id="cdc5b-109">Objektmanipulator</span><span class="sxs-lookup"><span data-stu-id="cdc5b-109">Object manipulator</span></span>](../ux-building-blocks/object-manipulator.md)

## <a name="elastics-manager"></a><span data-ttu-id="cdc5b-110">Manager für elastische Datenbanken</span><span class="sxs-lookup"><span data-stu-id="cdc5b-110">Elastics manager</span></span>

![Elastic System2](../images/elastics/Elastics_Main.gif)

<span data-ttu-id="cdc5b-112">Der Elastics Manager verarbeitet übergebene Transformationen und leitet sie in das System für elastische Datenbanken ein.</span><span class="sxs-lookup"><span data-stu-id="cdc5b-112">The elastics manager processes passed transforms and feeds them into the elastics system.</span></span>

<span data-ttu-id="cdc5b-113">Das Aktivieren von elastischen Datenbanken für benutzerdefinierte Komponenten kann mit zwei Schritten erreicht werden:</span><span class="sxs-lookup"><span data-stu-id="cdc5b-113">Enabling elastics for custom components can be achieved by two steps:</span></span>

1. <span data-ttu-id="cdc5b-114">Durch Aufrufen der Initialize-Methode beim Manipulationsstart wird das System mit der aktuellen Hosttransformation aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="cdc5b-114">Calling the Initialize method on manipulation start, updating the system with the current host transform.</span></span>
1. <span data-ttu-id="cdc5b-115">Abfragen von ApplyHostTransform, wenn eine Berechnung für elastische Datenbanken für die aktualisierte Zieltransformation durchgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="cdc5b-115">Querying ApplyHostTransform whenever a elastics calculation should be performed on the updated target transform.</span></span>

<span data-ttu-id="cdc5b-116">Beachten Sie, dass elastische Datenbanken weiterhin simulieren, sobald die Bearbeitung beendet ist (über die Updateschleife des Managers für elastische Datenbanken).</span><span class="sxs-lookup"><span data-stu-id="cdc5b-116">Note that elastics will continue simulating once manipulation ends (through the elastics manager update loop).</span></span> <span data-ttu-id="cdc5b-117">Um das Verhalten zu blockieren, kann [EnableElasticsUpdate](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager.EnableElasticsUpdate) für elastische Datenbanken automatisch auf FALSE festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="cdc5b-117">To block the behavior, elastics auto update [EnableElasticsUpdate](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager.EnableElasticsUpdate) can be set to false.</span></span>

<span data-ttu-id="cdc5b-118">Standardmäßig sind für die Elastics Manager-Komponente beim Hinzufügen zu einem Spielobjekt keine elastischen Datenbanken für jeden Transformationstyp aktiviert.</span><span class="sxs-lookup"><span data-stu-id="cdc5b-118">By default, the elastics manager component, when added to a game object, won't have elastics enabled for any transforms type.</span></span>
<span data-ttu-id="cdc5b-119">Das Feld `Manipulation types using elastic feedback` muss für bestimmte Transformationstypen aktiviert werden, um elastische Konfigurationen und Erweiterungen für den ausgewählten Typ zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="cdc5b-119">The field `Manipulation types using elastic feedback` needs to be enabled for specific transform types to create elastics configuration and extents for the selected type.</span></span>

### <a name="elastics-configurations"></a><span data-ttu-id="cdc5b-120">Konfigurationen für elastische Datenbanken</span><span class="sxs-lookup"><span data-stu-id="cdc5b-120">Elastics configurations</span></span>

<span data-ttu-id="cdc5b-121">Ähnlich wie [bei Begrenzungssteuerelementkonfigurationen](../ux-building-blocks/bounds-control.md#configuration-objects)verfügt der Elastische Manager über eine Reihe von Konfigurationsobjekten, die als skriptfähige Objekte gespeichert und von verschiedenen Instanzen oder Prefabs gemeinsam genutzt werden können.</span><span class="sxs-lookup"><span data-stu-id="cdc5b-121">Similar to [bounds control configurations](../ux-building-blocks/bounds-control.md#configuration-objects), elastic manager comes with a set of configuration objects that can be stored as scriptable objects and shared between different instances or prefabs.</span></span> <span data-ttu-id="cdc5b-122">Konfigurationen können als einzelne skriptfähige Medienobjektdateien oder als geschachtelte skriptfähige Objekte innerhalb von Prefabs freigegeben und verknüpft werden.</span><span class="sxs-lookup"><span data-stu-id="cdc5b-122">Configurations can be shared and linked either as individual scriptable asset files or nested scriptable assets inside of prefabs.</span></span> <span data-ttu-id="cdc5b-123">Weitere Konfigurationen können auch direkt auf der Instanz definiert werden, ohne eine Verknüpfung mit einem externen oder geschachtelten Skriptobjekt zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="cdc5b-123">Further configurations can also be defined directly on the instance without linking to an external or nested scriptable asset.</span></span>

<span data-ttu-id="cdc5b-124">Der Inspektor des Managers für elastische Datenbanken gibt an, ob eine Konfiguration als Teil der aktuellen Instanz freigegeben oder inline ist, indem eine Meldung im Eigenschafteninspektor angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="cdc5b-124">The elastics manager inspector will indicate whether a configuration is shared or inlined as part of the current instance by showing a message in the property inspector.</span></span> <span data-ttu-id="cdc5b-125">Darüber hinaus können freigegebene Instanzen nicht direkt im Eigenschaftenfenster des Managers für elastische Datenbanken selbst bearbeitet werden. Stattdessen muss die Ressource, mit der sie verknüpft wird, direkt geändert werden, um versehentliche Änderungen an freigegebenen Konfigurationen zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="cdc5b-125">In addition, shared instances won't be editable directly in the elastics manager property window itself, but instead the asset it's linking to has to be directly modfied to avoid any accidental changes on shared configurations.</span></span>

<span data-ttu-id="cdc5b-126">Der Manager für elastische Datenbanken bietet Konfigurationsoptionen für die folgenden Transformationstypen, die jeweils durch ein [elastisches Konfigurationsobjekt](#elastic-configuration-object)dargestellt werden:</span><span class="sxs-lookup"><span data-stu-id="cdc5b-126">Elastics manager offers configuration objects options for the following transform types, each of them represented by a [elastic configuration object](#elastic-configuration-object):</span></span>

- <span data-ttu-id="cdc5b-127">Elastische Übersetzung</span><span class="sxs-lookup"><span data-stu-id="cdc5b-127">Translation Elastic</span></span>
- <span data-ttu-id="cdc5b-128">Elastische Rotation</span><span class="sxs-lookup"><span data-stu-id="cdc5b-128">Rotation Elastic</span></span>
- <span data-ttu-id="cdc5b-129">Skalieren der elastischen Datenbanken</span><span class="sxs-lookup"><span data-stu-id="cdc5b-129">Scale Elastic</span></span>

#### <a name="elastic-configuration-object"></a><span data-ttu-id="cdc5b-130">Elastisches Konfigurationsobjekt</span><span class="sxs-lookup"><span data-stu-id="cdc5b-130">Elastic configuration object</span></span>

<span data-ttu-id="cdc5b-131">Eine Konfiguration für elastische Datenbanken definiert Eigenschaften für ein gestuftes differenzielles System mit einem elastischen Oszillationsor.</span><span class="sxs-lookup"><span data-stu-id="cdc5b-131">A elastics configuration defines properties for a damped harmonic oscillator differential system.</span></span>
<span data-ttu-id="cdc5b-132">Die folgenden Eigenschaften können angepasst werden, verfügen aber bereits über einen Satz von Standardwerten im MRTK:</span><span class="sxs-lookup"><span data-stu-id="cdc5b-132">The following properties can be adjusted but already come with a set of defaults in MRTK:</span></span>

- <span data-ttu-id="cdc5b-133">**Mass:** Die Menge des simulierten Oszillationselements.</span><span class="sxs-lookup"><span data-stu-id="cdc5b-133">**Mass**: mass of the simulated oscillator element.</span></span>
- <span data-ttu-id="cdc5b-134">**HandK:** Handspringkonstante.</span><span class="sxs-lookup"><span data-stu-id="cdc5b-134">**HandK**: hand spring constant.</span></span>
- <span data-ttu-id="cdc5b-135">**EndK:** Endendeende-Springkonstante.</span><span class="sxs-lookup"><span data-stu-id="cdc5b-135">**EndK**: end cap spring constant.</span></span>
- <span data-ttu-id="cdc5b-136">**SnapK:** Andockpunkt-Springkonstante.</span><span class="sxs-lookup"><span data-stu-id="cdc5b-136">**SnapK**: snap point spring constant.</span></span>
- <span data-ttu-id="cdc5b-137">**Ziehen Sie**: Zieh-/Ziehfaktor, proportional zur Geschwindigkeit.</span><span class="sxs-lookup"><span data-stu-id="cdc5b-137">**Drag**: drag/damper factor, proportional to velocity.</span></span>

### <a name="elastics-extents"></a><span data-ttu-id="cdc5b-138">Bänder für elastische Datenbanken</span><span class="sxs-lookup"><span data-stu-id="cdc5b-138">Elastics extents</span></span>

<span data-ttu-id="cdc5b-139">Die Einstellungen für elastische Erweiterungen variieren je nach Art der Bearbeitung.</span><span class="sxs-lookup"><span data-stu-id="cdc5b-139">Elastics extents settings vary depending on the type of manipulation.</span></span> <span data-ttu-id="cdc5b-140">Übersetzung und Skalierung werden durch [elastische Volume-Skalen](#volume-elastic-extent) dargestellt, und die Drehung wird durch einen [elastischen Quaternion-Skalar dargestellt.](#quaternion-elastic-extent)</span><span class="sxs-lookup"><span data-stu-id="cdc5b-140">Translation and scale are represented by [volume elastic extents](#volume-elastic-extent) and rotation is represented by a [quaternion elastic extent](#quaternion-elastic-extent).</span></span>

#### <a name="volume-elastic-extent"></a><span data-ttu-id="cdc5b-141">Elastischer Volume-Erweiterungsumfang</span><span class="sxs-lookup"><span data-stu-id="cdc5b-141">Volume elastic extent</span></span>

<span data-ttu-id="cdc5b-142">Volumendehnungen definieren einen dreidimensionalen Raum, in dem sich der 160-Grad-Oszillatoren frei bewegen kann.</span><span class="sxs-lookup"><span data-stu-id="cdc5b-142">Volume extents define a three dimensional space in which the damped harmonic oscillator is free to move.</span></span>

![Elastische Volumedehnungsgrenzen](../images/elastics/Elastics_Volume_Bounds.gif)

- <span data-ttu-id="cdc5b-144">**StretchBounds:** Stellt die unteren Grenzen des elastischen Raums dar.</span><span class="sxs-lookup"><span data-stu-id="cdc5b-144">**StretchBounds**: represents the lower bounds of the elastic space.</span></span>
- <span data-ttu-id="cdc5b-145">**UseBounds:** Gibt an, ob die Stretchinggrenzen vom System berücksichtigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="cdc5b-145">**UseBounds**: whether the stretch bounds should be respected by the system.</span></span> <span data-ttu-id="cdc5b-146">True gibt an, dass die Endkraft angewendet wird, wenn sich die aktuelle Iteration der Zielposition außerhalb der Streckungsgrenzen befindet.</span><span class="sxs-lookup"><span data-stu-id="cdc5b-146">If true, when the current iteration of the target position is outside the stretch bounds, the end force will be applied.</span></span>
- <span data-ttu-id="cdc5b-147">**SnapPoints:** Punkte innerhalb des Leerzeichens, an dem das System ausgerichtet wird.</span><span class="sxs-lookup"><span data-stu-id="cdc5b-147">**SnapPoints**: points inside the space to which the system will snap.</span></span>
- <span data-ttu-id="cdc5b-148">**RepeatSnapPoints:** wiederholt die Ausrichtungspunkte auf unendlich.</span><span class="sxs-lookup"><span data-stu-id="cdc5b-148">**RepeatSnapPoints**: repeats the snap points to infinity.</span></span> <span data-ttu-id="cdc5b-149">Vorhandene Ausrichtungspunkte dienen als Modulo, wobei die tatsächlichen Ausrichtungspunkte den nächsten ganzzahligen Vielfachen jedes Ausrichtungspunkts zugeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="cdc5b-149">Existing snap points will serve as a modulo where the actual snap points are mapped to the closest integer multiples of every snap point.</span></span>
- <span data-ttu-id="cdc5b-150">**SnapRadius:** Abstand, an dem Andockpunkte beginnen, die Feder zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="cdc5b-150">**SnapRadius**: distance at which snap points begin forcing the spring.</span></span>

![Snap Grid für elastische Volumes](../images/elastics/Elastics_Volume_Snap.gif)

#### <a name="quaternion-elastic-extent"></a><span data-ttu-id="cdc5b-152">Elastischer Quaternion-Extent</span><span class="sxs-lookup"><span data-stu-id="cdc5b-152">Quaternion elastic extent</span></span>

<span data-ttu-id="cdc5b-153">Quaternion-Erweiterungen definieren einen vierdimensionalen Drehungsbereich, in dem der 100-Grad-Oszillatoren frei gedreht werden kann.</span><span class="sxs-lookup"><span data-stu-id="cdc5b-153">Quaternion extents define a four dimensional rotation space in which the damped harmonic oscillator is free to rotate.</span></span>

![Beispiel für elastische Rotation](../images/elastics/Elastics_Rotation.gif)

- <span data-ttu-id="cdc5b-155">**SnapPoints:** Eulerwinkel, an denen das System ausgerichtet wird.</span><span class="sxs-lookup"><span data-stu-id="cdc5b-155">**SnapPoints**: euler angles to which the system will snap.</span></span>
- <span data-ttu-id="cdc5b-156">**RepeatSnapPoints:** wiederholt die Ausrichtungspunkte.</span><span class="sxs-lookup"><span data-stu-id="cdc5b-156">**RepeatSnapPoints**: repeats the snap points.</span></span> <span data-ttu-id="cdc5b-157">Vorhandene Ausrichtungspunkte dienen als Modulo, wobei die tatsächlichen Ausrichtungspunkte den nächsten ganzzahligen Vielfachen jedes Ausrichtungspunkts zugeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="cdc5b-157">Existing snap points will serve as a modulo where the actual snap points are mapped to the closest integer multiples of every snap point.</span></span>
- <span data-ttu-id="cdc5b-158">**SnapRadius:** Bogenwinkel, an dem Andockpunkte beginnen, die Feder in Eulergraden zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="cdc5b-158">**SnapRadius**: arc-angle at which snap points begin forcing the spring in euler degrees.</span></span>

## <a name="elastics-example-scene"></a><span data-ttu-id="cdc5b-159">Beispielszene für elastische Datenbanken</span><span class="sxs-lookup"><span data-stu-id="cdc5b-159">Elastics example scene</span></span>

<span data-ttu-id="cdc5b-160">Beispiele für Elastische Konfigurationen finden Sie in der `ElasticSystemExample` Szene.</span><span class="sxs-lookup"><span data-stu-id="cdc5b-160">You can find examples of elastics configurations in the `ElasticSystemExample` scene.</span></span>

![Beispielszene für elastische Datenbanken](../images/elastics/Elastics_Example_Scene.png)
