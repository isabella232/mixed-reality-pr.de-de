---
title: Handmenü
description: Handmenüs ermöglichen es Benutzern, schnell eine hand angefügte Benutzeroberfläche für häufig verwendete Funktionen zu öffnen.
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: Hand, Menü, Schaltfläche, Schnellzugriff, Layout, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: f007ada2d7a594f141d30a3619d4d80ac74621d8
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600329"
---
# <a name="hand-menu"></a><span data-ttu-id="4aeed-104">Handmenü</span><span class="sxs-lookup"><span data-stu-id="4aeed-104">Hand menu</span></span>

![Ulnar-Seitenposition](images/UX_Hero_HandMenu.jpg)

<span data-ttu-id="4aeed-106">Das Handmenü ist eines der einzigartigsten UX-Muster in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="4aeed-106">The hand menu is one of the most unique UX patterns in HoloLens 2.</span></span> <span data-ttu-id="4aeed-107">Dadurch können Sie schnell eine hand angefügte Benutzeroberfläche anzeigen.</span><span class="sxs-lookup"><span data-stu-id="4aeed-107">It allows you to quickly bring up hand-attached UI.</span></span> <span data-ttu-id="4aeed-108">Da sie jederzeit zugänglich ist und einfach angezeigt und ausgeblendet werden kann, ist sie ideal für schnelle Aktionen.</span><span class="sxs-lookup"><span data-stu-id="4aeed-108">Since it's accessible anytime and can be shown and hidden easily, it's great for quick actions.</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAg]

<span data-ttu-id="4aeed-109">Unsere empfohlenen bewährten Methoden für die Arbeit mit Handmenüs finden Sie in der folgenden Liste.</span><span class="sxs-lookup"><span data-stu-id="4aeed-109">You'll find our recommended best practices for working with hand menus in the list below.</span></span> <span data-ttu-id="4aeed-110">Sie finden auch eine Beispielszene, die das Handmenü in [MRTK zeigt.](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)</span><span class="sxs-lookup"><span data-stu-id="4aeed-110">You can also find an example scene demonstrating the hand menu in [MRTK](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu).</span></span>

<br>

---

## <a name="best-practices"></a><span data-ttu-id="4aeed-111">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="4aeed-111">Best practices</span></span>

<span data-ttu-id="4aeed-112">**Halten Sie die Anzahl der Schaltflächen klein.**</span><span class="sxs-lookup"><span data-stu-id="4aeed-112">**Keep the number of buttons small**</span></span> 

<span data-ttu-id="4aeed-113">Aufgrund der nähen Entfernung zwischen einem handgesperrten Menü und den Augen und der Neigung, dass benutzer sich jederzeit auf einen relativ kleinen visuellen Bereich konzentrieren (der Augenkegel beträgt ungefähr 10 Grad), wird empfohlen, die Anzahl der Schaltflächen klein zu halten.</span><span class="sxs-lookup"><span data-stu-id="4aeed-113">Because of the close distance between a hand-locked menu and the eyes, and the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), we recommend keeping the number of buttons small.</span></span> <span data-ttu-id="4aeed-114">Basierend auf unserer Untersuchung funktioniert eine Spalte mit drei Schaltflächen gut, indem alle Inhalte innerhalb des Sichtfelds (Field of View, FOV) selbst dann zentriert bleiben, wenn ein Benutzer seine Hände in die Mitte des FOV bewegt.</span><span class="sxs-lookup"><span data-stu-id="4aeed-114">Based on our exploration, one column with three buttons works well by keeping all the content within the field of view (FOV) even when a user moves their hands to the center of the FOV.</span></span> 

<span data-ttu-id="4aeed-115">**Verwenden des Handmenüs für schnelle Aktionen**</span><span class="sxs-lookup"><span data-stu-id="4aeed-115">**Use hand menu for quick action**</span></span> 

<span data-ttu-id="4aeed-116">Das Erhöhen eines Arms und das Beibehalten der Position kann leicht zu Armermüdung führen.</span><span class="sxs-lookup"><span data-stu-id="4aeed-116">Raising an arm and maintaining the position could easily cause arm fatigue.</span></span> <span data-ttu-id="4aeed-117">Verwenden Sie eine handgesperrte Methode für das Menü, das eine kurze Interaktion erfordert.</span><span class="sxs-lookup"><span data-stu-id="4aeed-117">Use a hand-locked method for the menu requiring a short interaction.</span></span> <span data-ttu-id="4aeed-118">Wenn Ihr Menü komplex ist und längere Interaktionszeiten erfordert, sollten Sie stattdessen die Verwendung von welt- oder textgesperrt in Betracht ziehen.</span><span class="sxs-lookup"><span data-stu-id="4aeed-118">If your menu is complex and requires extended interaction times, consider using world-locked or body-locked instead.</span></span> 

<span data-ttu-id="4aeed-119">**Schaltflächen-/Panelwinkel**</span><span class="sxs-lookup"><span data-stu-id="4aeed-119">**Button / Panel angle**</span></span>

<span data-ttu-id="4aeed-120">Menüs sollten sich gegen die entgegengesetzte Kopf- und Kopfmitte bewegen: Dies ermöglicht eine natürliche Handbewegung, um mit der entgegengesetzten Hand mit dem Menü zu interagieren, und vermeidet unhandliche oder träge Handpositionen beim Berühren von Schaltflächen.</span><span class="sxs-lookup"><span data-stu-id="4aeed-120">Menus should billboard towards the opposite shoulder and middle of the head: This allows a natural hand move to interact with the menu with the opposite hand and avoids any awkward or uncomfortable hand positions when touching buttons.</span></span> 

<span data-ttu-id="4aeed-121">**Erwägen Sie die Unterstützung eines einhändigen oder freihändigen Vorgangs.**</span><span class="sxs-lookup"><span data-stu-id="4aeed-121">**Consider supporting one-handed or hands-free operation**</span></span>

<span data-ttu-id="4aeed-122">Gehen Sie nicht davon aus, dass beide Hände des Benutzers immer verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="4aeed-122">Don't assume both of the user's hands are always available.</span></span> <span data-ttu-id="4aeed-123">Stellen Sie sich eine Vielzahl von Kontexten vor, wenn eine oder beide Hände nicht verfügbar sind, und stellen Sie sicher, dass Ihr Entwurf für diese Situationen kontent.</span><span class="sxs-lookup"><span data-stu-id="4aeed-123">Consider a wide range of contexts when one or both hands aren't available, and make sure your design accounts for those situations.</span></span> <span data-ttu-id="4aeed-124">Um ein einhändiges Handmenü zu unterstützen, können Sie versuchen, die Menüplatzierung von handgesperrt in weltgesperrt zu überstellen, wenn die Hand kippt (die Hand nach unten geht).</span><span class="sxs-lookup"><span data-stu-id="4aeed-124">To support a one-handed hand menu, you can try transitioning the menu placement from hand-locked to world-locked when the hand flips (goes palm down).</span></span> <span data-ttu-id="4aeed-125">Erwägen Sie für Freihandszenarien die Verwendung eines Sprachbefehls zum Aufrufen des Handmenüs.</span><span class="sxs-lookup"><span data-stu-id="4aeed-125">For hands-free scenarios, consider using a voice command to invoke the hand menu.</span></span>

<span data-ttu-id="4aeed-126">**Vermeiden des Hinzufügens von Schaltflächen in der Nähe des Handgelenks (System-Startschaltfläche)**</span><span class="sxs-lookup"><span data-stu-id="4aeed-126">**Avoid adding buttons near the wrist (system home button)**</span></span>

<span data-ttu-id="4aeed-127">Wenn die Handmenüschaltflächen zu nah an der Startschaltfläche platziert werden, kann dies bei der Interaktion mit dem Handmenü versehentlich ausgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="4aeed-127">If the hand menu buttons are placed too close to the home button, it may accidentally trigger while interacting with the hand menu.</span></span>

<br>

## <a name="hand-menu-with-large-and-complex-ui-controls"></a><span data-ttu-id="4aeed-128">Handmenü mit großen und komplexen Ui-Steuerelementen</span><span class="sxs-lookup"><span data-stu-id="4aeed-128">Hand menu with large and complex UI controls</span></span>

<img src="images/HandMenu_SizeExample.png" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<span data-ttu-id="4aeed-129">Es wird empfohlen, die Anzahl der Schaltflächen oder Ui-Steuerelemente in hand angefügten Menüs zu beschränken.</span><span class="sxs-lookup"><span data-stu-id="4aeed-129">It's recommended to limit the number of buttons or UI controls on hand-attached menus.</span></span> <span data-ttu-id="4aeed-130">Dies liegt daran, dass die erweiterte Interaktion mit einer großen Anzahl von Benutzeroberflächenelementen zu Armermüdung führen kann.</span><span class="sxs-lookup"><span data-stu-id="4aeed-130">This is because extended interaction with a large number of UI elements can cause arm fatigue.</span></span> <span data-ttu-id="4aeed-131">Wenn Ihre Erfahrung ein umfangreiches Menü erfordert, bieten Sie dem Benutzer eine einfache Möglichkeit, das Menü weltweit zu sperren.</span><span class="sxs-lookup"><span data-stu-id="4aeed-131">If your experience requires a large menu, provide an easy way for the user to world lock the menu.</span></span> <span data-ttu-id="4aeed-132">Eine methode, die wir empfehlen, ist das Weltsperren und dann das Menü, wenn die Hand vom Benutzer abfällt oder sich davon kippt.</span><span class="sxs-lookup"><span data-stu-id="4aeed-132">One technique we recommend is to world-lock then menu when the hand drops or flips away from the user.</span></span> <span data-ttu-id="4aeed-133">Ein zweites Verfahren besteht in der Möglichkeit, dem Benutzer zu ermöglichen, das Menü direkt mit der anderen Hand zu greifen.</span><span class="sxs-lookup"><span data-stu-id="4aeed-133">A second technique is to allow the user to directly grab the menu with the other hand.</span></span> <span data-ttu-id="4aeed-134">Wenn der Benutzer das Menü freilässt, sollte das Menü weltsperren.</span><span class="sxs-lookup"><span data-stu-id="4aeed-134">When the user releases the menu, the menu should world lock.</span></span> <span data-ttu-id="4aeed-135">Auf diese Weise kann ein Benutzer über einen längeren Zeitraum bequem und sicher mit verschiedenen Benutzeroberflächenelementen interagieren.</span><span class="sxs-lookup"><span data-stu-id="4aeed-135">This way, a user can interact with various UI elements comfortably and confidently over an extended period of time.</span></span> 

<span data-ttu-id="4aeed-136">Wenn das Menü weltgesperrt ist, stellen Sie sicher, dass Sie eine Möglichkeit zum Verschieben des Menüs bereitstellen und das Menü schließen, wenn es nicht mehr benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="4aeed-136">When the menu is world-locked, make sure to provide a way to move the menu, and close the menu when it's no longer needed.</span></span> <span data-ttu-id="4aeed-137">Machen Sie das Menü verschiebbar, indem Sie Ziehpunkte an den Seiten oder oben im Menü bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="4aeed-137">Make the menu movable by providing handles on the sides or top of menu.</span></span> <span data-ttu-id="4aeed-138">Fügen Sie eine Schaltfläche zum Schließen hinzu, damit das Menü geschlossen werden kann.</span><span class="sxs-lookup"><span data-stu-id="4aeed-138">Add a close button to allow the menu to close.</span></span> <span data-ttu-id="4aeed-139">Lassen Sie zu, dass das Menü erneut an die Hand angefügt wird, wenn der Benutzer dem Benutzer die Hand stellt.</span><span class="sxs-lookup"><span data-stu-id="4aeed-139">Allow for the menu to reattach to the hand when the user hand faces the user.</span></span> <span data-ttu-id="4aeed-140">Es wird auch empfohlen, dass die Benutzer an ihre Hand schauen, um falsche Aktivierungen zu verhindern (siehe unten).</span><span class="sxs-lookup"><span data-stu-id="4aeed-140">We also recommend requiring that the users gaze at their hand to prevent false activations (see below).</span></span>

<span data-ttu-id="4aeed-141">**Großes Menü, das ein Benutzerfreundlichkeitsproblem zeigt**</span><span class="sxs-lookup"><span data-stu-id="4aeed-141">**Large menu that shows a usability issue**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AOPx]

<span data-ttu-id="4aeed-142">**World-locked menu on hand drop**</span><span class="sxs-lookup"><span data-stu-id="4aeed-142">**World-locked menu on hand drop**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AGZi]

<span data-ttu-id="4aeed-143">**Manuelles Greifen & zum Weltsperren des Menüs**</span><span class="sxs-lookup"><span data-stu-id="4aeed-143">**Manual grab & pull to world-lock the menu**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAf]

## <a name="how-to-prevent-false-activation"></a><span data-ttu-id="4aeed-144">Verhindern einer falschen Aktivierung</span><span class="sxs-lookup"><span data-stu-id="4aeed-144">How to prevent false activation</span></span>

<span data-ttu-id="4aeed-145">Wenn Sie das Handmenü nur als Ereignis auslösen, wird es möglicherweise versehentlich angezeigt, wenn Sie es nicht benötigen (falsch positiv), da Benutzer ihre Hände sowohl absichtlich (zur Kommunikation als auch zur Objektbearbeitung) und unbeabsichtigt bewegen.</span><span class="sxs-lookup"><span data-stu-id="4aeed-145">If you use just palm-up as an event to trigger the hand menu, it may accidentally appear when you don't need it (false-positive), because people move their hands both intentionally (for communication and object manipulation) and unintentionally.</span></span> <span data-ttu-id="4aeed-146">Um falsche Aktivierungen zu reduzieren, fügen Sie neben dem Handmenü einen zusätzlichen Schritt hinzu, um das Handmenü auf dem Handmenü auf zu rufen (z. B. vollständig geöffnete Finger oder der Benutzer, der absichtlich an der Hand blättern soll).</span><span class="sxs-lookup"><span data-stu-id="4aeed-146">To reduce false activations, add an extra step besides the palm-up event to invoke the hand menu (such as fully opened fingers, or the user intentionally gazing at their hand).</span></span>

<span data-ttu-id="4aeed-147">**Flache Handfläche erforderlich**</span><span class="sxs-lookup"><span data-stu-id="4aeed-147">**Require Flat Palm**</span></span>

<span data-ttu-id="4aeed-148">Wenn Sie eine flache offene Hand benötigen, können Sie eine falsche Aktivierung verhindern, die auftreten kann, wenn der Benutzer Objekte oder Gesten während der Kommunikation innerhalb einer Umgebung bearbeitet.</span><span class="sxs-lookup"><span data-stu-id="4aeed-148">By requiring a flat open hand, you can prevent false activation that might occur as the user manipulates objects or gestures while communicating within an environment.</span></span> 

<span data-ttu-id="4aeed-149">**Anving erfordern**</span><span class="sxs-lookup"><span data-stu-id="4aeed-149">**Require Gaze**</span></span>

<span data-ttu-id="4aeed-150">Indem der Benutzer an seine Hand anviert werden muss (entweder mit dem Anving mit den Augen oder mit dem Kopf), werden falsche Aktivierungen verhindert, da der Benutzer seine Aufmerksamkeit als sekundären Aktivierungsschritt auf die Hand richten muss (mit einem abstimmbaren Entfernungsschwellenwert, der für Benutzerfreundlichkeit verwendet wird).</span><span class="sxs-lookup"><span data-stu-id="4aeed-150">By requiring the user to gaze at their hand (either with eye gaze or head gaze), it prevents false activations because of the user having to direct their attention to the hand as a secondary activation step (with a tunable distance threshold used to allow for user comfort).</span></span>  

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Asn4]

---

## <a name="hand-menu-placement-best-practices"></a><span data-ttu-id="4aeed-151">Bewährte Methoden für die Platzierung von Handmenüs</span><span class="sxs-lookup"><span data-stu-id="4aeed-151">Hand menu placement best practices</span></span>

<span data-ttu-id="4aeed-152">In der menschlichen Anatomie ist die Ulnar-Menschlichen ein Menschlichen, der in der Nähe des Ulna-Menschlichen ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="4aeed-152">In human anatomy, the ulnar nerve is a nerve that runs near the ulna bone.</span></span> <span data-ttu-id="4aeed-153">Die Ulna ist ein langer Glied im Unterarm, der sich vom Glied bis zum kleinsten Finger erstreckt.</span><span class="sxs-lookup"><span data-stu-id="4aeed-153">The ulna is a long bone found in the forearm that stretches from the elbow to the smallest finger.</span></span>

<span data-ttu-id="4aeed-154">Im Folgenden finden Sie zwei empfohlene Platzierungen basierend auf unseren Untersuchungen:</span><span class="sxs-lookup"><span data-stu-id="4aeed-154">Below are two recommended placements based on our explorations:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="4aeed-155">![Ulnar-Seitenposition innerhalb der Hand](images/UlnarSideHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="4aeed-155">![Ulnar side hand location inside palm](images/UlnarSideHandMenu.gif)</span></span><br>
        <span data-ttu-id="4aeed-156">**A. Ulnar in der Handfläche**</span><span class="sxs-lookup"><span data-stu-id="4aeed-156">**A. Ulnar inside palm**</span></span><br>
        <span data-ttu-id="4aeed-157">Diese Position ist zuverlässig, da sich die Hände nicht überlappen.</span><span class="sxs-lookup"><span data-stu-id="4aeed-157">This position is reliable because the hands don't overlap each other.</span></span> <span data-ttu-id="4aeed-158">Dies ist wichtig für eine genaue Handerkennung und Nachverfolgung.</span><span class="sxs-lookup"><span data-stu-id="4aeed-158">This is critical for accurate hand detection and tracking.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="4aeed-159">![Ulnar-Seitenposition über der Hand](images/UlnarAboveHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="4aeed-159">![Ulnar side hand location above hand](images/UlnarAboveHandMenu.gif)</span></span><br>
        <span data-ttu-id="4aeed-160">**B. Ulnar oben**</span><span class="sxs-lookup"><span data-stu-id="4aeed-160">**B. Ulnar above hand**</span></span><br>
        <span data-ttu-id="4aeed-161">Dieser Ort ist für Benutzer bequem, da sie ihren Arm nicht zu stark erhöhen müssen, um mit dem Handmenü zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="4aeed-161">This location is comfortable for users because they don't need to raise their arm too much to interact with the hand menu.</span></span> <span data-ttu-id="4aeed-162">Es wird empfohlen, Menüs **13 cm** über der Handfläche zu platzieren und die Schaltflächen in der Ulnar-Handfläche auszurichten.</span><span class="sxs-lookup"><span data-stu-id="4aeed-162">We recommend placing menus **13 cm** above the palm and align the buttons inside the ulnar palm.</span></span> [<span data-ttu-id="4aeed-163">Erfahren Sie mehr über die optimale Schaltflächengröße.</span><span class="sxs-lookup"><span data-stu-id="4aeed-163">Read more about the optimal button size</span></span>](interactable-object.md)<br>
        <br>
        <span data-ttu-id="4aeed-164">Aus technischen Gründen empfehlen wir diesen Speicherort mit einer erforderlichen Implementierung: Der Entwickler muss das Menü einfrieren, sobald die entgegengesetzte Hand des Benutzers der Interaktion nahe kommt.</span><span class="sxs-lookup"><span data-stu-id="4aeed-164">For technical reasons, we recommend this location with one required implementation: the developer will need to freeze the menu once the user's opposite hand gets close to interacting with it.</span></span> <span data-ttu-id="4aeed-165">Dies vermeidet Jitteriness durch überlappende Hände und ermöglicht auch eine schnellere Ausrichtung der Schaltflächen.</span><span class="sxs-lookup"><span data-stu-id="4aeed-165">This will avoid jitteriness from overlapping hands and also allows for a faster targeting of the buttons.</span></span><br>
        <br>
        <span data-ttu-id="4aeed-166">HoloLens 2 Die Hände werden von Kameras genau identifiziert, wenn sie voneinander getrennt sind.</span><span class="sxs-lookup"><span data-stu-id="4aeed-166">HoloLens 2 cameras identify hands accurately when they're separate from each other.</span></span> <span data-ttu-id="4aeed-167">Überlappende Hände können dazu führen, dass Handmenüs von der Ankerposition entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="4aeed-167">Any overlapping hands can cause hand menus move away from the anchor location.</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="menu-positions-that-arent-recommended"></a><span data-ttu-id="4aeed-168">Menüpositionen, die nicht empfohlen werden</span><span class="sxs-lookup"><span data-stu-id="4aeed-168">Menu positions that aren't recommended</span></span>

<span data-ttu-id="4aeed-169">Wir haben Benutzerforschung mit verschiedenen Menülayouts und -standorten durchgeführt. Die folgenden Menüpositionen werden **NICHT** empfohlen. Die Nachteile jeder Studie finden Sie unten:</span><span class="sxs-lookup"><span data-stu-id="4aeed-169">We have done user research with different menus layouts and locations, the following menu locations are **NOT recommended**, find the cons of each study below:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="4aeed-170">![Über arm](images/AboveArm.gif)</span><span class="sxs-lookup"><span data-stu-id="4aeed-170">![Above arm](images/AboveArm.gif)</span></span><br>
        <span data-ttu-id="4aeed-171">**Über dem Arm**</span><span class="sxs-lookup"><span data-stu-id="4aeed-171">**Above the arm**</span></span><br>
        <span data-ttu-id="4aeed-172">1 – Schwierig, eine gute Handverfolgung zu verwalten</span><span class="sxs-lookup"><span data-stu-id="4aeed-172">1 - Difficult to maintain good hand tracking</span></span><br>
        <span data-ttu-id="4aeed-173">2 : Verursacht Benutzermüdigkeit aufgrund einer unnatürlichen Position</span><span class="sxs-lookup"><span data-stu-id="4aeed-173">2 - Causes user fatigue because of unnatural position</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="4aeed-174">![Über den Fingern](images/AboveFingers.gif)</span><span class="sxs-lookup"><span data-stu-id="4aeed-174">![Above fingers](images/AboveFingers.gif)</span></span><br>
        <span data-ttu-id="4aeed-175">**Über den Fingern**</span><span class="sxs-lookup"><span data-stu-id="4aeed-175">**Above fingers**</span></span><br>
        <span data-ttu-id="4aeed-176">1 – Handermüdung aufgrund der langen Handhaltung</span><span class="sxs-lookup"><span data-stu-id="4aeed-176">1 - Hand fatigue because of holding out hand for a long time</span></span><br>
        <span data-ttu-id="4aeed-177">2: Probleme bei der Handnachverfolgung an Index- und Mittelfingern</span><span class="sxs-lookup"><span data-stu-id="4aeed-177">2 - Hand tracking issues on index and middle fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="4aeed-178">![Obere Mittelfläche](images/handCenter.gif)</span><span class="sxs-lookup"><span data-stu-id="4aeed-178">![Above center palm](images/handCenter.gif)</span></span><br>
        <span data-ttu-id="4aeed-179">**Obere Mittelfläche**</span><span class="sxs-lookup"><span data-stu-id="4aeed-179">**Above-center palm**</span></span><br>
        <span data-ttu-id="4aeed-180">1– Probleme bei der Handnachverfolgung aufgrund von überlappenden Händen</span><span class="sxs-lookup"><span data-stu-id="4aeed-180">1 - Hand tracking issues because of overlapping hands</span></span><br>
        <span data-ttu-id="4aeed-181">2– Handermüdung aufgrund der langen Handhaltung für die Interaktion mit Menüs</span><span class="sxs-lookup"><span data-stu-id="4aeed-181">2 - Hand fatigue because of holding hands for long time to interact with menus</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="4aeed-182">![Fingerspitze oben ](images/TopFingerTip.gif) **Fingerspitze**</span><span class="sxs-lookup"><span data-stu-id="4aeed-182">![Top Fingertip](images/TopFingerTip.gif) **Top fingertip**</span></span><br>
        <span data-ttu-id="4aeed-183">1– Probleme mit der Handverfolgung</span><span class="sxs-lookup"><span data-stu-id="4aeed-183">1 - Hand tracking issues</span></span><br>
        <span data-ttu-id="4aeed-184">2– Handermüdung, wenn die Hand über dem normalen Zustand hält</span><span class="sxs-lookup"><span data-stu-id="4aeed-184">2 - Hand fatigue from holding hand above normal posture</span></span><br>
        <span data-ttu-id="4aeed-185">3. Probleme beim Drücken von Schaltflächen mit anderen Fingern aufgrund von begrenztem Abstand zwischen den Fingern</span><span class="sxs-lookup"><span data-stu-id="4aeed-185">3 - Issues pressing buttons with other fingers by accident because of limited space between fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="4aeed-186">![Rückseite des Arms](images/BackOfTheArm.gif)</span><span class="sxs-lookup"><span data-stu-id="4aeed-186">![Back of the Arm](images/BackOfTheArm.gif)</span></span><br>
        <span data-ttu-id="4aeed-187">**Rückseite des Arms**</span><span class="sxs-lookup"><span data-stu-id="4aeed-187">**Back of the arm**</span></span><br>
        <span data-ttu-id="4aeed-188">1. Kann die Startschaltfläche aus Zufall auslösen</span><span class="sxs-lookup"><span data-stu-id="4aeed-188">1 - Can trigger home button by accident</span></span><br>
        <span data-ttu-id="4aeed-189">2 – Keine natürliche oder komfortable Position</span><span class="sxs-lookup"><span data-stu-id="4aeed-189">2 - Not a natural or comfortable position</span></span>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="4aeed-190">Handmenü im MRTK (Mixed Reality Toolkit) für Unity</span><span class="sxs-lookup"><span data-stu-id="4aeed-190">Hand menu in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="4aeed-191">**[MRTK stellt](https://github.com/Microsoft/MixedRealityToolkit-Unity)** Skripts und Beispielszenen für das Handmenü zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="4aeed-191">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and example scenes for the hand menu.</span></span> <span data-ttu-id="4aeed-192">Mit dem Solverskript HandConstraintPalmUp können Sie alle Objekte mit verschiedenen konfigurierbaren Optionen an die Hände anfügen.</span><span class="sxs-lookup"><span data-stu-id="4aeed-192">The HandConstraintPalmUp solver script allows you to attach any objects to the hands with various configurable options.</span></span> <span data-ttu-id="4aeed-193">Die Handmenübeispiele des MRTK enthalten nützliche Optionen wie flache Handfläche und Anvisanforderung, um eine falsche Aktivierung zu verhindern.</span><span class="sxs-lookup"><span data-stu-id="4aeed-193">MRTK's hand menu examples include useful options such as flat palm and gaze requirement for preventing false activation.</span></span>

* [<span data-ttu-id="4aeed-194">Hand Menu Documentations</span><span class="sxs-lookup"><span data-stu-id="4aeed-194">Hand Menu Documentations</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)
* [<span data-ttu-id="4aeed-195">Beispielszene für Handmenü</span><span class="sxs-lookup"><span data-stu-id="4aeed-195">Hand Menu Example Scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandMenuExamples.unity)

<span data-ttu-id="4aeed-196">Sie können Handmenübeispiele in der HoloLens 2 mit der MRTK Examples Hub-App ausprobieren.</span><span class="sxs-lookup"><span data-stu-id="4aeed-196">You can try hand menu examples in HoloLens 2 with MRTK Examples Hub app.</span></span>

* [<span data-ttu-id="4aeed-197">Handmenüszene im MRTK-Beispielhub</span><span class="sxs-lookup"><span data-stu-id="4aeed-197">Hand Menu Scene in MRTK Examples Hub</span></span>](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4?activetab=pivot:overviewtab)

<br>

---

## <a name="see-also"></a><span data-ttu-id="4aeed-198">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="4aeed-198">See also</span></span>

* [<span data-ttu-id="4aeed-199">Cursor</span><span class="sxs-lookup"><span data-stu-id="4aeed-199">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="4aeed-200">Handstrahl</span><span class="sxs-lookup"><span data-stu-id="4aeed-200">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="4aeed-201">Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="4aeed-201">Button</span></span>](button.md)
* [<span data-ttu-id="4aeed-202">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="4aeed-202">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="4aeed-203">Begrenzungsrahmen und App-Leiste</span><span class="sxs-lookup"><span data-stu-id="4aeed-203">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="4aeed-204">Manipulation</span><span class="sxs-lookup"><span data-stu-id="4aeed-204">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="4aeed-205">Handmenü</span><span class="sxs-lookup"><span data-stu-id="4aeed-205">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="4aeed-206">Nähemenü</span><span class="sxs-lookup"><span data-stu-id="4aeed-206">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="4aeed-207">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="4aeed-207">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="4aeed-208">Sprachbefehl</span><span class="sxs-lookup"><span data-stu-id="4aeed-208">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="4aeed-209">Tastatur</span><span class="sxs-lookup"><span data-stu-id="4aeed-209">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="4aeed-210">QuickInfo</span><span class="sxs-lookup"><span data-stu-id="4aeed-210">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="4aeed-211">Filmklappe</span><span class="sxs-lookup"><span data-stu-id="4aeed-211">Slate</span></span>](slate.md)
* [<span data-ttu-id="4aeed-212">Schieberegler</span><span class="sxs-lookup"><span data-stu-id="4aeed-212">Slider</span></span>](slider.md)
* [<span data-ttu-id="4aeed-213">Shader</span><span class="sxs-lookup"><span data-stu-id="4aeed-213">Shader</span></span>](shader.md)
* [<span data-ttu-id="4aeed-214">Billboarding und Tag-along</span><span class="sxs-lookup"><span data-stu-id="4aeed-214">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="4aeed-215">Anzeigen des Fortschritts</span><span class="sxs-lookup"><span data-stu-id="4aeed-215">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="4aeed-216">Oberflächenmagnetismus</span><span class="sxs-lookup"><span data-stu-id="4aeed-216">Surface magnetism</span></span>](surface-magnetism.md)