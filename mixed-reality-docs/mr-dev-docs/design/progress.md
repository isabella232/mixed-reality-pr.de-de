---
title: Anzeigen des Fortschritts
description: Erfahren Sie, wie Statussteuerelemente dem Benutzer Feedback darüber senden, dass in Ihren Mixed Reality-Apps ein Vorgang mit langer Ausführungslaufzeit ausgeführt wird.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Design, Steuerelemente, Ui, ux, Statusanzeige, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 01f032efb887ecfc6f8d66683fb954cd0574a4f3
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600549"
---
# <a name="progress-indicator"></a><span data-ttu-id="98a7b-104">Statusanzeige</span><span class="sxs-lookup"><span data-stu-id="98a7b-104">Progress indicator</span></span>

<br>

<img src="images/MRTK_ProgressIndicator.gif" alt="Progress ring example in HoloLens" width="940px">

<span data-ttu-id="98a7b-105">Ein Statussteuerelement gibt Feedback, dass ein Vorgang mit langer Ausführung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="98a7b-105">A progress control provides feedback that a long-running operation is underway.</span></span> <span data-ttu-id="98a7b-106">Wenn ein Statusindikator angezeigt wird, können Benutzer die Wartezeit anzeigen und nicht mit der App interagieren.</span><span class="sxs-lookup"><span data-stu-id="98a7b-106">When a progress indicator is visible, users can see the wait time and can't interact with the app.</span></span>

<br>

---

## <a name="types-of-progress"></a><span data-ttu-id="98a7b-107">Typen von Statussteuerelementen</span><span class="sxs-lookup"><span data-stu-id="98a7b-107">Types of progress</span></span>

<span data-ttu-id="98a7b-108">Es ist wichtig, dem Benutzer Informationen darüber bereitzustellen, was passiert.</span><span class="sxs-lookup"><span data-stu-id="98a7b-108">It's important to provide the user information about what is happening.</span></span> <span data-ttu-id="98a7b-109">In Mixed Reality können Benutzer leicht von der physischen Umgebung oder den Objekten ablenken, wenn Ihre App kein gutes visuelles Feedback hat.</span><span class="sxs-lookup"><span data-stu-id="98a7b-109">In mixed reality, users can be easily distracted by the physical environment or objects if your app doesn't have good visual feedback.</span></span> <span data-ttu-id="98a7b-110">In Situationen, die einige Sekunden dauern, z. B. wenn Daten geladen werden oder eine Szene aktualisiert wird, empfiehlt es sich, einen visuellen Indikator anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="98a7b-110">For situations that take a few seconds, like when data is loading or a scene is updating, it's a good idea to show a visual indicator.</span></span> <span data-ttu-id="98a7b-111">Es gibt zwei Optionen, um dem Benutzer anzuzeigen, dass ein Vorgang ausgeführt wird: eine **Statusanzeige** oder ein **Statusring.**</span><span class="sxs-lookup"><span data-stu-id="98a7b-111">There are two options to show the user that an operation is underway – a **Progress bar** or a **Progress ring**.</span></span>

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a><span data-ttu-id="98a7b-112">Statusleiste</span><span class="sxs-lookup"><span data-stu-id="98a7b-112">Progress bar</span></span><br>
        <span data-ttu-id="98a7b-113">Eine Statusanzeige zeigt den Prozentsatz an, in dem eine Aufgabe abgeschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="98a7b-113">A Progress bar shows the percentage completed of a task.</span></span> <span data-ttu-id="98a7b-114">Sie sollte während eines Vorgangs verwendet werden, dessen Dauer bekannt ist (determinierend), aber der Fortschritt sollte die Interaktion des Benutzers mit der App nicht blockieren.</span><span class="sxs-lookup"><span data-stu-id="98a7b-114">It should be used during an operation whose duration is known (determinate), but its progress shouldn't block the user's interaction with the app.</span></span><br>
        <br>
        <span data-ttu-id="98a7b-115">*Abbildung: Beispiel der Statusanzeige in HoloLens*</span><span class="sxs-lookup"><span data-stu-id="98a7b-115">*Image: Progress bar example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="98a7b-116">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="98a7b-116">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="98a7b-117">![Beispiel der Statusanzeige in HoloLens](images/640px-progressbar.jpg)</span><span class="sxs-lookup"><span data-stu-id="98a7b-117">![Progress bar example in HoloLens](images/640px-progressbar.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a><span data-ttu-id="98a7b-118">Statusring</span><span class="sxs-lookup"><span data-stu-id="98a7b-118">Progress ring</span></span><br>
        <span data-ttu-id="98a7b-119">Ein Statusring weist nur einen unbestimmten Zustand auf und sollte verwendet werden, wenn die Benutzerinteraktion blockiert wird, bis der Vorgang abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="98a7b-119">A Progress ring only has an indeterminate state, and should be used when user interaction is blocked until the operation has completed.</span></span><br>
        <br>
        <span data-ttu-id="98a7b-120">*Abbildung: Beispiel eines Statusrings in HoloLens*</span><span class="sxs-lookup"><span data-stu-id="98a7b-120">*Image: Progress ring example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="98a7b-121">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="98a7b-121">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="98a7b-122">![Beispiel eines Statusrings auf HoloLens-Gerät](images/640px-progressring.jpg)</span><span class="sxs-lookup"><span data-stu-id="98a7b-122">![Progress ring example on HoloLens device](images/640px-progressring.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a><span data-ttu-id="98a7b-123">Status mit einem benutzerdefinierten Objekt</span><span class="sxs-lookup"><span data-stu-id="98a7b-123">Progress with a custom object</span></span><br>
        <span data-ttu-id="98a7b-124">Sie können der Persönlichkeit und Markenidentität Ihrer App hinzufügen, indem Sie das Progress-Steuerelement mit Ihren eigenen benutzerdefinierten 2D/3D-Objekten anpassen.</span><span class="sxs-lookup"><span data-stu-id="98a7b-124">You can add to your app's personality and brand identity by customizing the Progress control with your own custom 2D/3D objects.</span></span><br>
        <br>
        <span data-ttu-id="98a7b-125">*Abbildung: Status mit benutzerdefiniertem Meshbeispiel in HoloLens*</span><span class="sxs-lookup"><span data-stu-id="98a7b-125">*Image: Progress with custom mesh example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="98a7b-126">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="98a7b-126">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="98a7b-127">![Fortschritt mit benutzerdefiniertem Meshbeispiel in HoloLens](images/640px-progresscustom.jpg)</span><span class="sxs-lookup"><span data-stu-id="98a7b-127">![Progress with custom mesh example in HoloLens](images/640px-progresscustom.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a><span data-ttu-id="98a7b-128">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="98a7b-128">Best practices</span></span>

* <span data-ttu-id="98a7b-129">Eng an die Anzeige von Progress [koppeln oder taggen,](billboarding-and-tag-along.md) da der Benutzer den Kopf leicht in einen leeren Bereich verschieben und den Kontext verlieren kann.</span><span class="sxs-lookup"><span data-stu-id="98a7b-129">Tightly couple [billboarding or tag-along](billboarding-and-tag-along.md) to the display of Progress since the user can easily move their head into empty space and lose context.</span></span> <span data-ttu-id="98a7b-130">Ihre App könnte so aussehen, als wäre sie abgestürzt, wenn der Benutzer nichts sehen kann.</span><span class="sxs-lookup"><span data-stu-id="98a7b-130">Your app might look like it has crashed if the user is unable to see anything.</span></span> <span data-ttu-id="98a7b-131">Die Kennzeichnung und das Tag-Along sind in das Prefab Progress integriert.</span><span class="sxs-lookup"><span data-stu-id="98a7b-131">Billboarding and tag-along is built into the Progress prefab.</span></span>
* <span data-ttu-id="98a7b-132">Es ist immer gut, Statusinformationen darüber bereitzustellen, was dem Benutzer passiert.</span><span class="sxs-lookup"><span data-stu-id="98a7b-132">It's always good to provide status information about what is happening to the user.</span></span> <span data-ttu-id="98a7b-133">Das Prefab Progress stellt verschiedene visuelle Stile bereit, einschließlich des Status des Windows-Standardringtyps zum Bereitstellen des Status.</span><span class="sxs-lookup"><span data-stu-id="98a7b-133">The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status.</span></span> <span data-ttu-id="98a7b-134">Sie können auch ein benutzerdefiniertes Gitternetz mit einer Animation verwenden, wenn der Stil Ihres Fortschritts an der Marke Ihrer App ausgerichtet werden soll.</span><span class="sxs-lookup"><span data-stu-id="98a7b-134">You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.</span></span>

<br>

---

## <a name="progress-indicator-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="98a7b-135">Statusanzeige im MRTK (Mixed Reality Toolkit) für Unity</span><span class="sxs-lookup"><span data-stu-id="98a7b-135">Progress indicator in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="98a7b-136">MRTK – Prefabs für Statusanzeigen</span><span class="sxs-lookup"><span data-stu-id="98a7b-136">MRTK - Progress indicator prefabs</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/Features/UX/Prefabs/ProgressIndicators)
* [<span data-ttu-id="98a7b-137">MRTK – Szenenübergangsdienst</span><span class="sxs-lookup"><span data-stu-id="98a7b-137">MRTK - Scene transition service</span></span>](/windows/mixed-reality/mrtk-unity/features/extensions/scene-transition-service)


<br>

---

## <a name="see-also"></a><span data-ttu-id="98a7b-138">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="98a7b-138">See also</span></span>

* [<span data-ttu-id="98a7b-139">Cursor</span><span class="sxs-lookup"><span data-stu-id="98a7b-139">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="98a7b-140">Handstrahl</span><span class="sxs-lookup"><span data-stu-id="98a7b-140">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="98a7b-141">Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="98a7b-141">Button</span></span>](button.md)
* [<span data-ttu-id="98a7b-142">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="98a7b-142">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="98a7b-143">Begrenzungsrahmen und App-Leiste</span><span class="sxs-lookup"><span data-stu-id="98a7b-143">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="98a7b-144">Manipulation</span><span class="sxs-lookup"><span data-stu-id="98a7b-144">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="98a7b-145">Handmenü</span><span class="sxs-lookup"><span data-stu-id="98a7b-145">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="98a7b-146">Nähemenü</span><span class="sxs-lookup"><span data-stu-id="98a7b-146">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="98a7b-147">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="98a7b-147">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="98a7b-148">Sprachbefehl</span><span class="sxs-lookup"><span data-stu-id="98a7b-148">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="98a7b-149">Tastatur</span><span class="sxs-lookup"><span data-stu-id="98a7b-149">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="98a7b-150">QuickInfo</span><span class="sxs-lookup"><span data-stu-id="98a7b-150">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="98a7b-151">Filmklappe</span><span class="sxs-lookup"><span data-stu-id="98a7b-151">Slate</span></span>](slate.md)
* [<span data-ttu-id="98a7b-152">Schieberegler</span><span class="sxs-lookup"><span data-stu-id="98a7b-152">Slider</span></span>](slider.md)
* [<span data-ttu-id="98a7b-153">Shader</span><span class="sxs-lookup"><span data-stu-id="98a7b-153">Shader</span></span>](shader.md)
* [<span data-ttu-id="98a7b-154">Billboarding und Tag-along</span><span class="sxs-lookup"><span data-stu-id="98a7b-154">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="98a7b-155">Anzeigen des Fortschritts</span><span class="sxs-lookup"><span data-stu-id="98a7b-155">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="98a7b-156">Oberflächenmagnetismus</span><span class="sxs-lookup"><span data-stu-id="98a7b-156">Surface magnetism</span></span>](surface-magnetism.md)