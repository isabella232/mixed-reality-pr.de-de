---
title: QR-Codes in Unreal
description: Leitfaden zur Verwendung von QR-Codes in Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, Features, Dokumentation, Leitfäden, Hologramme, QR-Codes
ms.openlocfilehash: 0f0507e2f726830cef27c190083363b3607379ee
ms.sourcegitcommit: 8e91ff47ef70e80a41137f80aa1093e711d27bf7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2020
ms.locfileid: "91957820"
---
# <a name="qr-codes-in-unreal"></a>QR-Codes in Unreal

## <a name="overview"></a>Übersicht

HoloLens 2 kann QR-Codes in der Außenwelt mithilfe der Webcam sehen und gibt sie mithilfe eines Koordinatensystems an jeder Position von Codes in der Realwelt als Hologramme wieder.  Über einzelne QR-Codes hinaus kann HoloLens 2 Hologramme außerdem an der gleichen Position auf mehreren Geräten rendern, um eine gemeinsame Erfahrung zu ermöglichen. Achten Sie darauf, die bewährten Methoden für das Hinzufügen von QR-Codes zu Ihren Anwendungen zu befolgen:

- Ruhezonen
- Beleuchtung und Hintergrund
- Größe, Abstand und Winkelposition

Achten Sie besonders auf [Umgebungsaspekte](../../environment-considerations-for-hololens.md), wenn in Ihrer App QR-Codes platziert werden. Weitere Informationen zu jedem dieser Themen und Anweisungen zum Herunterladen des erforderlichen NuGet-Pakets finden Sie im Dokument zum [Nachverfolgen von QR-Codes](../platform-capabilities-and-apis/qr-code-tracking.md).

## <a name="enabling-qr-detection"></a>Aktivieren der QR-Erkennung
Da HoloLens 2 die Webcam verwenden muss, um QR-Codes zu sehen, müssen Sie diese in den Projekteinstellungen aktivieren:
- Öffnen Sie **Edit > Project Settings** (Bearbeiten > Projekteinstellungen), scrollen Sie zum Abschnitt **Platforms** (Plattformen), und klicken Sie auf **HoloLens**.
    + Klappen Sie den Abschnitt **Capabilities** (Funktionen) auf, und aktivieren Sie **Webcam**.  

Ferner müssen Sie die Nachverfolgung von QR-Codes abonnieren, indem Sie [ein ARSessionConfig-Objekt hinzufügen](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).

Unmittelbar vor der Verwendung sollten Sie die Nachverfolgung manuell durch Aufrufen von `UHoloLensARFunctionLibrary::StartCameraCapture()` aktivieren. Nachdem Sie die QR-Codenachverfolgung beendet haben, sollten Sie sie mittels `UHoloLensARFunctionLibrary::StopCameraCapture()` deaktivieren, um die Geräteressourcen zu sparen.

## <a name="setting-up-a-tracked-image"></a>Einrichten eines nachverfolgten Bilds

QR-Codes werden über das AR-Geometrienachverfolgungssystem von Unreal als nachverfolgtes Bild bereitgestellt. Damit dies funktioniert, müssen Sie Folgendes ausführen:
1. Erstellen einer Blaupause und Hinzufügen einer **ARTrackableNotify**-Komponente.

![QR: In AR nachverfolgbare Benachrichtigung](images/unreal-spatialmapping-artrackablenotify.PNG)

2. Wählen Sie **ARTrackableNotify** aus, und klappen Sie im Bereich **Details** den Abschnitt **Events** (Ereignisse) auf.

![QR: Ereignisse](images/unreal-spatialmapping-events.PNG)

3. Klicken Sie neben **On Add Tracked Geometry** (Beim Hinzufügen von nachverfolgter Geometrie) auf **+** , um dem Ereignisdiagramm den Knoten hinzuzufügen.
    - Die vollständige Liste der Ereignisse finden Sie in der Komponenten-API [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html).

![Knoten zu On Add Tracked Geometry hinzufügen](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-image"></a>Verwenden eines nachverfolgten Bilds
Das Ereignisdiagramm in der folgenden Abbildung zeigt, wie das **OnUpdateTrackedImage**-Ereignis dazu verwendet wird, einen Punkt in der Mitte eines QR-Codes zu rendern und dessen Daten auszugeben.

![QR: Renderbeispiel](images/unreal-qr-render.PNG)

Das geschieht bei diesem Vorgang:
1. Zunächst wird das nachverfolgte Bild in einen **ARTrackedQRCode** umgewandelt, um zu prüfen, ob es sich bei dem aktuellen aktualisierten Bild um einen QR-Code handelt.  
2. Die codierten Daten werden aus der **QRCode**-Variable abgerufen. Sie können den oberen linken Punkt des QR-Codes aus der Position von **GetLocalToWorldTransform** und seine Abmessungen mit **GetEstimateSize** abrufen.

Ferner können Sie [das Koordinatensystem für einen QR-Code in Code abrufen](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code).

## <a name="finding-the-unique-id"></a>Ermitteln der eindeutigen ID
Jeder QR-Code weist eine eindeutige GUID-ID auf, die Sie auf diese Weise herausfinden können:
- Ziehen und Ablegen des **As ARTracked QRCode**-Stifts und Suchen nach **Get Unique ID** (Eindeutige ID abrufen).

![QR: GUID](images/unreal-qr-guid.PNG)

Mit QR-Codes passiert eine Menge hinter den Kulissen, daher ist diese Erörterung nicht abschließend. Folgen Sie unbedingt den folgenden Links, um mehr über die inneren Vorgänge zu erfahren.

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie dem Weg der Unity-Entwicklungsprüfpunkte folgen, den wir entworfen haben, befinden Sie sich mitten im Kennenlernen der Mixed Reality-Plattformfunktionen und APIs. Von hier aus können Sie mit dem nächsten Thema fortfahren:

> [!div class="nextstepaction"]
> [WinRT](unreal-winRT.md)

Oder wechseln Sie direkt zur Bereitstellung Ihrer App auf einem Gerät oder Emulator:

> [!div class="nextstepaction"]
> [Bereitstellung auf Gerät](unreal-deploying.md)

Sie können jederzeit zu den [Prüfpunkten für die Unreal-Entwicklung](unreal-development-overview.md#3-platform-capabilities-and-apis) zurückkehren.

## <a name="see-also"></a>Siehe auch
* [Räumliche Abbildung](../../design/spatial-mapping.md)
* [Hologramme](../../discover/hologram.md)
* [Koordinatensysteme](../../design/coordinate-systems.md)
