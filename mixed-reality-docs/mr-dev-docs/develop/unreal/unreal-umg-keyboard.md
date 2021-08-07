---
title: UMG und Tastatur in Unreal
description: Erfahren Sie, wie Sie unrealm Motion Graphics verwenden, um ein Benutzeroberflächensystem aus Widgets zu erstellen.
author: hferrone
ms.author: suwu
ms.date: 11/25/2020
ms.topic: article
keywords: Windows Mixed Reality, Hologramme, HoloLens 2, Blickverfolgung, Eingabe zum Anvisierten anvisierter Kopf, Unreal-Engine, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Widgets, BENUTZEROBERFLÄCHE, UMG, Unreal Motion Graphics, Unreal Engine, UE, UE4
ms.openlocfilehash: 8cb1c804757332ce7b78f0cb92cf895b873c1835208962b20d5bbbfae4684785
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212804"
---
# <a name="umg-and-keyboard-in-unreal"></a>UMG und Tastatur in Unreal

Unreal Motion Graphics (UMG) ist das integrierte Benutzeroberflächensystem der Unreal Engine, das zum Erstellen von Schnittstellen wie Menüs und Textfeldern verwendet wird. Benutzeroberflächen, die mit UMG erstellt wurden, bestehen aus Widgets. Wir führen Sie durch das Erstellen eines neuen Widgets, das Hinzufügen des Widgets zum Weltraum und das Aktivieren der Interaktion mithilfe der Systemtastatur als Beispiel. Weitere Informationen zu UMG finden Sie in der offiziellen Unreal [Engine-Dokumentation.](https://docs.unrealengine.com/en-US/Engine/UMG/index.html) 

## <a name="create-a-new-widget"></a>Erstellen eines neuen Widgets

- Erstellen Sie eine Widget-Blaupause, um die Benutzeroberfläche des Spiels zu gestalten:

![Screenshot: Hinzufügen einer Widget-Blaupause aus dem Unreal-Menü](images/unreal-umg-img-01.png)

- Öffnen Sie die neue Blaupause, und fügen Sie der Canvas Komponenten aus der Palette hinzu.  In diesem Fall haben wir zwei Textfeldkomponenten aus dem Abschnitt "Eingabe" hinzugefügt:

![Screenshot des Hierarchiefensters mit hervorgehobener und erweiterter Textwidgetkomponente](images/unreal-umg-img-02.png)

- Wählen Sie im Hierarchie- oder Designerfenster ein Widget aus, und ändern Sie die Parameter im Detailbereich.  In diesem Fall haben wir eine Standardfarbe für "Hinweistext" und eine Tönungsfarbe hinzugefügt, die angezeigt wird, wenn Sie mit dem Mauszeiger auf das Textfeld zeigen.  In einem Textfeld wird eine virtuelle Tastatur auf HoloLens angezeigt, wenn sie mit interagiert:

![Screenshot der geänderten Parameter im Hierarchiefenster](images/unreal-umg-img-03.png)

- Ereignisse können auch im Detailbereich abonniert werden:

![Screenshot der Ereignisse im Detailbereich](images/unreal-umg-img-04.png)

## <a name="add-a-widget-to-world-space"></a>Hinzufügen eines Widgets zum Weltraum

- Erstellen Sie einen neuen Actor, fügen Sie eine Widget-Komponente hinzu, und fügen Sie den Akteur der Szene hinzu:

![Screenshot eines Akteurs mit angefügtem Widget](images/unreal-umg-img-05.png)

- Legen Sie im Detailbereich für das Widget die **Widget-Klasse** auf die zuvor erstellte Widget-Blaupause fest:

![Screenshot des Bereichs "Blaupausendetails" mit dem Widgetklassensatz](images/unreal-umg-img-06.png)

- Stellen Sie für ein Textwidget sicher, dass **Die Option Hardwareeingabe empfangen** deaktiviert ist, sodass der Text nur über die virtuelle Tastatur aktualisiert wird:

![Screenshot des Interaktionsabschnitts mit deaktivierter Option "Empfangshardwareeingabe"](images/unreal-umg-img-07.png)

## <a name="widget-interaction"></a>Widgetinteraktion

UMG-Widgets empfangen in der Regel Eingaben von einer Maus.  Auf HoloLens oder VR müssen wir eine Maus mit einer Widgetinteraktionskomponente simulieren, um die gleichen Ereignisse zu erhalten.

- Erstellen Sie einen neuen Actor, fügen Sie eine **Widgetinteraktionskomponente** hinzu, und fügen Sie den Akteur Ihrer Szene hinzu:

![Screenshot eines neuen Akteurs mit hervorgehobener Widgetinteraktionskomponente](images/unreal-umg-img-08.png)

- Im Detailbereich für die Widgetinteraktionskomponente:
    - Legen Sie die Interaktionsentfernung auf den gewünschten Entfernungswert fest.
    - Festlegen der **Interaktionsquelle** auf **"Benutzerdefiniert"**
    - Legen Sie **für** die Entwicklung Debug anzeigen auf **TRUE** fest:

![Screenshot der Eigenschaften der Widgetinteraktion und des Debuggens von Komponenten](images/unreal-umg-img-09.png)

Die Standardeinstellung für Interaction Source ist "World", die Raycasts basierend auf der Weltposition der Widgetinteraktionskomponente senden sollte. In AR und VR ist dies nicht der Fall.  Das Aktivieren von "Debuggen anzeigen" und das Hinzufügen eines Farbtons mit dem Mauszeiger zu Widgets ist wichtig, um zu überprüfen, ob die Interaktionskomponente des Widgets die erwarteten Aktivitäten vornimmt.  Die Problemumgehung besteht darin, eine benutzerdefinierte Quelle zu verwenden und den Raycast aus dem Handstrahl im Ereignisdiagramm festzulegen.  

Hier rufen wir dies aus Dem Ereignist tick auf:

![Blaupause des Ereignisticks](images/unreal-umg-img-10.png)

Fügen Sie dann der Widgetinteraktionskomponente virtuelle Mauszeigerereignisse hinzu, die auf HoloLens Eingabe reagieren.  Senden Sie in diesem Fall ein Left Mouse-Press-Ereignis, wenn die Hand erkannt wird, und ein Left Mouse-Releaseereignis, wenn es nicht erkannt wird:

![Blaupause mit hinzugefügten Ereignissen für virtuelle Mauszeiger](images/unreal-umg-img-13.png)

Wenn Sie die App nun im HoloLens 2 bereitstellen, sehen Sie einen Handstrahl, der sich von ihrer rechten Hand aus erstreckt. Wenn Sie sie an eines der bearbeitbaren Textfelder und das Tippen in die Luft leiten, wird die Systemtastatur vor Ihnen angezeigt, und Sie können Text eingeben. 
 
> [!NOTE]
> Die HoloLens Systemtastatur erfordert Unreal Engine 4.26 oder höher. Darüber hinaus wird die Tastatur nicht angezeigt, wenn Ihre App nur dann vom Unreal-Editor an das Headset gestreamt wird, wenn die App auf dem Gerät ausgeführt wird.

## <a name="see-also"></a>Siehe auch:
* [UMG-Dokumentation von Unreal](https://docs.unrealengine.com/Engine/UMG/index.html)
* [UMG-Tutorials von Unreal](https://docs.unrealengine.com/Programming/Tutorials/UMG/index.html)
