---
title: Persistenz in Unity
description: Persistenz ermöglicht es dem Benutzer, einzelne Hologramme an den gewünschten Ort zu heften und sie später bei vielen Verwendungen Ihrer App zu finden.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, Persistenz, Unity, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 9283191c024cbe33ecda3946a4e9bcbd5f3708c21a3578484b547207ee70a49b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208970"
---
# <a name="persistence-in-unity"></a>Persistenz in Unity

**Namespace:** *UnityEngine.XR.WSA.Persistence*<br>
**Klasse:** *WorldAnchorStore*

WorldAnchorStore ist der Schlüssel zum Erstellen holografischer Erfahrungen, bei denen Hologramme in bestimmten realen Positionen über Instanzen der Anwendung hinweg verbleiben. Benutzer können dann einzelne Hologramme an jeder gewünschten Stelle anheften und sie später bei vielen Verwendungsmöglichkeiten Ihrer App an der gleichen Stelle finden.

## <a name="how-to-persist-holograms-across-sessions"></a>Beibehalten von Hologrammen über Sitzungen hinweg

Mit WorldAnchorStore können Sie den Speicherort von WorldAnchor sitzungsübergreifend beibehalten. Um Hologramme tatsächlich sitzungsübergreifend beizubehalten, müssen Sie Ihre GameObjects, die einen bestimmten Weltanker verwenden, separat nachverfolgen. Es ist oft sinnvoll, einen GameObject-Stamm mit einem Weltanker zu erstellen und untergeordnete Hologramme mit einem lokalen Positionsoffset zu verankern.

So laden Sie Hologramme aus vorherigen Sitzungen:
1. Abrufen des WorldAnchorStore
2. Laden von App-Daten im Zusammenhang mit dem Weltanker, der Ihnen die ID des Weltankers liefert
3. Laden eines Weltankers aus seiner ID

So speichern Sie Hologramme für zukünftige Sitzungen:
1. Abrufen des WorldAnchorStore
2. Speichern eines Weltankers, der eine ID angibt
3. Speichern von App-Daten im Zusammenhang mit dem Weltanker zusammen mit einer ID

### <a name="getting-the-worldanchorstore"></a>Abrufen von WorldAnchorStore

Sie sollten einen Verweis auf WorldAnchorStore beibehalten, damit Sie wissen, wann er bereit ist, einen Vorgang auszuführen. Da dies ein asynchroner Aufruf ist, möchten Sie möglicherweise nach dem Start Aufrufen von:

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

StoreLoaded ist in diesem Fall unser Handler für den Fall, dass das Laden des WorldAnchorStore abgeschlossen wurde:

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

Wir haben nun einen Verweis auf den WorldAnchorStore, den wir zum Speichern und Laden bestimmter World Anchors verwenden.

### <a name="saving-a-worldanchor"></a>Speichern eines WorldAnchor

Um zu speichern, müssen wir einfach benennen, was wir speichern, und es an den WorldAnchor übergeben, den wir zuvor erhalten haben, als wir speichern möchten. Hinweis: Beim Versuch, zwei Anker in derselben Zeichenfolge zu speichern, tritt ein Fehler auf (speichern. Speichern gibt FALSE zurück. Löschen Sie den vorherigen Speicher, bevor Sie den neuen speichern:

```
private void SaveGame()
{
       // Save data about holograms positioned by this world anchor
       if (!this.savedRoot) // Only Save the root once
       {
              this.savedRoot = this.store.Save("rootGameObject", anchor);
              Assert(this.savedRoot);
       }
}
```

### <a name="loading-a-worldanchor"></a>Laden eines WorldAnchor

Und laden Sie:

```
private void LoadGame()
{
       // Save data about holograms positioned by this world anchor
       this.savedRoot = this.store.Load("rootGameObject", rootGameObject);
       if (!this.savedRoot)
       {
              // We didn't actually have the game root saved! We have to re-place our objects or start over
       }
}
```

Darüber hinaus können wir store verwenden. Delete() zum Entfernen eines Zuvor gespeicherten und gespeicherten Ankers. Clear(), um alle zuvor gespeicherten Daten zu entfernen.

### <a name="enumerating-existing-anchors"></a>Aufzählen vorhandener Anker

Rufen Sie GetAllIds auf, um zuvor gespeicherte Anker zu ermitteln.

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a>Beibehalten von Hologrammen für mehrere Geräte

Sie können <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> verwenden, um einen permanenten Cloudanker aus einem lokalen WorldAnchor zu erstellen, den Ihre App dann auf mehreren HoloLens-, iOS- und Android-Geräten finden kann, auch wenn diese Geräte nicht gleichzeitig vorhanden sind.  Da Cloudanker persistent sind, können mehrere Geräte im Laufe der Zeit jeweils Inhalte sehen, die relativ zu diesem Anker an demselben physischen Ort gerendert werden.

Probieren Sie die fünfminütigen <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity-Schnellstarts</a>aus, um mit dem Erstellen von gemeinsamen Erfahrungen in Unity zu beginnen.

Sobald Sie mit Azure Spatial Anchors ausgeführt werden, können Sie <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Anker in Unity erstellen und suchen.</a>

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie die von uns festgelegte Unity-Entwicklungsprüfpunkt-Journey verfolgen, können Sie die Mixed Reality wichtigsten Bausteine erkunden. Von hier aus können Sie mit dem nächsten Baustein fortfahren:

> [!div class="nextstepaction"]
> [Räumliche Abbildung](spatial-mapping-in-unity.md)

Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:

> [!div class="nextstepaction"]
> [Gemeinsame Erfahrung](shared-experiences-in-unity.md)

Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#2-core-building-blocks) zurückkehren.

## <a name="see-also"></a>Weitere Informationen
* [Persistenz des Raumankers](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK für Unity</a>