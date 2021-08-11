---
title: Gemeinsame Erfahrungen in Mixed Reality
description: Holografische Apps können Raumanker von einem HoloLens zu einem anderen freigeben, sodass Benutzer ein Hologramm an derselben Stelle in der realen Welt auf mehreren Geräten rendern können.
author: thetuvix
ms.author: grbury
ms.date: 02/10/2019
ms.topic: article
keywords: Shared Experience, Mixed Reality, Hologramm, Raumanker, Mehrere Benutzer, Multi
ms.openlocfilehash: fe738d07e57bd2f62cab8036a09ca6ab31d6544bdd9b6dacc8dde3445fa58214
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193590"
---
# <a name="shared-experiences-in-mixed-reality"></a>Gemeinsame Erfahrungen in Mixed Reality

Hologramme müssen nicht nur für einen Benutzer privat bleiben. Holografische Apps können [Raumanker](../../design/spatial-anchors.md) von einem HoloLens-, iOS- oder Android-Gerät an ein anderes weitergeben, sodass Benutzer ein Hologramm an derselben Stelle in der realen Welt auf mehreren Geräten rendern können.

## <a name="six-questions-to-define-shared-scenarios"></a>Sechs Fragen zum Definieren freigegebener Szenarien

Bevor Sie mit dem Entwerfen für freigegebene Erfahrungen beginnen, ist es wichtig, die Zielszenarien zu definieren. Anhand dieser Szenarien können Sie verdeutlichen, was Sie entwerfen, und ein gemeinsames Vokabular einrichten, um die in Ihrer Erfahrung erforderlichen Features zu vergleichen und zu kontrastieren. Das Verständnis des Kernproblems und der verschiedenen Möglichkeiten für Lösungen ist der Schlüssel zum Aufdecken von Möglichkeiten, die in diesem neuen Medium inhärent sind.

Durch interne Prototypen und Durchsuchungen unserer HoloLens Partnerorganisationen haben wir sechs Fragen erstellt, mit denen Sie gemeinsam genutzte Szenarien definieren können. Diese Fragen bilden ein Framework, das nicht vollständig sein soll, um die wichtigen Attribute Ihrer Szenarien zu verdingen.

### <a name="1-how-are-they-sharing"></a>1. Wie werden sie freigegeben?

Eine Präsentation kann von einem einzelnen virtuellen Benutzer geleitet werden, während mehrere Benutzer zusammenarbeiten können, oder eine Lehrkraft kann anleitungen für virtuelle Kursteilnehmer bereitstellen, die mit virtuellen Materialien arbeiten. Die Komplexität der Erfahrungen steigt basierend auf der Ebene der Agentur, die ein Benutzer in einem Szenario hat oder haben kann.

![Man and women with hologramm on table (Menschen und Frauen mit Hologramm auf dem Tisch)](images/man-and-women-with-holograph-on-table-500px.png)

Es gibt viele Möglichkeiten zum Freigeben, aber wir haben festgestellt, dass die meisten davon in drei Kategorien fallen:

* **Präsentation:** Wenn mehreren Benutzern derselbe Inhalt angezeigt wird. Beispiel: Ein Professor hält eine Lektion an mehrere Studenten, die das gleiche holografische Material verwenden, das allen präsentiert wird. Der Professor könnte jedoch über eigene Hinweise und Notizen verfügen, die für andere möglicherweise nicht sichtbar sind.
* **Zusammenarbeit:** Wenn Personen zusammenarbeiten, um einige gemeinsame Ziele zu erreichen. Beispiel: Der Professor hat ein Projekt gegeben, um mehr über die Durchführung eines Heart-Spreches zu erfahren. Studenten koppeln sich und erstellen ein gemeinsames Skills-Lab, das es Medizinischen Studenten ermöglicht, am Heartmodell zusammenzuarbeiten und zu lernen.
* **Leitfaden:** Wenn eine Person einem Benutzer hilft, ein Problem in einer 1:1-Interaktion zu lösen. Beispiel: Der Professor, der einem Kursteilnehmer Anleitungen gibt, wenn er das Lab für fähigkeitenbehaftete Fähigkeiten in der gemeinsamen Umgebung durchnimmt.

### <a name="2-what-is-the-group-size"></a>2. Wie groß ist die Gruppe?

**1:1-Freigabeerfahrungen** können eine starke Baseline darstellen, und im Idealfall können Ihre Proof of Concept-Funktionen auf dieser Ebene erstellt werden. Beachten Sie jedoch, dass die Gemeinsame Nutzung mit großen Gruppen (über sechs Personen) sowohl technische (Daten und Netzwerke) als auch soziale Probleme verursachen kann (die Auswirkung, dass sie sich in einem Raum mit [mehreren Avataren](https://vimeo.com/160704056)befinden). Die Komplexität nimmt exponentiell zu, wenn Sie von **kleinen** zu **großen Gruppen** wechseln.

Wir haben festgestellt, dass die Anforderungen von Gruppen in drei Größenkategorien fallen können:
* 1:1
* Kleine < 7
* Large >= 7

Die Gruppengröße stellt eine wichtige Frage, da sie Beeinflusst:

* Darstellungen von Personen im holografischen Raum
* Skalierung von Objekten
* Skalierung der Umgebung

### <a name="3-where-is-everyone"></a>3. Wo sind alle?

Die Stärke von Mixed Reality kommt ins Spiel, wenn eine gemeinsame Erfahrung an demselben Ort stattfinden kann. Wir nennen **dies zusammengeknannte**. Wenn die Gruppe dagegen verteilt ist und sich mindestens ein Teilnehmer nicht im gleichen physischen Raum befindet (wie dies häufig bei VR der Fall ist), wird dies als **Remoteerfahrung** bezeichnet. Häufig ist es der Fall, dass Ihre Gruppe sowohl gruppierungsbeteiligte **teilnehmer** als auch Remoteteilnehmer hat (z. B. zwei Gruppen in Konferenzräumen).

![Drei Personen mit Hologramm auf der Tabelle](images/three-people-with-holograph-on-table-500px.png)

Die folgenden Kategorien helfen ihnen zu vermitteln, wo sich Benutzer befinden:

* **Verteilbar:** Alle Ihre Benutzer werden sich im selben physischen Raumbefinden.
* **Remote:** Alle Ihre Benutzer sind in separaten physischen Räumen.
* **Beide:** Ihre Benutzer sind eine Mischung aus zusammenstellungs- und Remoteräumen.

Diese Frage ist von entscheidender Bedeutung, da sie Sich auf Dies auswirkt:

* Wie kommunizieren Menschen?
    * Beispiel: Ob sie Avatare haben sollen?
* Welche Objekte sie sehen. Werden alle Objekte freigegeben?
* Ob wir uns an ihre Umgebung anpassen müssen?

### <a name="4-when-are-they-sharing"></a>4. Wann werden sie freigegeben?

In der Regel stellen wir uns **synchrone** Erfahrungen vor, wenn gemeinsame Erfahrungen in den Sinn kommen: Wir machen alles zusammen. Wenn wir jedoch ein einzelnes virtuelles Element einschließen, das von einer anderen Person hinzugefügt wurde, haben wir ein **asynchrones** Szenario. Imagine eine Notiz oder ein Sprachmemot, das in einer virtuellen Umgebung hinterlassen wird. Wie gehen Sie mit 100 virtuellen Memos um, die in Ihrem Entwurf übrig sind? Was geschieht, wenn sie von Dutzenden von Personen mit unterschiedlichen Datenschutzebenen stammen?

Betrachten Sie Ihre Erfahrungen als eine dieser Zeitkategorien:

* **Synchron:** Gleichzeitiges Freigeben der holografischen Benutzeroberfläche. Beispiel: Zwei Kursteilnehmer, die das Skills Lab gleichzeitig durchführen.
* **Asynchron:** Gemeinsame Nutzung der holografischen Benutzeroberfläche zu unterschiedlichen Zeiten. Beispiel: Zwei Kursteilnehmer, die das Skills Lab durchführen, aber zu unterschiedlichen Zeiten an separaten Abschnitten arbeiten.
* **Beides:** Ihre Benutzer verwenden die Freigabe manchmal synchron, aber zu anderen Zeiten asynchron. Beispiel: Ein Professor, der die Von den Kursteilnehmern zu einem späteren Zeitpunkt durchgeführte Zuweisung bewertet und Notizen für die Kursteilnehmer für den nächsten Tag ablässt.

Diese Frage ist wichtig, da sie Sich auf Dies auswirkt:

* Objekt- und Umgebungspersistenz. Beispiel: Speichern der Zustände, damit sie abgerufen werden können.
* Benutzerperspektive. Beispiel: Denken Sie vielleicht daran, was der Benutzer beim Hinterlassen von Notizen betrachtet hat.

### <a name="5-how-similar-are-their-physical-environments"></a>5. Wie ähnlich sind die physischen Umgebungen?

Die Wahrscheinlichkeit, dass zwei identische Umgebungen in der Praxis außerhalb der umgebungsbezogenen Umgebungen gleich sind, ist ärg, es sei denn, diese Umgebungen wurden so konzipiert, dass sie identisch sind. Es ist wahrscheinlicher, dass Sie **über ähnliche** Umgebungen verfügen. Konferenzräume sind z. B. ähnlich– sie verfügen in der Regel über eine zentral angeordnete Tabelle, die von Einemen umgeben ist. Dagegen sind Die Räume unterschiedlich** und können eine beliebige Anzahl von Steine in einem unendlichen Array von Layouts enthalten.

![Hologramm für Tabelle](images/holograph-on-table-500px.png)

Berücksichtigen Sie Ihre Freigabeerfahrungen, die in eine der beiden folgenden Kategorien passen:

* **Ähnlich:** Umgebungen, die tendenziell ähnliches Licht, Umgebungslicht und -sound und physische Raumgröße aufweisen. Beispiel: Der Professor befindet sich in der Lektionsreihe A, und die Studierenden befinden sich in Der Lektionsraum B. Die Lektionsreihe A hat möglicherweise weniger Treffer als B, aber beide verfügen möglicherweise über einen physischen Tisch, auf dem Hologramme zu platzieren sind.
* **Unterschiedlich:** Umgebungen, die sich in Denkeinstellungen, Raumgrößen, Licht- und Soundaspekten unterscheiden. Beispiel: Ein Professor befindet sich in einem Schwerpunktraum, aber die Studenten befinden sich in einem großen Lektionsraum, der mit Studenten und Lehrkräften gefüllt ist.

Es ist wichtig, sich gedanken über die Umgebung zu machen, da sich [dies](/hololens/hololens-environment-considerations)auf Folgendes auswirkt:

* Wie Benutzer diese Objekte erleben. Beispiel: Wenn Ihre Erfahrung am besten für eine Tabelle funktioniert und der Benutzer keine Tabelle hat? Oder auf einer flachen Bodenoberfläche, aber der Benutzer hat einen überladenen Platz.
* Skalierung der Objekte. Beispiel: Das Platzieren eines menschlichen Modells mit sechs Metern auf einer Tabelle kann eine Herausforderung darstellen, aber ein Heart-Modell würde hervorragend funktionieren.

### <a name="6-what-devices-are-they-using"></a>6. Welche Geräte werden verwendet?

Heutzutage sehen Sie häufig gemeinsame Erfahrungen zwischen zwei [**immersiven Geräten**](../../discover/immersive-headset-hardware-details.md) (diese Geräte unterscheiden sich möglicherweise geringfügig für Schaltflächen und relative Funktionen, aber nicht stark) oder zwei **holografische Geräte,** wenn die Lösungen für diese Geräte vorgesehen sind. Überlegen Sie jedoch, ob **2D-Geräte** (ein Mobile/Desktop-Teilnehmer oder Beobachter) ein notwendiger Aspekt sind, insbesondere in Situationen **mit gemischten 2D- und 3D-Geräten.** Das Verständnis der Gerätetypen, die Ihre Teilnehmer verwenden werden, ist wichtig, nicht nur, weil sie unterschiedliche Genauigkeits- und Dateneinschränkungen und -möglichkeiten aufweisen, sondern auch, weil Benutzer eindeutige Erwartungen an jede Plattform haben.

## <a name="exploring-the-potential-of-shared-experiences"></a>Untersuchen des Potenzials gemeinsam genutzter Umgebungen

Antworten auf die oben genannten Fragen können kombiniert werden, um Ihr gemeinsames Szenario besser zu verstehen und die Herausforderungen beim Erweitern der Erfahrung zu verinerten. Für das Microsoft-Team hat dies dazu beigetragen, eine Roadmap für die Verbesserung der heutigen Erfahrungen zu erstellen, die Nuancen dieser komplexen Probleme zu verstehen und zu erfahren, wie sie von gemeinsamen Erfahrungen in Mixed Reality profitieren können.

Stellen Sie sich beispielsweise eines der Szenarien Skype aus dem HoloLens-Start vor: Ein Benutzer hat mithilfe eines Remoteexperten [durchgearbeitet, wie ein fehlerhafter Lichtschalter behoben](https://www.youtube.com/watch?v=iBfzs3G8BEA) werden kann.

![Korrigieren eines Lichtschalters mit Unterstützung über Skype für HoloLens](images/fix-a-broken-switch-with-hololens-640px.jpg)

*Ein Experte stellt **1:1-Anleitungen** von seinem **2D-Desktopcomputer** für einen Benutzer eines **3D-Mixed Reality-Geräts** bereit. Die **Anleitung** ist **synchron,** und die physischen Umgebungen **unterscheiden** sich von .*

Eine solche Erfahrung ist eine Schrittänderung gegenüber unserer aktuellen Erfahrung– das Anwenden des Paradigmas von Video und Stimme auf ein neues Medium. Wenn wir jedoch in die Zukunft blicken, müssen wir die Möglichkeiten unserer Szenarien besser definieren und Erfahrungen erstellen, die die Stärke von Mixed Reality widerspiegeln.

Betrachten Sie das Tool für die [OnSight-Zusammenarbeit,](https://www.youtube.com/watch?v=XtUyUJAVQ6w)das vom Jet-Brillenlabor der NASA entwickelt wurde. Forscher, die an Daten der Mars-Rover-Missionen arbeiten, können mit Kollegen in Echtzeit innerhalb der Daten aus der Marslandschaft zusammenarbeiten.

![Zusammenarbeit zwischen Kollegen, die remote getrennt sind, um die Arbeit für den Mars Rover zu planen](images/onsight-nasa-jpl.gif)

*Ein Forscher untersucht eine Umgebung mithilfe eines **3D-Mixed Reality-Geräts** mit einer kleinen Gruppe von Remote-Kollegen, die **3D- und 2D-Geräte** verwenden.   Die **Zusammenarbeit** ist **synchron** (kann aber asynchron erneut aufgerufen werden), und die physischen Umgebungen sind (virtuell) **ähnlich.***

Erfahrungen wie OnSight bieten neue Möglichkeiten für die Zusammenarbeit. Vom physischen Verweisen auf Elemente in der virtuellen Umgebung bis hin zum Stehen neben einem Kollegen und teilen deren Perspektive, während sie ihre Ergebnisse erklären. OnSight verwendet den Blick auf Immersion und Präsenz, um das Teilen von Erfahrungen in Mixed Reality zu überdenken.

Intuitive Zusammenarbeit ist das Fundament der Konversation, und es ist entscheidend, zusammen zu arbeiten und zu verstehen, wie wir diese Komplexität auf die Komplexität von Mixed Reality anwenden können. Wenn wir nicht nur die Freigabe von Erfahrungen in Mixed Reality neu erstellen, sondern sie auch überladen können, ist dies ein Paradigmenwechsel für die Zukunft der Arbeit. Das Entwerfen für gemeinsame Erfahrungen in Mixed Reality ist ein neuer und spannender Bereich – und wir sind erst am Anfang.

## <a name="get-started-building-shared-experiences"></a>Erste Schritte beim Erstellen gemeinsam genutzter Erfahrungen

Je nach Anwendung und Szenario gibt es verschiedene Anforderungen, um die gewünschte Benutzererfahrung zu erzielen. Dazu zählen:

* **Übereinstimmungsherstellung:** Die Möglichkeit, Sitzungen zu erstellen, Sitzungen anordnen, bestimmte Personen lokal und remote für die Sitzung zu entdecken und einzulädnen.
* **Ankerfreigabe:** Möglichkeit, Koordinaten auf mehreren Geräten in einem gemeinsamen lokalen Raum auszurichten, sodass Hologramme für alle Personen an derselben Stelle angezeigt werden.
* **Netzwerk:** Möglichkeit, Positionen, Interaktionen und Bewegungen von Personen und Hologrammen in Echtzeit über alle Teilnehmer hinweg zu synchronisieren.
* **Zustandsspeicher:** Möglichkeit zum Speichern von Hologrammmerkmalen und -positionen im Raum für die Verknüpfung während der Sitzung, die Rückrufaktion zu einem späteren Zeitpunkt und die Stabilität gegenüber Netzwerkproblemen.

Der Schlüssel für gemeinsame Erfahrungen ist, dass mehrere Benutzer die gleichen Hologramme weltweit auf ihrem eigenen Gerät sehen, was häufig durch gemeinsame Anker erfolgt, um Koordinaten geräteübergreifend auszurichten.

Verwenden Sie zum Freigeben von Ankern die [Azure-Spatial Anchors](/azure/spatial-anchors):

* Zuerst platziert der Benutzer das Hologramm.
* Die App erstellt [einen Raumanker,](../../design/spatial-anchors.md)um dieses Hologramm genau in der Welt anheften zu können.
* Die Anker können für HoloLens, iOS- und Android-Geräte über [Azure Spatial Anchors.](/azure/spatial-anchors/)

Mit einem gemeinsam genutzten Raumanker verfügt die App auf jedem Gerät jetzt über ein gemeinsames Koordinatensystem, [in](../../design/coordinate-systems.md) dem sie Inhalte platzieren kann. Nun kann die App sicherstellen, dass das Hologramm an der gleichen Position positioniert und positioniert wird.

Auf HoloLens Geräten können Sie Anker auch offline von einem Gerät an ein anderes freigeben.  Verwenden Sie die folgenden Links, um zu entscheiden, was für Ihre Anwendung am besten ist.

## <a name="evaluating-tech-options"></a>Auswerten von technischen Optionen

Es stehen verschiedene Dienst- und Technologieoptionen zur Verfügung, um Mixed Reality-Funktionen für mehrere Benutzer zu erstellen.  Es kann schwierig sein, einen Pfad zu wählen, daher werden im Folgenden einige Optionen im Szenario erläutert.

## <a name="shared-static-holograms-no-interactions"></a>Freigegebene statische Hologramme (keine Interaktionen)

Nutzen [Sie Azure Spatial Anchors](/azure/spatial-anchors/) in Ihrer App.  Wenn Sie Raumanker aktivieren und geräteübergreifend freigeben, können Sie eine Anwendung erstellen, in der Benutzer Hologramme gleichzeitig an derselben Stelle sehen.  Zusätzliche geräteübergreifende Synchronisierung ist erforderlich, damit Benutzer mit Hologrammen interagieren und Bewegungen oder Zustandsaktualisierungen von Hologrammen sehen können.

## <a name="share-first-person-perspective"></a>Freigeben der Perspektive der ersten Person

Nutzen Sie die integrierte Miracast-Unterstützung für lokale Benutzer, wenn Sie über einen unterstützten Miracast-Empfänger verfügen, z. B. einen PC oder TV. Es ist kein zusätzlicher App-Code erforderlich.

Nutzen [Sie MixedReality-WebRTC](https://github.com/microsoft/mixedreality-webrtc) in Ihrer App für Remotebenutzer oder wenn Sie nicht über Miracast verfügen, für die Sie freigeben möchten.  Das Aktivieren einer WebRTC-Verbindung ermöglicht 1:1-Audio-/Videostreams zwischen Benutzern mit einem Datenkanal für das geräteübergreifende Messaging.  Die Mixed Reality-Implementierung optimiert für HoloLens, indem mixed reality capture video stream of the view of the view of the HoloLens user to others (Mixed Reality-Erfassungsvideostream der Ansicht des Benutzers für andere Benutzer) zur Verfügung stellt.  Wenn Sie das Videostreaming auf mehrere Remoteclients hochskalieren möchten, wird in der Regel ein [MCU-Dienstanbieter](https://webrtcglossary.com/mcu/) (Multipoint-Konferenzeinheit) verwendet, z. [B. SignalWire](https://signalwire.com/).  Eine SignalWire-Bereitstellung in Azure mit einem Klick ist über [Freeswitch verfügbar.](https://github.com/andywolk/azure-freeswitch-gpu-windows)

> [!NOTE]
> Beachten Sie, dass SignalWire ein kostenpflichtiger Dienst ist und sich nicht im Besitz von Microsoft befindet bzw. nicht mit Microsoft verbunden ist.

## <a name="presenter-spectator-applications-and-demos"></a>Presenter-Spectator von Anwendungen und Demos

Nutzen [Sie MixedReality-Durchsichtansicht,](https://github.com/microsoft/MixedReality-SpectatorView) um ihre [App mit](spectator-view.md) zahlreichen Funktionen zu betrachten.  Aktivieren Sie andere Geräte (HL, Android, iOS und Videokameras), um zu sehen, was die HoloLens aus einer anderen Perspektive am gleichen Standort sieht, und Updates zu Interaktionen des Host HoloLens benutzers zu erhalten, der mit den Hologrammen interagiert.  Sehen Sie sich an, machen Sie Bilder, und zeichnen Sie video auf, was der Host mit den Hologrammen in der Anwendung aus Ihrer eigenen räumlichen Perspektive mit dem Begleitperson der gleichen App macht.

**Hinweis:** Bilder werden über einen Screenshot auf iOS-/Android-Geräten aufgenommen.

## <a name="multi-user-collaborative-experience"></a>Umgebung für die Zusammenarbeit mit mehreren Benutzer

Beginnen Sie [mit](../unity/tutorials/mr-learning-sharing-02.md)unserem Lerntutorial für mehrere Benutzer, das [Azure Spatial Anchors](/azure/spatial-anchors/) für lokale Benutzer und das [Photon SDK](https://www.photonengine.com/PUN) zum Synchronisieren des Inhalts/Status in der Szene nutzt. Erstellen Sie lokal zusammenarbeitende Anwendungen, bei denen jeder Benutzer seine eigene Perspektive auf die Hologramme in der Szene hat und jeder vollständig mit den Hologrammen interagieren kann.  Updates werden auf allen Geräten bereitgestellt, und die Interaktionskonfliktverwaltung wird von Photon verarbeitet.

> [!NOTE]
> Beachten Sie, [dass Photon](https://www.photonengine.com/) ein Nicht-Microsoft-Produkt ist, sodass möglicherweise eine Abrechnungsbeziehung mit Photon erforderlich ist, um eine höhere Nutzung zu produktisieren und zu skalieren.

## <a name="future-work"></a>Die Zukunft

Komponentenfunktionen und Schnittstellen helfen bei der Bereitstellung von gemeinsamer Konsistenz und stabiler Unterstützung für die verschiedenen Szenarien und zugrunde liegenden Technologien.  Wählen Sie bis dahin den besten Pfad aus, der dem Szenario entspricht, das Sie in Ihrer Anwendung erreichen möchten.

Ein anderes Szenario oder wunsch, eine andere Technologie/einen anderen Dienst zu verwenden? Geben Sie Feedback GitHub Probleme im entsprechenden Repository am unteren Rand dieser Seite, oder erreichen Sie [HoloDevelopers Slack](https://holodevelopers.slack.com/).

## <a name="see-also"></a>Siehe auch

* [Azure Spatial Anchors](/azure/spatial-anchors)
* [Gemeinsame Raumanker in DirectX](shared-spatial-anchors-in-directx.md)
* [Gemeinsame Erlebnisse in Unity](../unity/shared-experiences-in-unity.md)
* [Spectator View](spectator-view.md)