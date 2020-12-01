---
title: Umschlag und Tastatur in Unreal
description: Erfahren Sie, wie Sie unbereichbewegungs Grafiken verwenden, um ein UI-System aus Widgets zu erstellen.
author: hferrone
ms.author: suwu
ms.date: 11/25/2020
ms.topic: article
keywords: Windows Mixed Reality, holograms, hololens 2, Eye Tracking, Blick Eingaben, Head-eingebundene Anzeige, Unreal Engine, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Widgets, UI, Umschlag, unechte Bewegungsgrafiken, Unreal Engine, UE, UE4
ms.openlocfilehash: 9f22a5f7a13732727b6b122d385aad7e708a1343
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2020
ms.locfileid: "96355320"
---
# <a name="umg-and-keyboard-in-unreal"></a><span data-ttu-id="2e2a9-104">Umschlag und Tastatur in Unreal</span><span class="sxs-lookup"><span data-stu-id="2e2a9-104">UMG and keyboard in Unreal</span></span>

<span data-ttu-id="2e2a9-105">Unreal Motion Graphics (Umschlag) ist das integrierte UI-System von Unreal Engine, das zum Erstellen von Schnittstellen wie Menüs und Textfeldern verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="2e2a9-105">Unreal Motion Graphics (UMG) is Unreal Engine’s built-in UI system, used to create interfaces such as menus and text boxes.</span></span> <span data-ttu-id="2e2a9-106">Benutzeroberflächen, die mit "Umschlag" erstellt wurden, bestehen aus Widgets.</span><span class="sxs-lookup"><span data-stu-id="2e2a9-106">User interfaces built with UMG consist of widgets.</span></span> <span data-ttu-id="2e2a9-107">In dieser Anleitung erfahren Sie, wie Sie ein neues Widget erstellen, es dem Raum hinzufügen und die Interaktion mit diesem Widget in gemischter Realität aktivieren. verwenden Sie dazu die System Tastatur als Beispiel.</span><span class="sxs-lookup"><span data-stu-id="2e2a9-107">This guide will show you how to create a new widget, add it to world space, and enable interaction with that widget in mixed reality, using the system keyboard as an example.</span></span> <span data-ttu-id="2e2a9-108">Weitere Informationen zu "gg" finden Sie in der offiziellen Unreal Engine- [Dokumentation](https://docs.unrealengine.com/en-US/Engine/UMG/index.html).</span><span class="sxs-lookup"><span data-stu-id="2e2a9-108">You can learn more about UMG in the official Unreal Engine [documentation](https://docs.unrealengine.com/en-US/Engine/UMG/index.html).</span></span> 

## <a name="create-a-new-widget"></a><span data-ttu-id="2e2a9-109">Neues Widget erstellen</span><span class="sxs-lookup"><span data-stu-id="2e2a9-109">Create a new widget</span></span>

- <span data-ttu-id="2e2a9-110">Erstellen Sie eine widgeblaupause, um die Benutzeroberfläche des Spiels zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="2e2a9-110">Create a Widget Blueprint to lay out the game’s UI:</span></span>

![Screenshot: Hinzufügen einer widgeblaupause aus dem Unreal-Menü](images/unreal-umg-img-01.png)

- <span data-ttu-id="2e2a9-112">Öffnen Sie den neuen Blueprint, und fügen Sie der Canvas Komponenten aus der Palette hinzu.</span><span class="sxs-lookup"><span data-stu-id="2e2a9-112">Open the new blueprint and add components from the Palette to the canvas.</span></span>  <span data-ttu-id="2e2a9-113">In diesem Fall haben wir zwei Textfeld-Komponenten aus dem Abschnitt "Input" hinzugefügt:</span><span class="sxs-lookup"><span data-stu-id="2e2a9-113">In this case we have added two Text Box components from the “Input” section:</span></span>

![Screenshot des Fensters "Hierarchie" mit hervorgehobener und erweiterter textwidget-Komponente](images/unreal-umg-img-02.png)

- <span data-ttu-id="2e2a9-115">Wählen Sie im Fenster Hierarchie oder Designer ein Widget aus, und ändern Sie die Parameter im Detail Panel.</span><span class="sxs-lookup"><span data-stu-id="2e2a9-115">Select a widget in the Hierarchy or Designer window and modify parameters in the details panel.</span></span>  <span data-ttu-id="2e2a9-116">In diesem Fall haben wir einige Standardwerte für "Hinweis Text" und eine Farben hinzugefügt, wenn der Cursor über das Textfeld bewegt wird, um Feedback zu geben, mit dem das Widget interagiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="2e2a9-116">In this case, we’ve added some default “Hint Text” and a tint color when the cursor is hovering over the text box to give feedback that the widget is ready to be interacted with.</span></span>  <span data-ttu-id="2e2a9-117">In einem Textfeld wird eine virtuelle Tastatur auf hololens angezeigt, wenn Sie mit folgenden Aktionen interagiert:</span><span class="sxs-lookup"><span data-stu-id="2e2a9-117">A text box will pop up a virtual keyboard on HoloLens when it is interacted with:</span></span>

![Screenshot der geänderten Parameter im Hierarchie Fenster](images/unreal-umg-img-03.png)

- <span data-ttu-id="2e2a9-119">Ereignisse können auch im Detail Panel abonniert werden:</span><span class="sxs-lookup"><span data-stu-id="2e2a9-119">Events can also be subscribed to in the details panel:</span></span>

![Screenshot der Ereignisse im Detail Panel](images/unreal-umg-img-04.png)

## <a name="add-a-widget-to-world-space"></a><span data-ttu-id="2e2a9-121">Hinzufügen eines Widgets zum Raum</span><span class="sxs-lookup"><span data-stu-id="2e2a9-121">Add a Widget to World Space</span></span>

- <span data-ttu-id="2e2a9-122">Erstellen Sie einen neuen Actor, fügen Sie eine widgekomponente hinzu, und fügen Sie den Actor der Szene hinzu:</span><span class="sxs-lookup"><span data-stu-id="2e2a9-122">Create a new Actor, add a Widget component, and add the actor to the scene:</span></span>

![Screenshot eines Actors mit angefügtem widget](images/unreal-umg-img-05.png)

- <span data-ttu-id="2e2a9-124">Legen Sie im Detailbereich für das Widget die **Widget-Klasse** auf die zuvor erstellte widgeblaupause fest:</span><span class="sxs-lookup"><span data-stu-id="2e2a9-124">In the details panel for the Widget, set the **Widget Class** to the Widget Blueprint created earlier:</span></span>

![Screenshot des Bereichs "Blaupausen Details" mit der Widget-Klassensatz](images/unreal-umg-img-06.png)

- <span data-ttu-id="2e2a9-126">Vergewissern Sie sich bei einem textwidget, dass **Empfangs Hardware Eingabe** deaktiviert ist, sodass nur der zugehörige Text von der virtuellen Tastatur aktualisiert wird:</span><span class="sxs-lookup"><span data-stu-id="2e2a9-126">For a text Widget, ensure **Receive Hardware Input** is unchecked so we only update its text from the virtual keyboard:</span></span>

![Screenshot des Abschnitts "Interaktion" mit "Hardware Eingabe empfangen" ist nicht aktiviert](images/unreal-umg-img-07.png)

## <a name="widget-interaction"></a><span data-ttu-id="2e2a9-128">Widget-Interaktion</span><span class="sxs-lookup"><span data-stu-id="2e2a9-128">Widget Interaction</span></span>

<span data-ttu-id="2e2a9-129">In der Regel erhalten die-Widgets Eingaben von einer Maus.</span><span class="sxs-lookup"><span data-stu-id="2e2a9-129">UMG Widgets typically receive input from a mouse.</span></span>  <span data-ttu-id="2e2a9-130">Bei hololens oder VR müssen wir eine Maus mit einer Widget-Interaktions Komponente simulieren, um die gleichen Ereignisse zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="2e2a9-130">On HoloLens or VR, we need to simulate a mouse with a Widget Interaction component to get the same events.</span></span>

- <span data-ttu-id="2e2a9-131">Erstellen Sie einen neuen Actor, fügen Sie eine **Widget-Interaktions** Komponente hinzu, und fügen Sie den Actor Ihrer Szene hinzu:</span><span class="sxs-lookup"><span data-stu-id="2e2a9-131">Create a new Actor, add a **Widget Interaction** component, and add the actor to your scene:</span></span>

![Screenshot eines neuen Actors mit hervorgehobener Widget-Interaktions Komponente](images/unreal-umg-img-08.png)

- <span data-ttu-id="2e2a9-133">Legen Sie im Detailbereich für die Komponente für die Widget-Interaktion die Interaktions Entfernung auf den gewünschten Abstand fest, legen Sie die **Interaktions Quelle** auf **Custom** fest, und legen Sie für Entwicklung die Option **Debuggen anzeigen** auf **true** fest:</span><span class="sxs-lookup"><span data-stu-id="2e2a9-133">In the details panel for the Widget Interaction component, set the interaction distance to the desired distance, set the **Interaction Source** to **custom**, and for development, set **Show Debug** to **true**:</span></span>

![Screenshot der Eigenschaften der Widget-Interaktion und Debugkomponente](images/unreal-umg-img-09.png)

<span data-ttu-id="2e2a9-135">Der Standardwert für die Interaktions Quelle ist "World", der Raycasts basierend auf der Weltposition der Widget-Interaktions Komponente senden sollte, aber in AR und VR scheint dies nicht der Fall zu sein.</span><span class="sxs-lookup"><span data-stu-id="2e2a9-135">The default for Interaction Source is “World”, which should send raycasts based on the world position of the Widget Interaction component, but in AR and VR this does not appear to be the case.</span></span>  <span data-ttu-id="2e2a9-136">Das Aktivieren von "Debuggen anzeigen" und das Hinzufügen eines Hover-tints zu Widgets während der Entwicklung ist wichtig, um zu prüfen, ob die Komponente für die Widget-Interaktion das erwartete Verhalten</span><span class="sxs-lookup"><span data-stu-id="2e2a9-136">Enabling “Show Debug” and adding a hover tint to widgets while developing is important to sanity check the widget interaction component is doing what you expect.</span></span>  <span data-ttu-id="2e2a9-137">Die Problem Umgehung besteht darin, eine benutzerdefinierte Quelle zu verwenden und den raycast aus dem Hand Strahl im Ereignis Diagramm festzulegen.</span><span class="sxs-lookup"><span data-stu-id="2e2a9-137">The workaround is to use a custom source and set the raycast in the event graph from the hand ray.</span></span>  

<span data-ttu-id="2e2a9-138">Hier rufen wir dies aus dem Ereignis Takt auf:</span><span class="sxs-lookup"><span data-stu-id="2e2a9-138">Here we are calling this from Event Tick:</span></span>

![Blaupause von Ereignis Tick](images/unreal-umg-img-10.png)

<span data-ttu-id="2e2a9-140">Fügen Sie dann der Widget-Interaktions Komponente Ereignisse für virtuelle Mauszeiger hinzu, die auf hololens-Eingaben reagieren.</span><span class="sxs-lookup"><span data-stu-id="2e2a9-140">Then add virtual mouse pointer events to the widget interaction component reacting to HoloLens input.</span></span>  <span data-ttu-id="2e2a9-141">Senden Sie in diesem Fall ein linkes mousepress-Ereignis, wenn die Hand erfasst wird, und ein linkes mousereleaseereignis, wenn es nicht verstanden wird:</span><span class="sxs-lookup"><span data-stu-id="2e2a9-141">In this case, send a Left Mouse press event when the hand is grasped, and a Left Mouse release event when not grasped:</span></span>

![Blaupause mit hinzugefügten Ereignissen für virtuelle Mauszeiger](images/unreal-umg-img-13.png)

<span data-ttu-id="2e2a9-143">Wenn Sie die App nun in den hololens 2 bereitstellen, wird ein Hand Strahl angezeigt, der von der rechten Seite aus erweitert wird.</span><span class="sxs-lookup"><span data-stu-id="2e2a9-143">Now, when you deploy the app to the HoloLens 2, you’ll see a hand ray extending from your right hand.</span></span> <span data-ttu-id="2e2a9-144">Wenn Sie den Text in einem der bearbeitbaren Textfelder und der Luft tippen, wird die Tastatur des Systems vor Ihnen angezeigt, und Sie können Text eingeben.</span><span class="sxs-lookup"><span data-stu-id="2e2a9-144">If you direct it at one of the editable text boxes and air tap, the system keyboard will appear in front of you and allow you to enter text.</span></span> 
 
> [!NOTE]
> <span data-ttu-id="2e2a9-145">Die hololens-System Tastatur erfordert Unreal Engine 4,26 oder höher.</span><span class="sxs-lookup"><span data-stu-id="2e2a9-145">The HoloLens system keyboard requires Unreal Engine 4.26 or later.</span></span> <span data-ttu-id="2e2a9-146">Außerdem wird die Tastatur nicht angezeigt, wenn Ihre APP aus dem Unreal-Editor nicht an das Headset gestreamt wird, sondern nur, wenn die APP auf dem Gerät ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="2e2a9-146">Additionally, the keyboard will not appear when your app is being streamed from the Unreal editor to the headset, only when the app is running on device.</span></span>

## <a name="see-also"></a><span data-ttu-id="2e2a9-147">Siehe auch:</span><span class="sxs-lookup"><span data-stu-id="2e2a9-147">See Also:</span></span>
* [<span data-ttu-id="2e2a9-148">Die-um-Dokumentation zu Unreal</span><span class="sxs-lookup"><span data-stu-id="2e2a9-148">Unreal's UMG documentation</span></span>](https://docs.unrealengine.com/Engine/UMG/index.html)
* [<span data-ttu-id="2e2a9-149">"Ung"-Tutorials von Unreal</span><span class="sxs-lookup"><span data-stu-id="2e2a9-149">Unreal's UMG tutorials</span></span>](https://docs.unrealengine.com/Programming/Tutorials/UMG/index.html)
