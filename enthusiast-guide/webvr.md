---
title: Verwenden von webvr mit gemischter Windows-Realität
description: Beschreibt webvr und erläutert, wie Sie mit Microsoft Edge auf Windows Mixed Reality-Headsets verwendet werden.
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, Mr, webvr, Edge, Microsoft Edge, Webbrowser
ms.openlocfilehash: 8e8d7b5feefe5b1eccad0684808b40b63e9bbbca
ms.sourcegitcommit: 2da7e181e4e23eed31b59f0332c3ba8b3f594cd0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2020
ms.locfileid: "93131854"
---
# <a name="using-webvr-with-windows-mixed-reality"></a><span data-ttu-id="b6879-104">Verwenden von webvr mit gemischter Windows-Realität</span><span class="sxs-lookup"><span data-stu-id="b6879-104">Using WebVR with Windows Mixed Reality</span></span>

>[!IMPORTANT]
><span data-ttu-id="b6879-105">Die meisten modernen Webbrowser haben die Unterstützung von webvr zugunsten von webxr, dem neuen Standard zum Erstellen von immersiven Webumgebungen für VR-Headsets, als veraltet markiert.</span><span class="sxs-lookup"><span data-stu-id="b6879-105">Most modern web browsers have deprecated support of WebVR in favor of WebXR, the new standard for creating immersive web experiences for VR headsets.</span></span> <span data-ttu-id="b6879-106">Installieren Sie [den neuen Microsoft Edge](using-microsoft-edge.md) für webxr-Support.</span><span class="sxs-lookup"><span data-stu-id="b6879-106">Please install [the new Microsoft Edge](using-microsoft-edge.md) for WebXR support.</span></span>

## <a name="what-is-webvr"></a><span data-ttu-id="b6879-107">Was ist WebVR?</span><span class="sxs-lookup"><span data-stu-id="b6879-107">What is WebVR</span></span>

<span data-ttu-id="b6879-108">[Webvr](https://webvr.info) ist eine offene Spezifikation, die es ermöglicht, VR in Ihrem Browser zu erleben.</span><span class="sxs-lookup"><span data-stu-id="b6879-108">[WebVR](https://webvr.info) is an open specification that makes it possible to experience VR in your browser.</span></span> <span data-ttu-id="b6879-109">Wenn eine Website die webvr-Unterstützung implementiert und 3D-Inhalte bereitstellt, können Sie mit der Zustimmung des Benutzers immersive Inhalte im Headset anzeigen.</span><span class="sxs-lookup"><span data-stu-id="b6879-109">If a website implements WebVR support and provides 3D content, it can display immersive content in the headset, with user consent.</span></span>

## <a name="what-is-the-difference-between-webvr-and-browsing-the-web-in-vr"></a><span data-ttu-id="b6879-110">Worin besteht der Unterschied zwischen webvr und dem Durchsuchen des Internets in VR?</span><span class="sxs-lookup"><span data-stu-id="b6879-110">What is the difference between WebVR and browsing the web in VR</span></span>

<span data-ttu-id="b6879-111">Webvr ist eine Technologie, die es einem Website Autor ermöglicht, eine VR-Funktionalität zu einer Seite hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="b6879-111">WebVR is a technology that allows a website author to add VR functionality to a page.</span></span> <span data-ttu-id="b6879-112">Die webvr-API wird von einer Seite verwendet, um 3D-Inhalte (z. b. 360-Grad-Video oder 3D-Modell oder 3D-Spiel) mit dem gesamten Headset anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="b6879-112">The WebVR API is used by a page to display 3D content (such as 360 degree video, or a 3D model, or a 3D game) to the entirety of your headset.</span></span> <span data-ttu-id="b6879-113">**Beispiel:** Anzeigen eines 360-Videos auf [CNN.com/VR](http://cnn.com/vr).</span><span class="sxs-lookup"><span data-stu-id="b6879-113">**Example:** Viewing a 360 Video on [cnn.com/vr](http://cnn.com/vr).</span></span> <span data-ttu-id="b6879-114">Wenn eine Seite webvr unterstützt, wird eine Schaltfläche oder ein anderes UI-Element hinzugefügt, auf das Sie klicken können, um VR einzugeben.</span><span class="sxs-lookup"><span data-stu-id="b6879-114">If a page supports WebVR, it will add a button or other UI element that you can click to enter VR.</span></span>

<span data-ttu-id="b6879-115">Das Durchsuchen des Internets in VR bedeutet, dass Sie den Edge-Browser verwenden, während Sie Ihr Headset verwenden, als 2D-App-Slate innerhalb von cliffhouse.</span><span class="sxs-lookup"><span data-stu-id="b6879-115">Browsing the web in VR means using the Edge browser while you are wearing your headset, as a 2D app slate within the Cliffhouse.</span></span>

## <a name="do-all-websites-support-webvr"></a><span data-ttu-id="b6879-116">Unterstützen alle Websites webvr</span><span class="sxs-lookup"><span data-stu-id="b6879-116">Do all websites support WebVR</span></span>

<span data-ttu-id="b6879-117">Nein.</span><span class="sxs-lookup"><span data-stu-id="b6879-117">No.</span></span> <span data-ttu-id="b6879-118">Website Autoren müssen sich für die Verwendung von webvr entscheiden. Außerdem können Sie Websites erstellen, die für bestimmte Browser, Headsets und Controller optimiert sind.</span><span class="sxs-lookup"><span data-stu-id="b6879-118">Website authors must opt-in to use WebVR and furthermore they may create sites that are optimized for specific browsers, headsets, and controllers.</span></span> <span data-ttu-id="b6879-119">Einige webvr-Inhalte sind z. b. nur für Mobile VR-Geräte optimiert.</span><span class="sxs-lookup"><span data-stu-id="b6879-119">For example, some WebVR content is optimized for mobile VR devices only.</span></span> <span data-ttu-id="b6879-120">Beachten Sie auch, dass Websites den webvr-Inhalt explizit erstellen und bereitstellen müssen.</span><span class="sxs-lookup"><span data-stu-id="b6879-120">Also, keep in mind that web sites need to explicitly create and provide WebVR content.</span></span> <span data-ttu-id="b6879-121">Die Anzahl von Standorten, an denen einige webvr-kompatible Inhalte vorhanden sind, wächst jeden Tag.</span><span class="sxs-lookup"><span data-stu-id="b6879-121">The number of sites that have some WebVR compatible content is growing every day.</span></span>

## <a name="can-i-use-my-viveoculus-etc-to-view-webvr-content-in-microsoft-edge"></a><span data-ttu-id="b6879-122">Kann ich "Vive/Oculus" usw. verwenden, um webvr-Inhalte in Microsoft Edge anzuzeigen</span><span class="sxs-lookup"><span data-stu-id="b6879-122">Can I use my Vive/Oculus etc to view WebVR content in Microsoft Edge</span></span>

<span data-ttu-id="b6879-123">Nein.</span><span class="sxs-lookup"><span data-stu-id="b6879-123">No.</span></span> <span data-ttu-id="b6879-124">Sie müssen ein Windows Mixed Reality-Headset verwenden, um webvr in Edge zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="b6879-124">You must use a Windows Mixed Reality headset to use WebVR in Edge.</span></span> <span data-ttu-id="b6879-125">Allerdings können Sie in einem anderen Browser auf webvr-Inhalte zugreifen. eine komplette Liste der kompatiblen Geräte und Browser finden Sie unter: [webvr. Rocks](http://webvr.rocks/).</span><span class="sxs-lookup"><span data-stu-id="b6879-125">However, you may be able to access WebVR content in another browser; see the complete list of compatible devices and browsers at: [WebVR.rocks](http://webvr.rocks/).</span></span>

## <a name="where-can-i-find-the-webvr-developer-documentation"></a><span data-ttu-id="b6879-126">Wo finde ich die webvr-Entwicklerdokumentation?</span><span class="sxs-lookup"><span data-stu-id="b6879-126">Where can I find the WebVR developer documentation</span></span>

<span data-ttu-id="b6879-127">Die Entwicklerdokumentation finden Sie hier: [webvr-Entwicklerdokumentation](https://docs.microsoft.com/microsoft-edge/webvr/).</span><span class="sxs-lookup"><span data-stu-id="b6879-127">The developer documentation is located here: [WebVR Developer Documentation](https://docs.microsoft.com/microsoft-edge/webvr/).</span></span>

## <a name="ive-found-a-website-with-webvr-that-doesnt-work-in-windows-mixed-reality-what-do-i-do"></a><span data-ttu-id="b6879-128">Ich habe eine Website mit webvr gefunden, die in Windows Mixed Reality nicht funktioniert.</span><span class="sxs-lookup"><span data-stu-id="b6879-128">I've found a website with WebVR that doesn't work in Windows Mixed Reality.</span></span> <span data-ttu-id="b6879-129">Was soll ich tun</span><span class="sxs-lookup"><span data-stu-id="b6879-129">What do I do</span></span>

<span data-ttu-id="b6879-130">Sie können fehlerhafte Websites direkt an das Microsoft Edge-Browser Team in der [Problem](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/)Verfolgung oder per Twitter über [#EdgeBug hashtag](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/)Berichten.</span><span class="sxs-lookup"><span data-stu-id="b6879-130">You can report broken sites directly to the Microsoft Edge browser team in the [issue tracker](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/), or via twitter using [#EdgeBug hashtag](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/).</span></span>

<span data-ttu-id="b6879-131">Fehler können auch mithilfe der Windows-Feedback-Hub-App Unterkategorie protokolliert werden:</span><span class="sxs-lookup"><span data-stu-id="b6879-131">You can also log bugs using the Windows Feedback Hub app under category:</span></span>

<span data-ttu-id="b6879-132">Probleme mit der Microsoft Edge->-Website</span><span class="sxs-lookup"><span data-stu-id="b6879-132">Microsoft Edge -> Website Issues</span></span>

## <a name="what-is-a-good-page-to-test-if-webvr-is-working"></a><span data-ttu-id="b6879-133">Was ist eine gute Seite, um zu testen, ob webvr funktioniert</span><span class="sxs-lookup"><span data-stu-id="b6879-133">What is a good page to test if WebVR is working</span></span>

<span data-ttu-id="b6879-134">Siehe [webvr.info Samples](http://webvr.info/samples/XX-vr-controllers.html).</span><span class="sxs-lookup"><span data-stu-id="b6879-134">See [webvr.info samples](http://webvr.info/samples/XX-vr-controllers.html).</span></span>

## <a name="how-do-i-set-up-webvr"></a><span data-ttu-id="b6879-135">Gewusst wie webvr einrichten</span><span class="sxs-lookup"><span data-stu-id="b6879-135">How do I set up WebVR</span></span>

<span data-ttu-id="b6879-136">Um webvr-Inhalte auf einem Windows Mixed Reality-Headset (mit Hardware oder Simulation) zu erleben, müssen Sie folgende Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="b6879-136">To experience WebVR content on a Windows Mixed Reality headset (using hardware or simulation) you must:</span></span>

1. <span data-ttu-id="b6879-137">Stellen Sie sicher, dass Ihr Headset angeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="b6879-137">Ensure your headset is connected.</span></span>
2. <span data-ttu-id="b6879-138">Starten Sie Microsoft Edge entweder auf dem Desktop oder in gemischter Realität.</span><span class="sxs-lookup"><span data-stu-id="b6879-138">Launch Microsoft Edge, either on the desktop or within Mixed Reality.</span></span>
3. <span data-ttu-id="b6879-139">Navigieren Sie zu einer webvr-aktivierten Seite.</span><span class="sxs-lookup"><span data-stu-id="b6879-139">Navigate to a WebVR enabled page.</span></span>
4. <span data-ttu-id="b6879-140">Klicken Sie auf der Seite auf die Schaltfläche Enter VR eingeben (der Speicherort und die visuelle Darstellung dieser Schaltfläche können je nach Website variieren).</span><span class="sxs-lookup"><span data-stu-id="b6879-140">Click the Enter VR button within the page (the location and visual representation of this button may vary per website).</span></span> <span data-ttu-id="b6879-141">Dies könnte etwa wie folgt aussehen: </span><span class="sxs-lookup"><span data-stu-id="b6879-141">It may look similar to:</span></span>\
   ![VR-Brillen Bild](images/75px-enter-vr.png)
5. <span data-ttu-id="b6879-143">Wenn Sie zum ersten Mal versuchen, VR in eine bestimmte Domäne einzugeben, fordert der Browser die Zustimmung zur Verwendung der immersiven Ansicht an. Klicken Sie dann auf Ja:</span><span class="sxs-lookup"><span data-stu-id="b6879-143">The first time you try to enter VR on a specific domain, the browser will ask for consent to use immersive view, click yes:</span></span> ![Benutzeroberfläche für Zustimmung, die beim ersten Versuch angezeigt wird, VR in eine bestimmte Domäne einzugeben](images/1053px-Webvr-consent-ui.png)
6. <span data-ttu-id="b6879-145">Ihr Headset sollte mit dem Anzeigen der webvr-Inhalte beginnen.</span><span class="sxs-lookup"><span data-stu-id="b6879-145">Your headset should begin displaying the WebVR content.</span></span>

## <a name="see-also"></a><span data-ttu-id="b6879-146">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b6879-146">See also</span></span>

* [<span data-ttu-id="b6879-147">Problembehandlung > webvr</span><span class="sxs-lookup"><span data-stu-id="b6879-147">Troubleshooting > WebVR</span></span>](webvr-questions.md)
* [<span data-ttu-id="b6879-148">Vorgehensweise beim Einstieg in Ihre erste webvr-Benutzer Darstellung</span><span class="sxs-lookup"><span data-stu-id="b6879-148">How to get into your first WebVR experience</span></span>](using-games-and-apps-in-windows-mixed-reality.md#how-to-get-into-your-first-webvr-experience)
* [<span data-ttu-id="b6879-149">Verwenden von spielen und apps in Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="b6879-149">Using games and apps in Windows Mixed Reality</span></span>](using-games-and-apps-in-windows-mixed-reality.md)
* [<span data-ttu-id="b6879-150">Ihre gemischte Reality-Startseite</span><span class="sxs-lookup"><span data-stu-id="b6879-150">Your Mixed Reality Home</span></span>](your-mixed-reality-home.md)
* [<span data-ttu-id="b6879-151">Überwachungs System</span><span class="sxs-lookup"><span data-stu-id="b6879-151">Tracking System</span></span>](tracking-system.md)
* [<span data-ttu-id="b6879-152">Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="b6879-152">Motion Controllers</span></span>](controllers-in-wmr.md)
* [<span data-ttu-id="b6879-153">SteamVR</span><span class="sxs-lookup"><span data-stu-id="b6879-153">SteamVR</span></span>](using-steamvr-with-windows-mixed-reality.md)
* [<span data-ttu-id="b6879-154">Einreichen von Feedback</span><span class="sxs-lookup"><span data-stu-id="b6879-154">Filing feedback</span></span>](filing-feedback.md)
