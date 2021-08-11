---
title: Handmenü
description: MitHilfe von Handmenüs können Benutzer schnell eine handverfügte Benutzeroberfläche für häufig verwendete Funktionen aufrufen.
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: Hand, Menü, Schaltfläche, Schnellzugriff, Layout, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 76338f75250054c531560dc0b6cb18aa7130c09fe30a49b4afc3fd409f88fdc0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115201976"
---
# <a name="hand-menu"></a>Handmenü

![Ulnar side hand location (Ulnar-Seitenposition)](images/UX_Hero_HandMenu.jpg)

Das Handmenü ist eines der einzigartigsten UX-Muster in HoloLens 2. So können Sie schnell eine handverfügte Benutzeroberfläche einrichten. Da sie jederzeit zugänglich ist und leicht angezeigt und ausgeblendet werden kann, ist sie hervorragend für schnelle Aktionen geeignet.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAg]

Unsere empfohlenen bewährten Methoden für die Arbeit mit Handmenüs finden Sie in der folgenden Liste. Sie finden auch eine Beispielszene, die das Handmenü im [MRTK](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)veranschaulicht.

<br>

---

## <a name="best-practices"></a>Bewährte Methoden

**Halten Sie die Anzahl der Schaltflächen klein.** 

Aufgrund der nähen Entfernung zwischen einem handgesperrten Menü und den Augen und der Neigung für Benutzer, sich jederzeit auf einen relativ kleinen visuellen Bereich zu konzentrieren (der Aufmerksamkeitskegel des Sehens beträgt ungefähr 10 Grad), wird empfohlen, die Anzahl der Schaltflächen klein zu halten. Basierend auf unserer Untersuchung funktioniert eine Spalte mit drei Schaltflächen gut, indem der gesamte Inhalt innerhalb des Sichtfelds (Field of View, FOV) verbleibt, auch wenn ein Benutzer seine Hände in die Mitte des FOV verschiebt. 

**Verwenden des Handmenüs für schnelle Aktionen** 

Das Auslösen eines Arms und das Beibehalten der Position kann leicht zu Armmüdigkeit führen. Verwenden Sie eine handgesperrte Methode für das Menü, das eine kurze Interaktion erfordert. Wenn Ihr Menü komplex ist und längere Interaktionszeiten erfordert, sollten Sie stattdessen die Verwendung von world-locked oder body-locked in Betracht ziehen. 

**Schaltflächen-/Panelwinkel**

Menüs sollten auf die entgegengesetzte Seite und Mitte des Kopfes ausgerichtet sein: Dies ermöglicht eine natürliche Handbewegung, um mit dem Menü mit der entgegengesetzten Hand zu interagieren, und vermeidet umständliche oder schwierige Handpositionen beim Berühren von Schaltflächen. 

**Erwägen Sie die Unterstützung eines einhändigen oder freihändigen Vorgangs.**

Gehen Sie nicht davon aus, dass beide Hände des Benutzers immer verfügbar sind. Berücksichtigen Sie eine Vielzahl von Kontexten, wenn ein oder beide Hände nicht verfügbar sind, und stellen Sie sicher, dass Ihr Entwurf diese Situationen berücksichtigt. Um ein einhändiges Handmenü zu unterstützen, können Sie versuchen, die Menüplatzierung von "hand-locked" in "world-locked" zu übergehen, wenn die Hand umkippt (geht die Hand nach unten). Erwägen Sie für Freihandszenarien die Verwendung eines Sprachbefehls, um das Handmenü aufzurufen.

**Vermeiden Sie das Hinzufügen von Schaltflächen in der Nähe des Handbands (Startschaltfläche des Systems).**

Wenn die Handmenüschaltflächen zu nah an der Startschaltfläche platziert werden, wird sie möglicherweise versehentlich ausgelöst, während sie mit dem Handmenü interagieren.

<br>

## <a name="hand-menu-with-large-and-complex-ui-controls"></a>Handmenü mit großen und komplexen Ui-Steuerelementen

<img src="images/HandMenu_SizeExample.png" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
Es wird empfohlen, die Anzahl von Schaltflächen oder Ui-Steuerelementen in handgebundenen Menüs einzuschränken. Dies liegt daran, dass die erweiterte Interaktion mit einer großen Anzahl von Benutzeroberflächenelementen zu Armmüdigkeit führen kann. Wenn Ihre Benutzeroberfläche ein großes Menü erfordert, stellen Sie eine einfache Möglichkeit für den Benutzer bereit, das Menü weltweit zu sperren. Eine methode, die wir empfehlen, besteht darin, die Welt zu sperren und dann das Menü zu verwenden, wenn die Hand abfällt oder vom Benutzer wegklappt. Eine zweite Technik besteht darin, dem Benutzer zu ermöglichen, das Menü direkt mit der anderen Hand zu greifen. Wenn der Benutzer das Menü freigibt, sollte das Menü die Weltsperre haben. Auf diese Weise kann ein Benutzer über einen längeren Zeitraum problemlos und sicher mit verschiedenen Benutzeroberflächenelementen interagieren. 

Wenn das Menü weltweit gesperrt ist, stellen Sie sicher, dass Sie eine Möglichkeit zum Verschieben des Menüs bereitstellen und das Menü schließen, wenn es nicht mehr benötigt wird. Machen Sie das Menü verschiebbar, indem Sie Ziehpunkte an den Seiten oder am oberen Rand des Menüs bereitstellen. Fügen Sie eine Schaltfläche zum Schließen hinzu, damit das Menü geschlossen werden kann. Lassen Sie zu, dass das Menü erneut an die Hand angefügt wird, wenn die Benutzerhand dem Benutzer angezeigt wird. Außerdem wird empfohlen, dass die Benutzer an ihre Hand sehen müssen, um falsche Aktivierungen zu verhindern (siehe unten).

**Großes Menü mit einem Benutzerfreundlichkeitsproblem**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AOPx]

**World-locked menu on hand drop**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AGZi]

**Manuelles Greifen & Per Pull zum Weltsperren des Menüs**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAf]

## <a name="how-to-prevent-false-activation"></a>Verhindern einer falschen Aktivierung

Wenn Sie einfach hand-up als Ereignis verwenden, um das Handmenü auszulösen, wird es möglicherweise versehentlich angezeigt, wenn Sie es nicht benötigen (falsch-positiv), da Personen ihre Hände sowohl absichtlich (zur Kommunikation und Objektbearbeitung) als auch unbeabsichtigt bewegen. Um falsche Aktivierungen zu reduzieren, fügen Sie neben dem Handfläche-Up-Ereignis einen zusätzlichen Schritt hinzu, um das Handmenü aufzurufen (z. B. vollständig geöffnete Finger oder der Benutzer, der absichtlich an der Hand brettscht).

**Flache Handfläche erforderlich**

Indem Sie eine flache geöffnete Hand erfordern, können Sie eine falsche Aktivierung verhindern, die auftreten kann, wenn der Benutzer Objekte oder Gesten während der Kommunikation innerhalb einer Umgebung bearbeitet. 

**Anv anfordern**

Durch die Anforderung, dass der Benutzer seine Hand anviert (entweder mit dem Anvischen mit den Augen oder mit dem Kopf), verhindert er falsche Aktivierungen, da der Benutzer seine Aufmerksamkeit als sekundären Aktivierungsschritt auf die Hand richten muss (mit einem änderbaren Abstandsschwellenwert, der für den Benutzerfreundlichkeit verwendet wird).  

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Asn4]

---

## <a name="hand-menu-placement-best-practices"></a>Bewährte Methoden für die Platzierung von Handmenüs

In der menschlichen Anatomie ist die Ulnar-1600-160-160-160-160-160-160-160-160- Der Ulna ist ein langer Unterarm im Unterarm, der vom Ellenbogen bis zum kleinsten Finger gestreckt wird.

Im Folgenden finden Sie zwei empfohlene Platzierungen basierend auf unseren Untersuchungen:

:::row:::
    :::column:::
        ![Ulnar-Seitenhandposition in Handfläche](images/UlnarSideHandMenu.gif)<br>
        **A. Ulnar in der Handfläche**<br>
        Diese Position ist zuverlässig, da sich die Hände nicht überlappen. Dies ist wichtig für die genaue Erkennung und Nachverfolgung von Hand.
    :::column-end:::
    :::column:::
        ![Ulnar side hand location above hand](images/UlnarAboveHandMenu.gif)<br>
        **B. Ulnar oben**<br>
        Diese Position ist für Benutzer praktisch, da sie ihren Arm nicht zu stark erhöhen müssen, um mit dem Handmenü zu interagieren. Es wird empfohlen, Menüs **13 cm** über der Handfläche zu platzieren und die Schaltflächen in der Ulnar-Handfläche auszurichten. [Weitere Informationen zur optimalen Schaltflächengröße](interactable-object.md)<br>
        <br>
        Aus technischen Gründen wird dieser Speicherort mit einer erforderlichen Implementierung empfohlen: Der Entwickler muss das Menü einfrieren, sobald die entgegengesetzte Hand des Benutzers sich der Interaktion nähert. Dies vermeidet Jitteriness durch überlappende Hände und ermöglicht auch eine schnellere Ausrichtung der Schaltflächen.<br>
        <br>
        HoloLens 2 Kameras identifizieren die Hände genau, wenn sie voneinander getrennt sind. Alle überlappenden Hände können dazu führen, dass Handmenüs von der Position des Ankers weg verschoben werden.<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="menu-positions-that-arent-recommended"></a>Menüpositionen, die nicht empfohlen werden

Wir haben Benutzer recherchiert und verschiedene Menülayouts und -orte verwendet. Die folgenden Menüspeicherorte werden **NICHT empfohlen.** Die Nachteile der einzelnen Studie finden Sie unten:

:::row:::
    :::column:::
        ![Oberer Arm](images/AboveArm.gif)<br>
        **Über dem Arm**<br>
        1– Schwierig, eine gute Handverfolgung zu verwalten<br>
        2– Verursacht Benutzermüdigkeit aufgrund unnatürlicher Position
    :::column-end:::
    :::column:::
        ![Obere Finger](images/AboveFingers.gif)<br>
        **Obere Finger**<br>
        1 – Handmüdigkeit aufgrund des langen Haltens der Hand<br>
        2– Probleme bei der Handnachverfolgung an Index- und Mittelfingern
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![Oberhalb der mittleren Handfläche](images/handCenter.gif)<br>
        **Übermittelte Handfläche**<br>
        1– Probleme bei der Handnachverfolgung aufgrund überlappender Hände<br>
        2 – Handmüdigkeit aufgrund der langen Handhaltung für die Interaktion mit Menüs
    :::column-end:::
    :::column:::
        ![Top Fingertip ](images/TopFingerTip.gif) **Top fingertip**<br>
        1– Probleme mit der Handnachverfolgung<br>
        2 – Handmüdigkeit durch Halten der Hand über dem normalen Körper<br>
        3– Probleme beim Drücken von Schaltflächen mit anderen Fingern aufgrund von begrenztem Platz zwischen den Fingern
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![Rückseite des Arms](images/BackOfTheArm.gif)<br>
        **Rückseite des Arms**<br>
        1– Kann die Startschaltfläche aus Versehen auslösen<br>
        2 – Keine natürliche oder komfortable Position
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a>Handmenü im MRTK (Mixed Reality Toolkit) für Unity

**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** stellt Skripts und Beispielszenen für das Handmenü bereit. Mit dem HandConstraintPalmUp-Solverskript können Sie alle Objekte mit verschiedenen konfigurierbaren Optionen an die Hände anfügen. Die Handmenübeispiele des MRTK enthalten nützliche Optionen wie flache Handflächen und Anverweise, um eine falsche Aktivierung zu verhindern.

* [Handmenüdokumentationen](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)
* [Beispielszene im Handmenü](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandMenuExamples.unity)

Sie können menübeispiele in HoloLens 2 mit der MRTK Examples Hub-App ausprobieren.

* [Handmenüszene im MRTK-Beispielhub](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4?activetab=pivot:overviewtab)

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