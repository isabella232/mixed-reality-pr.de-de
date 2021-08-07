---
title: Hinzufügen von nähebezogener Interaktivität
description: Dokumentation zur nahezuen Interaktion in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Near Interaction,
ms.openlocfilehash: 174623ebf340e800848c15e22dc2299aaf997b484a1329d67c28540acd79515a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212596"
---
# <a name="how-to-add-near-interactivity"></a>Hinzufügen von nähebezogener Interaktivität

Nahinteraktionen erfolgen in Form von Berührungen und Greifen. Berührungs- und Tastenereignisse werden als Zeigerereignisse von [Der PointePointer](pointers.md#pokepointer) bzw. [SpherePointer](pointers.md#spherepointer)ausgelöst.

Drei wichtige Schritte sind erforderlich, um auf Touch- und/oder Eingabeereignisse auf einem bestimmten GameObject zu lauschen.

1. Stellen Sie sicher, dass der relevante Zeiger im [MRTK-Hauptkonfigurationsprofil](../../configuration/mixed-reality-configuration-guide.md)registriert ist.
1. Stellen Sie sicher, dass das gewünschte GameObject über die entsprechende [Grab-](#add-grab-interactions) oder [Touchskriptkomponente](#add-touch-interactions) und [`Unity Collider`](https://docs.unity3d.com/ScriptReference/Collider.html) verfügt.
1. Implementieren Sie eine Eingabehandlerschnittstelle für ein angefügtes Skript an das gewünschte GameObject, um auf die [Zieh-](#grab-code-example) oder [Touchereignisse](#touch-code-example) zu lauschen.

## <a name="add-grab-interactions"></a>Hinzufügen von Grabinteraktionen

1. Stellen Sie sicher, dass ein [SpherePointer](pointers.md#spherepointer) im *MRTK-Zeigerprofil* registriert ist.

    Das MRTK-Standardprofil und das Standardprofil HoloLens 2 enthalten bereits ein *SpherePointer-Profil.* Sie können bestätigen, dass ein SpherePointer erstellt wird, indem Sie das MRTK-Konfigurationsprofil auswählen und zu  >  **Eingabezeigerzeigeroptionen**  >  navigieren. Das `GrabPointer` Standard-Prefab (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) sollte mit dem *Controllertyp* *"Artikulierte Hand"* aufgelistet werden. Ein benutzerdefiniertes Prefab kann verwendet werden, solange es die [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer) -Klasse implementiert.

    ![Beispiel für ein Grab-Zeigerprofil](../images/input/Pointers/GrabPointer_MRTKProfile.png)

    Der Standard-Greifzeiger fragt objekte in der Nähe in einem Kegel um den Greifenpunkt ab, um mit der Hololens 2-Standardschnittstelle zu übereinstimmen.

    ![Konische Klammerzeiger](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

1. Fügen Sie auf dem GameObject, das ziehbar sein soll, sowohl einen [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) als auch einen Collider hinzu.

    Stellen Sie sicher, dass sich die Ebene des GameObject auf einer gierbaren Ebene befindet. Standardmäßig sind alle Ebenen außer *räumlicher Wahrnehmung* und *Ignore Raycasts* greifend. Überprüfen Sie die *Grab Layer Masks* in Ihrem *GrabPointer-Prefab,* um zu überprüfen, welche Ebenen gepackt werden können.

1. Fügen Sie auf dem GameObject oder einem seiner Vorgänger eine Skriptkomponente hinzu, die die [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) -Schnittstelle implementiert. Jeder Vorgänger des -Objekts mit dem [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) kann auch Zeigerereignisse empfangen.

### <a name="grab-code-example"></a>Beispiel für Den Code greifen

Im Folgenden finden Sie ein Skript, das gedruckt wird, wenn es sich bei einem Ereignis um eine Toucheingabe oder ein Greifen handelt. In der relevanten *IMixedRealityPointerHandler-Schnittstellenfunktion* kann der Typ des Zeigers betrachtet werden, der dieses Ereignis über den [`MixedRealityPointerEventData`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerEventData) auslöst. Wenn der Zeiger ein *SpherePointer* ist, ist die Interaktion ein Greifen.

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

## <a name="add-touch-interactions"></a>Hinzufügen von Touchinteraktionen

Der Prozess zum Hinzufügen von Touchinteraktionen für UnityUI-Elemente unterscheidet sich von der Vorgehensweise für 3D-GameObjects von Vane. Sie können mit dem folgenden Abschnitt( *Unity UI*) zum Aktivieren von Komponenten der Unity-Benutzeroberfläche springen.

Stellen Sie jedoch für **beide** Arten von UX-Elementen sicher, dass ein [PointerePointer](pointers.md#pokepointer) im *MRTK-Zeigerprofil* registriert ist.

Das MRTK-Standardprofil und das Standardprofil für HoloLens 2 enthalten bereits einen *Derpointer*. Sie können bestätigen, dass ein PointerePointer erstellt wird, indem Sie das MRTK-Konfigurationsprofil auswählen und zu  >  **Eingabezeigerzeigeroptionen**  >  navigieren. Das `PokePointer` Standard-Prefab (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) sollte mit dem *Controllertyp* *"Artikulierte Hand"* aufgelistet werden. Ein benutzerdefiniertes Prefab kann verwendet werden, solange es die [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) -Klasse implementiert.

![Beispiel für Zeigerprofil](../images/input/Pointers/PokePointer_MRTKProfile.png)

### <a name="3d-gameobjects"></a>3D GameObjects

Es gibt zwei verschiedene Möglichkeiten, 3D-GameObjects Touchinteraktionen hinzuzufügen, je nachdem, ob Ihr 3D-Objekt nur eine einzelne touchierbare Ebene haben soll, oder ob es basierend auf seinem gesamten Collider touchierbar sein soll.
Die erste Möglichkeit besteht in der Regel in Objekten mit BoxColliders, bei denen nur ein einzelnes Gesicht des Colliders auf Berührungsereignisse reagieren soll. Die andere ist für Objekte, die je nach Collider aus beliebiger Richtung erreichbar sein müssen.

### <a name="single-face-touch"></a>Toucheingabe mit einzelnem Gesicht

Dies ist nützlich, um Situationen zu ermöglichen, in denen nur ein einzelnes Gesicht berührt werden muss. Bei dieser Option wird davon ausgegangen, dass das Spielobjekt über einen BoxCollider verfügt. Es ist möglich, dies mit Nicht-BoxCollider-Objekten zu verwenden. In diesem Fall werden die Eigenschaften "Bounds" und "Local Center" viel manuell festgelegt, um die touchierbare Ebene zu konfigurieren (d.h. Bounds sollte auf einen Wert ungleich 0 (null) festgelegt werden).

1. Fügen Sie auf dem GameObject, das touchierbar sein soll, eine BoxCollider- und eine [ `NearInteractionTouchable` ] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable)-Komponente hinzu.

    1. Legen Sie **Ereignisse auf Receive (Empfangen)** auf *Touch* fest, wenn Sie die `IMixedRealityTouchHandler` []-Schnittstelle (xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) in Ihrem Komponentenskript unten verwenden.

    1. Klicken Sie auf Fix bounds and Fix center **(Begrenzungen** korrigieren und **Mitte korrigieren).**

    ![NearInteractionTouchable-Setup](../images/input/Pointers/NearInteractionTouchableSetup.gif)

1. Fügen Sie für dieses Objekt oder einen seiner Vorgänger eine Skriptkomponente hinzu, die implementiert. [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
   Schnittstelle implementiert. Alle Vorgänger des Objekts mit dem `NearInteractionTouchable` [] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) können ebenfalls Zeigerereignisse empfangen.

> [!NOTE]
> Beachten Sie in der Szenenansicht des Editors, in der *nearInteractionTouchable* GameObject ausgewählt ist, ein weißes Konturquadrat und einen Pfeil. Der Pfeil zeigt auf die "Front" des touchierbaren . Das kollisionsfähige ist nur von dieser Richtung aus erreichbar. Informationen zum Touchieren eines Colliders aus allen Richtungen finden Sie im Abschnitt zu [beliebigen Collidereingaben.](#arbitrary-collider-touch)
> ![NearInteractionTouchable–Mos ](../images/input/Pointers/NearInteractionTouchableGizmos.png)

### <a name="arbitrary-collider-touch"></a>Beliebige Collider-Toucheingabe

Dies ist nützlich, um Situationen zu ermöglichen, in denen das Spielobjekt entlang seines gesamten Collidergesichts berührt werden muss. Dies kann z. B. verwendet werden, um Touchinteraktionen für ein Objekt mit einem SphereCollider zu aktivieren, wobei der gesamte Collider berührt werden muss.

1. Fügen Sie auf dem GameObject, das touchierbar sein soll, einen Collider und eine `NearInteractionTouchableVolume` [] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableVolume)-Komponente hinzu.

    1. Legen Sie **Ereignisse auf Receive (Empfangen)** auf *Touch* fest, wenn Sie die `IMixedRealityTouchHandler` []-Schnittstelle (xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) in Ihrem Komponentenskript unten verwenden.

1. Fügen Sie für dieses Objekt oder einen seiner Vorgänger eine Skriptkomponente hinzu, die implementiert. [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
   Schnittstelle implementiert. Alle Vorgänger des Objekts mit dem `NearInteractionTouchable` [] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) können ebenfalls Zeigerereignisse empfangen.

### <a name="unity-ui"></a>Unity-Benutzeroberfläche

1. Fügen Sie einen [UnityUI-Zeichenbereich](https://docs.unity3d.com/Manual/UICanvas.html) in der Szene hinzu, oder stellen Sie sicher, dass er vorhanden ist.

1. Fügen Sie auf dem GameObject, das touchierbar sein soll, eine [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) -Komponente hinzu.  

    1. Legen Sie **Ereignisse auf Receive (Empfangen)** auf *Touch* fest, wenn Sie die [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) -Schnittstelle in Ihrem Komponentenskript unten verwenden.

1. Fügen Sie für dieses Objekt oder einen seiner Vorgänger eine Skriptkomponente hinzu, die die [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) -Schnittstelle implementiert. Jeder Vorgänger des -Objekts mit dem [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) kann auch Zeigerereignisse empfangen.

> [!IMPORTANT]
> Objekte verhalten sich möglicherweise nicht wie erwartet, wenn sie sich auf überlappenden Canvasobjekten befinden. Um ein konsistentes Verhalten sicherzustellen, überlappen Sie canvas-Objekte in Ihrer Szene niemals.

> [!IMPORTANT]
> Für die Eigenschaft Ereignisse, die empfangen werden sollen, stehen in der `NearInteractionTouchable` Skriptkomponente zwei Optionen zur Verfügung: *Zeiger* und *Touch.*  Legen Sie *Ereignisse auf Empfangen* auf *Zeiger* fest, wenn Sie die [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) -Schnittstelle verwenden, und legen Sie auf *Touch* fest, wenn Sie die Schnittstelle in [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) Ihrem Komponentenskript verwenden, das auf die Eingabeereignisse reagiert bzw. behandelt.

#### <a name="touch-code-example"></a>Beispiel für Touchcode

Der folgende Code veranschaulicht ein MonoBehaviour-Element, das mit einer Variant-Komponente an ein GameObject angefügt werden kann [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) und auf Toucheingabeereignisse reagiert.

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

## <a name="near-interaction-script-examples"></a>Beispiele für Skripts für die nahe Interaktion

### <a name="touch-events"></a>Berührungsereignisse

In diesem Beispiel wird ein Cube erstellt, touchierbar und die Farbe bei der Berührung geändert.

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

### <a name="grab-events"></a>Grab-Ereignisse

Das folgende Beispiel zeigt, wie Ein GameObject gezogen werden kann. Es wird davon ausgegangen, dass das Spielobjekt über einen Collider verfügt.

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

## <a name="useful-apis"></a>Nützliche APIs

* [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable)
* [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable)
* [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI)
* [`NearInteractionTouchableVolume`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableVolume)
* [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
* [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler)

## <a name="see-also"></a>Siehe auch

* [Übersicht über die Eingabe](overview.md)
* [Zeiger](pointers.md)
* [Eingabeereignisse](input-events.md)
