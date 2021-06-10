---
title: Versionshinweise zu MRTK 2.7
description: Versionshinweise zu MRTK Version 2.7
author: RogPodge
ms.author: roliu
ms.date: 05/27/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, XRSDK, Legacy XR, Leap Motion, Ultraleap
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 92c8705c70a2a6c1e25f1ed6b1f87eac1e5726e0
ms.sourcegitcommit: 11d5d7c3fdd59c1ebcfca34dbb6d84c05b481e5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/10/2021
ms.locfileid: "111897403"
---
# <a name="microsoft-mixed-reality-toolkit-27-release-notes"></a>Versionshinweise zu Microsoft Mixed Reality Toolkit 2.7

## <a name="whats-new-in-270"></a>Neuerungen in 2.7.0

### <a name="openxr-is-now-officially-supported-in-mrtk"></a>OpenXR wird jetzt offiziell im MRTK unterstützt.

Da die neuen OpenXR-Plug-Ins immer ausgereifter werden, unterstützt MRTK jetzt offiziell OpenXR. Im Vergleich zu früheren Releases haben wir Projekten mit OpenXR die folgenden Funktionen hinzugefügt:

- [Unterstützung für das vom System bereitgestellte Motion Controller-Modell](#support-for-the-system-provided-motion-controller-model-on-openxr)
- Unterstützung für WinMR-Gesten (Auswählen, Halten, Bearbeiten und Navigation) [#9843](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9843)
- [Unterstützung für Controller-Haptik](#support-for-controller-haptics-across-legacy-wmr-windows-xr-plugin-and-openxr)
- [Unterstützung für ein artikuliertes Handgitter auf HoloLens 2](#support-for-hololens-2-articulated-hand-mesh-on-openxr)
- Unterstützung der räumlichen Zuordnung auf HoloLens 2 [#9567](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9567) [, #9827](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9827)
- Unterstützung für Scene Understanding in HoloLens 2 [#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)

### <a name="legacy-xr-and-xr-sdk-data-providers-can-now-be-used-within-the-same-profile"></a>Legacy-XR- und XR SDK-Datenanbieter können jetzt innerhalb desselben Profils verwendet werden.

Datenanbieter werden jetzt auch nur geladen, wenn die entsprechende Pipeline ausgewählt ist, sodass sowohl Legacy-XR- als auch XR SDK-Datenanbieter innerhalb desselben Profils gleichzeitig vorhanden sein können. Um dies zu berücksichtigen, sind Legacy-XR- und XR SDK-Datenanbieter jetzt auf verschiedenen Registerkarten in der Profilansicht organisiert, damit Benutzer bestimmen können, ob sie über das richtige Profil für ihre XR-Zielpipeline verfügen.

![Legacy- und XR SDK-Datenanbieter können jetzt unter einem einzigen Profil vereinheitlicht werden.](../features/images/xrsdk/LegacyAndXrsdkUnified.png)

Um dies zu berücksichtigen, werden NULL-Datenanbieter jetzt nicht mehr geladen und im Profilinspektor angezeigt. Benutzer können `Show null data providers in the profile inspector` unter **Bearbeiten -> Projekteinstellungen -> Mixed Reality Toolkit** umschalten, um unerwartetes Verhalten bei fehlenden Datenanbietern zu debuggen.

![NULL-Datenanbieter sind jetzt standardmäßig ausgeblendet ](https://user-images.githubusercontent.com/39840334/115093658-ead24600-9ecf-11eb-91c2-486a37f69aba.png)
 ![ Umschalten zeigt NULL-Datenanbieter im Profilinspektor an](https://user-images.githubusercontent.com/39840334/115093670-f6257180-9ecf-11eb-96ec-ffe44a225a55.png)

### <a name="added-experience-settings-and-an-associated-mixed-reality-scene-content-behavior"></a>Experience Settings and an associated Mixed Reality Scene Content behavior (Benutzerfreundlichkeitseinstellungen und ein zugeordnetes verhalten Mixed Reality Szeneninhalt hinzugefügt)

Benutzer können jetzt Einstellungen für die [Benutzeroberfläche](../features/experience-settings/experience-settings.md)konfigurieren, sodass MRTK [Mixed Reality Szeneninhalt](../features/experience-settings/scene-content.md) entsprechend der Zielerfahrung anzeigen kann.

Wenn die vorherigen Einstellungen für die Skalierung der Benutzeroberfläche nicht mit dem neuen Profil "Benutzeroberflächeneinstellungen" übereinstimmen, werden sie im Inspektor aufgefordert, sie zu korrigieren.

![Erfahrungsskalamigration](https://user-images.githubusercontent.com/39840334/114946863-d70bde80-9e00-11eb-9859-fa40d40d2b36.gif)

### <a name="the-redesigned-configurator-now-guides-the-user-through-the-setup-process"></a>Der neu gestaltete Konfigurator führt den Benutzer jetzt durch den Einrichtungsprozess.

Der neue MRTK-Konfigurator bietet Benutzern schritt-für-Schritt-Anleitungen, um das Projekt ordnungsgemäß für die XR-Entwicklung und die Verwendung mit MRTK zu konfigurieren. Es behandelt die Auswahl der XR-Pipeline, das Abrufen der plattformspezifischen Plug-Ins, das Importieren von TextMeshPro, das Anzeigen der Beispiele (bei Verwendung von UPM) und andere zuvor empfohlene Einstellungen für das Projekt.

![Konfigurator mit der Liste der Pipelines](images/Configurator.png)

### <a name="graduated-teleport-hotspot"></a>Gestaffelter Teleport-Hotspot

Eine neue [Teleport-Hotspotkomponente](../features/teleport-system/teleport-hotspot.md) wurde umschlossen. Sie können Ihrem GameObject einen Teleport-Hotspot hinzufügen, um sicherzustellen, dass sich der Benutzer an einer bestimmten Position und Ausrichtung befindet, wenn er an diesen Ort teleportieren soll.

![Beispiel für Teleport-Hotspot](images/TeleportHotspot.gif)

### <a name="graduated-dwell"></a>Gestaffelte Verweildauer

Die Verweilfunktion und das Beispiel wurden nun aus experimentell abgeleitet. Neue Beispiele für volumetrische HoloLens 2 Schaltflächen im Stil sind in der Beispielszene enthalten.

![Verweilen eines Heros](../features/images/dwell/MRTK_UX_Dwell.png)

### <a name="added-support-for-leap-motion-unity-modules-version-460-470-471-and-480"></a>Unterstützung für Leap Motion Unity-Module, Version 4.6.0, 4.7.0, 4.7.1 und 4.8.0 hinzugefügt

Die Unterstützung für die neuesten Versionen der [Leap Motion Unity-Module](https://developer.leapmotion.com/unity) ist jetzt mit MRTK 2.7.0 kompatibel.  Weitere Informationen finden Sie unter [Konfigurieren von MRTK für Leap Motion.](../supported-devices/leap-motion-mrtk.md)

Vielen Dank an für die Mitwirkung an @jackyangzzh der neuen LeapMotionOrientationExample-Szene!

### <a name="targeted-speech-events-raised-no-longer-restricted-to-gaze-pointers"></a>Zielgerichtete Sprachereignisse, die nicht mehr auf Anvisiertzeiger beschränkt sind

Bisher konnten zielgerichtete Sprachereignisse nur für Objekte ausgelöst werden, auf die mit dem Anvisierten-Zeiger der Fokus lag. Jetzt können Objekte Sprachereignisse empfangen, wenn sie durch einen Zeiger fokussiert sind.

![Sprachereignisse mit Fernzeigern](https://user-images.githubusercontent.com/39840334/117516612-6fa00500-af4e-11eb-94ba-d5fb2ed4e7de.gif)

### <a name="ported-texttospeech-from-htk-to-mrtk"></a>Portiertes TextToSpeech von HTK zu MRTK

Das beliebte TextToSpeech-Skript ist nun im MRTK verfügbar, damit Sie mithilfe von Sprache aus Text auf der UWP-Plattform generieren [`SpeechSynthesizer`](/uwp/api/windows.media.speechsynthesis.speechsynthesizer) können. Außerdem wurde eine Beispielszene hinzugefügt, um das Feature zu veranschaulichen.

### <a name="support-for-the-system-provided-motion-controller-model-on-openxr"></a>Unterstützung für das vom System bereitgestellte Motion Controller-Modell in OpenXR

Unterstützung sowohl im Editor als auch zur Laufzeit für das vom System bereitgestellte Motion Controller-Modell in OpenXR wurde hinzugefügt.

![Editor-Fenster mit zwei Motion Controller-Modellen](https://user-images.githubusercontent.com/3580640/116493405-89a55d80-a853-11eb-95ae-d430e6fdc8b4.png)

### <a name="support-for-hololens-2-articulated-hand-mesh-on-openxr"></a>Unterstützung für HoloLens 2 artikuliertes Handgitternetz in OpenXR

![Das Handgitternetz, das auf dem Gerät in einer MRTK-Beispielszene ausgeführt wird](https://user-images.githubusercontent.com/3580640/112909923-32bb3580-90a7-11eb-925d-464b135edc61.png)

### <a name="support-for-controller-haptics-across-legacy-wmr-windows-xr-plugin-and-openxr"></a>Unterstützung für Controller-Haptik in Legacy-WMR, Windows XR-Plug-In und OpenXR

Unterstützung für Controllerhaptik für ältere WMR-, Windows XR-Plug-Ins und OpenXR-Dateien wurde hinzugefügt. [#9735](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9735)

### <a name="support-for-eye-tracking-on-windows-xr-plugin"></a>Unterstützung für Eyetracking im Windows XR-Plug-In

Unterstützung für das Anvieren mit den Augen bei Verwendung der Windows XR-Plug-In-Mindestversionen 2.7.0 (Unity 2019), 4.4.2 (Unity 2020) und 5.2.2 (Unity 2021) wurde hinzugefügt. [#9609](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9609)

### <a name="notable-bugfixes-and-changes"></a>Wichtige Fehlerbehebungen und Änderungen

- Die Pincherkennung wurde reibungsloser gestaltet. Es ist jetzt schwieriger, die Geste versehentlich zu löschen. [#9576](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9576)
- Objekte mit der Objektmanipulatorkomponente behalten jetzt die Geschwindigkeit bei der Freigabe bei, wenn das Flag festgelegt ist. [#9733](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9733)
- Der Hintergrund prüft jetzt auf einen Boden, um Situationen zu verhindern, in denen die Kamera in die Umgebung eingeclipt werden kann oder in denen der Benutzer mit dem Mauszeiger auf leeren Raum zeigen muss. [#9697](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9697)
- IsNearObject ist jetzt eine virtuelle Eigenschaft, die mehr Flexibilität beim Erweitern der Kugel oder des Pfeilzeigers bietet. [#9803](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9803)
- Schaltflächen zeigen nun das richtige Schlüsselwort an, wenn der verfügbare Sprachbefehl angezeigt wird. [#9824](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9824)
- Oculus-Controller verwenden jetzt eine eigene eigenständige Schnellansicht, die verhindert, dass die MRTK-Visualisierung mit der Visualisierung des Oculus-Integrationspakets in Konflikt tritt. [#9589](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9589)
- Tastaturbezogene Skripts wurden so geändert, dass sie dem Verhalten in den neuesten Unity-Versionen (2019.4.25 und höher & 2020.3.2+) entsprechen. Ab dem Release gibt es immer noch einen Fehler bei der automatischen Vervollständigung und einen TMP-Eingabefeldfehler (beide sind extern für MRTK) und wirken sich auf HoloLens aus. Weitere Informationen finden Sie unter [#9056](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9056) und [#9724](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9724).
- Verbesserte Leistung der Bildlaufobjektauflistung. Außerdem wurde ein Problem behoben, das dazu führte, dass GameObject innerhalb der Sammlung materialverliert, wenn es dupliziert wurde. [#9813](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9813), [#9718](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9718)
- Im Scene Understanding-Demoskript wurde die -Funktion hinzugefügt, `GetSceneObjectsOfType` um alle beobachteten Szenenobjekte einer bestimmten Art abzurufen. [#9524](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9524), [#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)
- Im Befehlszeilenbuildtool werden nur Szenen, die durch die `sceneList` Flags oder `sceneListFile` (wenn ein Flag vorhanden ist) angegeben werden, in den Build aufgenommen. [#9695](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9695)
- Im Buildtool gibt es eine neue Option, um einen Pfad zu anzugeben und zu verwenden, um die `nuget.exe` Paketwiederherstellung durchzuführen, anstatt zu verwenden `msbuild` (die Standardoption). [#9556](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9556)
- Es wurde ein Problem behoben, bei dem die Verwendung des Windows XR-Plug-Ins zu veralteten Handverbindungen und doppelten Handgittern führen konnte. [#9890](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9890)
- Es wurde ein Problem behoben, bei dem die Verwendung des automatischen Remotingfeatures des Windows XR-Plug-Ins zu fehlenden Eingaben und Interaktionen führte. [#9868](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9868)
- Es wurde ein Problem behoben, bei dem BuildDeployWindow versucht hat, einen ungültigen regulären Schlüssel für den Windows SDK Pfad abzufragen. [#9664](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9664)
- Die glTF-Importeure von MRTK sind jetzt optional. Wenn mehrere glTF-Importeure vorhanden sind, können MRTKs deaktiviert werden, indem `MRTK_GLTF_IMPORTER_OFF` sie den benutzerdefinierten Skripterstellungs-Define-Symbolen hinzugefügt werden. [#9658](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9658)
- Es wurde ein Problem behoben, bei dem die Knuckles-Controller in OpenVR nicht ordnungsgemäß erkannt wurden. [#9881](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9881)
- Reduzieren Sie die Anzahl der Pro-Frame-Zuordnungen, wenn Sie das Handgitternetz [#9756](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9756)
- Ein Menüelement zum Starten des MRTK-Beispielpakets (in Unity Paket-Manager) wurde hinzugefügt, um das Importieren [von](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9798) Beispielen #9798
- Reduzierte Anzahl von Ladezeitwarnungen bei Verwendung von Unity 2020.3.
- Dokumentation zum Buildfensterfeature hinzugefügt: [Besuchen Sie die Seite.](/windows/mixed-reality/mrtk-unity/features/tools/build-window)

## <a name="known-issues"></a>Bekannte Probleme

### <a name="audio-demos-are-missing-an-asmdef-file-upm-package"></a>Bei Audiodemos fehlt eine Asmdef-Datei (UPM-Paket).

Beim Importieren von MRTK über das Mixed Reality Feature-Tool werden dem Projekt mithilfe der Unity Paket-Manager-Benutzeroberfläche Beispiele und Demos hinzugefügt. Nach dem Importieren der Audiodemos verhält sich die `WindowsMicrophoneStreamDemo.unity` Szene nicht ordnungsgemäß. Dies ist das Ergebnis einer fehlenden ASMDEF-Datei für das Beispiel.

Führen Sie die folgenden Schritte aus, um dieses [Problem](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9908)zu umgehen:

- Copy Library/PackageCache/com.microsoft.mixedreality.toolkit.examples@[...] /MRTK. Examples.asmdef im Ordner "Assets/Samples/Mixed Reality Toolkit Examples" (Beispiele für das Toolkit)
- Umbenennen der kopierten Datei in Beispiele
- Öffnen sie die Datei "Beispiele".
- Ersetzen Sie im Feld Name den Inhalt durch Beispiele.
- Klicken Sie auf Übernehmen.
- Erstellen und Bereitstellen

Dieses Problem wird in einer zukünftigen MRTK-Version behoben.

### <a name="mrtk-build-window-triggers-indefinite-importing-assets-dialog-in-unity-20203"></a>Das MRTK-Buildfenster löst in Unity 2020.3 das unbefristete Dialogfeld "Importieren von Ressourcen" aus.

Es gibt ein bekanntes [Problem](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9723) mit dem MRTK-Buildfenster in Unity 2020.3, bei dem das Dialogfeld "Importieren von Ressourcen" nach erfolgreicher Ausführung eines UWP-Builds nicht abgeschlossen ist. Dieses Problem wird in Zusammenarbeit mit Unity untersucht.

### <a name="text-mesh-pro-canvas-renderer-warnings-in-unity-2020"></a>Text Mesh Pro Canvas Renderer-Warnungen in Unity 2020

Die folgende Warnung wird in den meisten MRTK-Beispielszenen protokolliert, während Unity 2020 verwendet wird:

```txt
Please remove the CanvasRenderer component from the [TextMeshPro] GameObject as this component is no longer necessary.
```

Die Canvas-Rendererwarnung wurde in [TextMeshPro Version 3.0.3](https://docs.unity3d.com/Packages/com.unity.textmeshpro@3.0/changelog/CHANGELOG.html#changes-3)hinzugefügt.  Diese Warnung hat keine Auswirkungen auf die Beispielszenen des MRTK und kann über die Konsole gelöscht werden. Weitere Informationen finden Sie unter [Issue 9811 (Problem 9811).](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9811)
