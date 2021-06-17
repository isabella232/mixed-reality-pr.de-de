---
title: Konfigurieren Ihres Projekts ohne MRTK
description: Erfahren Sie, wie Sie ein neues Unity-Projekt für Windows Mixed Reality ohne das Mixed Reality Toolkit konfigurieren.
author: hferrone
ms.author: alexturn
ms.date: 07/29/2020
ms.topic: article
keywords: Unity, Mixed Reality, Entwicklung, erste Schritte, neues Projekt, Windows Mixed Reality, UWP, XR, Leistung
ms.openlocfilehash: c496dc415ff09eea3015b5195e131554c43a98f1
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110257"
---
# <a name="configuring-your-project-without-mrtk"></a>Konfigurieren von Projekten ohne MRTK

Windows Mixed Reality (WMR) ist eine Microsoft-Plattform, die als Teil des Windows 10 Betriebssystems eingeführt wurde. Mit der WMR-Plattform können Sie Anwendungen erstellen, die digitale Inhalte auf holografischen und VR-Anzeigegeräten rendern.

Während Microsoft und die Community Open Source-Tools wie das [Mixed Reality Toolkit (MRTK)](/windows/mixed-reality/mrtk-unity/configuration/usingupm) erstellt haben, mit denen die WMR-Umgebung automatisch eingerichtet wird, möchten viele Entwickler ihre Erfahrungen von Grund auf erstellen.  In der folgenden Dokumentation wird veranschaulicht, wie Sie ein Projekt ordnungsgemäß für Mixed Reality Entwicklung einrichten, unabhängig davon, ob Sie MRTK verwenden oder nicht.  Die Einstellungen, die Sie ändern müssen, sind in zwei Kategorien unterteilt: Einstellungen pro Projekt und Einstellungen pro Szene.

> [!NOTE]
> Sie können MRTK später immer importieren, sodass es keineRlei Einbußen beim ersten Durchlaufen der manuellen Route gibt.

Wenn Sie sich für das manuelle WMR-Setup entscheiden, werden die Einstellungen, die Sie ändern müssen, in zwei Kategorien unterteilt: pro Projekt und pro Szene.

## <a name="per-project-settings"></a>Projektspezifische Einstellungen

Wenn Sie desktop VR als Ziel verwenden möchten, empfehlen wir, die pc Standalone Platform zu verwenden, die standardmäßig für ein neues Unity-Projekt ausgewählt ist:

![Screenshot des Fensters "Buildeinstellungen", das im Unity-Editor geöffnet ist, wobei PC, Mac & eigenständige Plattform hervorgehoben ist](images/wmr-config-img-3.png)

Wenn Sie HoloLens 2 als Ziel haben, müssen Sie zum Universelle Windows-Plattform wechseln:

1.  Wählen Sie **Datei > Buildeinstellungen... aus.**
2.  Wählen Sie **Universelle Windows-Plattform** in der Liste Plattform und dann **Plattform wechseln** aus.
3.  Legen Sie **Architektur** auf **ARM 64** fest
4.  Legen Sie **Zielgerät** auf **HoloLens** fest
5.  Legen Sie **Buildtyp** auf **D3D** fest
6.  Legen Sie **UWP SDK** auf **Zuletzt installiert** fest
7.  Legen Sie **Buildkonfiguration** auf **Release** fest, da beim Debuggen bekannte Leistungsprobleme auftreten.

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor mit hervorgehobener Universelle Windows-Plattform](images/wmr-config-img-4.png)

Nachdem Sie Ihre Plattform festgelegt haben, müssen Sie Unity mitteilen, dass beim Exportieren eine [immersive Ansicht](../../design/app-views.md) anstelle einer 2D-Ansicht erstellt werden soll.

### <a name="for-xrsdk"></a>Für XRSDK 

1. Navigieren Sie im Unity-Editor zu **> Projekteinstellungen bearbeiten,** und wählen Sie **XR-Plug-In-Verwaltung** aus.

2. Wählen Sie **XR-Plug-In-Verwaltung installieren aus.**

![Screenshot: Geöffnetes Fenster "Projekteinstellungen" im Unity-Editor mit hervorgehobener XR-Plug-In-Verwaltung](images/wmr-config-img-5.png)

3. Wählen Sie **XR beim Start initialisieren** und **Windows Mixed Reality**

![Screenshot: Fenster "Projekteinstellungen" im Unity-Editor mit hervorgehobener XR-Plug-In-Verwaltung](images/wmr-config-img-7.png)

4. Erweitern Sie den Abschnitt **XR-Plug-In-Verwaltung,** und wählen Sie die Registerkarte **Windows Platform Settings (Windows-Plattformeinstellungen)** aus.
5. Wenn Sie Unity 2020 oder höher verwenden, werden die Optionen zum Überprüfen von **OpenXR** oder **Windows Mixed Reality** angezeigt. 
    * Sie können eine der beiden Laufzeiten auswählen.  Wenn Sie speziell für die HoloLens 2 oder HP Reverb G2 entwickeln und **openXR** ausprobieren möchten, wählen Sie das Feld OpenXR aus, und lesen Sie unseren Leitfaden [zum Verwenden des Mixed Reality OpenXR-Plug-Ins für Unity,](openxr-getting-started.md) um sich für diese Geräte ordnungsgemäß einzurichten, bevor Sie zu diesem Tutorial zurückkehren.

> [!NOTE]
> Ab Unity 2020 LTS setzt Microsoft auf die Entwicklung mit OpenXR.  Bei der Migration zu diesem Pfad wird in Unity 2021.1 das Windows XR-Plug-In veraltet sein und in 2021.2 entfernt, sodass OpenXR der einzige unterstützte Pfad ist. Weitere Informationen finden Sie unter [Verwenden des Mixed Reality OpenXR-Plug-Ins.](openxr-getting-started.md)

6. Wenn Sie sich  für das Windows Mixed Reality-Plug-In entscheiden, aktivieren Sie alle Kontrollkästchen, und legen Sie **Den Tiefenübermittlungsmodus** auf **Tiefe 16 Bit** fest.

![Screenshot: Geöffnetes Fenster "Projekteinstellungen" im Unity-Editor mit hervorgehobener Windows Mixed Reality Abschnitt](images/wmr-config-img-8.png)

### <a name="for-legacy-xr"></a>Für Legacy-XR 

> [!CAUTION]
> Legacy-XR ist in Unity 2019 veraltet und wurde in Unity 2020 entfernt.

1. Öffnen **Sie Playereinstellungen...** aus den **Buildeinstellungen... Fenster** und Erweitern der Gruppe **"XR-Einstellungen"**
2. Wählen Sie im Abschnitt **XR-Einstellungen** die Option **Virtual Reality Unterstützt** aus, um die Liste Virtual Reality-Geräte hinzuzufügen.
3. Festlegen des **Tiefenformats** auf **16-Bit-Tiefe** und Aktivieren der **Tiefenpufferfreigabe**
4. Festlegen **des Stereorenderingmodus** auf **eine Einzeldurchlaufinstanz**
5. Wählen Sie **WSA Holographic Remoting Supported (Unterstütztes WSA Holographic Remoting)** aus, wenn Sie Holographic Remoting verwenden möchten. 

![Screenshot: Geöffnetes Fenster "Projekteinstellungen" im Unity-Editor mit hervorgehobenen Player-Einstellungen](images/wmr-config-img-9.png)

### <a name="updating-the-manifest"></a>Aktualisieren des Manifests

Ihre App kann jetzt holografisches Rendering und räumliche Eingaben verarbeiten. Ihre App muss jedoch die entsprechenden Funktionen im Manifest deklarieren, um bestimmte Funktionen nutzen zu können. Sie finden Ihre Projektfunktionen unter **Playereinstellungen > Einstellungen für Universelle Windows-Plattform > Veröffentlichungseinstellungen > Funktionen**. 

Es wird empfohlen, die Manifestdeklarationen in Unity zu erstellen, um sie in alle zukünftigen Projekte einzubinden, die Sie exportieren. Die anwendbaren Funktionen zum Aktivieren häufig verwendeter Unity-APIs für Mixed Reality sind:

|  Funktion  |  APIs, die Funktionen erfordern | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver (Zugriff auf [Raumzuordnungsgitternetze](../../design/spatial-mapping.md) auf HoloLens) &mdash; *Keine Funktion für allgemeine räumliche Nachverfolgung des Headsets erforderlich* | 
|  Webcam  |  PhotoCapture und VideoCapture | 
|  PicturesLibrary/VideosLibrary  |  PhotoCapture bzw. VideoCapture (beim Speichern des erfassten Inhalts) | 
|  Mikrofon  |  VideoCapture (beim Erfassen von Audio), DictationRecognizer, GrammarRecognizer und KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer (und zur Verwendung des Unity Profilers) | 

### <a name="quality-settings"></a>Qualitätseinstellungen

HoloLens verfügt über eine GPU der Mobilen Klasse. Wenn Ihre App HoloLens als Ziel verwendet, sollten Sie mit den Qualitätseinstellungen in Ihrer App beginnen, die für die schnellste Leistung optimiert sind, um sicherzustellen, dass sie die vollständige Bildfrequenz beibehält.  Sobald Sie sich weiter in Ihrer Entwicklung befinden, können Sie die Qualitätseinstellungen in Betracht ziehen, um das richtige Gleichgewicht zwischen Qualität und Leistung zu finden: 

1. Wählen Sie **> Projekteinstellungen > Qualität bearbeiten** aus. 
2. Wählen Sie die **Dropdownliste** unter dem  **Windows Store-Logo**   und dann Sehr  **niedrig** aus. Sie wissen, dass die Einstellung ordnungsgemäß angewendet wird, wenn das Feld in der Windows Store-Spalte und die Zeile "Sehr niedrig" grün sind. 
3. Wählen Sie im Abschnitt **Schatten** die   Option Schatten deaktivieren **aus.** 

![Screenshot des Fensters "Projekteinstellungen" im Unity-Editor mit hervorgehobener Abschnitt "Qualitätseinstellungen"](images/wmr-config-img-10.png)<br>
*Unity-Qualitätseinstellungen*

## <a name="per-scene-settings"></a>Einstellungen pro Szene

### <a name="unity-camera-settings"></a>Unity-Kameraeinstellungen

Wenn **Virtual Reality Unterstützt aktiviert ist,** verarbeitet die [Unity-Kamerakomponente](camera-in-unity.md) die [Kopfnachverfolgung und stereoskopisches Rendering.](../platform-capabilities-and-apis/rendering.md) Das bedeutet, dass Sie das Hauptkameraobjekt nicht durch eine benutzerdefinierte Kamera ersetzen müssen.

Wenn Ihre App speziell auf HoloLens ausgerichtet ist, müssen Sie einige Einstellungen ändern, um die Anzeige transparent auf dem Gerät zu optimieren. Mit diesen Einstellungen können Ihre holografischen Inhalte der physischen Welt angezeigt werden:

1. Wählen Sie in der **Hierarchie** die **Hauptkamera aus.**
2. Legen Sie im **Inspektorbereich** die **Transformationsposition** auf **0, 0, 0 fest,** damit die Position des Kopfes des Benutzers am Unity-Ursprung beginnt.
3. Ändern Sie **Clear Flags (Flags** löschen) in **Solid Color (Volltonfarbe).**
4. Ändern Sie die **Hintergrundfarbe** in **RGBA 0,0,0,0**. Schwarz wird in HoloLens als transparent gerendert.
5. Ändern der **Clippingebenen: In** der Nähe der [holoLens empfohlenen](camera-in-unity.md#using-clipping-planes) 0,85 (Meter).

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