---
title: Editor-Erweiterungen in Unreal
description: Erfahren Sie, wie Sie den Unreal Engine-Editor mit benutzerdefinierten Skripts, Skriptaktionen und Hilfsprogrammwidgets erweitern.
author: hferrone
ms.author: safarooq
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, Editorerweiterungen, Unreal-Editor, UE4, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, Dokumentation, Leitfäden, Features, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Portieren, Upgrade
ms.openlocfilehash: ee0ba5d1d60b83dc334204e12283c76a877b4ec8
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98584918"
---
# <a name="editor-extensions-in-unreal"></a><span data-ttu-id="4975c-104">Editor-Erweiterungen in Unreal</span><span class="sxs-lookup"><span data-stu-id="4975c-104">Editor extensions in Unreal</span></span>

<span data-ttu-id="4975c-105">Unreal bietet einen umfangreichen Satz von Features, mit denen Sie die Engine an Ihre Anforderungen anpassen können.</span><span class="sxs-lookup"><span data-stu-id="4975c-105">Unreal provides an extensive set of features that allow you to customize the engine to your needs.</span></span> <span data-ttu-id="4975c-106">Die Features reichen von einfachen, aber begrenzten, bis hin zu sehr leistungsstarken, aber komplexen Funktionen.</span><span class="sxs-lookup"><span data-stu-id="4975c-106">The features range from simple but limited, to very powerful but complex.</span></span> <span data-ttu-id="4975c-107">Die folgenden Schritte sind in der Reihenfolge zunehmender Komplexität aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="4975c-107">The following steps are listed in order of increasing complexity.</span></span> <span data-ttu-id="4975c-108">Generell sollten Sie nach einfacheren Lösungen für Ihr Problem suchen und seine Optionen ausschöpfen, bevor Sie zu einer komplexeren Option wechseln.</span><span class="sxs-lookup"><span data-stu-id="4975c-108">In general, you should reach for simpler solutions to your problem, and exhausting its options, before moving to a more complex option.</span></span> <span data-ttu-id="4975c-109">Beispielsweise haben wir festgestellt, dass das grundlegende Konstruktionsskript in den meisten Fällen anstelle von Plug-Ins verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="4975c-109">As an example, we have found that the basic Construction Script can be used in lieu of plugins most of the time.</span></span> 

<!-- Also, engine modification should be a last resort, as it is not only complex, but integrating changes back into the engine for simple work-around can take a disproportionately long time. -->

## <a name="construction-scripts"></a><span data-ttu-id="4975c-110">Konstruktionsskripts</span><span class="sxs-lookup"><span data-stu-id="4975c-110">Construction scripts</span></span>

<span data-ttu-id="4975c-111">Sie können Konstruktionsskripts verwenden, um Initialisierungsaktionen vorzunehmen, die ausgeführt werden, wenn eine Blaupauseninstanz erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="4975c-111">You can use construction scripts to perform initialization actions, which run when Blueprint instance are created.</span></span>

* [<span data-ttu-id="4975c-112">Benutzerkonstruktionsskript</span><span class="sxs-lookup"><span data-stu-id="4975c-112">User Constructions script</span></span>](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/UserConstructionScript/index.html)
* [<span data-ttu-id="4975c-113">Blaupausenbeispiel</span><span class="sxs-lookup"><span data-stu-id="4975c-113">Blueprint example</span></span>](https://docs.unrealengine.com/Resources/ContentExamples/Blueprints/1_4/index.html)
* [<span data-ttu-id="4975c-114">Videotutorial</span><span class="sxs-lookup"><span data-stu-id="4975c-114">Video tutorial</span></span>](https://www.youtube.com/watch?v=z1SD-d9yJmQ&ab_channel=UnrealEngine)

## <a name="scripted-actions"></a><span data-ttu-id="4975c-115">Skriptaktionen</span><span class="sxs-lookup"><span data-stu-id="4975c-115">Scripted actions</span></span>

<span data-ttu-id="4975c-116">Skriptaktionen sind Blaupausen des Editor-Hilfsprogramms.</span><span class="sxs-lookup"><span data-stu-id="4975c-116">Scripted Actions are Editor Utility Blueprints.</span></span> <span data-ttu-id="4975c-117">Sie können sie im Unreal-Editor wie folgt starten:</span><span class="sxs-lookup"><span data-stu-id="4975c-117">You can launch them in the Unreal Editor by:</span></span>
* <span data-ttu-id="4975c-118">Klicken Sie mit der rechten Maustaste auf **Assets** (Ressourcen) im Inhaltsbrowser.</span><span class="sxs-lookup"><span data-stu-id="4975c-118">Right-clicking **Assets** in the Content Browser</span></span>
* <span data-ttu-id="4975c-119">Oder klicken Sie mit der rechten Maustaste auf **Actors** (Akteure), entweder im Ebenenviewport oder im Gliederungs-Editor.</span><span class="sxs-lookup"><span data-stu-id="4975c-119">Or by right-clicking **Actors** either in the Level Viewport or in the World Outliner</span></span>

<span data-ttu-id="4975c-120">Skriptaktionen eignen sich einzigartig für Gelegenheiten, bei denen Ihre Blaupausenlogik kontextabhängig Gruppen von Ressourcen oder Akteuren erkennen muss.</span><span class="sxs-lookup"><span data-stu-id="4975c-120">Scripted Actions are uniquely suited for times when you need your Blueprint logic to have contextual awareness about sets of Assets or Actors.</span></span> <span data-ttu-id="4975c-121">Typischerweise ruft eine Skriptaktion eine Liste von Ressourcen oder Akteuren ab, die Sie bei Ausführung der Aktion ausgewählt haben. Anschließend ändert die Aktion diese Objekte oder berücksichtigt sie in ihrem Diagramm.</span><span class="sxs-lookup"><span data-stu-id="4975c-121">Typically, a Scripted Action gets a list of Assets or Actors that you've selected when the action is executed, then modifies those objects or considers them in its graph.</span></span>

* [<span data-ttu-id="4975c-122">Skriptaktionen</span><span class="sxs-lookup"><span data-stu-id="4975c-122">Scripted Actions</span></span>](https://docs.unrealengine.com/ProductionPipelines/ScriptingAndAutomation/Blueprints/ScriptedActions/index.html)
* [<span data-ttu-id="4975c-123">Ausführen von Skriptaktionen beim Projektstart</span><span class="sxs-lookup"><span data-stu-id="4975c-123">Running scripted actions on project startup</span></span>](https://docs.unrealengine.com/ProductionPipelines/ScriptingAndAutomation/Blueprints/StartupObjects/index.html)

## <a name="editor-utility-widgets"></a><span data-ttu-id="4975c-124">Editor-Hilfsprogrammwidgets</span><span class="sxs-lookup"><span data-stu-id="4975c-124">Editor utility widgets</span></span>

<span data-ttu-id="4975c-125">Sie können [Editor-Hilfsprogrammwidgets](https://docs.unrealengine.com/InteractiveExperiences/UMG/UserGuide/EditorUtilityWidgets/index.html) jederzeit verwenden, um neue Benutzeroberflächenelemente hinzuzufügen, mit denen die Benutzeroberfläche des Unreal-Editors geändert werden soll.</span><span class="sxs-lookup"><span data-stu-id="4975c-125">You can use [Editor Utility Widgets](https://docs.unrealengine.com/InteractiveExperiences/UMG/UserGuide/EditorUtilityWidgets/index.html) anytime you want to add new UI elements to modify the User Interface (UI) of the Unreal Editor.</span></span> <span data-ttu-id="4975c-126">Editor-Hilfsprogrammwidgets basieren auf UMG (Unreal Motion Graphics), sodass Sie Widgets so in einer Blaupause einrichten können, wie Sie es bei jeder anderen UMG-Widgetblaupause tun würden.</span><span class="sxs-lookup"><span data-stu-id="4975c-126">Editor Utility Widgets are based on Unreal Motion Graphics (UMG), so you can set up Widgets in a Blueprint like you would for any other UMG Widget Blueprint.</span></span>

<span data-ttu-id="4975c-127">Diese Widgets sind für die Editor-Benutzeroberfläche spezifisch, und Sie können sie zum Erstellen benutzerdefinierter Editor-Registerkarten verwenden.</span><span class="sxs-lookup"><span data-stu-id="4975c-127">These Widgets are specifically for the Editor UI, and you can use them to create custom Editor tabs.</span></span> <span data-ttu-id="4975c-128">Sie können diese benutzerdefinierten Registerkarten dann im Windows-Menü auswählen, wie Sie auch vorhandene Editor-Registerkarten auswählen würden.</span><span class="sxs-lookup"><span data-stu-id="4975c-128">You can then select these custom tabs from the Windows menu, like you would select existing Editor tabs.</span></span>

## <a name="plugins"></a><span data-ttu-id="4975c-129">Plug-Ins</span><span class="sxs-lookup"><span data-stu-id="4975c-129">Plugins</span></span>

<span data-ttu-id="4975c-130">Unreal ermöglicht Ihnen die Entwicklung und Verwaltung Ihrer eigenen benutzerdefinierten [Plug-Ins](https://docs.unrealengine.com/ProductionPipelines/Plugins/index.html) für die Verwendung mit UE4-Tools und der UE4-Laufzeit.</span><span class="sxs-lookup"><span data-stu-id="4975c-130">Unreal lets you develop and manage your own custom [plugins](https://docs.unrealengine.com/ProductionPipelines/Plugins/index.html) for use with UE4 tools and runtime.</span></span> <span data-ttu-id="4975c-131">Sie können Ihre Plug-Ins jederzeit im Unreal-Editor aktivieren oder deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="4975c-131">You can enable or disable your plugins at any time in the Unreal Editor.</span></span> <span data-ttu-id="4975c-132">Mit Plug-Ins lassen sich Laufzeit-Gameplayfunktionen hinzufügen, integrierte Engine-Funktionen ändern, neue Dateitypen erstellen und die Funktionen des Editors erweitern.</span><span class="sxs-lookup"><span data-stu-id="4975c-132">Plugins can add runtime gameplay functionality, modify built-in Engine features, create new file types, and extend the capabilities of the Editor.</span></span>

<!-- ## Engine modifications -->

