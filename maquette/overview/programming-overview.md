---
title: Übersicht über die Programmierung
description: Erfahren Sie, wie Sie mit Skripts auf Makett-Objekte und-Schnittstellen zugreifen
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, Maquette, Prototyperstellung, gemischte Realität, Virtual Reality, VR, Mr, Feedback, Feedback-Hub, Fehler
ms.openlocfilehash: 6761ed0fab70b0d497ad1e1398cbd6c1af6ab38b
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935507"
---
# <a name="programming-overview"></a><span data-ttu-id="71781-104">Übersicht über die Programmierung</span><span class="sxs-lookup"><span data-stu-id="71781-104">Programming overview</span></span>

<!-- TODO(Harrison): Need consolidated logo with text -->

![Logo](../images/MaquetteIcon.png) <span data-ttu-id="71781-106">Übersicht über die Programmierung</span><span class="sxs-lookup"><span data-stu-id="71781-106">Programming Overview</span></span>

<span data-ttu-id="71781-107">Microsoft Maquette verwendet JavaScript (ECMAScript 5,1 mit Erweiterungen), das auf dem [Jint](https://github.com/sebastienros/jint) -Interpreter basiert.</span><span class="sxs-lookup"><span data-stu-id="71781-107">Microsoft Maquette uses JavaScript (ECMAScript 5.1 with extensions) based on the [Jint](https://github.com/sebastienros/jint) interpreter.</span></span> <span data-ttu-id="71781-108">Die Erweiterung `.mqjs` wird verwendet, um Makett-JavaScript-Dateien von normalem JavaScript zu unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="71781-108">The extension `.mqjs` is used to distinguish Maquette javascript files from normal JavaScript.</span></span>

<!-- TODO(Stefan): Need more context and high-level explanation of Maquette objects, their accessible interfaces, and functionality. 
                   - What can they do and what problems can they solve?
                   - Is there a specific link to the Maquette object API that can be included here?  
-->
<span data-ttu-id="71781-109">Auf Maquette-Objekte und-Schnittstellen kann über das-Objekt zugegriffen werden `Maquette` .</span><span class="sxs-lookup"><span data-stu-id="71781-109">Maquette objects and interfaces are accessible and scriptable via the `Maquette` Object.</span></span> <span data-ttu-id="71781-110">Dokumentation zu Maquette-Objekten und-Schnittstellen finden Sie in der Referenz zur API-Referenz von Maquette.</span><span class="sxs-lookup"><span data-stu-id="71781-110">Documentation on Maquette Objects and interfaces are provided in Maquette's API Reference.</span></span>

<!-- TODO(Stefan): Link to roadmap information, which hasn't been documented yet. -->
<span data-ttu-id="71781-111">Maquettescript ist eine neue Addition und in Flux, damit Änderungen erwartet werden.</span><span class="sxs-lookup"><span data-stu-id="71781-111">MaquetteScript is a new addition and in flux so changes should be expected.</span></span> <span data-ttu-id="71781-112">Ausführlichere Dokumentation und Updates sind in Kürze verfügbar.</span><span class="sxs-lookup"><span data-stu-id="71781-112">More detailed documentation and updates available soon.</span></span>

<!-- TODO(Stefan): Is Spotlights a component or added functionality of Maquette? -->
## <a name="spotlights-on-scripting"></a><span data-ttu-id="71781-113">Spotlights bei der Skripterstellung</span><span class="sxs-lookup"><span data-stu-id="71781-113">Spotlights on Scripting</span></span>

* <span data-ttu-id="71781-114">TBD-Skripts für die Skripterstellung als Beispiele/Tutorials</span><span class="sxs-lookup"><span data-stu-id="71781-114">TBD - Scripting Spotlights focused as Samples/Tutorials</span></span>
  * <span data-ttu-id="71781-115">2X-Bilder/Beschriftung – Link zur Spotlight-Seite</span><span class="sxs-lookup"><span data-stu-id="71781-115">2x Images/Caption – link to spotlight page</span></span>

<!-- TODO(Stefan): Each of these bullets need to be fleshed out. -->
## <a name="getting-started-with-maquettescript"></a><span data-ttu-id="71781-116">Einstieg in maquettescript</span><span class="sxs-lookup"><span data-stu-id="71781-116">Getting started with MaquetteScript</span></span>

* <span data-ttu-id="71781-117">Mqjs im Vergleich zu JS</span><span class="sxs-lookup"><span data-stu-id="71781-117">Mqjs vs. JS</span></span>
* <span data-ttu-id="71781-118">Programmiermodell</span><span class="sxs-lookup"><span data-stu-id="71781-118">Programming Model</span></span>
  * <span data-ttu-id="71781-119">Bearbeiten und ausführen</span><span class="sxs-lookup"><span data-stu-id="71781-119">Editing vs. Running</span></span>
* <span data-ttu-id="71781-120">Link zum Programmier Workflow</span><span class="sxs-lookup"><span data-stu-id="71781-120">Link to Programming Workflow</span></span>
* <span data-ttu-id="71781-121">Link zu Freigabe Ergebnissen</span><span class="sxs-lookup"><span data-stu-id="71781-121">Link to Sharing Results</span></span>

## <a name="programming-workflow"></a><span data-ttu-id="71781-122">Programmier Workflow</span><span class="sxs-lookup"><span data-stu-id="71781-122">Programming workflow</span></span>

<!-- TODO(Stefan): Which of these bullets are no longer TBD? We only want to include documentation on existing content. -->
<span data-ttu-id="71781-123">TBD</span><span class="sxs-lookup"><span data-stu-id="71781-123">TBD</span></span>
* <span data-ttu-id="71781-124">REPL</span><span class="sxs-lookup"><span data-stu-id="71781-124">REPL</span></span>
* <span data-ttu-id="71781-125">Skript Vorgang</span><span class="sxs-lookup"><span data-stu-id="71781-125">Scripting operation</span></span>
* <span data-ttu-id="71781-126">Debugger-Vorgang</span><span class="sxs-lookup"><span data-stu-id="71781-126">Debugger operation</span></span>
* <span data-ttu-id="71781-127">Debugschleife</span><span class="sxs-lookup"><span data-stu-id="71781-127">Debugging loop</span></span>
* <span data-ttu-id="71781-128">Code kopieren/einfügen?</span><span class="sxs-lookup"><span data-stu-id="71781-128">Copy/Paste of code?</span></span>

## <a name="running-mqjs-scripts"></a><span data-ttu-id="71781-129">Ausführen von mqjs-Skripts</span><span class="sxs-lookup"><span data-stu-id="71781-129">Running .mqjs scripts</span></span>

<!-- TODO(Stefan): Need screenshot -->
<span data-ttu-id="71781-130">Wechseln Sie zum Ausführen einer Datei maquettescript. mqjs zum Begleit Fenster von Maquette, und öffnen Sie die Registerkarte Skripterstellung, um nach Skripts zu suchen.</span><span class="sxs-lookup"><span data-stu-id="71781-130">To run a MaquetteScript .mqjs file, go to the companion windows of Maquette and open the scripting tab to locate scripts.</span></span>

> [!NOTE] 
> <span data-ttu-id="71781-131">Einige Optionen sind noch nicht funktionsfähig, da die Skripts nicht ausgeliefert wurden.</span><span class="sxs-lookup"><span data-stu-id="71781-131">Some options will not work yet because we have not ship the scripts.</span></span>

## <a name="vscode-editor-workflow"></a><span data-ttu-id="71781-132">Vscode-Editor-Workflow</span><span class="sxs-lookup"><span data-stu-id="71781-132">VSCode Editor Workflow</span></span>

<span data-ttu-id="71781-133">Um Skripts in Maquette aus vscode heraus auszuwerten, muss der Benutzer zwei Befehle kennen:</span><span class="sxs-lookup"><span data-stu-id="71781-133">To evaluate script in Maquette from within VSCode, the user needs to know two commands:</span></span>

   <span data-ttu-id="71781-134">`CTRL-5` wertet den markierten Text oder die gesamte Zeile aus, in der sich der Cursor befindet.</span><span class="sxs-lookup"><span data-stu-id="71781-134">`CTRL-5` evaluates the selected text or the entire line where the cursor is located.</span></span> 

   <span data-ttu-id="71781-135">`CTRL-SHIFT-5` wertet die gesamte Datei aus.</span><span class="sxs-lookup"><span data-stu-id="71781-135">`CTRL-SHIFT-5` evaluates the entire file.</span></span>

<!-- TODO(Stefan): This could use a nice simple infographic of the REPL loop. -->
<span data-ttu-id="71781-136">Der Text wird an die Makette gesendet, in der JavaScript-Umgebung ausgewertet, und das Ergebnis wird zurück an die Ausgabe Konsole von vscode gesendet.</span><span class="sxs-lookup"><span data-stu-id="71781-136">Text is sent to Maquette, evaluated in the JavaScript environment, and the result is sent back to the output console of VSCode.</span></span> <span data-ttu-id="71781-137">Diese kann als REPL (Read-eval-Print-Loop) verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="71781-137">This can be used as a REPL (read-eval-print-loop).</span></span>

## <a name="example-first-step"></a><span data-ttu-id="71781-138">Beispiel für den ersten Schritt</span><span class="sxs-lookup"><span data-stu-id="71781-138">Example First Step</span></span>

<!-- TODO(Stefan): What kind of file, a C# or .mqjs file? -->
<span data-ttu-id="71781-139">Kopieren Sie den folgenden Code in eine Datei in vscode:</span><span class="sxs-lookup"><span data-stu-id="71781-139">Copy the following code into a file in VSCode:</span></span>

```csharp
var myCube = Maquette.CreateCube();
myCube.position = Maquette.User.GetPositionInFront(0.6);
myCube.color = Color(1.0, 0.5, 0.0);
```

<!-- TODO(Stefan): Need screenshot. -->
<span data-ttu-id="71781-140">Wählen Sie den Code oder nur die Abschnitte aus, und klicken Sie `CTRL-5` auf ausführen.</span><span class="sxs-lookup"><span data-stu-id="71781-140">Select the code or just sections and hit `CTRL-5` to execute.</span></span> <span data-ttu-id="71781-141">Dies sollte einen Cube erstellen, ihn vor Ihnen platzieren und seine Farbe ändern.</span><span class="sxs-lookup"><span data-stu-id="71781-141">This should create a cube, place it in front of you and change its color.</span></span>

<span data-ttu-id="71781-142">Weitere Beispiele finden Sie in der Erweiterung.</span><span class="sxs-lookup"><span data-stu-id="71781-142">There are more examples to find through the extension.</span></span>

## <a name="sharing-results"></a><span data-ttu-id="71781-143">Freigabe Ergebnisse</span><span class="sxs-lookup"><span data-stu-id="71781-143">Sharing Results</span></span>

<!-- TODO(Stefan): Need to fill in content/context for these bullets. If there's a lot of content, we might consider breaking this out into it's own doc. -->
<span data-ttu-id="71781-144">Freigeben zwischen Benutzern und Teams</span><span class="sxs-lookup"><span data-stu-id="71781-144">How to share between users/teams</span></span>
* <span data-ttu-id="71781-145">ZIP-Projekt im Verzeichnis "Dokumente"</span><span class="sxs-lookup"><span data-stu-id="71781-145">Zip project in documents directory</span></span>
* <span data-ttu-id="71781-146">Projekt in Dateifreigabe kopieren</span><span class="sxs-lookup"><span data-stu-id="71781-146">Copy project to file share</span></span>
* <span data-ttu-id="71781-147">Hinzufügen des Dateispeicher Orts von Team Freigabe Einreichungen zum Maquette-Team</span><span class="sxs-lookup"><span data-stu-id="71781-147">Adding file location of team share Submissions to Maquette Team</span></span>

<!-- TODO(Stefan): Need to break these out into their own sections and fill in the missing content/context. 
                   - Which of these is accessible now and not TBD?
-->
<span data-ttu-id="71781-148">TBD</span><span class="sxs-lookup"><span data-stu-id="71781-148">TBD</span></span>
* <span data-ttu-id="71781-149">Enthält einen Verweis auf Code an anderer Stelle mit relativen/absoluten Pfaden, Modulen</span><span class="sxs-lookup"><span data-stu-id="71781-149">Includes, reference to code elsewhere with relative/absolute paths, modules</span></span>
* <span data-ttu-id="71781-150">Bibliotheken?</span><span class="sxs-lookup"><span data-stu-id="71781-150">Libraries?</span></span>
* <span data-ttu-id="71781-151">Laufzeitunterstützung</span><span class="sxs-lookup"><span data-stu-id="71781-151">Runtime support</span></span>
* <span data-ttu-id="71781-152">Nicht aufgelöste externale: Verhalten bei fehlenden/abstürzenden Einträgen</span><span class="sxs-lookup"><span data-stu-id="71781-152">Unresolved Externals - Behavior when entries missing/crashing</span></span>
* <span data-ttu-id="71781-153">Können wir Skripts hinzufügen/bearbeiten/beobachten, die bestimmten Objekten zugeordnet sind?</span><span class="sxs-lookup"><span data-stu-id="71781-153">Can we add/edit/observe script associated with specific objects?</span></span>
  * <span data-ttu-id="71781-154">Können wir dieses Skript kopieren und an anderer Stelle einfügen?</span><span class="sxs-lookup"><span data-stu-id="71781-154">Can we copy/paste this script elsewhere?</span></span>
  * <span data-ttu-id="71781-155">Was ist mit Objekteigenschaften?</span><span class="sxs-lookup"><span data-stu-id="71781-155">What about object properties?</span></span>
  * <span data-ttu-id="71781-156">Benennen von Objekten in meiner Szene?</span><span class="sxs-lookup"><span data-stu-id="71781-156">Naming objects in my scene?</span></span> <span data-ttu-id="71781-157">(Skript mit dem Skript umbenennen)</span><span class="sxs-lookup"><span data-stu-id="71781-157">(renaming script with it)</span></span>
  * <span data-ttu-id="71781-158">Dieses oder selbst Schlüsselwort für ein einem Objekt zugeordnetes Skript</span><span class="sxs-lookup"><span data-stu-id="71781-158">THIS or SELF keyword for script associated with an object</span></span>
  * <span data-ttu-id="71781-159">Wenn ich mit der rechten Maustaste auf ein Objekt klicke, kann ich Code sehen, der ihm zugeordnet ist (und hier Hierarchie).</span><span class="sxs-lookup"><span data-stu-id="71781-159">If I right click on an object, can I see code associated with it (and all it's hierarchy)</span></span>
  * <span data-ttu-id="71781-160">Kann ich in der Benutzeroberfläche auswählen und im Code in vscode angezeigt werden?</span><span class="sxs-lookup"><span data-stu-id="71781-160">Can I select in UI and be brought up at the code in VSCode?</span></span>
  * <span data-ttu-id="71781-161">Zusammenhalten von Code, der einem Objekt zugeordnet ist, in der Skript Quelldatei</span><span class="sxs-lookup"><span data-stu-id="71781-161">Keeping code associated with an object "together" in the script source file?</span></span>
  * <span data-ttu-id="71781-162">Wenn ich auf das Eigenschaften Fenster eines Objekts klicke?</span><span class="sxs-lookup"><span data-stu-id="71781-162">Bring property window up of an object when I click on it?</span></span> <span data-ttu-id="71781-163">In VR und in der Haupt Registerkarte?</span><span class="sxs-lookup"><span data-stu-id="71781-163">In VR and in main tab?</span></span>
* <span data-ttu-id="71781-164">Sicherheitsprobleme</span><span class="sxs-lookup"><span data-stu-id="71781-164">Security Issues</span></span>
* <span data-ttu-id="71781-165">Test – kann "TBD" lauten, aber wir könnten Video-oder Frame-Einfügeverfahren mit Skript</span><span class="sxs-lookup"><span data-stu-id="71781-165">Testing – might be TBD but we could suggest video or frame grab by script</span></span>
* <span data-ttu-id="71781-166">Wenn ein Fehlerbericht Erstellungs Mechanismus vorhanden ist, kann dies über das Skript für andere Benutzer (?) verfügbar gemacht werden... höher</span><span class="sxs-lookup"><span data-stu-id="71781-166">If we have a bug reporting mechanism, we might make that accessible via script for others (?) …later</span></span>
* <span data-ttu-id="71781-167">Bereitstellung – Gewusst wie: "freigeben" des Ergebnisses, Verpacken als exe</span><span class="sxs-lookup"><span data-stu-id="71781-167">Deployment – how to “share” the result, package as EXE</span></span>
* <span data-ttu-id="71781-168">Ausführen/Steuern einer Demo oder spectierung/Überwachung</span><span class="sxs-lookup"><span data-stu-id="71781-168">Running/controlling a demo or spectating/monitoring</span></span>
* <span data-ttu-id="71781-169">Player Modus</span><span class="sxs-lookup"><span data-stu-id="71781-169">Player mode</span></span>
* <span data-ttu-id="71781-170">Wir verfügen möglicherweise über ein Segment zum Erstellen von "Komponenten" für die Freigabe?</span><span class="sxs-lookup"><span data-stu-id="71781-170">We might have a segment on how to make “components” for sharing?</span></span> <span data-ttu-id="71781-171">(kann "TBD" lauten)</span><span class="sxs-lookup"><span data-stu-id="71781-171">(might  be tbd)</span></span>
  * <span data-ttu-id="71781-172">Gibt es #include?</span><span class="sxs-lookup"><span data-stu-id="71781-172">Is there #include?</span></span> <span data-ttu-id="71781-173">Dies kümmert sich um das reine js, es kann jedoch zu Namespace Konflikten kommen.</span><span class="sxs-lookup"><span data-stu-id="71781-173">This handles pure JS I suppose but may have namespace conflicts.</span></span>
  * <span data-ttu-id="71781-174">Gibt es etwas, was wir für eine Maquette tun könnten, um eine andere Makett mit benannten Objekten zu integrieren, um den JS-Code abzugleichen?</span><span class="sxs-lookup"><span data-stu-id="71781-174">Is there anything we could do for a maquette to incorporate some other maquette with named objects to match JS code?</span></span>
