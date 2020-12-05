---
title: UMG und Tastatur in Unreal
description: Erfahren Sie, wie Sie unbereichbewegungs Grafiken verwenden, um ein UI-System aus Widgets zu erstellen.
author: hferrone
ms.author: suwu
ms.date: 11/25/2020
ms.topic: article
keywords: Windows Mixed Reality, holograms, hololens 2, Eye Tracking, Blick Eingaben, Head-eingebundene Anzeige, Unreal Engine, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Widgets, UI, Umschlag, unechte Bewegungsgrafiken, Unreal Engine, UE, UE4
ms.openlocfilehash: 59ad108a0e27298256f4f0d1661381a4f1748777
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609761"
---
# <a name="umg-and-keyboard-in-unreal"></a><span data-ttu-id="e3375-104">UMG und Tastatur in Unreal</span><span class="sxs-lookup"><span data-stu-id="e3375-104">UMG and keyboard in Unreal</span></span>

<span data-ttu-id="e3375-105">Unreal Motion Graphics (Umschlag) ist das integrierte UI-System von Unreal Engine, das zum Erstellen von Schnittstellen wie Menüs und Textfeldern verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="e3375-105">Unreal Motion Graphics (UMG) is Unreal Engine’s built-in UI system, used to create interfaces such as menus and text boxes.</span></span> <span data-ttu-id="e3375-106">Benutzeroberflächen, die mit "Umschlag" erstellt wurden, bestehen aus Widgets.</span><span class="sxs-lookup"><span data-stu-id="e3375-106">User interfaces built with UMG consist of widgets.</span></span> <span data-ttu-id="e3375-107">Wir führen Sie durch die Erstellung eines neuen Widgets, das Hinzufügen zu einem Welt Raum und das Aktivieren der Interaktion mithilfe der System Tastatur als Beispiel.</span><span class="sxs-lookup"><span data-stu-id="e3375-107">We'll guide you through creating a new widget, adding it to world space, and enabling interaction using the system keyboard as an example.</span></span> <span data-ttu-id="e3375-108">Weitere Informationen zu "gg" finden Sie in der offiziellen Unreal Engine- [Dokumentation](https://docs.unrealengine.com/en-US/Engine/UMG/index.html).</span><span class="sxs-lookup"><span data-stu-id="e3375-108">You can learn more about UMG in the official Unreal Engine [documentation](https://docs.unrealengine.com/en-US/Engine/UMG/index.html).</span></span> 

## <a name="create-a-new-widget"></a><span data-ttu-id="e3375-109">Neues Widget erstellen</span><span class="sxs-lookup"><span data-stu-id="e3375-109">Create a new widget</span></span>

- <span data-ttu-id="e3375-110">Erstellen Sie eine widgeblaupause, um die Benutzeroberfläche des Spiels zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="e3375-110">Create a Widget Blueprint to lay out the game’s UI:</span></span>

![Screenshot: Hinzufügen einer widgeblaupause aus dem Unreal-Menü](images/unreal-umg-img-01.png)

- <span data-ttu-id="e3375-112">Öffnen Sie den neuen Blueprint, und fügen Sie der Canvas Komponenten aus der Palette hinzu.</span><span class="sxs-lookup"><span data-stu-id="e3375-112">Open the new blueprint and add components from the Palette to the canvas.</span></span>  <span data-ttu-id="e3375-113">In diesem Fall haben wir zwei Text Feld Komponenten aus dem Abschnitt "Input" hinzugefügt:</span><span class="sxs-lookup"><span data-stu-id="e3375-113">In this case, we've added two Text Box components from the “Input” section:</span></span>

![Screenshot des Fensters "Hierarchie" mit hervorgehobener und erweiterter textwidget-Komponente](images/unreal-umg-img-02.png)

- <span data-ttu-id="e3375-115">Wählen Sie im Fenster Hierarchie oder Designer ein Widget aus, und ändern Sie die Parameter im Detail Panel.</span><span class="sxs-lookup"><span data-stu-id="e3375-115">Select a widget in the Hierarchy or Designer window and modify parameters in the details panel.</span></span>  <span data-ttu-id="e3375-116">In diesem Fall haben wir einige Standardwerte für "Hinweis Text" und eine Farben hinzugefügt, die angezeigt werden, wenn Sie mit dem Mauszeiger auf das Textfeld zeigen.</span><span class="sxs-lookup"><span data-stu-id="e3375-116">In this case, we’ve added some default “Hint Text” and a tint color that appears when you hover over the text box.</span></span>  <span data-ttu-id="e3375-117">In einem Textfeld wird eine virtuelle Tastatur auf hololens angezeigt, wenn Sie mit folgenden Aktionen interagiert:</span><span class="sxs-lookup"><span data-stu-id="e3375-117">A text box will pop up a virtual keyboard on HoloLens when it's interacted with:</span></span>

![Screenshot der geänderten Parameter im Hierarchie Fenster](images/unreal-umg-img-03.png)

- <span data-ttu-id="e3375-119">Ereignisse können auch im Detail Panel abonniert werden:</span><span class="sxs-lookup"><span data-stu-id="e3375-119">Events can also be subscribed to in the details panel:</span></span>

![Screenshot der Ereignisse im Detail Panel](images/unreal-umg-img-04.png)

## <a name="add-a-widget-to-world-space"></a><span data-ttu-id="e3375-121">Hinzufügen eines Widgets zum Raum</span><span class="sxs-lookup"><span data-stu-id="e3375-121">Add a Widget to World Space</span></span>

- <span data-ttu-id="e3375-122">Erstellen Sie einen neuen Actor, fügen Sie eine widgekomponente hinzu, und fügen Sie den Actor der Szene hinzu:</span><span class="sxs-lookup"><span data-stu-id="e3375-122">Create a new Actor, add a Widget component, and add the actor to the scene:</span></span>

![Screenshot eines Actors mit angefügtem widget](images/unreal-umg-img-05.png)

- <span data-ttu-id="e3375-124">Legen Sie im Detailbereich für das Widget die **Widget-Klasse** auf die zuvor erstellte widgeblaupause fest:</span><span class="sxs-lookup"><span data-stu-id="e3375-124">In the details panel for the Widget, set the **Widget Class** to the Widget Blueprint created earlier:</span></span>

![Screenshot des Bereichs "Blaupausen Details" mit der Widget-Klassensatz](images/unreal-umg-img-06.png)

- <span data-ttu-id="e3375-126">Vergewissern Sie sich bei einem textwidget, dass **Empfangs Hardware Eingabe** deaktiviert ist, sodass nur der zugehörige Text von der virtuellen Tastatur aktualisiert wird:</span><span class="sxs-lookup"><span data-stu-id="e3375-126">For a text Widget, ensure **Receive Hardware Input** is unchecked so we only update its text from the virtual keyboard:</span></span>

![Screenshot des Abschnitts "Interaktion" mit "Hardware Eingabe empfangen" ist nicht aktiviert](images/unreal-umg-img-07.png)

## <a name="widget-interaction"></a><span data-ttu-id="e3375-128">Widget-Interaktion</span><span class="sxs-lookup"><span data-stu-id="e3375-128">Widget Interaction</span></span>

<span data-ttu-id="e3375-129">In der Regel erhalten die-Widgets Eingaben von einer Maus.</span><span class="sxs-lookup"><span data-stu-id="e3375-129">UMG Widgets typically receive input from a mouse.</span></span>  <span data-ttu-id="e3375-130">Bei hololens oder VR müssen wir eine Maus mit einer Widget-Interaktions Komponente simulieren, um die gleichen Ereignisse zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="e3375-130">On HoloLens or VR, we need to simulate a mouse with a Widget Interaction component to get the same events.</span></span>

- <span data-ttu-id="e3375-131">Erstellen Sie einen neuen Actor, fügen Sie eine **Widget-Interaktions** Komponente hinzu, und fügen Sie den Actor Ihrer Szene hinzu:</span><span class="sxs-lookup"><span data-stu-id="e3375-131">Create a new Actor, add a **Widget Interaction** component, and add the actor to your scene:</span></span>

![Screenshot eines neuen Actors mit hervorgehobener Widget-Interaktions Komponente](images/unreal-umg-img-08.png)

- <span data-ttu-id="e3375-133">Im Detail Panel für die Widget-Interaktions Komponente:</span><span class="sxs-lookup"><span data-stu-id="e3375-133">In the details panel for the Widget Interaction component:</span></span>
    - <span data-ttu-id="e3375-134">Legen Sie die Interaktions Distanz auf den gewünschten Entfernungswert fest.</span><span class="sxs-lookup"><span data-stu-id="e3375-134">Set the interaction distance to the distance value you want</span></span>
    - <span data-ttu-id="e3375-135">Legen Sie die **Interaktions Quelle** auf **Custom** fest.</span><span class="sxs-lookup"><span data-stu-id="e3375-135">Set the **Interaction Source** to **custom**</span></span>
    - <span data-ttu-id="e3375-136">Legen Sie für die Entwicklung die Einstellung **Debug anzeigen** auf **true** fest:</span><span class="sxs-lookup"><span data-stu-id="e3375-136">For development, set **Show Debug** to **true**:</span></span>

![Screenshot der Eigenschaften der Widget-Interaktion und Debugkomponente](images/unreal-umg-img-09.png)

<span data-ttu-id="e3375-138">Der Standardwert für die Interaktions Quelle ist "World", der Raycasts basierend auf der Weltposition der Widget-Interaktions Komponente senden soll.</span><span class="sxs-lookup"><span data-stu-id="e3375-138">The default for Interaction Source is “World”, which should send raycasts based on the world position of the Widget Interaction component.</span></span> <span data-ttu-id="e3375-139">In AR und VR ist das nicht der Fall.</span><span class="sxs-lookup"><span data-stu-id="e3375-139">In AR and VR, that's not the case.</span></span>  <span data-ttu-id="e3375-140">Das Aktivieren von "Debuggen anzeigen" und das Hinzufügen eines Hover-tints zu Widgets ist wichtig, um zu überprüfen, ob die Komponente für die Widget-Interaktion</span><span class="sxs-lookup"><span data-stu-id="e3375-140">Enabling “Show Debug” and adding a hover tint to widgets is important to check the widget interaction component is doing what you expect.</span></span>  <span data-ttu-id="e3375-141">Die Problem Umgehung besteht darin, eine benutzerdefinierte Quelle zu verwenden und den raycast aus dem Hand Strahl im Ereignis Diagramm festzulegen.</span><span class="sxs-lookup"><span data-stu-id="e3375-141">The workaround is to use a custom source and set the raycast in the event graph from the hand ray.</span></span>  

<span data-ttu-id="e3375-142">Hier rufen wir dies von der Ereignis Tick-Methode auf:</span><span class="sxs-lookup"><span data-stu-id="e3375-142">Here we're calling this from Event Tick:</span></span>

![Blaupause von Ereignis Tick](images/unreal-umg-img-10.png)

<span data-ttu-id="e3375-144">Fügen Sie dann der Widget-Interaktions Komponente Ereignisse für virtuelle Mauszeiger hinzu, die auf hololens-Eingaben reagieren.</span><span class="sxs-lookup"><span data-stu-id="e3375-144">Then add virtual mouse pointer events to the widget interaction component reacting to HoloLens input.</span></span>  <span data-ttu-id="e3375-145">Senden Sie in diesem Fall ein linkes mousepress-Ereignis, wenn die Hand erfasst wird, und ein linkes mousereleaseereignis, wenn es nicht verstanden wird:</span><span class="sxs-lookup"><span data-stu-id="e3375-145">In this case, send a Left Mouse press event when the hand is grasped, and a Left Mouse release event when not grasped:</span></span>

![Blaupause mit hinzugefügten Ereignissen für virtuelle Mauszeiger](images/unreal-umg-img-13.png)

<span data-ttu-id="e3375-147">Wenn Sie die App nun in den hololens 2 bereitstellen, wird ein Hand Strahl angezeigt, der von der rechten Seite aus erweitert wird.</span><span class="sxs-lookup"><span data-stu-id="e3375-147">Now, when you deploy the app to the HoloLens 2, you’ll see a hand ray extending from your right hand.</span></span> <span data-ttu-id="e3375-148">Wenn Sie den Text in einem der bearbeitbaren Textfelder und der Luft tippen, wird die Tastatur des Systems vor Ihnen angezeigt, und Sie können Text eingeben.</span><span class="sxs-lookup"><span data-stu-id="e3375-148">If you direct it at one of the editable text boxes and air tap, the system keyboard will appear in front of you and allow you to enter text.</span></span> 
 
> [!NOTE]
> <span data-ttu-id="e3375-149">Die hololens-System Tastatur erfordert Unreal Engine 4,26 oder höher.</span><span class="sxs-lookup"><span data-stu-id="e3375-149">The HoloLens system keyboard requires Unreal Engine 4.26 or later.</span></span> <span data-ttu-id="e3375-150">Außerdem wird die Tastatur nicht angezeigt, wenn Ihre APP aus dem Unreal-Editor nicht an das Headset gestreamt wird, sondern nur, wenn die APP auf dem Gerät ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="e3375-150">Additionally, the keyboard will not appear when your app is being streamed from the Unreal editor to the headset, only when the app is running on device.</span></span>

## <a name="see-also"></a><span data-ttu-id="e3375-151">Siehe auch:</span><span class="sxs-lookup"><span data-stu-id="e3375-151">See Also:</span></span>
* [<span data-ttu-id="e3375-152">Die-um-Dokumentation zu Unreal</span><span class="sxs-lookup"><span data-stu-id="e3375-152">Unreal's UMG documentation</span></span>](https://docs.unrealengine.com/Engine/UMG/index.html)
* [<span data-ttu-id="e3375-153">"Ung"-Tutorials von Unreal</span><span class="sxs-lookup"><span data-stu-id="e3375-153">Unreal's UMG tutorials</span></span>](https://docs.unrealengine.com/Programming/Tutorials/UMG/index.html)
