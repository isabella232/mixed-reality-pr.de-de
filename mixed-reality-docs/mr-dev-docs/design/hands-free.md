---
title: Freihändig
description: Erfahren Sie mehr über die Schwierigkeiten, mit denen Benutzer möglicherweise mit einer Schnittstelle für Hände und Controller konfrontiert sind, und über verschiedene Freihandalternativen.
author: hferrone
ms.author: v-hferrone
ms.date: 04/20/2019
ms.topic: article
keywords: Mixed Reality, Freihand, Anvisieren, Anvisieren, Zielgruppenadressierung, Interaktion, Design, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit, Spracheingabe, Benutzerfreundlichkeit
ms.openlocfilehash: 725d8886d21b42ee4643680c0dc91c1d29c25f8409b0ed0828256564dde7545c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213534"
---
# <a name="hands-free"></a>Freihändig

## <a name="scenarios"></a>Szenarien

Wie in der Übersicht über das [Interaktionsmodell](interaction-fundamentals.md)beschrieben, fragen Sie sich nach der Identifizierung Ihrer Benutzer und deren Ziele, welchen Umgebungs- oder Situationsproblemen sie möglicherweise gegenüberstehen, wenn sie ihre Aufgaben erfüllen. Beispielsweise müssen viele Benutzer ihre Hände verwenden, um ihre realen Ziele zu erreichen, und sie haben Schwierigkeiten bei der Interaktion mit einer auf Händen und Controllern basierenden Schnittstelle.

Zu den spezifischen Szenarien gehören: 
* Führung durch eine Aufgabe, während die Hände des Benutzers beschäftigt sind
* Nachschlagen in der Dokumentation, während die Hände des Benutzers beschäftigt sind
* Ermüden der Hände
* Handschuhe, die nicht nachverfolgt werden können
* Tragen von Gegenständen in den Händen
* Soziale Umständlichkeit bei der Verwendung großer Handgesten
* Beengte Raumverhältnisse

## <a name="hands-free-modalities"></a>Freihändige Verzeichnisse

### <a name="voice-input"></a>[Spracheingabe](voice-input.md)

Die Verwendung Ihrer Stimme zum Befehlen und Steuern einer Schnittstelle bietet eine bequeme Möglichkeit zum Ausführen von freihändigen Sprechfunktionen und zum Verwenden von Tastenkombinationen, um bei Bedarf mehrere Schritte zu überspringen. Mit der Spracheingabe kann der Benutzer den Namen einer beliebigen Schaltfläche laut vorlesen, um sie zu aktivieren _("sie sehen, sagen")_ und mit einem digitalen Agent kommunizieren, der Aufgaben für Sie erledigen kann.

### <a name="gaze-and-dwell"></a>[Anvisieren und Verweilen](gaze-and-dwell.md)

In einigen Situationen ohne Hände ist die Verwendung Ihrer Stimme nicht ideal oder sogar möglich. Laute Fabrikumgebungen, Datenschutz oder soziale Normen können Einschränkungen sein. Mit dem Modell "Anvieren + Verweilen" kann der Benutzer ohne zusätzliche Eingaben neben dem Anvieren mit dem Auge oder dem Kopf durch eine App navigieren: Der Benutzer hält einfach (mit dem Kopf oder den Augen) am Ziel weiter und verweilt dort für einen Moment, um es zu aktivieren. Weitere Informationen zu den einzelnen Entwurfsüberlegungen für Anverweise und Verweilen finden Sie unter [Anväuschen mit den Augen und Verweilen](gaze-and-dwell-eyes.md) mit dem Kopf und [Verweilen.](gaze-and-dwell-head.md)

## <a name="transitioning-in-and-out-of-hands-free"></a>Übergang in und aus der Freihandfunktion

In diesen Szenarien kann es von einer absoluten Anforderung bis hin zum End-to-End-Betrieb der Anwendung bis hin zu einem zusätzlichen Komfort reichen, dass der Benutzer jederzeit ein- und aussteigen kann, um die Hand von der Interaktion mit Hologrammen für Befehle und Navigation zu lassen. 

Wenn die Anwendung erfordert, dass sie immer freihändig verwendet wird, unabhängig davon, ob Sie verweilen, benutzerdefinierte Sprachbefehle oder den Befehl "select" mit einzelner Stimme verwenden, stellen Sie sicher, dass Sie die entsprechenden Gänge in Ihrer Benutzeroberfläche vornehmen. 

Wenn Ihr Zielbenutzer nach eigenem Ermessen von der Hand zur Freihand wechseln muss, ist es wichtig, die folgenden Prinzipien zu berücksichtigen.

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a>Angenommen, der Benutzer befindet sich bereits im Modus, zu dem er wechseln möchte.
Wenn sich der Benutzer z. B. in der Fabrik befindet, sich einen Videoverweis auf ihrem HoloLens ansieht und entscheidet, einen Schraubenschlüssel zu holen, um mit der Arbeit zu beginnen, beginnt er höchstwahrscheinlich frei zu arbeiten, ohne den Schraubenschlüssel zum Drücken einer Schaltfläche zu setzen. Sie kann eine Sprachsitzung mit einem Sprachbefehl aufrufen, auf einer bereits sichtbaren Benutzeroberfläche verweilen, um mit dem Verweilen zu beginnen, oder das Wort "select" sagen.

Der Benutzer kann folgende Möglichkeiten haben: 
* Wechseln zu "Freihändigen" während der Freihandfunktion
* Wechseln sie mit den Händen zu den Händen.
* Wechseln zum Controller mithilfe eines Controllers 

### <a name="create-redundant-ways-to-switch-modes"></a>Erstellen redundanter Methoden zum Wechseln von Modi

Während das erste Prinzip den Zugriff betrifft, geht es im zweiten um die Verfügbarkeit. Es sollte nicht nur eine einzige Möglichkeit zum Ein- und Ausstieg aus einem Modus geben. 

Beispiele hierfür sind: 
* Eine Schaltfläche zum Starten von Sprachinteraktionen
* Ein Sprachbefehl für den Übergang zu mithilfe von Anvieren mit dem Kopf und Verweilen

### <a name="add-a-dash-of-drama"></a>Hinzufügen eines Bindestrichs mit einem Bindestrich

Ein Moduswechsel ist eine große Sache. Wenn diese Übergänge auftreten, ist es wichtig, dass sie ein expliziter, sogar ein drastischer Schalter sind, um den Benutzer darüber zu informieren, was passiert ist. 

## <a name="usability-checklist"></a>Checkliste zur Benutzerfreundlichkeit

**Kann der Benutzer alles und alles freihändige, end-to-end-Tun?**
* Jeder interaktivierbare Sollte frei zugänglich sein.
* Stellen Sie sicher, dass es einen Ersatz für alle benutzerdefinierten Gesten gibt, z. B. Größenänderung, Platzierung, Wischbewegungen, Tippen usw.
* Stellen Sie sicher, dass der Benutzer immer eine sichere Kontrolle über die Präsenz, Platzierung und Ausführlichkeit der Benutzeroberfläche hat.
    * Benutzeroberfläche aus dem Weg gehen
    * Adressierung der Benutzeroberfläche außerhalb des Sichtfelds (FOV)
    * Wie viel ich sehe, wo, wann

**Werden die Mechanismen der Interaktion trainiert und mit den richtigen Geboten trainiert?**

Versteht der Benutzer ...
* ... In welchem Modus befinden sie sich?
* ... Welche Möglichkeiten haben sie in diesem Modus?
* ... Wie lautet der aktuelle Status?
* ... Wie kann der Übergang erfolgen?
    
**Ist die Benutzeroberfläche für freihändige Zwecke optimiert?**   

* Beispiel: Verweilen ist nicht in typische 2D-Muster integriert.
* Beispiel: Sprachadressierung ist besser mit Objekthervorhebung
* Beispiel: Sprachinteraktionen sind besser mit Untertiteln, die aktiviert werden müssen

## <a name="see-also"></a>Siehe auch

* [Blickverfolgung auf HoloLens 2](eye-tracking.md)
* [Anvisieren und Ausführen](gaze-and-commit.md)
* [Anvisieren und Verweilen](gaze-and-dwell.md)
* [Hände – Direkte Manipulation](direct-manipulation.md)
* [Hände – Gesten](gaze-and-commit.md#composite-gestures)
* [Hände – Zeigen und Ausführen](point-and-commit.md)
* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Spracheingabe](voice-input.md)
