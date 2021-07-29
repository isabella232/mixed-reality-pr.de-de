---
title: Lunar-Modul
description: Erfahren Sie, wie HoloLens gesten mit zweihändiger Nachverfolgung und Xbox-Controllereingabe erweitern, reaktive Objekte erstellen und Menüsysteme implementieren.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Beispiel-Apps, Design, MRTK, Mixed Reality Toolkit, Unity, Beispiel-Apps, Beispiel-Apps, Open Source, Microsoft Store, HoloLens, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 4a736990a94d7f5c97a1bfc2edf998e327071bcb
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757222"
---
# <a name="lunar-module"></a>Lunar-Modul

>[!NOTE]
>In diesem Artikel wird ein exploratives Beispiel erläutert, das wir in den [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity)erstellt haben, einem Ort, an dem wir unsere Erfahrungen und Vorschläge für die Entwicklung von Mixed Reality-Apps teilen. Unsere designbezogenen Artikel und der Code werden weiterentwickelt, wenn wir neue Erkenntnisse machen.

[Lunar Module ist](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule) eine Open-Source-Beispiel-App aus Mixed Reality Design Labs von Microsoft. Erfahren Sie, wie HoloLens Gesten mit zweihändiger Nachverfolgung und Xbox-Controllereingabe erweitern, Objekte erstellen, die reaktiv für die Oberflächenzuordnung und Ebenensuche sind, und einfache Menüsysteme implementieren. Alle Komponenten des Projekts stehen für die Verwendung in Ihren eigenen Mixed Reality-App-Erfahrungen zur Verfügung.

## <a name="demo-video"></a>Demovideo 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IcIP]

Aufgezeichnet mit HoloLens 2 mit Mixed Reality-Aufnahme

## <a name="rethinking-classic-experiences-for-windows-mixed-reality"></a>Überdacht klassische Erfahrungen für Windows Mixed Reality

Hoch oben in der Umgebung stellt ein kleiner Ship-1-Mitarbeiter des Moduls "Stil" unten methodisch verknustetes Gelände auf. Unser unfreier Pilot macht einen geeigneten Zielbereich aus. Der Abstieg ist mühsam, aber glücklicherweise wurde dieser Weg schon mehrmals gemacht...

![Ursprüngliche Schnittstelle von Ataris Mondlander von 1979](images/640px-atari-lunar-lander.png)<br>
*Ursprüngliche Schnittstelle von Ataris Mondlander von 1979*

[Lunar Lander ist](https://en.wikipedia.org/wiki/Lunar_Lander_(1979_video_game)) ein klassisches Mondland, bei dem Spieler versuchen, ein Mondlander an einem flachen Ort des Mondlandes zu pilotieren. Jeder, der in den 1970er Jahren geerbt wurde, hat höchstwahrscheinlich Stunden in einem 30-Stunden-Paar mit den Augen verbracht, die an das vom Himmel her aufgestürzte Vektor-Ship verknaust sind. Wenn ein Spieler sein Boot zu einem Zielbereich navigiert, wird das Gelände skaliert, um zunehmend mehr Details zu zeigen. Erfolg bedeutet, innerhalb des sicheren Schwellenwerts der horizontalen und vertikalen Geschwindigkeit zu landen. Punkte werden für die zeitbezogene Landezeit und den verbleibenden Kraftstoff mit einem Multiplikator basierend auf der Größe des Zielbereichs vergeben.

Abgesehen vom Spielstil führte die Spielzeit zu einer konstanten Innovation von Steuerungsschemas. Von den einfachsten Vier-Wege-Knopf- und Schaltflächenkonfigurationen (wie in der hier genannten [Pac-Man-Datei)](https://en.wikipedia.org/wiki/Pac-Man)bis hin zu den äußerst spezifischen und komplizierten Schemas, die in den 90er und 00er Jahren zu sehen waren (z. B. in Simulatoren und Schienenschienen). Das eingabeschema, das auf dem Lunar Lander-Computer verwendet wird, ist aus zwei Gründen verzirrend: Drosselung und Immersion.

![Konsole "Lunar Lander" von Atari](images/atariconsole.png)<br>
*Lunar Lander-Konsole von Atari*

Warum haben sich Atari und so viele andere Spieleunternehmen dazu entschieden, die Eingabe zu überdenken?

Ein Kind, das durch einen 2000Er-Computer geht, ist natürlich von der neuesten, flashesten Maschine versiert. Lunar Lander verfügt jedoch über einen neuen Eingabebeiger, der sich aus der Menge ausdrängt.

Lunar Lander verwendet zwei Schaltflächen, um das  Boot nach links und rechts zu drehen, und einen Knopf, um die Menge der vom Versand erzeugten Schubsen zu steuern. Dieser Hebel gibt Benutzern ein bestimmtes Maß an Hand, das ein regulärer Zettel nicht bereitstellen kann. Es ist auch eine Komponente, die modernen Cockpits gemeinsam ist. Atari wollte, dass Lunar Lander den Benutzer in das Gefühl versetzt, tatsächlich ein Mondlandmodul zu pilotieren. Dieses Konzept wird als **taktile Immersion bezeichnet.**

Taktiles Immersion ist die Erfahrung von sensorischem Feedback bei sich wiederholenden Aktionen. In diesem Fall hilft die sich wiederholende Aktion der Anpassung des Drosselungshbels und der Drehung, die unsere Augen sehen und unsere Augen hören, den Spieler mit der Aktion zu verbinden, ein Boot auf der Mondoberfläche zu landen. Dieses Konzept kann an das Konzept des "Flusses" gebunden werden. Wenn ein Benutzer vollständig in einer Aufgabe mit der richtigen Mischung aus Herausforderung und Belohnung oder einfach ausgedrückt ist, befindet er sich "in der Zone".

Wohl ist der wichtigste Typ des Immersions in Mixed Reality das räumliche Immersion. Der eigentliche Punkt von Mixed Reality ist es, sich selbst zu übertäuischen, dass diese digitalen Objekte in der realen Welt vorhanden sind. Wir synthetisieren Hologramme in unserer Umgebung, räumlich versetzt in ganze Umgebungen und Umgebungen. Dies bedeutet nicht, dass wir nicht immer noch andere Arten von Immersion in unseren Erfahrungen einsetzen können, wie atari es bei der taktilen Immersion in Lunar Lander getan hat.

## <a name="designing-with-immersion"></a>Entwerfen mit Immersion

Wie können wir die taktile Immersion auf eine aktualisierte volumetrischen Sequel auf den Atari-Classic anwenden? Bevor sie das Eingabeschema in Angriff nehmen, muss das Spielkonstrukt für den dreidimensionalen Raum behandelt werden.

![Visualisieren der Oberflächenzuordnung in HoloLens](images/surfacemapping.png)<br>
*Visualisieren der räumlichen HoloLens*

Durch die Nutzung der Umgebung eines Benutzers haben wir effektiv unendliche Geländeoptionen, um unser Mondlandemodul zu landen. Damit das Spiel dem ursprünglichen Titel am meisten gefällt, könnte ein Benutzer Zielpads mit unterschiedlichen Schwierigkeiten in seiner Umgebung manipulieren und platzieren.

![Bekringen des Mondlandmoduls](images/640px-lm-hero.jpg)<br>
*Bekringen des Mondlandmoduls*

Der Benutzer muss das Eingabeschema erlernen, das Versandsystem steuern und über ein kleines Ziel verfügen, auf dem er landen kann. Eine erfolgreiche Spielerfahrung bietet die richtige Mischung aus Herausforderung und Belohnung. Der Benutzer kann einen Grad an Schwierigkeiten auswählen. Der einfachste Modus erfordert lediglich, dass der Benutzer erfolgreich in einen benutzerdefinierten Bereich auf einer Oberfläche landen muss, die vom Benutzer gescannt HoloLens. Sobald ein Benutzer das Spiel abfängt, kann er die Schwierigkeiten nach Besendung ankurbeln.

### <a name="adding-input-for-hand-gestures"></a>Hinzufügen von Eingaben für Handgesten

HoloLens Basiseingabe verfügt nur über zwei Gesten: [Air Tap und Bloom](../../design/gaze-and-commit.md#composite-gestures). Benutzer müssen sich keine kontextbezogenen Nuancen oder eine liste mit bestimmten Gesten merken, die die Plattformschnittstelle vielseitig und leicht zu erlernen machen. Während das System diese beiden Gesten möglicherweise nur verfügbar macht, HoloLens gerät zwei Hände gleichzeitig nachverfolgen. Unser Ode zu Lunar Lander ist eine [immersive App. Das bedeutet, dass wir den Basissatz von Gesten erweitern können, um zwei Hände zu nutzen und unsere eigenen taktilen Mittel für die Navigation mit Mondmodulen hinzuzufügen.

Wenn wir auf das ursprüngliche Steuerungsschema zurückkommen, **mussten wir für die Drehung und die Drehung lösen.** Der Nachteil ist, dass die Drehung im neuen Kontext eine zusätzliche Achse hinzufügt (technisch gesehen zwei, aber die Y-Achse ist für die Landung weniger wichtig). Die beiden unterschiedlichen Versandbewegungen eignen sich natürlich für die Zuordnung zu jeder Hand:

![Tippen und Ziehen der Geste zum Drehen des Landers auf allen drei Achsen](images/module-handdrag.gif)<br>
*Tippen und Ziehen der Geste zum Drehen des Landers auf allen drei Achsen*

**Schub**

Je höher der Hebel bewegt wurde, desto mehr Schub wurde auf das Boot angewendet, um den Hebel auf dem ursprünglichen Maschinengerät einer Skala von Werten zu unterordnen. Eine wichtige Nuance, auf die hier hingezeiget werden muss, ist, wie der Benutzer die Hand vom Steuerelement nehmen und einen gewünschten Wert verwalten kann. Wir können effektiv das Verhalten beim Tippen und Ziehen verwenden, um das gleiche Ergebnis zu erzielen. Der Stoßwert beginnt bei 0 (null). Der Benutzer tippt und zieht, um den Wert zu erhöhen. An diesem Punkt könnten sie es warten lassen. Jede Änderung des Tipp- und Ziehgestenwerts wäre das Delta des ursprünglichen Werts.

**Drehung**

Dies ist etwas schwieriger. Holografische "Drehen"-Schaltflächen zum Tippen machen dies zu einem lässigsten Erlebnis. Es gibt kein physisches Steuerelement, das genutzt werden kann, daher muss das Verhalten aus der Bearbeitung eines Objekts stammen, das den Lander darstellt, oder mit dem Lander selbst. Wir haben eine Methode mit "Tippen und Ziehen" entwickelt, die es einem Benutzer ermöglicht, es effektiv in die Richtung zu "pushen und zu pullen", in der er es sehen möchte. Wenn ein Benutzer tippt und hält, wird der Punkt im Raum, an dem die Geste initiiert wurde, zum Ursprung für die Drehung. Durch Ziehen vom Ursprung wird das Delta der Übersetzung der Hand (X,Y,Z) konvertiert und auf das Delta der Drehungswerte des Landers angewendet. Oder einfach: Wenn Sie nach links <-> nach oben <-> nach unten *ziehen, <->* wieder in Leerzeichen zurück ziehen, wird das Boot entsprechend gedreht.

Da die HoloLens zwei Hände nachverfolgen kann, kann die Drehung der rechten Hand zugewiesen werden, während die Drehung von der linken Seite gesteuert wird. Die Spielweise ist der Faktor für den Erfolg in diesem Spiel. Das *Gefühl* dieser Interaktionen hat die absolute höchste Priorität. Insbesondere im Kontext der taktilen Immersion. Ein Versand, der zu schnell reagiert, wäre schwierig zu steuern, während ein zu langsames Boot erfordert, dass der Benutzer das Boot für einen umstänglich langen Zeitraum "pushen und pullen" muss.

### <a name="adding-input-for-game-controllers"></a>Hinzufügen von Eingaben für Gamecontroller

Während Handgesten auf dem HoloLens eine neue Methode der feinen Steuerung bieten, gibt es immer noch ein gewisses Fehlen von "echtem" taktilem Feedback, das Sie von analogen Steuerelementen erhalten. Das Verbinden eines Xbox-Spielcontrollers ermöglicht es uns, dieses Gefühl der Physischen zu nutzen, während wir die Steuerstäbchen nutzen, um eine fein abgrenzende Kontrolle zu behalten.

Es gibt mehrere Möglichkeiten, das relativ einfache Steuerungsschema auf den Xbox-Controller anzuwenden. Da wir versuchen, so nah wie möglich an der ursprünglichen Einrichtung zu bleiben, wird die Schaltfläche **"Trigger"** am besten von "1" verwendet. Diese Schaltflächen sind analoge Steuerelemente,  d. h., sie haben mehr als einfache Ein- und Aus-Zustände, sie reagieren tatsächlich auf den Grad des Drucks, der auf sie gesetzt wird. Dadurch erhalten wir ein ähnliches Konstrukt wie **der 2016-Hebel**. Im Gegensatz zum ursprünglichen Spiel und der Handgeste schneide dieses Steuerelement die Schubkraft des Versands ab, sobald ein Benutzer den Trigger nicht mehr unter Druck setzt. Es bietet dem Benutzer immer noch den gleichen Grad an Freundlichkeit wie das ursprüngliche Spiel.

![Linker Thumbstick wird "Yaw" und "Roll" zugeordnet, der rechte Thumbstick "Pitch" und "Roll".](images/thumbsticksidebyside.gif)<br>
*Linker Thumbstick wird yaw und roll zugeordnet. Rechter Fingerabdruck wird Tonhöhe und Roll zugeordnet*

Die dualen Thumbsticks eignen sich natürlich für die Steuerung der Versandrotation. Leider gibt es drei Achsen, auf denen sich das Boot drehen kann, und zwei Thumbsticks, die beide zwei Achsen unterstützen. Dieser Konflikt bedeutet, dass entweder ein Thumbstick eine Achse steuert. oder es gibt eine Überlappung der Achsen für die Sticks. Die frühere Lösung hat sich als "fehlerhaft" gefühlt, da Die Daumenstäbchen ihre lokalen X- und Y-Werte inhärent kombinieren. Die zweite Lösung erforderte einige Tests, um zu ermitteln, welche redundanten Achsen sich am natürlichsten anfühlen. Im letzten Beispiel werden *yaw* und *roll* (Y- und X-Achsen) für den linken Thumbstick und *pitch* and *roll* (Z- und X-Achsen) für den rechten Thumbstick verwendet. Dies hat das natürlichste gefühlt, da *roll* scheinbar unabhängig gut mit *yaw* und pitch gekoppelt *ist.* Beachten Sie, dass die Verwendung beider Thumbsticks für *roll* ebenfalls den Drehwert verdoppelt. Es macht ziemlich viel Spaß, die Lander-Do-Schleifen zu haben.

Diese Beispiel-App veranschaulicht, wie räumliche Erkennung und taktiler Immersion eine Benutzererfahrung dank der erweiterbaren Eingabemuster Windows Mixed Reality erheblich verändern können. Während Lunar Lander fast 40 Jahre alt sein kann, werden die konzepte, die mit diesem kleinen Oktaggon-mit-Anstieg verfügbar gemacht werden, dauerhaft weiterleben. Warum sollten Sie sich bei der Vorstellung von der Zukunft nicht die Vergangenheit ansehen?

## <a name="technical-details"></a>Technische Details

Skripts und Prefabs für die Lunar Module-Beispiel-App finden Sie auf der [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule).

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
* [Periodensystem der Elemente 2.0](periodic-table-of-the-elements-2.md)
* [Galaxy Explorer 2.0](galaxy-explorer-update.md)