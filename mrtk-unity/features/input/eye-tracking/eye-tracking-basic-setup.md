---
title: 'Eyetracking (Blickverfolgung): Grundlegende Einrichtung'
description: Einrichten von Eye Tracking in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Eye Tracking,
ms.openlocfilehash: d8b47639729381a41e4fe1e1db86700bf9323860553934a6da4dfa4b15de49eb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197456"
---
# <a name="getting-started-with-eye-tracking-in-mrtk"></a>Erste Schritte mit eye tracking in MRTK

Auf dieser Seite wird erläutert, wie Sie Ihre Unity MRTK-Szene für die Verwendung der Eyetracking in Ihrer App einrichten.
Im Folgenden wird davon ausgegangen, dass Sie mit einer neuen Szene beginnen.
Alternativ können Sie sich unsere bereits konfigurierten [MRTK-Eyetrackingbeispiele](../../example-scenes/eye-tracking-examples-overview.md) mit unzähligen hervorragenden Beispielen ansehen, auf denen Sie direkt aufbauen können.

## <a name="eye-tracking-requirements-checklist"></a>Checkliste für Eyetrackinganforderungen

Damit eye tracking ordnungsgemäß funktioniert, müssen die folgenden Anforderungen erfüllt sein.
Wenn Sie noch nicht mit der Eyetracking auf HoloLens 2 und der Einrichtung der Blickverfolgung im MRTK sind, machen Sie sich keine Sorgen!
Im Folgenden wird ausführlich erläutert, wie sie jeweils behandelt werden.

1. Dem Eingabesystem muss _ein "Eye Gaze Datenanbieter"_ hinzugefügt werden. Dies stellt Eyetrackingdaten von der Plattform bereit.
2. Die _GazeInput-Funktion_ muss im Anwendungsmanifest aktiviert werden.
   **Diese Funktion kann in Unity 2019 festgelegt werden, aber in Unity 2018 und früher ist diese Funktion nur in Visual Studio und über das MRTK-Buildtool verfügbar.**
3. Die HoloLens **muss** für den aktuellen Benutzer mit dem Auge kalibriert werden. Sehen Sie sich unser [Beispiel an, um zu ermitteln, ob ein Benutzer mit dem Auge kalibriert ist oder nicht.](eye-tracking-is-user-calibrated.md)

### <a name="a-note-on-the-gazeinput-capability"></a>Hinweis zur GazeInput-Funktion

Die von MRTK bereitgestellten Buildtools (d. h. Mixed Reality Toolkit -> Utilities -> Buildfenster) können die GazeInput-Funktion automatisch für Sie aktivieren. Hierzu müssen Sie sicherstellen, dass die Eingabefunktion "Anvieren" auf der Registerkarte "Appx-Buildoptionen" aktiviert ist:

![MRTK-Buildtools](../../images/eye-tracking/mrtk_et_buildsetup.png)

Mit diesen Tools wird das AppX-Manifest nach Abschluss des Unity-Builds gesucht und die GazeInput-Funktion manuell hinzugefügt.
**Vor Unity 2019 ist dieses Tool NICHT aktiv, wenn** das integrierte Buildfenster von Unity verwendet wird (d. h. Datei -> Build Einstellungen).

Vor Unity 2019 muss die Funktion bei Verwendung des Unity-Buildfensters nach dem Unity-Build wie folgt manuell hinzugefügt werden:

1. Öffnen Sie das kompilierte Visual Studio Projekt, und öffnen Sie dann _"Package.appxmanifest"_ in Ihrer Projektmappe.
2. Aktivieren Sie unter _Funktionen_ das Kontrollkästchen _"GazeInput"._ Wenn keine _GazeInput-Funktion_ angezeigt wird, überprüfen Sie, ob Ihr System die Voraussetzungen für die [Verwendung von MRTK](/windows/mixed-reality/develop/install-the-tools) erfüllt (insbesondere die Windows SDK-Version).

_Beachten Sie:_ Sie müssen dies nur tun, wenn Sie einen neuen Buildordner erstellen.
Dies bedeutet, dass Sie Ihre Änderungen nicht erneut übernehmen müssen, wenn Sie ihr Unity-Projekt bereits erstellt und das appxmanifest bereits vor eingerichtet haben und jetzt wieder auf denselben Ordner abzielen.

## <a name="setting-up-eye-tracking-step-by-step"></a>Einrichten der Eyetracking schritt für Schritt

### <a name="setting-up-the-scene"></a>Einrichten der Szene

Richten Sie _das MixedRealityToolkit_ ein, indem Sie einfach auf _"Mixed Reality Toolkit -> Configure..." klicken._ in der Menüleiste.

![MRTK-Konfiguration](../../images/eye-tracking/mrtk_setup_configure.jpg)

### <a name="setting-up-the-mrtk-profiles-required-for-eye-tracking"></a>Einrichten der MRTK-Profile, die für eye tracking erforderlich sind

Nachdem Sie Ihre MRTK-Szene eingerichtet haben, werden Sie aufgefordert, ein Profil für MRTK auszuwählen.
Sie können einfach _DefaultMixedRealityToolkitConfigurationProfile_ und dann die Option _"Kopieren & Anpassen"_ auswählen.

![MRTK-Profil](../../images/eye-tracking/mrtk_setup_configprofile.jpg)

### <a name="create-an-eye-gaze-data-provider"></a>Erstellen eines Datenanbieters zum Anvieren mit den Augen

- Klicken Sie in Ihrem MRTK-Profil auf die Registerkarte _"Eingabe"._
- Klicken Sie auf die Schaltfläche _"Klonen",_ um die Standardeinstellung _(DefaultMixedRealityInputSystemProfile)_ zu bearbeiten. Ein Menü _"Profil klonen"_ wird angezeigt. Klicken Sie einfach unten im Menü auf _"Klonen"._
- Doppelklicken Sie auf Ihr neues Eingabeprofil, erweitern Sie _"Eingabedatenanbieter",_ und wählen _Sie "+ Datenanbieter hinzufügen" aus._
- Erstellen Sie einen neuen Datenanbieter:
  - Wählen Sie unter **Typ** die Option _"Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input"_  ->  _"WindowsMixedRealityEyeGazeDataProvider" aus._
  - Wählen Sie unter **Plattform(en)** die Option _"Windows Universal" aus._

![MRTK-Datenanbieter](../../images/eye-tracking/mrtk_setup_eyes_dataprovider.jpg)

### <a name="simulating-eye-tracking-in-the-unity-editor"></a>Simulieren der Eyetracking im Unity-Editor

Sie können die Eyetrackingeingabe im Unity-Editor simulieren, um sicherzustellen, dass Ereignisse ordnungsgemäß ausgelöst werden, bevor Sie die App auf Ihrem HoloLens 2 bereitstellen.
Das Anvisieren mit den Augen wird simuliert, indem einfach die Position der Kamera als Ursprung für anvisierende Augen und der Vorwärtsvektor der Kamera als Blickrichtung verwendet wird.
Obwohl dies hervorragend für erste Tests geeignet ist, beachten Sie, dass es sich nicht um eine gute Vorbereitung für schnelle Augenbewegungen handelt.
Hierfür ist es besser, häufige Tests Ihrer augenbasierten Interaktionen auf der HoloLens 2 sicherzustellen.

1. **Simulierte Eyetracking aktivieren:**
    - Klicken Sie in Ihrem MRTK-Konfigurationsprofil auf die Registerkarte _"Eingabe"._
    - Navigieren Sie von dort aus zu _"Eingabedatenanbieter"_  ->  _"Eingabesimulationsdienst"._
    - Klonen Sie _"DefaultMixedRealityInputSimpulationProfile",_ um Änderungen daran vorzunehmen.
    - Aktivieren Sie das _Kontrollkästchen "Simulieren der Augenposition"._

    ![MRTK-Augen simulieren](../../images/eye-tracking/mrtk_setup_eyes_simulate.jpg)

2. **Standardcursor für das Anvieren** mit dem Kopf deaktivieren: Im Allgemeinen empfiehlt es sich, die Anzeige eines Anverweises mit den Augen zu vermeiden, oder wenn dies unbedingt erforderlich ist, um ihn _sehr_ dezent zu gestalten.
Es wird empfohlen, den standardmäßigen Cursor für das Anvfassen mit dem Kopf auszublenden, der standardmäßig an das MRTK-Anviertzeigerprofil angefügt ist.
    - Navigieren Sie zu Ihrem MRTK-Konfigurationsprofil > _"Eingabe"_  ->  _"Zeiger"._
    - Klonen Sie _"DefaultMixedRealityInputPointerProfile",_ um Änderungen daran vorzunehmen.
    - Am oberen Rand des _"Zeiger-Einstellungen"_ sollten Sie dem _"GazeCursor"_ ein unsichtbares Cursor-Prefab zuweisen. Wählen Sie hierzu das Prefab _"EyeGazeCursor"_ aus der MRTK Foundation aus.

### <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a>Aktivieren des blickbasierten Anvischens im Anviert-Anbieter

In HoloLens v1 wurde das Anvieren mit dem Kopf als primäres Punktverfahren verwendet.
Während das Anverfolgen mit dem Kopf weiterhin über den _GazeProvider_ im MRTK verfügbar ist, der an Ihre [Kamera](https://docs.unity3d.com/ScriptReference/Camera.html)angefügt ist, können Sie überprüfen, ob Sie stattdessen anverfolgt werden, indem Sie das _Kontrollkästchen "IsEyeTrackingEnabled"_ in den Anverfolgungseinstellungen des Eingabezeigerprofils aktivieren.

>[!NOTE]
>Entwickler können im Code zwischen dem blickbasierten anverfolgten und dem kopfbasierten Anverfolgen wechseln, indem sie die _IsEyeTrackingEnabled-Eigenschaft_ von _"GazeProvider"_ ändern.  

>[!IMPORTANT]
>Wenn eine der Anforderungen an die Blickverfolgung nicht erfüllt ist, wird die Anwendung automatisch auf das kopfbasierte Anverfolgen zurückgreifen.

### <a name="accessing-eye-gaze-data"></a>Zugreifen auf Daten zum Anvieren mit den Augen

Nachdem Ihre Szene nun für die Verwendung von Eyetracking eingerichtet ist, sehen wir uns an, wie Sie in Ihren Skripts darauf zugreifen können: [Zugreifen auf Eyetrackingdaten über EyeGazeProvider](eye-tracking-eye-gaze-provider.md) und [eye-supported target selections](eye-tracking-target-selection.md)(Blickverfolgungsdaten über EyeGazeProvider und durch die Augen unterstützte Zielauswahl).

### <a name="testing-your-unity-app-on-a-hololens-2"></a>Testen Ihrer Unity-App auf einem HoloLens 2

Das Erstellen Ihrer App mit Blickverfolgung sollte mit der Kompilierung anderer HoloLens 2 MRTK-Apps vergleichbar sein. Stellen Sie sicher, dass Sie die Funktion *"Gaze Input"* wie oben im Abschnitt [*A note on the GazeInput capability (Hinweis zur GazeInput-Funktion)*](#a-note-on-the-gazeinput-capability)beschrieben aktiviert haben.

#### <a name="eye-calibration"></a>Augenkalibrierung

Vergessen Sie abschließend nicht, die Kalibrierung ihrer HoloLens 2 durch die Augen zu ziehen.
Das Eyetrackingsystem gibt keine Eingabe zurück, wenn der Benutzer nicht kalibriert ist.
Die einfachste Möglichkeit, zur Kalibrierung zu gelangen, besteht darin, das Visier nach oben und wieder nach unten zu drehen.
Es sollte eine Systembenachrichtigung angezeigt werden, die Sie als neuen Benutzer empfängt und Sie auffordert, die Augenkalibrierung zu durchlaufen.
Alternativ können Sie die Augenkalibrierung in den Systemeinstellungen finden: Einstellungen > System > Kalibrierung > Kalibrierung der Augen ausführen.

#### <a name="eye-tracking-permission"></a>Eyetrackingberechtigung

Wenn Sie die App auf Ihrem HoloLens 2 zum ersten Mal starten, sollte eine Eingabeaufforderung angezeigt werden, in der der Benutzer um die Berechtigung zur Verwendung der Eyetracking gebeten wird.
Wenn sie nicht angezeigt wird, ist dies in der Regel ein Hinweis darauf, dass die _GazeInput-Funktion_ nicht festgelegt wurde.

Nachdem die Berechtigungsaufforderung einmal angezeigt wurde, wird sie nicht automatisch erneut angezeigt.
Wenn Sie _die Eyetrackingberechtigung verweigert_ haben, können Sie dies in Einstellungen -> Privacy -> Apps zurücksetzen.

---

Dies sollte Ihnen den Einstieg in die Verwendung von Eyetracking in Ihrer MRTK Unity-App bringen.
Vergessen Sie nicht, [unsere MRTK-Eyetracking-Tutorials und -Beispiele](../../example-scenes/eye-tracking-examples-overview.md) zu lesen, die veranschaulichen, wie Sie Eyetrackingeingaben verwenden und skripts bereitstellen, die Sie in Ihren Projekten wiederverwenden können.

---
[Zurück zu "Eye tracking in the MixedRealityToolkit" (Blickverfolgung im MixedRealityToolkit)](eye-tracking-main.md)