---
title: Lunar-Modul
description: Erfahren Sie, wie Sie die Basisgesten von HoloLens mit zweihändigen Nachverfolgungs- und Xbox-Controllereingaben erweitern, reaktive Objekte erstellen und Menüsysteme implementieren.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Beispiel-Apps, Design, MRTK, Mixed Reality Toolkit, Unity, Beispiel-Apps, Beispiel-Apps, Open Source, Microsoft Store, HoloLens, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: ebac2c5680524b408d6dde8635d2585236fa0b08
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743508"
---
# <a name="lunar-module"></a>Lunar-Modul

>[!NOTE]
>In diesem Artikel wird ein exploratives Beispiel erläutert, das wir in den [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity)erstellt haben, einem Ort, an dem wir unsere Erkenntnisse und Vorschläge für die Entwicklung von Mixed Reality-Apps teilen. Unsere artikel- und codebezogenen Entwurfsartikel werden sich weiterentwickeln, wenn wir neue Ermittlungen vornehmen.

[Lunar Module](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule) ist eine Open-Source-Beispiel-App aus den Mixed Reality Design Labs von Microsoft. Erfahren Sie, wie Sie die Basisgesten von HoloLens mit zweihändigen Nachverfolgungs- und Xbox-Controllereingaben erweitern, Objekte erstellen, die auf Oberflächenzuordnung und Ebenensuche reaktiv sind, und einfache Menüsysteme implementieren. Alle Komponenten des Projekts stehen zur Verwendung in Ihren eigenen Mixed Reality-App-Erfahrungen zur Verfügung.

## <a name="demo-video"></a>Demovideo 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IcIP]

Aufgezeichnet mit HoloLens 2 mithilfe von Mixed Reality-Aufnahme

## <a name="rethinking-classic-experiences-for-windows-mixed-reality"></a>Neudenklassigen klassischer Funktionen für Windows Mixed Reality

Hoch oben in der Umgebung durchknöpft ein kleines Boot des Moduls "Apollo" das verzweigte Gelände darunter. Unsere unbefürchteten Pilotprojekte stellen einen geeigneten Zielbereich her. Der Abstieg ist mühsam, aber glücklicherweise wurde dieser Weg bereits mehrmals durchgeführt...

![Ursprüngliche Schnittstelle aus Ataris Lunar Lander von 1979](images/640px-atari-lunar-lander.png)<br>
*Ursprüngliche Schnittstelle aus Ataris Lunar Lander von 1979*

[Lunar Lander](https://en.wikipedia.org/wiki/Lunar_Lander_(1979_video_game)) ist ein klassischer Mondlander, bei dem Spieler versuchen, einen Mondlander auf eine flache Stelle des Mondlandeplatzes zu bringen. Jeder, der in den 1970er Jahren stammt, hat höchstwahrscheinlich Stunden in einem Bogen mit den Augen verbracht, die mit diesem Vektorversand vom Himmel geklebt wurden. Wenn ein Spieler sein Boot in Richtung eines Zielbereichs navigiert, wird das Gelände skaliert, um progressiv mehr Details zu zeigen. Erfolg bedeutet, dass innerhalb des sicheren Schwellenwerts horizontaler und vertikaler Geschwindigkeit gelandet wird. Punkte werden für die zeitaufgewendete Landezeit und den verbleibenden Kraftstoff mit einem Multiplikator basierend auf der Größe des Zielbereichs vergeben.

Abgesehen vom Spielbetrieb führte die Zeit der Spiele zu konstanten Innovationen von Steuerungsschemas. Von den einfachsten Vier-Wege-Brillen- und Schaltflächenkonfigurationen (in der Brille [Pac-Man)](https://en.wikipedia.org/wiki/Pac-Man)bis hin zu den sehr spezifischen und komplizierten Schemas, die in den späten 90er und 00er-Jahren (z. B. in Simulatoren und Schienenschienen) zu sehen waren. Das eingabeschema, das auf dem Lunar Lander-Computer verwendet wird, ist aus zwei Gründen nicht erfolgreich: Aus gründen der Rekursion und der Immersion.

![Lunar Lander-Konsole von Atari](images/atariconsole.png)<br>
*Lunar Lander-Konsole von Atari*

Warum entschieden sich Atari und so viele andere Spieleunternehmen, die Eingabe zu überdenken?

Ein Kind, das durch einen Gang geht, wird natürlich von der neuesten, blitzschnellsten Maschine durchsucht. Lunar Lander verfügt jedoch über ein neues Eingabegerät, das sich von der Menge abmeldet.

Lunar Lander verwendet zwei Schaltflächen zum Drehen des Versands nach links und rechts und einen **Drehungshöpf,** um die Menge der Vom landenden Maschinen zu steuern. Dieser Hebel bietet Benutzern ein bestimmtes Maß an Finesse, das ein regulärer Schleusung nicht bieten kann. Es ist auch eine Komponente, die modernen Cockpits gemeinsam ist. Atari wollte, dass Lunar Lander dem Benutzer das Gefühl vermittelt, tatsächlich ein Mondlandefähremodul zu steuern. Dieses Konzept wird als **taktile Immersion** bezeichnet.

Taktile Immersion ist die Erfahrung sensorischen Feedbacks durch sich wiederholende Aktionen. In diesem Fall hilft die sich wiederholende Aktion der Anpassung des Drosselungshänders und der Drehung, die unsere Augen sehen und unsere Hörer hören, den Spieler mit dem Anlanden eines Versands auf der Mondoberfläche zu verbinden. Dieses Konzept kann an das Konzept "Flow" gebunden werden. Wenn ein Benutzer vollständig in eine Aufgabe aufgenommen wird, die über die richtige Mischung aus Herausforderung und Belohnung verfügt, oder einfacher ausgedrückt, befindet er sich "in der Zone".

Wohl ist die wichtigste Art von Immersion in Mixed Reality räumliche Immersion. Der ganze Punkt von Mixed Reality besteht darin, sich selbst in die Aufnahme dieser digitalen Objekte zu verarscht, die in der realen Welt vorhanden sind. Wir synthetisieren Hologramme in unserer Umgebung, die in ganzen Umgebungen und Umgebungen räumlich zusammengestellt sind. Dies bedeutet nicht, dass wir in unseren Erfahrungen nicht immer noch andere Arten von Immersion einsetzen können, so wie es Atari mit taktiler Immersion in Lunar Lander getan hat.

## <a name="designing-with-immersion"></a>Entwerfen mit Immersion

Wie können wir die taktile Immersion auf eine aktualisierte volumetrische Sequel auf den klassischen Atari-Artikel anwenden? Vor dem Umgang mit dem Eingabeschema muss das Spielkonstrukt für den dreidimensionalen Raum behandelt werden.

![Visualisieren der Oberflächenzuordnung in HoloLens](images/surfacemapping.png)<br>
*Visualisieren der räumlichen Zuordnung in HoloLens*

Durch die Nutzung der Umgebung eines Benutzers stehen uns unendliche Geländeoptionen für die Ziellandung unseres Mondlandemoduls zur Verfügung. Damit das Spiel dem ursprünglichen Titel am ähnlichsten ist, könnte ein Benutzer potenziell Zielpads mit unterschiedlichen Schwierigkeiten in seiner Umgebung bearbeiten und platzieren.

![Das Mondlandefähremodul](images/640px-lm-hero.jpg)<br>
*Das Mondlandefähremodul*

Der Benutzer muss das Eingabeschema erlernen, das Landeziel steuern und ein kleines Ziel haben. Eine erfolgreiche Spielerfahrung bietet die richtige Mischung aus Herausforderung und Belohnung. Der Benutzer kann ein Bestimmtes Maß an Schwierigkeiten auswählen, wobei der einfachste Modus einfach erfordert, dass der Benutzer erfolgreich in einen benutzerdefinierten Bereich auf einer Oberfläche gelangen muss, die von der HoloLens gescannt wird. Sobald ein Benutzer das Spiel hängt, kann er die Schwierigkeiten nach Bedarf hochholen.

### <a name="adding-input-for-hand-gestures"></a>Hinzufügen von Eingaben für Handgesten

Die HoloLens-Basiseingabe verfügt nur über zwei Gesten: [Air Tap und Bloom](../../design/gaze-and-commit.md#composite-gestures). Benutzer müssen sich keine kontextbezogenen Nuancen oder eine Liste bestimmter Gesten merken, die die Benutzeroberfläche der Plattform vielseitig und leicht zu erlernen machen. Während das System diese beiden Gesten möglicherweise nur verfügbar macht, kann HoloLens als Gerät zwei Hände gleichzeitig nachverfolgen. Unser Ode an Lunar Lander ist eine [immersive App, d.h., wir können den Basissatz von Gesten erweitern, um zwei Hände zu nutzen und unsere eigenen, übermäßig taktilen Mittel für die Navigation von Mondlandemodulen hinzuzufügen.

Wenn wir auf das ursprüngliche Steuerelementschema zurückblicken, **mussten wir für Diess und Drehung lösen.** Der Nachteil ist, dass die Drehung im neuen Kontext eine zusätzliche Achse hinzufügt (technisch gesehen zwei, aber die Y-Achse ist weniger wichtig für das Ziel). Die beiden unterschiedlichen Versandbewegungen eignen sich natürlich, um jeder Hand zugeordnet zu werden:

![Tippen und ziehen Sie die Geste, um das Lander auf allen drei Achsen zu drehen.](images/module-handdrag.gif)<br>
*Tippen und ziehen Sie die Geste, um das Lander auf allen drei Achsen zu drehen.*

**Schub**

Der Hebel auf dem ursprünglichen Maschinenautomaten, der einer Skala von Werten zugeordnet ist, je höher der Hebel verschoben wurde, desto mehr Strahl wurde auf das Boot angewendet. Eine wichtige Feinheiten, die hier zu beachten sind, ist, wie der Benutzer seine Kontrolle übernehmen und einen gewünschten Wert beibehalten kann. Wir können das Verhalten beim Tippen und Ziehen effektiv verwenden, um das gleiche Ergebnis zu erzielen. Der Wert beginnt bei 0 (null). Der Benutzer tippt und zieht, um den Wert zu erhöhen. An diesem Punkt könnten sie loslassen, um sie zu verwalten. Jede Änderung des Werts der Tipp- und Ziehgeste wäre das Delta zum ursprünglichen Wert.

**Drehung**

Dies ist etwas komplizierter. Wenn holografische Schaltflächen zum Tippen "gedreht" werden, ist dies ein unerhörliches Erlebnis. Es gibt keine physische Kontrolle, die genutzt werden muss, sodass das Verhalten aus der Bearbeitung eines Objekts stammen muss, das den Lander darstellt, oder mit dem Lander selbst. Wir haben eine Methode mit Tippen und Ziehen entwickelt, die es einem Benutzer ermöglicht, sie effektiv in die gewünschte Richtung zu "pushen und zu pullen". Jedes Mal, wenn ein Benutzer tippt und hält, wird der Punkt im Raum, an dem die Geste initiiert wurde, zum Ursprung für die Drehung. Beim Ziehen vom Ursprung wird das Delta der Handübersetzung (X,Y,Z) konvertiert und auf das Delta der Drehungswerte des Landers angewendet. Oder einfach *ausgedrückt: Wenn Sie nach links <-> nach rechts, nach oben <-> nach unten ziehen, <-> zurück in Leerzeichen ziehen, wird das Versand entsprechend gedreht.*

Da die HoloLens zwei Hände nachverfolgen kann, kann die Drehung der rechten Hand zugewiesen werden, während die Luftbewegung von links gesteuert wird. Finesse ist der entscheidende Faktor für den Erfolg in diesem Spiel. Das *Gefühl* dieser Interaktionen ist die absolute höchste Priorität. Insbesondere im Kontext der taktilen Immersion. Ein Zu schnelles Versenden wäre schwierig zu steuern, während ein zu langsames das "Pushen und Pullen" des Benutzers auf dem Versand für einen umständlich langen Zeitraum erfordern würde.

### <a name="adding-input-for-game-controllers"></a>Hinzufügen von Eingaben für Gamecontroller

Handgesten auf der HoloLens stellen zwar eine neue Methode der differenzierten Steuerung bereit, aber es gibt immer noch ein gewisses Fehlen von "echtem" taktilem Feedback, das Sie von analogen Steuerelementen erhalten. Durch das Verbinden eines Xbox-Spielcontrollers können wir dieses Gefühl der Physischen wiedererlangen und gleichzeitig die Steuerungsstäbchen nutzen, um eine differenzierte Steuerung zu erhalten.

Es gibt mehrere Möglichkeiten, das relativ einfache Steuerungsschema auf den Xbox-Controller anzuwenden. Da wir versuchen, so nah wie möglich an der ursprünglichen Einrichtung zu bleiben, wird **Dies** am besten der Triggerschaltfläche zugeordnet. Bei diesen Schaltflächen handelt es sich um analoge Steuerelemente, d. h., sie verfügen über mehr als einfache *Ein- und Aus-Zustände* und reagieren tatsächlich auf den Druckgrad, der auf sie zunimmt. Dies gibt uns ein ähnliches Konstrukt wie das **Ehrmittelmittel**. Im Gegensatz zum ursprünglichen Spiel und der Handgeste schneidet dieses Steuerelement die Brille des Versands ab, sobald ein Benutzer den Trigger nicht mehr unter Druck setzt. Es gibt dem Benutzer immer noch das gleiche Maß an Finesse wie das ursprüngliche Spiel.

![Der linke Thumbstick ist Yaw und Roll zugeordnet, der rechte Ziehstäbchen wird Tonhöhe und Roll zugeordnet.](images/thumbsticksidebyside.gif)<br>
*Der linke Thumbstick wird yaw und roll zugeordnet. Der rechte Thumbstick wird Tonhöhe und Roll zugeordnet.*

Die dualen Sticks eignen sich natürlich für die Steuerung der Drehung des Versands. Leider gibt es drei Achsen, auf denen sich das Boot drehen kann, und zwei Thumbsticks, die beide zwei Achsen unterstützen. Dieser Konflikt bedeutet, dass entweder ein Thumbstick eine Achse steuert. oder es gibt eine Überlappung der Achsen für die Sticks. Die frühere Lösung hat sich "gebrochen" gefühlt, da Daumenstäbchen ihre lokalen X- und Y-Werte inhärent kombinieren. Die zweite Lösung erforderte einige Tests, um zu ermitteln, welche redundanten Achsen sich am natürlichsten anfühlen. Im letzten Beispiel werden *yaw* und *roll* (Y- und X-Achsen) für den linken Thumbstick und *pitch* and *roll* (Z- und X-Achsen) für den rechten Thumbstick verwendet. Dies hat das natürlichste gefühlt, da *Roll* scheinbar unabhängig voneinander gut mit *Gier* und *Tonhöhe* gekoppelt ist. Beachten Sie, dass die Verwendung beider Thumbsticks für *roll* ebenfalls den Drehwert verdoppelt. Es macht ziemlich viel Spaß, die Lander-Do-Schleifen zu haben.

Diese Beispiel-App veranschaulicht, wie räumliche Erkennung und taktiler Immersion eine Benutzeroberfläche dank der erweiterbaren Eingabemuster Windows Mixed Reality erheblich verändern können. Während Lunar Lander fast 40 Jahre alt sein kann, werden die konzepte, die mit diesem kleinen Oktaggon-mit-Anstieg verfügbar gemacht werden, dauerhaft weiterleben. Warum sollten Sie sich bei der Vorstellung von der Zukunft nicht die Vergangenheit ansehen?

## <a name="technical-details"></a>Technische Details

Skripts und Prefabs für die Lunar Module-Beispiel-App finden Sie auf [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule).

## <a name="about-the-author"></a>Informationen zum Autor

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Addison Linville" width="60" height="60" src="images/addisonlinville-tile-60px.jpg"></td>
<td style="border-style: none"><b>Addison Linville</b><br>UX-Designer @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Siehe auch

* [Hub für MRTK-Beispiele](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(Aus dem Microsoft Store in HoloLens 2 herunterladen)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)
* [Oberflächen](sampleapp-surfaces.md) - [(Aus dem Microsoft Store in HoloLens 2 herunterladen)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)
* [Periodensystem der Elemente 2.0](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [Galaxy Explorer 2.0](galaxy-explorer-update.md)