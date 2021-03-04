---
title: Billboarding und Tag-along
description: Erfahren Sie, wie Sie Objekte mit dem Abgleichen von Objekten verwenden, die sich immer für den Benutzer in gemischten Reality-Anwendungen orientieren.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, fakboardingvorgang, tagparallel, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens, mrtk, Mixed Reality Toolkit
ms.openlocfilehash: f0a5c4fc66e287c04fe8fa42c0c671e895a26169
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759406"
---
# <a name="billboarding-and-tag-along"></a>Billboarding und Tag-along

<br>

<img src="images/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a>Was ist die Abrechnung?

Bei der Abrechnung handelt es sich um ein Verhaltens Konzept, das auf Objekte in gemischter Realität angewendet werden kann. Objekte mit einem Abrechnungs-Board orientieren sich stets an dem Benutzer. Text-und Menüsysteme sind gängige Anwendungsfälle, in denen statische Objekte, die in der Umgebung des Benutzers platziert werden (weltweit gesperrt), andernfalls verdeckt oder unlesbar sind, wenn sich die Benutzer bewegen.

Objekte mit aktiviertem fakboardingvorgang können in der Benutzerumgebung frei rotiert werden. Sie können je nach Entwurfs Überlegungen auch auf eine einzelne Achse beschränkt werden. Beachten Sie, dass die Objekte, die von einem Abbild untergebracht werden, sich selbst durch ein-oder ausgeblendet werden können, wenn Sie sich zu nahe an anderen Objekten befinden oder in hololens zu schließen. Um dies zu vermeiden, stellen Sie sich den Gesamt Speicherbedarf vor, der von einem Objekt erzeugt wird, wenn es auf der Achse gedreht wird, die für das

<br>

---
## <a name="what-is-a-tag-along"></a>Was ist ein Tag?

Tagparallel ist ein Verhaltens Konzept, das holograms hinzugefügt werden kann. Ein Tag-entlang-Objekt versucht, in einem Bereich zu bleiben, der es dem Benutzer ermöglicht, komfortabel zu interagieren.

![Das hololens-Pins-Panel ist ein gutes Beispiel dafür, wie sich das Tag-entlang verhält.](images/tagalong-1000px.jpg)<br>
*Das hololens-Startmenü ist ein gutes Beispiel für das tagparallel Verhalten.*

Tagbasierte Objekte verfügen über Parameter, die die Art und Weise, wie Sie sich Verhalten, optimieren können. Der Inhalt kann sich innerhalb oder außerhalb der Sicht des Benutzers befinden, während sich der Benutzer um seine Umgebung bewegt. Während des Verschiebens versucht der Inhalt, in der Peripherie des Benutzers zu bleiben, indem er an den Rand der Ansicht bewegt wird. Der Inhalt ist möglicherweise vorübergehend außerhalb der Ansicht, je nachdem, wie schnell der Benutzer bewegt wird. Wenn der Benutzer in Richtung des tagbasierten Objekts zeigt, wird es vollständig in die Ansicht integriert. Stellen Sie sich vor, dass Inhalte immer "auf einen Blick entfernt" werden, damit Benutzer niemals vergessen, welche Richtung ihr Inhalt hat.

Zusätzliche Parameter können dazu führen, dass das Tag-an-Objekt von einem Gummi Band an den Kopf des Benutzers angefügt wird. Durch die Beschleunigung oder Verlangsamung der Dämpfung wird das-Objekt gewichtet, sodass es physisch vorhanden ist. Dieses Spring Verhalten ist ein kostengünstiger, mit dem der Benutzer ein genaues mentales Modell zur Funktionsweise von Tag-Along erstellen kann. Audiodaten helfen bei der Bereitstellung anderer Hinweise, wenn Benutzer Objekte im tagbasierten Modus haben. Audiogeschwindigkeit sollte die Geschwindigkeit der Bewegung verstärken. eine schnelle Kopfzeile sollte einen auffälligeren Soundeffekt bereitstellen, während das laufen mit einer natürlichen Geschwindigkeit minimale oder keine Audioeffekte aufweisen sollte.

Ebenso wie wirklich mit dem Titel gesperrter Inhalt können sich taggingobjekte als überwältigend oder übersichtlich erweisen, wenn Sie in der Ansicht des Benutzers sehr stark verschoben werden. Wenn ein Benutzer die Suche durchsucht, werden die zugehörigen Sinne schnell angehalten. Ihr Saldo informiert Sie darüber, dass ihre Kopfzeile angehalten wurde, und ihre Vision sieht, dass die Welt nicht mehr schaltet. Wenn das Tag-Along jedoch weiterhin verschoben wird, wenn der Benutzer angehalten wurde, kann es seine Sinne verwirren.

<br>

---

## <a name="billboarding-and-tag-along-in-mrtk-mixed-reality-toolkit-for-unity"></a>Fakboardingvorgang und tagparallel in mrtk (Mixed Reality Toolkit) für Unity
**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** stellt Skripts für das fakboardingverhalten und das tagbasierte Verhalten bereit. Weisen Sie das Billboard.cs-Skript einem beliebigen Objekt zu, um das Verhalten von Verhaltensweisen hinzuzufügen, und machen Sie das Objekt immer als Verwenden Sie das RadialView.cs-Skript, um das tagbasierte Verhalten hinzuzufügen. Sie können verschiedene Optionen wie z. b. lerping-Zeit, Entfernung und Grad anpassen.

* [-Solver der mrtk-radialen Ansicht](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/solvers/solver.md#radialview)
* [Mrtk-Billboard-Skript](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


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
