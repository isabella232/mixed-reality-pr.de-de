---
title: Scene understanding SDK
description: Erfahren Sie, wie Sie das Scene Understanding SDK installieren und verwenden, einschließlich Komponenten, Gitternetzen und Objekten in Mixed Reality-Apps.
author: szymons
ms.author: szymons
ms.date: 12/14/2020
ms.topic: article
keywords: Scene Understanding, Spatial Mapping, Windows Mixed Reality, Unity
ms.openlocfilehash: 2f6e0c9d0370caed2b2bc01399b9e4fc00836556
ms.sourcegitcommit: 0c717ed0043c7a65e2caf1452eb0f49059cdf154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2021
ms.locfileid: "108644836"
---
# <a name="scene-understanding-sdk-overview"></a><span data-ttu-id="cb4f5-104">Übersicht über das Scene Understanding SDK</span><span class="sxs-lookup"><span data-stu-id="cb4f5-104">Scene understanding SDK overview</span></span>

<span data-ttu-id="cb4f5-105">Scene Understanding transformiert die Sensordaten der unstrukturierten Umgebung, die ihr Mixed Reality Gerät erfasst und in eine leistungsfähige abstrakte Darstellung umwandelt.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-105">Scene understanding transforms the unstructured environment sensor data that your Mixed Reality device captures and converts it into a powerful abstract representation.</span></span> <span data-ttu-id="cb4f5-106">Das SDK fungiert als Kommunikationsschicht zwischen Ihrer Anwendung und der Scene Understanding-Runtime.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-106">The SDK acts as the communication layer between your application and the Scene Understanding runtime.</span></span> <span data-ttu-id="cb4f5-107">Es soll vorhandene Standardkonstrukte imitieren, z. B. 3D-Szenendiagramme für 3D-Darstellungen und 2D-Rechtecke und -Bereiche für 2D-Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-107">It's aimed to mimic existing standard constructs, such as 3D scene graphs for 3D representations, and 2D rectangles and panels for 2D applications.</span></span> <span data-ttu-id="cb4f5-108">Während die Scene Understanding-Konstrukte konkreten Frameworks zugeordnet werden, ist SceneUnderstanding im Allgemeinen frameworkunabhängig und ermöglicht die Interoperabilität zwischen verschiedenen Frameworks, die damit interagieren.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-108">While the constructs Scene Understanding mimics will map to concrete frameworks, in general SceneUnderstanding is framework agnostic allowing for interoperability between varied frameworks that interact with it.</span></span> <span data-ttu-id="cb4f5-109">Mit der Weiterentwicklung von Scene Understanding besteht die Rolle des SDK darin, sicherzustellen, dass neue Darstellungen und Funktionen in einem einheitlichen Framework weiterhin verfügbar gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-109">As Scene Understanding evolves the role of the SDK is to ensure new representations and capabilities continue to be exposed within a unified framework.</span></span> <span data-ttu-id="cb4f5-110">In diesem Dokument werden zunächst konzepte auf hoher Ebene vorgestellt, die Ihnen helfen, sich mit der Entwicklungsumgebung/-verwendung vertraut zu machen und dann eine ausführlichere Dokumentation für bestimmte Klassen und Konstrukte bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-110">In this document, we will first introduce high-level concepts that will help you get familiar with the development environment/usage and then provide more detailed documentation for specific classes and constructs.</span></span>

## <a name="where-do-i-get-the-sdk"></a><span data-ttu-id="cb4f5-111">Wo erhalte ich das SDK?</span><span class="sxs-lookup"><span data-stu-id="cb4f5-111">Where do I get the SDK?</span></span>

<span data-ttu-id="cb4f5-112">Das SceneUnderstanding SDK kann über das [Mixed Reality Feature Tool](../unity/welcome-to-mr-feature-tool.md)heruntergeladen werden.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-112">The SceneUnderstanding SDK is downloadable via the [Mixed Reality Feature Tool](../unity/welcome-to-mr-feature-tool.md).</span></span>

<span data-ttu-id="cb4f5-113">**Hinweis:** Die neueste Version hängt von Vorschaupaketen ab, und Sie müssen Vorabversionspakete aktivieren, um sie anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-113">**Note:** the latest release depends on preview packages and you'll need to enable pre-release packages to see it.</span></span>

<span data-ttu-id="cb4f5-114">Für Version 0.5.2022-rc und höher unterstützt Scene Understanding Sprachprojektionen für C# und C++, sodass Anwendungen Anwendungen für Win32- oder UWP-Plattformen entwickeln können.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-114">For version 0.5.2022-rc and later, Scene Understanding supports language projections for C# and C++ allowing applications to develop applications for Win32 or UWP platforms.</span></span> <span data-ttu-id="cb4f5-115">Ab dieser Version unterstützt SceneUnderstanding die Unity-Unterstützung im Editor, die den SceneObserver aussperrt, der ausschließlich für die Kommunikation mit HoloLens2 verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-115">As of this version, SceneUnderstanding supports unity in-editor support barring the SceneObserver, which is used solely for communicating with HoloLens2.</span></span> 

<span data-ttu-id="cb4f5-116">SceneUnderstanding erfordert Windows SDK Version 18362 oder höher.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-116">SceneUnderstanding requires Windows SDK version 18362 or higher.</span></span> 

## <a name="conceptual-overview"></a><span data-ttu-id="cb4f5-117">Konzeptionelle Übersicht</span><span class="sxs-lookup"><span data-stu-id="cb4f5-117">Conceptual Overview</span></span>

### <a name="the-scene"></a><span data-ttu-id="cb4f5-118">Die Szene</span><span class="sxs-lookup"><span data-stu-id="cb4f5-118">The Scene</span></span>

<span data-ttu-id="cb4f5-119">Ihr Mixed Reality-Gerät integriert ständig Informationen darüber, was es in Ihrer Umgebung sieht.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-119">Your mixed reality device is constantly integrating information about what it sees in your environment.</span></span> <span data-ttu-id="cb4f5-120">Scene Understanding trichtert alle diese Datenquellen und erzeugt eine einzelne kohäsive Abstraktion.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-120">Scene Understanding funnels all of these data sources and produces one single cohesive abstraction.</span></span> <span data-ttu-id="cb4f5-121">Scene Understanding generiert Szenen, bei denen es sich um eine Komposition von [SceneObjects](scene-understanding-SDK.md#sceneobjects) handelt, die eine Instanz eines einzelnen Objekts darstellen (z. B. eine Wand, eine Decke oder einen Boden). Szenenobjekte selbst sind eine Komposition von [SceneComponents, die präzisere Teile darstellen, aus denen sich dieses SceneObject zusammensetzen.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-121">Scene Understanding generates Scenes, which are a composition of [SceneObjects](scene-understanding-SDK.md#sceneobjects) that represent an instance of a single thing, (for example, a wall/ceiling/floor.) Scene Objects themselves are a composition of [SceneComponents, which represent more granular pieces that make up this SceneObject.</span></span> <span data-ttu-id="cb4f5-122">Beispiele für Komponenten sind Quads und Gitter, aber in Zukunft könnten Begrenzungsfelder, Kollisionsgitter, Metadaten usw. stehen.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-122">Examples of components are quads and meshes, but in the future could represent bounding boxes, collision meshes, metadata etc.</span></span>

<span data-ttu-id="cb4f5-123">Der Prozess der Konvertierung der rohen Sensordaten in eine Szene ist ein potenziell kostspieliger Vorgang, der bei großen Räumen (ca. 50 x 50 m) Sekunden für mittlere Räume (ca. 10 x 10 m) in Minuten dauern kann und daher nicht ohne Anwendungsanforderung vom Gerät berechnet wird.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-123">The process of converting the raw sensor data into a Scene is a potentially expensive operation that could take seconds for medium spaces (~10x10m) to minutes for large spaces (~50x50m) and therefore it is not something that is being computed by the device without application request.</span></span> <span data-ttu-id="cb4f5-124">Stattdessen wird die Szenengenerierung von Ihrer Anwendung bei Bedarf ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-124">Instead, Scene generation is triggered by your application on demand.</span></span> <span data-ttu-id="cb4f5-125">Die SceneObserver-Klasse verfügt über statische Methoden, die eine Szene berechnen oder deserialisieren können, mit denen Sie dann aufzählen/interagieren können.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-125">The SceneObserver class has static methods that can Compute or Deserialize a scene, which you can then enumerate/interact with.</span></span> <span data-ttu-id="cb4f5-126">Die Aktion "Compute" wird bei Bedarf ausgeführt und auf der CPU ausgeführt, jedoch in einem separaten Prozess (Mixed Reality Treiber).</span><span class="sxs-lookup"><span data-stu-id="cb4f5-126">The "Compute" action is executed on-demand and executes on the CPU but in a separate process (the Mixed Reality Driver).</span></span> <span data-ttu-id="cb4f5-127">Während wir jedoch in einem anderen Prozess berechnen, werden die resultierenden Szenendaten in Ihrer Anwendung im Szenenobjekt gespeichert und verwaltet.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-127">However, while we do compute in another process the resulting Scene data is stored and maintained in your application in the Scene object.</span></span> 

<span data-ttu-id="cb4f5-128">Das folgende Diagramm veranschaulicht diesen Prozessablauf und zeigt Beispiele für zwei Anwendungen, die mit der Scene Understanding-Runtime zusammenarbeiten.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-128">Below is a diagram that illustrates this process flow and shows examples of two applications interfacing with the Scene Understanding runtime.</span></span> 

![Prozessdiagramm](images/SU-ProcessFlow.png)

<span data-ttu-id="cb4f5-130">Auf der linken Seite befindet sich ein Diagramm der Mixed Reality-Runtime, die immer in einem eigenen Prozess ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-130">On the left-hand side is a diagram of the mixed reality runtime, which is always on and running in its own process.</span></span> <span data-ttu-id="cb4f5-131">Diese Runtime ist für die Durchführung von Gerätenachverfolgung, räumlicher Zuordnung und anderen Vorgängen verantwortlich, die Scene Understanding verwendet, um die Welt um Sie herum zu verstehen und zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-131">This runtime is responsible for performing device tracking, spatial mapping, and other operations that Scene Understanding uses to understand and reason about the world around you.</span></span> <span data-ttu-id="cb4f5-132">Auf der rechten Seite des Diagramms zeigen wir zwei theoretische Anwendungen, die Scene Understanding verwenden.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-132">On the right side of the diagram, we show two theoretical applications that make use of Scene Understanding.</span></span> <span data-ttu-id="cb4f5-133">Die erste Anwendung ist mit MRTK verbunden, die intern das Scene Understanding SDK verwendet, die zweite App berechnet und verwendet zwei separate Szeneninstanzen.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-133">The first application interfaces with MRTK, which uses the Scene Understanding SDK internally, the second app computes and uses two separate scene instances.</span></span> <span data-ttu-id="cb4f5-134">Alle drei Szenen in diesem Diagramm generieren unterschiedliche Instanzen der Szenen. Der Treiber verfolgt den globalen Zustand, der von Anwendungen gemeinsam genutzt wird, und Szenenobjekte in einer Szene nicht in einer anderen Szene.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-134">All three Scenes in this diagram generate distinct instances of the scenes, the driver isn't tracking global state that is shared between applications and Scene Objects in one scene aren't found in another.</span></span> <span data-ttu-id="cb4f5-135">Scene Understanding bietet einen Mechanismus, der im Laufe der Zeit nachverfolgt werden kann, aber dies erfolgt mithilfe des SDK.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-135">Scene Understanding does provide a mechanism to track over time, but this is done using the SDK.</span></span> <span data-ttu-id="cb4f5-136">Der Nachverfolgungscode wird bereits im SDK im Prozess Ihrer App ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-136">Tracking code is already running in the SDK in your app's process.</span></span>

<span data-ttu-id="cb4f5-137">Da jede Szene ihre Daten im Arbeitsspeicher Ihrer Anwendung speichert, können Sie davon ausgehen, dass die gesamte Funktion des Scene-Objekts oder seine internen Daten immer im Prozess Ihrer Anwendung ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-137">Because each Scene stores it's data in your application's memory space, you can assume that all function of the Scene object or it's internal data is always executed in your application's process.</span></span>

### <a name="layout"></a><span data-ttu-id="cb4f5-138">Layout</span><span class="sxs-lookup"><span data-stu-id="cb4f5-138">Layout</span></span>

<span data-ttu-id="cb4f5-139">Für die Arbeit mit Scene Understanding kann es hilfreich sein, zu wissen und zu verstehen, wie die Laufzeit Komponenten logisch und physisch darstellt.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-139">To work with Scene Understanding, it may be valuable to know and understand how the runtime represents components logically and physically.</span></span> <span data-ttu-id="cb4f5-140">Die Szene stellt Daten mit einem bestimmten Layout dar, das als einfach ausgewählt wurde, während eine zugrunde liegende Struktur beibehalten wird, die zukünftige Anforderungen erfüllen kann, ohne dass größere Revisionen erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-140">The Scene represents data with a specific layout that was chosen to be simple while maintaining an underlying structure that is pliable to meet future requirements without needing major revisions.</span></span> <span data-ttu-id="cb4f5-141">Die Szene speichert dazu alle Komponenten (Bausteine für alle Szenenobjekte) in einer flachen Liste und definiert Hierarchie und Komposition über Verweise, in denen bestimmte Komponenten auf andere verweisen.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-141">The Scene does this by storing all Components (building blocks for all Scene Objects) in a flat list and defining hierarchy and composition through references where specific components reference others.</span></span>

<span data-ttu-id="cb4f5-142">Unten sehen Sie ein Beispiel für eine -Struktur in ihrer flachen und logischen Form.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-142">Below we present an example of a structure in both its flat and logical form.</span></span>

<table>
<tr><th><span data-ttu-id="cb4f5-143">Logisches Layout</span><span class="sxs-lookup"><span data-stu-id="cb4f5-143">Logical Layout</span></span></th><th><span data-ttu-id="cb4f5-144">Physisches Layout</span><span class="sxs-lookup"><span data-stu-id="cb4f5-144">Physical Layout</span></span></th></tr>
<tr>
<td>
<ul>
  <span data-ttu-id="cb4f5-145">Szene</span><span class="sxs-lookup"><span data-stu-id="cb4f5-145">Scene</span></span>
  <ul>
  <li><span data-ttu-id="cb4f5-146">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="cb4f5-146">SceneObject_1</span></span>
    <ul>
      <li><span data-ttu-id="cb4f5-147">SceneMesh_1</span><span class="sxs-lookup"><span data-stu-id="cb4f5-147">SceneMesh_1</span></span></li>
      <li><span data-ttu-id="cb4f5-148">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="cb4f5-148">SceneQuad_1</span></span></li>
      <li><span data-ttu-id="cb4f5-149">SceneQuad_2</span><span class="sxs-lookup"><span data-stu-id="cb4f5-149">SceneQuad_2</span></span></li>
    </ul>
  </li>
  <li><span data-ttu-id="cb4f5-150">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="cb4f5-150">SceneObject_2</span></span>
    <ul>
      <li><span data-ttu-id="cb4f5-151">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="cb4f5-151">SceneQuad_1</span></span></li>
      <li><span data-ttu-id="cb4f5-152">SceneQuad_3</span><span class="sxs-lookup"><span data-stu-id="cb4f5-152">SceneQuad_3</span></span></li>
      </li></ul>
  </li>
  <li><span data-ttu-id="cb4f5-153">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="cb4f5-153">SceneObject_3</span></span>
    <ul>
      <li><span data-ttu-id="cb4f5-154">SceneMesh_3</span><span class="sxs-lookup"><span data-stu-id="cb4f5-154">SceneMesh_3</span></span></li>
    </ul>
  </ul>
</ul>
</td>
<td>
<ul>
  <li><span data-ttu-id="cb4f5-155">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="cb4f5-155">SceneObject_1</span></span></li>
  <li><span data-ttu-id="cb4f5-156">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="cb4f5-156">SceneObject_2</span></span></li>
  <li><span data-ttu-id="cb4f5-157">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="cb4f5-157">SceneObject_3</span></span></li>
  <li><span data-ttu-id="cb4f5-158">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="cb4f5-158">SceneQuad_1</span></span></li>
  <li><span data-ttu-id="cb4f5-159">SceneQuad_2</span><span class="sxs-lookup"><span data-stu-id="cb4f5-159">SceneQuad_2</span></span></li>
  <li><span data-ttu-id="cb4f5-160">SceneQuad_3</span><span class="sxs-lookup"><span data-stu-id="cb4f5-160">SceneQuad_3</span></span></li>
  <li><span data-ttu-id="cb4f5-161">SceneMesh_1</span><span class="sxs-lookup"><span data-stu-id="cb4f5-161">SceneMesh_1</span></span></li>
  <li><span data-ttu-id="cb4f5-162">SceneMesh_2</span><span class="sxs-lookup"><span data-stu-id="cb4f5-162">SceneMesh_2</span></span></li>
</ul>
</td>
</tr>
</table>

<span data-ttu-id="cb4f5-163">Diese Abbildung veranschaulicht den Unterschied zwischen dem physischen und logischen Layout der Szene.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-163">This illustration highlights the difference between the physical and logical layout of the Scene.</span></span> <span data-ttu-id="cb4f5-164">Auf der linken Seite sehen wir das hierarchische Layout der Daten, die Ihre Anwendung beim Aufzählen der Szene sieht.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-164">On the left, we see the hierarchical layout of the data that your application sees when enumerating the scene.</span></span> <span data-ttu-id="cb4f5-165">Auf der rechten Seite sehen wir, dass die Szene aus 12 verschiedenen Komponenten besteht, auf die bei Bedarf einzeln zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-165">On the right, we see that the scene is comprised of 12 distinct components that are accessible individually if necessary.</span></span> <span data-ttu-id="cb4f5-166">Bei der Verarbeitung einer neuen Szene erwarten wir, dass Anwendungen diese Hierarchie logisch durchverteilen. Bei der Nachverfolgung zwischen Szenenupdates sind einige Anwendungen jedoch möglicherweise nur an bestimmten Komponenten interessiert, die von zwei Szenen gemeinsam genutzt werden.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-166">When processing a new scene, we expect applications to walk this hierarchy logically, however when tracking between scene updates, some applications may only be interested in targeting specific components that are shared between two scenes.</span></span>

## <a name="api-overview"></a><span data-ttu-id="cb4f5-167">API-Übersicht</span><span class="sxs-lookup"><span data-stu-id="cb4f5-167">API overview</span></span>

<span data-ttu-id="cb4f5-168">Der folgende Abschnitt bietet eine grundlegende Übersicht über die Konstrukte in Scene Understanding.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-168">The following section provides a high-level overview of the constructs in Scene Understanding.</span></span> <span data-ttu-id="cb4f5-169">In diesem Abschnitt erhalten Sie einen Überblick darüber, wie Szenen dargestellt werden und wofür die verschiedenen Komponenten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-169">Reading this section will give you an  understanding of how scenes are represented, and what the various components do/are used for.</span></span> <span data-ttu-id="cb4f5-170">Der nächste Abschnitt enthält konkrete Codebeispiele und zusätzliche Details, die in dieser Übersicht erläutert werden.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-170">The next section will provide concrete code examples and additional details that are glossed over in this overview.</span></span>

<span data-ttu-id="cb4f5-171">Alle unten beschriebenen Typen befinden sich im `Microsoft.MixedReality.SceneUnderstanding` -Namespace.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-171">All of the types described below reside in the `Microsoft.MixedReality.SceneUnderstanding` namespace.</span></span>

### <a name="scenecomponents"></a><span data-ttu-id="cb4f5-172">SceneComponents</span><span class="sxs-lookup"><span data-stu-id="cb4f5-172">SceneComponents</span></span>

<span data-ttu-id="cb4f5-173">Nachdem Sie nun das logische Layout von Szenen verstanden haben, können wir nun das Konzept von SceneComponents und deren Verwendung zum Erstellen von Hierarchien präsentieren.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-173">Now that you understand the logical layout of scenes we can now present the concept of SceneComponents and how they're used to compose hierarchy.</span></span> <span data-ttu-id="cb4f5-174">SceneComponents sind die präzisesten Zerlegungen in SceneUnderstanding, die ein einzelnes Kernstück darstellen, z. B. ein Gitternetz, ein Quad oder ein Begrenzungsfeld.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-174">SceneComponents are the most granular decompositions in SceneUnderstanding representing a single core thing, for example, a mesh or a quad or a bounding box.</span></span> <span data-ttu-id="cb4f5-175">SceneComponents sind Dinge, die unabhängig aktualisiert werden können und auf die von anderen SceneComponents verwiesen werden kann. Daher verfügen sie über eine einzelne globale Eigenschaft mit einer eindeutigen ID, die diese Art von Nachverfolgungs-/Verweismechanismus ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-175">SceneComponents are things that can update independently and can be referenced by other SceneComponents, hence they have a single global property a unique ID, that allow for this type of tracking/referencing mechanism.</span></span> <span data-ttu-id="cb4f5-176">IDs werden für die logische Zusammensetzung der Szenenhierarchie sowie für die Objektpersistenz (das Aktualisieren einer Szene relativ zu einer anderen) verwendet.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-176">Ids are used for the logical composition of scene hierarchy as well as object persistence (the act of updating one scene relative to another.)</span></span> 

<span data-ttu-id="cb4f5-177">Wenn Sie jede neu berechnete Szene als eindeutig behandeln und einfach alle Daten in ihr aufzählen, sind IDs für Sie größtenteils transparent.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-177">If you're treating every newly computed scene as being distinct, and simply enumerating all data within it then Ids are largely transparent to you.</span></span> <span data-ttu-id="cb4f5-178">Wenn Sie jedoch planen, Komponenten über mehrere Updates nachzuverfolgen, verwenden Sie die IDs, um SceneComponents zwischen Szenenobjekten zu indizieren und zu suchen.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-178">However, if you're planning to track components over several updates you'll use the Ids to index and find SceneComponents between Scene objects.</span></span>

### <a name="sceneobjects"></a><span data-ttu-id="cb4f5-179">SceneObjects</span><span class="sxs-lookup"><span data-stu-id="cb4f5-179">SceneObjects</span></span>

<span data-ttu-id="cb4f5-180">Ein SceneObject ist ein SceneComponent, das eine Instanz eines "Dings" darstellt, z. B. eine Wand, einen Boden, eine Obergrenze usw. ausgedrückt durch die Kind-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-180">A SceneObject is a SceneComponent that represents an instance of a "thing" for example, a wall, a floor, a ceiling, etc.... expressed by their Kind property.</span></span> <span data-ttu-id="cb4f5-181">SceneObjects sind geometrisch und verfügen daher über Funktionen und Eigenschaften, die ihre Position im Raum darstellen, jedoch keine geometrische oder logische Struktur enthalten.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-181">SceneObjects are geometric, and therefore have functions and properties that represent their location in space, however they don't contain any geometric or logical structure.</span></span> <span data-ttu-id="cb4f5-182">Stattdessen verweisen SceneObjects auf andere SceneComponents, insbesondere SceneQuads und SceneMeshes, die die verschiedenen Darstellungen bereitstellen, die vom System unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-182">Instead, SceneObjects reference other SceneComponents, specifically SceneQuads, and SceneMeshes, which provide the varied representations that are supported by the system.</span></span> <span data-ttu-id="cb4f5-183">Wenn eine neue Szene berechnet wird, zählt Ihre Anwendung höchstwahrscheinlich die SceneObjects der Szene auf, um das zu verarbeiten, was sie interessiert.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-183">When a new scene is computed, your application will most likely enumerate the Scene's SceneObjects to process what it's interested in.</span></span>

<span data-ttu-id="cb4f5-184">SceneObjects kann eine der folgenden Funktionen aufweisen:</span><span class="sxs-lookup"><span data-stu-id="cb4f5-184">SceneObjects can have any one of the following:</span></span>

<table>
<tr>
<th><span data-ttu-id="cb4f5-185">SceneObjectKind</span><span class="sxs-lookup"><span data-stu-id="cb4f5-185">SceneObjectKind</span></span></th> <th><span data-ttu-id="cb4f5-186">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="cb4f5-186">Description</span></span></th>
</tr>
<tr><td><span data-ttu-id="cb4f5-187">Hintergrund</span><span class="sxs-lookup"><span data-stu-id="cb4f5-187">Background</span></span></td><td><span data-ttu-id="cb4f5-188">Das SceneObject ist bekannt dafür, dass es <b>sich nicht</b> um eine der anderen erkannten Arten von Szenenobjekten handelt.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-188">The SceneObject is known to be <b>not</b> one of the other recognized kinds of scene object.</span></span> <span data-ttu-id="cb4f5-189">Diese Klasse sollte nicht mit Unknown verwechselt werden, wobei Background bekanntermaßen nicht "Wall", "Floor", "ceiling" usw. ist. während unbekannt noch nicht kategorisiert ist.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-189">This class shouldn't be confused with Unknown where Background is known not to be wall/floor/ceiling etc.... while unknown isn't yet categorized.</span></span></b></td></tr>
<tr><td><span data-ttu-id="cb4f5-190">Wall</span><span class="sxs-lookup"><span data-stu-id="cb4f5-190">Wall</span></span></td><td><span data-ttu-id="cb4f5-191">Eine physische Wand.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-191">A physical wall.</span></span> <span data-ttu-id="cb4f5-192">Es wird davon ausgegangen, dass Es sich um wähnbare Umgebungsstrukturen handelt.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-192">Walls are assumed to be immovable environmental structures.</span></span></td></tr>
<tr><td><span data-ttu-id="cb4f5-193">Etage</span><span class="sxs-lookup"><span data-stu-id="cb4f5-193">Floor</span></span></td><td><span data-ttu-id="cb4f5-194">Etagen sind alle Oberflächen, auf denen sie begehbar sind.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-194">Floors are any surfaces on which one can walk.</span></span> <span data-ttu-id="cb4f5-195">Hinweis: Dies sind keine Etagen.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-195">Note: stairs aren't floors.</span></span> <span data-ttu-id="cb4f5-196">Beachten Sie auch, dass Die Etagen eine beliebige begehbare Oberfläche annehmen und daher keine explizite Annahme einer einzelnen Etage besteht.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-196">Also note, that floors assume any walkable surface and therefore there's no explicit assumption of a singular floor.</span></span> <span data-ttu-id="cb4f5-197">Strukturen auf mehreren Ebenen, Rampen usw. sollte alle als Floor klassifiziert werden.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-197">Multi-level structures, ramps etc.... should all classify as floor.</span></span></td></tr>
<tr><td><span data-ttu-id="cb4f5-198">Ceiling</span><span class="sxs-lookup"><span data-stu-id="cb4f5-198">Ceiling</span></span></td><td><span data-ttu-id="cb4f5-199">Die obere Oberfläche eines Raumes.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-199">The upper surface of a room.</span></span></td></tr>
<tr><td><span data-ttu-id="cb4f5-200">Plattform</span><span class="sxs-lookup"><span data-stu-id="cb4f5-200">Platform</span></span></td><td><span data-ttu-id="cb4f5-201">Eine große flache Oberfläche, auf der Sie Hologramme platzieren können.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-201">A large flat surface on which you could place holograms.</span></span> <span data-ttu-id="cb4f5-202">Diese stellen in der Regel Tabellen, Arbeitsflächen und andere große horizontale Oberflächen dar.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-202">These tend to represent tables, countertops, and other large horizontal surfaces.</span></span></td></tr>
<tr><td><span data-ttu-id="cb4f5-203">World</span><span class="sxs-lookup"><span data-stu-id="cb4f5-203">World</span></span></td><td><span data-ttu-id="cb4f5-204">Eine reservierte Bezeichnung für geometrische Daten, die von der Bezeichnung unabhängig sind.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-204">A reserved label for geometric data that is agnostic to labeling.</span></span> <span data-ttu-id="cb4f5-205">Das Gitternetz, das durch Festlegen des EnableWorldMesh-Updateflags generiert wird, würde als World klassifiziert.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-205">The mesh generated by setting the EnableWorldMesh update flag would be classified as world.</span></span></td></tr>
<tr><td><span data-ttu-id="cb4f5-206">Unbekannt</span><span class="sxs-lookup"><span data-stu-id="cb4f5-206">Unknown</span></span></td><td><span data-ttu-id="cb4f5-207">Dieses Szenenobjekt muss noch klassifiziert und einer Art zugewiesen werden.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-207">This scene object has yet to be classified and assigned a kind.</span></span> <span data-ttu-id="cb4f5-208">Dies sollte nicht mit Background verwechselt werden, da dieses Objekt etwas sein könnte, das System hat einfach noch keine ausreichend starke Klassifizierung dafür erstellt.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-208">This shouldn't be confused with Background, as this object could be anything, the system has just not come up with a strong enough classification for it yet.</span></span></td></tr>
</tr>
</table>

### <a name="scenemesh"></a><span data-ttu-id="cb4f5-209">SceneMesh</span><span class="sxs-lookup"><span data-stu-id="cb4f5-209">SceneMesh</span></span>

<span data-ttu-id="cb4f5-210">Ein SceneMesh ist eine SceneComponent, die der Geometrie beliebiger geometrischer Objekte mithilfe einer Dreiecksliste ungefährt.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-210">A SceneMesh is a SceneComponent that approximates the geometry of arbitrary geometric objects using a triangle list.</span></span> <span data-ttu-id="cb4f5-211">SceneMeshes werden in verschiedenen Kontexten verwendet. Sie können Komponenten der wasserdichten Zellenstruktur oder als WorldMesh darstellen, das das Gitternetz für die räumliche Zuordnung darstellt, das der Szene zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-211">SceneMeshes are used in several different contexts, they can represent components of the watertight cell structure or as the WorldMesh, which represents the unbounded spatial mapping mesh associated with the Scene.</span></span> <span data-ttu-id="cb4f5-212">Die index- und vertex-Daten, die mit jedem Gitternetz bereitgestellt werden, verwenden das gleiche vertraute Layout wie die Scheitelpunkt- und Indexpuffer, die zum Rendern von [Dreiecksgittern](/windows/win32/direct3d9/rendering-from-vertex-and-index-buffers) in allen modernen Rendering-APIs verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-212">The index and vertex data provided with each mesh uses the same familiar layout as the [vertex and index buffers](/windows/win32/direct3d9/rendering-from-vertex-and-index-buffers) that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="cb4f5-213">In Scene Understanding verwenden Gitternetze 32-Bit-Indizes und müssen möglicherweise für bestimmte Rendering-Engines in Brüche zerlegt werden.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-213">In Scene Understanding, meshes use 32-bit indices and may need to be broken up into chunks for certain rendering engines.</span></span>

#### <a name="winding-order-and-coordinate-systems"></a><span data-ttu-id="cb4f5-214">Wickelrichtungs- und Koordinatensysteme</span><span class="sxs-lookup"><span data-stu-id="cb4f5-214">Winding Order and Coordinate Systems</span></span>

<span data-ttu-id="cb4f5-215">Von allen Gittern, die von Scene Understanding erzeugt werden, wird erwartet, dass sie Gitternetze in Right-Handed Koordinatensystem mit der Wickelrichtung im Uhrzeigersinn zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-215">All meshes produced by Scene Understanding are expected to return meshes in a Right-Handed coordinate system using clockwise winding order.</span></span> 

<span data-ttu-id="cb4f5-216">Hinweis: Betriebssystem-Builds vor .191105 weisen möglicherweise einen bekannten Fehler auf, bei dem "World"-Gitternetze in einer Counter-Clockwise-Reihenfolge zurückgelangen, die anschließend behoben wurde.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-216">Note: OS builds prior to .191105 may have a known bug where "World" meshes were returning in Counter-Clockwise winding order, which has subsequently been fixed.</span></span>

### <a name="scenequad"></a><span data-ttu-id="cb4f5-217">SceneQuad</span><span class="sxs-lookup"><span data-stu-id="cb4f5-217">SceneQuad</span></span>

<span data-ttu-id="cb4f5-218">Ein SceneQuad ist eine SceneComponent, die 2d-Oberflächen darstellt, die die 3D-Welt einnehmen.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-218">A SceneQuad is a SceneComponent that represents 2d surfaces that occupy the 3d world.</span></span> <span data-ttu-id="cb4f5-219">SceneQuads können ähnlich wie ARKit ARPlaneAnchor- oder ARCore-Ebenen verwendet werden, bieten jedoch eine erweiterte Funktionalität als 2D-Canvases, die von flachen Apps oder erweiterter UX verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-219">SceneQuads can be used similarly to ARKit ARPlaneAnchor or ARCore Planes but they offer more high-level functionality as 2d canvases to be used by flat apps, or augmented UX.</span></span> <span data-ttu-id="cb4f5-220">2D-spezifische APIs werden für Quads bereitgestellt, die die Platzierung und das Layout einfach zu verwenden machen, und die Entwicklung (mit Ausnahme des Renderings) mit Quads sollte sich eher an die Arbeit mit 2d-Canvases als an 3D-Gittern anfühlen.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-220">2D specific APIs are provided for quads that make placement and layout simple to use, and developing (with the exception of rendering) with quads should feel more akin to working with 2d canvases than 3d meshes.</span></span>

#### <a name="scenequad-shape"></a><span data-ttu-id="cb4f5-221">SceneQuad-Form</span><span class="sxs-lookup"><span data-stu-id="cb4f5-221">SceneQuad shape</span></span>

<span data-ttu-id="cb4f5-222">SceneQuads definieren eine begrenzungsbegrenzete rechteckige Oberfläche in 2d.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-222">SceneQuads define a bounded rectangular surface in 2d.</span></span> <span data-ttu-id="cb4f5-223">SceneQuads stellen jedoch Oberflächen mit beliebigen und potenziell komplexen Formen dar (z. B. eine donutförmige Tabelle). Um die komplexe Form der Oberfläche eines Quaders darzustellen, können Sie die GetSurfaceMask-API verwenden, um die Form der Oberfläche in einem von Ihnen bereitgestellten Bildpuffer zu rendern.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-223">However, SceneQuads are representing surfaces with arbitrary and potentially complex shapes (e.g. a donut shaped table.) To represent the complex shape of the surface of a quad you may use the GetSurfaceMask API to render the shape of the surface onto an image buffer you provide.</span></span> <span data-ttu-id="cb4f5-224">Wenn das SceneObject mit dem Quader ebenfalls über ein Gitternetz verfügt, sollten die Gittergitterdreiecke diesem gerenderten Bild entsprechen. Beide stellen die echte Geometrie der Oberfläche dar, entweder in 2d- oder 3d-Koordinaten.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-224">If the SceneObject that has the quad also has a mesh, the mesh triangles should be equivalent to this rendered image, they both represent real geometry of the surface, either in 2d or 3d coordinates.</span></span>

## <a name="scene-understanding-sdk-details-and-reference"></a><span data-ttu-id="cb4f5-225">Details und Referenz zum Scene Understanding SDK</span><span class="sxs-lookup"><span data-stu-id="cb4f5-225">Scene understanding SDK details and reference</span></span>

<span data-ttu-id="cb4f5-226">Der folgende Abschnitt hilft Ihnen, sich mit den Grundlagen von SceneUnderstanding vertraut zu machen.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-226">The following section will help get you familiar with the basics of SceneUnderstanding.</span></span> <span data-ttu-id="cb4f5-227">Dieser Abschnitt sollte Ihnen die Grundlagen bieten. An diesem Punkt sollten Sie über genügend Kontext verfügen, um die Beispielanwendungen zu durchsuchen, um zu sehen, wie SceneUnderstanding ganzheitlicher verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-227">This section should provide you with the basics, at which point you should have enough context to browse through the sample applications to see how SceneUnderstanding is used holistically.</span></span>

### <a name="initialization"></a><span data-ttu-id="cb4f5-228">Initialisierung</span><span class="sxs-lookup"><span data-stu-id="cb4f5-228">Initialization</span></span>

<span data-ttu-id="cb4f5-229">Der erste Schritt beim Arbeiten mit SceneUnderstanding besteht darin, dass Ihre Anwendung einen Verweis auf ein Scene-Objekt erhält.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-229">The first step to working with SceneUnderstanding is for your application to gain reference to a Scene object.</span></span> <span data-ttu-id="cb4f5-230">Dies kann auf zwei Arten erfolgen: Eine Szene kann entweder vom Treiber berechnet werden, oder eine vorhandene Szene, die in der Vergangenheit berechnet wurde, kann deserimetrisiert werden.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-230">This can be done in one of two ways, a Scene can either be computed by the driver, or an existing Scene that was computed in the past can be de-serialized.</span></span> <span data-ttu-id="cb4f5-231">Letzteres ist nützlich für die Arbeit mit SceneUnderstanding während der Entwicklung, bei der Anwendungen und Erfahrungen schnell ohne ein Mixed Reality-Gerät prototypiert werden können.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-231">The latter is useful for working with SceneUnderstanding during development, where applications and experiences can be prototyped quickly without a mixed reality device.</span></span>

<span data-ttu-id="cb4f5-232">Szenen werden mithilfe eines SceneObservers berechnet.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-232">Scenes are computed using a SceneObserver.</span></span> <span data-ttu-id="cb4f5-233">Vor dem Erstellen einer Szene sollte Ihre Anwendung Ihr Gerät abfragen, um sicherzustellen, dass es SceneUnderstanding unterstützt, sowie Benutzerzugriff für Informationen anfordern, die SceneUnderstanding benötigt.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-233">Before creating a Scene, your application should query your device to ensure that it supports SceneUnderstanding, as well as to request user access for information that SceneUnderstanding needs.</span></span>

```cs
if (!SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

<span data-ttu-id="cb4f5-234">Wenn RequestAccessAsync() nicht aufgerufen wird, schlägt das Berechnen einer neuen Szene fehl.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-234">If RequestAccessAsync() is not called, computing a new Scene will fail.</span></span> <span data-ttu-id="cb4f5-235">Als Nächstes berechnen wir eine neue Szene, die auf dem Mixed Reality Headset basiert und einen Radius von 10 Metern hat.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-235">Next we will compute a new scene that's rooted around the Mixed Reality headset and has a 10-meter radius.</span></span>

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

### <a name="initialization-from-data-also-known-as-the-pc-path"></a><span data-ttu-id="cb4f5-236">Initialisierung aus Daten (auch bekannt als .</span><span class="sxs-lookup"><span data-stu-id="cb4f5-236">Initialization from Data (also known as.</span></span> <span data-ttu-id="cb4f5-237">PC-Pfad)</span><span class="sxs-lookup"><span data-stu-id="cb4f5-237">the PC Path)</span></span>

<span data-ttu-id="cb4f5-238">Szenen können zwar für die direkte Nutzung berechnet werden, sie können aber auch zur späteren Verwendung in serialisierter Form berechnet werden.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-238">While Scenes can be computed for direct consumption, they can also be computed in serialized form for later use.</span></span> <span data-ttu-id="cb4f5-239">Dies hat sich als nützlich für die Entwicklung erwiesen, da Entwickler damit Scene Understanding ohne geräteloses Arbeiten und Testen testen können.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-239">This has proven to be useful for development as it allows developers to work in and test Scene Understanding without the need for a device.</span></span> <span data-ttu-id="cb4f5-240">Das Serialisieren einer Szene ist nahezu identisch mit der Berechnung. Die Daten werden an Ihre Anwendung zurückgegeben, anstatt lokal vom SDK deserialisiert zu werden.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-240">The act of serializing a scene is nearly identical to computing it, the data is returned to your application instead of being deserialized locally by the SDK.</span></span> <span data-ttu-id="cb4f5-241">Sie können sie dann selbst deserialisieren oder zur zukünftigen Verwendung speichern.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-241">You may then deserialize it yourself or save it for future use.</span></span>

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

### <a name="sceneobject-enumeration"></a><span data-ttu-id="cb4f5-242">SceneObject-Enumeration</span><span class="sxs-lookup"><span data-stu-id="cb4f5-242">SceneObject Enumeration</span></span>

<span data-ttu-id="cb4f5-243">Nachdem Ihre Anwendung nun über eine Szene verfügt, wird ihre Anwendung SceneObjects anzeigen und mit ihnen interagieren.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-243">Now that your application has a scene, your application will be looking at and interacting with SceneObjects.</span></span> <span data-ttu-id="cb4f5-244">Dies erfolgt durch Zugriff auf die **SceneObjects-Eigenschaft:**</span><span class="sxs-lookup"><span data-stu-id="cb4f5-244">This is done by accessing the **SceneObjects** property:</span></span>

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

### <a name="component-update-and-refinding-components"></a><span data-ttu-id="cb4f5-245">Komponentenupdate und -neufinden von Komponenten</span><span class="sxs-lookup"><span data-stu-id="cb4f5-245">Component update and refinding components</span></span>

<span data-ttu-id="cb4f5-246">Es gibt eine weitere Funktion, die Komponenten in der Szene mit dem Namen ***FindComponent abruft.***</span><span class="sxs-lookup"><span data-stu-id="cb4f5-246">There's another function that retrieves components in the Scene called ***FindComponent***.</span></span> <span data-ttu-id="cb4f5-247">Diese Funktion ist nützlich, wenn Sie Nachverfolgungsobjekte aktualisieren und später finden.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-247">This function is useful when updating tracking objects and finding them in later scenes.</span></span> <span data-ttu-id="cb4f5-248">Der folgende Code berechnet eine neue Szene relativ zu einer vorherigen Szene und findet dann den Boden in der neuen Szene.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-248">The following code will compute a new scene relative to a previous scene and then find the floor in the new scene.</span></span>

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

## <a name="accessing-meshes-and-quads-from-scene-objects"></a><span data-ttu-id="cb4f5-249">Zugreifen auf Gitter und Quader von Szenenobjekten</span><span class="sxs-lookup"><span data-stu-id="cb4f5-249">Accessing Meshes and Quads from Scene Objects</span></span>

<span data-ttu-id="cb4f5-250">Sobald SceneObjects gefunden wurde, möchte Ihre Anwendung höchstwahrscheinlich auf die Daten zugreifen, die in den Quads/Meshes enthalten sind, aus denen sie besteht.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-250">Once SceneObjects have been found your application will most likely want to access the data that is contained in the quads/meshes that it is composed of.</span></span> <span data-ttu-id="cb4f5-251">Auf diese Daten wird mit den Eigenschaften ***Quads** _ und _ *_Meshes_** zugegriffen.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-251">This data is accessed with the ***Quads** _ and _ *_Meshes_** properties.</span></span> <span data-ttu-id="cb4f5-252">Im folgenden Code werden alle Quads und Gitter des Bodenobjekts aufzählt.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-252">The following code will enumerate all quads and meshes of our floor object.</span></span>

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

<span data-ttu-id="cb4f5-253">Beachten Sie, dass es das SceneObject ist, das über die Transformation verfügt, die relativ zum Ursprung der Szene ist.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-253">Notice that it's the SceneObject that has the transform that is relative to the Scene origin.</span></span> <span data-ttu-id="cb4f5-254">Dies liegt daran, dass das SceneObject eine Instanz eines "Objekts" darstellt und im Raum verwendbar ist, die Quads und Gitternetze die Geometrie darstellen, die relativ zu ihrem übergeordneten Element transformiert wird.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-254">This is because the SceneObject represents an instance of a "thing" and is locatable in space, the quads, and meshes represent geometry that is transformed relative to their parent.</span></span> <span data-ttu-id="cb4f5-255">Es ist möglich, dass separate SceneObjects auf die gleichen SceneMesh/SceneQuad SceneComponents verweisen, und es ist auch möglich, dass ein SceneObject über mehr als ein SceneMesh/SceneQuad verfügt.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-255">It's possible for separate SceneObjects to reference the same SceneMesh/SceneQuad SceneComponents, and it's also possible that a SceneObject has more than one SceneMesh/SceneQuad.</span></span>

### <a name="dealing-with-transforms"></a><span data-ttu-id="cb4f5-256">Umgang mit Transformationen</span><span class="sxs-lookup"><span data-stu-id="cb4f5-256">Dealing with Transforms</span></span>

<span data-ttu-id="cb4f5-257">Scene Understanding hat beim Umgang mit Transformationen bewusst versucht, sich an herkömmlichen 3D-Szenendarstellungen auszurichten.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-257">Scene Understanding has made a deliberate attempt to align with traditional 3D scene representations when dealing with transforms.</span></span> <span data-ttu-id="cb4f5-258">Jede Szene ist daher ähnlich wie die gängigsten 3D-Umgebungsdarstellungen auf ein einzelnes Koordinatensystem beschränkt.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-258">Each Scene is therefore confined to a single coordinate system much like most common 3D environmental representations.</span></span> <span data-ttu-id="cb4f5-259">SceneObjects stellen jeweils ihre Position relativ zu diesem Koordinatensystem zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-259">SceneObjects each provide their location relative to that coordinate system.</span></span> <span data-ttu-id="cb4f5-260">Wenn Ihre Anwendung mit Szenen zu tun hat, die die Grenze des von einem einzelnen Ursprung bereitgestellten Objekts ausdehnen, kann sie SceneObjects in SpatialAnchors verankern oder mehrere Szenen generieren und zusammenführen. Der Einfachheit halber gehen wir jedoch davon aus, dass sich wässrige Szenen in ihrem eigenen Ursprung befinden, der durch eine NodeId lokalisiert ist, die durch Scene.OriginSpatialGraphNodeId definiert wird.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-260">If your application is dealing with Scenes that stretch the limit of what a single origin provides it can anchor SceneObjects to SpatialAnchors, or generate several scenes and merge them together, but for simplicity we assume that watertight scenes exist in their own origin that's localized by one NodeId defined by Scene.OriginSpatialGraphNodeId.</span></span>

<span data-ttu-id="cb4f5-261">Der folgende Unity-Code zeigt beispielsweise, wie Sie Windows Perception- und Unity-APIs verwenden, um Koordinatensysteme zusammen auszurichten.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-261">The following Unity code, for example, shows how to use Windows Perception and Unity APIs to align coordinate systems together.</span></span> <span data-ttu-id="cb4f5-262">Ausführliche Informationen zu den Windows Perception-APIs finden Sie unter [SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) und [SpatialGraphInteropPreview](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) und [Mixed Reality nativen Objekte in Unity,](/windows/mixed-reality/unity-xrdevice-advanced) um Details zum Abrufen eines SpatialCoordinateSystem zu erhalten, das dem Ursprung von Unity entspricht.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-262">See [SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) and [SpatialGraphInteropPreview](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) for details on the Windows Perception APIs, and [Mixed Reality native objects in Unity](/windows/mixed-reality/unity-xrdevice-advanced) for details on obtaining a SpatialCoordinateSystem that corresponds to Unity's world origin.</span></span>

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

<span data-ttu-id="cb4f5-263">Jede `SceneObject` verfügt über eine Transformation, die dann auf dieses Objekt angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-263">Each `SceneObject` has a transform, which is then applied to that object.</span></span> <span data-ttu-id="cb4f5-264">In Unity konvertieren wir in rechtshändige Koordinaten und weisen lokale Transformationen zu:</span><span class="sxs-lookup"><span data-stu-id="cb4f5-264">In Unity we convert to right handed coordinates and assign local transforms as so:</span></span>

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

### <a name="quad"></a><span data-ttu-id="cb4f5-265">Viereck</span><span class="sxs-lookup"><span data-stu-id="cb4f5-265">Quad</span></span>

<span data-ttu-id="cb4f5-266">Quads wurden entwickelt, um 2D-Platzierungsszenarien zu unterstützen, und sollten als Erweiterungen für 2D-Canvas-UX-Elemente gedacht werden.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-266">Quads were designed to help 2D placement scenarios and should be thought of as extensions to 2D canvas UX elements.</span></span> <span data-ttu-id="cb4f5-267">Während Quads Komponenten von SceneObjects sind und in 3D gerendert werden können, gehen die Quad-APIs selbst davon aus, dass Quads 2D-Strukturen sind.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-267">While Quads are components of SceneObjects and can be rendered in 3D, the Quad APIs themselves assume Quads are 2D structures.</span></span> <span data-ttu-id="cb4f5-268">Sie bieten Informationen wie "extent", "shape" und "provide APIs for placement".</span><span class="sxs-lookup"><span data-stu-id="cb4f5-268">They offer information such as extent, shape, and provide APIs for placement.</span></span>

<span data-ttu-id="cb4f5-269">Quader verfügen über rechteckige Kästchen, stellen aber beliebig formatierte 2D-Oberflächen dar.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-269">Quads have rectangular extents, but they represent arbitrarily shaped 2D surfaces.</span></span> <span data-ttu-id="cb4f5-270">Um die Platzierung auf diesen 2D-Oberflächen zu ermöglichen, die mit den 3D-Umgebungsquads interagieren, bieten Quads Hilfsprogramme, um diese Interaktion zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-270">To enable placement on these 2D surfaces that interact with the 3D environment quads offer utilities to make this interaction possible.</span></span> <span data-ttu-id="cb4f5-271">Scene Understanding bietet derzeit zwei solche Funktionen: **FindCentermostPlacement** und **GetSurfaceMask.**</span><span class="sxs-lookup"><span data-stu-id="cb4f5-271">Currently Scene Understanding provides two such functions, **FindCentermostPlacement** and **GetSurfaceMask**.</span></span> <span data-ttu-id="cb4f5-272">FindCentermostPlacement ist eine high-level-API, die eine Position auf dem Quader sucht, an der ein Objekt platziert werden kann, und versucht, den besten Speicherort für Ihr Objekt zu finden, wodurch sichergestellt wird, dass der von Ihnen bereitgestellte Begrenzungsfeld auf der zugrunde liegenden Oberfläche verbleibt.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-272">FindCentermostPlacement is a high-level API that locates a position on the quad where an object can be placed and will try to find the best location for your object guaranteeing that the bounding box you provide will stay on the underlying surface.</span></span>

> [!NOTE]
> <span data-ttu-id="cb4f5-273">Die Koordinaten der Ausgabe sind relativ zum Quader im "Quad space", wobei die linke obere Ecke (x = 0, y = 0) ist, genau wie bei anderen Rect-Typen von Fenstern.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-273">The coordinates of the output are relative to the quad in "quad space" with the top left corner being (x = 0, y = 0), just as it would be with other windows Rect types.</span></span> <span data-ttu-id="cb4f5-274">Berücksichtigen Sie dies unbedingt, wenn Sie mit den Ursprüngen Ihrer eigenen Objekte arbeiten.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-274">Be sure to take this into account when working with the origins of your own objects.</span></span> 

<span data-ttu-id="cb4f5-275">Das folgende Beispiel zeigt, wie Sie die zentriertste positionierbare Position finden und ein Hologramm am Quader verankern.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-275">The following example shows how to find the centermost placeable location and anchor a hologram to the quad.</span></span>

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

<span data-ttu-id="cb4f5-276">Die Schritte 1 bis 4 hängen stark von Ihrem jeweiligen Framework bzw. Ihrer Implementierung ab, die Designs sollten jedoch ähnlich sein.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-276">Steps 1-4 are highly dependent on your particular framework/implementation, but the themes should be similar.</span></span> <span data-ttu-id="cb4f5-277">Es ist wichtig zu beachten, dass das Quad einfach eine 2D-Begrenzungsebene darstellt, die im Raum lokalisiert ist.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-277">It's important to note that the Quad simply represents a bounded 2D plane that is localized in space.</span></span> <span data-ttu-id="cb4f5-278">Wenn Ihre Engine/Ihr Framework weiß, wo sich das Quad befindet, und Ihre Objekte relativ zum Quader rooten, werden Ihre Hologramme im Hinblick auf die reale Welt korrekt gefunden.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-278">By having your engine/framework know where the quad is and rooting your objects relative to the quad, your holograms will be located correctly with respect to the real world.</span></span> 

<!-- 
// TODO: Add sample link when released
For more detailed information please see our samples on quads which show specific implementations.
-->

### <a name="mesh"></a><span data-ttu-id="cb4f5-279">Mesh</span><span class="sxs-lookup"><span data-stu-id="cb4f5-279">Mesh</span></span>

<span data-ttu-id="cb4f5-280">Gitternetze stellen geometrische Darstellungen von Objekten oder Umgebungen dar.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-280">Meshes represent geometric representations of objects or environments.</span></span> <span data-ttu-id="cb4f5-281">Ähnlich [wie](../../design/spatial-mapping.md)bei der räumlichen Zuordnung verwenden Gitternetzindex- und Vertexdaten, die mit jedem Gitternetz für räumliche Oberflächen bereitgestellt werden, das gleiche vertraute Layout wie die Scheitelpunkt- und Indexpuffer, die zum Rendern von Dreiecksgittern in allen modernen Rendering-APIs verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-281">Much like [spatial mapping](../../design/spatial-mapping.md), mesh index and vertex data provided with each spatial surface mesh uses the same familiar layout as the vertex and index buffers that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="cb4f5-282">Scheitelpunktpositionen werden im Koordinatensystem von `Scene` bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-282">Vertex positions are provided in the coordinate system of the `Scene`.</span></span> <span data-ttu-id="cb4f5-283">Die spezifischen APIs, die verwendet werden, um auf diese Daten zu verweisen, lauten wie folgt:</span><span class="sxs-lookup"><span data-stu-id="cb4f5-283">The specific APIs used to reference this data are as follows:</span></span>

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(System.Numerics.Vector3[] vertices);
```

<span data-ttu-id="cb4f5-284">Der folgende Code enthält ein Beispiel für das Generieren einer Dreiecksliste aus der Gitternetzstruktur:</span><span class="sxs-lookup"><span data-stu-id="cb4f5-284">The following code provides an example of generating a triangle list from the mesh structure:</span></span>

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
System.Numerics.Vector3[] positions = new System.Numerics.Vector3[mesh.VertexCount];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

<span data-ttu-id="cb4f5-285">Die Index-/Scheitelpunktpuffer müssen >= Index-/Scheitelpunktanzahl angegeben werden, können aber andernfalls beliebig dimensioniert werden, um eine effiziente Speicherwiederverwendung zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-285">The index/vertex buffers must be >= the index/vertex counts, but otherwise can be arbitrarily sized allowing for efficient memory reuse.</span></span>

### <a name="collidermesh"></a><span data-ttu-id="cb4f5-286">ColliderMesh</span><span class="sxs-lookup"><span data-stu-id="cb4f5-286">ColliderMesh</span></span>

<span data-ttu-id="cb4f5-287">Szenenobjekte ermöglichen den Zugriff auf Gitter- und Collidermeshdaten über die Eigenschaften Meshes und ColliderMeshes.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-287">Scene objects provide access to mesh and collider mesh data via the Meshes and ColliderMeshes properties.</span></span> <span data-ttu-id="cb4f5-288">Diese Gitternetze werden immer übereinstimmen, was bedeutet, dass der i'th-Index der Meshes-Eigenschaft die gleiche Geometrie wie der i'th-Index der ColliderMeshes-Eigenschaft darstellt.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-288">These meshes will always match, meaning that the i'th index of the Meshes property represents the same geometry as the i'th index of the ColliderMeshes property.</span></span> <span data-ttu-id="cb4f5-289">Wenn die Laufzeit bzw. das Objekt Collidergitter unterstützt, erhalten Sie garantiert das niedrigste Polygon und die höchste Näherung, und es ist eine bewährte Methode, ColliderMeshes überall dort zu verwenden, wo Ihre Anwendung Collider verwenden würde.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-289">If the runtime/object supports collider meshes, you are guaranteed to get the lowest polygon, highest order approximation and it's good practice to use ColliderMeshes wherever your application would use colliders.</span></span> <span data-ttu-id="cb4f5-290">Wenn das System keine Collider unterstützt, ist das in ColliderMeshes zurückgegebene Mesh-Objekt dasselbe Objekt wie das Netz, das Arbeitsspeichereinschränkungen reduziert.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-290">If the system does not support colliders the Mesh object returned in ColliderMeshes will be the same object as the mesh reducing memory constraints.</span></span>

## <a name="developing-with-scene-understanding"></a><span data-ttu-id="cb4f5-291">Entwickeln mit Szenenverständnis</span><span class="sxs-lookup"><span data-stu-id="cb4f5-291">Developing with scene understanding</span></span>

<span data-ttu-id="cb4f5-292">An diesem Punkt sollten Sie die grundlegenden Bausteine der Szene verstehen, die Laufzeit und SDK verstehen.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-292">At this point, you should understand the core building blocks of the scene understanding runtime and SDK.</span></span> <span data-ttu-id="cb4f5-293">Der Großteil der Leistungsfähigkeit und Komplexität liegt in Zugriffsmustern, der Interaktion mit 3D-Frameworks und Tools, die auf diesen APIs geschrieben werden können, um komplexere Aufgaben wie räumliche Planung, Raumanalyse, Navigation, Physik usw. auszuführen.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-293">The bulk of the power and complexity lies in access patterns, interaction with 3D frameworks, and tools that can be written on top of these APIs to do more advanced tasks like spatial planning, room analysis, navigation, physics, and so on.</span></span> <span data-ttu-id="cb4f5-294">Wir hoffen, diese in Beispielen erfassen zu können, die Sie hoffentlich in die richtige Richtung führen sollten, um Ihre Szenarien zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-294">We hope to capture these in samples that should hopefully guide you in the proper direction to make your scenarios shine.</span></span> <span data-ttu-id="cb4f5-295">Wenn es Beispiele oder Szenarien gibt, die wir nicht behandeln, teilen Sie uns dies mit, und wir versuchen, die benötigten Informationen zu dokumentieren bzw. einen Prototyp zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-295">If there are samples or scenarios we aren't addressing, let us know and we'll try to document/prototype what you need.</span></span>

### <a name="where-can-i-get-sample-code"></a><span data-ttu-id="cb4f5-296">Wo erhalte ich Beispielcode?</span><span class="sxs-lookup"><span data-stu-id="cb4f5-296">Where can I get sample code?</span></span>

<span data-ttu-id="cb4f5-297">Scene Understanding-Beispielcode für Unity finden Sie auf unserer [Unity-Beispielseite.](https://github.com/sceneunderstanding-microsoft/unitysample)</span><span class="sxs-lookup"><span data-stu-id="cb4f5-297">Scene Understanding sample code for Unity can be found on our [Unity Sample Page](https://github.com/sceneunderstanding-microsoft/unitysample) page.</span></span> <span data-ttu-id="cb4f5-298">Mit dieser Anwendung können Sie mit Ihrem Gerät kommunizieren und die verschiedenen Szenenobjekte rendern, oder Sie können eine serialisierte Szene auf Ihrem PC laden und Scene Understanding ohne Gerät erleben.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-298">This application will allow you to communicate with your device and render the various scene objects, or, it will allow you to load a serialized scene on your PC and allow you to experience Scene Understanding without a device.</span></span>

### <a name="where-can-i-get-sample-scenes"></a><span data-ttu-id="cb4f5-299">Wo erhalte ich Beispielszenen?</span><span class="sxs-lookup"><span data-stu-id="cb4f5-299">Where can I get sample scenes?</span></span>

<span data-ttu-id="cb4f5-300">Wenn Sie über eine HoloLens2 verfügen, können Sie jede erfasste Szene speichern, indem Sie die Ausgabe von ComputeSerializedAsync in einer Datei speichern und sie nach Belieben deserialisieren.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-300">If you have a HoloLens2, you can save any scene you've captured by saving the output of ComputeSerializedAsync to file and deserializing it at your own convenience.</span></span> 

<span data-ttu-id="cb4f5-301">Wenn Sie kein HoloLens2-Gerät haben, aber mit Scene Understanding spielen möchten, müssen Sie eine vorab erfasste Szene herunterladen.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-301">If you don't have a HoloLens2 device but want to play with Scene Understanding, you'll need to download a pre-captured scene.</span></span> <span data-ttu-id="cb4f5-302">Das Scene Understanding-Beispiel enthält derzeit serialisierte Szenen, die heruntergeladen und nach Belieben verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="cb4f5-302">The Scene Understanding sample currently ships with serialized scenes that can be downloaded and used at your own convenience.</span></span> <span data-ttu-id="cb4f5-303">Sie finden sie hier:</span><span class="sxs-lookup"><span data-stu-id="cb4f5-303">You can find them here:</span></span>

[<span data-ttu-id="cb4f5-304">Scene Understanding-Beispielszenen</span><span class="sxs-lookup"><span data-stu-id="cb4f5-304">Scene Understanding Sample Scenes</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

## <a name="see-also"></a><span data-ttu-id="cb4f5-305">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="cb4f5-305">See also</span></span>

* [<span data-ttu-id="cb4f5-306">Räumliche Abbildung</span><span class="sxs-lookup"><span data-stu-id="cb4f5-306">Spatial mapping</span></span>](../../design/spatial-mapping.md)
* [<span data-ttu-id="cb4f5-307">Grundlegendes zu Szenen</span><span class="sxs-lookup"><span data-stu-id="cb4f5-307">Scene understanding</span></span>](../../design/scene-understanding.md)
* [<span data-ttu-id="cb4f5-308">Unity-Beispiel</span><span class="sxs-lookup"><span data-stu-id="cb4f5-308">Unity Sample</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)