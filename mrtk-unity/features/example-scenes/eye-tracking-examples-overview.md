---
title: 'Eyetracking (Blickverfolgung): Beispieleübersicht'
description: Beispiel zum Erstellen von Eyetracking in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, EyeTracking,
ms.openlocfilehash: 32ae64a470572dda71578948d5091887bea9e0e084d97ede7f2f14af596b5a6b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223218"
---
# <a name="eye-tracking-examples-overview"></a>Eyetracking (Blickverfolgung): Beispieleübersicht

In diesem Thema wird beschrieben, wie Sie schnell mit der Eyetracking in MRTK beginnen können, indem Sie auf MRTK-Eyetrackingbeispielen (Assets/MRTK/Examples/Demos/EyeTracking) aufbaut.
Mit diesen Beispielen können Sie eine unserer neuen magischen Eingabefunktionen **erleben: Eye tracking**!
Die Demo umfasst verschiedene Anwendungsfälle, die von impliziten Aktivierungen auf Augenbasis bis hin  zur nahtlosen Kombination von Informationen über das, was Sie sich ansehen, mit Sprach- und **Handeingaben** reichen.
Dadurch können Benutzer holografische Inhalte schnell und mühelos auswählen und über ihre Ansicht verschieben, indem sie einfach auf ein Ziel schauen und _"Auswählen"_ sagen oder eine Handgeste ausführen.
Die Demos enthalten auch ein Beispiel für bildlaufgesteuertes Anvieren mit den Augen, Schwenken und Zoomen von Text und Bildern auf einer Tafel.
Schließlich wird ein Beispiel für die Aufzeichnung und Visualisierung der visuellen Aufmerksamkeit des Benutzers in einer 2D-Tafel bereitgestellt.
Im folgenden Abschnitt finden Sie weitere Details zu den einzelnen Beispielen im MRTK-Beispielpaket für die Blickverfolgung (Assets/MRTK/Examples/Demos/EyeTracking):

![Liste der Eyetracking-Szenen](../images/eye-tracking/mrtk_et_list_et_scenes.jpg)

Der folgende Abschnitt enthält eine kurze Übersicht über die einzelnen Szenen der Eyetracking-Demo.
Die MRTK Eye Tracking-Demoszenen werden [additiv](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html)geladen. Im Folgenden wird die Einrichtung erläutert.

## <a name="overview-of-the-eye-tracking-demo-samples"></a>Übersicht über die Beispiele für Eyetrackingdemos

### <a name="eye-supported-target-selection"></a>[**Eye-Supported Target Selection**](../input/eye-tracking/eye-tracking-target-selection.md)

In diesem Tutorial wird der einfache Zugriff auf Daten zum Anvieren mit den Augen zum Auswählen von Zielen gezeigt.
Es enthält ein Beispiel für ein subtiles, aber leistungsstarkes Feedback, um dem Benutzer die Sicherheit zu geben, dass ein Ziel fokussiert ist, ohne zu überfordern.
Darüber hinaus gibt es ein einfaches Beispiel für intelligente Benachrichtigungen, die nach dem Lesen automatisch nicht mehr angezeigt werden.

**Zusammenfassung:** Schnelle und mühelose Zielauswahl mit einer Kombination aus Augen, Stimme und Handeingabe.

### <a name="eye-supported-navigation"></a>[**Eye-Supported Navigation**](../input/eye-tracking/eye-tracking-navigation.md)

Imagine, dass Sie einige Informationen auf einer entfernten Anzeige oder ihrem E-Reader lesen und wenn Sie das Ende des angezeigten Texts erreichen, scrollt der Text automatisch nach oben, um weitere Inhalte anzuzeigen.
Oder wie sieht es aus, direkt auf den Ort zu zoomen, an dem Sie sich das zielten?
Dies sind einige der Beispiele, die in diesem Tutorial zur brillengestützten Navigation gezeigt werden.
Darüber hinaus gibt es ein Beispiel für die freihnde Drehung von 3D-Hologrammen, indem sie basierend auf Ihrem aktuellen Fokus automatisch gedreht werden.

**Zusammenfassung:** Scrollen, Schwenken, Zoomen, 3D-Drehung mit einer Kombination aus Augen, Stimme und Handeingabe.

### <a name="eye-supported-positioning"></a>[**Eye-Supported Positioning**](../input/eye-tracking/eye-tracking-eyes-and-hands.md)

In diesem Tutorial wird ein Eingabeszenario mit dem Namen [Put-That-There](https://youtu.be/CbIn8p4_4CQ) gezeigt, das sich anfang der 1980er Jahre mit Blick-, Hand- und Stimmeingaben im MIT Media Lab recherchierte.
Die Idee ist einfach: Profitieren Sie von Ihren Augen für eine schnelle Zielauswahl und Positionierung.
Sehen Sie sich einfach ein Hologramm an, und sagen Sie _"put this",_ sehen Sie sich an, wo Sie es platzieren möchten, und sagen _Sie "there!"._
Um Ihr Hologramm genauer zu positionieren, können Sie zusätzliche Eingaben von Ihren Händen, Stimmen oder Controllern verwenden.

**Summary**: Positioning holograms using eyes, voice and hand input (*drag-and-drop*). Schieberegler mit Augen und Händen, die von den Augen unterstützt werden.

### <a name="visualization-of-visual-attention"></a>**Visualisierung der visuellen Aufmerksamkeit**

Daten, die darauf basieren, wo Benutzer aussehen, sind ein äußerst leistungsstarkes Tool, um die Verwendbarkeit eines Entwurfs zu bewerten und Probleme in effizienten Arbeitsströmen zu identifizieren.
In diesem Tutorial werden verschiedene Eyetrackingvisualisierungen und deren Anpassung an verschiedene Anforderungen erläutert.
Wir stellen grundlegende Beispiele für die Protokollierung und das Laden von Eyetrackingdaten sowie Beispiele für deren Visualisierung zur Verfügung.

**Zusammenfassung:** Zweidimensionale Aufmerksamkeitskarte (Wärmekarten) auf Tafeln. Aufzeichnen & Wiedervergennung von Eyetrackingdaten.

## <a name="setting-up-the-mrtk-eye-tracking-samples"></a>Einrichten der MRTK-Eyetrackingbeispiele

### <a name="prerequisites"></a>Voraussetzungen

Beachten Sie, dass für die Verwendung der Eyetrackingbeispiele auf dem Gerät ein HoloLens 2 und ein Beispiel-App-Paket erforderlich sind, das mit der Funktion "Eingabe anvizieren" im AppXManifest des Pakets erstellt wurde.

Um diese Eye tracking-Beispiele auf dem Gerät [](../input/eye-tracking/eye-tracking-basic-setup.md#testing-your-unity-app-on-a-hololens-2) zu verwenden, führen Sie diese Schritte aus, bevor Sie die App in Visual Studio.

### <a name="1-load-eyetrackingdemo-00-rootsceneunity"></a>1. Laden von EyeTrackingDemo-00-RootScene.unity

*EyeTrackingDemo-00-RootScene* ist die Basisszene _(Stamm)_ mit allen MRTK-Kernkomponenten.
Dies ist die Szene, die Sie zuerst laden müssen und aus der Sie die Eyetracking-Demos ausführen.
Es verfügt über ein grafisches Szenenmenü, mit dem Sie problemlos zwischen den verschiedenen Eyetrackingbeispielen wechseln können, die [additiv geladen werden.](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html)

![Szenenmenü im Eyetrackingbeispiel](../images/eye-tracking/mrtk_et_scenemenu.jpg)

Die Stammszene enthält einige Kernkomponenten, die über die additiv geladenen Szenen hinweg beibehalten werden, z. B. die vom MRTK konfigurierten Profile und die Szenenkamera.
_MixedRealityBasicSceneSetup_ (siehe Screenshot unten) enthält ein Skript, mit dem die referenzierte Szene beim Start automatisch geladen wird.
Standardmäßig ist dies _EyeTrackingDemo-02-TargetSelection._  

![Beispiel für das OnLoadStartScene-Skript](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

### <a name="2-adding-scenes-to-the-build-menu"></a>2. Hinzufügen von Szenen zum Buildmenü

Um additive Szenen während der Laufzeit zu laden, müssen Sie diese Szenen zuerst dem Menü Build Einstellungen _-> Scenes in Build_ hinzufügen.
Es ist wichtig, dass die Stammszene als erste Szene in der Liste angezeigt wird:

![Erstellen Einstellungen Szenenmenüs für Eyetrackingbeispiele](../images/eye-tracking/mrtk_et_build_settings.jpg)

### <a name="3-play-the-eye-tracking-samples-in-the-unity-editor"></a>3. Wiedergabe der Eyetrackingbeispiele im Unity-Editor

Nachdem Sie dem Build-Einstellungen die EyeTracking-Szenen hinzugefügt und _eyeTrackingDemo-00-RootScene_ geladen haben, sollten Sie noch einen letzten Punkt überprüfen: Ist das Skript _"OnLoadStartScene",_ das an _das MixedRealityBasicSceneSetup-GameObject_ angefügt ist, aktiviert? Dies soll die Stammszene darüber informieren, welche Demoszene zuerst geladen werden soll.

![Beispiel für das OnLoad_StartScene Skript](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

Jetzt rollen wir! Treffer _"Play"_!
Es sollten mehrere Gems und das Szenenmenü oben angezeigt werden.

![Beispiel screenshot from the ET target select scene (Beispielabbildung aus der Auswahlszene des ET-Ziels)](../images/eye-tracking/mrtk_et_targetselect.png)

Sie sollten auch einen kleinen halbtransparenten Kreis in der Mitte der Spielansicht bemerken.
Dies fungiert als Indikator (Cursor) Ihres simulierten Anvistiks mit den _Augen:_ Drücken Sie einfach die rechte Maustaste, und bewegen Sie die Maus, um ihre Position zu ändern. 
Wenn der Cursor auf die Gems zeigt, werden Sie feststellen, dass er an der Mitte des aktuell angezeigten Gems andockt.
Dies ist eine hervorragende Möglichkeit, um zu testen, ob Ereignisse wie erwartet ausgelöst werden, wenn ein Ziel _"betrachtet"_ wird.
Beachten Sie, dass _das simulierte_ Anvieren mit den Augen über die Maussteuerung eine eher schlechte Ergänzung unserer schnellen und unbeabsichtigten Augenbewegungen ist.
Sie ist jedoch ideal, um die grundlegende Funktionalität zu testen, bevor Sie den Entwurf durch Bereitstellen auf dem HoloLens 2 iterieren.
Zurück zur Eyetracking-Beispielszene: Das Gem dreht sich, solange es betrachtet wird, und kann zerstört werden, indem es "betrachtet" und ...

- Drücken _der EINGABETASTE_ (wodurch das "Auswählen" simuliert wird)
- _"Select" (Auswählen)_ in Ihr Mikrofon
- Klicken Sie beim _Drücken_ des Leerzeichens zum Anzeigen der simulierten Handeingabe auf die linke Maustaste, um eine simulierte Stecknadel durchzuführen.

Ausführlichere Informationen dazu, wie Sie diese Interaktionen erreichen können, finden Sie in unserem Tutorial zur Zielauswahl [**mit**](../input/eye-tracking/eye-tracking-target-selection.md) Blickgestützter Unterstützung.

Wenn Sie den Cursor auf die obere Menüleiste in der Szene bewegen, werden Sie feststellen, dass das element, auf das gerade mit dem Mauszeiger gezeigert wird, subtly hervorhebt.
Sie können das derzeit hervorgehobene Element mithilfe einer der oben beschriebenen Commitmethoden auswählen (z. B. durch Drücken der _EINGABETASTE)._
Auf diese Weise können Sie zwischen den verschiedenen Eyetracking-Beispielszenen wechseln.

### <a name="4-how-to-test-specific-sub-scenes"></a>4. Testen bestimmter Unterszenen

Wenn Sie an einem bestimmten Szenario arbeiten, sollten Sie nicht jedes Mal das Szenenmenü durchgehen.
Stattdessen sollten Sie direkt mit der Szene beginnen, an der Sie gerade arbeiten, wenn Sie auf die _Wiedergabeschaltfläche_ klicken.
Kein Problem. Sie haben dies:

1. Laden der _Stammszene_
2. Deaktivieren Sie _in der_ Stammszene das _Skript "OnLoadStartScene"._
3. _Drag and drop_ one of the eye tracking test scenes that are described below (or any other scene) into your _Hierarchy_ view as shown in the screenshot below.

    ![Beispiel für additive Szene](../images/eye-tracking/mrtk_et_additivescene.jpg)

4. Wiedergabe _drücken_

Beachten Sie, dass das Laden der Untergeordneten Szene wie diese nicht persistent ist: Wenn Sie Ihre App auf dem HoloLens 2-Gerät bereitstellen, wird nur die Stammszene geladen (vorausgesetzt, sie wird am oberen Ende Ihrer Build-Einstellungen).
Wenn Sie Ihr Projekt für andere freigeben, werden die Unterszenen auch nicht automatisch geladen.

---

Nachdem Sie nun wissen, wie Sie die MRTK-Eyetracking-Beispielszenen verwenden können, gehen wir mit der Auswahl von Hologrammen mit Ihren Augen weiter: Von den Augen unterstützte [Zielauswahl.](../input/eye-tracking/eye-tracking-target-selection.md)

---
[Zurück zu "Eye tracking in the MixedRealityToolkit"](../input/eye-tracking/eye-tracking-Main.md)
