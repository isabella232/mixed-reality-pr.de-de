---
title: Installieren von PIX für HoloLens 2
description: Erfahren Sie, wie Sie pix für hololens 2-Geräte installieren.
author: hferrone
ms.author: flbagar
ms.date: 12/02/2020
ms.topic: article
keywords: Hololens, hololens 2, pix, Capture, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 5dfc16f97790b47af3c24ca44c060a9a2495a320
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530443"
---
# <a name="installing-pix-for-hololens-2"></a>Installieren von PIX für HoloLens 2

[Pix](https://devblogs.microsoft.com/pix) ist ein Tool zur Leistungsoptimierung und-Debuggen für DirectX 12-Anwendungen unter Windows. 

## <a name="setup"></a>Einrichten

1. Holen Sie sich die neueste pix- [Version]( https://devblogs.microsoft.com/pix/download) von Ihrem Host-PC, und verbinden Sie Ihre hololens 2 über ein USB-Kabel mit Ihrem PC.

2. Wenn sich Ihre hololens 2 in einem [Windows Insider-Build](https://insider.windows.com) befinden oder über eine Konfiguration verfügen, die pix unterbricht, löschen  [Sie Ihr Gerät](https://docs.microsoft.com/hololens/hololens-recovery) , um alle Daten zu löschen.

3. **Entwicklermodus** und **Geräte Portal** aktivieren:

* Öffnen Sie die **Einstellungen** in der Shell:

![Screenshot des Menüs "hololens" mit hervorgehobener Einstellungs Schaltfläche](images/pix-img-01.jpg)

* Wählen Sie **Update & Sicherheit**:

![Screenshot des Fensters "Einstellungen" in hololens mit hervorgehobener Schaltfläche "aktualisieren und Sicherheit"](images/pix-img-02.jpg)

* Wählen Sie **für Entwickler**:

![Screenshot der Schaltfläche "Sicherheit und Updates" mit hervorgehobener Schaltfläche "Entwickler"](images/pix-img-03.jpg)

* Aktivieren der **Verwendung von Entwickler Features** und **Aktivieren des Geräte Portals**

![Screenshot des Fensters "Entwickler" in den Einstellungen "Geräte Portal aktivieren"](images/pix-img-04.jpg)

![Screenshot des Fensters "Entwickler" in "Einstellungen" mit der Schaltfläche "entwickeln von Features umschalten"](images/pix-img-05.jpg)

* Starten Sie Visual Studio, wenn das Gerät immer noch verbunden ist, aktiv ist und der Benutzer angemeldet ist.

> [!IMPORTANT]
> Stellen Sie sicher, dass sich Ihr Gerät nicht im Standbymodus befindet oder nicht Wenn Sie Probleme mit diesem Schritt haben, finden Sie die [Anweisungen im Windows-Geräte Portal](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal).

## <a name="preparing-for-deployment"></a>Vorbereiten der Bereitstellung

1. Legen Sie in Visual Studio **ARM64** als Plattform und **Gerät** als Gerät fest:

![Screenshot der Visual Studio-Projekt Mappe mit hervorgehobenen Plattform-und Geräteeinstellungen](images/pix-img-06.png)

2. Wenn Sie von Visual Studio aufgefordert werden, eine **Pin** vom Gerät einzugeben:

![Screenshot der Visual Studio-Popup-Aufforderung zur PIN](images/pix-img-07.png)

* Auswählen von **Einstellungen** aus der Shell
* Wählen Sie **Update & Sicherheit** aus.
* Wählen Sie **für Entwickler aus** , und klicken Sie unter **Geräte** Ermittlung auf paar 

![Screenshot von für Entwickler Fenster "in Einstellungen öffnen" mit hervorgehobener Geräte Ermittlung](images/pix-img-08.jpg)

![Screenshot des Popups für kostenpflichtige Geräte mit hervorgehobenem Registrierungscode](images/pix-img-09.jpg)

* Geben Sie die generierte PIN-Nummer in Visual Studio ein.

3. Visual Studio stellt die app in den verbundenen hololens 2 bereit. Dies kann je nach App einige Minuten dauern.

## <a name="launching-pix"></a>Starten von Pix

Überprüfen Sie zunächst mithilfe des Geräte Portals, ob die APP auf den hololens 2 ausgeführt wird. Starten Sie dann pix, stellen Sie eine Verbindung mit Ihrem Gerät her, und wählen Sie **Startseite**:

![Screenshot des pix-Anwendungs-Startbildschirms](images/pix-img-10.png)

* Wählen Sie im Menü auf der linken Seite die Option **verbinden** aus:

![Screenshot des linksseitigen Menüs der PIX-Anwendung mit hervorgehobener Schaltfläche "verbinden"](images/pix-img-11.png)

2. Klicken Sie auf der Registerkarte **Computer** auf **Hinzufügen**, und geben Sie die folgenden Anmelde Informationen ein:
    * Alias: der Ermessen des Benutzers
    * Hostname oder IP-Adresse: 127.0.0.1

3. Wählen Sie in der unteren rechten Ecke der Registerkarte **Computer** die Option **verbinden** aus:

![Screenshot des pix-Anwendungs Verbindungs Fensters mit hervorgehobenem Alias, Hostname, IP-Adresse und Schaltfläche "hinzufügen"](images/pix-img-12.png)

> [!NOTE]
> Die erste Verbindung ist immer langsamer, da Binärdateien kopiert werden.

4. Wenn pix mit den hololens 2 verbunden ist, suchen Sie Ihre APP im Abschnitt **Ziel Prozess auswählen** auf der Registerkarte "UWP starten", und wählen Sie " **starten**" aus:

![Screenshot der PIX-Anwendung mit hervorgehobenem Ziel Prozessfenster auswählen und Start Schaltfläche](images/pix-img-13.png)

## <a name="gpu-captured"></a>GPU aufgezeichnet

1. Starten Sie die GPU-Erfassung, indem Sie im Abschnitt **GPU-Erfassung** auf **Foto** klicken:

![Screenshot der PIX-Anwendung, bei der der PC-Verbindungsbereich geöffnet ist und GPU-Erfassung hervorgehoben ist](images/pix-img-14.png)

2. Öffnen Sie die Erfassung für die Analyse, indem Sie im GPU- **Erfassungs** Bereich auf den generierten Screenshot klicken:

![Screenshot der PIX-Anwendung mit hervorgehobenem GPU-Erfassungsbereich mit hervorgehobenem GPU-Erfassungsbereich](images/pix-img-15.png)

3. Klicken Sie auf starten, um die Analyse zu **starten** :

![Screenshot der PIX-Anwendung mit hervorgehobener Schaltfläche "Start"](images/pix-img-16.png)

> [!IMPORTANT]
> Wenn Sie Zeit Steuerungsdaten sammeln, nachdem Sie eine GPU-Erfassung durch genommen haben, müssen Sie das Headset neu starten. Hierbei handelt es sich um einen einmaligen Neustart des Geräts, der für die Erfassung von Zeit Steuerungsdaten erforderlich ist.

PIX ist jetzt einsatzbereit!

## <a name="see-also"></a>Weitere Informationen
* [Pix-Homepage](https://devblogs.microsoft.com/pix)