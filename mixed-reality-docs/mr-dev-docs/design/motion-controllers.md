---
title: Bewegungscontroller
description: Erfahren Sie, wie Sie Eingabeinteraktionen mit Mixed Reality Motion-Controllern in Ihren Anwendungen einrichten, koppeln und verwalten.
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: 6dof-Controller, Motion-Controller, Kopplung, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, Scrollen, Klammer, Zustand
ms.openlocfilehash: bced0115eee5e753ef01d129ae10910acdca2b7b91020117f53b2ebf8833a130
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224883"
---
# <a name="motion-controllers"></a>Bewegungscontroller

:::row:::
    :::column:::
        Motion-Controller sind [Hardwareaccessements,](../discover/hardware-accessories.md) mit denen Benutzer in Mixed Reality Maßnahmen ergreifen können. Ein Vorteil von Motion-Controllern gegenüber [Gesten](gaze-and-commit.md#composite-gestures) ist, dass die Controller eine präzise Position im Raum haben, die eine differenzierte Interaktion mit digitalen Objekten ermöglicht. Bei Windows Mixed Reality immersiven Headsets sind Motion-Controller die primäre Methode, mit der Benutzer in ihrer Welt Maßnahmen ergreifen.<br>
        <br>
        *Abbildung: Ein Windows Mixed Reality Motion Controller*
    :::column-end:::
        :::column:::
       ![Windows Mixed Reality Motion-Controller](images/winmr-ck-1080x1080-350px.jpg)<br> 
    :::column-end:::
:::row-end:::

<br>

---

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
     <td>Bewegungscontroller</td>
     <td>❌</td>
     <td>❌</td>
     <td>✔️</td>
</tr>
</table>

## <a name="hardware-details"></a>Hardwaredetails

<iframe width="940" height="530" src="https://www.youtube.com/embed/1nlcdDNOdm8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Windows Mixed Reality Motion-Controller bieten eine präzise und reaktionsfähige Bewegungsnachverfolgung in Ihrem Sichtfeld mithilfe der Sensoren im immersiven Headset. Es ist nicht erforderlich, Hardware auf den Wänden in Ihrem Raum zu installieren. Diese Motion-Controller bieten die gleiche einfache Einrichtung und Portabilität wie Windows Mixed Reality immersive Headsets. Unsere Gerätepartner planen, diese Controller an diesem Feiertag in Einzelhandelsregalen zu verkaufen und zu verkaufen.

![Kennenlernen Ihres Controllers](images/controllerimage-750px.png)<br>
*Kennenlernen Ihres Controllers*

**Funktionen:**
* Optische Nachverfolgung
* Trigger
* Schaltfläche "Greifen"
* Thumbstick
* Touchpad

## <a name="setup"></a>Setup

### <a name="before-you-begin"></a>Vorbereitung

**Sie benötigen Folgendes:**
* Eine Gruppe von zwei Motion-Controllern.
* Vier AA-Akkus.
* Ein PC mit Bluetooth 4.0-Unterstützung.

**Suchen nach Windows, Unity und Treiberupdates**
* Informationen zur Mixed Reality-Entwicklung finden Sie unter [Installieren der Tools](../develop/install-the-tools.md) für die bevorzugten Versionen von Windows, Unity usw.
* Stellen Sie sicher, dass Sie über die aktuellsten [Headset- und Motion Controller-Treiber verfügen.](/windows/mixed-reality/enthusiast-guide/mixed-reality-software)

### <a name="pairing-controllers"></a>Kopplung von Controllern

Motion-Controller können mithilfe Windows Einstellungen wie jedes andere Bluetooth Gerät mit dem Host-PC verbunden werden.

1. Fügen Sie zwei AA-Akkus in die Rückseite des Controllers ein. Lassen Sie die Akkuabdeckung vorerst aus.
2. Wenn Sie einen externen USB Bluetooth Adapter anstelle eines integrierten Bluetooth Radios verwenden, lesen Sie die [bewährten Methoden für Bluetooth,](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) bevor Sie fortfahren. Stellen Sie für die Desktopkonfiguration mit integriertem Radio sicher, dass die Antenne verbunden ist.
3. Öffnen Sie **Windows Einstellungen**  ->  **Geräte**  ->  **Hinzufügen Bluetooth oder eines anderen Geräts**  ->  **Bluetooth,** und entfernen Sie alle früheren Instanzen von "Motion Controller – Right" und "Motion controller – Left". Aktivieren Sie auch die Kategorie Andere Geräte am unteren Rand der Liste.
4. Wählen **Sie Add Bluetooth or other device (Hinzufügen** Bluetooth oder eines anderen Geräts) aus, um Bluetooth Geräte zu ermitteln.
5. Halten Sie die Windows-Taste des Controllers gedrückt, um den Controller zu aktivieren, und lassen Sie ihn los, sobald er wieder losgelassen wird.
6. Halten Sie die Kopplungsschaltfläche gedrückt (Registerkarte im Akkufach), bis die LEDs mit dem Pulsieren beginnen.

:::row:::
    :::column:::
7. Warten Sie , bis "Motion controller - Left" oder "Motion controller - Right" am ende der Liste angezeigt wird. Wählen Sie diese Option aus, um eine Kopplung zu wählen. Der Controller vibriert einmal, wenn er verbunden ist.<br>
        <br>
        *Bild: Wählen Sie "Bewegungscontroller" zum Koppeln aus. Wenn mehrere Instanzen vorhanden sind, wählen Sie eine am unteren Rand der Liste aus.*
    :::column-end:::
        :::column:::
       ![Wählen Sie Motion controller to pair (Bewegungscontroller zu koppeln) aus, wenn mehrere Instanzen eine davon auswählen, die unten in der Liste angezeigt wird.](images/450px-bluetooth-add-a-device-300px.png)<br> 
    :::column-end:::
:::row-end:::
   
8. Der Controller wird in den Bluetooth-Einstellungen unter **der Kategorie "Maus, Tastatur, & Stift"** als **Verbunden** angezeigt. An diesem Punkt erhalten Sie möglicherweise ein Firmwareupdate . Weitere Informationen finden Sie im [nächsten Abschnitt.](motion-controllers.md#updating-controller-firmware)
9. Akkuabdeckung erneut anfügen.
10. Wiederholen Sie die Schritte 1 bis 9 für den zweiten Controller.

<br>

:::row:::
    :::column:::
        Nach der erfolgreichen Kopplung beider Controller sollten Ihre Einstellungen in der **Kategorie "Maus, Tastatur, & Stift"** wie folgt aussehen: <br>
        <br>
        *Bild: Verbundene Motion-Controller*
    :::column-end:::
        :::column:::
       ![Verbundene Motion-Controller](images/450px-motion-controller-connected-300px.png)<br>
    :::column-end:::
:::row-end:::

Wenn die Controller nach der Kopplung ausgeschaltet werden, wird ihr Status als Gekoppelt angezeigt. Bei Controllern, die dauerhaft unter der Kategorie "Andere Geräte" stehen, ist die Kopplung möglicherweise nur teilweise abgeschlossen. Führen Sie in diesem Fall die Kopplungsschritte erneut aus, um den Controller funktionsfähig zu machen.

### <a name="updating-controller-firmware"></a>Aktualisieren der Controllerfirmware

* Wenn ein immersives Headset mit der neuen Controllerfirmware mit Ihrem PC verbunden ist, wird die Firmware automatisch an Ihre Motion-Controller gepusht, wenn Sie sie das nächste Mal einschalten. Controllerfirmwareupdates werden durch ein Muster der Beleuchtung von LED-Quadranten in einer kreisförmigen Bewegung angegeben und dauern 1-2 Minuten.


:::row:::
    :::column:::
* Nach Abschluss des Firmwareupdates werden die Controller neu gestartet und die Verbindung wiederhergestellt. Beide Controller sollten jetzt verbunden sein. <br>
        <br>
        *Image: Controller, die in Bluetooth Einstellungen verbunden sind*
    :::column-end:::
        :::column:::
       ![Verbundene Controller](images/cyk-connected-300px.jpg)<br>
    :::column-end:::
:::row-end:::


* Überprüfen Sie, ob Ihre Controller ordnungsgemäß funktionieren:
    1. Starten Sie **Mixed Reality-Portal,** und geben Sie Ihr Mixed Reality Home ein.
    2. Verschieben Sie Ihre Controller, überprüfen Sie die Nachverfolgung, testen Sie Schaltflächen, und überprüfen Sie, ob [die Teleportierung](../discover/navigating-the-windows-mixed-reality-home.md#getting-around-your-home) funktioniert. Wenn dies nicht dere ist, sehen Sie sich die [Problembehandlung für den Motion-Controller an.](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers)

## <a name="gazing-and-pointing"></a>An- und Zeigen

Windows Mixed Reality unterstützt zwei wichtige Interaktionsmodelle: **Anv gaze und commit** sowie **zeigen und committen:**
* Beim **Anvischen und Committen** zielen Benutzer auf ein Objekt mit ihrem [Anvischen](gaze-and-commit.md)und wählen dann Objekte mit Hand-Luft-Tippen, einem Gamepad, einem Clicker oder ihrer Stimme aus.
* Mit **Punkt und Commit** kann ein Benutzer einen zeigenden Bewegungscontroller auf das Zielobjekt ausrichten und dann Objekte mit dem Trigger des Controllers auswählen.

Apps, die zeigen mit Motion-Controllern unterstützen, sollten nach Möglichkeit auch anvgesteuerte Interaktionen ermöglichen, um Benutzern eine Auswahl zu geben, welche Eingabegeräte sie verwenden.

### <a name="managing-recoil-when-pointing"></a>Verwalten der Zurückdrückung beim Zeigen

Wenn Sie Motion-Controller zum Zeigen und Committen verwenden, verwenden Ihre Benutzer den Controller, um durch Pullen des Triggers auf den Controller abzuzielen und zu interagieren. Benutzer, die den Trigger ungern pullen, versuchen möglicherweise, den Controller am Ende des Trigger-Pulls höher als vorgesehen zu erreichen.

Um eine solche Zurückdrückung zu verwalten, die auftreten kann, wenn Benutzer den Trigger pullen, kann Ihre App ihren Zielstrahl ausrichten, wenn der Analogachsenwert des Triggers über 0,0 steigt. Sie können dann mit diesem Zielstrahl einige Frames später maßnahmen, sobald der Triggerwert 1,0 erreicht, solange der letzte Press innerhalb eines kurzen Zeitfensters erfolgt. Bei Verwendung der [zusammengesetzten Tippgeste](gaze-and-commit.md#composite-gestures)auf höherer Ebene verwaltet Windows diese Zielstrahlerfassung und das Timeout für Sie.

## <a name="grip-pose-vs-pointing-pose"></a>Klammerpose im Vergleich zu zeigender Pose

Windows Mixed Reality unterstützt Motion-Controller in unterschiedlichen Formfaktoren, wobei sich der Entwurf jedes Controllers in der Beziehung zwischen der Handposition des Benutzers und der natürlichen Vorwärtsrichtung unterscheidet, die Apps beim Rendern des Controllers verwenden sollten.

Um diese Controller besser darzustellen, gibt es zwei Arten von Posen, die Sie für jede Interaktionsquelle untersuchen können: die **Klammerpose** und die **Zeigerpose**.

### <a name="grip-pose"></a>Klammerpose

Die **Klammerhaltung** stellt entweder die Position der Handfläche dar, die von einem HoloLens erkannt wurde, oder die Handfläche, die einen Bewegungscontroller hält.

Bei immersiven Headsets wird die Klammerpose am besten verwendet, um **die Hand des Benutzers** oder ein Objekt in der Hand des **Benutzers** zu rendern, z. B. einen Schläger oder eine Schütze. Die Klammerpose wird auch beim Visualisieren eines Bewegungscontrollers verwendet, da das **renderbare Modell,** das von Windows für einen Motion Controller bereitgestellt wird, die Klammerpose als Ursprung und Drehmittelpunkt verwendet.

Die Klammerpose ist speziell wie folgt definiert:
* Die **Klammerposition:** Der Schwerpunkt der Handfläche, wenn der Controller auf natürliche Weise gehalten wird, wird nach links oder rechts angepasst, um die Position innerhalb des Reglers zu zentriert. Auf dem Windows Mixed Reality Motion-Controller ist diese Position in der Regel an der Schaltfläche Greifen ausgerichtet.
* **Die Rechte Achse der Ziehrichtung:** Wenn Sie Ihre Hand vollständig öffnen, um eine flache Fünf-Finger-Pose zu bilden, ist der Strahl, der für Ihre Handfläche normal ist (vorwärts von der linken Handfläche, rückwärts von der rechten Handfläche)
* **Die Vorwärtsachse der Klammerausrichtung:** Wenn Sie Ihre Hand teilweise schließen (als ob Sie den Controller halten), zeigt der Strahl, der "vorwärts" durch die Von den Nichtfingerfinger gebildeten Strahl zeigt.
* Die **Nach-oben-Achse der Klammerausrichtung:** Die nach oben-Achse, die durch die Definitionen Rechts und Vorwärts impliziert wird.

### <a name="pointer-pose"></a>Zeigerpose

Die **Zeigerpose** stellt die Spitze des Controllers dar, der nach vorn zeigt.

Die vom System bereitgestellte Zeigerpose wird am besten zum Raycasten verwendet, wenn Sie **das Controllermodell selbst rendern.** Wenn Sie ein anderes virtuelles Objekt anstelle des Controllers rendern, z. B. ein virtuelles Geschütz, sollten Sie mit einem Strahl zeigen, der für dieses virtuelle Objekt am natürlichsten ist, z. B. ein Strahl, der entlang des Von der App definierten Strahlmodells verläuft. Da Benutzer das virtuelle Objekt und nicht den physischen Controller sehen können, ist das Verweisen auf das virtuelle Objekt wahrscheinlich natürlicher für Benutzer, die Ihre App verwenden.

## <a name="controller-tracking-state"></a>Controllernachverfolgungsstatus

Wie die Headsets erfordert auch der Windows Mixed Reality Motion Controller keine Einrichtung externer Überwachungssensoren. Stattdessen werden die Controller von Sensoren im Headset selbst nachverfolgt.

Wenn der Benutzer die Controller aus dem Ansichtsfeld des Headsets verschiebt, leitet Windows in den meisten Fällen weiterhin Controllerpositionen ab und stellt sie der App zur Verfügung. Wenn der Controller die visuelle Nachverfolgung lange genug verloren hat, werden die Positionen des Controllers auf Positionen mit ungefährer Genauigkeit abgesenkt.

An diesem Punkt sperrt das System den Controller für den Benutzer, verfolgt die Position des Benutzers, während er sich bewegt, während die tatsächliche Ausrichtung des Controllers weiterhin mit seinen internen Ausrichtungssensoren verfügbar ist. Viele Apps, die Controller verwenden, um auf Benutzeroberflächenelemente zu zeigen und diese zu aktivieren, können normal und mit ungefährer Genauigkeit ausgeführt werden, ohne dass der Benutzer darauf hinweist.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/rkDpRllbLII" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### <a name="reasoning-about-tracking-state-explicitly"></a>Explizite Überlegungen zum Nachverfolgungszustand

Apps, die Positionen basierend auf dem Nachverfolgungsstatus unterschiedlich behandeln möchten, können weiter gehen und Eigenschaften für den Zustand des Controllers überprüfen, z. B. SourceLossRisk und PositionAccuracy:

<table>
<tr>
<th> Nachverfolgungsstatus </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>Hohe Genauigkeit</b> </td><td style="background-color: green; color: white"> &lt; 1.0 </td><td style="background-color: green; color: white"> Hoch </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Hohe Genauigkeit (verlustgefahrt)</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: green; color: white"> Hoch </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Ungefähre Genauigkeit</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> Ungefähr </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Keine Position</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> Ungefähr </td><td style="background-color: orange"> false</td>
</tr>
</table>

Diese Bewegungscontroller-Nachverfolgungszustände sind wie folgt definiert:
* **Hohe Genauigkeit:** Während sich der Motion-Controller im Ansichtsfeld des Headsets befindet, bietet er in der Regel basierend auf der visuellen Nachverfolgung positionen mit hoher Genauigkeit. Ein sich bewegender Controller, der vorübergehend das Sichtfeld verlässt oder kurzzeitig von den Headsetsensoren verdeckt wird (z. B. durch die andere Seite des Benutzers), gibt weiterhin eine kurze Zeit lang hochgenaue Posen zurück, basierend auf der trägen Nachverfolgung des Controllers selbst.
* **Hohe Genauigkeit (verlustgefährdete):** Wenn der Benutzer den Motion-Controller hinter den Rand des Ansichtsfelds des Headsets bewegt, kann das Headset die Position des Controllers bald nicht mehr visuell nachverfolgen. Die App weiß, wann der Controller diese FOV-Grenze erreicht hat, indem sie den **SourceLossRisk-Wert** 1.0 erreicht. An diesem Punkt kann die App Controllergesten anhalten, die einen stabilen Stream von hochwertigen Posen erfordern.
* **Ungefähre Genauigkeit:** Wenn der Controller die visuelle Nachverfolgung lange genug verloren hat, werden die Positionen des Controllers auf Positionen mit ungefährer Genauigkeit abgesenkt. An diesem Punkt sperrt das System den Controller für den Benutzer, verfolgt die Position des Benutzers, während er sich bewegt, während die tatsächliche Ausrichtung des Controllers weiterhin mit seinen internen Ausrichtungssensoren verfügbar ist. Viele Apps, die Controller verwenden, um auf Benutzeroberflächenelemente zu zeigen und diese zu aktivieren, können normal und mit ungefährer Genauigkeit ausgeführt werden, ohne dass der Benutzer dies notiert. Apps mit größeren Eingabeanforderungen können diesen Abfall von **Hoher** Genauigkeit zu **Ungefähre** Genauigkeit durch Untersuchen der **PositionAccuracy-Eigenschaft** einsehen, um dem Benutzer z. B. während dieser Zeit einen freundlicheren Hitbox-Wert für Ziele außerhalb des Bildschirms zu geben.
* **Keine Position:** Während der Controller lange Zeit mit ungefährer Genauigkeit arbeiten kann, weiß das System manchmal, dass selbst eine durch Körper gesperrte Position im Moment nicht sinnvoll ist. Beispielsweise wurde ein controller, der aktiviert wurde, möglicherweise nie visuell beobachtet, oder ein Benutzer kann einen Controller abstellen, der dann von einer anderen Person übernommen wird. Zu diesen Zeiten stellt das System keine Position für die App bereit, und **TryGetPosition** gibt FALSE zurück.

## <a name="interactions-low-level-spatial-input"></a>Interaktionen: Räumliche Eingabe auf niedriger Ebene

Die Hauptinteraktionen zwischen Händen und Motion-Controllern sind **Auswählen,** **Menü,** **Greifen,** **Touchpad,** **Thumbstick** und **Home.**
* **Select** ist die primäre Interaktion zum Aktivieren eines Hologramms, das aus einem Pressen gefolgt von einer Veröffentlichung besteht. Für Motion-Controller führen Sie mithilfe des Triggers des Controllers die Option Auswählen aus. Andere Möglichkeiten zum Ausführen einer Select-Anweisung sind das Sprechen des [Sprachbefehls](voice-input.md) "Select". Dieselbe Select-Interaktion kann in jeder App verwendet werden. Stellen Sie sich Auswählen als Entsprechung eines Mausklicks vor. eine universelle Aktion, die Sie einmal lernen und dann auf alle Ihre Apps anwenden.
* **Menu** ist die sekundäre Interaktion für die Aktion auf ein Objekt, die zum Abrufen eines Kontextmenüs oder zum Ergreifen einer anderen sekundären Aktion verwendet wird. Mit Motion-Controllern können Sie über die Menüschaltfläche des Controllers eine *Menüaktion* erstellen. (Das heißt, die Schaltfläche mit dem Hamburger-Symbol "Menü" darauf)
* **Es** wird verstanden, wie Benutzer Direktaktionen für objekte ergreifen können, um sie zu bearbeiten. Mit Motion-Controllern können Sie eine aktionsaufwendigen Aktion durchführen, indem Sie ihre Fist-Gier eng drücken. Ein Motion-Controller kann einen Greif mit einer Greifen-Taste, einem Handflächentrigger oder einem anderen Sensor erkennen.
* **Touchpad** ermöglicht es dem Benutzer, eine Aktion in zwei Dimensionen entlang der Oberfläche des Touchpads eines Motion-Controllers anzupassen und die Aktion zu committen, indem er auf das Touchpad klickt. Touchpads bieten einen gedrückten Zustand, einen berührten Zustand und normalisierte XY-Koordinaten. X und Y reichen von -1 bis 1 über den Bereich des kreisförmigen Touchpads mit einem Mittelpunkt bei (0, 0). Für X befindet sich -1 links und 1 auf der rechten Seite. Für Y befindet sich -1 unten und 1 oben.
* **Mit thumbstick** kann der Benutzer eine Aktion in zwei Dimensionen anpassen, indem er den Fingerabdruck eines Motion-Controllers innerhalb seines Kreisbereichs bewegt und die Aktion durch Klicken auf den Fingerabdruck nach unten committen kann. Thumbsticks bieten auch einen gedrückten Zustand und normalisierte XY-Koordinaten. X und Y reichen von -1 bis 1 über den Bereich des kreisförmigen Touchpads mit einem Mittelpunkt bei (0, 0). Für X befindet sich -1 links und 1 auf der rechten Seite. Für Y befindet sich -1 unten und 1 oben.
* **Home** ist eine spezielle Systemaktion, die verwendet wird, um zum Startmenü zurückzukehren. Dies ähnelt dem Drücken der Windows-Taste auf einer Tastatur oder der Xbox-Taste auf einem Xbox-Controller. Sie können nach Hause wechseln, indem Sie auf einem Motion Controller auf die Schaltfläche Windows klicken. Beachten Sie, dass Sie jederzeit zu Start zurückkehren können, indem Sie "Hey Cortana, Go Home" (Hey Cortana, Go Home) sagen. Apps können nicht speziell auf Home-Aktionen reagieren, da diese vom System verarbeitet werden.

## <a name="composite-gestures-high-level-spatial-input"></a>Zusammengesetzte Gesten: Räumliche Eingabe auf hoher Ebene

Sowohl [Handgesten](gaze-and-commit.md#composite-gestures) als auch Motion-Controller können im Laufe der Zeit nachverfolgt werden, um einen gemeinsamen Satz allgemeiner **[zusammengesetzter Gesten](gaze-and-commit.md#composite-gestures)** zu erkennen. Dadurch kann Ihre App tippen, **halten,** **Bearbeiten** und Navigationsgesten auf hoher **Ebene** erkennen, unabhängig davon, ob Benutzer am Ende Hände oder Controller verwenden. 

## <a name="rendering-the-motion-controller-model"></a>Rendern des Motion Controller-Modells

**3D-Controllermodelle** Windows stellt Apps ein renderbares Modell jedes aktuell im System aktiven Bewegungscontrollers zur Verfügung. Indem Ihre App diese vom System bereitgestellten Controllermodelle zur Laufzeit dynamisch laden und formulieren kann, können Sie sicherstellen, dass Ihre App mit allen zukünftigen Controllerentwürfen kompatibel ist.

Es wird empfohlen, alle renderbaren Modelle mit der **Klammer des** Controllers zu rendern, da der Ursprung des Modells an diesem Punkt in der physischen Welt ausgerichtet ist. Wenn Sie Controllermodelle rendern, können Sie einen Raycast in Ihre Szene von der **Zeigerpose** aus erstellen. Dies stellt den Strahl dar, auf den Benutzer aufgrund des physischen Designs dieses Controllers natürlich zeigen werden.

Weitere Informationen zum dynamischen Laden von Controllermodellen in Unity finden Sie im Abschnitt [Rendern des Motion Controller-Modells in Unity.](../develop/unity/gestures-in-unity.md#rendering-the-motion-controller-model-in-unity)

**2D-Controllerliniengrafik** Es wird zwar empfohlen, Tipps und Befehle für In-App-Controller an die In-App-Controllermodelle selbst anzufügen, einige Entwickler möchten jedoch möglicherweise 2D-Liniengrafikdarstellungen der Motion-Controller in einer flachen "Tutorial"- oder "Anleitungsbenutzeroberfläche" verwenden. Für diese Entwickler haben wir .png Motion Controller Line Art-Dateien in Schwarz und Weiß unten verfügbar gemacht (Rechtsklick zum Speichern).

![Vorschau der Liniengrafik von Motion-Controllern](images/motioncontrollers-black-preview-300px.png)

[Line Art von Motion-Controllern mit voller Auflösung in "'White''"](images/motioncontrollers-white.png)
 
[Line Art von Motion Controllern mit voller Auflösung in "''black''"](images/motioncontrollers-black.png)

## <a name="faq"></a>Häufig gestellte Fragen

### <a name="can-i-pair-motion-controllers-to-multiple-pcs"></a>Kann ich Motion-Controller mit mehreren PCs koppeln?

Motion-Controller unterstützen die Kopplung mit einem einzelnen PC. Befolgen Sie die Anweisungen zum [Einrichten des Motion-Controllers,](motion-controllers.md#setup) um Ihre Controller zu koppeln.

### <a name="how-do-i-update-motion-controller-firmware"></a>Gewusst wie Die Motion Controller-Firmware aktualisieren?

Die Motion Controller-Firmware ist Teil des Headsettreibers und wird bei Bedarf automatisch bei der Verbindung aktualisiert. Firmwareupdates dauern in der Regel 1 bis 2 Minuten, je nach Bluetooth Radio- und Linkqualität. In seltenen Fällen können Controllerfirmwareupdates bis zu 10 Minuten dauern, was auf eine schlechte Bluetooth Konnektivität oder Funkinterferenz hindeuten kann. Informationen zur Behandlung von Konnektivitätsproblemen finden Sie unter Bluetooth bewährten Methoden im Handbuch für [Sehenswürdigkeiten.](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) Nach einem Firmwareupdate werden controller neu gestartet und stellen erneut eine Verbindung mit dem Host-PC her (sie werden feststellen, dass die LEDs für die Nachverfolgung hell sind). Wenn ein Firmwareupdate unterbrochen wird (z. B. wenn die Controller die Stromversorgung verlieren), wird beim nächsten Einschalten der Controller erneut versucht.

### <a name="how-i-can-check-battery-level"></a>Wie kann ich den Akkustand überprüfen?

Im Windows Mixed Reality [können](../discover/navigating-the-windows-mixed-reality-home.md)Sie ihren Controller umdrehen, um den Akkustand auf der umgekehrten Seite des virtuellen Modells zu sehen. Es gibt keinen Indikator für den physischen Akkustand.

### <a name="can-you-use-these-controllers-without-a-headset-just-for-the-joysticktriggeretc-input"></a>Können Sie diese Controller ohne Headset verwenden? Nur für die Eingabe "10/trigger/etc"?

Nicht für universelle Windows Anwendungen.

## <a name="troubleshooting"></a>Problembehandlung

Weitere Informationen [finden Sie unter Problembehandlung bei Bewegungscontrollern](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers) im Handbuch für Fans.

## <a name="filing-motion-controller-feedbackbugs"></a>Einreichen von Feedback/Fehlern für den Motion Controller

[Senden Sie uns](/hololens/hololens-feedback) feedback in Feedback-Hub mithilfe der Kategorie "Mixed Reality -> Input".

## <a name="see-also"></a>Siehe auch

* [Motion-Controller in Unity](../develop/unity/motion-controllers-in-unity.md)
* [Hände und Motion-Controller in DirectX](../develop/native/hands-and-motion-controllers-in-directx.md)
* [Gesten](gaze-and-commit.md#composite-gestures)
* [Handbuch für Fans: Ihr Windows Mixed Reality Zu Hause](/windows/mixed-reality/enthusiast-guide/your-mixed-reality-home)
* [Handbuch für Fans: Verwenden von Spielen & Apps in Windows Mixed Reality](/windows/mixed-reality/enthusiast-guide/using-games-and-apps-in-windows-mixed-reality)
* [Funktionsweise von Inside-Out-Tracking](/windows/mixed-reality/enthusiast-guide/tracking-system)