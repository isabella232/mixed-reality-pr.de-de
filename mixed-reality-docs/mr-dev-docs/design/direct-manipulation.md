---
title: Direkte Manipulation mit den Händen
description: Erfahren Sie mehr über direkte Manipulation, ein Eingabemodell, bei dem Benutzer Hologramme direkt mit den Händen berühren.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, Anvisieren, Zielen per Anvisieren, Interaktion, Design, Eingabe, Hände nah beieinander, HoloLens, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, MRTK, Mixed Reality Toolkit, Taste, Collider, Begrenzungsrahmen, 2D, instinktive Gesten
ms.openlocfilehash: 8316452b8308e159612a81d097c352cf1d935362
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2021
ms.locfileid: "101759322"
---
# <a name="direct-manipulation-with-hands"></a>Direkte Manipulation mit den Händen

![Schaltfläche](images/UX_Hero_Manipulation.jpg)

Die direkte Manipulation ist ein Eingabemodell, bei dem Hologramme direkt mit den Händen berührt werden. Die Idee hinter diesem Konzept ist, dass sich Objekte wie in der realen Welt verhalten. Schaltflächen können einfach durch Drücken aktiviert werden, Objekte können durch Greifen aufgenommen werden und 2D-Inhalte verhalten sich wie ein virtueller Touchscreen. Die direkte Manipulation ist angebotsbasiert, d. h. benutzerfreundlich. Es gibt keine symbolischen Gesten, die den Benutzern vermittelt werden müssen. Alle Interaktionen basieren auf einem visuellen Element, das Sie berühren oder greifen können. Sie gilt als „nahes“ Eingabemodell, d. h. es wird am besten für die Interaktion mit Inhalten verwendet, die innerhalb der Reichweite der Arme liegen.

## <a name="device-support"></a>Geräteunterstützung

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><strong>Eingabemodell</strong></td>
     <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1. Generation)</strong></a></td>
     <td><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></td>
     <td><a href="/windows/mixed-reality/immersive-headset-hardware-details"><strong>Immersive Headsets</strong></a></td>
</tr>
<tr>
     <td>Direkte Manipulation mit den Händen</td>
     <td>❌ Nicht unterstützt</td>
     <td>✔️ Empfohlen</td>
     <td>➕ Unterstützt.  Für die Benutzeroberfläche empfehlen wir stattdessen <a href="point-and-commit.md">Zeigen und Ausführen mit den Händen</a>.</td>
    
</tr>
</table>


Die direkte Manipulation ist ein primäres Eingabemodell für HoloLens 2 und nutzt das neue artikulierte Handtracking-System. Das Eingabemodell ist auch bei immersiven Headsets über Motion-Controller verfügbar, wird aber nicht als primäre Möglichkeit zur Interaktion außerhalb der Objektmanipulation empfohlen. Die direkte Manipulation ist bei HoloLens (1. Generation) nicht verfügbar.

<br>

---

## <a name="collidable-fingertip"></a>Kollisionsfähige Fingerspitze

Bei HoloLens 2 werden die Hände des Benutzers als Skelettmodelle der linken und rechten Hand erkannt und interpretiert. Um die Idee, Hologramme direkt mit den Händen zu berühren, zu implementieren, könnten idealerweise fünf Collider an fünf Fingerspitzen der einzelnen Handskelettmodelle angefügt werden. Aufgrund der fehlenden taktilen Rückmeldung können jedoch 10 kollisionsfähige Fingerspitzen unerwartete und unvorhersehbare Kollisionen mit Hologrammen verursachen. 

Wir empfehlen, nur einen Collider an jedem Zeigefinger anzufügen. Die kollisionsfähigen Zeigefingerspitzen können trotzdem als aktive Berührungspunkte für verschiedene Touchgesten dienen, die andere Finger einbeziehen. Zu den Touchgesten gehören das Drücken mit einem Finger, das Tippen mit einem Finger, das Drücken mit zwei Fingern und das Drücken mit fünf Fingern, wie unten dargestellt:

:::row:::
    :::column:::
       ![Kollisionsfähige Fingerspitze](images/Collidable-Fingertip.jpg)<br>
       **Kollisionsfähige Fingerspitze**<br>
    :::column-end:::
    :::column:::
       ![Drücken mit einem Finger](images/Collidable-Fingertip-1-finger-press.jpg)<br>
        **Drücken mit einem Finger**<br>
    :::column-end:::
    :::column:::
       ![Tippen mit einem Finger](images/Collidable-Fingertip-1-finger-tap.jpg)<br>
       **Tippen mit einem Finger**<br>
    :::column-end:::
    :::column:::
       ![Drücken mit fünf Fingern](images/Collidable-Fingertip-5-finger-press.jpg)<br>
       **Drücken mit fünf Fingern**<br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="sphere-collider"></a>Kugel-Collider

Anstelle einer zufälligen generischen Form wird empfohlen, einen Kugel-Collider zu verwenden. Anschließend können Sie diesen visuell rendern, um bessere Hinweise für die Zielbestimmung im Nahbereich zu bieten. Der Durchmesser der Kugel muss der Dicke des Zeigefingers entsprechen, um die Genauigkeit bei der Toucheingabe zu erhöhen. Die Variable für die Fingerdicke lässt sich durch den Aufruf der Hand-API einfacher abrufen.

### <a name="fingertip-cursor"></a>Fingerspitzencursor

Zusätzlich zum Rendern einer kollisionsfähigen Kugel an der Zeigefingerspitze haben wir einen erweiterten Fingerspitzencursor entwickelt, um ein besseres Erlebnis bei der Bestimmung nahegelegener Ziele zu erreichen. Es handelt sich um einen ringförmigen Cursor, der an der Zeigefingerspitze angebracht ist. Entsprechend der Nähe reagiert er hinsichtlich Ausrichtung und Größe dynamisch auf ein Ziel, wie unten beschrieben:

* Wenn sich ein Zeigefinger auf ein Hologramm zubewegt, befindet sich der Cursor immer parallel zur Oberfläche des Hologramms und verkleinert seine Größe.
* Sobald der Finger die Oberfläche berührt, schrumpft der Cursor zu einem Punkt und gibt ein Toucheingabeereignis aus.

Mit interaktiven Feedback können Benutzer eine hohe Genauigkeit bei Aufgaben zur Zielbestimmung im Nahbereich erreichen, z. B. das Auslösen eines Hyperlinks oder das Drücken einer Schaltfläche, wie nachfolgend veranschaulicht. 

:::row:::
    :::column:::
       ![Fingerspitzencursor – fern](images/Fingertip-cursor-far.jpg)<br>
       **Fingerspitzencursor – fern**<br>
    :::column-end:::
    :::column:::
       ![Fingerspitzencursor – nah](images/Fingertip-cursor-near.jpg)<br>
        **Fingerspitzencursor – nah**<br>
    :::column-end:::
    :::column:::
       ![Fingerspitzencursor – Kontakt](images/Fingertip-cursor-contact.jpg)<br>
       **Fingerspitzencursor – Kontakt**<br>
    :::column-end:::
:::row-end:::

<br>



## <a name="bounding-box-with-proximity-shader"></a>Begrenzungsrahmen mit Näherungsshader

Das Hologramm selbst erfordert auch die Fähigkeit, sowohl visuelles als auch akustisches Feedback zu liefern, um den Mangel an taktilem Feedback auszugleichen. Dazu erstellen wir das Konzept eines Begrenzungsrahmens mit einem Näherungsshader. Ein Begrenzungsrahmen ist ein minimaler volumetrischer Bereich, der ein 3D-Objekt umgibt. Der Begrenzungsrahmen verfügt über einen interaktiven Renderingmechanismus, der als Näherungsshader bezeichnet wird. Der Näherungsshader verhält sich wie folgt:

:::row:::
    :::column:::
       ![Hover (fern) mit visuellem Feedback](images/bounding-box-with-proximity-shader-hover-far.jpg)<br>
       **Hover (fern)**<br>
       Wenn sich der Zeigefinger innerhalb eines Bereichs befindet, wird ein Fingerspitzenspotlight auf die Oberfläche des Begrenzungsrahmens gerichtet.
    :::column-end:::
    :::column:::
       ![Hover (nah) mit visuellem Feedback](images/bounding-box-with-proximity-shader-hover-near.jpg)<br>
        **Hover (nah)**<br>
        Wenn sich die Fingerspitze der Oberfläche nähert, schrumpft das Spotlight.
    :::column-end:::
    :::column:::
       ![Kontakt beginnt](images/bounding-box-with-proximity-shader-begin-contact.jpg)<br>
       **Kontakt beginnt**<br>
       Sobald die Fingerspitze die Oberfläche berührt, wechselt der gesamte Begrenzungsrahmen die Farbe oder erzeugt einen visuellen Effekt, um den Toucheingabezustand zu reflektieren.
    :::column-end:::
    :::column:::
       ![Kontakt endet](images/bounding-box-with-proximity-shader-end-contact.jpg)<br>
       **Kontakt endet**<br>
       Es kann auch ein Soundeffekt aktiviert werden, um das visuelle Feedback der Toucheingabe zu verbessern.
    :::column-end:::
:::row-end:::

<br>

---

## <a name="pressable-button"></a>Drückbare Schaltfläche

Mit einer kollisionsfähigen Fingerspitze sind die Benutzer jetzt bereit, mit einer grundlegenden holografischen Benutzeroberflächenkomponente, z. B. einer drückbaren Schaltfläche, zu interagieren. Eine drückbare Schaltfläche ist eine holografische Schaltfläche, die auf einen direkten Fingerdruck angepasst ist. Da es an taktilem Feedback mangelt, setzt eine drückbare Schaltfläche wiederum einige Mechanismen ein, um auf dem taktilen Feedback basierende Probleme zu beheben.

* Der erste Mechanismus ist ein Begrenzungsrahmen mit einem Näherungsshader, wie er im vorherigen Abschnitt beschrieben wurde. Er vermittelt Benutzern ein besseres Gefühl von Nähe, wenn sie sich einer Schaltfläche nähern und mit ihr Kontakt aufnehmen können.
* Der zweite Mechanismus ist die Absenkung. Absenkung erzeugt ein Gefühl des Niederdrückens, nachdem eine Fingerspitze die Schaltfläche berührt hat. Der Mechanismus stellt sicher, dass sich die Schaltfläche mit der Fingerspitze eng entlang der Tiefenachse bewegt. Die Schaltfläche kann ausgelöst werden, wenn sie eine gewählte Tiefe erreicht (beim Drücken) oder die Tiefe wieder verlässt (beim Loslassen), nachdem sie passiert wurde.
* Der Soundeffekt sollte hinzugefügt werden, um das Feedback zu verbessern, wenn die Schaltfläche ausgelöst wird.

:::row:::
    :::column:::
       ![Drückbare Schaltfläche – fern](images/pressable-button-far.jpg)<br>
       **Finger ist weit entfernt**<br>
    :::column-end:::
    :::column:::
       ![Drückbare Schaltfläche – nah](images/pressable-button-approach.jpg)<br>
        **Finger nähert sich**<br>
    :::column-end:::
    :::column:::
       ![Drückbare Schaltfläche – Kontakt beginnt](images/pressable-button-contact.jpg)<br>
       **Kontakt beginnt**<br>
    :::column-end:::
    :::column:::
       ![Drückbare Schaltfläche – Drücken](images/pressable-button-press.jpg)<br>
       **Nach unten drücken**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a>2D-Tafel – Interaktion

Eine 2D-[Tafel](slate.md) ist ein holografischer Container, der zum Hosten von 2D-App-Inhalten verwendet wird (z. B. ein Webbrowser). Das Konzept für die Interaktion mit einer 2D-Tafel durch direkte Manipulation ist das gleiche wie für die Interaktion mit einem physischen Touchscreen.

### <a name="to-interact-with-the-slate-contact"></a>So interagieren Sie mit dem Tafelkontakt

:::row:::
    :::column:::
       ![Toucheingabe](images/2d-slate-interaction-touch.jpg)<br>
       **Toucheingabe**<br>
       Verwenden Sie einen Zeigefinger, um einen Link oder eine Schaltfläche zu drücken.
    :::column-end:::
    :::column:::
       ![Scrollen](images/2d-slate-interaction-scroll2.jpg)<br>
        **Scrollen**<br>
        Verwenden Sie einen Zeigefinger, um einen Tafelinhalt nach oben und unten zu scrollen.
    :::column-end:::
    :::column:::
       ![Zoomen](images/2d-slate-interaction-zoom2.jpg)<br>
       **Zoomen**<br>
       Die zwei Zeigefinger des Benutzers werden verwendet, um den Tafelinhalt entsprechend der relativen Bewegung der Finger zu vergrößern oder zu verkleinern.
    :::column-end:::
:::row-end:::


### <a name="for-manipulating-the-2d-slate-itself"></a>So bearbeiten Sie die eigentliche 2D-Tafel

:::row:::
    :::column:::
       ![Grafik mit der Darstellung des Features zum Greifen und Ziehen](images/manipulate-2d-slate-move.jpg)<br>
       **Verschieben**<br>
       Bewegen Sie Ihre Hände in Richtung von Ecken und Kanten, um die nächstgelegenen Manipulationsangebote zu enthüllen. Greifen Sie die Hololeiste im oberen Bereich der 2D-Tafel, mit der Sie die gesamte Tafel verschieben können.
    :::column-end:::
    :::column:::
       ![Grafik mit Darstellung der Skalierungsfunktion](images/manipulate-2d-slate-scale.jpg)<br>
        **Skalierung**<br>
        Greifen Sie die Manipulationsangebote, und führen Sie über die Eckenangebote eine einheitliche Skalierung aus.
    :::column-end:::
    :::column:::
       ![Neuanordnen](images/manipulate-2d-slate-reflow.jpg)<br>
       **Neuanordnen**<br>
       Greifen Sie die Manipulationsangebote, und führen Sie über die Eckenangebote die Neuanordnung aus.
    :::column-end:::
:::row-end:::

<br>

---


## <a name="3d-object-manipulation"></a>3D-Objektbearbeitung

Bei HoloLens 2 können Benutzer ihre Hände in die Lage versetzen, holografische 3D-Objekte zu steuern und zu bearbeiten, indem sie auf die einzelnen 3D-Objekte einen Begrenzungsrahmen anwenden. Der Begrenzungsrahmen sorgt durch seinen Näherungsshader für eine bessere Tiefenwahrnehmung. Mit dem Begrenzungsrahmen gibt es zwei Konstruktionsansätze für die 3D-Objektbearbeitung.

### <a name="affordance-based-manipulation"></a>Angebotsbasierte Bearbeitung

Angebotsbasierte Bearbeitung gestattet es Ihnen, das 3D-Objekt durch einen Begrenzungsrahmen zusammen mit dem diesen umgebenden Bearbeitungsangeboten zu manipulieren. 

:::row:::
    :::column:::
       ![Grafik mit der Darstellung von Begrenzungsrahmen und Verschiebefeature eines Objekts](images/3d-object-manipulation-move.jpg)<br>
       **Verschieben**<br>
       Sobald sich die Hand eines Benutzers in der Nähe eines 3D-Objekts befindet, werden der Begrenzungsrahmen und das nächstgelegene Angebot angezeigt. Benutzer können den Begrenzungsrahmen greifen, um das gesamte Objekt zu verschieben.
    :::column-end:::
    :::column:::
       ![Grafik mit der Darstellung eines Benutzers, der die Kante eines Objekts greift, um es zu drehen](images/3d-object-manipulation-rotate.jpg)<br>
        **Drehen**<br>
        Benutzer können zum Drehen die Eckenangebote greifen.
    :::column-end:::
    :::column:::
       ![Grafik mit der Darstellung eines Benutzers, der die Ecke eines Objekts greift, um es zu skalieren](images/3d-object-manipulation-scale.jpg)<br>
       **Skalierung**<br>
       Benutzer können die Eckenangebote greifen, um eine einheitliche Skalierung auszuführen.
    :::column-end:::
:::row-end:::

<br>


### <a name="non-affordance-based-manipulation"></a>Bearbeitung ohne Angebot

Bei der Bearbeitung ohne Angebot werden dem Begrenzungsrahmen keine Angebote angefügt. Benutzer können den Begrenzungsrahmen nur anzeigen und dann direkt mit ihm interagieren. Wenn der Begrenzungsrahmen mit einer Hand gegriffen wird, sind Verschiebung und Drehung des Objekts der Bewegung und Ausrichtung der Hand zugeordnet. Wenn das Objekt mit zwei Händen gegriffen wird, kann der Benutzer Verschiebung, Drehung und Skalierung entsprechend der relativen Bewegung der beiden Hände vornehmen.

Bestimmte Bearbeitungen erfordern Präzision. Wir empfehlen, dass Sie **angebotsbasierter Bearbeitung** verwenden, da sie ein hohes Maß an Granularität bietet. Für eine flexible Bearbeitung empfehlen wir Ihnen, **eine angebotsfreie Bearbeitung** zu verwenden, da sie sofortige und spielerische Umgebungen ermöglicht.

<br>

---


## <a name="instinctual-gestures"></a>Instinktive Gesten

Mit HoloLens (1. Generation) haben wir den Benutzern eine Reihe vordefinierter Gesten vermittelt, z. B. „Öffnen“ und „In die Luft tippen“. Bei HoloLens 2 werden die Benutzer nicht aufgefordert, sich symbolische Gesten zu merken. Alle erforderlichen Benutzergesten, mit denen der Benutzer mit Hologrammen und Inhalten interagieren muss, sind instinktiv. Um instinktive Gesten zu erreichen, müssen Benutzer durch den Entwurf von Benutzeroberflächenangeboten dazu angeleitet werden, Gesten auszuführen.

Wenn wir den Benutzer z. B. bestärken, ein Objekt oder einen Kontrollpunkt durch Zusammenführen von zwei Fingern zu greifen, sollte das Objekt oder der Kontrollpunkt klein sein. Wenn wir möchten, dass der Benutzer mit fünf Fingern greift, sollte das Objekt oder der Kontrollpunkt relativ groß sein. Ähnlich wie bei Tasten schränkt eine kleine Taste Benutzer darauf ein, sie mit einem einzelnen Finger zu drücken. Eine große Taste ermutigt Benutzer, sie mit der Handfläche zu drücken.


:::row:::
    :::column:::
       ![Grafik, die einen Benutzer zeigt, der ein kleines Objekt greift, um es zu bewegen](images/instinctual-gestures-smallobject.jpg)<br>
       **Kleines Objekt**<br>
    :::column-end:::
    :::column:::
       ![Grafik, die einen Benutzer zeigt, der ein mittelgroßes Objekt greift, um es zu bewegen](images/instinctual-gestures-mediumobject.jpg)<br>
        **Mittelgroßes Objekt**<br>
    :::column-end:::
    :::column:::
       ![Grafik, die einen Benutzer zeigt, der ein großes Objekt greift, um es zu bewegen](images/instinctual-gestures-largeobject.jpg)<br>
       **Großes Objekt**<br>
    :::column-end:::
:::row-end:::


<br>

---

<br>

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a>Symmetrisches Design zwischen Händen und Controllern mit 6 Freiheitsgraden

Sie haben vielleicht bemerkt, dass es Interaktionsparallelen gibt, die wir zwischen Händen in AR und Motion-Controllern in VR ziehen können. Beide Eingabemethoden können verwendet werden, um direkte Bearbeitungen in ihrer jeweiligen Umgebung auszulösen. In HoloLens 2 funktioniert das Greifen und Ziehen mit den Händen aus nächster Nähe weitgehend so, wie die Taste zum Greifen an den WMR-Motion-Controllern. Dies bietet den Benutzern die vertraute Interaktion zwischen den beiden Plattformen, die sich als nützlich erweisen kann, falls Sie sich jemals dazu entscheiden, Ihre Anwendung zwischen den Plattformen zu portieren.

<br>

---

## <a name="optimize-with-eye-tracking"></a>Optimieren mit Eyetracking

Direkte Bearbeitung kann sich magisch anfühlen, wenn sie wie beabsichtigt funktioniert. Sie kann aber auch zu Enttäuschungen führen, wenn Sie Ihre Hand nicht mehr bewegen können, ohne unbeabsichtigt ein Hologramm zu aktivieren. Das Eyetracking hilft potenziell, die Absicht des Benutzers besser zu erkennen.

* **Wann**: Reduzieren der unbeabsichtigten Auslösung einer Bearbeitungsreaktion. Das Eyetracking ermöglicht ein besseres Verständnis dafür, womit sich ein Benutzer gerade beschäftigt.
Stellen Sie sich z. B. vor, Sie lesen einen holografischen Text (mit Anweisungen) durch, wenn Sie rübergreifen, um Ihr reales Arbeitsgerät aufzunehmen.

Dabei bewegen Sie Ihre Hand versehentlich über einige interaktive holografische Schaltflächen, die Sie vorher noch nicht einmal bemerkt haben. Beispielsweise lagen sie möglicherweise außerhalb des Sichtfelds des Benutzers.

Wenn der Benutzer ein Hologramm eine Weile nicht betrachtet hat, aber ein Toucheingabe- oder Greifereignis dafür erkannt wurde, ist die Interaktion wahrscheinlich nicht beabsichtigt.

* **Welche**:  Abgesehen von der Behandlung falsch positiver Aktivierungen umfasst ein weiteres Beispiel die bessere Identifizierung, welche Hologramme zu greifen oder zu drücken sind, da der genaue Schnittpunkt aus Ihrer Sicht möglicherweise nicht eindeutig ist, insbesondere wenn mehrere Hologramme nahe beieinander positioniert sind.

  Während das Eyetracking bei HoloLens 2 Einschränkungen aufweisen kann, wie genau es Ihr Anvisieren mit dem Kopf bestimmen kann, ist dies bei nahen Interaktionen aufgrund von Tiefenunterschieden bei der Interaktion mit der Handeingabe möglicherweise hilfreich. Das bedeutet, dass es manchmal schwierig ist, festzustellen, ob sich Ihre Hand hinter oder vor einem Hologramm befindet, um z. B. ein Widget für die Bearbeitung präzise zu greifen.

* **Wohin**: Verwenden Sie Informationen darüber, was sich ein Benutzer ansieht, mit schnell auslösenden Gesten. Greifen Sie ein Hologramm, und werfen Sie es grob in Richtung Ihres beabsichtigten Ziels.  

    Obwohl dies manchmal funktioniert, können schnell ausgeführte Handgesten zu sehr ungenauen Zielen führen. Das Eyetracking (Blickverfolgung) könnte die Genauigkeit der Geste verbessern.

<br>

---

## <a name="manipulation-in-mrtk-mixed-reality-toolkit-for-unity"></a>Bearbeitung im MRTK (Mixed Reality Toolkit) für Unity
Mit dem **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** können Sie mithilfe des Skripts **ObjectManipulator** ganz einfach ein gängiges Bearbeitungsverhalten erzielen. Mit ObjectManipulator können Sie Objekte direkt mit der Hand oder dem Handlichtstrahl greifen und verschieben. Außerdem wird die Bearbeitung mit beiden Händen zum Skalieren und Rotieren eines Objekts unterstützt.

* [MRTK – Bearbeitung](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/object-manipulator.md)

---

## <a name="see-also"></a>Siehe auch

* [Anvisieren mit dem Kopf und Ausführen](gaze-and-commit.md)
* [Zeigen und Ausführen mit den Händen](point-and-commit.md)
* [Instinktive Interaktionen](interaction-fundamentals.md)