---
title: Grundlegendes zu Szenen
description: Erfahren Sie, wie Sie mit Szenenverständnis für HoloLens entwickeln, einschließlich SDK, Funktionen und gängigen Verwendungsszenarien.
author: szymons
ms.author: szymons
ms.date: 07/08/2019
ms.topic: article
keywords: Szenenverständnis, Räumliche Zuordnung, Windows Mixed Reality, Unity, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, Verdeckung, SDK
ms.openlocfilehash: 4dd5a2c96478e50b2e9eda35be22c15c1db07f88cfc4d25d753c4860a1283f55
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213466"
---
# <a name="scene-understanding"></a>Grundlegendes zu Szenen

Szenenverständnis bietet Mixed Reality-Entwicklern eine strukturierte, allgemeine Umgebungsdarstellung, die die Entwicklung für umgebungssensible Anwendungen intuitiv macht. Das Szenenverständnis kombiniert dazu die Leistungsfähigkeit vorhandener Mixed Reality-Runtimes, z. B. die äußerst genaue, aber weniger strukturierte [räumliche Zuordnung](spatial-mapping.md) und neue KI-gesteuerte Runtimes. Durch die Kombination dieser Technologien generiert Scene Understanding Darstellungen von 3D-Umgebungen, die denen ähneln, die Sie möglicherweise in Frameworks wie Unity oder ARKit/ARCore verwendet haben. Der Einstiegspunkt scene understanding beginnt mit einem Scene Observer, der von Ihrer Anwendung aufgerufen wird, um eine neue Szene zu berechnen. Heute kann die Technologie drei verschiedene, aber verwandte Objektkategorien generieren:

* Vereinfachte, wasserdichte Umgebungsgitternetze, die die planare Raumstruktur ohne Überladen ableiten
* Ebenenbereiche für die Platzierung, die wir Quads nennen
* Eine Momentaufnahme des [Raumzuordnungsgitters,](spatial-mapping.md) das an den quads/Watertight-Daten ausgerichtet ist, die wir auffüllen

![Gitternetz für räumliche Zuordnung, beschriftete planare Oberflächen, wasserdichtes Gitternetz](images/SUScenarios.png)

Dieses Dokument soll eine Szenarioübersicht bieten und die Beziehung verdeutlichen, die Szenenverständnis und räumliche Zuordnung teilen. Wenn Sie Scene Understanding in Aktion sehen möchten, sehen Sie sich unsere Videodemo **zum Entwerfen Hologramme – Räumliche Wahrnehmung** unten an:

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

*Dieses Video wurde aus der HoloLens 2-App „Entwerfen von Hologrammen“ aufgenommen. Laden Sie die vollständige Erfahrung [hier](https://aka.ms/dhapp) herunter, und genießen Sie sie.*

## <a name="developing-with-scene-understanding"></a>Entwickeln mit Scene Understanding

In diesem Artikel werden nur die Laufzeit und Konzepte von Scene Understanding vorgestellt. Wenn Sie nach Dokumentation zur Entwicklung mit Scene Understanding suchen, interessieren Sie sich möglicherweise für die folgenden Artikel:

[Übersicht über das Scene Understanding SDK](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)

Sie können die Scene Understanding-Beispiel-App von der Beispiel-GitHub-Website herunterladen:

[Scene Understanding-Beispiel](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

Wenn Sie kein Gerät haben und auf Beispielszenen zugreifen möchten, um Scene Understanding auszuprobieren, befinden sich Szenen im Beispielobjektordner:

[Scene Understanding-Beispielszenen](https://github.com/sceneunderstanding-microsoft/unitysample/tree/master/Assets/Resources/SerializedScenesForPCPath)

### <a name="sdk"></a>SDK

Wenn Sie nach spezifischen Details zur Entwicklung mit Scene Understanding suchen, lesen Sie die Übersichtsdokumentation zum [Scene Understanding SDK.](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)

### <a name="sample"></a>Beispiel

## <a name="device-support"></a>Geräteunterstützung

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Feature</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1. Generation)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
    </tr>
     <tr>
        <td>Grundlegendes zu Szenen</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="common-usage-scenarios"></a>Allgemeine Verwendungsszenarios

![Abbildungen allgemeiner Verwendungsszenarien für räumliche Zuordnungen: Platzierung, Verdeckung, Physik und Navigation](images/sm-concepts-1000px.png)<br>
*Allgemeine Verwendungsszenarien für räumliche Zuordnungen: Platzierung, Verdeckung, Physik und Navigation.*

<br>

Viele der Kernszenarien für fähige Anwendungen können sowohl durch räumliche Zuordnung als auch durch Szenenverständnis behandelt werden. Zu diesen Kernszenarien gehören Platzierung, Verdeckung, Physik usw. Ein Hauptunterschied zwischen Szenenverständnis und räumlicher Zuordnung ist ein Kompromiss zwischen maximaler Genauigkeit und Latenz gegenüber Struktur und Einfachheit. Wenn Ihre Anwendung die geringstmögliche Latenz und Gitterdreiecke erfordert, auf die nur Sie zugreifen möchten, verwenden Sie die räumliche Zuordnung direkt. Wenn Sie eine Verarbeitung auf höherer Ebene durchführen, können Sie erwägen, zum Scene Understanding-Modell zu wechseln, da es Ihnen eine Obermenge an Funktionen bieten sollte. Sie haben immer Zugriff auf die vollständigsten und präzisesten räumlichen Zuordnungsdaten, da Scene Understanding eine Momentaufnahme des Gitternetzes für räumliche Zuordnungen als Teil seiner Darstellung bereitstellt.

In den folgenden Abschnitten werden die wichtigsten Szenarien für die räumliche Zuordnung im Kontext des neuen Scene Understanding SDK erneut erläutert.

### <a name="placement"></a>Platzierung

Szenenverständnis bietet neue Konstrukte zur Vereinfachung von Platzierungsszenarien. Eine Szene kann Primitive mit dem Namen SceneQuads berechnen, die flache Oberflächen beschreiben, auf denen Hologramme platziert werden können. SceneQuads wurden für die Platzierung entworfen und beschreiben eine 2D-Oberfläche und stellen eine API für die Platzierung auf dieser Oberfläche bereit. Bei der Verwendung des Dreiecksgittermodells für die Platzierung mussten zuvor alle Bereiche des Quaders überprüft und Die Füllung/Nachbearbeitung von Löchern durchgeführt werden, um gute Positionen für die Objektplatzierung zu identifizieren. Dies ist bei Quads nicht immer erforderlich, da die Scene Understanding-Laufzeit hergeleitet wird, welche Quaderbereiche nicht gescannt wurden, und Bereiche ungültig macht, die nicht Teil der Oberfläche sind.

:::row:::
    :::column:::
       ![SceneQuads mit deaktivierter Rückschlusserfassung von Platzierungsbereichen für gescannte Regionen.](images/SUQuads.png)<br>
       **Bild #1:** SceneQuads mit deaktivierter Rückschlusserfassung von Platzierungsbereichen für gescannte Regionen.
    :::column-end:::
        :::column:::
       ![Quads mit aktiviertem Rückschluss, die Platzierung ist nicht mehr auf gescannte Bereiche beschränkt.](images/SUWatertight.png)<br>
        **Image #2:** Quads mit aktiviertem Rückschluss ist die Platzierung nicht mehr auf gescannte Bereiche beschränkt.
    :::column-end:::
:::row-end:::

<br>


Wenn Ihre Anwendung 2D- oder 3D-Hologramme auf festen Strukturen Ihrer Umgebung platzieren möchte, ist die Einfachheit und Einfachheit von SceneQuads für die Platzierung dem Berechnen dieser Informationen aus dem Gitternetz für [räumliche Zuordnungen](spatial-mapping.md) vorzuziehen. Weitere Informationen zu diesem Thema finden Sie in der Referenz zum [Scene Understanding SDK.](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)

**Hinweis** Für Legacyplatzierungscode, der vom Gitternetz für räumliche Zuordnungen abhängt, kann das Gitternetz für die räumliche Zuordnung zusammen mit SceneQuads berechnet werden, indem die Einstellung EnableWorldMesh festgelegt wird. Wenn die Scene Understanding-API die Latenzanforderungen Ihrer Anwendung nicht erfüllt, empfiehlt es sich, weiterhin die [API für räumliche Zuordnungen](spatial-mapping.md#placement)zu verwenden.

### <a name="occlusion"></a>Okklusion

[Die Verdeckung räumlicher Zuordnungen](spatial-mapping.md#occlusion) bleibt die am wenigsten latente Möglichkeit, den Echtzeitzustand der Umgebung zu erfassen. Obwohl dies nützlich sein kann, um Okklusion in hochgradig dynamischen Szenen bereitzustellen, sollten Sie das Szenenverständnis aus verschiedenen Gründen für Okklusion in Betracht ziehen. Wenn Sie das von Scene Understanding generierte Gitternetz für räumliche Zuordnungen verwenden, können Sie Daten von der räumlichen Zuordnung anfordern, die nicht im lokalen Cache gespeichert werden und nicht über die Perception-APIs verfügbar sind. Die Verwendung der räumlichen Zuordnung für die Verdeckung neben wasserdichten Gitternetzen bietet einen zusätzlichen Wert, insbesondere die Vervollständigung der nicht überprüften Raumstruktur.

Wenn Ihre Anforderungen die erhöhte Latenz des Szenenverständnisses tolerieren können, sollten Anwendungsentwickler erwägen, das gitterförmige Gitternetz scene understanding und das Gitternetz für räumliche Zuordnungen in Einklang mit planaren Darstellungen zu verwenden. Dies wäre ein "Best of Both Worlds"-Szenario, in dem eine vereinfachte, wasserdichte Verdeckung mit einer feineren nichtplanaren Geometrie zusammengestellt wird, die die realistischsten Verdeckungskarten bietet.

### <a name="physics"></a>Physische Effekte

Szenenverständnis generiert wasserdichte Gitternetze, die den Raum mit Semantik zerlegen, insbesondere um viele Einschränkungen der Physik zu berücksichtigen, die räumliche Zuordnungsgitternetze vorgeben. Wasserdichte Strukturen stellen sicher, dass physikalische Raycasts immer getroffen werden, und die semantische Zerlegung ermöglicht eine einfachere Generierung von Navigationsleisten für die Gebäudenavigation. Wie im Abschnitt zur [Verdeckung](#occlusion)beschrieben, erzeugt das Erstellen einer Szene mit EnableSceneObjectMeshes und EnableWorldMesh das physisch vollständigste Gitternetz. Die wasserdichte Eigenschaft des Umgebungsgitternetzes verhindert, dass Treffertests nicht auf Oberflächen treffen können. Die Gitternetzdaten stellen sicher, dass die Physik mit allen Objekten in der Szene und nicht nur mit der Raumstruktur interagiert.

### <a name="navigation"></a>Navigation

Planare Gitternetze, die durch eine semantische Klasse zerlegt werden, sind ideale Konstrukte für die Navigation und Pfadplanung, die viele der in der Übersicht über die Navigation der [räumlichen Zuordnung](spatial-mapping.md#navigation) beschriebenen Probleme erleichtern. Die in der Szene berechneten SceneMesh-Objekte werden nach Oberflächentyp dekomponiert, um sicherzustellen, dass die Navigationsgitternetzgenerierung auf Oberflächen beschränkt ist, die durchgehen können. Aufgrund der Einfachheit der Bodenstrukturen ist die dynamische Navigationsnetzgenerierung in 3D-Engines wie Unity je nach Echtzeitanforderungen erreichbar.

Das Generieren präziser Navigationsgitternetze erfordert derzeit noch eine Nachverarbeitung, d. h. Anwendungen müssen occluders immer noch auf den Boden prognostieren, um sicherzustellen, dass die Navigation nicht überladen/Tabellen durchgeht usw. Die genaueste Möglichkeit, dies zu erreichen, besteht darin, die weltweiten Gitternetzdaten zu projektieren, die bereitgestellt werden, wenn die Szene mit dem EnableWorldMesh-Flag berechnet wird.

### <a name="visualization"></a>Visualisierung

Die Visualisierung der [räumlichen Zuordnung](spatial-mapping.md#visualization) kann zwar für Echtzeitfeedback der Umgebung verwendet werden, es gibt jedoch viele Szenarien, in denen die Einfachheit planarer und wasserdichter Objekte eine größere Leistung oder visuelle Qualität bietet. Schattenprojektions- und Erdungstechniken, die mithilfe der räumlichen Zuordnung beschrieben werden, können ansprechender sein, wenn sie auf die planaren Oberflächen projiziert werden, die von Quads oder dem planaren wasserdichten Gitternetz bereitgestellt werden. Dies gilt insbesondere für Umgebungen/Szenarien, in denen eine gründliche Vorabüberprüfung nicht optimal ist, da die Szene rückschlüsset und vollständige Umgebungen und planare Annahmen Artefakte minimieren.

Darüber hinaus wird die Gesamtzahl der von der räumlichen Zuordnung zurückgegebenen Oberflächen durch den internen räumlichen Cache beschränkt, während die Scene Understanding-Version des Spatial Mapping-Gitters auf räumliche Zuordnungsdaten zugreifen kann, die nicht zwischengespeichert werden. Aus diesem Grund eignet sich scene understanding besser für die Erfassung von Gitternetzdarstellungen für größere Räume (z. B. größer als ein einzelner Raum) für die Visualisierung oder die weitere Gitternetzverarbeitung. Das mit EnableWorldMesh zurückgegebene Weltgittermodell hat durchgängig einen konsistenten Detailgrad, der zu einer ansprechenderen Visualisierung führen kann, wenn es als Wireframe gerendert wird.

### <a name="see-also"></a>Weitere Informationen

* [Scene understanding SDK](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)
* [Räumliche Abbildung](spatial-mapping.md)