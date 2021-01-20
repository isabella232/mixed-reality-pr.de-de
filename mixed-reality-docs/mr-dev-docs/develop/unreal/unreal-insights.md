---
title: Profilerstellung mit Unreal Insights
description: Erfahren Sie, wie Sie Unreal Insights auf hololens 2 verwenden.
author: sajidfarooq
ms.author: v-hferrone
ms.date: 12/10/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, hololens, hololens 2, Development, profling, Unreal Insights, Dokumentation, Guides, Features, holograms, Spieleentwicklung, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: b41d36679adfb35b5cc3561b8d5e7734654e7fb5
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580838"
---
# <a name="profiling-with-unreal-insights"></a><span data-ttu-id="898b0-104">Profilerstellung mit Unreal Insights</span><span class="sxs-lookup"><span data-stu-id="898b0-104">Profiling with Unreal Insights</span></span> 

<span data-ttu-id="898b0-105">[Unreal Insights](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html) ist ein Profil Erstellungs System, das Daten von Unreal Engine sammelt, analysiert und visualisiert.</span><span class="sxs-lookup"><span data-stu-id="898b0-105">[Unreal Insights](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html) is a profiling system that collects, analyzes, and visualizes data from Unreal Engine.</span></span> <span data-ttu-id="898b0-106">Das Profil Erstellungs System kann Sie bei der Suche nach Optimierungs Engpässen und Bereichen unterstützen, in denen die Leistung von apps eine Erhöhung der Anwendungen</span><span class="sxs-lookup"><span data-stu-id="898b0-106">The profiling system can help you find optimization bottlenecks and areas where you apps performance could use a boost.</span></span> <span data-ttu-id="898b0-107">Normalerweise aktivieren Sie Unreal Insights direkt aus dem Editor, aber für hololens 2 müssen Sie die Befehlszeile verwenden.</span><span class="sxs-lookup"><span data-stu-id="898b0-107">Normally, you enable Unreal Insights right from the editor, but for HoloLens 2 you'll need to use the command line.</span></span>  

## <a name="setup"></a><span data-ttu-id="898b0-108">Einrichten</span><span class="sxs-lookup"><span data-stu-id="898b0-108">Setup</span></span>

<span data-ttu-id="898b0-109">Unreal ermöglicht es Ihnen, ein "benutzerdefiniertes Profil" im hololens-Start Programm mit den Befehlszeilen Parametern zu erstellen und zu konfigurieren, die Unreal Insights ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="898b0-109">Unreal lets you to create and configure a "Custom Profile" in the HoloLens launcher with the command line parameters that enable Unreal Insights.</span></span>

1.  <span data-ttu-id="898b0-110">Suchen Sie die IP-Adresse Ihres Computers mithilfe des Befehls " **ipconfig** " an der Eingabeaufforderung.</span><span class="sxs-lookup"><span data-stu-id="898b0-110">Find the IP address of your computer using the **ipconfig** command on the command prompt.</span></span> <span data-ttu-id="898b0-111">Die IP-Adresse ist die von ipconfig aufgelistete IPv4-Adresse.</span><span class="sxs-lookup"><span data-stu-id="898b0-111">The IP address is the IPv4 address listed by ipconfig.</span></span> <span data-ttu-id="898b0-112">Beachten Sie dies für den späteren Zeitpunkt, wenn Sie Befehlszeilenparameter festlegen.</span><span class="sxs-lookup"><span data-stu-id="898b0-112">Keep this in mind for later when you set Command Line Parameters.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="898b0-113">Wenn Sie sich hinter einem VPN befinden, müssen Sie möglicherweise die IP-Adresse angeben, die über das VPN bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="898b0-113">If you're behind a VPN, you may need to provide the IP address provided via the VPN instead.</span></span>

![Screenshot der Befehlszeilen Ergebnisse für den Befehl "ipconfig"](images/unreal-insights-img-01.png)

2.  <span data-ttu-id="898b0-115">Wechseln Sie zum oberen Rand des Unreal Engine-Panels, und öffnen Sie **Geräte-Manager** unter der Schaltfläche " **starten** ":</span><span class="sxs-lookup"><span data-stu-id="898b0-115">Go to the top of the Unreal Engine panel and open **Device Manager** under the **Launch** button:</span></span>

![Screenshot der Startoptionen mit hervorgehobenem Geräte-Manager](images/unreal-insights-img-02.png)

3.  <span data-ttu-id="898b0-117">Wählen Sie im Geräte-Manager die **Option nicht aufgelistetes Gerät hinzufügen** aus:</span><span class="sxs-lookup"><span data-stu-id="898b0-117">In the Device Manager, select **Add an Unlisted Device**:</span></span>

![Screenshot des geöffneten Geräte-Managers in der Unreal-Engine](images/unreal-insights-img-03.png)

4. <span data-ttu-id="898b0-119">Klicken Sie auf **Plattform auswählen** , und wählen Sie **hololens** aus:</span><span class="sxs-lookup"><span data-stu-id="898b0-119">Click **Select a platform** and choose **HoloLens**:</span></span>

![Screenshot der Dropdown Liste "nicht aufgelisteten Gerät hinzufügen" mit hervorgehobenem hololens](images/unreal-insights-img-04.png)

5.  <span data-ttu-id="898b0-121">Wenn Sie ipoverusb verwenden, geben Sie 127.0.0.1:10080 als Geräte Bezeichner ein.</span><span class="sxs-lookup"><span data-stu-id="898b0-121">If you're using IPoverUSB, enter 127.0.0.1:10080 as the Device Identifier.</span></span> <span data-ttu-id="898b0-122">Geben Sie Ihren hololens-Benutzer und das Kennwort in die entsprechenden Felder ein, und füllen Sie den **anzeigen Amen** wie gewünscht aus.</span><span class="sxs-lookup"><span data-stu-id="898b0-122">Enter your HoloLens user and password in their respective fields and fill **Display Name** as you wish.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="898b0-123">Der Geräte Bezeichner ist die IP-Adresse der hololens und nicht der Computer, auf dem Unreal Insights ausgeführt wird, den Sie in Schritt 1 gefunden haben.</span><span class="sxs-lookup"><span data-stu-id="898b0-123">The Device Identifier is the IP address of the HoloLens, NOT of the computer running Unreal Insights you found in step 1.</span></span>

![Screenshot der Geräte Details des hololens in Device Manager](images/unreal-insights-img-05.png)

6.  <span data-ttu-id="898b0-125">Wählen Sie **Hinzufügen** aus, und ihre hololens sollte in der Geräteliste des Geräte-Managers angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="898b0-125">Select **Add** and your HoloLens should appear in the device list of the device manager:</span></span>

![Screenshot der der Geräteliste hinzugefügten hololens](images/unreal-insights-img-06.png)

## <a name="launch"></a><span data-ttu-id="898b0-127">Starten</span><span class="sxs-lookup"><span data-stu-id="898b0-127">Launch</span></span>

1. <span data-ttu-id="898b0-128">Öffnen Sie das **Projekt** **Startfeld** über den Bereich UE4 unter der Schaltfläche starten:</span><span class="sxs-lookup"><span data-stu-id="898b0-128">Open **Project Launcher** from the UE4 panel under the **Launch** button:</span></span>

![Screenshot der Startoptionen mit hervorgehobenem Projekt Starter](images/unreal-insights-img-07.png)

2. <span data-ttu-id="898b0-130">Wählen Sie die **+** Schaltfläche zum Erstellen eines benutzerdefinierten Profils unter **benutzerdefinierte Start profile** aus.</span><span class="sxs-lookup"><span data-stu-id="898b0-130">Select the **+** button to create a custom profile under **Custom Launch Profiles**.</span></span> <span data-ttu-id="898b0-131">Nach der Erstellung können Sie dieses Profil später jederzeit bearbeiten:</span><span class="sxs-lookup"><span data-stu-id="898b0-131">Once created, you can always edit this profile later:</span></span>

![Screenshot: Projektstart Programm mit hervorgehobenem benutzerdefinierten Start Profilen](images/unreal-insights-img-08.png)

3. <span data-ttu-id="898b0-133">Wählen Sie im benutzerdefinierten Start Profil hololens die Schaltfläche **Profil bearbeiten** aus, und konfigurieren Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="898b0-133">Select **edit profile** button on the HoloLens custom launch profile and configure:</span></span>
    * <span data-ttu-id="898b0-134">Wählen Sie für **das Buch die** Option **Kochen** aus, um das Kopieren auf das Gerät</span><span class="sxs-lookup"><span data-stu-id="898b0-134">Select **Cook** to **By the Book** to enable copying to device</span></span>
    * <span data-ttu-id="898b0-135">Sie sollten die Option "möchten **Sie archivieren?** " im Abschnitt " **Archive** " aktivieren, um die generierte. appxbundle-Datei beizubehalten, anstatt Sie zu löschen, um Speicherplatz zu sparen.</span><span class="sxs-lookup"><span data-stu-id="898b0-135">You may want to check **Do you wish to archive?** in the **Archive** section to retain the generated .appxbundle rather than deleting to save disk space.</span></span> <span data-ttu-id="898b0-136">Geben Sie einen Speicherort für die appxbundle-Datei an, und wechseln Sie bei Bedarf zu einem entwicklungbuild.</span><span class="sxs-lookup"><span data-stu-id="898b0-136">Specify a location for the .appxbundle and switch to a development build if you wish</span></span>

![Screenshot der Koch Optionen in der Profil Konfiguration mit dem Buch "Cook" und "hololens" hervorgehoben](images/unreal-insights-img-09.png)

4. <span data-ttu-id="898b0-138">Legen **Sie fest, wie soll der Build** bereitgestellt werden soll? auf das **Gerät zu kopieren** , um den **Startbereich** der Benutzeroberfläche zu aktivieren:</span><span class="sxs-lookup"><span data-stu-id="898b0-138">Set **How would you like to deploy the build?** to **Copy to device** to activate the **Launch** section of the UI:</span></span>

![Screenshot des Projektstart Programms mit den Bereitstellungs Optionen mit hervorgehobener Kopie auf Gerät](images/unreal-insights-img-10.png)

5. <span data-ttu-id="898b0-140">Legen Sie **Zusätzliche Befehlszeilenparameter** im **Startbereich** fest.</span><span class="sxs-lookup"><span data-stu-id="898b0-140">Set **Additional Command Line Parameters** in the **Launch** section.</span></span> <span data-ttu-id="898b0-141">Die Parameter werden in eine ue4commandline.txt Datei geschrieben, in das Bündel gepackt und beim Start verwendet.</span><span class="sxs-lookup"><span data-stu-id="898b0-141">The parameters will be written into a ue4commandline.txt file, packaged into the bundle, and used at launch.</span></span> 
    <!-- TODO: Need more detail on what this parameter does and where to find others. -->
    * <span data-ttu-id="898b0-142">Probieren Sie die folgenden Schritte aus: **-tracehost = IP_OF_YOUR_PC-Trace = Log, Bookmark, Frame, CPU, GPU, loadtime, File, NET**</span><span class="sxs-lookup"><span data-stu-id="898b0-142">Try these for starters: **-tracehost=IP_OF_YOUR_PC -trace=Log,Bookmark,Frame,CPU,GPU,LoadTime,File,Net**</span></span>
    * <span data-ttu-id="898b0-143">Eine komplette Liste der verfügbaren Startparameter finden Sie in der [Unreal Insights-Referenz Dokumentation](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html).</span><span class="sxs-lookup"><span data-stu-id="898b0-143">You can find a complete list of available launch parameters in the [Unreal Insights reference documentation](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html).</span></span>

> [!NOTE]
> <span data-ttu-id="898b0-144">"IP_OF_YOUR_PC" ist die IP-Adresse, die in Schritt 1 gefunden wurde.</span><span class="sxs-lookup"><span data-stu-id="898b0-144">"IP_OF_YOUR_PC" is the IP address we found in step 1.</span></span> <span data-ttu-id="898b0-145">Dabei handelt es sich um die IP-Adresse des Computers, auf dem Unreal Insights ausgeführt wird, nicht um die IP-Adresse der hololens.</span><span class="sxs-lookup"><span data-stu-id="898b0-145">This is the IP address of the computer running Unreal Insights, NOT the IP address of the HoloLens.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="898b0-146">Ablauf Verfolgungen können sehr schnell groß werden.</span><span class="sxs-lookup"><span data-stu-id="898b0-146">Traces can get large very quickly.</span></span> <span data-ttu-id="898b0-147">Aktivieren Sie nur die Kanäle, die Sie benötigen, um die Ablauf Verfolgungs Größe zu beschränken.</span><span class="sxs-lookup"><span data-stu-id="898b0-147">Enable only those channels you need to keep trace size low.</span></span>

![Screenshot der Start Konfigurationsoptionen](images/unreal-insights-img-11.png)

6. <span data-ttu-id="898b0-149">Starten Sie vor dem Starten der APP Unreal Insights, sonst ist Unreal Insights nicht in der Lage, vor der APP ordnungsgemäß zu initialisieren:</span><span class="sxs-lookup"><span data-stu-id="898b0-149">Launch Unreal Insights BEFORE app launch, otherwise Unreal Insights wont be able to initialize appropriately before the app:</span></span>
    * <span data-ttu-id="898b0-150">Die ausführbare Datei von Unreal Insights wird im Ordner Binärdateien-Engine gespeichert, in der Regel wie folgt: "c:\programme\epic Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe"</span><span class="sxs-lookup"><span data-stu-id="898b0-150">The Unreal Insights executable is stored in the binaries engine folder, usually as follows: "C:\Program Files\Epic Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe"</span></span>

![Screenshot der ausführbaren Datei "Unreal Insights"](images/unreal-insights-img-12.png)

6.  <span data-ttu-id="898b0-152">Wählen Sie **zurück** , um zum Stamm des Dialog Felds für das **Projekt** Startfeld zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="898b0-152">Select **Back** to return to the root of the **Project Launcher** dialog</span></span>
7.  <span data-ttu-id="898b0-153">Klicken Sie im Editor auf **Start** im benutzerdefinierten Start Profil.</span><span class="sxs-lookup"><span data-stu-id="898b0-153">Back in the editor, Click **Launch** on your custom launch profile</span></span>

![Bildschirm Abbildung von benutzerdefinierten Start Profilen](images/unreal-insights-img-13.png)

8.  <span data-ttu-id="898b0-155">Sehen Sie sich an, wie Ihr Projekt verpackt, auf Ihrem Gerät installiert und gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="898b0-155">Watch as your project is packaged up, installed on your device, and launched</span></span>

## <a name="profiling"></a><span data-ttu-id="898b0-156">Profilerstellung</span><span class="sxs-lookup"><span data-stu-id="898b0-156">Profiling</span></span>

<span data-ttu-id="898b0-157">Zurück in Unreal Insights: Wählen Sie die **Live** Verbindung zum Gerät aus, um die Profilerstellung zu starten.</span><span class="sxs-lookup"><span data-stu-id="898b0-157">Back in Unreal Insights, select the **Live** connection to your device to start profiling</span></span>

<span data-ttu-id="898b0-158">Das benutzerdefinierte Profil wird von Projekten gemeinsam genutzt.</span><span class="sxs-lookup"><span data-stu-id="898b0-158">The custom profile is shared between projects.</span></span> <span data-ttu-id="898b0-159">Von hier aus können Sie das von Ihnen erstellte benutzerdefinierte Profil verwenden, anstatt jedes Mal dies zu tun.</span><span class="sxs-lookup"><span data-stu-id="898b0-159">From here on out, you can use the custom profile you created instead of having to do this every time.</span></span> <span data-ttu-id="898b0-160">Sie müssen die Verbindung mit dem Gerät nur bei jedem Start von Unreal mit den Schritten 3 bis 6 im [Abschnitt Setup](#setup)neu erstellen.</span><span class="sxs-lookup"><span data-stu-id="898b0-160">You only need to recreate the connection to the device every time you start Unreal with steps 3 to 6 in the [setup section](#setup).</span></span>

## <a name="see-also"></a><span data-ttu-id="898b0-161">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="898b0-161">See also</span></span>
* [<span data-ttu-id="898b0-162">Unreal Insights-Dokumentation</span><span class="sxs-lookup"><span data-stu-id="898b0-162">Unreal Insights documentation</span></span>](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/index.html)

