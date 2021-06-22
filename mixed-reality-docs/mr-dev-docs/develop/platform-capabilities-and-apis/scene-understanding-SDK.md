---
title: Scene understanding SDK
description: Erfahren Sie, wie Sie das Scene Understanding SDK installieren und verwenden, einschließlich Komponenten, Gitternetzen und Objekten in Mixed Reality-Apps.
author: szymons
ms.author: szymons
ms.date: 12/14/2020
ms.topic: article
keywords: Scene Understanding, Spatial Mapping, Windows Mixed Reality, Unity
ms.openlocfilehash: dee561e49a9457aa35c44037f4573caaefd00f2a
ms.sourcegitcommit: 86fafb3a7ac6a5f60340ae5041619e488223f4f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "112449729"
---
# <a name="scene-understanding-sdk-overview"></a><span data-ttu-id="31b7e-104">Übersicht über das Scene Understanding SDK</span><span class="sxs-lookup"><span data-stu-id="31b7e-104">Scene understanding SDK overview</span></span>

<span data-ttu-id="31b7e-105">Scene Understanding transformiert die Sensordaten der unstrukturierten Umgebung, die ihr Mixed Reality Gerät erfasst und in eine leistungsfähige abstrakte Darstellung umwandelt.</span><span class="sxs-lookup"><span data-stu-id="31b7e-105">Scene understanding transforms the unstructured environment sensor data that your Mixed Reality device captures and converts it into a powerful abstract representation.</span></span> <span data-ttu-id="31b7e-106">Das SDK fungiert als Kommunikationsschicht zwischen Ihrer Anwendung und der Scene Understanding-Runtime.</span><span class="sxs-lookup"><span data-stu-id="31b7e-106">The SDK acts as the communication layer between your application and the Scene Understanding runtime.</span></span> <span data-ttu-id="31b7e-107">Es soll vorhandene Standardkonstrukte imitieren, z. B. 3D-Szenendiagramme für 3D-Darstellungen und 2D-Rechtecke und -Bereiche für 2D-Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="31b7e-107">It's aimed to mimic existing standard constructs, such as 3D scene graphs for 3D representations, and 2D rectangles and panels for 2D applications.</span></span> <span data-ttu-id="31b7e-108">Während die Scene Understanding-Konstrukte konkreten Frameworks zugeordnet werden, ist SceneUnderstanding im Allgemeinen frameworkunabhängig und ermöglicht die Interoperabilität zwischen verschiedenen Frameworks, die damit interagieren.</span><span class="sxs-lookup"><span data-stu-id="31b7e-108">While the constructs Scene Understanding mimics will map to concrete frameworks, in general SceneUnderstanding is framework agnostic allowing for interoperability between varied frameworks that interact with it.</span></span> <span data-ttu-id="31b7e-109">Mit der Weiterentwicklung von Scene Understanding besteht die Rolle des SDK darin, sicherzustellen, dass neue Darstellungen und Funktionen in einem einheitlichen Framework weiterhin verfügbar gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="31b7e-109">As Scene Understanding evolves the role of the SDK is to ensure new representations and capabilities continue to be exposed within a unified framework.</span></span> <span data-ttu-id="31b7e-110">In diesem Dokument werden zunächst konzepte auf hoher Ebene vorgestellt, die Ihnen helfen, sich mit der Entwicklungsumgebung/-verwendung vertraut zu machen und dann eine ausführlichere Dokumentation für bestimmte Klassen und Konstrukte bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="31b7e-110">In this document, we will first introduce high-level concepts that will help you get familiar with the development environment/usage and then provide more detailed documentation for specific classes and constructs.</span></span>

## <a name="where-do-i-get-the-sdk"></a><span data-ttu-id="31b7e-111">Wo erhalte ich das SDK?</span><span class="sxs-lookup"><span data-stu-id="31b7e-111">Where do I get the SDK?</span></span>

<span data-ttu-id="31b7e-112">Das SceneUnderstanding SDK kann über das [Mixed Reality Feature Tool](../unity/welcome-to-mr-feature-tool.md)heruntergeladen werden.</span><span class="sxs-lookup"><span data-stu-id="31b7e-112">The SceneUnderstanding SDK is downloadable via the [Mixed Reality Feature Tool](../unity/welcome-to-mr-feature-tool.md).</span></span>

<span data-ttu-id="31b7e-113">**Hinweis:** Die neueste Version hängt von Vorschaupaketen ab, und Sie müssen Vorabversionspakete aktivieren, um sie anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="31b7e-113">**Note:** the latest release depends on preview packages and you'll need to enable pre-release packages to see it.</span></span>

<span data-ttu-id="31b7e-114">Für Version 0.5.2022-rc und höher unterstützt Scene Understanding Sprachprojektionen für C# und C++, sodass Anwendungen Anwendungen für Win32- oder UWP-Plattformen entwickeln können.</span><span class="sxs-lookup"><span data-stu-id="31b7e-114">For version 0.5.2022-rc and later, Scene Understanding supports language projections for C# and C++ allowing applications to develop applications for Win32 or UWP platforms.</span></span> <span data-ttu-id="31b7e-115">Ab dieser Version unterstützt SceneUnderstanding die Unity-Unterstützung im Editor, die den SceneObserver aussperrt, der ausschließlich für die Kommunikation mit HoloLens2 verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="31b7e-115">As of this version, SceneUnderstanding supports unity in-editor support barring the SceneObserver, which is used solely for communicating with HoloLens2.</span></span> 

<span data-ttu-id="31b7e-116">SceneUnderstanding erfordert Windows SDK Version 18362 oder höher.</span><span class="sxs-lookup"><span data-stu-id="31b7e-116">SceneUnderstanding requires Windows SDK version 18362 or higher.</span></span> 

## <a name="conceptual-overview"></a><span data-ttu-id="31b7e-117">Konzeptionelle Übersicht</span><span class="sxs-lookup"><span data-stu-id="31b7e-117">Conceptual Overview</span></span>

### <a name="the-scene"></a><span data-ttu-id="31b7e-118">Die Szene</span><span class="sxs-lookup"><span data-stu-id="31b7e-118">The Scene</span></span>

<span data-ttu-id="31b7e-119">Ihr Mixed Reality-Gerät integriert ständig Informationen darüber, was es in Ihrer Umgebung sieht.</span><span class="sxs-lookup"><span data-stu-id="31b7e-119">Your mixed reality device is constantly integrating information about what it sees in your environment.</span></span> <span data-ttu-id="31b7e-120">Scene Understanding trichtert alle diese Datenquellen und erzeugt eine einzelne kohäsive Abstraktion.</span><span class="sxs-lookup"><span data-stu-id="31b7e-120">Scene Understanding funnels all of these data sources and produces one single cohesive abstraction.</span></span> <span data-ttu-id="31b7e-121">Scene Understanding generiert Szenen, bei denen es sich um eine Komposition von [SceneObjects](scene-understanding-SDK.md#sceneobjects) handelt, die eine Instanz eines einzelnen Objekts darstellen (z. B. eine Wand/Hänge/Etage). Szenenobjekte selbst sind eine Komposition von [SceneComponents), die präzisere Teile darstellen, aus denen dieses SceneObject besteht.</span><span class="sxs-lookup"><span data-stu-id="31b7e-121">Scene Understanding generates Scenes, which are a composition of [SceneObjects](scene-understanding-SDK.md#sceneobjects) that represent an instance of a single thing, (for example, a wall/ceiling/floor.) Scene Objects themselves are a composition of [SceneComponents, which represent more granular pieces that make up this SceneObject.</span></span> <span data-ttu-id="31b7e-122">Beispiele für Komponenten sind Quads und Gitternetze, aber in Zukunft könnten Begrenzungsfelder, Kollisionsgitternetze, Metadaten usw. dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="31b7e-122">Examples of components are quads and meshes, but in the future could represent bounding boxes, collision meshes, metadata etc.</span></span>

<span data-ttu-id="31b7e-123">Der Prozess der Konvertierung der rohen Sensordaten in eine Szene ist ein potenziell kostspieliger Vorgang, der bei großen Bereichen (~50 x 50 m) sekundenlang dauern kann (~10 x 10 m) und daher nicht vom Gerät ohne Anwendungsanforderung berechnet wird.</span><span class="sxs-lookup"><span data-stu-id="31b7e-123">The process of converting the raw sensor data into a Scene is a potentially expensive operation that could take seconds for medium spaces (~10x10m) to minutes for large spaces (~50x50m) and therefore it is not something that is being computed by the device without application request.</span></span> <span data-ttu-id="31b7e-124">Stattdessen wird die Szenengenerierung von Ihrer Anwendung bei Bedarf ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="31b7e-124">Instead, Scene generation is triggered by your application on demand.</span></span> <span data-ttu-id="31b7e-125">Die SceneObserver-Klasse verfügt über statische Methoden, die eine Szene berechnen oder deserialisieren können, mit denen Sie dann aufzählen/interagieren können.</span><span class="sxs-lookup"><span data-stu-id="31b7e-125">The SceneObserver class has static methods that can Compute or Deserialize a scene, which you can then enumerate/interact with.</span></span> <span data-ttu-id="31b7e-126">Die Aktion "Compute" wird bei Bedarf ausgeführt und auf der CPU ausgeführt, jedoch in einem separaten Prozess (der Mixed Reality-Treiber).</span><span class="sxs-lookup"><span data-stu-id="31b7e-126">The "Compute" action is executed on-demand and executes on the CPU but in a separate process (the Mixed Reality Driver).</span></span> <span data-ttu-id="31b7e-127">Während wir jedoch Compute in einem anderen Prozess durchführen, werden die resultierenden Szenendaten in Ihrer Anwendung im Scene-Objekt gespeichert und verwaltet.</span><span class="sxs-lookup"><span data-stu-id="31b7e-127">However, while we do compute in another process the resulting Scene data is stored and maintained in your application in the Scene object.</span></span> 

<span data-ttu-id="31b7e-128">Im Folgenden finden Sie ein Diagramm, das diesen Prozessfluss veranschaulicht und Beispiele für zwei Anwendungen zeigt, die mit der Scene Understanding-Runtime verbunden sind.</span><span class="sxs-lookup"><span data-stu-id="31b7e-128">Below is a diagram that illustrates this process flow and shows examples of two applications interfacing with the Scene Understanding runtime.</span></span> 

![Prozessdiagramm](images/SU-ProcessFlow.png)

<span data-ttu-id="31b7e-130">Auf der linken Seite befindet sich ein Diagramm der Mixed Reality-Runtime, die immer aktiv ist und in einem eigenen Prozess ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="31b7e-130">On the left-hand side is a diagram of the mixed reality runtime, which is always on and running in its own process.</span></span> <span data-ttu-id="31b7e-131">Diese Runtime ist für die Durchführung von Gerätenachverfolgung, räumlicher Zuordnung und anderen Vorgängen verantwortlich, die Scene Understanding verwendet, um die Welt um Sie herum zu verstehen und zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="31b7e-131">This runtime is responsible for performing device tracking, spatial mapping, and other operations that Scene Understanding uses to understand and reason about the world around you.</span></span> <span data-ttu-id="31b7e-132">Auf der rechten Seite des Diagramms werden zwei theoretische Anwendungen gezeigt, die Scene Understanding nutzen.</span><span class="sxs-lookup"><span data-stu-id="31b7e-132">On the right side of the diagram, we show two theoretical applications that make use of Scene Understanding.</span></span> <span data-ttu-id="31b7e-133">Die erste Anwendung arbeitet mit MRTK zusammen, das intern das Scene Understanding SDK verwendet, die zweite App berechnet und verwendet zwei separate Szeneninstanzen.</span><span class="sxs-lookup"><span data-stu-id="31b7e-133">The first application interfaces with MRTK, which uses the Scene Understanding SDK internally, the second app computes and uses two separate scene instances.</span></span> <span data-ttu-id="31b7e-134">Alle drei Szenen in diesem Diagramm generieren unterschiedliche Instanzen der Szenen. Der Treiber verfolgt den globalen Zustand, der von Anwendungen gemeinsam genutzt wird, und Szenenobjekte in einer Szene nicht in einer anderen Szene.</span><span class="sxs-lookup"><span data-stu-id="31b7e-134">All three Scenes in this diagram generate distinct instances of the scenes, the driver isn't tracking global state that is shared between applications and Scene Objects in one scene aren't found in another.</span></span> <span data-ttu-id="31b7e-135">Scene Understanding bietet einen Mechanismus, der im Laufe der Zeit nachverfolgt werden kann, aber dies erfolgt mithilfe des SDK.</span><span class="sxs-lookup"><span data-stu-id="31b7e-135">Scene Understanding does provide a mechanism to track over time, but this is done using the SDK.</span></span> <span data-ttu-id="31b7e-136">Der Nachverfolgungscode wird bereits im SDK im Prozess Ihrer App ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="31b7e-136">Tracking code is already running in the SDK in your app's process.</span></span>

<span data-ttu-id="31b7e-137">Da jede Szene ihre Daten im Arbeitsspeicher Ihrer Anwendung speichert, können Sie davon ausgehen, dass die gesamte Funktion des Scene-Objekts oder seine internen Daten immer im Prozess Ihrer Anwendung ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="31b7e-137">Because each Scene stores it's data in your application's memory space, you can assume that all function of the Scene object or it's internal data is always executed in your application's process.</span></span>

### <a name="layout"></a><span data-ttu-id="31b7e-138">Layout</span><span class="sxs-lookup"><span data-stu-id="31b7e-138">Layout</span></span>

<span data-ttu-id="31b7e-139">Für die Arbeit mit Scene Understanding kann es hilfreich sein, zu wissen und zu verstehen, wie die Laufzeit Komponenten logisch und physisch darstellt.</span><span class="sxs-lookup"><span data-stu-id="31b7e-139">To work with Scene Understanding, it may be valuable to know and understand how the runtime represents components logically and physically.</span></span> <span data-ttu-id="31b7e-140">Die Szene stellt Daten mit einem bestimmten Layout dar, das als einfach ausgewählt wurde, während eine zugrunde liegende Struktur beibehalten wird, die zukünftige Anforderungen erfüllen kann, ohne dass größere Revisionen erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="31b7e-140">The Scene represents data with a specific layout that was chosen to be simple while maintaining an underlying structure that is pliable to meet future requirements without needing major revisions.</span></span> <span data-ttu-id="31b7e-141">Die Szene speichert dazu alle Komponenten (Bausteine für alle Szenenobjekte) in einer flachen Liste und definiert Hierarchie und Komposition über Verweise, in denen bestimmte Komponenten auf andere verweisen.</span><span class="sxs-lookup"><span data-stu-id="31b7e-141">The Scene does this by storing all Components (building blocks for all Scene Objects) in a flat list and defining hierarchy and composition through references where specific components reference others.</span></span>

<span data-ttu-id="31b7e-142">Unten sehen Sie ein Beispiel für eine -Struktur in ihrer flachen und logischen Form.</span><span class="sxs-lookup"><span data-stu-id="31b7e-142">Below we present an example of a structure in both its flat and logical form.</span></span>

<table>
<tr><th><span data-ttu-id="31b7e-143">Logisches Layout</span><span class="sxs-lookup"><span data-stu-id="31b7e-143">Logical Layout</span></span></th><th><span data-ttu-id="31b7e-144">Physisches Layout</span><span class="sxs-lookup"><span data-stu-id="31b7e-144">Physical Layout</span></span></th></tr>
<tr>
<td>
<ul>
  <span data-ttu-id="31b7e-145">Szene</span><span class="sxs-lookup"><span data-stu-id="31b7e-145">Scene</span></span>
  <ul>
  <li><span data-ttu-id="31b7e-146">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="31b7e-146">SceneObject_1</span></span>
    <ul>
      <li><span data-ttu-id="31b7e-147">SceneMesh_1</span><span class="sxs-lookup"><span data-stu-id="31b7e-147">SceneMesh_1</span></span></li>
      <li><span data-ttu-id="31b7e-148">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="31b7e-148">SceneQuad_1</span></span></li>
      <li><span data-ttu-id="31b7e-149">SceneQuad_2</span><span class="sxs-lookup"><span data-stu-id="31b7e-149">SceneQuad_2</span></span></li>
    </ul>
  </li>
  <li><span data-ttu-id="31b7e-150">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="31b7e-150">SceneObject_2</span></span>
    <ul>
      <li><span data-ttu-id="31b7e-151">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="31b7e-151">SceneQuad_1</span></span></li>
      <li><span data-ttu-id="31b7e-152">SceneQuad_3</span><span class="sxs-lookup"><span data-stu-id="31b7e-152">SceneQuad_3</span></span></li>
      </li></ul>
  </li>
  <li><span data-ttu-id="31b7e-153">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="31b7e-153">SceneObject_3</span></span>
    <ul>
      <li><span data-ttu-id="31b7e-154">SceneMesh_3</span><span class="sxs-lookup"><span data-stu-id="31b7e-154">SceneMesh_3</span></span></li>
    </ul>
  </ul>
</ul>
</td>
<td>
<ul>
  <li><span data-ttu-id="31b7e-155">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="31b7e-155">SceneObject_1</span></span></li>
  <li><span data-ttu-id="31b7e-156">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="31b7e-156">SceneObject_2</span></span></li>
  <li><span data-ttu-id="31b7e-157">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="31b7e-157">SceneObject_3</span></span></li>
  <li><span data-ttu-id="31b7e-158">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="31b7e-158">SceneQuad_1</span></span></li>
  <li><span data-ttu-id="31b7e-159">SceneQuad_2</span><span class="sxs-lookup"><span data-stu-id="31b7e-159">SceneQuad_2</span></span></li>
  <li><span data-ttu-id="31b7e-160">SceneQuad_3</span><span class="sxs-lookup"><span data-stu-id="31b7e-160">SceneQuad_3</span></span></li>
  <li><span data-ttu-id="31b7e-161">SceneMesh_1</span><span class="sxs-lookup"><span data-stu-id="31b7e-161">SceneMesh_1</span></span></li>
  <li><span data-ttu-id="31b7e-162">SceneMesh_2</span><span class="sxs-lookup"><span data-stu-id="31b7e-162">SceneMesh_2</span></span></li>
</ul>
</td>
</tr>
</table>

<span data-ttu-id="31b7e-163">In dieser Abbildung wird der Unterschied zwischen dem physischen und logischen Layout der Szene hervorgehoben.</span><span class="sxs-lookup"><span data-stu-id="31b7e-163">This illustration highlights the difference between the physical and logical layout of the Scene.</span></span> <span data-ttu-id="31b7e-164">Auf der linken Seite sehen wir das hierarchische Layout der Daten, die Ihrer Anwendung beim Aufzählen der Szene angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="31b7e-164">On the left, we see the hierarchical layout of the data that your application sees when enumerating the scene.</span></span> <span data-ttu-id="31b7e-165">Auf der rechten Seite sehen wir, dass die Szene aus 12 unterschiedlichen Komponenten besteht, auf die bei Bedarf einzeln zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="31b7e-165">On the right, we see that the scene is comprised of 12 distinct components that are accessible individually if necessary.</span></span> <span data-ttu-id="31b7e-166">Bei der Verarbeitung einer neuen Szene erwarten wir, dass Anwendungen diese Hierarchie logisch durchgehen. Bei der Nachverfolgung zwischen Szenenupdates sind einige Anwendungen jedoch möglicherweise nur an bestimmten Komponenten interessiert, die von zwei Szenen gemeinsam genutzt werden.</span><span class="sxs-lookup"><span data-stu-id="31b7e-166">When processing a new scene, we expect applications to walk this hierarchy logically, however when tracking between scene updates, some applications may only be interested in targeting specific components that are shared between two scenes.</span></span>

## <a name="api-overview"></a><span data-ttu-id="31b7e-167">API-Übersicht</span><span class="sxs-lookup"><span data-stu-id="31b7e-167">API overview</span></span>

<span data-ttu-id="31b7e-168">Der folgende Abschnitt bietet eine allgemeine Übersicht über die Konstrukte in Scene Understanding.</span><span class="sxs-lookup"><span data-stu-id="31b7e-168">The following section provides a high-level overview of the constructs in Scene Understanding.</span></span> <span data-ttu-id="31b7e-169">In diesem Abschnitt erfahren Sie, wie Szenen dargestellt werden und wofür die verschiedenen Komponenten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="31b7e-169">Reading this section will give you an  understanding of how scenes are represented, and what the various components do/are used for.</span></span> <span data-ttu-id="31b7e-170">Der nächste Abschnitt enthält konkrete Codebeispiele und zusätzliche Details, die in dieser Übersicht erläutert werden.</span><span class="sxs-lookup"><span data-stu-id="31b7e-170">The next section will provide concrete code examples and additional details that are glossed over in this overview.</span></span>

<span data-ttu-id="31b7e-171">Alle unten beschriebenen Typen befinden sich im `Microsoft.MixedReality.SceneUnderstanding` -Namespace.</span><span class="sxs-lookup"><span data-stu-id="31b7e-171">All of the types described below reside in the `Microsoft.MixedReality.SceneUnderstanding` namespace.</span></span>

### <a name="scenecomponents"></a><span data-ttu-id="31b7e-172">SceneComponents</span><span class="sxs-lookup"><span data-stu-id="31b7e-172">SceneComponents</span></span>

<span data-ttu-id="31b7e-173">Nachdem Sie nun das logische Layout von Szenen verstanden haben, können wir nun das Konzept von SceneComponents und ihre Verwendung zum Erstellen von Hierarchien darstellen.</span><span class="sxs-lookup"><span data-stu-id="31b7e-173">Now that you understand the logical layout of scenes we can now present the concept of SceneComponents and how they're used to compose hierarchy.</span></span> <span data-ttu-id="31b7e-174">SceneComponents sind die präzisesten Zerlegungen in SceneUnderstanding, die einen einzelnen Kern darstellen, z. B. ein Gitternetz oder ein Quader oder ein Begrenzungsfeld.</span><span class="sxs-lookup"><span data-stu-id="31b7e-174">SceneComponents are the most granular decompositions in SceneUnderstanding representing a single core thing, for example, a mesh or a quad or a bounding box.</span></span> <span data-ttu-id="31b7e-175">SceneComponents sind Dinge, die unabhängig aktualisiert werden können und von anderen SceneComponents referenziert werden können. Daher verfügen sie über eine einzelne globale Eigenschaft mit einer eindeutigen ID, die diesen Typ von Nachverfolgungs-/Verweismechanismus ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="31b7e-175">SceneComponents are things that can update independently and can be referenced by other SceneComponents, hence they have a single global property a unique ID, that allow for this type of tracking/referencing mechanism.</span></span> <span data-ttu-id="31b7e-176">IDs werden für die logische Zusammensetzung der Szenenhierarchie und objektpersistenz verwendet (das Aktualisieren einer Szene relativ zu einer anderen).</span><span class="sxs-lookup"><span data-stu-id="31b7e-176">Ids are used for the logical composition of scene hierarchy as well as object persistence (the act of updating one scene relative to another.)</span></span> 

<span data-ttu-id="31b7e-177">Wenn Sie jede neu berechnete Szene als eindeutig behandeln und einfach alle darin enthaltenen Daten aufzählen, sind die IDs für Sie weitgehend transparent.</span><span class="sxs-lookup"><span data-stu-id="31b7e-177">If you're treating every newly computed scene as being distinct, and simply enumerating all data within it then Ids are largely transparent to you.</span></span> <span data-ttu-id="31b7e-178">Wenn Sie jedoch planen, Komponenten über mehrere Updates nachzuverfolgen, verwenden Sie die IDs, um SceneComponents zwischen Szenenobjekten zu indizieren und zu suchen.</span><span class="sxs-lookup"><span data-stu-id="31b7e-178">However, if you're planning to track components over several updates you'll use the Ids to index and find SceneComponents between Scene objects.</span></span>

### <a name="sceneobjects"></a><span data-ttu-id="31b7e-179">SceneObjects</span><span class="sxs-lookup"><span data-stu-id="31b7e-179">SceneObjects</span></span>

<span data-ttu-id="31b7e-180">Ein SceneObject ist ein SceneComponent, das eine Instanz eines "Dings" darstellt, z. B. eine Wand, einen Boden, eine Obergrenze usw. ausgedrückt durch die Kind-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="31b7e-180">A SceneObject is a SceneComponent that represents an instance of a "thing" for example, a wall, a floor, a ceiling, etc.... expressed by their Kind property.</span></span> <span data-ttu-id="31b7e-181">SceneObjects sind geometrisch und verfügen daher über Funktionen und Eigenschaften, die ihre Position im Raum darstellen, jedoch keine geometrische oder logische Struktur enthalten.</span><span class="sxs-lookup"><span data-stu-id="31b7e-181">SceneObjects are geometric, and therefore have functions and properties that represent their location in space, however they don't contain any geometric or logical structure.</span></span> <span data-ttu-id="31b7e-182">Stattdessen verweisen SceneObjects auf andere SceneComponents, insbesondere SceneQuads und SceneMeshes, die die verschiedenen Darstellungen bereitstellen, die vom System unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="31b7e-182">Instead, SceneObjects reference other SceneComponents, specifically SceneQuads, and SceneMeshes, which provide the varied representations that are supported by the system.</span></span> <span data-ttu-id="31b7e-183">Wenn eine neue Szene berechnet wird, zählt Ihre Anwendung höchstwahrscheinlich die SceneObjects der Szene auf, um das zu verarbeiten, was sie interessiert.</span><span class="sxs-lookup"><span data-stu-id="31b7e-183">When a new scene is computed, your application will most likely enumerate the Scene's SceneObjects to process what it's interested in.</span></span>

<span data-ttu-id="31b7e-184">SceneObjects kann eine der folgenden Funktionen aufweisen:</span><span class="sxs-lookup"><span data-stu-id="31b7e-184">SceneObjects can have any one of the following:</span></span>

<table>
<tr>
<th><span data-ttu-id="31b7e-185">SceneObjectKind</span><span class="sxs-lookup"><span data-stu-id="31b7e-185">SceneObjectKind</span></span></th> <th><span data-ttu-id="31b7e-186">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="31b7e-186">Description</span></span></th>
</tr>
<tr><td><span data-ttu-id="31b7e-187">Hintergrund</span><span class="sxs-lookup"><span data-stu-id="31b7e-187">Background</span></span></td><td><span data-ttu-id="31b7e-188">Das SceneObject ist bekannt dafür, dass es <b>sich nicht</b> um eine der anderen erkannten Arten von Szenenobjekten handelt.</span><span class="sxs-lookup"><span data-stu-id="31b7e-188">The SceneObject is known to be <b>not</b> one of the other recognized kinds of scene object.</span></span> <span data-ttu-id="31b7e-189">Diese Klasse sollte nicht mit Unknown verwechselt werden, wobei Background bekanntermaßen nicht "Wall", "Floor", "ceiling" usw. ist. während unbekannt noch nicht kategorisiert ist.</span><span class="sxs-lookup"><span data-stu-id="31b7e-189">This class shouldn't be confused with Unknown where Background is known not to be wall/floor/ceiling etc.... while unknown isn't yet categorized.</span></span></b></td></tr>
<tr><td><span data-ttu-id="31b7e-190">Wall</span><span class="sxs-lookup"><span data-stu-id="31b7e-190">Wall</span></span></td><td><span data-ttu-id="31b7e-191">Eine physische Wand.</span><span class="sxs-lookup"><span data-stu-id="31b7e-191">A physical wall.</span></span> <span data-ttu-id="31b7e-192">Es wird davon ausgegangen, dass Es sich um wähnbare Umgebungsstrukturen handelt.</span><span class="sxs-lookup"><span data-stu-id="31b7e-192">Walls are assumed to be immovable environmental structures.</span></span></td></tr>
<tr><td><span data-ttu-id="31b7e-193">Etage</span><span class="sxs-lookup"><span data-stu-id="31b7e-193">Floor</span></span></td><td><span data-ttu-id="31b7e-194">Etagen sind alle Oberflächen, auf denen sie begehbar sind.</span><span class="sxs-lookup"><span data-stu-id="31b7e-194">Floors are any surfaces on which one can walk.</span></span> <span data-ttu-id="31b7e-195">Hinweis: Dies sind keine Etagen.</span><span class="sxs-lookup"><span data-stu-id="31b7e-195">Note: stairs aren't floors.</span></span> <span data-ttu-id="31b7e-196">Beachten Sie auch, dass Die Etagen eine beliebige begehbare Oberfläche annehmen und daher keine explizite Annahme einer einzelnen Etage besteht.</span><span class="sxs-lookup"><span data-stu-id="31b7e-196">Also note, that floors assume any walkable surface and therefore there's no explicit assumption of a singular floor.</span></span> <span data-ttu-id="31b7e-197">Strukturen auf mehreren Ebenen, Rampen usw. sollte alle als Floor klassifiziert werden.</span><span class="sxs-lookup"><span data-stu-id="31b7e-197">Multi-level structures, ramps etc.... should all classify as floor.</span></span></td></tr>
<tr><td><span data-ttu-id="31b7e-198">Ceiling</span><span class="sxs-lookup"><span data-stu-id="31b7e-198">Ceiling</span></span></td><td><span data-ttu-id="31b7e-199">Die obere Oberfläche eines Raumes.</span><span class="sxs-lookup"><span data-stu-id="31b7e-199">The upper surface of a room.</span></span></td></tr>
<tr><td><span data-ttu-id="31b7e-200">Plattform</span><span class="sxs-lookup"><span data-stu-id="31b7e-200">Platform</span></span></td><td><span data-ttu-id="31b7e-201">Eine große flache Oberfläche, auf der Sie Hologramme platzieren können.</span><span class="sxs-lookup"><span data-stu-id="31b7e-201">A large flat surface on which you could place holograms.</span></span> <span data-ttu-id="31b7e-202">Diese stellen in der Regel Tabellen, Arbeitsflächen und andere große horizontale Oberflächen dar.</span><span class="sxs-lookup"><span data-stu-id="31b7e-202">These tend to represent tables, countertops, and other large horizontal surfaces.</span></span></td></tr>
<tr><td><span data-ttu-id="31b7e-203">World</span><span class="sxs-lookup"><span data-stu-id="31b7e-203">World</span></span></td><td><span data-ttu-id="31b7e-204">Eine reservierte Bezeichnung für geometrische Daten, die von der Bezeichnung unabhängig sind.</span><span class="sxs-lookup"><span data-stu-id="31b7e-204">A reserved label for geometric data that is agnostic to labeling.</span></span> <span data-ttu-id="31b7e-205">Das Gitternetz, das durch Festlegen des EnableWorldMesh-Updateflags generiert wird, wird als world klassifiziert.</span><span class="sxs-lookup"><span data-stu-id="31b7e-205">The mesh generated by setting the EnableWorldMesh update flag would be classified as world.</span></span></td></tr>
<tr><td><span data-ttu-id="31b7e-206">Unbekannt</span><span class="sxs-lookup"><span data-stu-id="31b7e-206">Unknown</span></span></td><td><span data-ttu-id="31b7e-207">Dieses Szenenobjekt muss noch klassifiziert und einer Art zugewiesen werden.</span><span class="sxs-lookup"><span data-stu-id="31b7e-207">This scene object has yet to be classified and assigned a kind.</span></span> <span data-ttu-id="31b7e-208">Dies sollte nicht mit Background verwechselt werden, da es sich bei diesem Objekt um etwas handelt, hat das System noch keine stark genug klassifizierung dafür eingerichtet.</span><span class="sxs-lookup"><span data-stu-id="31b7e-208">This shouldn't be confused with Background, as this object could be anything, the system has just not come up with a strong enough classification for it yet.</span></span></td></tr>
</tr>
</table>

### <a name="scenemesh"></a><span data-ttu-id="31b7e-209">SceneMesh</span><span class="sxs-lookup"><span data-stu-id="31b7e-209">SceneMesh</span></span>

<span data-ttu-id="31b7e-210">Eine SceneMesh ist eine SceneComponent, die die Geometrie beliebiger geometrischer Objekte mithilfe einer Dreiecksliste annähert.</span><span class="sxs-lookup"><span data-stu-id="31b7e-210">A SceneMesh is a SceneComponent that approximates the geometry of arbitrary geometric objects using a triangle list.</span></span> <span data-ttu-id="31b7e-211">SceneMeshes werden in verschiedenen Kontexten verwendet. Sie können Komponenten der wasserdichten Zellstruktur oder als WorldMesh darstellen, das das der Szene zugeordnete Gitternetz für die ungebundene räumliche Zuordnung darstellt.</span><span class="sxs-lookup"><span data-stu-id="31b7e-211">SceneMeshes are used in several different contexts, they can represent components of the watertight cell structure or as the WorldMesh, which represents the unbounded spatial mapping mesh associated with the Scene.</span></span> <span data-ttu-id="31b7e-212">Die index- und vertex-Daten, die mit jedem Gitternetz bereitgestellt werden, verwenden das gleiche vertraute Layout wie die [Scheitelpunkt- und Indexpuffer,](/windows/win32/direct3d9/rendering-from-vertex-and-index-buffers) die zum Rendern von Dreiecksgittern in allen modernen Rendering-APIs verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="31b7e-212">The index and vertex data provided with each mesh uses the same familiar layout as the [vertex and index buffers](/windows/win32/direct3d9/rendering-from-vertex-and-index-buffers) that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="31b7e-213">In Scene Understanding verwenden Gitternetze 32-Bit-Indizes und müssen möglicherweise in Blöcke für bestimmte Rendering-Engines unterteilt werden.</span><span class="sxs-lookup"><span data-stu-id="31b7e-213">In Scene Understanding, meshes use 32-bit indices and may need to be broken up into chunks for certain rendering engines.</span></span>

#### <a name="winding-order-and-coordinate-systems"></a><span data-ttu-id="31b7e-214">Windingreihenfolge und Koordinatensysteme</span><span class="sxs-lookup"><span data-stu-id="31b7e-214">Winding Order and Coordinate Systems</span></span>

<span data-ttu-id="31b7e-215">Von allen von Scene Understanding erzeugten Gitternetzen wird erwartet, dass sie Gitternetze in einem Right-Handed Koordinatensystem zurückgeben, indem sie im Uhrzeigersinn gewunden werden.</span><span class="sxs-lookup"><span data-stu-id="31b7e-215">All meshes produced by Scene Understanding are expected to return meshes in a Right-Handed coordinate system using clockwise winding order.</span></span> 

<span data-ttu-id="31b7e-216">Hinweis: Betriebssystembuilds vor .191105 weisen möglicherweise einen bekannten Fehler auf, bei dem "World"-Gitternetze in Counter-Clockwise Wickelreihenfolge zurückgegeben wurden, die anschließend behoben wurde.</span><span class="sxs-lookup"><span data-stu-id="31b7e-216">Note: OS builds prior to .191105 may have a known bug where "World" meshes were returning in Counter-Clockwise winding order, which has subsequently been fixed.</span></span>

### <a name="scenequad"></a><span data-ttu-id="31b7e-217">SceneQuad</span><span class="sxs-lookup"><span data-stu-id="31b7e-217">SceneQuad</span></span>

<span data-ttu-id="31b7e-218">Ein SceneQuad ist eine SceneComponent, die 2d-Oberflächen darstellt, die die 3D-Welt einnehmen.</span><span class="sxs-lookup"><span data-stu-id="31b7e-218">A SceneQuad is a SceneComponent that represents 2d surfaces that occupy the 3d world.</span></span> <span data-ttu-id="31b7e-219">SceneQuads können ähnlich wie ARKit ARPlaneAnchor oder ARCore Planes verwendet werden, bieten jedoch eine allgemeinere Funktionalität als 2D-Canvass, die von flachen Apps oder einer erweiterten Benutzererfahrung verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="31b7e-219">SceneQuads can be used similarly to ARKit ARPlaneAnchor or ARCore Planes but they offer more high-level functionality as 2d canvases to be used by flat apps, or augmented UX.</span></span> <span data-ttu-id="31b7e-220">2D-spezifische APIs werden für Quader bereitgestellt, die die Verwendung von Platzierung und Layout vereinfachen. Die Entwicklung (mit Ausnahme des Renderings) mit Quadern sollte sich eher wie die Arbeit mit 2D-Canvass als mit 3D-Gitternetzen anfühlen.</span><span class="sxs-lookup"><span data-stu-id="31b7e-220">2D specific APIs are provided for quads that make placement and layout simple to use, and developing (with the exception of rendering) with quads should feel more akin to working with 2d canvases than 3d meshes.</span></span>

#### <a name="scenequad-shape"></a><span data-ttu-id="31b7e-221">SceneQuad-Form</span><span class="sxs-lookup"><span data-stu-id="31b7e-221">SceneQuad shape</span></span>

<span data-ttu-id="31b7e-222">SceneQuads definieren eine umgrenzte rechteckige Oberfläche in 2d.</span><span class="sxs-lookup"><span data-stu-id="31b7e-222">SceneQuads define a bounded rectangular surface in 2d.</span></span> <span data-ttu-id="31b7e-223">SceneQuads stellen jedoch Oberflächen mit beliebigen und potenziell komplexen Formen dar (z. B. eine donutförmige Tabelle). Um die komplexe Form der Oberfläche eines Quaders darzustellen, können Sie die GetSurfaceMask-API verwenden, um die Form der Oberfläche in einem von Ihnen bereitgestellten Bildpuffer zu rendern.</span><span class="sxs-lookup"><span data-stu-id="31b7e-223">However, SceneQuads are representing surfaces with arbitrary and potentially complex shapes (e.g. a donut shaped table.) To represent the complex shape of the surface of a quad you may use the GetSurfaceMask API to render the shape of the surface onto an image buffer you provide.</span></span> <span data-ttu-id="31b7e-224">Wenn das SceneObject mit dem Quader ebenfalls über ein Gitternetz verfügt, sollten die Gittergitterdreiecke diesem gerenderten Bild entsprechen. Beide stellen die echte Geometrie der Oberfläche dar, entweder in 2d- oder 3d-Koordinaten.</span><span class="sxs-lookup"><span data-stu-id="31b7e-224">If the SceneObject that has the quad also has a mesh, the mesh triangles should be equivalent to this rendered image, they both represent real geometry of the surface, either in 2d or 3d coordinates.</span></span>

## <a name="scene-understanding-sdk-details-and-reference"></a><span data-ttu-id="31b7e-225">Details und Referenz zum Scene Understanding SDK</span><span class="sxs-lookup"><span data-stu-id="31b7e-225">Scene understanding SDK details and reference</span></span>

> [!NOTE] 
> <span data-ttu-id="31b7e-226">Beachten Sie bei der Verwendung von MRTK, dass Sie mit MRTKs interagieren [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) und daher diesen Abschnitt in den meisten Fällen überspringen können.</span><span class="sxs-lookup"><span data-stu-id="31b7e-226">When using MRTK, please note you will be interacting with MRTK's [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) and thus may skip this section under most circumstances.</span></span> <span data-ttu-id="31b7e-227">Weitere Informationen finden Sie in der [MRTK Scene Understanding-Dokumentation.](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/scene-understanding)</span><span class="sxs-lookup"><span data-stu-id="31b7e-227">Please refer to the [MRTK Scene Understanding docs](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/scene-understanding) for more information.</span></span>

<span data-ttu-id="31b7e-228">Der folgende Abschnitt hilft Ihnen, sich mit den Grundlagen von SceneUnderstanding vertraut zu machen.</span><span class="sxs-lookup"><span data-stu-id="31b7e-228">The following section will help get you familiar with the basics of SceneUnderstanding.</span></span> <span data-ttu-id="31b7e-229">Dieser Abschnitt sollte Ihnen die Grundlagen bieten. An diesem Punkt sollten Sie über genügend Kontext verfügen, um die Beispielanwendungen zu durchsuchen, um zu sehen, wie SceneUnderstanding ganzheitlicher verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="31b7e-229">This section should provide you with the basics, at which point you should have enough context to browse through the sample applications to see how SceneUnderstanding is used holistically.</span></span>

### <a name="initialization"></a><span data-ttu-id="31b7e-230">Initialisierung</span><span class="sxs-lookup"><span data-stu-id="31b7e-230">Initialization</span></span>

<span data-ttu-id="31b7e-231">Der erste Schritt beim Arbeiten mit SceneUnderstanding besteht darin, dass Ihre Anwendung einen Verweis auf ein Scene-Objekt erhält.</span><span class="sxs-lookup"><span data-stu-id="31b7e-231">The first step to working with SceneUnderstanding is for your application to gain reference to a Scene object.</span></span> <span data-ttu-id="31b7e-232">Dies kann auf zwei Arten erfolgen: Eine Szene kann entweder vom Treiber berechnet werden, oder eine vorhandene Szene, die in der Vergangenheit berechnet wurde, kann deserimetrisiert werden.</span><span class="sxs-lookup"><span data-stu-id="31b7e-232">This can be done in one of two ways, a Scene can either be computed by the driver, or an existing Scene that was computed in the past can be de-serialized.</span></span> <span data-ttu-id="31b7e-233">Letzteres ist nützlich für die Arbeit mit SceneUnderstanding während der Entwicklung, bei der Anwendungen und Erfahrungen schnell ohne ein Mixed Reality-Gerät prototypiert werden können.</span><span class="sxs-lookup"><span data-stu-id="31b7e-233">The latter is useful for working with SceneUnderstanding during development, where applications and experiences can be prototyped quickly without a mixed reality device.</span></span>

<span data-ttu-id="31b7e-234">Szenen werden mithilfe eines SceneObservers berechnet.</span><span class="sxs-lookup"><span data-stu-id="31b7e-234">Scenes are computed using a SceneObserver.</span></span> <span data-ttu-id="31b7e-235">Vor dem Erstellen einer Szene sollte Ihre Anwendung Ihr Gerät abfragen, um sicherzustellen, dass es SceneUnderstanding unterstützt, sowie Benutzerzugriff für Informationen anfordern, die SceneUnderstanding benötigt.</span><span class="sxs-lookup"><span data-stu-id="31b7e-235">Before creating a Scene, your application should query your device to ensure that it supports SceneUnderstanding, as well as to request user access for information that SceneUnderstanding needs.</span></span>

```cs
if (!SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

<span data-ttu-id="31b7e-236">Wenn RequestAccessAsync() nicht aufgerufen wird, schlägt das Berechnen einer neuen Szene fehl.</span><span class="sxs-lookup"><span data-stu-id="31b7e-236">If RequestAccessAsync() is not called, computing a new Scene will fail.</span></span> <span data-ttu-id="31b7e-237">Als Nächstes berechnen wir eine neue Szene, die auf dem Mixed Reality Headset basiert und einen Radius von 10 Metern hat.</span><span class="sxs-lookup"><span data-stu-id="31b7e-237">Next we will compute a new scene that's rooted around the Mixed Reality headset and has a 10-meter radius.</span></span>

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

querySettings.EnableSceneObjectQuads = true;                                       // Requests that the scene updates quads.
querySettings.EnableSceneObjectMeshes = true;                                      // Requests that the scene updates watertight mesh data.
querySettings.EnableOnlyObservedSceneObjects = false;                              // Do not explicitly turn off quad inference.
querySettings.EnableWorldMesh = true;                                              // Requests a static version of the spatial mapping mesh.
querySettings.RequestedMeshLevelOfDetail = SceneMeshLevelOfDetail.Fine;            // Requests the finest LOD of the static spatial mapping mesh.

// Initialize a new Scene
Scene myScene = SceneObserver.ComputeAsync(querySettings, 10.0f).GetAwaiter().GetResult();
```

### <a name="initialization-from-data-also-known-as-the-pc-path"></a><span data-ttu-id="31b7e-238">Initialisierung aus Daten (auch bekannt als .</span><span class="sxs-lookup"><span data-stu-id="31b7e-238">Initialization from Data (also known as.</span></span> <span data-ttu-id="31b7e-239">PC-Pfad)</span><span class="sxs-lookup"><span data-stu-id="31b7e-239">the PC Path)</span></span>

<span data-ttu-id="31b7e-240">Szenen können zwar für die direkte Nutzung berechnet werden, sie können aber auch zur späteren Verwendung in serialisierter Form berechnet werden.</span><span class="sxs-lookup"><span data-stu-id="31b7e-240">While Scenes can be computed for direct consumption, they can also be computed in serialized form for later use.</span></span> <span data-ttu-id="31b7e-241">Dies hat sich als nützlich für die Entwicklung erwiesen, da Entwickler damit Scene Understanding ohne geräteloses Arbeiten und Testen testen können.</span><span class="sxs-lookup"><span data-stu-id="31b7e-241">This has proven to be useful for development as it allows developers to work in and test Scene Understanding without the need for a device.</span></span> <span data-ttu-id="31b7e-242">Die Serialisierung einer Szene ist nahezu identisch mit der Berechnung. Die Daten werden an Ihre Anwendung zurückgegeben, anstatt lokal vom SDK deserialisiert zu werden.</span><span class="sxs-lookup"><span data-stu-id="31b7e-242">The act of serializing a scene is nearly identical to computing it, the data is returned to your application instead of being deserialized locally by the SDK.</span></span> <span data-ttu-id="31b7e-243">Sie können es dann selbst deserialisieren oder zur zukünftigen Verwendung speichern.</span><span class="sxs-lookup"><span data-stu-id="31b7e-243">You may then deserialize it yourself or save it for future use.</span></span>

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

// Compute a scene but serialized as a byte array
SceneBuffer newSceneBuffer = SceneObserver.ComputeSerializedAsync(querySettings, 10.0f).GetAwaiter().GetResult();

// If we want to use it immediately we can de-serialize the scene ourselves
byte[] newSceneData = new byte[newSceneBuffer.Size];
newSceneBuffer.GetData(newSceneData);
Scene mySceneDeSerialized = Scene.Deserialize(newSceneData);

// Save newSceneData for later
```

### <a name="sceneobject-enumeration"></a><span data-ttu-id="31b7e-244">SceneObject-Enumeration</span><span class="sxs-lookup"><span data-stu-id="31b7e-244">SceneObject Enumeration</span></span>

<span data-ttu-id="31b7e-245">Nachdem Ihre Anwendung nun über eine Szene verfügt, wird ihre Anwendung SceneObjects betrachten und mit ihnen interagieren.</span><span class="sxs-lookup"><span data-stu-id="31b7e-245">Now that your application has a scene, your application will be looking at and interacting with SceneObjects.</span></span> <span data-ttu-id="31b7e-246">Dazu greifen Sie auf die **SceneObjects-Eigenschaft** zu:</span><span class="sxs-lookup"><span data-stu-id="31b7e-246">This is done by accessing the **SceneObjects** property:</span></span>

```cs
SceneObject firstFloor = null;

// Find the first floor object
foreach (var sceneObject in myScene.SceneObjects)
{
    if (sceneObject.Kind == SceneObjectKind.Floor)
    {
        firstFloor = sceneObject;
        break;
    }
}
```

### <a name="component-update-and-refinding-components"></a><span data-ttu-id="31b7e-247">Komponentenaktualisierung und Neusuche von Komponenten</span><span class="sxs-lookup"><span data-stu-id="31b7e-247">Component update and refinding components</span></span>

<span data-ttu-id="31b7e-248">Es gibt eine weitere Funktion, die Komponenten in der Szene mit dem Namen ***FindComponent abruft.***</span><span class="sxs-lookup"><span data-stu-id="31b7e-248">There's another function that retrieves components in the Scene called ***FindComponent***.</span></span> <span data-ttu-id="31b7e-249">Diese Funktion ist nützlich, wenn Nachverfolgungsobjekte aktualisiert und in späteren Szenen gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="31b7e-249">This function is useful when updating tracking objects and finding them in later scenes.</span></span> <span data-ttu-id="31b7e-250">Der folgende Code berechnet eine neue Szene relativ zu einer vorherigen Szene und sucht dann den Boden in der neuen Szene.</span><span class="sxs-lookup"><span data-stu-id="31b7e-250">The following code will compute a new scene relative to a previous scene and then find the floor in the new scene.</span></span>

```cs
// Compute a new scene, and tell the system that we want to compute relative to the previous scene
Scene myNextScene = SceneObserver.ComputeAsync(querySettings, 10.0f, myScene).GetAwaiter().GetResult();

// Use the Id for the floor we found last time, and find it again
firstFloor = (SceneObject)myNextScene.FindComponent(firstFloor.Id);

if (firstFloor != null)
{
    // We found it again, we can now update the transforms of all objects we attached to this floor transform
}
```

## <a name="accessing-meshes-and-quads-from-scene-objects"></a><span data-ttu-id="31b7e-251">Zugreifen auf Gitternetze und Quader aus Szenenobjekten</span><span class="sxs-lookup"><span data-stu-id="31b7e-251">Accessing Meshes and Quads from Scene Objects</span></span>

<span data-ttu-id="31b7e-252">Sobald SceneObjects gefunden wurde, möchte Ihre Anwendung höchstwahrscheinlich auf die Daten zugreifen, die in den Quadern/Gitternetzen enthalten sind, aus denen sie besteht.</span><span class="sxs-lookup"><span data-stu-id="31b7e-252">Once SceneObjects have been found your application will most likely want to access the data that is contained in the quads/meshes that it is composed of.</span></span> <span data-ttu-id="31b7e-253">Auf diese Daten wird mit den Eigenschaften ***Quads** _ und _ *_Meshes_** zugegriffen.</span><span class="sxs-lookup"><span data-stu-id="31b7e-253">This data is accessed with the ***Quads** _ and _ *_Meshes_** properties.</span></span> <span data-ttu-id="31b7e-254">Mit dem folgenden Code werden alle Quader und Gitternetze des Floor-Objekts aufzählt.</span><span class="sxs-lookup"><span data-stu-id="31b7e-254">The following code will enumerate all quads and meshes of our floor object.</span></span>

```cs

// Get the transform for the SceneObject
System.Numerics.Matrix4x4 objectToSceneOrigin = firstFloor.GetLocationAsMatrix();

// Enumerate quads
foreach (var quad in firstFloor.Quads)
{
    // Process quads
}

// Enumerate meshes
foreach (var mesh in firstFloor.Meshes)
{
    // Process meshes
}
```

<span data-ttu-id="31b7e-255">Beachten Sie, dass es sich um das SceneObject handelt, das über die Transformation verfügt, die relativ zum Ursprung der Szene ist.</span><span class="sxs-lookup"><span data-stu-id="31b7e-255">Notice that it's the SceneObject that has the transform that is relative to the Scene origin.</span></span> <span data-ttu-id="31b7e-256">Dies liegt daran, dass das SceneObject eine Instanz eines "Dings" darstellt und im Raum veranladbar ist, die Quader und Gitternetze Geometrie darstellen, die relativ zu ihrem übergeordneten Element transformiert wird.</span><span class="sxs-lookup"><span data-stu-id="31b7e-256">This is because the SceneObject represents an instance of a "thing" and is locatable in space, the quads, and meshes represent geometry that is transformed relative to their parent.</span></span> <span data-ttu-id="31b7e-257">Es ist möglich, dass separate SceneObjects auf dieselben SceneMesh/SceneQuad SceneComponents verweisen, und es ist auch möglich, dass ein SceneObject über mehr als eine SceneMesh/SceneQuad verfügt.</span><span class="sxs-lookup"><span data-stu-id="31b7e-257">It's possible for separate SceneObjects to reference the same SceneMesh/SceneQuad SceneComponents, and it's also possible that a SceneObject has more than one SceneMesh/SceneQuad.</span></span>

### <a name="dealing-with-transforms"></a><span data-ttu-id="31b7e-258">Umgang mit Transformationen</span><span class="sxs-lookup"><span data-stu-id="31b7e-258">Dealing with Transforms</span></span>

<span data-ttu-id="31b7e-259">Scene Understanding hat einen absichtlichen Versuch unternommen, sich beim Umgang mit Transformationen an herkömmlichen 3D-Szenendarstellungen auszurichten.</span><span class="sxs-lookup"><span data-stu-id="31b7e-259">Scene Understanding has made a deliberate attempt to align with traditional 3D scene representations when dealing with transforms.</span></span> <span data-ttu-id="31b7e-260">Jede Szene ist daher auf ein einzelnes Koordinatensystem beschränkt, ähnlich wie die meisten gängigen 3D-Umgebungsdarstellungen.</span><span class="sxs-lookup"><span data-stu-id="31b7e-260">Each Scene is therefore confined to a single coordinate system much like most common 3D environmental representations.</span></span> <span data-ttu-id="31b7e-261">SceneObjects geben jeweils ihre Position relativ zu diesem Koordinatensystem an.</span><span class="sxs-lookup"><span data-stu-id="31b7e-261">SceneObjects each provide their location relative to that coordinate system.</span></span> <span data-ttu-id="31b7e-262">Wenn Ihre Anwendung mit Szenen zu tun hat, die die Grenze des von einem einzelnen Ursprung bereitgestellten Objekts ausdehnen, kann sie SceneObjects in SpatialAnchors verankern oder mehrere Szenen generieren und zusammenführen. Der Einfachheit halber gehen wir jedoch davon aus, dass sich wässrige Szenen in ihrem eigenen Ursprung befinden, der durch eine NodeId lokalisiert ist, die durch Scene.OriginSpatialGraphNodeId definiert wird.</span><span class="sxs-lookup"><span data-stu-id="31b7e-262">If your application is dealing with Scenes that stretch the limit of what a single origin provides it can anchor SceneObjects to SpatialAnchors, or generate several scenes and merge them together, but for simplicity we assume that watertight scenes exist in their own origin that's localized by one NodeId defined by Scene.OriginSpatialGraphNodeId.</span></span>

<span data-ttu-id="31b7e-263">Der folgende Unity-Code zeigt beispielsweise, wie Sie Windows Perception- und Unity-APIs verwenden, um Koordinatensysteme zusammen auszurichten.</span><span class="sxs-lookup"><span data-stu-id="31b7e-263">The following Unity code, for example, shows how to use Windows Perception and Unity APIs to align coordinate systems together.</span></span> <span data-ttu-id="31b7e-264">Ausführliche Informationen zu den Windows Perception-APIs finden Sie unter [SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) und [SpatialGraphInteropPreview](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) und [Mixed Reality nativen Objekte in Unity,](/windows/mixed-reality/unity-xrdevice-advanced) um Details zum Abrufen eines SpatialCoordinateSystem zu erhalten, das dem Ursprung von Unity entspricht.</span><span class="sxs-lookup"><span data-stu-id="31b7e-264">See [SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) and [SpatialGraphInteropPreview](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) for details on the Windows Perception APIs, and [Mixed Reality native objects in Unity](/windows/mixed-reality/unity-xrdevice-advanced) for details on obtaining a SpatialCoordinateSystem that corresponds to Unity's world origin.</span></span>

```cs
private System.Numerics.Matrix4x4? GetSceneToUnityTransformAsMatrix4x4(SceneUnderstanding.Scene scene)
{

      System.Numerics.Matrix4x4? sceneToUnityTransform = System.Numerics.Matrix4x4.Identity;

      Windows.Perception.Spatial.SpatialCoordinateSystem sceneCoordinateSystem = Microsoft.Windows.Perception.Spatial.Preview.SpatialGraphInteropPreview.CreateCoordinateSystemForNode(scene.OriginSpatialGraphNodeId);
      HolograhicFrameData holoFrameData =  Marshal.PtrToStructure<HolograhicFrameData>(UnityEngine.XR.XRDevice.GetNativePtr());
      Windows.Perception.Spatial.SpatialCoordinateSystem unityCoordinateSystem = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(holoFrameData.ISpatialCoordinateSystemPtr);

      sceneToUnityTransform = sceneCoordinateSystem.TryGetTransformTo(unityCoordinateSystem);

      if(sceneToUnityTransform != null)
      {
          sceneToUnityTransform = ConvertRightHandedMatrix4x4ToLeftHanded(sceneToUnityTransform.Value);
      }
      else
      {
          return null;
      }

    return sceneToUnityTransform;
}
```

<span data-ttu-id="31b7e-265">Jede `SceneObject` verfügt über eine Transformation, die dann auf dieses Objekt angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="31b7e-265">Each `SceneObject` has a transform, which is then applied to that object.</span></span> <span data-ttu-id="31b7e-266">In Unity konvertieren wir in rechtshändige Koordinaten und weisen lokale Transformationen zu:</span><span class="sxs-lookup"><span data-stu-id="31b7e-266">In Unity we convert to right handed coordinates and assign local transforms as so:</span></span>

```cs
private System.Numerics.Matrix4x4 ConvertRightHandedMatrix4x4ToLeftHanded(System.Numerics.Matrix4x4 matrix)
{
    matrix.M13 = -matrix.M13;
    matrix.M23 = -matrix.M23;
    matrix.M43 = -matrix.M43;

    matrix.M31 = -matrix.M31;
    matrix.M32 = -matrix.M32;
    matrix.M34 = -matrix.M34;

    return matrix;
}

 private void SetUnityTransformFromMatrix4x4(Transform targetTransform, System.Numerics.Matrix4x4 matrix, bool updateLocalTransformOnly = false)
 {
    if(targetTransform == null)
    {
        return;
    }

    Vector3 unityTranslation;
    Quaternion unityQuat;
    Vector3 unityScale;

    System.Numerics.Vector3 vector3;
    System.Numerics.Quaternion quaternion;
    System.Numerics.Vector3 scale;

    System.Numerics.Matrix4x4.Decompose(matrix, out scale, out quaternion, out vector3);

    unityTranslation = new Vector3(vector3.X, vector3.Y, vector3.Z);
    unityQuat        = new Quaternion(quaternion.X, quaternion.Y, quaternion.Z, quaternion.W);
    unityScale       = new Vector3(scale.X, scale.Y, scale.Z);

    if(updateLocalTransformOnly)
    {
        targetTransform.localPosition = unityTranslation;
        targetTransform.localRotation = unityQuat;
    }
    else
    {
        targetTransform.SetPositionAndRotation(unityTranslation, unityQuat);
    }
}

// Assume we have an SU object called suObject and a unity equivalent unityObject

System.Numerics.Matrix4x4 converted4x4LocationMatrix = ConvertRightHandedMatrix4x4ToLeftHanded(suObject.GetLocationAsMatrix());
SetUnityTransformFromMatrix4x4(unityObject.transform, converted4x4LocationMatrix, true);
        
```

### <a name="quad"></a><span data-ttu-id="31b7e-267">Viereck</span><span class="sxs-lookup"><span data-stu-id="31b7e-267">Quad</span></span>

<span data-ttu-id="31b7e-268">Quads wurden entwickelt, um 2D-Platzierungsszenarien zu unterstützen, und sollten als Erweiterungen für 2D-Canvas-UX-Elemente gedacht werden.</span><span class="sxs-lookup"><span data-stu-id="31b7e-268">Quads were designed to help 2D placement scenarios and should be thought of as extensions to 2D canvas UX elements.</span></span> <span data-ttu-id="31b7e-269">Während Quads Komponenten von SceneObjects sind und in 3D gerendert werden können, gehen die Quad-APIs selbst davon aus, dass Quads 2D-Strukturen sind.</span><span class="sxs-lookup"><span data-stu-id="31b7e-269">While Quads are components of SceneObjects and can be rendered in 3D, the Quad APIs themselves assume Quads are 2D structures.</span></span> <span data-ttu-id="31b7e-270">Sie bieten Informationen wie "extent", "shape" und "provide APIs for placement".</span><span class="sxs-lookup"><span data-stu-id="31b7e-270">They offer information such as extent, shape, and provide APIs for placement.</span></span>

<span data-ttu-id="31b7e-271">Quader verfügen über rechteckige Kästchen, stellen aber beliebig formatierte 2D-Oberflächen dar.</span><span class="sxs-lookup"><span data-stu-id="31b7e-271">Quads have rectangular extents, but they represent arbitrarily shaped 2D surfaces.</span></span> <span data-ttu-id="31b7e-272">Um die Platzierung auf diesen 2D-Oberflächen zu ermöglichen, die mit den 3D-Umgebungsquads interagieren, bieten Quads Hilfsprogramme, um diese Interaktion zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="31b7e-272">To enable placement on these 2D surfaces that interact with the 3D environment quads offer utilities to make this interaction possible.</span></span> <span data-ttu-id="31b7e-273">Scene Understanding bietet derzeit zwei solche Funktionen: **FindCentermostPlacement** und **GetSurfaceMask.**</span><span class="sxs-lookup"><span data-stu-id="31b7e-273">Currently Scene Understanding provides two such functions, **FindCentermostPlacement** and **GetSurfaceMask**.</span></span> <span data-ttu-id="31b7e-274">FindCentermostPlacement ist eine high-level-API, die eine Position auf dem Quader sucht, an der ein Objekt platziert werden kann, und versucht, den besten Speicherort für Ihr Objekt zu finden, wodurch sichergestellt wird, dass der von Ihnen bereitgestellte Begrenzungsfeld auf der zugrunde liegenden Oberfläche verbleibt.</span><span class="sxs-lookup"><span data-stu-id="31b7e-274">FindCentermostPlacement is a high-level API that locates a position on the quad where an object can be placed and will try to find the best location for your object guaranteeing that the bounding box you provide will stay on the underlying surface.</span></span>

> [!NOTE]
> <span data-ttu-id="31b7e-275">Die Koordinaten der Ausgabe sind relativ zum Quader im "Quad space", wobei die linke obere Ecke (x = 0, y = 0) ist, genau wie bei anderen Rect-Typen von Fenstern.</span><span class="sxs-lookup"><span data-stu-id="31b7e-275">The coordinates of the output are relative to the quad in "quad space" with the top left corner being (x = 0, y = 0), just as it would be with other windows Rect types.</span></span> <span data-ttu-id="31b7e-276">Berücksichtigen Sie dies unbedingt, wenn Sie mit den Ursprüngen Ihrer eigenen Objekte arbeiten.</span><span class="sxs-lookup"><span data-stu-id="31b7e-276">Be sure to take this into account when working with the origins of your own objects.</span></span> 

<span data-ttu-id="31b7e-277">Im folgenden Beispiel wird gezeigt, wie Sie die ortsmittelbarste Position finden und ein Hologramm am Quader ankert.</span><span class="sxs-lookup"><span data-stu-id="31b7e-277">The following example shows how to find the centermost placeable location and anchor a hologram to the quad.</span></span>

```cs
// This code assumes you already have a "Root" object that attaches the Scene's Origin.

// Find the first quad
foreach (var sceneObject in myScene.SceneObjects)
{
    // Find a wall
    if (sceneObject.Kind == SceneObjectKind.Wall)
    {
        // Get the quad
        var quads = sceneObject.Quads;
        if (quads.Count > 0)
        {
            // Find a good location for a 1mx1m object  
            System.Numerics.Vector2 location;
            if (quads[0].FindCentermostPlacement(new System.Numerics.Vector2(1.0f, 1.0f), out location))
            {
                // We found one, anchor something to the transform
                // Step 1: Create a new game object for the quad itself as a child of the scene root
                // Step 2: Set the local transform from quads[0].Position and quads[0].Orientation
                // Step 3: Create your hologram and set it as a child of the quad's game object
                // Step 4: Set the hologram's local transform to a translation (location.x, location.y, 0)
            }
        }
    }
}
```

<span data-ttu-id="31b7e-278">Die Schritte 1 bis 4 hängen stark von Ihrem spezifischen Framework bzw. Ihrer Implementierung ab, die Designs sollten jedoch ähnlich sein.</span><span class="sxs-lookup"><span data-stu-id="31b7e-278">Steps 1-4 are highly dependent on your particular framework/implementation, but the themes should be similar.</span></span> <span data-ttu-id="31b7e-279">Es ist wichtig zu beachten, dass der Quader einfach eine umgrenzte 2D-Ebene darstellt, die im Raum lokalisiert ist.</span><span class="sxs-lookup"><span data-stu-id="31b7e-279">It's important to note that the Quad simply represents a bounded 2D plane that is localized in space.</span></span> <span data-ttu-id="31b7e-280">Wenn Ihre Engine/Ihr Framework weiß, wo sich das Quad befindet, und Ihre Objekte relativ zum Quader stammen, werden Ihre Hologramme in Bezug auf die reale Welt korrekt angeordnet.</span><span class="sxs-lookup"><span data-stu-id="31b7e-280">By having your engine/framework know where the quad is and rooting your objects relative to the quad, your holograms will be located correctly with respect to the real world.</span></span> 

<!-- 
// TODO: Add sample link when released
For more detailed information please see our samples on quads which show specific implementations.
-->

### <a name="mesh"></a><span data-ttu-id="31b7e-281">Mesh</span><span class="sxs-lookup"><span data-stu-id="31b7e-281">Mesh</span></span>

<span data-ttu-id="31b7e-282">Gittermodelle stellen geometrische Darstellungen von Objekten oder Umgebungen dar.</span><span class="sxs-lookup"><span data-stu-id="31b7e-282">Meshes represent geometric representations of objects or environments.</span></span> <span data-ttu-id="31b7e-283">Ähnlich wie [bei der räumlichen Zuordnung](../../design/spatial-mapping.md)verwenden Gitterindex- und Vertexdaten, die mit jedem Raumoberflächengitternetz bereitgestellt werden, das gleiche vertraute Layout wie die Scheitelpunkt- und Indexpuffer, die zum Rendern von Dreiecksgitternetzen in allen modernen Rendering-APIs verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="31b7e-283">Much like [spatial mapping](../../design/spatial-mapping.md), mesh index and vertex data provided with each spatial surface mesh uses the same familiar layout as the vertex and index buffers that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="31b7e-284">Scheitelpunktpositionen werden im Koordinatensystem des `Scene` bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="31b7e-284">Vertex positions are provided in the coordinate system of the `Scene`.</span></span> <span data-ttu-id="31b7e-285">Die spezifischen APIs, die zum Verweisen auf diese Daten verwendet werden, lauten wie folgt:</span><span class="sxs-lookup"><span data-stu-id="31b7e-285">The specific APIs used to reference this data are as follows:</span></span>

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(System.Numerics.Vector3[] vertices);
```

<span data-ttu-id="31b7e-286">Der folgende Code enthält ein Beispiel für das Generieren einer Dreiecksliste aus der Gitternetzstruktur:</span><span class="sxs-lookup"><span data-stu-id="31b7e-286">The following code provides an example of generating a triangle list from the mesh structure:</span></span>

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
System.Numerics.Vector3[] positions = new System.Numerics.Vector3[mesh.VertexCount];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

<span data-ttu-id="31b7e-287">Die Index-/Scheitelpunktpuffer müssen >= index/vertex counts sein, können aber andernfalls beliebig dimensioniert werden, um eine effiziente Speicherwiederverwendung zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="31b7e-287">The index/vertex buffers must be >= the index/vertex counts, but otherwise can be arbitrarily sized allowing for efficient memory reuse.</span></span>

### <a name="collidermesh"></a><span data-ttu-id="31b7e-288">ColliderMesh</span><span class="sxs-lookup"><span data-stu-id="31b7e-288">ColliderMesh</span></span>

<span data-ttu-id="31b7e-289">Szenenobjekte ermöglichen den Zugriff auf Mesh- und Collidermeshdaten über die Eigenschaften Meshes und ColliderMeshes.</span><span class="sxs-lookup"><span data-stu-id="31b7e-289">Scene objects provide access to mesh and collider mesh data via the Meshes and ColliderMeshes properties.</span></span> <span data-ttu-id="31b7e-290">Diese Gitternetze stimmen immer überein, was bedeutet, dass der i'th-Index der Meshes-Eigenschaft die gleiche Geometrie wie der i'th-Index der ColliderMeshes-Eigenschaft darstellt.</span><span class="sxs-lookup"><span data-stu-id="31b7e-290">These meshes will always match, meaning that the i'th index of the Meshes property represents the same geometry as the i'th index of the ColliderMeshes property.</span></span> <span data-ttu-id="31b7e-291">Wenn die Laufzeit bzw. das Objekt Collidergitternetze unterstützt, erhalten Sie garantiert das niedrigste Polygon und die höchste Näherung der Reihenfolge, und es empfiehlt sich, ColliderMeshes überall dort zu verwenden, wo Ihre Anwendung Collider verwenden würde.</span><span class="sxs-lookup"><span data-stu-id="31b7e-291">If the runtime/object supports collider meshes, you are guaranteed to get the lowest polygon, highest order approximation and it's good practice to use ColliderMeshes wherever your application would use colliders.</span></span> <span data-ttu-id="31b7e-292">Wenn das System keine Collider unterstützt, ist das in ColliderMeshes zurückgegebene Mesh-Objekt dasselbe Objekt wie das Gittermodell, das Arbeitsspeichereinschränkungen reduziert.</span><span class="sxs-lookup"><span data-stu-id="31b7e-292">If the system does not support colliders the Mesh object returned in ColliderMeshes will be the same object as the mesh reducing memory constraints.</span></span>

## <a name="developing-with-scene-understanding"></a><span data-ttu-id="31b7e-293">Entwickeln mit Szenenverständnis</span><span class="sxs-lookup"><span data-stu-id="31b7e-293">Developing with scene understanding</span></span>

<span data-ttu-id="31b7e-294">An diesem Punkt sollten Sie die grundlegenden Bausteine der Szene verstehen, die Laufzeit und SDK verstehen.</span><span class="sxs-lookup"><span data-stu-id="31b7e-294">At this point, you should understand the core building blocks of the scene understanding runtime and SDK.</span></span> <span data-ttu-id="31b7e-295">Der Großteil der Leistungsfähigkeit und Komplexität liegt in Zugriffsmustern, der Interaktion mit 3D-Frameworks und Tools, die auf diesen APIs geschrieben werden können, um komplexere Aufgaben wie räumliche Planung, Raumanalyse, Navigation, Physik usw. auszuführen.</span><span class="sxs-lookup"><span data-stu-id="31b7e-295">The bulk of the power and complexity lies in access patterns, interaction with 3D frameworks, and tools that can be written on top of these APIs to do more advanced tasks like spatial planning, room analysis, navigation, physics, and so on.</span></span> <span data-ttu-id="31b7e-296">Wir hoffen, diese in Beispielen erfassen zu können, die Sie hoffentlich in die richtige Richtung führen sollten, um Ihre Szenarien zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="31b7e-296">We hope to capture these in samples that should hopefully guide you in the proper direction to make your scenarios shine.</span></span> <span data-ttu-id="31b7e-297">Wenn es Beispiele oder Szenarien gibt, die wir nicht behandeln, teilen Sie uns dies mit, und wir versuchen, die benötigten Informationen zu dokumentieren bzw. einen Prototyp zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="31b7e-297">If there are samples or scenarios we aren't addressing, let us know and we'll try to document/prototype what you need.</span></span>

### <a name="where-can-i-get-sample-code"></a><span data-ttu-id="31b7e-298">Wo erhalte ich Beispielcode?</span><span class="sxs-lookup"><span data-stu-id="31b7e-298">Where can I get sample code?</span></span>

<span data-ttu-id="31b7e-299">Scene Understanding-Beispielcode für Unity finden Sie auf unserer [Unity-Beispielseite.](https://github.com/sceneunderstanding-microsoft/unitysample)</span><span class="sxs-lookup"><span data-stu-id="31b7e-299">Scene Understanding sample code for Unity can be found on our [Unity Sample Page](https://github.com/sceneunderstanding-microsoft/unitysample) page.</span></span> <span data-ttu-id="31b7e-300">Mit dieser Anwendung können Sie mit Ihrem Gerät kommunizieren und die verschiedenen Szenenobjekte rendern, oder Sie können eine serialisierte Szene auf Ihrem PC laden und Scene Understanding ohne Gerät erleben.</span><span class="sxs-lookup"><span data-stu-id="31b7e-300">This application will allow you to communicate with your device and render the various scene objects, or, it will allow you to load a serialized scene on your PC and allow you to experience Scene Understanding without a device.</span></span>

### <a name="where-can-i-get-sample-scenes"></a><span data-ttu-id="31b7e-301">Wo finde ich Beispielszenen?</span><span class="sxs-lookup"><span data-stu-id="31b7e-301">Where can I get sample scenes?</span></span>

<span data-ttu-id="31b7e-302">Wenn Sie über eine HoloLens2 verfügen, können Sie jede von Ihnen erfasste Szene speichern, indem Sie die Ausgabe von ComputeSerializedAsync in einer Datei speichern und nach Beholholen deserialisieren.</span><span class="sxs-lookup"><span data-stu-id="31b7e-302">If you have a HoloLens2, you can save any scene you've captured by saving the output of ComputeSerializedAsync to file and deserializing it at your own convenience.</span></span> 

<span data-ttu-id="31b7e-303">Wenn Sie kein HoloLens2-Gerät haben, aber mit Scene Understanding spielen möchten, müssen Sie eine vorab erfasste Szene herunterladen.</span><span class="sxs-lookup"><span data-stu-id="31b7e-303">If you don't have a HoloLens2 device but want to play with Scene Understanding, you'll need to download a pre-captured scene.</span></span> <span data-ttu-id="31b7e-304">Das Scene Understanding-Beispiel wird derzeit mit serialisierten Szenen bereitgestellt, die heruntergeladen und nach Behebung verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="31b7e-304">The Scene Understanding sample currently ships with serialized scenes that can be downloaded and used at your own convenience.</span></span> <span data-ttu-id="31b7e-305">Sie finden sie hier:</span><span class="sxs-lookup"><span data-stu-id="31b7e-305">You can find them here:</span></span>

[<span data-ttu-id="31b7e-306">Szenenverständnis von Beispielszenen</span><span class="sxs-lookup"><span data-stu-id="31b7e-306">Scene Understanding Sample Scenes</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

## <a name="see-also"></a><span data-ttu-id="31b7e-307">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="31b7e-307">See also</span></span>

* [<span data-ttu-id="31b7e-308">Räumliche Abbildung</span><span class="sxs-lookup"><span data-stu-id="31b7e-308">Spatial mapping</span></span>](../../design/spatial-mapping.md)
* [<span data-ttu-id="31b7e-309">Grundlegendes zu Szenen</span><span class="sxs-lookup"><span data-stu-id="31b7e-309">Scene understanding</span></span>](../../design/scene-understanding.md)
* [<span data-ttu-id="31b7e-310">Unity-Beispiel</span><span class="sxs-lookup"><span data-stu-id="31b7e-310">Unity Sample</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)