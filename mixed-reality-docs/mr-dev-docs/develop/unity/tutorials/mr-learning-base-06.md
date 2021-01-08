---
title: 'MRTK-Tutorials: 6. Erstellen der Benutzeroberfläche'
description: In diesem Kurs erfahren Sie, wie Sie das Mixed Reality Toolkit (MRTK) verwenden, um Benutzeroberflächen zu erstellen.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, MRTK, Mixed Reality Toolkit, UWP, Prefabs, Hologramme, QuickInfos
ms.localizationpriority: high
ms.openlocfilehash: 90b794dc6e88b724d16c339e428c4d2ed9cdac07
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613514"
---
# <a name="6-creating-user-interfaces"></a><span data-ttu-id="1aec8-105">6. Erstellen der Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="1aec8-105">6. Creating user interfaces</span></span>

## <a name="overview"></a><span data-ttu-id="1aec8-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="1aec8-106">Overview</span></span>

<span data-ttu-id="1aec8-107">In diesem Tutorial erfahren Sie, wie Sie mithilfe der Schaltflächen- und Menü-Prefabs des MRTK in Kombination mit der TextMeshPro-Komponente von Unity eine einfache Benutzeroberfläche erstellen.</span><span class="sxs-lookup"><span data-stu-id="1aec8-107">In this tutorial, you will learn how to create a simple user interface using MRTK's button and menu prefabs alongside Unity's TextMeshPro component.</span></span> <span data-ttu-id="1aec8-108">Sie erfahren außerdem, wie Sie die Schaltflächen konfigurieren, um Ereignisse auszulösen, und dynamische QuickInfo-Benutzeroberflächenelemente hinzufügen, um den Benutzer mit ergänzenden Informationen zu versorgen.</span><span class="sxs-lookup"><span data-stu-id="1aec8-108">You will also learn how to configure the buttons to trigger events and add dynamic tooltip UI elements to provide the user with additional information.</span></span>

## <a name="objectives"></a><span data-ttu-id="1aec8-109">Ziele</span><span class="sxs-lookup"><span data-stu-id="1aec8-109">Objectives</span></span>

* <span data-ttu-id="1aec8-110">Erfahren, wie Schaltflächen in einer Sammlung organisiert werden</span><span class="sxs-lookup"><span data-stu-id="1aec8-110">Learn how to organize buttons in a collection</span></span>
* <span data-ttu-id="1aec8-111">Erfahren, wie die Menü-Prefabs des MRTK eingesetzt werden</span><span class="sxs-lookup"><span data-stu-id="1aec8-111">Learn how to use MRTK's menu prefabs</span></span>
* <span data-ttu-id="1aec8-112">Erfahren, wie die Interaktion mit Hologrammen mithilfe von Menüs und Schaltflächen der Benutzeroberfläche erfolgt</span><span class="sxs-lookup"><span data-stu-id="1aec8-112">Learn how to interact with holograms using UI menus and buttons</span></span>
* <span data-ttu-id="1aec8-113">Erfahren, wie Textelemente hinzugefügt werden</span><span class="sxs-lookup"><span data-stu-id="1aec8-113">Learn how to add text elements</span></span>
* <span data-ttu-id="1aec8-114">Erfahren, wie QuickInfos für Objekte dynamisch erzeugt werden</span><span class="sxs-lookup"><span data-stu-id="1aec8-114">Learn how to spawn tooltips on objects dynamically</span></span>

## <a name="creating-a-static-panel-of-buttons"></a><span data-ttu-id="1aec8-115">Erstellen eines statischen Schaltflächenpanels</span><span class="sxs-lookup"><span data-stu-id="1aec8-115">Creating a static panel of buttons</span></span>

<span data-ttu-id="1aec8-116">Klicken Sie im Hierarchiefenster mit der rechten Maustaste auf das **RoverExplorer**-Objekt, und wählen Sie **Create Empty** (Leer erstellen) aus, um ein leeres Objekt als untergeordnetes Objekt des RoverExplorers hinzuzufügen, benennen Sie das Objekt **Buttons** (Schaltflächen), und konfigurieren Sie die Komponente **Transform** (Transformieren) wie folgt:</span><span class="sxs-lookup"><span data-stu-id="1aec8-116">In the Hierarchy window, right-click on the **RoverExplorer** object and select **Create Empty** to add an empty object as a child of the RoverExplorer, name the object **Buttons**, and configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="1aec8-117">**Position**: X = -0,6, Y = 0,036, Z = -0,5</span><span class="sxs-lookup"><span data-stu-id="1aec8-117">**Position**: X = -0.6, Y = 0.036, Z = -0.5</span></span>
* <span data-ttu-id="1aec8-118">**Drehung**: X = 90, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="1aec8-118">**Rotation**: X = 90, Y = 0, Z = 0</span></span>
* <span data-ttu-id="1aec8-119">**Skalierung**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="1aec8-119">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Unity mit neu erstelltem, ausgewähltem und positioniertem Buttons-Objekt](images/mr-learning-base/base-06-section1-step1-1.png)

<span data-ttu-id="1aec8-121">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** (Medienobjekte > MRTK.Tutorials.GettingStarted > Prefabs), klicken Sie, und ziehen Sie das **PressableRoundButton**-Prefab auf das **Buttons**-Objekt (Schaltflächen), klicken Sie dann mit der rechten Maustaste auf den PressableRoundButton, und wählen Sie **Duplicate** (Duplizieren) aus, um eine Kopie zu erstellen. Wiederholen Sie diesen letzten Schritt, bis Sie über insgesamt drei PressableRoundButton-Objekte verfügen:</span><span class="sxs-lookup"><span data-stu-id="1aec8-121">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder, click-and-drag the **PressableRoundButton** prefab on to the **Buttons** object, then right-click on the PressableRoundButton and select **Duplicate** to create a copy, repeat until you have a total of three PressableRoundButton objects:</span></span>

![Unity mit neu hinzugefügten PressableRoundButton-Prefabs](images/mr-learning-base/base-06-section1-step1-2.png)

<span data-ttu-id="1aec8-123">Wählen Sie im Hierarchiefenster das Objekt **Buttons** aus, verwenden Sie dann im Inspektorfenster die Schaltfläche **Add Component** (Komponente hinzufügen), um die Komponente **GridObjectCollection** (Rasterobjektsammlung) hinzuzufügen, und konfigurieren Sie sie wie folgt:</span><span class="sxs-lookup"><span data-stu-id="1aec8-123">In the Hierarchy window, select the **Buttons** object, then in the Inspector window, use the **Add Component** button to add the **GridObjectCollection** component and configure it as follows:</span></span>

* <span data-ttu-id="1aec8-124">**Sortierungstyp**: Reihenfolge der untergeordneten Elemente</span><span class="sxs-lookup"><span data-stu-id="1aec8-124">**Sort Type**: Child Order</span></span>
* <span data-ttu-id="1aec8-125">**Layout**: Horizontal</span><span class="sxs-lookup"><span data-stu-id="1aec8-125">**Layout**: Horizontal</span></span>
* <span data-ttu-id="1aec8-126">**Zellenbreite**: 0,2</span><span class="sxs-lookup"><span data-stu-id="1aec8-126">**Cell Width**: 0.2</span></span>
* <span data-ttu-id="1aec8-127">**Anker**: Mitte links</span><span class="sxs-lookup"><span data-stu-id="1aec8-127">**Anchor**: Middle Left</span></span>

<span data-ttu-id="1aec8-128">Klicken Sie dann auf die Schaltfläche **Update Collection** (Sammlung aktualisieren), um die Position der untergeordneten Buttons-Objekte zu aktualisieren:</span><span class="sxs-lookup"><span data-stu-id="1aec8-128">Then click the **Update Collection** button to update the position of the Buttons object's child objects:</span></span>

![Unity-Objekt „Buttons“ mit hinzugefügter, konfigurierter und angewendeter GridObjectCollection-Komponente](images/mr-learning-base/base-06-section1-step1-3.png)

<span data-ttu-id="1aec8-130">Benennen Sie die Schaltflächen im Hierarchiefenster **Hints** (Hinweise), **Explode** (Explodieren) und **Reset** (Zurücksetzen).</span><span class="sxs-lookup"><span data-stu-id="1aec8-130">In the Hierarchy window, name the buttons **Hints**, **Explode**, and **Reset**.</span></span>

<span data-ttu-id="1aec8-131">Wählen Sie für jede Schaltfläche das untergeordnete **SeeItSayItLabel** > **TextMeshPro**-Objekt aus, und ändern Sie dann im Inspektorfenster die entsprechende **TextMeshPro – Text**-Komponente so, dass sie mit den Schaltflächennamen übereinstimmt:</span><span class="sxs-lookup"><span data-stu-id="1aec8-131">For each button, select the **SeeItSayItLabel** > **TextMeshPro** child object, then in the Inspector window, change the respective **TextMeshPro - Text** component text to match the button names:</span></span>

![Unity mit konfigurierten Schaltflächen-Textbezeichnungen](images/mr-learning-base/base-06-section1-step1-4.png)

<span data-ttu-id="1aec8-133">Nachdem das erfolgt ist, klappen Sie die untergeordneten Objekte des Button-Objekts zu.</span><span class="sxs-lookup"><span data-stu-id="1aec8-133">Once done, collapse the Buttons object's child objects.</span></span>

<span data-ttu-id="1aec8-134">Wählen Sie im Hierarchiefenster das Schaltflächenobjekt **Hints** (Hinweise) aus, und konfigurieren Sie dann im Inspektorfenster das **Interactable.OnClick()** -Ereignis wie folgt:</span><span class="sxs-lookup"><span data-stu-id="1aec8-134">In the Hierarchy window, select the **Hints** button object, then in the Inspector window, configure the **Interactable.OnClick ()** event as follows:</span></span>

* <span data-ttu-id="1aec8-135">Weisen Sie das **RoverAssembly**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu.</span><span class="sxs-lookup"><span data-stu-id="1aec8-135">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="1aec8-136">Wählen Sie in der Dropdownliste **No Function** (Keine Funktion) **PlacementHintsController** > **TogglePlacementHints ()** aus, um diese Funktion als Aktion festzulegen, die beim Auslösen des Ereignisses ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="1aec8-136">From the **No Function** dropdown, select **PlacementHintsController** > **TogglePlacementHints ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity mit konfiguriertem OnClick-Ereignis für das Hints-Schaltflächenobjekt](images/mr-learning-base/base-06-section1-step1-5.png)

> [!TIP]
> <span data-ttu-id="1aec8-138">Die Interactable-Komponente ist ein Universalcontainer (All-in-One), mit dem jedes Objekt problemlos in die Lage versetzt werden kann, mit Eingaben zu interagieren und darauf zu reagieren.</span><span class="sxs-lookup"><span data-stu-id="1aec8-138">The Interactable component is an all-in-one container to make any object easily interactable and responsive to input.</span></span> <span data-ttu-id="1aec8-139">Interactable fungiert als Generalcontainer für alle Eingabetypen, einschließlich Toucheingabe, Handstrahl, Sprache usw., und leitet diese Interaktionen in Ereignisse und visuelle Designantworten.</span><span class="sxs-lookup"><span data-stu-id="1aec8-139">Interactable acts as a catch-all for all types of input including touch, hand rays, speech, etc. and funnels these interactions into events and visual theme responses.</span></span> <span data-ttu-id="1aec8-140">Informationen, wie Sie die Komponente für verschiedene Eingabetypen konfigurieren und ihr visuelle Design anpassen, finden Sie im [Interactable](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)-Leitfaden im [MRTK-Dokumentationsportal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="1aec8-140">To learn how to configure it for different input types and customize it's visual theme, you can refer to the [Interactable](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

<span data-ttu-id="1aec8-141">Wählen Sie im Hierarchiefenster das Schaltflächenobjekt **Explode** (Explodieren) aus, und konfigurieren Sie dann im Inspektorfenster das **Interactable.OnClick()** -Ereignis wie folgt:</span><span class="sxs-lookup"><span data-stu-id="1aec8-141">In the Hierarchy window, select the **Explode** button object, then in the Inspector window, configure the **Interactable.OnClick ()** event as follows:</span></span>

* <span data-ttu-id="1aec8-142">Weisen Sie das **RoverAssembly**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu.</span><span class="sxs-lookup"><span data-stu-id="1aec8-142">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="1aec8-143">Wählen Sie in der Dropdownliste **No Function** (Keine Funktion) **ExplodedViewController** > **ToggleExplodedView ()** aus, um diese Funktion als Aktion festzulegen, die beim Auslösen des Ereignisses ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="1aec8-143">From the **No Function** dropdown, select **ExplodedViewController** > **ToggleExplodedView ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity mit konfiguriertem OnClick-Ereignis für das Explode-Schaltflächenobjekt](images/mr-learning-base/base-06-section1-step1-6.png)

<span data-ttu-id="1aec8-145">Drücken Sie die Wiedergabe-Schaltfläche, um in den Spielmodus zu wechseln, und drücken und halten Sie die Leertasten-Schaltfläche, um die Hand zu aktivieren, Verwenden Sie dann die Maus, um auf die **Hints**-Schaltfläche zu klicken, um die Sichtbarkeit der Platzierungshinweisobjekte umzuschalten:</span><span class="sxs-lookup"><span data-stu-id="1aec8-145">Press the Play button to enter Game mode, then press-and-hold the space bar button to activate the hand and use the mouse to press the **Hints** button to toggle the visibility of the placement hint objects:</span></span>

![Geteilte Ansicht des Unity-Wiedergabemodus mit gedrückter Schaltfläche „Hints“](images/mr-learning-base/base-06-section1-step1-7.png)

<span data-ttu-id="1aec8-147">und die **Explode**-Schaltfläche, um die Explosionsansicht ein- und auszuschalten:</span><span class="sxs-lookup"><span data-stu-id="1aec8-147">and the **Explode** button to toggle the exploded view on and off:</span></span>

![Geteilte Ansicht des Unity-Wiedergabemodus mit gedrückter Schaltfläche „Explode“](images/mr-learning-base/base-06-section1-step1-8.png)

## <a name="creating-a-dynamic-menu-that-follows-the-user"></a><span data-ttu-id="1aec8-149">Erstellen eines dynamischen Menüs, das dem Benutzer folgt</span><span class="sxs-lookup"><span data-stu-id="1aec8-149">Creating a dynamic menu that follows the user</span></span>

<span data-ttu-id="1aec8-150">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **Menus** (Medienobjekte > MRTK > SDK > Features > UX > Prefabs > Menüs), klicken Sie auf das **NearMenu4x1**-Prefab, ziehen Sie es auf das Hierarchiefenster, und legen Sie seine **Transformationsposition** auf X = 0, Y = -0,4, Z = 0 fest. Konfigurieren Sie es dann wie folgt:</span><span class="sxs-lookup"><span data-stu-id="1aec8-150">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **Menus** folder, click-and-drag the **NearMenu4x1** prefab into the Hierarchy window, set its Transform **Position** to X = 0, Y = -0.4, Z = 0 and configure it as follows:</span></span>

* <span data-ttu-id="1aec8-151">Vergewissern Sie sich, dass der **Tracked Target Type** (Typ des nachverfolgten Ziels) der **SolverHandler**-Komponente auf **Head** (Kopf) festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="1aec8-151">Verify that the **SolverHandler** component's **Tracked Target Type** is set to **Head**</span></span>
* <span data-ttu-id="1aec8-152">Aktivieren Sie das Kontrollkästchen neben Der Solver-Komponente **RadialView**, sodass sie standardmäßig aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="1aec8-152">Check the checkbox next to the **RadialView** Solver component so it is enabled by default</span></span>

![Unity mit neu hinzugefügtem, ausgewähltem NearMenu-Prefab](images/mr-learning-base/base-06-section2-step1-1.png)

<span data-ttu-id="1aec8-154">Benennen Sie im Hierarchiefenster das Objekt in **Menü** um, und klappen Sie dann sein untergeordnetes Objekt **ButtonCollection** auf, um die vier Schaltflächen anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="1aec8-154">In the Hierarchy window, rename the object to **Menu**, then expand its **ButtonCollection** child object to reveal the four buttons:</span></span>

![Unity mit ausgewähltem Menü-Objekt und erweitertem ButtonCollection-Objekt](images/mr-learning-base/base-06-section2-step1-2.png)

<span data-ttu-id="1aec8-156">Benennen Sie die erste Schaltfläche in **Indicator** (Indikator) um, und konfigurieren Sie dann im Inspektorfenster die Komponente **Button Config Helper (Script)** wie folgt:</span><span class="sxs-lookup"><span data-stu-id="1aec8-156">Rename the first button to **Indicator**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="1aec8-157">Ändern Sie den **Main Label Text** (Hauptbezeichnungstext) so, dass er dem Namen der Schaltfläche entspricht.</span><span class="sxs-lookup"><span data-stu-id="1aec8-157">Change the **Main Label Text** to match the name of the button</span></span>
* <span data-ttu-id="1aec8-158">Weisen Sie das **Indicator**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu.</span><span class="sxs-lookup"><span data-stu-id="1aec8-158">Assign the **Indicator** object to the **None (Object)** field</span></span>
* <span data-ttu-id="1aec8-159">Wählen Sie in der Dropdownliste **No Function** (Keine Funktion) **GameObject** > **SetActive (bool)** aus, um diese Funktion als die beim Auslösen des Ereignisses auszuführende Aktion festzulegen.</span><span class="sxs-lookup"><span data-stu-id="1aec8-159">From the **No Function** dropdown, select **GameObject** > **SetActive (bool)** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="1aec8-160">Überprüfen Sie, ob das Argumentkontrollkästchen **aktiviert** ist.</span><span class="sxs-lookup"><span data-stu-id="1aec8-160">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="1aec8-161">Ändern Sie das **Symbol** zum Symbol „Suchen“</span><span class="sxs-lookup"><span data-stu-id="1aec8-161">Change the **Icon** to the 'search' icon</span></span>

![Unity mit konfiguriertem Button Config Helper für Indicator-Schaltflächenobjekt](images/mr-learning-base/base-06-section2-step1-3.png)

<span data-ttu-id="1aec8-163">Wählen Sie im Hierarchiefenster das **Indikator**-Objekt aus, und führen Sie dann im Inspektorfenster folgende Aktionen aus:</span><span class="sxs-lookup"><span data-stu-id="1aec8-163">In the Hierarchy window, select the **Indicator** object, then in the Inspector window:</span></span>

* <span data-ttu-id="1aec8-164">Deaktivieren Sie das Kontrollkästchen neben ihrem Namen, um sie als standardmäßig inaktiv festzulegen.</span><span class="sxs-lookup"><span data-stu-id="1aec8-164">Uncheck the checkbox next to its name to make it inactive by default</span></span>
* <span data-ttu-id="1aec8-165">Verwenden Sie die Schaltfläche **Komponente hinzufügen**, um die Komponente **Directional Indicator Controller (Script)** hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="1aec8-165">Use the **Add Component** button to add the **Directional Indicator Controller (Script)** component</span></span>

![Unity mit ausgewähltem und deaktiviertem Indicator-Objekt sowie hinzugefügter DirectionalIndicatorController-Komponente](images/mr-learning-base/base-06-section2-step1-4.png)

> [!NOTE]
> <span data-ttu-id="1aec8-167">Jetzt ist der Indikator beim Starten der App standardmäßig deaktiviert und kann durch Drücken der Schaltfläche „Indicator“ (Indikator) aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="1aec8-167">Now, when the app starts, the Indicator is disabled by default and can be enabled by pressing the Indicator button.</span></span>

<span data-ttu-id="1aec8-168">Benennen Sie die zweite Schaltfläche in **TapToPlace** (Zum Platzieren tippen) um, und konfigurieren Sie dann im Inspektorfenster die Komponente **Button Config Helper (Script)** wie folgt:</span><span class="sxs-lookup"><span data-stu-id="1aec8-168">Rename the second button to **TapToPlace**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="1aec8-169">Ändern Sie den **Main Label Text** (Hauptbezeichnungstext) so, dass er dem Namen der Schaltfläche entspricht.</span><span class="sxs-lookup"><span data-stu-id="1aec8-169">Change the **Main Label Text** to match the name of the button</span></span>
* <span data-ttu-id="1aec8-170">Weisen Sie das RoverExplorer > **RoverAssembly**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu.</span><span class="sxs-lookup"><span data-stu-id="1aec8-170">Assign the RoverExplorer > **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="1aec8-171">Wählen Sie in der Dropdownliste **No Function** (Ohne Funktion) **TapToPlace** > **bool Enabled** aus, um diesen Eigenschaftswert zu aktualisieren, wenn das Ereignis ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="1aec8-171">From the **No Function** dropdown, select **TapToPlace** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="1aec8-172">Überprüfen Sie, ob das Argumentkontrollkästchen **aktiviert** ist.</span><span class="sxs-lookup"><span data-stu-id="1aec8-172">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="1aec8-173">Ändern des **Symbols** in das Symbol „Hand mit Strahl“</span><span class="sxs-lookup"><span data-stu-id="1aec8-173">Change the **Icon** to the 'hand with ray' icon</span></span>

![Unity mit konfiguriertem Button Config Helper für TapToPlace-Schaltflächenobjekt](images/mr-learning-base/base-06-section2-step1-5.png)

<span data-ttu-id="1aec8-175">Wählen Sie im Hierarchiefenster das **RoverAssembly**-Objekt aus, und konfigurieren Sie dann im Inspektorfenster die Komponente **Tap To Place (Script)** wie folgt:</span><span class="sxs-lookup"><span data-stu-id="1aec8-175">In the Hierarchy window, select the **RoverAssembly** object, then in the Inspector window, configure the **Tap To Place (Script)** component as follows:</span></span>

* <span data-ttu-id="1aec8-176">Deaktivieren Sie das Kontrollkästchen neben ihrem Namen, um sie als standardmäßig inaktiv festzulegen.</span><span class="sxs-lookup"><span data-stu-id="1aec8-176">Uncheck the checkbox next to its name to make it inactive by default</span></span>
* <span data-ttu-id="1aec8-177">Klicken Sie im Ereignisabschnitt **On Placing Stopped ()** auf das Symbol **+** , um ein neues Ereignis hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="1aec8-177">In the **On Placing Stopped ()** event section, click the **+** icon to add a new event:</span></span>
* <span data-ttu-id="1aec8-178">Weisen Sie das RoverExplorer > **RoverAssembly**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu.</span><span class="sxs-lookup"><span data-stu-id="1aec8-178">Assign the RoverExplorer > **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="1aec8-179">Wählen Sie in der Dropdownliste **No Function** (Ohne Funktion) **TapToPlace** > **bool Enabled** aus, um diesen Eigenschaftswert zu aktualisieren, wenn das Ereignis ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="1aec8-179">From the **No Function** dropdown, select **TapToPlace** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="1aec8-180">Vergewissern Sie sich, dass das Argumentkontrollkästchen **deaktiviert** ist.</span><span class="sxs-lookup"><span data-stu-id="1aec8-180">Verify that the argument checkbox is **unchecked**</span></span>

![Unity mit neu konfigurierter TapToPlace-Komponente](images/mr-learning-base/base-06-section2-step1-6.png)

> [!NOTE]
> <span data-ttu-id="1aec8-182">Jetzt ist die Tap to Place-Funktionalität beim Starten der App standardmäßig deaktiviert und kann durch Drücken der Schaltfläche „Tap to Place“ aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="1aec8-182">Now, when the app starts, the Tap to Place functionality is disabled by default and can be enabled by pressing the Tap to Place button.</span></span> <span data-ttu-id="1aec8-183">Wenn das Tippen zum Platzieren abgeschlossen ist, deaktiviert es sich darüber hinaus selbst.</span><span class="sxs-lookup"><span data-stu-id="1aec8-183">Additionally, when the tap to place is completed, it will disable itself.</span></span>

## <a name="adding-text-to-the-scene"></a><span data-ttu-id="1aec8-184">Hinzufügen von Text zur Szene</span><span class="sxs-lookup"><span data-stu-id="1aec8-184">Adding text to the scene</span></span>

<span data-ttu-id="1aec8-185">Klicken Sie im Hierarchiefenster mit der rechten Maustaste auf das **Table**-Objekt (Tabelle), und wählen Sie **3D Object** > **Text - TextMeshPro** (3D-Objekt > Text – TextMeshPro) aus, um ein Textobjekt als untergeordnetes Objekt des Tabellenobjekts hinzuzufügen. Konfigurieren Sie anschließend im Inspektorfenster die Komponente **Rect Transform** (Rechtecktransformation) wie folgt:</span><span class="sxs-lookup"><span data-stu-id="1aec8-185">In the Hierarchy window, right-click on the **Table** object and select **3D Object** > **Text - TextMeshPro** to add a text object as a child of the Table object, then in the Inspector window, configure the **Rect Transform** component as follows:</span></span>

* <span data-ttu-id="1aec8-186">Ändern Sie **Pos Y** in 1</span><span class="sxs-lookup"><span data-stu-id="1aec8-186">Change **Pos Y** to 1</span></span>
* <span data-ttu-id="1aec8-187">Ändern Sie **Breite** in 1</span><span class="sxs-lookup"><span data-stu-id="1aec8-187">Change **Width** to 1</span></span>
* <span data-ttu-id="1aec8-188">Ändern Sie **Höhe** in 1</span><span class="sxs-lookup"><span data-stu-id="1aec8-188">Change **Height** to 1</span></span>
* <span data-ttu-id="1aec8-189">Ändern Sie **Drehung X** in 90.</span><span class="sxs-lookup"><span data-stu-id="1aec8-189">Change **Rotation X** to 90</span></span>

![Unity mit neu erstelltem, ausgewähltem TextMeshPro-Objekt](images/mr-learning-base/base-06-section3-step1-1.png)

<span data-ttu-id="1aec8-191">Konfigurieren Sie dann die Komponente **TextMeshPro - Text** wie folgt:</span><span class="sxs-lookup"><span data-stu-id="1aec8-191">Then configure the **TextMeshPro - Text** component as follows::</span></span>

* <span data-ttu-id="1aec8-192">Ändern Sie **Text** in „Rover Explorer“</span><span class="sxs-lookup"><span data-stu-id="1aec8-192">Change **Text** to Rover Explorer</span></span>
* <span data-ttu-id="1aec8-193">Ändern Sie **Schriftschnitt** in Fett</span><span class="sxs-lookup"><span data-stu-id="1aec8-193">Change **Font Style** to Bold</span></span>
* <span data-ttu-id="1aec8-194">Ändern Sie den **Schriftgrad** in „1“</span><span class="sxs-lookup"><span data-stu-id="1aec8-194">Change **Font Size** to 1</span></span>
* <span data-ttu-id="1aec8-195">Ändern Sie „Zusätzliche Einstellungen > **Ränder** in 0,03</span><span class="sxs-lookup"><span data-stu-id="1aec8-195">Change Extra Settings > **Margins** to 0.03</span></span>

![Unity mit konfigurierter TextMeshPro-Komponente](images/mr-learning-base/base-06-section3-step1-2.png)

## <a name="adding-tooltips"></a><span data-ttu-id="1aec8-197">Hinzufügen von QuickInfos</span><span class="sxs-lookup"><span data-stu-id="1aec8-197">Adding tooltips</span></span>

<span data-ttu-id="1aec8-198">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** (Medienobjekte > MRTK > SDK > Features > UX > Prefabs > QuickInfo), um die QuickInfo-Prefabs zu suchen:</span><span class="sxs-lookup"><span data-stu-id="1aec8-198">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** folder to locate the tooltip prefabs:</span></span>

![Unity-Projektfenster mit ausgewähltem Ordner „ToolTips“](images/mr-learning-base/base-06-section4-step1-1.png)

<span data-ttu-id="1aec8-200">Klappen Sie im Hierarchiefenster das Objekt „RoverExplorer > **RoverParts**“ auf, und wählen Sie alle seine untergeordneten Rover-Teilobjekte aus. Verwenden Sie dann im Inspektorfenster die Schaltfläche **Add Component** (Komponente hinzufügen), um die Komponente **ToolTipSpawner** hinzuzufügen, und konfigurieren Sie sie wie folgt:</span><span class="sxs-lookup"><span data-stu-id="1aec8-200">In the Hierarchy window, expand the RoverExplorer > **RoverParts** object and select all its child rover part objects, then in the Inspector window, use the **Add Component** button to add the **ToolTipSpawner** component and configure it as follows:</span></span>

* <span data-ttu-id="1aec8-201">Vergewissern Sie sich, dass das Kontrollkästchen **Focus Enabled** (Fokus aktiviert) aktiviert ist, um vorzuschreiben, dass der Benutzer das Teil anblickt, damit die QuickInfo angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="1aec8-201">Ensure the **Focus Enabled** checkbox is checked to require the user to look at the part for the tooltip to appear</span></span>
* <span data-ttu-id="1aec8-202">Weisen Sie das **Simple Line ToolTip**-Prefab (Einfachlinie-QuickInfo) aus dem Projektfenster dem Feld **Tool Tip Prefab** (QuickInfo-Prefab) zu.</span><span class="sxs-lookup"><span data-stu-id="1aec8-202">Assign the **Simple Line ToolTip** prefab from the Project window to the **Tool Tip Prefab** field</span></span>
* <span data-ttu-id="1aec8-203">Ändern Sie den „ToolTip Override Settings > **Settings Mode**“ (QuickInfo-Einstellungen für die Außerkraftsetzung > Einstellungsmodus) in **Override** (Außer Kraft setzen).</span><span class="sxs-lookup"><span data-stu-id="1aec8-203">Change the ToolTip Override Settings > **Settings Mode** to **Override**</span></span>
* <span data-ttu-id="1aec8-204">Ändern Sie die „ToolTip Override Settings > **Manual Pivot Local Position Y**“ (QuickInfo-Einstellungen für die Außerkraftsetzung > Manuelle lokale Y-Pivotposition) in **1,5**.</span><span class="sxs-lookup"><span data-stu-id="1aec8-204">Change the ToolTip Override Settings > **Manual Pivot Local Position Y** to **1.5**</span></span>

![Unity mit allen Rover-Teil-Objekten ausgewählt und hinzugefügter und konfigurierter ToolTipSpawner-Komponente](images/mr-learning-base/base-06-section4-step1-2.png)

<span data-ttu-id="1aec8-206">Wählen Sie im Hierarchiefenster das erste Rover-Teil aus „RoverParts > **Camera_Part**“ aus, und konfigurieren Sie die **ToolTipSpawner**-Komponente wie folgt:</span><span class="sxs-lookup"><span data-stu-id="1aec8-206">In the Hierarchy window, select the first rover part, RoverParts > **Camera_Part**, and configure the **ToolTipSpawner** component as follows:</span></span>

* <span data-ttu-id="1aec8-207">Ändern Sie den **Tool Tip Text** (QuickInfo-Text) so, dass er den Namen des Teils wiedergibt, d. h. **Camera** (Kamera).</span><span class="sxs-lookup"><span data-stu-id="1aec8-207">Change **Tool Tip Text** to reflect the name of the part, i.e., **Camera**</span></span>

![Unity mit konfiguriertem Camera ToolTipText](images/mr-learning-base/base-06-section4-step1-3.png)

<span data-ttu-id="1aec8-209">**Wiederholen** Sie diesen Schritt für jedes der Rover-Teilobjekte, um die **ToolTipSpawner**-Komponente wie folgt zu konfigurieren:</span><span class="sxs-lookup"><span data-stu-id="1aec8-209">**Repeat** this step for each of the rover part objects to configure the **ToolTipSpawner** component as follows:</span></span>

* <span data-ttu-id="1aec8-210">Ändern Sie für das **Generator_Part** den **Tool Tip Text** in **Generator**.</span><span class="sxs-lookup"><span data-stu-id="1aec8-210">For the **Generator_Part**, change the **Tool Tip Text** to **Generator**</span></span>
* <span data-ttu-id="1aec8-211">Ändern Sie für das **Lights_Part** den **Tool Tip Text** in **Lights** (Lichter).</span><span class="sxs-lookup"><span data-stu-id="1aec8-211">For the **Lights_Part**, change the **Tool Tip Text** to **Lights**</span></span>
* <span data-ttu-id="1aec8-212">Ändern Sie für das **UHFAntenna_Part** den **Tool Tip Text** in **UHF Antenna** (UHF-Antenne).</span><span class="sxs-lookup"><span data-stu-id="1aec8-212">For the **UHFAntenna_Part**, change the **Tool Tip Text** to **UHF Antenna** field</span></span>
* <span data-ttu-id="1aec8-213">Ändern Sie für das **Spectrometer_Part** den **Tool Tip Text** in **Spectrometer** (Spektrometer).</span><span class="sxs-lookup"><span data-stu-id="1aec8-213">For the **Spectrometer_Part**, change the **Tool Tip Text** to **Spectrometer**</span></span>

<span data-ttu-id="1aec8-214">Drücken Sie die Wiedergabe-Schaltfläche, um in den Spielmodus zu wechseln, drücken Sie dann die rechte Maustaste, und halten Sie sie gedrückt, während Sie Maus bewegen, bis der Blick auf eins der Teile trifft, dann wird die QuickInfo für das betreffende Teil angezeigt:</span><span class="sxs-lookup"><span data-stu-id="1aec8-214">Press the Play button to enter Game mode, then press-and-hold the right mouse button while moving your mouse until the gaze hit's one of the parts and the tooltip for that part will be displayed:</span></span>

![Geteilte Ansicht des Unity-Wiedergabemodus mit mittels Anvisieren ausgelöstem ToolTip](images/mr-learning-base/base-06-section4-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="1aec8-216">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="1aec8-216">Congratulations</span></span>

<span data-ttu-id="1aec8-217">In diesem Tutorial haben Sie gelernt, wie Sie eine einfache Benutzeroberfläche mit den von MRTK bereitgestellten Schaltfläche- und Menü-Prefabs in Kombination mit der TextMeshPro-Komponente von Unity erstellen und wie Sie die Schaltflächen für das Auslösen von Ereignissen konfigurieren, wenn sie gedrückt werden.</span><span class="sxs-lookup"><span data-stu-id="1aec8-217">In this tutorial, you learned how to create a simple user interface using MRTK's provided button and menu prefabs alongside Unity's TextMeshPro component and how to configure the buttons to trigger events when they are pressed.</span></span> <span data-ttu-id="1aec8-218">Sie haben außerdem gelernt, wie Sie dynamische QuickInfo-Elemente zur Benutzeroberfläche hinzufügen, um dem Benutzer zusätzliche Informationen an die Hand zu geben.</span><span class="sxs-lookup"><span data-stu-id="1aec8-218">You also learned how to add dynamic tooltip UI elements to provide the user with additional information.</span></span>

[<span data-ttu-id="1aec8-219">Nächstes Tutorial: 7. Interagieren mit 3D-Objekten</span><span class="sxs-lookup"><span data-stu-id="1aec8-219">Next Tutorial: 7. Interacting with 3D objects</span></span>](mr-learning-base-07.md)