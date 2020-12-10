---
title: Persistenz in Unity
description: Mit der Persistenz können Sie die einzelnen Hologramme an den gewünschten Ort anheften und später über viele Verwendungszwecke Ihrer APP suchen.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Hololens, Persistenz, Unity, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: d74f9c0a118c1886037c564073742ebedc7d0146
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010441"
---
# <a name="persistence-in-unity"></a>Persistenz in Unity

**Namespace:** *unityengine. XR. WSA. Persistenz*<br>
**Klasse:** *worldanchorstore*

Worldanchorstore ist der Schlüssel für die Erstellung von Holographic-Erfahrungen, bei denen Hologramme in den einzelnen Anwendungs Instanzen in bestimmten realen Positionen bleiben. Benutzer können dann jedes beliebige Hologramm an die gewünschte Stelle anheften und später auf der gleichen Stelle über viele Verwendungszwecke Ihrer APP suchen.

## <a name="how-to-persist-holograms-across-sessions"></a>Beibehalten von holograms über Sitzungen hinweg

Mit worldanchorstore können Sie den Speicherort von worldanchor Sitzungs übergreifend beibehalten. Sie müssen ihre gameobjects-Objekte, die einen bestimmten Welt Anker verwenden, separat nachverfolgen, um Hologramme in mehreren Sitzungen dauerhaft beizubehalten. Häufig ist es sinnvoll, einen gameobject-Stamm mit einem Welt Anker zu erstellen und untergeordnete Hologramme mit einem lokalen Positions Offset zu verankern.

So laden Sie holograms aus vorherigen Sitzungen:
1. Verschaffen Sie sich den worldanchorstore
2. Laden von App-Daten in Bezug auf den World-Anker, der Ihnen die ID des Welt Ankers liefert
3. Einen Welt Anker aus seiner ID laden

So speichern Sie Hologramme für zukünftige Sitzungen:
1. Verschaffen Sie sich den worldanchorstore
2. Speichern eines Welt Ankers, der eine ID angibt
3. Speichern von App-Daten, die sich auf den Welt Anker beziehen, sowie eine ID

### <a name="getting-the-worldanchorstore"></a>Der worldanchorstore wird erhalten.

Sie sollten einen Verweis auf den worldanchorstore behalten, damit Sie wissen, wann er bereit ist, einen Vorgang auszuführen. Da es sich hierbei um einen asynchronen-Befehl handelt, der möglicherweise unmittelbar nach dem Start aufgerufen wird, sollten Sie Folgendes aufrufen:

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

Storeloaded ist in diesem Fall der Handler für den Fall, dass der worldanchorstore das Laden abgeschlossen hat:

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

Wir haben nun einen Verweis auf den worldanchorstore, den wir verwenden werden, um bestimmte weltanker zu speichern und zu laden.

### <a name="saving-a-worldanchor"></a>Speichern von worldanchor

Zum Speichern müssen wir einfach den Namen der Speicherung benennen und Sie an den worldanchor übergeben, den wir vor dem Speichern erhalten haben. Hinweis: Wenn Sie versuchen, zwei Anker in derselben Zeichenfolge zu speichern, tritt ein Fehler auf (speichern. Save gibt false zurück). Löschen Sie die vorherige Speicherung, bevor Sie die neue speichern:

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

### <a name="loading-a-worldanchor"></a>Laden von worldanchor

Und zum Laden:

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

Wir können außerdem "Store" verwenden. Delete () um einen Anker zu entfernen, den wir zuvor gespeichert und gespeichert haben. Löschen Sie (), um alle zuvor gespeicherten Daten zu entfernen.

### <a name="enumerating-existing-anchors"></a>Auflisten vorhandener Anker

Um zuvor gespeicherte Anker zu ermitteln, müssen Sie getallids aufrufen.

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a>Beibehalten von holograms für mehrere Geräte

Sie können <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial</a> Anchor verwenden, um einen permanenten cloudanker von einem lokalen worldanchor zu erstellen, den Ihre APP dann über mehrere hololens-, IOS-und Android-Geräte hinweg finden kann, auch wenn diese Geräte nicht gleichzeitig vorhanden sind.  Da cloudananker permanent sind, können mehrere Geräte im Lauf der Zeit jeweils Inhalte sehen, die relativ zu diesem Anker am gleichen physischen Standort gerendert werden.

Um mit der Einführung von freigegebenen Erfahrungen in Unity zu beginnen, testen Sie die fünfminütigen <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchor Unity-Schnellstarts</a>.

Sobald Sie mit räumlichen Azure-Ankern arbeiten, können Sie <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Anker in Unity erstellen und lokalisieren</a>.

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie der Unity-Entwicklungs Prüf Punkt Journey folgen, die wir gerade angelegt haben, sind Sie in der Mitte, dass Sie die Grundbausteine der gemischten Realität erkunden. Von hier aus können Sie mit dem nächsten Baustein fortfahren:

> [!div class="nextstepaction"]
> [Räumliche Abbildung](spatial-mapping-in-unity.md)

Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:

> [!div class="nextstepaction"]
> [Gemeinsame Erfahrung](shared-experiences-in-unity.md)

Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#2-core-building-blocks) zurückkehren.

## <a name="see-also"></a>Weitere Informationen
* [Dauerhaftigkeit räumlicher Anker](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchor SDK für Unity</a>
