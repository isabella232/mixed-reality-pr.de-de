---
title: Erste Schritte mit räumlichem Bewusstsein
description: beschreibt räumliche Wahrnehmung im MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 46bb78bc4e2574fd4da14f19edf52624b7b301c2
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176716"
---
# <a name="spatial-awareness-getting-started"></a>Erste Schritte mit räumlichem Bewusstsein

![Räumliche Wahrnehmung](../images/spatial-awareness/MRTK_SpatialAwareness_Main.png)

Das Spatial Awareness-System bietet umgebungsbezogenes Bewusstsein in Mixed Reality-Anwendungen. Bei der Einführung in Microsoft HoloLens bot Spatial Awareness eine Sammlung von Gittern, die die Geometrie der Umgebung darstellen, die überzeugende Interaktionen zwischen Hologrammen und der realen Welt ermöglichte.

> [!NOTE]
> Derzeit wird das Mixed Reality Toolkit nicht mit Spatial Understanding-Algorithmen wie ursprünglich im HoloToolkit gepackt. Spatial Understanding umfasst im Allgemeinen das Transformieren von Spatial Mesh-Daten, um vereinfachte und/oder gruppenvernetzte Daten wie Ebenen, Wände, Boden, Decken usw. zu erstellen.

## <a name="getting-started"></a>Erste Schritte

Zum Hinzufügen von Unterstützung für spatial awareness sind zwei Hauptkomponenten des Mixed Reality Toolkits erforderlich: das Spatial Awareness-System und ein unterstützter Plattformanbieter.

1. [Aktivieren](#enable-the-spatial-awareness-system) des Systems für räumliche Wahrnehmung
2. [Registrieren](#register-observers) und [Konfigurieren eines](configuring-spatial-awareness-mesh-observer.md) oder mehrere räumlicher Beobachter zum Bereitstellen von Gitternetzdaten
3. [Erstellen und Bereitstellen auf](#build-and-deploy) einer Plattform, die räumliche Wahrnehmung unterstützt

### <a name="enable-the-spatial-awareness-system"></a>Aktivieren des Systems für räumliche Wahrnehmung

Das Spatial Awareness-System wird vom MixedRealityToolkit-Objekt (oder einer anderen [Dienstregistrierungskomponente)](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) verwaltet. Führen Sie die folgenden Schritte aus, um das *Spatial Awareness-System im* *MixedRealityToolkit-Profil zu* aktivieren oder zu deaktivieren.

Das Mixed Reality Toolkit enthält einige vorkonfigurierte Standardprofile. Für einige davon ist das Spatial Awareness-System standardmäßig aktiviert oder deaktiviert. Die Absicht dieser Vorkonfiguration, insbesondere für deaktivierte, besteht in der Vermeidung des visuellen Aufwands beim Berechnen und Rendern der Gitternetze.

| Profil | Standardmäßig aktiviertes System |
| --- | --- |
| `DefaultHoloLens1ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens1) | Falsch |
| `DefaultHoloLens2ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens2) | Falsch |
| `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles) | Richtig |

1. Wählen Sie das MixedRealityToolkit-Objekt in der Szenenhierarchie aus, um es im Inspektorbereich zu öffnen.

    ![MRTK– Konfigurierte Szenenhierarchie](../images/MRTK_ConfiguredHierarchy.png)

1. Navigieren Sie zum Abschnitt *Spatial Awareness System,* und aktivieren Sie *Enable Spatial Awareness System (Raumbewusstseinssystem aktivieren).*

    ![Aktivieren der räumlichen Wahrnehmung](../images/spatial-awareness/MRTKConfig_SpatialAwareness.png)

1. Wählen Sie den gewünschten Implementierungstyp des Spatial Awareness-Systems aus. ist [`MixedRealitySpatialAwarenessSystem`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessSystem) die bereitgestellte Standardeinstellung.

    ![Auswählen der Spatial Awareness-Systemimplementierung](../images/spatial-awareness/SpatialAwarenessSelectSystemType.png)

### <a name="register-observers"></a>Registrieren von Beobachtern

Dienste im Mixed Reality Toolkit können [](../../architecture/systems-extensions-providers.md) über Datenanbieter verfügen, die den Hauptdienst durch plattformspezifische Daten und Implementierungssteuerungen ergänzen. Ein Beispiel hierfür ist das Mixed Reality Input [](../input/input-providers.md) System, das über mehrere Datenanbieter verfügt, um Controller- und andere zugehörige Eingabeinformationen von verschiedenen plattformspezifischen APIs zu erhalten.

Das Spatial Awareness-System ist ähnlich, da Datenanbieter dem System Gitternetzdaten über die reale Welt liefern. Für das Profil "Räumliche Wahrnehmung" muss mindestens ein Spatial Observer registriert sein. Raumbeobachter sind in der Regel plattformspezifische Komponenten, die als Anbieter für die Suche nach verschiedenen Arten von Gitterdaten von einem plattformspezifischen Endpunkt (d. h. HoloLens).

1. Öffnen oder Erweitern des *Profils "Spatial Awareness System"*

    ![Profil des Spatial Awareness-Systems](../images/spatial-awareness/SpatialAwarenessProfile.png)

1. Klicken Sie auf *die Schaltfläche "Räumlichen Beobachter hinzufügen".*
1. Auswählen des gewünschten *Implementierungstyps für räumliche Beobachter*

    ![Auswählen der Spatial Observer-Implementierung](../images/spatial-awareness/SpatialAwarenessSelectObserver.png)

1. [Ändern von Konfigurationseigenschaften auf dem Beobachter](configuring-spatial-awareness-mesh-observer.md) nach Bedarf

> [!NOTE]
> Benutzer von `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles) verfügen über ein vorkonfiguriertes Spatial Awareness-System für die Windows Mixed Reality-Plattform, die die -Klasse [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) verwendet.

### <a name="build-and-deploy"></a>Erstellen und Bereitstellen

Sobald das Spatial Awareness-System mit den gewünschten Beobachtern konfiguriert wurde, kann das Projekt erstellt und auf der Zielplattform bereitgestellt werden.

> [!IMPORTANT]
> Wenn sie auf die Windows Mixed Reality-Plattform (z. B. HoloLens) abzielen, ist es wichtig sicherzustellen, dass die Spatial [Perception-Funktion](/windows/mixed-reality/spatial-mapping-in-unity) aktiviert ist, um das Spatial Awareness-System auf dem Gerät zu verwenden.

> [!WARNING]
> Einige Plattformen, einschließlich Microsoft HoloLens, bieten Unterstützung für die Remoteausführung innerhalb von Unity. Dieses Feature ermöglicht schnelle Entwicklung und Tests, ohne dass der Build- und Bereitstellungsschritt erforderlich ist. Stellen Sie sicher, dass Sie abschließende Akzeptanztests mit einer erstellten und bereitgestellten Version der Anwendung durchführen, die auf der Zielhardware und -plattform ausgeführt wird.

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie die oben beschriebenen Verfahren zum Aktivieren des Spatial Awareness-Systems durchgeführt haben, kann das System ausführlicher konfiguriert und gesteuert werden.

Informationen zum Konfigurieren von Beobachtern im Inspektor:

- [Konfigurieren von Beobachtern für bei der Gerätenutzung](configuring-spatial-awareness-mesh-observer.md)
- [Konfigurieren von Beobachtern für die Verwendung im Editor](spatial-object-mesh-observer.md)

Informationen zum Steuern und Erweitern von Beobachtern über Code:

- [Konfigurieren von Beobachtern über Code](usage-guide.md)
- [Erstellen eines benutzerdefinierten Beobachters](create-data-provider.md)

## <a name="see-also"></a>Siehe auch

- [Dokumentation zur Spatial Awareness-API](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness)
- [Übersicht über spatial mapping WMR](/windows/mixed-reality/spatial-mapping)
- [Räumliche Zuordnung in Unity WMR](/windows/mixed-reality/spatial-mapping-in-unity)
