---
title: Verteilen von apps
description: Eine Übersicht über die verschiedenen Verteilungs Optionen für verschiedene unterstützte Plattformen und Veröffentlichungs Speicher.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: Hololens, gemischte Realität, immersive Headsets, APP, UWP, einreichen, Übermittlung, Filter, Metadaten, Systemanforderungen, Schlüsselwörter, Wack, Zertifizierung, Paket, AppX, Merchandising
ms.openlocfilehash: b4b82557ba274852ebb3f97058017fa2e5db1c02
ms.sourcegitcommit: 9e9d58de4513655c7daa71ff4b5b2c2b115ab959
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "97034581"
---
# <a name="distributing-your-apps"></a><span data-ttu-id="15405-104">Verteilen von apps</span><span class="sxs-lookup"><span data-stu-id="15405-104">Distributing your apps</span></span>

![Floaty Bird 3D-App-lancher in WMR-Startseite](images/distribute-hero-image.png)

<span data-ttu-id="15405-106">Das Erreichen Ihrer Apps in die Hände Ihrer Benutzer oder der Welt ist der wichtigste und manchmal mühsame Teil eines beliebigen Entwicklungsaufwands.</span><span class="sxs-lookup"><span data-stu-id="15405-106">Getting your apps into the hands of your users or out into the world is the most important, and sometimes painstaking, part of any development effort.</span></span> <span data-ttu-id="15405-107">Wir haben den Prozess in eine Reihe von Ressourcen vereinfacht, die im folgenden aufgeführt sind. diese sind abhängig von dem Verteilungs-und Bereitstellungs Szenario, das für Sie oder Ihr Team am besten geeignet ist.</span><span class="sxs-lookup"><span data-stu-id="15405-107">We've simplified process into a set of resources listed below, all of which depend on the distribution and deployment scenario that's best suited for you or your team.</span></span>

[!INCLUDE[](includes/before-submission.md)]

## <a name="distribution-options"></a><span data-ttu-id="15405-108">Verteilungsoptionen</span><span class="sxs-lookup"><span data-stu-id="15405-108">Distribution options</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="15405-109">Wenn Sie Ihre APP für eine andere Partei freigeben, müssen Sie die AppX-Datei erstellen und bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="15405-109">If you're sharing your app with another party, you need to build and supply the appx file.</span></span> 
>     * <span data-ttu-id="15405-110">Wenn Sie das App-Installationsprogramm verwenden, müssen Sie auch das Zertifikat für den Benutzer freigeben.</span><span class="sxs-lookup"><span data-stu-id="15405-110">If you're using App Installer, you'll also need to share the certificate with the user.</span></span>
> 
> * <span data-ttu-id="15405-111">Wenn Sie die Freigabe für eine Organisation durcharbeiten, benötigen Sie ein Geschäfts-, Schul-oder unikonto und Zugriff auf die [MDM-Infrastruktur (Mobile Device Management)](https://docs.microsoft.com/hololens/hololens-enroll-mdm) der Organisation.</span><span class="sxs-lookup"><span data-stu-id="15405-111">If you're sharing with an organization, you need a work or school account and access to the organizations [MDM (Mobile Device Management)](https://docs.microsoft.com/hololens/hololens-enroll-mdm) infrastructure.</span></span>  
>    * <span data-ttu-id="15405-112">Wenn Sie die Freigabe Partei sind, müssen Sie in Ihrem Mandanten Administrator sein und das [Microsoft Endpoint Manager Admin Center](https://docs.microsoft.com/mem/intune/apps/apps-deploy) verwenden, um die app verfügbar zu machen.</span><span class="sxs-lookup"><span data-stu-id="15405-112">If you're the sharing party, you need to be an Admin in your tenant and use the [Microsoft Endpoint Manager admin center](https://docs.microsoft.com/mem/intune/apps/apps-deploy) to make the app available.</span></span> <span data-ttu-id="15405-113">Eine andere Möglichkeit besteht darin, die AppX-Datei und die APP-Abhängigkeiten für den Endbenutzer freizugeben.</span><span class="sxs-lookup"><span data-stu-id="15405-113">Another option is to share the appx file and the app dependencies with your end user.</span></span>
>    * <span data-ttu-id="15405-114">Wenn Sie der Endbenutzer sind, wird die APP entweder automatisch heruntergeladen oder steht zum Herunterladen zur Verfügung, sobald Sie sich mit dem Mandanten der Freigabe Organisation registrieren.</span><span class="sxs-lookup"><span data-stu-id="15405-114">If you're the end user, the app will either automatically download or be available for download once you enroll with the sharing organization's tenant.</span></span> 

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
    <td><span data-ttu-id="15405-115"><strong>Szenario</strong></span><span class="sxs-lookup"><span data-stu-id="15405-115"><strong>Scenario</strong></span></span></td>
    <td><span data-ttu-id="15405-116"><strong>Lokale Geräteinstallation</strong></span><span class="sxs-lookup"><span data-stu-id="15405-116"><strong>Local device install</strong></span></span></td>
    <td><span data-ttu-id="15405-117"><strong>Für beliebige Personen freigeben</strong></span><span class="sxs-lookup"><span data-stu-id="15405-117"><strong>Share with anyone</strong></span></span></td>
    <td><span data-ttu-id="15405-118"><strong>Freigeben für eine Organisation</strong></span><span class="sxs-lookup"><span data-stu-id="15405-118"><strong>Share with an organization</strong></span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="15405-119"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>APP-Installer</strong></span><span class="sxs-lookup"><span data-stu-id="15405-119"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>App Installer</strong></span></span></td>
    <td><span data-ttu-id="15405-120">✔️</span><span class="sxs-lookup"><span data-stu-id="15405-120">✔️</span></span></td>
    <td><span data-ttu-id="15405-121">✔️</span><span class="sxs-lookup"><span data-stu-id="15405-121">✔️</span></span></td>
    <td>❌</td>
</tr>
<tr>
    <td><span data-ttu-id="15405-122"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>MDM-Unternehmensportal</strong></a></span><span class="sxs-lookup"><span data-stu-id="15405-122"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>MDM - Company Portal</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="15405-123">✔️</span><span class="sxs-lookup"><span data-stu-id="15405-123">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="15405-124"><a href="https://docs.microsoft.com/hololens/app-deploy-intune"><strong>MDM-erforderliche App-Installation</strong></a></span><span class="sxs-lookup"><span data-stu-id="15405-124"><a href="https://docs.microsoft.com/hololens/app-deploy-intune"><strong>MDM - Required App Install</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="15405-125">✔️</span><span class="sxs-lookup"><span data-stu-id="15405-125">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="15405-126"><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></span><span class="sxs-lookup"><span data-stu-id="15405-126"><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></span></span></td>
    <td>❌</td>
    <td><span data-ttu-id="15405-127">✔️</span><span class="sxs-lookup"><span data-stu-id="15405-127">✔️</span></span></td>
    <td><span data-ttu-id="15405-128">✔️</span><span class="sxs-lookup"><span data-stu-id="15405-128">✔️</span></span></td><span data-ttu-id="15405-129">s</span><span class="sxs-lookup"><span data-stu-id="15405-129">s</span></span>
</tr>
<tr>
    <td><span data-ttu-id="15405-130"><a href="https://docs.microsoft.com/hololens/app-deploy-store-business"><strong>Microsoft Store für Unternehmen</strong></a></span><span class="sxs-lookup"><span data-stu-id="15405-130"><a href="https://docs.microsoft.com/hololens/app-deploy-store-business"><strong>Microsoft Store for Business</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="15405-131">✔️</span><span class="sxs-lookup"><span data-stu-id="15405-131">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="15405-132"><a href="https://docs.microsoft.com/hololens/app-deploy-provisioning-package"><strong>Bereitstellungs Paket</strong></a></span><span class="sxs-lookup"><span data-stu-id="15405-132"><a href="https://docs.microsoft.com/hololens/app-deploy-provisioning-package"><strong>Provisioning Package</strong></a></span></span></td>
    <td><span data-ttu-id="15405-133">✔️</span><span class="sxs-lookup"><span data-stu-id="15405-133">✔️</span></span></td>
    <td><span data-ttu-id="15405-134">✔️</span><span class="sxs-lookup"><span data-stu-id="15405-134">✔️</span></span></td>
    <td><span data-ttu-id="15405-135">✔️</span><span class="sxs-lookup"><span data-stu-id="15405-135">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="15405-136"><a href="#additional-scenarios"><strong>Benutzerdefinierte Win32-Bereitstellung</strong></a> (für hololens-Geräte nicht verfügbar-siehe unten)</span><span class="sxs-lookup"><span data-stu-id="15405-136"><a href="#additional-scenarios"><strong>Custom Win32 deployment</strong></a> (Not available for HoloLens devices - see below)</span></span></td>
    <td><span data-ttu-id="15405-137">✔️</span><span class="sxs-lookup"><span data-stu-id="15405-137">✔️</span></span></td>
    <td><span data-ttu-id="15405-138">✔️</span><span class="sxs-lookup"><span data-stu-id="15405-138">✔️</span></span></td>
    <td>❌</td>
</tr>
</table>

> [!IMPORTANT]
> <span data-ttu-id="15405-139">Der APP-Installer ist zurzeit nicht für verwaltete Geräte oder hololens (1. Gen)-Geräte verfügbar.</span><span class="sxs-lookup"><span data-stu-id="15405-139">App Installer isn't currently available for managed devices or HoloLens (1st Gen) devices.</span></span>

## <a name="additional-scenarios"></a><span data-ttu-id="15405-140">Zusätzliche Szenarien</span><span class="sxs-lookup"><span data-stu-id="15405-140">Additional scenarios</span></span>

* <span data-ttu-id="15405-141">Für die Bereitstellung von Win32-Anwendungen, einschließlich "Steam" und "Game Pass", können Sie eine Win32- EXE-Datei, die das eigenständige PC-Buildziel von Unity verwendet und ihre apps so normal an die ausgewählte Plattform sendet.</span><span class="sxs-lookup"><span data-stu-id="15405-141">For Win32 application deployment, including Steam and Game Pass, you can produce a Win32 .EXE file using the PC Standalone build target from Unity and submit your apps as normal to your chosen platform.</span></span> 

* <span data-ttu-id="15405-142">Wenn Sie eine "hololens 2"-Anwendung installieren müssen, während Sie offline sind, lesen Sie die Anweisungen im [Offline-Secure hololens 2](https://docs.microsoft.com/hololens/hololens-common-scenarios-offline-secure) , oder instanzieren Sie die APP über ein Bereitstellungs Paket, ohne den Entwicklermodus zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="15405-142">If you need to install a HoloLens 2 application while you're offline, refer to the [offline secure HoloLens 2](https://docs.microsoft.com/hololens/hololens-common-scenarios-offline-secure) instructions or instal the app through a Provisioning Package without enabling developer mode.</span></span>

* <span data-ttu-id="15405-143">Sie können auch Builds auf Ihrem Gerät bereitstellen und für andere Entwickler freigeben, bei denen der Entwicklermodus aktiviert ist, indem Sie [Visual Studio bereitstellen und Debuggen](../develop/platform-capabilities-and-apis/using-visual-studio.md) oder [ein Anwendungspaket mit dem Geräte Portal installieren](https://docs.microsoft.com/hololens/holographic-custom-apps#installing-an-application-package-with-the-device-portal).</span><span class="sxs-lookup"><span data-stu-id="15405-143">You can also deploy builds to your device and share them with other developers who have Developer Mode enabled by [deploying and debugging with Visual Studio](../develop/platform-capabilities-and-apis/using-visual-studio.md) or [installing an application package with the Device Portal](https://docs.microsoft.com/hololens/holographic-custom-apps#installing-an-application-package-with-the-device-portal).</span></span>

## <a name="see-also"></a><span data-ttu-id="15405-144">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="15405-144">See also</span></span>
* [<span data-ttu-id="15405-145">Suchen, installieren und Deinstallieren von Anwendungen über die Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="15405-145">Finding, installing, and uninstalling applications from the Microsoft Store</span></span>](https://docs.microsoft.com/hololens/holographic-store-apps)

