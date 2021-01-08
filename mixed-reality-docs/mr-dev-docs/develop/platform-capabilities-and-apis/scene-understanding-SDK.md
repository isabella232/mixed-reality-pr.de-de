---
title: Scene Understanding SDK
description: Erfahren Sie, wie Sie das Scene Understanding SDK, einschließlich Komponenten, Meshes und Objekten, in Mixed Reality-apps installieren und verwenden.
author: szymons
ms.author: szymons
ms.date: 12/14/2020
ms.topic: article
keywords: Szenen Verständnis, räumliche Zuordnung, Windows Mixed Reality, Unity
ms.openlocfilehash: 9520ad604125705c60624254b097de5fc93021ec
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009380"
---
# <a name="scene-understanding-sdk-overview"></a><span data-ttu-id="89a16-104">Übersicht über das Szene Verständnis von SDK</span><span class="sxs-lookup"><span data-stu-id="89a16-104">Scene understanding SDK overview</span></span>

<span data-ttu-id="89a16-105">Mit dem Einblick in die Szene werden die unstrukturierten Umgebungs Sensordaten transformiert, die ihr gemischtes Reality-Gerät erfasst und in eine leistungsstarke abstrakte Darstellung konvertiert.</span><span class="sxs-lookup"><span data-stu-id="89a16-105">Scene understanding transforms the unstructured environment sensor data that your Mixed Reality device captures and converts it into a powerful abstract representation.</span></span> <span data-ttu-id="89a16-106">Das SDK fungiert als Kommunikationsschicht zwischen Ihrer Anwendung und der Szene zur Laufzeit.</span><span class="sxs-lookup"><span data-stu-id="89a16-106">The SDK acts as the communication layer between your application and the Scene Understanding runtime.</span></span> <span data-ttu-id="89a16-107">Sie ist darauf ausgerichtet, vorhandene standardkonstrukte wie 3D-Szenen Diagramme für 3D-Darstellungen und 2D-Rechtecke und Panels für 2D-Anwendungen zu imitieren.</span><span class="sxs-lookup"><span data-stu-id="89a16-107">It's aimed to mimic existing standard constructs, such as 3D scene graphs for 3D representations, and 2D rectangles and panels for 2D applications.</span></span> <span data-ttu-id="89a16-108">Die Konstrukte der Konstrukte sind zwar mit konkreten Frameworks vertraut, aber im Allgemeinen ist das Framework agnostisch eine Interoperabilität zwischen verschiedenen Frameworks, die mit ihr interagieren.</span><span class="sxs-lookup"><span data-stu-id="89a16-108">While the constructs Scene Understanding mimics will map to concrete frameworks, in general SceneUnderstanding is framework agnostic allowing for interoperability between varied frameworks that interact with it.</span></span> <span data-ttu-id="89a16-109">Wenn das Verständnis von Szenen weiterentwickelt wird, besteht die Rolle des SDK darin, dass neue Darstellungen und Funktionen weiterhin in einem vereinheitlichten Framework verfügbar gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="89a16-109">As Scene Understanding evolves the role of the SDK is to ensure new representations and capabilities continue to be exposed within a unified framework.</span></span> <span data-ttu-id="89a16-110">In diesem Dokument werden zunächst allgemeine Konzepte vorgestellt, die Ihnen helfen, sich mit der Entwicklungsumgebung und-Nutzung vertraut zu machen und dann eine ausführlichere Dokumentation für bestimmte Klassen und Konstrukte bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="89a16-110">In this document, we will first introduce high-level concepts that will help you get familiar with the development environment/usage and then provide more detailed documentation for specific classes and constructs.</span></span>

## <a name="where-do-i-get-the-sdk"></a><span data-ttu-id="89a16-111">Wo erhalte ich das SDK?</span><span class="sxs-lookup"><span data-stu-id="89a16-111">Where do I get the SDK?</span></span>

<span data-ttu-id="89a16-112">Das sceneunderstanding SDK kann über nuget heruntergeladen werden.</span><span class="sxs-lookup"><span data-stu-id="89a16-112">The SceneUnderstanding SDK is downloadable via NuGet.</span></span>

[<span data-ttu-id="89a16-113">Sceneunderstanding-SDK</span><span class="sxs-lookup"><span data-stu-id="89a16-113">SceneUnderstanding SDK</span></span>](https://www.nuget.org/packages/Microsoft.MixedReality.SceneUnderstanding/)

<span data-ttu-id="89a16-114">**Hinweis:** die neueste Version hängt von den Vorschau Paketen ab, und Sie müssen die Vorabversion von Paketen aktivieren, um Sie anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="89a16-114">**Note:** the latest release depends on preview packages and you'll need to enable pre-release packages to see it.</span></span>

<span data-ttu-id="89a16-115">Bei Version 0.5.2022-RC und höher unterstützt Szenen Verständnis sprach Projektionen für c# und C++, mit denen Anwendungen Anwendungen für Win32-oder UWP-Plattformen entwickeln können.</span><span class="sxs-lookup"><span data-stu-id="89a16-115">For version 0.5.2022-rc and later, Scene Understanding supports language projections for C# and C++ allowing applications to develop applications for Win32 or UWP platforms.</span></span> <span data-ttu-id="89a16-116">Ab dieser Version unterstützt sceneunderstanding die Unterstützung von Unity im Editor, die den sceneobserver verwendet, der ausschließlich für die Kommunikation mit HoloLens2 verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="89a16-116">As of this version, SceneUnderstanding supports unity in-editor support barring the SceneObserver, which is used solely for communicating with HoloLens2.</span></span> 

<span data-ttu-id="89a16-117">Sceneunderstanding erfordert Windows SDK-Version 18362 oder höher.</span><span class="sxs-lookup"><span data-stu-id="89a16-117">SceneUnderstanding requires Windows SDK version 18362 or higher.</span></span> 

<span data-ttu-id="89a16-118">Wenn Sie das SDK in einem Unity-Projekt verwenden, verwenden Sie [nuget für Unity](https://github.com/GlitchEnzo/NuGetForUnity) , um das Paket in Ihrem Projekt zu installieren.</span><span class="sxs-lookup"><span data-stu-id="89a16-118">If you're using the SDK in a Unity project, use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity) to install the package into your project.</span></span>

## <a name="conceptual-overview"></a><span data-ttu-id="89a16-119">Konzeptionelle Übersicht</span><span class="sxs-lookup"><span data-stu-id="89a16-119">Conceptual Overview</span></span>

### <a name="the-scene"></a><span data-ttu-id="89a16-120">Die Szene</span><span class="sxs-lookup"><span data-stu-id="89a16-120">The Scene</span></span>

<span data-ttu-id="89a16-121">Ihr gemischtes Reality-Gerät integriert ständig Informationen zu den in Ihrer Umgebung angezeigten Informationen.</span><span class="sxs-lookup"><span data-stu-id="89a16-121">Your mixed reality device is constantly integrating information about what it sees in your environment.</span></span> <span data-ttu-id="89a16-122">In der Szene werden alle diese Datenquellen verstanden und eine einzelne, zusammenhängende Abstraktion erzeugt.</span><span class="sxs-lookup"><span data-stu-id="89a16-122">Scene Understanding funnels all of these data sources and produces one single cohesive abstraction.</span></span> <span data-ttu-id="89a16-123">Szenen Verständnis generiert Szenen, bei denen es sich um eine Komposition von [sceneobjects](scene-understanding-SDK.md#sceneobjects) handelt, die eine Instanz eines einzelnen Objekts darstellen (z. b. eine Wand/Ceiling/Floor). Szenen Objekte selbst sind eine Komposition von [scenecomponents, die präziseste Teile darstellen, die dieses sceneobject bilden.</span><span class="sxs-lookup"><span data-stu-id="89a16-123">Scene Understanding generates Scenes, which are a composition of [SceneObjects](scene-understanding-SDK.md#sceneobjects) that represent an instance of a single thing, (for example, a wall/ceiling/floor.) Scene Objects themselves are a composition of [SceneComponents, which represent more granular pieces that make up this SceneObject.</span></span> <span data-ttu-id="89a16-124">Beispiele für Komponenten sind Quads und Meshes, aber in der Zukunft könnten Begrenzungs Felder, Kollisions Netze, Metadaten usw. darstellen.</span><span class="sxs-lookup"><span data-stu-id="89a16-124">Examples of components are quads and meshes, but in the future could represent bounding boxes, collision meshes, metadata etc.</span></span>

<span data-ttu-id="89a16-125">Der Prozess der Umstellung der Rohdaten des Sensors in eine Szene ist ein potenziell kostspieliger Vorgang, bei dem mittlere Leerräume (~ 10X 10m) für große Leerzeichen (~ 50X 50 Mio.) auf Minuten und somit nicht vom Gerät ohne Anwendungsanforderung berechnet werden.</span><span class="sxs-lookup"><span data-stu-id="89a16-125">The process of converting the raw sensor data into a Scene is a potentially expensive operation that could take seconds for medium spaces (~10x10m) to minutes for large spaces (~50x50m) and therefore it is not something that is being computed by the device without application request.</span></span> <span data-ttu-id="89a16-126">Stattdessen wird die Szenen Generierung von Ihrer Anwendung Bedarfs gesteuert ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="89a16-126">Instead, Scene generation is triggered by your application on demand.</span></span> <span data-ttu-id="89a16-127">Die sceneobserver-Klasse verfügt über statische Methoden, die eine Szene berechnen oder deserialisieren können, die Sie dann auflisten/mit der Sie interagieren können.</span><span class="sxs-lookup"><span data-stu-id="89a16-127">The SceneObserver class has static methods that can Compute or Deserialize a scene, which you can then enumerate/interact with.</span></span> <span data-ttu-id="89a16-128">Die "Compute"-Aktion wird Bedarfs gesteuert ausgeführt und wird auf der CPU ausgeführt, aber in einem separaten Prozess (dem Mixed Reality-Treiber).</span><span class="sxs-lookup"><span data-stu-id="89a16-128">The "Compute" action is executed on-demand and executes on the CPU but in a separate process (the Mixed Reality Driver).</span></span> <span data-ttu-id="89a16-129">Während wir in einem anderen Prozess berechnen, werden die resultierenden Szenen Daten jedoch in der Anwendung im Scene-Objekt gespeichert und verwaltet.</span><span class="sxs-lookup"><span data-stu-id="89a16-129">However, while we do compute in another process the resulting Scene data is stored and maintained in your application in the Scene object.</span></span> 

<span data-ttu-id="89a16-130">Das folgende Diagramm veranschaulicht den Prozessfluss und zeigt Beispiele für zwei Anwendungen an, die mit der Laufzeitumgebung vertraut sind.</span><span class="sxs-lookup"><span data-stu-id="89a16-130">Below is a diagram that illustrates this process flow and shows examples of two applications interfacing with the Scene Understanding runtime.</span></span> 

![Prozessdiagramm](images/SU-ProcessFlow.png)

<span data-ttu-id="89a16-132">Auf der linken Seite befindet sich ein Diagramm der Mixed Reality-Laufzeit, die immer eingeschaltet ist und in einem eigenen Prozess ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="89a16-132">On the left-hand side is a diagram of the mixed reality runtime, which is always on and running in its own process.</span></span> <span data-ttu-id="89a16-133">Diese Laufzeit ist für die Durchführung von Geräte Nachverfolgung, räumlicher Zuordnung und anderen Vorgängen zuständig, die von der Szene verstanden werden, um die Welt zu verstehen und zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="89a16-133">This runtime is responsible for performing device tracking, spatial mapping, and other operations that Scene Understanding uses to understand and reason about the world around you.</span></span> <span data-ttu-id="89a16-134">Auf der rechten Seite des Diagramms zeigen wir zwei theoretische Anwendungen, die das Verständnis von Szenen nutzen.</span><span class="sxs-lookup"><span data-stu-id="89a16-134">On the right side of the diagram, we show two theoretical applications that make use of Scene Understanding.</span></span> <span data-ttu-id="89a16-135">Die erste Anwendung stellt mit mrtk eine Schnittstelle dar, die intern das Scene Understanding SDK verwendet, die zweite App berechnet und verwendet zwei separate Szenen Instanzen.</span><span class="sxs-lookup"><span data-stu-id="89a16-135">The first application interfaces with MRTK, which uses the Scene Understanding SDK internally, the second app computes and uses two separate scene instances.</span></span> <span data-ttu-id="89a16-136">In allen drei Szenen in diesem Diagramm werden unterschiedliche Instanzen der Kulissen generiert. der Treiber verfolgt keinen globalen Status, der von Anwendungen gemeinsam genutzt wird, und Szenen Objekte in einer Szene werden nicht in einer anderen Szene gefunden.</span><span class="sxs-lookup"><span data-stu-id="89a16-136">All three Scenes in this diagram generate distinct instances of the scenes, the driver isn't tracking global state that is shared between applications and Scene Objects in one scene aren't found in another.</span></span> <span data-ttu-id="89a16-137">Der Einblick in die Szene bietet einen Mechanismus, mit dem Sie die Zeit nachverfolgen können, dies erfolgt jedoch mit dem SDK.</span><span class="sxs-lookup"><span data-stu-id="89a16-137">Scene Understanding does provide a mechanism to track over time, but this is done using the SDK.</span></span> <span data-ttu-id="89a16-138">Der Überwachungs Code wird im SDK bereits im Prozess der app ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="89a16-138">Tracking code is already running in the SDK in your app's process.</span></span>

<span data-ttu-id="89a16-139">Da jede Szene Ihre Daten im Speicherbereich Ihrer Anwendung speichert, können Sie davon ausgehen, dass alle Funktionen des Szene Objekts oder der internen Daten immer im Prozess ihrer Anwendung ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="89a16-139">Because each Scene stores it's data in your application's memory space, you can assume that all function of the Scene object or it's internal data is always executed in your application's process.</span></span>

### <a name="layout"></a><span data-ttu-id="89a16-140">Layout</span><span class="sxs-lookup"><span data-stu-id="89a16-140">Layout</span></span>

<span data-ttu-id="89a16-141">Um mit der Darstellung von Szenen zu arbeiten, kann es hilfreich sein zu wissen und zu verstehen, wie die Laufzeit Komponenten logisch und physisch darstellt.</span><span class="sxs-lookup"><span data-stu-id="89a16-141">To work with Scene Understanding, it may be valuable to know and understand how the runtime represents components logically and physically.</span></span> <span data-ttu-id="89a16-142">Die Szene stellt Daten mit einem bestimmten Layout dar, das als einfach gewählt wurde, während eine zugrunde liegende Struktur beibehalten wird, die für zukünftige Anforderungen geeignet ist, ohne dass größere Revisionen erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="89a16-142">The Scene represents data with a specific layout that was chosen to be simple while maintaining an underlying structure that is pliable to meet future requirements without needing major revisions.</span></span> <span data-ttu-id="89a16-143">In der Szene werden alle Komponenten (Bausteine für alle Szene Objekte) in einer flachen Liste gespeichert, und die Hierarchie und Komposition werden durch Verweise definiert, bei denen bestimmte Komponenten auf andere verweisen.</span><span class="sxs-lookup"><span data-stu-id="89a16-143">The Scene does this by storing all Components (building blocks for all Scene Objects) in a flat list and defining hierarchy and composition through references where specific components reference others.</span></span>

<span data-ttu-id="89a16-144">Im folgenden finden Sie ein Beispiel für eine Struktur in der flachen und logischen Form.</span><span class="sxs-lookup"><span data-stu-id="89a16-144">Below we present an example of a structure in both its flat and logical form.</span></span>

<table>
<tr><th><span data-ttu-id="89a16-145">Logisches Layout</span><span class="sxs-lookup"><span data-stu-id="89a16-145">Logical Layout</span></span></th><th><span data-ttu-id="89a16-146">Physisches Layout</span><span class="sxs-lookup"><span data-stu-id="89a16-146">Physical Layout</span></span></th></tr>
<tr>
<td>
<ul>
  <span data-ttu-id="89a16-147">Szene</span><span class="sxs-lookup"><span data-stu-id="89a16-147">Scene</span></span>
  <ul>
  <li><span data-ttu-id="89a16-148">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="89a16-148">SceneObject_1</span></span>
    <ul>
      <li><span data-ttu-id="89a16-149">SceneMesh_1</span><span class="sxs-lookup"><span data-stu-id="89a16-149">SceneMesh_1</span></span></li>
      <li><span data-ttu-id="89a16-150">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="89a16-150">SceneQuad_1</span></span></li>
      <li><span data-ttu-id="89a16-151">SceneQuad_2</span><span class="sxs-lookup"><span data-stu-id="89a16-151">SceneQuad_2</span></span></li>
    </ul>
  </li>
  <li><span data-ttu-id="89a16-152">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="89a16-152">SceneObject_2</span></span>
    <ul>
      <li><span data-ttu-id="89a16-153">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="89a16-153">SceneQuad_1</span></span></li>
      <li><span data-ttu-id="89a16-154">SceneQuad_3</span><span class="sxs-lookup"><span data-stu-id="89a16-154">SceneQuad_3</span></span></li>
      </li></ul>
  </li>
  <li><span data-ttu-id="89a16-155">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="89a16-155">SceneObject_3</span></span>
    <ul>
      <li><span data-ttu-id="89a16-156">SceneMesh_3</span><span class="sxs-lookup"><span data-stu-id="89a16-156">SceneMesh_3</span></span></li>
    </ul>
  </ul>
</ul>
</td>
<td>
<ul>
  <li><span data-ttu-id="89a16-157">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="89a16-157">SceneObject_1</span></span></li>
  <li><span data-ttu-id="89a16-158">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="89a16-158">SceneObject_2</span></span></li>
  <li><span data-ttu-id="89a16-159">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="89a16-159">SceneObject_3</span></span></li>
  <li><span data-ttu-id="89a16-160">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="89a16-160">SceneQuad_1</span></span></li>
  <li><span data-ttu-id="89a16-161">SceneQuad_2</span><span class="sxs-lookup"><span data-stu-id="89a16-161">SceneQuad_2</span></span></li>
  <li><span data-ttu-id="89a16-162">SceneQuad_3</span><span class="sxs-lookup"><span data-stu-id="89a16-162">SceneQuad_3</span></span></li>
  <li><span data-ttu-id="89a16-163">SceneMesh_1</span><span class="sxs-lookup"><span data-stu-id="89a16-163">SceneMesh_1</span></span></li>
  <li><span data-ttu-id="89a16-164">SceneMesh_2</span><span class="sxs-lookup"><span data-stu-id="89a16-164">SceneMesh_2</span></span></li>
</ul>
</td>
</tr>
</table>

<span data-ttu-id="89a16-165">In dieser Abbildung wird der Unterschied zwischen dem physischen und dem logischen Layout der Szene hervorgehoben.</span><span class="sxs-lookup"><span data-stu-id="89a16-165">This illustration highlights the difference between the physical and logical layout of the Scene.</span></span> <span data-ttu-id="89a16-166">Auf der linken Seite sehen wir das hierarchische Layout der Daten, die Ihre Anwendung beim Auflisten der Szene sieht.</span><span class="sxs-lookup"><span data-stu-id="89a16-166">On the left, we see the hierarchical layout of the data that your application sees when enumerating the scene.</span></span> <span data-ttu-id="89a16-167">Auf der rechten Seite sehen wir, dass die Szene aus 12 unterschiedlichen Komponenten besteht, auf die bei Bedarf einzeln zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="89a16-167">On the right, we see that the scene is comprised of 12 distinct components that are accessible individually if necessary.</span></span> <span data-ttu-id="89a16-168">Bei der Verarbeitung einer neuen Szene erwarten wir, dass Anwendungen diese Hierarchie logisch durchlaufen. bei der Überwachung zwischen Szenen Aktualisierungen sind einige Anwendungen jedoch möglicherweise nur für bestimmte Komponenten interessant, die von zwei Szenen gemeinsam genutzt werden.</span><span class="sxs-lookup"><span data-stu-id="89a16-168">When processing a new scene, we expect applications to walk this hierarchy logically, however when tracking between scene updates, some applications may only be interested in targeting specific components that are shared between two scenes.</span></span>

## <a name="api-overview"></a><span data-ttu-id="89a16-169">API-Übersicht</span><span class="sxs-lookup"><span data-stu-id="89a16-169">API overview</span></span>

<span data-ttu-id="89a16-170">Der folgende Abschnitt enthält eine allgemeine Übersicht über die Konstrukte in der Szene.</span><span class="sxs-lookup"><span data-stu-id="89a16-170">The following section provides a high-level overview of the constructs in Scene Understanding.</span></span> <span data-ttu-id="89a16-171">In diesem Abschnitt erfahren Sie, wie Szenen dargestellt werden und für welche Komponenten die verschiedenen Komponenten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="89a16-171">Reading this section will give you an  understanding of how scenes are represented, and what the various components do/are used for.</span></span> <span data-ttu-id="89a16-172">Im nächsten Abschnitt werden konkrete Codebeispiele und zusätzliche Details bereitgestellt, die in dieser Übersicht ausgeblendet sind.</span><span class="sxs-lookup"><span data-stu-id="89a16-172">The next section will provide concrete code examples and additional details that are glossed over in this overview.</span></span>

<span data-ttu-id="89a16-173">Alle unten beschriebenen Typen befinden sich im- `Microsoft.MixedReality.SceneUnderstanding` Namespace.</span><span class="sxs-lookup"><span data-stu-id="89a16-173">All of the types described below reside in the `Microsoft.MixedReality.SceneUnderstanding` namespace.</span></span>

### <a name="scenecomponents"></a><span data-ttu-id="89a16-174">Scenecomponents</span><span class="sxs-lookup"><span data-stu-id="89a16-174">SceneComponents</span></span>

<span data-ttu-id="89a16-175">Nachdem Sie nun das logische Layout von Szenen verstanden haben, können wir nun das Konzept der scenecomponents und deren Verwendung zum Verfassen der Hierarchie vorstellen.</span><span class="sxs-lookup"><span data-stu-id="89a16-175">Now that you understand the logical layout of scenes we can now present the concept of SceneComponents and how they're used to compose hierarchy.</span></span> <span data-ttu-id="89a16-176">Scenecomponents sind die präzisesten Zusammensetzungen in sceneunderstanding, die ein einzelnes Kernstück darstellen, z. b. ein Mesh-oder ein Quad-oder ein Begrenzungsfeld.</span><span class="sxs-lookup"><span data-stu-id="89a16-176">SceneComponents are the most granular decompositions in SceneUnderstanding representing a single core thing, for example, a mesh or a quad or a bounding box.</span></span> <span data-ttu-id="89a16-177">Scenecomponents sind Dinge, die unabhängig voneinander aktualisiert werden können und von anderen scenecomponents referenziert werden können. Daher verfügen Sie über eine einzelne globale Eigenschaft, die eine eindeutige ID für diese Art von Nachverfolgung/Verweis Mechanismus zulässt.</span><span class="sxs-lookup"><span data-stu-id="89a16-177">SceneComponents are things that can update independently and can be referenced by other SceneComponents, hence they have a single global property a unique ID, that allow for this type of tracking/referencing mechanism.</span></span> <span data-ttu-id="89a16-178">IDs werden sowohl für die logische Komposition der Szenen Hierarchie als auch für die Objekt Persistenz verwendet (der Vorgang der Aktualisierung einer Szene relativ zu einer anderen).</span><span class="sxs-lookup"><span data-stu-id="89a16-178">Ids are used for the logical composition of scene hierarchy as well as object persistence (the act of updating one scene relative to another.)</span></span> 

<span data-ttu-id="89a16-179">Wenn Sie jede neu berechnete Szene als unterschiedlich behandeln und einfach alle darin enthaltenen Daten auflisten, sind die IDs größtenteils für Sie transparent.</span><span class="sxs-lookup"><span data-stu-id="89a16-179">If you're treating every newly computed scene as being distinct, and simply enumerating all data within it then Ids are largely transparent to you.</span></span> <span data-ttu-id="89a16-180">Wenn Sie jedoch planen, Komponenten über mehrere Updates zu verfolgen, verwenden Sie die IDs, um scenecomponents zwischen Szene Objekten zu indizieren und zu suchen.</span><span class="sxs-lookup"><span data-stu-id="89a16-180">However, if you're planning to track components over several updates you'll use the Ids to index and find SceneComponents between Scene objects.</span></span>

### <a name="sceneobjects"></a><span data-ttu-id="89a16-181">Sceneobjects</span><span class="sxs-lookup"><span data-stu-id="89a16-181">SceneObjects</span></span>

<span data-ttu-id="89a16-182">Ein sceneobject ist eine scenecomponent, die eine Instanz eines "Thing" darstellt (z. b. eine Wand, eine Fläche, eine Obergrenze usw.). ausgedrückt durch ihre Kind-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="89a16-182">A SceneObject is a SceneComponent that represents an instance of a "thing" for example, a wall, a floor, a ceiling, etc.... expressed by their Kind property.</span></span> <span data-ttu-id="89a16-183">Sceneobjects sind geometrisch und verfügen daher über Funktionen und Eigenschaften, die ihre Position im Raum darstellen, Sie enthalten jedoch keine geometrische oder logische Struktur.</span><span class="sxs-lookup"><span data-stu-id="89a16-183">SceneObjects are geometric, and therefore have functions and properties that represent their location in space, however they don't contain any geometric or logical structure.</span></span> <span data-ttu-id="89a16-184">Stattdessen verweisen sceneobjects auf andere scenecomponents, insbesondere scenequads und scenemesches, die die unterschiedlichen Darstellungen bereitstellen, die vom System unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="89a16-184">Instead, SceneObjects reference other SceneComponents, specifically SceneQuads, and SceneMeshes, which provide the varied representations that are supported by the system.</span></span> <span data-ttu-id="89a16-185">Wenn eine neue Szene berechnet wird, listet Ihre Anwendung wahrscheinlich die sceneobjects der Szene auf, um zu verarbeiten, was Sie interessiert.</span><span class="sxs-lookup"><span data-stu-id="89a16-185">When a new scene is computed, your application will most likely enumerate the Scene's SceneObjects to process what it's interested in.</span></span>

<span data-ttu-id="89a16-186">Sceneobjects können eine der folgenden Möglichkeiten aufweisen:</span><span class="sxs-lookup"><span data-stu-id="89a16-186">SceneObjects can have any one of the following:</span></span>

<table>
<tr>
<th><span data-ttu-id="89a16-187">Sceneobjectkind</span><span class="sxs-lookup"><span data-stu-id="89a16-187">SceneObjectKind</span></span></th> <th><span data-ttu-id="89a16-188">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="89a16-188">Description</span></span></th>
</tr>
<tr><td><span data-ttu-id="89a16-189">Hintergrund</span><span class="sxs-lookup"><span data-stu-id="89a16-189">Background</span></span></td><td><span data-ttu-id="89a16-190">Das sceneobject-Objekt ist bekannt, dass es sich <b>nicht</b> um eines der anderen erkannten Arten von Szenen Objekten handelt.</span><span class="sxs-lookup"><span data-stu-id="89a16-190">The SceneObject is known to be <b>not</b> one of the other recognized kinds of scene object.</span></span> <span data-ttu-id="89a16-191">Diese Klasse sollte nicht mit unknown verwechselt werden, wenn der Hintergrund bekanntermaßen nicht "Wall/Floor/Ceiling" ist usw... Obwohl Unknown noch nicht kategorisiert ist.</span><span class="sxs-lookup"><span data-stu-id="89a16-191">This class shouldn't be confused with Unknown where Background is known not to be wall/floor/ceiling etc.... while unknown isn't yet categorized.</span></span></b></td></tr>
<tr><td><span data-ttu-id="89a16-192">Wall</span><span class="sxs-lookup"><span data-stu-id="89a16-192">Wall</span></span></td><td><span data-ttu-id="89a16-193">Eine physische Wand.</span><span class="sxs-lookup"><span data-stu-id="89a16-193">A physical wall.</span></span> <span data-ttu-id="89a16-194">Wände werden als unveränderbare Umgebungs Strukturen angesehen.</span><span class="sxs-lookup"><span data-stu-id="89a16-194">Walls are assumed to be immovable environmental structures.</span></span></td></tr>
<tr><td><span data-ttu-id="89a16-195">Etage</span><span class="sxs-lookup"><span data-stu-id="89a16-195">Floor</span></span></td><td><span data-ttu-id="89a16-196">Die Ebenen sind beliebige Oberflächen, auf denen eine durchlaufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="89a16-196">Floors are any surfaces on which one can walk.</span></span> <span data-ttu-id="89a16-197">Hinweis: die Treppe ist nicht "Floors".</span><span class="sxs-lookup"><span data-stu-id="89a16-197">Note: stairs aren't floors.</span></span> <span data-ttu-id="89a16-198">Beachten Sie auch, dass die Böden eine beliebige über-und-Oberfläche annehmen und daher keine explizite Annahme eines Singular ist.</span><span class="sxs-lookup"><span data-stu-id="89a16-198">Also note, that floors assume any walkable surface and therefore there's no explicit assumption of a singular floor.</span></span> <span data-ttu-id="89a16-199">Strukturen mit mehreren Ebenen, Rampen usw.... sollten alle als Floor klassifiziert werden.</span><span class="sxs-lookup"><span data-stu-id="89a16-199">Multi-level structures, ramps etc.... should all classify as floor.</span></span></td></tr>
<tr><td><span data-ttu-id="89a16-200">Ceiling</span><span class="sxs-lookup"><span data-stu-id="89a16-200">Ceiling</span></span></td><td><span data-ttu-id="89a16-201">Die Oberfläche eines Raums.</span><span class="sxs-lookup"><span data-stu-id="89a16-201">The upper surface of a room.</span></span></td></tr>
<tr><td><span data-ttu-id="89a16-202">Plattform</span><span class="sxs-lookup"><span data-stu-id="89a16-202">Platform</span></span></td><td><span data-ttu-id="89a16-203">Eine große flache Oberfläche, auf der Sie holograms platzieren können.</span><span class="sxs-lookup"><span data-stu-id="89a16-203">A large flat surface on which you could place holograms.</span></span> <span data-ttu-id="89a16-204">Diese stellen tendenziell Tabellen, Countertops und andere große horizontale Flächen dar.</span><span class="sxs-lookup"><span data-stu-id="89a16-204">These tend to represent tables, countertops, and other large horizontal surfaces.</span></span></td></tr>
<tr><td><span data-ttu-id="89a16-205">World</span><span class="sxs-lookup"><span data-stu-id="89a16-205">World</span></span></td><td><span data-ttu-id="89a16-206">Eine reservierte Bezeichnung für geometrische Daten, die für die Bezeichnung agnostisch ist.</span><span class="sxs-lookup"><span data-stu-id="89a16-206">A reserved label for geometric data that is agnostic to labeling.</span></span> <span data-ttu-id="89a16-207">Das Mesh, das durch Festlegen des enableworldmesh-UpdateFlags generiert wird, würde als Welt klassifiziert werden.</span><span class="sxs-lookup"><span data-stu-id="89a16-207">The mesh generated by setting the EnableWorldMesh update flag would be classified as world.</span></span></td></tr>
<tr><td><span data-ttu-id="89a16-208">Unbekannt</span><span class="sxs-lookup"><span data-stu-id="89a16-208">Unknown</span></span></td><td><span data-ttu-id="89a16-209">Dieses Scene-Objekt muss noch klassifiziert und zugewiesen werden.</span><span class="sxs-lookup"><span data-stu-id="89a16-209">This scene object has yet to be classified and assigned a kind.</span></span> <span data-ttu-id="89a16-210">Dies sollte nicht mit dem Hintergrund verwechselt werden, da es sich bei diesem Objekt um beliebige Elemente handeln könnte.</span><span class="sxs-lookup"><span data-stu-id="89a16-210">This shouldn't be confused with Background, as this object could be anything, the system has just not come up with a strong enough classification for it yet.</span></span></td></tr>
</tr>
</table>

### <a name="scenemesh"></a><span data-ttu-id="89a16-211">SceneMesh</span><span class="sxs-lookup"><span data-stu-id="89a16-211">SceneMesh</span></span>

<span data-ttu-id="89a16-212">Eine scenemesh ist eine scenecomponent, die die Geometrie willkürlicher geometrischer Objekte mithilfe einer Dreiecks Liste angleicht.</span><span class="sxs-lookup"><span data-stu-id="89a16-212">A SceneMesh is a SceneComponent that approximates the geometry of arbitrary geometric objects using a triangle list.</span></span> <span data-ttu-id="89a16-213">Scenemesches werden in verschiedenen Kontexten verwendet, Sie können Komponenten der wasserdichten Zellstruktur oder als worldmesh darstellen, das das ungebundene räumliche zustrukturnetz darstellt, das der Szene zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="89a16-213">SceneMeshes are used in several different contexts, they can represent components of the watertight cell structure or as the WorldMesh, which represents the unbounded spatial mapping mesh associated with the Scene.</span></span> <span data-ttu-id="89a16-214">Die für jedes Mesh bereitgestellten Index-und Vertex-Daten verwenden dasselbe vertraute Layout wie der [Scheitelpunkt und die Index Puffer](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) , die zum Rendern von Dreiecksnetzen in allen modernen renderingapis verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="89a16-214">The index and vertex data provided with each mesh uses the same familiar layout as the [vertex and index buffers](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="89a16-215">In der Szene ist es erforderlich, dass die Netze 32-Bit-Indizes verwenden und möglicherweise in Blöcke für bestimmte renderingengines aufgeteilt werden.</span><span class="sxs-lookup"><span data-stu-id="89a16-215">In Scene Understanding, meshes use 32-bit indices and may need to be broken up into chunks for certain rendering engines.</span></span>

#### <a name="winding-order-and-coordinate-systems"></a><span data-ttu-id="89a16-216">Sortieren von Reihenfolge und Koordinatensystemen</span><span class="sxs-lookup"><span data-stu-id="89a16-216">Winding Order and Coordinate Systems</span></span>

<span data-ttu-id="89a16-217">Alle Netzen, die von der Szene verstanden werden, werden voraussichtlich in einem Right-Handed Koordinatensystem mithilfe der Reihenfolge im Uhrzeigersinn zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="89a16-217">All meshes produced by Scene Understanding are expected to return meshes in a Right-Handed coordinate system using clockwise winding order.</span></span> 

<span data-ttu-id="89a16-218">Hinweis: Betriebssystem-Builds vor. 191105 verfügen möglicherweise über einen bekannten Fehler, bei dem "World"-Netzen in Counter-Clockwise Sortierreihenfolge zurückgegeben werden, die anschließend korrigiert wurde.</span><span class="sxs-lookup"><span data-stu-id="89a16-218">Note: OS builds prior to .191105 may have a known bug where "World" meshes were returning in Counter-Clockwise winding order, which has subsequently been fixed.</span></span>

### <a name="scenequad"></a><span data-ttu-id="89a16-219">Scenequad</span><span class="sxs-lookup"><span data-stu-id="89a16-219">SceneQuad</span></span>

<span data-ttu-id="89a16-220">Eine scenequad ist eine scenecomponent, die 2D-Oberflächen darstellt, die die 3D--Welt belegen.</span><span class="sxs-lookup"><span data-stu-id="89a16-220">A SceneQuad is a SceneComponent that represents 2d surfaces that occupy the 3d world.</span></span> <span data-ttu-id="89a16-221">Scenequads können ähnlich wie Arkit arplaneanchor oder Arcore-Ebenen verwendet werden, bieten jedoch eine höhere Funktionalität als 2D-canvasen, die von flachen Apps oder einer erweiterten UX verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="89a16-221">SceneQuads can be used similarly to ARKit ARPlaneAnchor or ARCore Planes but they offer more high-level functionality as 2d canvases to be used by flat apps, or augmented UX.</span></span> <span data-ttu-id="89a16-222">2D-spezifische APIs werden für Quads bereitgestellt, mit denen die Platzierung und das Layout einfach zu verwenden sind, und die Entwicklung (mit Ausnahme des Renderings) mit Quads sollte eher dem Arbeiten mit 2D-kanvasen als 3D--Meshes ähneln.</span><span class="sxs-lookup"><span data-stu-id="89a16-222">2D specific APIs are provided for quads that make placement and layout simple to use, and developing (with the exception of rendering) with quads should feel more akin to working with 2d canvases than 3d meshes.</span></span>

#### <a name="scenequad-shape"></a><span data-ttu-id="89a16-223">Scenequad-Form</span><span class="sxs-lookup"><span data-stu-id="89a16-223">SceneQuad shape</span></span>

<span data-ttu-id="89a16-224">Scenequads definieren eine begrenzte rechteckige Oberfläche in 2D.</span><span class="sxs-lookup"><span data-stu-id="89a16-224">SceneQuads define a bounded rectangular surface in 2d.</span></span> <span data-ttu-id="89a16-225">Scenequads stellen jedoch Oberflächen mit beliebigen und potenziell komplexen Formen dar (z. b. eine ringförmige Tabelle). Wenn Sie die komplexe Form der Oberfläche eines viervieres darstellen möchten, können Sie die getsurfacemask-API verwenden, um die Form der Oberfläche auf einem von Ihnen bereitgestellten Bild Puffer zu Renderern.</span><span class="sxs-lookup"><span data-stu-id="89a16-225">However, SceneQuads are representing surfaces with arbitrary and potentially complex shapes (e.g. a donut shaped table.) To represent the complex shape of the surface of a quad you may use the GetSurfaceMask API to render the shape of the surface onto an image buffer you provide.</span></span> <span data-ttu-id="89a16-226">Wenn das sceneobject mit dem Quad auch ein Mesh hat, sollte der Gitter Dreiecke diesem gerenderten Bild entsprechen, beide stellen eine echte Geometrie der Oberfläche dar, entweder in 2D-oder 3D--Koordinaten.</span><span class="sxs-lookup"><span data-stu-id="89a16-226">If the SceneObject that has the quad also has a mesh, the mesh triangles should be equivalent to this rendered image, they both represent real geometry of the surface, either in 2d or 3d coordinates.</span></span>

## <a name="scene-understanding-sdk-details-and-reference"></a><span data-ttu-id="89a16-227">Scene Understanding SDK-Details und-Referenz</span><span class="sxs-lookup"><span data-stu-id="89a16-227">Scene understanding SDK details and reference</span></span>

<span data-ttu-id="89a16-228">Im folgenden Abschnitt wird erläutert, wie Sie mit den Grundlagen von sceneunderstanding vertraut werden.</span><span class="sxs-lookup"><span data-stu-id="89a16-228">The following section will help get you familiar with the basics of SceneUnderstanding.</span></span> <span data-ttu-id="89a16-229">In diesem Abschnitt werden die Grundlagen erläutert. zu diesem Zeitpunkt sollten Sie über genügend Kontext verfügen, um die Beispielanwendungen zu durchsuchen und zu sehen, wie sceneunderstanding ganzheitlich genutzt wird.</span><span class="sxs-lookup"><span data-stu-id="89a16-229">This section should provide you with the basics, at which point you should have enough context to browse through the sample applications to see how SceneUnderstanding is used holistically.</span></span>

### <a name="initialization"></a><span data-ttu-id="89a16-230">Initialisierung</span><span class="sxs-lookup"><span data-stu-id="89a16-230">Initialization</span></span>

<span data-ttu-id="89a16-231">Der erste Schritt bei der Arbeit mit sceneunderstanding besteht darin, dass Ihre Anwendung auf ein Szene Objekt verweist.</span><span class="sxs-lookup"><span data-stu-id="89a16-231">The first step to working with SceneUnderstanding is for your application to gain reference to a Scene object.</span></span> <span data-ttu-id="89a16-232">Dies kann auf zwei Arten erfolgen: eine Szene kann entweder vom Treiber berechnet werden, oder eine vorhandene Szene, die in der Vergangenheit berechnet wurde, kann deserialisiert werden.</span><span class="sxs-lookup"><span data-stu-id="89a16-232">This can be done in one of two ways, a Scene can either be computed by the driver, or an existing Scene that was computed in the past can be de-serialized.</span></span> <span data-ttu-id="89a16-233">Letzteres ist für die Arbeit mit sceneunderstanding während der Entwicklung nützlich, bei der Anwendungen und Erfahrungen schnell ohne ein gemischtes Reality-Gerät prototypisiert werden können.</span><span class="sxs-lookup"><span data-stu-id="89a16-233">The latter is useful for working with SceneUnderstanding during development, where applications and experiences can be prototyped quickly without a mixed reality device.</span></span>

<span data-ttu-id="89a16-234">Szenen werden mithilfe eines sceneobserver berechnet.</span><span class="sxs-lookup"><span data-stu-id="89a16-234">Scenes are computed using a SceneObserver.</span></span> <span data-ttu-id="89a16-235">Bevor Sie eine Szene erstellen, sollte Ihre Anwendung Ihr Gerät Abfragen, um sicherzustellen, dass Sie sceneunderstanding unterstützt, sowie den Benutzer Zugriff auf Informationen anfordern, die von sceneunderstanding benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="89a16-235">Before creating a Scene, your application should query your device to ensure that it supports SceneUnderstanding, as well as to request user access for information that SceneUnderstanding needs.</span></span>

```cs
if (!SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

<span data-ttu-id="89a16-236">Wenn requestaccessasync () nicht aufgerufen wird, tritt beim Berechnen einer neuen Szene ein Fehler auf.</span><span class="sxs-lookup"><span data-stu-id="89a16-236">If RequestAccessAsync() is not called, computing a new Scene will fail.</span></span> <span data-ttu-id="89a16-237">Als Nächstes berechnen wir eine neue Szene, die auf dem Mixed Reality-Headset liegt und über einen Radius von 10 Metern verfügt.</span><span class="sxs-lookup"><span data-stu-id="89a16-237">Next we will compute a new scene that's rooted around the Mixed Reality headset and has a 10-meter radius.</span></span>

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

### <a name="initialization-from-data-also-known-as-the-pc-path"></a><span data-ttu-id="89a16-238">Initialisierung von Daten (auch als bezeichnet).</span><span class="sxs-lookup"><span data-stu-id="89a16-238">Initialization from Data (also known as.</span></span> <span data-ttu-id="89a16-239">der PC-Pfad)</span><span class="sxs-lookup"><span data-stu-id="89a16-239">the PC Path)</span></span>

<span data-ttu-id="89a16-240">Szenen können für den direkten Verbrauch berechnet werden, Sie können jedoch auch in serialisierter Form für die spätere Verwendung berechnet werden.</span><span class="sxs-lookup"><span data-stu-id="89a16-240">While Scenes can be computed for direct consumption, they can also be computed in serialized form for later use.</span></span> <span data-ttu-id="89a16-241">Dies hat sich als nützlich für die Entwicklung bewährt, da Entwickler damit arbeiten können, ohne dass ein Gerät benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="89a16-241">This has proven to be useful for development as it allows developers to work in and test Scene Understanding without the need for a device.</span></span> <span data-ttu-id="89a16-242">Der Vorgang der Serialisierung einer Szene ist nahezu identisch mit dem berechnen, die Daten werden an Ihre Anwendung zurückgegeben, anstatt lokal vom SDK deserialisiert zu werden.</span><span class="sxs-lookup"><span data-stu-id="89a16-242">The act of serializing a scene is nearly identical to computing it, the data is returned to your application instead of being deserialized locally by the SDK.</span></span> <span data-ttu-id="89a16-243">Sie können Sie dann selbst deserialisieren oder zur späteren Verwendung speichern.</span><span class="sxs-lookup"><span data-stu-id="89a16-243">You may then deserialize it yourself or save it for future use.</span></span>

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

### <a name="sceneobject-enumeration"></a><span data-ttu-id="89a16-244">Sceneobject-Enumeration</span><span class="sxs-lookup"><span data-stu-id="89a16-244">SceneObject Enumeration</span></span>

<span data-ttu-id="89a16-245">Nun, da Ihre Anwendung eine Szene hat, wird Ihre Anwendung mit sceneobjects beschäftigt und interagiert.</span><span class="sxs-lookup"><span data-stu-id="89a16-245">Now that your application has a scene, your application will be looking at and interacting with SceneObjects.</span></span> <span data-ttu-id="89a16-246">Dies erfolgt durch den Zugriff auf die **sceneobjects** -Eigenschaft:</span><span class="sxs-lookup"><span data-stu-id="89a16-246">This is done by accessing the **SceneObjects** property:</span></span>

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

### <a name="component-update-and-refinding-components"></a><span data-ttu-id="89a16-247">Komponenten Update und neusuchen von Komponenten</span><span class="sxs-lookup"><span data-stu-id="89a16-247">Component update and refinding components</span></span>

<span data-ttu-id="89a16-248">Es gibt eine weitere Funktion, die Komponenten in der Szene abruft, die als \**_findComponent_* _ bezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="89a16-248">There's another function that retrieves components in the Scene called \**_FindComponent_* _.</span></span> <span data-ttu-id="89a16-249">Diese Funktion ist nützlich, wenn Überwachungs Objekte aktualisiert und in späteren Szenen gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="89a16-249">This function is useful when updating tracking objects and finding them in later scenes.</span></span> <span data-ttu-id="89a16-250">Mit dem folgenden Code wird eine neue Szene in Relation zu einer vorherigen Szene berechnet und dann die Fläche in der neuen Szene gefunden.</span><span class="sxs-lookup"><span data-stu-id="89a16-250">The following code will compute a new scene relative to a previous scene and then find the floor in the new scene.</span></span>

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

## <a name="accessing-meshes-and-quads-from-scene-objects"></a><span data-ttu-id="89a16-251">Zugreifen auf Meshes und Quads von Szenen Objekten</span><span class="sxs-lookup"><span data-stu-id="89a16-251">Accessing Meshes and Quads from Scene Objects</span></span>

<span data-ttu-id="89a16-252">Nachdem sceneobjects gefunden wurde, möchte Ihre Anwendung höchstwahrscheinlich auf die Daten zugreifen, die in den Quads/Meshes enthalten sind, aus denen Sie besteht.</span><span class="sxs-lookup"><span data-stu-id="89a16-252">Once SceneObjects have been found your application will most likely want to access the data that is contained in the quads/meshes that it is composed of.</span></span> <span data-ttu-id="89a16-253">Der Zugriff auf diese Daten erfolgt über die Eigenschaften " _*_Quads_*_ " und " _*_Meshes_*_ ".</span><span class="sxs-lookup"><span data-stu-id="89a16-253">This data is accessed with the _*_Quads_*_ and _*_Meshes_*_ properties.</span></span> <span data-ttu-id="89a16-254">Mit dem folgenden Code werden alle Quads und Netzen des Floor-Objekts aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="89a16-254">The following code will enumerate all quads and meshes of our floor object.</span></span>

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

<span data-ttu-id="89a16-255">Beachten Sie, dass es sich um das sceneobject-Objekt mit der Transformation handelt, die relativ zum Ursprung der Szene ist.</span><span class="sxs-lookup"><span data-stu-id="89a16-255">Notice that it's the SceneObject that has the transform that is relative to the Scene origin.</span></span> <span data-ttu-id="89a16-256">Der Grund hierfür ist, dass das sceneobject-Objekt eine Instanz eines "Thing" darstellt und im Raum einstellbar ist, die Quads und die Netzen eine Geometrie darstellen, die relativ zu ihrem übergeordneten Element transformiert wird.</span><span class="sxs-lookup"><span data-stu-id="89a16-256">This is because the SceneObject represents an instance of a "thing" and is locatable in space, the quads, and meshes represent geometry that is transformed relative to their parent.</span></span> <span data-ttu-id="89a16-257">Es ist möglich, dass separate sceneobjects auf die gleichen scenemesh/scenequad scenecomponents verweisen, und es ist auch möglich, dass ein sceneobject-Objekt über mehr als eine scenemesh/scenequad verfügt.</span><span class="sxs-lookup"><span data-stu-id="89a16-257">It's possible for separate SceneObjects to reference the same SceneMesh/SceneQuad SceneComponents, and it's also possible that a SceneObject has more than one SceneMesh/SceneQuad.</span></span>

### <a name="dealing-with-transforms"></a><span data-ttu-id="89a16-258">Umgang mit Transformationen</span><span class="sxs-lookup"><span data-stu-id="89a16-258">Dealing with Transforms</span></span>

<span data-ttu-id="89a16-259">Das Verständnis der Szene hat beim Umgang mit Transformationen einen absichtlichen Versuch unternommen, an herkömmlichen 3D-Szenen Darstellungen auszurichten.</span><span class="sxs-lookup"><span data-stu-id="89a16-259">Scene Understanding has made a deliberate attempt to align with traditional 3D scene representations when dealing with transforms.</span></span> <span data-ttu-id="89a16-260">Daher ist jede Szene auf ein einzelnes Koordinatensystem beschränkt, ähnlich wie die gängigsten 3D-Umwelt Darstellungen.</span><span class="sxs-lookup"><span data-stu-id="89a16-260">Each Scene is therefore confined to a single coordinate system much like most common 3D environmental representations.</span></span> <span data-ttu-id="89a16-261">Sceneobjects stellen jeweils ihren Speicherort relativ zu diesem Koordinatensystem bereit.</span><span class="sxs-lookup"><span data-stu-id="89a16-261">SceneObjects each provide their location relative to that coordinate system.</span></span> <span data-ttu-id="89a16-262">Wenn Ihre Anwendung mit Szenen beschäftigt ist, die das Limit eines einzelnen Ursprungs überschreiten, können Sie sceneobjects an spatialanchor anfügen oder mehrere Szenen generieren und zusammen zusammenführen, aber aus Gründen der Einfachheit gehen wir davon aus, dass die wasserdichten Szenen in Ihrem eigenen Ursprung vorhanden sind, der durch eine durch Scene. originspatialgraphnodeid definierte NodeId lokalisiert wird.</span><span class="sxs-lookup"><span data-stu-id="89a16-262">If your application is dealing with Scenes that stretch the limit of what a single origin provides it can anchor SceneObjects to SpatialAnchors, or generate several scenes and merge them together, but for simplicity we assume that watertight scenes exist in their own origin that's localized by one NodeId defined by Scene.OriginSpatialGraphNodeId.</span></span>

<span data-ttu-id="89a16-263">Der folgende Unity-Code zeigt beispielsweise, wie Sie die Windows-perception-und Unity-APIs verwenden, um Koordinatensysteme gleich abzustimmen.</span><span class="sxs-lookup"><span data-stu-id="89a16-263">The following Unity code, for example, shows how to use Windows Perception and Unity APIs to align coordinate systems together.</span></span> <span data-ttu-id="89a16-264">Ausführliche Informationen zum Abrufen eines spatialcoordinatesystem, das dem Welt [Ursprung von Unity](https://docs.microsoft.com//windows/mixed-reality/unity-xrdevice-advanced) entspricht, finden Sie unter [spatialcoordinatesystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) und [spatialgraphinteroppreview](https://docs.microsoft.com//uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) .</span><span class="sxs-lookup"><span data-stu-id="89a16-264">See [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) and [SpatialGraphInteropPreview](https://docs.microsoft.com//uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) for details on the Windows Perception APIs, and [Mixed Reality native objects in Unity](https://docs.microsoft.com//windows/mixed-reality/unity-xrdevice-advanced) for details on obtaining a SpatialCoordinateSystem that corresponds to Unity's world origin.</span></span>

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

<span data-ttu-id="89a16-265">Jede `SceneObject` verfügt über eine Transformation, die dann auf das Objekt angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="89a16-265">Each `SceneObject` has a transform, which is then applied to that object.</span></span> <span data-ttu-id="89a16-266">In Unity konvertieren wir in Rechte übergebene Koordinaten und weisen lokale Transformationen wie folgt zu:</span><span class="sxs-lookup"><span data-stu-id="89a16-266">In Unity we convert to right handed coordinates and assign local transforms as so:</span></span>

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

### <a name="quad"></a><span data-ttu-id="89a16-267">Quad</span><span class="sxs-lookup"><span data-stu-id="89a16-267">Quad</span></span>

<span data-ttu-id="89a16-268">Die Quads wurden zur Unterstützung von 2D-Platzierungs Szenarios entwickelt und sollten sich als Erweiterungen für 2D-Canvas-UX-Elemente vorstellen.</span><span class="sxs-lookup"><span data-stu-id="89a16-268">Quads were designed to help 2D placement scenarios and should be thought of as extensions to 2D canvas UX elements.</span></span> <span data-ttu-id="89a16-269">Obwohl es sich bei den Quads um Komponenten von sceneobjects handelt, die in 3D gerendert werden können, werden die Quad-APIs selbst annehmen, dass die Quad-</span><span class="sxs-lookup"><span data-stu-id="89a16-269">While Quads are components of SceneObjects and can be rendered in 3D, the Quad APIs themselves assume Quads are 2D structures.</span></span> <span data-ttu-id="89a16-270">Sie bieten Informationen wie Block, Form und Bereitstellen von APIs für die Platzierung.</span><span class="sxs-lookup"><span data-stu-id="89a16-270">They offer information such as extent, shape, and provide APIs for placement.</span></span>

<span data-ttu-id="89a16-271">Die Unterbrechungen haben rechteckige Blöcke, stellen aber beliebig geformte 2D-Oberflächen dar.</span><span class="sxs-lookup"><span data-stu-id="89a16-271">Quads have rectangular extents, but they represent arbitrarily shaped 2D surfaces.</span></span> <span data-ttu-id="89a16-272">Um die Platzierung auf diesen 2D-Oberflächen zu ermöglichen, die mit der 3D-Umgebung interagieren, bieten Sie Hilfsprogramme, um diese Interaktion zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="89a16-272">To enable placement on these 2D surfaces that interact with the 3D environment quads offer utilities to make this interaction possible.</span></span> <span data-ttu-id="89a16-273">Das grundlegendes Verständnis von Szenen bietet derzeit zwei Funktionen, _ *findcentermustplacement*\* und **getsurfakemask**.</span><span class="sxs-lookup"><span data-stu-id="89a16-273">Currently Scene Understanding provides two such functions, _ *FindCentermostPlacement*\* and **GetSurfaceMask**.</span></span> <span data-ttu-id="89a16-274">Findcentermostplacement ist eine API auf hoher Ebene, die eine Position auf dem Quad sucht, an der ein Objekt platziert werden kann, und versucht, den optimalen Speicherort für das Objekt zu finden, das sicherstellt, dass das von Ihnen bereitgestellte Begrenzungsfeld auf der zugrunde liegenden Oberfläche bleibt.</span><span class="sxs-lookup"><span data-stu-id="89a16-274">FindCentermostPlacement is a high-level API that locates a position on the quad where an object can be placed and will try to find the best location for your object guaranteeing that the bounding box you provide will stay on the underlying surface.</span></span>

> [!NOTE]
> <span data-ttu-id="89a16-275">Die Koordinaten der Ausgabe sind relativ zum Quad in "Quad-Space", wobei die obere linke Ecke (x = 0, y = 0) ist, ebenso wie bei anderen Windows-Rect-Typen.</span><span class="sxs-lookup"><span data-stu-id="89a16-275">The coordinates of the output are relative to the quad in "quad space" with the top left corner being (x = 0, y = 0), just as it would be with other windows Rect types.</span></span> <span data-ttu-id="89a16-276">Berücksichtigen Sie dies, wenn Sie mit den Ursprüngen ihrer eigenen Objekte arbeiten.</span><span class="sxs-lookup"><span data-stu-id="89a16-276">Be sure to take this into account when working with the origins of your own objects.</span></span> 

<span data-ttu-id="89a16-277">Im folgenden Beispiel wird gezeigt, wie Sie den am häufigsten ersetzbaren Speicherort suchen und ein – Hologramm für das Vierfache verankern.</span><span class="sxs-lookup"><span data-stu-id="89a16-277">The following example shows how to find the centermost placeable location and anchor a hologram to the quad.</span></span>

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

<span data-ttu-id="89a16-278">Die Schritte 1-4 sind stark von Ihrem speziellen Framework/der Implementierung abhängig, die Designs sollten jedoch ähnlich sein.</span><span class="sxs-lookup"><span data-stu-id="89a16-278">Steps 1-4 are highly dependent on your particular framework/implementation, but the themes should be similar.</span></span> <span data-ttu-id="89a16-279">Es ist wichtig zu beachten, dass das Vierfache eine begrenzte 2D-Ebene darstellt, die im Raum lokalisiert wird.</span><span class="sxs-lookup"><span data-stu-id="89a16-279">It's important to note that the Quad simply represents a bounded 2D plane that is localized in space.</span></span> <span data-ttu-id="89a16-280">Wenn Ihr Modul/Framework weiß, wo das Vierfache ist, und die Objekte in Relation zum Quad Hogen, werden Ihre Hologramme in Bezug auf die reale Welt ordnungsgemäß gefunden.</span><span class="sxs-lookup"><span data-stu-id="89a16-280">By having your engine/framework know where the quad is and rooting your objects relative to the quad, your holograms will be located correctly with respect to the real world.</span></span> 

<!-- 
// TODO: Add sample link when released
For more detailed information please see our samples on quads which show specific implementations.
-->

### <a name="mesh"></a><span data-ttu-id="89a16-281">Mesh</span><span class="sxs-lookup"><span data-stu-id="89a16-281">Mesh</span></span>

<span data-ttu-id="89a16-282">Meshes stellen geometrische Darstellungen von Objekten oder Umgebungen dar.</span><span class="sxs-lookup"><span data-stu-id="89a16-282">Meshes represent geometric representations of objects or environments.</span></span> <span data-ttu-id="89a16-283">Ähnlich wie bei der [räumlichen Zuordnung](../../design/spatial-mapping.md)verwendet Mesh-Index-und Vertex-Daten, die für jedes räumliche Oberflächen Mesh bereitgestellt werden, dasselbe vertraute Layout wie der Scheitelpunkt und die Index Puffer, die zum Rendern von Dreiecksnetzen in allen modernen Rendering-APIs verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="89a16-283">Much like [spatial mapping](../../design/spatial-mapping.md), mesh index and vertex data provided with each spatial surface mesh uses the same familiar layout as the vertex and index buffers that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="89a16-284">Vertex-Positionen werden im Koordinatensystem von bereitgestellt `Scene` .</span><span class="sxs-lookup"><span data-stu-id="89a16-284">Vertex positions are provided in the coordinate system of the `Scene`.</span></span> <span data-ttu-id="89a16-285">Die spezifischen APIs, die zum Verweisen auf diese Daten verwendet werden, lauten wie folgt:</span><span class="sxs-lookup"><span data-stu-id="89a16-285">The specific APIs used to reference this data are as follows:</span></span>

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(System.Numerics.Vector3[] vertices);
```

<span data-ttu-id="89a16-286">Der folgende Code enthält ein Beispiel für das Erstellen einer Dreiecks Liste aus der Mesh-Struktur:</span><span class="sxs-lookup"><span data-stu-id="89a16-286">The following code provides an example of generating a triangle list from the mesh structure:</span></span>

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
System.Numerics.Vector3[] positions = new System.Numerics.Vector3[mesh.VertexCount];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

<span data-ttu-id="89a16-287">Der Index/Scheitelpunkt Puffer muss >= der Index/Scheitelpunkt Anzahl sein, kann aber auch willkürlich skaliert werden, um eine effiziente Arbeitsspeicher Wiederverwendung zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="89a16-287">The index/vertex buffers must be >= the index/vertex counts, but otherwise can be arbitrarily sized allowing for efficient memory reuse.</span></span>

### <a name="collidermesh"></a><span data-ttu-id="89a16-288">Collidermesh</span><span class="sxs-lookup"><span data-stu-id="89a16-288">ColliderMesh</span></span>

<span data-ttu-id="89a16-289">Szene Objekte ermöglichen den Zugriff auf Mesh-und Collider-Mesh-Daten über die Eigenschaften Meshes und collidermeshes.</span><span class="sxs-lookup"><span data-stu-id="89a16-289">Scene objects provide access to mesh and collider mesh data via the Meshes and ColliderMeshes properties.</span></span> <span data-ttu-id="89a16-290">Diese Meshs Stimmen immer überein, was bedeutet, dass der Index der ' Netzen '-Eigenschaft die gleiche Geometrie darstellt wie der Index ' Index ' der ' collidermeshes '-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="89a16-290">These meshes will always match, meaning that the i'th index of the Meshes property represents the same geometry as the i'th index of the ColliderMeshes property.</span></span> <span data-ttu-id="89a16-291">Wenn die Runtime/das Objekt Collider-Meshes unterstützt, erhalten Sie garantiert das niedrigste Polygon mit der höchsten anordnen, und es wird empfohlen, collidermeshes zu verwenden, wenn die Anwendung Kollisionen verwenden würde.</span><span class="sxs-lookup"><span data-stu-id="89a16-291">If the runtime/object supports collider meshes, you are guaranteed to get the lowest polygon, highest order approximation and it's good practice to use ColliderMeshes wherever your application would use colliders.</span></span> <span data-ttu-id="89a16-292">Wenn das System keine Kollisionen unterstützt, ist das in collidermeshes zurückgegebene Mesh-Objekt dasselbe Objekt wie das Mesh, das Speicher Einschränkungen reduziert.</span><span class="sxs-lookup"><span data-stu-id="89a16-292">If the system does not support colliders the Mesh object returned in ColliderMeshes will be the same object as the mesh reducing memory constraints.</span></span>

## <a name="developing-with-scene-understanding"></a><span data-ttu-id="89a16-293">Entwickeln mit Szenen Verständnis</span><span class="sxs-lookup"><span data-stu-id="89a16-293">Developing with scene understanding</span></span>

<span data-ttu-id="89a16-294">An diesem Punkt sollten Sie die wichtigsten Bausteine der Szene verstehen, die Laufzeit und SDK versteht.</span><span class="sxs-lookup"><span data-stu-id="89a16-294">At this point, you should understand the core building blocks of the scene understanding runtime and SDK.</span></span> <span data-ttu-id="89a16-295">Der größte Teil der Leistungsfähigkeit und Komplexität liegt in Zugriffs Mustern, der Interaktion mit 3D-Frameworks und Tools, die zusätzlich zu diesen APIs verfasst werden können, um erweiterte Aufgaben wie räumliche Planung, Raumanalyse, Navigation, Physik usw. auszuführen.</span><span class="sxs-lookup"><span data-stu-id="89a16-295">The bulk of the power and complexity lies in access patterns, interaction with 3D frameworks, and tools that can be written on top of these APIs to do more advanced tasks like spatial planning, room analysis, navigation, physics, and so on.</span></span> <span data-ttu-id="89a16-296">Wir hoffen, diese Beispiele in Beispielen zu erfassen, die Sie in die richtige Richtung bringen sollten, um Ihre Szenarios zu glänzen.</span><span class="sxs-lookup"><span data-stu-id="89a16-296">We hope to capture these in samples that should hopefully guide you in the proper direction to make your scenarios shine.</span></span> <span data-ttu-id="89a16-297">Wenn es Beispiele oder Szenarios gibt, die wir nicht behandeln, informieren Sie uns, und wir versuchen, das Dokument/den Prototyp zu dokumentieren.</span><span class="sxs-lookup"><span data-stu-id="89a16-297">If there are samples or scenarios we aren't addressing, let us know and we'll try to document/prototype what you need.</span></span>

### <a name="where-can-i-get-sample-code"></a><span data-ttu-id="89a16-298">Wo kann ich Beispielcode erhalten?</span><span class="sxs-lookup"><span data-stu-id="89a16-298">Where can I get sample code?</span></span>

<span data-ttu-id="89a16-299">Szeneninformationen zum Beispielcode für Unity finden Sie auf unserer Seite mit der [Unity-Beispielseite](https://github.com/sceneunderstanding-microsoft/unitysample) .</span><span class="sxs-lookup"><span data-stu-id="89a16-299">Scene Understanding sample code for Unity can be found on our [Unity Sample Page](https://github.com/sceneunderstanding-microsoft/unitysample) page.</span></span> <span data-ttu-id="89a16-300">Diese Anwendung ermöglicht Ihnen die Kommunikation mit Ihrem Gerät und das Rendering der verschiedenen Szenen Objekte, oder Sie können eine serialisierte Szene auf Ihren PC laden und das Verständnis von Szenen ohne Gerät ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="89a16-300">This application will allow you to communicate with your device and render the various scene objects, or, it will allow you to load a serialized scene on your PC and allow you to experience Scene Understanding without a device.</span></span>

### <a name="where-can-i-get-sample-scenes"></a><span data-ttu-id="89a16-301">Wo kann ich Beispiel Szenen erhalten?</span><span class="sxs-lookup"><span data-stu-id="89a16-301">Where can I get sample scenes?</span></span>

<span data-ttu-id="89a16-302">Wenn Sie über eine HoloLens2 verfügen, können Sie jede Szene speichern, die Sie erfasst haben, indem Sie die Ausgabe von "computeserializedasync" in der Datei speichern und Sie in ihrer eigenen Weise deserialisieren.</span><span class="sxs-lookup"><span data-stu-id="89a16-302">If you have a HoloLens2, you can save any scene you've captured by saving the output of ComputeSerializedAsync to file and deserializing it at your own convenience.</span></span> 

<span data-ttu-id="89a16-303">Wenn Sie nicht über ein HoloLens2-Gerät verfügen, aber mit Szenen Verständnis experimentieren möchten, müssen Sie eine vorab erfasste Szene herunterladen.</span><span class="sxs-lookup"><span data-stu-id="89a16-303">If you don't have a HoloLens2 device but want to play with Scene Understanding, you'll need to download a pre-captured scene.</span></span> <span data-ttu-id="89a16-304">Das Beispiel für Szenen Verständnis wird derzeit in serialisierten Szenen geliefert, die Sie herunterladen und in ihrer eigenen Weise verwenden können.</span><span class="sxs-lookup"><span data-stu-id="89a16-304">The Scene Understanding sample currently ships with serialized scenes that can be downloaded and used at your own convenience.</span></span> <span data-ttu-id="89a16-305">Sie finden Sie hier:</span><span class="sxs-lookup"><span data-stu-id="89a16-305">You can find them here:</span></span>

[<span data-ttu-id="89a16-306">Szenen Einblick in Beispiel Szenen</span><span class="sxs-lookup"><span data-stu-id="89a16-306">Scene Understanding Sample Scenes</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples/tree/master/Assets/Resources/SerializedScenesForPCPath)

## <a name="see-also"></a><span data-ttu-id="89a16-307">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="89a16-307">See also</span></span>

* [<span data-ttu-id="89a16-308">Räumliche Abbildung</span><span class="sxs-lookup"><span data-stu-id="89a16-308">Spatial mapping</span></span>](../../design/spatial-mapping.md)
* [<span data-ttu-id="89a16-309">Grundlegendes zu Szenen</span><span class="sxs-lookup"><span data-stu-id="89a16-309">Scene understanding</span></span>](../../design/scene-understanding.md)
* [<span data-ttu-id="89a16-310">Unity-Beispiel</span><span class="sxs-lookup"><span data-stu-id="89a16-310">Unity Sample</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)
