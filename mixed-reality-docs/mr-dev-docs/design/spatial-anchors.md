---
title: Raumanker
description: Bewährte Methoden für die Verwendung von Raumankern zum Rendern stabiler Hologramme.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Koordinatensystem, geografischer Koordinatensystem, Welt Skalierbarkeit, Welt, Skalierung, Position, Ausrichtung, Anker, räumlicher Anker, weltweit gesperrt, Welt Sperre, Persistenz, Freigabe, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens
ms.openlocfilehash: 7f6997e491f76e66845b88ea0897dbb037495ba6
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848211"
---
# <a name="spatial-anchors"></a>Raumanker

Ein räumlicher Anker stellt einen wichtigen Punkt in der Welt dar, den das System über einen Zeitraum nachverfolgt. Jeder Anker verfügt über ein anpassbares [Koordinatensystem](coordinate-systems.md), das auf anderen Anker oder Frames basiert, um sicherzustellen, dass die verankerten Hologramme genau vorhanden sind.  Durch das Rendern eines holograms im Koordinatensystem eines Ankers erhalten Sie jeweils die präzisere Positionierung für dieses Hologramm. Dies ist der Aufwand für kleine Anpassungen im Zeitverlauf bis zur Position des Hologramms, da das System das System ständig auf der realen Welt wieder auf den Stand bringt.

Sie können auch räumliche Anker für Anwendungs Sitzungen und Geräte übergreifend beibehalten und freigeben:
* Indem lokale räumliche Anker auf einem Datenträger gespeichert und später wieder geladen werden, kann die Anwendung denselben Speicherort in der realen Welt über mehrere Anwendungs Sitzungen hinweg in einem einzelnen hololens berechnen.
* Durch die Verwendung von <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial</a> Anchor zum Erstellen eines cloudankers kann Ihre Anwendung einen räumlichen Anker für mehrere hololens-, IOS-und Android-Geräte freigeben. Wenn jedes Gerät ein – Hologramm mithilfe desselben räumlichen Ankers erstellt, sehen Benutzer, dass das – Hologramm an derselben Stelle in der realen Welt angezeigt wird. Dies ermöglicht gemeinsame Erfahrungen in Echtzeit.
* Sie können auch <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">räumliche Azure-Anker</a> für die asynchrone – Hologramm-Persistenz über hololens-, IOS-und Android-Geräte verwenden. Durch die gemeinsame Nutzung eines permanenten clouddiensts können mehrere Geräte im Lauf der Zeit dasselbe persistente Hologramm beobachten, auch wenn diese Geräte nicht gleichzeitig vorhanden sind.

Für den Einsatz von Desktop-Headsets, die sich in einem Fünfdimensionalen Durchmesser befinden, können Sie in der Regel den [stagingframe von Reference](coordinate-systems.md#stage-frame-of-reference) anstelle räumlicher Anker verwenden, der ein einzelnes Koordinatensystem bereitstellt, in dem der gesamte Inhalt dargestellt werden kann. Wenn Ihre Anwendung jedoch Benutzern ermöglicht, mehr als 5 Meter in hololens zu bewegen, was vielleicht in der gesamten Etage eines Gebäudes betrieben wird, benötigen Sie räumliche Anker, um Inhalte stabil zu halten.

Obwohl Raumanker ideal für Hologramme sind, die in der Umgebung verankert bleiben sollen, kann ein Anker nach der Positionierung nicht mehr bewegt werden. Es gibt Alternativen zu ankern, die für dynamische Hologramme geeignet sind, die mit dem Benutzer versehen werden. Es ist am besten, dynamische Hologramme mithilfe eines stationären Frame Rahmens (Grundlage der Weltkoordinaten von Unity) oder eines angefügten Frame Bilds zu positionieren.

## <a name="best-practices"></a>Bewährte Methoden

Diese Richtlinien für Raumanker helfen Ihnen, stabile Hologramme zu rendern, die die reale Welt präzise nachverfolgen.

### <a name="create-spatial-anchors-where-users-place-them"></a>Erstellen von Raumankern, wo sie vom Benutzer platziert werden

Normalerweise platzieren Benutzer explizit räumliche Anker.

Beispielsweise kann eine Anwendung auf hololens den [Blick](gaze-and-commit.md) Strahl des Benutzers mit dem [räumlichen Mapping](spatial-mapping.md) -Mesh überschneiden, damit der Benutzer entscheiden kann, wo ein Hologram platziert werden soll. Wenn der Benutzer tippt, um dieses – Hologramm zu platzieren, erstellen Sie am schnittspunkt einen räumlichen Anker, und platzieren Sie dann das – Hologramm am Ursprung des Koordinatensystems dieses Ankers.

Lokale räumliche Anker sind einfach und leistungsfähig zum Erstellen. Das System kombiniert interne Daten, wenn mehrere Anker ihre zugrunde liegenden Sensordaten gemeinsam nutzen können. Wir empfehlen die Erstellung eines neuen lokalen räumlichen Ankers für jedes – Hologramm, das ein Benutzer explizit platziert, außer in den unten beschriebenen Fällen, wie z. b. bei festen Gruppen von holograms.

### <a name="always-render-anchored-holograms-within-3-meters-of-their-anchor"></a>Verankerte Hologramme immer innerhalb von 3 Metern von ihrem Anker rendern

Raumanker stabilisieren ihr Koordinatensystem in der Nähe des Ankerursprungs. Wenn Sie Hologramme aus dem Ursprungs Bereich auf mehr als 3 Meter rendernen, treten möglicherweise spürbare Positionsfehler auf, die relativ zu ihrer Entfernung von diesem Ursprung liegen. Dies funktioniert, wenn der Benutzer in der Nähe des Ankers steht, da das – Hologramm auch weit entfernt ist. Anders ausgedrückt: der Angular-Fehler des entfernten holograms ist klein. Wenn der Benutzer jedoch zu diesem entfernten Hologram geht, ist er in seiner Ansicht groß, sodass die Auswirkungen der Hebel-Arm aus dem Ursprung des Ursprungs Ankers offensichtlich werden.

### <a name="group-holograms-that-should-form-a-rigid-cluster"></a>Gruppieren von Hologrammen, die einen starren Cluster bilden sollen

Mehrere holograms können denselben räumlichen Anker gemeinsam verwenden, wenn die Anwendung erwartet, dass diese Hologramme eine fixierte Beziehung untereinander aufrechterhalten.

Wenn Sie z. b. ein Holographic-Sonnensystem in einem Raum animieren, ist es besser, alle Objekte des Sonnensystems mit einem einzigen Anker in der Mitte zu verbinden. Auf diese Weise werden Sie problemlos auf der Grundlage der anderen verschoben. In diesem Fall ist es das Sonnensystem als Ganzes, das verankert ist, auch wenn die Komponenten Teile sich dynamisch um den Anker bewegen.

Der Schlüssel für die Beibehaltung der – Hologramm-Stabilität besteht darin, die drei Meter lange Regel zu befolgen.

### <a name="render-highly-dynamic-holograms-using-the-stationary-frame-of-reference-instead-of-a-local-spatial-anchor"></a>Hochdynamische Hologramme mit dem stationären Bezugsrahmen anstatt mit einem lokalen Raumanker rendern

Wenn Sie über ein sehr dynamisches Hologram verfügen, z. b. ein Zeichen, das um einen Raum geht, oder eine unverankerte Benutzeroberfläche, die entlang der Wand in der [Nähe des Benutzers](coordinate-systems.md#stationary-frame-of-reference)folgt, empfiehlt es sich, lokale räumliche Anker zu überspringen und diese Hologramme direkt im Koordinatensystem zu erzeugen In Unity erreichen Sie dies, indem Sie holograms direkt in Weltkoordinaten ohne worldanchor platzieren. Bei holograms in einem stationären Verweis Rahmen kann es zu Abweichungen kommen, wenn der Benutzer weit vom Hologram abweicht. Dies ist jedoch weniger wahrscheinlich für dynamische Hologramme erkennbar: entweder wird das – Hologramm ständig ständig verschoben, oder die Bewegung hält den Benutzer ständig in der Nähe, wo Abweichungen minimiert werden.

Ein interessanter Fall von dynamischen Hologrammen ist ein Objekt, das von einem verankerten Koordinatensystem zum anderen animiert wird. Beispielsweise können Sie über zwei Burgen verfügen, die zehn Meter voneinander entfernt sind, und jeweils auf Ihrem eigenen räumlichen Anker, wobei eine Burg einen Cannonball auf der anderen Burg auslöst. Wenn der Cannonball ausgelöst wird, können Sie ihn an der entsprechenden Stelle im stationären Verweis Verweis an die Kanone im verankerten Koordinatensystem der ersten Burg Rendering. Im stationären Bezugsrahmen kann sie dann ihrer Flugbahn folgen, wenn sie 10 Meter durch die Luft fliegt. Wenn der Cannonball das andere Schloss erreicht, können Sie ihn in das verankerte Koordinatensystem der zweiten Burg verschieben, um die Physik Berechnungen mit den starren Texten dieser Burg zuzulassen.

Wenn Sie ein äußerst dynamisches Hologramm für Geräte freigeben, wählen Sie einen räumlichen Anker in der Cloud aus, der als übergeordnetes Element fungiert, da die Rahmen der Referenz nicht auf allen Geräten freigegeben werden können.  Sie sollten jedoch sicherstellen, dass entweder das dynamische – Hologramm oder die Geräte, die Sie anzeigen, im 3-Meter-Radius des Ankers bleiben, sodass das – Hologramm auf allen Geräten stabil erscheint.

### <a name="avoid-creating-a-grid-of-spatial-anchors"></a>Vermeiden der Erstellung eines Rasters von Raumankern

Möglicherweise ist es verlockend, dass Ihre Anwendung ein reguläres Raster räumlicher Anker ablegen soll, während der Benutzer durchläuft, um dynamische Objekte vom Anker zum Anker zu bewegen, während Sie sich bewegen. Dies umfasst jedoch mehr Verwaltung für Ihre Anwendung, ohne dass die Tiefensensor Daten, die das System selbst intern verwaltet, genutzt werden. In diesen Fällen erzielen Sie bessere Ergebnisse, indem Sie Ihre Hologramme im stationären Frame des Verweises platzieren, wie im obigen Abschnitt beschrieben.
Wenn Sie einen Satz von cloudbasierten Ankern in einem statischen Raum vorpositionieren, erwägen Sie, die räumlichen Anker an den Standorten der wichtigen Hologramme zu platzieren, über die der Benutzer gemäß dem oben genannten Prinzip verfügt, anstatt ein beliebiges Raster von Ankern zu erstellen. Dadurch wird sichergestellt, dass Sie die maximale Stabilität für diese Schlüsselhologramme erhalten.

### <a name="release-local-spatial-anchors-you-no-longer-need"></a>Freigeben lokaler Raumanker, die nicht länger benötigt werden

Obwohl ein lokaler räumlicher Anker aktiv ist, priorisiert das System die Beibehaltung der Sensordaten, die sich in der Nähe des Ankers befinden. Wenn Sie keinen räumlichen Anker mehr verwenden, können Sie nicht mehr auf das Koordinatensystem zugreifen. Dadurch können die zugrunde liegenden Sensordaten bei Bedarf entfernt werden.

Dies ist besonders wichtig für lokale Anker, die Sie im räumlichen Anker Speicher beibehalten haben. Die Sensordaten hinter diesen ankern werden permanent aufbewahrt, damit Ihre Anwendung diesen Anker in zukünftigen Sitzungen finden kann, wodurch der zum Nachverfolgen anderer Anker verfügbare Speicherplatz reduziert wird. Speichern Sie nur lokale Anker, die Sie in zukünftigen Sitzungen erneut finden müssen. Wir empfehlen, Sie aus dem Speicher zu entfernen, wenn Sie für den Benutzer nicht mehr sinnvoll sind.

Bei Cloudraumankern kann Ihr Speicher entsprechend den Anforderungen Ihres Szenarios skaliert werden. Sie können beliebig viele cloudananker speichern und freigeben, wenn Sie wissen, dass die Benutzer den Anker nicht mehr benötigen.

## <a name="see-also"></a>Weitere Informationen

* [Koordinatensysteme](coordinate-systems.md)
* [Gemeinsame Erlebnisse in Mixed Reality](../develop/platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* [Persistenz in Unity](../develop/unity/persistence-in-unity.md)
* [Raumanker in DirectX](../develop/native/coordinate-systems-in-directx.md#place-holograms-in-the-world-using-spatial-anchors)
* [Fallstudie – Schauen durch Löcher in Ihrer Realität](../out-of-scope/case-study-looking-through-holes-in-your-reality.md)
