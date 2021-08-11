---
title: 'Räumliche Wahrnehmung: Erste Schritte'
description: beschreibt räumliche Wahrnehmung in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: bbe5b923ea7da965424e7fac98adca180c6f91d0c9b4c4ca7a0477e301c362f9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115204328"
---
# <a name="spatial-awareness-getting-started"></a>Räumliche Wahrnehmung: Erste Schritte

![Räumliche Wahrnehmung](../images/spatial-awareness/MRTK_SpatialAwareness_Main.png)

Das Spatial Awareness-System bietet umgebungsbezogenes Bewusstsein in Mixed Reality-Anwendungen. Bei der Einführung in Microsoft HoloLens bot räumliches Bewusstsein eine Sammlung von Gitternetzen, die die Geometrie der Umgebung darstellten, die überzeugende Interaktionen zwischen Hologrammen und der realen Welt ermöglichte.

> [!NOTE]
> Derzeit wird das Mixed Reality Toolkit nicht mit Spatial Understanding-Algorithmen geliefert, die ursprünglich im HoloToolkit gepackt wurden. Spatial Understanding umfasst im Allgemeinen die Transformation räumlicher Gitternetzdaten, um vereinfachte und/oder gruppierte Gitternetzdaten wie Ebenen, Wände, Etagen, Decken usw. zu erstellen.

## <a name="getting-started"></a>Erste Schritte

Das Hinzufügen von Unterstützung für räumliche Wahrnehmung erfordert zwei Hauptkomponenten des Mixed Reality Toolkits: das Spatial Awareness-System und einen unterstützten Plattformanbieter.

1. [Aktivieren](#enable-the-spatial-awareness-system) des Systems für räumliche Wahrnehmung
2. [Registrieren](#register-observers) und [Konfigurieren](configuring-spatial-awareness-mesh-observer.md) von raumbezogenen Beobachtern zum Bereitstellen von Gitternetzdaten
3. [Erstellen und Bereitstellen](#build-and-deploy) auf einer Plattform, die räumliche Wahrnehmung unterstützt

### <a name="enable-the-spatial-awareness-system"></a>Aktivieren des Räumlichen Wahrnehmungssystems

Das Spatial Awareness-System wird vom MixedRealityToolkit-Objekt (oder einer anderen [Dienstregistrierungskomponente)](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) verwaltet. Führen Sie die folgenden Schritte aus, um das *Spatial Awareness-System* im *MixedRealityToolkit-Profil* zu aktivieren oder zu deaktivieren.

Das Mixed Reality Toolkit enthält einige vorkonfigurierte Standardprofile. Bei einigen dieser Funktionen ist das System für räumliche Wahrnehmung standardmäßig aktiviert oder deaktiviert. Die Absicht dieser Vorkonfiguration, insbesondere bei Deaktiviert, besteht darin, den visuellen Mehraufwand beim Berechnen und Rendern der Gitternetze zu vermeiden.

| Profil | Standardmäßig aktiviertes System |
| --- | --- |
| `DefaultHoloLens1ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens1) | Falsch |
| `DefaultHoloLens2ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens2) | Falsch |
| `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profile) | True |

1. Wählen Sie das MixedRealityToolkit-Objekt in der Szenenhierarchie aus, das im Inspektorbereich geöffnet werden soll.

    ![KONFIGURIERTE MRTK-Szenenhierarchie](../images/MRTK_ConfiguredHierarchy.png)

1. Navigieren Sie zum Abschnitt *Spatial Awareness System ,* und aktivieren Sie *Räumliches Wahrnehmungssystem aktivieren.*

    ![Aktivieren der räumlichen Wahrnehmung](../images/spatial-awareness/MRTKConfig_SpatialAwareness.png)

1. Wählen Sie den gewünschten Implementierungstyp für das Spatial Awareness-System aus. Der [`MixedRealitySpatialAwarenessSystem`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessSystem) ist die standardmäßig bereitgestellte .

    ![Auswählen der Spatial Awareness System-Implementierung](../images/spatial-awareness/SpatialAwarenessSelectSystemType.png)

### <a name="register-observers"></a>Registrieren von Beobachtern

Dienste im Mixed Reality Toolkit können [über Datenanbieter Dienste](../../architecture/systems-extensions-providers.md) verfügen, die den Hauptdienst durch plattformspezifische Daten- und Implementierungssteuerelemente ergänzen. Ein Beispiel hierfür ist das Mixed Reality-Eingabesystem, das [über mehrere Datenanbieter](../input/input-providers.md) verfügt, um Controller- und andere zugehörige Eingabeinformationen von verschiedenen plattformspezifischen APIs abzurufen.

Das Spatial Awareness-System ist ähnlich, da Datenanbieter das System mit Gitterdaten über die reale Welt bereitstellen. Für das Profil räumliche Wahrnehmung muss mindestens ein Spatial Observer registriert sein. Räumliche Beobachter sind im Allgemeinen plattformspezifische Komponenten, die als Anbieter für die Erkennung verschiedener Arten von Meshdaten von einem plattformspezifischen Endpunkt (d. h. HoloLens).

1. Öffnen oder Erweitern des *Profils "Spatial Awareness System"*

    ![Spatial Awareness System Profile](../images/spatial-awareness/SpatialAwarenessProfile.png)

1. Klicken Sie auf die Schaltfläche *"Räumlichen Beobachter hinzufügen".*
1. Auswählen des gewünschten *Implementierungstyps für räumliche Beobachter*

    ![Auswählen der Spatial Observer-Implementierung](../images/spatial-awareness/SpatialAwarenessSelectObserver.png)

1. [Ändern der Konfigurationseigenschaften für den Beobachter](configuring-spatial-awareness-mesh-observer.md) nach Bedarf

> [!NOTE]
> Benutzer von `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profile) haben das Spatial Awareness-System für die Windows Mixed Reality Plattform vorkonfiguriert, die die [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) -Klasse verwendet.

### <a name="build-and-deploy"></a>Erstellen und Bereitstellen

Nachdem das System für räumliche Wahrnehmung mit den gewünschten Beobachtern konfiguriert wurde, kann das Projekt erstellt und auf der Zielplattform bereitgestellt werden.

> [!IMPORTANT]
> Wenn sie auf die Windows Mixed Reality-Plattform ausgerichtet ist (z. B. HoloLens), ist es wichtig sicherzustellen, dass die [Spatial Perception-Funktion](/windows/mixed-reality/spatial-mapping-in-unity) aktiviert ist, um das Spatial Awareness-System auf dem Gerät zu verwenden.

> [!WARNING]
> Einige Plattformen, einschließlich Microsoft HoloLens, bieten Unterstützung für die Remoteausführung innerhalb von Unity. Dieses Feature ermöglicht schnelle Entwicklung und Tests, ohne dass der Build- und Bereitstellungsschritt erforderlich ist. Stellen Sie sicher, dass Sie abschließende Akzeptanztests mithilfe einer erstellten und bereitgestellten Version der Anwendung durchführen, die auf der Zielhardware und -plattform ausgeführt wird.

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie die oben beschriebenen Verfahren ausgeführt haben, um das Spatial Awareness-System zu aktivieren, kann das System ausführlicher konfiguriert und gesteuert werden.

Informationen zum Konfigurieren von Beobachtern im Inspektor:

- [Konfigurieren von Beobachtern für die Gerätenutzung](configuring-spatial-awareness-mesh-observer.md)
- [Konfigurieren von Beobachtern für die Verwendung im Editor](spatial-object-mesh-observer.md)

Informationen zum Steuern und Erweitern von Beobachtern über Code:

- [Konfigurieren von Beobachtern über Code](usage-guide.md)
- [Erstellen eines benutzerdefinierten Beobachters](create-data-provider.md)

## <a name="see-also"></a>Siehe auch

- [Dokumentation zur Spatial Awareness-API](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness)
- [Übersicht über räumliche Zuordnungen WMR](/windows/mixed-reality/spatial-mapping)
- [Räumliche Zuordnung in Unity WMR](/windows/mixed-reality/spatial-mapping-in-unity)
