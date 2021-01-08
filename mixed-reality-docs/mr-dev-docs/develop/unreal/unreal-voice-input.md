---
title: Spracheingabe in Unreal
description: Erfahren Sie, wie Sie Spracheingaben, sprach Zuordnungen und erkennungsungen in Unreal Mixed Reality-Apps für hololens 2-Geräte einrichten und verwenden.
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, Unreal, Unreal Engine 4, UE4, hololens 2, Voice, Voice Input, Spracherkennung, gemischte Realität, Entwicklung, Features, Dokumentation, Leitfäden, holograms, Spieleentwicklung, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: c7ac523258dc44aa261470aea8cdf21f32c915b2
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010070"
---
# <a name="voice-input-in-unreal"></a>Spracheingabe in Unreal

Mit der Spracheingabe in Unreal können Sie mit einem – Hologramm interagieren, ohne Handgesten zu verwenden, und es wird nur hololens 2 unterstützt. Spracheingaben auf hololens 2 werden von derselben Engine unterstützt, die Sprache in allen anderen universellen Windows-Apps unterstützt, aber Unreal verwendet ein eingeschränkteren Modul, um die Spracheingabe zu verarbeiten. Dies schränkt die Spracheingabe Features in Unreal auf vordefinierte sprach Zuordnungen ein, die in den folgenden Abschnitten behandelt werden. 

## <a name="enabling-speech-recognition"></a>Aktivieren der Spracherkennung

So aktivieren Sie die Spracherkennung in hololens:
1. Wählen Sie **Projekteinstellungen > Plattform > hololens > Funktionen** aus, und aktivieren Sie das **Mikrofon**. 
2. Aktivieren Sie die Spracherkennung in den **Einstellungen > Datenschutz > Sprache** und wählen Sie **Englisch** aus.

> [!NOTE]
> Die Spracherkennung funktioniert immer in der in der App " **Einstellungen** " konfigurierten Windows-Anzeige Sprache. Es wird empfohlen, dass Sie auch die **Online Spracherkennung** für die beste Dienst Qualität aktivieren.

![Einstellungen für die Windows-Spracherkennung](images/unreal/speech-recognition-settings.png)

3. Ein Dialogfeld wird angezeigt, wenn die Anwendung zum ersten Mal gefragt wird, ob Sie das Mikrofon aktivieren möchten. Wenn Sie **Ja** auswählen, wird die Spracheingabe in der APP gestartet.

Die Spracheingabe erfordert keine speziellen Windows Mixed Reality-APIs. Es basiert auf der vorhandenen API für die [Eingabe](https://docs.unrealengine.com/Gameplay/Input/index.html) Zuordnung von Unreal Engine 4. 

## <a name="adding-speech-mappings"></a>Hinzufügen von sprach Zuordnungen

Das Verbinden von Sprache und Aktion ist ein wichtiger Schritt bei der Verwendung von Spracheingaben. Diese Zuordnungen überwachen die APP auf sprach Schlüsselwörter, die ein Benutzer möglicherweise anweist, und lösen dann eine verknüpfte Aktion aus. Sie finden sprach Zuordnungen wie folgt:
1. Wählen Sie **> Projekteinstellungen bearbeiten** aus, Scrollen Sie zum Abschnitt **Engine** , und klicken Sie auf **Eingabe**.

So fügen Sie eine neue sprach Zuordnung für einen Jump-Befehl hinzu:
1. Wählen Sie das **+** Symbol neben **Array Elemente** aus, und geben Sie die folgenden Werte ein:
    * **jumpword** für **Aktions Name**
    * **springen** für **sprach Schlüsselwort**

> [!NOTE]
> Alle englischen Wörter oder kurzsätze können als Schlüsselwort verwendet werden. 

![Eingabeeinstellungen der UE4-Engine](images/unreal/engine-input.png)

Sprach Zuordnungen können als Eingabe Komponenten wie Aktions-oder Achsen Zuordnungen oder als Blueprint-Knoten im Ereignis Diagramm verwendet werden. Beispielsweise können Sie den Jump-Befehl verknüpfen, um zwei verschiedene Protokolle auszugeben, je nachdem, wann das Wort gesprochen wird:

1. Doppelklicken Sie auf eine Blaupause, um Sie im **Ereignis Diagramm** zu öffnen.
2. **Klicken Sie mit der rechten Maustaste** , und suchen Sie nach dem **Aktions Namen** ihrer sprach Zuordnung (in diesem Fall **jumpword**), und drücken **Sie** dann die EINGABETASTE, um dem Diagramm einen **Eingabe Aktions** Knoten hinzuzufügen.
3. Ziehen Sie die **gedrückte** PIN per Drag & Drop auf den Knoten **Druck Zeichenfolge** , wie in der folgenden Abbildung dargestellt Sie können die **freigegebene** Pin leer lassen, ohne dass für sprach Zuordnungen etwas ausgeführt wird.
 
![Einfache Aktion für Stimme](images/unreal/voice-input-img-03.png)

4. Spielen Sie die APP, sagen Sie das Wort **springt**, und sehen Sie sich an, dass die Konsole die Protokolle ausgibt.

Das ist alles, was Sie benötigen, um Ihren hololens-apps in Unreal Spracheingaben hinzuzufügen. Weitere Informationen zu Sprache und Interaktivität finden Sie unter den folgenden Links, und Sie sollten sich über die Benutzeroberflächen Gedanken machen, die Sie für Ihre Benutzer erstellen.

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie die unwirkliche Entwicklungs Journey befolgen, die wir festgelegt haben, haben Sie die nächste Aufgabe darin, die Funktionen und APIs der Mixed Reality-Plattform zu untersuchen: 

> [!div class="nextstepaction"]
> [HoloLens-Kamera](unreal-hololens-camera.md)

Sie können jederzeit zu den [Prüfpunkten für die Unreal-Entwicklung](unreal-development-overview.md#2-core-building-blocks) zurückkehren.

## <a name="see-also"></a>Siehe auch
* [Spracheingabe](../../design/voice-input.md)
* [Anvisieren und Ausführen](../../design/gaze-and-commit.md)
* [Instinktive Interaktionen](../../design/interaction-fundamentals.md)

