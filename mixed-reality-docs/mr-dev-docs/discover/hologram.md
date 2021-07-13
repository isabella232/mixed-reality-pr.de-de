---
title: Was ist ein Hologramm?
description: HoloLens können Sie dreidimensionale Hologramme und Objekte aus Licht und Sound anzeigen und mit ihnen interagieren, die in ihrer Umgebung erscheinen.
author: qianw211
ms.author: v-qianwen
ms.date: 07/09/2021
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, Hologramme, Design, Interaktion, Mixed Reality-Headset, Windows Mixed Reality-Headset, Was ist Augmented Reality?
ms.openlocfilehash: bef2c378dcba54d3ed3da33262153f35d72c3cba
ms.sourcegitcommit: b0b49ad27a0d09eb0a3d5df0c766bb4b7bbd8208
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2021
ms.locfileid: "113634331"
---
# <a name="what-is-a-hologram"></a><span data-ttu-id="fc785-104">Was ist ein Hologramm?</span><span class="sxs-lookup"><span data-stu-id="fc785-104">What is a hologram?</span></span>

<span data-ttu-id="fc785-105">HoloLens können Sie **Hologramme** anzeigen, bei denen es sich um Objekte aus Licht und Sound handelt, die in der Welt um Sie herum wie echte Objekte erscheinen.</span><span class="sxs-lookup"><span data-stu-id="fc785-105">HoloLens lets you view **holograms**, which are objects made of light and sound that appear in the world around you like real objects.</span></span> <span data-ttu-id="fc785-106">Hologramme können auf Ihre [Anverweise,](../design/gaze-and-commit.md) [Gesten](../design/gaze-and-commit.md#composite-gestures)und [Sprachbefehle](../design/voice-input.md)reagieren.</span><span class="sxs-lookup"><span data-stu-id="fc785-106">Holograms can respond to your [gaze](../design/gaze-and-commit.md), [gestures](../design/gaze-and-commit.md#composite-gestures), and [voice commands](../design/voice-input.md).</span></span> <span data-ttu-id="fc785-107">Sie können sogar mit [realen Oberflächen](../design/spatial-mapping.md) um Sie herum interagieren.</span><span class="sxs-lookup"><span data-stu-id="fc785-107">They can even interact with [real-world surfaces](../design/spatial-mapping.md) around you.</span></span> <span data-ttu-id="fc785-108">Hologramme sind digitale Objekte, die Teil Ihrer Welt sind.</span><span class="sxs-lookup"><span data-stu-id="fc785-108">Holograms are digital objects that are part of your world.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/MVXH5V8MVQo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

## <a name="device-support"></a><span data-ttu-id="fc785-109">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="fc785-109">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="fc785-110"><strong>Feature</strong></span><span class="sxs-lookup"><span data-stu-id="fc785-110"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="fc785-111"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1. Generation)</strong></a></span><span class="sxs-lookup"><span data-stu-id="fc785-111"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="fc785-112"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="fc785-112"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="fc785-113"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="fc785-113"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="fc785-114">Holograms</span><span class="sxs-lookup"><span data-stu-id="fc785-114">Holograms</span></span></td>
        <td><span data-ttu-id="fc785-115">✔️</span><span class="sxs-lookup"><span data-stu-id="fc785-115">✔️</span></span></td>
        <td><span data-ttu-id="fc785-116">✔️</span><span class="sxs-lookup"><span data-stu-id="fc785-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

<br>

---

## <a name="a-hologram-is-made-of-light-and-sound"></a><span data-ttu-id="fc785-117">Ein Hologramm besteht aus Licht und Sound.</span><span class="sxs-lookup"><span data-stu-id="fc785-117">A hologram is made of light and sound</span></span>

### <a name="light"></a><span data-ttu-id="fc785-118">Hell</span><span class="sxs-lookup"><span data-stu-id="fc785-118">Light</span></span>

<span data-ttu-id="fc785-119">Die Hologramme, die HoloLens [gerendert](../develop/platform-capabilities-and-apis/rendering.md) werden, werden im holografischen Frame direkt vor den Augen der Benutzer angezeigt.</span><span class="sxs-lookup"><span data-stu-id="fc785-119">The holograms that HoloLens [renders](../develop/platform-capabilities-and-apis/rendering.md) appear in the holographic frame directly in front of users' eyes.</span></span> <span data-ttu-id="fc785-120">Hologramme Ihrer Welt Licht hinzufügen, was bedeutet, dass Sie sowohl das Licht von der Anzeige als auch das Licht aus Ihrer Umgebung sehen.</span><span class="sxs-lookup"><span data-stu-id="fc785-120">Holograms add light to your world, which means that you see both the light from the display and the light from your surrounding world.</span></span> <span data-ttu-id="fc785-121">Da HoloLens eine additive Anzeige verwendet, die Licht hinzufügt, wird die schwarze Farbe transparent gerendert.</span><span class="sxs-lookup"><span data-stu-id="fc785-121">Since HoloLens uses an additive display that adds light, the black color will be rendered transparent.</span></span> 

<span data-ttu-id="fc785-122">Hologramme können sehr unterschiedliche Darstellungen und Verhaltensweisen aufweisen.</span><span class="sxs-lookup"><span data-stu-id="fc785-122">Holograms can have very different appearances and behaviors.</span></span> <span data-ttu-id="fc785-123">Einige sind realistisch und solide, während andere zierlich und ätherisch sind.</span><span class="sxs-lookup"><span data-stu-id="fc785-123">Some are realistic and solid, and others are cartoonish and ethereal.</span></span> <span data-ttu-id="fc785-124">Sie können Hologramme verwenden, um Features in Ihrer Umgebung hervorzuheben oder als Elemente in der Benutzeroberfläche Ihrer App zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="fc785-124">You can use holograms to highlight features in your environment or use them as elements in your app's user interface.</span></span>

![Hände, die ein Hologramm bearbeiten](images/hologram-hands-940px.jpg)

### <a name="sound"></a><span data-ttu-id="fc785-126">Sound</span><span class="sxs-lookup"><span data-stu-id="fc785-126">Sound</span></span>

<span data-ttu-id="fc785-127">Hologramme können auch [Sounds](../design/spatial-sound.md)erzeugen, die von einem bestimmten Ort in Ihrer Umgebung stammen.</span><span class="sxs-lookup"><span data-stu-id="fc785-127">Holograms can also produce [sounds](../design/spatial-sound.md), which appear to come from a specific place in your environment.</span></span> <span data-ttu-id="fc785-128">Bei HoloLens kommt der Sound von zwei Lautsprechern, die sich direkt über Ihrem Gerät befinden.</span><span class="sxs-lookup"><span data-stu-id="fc785-128">On HoloLens, sound comes from two speakers that are located directly above your ears.</span></span> <span data-ttu-id="fc785-129">Wie die holografischen Displays sind die Lautsprecher additiv, was neue Sounds einführt, ohne die Sounds aus Ihrer Umgebung zu blockieren.</span><span class="sxs-lookup"><span data-stu-id="fc785-129">Same as the holographic displays, the speakers are additive, introducing new sounds without blocking the sounds from your environment.</span></span>

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a><span data-ttu-id="fc785-130">Ein Hologramm kann in der Welt platziert oder zusammen mit Ihnen versehen werden.</span><span class="sxs-lookup"><span data-stu-id="fc785-130">A hologram can be placed in the world or tag along with you</span></span>

<span data-ttu-id="fc785-131">Wenn Sie über eine feste Position für ein Hologramm verfügen, können Sie es genau an diesem Punkt auf der Welt [platzieren.](../design/coordinate-systems.md)</span><span class="sxs-lookup"><span data-stu-id="fc785-131">When you have a fixed location for a hologram, you can [place](../design/coordinate-systems.md) it precisely at that point in the world.</span></span> <span data-ttu-id="fc785-132">Während Sie sich bewegen, erscheint das Hologramm wie ein physisches Objekt, basierend auf der Welt um Sie herum, stationär.</span><span class="sxs-lookup"><span data-stu-id="fc785-132">As you walk around, the hologram appears stationary based on the world around you, just like a physical object.</span></span> <span data-ttu-id="fc785-133">Wenn Sie einen [Raumanker](../design/coordinate-systems.md#spatial-anchors) verwenden, um das Objekt anzuheften, kann sich das System sogar merken, wo Sie es verlassen haben, wenn Sie später zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="fc785-133">If you use a [spatial anchor](../design/coordinate-systems.md#spatial-anchors) to pin the object, the system can even remember where you left it when you come back later.</span></span>

![Zwei Personen, die Microsoft Dynamics 365 Layout in einem Einzelhandelsbereich verwenden](images/HLS19_retailLayoutHologram_001-940px.jpg)

<span data-ttu-id="fc785-135">Einige Hologramme folgen stattdessen dem Benutzer.</span><span class="sxs-lookup"><span data-stu-id="fc785-135">Some holograms follow the user instead.</span></span> <span data-ttu-id="fc785-136">Sie positionieren sich basierend auf dem Benutzer.</span><span class="sxs-lookup"><span data-stu-id="fc785-136">They position themselves based on the user.</span></span> <span data-ttu-id="fc785-137">Sie können ein Hologramm mit sich bringen und es dann an der Wand platzieren, sobald Sie in einen anderen Raum gelangen.</span><span class="sxs-lookup"><span data-stu-id="fc785-137">You can choose to bring a hologram with you, and then place it on the wall once you get to another room.</span></span>

<span data-ttu-id="fc785-138">**Empfohlene Methoden**</span><span class="sxs-lookup"><span data-stu-id="fc785-138">**Best practices**</span></span>

* <span data-ttu-id="fc785-139">Einige Szenarien erfordern, dass Hologramme während der gesamten Benutzeroberfläche leicht erkennbar oder sichtbar bleiben.</span><span class="sxs-lookup"><span data-stu-id="fc785-139">Some scenarios demand that holograms remain easily discoverable or visible throughout the experience.</span></span> <span data-ttu-id="fc785-140">Es gibt zwei übergeordnete Ansätze für diese Art der Positionierung.</span><span class="sxs-lookup"><span data-stu-id="fc785-140">There are two high-level approaches to this kind of positioning.</span></span> <span data-ttu-id="fc785-141">Wir nennen sie **display-locked** und **body-locked**.</span><span class="sxs-lookup"><span data-stu-id="fc785-141">Let's call them **display-locked** and **body-locked**.</span></span>
   * <span data-ttu-id="fc785-142">**Anzeigesperren von Inhalten** sind für das Anzeigegerät gesperrt.</span><span class="sxs-lookup"><span data-stu-id="fc785-142">**Display-locked** content is locked to the display device.</span></span> <span data-ttu-id="fc785-143">Diese Art von Inhalt ist aus verschiedenen Gründen schwierig, einschließlich eines unnatürlichen Gefühls der "Klammerfähigkeit", das viele Benutzer frustriert macht und sie "abwaschen" möchte.</span><span class="sxs-lookup"><span data-stu-id="fc785-143">This type of content is tricky for several reasons, including an unnatural feeling of "clingyness" that makes many users frustrated and wanting to "shake it off."</span></span> <span data-ttu-id="fc785-144">Im Allgemeinen haben Designer es besser gefunden, Anzeigesperren von Inhalten zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="fc785-144">In general, designers have found it better to avoid display-locking content.</span></span>
   * <span data-ttu-id="fc785-145">**Textgesperrte** Inhalte können weitaus verzeihlicher sein.</span><span class="sxs-lookup"><span data-stu-id="fc785-145">**Body-locked** content can be far more forgiving.</span></span> <span data-ttu-id="fc785-146">Body-Locking ist, wenn Sie ein Hologramm an den Körper oder anvisierungsvektor des Benutzers im 3D-Raum anbinden.</span><span class="sxs-lookup"><span data-stu-id="fc785-146">Body-locking is when you tether a hologram to the user's body or gaze vector in 3D space.</span></span> <span data-ttu-id="fc785-147">Viele Erfahrungen haben ein Körpersperrverhalten eingeführt, bei dem das Hologramm dem Anvieren des Benutzers folgt, wodurch der Benutzer seinen Körper drehen und sich durch den Raum bewegen kann, ohne das Hologramm zu verlieren.</span><span class="sxs-lookup"><span data-stu-id="fc785-147">Many experiences have adopted a body-locking behavior where the hologram follows the user's gaze, which allows the user to rotate their body and move through space without losing the hologram.</span></span> <span data-ttu-id="fc785-148">Das Integrieren einer Verzögerung hilft den Hologrammbewegungen, sich natürlicher zu fühlen.</span><span class="sxs-lookup"><span data-stu-id="fc785-148">Incorporating a delay helps the hologram movements to feel more natural.</span></span> <span data-ttu-id="fc785-149">Einige kernige Benutzeroberflächen des Windows Holographic OS verwenden z. B. eine Variation der Körpersperrung, die dem Anvieren des Benutzers mit einer elastischen Verzögerung folgt, während der Benutzer den Kopf umdreht.</span><span class="sxs-lookup"><span data-stu-id="fc785-149">For example, some core UI of the Windows Holographic OS uses a variation on body-locking that follows the user's gaze with a gentle, elastic-like delay while the user turns their head.</span></span>
* <span data-ttu-id="fc785-150">Platzieren Sie das Hologramm in einer komfortablen Entfernung von etwa 1 bis 2 Metern vom Kopf.</span><span class="sxs-lookup"><span data-stu-id="fc785-150">Place the hologram at a comfortable viewing distance typically about 1-2 meters away from the head.</span></span>
* <span data-ttu-id="fc785-151">Lassen Sie zu, dass Elemente driften, wenn sie sich ständig im holografischen Frame bewegen müssen, oder ziehen Sie in Betracht, Ihren Inhalt auf eine Seite der Anzeige zu verschieben, wenn der Benutzer seine Ansicht ändert.</span><span class="sxs-lookup"><span data-stu-id="fc785-151">Allow elements to drift if they must be continually in the holographic frame, or consider moving your content to one side of the display when the user changes their point of view.</span></span> <span data-ttu-id="fc785-152">Weitere Informationen finden Sie in der [Markierungs- und](../design/billboarding-and-tag-along.md) Markierungsartilce.</span><span class="sxs-lookup"><span data-stu-id="fc785-152">For more information, see the [billboarding and tag-along](../design/billboarding-and-tag-along.md) artilce.</span></span>

<span data-ttu-id="fc785-153">**Platzieren von Hologrammen in der optimalen Zone – zwischen 1,25 m und 5 m**</span><span class="sxs-lookup"><span data-stu-id="fc785-153">**Place holograms in the optimal zone - between 1.25 m and 5 m**</span></span>

<span data-ttu-id="fc785-154">Zwei Meter sind die optimale Sichtdistanz.</span><span class="sxs-lookup"><span data-stu-id="fc785-154">Two meters is the most optimal viewing distance.</span></span> <span data-ttu-id="fc785-155">Die Benutzeroberfläche wird beeinträchtigt, wenn Sie näher als 1 Meter kommen.</span><span class="sxs-lookup"><span data-stu-id="fc785-155">The experience will start to degrade as you get closer than 1 meter.</span></span> <span data-ttu-id="fc785-156">Bei Entfernungen von weniger als 1 Meter sind Hologramme, die sich regelmäßig in die Tiefe bewegen, wahrscheinlich problematischer als hologramme.</span><span class="sxs-lookup"><span data-stu-id="fc785-156">At distances less than 1 meter, holograms that regularly move in depth are more likely to be problematic than stationary holograms.</span></span> <span data-ttu-id="fc785-157">Ziehen Sie in Betracht, Ihre Inhalte ordnungsgemäß zu beschneiden oder auszublenden, wenn sie sich zu nah kommen, damit Sie den Benutzer nicht in eine benutzerfreundliche Ansichtserfahrung eindrücken.</span><span class="sxs-lookup"><span data-stu-id="fc785-157">Consider gracefully clipping or fading out your content when it gets too close, so you don't jar the user into an unpleasant viewing experience.</span></span>

![Optimaler Abstand zum Platzieren von Hologrammen vom Benutzer.](images/distanceguiderendering-950px.png)

<br>

---

## <a name="a-hologram-interacts-with-you-and-your-world"></a><span data-ttu-id="fc785-159">Ein Hologramm interagiert mit Ihnen und Ihrer Welt.</span><span class="sxs-lookup"><span data-stu-id="fc785-159">A hologram interacts with you and your world</span></span>

<span data-ttu-id="fc785-160">Hologramme geht es nicht nur um Licht und Sound. Sie sind auch ein aktiver Teil Ihrer Welt.</span><span class="sxs-lookup"><span data-stu-id="fc785-160">Holograms aren't only about light and sound; they're also an active part of your world.</span></span> <span data-ttu-id="fc785-161">Sehen Sie sich ein Hologramm und eine Geste mit der Hand an, und ein Hologramm kann Ihnen folgen.</span><span class="sxs-lookup"><span data-stu-id="fc785-161">Gaze at a hologram and gesture with your hand, and a hologram can start to follow you.</span></span> <span data-ttu-id="fc785-162">Geben Sie einen Sprachbefehl, und das Hologramm kann antworten.</span><span class="sxs-lookup"><span data-stu-id="fc785-162">Give a voice command, and the hologram can reply.</span></span>

![Gruppe von Behördenhilfsmitarbeitern, die Microsoft HoloLens 2 verwenden, um an einem Windfarmentwicklungsprojekt zusammenzuarbeiten](images/HLS19_governmentUtilitiesHologram_001-940px.jpg)

<span data-ttu-id="fc785-164">Hologramme persönliche Interaktionen zu ermöglichen, die an anderer Stelle nicht möglich sind.</span><span class="sxs-lookup"><span data-stu-id="fc785-164">Holograms enable personal interactions that aren't possible elsewhere.</span></span> <span data-ttu-id="fc785-165">Da der HoloLens weiß, wo er sich auf der Welt befindet, kann ein holografisches Zeichen Sie direkt in den Augen betrachten und eine Konversation mit Ihnen beginnen.</span><span class="sxs-lookup"><span data-stu-id="fc785-165">Because the HoloLens knows where it is in the world, a holographic character can look at you directly in the eyes and start a conversation with you.</span></span>

<span data-ttu-id="fc785-166">Ein Hologramm kann auch mit Ihrer Umgebung interagieren.</span><span class="sxs-lookup"><span data-stu-id="fc785-166">A hologram can also interact with your surroundings.</span></span> <span data-ttu-id="fc785-167">Beispielsweise können Sie eine holografische Hüpfkugel über einer Tabelle platzieren.</span><span class="sxs-lookup"><span data-stu-id="fc785-167">For example, you can place a holographic bouncing ball above a table.</span></span> <span data-ttu-id="fc785-168">Beobachten Sie dann mit einem [Tippen in](../design/gaze-and-commit.md#composite-gestures)die Luft, wie der Ball abprallt, und machen Sie einen Sound, wenn er auf den Tisch trifft.</span><span class="sxs-lookup"><span data-stu-id="fc785-168">Then, with an [air tap](../design/gaze-and-commit.md#composite-gestures), watch the ball bounce, and make sound as it hits the table.</span></span>

<span data-ttu-id="fc785-169">Hologramme können auch von realen Objekten verdeckt werden.</span><span class="sxs-lookup"><span data-stu-id="fc785-169">Holograms can also be occluded by real-world objects.</span></span> <span data-ttu-id="fc785-170">Beispielsweise kann ein holografisches Zeichen durch eine Tür und hinter einer Wand außerhalb ihrer Sicht gehen.</span><span class="sxs-lookup"><span data-stu-id="fc785-170">For example, a holographic character might walk through a door and behind a wall, out of your sight.</span></span>

<span data-ttu-id="fc785-171">**Tipps für die Integration von Hologrammen und der realen Welt**</span><span class="sxs-lookup"><span data-stu-id="fc785-171">**Tips for integrating holograms and the real world**</span></span>

* <span data-ttu-id="fc785-172">Durch die Ausrichtung an den Gewichtungsregeln können Hologramme leichter aufeinander bezogen werden und sind leichter zu glauben.</span><span class="sxs-lookup"><span data-stu-id="fc785-172">Aligning to gravitational rules makes holograms easier to relate to and more believable.</span></span> <span data-ttu-id="fc785-173">Beispiel: Platzieren Sie einen holografischen Hund auf dem Boden & eine Vase auf dem Tisch, anstatt sie im Raum zu gleiten.</span><span class="sxs-lookup"><span data-stu-id="fc785-173">For example: Place a holographic dog on the ground & a vase on the table rather than have them floating in space.</span></span>
* <span data-ttu-id="fc785-174">Viele Designer haben festgestellt, dass sie zuverlässigere Hologramme integrieren können, indem sie einen "negativen Schatten" auf der Oberfläche erstellen, auf der sich das Hologramm befindet.</span><span class="sxs-lookup"><span data-stu-id="fc785-174">Many designers have found that they can integrate more believable holograms by creating a "negative shadow" on the surface that the hologram is sitting on.</span></span> <span data-ttu-id="fc785-175">Hierzu erstellen sie ein weiches Leuchtlicht auf dem Boden um das Hologramm und subtrahieren dann den "Schatten" vom Leuchtlicht.</span><span class="sxs-lookup"><span data-stu-id="fc785-175">They do this by creating a soft glow on the ground around the hologram and then subtracting the "shadow" from the glow.</span></span> <span data-ttu-id="fc785-176">Das weiche Leuchten lässt sich in das Licht aus der realen Welt integrieren.</span><span class="sxs-lookup"><span data-stu-id="fc785-176">The soft glow integrates with the light from the real world.</span></span> <span data-ttu-id="fc785-177">Der Schatten wird verwendet, um das Hologramm in der Umgebung zu vererbt.</span><span class="sxs-lookup"><span data-stu-id="fc785-177">The shadow is used to ground the hologram in the environment.</span></span>

<br>

---

:::row:::
    :::column:::
        ## <a name="a-hologram-is-what-bryou-can-dream-upbr"></a><span data-ttu-id="fc785-178">Ein Hologramm ist das, was</span><span class="sxs-lookup"><span data-stu-id="fc785-178">A hologram is what</span></span> <br><span data-ttu-id="fc785-179">Sie können sich einträumen.</span><span class="sxs-lookup"><span data-stu-id="fc785-179">you can dream up</span></span><br>
        <span data-ttu-id="fc785-180">Als holografischer Entwickler haben Sie die Möglichkeit, Ihre Kreativität aus 2D-Bildschirmen herauszubrechen und in die Welt um Sie herum zu gelangen.</span><span class="sxs-lookup"><span data-stu-id="fc785-180">As a holographic developer, you have the power to break your creativity out of 2D screens and into the world around you.</span></span><br><br>
        <span data-ttu-id="fc785-181">Was erstellen *Sie?*</span><span class="sxs-lookup"><span data-stu-id="fc785-181">What will *you* build?</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="fc785-182">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="fc785-182">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="fc785-183">![Holografische imaginäre Welt im Leben](images/designoverview.jpg)</span><span class="sxs-lookup"><span data-stu-id="fc785-183">![Holographic imaginary world in living room](images/designoverview.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="next-discovery-checkpoint"></a><span data-ttu-id="fc785-184">Nächster Erkundungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="fc785-184">Next Discovery Checkpoint</span></span>

<span data-ttu-id="fc785-185">Sie sind auf der [Ermittlungsreise,](get-started-with-mr.md) die wir festgelegt haben, und erkunden die Grundlagen der Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="fc785-185">You're on the [discovery journey](get-started-with-mr.md) we've laid out, and exploring the basics of Mixed Reality.</span></span> <span data-ttu-id="fc785-186">Von hier aus können Sie mit dem nächsten grundlegenden Thema fortfahren:</span><span class="sxs-lookup"><span data-stu-id="fc785-186">From here, you can continue to the next foundational topic:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="fc785-187">Erweitern Ihres Entwurfsprozesses</span><span class="sxs-lookup"><span data-stu-id="fc785-187">Expand your design process</span></span>](case-study-expanding-the-design-process-for-mixed-reality.md)