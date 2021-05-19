---
title: 'Eyetracking (Blickverfolgung): Grundlegende Einrichtung'
description: Einrichten von Eye Tracking in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Eye Tracking,
ms.openlocfilehash: 0513161bf8151069296c39612cbcacd15cc5c6c1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144092"
---
# <a name="getting-started-with-eye-tracking-in-mrtk"></a>Erste Schritte mit eye tracking in MRTK

Auf dieser Seite erfahren Sie, wie Sie Ihre Unity MRTK-Szene für die Verwendung von Eyetracking in Ihrer App einrichten.
Im Folgenden wird davon ausgegangen, dass Sie mit einer neuen Szene beginnen.
Alternativ können Sie sich unsere bereits konfigurierten [MRTK-Eyetrackingbeispiele](../../example-scenes/eye-tracking-examples-overview.md) mit vielen großartigen Beispielen, auf denen Sie direkt aufbauen können, informieren.

## <a name="eye-tracking-requirements-checklist"></a>Checkliste für Eyetrackinganforderungen

Damit eye tracking ordnungsgemäß funktioniert, müssen die folgenden Anforderungen erfüllt sein.
Wenn Sie noch nicht mit der Eyetracking-HoloLens 2 und der Einrichtung von EyeTracking in MRTK noch nicht sehr schnell sind, machen Sie sich keine Sorgen!
Im Folgenden wird ausführlich erläutert, wie sie behandelt werden können.

1. Dem _Eingabesystem muss Datenanbieter_ "Eye Gaze" hinzugefügt werden. Dies stellt Eyetrackingdaten von der Plattform zur Verfügung.
2. Die _Funktion "GazeInput"_ muss im Anwendungsmanifest aktiviert sein.
   **Diese Funktion kann in Unity 2019 festgelegt werden, aber in Unity 2018 und früher ist diese Funktion nur in Visual Studio und über das MRTK-Buildtool verfügbar.**
3. Die HoloLens **muss für** den aktuellen Benutzer mit den Augen kalibriert sein. Sehen Sie sich unser [Beispiel an, um zu ermitteln, ob ein Benutzer mit](eye-tracking-is-user-calibrated.md)den Augen kalibriert ist oder nicht.

### <a name="a-note-on-the-gazeinput-capability"></a>Hinweis zur GazeInput-Funktion

Die vom MRTK bereitgestellten Buildtools (d. h. Mixed Reality Toolkit -> Utilities -> Build Window) können die GazeInput-Funktion automatisch für Sie aktivieren. Hierzu müssen Sie sicherstellen, dass auf der Registerkarte "Appx Build Options" (Appx-Buildoptionen) die Option "Gaze Input Capability" (Eingabefunktion zum Anv überprüfen) angezeigt wird:

![MRTK-Buildtools](../../images/eye-tracking/mrtk_et_buildsetup.png)

Mit diesen Tools wird das AppX-Manifest nach Abschluss des Unity-Builds gesucht und die GazeInput-Funktion manuell hinzugefügt.
**Vor Unity 2019 ist dieses Tool NICHT aktiv, wenn** das integrierte Buildfenster von Unity verwendet wird (d. h. Datei -> Buildeinstellungen).

Vor Unity 2019 muss die Funktion bei Verwendung des Unity-Buildfensters nach dem Unity-Build wie folgt manuell hinzugefügt werden:

1. Öffnen Sie das kompilierte Visual Studio-Projekt, und öffnen Sie dann _"Package.appxmanifest"_ in Ihrer Projektmappe.
2. Aktivieren Sie unter _Funktionen_ das Kontrollkästchen _"GazeInput"._ Wenn keine _GazeInput-Funktion_ angezeigt wird, überprüfen Sie, ob Ihr System die Voraussetzungen für die [Verwendung von MRTK](/windows/mixed-reality/develop/install-the-tools) erfüllt (insbesondere die Windows SDK Version).

_Beachten Sie:_ Sie müssen dies nur tun, wenn Sie einen neuen Buildordner erstellen.
Dies bedeutet, dass Sie Ihre Änderungen nicht erneut übernehmen müssen, wenn Sie ihr Unity-Projekt bereits erstellt und das appxmanifest vor eingerichtet haben und jetzt wieder auf denselben Ordner abzielen.

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
- Klicken Sie auf die Schaltfläche _"Klonen",_ um die Standardeinstellung _(DefaultMixedRealityInputSystemProfile)_ zu bearbeiten. Das _Menü "Profil klonen"_ wird angezeigt. Klicken Sie einfach _am unteren_ Rand dieses Menüs auf "Klonen".
- Doppelklicken Sie auf Ihr neues Eingabeprofil, erweitern Sie _"Eingabedatenanbieter",_ und wählen Sie _"+ Hinzufügen Datenanbieter" aus._
- Erstellen Sie einen neuen Datenanbieter:
  - Wählen **Sie** unter Typ _die Option "Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input"_  ->  _"WindowsMixedRealityEye DateitypDataProvider" aus._
  - Wählen **Sie für Plattform(en)** _die Option "Windows Universal" aus._

![MRTK-Datenanbieter](../../images/eye-tracking/mrtk_setup_eyes_dataprovider.jpg)

### <a name="simulating-eye-tracking-in-the-unity-editor"></a>Simulieren von Eyetracking im Unity-Editor

Sie können eye tracking-Eingaben im Unity-Editor simulieren, um sicherzustellen, dass Ereignisse ordnungsgemäß ausgelöst werden, bevor Sie die App in Ihrem HoloLens 2.
Das Anvisieren mit den Augen wird simuliert, indem einfach die Position der Kamera als Ursprung des Anvisierens mit den Augen und der Vorwärtsvektor der Kamera als Blickrichtung verwendet wird.
Obwohl dies für erste Tests ideal ist, beachten Sie, dass es sich nicht um eine gute Imitation für schnelle Augenbewegungen handelt.
Dafür ist es besser, häufige Tests Ihrer augenbasierten Interaktionen mit dem HoloLens 2.

1. **Aktivieren sie simuliertes Eyetracking:**
    - Klicken Sie _in_ Ihrem MRTK-Konfigurationsprofil auf die Registerkarte "Eingabe".
    - Navigieren Sie von dort zu _"Eingabedatenanbieter"_  ->  _"Eingabesimulationsdienst"._
    - _Klonen Sie "DefaultMixedRealityInputSimpulationProfile",_ um Änderungen vorzunehmen.
    - Aktivieren Sie _das Kontrollkästchen "Simulate Eye Position"_ (Augenposition simulieren).

    ![MRTK-Augen simulieren](../../images/eye-tracking/mrtk_setup_eyes_simulate.jpg)

2. **Standardcursor für** den Anvanvitätszeiger mit dem Kopf deaktivieren: Im Allgemeinen wird empfohlen, die Anzeige eines Cursors mit dem Anvitätszeiger mit den Augen zu vermeiden oder wenn dies unbedingt erforderlich ist, um ihn sehr dezent _zu_ machen.
Es wird empfohlen, den Standardmäßigen Cursor zum Anvieren mit dem Kopf auszublenden, der standardmäßig an das MRTK-Blickzeigerprofil angefügt ist.
    - Navigieren Sie zu Ihrem MRTK-Konfigurationsprofil, und > _"Eingabe"_  ->  _"Zeiger"_
    - _Klonen Sie das "DefaultMixedRealityInputPointerProfile",_ um Änderungen vorzunehmen.
    - Am oberen Ende der _Zeigereinstellungen_ sollten Sie dem _"GazeCursor"_ ein unsichtbares Cursor-Prefab zuweisen. Wählen Sie hierzu in der MRTK Foundation das _Prefab "Eye Eye EyeeCursor"_ aus.

### <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a>Aktivieren des blickbasierten Anvierens im Anvierungsanbieter

In HoloLens v1 wurde das Anvieren mit dem Kopf als primäres Zeigerverfahren verwendet.
Während das Anvieren mit dem Kopf weiterhin über _den GazeProvider_ im MRTK verfügbar ist, der an Ihre Kamera angefügt [ist,](https://docs.unity3d.com/ScriptReference/Camera.html)können Sie überprüfen, ob Sie stattdessen das Anvieren mit den Augen verwenden, indem Sie das Kontrollkästchen _"IsEyeTrackingEnabled"_ in den Anvitierungseinstellungen des Eingabezeigerprofils aktivieren.

>[!NOTE]
>Entwickler können zwischen dem blickbasierten Anvieren und dem kopfbasierten Anvieren im Code wechseln, indem sie die _Eigenschaft "IsEyeTrackingEnabled"_ von _"GazeProvider" ändern._  

>[!IMPORTANT]
>Wenn eine der Eyetrackinganforderungen nicht erfüllt wird, wird die Anwendung automatisch auf das kopfbasierte Anving zurückfallen.

### <a name="accessing-eye-gaze-data"></a>Zugreifen auf Daten zum Anvieren mit den Augen

Nachdem Ihre Szene nun für die Verwendung der Eyetracking eingerichtet ist, sehen wir uns an, wie Sie in Ihren [Skripts](eye-tracking-target-selection.md)darauf zugreifen: Zugreifen auf Eyetrackingdaten über [EyeTrackeProvider](eye-tracking-eye-gaze-provider.md) und von den Augen unterstützte Zielauswahlen.

### <a name="testing-your-unity-app-on-a-hololens-2"></a>Testen Ihrer Unity-App auf HoloLens 2

Das Erstellen Ihrer App mit Eyetracking sollte mit der Kompilierung anderer mrtk HoloLens 2-Apps vergleichbar sein. Stellen Sie sicher, dass Sie die Funktion *"Eingabe* anvizieren" aktiviert haben, wie oben im Abschnitt [*A note on the GazeInput capability (Hinweis zur GazeInput-Funktion) beschrieben.*](#a-note-on-the-gazeinput-capability)

#### <a name="eye-calibration"></a>Kalibrierung der Augen

Vergessen Sie abschließend nicht, die Kalibrierung der Augen auf Ihrem Gerät HoloLens 2.
Das Eyetrackingsystem gibt keine Eingaben zurück, wenn der Benutzer nicht kalibriert ist.
Am einfachsten erreichen Sie die Kalibrierung, indem Sie das Visor nach oben und wieder nach unten kippen.
Eine Systembenachrichtigung sollte Sie als neuen Benutzer einladen und Sie bitten, die Kalibrierung der Augen zu durchgehen.
Alternativ finden Sie die Augenkalibrierung in den Systemeinstellungen: Einstellungen > System > Kalibrierung > Kalibrierung der Augen ausführen.

#### <a name="eye-tracking-permission"></a>Eyetrackingberechtigung

Wenn Sie die App auf Ihrem HoloLens 2 zum ersten Mal starten, sollte eine Eingabeaufforderung angezeigt werden, in der der Benutzer um die Berechtigung zur Verwendung der Eyetracking gebeten wird.
Wenn sie nicht angezeigt wird, ist dies in der Regel ein Hinweis darauf, dass die _GazeInput-Funktion_ nicht festgelegt wurde.

Nachdem die Berechtigungsaufforderung einmal angezeigt wurde, wird sie nicht automatisch erneut angezeigt.
Wenn Sie _die Eyetrackingberechtigung verweigert_ haben, können Sie dies unter Einstellungen -> Datenschutz -> Apps zurücksetzen.

---

Dies sollte Ihnen den Einstieg in die Verwendung von Eyetracking in Ihrer MRTK Unity-App bringen.
Vergessen Sie nicht, [unsere MRTK-Eyetracking-Tutorials und -Beispiele](../../example-scenes/eye-tracking-examples-overview.md) zu lesen, die veranschaulichen, wie Sie Eyetrackingeingaben verwenden und skripts bereitstellen, die Sie in Ihren Projekten wiederverwenden können.

---
[Zurück zu "Eye tracking in the MixedRealityToolkit" (Blickverfolgung im MixedRealityToolkit)](eye-tracking-main.md)