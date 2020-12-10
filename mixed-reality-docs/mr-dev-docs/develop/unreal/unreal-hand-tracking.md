---
title: Handtracking in Unreal
description: Erläutert die Verwendung der Hand Verfolgung in Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, Hand Verfolgung, Unreal, Unreal Engine 4, UE4, hololens, hololens 2, Mixed Reality, Entwicklung, Features, Dokumentation, Handbücher, holograms, Spieleentwicklung, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 66ae1994f2bbee3ba4786a7c4eeebfe1cd57ca37
ms.sourcegitcommit: fbeff51cae92add88d2b960c9b7bbfb04d5a0291
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "97002660"
---
# <a name="hand-tracking-in-unreal"></a>Handtracking in Unreal

Das Hand Verfolgungssystem verwendet die Palmen und Finger der Person als Eingabe. Daten an Position und Drehung jedes Fingers, das gesamte Palmen und Handgesten sind verfügbar. Ab Unreal 4,26 basiert die Hand Verfolgung auf dem Unreal headmounteddisplay-Plug-in und verwendet eine gemeinsame API für alle XR-Plattformen und-Geräte. Die Funktionalität ist für Windows Mixed Reality und openxr Systems identisch.

## <a name="hand-pose"></a>Hand darstellen

Hand darstellen ermöglicht Ihnen die Nachverfolgung und Verwendung der Hände und Finger der Benutzer als Eingabe, auf die in Blueprints und C++ zugegriffen werden kann. Die Unreal-API sendet die Daten als Koordinatensystem, wobei Ticks mit der Unreal-Engine synchronisiert werden.

![Hand Gerüst](../native/images/hand-skeleton.png)

[!INCLUDE[](includes/tabs-tracking-hand-pose.md)]

## <a name="hand-live-link-animation"></a>Live Link Animation Hand

Hand stellen werden der Animation mithilfe des [Live Link-Plug](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html)-ins ausgesetzt.

Wenn die Windows Mixed Reality-und Live Link-Plug-ins aktiviert sind:
1. Wählen Sie **Window > Live Link** aus, um das Fenster Live Link-Editor zu öffnen.
2. **Quelle** auswählen und **Windows Mixed Reality-Hand Verfolgungs Quelle** aktivieren

![Live Link Quelle](images/unreal/live-link-source.png)

Nachdem Sie die Quelle aktiviert und ein Animations Objekt geöffnet haben, erweitern Sie den Abschnitt **Animation** auf der Registerkarte **Vorschau Szene** , um zusätzliche Optionen anzuzeigen.

![Live Link Animation](images/unreal/live-link-animation.png)

Die Hand Animations Hierarchie ist identisch mit der in `EWMRHandKeypoint` . Die Animation kann mithilfe von **windowsmixedrealityhandtrackinglebinkremapasset** neu zugewiesen werden:

![Live Link Animation 2](images/unreal/live-link-animation2.png)

Sie kann auch im Editor untergeordnet werden:

![Live Link Neuzuordnung](images/unreal/live-link-remap.png)

## <a name="hand-mesh"></a>Hand Netz

### <a name="hand-mesh-as-a-tracked-geometry"></a>Hand Mesh als nach verfolgte Geometrie

> [!IMPORTANT]
> Zum Abrufen von Hand Netzen als nach verfolgte Geometrie in openxr müssen Sie **Set use Hand Mesh** with **aktivierte Tracking Geometry** aufzurufen.

Um diesen Modus zu aktivieren, müssen Sie **Set use Hand Mesh** with **aktivierte nach Verfolgungs Geometrie** verwenden:

![Blaupause der Ereignis Start Wiedergabe, verbunden mit Set use Hand Mesh-Funktion mit aktiviertem nach Verfolgungs Geometrie Modus](images/unreal-hand-tracking-img-08.png)

> [!NOTE]
> Beide Modi können nicht gleichzeitig aktiviert werden. Wenn Sie eins aktivieren, wird das andere automatisch deaktiviert.

### <a name="accessing-hand-mesh-data"></a>Zugreifen auf Hand Mesh-Daten

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

So arbeiten Sie mit Hand-Meshes in Blaupausen:
1. Hinzufügen einer **artrackablenotify** -Komponente zu einem Blueprint-Actor

![Meldung zu einem darstellbaren Element](images/unreal/ar-trackable-notify.png)

2. Wechseln Sie zum **Detail** Panel, und erweitern Sie den Abschnitt **Ereignisse** .

![Artrackable Benachrichtigen 2](images/unreal/ar-trackable-notify2.png)

3. Überschreiben Sie beim Hinzufügen/Aktualisieren/Entfernen der überwachten Geometrie mit den folgenden Knoten im Ereignis Diagramm:

![Bei der über sichtbaren Benachrichtigung](images/unreal/on-artrackable-notify.png)

### <a name="hand-mesh-visualization-in-openxr"></a>Hand Mesh-Visualisierung in openxr

Die empfohlene Vorgehensweise zum Visualisieren des Hand Netzes ist, das xrvisualisierung-Plug-in von epic gemeinsam mit dem [Microsoft openxr-Plug](https://github.com/microsoft/Microsoft-OpenXR-Unreal)-in zu verwenden 

Verwenden Sie dann im Blueprint-Editor die Option **use Hand Mesh** Function aus dem [Microsoft openxr-Plug](https://github.com/microsoft/Microsoft-OpenXR-Unreal) -in mit **aktiviertem xrvisualisierung** als Parameter.

![Blaupause für Ereignis BEGIN Play ist verbunden mit Set use Hand Mesh-Funktion mit aktiviertem xrvisualisierungs Modus](images/unreal-hand-tracking-img-05.png)

Um den Renderingprozess zu verwalten, sollten Sie **renderbewegungs-Controller** aus xrvisualisierung verwenden:

![Blaupause der Get Motion Controller-Daten Funktion, die mit der Funktion "Rendering Motion Controller" verbunden](images/unreal-hand-tracking-img-06.png)

Das Ergebnis:

![Bild der digitalen Hand, die auf einer echten Menschen überladenen Hand ist](images/unreal-hand-tracking-img-07.png) 

Wenn Sie etwas komplizierteres benötigen (z. b. das Zeichnen eines Hand Diagramms mit einem benutzerdefinierten Shader), müssen Sie die Netzen als nach verfolgte Geometrie erhalten. 

## <a name="hand-rays"></a>Handlichtstrahl

Das Abrufen von Hand stellen funktioniert für schließen-Interaktionen wie das Durchsuchen von Objekten oder das Drücken von Manchmal müssen Sie jedoch mit holograms arbeiten, die von den Benutzern weit entfernt sind. Dies kann mit Hand Strahlen erreicht werden, die als Zeigegeräte sowohl in C++ als auch in Blaupausen verwendet werden können. Sie können einen Strahl von Hand zu einem Punkt zeichnen und, mit Hilfe von Unreal Ray Tracing, ein – Hologramm auswählen, das andernfalls nicht erreichbar wäre. 

> [!IMPORTANT]
> Da alle Funktions Ergebnisse jeden Frame ändern, werden Sie alle aufgerufen. Weitere Informationen zu reinen und impformen oder Aufruf baren Funktionen finden Sie in der Blueprint-Benutzer-GUID für [Funktionen](https://docs.unrealengine.com/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure).

[!INCLUDE[](includes/tabs-tracking-hand-ray.md)]

## <a name="gestures"></a>Gesten

Hololens 2 verfolgt räumliche Gesten, was bedeutet, dass Sie diese Gesten als Eingabe erfassen können. Die Gesten Verfolgung basiert auf einem Abonnement Modell. Verwenden Sie die Funktion "Gesten konfigurieren", um dem Gerät mitzuteilen, welche Gesten Sie nachverfolgen möchten.  Weitere Informationen zu Gesten finden Sie im Artikel zur [grundlegenden Verwendung von hololens 2](https://docs.microsoft.com/hololens/hololens2-basic-usage) .

[!INCLUDE[](includes/tabs-tracking-gestures.md)]

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie die unwirkliche Entwicklungs Journey befolgen, die wir festgelegt haben, befinden Sie sich mitten in der Untersuchung der mrtk Core-Bausteine. Von hier aus können Sie mit dem nächsten Baustein fortfahren:

> [!div class="nextstepaction"]
> [Lokale Raumanker](unreal-spatial-anchors.md)

Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:

> [!div class="nextstepaction"]
> [HoloLens-Kamera](unreal-hololens-camera.md)

Sie können jederzeit zu den [Prüfpunkten für die Unreal-Entwicklung](unreal-development-overview.md#2-core-building-blocks) zurückkehren.
