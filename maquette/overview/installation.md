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
# <a name="installing-maquette"></a>Installieren von Maquette

<!-- TODO(Harrison): Need consolidated logo with text. -->
![Logo ](../images/MaquetteIcon.png) maquettescript-Installation

<!-- TODO(Stefan): Need more explanation on the .mqjs route for running MaquetteScript. -->
Maquettescript-Entwicklung erfolgt in erster Linie in vscode. Maquettescript kann aus Skripts in `.mqjs` Dateien und auch über eine spezielle vscode-Erweiterungsschnittstelle ausgeführt werden. Die Integration von vscode und Maquette zum Aktivieren der Erweiterungsschnittstelle erfolgt mit einer maquettescript-vscode-Erweiterung.

## <a name="installing-the-vscode-extension"></a>Installieren der vscode-Erweiterung

* Herunterladen und Installieren von [vscode](https://code.visualstudio.com). 

Die Erweiterung "Maquette JavaScript" befindet sich im [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-maquette.vscode-maquette-javascript).

* Führen Sie die [Installationsprozedur für die Erweiterung aus](vscode:extension/ms-maquette.vscode-maquette-javascript).

<!-- TODO(Stefan): Are there plans to have the extension update manually in the future? If so, when will this be available? -->
`NOTE: The VSCode extension does not automatically update currently and will need to be updated manually.`

## <a name="enabling-scripting"></a>Aktivieren der Skripterstellung

<!-- TODO(Stefan): Is scripting still a pre-release only option? If and when will it be available for current users? -->
`PRE-RELEASE NOTE: Javascript is already embedded within Maquette but requires additional steps and settings to access and enable. Scripting is currently only available for pre-release testing and is not a visible option for current users. Ensure at least version 2020.3.0.0.1315 but preferably use latest version.`

So machen Sie die Skripterstellung während der Vorabversion verfügbar:

* Fügen Sie eine Datei mit dem Namen `scripting.enabled` im Verzeichnis Benutzer Dokumente für Maquette in: ein `~/Documents/Maquette/Settings` .

Nach der Installation wird die Skripterstellung aus Sicherheitsgründen standardmäßig deaktiviert.

<!-- TODO(Stefan): Missing a first step where the user has to select the {} tab in VSCode, shown in the screenshot, to access the scripting enabled setting.
                   - Also missing instructions and screenshot on how to turn on scripting in the JSON settings file.
 -->
* Um die Skriptausführung zu aktivieren, aktivieren Sie Sie auf der Registerkarte Haupt des Begleit Fensters oder in der JSON-Einstellungsdatei.

![Aktivieren der Skripterstellung in vs Code](images/IntroductionEnableScripting.png)


