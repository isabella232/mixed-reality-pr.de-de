---
title: Informationen zu dieser Entwurfsanleitung
description: Dieser Leitfaden wurde von Microsoft-Designern, -Entwicklern, -Programmmanagern und -Forschern verfasst, deren Arbeit holografische Geräte (wie HoloLens) und immersive Geräte (wie die Windows Mixed Reality-Headsets von Acer und HP) umfasst.
author: mrwied
ms.author: jonwie
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Design, Introduction, Guidance, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, UX, Ressourcen
ms.openlocfilehash: f731ad91d48cdb50ad12b6a9cc250b6561eebaff
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847687"
---
# <a name="about-this-design-guidance"></a>Informationen zu dieser Entwurfsanleitung

## <a name="introduction"></a>Einführung

**Hallo, und Willkommen bei Ihrem Entwurfs Leit Faden für gemischte Realität.**

Diese Anleitung wird von Microsoft-Designern, Entwicklern, Programmmanagern und Forschern verfasst. Die Arbeit unserer Writer umfasst holografische Geräte, einschließlich hololens, immersive Geräte, andacer und HP Windows Mixed Reality-Headsets. Es wird empfohlen, diesen Artikel als einen Satz von Themen für den mit dem Head bereitgestellten Windows-Entwurf zu betrachten.

Wir werden direkt mit Ihnen einen überaus aufregenden neuen Zeitraum für die computingzeit eingeben. Unter Brüche in den bereitgestellten anzeigen, räumlichen Sound, Sensoren, Umweltbewusstsein, Eingabe und 3D-Grafiken führen Sie aus und fordern uns auf, neue Arten von Erfahrungen zu definieren. Die neue Grenze ist erheblich persönlicher, intuitiver, immersiver und kontextbezogen.

Nach Möglichkeit bieten wir Ihnen einen aussagekräftigen Entwurfs Leit Faden mit verknüpften Code auf GitHub. Da wir direkt mit Ihnen zusammenarbeiten, können wir hier nicht immer bestimmte, Handlungs relevante Anleitungen anbieten. Einige der freigegebenen Elemente werden im Sinne von "Lektionen, die wir gelernt haben" und "vermeiden, dass dieser Pfad ausfällt".

Und wir wissen, dass viele Innovationen von der größeren Entwurfs Community generiert werden. Wir freuen uns, von Ihnen zu hören, von Ihnen zu lernen und eng mit Ihnen zusammenzuarbeiten. Wir werden unsere Erkenntnisse am besten teilen, auch wenn Sie explorativ und frühzeitig sind. Unser Ziel ist es, Entwicklern und Designern Ihre Entwurfs denkenden, bewährten Methoden sowie die zugehörigen Open Source-Steuerelemente, Muster und Beispiel-apps zu unterstützen, die Sie direkt in ihrer eigenen Arbeit verwenden können.

## <a name="overview"></a>Übersicht

Im folgenden finden Sie eine kurze Übersicht über die Organisation dieses Entwurfs Leitfadens:

* **[Übersicht](design.md)** : erfahren Sie mehr über den Entwurfsprozess, die Kernkonzepte und die Interaktions Faktoren, die berücksichtigt werden müssen.
* **[Grundlegende Konzepte](core-concepts-landingpage.md)** : erfahren Sie mehr über Komfort, Holographic Frame, räumliche Zuordnung und andere wichtige Konzepte, die berücksichtigt werden müssen.
* **[Interaktionsmodelle](interaction-fundamentals.md)** : Diese Anleitung ist in drei Haupt Interaktions Modellen gegliedert.
* **[UX-Elemente](app-patterns-landingpage.md)** : Verwenden Sie Steuerelemente und Verhaltensweisen als Bausteine zum Erstellen Ihrer eigenen Anwendungserfahrung.
* **[Ressourcen](design.md#choose-a-prototyping-option)** : Starten Sie Ihr Projekt mit Entwurfs Tools und Prototypen-Optionen.

Für alle oben genannten Ziele wird die richtige Mischung aus Text, Abbildungen und Videos bereitzustellen. Sie werden sehen, dass wir mit unterschiedlichen Formaten und Techniken experimentieren und alles mit der Absicht bereitstellen, was Sie benötigen. In den kommenden Monaten wird diese Taxonomie erweitert, um einen umfassenderen Satz von Entwurfs Themen einzubeziehen. Nachdem möglich haben wir Ihnen einen Überblick über das nächste Mal, also schauen wir uns das Mal an.

## <a name="objectives"></a>Ziele

Hier sehen Sie eine kurze Übersicht über einige allgemeine Ziele, die diese Arbeit leiten, damit Sie verstehen können, woher wir kommen.

### <a name="help-solve-customer-challenges"></a>Hilfe bei der Lösung von Kundenproblemen

![Hilfe bei der Lösung von Kundenproblemen](images/500px-fix-a-broken-switch-with-hololens.jpg) <br>

Wir führen viele der gleichen Probleme aus, und wir verstehen, wie ihre Arbeit schwierig ist. Es ist aufregend, eine neue Grenze zu erforschen und zu definieren... Außerdem kann es sich als beängstigend erweisen. Alte Paradigmen und Verfahren werden wiederholt, Kunden benötigen neue Erfahrungen, und es gibt so viele Möglichkeiten für Innovationen. Wir möchten, dass diese Arbeit so umfassend wie möglich ist, und Sie sollten sich über einen Stil Leit Faden hinaus bewegen. Wir sind bestrebt, einen umfassenden Satz von Entwurfs Anleitungen bereitzustellen, in denen gemischte Interaktionen, Befehle, Navigation, Eingaben und Stil behandelt werden – alle auf menschliches Verhalten und Szenarios basieren. 

### <a name="point-the-way-towards-a-new-more-human-way-of-computing"></a>Zeigen Sie auf eine neue, menschlichere Art von Computing

![Zeigen Sie auf eine neue, menschlichere Art von Computing](images/500px-man-and-women-with-holograph-on-table.png)<br>

Obwohl es wichtig ist, sich auf bestimmte Kunden Probleme zu konzentrieren, möchten wir uns auch selbst pushen, um weitere Informationen zu erhalten. Wir glauben, dass es sich bei dem Design nicht um die Problembehebung handelt. Neue Möglichkeiten für menschliches Verhalten, zwischenmenschliche Beziehungen, Aktivitäten und Umgebungen fördern unsere Innovationen. Wir möchten, dass unser Leitfaden all diese stärker anzurufenden Ansätze widerspiegelt. 

### <a name="meet-creators-where-they-are"></a>Treffen Sie Ersteller, wo Sie

![Treffen Sie Ersteller, wo Sie](images/500px-creators.jpg) <br>

Wir hoffen, dass viele Zielgruppen diese Anleitung finden, um hilfreich zu sein. Sie verfügen über unterschiedliche Fertigkeiten (Anfang, Fortgeschrittene, erweitert), verwenden verschiedene Tools (Unity, DirectX, C++, c#, andere), sind mit verschiedenen Plattformen (Windows, Ios, Android) vertraut und stammen aus unterschiedlichen Hintergründen (Mobile, Enterprise, Gaming) und arbeiten an verschiedenen Größen Teams ("Solo", "Small", "Medium"). Diese Anleitung kann also mit unterschiedlichen Perspektiven und Anforderungen angezeigt werden. Nach Möglichkeit werden wir versuchen, diese Vielfalt zu berücksichtigen und unseren Leitfaden so wichtig wie möglich für so viele Personen wie möglich zu gestalten. Wir wissen, dass viele von Ihnen bereits auf GitHub vorhanden sind. Wir werden also direkt mit GitHub-retorys und Foren verknüpft, um Ihnen die Stelle zu begegnen, an der Sie bereits sind. 

### <a name="share-as-much-as-possible-from-experimental-to-explicit"></a>So viel wie möglich von experimentellen bis expliziten teilen

![So viel wie möglich von experimentellen bis expliziten teilen](images/500px-man-playinggame.jpg) <br>

Eine der Herausforderungen bei der Bereitstellung eines Entwurfs Leitfadens in diesem neuen 3D-Medium besteht darin, dass wir nicht immer definitive Anleitungen zum Angebot haben. Ebenso wie Sie lernen, experimentieren, Prototypen, Problembehebung und Anpassung, wenn wir auf Hindernisse stoßen. Anstatt auf eine mythliche Zukunft zu warten, in der wir alles herausgefunden haben, wollen wir unsere Meinung in Echtzeit teilen, auch wenn Sie nicht eindeutig ist. Unser Ziel ist es, an jedem Punkt genau zu sein, und Sie können eine klare, flexible Entwurfs Anleitung bereitstellen, die an Open Source-Code gebunden ist und in Entwicklungs-und Entwurfs Tools von Microsoft handlungsfähig ist. Das Erreichen dieses Punkts dauert jedoch viele Runden an Iterationen und Lern Vorgängen. Wir möchten uns mit Ihnen in Verbindung treten und mit Ihnen zusammenarbeiten. Wir werden unsere bestmögliche Freigabe tun, auch wenn unsere experimentellen Inhalte experimentell sind. 

### <a name="the-right-balance-of-global-and-local-design"></a>Das richtige Gleichgewicht des globalen und des lokalen Entwurfs

![Das richtige Gleichgewicht des globalen und des lokalen Entwurfs](images/500px-fluentdesign.jpg) <br>

Wir bieten zwei Entwurfs Leit Fäden: Global und local. Unser "Global"-Entwurfs Leit Faden ist im [System für das fließende Design](https://fluent.microsoft.com)enthalten. Es wird ausführlich erläutert, wie wir über Grundlagen wie Light, Tiefe, Bewegung, Material und Skalierung für alle Microsoft-Entwürfe nachzudenken, unsere Geräte, Produkte, Tools und Dienste. Dies bedeutet, dass in diesem größeren System erhebliche gerätespezifische Unterschiede vorhanden sind. Der "local"-Entwurfs Leit Faden für die in der Eingabe eingebundenen anzeigen beschreibt den Entwurf für holografische und immersive Geräte, die häufig über verschiedene Eingabe-und Ausgabemethoden und verschiedene Benutzer Anforderungen und-Szenarien verfügen. Leitfaden zum lokalen Design behandelt die für HMDs eindeutigen Themen. Beispiel: 3D-Umgebungen und-Objekte; freigegebene Umgebungen; Verwendung von Sensoren, Augen Verfolgung und räumlicher Zuordnung und die Möglichkeiten räumlicher Audiodaten. Im Rahmen unserer Anleitung sehen Sie wahrscheinlich, dass wir sowohl auf die globalen als auch auf die lokalen Aspekte verweisen. Hoffentlich hilft Ihnen dies, ihre Arbeit in einer größeren Entwurfs Grundlage zu unterstützen und gleichzeitig die Entwurfs Unterschiede zwischen bestimmten Geräten zu nutzen.

### <a name="have-a-discussion"></a>Diskussion

![Diskussion](images/500px-share.jpg) <br>

Am wichtigsten ist, dass wir uns mit Ihnen, der Community von Holographic und immersiven Designern und Entwicklern in Verbindung treten möchten, um diesen neuen Entwurfs Zeitraum zu definieren. Wie bereits erwähnt, wissen wir, dass wir nicht alle Antworten haben. Aus diesem Grund werden wir glauben, dass viele interessante Lösungen und Innovationen von Ihnen kommen. Wir sind bestrebt, offen und verfügbar zu sein, um zu erfahren, wie Sie mit Ihnen Online und bei Veranstaltungen besprechen können, und Sie können jederzeit den Wert hinzufügen. Wir freuen uns, ein Teil dieser beeindruckenden Entwurfs Community zu sein, die ein Adventure zusammenfasst. 

## <a name="dive-in"></a>Einblick in

Wir hoffen, dass dieser Einführungs Artikel einen sinnvollen Kontext bietet, während Sie unsere Entwurfs Leit Fäden kennenlernen. Informieren Sie sich, und teilen Sie uns Ihre Gedanken in den GitHub-Foren mit, die Sie in unseren Artikeln finden, oder bei Microsoft Design auf [Twitter](https://twitter.com/MicrosoftDesign) und [Facebook](https://www.facebook.com/microsoftdesign/). Lassen Sie uns die Zukunft gemeinsam entwerfen!
