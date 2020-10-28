---
ms.openlocfilehash: dcbeceb4cbe6b87cd6458afa789f9e09abaf7f3d
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638732"
---
# <a name="all-platforms"></a>[<span data-ttu-id="06567-101">Alle Plattformen</span><span class="sxs-lookup"><span data-stu-id="06567-101">All platforms</span></span>](#tab/all)

### <a name="enabling-hp-motion-controller-plugin"></a><span data-ttu-id="06567-102">Aktivieren von HP Motion Controller Plugin</span><span class="sxs-lookup"><span data-stu-id="06567-102">Enabling HP Motion Controller Plugin</span></span> 

<span data-ttu-id="06567-103">Das Interaktions Profil und die Controller Zuordnungen befinden sich im HP Motion Controller-Plug-in, das aktiviert werden muss, um die Controller Zuordnungen für das Eingabe System von Unreal verfügbar zu machen.</span><span class="sxs-lookup"><span data-stu-id="06567-103">The interaction profile and controller mappings are in the HP Motion Controller plugin, which must be enabled to expose the controller mappings to Unreal’s input system.</span></span>

![Aktivieren des openxrhpcontroller-Plug-ins](../images/reverb-g2-img-01.png)

# <a name="steamvr"></a>[<span data-ttu-id="06567-105">SteamVR</span><span class="sxs-lookup"><span data-stu-id="06567-105">SteamVR</span></span>](#tab/steamvr)

### <a name="configuring-startup-and-hmdpluginpriority"></a><span data-ttu-id="06567-106">Konfigurieren von Start und hmdpluginpriority</span><span class="sxs-lookup"><span data-stu-id="06567-106">Configuring Startup and HMDPluginPriority</span></span>

<span data-ttu-id="06567-107">Eingaben in Unreal mit steamvr haben einige Unterschiede.</span><span class="sxs-lookup"><span data-stu-id="06567-107">Input in Unreal using SteamVR has a few differences.</span></span>  <span data-ttu-id="06567-108">Vergewissern Sie sich beim Einrichten des Projekts zunächst, dass das neue Eingabe System von steamvr verwendet wird, indem Sie VR hinzufügen **. Steamvr. enablevrinput = 1** bis zum **Start** Abschnitt in **Engine/config/ConsoleVariables.ini** .</span><span class="sxs-lookup"><span data-stu-id="06567-108">When setting up the project, first ensure it is using SteamVR’s new input system by adding **vr.SteamVR.EnableVRInput=1** to the **Startup** section in **Engine/Config/ConsoleVariables.ini** .</span></span>  <span data-ttu-id="06567-109">Diese ini befindet sich im Installationsverzeichnis der Engine, nicht im Projektverzeichnis.</span><span class="sxs-lookup"><span data-stu-id="06567-109">This ini is found in the engine install directory, not the project directory.</span></span>

![Aktualisieren der Startkonfiguration](../images/reverb-g2-img-07.png)

<span data-ttu-id="06567-111">Das HP Motion Controller-Plug-in aktiviert openxr.</span><span class="sxs-lookup"><span data-stu-id="06567-111">The HP Motion Controller plugin will enable OpenXR.</span></span>  <span data-ttu-id="06567-112">Wenn Sie openxr nicht verwenden, müssen Sie den hmdpluginpriority-Wert von "steamvr" in BaseEngine.ini in demselben Verzeichnis wie ConsoleVariables.ini bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="06567-112">If you're not using OpenXR, you will need to edit the HMDPluginPriority of SteamVR in BaseEngine.ini in the same directory as ConsoleVariables.ini.</span></span>  <span data-ttu-id="06567-113">Ändern Sie den Wert von "steamvr" in einen höheren Wert als den openxrhmd-Wert.</span><span class="sxs-lookup"><span data-stu-id="06567-113">Change the SteamVR value to be greater than the OpenXRHMD value.</span></span>

![Aktualisieren der hmdpluginpriority-Konfiguration](../images/reverb-g2-img-08.png)


