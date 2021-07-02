---
title: Fenster „Build“ (Erstellen)
description: Dokumentation zur Verwendung des Buildfensters in MRTK für Unity.
author: cre8ivepark
ms.author: dongpark
ms.date: 04/06/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Build, Buildfenster, Tools
ms.openlocfilehash: b0b2bb1d06a561f5f647d01145fe88f562c53017
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176149"
---
# <a name="build-window"></a><span data-ttu-id="57177-104">Fenster „Build“ (Erstellen)</span><span class="sxs-lookup"><span data-stu-id="57177-104">Build window</span></span>
![Erstellen & Bereitstellungsflows](images/MRTK_BuildWindow0.png)

<span data-ttu-id="57177-106">Das MRTK-Buildfenster erleichtert das Erstellen & Bereitstellen Ihrer MRTK-Unity Projekte.</span><span class="sxs-lookup"><span data-stu-id="57177-106">MRTK's build window make it easy to build & deploy your MRTK-Unity projects.</span></span> <span data-ttu-id="57177-107">Mit einem einzigen Klick auf die Schaltfläche können Sie ein Unity-Projekt erstellen und Visual Studio projektmappe(. SLN), UWP-App-Paket(. APPX), und installieren Sie das App-Paket auf dem Gerät.</span><span class="sxs-lookup"><span data-stu-id="57177-107">With a single button click, you can build Unity project and generate Visual Studio solution(.SLN), UWP App package(.APPX), and install the app package on the device.</span></span> 


## <a name="unity-build-options"></a><span data-ttu-id="57177-108">Unity-Buildoptionen</span><span class="sxs-lookup"><span data-stu-id="57177-108">Unity Build Options</span></span>
![Buildfenster – Unity-Buildoptionen 1](images/MRTK_BuildWindow1.png)

<span data-ttu-id="57177-110">Diese Szenen stammen aus der Unity Build Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="57177-110">These scenes are from the Unity Build Settings.</span></span> <span data-ttu-id="57177-111">Sie können den Zielgerätetyp über das Dropdownmenü ändern.</span><span class="sxs-lookup"><span data-stu-id="57177-111">You can change the target device type using the dropdown menu.</span></span>

## <a name="appx-build-options"></a><span data-ttu-id="57177-112">Appx-Buildoptionen</span><span class="sxs-lookup"><span data-stu-id="57177-112">Appx Build Options</span></span>
![Buildfenster – Appx-Buildoptionen 2](images/MRTK_BuildWindow2.png)

<span data-ttu-id="57177-114">Auf dieser Registerkarte wird die Konfiguration für die Visual Studio Projektmappe angezeigt.</span><span class="sxs-lookup"><span data-stu-id="57177-114">This tab shows the configuration for the Visual Studio solution.</span></span> <span data-ttu-id="57177-115">Aktivieren Sie die Option **Eingabefunktion anverfolgen,** um die Eyetracking-Eingabefunktion von HoloLens 2 zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="57177-115">To enabled HoloLens 2's eye-tracking input capability, check **Gaze Input Capability** option.</span></span> 

<span data-ttu-id="57177-116">Sie können die GLB-Datei im Feld **3D-App Startprogramm Modell** für das benutzerdefinierte 3D-App-Startfeldsymbol zuweisen.</span><span class="sxs-lookup"><span data-stu-id="57177-116">You can assign .glb file in the **3D App Launcher Model** field for custom 3D app launcher icon.</span></span> <span data-ttu-id="57177-117">Weitere Informationen finden Sie unter Entwurfsrichtlinie für [3D-App-Starter.](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance)</span><span class="sxs-lookup"><span data-stu-id="57177-117">See [3D app launcher design guideline](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) for more information.</span></span>

<span data-ttu-id="57177-118">Standardmäßig wird **automatisches Inkrement** in den Versionierungsoptionen aktiviert.</span><span class="sxs-lookup"><span data-stu-id="57177-118">By default, **Auto Increment** is checked in the Versioning Options.</span></span> <span data-ttu-id="57177-119">AppX-Versionen werden automatisch erhöht.</span><span class="sxs-lookup"><span data-stu-id="57177-119">AppX versions will be automatically incremented.</span></span>


## <a name="deploy-options"></a><span data-ttu-id="57177-120">Bereitstellungsoptionen</span><span class="sxs-lookup"><span data-stu-id="57177-120">Deploy Options</span></span>
![Buildfenster – Bereitstellungsoptionen 3](images/MRTK_BuildWindow3.png)

<span data-ttu-id="57177-122">Auf dieser Registerkarte können Sie eine Verbindung mit dem Gerät herstellen, indem Sie Benutzername und Kennwort für die Geräteportal eingeben.</span><span class="sxs-lookup"><span data-stu-id="57177-122">In this tab, you can connect to the device by entering username and password for the Device Portal.</span></span> 

<span data-ttu-id="57177-123">Unten auf der Seite finden Sie eine Liste der app-Pakete, die erstellt wurden.</span><span class="sxs-lookup"><span data-stu-id="57177-123">On the bottom of the page, you can find list of the app packages that has been created.</span></span> 

