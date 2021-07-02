---
title: Schreiben und Ausführen von Tests
description: Komponententests zur Überprüfung der Zuverlässigkeit des MRTK.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, Mixed Reality, Development, MRTK, UnitTest,
ms.openlocfilehash: c8efb192982a1cb9ca07e91d29a69b11aaffc290
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177117"
---
# <a name="writing-and-running-tests"></a>Schreiben und Ausführen von Tests

Um sicherzustellen, dass MRTK zuverlässig ist, verfügt das MRTK über eine Reihe von Tests, um sicherzustellen, dass Änderungen am Code das vorhandene Verhalten nicht zurücknehmen. Eine gute Testabdeckung in einer großen Codebasis wie MRTK ist entscheidend für Stabilität und Vertrauen beim Vornehmen von Änderungen.

MRTK verwendet die [Unity-Test Runner,](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) die eine Unity-Integration von [NUnit verwendet.](https://nunit.org/) Dieser Leitfaden bietet einen Ausgangspunkt für das Hinzufügen von Tests zum MRTK. Die Unity-Test Runner [und](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) [NUnit,](https://nunit.org/) die in den bereitgestellten Links nachschaut werden können, werden nicht erläutert.

Stellen Sie vor dem Übermitteln eines Pull Requests Sicher, dass:

1. Führen Sie die Tests lokal aus, damit Ihre Änderungen das vorhandene Verhalten nicht zurücknehmen (das Abschließen von PRs ist nicht zulässig, wenn Tests fehlschlagen).

1. Wenn Sie einen Fehler beheben, schreiben Sie einen Test, um die Fehlerbehebung zu testen und sicherzustellen, dass zukünftige Codeänderungen ihn nicht erneut verhindern.

1. Wenn Sie ein Feature schreiben, schreiben Sie neue Tests, um zu verhindern, dass anstehende Codeänderungen dieses Feature verhindern.

Derzeit sind Playmodetests für die Ausführung in Unity 2018.4 gedacht und können in anderen Versionen von Unity fehlschlagen.

## <a name="running-tests"></a>Ausführen von Tests

### <a name="unity-editor"></a>Unity-Editor

Die [Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) finden Sie unter **Window** General Test Runner und zeigt alle verfügbaren MRTK-Wiedergabe- und  >    >   Bearbeitungsmodustests an.

### <a name="command-line"></a>Befehlszeile

Tests können auch von einem [PowerShell-Skript](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6) unter ausgeführt `Scripts\test\run_playmode_tests.ps1` werden. Dadurch werden die Playmodetests genau so ausgeführt, wie sie auf GitHub/CI ausgeführt werden (siehe unten) und Ergebnisse drucken. Im Folgenden finden Sie einige Beispiele zum Ausführen des Skripts.

Führen Sie die Tests für das Projekt unter H:\mrtk.dev mit Unity 2018.4 aus (z.B. Unity 2018.4.26f1).

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath = "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe"
```

Führen Sie die Tests für das Projekt unter H:\mrtk.dev mit Unity 2018.4 aus, und geben Sie die Ergebnisse in C:\playmode_test_out

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath = "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe" -outFolder "C:\playmode_test_out\"
```

Es ist auch möglich, die Playmodetests mehrmals über das Skript `run_repeat_tests.ps1` auszuführen. Alle in verwendeten `run_playmode_tests.ps1` Parameter können verwendet werden.

```ps
.\run_repeat_tests.ps1 -Times 5
```

### <a name="pull-request-validation"></a>Pull Request-Überprüfung

Die CI des MRTK wird MRTK in allen Konfigurationen erstellen und alle Bearbeitungs- und Wiedergabemodustests ausführen. CI kann ausgelöst werden, indem ein Kommentar auf dem GitHub-PR veröffentlicht `/azp run mrtk_pr` wird, wenn der Benutzer über ausreichende Rechte verfügt. CI-Läufe werden auf der Registerkarte "Überprüfungen" des PR angezeigt.

Erst nachdem alle Tests erfolgreich bestanden wurden, kann der PR mit main zusammengeführt werden.

### <a name="stress-tests--bulk-tests"></a>Belastungstests/Massentests

Manchmal schlagen Tests nur gelegentlich fehl, was das Debuggen frustrieren kann.

Um mehrere Testläufe lokal zu haben, ändern Sie die entsprechend Testskripts. Das folgende Python-Skript sollte dieses Szenario praktischer machen.

Voraussetzung für die Ausführung des Python-Skripts ist, [dass Python 3.X installiert ist.](https://www.python.org/downloads/)

Für einen einzelnen Test, der mehrmals ausgeführt werden muss:

```c#
[UnityTest]
public IEnumerator MyTest() {...}
```

Führen Sie Folgendes über eine Befehlszeile aus[(PowerShell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6#powershell-core) wird empfohlen).

```powershell
cd scripts\tests
# Repeat the test 5 times. Default is 100
python .\generate_repeat_tests.py -n 5 -t MyTest
```

Kopieren Sie die Ausgabe, und fügen Sie sie in Die Testdatei ein. Mit dem folgenden Skript werden mehrere Tests nacheinander ausgeführt:

```powershell
cd scripts\tests
# Repeat the test 5 times. Default is 100
python .\generate_repeat_tests.py -n 5 -t MyTest MySecondTest
```

Die neue Testdatei sollte jetzt enthalten.

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

Öffnen Sie den Test Runner, und beobachten Sie die neuen Tests, die jetzt wiederholt aufgerufen werden können.

## <a name="writing-tests"></a>Schreiben von Tests

Es gibt zwei Arten von Tests, die für neuen Code hinzugefügt werden können.

* Tests im Wiedergabemodus
* Bearbeiten von Modustests

### <a name="play-mode-tests"></a>Tests im Wiedergabemodus

MRTK-Wiedergabemodustests können testen, wie Ihr neues Feature auf verschiedene Eingabequellen wie Hände oder Augen reagiert.

Neue Wiedergabemodustests können [BasePlayModeTests erben,](xref:Microsoft.MixedReality.Toolkit.Tests) oder das folgende Gerüst kann verwendet werden.

So erstellen Sie einen neuen Wiedergabemodustest:

* Navigieren Sie zu Assets > MRTK > Tests > PlayModeTests.
* Klicken Sie mit der rechten Maustaste auf > Testing > C#-Testskripts.
* Ersetzen Sie die Standardvorlage durch das folgende Gerüst.

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

### <a name="edit-mode-tests"></a>Bearbeiten von Modustests

Bearbeitungsmodustests werden im Bearbeitungsmodus von Unity ausgeführt und können im Repository des Mixed Reality Toolkits unter dem Ordner **MRTK** Tests  >    >  **EditModeTests** hinzugefügt werden.
Zum Erstellen eines neuen Tests kann die folgende Vorlage verwendet werden:

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

### <a name="test-naming-conventions"></a>Testbenennungskonventionen

Tests sollten in der Regel basierend auf der Klasse benannt werden, die sie testen, oder dem Szenario, in dem sie getestet werden.
Beispiel für eine zu testete Klasse:

```c#
namespace Microsoft.MixedReality.Toolkit.Input
{
    class InterestingInputClass
    {
    }
}
```

Benennen Sie den Test.

```c#
namespace Microsoft.MixedReality.Toolkit.Tests.Input
{
    class InterestingInputClassTest
    {
    }
}
```

Erwägen Sie, den Test in einer Ordnerhierarchie zu platzieren, die der entsprechenden Nicht-Testdatei ähnelt.
Beispiel:

```md
Non-Test: Assets/MRTK/Core/Utilities/InterestingUtilityClass.cs
Test: Assets/MRTK/Tests/EditModeTests/Core/Utilities/InterestingUtilityClassTest.cs
```

Dadurch wird sichergestellt, dass es eine klare Möglichkeit gibt, die entsprechende Testklasse jeder Klasse zu finden, wenn eine solche Testklasse vorhanden ist.

Die Platzierung szenariobasierter Tests ist weniger definiert. Wenn der Test z. B. das gesamte Eingabesystem austestet, sollten Sie es in einen Ordner "InputSystem" im entsprechenden Testordner für den Bearbeitungs- oder Wiedergabemodus platzieren.

### <a name="test-script-icons"></a>Testskriptsymbole

Wenn Sie einen neuen Test hinzufügen, ändern Sie das Skript, um das richtige MRTK-Symbol zu erhalten. Dazu gibt es ein einfaches MRTK-Tool:

1. Wechseln Sie zum Menüelement Mixed Reality Toolkit.
1. Klicken Sie auf Hilfsprogramme, dann auf Aktualisieren und dann auf Symbole.
1. Klicken Sie auf Tests, und der Updater wird automatisch ausgeführt und aktualisiert alle Testskripts, deren Symbole fehlen.

### <a name="mrtk-utility-methods"></a>MRTK-Hilfsprogrammmethoden

Dieser Abschnitt zeigt einige der häufig verwendeten Codeausschnitte/-methoden beim Schreiben von Tests für MRTK.

Es gibt zwei Hilfsprogrammklassen, die beim Einrichten des MRTK und beim Testen von Interaktionen mit Komponenten in MRTK helfen.

* [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities)
* [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities)

TestUtilities bietet die folgenden Methoden zum Einrichten Ihrer MRTK-Szene und GameObjects:

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

Weitere Methoden dieser util-Klassen finden Sie in den API-Dokumentationen von und , da sie regelmäßig erweitert werden, während dem [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities) [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities) MRTK neue Tests hinzugefügt werden.
