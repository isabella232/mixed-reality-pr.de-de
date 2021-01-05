---
title: Typen von Mixed Reality-apps
description: Erfahren Sie mehr über das Spektrum der Erfahrungen, die die Mixed Reality-Plattform unterstützen kann, von vollständig immersiven Umgebungen bis hin zu hellen Informationen über die aktuelle Umgebung eines Benutzers.
author: rwinj
ms.author: willyang
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Design, App Patterns, Mixed Reality Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens
ms.openlocfilehash: 8c9a051ff0b80461fe590efa37593bddb01c0e63
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848105"
---
# <a name="types-of-mixed-reality-apps"></a>Typen von Mixed Reality-apps

Einer der Vorteile bei der Entwicklung von Apps für Windows Mixed Reality ist das Spektrum der Benutzeroberflächen, die die Plattform unterstützen kann. Von vollständig immersiven virtuellen Umgebungen bis zur leichten Überlagerung der aktuellen Umgebung eines Benutzers mit Informationen bietet Windows Mixed Reality eine Sammlung robuster Tools, mit denen sich jede Erfahrung lebendig gestalten lässt. Es ist wichtig, dass ein App-Ersteller frühzeitig im Entwicklungsprozess daran interessiert ist, an welcher Stelle dieses Spektrum liegt. Diese Entscheidung wirkt sich letztendlich sowohl auf die Zusammensetzung des App-Entwurfs als auch auf den technologischen Entwicklungspfad aus.

## <a name="enhanced-environment-apps-hololens-only"></a>Erweiterte Umgebungs-Apps (nur hololens)

Eine der leistungsfähigsten Möglichkeiten, wie gemischte Realität den Wert einbringen kann, ist die Möglichkeit, dass Entwickler digitale Informationen oder Inhalte in der aktuellen Umgebung eines Benutzers platzieren. Diese Vorgehensweise ist für apps beliebt, bei denen die kontextabhängige Platzierung digitaler Inhalte in der realen Welt von größter Bedeutung ist und die tatsächliche Umgebung des Benutzers in der Praxis "Present" ist. Benutzer können auch mühelos zwischen realen digitalen Aufgaben wechseln. Dies bietet sogar noch mehr an die Zusage, dass die vom Benutzer angezeigten gemischten Reality-apps wirklich ein Teil Ihrer Umgebung sind.

![Erweiterte Umgebungs-apps](images/enhancedenvironmentapps-640px.jpg)<br>
*Erweiterte Umgebungs-apps*

**Verwendungs Beispiele**
* Eine gemischte Reality-App im Editor-Stil, die Benutzern das Erstellen und Platzieren von Notizen in Ihrer Umgebung ermöglicht
* Eine gemischte Reality-TV-APP, die für die Anzeige
* Eine gemischte Reality-APP, die über der Kücheninsel platziert wird, um eine Koch Aufgabe zu unterstützen
* Eine Mixed Reality-APP, mit der Benutzer das Gefühl der "x-ray-Vision" haben (d. h. ein – Hologramm, das auf ein reales Objekt folgt und es imitiert, während der Benutzer "in IT" holografisch sehen kann)
* In einer Factory enthaltene gemischte Reality-Anmerkungen, um die erforderlichen Informationen zu den Mitarbeitern zu senden
* Gemischte Realität bei der Suche in einem Bürobereich
* Gemischte Realität: richtige-Erfahrungen (d. h. das Spiel Stil der Platine)
* Kommunikations-apps mit gemischter Realität wie Skype

## <a name="blended-environment-apps"></a>Apps für gemischte Umgebungen

Angesichts der Fähigkeit von Windows Mixed Reality, die Umgebung des Benutzers zu erkennen und zuzuordnen, ist es möglich, eine digitale Ebene zu erstellen, die sich auf den Platz des Benutzers überlagern kann. Die schlanke Ebene respektiert die Form und die Grenzen der Benutzerumgebung, aber die APP kann bestimmte Elemente transformieren, die sich am besten für das Eintauchen des Benutzers in der APP eignen. Dies wird als gemischte Umgebungs-App bezeichnet. Anders als bei einer erweiterten Umgebungs-APP sind Apps für die gemischte Umgebung unter Umständen nur für die Umgebung geeignet, um das jeweilige Benutzer Verhalten (z. b. das fördern von Bewegung oder durchsuchen) und das Ersetzen von Elementen durch Änderungen zu verbessern (ein Küchen-Counter wird zum Anzeigen eines anderen Kachel Musters erfasst). Diese Art von Umgebung kann sogar ein Element in ein völlig anderes Objekt transformieren, aber dennoch die groben Dimensionen des Objekts als Basis beibehalten (eine Kücheninsel wird in eine dumpfunktion für ein Krimi Spiel für den Krimi transformiert).

![Apps für gemischte Umgebungen](images/blendedenvironmentapps-640px.jpg)<br>
*Apps für gemischte Umgebungen*

**Verwendungs Beispiele**
* Eine gemischte Reality-Design-APP, mit der Wände, gegen Flächen oder Bereiche in unterschiedlichen Farben und Mustern gezeichnet werden können
* Eine Mixed Reality-APP, die es einem Automobildesigner ermöglicht, neue Entwurfs Iterationen für eine bevorstehende Fahrzeug Aktualisierung über ein vorhandenes Auto zu überlagern
* Ein Bett ist "abgedeckt" und wird durch eine Mischung aus der Realität der Realität im Spiel der Kinder ersetzt.
* Ein Schreibtisch wird "abgedeckt" und durch eine gemischte Realität dumpester in einem Krimi Spiel
* Eine hängende Laterne wird "abgedeckt" und durch Signpost ersetzt, wobei ungefähr dieselbe Form und Dimension verwendet werden.
* Eine APP, die es Benutzern ermöglicht, Löcher in ihren realen oder immersiven weltweiten Wänden zu sprengen, die eine magische Welt offenlegen

## <a name="immersive-environment-apps"></a>Immersive Umgebungs-apps

Immersive Umgebungs-apps sind auf eine Umgebung ausgerichtet, die die Benutzer Welt vollständig ändert und Sie in einer anderen Zeit und in einem anderen Bereich platzieren kann. Diese Umgebungen können sich in Echtzeit fühlen und so eine immersive und aufregende Erfahrung schaffen, die nur durch die Phantasie der APP-Ersteller eingeschränkt wird. Anders als bei Umgebungen mit gemischten Umgebungen, wenn Windows Mixed Reality den Platz des Benutzers identifiziert, kann eine immersive Umgebungs-APP die aktuelle Umgebung des Benutzers vollständig ignorieren und den gesamten Bestand durch einen eigenen ersetzen. Diese Erfahrungen können auch Zeit und Speicherplatz trennen, was bedeutet, dass ein Benutzer die Straßen von Rom in einem immersiven Erlebnis durchlaufen kann, während er sich relativ immer noch in der Praxis verbleiben kann. Der Kontext der realen Umgebung ist für eine immersive Umgebungs-App möglicherweise nicht von Bedeutung.

![Immersive Umgebungs-apps](images/windows-mixed-reality-640px.jpg)<br>
*Immersive Umgebungs-apps*

**Verwendungs Beispiele**
* Eine immersive APP, die es einem Benutzer ermöglicht, einen Platz voneinander getrennt zu machen (d. h. durch einen berühmten Gebäude, ein Gebäude, beliebte Stadt)
* Eine immersive APP, die ein Ereignis oder Szenario für den Benutzer orchestriert (d. h. einen Kampf oder eine Leistung).

## <a name="see-also"></a>Siehe auch

* [Entwicklung – Übersicht](../develop/development.md)
* [App-Modell](app-model.md)
* [App-Ansichten](app-views.md)
