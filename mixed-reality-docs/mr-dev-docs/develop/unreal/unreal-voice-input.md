---
title: Spracheingabe
description: Tutorial zum Einrichten und Verwenden von Spracheingaben in hololens 2 und Unreal Engine
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, Unreal, Unreal Engine 4, UE4, hololens 2, Voice, Voice Input, Spracherkennung, gemischte Realität, Entwicklung, Features, Dokumentation, Anleitungen, holograms, Spieleentwicklung
ms.openlocfilehash: 88ab39de5f219691a6c3fe5b4ad3008d9614668e
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2020
ms.locfileid: "91689643"
---
# <a name="voice-input-in-unreal"></a><span data-ttu-id="7ad76-104">Spracheingabe in Unreal</span><span class="sxs-lookup"><span data-stu-id="7ad76-104">Voice Input in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="7ad76-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="7ad76-105">Overview</span></span>
<span data-ttu-id="7ad76-106">Mit der Spracheingabe in Unreal können Sie mit einem – Hologramm interagieren, ohne Handgesten zu verwenden, und es wird nur hololens 2 unterstützt.</span><span class="sxs-lookup"><span data-stu-id="7ad76-106">Voice input in Unreal allows you to interact with a hologram without having to use hand gestures and is only supported HoloLens 2.</span></span> <span data-ttu-id="7ad76-107">Obwohl die Spracheingabe auf hololens 2 von der gleichen Engine unterstützt wird, die Sprache in allen anderen universellen Windows-Apps unterstützt, verwendet Unreal ein eingeschränkteren Modul, das eine selbstständig beschränkte Engine für die Verarbeitung von Spracheingaben verwendet.</span><span class="sxs-lookup"><span data-stu-id="7ad76-107">Even though voice input on HoloLens 2 is powered by the same engine that supports speech in all other Universal Windows Apps, Unreal uses a more limited engine of its own to process voice input.</span></span> <span data-ttu-id="7ad76-108">Dies schränkt die Spracheingabe Features in Unreal auf vordefinierte sprach Zuordnungen ein, die in den folgenden Abschnitten behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="7ad76-108">This limits voice input features in Unreal to predefined speech mappings, which is covered in the following sections.</span></span> 

## <a name="enabling-speech-recognition"></a><span data-ttu-id="7ad76-109">Aktivieren der Spracherkennung</span><span class="sxs-lookup"><span data-stu-id="7ad76-109">Enabling Speech Recognition</span></span>

<span data-ttu-id="7ad76-110">So aktivieren Sie die Spracherkennung in hololens:</span><span class="sxs-lookup"><span data-stu-id="7ad76-110">To enable speech recognition on HoloLens:</span></span>
1. <span data-ttu-id="7ad76-111">Wählen Sie **Projekteinstellungen > Plattform > hololens > Funktionen** aus, und aktivieren Sie das **Mikrofon** .</span><span class="sxs-lookup"><span data-stu-id="7ad76-111">Select **Project Settings > Platform > HoloLens > Capabilities** and enable **Microphone** .</span></span> 
2. <span data-ttu-id="7ad76-112">Aktivieren Sie die Spracherkennung in den **Einstellungen > Datenschutz > Sprache** und wählen Sie **Englisch** aus.</span><span class="sxs-lookup"><span data-stu-id="7ad76-112">Enabled speech recognition in **Settings > Privacy > Speech** and select **English** .</span></span>

> [!NOTE]
> <span data-ttu-id="7ad76-113">Die Spracherkennung funktioniert immer in der in der App " **Einstellungen** " konfigurierten Windows-Anzeige Sprache.</span><span class="sxs-lookup"><span data-stu-id="7ad76-113">Speech recognition always functions in the Windows display language configured in the **Settings** app.</span></span> <span data-ttu-id="7ad76-114">Es wird empfohlen, dass Sie auch die **Online Spracherkennung** für die beste Dienst Qualität aktivieren.</span><span class="sxs-lookup"><span data-stu-id="7ad76-114">It’s recommended that you also enable **Online speech recognition** for the best service quality.</span></span>

![Einstellungen für die Windows-Spracherkennung](images/unreal/speech-recognition-settings.png)

3. <span data-ttu-id="7ad76-116">Ein Dialogfeld wird angezeigt, wenn die Anwendung zum ersten Mal gefragt wird, ob Sie das Mikrofon aktivieren möchten.</span><span class="sxs-lookup"><span data-stu-id="7ad76-116">A dialog will show up when the application first starts to ask if you want to enable the microphone.</span></span> <span data-ttu-id="7ad76-117">Wenn Sie **Ja** auswählen, wird die Spracheingabe in der APP gestartet.</span><span class="sxs-lookup"><span data-stu-id="7ad76-117">Selecting **Yes** starts voice input in the app.</span></span>

<span data-ttu-id="7ad76-118">Die Spracheingabe erfordert keine speziellen Windows Mixed Reality-APIs. Es basiert auf der vorhandenen API für die [Eingabe](https://docs.unrealengine.com/Gameplay/Input/index.html) Zuordnung von Unreal Engine 4.</span><span class="sxs-lookup"><span data-stu-id="7ad76-118">Voice input doesn’t require any special Windows Mixed Reality APIs; it's built on the existing Unreal Engine 4 [Input](https://docs.unrealengine.com/Gameplay/Input/index.html) mapping API.</span></span> 

## <a name="adding-speech-mappings"></a><span data-ttu-id="7ad76-119">Hinzufügen von sprach Zuordnungen</span><span class="sxs-lookup"><span data-stu-id="7ad76-119">Adding Speech Mappings</span></span>
<span data-ttu-id="7ad76-120">Das Verbinden von Sprache und Aktion ist ein wichtiger Schritt bei der Verwendung von Spracheingaben.</span><span class="sxs-lookup"><span data-stu-id="7ad76-120">Connecting speech to action is an important step when using voice input.</span></span> <span data-ttu-id="7ad76-121">Diese Zuordnungen überwachen die APP auf sprach Schlüsselwörter, die ein Benutzer möglicherweise anweist, und lösen dann eine verknüpfte Aktion aus.</span><span class="sxs-lookup"><span data-stu-id="7ad76-121">These mappings monitor the app for speech keywords that a user might say, then fire off a linked action.</span></span> <span data-ttu-id="7ad76-122">Sie finden sprach Zuordnungen wie folgt:</span><span class="sxs-lookup"><span data-stu-id="7ad76-122">You can find Speech Mappings by:</span></span>
1. <span data-ttu-id="7ad76-123">Wählen Sie **> Projekteinstellungen bearbeiten** aus, Scrollen Sie zum Abschnitt **Engine** , und klicken Sie auf **Eingabe** .</span><span class="sxs-lookup"><span data-stu-id="7ad76-123">Selecting **Edit > Project Settings** , scrolling to the **Engine** section, and clicking **Input** .</span></span>

<span data-ttu-id="7ad76-124">So fügen Sie eine neue sprach Zuordnung für einen Jump-Befehl hinzu:</span><span class="sxs-lookup"><span data-stu-id="7ad76-124">To add a new Speech Mapping for a jump command:</span></span>
1. <span data-ttu-id="7ad76-125">Klicken Sie auf das **+** Symbol neben **Array Elemente** , und füllen Sie die folgenden Werte aus:</span><span class="sxs-lookup"><span data-stu-id="7ad76-125">Click the **+** icon next to **Array elements** and fill out the following values:</span></span>
    * <span data-ttu-id="7ad76-126">**jumpword** für **Aktions Name**</span><span class="sxs-lookup"><span data-stu-id="7ad76-126">**jumpWord** for **Action Name**</span></span>
    * <span data-ttu-id="7ad76-127">**springen** für **sprach Schlüsselwort**</span><span class="sxs-lookup"><span data-stu-id="7ad76-127">**jump** for **Speech Keyword**</span></span>

> [!NOTE]
> <span data-ttu-id="7ad76-128">Alle englischen Wörter oder kurzsätze können als Schlüsselwort verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="7ad76-128">Any English word(s) or short sentence(s) can be used as a keyword.</span></span> 

![Eingabeeinstellungen der UE4-Engine](images/unreal/engine-input.png)

<span data-ttu-id="7ad76-130">Sprach Zuordnungen können als Eingabe Komponenten wie Aktions-oder Achsen Zuordnungen oder als Blueprint-Knoten im Ereignis Diagramm verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="7ad76-130">Speech Mappings can be used as Input components like Action or Axis Mappings or as blueprint nodes in the Event Graph.</span></span> <span data-ttu-id="7ad76-131">Beispielsweise können Sie den Jump-Befehl verknüpfen, um zwei verschiedene Protokolle auszugeben, je nachdem, wann das Wort gesprochen wird:</span><span class="sxs-lookup"><span data-stu-id="7ad76-131">For example, you could link the jump command to print out two different logs depending on when the word is spoken:</span></span>

1. <span data-ttu-id="7ad76-132">Doppelklicken Sie auf eine Blaupause, um Sie im **Ereignis Diagramm** zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="7ad76-132">Double-click a blueprint to open it in the **Event Graph** .</span></span>
2. <span data-ttu-id="7ad76-133">**Klicken Sie mit der rechten Maustaste** , und suchen Sie nach dem **Aktions Namen** ihrer sprach Zuordnung (in diesem Fall **jumpword** ), und drücken Sie dann die **Eingabe** Taste.</span><span class="sxs-lookup"><span data-stu-id="7ad76-133">**Right-click** and search for the **Action Name** of your speech mapping (in this case **jumpWord** ), then hit **Enter** .</span></span> <span data-ttu-id="7ad76-134">Dadurch wird dem Diagramm ein **Eingabe Aktions** Knoten hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="7ad76-134">This adds an **Input Action** node to the graph.</span></span>
3. <span data-ttu-id="7ad76-135">Ziehen Sie die **gedrückte** PIN per Drag & Drop auf den Knoten **Druck Zeichenfolge** , wie in der folgenden Abbildung dargestellt</span><span class="sxs-lookup"><span data-stu-id="7ad76-135">Drag and drop the **Pressed** pin to **Print String** node as shown in the image below.</span></span> <span data-ttu-id="7ad76-136">Sie können die **freigegebene** Pin leer lassen, ohne dass für sprach Zuordnungen etwas ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="7ad76-136">You can leave the **Released** pin empty, it won't execute anything for speech mappings.</span></span>
 
![Einfache Aktion für Stimme](images/unreal/voice-input-img-03.png)

4. <span data-ttu-id="7ad76-138">Spielen Sie die APP, sagen Sie, das Wort **springt** , und sehen Sie sich an, dass die Konsole die Protokolle ausgibt</span><span class="sxs-lookup"><span data-stu-id="7ad76-138">Play the app, say the word **jump** and watch the console print out the logs!</span></span>

<span data-ttu-id="7ad76-139">Das ist alles, was Sie benötigen, um Ihren hololens-apps in Unreal Spracheingaben hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="7ad76-139">That's all the setup you'll need to start adding voice input to your HoloLens apps in Unreal.</span></span> <span data-ttu-id="7ad76-140">Weitere Informationen zu Sprache und Interaktivität finden Sie unter den folgenden Links. Stellen Sie sicher, dass Sie sich über die Benutzeroberflächen Gedanken machen, die Sie für Ihre Benutzer erstellen.</span><span class="sxs-lookup"><span data-stu-id="7ad76-140">You can find more information on speech and interactivity can be found at the links below, and be sure to think about the experience you're creating for your users.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="7ad76-141">Nächster Entwicklungs Prüfpunkt</span><span class="sxs-lookup"><span data-stu-id="7ad76-141">Next Development Checkpoint</span></span>

<span data-ttu-id="7ad76-142">Wenn Sie die unechte Development Checkpoint Journey befolgen, die wir angelegt haben, sind Sie die nächste Aufgabe, die Funktionen und APIs der Mixed Reality-Plattform zu untersuchen:</span><span class="sxs-lookup"><span data-stu-id="7ad76-142">If you're following the Unreal development checkpoint journey we've laid out, you're next task is exploring the Mixed Reality platform capabilities and APIs:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="7ad76-143">HoloLens-Kamera</span><span class="sxs-lookup"><span data-stu-id="7ad76-143">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="7ad76-144">Sie können jederzeit jederzeit zu den [unechten Entwicklungs Prüfpunkten](unreal-development-overview.md#2-core-building-blocks) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="7ad76-144">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ad76-145">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="7ad76-145">See also</span></span>
* [<span data-ttu-id="7ad76-146">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="7ad76-146">Voice Input</span></span>](../../design/voice-input.md)
* [<span data-ttu-id="7ad76-147">Anvisieren und Ausführen</span><span class="sxs-lookup"><span data-stu-id="7ad76-147">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="7ad76-148">Instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="7ad76-148">Instinctual interactions</span></span>](../../design/interaction-fundamentals.md)

