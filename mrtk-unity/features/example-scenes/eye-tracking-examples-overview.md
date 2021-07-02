---
title: Übersicht über Eyetrackingbeispiele
description: Beispiel zum Erstellen von Eyetracking in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, EyeTracking,
ms.openlocfilehash: 4cdeaa10725e00ac1a041c3692d64c1bd6488854
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175544"
---
# <a name="eye-tracking-examples-overview"></a>Übersicht über Eyetrackingbeispiele

In diesem Thema wird beschrieben, wie Sie schnell mit eye tracking in MRTK beginnen können, indem Sie auf MRTK-Eyetrackingbeispielen (Assets/MRTK/Examples/Demos/EyeTracking) aufbauen.
Mit diesen Beispielen können Sie eine unserer neuen magischen Eingabefunktionen erleben: **Eye tracking**!
Die Demo enthält verschiedene Anwendungsfälle, die von impliziten augenbasierten Aktivierungen bis hin zur nahtlosen Kombination von Informationen zu dem, was Sie betrachten, mit **Sprach-** und **Handeingaben** reichen.
Dadurch können Benutzer holografische Inhalte schnell und mühelos auswählen und über ihre Ansicht verschieben, indem sie einfach ein Ziel betrachten und _"Auswählen"_ sagen oder eine Handgeste ausführen.
Die Demos enthalten auch ein Beispiel für bildlaufgesteuertes Anvieren mit den Augen, Schwenken und Zoomen von Text und Bildern auf einer Schiefer.
Schließlich wird ein Beispiel für die Aufzeichnung und Visualisierung der visuellen Aufmerksamkeit des Benutzers auf einer 2D-Schiefer bereitgestellt.
Im folgenden Abschnitt finden Sie weitere Details zu den einzelnen Beispielen im MRTK-Beispielpaket zur Blickverfolgung (Assets/MRTK/Examples/Demos/EyeTracking):

![Liste der Blickverfolgungsszenen](../images/eye-tracking/mrtk_et_list_et_scenes.jpg)

Der folgende Abschnitt enthält eine kurze Übersicht über die einzelnen Eyetracking-Demoszenen.
Die MRTK-Blickverfolgungs-Demoszenen werden [additiv geladen,](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html)was im Folgenden erläutert wird, wie sie eingerichtet werden.

## <a name="overview-of-the-eye-tracking-demo-samples"></a>Übersicht über die Eyetracking-Demobeispiele

### <a name="eye-supported-target-selection"></a>[**Durch die Augen unterstützte Zielauswahl**](../input/eye-tracking/eye-tracking-target-selection.md)

In diesem Tutorial wird veranschaulicht, wie einfach der Zugriff auf Daten zum Anvisierten der Augen zum Auswählen von Zielen ist.
Es enthält ein Beispiel für ein dezentes, aber leistungsstarkes Feedback, um dem Benutzer das Vertrauen zu geben, dass ein Ziel fokussiert ist, ohne überwältigend zu sein.
Darüber hinaus gibt es ein einfaches Beispiel für intelligente Benachrichtigungen, die nach dem Lesen automatisch ausgeblendet werden.

**Zusammenfassung:** Schnelle und mühelose Zielauswahl mithilfe einer Kombination aus Augen, Stimme und Handeingabe.

### <a name="eye-supported-navigation"></a>[**Durch die Augen unterstützte Navigation**](../input/eye-tracking/eye-tracking-navigation.md)

Imagine, dass Sie einige Informationen auf einer entfernten Anzeige oder ihrem E-Reader lesen und wenn Sie das Ende des angezeigten Texts erreichen, scrollt der Text automatisch nach oben, um weitere Inhalte anzuzeigen.
Oder wie sieht es mit dem magischen Zoomen direkt an dem Ort aus, an dem Sie sich befanden?
Dies sind einige der Beispiele, die in diesem Tutorial zur durch die Augen unterstützten Navigation vorgestellt werden.
Darüber hinaus gibt es ein Beispiel für die freihändige Drehung von 3D-Hologrammen, indem sie basierend auf Ihrem aktuellen Fokus automatisch gedreht werden.

**Zusammenfassung: Scrollen,** Schwenken, Zoomen, 3D-Drehung mithilfe einer Kombination aus Augen, Stimme und Handeingabe.

### <a name="eye-supported-positioning"></a>[**Durch die Augen unterstützte Positionierung**](../input/eye-tracking/eye-tracking-eyes-and-hands.md)

In diesem Tutorial wird ein Eingabeszenario mit dem Namen [Put-That-There](https://youtu.be/CbIn8p4_4CQ) gezeigt, das anfang der 1980er Jahre mit Augen-, Hand- und Spracheingaben auf die Forschung vom MIT Media Lab zurückgeht.
Die Idee ist einfach: Profitieren Sie von Ihren Augen für eine schnelle Zielauswahl und Positionierung.
Sehen Sie sich einfach ein Hologramm an, und sagen _Sie "Put this",_ und sehen Sie sich an, wo Sie es platzieren möchten, und sagen _Sie "There!"._
Um Ihr Hologramm genauer zu positionieren, können Sie zusätzliche Eingaben von Den Händen, Stimmen oder Controllern verwenden.

**Summary**: Positioning holograms using eyes, voice and hand input (*drag-and-drop*). Von den Augen unterstützte Schieberegler mit Augen und Händen.

### <a name="visualization-of-visual-attention"></a>**Visualisierung der visuellen Aufmerksamkeit**

Daten, die auf dem Blick der Benutzer basieren, sind ein äußerst leistungsfähiges Tool, um die Nutzbarkeit eines Entwurfs zu bewerten und Probleme in effizienten Arbeitsströmen zu identifizieren.
In diesem Tutorial werden verschiedene Visualisierungen für die Blickverfolgung erläutert, und es wird erläutert, wie sie unterschiedliche Anforderungen erfüllen.
Wir stellen grundlegende Beispiele für das Protokollieren und Laden von Eyetrackingdaten sowie Beispiele für deren Visualisierung bereit.

**Zusammenfassung:** Karte mit zweidimensionaler Aufmerksamkeit (Wärmebild) auf Schiefern. Aufzeichnen & Wiedergeben von Eyetrackingdaten.

## <a name="setting-up-the-mrtk-eye-tracking-samples"></a>Einrichten der MRTK-Eyetrackingbeispiele

### <a name="prerequisites"></a>Voraussetzungen

Beachten Sie, dass für die Verwendung der Eyetrackingbeispiele auf dem Gerät ein HoloLens 2 und ein Beispiel-App-Paket erforderlich sind, das mit der Funktion "Gaze Input" auf dem AppXManifest des Pakets erstellt wurde.

Um diese Eyetrackingbeispiele auf dem Gerät zu verwenden, müssen Sie [diese Schritte](../input/eye-tracking/eye-tracking-basic-setup.md#testing-your-unity-app-on-a-hololens-2) ausführen, bevor Sie die App in Visual Studio erstellen.

### <a name="1-load-eyetrackingdemo-00-rootsceneunity"></a>1. Laden von EyeTrackingDemo-00-RootScene.unity

*EyeTrackingDemo-00-RootScene* ist die Basisszene _(Root),_ in der alle MRTK-Kernkomponenten enthalten sind.
Dies ist die Szene, die Sie zuerst laden müssen und aus der Sie die Eyetracking-Demos ausführen.
Es verfügt über ein grafisches Szenenmenü, mit dem Sie problemlos zwischen den verschiedenen Eyetrackingbeispielen wechseln können, die [additiv geladen](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html)werden.

![Szenenmenü im Eyetrackingbeispiel](../images/eye-tracking/mrtk_et_scenemenu.jpg)

Die Stammszene enthält einige Kernkomponenten, die über die additiv geladenen Szenen hinweg beibehalten werden, z. B. die von MRTK konfigurierten Profile und die Szenenkamera.
_MixedRealityBasicSceneSetup_ (siehe Screenshot unten) enthält ein Skript, das die Referenzszene beim Start automatisch lädt.
Standardmäßig ist dies _EyeTrackingDemo-02-TargetSelection_.  

![Beispiel für das OnLoadStartScene-Skript](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

### <a name="2-adding-scenes-to-the-build-menu"></a>2. Hinzufügen von Szenen zum Buildmenü

Um additive Szenen während der Laufzeit zu laden, müssen Sie diese Szenen zuerst dem Menü _Build Einstellungen -> Scenes in Build_ hinzufügen.
Es ist wichtig, dass die Stammszene als erste Szene in der Liste angezeigt wird:

![Erstellen Einstellungen Szenenmenüs für Eyetrackingbeispiele](../images/eye-tracking/mrtk_et_build_settings.jpg)

### <a name="3-play-the-eye-tracking-samples-in-the-unity-editor"></a>3. Wiedergeben der Eyetrackingbeispiele im Unity-Editor

Nachdem Sie dem Build Einstellungen die Blickverfolgungsszenen hinzugefügt und das _EyeTrackingDemo-00-RootScene_ geladen haben, sollten Sie als Letztes überprüfen: Ist das Skript _"OnLoadStartScene"_ aktiviert, das an _das MixedRealityBasicSceneSetup_ GameObject angefügt ist? Dies soll der Stammszene mitteilen, welche Demoszene zuerst geladen werden soll.

![Beispiel für das OnLoad_StartScene-Skript](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

Jetzt geht es los! Klicken Sie auf _"Play"_!
Es sollten mehrere Gems und das Szenenmenü oben angezeigt werden.

![Beispielscreenshot der Et-Zielauswahl-Szene](../images/eye-tracking/mrtk_et_targetselect.png)

Sie sollten auch einen kleinen halbtransparenten Kreis in der Mitte Ihrer Spielansicht bemerken.
Dies fungiert als Indikator (Cursor) des _simulierten Anvierens_ der Augen: Drücken Sie einfach die _rechte Maustaste_ nach unten, und bewegen Sie die Maus, um ihre Position zu ändern.
Wenn der Cursor auf die Gems zeigen, werden Sie feststellen, dass er an der Mitte des aktuell angezeigten Gems ausgerichtet wird.
Dies ist eine hervorragende Möglichkeit, um zu testen, ob Ereignisse wie erwartet ausgelöst werden, wenn ein Ziel _"betrachtet"_ wird.
Beachten Sie, dass das _simulierte Anvisierten_ der Augen über das Maussteuerelement eine eher schlechte Ergänzung unserer schnellen und unbeabsichtigten Augenbewegungen ist.
Sie eignet sich jedoch hervorragend zum Testen der grundlegenden Funktionalität, bevor Sie den Entwurf durch Bereitstellung auf dem HoloLens 2 Gerät iterieren.
Zurück zur Blickverfolgungs-Beispielszene: Das Gem wird gedreht, solange es betrachtet wird und zerstört werden kann, indem es sich ansieht und ...

- Drücken _der EINGABETASTE_ (wodurch "Select" simuliert wird)
- _"Auswählen"_ ins Mikrofon
- Klicken Sie beim Drücken von _Leertaste_ zum Anzeigen der simulierten Handeingabe auf die linke Maustaste, um eine simulierte Zusammendrückung durchzuführen.

In unserem Tutorial [**Eye-Supported Target Selection (Eye-Supported Target Selection)**](../input/eye-tracking/eye-tracking-target-selection.md) wird ausführlicher beschrieben, wie Sie diese Interaktionen erreichen können.

Wenn Sie den Cursor auf die obere Menüleiste in der Szene bewegen, werden Sie feststellen, dass das aktuell gezeigte Element subtly hervorgehoben wird.
Sie können das aktuell hervorgehobene Element auswählen, indem Sie eine der oben beschriebenen Commitmethoden verwenden (z. B. drücken Sie die _EINGABETASTE)._
Auf diese Weise können Sie zwischen den verschiedenen Eyetracking-Beispielszenen wechseln.

### <a name="4-how-to-test-specific-sub-scenes"></a>4. Testen bestimmter Teilszenen

Wenn Sie an einem bestimmten Szenario arbeiten, möchten Sie das Szenenmenü möglicherweise nicht jedes Mal durchlaufen.
Stattdessen sollten Sie direkt von der Szene aus beginnen, an der Sie gerade arbeiten, wenn Sie auf die Schaltfläche _Wiedergabe_ klicken.
Kein Problem. Folgendes können Sie tun:

1. Laden der _Stammszene_
2. Deaktivieren Sie in der _Stammszene_ das Skript _"OnLoadStartScene"._
3. _Drag and drop_ one of the eye tracking test scenes that are described below (or any other scene) into your _Hierarchy_ view as shown in the screenshot below.

    ![Beispiel für additive Szene](../images/eye-tracking/mrtk_et_additivescene.jpg)

4. Klicken Sie auf _Wiedergabe._

Beachten Sie, dass das Laden der untergeordneten Szene wie folgt nicht persistent ist: Wenn Sie Ihre App auf dem HoloLens 2 Gerät bereitstellen, wird nur die Stammszene geladen (vorausgesetzt, sie wird oben im Build Einstellungen angezeigt).
Wenn Sie Ihr Projekt für andere freigeben, werden die Untergeordneten Szenen nicht automatisch geladen.

---

Nachdem Sie nun wissen, wie Sie die MRTK-Eyetracking-Beispielszenen umsetzen können, fahren wir mit dem Tiefergehen der Auswahl von Hologrammen mit Ihren Augen fort: [Eye-supported target selection](../input/eye-tracking/eye-tracking-target-selection.md).

---
[Zurück zu "Eye tracking in the MixedRealityToolkit" (Blickverfolgung im MixedRealityToolkit)](../input/eye-tracking/eye-tracking-Main.md)
