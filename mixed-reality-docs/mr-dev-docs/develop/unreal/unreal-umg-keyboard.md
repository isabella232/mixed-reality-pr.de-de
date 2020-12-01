---
title: Umschlag und Tastatur in Unreal
description: Erfahren Sie, wie Sie unbereichbewegungs Grafiken verwenden, um ein UI-System aus Widgets zu erstellen.
author: hferrone
ms.author: suwu
ms.date: 11/25/2020
ms.topic: article
keywords: Windows Mixed Reality, holograms, hololens 2, Eye Tracking, Blick Eingaben, Head-eingebundene Anzeige, Unreal Engine, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Widgets, UI, Umschlag, unechte Bewegungsgrafiken, Unreal Engine, UE, UE4
ms.openlocfilehash: 9f22a5f7a13732727b6b122d385aad7e708a1343
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2020
ms.locfileid: "96355320"
---
# <a name="umg-and-keyboard-in-unreal"></a>Umschlag und Tastatur in Unreal

Unreal Motion Graphics (Umschlag) ist das integrierte UI-System von Unreal Engine, das zum Erstellen von Schnittstellen wie Menüs und Textfeldern verwendet wird. Benutzeroberflächen, die mit "Umschlag" erstellt wurden, bestehen aus Widgets. In dieser Anleitung erfahren Sie, wie Sie ein neues Widget erstellen, es dem Raum hinzufügen und die Interaktion mit diesem Widget in gemischter Realität aktivieren. verwenden Sie dazu die System Tastatur als Beispiel. Weitere Informationen zu "gg" finden Sie in der offiziellen Unreal Engine- [Dokumentation](https://docs.unrealengine.com/en-US/Engine/UMG/index.html). 

## <a name="create-a-new-widget"></a>Neues Widget erstellen

- Erstellen Sie eine widgeblaupause, um die Benutzeroberfläche des Spiels zu erstellen:

![Screenshot: Hinzufügen einer widgeblaupause aus dem Unreal-Menü](images/unreal-umg-img-01.png)

- Öffnen Sie den neuen Blueprint, und fügen Sie der Canvas Komponenten aus der Palette hinzu.  In diesem Fall haben wir zwei Textfeld-Komponenten aus dem Abschnitt "Input" hinzugefügt:

![Screenshot des Fensters "Hierarchie" mit hervorgehobener und erweiterter textwidget-Komponente](images/unreal-umg-img-02.png)

- Wählen Sie im Fenster Hierarchie oder Designer ein Widget aus, und ändern Sie die Parameter im Detail Panel.  In diesem Fall haben wir einige Standardwerte für "Hinweis Text" und eine Farben hinzugefügt, wenn der Cursor über das Textfeld bewegt wird, um Feedback zu geben, mit dem das Widget interagiert werden kann.  In einem Textfeld wird eine virtuelle Tastatur auf hololens angezeigt, wenn Sie mit folgenden Aktionen interagiert:

![Screenshot der geänderten Parameter im Hierarchie Fenster](images/unreal-umg-img-03.png)

- Ereignisse können auch im Detail Panel abonniert werden:

![Screenshot der Ereignisse im Detail Panel](images/unreal-umg-img-04.png)

## <a name="add-a-widget-to-world-space"></a>Hinzufügen eines Widgets zum Raum

- Erstellen Sie einen neuen Actor, fügen Sie eine widgekomponente hinzu, und fügen Sie den Actor der Szene hinzu:

![Screenshot eines Actors mit angefügtem widget](images/unreal-umg-img-05.png)

- Legen Sie im Detailbereich für das Widget die **Widget-Klasse** auf die zuvor erstellte widgeblaupause fest:

![Screenshot des Bereichs "Blaupausen Details" mit der Widget-Klassensatz](images/unreal-umg-img-06.png)

- Vergewissern Sie sich bei einem textwidget, dass **Empfangs Hardware Eingabe** deaktiviert ist, sodass nur der zugehörige Text von der virtuellen Tastatur aktualisiert wird:

![Screenshot des Abschnitts "Interaktion" mit "Hardware Eingabe empfangen" ist nicht aktiviert](images/unreal-umg-img-07.png)

## <a name="widget-interaction"></a>Widget-Interaktion

In der Regel erhalten die-Widgets Eingaben von einer Maus.  Bei hololens oder VR müssen wir eine Maus mit einer Widget-Interaktions Komponente simulieren, um die gleichen Ereignisse zu erhalten.

- Erstellen Sie einen neuen Actor, fügen Sie eine **Widget-Interaktions** Komponente hinzu, und fügen Sie den Actor Ihrer Szene hinzu:

![Screenshot eines neuen Actors mit hervorgehobener Widget-Interaktions Komponente](images/unreal-umg-img-08.png)

- Legen Sie im Detailbereich für die Komponente für die Widget-Interaktion die Interaktions Entfernung auf den gewünschten Abstand fest, legen Sie die **Interaktions Quelle** auf **Custom** fest, und legen Sie für Entwicklung die Option **Debuggen anzeigen** auf **true** fest:

![Screenshot der Eigenschaften der Widget-Interaktion und Debugkomponente](images/unreal-umg-img-09.png)

Der Standardwert für die Interaktions Quelle ist "World", der Raycasts basierend auf der Weltposition der Widget-Interaktions Komponente senden sollte, aber in AR und VR scheint dies nicht der Fall zu sein.  Das Aktivieren von "Debuggen anzeigen" und das Hinzufügen eines Hover-tints zu Widgets während der Entwicklung ist wichtig, um zu prüfen, ob die Komponente für die Widget-Interaktion das erwartete Verhalten  Die Problem Umgehung besteht darin, eine benutzerdefinierte Quelle zu verwenden und den raycast aus dem Hand Strahl im Ereignis Diagramm festzulegen.  

Hier rufen wir dies aus dem Ereignis Takt auf:

![Blaupause von Ereignis Tick](images/unreal-umg-img-10.png)

Fügen Sie dann der Widget-Interaktions Komponente Ereignisse für virtuelle Mauszeiger hinzu, die auf hololens-Eingaben reagieren.  Senden Sie in diesem Fall ein linkes mousepress-Ereignis, wenn die Hand erfasst wird, und ein linkes mousereleaseereignis, wenn es nicht verstanden wird:

![Blaupause mit hinzugefügten Ereignissen für virtuelle Mauszeiger](images/unreal-umg-img-13.png)

Wenn Sie die App nun in den hololens 2 bereitstellen, wird ein Hand Strahl angezeigt, der von der rechten Seite aus erweitert wird. Wenn Sie den Text in einem der bearbeitbaren Textfelder und der Luft tippen, wird die Tastatur des Systems vor Ihnen angezeigt, und Sie können Text eingeben. 
 
> [!NOTE]
> Die hololens-System Tastatur erfordert Unreal Engine 4,26 oder höher. Außerdem wird die Tastatur nicht angezeigt, wenn Ihre APP aus dem Unreal-Editor nicht an das Headset gestreamt wird, sondern nur, wenn die APP auf dem Gerät ausgeführt wird.

## <a name="see-also"></a>Siehe auch:
* [Die-um-Dokumentation zu Unreal](https://docs.unrealengine.com/Engine/UMG/index.html)
* ["Ung"-Tutorials von Unreal](https://docs.unrealengine.com/Programming/Tutorials/UMG/index.html)
