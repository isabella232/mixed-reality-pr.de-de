---
title: Übersicht über die Architektur
description: Architekturübersicht über MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK-Architektur,
ms.openlocfilehash: 7113ee68a3d8bae016236996725a879c95e31f410cb273184ddcc255ae7a0685
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115186600"
---
# <a name="architecture-overview"></a>Übersicht über die Architektur

Für eine allgemeine Einführung in den Inhalt des MRTK helfen Ihnen die in diesem Dokument enthaltenen Architekturinformationen, Folgendes zu verstehen:

- Große Teile des MRTK und deren Verbindung
- Von MRTK eingeführte Konzepte, die in Unity möglicherweise nicht vorhanden sind
- Funktionsweise einiger der größeren Systeme (z. B. Eingabe)

In diesem Abschnitt soll Ihnen nicht vermittelt werden, wie Aufgaben auszuführen sind, sondern wie diese Aufgaben strukturiert sind und warum.

## <a name="many-audiences-one-toolkit"></a>Viele Zielgruppen, ein Toolkit

MRTK hat keine einzige, einheitliche Zielgruppe. Es wurde geschrieben, um Anwendungsfälle zu unterstützen, die von erstmaligen Hackathons bis hin zu Einzelpersonen reichen, die komplexe, freigegebene Erfahrungen für Unternehmen erstellen. Möglicherweise wurden Code und APIs geschrieben, die für eine mehr als die andere optimiert sind (d. h., einige Teile des MRTK scheinen für "One-Click-Konfiguration" optimiert zu sein), aber es ist wichtig zu beachten, dass einige davon eher aus historischen und wiederverwendenden Gründen erfolgen. Mit der Weiterentwicklung des MRTK sollten die erstellten Features so entworfen werden, dass sie skaliert werden, um die Verschiedenen Anwendungsfälle zu unterstützen.

MRTK verfügt auch über Anforderungen für die ordnungsgemäßen Skalierung über VR- und AR-Umgebungen hinweg. Es sollte einfach sein, Anwendungen zu erstellen, die bei der Bereitstellung auf einem HoloLens 2 ODER einem HoloLens 1 ordnungsgemäß ein Fallback im Verhalten haben, und es sollte einfach sein, Anwendungen zu erstellen, die auf OpenVR und WMR (und andere Plattformen) ausgerichtet sind. Obwohl das Team manchmal eine bestimmte Iteration auf ein bestimmtes System oder eine bestimmte Plattform ausrichten kann, besteht das langfristige Ziel darin, ein breites Spektrum an Unterstützung für den Ort zu entwickeln, an dem Menschen Mixed Reality-Erfahrungen erstellen.

## <a name="high-level-breakdown"></a>Aufschlüsselung auf hoher Ebene

Das MRTK ist sowohl eine Sammlung von Tools zum schnellen Starten von Mixed Reality-Erfahrungen (MR) als auch ein Anwendungsframework mit Ansichten zur eigenen Laufzeit, wie es erweitert werden sollte und wie es konfiguriert werden sollte.

Auf hoher Ebene kann das MRTK wie folgt unterteilt werden:

![Architekturübersichtsdiagramm](../features/images/architecture/MRTK_Architecture.png)

Das MRTK enthält auch einen weiteren Satz von Grab-Bag-Hilfsprogrammen, die nur wenige oder gar keine Abhängigkeiten vom restlichen MRTK aufweisen (um einige aufzulisten: Buildtools, Solver, Audioeinflusser, Glättungshilfsprogramme und Zeilenrenderer).

Der Rest der Architekturdokumentation wird von unten nach oben erstellt, beginnend mit dem Framework und der Laufzeit bis hin zu interessanteren und komplexeren Systemen, z. B. Eingaben. Lesen Sie das Inhaltsverzeichnis, um mit der Architekturübersicht fortzufahren.
