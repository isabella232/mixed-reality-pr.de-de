---
title: HowToAddNearInteractivity
description: Dokumentation zur Nahinteraktion in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Near Interaction,
ms.openlocfilehash: fc6fbb33e5a8e9aa6930f56f292f8ded51c53ff0
ms.sourcegitcommit: 0c717ed0043c7a65e2caf1452eb0f49059cdf154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2021
ms.locfileid: "108644846"
---
# <a name="how-to-add-near-interaction-in-mrtk"></a><span data-ttu-id="9dec4-104">Hinzufügen einer nahezuen Interaktion in MRTK</span><span class="sxs-lookup"><span data-stu-id="9dec4-104">How to add near interaction in MRTK</span></span>

<span data-ttu-id="9dec4-105">Nahinteraktionen kommen in Form von Berührungen und Greifern vor.</span><span class="sxs-lookup"><span data-stu-id="9dec4-105">Near interactions come in the form of touches and grabs.</span></span> <span data-ttu-id="9dec4-106">Touch- und Greifereignisse werden vom [PokePointer](pointers.md#pokepointer) bzw. [SpherePointer](pointers.md#spherepointer)als Zeigerereignisse ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="9dec4-106">Touch and grab events are raised as pointer events by the [PokePointer](pointers.md#pokepointer) and [SpherePointer](pointers.md#spherepointer), respectively.</span></span>

<span data-ttu-id="9dec4-107">Drei wichtige Schritte sind erforderlich, um auf Toucheingabe- und/oder Greifeingabeereignisse für ein bestimmtes GameObject zu lauschen.</span><span class="sxs-lookup"><span data-stu-id="9dec4-107">Three key steps are required to listen for touch and/or grab input events on a particular GameObject.</span></span>

1. <span data-ttu-id="9dec4-108">Stellen Sie sicher, dass der relevante Zeiger im [MRTK-Hauptkonfigurationsprofil registriert ist.](../../configuration/mixed-reality-configuration-guide.md)</span><span class="sxs-lookup"><span data-stu-id="9dec4-108">Ensure the relevant pointer is registered in the main [MRTK Configuration Profile](../../configuration/mixed-reality-configuration-guide.md).</span></span>
1. <span data-ttu-id="9dec4-109">Stellen Sie sicher, dass das gewünschte GameObject über die entsprechende [Greif-](#add-grab-interactions) oder [Touchskriptkomponente](#add-touch-interactions) und [`Unity Collider`](https://docs.unity3d.com/ScriptReference/Collider.html) verfügt.</span><span class="sxs-lookup"><span data-stu-id="9dec4-109">Ensure the desired GameObject has the appropriate [grab](#add-grab-interactions) or [touch](#add-touch-interactions) script component and [`Unity Collider`](https://docs.unity3d.com/ScriptReference/Collider.html).</span></span>
1. <span data-ttu-id="9dec4-110">Implementieren Sie eine Eingabehandlerschnittstelle für ein angefügtes Skript für das gewünschte GameObject, um auf die Greif- [oder](#grab-code-example) [Touchereignisse zu](#touch-code-example) lauschen.</span><span class="sxs-lookup"><span data-stu-id="9dec4-110">Implement an input handler interface on an attached script to the desired GameObject to listen for the [grab](#grab-code-example) or [touch](#touch-code-example) events.</span></span>

## <a name="add-grab-interactions"></a><span data-ttu-id="9dec4-111">Hinzufügen von Greifinteraktionen</span><span class="sxs-lookup"><span data-stu-id="9dec4-111">Add grab interactions</span></span>

1. <span data-ttu-id="9dec4-112">Stellen Sie [sicher, dass ein SpherePointer](pointers.md#spherepointer) im *MRTK-Zeigerprofil registriert ist.*</span><span class="sxs-lookup"><span data-stu-id="9dec4-112">Ensure a [SpherePointer](pointers.md#spherepointer) is registered in the *MRTK Pointer profile*.</span></span>

    <span data-ttu-id="9dec4-113">Das MRTK-Standardprofil und das Standardprofil HoloLens 2 bereits ein *SpherePointer-Profil.*</span><span class="sxs-lookup"><span data-stu-id="9dec4-113">The default MRTK profile and the default HoloLens 2 profile already contain a *SpherePointer*.</span></span> <span data-ttu-id="9dec4-114">Sie können bestätigen, dass ein SpherePointer erstellt wird, indem Sie das MRTK-Konfigurationsprofil auswählen und zu  >  **Eingabezeigerzeiger-Zeigeroptionen**  >  **navigieren.**</span><span class="sxs-lookup"><span data-stu-id="9dec4-114">One can confirm a SpherePointer will be created by selecting the MRTK Configuration Profile and navigating to **Input** > **Pointers** > **Pointer Options**.</span></span> <span data-ttu-id="9dec4-115">Das `GrabPointer` Standard-Prefab (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) sollte mit dem *Controllertyp* *"Articulated Hand"* aufgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="9dec4-115">The default `GrabPointer` prefab (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) should be listed with a *Controller Type* of *Articulated Hand*.</span></span> <span data-ttu-id="9dec4-116">Ein benutzerdefiniertes Prefab kann verwendet werden, solange es die -Klasse [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer) implementiert.</span><span class="sxs-lookup"><span data-stu-id="9dec4-116">A custom prefab can be utilized as long as it implements the [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer) class.</span></span>

    ![Beispiel für ein Greifzeigerprofil](../images/input/Pointers/GrabPointer_MRTKProfile.png)

    <span data-ttu-id="9dec4-118">Der Standardmäßige Greifzeiger fragt objekte in der Nähe in einem Kegel um den Greifpunkt ab, um mit der Hololens 2-Standardschnittstelle überein zu passen.</span><span class="sxs-lookup"><span data-stu-id="9dec4-118">The default grab pointer queries for nearby objects in a cone around the grab point to match the default Hololens 2 interface.</span></span>

    ![Conical-Greifzeiger](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

1. <span data-ttu-id="9dec4-120">Fügen Sie auf dem GameObject, das ziehbar sein soll, einen sowie [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) einen Collider hinzu.</span><span class="sxs-lookup"><span data-stu-id="9dec4-120">On the GameObject that should be grabbable, add a [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable), as well as a collider.</span></span>

    <span data-ttu-id="9dec4-121">Stellen Sie sicher, dass sich die Ebene des GameObject auf einer gierbaren Ebene befindet.</span><span class="sxs-lookup"><span data-stu-id="9dec4-121">Make sure the layer of the GameObject is on a grabbable layer.</span></span> <span data-ttu-id="9dec4-122">Standardmäßig können alle Ebenen außer *Räumliche Wahrnehmung* und *Raycasts ignorieren* gepackt werden.</span><span class="sxs-lookup"><span data-stu-id="9dec4-122">By default, all layers except *Spatial Awareness* and *Ignore Raycasts* are grabbable.</span></span> <span data-ttu-id="9dec4-123">Überprüfen Sie die *Grab Layer Masks* in Ihrem *GrabPointer-Prefab,* um zu überprüfen, welche Ebenen gepackt werden können.</span><span class="sxs-lookup"><span data-stu-id="9dec4-123">See which layers are grabbable by inspecting the *Grab Layer Masks* in your *GrabPointer* prefab.</span></span>

1. <span data-ttu-id="9dec4-124">Fügen Sie auf dem GameObject oder einem seiner Vorgänger eine Skriptkomponente hinzu, die die [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) -Schnittstelle implementiert.</span><span class="sxs-lookup"><span data-stu-id="9dec4-124">On the GameObject or one of its ancestors, add a script component that implements the [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) interface.</span></span> <span data-ttu-id="9dec4-125">Jeder Vorgänger des -Objekts mit dem [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) kann auch Zeigerereignisse empfangen.</span><span class="sxs-lookup"><span data-stu-id="9dec4-125">Any ancestor of the object with the [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) will be able to receive pointer events, as well.</span></span>

### <a name="grab-code-example"></a><span data-ttu-id="9dec4-126">Beispiel für den Codegrabber</span><span class="sxs-lookup"><span data-stu-id="9dec4-126">Grab code example</span></span>

<span data-ttu-id="9dec4-127">Im Folgenden finden Sie ein Skript, das gedruckt wird, wenn es sich bei einem Ereignis um eine Toucheingabe oder ein Greifen handelt.</span><span class="sxs-lookup"><span data-stu-id="9dec4-127">Below is a script that will print if an event is a touch or grab.</span></span> <span data-ttu-id="9dec4-128">In der relevanten *IMixedRealityPointerHandler-Schnittstellenfunktion* kann der Typ des Zeigers betrachtet werden, der dieses Ereignis über die [`MixedRealityPointerEventData`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerEventData) auslöst.</span><span class="sxs-lookup"><span data-stu-id="9dec4-128">In the relevant *IMixedRealityPointerHandler* interface function, one can look at the type of pointer that triggers that event via the [`MixedRealityPointerEventData`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerEventData).</span></span> <span data-ttu-id="9dec4-129">Wenn der Zeiger ein *SpherePointer* ist, ist die Interaktion ein Greifen.</span><span class="sxs-lookup"><span data-stu-id="9dec4-129">If the pointer is a *SpherePointer*, the interaction is a grab.</span></span>

```c#
public class PrintPointerEvents : MonoBehaviour, IMixedRealityPointerHandler
{
    public void OnPointerDown(MixedRealityPointerEventData eventData)
    {
        if (eventData.Pointer is SpherePointer)
        {
            Debug.Log($"Grab start from {eventData.Pointer.PointerName}");
        }
        if (eventData.Pointer is PokePointer)
        {
            Debug.Log($"Touch start from {eventData.Pointer.PointerName}");
        }
    }

    public void OnPointerClicked(MixedRealityPointerEventData eventData) {}
    public void OnPointerDragged(MixedRealityPointerEventData eventData) {}
    public void OnPointerUp(MixedRealityPointerEventData eventData) {}
}
```

## <a name="add-touch-interactions"></a><span data-ttu-id="9dec4-130">Hinzufügen von Touchinteraktionen</span><span class="sxs-lookup"><span data-stu-id="9dec4-130">Add touch interactions</span></span>

<span data-ttu-id="9dec4-131">Der Prozess zum Hinzufügen von Touchinteraktionen für UnityUI-Elemente unterscheidet sich von der Vorgehensweise für 3D-GameObjects von Vane.</span><span class="sxs-lookup"><span data-stu-id="9dec4-131">The process for adding touch interactions on UnityUI elements is different than for vanilla 3D GameObjects.</span></span> <span data-ttu-id="9dec4-132">Sie können mit dem folgenden Abschnitt( *Unity UI*) zum Aktivieren von Komponenten der Unity-Benutzeroberfläche springen.</span><span class="sxs-lookup"><span data-stu-id="9dec4-132">You can skip to the following section, *Unity UI*, for enabling Unity UI components.</span></span>

<span data-ttu-id="9dec4-133">Stellen Sie jedoch für **beide** Arten von UX-Elementen sicher, dass ein Element vom Typ ["PointerePointer"](pointers.md#pokepointer) im *MRTK-Zeigerprofil* registriert ist.</span><span class="sxs-lookup"><span data-stu-id="9dec4-133">For **both** types of UX elements though, ensure a [PokePointer](pointers.md#pokepointer) is registered in the *MRTK Pointer profile*.</span></span>

<span data-ttu-id="9dec4-134">Das MRTK-Standardprofil und das Standardmäßige HoloLens 2-Profil enthalten bereits einen *DerePointer*.</span><span class="sxs-lookup"><span data-stu-id="9dec4-134">The default MRTK profile and the default HoloLens 2 profile already contain a *PokePointer*.</span></span> <span data-ttu-id="9dec4-135">Sie können bestätigen, dass ein PointerePointer erstellt wird, indem Sie das MRTK-Konfigurationsprofil auswählen und zu  >  **Eingabezeigerzeigeroptionen**  >  navigieren.</span><span class="sxs-lookup"><span data-stu-id="9dec4-135">One can confirm a PokePointer will be created by selecting the MRTK Configuration Profile and navigate to **Input** > **Pointers** > **Pointer Options**.</span></span> <span data-ttu-id="9dec4-136">Das `PokePointer` Standard-Prefab (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) sollte mit dem *Controllertyp* *"Artikulierte Hand"* aufgelistet werden.</span><span class="sxs-lookup"><span data-stu-id="9dec4-136">The default `PokePointer` (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) prefab should be listed with a *Controller Type* of *Articulated Hand*.</span></span> <span data-ttu-id="9dec4-137">Ein benutzerdefiniertes Prefab kann verwendet werden, solange es die [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) -Klasse implementiert.</span><span class="sxs-lookup"><span data-stu-id="9dec4-137">A custom prefab can be utilized as long as it implements the [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) class.</span></span>

![Beispiel für Zeigerprofil](../images/input/Pointers/PokePointer_MRTKProfile.png)

### <a name="3d-gameobjects"></a><span data-ttu-id="9dec4-139">3D GameObjects</span><span class="sxs-lookup"><span data-stu-id="9dec4-139">3D GameObjects</span></span>

<span data-ttu-id="9dec4-140">Es gibt zwei verschiedene Möglichkeiten, Touchinteraktionen zu 3D GameObjects hinzuzufügen, je nachdem, ob Ihr 3D-Objekt nur eine einzelne touchierbare Ebene haben soll, oder davon, ob es basierend auf seinem gesamten Collider touchierbar sein soll.</span><span class="sxs-lookup"><span data-stu-id="9dec4-140">There are two different ways of adding touch interactions to 3D GameObjects, depending on if your 3d object should only have a single touchable plane, or of if it should be touchable based on its entire collider.</span></span>
<span data-ttu-id="9dec4-141">Die erste Möglichkeit besteht in der Regel bei Objekten mit BoxColliders, bei denen nur ein einzelnes Gesicht des Colliders auf Berührungsereignisse reagieren soll.</span><span class="sxs-lookup"><span data-stu-id="9dec4-141">The first way is typically on objects with BoxColliders, where it is desired to only have a single face of the collider react to touch events.</span></span> <span data-ttu-id="9dec4-142">Die andere ist für Objekte, die aus beliebiger Richtung basierend auf ihrem Collider berührbar sein müssen.</span><span class="sxs-lookup"><span data-stu-id="9dec4-142">The other is for objects that need to be touchable from any direction based on their collider.</span></span>

### <a name="single-face-touch"></a><span data-ttu-id="9dec4-143">Touch mit einzelnem Gesicht</span><span class="sxs-lookup"><span data-stu-id="9dec4-143">Single face touch</span></span>

<span data-ttu-id="9dec4-144">Dies ist nützlich, um Situationen zu ermöglichen, in denen nur ein einzelnes Gesicht berührt werden muss.</span><span class="sxs-lookup"><span data-stu-id="9dec4-144">This is useful to enable situations where only a single face needs to be touchable.</span></span> <span data-ttu-id="9dec4-145">Bei dieser Option wird davon ausgegangen, dass das Spielobjekt über einen BoxCollider verfügt.</span><span class="sxs-lookup"><span data-stu-id="9dec4-145">This option assumes that the game object has a BoxCollider.</span></span> <span data-ttu-id="9dec4-146">Es ist möglich, dies mit Nicht-BoxCollider-Objekten zu verwenden. In diesem Fall werden die Eigenschaften "Bounds" und "Local Center" viel manuell festgelegt, um die berührbare Ebene zu konfigurieren (d. h. Begrenzungen sollten auf einen Wert festgelegt werden, der nicht null ist).</span><span class="sxs-lookup"><span data-stu-id="9dec4-146">it's possible to use this with non-BoxCollider objects, in which case the 'Bounds' and 'Local Center' properties much be manually set to configure the touchable plane (i.e. Bounds should be set to a non-zero-zero value).</span></span>

1. <span data-ttu-id="9dec4-147">Fügen Sie dem GameObject, das berührbar sein soll, eine BoxCollider- und eine [ `NearInteractionTouchable` ] -Komponente (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) hinzu.</span><span class="sxs-lookup"><span data-stu-id="9dec4-147">On the GameObject that should be touchable, add a BoxCollider and a [`NearInteractionTouchable`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) component.</span></span>

    1. <span data-ttu-id="9dec4-148">Legen **Sie Ereignisse** auf Receive to *Touch* fest, wenn Sie die Schnittstelle [ `IMixedRealityTouchHandler` ] (xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) in Ihrem Komponentenskript unten verwenden.</span><span class="sxs-lookup"><span data-stu-id="9dec4-148">Set **Events to Receive** to *Touch* if using the [`IMixedRealityTouchHandler`] (xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script below.</span></span>

    1. <span data-ttu-id="9dec4-149">Klicken **Sie auf Begrenzungen korrigieren und** **Zentrieren korrigieren.**</span><span class="sxs-lookup"><span data-stu-id="9dec4-149">Click **Fix bounds** and **Fix center**</span></span>

    ![NearInteractionTouchable-Setup](../images/input/Pointers/NearInteractionTouchableSetup.gif)

1. <span data-ttu-id="9dec4-151">Fügen Sie für dieses Objekt oder einen seiner Vorgänger eine Skriptkomponente hinzu, die implementiert. [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span><span class="sxs-lookup"><span data-stu-id="9dec4-151">On that object or one of its ancestors, add a script component that implements the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span></span>
   <span data-ttu-id="9dec4-152">Schnittstelle implementiert.</span><span class="sxs-lookup"><span data-stu-id="9dec4-152">interface.</span></span> <span data-ttu-id="9dec4-153">Jeder Vorgänger des Objekts mit [ `NearInteractionTouchable` ] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) kann auch Zeigerereignisse empfangen.</span><span class="sxs-lookup"><span data-stu-id="9dec4-153">Any ancestor of the object with the [`NearInteractionTouchable`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) will be able to receive pointer events, as well.</span></span>

> [!NOTE]
> <span data-ttu-id="9dec4-154">Beachten Sie in der Editor-Szenenansicht mit ausgewähltem *GameObject NearInteractionTouchable* ein weißes Umriss-Quadrat und einen Pfeil.</span><span class="sxs-lookup"><span data-stu-id="9dec4-154">In the editor scene view with the *NearInteractionTouchable* GameObject selected, notice a white outline square and arrow.</span></span> <span data-ttu-id="9dec4-155">Der Pfeil zeigt auf den "Front" des berührbaren .</span><span class="sxs-lookup"><span data-stu-id="9dec4-155">The arrow points to the "front" of the touchable.</span></span> <span data-ttu-id="9dec4-156">Das kollisionsfähige Ist ist nur in dieser Richtung berührbar.</span><span class="sxs-lookup"><span data-stu-id="9dec4-156">The collidable will only be touchable from that direction.</span></span> <span data-ttu-id="9dec4-157">Um einen Collider aus allen Richtungen berührbar zu machen, lesen Sie den Abschnitt zum Touch eines [beliebigen Colliders.](#arbitrary-collider-touch)</span><span class="sxs-lookup"><span data-stu-id="9dec4-157">To make a collider touchable from all directions, see the section on [arbitrary collider touch](#arbitrary-collider-touch).</span></span>
> <span data-ttu-id="9dec4-158">![NearInteractionTouchableMos ](../images/input/Pointers/NearInteractionTouchableGizmos.png)</span><span class="sxs-lookup"><span data-stu-id="9dec4-158">![NearInteractionTouchable Gizmos ](../images/input/Pointers/NearInteractionTouchableGizmos.png)</span></span>

### <a name="arbitrary-collider-touch"></a><span data-ttu-id="9dec4-159">Beliebiger Collider touch</span><span class="sxs-lookup"><span data-stu-id="9dec4-159">Arbitrary collider touch</span></span>

<span data-ttu-id="9dec4-160">Dies ist nützlich, um Situationen zu ermöglichen, in denen das Spielobjekt entlang des gesamten Collidergesichts berührt werden muss.</span><span class="sxs-lookup"><span data-stu-id="9dec4-160">This is useful to enable situations where the game object needs to be touchable along its entire collider face.</span></span> <span data-ttu-id="9dec4-161">Dies kann beispielsweise verwendet werden, um Touchinteraktionen für ein Objekt mit einem SphereCollider zu ermöglichen, bei dem der gesamte Collider berührt werden muss.</span><span class="sxs-lookup"><span data-stu-id="9dec4-161">For example, this can be used to enable touch interactions for an object with a SphereCollider, where the entire collider needs to be touchable.</span></span>

1. <span data-ttu-id="9dec4-162">Fügen Sie auf dem GameObject, das touchierbar sein soll, einen Collider und eine `NearInteractionTouchableVolume` [] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableVolume)-Komponente hinzu.</span><span class="sxs-lookup"><span data-stu-id="9dec4-162">On the GameObject that should be touchable, add a collider and a [`NearInteractionTouchableVolume`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableVolume) component.</span></span>

    1. <span data-ttu-id="9dec4-163">Legen Sie **Ereignisse auf Receive (Empfangen)** auf *Touch* fest, wenn Sie die `IMixedRealityTouchHandler` []-Schnittstelle (xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) in Ihrem Komponentenskript unten verwenden.</span><span class="sxs-lookup"><span data-stu-id="9dec4-163">Set **Events to Receive** to *Touch* if using the [`IMixedRealityTouchHandler`] (xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script below.</span></span>

1. <span data-ttu-id="9dec4-164">Fügen Sie für dieses Objekt oder einen seiner Vorgänger eine Skriptkomponente hinzu, die implementiert. [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span><span class="sxs-lookup"><span data-stu-id="9dec4-164">On that object or one of its ancestors, add a script component that implements the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span></span>
   <span data-ttu-id="9dec4-165">Schnittstelle implementiert.</span><span class="sxs-lookup"><span data-stu-id="9dec4-165">interface.</span></span> <span data-ttu-id="9dec4-166">Alle Vorgänger des Objekts mit dem `NearInteractionTouchable` [] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) können ebenfalls Zeigerereignisse empfangen.</span><span class="sxs-lookup"><span data-stu-id="9dec4-166">Any ancestor of the object with the [`NearInteractionTouchable`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) will be able to receive pointer events, as well.</span></span>

### <a name="unity-ui"></a><span data-ttu-id="9dec4-167">Unity-Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="9dec4-167">Unity UI</span></span>

1. <span data-ttu-id="9dec4-168">Fügen Sie einen [UnityUI-Zeichenbereich](https://docs.unity3d.com/Manual/UICanvas.html) in der Szene hinzu, oder stellen Sie sicher, dass er vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="9dec4-168">Add/ensure there is a [UnityUI canvas](https://docs.unity3d.com/Manual/UICanvas.html) in the scene.</span></span>

1. <span data-ttu-id="9dec4-169">Fügen Sie auf dem GameObject, das touchierbar sein soll, eine [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) -Komponente hinzu.</span><span class="sxs-lookup"><span data-stu-id="9dec4-169">On the GameObject that should be touchable, add a [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) component.</span></span>  

    1. <span data-ttu-id="9dec4-170">Legen Sie **Ereignisse auf Receive (Empfangen)** auf *Touch* fest, wenn Sie die [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) -Schnittstelle in Ihrem Komponentenskript unten verwenden.</span><span class="sxs-lookup"><span data-stu-id="9dec4-170">Set **Events to Receive** to *Touch* if using the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script below.</span></span>

1. <span data-ttu-id="9dec4-171">Fügen Sie für dieses Objekt oder einen seiner Vorgänger eine Skriptkomponente hinzu, die die [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) -Schnittstelle implementiert.</span><span class="sxs-lookup"><span data-stu-id="9dec4-171">On that object or one of its ancestors, add a script component that implements the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface.</span></span> <span data-ttu-id="9dec4-172">Jeder Vorgänger des -Objekts mit dem [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) kann auch Zeigerereignisse empfangen.</span><span class="sxs-lookup"><span data-stu-id="9dec4-172">Any ancestor of the object with the [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) will be able to receive pointer events as well.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9dec4-173">Objekte verhalten sich möglicherweise nicht wie erwartet, wenn sie sich auf überlappenden Canvasobjekten befinden.</span><span class="sxs-lookup"><span data-stu-id="9dec4-173">Objects may not behave as expected if they are located on overlapping canvas objects.</span></span> <span data-ttu-id="9dec4-174">Um ein konsistentes Verhalten sicherzustellen, überlappen Sie canvas-Objekte in Ihrer Szene niemals.</span><span class="sxs-lookup"><span data-stu-id="9dec4-174">To ensure consistent behavior, never overlap canvas objects in your scene.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9dec4-175">Für die Eigenschaft Ereignisse, die empfangen werden sollen, stehen in der `NearInteractionTouchable` Skriptkomponente zwei Optionen zur Verfügung: *Zeiger* und *Touch.* </span><span class="sxs-lookup"><span data-stu-id="9dec4-175">On the `NearInteractionTouchable` script component, for the property *Events to Receive* there are two options: *Pointer* and *Touch*.</span></span> <span data-ttu-id="9dec4-176">Legen Sie *Ereignisse auf Empfangen* auf *Zeiger* fest, wenn Sie die [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) -Schnittstelle verwenden, und legen Sie auf *Touch* fest, wenn Sie die Schnittstelle in [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) Ihrem Komponentenskript verwenden, das auf die Eingabeereignisse reagiert bzw. behandelt.</span><span class="sxs-lookup"><span data-stu-id="9dec4-176">Set *Events to Receive* to *Pointer* if using the [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) interface and set to *Touch* if using the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script that responds/handles the input events.</span></span>

#### <a name="touch-code-example"></a><span data-ttu-id="9dec4-177">Beispiel für Touchcode</span><span class="sxs-lookup"><span data-stu-id="9dec4-177">Touch code example</span></span>

<span data-ttu-id="9dec4-178">Der folgende Code veranschaulicht ein MonoBehaviour-Element, das mit einer Variant-Komponente an ein GameObject angefügt werden kann [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) und auf Toucheingabeereignisse reagiert.</span><span class="sxs-lookup"><span data-stu-id="9dec4-178">The code below demonstrates a MonoBehaviour that can be attached to a GameObject with a [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) variant component and respond to touch input events.</span></span>

```c#
public class TouchEventsExample : MonoBehaviour, IMixedRealityTouchHandler
{
    public void OnTouchStarted(HandTrackingInputEventData eventData)
    {
        string ptrName = eventData.Pointer.PointerName;
        Debug.Log($"Touch started from {ptrName}");
    }
    public void OnTouchCompleted(HandTrackingInputEventData eventData) {}
    public void OnTouchUpdated(HandTrackingInputEventData eventData) { }
}
```

## <a name="near-interaction-script-examples"></a><span data-ttu-id="9dec4-179">Beispiele für Skripts für die nahe Interaktion</span><span class="sxs-lookup"><span data-stu-id="9dec4-179">Near interaction script examples</span></span>

### <a name="touch-events"></a><span data-ttu-id="9dec4-180">Berührungsereignisse</span><span class="sxs-lookup"><span data-stu-id="9dec4-180">Touch events</span></span>

<span data-ttu-id="9dec4-181">In diesem Beispiel wird ein Cube erstellt, touchierbar und die Farbe bei der Berührung geändert.</span><span class="sxs-lookup"><span data-stu-id="9dec4-181">This example creates a cube, makes it touchable, and changes color on touch.</span></span>

```c#
public static void MakeChangeColorOnTouch(GameObject target)
{
    // Add and configure the touchable
    var touchable = target.AddComponent<NearInteractionTouchableVolume>();
    touchable.EventsToReceive = TouchableEventType.Pointer;

    var material = target.GetComponent<Renderer>().material;
    // Change color on pointer down and up
    var pointerHandler = target.AddComponent<PointerHandler>();
    pointerHandler.OnPointerDown.AddListener((e) => material.color = Color.green);
    pointerHandler.OnPointerUp.AddListener((e) => material.color = Color.magenta);
}
```

### <a name="grab-events"></a><span data-ttu-id="9dec4-182">Grab-Ereignisse</span><span class="sxs-lookup"><span data-stu-id="9dec4-182">Grab events</span></span>

<span data-ttu-id="9dec4-183">Das folgende Beispiel zeigt, wie Ein GameObject gezogen werden kann.</span><span class="sxs-lookup"><span data-stu-id="9dec4-183">The below example shows how to make a GameObject draggable.</span></span> <span data-ttu-id="9dec4-184">Es wird davon ausgegangen, dass das Spielobjekt über einen Collider verfügt.</span><span class="sxs-lookup"><span data-stu-id="9dec4-184">Assumes that the game object has a collider on it.</span></span>

```c#
public static void MakeNearDraggable(GameObject target)
{
    // Instantiate and add grabbable
    target.AddComponent<NearInteractionGrabbable>();

    // Add ability to drag by re-parenting to pointer object on pointer down
    var pointerHandler = target.AddComponent<PointerHandler>();
    pointerHandler.OnPointerDown.AddListener((e) =>
    {
        if (e.Pointer is SpherePointer)
        {
            target.transform.parent = ((SpherePointer)(e.Pointer)).transform;
        }
    });
    pointerHandler.OnPointerUp.AddListener((e) =>
    {
        if (e.Pointer is SpherePointer)
        {
            target.transform.parent = null;
        }
    });
}
```

## <a name="useful-apis"></a><span data-ttu-id="9dec4-185">Nützliche APIs</span><span class="sxs-lookup"><span data-stu-id="9dec4-185">Useful APIs</span></span>

* [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable)
* [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable)
* [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI)
* [`NearInteractionTouchableVolume`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableVolume)
* [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
* [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler)

## <a name="see-also"></a><span data-ttu-id="9dec4-186">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="9dec4-186">See also</span></span>

* [<span data-ttu-id="9dec4-187">Übersicht über die Eingabe</span><span class="sxs-lookup"><span data-stu-id="9dec4-187">Input Overview</span></span>](overview.md)
* [<span data-ttu-id="9dec4-188">Zeiger</span><span class="sxs-lookup"><span data-stu-id="9dec4-188">Pointers</span></span>](pointers.md)
* [<span data-ttu-id="9dec4-189">Eingabeereignisse</span><span class="sxs-lookup"><span data-stu-id="9dec4-189">Input Events</span></span>](input-events.md)
