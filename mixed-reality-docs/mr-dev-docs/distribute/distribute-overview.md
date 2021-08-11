---
title: Verteilen Ihrer Apps
description: Eine Übersicht über die verschiedenen Verteilungsoptionen für verschiedene unterstützte Plattformen und Veröffentlichungsspeicher.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: HoloLens, Mixed Reality, immersive Headsets, App, UWP, Übermitteln, Übermitteln, Filter, Metadaten, Systemanforderungen, Schlüsselwörter, Wack, Zertifizierung, Paket, Appx, Zertifikat
ms.openlocfilehash: 7d4fbc1a7a5767ad8276017c7cdc38e9bb436bc83b12a4d8caeb9a8d84f1caca
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198784"
---
# <a name="distributing-your-apps"></a>Verteilen Ihrer Apps

![Floaty bird 3D app lancher in WMR home](images/distribute-hero-image.png)

Ihre Apps in die Hände Ihrer Benutzer oder in die Welt zu bekommen, ist der wichtigste und manchmal mühsamste Teil jedes Entwicklungsaufwands. Wir haben den Prozess in eine Reihe von Ressourcen vereinfacht, die vom Verteilungs- und Bereitstellungsszenario abhängen, das für Sie oder Ihr Team am besten geeignet ist.

[!INCLUDE[](includes/before-submission.md)]

## <a name="distribution-options"></a>Verteilungsoptionen

> [!IMPORTANT]
> * Wenn Sie Ihre App für eine andere Partei freigeben, müssen Sie die AppX-Datei erstellen und liefern. 
>     * Wenn Sie die App-Installer, müssen Sie das Zertifikat auch für den Benutzer freigeben.
> 
> * Wenn Sie die Freigabe für eine Organisation erstellen, benötigen Sie ein Arbeits- oder Schulkonto und Zugriff auf die [MDM-Infrastruktur (Mobile Geräteverwaltung).](/hololens/hololens-enroll-mdm)  
>    * Wenn Sie die Freigabestelle sind, müssen Sie Administrator in Ihrem Mandanten sein und das [Microsoft Endpoint Manager Admin Center](/mem/intune/apps/apps-deploy) verwenden, um die App verfügbar zu machen. Eine weitere Möglichkeit besteht in der Freigabe der AppX-Datei und der App-Abhängigkeiten für Ihren Endbenutzer.
>    * Wenn Sie der Endbenutzer sind, wird die App entweder automatisch heruntergeladen oder steht zum Download zur Verfügung, sobald Sie sich beim Mandanten der Freigabeorganisation registrieren. 

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
    <td><strong>Szenario</strong></td>
    <td><strong>Installationen lokaler Geräte</strong></td>
    <td><strong>Freigeben für alle</strong></td>
    <td><strong>Freigeben für eine Organisation</strong></td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>App-Installer</strong></td>
    <td>✔️</td>
    <td>✔️</td>
    <td>❌</td>
</tr>
<tr>
    <td><a href="/hololens/app-deploy-app-installer"><strong>MDM – Unternehmensportal</strong></a></td>
    <td>❌</td>
    <td>❌</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="/hololens/app-deploy-intune"><strong>MDM: Erforderliche App-Installation</strong></a></td>
    <td>❌</td>
    <td>❌</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></td>
    <td>❌</td>
    <td>✔️</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="/hololens/app-deploy-store-business"><strong>Microsoft Store für Unternehmen</strong></a></td>
    <td>❌</td>
    <td>❌</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="/hololens/app-deploy-provisioning-package"><strong>Bereitstellungspaket</strong></a></td>
    <td>✔️</td>
    <td>✔️</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="#other-scenarios"><strong>Benutzerdefinierte Win32-Bereitstellung</strong></a> (nicht für HoloLens verfügbar – siehe unten)</td>
    <td>✔️</td>
    <td>✔️</td>
    <td>❌</td>
</tr>
</table>

> [!IMPORTANT]
> App-Installer ist derzeit nicht für verwaltete Geräte oder HoloLens (1. Generation) verfügbar.

## <a name="other-scenarios"></a>Andere Szenarien

* Sie können eine Win32-.EXE erstellen, indem Sie das eigenständige PC-Buildziel von Unity für die Win32-Anwendungsbereitstellung verwenden, einschließlich "Steam" und "Game Pass. Sobald Sie über die .EXE verfügen, können Sie Ihre Apps wie gewohnt an Die ausgewählte Plattform übermitteln. 

* Wenn Sie eine HoloLens 2-Anwendung installieren müssen, während Sie offline sind, lesen Sie die Offlineanweisungen für sichere [HoloLens 2,](/hololens/hololens-common-scenarios-offline-secure) oder installieren Sie die App über ein Bereitstellungspaket, ohne den Entwicklermodus zu aktivieren.

* Sie können builds auch auf Ihrem Gerät bereitstellen und für andere Entwickler freigeben, für die der Entwicklermodus aktiviert [ist,](../develop/platform-capabilities-and-apis/using-visual-studio.md) indem Sie mit Visual Studio bereitstellen und debuggen oder ein Anwendungspaket mit dem [Geräteportal.](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#sideloading-applications)

## <a name="see-also"></a>Siehe auch
* [Suchen, Installieren und Deinstallieren von Anwendungen im Microsoft Store](/hololens/holographic-store-apps)