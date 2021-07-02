---
title: MRTK-Modularisierung
description: Beschreibt die Komponentenisierung in MRTK.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: eac96e309afc21f9a2b6efe9c3aef5975e4f0dff
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177014"
---
# <a name="mrtk-modularization"></a>MRTK-Modularisierung

Eines der großartigen neuen Features von Mixed Reality Toolkit v2 ist die verbesserte Komponentenisierung. Wenn möglich, werden einzelne Komponenten von allen Komponenten isoliert, mit Der Kernebene der Grundlage abgesehen.

## <a name="minimized-dependencies"></a>Minimierte Abhängigkeiten

MRTK v2 wurde absichtlich entwickelt, um modular zu sein und Abhängigkeiten zwischen Systemdiensten (z. B. räumliche Wahrnehmung) zu minimieren.

Aufgrund der Art einiger Systemdienste (z. B. Eingabe und Teleportation) gibt es eine kleine Anzahl von Abhängigkeiten.

Es wird zwar erwartet, dass Dienste eine oder mehrere Datenanbieterkomponenten benötigen, es gibt jedoch keine direkten Verknüpfungen zwischen ihnen. Dasselbe gilt für SDK-Features (z. B. Benutzeroberfläche Komponenten).

## <a name="component-communication"></a>Komponentenkommunikation

Um sicherzustellen, dass keine direkten Links zwischen Komponenten verfügbar sind, verwendet MRTK v2 Schnittstellen für die Kommunikation zwischen Diensten, Datenanbietern und Anwendungscode. Diese Schnittstellen werden in definiert, und die gesamte Kommunikation wird über die Mixed Reality Toolkit-Kernkomponente geroutet.

![Verwenden des Systems für räumliche Wahrnehmung über Schnittstellen](../features/images/packaging/AccessingViaInterfaces.png)

## <a name="minimizing-mrtk-import-footprint"></a>Minimieren des MRTK-Importbedarfs

Zu diesem Zeitpunkt wird das MRTK als einzelnes Basispaket importiert (das Vorhandensein des Beispielpakets wird für einen Moment ignoriert, bei dem es sich um ein vollständig optionales Paket handelt). Es ist möglich, diesen Speicherbedarf zu verkleinern, indem Sie die importierten Dateien manuell reduzieren. Dies ist jedoch ein sehr manueller Prozess, der keine klar definierte Anleitung enthält.

Es ist möglich, während des Imports des Foundation-Pakets beliebige Elemente zu deaktivieren. Es wird jedoch nicht empfohlen, dies zu einem frühen Zeitpunkt in der Entwicklung zu tun, da dies die Funktionalität möglicherweise unterbricht. Nachdem Sie den endgültigen Funktionssatz einer App festgelegt haben, können nicht mehr nutzte Anbieter und Dienste in den folgenden Ordnern beschnitten werden:

- MRTK/Dienste
- MRTK/Providers
- MRTK/SDK/Features

> [!NOTE]
> MRTK v2.x **_erfordert_** den Inhalt des Ordners Assets/MRTK/Core.

## <a name="upcoming-features"></a>Nächste Features

### <a name="application-architecture"></a>Anwendungsarchitektur

Das MRTK wird unterstützt, um die Entwicklung von Anwendungen mit einer Vielzahl von Architekturen zu ermöglichen, einschließlich:

- [MixedRealityToolkit-Dienstlocator](#mixedrealitytoolkit-service-locator)
- [Einzelne Dienste](#individual-service-components)
- [Benutzerdefinierter Dienstlocator](#custom-service-locator)
- [Hybridarchitektur](#hybrid-architecture)

Bei der Auswahl einer Anwendungsarchitektur ist es wichtig, Entwurfsflexibilität und Anwendungsleistung zu berücksichtigen. Es wird nicht erwartet, dass die hier beschriebenen Architekturen für jede Anwendung geeignet sind.

#### <a name="mixedrealitytoolkit-service-locator"></a>MixedRealityToolkit-Dienstlocator

Das MRTK ermöglicht (und konfiguriert) Anwendungsszenen automatisch, um die Standardmäßige [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) Dienstlocatorkomponente zu verwenden. Diese Komponente bietet Unterstützung für die Konfiguration von MRTK-Systemen und -Datenanbietern über Konfigurationsinspektoren und verwaltet die Lebensdauer und das Kernverhalten von Komponenten (z. B. wann sie aktualisiert werden sollten).

Alle Systeme werden im Hauptkonfigurationsinspektor dargestellt, unabhängig davon, ob sie im Projekt vorhanden oder aktiviert sind. Weitere Informationen finden [Mixed Reality Konfigurationshandbuch.](../configuration/mixed-reality-configuration-guide.md)

#### <a name="individual-service-components"></a>Einzelne Dienstkomponenten

Einige Entwickler haben den Wunsch ausgedrückt, einzelne Dienstkomponenten in die Anwendungsszenenhierarchie ein-/ausdingen zu können. Um diese Nutzung zu ermöglichen, müssen Dienste entweder in einer benutzerdefinierten Registrierungsstelle gekapselt werden oder sich selbst registrieren/selbst verwalten.

Ein selbstregistrierungsdienst würde implementieren und sich selbst registrieren, damit der Anwendungscode die Dienstinstanz über [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) eine Registrierung entdecken kann.

Ein Selbstverwaltungsdienst kann als Singletonobjekt in der Szenenhierarchie implementiert werden. Dieses Objekt stellt die -Instanzeigenschaft und die -Instanz zur Verfügung, mit der Anwendungscode direkt auf die Dienstfunktionen zugreifen kann.

#### <a name="custom-service-locator"></a>Benutzerdefinierter Dienstlocator

Einige Entwickler haben die Möglichkeit angefordert, eine benutzerdefinierte Dienstlocatorkomponente zu erstellen. Benutzerdefinierte Dienstlocatoren implementieren die -Schnittstelle und verwalten den Lebenszyklus und das [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) Kernverhalten aktiver Dienste.

#### <a name="hybrid-architecture"></a>Hybridarchitektur

Das MRTK unterstützt eine Hybridarchitektur, in der Entwickler die vorherigen Ansätze nach Bedarf oder wunsch kombinieren können. Beispielsweise könnte ein Entwickler mit dem [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) Dienstlocator beginnen und einen selbstregistrierungsbasierten Dienst hinzufügen.

> [!NOTE]
> Wenn Sie sich für eine Hybridarchitektur entscheiden, ist es wichtig, jede Duplizierung der Arbeit zu berücksichtigen (z. B. das Abrufen von Controllerdaten von mehreren Komponenten).
