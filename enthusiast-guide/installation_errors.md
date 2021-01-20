---
title: Installationsfehler
description: Erweiterte Problembehandlung bei der Installation von Windows Mixed Reality, die über die standardmäßige Kundensupport Dokumentation hinausgeht.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, Mr, Problembehandlung, Fehler, Hilfe, Support, Installation
appliesto:
- Windows 10
ms.openlocfilehash: 056caca0b7e562007178929d4a59c2faeaece450
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581662"
---
# <a name="installation-errors"></a>Installationsfehler

## <a name="your-pc-cant-run-windows-mixed-reality"></a>"Ihr PC kann Windows Mixed Reality nicht ausführen"

Der PC erfüllt nicht die [Mindestanforderungen](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) für die Durchführung von Windows Mixed Reality. Die Hardware Einrichtung Ihres Computers ist möglicherweise nicht kompatibel mit Windows Mixed Reality, oder Sie müssen möglicherweise ein [Update auf die neueste Version von Windows](https://support.microsoft.com/help/12373/windows-update-faq)durchgehen. 

Für Windows Mixed Reality ist ein Grafikkartentreiber erforderlich, der mindestens WDDM 2,2 unterstützt. Stellen Sie sicher, dass Sie über das neueste Treiberupdate des Herstellers verfügen. Wenn das Setup von Windows Mixed Reality besagt, dass Ihre Grafikkarte die Anforderungen nicht erfüllt, und Sie meinen, dass das Headset an die richtige Karte angeschlossen ist.

## <a name="youre-nearly-therethis-pc-doesnt-meet-the-minimum-requirements-needed-to-run-windows-mixed-reality"></a>"Sie sind fast da – dieser PC erfüllt nicht die Mindestanforderungen für die Durchführung von Windows Mixed Reality".

Ihr PC erfüllt nicht die [Mindestanforderungen](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) , die für die bestmögliche Verwendung in Windows Mixed Reality erforderlich sind. Ihr PC ist möglicherweise in der Lage, ein immersives Headset auszuführen, kann jedoch Leistungsprobleme haben und nicht in der Lage sein, bestimmte Anwendungen auszuführen.

Für Windows Mixed Reality ist ein Grafikkartentreiber erforderlich, der mindestens WDDM 2,2 unterstützt. Stellen Sie sicher, dass Sie über das neueste Treiberupdate des Herstellers verfügen. Wenn das Setup von Windows Mixed Reality besagt, dass Ihre Grafikkarte die Anforderungen nicht erfüllt, und Sie meinen, dass das Headset an die richtige Karte angeschlossen ist.

## <a name="before-we-can-set-up-windows-mixed-reality-your-administrator-will-need-to-enable-it-for-your-organization-learn-more"></a>"Bevor Sie Windows Mixed Reality einrichten können, muss Ihr Administrator es für Ihre Organisation aktivieren. Weitere Informationen "

Sie befinden sich wahrscheinlich in einem vom Unternehmen verwalteten Netzwerk, und Ihre Organisation verwendet Windows Server Update Services (WSUS). Diese und andere Richtlinien, die den Download blockieren können. Wenden Sie sich an die IT-Abteilung oder den Systemadministrator Ihrer Organisation, um [Windows Mixed Reality zu aktivieren](/windows/application-management/manage-windows-mixed-reality#enable).

## <a name="we-couldnt-download-the-mixed-reality-software-or-hang-tight-while-we-do-some-downloading"></a>"Wir konnten die Mixed-Reality-Software nicht herunterladen

* Manchmal kann ein ausstehendes Update den gemischten Reality-Software Download blockieren. Wechseln Sie zu **Einstellungen > aktualisieren Sie & Sicherheits > Windows Update** , und stellen Sie sicher, dass Windows Update auf on. Anschließend können Sie alle wartenden Updates herunterladen und installieren. Wenn Sie einen Windows Update Fehler erhalten, erhalten Sie [hier](https://support.microsoft.com/help/10164/fix-windows-update-errors)Hilfe.
* Stellen Sie sicher, dass Ihr PC mit dem Internet verbunden ist und über mindestens 2 GB freien Speicherplatz verfügt. Überprüfen Sie den Netzwerkstatus unter: **Einstellungen > Netzwerk & Internet > Status**. Wenn Sie keine Verbindung mit dem Internet herstellen können, erhalten Sie [hier](https://support.microsoft.com/help/10741/windows-10-fix-network-connection-issues)Hilfe.  
* Starten Sie den PC neu, und versuchen Sie es erneut. 

Wenn diese Lösungen nicht funktionieren, versuchen Sie Folgendes:
* Wenn die Wi-Fi Netzwerkverbindung auf "getaktet" festgelegt ist, ändern Sie Sie in " [nicht gemessen"](https://support.microsoft.com//help/17452/windows-metered-internet-connections-faq). Wechseln Sie zum Deaktivieren einer getakteten Verbindung zu **Einstellungen > Netzwerk & Internet > Status > Verbindungs Eigenschaften ändern > als** getaktete Verbindung festlegen, und wählen Sie "aus".  
* Wenn Sie vor kurzem ein Update installiert haben, kann dies zu Problemen führen. Es wird nicht empfohlen, installierte Updates zu entfernen, insbesondere Sicherheitsupdates, die Ihren PC sicher halten. Manchmal kann es jedoch hilfreich sein, das aktuellste Update zu entfernen, um die Ursache des Problems zu bestimmen: 
    * Wechseln Sie zu **Einstellungen > aktualisieren Sie & Sicherheit > den installierten Update Verlauf anzeigen > Updates deinstallieren** .
    * Wählen Sie das zuletzt installierte Update aus, und deinstallieren Sie es.
    * Wenn Sie gefragt werden, ob Sie dieses Update deinstallieren möchten? Antworten Sie auf "Ja". Wenn Sie eine Fehlermeldung erhalten, wenn Sie diese Schritte ausführen, finden Sie weitere Informationen zum [Beheben von Windows Update-Fehlern](https://support.microsoft.com//help/10164/fix-windows-update-errors). 
    * Starten Sie den PC neu, und versuchen Sie es erneut. 
    * Wenn Windows Mixed Reality ordnungsgemäß installiert wird, installieren Sie die neuesten Updates unter **Einstellungen > Windows Update > nach Updates suchen, und prüfen Sie** , ob Windows Mixed Reality weiterhin funktionsfähig ist. Wenn die Installation nicht korrekt ist, installieren Sie die Updates, und wenden Sie sich an den Windows-Support. 

## <a name="something-went-wrong-and-we-couldnt-start-windows-mixed-reality"></a>"Es ist ein Fehler aufgetreten, und wir konnten Windows Mixed Reality nicht starten"
Weitere Informationen zu einem bestimmten Fehlercode finden Sie [hier](error-codes.md). Sie können auch versuchen, Folgendes auszuführen:

* Entfernen Sie beide Headset-Kabel vom PC.
* Starten Sie den PC neu.
* Wechseln Sie zu **Einstellungen > aktualisieren Sie & Sicherheits > Windows Update** , und stellen Sie sicher, dass Windows Update aktiviert ist. Laden Sie alle wartenden Updates herunter, und installieren Sie Sie.
* Stellen Sie erneut eine Verbindung mit dem PC her, und wiederholen Sie dann das Setup.

Wenn diese Schritte nicht funktionieren, deinstallieren Sie Windows Mixed Reality, und installieren Sie es neu:
* Wechseln Sie zu **Einstellungen > gemischte Realität > deinstallieren** , und wählen Sie "deinstallieren" aus. 
* Starten Sie Ihren PC neu. 
* Wenn Sie den Setup Vorgang erneut starten möchten, können Sie Ihr Headset einfach an Ihren PC anschließen.