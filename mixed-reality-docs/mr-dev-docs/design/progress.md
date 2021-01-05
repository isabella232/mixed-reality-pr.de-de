---
title: Anzeigen des Fortschritts
description: Ein Statussteuerelement gibt dem Benutzer eine Rückmeldung, dass ein Vorgang mit langer Laufzeit ausgeführt wird.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Gemischte Windows Mixed Reality, Design, Steuerelemente, UI, UX, Fortschrittsanzeige, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens, mrtk, Mixed Reality Toolkit
ms.openlocfilehash: 3f24f7095147a0d220df8adc42b67a1b8e4053c9
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848279"
---
# <a name="progress-indicator"></a>Statusanzeige

<br>

<img src="images/MRTK_ProgressIndicator.gif" alt="Progress ring example in HoloLens" width="940px">

Eine Statuskontrolle bietet Feedback, dass ein Vorgang mit langer Laufzeit ausgeführt wird. Wenn eine Statusanzeige sichtbar ist, können Benutzer die Wartezeit sehen und können nicht mit der APP interagieren.

<br>

---

## <a name="types-of-progress"></a>Typen von Statussteuerelementen

Es ist wichtig, dass Sie die Benutzerinformationen zu den Vorgängen bereitstellen. In gemischter Realität können Benutzer leicht von der physischen Umgebung oder Objekten abgelenkt werden, wenn Ihre APP kein gutes visuelles Feedback hat. Für Situationen, die einige Sekunden dauern, z. b. beim Laden von Daten oder beim Aktualisieren einer Szene, empfiehlt es sich, einen visuellen Indikator anzuzeigen. Es gibt zwei Möglichkeiten, den Benutzer anzuzeigen, dass ein Vorgang ausgeführt wird – eine **Status** Anzeige oder ein **Fortschritts Ring**.

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a>Statusanzeige<br>
        Eine Statusanzeige zeigt den Prozentsatz der abgeschlossenen Aufgabe an. Er sollte bei einem Vorgang verwendet werden, dessen Dauer bekannt ist (determinate), aber sein Fortschritt sollte die Interaktion des Benutzers mit der APP nicht blockieren.<br>
        <br>
        *Bild: Statusanzeige Beispiel in hololens*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Beispiel für Statusanzeige in hololens](images/640px-progressbar.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a>Statusring<br>
        Ein Fortschritts Ring hat nur einen unbestimmten Status und sollte verwendet werden, wenn die Benutzerinteraktion blockiert wird, bis der Vorgang abgeschlossen ist.<br>
        <br>
        *Image: Fortschritts Ring-Beispiel in hololens*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Beispiel für Status Ring auf hololens-Gerät](images/640px-progressring.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a>Fortschritt mit einem benutzerdefinierten Objekt<br>
        Sie können der Identität und Markenidentität Ihrer APP hinzufügen, indem Sie das Status Steuerelement mit ihren eigenen benutzerdefinierten 2D-/3D-Objekten anpassen.<br>
        <br>
        *Bild: Fortschritt mit einem benutzerdefinierten Mesh-Beispiel in hololens*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Fortschritt mit einem benutzerdefinierten Mesh-Beispiel in hololens](images/640px-progresscustom.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a>Bewährte Methoden
* Schließen Sie das [Abrechnungs-oder tagboarding](billboarding-and-tag-along.md) eng mit der Anzeige des Fortschritts ab, da der Benutzer problemlos seinen Kopf in einen leeren Bereich verschieben und Kontext verlieren kann. Ihre APP könnte so aussehen, als ob Sie abgestürzt ist, wenn der Benutzer nichts sehen kann. Das fakboardingboarding und das Tag-Along sind in den Fortschritt vorfab integriert.
* Es ist immer gut, Statusinformationen zu den Ereignissen für den Benutzer bereitzustellen. Die Fortschritts präfab stellt verschiedene visuelle Stile bereit, einschließlich des Windows-standardmäßigen Rings-Typs zum Angeben des Status. Sie können auch ein benutzerdefiniertes Mesh mit einer Animation verwenden, wenn Sie möchten, dass der Stil Ihres Fortschritts an der Marke Ihrer APP ausgerichtet wird.

<br>

---

## <a name="progress-indicator-in-mrtk-mixed-reality-toolkit-for-unity"></a>Fortschrittsanzeige in mrtk (Mixed Reality Toolkit) für Unity

* [Mrtk-Fortschrittsanzeige (Prefabs)](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MRTK/SDK/Features/UX/Prefabs/ProgressIndicators)
* [Mrtk-Szenen Übergangs Dienst](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Extensions/SceneTransitionService/SceneTransitionServiceOverview.html)


<br>

---

## <a name="see-also"></a>Weitere Informationen

* [Cursor](cursors.md)
* [Handstrahl](point-and-commit.md)
* [Schaltfläche](button.md)
* [Interaktionsfähiges Objekt](interactable-object.md)
* [Begrenzungsrahmen und App-Leiste](app-bar-and-bounding-box.md)
* [Manipulation](direct-manipulation.md)
* [Handmenü](hand-menu.md)
* [Nähemenü](near-menu.md)
* [Objektsammlung](object-collection.md)
* [Sprachbefehl](voice-input.md)
* [Tastatur](keyboard.md)
* [QuickInfo](tooltip.md)
* [Filmklappe](slate.md)
* [Schieberegler](slider.md)
* [Shader](shader.md)
* [Billboarding und Tag-along](billboarding-and-tag-along.md)
* [Anzeigen des Fortschritts](progress.md)
* [Oberflächenmagnetismus](surface-magnetism.md)
