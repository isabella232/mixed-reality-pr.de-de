---
title: Experimentelle Features
description: Dokument im Zusammenhang mit experimentellen Features im MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 705b7ab96d22c5c94c04476de30e5524095c1ce2
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144787"
---
# <a name="experimental-features"></a><span data-ttu-id="84804-104">Experimentelle Features</span><span class="sxs-lookup"><span data-stu-id="84804-104">Experimental features</span></span>

<span data-ttu-id="84804-105">Einige Features, an die das MRTK-Team arbeitet, scheinen einen großen Anfangswert zu haben, auch wenn wir die Details noch nicht vollständig umgesetzt haben.</span><span class="sxs-lookup"><span data-stu-id="84804-105">Some features the MRTK team works on appear to have a lot of initial value even if we haven’t fully fleshed out the details.</span></span> <span data-ttu-id="84804-106">Für diese Arten von Features möchten wir, dass die Community sie frühzeitig sehen kann.</span><span class="sxs-lookup"><span data-stu-id="84804-106">For these types of features, we want the community to get a chance to see them early.</span></span> <span data-ttu-id="84804-107">Da sie zu einem frühen Zeitpunkt im Zyklus liegen, kennzeichnen wir sie als experimentell, um anzugeben, dass sie sich noch weiterentwickeln und sich im Laufe der Zeit ändern können.</span><span class="sxs-lookup"><span data-stu-id="84804-107">Because they are early in the cycle, we label them as experimental to indicate that they are still evolving, and subject to change over time.</span></span>

## <a name="what-to-expect-from-an-experimental-feature"></a><span data-ttu-id="84804-108">Was sie von einem experimentellen Feature erwarten können</span><span class="sxs-lookup"><span data-stu-id="84804-108">What to expect from an experimental feature</span></span>

<span data-ttu-id="84804-109">Wenn eine Komponente als experimentell markiert ist, können Sie Folgendes erwarten:</span><span class="sxs-lookup"><span data-stu-id="84804-109">If a component is marked experimental you can expect the following:</span></span>

- <span data-ttu-id="84804-110">Eine Beispielszene, die die Verwendung unter dem `MRTK/Examples/Experimental` Unterordner demonstriert</span><span class="sxs-lookup"><span data-stu-id="84804-110">An example scene demonstrating usage, located under `MRTK/Examples/Experimental` sub-folder</span></span>
- <span data-ttu-id="84804-111">Experimentelle Features verfügen möglicherweise nicht über Dokumentationen.</span><span class="sxs-lookup"><span data-stu-id="84804-111">Experimental features may not have docs.</span></span>
- <span data-ttu-id="84804-112">Sie verfügen wahrscheinlich nicht über Tests.</span><span class="sxs-lookup"><span data-stu-id="84804-112">They probably don't have tests.</span></span>
- <span data-ttu-id="84804-113">Experimentelle Features können sich ändern.</span><span class="sxs-lookup"><span data-stu-id="84804-113">Experimental features are subject to change.</span></span>

## <a name="experimental-feature-guidelines"></a><span data-ttu-id="84804-114">Richtlinien für experimentelle Features</span><span class="sxs-lookup"><span data-stu-id="84804-114">Experimental feature guidelines</span></span>

### <a name="experimental-code-should-live-in-a-separate-folder"></a><span data-ttu-id="84804-115">Experimenteller Code sollte sich in einem separaten Ordner befinden</span><span class="sxs-lookup"><span data-stu-id="84804-115">Experimental code should live in a separate folder</span></span>

<span data-ttu-id="84804-116">Experimenteller Code sollte in einen experimentellen Ordner der obersten Ebene gefolgt vom Namen des experimentellen Features wechseln.</span><span class="sxs-lookup"><span data-stu-id="84804-116">Experimental code should go into a top-level experimental folder followed by the experimental feature name.</span></span> <span data-ttu-id="84804-117">Wenn Sie z. B. versuchen, ein neues Feature fooBar bei beizutragen, geben Sie code in folgendes Ein:</span><span class="sxs-lookup"><span data-stu-id="84804-117">For example, if trying to contribute a new feature FooBar, put code in the following:</span></span>

- <span data-ttu-id="84804-118">Beispielszenen, Skripts werden in `MRTK/Examples/Experimental/FooBar/`</span><span class="sxs-lookup"><span data-stu-id="84804-118">Example scenes, scripts go into `MRTK/Examples/Experimental/FooBar/`</span></span>
- <span data-ttu-id="84804-119">Komponentenskripts, Prefabs gehen in `MRTK/SDK/Experimental/FooBar/`</span><span class="sxs-lookup"><span data-stu-id="84804-119">Component scripts, prefabs go into `MRTK/SDK/Experimental/FooBar/`</span></span>
- <span data-ttu-id="84804-120">Komponenteninspektoren gehen in `MRTK/SDK/Inspectors/Experimental/FooBar`</span><span class="sxs-lookup"><span data-stu-id="84804-120">Component inspectors go into `MRTK/SDK/Inspectors/Experimental/FooBar`</span></span>

<span data-ttu-id="84804-121">Wenn Sie Unterordner unter dem experimentellen Featurenamen verwenden, versuchen Sie, die gleiche Ordnerstruktur des MRTK zu spiegeln.</span><span class="sxs-lookup"><span data-stu-id="84804-121">When using sub-folders under the experimental feature name, try to mirror the same folder structure of MRTK.</span></span>

<span data-ttu-id="84804-122">Solver würden z. B. unter `MRTK/SDK/Experimental/FooBar/Features/Utilities/Solvers/FooBarSolver.cs`</span><span class="sxs-lookup"><span data-stu-id="84804-122">For example, solvers would go under `MRTK/SDK/Experimental/FooBar/Features/Utilities/Solvers/FooBarSolver.cs`</span></span>

<span data-ttu-id="84804-123">Behalten Sie Szenen in einem Szenenordner im oberen Bereich bei: `MRTK/Examples/Experimental/FooBar/Scenes/FooBarExample.unity`</span><span class="sxs-lookup"><span data-stu-id="84804-123">Keep scenes in a scene folder near the top: `MRTK/Examples/Experimental/FooBar/Scenes/FooBarExample.unity`</span></span>

> [!NOTE]
> <span data-ttu-id="84804-124">Wir haben in Betracht gezogen, keinen einzelnen experimentellen Stammordner zu haben und stattdessen Experimental unter zu `MRTK/Examples/HandTracking/Scenes/Experimental/HandBasedMenuExample.unity` speichern.</span><span class="sxs-lookup"><span data-stu-id="84804-124">We considered not having a single Experimental root folder and instead putting Experimental under say `MRTK/Examples/HandTracking/Scenes/Experimental/HandBasedMenuExample.unity`.</span></span> <span data-ttu-id="84804-125">Wir haben uns entschieden, mit Ordnern an der Basis zu arbeiten, um die experimentellen Features leichter zu finden.</span><span class="sxs-lookup"><span data-stu-id="84804-125">We decided to go with folders at the base to make the experimental features easier to discover.</span></span>

### <a name="experimental-code-should-be-in-a-special-namespace"></a><span data-ttu-id="84804-126">Experimenteller Code sollte sich in einem speziellen Namespace befinden.</span><span class="sxs-lookup"><span data-stu-id="84804-126">Experimental code should be in a special namespace</span></span>

<span data-ttu-id="84804-127">Stellen Sie sicher, dass sich der experimentelle Code in einem experimentellen Namespace befindet, der dem nicht experimentellen Speicherort entspricht.</span><span class="sxs-lookup"><span data-stu-id="84804-127">Ensure that the experimental code lives in an experimental namespace that matches the non-experimental location.</span></span> <span data-ttu-id="84804-128">Wenn Ihre Komponente beispielsweise Teil von Solvern unter `Microsoft.MixedReality.Toolkit.Utilities.Solvers` ist, sollte ihr Namespace `Microsoft.MixedReality.Toolkit.Experimental.Utilities.Solvers` sein.</span><span class="sxs-lookup"><span data-stu-id="84804-128">For example, if your component is part of solvers at `Microsoft.MixedReality.Toolkit.Utilities.Solvers`, its namespace should be `Microsoft.MixedReality.Toolkit.Experimental.Utilities.Solvers`.</span></span>

<span data-ttu-id="84804-129">Ein Beispiel finden Sie in diesem [PR.](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532)</span><span class="sxs-lookup"><span data-stu-id="84804-129">See [this PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532) for an example.</span></span>

### <a name="experimental-features-should-have-an-experimental-attribute"></a><span data-ttu-id="84804-130">Experimentelle Features sollten ein [Experimental]-Attribut haben.</span><span class="sxs-lookup"><span data-stu-id="84804-130">Experimental features should have an [Experimental] attribute</span></span>

<span data-ttu-id="84804-131">Fügen Sie ein Attribut über einem Ihrer Felder hinzu, damit ein kleiner Dialog im Komponenten-Editor angezeigt wird, in dem erwähnt wird, dass Ihr Feature experimentell ist und `[Experimental]` erheblichen Änderungen unterliegt.</span><span class="sxs-lookup"><span data-stu-id="84804-131">Add an `[Experimental]` attribute above one of your fields to have a small dialog appear in the component editor that mentions your feature is experimental and subject to significant changes.</span></span>

### <a name="menus-for-experimental-features-should-go-under-experimental-sub-menu"></a><span data-ttu-id="84804-132">Menüs für experimentelle Features sollten unter dem Untermenü "Experimentell" angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="84804-132">Menus for experimental features should go under "Experimental" sub-menu</span></span>

<span data-ttu-id="84804-133">Stellen Sie sicher, dass experimentelle Features unter "experimentellen" Untermenüs stehen, wenn Sie Menüs im Editor Befehle hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="84804-133">Ensure that experimental features are under "experimental" sub-menus when adding commands to menus in the editor.</span></span> <span data-ttu-id="84804-134">Hier sind einige Beispiele:</span><span class="sxs-lookup"><span data-stu-id="84804-134">Here are a few examples:</span></span>

<span data-ttu-id="84804-135">Hinzufügen eines Menübefehls der obersten Ebene:</span><span class="sxs-lookup"><span data-stu-id="84804-135">Adding a top-level menu command:</span></span>

```c#
[MenuItem("Mixed Reality Toolkit/Experimental/MyCommand")]
public static void MyCommand()
```

<span data-ttu-id="84804-136">Hinzufügen eines Komponentenmenüs:</span><span class="sxs-lookup"><span data-stu-id="84804-136">Adding a component menu:</span></span>

```c#
[AddComponentMenu("MRTK/Experimental/MyCommand")]
```

## <a name="documentation"></a><span data-ttu-id="84804-137">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="84804-137">Documentation</span></span>

<span data-ttu-id="84804-138">Führen Sie die folgenden Schritte aus, um Dokumentation für Ihr experimentelles Feature hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="84804-138">Follow these steps to add documentation for your experimental feature:</span></span>

1. <span data-ttu-id="84804-139">Jede Dokumentation für ein experimentelles Feature sollte in einer `readme.md` Datei im experimentellen Ordner enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="84804-139">Any documentation for an experimental feature should go in a `readme.md` file in the experimental folder.</span></span> <span data-ttu-id="84804-140">Beispiel: MRTK/SDK/Experimental/PulseShader/readme.md.</span><span class="sxs-lookup"><span data-stu-id="84804-140">For example, MRTK/SDK/Experimental/PulseShader/readme.md.</span></span>

1. <span data-ttu-id="84804-141">Fügen *Sie unter Featureübersichten* im Abschnitt *Experimentell* unter einen Link [`Documentation/toc.yml`](../toc.yml) hinzu.</span><span class="sxs-lookup"><span data-stu-id="84804-141">Under *Feature Overviews* Add a link in the *Experimental* section at [`Documentation/toc.yml`](../toc.yml).</span></span>

### <a name="minimize-impact-to-mrtk-code"></a><span data-ttu-id="84804-142">Minimieren der Auswirkungen auf MRTK-Code</span><span class="sxs-lookup"><span data-stu-id="84804-142">Minimize impact to MRTK code</span></span>

<span data-ttu-id="84804-143">Während Ihre MRTK-Änderung möglicherweise dazu beikommt, dass Ihr Experiment funktioniert, kann dies andere Personen in einer Weise beeinflussen, die Sie nicht erwarten.</span><span class="sxs-lookup"><span data-stu-id="84804-143">While your MRTK change might get your experiment to work, it could impact other people in ways you do not expect.</span></span>
<span data-ttu-id="84804-144">Alle Regressionen, die Sie am MRTK-Kerncode ausführen, würden dazu führen, dass Ihr Pull Request zurückgewollt wird.</span><span class="sxs-lookup"><span data-stu-id="84804-144">Any regressions you make to the MRTK core code would result in your pull request getting reverted.</span></span>

<span data-ttu-id="84804-145">Ziel ist es, keine Änderungen an anderen Ordnern als experimentellen Ordnern vorzunehmen.</span><span class="sxs-lookup"><span data-stu-id="84804-145">Aim to have zero changes in folders other than experimental folders.</span></span> <span data-ttu-id="84804-146">Im Folgenden finden Sie eine Liste der Ordner, die experimentelle Änderungen aufweisen können:</span><span class="sxs-lookup"><span data-stu-id="84804-146">Here is a list of folders that can have experimental changes:</span></span>

- <span data-ttu-id="84804-147">MRTK/SDK/Experimentell</span><span class="sxs-lookup"><span data-stu-id="84804-147">MRTK/SDK/Experimental</span></span>
- <span data-ttu-id="84804-148">MRTK/SDK/Inspectors/Experimental</span><span class="sxs-lookup"><span data-stu-id="84804-148">MRTK/SDK/Inspectors/Experimental</span></span>
- <span data-ttu-id="84804-149">MRTK/Examples/Experimental</span><span class="sxs-lookup"><span data-stu-id="84804-149">MRTK/Examples/Experimental</span></span>

<span data-ttu-id="84804-150">Änderungen außerhalb dieser Ordner sollten sehr sorgfältig behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="84804-150">Changes outside of these folders should be treated very carefully.</span></span> <span data-ttu-id="84804-151">Wenn Ihr experimentelles Feature Änderungen am MRTK-Kerncode enthalten muss, sollten Sie die MRTK-Änderungen in einen separaten Pull Request aufteilen, der Tests und Dokumentation enthält.</span><span class="sxs-lookup"><span data-stu-id="84804-151">If your experimental feature must include changes to MRTK core code, consider splitting out MRTK changes into a separate pull request that includes tests and documentation.</span></span>

### <a name="using-your-experimental-feature-should-not-impact-peoples-ability-to-use-core-controls"></a><span data-ttu-id="84804-152">Die Verwendung Ihres experimentellen Features sollte sich nicht auf die Fähigkeit von Personen auswirken, Kernsteuerelemente zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="84804-152">Using your experimental feature should not impact people's ability to use core controls</span></span>

<span data-ttu-id="84804-153">Die meisten Benutzer verwenden kernige UX-Komponenten wie die Schaltfläche, ManipulationHandler und Interactable sehr häufig.</span><span class="sxs-lookup"><span data-stu-id="84804-153">Most people use core UX components like the button, ManipulationHandler and Interactable very frequently.</span></span> <span data-ttu-id="84804-154">Sie verwenden ihr experimentelles Feature wahrscheinlich nicht, wenn es sie daran hindert, Schaltflächen zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="84804-154">They will likely not use your experimental feature if it prevents them from using buttons.</span></span>

<span data-ttu-id="84804-155">Wenn Sie Ihre Komponente verwenden, sollten Sie schaltflächen, ManipulationHandler, BoundingBox oder interaktiv nicht unterbrechen.</span><span class="sxs-lookup"><span data-stu-id="84804-155">Using your component should not break buttons, ManipulationHandler, BoundingBox, or interactable.</span></span>

<span data-ttu-id="84804-156">Beispielsweise hat das Hinzufügen einer ScrollableObjectCollection in [diesem ScrollableObjectCollection-PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6001)dazu geführt, dass Benutzer die Prefabs der HoloLens-Schaltfläche nicht verwenden konnten.</span><span class="sxs-lookup"><span data-stu-id="84804-156">For example, in [this ScrollableObjectCollection PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6001), adding a ScrollableObjectCollection caused people to not be able to use the HoloLens button prefabs.</span></span> <span data-ttu-id="84804-157">Obwohl dies nicht durch einen Fehler im PR verursacht wurde (sondern stattdessen einen vorhandenen Fehler verfügbar gemacht hat), verhinderte dies, dass der PR eingecheckt wurde.</span><span class="sxs-lookup"><span data-stu-id="84804-157">Even though this was not caused by a bug in the PR (but rather exposed an existing bug), it prevented the PR from getting checked in.</span></span>

### <a name="provide-an-example-scene-that-demonstrates-how-to-use-the-feature"></a><span data-ttu-id="84804-158">Bereitstellen einer Beispielszene, die die Verwendung des Features veranschaulicht</span><span class="sxs-lookup"><span data-stu-id="84804-158">Provide an example scene that demonstrates how to use the feature</span></span>

<span data-ttu-id="84804-159">Die Benutzer müssen wissen, wie Sie Ihr Feature verwenden und testen können.</span><span class="sxs-lookup"><span data-stu-id="84804-159">People need to see how to use your feature, and how to test it.</span></span>

<span data-ttu-id="84804-160">Geben Sie unter MRTK/Examples/Experimental/YOUR_FEATURE ein Beispiel an.</span><span class="sxs-lookup"><span data-stu-id="84804-160">Provide an example under MRTK/Examples/Experimental/YOUR_FEATURE</span></span>

### <a name="minimize-user-visible-flaws-in-experimental-features"></a><span data-ttu-id="84804-161">Minimieren sichtbarer Benutzerfehler in experimentellen Features</span><span class="sxs-lookup"><span data-stu-id="84804-161">Minimize user visible flaws in experimental features</span></span>

<span data-ttu-id="84804-162">Andere verwenden das experimentelle Feature nicht, wenn es nicht funktioniert, es wird nicht zu einem Feature.</span><span class="sxs-lookup"><span data-stu-id="84804-162">Others will not use the experimental feature if it does not work, it will not graduate to a feature.</span></span>

<span data-ttu-id="84804-163">Testen Sie Ihre Beispielszene auf Ihrer Zielplattform, und stellen Sie sicher, dass sie wie erwartet funktioniert.</span><span class="sxs-lookup"><span data-stu-id="84804-163">Test your example scene on your target platform, make sure it works as expected.</span></span> <span data-ttu-id="84804-164">Stellen Sie sicher, dass Ihr Feature auch im Editor funktioniert, damit Benutzer Ihr Feature schnell iterieren und anzeigen können, auch wenn sie nicht über die Zielplattform verfügen.</span><span class="sxs-lookup"><span data-stu-id="84804-164">Make sure your feature also works in editor, so people can rapidly iterate and see your feature even if they don’t have the target platform.</span></span>

## <a name="graduating-experimental-code-into-mrtk-code"></a><span data-ttu-id="84804-165">Verzweigen von experimentellem Code in MRTK-Code</span><span class="sxs-lookup"><span data-stu-id="84804-165">Graduating experimental code into MRTK code</span></span>

<span data-ttu-id="84804-166">Wenn für ein Feature eine große Nutzung zu beobachten ist, sollten wir es in KERN-MRTK-Code aufhingen.</span><span class="sxs-lookup"><span data-stu-id="84804-166">If a feature ends up seeing quite a lot of use, then we should graduate it into core MRTK code.</span></span> <span data-ttu-id="84804-167">Hierzu sollte das Feature Tests, Dokumentation und eine Beispielszene enthalten.</span><span class="sxs-lookup"><span data-stu-id="84804-167">To do this, the feature should have tests, documentation, and an example scene.</span></span>

<span data-ttu-id="84804-168">Wenn Sie bereit sind, das Feature MRTK zu aktivieren, erstellen Sie ein Problem, mit dem Sie Ihren PR überprüfen können.</span><span class="sxs-lookup"><span data-stu-id="84804-168">When you are ready to graduate the feature MRTK, create an issue to check in your PR against.</span></span> <span data-ttu-id="84804-169">Der PR sollte alle Dinge enthalten, die erforderlich sind, um dies zu einem Kernfeature zu machen: Tests, Dokumentation und eine Beispielszene, die die Verwendung zeigt.</span><span class="sxs-lookup"><span data-stu-id="84804-169">The PR should include all the things needed to make this a core feature: tests, documentation, and an example scene showing usage.</span></span>

<span data-ttu-id="84804-170">Vergessen Sie auch nicht, die Namespaces zu aktualisieren, um den Unterbereich "Experimentell" zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="84804-170">Also, don’t forget to update the namespaces to remove the “Experimental” subspace.</span></span>
