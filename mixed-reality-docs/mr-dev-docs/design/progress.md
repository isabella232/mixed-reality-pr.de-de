---
title: Anzeigen des Fortschritts
description: Erfahren Sie, wie Statussteuerelemente dem Benutzer Feedback darüber senden, dass in Ihren Mixed Reality-Apps ein Vorgang mit langer Ausführungslaufzeit ausgeführt wird.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Design, Steuerelemente, Ui, ux, Statusanzeige, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 8d397f627b55409d640ac6925a72d6bf169e207c27cb2a90bcee990c7a8d7683
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207884"
---
# <a name="progress-indicator"></a>Statusanzeige

<br>

<img src="images/MRTK_ProgressIndicator.gif" alt="Progress ring example in HoloLens" width="940px">

Ein Statussteuerelement gibt Feedback, dass ein Vorgang mit langer Ausführung ausgeführt wird. Wenn eine Statusanzeige angezeigt wird, können Benutzer die Wartezeit anzeigen und nicht mit der App interagieren.

<br>

---

## <a name="types-of-progress"></a>Typen von Statussteuerelementen

Es ist wichtig, dem Benutzer Informationen darüber bereitzustellen, was passiert. In Mixed Reality können Benutzer leicht von der physischen Umgebung oder objekten ablenkt werden, wenn Ihre App kein gutes visuelles Feedback hat. In Situationen, die einige Sekunden dauern, z. B. wenn Daten geladen werden oder eine Szene aktualisiert wird, empfiehlt es sich, einen visuellen Indikator anzuzeigen. Es gibt zwei Optionen, um dem Benutzer anzuzeigen, dass ein Vorgang ausgeführt wird: eine **Statusanzeige** oder ein **Statusring.**

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a>Statusleiste<br>
        Eine Statusanzeige zeigt den Prozentsatz an, in dem eine Aufgabe abgeschlossen wurde. Sie sollte während eines Vorgangs verwendet werden, dessen Dauer bekannt ist (determinierend), aber der Fortschritt sollte die Interaktion des Benutzers mit der App nicht blockieren.<br>
        <br>
        *Abbildung: Statusanzeigebeispiel in HoloLens*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Beispiel der Statusanzeige in HoloLens](images/640px-progressbar.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a>Statusring<br>
        Ein Statusring weist nur einen unbestimmten Zustand auf und sollte verwendet werden, wenn die Benutzerinteraktion blockiert wird, bis der Vorgang abgeschlossen ist.<br>
        <br>
        *Abbildung: Beispiel eines Statusrings in HoloLens*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Beispiel eines Statusrings auf HoloLens Gerät](images/640px-progressring.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a>Status mit einem benutzerdefinierten Objekt<br>
        Sie können der Persönlichkeit und Markenidentität Ihrer App hinzufügen, indem Sie das Progress-Steuerelement mit Ihren eigenen benutzerdefinierten 2D/3D-Objekten anpassen.<br>
        <br>
        *Abbildung: Status mit benutzerdefiniertem Meshbeispiel in HoloLens*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Fortschritt mit benutzerdefiniertem Meshbeispiel in HoloLens](images/640px-progresscustom.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a>Bewährte Methoden

* Eng an die Anzeige von Progress [koppeln oder taggen,](billboarding-and-tag-along.md) da der Benutzer den Kopf leicht in einen leeren Bereich verschieben und den Kontext verlieren kann. Ihre App könnte so aussehen, als wäre sie abgestürzt, wenn der Benutzer nichts sehen kann. Die Kennzeichnung und das Tag-Along sind in das Prefab Progress integriert.
* Es ist immer gut, Statusinformationen darüber bereitzustellen, was dem Benutzer passiert. Das Prefab Progress stellt verschiedene visuelle Stile bereit, einschließlich des Windows Standardmäßigen Ringtypstatus zum Bereitstellen des Status. Sie können auch ein benutzerdefiniertes Gitternetz mit einer Animation verwenden, wenn der Stil Ihres Fortschritts an der Marke Ihrer App ausgerichtet werden soll.

<br>

---

## <a name="progress-indicator-in-mrtk-mixed-reality-toolkit-for-unity"></a>Statusanzeige im MRTK (Mixed Reality Toolkit) für Unity

* [MRTK – Prefabs für Statusanzeigen](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/Features/UX/Prefabs/ProgressIndicators)
* [MRTK – Szenenübergangsdienst](/windows/mixed-reality/mrtk-unity/features/extensions/scene-transition-service)


<br>

---

## <a name="see-also"></a>Siehe auch

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