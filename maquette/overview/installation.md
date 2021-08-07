---
title: Installieren von Mainstallieren
description: Erfahren Sie, wie Sie Ma csv in VSCode installieren und konfigurieren.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, Ma bugs, prototyping, Mixed Reality, Virtual Reality, VR, MR, Feedback, Feedback-Hub, bugs
ms.openlocfilehash: c31f461adbe553a5c10e7acfff3037ea0c2b65caf2bbe63bfc234e067a6369e8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214768"
---
# <a name="installing-maquette"></a>Installieren von Mainstallieren

<!-- TODO(Harrison): Need consolidated logo with text. -->
![](../images/MaquetteIcon.png)Ma javascriptScript-Logoinstallation

<!-- TODO(Stefan): Need more explanation on the .mqjs route for running MaquetteScript. -->
Die Ma csvScript-Entwicklung erfolgt in erster Linie innerhalb von VSCode. Ma scriptsScript kann aus Skripts ausgeführt werden, die in `.mqjs` Dateien enthalten sind, sowie über eine spezielle VSCode-Erweiterungsschnittstelle. Die Integration zwischen VSCode und Ma csv, um die Erweiterungsschnittstelle zu aktivieren, erfolgt mit einer Mascript VSCode-Erweiterung.

## <a name="installing-the-vscode-extension"></a>Installieren der VSCode-Erweiterung

* Laden Sie [VSCode](https://code.visualstudio.com)herunter, und installieren Sie es. 

Die JavaScript-Erweiterung Ma javascript befindet sich [im Visual Studio Marketplace.](https://marketplace.visualstudio.com/items?itemName=ms-maquette.vscode-maquette-javascript)

* Führen Sie die [Installationsprozedur für die Erweiterung aus.](vscode:extension/ms-maquette.vscode-maquette-javascript)

<!-- TODO(Stefan): Are there plans to have the extension update manually in the future? If so, when will this be available? -->
`NOTE: The VSCode extension does not automatically update currently and will need to be updated manually.`

## <a name="enabling-scripting"></a>Aktivieren der Skripterstellung

<!-- TODO(Stefan): Is scripting still a pre-release only option? If and when will it be available for current users? -->
`PRE-RELEASE NOTE: Javascript is already embedded within Maquette but requires additional steps and settings to access and enable. Scripting is currently only available for pre-release testing and is not a visible option for current users. Ensure at least version 2020.3.0.0.1315 but preferably use latest version.`

So machen Sie die Skripterstellung während der Vorabversion zugänglich:

* Speichern Sie eine Datei mit dem Namen `scripting.enabled` im Verzeichnis Benutzerdokumente für Ma username in `~/Documents/Maquette/Settings` : .

Nach der Installation wird die Skripterstellung aus Sicherheitsgründen standardmäßig deaktiviert.

<!-- TODO(Stefan): Missing a first step where the user has to select the {} tab in VSCode, shown in the screenshot, to access the scripting enabled setting.
                   - Also missing instructions and screenshot on how to turn on scripting in the JSON settings file.
 -->
* Um die Ausführung des Skripts zu aktivieren, aktivieren Sie es auf der Hauptregisterkarte des Begleitfensters oder in der JSON-Einstellungsdatei.

![Aktivieren der Skripterstellung in VS Code](images/IntroductionEnableScripting.png)


