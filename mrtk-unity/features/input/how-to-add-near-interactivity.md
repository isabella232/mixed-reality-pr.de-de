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
# <a name="how-to-add-near-interaction-in-mrtk"></a>Hinzufügen einer nahezuen Interaktion in MRTK

Nahinteraktionen kommen in Form von Berührungen und Greifern vor. Touch- und Greifereignisse werden vom [PokePointer](pointers.md#pokepointer) bzw. [SpherePointer](pointers.md#spherepointer)als Zeigerereignisse ausgelöst.

Drei wichtige Schritte sind erforderlich, um auf Toucheingabe- und/oder Greifeingabeereignisse für ein bestimmtes GameObject zu lauschen.

1. Stellen Sie sicher, dass der relevante Zeiger im [MRTK-Hauptkonfigurationsprofil registriert ist.](../../configuration/mixed-reality-configuration-guide.md)
1. Stellen Sie sicher, dass das gewünschte GameObject über die entsprechende [Greif-](#add-grab-interactions) oder [Touchskriptkomponente](#add-touch-interactions) und [`Unity Collider`](https://docs.unity3d.com/ScriptReference/Collider.html) verfügt.
1. Implementieren Sie eine Eingabehandlerschnittstelle für ein angefügtes Skript für das gewünschte GameObject, um auf die Greif- [oder](#grab-code-example) [Touchereignisse zu](#touch-code-example) lauschen.

## <a name="add-grab-interactions"></a>Hinzufügen von Greifinteraktionen

1. Stellen Sie [sicher, dass ein SpherePointer](pointers.md#spherepointer) im *MRTK-Zeigerprofil registriert ist.*

    Das MRTK-Standardprofil und das Standardprofil HoloLens 2 bereits ein *SpherePointer-Profil.* Sie können bestätigen, dass ein SpherePointer erstellt wird, indem Sie das MRTK-Konfigurationsprofil auswählen und zu  >  **Eingabezeigerzeiger-Zeigeroptionen**  >  **navigieren.** Das `GrabPointer` Standard-Prefab (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) sollte mit dem *Controllertyp* *"Articulated Hand"* aufgeführt werden. Ein benutzerdefiniertes Prefab kann verwendet werden, solange es die -Klasse [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer) implementiert.

    ![Beispiel für ein Greifzeigerprofil](../images/input/Pointers/GrabPointer_MRTKProfile.png)

    Der Standardmäßige Greifzeiger fragt objekte in der Nähe in einem Kegel um den Greifpunkt ab, um der Standardmäßigen Hololens 2-Schnittstelle zu passen.

    ![Conical Grab-Zeiger](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

1. Fügen Sie auf dem GameObject, das ziehbar sein soll, einen sowie [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) einen Collider hinzu.

    Stellen Sie sicher, dass sich die Ebene des GameObject auf einer greifbaren Ebene befindet. Standardmäßig sind alle Ebenen außer *Spatial Awareness und* Ignore *Raycasts* greifbar. Sehen Sie sich die Greifebenenmasken *in* Ihrem GrabPointer-Prefab an, um zu sehen, welche Ebenen *greifbar* sind.

1. Fügen Sie auf dem GameObject oder einem seiner Vorgänger eine Skriptkomponente hinzu, die die -Schnittstelle [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) implementiert. Jeder Vorgänger des Objekts mit dem [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) kann auch Zeigerereignisse empfangen.

### <a name="grab-code-example"></a>Beispiel für "Code greifen"

Im Folgenden finden Sie ein Skript, das aus druckt, wenn es sich bei einem Ereignis um eine Berührung oder einen Greif handelt. In der *relevanten IMixedRealityPointerHandler-Schnittstellenfunktion* können Sie den Typ des Zeigers betrachten, der dieses Ereignis über [`MixedRealityPointerEventData`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerEventData) auslöst. Wenn der Zeiger ein *SpherePointer* ist, ist die Interaktion ein Greif.

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

Der Prozess zum Hinzufügen von Touchinteraktionen zu UnityUI-Elementen ist anders als bei 3D-GameObjects. Sie können zum Aktivieren von Unity-Benutzeroberflächenkomponenten mit dem folgenden Abschnitt( Unity-Benutzeroberfläche) springen.

Stellen **Sie für** beide Typen von UX-Elementen jedoch sicher, dass ein [PokePointer](pointers.md#pokepointer) im *MRTK-Zeigerprofil registriert ist.*

Das MRTK-Standardprofil und das Standardprofil HoloLens 2 bereits *ein PokePointer-Profil.* Sie können bestätigen, dass ein PokePointer erstellt wird, indem Sie das MRTK-Konfigurationsprofil auswählen und zu  >  **Eingabezeigerzeigeroptionen**  >  **navigieren.** Das Standard `PokePointer` prefab (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) sollte mit dem *Controllertyp* *"Articulated Hand"* aufgeführt werden. Ein benutzerdefiniertes Prefab kann verwendet werden, solange es die -Klasse [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) implementiert.

![Poke-Zeigerprofilbeispiel](../images/input/Pointers/PokePointer_MRTKProfile.png)

### <a name="3d-gameobjects"></a>3D-GameObjects

Es gibt zwei verschiedene Möglichkeiten, 3D GameObjects Touchinteraktionen hinzufügen zu können, je nachdem, ob Ihr 3D-Objekt nur eine einzige berührbare Ebene haben soll, oder ob es auf der Grundlage des gesamten Colliders berührbar sein sollte.
Die erste Möglichkeit besteht in der Regel bei Objekten mit BoxColliders, bei denen nur ein einzelnes Gesicht des Colliders auf Berührungsereignisse reagieren soll. Die andere ist für Objekte, die je nach Collider aus beliebiger Richtung erreichbar sein müssen.

### <a name="single-face-touch"></a>Toucheingabe mit einzelnem Gesicht

Dies ist nützlich, um Situationen zu ermöglichen, in denen nur ein einzelnes Gesicht berührt werden muss. Bei dieser Option wird davon ausgegangen, dass das Spielobjekt über einen BoxCollider verfügt. Es ist möglich, dies mit Nicht-BoxCollider-Objekten zu verwenden. In diesem Fall werden die Eigenschaften "Bounds" und "Local Center" viel manuell festgelegt, um die touchierbare Ebene zu konfigurieren (d.h. Bounds sollte auf einen Wert ungleich 0 (null) festgelegt werden).

1. Fügen Sie auf dem GameObject, das touchierbar sein soll, eine BoxCollider- und eine [ `NearInteractionTouchable` ] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable)-Komponente hinzu.

    1. Legen Sie **Ereignisse auf Receive (Empfangen)** auf *Touch* fest, wenn Sie die `IMixedRealityTouchHandler` []-Schnittstelle (xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) in Ihrem Komponentenskript unten verwenden.

    1. Klicken Sie auf Fix bounds and Fix center **(Begrenzungen** korrigieren und **Mitte korrigieren).**

    ![NearInteractionTouchable-Setup](../images/input/Pointers/NearInteractionTouchableSetup.gif)

1. Fügen Sie für dieses Objekt oder einen seiner Vorgänger eine Skriptkomponente hinzu, die implementiert. [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
   Schnittstelle implementiert. Alle Vorgänger des Objekts mit dem `NearInteractionTouchable` [] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) können ebenfalls Zeigerereignisse empfangen.

> [!NOTE]
> Beachten Sie in der Editor-Szenenansicht, in der *nearInteractionTouchable* GameObject ausgewählt ist, ein weißes Konturquadrat und einen Pfeil. Der Pfeil zeigt auf die "Front" des touchierbaren . Das kollisionsfähige ist nur von dieser Richtung aus erreichbar. Informationen zum Touchieren eines Colliders aus allen Richtungen finden Sie im Abschnitt zu [beliebigen Collidereingaben.](#arbitrary-collider-touch)
> ![NearInteractionTouchable–Mos ](../images/input/Pointers/NearInteractionTouchableGizmos.png)

### <a name="arbitrary-collider-touch"></a>Beliebige Collider-Toucheingabe

Dies ist nützlich, um Situationen zu ermöglichen, in denen das Spielobjekt entlang seines gesamten Collidergesichts berührt werden muss. Dies kann z. B. verwendet werden, um Touchinteraktionen für ein Objekt mit einem SphereCollider zu aktivieren, wobei der gesamte Collider berührt werden muss.

1. Fügen Sie auf dem GameObject, das touchierbar sein soll, einen Collider und eine `NearInteractionTouchableVolume` [] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableVolume)-Komponente hinzu.

    1. Legen **Sie Ereignisse** auf Receive to *Touch* fest, wenn Sie die Schnittstelle [ `IMixedRealityTouchHandler` ] (xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) in Ihrem Komponentenskript unten verwenden.

1. Fügen Sie für dieses Objekt oder einen seiner Vorgänger eine Skriptkomponente hinzu, die implementiert. [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
   Schnittstelle implementiert. Jeder Vorgänger des Objekts mit [ `NearInteractionTouchable` ] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) kann auch Zeigerereignisse empfangen.

### <a name="unity-ui"></a>Unity-Benutzeroberfläche

1. Fügen Sie einen [UnityUI-Zeichenbereich](https://docs.unity3d.com/Manual/UICanvas.html) in der Szene hinzu, bzw. stellen Sie sicher.

1. Fügen Sie auf dem GameObject, das berührbar sein soll, eine Komponente [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) hinzu.  

    1. Legen **Sie Ereignisse auf Empfangen auf** Touch *fest,* wenn Sie die [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) -Schnittstelle in Ihrem Komponentenskript unten verwenden.

1. Fügen Sie für dieses Objekt oder einen seiner Vorgänger eine Skriptkomponente hinzu, die die -Schnittstelle [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) implementiert. Jeder Vorgänger des Objekts mit dem [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) kann auch Zeigerereignisse empfangen.

> [!IMPORTANT]
> Objekte verhalten sich möglicherweise nicht wie erwartet, wenn sie sich auf überlappenden Canvasobjekten befinden. Um ein konsistentes Verhalten sicherzustellen, überlappen Sie keine Canvas-Objekte in Ihrer Szene.

> [!IMPORTANT]
> In der Skriptkomponente gibt es für die Eigenschaft Zu empfangende Ereignisse `NearInteractionTouchable` zwei Optionen: *Zeiger* und *Touch*.  Legen *Sie Ereignisse auf Empfangen* auf *Zeiger* fest, wenn Sie die -Schnittstelle verwenden, und legen Sie auf Touch fest, wenn Sie die Schnittstelle in Ihrem Komponentenskript verwenden, das die [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler)  [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) Eingabeereignisse antwortet/behandelt.

#### <a name="touch-code-example"></a>Beispiel für Touchcode

Der folgende Code veranschaulicht ein MonoBehaviour-Objekt, das mit einer Variantenkomponente an ein GameObject angefügt werden kann und auf [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) Toucheingabeereignisse reagieren kann.

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

## <a name="near-interaction-script-examples"></a>Beispiele für Skripts für die Nahinteraktion

### <a name="touch-events"></a>Berührungsereignisse

In diesem Beispiel wird ein Würfel erstellt, er ist berührbar und ändert die Farbe bei der Berührung.

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

Das folgende Beispiel zeigt, wie ein GameObject gezogen werden kann. Es wird davon ausgegangen, dass das Spielobjekt über einen Collider verfügt.

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

## <a name="see-also"></a>Weitere Informationen

* [Übersicht über die Eingabe](overview.md)
* [Zeiger](pointers.md)
* [Eingabeereignisse](input-events.md)
