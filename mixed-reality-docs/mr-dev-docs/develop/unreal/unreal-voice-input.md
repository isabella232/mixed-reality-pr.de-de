---
title: Spracheingabe in Unreal
description: Erfahren Sie, wie Sie Spracheingaben, Sprachzuordnungen und Erkennung in Unreal Mixed Reality-Apps für HoloLens 2 verwenden.
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, Unreal, Unreal Engine 4, UE4, HoloLens 2, Stimme, Spracheingabe, Spracherkennung, Mixed Reality, Entwicklung, Features, Dokumentation, Leitfäden, Hologramme, Spieleentwicklung, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 12d0c595b5319da50e119f4a2463e2ca3e07ce449f11d6fd266c5f988d180465
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221008"
---
# <a name="voice-input-in-unreal"></a>Spracheingabe in Unreal

Die Spracheingabe in Unreal ermöglicht es Ihnen, mit einem Hologramm zu interagieren, ohne Handgesten verwenden zu müssen, und wird nur HoloLens 2. Die Spracheingabe auf HoloLens 2 wird von derselben Engine unterstützt, die Sprache in allen anderen universellen Windows-Apps unterstützt. Unreal verwendet jedoch eine eingeschränktere Engine zur Verarbeitung von Spracheingaben. Dadurch werden die Spracheingabefunktionen in Unreal auf vordefinierte Sprachzuordnungen beschränkt, die in den folgenden Abschnitten behandelt werden. 

## <a name="enabling-speech-recognition"></a>Aktivieren der Spracherkennung

Wenn Sie das Windows Mixed Reality-Plug-In verwenden, sind für die Spracheingabe keine speziellen Windows Mixed Reality-APIs erforderlich. Sie basiert auf der vorhandenen Eingabezuordnungs-API der Unreal Engine [4.](https://docs.unrealengine.com/Gameplay/Input/index.html) Wenn Sie OpenXR verwenden, sollten Sie zusätzlich [das Microsoft OpenXR-Plug-In installieren.](https://github.com/microsoft/Microsoft-OpenXR-Unreal) 

So aktivieren Sie die Spracherkennung HoloLens
1. Wählen **sie Project Einstellungen > Platform > HoloLens > Capabilities (> HoloLens > Plattformfunktionen) aus,** und aktivieren Sie **Mikrofon**. 
2. Aktivieren Sie die Spracherkennung in **Einstellungen > Privacy > Speech,** und wählen Sie **Englisch aus.**

> [!NOTE]
> Die Spracherkennung funktioniert immer in der Windows Anzeigesprache, die in der App **Einstellungen** ist. Es wird empfohlen, auch die **Online-Spracherkennung zu aktivieren,** um die beste Dienstqualität zu erhalten.

![Windows Einstellungen für die Spracherkennung](images/unreal/speech-recognition-settings.png)

3. Ein Dialogfeld wird angezeigt, wenn die Anwendung zum ersten Mal fragt, ob Sie das Mikrofon aktivieren möchten. Wenn Sie **Ja auswählen,** wird die Spracheingabe in der App gestartet.

## <a name="adding-speech-mappings"></a>Hinzufügen von Sprachzuordnungen

Das Verbinden von Sprache mit Aktion ist ein wichtiger Schritt bei der Verwendung der Spracheingabe. Diese Zuordnungen überwachen die App auf Sprachschlüsselwörter, die ein Benutzer sagen könnte, und deaktivieren dann eine verknüpfte Aktion. Sie finden Sprachzuordnungen wie hier:
1. Wählen Sie **Bearbeiten > Project Einstellungen** aus, scrollen Sie zum **Abschnitt Engine,** und klicken Sie auf **Eingabe.**

So fügen Sie eine neue Sprachzuordnung für einen Sprungbefehl hinzu:
1. Wählen Sie das **+** Symbol neben **Arrayelemente aus,** und geben Sie die folgenden Werte ein:
    * **jumpWord** für **Aktionsname**
    * **Jump for** **Speech-Schlüsselwort**

> [!NOTE]
> Alle englischen Wörter oder kurzen Sätze können als Schlüsselwort verwendet werden. 

![UE4 Engine Input Einstellungen](images/unreal/engine-input.png)

Sprachzuordnungen können als Eingabekomponenten wie Aktions- oder Achsenzuordnungen oder als Blaupausenknoten im Ereignis-Graph. Sie können z. B. den Sprungbefehl verknüpfen, um zwei verschiedene Protokolle aus drucken, je nachdem, wann das Wort gesprochen wird:

1. Doppelklicken Sie auf eine Blaupause, um sie im **Ereignis-Graph.**
2. **Klicken Sie mit der rechten** Maustaste, und suchen Sie nach dem Aktionsnamen  Ihrer Sprachzuordnung (in diesem Fall **jumpWord),** und klicken Sie dann auf DIE **EINGABETASTE,** um dem Diagramm einen Knoten Eingabeaktion hinzuzufügen. 
3. Drag and drop the **Pressed** pin to **Print String** node as shown in the image below. Sie können den Pin **Released** leer lassen. Für Sprachzuordnungen wird nichts ausgeführt.
 
![Einfache Aktion für Sprache](images/unreal/voice-input-img-03.png)

4. Spielen Sie die App wieder, sagen Sie das Wort **Jump,** und beobachten Sie, wie die Konsole die Protokolle ausdruckt!

Das ist alles, was Sie einrichten müssen, um Spracheingaben zu Ihren HoloLens-Apps in Unreal hinzufügen zu können. Weitere Informationen zu Sprache und Interaktivität finden Sie unter den folgenden Links, und denken Sie unbedingt an die Benutzererfahrung, die Sie für Ihre Benutzer erstellen.

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie den von uns entwickelten Weg zur Unreal-Entwicklung folgen, sind Sie die nächste Aufgabe, die Funktionen und APIs Mixed Reality Plattform zu erkunden: 

> [!div class="nextstepaction"]
> [HoloLens-Kamera](unreal-hololens-camera.md)

Sie können jederzeit zu den [Prüfpunkten für die Unreal-Entwicklung](unreal-development-overview.md#2-core-building-blocks) zurückkehren.

## <a name="see-also"></a>Siehe auch
* [Spracheingabe](../../design/voice-input.md)
* [Anvisieren und Ausführen](../../design/gaze-and-commit.md)
* [Instinktive Interaktionen](../../design/interaction-fundamentals.md)

