---
title: Veröffentlichen im Microsoft Store
description: Erfahren Sie, wie Sie Ihre Unreal-Mixed Reality-Anwendungen für den Microsoft Store verpacken, zertifizieren und sie dort veröffentlichen können.
author: hferrone
ms.author: jacksonf
ms.date: 12/3/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, Dokumentation, Leitfäden, Features, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Veröffentlichen, Verteilung, Microsoft Store
ms.openlocfilehash: 41f081f11cdb9ac2fdf96a81bb761a1321d1776f
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010020"
---
# <a name="publishing-to-the-microsoft-store"></a><span data-ttu-id="70a8f-104">Veröffentlichen im Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="70a8f-104">Publishing to the Microsoft Store</span></span>

<span data-ttu-id="70a8f-105">Wenn Sie bereit sind, ihre Unreal-App zu veröffentlichen, müssen Sie ein paar Projekteinstellungen aktualisieren, bevor Sie sie an den Microsoft Store senden.</span><span class="sxs-lookup"><span data-stu-id="70a8f-105">When you're ready to get your Unreal app out to the world, there are a few project settings that need updating before you submit to the Microsoft Store.</span></span> <span data-ttu-id="70a8f-106">Alle diese Einstellungen verfügen über Standardwerte, sollten aber für die Produktion geändert werden, damit die Anwendung optimal dargestellt wird.</span><span class="sxs-lookup"><span data-stu-id="70a8f-106">All of these settings have default values, but should be changed for production to best represent the application.</span></span>

## <a name="project-settings-for-the-store-packaging"></a><span data-ttu-id="70a8f-107">Projekteinstellungen für die Store-Verpackung</span><span class="sxs-lookup"><span data-stu-id="70a8f-107">Project settings for the store packaging</span></span>

1. <span data-ttu-id="70a8f-108">Wählen Sie zunächst **Projekteinstellungen > Beschreibung** aus, und aktualisieren Sie die Spiel- und Herausgeberinformationen:</span><span class="sxs-lookup"><span data-stu-id="70a8f-108">First, select **Project Settings > Description** and update the game and publisher information:</span></span> 
    * <span data-ttu-id="70a8f-109">Der **Spielname** wird in der App-Kachel auf der HoloLens angezeigt.</span><span class="sxs-lookup"><span data-stu-id="70a8f-109">The **Game Name** will appear in the app tile on the HoloLens</span></span>
    * <span data-ttu-id="70a8f-110">Der **Distinguished Name des Unternehmens** wird beim Generieren des Projektzertifikats verwendet und sollte folgendes Format aufweisen:</span><span class="sxs-lookup"><span data-stu-id="70a8f-110">The **Company Distinguished Name** is used when generating the project certificate and should be in the format:</span></span> 
        * <span data-ttu-id="70a8f-111">**CN=CommonName, O=OrganizationName, L=LocalityName, S=StateOrProvinceName, C=CountryName**:</span><span class="sxs-lookup"><span data-stu-id="70a8f-111">**CN=CommonName, O=OrganizationName, L=LocalityName, S=StateOrProvinceName, C=CountryName**:</span></span>

![Screenshot des Unreal-Editors mit dem in den Projekteinstellungen erweiterten Abschnitt „Beschreibung“.](images/unreal-publishing-img-01.png)

2. <span data-ttu-id="70a8f-113">Erweitern Sie den Abschnitt **HoloLens** der Projekteinstellungen, und aktualisieren Sie die Verpackungsressourcen.</span><span class="sxs-lookup"><span data-stu-id="70a8f-113">Expand the **HoloLens** section of the project settings and update the packaging resources.</span></span>  <span data-ttu-id="70a8f-114">Diese Ressourcennamen werden auf der Store-Seite der Anwendung angezeigt:</span><span class="sxs-lookup"><span data-stu-id="70a8f-114">These resource names will be shown on the application’s store page:</span></span>

![Screenshot des Unreal-Editors mit dem in den Projekteinstellungen erweiterten Abschnitt „Verpacken“.](images/unreal-publishing-img-02.png)

3. <span data-ttu-id="70a8f-116">Erweitern Sie den Abschnitt **Bilder**, und aktualisieren Sie die standardmäßigen Store-Bilder mit Texturen, die die Store-App darstellen.</span><span class="sxs-lookup"><span data-stu-id="70a8f-116">Expand the **Images** section and update the default store images with textures that represent the store app.</span></span>  <span data-ttu-id="70a8f-117">Aktivieren Sie optional das Kontrollkästchen **3D-Logo**, um eine GLB-Datei hochzuladen, die beim Starten der Anwendung als 3D-Live Cube verwendet werden soll:</span><span class="sxs-lookup"><span data-stu-id="70a8f-117">Optionally, select the **3D Logo** checkbox to upload a glb file to use as a 3D live cube when launching the application:</span></span>

![Screenshot des Unreal-Editors mit dem in den Projekteinstellungen erweiterten Abschnitt „Bilder“.](images/unreal-publishing-img-03.png)

4. <span data-ttu-id="70a8f-119">Wählen Sie zuletzt **Neu generieren** aus, um ein Signaturzertifikat aus dem Projektnamen und dem Distinguished Name des Unternehmens zu generieren.</span><span class="sxs-lookup"><span data-stu-id="70a8f-119">Lastly, select **Generate New** to generate a signing certificate from the project name and company distinguished name</span></span>  
    * <span data-ttu-id="70a8f-120">Legen Sie eine **Kachel-Hintergrundfarbe** fest, die anstelle von transparenten Pixeln in den Store-Bildern angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="70a8f-120">Set a **Tile Background Color**, which will appear in place of any transparent pixels in the store images.</span></span>
    * <span data-ttu-id="70a8f-121">Erweitern Sie die Dropdownliste, und aktivieren Sie **Windows Store-Umgebung für den Einzelhandel verwenden**, damit die Ausführung auf im Einzelhandel gesperrten, nicht für Entwicklung entsperrten Geräten, erfolgen kann.</span><span class="sxs-lookup"><span data-stu-id="70a8f-121">Expand the dropdown and enable **Use Retail Windows Store Environment** to run on retail-locked, not dev-unlocked, devices.</span></span>

![Screenshot des Unreal-Editors mit dem in den Projekteinstellungen erweiterten Abschnitt „Zertifikatgenerierung“.](images/unreal-publishing-img-04.png)

## <a name="optional-app-installer"></a><span data-ttu-id="70a8f-123">Optionaler App-Installer</span><span class="sxs-lookup"><span data-stu-id="70a8f-123">Optional App Installer</span></span>

<span data-ttu-id="70a8f-124">Eine App-Installer-Datei kann aus **Projekteinstellungen > HoloLens** erstellt und dann zum Verteilen der Anwendung außerhalb des Stores verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="70a8f-124">An App Installer file can be created from **Project Settings > HoloLens**, which can be used to distribute the application outside of the store.</span></span>  <span data-ttu-id="70a8f-125">Aktivieren Sie das Kontrollkästchen **App-Installer erstellen**, und legen Sie eine URL oder einen Netzwerkpfad fest, wo Sie das appxbundle des Spiels speichern möchten.</span><span class="sxs-lookup"><span data-stu-id="70a8f-125">Enable the **Should Create App Installer** checkbox and set a URL or network path where you'd like the game’s appxbundle to be stored.</span></span>  

![Screenshot des Unreal-Editors mit dem in den Projekteinstellungen erweiterten Abschnitt „App-Installer“.](images/unreal-publishing-img-05.png)

<span data-ttu-id="70a8f-127">Wenn die App verpackt wird, werden sowohl „appxbundle“ als auch „appinstaller“ generiert.</span><span class="sxs-lookup"><span data-stu-id="70a8f-127">When the app is being packaged, both the appxbundle and appinstaller will be generated.</span></span>  <span data-ttu-id="70a8f-128">Laden Sie das appxbundle in die Installations-URL hoch, und starten Sie dann appinstaller, um die App von dem Netzwerkspeicherort aus zu installieren.</span><span class="sxs-lookup"><span data-stu-id="70a8f-128">Upload the appxbundle to the installation URL, then launch the appinstaller to install the app from the network location.</span></span>

## <a name="windows-app-certification-kit"></a><span data-ttu-id="70a8f-129">Zertifizierungskit für Windows-Apps</span><span class="sxs-lookup"><span data-stu-id="70a8f-129">Windows App Certification Kit</span></span>

<span data-ttu-id="70a8f-130">Der Lieferumfang des Windows 10 SDKs umfasst das Zertifizierungskit für Windows-Apps (WACK), um häufige Probleme zu überprüfen, die das Hochladen eines Pakets in den Store beeinträchtigen könnten.</span><span class="sxs-lookup"><span data-stu-id="70a8f-130">The Windows 10 SDK ships with the Windows App Certification Kit (WACK) to validate common issues that could affect uploading a package to the store.</span></span>  <span data-ttu-id="70a8f-131">Sie finden das WACK im Verzeichnis für Windows-Kits, in der Regel unter folgendem Pfad:</span><span class="sxs-lookup"><span data-stu-id="70a8f-131">You can find the WACK in the Windows Kits directory, usually under the following path:</span></span> 

```
C:\Program Files (x86)\Windows Kits\10\App Certification Kit.
```

1. <span data-ttu-id="70a8f-132">Nachdem Ihre appx-Datei für die Veröffentlichung gepackt wurde, führen Sie **appcertui.exe** aus, und befolgen Sie die Anweisungen zum Überprüfen der appx:</span><span class="sxs-lookup"><span data-stu-id="70a8f-132">After your appx file is packaged for publication, run **appcertui.exe** and follow the prompts to scan the appx:</span></span>

![Screenshot der App, die zur Validierung im Zertifizierungskit für Windows-Apps ausgewählt wird.](images/unreal-publishing-img-06.png)

2. <span data-ttu-id="70a8f-134">Wählen Sie **Store-App überprüfen** aus:</span><span class="sxs-lookup"><span data-stu-id="70a8f-134">Select **Validate Store App**:</span></span>

![Screenshot der Überprüfungsauswahl im Zertifizierungskit für Windows-Apps.](images/unreal-publishing-img-07.png)

3. <span data-ttu-id="70a8f-136">Suchen Sie im oberen Abschnitt nach der appx, und wählen Sie **Weiter** aus:</span><span class="sxs-lookup"><span data-stu-id="70a8f-136">Browse for the appx in the top section and select **Next**:</span></span>

![Screenshot der Testauswahl im Zertifizierungskit für Windows-Apps.](images/unreal-publishing-img-08.png)

4. <span data-ttu-id="70a8f-138">Wählen Sie **Weiter** aus, um die Tests auszuführen und einen Bericht zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="70a8f-138">Select **Next** to run the tests and create a report:</span></span>
    * <span data-ttu-id="70a8f-139">Alle verfügbaren Tests, die auf dem Host-PC ausgeführt werden können, sind standardmäßig aktiviert.</span><span class="sxs-lookup"><span data-stu-id="70a8f-139">All available tests that can be run on the host PC will be enabled by default</span></span>

![Screenshot des Überprüfungsstatus der App im Zertifizierungskit für Windows-Apps.](images/unreal-publishing-img-09.png)

5. <span data-ttu-id="70a8f-141">Warten Sie, bis die Tests abgeschlossen sind.</span><span class="sxs-lookup"><span data-stu-id="70a8f-141">Wait for the tests to finish.</span></span> <span data-ttu-id="70a8f-142">Sobald der Vorgang abgeschlossen ist, wird im letzten Fenster ein „Bestanden“- oder „Fehler“-Ergebnis angezeigt, das im gespeicherten Bericht überprüft werden kann.</span><span class="sxs-lookup"><span data-stu-id="70a8f-142">Once complete, the final window will show a pass or fail result, which can be viewed in the saved report.</span></span>

![Screenshot der Ergebnisse des Abschlussberichts im Zertifizierungskit für Windows-Apps.](images/unreal-publishing-img-10.png)

## <a name="known-wack-failure-with-425"></a><span data-ttu-id="70a8f-144">Bekannter WACK-Fehler bei Version 4.25</span><span class="sxs-lookup"><span data-stu-id="70a8f-144">Known WACK failure with 4.25</span></span>

<span data-ttu-id="70a8f-145">Das Windows Mixed Reality-Plug-In für Unreal 4.25 besteht das WACK nicht, weil einige x64-Binärdateien beim Verpacken für HoloLens eingeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="70a8f-145">The Windows Mixed Reality plugin in Unreal 4.25 will fail WACK because some x64 binaries are included while packaging for HoloLens.</span></span> <span data-ttu-id="70a8f-146">Der Fehler sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="70a8f-146">The failure will look like this:</span></span>

![Screenshot eines fehlgeschlagenen Ergebnisses wegen Binary Analyzer und unterstützter APIs aus dem Zertifizierungskit für Windows-Apps.](images/unreal-publishing-img-11.png)

<span data-ttu-id="70a8f-148">So beheben Sie das Problem:</span><span class="sxs-lookup"><span data-stu-id="70a8f-148">To fix the issue:</span></span>
1. <span data-ttu-id="70a8f-149">Navigieren Sie zum Stamm der Unreal-Installation oder des Quellverzeichnisses, indem Sie ein Unreal-Projekt öffnen und in der Taskleiste mit der rechten Maustaste auf das Unreal-Symbol klicken.</span><span class="sxs-lookup"><span data-stu-id="70a8f-149">Browse to the Unreal installation or source directory root by opening an Unreal project and right-click on the Unreal icon in the taskbar.</span></span>
2. <span data-ttu-id="70a8f-150">Klicken Sie mit der rechten Maustaste auf „UE4Editor“, wählen Sie „Eigenschaften“ aus, und navigieren Sie zum Pfad im Eintrag **Speicherort**:</span><span class="sxs-lookup"><span data-stu-id="70a8f-150">Right-click on UE4Editor, select properties, and browse to the path in the **Location** entry:</span></span>

```
Open Engine\Plugins\Runtime\WindowsMixedReality\Source\WindowsMixedRealityHMD\WindowsMixedRealityHMD.Build.cs.
```

3. <span data-ttu-id="70a8f-151">Ändern Sie in **WindowsMixedRealityHMD.Build.cs** **Zeile 32** von:</span><span class="sxs-lookup"><span data-stu-id="70a8f-151">In **WindowsMixedRealityHMD.Build.cs**, modify **line 32** from:</span></span>

```cpp
if(Target.Platform != UnrealTargetPlatform.Win32)
```

<span data-ttu-id="70a8f-152">in:</span><span class="sxs-lookup"><span data-stu-id="70a8f-152">to:</span></span>

```cpp
if(Target.Platform == UnrealTargetPlatform.Win64)

```

4. <span data-ttu-id="70a8f-153">Schließen Sie Unreal, öffnen Sie das Projekt erneut, und verpacken Sie es erneut für HoloLens.</span><span class="sxs-lookup"><span data-stu-id="70a8f-153">Close Unreal, reopen the project, and repackage for HoloLens.</span></span>  <span data-ttu-id="70a8f-154">Führen Sie WACK erneut aus, und der Fehler sollte nicht mehr angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="70a8f-154">Rerun WACK and the error will be gone.</span></span> 

## <a name="see-also"></a><span data-ttu-id="70a8f-155">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="70a8f-155">See also</span></span>

* [<span data-ttu-id="70a8f-156">Senden einer App an den Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="70a8f-156">Submitting an app to the Microsoft Store</span></span>](../../distribute/submitting-an-app-to-the-microsoft-store.md)
* [<span data-ttu-id="70a8f-157">Zertifizierungskit für Windows-Apps</span><span class="sxs-lookup"><span data-stu-id="70a8f-157">Windows App Certification Kit</span></span>](https://developer.microsoft.com/windows/downloads/app-certification-kit)
* [<span data-ttu-id="70a8f-158">Manuelles Erstellen einer App-Installer-Datei</span><span class="sxs-lookup"><span data-stu-id="70a8f-158">Create an App Installer file manually</span></span>](https://docs.microsoft.com/windows/msix/app-installer/how-to-create-appinstaller-file)