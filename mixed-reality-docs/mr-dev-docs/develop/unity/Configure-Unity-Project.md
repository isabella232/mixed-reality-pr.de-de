---
title: Konfigurieren Ihres Projekts ohne MRTK
description: Erfahren Sie, wie Sie ein neues Unity-Projekt für Windows Mixed Reality ohne das Mixed Reality Toolkit konfigurieren.
author: hferrone
ms.author: alexturn
ms.date: 07/29/2020
ms.topic: article
keywords: Unity, Mixed Reality, Entwicklung, erste Schritte, neues Projekt, Windows Mixed Reality, UWP, XR, Leistung
ms.openlocfilehash: 85f8dee3208ce2c2a3bd328641544cbba0525cabdd1bf99404065572aeb354cf
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210981"
---
# <a name="configuring-your-project-without-mrtk"></a>Konfigurieren von Projekten ohne MRTK

Windows Mixed Reality (WMR) ist eine Microsoft-Plattform, die als Teil des Windows 10 Betriebssystems eingeführt wurde. Mit der WMR-Plattform können Sie Anwendungen erstellen, die digitale Inhalte auf holografischen und VR-Anzeigegeräten rendern.

Während Microsoft und die Community Open Source-Tools wie das [Mixed Reality Toolkit (MRTK)](/windows/mixed-reality/mrtk-unity/configuration/usingupm) erstellt haben, mit denen die WMR-Umgebung automatisch eingerichtet wird, möchten viele Entwickler ihre Erfahrungen von Grund auf erstellen.  In der folgenden Dokumentation wird veranschaulicht, wie Sie ein Projekt ordnungsgemäß für Mixed Reality Entwicklung einrichten, unabhängig davon, ob Sie MRTK verwenden oder nicht.  Die Einstellungen, die Sie ändern müssen, sind in zwei Kategorien unterteilt: Einstellungen pro Projekt und Einstellungen pro Szene.

> [!NOTE]
> Sie können MRTK später immer importieren, sodass es keineRlei Einbußen beim ersten Durchlaufen der manuellen Route gibt.

Wenn Sie sich für das manuelle WMR-Setup entscheiden, werden die Einstellungen, die Sie ändern müssen, in zwei Kategorien unterteilt: pro Projekt und pro Szene.

## <a name="per-project-settings"></a>Projektspezifische Einstellungen

Wenn Sie desktop VR als Ziel verwenden möchten, empfehlen wir, die pc Standalone Platform zu verwenden, die standardmäßig für ein neues Unity-Projekt ausgewählt ist:

![Screenshot des Fensters "Build Einstellungen", das im Unity-Editor geöffnet ist, wobei PC, Mac & eigenständige Plattform hervorgehoben ist](images/wmr-config-img-3.png)

Wenn Sie HoloLens 2 als Ziel verwenden, müssen Sie zur universellen Windows-Plattform wechseln:

1.  Wählen Sie **Datei > Build Einstellungen... aus.**
2.  Wählen Sie in der Liste Plattform die Option **Universal Windows Platform** und dann Plattform **wechseln** aus.
3.  Legen Sie **Architektur** auf **ARM 64** fest
4.  Legen Sie **Zielgerät** auf **HoloLens** fest
5.  Legen Sie **Buildtyp** auf **D3D** fest
6.  Legen Sie **UWP SDK** auf **Zuletzt installiert** fest
7.  Legen Sie **Buildkonfiguration** auf **Release** fest, da beim Debuggen bekannte Leistungsprobleme auftreten.

![Screenshot des Fensters "Build Einstellungen" im Unity-Editor mit hervorgehobener "Universal Windows Platform"](images/wmr-config-img-4.png)

Nachdem Sie Ihre Plattform festgelegt haben, müssen Sie Unity mitteilen, dass beim Exportieren eine [immersive Ansicht](../../design/app-views.md) anstelle einer 2D-Ansicht erstellt werden soll.

### <a name="for-xrsdk"></a>Für XRSDK 

1. Navigieren Sie im Unity-Editor zu **> Project Einstellungen bearbeiten,** und wählen Sie **XR-Plug-In-Verwaltung** aus.

2. Wählen Sie **XR-Plug-In-Verwaltung installieren aus.**

![Screenshot: geöffnetes fenster "Project Einstellungen" im Unity-Editor mit hervorgehobener XR-Plug-In-Verwaltung](images/wmr-config-img-5.png)

3. Wählen Sie **XR beim Start initialisieren** und **Windows Mixed Reality**

![Screenshot: Fenster "Einstellungen" Project im Unity-Editor mit hervorgehobener XR-Plug-In-Verwaltung geöffnet](images/wmr-config-img-7.png)

4. Erweitern Sie den Abschnitt **XR-Plug-In-Verwaltung,** und klicken Sie auf die Registerkarte **Windows Plattform Einstellungen.**
5. Wenn Sie Unity 2020 oder höher verwenden, werden die Optionen zum Aktivieren von **OpenXR** oder **Windows Mixed Reality** angezeigt. 
    * Sie können eine der beiden Laufzeiten auswählen.  Wenn Sie speziell für die HoloLens 2 oder HP Reverb G2 entwickeln und **openXR** ausprobieren möchten, wählen Sie das Feld OpenXR aus, und lesen Sie unseren Leitfaden [zum Verwenden des Mixed Reality OpenXR-Plug-Ins für Unity,](./xr-project-setup.md) um sich für diese Geräte ordnungsgemäß einzurichten, bevor Sie zu diesem Tutorial zurückkehren.

> [!NOTE]
> Ab Unity 2020 LTS setzt Microsoft auf die Entwicklung mit OpenXR.  Bei der Migration zu diesem Pfad wird in Unity 2021.1 das Windows XR-Plug-In veraltet sein und in 2021.2 entfernt, sodass OpenXR der einzige unterstützte Pfad ist. Weitere Informationen finden Sie unter [Verwenden des Mixed Reality OpenXR-Plug-Ins.](./xr-project-setup.md)

6. Wenn Sie sich  für das Windows Mixed Reality-Plug-In entscheiden, aktivieren Sie alle Kontrollkästchen, und legen Sie **den Tiefenübermittlungsmodus** auf **Tiefe 16 Bit** fest.

![Screenshot: Fenster "Einstellungen" Project im Unity-Editor geöffnet, wobei Windows Mixed Reality Abschnitt hervorgehoben ist](images/wmr-config-img-8.png)

### <a name="for-legacy-xr"></a>Für Legacy-XR 

> [!CAUTION]
> Legacy-XR ist in Unity 2019 veraltet und wurde in Unity 2020 entfernt.

1. Öffnen Sie **Player Einstellungen...** aus der **Build Einstellungen... fenster** und erweitern Sie die **Gruppe XR Einstellungen**
2. Wählen Sie im Abschnitt **XR Einstellungen** virtual **reality supported (Virtual Reality unterstützt)** aus, um die Liste Virtual Reality-Geräte hinzuzufügen.
3. Festlegen des **Tiefenformats** auf **16-Bit-Tiefe** und Aktivieren der **Tiefenpufferfreigabe**
4. Festlegen **des Stereorenderingmodus** auf **eine Einzeldurchlaufinstanz**
5. Wählen Sie **WSA Holographic Remoting Supported (Unterstütztes WSA Holographic Remoting)** aus, wenn Sie Holographic Remoting verwenden möchten. 

![Screenshot des fensters "Project"-Einstellungen, das im Unity-Editor geöffnet ist, wobei der Abschnitt "Playereinstellungen" hervorgehoben ist](images/wmr-config-img-9.png)

### <a name="updating-the-manifest"></a>Aktualisieren des Manifests

Ihre App kann jetzt holografisches Rendering und räumliche Eingaben verarbeiten. Ihre App muss jedoch die entsprechenden Funktionen im Manifest deklarieren, um bestimmte Funktionen nutzen zu können. Sie finden Ihre Projektfunktionen, indem Sie zu Player Einstellungen > Einstellungen for Universal Windows Platform > Publishing Einstellungen > Capabilities (Funktionen für die **universelle Windows-Plattform > Veröffentlichen Einstellungen >) gehen.** 

Es wird empfohlen, die Manifestdeklarationen in Unity zu erstellen, um sie in alle zukünftigen Projekte einzubinden, die Sie exportieren. Die anwendbaren Funktionen zum Aktivieren häufig verwendeter Unity-APIs für Mixed Reality sind:

|  Funktion  |  APIs, die Funktionen erfordern | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver (Zugriff auf Gitternetze für [räumliche Zuordnungen](../../design/spatial-mapping.md) auf HoloLens) &mdash; *Für die allgemeine räumliche Nachverfolgung des Headsets ist keine Funktion erforderlich.* | 
|  Webcam  |  PhotoCapture und VideoCapture | 
|  PicturesLibrary/VideosLibrary  |  PhotoCapture bzw. VideoCapture (beim Speichern der erfassten Inhalte) | 
|  Mikrofon  |  VideoCapture (beim Erfassen von Audio), DictationRecognizer, GrammarRecognizer und KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer (und zur Verwendung des Unity Profilers) | 

### <a name="quality-settings"></a>Qualitätseinstellungen

HoloLens verfügt über eine GPU der mobilen Klasse. Wenn Ihre App auf HoloLens ausgerichtet ist, sollten Sie mit den Qualitätseinstellungen in Ihrer App beginnen, die für die schnellste Leistung optimiert sind, um sicherzustellen, dass sie die vollständige Bildfrequenz beibehält.  Sobald Sie sich weiter in Ihrer Entwicklung befinden, können Sie die Qualitätseinstellungen in Betracht ziehen, um das richtige Gleichgewicht zwischen Qualität und Leistung zu finden: 

1. Wählen Sie **Edit > Project Einstellungen > Quality (> Project Einstellungen > Qualität bearbeiten)** aus. 
2. Wählen Sie die **Dropdownliste** unter dem  ****   Windows Store-Logo und dann  **Sehr niedrig** aus. Sie wissen, dass die Einstellung ordnungsgemäß angewendet wird, wenn das Feld in der Windows Store Spalte und die Zeile "Sehr niedrig" grün ist. 
3. Wählen Sie im Abschnitt **Schatten** die   Option Schatten **deaktivieren** aus. 

![Screenshot des fensters "Project"-Einstellungen, das im Unity-Editor geöffnet ist, wobei der Abschnitt "Qualitätseinstellungen" hervorgehoben ist](images/wmr-config-img-10.png)<br>
*Unity-Qualitätseinstellungen*

## <a name="per-scene-settings"></a>Einstellungen pro Szene

### <a name="unity-camera-settings"></a>Unity-Kameraeinstellungen

Wenn **Virtual Reality Unterstützt aktiviert ist,** verarbeitet die [Unity-Kamerakomponente](camera-in-unity.md) die [Kopfverfolgung und stereoskopisches Rendering.](../platform-capabilities-and-apis/rendering.md) Das bedeutet, dass Sie das Hauptkameraobjekt nicht durch eine benutzerdefinierte Kamera ersetzen müssen.

Wenn Ihre App speziell auf HoloLens ausgerichtet ist, müssen Sie einige Einstellungen ändern, um die Anzeige des Geräts zu optimieren. Mit diesen Einstellungen können Ihre holografischen Inhalte der physischen Welt angezeigt werden:

1. Wählen Sie in der **Hierarchie** die **Hauptkamera aus.**
2. Legen Sie im **Inspektorbereich** die **Transformationsposition** auf **0, 0, 0 fest,** damit die Position des Kopfes des Benutzers am Unity-Ursprung beginnt.
3. Ändern Sie **Clear Flags (Flags** löschen) in **Solid Color (Volltonfarbe).**
4. Ändern Sie die **Hintergrundfarbe** in **RGBA 0,0,0,0**. Schwarz wird in HoloLens als transparent gerendert.
5. Ändern der **Clippingebenen– in** der Nähe des [HoloLens empfohlenen](camera-in-unity.md#using-clipping-planes) 0,85 (Meter).

![Screenshot der geöffneten Inspektorregisterkarte im Unity-Editor](images/wmr-config-img-11.png)<br>
*Unity-Kameraeinstellungen*

> [!IMPORTANT]
> Wenn Sie eine neue Kamera löschen und erstellen, stellen Sie sicher, dass Ihre neue Kamera als **MainCamera** gekennzeichnet ist.

## <a name="next-steps"></a>Nächste Schritte

Nachdem Ihr Projekt nun bereit ist, können Sie mit der Entwicklung Ihrer Mixed Reality beginnen:

* Hinzufügen [von Kernbausteinen](unity-development-overview.md#2-core-building-blocks)
* Sehen Sie sich die verfügbaren [Plattformfunktionen und APIs](unity-development-overview.md#3-advanced-features) an.
* Erfahren Sie, wie Sie [Ihre App bereitstellen.](../platform-capabilities-and-apis/using-visual-studio.md#)
* Verwenden des [Mixed Reality Simulators](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="see-also"></a>Siehe auch
* [Installieren der Tools](../install-the-tools.md)