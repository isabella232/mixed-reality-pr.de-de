---
title: Grundlegendes zu Szenen
description: Erfahren Sie, wie Sie mit Szenenverständnis für HoloLens entwickeln, einschließlich SDK, Funktionen und gängigen Verwendungsszenarien.
author: szymons
ms.author: szymons
ms.date: 07/08/2019
ms.topic: article
keywords: Szenenverständnis, Räumliche Abbildung, Windows Mixed Reality, Unity, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, Okklusion, SDK
ms.openlocfilehash: 6d950fca4211aef659b1f957ca5e7135ac9764ac
ms.sourcegitcommit: 6b8ccb881fbbdaa5119841eac528e29d7b49bd04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/07/2021
ms.locfileid: "123557319"
---
# <a name="scene-understanding"></a>Grundlegendes zu Szenen

Szenenverständnis bietet Mixed Reality-Entwicklern eine strukturierte, allgemeine Umgebungsdarstellung, die die Entwicklung für umgebungssensible Anwendungen intuitiv macht. Das Szenenverständnis kombiniert dazu die Leistung der vorhandenen Mixed Reality-Runtimes, z. B. die hochgradig genaue, aber weniger strukturierte räumliche Zuordnung und neue KI-gesteuerte Runtimes. [](spatial-mapping.md) Durch die Kombination dieser Technologien generiert Scene Understanding Darstellungen von 3D-Umgebungen, die denen ähneln, die Sie möglicherweise in Frameworks wie Unity oder ARKit/ARCore verwendet haben. Der Einstiegspunkt "Szenenverständnis" beginnt mit einem Szenenbeobachter, der von Ihrer Anwendung aufgerufen wird, um eine neue Szene zu berechnen. Heute kann die Technologie drei unterschiedliche, aber verwandte Objektkategorien generieren:

* Vereinfachte Gitternetze für die wasserdichte Umgebung, die die planare Raumstruktur ohne Unübersichtlichkeit abgeleitet haben
* Ebenenregionen für die Platzierung, die wir Quads nennen
* Eine Momentaufnahme des [Gitters für](spatial-mapping.md) die räumliche Abbildung, die an den Quads-/Watertight-Daten ausgerichtet ist, die wir an die Oberfläche bringen.

![Gitternetz für räumliche Abbildung, planare Oberflächen mit Bezeichnung, wasserdichtes Gitternetz](images/SUScenarios.png)

Dieses Dokument soll eine Szenarioübersicht bieten und die Beziehung verdeutlichen, die szenenbezogenes Verständnis und räumliche Zuordnung gemeinsam verwenden. Wenn Sie Scene Understanding in Aktion sehen möchten, sehen Sie sich unten unsere Videodemo **Designing Hologramme – Spatial Awareness** an:

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

*Dieses Video wurde aus der HoloLens 2-App „Entwerfen von Hologrammen“ aufgenommen. Laden Sie die vollständige Erfahrung [hier](https://aka.ms/dhapp) herunter, und genießen Sie sie.*

## <a name="developing-with-scene-understanding"></a>Entwickeln mit Scene Understanding

In diesem Artikel werden nur die Scene Understanding-Runtime und -Konzepte beschrieben. Wenn Sie nach Dokumentation zur Entwicklung mit Scene Understanding suchen, sind möglicherweise die folgenden Artikel für Sie von Interesse:

[Übersicht über das Scene Understanding SDK](../develop/unity/scene-understanding-SDK.md)

Sie können die Scene Understanding-Beispiel-App von der Beispielwebsite GitHub herunterladen:

[Scene Understanding-Beispiel](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

Wenn Sie nicht über ein Gerät verfügen und auf Beispielszenen zugreifen möchten, um Scene Understanding auszuprobieren, finden Sie Szenen im Ordner "Sample Asset":

[Szenenverständnis von Beispielszenen](https://github.com/sceneunderstanding-microsoft/unitysample/tree/master/Assets/Resources/SerializedScenesForPCPath)

### <a name="sdk"></a>SDK

Wenn Sie nach spezifischen Details zur Entwicklung mit Scene Understanding suchen, lesen Sie die [Übersichtsdokumentation zum Scene Understanding SDK.](../develop/unity/scene-understanding-SDK.md)

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

![Abbildungen gängiger Szenarien zur Räumlichen Zuordnung: Platzierung, Okklusion, Physik und Navigation](images/sm-concepts-1000px.png)<br>
*Gängige Verwendungsszenarien für die räumliche Zuordnung: Platzierung, Okklusion, Physik und Navigation.*

<br>

Viele der Kernszenarien für unterschiedliche Anwendungen können sowohl durch räumliche Zuordnung als auch durch Szenenverständnis behandelt werden. Zu diesen Kernszenarien gehören Platzierung, Okklusion, Physik und so weiter. Ein Hauptunterschied zwischen Szenenverständnis und räumlicher Zuordnung ist ein Kompromiss zwischen maximaler Genauigkeit und Latenz in Bezug auf Struktur und Einfachheit. Wenn Ihre Anwendung die geringstmögliche Latenz und Gitterdreiecke erfordert, auf die nur Sie zugreifen möchten, verwenden Sie spatial mapping direkt. Wenn Sie eine Verarbeitung auf höherer Ebene verwenden, können Sie in Betracht ziehen, zum Scene Understanding-Modell zu wechseln, da es Ihnen eine obere Reihe von Funktionen bieten sollte. Sie haben immer Zugriff auf die vollständigsten und genauesten räumlichen Kartendaten, da Scene Understanding eine Momentaufnahme des Gitters für die räumliche Abbildung als Teil seiner Darstellung bietet.

In den folgenden Abschnitten werden die wichtigsten Szenarien der räumlichen Zuordnung im Kontext des neuen Scene Understanding SDK erneut erläutert.

### <a name="placement"></a>Platzierung

Das Szenenverständnis stellt neue Konstrukte zur Vereinfachung von Platzierungsszenarien zur Verfügung. Eine Szene kann Primitive namens SceneQuads berechnen, die flache Oberflächen beschreiben, auf denen Hologramme platziert werden können. SceneQuads wurden für die Platzierung entworfen und beschreiben eine 2D-Oberfläche und stellen eine API für die Platzierung auf dieser Oberfläche bereit. Zuvor mussten sie bei der Verwendung des Dreiecksgittermodells für die Platzierung alle Bereiche des Quaderbereichs scannen und Füll- bzw. Nachbearbeitungsvorgänge durchführen, um gute Positionen für die Objektplatzierung zu identifizieren. Dies ist bei Quads nicht immer erforderlich, da die Scene Understanding Runtime daraus abgeleitet wird, welche Viererbereiche nicht gescannt wurden, und Bereiche ungültig macht, die nicht Teil der Oberfläche sind.

:::row:::
    :::column:::
       ![SceneQuads mit deaktivierten Rückschlüssen, die Platzierungsbereiche für gescannte Bereiche erfassen.](images/SUQuads.png)<br>
       **Bild #1:** SceneQuads mit deaktivierten Rückschlüssen, die Platzierungsbereiche für gescannte Regionen erfassen.
    :::column-end:::
        :::column:::
       ![Quads mit aktiviertem Rückschluss, die Platzierung ist nicht mehr auf gescannte Bereiche beschränkt.](images/SUWatertight.png)<br>
        **Image #2:** Quads mit aktiviertem Rückschluss, die Platzierung ist nicht mehr auf gescannte Bereiche beschränkt.
    :::column-end:::
:::row-end:::

<br>


Wenn Ihre Anwendung beabsichtigt, 2D- oder 3D-Hologramme auf festen Strukturen Ihrer Umgebung zu platzieren, ist die Einfachheit [](spatial-mapping.md) und Benutzerfreundlichkeit von SceneQuads für die Platzierung dem Berechnen dieser Informationen aus dem Gitternetz der räumlichen Abbildung vorzuziehen. Weitere Informationen zu diesem Thema finden Sie in der [Scene Understanding SDK-Referenz.](../develop/unity/scene-understanding-SDK.md)

**Hinweis:** Für Legacyplatzierungscode, der vom Gitternetz der räumlichen Zuordnung abhängt, kann das Gitternetz für räumliche Karten zusammen mit SceneQuads berechnet werden, indem die Einstellung EnableWorldMesh aktiviert wird. Wenn die Scene Understanding-API die Latenzanforderungen Ihrer Anwendung nicht erfüllt, empfehlen wir Ihnen, weiterhin die API für räumliche [Zuordnung zu verwenden.](spatial-mapping.md#placement)

### <a name="occlusion"></a>Okklusion

[Die Verdecken der räumlichen Zuordnung bleibt](spatial-mapping.md#occlusion) die am wenigsten latente Möglichkeit, den Echtzeitzustand der Umgebung zu erfassen. Obwohl dies nützlich sein kann, um die Verdecken in sehr dynamischen Szenen zu ermöglichen, sollten Sie scene understanding for occlusion aus verschiedenen Gründen in Betracht ziehen. Wenn Sie das von Scene Understanding generierte Gitternetz für die räumliche Zuordnung verwenden, können Sie Daten aus der räumlichen Zuordnung anfordern, die nicht im lokalen Cache gespeichert werden und nicht über die Wahrnehmungs-APIs verfügbar sind. Die Verwendung der räumlichen Zuordnung für okklusion neben wasserdichten Gittern bietet zusätzlichen Nutzen, insbesondere die Vervollständigung einer nicht gekannten Raumstruktur.

Wenn Ihre Anforderungen die erhöhte Latenz des Szenenverständnisses tolerieren können, sollten Anwendungsentwickler erwägen, das Watertight-Gitternetz für Szenenverständnis und das Gitternetz für die räumliche Abbildung in Einklang mit planaren Darstellungen zu verwenden. Dies würde ein Szenario mit dem "Besten aus beiden Welten" bieten, bei dem eine vereinfachte verdeckende Wasserdichte mit einer feineren nichtplanaren Geometrie zur Verfügung steht, die die realistischsten Verdeckungszuordnungen ermöglicht.

### <a name="physics"></a>Physische Effekte

Das Szenenverständnis generiert wasserdichte Gitternetze, die den Raum mit Semantik zersetzen, insbesondere um viele Einschränkungen der Physik zu adressieren, die Gittermodells für räumliche Zuordnungen erzwingt. Wasserdichte Strukturen stellen sicher, dass physikalische Raycasts immer getroffen werden, und die semantische Zerlegung ermöglicht eine einfachere Generierung von Navigationsgittern für die Gebäudenavigation. Wie im Abschnitt zur [Okklusion](#occlusion)beschrieben, erzeugt das Erstellen einer Szene mit EnableSceneObjectMeshes und EnableWorldMesh das physisch vollständigste Gitternetz. Die watertight-Eigenschaft des Umgebungsgitters verhindert, dass Treffertests nicht auf Oberflächen treffen. Die Gitternetzdaten stellen sicher, dass die Physik mit allen Objekten in der Szene und nicht nur mit der Raumstruktur interagiert.

### <a name="navigation"></a>Navigation

Planare Gitternetze, die durch semantische Klassen zersetzt sind, sind ideale Konstrukte für die Navigations- und Pfadplanung und erleichtern viele der Probleme, die in der Übersicht über die Navigation der räumlichen [Zuordnung beschrieben](spatial-mapping.md#navigation) werden. Die in der Szene berechneten SceneMesh-Objekte werden durch den Oberflächentyp destrukturiert, um sicherzustellen, dass die Generierung des Navigationsgitters auf Oberflächen beschränkt ist, auf denen ein Walking möglich ist. Aufgrund der Einfachheit der Bodenstrukturen ist die dynamische Navigationsleistengenerierung in 3D-Engines wie Unity je nach Echtzeitanforderungen erreichbar.

Das Generieren genauer Navigationsgitternetze erfordert derzeit noch eine Nachverarbeitung, d. h., Anwendungen müssen weiterhin Okcluder auf den Boden pro probieren, um sicherzustellen, dass die Navigation nicht durch unübersichtlich/tabellen und so weiter verfeinert wird. Die genaueste Möglichkeit, dies zu erreichen, ist das Projektieren der Weltgitterdaten, die bereitgestellt werden, wenn die Szene mit dem EnableWorldMesh-Flag berechnet wird.

### <a name="visualization"></a>Visualisierung

Die [Visualisierung der räumlichen](spatial-mapping.md#visualization) Zuordnung kann zwar für Echtzeitfeedback der Umgebung verwendet werden, es gibt jedoch viele Szenarien, in denen die Einfachheit von planaren und wasserdichten Objekten mehr Leistung oder visuelle Qualität bietet. Schattenprojektion und Erdungstechniken, die mithilfe der räumlichen Zuordnung beschrieben werden, sind möglicherweise ansprechender, wenn sie auf die planaren Oberflächen projiziert werden, die von Quads oder dem planaren wasserdichten Gitternetz bereitgestellt werden. Dies gilt insbesondere für Umgebungen/Szenarien, in denen eine gründliche Vorabprüfung nicht optimal ist, da die Szene abgeleitet wird und vollständige Umgebungen und planare Annahmen Artefakte minimieren.

Darüber hinaus wird die Gesamtanzahl von Oberflächen, die von der räumlichen Zuordnung zurückgegeben werden, durch den internen räumlichen Cache beschränkt, während die Version des Spatial Mapping-Gitters von Scene Understanding auf daten der räumlichen Zuordnung zugreifen kann, die nicht zwischengespeichert werden. Aus diesem Grund eignet sich das Szenenverständnis besser für die Erfassung von Gitternetzdarstellungen für größere Bereiche (z. B. größer als ein einzelner Raum) für die Visualisierung oder weitere Gitternetzverarbeitung. Das mit EnableWorldMesh zurückgegebene Weltgittermodell hat durchgängig ein konsistentes Detailniveau, das eine ansprechendere Visualisierung ergeben kann, wenn es als Wireframe gerendert wird.

### <a name="see-also"></a>Weitere Informationen

* [Scene understanding SDK](../develop/unity/scene-understanding-SDK.md)
* [Räumliche Abbildung](spatial-mapping.md)