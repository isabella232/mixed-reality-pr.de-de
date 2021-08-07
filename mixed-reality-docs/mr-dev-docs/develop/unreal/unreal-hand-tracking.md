---
title: Handtracking in Unreal
description: Erfahren Sie, wie Sie Eingaben, Posen, Handgitternetze und Livelinkanimationen in Unreal Mixed Reality-Apps verwenden.
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, Handtracking, Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, Features, Dokumentation, Leitfäden, Hologramme, Spieleentwicklung, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 4c3b86c842fc875ebedbdf2527bf962fd8afd4d19cef90d168293cc85b664f70
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187264"
---
# <a name="hand-tracking-in-unreal"></a>Handtracking in Unreal

Das Handtrackingsystem verwendet die Handflächen und Finger einer Person als Eingabe. Daten zur Position und Drehung jedes Fingers, der gesamten Handfläche und handgesten sind verfügbar. Ab Unreal 4.26 basiert die Handnachverfolgung auf dem Unreal HeadMountedDisplay-Plug-In und verwendet eine gemeinsame API für alle XR-Plattformen und -Geräte. Die Funktionalität ist sowohl für Windows Mixed Reality als auch für OpenXR-Systeme identisch.

## <a name="hand-pose"></a>Handpose

Mit der Handpose können Sie die Hände und Finger Ihrer Benutzer als Eingabe nachverfolgen und verwenden, auf die sowohl in Blueprints als auch in C++ zugegriffen werden kann. Die Unreal-API sendet die Daten als Koordinatensystem, wobei Ticks mit der Unreal-Engine synchronisiert werden.

![Hand skeleton image with joints overlay Hand Skeleton (Handgerüstbild mit Überlagerung von ](images/hand-tracking-img-02.png)
 ![ Fugen)](images/hand-tracking-skeleton-update.png)

[!INCLUDE[](includes/tabs-tracking-hand-pose.md)]

## <a name="hand-live-link-animation"></a>Hand Live Link Animation

Handposen werden mithilfe des [Live Link-Plug-Ins](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html)für Animationen verfügbar gemacht.

Wenn die Windows Mixed Reality- und Live Link-Plug-Ins aktiviert sind:
1. Wählen Sie **Fenster > Live Link aus,** um das Live Link-Editorfenster zu öffnen.
2. Wählen Sie **Quelle** aus, und aktivieren **Sie Windows Mixed Reality Handtrackingquelle.**

![Live Link-Quelle](images/unreal/live-link-source.png)

Nachdem Sie die Quelle aktiviert und ein Animationsobjekt geöffnet haben, erweitern Sie den Abschnitt **Animation** auf der Registerkarte **Vorschauszene,** um weitere Optionen anzuzeigen.

![Live Link-Animation](images/unreal/live-link-animation.png)

Die Hierarchie der Handanimation ist identisch mit in `EWMRHandKeypoint` . Animationen können mithilfe von **WindowsMixedRealityHandTrackingLiveLinkRemapAsset** neu ermittelt werden:

![Live Link-Animation 2](images/unreal/live-link-animation2.png)

Sie kann auch im Editor untergliedert werden:

![Live Link Remap](images/unreal/live-link-remap.png)

## <a name="hand-mesh"></a>Handgitternetz

### <a name="hand-mesh-as-a-tracked-geometry"></a>Handgitter als nachverfolgte Geometrie

> [!IMPORTANT]
> Zum Abrufen von Handgittern als nachverfolgte Geometrie in OpenXR müssen Sie **Set Use Hand Mesh** with Enabled Tracking **Geometry** aufrufen.

Um diesen Modus zu aktivieren, sollten Sie **Set Use Hand Mesh** with Enabled Tracking **Geometry** aufrufen:

![Blaupause des Ereignisstarts wird verbunden, um die Verwendung der Handgitternetzfunktion mit aktivierter Nachverfolgung des Geometriemodus festzulegen.](images/unreal-hand-tracking-img-08.png)

> [!NOTE]
> Es ist nicht möglich, dass beide Modi gleichzeitig aktiviert werden. Wenn Sie eine aktivieren, wird die andere automatisch deaktiviert.

### <a name="accessing-hand-mesh-data"></a>Zugreifen auf Hand Mesh-Daten

![Handgitternetz](images/unreal/hand-mesh.png)

Bevor Sie auf Handgitternetzdaten zugreifen können, müssen Sie:
- Wählen Sie Ihr **ARSessionConfig-Medienobjekt** aus, erweitern Sie die Ar **Einstellungen -> World** Mapping-Einstellungen, und aktivieren **Sie Gitternetzdaten aus nachverfolgter Geometrie generieren.**

Im Folgenden sind die Standardgitternetzparameter aufgeführt:

1.  Verwenden von Gitternetzdaten für die Verdeckung
2.  Generieren von Kollisionen für Gitternetzdaten
3.  Generieren eines Navigationsgitters für Mesh-Daten
4.  Render Mesh Data in Wireframe – Debugparameter, der das generierte Gittermodell anzeigt

Diese Parameterwerte werden als Standardeinstellungen für räumliche Zuordnung und Handgitternetz verwendet. Sie können sie jederzeit in Blaupausen oder Code für ein beliebiges Netz ändern.

### <a name="c-api-reference"></a>C++-API-Referenz
Verwenden Sie `EEARObjectClassification` , um Handgitternetzwerte in allen nachverfolgbaren Objekten zu suchen.
```cpp
enum class EARObjectClassification : uint8
{
    // Other types
    HandMesh,
};
```

Die folgenden Delegaten werden aufgerufen, wenn das System ein nachverfolgbares Objekt erkennt, einschließlich eines Handgittermodells.

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

Stellen Sie sicher, dass Ihre Delegathandler der unten angegebenen Funktionssignatur folgen:

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

Sie können auf Meshdaten über  `UARTrackedGeometry::GetUnderlyingMesh` zugreifen:

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```

### <a name="blueprint-api-reference"></a>Referenz zur Blaupausen-API

So arbeiten Sie mit Handgittern in Blaupausen:
1. Hinzufügen einer **ARTrackableNotify-Komponente** zu einem Blueprint-Akteur

![ARTrackable-Benachrichtigung](images/unreal/ar-trackable-notify.png)

2. Wechseln Sie zum **Bereich Details,** und erweitern Sie den Abschnitt **Ereignisse.**

![ARTrackable Notify 2](images/unreal/ar-trackable-notify2.png)

3. Überschreiben Sie nachverfolgte Geometrie beim Hinzufügen/Aktualisieren/Entfernen mit den folgenden Knoten in Ihrer Event Graph:

![Bei ARTrackable-Benachrichtigung](images/unreal/on-artrackable-notify.png)

### <a name="hand-mesh-visualization-in-openxr"></a>Hand Mesh-Visualisierung in OpenXR

Die empfohlene Möglichkeit zum Visualisieren von Handgittern besteht darin, das XRVisualization-Plug-In von Epic zusammen mit dem [Microsoft OpenXR-Plug-In](https://github.com/microsoft/Microsoft-OpenXR-Unreal)zu verwenden. 

Verwenden Sie dann im Blaupausen-Editor die Funktion **Set Use Hand Mesh (Handnetz verwenden)** aus dem Microsoft [OpenXR-Plug-In](https://github.com/microsoft/Microsoft-OpenXR-Unreal) mit **aktivierter XRVisualization** als Parameter:

![Blaupause der Ereignisstartwiedergabe verbunden, um die Verwendung der Handnetzfunktion mit aktivierten Xrvisualisierungsmodus festzulegen](images/unreal-hand-tracking-img-05.png)

Um den Renderingprozess zu verwalten, sollten Sie **den Render Motion Controller** aus XRVisualization verwenden:

![Blaupause für die Get Motion Controller-Datenfunktion, die mit der Renderfunktion des Bewegungscontrollers verbunden ist](images/unreal-hand-tracking-img-06.png)

Das Ergebnis:

![Bild der digitalen Hand, die auf einer echten menschlichen Hand überlagert ist](images/unreal-hand-tracking-img-07.png) 

Wenn Sie etwas Komplizierteres benötigen, z. B. das Zeichnen eines Handgitters mit einem benutzerdefinierten Shader, müssen Sie die Gitternetze als nachverfolgte Geometrie abrufen. 

## <a name="hand-rays"></a>Handlichtstrahl

Das Abrufen der Handpose funktioniert für enge Interaktionen wie das Greifen von Objekten oder das Drücken von Schaltflächen. Manchmal müssen Sie jedoch mit Hologrammen arbeiten, die weit von Ihren Benutzern entfernt sind. Dies kann mit Handlichtlicht erreicht werden, das sowohl in C++ als auch in Blaupausen als zeigende Geräte verwendet werden kann. Sie können einen Strahl von der Hand bis zu einem fernen Punkt zeichnen und mithilfe der Unreal-Ray-Ablaufverfolgung ein Hologramm auswählen, das andernfalls nicht erreichbar wäre. 

> [!IMPORTANT]
> Da sich alle Funktionsergebnisse in jedem Frame ändern, werden sie alle aufrufbar gemacht. Weitere Informationen zu reinen und unreinen oder aufrufbaren Funktionen finden Sie unter Blueprint user guid on functions (Blaupausenbenutzer-GUID für [Funktionen).](https://docs.unrealengine.com/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)

[!INCLUDE[](includes/tabs-tracking-hand-ray.md)]

## <a name="gestures"></a>Gesten

Der HoloLens 2 verfolgt räumliche Gesten nach, was bedeutet, dass Sie diese Gesten als Eingabe erfassen können. Die Gestennachverfolgung basiert auf einem Abonnementmodell. Sie sollten die Funktion "Gesten konfigurieren" verwenden, um dem Gerät mitzuteilen, welche Gesten Sie nachverfolgen möchten.  Weitere Informationen zu Gesten finden Sie im [dokument HoloLens 2 Grundlegende Verwendung.](/hololens/hololens2-basic-usage)

[!INCLUDE[](includes/tabs-tracking-gestures.md)]

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie der Unreal-Entwicklungs-Journey folgen, die wir entworfen haben, befinden Sie sich mitten im Kennenlernen der MRTK-Grundbausteine. Von hier aus können Sie mit dem nächsten Baustein fortfahren:

> [!div class="nextstepaction"]
> [Lokale Raumanker](unreal-spatial-anchors.md)

Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:

> [!div class="nextstepaction"]
> [HoloLens-Kamera](unreal-hololens-camera.md)

Sie können jederzeit zu den [Prüfpunkten für die Unreal-Entwicklung](unreal-development-overview.md#2-core-building-blocks) zurückkehren.