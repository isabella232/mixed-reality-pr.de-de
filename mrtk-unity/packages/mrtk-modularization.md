---
title: MRTK-Modularisierung
description: Beschreibt die Komponentenisierung in MRTK.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 04b2e6155e591a918b95aed20961a0450afe5f43
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144419"
---
# <a name="mixed-reality-toolkit-componentization"></a>Mixed Reality Toolkit-Komponenten

Eines der hervorragenden neuen Features von Mixed Reality Toolkit v2 ist die verbesserte Komponentenisierung. Nach Möglichkeit sind einzelne Komponenten von allen Komponenten bis auf die Kernebene der Grundlage isoliert.

## <a name="minimized-dependencies"></a>Minimierte Abhängigkeiten

MRTK v2 wurde absichtlich entwickelt, um modular zu sein und Abhängigkeiten zwischen Systemdiensten zu minimieren (z. B. räumliche Wahrnehmung).

Aufgrund der Art einiger Systemdienste (z. B. Eingabe und Teleportierung) gibt es eine kleine Anzahl von Abhängigkeiten.

Es ist zwar zu erwarten, dass Dienste eine oder mehrere Datenanbieterkomponenten benötigen, es gibt jedoch keine direkten Verknüpfungen zwischen ihnen. Dasselbe gilt für SDK-Features (z. B. Benutzeroberfläche Komponenten).

## <a name="component-communication"></a>Komponentenkommunikation

Um sicherzustellen, dass es keine direkten Verknüpfungen zwischen Komponenten gibt, verwendet MRTK v2 Schnittstellen für die Kommunikation zwischen Diensten, Datenanbietern und Anwendungscode. Diese Schnittstellen werden in definiert, und die gesamte Kommunikation wird über die Mixed Reality Toolkit-Kernkomponente geleitet.

![Verwenden des Räumlichen Wahrnehmungssystems über Schnittstellen](../features/images/packaging/AccessingViaInterfaces.png)

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

Das MRTK bietet Unterstützung für die Entwicklung von Anwendungen mit einer Vielzahl von Architekturen, einschließlich:

- [MixedRealityToolkit-Dienstlocator](#mixedrealitytoolkit-service-locator)
- [Einzelne Dienste](#individual-service-components)
- [Benutzerdefinierter Dienstlocator](#custom-service-locator)
- [Hybridarchitektur](#hybrid-architecture)

Bei der Auswahl einer Anwendungsarchitektur ist es wichtig, Entwurfsflexibilität und Anwendungsleistung zu berücksichtigen. Es wird nicht erwartet, dass die hier beschriebenen Architekturen für jede Anwendung geeignet sind.

#### <a name="mixedrealitytoolkit-service-locator"></a>MixedRealityToolkit-Dienstlocator

Das MRTK ermöglicht (und konfiguriert) Anwendungsszenen automatisch, um die Standardmäßige [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) Dienstlocatorkomponente zu verwenden. Diese Komponente bietet Unterstützung für die Konfiguration von MRTK-Systemen und -Datenanbietern über Konfigurationsinspektoren und verwaltet die Lebensdauer und das Kernverhalten von Komponenten (z. B. wann aktualisiert werden soll).

Alle Systeme werden im Hauptkonfigurationsinspektor dargestellt, unabhängig davon, ob sie im Projekt vorhanden oder aktiviert sind. Weitere Informationen finden [Sie Mixed Reality-Konfigurationshandbuch.](../configuration/mixed-reality-configuration-guide.md)

#### <a name="individual-service-components"></a>Einzelne Dienstkomponenten

Einige Entwickler haben den Wunsch ausgedrückt, einzelne Dienstkomponenten in die Anwendungsszenenhierarchie ein-/ausdingen zu können. Um diese Nutzung zu ermöglichen, müssen Dienste entweder in einer benutzerdefinierten Registrierungsstelle gekapselt werden oder sich selbst registrieren/selbst verwalten.

Ein selbstregistrierungsdienst würde implementieren und sich selbst registrieren, damit der Anwendungscode die Dienstinstanz über [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) eine Registrierung entdecken kann.

Ein Selbstverwaltungsdienst kann als Singletonobjekt in der Szenenhierarchie implementiert werden. Dieses Objekt stellt die Instanzeigenschaft und zur Verfügung, mit der Anwendungscode direkt auf die Dienstfunktionalität zugreifen kann.

#### <a name="custom-service-locator"></a>Benutzerdefinierter Dienstlocator

Einige Entwickler haben die Möglichkeit angefordert, eine benutzerdefinierte Dienstlocatorkomponente zu erstellen. Benutzerdefinierte Dienstlocator implementieren die -Schnittstelle und verwalten den Lebenszyklus und das [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) Kernverhalten aktiver Dienste.

#### <a name="hybrid-architecture"></a>Hybridarchitektur

Das MRTK unterstützt eine Hybridarchitektur, in der Entwickler die vorherigen Ansätze nach Bedarf oder wunsch kombinieren können. Beispielsweise könnte ein Entwickler mit dem [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) Dienstlocator beginnen und einen selbstregistrierungsbasierten Dienst hinzufügen.

> [!NOTE]
> Wenn Sie sich für eine Hybridarchitektur entscheiden, ist es wichtig, jede Duplizierung der Arbeit zu berücksichtigen (z. B. das Abrufen von Controllerdaten von mehreren Komponenten).
