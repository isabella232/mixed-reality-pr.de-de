---
title: MRTK-Modularisierung
description: Beschreibt die Komponentenisierung in MRTK.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 1c32486c83eda9b99540d1719753977b6cdb2d18735e799dcd6c2ca3fcf200ce
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203621"
---
# <a name="mrtk-modularization"></a>MRTK-Modularisierung

Eines der hervorragenden neuen Features von Mixed Reality Toolkit v2 ist die verbesserte Komponentenisierung. Nach Möglichkeit sind einzelne Komponenten von allen Komponenten bis auf die Kernebene der Grundlage isoliert.

## <a name="minimized-dependencies"></a>Minimierte Abhängigkeiten

MRTK v2 wurde absichtlich entwickelt, um modular zu sein und Abhängigkeiten zwischen Systemdiensten zu minimieren (z. B. räumliche Wahrnehmung).

Aufgrund der Art einiger Systemdienste (z. B. Eingabe und Teleportierung) gibt es eine kleine Anzahl von Abhängigkeiten.

Es ist zwar zu erwarten, dass Dienste eine oder mehrere Datenanbieterkomponenten benötigen, es gibt jedoch keine direkten Verknüpfungen zwischen ihnen. Dasselbe gilt für SDK-Features (z. B. Benutzeroberfläche Komponenten).

## <a name="component-communication"></a>Komponentenkommunikation

Um sicherzustellen, dass es keine direkten Verknüpfungen zwischen Komponenten gibt, verwendet MRTK v2 Schnittstellen für die Kommunikation zwischen Diensten, Datenanbietern und Anwendungscode. Diese Schnittstellen werden in definiert, und die gesamte Kommunikation wird über die Mixed Reality Toolkit-Kernkomponente geleitet.

![Verwenden des Systems für räumliche Wahrnehmung über Schnittstellen](../features/images/packaging/AccessingViaInterfaces.png)

## <a name="minimizing-mrtk-import-footprint"></a>Minimieren des MRTK-Importbedarfs

Derzeit wird das MRTK als einzelnes Basispaket importiert (wobei das Vorhandensein des Beispielpakets, das ein vollständig optionales Paket ist, für einen Moment ignoriert wird). Es ist möglich, diesen Speicherbedarf zu verringern, indem Sie die importierten Dateien manuell reduzieren. Dies ist jedoch ein sehr manueller Prozess, der keine genau definierte Anleitung enthält.

Es ist möglich, beliebige Elemente während des Imports des Foundation-Pakets zu deaktivieren. Es wird jedoch nicht empfohlen, dies zu einem frühen Zeitpunkt in der Entwicklung zu tun, da dies die Funktionalität beeinträchtigen kann. Nachdem Sie den endgültigen Featuresatz einer App herausgefunden haben, können Sie nicht benötigte Anbieter und Dienste in den folgenden Ordnern löschen:

- MRTK/Services
- MRTK/Providers
- MRTK/SDK/Features

> [!NOTE]
> MRTK v2.x **_erfordert_** den Inhalt des Ordners Assets/MRTK/Core.

## <a name="upcoming-features"></a>Nächste Features

### <a name="application-architecture"></a>Anwendungsarchitektur

Das MRTK wird Unterstützung bieten, damit Anwendungen mit einer Vielzahl von Architekturen erstellt werden können, einschließlich:

- [MixedRealityToolkit-Dienstlocator](#mixedrealitytoolkit-service-locator)
- [Einzelne Dienste](#individual-service-components)
- [Benutzerdefinierter Dienstlocator](#custom-service-locator)
- [Hybridarchitektur](#hybrid-architecture)

Bei der Auswahl einer Anwendungsarchitektur ist es wichtig, Entwurfsflexibilität und Anwendungsleistung zu berücksichtigen. Es wird nicht erwartet, dass die hier beschriebenen Architekturen für jede Anwendung geeignet sind.

#### <a name="mixedrealitytoolkit-service-locator"></a>MixedRealityToolkit-Dienstlocator

Das MRTK aktiviert (und konfiguriert automatisch) Anwendungsszenen, um die Standardmäßige [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) Dienstlocatorkomponente zu verwenden. Diese Komponente umfasst Unterstützung für die Konfiguration von MRTK-Systemen und -Datenanbietern über Konfigurationsinspektoren und verwaltet die Lebensdauer und das Kernverhalten von Komponenten (z. B. zeitpunkt der Aktualisierung).

Alle Systeme werden im Hauptkonfigurationsinspektor dargestellt, unabhängig davon, ob sie im Projekt vorhanden oder aktiviert sind. Weitere Informationen finden Sie im [Mixed Reality-Konfigurationshandbuch.](../configuration/mixed-reality-configuration-guide.md)

#### <a name="individual-service-components"></a>Einzelne Dienstkomponenten

Einige Entwickler haben den Wunsch ausgedrückt, einzelne Dienstkomponenten in die Hierarchie der Anwendungsszene aufzunehmen. Um diese Nutzung zu ermöglichen, müssen Dienste entweder in einer benutzerdefinierten Registrierungsstelle gekapselt oder selbstregistriert/selbst verwaltet werden.

Ein selbst registrierender Dienst implementiert und [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) registriert sich selbst, sodass Anwendungscode die Dienstinstanz über eine Registrierung ermitteln kann.

Ein Selbstverwaltungsdienst kann als Singletonobjekt in der Szenenhierarchie implementiert werden. Dieses Objekt würde die Instanzeigenschaft und bereitstellen, die Anwendungscode verwenden kann, um direkt auf die Dienstfunktionalität zuzugreifen.

#### <a name="custom-service-locator"></a>Benutzerdefinierter Dienstlocator

Einige Entwickler haben die Möglichkeit angefordert, eine benutzerdefinierte Dienstlocatorkomponente zu erstellen. Benutzerdefinierte Dienstlocators implementieren die [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) -Schnittstelle und verwalten den Lebenszyklus und das Kernverhalten aktiver Dienste.

#### <a name="hybrid-architecture"></a>Hybridarchitektur

Das MRTK unterstützt eine Hybridarchitektur, in der Entwickler die vorherigen Ansätze nach Bedarf oder nach Bedarf kombinieren können. Beispielsweise könnte ein Entwickler mit dem [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) Dienstlocator beginnen und einen selbst registrierenden Dienst hinzufügen.

> [!NOTE]
> Wenn Sie sich für eine Hybridarchitektur entscheiden, ist es wichtig, auf jede Duplizierung von Arbeit zu achten (z. B. das Abrufen von Controllerdaten aus mehreren Komponenten).
