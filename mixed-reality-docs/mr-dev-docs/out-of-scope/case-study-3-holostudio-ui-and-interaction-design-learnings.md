---
title: 'Fallstudie: 3 HoloStudio Der Benutzeroberflächen- und Interaktionsentwurfslernen'
description: Lernprozesse für die Gestaltung von HoloStudio-Benutzeroberfläche und -Interaktion
author: rwinj
ms.author: marcghal
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, HoloStudio, Windows Mixed Reality
ms.openlocfilehash: 1b384a10d3fe53cf7e69c2e8437904040322dc213d9473d9ae9abf272c08ec5e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115195869"
---
# <a name="case-study---3-holostudio-ui-and-interaction-design-learnings"></a>Fallstudie: 3 HoloStudio Der Benutzeroberflächen- und Interaktionsentwurfslernen

[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) war eine der ersten Microsoft-Apps für HoloLens. Aus diesem Grund mussten wir neue bewährte Methoden für die 3D-Benutzeroberfläche und das Interaktionsdesign erstellen. Wir haben dies durch viele Benutzertests, Prototyperstellung und Test- und Fehlertests durchgeführt.

Wir wissen, dass nicht jeder über die Ressourcen verfügt, die für diese Art von Forschung zur Verfügung stehen. Daher haben wir unseren Sr. Holographic Designer, Ghaly, drei Dinge teilen, die wir bei der Entwicklung von HoloStudio über benutzeroberfläche und Interaktionsentwurf für HoloLens-Apps gelernt haben.

## <a name="watch-the-video"></a>Video ansehen

>[!VIDEO https://www.youtube.com/embed/sX6yKHmN1qM]

## <a name="problem-1-people-didnt-want-to-move-around-their-creations"></a>Problem #1: Personen wollten sich nicht um ihre Erstellungen bewegen.

Wir haben die Workbench ursprünglich in HoloStudio Rechteck entworfen, ähnlich wie in der realen Welt. Das Problem ist, dass Die Benutzer eine Lebensdauer haben, die sie dazu beträgt, still zu bleiben, wenn sie am Arbeitsplatz oder vor einem Computer arbeiten, sodass sie sich nicht um die Workbench bewegen und ihre 3D-Erstellung von allen Seiten aus erkunden.

![Das rechteckige Design der Workbench in HoloStudio Benutzer davon ab, sich zu bewegen und ihre Erstellungen von allen Seiten aus zu sehen.](images/rectangular-workbench-500px.jpg)

Wir hatten die Erkenntnis, die Workbench rund zu machen, sodass es keinen "front" oder klaren Ort gab, an dem Sie stehen sollten. Als wir dies getestet haben, begannen die Menschen plötzlich, sich zu bewegen und ihre Erstellungen selbst zu untersuchen.

![Der Entwurf der Ringarbeits-Workbench hat Benutzer dazu aufgefordert, ihre Erstellungen zu durcharbeiten.](images/circular-workbench-500px.jpg)

**Was wir gelernt haben**

Denken Sie immer darüber nach, was für den Benutzer bequem ist. Die Nutzung des physischen Raums ist ein kaltes Feature HoloLens und etwas, das Sie nicht mit anderen Geräten tun können.

## <a name="problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame"></a>Problem #2: Modale Dialoge befinden sich manchmal nicht im holografischen Rahmen

Manchmal kann es sein, dass Ihr Benutzer in eine andere Richtung als etwas sucht, das seine Aufmerksamkeit in Ihrer App erfordert. Auf einem PC können Sie einfach einen Dialog öffnen, aber wenn Sie dies im Gesicht einer Person in einer 3D-Umgebung tun, kann es so aussehen, als würde sich der Dialog im Weg halten. Sie benötigen sie, um die Nachricht zu lesen, aber ihr Instinktiv besteht in dem Versuch, sie zu verlassen. Diese Reaktion ist hervorragend, wenn Sie ein Spiel spielen, aber in einem Tool, das für die Arbeit entwickelt wurde, ist es weniger ideal.

Nachdem wir einige verschiedene Dinge versucht haben, haben wir uns schließlich mit der Verwendung eines "Denkblasensystems" für unsere Dialoge begnötige, und es wurden Tend tend tend- hinzugefügt, denen Benutzer folgen können, wo ihre Aufmerksamkeit in unserer Anwendung benötigt wird. Wir haben auch die Tend tend, was ein Gefühl von Direktionalität implizierte, sodass die Benutzer wissen, wo sie hingehen sollten.

![Das "Thought Bubble"-System umfasste pulsing tend , was ein Gefühl der Richtung lieferte, wodurch Benutzer zu den Stellen führen, an denen ihre Aufmerksamkeit in der App benötigt wurde.](images/thought-bubble-500px.jpg)

**Was wir gelernt haben**

In 3D ist es viel schwieriger, Benutzer über Dinge zu warnen, auf die sie achten müssen. Die Verwendung von [](../design/spatial-sound.md)Aufmerksamkeitsführungen wie raumbezogenem Sound, Lichtstrahl oder Denkblasen kann Benutzer zu dem Ort führen, an dem sie sich auch finden müssen.

## <a name="problem-3-sometimes-ui-can-get-blocked-by-other-holograms"></a>Problem #3: Manchmal kann die Benutzeroberfläche durch andere Hologramme blockiert werden.

Es gibt Zeiten, in denen ein Benutzer mit einem Hologramm und den zugehörigen UI-Steuerelementen interagieren möchte, sie jedoch nicht angezeigt werden, da sich ein anderes Hologramm vor ihnen befindet. Während der Entwicklung von HoloStudio test and error verwendet, um eine Lösung dafür zu finden.

![Ein ui-Steuerelement, das einem Hologramm zugeordnet ist, kann blockiert werden, wenn ein anderes Hologramm zwischen ihm und dem Benutzer HoloLens.](images/ui-blocked-500px.jpg)

Wir haben versucht, das UI-Steuerelement näher an den Benutzer zu verschieben, damit es nicht blockiert werden konnte, aber es war für den Benutzer nicht benutzerfreundlich, ein Steuerelement in Ihrer Nähe zu betrachten, während gleichzeitig ein hologramm, das weit entfernt war, betrachtet wurde. Wenn wir das Steuerelement jedoch vor das hologramm verschoben haben, das dem Benutzer am nächsten liegt, hat es sich so an gefühlt, als wäre es vom Hologramm getrennt, das es beeinflussen sollte.

Am Ende haben wir das UI-Steuerelement in den gleichen Abstand wie das Hologramm, dem es zugeordnet ist, in den gleichen Abstand zum Benutzer entfernt, damit beide verbunden sind. Dadurch kann der Benutzer mit dem Steuerelement interagieren, obwohl es verdeckt wurde.

![Die Lösung: Wir haben das Ui-Steuerelement in den Ghosting aufgenommen, das sowohl die Interaktion mit dem Steuerelement ermöglicht als auch das Gefühl hat, dass es mit dem Hologramm verbunden ist, das es beeinflusst hat.](images/ghosting-ui-500px.jpg)

**Was wir gelernt haben**

Benutzer müssen problemlos auf Ui-Steuerelemente zugreifen können, auch wenn sie blockiert wurden. Finden Sie daher Methoden heraus, um sicherzustellen, dass Benutzer ihre Aufgaben unabhängig davon ausführen können, wo sich ihre Hologramme in der realen Welt befinden.

## <a name="about-the-author"></a>Informationen zum Autor

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Marcus Ghaly" width="60" height="60" src="images/marcus-ghaly-200px.jpg"></td>
<td style="border-style: none"><b>Gegen ghaly</b><br>Sr. Holographic Designer @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Siehe auch
* [Instinktive Interaktionen](../design/interaction-fundamentals.md)
