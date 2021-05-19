---
title: Grundlegendes zu Szenen
description: Erfahren Sie, wie Sie mit Szenenverständnis für HoloLens entwickeln, einschließlich SDK, Funktionen und gängigen Verwendungsszenarien.
author: szymons
ms.author: szymons
ms.date: 07/08/2019
ms.topic: article
keywords: Szenenverständnis, räumliche Abbildung, Windows Mixed Reality, Unity, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, Okklusion, SDK
ms.openlocfilehash: 06a4fdb6f3ad777c47151950acbd4ccdec9935ca
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143593"
---
# <a name="scene-understanding"></a>Grundlegendes zu Szenen

Szenenverständnis bietet Mixed Reality Entwicklern eine strukturierte, umfassende Umgebungsdarstellung, die die Entwicklung für benutzerorientierte Anwendungen intuitiv macht. Das Szenenverständnis kombiniert dazu die Leistung der vorhandenen Mixed Reality-Runtimes, z. B. die hochgradig genaue, aber weniger strukturierte räumliche Zuordnung und neue KI-gesteuerte Runtimes. [](spatial-mapping.md) Durch die Kombination dieser Technologien generiert Scene Understanding Darstellungen von 3D-Umgebungen, die denen ähneln, die Sie möglicherweise in Frameworks wie Unity oder ARKit/ARCore verwendet haben. Der Einstiegspunkt "Szenenverständnis" beginnt mit einem Szenenbeobachter, der von Ihrer Anwendung aufgerufen wird, um eine neue Szene zu berechnen. Heute kann die Technologie drei unterschiedliche, aber verwandte Objektkategorien generieren:

* Vereinfachte Gitternetze für die wasserdichte Umgebung, die die planare Raumstruktur ohne Unübersichtlichkeit abgeleitet haben
* Ebenenregionen für die Platzierung, die wir Quads nennen
* Eine Momentaufnahme des [Gitters für](spatial-mapping.md) die räumliche Abbildung, die an den Quads-/Watertight-Daten ausgerichtet ist, die wir an die Oberfläche bringen.

![Gitternetz für räumliche Abbildung, beschriftete planare Oberflächen, wasserdichtes Gitternetz](images/SUScenarios.png)

Dieses Dokument soll eine Szenarioübersicht bereitstellen und die Beziehung verdeutlichen, die szenenbezogenes Verständnis und räumliche Zuordnung teilen. Wenn Sie Scene Understanding in Aktion sehen möchten, sehen Sie sich unsere Videodemo [Designing Holograms - Spatial Awareness]() (Entwerfen von Hologrammen – räumliche Wahrnehmung) weiter unten an:

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

## <a name="developing-with-scene-understanding"></a>Entwickeln mit Scene Understanding

Dieser Artikel dient nur zur Einführung in die Scene Understanding-Runtime und -Konzepte. Wenn Sie nach Dokumentation zur Entwicklung mit Scene Understanding suchen, sind möglicherweise die folgenden Artikel für Sie von Interesse:

[Übersicht über das Scene Understanding SDK](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)

Sie können die Scene Understanding-Beispiel-App von der GitHub-Beispielwebsite herunterladen:

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

Szenenverständnis bietet neue Konstrukte zur Vereinfachung von Platzierungsszenarien. Eine Szene kann Primitive mit dem Namen SceneQuads berechnen, die flache Oberflächen beschreiben, auf denen Hologramme platziert werden können. SceneQuads wurden für die Platzierung entworfen und beschreiben eine 2D-Oberfläche und stellen eine API für die Platzierung auf dieser Oberfläche bereit. Zuvor musste bei der Verwendung des Dreiecksgittermodells für die Platzierung alle Bereiche des Quaderbereichs gescannt und Füll- bzw. Nachbearbeitungsvorgänge durchführen, um gute Positionen für die Objektplatzierung zu identifizieren. Dies ist bei Quads nicht immer erforderlich, da die Scene Understanding Runtime daraus abgeleitet wird, welche Viererbereiche nicht gescannt wurden, und Bereiche ungültig machen, die nicht Teil der Oberfläche sind.

:::row:::
    :::column:::
       ![SceneQuads mit deaktivierten Rückschlüssen, die Platzierungsbereiche für gescannte Bereiche erfassen.](images/SUQuads.png)<br>
       **Image #1:** SceneQuads mit deaktivierten Rückschlüssen, die Platzierungsbereiche für gescannte Regionen erfassen.
    :::column-end:::
        :::column:::
       ![Quads mit aktiviertem Rückschluss, die Platzierung ist nicht mehr auf gescannte Bereiche beschränkt.](images/SUWatertight.png)<br>
        **Bild #2:** Quads mit aktiviertem Rückschluss, die Platzierung ist nicht mehr auf gescannte Bereiche beschränkt.
    :::column-end:::
:::row-end:::

<br>


Wenn Ihre Anwendung beabsichtigt, 2D- oder 3D-Hologramme auf festen Strukturen Ihrer Umgebung zu platzieren, ist die Einfachheit [](spatial-mapping.md) und Benutzerfreundlichkeit von SceneQuads für die Platzierung dem Berechnen dieser Informationen aus dem Gitternetz der räumlichen Zuordnung vorzuziehen. Weitere Informationen zu diesem Thema finden Sie in der [Scene Understanding SDK-Referenz.](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)

**Hinweis:** Für Legacyplatzierungscode, der vom Gitternetz der räumlichen Zuordnung abhängt, kann das Gitternetz für räumliche Zuordnung zusammen mit SceneQuads berechnet werden, indem die Einstellung EnableWorldMesh aktiviert wird. Wenn die Scene Understanding-API die Latenzanforderungen Ihrer Anwendung nicht erfüllt, empfehlen wir Ihnen, weiterhin die API für räumliche [Zuordnung zu verwenden.](spatial-mapping.md#placement)

### <a name="occlusion"></a>Okklusion

[Die Verdecken der räumlichen Zuordnung bleibt](spatial-mapping.md#occlusion) die am wenigsten latente Möglichkeit, den Echtzeitzustand der Umgebung zu erfassen. Obwohl dies nützlich sein kann, um die Verdecken in sehr dynamischen Szenen zu ermöglichen, sollten Sie scene understanding for occlusion aus verschiedenen Gründen in Betracht ziehen. Wenn Sie das von Scene Understanding generierte Gitternetz für die räumliche Zuordnung verwenden, können Sie Daten aus der räumlichen Zuordnung anfordern, die nicht im lokalen Cache gespeichert werden und nicht über die Wahrnehmungs-APIs verfügbar sind. Die Verwendung der räumlichen Zuordnung für okklusion neben wasserdichten Gittern bietet zusätzlichen Nutzen, insbesondere die Vervollständigung der nicht gekannten Raumstruktur.

Wenn Ihre Anforderungen die erhöhte Latenz des Szenenverständnisses tolerieren können, sollten Anwendungsentwickler erwägen, das gitterförmige Gitternetz scene understanding und das Gitternetz für räumliche Zuordnungen in Einklang mit planaren Darstellungen zu verwenden. Dies wäre ein "Best of Both Worlds"-Szenario, in dem eine vereinfachte, wasserdichte Verdeckung mit einer feineren nichtplanaren Geometrie zusammengestellt wird, die die realistischsten Verdeckungskarten bietet.

### <a name="physics"></a>Physische Effekte

Szenenverständnis generiert wasserdichte Gitternetze, die den Raum mit Semantik zerlegen, insbesondere um viele Einschränkungen der Physik zu berücksichtigen, die räumliche Zuordnungsgitternetze vorgeben. Wasserdichte Strukturen stellen sicher, dass physikalische Raycasts immer getroffen werden, und die semantische Zerlegung ermöglicht eine einfachere Generierung von Navigationsleisten für die Gebäudenavigation. Wie im Abschnitt zur [Verdeckung](#occlusion)beschrieben, erzeugt das Erstellen einer Szene mit EnableSceneObjectMeshes und EnableWorldMesh das physisch vollständigste Gitternetz. Die wasserdichte Eigenschaft des Umgebungsgitternetzes verhindert, dass Treffertests nicht auf Oberflächen treffen können. Die Gitternetzdaten stellen sicher, dass die Physik mit allen Objekten in der Szene und nicht nur mit der Raumstruktur interagiert.

### <a name="navigation"></a>Navigation

Planare Gitternetze, die durch eine semantische Klasse zerlegt werden, sind ideale Konstrukte für die Navigation und Pfadplanung, die viele der in der Übersicht über die Navigation der [räumlichen Zuordnung](spatial-mapping.md#navigation) beschriebenen Probleme erleichtern. Die in der Szene berechneten SceneMesh-Objekte werden nach Oberflächentyp dekomponiert, um sicherzustellen, dass die Navigationsgitternetzgenerierung auf Oberflächen beschränkt ist, die durchgehen können. Aufgrund der Einfachheit der Bodenstrukturen ist die dynamische Navigationsnetzgenerierung in 3D-Engines wie Unity je nach Echtzeitanforderungen erreichbar.

Das Generieren präziser Navigationsgitternetze erfordert derzeit noch eine Nachverarbeitung, d. h. Anwendungen müssen occluders immer noch auf den Boden prognostieren, um sicherzustellen, dass die Navigation nicht überladen/Tabellen durchgeht usw. Die genaueste Möglichkeit, dies zu erreichen, besteht darin, die weltweiten Gitternetzdaten zu projektieren, die bereitgestellt werden, wenn die Szene mit dem EnableWorldMesh-Flag berechnet wird.

### <a name="visualization"></a>Visualisierung

Die Visualisierung der [räumlichen Zuordnung](spatial-mapping.md#visualization) kann zwar für Echtzeitfeedback der Umgebung verwendet werden, es gibt jedoch viele Szenarien, in denen die Einfachheit planarer und wasserdichter Objekte eine größere Leistung oder visuelle Qualität bietet. Schattenprojektions- und Erdungstechniken, die mithilfe der räumlichen Zuordnung beschrieben werden, können ansprechender sein, wenn sie auf die planaren Oberflächen projiziert werden, die von Quads oder dem planaren, wasserdichten Gitternetz bereitgestellt werden. Dies gilt insbesondere für Umgebungen/Szenarien, in denen eine gründliche Vorabüberprüfung nicht optimal ist, da die Szene rückschlüsset und vollständige Umgebungen und planare Annahmen Artefakte minimieren.

Darüber hinaus wird die Gesamtzahl der von der räumlichen Zuordnung zurückgegebenen Oberflächen durch den internen räumlichen Cache beschränkt, während die Scene Understanding-Version des Spatial Mapping-Gitters auf räumliche Zuordnungsdaten zugreifen kann, die nicht zwischengespeichert werden. Aus diesem Grund eignet sich Scene Understanding besser für die Erfassung von Gitternetzdarstellungen für größere Räume (z. B. größer als ein einzelner Raum) für die Visualisierung oder die weitere Gitternetzverarbeitung. Das mit EnableWorldMesh zurückgegebene Weltgittermodell hat durchgängig einen konsistenten Detailgrad, der zu einer ansprechenderen Visualisierung führen kann, wenn es als Wireframe gerendert wird.

### <a name="see-also"></a>Weitere Informationen

* [Scene understanding SDK](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)
* [Räumliche Abbildung](spatial-mapping.md)