---
title: Eyetracking – Blickverfolgung
description: Erfahren Sie mehr über Eyetracking für HoloLens 2 und die neuen Ebenen des menschlichen Verständnisses, wenn es sich um holografische Erfahrungen handelt.
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
keywords: Eyetracking, Mixed Reality, Eingabe, Anvisiert mit den Augen, Kalibrierung, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit, Absicht, Aktionen
ms.openlocfilehash: a4010e5244539909d2b04cdb9e2044672d1decab
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143245"
---
# <a name="eye-tracking-on-hololens-2"></a>Blickverfolgung auf HoloLens 2

![Eye tracking demo in MRTK](images/mrtk_et_scenemenu.jpg)

HoloLens 2 ermöglicht eine neue Ebene des Kontexts und des menschlichen Verständnisses innerhalb der holografischen Erfahrung, indem Entwicklern die Möglichkeit geboten wird, Informationen dazu zu verwenden, was der Benutzer ansieht. Auf dieser Seite wird erläutert, wie Entwickler von eye tracking für verschiedene Anwendungsfälle profitieren können und was beim Entwerfen von Benutzerinteraktionen mit blickbasiertem Anverfolgen zu suchen ist. 

Die Eyetracking-API wurde unter Berücksichtigung des Datenschutzes eines Benutzers entwickelt und vermeidet die Übergabe identifizierbarer Informationen, insbesondere biometrischer Daten. Für Eyetracking-fähige Anwendungen muss der Benutzer der App die Berechtigung zum Verwenden von Eyetrackinginformationen erteilen.

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
     <td>Anväuten mit den Augen</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>

<br>

## <a name="head-and-eye-tracking-design-concepts-demo"></a>Demo zu Designkonzepten für Head- und Eyetracking

Wenn Sie die Entwurfskonzepte für Kopf- und Blickverfolgung in Aktion sehen möchten, sehen Sie sich unten unsere Videodemo [entwerfen von Hologrammen – Kopfverfolgung und Blickverfolgung]() an. Wenn Sie fertig sind, fahren Sie mit einem ausführlicheren Einblick in bestimmte Themen fort.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

## <a name="calibration"></a>Kalibrierung 

Damit eye tracking korrekt funktioniert, muss jeder Benutzer eine [Eyetracking-Benutzer-Kalibrierung](/hololens/hololens-calibration) durchlaufen, für die der Benutzer eine Reihe holografischer Ziele betrachten muss. Dadurch kann das Gerät das System anpassen, um eine komfortablere und qualitativ hochwertigere Anzeige für den Benutzer zu gewährleisten und gleichzeitig eine genaue Blickverfolgung sicherzustellen. 

Eyetracking sollte für die meisten Benutzer funktionieren, aber es gibt selten Fälle, in denen ein Benutzer nicht erfolgreich kalibrieren kann. Die Kalibrierung kann aus verschiedenen Gründen fehlschlagen, einschließlich, aber nicht beschränkt auf: 
* Der Benutzer hat sich zuvor vom Kalibrierungsprozess abgemeldet.
* Der Benutzer wurde ablenkend und hat die Kalibrierungsziele nicht befolgt.
* Der Benutzer verfügt über bestimmte Arten von Kontaktobjektiven und Brillen, die das System noch nicht unterstützt. 
* Der Benutzer hat bestimmte Augen, Augenbedingungen oder Augenbrillen, die das System noch nicht unterstützt.  
* Externe Faktoren, die eine zuverlässige Blickverfolgung verhindern, z. B. Wischbeugungen am HoloLens-Visor oder Brillen, intensive direkte Brillen und Okklusionen durch Diebe vor den Augen

Entwickler sollten sicherstellen, dass sie eine angemessene Unterstützung für Benutzer bereitstellen, für die eye tracking-Daten möglicherweise nicht verfügbar sind (die nicht erfolgreich kalibrieren können). Im Abschnitt am unteren Rand dieser Seite haben wir Empfehlungen für Fallbacklösungen bereitgestellt. 

Weitere Informationen zur Kalibrierung und zur Sicherstellung eines reibungslosen Ablaufs finden Sie auf unserer [Seite zur Eyetracking-Benutzer kalibrierung.](/hololens/hololens-calibration)

<br>

## <a name="available-eye-tracking-data"></a>Verfügbare Eyetrackingdaten

Bevor wir uns mit bestimmten Anwendungsfällen für die Eingabe anvissen, möchten wir kurz auf die Funktionen hinweisen, die die HoloLens 2 [EyeTracking-API](/uwp/api/windows.perception.people.eyespose) bietet. Entwickler erhalten Zugriff auf einen einzelnen Blickstrahl (Ursprung und Richtung des Anvings) mit ca. _30 FPS (30 Hz)._
Ausführlichere Informationen zum Zugriff auf Eyetrackingdaten finden Sie in unseren Entwicklerhandbüchern für die Verwendung des Anvings mit den Augen [in DirectX](../develop/native/gaze-in-directx.md) und des Anvings mit den Augen [in Unity.](https://aka.ms/mrtk-eyes)

Das vorhergesagte Anvisieren mit den Augen liegt ungefähr innerhalb von 1,5 Grad im visuellen Winkel um das tatsächliche Ziel (siehe Abbildung unten). Da geringfügige Ungenauigkeiten zu erwarten sind, sollten Entwickler einen Gewissensrand um diesen unteren Grenzwert einplanen (z. B. können 2,0 bis 3,0 Grad zu einer viel komfortableren Erfahrung führen). Im Folgenden wird ausführlicher erläutert, wie Sie die Auswahl kleiner Ziele in Angriff setzen können. Damit die Blickverfolgung exakt funktioniert, muss jeder Benutzer eine Benutzerkalibrierung für seine Blickverfolgung durchlaufen. 

![Optimale Zielgröße im Abstand von 2 Metern](images/gazetargeting-size-1000px.jpg)<br>
*Optimale Zielgröße mit einer Entfernung von 2 Metern*

<br>

## <a name="use-cases"></a>Anwendungsfälle

Mit der Blickverfolgung können Anwendungen in Echtzeit verfolgen, wohin der Benutzer schaut. In den folgenden Anwendungsfällen werden einige Interaktionen beschrieben, die mit Blickverfolgung für HoloLens 2 Mixed Reality möglich sind.
Diese Anwendungsfälle sind noch nicht Teil der Holographic Shell-Benutzeroberfläche (d. h. der Schnittstelle, die Sie beim Starten Ihrer Anwendung HoloLens 2).
Sie können einige davon im [Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html)ausprobieren, das mehrere interessante und leistungsstarke Beispiele für die Verwendung von Eyetracking bietet, z. B. schnelle und mühelose, von den Augen unterstützte Zielauswahlen und das automatische Scrollen durch Text basierend auf dem, was der Benutzer betrachtet. 

### <a name="user-intent"></a>Benutzerabsicht

Informationen dazu, wo und was ein Benutzer ansieht, bieten einen leistungsfähigen **Kontext für andere Eingaben,** z. B. Sprache, Hände und Controller.
Dies kann für verschiedene Aufgaben verwendet werden.
Dies kann z. B. von der schnellen und mühelosen **Ausrichtung** auf die gesamte Szene reichen, indem ein Hologramm betrachtet und *"Select"* (siehe auch [Anvisieren und Committen)](gaze-and-commit.md)oder *"Put this..."* angezeigt wird. Anschließend wird nach dem Ort gesucht, an dem der Benutzer das Hologramm platzieren und *"... there" .* Beispiele hierfür finden Sie in den Artikeln [Mixed Reality Toolkit – Eye-supported Target Selection](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) (Mixed Reality-Toolkit – Blickgestützte Zielauswahl) und [Mixed Reality Toolkit – Eye-supported Target Positioning](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Positioning.html) (Mixed Reality-Toolkit – Blickgestützte Zielpositionierung).

Darüber hinaus kann ein Beispiel für eine Benutzerabsicht die Verwendung von Informationen darüber umfassen, was Benutzer betrachten, um die Interaktion mit verkörperten virtuellen Agents und interaktiven Hologrammen zu verbessern. Beispielsweise können virtuelle Agents verfügbare Optionen und ihr Verhalten basierend auf dem aktuell angezeigten Inhalt anpassen. 

### <a name="implicit-actions"></a>Implizite Aktionen

Die Kategorie der impliziten Aktionen steht in enger Beziehung zur Benutzerabsicht.
Die Idee ist, dass Hologramme oder Benutzeroberflächenelemente auf instinktive Weise reagieren, die möglicherweise nicht einmal das Gefühl hat, als interagiere der Benutzer überhaupt mit dem System, sondern dass das System und der Benutzer synchron sind. Ein Beispiel hierfür ist das **automatische Scrollen** mit den Augen, bei dem der Benutzer einen langen Text lesen kann, der automatisch mit dem Scrollen beginnt, sobald der Benutzer zum Ende des Textfelds gelangt, um den Benutzer im Lesefluss zu halten, ohne einen Finger zu heben.  
Ein wichtiger Aspekt ist, dass sich die Bildlaufgeschwindigkeit an die Lesegeschwindigkeit des Benutzers anpasst.
Ein weiteres Beispiel ist das **mit den Augen unterstützte Zoomen und Schwenken,** bei dem der Benutzer das Gefühl hat, genau auf das zu springen, worauf er sich konzentriert. Das Auslösen und Steuern der Zoomgeschwindigkeit kann durch Spracheingaben oder Handeingaben gesteuert werden. Dies ist wichtig, um dem Benutzer das Gefühl der Kontrolle zu geben und gleichzeitig eine Überlastung zu vermeiden. Im Folgenden werden diese Entwurfsüberlegungen ausführlicher erläutert. Nach dem Vergrößern kann der Benutzer dem Weg einer Straße folgen, um seine Umgebung mit den Augen zu erkunden.
Demobeispiele für diese Arten von Interaktion finden Sie im Beispiel [Mixed Reality Toolkit – Eye-supported Navigation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) (Mixed Reality-Toolkit – Blickgestützte Navigation).

Andere Anwendungsfälle für _implizite Aktionen_ können Folgendes sein:
- **Intelligente Benachrichtigungen:** Sie können sich jemals über Benachrichtigungen verärgern, die genau dort angezeigt werden, wo Sie suchen? Unter Berücksichtigung der Aufmerksamkeit eines Benutzers können Sie diese Benutzererfahrung verbessern, indem Sie Benachrichtigungen von dem Ort, an dem sich der Benutzer gerade befindet, absetzen. Dies schränkt Ableitungen ein und verlässt sie automatisch, sobald der Benutzer mit dem Lesen fertig ist. 
- **Unentdeckte Hologramme:** Hologramme, die beim Anvieren auf untergeordnetes Verhalten reagieren. Dies kann von leicht glühenden Benutzeroberflächenelementen, einer langsam aufblühenden Blume bis hin zu einem virtuellen Hund reichen, beginnend mit dem Blick auf den Benutzer und dem Wedeln des Tails. Diese Interaktion kann ein interessantes Gefühl von Konnektivität und Zufriedenheit in Ihrer Anwendung bieten.

### <a name="attention-tracking"></a>Aufmerksamkeitsverfolgung

Informationen dazu, wo oder was Benutzer betrachten, können ein äußerst leistungsstarkes Tool sein. Sie kann dabei helfen, die Verwendbarkeit von Entwürfen zu bewerten und Probleme in Workflows zu identifizieren, um sie effizienter zu gestalten.
Eyetrackingvisualisierung und -analysen sind in verschiedenen Anwendungsbereichen eine gängige Praxis. Mit HoloLens 2 bieten wir diesem Verständnis eine neue Dimension, da 3D-Hologramme in realen Kontexten platziert und entsprechend bewertet werden können. Das [Mixed Reality Toolkit enthält](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html) grundlegende Beispiele für die Protokollierung und das Laden von Eyetrackingdaten und deren Visualisierung.
Microsoft ist bestrebt, Innovationen zu fördern und gleichzeitig sicherzustellen, dass Benutzer über eine informierte und transparente Erfahrung mit der Verwendung ihrer Eye-Tracking-Informationen verfügen.  Wir arbeiten mit unseren Entwicklern und UX-Teams zusammen, um Drittanbieter zu unterstützen, um sicherzustellen, dass die Benutzererfahrungen im Mittelpunkt stehen.  

Zu diesem Bereich zählen möglicherweise auch die folgenden Anwendungen: 
-   **Visualisierung mit remotem Anvisieren mit den Augen:** Visualisierungen mit remotem Anvisieren mit den Augen: Visualisieren Sie, was Remotemitarbeiter betrachten, um sofortiges Feedback zu geben und eine genauere Verarbeitung von Informationen zu ermöglichen.
-   **Studien zur Benutzerforschung:** Die Aufmerksamkeitsnachverfolgung kann Forscher dabei unterstützen, mehr Einblicke in die Wahrnehmung und Interaktion von Benutzern in der natürlichen Umgebung zu erhalten, ohne zu beeinträchtigen, um instinktive Interaktionen zwischen Menschen und Computern zu entwerfen. Eyetracking kann Informationen liefern, die nicht direkt von den Teilnehmern der Studie formuliert werden, die andernfalls vom Forscher leicht übersehen werden können. 
-   **Trainings- und Leistungsüberwachung:** Üben und optimieren Sie die Ausführung von Aufgaben, indem Sie Engpässe im Ausführungsfluss effektiver identifizieren. Eyetracking kann natürliche, Echtzeit- und Zielinformationen bereitstellen, um das Training, die Produktivität und die Sicherheit am Arbeitsplatz zu verbessern. 
-   **Entwurfsauswertungen, Marketing und Verbraucherforschung:** Eyetracking ermöglicht kommerziellen Unternehmen, Marketing- und Verbraucherstudien in realen Umgebungen durchzuführen oder zu analysieren, was die Aufmerksamkeit eines Benutzers zur Verbesserung des Produkt- oder Raumdesigns erfasst. 

### <a name="other-use-cases"></a>Weitere Anwendungsfälle

- **Gaming:** Möchten Sie schon immer Superpowers haben? Hier kommt Ihre Chance! Sie können Hologramme befüllen, indem Sie auf sie starren. Probieren Sie es in [RoboRaid aus, um HoloLens 2](https://www.microsoft.com/p/roboraid/9nblggh5fv3j)zu HoloLens 2.
Wandeln Sie Diensel in Steine um, oder frieren Sie sie ein. Verwenden Sie Ihren Röntgenblick, um Gebäude zu erkunden. Ihrer Phantasie sind keine Grenzen gesetzt!
Achten Sie jedoch darauf, den Benutzer nicht zu überfordern. Um mehr zu erfahren, sehen Sie sich unsere Richtlinien zum Entwerfen von [Eingaben an, die auf anviert](eye-gaze-interaction.md)werden.

- **Ausdrucksstärker Avatar:** Eyetracking unterstützt ausdrucksstärkeere 3D-Avatare, indem mithilfe von Live-Blickverfolgungsdaten die Augen des Avatars animiert werden, die angeben, was der Benutzer ansieht. 

- **Texteintrag:** Eyetracking kann als Alternative für Texteingaben mit geringem Aufwand verwendet werden, insbesondere dann, wenn Sprache oder Hände unpraktisch zu verwenden sind. 

<br>

## <a name="using-eye-gaze-for-interaction"></a>Verwenden des Anvierens mit den Augen für die Interaktion

Das Erstellen einer Interaktion, die sich schnell bewegende Blickrichtung nutzt, kann eine Herausforderung darstellen.
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

Wenn Sie dem Benutzer mitteilen, warum eye tracking für Ihre Anwendung wichtig ist (möglicherweise sogar einige erweiterte Features auflisten), um das volle Potenzial Ihrer Anwendung zu erleben, kann der Benutzer besser verstehen, was er aufgibt. Helfen Sie dem Benutzer, zu ermitteln, warum die Blickverfolgung möglicherweise nicht funktioniert (basierend auf den oben genannten Überprüfungen), und bieten Sie einige Vorschläge, um potenzielle Probleme schnell zu beheben. 

Wenn Sie z. B. erkennen können, dass das System Eyetracking unterstützt, der Benutzer kalibriert wird und sogar seine Berechtigung erteilt hat, aber keine Eyetrackingdaten empfangen werden, kann dies auf einige andere Probleme verweisen, z. B. Auftäusche oder augenverblendete Augen. 

Es gibt seltene Fälle von Benutzern, für die eye tracking möglicherweise nicht funktioniert. Denken Sie daran, dass Sie Erinnerungen zum Aktivieren von EyeTracking in Ihrer App ver- oder sogar deaktivieren können.

### <a name="fall-back-for-apps-using-eye-gaze-as-a-primary-input-pointer"></a>Fall back for apps using eye-gaze as a primary input pointer (Fall back für Apps, die das Anvingen mit den Augen als primären Eingabezeiger verwenden)

Wenn Ihre App das Anvieren mit den Augen als Zeigereingabe verwendet, um hologramme in der gesamten Szene schnell auszuwählen, die Eyetrackingdaten jedoch nicht verfügbar sind, empfehlen wir, zurück zum Anvieren mit dem Kopf zu fallen und mit dem Zeigen des Cursors mit dem Kopf zu beginnen. Es wird empfohlen, ein Timeout (z. B. 500–1500 ms) zu verwenden, um zu bestimmen, ob sie wechseln möchten. Diese Aktion verhindert, dass Cursor jedes Mal angezeigt werden, wenn das System aufgrund schneller Augenbewegungen oder Winks und Blinken kurzzeitig die Nachverfolgung verliert. Wenn Sie ein Unity-Entwickler sind, wird der automatische Fallback zum Anvischen mit dem Kopf bereits im Mixed Reality Behandelt. Wenn Sie DirectX-Entwickler sind, müssen Sie diesen Schalter selbst behandeln.

### <a name="fall-back-for-other-eye-tracking-specific-applications"></a>Fall back for other eye-tracking-specific applications (Fall back für andere Eye-Tracking-spezifische Anwendungen)

Ihre App kann das Anvingen mit den Augen auf einzigartige Weise verwenden, die speziell auf die Augen zugeschnitten ist. Beispielsweise das Animieren der Augen eines Avatars oder für wärmebildbasierte Blicke, die auf genauen Informationen zur visuellen Aufmerksamkeit basieren. In diesem Fall gibt es keinen eindeutigen Fallback. Wenn eye tracking nicht verfügbar ist, müssen diese Funktionen möglicherweise deaktiviert werden.
Auch hier wird empfohlen, dies dem Benutzer klar zu vermitteln, der möglicherweise nicht weiß, dass die Funktion nicht funktioniert.

<br>

Auf dieser Seite haben Sie hoffentlich einen guten Überblick erhalten, damit Sie sich mit der Rolle der Eyetracking- und Eye-Gaze-Eingabe für HoloLens 2. Um mit der Entwicklung zu beginnen, sehen Sie sich unsere Informationen zur Rolle des Anvierens mit den Augen für die Interaktion mit Hologrammen, dem Anvieren mit den Augen [in Unity](https://aka.ms/mrtk-eyes) und dem Anvieren mit den Augen [in DirectX an.](../develop/native/gaze-in-directx.md) [](eye-gaze-interaction.md)

## <a name="see-also"></a>Weitere Informationen

* [Kalibrierung](/hololens/hololens-calibration)
* [Komfort](comfort.md)
* [Interaktion durch Anvisieren](eye-gaze-interaction.md)
* [Anvingen mit den Augen in DirectX](../develop/native/gaze-in-directx.md)
* [Anvingen mit den Augen in Unity (Mixed Reality Toolkit)](https://aka.ms/mrtk-eyes)
* [Anvisieren und Ausführen](gaze-and-commit.md)
* [Spracheingabe](../out-of-scope/voice-design.md)
