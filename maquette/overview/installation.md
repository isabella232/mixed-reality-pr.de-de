---
title: Installieren von Maquette
description: Erfahren Sie, wie Sie Maquette in vscode installieren und konfigurieren.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, Maquette, Prototyperstellung, gemischte Realität, Virtual Reality, VR, Mr, Feedback, Feedback-Hub, Fehler
ms.openlocfilehash: ba0064326e83f04b056c0baa2f86f718e41bedfe
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935425"
---
# <a name="installing-maquette"></a><span data-ttu-id="8f8d3-104">Installieren von Maquette</span><span class="sxs-lookup"><span data-stu-id="8f8d3-104">Installing Maquette</span></span>

<!-- TODO(Harrison): Need consolidated logo with text. -->
<span data-ttu-id="8f8d3-105">![Logo ](../images/MaquetteIcon.png) maquettescript-Installation</span><span class="sxs-lookup"><span data-stu-id="8f8d3-105">![Logo](../images/MaquetteIcon.png) MaquetteScript Installation</span></span>

<!-- TODO(Stefan): Need more explanation on the .mqjs route for running MaquetteScript. -->
<span data-ttu-id="8f8d3-106">Maquettescript-Entwicklung erfolgt in erster Linie in vscode.</span><span class="sxs-lookup"><span data-stu-id="8f8d3-106">MaquetteScript development is primarily done within VSCode.</span></span> <span data-ttu-id="8f8d3-107">Maquettescript kann aus Skripts in `.mqjs` Dateien und auch über eine spezielle vscode-Erweiterungsschnittstelle ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="8f8d3-107">MaquetteScript can run from script contained in `.mqjs` files and also via a special VSCode extension interface.</span></span> <span data-ttu-id="8f8d3-108">Die Integration von vscode und Maquette zum Aktivieren der Erweiterungsschnittstelle erfolgt mit einer maquettescript-vscode-Erweiterung.</span><span class="sxs-lookup"><span data-stu-id="8f8d3-108">Integration between VSCode and Maquette to enable the extension interface is accomplished with a MaquetteScript VSCode extension.</span></span>

## <a name="installing-the-vscode-extension"></a><span data-ttu-id="8f8d3-109">Installieren der vscode-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="8f8d3-109">Installing the VSCode Extension</span></span>

* <span data-ttu-id="8f8d3-110">Herunterladen und Installieren von [vscode](https://code.visualstudio.com).</span><span class="sxs-lookup"><span data-stu-id="8f8d3-110">Download and install [VSCode](https://code.visualstudio.com).</span></span> 

<span data-ttu-id="8f8d3-111">Die Erweiterung "Maquette JavaScript" befindet sich im [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-maquette.vscode-maquette-javascript).</span><span class="sxs-lookup"><span data-stu-id="8f8d3-111">The Maquette javascript extension is in [the Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-maquette.vscode-maquette-javascript).</span></span>

* <span data-ttu-id="8f8d3-112">Führen Sie die [Installationsprozedur für die Erweiterung aus](vscode:extension/ms-maquette.vscode-maquette-javascript).</span><span class="sxs-lookup"><span data-stu-id="8f8d3-112">Run the [installation procedure for the extension](vscode:extension/ms-maquette.vscode-maquette-javascript).</span></span>

<!-- TODO(Stefan): Are there plans to have the extension update manually in the future? If so, when will this be available? -->
`NOTE: The VSCode extension does not automatically update currently and will need to be updated manually.`

## <a name="enabling-scripting"></a><span data-ttu-id="8f8d3-113">Aktivieren der Skripterstellung</span><span class="sxs-lookup"><span data-stu-id="8f8d3-113">Enabling Scripting</span></span>

<!-- TODO(Stefan): Is scripting still a pre-release only option? If and when will it be available for current users? -->
`PRE-RELEASE NOTE: Javascript is already embedded within Maquette but requires additional steps and settings to access and enable. Scripting is currently only available for pre-release testing and is not a visible option for current users. Ensure at least version 2020.3.0.0.1315 but preferably use latest version.`

<span data-ttu-id="8f8d3-114">So machen Sie die Skripterstellung während der Vorabversion verfügbar:</span><span class="sxs-lookup"><span data-stu-id="8f8d3-114">To make scripting accessible during pre-release:</span></span>

* <span data-ttu-id="8f8d3-115">Fügen Sie eine Datei mit dem Namen `scripting.enabled` im Verzeichnis Benutzer Dokumente für Maquette in: ein `~/Documents/Maquette/Settings` .</span><span class="sxs-lookup"><span data-stu-id="8f8d3-115">Put a file with the name `scripting.enabled` in the Users Documents directory for Maquette in: `~/Documents/Maquette/Settings`.</span></span>

<span data-ttu-id="8f8d3-116">Nach der Installation wird die Skripterstellung aus Sicherheitsgründen standardmäßig deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="8f8d3-116">After installation, scripting will be disabled by default for security reasons.</span></span>

<!-- TODO(Stefan): Missing a first step where the user has to select the {} tab in VSCode, shown in the screenshot, to access the scripting enabled setting.
                   - Also missing instructions and screenshot on how to turn on scripting in the JSON settings file.
 -->
* <span data-ttu-id="8f8d3-117">Um die Skriptausführung zu aktivieren, aktivieren Sie Sie auf der Registerkarte Haupt des Begleit Fensters oder in der JSON-Einstellungsdatei.</span><span class="sxs-lookup"><span data-stu-id="8f8d3-117">To enable execution of script, turn it ON in the main tab of the companion window or in the json settings file.</span></span>

![Aktivieren der Skripterstellung in vs Code](images/IntroductionEnableScripting.png)


