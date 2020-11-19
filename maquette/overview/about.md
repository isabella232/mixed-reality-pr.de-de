---
title: Informationen über Maquette
description: Einführung in Maquette und seine Features.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, Maquette, Prototyperstellung, gemischte Realität, Virtual Reality, VR, Mr, Feedback, Feedback-Hub, Fehler
ms.openlocfilehash: fbc2aee7472a26e508937fa1dedfdac08fadfa10
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935529"
---
# <a name="about-maquette"></a><span data-ttu-id="6f11f-104">Informationen über Maquette</span><span class="sxs-lookup"><span data-stu-id="6f11f-104">About Maquette</span></span>

<!-- TODO(Harrison): Need consolidated logo with text -->
<span data-ttu-id="6f11f-105">![Einführung in Logo ](../images/MaquetteIcon.png) maquettescript</span><span class="sxs-lookup"><span data-stu-id="6f11f-105">![Logo](../images/MaquetteIcon.png) MaquetteScript Introduction</span></span>

<!-- TODO(Harrison/Stefan): Add more high level, less technical explanation of what Maquette is and why it's useful in MR development. 
          - Differentiate between Maquette and MaquetteScript
          - Separate out each of Maquette's main parts and add content
          - Give brief explanations of use case or examples
-->
<span data-ttu-id="6f11f-106">Maquette integriert Standard-ECMA 5,1 JavaScript, um die Investition von Interaktivität in Maquette-Szenen und Objekten zu ermöglichen, die in vscode bearbeitet und ausgeführt werden können.</span><span class="sxs-lookup"><span data-stu-id="6f11f-106">Maquette integrates standard ECMA 5.1 Javascript to enable investment of interactivity in Maquette scenes and objects which can be edited and executed from within VSCode.</span></span> <span data-ttu-id="6f11f-107">Eigenschaften von Objekten werden für das Lesen und Festlegen von innerhalb des Skripts, von Objektmethoden mit dem Namen und von Objekt-und System Ereignissen verfügbar gemacht.</span><span class="sxs-lookup"><span data-stu-id="6f11f-107">Properties of objects are exposed for reading and setting from within script, object methods called, and object and system events fielded.</span></span> <span data-ttu-id="6f11f-108">Das Skript kann auch mit Maquette selbst über Systemobjekte interagieren, auf die über das Skript zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="6f11f-108">Script can also interact with Maquette itself via system objects accessible via script.</span></span> <span data-ttu-id="6f11f-109">Verschiedene UI-Steuerelemente, mit denen der Benutzer interagieren kann, sind Teil des Systems.</span><span class="sxs-lookup"><span data-stu-id="6f11f-109">Various UI controls that the user can interact with are part of the system.</span></span> <span data-ttu-id="6f11f-110">Diese können hinzugefügt werden, wenn Sie in Maquette erstellen oder innerhalb eines Skripts erstellt und verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="6f11f-110">These can be added when authoring in Maquette or created and managed from within script.</span></span> <span data-ttu-id="6f11f-111">Benutzer Interaktions Ereignisse mit diesen Elementen (Dateneingabe, Klicks usw.) werden auch für Skripts als Ereignisse verfügbar gemacht.</span><span class="sxs-lookup"><span data-stu-id="6f11f-111">User interaction events with these elements (data entry, clicks, etc) are also exposed to script as events.</span></span> <span data-ttu-id="6f11f-112">Mit diesen Ergänzungen können einfache bis komplexe Szenen erstellt werden, von Experimenten bis hin zu Datenvisualisierungen bis hin zu Explorationen von gemischten Reality-Benutzer Szenarien bis hin zu vollständig erkannten Erfahrungen in AR oder VR.</span><span class="sxs-lookup"><span data-stu-id="6f11f-112">With these additions, simple to complex scenes can be built, from experiments to data visualization to explorations of Mixed Reality user scenarios to fully realized experiences in AR or VR.</span></span>

<p align="center">
  <img src="images/ScriptingOverview.png" alt="Scripting overview video screenshot">
</p>

<!-- TODO(Harrison/Stefan): Get this video recorded or create the content in text form until it's available. -->
<span data-ttu-id="6f11f-113">60 Second-Video</span><span class="sxs-lookup"><span data-stu-id="6f11f-113">60 second'ish video</span></span>
* <span data-ttu-id="6f11f-114">Eintrags Titelkarte</span><span class="sxs-lookup"><span data-stu-id="6f11f-114">Entry Title Card</span></span>
  * <span data-ttu-id="6f11f-115">Erstellung von interaktiven gemischten Reality-Inhalten in Maquette</span><span class="sxs-lookup"><span data-stu-id="6f11f-115">Creation of Interactive Mixed Reality Content in Maquette</span></span>
  * <span data-ttu-id="6f11f-116">Skripterstellung/Interaktivität/UI-System</span><span class="sxs-lookup"><span data-stu-id="6f11f-116">Scripting/Interactivity/UI System</span></span>
* <span data-ttu-id="6f11f-117">Willkommen bei Team-oder Video Beschriftungen?</span><span class="sxs-lookup"><span data-stu-id="6f11f-117">VO welcome by team or video captions?</span></span>  <span data-ttu-id="6f11f-118">enden</span><span class="sxs-lookup"><span data-stu-id="6f11f-118">explaining:</span></span>
  * <span data-ttu-id="6f11f-119">Grund für die Skripterstellung, um die Erstellung interaktiver Mr-Inhalte zu ermöglichen</span><span class="sxs-lookup"><span data-stu-id="6f11f-119">reasoning behind scripting to enable creation of interactive MR content</span></span>
  * <span data-ttu-id="6f11f-120">Verwenden Sie die Verwendung in sehr breiten Pinselstrichen.</span><span class="sxs-lookup"><span data-stu-id="6f11f-120">touch on how it can be used in very broad brush strokes</span></span>
* <span data-ttu-id="6f11f-121">Skripterstellung von vingette in Aktion</span><span class="sxs-lookup"><span data-stu-id="6f11f-121">Scripting vingette’s in action</span></span>
  * <span data-ttu-id="6f11f-122">Erstellen (Dialogfeld)</span><span class="sxs-lookup"><span data-stu-id="6f11f-122">Composing dialog box</span></span>
  * <span data-ttu-id="6f11f-123">Entwickeln einer App aus einer Gliederung (app-App-Demo)</span><span class="sxs-lookup"><span data-stu-id="6f11f-123">Building app from outline (cooking app demo)</span></span>
  * <span data-ttu-id="6f11f-124">Verfassen im photogrammmetrikmodell</span><span class="sxs-lookup"><span data-stu-id="6f11f-124">Composing in photogrammetry model</span></span>
  * <span data-ttu-id="6f11f-125">Interagieren mit Handbuch zur Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="6f11f-125">Interacting with troubleshooting guide</span></span>
  * <span data-ttu-id="6f11f-126">Bildschirmansicht des Debuggens von Skripts in vscode</span><span class="sxs-lookup"><span data-stu-id="6f11f-126">Screen view of debugging scripting in VSCode</span></span>
  * <span data-ttu-id="6f11f-127">Abrufen des Zugriffs auf Skripts aus einem Objekt in der Szene</span><span class="sxs-lookup"><span data-stu-id="6f11f-127">Getting access to script from an object in scene</span></span>
  * <span data-ttu-id="6f11f-128">Usw....</span><span class="sxs-lookup"><span data-stu-id="6f11f-128">Etc...</span></span>
* <span data-ttu-id="6f11f-129">Übersichts Titelkarte am Ende</span><span class="sxs-lookup"><span data-stu-id="6f11f-129">Summary Title card at end</span></span>
  * <span data-ttu-id="6f11f-130">Link zu Maquette</span><span class="sxs-lookup"><span data-stu-id="6f11f-130">Link to Maquette</span></span>
  * <span data-ttu-id="6f11f-131">Einstieg in die Skripterstellung</span><span class="sxs-lookup"><span data-stu-id="6f11f-131">Where to go to get started with scripting</span></span>
  * <span data-ttu-id="6f11f-132">Ankündigungen/Status/Community</span><span class="sxs-lookup"><span data-stu-id="6f11f-132">Announcements/status/community</span></span>
  * <span data-ttu-id="6f11f-133">Sehen Sie sich an, was Sie tun können/Übermittlungen (?)</span><span class="sxs-lookup"><span data-stu-id="6f11f-133">Look forward to seeing what you can do/submissions(?)</span></span>
  * <span data-ttu-id="6f11f-134">Feedback und wie wir Sie besser bedienen können</span><span class="sxs-lookup"><span data-stu-id="6f11f-134">Feedback and how we can serve you better</span></span>

<!-- TODO(Harrison): Consider breaking this out into a Maquette journey doc or section as applicable. -->
* [<span data-ttu-id="6f11f-135">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="6f11f-135">Getting Started</span></span>](installation.md)
* [<span data-ttu-id="6f11f-136">Beispiele und Beispiel-apps</span><span class="sxs-lookup"><span data-stu-id="6f11f-136">Examples and Sample Apps</span></span>](../samples/overview.md)
* [<span data-ttu-id="6f11f-137">Unterstützung</span><span class="sxs-lookup"><span data-stu-id="6f11f-137">Support</span></span>](../resources/support.md)

<!-- TODO(Harrison): Need to find out why docs feedback footer isn't appearing. -->
## <a name="send-us-feedback"></a><span data-ttu-id="6f11f-138">Senden Sie uns Feedback</span><span class="sxs-lookup"><span data-stu-id="6f11f-138">Send us feedback</span></span>

<span data-ttu-id="6f11f-139">Wir freuen uns auf Ihre Erfahrungen und Ergebnisse.</span><span class="sxs-lookup"><span data-stu-id="6f11f-139">We look forward to hearing about your experiences and results.</span></span> <span data-ttu-id="6f11f-140">Feedback, Vorschläge und Fehlerberichte sind immer willkommen!</span><span class="sxs-lookup"><span data-stu-id="6f11f-140">Feedback, suggestions and bug reports always welcome!</span></span>
<span data-ttu-id="6f11f-141"><Link? ></span><span class="sxs-lookup"><span data-stu-id="6f11f-141"><Link?></span></span>