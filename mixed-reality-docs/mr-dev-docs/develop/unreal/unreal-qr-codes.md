---
title: QR-Codes in Unreal
description: Erfahren Sie, wie QR-Codes in Unreal-Mixed Reality-Anwendungen eingerichtet, verwendet und nachverfolgt werden.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, Features, Dokumentation, Leitfäden, Hologramme, QR-Codes, Mixed Reality-Headset Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 689ebe9b904b269c00078245b137bc21f2e56df2b441150c7c6b18c179ac51f4
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115205124"
---
# <a name="qr-codes-in-unreal"></a>QR-Codes in Unreal

HoloLens 2 kann QR-Codes in der Außenwelt mithilfe der Webcam sehen und gibt sie an jeder Position von Codes in der Realwelt als Hologramme wieder. HoloLens 2 kann Hologramme außerdem an der gleichen Position auf mehreren Geräten rendern, um eine gemeinsame Erfahrung zu ermöglichen. Achten Sie darauf, die bewährten Methoden für das Hinzufügen von QR-Codes zu Ihren Anwendungen zu befolgen:

- Ruhezonen
- Beleuchtung und Hintergrund
- Größe, Abstand und Winkelposition

Achten Sie besonders auf [Umgebungsaspekte](/hololens/hololens-environment-considerations), wenn in Ihrer App QR-Codes platziert werden. Weitere Informationen zu jedem dieser Themen und Anweisungen zum Herunterladen des erforderlichen NuGet-Pakets finden Sie im Dokument zum [Nachverfolgen von QR-Codes](../platform-capabilities-and-apis/qr-code-tracking.md).

> [!CAUTION]
> QR-Codes sind die einzige Art von Bildern, die von HoloLens standardmäßig nachverfolgt werden können – das Modul **UARTrackedImage** von Unreal wird von HoloLens nicht unterstützt. Wenn Sie benutzerdefinierte Bilder nachverfolgen müssen, können Sie auf die [Webcam](unreal-hololens-camera.md) des Geräts zugreifen und Bilder mithilfe einer Drittanbieterbibliothek zur Bilderkennung verarbeiten. 

## <a name="enabling-qr-detection"></a>Aktivieren der QR-Erkennung

Da HoloLens 2 die Webcam verwenden muss, um QR-Codes zu sehen, müssen Sie diese in den Projekteinstellungen aktivieren:
- Öffnen Sie **Edit > Project Settings** (Bearbeiten > Projekteinstellungen), scrollen Sie zum Abschnitt **Platforms** (Plattformen), und wählen Sie **HoloLens** aus.
    + Klappen Sie den Abschnitt **Capabilities** (Funktionen) auf, und aktivieren Sie **Webcam**.  
- Ferner müssen Sie die Nachverfolgung von QR-Codes abonnieren, indem Sie [ein ARSessionConfig-Objekt hinzufügen](/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).

[!INCLUDE[](includes/tabs-qr-codes-1.md)]

## <a name="setting-up-a-tracked-qr-code"></a>Einrichten eines nachverfolgten QR-Codes

QR-Codes werden über das AR-Geometrienachverfolgungssystem von Unreal als nachverfolgtes Bild bereitgestellt. Damit dies funktioniert, müssen Sie Folgendes ausführen:
1. Eine Blaupause eines Akteurs erstellen und eine **ARTrackableNotify**-Komponente hinzufügen:

![QR: In AR nachverfolgbare Benachrichtigung](images/unreal-spatialmapping-artrackablenotify.PNG)

2. **ARTrackableNotify** auswählen und den Abschnitt **Events** (Ereignisse) im Bereich **Details** aufklappen:

![QR: Ereignisse](images/unreal-spatialmapping-events.PNG)

3. Klicken Sie neben **On Add Tracked Geometry** (Beim Hinzufügen von nachverfolgter Geometrie) auf **+** , um dem Ereignisdiagramm den Knoten hinzuzufügen.
    - Die vollständige Liste der Ereignisse finden Sie in der Komponenten-API [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html).

![Knoten zu On Add Tracked Geometry hinzufügen](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-qr-code"></a>Verwenden eines nachverfolgten QR-Codes

Das Ereignisdiagramm in der folgenden Abbildung zeigt, wie das **OnUpdateTrackedImage**-Ereignis dazu verwendet wird, einen Punkt in der Mitte eines QR-Codes zu rendern und dessen Daten auszugeben.

[!INCLUDE[](includes/tabs-qr-codes-2.md)]

Das geschieht bei diesem Vorgang:
1. Zunächst wird das nachverfolgte Bild in einen **ARTrackedQRCode** umgewandelt, um zu prüfen, ob es sich bei dem aktuellen aktualisierten Bild um einen QR-Code handelt.  
2. Die codierten Daten werden aus der **QRCode**-Variable abgerufen. Sie können den oberen linken Punkt des QR-Codes aus der Position von **GetLocalToWorldTransform** und seine Abmessungen mit **GetEstimateSize** abrufen.

Ferner können Sie [das Koordinatensystem für einen QR-Code in Code abrufen](/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code).

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

Sie können jederzeit zu den [Prüfpunkten für die Unreal-Entwicklung](unreal-development-overview.md#3-advanced-features) zurückkehren.

## <a name="see-also"></a>Siehe auch
* [Räumliche Abbildung](../../design/spatial-mapping.md)
* [Hologramme](../../discover/hologram.md)
* [Koordinatensysteme](../../design/coordinate-systems.md)