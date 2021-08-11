---
title: Bereitstellen auf Gerät in Unreal
description: Erfahren Sie alles, was Sie wissen müssen, um Ihre Mixed Reality-Unreal-Apps für HoloLens 2 über den Editor oder das Geräteportal bereitzustellen.
author: sw5813
ms.author: suwu
ms.date: 12/9/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Bereitstellung auf Gerät, PC, Dokumentation, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
appliesto:
- HoloLens 2
ms.openlocfilehash: d6df3f9af21a0759c98306c28696d21eac7687b92d3cb74a9cd9948122cbcbcc
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226640"
---
# <a name="deploy-to-device-in-unreal"></a>Bereitstellen auf Gerät in Unreal

Es gibt zwei Möglichkeiten zum Bereitstellen einer Unreal-Anwendung für HoloLens 2:
* Direkt aus dem Unreal-Editor
* Als über das Geräteportal hochgeladenes Paket

Beide Optionen erfordern, dass Sie Ihre HoloLens für die Verwendung des [Geräteportals für die](../platform-capabilities-and-apis/using-the-windows-device-portal.md) Entwicklung einrichten.

## <a name="deploying-to-device-from-the-unreal-editor"></a>Bereitstellen auf dem Gerät über den Unreal-Editor

1. Wählen Sie den Dropdownpfeil neben der **Schaltfläche Starten** aus. Zunächst wird die HoloLens-Option ausgegraut.

![Dropdownoptionen zum Starten](images/unreal/launch-dropdown.png)

2. Öffnen Sie **Geräte-Manager,** und beachten Sie, dass HoloLens nicht automatisch in der Geräteliste angezeigt wird.

3. Erweitern Sie **den Abschnitt Nicht aufgelistetes Gerät hinzufügen.**

4. Wählen **HoloLens** als Plattform **aus.**

5. Geben Sie die IP-Adresse und die Portinformationen Ihrer Geräte getrennt durch einen Doppelpunkt als Geräte-ID ein. Beispiel: "127.0.0.1:10080" (bei Verbindung über USB). Verwenden Sie Geräteportal Anmeldeinformationen für Benutzername und Kennwort.

6. **Treffe auf** Hinzufügen, und füge den Geräte-Manager zu.
    * Wenn ein Fehler auftritt, z. B. falsche Adresse oder falsche Benutzeranmeldeinformationen, wird eine Meldung im Ausgabeprotokoll ausgegeben.

![Hinzufügen eines nicht aufgelisteten Geräts](images/unreal/add-unlisted-device.png)

7. Wählen Sie erneut den  Dropdownpfeil neben der Schaltfläche Starten aus. Dieses Mal sollte das HoloLens gerät angezeigt werden, das Sie gerade hinzugefügt haben. Wählen Sie das HoloLens aus, das Sie erstellen und auf Ihrem Computer HoloLens.

>[!NOTE]
>Das Erstellen für das Gerät kann das erneute Kompilieren von Shadern (insbesondere bei der ersten Ausführung) umfassen. Dies kann eine Weile dauern. Lassen Sie das Gerät erst in den Ruhezustand, wenn die App ausgeführt wird (möglicherweise müssen Sie es tragen). Andernfalls wird die Shaderkompilierung fehlschlagen!

## <a name="deploying-to-device-via-device-portal"></a>Bereitstellen auf dem Gerät über das Geräteportal

Ausführliche Anweisungen zum Packen und Bereitstellen einer App finden Sie in der [Unreal-Tutorialreihe](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal).

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie die unreal-Entwicklungsreise, die wir festgelegt haben, folgen, sind Sie in der Phase der Bereitstellung. Von hier aus können Sie mit dem Hinzufügen erweiterter Dienste fortfahren:

> [!div class="nextstepaction"]
> [Erweiterte Dienste](unreal-development-overview.md#5-adding-services)

Sie können jederzeit zu den [Prüfpunkten für die Unreal-Entwicklung](unreal-development-overview.md#4-streaming-and-deploying-to-a-device) zurückkehren.
