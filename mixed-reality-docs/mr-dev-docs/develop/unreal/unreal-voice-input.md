---
title: Spracheingabe in Unreal
description: Erfahren Sie, wie Sie Spracheingaben, sprach Zuordnungen und erkennungsungen in Unreal Mixed Reality-Apps für hololens 2-Geräte einrichten und verwenden.
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, Unreal, Unreal Engine 4, UE4, hololens 2, Voice, Voice Input, Spracherkennung, gemischte Realität, Entwicklung, Features, Dokumentation, Leitfäden, holograms, Spieleentwicklung, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: c7ac523258dc44aa261470aea8cdf21f32c915b2
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010070"
---
# <a name="voice-input-in-unreal"></a><span data-ttu-id="be5e6-104">Spracheingabe in Unreal</span><span class="sxs-lookup"><span data-stu-id="be5e6-104">Voice Input in Unreal</span></span>

<span data-ttu-id="be5e6-105">Mit der Spracheingabe in Unreal können Sie mit einem – Hologramm interagieren, ohne Handgesten zu verwenden, und es wird nur hololens 2 unterstützt.</span><span class="sxs-lookup"><span data-stu-id="be5e6-105">Voice input in Unreal allows you to interact with a hologram without having to use hand gestures and is only supported HoloLens 2.</span></span> <span data-ttu-id="be5e6-106">Spracheingaben auf hololens 2 werden von derselben Engine unterstützt, die Sprache in allen anderen universellen Windows-Apps unterstützt, aber Unreal verwendet ein eingeschränkteren Modul, um die Spracheingabe zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="be5e6-106">Voice input on HoloLens 2 is powered by the same engine that supports speech in all other Universal Windows Apps, but Unreal uses a more limited engine to process voice input.</span></span> <span data-ttu-id="be5e6-107">Dies schränkt die Spracheingabe Features in Unreal auf vordefinierte sprach Zuordnungen ein, die in den folgenden Abschnitten behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="be5e6-107">This limits voice input features in Unreal to predefined speech mappings, which are covered in the following sections.</span></span> 

## <a name="enabling-speech-recognition"></a><span data-ttu-id="be5e6-108">Aktivieren der Spracherkennung</span><span class="sxs-lookup"><span data-stu-id="be5e6-108">Enabling Speech Recognition</span></span>

<span data-ttu-id="be5e6-109">So aktivieren Sie die Spracherkennung in hololens:</span><span class="sxs-lookup"><span data-stu-id="be5e6-109">To enable speech recognition on HoloLens:</span></span>
1. <span data-ttu-id="be5e6-110">Wählen Sie **Projekteinstellungen > Plattform > hololens > Funktionen** aus, und aktivieren Sie das **Mikrofon**.</span><span class="sxs-lookup"><span data-stu-id="be5e6-110">Select **Project Settings > Platform > HoloLens > Capabilities** and enable **Microphone**.</span></span> 
2. <span data-ttu-id="be5e6-111">Aktivieren Sie die Spracherkennung in den **Einstellungen > Datenschutz > Sprache** und wählen Sie **Englisch** aus.</span><span class="sxs-lookup"><span data-stu-id="be5e6-111">Enabled speech recognition in **Settings > Privacy > Speech** and select **English**.</span></span>

> [!NOTE]
> <span data-ttu-id="be5e6-112">Die Spracherkennung funktioniert immer in der in der App " **Einstellungen** " konfigurierten Windows-Anzeige Sprache.</span><span class="sxs-lookup"><span data-stu-id="be5e6-112">Speech recognition always functions in the Windows display language configured in the **Settings** app.</span></span> <span data-ttu-id="be5e6-113">Es wird empfohlen, dass Sie auch die **Online Spracherkennung** für die beste Dienst Qualität aktivieren.</span><span class="sxs-lookup"><span data-stu-id="be5e6-113">It’s recommended that you also enable **Online speech recognition** for the best service quality.</span></span>

![Einstellungen für die Windows-Spracherkennung](images/unreal/speech-recognition-settings.png)

3. <span data-ttu-id="be5e6-115">Ein Dialogfeld wird angezeigt, wenn die Anwendung zum ersten Mal gefragt wird, ob Sie das Mikrofon aktivieren möchten.</span><span class="sxs-lookup"><span data-stu-id="be5e6-115">A dialog will show up when the application first starts to ask if you want to enable the microphone.</span></span> <span data-ttu-id="be5e6-116">Wenn Sie **Ja** auswählen, wird die Spracheingabe in der APP gestartet.</span><span class="sxs-lookup"><span data-stu-id="be5e6-116">Selecting **Yes** starts voice input in the app.</span></span>

<span data-ttu-id="be5e6-117">Die Spracheingabe erfordert keine speziellen Windows Mixed Reality-APIs. Es basiert auf der vorhandenen API für die [Eingabe](https://docs.unrealengine.com/Gameplay/Input/index.html) Zuordnung von Unreal Engine 4.</span><span class="sxs-lookup"><span data-stu-id="be5e6-117">Voice input doesn’t require any special Windows Mixed Reality APIs; it's built on the existing Unreal Engine 4 [Input](https://docs.unrealengine.com/Gameplay/Input/index.html) mapping API.</span></span> 

## <a name="adding-speech-mappings"></a><span data-ttu-id="be5e6-118">Hinzufügen von sprach Zuordnungen</span><span class="sxs-lookup"><span data-stu-id="be5e6-118">Adding Speech Mappings</span></span>

<span data-ttu-id="be5e6-119">Das Verbinden von Sprache und Aktion ist ein wichtiger Schritt bei der Verwendung von Spracheingaben.</span><span class="sxs-lookup"><span data-stu-id="be5e6-119">Connecting speech to action is an important step when using voice input.</span></span> <span data-ttu-id="be5e6-120">Diese Zuordnungen überwachen die APP auf sprach Schlüsselwörter, die ein Benutzer möglicherweise anweist, und lösen dann eine verknüpfte Aktion aus.</span><span class="sxs-lookup"><span data-stu-id="be5e6-120">These mappings monitor the app for speech keywords that a user might say, then fire off a linked action.</span></span> <span data-ttu-id="be5e6-121">Sie finden sprach Zuordnungen wie folgt:</span><span class="sxs-lookup"><span data-stu-id="be5e6-121">You can find Speech Mappings by:</span></span>
1. <span data-ttu-id="be5e6-122">Wählen Sie **> Projekteinstellungen bearbeiten** aus, Scrollen Sie zum Abschnitt **Engine** , und klicken Sie auf **Eingabe**.</span><span class="sxs-lookup"><span data-stu-id="be5e6-122">Selecting **Edit > Project Settings**, scrolling to the **Engine** section, and clicking **Input**.</span></span>

<span data-ttu-id="be5e6-123">So fügen Sie eine neue sprach Zuordnung für einen Jump-Befehl hinzu:</span><span class="sxs-lookup"><span data-stu-id="be5e6-123">To add a new Speech Mapping for a jump command:</span></span>
1. <span data-ttu-id="be5e6-124">Wählen Sie das **+** Symbol neben **Array Elemente** aus, und geben Sie die folgenden Werte ein:</span><span class="sxs-lookup"><span data-stu-id="be5e6-124">Select the **+** icon next to **Array elements** and fill out the following values:</span></span>
    * <span data-ttu-id="be5e6-125">**jumpword** für **Aktions Name**</span><span class="sxs-lookup"><span data-stu-id="be5e6-125">**jumpWord** for **Action Name**</span></span>
    * <span data-ttu-id="be5e6-126">**springen** für **sprach Schlüsselwort**</span><span class="sxs-lookup"><span data-stu-id="be5e6-126">**jump** for **Speech Keyword**</span></span>

> [!NOTE]
> <span data-ttu-id="be5e6-127">Alle englischen Wörter oder kurzsätze können als Schlüsselwort verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="be5e6-127">Any English word(s) or short sentence(s) can be used as a keyword.</span></span> 

![Eingabeeinstellungen der UE4-Engine](images/unreal/engine-input.png)

<span data-ttu-id="be5e6-129">Sprach Zuordnungen können als Eingabe Komponenten wie Aktions-oder Achsen Zuordnungen oder als Blueprint-Knoten im Ereignis Diagramm verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="be5e6-129">Speech Mappings can be used as Input components like Action or Axis Mappings or as blueprint nodes in the Event Graph.</span></span> <span data-ttu-id="be5e6-130">Beispielsweise können Sie den Jump-Befehl verknüpfen, um zwei verschiedene Protokolle auszugeben, je nachdem, wann das Wort gesprochen wird:</span><span class="sxs-lookup"><span data-stu-id="be5e6-130">For example, you could link the jump command to print out two different logs depending on when the word is spoken:</span></span>

1. <span data-ttu-id="be5e6-131">Doppelklicken Sie auf eine Blaupause, um Sie im **Ereignis Diagramm** zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="be5e6-131">Double-click a blueprint to open it in the **Event Graph**.</span></span>
2. <span data-ttu-id="be5e6-132">**Klicken Sie mit der rechten Maustaste** , und suchen Sie nach dem **Aktions Namen** ihrer sprach Zuordnung (in diesem Fall **jumpword**), und drücken **Sie** dann die EINGABETASTE, um dem Diagramm einen **Eingabe Aktions** Knoten hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="be5e6-132">**Right-click** and search for the **Action Name** of your speech mapping (in this case **jumpWord**), then hit **Enter** to add an **Input Action** node to the graph.</span></span>
3. <span data-ttu-id="be5e6-133">Ziehen Sie die **gedrückte** PIN per Drag & Drop auf den Knoten **Druck Zeichenfolge** , wie in der folgenden Abbildung dargestellt</span><span class="sxs-lookup"><span data-stu-id="be5e6-133">Drag and drop the **Pressed** pin to **Print String** node as shown in the image below.</span></span> <span data-ttu-id="be5e6-134">Sie können die **freigegebene** Pin leer lassen, ohne dass für sprach Zuordnungen etwas ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="be5e6-134">You can leave the **Released** pin empty, it won't execute anything for speech mappings.</span></span>
 
![Einfache Aktion für Stimme](images/unreal/voice-input-img-03.png)

4. <span data-ttu-id="be5e6-136">Spielen Sie die APP, sagen Sie das Wort **springt**, und sehen Sie sich an, dass die Konsole die Protokolle ausgibt.</span><span class="sxs-lookup"><span data-stu-id="be5e6-136">Play the app, say the word **jump**, and watch the console print out the logs!</span></span>

<span data-ttu-id="be5e6-137">Das ist alles, was Sie benötigen, um Ihren hololens-apps in Unreal Spracheingaben hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="be5e6-137">That's all the setup you'll need to start adding voice input to your HoloLens apps in Unreal.</span></span> <span data-ttu-id="be5e6-138">Weitere Informationen zu Sprache und Interaktivität finden Sie unter den folgenden Links, und Sie sollten sich über die Benutzeroberflächen Gedanken machen, die Sie für Ihre Benutzer erstellen.</span><span class="sxs-lookup"><span data-stu-id="be5e6-138">You can find more information on speech and interactivity at the links below, and be sure to think about the experience you're creating for your users.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="be5e6-139">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="be5e6-139">Next Development Checkpoint</span></span>

<span data-ttu-id="be5e6-140">Wenn Sie die unwirkliche Entwicklungs Journey befolgen, die wir festgelegt haben, haben Sie die nächste Aufgabe darin, die Funktionen und APIs der Mixed Reality-Plattform zu untersuchen:</span><span class="sxs-lookup"><span data-stu-id="be5e6-140">If you're following the Unreal development journey we've laid out, you're next task is exploring the Mixed Reality platform capabilities and APIs:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="be5e6-141">HoloLens-Kamera</span><span class="sxs-lookup"><span data-stu-id="be5e6-141">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="be5e6-142">Sie können jederzeit zu den [Prüfpunkten für die Unreal-Entwicklung](unreal-development-overview.md#2-core-building-blocks) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="be5e6-142">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="be5e6-143">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="be5e6-143">See also</span></span>
* [<span data-ttu-id="be5e6-144">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="be5e6-144">Voice Input</span></span>](../../design/voice-input.md)
* [<span data-ttu-id="be5e6-145">Anvisieren und Ausführen</span><span class="sxs-lookup"><span data-stu-id="be5e6-145">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="be5e6-146">Instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="be5e6-146">Instinctual interactions</span></span>](../../design/interaction-fundamentals.md)

