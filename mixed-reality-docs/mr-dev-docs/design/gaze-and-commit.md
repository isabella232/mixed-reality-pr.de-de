---
title: Anvisieren und Bestätigen
description: Erfahren Sie mehr über das Eingabemodell "Anvieren und Committen", darunter zwei Arten von Anvieren (Anvieren mit dem Kopf und Anvieren mit den Augen) und verschiedene Arten von Commits.
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Mixed Reality, Anvisieren, Anvisieren, Interaktion, Design, Blickverfolgung, Kopfverfolgung, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: db394ab4aded7136550e8e88eb3d66e06f3eeb92
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196565"
---
# <a name="gaze-and-commit"></a>Anvisieren und Bestätigen

_Anvieren und Committen_ ist ein grundlegendes Eingabemodell, das eng mit der Art und Weise zusammenhängt, wie wir mit der Maus mit unseren Computern interagieren: _Zeigen Sie & klicken Sie auf_. Auf dieser Seite werden zwei Arten von Eingaben zum Anvieren (Anvieren mit dem Kopf und mit den Augen) und verschiedene Arten von Commitaktionen vorgestellt. _Anvieren und Committen_ wird als weit entferntes Eingabemodell mit indirekter Bearbeitung betrachtet. Es wird am besten für die Interaktion mit holografischen Inhalten verwendet, die nicht erreichbar sind.

Mixed Reality-Headsets können die Position und Ausrichtung des Kopfes des Benutzers verwenden, um seinen Vektor für die Kopfrichtung zu bestimmen. Stellen Sie sich das Anvieren als einen Geleer vor, der direkt zwischen den Augen des Benutzers direkt nach vorn zeigen kann. Dies ist eine ziemlich grobe Annäherung hinsichtlich der Position, die der Benutzer betrachtet. Ihre Anwendung kann diesen Strahl mit virtuellen oder realen Objekten überschneiden und einen Cursor an dieser Position zeichnen, um den Benutzer darüber zu informieren, worauf er abzielt.

Neben dem Anverfolgen mit dem Kopf enthalten einige Mixed Reality-Headsets, z. B. HoloLens 2, Eyetrackingsysteme, die einen Anvektor für anverfolgte Augen erzeugen. Dies ermöglicht eine präzisere Messung der Position, die der Benutzer betrachtet. In beiden Fällen stellt das Anvisieren ein wichtiges Signal für die Absicht des Benutzers dar. Je besser das System die beabsichtigten Aktionen des Benutzers interpretieren und vorhersagen kann, desto mehr Benutzerzufriedenheit und Leistung werden verbessert.

Im Folgenden finden Sie einige Beispiele dafür, wie Sie als Mixed Reality-Entwickler vom Anvieren mit dem Kopf oder den Augen profitieren können:
* Ihre App kann das Anvisieren mit den Hologrammen in Ihrer Szene überschneiden, um zu bestimmen, wo die Aufmerksamkeit des Benutzers liegt (genauer mit dem Anvisieren mit den Augen).
* Ihre App kann Gesten und Controllerdrücke basierend auf dem Anvisieren des Benutzers kanalisieren, wodurch der Benutzer seine Hologramme nahtlos auswählen, aktivieren, greifen, scrollen oder anderweitig interagieren kann.
* Ihre App kann es dem Benutzer gestatten, Hologramme auf realen Oberflächen zu platzieren, indem er seinen Blickstrahl mit dem Gitternetz der räumlichen Abbildung überschneidet.
* Ihre App kann wissen, wenn der Benutzer nicht in richtung eines wichtigen Objekts sucht. Dies kann dazu führen, dass Ihre App visuelle und audioorientierte Hinweise zu diesem Objekt gibt.

<br>

## <a name="device-support"></a>Geräteunterstützung

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Eingabemodell</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1. Generation)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
    </tr>
     <tr>
        <td>Anvisieren mit dem Kopf und Ausführen</td>
        <td>✔️ Empfohlen</td>
        <td>✔️ Empfohlen (dritte Auswahl – <a href="interaction-fundamentals.md">Siehe andere Optionen</a>)</td>
        <td>➕ Alternative Option</td>
    </tr>
         <tr>
        <td>Anvisieren mit den Augen und Ausführen</td>
        <td>❌ Nicht verfügbar</td>
        <td>✔️ Empfohlen (dritte Auswahl – <a href="interaction-fundamentals.md">Siehe andere Optionen</a>)</td>
        <td>❌ Nicht verfügbar</td>
    </tr>
</table>

## <a name="head-and-eye-tracking-design-concepts-demo"></a>Demo zu Designkonzepten für Kopf- und Blickverfolgung

Wenn Sie Designkonzepte für Kopf- und Blickverfolgung in Aktion sehen möchten, sehen Sie sich die Videodemo **Designing Holograms - Head Tracking and Eye Tracking** (Entwerfen von Hologrammen – Kopfverfolgung und Eyetracking) weiter unten an. Wenn Sie fertig sind, fahren Sie fort, um ausführlichere Informationen zu bestimmten Themen zu erhalten.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

*Dieses Video wurde aus der App "Entwerfen von Hologrammen" HoloLens 2 aufgenommen. Laden Sie hier herunter, und profitieren Sie [von der vollständigen Erfahrung.](https://aka.ms/dhapp)*

## <a name="gaze"></a>Anvisieren

### <a name="eye--or-head-gaze"></a>Mit den Augen oder mit dem Kopf?
Bei der Frage, ob Sie das Eingabemodell "Anvieren mit den Augen und Commit" oder "Anvieren mit dem Kopf und Commit" verwenden sollten, gibt es mehrere Überlegungen. Wenn Sie für ein immersives Headset oder für HoloLens (1. Generation) entwickeln, ist die Wahl einfach: Anvitieren mit dem Kopf und Commit. Wenn Sie für die entwicklung HoloLens 2, wird die Auswahl etwas schwieriger. Es ist wichtig, die Vorteile und Herausforderungen zu verstehen, die mit jedem dieser Beiden verbunden sind.
In der folgenden Tabelle haben wir einige allgemeine Pros und Kontras kompiliert, um das Ziel mit dem Kopf- und dem Anvieren mit den Augen gegenüber zu vergleichen. Dies ist noch lange nicht abgeschlossen, und wir empfehlen Ihnen, hier mehr über das Anvieren mit den Augen in Mixed Reality zu erfahren:
* [Eye tracking on HoloLens 2](eye-tracking.md): General introduction of our new eye tracking capability on HoloLens 2 including some developer guidance. 
* [Interaktion mit dem Anvistik-Blick:](eye-gaze-interaction.md)Entwurfsüberlegungen und -empfehlungen bei der Planung der Verwendung von EyeTracking als Eingabe.

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
   <tr>
        <td><strong>Zielgruppenadressierung mit den Augen</strong></td>
        <td><strong>Anvisieren mit dem Kopf</strong></td>
    </tr>
    <tr>
        <td>schnell!</td>
        <td>Langsamer</td>
    </tr>
    <tr>
        <td>Geringer Aufwand (abschwächen aller erforderlichen Körperbewegungen)</td>
        <td>Kann ermüdend sein: Mögliche Störungen (z. B. Hängebelastung)</td>
    </tr>
    <tr>
        <td>Erfordert keinen Cursor, aber es wird ein dezentes Feedback empfohlen.</td>
        <td>Erfordert das Anzeigen eines Cursors</td>
    </tr>
    <tr>
        <td>Keine reibungslosen Augenbewegungen– z. B. nicht gut zum Zeichnen</td>
        <td>Kontrollierter und expliziter</td>
    </tr>
    <tr>
        <td>Schwierig für kleine Ziele (z. B. kleine Schaltflächen oder Weblinks)</td>
        <td>Zuverlässige! Toller Fallback!</td>
    </tr>
    <tr>
        <td>...</td>
        <td>...</td>
    </tr>
</table>

Unabhängig davon, ob Sie das Anvieren mit dem Kopf oder das Anvieren mit den Augen für Ihr Eingabemodell zum Anvieren und Committen verwenden, gibt es jeweils unterschiedliche Entwurfseinschränkungen. Diese werden separat in den Artikeln [Anvieren mit](gaze-and-commit-eyes.md) den Augen und Committen und [Anvieren mit](gaze-and-commit-head.md) dem Kopf und Commit behandelt.

<br>

---

### <a name="cursor"></a>Cursor

:::row:::
    :::column:::
        Für das Anvieren mit dem Kopf sollten die meisten Apps einen [Cursor](cursors.md) oder einen anderen akustischen/visuellen Hinweis verwenden, um dem Benutzer Vertrauen in die Interaktion zu geben. In der Regel positionieren Sie diesen Cursor in der Welt, wo der Strahl des Anvierens des Kopfes zuerst ein Objekt überschneidet, bei dem es sich um ein Hologramm oder eine reale Oberfläche handeln kann.<br>
        <br>
        Für das Anvieren mit den Augen empfiehlt es sich im Allgemeinen, *keinen* Cursor anzuzeigen, da dies für den Benutzer schnell ablenkend und nervig werden kann. Markieren Sie stattdessen visuelle Ziele, oder verwenden Sie einen schwachen Blickcursor, um die Zuverlässigkeit der Interaktion des Benutzers zu gewährleisten. Weitere Informationen finden Sie in unserer [Entwurfsleitfäden für blickbasierte Eingaben](eye-tracking.md) zu HoloLens 2.
    :::column-end:::
        :::column:::
       ![Ein Beispiel für einen visuellen Cursor zum Anzeigen des Anv](images/cursor.jpg)<br>
       *Bild: Beispiel für einen visuellen Cursor zum Anzeigen des Anv*
    :::column-end:::
:::row-end:::

<br>

---

## <a name="commit"></a>Commit
Nachdem wir über verschiedene Möglichkeiten zum _Anvischen_ eines Ziels gesprochen haben, sprechen wir ein wenig mehr über den _Committeil_ beim _Anvischen und Committen._
Nachdem ein Objekt oder ein Benutzeroberflächenelement als Ziel verwendet wurde, kann der Benutzer mithilfe einer sekundären Eingabe interagieren oder darauf klicken. Dies wird als Bestätigungsschritt (Commit) des Eingabemodells bezeichnet. 

Die folgenden Methoden zum Ausführen werden unterstützt:
- Handgeste zum Tippen in die Luft (d. h., die Hand vor Ihnen heben und Zeigefinger und Daumen zusammenbringen)
- Sagen _Sie "select"_ oder einen der Sprachbefehle, die als Ziel verwendet werden.
- Drücken einer einzelnen Schaltfläche auf einem [HoloLens-Clicker](/hololens/hololens1-clicker)
- Klicken Sie auf einem Xbox-Gamepad auf die Schaltfläche "A".
- Klicken Sie auf die Schaltfläche "A" auf einem adaptiven Xbox-Controller.

### <a name="gaze-and-air-tap-gesture"></a>Geste "Anv" und "Tippen in die Luft"
„In die Luft tippen“ ist eine Tippbewegung mit aufrecht gehaltener Hand Um einen Tippen in die Luft zu verwenden, heben Sie den Zeigefinger auf die bereite Position, und heften Sie dann mit dem Daumen zusammen, und heben Sie den Zeigefinger wieder hoch, um es frei zu machen. Bei HoloLens (1. Generation) ist Tippen in die Luft die häufigste sekundäre Eingabe.


:::row:::
    :::column:::
       ![Finger in der bereiten Position](images/readyandpress-ready.jpg)<br>
       **Finger in der bereiten Position**<br>
    :::column-end:::
    :::column:::
       ![Drücken Sie den Finger nach unten, um zu tippen oder zu klicken.](images/readyandpress-press.jpg)<br>
        **Drücken Sie den Finger nach unten, um zu tippen oder zu klicken.**<br>
    :::column-end:::
:::row-end:::


Tippen in die Luft ist auch auf HoloLens 2. Sie wurde von der ursprünglichen Version gelockert. Fast alle Arten von Pinches werden jetzt unterstützt, solange die Hand aufrecht ist und still hält. Dadurch können Benutzer die Geste viel einfacher erlernen und verwenden. Dieses neue Tippen in die Luft ersetzt das alte über dieselbe API, sodass vorhandene Anwendungen das neue Verhalten automatisch nach der Neukompilierung für HoloLens 2.

<br>

---

### <a name="gaze-and-select-voice-command&quot;></a>Sprachbefehl &quot;Anv&quot; und &quot;Auswählen&quot;
Sprachbefehle sind eine der wichtigsten Interaktionsmethoden in Mixed Reality. Es bietet einen leistungsstarken Freihandmechanismus zum Steuern des Systems. Es gibt verschiedene Arten von Sprachinteraktionsmodellen:

- Der generische Befehl &quot;Select&quot;, der eine Click-Aktuation oder einen Commit als sekundäre Eingabe verwendet.
- Objektbefehle (z. B. &quot;Schließen&quot; oder &quot;Vergrößern") führen einen Commit für eine Aktion als sekundäre Eingabe aus und committen sie.
- Globale Befehle (z. B. "Gehe zu Start") erfordern kein Ziel.
- Konversationsbenutzeroberflächen oder Entitäten wie Cortana verfügen über eine KI-Funktion in natürlicher Sprache.
- Benutzerdefinierte Sprachbefehle

Weitere Informationen zu Details und eine umfassende Liste der verfügbaren Sprachbefehle und deren Verwendung finden Sie in unserer Anleitung zur [Sprachbefehlsführung.](../out-of-scope/voice-design.md)

<br>

---


### <a name="gaze-and-hololens-clicker"></a>Gaze und HoloLens Clicker

:::row:::
    :::column:::
        HoloLens Clicker ist das erste Peripheriegerät, das speziell für HoloLens entwickelt wurde. Sie ist in der HoloLens Development Edition (1. Generation) enthalten. Mit dem HoloLens-Clicker kann ein Benutzer mit minimaler Handbewegung klicken und als sekundäre Eingabe committen. Der HoloLens-Clicker stellt über Bluetooth Low Energy (BTLE) eine Verbindung mit HoloLens (1. Generation) oder HoloLens 2 her.<br>
        <br>
        [Weitere Informationen und Anweisungen zum Koppeln des Geräts](../discover/hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        *Abbildung: HoloLens-Clicker*
    :::column-end:::
        :::column:::
       ![HoloLens-Klick-Gerät](images/hololens-clicker-500px.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="gaze-and-xbox-wireless-controller"></a>Anv und Xbox Wireless Controller

:::row:::
    :::column:::
        Der Xbox Wireless Controller führt eine Klickbetätigung als sekundäre Eingabe mithilfe der Schaltfläche "A" aus. Das Gerät wird einem Standardsatz von Aktionen zugeordnet, die beim Navigieren und Steuern des Systems helfen. Wenn Sie den Controller anpassen möchten, verwenden Sie die Xbox Zubehör Anwendung, um Ihren Xbox Wireless Controller zu konfigurieren.<br>
        <br>
        [Koppeln eines Xbox-Controllers mit Ihrem PC](../discover/hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        *Abbildung: Xbox Wireless Controller*
    :::column-end:::
        :::column:::
       ![Xbox Wireless Controller](images/xboxcontroller.jpg)<br>
    :::column-end:::
:::row-end:::



<br>

---


### <a name="gaze-and-xbox-adaptive-controller"></a>Anving und Xbox Adaptive Controller
Der Xbox Adaptive Controller wurde hauptsächlich zur Erfüllung der Anforderungen von Gamern mit eingeschränkter Mobilität entwickelt und ist ein einheitlicher Hub für Geräte, mit dem Mixed Reality zugänglicher wird.

Der Xbox Adaptive Controller führt einen Klick als sekundäre Eingabe aus, indem er die Schaltfläche "A" verwendet. Das Gerät ist einem Standardsatz von Aktionen zugeordnet, die beim Navigieren und Steuern des Systems helfen. Wenn Sie den Controller anpassen möchten, verwenden Sie die Xbox Zubehör, um Ihren Xbox Adaptive Controller zu konfigurieren.

![Xbox Adaptive Controller](images/xbox-adaptive-controller-devices.jpg)<br>
*Xbox Adaptive Controller*

Verbinden Sie externe Geräte wie Switches, Schaltflächen, Einbinder und Halter, um eine benutzerdefinierte Controllererfahrung zu erstellen, die ihre eigene ist. Eingaben für Schaltflächen, Thumbsticks und Trigger werden mit Hilfsgeräten gesteuert, die über 3,5-mm-Buchsen und USB-Anschlüsse verbunden sind.

![Xbox Adaptive Controller-Anschlüsse](images/xbox-adaptive-controller-ports.jpg)<br>
*Xbox Adaptive Controller-Anschlüsse*

[Anweisungen zum Koppeln des Geräts](../discover/hardware-accessories.md#pairing-bluetooth-accessories)

<a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>Weitere Informationen, die auf der Xbox-Website verfügbar sind</a>

<br>

---

## <a name="composite-gestures"></a>Zusammengesetzte Gesten

### <a name="air-tap"></a>In die Luft tippen
Die Tippbewegung in die Luft (und die anderen gesten unten) reagiert nur auf einen bestimmten Tippen. Um andere Tippbewegungen wie Menu oder Grasp zu erkennen, muss Ihre Anwendung direkt die Interaktionen auf niedrigerer Ebene verwenden, die oben im Abschnitt mit den beiden wichtigsten Komponentengesten beschrieben werden.

### <a name="tap-and-hold"></a> Tippen und halten Sie 
„Halten“ bedeutet einfach, die Position mit dem Finger nach unten beim „In die Luft tippen“ beizubehalten. Die Kombination aus Tippen in die Luft und Halten ermöglicht verschiedene komplexere "Klick- und Drag"-Interaktionen in Kombination mit Armbewegungen, z. B. das Aufnehmen eines Objekts anstelle der Aktivierung oder sekundäre Interaktionen mit dem Mausdown, z. B. das Anzeigen eines Kontextmenüs.
Beim Entwerfen für diese Geste sollte jedoch Vorsicht geboten werden, da Benutzer bei jeder erweiterten Geste anfällig sein können, ihre Handhaltungen zu lockern.

### <a name="manipulation"></a>Manipulation
Manipulationsgesten können zum Verschieben, Ändern der Größe oder Drehen eines Hologramms verwendet werden, wenn das Hologramm 1:1 auf die Handbewegungen des Benutzers reagieren soll. Eine Verwendungsmöglichkeit für solche 1:1-Bewegungen ist es, den Benutzer in der Umgebung zeichnen oder malen zu lassen.
Die anfängliche Zielbestimmung für eine Manipulationsgeste sollte durch Anvisieren oder Zeigen erfolgen. Sobald das Tippen und Halten beginnt, wird jede Objektbearbeitung durch Handbewegungen verarbeitet, wodurch der Benutzer sich beim Bearbeiten umschauen kann.

### <a name="navigation"></a>Navigation
Navigationsgesten funktionieren wie ein virtueller Joystick und können zur Navigation in Widgets der Benutzeroberfläche, z. B. Radialmenüs, verwendet werden. Sie tippen und halten, um die Geste zu starten, und bewegen dann Ihre Hand in einem normalisierten 3D-Würfel, der um die erste Betätigung herum angeordnet ist. Sie können Ihre Hand entlang der X-, Y- oder Z-Achse von einem Wert von -1 bis 1 bewegen, während 0 der Ausgangspunkt ist.
Mithilfe der Navigation können geschwindigkeitsbasierte kontinuierliche Gesten zum Scrollen oder Zoomen erstellt werden, ähnlich dem Scrollen bei einer 2D-Benutzeroberfläche durch Klicken mit der mittleren Maustaste und anschließendes Bewegen der Maus nach oben und unten.

Navigation mit Schienen bezieht sich auf die Fähigkeit, Bewegungen auf einer bestimmten Achse zu erkennen, bis ein bestimmter Schwellenwert auf dieser Achse erreicht ist. Dies ist nur nützlich, wenn die Bewegung auf mehr als einer Achse in einer Anwendung durch den Entwickler aktiviert wird, z. B. wenn eine Anwendung so konfiguriert ist, dass Navigationsgesten über die X-, Y-Achse, aber auch die angegebene X-Achse mit Schienen erkannt werden. In diesem Fall erkennt das System Handbewegungen über die X-Achse, solange sie innerhalb einer imaginären Schienen (Führungslinie) auf der X-Achse verbleiben, wenn die Handbewegung auch auf der Y-Achse auftritt.

Innerhalb von 2D-Apps können Benutzer mit vertikalen Navigationsgesten innerhalb der App scrollen, zoomen oder ziehen. Dadurch werden virtuelle Fingerberührungen in der App eingeführt, um Gesten für die Toucheingabe desselben Typs zu simulieren. Benutzer können auswählen, welche dieser Aktionen ausgeführt werden, indem sie zwischen den Tools auf der Leiste oberhalb der Anwendung umschalten, indem sie entweder die Schaltfläche auswählen oder "<Scrollen/Ziehen/Zoomen> Tool" sagen.

[Weitere Informationen zu zusammengesetzten Gesten](gaze-and-commit.md#composite-gestures)

## <a name="gesture-recognizers"></a>Gestenerkennung

Ein Vorteil der Gestenerkennung besteht darin, dass Sie eine Gestenerkennung nur für die Gesten konfigurieren können, die das aktuell als Ziel dienende Hologramm akzeptieren kann. Die Plattform unterscheidet nur nach Bedarf nach Bedarf, um diese bestimmten unterstützten Gesten zu unterscheiden. Auf diese Weise kann ein Hologramm, das nur das Tippen in die Luft unterstützt, eine beliebige Zeitspanne zwischen Drücken und Loslassen akzeptieren, während ein Hologramm, das tippen und halten unterstützt, das Tippen auf einen Haltebereich nach dem Schwellenwert für die Wartezeit heraufstufen kann.

## <a name="hand-recognition"></a>Handerkennung
HoloLens erkennt Handgesten, indem die Position einer oder beider Hände, die für das Gerät sichtbar sind, verfolgt wird. HoloLens erkennt Hände, wenn sie sich entweder im Bereitschaftszustand (Handrücken mit nach oben gerichtetem Zeigefinger zu Ihnen gewandt) oder im gedrückten Zustand (Handrücken mit nach unten gerichtetem Zeigefinger zu Ihnen gewandt) befinden. Wenn sich die Hände in anderen Posen befinden, ignoriert HoloLens sie.
Für jede Hand, die HoloLens erkennt, können Sie ohne Ausrichtung und gedrückten Zustand auf ihre Position zugreifen. Wenn sich die Hand dem Rand des Gestenrahmens nähert, erhalten Sie auch einen Richtungsvektor, den Sie dem Benutzer zeigen können, damit er weiß, wie er seine Hand bewegen muss, um sie dorthin zurückzubringen, wo sie von HoloLens erkannt werden kann.

## <a name="gesture-frame"></a>Gestenrahmen
Bei Gesten auf HoloLens muss sich die Hand innerhalb eines Gestenrahmens in einem Bereich befindet, den die Gestenerkennungskameras entsprechend sehen können, von der Stirn bis zur Tante und zwischen den Seiten. Benutzer müssen in diesem Erkennungsbereich sowohl für den Erfolg der Aktion als auch für ihren eigenen Komfort trainiert werden. Viele Benutzer gehen zunächst davon aus, dass sich der Gestenrahmen innerhalb ihrer Ansicht über HoloLens belassen und die Arme unerbittlich halten muss, um zu interagieren. Bei Verwendung des HoloLens-Clickers ist es nicht erforderlich, dass sich die Hände innerhalb des Gestenrahmens befinden.

Insbesondere bei kontinuierlichen Gesten besteht die Gefahr, dass Benutzer ihre Hände außerhalb des Gestenrahmens bewegen, während sie z. B. während der Geste ein holografisches Objekt bewegen und ihr beabsichtigtes Ergebnis verlieren.

Sie sollten die folgenden drei Aspekte berücksichtigen:

- Benutzerinformationen zum Vorhandensein des Gestenrahmens und zu den ungefähren Grenzen. Dies wird während des HoloLens-Setups vermittelt.

- Benachrichtigen von Benutzern, wenn sich ihre Gesten in der Nähe der Gestenrahmengrenzen innerhalb einer Anwendung befinden, bis zu dem Grad, in dem eine verlorene Geste zu unerwünschten Ergebnissen führt. Die Forschung hat die wichtigsten Qualitäten eines solchen Benachrichtigungssystems gezeigt. Die HoloLens-Shell bietet ein gutes Beispiel für diese Art von Benachrichtigung: visuelle Elemente am zentralen Cursor, die die Richtung angeben, in der die Begrenzungsüberquerung stattfindet.

- Die Folgen des Überschreitens der Begrenzungen des Gestenrahmens sollten minimiert werden. Im Allgemeinen bedeutet dies, dass das Ergebnis einer Geste an der Grenze angehalten und nicht umgekehrt werden sollte. Wenn ein Benutzer beispielsweise ein holografisches Objekt über einen Raum bewegt, sollte die Bewegung anhalten, wenn der Gestenrahmen verletzt wird, und nicht an den Ausgangspunkt zurückgegeben werden. Der Benutzer kann frustriert sein, kann aber die Grenzen schneller verstehen und muss nicht jedes Mal seine vollständigen beabsichtigten Aktionen neu starten.



## <a name="see-also"></a>Weitere Informationen
* [Augenbasierte Interaktion](eye-gaze-interaction.md)
* [Blickverfolgung auf HoloLens 2](eye-tracking.md)
* [Anvisieren und Verweilen](gaze-and-dwell.md)
* [Hände – Direkte Manipulation](direct-manipulation.md)
* [Hände – Gesten](gaze-and-commit.md#composite-gestures)
* [Hände – Zeigen und Ausführen](point-and-commit.md)
* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Spracheingabe](voice-input.md)