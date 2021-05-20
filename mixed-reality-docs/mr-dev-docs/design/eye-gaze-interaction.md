---
title: Interaktion durch Anvisieren
description: Erfahren Sie mehr über die auf Augen und Anvischen basierenden Interaktionen auf HoloLens 2 und die neuen Ebenen des Kontexts und des menschlichen Verständnisses, wenn es sich um holografische Erfahrungen handelt.
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
keywords: Eye Tracking, Mixed Reality, Input, Eye-Gaze, Mixed Reality Headset, Windows Mixed Reality Headset, Virtual Reality Headset, HoloLens, MRTK, Mixed Reality Toolkit, Design, Interaktionen
ms.openlocfilehash: 207f8d0f179f722a2e4dd6d6e2bdd9cbf75b2250
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196575"
---
# <a name="eye-gaze-based-interaction-on-hololens-2"></a>Interaktion mit den Augen auf HoloLens 2

![Eye tracking demo in MRTK](images/mrtk_et_scenemenu.jpg)

Eine unserer interessanten neuen Funktionen für HoloLens 2 ist eye tracking. Auf unserer Seite [Eye tracking on HoloLens 2 (Blickverfolgung auf HoloLens 2](eye-tracking.md) Seite) haben wir erwähnt, dass jeder Benutzer eine [Kalibrierung](/hololens/hololens-calibration)durchlaufen muss, einige Entwicklerleitfäden bereitgestellt und Anwendungsfälle für eye tracking hervorgehoben. Die Eingabe mit den Augen ist immer noch eine neue Art von Benutzereingabe, und es gibt viel zu lernen. 

Während die Eingabe mit den Augen nur einfach in unserer Holographic Shell-Oberfläche verwendet wird (die Benutzeroberfläche, die Sie sehen, wenn Sie Ihre HoloLens 2 starten), zeigen mehrere Apps, z. B. ["HoloLens Playground",](https://www.microsoft.com/p/mr-playground/9nb31lh723s2)hervorragende Beispiele dafür, wie die Eingabe mit den Augen zur Magischen Ihrer holografischen Erfahrung beifügen kann.
Auf dieser Seite werden Entwurfsüberlegungen für die Integration von Anverweisen mit den Augen für die Interaktion mit Ihren holografischen Anwendungen erörtert.

Sie lernen wichtige Vorteile und auch einzigartige Herausforderungen kennen, die mit Blickeingaben verbunden sind. Auf dieser Grundlage bieten wir mehrere Entwurfsempfehlungen, die Ihnen helfen, benutzerfreundliche Benutzeroberflächen zu erstellen, die mit blickgestützten Blicken unterstützt werden. 

## <a name="device-support"></a>Geräteunterstützung

<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><strong>Feature</strong></td>
     <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1. Generation)</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
</tr>
<tr>
     <td>Anväuten mit den Augen</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>

## <a name="head-and-eye-tracking-design-concepts-demo"></a>Demo zu Designkonzepten für Head- und Eyetracking

Wenn Sie die Entwurfskonzepte für Head und Eye Tracking in Aktion sehen möchten, sehen Sie sich unsere Videodemo **designing Holograms - Head Tracking and Eye Tracking (Entwerfen von Hologrammen – Kopfverfolgung und Eye tracking)** unten an. Wenn Sie fertig sind, fahren Sie mit einem ausführlicheren Einblick in bestimmte Themen fort.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

*Dieses Video stammt aus der App "Entwerfen von Hologrammen" HoloLens 2. Laden Sie die vollständige Benutzeroberfläche hier herunter, und nutzen Sie [sie.](https://aka.ms/dhapp)*

## <a name="eye-gaze-input-design-guidelines"></a>Richtlinien für den Entwurf von Eingaben mit den Augen

Das Erstellen einer Interaktion, die sich schnell bewegende Blickrichtung nutzt, kann eine Herausforderung darstellen. In diesem Abschnitt werden die wichtigsten Vorteile und Herausforderungen zusammengefasst, die beim Entwerfen Ihrer Anwendung zu berücksichtigen sind. 

### <a name="benefits-of-eye-gaze-input"></a>Vorteile der Eingabe mit dem Anving mit den Augen

- **Zeigen mit hoher Geschwindigkeit.** Das Augengefäuss ist die schnellste Reaktion im menschlichen Körper. 

- **Wenig Aufwand.** Es sind kaum physische Bewegungen erforderlich. 

- **Selbstverständlichkeit.** Informationen zu den Augenbewegungen eines Benutzers, die von Benutzern häufig als "Mind Reading" (Denken lesen) beschrieben werden, informieren das System darüber, welches Ziel der Benutzer einspricht. 

- **Alternativer Eingabekanal.** Mit den Augen können Sie eine leistungsstarke unterstützungsbasierte Eingabe für Hand- und Spracheingaben bereitstellen, die auf der erfahrungsbasierten Erfahrung der Benutzer basierend auf ihrer Hand-Augen-Koordination aufbaut.

- **Visuelle Aufmerksamkeit.** Ein weiterer wichtiger Vorteil ist die Möglichkeit, daraus zu ziehen, worauf ein Benutzer achten muss. Dies kann in verschiedenen Anwendungsbereichen helfen, von der effektiveren Auswertung verschiedener Entwürfe bis hin zur Unterstützung intelligenterer Benutzeroberflächen und verbesserter sozialer Hinweise für die Remotekommunikation.

Kurz gesagt bietet die Verwendung des Anvisierens mit den Augen als Eingabe ein schnelles und müheloses kontextbezogenes Eingabesignal. Dies ist in Kombination mit  anderen  Eingaben wie Spracheingaben und manuellen Eingaben zum Bestätigen der Absicht des Benutzers leistungsstark.


### <a name="challenges-of-eye-gaze-as-an-input"></a>Herausforderungen beim Anvingen mit den Augen als Eingabe

Obwohl das Anvieren mit den Augen verwendet werden kann, um zufriedenstellende Benutzererfahrungen zu schaffen, die Ihnen das Gefühl geben, ein Superhero zu sein, ist es auch wichtig zu wissen, wofür es nicht gut ist, dies entsprechend zu berücksichtigen. In der folgenden Liste werden einige *zu berücksichtigende* Herausforderungen und deren Bewältigung bei der Arbeit mit Der Blickeingabe erläutert: 

- **Ihr Anving mit den Augen ist "immer ein"** In dem Moment, in dem Sie Ihre Augenlider öffnen, beginnen Ihre Augen mit der Korrektur der Dinge in der Umgebung. Wenn Sie auf jedes von Ihnen durchgeführte Aussehen reagieren und versehentlich Aktionen ausführen, da Sie etwas zu lange durchdrungen haben, würde dies zu einer unbesättigenden Erfahrung führen.
Es wird empfohlen, das Anvieren mit  den Augen mit einem Sprachbefehl, einer Handgeste, einem Schaltflächenklick oder einem erweiterten Verweilen zu kombinieren, um die Auswahl eines Ziels auszulösen (weitere Informationen finden Sie unter Anvieren mit den Augen und [Ausführen).](gaze-and-commit-eyes.md)
Diese Lösung ermöglicht auch einen Modus, in dem sich der Benutzer frei umschauen kann, ohne durch unfreiwilliges Auslösen von etwas überfordert zu werden. Dieses Problem sollte auch beim Entwerfen von visuellem und akustischem Feedback beim Betrachten eines Ziels berücksichtigt werden.
Versuchen Sie nicht, den Benutzer mit sofortigen Pop-Out-Effekten oder Hover-Sounds zu überfordern. Dezentität ist der Schlüssel. Im Folgenden werden einige bewährte Methoden für dieses Thema erläutert, wenn wir über [Entwurfsempfehlungen](eye-gaze-interaction.md#design-recommendations)sprechen.

- **Beobachtung und Kontrolle** Stellen Sie sich vor, Sie möchten ein Foto genau an der Wand begradigen. Sie schauen zuerst auf den Rahmen und dann auf die Umgebung, um festzustellen, ob es richtig ausgerichtet ist. Stellen Sie sich nun vor, wie Sie dies tun würden, wenn Sie Das Anvieren mit den Augen als Eingabe verwenden möchten, um das Bild zu verschieben. Schwierig, nicht wahr? Dies beschreibt die doppelte Rolle des Anverfolgens mit den Augen, wenn es sowohl für die Eingabe als auch für die Steuerung erforderlich ist. 

- **Belassen Sie vor dem Klicken:** Für schnelle Zielauswahlen hat die Forschung gezeigt, dass das Anvieren mit den Augen eines Benutzers weitergehen kann, bevor ein manueller Klick (z. B. ein Tippen in die Luft) erfolgen kann. Achten Sie besonders darauf, das Signal für schnelles Anvisieren mit den Augen mit langsamerer Steuereingabe (z. B. Sprache, Hände, Controller) zu synchronisieren.

- **Kleine Ziele:** Kennen Sie das Gefühl, wenn Sie versuchen, Text zu lesen, der nur etwas zu klein ist, um unerwünscht zu lesen? Dieses belastungsbeanspruchende Gefühl für Ihre Augen kann dazu führen, dass Sie sich unaussichtlich und unaussichtlich fühlen, da Sie versuchen, Ihre Augen neu zu justieren, um sich besser zu konzentrieren.
Dies ist ein Gefühl, das Sie in Ihren Benutzern aufrufen können, wenn Sie sie zwingen, Ziele auszuwählen, die in Ihrer Anwendung zu klein sind, indem Sie eye targeting verwenden.
Damit Sie für Ihre Benutzer eine angenehme und komfortable Erfahrung schaffen, sollte bei Zielen für Ihren Entwurf der Sehwinkel mindestens 2 Grad (vorzugsweise mehr) betragen.

- **Unregelmäßige Anvieren mit den Augen** Unsere Augen führen schnelle Bewegungen von der Fixierung zur Fixierung durch. Wenn Sie Scanwege aufgezeichneter Blickbewegungen betrachten, können Sie die Flatterhaftigkeit erkennen. Ihre Augen bewegen sich schnell und springen im Vergleich zu *Anvieren* mit dem Kopf oder *Handbewegungen.*  

- **Nachverfolgung der Zuverlässigkeit:** Die Genauigkeit der Blickverfolgung kann sich beim Ändern des Lichts ein wenig beeinträchtigen, wenn sich Ihre Augen an die neuen Bedingungen anpassen.
Dies sollte sich nicht unbedingt auf den Anwendungsentwurf auswirken, da die Genauigkeit innerhalb der 2°-Einschränkung liegen sollte, kann es jedoch erforderlich sein, dass der Benutzer erneut kalibriert. 


## <a name="design-recommendations"></a>Entwurfsempfehlungen
Im Folgenden sind spezifische Entwurfsempfehlungen aufgeführt, die auf den beschriebenen Vorteilen und Herausforderungen für die Eingabe mit den Augen basieren:

1. **Das Anvischen mit den Augen ist nicht identisch mit dem Anvischen mit dem Kopf:**
    - **Überlegen Sie, ob schnelle, aber unbende Augenbewegungen zu Ihrer Eingabeaufgabe passen:** Während unsere schnellen und lappenden Augenbewegungen sich gut in der schnellen Auswahl von Zielen in unserem Sichtfeld befinden, sind sie weniger anwendbar für Aufgaben, die reibungslose Eingabebewegungen erfordern (z. B. Zeichnen oder Umkreisen von Anmerkungen). In diesem Fall ist das Zeigen mit Hand oder Kopf zu bevorzugen.
  
    - **Vermeiden Sie es, etwas direkt an das Anvieren mit den Augen des Benutzers (z. B. einen Schieberegler oder Cursor) anfügen.**
Bei Cursorn kann dies aufgrund von geringfügigen Offsets im projizierten Signal zum Anvisieren mit den Augen zu einem "flüchtigen Cursoreffekt" führen. Bei einem Schieberegler kann es zu Konflikten mit der doppelten Rolle führen, den Schieberegler mit Ihren Augen zu steuern, während gleichzeitig überprüft werden soll, ob sich das Objekt an der richtigen Position befindet. Für das Beispiel des Schiebereglers ist es sinnvoller, das Anvingen mit den Augen in Kombination mit Handgesten zu verwenden. Dies bedeutet, dass der Benutzer schnell und mühelos zwischen vielen Schiebereglern wechseln und die Hand hochziehen und den Daumen und den Zeigefinger anheften kann, um sie zu greifen und zu bewegen. Wenn der Schieberegler freigegeben wird, wird der Schieberegler nicht mehr bewegt. Benutzer könnten überfordert und abgelenkt werden, insbesondere, wenn das Signal für diesen Benutzer unpräzise ist. 
  
2. **Kombinieren Sie das Anvingen mit den Augen mit anderen Eingaben:** Die Integration von EyeTracking in andere Eingaben, z. B. Handgesten, Sprachbefehle oder Tastendruck, bietet mehrere Vorteile:
    - **Kostenlose Beobachtung zulassen:** Da die Hauptaufgabe unserer Augen die Beobachtung unserer Umgebung ist, ist es wichtig, dass Benutzer sich umschauen dürfen, ohne Feedback oder Aktionen auszulösen (visuell, a audity und so weiter). 
    Die Kombination von EyeTracking mit einem anderen Eingabesteuerfeld ermöglicht einen reibungslosen Übergang zwischen der Eyetracking-Beobachtung und den Eingabesteuerungsmodi.
  
    - **Leistungsstarker Kontextanbieter:** Die Verwendung von Informationen darüber, wo und was der Benutzer beim Sagen eines Sprachbefehls oder mithilfe einer Handgeste betrachtet, ermöglicht die nahtlose Kanalierung der Eingabe über das Sichtfeld. Beispiel: Sagen Sie _"Put that there",_ um ein Hologramm schnell und reibungslos in der gesamten Szene auszuwählen und zu positionieren, indem Sie ein Ziel und sein beabsichtigtes Ziel betrachten. 

    - **Notwendigkeit der Synchronisierung von kombinierten Eingaben:** Die Kombination schneller Augenbewegungen mit komplexeren Eingaben, z. B. langen Sprachbefehlen oder Handgesten, birgt das Risiko, dass der Benutzer sich bereits umsehen kann, bevor der zusätzliche Eingabebefehl abgeschlossen und erkannt wird. Wenn Sie ihre eigenen Eingabesteuerelemente erstellen (z. B. benutzerdefinierte Handgesten), stellen Sie sicher, dass Sie den Beginn dieser Eingabe oder die ungefähre Dauer protokollieren, um sie mit dem zu korrelieren, was ein Benutzer in der Vergangenheit betrachtet hat.
    
3. **Dezentes Feedback für Blickverfolgungseingaben:** Es ist hilfreich, Feedback zu geben, wenn ein Ziel betrachtet wird, um anzugeben, dass das System wie vorgesehen funktioniert, aber dezent gehalten werden sollte. Dies kann das langsame Ein- und Ausblenden, visuelle Hervorhebungen oder andere dezente Zielverhaltensweisen wie langsame Bewegung, z. B. eine geringfügige Erhöhung der Zielgröße, umfassen. Dies gibt an, dass das System ordnungsgemäß erkannt hat, dass der Benutzer ein Ziel ansieht, ohne den aktuellen Workflow des Benutzers unnötig zu unterbrechen. 

4. **Vermeiden Sie das Erzwingen unnatürlicher Augenbewegungen als Eingabe:** Zwingen Sie Benutzer nicht, bestimmte Augenbewegungen (Anvischen von Gesten) zu verwenden, um Aktionen in Ihrer Anwendung auszulösen.

5. **Berücksichtigen Sie Ungenauigkeiten:** Wir unterscheiden zwei Arten von Ungenauigkeiten, die für Benutzer wahrnehmbar sind: Offset und Jitter. Die einfachste Möglichkeit, einen Offset zu adressieren, besteht darin, ausreichend große Ziele für die Interaktion bereitzustellen. Es wird empfohlen, einen visuellen Winkel größer als 2° als Verweis zu verwenden. Ihre Miniaturansicht liegt beispielsweise etwa 2° im visuellen Winkel, wenn Sie den Arm ausdehnen. Dies führt zu folgender Richtlinie:
    - Erzwingen Sie nicht, dass Benutzer kleine Ziele auswählen. Untersuchungen haben ergeben, dass Benutzer ihre Interaktionen als mühelos und unwahrscheinlich beschreiben, wenn Ziele ausreichend groß sind und das System gut entworfen ist. Wenn Ziele zu klein sind, empfinden Benutzer die Erfahrung als ermüdend und frustrierend.
  
<br>

Auf dieser Seite haben Sie eine gute Übersicht erhalten, damit Sie mit dem Anvischen mit den Augen als Eingabe in Mixed Reality beginnen können. Um mit der Entwicklung zu beginnen, sehen Sie sich unsere Informationen zu Anvingen mit den Augen [in Unity](https://aka.ms/mrtk-eyes) und [Anvingen mit den Augen in DirectX an.](../develop/native/gaze-in-directx.md)


## <a name="see-also"></a>Siehe auch
* [Komfort](comfort.md)
* [Anvingen mit den Augen in DirectX](../develop/native/gaze-in-directx.md)
* [Anvingen mit den Augen in Unity (Mixed Reality Toolkit)](https://aka.ms/mrtk-eyes)
* [Blickverfolgung auf HoloLens 2](eye-tracking.md)
* [Anvisieren und Ausführen](gaze-and-commit.md)
* [Anvisieren und Verweilen](gaze-and-dwell.md)
* [Spracheingabe](../out-of-scope/voice-design.md)