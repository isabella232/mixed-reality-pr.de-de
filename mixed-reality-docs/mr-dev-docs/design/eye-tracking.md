---
title: Eyetracking – Blickverfolgung
description: Erfahren Sie mehr über eye tracking for HoloLens 2 und die neuen Ebenen des menschlichen Verständnisses, wenn es holografische Erfahrungen bietet.
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
keywords: Eyetracking, Mixed Reality, Eingabe, Anvieren mit den Augen, Kalibrierung, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit, Absicht, Aktionen
ms.openlocfilehash: b76fd2e05999e5807156714fcdf12ca2863501bc
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196505"
---
# <a name="eye-tracking-on-hololens-2"></a>Blickverfolgung auf HoloLens 2

![Eyetracking-Demo in MRTK](images/mrtk_et_scenemenu.jpg)

HoloLens 2 ermöglicht ein neues Maß an Kontext und menschlichem Verständnis innerhalb der holografischen Benutzeroberfläche, indem Entwicklern die Möglichkeit zur Verfügung steht, Informationen dazu zu verwenden, was der Benutzer betrachtet. Auf dieser Seite wird erläutert, wie Entwickler von der Eyetracking für verschiedene Anwendungsfälle profitieren können und worauf sie beim Entwerfen von Benutzerinteraktionen achten müssen, die auf anvingerten Blicken basieren. 

Die Eyetracking-API wurde mit Blick auf den Datenschutz eines Benutzers entwickelt und vermeidet die Übergabe identifizierbarer Informationen, insbesondere biometrischer Daten. Für Eyetracking-fähige Anwendungen muss der Benutzer der App die Berechtigung zum Verwenden von Eyetrackinginformationen erteilen.

### <a name="device-support"></a>Geräteunterstützung

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

<br>

## <a name="head-and-eye-tracking-design-concepts-demo"></a>Demo zu Designkonzepten für Kopf- und Blickverfolgung

Wenn Sie Designkonzepte für Kopf- und Blickverfolgung in Aktion sehen möchten, sehen Sie sich die Videodemo **Designing Holograms - Head Tracking and Eye Tracking** (Entwerfen von Hologrammen – Kopfverfolgung und Eyetracking) weiter unten an. Wenn Sie fertig sind, fahren Sie fort, um ausführlichere Informationen zu bestimmten Themen zu erhalten.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

*Dieses Video wurde aus der App "Entwerfen von Hologrammen" HoloLens 2 aufgenommen. Laden Sie hier herunter, und profitieren Sie [von der vollständigen Erfahrung.](https://aka.ms/dhapp)*

## <a name="calibration"></a>Kalibrierung 

Damit eye tracking richtig funktioniert, muss jeder Benutzer [](/hololens/hololens-calibration) eine Eyetracking-Benutzer kalibrieren, für die der Benutzer einen Satz holografischer Ziele betrachten muss. Auf diese Weise kann das Gerät das System für eine komfortablere und qualitativ hochwertigere Anzeige anpassen und gleichzeitig eine genaue Blickverfolgung sicherstellen. 

Eyetracking sollte für die meisten Benutzer funktionieren, aber es gibt selten Fälle, in denen ein Benutzer nicht erfolgreich kalibrieren kann. Die Kalibrierung kann aus verschiedenen Gründen fehlschlagen, einschließlich, aber nicht beschränkt auf: 
* Der Benutzer hat sich zuvor vom Kalibrierungsprozess abgemeldet.
* Der Benutzer wurde ablenkend und hat die Kalibrierungsziele nicht befolgt.
* Der Benutzer verfügt über bestimmte Arten von Kontaktobjektiven und Brillen, die das System noch nicht unterstützt. 
* Der Benutzer hat bestimmte Augen- oder Augenbedingungen oder hatte Augenaussichten, die das System noch nicht unterstützt.  
* Externe Faktoren, die eine zuverlässige Blickverfolgung verhindern, z. B. Verblendungen auf dem HoloLens-Visier oder der Brille, intensive direkte Brillen und Verdeckungen durch Diebe vor den Augen

Entwickler sollten sicherstellen, dass sie eine angemessene Unterstützung für Benutzer bereitstellen, für die eye tracking-Daten möglicherweise nicht verfügbar sind (die nicht in der Lage sind, erfolgreich zu kalibrieren). Im Abschnitt am unteren Rand dieser Seite haben wir Empfehlungen für Fallbacklösungen bereitgestellt. 

Weitere Informationen zur Kalibrierung und zur Sicherstellung eines reibungslosen Ablaufs finden Sie auf unserer Seite zur Kalibrierung von [Eyetrackingbenutzern.](/hololens/hololens-calibration)

<br>

## <a name="available-eye-tracking-data"></a>Verfügbare Eyetrackingdaten

Bevor wir uns mit bestimmten Anwendungsfällen für die Eingabe von Anverfolgen mit den Augen nähern, möchten wir kurz auf die Funktionen hinweisen, die die HoloLens 2 [Eye Tracking-API](/uwp/api/windows.perception.people.eyespose) bietet. Entwickler erhalten Bei ca. _30 FPS (30 Hz)_ Zugriff auf einen einzelnen Anviert-Strahl mit den Augen (Ursprung und Richtung des Anvierens).
Ausführlichere Informationen zum Zugriff auf Eyetrackingdaten finden Sie in unseren Entwicklerhandbüchern zum Verwenden des [Anvierens mit](../develop/native/gaze-in-directx.md) den Augen in DirectX und [zum Anvieren mit den Augen in Unity.](https://aka.ms/mrtk-eyes)

Das vorhergesagte Anvieren mit den Augen liegt ungefähr innerhalb von 1,5 Grad im visuellen Winkel um das tatsächliche Ziel (siehe abbildung unten). Da geringfügige Ungenauigkeiten erwartet werden, sollten Entwickler einen Gewissensrand um diesen unteren Grenzwert planen (z.B. können 2,0 bis 3,0 Grad zu einer viel komfortableren Erfahrung führen). Im Folgenden erfahren Sie, wie Sie die Auswahl kleiner Ziele genauer behandeln. Damit die Blickverfolgung exakt funktioniert, muss jeder Benutzer eine Benutzerkalibrierung für seine Blickverfolgung durchlaufen. 

![Optimale Zielgröße im Abstand von 2 Metern](images/gazetargeting-size-1000px.jpg)<br>
*Optimale Zielgröße in einer Entfernung von 2 Metern*

<br>

## <a name="use-cases"></a>Anwendungsfälle

Mit der Blickverfolgung können Anwendungen in Echtzeit verfolgen, wohin der Benutzer schaut. In den folgenden Anwendungsfällen werden einige Interaktionen beschrieben, die mit eye tracking auf HoloLens 2 in Mixed Reality möglich sind.
Diese Anwendungsfälle sind noch nicht Teil der Holographic Shell-Benutzeroberfläche (d. h. der Schnittstelle, die Sie beim Starten Ihrer Anwendung HoloLens 2).
Sie können einige davon im [Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html)ausprobieren, das mehrere interessante und leistungsstarke Beispiele für die Verwendung von Eyetracking bietet, z. B. schnelle und mühelose, durch die Augen unterstützte Zielauswahl und automatisches Scrollen durch Text basierend auf dem, was der Benutzer betrachtet. 

### <a name="user-intent"></a>Benutzerabsicht

Informationen darüber, wo und was ein Benutzer betrachtet, bieten einen leistungsstarken Kontext für andere Eingaben, z. B. Stimme, Hände und Controller.
Dies kann für verschiedene Aufgaben verwendet werden.
Dies kann z. B.  von der schnellen und mühelosen Ausrichtung auf die gesamte Szene reichen, indem ein Hologramm betrachtet wird und *"Auswählen"* (siehe auch Anvieren und [Commit)](gaze-and-commit.md)oder *"Put this..."* gesagt wird, dann der Blick auf den Ort, an dem der Benutzer das Hologramm platzieren möchte, und *"... there" auf.* Beispiele hierfür finden Sie in den Artikeln [Mixed Reality Toolkit – Eye-supported Target Selection](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) (Mixed Reality-Toolkit – Blickgestützte Zielauswahl) und [Mixed Reality Toolkit – Eye-supported Target Positioning](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Positioning.html) (Mixed Reality-Toolkit – Blickgestützte Zielpositionierung).

Darüber hinaus kann ein Beispiel für die Benutzerabsicht die Verwendung von Informationen darüber enthalten, was Benutzer betrachten, um die Interaktion mit verfachten virtuellen Agents und interaktiven Hologrammen zu verbessern. Beispielsweise können virtuelle Agents verfügbare Optionen und ihr Verhalten basierend auf aktuell angezeigten Inhalten anpassen. 

### <a name="implicit-actions"></a>Implizite Aktionen

Die Kategorie der impliziten Aktionen steht in enger Beziehung zur Benutzerabsicht.
Die Idee ist, dass Hologramme oder Benutzeroberflächenelemente auf instinktive Weise reagieren, die sich möglicherweise nicht einmal so anfühlt, als ob der Benutzer mit dem System interagiert, sondern dass das System und der Benutzer synchron sind. Ein Beispiel  hierfür ist die automatische Bildlauf-Funktion, bei der der Benutzer einen langen Text lesen kann, der automatisch beginnt, zu scrollen, sobald der Benutzer zum Ende des Textfelds kommt, um den Benutzer im Lesefluss zu halten, ohne einen Finger zu heben.  
Ein wichtiger Aspekt dabei ist, dass sich die Bildlaufgeschwindigkeit an die Lesegeschwindigkeit des Benutzers anpasst.
Ein weiteres Beispiel ist **der mit** den Augen unterstützte Zoom und Schwenken, bei dem der Benutzer genau das sehen kann, worauf er sich konzentriert. Das Auslösen und Steuern der Zoomgeschwindigkeit kann durch Spracheingaben oder Handeingaben gesteuert werden. Dies ist wichtig, um dem Benutzer das Gefühl der Kontrolle zu geben und gleichzeitig eine Überlastung zu vermeiden. Im Folgenden werden diese Entwurfsüberlegungen ausführlicher erläutert. Nach dem Vergrößern kann der Benutzer problemlos dem Lauf einer Straße folgen, um seine Umgebung mithilfe des Anvierens mit den Augen zu erkunden.
Demobeispiele für diese Arten von Interaktion finden Sie im Beispiel [Mixed Reality Toolkit – Eye-supported Navigation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) (Mixed Reality-Toolkit – Blickgestützte Navigation).

Andere Anwendungsfälle für _implizite Aktionen_ können Folgendes umfassen:
- **Intelligente Benachrichtigungen:** Haben Sie sich jemals darüber geärgert, dass Benachrichtigungen genau dort angezeigt werden, wo Sie suchen? Unter Berücksichtigung der Aufmerksamkeit, auf die ein Benutzer achten muss, können Sie diese Erfahrung verbessern, indem Sie Benachrichtigungen von dem Ort abstellen, an dem der Benutzer gerade arbeitet. Dies schränkt Ablenkungen ein und schließt sie automatisch, sobald der Benutzer das Lesen abgeschlossen hat. 
- **Hologramme:** Hologramme, die beim Anvieren unaufdinglich reagieren. Dies kann von leicht leuchtenden UI-Elementen, einer langsamen Blume bis hin zu einem virtuellen Hund reichen, der mit dem Blick auf den Benutzer beginnt und sein Ende wackelt. Diese Interaktion kann ein interessantes Gefühl für Konnektivität und Zufriedenheit in Ihrer Anwendung bieten.

### <a name="attention-tracking"></a>Aufmerksamkeitsverfolgung

Informationen dazu, wo oder was Benutzer betrachten, können ein äußerst leistungsfähiges Tool sein. Sie kann dabei helfen, die Nutzbarkeit von Entwürfen zu bewerten und Probleme in Workflows zu identifizieren, um sie effizienter zu gestalten.
Eyetrackingvisualisierung und -analyse sind eine gängige Praxis in verschiedenen Anwendungsbereiche. Mit HoloLens 2 bieten wir diesem Verständnis eine neue Dimension, da 3D-Hologramme in realen Kontexten platziert und entsprechend bewertet werden können. Das [Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html) enthält grundlegende Beispiele für das Protokollieren und Laden von Eyetrackingdaten und deren Visualisierung.
Microsoft ist bestrebt, Innovationen zu fördern und gleichzeitig sicherzustellen, dass Benutzer über eine informierte und transparente Erfahrung mit der Verwendung ihrer Eyetrackinginformationen verfügen.  Wir arbeiten mit unseren Entwicklern und UX-Teams zusammen, um Drittanbieter zu unterstützen, um sicherzustellen, dass die Benutzeroberflächen im Mittelpunkt stehen.  

Zu diesem Bereich zählen möglicherweise auch die folgenden Anwendungen: 
-   **Visualisierung mit remotem Anvisieren mit den Augen:** Visualisierungen mit remotem Anvisieren mit den Augen: Visualisieren Sie, was Remotemitarbeiter betrachten, um sofortiges Feedback zu geben und eine genauere Verarbeitung von Informationen zu ermöglichen.
-   **Studien zur Benutzerforschung:** Die Aufmerksamkeitsnachverfolgung kann Forscher dabei unterstützen, mehr Erkenntnisse darüber zu gewinnen, wie Benutzer die natürliche Umgebung ohne Beeinträchtigungen erkennen und damit interagieren, um mehr instinktive Interaktionen zwischen Menschen und Computern zu entwerfen. Eyetracking kann Informationen liefern, die von den Teilnehmern der Studie nicht direkt formuliert werden, die andernfalls von der Forscherin leicht übersehen werden könnten. 
-   **Trainings- und Leistungsüberwachung:** Üben und optimieren Sie die Ausführung von Aufgaben, indem Sie Engpässe im Ausführungsfluss effektiver identifizieren. Eyetracking kann natürliche, Echtzeit- und zielorientierte Informationen bereitstellen, um Training, Produktivität und Sicherheit am Arbeitsplatz zu verbessern. 
-   **Entwurfsauswertungen, Marketing und Verbraucherforschung:** Eyetracking ermöglicht es kommerziellen Unternehmen, Marketing- und Verbraucherstudien in realen Umgebungen durchzuführen oder zu analysieren, was die Aufmerksamkeit eines Benutzers zur Verbesserung des Produkt- oder Raumdesigns erfasst. 

### <a name="other-use-cases"></a>Weitere Anwendungsfälle

- **Gaming:** Wollten Sie schon immer superpowers haben? Hier kommt Ihre Chance! Sie können Hologramme verstechen, indem Sie sie an ihnen ansteuern. Schneidelasen von deinen Augen – probieren Sie es in [RoboRaid aus, um HoloLens 2.](https://www.microsoft.com/p/roboraid/9nblggh5fv3j)
Machen Sie die Enanständung in Steine, oder fixieren Sie sie. Verwenden Sie Ihren Röntgenblick, um Gebäude zu erkunden. Ihrer Phantasie sind keine Grenzen gesetzt!
Sie sollten den Benutzer jedoch nicht überfordern. Um mehr zu erfahren, sehen Sie sich unsere Richtlinien für den Entwurf von Eingaben mit Blick [an.](eye-gaze-interaction.md)

- **Ausdrucksstärkere Avatare:** Eyetracking unterstützt ausdrucksstärkere 3D-Avatare, indem live Eye Tracking-Daten verwendet werden, um die Augen des Avatars zu animieren, die angeben, was der Benutzer anschaut. 

- **Texteintrag:** Eyetracking kann als Alternative für die Eingabe von Text mit geringem Aufwand verwendet werden, insbesondere dann, wenn Sprache oder Hände nicht verwendet werden können. 

<br>

## <a name="using-eye-gaze-for-interaction"></a>Verwenden des Anvings mit den Augen für die Interaktion

Es kann schwierig sein, eine Interaktion zu erstellen, die die Schnellsteuerung mit den Augen nutzt.
Auf der einen Seite bewegen sich die Augen so schnell, dass Sie darauf achten müssen, wie Sie die Eingabe zum Anvieren mit den Augen verwenden, da benutzer andernfalls die Erfahrung überwältigend oder ablenkend finden. Auf der anderen Seite können Sie auch wirklich magische Erfahrungen erstellen, die Ihre Benutzer anregen! Um Ihnen zu helfen, sehen Sie sich unsere Übersicht über wichtige Vorteile, Herausforderungen und Entwurfsempfehlungen für die Interaktion mit [den Augen an.](eye-gaze-interaction.md) 
 
## <a name="fallback-solutions-when-eye-tracking-isnt-available"></a>Fallbacklösungen, wenn eye tracking nicht verfügbar ist

In seltenen Fällen sind Eyetrackingdaten möglicherweise nicht verfügbar.
Dies kann verschiedene Gründe haben, aus denen die gängigsten unten aufgeführt sind:
* Das System konnte den Benutzer nicht [kalibrieren.](/hololens/hololens-calibration)
* Der Benutzer hat die [Kalibrierung übersprungen.](/hololens/hololens-calibration)   
* Der Benutzer ist kalibriert, hat sich aber entschieden, Ihrer App keine Berechtigung zur Verwendung seiner Eyetrackingdaten zu erteilen.    
* Der Benutzer verfügt über eine eindeutige Brille oder eine Augenbedingung, die das System noch nicht unterstützt. 
* Externe Faktoren, die eine zuverlässige Blickverfolgung verhindern, z. B. Verblendungen des HoloLens-Visiers oder der Brille, intensive direkte Brillen und Verdeckungen aufgrund von Härchen vor den Augen.

Entwickler sollten sicherstellen, dass für diese Benutzer geeignete Fallbackunterstützung vorhanden ist. Auf der Seite [Eye Tracking in DirectX (Blickverfolgung in DirectX)](../develop/native/gaze-in-directx.md#fallback-when-eye-tracking-isnt-available) werden die APIs erläutert, die erforderlich sind, um zu erkennen, ob Eyetrackingdaten verfügbar sind. 

Einige Benutzer haben sich möglicherweise bewusst dafür entschieden, den Zugriff auf ihre Eyetrackingdaten aufzuheben, und sind mit dem Kompromiss einer vertrauenswürdigen Benutzererfahrung mit dem Datenschutz in Ordnung, dass sie keinen Zugriff auf ihre Eyetrackingdaten bieten, in einigen Fällen kann dies unbeabsichtigt sein. Wenn Ihre App eye tracking verwendet und dies ein wichtiger Teil der Benutzeroberfläche ist, empfehlen wir, dies dem Benutzer klar mitzuteilen.   

Wenn Sie dem Benutzer mitteilen, warum eye tracking für Ihre Anwendung wichtig ist (möglicherweise sogar einige erweiterte Features auflisten), um das volle Potenzial Ihrer Anwendung zu erleben, kann der Benutzer besser verstehen, was er aufgibt. Helfen Sie dem Benutzer, zu ermitteln, warum eye tracking möglicherweise nicht funktioniert (basierend auf den obigen Überprüfungen), und bieten Sie einige Vorschläge, um potenzielle Probleme schnell zu beheben. 

Wenn Sie z. B. erkennen können, dass das System Eyetracking unterstützt, der Benutzer kalibriert wird und sogar seine Berechtigung erteilt hat, aber keine Eyetrackingdaten empfangen werden, kann dies auf einige andere Probleme verweisen, z. B. Auftäusche oder augenverblendete Augen. 

Es gibt seltene Fälle von Benutzern, für die eye tracking möglicherweise nicht funktioniert. Denken Sie daran, indem Sie zulassen, erinnerungen zu ver- oder sogar zu deaktivieren, um eye tracking in Ihrer App zu aktivieren.

### <a name="fall-back-for-apps-using-eye-gaze-as-a-primary-input-pointer"></a>Fall back for apps using eye-gaze as a primary input pointer (Fall back für Apps, die das Anvingen mit den Augen als primären Eingabezeiger verwenden)

Wenn Ihre App das Anvieren mit den Augen als Zeigereingabe verwendet, um hologramme in der gesamten Szene schnell auszuwählen, die Eyetrackingdaten jedoch nicht verfügbar sind, empfehlen wir, zurück zum Anvieren mit dem Kopf zu fallen und mit dem Zeigen des Cursors mit dem Kopf zu beginnen. Es wird empfohlen, ein Timeout (z. B. 500–1500 ms) zu verwenden, um zu bestimmen, ob sie wechseln möchten. Diese Aktion verhindert, dass Cursor jedes Mal angezeigt werden, wenn das System aufgrund schneller Augenbewegungen oder Winks und Blinken kurzzeitig die Nachverfolgung verliert. Wenn Sie Ein Unity-Entwickler sind, wird das automatische Fallback zum Anvischen mit dem Kopf bereits im Mixed Reality Behandelt. Wenn Sie DirectX-Entwickler sind, müssen Sie diesen Schalter selbst behandeln.

### <a name="fall-back-for-other-eye-tracking-specific-applications"></a>Fall back for other eye-tracking-specific applications (Fall back für andere Eye-Tracking-spezifische Anwendungen)

Ihre App kann das Anvingen mit den Augen auf einzigartige Weise verwenden, die speziell auf die Augen zugeschnitten ist. Beispielsweise das Animieren der Augen eines Avatars oder für wärmebildbasierte Blicke, die auf genauen Informationen zur visuellen Aufmerksamkeit basieren. In diesem Fall gibt es keinen eindeutigen Fallback. Wenn eye tracking nicht verfügbar ist, müssen diese Funktionen möglicherweise deaktiviert werden.
Auch hier wird empfohlen, dies dem Benutzer klar zu vermitteln, der möglicherweise nicht weiß, dass die Funktion nicht funktioniert.

<br>

Auf dieser Seite haben Sie hoffentlich einen guten Überblick erhalten, damit Sie sich mit der Rolle der Eyetracking- und Eye-Gaze-Eingabe für HoloLens 2. Um mit der Entwicklung zu beginnen, sehen Sie sich unsere Informationen zur Rolle des Anvierens mit den Augen für die [Interaktion mit Hologrammen,](eye-gaze-interaction.md)das [Anvieren mit](https://aka.ms/mrtk-eyes) den Augen in Unity und das [Anvieren mit den Augen in DirectX](../develop/native/gaze-in-directx.md)an.

## <a name="see-also"></a>Weitere Informationen

* [Kalibrierung](/hololens/hololens-calibration)
* [Komfort](comfort.md)
* [Interaktion durch Anvisieren](eye-gaze-interaction.md)
* [Anvischen mit den Augen in DirectX](../develop/native/gaze-in-directx.md)
* [Anvieren mit den Augen in Unity (Mixed Reality Toolkit)](https://aka.ms/mrtk-eyes)
* [Anvisieren und Ausführen](gaze-and-commit.md)
* [Spracheingabe](../out-of-scope/voice-design.md)
