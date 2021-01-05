---
ms.openlocfilehash: 6bed33ee9b41a4ee66ce4c1c579d398f0958143d
ms.sourcegitcommit: db01faaf76bccd4f0432cf6b383fefa04ab7a085
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/23/2020
ms.locfileid: "97745714"
---
# <a name="426"></a>[<span data-ttu-id="2cc7a-101">4.26</span><span class="sxs-lookup"><span data-stu-id="2cc7a-101">4.26</span></span>](#tab/426)

## <a name="the-standard-winrt-apis"></a><span data-ttu-id="2cc7a-102">Die WinRT-Standard-APIs</span><span class="sxs-lookup"><span data-stu-id="2cc7a-102">The standard WinRT APIs</span></span>

<span data-ttu-id="2cc7a-103">Die gängigste und einfachste Methode, WinRT zu verwenden, ist das aufzurufen von Methoden aus winsdk.</span><span class="sxs-lookup"><span data-stu-id="2cc7a-103">The most common and easiest way to use WinRT is to call methods from WinSDK.</span></span> <span data-ttu-id="2cc7a-104">Öffnen Sie hierzu die Datei YourModule.Build.cs, und fügen Sie die folgenden Zeilen hinzu:</span><span class="sxs-lookup"><span data-stu-id="2cc7a-104">To do so, open YourModule.Build.cs file and add the following lines:</span></span>

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

<span data-ttu-id="2cc7a-105">Als nächstes müssen Sie die folgenden WinRT-Header hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="2cc7a-105">Next, you need to add the following WinRT headers:</span></span> 

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

<span data-ttu-id="2cc7a-106">WinRT-Code kann nur auf den Plattformen Win64 und hololens kompiliert werden, sodass die if-Anweisung verhindert, dass WinRT-Bibliotheken auf anderen Plattformen enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="2cc7a-106">WinRT code can only be compiled in the Win64 and HoloLens platforms, so the if statement prevents WinRT libraries from being included on other platforms.</span></span> <span data-ttu-id="2cc7a-107">"unknwn. h" wurde für die IUnknown-Schnittstelle hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="2cc7a-107">unknwn.h was added for having the IUnknown interface.</span></span> 


## <a name="winrt-from-a-nuget-package"></a><span data-ttu-id="2cc7a-108">WinRT von einem nuget-Paket</span><span class="sxs-lookup"><span data-stu-id="2cc7a-108">WinRT from a NuGet package</span></span>

<span data-ttu-id="2cc7a-109">Es ist etwas komplizierter, wenn Sie ein nuget-Paket mit WinRT-Unterstützung hinzufügen müssen.</span><span class="sxs-lookup"><span data-stu-id="2cc7a-109">It’s a little more complicated if you need to add a NuGet package with WinRT support.</span></span> <span data-ttu-id="2cc7a-110">In diesem Fall kann Visual Studio praktisch alle Aufgaben ausführen, aber das Unreal Build-System nicht.</span><span class="sxs-lookup"><span data-stu-id="2cc7a-110">In this case, Visual Studio can do practically all job for you, but the Unreal build system can’t.</span></span> <span data-ttu-id="2cc7a-111">Glücklicherweise ist es nicht zu schwierig.</span><span class="sxs-lookup"><span data-stu-id="2cc7a-111">Luckily, it’s not too difficult.</span></span> <span data-ttu-id="2cc7a-112">Im folgenden finden Sie ein Beispiel dafür, wie Sie das Paket Microsoft. mixedreality. QR herunterladen.</span><span class="sxs-lookup"><span data-stu-id="2cc7a-112">Below is an example of how you would go about downloading the Microsoft.MixedReality.QR package.</span></span> <span data-ttu-id="2cc7a-113">Sie können ihn durch einen anderen ersetzen. Stellen Sie lediglich sicher, dass die winmd-Datei nicht verloren geht, und kopieren Sie die korrekte dll.</span><span class="sxs-lookup"><span data-stu-id="2cc7a-113">You can replace it with another, just make sure you don’t lose the winmd file and copy the correct dll.</span></span> 

<span data-ttu-id="2cc7a-114">Windows SDK DLLs aus dem vorherigen Abschnitt werden vom Betriebssystem behandelt.</span><span class="sxs-lookup"><span data-stu-id="2cc7a-114">Windows SDK dlls from the previous section are handled by the OS.</span></span> <span data-ttu-id="2cc7a-115">Die nuget-DLLs müssen vom Code in Ihrem Modul verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="2cc7a-115">NuGet’s dlls must be managed by the code in your module.</span></span> <span data-ttu-id="2cc7a-116">Es wird empfohlen, Code hinzuzufügen, um sie herunterzuladen, in den Ordner Binärdateien zu kopieren und beim Modul Start in den Prozess Speicher zu laden.</span><span class="sxs-lookup"><span data-stu-id="2cc7a-116">We recommend adding code to download them, copying into binaries folder, and load into the process memory at the module startup.</span></span>

<span data-ttu-id="2cc7a-117">Im ersten Schritt sollten Sie eine packages.config ( https://docs.microsoft.com/nuget/reference/packages-config) in den Stamm Ordner des Moduls einfügen).</span><span class="sxs-lookup"><span data-stu-id="2cc7a-117">At the first step, you should add a packages.config (https://docs.microsoft.com/nuget/reference/packages-config) into the root folder of your module.</span></span> <span data-ttu-id="2cc7a-118">Dort sollten Sie alle Pakete hinzufügen, die Sie herunterladen möchten, einschließlich aller Abhängigkeiten.</span><span class="sxs-lookup"><span data-stu-id="2cc7a-118">There you should add all packages you want to download, including all their dependencies.</span></span> <span data-ttu-id="2cc7a-119">Hier habe ich Microsoft. mixedreality. QR als primäre Nutzlast und zwei weitere als Abhängigkeiten hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="2cc7a-119">Here I added Microsoft.MixedReality.QR as a primary payload and two others as dependencies to it.</span></span> <span data-ttu-id="2cc7a-120">Das Format dieser Datei ist identisch mit der in Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="2cc7a-120">The format of that file is same as in Visual Studio:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
  <package id="Microsoft.MixedReality.QR" version="0.5.2102" targetFramework="native" />
  <package id="Microsoft.VCRTForwarders.140" version="1.0.6" targetFramework="native" />
  <package id="Microsoft.Windows.CppWinRT" version="2.0.200729.8" targetFramework="native" />
</packages>
```

<span data-ttu-id="2cc7a-121">Nun können Sie nuget, die erforderlichen Pakete oder die nuget- [Dokumentation](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-nuget-cli)herunterladen.</span><span class="sxs-lookup"><span data-stu-id="2cc7a-121">Now you can download the NuGet, the required packages, or refer to the NuGet [documentation](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-nuget-cli).</span></span>

<span data-ttu-id="2cc7a-122">Öffnen Sie YourModule.Build.cs, und fügen Sie den folgenden Code hinzu:</span><span class="sxs-lookup"><span data-stu-id="2cc7a-122">Open YourModule.Build.cs and add the following code:</span></span>

```csharp
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
    string CppWinRTPackage = InstalledPackages.FirstOrDefault(x => x.StartsWith("Microsoft.Windows.CppWinRT"));
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
        // fall back to default WinSDK headers
        PrivateIncludePaths.Add(Path.Combine(Target.WindowsPlatform.WindowsSdkDir, "Include", Target.WindowsPlatform.WindowsSdkVersion, "cppwinrt"));
    }

    // WinRT lib for some job
    string QRPackage = InstalledPackages.FirstOrDefault(x => x.StartsWith("Microsoft.MixedReality.QR"));
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
```

<span data-ttu-id="2cc7a-123">Sie müssen die safecopy-Methode wie folgt definieren:</span><span class="sxs-lookup"><span data-stu-id="2cc7a-123">You'll need to define the SafeCopy method as follows:</span></span>

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

<span data-ttu-id="2cc7a-124">Nuget-DLLs müssen manuell in den Win32-Prozess Speicher geladen werden. Es wird empfohlen, ein manuelles Laden in die Start Methode Ihres Moduls einzufügen:</span><span class="sxs-lookup"><span data-stu-id="2cc7a-124">NuGet DLLs needs to load into your Win32 process memory manually; we recommend adding manual loading into the startup method of your module:</span></span>

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

<span data-ttu-id="2cc7a-125">Schließlich können Sie WinRT-Header in Ihren Code einschließen, wie im vorherigen Abschnitt beschrieben.</span><span class="sxs-lookup"><span data-stu-id="2cc7a-125">Finally, you can include WinRT headers into your code as described in the previous section.</span></span>

# <a name="425"></a>[<span data-ttu-id="2cc7a-126">4.25</span><span class="sxs-lookup"><span data-stu-id="2cc7a-126">4.25</span></span>](#tab/425)

<span data-ttu-id="2cc7a-127">Unreal kompiliert den WinRT-Code nicht in Version 4,25, daher ist es Ihre Aufgabe, eine separate Binärdatei zu erstellen, die das Buildsystem von Unreal verwenden kann.</span><span class="sxs-lookup"><span data-stu-id="2cc7a-127">Unreal doesn't natively compile WinRT code in version 4.25, so it's your job to build a separate binary that Unreal’s build system can consume.</span></span> 

## <a name="objectives"></a><span data-ttu-id="2cc7a-128">Ziele</span><span class="sxs-lookup"><span data-stu-id="2cc7a-128">Objectives</span></span>

- <span data-ttu-id="2cc7a-129">Erstellen einer universellen Windows-DLL, die ein filesavedialog öffnet</span><span class="sxs-lookup"><span data-stu-id="2cc7a-129">Create a Universal Windows DLL that opens a FileSaveDialogue</span></span>
- <span data-ttu-id="2cc7a-130">Diese DLL mit einem Unreal Game-Projekt verknüpfen</span><span class="sxs-lookup"><span data-stu-id="2cc7a-130">Link that DLL to an Unreal game project</span></span>
- <span data-ttu-id="2cc7a-131">Speichern einer Datei in den hololens von einem Unreal Blueprint mithilfe der neuen dll</span><span class="sxs-lookup"><span data-stu-id="2cc7a-131">Save a file on the HoloLens from an Unreal blueprint using the new DLL</span></span>

## <a name="getting-started"></a><span data-ttu-id="2cc7a-132">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="2cc7a-132">Getting started</span></span>

1. <span data-ttu-id="2cc7a-133">Überprüfen Sie, ob alle [erforderlichen Tools](../tutorials/unreal-uxt-ch1.md) installiert sind</span><span class="sxs-lookup"><span data-stu-id="2cc7a-133">Check that you have all [required tools](../tutorials/unreal-uxt-ch1.md) installed</span></span>
2. <span data-ttu-id="2cc7a-134">[Erstellen Sie ein neues Unreal-Projekt](../tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) , und nennen Sie es **consumewinrt** .</span><span class="sxs-lookup"><span data-stu-id="2cc7a-134">[Create a new Unreal project](../tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) and name it **Consumewinrt**</span></span>
3. <span data-ttu-id="2cc7a-135">Aktivieren der [erforderlichen](../tutorials/unreal-uxt-ch2.md#enabling-required-plugins) Plug-Ins für die hololens-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="2cc7a-135">Enable the [required plugins](../tutorials/unreal-uxt-ch2.md#enabling-required-plugins) for HoloLens development</span></span>
4. <span data-ttu-id="2cc7a-136">[Setup für die Bereitstellung](../tutorials/unreal-uxt-ch6.md) auf einem Gerät oder Emulator</span><span class="sxs-lookup"><span data-stu-id="2cc7a-136">[Setup for deployment](../tutorials/unreal-uxt-ch6.md) to a device or emulator</span></span>

## <a name="creating-a-winrt-dll"></a><span data-ttu-id="2cc7a-137">Erstellen einer WinRT-dll</span><span class="sxs-lookup"><span data-stu-id="2cc7a-137">Creating a WinRT DLL</span></span> 

1. <span data-ttu-id="2cc7a-138">Öffnen Sie ein neues Visual Studio-Projekt, und erstellen Sie ein DLL-Projekt **(Universal Windows)** im selben Verzeichnis wie die **uproject** -Datei des Unreal-Spiels.</span><span class="sxs-lookup"><span data-stu-id="2cc7a-138">Open a new Visual Studio project and create a **DLL (Universal Windows)** project in the same directory as the Unreal game’s **uproject** file.</span></span> 

![Erstellen einer dll](../images/unreal-winrt-img-01.png)

2. <span data-ttu-id="2cc7a-140">Nennen Sie das Projekt **hololenswinrtdll** , und legen Sie den Speicherort als Unterverzeichnis **thirdparty** auf die uproject-Datei des Unreal-Spiels fest.</span><span class="sxs-lookup"><span data-stu-id="2cc7a-140">Name the project **HoloLensWinrtDLL** and set the location as a **ThirdParty** subdirectory to the Unreal game’s uproject file.</span></span> 
    * <span data-ttu-id="2cc7a-141">Wählen Sie **Projekt Mappe und Projekt in demselben Verzeichnis platzieren** aus, um die Suche nach Pfaden später zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="2cc7a-141">Select **Place solution and project in the same directory** to simplify looking for paths later.</span></span> 

![Konfigurieren der dll](../images/unreal-winrt-img-02.png)

> [!IMPORTANT]
> <span data-ttu-id="2cc7a-143">Nachdem das neue Projekt kompiliert wurde, achten Sie besonders auf die leeren cpp-und Header Dateien ( **hololenswinrtdll. cpp** bzw. **hololenswinrtdll. h** ).</span><span class="sxs-lookup"><span data-stu-id="2cc7a-143">After the new project compiles, pay special attention to the blank cpp and header files, named **HoloLensWinrtDLL.cpp** and **HoloLensWinrtDLL.h** respectively.</span></span> <span data-ttu-id="2cc7a-144">Der-Header ist die Includedatei, die die dll in Unreal verwendet, während der cpp den Text der Funktionen enthält, die Sie exportieren, und einen WinRT-Code enthält, den Unreal nicht anderweitig kompilieren kann.</span><span class="sxs-lookup"><span data-stu-id="2cc7a-144">The header is the include file that uses the DLL in Unreal, while the cpp holds the body of any functions you export and includes any WinRT code that Unreal wouldn't otherwise be able to compile.</span></span> 

3. <span data-ttu-id="2cc7a-145">Bevor Sie Code hinzufügen, müssen Sie die Projekteigenschaften aktualisieren, um sicherzustellen, dass der benötigte WinRT-Code kompiliert werden kann:</span><span class="sxs-lookup"><span data-stu-id="2cc7a-145">Before you add any code, you need to update the project properties to ensure the WinRT code you need can compile:</span></span> 
    * <span data-ttu-id="2cc7a-146">Klicken Sie mit der rechten Maustaste auf das Projekt hololenswinrtdll, und wählen Sie **Eigenschaften** aus.</span><span class="sxs-lookup"><span data-stu-id="2cc7a-146">Right-click on the HoloLensWinrtDLL project and select **properties**</span></span>  
    * <span data-ttu-id="2cc7a-147">Ändern Sie die Dropdown Liste **Konfiguration** auf **alle Konfigurationen** und die Dropdown Liste für die **Plattform** auf **alle Plattformen** .</span><span class="sxs-lookup"><span data-stu-id="2cc7a-147">Change the **Configuration** dropdown to **All Configurations** and the **Platform** dropdown to **All Platforms**</span></span>  
    * <span data-ttu-id="2cc7a-148">Unter **Konfigurations Eigenschaften> C/C++> alle Optionen**:</span><span class="sxs-lookup"><span data-stu-id="2cc7a-148">Under **Configuration Properties> C/C++> All Options**:</span></span>
        * <span data-ttu-id="2cc7a-149">Fügen Sie **zusätzliche Optionen** hinzu **, um sicher** zustellen, dass wir auf asynchrone Tasks warten können.</span><span class="sxs-lookup"><span data-stu-id="2cc7a-149">Add **await** to **Additional Options** to ensure we can wait on async tasks</span></span>  
        * <span data-ttu-id="2cc7a-150">Ändern Sie den **C++-Sprachstandard** in **ISO C++ 17 Standard (/Std: C++ 17)** , um WinRT-Code einzubeziehen.</span><span class="sxs-lookup"><span data-stu-id="2cc7a-150">Change **C++ Language Standard** to **ISO C++17 Standard (/std:c++17)** to include any WinRT code</span></span>

![Aktualisieren von Projekteigenschaften](../images/unreal-winrt-img-03.png)

<span data-ttu-id="2cc7a-152">Das Projekt ist zum Aktualisieren der DLL-Quelle mit WinRT-Code bereit, mit dem ein Datei Dialogfeld geöffnet und eine Datei auf dem Datenträger für hololens gespeichert wird.</span><span class="sxs-lookup"><span data-stu-id="2cc7a-152">Your project is ready to update the DLL’s source with WinRT code that opens a file dialogue and saves a file to the HoloLens disk.</span></span>  

## <a name="adding-the-dll-code"></a><span data-ttu-id="2cc7a-153">Hinzufügen des dll-Codes</span><span class="sxs-lookup"><span data-stu-id="2cc7a-153">Adding the DLL code</span></span>

1. <span data-ttu-id="2cc7a-154">Öffnen Sie **hololenswinrtdll. h** , und fügen Sie eine exportierte DLL-Funktion hinzu, damit Unreal verwendet wird:</span><span class="sxs-lookup"><span data-stu-id="2cc7a-154">Open **HoloLensWinrtDLL.h** and add a dll exported function for Unreal to consume:</span></span> 

```cpp
#pragma once

class HoloLensWinrtDLL
{
public:
    _declspec(dllexport) static void OpenFileDialogue();
};
```

2. <span data-ttu-id="2cc7a-155">Öffnen Sie **hololenswinrtdll. cpp** , und fügen Sie alle Header hinzu, die von der-Klasse verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="2cc7a-155">Open **HoloLensWinrtDLL.cpp** and add all headers the class will use:</span></span>  

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
> <span data-ttu-id="2cc7a-156">Der gesamte WinRT-Code wird in **hololenswinrtdll. cpp** gespeichert, sodass Unreal nicht versucht, beim Verweis auf den Header einen WinRT-Code einzufügen.</span><span class="sxs-lookup"><span data-stu-id="2cc7a-156">All WinRT code is stored in **HoloLensWinrtDLL.cpp** so Unreal doesn't try to include any WinRT code when referencing the header.</span></span> 

3. <span data-ttu-id="2cc7a-157">Fügen Sie in **hololenswinrtdll. cpp** einen Funktions Text für OpenFileDialog () und den gesamten unterstützten Code hinzu:</span><span class="sxs-lookup"><span data-stu-id="2cc7a-157">Still in **HoloLensWinrtDLL.cpp**, add a function body for OpenFileDialogue() and all supported code:</span></span> 

```cpp
// sgm is declared outside of OpenFileDialogue so it doesn't
// get destroyed when OpenFileDialogue goes out of scope.
SaveGameManager sgm;

void HoloLensWinrtDLL::OpenFileDialogue()
{
    sgm.SaveGame();
}
```

4. <span data-ttu-id="2cc7a-158">Fügen Sie eine SavegameManager-Klasse zu **hololenswinrtdll. cpp** hinzu, um das Datei Dialogfeld zu verarbeiten und die Datei zu speichern:</span><span class="sxs-lookup"><span data-stu-id="2cc7a-158">Add a SaveGameManager class to **HoloLensWinrtDLL.cpp** to handle the file dialogue and saving the file:</span></span> 

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

5. <span data-ttu-id="2cc7a-159">Erstellen Sie die Projekt Mappe für **Release > ARM64** , um die DLL für das untergeordnete Verzeichnis ARM64/Release/hololenswinrtdll aus der DLL-Projekt Mappe zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="2cc7a-159">Build the solution for **Release > ARM64** to build the DLL to the child directory ARM64/Release/HoloLensWinrtDLL from the DLL solution.</span></span> 

## <a name="adding-the-winrt-binary-to-unreal"></a><span data-ttu-id="2cc7a-160">Hinzufügen der WinRT-Binärdatei zu Unreal</span><span class="sxs-lookup"><span data-stu-id="2cc7a-160">Adding the WinRT binary to Unreal</span></span> 
<span data-ttu-id="2cc7a-161">Das Verknüpfen und Verwenden einer DLL in Unreal erfordert ein C++-Projekt.</span><span class="sxs-lookup"><span data-stu-id="2cc7a-161">Linking and using a DLL in Unreal requires a C++ project.</span></span> <span data-ttu-id="2cc7a-162">Wenn Sie ein Blueprint-Projekt verwenden, kann es problemlos in ein C++-Projekt konvertiert werden, indem eine C++-Klasse hinzugefügt wird:</span><span class="sxs-lookup"><span data-stu-id="2cc7a-162">If you're using a Blueprint project, it can be easily converted to a C++ project by adding a C++ class:</span></span>  

1. <span data-ttu-id="2cc7a-163">Öffnen Sie im Unreal Editor **File > New C++ Class...**</span><span class="sxs-lookup"><span data-stu-id="2cc7a-163">In the Unreal editor, open **File > New C++ Class…**</span></span> <span data-ttu-id="2cc7a-164">und erstellen Sie einen neuen **Actor** namens **winrtactor** , um den Code in der DLL auszuführen:</span><span class="sxs-lookup"><span data-stu-id="2cc7a-164">and create a new **Actor** named **WinrtActor** to run the code in the DLL:</span></span> 

![Erstellen eines neuen Actors](../images/unreal-winrt-img-04.png)

> [!NOTE]
> <span data-ttu-id="2cc7a-166">Eine Projekt Mappe wurde nun im gleichen Verzeichnis wie die uproject-Datei erstellt, zusammen mit einem neuen Buildskript mit dem Namen "Source/consumewinrt/consumewinrt. Build. cs".</span><span class="sxs-lookup"><span data-stu-id="2cc7a-166">A solution has now been created in the same directory as the uproject file along with a new build script named Source/ConsumeWinRT/ConsumeWinRT.Build.cs.</span></span>

2. <span data-ttu-id="2cc7a-167">Öffnen Sie die Projekt Mappe, suchen Sie nach dem Ordner **Games/consumewinrt/Source/consumewinrt** , und öffnen Sie **ConsumeWinRT.Build.cs**:</span><span class="sxs-lookup"><span data-stu-id="2cc7a-167">Open the solution, browse for the **Games/ConsumeWinRT/Source/ConsumeWinRT** folder, and open **ConsumeWinRT.build.cs**:</span></span>

![Öffnen der ConsumeWinRT.Build.cs-Datei](../images/unreal-winrt-img-05.png)

### <a name="linking-the-dll"></a><span data-ttu-id="2cc7a-169">Verknüpfen der dll</span><span class="sxs-lookup"><span data-stu-id="2cc7a-169">Linking the DLL</span></span>
1. <span data-ttu-id="2cc7a-170">Fügen Sie in **ConsumeWinRT.Build.cs** eine Eigenschaft hinzu, um den Includepfad für die dll zu suchen (das Verzeichnis, das hololenswinrtdll. h enthält).</span><span class="sxs-lookup"><span data-stu-id="2cc7a-170">In **ConsumeWinRT.build.cs**, add a property to find the include path for the DLL (the directory containing HoloLensWinrtDLL.h).</span></span> <span data-ttu-id="2cc7a-171">Die dll befindet sich in einem untergeordneten Verzeichnis des include-Pfads, sodass diese Eigenschaft als binäres Stammverzeichnis verwendet wird:</span><span class="sxs-lookup"><span data-stu-id="2cc7a-171">The DLL is in a child directory to the include path, so this property will be used as the binary root dir:</span></span>

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

2. <span data-ttu-id="2cc7a-172">Fügen Sie im Klassenkonstruktor den folgenden Code hinzu, um den Includepfad zu aktualisieren, verknüpfen Sie die neue lib, und kopieren Sie die dll in den gepackten AppX-Speicherort:</span><span class="sxs-lookup"><span data-stu-id="2cc7a-172">In the class constructor, add the following code to update the include path, link the new lib, and delay-load and copy the DLL to the packaged appx location:</span></span>

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

3. <span data-ttu-id="2cc7a-173">Öffnen Sie **winrtactor. h** , und fügen Sie eine Funktionsdefinition hinzu, eine, die von einem Blueprint aufgerufen wird:</span><span class="sxs-lookup"><span data-stu-id="2cc7a-173">Open **WinrtActor.h** and add one function definition, one that a blueprint will call:</span></span> 

```cpp
public:
    UFUNCTION(BlueprintCallable)
    static void OpenFileDialogue();
```

4. <span data-ttu-id="2cc7a-174">Öffnen Sie **winrtactor. cpp** und Update beginplay, um die dll zu laden:</span><span class="sxs-lookup"><span data-stu-id="2cc7a-174">Open **WinrtActor.cpp** and update BeginPlay to load the DLL:</span></span> 

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
> <span data-ttu-id="2cc7a-175">Die dll muss geladen werden, bevor Sie Ihre Funktionen aufrufen können.</span><span class="sxs-lookup"><span data-stu-id="2cc7a-175">The DLL must be loaded before calling any of its functions.</span></span>

### <a name="building-the-game"></a><span data-ttu-id="2cc7a-176">Entwickeln des Spiels</span><span class="sxs-lookup"><span data-stu-id="2cc7a-176">Building the game</span></span>
1. <span data-ttu-id="2cc7a-177">Erstellen Sie die Spiel Projekt Mappe, um den Unreal Editor zu starten, der für das Spiel Projekt geöffnet wurde:</span><span class="sxs-lookup"><span data-stu-id="2cc7a-177">Build the game solution to launch the Unreal editor opened to the game project:</span></span> 
    * <span data-ttu-id="2cc7a-178">Suchen Sie auf der Registerkarte **platzieren der Actors** nach dem neuen **winrtactor** , und ziehen Sie ihn in die Szene.</span><span class="sxs-lookup"><span data-stu-id="2cc7a-178">In the **Place Actors** tab, search for the new **WinrtActor** and drag it into the scene</span></span> 
    * <span data-ttu-id="2cc7a-179">Öffnen Sie die Ebene Blueprint, um die Aufruf Bare Blueprint-Funktion im **winrtactor** auszuführen.</span><span class="sxs-lookup"><span data-stu-id="2cc7a-179">Open the level blueprint to execute the blueprint callable function in the **WinrtActor**</span></span> 

![Platzieren des winrtactors in der Szene](../images/unreal-winrt-img-06.png)

2. <span data-ttu-id="2cc7a-181">Suchen Sie im **World Outliner** den zuvor in der Szene gelöschten **windrtactor** , und ziehen Sie ihn in den Blueprint der Ebene:</span><span class="sxs-lookup"><span data-stu-id="2cc7a-181">In the **World Outliner**, find the **WindrtActor** previously dropped into the scene and drag it into the level blueprint:</span></span> 

![Ziehen von winrtactor in den Stufen Blueprint](../images/unreal-winrt-img-07.png)

3. <span data-ttu-id="2cc7a-183">Ziehen Sie in der Ebene Blueprint den Ausgabe Knoten von winrtactor, suchen Sie nach dem Dialogfeld " **Datei öffnen**", und leiten Sie den Knoten von jeder Benutzereingabe weiter.</span><span class="sxs-lookup"><span data-stu-id="2cc7a-183">In the level blueprint, drag the output node from WinrtActor, search for **Open File Dialogue**, then route the node from any user input.</span></span>  <span data-ttu-id="2cc7a-184">In diesem Fall wird das Dialogfeld "Datei öffnen" von einem sprach Ereignis aufgerufen:</span><span class="sxs-lookup"><span data-stu-id="2cc7a-184">In this case, Open File Dialogue is being called from a speech event:</span></span> 

![Konfigurieren von Knoten in der Ebene Blueprint](../images/unreal-winrt-img-08.png)

4. <span data-ttu-id="2cc7a-186">[Packen Sie dieses Spiel für hololens](../tutorials/unreal-uxt-ch6.md), stellen Sie es bereit, und führen Sie aus.</span><span class="sxs-lookup"><span data-stu-id="2cc7a-186">[Package this game for HoloLens](../tutorials/unreal-uxt-ch6.md), deploy it, and run.</span></span>  

<span data-ttu-id="2cc7a-187">Wenn Unreal "OpenFileDialog" aufruft, wird ein Datei Dialogfeld in den hololens geöffnet, in dem der Dateiname "</span><span class="sxs-lookup"><span data-stu-id="2cc7a-187">When Unreal calls OpenFileDialogue, a File Dialogue opens on the HoloLens prompting for a .txt file name.</span></span>  <span data-ttu-id="2cc7a-188">Nachdem die Datei gespeichert wurde, wechseln Sie im Geräte Portal zur Registerkarte " **Datei-Explorer** ", um den Inhalt "Hello WinRT" anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="2cc7a-188">After the file is saved, go to the **File explorer** tab in the device portal to see the contents “Hello WinRT”.</span></span> 

## <a name="summary"></a><span data-ttu-id="2cc7a-189">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="2cc7a-189">Summary</span></span> 

<span data-ttu-id="2cc7a-190">Wir empfehlen Ihnen, dieses Tutorial als Ausgangspunkt für die Verwendung von WinRT-Code in Unreal zu verwenden, wenn Sie Dateien mit dem gleichen Datei Dialogfeld wie Windows auf dem Datenträger "hololens" speichern müssen.</span><span class="sxs-lookup"><span data-stu-id="2cc7a-190">We encourage you to use this tutorial as a starting point for consuming WinRT code in Unreal when you need to save files to the HoloLens disk using the same file dialogue as Windows.</span></span>  <span data-ttu-id="2cc7a-191">Der gleiche Vorgang gilt für den Export zusätzlicher Funktionen aus dem hololenswinrtdll-Header und die Verwendung in Unreal.</span><span class="sxs-lookup"><span data-stu-id="2cc7a-191">The same process applies to exporting additional functions from the HoloLensWinrtDLL header and used in Unreal.</span></span>  <span data-ttu-id="2cc7a-192">Achten Sie besonders auf den DLL-Code, der auf Async-WinRT-Code in einem MTA-Hintergrund Thread wartet, der das Deadlocks des Unreal Game-Threads vermeidet.</span><span class="sxs-lookup"><span data-stu-id="2cc7a-192">Pay special attention to the DLL code that waits on async WinRT code in a background MTA thread, which avoids deadlocking the Unreal game thread.</span></span> 

