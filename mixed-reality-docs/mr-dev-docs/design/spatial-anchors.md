---
title: Raumanker
description: Erfahren Sie mehr über bewährte Methoden für die Verwendung von Raumankern zum Rendern stabiler Hologramme in Mixed Reality-Anwendungen.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Koordinatensystem, Raumkoordinatensystem, Weltskalierung, Welt, Skalierung, Position, Ausrichtung, Anker, Raumanker, Weltsperrung, Persistenz, Freigabe, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens
ms.openlocfilehash: dc9b57d51f4202499d82abb8d210261d2ee36dc60bb90ed039a7554f82af79a0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193514"
---
# <a name="spatial-anchors"></a>Raumanker

Ein Raumanker stellt einen wichtigen Punkt auf der Welt dar, den das System im Laufe der Zeit verfolgt. Jeder Anker verfügt über ein anpassbares [Koordinatensystem, das](coordinate-systems.md)auf anderen Ankern oder Bezugsrahmen basiert, um sicherzustellen, dass verankerte Hologramme genau an Ort und Stelle bleiben.  Wenn Sie ein Hologramm im Koordinatensystem eines Ankers rendern, erhalten Sie die genaueste Positionierung für dieses Hologramm zu einem beliebigen Zeitpunkt. Dies geschieht auf Kosten kleiner Anpassungen der Position des Hologramms im Laufe der Zeit, während das System es basierend auf der realen Welt ständig wieder an den richtigen Ort verschiebt.

Sie können Raumanker auch für Anwendungssitzungen und Geräte hinweg beibehalten und freigeben:
* Indem lokale Raumanker auf dem Datenträger gespeichert und später wieder geladen werden, kann Ihre Anwendung den gleichen Standort in der realen Welt über mehrere Anwendungssitzungen auf einem einzigen HoloLens berechnen.
* Durch die Verwendung von <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> zum Erstellen eines Cloudankers kann Ihre Anwendung einen Raumanker auf mehreren HoloLens-, iOS- und Android-Geräten gemeinsam nutzen. Wenn jedes Gerät ein Hologramm mit demselben Raumanker rendert, sehen Benutzer, dass das Hologramm an derselben Stelle in der realen Welt angezeigt wird. Dies ermöglicht gemeinsame Erfahrungen in Echtzeit.
* Sie können <a href="/azure/spatial-anchors/overview" target="_blank">azure Spatial Anchors</a> auch für asynchrone Hologrammpersistenz auf HoloLens-, iOS- und Android-Geräten verwenden. Durch die gemeinsame Nutzung eines permanenten Cloudraumankers können mehrere Geräte das gleiche persistente Hologramm im Laufe der Zeit beobachten, auch wenn diese Geräte nicht gleichzeitig vorhanden sind.

Für Stand- oder Raumerfahrungen für tethered-Desktop-Headsets, die innerhalb eines 5-Meter-Koordinatenbereichs bleiben, können Sie in der Regel den [Referenzrahmen der Stufe](coordinate-systems.md#stage-frame-of-reference) anstelle von Raumankern verwenden, wodurch Sie ein einzelnes Koordinatensystem zum Rendern aller Inhalte erhalten. Wenn Ihre Anwendung Benutzern jedoch eine Entfernung von mehr als 5 Metern in HoloLens ermöglicht, z. B. in einer ganzen Etage eines Gebäudes, benötigen Sie Raumanker, um die Inhalte stabil zu halten.

Obwohl Raumanker ideal für Hologramme sind, die in der Umgebung verankert bleiben sollen, kann ein Anker nach der Positionierung nicht mehr bewegt werden. Es gibt Alternativen zu Ankern, die besser für dynamische Hologramme geeignet sind, die zusammen mit dem Benutzer taggiert werden. Es empfiehlt sich, dynamische Hologramme mithilfe eines ortsfesten Bezugsrahmens (der Grundlage für die Weltkoordinaten von Unity) oder eines angefügten Bezugsrahmens zu positionieren.

## <a name="best-practices"></a>Bewährte Methoden

Diese Richtlinien für Raumanker helfen Ihnen, stabile Hologramme zu rendern, die die reale Welt präzise nachverfolgen.

### <a name="create-spatial-anchors-where-users-place-them"></a>Erstellen von Raumankern, wo sie vom Benutzer platziert werden

In der Regel platzieren Benutzer explizit Raumanker.

Beispielsweise kann eine Anwendung auf HoloLens den [Anviertstrahl](gaze-and-commit.md) des Benutzers mit dem [Raumzuordnungsgitternetz](spatial-mapping.md) überschneiden, damit der Benutzer entscheiden kann, wo ein Hologramm zu platzieren ist. Wenn der Benutzer tippt, um dieses Hologramm zu platzieren, erstellen Sie einen Raumanker am Schnittpunkt, und platzieren Sie das Hologramm dann am Ursprung des Koordinatensystems dieses Ankers.

Lokale Raumanker sind einfach und leistungsbringend zu erstellen. Das System kombiniert interne Daten, wenn mehrere Anker ihre zugrunde liegenden Sensordaten gemeinsam nutzen können. Es wird empfohlen, einen neuen lokalen Raumanker für jedes Hologramm zu erstellen, das ein Benutzer explizit platziert, mit Ausnahme der unten beschriebenen Fälle, z. B. starre Gruppen von Hologrammen.

### <a name="always-render-anchored-holograms-within-3-meters-of-their-anchor"></a>Verankerte Hologramme immer innerhalb von 3 Metern von ihrem Anker rendern

Raumanker stabilisieren ihr Koordinatensystem in der Nähe des Ankerursprungs. Wenn Sie Hologramme mehr als 3 Meter vom Ursprung entfernt rendern, treten bei den Hologrammen aufgrund von Arm-Arm-Effekten möglicherweise merkliche Positionsfehler im Verhältnis zu ihrer Entfernung zu diesem Ursprung auf. Dies funktioniert, wenn der Benutzer in der Nähe des Ankers steht, da das Hologramm auch weit vom Benutzer entfernt ist. Anders ausgedrückt: Der Winkelfehler des entfernten Hologramms ist klein. Wenn der Benutzer jedoch zu diesem entfernten Hologramm führt, ist es in seiner Ansicht groß, sodass die Hebel-Arm-Effekte des fernen Ankerursprungs offensichtlich werden.

### <a name="group-holograms-that-should-form-a-rigid-cluster"></a>Gruppieren von Hologrammen, die einen starren Cluster bilden sollen

Mehrere Hologramme können denselben Raumanker gemeinsam nutzen, wenn die Anwendung erwartet, dass diese Hologramme feste Beziehungen miteinander aufrechterhalten.

Wenn Sie beispielsweise ein holografisches Solarsystem in einem Raum animieren, ist es besser, alle Solarsystemobjekte an einen einzelnen Anker in der Mitte zu binden. Auf diese Weise bewegen sie sich reibungslos aufeinander. In diesem Fall ist es das gesamte Solarsystem, das verankert ist, obwohl sich seine Komponenten dynamisch um den Anker bewegen.

Der wichtigste Nachteil bei der Aufrechterhaltung der Hologrammstabilität besteht darin, die oben genannte 3-Meter-Regel zu befolgen.

### <a name="render-highly-dynamic-holograms-using-the-stationary-frame-of-reference-instead-of-a-local-spatial-anchor"></a>Hochdynamische Hologramme mit dem stationären Bezugsrahmen anstatt mit einem lokalen Raumanker rendern

Wenn Sie über ein hochgradig dynamisches Hologramm verfügen, z. B. ein Zeichen, das einen Raum durchläuft, oder eine unverankerte Benutzeroberfläche, die entlang der Wand in der Nähe des Benutzers folgt, ist es am besten, lokale Raumanker zu überspringen und diese Hologramme direkt im Koordinatensystem zu rendern, das vom [stationären Bezugsrahmen](coordinate-systems.md#stationary-frame-of-reference)bereitgestellt wird. In Unity erreichen Sie dies, indem Sie Hologramme direkt in Weltkoordinaten ohne WorldAnchor platzieren. Hologramme in einem stationären Bezugsrahmen kann es zu Abweichungen kommen, wenn der Benutzer weit vom Hologramm entfernt ist. Für dynamische Hologramme ist dies jedoch weniger wahrscheinlich: Entweder bewegt sich das Hologramm ohnehin ständig, oder seine Bewegung hält es ständig in der Nähe des Benutzers, wo abweichungen minimiert werden.

Ein interessanter Fall von dynamischen Hologrammen ist ein Objekt, das von einem verankerten Koordinatensystem zum anderen animiert wird. Sie können z. B. zwei 10 Meter voneinander entfernte Schlöße haben, die jeweils auf einem eigenen Raumanker stehen, wobei eine Einzige einen 10-Meter-Löschball auf der anderen Kugel auslöst. Wenn der Brillenball ausgelöst wird, können Sie ihn an der entsprechenden Stelle im stationären Bezugsrahmen rendern, um mit dem Sand im verankerten Koordinatensystem des ersten Schlosses übereinzutreffen. Im stationären Bezugsrahmen kann sie dann ihrer Flugbahn folgen, wenn sie 10 Meter durch die Luft fliegt. Wenn der Kastenball die andere Schlossanlage erreicht, können Sie ihn in das verankerte Koordinatensystem der zweiten Luftanlage verschieben, um physikalische Berechnungen mit den starren Körpern dieses Schlosses zu ermöglichen.

Wenn Sie ein hochgradig dynamisches Hologramm geräteübergreifend freigeben, wählen Sie einen cloudbasierten Raumanker aus, um als übergeordnetes Element zu fungieren, da ortsbezogene Bezugsrahmen nicht geräteübergreifend freigegeben werden können.  Sie sollten jedoch sicherstellen, dass entweder das dynamische Hologramm oder die Geräte, die es anzeigen, innerhalb des Radius von 3 Metern des Ankers bleiben, damit das Hologramm auf allen Geräten stabil angezeigt wird.

### <a name="avoid-creating-a-grid-of-spatial-anchors"></a>Vermeiden der Erstellung eines Rasters von Raumankern

Möglicherweise sind Sie verlockend, dass Ihre Anwendung ein reguläres Raster von Raumankern verwerfen kann, während der Benutzer durchläuft und dynamische Objekte von Anker zu Anker übergibt, während sie sich bewegen. Dies umfasst jedoch eine größere Verwaltung für Ihre Anwendung, ohne die Vorteile der tiefen Sensordaten zu nutzen, die das System selbst intern verwaltet. In diesen Fällen erzielen Sie bessere Ergebnisse, indem Sie Ihre Hologramme wie im obigen Abschnitt beschrieben im stationären Bezugsrahmen platzieren.
Wenn Sie eine Reihe von Cloudraumankern um einen statischen Raum vorab positionieren, sollten Sie die Raumanker an den Positionen der Schlüssel hologramme platzieren, auf die der Benutzer nach dem oben genannten Prinzip stößt, anstatt ein beliebiges Raster von Ankern zu erstellen. Dadurch wird sichergestellt, dass Sie die maximale Stabilität für diese Schlüsselhologramme erhalten.

### <a name="release-local-spatial-anchors-you-no-longer-need"></a>Freigeben lokaler Raumanker, die nicht länger benötigt werden

Während ein lokaler Raumanker aktiv ist, priorisiert das System die Beibehaltung der Sensordaten, die sich in der Nähe dieses Ankers befindet. Wenn Sie keinen Raumanker mehr verwenden, beenden Sie den Zugriff auf das Koordinatensystem. Dadurch können die zugrunde liegenden Sensordaten nach Bedarf entfernt werden.

Dies ist besonders wichtig für lokale Anker, die Sie im Raumankerspeicher beibehalten haben. Die Sensordaten hinter diesen Ankern werden dauerhaft gespeichert, damit Ihre Anwendung diesen Anker in zukünftigen Sitzungen finden kann, wodurch der verfügbare Platz zum Nachverfolgen anderer Anker reduziert wird. Speichern Sie nur lokale Anker, die Sie in zukünftigen Sitzungen erneut finden müssen. Es wird empfohlen, sie aus dem Speicher zu entfernen, wenn sie für den Benutzer nicht mehr aussagekräftig sind.

Bei Cloudraumankern kann Ihr Speicher entsprechend den Anforderungen Ihres Szenarios skaliert werden. Sie können beliebig viele Cloudanker speichern und freigeben, wenn Sie wissen, dass Ihre Benutzer den Anker nicht mehr benötigen.

## <a name="see-also"></a>Weitere Informationen

* [Koordinatensysteme](coordinate-systems.md)
* [Gemeinsame Erlebnisse in Mixed Reality](../develop/platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* [Persistenz in Unity](../develop/unity/persistence-in-unity.md)
* [Raumanker in DirectX](../develop/native/coordinate-systems-in-directx.md#place-holograms-in-the-world-using-spatial-anchors)
* [Fallstudie – Schauen durch Löcher in Ihrer Realität](../out-of-scope/case-study-looking-through-holes-in-your-reality.md)