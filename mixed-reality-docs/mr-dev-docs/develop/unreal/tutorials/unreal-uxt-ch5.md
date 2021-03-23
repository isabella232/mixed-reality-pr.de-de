---
title: 5. Hinzufügen einer Taste und Zurücksetzen von Figurenpositionen
description: Teil 5 von 6 einer Tutorialreihe zum Erstellen einer Schach-App mit der Unreal Engine 4 und dem UX Tools-Plug-In des Mixed Reality-Toolkits
author: hferrone
ms.author: v-hferrone
ms.date: 11/18/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Tutorial, Erste Schritte, MRTK, UXT, UX-Tools, Dokumentation, Mixed Reality-Headset Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 8e16865e89c06c37f2932f1828bf8ca5551e6fce
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2021
ms.locfileid: "96609691"
---
# <a name="5-adding-a-button--resetting-piece-locations"></a><span data-ttu-id="720be-104">5. Hinzufügen einer Taste und Zurücksetzen von Figurenpositionen</span><span class="sxs-lookup"><span data-stu-id="720be-104">5. Adding a button & resetting piece locations</span></span>

<span data-ttu-id="720be-105">Im vorhergehenden Tutorial haben Sie den Pawn- und Manipulatorkomponenten Handinteraktionsakteure auf dem Schachbrett hinzugefügt, um eine Interaktion zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="720be-105">In the previous tutorial, you added Hand Interaction Actors to the Pawn and Manipulator components to the chess board to make them both interactive.</span></span> <span data-ttu-id="720be-106">In diesem Abschnitt verwenden Sie weiterhin das UX-Tools-Plug-In des Mixed Reality Toolkit, um Ihre Schach-App um neue Funktionen sowie Akteurverweisen in Blaupausen zu erweitern.</span><span class="sxs-lookup"><span data-stu-id="720be-106">In this section, you'll continue to use the Mixed Reality Toolkit UX Tools plugin to build out your chess app with new functions and Actor references in Blueprints.</span></span> <span data-ttu-id="720be-107">Am Ende dieses Abschnitts können Sie die Mixed Reality-App verpacken und auf einem Gerät oder in einem Emulator bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="720be-107">By the end of this section, you'll be ready to package and deploy the mixed reality app on a device or emulator.</span></span>

## <a name="objectives"></a><span data-ttu-id="720be-108">Ziele</span><span class="sxs-lookup"><span data-stu-id="720be-108">Objectives</span></span>

* <span data-ttu-id="720be-109">Hinzufügen einer interaktiven Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="720be-109">Adding an interactive button</span></span>
* <span data-ttu-id="720be-110">Erstellen einer Funktion zum Zurücksetzen der Position der Figuren</span><span class="sxs-lookup"><span data-stu-id="720be-110">Creating a function to reset a pieces' location</span></span>
* <span data-ttu-id="720be-111">Verknüpfen der Schaltfläche, damit die Funktion beim Tippen auf die Schaltfläche ausgelöst wird</span><span class="sxs-lookup"><span data-stu-id="720be-111">Hooking the button up to trigger the function when pressed</span></span>

## <a name="creating-a-reset-function"></a><span data-ttu-id="720be-112">Erstellen einer Funktion zum Zurücksetzen</span><span class="sxs-lookup"><span data-stu-id="720be-112">Creating a reset function</span></span>

<span data-ttu-id="720be-113">Ihre erste Aufgabe besteht darin, eine Funktionsblaupause zu erstellen, mit der die Position einer Schachfigur auf die ursprüngliche Position in der Szene zurückgesetzt wird.</span><span class="sxs-lookup"><span data-stu-id="720be-113">Your first task is to create a function blueprint that resets a chess piece to its original position in the scene.</span></span>

1.  <span data-ttu-id="720be-114">Öffnen Sie **WhiteKing**, wählen Sie das Symbol **+** unter **My Blueprint** (Meine Blaupause) neben dem Abschnitt **Functions** (Funktionen) aus, und geben Sie ihr den Namen **Reset Location** (Position zurücksetzen).</span><span class="sxs-lookup"><span data-stu-id="720be-114">Open **WhiteKing**, select the **+** icon next to the **Functions** section in the **My Blueprint** and name it **Reset Location**.</span></span>

2.  <span data-ttu-id="720be-115">Ziehen Sie die Ausführung aus **Reset Location** auf das Blaupausenraster, um den Knoten **SetActorRelativeTransform** zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="720be-115">Drag and release the execution from **Reset Location** on the Blueprint grid to create a **SetActorRelativeTransform** node.</span></span>
    * <span data-ttu-id="720be-116">Durch diese Funktion wird die Transformation (Position, Rotation und Skalierung) eines Akteurs relativ zum übergeordneten Element festgelegt.</span><span class="sxs-lookup"><span data-stu-id="720be-116">This function sets the transform (location, rotation, and scale) of an actor relative to its parent.</span></span> <span data-ttu-id="720be-117">Sie verwenden diese Funktion, um die Position des Königs auf dem Schachbrett zurückzusetzen, auch wenn sich dieses nicht mehr an seiner ursprünglichen Position befindet.</span><span class="sxs-lookup"><span data-stu-id="720be-117">You’ll use this function to reset the king’s position on the board, even if the board has been moved from its original position.</span></span>

3. <span data-ttu-id="720be-118">Klicken Sie mit der rechten Maustaste auf eine Stelle im Ereignisdiagramm, wählen Sie **Make Transform** (Transformation erstellen) aus, und ändern Sie **Location** (Position) in **X = -26**, **Y = 4**, **Z = 0**.</span><span class="sxs-lookup"><span data-stu-id="720be-118">Right-click inside the Event Graph, select **Make Transform**, and change its **Location** to **X = -26**, **Y = 4**, **Z = 0**.</span></span>
    * <span data-ttu-id="720be-119">Verbinden Sie **Return Value** (Rückgabewert) mit dem Pin **New Relative Transform** (Neue relative Transformation) in **SetActorRelativeTransform**.</span><span class="sxs-lookup"><span data-stu-id="720be-119">Connect its **Return Value** to the **New Relative Transform** pin in **SetActorRelativeTransform**.</span></span>

![Funktion zum Zurücksetzen der Position](images/unreal-uxt/5-function.PNG)

<span data-ttu-id="720be-121">**Kompilieren** und **speichern** Sie das Projekt, bevor Sie zum Hauptfenster zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="720be-121">**Compile** and **Save** the project before returning to the Main window.</span></span>


## <a name="adding-a-button"></a><span data-ttu-id="720be-122">Hinzufügen einer Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="720be-122">Adding a button</span></span>

<span data-ttu-id="720be-123">Nachdem die Funktion nun ordnungsgemäß eingerichtet wurde, besteht die nächste Aufgabe darin, eine Schaltfläche zu erstellen, die ausgelöst wird, sobald sie berührt wird.</span><span class="sxs-lookup"><span data-stu-id="720be-123">Now that the function is set up correctly, your next task is to create a button that fires it off when touched.</span></span>

1.  <span data-ttu-id="720be-124">Klicken Sie auf **Add New > Blueprint Class** (Neu hinzufügen > Blaupausenklasse), erweitern Sie den Abschnitt **All Classes** (Alle Klassen), und suchen Sie nach **UxtPressableButtonActor**.</span><span class="sxs-lookup"><span data-stu-id="720be-124">Click **Add New > Blueprint Class**, expand the **All Classes** section, and search for **UxtPressableButtonActor**.</span></span>
    * <span data-ttu-id="720be-125">Geben Sie Ihr den Namen **ResetButton**, und doppelklicken Sie darauf, um die Blaupause zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="720be-125">Name it **ResetButton** and double click to open the Blueprint</span></span>

![Erstellen Sie die neue Blaupause als Unterklasse der HoloLens 2-Formatvorlagen-Schaltfläche](images/unreal-uxt/5-subclass.PNG)

2. <span data-ttu-id="720be-127">Vergewissern Sie sich, dass **ResetButton(self)** im Bereich **Komponenten** ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="720be-127">Ensure **ResetButton(self)** is selected in the **Components** panel.</span></span> <span data-ttu-id="720be-128">Navigieren Sie im Bereich **Details** zum Abschnitt **Button** (Schaltfläche).</span><span class="sxs-lookup"><span data-stu-id="720be-128">In the **Details** panel, navigate to the **Button** section.</span></span> <span data-ttu-id="720be-129">Ändern Sie das standardmäßige **Button Label** (Schaltflächenbezeichnung), erweitern Sie den Abschnitt **Schaltflächen-Symbolpinsel**, und drücken Sie die Schaltfläche **Open Icon Brush Editor** (Symbolpinsel-Editor öffnen).</span><span class="sxs-lookup"><span data-stu-id="720be-129">Change the default **Button Label** to "Reset", expand the **Button Icon Brush** section, and press the **Open Icon Brush Editor** button.</span></span>

![Festlegen von Bezeichnung und Symbol für die Schaltfläche](images/unreal-uxt/5-buttonconfig.PNG)

<span data-ttu-id="720be-131">Der Symbolpinsel-Editor wird geöffnet. Mit diesem können Sie ein neues Symbol für Ihre Schaltfläche auswählen.</span><span class="sxs-lookup"><span data-stu-id="720be-131">The Icon Brush Editor will open, which you can use to select a new icon for your button.</span></span>

![Auswählen eines Symbols für die Schaltfläche](images/unreal-uxt/5-iconbrusheditor.PNG)

<span data-ttu-id="720be-133">Es gibt zahlreiche weitere Einstellungen, die Sie anpassen können, um Ihre Schaltfläche zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="720be-133">There are plenty of other settings you can adjust to configure your button.</span></span> <span data-ttu-id="720be-134">Weitere Informationen über die UXT-Komponente „Drückbare Schaltfläche“ finden Sie in der [Dokumentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/PressableButton.html).</span><span class="sxs-lookup"><span data-stu-id="720be-134">To learn more about the UXT Pressable Button component, check out the [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/PressableButton.html).</span></span>

3. <span data-ttu-id="720be-135">Klicken Sie im Bereich **Komponenten** auf **ButtonComponent (Inherited)** (ButtonComponent (Geerbt)), und scrollen Sie im Bereich **Details** zum Abschnitt **Events** (Ereignisse).</span><span class="sxs-lookup"><span data-stu-id="720be-135">Click **ButtonComponent (Inherited)** in the **Components** panel and scroll down the **Details** panel to the **Events** section.</span></span>
    * <span data-ttu-id="720be-136">Klicken Sie neben **On Button Pressed** (Beim Drücken der Schaltfläche) auf das grüne **+** , um dem Ereignisdiagramm ein Ereignis hinzuzufügen, das aufgerufen wird, wenn die Schaltfläche betätigt wird.</span><span class="sxs-lookup"><span data-stu-id="720be-136">Click the green **+** button next to **On Button Pressed** to add an event to the Event Graph, which will be called when the button is pressed.</span></span>

<span data-ttu-id="720be-137">Hier soll die Funktion **Reset Location** für **WhiteKing** aufgerufen werden. Dazu ist ein Verweis auf den Akteur **WhiteKing** im Level erforderlich.</span><span class="sxs-lookup"><span data-stu-id="720be-137">From here, you’ll want to call **WhiteKing**’s **Reset Location** function, which needs a reference to the **WhiteKing** Actor in the Level.</span></span>

4.  <span data-ttu-id="720be-138">Navigieren Sie im Bereich **My Blueprint** (Meine Blaupause) zum Abschnitt **Variables** (Variablen), klicken Sie auf die Schaltfläche **+** , und geben Sie der Variablen den Namen **WhiteKing**.</span><span class="sxs-lookup"><span data-stu-id="720be-138">In the **My Blueprint** panel, navigate to the **Variables** section, click the **+** button, and name the variable **WhiteKing**.</span></span>
    * <span data-ttu-id="720be-139">Wählen Sie im Bereich **Details** die Dropdownliste neben **Variable Type** (Variablentyp) aus, suchen Sie nach **WhiteKing**, und wählen Sie **Object Reference** (Objektverweis) aus.</span><span class="sxs-lookup"><span data-stu-id="720be-139">In the **Details** panel, select the dropdown next to **Variable Type**, search for **WhiteKing**, and select the **Object Reference**.</span></span>
    * <span data-ttu-id="720be-140">Aktivieren Sie das Kontrollkästchen neben **Instanz bearbeitbar**, sodass die Variable auf dem Hauptlevel festgelegt werden kann.</span><span class="sxs-lookup"><span data-stu-id="720be-140">Check the box next to **Instance Editable**, which allows the variable to be set from the Main Level.</span></span>

![Erstellen einer Variablen](images/unreal-uxt/5-var.PNG)

5.  <span data-ttu-id="720be-142">Ziehen Sie die Variable „WhiteKing“ aus **My Blueprint > Variables** (Meine Blaupause > Variablen) auf das Ereignisdiagramm für die Schaltfläche „Reset“, und wählen Sie **Get WhiteKing** aus.</span><span class="sxs-lookup"><span data-stu-id="720be-142">Drag the WhiteKing variable from **My Blueprint > Variables** onto the Reset Button Event Graph and choose **Get WhiteKing**.</span></span>

## <a name="firing-the-function"></a><span data-ttu-id="720be-143">Auslösen der Funktion</span><span class="sxs-lookup"><span data-stu-id="720be-143">Firing the function</span></span>

<span data-ttu-id="720be-144">Jetzt muss nur noch die Funktion zum Zurücksetzen ausgelöst werden, wenn die Schaltfläche betätigt wird.</span><span class="sxs-lookup"><span data-stu-id="720be-144">All that's left is to officially fire off the reset function when the button is pressed.</span></span>

1.  <span data-ttu-id="720be-145">Ziehen Sie den Ausgabepin von „WhiteKing“, und lassen Sie ihn los, um einen neuen Knoten zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="720be-145">Drag the WhiteKing output pin and release to place a new node.</span></span> <span data-ttu-id="720be-146">Wählen Sie die Funktion **Reset Location** (Position zurücksetzen) aus.</span><span class="sxs-lookup"><span data-stu-id="720be-146">Select the **Reset Location** function.</span></span> <span data-ttu-id="720be-147">Ziehen Sie abschließend den ausgehenden Ausführungspin von **On Button Pressed** (Beim Drücken des Schalters) zum eingehenden Ausführungspin von **Reset Location** (Position zurücksetzen).</span><span class="sxs-lookup"><span data-stu-id="720be-147">Finally, drag the outgoing execution pin from **On Button Pressed** to the incoming execution pin on **Reset Location**.</span></span> <span data-ttu-id="720be-148">**Kompilieren** und **speichern** Sie die Blaupause „ResetButton“, und kehren Sie anschließend zum Hauptfenster zurück.</span><span class="sxs-lookup"><span data-stu-id="720be-148">**Compile** and **Save** the ResetButton Blueprint, then return to the Main window.</span></span>

![Aufrufen der Funktion zum Zurücksetzen der Position über „On Button Pressed“ (Beim Drücken des Schalters)](images/unreal-uxt/5-callresetloc.PNG)

2.  <span data-ttu-id="720be-150">Ziehen Sie **ResetButton** in den Viewport, und legen Sie die Position auf **X = 50**, **Y = -25** und **Z = 10** fest.</span><span class="sxs-lookup"><span data-stu-id="720be-150">Drag **ResetButton** into the viewport and set its location to **X = 50**, **Y = -25**, and **Z = 10**.</span></span> <span data-ttu-id="720be-151">Legen Sie die Drehung auf **Z = 180** fest.</span><span class="sxs-lookup"><span data-stu-id="720be-151">Set its rotation to **Z = 180**.</span></span> <span data-ttu-id="720be-152">Legen Sie unter **Default** (Standard) den Wert der Variablen **WhiteKing** auf **WhiteKing** fest.</span><span class="sxs-lookup"><span data-stu-id="720be-152">Under **Default**, set the value of the **WhiteKing** variable to **WhiteKing**.</span></span>

![Festlegen der Variablen](images/unreal-uxt/5-buttonlevel.PNG)

<span data-ttu-id="720be-154">Führen Sie die App aus, verschieben Sie die Schachfigur an eine neue Position, und tippen Sie auf Ihre Schaltfläche im HoloLens 2-Stil, um die Logik zum Zurücksetzen auszuführen.</span><span class="sxs-lookup"><span data-stu-id="720be-154">Run the app, move the chess piece to a new location, and press your HoloLens 2-style button to see the reset logic in action!</span></span>

<span data-ttu-id="720be-155">Sie verfügen nun über eine Mixed Reality-App mit einer interaktionsfähigen Schachfigur und einem interaktionsfähigen Schachbrett sowie mit einer funktionsfähigen Schaltfläche, die die Position der Schachfigur zurücksetzt.</span><span class="sxs-lookup"><span data-stu-id="720be-155">You now have a mixed reality app with an interactable chess piece and board, and a fully functioning button that resets the piece’s location.</span></span> <span data-ttu-id="720be-156">Die bis hier hin fertige App finden Sie im [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp)-Repository.</span><span class="sxs-lookup"><span data-stu-id="720be-156">You can find the completed app up to this point in its [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp) repo.</span></span> <span data-ttu-id="720be-157">Sie können gerne noch einen Schritt weitergehen und die restlichen Schachfiguren einrichten, sodass das gesamte Schachbrett zurückgesetzt wird, wenn die Schaltfläche zum Zurücksetzen betätigen.</span><span class="sxs-lookup"><span data-stu-id="720be-157">Feel free to go beyond this tutorial and set up the rest of the chess pieces so that the entire board is reset when you press the reset button.</span></span>

![Fertige Szene im Viewport](images/unreal-uxt/5-endscene.PNG)

<span data-ttu-id="720be-159">Sie können nun mit dem letzten Abschnitt dieses Tutorials fortfahren, in dem Sie erfahren, wie Sie die App verpacken und auf einem Gerät oder in einem Emulator bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="720be-159">You're ready to move on to the final section of this tutorial where you'll learn how to package and deploy the app to a device or emulator.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="720be-160">An diesem Punkt sollten Sie Ihr Projekt mit den empfohlenen **[Unreal-Leistungseinstellungen](../performance-recommendations-for-unreal.md)** aktualisieren, bevor Sie Ihre Anwendung auf einem Gerät oder Emulator bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="720be-160">At this point, you should update your project with the recommended **[Unreal performance settings](../performance-recommendations-for-unreal.md)** before deploying your application to a device or emulator.</span></span>

[<span data-ttu-id="720be-161">Nächster Abschnitt: 6. Verpacken und Bereitstellen auf einem Gerät oder Emulator</span><span class="sxs-lookup"><span data-stu-id="720be-161">Next Section: 6. Packaging & deploying to device or emulator</span></span>](unreal-uxt-ch6.md)
