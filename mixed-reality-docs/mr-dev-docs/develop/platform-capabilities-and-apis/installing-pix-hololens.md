---
title: Installieren von PIX für HoloLens 2
description: Erfahren Sie, wie Sie PIX für HoloLens 2 Geräte installieren.
author: hferrone
ms.author: flbagar
ms.date: 12/02/2020
ms.topic: article
keywords: HoloLens, HoloLens 2, PIX, Aufnahme, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 2e5e66ea5a1a2b68d91213c38d88d815f54a28fa5328ab3b2d93f1e267f6f994
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217312"
---
# <a name="installing-pix-for-hololens-2"></a>Installieren von PIX für HoloLens 2

[PIX](https://devblogs.microsoft.com/pix) ist ein Tool zur Leistungsoptimierung und zum Debuggen für DirectX 12-Anwendungen auf Windows. 

## <a name="setup"></a>Setup

1. Greifen Sie die neueste [PIX-Version]( https://devblogs.microsoft.com/pix/download) von Ihrem Host-PC ab, und verbinden Sie Ihre HoloLens 2 über ein USB-Kabel mit Ihrem PC.

2. Wenn sich Ihr HoloLens 2 auf einem [Windows Insider-Build](https://insider.windows.com) befindet oder eine Konfiguration aufwies, die PIX unterbricht, [setzen Sie den Schrägstrich ihres Geräts](/hololens/hololens-recovery) so um, dass alle Daten gelöscht werden.

3. Aktivieren Sie **den Entwicklermodus,** und **Geräteportal**:

* Öffnen **Sie Einstellungen** über Mixed Reality Home:

![Screenshot: Menü "HoloLens" mit hervorgehobener Schaltfläche "Einstellungen"](images/pix-img-01.jpg)

* Wählen Sie **Update & Security (Sicherheit aktualisieren)** aus:

![Screenshot: Fenster "Einstellungen" auf HoloLens mit hervorgehobener Schaltfläche "Update" und "Sicherheit"](images/pix-img-02.jpg)

* Wählen Sie **Für Entwickler** aus:

![Screenshot: Fenster "Sicherheit und Updates" mit hervorgehobener Schaltfläche "Für Entwickler" geöffnet](images/pix-img-03.jpg)

* Aktivieren **sie Use Developer Features (Entwicklerfeatures verwenden),** und **aktivieren Sie Geräteportal**

![Screenshot: Fenster "Für Entwickler" in den Einstellungen mit hervorgehobener Schaltfläche "Geräteportal aktivieren" geöffnet](images/pix-img-04.jpg)

![Screenshot: Fenster "Für Entwickler" in den Einstellungen geöffnet, wobei die Umschaltfläche "Entwicklungsfeatures verwenden" hervorgehoben ist](images/pix-img-05.jpg)

* Starten Sie Visual Studio, wenn das Gerät weiterhin verbunden ist, aktiviert ist und der Benutzer angemeldet ist.

> [!IMPORTANT]
> Stellen Sie sicher, dass sich Ihr Gerät nicht im Standbymodus oder im Standbymodus befindet. Wenn Sie Probleme mit diesem Schritt haben, lesen Sie die [anweisungen](./using-the-windows-device-portal.md)Windows Geräteportal .

## <a name="preparing-for-deployment"></a>Vorbereiten der Bereitstellung

1. Legen Sie in Visual Studio **ARM64** als Plattform und **Gerät** als Gerät fest:

![Screenshot der Visual Studio-Projektmappe mit hervorgehobenen Plattform- und Geräteeinstellungen](images/pix-img-06.png)

2. Wenn Visual Studio Sie zur Eingabe einer **PIN** vom Gerät auffordert:

![Screenshot des Visual Studio-Popupfensters, in dem nach PIN gefragt wird](images/pix-img-07.png)

* Auswählen **Einstellungen** in der Shell
* Wählen Sie **Update & Security (Sicherheit aktualisieren)** aus.
* Wählen Sie **Für Entwickler aus,** und klicken Sie unter **Geräteermittlung** auf Paar. 

![Screenshot: Fenster "Für Entwickler" wird in den Einstellungen geöffnet, wobei die Geräteermittlung hervorgehoben ist](images/pix-img-08.jpg)

![Screenshot des Popupfensters für kostenpflichtige Geräte mit hervorgehobener Registrierung](images/pix-img-09.jpg)

* Geben Sie die generierte PIN-Nummer in Visual Studio

3. Visual Studio stellt die App auf dem verbundenen HoloLens 2 bereit, was je nach App einige Minuten dauern kann.

## <a name="launching-pix"></a>Starten von PIX

Verwenden Sie zunächst Geräteportal, um sicherzustellen, dass die App nicht auf dem HoloLens 2 ausgeführt wird. Starten Sie dann PIX, stellen Sie eine Verbindung mit Ihrem Gerät her, und wählen Sie **Start** aus:

![Screenshot des Startbildschirms der PIX-Anwendung](images/pix-img-10.png)

* Wählen Sie im Menü auf der linken Seite **Verbinden** aus:

![Screenshot: Menü auf der linken Seite der PIX-Anwendung mit hervorgehobener Schaltfläche "Verbinden"](images/pix-img-11.png)

2. Wählen Sie auf der Registerkarte **Computer** die Option **Hinzufügen** aus, und geben Sie die folgenden Anmeldeinformationen ein:
    * Alias: Nach Ermessen des Benutzers
    * Hostname oder IP-Adresse: 127.0.0.1

3. Wählen Sie **unten** rechts auf der Registerkarte **Computer** Verbinden aus:

![Screenshot des Fensters "Verbinden" der PIX-Anwendung mit hervorgehobenem Alias, Hostname, IP-Adresse und Schaltfläche "Hinzufügen"](images/pix-img-12.png)

> [!NOTE]
> Die erste Verbindung ist immer langsamer, da Binärdateien kopiert werden.

4. Wenn PIX eine Verbindung mit dem HoloLens 2 hergestellt hat, suchen Sie Ihre App im Abschnitt **Zielprozess auswählen** auf der Registerkarte UWP starten, und wählen Sie **Starten** aus:

![Screenshot der PIX-Anwendung mit hervorgehobener Schaltfläche "Zielprozess auswählen" und "Start"](images/pix-img-13.png)

## <a name="gpu-captured"></a>GPU erfasst

1. Starten Sie die GPU-Erfassung, indem Sie im Abschnitt **GPU-Erfassung** auf **Foto** klicken:

![Screenshot der PIX-Anwendung mit geöffneter PC-Verbindung mit hervorgehobener GPU-Erfassung](images/pix-img-14.png)

2. Öffnen Sie die Erfassung für die Analyse, indem Sie im **Bereich GPU-Erfassung** auf den generierten Screenshot klicken:

![Screenshot der PIX-Anwendung mit geöffneter GPU-Erfassung mit hervorgehobener GPU-Erfassung](images/pix-img-15.png)

3. Drücken **Sie Start,** um mit der Analyse zu beginnen:

![Screenshot der PIX-Anwendung mit hervorgehobener Startschaltfläche](images/pix-img-16.png)

> [!IMPORTANT]
> Wenn Sie Zeitsteuerungsdaten nach einer GPU-Erfassung sammeln, müssen Sie das Headset neu starten. Dies ist ein einmaliger Neustart des Geräts und für die Zeitsteuerung der Datensammlung erforderlich.

PIX ist jetzt einsatzbereit!

## <a name="see-also"></a>Siehe auch
* [PIX-Startseite](https://devblogs.microsoft.com/pix)