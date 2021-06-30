---
title: Komponententests
description: Komponententests zur Überprüfung der Zuverlässigkeit von MRTK.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, UnitTest,
ms.openlocfilehash: a915b005a69de1864a5674bbb0363f18d1c74b19
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121348"
---
# <a name="writing-and-running-tests-in-mrtk"></a><span data-ttu-id="8673a-104">Schreiben und Ausführen von Tests in MRTK</span><span class="sxs-lookup"><span data-stu-id="8673a-104">Writing and running tests in MRTK</span></span>

<span data-ttu-id="8673a-105">Um sicherzustellen, dass MRTK zuverlässig ist, verfügt MRTK über eine Reihe von Tests, um sicherzustellen, dass Änderungen am Code das vorhandene Verhalten nicht zurücknehmen.</span><span class="sxs-lookup"><span data-stu-id="8673a-105">To ensure MRTK is reliable, MRTK has a set of tests to ensure that changes to the code does not regress existing behavior.</span></span> <span data-ttu-id="8673a-106">Eine gute Testabdeckung in einer großen Codebasis wie MRTK ist entscheidend für Stabilität und Vertrauen beim Vornehmen von Änderungen.</span><span class="sxs-lookup"><span data-stu-id="8673a-106">Having good test coverage in a big codebase like MRTK is crucial for stability and having confidence when making changes.</span></span>

<span data-ttu-id="8673a-107">MRTK verwendet die [Unity-Test Runner,](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) die eine Unity-Integration von [NUnit](https://nunit.org/)verwendet.</span><span class="sxs-lookup"><span data-stu-id="8673a-107">MRTK uses the [Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) which uses a Unity integration of [NUnit](https://nunit.org/).</span></span> <span data-ttu-id="8673a-108">Dieser Leitfaden bietet einen Ausgangspunkt für das Hinzufügen von Tests zum MRTK.</span><span class="sxs-lookup"><span data-stu-id="8673a-108">This guide will provide a starting point on how to add tests to MRTK.</span></span> <span data-ttu-id="8673a-109">Die [Unity-Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) und [NUnit](https://nunit.org/) werden nicht erläutert, die unter den bereitgestellten Links nachverweiset werden können.</span><span class="sxs-lookup"><span data-stu-id="8673a-109">It will not explain the [Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) and [NUnit](https://nunit.org/) which can be looked up in the links provided.</span></span>

<span data-ttu-id="8673a-110">Stellen Sie vor dem Übermitteln eines Pull Requests Sicher, dass Sie:</span><span class="sxs-lookup"><span data-stu-id="8673a-110">Before submitting a pull request, make sure to:</span></span>

1. <span data-ttu-id="8673a-111">Führen Sie die Tests lokal aus, damit Ihre Änderungen das vorhandene Verhalten nicht zurücknehmen (das Abschließen von PRs ist nicht zulässig, wenn Tests fehlschlagen).</span><span class="sxs-lookup"><span data-stu-id="8673a-111">Run the tests locally so your changes don't regress existing behavior (completing PRs won't be allowed if any tests fail).</span></span>

1. <span data-ttu-id="8673a-112">Wenn Sie einen Fehler beheben, schreiben Sie einen Test, um die Korrektur zu testen, und stellen Sie sicher, dass zukünftige Codeänderungen ihn nicht erneut unterbrechen.</span><span class="sxs-lookup"><span data-stu-id="8673a-112">If fixing a bug, write a test to test the fix and ensure that future code modifications won't break it again.</span></span>

1. <span data-ttu-id="8673a-113">Wenn Sie ein Feature schreiben, schreiben Sie neue Tests, um zu verhindern, dass bevorstehende Codeänderungen dieses Feature verändern.</span><span class="sxs-lookup"><span data-stu-id="8673a-113">If writing a feature, write new tests to prevent upcoming code changes breaking this feature.</span></span>

<span data-ttu-id="8673a-114">Playmode-Tests sind derzeit für die Ausführung in Unity 2018.4 vorgesehen und können in anderen Versionen von Unity fehlschlagen.</span><span class="sxs-lookup"><span data-stu-id="8673a-114">Currently playmode tests are meant to be run in Unity 2018.4 and may fail in other versions of Unity</span></span>

## <a name="running-tests"></a><span data-ttu-id="8673a-115">Ausführen von Tests</span><span class="sxs-lookup"><span data-stu-id="8673a-115">Running tests</span></span>

### <a name="unity-editor"></a><span data-ttu-id="8673a-116">Unity-Editor</span><span class="sxs-lookup"><span data-stu-id="8673a-116">Unity editor</span></span>

<span data-ttu-id="8673a-117">Die [Unity-Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) finden Sie unter  >  **Fenster Allgemein**  >  **Test Runner** und zeigt alle verfügbaren MRTK-Wiedergabe- und Bearbeitungsmodustests an.</span><span class="sxs-lookup"><span data-stu-id="8673a-117">The [Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) can be found under **Window** > **General** > **Test Runner** and will show all available MRTK play and edit mode tests.</span></span>

### <a name="command-line"></a><span data-ttu-id="8673a-118">Befehlszeile</span><span class="sxs-lookup"><span data-stu-id="8673a-118">Command line</span></span>

<span data-ttu-id="8673a-119">Tests können auch von einem [PowerShell-Skript](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6) unter ausgeführt `Scripts\test\run_playmode_tests.ps1` werden.</span><span class="sxs-lookup"><span data-stu-id="8673a-119">Tests can also be run by a [powershell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6) script located at `Scripts\test\run_playmode_tests.ps1`.</span></span> <span data-ttu-id="8673a-120">Dadurch werden die Playmode-Tests genau so ausgeführt, wie sie auf GitHub/CI ausgeführt werden (siehe unten) und Ergebnisse drucken.</span><span class="sxs-lookup"><span data-stu-id="8673a-120">This will run the playmode tests exactly as they are executed on github / CI (see below), and print results.</span></span> <span data-ttu-id="8673a-121">Im Folgenden finden Sie einige Beispiele für die Ausführung des Skripts.</span><span class="sxs-lookup"><span data-stu-id="8673a-121">Here are some examples of how to run the script</span></span>

<span data-ttu-id="8673a-122">Führen Sie die Tests für das Projekt unter H:\mrtk.dev mit Unity 2018.4 aus (z.B. Unity 2018.4.26f1).</span><span class="sxs-lookup"><span data-stu-id="8673a-122">Run the tests on the project located at H:\mrtk.dev, with Unity 2018.4 (for example Unity 2018.4.26f1)</span></span>

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath = "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe"
```

<span data-ttu-id="8673a-123">Führen Sie die Tests für das Projekt unter H:\mrtk.dev mit Unity 2018.4 aus, und führen Sie die Ausgabeergebnisse in C:\playmode_test_out</span><span class="sxs-lookup"><span data-stu-id="8673a-123">Run the tests on the project located at H:\mrtk.dev, with Unity 2018.4, output results to C:\playmode_test_out</span></span>

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath = "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe" -outFolder "C:\playmode_test_out\"
```

<span data-ttu-id="8673a-124">Es ist auch möglich, die Playmode-Tests mehrmals über das `run_repeat_tests.ps1` Skript auszuführen.</span><span class="sxs-lookup"><span data-stu-id="8673a-124">It's also possible to run the playmode tests multiple times via the `run_repeat_tests.ps1` script.</span></span> <span data-ttu-id="8673a-125">Alle in verwendeten Parameter `run_playmode_tests.ps1` können verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="8673a-125">All parameters used in `run_playmode_tests.ps1` may be used.</span></span>

```ps
.\run_repeat_tests.ps1 -Times 5
```

### <a name="pull-request-validation"></a><span data-ttu-id="8673a-126">Pull Request-Überprüfung</span><span class="sxs-lookup"><span data-stu-id="8673a-126">Pull request validation</span></span>

<span data-ttu-id="8673a-127">Der CI von MRTK erstellt MRTK in allen Konfigurationen und führt alle Bearbeitungs- und Wiedergabemodustests aus.</span><span class="sxs-lookup"><span data-stu-id="8673a-127">MRTK's CI will build MRTK in all configurations and run all edit and play mode tests.</span></span> <span data-ttu-id="8673a-128">CI kann ausgelöst werden, indem ein Kommentar auf dem GitHub-PR gepostet `/azp run mrtk_pr` wird, wenn der Benutzer über ausreichende Rechte verfügt.</span><span class="sxs-lookup"><span data-stu-id="8673a-128">CI can be triggered by posting a comment on the github PR `/azp run mrtk_pr` if the user has sufficient rights.</span></span> <span data-ttu-id="8673a-129">CI-Ausführungen werden auf der Registerkarte "Überprüfungen" des PR angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8673a-129">CI runs can be seen in the 'checks' tab of the PR.</span></span>

<span data-ttu-id="8673a-130">Erst nachdem alle Tests erfolgreich bestanden wurden, kann der PR mit main zusammengeführt werden.</span><span class="sxs-lookup"><span data-stu-id="8673a-130">Only after all of the tests have passed successfully can the PR be merged into main.</span></span>

### <a name="stress-tests--bulk-tests"></a><span data-ttu-id="8673a-131">Belastungstests/Massentests</span><span class="sxs-lookup"><span data-stu-id="8673a-131">Stress tests / bulk tests</span></span>

<span data-ttu-id="8673a-132">Manchmal schlagen Tests nur gelegentlich fehl, was das Debuggen frustrierend sein kann.</span><span class="sxs-lookup"><span data-stu-id="8673a-132">Sometimes tests will only fail occasionally which can be frustrating to debug.</span></span>

<span data-ttu-id="8673a-133">Um mehrere Testläufe lokal zu erhalten, ändern Sie die entsprechend den Testskripts.</span><span class="sxs-lookup"><span data-stu-id="8673a-133">To have multiple test runs locally, modify the according test scripts.</span></span> <span data-ttu-id="8673a-134">Das folgende Python-Skript sollte dieses Szenario vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="8673a-134">The following python script should make this scenario more convenient.</span></span>

<span data-ttu-id="8673a-135">Voraussetzung für die Ausführung des Python-Skripts ist die Installation von [Python 3.X.](https://www.python.org/downloads/)</span><span class="sxs-lookup"><span data-stu-id="8673a-135">Prerequisite for running the python script is having [Python 3.X installed](https://www.python.org/downloads/).</span></span>

<span data-ttu-id="8673a-136">Für einen einzelnen Test, der mehrmals ausgeführt werden muss:</span><span class="sxs-lookup"><span data-stu-id="8673a-136">For a single test that needs to be executed multiple times:</span></span>

```c#
[UnityTest]
public IEnumerator MyTest() {...}
```

<span data-ttu-id="8673a-137">Führen Sie Folgendes über eine Befehlszeile aus ([PowerShell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6#powershell-core) wird empfohlen)</span><span class="sxs-lookup"><span data-stu-id="8673a-137">Run the following from a command line ([PowerShell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6#powershell-core) is recommended)</span></span>

```powershell
cd scripts\tests
# Repeat the test 5 times. Default is 100
python .\generate_repeat_tests.py -n 5 -t MyTest
```

<span data-ttu-id="8673a-138">Kopieren Sie die Ausgabe, und fügen Sie sie in die Testdatei ein.</span><span class="sxs-lookup"><span data-stu-id="8673a-138">Copy and paste the output into your test file.</span></span> <span data-ttu-id="8673a-139">Das folgende Skript dient zum Ausführen mehrerer Tests nacheinander:</span><span class="sxs-lookup"><span data-stu-id="8673a-139">The following script is for running multiple tests in sequence:</span></span>

```powershell
cd scripts\tests
# Repeat the test 5 times. Default is 100
python .\generate_repeat_tests.py -n 5 -t MyTest MySecondTest
```

<span data-ttu-id="8673a-140">Die neue Testdatei sollte jetzt enthalten.</span><span class="sxs-lookup"><span data-stu-id="8673a-140">The new test file should now contain</span></span>

```c#
[UnityTest]
public IEnumerator A1MyTest0(){ yield return MyTest();}
[UnityTest]
public IEnumerator A2MyTest0(){ yield return MyTest();}
[UnityTest]
public IEnumerator A3MyTest0(){ yield return MyTest();}
[UnityTest]
public IEnumerator A4MyTest0(){ yield return MyTest();}
[UnityTest]
public IEnumerator MyTest() {...}
```

<span data-ttu-id="8673a-141">Öffnen Sie den Test Runner, und beobachten Sie die neuen Tests, die jetzt wiederholt aufgerufen werden können.</span><span class="sxs-lookup"><span data-stu-id="8673a-141">Open the test runner and observe the new tests that can now be called repeatedly.</span></span>

## <a name="writing-tests"></a><span data-ttu-id="8673a-142">Schreiben von Tests</span><span class="sxs-lookup"><span data-stu-id="8673a-142">Writing tests</span></span>

<span data-ttu-id="8673a-143">Es gibt zwei Arten von Tests, die für neuen Code hinzugefügt werden können.</span><span class="sxs-lookup"><span data-stu-id="8673a-143">There are two types of tests that can be added for new code</span></span>

* <span data-ttu-id="8673a-144">Tests im Wiedergabemodus</span><span class="sxs-lookup"><span data-stu-id="8673a-144">Play mode tests</span></span>
* <span data-ttu-id="8673a-145">Bearbeiten von Modustests</span><span class="sxs-lookup"><span data-stu-id="8673a-145">Edit mode tests</span></span>

### <a name="play-mode-tests"></a><span data-ttu-id="8673a-146">Tests im Wiedergabemodus</span><span class="sxs-lookup"><span data-stu-id="8673a-146">Play mode tests</span></span>

<span data-ttu-id="8673a-147">MRTK-Wiedergabemodustests können testen, wie Ihr neues Feature auf verschiedene Eingabequellen wie Hände oder Augen reagiert.</span><span class="sxs-lookup"><span data-stu-id="8673a-147">MRTK play mode tests have the ability to test how your new feature responds to different input sources such as hands or eyes.</span></span>

<span data-ttu-id="8673a-148">Neue Tests im Wiedergabemodus können [BasePlayModeTests erben,](xref:Microsoft.MixedReality.Toolkit.Tests) oder das folgende Gerüst kann verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="8673a-148">New play mode tests can inherit [BasePlayModeTests](xref:Microsoft.MixedReality.Toolkit.Tests) or the skeleton below can be used.</span></span>

<span data-ttu-id="8673a-149">So erstellen Sie einen neuen Wiedergabemodustest:</span><span class="sxs-lookup"><span data-stu-id="8673a-149">To create a new play mode test:</span></span>

* <span data-ttu-id="8673a-150">Navigieren Sie zu Assets > MRTK > Tests > PlayModeTests.</span><span class="sxs-lookup"><span data-stu-id="8673a-150">Navigate to Assets > MRTK > Tests > PlayModeTests</span></span>
* <span data-ttu-id="8673a-151">Klicken Sie mit der rechten Maustaste auf Create > Testing > C#-Testskript.</span><span class="sxs-lookup"><span data-stu-id="8673a-151">Right click, Create > Testing > C# Test Script</span></span>
* <span data-ttu-id="8673a-152">Ersetzen Sie die Standardvorlage durch das folgende Gerüst.</span><span class="sxs-lookup"><span data-stu-id="8673a-152">Replace the default template with the skeleton below</span></span>

```c#
#if !WINDOWS_UWP
// When the .NET scripting backend is enabled and C# projects are built
// The assembly that this file is part of is still built for the player,
// even though the assembly itself is marked as a test assembly (this is not
// expected because test assemblies should not be included in player builds).
// Because the .NET backend is deprecated in 2018 and removed in 2019 and this
// issue will likely persist for 2018, this issue is worked around by wrapping all
// play mode tests in this check.

using Microsoft.MixedReality.Toolkit.Input;
using Microsoft.MixedReality.Toolkit.Utilities;
using NUnit.Framework;
using System;
using System.Collections;
using System.Linq;
using UnityEngine;
using UnityEngine.TestTools;

namespace Microsoft.MixedReality.Toolkit.Tests
{
    class ExamplePlayModeTests
    {
        // This method is called once before we enter play mode and execute any of the tests
        // do any kind of setup here that can't be done in playmode
        public void Setup()
        {
            // eg installing unity packages is only possible in edit mode
            // so if a test requires TextMeshPro we will need to check for the package before entering play mode
            PlayModeTestUtilities.InstallTextMeshProEssentials();
        }

        // Do common setup for each of your tests here - this will be called for each individual test after entering playmode
        // Note that this uses UnitySetUp instead of [SetUp] because the init function needs to await a frame passing
        // to ensure that the MRTK system has had the chance to fully set up before the test runs.
        [UnitySetUp]
        public IEnumerator Init()
        {
            // in most play mode test cases you would want to at least create an MRTK GameObject using the default profile
            TestUtilities.InitializeMixedRealityToolkit(true);
            yield return null;
        }

        // Destroy the scene - this method is called after each test listed below has completed
        // Note that this uses UnityTearDown instead of [TearDown] because the init function needs to await a frame passing
        // to ensure that the MRTK system has fully torn down before the next test setup->run cycle starts.
        [UnityTearDown]
        public IEnumerator TearDown()
        {
            PlayModeTestUtilities.TearDown();
            yield return null;
        }

        #region Tests

        /// <summary>
        /// Skeleton for a new MRTK play mode test.
        /// </summary>
        [UnityTest]
        public IEnumerator TestMyFeature()
        {
            // ----------------------------------------------------------
            // EXAMPLE PLAY MODE TEST METHODS
            // ----------------------------------------------------------
            // Getting the input system
            // var inputSystem = PlayModeTestUtilities.GetInputSystem();

            // Creating a new test hand for input
            // var rightHand = new TestHand(Handedness.Right);
            // yield return rightHand.Show(new Vector3(0, 0, 0.5f));

            // Moving the new test hand
            // We are doing a yield return here because moving the hand to a new position
            // requires multiple frames to complete the action.
            // yield return rightHand.MoveTo(new Vector3(0, 0, 2.0f));

            // Getting a specific pointer from the hand
            // var linePointer = PointerUtils.GetPointer<LinePointer>(Handedness.Right);
            // Assert.IsNotNull(linePointer);
            // ---------------------------------------------------------

            // Your new test here
            yield return null;
        }
        #endregion
    }
}
#endif
```

### <a name="edit-mode-tests"></a><span data-ttu-id="8673a-153">Bearbeiten von Modustests</span><span class="sxs-lookup"><span data-stu-id="8673a-153">Edit mode tests</span></span>

<span data-ttu-id="8673a-154">Bearbeitungsmodustests werden im Bearbeitungsmodus von Unity ausgeführt und können im Ordner **MRTK-Tests**  >    >  **EditModeTests** im Repository Mixed Reality Toolkit hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="8673a-154">Edit mode tests are executed in Unity's edit mode and can be added under the **MRTK** > **Tests** > **EditModeTests** folder in the Mixed Reality Toolkit repo.</span></span>
<span data-ttu-id="8673a-155">Zum Erstellen eines neuen Tests kann die folgende Vorlage verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="8673a-155">To create a new test the following template can be used:</span></span>

```c#
// Copyright (c) Microsoft Corporation.
// Licensed under the MIT License.

using NUnit.Framework;

namespace Microsoft.MixedReality.Toolkit.Tests
{
    class EditModeExampleTest
    {
        [Test]
        /// the name of this method will be used as test name in the unity test runner
        public void TestEditModeExampleFeature()
        {

        }
    }
}
```

### <a name="test-naming-conventions"></a><span data-ttu-id="8673a-156">Testbenennungskonventionen</span><span class="sxs-lookup"><span data-stu-id="8673a-156">Test naming conventions</span></span>

<span data-ttu-id="8673a-157">Tests sollten in der Regel basierend auf der Klasse benannt werden, die sie testen, oder dem Szenario, das sie testen.</span><span class="sxs-lookup"><span data-stu-id="8673a-157">Tests should generally be named based on the class they are testing, or the scenario that they are testing.</span></span>
<span data-ttu-id="8673a-158">Beispiel für eine zu testende Klasse:</span><span class="sxs-lookup"><span data-stu-id="8673a-158">For example, given a to-be-tested class:</span></span>

```c#
namespace Microsoft.MixedReality.Toolkit.Input
{
    class InterestingInputClass
    {
    }
}
```

<span data-ttu-id="8673a-159">Benennen sie den Test.</span><span class="sxs-lookup"><span data-stu-id="8673a-159">Consider naming the test</span></span>

```c#
namespace Microsoft.MixedReality.Toolkit.Tests.Input
{
    class InterestingInputClassTest
    {
    }
}
```

<span data-ttu-id="8673a-160">Erwägen Sie, den Test in einer Ordnerhierarchie zu platzieren, die der entsprechenden Nicht-Testdatei ähnelt.</span><span class="sxs-lookup"><span data-stu-id="8673a-160">Consider placing the test in a folder hierarchy that is similar to its corresponding non-test file.</span></span>
<span data-ttu-id="8673a-161">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="8673a-161">For example:</span></span>

```md
Non-Test: Assets/MRTK/Core/Utilities/InterestingUtilityClass.cs
Test: Assets/MRTK/Tests/EditModeTests/Core/Utilities/InterestingUtilityClassTest.cs
```

<span data-ttu-id="8673a-162">Dadurch wird sichergestellt, dass es eine klare Möglichkeit gibt, die entsprechende Testklasse jeder Klasse zu finden, wenn eine solche Testklasse vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="8673a-162">This is to ensure that there's a clear an obvious way of finding each class's corresponding test class, if such a test class exists.</span></span>

<span data-ttu-id="8673a-163">Die Platzierung von szenariobasierten Tests ist weniger definiert: Wenn der Test beispielsweise das gesamte Eingabesystem durchsetzt, sollten Sie es in einen Ordner "InputSystem" im entsprechenden Bearbeitungsmodus oder Testordner für den Wiedergabemodus platzieren.</span><span class="sxs-lookup"><span data-stu-id="8673a-163">Placement of scenario based tests is less defined - if the test exercises the overall input system, for example, consider putting it into an "InputSystem" folder in the corresponding edit mode or play mode test folder.</span></span>

### <a name="test-script-icons"></a><span data-ttu-id="8673a-164">Testen von Skriptsymbolen</span><span class="sxs-lookup"><span data-stu-id="8673a-164">Test script icons</span></span>

<span data-ttu-id="8673a-165">Wenn Sie einen neuen Test hinzufügen, ändern Sie das Skript, um das richtige MRTK-Symbol zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="8673a-165">When adding a new test, please modify the script to have the correct MRTK icon.</span></span> <span data-ttu-id="8673a-166">Hierzu gibt es ein einfaches MRTK-Tool:</span><span class="sxs-lookup"><span data-stu-id="8673a-166">There's an easy MRTK tool to do so:</span></span>

1. <span data-ttu-id="8673a-167">Go go the Mixed Reality Toolkit menu item</span><span class="sxs-lookup"><span data-stu-id="8673a-167">Go go the Mixed Reality Toolkit menu item</span></span>
1. <span data-ttu-id="8673a-168">Klicken Sie auf Hilfsprogramme, aktualisieren und dann auf Symbole.</span><span class="sxs-lookup"><span data-stu-id="8673a-168">Click on Utilities, then Update, then Icons</span></span>
1. <span data-ttu-id="8673a-169">Klicken Sie auf Tests, und der Updater wird automatisch ausgeführt, wobei alle Testskripts aktualisiert werden, deren Symbole fehlen.</span><span class="sxs-lookup"><span data-stu-id="8673a-169">Click on Tests, and the updater will run automatically, updating any test scripts missing their icons</span></span>

### <a name="mrtk-utility-methods"></a><span data-ttu-id="8673a-170">MRTK-Hilfsprogrammmethoden</span><span class="sxs-lookup"><span data-stu-id="8673a-170">MRTK Utility methods</span></span>

<span data-ttu-id="8673a-171">Dieser Abschnitt zeigt einige der häufig verwendeten Codeausschnitte/-methoden beim Schreiben von Tests für MRTK.</span><span class="sxs-lookup"><span data-stu-id="8673a-171">This section shows some of the commonly used code snippets / methods when writing tests for MRTK.</span></span>

<span data-ttu-id="8673a-172">Es gibt zwei Hilfsprogrammklassen, die beim Einrichten von MRTK und beim Testen von Interaktionen mit Komponenten in MRTK helfen.</span><span class="sxs-lookup"><span data-stu-id="8673a-172">There are two Utility classes that help with setting up MRTK and testing interactions with components in MRTK</span></span>

* [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities)
* [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities)

<span data-ttu-id="8673a-173">TestUtilities bietet die folgenden Methoden zum Einrichten Ihrer MRTK-Szene und GameObjects:</span><span class="sxs-lookup"><span data-stu-id="8673a-173">TestUtilities provide the following methods to set up your MRTK scene and GameObjects:</span></span>

```c#
/// creates the mrtk GameObject and sets the default profile if passed param is true
TestUtilities.InitializeMixedRealityToolkit()

/// creates an empty scene prior to adding the mrtk GameObject to it
TestUtilities.InitializeMixedRealityToolkitAndCreateScenes();

/// sets the initial playspace transform and camera position
TestUtilities.InitializePlayspace();

/// destroys previously created mrtk GameObject and playspace
TestUtilities.ShutdownMixedRealityToolkit();
```

<span data-ttu-id="8673a-174">Weitere Methoden dieser util-Klassen finden Sie in der API-Dokumentation von und , [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities) [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities) da sie in regelmäßigen Abständen erweitert werden, während mrtk neue Tests hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="8673a-174">Please refer to the API docs of [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities) and [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities) for further methods of these util classes as they're extended on a regular basis while new tests get added to MRTK.</span></span>