---
title: Richtlinien für das Codieren
description: Programmierprinzipien und Konventionen, die beim Beitragen zum MRTK zu befolgen sind.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, C#,
ms.openlocfilehash: 8887e248bd550bdd7a59f19c16df1ec3647ceff7
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145248"
---
# <a name="coding-guidelines"></a><span data-ttu-id="48536-104">Codierungsrichtlinien</span><span class="sxs-lookup"><span data-stu-id="48536-104">Coding guidelines</span></span>

<span data-ttu-id="48536-105">In diesem Dokument werden die Codierungsprinzipien und -konventionen beschrieben, die beim Beitragen zum MRTK zu befolgen sind.</span><span class="sxs-lookup"><span data-stu-id="48536-105">This document outlines coding principles and conventions to follow when contributing to MRTK.</span></span>

---

## <a name="philosophy"></a><span data-ttu-id="48536-106">Philosophie</span><span class="sxs-lookup"><span data-stu-id="48536-106">Philosophy</span></span>

### <a name="be-concise-and-strive-for-simplicity"></a><span data-ttu-id="48536-107">Seien Sie präzise, und setzen Sie sich für Einfachheit ein.</span><span class="sxs-lookup"><span data-stu-id="48536-107">Be concise and strive for simplicity</span></span>

<span data-ttu-id="48536-108">Die einfachste Lösung ist häufig die beste.</span><span class="sxs-lookup"><span data-stu-id="48536-108">The simplest solution is often the best.</span></span> <span data-ttu-id="48536-109">Dies ist ein überschreibende Ziel dieser Richtlinien und sollte das Ziel aller Codierungsaktivitäten sein.</span><span class="sxs-lookup"><span data-stu-id="48536-109">This is an overriding aim of these guidelines and should be the goal of all coding activity.</span></span> <span data-ttu-id="48536-110">Ein Teil des einfachen Seins ist, präzise und konsistent mit vorhandenem Code zu sein.</span><span class="sxs-lookup"><span data-stu-id="48536-110">Part of being simple is being concise, and consistent with existing code.</span></span> <span data-ttu-id="48536-111">Versuchen Sie, den Code einfach zu halten.</span><span class="sxs-lookup"><span data-stu-id="48536-111">Try to keep your code simple.</span></span>

<span data-ttu-id="48536-112">Leser sollten nur Artefakte finden, die nützliche Informationen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="48536-112">Readers should only encounter artifacts that provide useful information.</span></span> <span data-ttu-id="48536-113">Kommentare, die das offensichtliche Wiedererlädnen wieder geben, liefern beispielsweise keine zusätzlichen Informationen und erhöhen das Rauschen zu Signalverhältnis.</span><span class="sxs-lookup"><span data-stu-id="48536-113">For example, comments that restate what is obvious provide no extra information and increase the noise to signal ratio.</span></span>

<span data-ttu-id="48536-114">Halten Sie die Codelogik einfach.</span><span class="sxs-lookup"><span data-stu-id="48536-114">Keep code logic simple.</span></span> <span data-ttu-id="48536-115">Beachten Sie, dass es sich dabei nicht um eine Aussage zur Verwendung der geringsten Anzahl von Zeilen handelt, um die Größe von Bezeichnernamen oder geschweiften Klammern zu minimieren, sondern um die Reduzierung der Anzahl von Konzepten und die Maximierung der Sichtbarkeit dieser Zeilen durch vertraute Muster.</span><span class="sxs-lookup"><span data-stu-id="48536-115">Note that this is not a statement about using the fewest number of lines, minimizing the size of identifier names or brace style, but about reducing the number of concepts and maximizing the visibility of those through familiar patterns.</span></span>

### <a name="produce-consistent-readable-code"></a><span data-ttu-id="48536-116">Erstellen von konsistentem, lesbaren Code</span><span class="sxs-lookup"><span data-stu-id="48536-116">Produce consistent, readable code</span></span>

<span data-ttu-id="48536-117">Die Lesbarkeit von Code ist mit niedrigen Mängelraten korreliert.</span><span class="sxs-lookup"><span data-stu-id="48536-117">Code readability is correlated with low defect rates.</span></span> <span data-ttu-id="48536-118">Versuchen Sie, Leicht lesbaren Code zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="48536-118">Strive to create code that is easy to read.</span></span> <span data-ttu-id="48536-119">Versuchen Sie, Code zu erstellen, der über einfache Logik verfügt und vorhandene Komponenten erneut verwendet, da dies auch zur Sicherstellung der Richtigkeit beiträgt.</span><span class="sxs-lookup"><span data-stu-id="48536-119">Strive to create code that has simple logic and re-uses existing components as it will also help ensure correctness.</span></span>

<span data-ttu-id="48536-120">Alle Details des codes, den Sie erzeugen, sind wichtig, von den grundlegendsten Details der Richtigkeit bis zu konsistentem Stil und konsistenter Formatierung.</span><span class="sxs-lookup"><span data-stu-id="48536-120">All details of the code you produce matter, from the most basic detail of correctness to consistent style and formatting.</span></span> <span data-ttu-id="48536-121">Halten Sie Ihren Codierungsstil konsistent mit dem, was bereits vorhanden ist, auch wenn er nicht Ihren Anforderungen entspricht.</span><span class="sxs-lookup"><span data-stu-id="48536-121">Keep your coding style consistent with what already exists, even if it is not matching your preference.</span></span> <span data-ttu-id="48536-122">Dies erhöht die Lesbarkeit der gesamten Codebasis.</span><span class="sxs-lookup"><span data-stu-id="48536-122">This increases the readability of the overall codebase.</span></span>

### <a name="support-configuring-components-both-in-editor-and-at-run-time"></a><span data-ttu-id="48536-123">Unterstützung der Konfiguration von Komponenten sowohl im Editor als auch zur Laufzeit</span><span class="sxs-lookup"><span data-stu-id="48536-123">Support configuring components both in editor and at run-time</span></span>

<span data-ttu-id="48536-124">MRTK unterstützt eine Vielzahl von Benutzern: Personen, die Komponenten im Unity-Editor konfigurieren und Prefabs laden möchten, und Personen, die Objekte zur Laufzeit instanziieren und konfigurieren müssen.</span><span class="sxs-lookup"><span data-stu-id="48536-124">MRTK supports a diverse set of users – people who prefer to configure components in the Unity editor and load prefabs, and people who need to instantiate and configure objects at run-time.</span></span>

<span data-ttu-id="48536-125">Der gesamte Code sollte funktionieren, indem SOWOHL eine Komponente zu einem GameObject in einer gespeicherten Szene hinzugefügt als auch diese Komponente im Code instanziiert wird.</span><span class="sxs-lookup"><span data-stu-id="48536-125">All your code should work by BOTH adding a component to a GameObject in a saved scene, and by instantiating that component in code.</span></span> <span data-ttu-id="48536-126">Tests sollten einen Testfall sowohl zum Instanziieren von Prefabs als auch zum Instanziieren und Konfigurieren der Komponente zur Laufzeit enthalten.</span><span class="sxs-lookup"><span data-stu-id="48536-126">Tests should include a test case both for instantiating prefabs and instantiating, configuring the component at runtime.</span></span>

### <a name="play-in-editor-is-your-first-and-primary-target-platform"></a><span data-ttu-id="48536-127">Play-in-Editor ist Ihre erste und primäre Zielplattform.</span><span class="sxs-lookup"><span data-stu-id="48536-127">Play-in-editor is your first and primary target platform</span></span>

<span data-ttu-id="48536-128">Play-In-Editor ist die schnellste Möglichkeit zum Iterieren in Unity.</span><span class="sxs-lookup"><span data-stu-id="48536-128">Play-In-Editor is the fastest way to iterate in Unity.</span></span> <span data-ttu-id="48536-129">Die Bereitstellung von Möglichkeiten für unsere Kunden, schnell zu iterieren, ermöglicht es ihnen, Lösungen schneller zu entwickeln und weitere Ideen auszuprobieren.</span><span class="sxs-lookup"><span data-stu-id="48536-129">Providing ways for our customers to iterate quickly allows them to both develop solutions more quickly and try out more ideas.</span></span> <span data-ttu-id="48536-130">Mit anderen Worten: Die Maximierung der Iterationsgeschwindigkeit ermöglicht unseren Kunden, mehr zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="48536-130">In other words, maximizing the speed of iteration empowers our customers to achieve more.</span></span>

<span data-ttu-id="48536-131">Sorgen Sie dafür, dass alles im Editor funktioniert und dann auf jeder anderen Plattform funktioniert.</span><span class="sxs-lookup"><span data-stu-id="48536-131">Make everything work in editor, then make it work on any other platform.</span></span> <span data-ttu-id="48536-132">Arbeiten Sie weiterhin im Editor.</span><span class="sxs-lookup"><span data-stu-id="48536-132">Keep it working in the editor.</span></span> <span data-ttu-id="48536-133">Es ist einfach, play-in-editor eine neue Plattform hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="48536-133">It is easy to add a new platform to Play-In-Editor.</span></span> <span data-ttu-id="48536-134">Es ist sehr schwierig, play-in-editor funktionsfähig zu machen, wenn Ihre App nur auf einem Gerät funktioniert.</span><span class="sxs-lookup"><span data-stu-id="48536-134">It is very difficult to get Play-In-Editor working if your app only works on a device.</span></span>

### <a name="add-new-public-fields-properties-methods-and-serialized-private-fields-with-care"></a><span data-ttu-id="48536-135">Hinzufügen neuer öffentlicher Felder, Eigenschaften, Methoden und serialisierter privater Felder mit Vorsicht</span><span class="sxs-lookup"><span data-stu-id="48536-135">Add new public fields, properties, methods and serialized private fields with care</span></span>

<span data-ttu-id="48536-136">Jedes Mal, wenn Sie eine öffentliche Methode, ein Feld und eine Eigenschaft hinzufügen, wird sie Teil der öffentlichen API-Oberfläche des MRTK.</span><span class="sxs-lookup"><span data-stu-id="48536-136">Every time you add a public method, field, property, it becomes part of MRTK’s public API surface.</span></span> <span data-ttu-id="48536-137">Private Felder, die mit gekennzeichnet `[SerializeField]` sind, machen felder auch für den Editor verfügbar und sind Teil der öffentlichen API-Oberfläche.</span><span class="sxs-lookup"><span data-stu-id="48536-137">Private fields marked with `[SerializeField]` also expose fields to the editor and are part of the public API surface.</span></span> <span data-ttu-id="48536-138">Andere Personen können diese öffentliche Methode verwenden, benutzerdefinierte Prefabs mit Ihrem öffentlichen Feld konfigurieren und eine Abhängigkeit davon erstellen.</span><span class="sxs-lookup"><span data-stu-id="48536-138">Other people might use that public method, configure custom prefabs with your public field, and take a dependency on it.</span></span>

<span data-ttu-id="48536-139">Neue öffentliche Mitglieder sollten sorgfältig überprüft werden.</span><span class="sxs-lookup"><span data-stu-id="48536-139">New public members should be carefully examined.</span></span> <span data-ttu-id="48536-140">Jedes öffentliche Feld muss in Zukunft beibehalten werden.</span><span class="sxs-lookup"><span data-stu-id="48536-140">Any public field will need to be maintained in the future.</span></span> <span data-ttu-id="48536-141">Denken Sie daran: Wenn sich der Typ eines öffentlichen Felds (oder eines serialisierten privaten Felds) ändert oder aus einem MonoBehaviour entfernt wird, kann dies andere Personen unterbrechen.</span><span class="sxs-lookup"><span data-stu-id="48536-141">Remember that if the type of a public field (or serialized private field) changes or gets removed from a MonoBehaviour, that could break other people.</span></span> <span data-ttu-id="48536-142">Das Feld muss zunächst für ein Release veraltet sein, und Code zum Migrieren von Änderungen für Personen, die Abhängigkeiten übernommen haben, muss bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="48536-142">The field will need to first be deprecated for a release, and code to migrate changes for people that have taken dependencies would need to be provided.</span></span>

### <a name="prioritize-writing-tests"></a><span data-ttu-id="48536-143">Priorisieren des Schreibens von Tests</span><span class="sxs-lookup"><span data-stu-id="48536-143">Prioritize writing tests</span></span>

<span data-ttu-id="48536-144">MRTK ist ein Communityprojekt, das von einer Vielzahl von Mitwirkenden geändert wird.</span><span class="sxs-lookup"><span data-stu-id="48536-144">MRTK is a community project, modified by a diverse range of contributors.</span></span> <span data-ttu-id="48536-145">Diese Mitwirkenden kennen möglicherweise die Details Ihrer Fehlerbehebung/Ihres Features nicht und unterbricht versehentlich Ihr Feature.</span><span class="sxs-lookup"><span data-stu-id="48536-145">These contributors may not know the details of your bug fix / feature, and accidentally break your feature.</span></span> <span data-ttu-id="48536-146">[MRTK führt Continuous Integration-Tests aus,](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build?definitionId=16) bevor jeder Pull Request abgeschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="48536-146">[MRTK runs continuous integration tests](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build?definitionId=16) before completing every pull request.</span></span> <span data-ttu-id="48536-147">Änderungen, die Tests zum Einchecken unterbrechen, können nicht einchecken.</span><span class="sxs-lookup"><span data-stu-id="48536-147">Changes that break tests cannot be checked in.</span></span> <span data-ttu-id="48536-148">Daher sind Tests die beste Möglichkeit, um sicherzustellen, dass andere Personen Ihr Feature nicht unterbricht.</span><span class="sxs-lookup"><span data-stu-id="48536-148">Therefore, tests are the best way to ensure that other people do not break your feature.</span></span>

<span data-ttu-id="48536-149">Wenn Sie einen Fehler beheben, schreiben Sie einen Test, um sicherzustellen, dass er in Zukunft nicht zurück geht.</span><span class="sxs-lookup"><span data-stu-id="48536-149">When you fix a bug, write a test to ensure it does not regress in the future.</span></span> <span data-ttu-id="48536-150">Wenn Sie ein Feature hinzufügen, schreiben Sie Tests, die überprüfen, ob Ihr Feature funktioniert.</span><span class="sxs-lookup"><span data-stu-id="48536-150">If adding a feature, write tests that verify your feature works.</span></span> <span data-ttu-id="48536-151">Dies ist für alle UX-Features mit Ausnahme experimenteller Features erforderlich.</span><span class="sxs-lookup"><span data-stu-id="48536-151">This is required for all UX features except experimental features.</span></span>

## <a name="c-coding-conventions"></a><span data-ttu-id="48536-152">C#-Codierungskonventionen</span><span class="sxs-lookup"><span data-stu-id="48536-152">C# Coding conventions</span></span>

### <a name="script-license-information-headers"></a><span data-ttu-id="48536-153">Skriptlizenzinformationsheader</span><span class="sxs-lookup"><span data-stu-id="48536-153">Script license information headers</span></span>

<span data-ttu-id="48536-154">Alle Microsoft-Mitarbeiter, die neue Dateien beitragen, sollten den folgenden Standard-Lizenzheader am Anfang aller neuen Dateien hinzufügen, genau wie unten dargestellt:</span><span class="sxs-lookup"><span data-stu-id="48536-154">All Microsoft employees contributing new files should add the following standard License header at the top of any new files, exactly as shown below:</span></span>

```c#
// Copyright (c) Microsoft Corporation.
// Licensed under the MIT License.
```

### <a name="function--method-summary-headers"></a><span data-ttu-id="48536-155">Zusammenfassungsheader für Funktionen/Methoden</span><span class="sxs-lookup"><span data-stu-id="48536-155">Function / method summary headers</span></span>

<span data-ttu-id="48536-156">Alle öffentlichen Klassen, Strukturen, Enums, Funktionen, Eigenschaften und Felder, die im MRTK veröffentlicht werden, sollten genau wie unten dargestellt als Zweck und Verwendung beschrieben werden:</span><span class="sxs-lookup"><span data-stu-id="48536-156">All public classes, structs, enums, functions, properties, fields posted to the MRTK should be described as to its purpose and use, exactly as shown below:</span></span>

```c#
/// <summary>
/// The Controller definition defines the Controller as defined by the SDK / Unity.
/// </summary>
public struct Controller
{
    /// <summary>
    /// The ID assigned to the Controller
    /// </summary>
    public string ID;
}
```

<span data-ttu-id="48536-157">Dadurch wird sichergestellt, dass die Dokumentation für alle Klassen, Methoden und Eigenschaften ordnungsgemäß generiert und verbreitet wird.</span><span class="sxs-lookup"><span data-stu-id="48536-157">This ensures documentation is properly generated and disseminated for all all classes, methods, and properties.</span></span>

<span data-ttu-id="48536-158">Alle Skriptdateien, die ohne ordnungsgemäße Zusammenfassungstags übermittelt werden, werden abgelehnt.</span><span class="sxs-lookup"><span data-stu-id="48536-158">Any script files submitted without proper summary tags will be rejected.</span></span>

### <a name="mrtk-namespace-rules"></a><span data-ttu-id="48536-159">MRTK-Namespaceregeln</span><span class="sxs-lookup"><span data-stu-id="48536-159">MRTK namespace rules</span></span>

<span data-ttu-id="48536-160">Das Mixed Reality Toolkit verwendet ein featurebasiertes Namespacemodell, bei dem alle grundlegenden Namespaces mit "Microsoft.MixedReality.Toolkit" beginnen.</span><span class="sxs-lookup"><span data-stu-id="48536-160">The Mixed Reality Toolkit uses a feature based namespace model, where all foundational namespaces begin with "Microsoft.MixedReality.Toolkit".</span></span> <span data-ttu-id="48536-161">Im Allgemeinen müssen Sie die Toolkitebene (z. B. Kern, Anbieter, Dienste) nicht in Ihren Namespaces angeben.</span><span class="sxs-lookup"><span data-stu-id="48536-161">In general, you need not specify the toolkit layer (ex: Core, Providers, Services) in your namespaces.</span></span>

<span data-ttu-id="48536-162">Die derzeit definierten Namespaces sind:</span><span class="sxs-lookup"><span data-stu-id="48536-162">The currently defined namespaces are:</span></span>

- <span data-ttu-id="48536-163">Microsoft.MixedReality.Toolkit</span><span class="sxs-lookup"><span data-stu-id="48536-163">Microsoft.MixedReality.Toolkit</span></span>
- <span data-ttu-id="48536-164">Microsoft.MixedReality.Toolkit.Boundary</span><span class="sxs-lookup"><span data-stu-id="48536-164">Microsoft.MixedReality.Toolkit.Boundary</span></span>
- <span data-ttu-id="48536-165">Microsoft.MixedReality.Toolkit.Diagnostics</span><span class="sxs-lookup"><span data-stu-id="48536-165">Microsoft.MixedReality.Toolkit.Diagnostics</span></span>
- <span data-ttu-id="48536-166">Microsoft.MixedReality.Toolkit.Editor</span><span class="sxs-lookup"><span data-stu-id="48536-166">Microsoft.MixedReality.Toolkit.Editor</span></span>
- <span data-ttu-id="48536-167">Microsoft.MixedReality.Toolkit.Input</span><span class="sxs-lookup"><span data-stu-id="48536-167">Microsoft.MixedReality.Toolkit.Input</span></span>
- <span data-ttu-id="48536-168">Microsoft.MixedReality.Toolkit.SpatialAwareness</span><span class="sxs-lookup"><span data-stu-id="48536-168">Microsoft.MixedReality.Toolkit.SpatialAwareness</span></span>
- <span data-ttu-id="48536-169">Microsoft.MixedReality.Toolkit.Teleport</span><span class="sxs-lookup"><span data-stu-id="48536-169">Microsoft.MixedReality.Toolkit.Teleport</span></span>
- <span data-ttu-id="48536-170">Microsoft.MixedReality.Toolkit.Utilities</span><span class="sxs-lookup"><span data-stu-id="48536-170">Microsoft.MixedReality.Toolkit.Utilities</span></span>

<span data-ttu-id="48536-171">Für Namespaces mit einer großen Anzahl von Typen ist es akzeptabel, eine begrenzte Anzahl von Unternamespaces zu erstellen, um die Bereichsverwendung zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="48536-171">For namespaces with a large amount of types, it is acceptable to create a limited number of sub-namespaces to aid in scoping usage.</span></span>

<span data-ttu-id="48536-172">Wenn Sie den Namespace für eine Schnittstelle, klasse oder einen Datentyp weglassen, wird ihre Änderung blockiert.</span><span class="sxs-lookup"><span data-stu-id="48536-172">Omitting the namespace for an interface, class or data type will cause your change to be blocked.</span></span>

### <a name="adding-new-monobehaviour-scripts"></a><span data-ttu-id="48536-173">Hinzufügen neuer MonoBehaviour-Skripts</span><span class="sxs-lookup"><span data-stu-id="48536-173">Adding new MonoBehaviour scripts</span></span>

<span data-ttu-id="48536-174">Stellen Sie beim Hinzufügen neuer MonoBehaviour-Skripts mit einem Pull Request sicher, dass das [`AddComponentMenu`](https://docs.unity3d.com/ScriptReference/AddComponentMenu.html) -Attribut auf alle anwendbaren Dateien angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="48536-174">When adding new MonoBehaviour scripts with a pull request, ensure the [`AddComponentMenu`](https://docs.unity3d.com/ScriptReference/AddComponentMenu.html) attribute is applied to all applicable files.</span></span> <span data-ttu-id="48536-175">Dadurch wird sichergestellt, dass die Komponente im Editor unter der Schaltfläche *Komponente hinzufügen* leicht auffindbar ist.</span><span class="sxs-lookup"><span data-stu-id="48536-175">This ensures the component is easily discoverable in the editor under the *Add Component* button.</span></span> <span data-ttu-id="48536-176">Das Attributflag ist nicht erforderlich, wenn die Komponente nicht im Editor angezeigt werden kann, z. B. in einer abstrakten Klasse.</span><span class="sxs-lookup"><span data-stu-id="48536-176">The attribute flag is not necessary if the component cannot show up in editor such as an abstract class.</span></span>

<span data-ttu-id="48536-177">Im folgenden Beispiel sollte das *Paket hier* mit dem Paketspeicherort der Komponente gefüllt werden.</span><span class="sxs-lookup"><span data-stu-id="48536-177">In the example below, the *Package here* should be filled with the package location of the component.</span></span> <span data-ttu-id="48536-178">Wenn Sie ein Element im *MRTK-/SDK-Ordner* platzieren, ist das Paket *SDK*.</span><span class="sxs-lookup"><span data-stu-id="48536-178">If placing an item in *MRTK/SDK* folder, then the package will be *SDK*.</span></span>

```c#
[AddComponentMenu("Scripts/MRTK/{Package here}/MyNewComponent")]
public class MyNewComponent : MonoBehaviour
```

### <a name="adding-new-unity-inspector-scripts"></a><span data-ttu-id="48536-179">Hinzufügen neuer Unity-Inspektorskripts</span><span class="sxs-lookup"><span data-stu-id="48536-179">Adding new Unity inspector scripts</span></span>

<span data-ttu-id="48536-180">Versuchen Sie im Allgemeinen, das Erstellen von benutzerdefinierten Inspektorskripts für MRTK-Komponenten zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="48536-180">In general, try to avoid creating custom inspector scripts for MRTK components.</span></span> <span data-ttu-id="48536-181">Dies erhöht den Mehraufwand und die Verwaltung der Codebasis, die von der Unity-Engine verarbeitet werden kann.</span><span class="sxs-lookup"><span data-stu-id="48536-181">It adds additional overhead and management of the codebase that could be handled by the Unity engine.</span></span>

<span data-ttu-id="48536-182">Wenn eine Inspektorklasse erforderlich ist, versuchen Sie, unity zu [`DrawDefaultInspector()`](https://docs.unity3d.com/ScriptReference/Editor.DrawDefaultInspector.html) verwenden.</span><span class="sxs-lookup"><span data-stu-id="48536-182">If an inspector class is necessary, try to use Unity's [`DrawDefaultInspector()`](https://docs.unity3d.com/ScriptReference/Editor.DrawDefaultInspector.html).</span></span> <span data-ttu-id="48536-183">Dies vereinfacht erneut die Inspektorklasse und überlässt einen Großen Teil der Arbeit Unity.</span><span class="sxs-lookup"><span data-stu-id="48536-183">This again simplifies the inspector class and leaves much of the work to Unity.</span></span>

```c#
public override void OnInspectorGUI()
{
    // Do some custom calculations or checks
    // ....
    DrawDefaultInspector();
}
```

<span data-ttu-id="48536-184">Wenn benutzerdefiniertes Rendering in der Inspektorklasse erforderlich ist, versuchen Sie, und [`SerializedProperty`](https://docs.unity3d.com/ScriptReference/SerializedProperty.html) zu [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) verwenden.</span><span class="sxs-lookup"><span data-stu-id="48536-184">If custom rendering is required in the inspector class, try to utilize [`SerializedProperty`](https://docs.unity3d.com/ScriptReference/SerializedProperty.html) and [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html).</span></span> <span data-ttu-id="48536-185">Dadurch wird sichergestellt, dass Unity das Rendern geschachtelter Prefabs und geänderter Werte ordnungsgemäß verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="48536-185">This will ensure Unity correctly handles rendering nested prefabs and modified values.</span></span>

<span data-ttu-id="48536-186">Wenn aufgrund einer Anforderung in der benutzerdefinierten Logik nicht verwendet werden kann, stellen Sie [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) sicher, dass die verwendungsspezifische um eine umschlossen [`EditorGUI.PropertyScope`](https://docs.unity3d.com/ScriptReference/EditorGUI.PropertyScope.html) ist.</span><span class="sxs-lookup"><span data-stu-id="48536-186">If [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) cannot be used due to a requirement in custom logic, ensure all usage is wrapped around a [`EditorGUI.PropertyScope`](https://docs.unity3d.com/ScriptReference/EditorGUI.PropertyScope.html).</span></span> <span data-ttu-id="48536-187">Dadurch wird sichergestellt, dass Unity den Inspektor für geschachtelte Prefabs und geänderte Werte mit der angegebenen Eigenschaft ordnungsgemäß rendert.</span><span class="sxs-lookup"><span data-stu-id="48536-187">This will ensure Unity renders the inspector correctly for nested prefabs and modified values with the given property.</span></span>

<span data-ttu-id="48536-188">Versuchen Sie außerdem, die benutzerdefinierte Inspektorklasse mit einem zu [`CanEditMultipleObjects`](https://docs.unity3d.com/ScriptReference/CanEditMultipleObjects.html) verzieren.</span><span class="sxs-lookup"><span data-stu-id="48536-188">Furthermore, try to decorate the custom inspector class with a [`CanEditMultipleObjects`](https://docs.unity3d.com/ScriptReference/CanEditMultipleObjects.html).</span></span> <span data-ttu-id="48536-189">Dieses Tag stellt sicher, dass mehrere Objekte mit dieser Komponente in der Szene zusammen ausgewählt und geändert werden können.</span><span class="sxs-lookup"><span data-stu-id="48536-189">This tag ensure multiple objects with this component in the scene can be selected and modified together.</span></span> <span data-ttu-id="48536-190">Alle neuen Inspektorklassen sollten testen, ob ihr Code in dieser Situation in der Szene funktioniert.</span><span class="sxs-lookup"><span data-stu-id="48536-190">Any new inspector classes should test that their code works in this situation in the scene.</span></span>

```c#
    // Example inspector class demonstrating usage of SerializedProperty & EditorGUILayout.PropertyField
    // as well as use of EditorGUI.PropertyScope for custom property logic
    [CustomEditor(typeof(MyComponent))]
    public class MyComponentInspector : UnityEditor.Editor
    {
        private SerializedProperty myProperty;
        private SerializedProperty handedness;

        protected virtual void OnEnable()
        {
            myProperty = serializedObject.FindProperty("myProperty");
            handedness = serializedObject.FindProperty("handedness");
        }

        public override void OnInspectorGUI()
        {
            EditorGUILayout.PropertyField(destroyOnSourceLost);

            Rect position = EditorGUILayout.GetControlRect();
            var label = new GUIContent(handedness.displayName);
            using (new EditorGUI.PropertyScope(position, label, handedness))
            {
                var currentHandedness = (Handedness)handedness.enumValueIndex;

                handedness.enumValueIndex = (int)(Handedness)EditorGUI.EnumPopup(
                    position,
                    label,
                    currentHandedness,
                    (value) => {
                        // This function is executed by Unity to determine if a possible enum value
                        // is valid for selection in the editor view
                        // In this case, only Handedness.Left and Handedness.Right can be selected
                        return (Handedness)value == Handedness.Left
                        || (Handedness)value == Handedness.Right;
                    });
            }
        }
    }
```

### <a name="adding-new-scriptableobjects"></a><span data-ttu-id="48536-191">Hinzufügen neuer ScriptableObjects</span><span class="sxs-lookup"><span data-stu-id="48536-191">Adding new ScriptableObjects</span></span>

<span data-ttu-id="48536-192">Stellen Sie beim Hinzufügen neuer ScriptableObject-Skripts sicher, dass [`CreateAssetMenu`](https://docs.unity3d.com/ScriptReference/CreateAssetMenu.html) das -Attribut auf alle anwendbaren Dateien angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="48536-192">When adding new ScriptableObject scripts, ensure the [`CreateAssetMenu`](https://docs.unity3d.com/ScriptReference/CreateAssetMenu.html) attribute is applied to all applicable files.</span></span> <span data-ttu-id="48536-193">Dadurch wird sichergestellt, dass die Komponente im Editor über die Menüs zum Erstellen von Ressourcen leicht erkennbar ist.</span><span class="sxs-lookup"><span data-stu-id="48536-193">This ensures the component is easily discoverable in the editor via the asset creation menus.</span></span> <span data-ttu-id="48536-194">Das Attributflag ist nicht erforderlich, wenn die Komponente nicht im Editor wie einer abstrakten Klasse angezeigt werden kann.</span><span class="sxs-lookup"><span data-stu-id="48536-194">The attribute flag is not necessary if the component cannot show up in editor such as an abstract class.</span></span>

<span data-ttu-id="48536-195">Im folgenden Beispiel sollte der *Unterordner* ggf. mit dem MRTK-Unterordner gefüllt werden.</span><span class="sxs-lookup"><span data-stu-id="48536-195">In the example below, the *Subfolder* should be filled with the MRTK subfolder, if applicable.</span></span> <span data-ttu-id="48536-196">Wenn Sie ein Element im *MrTK/Providers-Ordner* platzieren, ist das Paket *Providers*.</span><span class="sxs-lookup"><span data-stu-id="48536-196">If placing an item in *MRTK/Providers* folder, then the package will be *Providers*.</span></span> <span data-ttu-id="48536-197">Wenn Sie ein Element im *MRTK/Core-Ordner* platzieren, legen Sie dies auf "Profile" fest.</span><span class="sxs-lookup"><span data-stu-id="48536-197">If placing an item in the *MRTK/Core* folder, set this to "Profiles".</span></span>

<span data-ttu-id="48536-198">Im folgenden Beispiel wird *myNewService | MyNewProvider* sollte ggf. mit dem Namen Ihrer neuen Klasse gefüllt werden.</span><span class="sxs-lookup"><span data-stu-id="48536-198">In the example below, the *MyNewService | MyNewProvider* should be filled with the your new class' name, if applicable.</span></span> <span data-ttu-id="48536-199">Wenn Sie ein Element im *Ordner MixedRealityToolkit* platzieren, lassen Sie diese Zeichenfolge weg.</span><span class="sxs-lookup"><span data-stu-id="48536-199">If placing an item in the *MixedRealityToolkit* folder, leave this string out.</span></span>

```c#
[CreateAssetMenu(fileName = "MyNewProfile", menuName = "Mixed Reality Toolkit/{Subfolder}/{MyNewService | MyNewProvider}/MyNewProfile")]
public class MyNewProfile : ScriptableObject
```

### <a name="logging"></a><span data-ttu-id="48536-200">Protokollierung</span><span class="sxs-lookup"><span data-stu-id="48536-200">Logging</span></span>

<span data-ttu-id="48536-201">Wenn Sie neue Features hinzufügen oder vorhandene Features aktualisieren, sollten Sie DebugUtilities.LogVerbose-Protokolle zu interessantem Code hinzufügen, der für zukünftiges Debuggen nützlich sein kann.</span><span class="sxs-lookup"><span data-stu-id="48536-201">When adding new features or updating existing features, consider adding DebugUtilities.LogVerbose logs to interesting code that may be useful for future debugging.</span></span> <span data-ttu-id="48536-202">Es gibt hier einen Kompromiss zwischen dem Hinzufügen der Protokollierung und dem zusätzlichen Rauschen und nicht genügend Protokollierung (was die Diagnose erschwert).</span><span class="sxs-lookup"><span data-stu-id="48536-202">There's a tradeoff here between adding logging and the added noise and not enough logging (which makes diagnosis difficult).</span></span>

<span data-ttu-id="48536-203">Ein interessantes Beispiel, bei dem die Protokollierung nützlich ist (zusammen mit einer interessanten Nutzlast):</span><span class="sxs-lookup"><span data-stu-id="48536-203">An interesting example where having logging is useful (along with interesting payload):</span></span>

```c#
DebugUtilities.LogVerboseFormat("RaiseSourceDetected: Source ID: {0}, Source Type: {1}", source.SourceId, source.SourceType);
```

<span data-ttu-id="48536-204">Diese Art der Protokollierung kann dabei helfen, Probleme wie [https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016) abzufangen, die durch nicht übereinstimmende ermittelte Quell- und Quellverlustereignisse verursacht wurden.</span><span class="sxs-lookup"><span data-stu-id="48536-204">This type of logging can help catch issues like [https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016), which were caused by mismatched source detected and source lost events.</span></span>

<span data-ttu-id="48536-205">Vermeiden Sie das Hinzufügen von Protokollen für Daten und Ereignisse, die in jedem Frame auftreten. Im Idealfall sollte die Protokollierung "interessante" Ereignisse abdecken, die durch unterschiedliche Benutzereingaben gesteuert werden (d. h. ein "Klick" durch einen Benutzer und der Satz von Änderungen und Ereignissen, die aus stammen, die für die Protokollierung interessant sind).</span><span class="sxs-lookup"><span data-stu-id="48536-205">Avoid adding logs for data and events that are occurring on every frame - ideally logging should cover "interesting" events driven by distinct user inputs (i.e. a "click" by a user and the set of changes and events that come from that are interesting to log).</span></span> <span data-ttu-id="48536-206">Der fortlaufende Zustand "Benutzer hält immer noch eine Geste" protokolliert jeder Frame ist nicht interessant und überfordert die Protokolle.</span><span class="sxs-lookup"><span data-stu-id="48536-206">The ongoing state of "user is still holding a gesture" logged every frame is not interesting and will overwhelm the logs.</span></span>

<span data-ttu-id="48536-207">Beachten Sie, dass diese ausführliche Protokollierung nicht standardmäßig aktiviert ist (sie muss in den Einstellungen des [Diagnosesystems](../features/diagnostics/configuring-diagnostics.md#enable-verbose-logging)aktiviert sein).</span><span class="sxs-lookup"><span data-stu-id="48536-207">Note that this verbose logging is not turned on by default (it must be enabled in the [Diagnostic System settings](../features/diagnostics/configuring-diagnostics.md#enable-verbose-logging))</span></span>

### <a name="spaces-vs-tabs"></a><span data-ttu-id="48536-208">Leerzeichen und Registerkarten</span><span class="sxs-lookup"><span data-stu-id="48536-208">Spaces vs tabs</span></span>

<span data-ttu-id="48536-209">Achten Sie darauf, dass Sie 4 Leerzeichen anstelle von Registerkarten verwenden, wenn Sie zu diesem Projekt beitragen.</span><span class="sxs-lookup"><span data-stu-id="48536-209">Please be sure to use 4 spaces instead of tabs when contributing to this project.</span></span>

### <a name="spacing"></a><span data-ttu-id="48536-210">Abstand</span><span class="sxs-lookup"><span data-stu-id="48536-210">Spacing</span></span>

<span data-ttu-id="48536-211">Fügen Sie keine zusätzlichen Leerzeichen zwischen eckigen Klammern und Klammern hinzu:</span><span class="sxs-lookup"><span data-stu-id="48536-211">Do not to add additional spaces between square brackets and parenthesis:</span></span>

#### <a name="dont"></a><span data-ttu-id="48536-212">Sie sollten auf keinen Fall</span><span class="sxs-lookup"><span data-stu-id="48536-212">Don't</span></span>

```c#
private Foo()
{
    int[ ] var = new int [ 9 ];
    Vector2 vector = new Vector2 ( 0f, 10f );
}

```

#### <a name="do"></a><span data-ttu-id="48536-213">Sie sollten</span><span class="sxs-lookup"><span data-stu-id="48536-213">Do</span></span>

```c#
private Foo()
{
    int[] var = new int[9];
    Vector2 vector = new Vector2(0f, 10f);
}
```

### <a name="naming-conventions"></a><span data-ttu-id="48536-214">Benennungskonventionen</span><span class="sxs-lookup"><span data-stu-id="48536-214">Naming conventions</span></span>

<span data-ttu-id="48536-215">Verwenden Sie immer `PascalCase` für Eigenschaften.</span><span class="sxs-lookup"><span data-stu-id="48536-215">Always use `PascalCase` for properties.</span></span> <span data-ttu-id="48536-216">Verwenden Sie `camelCase` für die meisten Felder, mit Ausnahme der `PascalCase` Felder und `static readonly` `const` .</span><span class="sxs-lookup"><span data-stu-id="48536-216">Use `camelCase` for most fields, except use `PascalCase` for `static readonly` and `const` fields.</span></span> <span data-ttu-id="48536-217">Die einzige Ausnahme hiervon ist für Datenstrukturen, die erfordern, dass die Felder von serialisiert `JsonUtility` werden.</span><span class="sxs-lookup"><span data-stu-id="48536-217">The only exception to this is for data structures that require the fields to be serialized by the `JsonUtility`.</span></span>

#### <a name="dont"></a><span data-ttu-id="48536-218">Sie sollten auf keinen Fall</span><span class="sxs-lookup"><span data-stu-id="48536-218">Don't</span></span>

```c#
public string myProperty; // <- Starts with a lowercase letter
private string MyField; // <- Starts with an uppercase letter
```

#### <a name="do"></a><span data-ttu-id="48536-219">Sie sollten</span><span class="sxs-lookup"><span data-stu-id="48536-219">Do</span></span>

```c#
public string MyProperty;
protected string MyProperty;
private static readonly string MyField;
private string myField;
```

### <a name="access-modifiers"></a><span data-ttu-id="48536-220">Zugriffsmodifizierer</span><span class="sxs-lookup"><span data-stu-id="48536-220">Access modifiers</span></span>

<span data-ttu-id="48536-221">Deklarieren Sie immer einen Zugriffsmodifizierer für alle Felder, Eigenschaften und Methoden.</span><span class="sxs-lookup"><span data-stu-id="48536-221">Always declare an access modifier for all fields, properties and methods.</span></span>

- <span data-ttu-id="48536-222">Alle Unity-API-Methoden sollten `private` standardmäßig sein, es sei denn, Sie müssen sie in einer abgeleiteten Klasse überschreiben.</span><span class="sxs-lookup"><span data-stu-id="48536-222">All Unity API Methods should be `private` by default, unless you need to override them in a derived class.</span></span> <span data-ttu-id="48536-223">In diesem Fall `protected` sollte verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="48536-223">In this case `protected` should be used.</span></span>

- <span data-ttu-id="48536-224">Felder sollten immer `private` , mit - oder `public` `protected` -Eigenschaftenaccessoren sein.</span><span class="sxs-lookup"><span data-stu-id="48536-224">Fields should always be `private`, with `public` or `protected` property accessors.</span></span>

- <span data-ttu-id="48536-225">Verwenden Von [Ausdruckskörpermembern](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#expression-bodied-function-members) und [automatischen Eigenschaften](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#auto-property-enhancements) nach Möglichkeit</span><span class="sxs-lookup"><span data-stu-id="48536-225">Use [expression-bodied members](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#expression-bodied-function-members) and [auto properties](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#auto-property-enhancements) where possible</span></span>

#### <a name="dont"></a><span data-ttu-id="48536-226">Sie sollten auf keinen Fall</span><span class="sxs-lookup"><span data-stu-id="48536-226">Don't</span></span>

```c#
// protected field should be private
protected int myVariable = 0;

// property should have protected setter
public int MyVariable => myVariable;

// No public / private access modifiers
void Foo() { }
void Bar() { }
```

#### <a name="do"></a><span data-ttu-id="48536-227">Sie sollten</span><span class="sxs-lookup"><span data-stu-id="48536-227">Do</span></span>

```c#
public int MyVariable { get; protected set; } = 0;

private void Foo() { }
public void Bar() { }
protected virtual void FooBar() { }
```

### <a name="use-braces"></a><span data-ttu-id="48536-228">Verwenden von geschweiften Klammern</span><span class="sxs-lookup"><span data-stu-id="48536-228">Use braces</span></span>

<span data-ttu-id="48536-229">Verwenden Sie nach jedem Anweisungsblock immer geschweifte Klammern, und platzieren Sie sie in der nächsten Zeile.</span><span class="sxs-lookup"><span data-stu-id="48536-229">Always use braces after each statement block, and place them on the next line.</span></span>

#### <a name="dont"></a><span data-ttu-id="48536-230">Nicht empfohlen</span><span class="sxs-lookup"><span data-stu-id="48536-230">Don't</span></span>

```c#
private Foo()
{
    if (Bar==null) // <- missing braces surrounding if action
        DoThing();
    else
        DoTheOtherThing();
}
```

#### <a name="dont"></a><span data-ttu-id="48536-231">Sie sollten auf keinen Fall</span><span class="sxs-lookup"><span data-stu-id="48536-231">Don't</span></span>

```c#
private Foo() { // <- Open bracket on same line
    if (Bar==null) DoThing(); <- if action on same line with no surrounding brackets
    else DoTheOtherThing();
}
```

#### <a name="do"></a><span data-ttu-id="48536-232">Sie sollten</span><span class="sxs-lookup"><span data-stu-id="48536-232">Do</span></span>

```c#
private Foo()
{
    if (Bar==true)
    {
        DoThing();
    }
    else
    {
        DoTheOtherThing();
    }
}
```

### <a name="public-classes-structs-and-enums-should-all-go-in-their-own-files"></a><span data-ttu-id="48536-233">Öffentliche Klassen, Strukturen und Enumerationen sollten alle in ihren eigenen Dateien gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="48536-233">Public classes, structs, and enums should all go in their own files</span></span>

<span data-ttu-id="48536-234">Wenn die Klasse, Struktur oder Enumeration privat gemacht werden kann, ist es in Ordnung, in derselben Datei enthalten zu sein.</span><span class="sxs-lookup"><span data-stu-id="48536-234">If the class, struct, or enum can be made private then it's okay to be included in the same file.</span></span>  <span data-ttu-id="48536-235">Dadurch werden Kompilierungsprobleme mit Unity vermieden, und es wird sichergestellt, dass eine ordnungsgemäße Codeabstraktion auftritt. Außerdem werden Konflikte und Breaking Changes reduziert, wenn Code geändert werden muss.</span><span class="sxs-lookup"><span data-stu-id="48536-235">This avoids compilations issues with Unity and ensure that proper code abstraction occurs, it also reduces conflicts and breaking changes when code needs to change.</span></span>

#### <a name="dont"></a><span data-ttu-id="48536-236">Sie sollten auf keinen Fall</span><span class="sxs-lookup"><span data-stu-id="48536-236">Don't</span></span>

```c#
public class MyClass
{
    public struct MyStruct() { }
    public enum MyEnumType() { }
    public class MyNestedClass() { }
}
```

#### <a name="do"></a><span data-ttu-id="48536-237">Sie sollten</span><span class="sxs-lookup"><span data-stu-id="48536-237">Do</span></span>

```c#
 // Private references for use inside the class only
public class MyClass
{
    private struct MyStruct() { }
    private enum MyEnumType() { }
    private class MyNestedClass() { }
}
```

#### <a name="do"></a><span data-ttu-id="48536-238">Empfohlen</span><span class="sxs-lookup"><span data-stu-id="48536-238">Do</span></span>

<span data-ttu-id="48536-239">MyStruct.cs</span><span class="sxs-lookup"><span data-stu-id="48536-239">MyStruct.cs</span></span>

```c#
// Public Struct / Enum definitions for use in your class.  Try to make them generic for reuse.
public struct MyStruct
{
    public string Var1;
    public string Var2;
}
```

<span data-ttu-id="48536-240">MyEnumType.cs</span><span class="sxs-lookup"><span data-stu-id="48536-240">MyEnumType.cs</span></span>

```c#
public enum MuEnumType
{
    Value1,
    Value2 // <- note, no "," on last value to denote end of list.
}
```

<span data-ttu-id="48536-241">MyClass.cs</span><span class="sxs-lookup"><span data-stu-id="48536-241">MyClass.cs</span></span>

```c#
public class MyClass
{
    private MyStruct myStructReference;
    private MyEnumType myEnumReference;
}
```

### <a name="initialize-enums"></a><span data-ttu-id="48536-242">Initialisieren von Enums</span><span class="sxs-lookup"><span data-stu-id="48536-242">Initialize enums</span></span>

<span data-ttu-id="48536-243">Um sicherzustellen, dass alle Aufumerungen ab 0 ordnungsgemäß initialisiert werden, bietet .NET Ihnen eine gute Verknüpfung, um die -Enum automatisch zu initialisieren, indem Sie einfach den ersten (Starter)-Wert hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="48536-243">To ensure all enums are initialized correctly starting at 0, .NET gives you a tidy shortcut to automatically initialize the enum by just adding the first (starter) value.</span></span> <span data-ttu-id="48536-244">(z.B. Wert 1 = 0 Verbleibende Werte sind nicht erforderlich)</span><span class="sxs-lookup"><span data-stu-id="48536-244">(e.g Value 1 = 0 Remaining values are not required)</span></span>

#### <a name="dont"></a><span data-ttu-id="48536-245">Sie sollten auf keinen Fall</span><span class="sxs-lookup"><span data-stu-id="48536-245">Don't</span></span>

```c#
public enum Value
{
    Value1, <- no initializer
    Value2,
    Value3
}
```

#### <a name="do"></a><span data-ttu-id="48536-246">Sie sollten</span><span class="sxs-lookup"><span data-stu-id="48536-246">Do</span></span>

```c#
public enum ValueType
{
    Value1 = 0,
    Value2,
    Value3
}
```

### <a name="order-enums-for-appropriate-extension"></a><span data-ttu-id="48536-247">Reihenfolge von Aufzählen für die entsprechende Erweiterung</span><span class="sxs-lookup"><span data-stu-id="48536-247">Order enums for appropriate extension</span></span>

<span data-ttu-id="48536-248">Es ist wichtig, dass, wenn eine Enum wahrscheinlich in Der Zukunft erweitert wird, um Standardwerte am Anfang der Enumerierung zu bestellen, dies sicherstellt, dass Enum-Indizes von neuen Ergänzungen nicht betroffen sind.</span><span class="sxs-lookup"><span data-stu-id="48536-248">It is critical that if an Enum is likely to be extended in the future, to order defaults at the top of the Enum, this ensures Enum indexes are not affected with new additions.</span></span>

#### <a name="dont"></a><span data-ttu-id="48536-249">Sie sollten auf keinen Fall</span><span class="sxs-lookup"><span data-stu-id="48536-249">Don't</span></span>

```c#
public enum SDKType
{
    WindowsMR,
    OpenVR,
    OpenXR,
    None, <- default value not at start
    Other <- anonymous value left to end of enum
}
```

#### <a name="do"></a><span data-ttu-id="48536-250">Sie sollten</span><span class="sxs-lookup"><span data-stu-id="48536-250">Do</span></span>

```c#
/// <summary>
/// The SDKType lists the VR SDKs that are supported by the MRTK
/// Initially, this lists proposed SDKs, not all may be implemented at this time (please see ReleaseNotes for more details)
/// </summary>
public enum SDKType
{
    /// <summary>
    /// No specified type or Standalone / non-VR type
    /// </summary>
    None = 0,
    /// <summary>
    /// Undefined SDK.
    /// </summary>
    Other,
    /// <summary>
    /// The Windows 10 Mixed reality SDK provided by the Universal Windows Platform (UWP), for Immersive MR headsets and HoloLens.
    /// </summary>
    WindowsMR,
    /// <summary>
    /// The OpenVR platform provided by Unity (does not support the downloadable SteamVR SDK).
    /// </summary>
    OpenVR,
    /// <summary>
    /// The OpenXR platform. SDK to be determined once released.
    /// </summary>
    OpenXR
}
```

### <a name="review-enum-use-for-bitfields"></a><span data-ttu-id="48536-251">Überprüfen der enum-Verwendung für Bitfelder</span><span class="sxs-lookup"><span data-stu-id="48536-251">Review enum use for bitfields</span></span>

<span data-ttu-id="48536-252">Wenn für eine -Enum mehrere Zustände als Wert erforderlich sind, z. B. "Handedness = Left & Right".</span><span class="sxs-lookup"><span data-stu-id="48536-252">If there is a possibility for an enum to require multiple states as a value, e.g. Handedness = Left & Right.</span></span> <span data-ttu-id="48536-253">Anschließend muss die Enum ordnungsgemäß mit BitFlags verziert werden, damit sie ordnungsgemäß verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="48536-253">Then the Enum needs to be decorated correctly with BitFlags to enable it to be used correctly</span></span>

<span data-ttu-id="48536-254">Die Datei "Handedness.cs" verfügt dafür über eine konkrete Implementierung.</span><span class="sxs-lookup"><span data-stu-id="48536-254">The Handedness.cs file has a concrete implementation for this</span></span>

### <a name="dont"></a><span data-ttu-id="48536-255">Sie sollten auf keinen Fall</span><span class="sxs-lookup"><span data-stu-id="48536-255">Don't</span></span>

```c#
public enum Handedness
{
    None,
    Left,
    Right
}
```

### <a name="do"></a><span data-ttu-id="48536-256">Sie sollten</span><span class="sxs-lookup"><span data-stu-id="48536-256">Do</span></span>

```c#
[Flags]
public enum Handedness
{
    None = 0 << 0,
    Left = 1 << 0,
    Right = 1 << 1,
    Both = Left | Right
}
```

### <a name="hard-coded-file-paths"></a><span data-ttu-id="48536-257">Hart codierte Dateipfade</span><span class="sxs-lookup"><span data-stu-id="48536-257">Hard-coded file paths</span></span>

<span data-ttu-id="48536-258">Gehen Sie beim Generieren von Zeichenfolgendateipfaden und insbesondere beim Schreiben hart codierter Zeichenfolgenpfade wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="48536-258">When generating string file paths, and in particular writing hard-coded string paths, do the following:</span></span>

1. <span data-ttu-id="48536-259">Verwenden Sie nach Möglichkeit [ `Path` C#-APIs](/dotnet/api/system.io.path?preserve-view=true&view=netframework-4.8) wie `Path.Combine` oder `Path.GetFullPath` .</span><span class="sxs-lookup"><span data-stu-id="48536-259">Use C#'s [`Path` APIs](/dotnet/api/system.io.path?preserve-view=true&view=netframework-4.8) whenever possible such as `Path.Combine` or `Path.GetFullPath`.</span></span>
1. <span data-ttu-id="48536-260">Verwenden Sie / oder [`Path.DirectorySeparatorChar`](/dotnet/api/system.io.path.directoryseparatorchar?preserve-view=true&view=netframework-4.8) anstelle von \ oder \\ \\ .</span><span class="sxs-lookup"><span data-stu-id="48536-260">Use / or [`Path.DirectorySeparatorChar`](/dotnet/api/system.io.path.directoryseparatorchar?preserve-view=true&view=netframework-4.8) instead of \ or \\\\.</span></span>

<span data-ttu-id="48536-261">Diese Schritte stellen sicher, dass MRTK sowohl auf Windows- als auch auf Unix-basierten Systemen funktioniert.</span><span class="sxs-lookup"><span data-stu-id="48536-261">These steps ensure that MRTK works on both Windows and Unix-based systems.</span></span>

### <a name="dont"></a><span data-ttu-id="48536-262">Sie sollten auf keinen Fall</span><span class="sxs-lookup"><span data-stu-id="48536-262">Don't</span></span>

```c#
private const string FilePath = "MyPath\\to\\a\\file.txt";
private const string OtherFilePath = "MyPath\to\a\file.txt";

string filePath = myVarRootPath + myRelativePath;
```

### <a name="do"></a><span data-ttu-id="48536-263">Sie sollten</span><span class="sxs-lookup"><span data-stu-id="48536-263">Do</span></span>

```c#
private const string FilePath = "MyPath/to/a/file.txt";
private const string OtherFilePath = "folder{Path.DirectorySeparatorChar}file.txt";

string filePath = Path.Combine(myVarRootPath,myRelativePath);

// Path.GetFullPath() will return the full length path of provided with correct system directory separators
string cleanedFilePath = Path.GetFullPath(unknownSourceFilePath);
```

## <a name="best-practices-including-unity-recommendations"></a><span data-ttu-id="48536-264">Bewährte Methoden, einschließlich Unity-Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="48536-264">Best practices, including Unity recommendations</span></span>

<span data-ttu-id="48536-265">Bei einigen Zielplattformen dieses Projekts muss die Leistung berücksichtigt werden.</span><span class="sxs-lookup"><span data-stu-id="48536-265">Some of the target platforms of this project require to take performance into consideration.</span></span> <span data-ttu-id="48536-266">Achten Sie vor diesem Hintergrund immer auf Vorsicht, wenn Sie Arbeitsspeicher in häufig aufgerufenem Code in engen Updateschleifen oder Algorithmen zuweisen.</span><span class="sxs-lookup"><span data-stu-id="48536-266">With this in mind always be careful when allocating memory in frequently called code in tight update loops or algorithms.</span></span>

### <a name="encapsulation"></a><span data-ttu-id="48536-267">Kapselung</span><span class="sxs-lookup"><span data-stu-id="48536-267">Encapsulation</span></span>

<span data-ttu-id="48536-268">Verwenden Sie immer private Felder und öffentliche Eigenschaften, wenn der Zugriff auf das Feld von außerhalb der Klasse oder Struktur benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="48536-268">Always use private fields and public properties if access to the field is needed from outside the class or struct.</span></span>  <span data-ttu-id="48536-269">Stellen Sie sicher, dass Sie das private Feld und die öffentliche Eigenschaft zusammenfinden.</span><span class="sxs-lookup"><span data-stu-id="48536-269">Be sure to co-locate the private field and the public property.</span></span> <span data-ttu-id="48536-270">Dadurch können Sie auf einen Blick leichter erkennen, was die Eigenschaft unterstützt und ob das Feld durch ein Skript geändert werden kann.</span><span class="sxs-lookup"><span data-stu-id="48536-270">This makes it easier to see, at a glance, what backs the property and that the field is modifiable by script.</span></span>

> [!NOTE]
> <span data-ttu-id="48536-271">Die einzige Ausnahme ist dies für Datenstrukturen, die erfordern, dass die Felder von serialisiert werden, wobei eine Datenklasse über alle öffentlichen Felder verfügen `JsonUtility` muss, damit die Serialisierung funktioniert.</span><span class="sxs-lookup"><span data-stu-id="48536-271">The only exception to this is for data structures that require the fields to be serialized by the `JsonUtility`, where a data class is required to have all public fields for the serialization to work.</span></span>

#### <a name="dont"></a><span data-ttu-id="48536-272">Sie sollten auf keinen Fall</span><span class="sxs-lookup"><span data-stu-id="48536-272">Don't</span></span>

```c#
private float myValue1;
private float myValue2;

public float MyValue1
{
    get{ return myValue1; }
    set{ myValue1 = value }
}

public float MyValue2
{
    get{ return myValue2; }
    set{ myValue2 = value }
}
```

#### <a name="do"></a><span data-ttu-id="48536-273">Sie sollten</span><span class="sxs-lookup"><span data-stu-id="48536-273">Do</span></span>

```c#
// Enable field to be configurable in the editor and available externally to other scripts (field is correctly serialized in Unity)
[SerializeField]
[ToolTip("If using a tooltip, the text should match the public property's summary documentation, if appropriate.")]
private float myValue; // <- Notice we co-located the backing field above our corresponding property.

/// <summary>
/// If using a tooltip, the text should match the public property's summary documentation, if appropriate.
/// </summary>
public float MyValue
{
    get => myValue;
    set => myValue = value;
}

/// <summary>
/// Getter/Setters not wrapping a value directly should contain documentation comments just as public functions would
/// </summary>
public float AbsMyValue
{
    get
    {
        if (MyValue < 0)
        {
            return -MyValue;
        }

        return MyValue
    }
}
```

### <a name="cache-values-and-serialize-them-in-the-sceneprefab-whenever-possible"></a><span data-ttu-id="48536-274">Zwischenspeichern von Werten und serialisieren sie nach Möglichkeit in der Szene/im Prefab</span><span class="sxs-lookup"><span data-stu-id="48536-274">Cache values and serialize them in the scene/prefab whenever possible</span></span>

<span data-ttu-id="48536-275">Unter Berücksichtigung von HoloLens empfiehlt es sich, die Leistung zu optimieren und Verweise in der Szene oder im Prefab zwischenzuspeichern, um die Speicherbelegung der Laufzeit einzuschränken.</span><span class="sxs-lookup"><span data-stu-id="48536-275">With the HoloLens in mind, it's best to optimize for performance and cache references in the scene or prefab to limit runtime memory allocations.</span></span>

#### <a name="dont"></a><span data-ttu-id="48536-276">Sie sollten auf keinen Fall</span><span class="sxs-lookup"><span data-stu-id="48536-276">Don't</span></span>

```c#
void Update()
{
    gameObject.GetComponent<Renderer>().Foo(Bar);
}
```

#### <a name="do"></a><span data-ttu-id="48536-277">Sie sollten</span><span class="sxs-lookup"><span data-stu-id="48536-277">Do</span></span>

```c#
[SerializeField] // To enable setting the reference in the inspector.
private Renderer myRenderer;

private void Awake()
{
    // If you didn't set it in the inspector, then we cache it on awake.
    if (myRenderer == null)
    {
        myRenderer = gameObject.GetComponent<Renderer>();
    }
}

private void Update()
{
    myRenderer.Foo(Bar);
}
```

### <a name="cache-references-to-materials-do-not-call-the-material-each-time"></a><span data-ttu-id="48536-278">Zwischenspeichern von Verweisen auf Materialien, nicht jedes Mal ".material" aufrufen</span><span class="sxs-lookup"><span data-stu-id="48536-278">Cache references to materials, do not call the ".material" each time</span></span>

<span data-ttu-id="48536-279">Unity erstellt jedes Mal, wenn Sie ".material" verwenden, ein neues Material, das zu einem Speicherverlust führt, wenn es nicht ordnungsgemäß bereinigt wird.</span><span class="sxs-lookup"><span data-stu-id="48536-279">Unity will create a new material each time you use ".material", which will cause a memory leak if not cleaned up properly.</span></span>

#### <a name="dont"></a><span data-ttu-id="48536-280">Sie sollten auf keinen Fall</span><span class="sxs-lookup"><span data-stu-id="48536-280">Don't</span></span>

```c#
public class MyClass
{
    void Update()
    {
        Material myMaterial = GetComponent<Renderer>().material;
        myMaterial.SetColor("_Color", Color.White);
    }
}
```

#### <a name="do"></a><span data-ttu-id="48536-281">Sie sollten</span><span class="sxs-lookup"><span data-stu-id="48536-281">Do</span></span>

```c#
// Private references for use inside the class only
public class MyClass
{
    private Material cachedMaterial;

    private void Awake()
    {
        cachedMaterial = GetComponent<Renderer>().material;
    }

    void Update()
    {
        cachedMaterial.SetColor("_Color", Color.White);
    }

    private void OnDestroy()
    {
        Destroy(cachedMaterial);
    }
}
```

> [!NOTE]
> <span data-ttu-id="48536-282">Verwenden Sie alternativ die Unity-Eigenschaft "SharedMaterial", die nicht jedes Mal, wenn darauf verwiesen wird, ein neues Material erstellt.</span><span class="sxs-lookup"><span data-stu-id="48536-282">Alternatively, use Unity's "SharedMaterial" property which does not create a new material each time it is referenced.</span></span>

### <a name="use-platform-dependent-compilation-to-ensure-the-toolkit-wont-break-the-build-on-another-platform"></a><span data-ttu-id="48536-283">Verwenden der [plattformabhängigen Kompilierung,](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) um sicherzustellen, dass das Toolkit den Build auf einer anderen Plattform nicht unterbricht</span><span class="sxs-lookup"><span data-stu-id="48536-283">Use [platform dependent compilation](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) to ensure the Toolkit won't break the build on another platform</span></span>

- <span data-ttu-id="48536-284">Verwenden Sie `WINDOWS_UWP` , um UWP-spezifische, nicht Unity-APIs zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="48536-284">Use `WINDOWS_UWP` in order to use UWP-specific, non-Unity APIs.</span></span> <span data-ttu-id="48536-285">Dadurch wird verhindert, dass sie versuchen, im Editor oder auf nicht unterstützten Plattformen auszuführen.</span><span class="sxs-lookup"><span data-stu-id="48536-285">This will prevent them from trying to run in the Editor or on unsupported platforms.</span></span> <span data-ttu-id="48536-286">Dies entspricht `UNITY_WSA && !UNITY_EDITOR` und sollte zugunsten von verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="48536-286">This is equivalent to `UNITY_WSA && !UNITY_EDITOR` and should be used in favor of.</span></span>
- <span data-ttu-id="48536-287">Verwenden Sie `UNITY_WSA` , um UWP-spezifische Unity-APIs wie den Namespace zu `UnityEngine.XR.WSA` verwenden.</span><span class="sxs-lookup"><span data-stu-id="48536-287">Use `UNITY_WSA` to use UWP-specific Unity APIs, such as the `UnityEngine.XR.WSA` namespace.</span></span> <span data-ttu-id="48536-288">Dies wird im Editor ausgeführt, wenn die Plattform auf UWP festgelegt ist, sowie in integrierten UWP-Apps.</span><span class="sxs-lookup"><span data-stu-id="48536-288">This will run in the Editor when the platform is set to UWP, as well as in built UWP apps.</span></span>

<span data-ttu-id="48536-289">Dieses Diagramm kann Ihnen bei der Entscheidung helfen, welche Sie `#if` verwenden möchten, abhängig von Ihren Anwendungsfällen und den erwarteten Buildeinstellungen.</span><span class="sxs-lookup"><span data-stu-id="48536-289">This chart can help you decide which `#if` to use, depending on your use cases and the build settings you expect.</span></span>

|<span data-ttu-id="48536-290">Plattform</span><span class="sxs-lookup"><span data-stu-id="48536-290">Platform</span></span> | <span data-ttu-id="48536-291">UWP IL2CPP</span><span class="sxs-lookup"><span data-stu-id="48536-291">UWP IL2CPP</span></span> | <span data-ttu-id="48536-292">UWP .NET</span><span class="sxs-lookup"><span data-stu-id="48536-292">UWP .NET</span></span> | <span data-ttu-id="48536-293">Editor</span><span class="sxs-lookup"><span data-stu-id="48536-293">Editor</span></span> |
| --- | --- | --- | --- |
| `UNITY_EDITOR` | <span data-ttu-id="48536-294">False</span><span class="sxs-lookup"><span data-stu-id="48536-294">False</span></span> | <span data-ttu-id="48536-295">False</span><span class="sxs-lookup"><span data-stu-id="48536-295">False</span></span> | <span data-ttu-id="48536-296">True</span><span class="sxs-lookup"><span data-stu-id="48536-296">True</span></span> |
| `UNITY_WSA` | <span data-ttu-id="48536-297">True</span><span class="sxs-lookup"><span data-stu-id="48536-297">True</span></span> | <span data-ttu-id="48536-298">True</span><span class="sxs-lookup"><span data-stu-id="48536-298">True</span></span> | <span data-ttu-id="48536-299">True</span><span class="sxs-lookup"><span data-stu-id="48536-299">True</span></span> |
| `WINDOWS_UWP` | <span data-ttu-id="48536-300">True</span><span class="sxs-lookup"><span data-stu-id="48536-300">True</span></span> | <span data-ttu-id="48536-301">True</span><span class="sxs-lookup"><span data-stu-id="48536-301">True</span></span> | <span data-ttu-id="48536-302">False</span><span class="sxs-lookup"><span data-stu-id="48536-302">False</span></span> |
| `UNITY_WSA && !UNITY_EDITOR` | <span data-ttu-id="48536-303">True</span><span class="sxs-lookup"><span data-stu-id="48536-303">True</span></span> | <span data-ttu-id="48536-304">True</span><span class="sxs-lookup"><span data-stu-id="48536-304">True</span></span> | <span data-ttu-id="48536-305">False</span><span class="sxs-lookup"><span data-stu-id="48536-305">False</span></span> |
| `ENABLE_WINMD_SUPPORT` | <span data-ttu-id="48536-306">True</span><span class="sxs-lookup"><span data-stu-id="48536-306">True</span></span> | <span data-ttu-id="48536-307">True</span><span class="sxs-lookup"><span data-stu-id="48536-307">True</span></span> | <span data-ttu-id="48536-308">False</span><span class="sxs-lookup"><span data-stu-id="48536-308">False</span></span> |
| `NETFX_CORE` | <span data-ttu-id="48536-309">False</span><span class="sxs-lookup"><span data-stu-id="48536-309">False</span></span> | <span data-ttu-id="48536-310">True</span><span class="sxs-lookup"><span data-stu-id="48536-310">True</span></span> | <span data-ttu-id="48536-311">False</span><span class="sxs-lookup"><span data-stu-id="48536-311">False</span></span> |

### <a name="prefer-datetimeutcnow-over-datetimenow"></a><span data-ttu-id="48536-312">"DateTime.UtcNow" gegenüber "DateTime.Now" bevorzugen</span><span class="sxs-lookup"><span data-stu-id="48536-312">Prefer DateTime.UtcNow over DateTime.Now</span></span>

<span data-ttu-id="48536-313">DateTime.UtcNow ist schneller als DateTime.Now.</span><span class="sxs-lookup"><span data-stu-id="48536-313">DateTime.UtcNow is faster than DateTime.Now.</span></span> <span data-ttu-id="48536-314">In vorherigen Leistungsuntersuchungen haben wir festgestellt, dass die Verwendung von DateTime.Now einen erheblichen Mehraufwand verursacht, insbesondere bei Verwendung in der Update()-Schleife.</span><span class="sxs-lookup"><span data-stu-id="48536-314">In previous performance investigations we've found that using DateTime.Now adds significant overhead especially when used in the Update() loop.</span></span> <span data-ttu-id="48536-315">[Andere haben das gleiche Problem.](https://stackoverflow.com/questions/1561791/optimizing-alternatives-to-datetime-now)</span><span class="sxs-lookup"><span data-stu-id="48536-315">[Others have hit the same issue](https://stackoverflow.com/questions/1561791/optimizing-alternatives-to-datetime-now).</span></span>

<span data-ttu-id="48536-316">Verwenden Sie DateTime.UtcNow, es sei denn, Sie benötigen tatsächlich die lokalisierten Zeiten (ein legitimer Grund kann sein, dass Sie die aktuelle Uhrzeit in der Zeitzone des Benutzers anzeigen möchten).</span><span class="sxs-lookup"><span data-stu-id="48536-316">Prefer using DateTime.UtcNow unless you actually need the localized times (a legitimate reason may be you wanting to show the current time in the user's time zone).</span></span> <span data-ttu-id="48536-317">Wenn Sie mit relativen Zeiten (d. h. dem Delta zwischen dem letzten Update und dem aktuellen Update) arbeiten, sollten Sie DateTime.UtcNow verwenden, um den Mehraufwand für Zeitzonenkonvertierungen zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="48536-317">If you are dealing with relative times (i.e. the delta between some last update and now), it's best to use DateTime.UtcNow to avoid the overhead of doing timezone conversions.</span></span>

## <a name="powershell-coding-conventions"></a><span data-ttu-id="48536-318">PowerShell-Codierungskonventionen</span><span class="sxs-lookup"><span data-stu-id="48536-318">PowerShell coding conventions</span></span>

<span data-ttu-id="48536-319">Eine Teilmenge der MRTK-Codebasis verwendet PowerShell für die Pipelineinfrastruktur und verschiedene Skripts und Hilfsprogramme.</span><span class="sxs-lookup"><span data-stu-id="48536-319">A subset of the MRTK codebase uses PowerShell for pipeline infrastructure and various scripts and utilities.</span></span> <span data-ttu-id="48536-320">Neuer PowerShell-Code sollte dem [PoshCode-Stil folgen.](https://poshcode.gitbooks.io/powershell-practice-and-style/)</span><span class="sxs-lookup"><span data-stu-id="48536-320">New PowerShell code should follow the [PoshCode style](https://poshcode.gitbooks.io/powershell-practice-and-style/).</span></span>

## <a name="see-also"></a><span data-ttu-id="48536-321">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="48536-321">See also</span></span>

 [<span data-ttu-id="48536-322">C#-Codierungskonventionen von MSDN</span><span class="sxs-lookup"><span data-stu-id="48536-322">C# coding conventions from MSDN</span></span>](/dotnet/csharp/programming-guide/inside-a-program/coding-conventions)