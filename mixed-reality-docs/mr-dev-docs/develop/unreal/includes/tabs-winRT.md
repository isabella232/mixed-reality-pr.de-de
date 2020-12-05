---
ms.openlocfilehash: be267da576e020e88f08d475395b144d42285383
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609405"
---
# <a name="425"></a>[4.25](#tab/425)

Unreal kompiliert den WinRT-Code nicht in Version 4,25, daher ist es Ihre Aufgabe, eine separate Binärdatei zu erstellen, die das Buildsystem von Unreal verwenden kann. 

## <a name="objectives"></a>Ziele

- Erstellen einer universellen Windows-DLL, die ein filesavedialog öffnet
- Diese DLL mit einem Unreal Game-Projekt verknüpfen
- Speichern einer Datei in den hololens von einem Unreal Blueprint mithilfe der neuen dll

## <a name="getting-started"></a>Erste Schritte

1. Überprüfen Sie, ob alle [erforderlichen Tools](../tutorials/unreal-uxt-ch1.md) installiert sind
2. [Erstellen Sie ein neues Unreal-Projekt](../tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) , und nennen Sie es **consumewinrt** .
3. Aktivieren der [erforderlichen](../tutorials/unreal-uxt-ch2.md#enabling-required-plugins) Plug-Ins für die hololens-Entwicklung
4. [Setup für die Bereitstellung](../tutorials/unreal-uxt-ch6.md) auf einem Gerät oder Emulator

## <a name="creating-a-winrt-dll"></a>Erstellen einer WinRT-dll 

1. Öffnen Sie ein neues Visual Studio-Projekt, und erstellen Sie ein DLL-Projekt **(Universal Windows)** im selben Verzeichnis wie die **uproject** -Datei des Unreal-Spiels. 

![Erstellen einer dll](../images/unreal-winrt-img-01.png)

2. Nennen Sie das Projekt **hololenswinrtdll** , und legen Sie den Speicherort als Unterverzeichnis **thirdparty** auf die uproject-Datei des Unreal-Spiels fest. 
    * Wählen Sie **Projekt Mappe und Projekt in demselben Verzeichnis platzieren** aus, um die Suche nach Pfaden später zu vereinfachen. 

![Konfigurieren der dll](../images/unreal-winrt-img-02.png)

> [!IMPORTANT]
> Nachdem das neue Projekt kompiliert wurde, achten Sie besonders auf die leeren cpp-und Header Dateien ( **hololenswinrtdll. cpp** bzw. **hololenswinrtdll. h** ). Der-Header ist die Includedatei, die die dll in Unreal verwendet, während der cpp den Text der Funktionen enthält, die Sie exportieren, und einen WinRT-Code enthält, den Unreal nicht anderweitig kompilieren kann. 

3. Bevor Sie Code hinzufügen, müssen Sie die Projekteigenschaften aktualisieren, um sicherzustellen, dass der benötigte WinRT-Code kompiliert werden kann: 
    * Klicken Sie mit der rechten Maustaste auf das Projekt hololenswinrtdll, und wählen Sie **Eigenschaften** aus.  
    * Ändern Sie die Dropdown Liste **Konfiguration** auf **alle Konfigurationen** und die Dropdown Liste für die **Plattform** auf **alle Plattformen** .  
    * Unter **Konfigurations Eigenschaften> C/C++> alle Optionen**:
        * Fügen Sie **zusätzliche Optionen** hinzu **, um sicher** zustellen, dass wir auf asynchrone Tasks warten können.  
        * Ändern Sie den **C++-Sprachstandard** in **ISO C++ 17 Standard (/Std: C++ 17)** , um WinRT-Code einzubeziehen.

![Aktualisieren von Projekteigenschaften](../images/unreal-winrt-img-03.png)

Das Projekt ist zum Aktualisieren der DLL-Quelle mit WinRT-Code bereit, mit dem ein Datei Dialogfeld geöffnet und eine Datei auf dem Datenträger für hololens gespeichert wird.  

## <a name="adding-the-dll-code"></a>Hinzufügen des dll-Codes

1. Öffnen Sie **hololenswinrtdll. h** , und fügen Sie eine exportierte DLL-Funktion hinzu, damit Unreal verwendet wird: 

```cpp
#pragma once

class HoloLensWinrtDLL
{
public:
    _declspec(dllexport) static void OpenFileDialogue();
};
```

2. Öffnen Sie **hololenswinrtdll. cpp** , und fügen Sie alle Header hinzu, die von der-Klasse verwendet werden:  

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
> Der gesamte WinRT-Code wird in **hololenswinrtdll. cpp** gespeichert, sodass Unreal nicht versucht, beim Verweis auf den Header einen WinRT-Code einzufügen. 

3. Fügen Sie in **hololenswinrtdll. cpp** einen Funktions Text für OpenFileDialog () und den gesamten unterstützten Code hinzu: 

```cpp
// sgm is declared outside of OpenFileDialogue so it doesn't
// get destroyed when OpenFileDialogue goes out of scope.
SaveGameManager sgm;

void HoloLensWinrtDLL::OpenFileDialogue()
{
    sgm.SaveGame();
}
```

4. Fügen Sie eine SavegameManager-Klasse zu **hololenswinrtdll. cpp** hinzu, um das Datei Dialogfeld zu verarbeiten und die Datei zu speichern: 

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

5. Erstellen Sie die Projekt Mappe für **Release > ARM64** , um die DLL für das untergeordnete Verzeichnis ARM64/Release/hololenswinrtdll aus der DLL-Projekt Mappe zu erstellen. 

## <a name="adding-the-winrt-binary-to-unreal"></a>Hinzufügen der WinRT-Binärdatei zu Unreal 
Das Verknüpfen und Verwenden einer DLL in Unreal erfordert ein C++-Projekt. Wenn Sie ein Blueprint-Projekt verwenden, kann es problemlos in ein C++-Projekt konvertiert werden, indem eine C++-Klasse hinzugefügt wird:  

1. Öffnen Sie im Unreal Editor **File > New C++ Class...** und erstellen Sie einen neuen **Actor** namens **winrtactor** , um den Code in der DLL auszuführen: 

![Erstellen eines neuen Actors](../images/unreal-winrt-img-04.png)

> [!NOTE]
> Eine Projekt Mappe wurde nun im gleichen Verzeichnis wie die uproject-Datei erstellt, zusammen mit einem neuen Buildskript mit dem Namen "Source/consumewinrt/consumewinrt. Build. cs".

2. Öffnen Sie die Projekt Mappe, suchen Sie nach dem Ordner **Games/consumewinrt/Source/consumewinrt** , und öffnen Sie **ConsumeWinRT.Build.cs**:

![Öffnen der ConsumeWinRT.Build.cs-Datei](../images/unreal-winrt-img-05.png)

### <a name="linking-the-dll"></a>Verknüpfen der dll
1. Fügen Sie in **ConsumeWinRT.Build.cs** eine Eigenschaft hinzu, um den Includepfad für die dll zu suchen (das Verzeichnis, das hololenswinrtdll. h enthält). Die dll befindet sich in einem untergeordneten Verzeichnis des include-Pfads, sodass diese Eigenschaft als binäres Stammverzeichnis verwendet wird:

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

2. Fügen Sie im Klassenkonstruktor den folgenden Code hinzu, um den Includepfad zu aktualisieren, verknüpfen Sie die neue lib, und kopieren Sie die dll in den gepackten AppX-Speicherort:

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

3. Öffnen Sie **winrtactor. h** , und fügen Sie eine Funktionsdefinition hinzu, eine, die von einem Blueprint aufgerufen wird: 

```cpp
public:
    UFUNCTION(BlueprintCallable)
    static void OpenFileDialogue();
```

4. Öffnen Sie **winrtactor. cpp** und Update beginplay, um die dll zu laden: 

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
> Die dll muss geladen werden, bevor Sie Ihre Funktionen aufrufen können.

### <a name="building-the-game"></a>Entwickeln des Spiels
1. Erstellen Sie die Spiel Projekt Mappe, um den Unreal Editor zu starten, der für das Spiel Projekt geöffnet wurde: 
    * Suchen Sie auf der Registerkarte **platzieren der Actors** nach dem neuen **winrtactor** , und ziehen Sie ihn in die Szene. 
    * Öffnen Sie die Ebene Blueprint, um die Aufruf Bare Blueprint-Funktion im **winrtactor** auszuführen. 

![Platzieren des winrtactors in der Szene](../images/unreal-winrt-img-06.png)

2. Suchen Sie im **World Outliner** den zuvor in der Szene gelöschten **windrtactor** , und ziehen Sie ihn in den Blueprint der Ebene: 

![Ziehen von winrtactor in den Stufen Blueprint](../images/unreal-winrt-img-07.png)

3. Ziehen Sie in der Ebene Blueprint den Ausgabe Knoten von winrtactor, suchen Sie nach dem Dialogfeld " **Datei öffnen**", und leiten Sie den Knoten von jeder Benutzereingabe weiter.  In diesem Fall wird das Dialogfeld "Datei öffnen" von einem sprach Ereignis aufgerufen: 

![Konfigurieren von Knoten in der Ebene Blueprint](../images/unreal-winrt-img-08.png)

4. [Packen Sie dieses Spiel für hololens](../tutorials/unreal-uxt-ch6.md), stellen Sie es bereit, und führen Sie aus.  

Wenn Unreal "OpenFileDialog" aufruft, wird ein Datei Dialogfeld in den hololens geöffnet, in dem der Dateiname "  Nachdem die Datei gespeichert wurde, wechseln Sie im Geräte Portal zur Registerkarte " **Datei-Explorer** ", um den Inhalt "Hello WinRT" anzuzeigen. 

## <a name="summary"></a>Zusammenfassung 

Wir empfehlen Ihnen, dieses Tutorial als Ausgangspunkt für die Verwendung von WinRT-Code in Unreal zu verwenden, wenn Sie Dateien mit dem gleichen Datei Dialogfeld wie Windows auf dem Datenträger "hololens" speichern müssen.  Der gleiche Vorgang gilt für den Export zusätzlicher Funktionen aus dem hololenswinrtdll-Header und die Verwendung in Unreal.  Achten Sie besonders auf den DLL-Code, der auf Async-WinRT-Code in einem MTA-Hintergrund Thread wartet, der das Deadlocks des Unreal Game-Threads vermeidet. 

# <a name="426"></a>[4.26](#tab/426)

## <a name="the-standard-winrt-apis"></a>Die WinRT-Standard-APIs

Die gängigste und einfachste Methode, WinRT zu verwenden, ist das aufzurufen von Methoden aus winsdk. Öffnen Sie hierzu die Datei YourModule.Build.cs, und fügen Sie die folgenden Zeilen hinzu:

```cpp
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

Als nächstes müssen Sie die folgenden WinRT-Header hinzufügen: 

```cpp
#if (PLATFORM_WINDOWS || PLATFORM_HOLOLENS) 
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

WinRT-Code kann nur auf den Plattformen Win64 und hololens kompiliert werden, sodass die if-Anweisung verhindert, dass WinRT-Bibliotheken auf anderen Plattformen enthalten sind. "unknwn. h" wurde für die IUnknown-Schnittstelle hinzugefügt. 

Vor dem Schreiben von Code müssen Sie häufige Warnungen in WinRT-Headern mithilfe von deaktivieren:

```cpp
#pragma warning(disable : 5205 4265)
```

## <a name="winrt-from-a-nuget-package"></a>WinRT von einem nuget-Paket

Es ist etwas komplizierter, wenn Sie ein nuget-Paket mit WinRT-Unterstützung hinzufügen müssen. In diesem Fall kann Visual Studio praktisch alle Aufgaben ausführen, aber das Unreal Build-System nicht. Glücklicherweise ist es nicht zu schwierig. Im folgenden finden Sie ein Beispiel dafür, wie Sie das Paket Microsoft. mixedreality. QR herunterladen. Sie können ihn durch einen anderen ersetzen. Stellen Sie lediglich sicher, dass die winmd-Datei nicht verloren geht, und kopieren Sie die korrekte dll. 

Windows SDK DLLs aus dem vorherigen Abschnitt werden vom Betriebssystem behandelt. Die nuget-DLLs müssen vom Code in Ihrem Modul verwaltet werden. Es wird empfohlen, Code hinzuzufügen, um sie herunterzuladen, in den Ordner Binärdateien zu kopieren und beim Modul Start in den Prozess Speicher zu laden.

Im ersten Schritt sollten Sie eine packages.config ( https://docs.microsoft.com/nuget/reference/packages-config) in den Stamm Ordner des Moduls einfügen). Dort sollten Sie alle Pakete hinzufügen, die Sie herunterladen möchten, einschließlich aller Abhängigkeiten. Hier habe ich Microsoft. mixedreality. QR als primäre Nutzlast und zwei weitere als Abhängigkeiten hinzugefügt. Das Format dieser Datei ist identisch mit der in Visual Studio:

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
  <package id="Microsoft.MixedReality.QR" version="0.5.2102" targetFramework="native" />
  <package id="Microsoft.VCRTForwarders.140" version="1.0.6" targetFramework="native" />
  <package id="Microsoft.Windows.CppWinRT" version="2.0.200729.8" targetFramework="native" />
</packages>
```

Nun können Sie nuget, die erforderlichen Pakete oder die nuget- [Dokumentation](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-nuget-cli)herunterladen.

Öffnen Sie YourModule.Build.cs, und fügen Sie den folgenden Code hinzu:

```cpp
if(Target.Platform == UnrealTargetPlatform.Win64 || Target.Platform == UnrealTargetPlatform.HoloLens)
{
    string MyModuleName = GetType().Name;

    // these parameters mandatory for winrt support
    bEnableExceptions = true;
    bUseUnity = false;
    CppStandard = CppStandardVersion.Cpp17;
    PublicSystemLibraries.Add("shlwapi.lib");
    PublicSystemLibraries.Add("runtimeobject.lib");

    // prepare everything for nuget
    string NugetFolder = Path.Combine(PluginDirectory, "Intermediate", "Nuget", MyModuleName);
    Directory.CreateDirectory(NugetFolder);

    string BinariesSubFolder = Path.Combine("Binaries", "ThirdParty", Target.Type.ToString(), Target.Platform.ToString(), Target.Architecture);

            PrivateDefinitions.Add(string.Format("THIRDPARTY_BINARY_SUBFOLDER=\"{0}\"", BinariesSubFolder.Replace(@"\", @"\\")));

    string BinariesFolder = Path.Combine(PluginDirectory, BinariesSubFolder);
    Directory.CreateDirectory(BinariesFolder);

    // download nuget
    string NugetExe = Path.Combine(NugetFolder, "nuget.exe");
    if(!File.Exists(NugetExe))
    {
        using (System.Net.WebClient myWebClient = new System.Net.WebClient())
        {
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
            
    // get list of the installed packages
    string[] InstalledPackages = Utils.RunLocalProcessAndReturnStdOut(NugetExe, string.Format("list -Source \"{0}\"", NugetFolder)).Split(new char[] {'\r', '\n' });

    // get WinRT package 
    string CppWinRTPackage = InstalledPackages.First(x => x.StartsWith("Microsoft.Windows.CppWinRT"));
    if(!string.IsNullOrEmpty(CppWinRTPackage))
    {
        string CppWinRTName = CppWinRTPackage.Replace(" ", ".");
        string CppWinRTExe = Path.Combine(NugetFolder, CppWinRTName, "bin", "cppwinrt.exe");
        string CppWinRTFolder = Path.Combine(PluginDirectory, "Intermediate", CppWinRTName, MyModuleName);
        Directory.CreateDirectory(CppWinRTFolder);

        // search all downloaded packages for winmd files
        string[] WinMDFiles = Directory.GetFiles(NugetFolder, "*.winmd", SearchOption.AllDirectories);

        // all downloaded winmd file with WinSDK to be processed by cppwinrt.exe
        var WinMDFilesStringbuilder = new System.Text.StringBuilder();
        foreach(var winmd in WinMDFiles)
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
        // fall to default WinSDK headers
                        PrivateIncludePaths.Add(Path.Combine(Target.WindowsPlatform.WindowsSdkDir, "Include", Target.WindowsPlatform.WindowsSdkVersion, "cppwinrt"));
            }

    // WinRT lib for some job
    string QRPackage = InstalledPackages.First(x => x.StartsWith("Microsoft.MixedReality.QR"));
    if (!string.IsNullOrEmpty(QRPackage))
    {
        string QRFolderName = QRPackage.Replace(" ", ".");

        // copying dll and winmd binaries to our local binaries folder
        // !!!!! please make sure that you use the path of file! Unreal can't do it for you !!!!!
        SafeCopy(Path.Combine(NugetFolder, QRFolderName, @"lib\uap10.0.18362\Microsoft.MixedReality.QR.winmd"), 
        Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.winmd"));

        SafeCopy(Path.Combine(NugetFolder, QRFolderName, string.Format(@"runtimes\win10-{0}\native\Microsoft.MixedReality.QR.dll", Target.WindowsPlatform.Architecture.ToString())), 
        Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.dll"));

        // also both both binaries must be in RuntimeDependencies, unless you get failures in Hololens platform
        RuntimeDependencies.Add(Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.dll"));
        RuntimeDependencies.Add(Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.winmd"));
    }

    if(Target.Platform == UnrealTargetPlatform.Win64)
    {
        // Microsoft.VCRTForwarders.140 is needed to run WinRT dlls in Win64 platforms
        string VCRTForwardersPackage = InstalledPackages.First(x => x.StartsWith("Microsoft.VCRTForwarders.140"));
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
```

Sie müssen die safecopy-Methode wie folgt definieren:

```cpp
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

Nuget-DLLs müssen manuell in den Win32-Prozess Speicher geladen werden. Es wird empfohlen, ein manuelles Laden in die Start Methode Ihres Moduls einzufügen:

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

Schließlich können Sie WinRT-Header in Ihren Code einschließen, wie im vorherigen Abschnitt beschrieben.