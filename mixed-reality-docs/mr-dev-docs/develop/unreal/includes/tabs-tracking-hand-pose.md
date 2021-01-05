---
ms.openlocfilehash: c5a13798ca6a73f1a6410abe310c2166b67f4626
ms.sourcegitcommit: 13ef9f89ee61fbfe547ecf5fdfdb97560a0de833
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/21/2020
ms.locfileid: "97717482"
---
# <a name="426"></a>[4.26](#tab/426)

Die Hierarchie wird von `EHandKeypoint` enum beschrieben:

![Bild der Hand-Optionen für "keypoint bluprint"](../images/hand-keypoint-bp.png)

Mithilfe der **Get Motion Controller-Daten** Funktion können Sie all diese Daten aus den Händen eines Benutzers erhalten. Diese Funktion gibt eine **xrmutioncontrollerdata** -Struktur zurück. Im folgenden finden Sie ein Beispielskript für eine Blaupause, das die xrmutioncontrollerdata-Struktur analysiert, um Handgelenk Positionen zu erhalten und ein debugkoordinaten System an den Positionen der einzelnen gemeinsamen Standorte zeichnet.

![Blaupause der get-Daten Funktion für den Blick an die Zeilen Ablauf Verfolgung nach Kanal Funktion](../images/unreal-hand-tracking-img-03.png)

Es ist wichtig, zu überprüfen, ob die Struktur gültig ist und dass Sie eine Hand ist. Andernfalls erhalten Sie möglicherweise nicht definiertes Verhalten beim Zugriff auf Positionen, Rotationen und Radien-Arrays.

# <a name="425"></a>[4.25](#tab/425)

Die `EWMRHandKeypoint` -Enumeration beschreibt die Knochen Hierarchie der Hand. Sie finden jeden Hand-keypoint, der in ihren Blaupausen aufgeführt ist:

![Hand-keypoint-BP](../images/hand-keypoint-bp.png)

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

Sie können die numerischen Werte für jeden enumerationsfall in der Tabelle " [Windows. perception. People. handjointkind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) " finden.

### <a name="supporting-hand-tracking"></a>Unterstützende Hand Verfolgung

Sie können die Hand Verfolgung in Blaupausen verwenden, indem Sie die Hand Verfolgung von Hand Nachverfolgung **> Windows Mixed Reality** **Hinzufügen** :

![Hand Tracking-BP](../images/unreal/hand-tracking-bp.png)

Diese Funktion gibt zurück, `true` Wenn die Hand Verfolgung auf dem Gerät unterstützt wird und die `false` Hand Nachverfolgung nicht verfügbar ist.

![Unterstützt die Hand Überwachung von BP](../images/unreal/supports-hand-tracking-bp.png)

C++:

Schließen Sie `WindowsMixedRealityHandTrackingFunctionLibrary.h` ein.

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a>Erhalten von Hand Nachverfolgung

Mit **gethandjointtransform** können Sie räumliche Daten von Hand zurückgeben. Die Daten aktualisieren jeden Frame, aber wenn Sie sich innerhalb eines Frames befinden, werden die zurückgegebenen Werte zwischengespeichert. Es wird aus Leistungsgründen nicht empfohlen, in dieser Funktion eine hohe Logik zu haben.

![Hand Gelenk Transformation](../images/unreal/get-hand-joint-transform.png)

C++:
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

Im folgenden finden Sie eine Aufschlüsselung der Funktionsparameter von gethandjointtransform:

* **Hand** – kann die Benutzer Links oder rechts sein.
* **Keypoint** – der Knochen der Hand.
* **Transformation** – Koordinaten und Ausrichtung der Basis von Bone. Sie können die Basis des nächsten Knochens anfordern, um die Transformations Daten für das Ende eines Knochens zu erhalten. Ein spezieller Tip-Bone gibt das Ende der distal-Tabelle an.
* * * Radius – Radius der Basis des-Knochens.
* * * Rückgabewert – true, wenn der Rahmen dieses Frames nachverfolgt wird, false, wenn der Knochen nicht nachverfolgt wird.

