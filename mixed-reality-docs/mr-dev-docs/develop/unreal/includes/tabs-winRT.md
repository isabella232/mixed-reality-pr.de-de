---
ms.openlocfilehash: 555360092a65b80a1298eb779736b29360f8c6e13bd1834994f316043843b47a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198383"
---
# <a name="426"></a>[4.26](#tab/426)

## <a name="the-standard-winrt-apis"></a>Die WinRT-Standard-APIs

Die gängigste und einfachste Möglichkeit zur Verwendung von WinRT ist das Aufrufen von Methoden aus WinSDK. Öffnen Sie hierzu die Datei YourModule.Build.cs, und fügen Sie die folgenden Zeilen hinzu:

```csharp
if (Target.Platform == UnrealTargetPlatform.Win64 || Target.Platform == UnrealTargetPlatform.HoloLens)
{
    // These parameters are mandatory for winrt support
    bEnableExceptions = true;
    bUseUnity = false;
    CppStandard = CppStandardVersion.Cpp17;
    PublicSystemLibraries.AddRange(new string[] { "shlwapi.lib", "runtimeobject.lib" });
    PrivateIncludePaths.Add(Path.Combine(Target.WindowsPlatform.WindowsSdkDir,        
                                        "Include", 
                                        Target.WindowsPlatform.WindowsSdkVersion, 
                                        "cppwinrt"));
}
```

Als Nächstes müssen Sie die folgenden WinRT-Header hinzufügen: 

```cpp
#if (PLATFORM_WINDOWS || PLATFORM_HOLOLENS) 
//Before writing any code, you need to disable common warnings in WinRT headers
#pragma warning(disable : 5205 4265 4268 4946)

#include "Windows/AllowWindowsPlatformTypes.h"
#include "Windows/AllowWindowsPlatformAtomics.h"
#include "Windows/PreWindowsApi.h"

#include <unknwn.h>
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Perception.Spatial.h>
#include <winrt/Windows.Foundation.Collections.h>

#include "Windows/PostWindowsApi.h"
#include "Windows/HideWindowsPlatformAtomics.h"
#include "Windows/HideWindowsPlatformTypes.h"
#endif
```

WinRT-Code kann nur auf win64- und HoloLens-Plattformen kompiliert werden, sodass die if-Anweisung verhindert, dass WinRT-Bibliotheken auf anderen Plattformen enthalten sind. unknwn.h wurde hinzugefügt, um die IUnknown-Schnittstelle zu verwenden. 


## <a name="winrt-from-a-nuget-package"></a>WinRT aus einem NuGet-Paket

Es ist etwas komplizierter, wenn Sie ein NuGet-Paket mit WinRT-Unterstützung hinzufügen müssen. In diesem Fall können Visual Studio praktisch alle Aufgaben für Sie erledigen, das Unreal-Buildsystem jedoch nicht. Glücklicherweise ist es nicht zu schwierig. Im Folgenden finden Sie ein Beispiel für das Herunterladen des Pakets Microsoft.MixedReality.QR. Sie können sie durch eine andere ersetzen. Stellen Sie einfach sicher, dass Sie die winmd-Datei nicht verlieren und die richtige DLL kopieren. 

Windows SDK-DLLs aus dem vorherigen Abschnitt werden vom Betriebssystem verarbeitet. NuGet DLL-Dateien müssen vom Code in Ihrem Modul verwaltet werden. Es wird empfohlen, Code hinzuzufügen, um sie herunterzuladen, in den Ordner "Binärdateien" zu kopieren und beim Start des Moduls in den Prozessspeicher zu laden.

Im ersten Schritt sollten Sie dem Stammordner Ihres Moduls einen packages.config ( https://docs.microsoft.com/nuget/reference/packages-config) hinzufügen. Dort sollten Sie alle Pakete hinzufügen, die Sie herunterladen möchten, einschließlich aller abhängigkeiten. Hier habe ich Microsoft.MixedReality.QR als primäre Nutzlast und zwei weitere als Abhängigkeiten hinzugefügt. Das Format dieser Datei entspricht Visual Studio:

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
  <package id="Microsoft.MixedReality.QR" version="0.5.2102" targetFramework="native" />
  <package id="Microsoft.VCRTForwarders.140" version="1.0.6" targetFramework="native" />
  <package id="Microsoft.Windows.CppWinRT" version="2.0.200729.8" targetFramework="native" />
</packages>
```

Jetzt können Sie die NuGet, die erforderlichen Pakete oder die [NuGet-Dokumentation](/nuget/consume-packages/install-use-packages-nuget-cli)herunterladen.

Öffnen Sie YourModule.Build.cs, und fügen Sie den folgenden Code hinzu:

```csharp
// WinRT with Nuget support
if (Target.Platform == UnrealTargetPlatform.Win64 || Target.Platform == UnrealTargetPlatform.HoloLens)
{
    // these parameters mandatory for winrt support
    bEnableExceptions = true;
    bUseUnity = false;
    CppStandard = CppStandardVersion.Cpp17;
    PublicSystemLibraries.AddRange(new string [] { "shlwapi.lib", "runtimeobject.lib" });

    // prepare everything for nuget
    string MyModuleName = GetType().Name;
    string NugetFolder = Path.Combine(PluginDirectory, "Intermediate", "Nuget", MyModuleName);
    Directory.CreateDirectory(NugetFolder);

    string BinariesSubFolder = Path.Combine("Binaries", "ThirdParty", Target.Type.ToString(), Target.Platform.ToString(), Target.Architecture);

    PrivateDefinitions.Add(string.Format("THIRDPARTY_BINARY_SUBFOLDER=\"{0}\"", BinariesSubFolder.Replace(@"\", @"\\")));

    string BinariesFolder = Path.Combine(PluginDirectory, BinariesSubFolder);
    Directory.CreateDirectory(BinariesFolder);

    ExternalDependencies.Add("packages.config");

    // download nuget
    string NugetExe = Path.Combine(NugetFolder, "nuget.exe");
    if (!File.Exists(NugetExe))
    {
        using (System.Net.WebClient myWebClient = new System.Net.WebClient())
        {
            // we aren't focusing on a specific nuget version, we can use any of them but the latest one is preferable
            myWebClient.DownloadFile(@"https://dist.nuget.org/win-x86-commandline/latest/nuget.exe", NugetExe);
        }
    }

    // run nuget to update the packages
    {
        var StartInfo = new System.Diagnostics.ProcessStartInfo(NugetExe, string.Format("install \"{0}\" -OutputDirectory \"{1}\"", Path.Combine(ModuleDirectory, "packages.config"), NugetFolder));
        StartInfo.UseShellExecute = false;
        StartInfo.CreateNoWindow = true;
        var ExitCode = Utils.RunLocalProcessAndPrintfOutput(StartInfo);
        if (ExitCode < 0)
        {
            throw new BuildException("Failed to get nuget packages.  See log for details.");
        }
    }

    // get list of the installed packages, that's needed because the code should get particular versions of the installed packages
    string[] InstalledPackages = Utils.RunLocalProcessAndReturnStdOut(NugetExe, string.Format("list -Source \"{0}\"", NugetFolder)).Split(new char[] { '\r', '\n' });

    // winmd files of the packages
    List<string> WinMDFiles = new List<string>();

    // WinRT lib for some job
    string QRPackage = InstalledPackages.FirstOrDefault(x => x.StartsWith("Microsoft.MixedReality.QR"));
    if (!string.IsNullOrEmpty(QRPackage))
    {
        string QRFolderName = QRPackage.Replace(" ", ".");

        // copying dll and winmd binaries to our local binaries folder
        // !!!!! please make sure that you use the path of file! Unreal can't do it for you !!!!!
        string WinMDFile = Path.Combine(NugetFolder, QRFolderName, @"lib\uap10.0.18362\Microsoft.MixedReality.QR.winmd");
        SafeCopy(WinMDFile, Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.winmd"));

        SafeCopy(Path.Combine(NugetFolder, QRFolderName, string.Format(@"runtimes\win10-{0}\native\Microsoft.MixedReality.QR.dll", Target.WindowsPlatform.Architecture.ToString())),
            Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.dll"));

        // also both both binaries must be in RuntimeDependencies, unless you get failures in Hololens platform
        RuntimeDependencies.Add(Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.dll"));
        RuntimeDependencies.Add(Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.winmd"));

        //add winmd file to the list for further processing using cppwinrt.exe
        WinMDFiles.Add(WinMDFile);
    }

    if (Target.Platform == UnrealTargetPlatform.Win64)
    {
        // Microsoft.VCRTForwarders.140 is needed to run WinRT dlls in Win64 platforms
        string VCRTForwardersPackage = InstalledPackages.FirstOrDefault(x => x.StartsWith("Microsoft.VCRTForwarders.140"));
        if (!string.IsNullOrEmpty(VCRTForwardersPackage))
        {
            string VCRTForwardersName = VCRTForwardersPackage.Replace(" ", ".");
            foreach (var Dll in Directory.EnumerateFiles(Path.Combine(NugetFolder, VCRTForwardersName, "runtimes/win10-x64/native/release"), "*_app.dll"))
            {
                string newDll = Path.Combine(BinariesFolder, Path.GetFileName(Dll));
                SafeCopy(Dll, newDll);
                RuntimeDependencies.Add(newDll);
            }
        }
    }

    // get WinRT package 
    string CppWinRTPackage = InstalledPackages.FirstOrDefault(x => x.StartsWith("Microsoft.Windows.CppWinRT"));
    if (!string.IsNullOrEmpty(CppWinRTPackage))
    {
        string CppWinRTName = CppWinRTPackage.Replace(" ", ".");
        string CppWinRTExe = Path.Combine(NugetFolder, CppWinRTName, "bin", "cppwinrt.exe");
        string CppWinRTFolder = Path.Combine(PluginDirectory, "Intermediate", CppWinRTName, MyModuleName);
        Directory.CreateDirectory(CppWinRTFolder);

        // all downloaded winmd file with WinSDK to be processed by cppwinrt.exe
        var WinMDFilesStringbuilder = new System.Text.StringBuilder();
        foreach (var winmd in WinMDFiles)
        {
            WinMDFilesStringbuilder.Append(" -input \"");
            WinMDFilesStringbuilder.Append(winmd);
            WinMDFilesStringbuilder.Append("\"");
        }

        // generate winrt headers and add them into include paths
        var StartInfo = new System.Diagnostics.ProcessStartInfo(CppWinRTExe, string.Format("{0} -input \"{1}\" -output \"{2}\"", WinMDFilesStringbuilder, Target.WindowsPlatform.WindowsSdkVersion, CppWinRTFolder));
        StartInfo.UseShellExecute = false;
        StartInfo.CreateNoWindow = true;
        var ExitCode = Utils.RunLocalProcessAndPrintfOutput(StartInfo);
        if (ExitCode < 0)
        {
            throw new BuildException("Failed to get generate WinRT headers.  See log for details.");
        }

        PrivateIncludePaths.Add(CppWinRTFolder);
    }
    else
    {
        // fall back to default WinSDK headers if no winrt package in our list
        PrivateIncludePaths.Add(Path.Combine(Target.WindowsPlatform.WindowsSdkDir, "Include", Target.WindowsPlatform.WindowsSdkVersion, "cppwinrt"));
    }
}
```

Sie müssen die SafeCopy-Methode wie folgt definieren:

```csharp
private void SafeCopy(string source, string destination)
{
    if(!File.Exists(source))
    {
        Log.TraceError("Class {0} can't find {1} file for copying", this.GetType().Name, source);
        return;
    }

    try
    {
        File.Copy(source, destination, true);
    }
    catch(IOException ex)
    {
        Log.TraceWarning("Failed to copy {0} to {1} with exception: {2}", source, destination, ex.Message);
        if (!File.Exists(destination))
        {
            Log.TraceError("Destination file {0} does not exist", destination);
            return;
        }

        Log.TraceWarning("Destination file {0} already existed and is probably in use.  The old file will be used for the runtime dependency.  This may happen when packaging a Win64 exe from the editor.", destination);
    }
}
```

NuGet DLLs müssen manuell in den Win32-Prozessspeicher geladen werden. Es wird empfohlen, der Startmethode Ihres Moduls manuelles Laden hinzuzufügen:

```cpp
void StartupModule() override
{
#if PLATFORM_WINDOWS
    const FString LibrariesDir = FPaths::ProjectPluginsDir() / "MyModule" / THIRDPARTY_BINARY_SUBFOLDER;
    FPlatformProcess::PushDllDirectory(*LibrariesDir);

    const FString DllName = "Microsoft.MixedReality.QR.dll";
    if (!FPlatformProcess::GetDllHandle(*DllName))
    {
        UE_LOG(LogHMD, Warning, TEXT("Dll \'%s\' can't be loaded from \'%s\'"), *DllName, *LibrariesDir);
    }

    FPlatformProcess::PopDllDirectory(*LibrariesDir);
#endif
}
```

Schließlich können Sie WinRT-Header wie im vorherigen Abschnitt beschrieben in Ihren Code einfügen.

# <a name="425"></a>[4.25](#tab/425)

Unreal kompiliert WinRT-Code in Version 4.25 nicht nativ. Daher ist es Ihre Aufgabe, eine separate Binärdatei zu erstellen, die das Unreal-Buildsystem nutzen kann. 

## <a name="objectives"></a>Ziele

- Erstellen einer Universal Windows DLL, die ein FileSaveDialogue öffnet
- Verknüpfen dieser DLL mit einem Unreal-Spielprojekt
- Speichern einer Datei auf dem HoloLens aus einer Unreal-Blaupause mithilfe der neuen DLL

## <a name="getting-started"></a>Erste Schritte

1. Überprüfen Sie, ob alle [erforderlichen Tools](../tutorials/unreal-uxt-ch1.md) installiert sind.
2. [Erstellen Sie ein neues Unreal-Projekt,](../tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) und nennen Sie es **Consumewinrt.**
3. Aktivieren der [erforderlichen Plug-Ins](../tutorials/unreal-uxt-ch2.md#enabling-required-plugins) für HoloLens Entwicklung
4. [Setup für die Bereitstellung](../tutorials/unreal-uxt-ch6.md) auf einem Gerät oder Emulator

## <a name="creating-a-winrt-dll"></a>Erstellen einer WinRT-DLL 

1. Öffnen Sie ein neues Visual Studio-Projekt, und erstellen Sie ein **DLL-Projekt (Universal Windows)** im gleichen Verzeichnis wie die **uproject-Datei** des Unreal-Spiels. 

![Erstellen einer DLL](../images/unreal-winrt-img-01.png)

2. Nennen Sie das Projekt **HoloLensWinrtDLL,** und legen Sie den Speicherort als **ThirdParty-Unterverzeichnis** auf die UPROJECT-Datei des Unreal-Spiels fest. 
    * Wählen Sie **Projektmappe und Projekt im selben Verzeichnis platzieren** aus, um die Suche nach Pfaden später zu vereinfachen. 

![Konfigurieren der DLL](../images/unreal-winrt-img-02.png)

> [!IMPORTANT]
> Nachdem das neue Projekt kompiliert wurde, achten Sie besonders auf die leeren CPP- und Headerdateien namens **HoloLensWinrtDLL.cpp** bzw. **HoloLensWinrtDLL.h.** Der Header ist die Includedatei, die die DLL in Unreal verwendet, während das CPP den Text aller von Ihnen exportierten Funktionen enthält und winRT-Code enthält, den Unreal andernfalls nicht kompilieren kann. 

3. Bevor Sie Code hinzufügen, müssen Sie die Projekteigenschaften aktualisieren, um sicherzustellen, dass der benötigte WinRT-Code kompiliert werden kann: 
    * Klicken Sie mit der rechten Maustaste auf das HoloLensWinrtDLL-Projekt, und wählen Sie **Eigenschaften** aus.  
    * Ändern Sie die Dropdownliste **Konfiguration** in **Alle Konfigurationen** und die Dropdownliste **Plattform** in **Alle Plattformen.**  
    * Unter **Konfigurationseigenschaften> C/C++> Alle Optionen:**
        * Fügen Sie **await** zu **Zusätzliche Optionen** hinzu, um sicherzustellen, dass wir auf asynchrone Aufgaben warten können.  
        * Ändern Sie **den C++-Sprachstandard** in **ISO C++17 Standard (/std:c++17),** um beliebigen WinRT-Code einzuschließt.

![Aktualisieren von Projekteigenschaften](../images/unreal-winrt-img-03.png)

Ihr Projekt ist bereit, die Quelle der DLL mit WinRT-Code zu aktualisieren, der einen Dateidialog öffnet und eine Datei auf dem HoloLens Datenträger speichert.  

## <a name="adding-the-dll-code"></a>Hinzufügen des DLL-Codes

1. Öffnen Sie **HoloLensWinrtDLL.h,** und fügen Sie eine exportierte DLL-Funktion hinzu, die Unreal nutzen kann: 

```cpp
#pragma once

class HoloLensWinrtDLL
{
public:
    _declspec(dllexport) static void OpenFileDialogue();
};
```

2. Öffnen Sie **HoloLensWinrtDLL.cpp,** und fügen Sie alle Header hinzu, die die Klasse verwendet:  

```cpp
#include "pch.h"
#include "HoloLensWinrtDLL.h"

#include <winrt/Windows.Storage.h>
#include <winrt/Windows.Storage.Streams.h>
#include <winrt/Windows.Storage.Pickers.h>
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Foundation.Collections.h>

#include <string>
#include <vector>
#include <thread>
```

> [!NOTE]
> Der gesamte WinRT-Code wird in **HoloLensWinrtDLL.cpp** gespeichert, sodass Unreal beim Verweisen auf den Header nicht versucht, WinRT-Code einzubeziehen. 

3. Fügen Sie in **HoloLensWinrtDLL.cpp** einen Funktionstext für OpenFileDialogue() und den gesamten unterstützten Code hinzu: 

```cpp
// sgm is declared outside of OpenFileDialogue so it doesn't
// get destroyed when OpenFileDialogue goes out of scope.
SaveGameManager sgm;

void HoloLensWinrtDLL::OpenFileDialogue()
{
    sgm.SaveGame();
}
```

4. Fügen Sie **HoloLensWinrtDLL.cpp** eine SaveGameManager-Klasse hinzu, um das Dateidialoging zu verarbeiten und die Datei zu speichern: 

```cpp
class SaveGameManager
{
public:
    SaveGameManager()
    {
    }

    ~SaveGameManager()
    {
        // Wait for currently running thread to complete before terminating.
        if(m_thread.joinable())
        {
            m_thread.join();
        }
    }

    void SaveGame()
    {
        OpenFileDialogueAction();
    }

private:
    winrt::Windows::Storage::StorageFile m_file = winrt::Windows::Storage::StorageFile(nullptr);
    std::thread m_thread;

    winrt::Windows::Foundation::IAsyncAction OpenFileDialogueAction()
    {
        std::vector<winrt::hstring> extensions;
        extensions.push_back(L".txt");

        auto picker = winrt::Windows::Storage::Pickers::FileSavePicker();

        // FileSavePicker needs a file type to open without errors.
        picker.FileTypeChoices().Insert(L"Plain Text",
                                        winrt::single_threaded_vector<winrt::hstring>(
                                        std::move(extensions)));

        // Opening the FilePicker must be done on the Game UI thread.
        // Any other IAsyncOperations should be done on a background thread.
        m_file = co_await picker.PickSaveFileAsync();

        if(m_file)
        {
            // Unreal's game thread is an STA, async tasks need to run on
            // a background MTA thread, or waiting on them will deadlock.    
            std::thread thread([this]() { RunThread(); });
            m_thread = std::move(thread);
        }
    }

    void RunThread()
    {
        // Ensure this thread is an MTA
        winrt::init_apartment();
        Run().get();
    }

    winrt::Windows::Foundation::IAsyncAction Run()
    {
        co_await winrt::Windows::Storage::FileIO::WriteTextAsync(
                m_file, L"Hello WinRT");
    }
};
```

5. Erstellen Sie die Projektmappe für **Release > ARM64,** um die DLL im untergeordneten Verzeichnis ARM64/Release/HoloLensWinrtDLL aus der DLL-Projektmappe zu erstellen. 

## <a name="adding-the-winrt-binary-to-unreal"></a>Hinzufügen der WinRT-Binärdatei zu Unreal 
Zum Verknüpfen und Verwenden einer DLL in Unreal ist ein C++-Projekt erforderlich. Wenn Sie ein Blaupausenprojekt verwenden, können Sie es problemlos in ein C++-Projekt konvertieren, indem Sie eine C++-Klasse hinzufügen:  

1. Öffnen Sie im Unreal-Editor **Datei > Neue C++-Klasse...** und erstellen Sie einen neuen **Akteur** mit dem Namen **WinrtActor,** um den Code in der DLL auszuführen: 

![Erstellen eines neuen Akteurs](../images/unreal-winrt-img-04.png)

> [!NOTE]
> Eine Projektmappe wurde nun im selben Verzeichnis wie die uproject-Datei zusammen mit einem neuen Buildskript mit dem Namen Source/ConsumeWinRT/ConsumeWinRT.Build.cs erstellt.

2. Öffnen Sie die Projektmappe, suchen Sie nach dem Ordner **Games/ConsumeWinRT/Source/ConsumeWinRT,** und öffnen **Sie ConsumeWinRT.build.cs:**

![Öffnen der Datei ConsumeWinRT.build.cs](../images/unreal-winrt-img-05.png)

### <a name="linking-the-dll"></a>Verknüpfen der DLL
1. Fügen **Sie in ConsumeWinRT.build.cs** eine Eigenschaft hinzu, um den Includepfad für die DLL zu suchen (das Verzeichnis, das HoloLensWinrtDLL.h enthält). Die DLL befindet sich in einem untergeordneten Verzeichnis des Includepfads, sodass diese Eigenschaft als binäres Stammverzeichnis verwendet wird:

```cs
using System.IO;

public class ConsumeWinRT : ModuleRules
{
    private string WinrtIncPath
    {
        get 
        {
            string ModulePath = Path.GetDirectoryName(
                   RulesCompiler.GetFileNameFromType(this.GetType()));

            // Third party directory is at the project root,
            // which is two directories up from the game .exe (Binaries/HoloLens)
            return Path.GetFullPath(
                   Path.Combine(ModulePath,
                   "../../ThirdParty/HoloLensWinrtDLL"));
        }
    }
}
```

2. Fügen Sie im Klassenkonstruktor den folgenden Code hinzu, um den Includepfad zu aktualisieren, die neue Bibliothek zu verknüpfen, die DLL zu verzögern und an den Speicherort der appx-Pakete zu kopieren:

```cs
public ConsumeWinRT(ReadOnlyTargetRules target) : base(Target)
{
    // This is the directory the DLL's include header is in.
    PublicIncludePaths.Add(WinrtIncPath);

    // The code in HoloLensWinrtDLL will only work in a Windows Store app.
    // Only link these binaries for HoloLens.
    // Similar code can be written for desktop and similarly linked 
    // to use the same features when using Holographic Remoting.
    if(Target.Platform == UnrealTargetPlatform.HoloLens)
    {
        // Link the lib
        PublicAdditionalLibraries.Add(Path.Combine(
              WinrtIncPath, "ARM64", "Release",
              "HoloLensWinrtDLL","HoloLensWinrtDLL.lib"));

        string winrtDLL = "HoloLensWinrtDLL.dll";
        // Mark the dll to be DelayLoaded
        PublicDelayLoadDLLs.Add(winrtDLL);
        // RuntimeDependencies are included in packaged builds.
        RuntimeDependencies.Add(Path.Combine(WinrtIncPath,
                "ARM64", "Release", "HoloLensWinrtDLL", winrtDLL));
    }

    // Preserve the original code in build.cs below:
}
```

3. Öffnen **Sie WinrtActor.h,** und fügen Sie eine Funktionsdefinition hinzu, die von einer Blaupause aufgerufen wird: 

```cpp
public:
    UFUNCTION(BlueprintCallable)
    static void OpenFileDialogue();
```

4. Öffnen **Sie WinrtActor.cpp,** und aktualisieren Sie BeginPlay, um die DLL zu laden: 

```cpp
void AWinrtActor::BeginPlay()
{
    Super::BeginPlay();

    // Gets path to DLL location
    const FString BinDir = FPaths::ProjectDir() / 
        "ThirdParty" / "HoloLensWinrtDLL" / 
        "arm64" / "Release" / "HoloLensWinrtDLL";

    // Loads DLL into application
    void * dllHandle = FPlatformProcess::GetDllHandle(
        *(BinDir / "HoloLensWinrtDLL.dll"));
}

void AWinrtActor::OpenFileDialogue()
{
#if PLATFORM_HOLOLENS
    HoloLensWinrtDLL::OpenFileDialogue();
#endif
}
``` 

>[!CAUTION]
> Die DLL muss geladen werden, bevor sie eine ihrer Funktionen aufruft.

### <a name="building-the-game"></a>Erstellen des Spiels
1. Erstellen Sie die Spiellösung, um den Unreal-Editor zu starten, der für das Spielprojekt geöffnet wurde: 
    * Suchen **Sie** auf der Registerkarte Place Actors nach dem neuen **WinrtActor,** und ziehen Sie ihn in die Szene. 
    * Öffnen Sie die Ebenen-Blaupause, um die aufrufbare Blaupausenfunktion im **WinrtActor** auszuführen. 

![Platzieren von WinrtActor in der Szene](../images/unreal-winrt-img-06.png)

2. Suchen Sie im **World Outliner** nach dem zuvor in der Szene abgelegten **WindrtActor,** und ziehen Sie ihn in die Ebenen-Blaupause: 

![Ziehen von WinrtActor in die Blaupause auf Ebene](../images/unreal-winrt-img-07.png)

3. Ziehen Sie in der Blaupause auf Ebene den Ausgabeknoten aus WinrtActor, suchen Sie nach **Open File Dialog (Dateidialog öffnen),** und leiten Sie den Knoten aus jeder Benutzereingabe weiter.  In diesem Fall wird das Dialogfeld "Datei öffnen" von einem Sprachereignis aufgerufen: 

![Konfigurieren von Knoten in der Ebenen-Blaupause](../images/unreal-winrt-img-08.png)

4. [Packen Sie dieses Spiel für HoloLens](../tutorials/unreal-uxt-ch6.md), stellen Sie es bereit, und führen Sie es aus.  

Wenn Unreal OpenFileDialogue aufruft, wird ein Dateidialog auf dem HoloLens geöffnet, der zur Eingabe eines .txt Dateinamens auffordert.  Nachdem die Datei gespeichert wurde, wechseln Sie im Geräteportal zur Registerkarte **Datei-Explorer,** um den Inhalt "Hello WinRT" anzuzeigen. 

## <a name="summary"></a>Zusammenfassung 

Wir empfehlen Ihnen, dieses Tutorial als Ausgangspunkt für die Verwendung von WinRT-Code in Unreal zu verwenden, wenn Sie Dateien auf dem HoloLens Datenträger mit demselben Dateidialog wie Windows speichern müssen.  Der gleiche Prozess gilt für das Exportieren zusätzlicher Funktionen aus dem HoloLensWinrtDLL-Header, die in Unreal verwendet werden.  Achten Sie besonders auf den DLL-Code, der auf asynchronen WinRT-Code in einem MTA-Hintergrundthread wartet, wodurch ein Deadlock des Unreal-Spielthreads vermieden wird.