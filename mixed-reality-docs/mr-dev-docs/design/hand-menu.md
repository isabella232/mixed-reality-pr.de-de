---
title: Handmenü
description: Mithilfe von Hand Menüs können Benutzer schnell Hand anfügende Benutzeroberflächen für häufig verwendete Funktionen aktivieren.
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: Hand, Menü, Schaltfläche, schnell Zugriff, Layout, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens, mrtk, Mixed Reality Toolkit
ms.openlocfilehash: e222d792d883ccacc71b177fbde21979c8dfcc77
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "107299915"
---
# <a name="hand-menu"></a><span data-ttu-id="d5d1e-104">Handmenü</span><span class="sxs-lookup"><span data-stu-id="d5d1e-104">Hand menu</span></span>

![Ulnar Seitenposition](images/UX_Hero_HandMenu.jpg)

<span data-ttu-id="d5d1e-106">Das Menü "Hand" ist eines der einzig testen UX-Muster in hololens 2.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-106">The hand menu is one of the most unique UX patterns in HoloLens 2.</span></span> <span data-ttu-id="d5d1e-107">Mit dieser Option können Sie schnell Hand anfügende Benutzeroberflächen einrichten.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-107">It allows you to quickly bring up hand-attached UI.</span></span> <span data-ttu-id="d5d1e-108">Da es jederzeit zugänglich ist und leicht angezeigt und ausgeblendet werden kann, ist es hervorragend für schnelle Aktionen geeignet.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-108">Since it's accessible anytime and can be shown and hidden easily, it's great for quick actions.</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAg]

<span data-ttu-id="d5d1e-109">Sie finden unsere empfohlenen bewährten Methoden für die Arbeit mit Hand Menüs in der folgenden Liste.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-109">You'll find our recommended best practices for working with hand menus in the list below.</span></span> <span data-ttu-id="d5d1e-110">Sie finden auch eine Beispiel Szene, die das Hand Menü in [mrtk](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)demonstriert.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-110">You can also find an example scene demonstrating the hand menu in [MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu).</span></span>

<br>

---

## <a name="best-practices"></a><span data-ttu-id="d5d1e-111">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="d5d1e-111">Best practices</span></span>

<span data-ttu-id="d5d1e-112">**Anzahl von Schaltflächen klein halten**</span><span class="sxs-lookup"><span data-stu-id="d5d1e-112">**Keep the number of buttons small**</span></span> 

<span data-ttu-id="d5d1e-113">Aufgrund der engen Entfernung zwischen einem Hand gesperrten Menü und den Augen und der Tendenz, dass sich Benutzer jederzeit auf einen relativ kleinen visuellen Bereich konzentrieren können (der Teilnehmer Kegel ist ungefähr 10 Grad), empfiehlt es sich, die Anzahl der Schaltflächen gering zu halten.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-113">Because of the close distance between a hand-locked menu and the eyes, and the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), we recommend keeping the number of buttons small.</span></span> <span data-ttu-id="d5d1e-114">Basierend auf unserer Untersuchung funktioniert eine Spalte mit drei Schaltflächen gut, indem der gesamte Inhalt in der Ansicht (FOV) beibehalten wird, auch wenn ein Benutzer seine Hände in den Mittelpunkt des FOV verschiebt.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-114">Based on our exploration, one column with three buttons works well by keeping all the content within the field of view (FOV) even when a user moves their hands to the center of the FOV.</span></span> 

<span data-ttu-id="d5d1e-115">**Verwenden des Hand Menüs für die schnelle Aktion**</span><span class="sxs-lookup"><span data-stu-id="d5d1e-115">**Use hand menu for quick action**</span></span> 

<span data-ttu-id="d5d1e-116">Das Auslösen eines Arm und das Aufrechterhalten der Position könnte leicht eine Arm-Müdigkeit verursachen.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-116">Raising an arm and maintaining the position could easily cause arm fatigue.</span></span> <span data-ttu-id="d5d1e-117">Verwenden Sie eine Hand gesperrte Methode für das Menü, das eine kurze Interaktion erfordert.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-117">Use a hand-locked method for the menu requiring a short interaction.</span></span> <span data-ttu-id="d5d1e-118">Wenn Ihr Menü Komplex ist und erweiterte Interaktions Zeiten erfordert, sollten Sie stattdessen "World-Locked" oder "Body-Lock" verwenden.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-118">If your menu is complex and requires extended interaction times, consider using world-locked or body-locked instead.</span></span> 

<span data-ttu-id="d5d1e-119">**Schaltflächen-/Panel-Winkel**</span><span class="sxs-lookup"><span data-stu-id="d5d1e-119">**Button / Panel angle**</span></span>

<span data-ttu-id="d5d1e-120">Menüs sollten in der gegenüberliegenden Schulter und der Mitte des Kopfes angezeigt werden: Dadurch kann eine natürliche Handbewegung mit dem Menü mit umgekehrter Hand interagieren und alle umständlichen oder unbequemen Handpositionen beim Berühren von Schaltflächen vermeiden.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-120">Menus should billboard towards the opposite shoulder and middle of the head: This allows a natural hand move to interact with the menu with the opposite hand and avoids any awkward or uncomfortable hand positions when touching buttons.</span></span> 

<span data-ttu-id="d5d1e-121">**In Erwägung gezogen, ein-oder frei Hand Vorgang zu unterstützen.**</span><span class="sxs-lookup"><span data-stu-id="d5d1e-121">**Consider supporting one-handed or hands-free operation**</span></span>

<span data-ttu-id="d5d1e-122">Gehen Sie nicht davon aus, dass beide Hände des Benutzers immer verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-122">Don't assume both of the user's hands are always available.</span></span> <span data-ttu-id="d5d1e-123">Stellen Sie sich einen großen Bereich von Kontexten vor, wenn eine oder beide Hände nicht verfügbar sind, und stellen Sie sicher, dass Ihre Entwurfs Konten für diese Situationen sind.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-123">Consider a wide range of contexts when one or both hands aren't available, and make sure your design accounts for those situations.</span></span> <span data-ttu-id="d5d1e-124">Um ein eindimensionales Menü zu unterstützen, können Sie versuchen, die Menü Platzierung von Hand gesperrt auf die gesperrte Seite zu übertragen, wenn die Hand kippt (in den Blättern).</span><span class="sxs-lookup"><span data-stu-id="d5d1e-124">To support a one-handed hand menu, you can try transitioning the menu placement from hand-locked to world-locked when the hand flips (goes palm down).</span></span> <span data-ttu-id="d5d1e-125">Bei praktischen Szenarios sollten Sie einen Sprachbefehl verwenden, um das Menü "Hand" aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-125">For hands-free scenarios, consider using a voice command to invoke the hand menu.</span></span>

<span data-ttu-id="d5d1e-126">**Vermeiden Sie das Hinzufügen von Schaltflächen in der Nähe der Hand**</span><span class="sxs-lookup"><span data-stu-id="d5d1e-126">**Avoid adding buttons near the wrist (system home button)**</span></span>

<span data-ttu-id="d5d1e-127">Wenn die Menü Schaltflächen "Hand" zu nah an der Start Schaltfläche platziert werden, kann Sie versehentlich bei der Interaktion mit dem Menü "Hand" auftreten.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-127">If the hand menu buttons are placed too close to the home button, it may accidentally trigger while interacting with the hand menu.</span></span>

<br>

## <a name="hand-menu-with-large-and-complex-ui-controls"></a><span data-ttu-id="d5d1e-128">Hand Menü mit großen und komplexen UI-Steuerelementen</span><span class="sxs-lookup"><span data-stu-id="d5d1e-128">Hand menu with large and complex UI controls</span></span>

<img src="images/HandMenu_SizeExample.png" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<span data-ttu-id="d5d1e-129">Es wird empfohlen, die Anzahl der Schaltflächen oder UI-Steuerelemente in Hand anfügenden Menüs einzuschränken.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-129">It's recommended to limit the number of buttons or UI controls on hand-attached menus.</span></span> <span data-ttu-id="d5d1e-130">Dies liegt daran, dass die erweiterte Interaktion mit einer großen Anzahl von Benutzeroberflächen Elementen eine Arm-Müdigkeit verursachen kann.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-130">This is because extended interaction with a large number of UI elements can cause arm fatigue.</span></span> <span data-ttu-id="d5d1e-131">Wenn Ihre Benutzerumgebung ein großes Menü erfordert, stellen Sie dem Benutzer eine einfache Möglichkeit zur Verfügung, um das Menü zu sperren.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-131">If your experience requires a large menu, provide an easy way for the user to world lock the menu.</span></span> <span data-ttu-id="d5d1e-132">Eine Methode, die wir empfehlen, ist die Welt, in der das Menü angezeigt wird, wenn das Handumdrehen vom Benutzer gelöscht oder umgekehrt wird.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-132">One technique we recommend is to world-lock then menu when the hand drops or flips away from the user.</span></span> <span data-ttu-id="d5d1e-133">Ein zweites Verfahren besteht darin, dem Benutzer zu gestatten, das Menü direkt mit der anderen Seite zu übernehmen.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-133">A second technique is to allow the user to directly grab the menu with the other hand.</span></span> <span data-ttu-id="d5d1e-134">Wenn der Benutzer das Menü loslässt, sollte das Menü auf der ganzen Welt gesperrt werden.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-134">When the user releases the menu, the menu should world lock.</span></span> <span data-ttu-id="d5d1e-135">Auf diese Weise kann ein Benutzer über einen längeren Zeitraum bequem und sicher mit verschiedenen Benutzeroberflächen Elementen interagieren.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-135">This way, a user can interact with various UI elements comfortably and confidently over an extended period of time.</span></span> 

<span data-ttu-id="d5d1e-136">Wenn das Menü weltweit gesperrt ist, stellen Sie sicher, dass Sie eine Möglichkeit zum Verschieben des Menüs und zum Schließen des Menüs haben, wenn es nicht mehr benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-136">When the menu is world-locked, make sure to provide a way to move the menu, and close the menu when it's no longer needed.</span></span> <span data-ttu-id="d5d1e-137">Legen Sie die Position des Menüs durch Bereitstellen von Handles auf den Seiten oder dem oberen Rand des Menüs auf den</span><span class="sxs-lookup"><span data-stu-id="d5d1e-137">Make the menu movable by providing handles on the sides or top of menu.</span></span> <span data-ttu-id="d5d1e-138">Fügen Sie eine Schaltfläche Schließen hinzu, um das Schließen des Menüs zuzulassen.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-138">Add a close button to allow the menu to close.</span></span> <span data-ttu-id="d5d1e-139">Hiermit wird das erneute Anfügen des Menüs an die Hand ermöglicht, wenn der Benutzer dem Benutzer die Hand gibt.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-139">Allow for the menu to reattach to the hand when the user hand faces the user.</span></span> <span data-ttu-id="d5d1e-140">Außerdem wird empfohlen, dass die Benutzer ihre Hand betrachten, um falsche Aktivierungen zu verhindern (siehe unten).</span><span class="sxs-lookup"><span data-stu-id="d5d1e-140">We also recommend requiring that the users gaze at their hand to prevent false activations (see below).</span></span>

<span data-ttu-id="d5d1e-141">**Großes Menü, das ein Problem mit der Benutzerfreundlichkeit anzeigt**</span><span class="sxs-lookup"><span data-stu-id="d5d1e-141">**Large menu that shows a usability issue**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AOPx]

<span data-ttu-id="d5d1e-142">**Weltweit gesperrtes Menü im Handschlag**</span><span class="sxs-lookup"><span data-stu-id="d5d1e-142">**World-locked menu on hand drop**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AGZi]

<span data-ttu-id="d5d1e-143">**Manueller Abruf & Pullvorgang an der Welt: Sperren Sie das Menü.**</span><span class="sxs-lookup"><span data-stu-id="d5d1e-143">**Manual grab & pull to world-lock the menu**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAf]

## <a name="how-to-prevent-false-activation"></a><span data-ttu-id="d5d1e-144">Verhindern der falsch Aktivierung</span><span class="sxs-lookup"><span data-stu-id="d5d1e-144">How to prevent false activation</span></span>

<span data-ttu-id="d5d1e-145">Wenn Sie nur die Option "Palm-up" als Ereignis verwenden, um das Menü "Hand" zu starten, wird es möglicherweise versehentlich angezeigt, wenn Sie es nicht benötigen (falsch positiv), da Personen die Hände absichtlich (für die Kommunikation und Objekt Bearbeitung) und unbeabsichtigt verschieben.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-145">If you use just palm-up as an event to trigger the hand menu, it may accidentally appear when you don't need it (false-positive), because people move their hands both intentionally (for communication and object manipulation) and unintentionally.</span></span> <span data-ttu-id="d5d1e-146">Um falsche Aktivierungen zu reduzieren, fügen Sie neben dem Palm-up-Ereignis einen zusätzlichen Schritt hinzu, um das Menü "Hand" (z. b. vollständig geöffnete Finger) aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-146">To reduce false activations, add an extra step besides the palm-up event to invoke the hand menu (such as fully opened fingers, or the user intentionally gazing at their hand).</span></span>

<span data-ttu-id="d5d1e-147">**Flache Palme erforderlich**</span><span class="sxs-lookup"><span data-stu-id="d5d1e-147">**Require Flat Palm**</span></span>

<span data-ttu-id="d5d1e-148">Wenn Sie eine flache öffnende Hand benötigen, können Sie die falsche Aktivierung verhindern, die auftreten kann, wenn der Benutzer während der Kommunikation innerhalb einer Umgebung Objekte oder Gesten bearbeitet.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-148">By requiring a flat open hand, you can prevent false activation that might occur as the user manipulates objects or gestures while communicating within an environment.</span></span> 

<span data-ttu-id="d5d1e-149">**Blick erfordern**</span><span class="sxs-lookup"><span data-stu-id="d5d1e-149">**Require Gaze**</span></span>

<span data-ttu-id="d5d1e-150">Wenn der Benutzer die Hand betrachten muss (entweder mit dem Augenblick oder dem Kopf), werden falsche Aktivierungen verhindert, da der Benutzer die Aufmerksamkeit auf die Hand als sekundären Aktivierungs Schritt lenken muss (mit einem anpassbaren Entfernungs Schwellenwert, der für den Benutzerkomfort verwendet wird).</span><span class="sxs-lookup"><span data-stu-id="d5d1e-150">By requiring the user to gaze at their hand (either with eye gaze or head gaze), it prevents false activations because of the user having to direct their attention to the hand as a secondary activation step (with a tunable distance threshold used to allow for user comfort).</span></span>  

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Asn4]

---

## <a name="hand-menu-placement-best-practices"></a><span data-ttu-id="d5d1e-151">Bewährte Methoden für die Platzierung von Hand Menüs</span><span class="sxs-lookup"><span data-stu-id="d5d1e-151">Hand menu placement best practices</span></span>

<span data-ttu-id="d5d1e-152">Bei der menschlichen Anatomie ist der ulnar-Nerv ein Nerv, der in der Nähe des Ulna-knochenverläuft.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-152">In human anatomy, the ulnar nerve is a nerve that runs near the ulna bone.</span></span> <span data-ttu-id="d5d1e-153">Die Ulna ist ein langer Ring in der forearm, der vom Bogen zum kleinsten Finger reicht.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-153">The ulna is a long bone found in the forearm that stretches from the elbow to the smallest finger.</span></span>

<span data-ttu-id="d5d1e-154">Im folgenden finden Sie zwei empfohlene Platzierungen, die auf unseren Explorationen basieren:</span><span class="sxs-lookup"><span data-stu-id="d5d1e-154">Below are two recommended placements based on our explorations:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="d5d1e-155">![Ularies Seitenposition innerhalb der Palme](images/UlnarSideHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="d5d1e-155">![Ulnar side hand location inside palm](images/UlnarSideHandMenu.gif)</span></span><br>
        <span data-ttu-id="d5d1e-156">**Ein. ulnar in der Palme**</span><span class="sxs-lookup"><span data-stu-id="d5d1e-156">**A. Ulnar inside palm**</span></span><br>
        <span data-ttu-id="d5d1e-157">Diese Position ist zuverlässig, da die Hände einander nicht überlappen.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-157">This position is reliable because the hands don't overlap each other.</span></span> <span data-ttu-id="d5d1e-158">Dies ist wichtig für die genaue Erkennung und Nachverfolgung von Hand.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-158">This is critical for accurate hand detection and tracking.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="d5d1e-159">![Ulnar Seitenposition oberhalb der Hand](images/UlnarAboveHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="d5d1e-159">![Ulnar side hand location above hand](images/UlnarAboveHandMenu.gif)</span></span><br>
        <span data-ttu-id="d5d1e-160">**B. ulnar oberhalb der Hand**</span><span class="sxs-lookup"><span data-stu-id="d5d1e-160">**B. Ulnar above hand**</span></span><br>
        <span data-ttu-id="d5d1e-161">Dieser Speicherort ist für Benutzer praktisch, da Sie den Arm nicht zu groß machen müssen, um mit dem Hand Menü zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-161">This location is comfortable for users because they don't need to raise their arm too much to interact with the hand menu.</span></span> <span data-ttu-id="d5d1e-162">Es empfiehlt sich, die Menüs **13 cm** oberhalb der Palme zu platzieren und die Schaltflächen innerhalb der ulnar-Palme auszurichten.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-162">We recommend placing menus **13 cm** above the palm and align the buttons inside the ulnar palm.</span></span> [<span data-ttu-id="d5d1e-163">Weitere Informationen zur optimalen Schaltflächen Größe</span><span class="sxs-lookup"><span data-stu-id="d5d1e-163">Read more about the optimal button size</span></span>](interactable-object.md)<br>
        <br>
        <span data-ttu-id="d5d1e-164">Aus technischen Gründen wird dieser Speicherort mit einer erforderlichen Implementierung empfohlen: der Entwickler muss das Menü fixieren, wenn die gegenüberliegende Seite des Benutzers in der Nähe der Interaktion mit dem Benutzer steht.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-164">For technical reasons, we recommend this location with one required implementation: the developer will need to freeze the menu once the user's opposite hand gets close to interacting with it.</span></span> <span data-ttu-id="d5d1e-165">Dadurch wird die überlappende Hände von jitterität vermieden, und es ist auch möglich, dass die Schaltflächen schneller ausgerichtet werden.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-165">This will avoid jitteriness from overlapping hands and also allows for a faster targeting of the buttons.</span></span><br>
        <br>
        <span data-ttu-id="d5d1e-166">Hololens 2 Kameras identifizieren Hände genau, wenn Sie voneinander getrennt sind.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-166">HoloLens 2 cameras identify hands accurately when they're separate from each other.</span></span> <span data-ttu-id="d5d1e-167">Überlappende Hände können dazu führen, dass Hand Menüs von der Ankerposition Weg wechseln.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-167">Any overlapping hands can cause hand menus move away from the anchor location.</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="menu-positions-that-arent-recommended"></a><span data-ttu-id="d5d1e-168">Nicht empfohlene Menü Positionen</span><span class="sxs-lookup"><span data-stu-id="d5d1e-168">Menu positions that aren't recommended</span></span>

<span data-ttu-id="d5d1e-169">Wir haben die Benutzer Forschung mit verschiedenen Menüs und Standorten durchgeführt. die folgenden Menü Positionen werden **nicht empfohlen**. Sie finden die Nachteile der einzelnen nachfolgenden Nachforschungen:</span><span class="sxs-lookup"><span data-stu-id="d5d1e-169">We have done user research with different menus layouts and locations, the following menu locations are **NOT recommended**, find the cons of each study below:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="d5d1e-170">![Oberhalb von Arm](images/AboveArm.gif)</span><span class="sxs-lookup"><span data-stu-id="d5d1e-170">![Above arm](images/AboveArm.gif)</span></span><br>
        <span data-ttu-id="d5d1e-171">**Oberhalb der Arm**</span><span class="sxs-lookup"><span data-stu-id="d5d1e-171">**Above the arm**</span></span><br>
        <span data-ttu-id="d5d1e-172">1: schwer zu verwaltender guter Hand Verfolgung</span><span class="sxs-lookup"><span data-stu-id="d5d1e-172">1 - Difficult to maintain good hand tracking</span></span><br>
        <span data-ttu-id="d5d1e-173">2: verursacht eine Benutzer Müdigkeit aufgrund der unnatürlichen Position.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-173">2 - Causes user fatigue because of unnatural position</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="d5d1e-174">![Über Fingern](images/AboveFingers.gif)</span><span class="sxs-lookup"><span data-stu-id="d5d1e-174">![Above fingers](images/AboveFingers.gif)</span></span><br>
        <span data-ttu-id="d5d1e-175">**Über Fingern**</span><span class="sxs-lookup"><span data-stu-id="d5d1e-175">**Above fingers**</span></span><br>
        <span data-ttu-id="d5d1e-176">eine Hand Müdigkeit aufgrund einer langen Zeitüberschreitung</span><span class="sxs-lookup"><span data-stu-id="d5d1e-176">1 - Hand fatigue because of holding out hand for a long time</span></span><br>
        <span data-ttu-id="d5d1e-177">2-Hand-nach Verfolgungs Probleme bei Index-und mittelfingern</span><span class="sxs-lookup"><span data-stu-id="d5d1e-177">2 - Hand tracking issues on index and middle fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="d5d1e-178">![Oberhalb der mittleren Palme](images/handCenter.gif)</span><span class="sxs-lookup"><span data-stu-id="d5d1e-178">![Above center palm](images/handCenter.gif)</span></span><br>
        <span data-ttu-id="d5d1e-179">**Oberhalb-Mittelpunkt**</span><span class="sxs-lookup"><span data-stu-id="d5d1e-179">**Above-center palm**</span></span><br>
        <span data-ttu-id="d5d1e-180">1-Hand-nach Verfolgungs Probleme aufgrund von überlappenden Händen</span><span class="sxs-lookup"><span data-stu-id="d5d1e-180">1 - Hand tracking issues because of overlapping hands</span></span><br>
        <span data-ttu-id="d5d1e-181">2-Hand-Müdigkeit aufgrund der langen Zeit für die Interaktion mit Menüs</span><span class="sxs-lookup"><span data-stu-id="d5d1e-181">2 - Hand fatigue because of holding hands for long time to interact with menus</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="d5d1e-182">![Top Fingertip ](images/TopFingerTip.gif) **Top Fingertip**</span><span class="sxs-lookup"><span data-stu-id="d5d1e-182">![Top Fingertip](images/TopFingerTip.gif) **Top fingertip**</span></span><br>
        <span data-ttu-id="d5d1e-183">1-Hand-nach Verfolgungs Probleme</span><span class="sxs-lookup"><span data-stu-id="d5d1e-183">1 - Hand tracking issues</span></span><br>
        <span data-ttu-id="d5d1e-184">2-Hand Müdigkeit von Hand über normalem Status</span><span class="sxs-lookup"><span data-stu-id="d5d1e-184">2 - Hand fatigue from holding hand above normal posture</span></span><br>
        <span data-ttu-id="d5d1e-185">3: Fehler beim Drücken von Schaltflächen mit anderen Fingern aufgrund von eingeschränktem Leerraum zwischen Fingern.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-185">3 - Issues pressing buttons with other fingers by accident because of limited space between fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="d5d1e-186">![Zurück zum Arm](images/BackOfTheArm.gif)</span><span class="sxs-lookup"><span data-stu-id="d5d1e-186">![Back of the Arm](images/BackOfTheArm.gif)</span></span><br>
        <span data-ttu-id="d5d1e-187">**Zurück zum Arm**</span><span class="sxs-lookup"><span data-stu-id="d5d1e-187">**Back of the arm**</span></span><br>
        <span data-ttu-id="d5d1e-188">1: Start Schaltfläche nach einem Unfall</span><span class="sxs-lookup"><span data-stu-id="d5d1e-188">1 - Can trigger home button by accident</span></span><br>
        <span data-ttu-id="d5d1e-189">2-keine natürliche oder bequeme Position</span><span class="sxs-lookup"><span data-stu-id="d5d1e-189">2 - Not a natural or comfortable position</span></span>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="d5d1e-190">Hand Menü im mrtk (Mixed Reality Toolkit) für Unity</span><span class="sxs-lookup"><span data-stu-id="d5d1e-190">Hand menu in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="d5d1e-191">**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** stellt Skripts und Beispiel Szenen für das Hand Menü bereit.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-191">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and example scenes for the hand menu.</span></span> <span data-ttu-id="d5d1e-192">Das handeinschränintpalmup-Solver-Skript ermöglicht es Ihnen, alle Objekte mit verschiedenen konfigurierbaren Optionen an die Hände anzufügen.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-192">The HandConstraintPalmUp solver script allows you to attach any objects to the hands with various configurable options.</span></span> <span data-ttu-id="d5d1e-193">Die Hand Menü Beispiele von mrtk enthalten nützliche Optionen, wie z. b. eine flache Palme und eine Blick Anforderung zum Verhindern der falschen Aktivierung.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-193">MRTK's hand menu examples include useful options such as flat palm and gaze requirement for preventing false activation.</span></span>

* [<span data-ttu-id="d5d1e-194">Hand Menü-Documentationen</span><span class="sxs-lookup"><span data-stu-id="d5d1e-194">Hand Menu Documentations</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)
* [<span data-ttu-id="d5d1e-195">Beispiel Szene für Hand Menü</span><span class="sxs-lookup"><span data-stu-id="d5d1e-195">Hand Menu Example Scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandMenuExamples.unity)

<span data-ttu-id="d5d1e-196">Sie können die Menü Beispiele in hololens 2 mit der mrtk examples Hub-App ausprobieren.</span><span class="sxs-lookup"><span data-stu-id="d5d1e-196">You can try hand menu examples in HoloLens 2 with MRTK Examples Hub app.</span></span>

* [<span data-ttu-id="d5d1e-197">Hand Menü Szene im mrtk-Beispiel-Hub</span><span class="sxs-lookup"><span data-stu-id="d5d1e-197">Hand Menu Scene in MRTK Examples Hub</span></span>](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4?activetab=pivot:overviewtab)

<br>

---

## <a name="see-also"></a><span data-ttu-id="d5d1e-198">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d5d1e-198">See also</span></span>

* [<span data-ttu-id="d5d1e-199">Cursor</span><span class="sxs-lookup"><span data-stu-id="d5d1e-199">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="d5d1e-200">Handstrahl</span><span class="sxs-lookup"><span data-stu-id="d5d1e-200">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="d5d1e-201">Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="d5d1e-201">Button</span></span>](button.md)
* [<span data-ttu-id="d5d1e-202">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="d5d1e-202">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="d5d1e-203">Begrenzungsrahmen und App-Leiste</span><span class="sxs-lookup"><span data-stu-id="d5d1e-203">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="d5d1e-204">Manipulation</span><span class="sxs-lookup"><span data-stu-id="d5d1e-204">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="d5d1e-205">Handmenü</span><span class="sxs-lookup"><span data-stu-id="d5d1e-205">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="d5d1e-206">Nähemenü</span><span class="sxs-lookup"><span data-stu-id="d5d1e-206">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="d5d1e-207">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="d5d1e-207">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="d5d1e-208">Sprachbefehl</span><span class="sxs-lookup"><span data-stu-id="d5d1e-208">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="d5d1e-209">Tastatur</span><span class="sxs-lookup"><span data-stu-id="d5d1e-209">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="d5d1e-210">QuickInfo</span><span class="sxs-lookup"><span data-stu-id="d5d1e-210">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="d5d1e-211">Filmklappe</span><span class="sxs-lookup"><span data-stu-id="d5d1e-211">Slate</span></span>](slate.md)
* [<span data-ttu-id="d5d1e-212">Schieberegler</span><span class="sxs-lookup"><span data-stu-id="d5d1e-212">Slider</span></span>](slider.md)
* [<span data-ttu-id="d5d1e-213">Shader</span><span class="sxs-lookup"><span data-stu-id="d5d1e-213">Shader</span></span>](shader.md)
* [<span data-ttu-id="d5d1e-214">Billboarding und Tag-along</span><span class="sxs-lookup"><span data-stu-id="d5d1e-214">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="d5d1e-215">Anzeigen des Fortschritts</span><span class="sxs-lookup"><span data-stu-id="d5d1e-215">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="d5d1e-216">Oberflächenmagnetismus</span><span class="sxs-lookup"><span data-stu-id="d5d1e-216">Surface magnetism</span></span>](surface-magnetism.md)
