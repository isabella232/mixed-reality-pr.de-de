---
title: Konfigurieren des Projekts ohne mrtk
description: Erfahren Sie, wie Sie ein neues Unity-Projekt für Windows Mixed Reality ohne das Mixed Reality Toolkit konfigurieren.
author: hferrone
ms.author: alexturn
ms.date: 07/29/2020
ms.topic: article
keywords: Unity, gemischte Realität, Entwicklung, Einstieg, neues Projekt, Windows Mixed Reality, UWP, XR, Leistung
ms.openlocfilehash: 47ca4041e997d623d08fa1732f7039c655810bfc
ms.sourcegitcommit: b0fb5497bf9f280ba5610c30e4b9e5aa1cda52c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/23/2021
ms.locfileid: "104837416"
---
# <a name="configuring-your-project-without-mrtk"></a>Konfigurieren von Projekten ohne MRTK

Windows Mixed Reality (WMR) ist eine Microsoft-Plattform, die als Teil des Betriebssystems Windows 10 eingeführt wird. Mit der WMR-Plattform können Sie Anwendungen erstellen, mit denen digitale Inhalte auf Holographic-und VR-Geräten angezeigt werden.

Obwohl Microsoft und die Community Open Source-Tools wie das [Mixed Reality Toolkit (mrtk)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) erstellt haben, das die WMR-Umgebung automatisch einrichten wird, möchten viele Entwickler ihre Erfahrungen von Grund auf neu erstellen.  In der folgenden Dokumentation wird veranschaulicht, wie Sie ein Projekt für die Entwicklung mit gemischter Realität ordnungsgemäß einrichten, unabhängig davon, ob Sie mrtk verwenden oder nicht.  Die Einstellungen, die Sie ändern müssen, werden in zwei Kategorien unterteilt: Einstellungen pro Projekt und Einstellungen pro Szene.

> [!NOTE]
> Sie können mrtk später jederzeit importieren, sodass es für die manuelle Route keinen Nachteil gibt.

Wenn Sie die manuelle Einrichtung von WMR auswählen, werden die Einstellungen, die Sie ändern müssen, in zwei Kategorien unterteilt: pro Projekt und pro Szene.

## <a name="per-project-settings"></a>Einstellungen pro Projekt

Wenn Sie auf Desktop VR abzielen, empfiehlt es sich, die eigenständige PC-Plattform zu verwenden, die für ein neues Unity-Projekt standardmäßig ausgewählt ist:

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor mit PC, Mac & eigenständige Plattform hervorgehoben](images/wmr-config-img-3.png)

Wenn Sie hololens 2 als Ziel verwenden, müssen Sie zum universelle Windows-Plattform wechseln:

1.  **Datei > Buildeinstellungen auswählen...**
2.  Wählen Sie in der Platt Form Liste **universelle Windows-Plattform** aus, und wählen Sie **Plattform wechseln**
3.  **Architektur** auf **Arm 64** festlegen
4.  **Zielgerät** auf **hololens** festlegen
5.  **Buildtyp** auf **D3D** festlegen
6.  **UWP SDK** auf **Letztes installiert** festlegen
7.  **Buildkonfiguration** auf **Release** festlegen, da beim Debuggen bekannte Leistungsprobleme auftreten

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor öffnen mit hervorgehobener universelle Windows-Plattform](images/wmr-config-img-4.png)

Nachdem Sie Ihre Plattform festgelegt haben, müssen Sie Unity mitteilen, dass Sie beim Exportieren eine [immersive Ansicht](../../design/app-views.md) anstelle einer 2D-Ansicht erstellen soll.

### <a name="for-xrsdk"></a>Für xrsdk 

1. Navigieren Sie im Unity-Editor zu **Edit > Project Settings** , und wählen Sie die **Verwaltung von XR Plugin** aus.

2. Select 

![Screenshot des Fensters "Projekteinstellungen" im Unity-Editor geöffnet, mit hervorgehobener Verwaltung von XR](images/wmr-config-img-5.png)

3. Wählen Sie " **XR beim Start** und **Windows Mixed Reality** initialisieren" aus.

![Screenshot des Fensters "Projekteinstellungen" im Unity-Editor geöffnet, mit hervorgehobener Verwaltung von XR](images/wmr-config-img-7.png)

4. Erweitern Sie den Abschnitt **XR-Plug-in-Verwaltung** , und wählen Sie die Registerkarte **universelle Windows-Plattform**
5. Wenn Sie Unity 2020 oder höher verwenden, sehen Sie die Optionen zum Überprüfen von **openxr** oder **Windows Mixed Reality**. 
    * Sie können beide Laufzeitoptionen auswählen.  Wenn Sie speziell für die hololens 2 oder den HP-Reverb-G2 entwickeln und das **openxr** testen möchten, wählen Sie das Feld openxr aus, und lesen Sie unser Handbuch zum [Verwenden des gemischten Reality openxr-Plug-Ins für Unity](openxr-getting-started.md) , um sich vor der Rückkehr zu diesem Tutorial ordnungsgemäß für diese Geräte einzurichten.

> [!NOTE]
> Ab Unity 2020 LTS geht Microsoft mit der Entwicklung mit openxr um.  Wenn wir zu diesem Pfad migrieren, wird das Windows-XR-Plug-in in Unity 2021,1 als veraltet markiert und 2021,2 entfernt, sodass openxr der einzige unterstützte Pfad ist. Weitere Informationen finden Sie unter [Verwenden des gemischten Reality openxr-Plug](openxr-getting-started.md)-ins.

6. Wenn Sie das **Windows Mixed Reality** -Plug-in auswählen, aktivieren Sie alle Kontrollkästchen, und legen Sie den tiefen Übermittlungs **Modus** auf **Tiefe 16 Bit** fest.

![Screenshot des Fensters "Projekteinstellungen" im Unity-Editor geöffnet mit hervorgehobenem Windows Mixed Reality-Abschnitt](images/wmr-config-img-8.png)

### <a name="for-legacy-xr"></a>Für Legacy-XR 

> [!CAUTION]
> Legacy XR ist in Unity 2019 veraltet und wurde in Unity 2020 entfernt.

1. **Player Einstellungen** öffnen... aus den **Buildeinstellungen... Fenster** und erweitern Sie die Gruppe " **XR-Einstellungen** ".
2. Wählen Sie im Abschnitt " **XR-Einstellungen** " die Option **virtuelle Realität unterstützt** aus, um die Liste Virtual Reality-Geräte
3. Festlegen des **tiefen Formats** auf eine **16-Bit-Tiefe** und Aktivieren der **tiefen Puffer Freigabe**
4. Festlegen des **Stereo Renderingmodus** auf eine **Einzel Pass Instanz**
5. Wählen Sie **WSA Holographic Remoting unterstützt** aus, wenn Sie Holographic Remoting verwenden möchten. 

![Screenshot des Fensters "Projekteinstellungen" im Unity-Editor mit hervorgehobenem Abschnitt "Player Einstellungen"](images/wmr-config-img-9.png)

### <a name="updating-the-manifest"></a>Aktualisieren des Manifests

Ihre APP kann jetzt Holographic-Rendering und räumliche Eingaben verarbeiten. Ihre APP muss jedoch die entsprechenden Funktionen in ihrem Manifest deklarieren, um von bestimmten Funktionen profitieren zu können. Sie finden Ihre Projektfunktionen, indem Sie zu den Einstellungen **für Player Einstellungen > Einstellungen für universelle Windows-Plattform > Veröffentlichungs Einstellungen > Funktionen** wechseln. 

Es wird empfohlen, dass Sie die Manifest-Deklarationen in Unity vornehmen, um Sie in allen zukünftigen Projekten einzuschließen, die Sie exportieren. Die anwendbaren Funktionen zum Aktivieren häufig verwendeter Unity-APIs für gemischte Realität sind:

|  Funktion  |  APIs, die Funktionen erfordern | 
|----------|----------|
|  SpatialPerception  |  "Surfaceobserver" (Zugriff auf [räumliche](../../design/spatial-mapping.md) zuordnungsnetze in hololens) ist &mdash; *für die allgemeine räumliche Nachverfolgung des Headsets nicht erforderlich* . | 
|  Webcam  |  Photocapture und Videocapture | 
|  Pictureslibrary/videoslibrary  |  Photocapture oder Videocapture bzw. (beim Speichern des erfassten Inhalts) | 
|  Mikrofon  |  Videocapture (bei der Erfassung von Audiodaten), "diktationerkenzer", "grammarerkenzer" und "keywordrecognizer" | 
|  InternetClient  |  "Diktationerkenzer" (und für die Verwendung des Unity-Profilers) | 

### <a name="quality-settings"></a>Qualitätseinstellungen

Hololens verfügt über eine GPU mobiler Klasse. Wenn Ihre APP auf hololens ausgerichtet ist, sollten Sie mit den Qualitätseinstellungen Ihrer APP beginnen, die für die schnellste Leistung optimiert ist, um sicherzustellen, dass Sie die vollständige Framerate beibehält.  Nachdem Sie Ihre Entwicklung weiterentwickelt haben, können Sie die Qualitätseinstellungen in Erwägung gezogen, um das richtige Gleichgewicht der Qualität und Leistung zu finden: 

1. Wählen Sie **> Projekteinstellungen bearbeiten > Qualität** aus. 
2. Wählen Sie im  **Windows Store**-Logo die **Dropdown** Liste aus,   und wählen Sie  **sehr niedrig** aus. Sie werden feststellen, dass die Einstellung ordnungsgemäß angewendet wird, wenn das Feld in der Windows Store-Spalte und die sehr niedrige Zeile grün ist. 
3. Wählen Sie im Abschnitt **Shadows** die Option    **Shadows deaktivieren** aus. 

![Screenshot des Fensters "Projekteinstellungen" im Unity-Editor mit hervorgehobenem Abschnitt "Qualitätseinstellungen"](images/wmr-config-img-10.png)<br>
*Unity-Qualitätseinstellungen*

## <a name="per-scene-settings"></a>Pro-Szene-Einstellungen

### <a name="unity-camera-settings"></a>Unity-Kameraeinstellungen

Wenn **Virtual Reality** aktiviert ist, behandelt die [Unity-Kamera](camera-in-unity.md) Komponente die [Kopf-und stereorenderingfunktionen](../platform-capabilities-and-apis/rendering.md). Dies bedeutet, dass Sie das Hauptkamera Objekt nicht durch eine benutzerdefinierte Kamera ersetzen müssen.

Wenn Ihre APP speziell auf hololens ausgerichtet ist, müssen Sie einige Einstellungen ändern, um die transparente Anzeige des Geräts zu optimieren. Mit diesen Einstellungen können Sie Ihre Holographic-Inhalte in der physischen Welt anzeigen:

1. Wählen Sie in der **Hierarchie** die **Hauptkamera** aus.
2. Legen Sie im **Inspektor** -Panel die Transformations **Position** auf **0, 0, 0** fest, sodass der Speicherort des Benutzer Kopfes am Ursprung der Unity-Welt beginnt.
3. Ändern Sie die **Clear-Flags** in eine voll **Tonfarbe**.
4. Ändern Sie die **Hintergrund** Farbe in **RGBA 0, 0, 0**, 0. Schwarz wird in hololens als transparent gerendert.
5. Ändern Sie die **Clippingebenen in der Nähe** der [empfohlenen hololens](camera-in-unity.md#clip-planes) 0,85 (Meter).

![Screenshot der Registerkarte "Inspektor" im Unity-Editor](images/wmr-config-img-11.png)<br>
*Unity-Kameraeinstellungen*

> [!IMPORTANT]
> Wenn Sie eine neue Kamera löschen und erstellen, stellen Sie sicher, dass die neue Kamera als " **maincamera**" gekennzeichnet ist.

## <a name="next-steps"></a>Nächste Schritte

Nachdem Ihr Projekt nun bereit ist, können Sie mit der Entwicklung ihrer gemischten Realität beginnen:

* Hinzufügen von [Kern Bausteinen](unity-development-overview.md#2-core-building-blocks)
* Sehen Sie sich die verfügbaren [Plattformfunktionen und APIs](unity-development-overview.md#3-advanced-features) an
* Erfahren Sie, wie [Sie Ihre APP](../platform-capabilities-and-apis/using-visual-studio.md#) bereitstellen.
* Verwenden des [gemischten Reality-Simulators](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="see-also"></a>Siehe auch
* [Installieren der Tools](../install-the-tools.md)