---
ms.openlocfilehash: fb8b5b509ef83e2a4f9d978dbf0faebbf3e0be1d10d6697f16cfb9366d7a2edb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187420"
---
# <a name="426"></a>[4.26](#tab/426)

Um die Daten für den Handlichtstrahl abzurufen, sollten Sie die Funktion Get Motion Controller Data (Bewegungscontrollerdaten abrufen) aus dem vorherigen Abschnitt verwenden. Die zurückgegebene Struktur enthält zwei Parameter, die Sie zum Erstellen eines Handstrahls verwenden können: **Zielposition** und **Zielrotation.** Diese Parameter bilden einen Strahl, der vom Ellenbogen geleitet wird. Sie sollten sie aufnehmen und ein Hologramm finden, auf das gezeigt wird.

Im Folgenden finden Sie ein Beispiel für die Bestimmung, ob ein Handstrahl auf ein Widget trifft und ein benutzerdefiniertes Trefferergebnis festlegt:

![Blaupause für die Datenfunktion "Bewegungscontroller abrufen"](../images/unreal-hand-tracking-img-04.png) 

# <a name="425"></a>[4.25](#tab/425)

Um Handstrahl in Blaupausen zu verwenden, suchen Sie nach einer der Aktionen unter **Windows Mixed Reality HMD**:

![Hand ray BP](../images/unreal/hand-rays-bp.png)

Um in C++ darauf zuzugreifen, schließen `WindowsMixedRealityFunctionLibrary.h` Sie am Anfang der aufrufenden Codedatei ein.

### <a name="enum"></a>Enumeration

Sie haben auch Zugriff auf Eingabefälle unter **EHMDInputControllerButtons,** die in Blaupausen verwendet werden können:

![Eingabecontroller-Schaltflächen](../images/unreal/input-controller-buttons.png)

Verwenden Sie für den Zugriff in C++ die `EHMDInputControllerButtons` Enumerationsklasse:
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```

Im Folgenden finden Sie eine Aufschlüsselung der beiden anwendbaren Enumerationsfälle:

* **Wählen Sie** – Vom Benutzer ausgelöstes Select-Ereignis aus.
    * Wird in HoloLens 2 ausgelöst, indem auf die Luft tippt, anviert und committet oder "Auswählen" mit aktivierter [Spracheingabe](../unreal-voice-input.md) angezeigt wird.
* **Greifen:** Vom Benutzer ausgelöstes Ereignis "Greifen".
    * Wird in HoloLens 2 ausgelöst, indem die Finger des Benutzers auf einem Hologramm geschlossen werden.

Sie können auf den Nachverfolgungsstatus Ihres Handgitternetzes in C++ über die `EHMDTrackingStatus` unten gezeigte Enumeration zugreifen:

```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```

Im Folgenden finden Sie eine Aufschlüsselung der beiden anwendbaren Enumerationsfälle:

* **NotTracked** : Die Hand ist nicht sichtbar
* **Nachverfolgt** – die Hand ist vollständig nachverfolgt.

### <a name="struct"></a>Struktur

Die PointerPoseInfo-Struktur kann Ihnen Informationen zu den folgenden Handdaten liefern:

* **Ursprung:** Ursprung der Hand
* **Richtung** : Richtung der Hand
* **Nach** oben – Nach oben Vektor der Hand
* **Ausrichtung** : Ausrichtungsquaternion
* **Nachverfolgungsstatus** – aktueller Nachverfolgungsstatus

Sie können wie unten dargestellt über Blaupausen auf die PointerPoseInfo-Struktur zugreifen:

![Zeigerposeinfo BP](../images/unreal/pointer-pose-info-bp.png)

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

Alle unten aufgeführten Funktionen können für jeden Frame aufgerufen werden, was eine kontinuierliche Überwachung ermöglicht.

1. **Get Pointer Pose Info** gibt vollständige Informationen zur Handstrahlrichtung im aktuellen Frame zurück.

Blueprint:

![Get Pointer Pose Info](../images/unreal/get-pointer-pose-info.png)

C++:
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. **Is Grasped** gibt TRUE zurück, wenn die Hand im aktuellen Frame erkannt wird.

Blueprint:

![Is Grasped BP](../images/unreal/is-grasped-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```

3. **Wählen Sie Gedrückt** gibt true zurück, wenn der Benutzer Im aktuellen Frame Auswählen ausgelöst hat.

Blueprint:

![Is Select Pressed BP](../images/unreal/is-select-pressed-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. **Ist Schaltfläche Geklickt** gibt TRUE zurück, wenn das Ereignis oder die Schaltfläche im aktuellen Frame ausgelöst wird.

Blueprint:

![Is Button Clicked BP](../images/unreal/is-button-clicked-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. **Get Controller Tracking Status** gibt den Nachverfolgungsstatus im aktuellen Frame zurück.

Blueprint:

![Abrufen des Controllernachverfolgungsstatus BP](../images/unreal/get-controller-tracking-status-bp.png)

C++:
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```