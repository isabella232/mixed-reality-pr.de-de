---
title: Verteilen von apps
description: Eine Übersicht über die verschiedenen Verteilungs Optionen für verschiedene unterstützte Plattformen und Veröffentlichungs Speicher.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: Hololens, gemischte Realität, immersive Headsets, APP, UWP, einreichen, Übermittlung, Filter, Metadaten, Systemanforderungen, Schlüsselwörter, Wack, Zertifizierung, Paket, AppX, Merchandising
ms.openlocfilehash: b729bd65413587d3ad3b05bef495349b60a6fffd
ms.sourcegitcommit: 47a5c86b4694449c825902631777a9962a40e332
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98215975"
---
# <a name="distributing-your-apps"></a>Verteilen von apps

![Floaty Bird 3D-App-lancher in WMR-Startseite](images/distribute-hero-image.png)

Das Erreichen Ihrer Apps in die Hände Ihrer Benutzer oder der Welt ist der wichtigste und manchmal mühsame Teil eines beliebigen Entwicklungsaufwands. Wir haben den Prozess in eine Reihe von Ressourcen vereinfacht, die von dem Verteilungs-und Bereitstellungs Szenario abhängig sind, das für Sie oder Ihr Team am besten geeignet ist.

[!INCLUDE[](includes/before-submission.md)]

## <a name="distribution-options"></a>Verteilungsoptionen

> [!IMPORTANT]
> * Wenn Sie Ihre APP für eine andere Partei freigeben, müssen Sie die AppX-Datei erstellen und bereitstellen. 
>     * Wenn Sie das App-Installationsprogramm verwenden, müssen Sie auch das Zertifikat für den Benutzer freigeben.
> 
> * Wenn Sie die Freigabe für eine Organisation durcharbeiten, benötigen Sie ein Geschäfts-, Schul-oder unikonto und Zugriff auf die [MDM-Infrastruktur (Mobile Device Management)](https://docs.microsoft.com/hololens/hololens-enroll-mdm) der Organisation.  
>    * Wenn Sie die Freigabe Partei sind, müssen Sie in Ihrem Mandanten Administrator sein und das [Microsoft Endpoint Manager Admin Center](https://docs.microsoft.com/mem/intune/apps/apps-deploy) verwenden, um die app verfügbar zu machen. Eine andere Möglichkeit besteht darin, die AppX-Datei und die APP-Abhängigkeiten für den Endbenutzer freizugeben.
>    * Wenn Sie der Endbenutzer sind, wird die APP entweder automatisch heruntergeladen oder steht zum Herunterladen zur Verfügung, sobald Sie sich mit dem Mandanten der Freigabe Organisation registrieren. 

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
    <td><strong>Szenario</strong></td>
    <td><strong>Lokale Geräte Installationen</strong></td>
    <td><strong>Für beliebige Personen freigeben</strong></td>
    <td><strong>Freigeben für eine Organisation</strong></td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>APP-Installer</strong></td>
    <td>✔️</td>
    <td>✔️</td>
    <td>❌</td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>MDM-Unternehmensportal</strong></a></td>
    <td>❌</td>
    <td>❌</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-intune"><strong>MDM-erforderliche App-Installation</strong></a></td>
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
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-store-business"><strong>Microsoft Store für Unternehmen</strong></a></td>
    <td>❌</td>
    <td>❌</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-provisioning-package"><strong>Bereitstellungs Paket</strong></a></td>
    <td>✔️</td>
    <td>✔️</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="#other-scenarios"><strong>Benutzerdefinierte Win32-Bereitstellung</strong></a> (für hololens-Geräte nicht verfügbar-siehe unten)</td>
    <td>✔️</td>
    <td>✔️</td>
    <td>❌</td>
</tr>
</table>

> [!IMPORTANT]
> Der APP-Installer ist zurzeit nicht für verwaltete Geräte oder hololens (1. Gen)-Geräte verfügbar.

## <a name="other-scenarios"></a>Andere Szenarien

* Sie können eine Win32-. EXE-Datei mit dem eigenständigen PC-Buildziel von Unity für die Win32-Anwendungs Bereitstellung, einschließlich Steam und Game Pass. Sobald Sie über das verfügen. EXE, Sie können Ihre apps normal an die ausgewählte Plattform übermitteln. 

* Wenn Sie eine "hololens 2"-Anwendung installieren müssen, während Sie offline sind, lesen Sie die Anweisungen im [Offline-Secure hololens 2](https://docs.microsoft.com/hololens/hololens-common-scenarios-offline-secure) , oder installieren Sie die APP über ein Bereitstellungs Paket, ohne den Entwicklermodus zu aktivieren.

* Sie können auch Builds auf Ihrem Gerät bereitstellen und für andere Entwickler freigeben, bei denen der Entwicklermodus aktiviert ist, indem Sie [Visual Studio bereitstellen und Debuggen](../develop/platform-capabilities-and-apis/using-visual-studio.md) oder [ein Anwendungspaket mit dem Geräte Portal installieren](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#sideloading-applications).

## <a name="see-also"></a>Siehe auch
* [Suchen, installieren und Deinstallieren von Anwendungen über die Microsoft Store](https://docs.microsoft.com/hololens/holographic-store-apps)

