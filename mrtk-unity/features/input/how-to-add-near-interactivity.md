---
title: Hinzufügen von nähebezogener Interaktivität
description: Dokumentation zur Nahinteraktion in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Near Interaction,
ms.openlocfilehash: fc0d6d4013392db74e5c8637574c258bee857865
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144179"
---
# <a name="how-to-add-near-interaction-in-mrtk"></a><span data-ttu-id="d6eb3-104">Hinzufügen einer nahezuen Interaktion in MRTK</span><span class="sxs-lookup"><span data-stu-id="d6eb3-104">How to add near interaction in MRTK</span></span>

<span data-ttu-id="d6eb3-105">Nahinteraktionen kommen in Form von Berührungen und Greifern vor.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-105">Near interactions come in the form of touches and grabs.</span></span> <span data-ttu-id="d6eb3-106">Touch- und Greifereignisse werden vom [PokePointer](pointers.md#pokepointer) bzw. [SpherePointer](pointers.md#spherepointer)als Zeigerereignisse ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-106">Touch and grab events are raised as pointer events by the [PokePointer](pointers.md#pokepointer) and [SpherePointer](pointers.md#spherepointer), respectively.</span></span>

<span data-ttu-id="d6eb3-107">Drei wichtige Schritte sind erforderlich, um auf Toucheingabe- und/oder Greifeingabeereignisse für ein bestimmtes GameObject zu lauschen.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-107">Three key steps are required to listen for touch and/or grab input events on a particular GameObject.</span></span>

1. <span data-ttu-id="d6eb3-108">Stellen Sie sicher, dass der relevante Zeiger im [MRTK-Hauptkonfigurationsprofil registriert ist.](../../configuration/mixed-reality-configuration-guide.md)</span><span class="sxs-lookup"><span data-stu-id="d6eb3-108">Ensure the relevant pointer is registered in the main [MRTK Configuration Profile](../../configuration/mixed-reality-configuration-guide.md).</span></span>
1. <span data-ttu-id="d6eb3-109">Stellen Sie sicher, dass das gewünschte GameObject über die entsprechende [Greif-](#add-grab-interactions) oder [Touchskriptkomponente](#add-touch-interactions) und [`Unity Collider`](https://docs.unity3d.com/ScriptReference/Collider.html) verfügt.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-109">Ensure the desired GameObject has the appropriate [grab](#add-grab-interactions) or [touch](#add-touch-interactions) script component and [`Unity Collider`](https://docs.unity3d.com/ScriptReference/Collider.html).</span></span>
1. <span data-ttu-id="d6eb3-110">Implementieren Sie eine Eingabehandlerschnittstelle für ein angefügtes Skript für das gewünschte GameObject, um auf die Greif- [oder](#grab-code-example) [Touchereignisse zu](#touch-code-example) lauschen.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-110">Implement an input handler interface on an attached script to the desired GameObject to listen for the [grab](#grab-code-example) or [touch](#touch-code-example) events.</span></span>

## <a name="add-grab-interactions"></a><span data-ttu-id="d6eb3-111">Hinzufügen von Greifinteraktionen</span><span class="sxs-lookup"><span data-stu-id="d6eb3-111">Add grab interactions</span></span>

1. <span data-ttu-id="d6eb3-112">Stellen Sie [sicher, dass ein SpherePointer](pointers.md#spherepointer) im *MRTK-Zeigerprofil registriert ist.*</span><span class="sxs-lookup"><span data-stu-id="d6eb3-112">Ensure a [SpherePointer](pointers.md#spherepointer) is registered in the *MRTK Pointer profile*.</span></span>

    <span data-ttu-id="d6eb3-113">Das MRTK-Standardprofil und das Standardprofil HoloLens 2 bereits ein *SpherePointer-Profil.*</span><span class="sxs-lookup"><span data-stu-id="d6eb3-113">The default MRTK profile and the default HoloLens 2 profile already contain a *SpherePointer*.</span></span> <span data-ttu-id="d6eb3-114">Sie können bestätigen, dass ein SpherePointer erstellt wird, indem Sie das MRTK-Konfigurationsprofil auswählen und zu  >  **Eingabezeigerzeiger-Zeigeroptionen**  >  **navigieren.**</span><span class="sxs-lookup"><span data-stu-id="d6eb3-114">One can confirm a SpherePointer will be created by selecting the MRTK Configuration Profile and navigating to **Input** > **Pointers** > **Pointer Options**.</span></span> <span data-ttu-id="d6eb3-115">Das `GrabPointer` Standard-Prefab (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) sollte mit dem *Controllertyp* *"Articulated Hand"* aufgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-115">The default `GrabPointer` prefab (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) should be listed with a *Controller Type* of *Articulated Hand*.</span></span> <span data-ttu-id="d6eb3-116">Ein benutzerdefiniertes Prefab kann verwendet werden, solange es die -Klasse [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer) implementiert.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-116">A custom prefab can be utilized as long as it implements the [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer) class.</span></span>

    ![Beispiel für ein Greifzeigerprofil](../images/input/Pointers/GrabPointer_MRTKProfile.png)

    <span data-ttu-id="d6eb3-118">Der Standardmäßige Greifzeiger fragt objekte in der Nähe in einem Kegel um den Greifpunkt ab, um der Standardmäßigen Hololens 2-Schnittstelle zu passen.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-118">The default grab pointer queries for nearby objects in a cone around the grab point to match the default Hololens 2 interface.</span></span>

    ![Conical Grab-Zeiger](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

1. <span data-ttu-id="d6eb3-120">Fügen Sie auf dem GameObject, das ziehbar sein soll, einen sowie [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) einen Collider hinzu.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-120">On the GameObject that should be grabbable, add a [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable), as well as a collider.</span></span>

    <span data-ttu-id="d6eb3-121">Stellen Sie sicher, dass sich die Ebene des GameObject auf einer greifbaren Ebene befindet.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-121">Make sure the layer of the GameObject is on a grabbable layer.</span></span> <span data-ttu-id="d6eb3-122">Standardmäßig sind alle Ebenen außer *Spatial Awareness und* Ignore *Raycasts* greifbar.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-122">By default, all layers except *Spatial Awareness* and *Ignore Raycasts* are grabbable.</span></span> <span data-ttu-id="d6eb3-123">Sehen Sie sich die Greifebenenmasken *in* Ihrem GrabPointer-Prefab an, um zu sehen, welche Ebenen *greifbar* sind.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-123">See which layers are grabbable by inspecting the *Grab Layer Masks* in your *GrabPointer* prefab.</span></span>

1. <span data-ttu-id="d6eb3-124">Fügen Sie auf dem GameObject oder einem seiner Vorgänger eine Skriptkomponente hinzu, die die -Schnittstelle [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) implementiert.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-124">On the GameObject or one of its ancestors, add a script component that implements the [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) interface.</span></span> <span data-ttu-id="d6eb3-125">Jeder Vorgänger des Objekts mit dem [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) kann auch Zeigerereignisse empfangen.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-125">Any ancestor of the object with the [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) will be able to receive pointer events, as well.</span></span>

### <a name="grab-code-example"></a><span data-ttu-id="d6eb3-126">Beispiel für "Code greifen"</span><span class="sxs-lookup"><span data-stu-id="d6eb3-126">Grab code example</span></span>

<span data-ttu-id="d6eb3-127">Im Folgenden finden Sie ein Skript, das aus druckt, wenn es sich bei einem Ereignis um eine Berührung oder einen Greif handelt.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-127">Below is a script that will print if an event is a touch or grab.</span></span> <span data-ttu-id="d6eb3-128">In der *relevanten IMixedRealityPointerHandler-Schnittstellenfunktion* können Sie den Typ des Zeigers betrachten, der dieses Ereignis über [`MixedRealityPointerEventData`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerEventData) auslöst.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-128">In the relevant *IMixedRealityPointerHandler* interface function, one can look at the type of pointer that triggers that event via the [`MixedRealityPointerEventData`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerEventData).</span></span> <span data-ttu-id="d6eb3-129">Wenn der Zeiger ein *SpherePointer* ist, ist die Interaktion ein Greif.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-129">If the pointer is a *SpherePointer*, the interaction is a grab.</span></span>

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

## <a name="add-touch-interactions"></a><span data-ttu-id="d6eb3-130">Hinzufügen von Touchinteraktionen</span><span class="sxs-lookup"><span data-stu-id="d6eb3-130">Add touch interactions</span></span>

<span data-ttu-id="d6eb3-131">Der Prozess zum Hinzufügen von Touchinteraktionen zu UnityUI-Elementen ist anders als bei 3D-GameObjects.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-131">The process for adding touch interactions on UnityUI elements is different than for vanilla 3D GameObjects.</span></span> <span data-ttu-id="d6eb3-132">Sie können zum Aktivieren von Unity-Benutzeroberflächenkomponenten mit dem folgenden Abschnitt( Unity-Benutzeroberfläche) springen.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-132">You can skip to the following section, *Unity UI*, for enabling Unity UI components.</span></span>

<span data-ttu-id="d6eb3-133">Stellen **Sie für** beide Typen von UX-Elementen jedoch sicher, dass ein [PokePointer](pointers.md#pokepointer) im *MRTK-Zeigerprofil registriert ist.*</span><span class="sxs-lookup"><span data-stu-id="d6eb3-133">For **both** types of UX elements though, ensure a [PokePointer](pointers.md#pokepointer) is registered in the *MRTK Pointer profile*.</span></span>

<span data-ttu-id="d6eb3-134">Das MRTK-Standardprofil und das Standardprofil HoloLens 2 bereits *ein PokePointer-Profil.*</span><span class="sxs-lookup"><span data-stu-id="d6eb3-134">The default MRTK profile and the default HoloLens 2 profile already contain a *PokePointer*.</span></span> <span data-ttu-id="d6eb3-135">Sie können bestätigen, dass ein PokePointer erstellt wird, indem Sie das MRTK-Konfigurationsprofil auswählen und zu  >  **Eingabezeigerzeigeroptionen**  >  **navigieren.**</span><span class="sxs-lookup"><span data-stu-id="d6eb3-135">One can confirm a PokePointer will be created by selecting the MRTK Configuration Profile and navigate to **Input** > **Pointers** > **Pointer Options**.</span></span> <span data-ttu-id="d6eb3-136">Das Standard `PokePointer` prefab (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) sollte mit dem *Controllertyp* *"Articulated Hand"* aufgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-136">The default `PokePointer` (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) prefab should be listed with a *Controller Type* of *Articulated Hand*.</span></span> <span data-ttu-id="d6eb3-137">Ein benutzerdefiniertes Prefab kann verwendet werden, solange es die -Klasse [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) implementiert.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-137">A custom prefab can be utilized as long as it implements the [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) class.</span></span>

![Poke-Zeigerprofilbeispiel](../images/input/Pointers/PokePointer_MRTKProfile.png)

### <a name="3d-gameobjects"></a><span data-ttu-id="d6eb3-139">3D-GameObjects</span><span class="sxs-lookup"><span data-stu-id="d6eb3-139">3D GameObjects</span></span>

<span data-ttu-id="d6eb3-140">Es gibt zwei verschiedene Möglichkeiten, 3D GameObjects Touchinteraktionen hinzufügen zu können, je nachdem, ob Ihr 3D-Objekt nur eine einzige berührbare Ebene haben soll, oder ob es auf der Grundlage des gesamten Colliders berührbar sein sollte.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-140">There are two different ways of adding touch interactions to 3D GameObjects, depending on if your 3d object should only have a single touchable plane, or of if it should be touchable based on its entire collider.</span></span>
<span data-ttu-id="d6eb3-141">Die erste Möglichkeit besteht in der Regel bei Objekten mit BoxColliders, bei denen nur ein einzelnes Gesicht des Colliders auf Berührungsereignisse reagieren soll.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-141">The first way is typically on objects with BoxColliders, where it is desired to only have a single face of the collider react to touch events.</span></span> <span data-ttu-id="d6eb3-142">Die andere ist für Objekte, die je nach Collider aus beliebiger Richtung erreichbar sein müssen.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-142">The other is for objects that need to be touchable from any direction based on their collider.</span></span>

### <a name="single-face-touch"></a><span data-ttu-id="d6eb3-143">Toucheingabe mit einzelnem Gesicht</span><span class="sxs-lookup"><span data-stu-id="d6eb3-143">Single face touch</span></span>

<span data-ttu-id="d6eb3-144">Dies ist nützlich, um Situationen zu ermöglichen, in denen nur ein einzelnes Gesicht berührt werden muss.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-144">This is useful to enable situations where only a single face needs to be touchable.</span></span> <span data-ttu-id="d6eb3-145">Bei dieser Option wird davon ausgegangen, dass das Spielobjekt über einen BoxCollider verfügt.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-145">This option assumes that the game object has a BoxCollider.</span></span> <span data-ttu-id="d6eb3-146">Es ist möglich, dies mit Nicht-BoxCollider-Objekten zu verwenden. In diesem Fall werden die Eigenschaften "Bounds" und "Local Center" viel manuell festgelegt, um die touchierbare Ebene zu konfigurieren (d.h. Bounds sollte auf einen Wert ungleich 0 (null) festgelegt werden).</span><span class="sxs-lookup"><span data-stu-id="d6eb3-146">it's possible to use this with non-BoxCollider objects, in which case the 'Bounds' and 'Local Center' properties much be manually set to configure the touchable plane (i.e. Bounds should be set to a non-zero-zero value).</span></span>

1. <span data-ttu-id="d6eb3-147">Fügen Sie auf dem GameObject, das touchierbar sein soll, eine BoxCollider- und eine [ `NearInteractionTouchable` ] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable)-Komponente hinzu.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-147">On the GameObject that should be touchable, add a BoxCollider and a [`NearInteractionTouchable`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) component.</span></span>

    1. <span data-ttu-id="d6eb3-148">Legen Sie **Ereignisse auf Receive (Empfangen)** auf *Touch* fest, wenn Sie die `IMixedRealityTouchHandler` []-Schnittstelle (xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) in Ihrem Komponentenskript unten verwenden.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-148">Set **Events to Receive** to *Touch* if using the [`IMixedRealityTouchHandler`] (xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script below.</span></span>

    1. <span data-ttu-id="d6eb3-149">Klicken Sie auf Fix bounds and Fix center **(Begrenzungen** korrigieren und **Mitte korrigieren).**</span><span class="sxs-lookup"><span data-stu-id="d6eb3-149">Click **Fix bounds** and **Fix center**</span></span>

    ![NearInteractionTouchable-Setup](../images/input/Pointers/NearInteractionTouchableSetup.gif)

1. <span data-ttu-id="d6eb3-151">Fügen Sie für dieses Objekt oder einen seiner Vorgänger eine Skriptkomponente hinzu, die implementiert. [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span><span class="sxs-lookup"><span data-stu-id="d6eb3-151">On that object or one of its ancestors, add a script component that implements the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span></span>
   <span data-ttu-id="d6eb3-152">Schnittstelle implementiert.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-152">interface.</span></span> <span data-ttu-id="d6eb3-153">Alle Vorgänger des Objekts mit dem `NearInteractionTouchable` [] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) können ebenfalls Zeigerereignisse empfangen.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-153">Any ancestor of the object with the [`NearInteractionTouchable`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) will be able to receive pointer events, as well.</span></span>

> [!NOTE]
> <span data-ttu-id="d6eb3-154">Beachten Sie in der Editor-Szenenansicht, in der *nearInteractionTouchable* GameObject ausgewählt ist, ein weißes Konturquadrat und einen Pfeil.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-154">In the editor scene view with the *NearInteractionTouchable* GameObject selected, notice a white outline square and arrow.</span></span> <span data-ttu-id="d6eb3-155">Der Pfeil zeigt auf die "Front" des touchierbaren .</span><span class="sxs-lookup"><span data-stu-id="d6eb3-155">The arrow points to the "front" of the touchable.</span></span> <span data-ttu-id="d6eb3-156">Das kollisionsfähige ist nur von dieser Richtung aus erreichbar.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-156">The collidable will only be touchable from that direction.</span></span> <span data-ttu-id="d6eb3-157">Informationen zum Touchieren eines Colliders aus allen Richtungen finden Sie im Abschnitt zu [beliebigen Collidereingaben.](#arbitrary-collider-touch)</span><span class="sxs-lookup"><span data-stu-id="d6eb3-157">To make a collider touchable from all directions, see the section on [arbitrary collider touch](#arbitrary-collider-touch).</span></span>
> <span data-ttu-id="d6eb3-158">![NearInteractionTouchable–Mos ](../images/input/Pointers/NearInteractionTouchableGizmos.png)</span><span class="sxs-lookup"><span data-stu-id="d6eb3-158">![NearInteractionTouchable Gizmos ](../images/input/Pointers/NearInteractionTouchableGizmos.png)</span></span>

### <a name="arbitrary-collider-touch"></a><span data-ttu-id="d6eb3-159">Beliebige Collider-Toucheingabe</span><span class="sxs-lookup"><span data-stu-id="d6eb3-159">Arbitrary collider touch</span></span>

<span data-ttu-id="d6eb3-160">Dies ist nützlich, um Situationen zu ermöglichen, in denen das Spielobjekt entlang seines gesamten Collidergesichts berührt werden muss.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-160">This is useful to enable situations where the game object needs to be touchable along its entire collider face.</span></span> <span data-ttu-id="d6eb3-161">Dies kann z. B. verwendet werden, um Touchinteraktionen für ein Objekt mit einem SphereCollider zu aktivieren, wobei der gesamte Collider berührt werden muss.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-161">For example, this can be used to enable touch interactions for an object with a SphereCollider, where the entire collider needs to be touchable.</span></span>

1. <span data-ttu-id="d6eb3-162">Fügen Sie auf dem GameObject, das touchierbar sein soll, einen Collider und eine `NearInteractionTouchableVolume` [] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableVolume)-Komponente hinzu.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-162">On the GameObject that should be touchable, add a collider and a [`NearInteractionTouchableVolume`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableVolume) component.</span></span>

    1. <span data-ttu-id="d6eb3-163">Legen **Sie Ereignisse** auf Receive to *Touch* fest, wenn Sie die Schnittstelle [ `IMixedRealityTouchHandler` ] (xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) in Ihrem Komponentenskript unten verwenden.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-163">Set **Events to Receive** to *Touch* if using the [`IMixedRealityTouchHandler`] (xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script below.</span></span>

1. <span data-ttu-id="d6eb3-164">Fügen Sie für dieses Objekt oder einen seiner Vorgänger eine Skriptkomponente hinzu, die implementiert. [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span><span class="sxs-lookup"><span data-stu-id="d6eb3-164">On that object or one of its ancestors, add a script component that implements the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span></span>
   <span data-ttu-id="d6eb3-165">Schnittstelle implementiert.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-165">interface.</span></span> <span data-ttu-id="d6eb3-166">Jeder Vorgänger des Objekts mit [ `NearInteractionTouchable` ] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) kann auch Zeigerereignisse empfangen.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-166">Any ancestor of the object with the [`NearInteractionTouchable`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) will be able to receive pointer events, as well.</span></span>

### <a name="unity-ui"></a><span data-ttu-id="d6eb3-167">Unity-Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="d6eb3-167">Unity UI</span></span>

1. <span data-ttu-id="d6eb3-168">Fügen Sie einen [UnityUI-Zeichenbereich](https://docs.unity3d.com/Manual/UICanvas.html) in der Szene hinzu, bzw. stellen Sie sicher.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-168">Add/ensure there is a [UnityUI canvas](https://docs.unity3d.com/Manual/UICanvas.html) in the scene.</span></span>

1. <span data-ttu-id="d6eb3-169">Fügen Sie auf dem GameObject, das berührbar sein soll, eine Komponente [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) hinzu.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-169">On the GameObject that should be touchable, add a [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) component.</span></span>  

    1. <span data-ttu-id="d6eb3-170">Legen **Sie Ereignisse auf Empfangen auf** Touch *fest,* wenn Sie die [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) -Schnittstelle in Ihrem Komponentenskript unten verwenden.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-170">Set **Events to Receive** to *Touch* if using the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script below.</span></span>

1. <span data-ttu-id="d6eb3-171">Fügen Sie für dieses Objekt oder einen seiner Vorgänger eine Skriptkomponente hinzu, die die -Schnittstelle [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) implementiert.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-171">On that object or one of its ancestors, add a script component that implements the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface.</span></span> <span data-ttu-id="d6eb3-172">Jeder Vorgänger des Objekts mit dem [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) kann auch Zeigerereignisse empfangen.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-172">Any ancestor of the object with the [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) will be able to receive pointer events as well.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d6eb3-173">Objekte verhalten sich möglicherweise nicht wie erwartet, wenn sie sich auf überlappenden Canvasobjekten befinden.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-173">Objects may not behave as expected if they are located on overlapping canvas objects.</span></span> <span data-ttu-id="d6eb3-174">Um ein konsistentes Verhalten sicherzustellen, überlappen Sie keine Canvas-Objekte in Ihrer Szene.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-174">To ensure consistent behavior, never overlap canvas objects in your scene.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d6eb3-175">In der Skriptkomponente gibt es für die Eigenschaft Zu empfangende Ereignisse `NearInteractionTouchable` zwei Optionen: *Zeiger* und *Touch*. </span><span class="sxs-lookup"><span data-stu-id="d6eb3-175">On the `NearInteractionTouchable` script component, for the property *Events to Receive* there are two options: *Pointer* and *Touch*.</span></span> <span data-ttu-id="d6eb3-176">Legen *Sie Ereignisse auf Empfangen* auf *Zeiger* fest, wenn Sie die -Schnittstelle verwenden, und legen Sie auf Touch fest, wenn Sie die Schnittstelle in Ihrem Komponentenskript verwenden, das die [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler)  [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) Eingabeereignisse antwortet/behandelt.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-176">Set *Events to Receive* to *Pointer* if using the [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) interface and set to *Touch* if using the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script that responds/handles the input events.</span></span>

#### <a name="touch-code-example"></a><span data-ttu-id="d6eb3-177">Beispiel für Touchcode</span><span class="sxs-lookup"><span data-stu-id="d6eb3-177">Touch code example</span></span>

<span data-ttu-id="d6eb3-178">Der folgende Code veranschaulicht ein MonoBehaviour-Objekt, das mit einer Variantenkomponente an ein GameObject angefügt werden kann und auf [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) Toucheingabeereignisse reagieren kann.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-178">The code below demonstrates a MonoBehaviour that can be attached to a GameObject with a [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) variant component and respond to touch input events.</span></span>

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

## <a name="near-interaction-script-examples"></a><span data-ttu-id="d6eb3-179">Beispiele für Skripts für die Nahinteraktion</span><span class="sxs-lookup"><span data-stu-id="d6eb3-179">Near interaction script examples</span></span>

### <a name="touch-events"></a><span data-ttu-id="d6eb3-180">Berührungsereignisse</span><span class="sxs-lookup"><span data-stu-id="d6eb3-180">Touch events</span></span>

<span data-ttu-id="d6eb3-181">In diesem Beispiel wird ein Würfel erstellt, er ist berührbar und ändert die Farbe bei der Berührung.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-181">This example creates a cube, makes it touchable, and changes color on touch.</span></span>

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

### <a name="grab-events"></a><span data-ttu-id="d6eb3-182">Grab-Ereignisse</span><span class="sxs-lookup"><span data-stu-id="d6eb3-182">Grab events</span></span>

<span data-ttu-id="d6eb3-183">Das folgende Beispiel zeigt, wie ein GameObject gezogen werden kann.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-183">The below example shows how to make a GameObject draggable.</span></span> <span data-ttu-id="d6eb3-184">Es wird davon ausgegangen, dass das Spielobjekt über einen Collider verfügt.</span><span class="sxs-lookup"><span data-stu-id="d6eb3-184">Assumes that the game object has a collider on it.</span></span>

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

## <a name="useful-apis"></a><span data-ttu-id="d6eb3-185">Nützliche APIs</span><span class="sxs-lookup"><span data-stu-id="d6eb3-185">Useful APIs</span></span>

* [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable)
* [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable)
* [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI)
* [`NearInteractionTouchableVolume`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableVolume)
* [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
* [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler)

## <a name="see-also"></a><span data-ttu-id="d6eb3-186">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d6eb3-186">See also</span></span>

* [<span data-ttu-id="d6eb3-187">Übersicht über die Eingabe</span><span class="sxs-lookup"><span data-stu-id="d6eb3-187">Input Overview</span></span>](overview.md)
* [<span data-ttu-id="d6eb3-188">Zeiger</span><span class="sxs-lookup"><span data-stu-id="d6eb3-188">Pointers</span></span>](pointers.md)
* [<span data-ttu-id="d6eb3-189">Eingabeereignisse</span><span class="sxs-lookup"><span data-stu-id="d6eb3-189">Input Events</span></span>](input-events.md)
