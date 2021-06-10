---
title: Billboarding und Tag-along
description: Hier erfahren Sie, wie Sie Objekte mit Demieren verwenden, die sich immer darauf ausrichten, den Benutzer in Mixed Reality-Anwendungen zu sehen.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Gaming, Tag-Along, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 0bd1ac2168284d714240c6775468a61ed3e665b8
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600339"
---
# <a name="billboarding-and-tag-along"></a>Billboarding und Tag-along

<br>

<img src="images/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a>Was ist Dies?

Das Erstellen von Objekten ist ein Verhaltenskonzept, das auf Objekte in Mixed Reality angewendet werden kann. Objekte mit Demieren richten sich immer so aus, dass sie dem Benutzer gegenüber stehen. Text- und Menüsysteme sind häufige Anwendungsfälle, in denen statische Objekte, die in der Umgebung des Benutzers platziert werden (weltgesperrt), andernfalls verdeckt oder unlesbar sind, wenn sich Benutzer bewegen.

Objekte mit aktivierter Umdrehung können sich in der Umgebung des Benutzers frei drehen. Sie können je nach Entwurfsüberlegungen auch auf eine einzelne Achse beschränkt werden. Beachten Sie, dass sich objekte, die zu nah an anderen Objekten platziert werden, oder in HoloLens zu nahe gescannte Oberflächen ausschneiden oder verdecken können. Um dies zu vermeiden, denken Sie an den gesamten Fußabdruck, den ein Objekt erzeugen kann, wenn es auf der Achse gedreht wird, die für das Auffahren aktiviert ist.

<br>

---
## <a name="what-is-a-tag-along"></a>Was ist ein Tag-Along?

Tag-Along ist ein Verhaltenskonzept, das Hologrammen hinzugefügt werden kann. Ein Tag-Along-Objekt versucht, in einem Bereich zu bleiben, der dem Benutzer die Interaktion ermöglicht.

![Der HoloLens-Pinbereich ist ein gutes Beispiel für das Tag-Along-Verhalten.](images/tagalong-1000px.jpg)<br>
*Die HoloLens-Startmenü ist ein gutes Beispiel für das Tag-Along-Verhalten.*

Tag-Along-Objekte verfügen über Parameter, die das Verhalten optimieren können. Inhalte können sich in oder außerhalb der Sichtlinie des Benutzers befinden, während sich der Benutzer in seiner Umgebung bewegt. Während sie verschoben werden, versucht der Inhalt, innerhalb der Peripherie des Benutzers zu bleiben, indem er zum Rand der Ansicht gleitet. Der Inhalt ist möglicherweise vorübergehend nicht mehr angezeigt, je nachdem, wie schnell sich der Benutzer bewegt. Wenn der Benutzer auf das Tag-Along-Objekt anviert, wird es ausführlicher angezeigt. Denken Sie daran, dass Inhalte immer "einen Blick weg" sind, sodass Benutzer nie vergessen, in welche Richtung sich ihre Inhalte bewegen.

Zusätzliche Parameter können das Tag-Along-Objekt an den Kopf des Benutzers durch ein Blasenband anfügen. Die beschleunigungs- oder verlangsamungsbeschleunigende Beschleunigung gibt dem Objekt Gewicht, sodass es physisch vorhanden ist. Dieses Spring-Verhalten ist eine Variante, die dem Benutzer hilft, ein genaues mentales Modell für die Funktionsweise von Tag-Along zu erstellen. Audio hilft, andere Hinweise dafür bereitzustellen, wenn Benutzer Objekte im Tag-Along-Modus haben. Audio sollte die Geschwindigkeit der Bewegung verstärken. Ein schneller Kopflauf sollte einen wahrnehmbareren Soundeffekt bieten, während das Gehen mit natürlicher Geschwindigkeit minimale oder gar keine Audioeffekte haben sollte.

Genau wie wirklich kopfgesperrte Inhalte können sich Tag-Along-Objekte als überwältigend oder verzehrend erweisen, wenn sie sich wild oder zu stark in der Ansicht des Benutzers bewegen. Wenn ein Benutzer sich umsieht und dann schnell anhält, teilen seine Sinne ihm mit, dass er beendet wurde. Ihr Gleichgewicht informiert sie darüber, dass sich der Kopf nicht mehr drehen kann und dass sich die Welt nicht mehr drehen kann. Wenn sich das Tag-Along jedoch fortbewegt, wenn der Benutzer beendet wurde, kann dies seine Sinne verwirren.

<br>

---

## <a name="billboarding-and-tag-along-in-mrtk-mixed-reality-toolkit-for-unity"></a>Ausfüllen und Tag-Along im MRTK (Mixed Reality Toolkit) für Unity
**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** stellt Skripts für das Verhalten beim Generieren und Tag-Along bereit. Weisen Sie jedem Objekt das Skript "Scripts.cs" zu, um das Verhaltensverhalten zu erweitern und das Objekt immer auf Sie zu treffen. Verwenden Sie das Skript RadialView.cs, um das Tag-Along-Verhalten hinzuzufügen. Sie können verschiedene Optionen anpassen, z. B. Lerpingzeit, Entfernung und Grad.

* [MRTK – Radial View Solver](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver#radialview)
* [MRTK – Skript "Scripts"](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


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