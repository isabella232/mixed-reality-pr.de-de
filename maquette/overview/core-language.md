---
title: Kernsprache
description: Erfahren Sie mehr über die Details der Kernsprache von Maquette.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, Maquette, Prototyperstellung, gemischte Realität, Virtual Reality, VR, Mr, Feedback, Feedback-Hub, Fehler
ms.openlocfilehash: e0c0b2f204aa32245cc13aff4c64fa641313de51
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935537"
---
# <a name="maquettescript-core-language-details"></a><span data-ttu-id="5a7f5-104">Details der maquettescript-Kernsprache</span><span class="sxs-lookup"><span data-stu-id="5a7f5-104">MaquetteScript core language details</span></span>

<!-- TODO(Harrison): Need consolidated logo with text -->
<span data-ttu-id="5a7f5-105">![Makett-Logo ](../images/MaquetteIcon.png) maquettescript-Kern Sprachen Details</span><span class="sxs-lookup"><span data-stu-id="5a7f5-105">![Maquette logo](../images/MaquetteIcon.png) MaquetteScript Core Language Details</span></span>

## <a name="accessing-maquette-object-and-namespace"></a><span data-ttu-id="5a7f5-106">Zugreifen auf `Maquette` Objekt und Namespace</span><span class="sxs-lookup"><span data-stu-id="5a7f5-106">Accessing `Maquette` Object and Namespace</span></span>

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
<span data-ttu-id="5a7f5-107">Maquette macht interne Objekte und Schnittstellen in JavaScript durch das `Maquette` -Objekt und seine untergeordneten Elemente verfügbar.</span><span class="sxs-lookup"><span data-stu-id="5a7f5-107">Maquette exposes internal objects and interfaces in JavaScript through the `Maquette` object and its children.</span></span> <span data-ttu-id="5a7f5-108">Diese Funktionalität wird in der Dokumentation zu [Maquette-Objekten und Namespace](https://www.maquette.ms/doc_staging/objects/Maquette.html) beschrieben.</span><span class="sxs-lookup"><span data-stu-id="5a7f5-108">This functionality is described in the [Maquette Object and Namespace](https://www.maquette.ms/doc_staging/objects/Maquette.html) documentation.</span></span> 

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
<span data-ttu-id="5a7f5-109">Das `Maquette` -Objekt verfügt über Funktionen der obersten Ebene, um die Interaktion mit Maquette selbst zu vereinfachen und sich wiederholende Probleme leichter lösen zu können.</span><span class="sxs-lookup"><span data-stu-id="5a7f5-109">The `Maquette` object has top-level functions to make it easier to interact with Maquette itself and make repetitive problems easier to solve.</span></span> <span data-ttu-id="5a7f5-110">Dies wird in der Dokumentation von [maquettescriptobject](https://www.maquette.ms/doc_staging/objects/Maquette.MaquetteScriptObject.html)beschrieben.</span><span class="sxs-lookup"><span data-stu-id="5a7f5-110">This is described in the documentation of [MaquetteScriptObject](https://www.maquette.ms/doc_staging/objects/Maquette.MaquetteScriptObject.html).</span></span>

## <a name="maquette-startup-and-loading"></a><span data-ttu-id="5a7f5-111">Starten und Laden von Maketten</span><span class="sxs-lookup"><span data-stu-id="5a7f5-111">Maquette Startup and Loading</span></span>

<!-- TODO(Stefan): Need context on why this is important for users and how they will take advantage of this in production? -->
<span data-ttu-id="5a7f5-112">Maquette lädt und wertet bestimmte JavaScript-Dateien aus, um die Konfiguration, Einrichtung und Initialisierung zu folgenden Zeitpunkten zu ermöglichen:</span><span class="sxs-lookup"><span data-stu-id="5a7f5-112">Maquette will load and evaluate specific JavaScript files to enable config, setup and initialization at the following times:</span></span>

<span data-ttu-id="5a7f5-113">Beim Starten der Makette:</span><span class="sxs-lookup"><span data-stu-id="5a7f5-113">During Maquette startup:</span></span>
<pre>
~/Documents/Maquette/Scripts/OnMaquetteStartup.mqjs
</pre>

<span data-ttu-id="5a7f5-114">Jedes Mal, wenn ein Projekt geladen wird:</span><span class="sxs-lookup"><span data-stu-id="5a7f5-114">Whenever any project is loaded:</span></span>
<pre>
~/Documents/Maquette/Scripts/OnMaquetteProjectLoad.mqjs
</pre>

<span data-ttu-id="5a7f5-115">Projekte laden ihre jeweiligen Projekt Skripts:</span><span class="sxs-lookup"><span data-stu-id="5a7f5-115">Projects load their respective project scripts:</span></span>
<pre>
~/Documents/Maquette/Project/&lt;Your Project&gt;/Scripts/OnLoad.mqjs
</pre>

## <a name="javascript-implementation"></a><span data-ttu-id="5a7f5-116">JavaScript-Implementierung</span><span class="sxs-lookup"><span data-stu-id="5a7f5-116">JavaScript Implementation</span></span>

<!-- TODO(Stefan): Is there anything else we can tell users about the JS interpreter as applied to Maquette? -->
<span data-ttu-id="5a7f5-117">Der in Maquette verwendete JavaScript-Interpreter basiert auf [Jint](https://github.com/sebastienros/jint).</span><span class="sxs-lookup"><span data-stu-id="5a7f5-117">The JavaScript interpreter used in Maquette is based on [Jint](https://github.com/sebastienros/jint).</span></span> <span data-ttu-id="5a7f5-118">Jint ist ECMAScript 5,1-kompatibel und unterstützt zusätzliche [Erweiterungen von ECMAScript 6](https://github.com/sebastienros/jint/issues/343).</span><span class="sxs-lookup"><span data-stu-id="5a7f5-118">Jint is ECMAScript 5.1 compatible and supports additional [extensions from ECMAScript 6](https://github.com/sebastienros/jint/issues/343).</span></span> 

<span data-ttu-id="5a7f5-119">Die Erweiterung `.mqjs` wird verwendet, um Makett-JavaScript-Dateien von normalem JavaScript zu unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="5a7f5-119">The extension `.mqjs` is used to distinguish Maquette javascript files from normal JavaScript.</span></span>

## <a name="see-also"></a><span data-ttu-id="5a7f5-120">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="5a7f5-120">See also</span></span> 
<!-- TODO(Stefan): Add any additional JS related links that may help with troubleshooting or issues? -->