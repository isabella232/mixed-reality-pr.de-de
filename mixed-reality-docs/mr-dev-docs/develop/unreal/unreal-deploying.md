---
title: Bereitstellen auf Gerät in Unreal
description: Leitfaden für die Bereitstellung auf dem Gerät in Unreal für hololens 2
author: sw5813
ms.author: suwu
ms.date: 7/10/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, hololens, hololens 2, Mixed Reality, bereitstellen auf Geräten, PCs, Dokumentationen, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
appliesto:
- HoloLens 2
ms.openlocfilehash: ef33e037d6ab6a69059c1452b71a428fe51836b9
ms.sourcegitcommit: d56e7dd6c917ddc4ead0792ebff21891921174b9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564020"
---
# <a name="deploy-to-device-in-unreal"></a>Bereitstellen auf Gerät in Unreal

## <a name="overview"></a>Übersicht
Es gibt zwei Möglichkeiten, eine Unreal-Anwendung auf hololens 2 bereitzustellen:
* Direkt aus dem Unreal-Editor
* Als Paket, das über das Geräte Portal hochgeladen wird

Für beide Optionen müssen Sie die hololens einrichten, damit das [Geräte Portal](../platform-capabilities-and-apis/using-the-windows-device-portal.md) für die Entwicklung verwendet werden können.

## <a name="deploying-to-device-from-the-unreal-editor"></a>Bereitstellen auf einem Gerät über den Unreal-Editor

1. Klicken Sie auf den Dropdown Pfeil neben der Schaltfläche **starten** . Anfänglich ist die hololens-Geräte Option ausgegraut.

![Startmenü Optionen](images/unreal/launch-dropdown.png)

2. Öffnen Sie die **Geräte-Manager**. Beachten Sie, dass Ihre hololens nicht automatisch in der Geräteliste angezeigt werden.

3. Erweitern Sie den Abschnitt **nicht aufgelisteten Gerät hinzufügen** .

4. Wählen Sie **hololens** als **Plattform** aus.

5. Geben Sie die IP-Adresse und die Port Informationen Ihrer Geräte als Geräte Bezeichner getrennt durch einen Doppelpunkt ein. Beispiel: "127.0.0.1:10080" (bei Verbindung über USB). Verwenden Sie die Anmelde Informationen für den Benutzernamen Ihres Geräte Portals.

6. Schließen **Sie** den Geräte-Manager, und schließen Sie ihn.
    * Im Falle eines Fehlers (z. b. falsche Adresse, Benutzername oder Kennwort) wird eine Meldung in das Ausgabeprotokoll ausgegeben.

![Hinzufügen eines nicht aufgelisteten Geräts](images/unreal/add-unlisted-device.png)

7. Klicken Sie erneut auf den Dropdown Pfeil neben der Schaltfläche " **Start** ". dieses Mal sollte das von Ihnen soeben hinzugefügte hololens-Gerät angezeigt werden. Wählen Sie das hololens-Gerät zum Erstellen und Bereitstellen Ihrer hololens aus.

>[!NOTE]
>Das Erstellen für das Gerät erfordert möglicherweise die Neukompilierung von Shadern (insbesondere bei der ersten Ausführung). Dies kann einige Zeit in Anspruch nehmen. Lassen Sie das Gerät erst wieder in den Standbymodus wechseln, wenn die app ausgeführt wird (möglicherweise müssen Sie es verwenden). Andernfalls tritt bei der shaderkompilierung ein Fehler auf.

## <a name="deploying-to-device-via-device-portal"></a>Bereitstellen auf einem Gerät über das Geräte Portal

Ausführliche Anweisungen zum [Verpacken und Bereitstellen einer APP](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) finden Sie im letzten Abschnitt der Reihe "Getting Started with Unreal Tutorial".

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie die unechte Development Checkpoint Journey befolgen, befinden wir uns in der Mitte der Bereitstellungs Phase. Von hier aus können Sie mit dem Hinzufügen erweiterter Dienste fortfahren:

> [!div class="nextstepaction"]
> [Erweiterte Dienste](unreal-development-overview.md#5-adding-services)

Sie können jederzeit zu den [Prüfpunkten für die Unreal-Entwicklung](unreal-development-overview.md#4-streaming-and-deploying-to-a-device) zurückkehren.
