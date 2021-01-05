---
ms.openlocfilehash: 18ccbf3e28eaa2f61157bd9585d633c987e9af48
ms.sourcegitcommit: 13ef9f89ee61fbfe547ecf5fdfdb97560a0de833
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/21/2020
ms.locfileid: "97717725"
---
# <a name="426"></a>[4.26](#tab/426)

Um die Daten für die Hand-Strahlen zu erhalten, sollten Sie die Get Motion Controller-Daten Funktion aus dem vorherigen Abschnitt verwenden. Die zurückgegebene Struktur enthält zwei Parameter, die Sie verwenden können, um eine Hand Strahl-– **Ziel Position** und **Ziel Drehung** zu erstellen. Diese Parameter bilden einen Strahl, der von Ihrem Bogen gesteuert wird. Sie sollten diese übernehmen und ein – Hologramm finden, auf das verweist.

Im folgenden finden Sie ein Beispiel für die Bestimmung, ob ein Hand Strahl auf ein Widget trifft und ein benutzerdefiniertes Treffer Ergebnis festlegt:

![Blaupause der Get Motion Controller-Daten Funktion](../images/unreal-hand-tracking-img-04.png) 

# <a name="425"></a>[4.25](#tab/425)

Um Hand Abdrücke in Blaupausen zu verwenden, suchen Sie nach den Aktionen unter **Windows Mixed Reality HMD**:

![Hand Strahlen-BP](../images/unreal/hand-rays-bp.png)

Wenn Sie in C++ auf Sie zugreifen möchten, schließen Sie am `WindowsMixedRealityFunctionLibrary.h` Anfang der aufrufenden Codedatei ein.

### <a name="enum"></a>Enumeration

Sie haben auch Zugriff auf die Eingabe Fälle unter **ehmdinputcontrollerbuttons**, die in Blaupausen verwendet werden können:

![Eingabe Controller-Schaltflächen](../images/unreal/input-controller-buttons.png)

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
    * Ausgelöst in hololens 2 durch Luft tippen, Überblicks und Commit oder durch "Select" mit aktivierter [Spracheingabe](../unreal-voice-input.md) .
* Das von Benutzern ausgelöste Ereignis **zum Erfassen von** Ereignissen.
    * Wird in hololens 2 ausgelöst, indem die Finger des Benutzers in einem Hologram geschlossen werden.

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

Sie können auf die pointerposeinfo-Struktur über Blaupausen zugreifen, wie unten dargestellt:

![Zeiger stellen Informationen BP dar](../images/unreal/pointer-pose-info-bp.png)

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

![Informationen zum Darstellen von Zeigern](../images/unreal/get-pointer-pose-info.png)

C++:
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. **Ist** "-Wert" gibt "true" zurück, wenn die Hand im aktuellen Frame erfasst wird.

Karte

![Erfasste BP](../images/unreal/is-grasped-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```

3. **Ist SELECT gedrückt** gibt true zurück, wenn der Benutzer SELECT im aktuellen Frame ausgelöst hat.

Karte

![Ist SELECT-Taste für BP](../images/unreal/is-select-pressed-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. **Wird auf die Schaltfläche "wird geklickt** " zurückgegeben, wenn das Ereignis oder die Schaltfläche im aktuellen Frame ausgelöst wird

Karte

![Ist Schaltfläche, auf die ein](../images/unreal/is-button-clicked-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. **Get Controller Tracking Status** gibt den verfolgungsstatus im aktuellen Frame zurück.

Karte

![Controller-Überwachungs Status-BP erhalten](../images/unreal/get-controller-tracking-status-bp.png)

C++:
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```