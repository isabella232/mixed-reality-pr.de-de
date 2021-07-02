---
title: Elastisches System
description: Dokumentation zur Simulation von elastischen Datenbanken in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, Mixed Reality, Development, MRTK, ElasticsSystem,
ms.openlocfilehash: 44110cac9ac5aadb7b5e680f18a5e93f43efce12
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177792"
---
# <a name="elastic-system"></a><span data-ttu-id="f1549-104">Elastisches System</span><span class="sxs-lookup"><span data-stu-id="f1549-104">Elastic system</span></span>

![Elastisches System](../images/elastics/Elastics_Main1.gif)

<span data-ttu-id="f1549-106">MRTK verfügt über ein elastisches Simulationssystem, das eine Vielzahl von erweiterbaren und flexiblen Unterklassen umfasst und Bindungen für 4-dimensionale Quaternionsveralbungen, 3-dimensionale Volume-Bänder und einfache lineare Federsysteme bietet.</span><span class="sxs-lookup"><span data-stu-id="f1549-106">MRTK comes with an elastic simulation system that includes a wide variety of extensible and flexible subclasses, offering bindings for 4-dimensional quaternion springs, 3-dimensional volume springs and simple linear spring systems.</span></span>

<span data-ttu-id="f1549-107">Derzeit können die folgenden MRTK-Komponenten, die [den Elastics Manager unterstützen,](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) elastische Funktionen nutzen:</span><span class="sxs-lookup"><span data-stu-id="f1549-107">Currently the following MRTK components supporting the [elastics manager](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) can leverage elastics functionality:</span></span>

- [<span data-ttu-id="f1549-108">Steuerelement "Begrenzungen"</span><span class="sxs-lookup"><span data-stu-id="f1549-108">Bounds control</span></span>](../ux-building-blocks/bounds-control.md)
- [<span data-ttu-id="f1549-109">Objektmanipulator</span><span class="sxs-lookup"><span data-stu-id="f1549-109">Object manipulator</span></span>](../ux-building-blocks/object-manipulator.md)

## <a name="elastics-manager"></a><span data-ttu-id="f1549-110">Manager für elastische Datenbanken</span><span class="sxs-lookup"><span data-stu-id="f1549-110">Elastics manager</span></span>

![Elastic System2](../images/elastics/Elastics_Main.gif)

<span data-ttu-id="f1549-112">Der Elastics Manager verarbeitet übergebene Transformationen und gibt sie in das Elastiksystem ein.</span><span class="sxs-lookup"><span data-stu-id="f1549-112">The elastics manager processes passed transforms and feeds them into the elastics system.</span></span>

<span data-ttu-id="f1549-113">Die Aktivierung von elastischen Komponenten für benutzerdefinierte Komponenten kann mit zwei Schritten erreicht werden:</span><span class="sxs-lookup"><span data-stu-id="f1549-113">Enabling elastics for custom components can be achieved by two steps:</span></span>

1. <span data-ttu-id="f1549-114">Durch Aufrufen der Initialize-Methode beim Start der Bearbeitung wird das System mit der aktuellen Hosttransformation aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="f1549-114">Calling the Initialize method on manipulation start, updating the system with the current host transform.</span></span>
1. <span data-ttu-id="f1549-115">Abfragen von ApplyHostTransform, wenn eine elastische Berechnung für die aktualisierte Zieltransformation durchgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="f1549-115">Querying ApplyHostTransform whenever a elastics calculation should be performed on the updated target transform.</span></span>

<span data-ttu-id="f1549-116">Beachten Sie, dass elastische Datenbanken weiterhin simulieren, sobald die Bearbeitung beendet ist (über die Updateschleife des Elastics-Managers).</span><span class="sxs-lookup"><span data-stu-id="f1549-116">Note that elastics will continue simulating once manipulation ends (through the elastics manager update loop).</span></span> <span data-ttu-id="f1549-117">Um das Verhalten zu blockieren, kann [enableElasticsUpdate für elastische](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager.EnableElasticsUpdate) Datenbanken auf FALSE festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="f1549-117">To block the behavior, elastics auto update [EnableElasticsUpdate](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager.EnableElasticsUpdate) can be set to false.</span></span>

<span data-ttu-id="f1549-118">Standardmäßig sind für die Elastics Manager-Komponente keine elastischen Datenbanken für transformationstypen aktiviert, wenn sie einem Spielobjekt hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="f1549-118">By default, the elastics manager component, when added to a game object, won't have elastics enabled for any transforms type.</span></span>
<span data-ttu-id="f1549-119">Das Feld muss für bestimmte Transformationstypen aktiviert werden, um elastische Konfigurationen und Extents für `Manipulation types using elastic feedback` den ausgewählten Typ zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="f1549-119">The field `Manipulation types using elastic feedback` needs to be enabled for specific transform types to create elastics configuration and extents for the selected type.</span></span>

### <a name="elastics-configurations"></a><span data-ttu-id="f1549-120">Elastische Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="f1549-120">Elastics configurations</span></span>

<span data-ttu-id="f1549-121">Ähnlich wie [bei Begrenzungssteuerungskonfigurationen](../ux-building-blocks/bounds-control.md#configuration-objects)enthält elastic manager eine Reihe von Konfigurationsobjekten, die als skriptfähige Objekte gespeichert und von verschiedenen Instanzen oder Prefabs gemeinsam genutzt werden können.</span><span class="sxs-lookup"><span data-stu-id="f1549-121">Similar to [bounds control configurations](../ux-building-blocks/bounds-control.md#configuration-objects), elastic manager comes with a set of configuration objects that can be stored as scriptable objects and shared between different instances or prefabs.</span></span> <span data-ttu-id="f1549-122">Konfigurationen können entweder als einzelne skriptfähige Assetdateien oder als geschachtelte skriptfähige Objekte innerhalb von Prefabs freigegeben und verknüpft werden.</span><span class="sxs-lookup"><span data-stu-id="f1549-122">Configurations can be shared and linked either as individual scriptable asset files or nested scriptable assets inside of prefabs.</span></span> <span data-ttu-id="f1549-123">Weitere Konfigurationen können auch direkt auf der Instanz definiert werden, ohne eine Verknüpfung mit einem externen oder geschachtelten skriptbaren Asset zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="f1549-123">Further configurations can also be defined directly on the instance without linking to an external or nested scriptable asset.</span></span>

<span data-ttu-id="f1549-124">Der Elastics Manager-Inspektor gibt an, ob eine Konfiguration als Teil der aktuellen Instanz freigegeben oder inline ist, indem eine Meldung im Eigenschafteninspektor angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="f1549-124">The elastics manager inspector will indicate whether a configuration is shared or inlined as part of the current instance by showing a message in the property inspector.</span></span> <span data-ttu-id="f1549-125">Darüber hinaus können freigegebene Instanzen nicht direkt im Eigenschaftenfenster des Elastics-Managers selbst bearbeitet werden. Stattdessen muss das Objekt, mit dem sie eine Verknüpfung erstellen, direkt geändert werden, um versehentliche Änderungen an freigegebenen Konfigurationen zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="f1549-125">In addition, shared instances won't be editable directly in the elastics manager property window itself, but instead the asset it's linking to has to be directly modfied to avoid any accidental changes on shared configurations.</span></span>

<span data-ttu-id="f1549-126">Elastics Manager bietet Konfigurationsobjektoptionen für die folgenden Transformationstypen, die jeweils durch ein elastisches [Konfigurationsobjekt dargestellt werden:](#elastic-configuration-object)</span><span class="sxs-lookup"><span data-stu-id="f1549-126">Elastics manager offers configuration objects options for the following transform types, each of them represented by a [elastic configuration object](#elastic-configuration-object):</span></span>

- <span data-ttu-id="f1549-127">Elastische Übersetzung</span><span class="sxs-lookup"><span data-stu-id="f1549-127">Translation Elastic</span></span>
- <span data-ttu-id="f1549-128">Elastische Rotation</span><span class="sxs-lookup"><span data-stu-id="f1549-128">Rotation Elastic</span></span>
- <span data-ttu-id="f1549-129">Elastische Skalierung</span><span class="sxs-lookup"><span data-stu-id="f1549-129">Scale Elastic</span></span>

#### <a name="elastic-configuration-object"></a><span data-ttu-id="f1549-130">Elastisches Konfigurationsobjekt</span><span class="sxs-lookup"><span data-stu-id="f1549-130">Elastic configuration object</span></span>

<span data-ttu-id="f1549-131">Eine konfiguration für elastische Datenbanken definiert Eigenschaften für ein geerbte oszillatorielles Oszillatorsystem.</span><span class="sxs-lookup"><span data-stu-id="f1549-131">A elastics configuration defines properties for a damped harmonic oscillator differential system.</span></span>
<span data-ttu-id="f1549-132">Die folgenden Eigenschaften können angepasst werden, enthalten jedoch bereits eine Reihe von Standardwerten im MRTK:</span><span class="sxs-lookup"><span data-stu-id="f1549-132">The following properties can be adjusted but already come with a set of defaults in MRTK:</span></span>

- <span data-ttu-id="f1549-133">**Massen:** Die Massen des simulierten Oszillatorelements.</span><span class="sxs-lookup"><span data-stu-id="f1549-133">**Mass**: mass of the simulated oscillator element.</span></span>
- <span data-ttu-id="f1549-134">**HandK:** Hand spring-Konstante.</span><span class="sxs-lookup"><span data-stu-id="f1549-134">**HandK**: hand spring constant.</span></span>
- <span data-ttu-id="f1549-135">**EndK:** End cap spring constant.</span><span class="sxs-lookup"><span data-stu-id="f1549-135">**EndK**: end cap spring constant.</span></span>
- <span data-ttu-id="f1549-136">**SnapK:** Andockpunkt-Springkonst constant.</span><span class="sxs-lookup"><span data-stu-id="f1549-136">**SnapK**: snap point spring constant.</span></span>
- <span data-ttu-id="f1549-137">**Ziehen** Sie : Drag/Drop-Faktor, proportional zur Geschwindigkeit.</span><span class="sxs-lookup"><span data-stu-id="f1549-137">**Drag**: drag/damper factor, proportional to velocity.</span></span>

### <a name="elastics-extents"></a><span data-ttu-id="f1549-138">Elastische Dehnungen</span><span class="sxs-lookup"><span data-stu-id="f1549-138">Elastics extents</span></span>

<span data-ttu-id="f1549-139">Die Einstellungen für Elastische Bänder variieren je nach Art der Bearbeitung.</span><span class="sxs-lookup"><span data-stu-id="f1549-139">Elastics extents settings vary depending on the type of manipulation.</span></span> <span data-ttu-id="f1549-140">Übersetzung und Skalierung werden durch [elastische Volumendehnungen](#volume-elastic-extent) dargestellt, und die Drehung wird durch einen [elastischen Quaternionsdehnungs-Extent dargestellt.](#quaternion-elastic-extent)</span><span class="sxs-lookup"><span data-stu-id="f1549-140">Translation and scale are represented by [volume elastic extents](#volume-elastic-extent) and rotation is represented by a [quaternion elastic extent](#quaternion-elastic-extent).</span></span>

#### <a name="volume-elastic-extent"></a><span data-ttu-id="f1549-141">Elastischer Volume-Umfang</span><span class="sxs-lookup"><span data-stu-id="f1549-141">Volume elastic extent</span></span>

<span data-ttu-id="f1549-142">Volume-Extent definieren einen dreidimensionalen Raum, in dem sich der geerbte Oszillator frei bewegen kann.</span><span class="sxs-lookup"><span data-stu-id="f1549-142">Volume extents define a three dimensional space in which the damped harmonic oscillator is free to move.</span></span>

![Elastische Volumen-Stretch-Begrenzungen](../images/elastics/Elastics_Volume_Bounds.gif)

- <span data-ttu-id="f1549-144">**StretchBounds:** Stellt die unteren Grenzen des elastischen Raums dar.</span><span class="sxs-lookup"><span data-stu-id="f1549-144">**StretchBounds**: represents the lower bounds of the elastic space.</span></span>
- <span data-ttu-id="f1549-145">**UseBounds:** Gibt an, ob die Streckungsgrenze vom System beachtet werden soll.</span><span class="sxs-lookup"><span data-stu-id="f1549-145">**UseBounds**: whether the stretch bounds should be respected by the system.</span></span> <span data-ttu-id="f1549-146">True gibt an, dass die Enderzwingen angewendet werden, wenn die aktuelle Iteration der Zielposition außerhalb der Streckungsgrenze liegt.</span><span class="sxs-lookup"><span data-stu-id="f1549-146">If true, when the current iteration of the target position is outside the stretch bounds, the end force will be applied.</span></span>
- <span data-ttu-id="f1549-147">**SnapPoints:** Zeigt innerhalb des Raums, an dem das System ausrichten wird.</span><span class="sxs-lookup"><span data-stu-id="f1549-147">**SnapPoints**: points inside the space to which the system will snap.</span></span>
- <span data-ttu-id="f1549-148">**RepeatSnapPoints:** Wiederholt die Ausrichtungspunkte auf unendlich.</span><span class="sxs-lookup"><span data-stu-id="f1549-148">**RepeatSnapPoints**: repeats the snap points to infinity.</span></span> <span data-ttu-id="f1549-149">Vorhandene Ausrichtungspunkte dienen als Modulo, bei dem die tatsächlichen Andockpunkte den nächsten ganzzahligen Vielfachen jedes Andockpunkts zugeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="f1549-149">Existing snap points will serve as a modulo where the actual snap points are mapped to the closest integer multiples of every snap point.</span></span>
- <span data-ttu-id="f1549-150">**SnapRadius:** Die Entfernung, ab der Andockpunkte die Feder erzwingen.</span><span class="sxs-lookup"><span data-stu-id="f1549-150">**SnapRadius**: distance at which snap points begin forcing the spring.</span></span>

![Andockraster für elastische Volumes](../images/elastics/Elastics_Volume_Snap.gif)

#### <a name="quaternion-elastic-extent"></a><span data-ttu-id="f1549-152">Elastische Quaternion</span><span class="sxs-lookup"><span data-stu-id="f1549-152">Quaternion elastic extent</span></span>

<span data-ttu-id="f1549-153">Quaternionendungen definieren einen vierdimensionalen Drehungsraum, in dem der geerbte Oszillator rotiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="f1549-153">Quaternion extents define a four dimensional rotation space in which the damped harmonic oscillator is free to rotate.</span></span>

![Beispiel für elastische Drehung](../images/elastics/Elastics_Rotation.gif)

- <span data-ttu-id="f1549-155">**SnapPoints:** Eulerwinkel, an denen das System ausrichten wird.</span><span class="sxs-lookup"><span data-stu-id="f1549-155">**SnapPoints**: euler angles to which the system will snap.</span></span>
- <span data-ttu-id="f1549-156">**RepeatSnapPoints:** Wiederholt die Andockpunkte.</span><span class="sxs-lookup"><span data-stu-id="f1549-156">**RepeatSnapPoints**: repeats the snap points.</span></span> <span data-ttu-id="f1549-157">Vorhandene Ausrichtungspunkte dienen als Modulo, bei dem die tatsächlichen Andockpunkte den nächsten ganzzahligen Vielfachen jedes Andockpunkts zugeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="f1549-157">Existing snap points will serve as a modulo where the actual snap points are mapped to the closest integer multiples of every snap point.</span></span>
- <span data-ttu-id="f1549-158">**SnapRadius:** Bogenwinkel, bei dem Ausrichtungspunkte beginnen, die Feder in Euler-Grad zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="f1549-158">**SnapRadius**: arc-angle at which snap points begin forcing the spring in euler degrees.</span></span>

## <a name="elastics-example-scene"></a><span data-ttu-id="f1549-159">Beispielszene für elastische Datenbanken</span><span class="sxs-lookup"><span data-stu-id="f1549-159">Elastics example scene</span></span>

<span data-ttu-id="f1549-160">Beispiele für elastische Konfigurationen finden Sie in der `ElasticSystemExample` Szene.</span><span class="sxs-lookup"><span data-stu-id="f1549-160">You can find examples of elastics configurations in the `ElasticSystemExample` scene.</span></span>

![Beispielszene für elastische Datenbanken](../images/elastics/Elastics_Example_Scene.png)
