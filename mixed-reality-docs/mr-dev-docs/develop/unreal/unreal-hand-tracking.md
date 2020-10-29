---
title: Handtracking in Unreal
description: Erläutert die Verwendung der Hand Verfolgung in Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, Hand Verfolgung, Unreal, Unreal Engine 4, UE4, hololens, hololens 2, Mixed Reality, Entwicklung, Features, Dokumentation, Anleitungen, holograms, Spieleentwicklung
ms.openlocfilehash: 5bc120f802c2160282befd1ce6cb8025be21cbaa
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2020
ms.locfileid: "91678962"
---
# <a name="hand-tracking-in-unreal"></a>Handtracking in Unreal

## <a name="overview"></a>Übersicht

Das Hand Verfolgungssystem verwendet die Palmen und Finger der Person als Eingabe. Sie können die Position und Drehung jedes Fingers, den gesamten Palmen und sogar Handgesten für die Verwendung in Ihrem Code erhalten. 

## <a name="hand-pose"></a>Hand darstellen

Hand darstellen ermöglicht Ihnen, die Hände und Finger des aktiven Benutzers zu verfolgen und als Eingabe zu verwenden, auf die Sie über Blueprints und C++ zugreifen können. Weitere technische Details finden Sie in der [Windows. perception. People. handpose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) -API von Unreal. Die Unreal-API sendet die Daten als Koordinatensystem, wobei Ticks mit der Unreal-Engine synchronisiert werden.

### <a name="understanding-the-bone-hierarchy"></a>Grundlegendes zur Knochen Hierarchie

Die `EWMRHandKeypoint` -Enumeration beschreibt die Knochen Hierarchie der Hand. Sie finden jeden Hand-keypoint, der in ihren Blaupausen aufgeführt ist:

![Hand-keypoint-BP](images/hand-keypoint-bp.png)

Die vollständige C++-Aufzählung ist im folgenden aufgeführt:
```cpp
enum class EWMRHandKeypoint : uint8
{
    Palm,
    Wrist,
    ThumbMetacarpal,
    ThumbProximal,
    ThumbDistal,
    ThumbTip,
    IndexMetacarpal,
    IndexProximal,
    IndexIntermediate,
    IndexDistal,
    IndexTip,
    MiddleMetacarpal,
    MiddleProximal,
    MiddleIntermediate,
    MiddleDistal,
    MiddleTip,
    RingMetacarpal,
    RingProximal,
    RingIntermediate,
    RingDistal,
    RingTip,
    LittleMetacarpal,
    LittleProximal,
    LittleIntermediate,
    LittleDistal,
    LittleTip
};
```

Sie können die numerischen Werte für jeden enumerationsfall in der Tabelle " [Windows. perception. People. handjointkind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) " finden. In der folgenden Abbildung ist das gesamte Hand Layout mit passenden Enumeration-Fällen dargestellt:

![Hand Gerüst](../native/images/hand-skeleton.png)
 
### <a name="supporting-hand-tracking"></a>Unterstützende Hand Verfolgung

Sie können die Hand Verfolgung in Blaupausen verwenden, indem Sie die Hand Verfolgung von Hand Nachverfolgung **> Windows Mixed Reality** **Hinzufügen** :

![Hand Tracking-BP](images/unreal/hand-tracking-bp.png)

Diese Funktion gibt zurück, `true` Wenn die Hand Verfolgung auf dem Gerät unterstützt wird und die `false` Hand Nachverfolgung nicht verfügbar ist.

![Unterstützt die Hand Überwachung von BP](images/unreal/supports-hand-tracking-bp.png)

C++: 

Schließen Sie `WindowsMixedRealityHandTrackingFunctionLibrary.h` ein.

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a>Erhalten von Hand Nachverfolgung
Mit **gethandjointtransform** können Sie räumliche Daten von Hand zurückgeben. Die Daten aktualisieren jeden Frame, aber wenn Sie sich innerhalb eines Frames befinden, werden die zurückgegebenen Werte zwischengespeichert. Es wird aus Leistungsgründen nicht empfohlen, in dieser Funktion eine hohe Logik zu haben. 

![Hand Gelenk Transformation](images/unreal/get-hand-joint-transform.png)
 
C++:
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

Funktionsparameter Aufschlüsselung:

* **Hand** – eine ist die linke oder Rechte Seite des Benutzers.
* **Keypoint** – der Knochen der Hand. 
* **Transformation** – Koordinaten und Ausrichtung der Basis von Bone. Sie können die Basis des nächsten Knochens anfordern, um die Transformations Daten für das Ende eines Knochens zu erhalten. Ein spezieller Tip-Bone gibt das Ende der distal-Tabelle an. 
* **RADIUS** – Radius der Basis des Knochens.
* **Rückgabewert** – true, wenn der Rahmen dieses Frames nachverfolgt wird, false, wenn der Knochen nicht nachverfolgt wird.

## <a name="hand-live-link-animation"></a>Live Link Animation Hand
Hand stellen werden der Animation mithilfe des [Live Link-Plug](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html)-ins ausgesetzt.

Wenn die Windows Mixed Reality-und Live Link-Plug-ins aktiviert sind: 
1. Wählen Sie **Window > Live Link** aus, um das Fenster Live Link-Editor zu öffnen. 
2. Klicken Sie auf **Quelle** , und aktivieren Sie **Windows Mixed Reality-Hand Verfolgungs Quelle**

![Live Link Quelle](images/unreal/live-link-source.png)
 
Nachdem Sie die Quelle aktiviert und ein Animations Objekt geöffnet haben, erweitern Sie den Abschnitt **Animation** auf der Registerkarte **Vorschau Szene** , und sehen Sie sich auch weitere Optionen an (die Details befinden sich in der Live Link Dokumentation von Unreal, da sich das Plug-in in der Beta Version befindet).

![Live Link Animation](images/unreal/live-link-animation.png)
 
Die Hand Animations Hierarchie ist identisch mit der in `EWMRHandKeypoint` . Die Animation kann mithilfe von **windowsmixedrealityhandtrackinglebinkremapasset** neu zugewiesen werden:

![Live Link Animation 2](images/unreal/live-link-animation2.png)
 
Sie kann auch im Editor untergeordnet werden:

![Live Link Neuzuordnung](images/unreal/live-link-remap.png)
 
## <a name="accessing-hand-mesh-data"></a>Zugreifen auf Hand Mesh-Daten

![Hand Netz](images/unreal/hand-mesh.png)

Bevor Sie auf Hand Netz Daten zugreifen können, müssen Sie folgende Schritte ausführen:
- Wählen Sie das Objekt " **arsessionconfig** " aus, erweitern Sie die Einstellungen für " **AR Settings-> World Mapping** ", und aktivieren Sie die Option **Mesh-Daten aus der** 

Unten sind die standardmesh-Parameter aufgeführt:

1.  Netzdaten für Okklusion verwenden
2.  Konflikt für Mesh-Daten generieren
3.  Navigations Gitter für Mesh-Daten generieren
4.  Gitternetz Daten in Wireframe Renderingparameter – Debug

Diese Parameterwerte werden als Gitter-und Hand Netz Standardwerte verwendet. Sie können Sie jederzeit in Blaupausen oder Code für ein beliebiges Mesh ändern.

### <a name="c-api-reference"></a>C++-API-Referenz 
Verwenden `EEARObjectClassification` Sie, um Hand gitterwerte in allen nachverfolgbare-Objekten zu suchen.
```cpp
enum class EARObjectClassification : uint8
{
    // Other types 
    HandMesh,
};
```

Die folgenden Delegaten werden aufgerufen, wenn das System ein ausführbares Objekt erkennt, einschließlich eines Hand Netzes. 

```cpp
class FARSupportInterface 
{
    public:
    // Other params 
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableAdded)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableUpdated)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableRemoved)
};
```

Stellen Sie sicher, dass die Delegathandler der folgenden Funktions Signatur folgen:

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

Sie können über die folgenden Schritte auf Mesh-Daten zugreifen  `UARTrackedGeometry::GetUnderlyingMesh` :

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```


### <a name="blueprint-api-reference"></a>Referenz zur Blueprint-API

Um mit Hand-Meshes in Blaupausen arbeiten zu können:
1. Hinzufügen einer **artrackablenotify** -Komponente zu einem Blueprint-Actor

![Meldung zu einem darstellbaren Element](images/unreal/ar-trackable-notify.png)
 
2. Wechseln Sie zum **Detail** Panel, und erweitern Sie den Abschnitt **Ereignisse** . 

![Artrackable Benachrichtigen 2](images/unreal/ar-trackable-notify2.png)
 
3. Überschreiben Sie beim Hinzufügen/Aktualisieren/Entfernen der überwachten Geometrie mit den folgenden Knoten im Ereignis Diagramm:

![Bei der über sichtbaren Benachrichtigung](images/unreal/on-artrackable-notify.png)
 
## <a name="hand-rays"></a>Hand Strahlen

Sie können einen Hand Strahl als Zeigegerät sowohl in C++ als auch in Blueprints verwenden, das die [Windows. UI. Input. Spatial. spatialpointerinteraktionsourcepose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose) -API verfügbar macht.

Es ist wichtig zu erwähnen, dass die Ergebnisse aller Funktionen jeden Frame ändern, dass Sie alle aufgerufen werden. Weitere Informationen zu reinen und impformen oder Aufruf baren Funktionen finden Sie in der Blueprint-Benutzer-GUID für [Funktionen](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure) .

Um Hand Abdrücke in Blaupausen zu verwenden, suchen Sie nach den Aktionen unter **Windows Mixed Reality HMD** :

![Hand Strahlen-BP](images/unreal/hand-rays-bp.png)
 
Wenn Sie in C++ auf Sie zugreifen möchten, schließen Sie am `WindowsMixedRealityFunctionLibrary.h` Anfang der aufrufenden Codedatei ein.

### <a name="enum"></a>Enumeration
Sie haben auch Zugriff auf die Eingabe Fälle unter **ehmdinputcontrollerbuttons** , die in Blaupausen verwendet werden können:

![Eingabe Controller-Schaltflächen](images/unreal/input-controller-buttons.png)

Verwenden Sie für den Zugriff in C++ die `EHMDInputControllerButtons` Enumerationsklasse:
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```

Im folgenden finden Sie eine Aufschlüsselung der beiden anwendbaren Aufzählungs Fälle:
* **Select** -User hat Select-Ereignis ausgelöst. 
    * Das Ereignis kann in hololens 2 per Air-Tap, Gaze und Commit oder durch "Select" mit aktivierter [Spracheingabe](unreal-voice-input.md) ausgelöst werden. 
* Das von Benutzern ausgelöste Ereignis **zum Erfassen von** Ereignissen. 
    * Dieses Ereignis kann in hololens 2 ausgelöst werden, indem die Finger des Benutzers in einem Hologram geschlossen werden. 

Sie können auf den Überwachungs Status Ihres Hand Netzes in C++ über die unten gezeigte Aufzählung zugreifen `EHMDTrackingStatus` :

```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```

Im folgenden finden Sie eine Aufschlüsselung der beiden anwendbaren Aufzählungs Fälle:
* **Notverfolgt** – die Hand ist nicht sichtbar.
* Nach **verfolgte** –: die Hand ist vollständig nachverfolgt.

### <a name="struct"></a>Struktur
Die pointerposeinfo-Struktur kann Ihnen Informationen zu den folgenden Daten liefern:
* **Ursprung** – Ursprung der Hand
* **Richtung** – Richtung der Hand
* **Up** – Up Vector of the Hand
* **Ausrichtung** – Ausrichtung Quaternion 
* **Überwachungs Status** – aktueller Überwachungs Status

Sie können auf diese über Blaupausen zugreifen, wie unten dargestellt:

![Zeiger stellen Informationen BP dar](images/unreal/pointer-pose-info-bp.png)

Oder mit C++:

```cpp
struct FPointerPoseInfo
{
    FVector Origin;
    FVector Direction;
    FVector Up;
    FQuat Orientation;
    EHMDTrackingStatus TrackingStatus;
};
```

### <a name="functions"></a>Functions

Alle unten aufgeführten Funktionen können für jeden Frame aufgerufen werden, der eine kontinuierliche Überwachung ermöglicht. 

1. **Get Pointer Pose Info** gibt alle Informationen über die Richtung des Hand Gers im aktuellen Frame zurück. 

Karte

![Informationen zum Darstellen von Zeigern](images/unreal/get-pointer-pose-info.png)

C++: 
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. **Ist** "-Wert" gibt "true" zurück, wenn die Hand im aktuellen Frame erfasst wird.

Karte

![Erfasste BP](images/unreal/is-grasped-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```
 
3. **Ist SELECT gedrückt** gibt true zurück, wenn der Benutzer SELECT im aktuellen Frame ausgelöst hat.

Karte

![Ist SELECT-Taste für BP](images/unreal/is-select-pressed-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. **Wird auf die Schaltfläche "wird geklickt** " zurückgegeben, wenn das Ereignis oder die Schaltfläche im aktuellen Frame ausgelöst wird

Karte

![Ist Schaltfläche, auf die ein](images/unreal/is-button-clicked-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. **Get Controller Tracking Status** gibt den verfolgungsstatus im aktuellen Frame zurück.

Karte

![Controller-Überwachungs Status-BP erhalten](images/unreal/get-controller-tracking-status-bp.png)

C++:
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```

## <a name="gestures"></a>Gesten

Die hololens 2 können räumliche Gesten nachverfolgen, was bedeutet, dass Sie diese Gesten als Eingabe erfassen können. Weitere Informationen zu Gesten finden Sie im Artikel zur [grundlegenden Verwendung von hololens 2](https://docs.microsoft.com/hololens/hololens2-basic-usage) .

Sie finden die Blueprint-Funktion in unter **Windows Mixed Reality Spatial Input** und die C++-Funktion, indem Sie `WindowsMixedRealitySpatialInputFunctionLibrary.h` Ihre aufrufende Codedatei hinzufügen.

![Erfassungs Gesten](images/unreal/capture-gestures.png)

### <a name="enum"></a>Enumeration
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
Karte 

![Gesten-Typ](images/unreal/gesture-type.png)

C++:
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```

### <a name="function"></a>Funktion
Sie können die Gesten Erfassung mit der-Funktion aktivieren und deaktivieren `CaptureGestures` . Wenn eine aktivierte Geste Eingabeereignisse auslöst, gibt die Funktion zurück, `true` Wenn die Gesten Erfassung erfolgreich war, und, `false` Wenn ein Fehler vorliegt.

Karte

![Erfassungs Gesten BP](images/unreal/capture-gestures-bp.png)

C++:
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false, 
    bool Hold = false, 
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None, 
    bool NavigationAxisX = true, 
    bool NavigationAxisY = true, 
    bool NavigationAxisZ = true);
```

Im folgenden finden Sie wichtige Ereignisse, die in Blueprints und C++: Key-Ereignisse zu finden sind. ![](images/unreal/key-events.png)

![Schlüsselereignisse 2](images/unreal/key-events2.png)
```cpp
const FKey FSpatialInputKeys::TapGesture(TapGestureName);
const FKey FSpatialInputKeys::DoubleTapGesture(DoubleTapGestureName);
const FKey FSpatialInputKeys::HoldGesture(HoldGestureName);

const FKey FSpatialInputKeys::LeftTapGesture(LeftTapGestureName);
const FKey FSpatialInputKeys::LeftDoubleTapGesture(LeftDoubleTapGestureName);
const FKey FSpatialInputKeys::LeftHoldGesture(LeftHoldGestureName);

const FKey FSpatialInputKeys::RightTapGesture(RightTapGestureName);
const FKey FSpatialInputKeys::RightDoubleTapGesture(RightDoubleTapGestureName);
const FKey FSpatialInputKeys::RightHoldGesture(RightHoldGestureName);

const FKey FSpatialInputKeys::LeftManipulationGesture(LeftManipulationGestureName);
const FKey FSpatialInputKeys::LeftManipulationXGesture(LeftManipulationXGestureName);
const FKey FSpatialInputKeys::LeftManipulationYGesture(LeftManipulationYGestureName);
const FKey FSpatialInputKeys::LeftManipulationZGesture(LeftManipulationZGestureName);

const FKey FSpatialInputKeys::LeftNavigationGesture(LeftNavigationGestureName);
const FKey FSpatialInputKeys::LeftNavigationXGesture(LeftNavigationXGestureName);
const FKey FSpatialInputKeys::LeftNavigationYGesture(LeftNavigationYGestureName);
const FKey FSpatialInputKeys::LeftNavigationZGesture(LeftNavigationZGestureName);


const FKey FSpatialInputKeys::RightManipulationGesture(RightManipulationGestureName);
const FKey FSpatialInputKeys::RightManipulationXGesture(RightManipulationXGestureName);
const FKey FSpatialInputKeys::RightManipulationYGesture(RightManipulationYGestureName);
const FKey FSpatialInputKeys::RightManipulationZGesture(RightManipulationZGestureName);

const FKey FSpatialInputKeys::RightNavigationGesture(RightNavigationGestureName);
const FKey FSpatialInputKeys::RightNavigationXGesture(RightNavigationXGestureName);
const FKey FSpatialInputKeys::RightNavigationYGesture(RightNavigationYGestureName);
const FKey FSpatialInputKeys::RightNavigationZGesture(RightNavigationZGestureName);
```

## <a name="next-development-checkpoint"></a>Nächster Entwicklungs Prüfpunkt

Wenn Sie die unechte Development Checkpoint Journey befolgen, sind Sie in der Mitte, dass Sie die mrtk Core-Bausteine erkunden. Von hier aus können Sie mit dem nächsten Baustein fortfahren: 

> [!div class="nextstepaction"]
> [Lokale Raumanker](unreal-spatial-anchors.md)

Oder springen Sie zu den Funktionen und APIs der Mixed Reality-Plattform:

> [!div class="nextstepaction"]
> [HoloLens-Kamera](unreal-hololens-camera.md)

Sie können jederzeit jederzeit zu den [unechten Entwicklungs Prüfpunkten](unreal-development-overview.md#2-core-building-blocks) zurückkehren.