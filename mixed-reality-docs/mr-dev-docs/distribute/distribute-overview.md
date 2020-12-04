---
title: Verteilen von apps
description: Eine Übersicht über die verschiedenen Verteilungs Optionen für verschiedene unterstützte Plattformen und Veröffentlichungs Speicher.
author: hferrone
ms.author: v-hferrone
ms.date: 10/02/2020
ms.topic: article
keywords: Hololens, gemischte Realität, immersive Headsets, APP, UWP, einreichen, Übermittlung, Filter, Metadaten, Systemanforderungen, Schlüsselwörter, Wack, Zertifizierung, Paket, AppX, Merchandising
ms.openlocfilehash: 4ea60d2111f99924eaa417d4ff6fa8830934588c
ms.sourcegitcommit: 9c640c96e2270ef69edd46f1b12acb00b373554d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2020
ms.locfileid: "96578879"
---
# <a name="distributing-your-apps"></a>Verteilen von apps

![Floaty Bird 3D-App-lancher in WMR-Startseite](images/distribute-hero-image.png)

Das Erreichen Ihrer Apps in die Hände Ihrer Benutzer oder der Welt ist der wichtigste und manchmal mühsame Teil eines beliebigen Entwicklungsaufwands. Wir haben den Prozess in eine Reihe von Ressourcen vereinfacht, die im folgenden aufgeführt sind. diese sind abhängig von dem Verteilungs-und Bereitstellungs Szenario, das für Sie oder Ihr Team am besten geeignet ist.

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
    <td><strong>Lokale Geräteinstallation</strong></td>
    <td><strong>Für beliebige Personen freigeben</strong></td>
    <td><strong>Freigeben für eine Organisation</strong></td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>APP-Installer</strong></a> (über <a href="https://docs.microsoft.com/hololens/hololens-insider">Windows Insider-Builds</a>)</td>
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
    <td><a href="#additional-scenarios"><strong>Benutzerdefinierte Win32-Bereitstellung</strong></a> (für hololens-Geräte nicht verfügbar-siehe unten)</td>
    <td>✔️</td>
    <td>✔️</td>
    <td>❌</td>
</tr>
</table>

> [!IMPORTANT]
> Der APP-Installer ist zurzeit nicht für verwaltete Geräte oder hololens (1. Gen)-Geräte verfügbar.

## <a name="additional-scenarios"></a>Zusätzliche Szenarien

* Für die Bereitstellung von Win32-Anwendungen, einschließlich "Steam" und "Game Pass", können Sie eine Win32- EXE-Datei, die das eigenständige PC-Buildziel von Unity verwendet und ihre apps so normal an die ausgewählte Plattform sendet. 

* Wenn Sie eine "hololens 2"-Anwendung installieren müssen, während Sie offline sind, lesen Sie die Anweisungen im [Offline-Secure hololens 2](https://docs.microsoft.com/hololens/hololens-common-scenarios-offline-secure) , oder instanzieren Sie die APP über ein Bereitstellungs Paket, ohne den Entwicklermodus zu aktivieren.

* Sie können auch Builds auf Ihrem Gerät bereitstellen und für andere Entwickler freigeben, bei denen der Entwicklermodus aktiviert ist, indem Sie [Visual Studio bereitstellen und Debuggen](../develop/platform-capabilities-and-apis/using-visual-studio.md) oder [ein Anwendungspaket mit dem Geräte Portal installieren](https://docs.microsoft.com/hololens/holographic-custom-apps#installing-an-application-package-with-the-device-portal).

## <a name="see-also"></a>Siehe auch
* [Suchen, installieren und Deinstallieren von Anwendungen über die Microsoft Store](https://docs.microsoft.com/hololens/holographic-store-apps)

<!-- ## Submitting to the Microsoft Store

You've finally made it to the last step on your distribution journey, actually getting your app into the Microsoft Store! Our [submission guidelines](submitting-an-app-to-the-microsoft-store.md) article will take you through: 

* Partner Center registration 
* Asset preparation
* App packaging
* Testing
* Final submission process

You can even give out free trials to get future consumers excited about your new immersive experience. Once your app is listed on the Microsoft Store you can sit back, engage with your expanding user community, and think about all the new features you want to add! -->
