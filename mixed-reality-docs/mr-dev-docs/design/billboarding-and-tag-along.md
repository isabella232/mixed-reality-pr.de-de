---
title: Billboarding und Tag-along
description: Erfahren Sie, wie Sie Objekte mit Überhing verwenden, die sich immer so ausrichten, dass sie dem Benutzer in Mixed Reality-Anwendungen gegenüber stehen.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Teering, Tag-Along, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 7ffcbe1d3401601e92eb1ac81dfd84f2af9e8e79eeea809b01a1e943a85f0db9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214162"
---
# <a name="billboarding-and-tag-along"></a>Billboarding und Tag-along

<br>

<img src="images/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a>Was ist Dies?

Die Überhingung ist ein Verhaltenskonzept, das auf Objekte in Mixed Reality angewendet werden kann. Objekte mit Freundlicherung richten sich immer nach dem Benutzer. Text- und Menüsysteme sind gängige Anwendungsfälle, in denen statische Objekte, die in der Umgebung des Benutzers platziert werden (weltgesperrt), ansonsten verdeckt oder unlesbar wären, wenn Benutzer sich bewegen.

Objekte mit aktivierter Drehung können in der Umgebung des Benutzers frei rotiert werden. Je nach Entwurfsüberlegungen können sie auch auf eine einzelne Achse beschränkt werden. Beachten Sie, dass sich überlappende Objekte selbst beschneiden oder verdecken können, wenn sie zu nah bei anderen Objekten oder in HoloLens, zu nah an gescannten Oberflächen platziert werden. Um dies zu vermeiden, denken Sie an den Gesamtfußabdruck, den ein Objekt erzeugen kann, wenn es auf der Achse rotiert wird, die für Diebung aktiviert ist.

<br>

---
## <a name="what-is-a-tag-along"></a>Was ist ein Tag-Along?

Tag-Along ist ein Verhaltenskonzept, das Hologrammen hinzugefügt werden kann. Ein Tag-Along-Objekt versucht, in einem Bereich zu bleiben, der dem Benutzer die interaktionsbeweglich ermöglicht.

![Der HoloLens ist ein gutes Beispiel dafür, wie sich das Tag-Along-Verhalten verhält.](images/tagalong-1000px.jpg)<br>
*Die HoloLens Startmenü ist ein gutes Beispiel für das Tag-Along-Verhalten.*

Tag-Along-Objekte verfügen über Parameter, die das Verhalten optimieren können. Inhalte können sich in oder aus der Sicht des Benutzers heraus bewegen, während sich der Benutzer in seiner Umgebung bewegt. Während sie sich bewegen, versucht der Inhalt, innerhalb der Benutzerfreundlichkeit zu bleiben, indem er zum Rand der Ansicht gleitet. Der Inhalt kann vorübergehend nicht mehr angezeigt werden, je nachdem, wie schnell der Benutzer bewegt wird. Wenn der Benutzer das Tag-Along-Objekt anviert, wird es vollständiger angezeigt. Denken Sie daran, dass Inhalte immer "einen Blick entfernt" sind, sodass Benutzer nie vergessen, in welche Richtung sich ihre Inhalte bewegen.

Zusätzliche Parameter können dazu sorgen, dass das Tag-Along-Objekt durch ein Bänder an den Kopf des Benutzers angefügt wird. Durch die Beschleunigung oder Verlangsamung wird das Objekt gewichtet, wodurch es physisch besser vorhanden ist. Dieses Spring-Verhalten ist ein Preismodell, das dem Benutzer hilft, ein genaues mentales Modell für die Funktionsweise von Tag-Along zu erstellen. Audio hilft bei der Bereitstellung weiterer Hinweise, wenn Benutzer Objekte im Tag-Along-Modus haben. Audio sollte die Geschwindigkeit der Bewegung verstärken. Eine schnelle Kopfdrehung sollte einen deutlicheren Soundeffekt bieten, während das Gehen mit natürlicher Geschwindigkeit minimale oder keine Audioeffekte haben sollte.

Genau wie wirklich kopfgesperrte Inhalte können sich Tag-Along-Objekte als überfordernd oder überfordernd erweisen, wenn sie sich in der Ansicht des Benutzers wild bewegen oder zu stark springen. Wenn ein Benutzer sich umsieht und dann schnell anhält, teilen seine Sinne ihm mit, dass er angehalten wurde. Ihr Gleichgewicht informiert sie darüber, dass sich ihr Kopf nicht mehr drehen kann und dass ihr Sehvermögen die Welt nicht mehr sieht. Wenn das Tag-Along jedoch weiter bewegt wird, wenn der Benutzer angehalten wurde, kann dies die Sinne verwirren.

<br>

---

## <a name="billboarding-and-tag-along-in-mrtk-mixed-reality-toolkit-for-unity"></a>Erstellen und Markieren im MRTK (Mixed Reality Toolkit) für Unity
**[MRTK stellt](https://github.com/Microsoft/MixedRealityToolkit-Unity)** Skripts für das Verhalten von "Ing" und "tag-along" zur Verfügung. Weisen Sie das Skript "Soll.cs" jedem Objekt zu, um Einfügeverhalten hinzuzufügen und das Objekt immer ins Gesicht zu stellen. Verwenden Sie das Skript RadialView.cs, um das Tag-Along-Verhalten hinzuzufügen. Sie können verschiedene Optionen anpassen, z. B. Lerpingzeit, Entfernung und Grad.

* [MRTK – Solver für radiale Ansicht](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver#radialview)
* [MRTK – Skript "Soll"](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


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