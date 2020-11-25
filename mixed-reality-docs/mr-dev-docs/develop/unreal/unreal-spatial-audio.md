---
title: Räumliche Audiowiedergabe in Unreal
description: Lernen Sie die Ein- und Ausgaben des Spatial Audio-Plug-Ins für die Unreal-Engine kennen.
author: hferrone
ms.author: v-hferrone
ms.date: 06/15/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Streaming, Remoting, Mixed Reality, Entwicklung, erste Schritte, Features, neues Projekt, Emulator, Dokumentation, Leitfäden, Features, Hologramme, Spieleentwicklung, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, räumliche Audiowiedergabe
ms.openlocfilehash: 25fa60b4e55ec0f3bd0875ad88834981d198f7f5
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679799"
---
# <a name="spatial-audio-in-unreal"></a><span data-ttu-id="a6182-104">Räumliche Audiowiedergabe in Unreal</span><span class="sxs-lookup"><span data-stu-id="a6182-104">Spatial Audio in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="a6182-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="a6182-105">Overview</span></span>

<span data-ttu-id="a6182-106">Anders als beim Sehen hören Menschen 360-Grad-Surroundsound.</span><span class="sxs-lookup"><span data-stu-id="a6182-106">Unlike vision, humans hear in 360 degree surround sound.</span></span> <span data-ttu-id="a6182-107">Räumliche Audiowiedergabe emuliert die Funktionsweise des menschlichen Hörens und stellt die Hinweise bereit, die zum Erkennen von Klangpositionen im Raum erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="a6182-107">Spatial sound emulates how human hearing works, providing the cues needed to identify sound locations in world-space.</span></span> <span data-ttu-id="a6182-108">Wenn Sie Ihren Mixed Reality-Anwendungen räumliche Audiowiedergabe hinzufügen, steigern Sie den Grad des Eintauchens, das Ihre Benutzer erleben.</span><span class="sxs-lookup"><span data-stu-id="a6182-108">When you add spatial sound in your mixed reality applications, you're enhancing the level of immersion your users experience.</span></span>  

<span data-ttu-id="a6182-109">Die erforderliche Verarbeitung für räumliche Audiowiedergabe in hoher Qualität ist komplex, daher besitzt HoloLens 2 dedizierte Hardware für die Verarbeitung dieser Klangobjekte.</span><span class="sxs-lookup"><span data-stu-id="a6182-109">High quality spatial sound processing is complex, so the HoloLens 2 comes with dedicated hardware for processing those sound objects.</span></span>  <span data-ttu-id="a6182-110">Damit Sie auf diese Hardwareunterstützung bei der Verarbeitung zugreifen können, müssen Sie das **MicrosoftSpatialSound**-Plug-In in Ihrem Unreal-Projekt installieren.</span><span class="sxs-lookup"><span data-stu-id="a6182-110">Before you can access this hardware processing support, you'll need to install the **MicrosoftSpatialSound** plugin in your Unreal project.</span></span> <span data-ttu-id="a6182-111">Dieser Artikel führt Sie durch die Installation und Konfiguration des Plug-Ins und weist Sie auf ausführlichere Ressourcen für die Verwendung von räumlicher Audiowiedergabe in der Unreal-Engine hin.</span><span class="sxs-lookup"><span data-stu-id="a6182-111">This article will walk you through the installation and configuration of that plugin and point you towards more in-depth resources for using spatial sound in the Unreal engine.</span></span>

## <a name="installing-the-microsoft-spatial-sound-plugin"></a><span data-ttu-id="a6182-112">Installieren des Microsoft Spatial Sound-Plug-Ins</span><span class="sxs-lookup"><span data-stu-id="a6182-112">Installing the Microsoft Spatial Sound plugin</span></span>

<span data-ttu-id="a6182-113">Der erste Schritt beim Hinzufügen von Raumklang zu Ihrem Projekt ist die Installation des Microsoft Spatial Sound-Plug-Ins, das Sie hier finden können:</span><span class="sxs-lookup"><span data-stu-id="a6182-113">The first step to adding spatial sound to your project is installing the Microsoft Spatial Sound plugin, which you can find by:</span></span>

1. <span data-ttu-id="a6182-114">Klicken Sie auf **Bearbeiten > Plug-Ins**, und suchen Sie im Suchfeld nach **MicrosoftSpatialSound**.</span><span class="sxs-lookup"><span data-stu-id="a6182-114">Clicking **Edit > Plugins** and searching for **MicrosoftSpatialSound** in the search box.</span></span>
2. <span data-ttu-id="a6182-115">Aktivieren Sie das Kontrollkästchen **Aktiviert** im **MicrosoftSpatialSound**-Plug-In.</span><span class="sxs-lookup"><span data-stu-id="a6182-115">Selecting the **Enabled** checkbox in the **MicrosoftSpatialSound** plugin.</span></span>
3. <span data-ttu-id="a6182-116">Starten Sie auf der Plug-Ins-Seite den Unreal Editor neu, indem Sie **Jetzt neu starten** auswählen.</span><span class="sxs-lookup"><span data-stu-id="a6182-116">Restarting the Unreal Editor by selecting **Restart Now** from the plugins page.</span></span>

> [!NOTE]
> <span data-ttu-id="a6182-117">Wenn dies noch nicht geschehen ist, müssen Sie die Plug-Ins **Microsoft Windows Mixed Reality** und **HoloLens** installieren, indem Sie die Anweisungen im Abschnitt **[Initialisieren des Projekts](tutorials/unreal-uxt-ch2.md)** unserer Reihe mit Unreal-Tutorials befolgen.</span><span class="sxs-lookup"><span data-stu-id="a6182-117">If you haven't already, you'll need to install the **Microsoft Windows Mixed Reality** and **HoloLens** plugins by following the instructions in the **[Initializing your project](tutorials/unreal-uxt-ch2.md)** section of our Unreal tutorial series.</span></span>

![Unreal Spatial Audio-Plug-In](images/unreal-spatial-audio-img-01.png)

<span data-ttu-id="a6182-119">Nach dem Neustart des Editors ist Ihr Projekt fertig eingerichtet.</span><span class="sxs-lookup"><span data-stu-id="a6182-119">Once the editor restarts, your project is all set!</span></span>


## <a name="setting-the-spatialization-plugin-for-hololens-2-platform"></a><span data-ttu-id="a6182-120">Festlegen des Raumklang-Plug-Ins für die HoloLens 2-Plattform</span><span class="sxs-lookup"><span data-stu-id="a6182-120">Setting the spatialization plugin for HoloLens 2 platform</span></span>
<span data-ttu-id="a6182-121">Die Konfiguration des Raumklang-Plug-Ins erfolgt auf Plattformbasis.</span><span class="sxs-lookup"><span data-stu-id="a6182-121">Configuring the spatialization plugin is done on a per-platform basis.</span></span>  <span data-ttu-id="a6182-122">Sie können das Microsoft Spatial Sound-Plug-In für HoloLens 2 in folgender Weise aktivieren:</span><span class="sxs-lookup"><span data-stu-id="a6182-122">You can enable the Microsoft Spatial Sound plugin for the HoloLens 2 by:</span></span>
1. <span data-ttu-id="a6182-123">Wählen Sie **Bearbeiten > Projekteinstellungen** aus, scrollen Sie zu **Plattformen**, und klicken Sie auf **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="a6182-123">Selecting **Edit > Project Settings**, scrolling to **Platforms** and clicking **HoloLens**.</span></span>
2. <span data-ttu-id="a6182-124">Erweitern Sie die **Audio**-Eigenschaften, und legen Sie das Feld **Spatialization Plugin** (Raumklang-Plug-In) auf **Microsoft Spatial Sound** fest.</span><span class="sxs-lookup"><span data-stu-id="a6182-124">Expanding the **Audio** properties and setting the **Spatialization Plugin** field to **Microsoft Spatial Sound**.</span></span>

![Raumklang-Plug-In für die HoloLens-Plattform](images/unreal-spatial-audio-img-02.png)

<span data-ttu-id="a6182-126">Wenn Sie die Vorschau Ihrer Anwendung im Unreal-Editor auf einem Desktop-PC ausführen möchten, müssen Sie die Schritte oben für die **Windows**-Plattform wiederholen:</span><span class="sxs-lookup"><span data-stu-id="a6182-126">If you're going to be previewing your application in the Unreal editor on a desktop PC, you'll need to repeat the above steps for the **Windows** platform:</span></span>

![Raumklang-Plug-In für die Windows-Plattform](images/unreal-spatial-audio-img-05.png)

## <a name="enabling-spatial-audio-on-your-workstation"></a><span data-ttu-id="a6182-128">Aktivieren von räumlicher Audiowiedergabe auf Ihrer Arbeitsstation</span><span class="sxs-lookup"><span data-stu-id="a6182-128">Enabling spatial audio on your workstation</span></span>
<span data-ttu-id="a6182-129">Die räumliche Audiowiedergabe ist in Desktopversionen von Windows standardmäßig deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="a6182-129">Spatial audio is disabled by default on desktop versions of Windows.</span></span> <span data-ttu-id="a6182-130">Sie können sie wie folgt aktivieren:</span><span class="sxs-lookup"><span data-stu-id="a6182-130">You can enable it by:</span></span>
* <span data-ttu-id="a6182-131">Klicken Sie mit der rechten Maustaste auf das **Lautstärke**-Symbol in der Taskleiste.</span><span class="sxs-lookup"><span data-stu-id="a6182-131">Right-clicking on the **volume** icon in the task bar.</span></span>
    + <span data-ttu-id="a6182-132">Wählen Sie **Raumklang -> Windows Sonic für Kopfhörer** aus, um die beste Darstellung des Höreindrucks mit HoloLens 2 zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="a6182-132">Choose **Spatial sound -> Windows Sonic for Headphones** to get the best representation of what you'll hear on HoloLens 2.</span></span>

![Raumklang-Plug-In](images/unreal-spatial-audio-img-04.png)

> [!NOTE]
><span data-ttu-id="a6182-134">Diese Einstellung ist nur erforderlich, wenn Sie beabsichtigen, das Projekt im Unreal-Editor zu testen.</span><span class="sxs-lookup"><span data-stu-id="a6182-134">This setting is only required if you plan to test your project in the Unreal editor.</span></span>

## <a name="creating-attenuation-objects"></a><span data-ttu-id="a6182-135">Erstellen von Dämpfungsobjekten</span><span class="sxs-lookup"><span data-stu-id="a6182-135">Creating Attenuation objects</span></span>
<span data-ttu-id="a6182-136">Nachdem Sie die erforderlichen Plug-Ins installiert und konfiguriert haben:</span><span class="sxs-lookup"><span data-stu-id="a6182-136">After you've installed and configured the necessary plugins:</span></span>
1. <span data-ttu-id="a6182-137">Suchen Sie nach einem Akteur **Ambient Sound** (Raumklang) im Fenster **Place Actors** (Akteure platzieren), und ziehen Sie ihn auf das **Szenenfenster**.</span><span class="sxs-lookup"><span data-stu-id="a6182-137">Search for an **Ambient Sound** actor in the **Place Actors** window and drag it into the **Scene** window.</span></span>

![Hinzufügen des Raumklang-Akteurs](images/unreal-spatial-audio-img-07.png)

2. <span data-ttu-id="a6182-139">Machen Sie den Akteur **Ambient Sound** (Raumklang) zu einem untergeordneten Element eines visuellen Elements in Ihrer Szene.</span><span class="sxs-lookup"><span data-stu-id="a6182-139">Make the **Ambient Sound** actor a child of a visual element in your scene.</span></span>
    * <span data-ttu-id="a6182-140">Ein Raumklang-Akteur hat standardmäßig keine visuelle Darstellung, Sie hören also lediglich einen Klang von seiner Position in der Szene.</span><span class="sxs-lookup"><span data-stu-id="a6182-140">An Ambient Sound actor doesn't have any visual representation by default, so you'll only hear a sound from its position in the scene.</span></span> <span data-ttu-id="a6182-141">Wenn Sie den Akteur an ein visuelles Element anfügen, können Sie ihn sehen und wie jedes andere Medienobjekt verschieben.</span><span class="sxs-lookup"><span data-stu-id="a6182-141">Attaching it to a visual element let's you see and move the actor like any other asset.</span></span>

3.  <span data-ttu-id="a6182-142">Klicken Sie mit der rechen Maustaste auf den **Inhalts-Browser**, und wählen Sie **Create Advanced Asset -> Sounds -> Sound Attenuation** (Erweitertes Medienobjekt erstellen > Sounds > Klangdämpfung) aus:</span><span class="sxs-lookup"><span data-stu-id="a6182-142">Right-click on the **Content Browser** and selecting **Create Advanced Asset -> Sounds -> Sound Attenuation**:</span></span>

![Erstellen eines Klangdämpfungs-Medienobjekts](images/unreal-spatial-audio-img-06.png)

4. <span data-ttu-id="a6182-144">Klicken Sie mit der rechten Maustaste auf das Medienobjekt **Sound Attenuation** (Klangdämpfung) im Fenster des **Inhalt-Browsers**, und wählen Sie die Option **Bearbeiten** aus, um das Eigenschaftenfenster anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="a6182-144">Right-click on the **Sound Attenuation** asset in the **Content Browser** window and select the **Edit** option to bring up the properties window.</span></span>
    * <span data-ttu-id="a6182-145">Ändern Sie die **Spatialization Method** (Raumklangverfahren) in **Binaural**.</span><span class="sxs-lookup"><span data-stu-id="a6182-145">Switch the **Spatialization Method** to **Binaural**.</span></span>

![Festlegen des Raumklangverfahrens](images/unreal-spatial-audio-img-03.png)

5. <span data-ttu-id="a6182-147">Wählen Sie den Akteur **Ambient Sound** (Raumklang) aus, und scrollen Sie nach unten zum Abschnitt **Attenuation** (Dämpfung) im Bereich **Details**.</span><span class="sxs-lookup"><span data-stu-id="a6182-147">Select the **Ambient Sound** actor and scroll down to the **Attenuation** section in the **Details** panel.</span></span>
    * <span data-ttu-id="a6182-148">Legen Sie die Einstellung **Attenuation Settings** (Dämpfungseinstellungen) auf das von Ihnen erstellte Medienobjekt **Sound Attenuation** (Klangdämpfung) fest.</span><span class="sxs-lookup"><span data-stu-id="a6182-148">Set the **Attenuation Settings** property to the **Sound Attenuation** asset you created.</span></span>

![Festlegen der Dämpfungseinstellung](images/unreal-spatial-audio-img-08.png)

6. <span data-ttu-id="a6182-150">Legen Sie das **Klangmedienobjekt** fest, das Sie an den Raumklang-Akteur anfügen möchten, indem Sie die Eigenschaft **Sound** des Raumklang-Akteurs auf die zu verwendende SoundAsset-Datei festlegen.</span><span class="sxs-lookup"><span data-stu-id="a6182-150">Set the **Sound Asset** you want to attach to the Ambient Sound actor by updating the **Sound** property of the Ambient Sound actor to specify the SoundAsset file to use.</span></span>

![Festlegen des Klangmedienobjekts](images/unreal-spatial-audio-img-09.png)

> [!NOTE]
> <span data-ttu-id="a6182-152">Die SoundAsset-Datei muss in Mono vorliegen, um mithilfe des Microsoft Spatial Sound-Plug-Ins mit Rauminformationen versehen zu werden.</span><span class="sxs-lookup"><span data-stu-id="a6182-152">The SoundAsset file needs to be mono to be spatialized with the Microsoft Spatial Sound plug-in.</span></span> <span data-ttu-id="a6182-153">Sie können die Eigenschaften der Sounddatei anzeigen, indem Sie den Mauszeiger im Fenster des Inhalt-Browsers auf dem Medienobjekt ruhen lassen, wie im Screenshot unten dargestellt.</span><span class="sxs-lookup"><span data-stu-id="a6182-153">You can find the sound file properties by hovering over the asset in the Content Browser window as shown in the screenshot below.</span></span>

![Neues Klangdämpfungs-Medienobjekt](images/unreal-spatial-audio-img-10.png)

<span data-ttu-id="a6182-155">Nachdem all dies konfiguriert wurde, kann der Raumklang mithilfe der dedizierten Hardware-Abladungsunterstützung in HoloLens 2 mit Rauminformationen versehen werden.</span><span class="sxs-lookup"><span data-stu-id="a6182-155">Once all of this is configured the ambient sound can be spatialized using the dedicated hardware offload support on HoloLens 2.</span></span>

## <a name="configuring-objects-for-spatialization"></a><span data-ttu-id="a6182-156">Konfigurieren von Objekten für die räumliche Wiedergabe</span><span class="sxs-lookup"><span data-stu-id="a6182-156">Configuring objects for spatialization</span></span>
<span data-ttu-id="a6182-157">Das Arbeiten mit Raumklang bedeutet, dass Sie dafür zuständig sind, wie sich der Klang in einer virtuellen Umgebung verhält.</span><span class="sxs-lookup"><span data-stu-id="a6182-157">Working with spatial audio means you're in charge of managing how sound behaves in a virtual environment.</span></span> <span data-ttu-id="a6182-158">Der Hauptschwerpunkt liegt auf dem Erstellen von Klangobjekten, die lauter erscheinen, wenn der Benutzer sich in der Nähe befindet, und leiser, wenn der Benutzer weit weg ist.</span><span class="sxs-lookup"><span data-stu-id="a6182-158">Your main focus is creating sound objects that appear louder when the user is close, and quieter when the user is far away.</span></span> <span data-ttu-id="a6182-159">Dies wird als Klangdämpfung bezeichnet und erzeugt den Eindruck, als ob Klänge an einem festen Ort positioniert wären.</span><span class="sxs-lookup"><span data-stu-id="a6182-159">This is referred to as sound attenuation, making sounds appear as if they are positioned in a fixed spot.</span></span>

<span data-ttu-id="a6182-160">Alle Dämpfungsobjekte umfassen konfigurierbare Einstellungen für:</span><span class="sxs-lookup"><span data-stu-id="a6182-160">All attenuation objects come with modifiable settings for:</span></span>
* <span data-ttu-id="a6182-161">Abstand</span><span class="sxs-lookup"><span data-stu-id="a6182-161">Distance</span></span>
* <span data-ttu-id="a6182-162">Raumklang</span><span class="sxs-lookup"><span data-stu-id="a6182-162">Spatialization</span></span>
* <span data-ttu-id="a6182-163">Luftabsorption</span><span class="sxs-lookup"><span data-stu-id="a6182-163">Air Absorption</span></span>
* <span data-ttu-id="a6182-164">Listenerfokus</span><span class="sxs-lookup"><span data-stu-id="a6182-164">Listener Focus</span></span>
* <span data-ttu-id="a6182-165">Nachhall-Send</span><span class="sxs-lookup"><span data-stu-id="a6182-165">Reverb Send</span></span>
* <span data-ttu-id="a6182-166">Okklusion</span><span class="sxs-lookup"><span data-stu-id="a6182-166">Occlusion</span></span>

<span data-ttu-id="a6182-167">[Klangdämpfung in Unreal](https://docs.unrealengine.com/Engine/Audio/DistanceModelAttenuation/index.html) bietet zu jedem dieser Themen Details und spezifische Eigenheiten der Implementierung.</span><span class="sxs-lookup"><span data-stu-id="a6182-167">[Sound attenuation in Unreal](https://docs.unrealengine.com/Engine/Audio/DistanceModelAttenuation/index.html) has details and implementation specifics on each of these topics.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="a6182-168">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="a6182-168">Next Development Checkpoint</span></span>

<span data-ttu-id="a6182-169">Wenn Sie dem Weg der Unreal-Entwicklungsprüfpunkte folgen, den wir entworfen haben, befinden Sie sich mitten im Kennenlernen der MRTK-Grundbausteine.</span><span class="sxs-lookup"><span data-stu-id="a6182-169">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="a6182-170">Von hier aus können Sie mit dem nächsten Baustein fortfahren:</span><span class="sxs-lookup"><span data-stu-id="a6182-170">From here, you can proceed to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a6182-171">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="a6182-171">Voice input</span></span>](unreal-voice-input.md)

<span data-ttu-id="a6182-172">Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:</span><span class="sxs-lookup"><span data-stu-id="a6182-172">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a6182-173">HoloLens-Kamera</span><span class="sxs-lookup"><span data-stu-id="a6182-173">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="a6182-174">Sie können jederzeit zu den [Prüfpunkten für die Unreal-Entwicklung](unreal-development-overview.md#2-core-building-blocks) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="a6182-174">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>


## <a name="see-also"></a><span data-ttu-id="a6182-175">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="a6182-175">See also</span></span>
* [<span data-ttu-id="a6182-176">Raumklang</span><span class="sxs-lookup"><span data-stu-id="a6182-176">Spatial Sound</span></span>](https://docs.microsoft.com/windows/mixed-reality/spatial-sound)
* [<span data-ttu-id="a6182-177">Raumklangentwurf</span><span class="sxs-lookup"><span data-stu-id="a6182-177">Spatial Sound Design</span></span>](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design)
* [<span data-ttu-id="a6182-178">MR räumlich 220: Raumklang</span><span class="sxs-lookup"><span data-stu-id="a6182-178">MR Spatial 220: Spatial sound</span></span>](https://docs.microsoft.com/windows/mixed-reality/holograms-220)
