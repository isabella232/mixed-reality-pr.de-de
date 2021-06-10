---
title: Handmenü
description: Handmenüs ermöglichen es Benutzern, schnell eine hand angefügte Benutzeroberfläche für häufig verwendete Funktionen zu öffnen.
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: Hand, Menü, Schaltfläche, Schnellzugriff, Layout, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: f007ada2d7a594f141d30a3619d4d80ac74621d8
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600329"
---
# <a name="hand-menu"></a>Handmenü

![Ulnar-Seitenposition](images/UX_Hero_HandMenu.jpg)

Das Handmenü ist eines der einzigartigsten UX-Muster in HoloLens 2. Dadurch können Sie schnell eine hand angefügte Benutzeroberfläche anzeigen. Da sie jederzeit zugänglich ist und einfach angezeigt und ausgeblendet werden kann, ist sie ideal für schnelle Aktionen.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAg]

Unsere empfohlenen bewährten Methoden für die Arbeit mit Handmenüs finden Sie in der folgenden Liste. Sie finden auch eine Beispielszene, die das Handmenü in [MRTK zeigt.](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)

<br>

---

## <a name="best-practices"></a>Bewährte Methoden

**Halten Sie die Anzahl der Schaltflächen klein.** 

Aufgrund der nähen Entfernung zwischen einem handgesperrten Menü und den Augen und der Neigung, dass benutzer sich jederzeit auf einen relativ kleinen visuellen Bereich konzentrieren (der Augenkegel beträgt ungefähr 10 Grad), wird empfohlen, die Anzahl der Schaltflächen klein zu halten. Basierend auf unserer Untersuchung funktioniert eine Spalte mit drei Schaltflächen gut, indem alle Inhalte innerhalb des Sichtfelds (Field of View, FOV) selbst dann zentriert bleiben, wenn ein Benutzer seine Hände in die Mitte des FOV bewegt. 

**Verwenden des Handmenüs für schnelle Aktionen** 

Das Erhöhen eines Arms und das Beibehalten der Position kann leicht zu Armermüdung führen. Verwenden Sie eine handgesperrte Methode für das Menü, das eine kurze Interaktion erfordert. Wenn Ihr Menü komplex ist und längere Interaktionszeiten erfordert, sollten Sie stattdessen die Verwendung von welt- oder textgesperrt in Betracht ziehen. 

**Schaltflächen-/Panelwinkel**

Menüs sollten sich gegen die entgegengesetzte Kopf- und Kopfmitte bewegen: Dies ermöglicht eine natürliche Handbewegung, um mit der entgegengesetzten Hand mit dem Menü zu interagieren, und vermeidet unhandliche oder träge Handpositionen beim Berühren von Schaltflächen. 

**Erwägen Sie die Unterstützung eines einhändigen oder freihändigen Vorgangs.**

Gehen Sie nicht davon aus, dass beide Hände des Benutzers immer verfügbar sind. Stellen Sie sich eine Vielzahl von Kontexten vor, wenn eine oder beide Hände nicht verfügbar sind, und stellen Sie sicher, dass Ihr Entwurf für diese Situationen kontent. Um ein einhändiges Handmenü zu unterstützen, können Sie versuchen, die Menüplatzierung von handgesperrt in weltgesperrt zu überstellen, wenn die Hand kippt (die Hand nach unten geht). Erwägen Sie für Freihandszenarien die Verwendung eines Sprachbefehls zum Aufrufen des Handmenüs.

**Vermeiden des Hinzufügens von Schaltflächen in der Nähe des Handgelenks (System-Startschaltfläche)**

Wenn die Handmenüschaltflächen zu nah an der Startschaltfläche platziert werden, kann dies bei der Interaktion mit dem Handmenü versehentlich ausgelöst werden.

<br>

## <a name="hand-menu-with-large-and-complex-ui-controls"></a>Handmenü mit großen und komplexen Ui-Steuerelementen

<img src="images/HandMenu_SizeExample.png" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
Es wird empfohlen, die Anzahl der Schaltflächen oder Ui-Steuerelemente in hand angefügten Menüs zu beschränken. Dies liegt daran, dass die erweiterte Interaktion mit einer großen Anzahl von Benutzeroberflächenelementen zu Armermüdung führen kann. Wenn Ihre Erfahrung ein umfangreiches Menü erfordert, bieten Sie dem Benutzer eine einfache Möglichkeit, das Menü weltweit zu sperren. Eine methode, die wir empfehlen, ist das Weltsperren und dann das Menü, wenn die Hand vom Benutzer abfällt oder sich davon kippt. Ein zweites Verfahren besteht in der Möglichkeit, dem Benutzer zu ermöglichen, das Menü direkt mit der anderen Hand zu greifen. Wenn der Benutzer das Menü freilässt, sollte das Menü weltsperren. Auf diese Weise kann ein Benutzer über einen längeren Zeitraum bequem und sicher mit verschiedenen Benutzeroberflächenelementen interagieren. 

Wenn das Menü weltgesperrt ist, stellen Sie sicher, dass Sie eine Möglichkeit zum Verschieben des Menüs bereitstellen und das Menü schließen, wenn es nicht mehr benötigt wird. Machen Sie das Menü verschiebbar, indem Sie Ziehpunkte an den Seiten oder oben im Menü bereitstellen. Fügen Sie eine Schaltfläche zum Schließen hinzu, damit das Menü geschlossen werden kann. Lassen Sie zu, dass das Menü erneut an die Hand angefügt wird, wenn der Benutzer dem Benutzer die Hand stellt. Es wird auch empfohlen, dass die Benutzer an ihre Hand schauen, um falsche Aktivierungen zu verhindern (siehe unten).

**Großes Menü, das ein Benutzerfreundlichkeitsproblem zeigt**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AOPx]

**World-locked menu on hand drop**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AGZi]

**Manuelles Greifen & zum Weltsperren des Menüs**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAf]

## <a name="how-to-prevent-false-activation"></a>Verhindern einer falschen Aktivierung

Wenn Sie das Handmenü nur als Ereignis auslösen, wird es möglicherweise versehentlich angezeigt, wenn Sie es nicht benötigen (falsch positiv), da Benutzer ihre Hände sowohl absichtlich (zur Kommunikation als auch zur Objektbearbeitung) und unbeabsichtigt bewegen. Um falsche Aktivierungen zu reduzieren, fügen Sie neben dem Handmenü einen zusätzlichen Schritt hinzu, um das Handmenü auf dem Handmenü auf zu rufen (z. B. vollständig geöffnete Finger oder der Benutzer, der absichtlich an der Hand blättern soll).

**Flache Handfläche erforderlich**

Wenn Sie eine flache offene Hand benötigen, können Sie eine falsche Aktivierung verhindern, die auftreten kann, wenn der Benutzer Objekte oder Gesten während der Kommunikation innerhalb einer Umgebung bearbeitet. 

**Anving erfordern**

Indem der Benutzer an seine Hand anviert werden muss (entweder mit dem Anving mit den Augen oder mit dem Kopf), werden falsche Aktivierungen verhindert, da der Benutzer seine Aufmerksamkeit als sekundären Aktivierungsschritt auf die Hand richten muss (mit einem abstimmbaren Entfernungsschwellenwert, der für Benutzerfreundlichkeit verwendet wird).  

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Asn4]

---

## <a name="hand-menu-placement-best-practices"></a>Bewährte Methoden für die Platzierung von Handmenüs

In der menschlichen Anatomie ist die Ulnar-Menschlichen ein Menschlichen, der in der Nähe des Ulna-Menschlichen ausgeführt wird. Die Ulna ist ein langer Glied im Unterarm, der sich vom Glied bis zum kleinsten Finger erstreckt.

Im Folgenden finden Sie zwei empfohlene Platzierungen basierend auf unseren Untersuchungen:

:::row:::
    :::column:::
        ![Ulnar-Seitenposition innerhalb der Hand](images/UlnarSideHandMenu.gif)<br>
        **A. Ulnar in der Handfläche**<br>
        Diese Position ist zuverlässig, da sich die Hände nicht überlappen. Dies ist wichtig für eine genaue Handerkennung und Nachverfolgung.
    :::column-end:::
    :::column:::
        ![Ulnar-Seitenposition über der Hand](images/UlnarAboveHandMenu.gif)<br>
        **B. Ulnar oben**<br>
        Dieser Ort ist für Benutzer bequem, da sie ihren Arm nicht zu stark erhöhen müssen, um mit dem Handmenü zu interagieren. Es wird empfohlen, Menüs **13 cm** über der Handfläche zu platzieren und die Schaltflächen in der Ulnar-Handfläche auszurichten. [Erfahren Sie mehr über die optimale Schaltflächengröße.](interactable-object.md)<br>
        <br>
        Aus technischen Gründen empfehlen wir diesen Speicherort mit einer erforderlichen Implementierung: Der Entwickler muss das Menü einfrieren, sobald die entgegengesetzte Hand des Benutzers der Interaktion nahe kommt. Dies vermeidet Jitteriness durch überlappende Hände und ermöglicht auch eine schnellere Ausrichtung der Schaltflächen.<br>
        <br>
        HoloLens 2 Die Hände werden von Kameras genau identifiziert, wenn sie voneinander getrennt sind. Überlappende Hände können dazu führen, dass Handmenüs von der Ankerposition entfernt werden.<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="menu-positions-that-arent-recommended"></a>Menüpositionen, die nicht empfohlen werden

Wir haben Benutzerforschung mit verschiedenen Menülayouts und -standorten durchgeführt. Die folgenden Menüpositionen werden **NICHT** empfohlen. Die Nachteile jeder Studie finden Sie unten:

:::row:::
    :::column:::
        ![Über arm](images/AboveArm.gif)<br>
        **Über dem Arm**<br>
        1 – Schwierig, eine gute Handverfolgung zu verwalten<br>
        2 : Verursacht Benutzermüdigkeit aufgrund einer unnatürlichen Position
    :::column-end:::
    :::column:::
        ![Über den Fingern](images/AboveFingers.gif)<br>
        **Über den Fingern**<br>
        1 – Handermüdung aufgrund der langen Handhaltung<br>
        2: Probleme bei der Handnachverfolgung an Index- und Mittelfingern
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![Obere Mittelfläche](images/handCenter.gif)<br>
        **Obere Mittelfläche**<br>
        1– Probleme bei der Handnachverfolgung aufgrund von überlappenden Händen<br>
        2– Handermüdung aufgrund der langen Handhaltung für die Interaktion mit Menüs
    :::column-end:::
    :::column:::
        ![Fingerspitze oben ](images/TopFingerTip.gif) **Fingerspitze**<br>
        1– Probleme mit der Handverfolgung<br>
        2– Handermüdung, wenn die Hand über dem normalen Zustand hält<br>
        3. Probleme beim Drücken von Schaltflächen mit anderen Fingern aufgrund von begrenztem Abstand zwischen den Fingern
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![Rückseite des Arms](images/BackOfTheArm.gif)<br>
        **Rückseite des Arms**<br>
        1. Kann die Startschaltfläche aus Zufall auslösen<br>
        2 – Keine natürliche oder komfortable Position
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a>Handmenü im MRTK (Mixed Reality Toolkit) für Unity

**[MRTK stellt](https://github.com/Microsoft/MixedRealityToolkit-Unity)** Skripts und Beispielszenen für das Handmenü zur Verfügung. Mit dem Solverskript HandConstraintPalmUp können Sie alle Objekte mit verschiedenen konfigurierbaren Optionen an die Hände anfügen. Die Handmenübeispiele des MRTK enthalten nützliche Optionen wie flache Handfläche und Anvisanforderung, um eine falsche Aktivierung zu verhindern.

* [Hand Menu Documentations](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)
* [Beispielszene für Handmenü](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandMenuExamples.unity)

Sie können Handmenübeispiele in der HoloLens 2 mit der MRTK Examples Hub-App ausprobieren.

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