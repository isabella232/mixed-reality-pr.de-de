---
title: MRTK-Buildfenster
description: Dokumentation zur Verwendung des Buildfensters in MRTK für Unity.
author: cre8ivepark
ms.author: dongpark
ms.date: 04/06/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Build, Buildfenster, Tools
ms.openlocfilehash: 00ccbc5cfbb3b034771585a1263c624309b08465
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196853"
---
# <a name="build-window"></a><span data-ttu-id="21556-104">Fenster „Build“ (Erstellen)</span><span class="sxs-lookup"><span data-stu-id="21556-104">Build window</span></span>
![Erstellen & Bereitstellungsablauf](images/MRTK_BuildWindow0.png)

<span data-ttu-id="21556-106">Mit dem Buildfenster des MRTK können Sie ganz einfach & Ihre MRTK-Unity bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="21556-106">MRTK's build window make it easy to build & deploy your MRTK-Unity projects.</span></span> <span data-ttu-id="21556-107">Mit einem einzigen Klick auf eine Schaltfläche können Sie ein Unity-Projekt erstellen und Visual Studio generieren(. SLN), UWP-App-Paket(. APPX), und installieren Sie das App-Paket auf dem Gerät.</span><span class="sxs-lookup"><span data-stu-id="21556-107">With a single button click, you can build Unity project and generate Visual Studio solution(.SLN), UWP App package(.APPX), and install the app package on the device.</span></span> 


## <a name="unity-build-options"></a><span data-ttu-id="21556-108">Unity-Buildoptionen</span><span class="sxs-lookup"><span data-stu-id="21556-108">Unity Build Options</span></span>
![Buildfenster – Unity-Buildoptionen 1](images/MRTK_BuildWindow1.png)

<span data-ttu-id="21556-110">Diese Szenen sind aus den Unity-Buildeinstellungen.</span><span class="sxs-lookup"><span data-stu-id="21556-110">These scenes are from the Unity Build Settings.</span></span> <span data-ttu-id="21556-111">Sie können den Typ des Zielgeräts über das Dropdownmenü ändern.</span><span class="sxs-lookup"><span data-stu-id="21556-111">You can change the target device type using the dropdown menu.</span></span>

## <a name="appx-build-options"></a><span data-ttu-id="21556-112">Appx-Buildoptionen</span><span class="sxs-lookup"><span data-stu-id="21556-112">Appx Build Options</span></span>
![Buildfenster – Appx-Buildoptionen 2](images/MRTK_BuildWindow2.png)

<span data-ttu-id="21556-114">Auf dieser Registerkarte wird die Konfiguration für die Visual Studio angezeigt.</span><span class="sxs-lookup"><span data-stu-id="21556-114">This tab shows the configuration for the Visual Studio solution.</span></span> <span data-ttu-id="21556-115">Aktivieren Sie HoloLens 2 Eingabefunktion zum Anvingen, um die Eingabefunktion für die Blickverfolgung **zu** aktivieren.</span><span class="sxs-lookup"><span data-stu-id="21556-115">To enabled HoloLens 2's eye-tracking input capability, check **Gaze Input Capability** option.</span></span> 

<span data-ttu-id="21556-116">Sie können die GLB-Datei im **Feld 3D-App-Startfeld Modell** für benutzerdefiniertes 3D-App-Startfeld zuweisen.</span><span class="sxs-lookup"><span data-stu-id="21556-116">You can assign .glb file in the **3D App Launcher Model** field for custom 3D app launcher icon.</span></span> <span data-ttu-id="21556-117">Weitere Informationen [finden Sie unter Designrichtlinie für das 3D-App-Startfeld.](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance)</span><span class="sxs-lookup"><span data-stu-id="21556-117">See [3D app launcher design guideline](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) for more information.</span></span>

<span data-ttu-id="21556-118">Standardmäßig ist **automatisches Inkrement** in den Versionsoptionen aktiviert.</span><span class="sxs-lookup"><span data-stu-id="21556-118">By default, **Auto Increment** is checked in the Versioning Options.</span></span> <span data-ttu-id="21556-119">AppX-Versionen werden automatisch erhöht.</span><span class="sxs-lookup"><span data-stu-id="21556-119">AppX versions will be automatically incremented.</span></span>


## <a name="deploy-options"></a><span data-ttu-id="21556-120">Bereitstellungsoptionen</span><span class="sxs-lookup"><span data-stu-id="21556-120">Deploy Options</span></span>
![Buildfenster – Bereitstellungsoptionen 3](images/MRTK_BuildWindow3.png)

<span data-ttu-id="21556-122">Auf dieser Registerkarte können Sie eine Verbindung mit dem Gerät herstellen, indem Sie Benutzername und Kennwort für die Geräteportal eingeben.</span><span class="sxs-lookup"><span data-stu-id="21556-122">In this tab, you can connect to the device by entering username and password for the Device Portal.</span></span> 

<span data-ttu-id="21556-123">Unten auf der Seite finden Sie eine Liste der app-Pakete, die erstellt wurden.</span><span class="sxs-lookup"><span data-stu-id="21556-123">On the bottom of the page, you can find list of the app packages that has been created.</span></span> 

