---
title: Interaktion durch Anvisieren
description: Erfahren Sie mehr über interaktionen mit den Augen und anvogrammbasierten HoloLens 2 und die neuen Kontext- und menschlichen Verständnisebenen, wenn dies in holografischen Erfahrungen zu bieten ist.
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
keywords: Eye tracking, Mixed Reality, Input, Eye-Gaze, Mixed Reality Headset, Windows Mixed Reality Headset, Virtual Reality Headset, HoloLens, MRTK, Mixed Reality Toolkit, Design, Interaktionen
ms.openlocfilehash: aec41c6654ce10254648e90e08a09ff9adade75a3dc63af81a0953b67b95729f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220956"
---
# <a name="eye-gaze-based-interaction-on-hololens-2"></a>Interaktion mit dem Anving mit den Augen HoloLens 2

![Eyetracking-Demo in MRTK](images/mrtk_et_scenemenu.jpg)

Eine unserer interessanten neuen Funktionen für HoloLens 2 ist eye tracking. Auf unserer [Seite eye tracking auf HoloLens 2](eye-tracking.md) haben wir erwähnt, dass jeder Benutzer eine Kalibrierung durchgehen muss, einige Entwicklerleitfäden bereitgestellt und Anwendungsfälle für eye tracking hervorgehoben hat. [](/hololens/hololens-calibration) Die Eingabe mit den Augen ist immer noch eine neue Art von Benutzereingabe, und es gibt viel zu lernen. 

Während die Eingabe mit dem Anvieren mit den Augen nur in unserer Holographic Shell-Benutzeroberfläche (der Benutzeroberfläche, die Sie sehen, wenn Sie Ihre HoloLens 2 starten) verwendet wird, zeigen verschiedene Apps, z. B. [der "HoloLens Playground",](https://www.microsoft.com/p/mr-playground/9nb31lh723s2)hervorragende Beispiele dafür, wie die Eingabe des Anvierens mit den Augen die Magic Ihrer holografischen Erfahrung verbessern kann.
Auf dieser Seite werden Entwurfsüberlegungen für die Integration von Blickeingaben für die Interaktion mit Ihren holografischen Anwendungen diskutiert.

Sie erfahren mehr über wichtige Vorteile und auch einzigartige Herausforderungen, die sich aus der Eingabe des Anvings mit den Augen ergeben. Auf der Grundlage dieser Empfehlungen stellen wir mehrere Entwurfsempfehlungen bereit, mit deren Hilfe Sie benutzeroberflächen erstellen können, die vom Anvieren mit den Augen unterstützt werden. 

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
     <td>Anvingen mit den Augen</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>

## <a name="head-and-eye-tracking-design-concepts-demo"></a>Demo der Entwurfskonzepte für Kopf- und Eyetracking

Wenn Sie die Entwurfskonzepte für Kopf- und Eyetracking in Aktion sehen möchten, sehen Sie sich unten unsere Videodemo **Entwerfen von Hologrammen: Kopf- und Eyetracking** an. Wenn Sie fertig sind, fahren Sie mit einem ausführlicheren Einblick in bestimmte Themen fort.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

*Dieses Video wurde aus der HoloLens 2-App „Entwerfen von Hologrammen“ aufgenommen. Laden Sie die vollständige Erfahrung [hier](https://aka.ms/dhapp) herunter, und genießen Sie sie.*

## <a name="eye-gaze-input-design-guidelines"></a>Entwurfsrichtlinien für die Eingabe des Anvings mit den Augen

Es kann schwierig sein, eine Interaktion zu erstellen, die die Vorteile der schnell bewegenden Blickadressierung nutzt. In diesem Abschnitt werden die wichtigsten Vorteile und Herausforderungen zusammengefasst, die beim Entwerfen Ihrer Anwendung zu berücksichtigen sind. 

### <a name="benefits-of-eye-gaze-input"></a>Vorteile der Eingabe mit dem Anving mit den Augen

- **Zeigen mit hoher Geschwindigkeit.** Die Augenbrille ist die am schnellsten reagierende Brille im menschlichen Körper. 

- **Wenig Aufwand.** Es sind kaum physische Bewegungen erforderlich. 

- **Selbstverständlichkeit.** Informationen zu den Augenbewegungen eines Benutzers, die von Benutzern häufig als "Gedankenlesen" beschrieben werden, geben dem System an, welches Ziel der Benutzer erreichen soll. 

- **Alternativer Eingabekanal.** Mit den Augen können Sie eine leistungsstarke unterstützungsbasierte Eingabe für Hand- und Spracheingaben bereitstellen, die auf der erfahrungsbasierten Erfahrung der Benutzer basierend auf ihrer Hand-Augen-Koordination aufbaut.

- **Visuelle Aufmerksamkeit.** Ein weiterer wichtiger Vorteil ist die Möglichkeit, daraus zu ziehen, worauf ein Benutzer achten muss. Dies kann in verschiedenen Anwendungsbereichen von der effektiveren Auswertung verschiedener Entwürfe bis hin zur Unterstützung intelligenterer Benutzeroberflächen und verbesserter sozialer Hinweise für die Remotekommunikation helfen.

Kurz gesagt bietet die Verwendung des Anvisierens mit den Augen als Eingabe ein schnelles und müheloses kontextbezogenes Eingabesignal. Dies ist in Kombination mit  anderen  Eingaben wie Spracheingaben und manuellen Eingaben zum Bestätigen der Absicht des Benutzers leistungsstark.


### <a name="challenges-of-eye-gaze-as-an-input"></a>Herausforderungen beim Anvingen mit den Augen als Eingabe

Obwohl das Anvieren mit den Augen verwendet werden kann, um zufriedenstellende Benutzererfahrungen zu schaffen, die Ihnen das Gefühl geben, ein Superhero zu sein, ist es auch wichtig zu wissen, wofür es nicht gut ist, dies entsprechend zu berücksichtigen. In der folgenden Liste werden einige *zu berücksichtigende* Herausforderungen und deren Bewältigung bei der Arbeit mit Der Blickeingabe erläutert: 

- **Ihr Anving mit den Augen ist "immer ein"** In dem Moment, in dem Sie die Augenlider öffnen, beginnen Ihre Augen mit der Korrektur der Dinge in der Umgebung. Wenn Sie auf jedes von Ihnen durchgeführte Aussehen reagieren und versehentlich Aktionen ausführen, da Sie etwas zu lange durchsucht haben, würde dies zu einer unbesättigenden Erfahrung führen.
Es wird empfohlen, das Anvieren mit  den Augen mit einem Sprachbefehl, einer Handgeste, einem Schaltflächenklick oder einem erweiterten Verweilen zu kombinieren, um die Auswahl eines Ziels auszulösen (weitere Informationen finden Sie unter Anvieren mit den Augen und [Ausführen).](gaze-and-commit-eyes.md)
Diese Lösung ermöglicht auch einen Modus, in dem sich der Benutzer frei umschauen kann, ohne durch unfreiwilliges Auslösen von etwas überfordert zu werden. Dieses Problem sollte auch beim Entwerfen von visuellem und audity-Feedback beim Blick auf ein Ziel berücksichtigt werden.
Versuchen Sie nicht, den Benutzer mit sofortigen Pop-Out-Effekten zu überlasten oder auf Sounds zu bewegen. Die Feinheiten sind entscheidend. Im Folgenden werden einige bewährte Methoden für dieses Thema erläutert, wenn es um [Entwurfsempfehlungen geht.](eye-gaze-interaction.md#design-recommendations)

- **Beobachtung im Vergleich** zu Imagine, dass Sie ein Foto genau an der Wand begradigen möchten. Sie schauen zuerst auf den Rahmen und dann auf die Umgebung, um festzustellen, ob es richtig ausgerichtet ist. Stellen Sie sich nun vor, wie Sie dies tun würden, wenn Sie ihr Anving mit den Augen als Eingabe verwenden möchten, um das Bild zu verschieben. Schwierig, nicht wahr? Dies beschreibt die doppelte Rolle des Anvingens mit den Augen, wenn es sowohl für die Eingabe als auch für die Steuerung erforderlich ist. 

- **Lassen Sie vor dem Klicken:** Für die schnelle Zielauswahl haben Untersuchungen ergeben, dass das Anvieren mit den Augen eines Benutzers vor dem manuellen Klicken (z. B. tippen in die Luft) weiter gehen kann. Achten Sie besonders auf die Synchronisierung des signals für schnelles Anvisieren mit langsameren Steuerungseingaben (z. B. Stimme, Hände, Controller).

- **Kleine Ziele:** Kennen Sie das Gefühl, wenn Sie versuchen, Text zu lesen, der einfach etwas zu klein ist, um ihn zu lesen? Dieses ermüdende Gefühl auf Ihren Augen kann dazu führen, dass Sie sich erschöpft und zerknausen, da Sie versuchen, Ihre Augen neu zu justieren, um sich besser zu konzentrieren.
Dies ist ein Gefühl, das Sie in Ihren Benutzern aufrufen können, wenn Sie sie dazu zwingen, Ziele auszuwählen, die in Ihrer Anwendung mithilfe der Zielgruppenadressierung zu klein sind.
Damit Sie für Ihre Benutzer eine angenehme und komfortable Erfahrung schaffen, sollte bei Zielen für Ihren Entwurf der Sehwinkel mindestens 2 Grad (vorzugsweise mehr) betragen.

- **Lappende Blickbewegungen** Unsere Augen führen schnelle Bewegungen von der Fixierung zur Fixierung durch. Wenn Sie Scanwege aufgezeichneter Blickbewegungen betrachten, können Sie die Flatterhaftigkeit erkennen. Ihre Augen bewegen sich schnell und  im Gegensatz zu Bewegungen mit dem Kopf oder Handbewegungen schnell und in *Sprungbewegungen.*  

- **Nachverfolgungszuverlässigkeit:** Die Genauigkeit der Blickverfolgung kann sich beim Wechseln des Lichts ein wenig herabsetzen, wenn sich Ihre Augen an die neuen Bedingungen anpassen.
Dies sollte sich nicht unbedingt auf ihren Anwendungsentwurf auswirken, da die Genauigkeit innerhalb der 2°-Einschränkung sein sollte, kann es jedoch erforderlich sein, dass der Benutzer erneut kalibriert. 


## <a name="design-recommendations"></a>Entwurfsempfehlungen
Im Folgenden finden Sie eine Liste mit spezifischen Entwurfsempfehlungen, die auf den beschriebenen Vorteilen und Herausforderungen für die Eingabe mit dem Auge basieren:

1. **Anvistik mit den Augen ist nicht identisch mit Anvistik mit dem Kopf:**
    - **Überlegen Sie, ob schnelle, aber unbende Augenbewegungen zu Ihrer Eingabeaufgabe passen:** Während unsere schnellen und lappenden Augenbewegungen sich gut in der schnellen Auswahl von Zielen in unserem Sichtfeld befinden, sind sie weniger anwendbar für Aufgaben, die reibungslose Eingabebewegungen erfordern (z. B. Zeichnen oder Umkreisen von Anmerkungen). In diesem Fall ist das Zeigen mit Hand oder Kopf zu bevorzugen.
  
    - **Vermeiden Sie es, etwas direkt an das Anvieren mit den Augen des Benutzers (z. B. einen Schieberegler oder Cursor) anfügen.**
Bei Cursorn kann dies aufgrund von geringfügigen Offsets im projizierten Anvisierensignal zu einem "flüchtigen Cursoreffekt" führen. Bei einem Schieberegler kann es zu Konflikten mit der doppelten Rolle führen, den Schieberegler mit Ihren Augen zu steuern, während gleichzeitig überprüft werden soll, ob sich das Objekt an der richtigen Position befindet. Für das Beispiel des Schiebereglers ist es sinnvoller, das Anvingen mit den Augen in Kombination mit Handgesten zu verwenden. Dies bedeutet, dass der Benutzer schnell und mühelos zwischen vielen Schiebereglern wechseln und die Hand hochziehen und den Daumen und den Zeigefinger anheften kann, um sie zu greifen und zu bewegen. Wenn der Schieberegler freigegeben wird, wird der Schieberegler nicht mehr bewegt. Benutzer könnten überfordert und abgelenkt werden, insbesondere, wenn das Signal für diesen Benutzer unpräzise ist. 
  
2. **Kombinieren Sie das Anvingen mit den Augen mit anderen Eingaben:** Die Integration von EyeTracking in andere Eingaben, z. B. Handgesten, Sprachbefehle oder Tastendruck, bietet mehrere Vorteile:
    - **Kostenlose Beobachtung zulassen:** Da die Hauptaufgabe unserer Augen die Beobachtung unserer Umgebung ist, ist es wichtig, dass Benutzer sich umschauen dürfen, ohne Feedback oder Aktionen auszulösen (visuell, a audity und so weiter). 
    Die Kombination von EyeTracking mit einem anderen Eingabesteuerfeld ermöglicht einen reibungslosen Übergang zwischen der Eyetracking-Beobachtung und den Eingabesteuerungsmodi.
  
    - **Leistungsstarker Kontextanbieter:** Die Verwendung von Informationen darüber, wo und was der Benutzer beim Sagen eines Sprachbefehls oder mithilfe einer Handgeste betrachtet, ermöglicht die nahtlose Kanalierung der Eingabe über das Sichtfeld. Beispiel: Sagen Sie _"put that there",_ um ein Hologramm schnell und fluent über der Szene auszuwählen und zu positionieren, indem Sie ein Ziel und das beabsichtigte Ziel sehen. 

    - **Bedarf für die Synchronisierung von synchronen Eingaben:** Das Kombinieren schneller Augenbewegungen mit komplexeren Eingaben, z. B. langen Sprachbefehlen oder Handgesten, birgt das Risiko, dass sich der Benutzer bereits umschaut, bevor der zusätzliche Eingabebefehl abgeschlossen und erkannt wird. Wenn Sie Ihre eigenen Eingabesteuerelemente erstellen (z. B. benutzerdefinierte Handgesten), stellen Sie sicher, dass Sie den Beginn dieser Eingabe oder die ungefähre Dauer protokollieren, um sie mit dem zu korrelieren, was ein Benutzer in der Vergangenheit betrachten musste.
    
3. **Subtiles Feedback für Eyetrackingeingaben:** Es ist hilfreich, Feedback zu geben, wenn ein Ziel angezeigt wird, um anzugeben, dass das System wie beabsichtigt funktioniert, aber fein gehalten werden sollte. Dies kann das langsame Ein- und Ausblenden, visuelle Highlights oder andere geringfügige Zielverhaltensverhalten umfassen, z. B. langsame Bewegungen, z. B. eine geringfügige Erhöhung der Zielgröße. Dies weist darauf hin, dass das System ordnungsgemäß erkannt hat, dass der Benutzer ein Ziel betrachtet, ohne den aktuellen Workflow des Benutzers unnötig zu unterbrechen. 

4. **Vermeiden Sie es, unnatürliche Augenbewegungen als Eingabe zu erzwingen:** Erzwingen Sie nicht, dass Benutzer bestimmte Augenbewegungen (Anvinggesten) verwenden, um Aktionen in Ihrer Anwendung auszulösen.

5. **Konto für Ungenauigkeiten:** Wir unterscheiden zwei Arten von Ungenauigkeiten, die für Benutzer wahrnehmbar sind: Offset und Jitter. Die einfachste Möglichkeit, einen Offset zu adressiert, besteht in der Bereitstellung ausreichend großer Ziele für die Interaktion. Es wird empfohlen, einen visuellen Winkel größer als 2° als Referenz zu verwenden. Ihre Miniaturansicht beträgt beispielsweise etwa 2° im visuellen Winkel, wenn Sie den Arm strecken. Dies führt zu folgender Richtlinie:
    - Erzwingen Sie nicht, dass Benutzer kleine Ziele auswählen. Untersuchungen haben ergeben, dass Benutzer ihre Interaktionen als mühelos und wissenschaftlich beschreiben, wenn Ziele ausreichend groß sind und das System gut entworfen ist. Wenn Ziele zu klein sind, empfinden Benutzer die Erfahrung als ermüdend und frustrierend.
  
<br>

Auf dieser Seite haben Sie einen guten Überblick erhalten, damit Sie mit dem Anvieren mit den Augen als Eingabe in Mixed Reality beginnen können. Um mit der Entwicklung zu beginnen, sehen Sie sich unsere Informationen zu Anvingen mit den Augen [in Unity](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main) und [Anvingen mit den Augen in DirectX an.](../develop/native/gaze-in-directx.md)


## <a name="see-also"></a>Siehe auch
* [Komfort](comfort.md)
* [Anvischen mit den Augen in DirectX](../develop/native/gaze-in-directx.md)
* [Anvieren mit den Augen in Unity (Mixed Reality Toolkit)](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main)
* [Blickverfolgung auf HoloLens 2](eye-tracking.md)
* [Anvisieren und Ausführen](gaze-and-commit.md)
* [Anvisieren und Verweilen](gaze-and-dwell.md)
* [Spracheingabe](../out-of-scope/voice-design.md)