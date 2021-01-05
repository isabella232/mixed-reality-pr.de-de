---
title: Freihändig
description: Erfahren Sie mehr über die Schwierigkeiten, die Benutzer mit einer Hand-und Controller Schnittstelle haben können, und über verschiedene Freihand freie Alternativen.
author: hferrone
ms.author: v-hferrone
ms.date: 04/20/2019
ms.topic: article
keywords: Mixed Reality, Hands-Free, Gaze, Blick auf das Ziel, Interaktion, Entwurf, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens, mrtk, Mixed Reality Toolkit, Spracheingabe, Benutzerfreundlichkeit
ms.openlocfilehash: 2864e58fdd8a29ae8f981b42f50735eb13a50869
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847683"
---
# <a name="hands-free"></a>Freihändig

## <a name="scenarios"></a>Szenarien

Wie in der [Übersicht über das Interaktionsmodell](interaction-fundamentals.md)erläutert, stellen Sie nach der Identifizierung Ihrer Benutzer und ihrer Ziele selbst fest, welche Umgebungs-oder situations Probleme bei der Ausführung ihrer Aufgaben auftreten können. Beispielsweise müssen viele Benutzer ihre Hände zum Erreichen Ihrer wirklichen Ziele verwenden, und Sie haben Schwierigkeiten bei der Interaktion mit einer auf der Basis-und Controller basierten Schnittstelle.

Zu den spezifischen Szenarien gehören: 
* Führung durch eine Aufgabe, während die Hände des Benutzers beschäftigt sind
* Nachschlagen in der Dokumentation, während die Hände des Benutzers beschäftigt sind
* Ermüden der Hände
* Handschuhe, die nicht nachverfolgt werden können
* Tragen von Gegenständen in den Händen
* Soziale Unbekümmertheit bei der Verwendung von großen Handgesten
* Beengte Raumverhältnisse

## <a name="hands-free-modalities"></a>Hände freie Modalitäten

### <a name="voice-input"></a>[Spracheingabe](voice-input.md)

Die Verwendung Ihrer Stimme für die Befehls-und Steuerungsmöglichkeiten einer Schnittstelle bietet eine bequeme Möglichkeit, die Hände frei zu betreiben und Verknüpfungen zu verwenden, um mehrere Schritte bei Bedarf zu überspringen. Mit der Spracheingabe kann der Benutzer den Namen einer beliebigen Schaltfläche mit dem Namen "Loud" lesen, um ihn zu aktivieren _("See it, Say it")_ und sich mit einem Digital Agent zu informieren, der Aufgaben für Sie erledigen kann.

### <a name="gaze-and-dwell"></a>[Anvisieren und Verweilen](gaze-and-dwell.md)

In einigen praktischen Situationen ist die Verwendung Ihrer Stimme nicht ideal oder gar nicht möglich. Laute Factory-Umgebungen, Datenschutz oder soziale Standards können Einschränkungen aufweisen. Mit dem "Eye + Dwell"-Modell kann der Benutzer durch eine APP navigieren, ohne dass zusätzliche Eingaben von der Augen-oder Kopfzeile entfernt werden: der Benutzer sorgt einfach dafür, dass er sich am Ziel befindet, und er wird für einen Moment zum Aktivieren des Ziels angezeigt. Weitere Informationen zu den einzelnen Entwurfs Überlegungen für "Blick" und "Wohnen" finden Sie unter " [Eye-Eye](gaze-and-dwell-eyes.md) " und "Wohnen" und " [Kopf-](gaze-and-dwell-head.md)und neben schauen"

## <a name="transitioning-in-and-out-of-hands-free"></a>Wechsel in und aus der Praxis freie Umstellung

In diesen Szenarien kann es von einer absoluten Anforderung bis zum Ende der Interaktion mit holograms für die Befehls-und Navigationsmöglichkeiten reichen, dass es sich um eine absolute Anforderung zum vollständigen betreiben der Anwendung handelt. 

Wenn die Anwendung erfordert, dass Sie immer mit der Hand frei verwendet wird, unabhängig davon, ob Sie den Befehl "weiter", benutzerdefinierte Sprachbefehle oder den einzelnen Sprachbefehl "Select" verwenden, stellen Sie sicher, dass Sie die entsprechenden Unternehmen in Ihrer Benutzeroberfläche verwenden. 

Wenn Ihr Ziel Benutzer nach eigenem Ermessen von Hand zu Hause wechseln muss, ist es wichtig, dass Sie die folgenden Prinzipien berücksichtigen.

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a>Gehen Sie davon aus, dass der Benutzer bereits im Modus ist, zu dem gewechselt werden soll.
Wenn sich der Benutzer beispielsweise auf der Werks Seite befindet, sehen Sie sich einen Video Verweis auf den hololens an und beschließt, einen Schraubendreher zu starten, um die Arbeit zu starten. er würde höchstwahrscheinlich in Hand arbeiten arbeiten, ohne den Schrauben Strich zum Drücken einer Schaltfläche ablegen zu müssen. Sie kann eine sprach Sitzung mit einem Sprachbefehl aufrufen, sich auf einer bereits sichtbaren Benutzeroberfläche befinden, um zu beginnen, oder das Wort "Select".

Der Benutzer kann folgende Aktionen ausführen: 
* Wechseln Sie in die Hände frei, während Sie kostenlos
* Wechseln Sie zur Hand.
* Wechseln zum Controller mithilfe eines Controllers 

### <a name="create-redundant-ways-to-switch-modes"></a>Erstellen von redundanten Möglichkeiten zum Wechseln von Modi

Beim ersten Prinzip geht es um den Zugriff, bei dem zweiten Prinzip um die Verfügbarkeit. Es darf nur eine Möglichkeit zum Wechseln in einen und aus einem Modus geben. 

Einige Beispiele sind: 
* Eine Schaltfläche zum Starten von sprach Interaktionen
* Ein Sprachbefehl für den Übergang zu, Verwendung von Head-Gaze und wohnen

### <a name="add-a-dash-of-drama"></a>Hinzufügen eines Bindestrichs

Ein Modusschalter ist ein großer Teil. Es ist wichtig, dass diese Übergängen auftreten, wenn Sie ein expliziter, sogar ein dramatischer Switch sind, um dem Benutzer mitzuteilen, was passiert ist. 

## <a name="usability-checklist"></a>Benutzerfreundlichkeit

**Kann der Benutzer alles durchführen, und alles, was für das Ende von Hand ist.**
* Jede austauschbare Tabelle sollte auf die Hand frei zugreifen können.
* Stellen Sie sicher, dass alle benutzerdefinierten Gesten ersetzt werden, z. b. das Ändern der Größe, das platzieren, Schwenken, tippen usw.
* Stellen Sie sicher, dass der Benutzer die Benutzeroberflächen Präsenz, Platzierung und Ausführlichkeit immer sicher kontrolliert.
    * So erhalten Sie die Benutzeroberfläche
    * Adressieren der Benutzeroberfläche, die nicht in der Ansicht angezeigt wird (FOV)
    * Wie viel ich sehe, wo, wann

**Werden die Mechanismen der Interaktion mit den richtigen Kosten für die Interaktion gelehrt und verstärkt?**

Versteht der Benutzer...
* ... In welchem Modus befinden Sie sich?
* ... Was können Sie in diesem Modus tun?
* ... Was ist der aktuelle Zustand?
* ... Wie können Sie übergehen?
    
**Ist die Benutzeroberfläche für die Hände frei optimiert?**   

* Beispiel: das Verb bauen von Strukturen ist nicht in typische 2D-Muster integriert.
* Beispiel: die sprach Ausrichtung ist besser mit der Objekt Hervorhebung.
* Beispiel: sprach Interaktionen sind besser mit Untertiteln, die eingeschaltet werden müssen

## <a name="see-also"></a>Weitere Informationen

* [Blickverfolgung auf HoloLens 2](eye-tracking.md)
* [Anvisieren und Ausführen](gaze-and-commit.md)
* [Anvisieren und Verweilen](gaze-and-dwell.md)
* [Hände – Direkte Manipulation](direct-manipulation.md)
* [Hände – Gesten](gaze-and-commit.md#composite-gestures)
* [Hände – Zeigen und Ausführen](point-and-commit.md)
* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Spracheingabe](voice-input.md)
