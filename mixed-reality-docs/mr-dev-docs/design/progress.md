---
title: Anzeigen des Fortschritts
description: Erfahren Sie, wie die Statuskontrolle dem Benutzer Feedback zur Verfügung stellt, dass ein Vorgang mit langer Ausführungszeit in ihren Mixed Reality-apps ausgeführt wird.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Gemischte Windows Mixed Reality, Design, Steuerelemente, UI, UX, Fortschrittsanzeige, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens, mrtk, Mixed Reality Toolkit
ms.openlocfilehash: f323559c9a50a6f01636f0aba0bddc93b547125b
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759846"
---
# <a name="progress-indicator"></a><span data-ttu-id="9c5cd-104">Statusanzeige</span><span class="sxs-lookup"><span data-stu-id="9c5cd-104">Progress indicator</span></span>

<br>

<img src="images/MRTK_ProgressIndicator.gif" alt="Progress ring example in HoloLens" width="940px">

<span data-ttu-id="9c5cd-105">Eine Statuskontrolle bietet Feedback, dass ein Vorgang mit langer Laufzeit ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="9c5cd-105">A progress control provides feedback that a long-running operation is underway.</span></span> <span data-ttu-id="9c5cd-106">Wenn eine Statusanzeige sichtbar ist, können Benutzer die Wartezeit sehen und können nicht mit der APP interagieren.</span><span class="sxs-lookup"><span data-stu-id="9c5cd-106">When a progress indicator is visible, users can see the wait time and can't interact with the app.</span></span>

<br>

---

## <a name="types-of-progress"></a><span data-ttu-id="9c5cd-107">Typen von Statussteuerelementen</span><span class="sxs-lookup"><span data-stu-id="9c5cd-107">Types of progress</span></span>

<span data-ttu-id="9c5cd-108">Es ist wichtig, dass Sie die Benutzerinformationen zu den Vorgängen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="9c5cd-108">It's important to provide the user information about what is happening.</span></span> <span data-ttu-id="9c5cd-109">In gemischter Realität können Benutzer leicht von der physischen Umgebung oder Objekten abgelenkt werden, wenn Ihre APP kein gutes visuelles Feedback hat.</span><span class="sxs-lookup"><span data-stu-id="9c5cd-109">In mixed reality, users can be easily distracted by the physical environment or objects if your app doesn't have good visual feedback.</span></span> <span data-ttu-id="9c5cd-110">Für Situationen, die einige Sekunden dauern, z. b. beim Laden von Daten oder beim Aktualisieren einer Szene, empfiehlt es sich, einen visuellen Indikator anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="9c5cd-110">For situations that take a few seconds, like when data is loading or a scene is updating, it's a good idea to show a visual indicator.</span></span> <span data-ttu-id="9c5cd-111">Es gibt zwei Möglichkeiten, den Benutzer anzuzeigen, dass ein Vorgang ausgeführt wird – eine **Status** Anzeige oder ein **Fortschritts Ring**.</span><span class="sxs-lookup"><span data-stu-id="9c5cd-111">There are two options to show the user that an operation is underway – a **Progress bar** or a **Progress ring**.</span></span>

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a><span data-ttu-id="9c5cd-112">Statusleiste</span><span class="sxs-lookup"><span data-stu-id="9c5cd-112">Progress bar</span></span><br>
        <span data-ttu-id="9c5cd-113">Eine Statusanzeige zeigt den Prozentsatz der abgeschlossenen Aufgabe an.</span><span class="sxs-lookup"><span data-stu-id="9c5cd-113">A Progress bar shows the percentage completed of a task.</span></span> <span data-ttu-id="9c5cd-114">Er sollte bei einem Vorgang verwendet werden, dessen Dauer bekannt ist (determinate), aber sein Fortschritt sollte die Interaktion des Benutzers mit der APP nicht blockieren.</span><span class="sxs-lookup"><span data-stu-id="9c5cd-114">It should be used during an operation whose duration is known (determinate), but its progress shouldn't block the user's interaction with the app.</span></span><br>
        <br>
        <span data-ttu-id="9c5cd-115">*Bild: Statusanzeige Beispiel in hololens*</span><span class="sxs-lookup"><span data-stu-id="9c5cd-115">*Image: Progress bar example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="9c5cd-116">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="9c5cd-116">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="9c5cd-117">![Beispiel für Statusanzeige in hololens](images/640px-progressbar.jpg)</span><span class="sxs-lookup"><span data-stu-id="9c5cd-117">![Progress bar example in HoloLens](images/640px-progressbar.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a><span data-ttu-id="9c5cd-118">Statusring</span><span class="sxs-lookup"><span data-stu-id="9c5cd-118">Progress ring</span></span><br>
        <span data-ttu-id="9c5cd-119">Ein Fortschritts Ring hat nur einen unbestimmten Status und sollte verwendet werden, wenn die Benutzerinteraktion blockiert wird, bis der Vorgang abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="9c5cd-119">A Progress ring only has an indeterminate state, and should be used when user interaction is blocked until the operation has completed.</span></span><br>
        <br>
        <span data-ttu-id="9c5cd-120">*Image: Fortschritts Ring-Beispiel in hololens*</span><span class="sxs-lookup"><span data-stu-id="9c5cd-120">*Image: Progress ring example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="9c5cd-121">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="9c5cd-121">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="9c5cd-122">![Beispiel für Status Ring auf hololens-Gerät](images/640px-progressring.jpg)</span><span class="sxs-lookup"><span data-stu-id="9c5cd-122">![Progress ring example on HoloLens device](images/640px-progressring.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a><span data-ttu-id="9c5cd-123">Fortschritt mit einem benutzerdefinierten Objekt</span><span class="sxs-lookup"><span data-stu-id="9c5cd-123">Progress with a custom object</span></span><br>
        <span data-ttu-id="9c5cd-124">Sie können der Identität und Markenidentität Ihrer APP hinzufügen, indem Sie das Status Steuerelement mit ihren eigenen benutzerdefinierten 2D-/3D-Objekten anpassen.</span><span class="sxs-lookup"><span data-stu-id="9c5cd-124">You can add to your app's personality and brand identity by customizing the Progress control with your own custom 2D/3D objects.</span></span><br>
        <br>
        <span data-ttu-id="9c5cd-125">*Bild: Fortschritt mit einem benutzerdefinierten Mesh-Beispiel in hololens*</span><span class="sxs-lookup"><span data-stu-id="9c5cd-125">*Image: Progress with custom mesh example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="9c5cd-126">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="9c5cd-126">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="9c5cd-127">![Fortschritt mit einem benutzerdefinierten Mesh-Beispiel in hololens](images/640px-progresscustom.jpg)</span><span class="sxs-lookup"><span data-stu-id="9c5cd-127">![Progress with custom mesh example in HoloLens](images/640px-progresscustom.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a><span data-ttu-id="9c5cd-128">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="9c5cd-128">Best practices</span></span>

* <span data-ttu-id="9c5cd-129">Schließen Sie das [Abrechnungs-oder tagboarding](billboarding-and-tag-along.md) eng mit der Anzeige des Fortschritts ab, da der Benutzer problemlos seinen Kopf in einen leeren Bereich verschieben und Kontext verlieren kann.</span><span class="sxs-lookup"><span data-stu-id="9c5cd-129">Tightly couple [billboarding or tag-along](billboarding-and-tag-along.md) to the display of Progress since the user can easily move their head into empty space and lose context.</span></span> <span data-ttu-id="9c5cd-130">Ihre APP könnte so aussehen, als ob Sie abgestürzt ist, wenn der Benutzer nichts sehen kann.</span><span class="sxs-lookup"><span data-stu-id="9c5cd-130">Your app might look like it has crashed if the user is unable to see anything.</span></span> <span data-ttu-id="9c5cd-131">Das fakboardingboarding und das Tag-Along sind in den Fortschritt vorfab integriert.</span><span class="sxs-lookup"><span data-stu-id="9c5cd-131">Billboarding and tag-along is built into the Progress prefab.</span></span>
* <span data-ttu-id="9c5cd-132">Es ist immer gut, Statusinformationen zu den Ereignissen für den Benutzer bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="9c5cd-132">It's always good to provide status information about what is happening to the user.</span></span> <span data-ttu-id="9c5cd-133">Die Fortschritts präfab stellt verschiedene visuelle Stile bereit, einschließlich des Windows-standardmäßigen Rings-Typs zum Angeben des Status.</span><span class="sxs-lookup"><span data-stu-id="9c5cd-133">The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status.</span></span> <span data-ttu-id="9c5cd-134">Sie können auch ein benutzerdefiniertes Mesh mit einer Animation verwenden, wenn Sie möchten, dass der Stil Ihres Fortschritts an der Marke Ihrer APP ausgerichtet wird.</span><span class="sxs-lookup"><span data-stu-id="9c5cd-134">You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.</span></span>

<br>

---

## <a name="progress-indicator-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="9c5cd-135">Fortschrittsanzeige in mrtk (Mixed Reality Toolkit) für Unity</span><span class="sxs-lookup"><span data-stu-id="9c5cd-135">Progress indicator in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="9c5cd-136">Mrtk-Fortschrittsanzeige (Prefabs)</span><span class="sxs-lookup"><span data-stu-id="9c5cd-136">MRTK - Progress indicator prefabs</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MRTK/SDK/Features/UX/Prefabs/ProgressIndicators)
* [<span data-ttu-id="9c5cd-137">Mrtk-Szenen Übergangs Dienst</span><span class="sxs-lookup"><span data-stu-id="9c5cd-137">MRTK - Scene transition service</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/extensions/scene-transition-service.md)


<br>

---

## <a name="see-also"></a><span data-ttu-id="9c5cd-138">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="9c5cd-138">See also</span></span>

* [<span data-ttu-id="9c5cd-139">Cursor</span><span class="sxs-lookup"><span data-stu-id="9c5cd-139">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="9c5cd-140">Handstrahl</span><span class="sxs-lookup"><span data-stu-id="9c5cd-140">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="9c5cd-141">Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="9c5cd-141">Button</span></span>](button.md)
* [<span data-ttu-id="9c5cd-142">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="9c5cd-142">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="9c5cd-143">Begrenzungsrahmen und App-Leiste</span><span class="sxs-lookup"><span data-stu-id="9c5cd-143">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="9c5cd-144">Manipulation</span><span class="sxs-lookup"><span data-stu-id="9c5cd-144">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="9c5cd-145">Handmenü</span><span class="sxs-lookup"><span data-stu-id="9c5cd-145">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="9c5cd-146">Nähemenü</span><span class="sxs-lookup"><span data-stu-id="9c5cd-146">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="9c5cd-147">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="9c5cd-147">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="9c5cd-148">Sprachbefehl</span><span class="sxs-lookup"><span data-stu-id="9c5cd-148">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="9c5cd-149">Tastatur</span><span class="sxs-lookup"><span data-stu-id="9c5cd-149">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="9c5cd-150">QuickInfo</span><span class="sxs-lookup"><span data-stu-id="9c5cd-150">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="9c5cd-151">Filmklappe</span><span class="sxs-lookup"><span data-stu-id="9c5cd-151">Slate</span></span>](slate.md)
* [<span data-ttu-id="9c5cd-152">Schieberegler</span><span class="sxs-lookup"><span data-stu-id="9c5cd-152">Slider</span></span>](slider.md)
* [<span data-ttu-id="9c5cd-153">Shader</span><span class="sxs-lookup"><span data-stu-id="9c5cd-153">Shader</span></span>](shader.md)
* [<span data-ttu-id="9c5cd-154">Billboarding und Tag-along</span><span class="sxs-lookup"><span data-stu-id="9c5cd-154">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="9c5cd-155">Anzeigen des Fortschritts</span><span class="sxs-lookup"><span data-stu-id="9c5cd-155">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="9c5cd-156">Oberflächenmagnetismus</span><span class="sxs-lookup"><span data-stu-id="9c5cd-156">Surface magnetism</span></span>](surface-magnetism.md)
