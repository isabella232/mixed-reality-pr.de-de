---
title: Editor-Erweiterungen in Unreal
description: Erfahren Sie, wie Sie den Unreal Engine-Editor mit benutzerdefinierten Skripts, Skriptaktionen und Hilfsprogrammwidgets erweitern.
author: hferrone
ms.author: safarooq
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, Editorerweiterungen, Unreal-Editor, UE4, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, Dokumentation, Leitfäden, Features, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Portieren, Upgrade
ms.openlocfilehash: 91d9a84e4e19cb7f0f2bf54060b45da1767b8d50cdfeb5655f5e58a29d45a702
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226622"
---
# <a name="editor-extensions-in-unreal"></a>Editor-Erweiterungen in Unreal

Unreal bietet einen umfangreichen Satz von Features, mit denen Sie die Engine an Ihre Anforderungen anpassen können. Die Features reichen von einfachen, aber begrenzten, bis hin zu sehr leistungsstarken, aber komplexen Funktionen. Die folgenden Schritte sind in der Reihenfolge zunehmender Komplexität aufgeführt. Generell sollten Sie nach einfacheren Lösungen für Ihr Problem suchen und seine Optionen ausschöpfen, bevor Sie zu einer komplexeren Option wechseln. Beispielsweise haben wir festgestellt, dass das grundlegende Konstruktionsskript in den meisten Fällen anstelle von Plug-Ins verwendet werden kann. 

<!-- Also, engine modification should be a last resort, as it is not only complex, but integrating changes back into the engine for simple work-around can take a disproportionately long time. -->

## <a name="construction-scripts"></a>Konstruktionsskripts

Sie können Konstruktionsskripts verwenden, um Initialisierungsaktionen vorzunehmen, die ausgeführt werden, wenn eine Blaupauseninstanz erstellt wird.

* [Benutzerkonstruktionsskript](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/UserConstructionScript/index.html)
* [Blaupausenbeispiel](https://docs.unrealengine.com/Resources/ContentExamples/Blueprints/1_4/index.html)
* [Videotutorial](https://www.youtube.com/watch?v=z1SD-d9yJmQ&ab_channel=UnrealEngine)

## <a name="scripted-actions"></a>Skriptaktionen

Skriptaktionen sind Blaupausen des Editor-Hilfsprogramms. Sie können sie im Unreal-Editor wie folgt starten:
* Klicken Sie mit der rechten Maustaste auf **Assets** (Ressourcen) im Inhaltsbrowser.
* Oder klicken Sie mit der rechten Maustaste auf **Actors** (Akteure), entweder im Ebenenviewport oder im Gliederungs-Editor.

Skriptaktionen eignen sich einzigartig für Gelegenheiten, bei denen Ihre Blaupausenlogik kontextabhängig Gruppen von Ressourcen oder Akteuren erkennen muss. Typischerweise ruft eine Skriptaktion eine Liste von Ressourcen oder Akteuren ab, die Sie bei Ausführung der Aktion ausgewählt haben. Anschließend ändert die Aktion diese Objekte oder berücksichtigt sie in ihrem Diagramm.

* [Skriptaktionen](https://docs.unrealengine.com/ProductionPipelines/ScriptingAndAutomation/Blueprints/ScriptedActions/index.html)
* [Ausführen von Skriptaktionen beim Projektstart](https://docs.unrealengine.com/ProductionPipelines/ScriptingAndAutomation/Blueprints/StartupObjects/index.html)

## <a name="editor-utility-widgets"></a>Editor-Hilfsprogrammwidgets

Sie können [Editor-Hilfsprogrammwidgets](https://docs.unrealengine.com/InteractiveExperiences/UMG/UserGuide/EditorUtilityWidgets/index.html) jederzeit verwenden, um neue Benutzeroberflächenelemente hinzuzufügen, mit denen die Benutzeroberfläche des Unreal-Editors geändert werden soll. Editor-Hilfsprogrammwidgets basieren auf UMG (Unreal Motion Graphics), sodass Sie Widgets so in einer Blaupause einrichten können, wie Sie es bei jeder anderen UMG-Widgetblaupause tun würden.

Diese Widgets sind für die Editor-Benutzeroberfläche spezifisch, und Sie können sie zum Erstellen benutzerdefinierter Editor-Registerkarten verwenden. Sie können diese benutzerdefinierten Registerkarten dann im Windows-Menü auswählen, wie Sie auch vorhandene Editor-Registerkarten auswählen würden.

## <a name="plugins"></a>Plug-Ins

Unreal ermöglicht Ihnen die Entwicklung und Verwaltung Ihrer eigenen benutzerdefinierten [Plug-Ins](https://docs.unrealengine.com/ProductionPipelines/Plugins/index.html) für die Verwendung mit UE4-Tools und der UE4-Laufzeit. Sie können Ihre Plug-Ins jederzeit im Unreal-Editor aktivieren oder deaktivieren. Mit Plug-Ins lassen sich Laufzeit-Gameplayfunktionen hinzufügen, integrierte Engine-Funktionen ändern, neue Dateitypen erstellen und die Funktionen des Editors erweitern.

<!-- ## Engine modifications -->

