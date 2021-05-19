---
title: Beobachter von Gittermodellen für räumliche Objekte
description: Dokumentation zum Spatial Mesh Observer in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 51963fca4fa76340089b84e400f2882763977f72
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144456"
---
# <a name="configuring-mesh-observers-for-the-editor"></a>Konfigurieren von Mesh-Beobachtern für den Editor

Eine praktische Möglichkeit zum Bereitstellen von Umgebungsnetzdaten im Unity-Editor ist die Verwendung der [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) -Klasse. Der *Spatial Object Mesh Observer* ist ein editorbasierter Datenanbieter für das Spatial [Awareness-System,](spatial-awareness-getting-started.md) mit dem 3D-Modelldaten importiert werden können, um ein räumliches Gittermodell darzustellen. Eine häufige Verwendung des *Spatial Object Mesh-Beobachters* ist das Importieren von Daten, die über einen Microsoft HoloLens gescannt werden, um zu testen, wie sich eine Umgebung an verschiedene Umgebungen innerhalb von Unity anpasst.

## <a name="getting-started"></a>Erste Schritte

Dieser Leitfaden führt Sie durch das Einrichten eines *Spatial Object Mesh-Beobachters.* Es gibt drei wichtige Schritte, um dieses Feature zu aktivieren.

1. Hinzufügen eines *Spatial Object Mesh-Beobachters* zum Systemprofil für räumliche Wahrnehmung
1. Festlegen des Environment Mesh Data-Objekts
1. [Konfigurieren der restlichen Mesh Observer-Profileigenschaften](configuring-spatial-awareness-mesh-observer.md)

### <a name="set-up-a-spatial-object-mesh-observer-profile"></a>Einrichten eines Beobachterprofils für *ein räumliches Objektgittermodell*

1. Wählen Sie das gewünschte *Mixed Reality Toolkit-Konfigurationsprofil* aus, oder wählen Sie das Mixed Reality *Toolkit-Objekt* in der Szene aus.
1. Öffnen oder erweitern Sie die Registerkarte *Spatial Awareness System (System für räumliche Wahrnehmung).*
1. Klicken Sie auf die Schaltfläche *"Räumlichen Beobachter hinzufügen".*

    ![Hinzufügen eines räumlichen Beobachters](../images/spatial-awareness/AddObserver.png)

1. Wählen Sie den Typ *SpatialObjectMeshObserver* aus.

    ![Wählen Sie Spatial Object Mesh Observer aus.](../images/spatial-awareness/SelectObjectObserver.png)

1. Wählen Sie das gewünschte *Spatial Mesh-Objekt aus.* Standardmäßig wird der Beobachter mit einem Beispielmodell konfiguriert. Dieses Modell wurde mit einem Microsoft HoloLens erstellt, aber es ist [möglich, ein neues Scannetzobjekt](#acquiring-environment-scans)zu erstellen.
1. [Konfigurieren der restlichen Mesh Observer-Profileigenschaften](configuring-spatial-awareness-mesh-observer.md)

    ![Wählen Sie das Mesh-Objekt aus.](../images/spatial-awareness/ObjectObserverProfile.png)

### <a name="spatial-object-mesh-observer-profile-notes"></a>Profilhinweise zum Beobachter für räumliches Objektgittermodell

Da der *Spatial Object Mesh Observer* Daten aus einem 3D-Modell lädt, werden einige der standarden Gittermodellbeobachtereinstellungen, die unten beschrieben sind, nicht unterstützt.

**Updateintervall**

Der  *Spatial Object Mesh Observer* sendet alle Gittermodelle an eine Anwendung, wenn das Modell geladen wird. Es werden keine Zeitdeltata zwischen Updates simuliert. Eine Anwendung kann die Mesh-Ereignisse durch Aufrufen von und [`myObserver.ClearObservation()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.ClearObservations) erneut [`myObserver.Resume()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume) empfangen.

**Is Stationärer Beobachter**

Der *Spatial Object Mesh Observer* betrachtet alle 3D-Gittermodellobjekte als stationär und ignoriert den Ursprung.

**Observer Shape and Extents**

Der  *Spatial Object Mesh Observer* sendet das gesamte 3D-Gittermodell an die Anwendung. Beobachterform und -ausdrungen werden nicht berücksichtigt.

**Detail- und Dreiecksebene/Kubische Verbrauchsmessung**

Der Observer versucht beim Senden der Gittermodelle an die Anwendung nicht, 3D-Modell-LODs zu finden.

## <a name="acquiring-environment-scans"></a>Abrufen von Umgebungsscans

In diesem Abschnitt werden zusätzliche Informationen zum Erstellen und Sammeln von *Spatial Mesh-Objektdateien* für die Verwendung mit *dem Spatial Object Mesh Observer beschrieben.*

### <a name="windows-device-portal"></a>Windows-Geräteportal

Die [Windows-Geräteportal](/windows/mixed-reality/using-the-windows-device-portal) kann verwendet werden, um das räumliche Gitternetz als OBJ-Datei von einem Microsoft HoloLens herunterladen.

1. Scannen durch einfaches Gehen und Anzeigen der gewünschten Umgebung mit einer HoloLens
1. Stellen Sie mithilfe der -Anwendung eine Verbindung mit hololens Windows-Geräteportal
1. Navigieren Sie zur *Seite "3D-Ansicht".*
1. Klicken Sie im *Abschnitt Räumliche* Zuordnung auf *die Schaltfläche* Aktualisieren.
1. Klicken Sie im *Abschnitt Räumliche* Zuordnung auf die *Schaltfläche* Speichern, um die OBJ-Datei auf dem PC zu speichern.

> [!NOTE]
> **HoloToolkit-ROOM-Dateien**
>
> Viele Entwickler haben HoloToolkit zuvor verwendet, um Umgebungen zu überprüfen und RAUM-Dateien zu erstellen. Das Mixed Reality Toolkit unterstützt jetzt das Importieren dieser Dateien als GameObjects in Unity und deren Verwendung als *Spatial Mesh-Objekte* im Beobachter.

## <a name="see-also"></a>Weitere Informationen

- [Profiles](../profiles/profiles.md)
- [Mixed Reality Toolkit-Profilkonfigurationshandbuch](../../configuration/mixed-reality-configuration-guide.md)
- [Erste Schritte mit räumlichem Bewusstsein](spatial-awareness-getting-started.md)
- [Konfigurieren von Gitternetzbeobachtern auf dem Gerät](configuring-spatial-awareness-mesh-observer.md)
- [Konfigurieren von Mesh-Beobachtern per Code](usage-guide.md)
- [Verwenden des Windows-Geräteportals](/windows/mixed-reality/using-the-windows-device-portal)