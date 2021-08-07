---
title: Installationsfehler
description: Advanced Windows Mixed Reality installation error troubleshooting that goes beyond our standard consumer support documentation .
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Problembehandlung, Fehler, Hilfe, Support, Installation
appliesto:
- Windows 10
ms.openlocfilehash: 702e38196ea3fda5cc7595decfeef4c6305ae2274ce6e5740af60c511447506b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213188"
---
# <a name="installation-errors"></a>Installationsfehler

## <a name="your-pc-cant-run-windows-mixed-reality"></a>"Your PC can't run Windows Mixed Reality" (Ihr PC kann nicht Windows Mixed Reality.

Ihr PC erfüllt nicht die [Mindestanforderungen, die zum](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) Ausführen von Windows Mixed Reality. Das Hardwaresetup Ihres Computers ist möglicherweise nicht mit Windows Mixed Reality kompatibel, oder Sie müssen ein Update auf die neueste [Version von Windows.](https://support.microsoft.com/help/12373/windows-update-faq) 

Windows Mixed Reality erfordert einen Grafikkartentreiber, der mindestens WDDM 2.2 unterstützt. Stellen Sie sicher, dass Sie über das neueste Treiberupdate des Herstellers verfügen. Wenn Windows Mixed Reality Setup besagt, dass Ihre Grafikkarte die Anforderungen nicht erfüllt, und Sie denken, dass sie dies tut, stellen Sie sicher, dass Ihr Headset an die richtige Karte angeschlossen ist.

## <a name="youre-nearly-therethis-pc-doesnt-meet-the-minimum-requirements-needed-to-run-windows-mixed-reality"></a>"Sie sind fast dort– dieser PC erfüllt nicht die Mindestanforderungen, die zum Ausführen von Windows Mixed Reality"

Ihr PC erfüllt nicht die [Mindestanforderungen, die für](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) eine optimale Benutzererfahrung in Windows Mixed Reality. Ihr PC kann möglicherweise ein immersives Headset ausführen, aber es können Leistungsprobleme und bestimmte Anwendungen nicht ausgeführt werden.

Windows Mixed Reality erfordert einen Grafikkartentreiber, der mindestens WDDM 2.2 unterstützt. Stellen Sie sicher, dass Sie über das neueste Treiberupdate des Herstellers verfügen. Wenn Windows Mixed Reality Setup besagt, dass Ihre Grafikkarte die Anforderungen nicht erfüllt, und Sie denken, dass sie dies tut, stellen Sie sicher, dass Ihr Headset an die richtige Karte angeschlossen ist.

## <a name="before-we-can-set-up-windows-mixed-reality-your-administrator-will-need-to-enable-it-for-your-organization-learn-more"></a>"Bevor sie eingerichtet Windows Mixed Reality kann, muss Ihr Administrator sie für Ihre Organisation aktivieren. Weitere Informationen"

Sie sind wahrscheinlich in einem vom Unternehmen verwalteten Netzwerk, und Ihre Organisation verwendet Windows Server Update Services (WSUS). Diese und andere Richtlinien, die den Download blockieren können. Wenden Sie sich an die IT-Abteilung oder den Systemadministrator Ihrer Organisation, um [die Windows Mixed Reality.](/windows/application-management/manage-windows-mixed-reality#enable)

## <a name="we-couldnt-download-the-mixed-reality-software-or-hang-tight-while-we-do-some-downloading"></a>"Wir konnten die Mixed Reality-Software nicht herunterladen" oder "Hang tight while we do some downloading"

* Manchmal kann ein ausstehendes Update den Mixed Reality Softwaredownload blockieren. Wechseln Sie **Einstellungen > update & security > Windows Update,** und stellen Sie sicher, Windows Update ein ist. Laden Sie dann alle wartenden Updates herunter, und installieren Sie sie. Wenn Sie einen Fehler Windows Update erhalten, erhalten Sie hier [Hilfe.](https://support.microsoft.com/help/10164/fix-windows-update-errors)
* Stellen Sie sicher, dass Ihr PC mit dem Internet verbunden ist und über mindestens 2 GB freien Speicherplatz verfügt. Überprüfen Sie Den Netzwerkstatus unter Einstellungen > **Netzwerk & Internet > Status**. Wenn Sie keine Verbindung mit dem Internet herstellen können, erhalten Sie hier [Hilfe.](https://support.microsoft.com/help/10741/windows-10-fix-network-connection-issues)  
* Starten Sie Ihren PC neu, und versuchen Sie es erneut. 

Wenn diese Lösungen nicht funktionieren, versuchen Sie:
* Wenn ihre Wi-Fi-Netzwerkverbindung auf ["gemessen" festgelegt](https://support.microsoft.com//help/17452/windows-metered-internet-connections-faq)ist, ändern Sie sie in nicht gemessen. Um eine gemessene Verbindung zu deaktivieren, wechseln Sie zu: **Einstellungen > Network & Internet > Status >** Ändern der Verbindungseigenschaften > Als gemessene Verbindung festlegen, und wählen Sie "Aus" aus.  
* Wenn Sie vor Kurzem ein Update installiert haben, kann dies zu Problemen führen. Es wird nicht empfohlen, installierte Updates zu entfernen, insbesondere Sicherheitsupdates, die den PC schützen. Manchmal kann das Entfernen des neuesten Updates jedoch dabei helfen, die Ursache des Problems zu ermitteln: 
    * Wechseln Sie **zu Einstellungen > Update & Security > View Installed Update History > Uninstall Updates**
    * Wählen Sie das letzte installierte Update und "Deinstallieren" aus.
    * Wenn Sie gefragt werden: "Sind Sie sicher, dass Sie dieses Update deinstallieren möchten?" Antwort "Ja". Wenn beim Versuch dieser Schritte eine Fehlermeldung angezeigt wird, erhalten Sie weitere Informationen zum Beheben von [Windows Update-Fehlern.](https://support.microsoft.com//help/10164/fix-windows-update-errors) 
    * Starten Sie Ihren PC neu, und versuchen Sie es erneut. 
    * Wenn Windows Mixed Reality ordnungsgemäß installiert wird, installieren Sie die neuesten Updates unter **Einstellungen > Windows Update >** Nach Updates suchen neu, und überprüfen Sie, ob Windows Mixed Reality weiterhin funktioniert. Wenn die Installation nicht ordnungsgemäß ist, installieren Sie die Updates neu, und wenden Sie sich an Windows Support. 

## <a name="something-went-wrong-and-we-couldnt-start-windows-mixed-reality"></a>"Etwas ist schief gelaufen, und wir konnten nicht mit der Windows Mixed Reality"
Weitere Informationen zu einem bestimmten Fehlercode finden Sie [hier.](error-codes.md) Sie können auch versuchen, dies zu versuchen:

* Trennen Sie beide Headsetkabel vom PC.
* Starten Sie den PC neu.
* Wechseln Sie **Einstellungen > update & security > Windows Update,** und stellen Sie sicher, dass Windows Update aktiviert ist. Laden Sie alle wartenden Updates herunter, und installieren Sie sie.
* Verbinden Sie Ihr Headset erneut mit dem PC, und versuchen Sie es dann erneut.

Wenn diese Schritte nicht funktionieren, deinstallieren Sie die Anwendung, und installieren Sie Windows Mixed Reality:
* Wechseln Sie zu **Einstellungen > Mixed Reality > Deinstallieren,** und wählen Sie "Deinstallieren" aus. 
* Starten Sie Ihren PC neu. 
* Um den Setupvorgang erneut zu starten, schließen Sie einfach Ihr Headset an Ihren PC an.