---
title: Übersicht über die Architektur
description: Übersicht über die Architektur des MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK-Architektur,
ms.openlocfilehash: 431e091cb6dc0efa0f941b95f58811d57166c82f
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281911"
---
# <a name="architecture-overview"></a>Übersicht über die Architektur

Für eine allgemeine Einführung in den Inhalt des MRTK helfen Ihnen die in diesem Dokument enthaltenen Architekturinformationen dabei, Folgendes zu verstehen:

- Große Teile des MRTK und wie sie eine Verbindung herstellen
- Konzepte, die MRTK ein einführen kann, die in Unity möglicherweise nicht vorhanden sind
- Funktionsweise einiger größerer Systeme (z. B. Eingabe)

Dieser Abschnitt soll Ihnen nicht vermitteln, wie Sie Aufgaben ausführen, sondern wie diese Aufgaben strukturiert sind und warum.

## <a name="many-audiences-one-toolkit"></a>Viele Zielgruppen, ein Toolkit

MRTK hat keine einzelne, einheitliche Zielgruppe. Es wurde geschrieben, um Anwendungsfälle zu unterstützen, die von erstmaligen Hackathons bis hin zu Personen reichen, die komplexe, gemeinsame Erfahrungen für Unternehmen erstellen. Möglicherweise wurden Code und APIs geschrieben, die für einen mehr als den anderen optimiert sind (d. h., einige Teile des MRTK scheinen besser für "1-Klick-Konfiguration" optimiert zu sein), aber es ist wichtig zu beachten, dass einige davon eher aus historischen gründen oder aus Gründen der Resourcing verwendet werden. Mit der Weiterentwicklung des MRTK sollten die features, die erstellt werden, so skaliert werden, dass sie die Bandbreite von Anwendungsfällen unterstützen.

MRTK verfügt auch über Anforderungen für eine ordnungsgemäß skalieren vr- und AR-Umgebung. Es sollte einfach sein, Anwendungen zu erstellen, die bei der Bereitstellung auf einer HoloLens 2 oder einer HoloLens 1 ordnungsgemäß ein Fallback im Verhalten ermöglichen, und es sollte einfach sein, Anwendungen für OpenVR und WMR (und andere Plattformen) zu erstellen. Manchmal kann sich das Team auf eine bestimmte Iteration auf ein bestimmtes System oder eine bestimmte Plattform konzentrieren, aber das langfristige Ziel besteht im Aufbau eines breiten Spektrums an Unterstützung für den Ort, an dem Menschen Mixed Reality-Erfahrungen erstellen.

## <a name="high-level-breakdown"></a>Aufschlüsselung auf hoher Ebene

Das MRTK ist sowohl eine Sammlung von Tools, um Mixed Reality-Erfahrungen (MR) schnell in die Praxis zu bringen, als auch ein Anwendungsframework mit Ansichten zur eigenen Laufzeit, wie es erweitert werden sollte und wie es konfiguriert werden sollte.

Auf hoher Ebene kann das MRTK wie folgt aufgeschlüsselt werden:

![Übersichtsdiagramm zur Architektur](../features/images/architecture/MRTK_Architecture.png)

Das MRTK enthält auch einen weiteren Satz von Greifschnabel-Hilfsprogrammen, die nur wenig bis gar keine Abhängigkeiten vom Rest des MRTK aufweisen (um einige auflisten zu können: Buildtools, Solver, Audioeinflusser, Glättungs-Hilfsprogramme und Linienrenderer).

Der Rest der Architekturdokumentation wird von unten nach oben erstellt, beginnend mit dem Framework und der Runtime, und es wird zu interessanteren und komplexeren Systemen, z. B. Eingaben, entwickelt. Lesen Sie das Inhaltsverzeichnis, um mit der Architekturübersicht fortzufahren.
