---
title: Typen von Mixed Reality-Apps
description: Erfahren Sie mehr über die von der Mixed Reality-Plattform unterstützten Umgebungen, von immersiven Umgebungen bis zu einfachen Informationsebenen über der Umgebung eines Benutzers.
author: rwinj
ms.author: willyang
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Design, App-Muster, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens
ms.openlocfilehash: 13d4f538148b2c6b6f4df422c6c423f2b2710ca1ba2d98fe4f952c14284035f8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115218924"
---
# <a name="types-of-mixed-reality-apps"></a>Typen von Mixed Reality-Apps

Einer der Vorteile der Entwicklung von Apps für Windows Mixed Reality ist das Spektrum an Erfahrungen, die die Plattform unterstützen kann. Von vollständig immersiven virtuellen Umgebungen bis zur leichten Überlagerung der aktuellen Umgebung eines Benutzers mit Informationen bietet Windows Mixed Reality eine Sammlung robuster Tools, mit denen sich jede Erfahrung lebendig gestalten lässt. Es ist wichtig, dass ein App-Ersteller frühzeitig im Entwicklungsprozess versteht, wo in diesem Spektrum seine Erfahrung liegt. Diese Entscheidung wirkt sich letztendlich sowohl auf das App-Design als auch auf den technologischen Entwicklungspfad aus.

## <a name="enhanced-environment-apps-hololens-only"></a>Erweiterte Umgebungs-Apps (nur HoloLens)

Eine der leistungsstärksten Möglichkeiten, die Mixed Reality nutzen kann, besteht in der Tatsache, dass Entwickler digitale Informationen oder Inhalte in der aktuellen Umgebung eines Benutzers platzieren können. Dieser Ansatz ist für Apps beliebt, bei denen die kontextbezogene Platzierung digitaler Inhalte in der realen Welt von entscheidender Bedeutung ist und die reale Umgebung des Benutzers während seiner Erfahrung "vorhanden" ist. Benutzer können auch problemlos zwischen realen digitalen Aufgaben wechseln. Dies bietet noch mehr Gedränge für die Zusage, dass die Mixed Reality-Apps, die dem Benutzer angezeigt werden, wirklich Teil ihrer Umgebung sind.

![Erweiterte Umgebungs-Apps](images/enhancedenvironmentapps-640px.jpg)<br>
*Erweiterte Umgebungs-Apps*

**Beispiel verwendet**
* Eine Mixed Reality-Editor-App, mit der Benutzer Notizen in ihrer Umgebung erstellen und platzieren können
* Eine Mixed Reality-Fernseh-App, die an einem komfortablen Ort für die Anzeige platziert ist
* Eine Mixed Reality-App, die über der Inselninsel platziert wurde, um eine Aufgabe zu unterstützen
* Eine Mixed Reality-App, die Benutzern das Gefühl des "X-Ray Vision" vermittelt (d. h. ein Hologramm, das auf einem realen Objekt platziert und es imitiert, während dem Benutzer ermöglicht wird, holografisches "darin" zu sehen)
* Mixed Reality-Anmerkungen, die in einer Factory platziert werden, um die erforderlichen Informationen des Mitarbeiters zu erhalten
* Mixed Reality-Wegesuche in einem Büroraum
* Mixed Reality-Tabellentoperfahrungen (d. h. Spielstilerfahrungen im Board)
* Mixed Reality-Kommunikations-Apps wie Skype

## <a name="blended-environment-apps"></a>Gemischte Umgebungs-Apps

Da Windows Mixed Reality die Umgebung des Benutzers erkennen und zuordnen können, kann er eine digitale Ebene erstellen, die im Bereich des Benutzers überlagert werden kann. Die schlanke Schicht beachtet die Form und die Grenzen der Umgebung des Benutzers, aber die App kann bestimmte Elemente transformieren, die sich am besten für den Benutzer in der App eignen. Dies wird als gemischte Umgebungs-App bezeichnet. Im Gegensatz zu einer erweiterten Umgebungs-App ist die Umgebung für Apps mit gemischter Umgebung möglicherweise nur so wichtig, dass sie ihr Make-Up am besten nutzen, um bestimmtes Benutzerverhalten zu fördern (z. B. bewegungs- oder untersuchungsfreundliches Verhalten) oder indem Elemente durch Änderungen ersetzt werden (ein Zähler für die Benutzeroberfläche wird ge skinnt, um ein anderes Kachelmuster zu zeigen). Diese Art von Erfahrung kann sogar ein Element in ein völlig anderes Objekt transformieren, aber dennoch die groben Dimensionen des Objekts als Basis behalten (eine Insel wird in einen Dumpster für ein Spiel mit EinemVerbrechen umgewandelt).

![Gemischte Umgebungs-Apps](images/blendedenvironmentapps-640px.jpg)<br>
*Gemischte Umgebungs-Apps*

**Beispiel verwendet**
* Eine Mixed Reality-App für den Innenentwurf, die Wände, Gegenspitzen oder Farben in unterschiedlichen Farben und Mustern zeichnen kann
* Eine Mixed Reality-App, die es einem Automobildesigner ermöglicht, neue Designiterationen für eine anstehende Fahrzeugaktualisierung über einem vorhandenen Auto zu schichten.
* Ein Beet wird "abgedeckt" und durch einen Mixed Reality-Kinderspielstand ersetzt.
* Ein Desk wird "abgedeckt" und durch einen Mixed Reality-Dumpster in einem Verbrechensspiel ersetzt.
* Eine hängende Laterne wird "abgedeckt" und durch einen Wegweiser ersetzt, der ungefähr die gleiche Form und Dimension verwendet.
* Eine App, mit der Benutzer Lücken in ihren realen oder immersiven Weltsteinen beseitigen können, die eine beeindruckende Welt zeigen

## <a name="immersive-environment-apps"></a>Immersive Umgebungs-Apps

Immersive Umgebungs-Apps sind um eine Umgebung zentriert, die die Welt des Benutzers vollständig verändert und sie in einer anderen Zeit und einem anderen Raum platzieren kann. Diese Umgebungen können sich real anfühlen und immersive und rauschende Umgebungen schaffen, die nur durch die Vorstellungsreichtum des App-Erstellers eingeschränkt sind. Im Gegensatz zu Apps mit gemischter Umgebung kann eine immersive Umgebungs-App die aktuelle Umgebung des Benutzers vollständig ignorieren und den gesamten Bestand durch eine eigene ersetzen, sobald Windows Mixed Reality den Raum des Benutzers identifiziert. Diese Erfahrungen können auch Zeit und Raum trennen, was bedeutet, dass ein Benutzer die Straßen von Rome in einer immersiven Umgebung durchstehen kann, während er relativ immer noch in ihrem realen Raum verbleibt. Der Kontext der realen Umgebung ist für eine immersive Umgebungs-App möglicherweise nicht wichtig.

![Immersive Umgebungs-Apps](images/windows-mixed-reality-640px.jpg)<br>
*Immersive Umgebungs-Apps*

**Beispiel verwendet**
* Eine immersive App, mit der ein Benutzer einen von seinem eigenen getrennten Raum erkunden kann (d. h. durch ein bekanntes Gebäude, eine beliebte Stadt, eine beliebte Stadt)
* Eine immersive App, die ein Ereignis oder Szenario um den Benutzer herum orchestriert (d. h. eine Aktion oder eine Leistung).

## <a name="see-also"></a>Siehe auch

* [Entwicklung – Übersicht](../develop/development.md)
* [App-Modell](app-model.md)
* [App-Ansichten](app-views.md)
