---
title: Lokale Raumanker in Unreal
description: Leitfaden für die Verwendung von Raumankern in Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, Features, Dokumentation, Leitfäden, Hologramme, Raumanker, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 3ce83160f745fc48f082776caa3cfa87d23a1844
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678829"
---
# <a name="local-spatial-anchors-in-unreal"></a>Lokale Raumanker in Unreal

## <a name="overview"></a>Übersicht

Raumanker werden verwendet, um Hologramme zwischen Anwendungssitzungen im realen Raum zu speichern. Diese werden über Unreal mithilfe von **ARPin** s angezeigt und im Ankerspeicher von HoloLens gespeichert, der in zukünftigen Sitzungen geladen wird. Lokale Anker eignen sich ideal als Fallback, wenn keine Internetverbindung vorhanden ist.

> [!IMPORTANT]
> Lokale Anker werden auf dem Gerät gespeichert, während Azure-Raumanker in der Cloud gespeichert werden. Wenn Sie Azure Cloud Services zum Speichern Ihrer Anker verwenden möchten, verfügen wir über ein Dokument, in dem Sie durch den Integrationsprozess für [Azure-Raumanker](unreal-azure-spatial-anchors.md) geführt werden. Beachten Sie, dass Sie sowohl lokale als auch Azure-Anker im selben Projekt haben können, ohne dass Konflikte auftreten.

## <a name="checking-the-anchor-store"></a>Überprüfen des Ankerspeichers

Vor dem Speichern oder Laden von Ankern müssen Sie sich zunächst vergewissern, dass der Ankerspeicher bereit ist.  Versuche, eine der HoloLens-Ankerfunktionen aufzurufen, bevor der Ankerspeicher bereit ist, sind nicht erfolgreich.  

![Raumanker: Speicher bereit](images/unreal-spatialanchors-store-ready.PNG)

## <a name="saving-anchors"></a>Speichern von Ankern

Sobald die Anwendung über eine Komponente verfügt, die in der Umgebung fixiert werden muss, kann sie wie folgt im Ankerspeicher gespeichert werden: 

![Raumanker: Speichern](images/unreal-spatialanchors-save.PNG)

Das heißt im Einzelnen:
1. Erzeugen Sie einen Akteur an einer bekannten Position.
2. Erstellen Sie einen **ARPin** mit dieser Position und einem Namen, der auf der Klasse des Akteurs basiert. 
3. Fügen Sie dem **ARPin** den Akteur hinzu, und speichern Sie den Pin im HoloLens-Ankerspeicher.  
    * Der gewählte Ankername muss eindeutig sein, in diesem Fall verwenden wir dafür den aktuellen Zeitstempel. 

4. Wenn der Anker erfolgreich im Ankerspeicher gespeichert wurde, kann er im HoloLens-Geräteportal unter **System > Map manager > Anchor Files Saved On Device** (System > Zuordnungs-Manager > Auf dem Gerät gespeicherte Ankerdateien) überprüft werden. 

## <a name="loading-anchors"></a>Laden von Ankern

Beim Start einer Anwendung können Sie die folgende Blaupause verwenden, um Komponenten an ihren Ankerpositionen wiederherzustellen:

![Raumanker: Laden](images/unreal-spatialanchors-load.PNG)

Das heißt im Einzelnen:
1. Iterieren Sie über alle Anker im Ankerspeicher. 
2. Erzeugen Sie einen Akteur an einem neutralen Element.
3. Heften Sie diesen Akteur an den **ARPin** aus dem Ankerspeicher an.  

    * Es ist wichtig, den Akteur am neutralen Element zu erzeugen, da der Anker dazu dient, das Hologramm in der Umgebung auf der Grundlage des gespeicherten Orts zu positionieren. Jede hier hinzugefügte Transformation fügt dem Anker einen Offset hinzu. 

Die Anker-ID wird ebenfalls abgefragt, um abhängig vom gespeicherten Namen des Ankers unterschiedliche Akteure erzeugen zu können. 

## <a name="removing-anchors"></a>Entfernen von Ankern 

Wenn Sie die Arbeit mit einem Anker beendet haben, können Sie einzelne Anker oder den gesamten Ankerspeicher mit den Komponenten **Remove ARPin from WMRAnchor Store** (ARPin aus WMRAnkerspeicher entfernen) und **Remove All ARPins from WMRAnchor Store** (Alle ARPins aus WMRAnkerspeicher entfernen) löschen.

![Raumanker: Entfernen](images/unreal-spatialanchors-remove.PNG)

> [!NOTE]
> Beachten Sie, dass Raumanker sich noch in der Betaphase befinden, prüfen Sie also unbedingt auf aktualisierte Informationen und Features.

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie dem Weg der Unreal-Entwicklungsprüfpunkte folgen, den wir entworfen haben, befinden Sie sich mitten im Kennenlernen der MRTK-Grundbausteine. Von hier aus können Sie mit dem nächsten Baustein fortfahren: 

> [!div class="nextstepaction"]
> [Azure Spatial Anchors](unreal-azure-spatial-anchors.md)

Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:

> [!div class="nextstepaction"]
> [HoloLens-Kamera](unreal-hololens-camera.md)

Sie können jederzeit zu den [Prüfpunkten für die Unreal-Entwicklung](unreal-development-overview.md#2-core-building-blocks) zurückkehren.

## <a name="see-also"></a>Siehe auch
* [Azure Spatial Anchors](unreal-azure-spatial-anchors.md)
* [Raumanker](../../design/spatial-anchors.md)
* [Koordinatensysteme](../../design/coordinate-systems.md)
