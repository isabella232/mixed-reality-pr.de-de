---
title: Beobachter für räumliches Objektgittermodell
description: Dokumentation zu Spatial Mesh Observer in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: db0b2f14d0a5d65140223d3fa3f4f5324ef2ba76
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176697"
---
# <a name="spatial-object-mesh-observer"></a>Beobachter für räumliches Objektgittermodell

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

    ![Wählen Sie Spatial Object Mesh Observer (Beobachter für räumliches Objektgittermodell) aus.](../images/spatial-awareness/SelectObjectObserver.png)

1. Wählen Sie das gewünschte *Spatial Mesh-Objekt aus.* Standardmäßig wird der Beobachter mit einem Beispielmodell konfiguriert. Dieses Modell wurde mit einem Microsoft HoloLens erstellt, aber es ist [möglich, ein neues Scannetzobjekt](#acquiring-environment-scans)zu erstellen.
1. [Konfigurieren der restlichen Mesh Observer-Profileigenschaften](configuring-spatial-awareness-mesh-observer.md)

    ![Wählen Sie das Mesh-Objekt aus.](../images/spatial-awareness/ObjectObserverProfile.png)

### <a name="spatial-object-mesh-observer-profile-notes"></a>Hinweise zum Spatial Object Mesh-Beobachterprofil

Da der *Spatial Object Mesh Observer* Daten aus einem 3D-Modell lädt, berücksichtigt er einige der standard mesh observer-Einstellungen, die unten beschrieben sind, nicht.

**Aktualisierungsintervall**

Der  *Spatial Object Mesh Observer* sendet alle Gittermodelle an eine Anwendung, wenn das Modell geladen wird. Zeitdelta zwischen Updates werden nicht simuliert. Eine Anwendung kann die Meshereignisse erneut empfangen, indem [`myObserver.ClearObservation()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.ClearObservations) sie und aufruft. [`myObserver.Resume()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume)

**Ist stationärer Beobachter**

Der *Spatial Object Mesh Observer* betrachtet alle 3D-Gittermodellobjekte als stationär und ignoriert den Ursprung.

**Observer-Form und -Erweiterungen**

Der  *Spatial Object Mesh Observer* sendet das gesamte 3D-Gittermodell an die Anwendung. Beobachterform und -werte werden nicht berücksichtigt.

**Detail- und Dreiecksebene/Kubische Verbrauchsmenge**

Der Observer versucht beim Senden der Gittermodelle an die Anwendung nicht, 3D-Modell-LODs zu finden.

## <a name="acquiring-environment-scans"></a>Abrufen von Umgebungsscans

In diesem Abschnitt werden zusätzliche Informationen zum Erstellen und Sammeln *von Spatial Mesh-Objektdateien* für die Verwendung mit dem *Spatial Object Mesh Observer beschrieben.*

### <a name="windows-device-portal"></a>Windows-Geräteportal

Die [Windows Geräteportal](/windows/mixed-reality/using-the-windows-device-portal) kann verwendet werden, um das räumliche Gitternetz als OBJ-Datei von einem Microsoft HoloLens Gerät herunterzuladen.

1. Überprüfen Sie einfach, indem Sie die gewünschte Umgebung mit einem HoloLens
1. Verbinden mithilfe des Windows Geräteportal zum HoloLens
1. Navigieren Zur Seite *"3D-Ansicht"*
1. Klicken Sie im Abschnitt *Räumliche Zuordnung* auf die Schaltfläche *Aktualisieren.*
1. Klicken Sie im Abschnitt *Räumliche Zuordnung* auf die Schaltfläche *Speichern,* um die Obj-Datei auf dem PC zu speichern.

> [!NOTE]
> **HoloToolkit-ROOM-Dateien**
>
> Viele Entwickler haben zuvor HoloToolkit verwendet, um Umgebungen zu überprüfen und ROOM-Dateien zu erstellen. Das Mixed Reality Toolkit unterstützt jetzt das Importieren dieser Dateien als GameObjects in Unity und deren Verwendung als *Spatial Mesh Objects* im Beobachter.

## <a name="see-also"></a>Siehe auch

- [Profiles](../profiles/profiles.md)
- [Konfigurationshandbuch für Mixed Reality Toolkit-Profil](../../configuration/mixed-reality-configuration-guide.md)
- [Erste Schritte mit räumlichem Bewusstsein](spatial-awareness-getting-started.md)
- [Konfigurieren von Mesh-Beobachtern auf dem Gerät](configuring-spatial-awareness-mesh-observer.md)
- [Konfigurieren von Mesh-Beobachtern über Code](usage-guide.md)
- [Verwenden des Windows-Geräteportals](/windows/mixed-reality/using-the-windows-device-portal)
