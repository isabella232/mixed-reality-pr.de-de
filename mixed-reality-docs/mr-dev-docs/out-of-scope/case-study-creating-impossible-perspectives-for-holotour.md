---
title: 'Fallstudie: Erstellen unmöglicher Perspektiven für HoloTour'
description: Wir wollten, dass Ihre Erfahrungen in HoloTour Microsoft HoloLens sind. Zusätzlich zu den herkömmlichen Stopps haben wir einige "unmögliche Perspektiven" geplant.
author: dannyaskew
ms.author: daaske
ms.date: 03/21/2018
ms.topic: article
keywords: HoloTour, HoloLens, Windows Mixed Reality
ms.openlocfilehash: bf1f2b3c9c82e4b649a75efc0275a063ea5a2363dfa15b818c0159b947f6b515
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115199913"
---
# <a name="case-study---creating-impossible-perspectives-for-holotour"></a>Fallstudie: Erstellen unmöglicher Perspektiven für HoloTour

Wir wollten, dass Ihre Erfahrungen in HoloTour Microsoft HoloLens sind. Zusätzlich zu den herkömmlichen Haltestellen haben wir einige "unmögliche Perspektiven" geplant– Momenten, die auf jeder Tour nicht zu erleben wären, die wir jedoch über die Technologie in HoloLens direkt in Ihr Zimmer bringen konnten. Das Erstellen des Inhalts für diese Erfahrungen erforderte einige andere Techniken als unser Standarderfassungsprozess.

## <a name="the-content-challenge"></a>Die Inhaltsausforderung

Es gibt bestimmte Szenen in der HoloTour-Erfahrung, z. B. die Fahrten mit dem Heißsprechblasen über das moderne Rom und die Sprechblasen in Classiatorial In Rom, die einzigartige Ansichten bieten, die Sie an anderer Stelle nicht sehen werden. Diese Augenblicke sollen Sie überdezitieren und in Erstaunen erleben, wodurch Ihre Fahrt durch HoloTour mehr als nur eine Lernerfahrung ist. Dies sind die Augenblicke, an die Sie sich erinnern sollten, und wir freuen uns, andere Personen darüber zu informieren. Da wir unser Kameragerät nicht in den Himmel steigen konnten und (noch) keine Zeitreise gemastert haben, hat jede dieser "unmöglichen Perspektiven" einen speziellen Ansatz zum Erstellen von Inhalten gefordert.

## <a name="behind-the-scenes"></a>Abläufe im Hintergrund

Das Erstellen dieser einzigartigen Augenblicke und Perspektiven erforderte mehr als nur das Erstellen und Bearbeiten. Es dauerte sehr viel Zeit, Menschen mit vielen unterschiedlichen Fähigkeiten und ein wenig Desast-Magic.

### <a name="viewing-rome-from-a-hot-air-balloon"></a>Anzeigen von Rome über einen Heißsprechblasen

Aus unseren frühen Planungstagen wussten wir, dass wir Luftaufnahmen in HoloTour machen wollten. Wenn Sie Rome vom Himmel aus sehen, erhalten Sie eine Perspektive, die die meisten Menschen nie sehen können, und ein Gefühl dafür, wie beliebte Sehenswürdigkeiten räumlich liegen. Es wäre sehr schwierig gewesen, dies selbst mit der vorhandenen Kamera und dem Mikrofongerät zu erfassen, aber glücklicherweise war dies nicht der Fall.

Zunächst ist es wichtig zu erklären, dass alle Orte, die Sie in HoloTour besuchen, Bewegungen in ihnen haben. Unser Ziel war es, Ihnen das "Gefühl zu geben, dass Sie wirklich dort sind", und da Sie von Bewegungen umgeben sind, überall dort, wo Sie sich im realen Leben bewegen, mussten unsere virtuellen Ziele auch Umgebungsbewegungen vermitteln. Wenn Sie z. B. das Pantheon auf Ihrer Fahrt besuchen, werden Sie sehen, wie Menschen durch die Nativ-Tische schweifen und die Schritte ausführen. Die Hintergrundbewegung sorgt dafür, dass Sie das Gefühl haben, tatsächlich am Standort zu stehen, anstatt sich in einer ge stageten, statischen Umgebung zu befinden.

Um die Luftaufnahmen für die Sprechblasenfahrten zu erstellen, haben wir mit anderen Teams von Microsoft zusammengearbeitet, um Zugriff auf Luftbildaufnahmen von Rome zu erhalten. Die Qualität dieser Bilder war hervorragend, und die Ansicht war hervorragend, aber als wir sie in den Szenen ohne Änderung verwendet haben, waren sie im Vergleich zu den anderen Teilen der Tour leblos, und das Fehlen von Bewegung war störend. 


![Der Hot Air Balloon Basket, gleitend über Rome.](images/hotairballoon1-300px.png)<br>
*Der Korb des Heißsprechblasenballs, der über Rome schwebt*

Um sicherzustellen, dass die Luftaufnahmen die gleiche Qualitätsleiste wie andere Ziele erreichen, haben wir uns entschieden, die statischen Fotos in dynamische Szenen zu transformieren. Der erste Schritt war das Bearbeiten des Bilds und der zusammengesetzten Bewegung. Wir haben einen Interpreten für visuelle Effekte vertrag, um uns dabei zu unterstützen. Die Bearbeitung wurde durchgeführt, um langsame Abweichungen von Clouds, Dasnen von Wilden und gelegentliches Durchlaufen der Wolke durch eine Ebene oder einen Sturz zu zeigen. Vor Ort wurden mehrere Autos auf den Straßen fahren. Wenn Sie auf der HoloTour auf der Tour durch Rome waren, ist es unwahrscheinlich, dass Sie sich dieser Bewegung explizit bewusst waren. Das ist wirklich toll! Die feinen Bewegungen sollen Ihnen nicht auf den Augen bleiben, aber ohne diese kleinen Berührungen haben die Menschen sofort bemerkt, dass es sich um ein statisches Bild in der Szene handelt.

Der zweite Schritt, den wir getan haben, war, Ihnen einen Ausgangspunkt für die Anzeige der Szene zu geben. Sie werden nicht das Gefühl haben, wirklich dort zu sein, wenn es so aussieht, als würden Sie einfach in der Luft gleiten. Daher haben wir ein 3D-Modell eines Balloons erstellt und darin platziert. Auf diese Weise können Sie den Sprechblasen umherspazieren und über den Rand schauen, um einen besseren Blick zu erhalten. Wir haben dies als eine natürliche und spaßige Möglichkeit zum Erleben der Luftaufnahmen gefunden.

Die Heißsprechblasenerfahrung stellte für unser Audioteam besondere Herausforderungen dar, da die Logistik verhinderte, dass Mikrofone tausende Meter über Rome bewegen. Glücklicherweise hatten wir eine große Menge von Umgebungsaudioaufnahmen aus der ganzen Stadt, die wir während der Postproduktion verwenden konnten. Wir haben Audioemitter an ihren relativen Stellen platziert, von wo aus sie vom Boden erfasst wurden. Die Audiowiedergabe wurde dann so gefiltert, dass sie weit entfernt klingt, als ob Sie sie aus der Perspektive einer Person hören würden, die sich im heißer Luftsprechblasenbereich befäbe, um eine echte, direktionale Soundscape für die Szene zu schaffen.

### <a name="time-traveling-to-ancient-rome"></a>Zeitreise nach Rom

Die Sehenswürdigkeiten von Sehenswürdigkeiten und Gebäuden in Rom sind auch zweitausend Jahre nach ihrer Konstruktion einzigartig, aber wir wussten, dass wir eine einzigartige Gelegenheit hatten, Ihnen zu zeigen, wie es wäre, in der Zeit zurück zu gehen und diese Strukturen so zu sehen, wie sie im 1. Rom aufgetreten sind.

Natürlich gibt es kein Videomaterial oder statische Bilder) von C wie bei der Erstellung, daher mussten wir ein eigenes erstellen. Wir mussten viel Nachforschungen unternehmen, um so viel über die Struktur zu erfahren, wie wir konnten. die Materialien zu verstehen, aus der sie erstellt wurde, Architekturdiagramme zu überprüfen und Historische Beschreibungen zu lesen, um genügend Informationen zu erhalten, um eine virtuelle Neugestaltung zu ermöglichen. 

![Die moderne Moderne des Cinnens mit einer Überlagerung, die die Hotelfläche zeigt, wie sie in der Stadt Rom aussehen würde.](images/rome-colosseum-overlay-500px.png)<br>
*Die moderne Moderne des Cinnens mit einer Überlagerung, die den Hotelbelag zeigt, wie er in "Rome" aussädet.*

Das erste, was wir tun wollten, war die Erweiterung der traditionellen Überlagerung mit Bildungseinrichtungen. Wenn Sie in HoloTour die heute so aussehenden Brillen in der heutigen Form besuchen, wird die Etage transformiert, um Ihnen zu zeigen, wie sie während der Verwendung aussistent wäre, einschließlich der aufwendigen Stagingbereiche. Bei einer normalen Tour haben Sie diese Informationen möglicherweise beschrieben, und Sie könnten versuchen, sie sich vorzustellen, aber in HoloTour können Sie sie tatsächlich sehen.

Bei einer überlagerten Darstellung wie dieser haben wir unsere Gäste mit dem Standpunkt des Aufnahmematerials übereinstimmen und das Überlagerungsbild von Hand erstellen können. Die Perspektive muss übereinstimmen, damit beides richtig ausgerichtet wird, wenn wir das Video durch unser Bild ersetzen.

### <a name="staging-the-gladiator-fight"></a>Staging des Verwalters

Obwohl Überlagerungen eine ansprechende Möglichkeit sind, Menschen über die Geschichte zu vermitteln, haben wir uns am meisten darüber gespannt, Sie zurück in die Zeit zu bringen. Die Überlagerung war nur ein stilles Bild von einem bestimmten Blickpunkt, aber für die Zeitreise müsste der gesamte C bildes modelliert werden, und wie oben erläutert, mussten wir Bewegung in der Szene haben, damit sie sich anfühlt. Dies zu erreichen, erforderte viel Aufwand.

Diese Aufgabe war für unser Team zu groß, um allein zu arbeiten. Daher hat unser Artteam mit Demklangtree zusammengearbeitet, einem Unternehmen mit externen Effekten, das in der Regel an visuellen Effekten für Seine Filme arbeitet. Wir haben uns bei der Neuerstellung von C wiederhergestellt, sodass wir Ihnen die Struktur beibringen konnten, während sie auf dem Fuße des Kastens stehen, und eine Ansicht eines Verwalters aus der Schachtel des Kastens erstellen konnten. Die jubelnden Massen und winkenden Banner fügen die feinen Bewegungen hinzu, die erforderlich sind, damit es sich so ansieht, als ob es sich um echte Orte und nicht nur um Bilder handelt.

![Die neu erstellten Cstellungen, wie aus der Parkfläche zu sehen. Wenn sie in HoloTour angezeigt werden, flattern die Banner in der Brille und geben ein Gefühl von Bewegung.](images/recreated-colosseum-holotour-500px.png)<br>
*Die neu erstellten Cstellungen, wie aus der Parkfläche zu sehen. Wenn sie in HoloTour angezeigt werden, flattern die Banner in der Brille und geben ein Gefühl von Bewegung.*

Die Tour durch Rome endet mit dem 4.000-Zähler. Wir stellten die als Video gerenderten 3D-Zuschauersimulationen für uns bereit, aber wir mussten die Beläge auf dem Boden der 3D-Menge hinzufügen. Dieser Teil unseres Prozesses hat eher wie eine Videoproduktion von Einer -Videoproduktion als ein Projekt aus einem Inkubationsspielstudio ausgesehen. Mitglieder unseres Teams haben eine grobe Abfolge erstellt und dann mit einem Moderatoren verfeinert. Wir haben Akteure eingestellt, um unseren Mock-Stand zu inseren und armor zu kaufen, damit sie den Teil betrachten. Schließlich haben wir die gesamte Szene auf einem grünen Bildschirm gescreent.

![Unsere Bearbeiter, die Anweisungen zwischen den Anweisungen erhalten.](images/green-screen-gladiators-holotour-500px.jpg)<br>
*Unsere Bewerter, die Anweisungen zwischen den Anweisungen erhalten*

In dieser Szene werden Sie in die Box des 1. Felds platziert, was bedeutete, dass alle Materialaufnahmen aus dieser Perspektive sein mussten. Wenn wir den Film von dem Ort aus aufgenommen hätten, an dem die Schützer auf dem Brandplatz schlägen, hätten wir die Sequenz später nicht richtig zusammengesetzt, sodass wir unseren Kameraoperator in einem sehr hohen Scissor-Lift nach unten auf die Sequenz für die Drehung setzen würden.

![Abrufen der richtigen Perspektive: Filming from a scissor lift (Film von einem Scissor-Lift).](images/scissor-lift-holotour-500px.jpg)<br>
*Abrufen der richtigen Perspektive: Filming from a scissor lift*

In der Postproduktion wurden die Beschriftungen auf dem Boden zusammengesetzt, und die Perspektive war richtig, aber ein Problem bleibt bestehen: Die Schatten der Schirme auf dem grünen Bildschirm wurden im Rahmen des Kompositionsprozesses entfernt. Ohne Schatten sieht es so aus, als ob die Schützer in der Luft schwebten. Glücklicherweise ist Esestree gut, nur diese Art von Problem zu lösen, und es wurden einige technische Assistenten verwendet, um Schatten wieder in unsere Szene zu setzen. Das Ergebnis ist das, was Sie heute in der Tour sehen.

## <a name="about-the-authors"></a>Über die Autoren

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="David Haley" width="60" height="60" src="images/haley.png" /></td>
<td style="border:0" width="408"> <b>David Haley</b> ist ein Leitender Entwickler, der mehr über Kamerageräte und die Videowiedergabe gelernt hat, als er bei der Arbeit an HoloTour für möglich halten kann.</td>

<td style="border:0" width="60px"> <img alt="Jason Syltebo" width="60" height="60" src="images/syltebo.png" /></td>
<td style="border:0" width="408"> <b>Jason Siltebo</b> ist ein Audio-Designer, der sichergestellt hat, dass Sie die Soundscape jedes Ziels, das Sie besuchen, auch in der Zeit erleben können.</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Danny Askew" width="60" height="60" src="images/askew.png" /></td>
<td style="border:0" width="408"> <b>Danny Askew</b> ist ein Videoist, der sichergestellt hat, dass Ihre Reise durch Rom so gut wie möglich war.</td>

<td style="border:0" width="60px"></td>
<td style="border:0" width="408"></td>
</tr>
</table>


## <a name="see-also"></a>Siehe auch
* [Video: Microsoft HoloLens: HoloTour](https://www.youtube.com/watch?v=pLd9WPlaMpY)
