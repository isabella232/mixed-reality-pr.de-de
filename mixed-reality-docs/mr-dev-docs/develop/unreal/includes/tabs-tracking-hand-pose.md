---
ms.openlocfilehash: ec1246085989b4b157504e9b8551694d6116e6f08789fa669200e5425ef75cc6
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187419"
---
# <a name="426"></a>[4.26](#tab/426)

Die Hierarchie wird durch `EHandKeypoint` enum beschrieben:

![Abbildung der Optionen für den Handtastenpunkt-Bluprint](../images/hand-keypoint-bp.png)

Sie können alle diese Daten aus den Händen eines Benutzers mithilfe der **Funktion Get Motion Controller Data (Motion Controller-Daten erhalten)** erhalten. Diese Funktion gibt eine **XRMotionControllerData-Struktur** zurück. Im Folgenden finden Sie ein Blaupausenskript, das die XRMotionControllerData-Struktur analysiert, um Hand-Fugenpositionen zu erhalten, und ein Debugkoordinatensystem an der Position der einzelnen Fugen zeichnet.

![Blaupause der Get Gaze Data-Funktion, die mit der Zeilenverfolgung nach Kanalfunktion verbunden ist](../images/unreal-hand-tracking-img-03.png)

Es ist wichtig zu überprüfen, ob die Struktur gültig und eine Hand ist. Andernfalls erhalten Sie möglicherweise nicht definiertes Verhalten beim Zugriff auf Positionen, Drehungen und Radiiarrays.

# <a name="425"></a>[4.25](#tab/425)

Die `EWMRHandKeypoint` -Aufzähle beschreibt die Hierarchie der Handhierarchie. Sie finden jeden Handschlüsselpunkt, der in Ihren Blaupausen aufgeführt ist:

![Hand Keypoint BP](../images/hand-keypoint-bp.png)

Die vollständige C++-Enum ist unten aufgeführt:
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

Sie finden die numerischen Werte für jeden Enumerum-Fall im [Windows. Perception.People.HandJointKind-Tabelle.](/uwp/api/windows.perception.people.handjointkind)

### <a name="supporting-hand-tracking"></a>Unterstützen der Handverfolgung

Sie können die Handnachverfolgung in Blaupausen verwenden, indem Sie **Unterstützung der Handnachverfolgung** von **Hand tracking > Windows Mixed Reality:**

![HandTracking BP](../images/unreal/hand-tracking-bp.png)

Diese Funktion gibt zurück, wenn die Handverfolgung auf dem Gerät unterstützt wird und keine Handverfolgung `true` `false` verfügbar ist.

![Unterstützt Hand Tracking BP](../images/unreal/supports-hand-tracking-bp.png)

C++:

Schließen Sie `WindowsMixedRealityHandTrackingFunctionLibrary.h` ein.

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a>Abrufen der Handverfolgung

Sie können **GetHandJointTransform verwenden,** um räumliche Daten von der Hand zurück zu geben. Die Daten aktualisieren jeden Frame, aber wenn Sie sich innerhalb eines Frames befinden, werden die zurückgegebenen Werte zwischengespeichert. Es wird aus Leistungsgründen nicht empfohlen, in dieser Funktion eine hohe Logik zu verwenden.

![Get Hand Joint Transform](../images/unreal/get-hand-joint-transform.png)

C++:
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

Hier ist eine Aufschlüsselung der Funktionsparameter von GetHandJointTransform:

* **Hand:** Kann die linke oder rechte Benutzerhand sein.
* **Keypoint:** das Handgefing.
* **Transformieren** : Koordinaten und Ausrichtung der Basis des 100.000-Menschen. Sie können die Basis des nächsten 100-Mal anfordern, um die Transformationsdaten für das Ende eines 30-00-00-00-Mal zu erhalten. Ein spezielles Trinkgeld gibt das Ende der Distalen.
* **Radius– Radius der Basis des 5.
* **Rückgabewert – TRUE, wenn der Gerüst in diesem Frame nachverfolgt wird, FALSE, wenn das Gerüst nicht nachverfolgt wird.