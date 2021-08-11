---
title: 'Fallstudie: Mein erstes Jahr im HoloLens Designteam'
description: Meine Reise von einer 2D-Flatland-Welt in die 3D-Welt begann, als ich im Januar 2016 dem HoloLens Designteam beigetreten bin.
author: designnomad
ms.author: v-hferrone
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, Design, Herausgeber, Privat
ms.openlocfilehash: 2defa24b8e53b28f90a8eb613afcbae7d1b9b1f2d12caaf885e405593df01ffe
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192874"
---
# <a name="case-study---my-first-year-on-the-hololens-design-team"></a>Fallstudie: Mein erstes Jahr im HoloLens Designteam

Meine Reise von einer 2D-Flatland-Welt in die 3D-Welt begann, als ich im Januar 2016 dem HoloLens Designteam beigetreten bin. Vor dem Beitritt zum Team hatte ich nur sehr wenig Erfahrung im 3D-Design. Es war wie das chinesische Spricht über eine Reise von tausend Kilometern, die mit einem einzelnen Schritt beginnt, außer in meinem Fall war der erste Schritt ein Schritt!

![Leap von 2D auf 3D](../develop/platform-capabilities-and-apis/images/2D_to_3D-800px.gif)<br>
*Den Sprung von 2D zu 3D*

> *"Ich hatte das Gefühl, als wäre ich auf den Fahrerplatz gesprungen, ohne zu wissen, wie ich das Auto fahren soll. Ich war überfordert und verängstigt, aber sehr fokussiert."*<br>
> – Hae Jin Lee

Im letzten Jahr habe ich so schnell wie möglich Fähigkeiten und Kenntnisse erworben, aber ich habe immer noch viel zu lernen. Hier habe ich vier Beobachtungen mit einem Videotutorial geschrieben, das meinen Übergang von einem 2D- zum 3D-Interaktionsdesigner dokumentiert. Ich hoffen, dass meine Erfahrung andere Designer dazu inspiriert, den Sprung zu 3D zu unternehmen.

## <a name="good-bye-frame-hello-spatial--diegetic-ui"></a>Good-Bye-Frame. Hello spatial/diegetic UI

Jedes Mal, wenn ich Poster, Magazinen, Websites oder App-Bildschirme entworfen habe, war ein definierter Rahmen (in der Regel ein Rechteck) eine Konstante für jedes Problem. Sofern Sie diesen Beitrag nicht in einem HoloLens oder einem  anderen VR-Gerät lesen, sehen Sie sich dies von außen über den 2D-Bildschirm sicher innerhalb eines Frames an. Inhalte sind für Sie extern. Allerdings entfernt Mixed Reality Headset den Rahmen, sodass Sie sich innerhalb des *Inhaltraums* befinden und den Inhalt von innen nach außen suchen und durchgehen.

Ich habe dies konzeptionell verstanden, aber am Anfang habe ich den Fehler gemacht, einfach 2D-Denken in den 3D-Raum zu übertragen. Dies funktionierte natürlich nicht gut, da der 3D-Raum über eigene eindeutige Eigenschaften verfügt, z. B. eine Ansichtsänderung (basierend auf der Kopfbewegung des Benutzers) und unterschiedliche Anforderungen an benutzerfreundliche Benutzerfreundlichkeit [(basierend](https://www.youtube.com/watch?v=-606oZKLa_s/) auf den Eigenschaften der Geräte und der Personen, die sie verwenden). In einem 2D-Benutzeroberflächenentwurfsraum ist das Sperren von Benutzeroberflächenelementen in der Ecke eines Bildschirms ein sehr gängiges Muster, aber diese Benutzeroberfläche im HUD-Stil (Head Up Display) ist in MR/VR-Benutzeroberflächen nicht natürlich. Sie verhindert das Ein immerion in den Raum des Benutzers und verursacht Benutzerbeschwerden. Es ist so, als ob Sie einen unermesslichen Partikel an Ihrer Brille haben, den Sie entfernen müssen. Im Laufe der Zeit habe ich gelernt, dass es natürlicher ist, Inhalte im 3D-Raum zu positionieren und textgesperrte Verhaltensweisen hinzuzufügen, die dazu führen, dass der Inhalt dem Benutzer in einem relativen festen Abstand folgt.

![Text gesperrt](../develop/platform-capabilities-and-apis/images/bodylockedtagalong.gif)<br>
*Text gesperrt*

<br>

![Weltgesperrt](../develop/platform-capabilities-and-apis/images/worldlocked.gif)<br>
*Weltgesperrt*

### <a name="fragments-an-example-of-great-diegetic-ui"></a>Fragmente: Ein Beispiel für eine großartige diegetische Benutzeroberfläche

[Fragmente](https://www.microsoft.com/p/fragments/9nblggh5ggm8), ein von [Asobo Studio](https://www.asobostudio.com/) für HoloLens entwickelter First-Person-Verbrechensverbrechen, veranschaulicht eine großartige diegetische Benutzeroberfläche. In diesem Spiel wird der Benutzer zu einer Hauptfigur, einem Detective, der versucht, einen Löser zu lösen. Die zentralen Hinweise zur Lösung dieses Problems werden im physischen Raum des Benutzers übers leben und oft in ein fiktives Objekt eingebettet, anstatt allein vorhanden zu sein. Diese diegetische Benutzeroberfläche ist in der Regel weniger aufzeigbar als die körpergesperrte Benutzeroberfläche, daher hat das Asobo-Team viele Hinweise wie anvisierte Richtung virtueller Zeichen, Sound, Licht und Leitfäden (z. B. Pfeil, der auf die Position des Hinweises zeigt) verwendet, um die Aufmerksamkeit des Benutzers zu gewinnen.

![Fragmente – Beispiele für diegetische Benutzeroberfläche](../develop/platform-capabilities-and-apis/images/fragments-game-example-1.jpg)<br>
*Fragmente – Beispiele für diegetische Benutzeroberfläche*

### <a name="observations-about-diegetic-ui"></a>Beobachtungen zur diegetischen Benutzeroberfläche

Die räumliche Benutzeroberfläche (sowohl körper- als auch weltgesperrt) und die diegetische Benutzeroberfläche haben ihre eigenen Stärken und Schwächen. Ich ermutige Designer, so viele MR/VR-Apps wie möglich auszuprobieren und ihr eigenes Verständnis und ihre eigene Lesbarkeit für verschiedene Positionierungsmethoden der Benutzeroberfläche zu entwickeln.

## <a name="the-return-of-skeuomorphism-and-magical-interaction"></a>Die Rückgabe von Skeuomorphie und interaktionsmäßiger Interaktion

Skeuomorphie, eine digitale Schnittstelle, die die Form realer Objekte imitiert, ist in der Designbranche in den letzten 5 bis 7 Jahren "unerschömend". Als Apple schließlich dem flachen Design in iOS 7 den Weg geliehen hat, scheint skeuomorphism schließlich als Schnittstellenentwurfsmethodik unblos zu sein. Aber dann ist ein neues Medium, ein MR/VR-Headset, auf dem Markt eingetroffen, und es scheint, als würde die Skeuomorphie wieder zurückgegeben werden. : )

### <a name="job-simulator-an-example-of-skeuomorphic-vr-design"></a>Auftragssimulator: Ein Beispiel für ein skeuomorphes VR-Design

[Der Auftragssimulator](https://jobsimulatorgame.com/)ist eines der beliebtesten Beispiele für skeuomorphes VR-Design, ein von [Sollchemy Labs](https://owlchemylabs.com/) entwickeltes Whimsical-Spiel. Innerhalb dieses Spiels werden Spieler in die Zukunft transportiert, in der Roboter Menschen ersetzen und Menschen einen Eindungswagen besuchen, um zu erleben, wie es sich anfühlt, alltägliche Aufgaben in einem von vier verschiedenen Aufträgen auszuführen: Auto-Schreiber, Chef Chef, Store Clerk oder Office Worker.

Der Vorteil der Skeuomorphie ist eindeutig. Vertraute Umgebungen und Objekte in diesem Spiel helfen neuen VR-Benutzern, sich im virtuellen Raum wohler und präsentieren zu können. Sie haben auch das Gefühl, dass sie die Kontrolle haben, indem sie vertrautes Wissen und Verhalten Objekten und ihren entsprechenden physischen Reaktionen zuordnen. Um z. B. einen Kaffee zu essen, müssen die Menschen einfach zur Kaffeemaschine gehen, eine Taste drücken, den Becherhandles greifen und ihn wie in der realen Welt an ihren Kopf kippen.

![Auftragssimulator](../develop/platform-capabilities-and-apis/images/job-simulator.gif)<br>
*Auftragssimulator*

Da MR/VR noch immer ein Entwicklungsmedium ist, ist die Verwendung eines bestimmten Skeuomorphiegrads erforderlich, um die MR/VR-Technologie zu demystisieren und für größere Zielgruppen auf der ganzen Welt einzuführen. Darüber hinaus kann die Verwendung von Skeuomorphie oder realistischer Darstellung für bestimmte Arten von Anwendungen wie Dieb- oder Flugsimulation von Vorteil sein. Da das Ziel dieser Apps das Entwickeln und Verfeinern bestimmter Fähigkeiten ist, die direkt in der realen Welt angewendet werden können, gilt: Je näher die Simulation an der realen Welt liegt, desto besser ist das Wissen übertragbar.

Denken Sie daran, dass Skeuomorphie nur ein Ansatz ist. Das Potenzial der MR/VR-Welt ist viel größer als das, und Designer sollten versuchen, einzigartige hyper-natürliche Interaktionen zu erstellen – neue Bezahlbarkeiten, die in der MR/VR-Welt einzigartig möglich sind. Als Erstens sollten Sie erwägen, gewöhnliche Objekte mit Rauschen zu befüllen, damit Benutzer ihre grundlegenden Anforderungen erfüllen können – einschließlich Teleportation und Omniscience.

![Doraemon-Tür (links) und Ruby-Schieber (rechts)](../develop/platform-capabilities-and-apis/images/doraemons-magical-door-and-ruby-slippers.jpg)<br>
*Doraemon-Tür (links) und Ruby-Schieber (rechts)*

### <a name="observations-about-skeuomorphism-in-vr"></a>Beobachtungen zur Skeuomorphie in VR

Von "Anywhere door" in Doraemon, "Ruby-Schützern" im Assistenten von Oz bis zu "Allerader-Karte" in Dabei gibt es Beispiele für gewöhnliche Objekte mit großer Beliebtheit in beliebten Fiktiven. Diese magischen Objekte helfen uns dabei, eine Verbindung zwischen der realen Welt und der Heiterheit, zwischen dem, was ist, und dem, was sein könnte, zu visualisieren. Denken Sie daran, dass beim Entwerfen des Bzw. des Objekts ein Gleichgewicht zwischen Funktionalität und Unterhaltung erfüllt werden muss. Seien Sie vorsichtig, wenn Sie etwas reines Magisches erstellen, nur um ihrer Selbstzweck willen.

## <a name="understanding-different-input-methods"></a>Grundlegendes zu verschiedenen Eingabemethoden

Als ich für das 2D-Medium entworfen habe, musste ich mich auf Toucheingaben, Maus- und Tastaturinteraktionen für Eingaben konzentrieren. Im MR/VR-Designbereich wird unser Text zur Schnittstelle, und Benutzer können eine größere Auswahl von Eingabemethoden verwenden: Sprache, Anvisierten, Gesten, [6-Dof-Controller](https://en.wikipedia.org/wiki/Six_degrees_of_freedom)und Handflächen, die intuitivere und direkte Verbindungen mit virtuellen Objekten bieten.

![Verfügbare Eingaben in HoloLens](../develop/platform-capabilities-and-apis/images/inputs.jpg)<br>
*Verfügbare Eingaben in HoloLens*

> *"Alles ist am besten für etwas und am schlechtesten für etwas anderes."*<br>
> – [Bill Buxton](https://www.billbuxton.com/)

Gesteneingaben mit Bare-Hand- und Kamerasensoren auf einem HMD-Gerät ermöglichen es Benutzern beispielsweise, Hand vom Halten von Controllern oder Vonstößen zu halten, aber häufige Verwendung kann zu physischer Belastung führen (auch als Gorilla-Arm bezeichnet). Außerdem müssen Benutzer ihre Hände innerhalb der Sichtlinie halten. Wenn die Kamera die Hände nicht sehen kann, können die Hände nicht verwendet werden.

Die Spracheingabe ist gut für das Durchlaufen komplexer Aufgaben, da sie es Benutzern ermöglicht, geschachtelte Menüs mit einem Befehl zu durchschneiden (z. B. "Show me the movies made by Laika studio.") und auch sehr wirtschaftlich, wenn sie mit anderen Modalitäten gekoppelt sind (z.B. richtet der Befehl "Zu mir drehen" das Hologramm aus, das ein Benutzer an den Benutzer richtet. Die Spracheingabe funktioniert jedoch möglicherweise nicht gut in einer lauten Umgebung oder in einem sehr stillen Raum nicht geeignet.

Neben Gesten und Sprache sind handgestend nachverfolgte Controller (z. B. Oculus Touch, Vive usw.) sehr beliebte Eingabemethoden, da sie einfach zu verwenden, präzise sind, die [Propführung](https://en.wikipedia.org/wiki/Proprioception)von Personen nutzen und passive, passive hinweise liefern. Diese Vorteile gehen jedoch mit dem Preis ein, dass sie nicht in der Lage sind, mit leeren Händen zu sein und die vollständige Fingerverfolgung zu verwenden.

![Senso (links) und Manus VR(rechts)](../develop/platform-capabilities-and-apis/images/senso-and-manus-vr.jpg)<br>
*Senso (links) und Manus VR (rechts)*

Obwohl sie nicht so beliebt wie Controller sind, gewinnen Handschutzgeräte dank der MR/VR-Welle wieder an Beliebtheit. In den letzten Jahren hat die Brain/Mind-Eingabe begonnen, sich als Schnittstelle für virtuelle Umgebungen zu entwickeln, indem sie DEN- oder EMG-Sensor in headset (z.B. [MindMaze VR) integriert.](https://www.mindmaze.com/)

### <a name="observations-about-input-methods"></a>Beobachtungen zu Eingabemethoden

Dies ist nur ein Beispiel für Eingabegeräte, die auf dem Markt für MR/VR verfügbar sind. Sie werden weiter wachsen, bis die Branche reift und sich auf bewährte Methoden einigt. Bis dahin sollten Designer neue Eingabegeräte kennen und in den spezifischen Eingabemethoden für ihr bestimmtes Projekt gut zu finden sein. Designer müssen innerhalb von Einschränkungen nach kreativen Lösungen suchen und gleichzeitig die Stärken eines Geräts ausspielen.

## <a name="sketch-the-scene-and-test-in-the-headset"></a>Skizzieren der Szene und Testen im Headset

Als ich in 2D gearbeitet habe, habe ich hauptsächlich nur den Inhalt gezeichnet. Im Mixed Reality-Raum reichte dies jedoch nicht aus. Ich musste die gesamte Szene skizzieren, um die Beziehungen zwischen dem Benutzer und virtuellen Objekten besser vorstellen zu können. Um mein räumliches Denken zu unterstützen, habe ich damit begonnen, Szenen in [Sollen 4D](https://www.maxon.net/en/products/cinema-4d/overview/) zu skizzieren und manchmal einfache Objekte für die Prototyperstellung in [Maya zu erstellen.](https://www.autodesk.com/products/maya/overview/) Ich hatte vor dem Beitritt zum HoloLens-Team noch nie ein Programm verwendet, und ich bin immer noch ein Neuling, aber durch die Arbeit mit diesen 3D-Programmen konnte ich mich definitiv mit neuer Terminologie wie [Shader](https://en.wikipedia.org/wiki/Shader) und [IK (inverse Kinematics)](https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2016/ENU/Maya/files/GUID-07C3BA47-32BB-477B-B6C5-1090E5C9B81C-htm.html/)auskennen.

**"Unabhängig davon, wie eng ich die Szene in 3D umrissen habe, war die tatsächliche Erfahrung im Headset fast nie das gleiche wie der Sketch. Deshalb ist es wichtig, die Szene in den Ziel-Headsets zu testen." – Hae Jin Lee**

Für HoloLens Prototyperstellung habe ich alle Tutorials unter Mixed Reality [Tutorials](../develop/unity/tutorials.md) zum Einstieg ausprobiert. Anschließend begann ich mit [HoloToolkit.Unity](https://github.com/Microsoft/HoloToolkit-Unity/) zu spielen, die Microsoft Entwicklern zur Verfügung stellt, um die Entwicklung holografischer Anwendungen zu beschleunigen. Als ich bei etwas hängen geblieben bin, habe ich meine Frage im HoloLens [Question & Answer Forum veröffentlicht.](https://forums.hololens.com/categories/questions-and-answers/)

Nachdem ich ein grundlegendes Verständnis HoloLens Prototyps erhalten hatte, wollte ich anderen Nicht-Codern die Möglichkeit geben, selbst Prototypen zu erstellen. Daher habe ich ein Videotutorial gemacht, in dem gezeigt wird, wie sie ein einfaches Projektil mithilfe von HoloLens. Ich erkläre kurz die grundlegenden Konzepte. Auch wenn Sie keine Erfahrung mit HoloLens haben, sollten Sie dies verfolgen können.

<br>

>[!VIDEO https://www.youtube.com/embed/58612RT2CT8]
*Ich habe dieses einfache Tutorial für Nicht-Programmierer wie mich selbst gemacht.*

Für die VR-Prototyperstellung habe ich Kurse an der [VR Dev School](https://learn.vrdev.school/) und bei der Erstellung von [3D-Inhalten](https://www.lynda.com/Unreal-Engine-tutorials/3D-Content-Creation-Virtual-Reality/482055-2.html?srchtrk=index%3a1%0alinktypeid%3a2%0aq%3aVirtual+Reality+%0apage%3a1%0as%3arelevance%0asa%3atrue%0aproducttypeid%3a2/) für Virtual Reality Lynda.com. Die VR Dev School hat mir detailliertere Kenntnisse im Programmieren bereitgestellt, und der Lynda-Kurs bot mir eine gute kurze Einführung in das Erstellen von Ressourcen für VR.

## <a name="take-the-leap"></a>Take the leap

Vor einem Jahr war ich der Ansicht, dass all dies etwas überfordert war. Nun kann ich Ihnen mitteilen, dass sich der Aufwand zu 100 % ge lohnt hat. MR/VR ist noch sehr alt, und es gibt so viele interessante Möglichkeiten, bis sie realisiert werden können. Ich bin inspiriert und glücklicherweise in der Lage, eine kleine Rolle bei der Gestaltung der Zukunft spielen zu können. Ich hoffen, dass Sie mich auf dem Weg in den 3D-Raum begleiten werden!

## <a name="about-the-author"></a>Informationen zum Autor

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Hae Jin Lee" width="60" height="60" src="../develop/platform-capabilities-and-apis/images/haejinlee.jpg"></td>
<td style="border-style: none"><b>Hae Jin Lee</b><br>UX-Designer @Microsoft</td>
</tr>
</table>

 
