---
title: Informationen zu dieser Entwurfsanleitung
description: Dieser Leitfaden wurde von Microsoft-Designern, -Entwicklern, -Programmmanagern und -Forschern verfasst, deren Arbeit holografische Geräte (wie HoloLens) und immersive Geräte (wie die Windows Mixed Reality-Headsets von Acer und HP) umfasst.
author: mrwied
ms.author: jonwie
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Design, Einführung, Anleitung, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, UX, Ressourcen
ms.openlocfilehash: 0bd70e08d55f8d556ff3a612dbbc979dc895cebbfc9950f18d8d474ff347407b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198643"
---
# <a name="about-this-design-guidance"></a>Informationen zu dieser Entwurfsanleitung

## <a name="introduction"></a>Einführung

**Hallo, und willkommen bei Ihrer Entwurfsanleitung für Mixed Reality.**

Diese Anleitung wurde von Microsoft-Designern, Entwicklern, Programmmanagern und Forschern geschrieben. Die Arbeit unserer Writer umfasst holografische Geräte, einschließlich HoloLens, immersiven Geräten undAcer- und HP-Windows Mixed Reality Headsets. Es wird empfohlen, diesen Artikel als eine Reihe von Themen für Windows design zu lesen.

Wir gehen direkt mit Ihnen in eine extrem interessante neue Zeit des Computings ein. Durchbrüche bei Monitoranzeigen, raumbezogenem Sound, Sensoren, Umgebungsbewusstsein, Eingaben und 3D-Grafiken führen und fordern uns dazu auf, neue Arten von Erfahrungen zu definieren. Die neue Grenze ist wesentlich persönlicher, intuitiver, immersiver und kontextbezogener.

Nach Möglichkeit bieten wir umsetzbare Entwurfsanleitungen mit zugehörigem Code GitHub. Da wir jedoch direkt mit Ihnen lernen, können wir hier nicht immer spezifische, umsetzbare Anleitungen anbieten. Einige der Vonnen, die wir teilen, werden in den "Lektionen, die wir gelernt haben" und "vermeiden, diesen Pfad zu gehen" sein.

Und wir wissen, dass viele Innovationen von der größeren Entwurfs-Community generiert werden. Daher freuen wir uns darauf, von Ihnen zu hören, von Ihnen zu lernen und eng mit Ihnen zusammen zu arbeiten. Wir werden unser Bestes tun, um unsere Erkenntnisse zu teilen, auch wenn sie exploratorisch und früh sind. Unser Ziel ist es, Entwicklern und Designern bei ihren Entwurfskonzepten, bewährten Methoden und den zugehörigen Open-Source-Steuerelementen, Mustern und Beispiel-Apps zu helfen, die Sie direkt in Ihrer eigenen Arbeit verwenden können.

## <a name="overview"></a>Überblick

Im Folgenden finden Sie eine kurze Übersicht über die Organisation dieses Entwurfsleitfadens:

* **[Übersicht:](design.md)** Erfahren Sie mehr über den Entwurfsprozess, die wichtigsten Konzepte und die zu berücksichtigenden Interaktionsfaktoren.
* **[Grundlegende Konzepte:](core-concepts-landingpage.md)** Erfahren Sie mehr über Komfort, holografischen Rahmen, räumliche Zuordnung und andere zu berücksichtigende Kernkonzepte.
* **[Interaktionsmodelle:](interaction-fundamentals.md)** Diese Anleitung ist um drei primäre Interaktionsmodelle strukturiert.
* **[UX-Elemente:](app-patterns-landingpage.md)** Verwenden Sie Steuerelemente und Verhaltensweisen als Bausteine, um Ihre eigene Anwendungserfahrung zu erstellen.
* **[Ressourcen:](design.md#choose-a-prototyping-option)** Starten Sie Ihr Projekt mit Entwurfstools und Prototyperstellungsoptionen.

Für alle oben genannten Informationen möchten wir die richtige Mischung aus Text, Abbildungen und Videos liefern. Sie werden sehen, wie wir mit verschiedenen Formaten und Techniken experimentieren, und das alles mit der Absicht, das zu liefern, was Sie benötigen. In den kommenden Monaten wird diese Taxonomie erweitert, um einen umfassenderen Satz von Entwurfsthemen zu erhalten. Wenn möglich, geben wir Ihnen einen Blick darauf, was als Nächstes kommen wird. Überprüfen Sie daher immer wieder.

## <a name="objectives"></a>Ziele

Hier finden Sie einen kurzen Überblick über einige ziele auf hoher Ebene, die diese Arbeit leiten, damit Sie verstehen können, woher wir kommen.

### <a name="help-solve-customer-challenges"></a>Hilfe bei der Lösung von Kundenherausforderungen

![Hilfe bei der Lösung von Kundenherausforderungen](images/500px-fix-a-broken-switch-with-hololens.jpg) <br>

Wir ringen mit vielen der gleichen Probleme wie Sie, und wir wissen, wie schwierig Ihre Arbeit ist. Es ist spannender, eine neue Grenze zu erkunden und zu definieren... und es kann auch bemutigend sein. Alte Paradigmen und Methoden werden neu gesucht, Kunden benötigen neue Erfahrungen, und es gibt so viel Potenzial für Innovation. Wir möchten, dass diese Arbeit so umfassend wie möglich ist und weit über einen Stilleitfaden hinaus geht. Wir möchten einen umfassenden Satz von Entwurfsanleitungen für Mixed Reality-Interaktion, Befehle, Navigation, Eingabe und Stil bieten– alles auf menschlichem Verhalten und Szenarien. 

### <a name="point-the-way-towards-a-new-more-human-way-of-computing"></a>Zeigen Sie den Weg zu einer neuen, menschlichen Computing-Methode

![Zeigen Sie den Weg zu einer neuen, menschlichen Computing-Methode](images/500px-man-and-women-with-holograph-on-table.png)<br>

Es ist zwar wichtig, sich auf bestimmte Kundenprobleme zu konzentrieren, aber wir möchten uns auch selbst pushen, um mehr zu liefern. Wir sind der Meinung, dass ein hervorragender Entwurf nicht nur die Problembehebung ist, sondern auch eine Möglichkeit, die menschliche Entwicklung sinnvoll zu aktivieren. Neue Methoden für menschliches Verhalten, zwischenmenschlichen Beziehungen, Aktivitäten und Umgebungen fördern unsere Innovation. Wir möchten, dass unsere Anleitung auch all diese anstirnenden Denkweisen widerspiegeln soll. 

### <a name="meet-creators-where-they-are"></a>Ersteller dort treffen, wo sie sich befinden

![Ersteller dort treffen, wo sie sich befinden](images/500px-creators.jpg) <br>

Wir hoffen, dass diese Anleitung für viele Zielgruppen hilfreich ist. Sie verfügen über verschiedene Skillsets (Anfang, Zwischenstufe, Erweitert), verwenden verschiedene Tools (Unity, DirectX, C++, C#, andere), sind mit verschiedenen Plattformen (Windows, iOS, Android) vertraut, kommen aus unterschiedlichen Hintergründen (mobil, Enterprise, Gaming) und arbeiten in verschiedenen Größenteams (Solo, Klein, Mittel, Groß). Diese Anleitung kann also mit unterschiedlichen Perspektiven und Anforderungen betrachtet werden. Nach Möglichkeit versuchen wir, diese Vielfalt im Hinterkopf zu behalten und unsere Anleitung so relevant wie möglich für so viele Personen wie möglich zu gestalten. Wir wissen, dass viele von Ihnen bereits GitHub. Wir stellen also direkt einen Link zu GitHub Repositorys und Foren, um Sie dort zu treffen, wo Sie sich bereits befinden. 

### <a name="share-as-much-as-possible-from-experimental-to-explicit"></a>Geben Sie so viel wie möglich von experimentell bis explizit weiter.

![Geben Sie so viel wie möglich von experimentell bis explizit weiter.](images/500px-man-playinggame.jpg) <br>

Eine der Herausforderungen beim Anbieten von Entwurfsleitfäden in diesem neuen 3D-Medium besteht in der, dass wir nicht immer über eine definitive Anleitung verfügen. Genau wie Sie lernen wir, experimentieren, prototypieren, lösen Probleme und passen uns an, wenn wir auf Hindernisse treffen. Anstatt auf einen sagenumklassischen zukünftigen Moment zu warten, wenn wir alles herausfinden, möchten wir unser Denken mit Ihnen in Echtzeit teilen, auch wenn es nicht heiter ist. Unser Endziel ist es, überall dort, wo wir können, definitiv zu sein und klare, flexible Entwurfsleitfäden zu bieten, die an Open-Source-Code gebunden sind und in Den Entwicklungs- und Entwurfstools von Microsoft umsetzbar sind. Aber bis zu diesem Punkt sind viele Iterations- und Lerndurchlaufe in Sicht. Wir möchten mit Ihnen interagieren und dabei mit Ihnen lernen. Wir werden unser Bestes geben, während wir losgehen, auch mit unseren Experimenten. 

### <a name="the-right-balance-of-global-and-local-design"></a>Das richtige Gleichgewicht zwischen globalem und lokalem Design

![Das richtige Gleichgewicht zwischen globalem und lokalem Design](images/500px-fluentdesign.jpg) <br>

Wir bieten zwei Entwurfsebenen an: global und lokal. Unsere "globale" Entwurfsanleitung ist in [der](https://fluent.microsoft.com)Fluent Design System. Fluent, wie wir über Grundlagen wie Licht, Tiefe, Bewegung, Material und Skalierung für alle Microsoft-Designs – unsere Geräte, Produkte, Tools und Dienste – nachdenken. In diesem größeren System gibt es jedoch erhebliche gerätespezifische Unterschiede. Daher wird in unserer "lokalen" Entwurfsanleitung für head-mounted Displays der Entwurf für holografische und immersive Geräte beschrieben, die häufig unterschiedliche Eingabe- und Ausgabemethoden sowie unterschiedliche Benutzeranforderungen und -szenarien haben. Der leitfaden für den lokalen Entwurf deckt Themen ab, die für HMDs einzigartig sind. Beispiel: 3D-Umgebungen und -Objekte; freigegebene Umgebungen; die Verwendung von Sensoren, Eyetracking und räumlicher Zuordnung; und die Möglichkeiten räumlicher Audioinhalte. Im gesamten Leitfaden werden wir wahrscheinlich sowohl auf diese globalen als auch auf die lokalen Aspekte verweisen. Dies hilft Ihnen hoffentlich dabei, Ihre Arbeit auf einer größeren Grundlage des Entwurfs zu gestalten und gleichzeitig die Entwurfsunterschiede zwischen bestimmten Geräten zu nutzen.

### <a name="have-a-discussion"></a>Diskussion

![Diskussion](images/500px-share.jpg) <br>

Vor allem möchten wir mit Ihnen, der Community von holografischen und immersiven Designern und Entwicklern, zusammenarbeiten, um diese interessante neue Designzeit zu definieren. Wie bereits erwähnt, wissen wir, dass wir nicht alle Antworten haben. Aus diesem Grund sind wir der Meinung, dass viele interessante Lösungen und Innovationen von Ihnen stammen werden. Wir sind bestrebt, offen und verfügbar zu sein, um sich darüber zu informieren, online und bei Veranstaltungen mit Ihnen zu besprechen und einen Mehrwert zu schaffen, wo immer wir können. Wir freuen uns, Teil dieser beeindruckenden Design-Community zu sein und gemeinsam ein Adventure zu unternehmen. 

## <a name="dive-in"></a>Dive in (In diesem Bereich)

Wir hoffen, dass dieser Einführungsartikel einen sinnvollen Kontext bietet, wenn Sie unsere Entwurfsanleitung untersuchen. Gehen Sie ein, und teilen Sie uns Ihre Gedanken in den GitHub-Foren mit, die Sie in unseren Artikeln finden, oder unter Microsoft Design auf [Twitter und](https://twitter.com/MicrosoftDesign) [Facebook.](https://www.facebook.com/microsoftdesign/) Lassen Sie uns die Zukunft gemeinsam gestalten!
