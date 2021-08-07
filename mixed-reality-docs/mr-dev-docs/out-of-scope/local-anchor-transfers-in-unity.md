---
title: Lokale Ankerübertragungen in Unity
description: Erfahren Sie, wie Sie Anker zwischen mehreren HoloLens in einer Unity Mixed Reality-Anwendung übertragen.
author: fieldsjacksong
ms.author: jacksonf
ms.date: 03/21/2018
ms.topic: article
keywords: Sharing, Anchor, WorldAnchor, MR Sharing 250, WorldAnchorTransferBatch, SpatialPerception, transfer, local anchor transfer, anchor export, anchor import
ms.openlocfilehash: eaf25edbae39aab628277aa29f975f3d4d9d7374c796fd1b7b159053d4a46b95
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189127"
---
# <a name="local-anchor-transfers-in-unity"></a>Lokale Ankerübertragungen in Unity

In Situationen, in denen Sie <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>nicht verwenden können, ermöglichen lokale Ankerübertragungen einem HoloLens-Gerät, einen Anker zu exportieren, der von einem zweiten Gerät HoloLens wird.

>[!NOTE]
>Lokale Ankerübertragungen bieten weniger stabile Ankerrückrufe als <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, und iOS- und Android-Geräte werden von diesem Ansatz nicht unterstützt.

### <a name="setting-the-spatialperception-capability"></a>Festlegen der SpatialPerception-Funktion

Damit eine App Raumanker übertragen kann, muss die *SpatialPerception-Funktion* aktiviert sein.

Aktivieren der *SpatialPerception-Funktion:*
1. Öffnen Sie im Unity-Editor den **Bereich "Player Einstellungen"** (Bearbeiten > Project Einstellungen > Player).
2. Klicken Sie auf **die Registerkarte "Windows Store".**
3. Erweitern **Sie "Einstellungen",** und überprüfen Sie die **Funktion "SpatialPerception"** in der **Liste "Funktionen".**

>[!NOTE]
>Wenn Sie Ihr Unity-Projekt bereits in eine Visual Studio-Projektmappe exportiert haben, müssen Sie entweder in einen neuen Ordner exportieren oder diese Funktion manuell im [AppxManifest in](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)Visual Studio.

### <a name="anchor-transfer"></a>Ankerübertragung

**Namespace:** *UnityEngine.XR.WSA.Sharing*<br>
**Typ:** *WorldAnchorTransferBatch*

Um einen [WorldAnchor zu übertragen,](../develop/unity/coordinate-systems-in-unity.md)muss der zu übertragende Anker einrichten. Der Benutzer eines HoloLens seine Umgebung und wählt entweder manuell oder programmgesteuert einen Punkt im Raum als Anker für die freigegebene Benutzeroberfläche aus. Die Daten, die diesen Punkt repräsentieren, können dann serialisiert und an die anderen Geräte übertragen werden, die in der Benutzererfahrung gemeinsam verwendet werden. Jedes Gerät deseriiert dann die Ankerdaten und versucht, diesen Punkt im Raum zu finden. Damit Anchor Transfer funktioniert, muss jedes Gerät in einer ausreichenden Umgebung gescannt worden sein, damit der durch den Anker dargestellte Punkt identifiziert werden kann.

### <a name="setup"></a>Setup

Der Beispielcode auf dieser Seite enthält einige Felder, die initialisiert werden müssen:
1. *GameObject rootGameObject* ist ein *GameObject* in Unity, das über eine *WorldAnchor-Komponente* verfügt. Ein Benutzer in der freigegebenen Benutzeroberfläche platzieren dieses *GameObject* und exportiert die Daten an die anderen Benutzer.
2. *WorldAnchor gameRootAnchor* ist *unityEngine.XR.WSA.WorldAnchor,* das sich auf *rootGameObject befindet.*
3. *byte[] importedData ist* ein Bytearray für den serialisierten Anker, den jeder Client über das Netzwerk empfängt.

```
public GameObject rootGameObject;
private UnityEngine.XR.WSA.WorldAnchor gameRootAnchor;

void Start ()
{
    gameRootAnchor = rootGameObject.GetComponent<UnityEngine.XR.WSA.WorldAnchor>();

    if (gameRootAnchor == null)
    {
        gameRootAnchor = rootGameObject.AddComponent<UnityEngine.XR.WSA.WorldAnchor>();
    }
}
```

### <a name="exporting"></a>Exportieren

Für den Export benötigen wir nur ein *WorldAnchor* und müssen wissen, was wir es nennen werden, damit es für die empfangende App sinnvoll ist. Ein Client in der freigegebenen Beerfahrung führt die folgenden Schritte aus, um den freigegebenen Anker zu exportieren:
1. Erstellen eines *WorldAnchorTransferBatch*
2. Hinzufügen der *zu übertragenden WorldAnchors*
3. Starten des Exports
4. Behandeln des *OnExportDataAvailable-Ereignisses,* wenn Daten verfügbar werden
5. Behandeln des *OnExportComplete-Ereignisses*

Wir erstellen ein *WorldAnchorTransferBatch-Objekt,* um das zu übertragende Objekt zu kapseln und anschließend in Bytes zu exportieren:

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

Wenn Daten verfügbar werden, senden Sie die Bytes an den Client oder Puffer, wenn Datensegmente verfügbar sind, und senden Sie sie über die gewünschten Mittel:

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

Wenn nach Abschluss des Exports Daten übertragen wurden und bei der Serialisierung ein Fehler auftraten, teilen Sie dem Client mit, die Daten zu verwerfen. Wenn die Serialisierung erfolgreich war, teilen Sie dem Client mit, dass alle Daten übertragen wurden, und der Importvorgang kann gestartet werden:

```
private void OnExportComplete(SerializationCompletionReason completionReason)
{
    if (completionReason != SerializationCompletionReason.Succeeded)
    {
        SendExportFailedToClient();
    }
    else
    {
        SendExportSucceededToClient();
    }
}
```

### <a name="importing"></a>Importieren

Nachdem alle Bytes vom Absender empfangen wurden, können wir die Daten wieder in *ein WorldAnchorTransferBatch-Objekt* importieren und unser Stammspielobjekt am gleichen physischen Speicherort sperren. Hinweis: Der Importvorgang kann vorübergehend fehlschlagen und muss wiederholt werden:

```
// This byte array should have been updated over the network from TransferDataToClient
private byte[] importedData;
private int retryCount = 3;

private void ImportRootGameObject()
{
    WorldAnchorTransferBatch.ImportAsync(importedData, OnImportComplete);
}

private void OnImportComplete(SerializationCompletionReason completionReason, WorldAnchorTransferBatch deserializedTransferBatch)
{
    if (completionReason != SerializationCompletionReason.Succeeded)
    {
        Debug.Log("Failed to import: " + completionReason.ToString());
        if (retryCount > 0)
        {
            retryCount--;
            WorldAnchorTransferBatch.ImportAsync(importedData, OnImportComplete);
        }
        return;
    }

    this.gameRootAnchor = deserializedTransferBatch.LockObject("gameRoot", this.rootGameObject);
}
```

Nachdem *ein GameObject* über den *LockObject-Aufruf* gesperrt wurde, wird es über einen *WorldAnchor* verfügen, der es an der gleichen physischen Position in der Welt hält, aber es kann sich an einer anderen Position im Unity-Koordinatenraum befinden als andere Benutzer.