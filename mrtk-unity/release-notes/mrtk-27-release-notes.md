---
title: Versionsanmerkungen zu MRTK 2.7
description: Versionsanmerkungen zu MRTK, Version 2.7
author: RogPodge
ms.author: roliu
ms.date: 06/16/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, XRSDK, Legacy XR, Leap Motion, Ultraleap, OpenXR
ms.localizationpriority: high
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 8f6c68c067df735761dd9c162c71fd85f1f3e132
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906976"
---
# <a name="microsoft-mixed-reality-toolkit-27-release-notes"></a>Versionsanmerkungen zu Microsoft Mixed Reality Toolkit 2.7

## <a name="whats-new-in-272"></a>Neuerungen in 2.7.2

### <a name="fixed-a-upm-package-dependency-issue"></a>Ein Problem mit der UPM-Paketabhängigkeit wurde behoben

Es besteht ein Problem mit MRTK 2.7.1-UPM-Paketen, das dazu führt, dass die Abhängigkeiten nicht ordnungsgemäß eingerichtet wurden. Das Problem bewirkte, dass das Mixed Reality Feature-Tool MRTK 2.7.1-Pakete nicht ordnungsgemäß importiert. Das Problem wurde nun in 2.7.2 behoben. Es gibt keine Codeänderung in dieser Version gegenüber 2.7.1.


## <a name="whats-new-in-271"></a>Neuerungen in 2.7.1

### <a name="show-version"></a>Version anzeigen

Das `Mixed Reality` > `Toolkit`-Menü enthält jetzt einen Eintrag `Show version...`, der das Mixed Reality Toolkit Foundation-Paket untersucht, um die Version von MRTK zu bestimmen, die vom Projekt verwendet wird.

![Menü „Version anzeigen“](images/ShowVersionMenu.png)

![MRTK-Versionsdialogfeld](images/VersionDialog.png)

> [!NOTE]
> Wenn MRTK aus dem [GitHub-Repository](https://aka.ms/mrtk) geklont wurde, wurden die Versionsinformationen nicht festgelegt.
>
> ![Version kann nicht bestimmt werden](images/CannotDetermineVersion.png)

### <a name="authors-list"></a>Autorenliste

Von MRTK 2.7.1 an aufwärts ist die Autorenlistendatei im Mixed Reality Toolkit Foundation-Paket enthalten.

### <a name="integrated-openxr-project-setup-into-the-configurator-setup-flow"></a>In den Konfigurator-Setupflow integriertes OpenXR-Projektsetup

Ab MRTK 2.7.1 erhalten Benutzer des Mixed Reality OpenXR-Plug-Ins Anweisungen zum Einrichten dieses Plug-Ins in MRTK. Es gibt eine Option für Benutzer mit der Zielplattform HoloLens 2, die empfohlenen Einstellungen automatisch anzuwenden.

![Konfigurationsfenster mit OpenXR-Setupanweisungen](images/configuratorMROpenXR.png)

### <a name="notable-bugfixes-and-changes"></a>Wichtige Fehlerbehebungen und Änderungen

- Unity Joystick-Manager in XR SDK-Pipeline als unterstützt gekennzeichnet [#9954](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9954), [#9994](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9994)
- Zusätzliche Überprüfungen für interaktiven Inspektorcode, um NULL-Fehler zu verhindern [#9943](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9943)
- OpenXR-Gitternetzanbieter zur Impuls-Shader-Beispielszene hinzugefügt [#9902](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9902)
- Wiederherstellen des Handmechanikprofils in Beispielszene [#9915](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9915)
- Einige Bereinigungen der HandConstraint*-Skripts [#9935](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9935)
- Es wurden einige Fehler behoben, die sich auf das Erstellen und Klonen von Profilen auswirken [#9982](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9982)


## <a name="whats-new-in-270"></a>Neuerungen in 2.7.0

### <a name="openxr-is-now-officially-supported-in-mrtk"></a>OpenXR wird im MRTK jetzt offiziell unterstützt

Da die neuen OpenXR-Plug-Ins immer ausgereifter werden, unterstützt MRTK jetzt offiziell OpenXR. Im Vergleich zu früheren Releases haben wir Projekten mit OpenXR die folgenden Funktionen hinzugefügt:

- [Unterstützung für das vom System bereitgestellte Motion Controller-Modell](#support-for-the-system-provided-motion-controller-model-on-openxr)
- Unterstützung für WinMR-Gesten (Auswählen, Halten, Bearbeiten und Navigation) [#9843](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9843)
- [Unterstützung für Controller-Haptik](#support-for-controller-haptics-across-legacy-wmr-windows-xr-plugin-and-openxr)
- [Unterstützung für ein artikuliertes Hand-Mesh in HoloLens 2](#support-for-hololens-2-articulated-hand-mesh-on-openxr)
- Unterstützung für räumliche Abbildung in HoloLens 2 [#9567](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9567), [#9827](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9827)
- Unterstützung für Scene Understanding in HoloLens 2 [#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)

Wenn Sie HoloLens 2 oder Windows Mixed Reality-Headsets als Zielplattform über OpenXR ansteuern, achten Sie darauf, mithilfe des [Mixed Reality Feature-Tools](https://aka.ms/MRFeatureTool) die **Mixed Reality OpenXR-Plug-In-Version 0.9.5 oder höher** zu installieren oder auf diese zu aktualisieren, andernfalls entgehen Ihnen einige der vorstehend genannten Verbesserungen.

### <a name="legacy-xr-and-xr-sdk-data-providers-can-now-be-used-within-the-same-profile"></a>Legacy-XR- und XR SDK-Datenanbieter können jetzt innerhalb desselben Profils verwendet werden

Datenanbieter werden jetzt außerdem nur dann geladen, wenn die entsprechende Pipeline ausgewählt ist, sodass sowohl Legacy-XR- als auch XR SDK-Datenanbieter innerhalb desselben Profils gleichzeitig vorhanden sein können. Diesem Umstand wird dadurch Rechnung getragen, dass Legacy-XR- und XR SDK-Datenanbieter jetzt unter verschiedenen Registerkarten innerhalb der Profilansicht untergebracht sind, so dass Benutzer leichter bestimmen können, ob sie das richtige Profil für ihre XR-Zielpipeline verwenden.

![Legacy- und XR SDK-Datenanbieter können jetzt unter einem einzelnen Profil vereinheitlicht werden](../features/images/xrsdk/LegacyAndXrsdkUnified.png)

Zu diesem Zweck werden im Profilinspektor keine NULL-Daten mehr geladen und angezeigt. Benutzer können unter **Bearbeiten > Projekteinstellungen > Mixed Reality Toolkit** `Show null data providers in the profile inspector` umschalten, um unerwartetes Verhalten mithilfe von fehlenden Datenanbietern zu debuggen.

![NULL-Datenanbieter sind jetzt standardmäßig ausgeblendet](https://user-images.githubusercontent.com/39840334/115093658-ead24600-9ecf-11eb-91c2-486a37f69aba.png)
![Umschalten der Anzeige von NULL-Datenanbietern im Profilinspektor](https://user-images.githubusercontent.com/39840334/115093670-f6257180-9ecf-11eb-96ec-ffe44a225a55.png)

### <a name="added-experience-settings-and-an-associated-mixed-reality-scene-content-behavior"></a>Zusätzliche Einstellungen für die Benutzererfahrung und ein zugeordnetes Verhalten von Mixed Reality-Szeneninhalten

Benutzer können jetzt [Einstellungen für die Benutzererfahrung](../features/experience-settings/experience-settings.md) konfigurieren, die MRTK ausgehend von der Zielerfahrung die angemessene Darstellung von [Mixed Reality-Szeneninhalten](../features/experience-settings/scene-content.md) ermöglichen.

Wenn die bisherigen Einstellungen des Benutzers für die Erfahrungsskala nicht mit dem neuen Profil für Benutzeroberflächeneinstellungen übereinstimmt, wird er aufgefordert, sie im Inspektor zu korrigieren

![Migration der Erfahrungsskala](https://user-images.githubusercontent.com/39840334/114946863-d70bde80-9e00-11eb-9859-fa40d40d2b36.gif)

### <a name="the-redesigned-configurator-now-guides-the-user-through-the-setup-process"></a>Der neu gestaltete Konfigurator führt den Benutzer jetzt durch den Setupvorgang

Der neue MRTK-Konfigurator bietet Benutzern Schritt-für-Schritt-Anleitungen, um das Projekt ordnungsgemäß für die XR-Entwicklung und die Verwendung mit MRTK zu konfigurieren. Sie behandeln die Auswahl der XR-Pipeline, das Abrufen der plattformspezifischen Plug-Ins, das Importieren von TextMeshPro, das Anzeigen der Beispiele (bei Verwendung von UPM) und andere zuvor enthaltene empfohlene Einstellungen für das Projekt.

![Konfigurator mit Darstellung der Pipelineliste](images/Configurator.png)

### <a name="graduated-teleport-hotspot"></a>Anerkannter Teleport-Hotspot

Eine neue [Teleport-Hotspotkomponente](../features/teleport-system/teleport-hotspot.md) wurde anerkannt. Sie können Ihrem GameObject einen Teleport-Hotspot hinzufügen, um sicherzustellen, dass sich der Benutzer beim Teleportieren an diesen Ort in einer bestimmten Position und Ausrichtung befindet.

![Beispiel für Teleport-Hotspot](images/TeleportHotspot.gif)

### <a name="graduated-dwell"></a>Anerkanntes Verweilen

Die Verweilen-Funktion und das entsprechende Beispiel sind jetzt dem experimentellen Stadium entwachsen und anerkannt. Neue Beispiele für volumetrische Schaltflächen im HoloLens 2-Stil sind in der Beispielszene enthalten.

![Verweilen-Hero](../features/images/dwell/MRTK_UX_Dwell.png)

### <a name="added-support-for-leap-motion-unity-modules-version-460-470-471-and-480"></a>Neu hinzugefügte Unterstützung für Leap Motion Unity-Module der Versionen 4.6.0, 4.7.0, 4.7.1 und 4.8.0

Die Unterstützung für die neuesten Versionen der [Leap Motion Unity-Module](https://developer.leapmotion.com/unity) ist jetzt mit MRTK 2.7.0 kompatibel. Weitere Informationen finden Sie unter [Konfigurieren von MRTK für Leap Motion](../supported-devices/leap-motion-mrtk.md).

Vielen Dank an @jackyangzzh für seinen Beitrag, der neuen LeapMotionOrientationExample-Szene!

### <a name="targeted-speech-events-raised-no-longer-restricted-to-gaze-pointers"></a>Auslösung von zielgerichteten Sprachereignissen nicht mehr auf den Anvisieren-Cursor beschränkt

Bisher konnten zielgerichtete Sprachereignisse nur für Objekte ausgelöst werden, die ihren Fokus durch den Anvisieren-Cursor erhalten hatten. Jetzt können Objekte Sprachereignisse unabhängig davon empfangen, durch welchen Cursor sie den Fokus erhalten.

![Sprachereignisse mit Fernzeigern](https://user-images.githubusercontent.com/39840334/117516612-6fa00500-af4e-11eb-94ba-d5fb2ed4e7de.gif)

### <a name="ported-texttospeech-from-htk-to-mrtk"></a>Die Sprachausgabe wurde von HTK zu MRTK portiert

Das beliebte TextToSpeech-Skript ist nun im MRTK verfügbar, damit Sie mithilfe von [`SpeechSynthesizer`](/uwp/api/windows.media.speechsynthesis.speechsynthesizer) auf der UWP-Plattform Sprache aus Text generieren können. Außerdem wurde eine Beispielszene hinzugefügt, um die Funktion zu veranschaulichen.

### <a name="support-for-the-system-provided-motion-controller-model-on-openxr"></a>Unterstützung für das vom System bereitgestellte Motion Controller-Modell in OpenXR

Sowohl im Editor als auch zur Laufzeit steht jetzt in OpenXR Unterstützung für das vom System bereitgestellte Motion Controller-Modell zur Verfügung.

![Editor-Fenster mit zwei Motion Controller-Modellen](https://user-images.githubusercontent.com/3580640/116493405-89a55d80-a853-11eb-95ae-d430e6fdc8b4.png)

### <a name="support-for-hololens-2-articulated-hand-mesh-on-openxr"></a>Unterstützung für das artikulierte Hand-Mesh von HoloLens 2 in OpenXR

![Das auf dem Gerät ausgeführte Hand-Mesh in einer MRTK-Beispielszene](https://user-images.githubusercontent.com/3580640/112909923-32bb3580-90a7-11eb-925d-464b135edc61.png)

### <a name="support-for-controller-haptics-across-legacy-wmr-windows-xr-plugin-and-openxr"></a>Unterstützung für Controllerhaptik in Legacy-WMR, dem Windows XR-Plug-In und OpenXR

Unterstützung für Controllerhaptik wurde für Legacy-WMR, das Windows XR-Plug-In und OpenXR hinzugefügt. [#9735](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9735)

### <a name="support-for-eye-tracking-on-windows-xr-plugin"></a>Unterstützung für Eyetracking im Windows XR-Plug-In

Neu hinzugefügte Unterstützung für Anvisieren bei Verwendung der Mindestversionen 2.7.0 (Unity 2019), 4.4.2 (Unity 2020) oder 5.2.2 (Unity 2021) des Windows XR-Plug-Ins. [#9609](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9609)

### <a name="notable-bugfixes-and-changes"></a>Wichtige Fehlerbehebungen und Änderungen

- Die Zusammendrücken-Erkennung arbeitet jetzt reibungsloser. Es ist jetzt schwieriger, die Zusammendrücken-Geste versehentlich einzugeben. [#9576](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9576)
- Objekte behalten jetzt in der Objektmanipulatorkomponente durchgängig die Geschwindigkeit bei, wenn das Flag gesetzt ist. [#9733](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9733)
- Die Hintergrundprüfung prüft jetzt auf einen Boden, um Situationen zu verhindern, in denen die Kamera in der Umgebung befestigt wird oder der Benutzer im leeren Raum schwebt.[#9697](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9697)
- IsNearObject ist jetzt eine virtuelle Eigenschaft, was mehr Flexibilität beim Erweitern der Kugel oder des Poke-Zeigers bietet. [#9803](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9803)
- Schaltflächen zeigen jetzt das richtige Schlüsselwort an, wenn der verfügbare Sprachbefehl angezeigt wird. [#9824](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9824)
- Oculus-Controller verwenden jetzt die eigene eigenständige Schnellansicht, was Konflikte zwischen der MRTK-Visualisierung und der Visualisierung des Oculus-Integrationspakets verhindert. [#9589](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9589)
- Tastaturbezogene Skripts wurden geändert, um dem Verhalten in den neuesten Unity-Versionen (2019.4.25 und höher sowie 2020.3.2 und höher) zu entsprechen. Zum Zeitpunkt der Veröffentlichung besteht immer noch ein Fehler bei der automatischen Vervollständigung und ein Fehler im TMP-Eingabefeld (beide sind zu MRTK extern), die HoloLens betreffen. Weitere Informationen finden Sie unter [#9056](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9056) und [#9724](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9724).
- Verbesserte Leistung der Scrolling-Objektsammlung. Außerdem wurde ein Problem behoben, das zum Verlust von Material des GameObjects innerhalb der Sammlung beim Duplizieren führte. [#9813](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9813), [#9718](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9718)
- Im Scene Understanding-Demoskript wurde die Funktion `GetSceneObjectsOfType` hinzugefügt, um alle beobachteten Szenenobjekte einer bestimmten Art abzurufen. [#9524](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9524), [#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)
- Im Befehlszeilen-Buildtool werden nur Szenen in den Build aufgenommen, die durch das Flag `sceneList` oder `sceneListFile` gekennzeichnet sind (falls Flags vorhanden sind). [#9695](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9695)
- Im Buildtool gibt es eine neue Option zum Angeben eines Pfads zu `nuget.exe` und zum Verwenden dieses Pfads zum Ausführen der Paketwiederherstellung anstelle der Option `msbuild` (Standardoption). [#9556](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9556)
- Das Problem, bei dem die Verwendung des Windows XR-Plug-Ins zu veralteten Handgelenken und doppelten Hand-Meshes führen konnte, wurde behoben. [#9890](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9890)
- Das Problem, bei dem die Verwendung des automatischen Remotingfeatures des Windows XR-Plug-Ins zu fehlenden Eingaben und Interaktionen führen konnte, wurde behoben. [#9868](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9868)
- Das Problem wurde behoben, bei dem das BuildDeployWindow versuchte, für den Windows SDK-Pfad einen ungültigen Registrierungsschlüssel abzufragen. [#9664](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9664)
- Die glTF-Importmodule des MRTK sind jetzt optional. Wenn mehrere glTF-Importmodule vorhanden sind, können diejenigen des MRTK durch Hinzufügen von `MRTK_GLTF_IMPORTER_OFF` zur Symboldefinition von benutzerdefinierten Skripts deaktiviert werden. [#9658](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9658)
- Ein Problem wurde behoben, bei dem die Knuckles-Controllers unter OpenVR nicht ordnungsgemäß erkannt wurden. [#9881](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9881)
- Verringern der Anzahl der Zuweisungen pro Einzelbild beim Visualisieren des Hand-Meshs [#9756](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9756)
- Neu hinzugefügtes Menüelement zum Starten des MRTK-Beispielpakets (im Unity-Paket-Manager), um das Importieren von Beispielen zu vereinfachen [#9798](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9798)
- Die Anzahl der Warnungen zur Ladezeit beim Verwenden von Unity 2020.3 wurde verringert.
- Neu hinzugefügte Dokumentation zum Erstellen-Fenster-Feature: [Seite besuchen](../features/tools/build-window.md)

## <a name="known-issues"></a>Bekannte Probleme

### <a name="audio-demos-are-missing-an-asmdef-file-upm-package"></a>In den Audiodemos fehlt eine ASMDEF-Datei (UPM-Paket)

Beim Importieren von MRTK mithilfe des Mixed Reality Feature-Tools werden dem Projekt Beispiele und Demos über die Benutzeroberfläche des Unity-Paket-Managers hinzugefügt. Nach dem Importieren der Audiodemos verhält sich die Szene `WindowsMicrophoneStreamDemo.unity` nicht ordnungsgemäß. Dies ist die Folge einer fehlenden ASMDEF-Datei für das Beispiel.

Führen Sie die folgenden Schritte aus, um dieses [Problem](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9908) zu beheben:

- Kopieren Sie Library/PackageCache/com.microsoft.mixedreality.toolkit.examples@[...]/MRTK.Examples.asmdef in Ihren Ordner „Assets/Samples/Mixed Reality Toolkit Examples“
- Benennen Sie die kopierte Datei in „Examples“ um
- Öffnen Sie die Datei „Examples“
- Ersetzen Sie im Namenfeld den Inhalt durch „Examples“
- Klicken Sie auf „Übernehmen“
- Erstellen und Bereitstellen

Dieses Problem wird in einer zukünftigen MRTK-Version behoben.

### <a name="mrtk-build-window-triggers-indefinite-importing-assets-dialog-in-unity-20203"></a>Das MRTK-Buildfenster löst ein nicht endendes Dialogfeld „Importieren von Medienobjekten“ in Unity 2020.3 aus

Es besteht ein bekanntes [Problem](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9723) mit dem MRTK-Buildfenster in Unity 2020.3, bei dem nach dem erfolgreichen Ausführen eines UWP-Builds das Dialogfeld „Importieren von Medienobjekten“ nicht abgeschlossen wird. Dieses Problem wird in Zusammenarbeit mit Unity untersucht.

### <a name="text-mesh-pro-canvas-renderer-warnings-in-unity-2020"></a>Text Mesh Pro Canvas-Rendererwarnungen in Unity 2020

Wenn Unity 2020 verwendet wird, wird in den meisten MRTK-Beispielszenen die folgende Warnung protokolliert:

```txt
Please remove the CanvasRenderer component from the [TextMeshPro] GameObject as this component is no longer necessary.
```

Die Canvas-Rendererwarnung wurde in [TextMeshPro-Version 3.0.3](https://docs.unity3d.com/Packages/com.unity.textmeshpro@3.0/changelog/CHANGELOG.html#changes-3) hinzugefügt. Diese Warnung wirkt sich nicht auf die MRTK-Beispielszenen aus und kann über die Konsole entfernt werden. Weitere Details finden Sie unter [Issue 9811](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9811).