---
title: Mixed Reality-Erfassung für Entwickler
description: Erfahren Sie mehr über die bewährten Methoden zum Aktivieren, Verwenden und Rendern der Mixed Reality-Erfassung für Entwickler.
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: mrc, photo, video, capture, camera
ms.openlocfilehash: ec1a53d2f623a8047c2ee1973d8d6f20458ade88
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110245"
---
# <a name="mixed-reality-capture-for-developers"></a>Mixed Reality-Erfassung für Entwickler

> [!NOTE]
> Unter [Rendern von der PV-Kamera weiter](#render-from-the-pv-camera-opt-in) unten finden Sie Eine Anleitung zu einer neuen MRC-Funktion für HoloLens 2.

Sie können jederzeit ein MrC-Foto oder -Video [(Mixed Reality Capture)](/hololens/holographic-photos-and-videos) aufnehmen, aber es gibt einige Dinge, die Sie bei der Entwicklung Ihrer Anwendung beachten sollten. Dies umfasst bewährte Methoden für die qualität der MRC-Visualisierung und die Reaktion auf Systemänderungen, während MRCs erfasst werden.

Entwickler können mixed reality capture und insertion nahtlos in ihre Apps integrieren.

MRC auf HoloLens (erste Generation) unterstützt Videos und Fotos bis zu 720p, während MRC auf HoloLens 2 Videos bis zu 1080p und Fotos mit einer Auflösung von bis zu 4K unterstützt.

## <a name="the-importance-of-quality-mrc"></a>Die Wichtigkeit von Qualitäts-MRC

Unabhängig davon, ob es sich um Mixed Reality-Screenshots auf Ihrer Microsoft Store-Seite oder um andere Benutzer handelt, die Erfassungsinhalte in sozialen Netzwerken freigeben, sind Mixed Reality-Aufnahme-Medien häufig ein Benutzer, der ihre App zuerst verfügbar macht. Sie können MRC verwenden, um Ihre App zu demoren, Benutzer zu schulen, Benutzer zu ermutigen, ihre Interaktionen in der gemischten Welt zu teilen, und um Benutzerforschung und Problemlösung zu ermöglichen.

## <a name="how-mrc-impacts-your-app"></a>Auswirkungen von MRC auf Ihre App

### <a name="enabling-mrc-in-your-app"></a>Aktivieren von MRC in Ihrer App

Standardmäßig muss eine App keine Maßnahmen ergreifen, damit Benutzer Mixed Reality-Erfassungen aufnehmen können.

### <a name="enabling-improved-alignment-for-mrc-in-your-app"></a>Aktivieren der verbesserten Ausrichtung für MRC in Ihrer App

Standardmäßig kombiniert die Mixed Reality-Aufnahme die holografische Ausgabe des rechten Auges mit der Foto-/Videokamera (PV). Diese beiden Quellen werden mithilfe des Fokuspunkts kombiniert, der von der aktuell ausgeführten immersiven App festgelegt wird.

Dies bedeutet, dass Hologramme außerhalb der Fokusebene aufgrund des physischen Abstands zwischen der PV-Kamera und der rechten Anzeige nicht ausgerichtet werden.

#### <a name="set-the-focus-point"></a>Festlegen des Fokuspunkts

Immersive Apps (auf HoloLens) [](../unity/focus-point-in-unity.md) sollten den Fokuspunkt festlegen, an dem ihre Stabilitätsebene sein soll. Dadurch wird die beste Ausrichtung sowohl im Headset als auch in der Mixed Reality-Aufnahme sichergestellt.

Wenn kein Fokuspunkt festgelegt ist, beträgt die Stabilitätsebene standardmäßig 2 Meter.

#### <a name="render-from-the-pv-camera-opt-in"></a>Rendern von der PV-Kamera (optional)

HoloLens 2 bietet einer immersiven App die Möglichkeit, von der **PV-Kamera** zu rendern, während die Mixed Reality-Aufnahme ausgeführt wird. Um sicherzustellen, dass die App das zusätzliche Rendern ordnungsgemäß unterstützt, muss die App diese Funktionalität verwenden.

Das Rendern von der PV-Kamera bietet die folgenden Verbesserungen gegenüber der MRC-Standarderfahrung:
* Die Hologrammausrichtung an Ihrer physischen Umgebung und den Händen für nahe Interaktionen sollte in allen Entfernungen genau sein. Vermeiden Sie es, einen Offset bei anderen Entfernungen als dem Fokuspunkt zu verwenden, wie sie möglicherweise im MRC-Standard angezeigt werden.
* Das rechte Auge im Headset wird nicht kompromittiert, da es nicht zum Rendern der Hologramme für die MRC-Ausgabe verwendet wird.

Es gibt drei Schritte, um das Rendering von der PV-Kamera zu aktivieren:
1. Aktivieren der PhotoVideoCamera HolographicViewConfiguration
2. Verarbeiten des zusätzlichen HolographicCamera-Renderns
3. Überprüfen Sie, ob Shader und Code von dieser zusätzlichen HolographicCamera ordnungsgemäß gerendert werden.

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-directx"></a>Aktivieren der PhotoVideoCamera HolographicViewConfiguration in DirectX

Um das Rendering von der PV-Kamera zu aktivieren, aktiviert eine App einfach die [HolographicViewConfiguration](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration)der PhotoVideoCamera:
```csharp
var display = Windows.Graphics.Holographic.HolographicDisplay.GetDefault();
var view = display.TryGetViewConfiguration(Windows.Graphics.Holographic.HolographicViewConfigurationKind.PhotoVideoCamera);
if (view != null)
{
    view.IsEnabled = true;
}
```

##### <a name="handle-the-additional-holographiccamera-render-in-directx"></a>Verarbeiten des zusätzlichen HolographicCamera-Renderns in DirectX

Wenn die App sich für das Rendern von der PV-Kamera entscheidet und die Mixed Reality-Aufnahme gestartet wird:
1. Das CameraAdded-Ereignis von HolographicSpace wird angezeigt. Dieses Ereignis kann verzögert werden, wenn die App die Kamera zu diesem Zeitpunkt nicht verarbeiten kann.
2. Sobald das Ereignis ohne ausstehende Verzögerungen abgeschlossen wurde, wird die HolographicCamera in der nächsten AddedCameras-Liste von HolographicFrame angezeigt.

Wenn die Mixed Reality-Erfassung beendet wird (oder wenn die App die Ansichtskonfiguration deaktiviert, während die Mixed Reality-Erfassung ausgeführt wird): Die HolographicCamera wird in der nächsten RemovedCameras-Liste von HolographicFrame angezeigt, und das CameraRemoved-Ereignis von HolographicSpace wird angezeigt.

HolographicCamera wurde eine [ViewConfiguration-Eigenschaft](/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration) hinzugefügt, um die Konfiguration zu identifizieren, zu der eine Kamera gehört.

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-unity"></a>Aktivieren der PhotoVideoCamera HolographicViewConfiguration in Unity

> [!NOTE]
> Wenn Sie Unity 2018 verwenden, ist **Unity 2018.4.13f1** oder neuer erforderlich. Wenn Sie Unity 2019 verwenden, ist **Unity 2019.4** oder eine neuere Version erforderlich.

Um das Rendering von der PV-Kamera bei Verwendung des [Mixed Reality Toolkits](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)zu aktivieren, aktivieren Sie den Windows Mixed Reality-Kameraeinstellungsanbieter, und aktivieren Sie Rendern von **der PV-Kamera**. [](/windows/mixed-reality/mrtk-unity/features/camera-system/windows-mixed-reality-camera-settings)

Wenn Sie das Mixed Reality Toolkit nicht verwenden, können Sie [](#enable-the-photovideocamera-holographicviewconfiguration-in-directx) eine Komponente verwenden, um sich manuell wie oben für DirectX beschrieben zu entscheiden.

##### <a name="handle-the-additional-holographiccamera-render-in-unity"></a>Verarbeiten des zusätzlichen HolographicCamera-Renderns in Unity

Dies wird automatisch von Unity für Sie durchgeführt.

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-unreal"></a>Aktivieren der PhotoVideoCamera HolographicViewConfiguration in Unreal

> [!NOTE]
> Dafür ist **Unreal Engine 4.25** oder höher erforderlich.

So abonnieren Sie das Rendering von der FV-Kamera:

1. Rufen Sie **SetEnabledMixedRealityCamera** und **ResizeMixedRealityCamera** auf.
    * Verwenden Sie die Werte **Size X** (Größe X) und **Size Y** (Größe Y), um die Videoabmessungen festzulegen.

![Dritte Kamera](images/unreal-camera-3rd.PNG)

##### <a name="handle-the-additional-holographiccamera-render-in-unreal"></a>Verarbeiten des zusätzlichen HolographicCamera-Renderns in Unreal

Dies erfolgt automatisch durch Unreal.

##### <a name="verify-shaders-and-code-support-additional-cameras"></a>Überprüfen, ob Shader und Code zusätzliche Kameras unterstützen

Führen Sie eine Mixed Reality-Erfassung aus, und überprüfen Sie, ob ungewöhnliche Ausrichtungen, fehlende Inhalte oder Leistungsprobleme vorhanden sind. Aktualisieren Sie Shader und Code entsprechend.

Wenn bestimmte Szenen das Rendern auf eine zusätzliche Kamera nicht unterstützen können, können Sie die HolographicViewConfiguration von PhotoVideoCamera deaktivieren.

### <a name="disabling-mrc-in-your-app"></a>Deaktivieren von MRC in Ihrer App

#### <a name="2d-app"></a>2D-App

2D-Apps können festlegen, dass ihre visuellen Inhalte verdeckt werden, wenn die Mixed Reality-Erfassung ausgeführt wird:
* Vorhanden mit [](/windows/desktop/direct3ddxgi/dxgi-present) dem DXGI_PRESENT_RESTRICT_TO_OUTPUT Flag
* Erstellen der Swapkette der App mit dem [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag) Flag
* Mit dem Windows 10 May 2019 Update Festlegen von [IsScreenCaptureEnabled](/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled) von ApplicationView

#### <a name="immersive-app"></a>Immersive App

Immersive Apps können festlegen, dass ihre visuellen Inhalte von der Mixed Reality-Erfassung ausgeschlossen werden:
* Festlegen von [IsContentProtectionEnabled](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled) von HolographicCameraRenderingParameter, um die Mixed Reality-Erfassung für den zugeordneten Frame zu deaktivieren
* Festlegen von [IsHardwareContentProtectionEnabled](/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled) von HolographicCamera, um die Mixed Reality-Aufnahme für die zugeordnete holografische Kamera zu deaktivieren

#### <a name="password-keyboard"></a>Kennworttastatur

Mit der Windows 10 May 2019 Update wird visueller Inhalt automatisch von der Mixed Reality-Erfassung ausgeschlossen, wenn ein Kennwort oder eine Pintastatur sichtbar ist.

### <a name="knowing-when-mrc-is-active"></a>Wissen, wann MRC aktiv ist

Die [AppCapture-Klasse](/uwp/api/Windows.Media.Capture.AppCapture) kann von einer App verwendet werden, um zu wissen, wann die Mixed Reality-Erfassung des Systems ausgeführt wird (für Audio oder Video).

>[!NOTE]
>Die [GetForCurrentView-API](/uwp/api/windows.media.capture.appcapture.getforcurrentview) von AppCapture kann NULL zurückgeben, wenn die Mixed Reality-Erfassung auf dem Gerät nicht verfügbar ist. Es ist auch wichtig, die Registrierung des CapturingChanged-Ereignisses zu aufgehoben, wenn Ihre App angehalten wird. Andernfalls kann MRC in einen blockierten Zustand übergewechselt werden.

### <a name="best-practices-hololens-specific"></a>Bewährte Methoden (HoloLens-spezifisch)

MRC funktioniert voraussichtlich ohne zusätzlichen Entwicklungsaufwand, aber es gibt einige Dinge, die Sie beachten sollten, wenn Sie die beste Mixed Reality-Erfassungserfahrung bereitstellen.

**MRC verwendet den Alphakanal des Hologramms, um sich mit den [Kamerabilder](locatable-camera.md) zu mischen.**

Der wichtigste Schritt besteht im Sicherstellen, dass Ihre App in transparentes Schwarz und nicht in undurchsichtiges Schwarz durchlässig wird. In Unity erfolgt dies standardmäßig mit dem MixedRealityToolkit. Wenn Sie in Nicht-Unity entwickeln, müssen Sie möglicherweise eine Zeilenänderung machen.

Hier sind einige der Artefakte, die in MRC möglicherweise angezeigt werden, wenn Ihre App nicht in transparentes Schwarz clearingt:

**Beispielfehler:** Schwarze Ränder um den Inhalt (Fehler beim Löschen in transparentes Schwarz)

<table>
<tr>
<td>
<img src="images/chessboardblackedges-300px.jpg" alt="Failure to clear to transparent black: black edge artifacts around holograms"/>
</td>
<td>
<img src="images/fieldblackedges-300px.jpg" alt="Failing to clear to transparent black: black edge artifacts around holograms"/>
</td>
</tr>
</table>

**Beispielfehler:** Die gesamte Hintergrundszene des Hologramms wird schwarz angezeigt. Das Festlegen eines Alpha-Hintergrundwerts von einem führt zu einem schwarzen Hintergrund.

![Das Festlegen eines Alpha-Hintergrundwerts von 1 führt zu einem schwarzen Hintergrund.](images/clearopaqueblack-300px.png)

**Erwartetes Ergebnis:** Hologramme werden ordnungsgemäß kombiniert mit der realen Welt angezeigt (erwartetes Ergebnis beim Löschen in transparentes Schwarz)

![Erwartetes Ergebnis beim Löschen in transparentes Schwarz](images/cleartransparentblack-300px.png)

**Lösung**:
* Ändern Sie alle Inhalte, die als nicht transparent schwarz angezeigt werden, so, dass sie den Alphawert 0 haben.
* Stellen Sie sicher, dass die App transparent schwarz angezeigt wird.
* Unity wird standardmäßig automatisch mit dem MixedRealityToolkit gelöscht. Wenn es sich jedoch um eine Nicht-Unity-App handelt, sollten Sie die mit ID3D11DeiceContext::ClearRenderTargetView() verwendete Farbe ändern. Sie möchten sicherstellen, dass Sie klar in transparentes Schwarz (0,0,0,0) statt in deckend schwarz (0,0,0,1) löschen.

Sie können jetzt die Alphawerte Ihrer Ressourcen optimieren, wenn Sie möchten, dies ist jedoch in der Regel nicht notwendig. In den meisten Jahren sehen MRCs bereits gut aus. MRC geht von vor multipliziertem Alpha aus. Die Alphawerte wirken sich nur auf die MRC-Erfassung aus.

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a>Was sie erwartet, wenn MRC auf HoloLens aktiviert ist

Folgendes gilt sowohl für HoloLens (erste Generation) als auch für HoloLens 2, sofern nicht anders angegeben:

* Das System drosselt die Anwendung auf das 30-Hz-Rendering. Dadurch entsteht ein gewisses Maß an Zeit für die Ausführung von MRC, sodass die App keine konstante Budgetreserve beibehalten muss und auch der MRC-Videoaufzeichnungsframerate von 30 FPS entspricht.
* Hologramminhalte im rechten Auge des Geräts können beim Aufzeichnen/Streamen von MRC "sparkle" erscheinen: Text kann schwieriger zu lesen sein, und Hologrammränder erscheinen möglicherweise verzweigt (die Dritte Kamera wird auf **HoloLens 2** vermeidet diese Kompromittierung).
* MRC-Fotos und -Videos berücksichtigen den [Fokuspunkt](../unity/focus-point-in-unity.md) der Anwendung, wenn die Anwendung sie aktiviert hat, wodurch sichergestellt wird, dass Hologramme korrekt positioniert sind. Bei Videos wird der Fokuspunkt geglättet, sodass Hologramme langsam abdriften können, wenn sich die Fokuspunkttiefe erheblich ändert. Hologramme, die sich in unterschiedlichen Tiefen vom Fokuspunkt befinden, können von der realen Welt versetzt erscheinen (siehe Beispiel unten, in dem der Fokuspunkt auf 2 Meter festgelegt ist, das Hologramm jedoch bei 1 Meter positioniert ist).

![Hologramme mit 2 Metern erscheinen perfekt für die Welt registriert. Hologramme in nah oder fernen Abständen können leicht versetzt werden.](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a>Integrieren von MRC-Funktionen aus Ihrer App

Ihre Mixed Reality-App kann MRC-Foto- oder -Videoaufnahmen innerhalb der App starten, und der erfasste Inhalt wird Ihrer App zur Verfügung gestellt, ohne im "Kameraroll" des Geräts gespeichert zu werden. Sie können einen benutzerdefinierten MRC-Aufzeichnungsgerät erstellen oder die integrierte Kameraerfassungsbenutzeroberfläche nutzen. 

### <a name="mrc-with-built-in-camera-ui"></a>MRC mit integrierter Kamerabenutzeroberfläche

Entwickler können die *[Kameraaufnahme-UI-API](/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* verwenden, um ein vom Benutzer erfasstes Mixed Reality-Foto oder -Video mit nur wenigen Codezeilen zu erhalten.

Diese API startet die integrierte MRC-Kamerabenutzeroberfläche, auf der Benutzer ein Foto oder Video aufnehmen und die resultierende Aufnahme an Ihre App zurücksenden können. Sie können einen benutzerdefinierten Mixed Reality-Aufnahme-Aufzeichnungsgerät erstellen, wenn Sie Eine eigene Kamerabenutzeroberfläche oder zugriff auf eine niedrigere Ebene zum Erfassen von Datenströmen hinzufügen müssen.

### <a name="creating-a-custom-mrc-recorder"></a>Erstellen eines benutzerdefinierten MRC-Aufzeichnungsgeräts

Während der Benutzer immer ein Foto oder Video mit dem MRC-Erfassungsdienst des Systems auslösen kann, kann eine Anwendung eine benutzerdefinierte Kamera-App erstellen, die Hologramme wie MRC in den Kameradatenstrom einschließt. Dadurch kann die Anwendung Erfassungen aus Benutzereingaben starten, eine benutzerdefinierte Aufzeichnungsoberfläche erstellen oder MRC-Einstellungen anpassen, um einige Beispiele zu nennen.

**HoloStudio fügt eine benutzerdefinierte MRC-Kamera mit MRC-Effekten hinzu**

![HoloStudio fügt eine benutzerdefinierte MRC-Kamera mit MRC-Effekten hinzu](images/cameraiconholostudio-300px.jpg)

Unity-Anwendungen sollten [Locatable_camera_in_Unity](../unity/locatable-camera-in-unity.md) für die -Eigenschaft sehen, um Hologramme zu aktivieren.

Andere Anwendungen können dies erreichen, indem sie die [Windows Media Capture-APIs](/uwp/api/Windows.Media.Capture.MediaCapture) verwenden, um die Kamera zu steuern und einen MRC-Effekt für Video und Audio hinzuzufügen, um virtuelle Hologramme und Anwendungsaudiodaten in Stills und Videos einzubeziehen.

Anwendungen haben zwei Optionen, um den Effekt hinzuzufügen:
* Die ältere API: [Windows.Media.Capture.MediaCapture.AddEffectAsync()](/uwp/api/windows.media.capture.mediacapture.addeffectasync)
* Die neue von Microsoft empfohlene API (gibt ein Objekt zurück, sodass dynamische Eigenschaften bearbeitet werden können): [Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync)  /  [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync(),](/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) für die die App eine eigene Implementierung von [IVideoEffectDefinition](/uwp/api/Windows.Media.Effects.IVideoEffectDefinition) und [IAudioEffectDefinition](/uwp/api/windows.media.effects.iaudioeffectdefinition)erstellen muss. Beispiele finden Sie in der [MRC-Beispiel-App.](https://github.com/microsoft/Windows-universal-samples/tree/master/Samples/HolographicMixedRealityCapture)

>[!NOTE]
> Der Windows.Media.MixedRealityCapture-Namespace wird von Visual Studio nicht erkannt, aber die Zeichenfolgen sind weiterhin gültig.

MRC Video Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)

|  Eigenschaftsname  |  Typ  |  Standardwert  |  BESCHREIBUNG |
|----------|----------|----------|----------|
|  StreamType  |  UINT32 ([MediaStreamType](/uwp/api/Windows.Media.Capture.MediaStreamType))  |  1 (VideoRecord)  |  Beschreiben Sie, für welchen Erfassungsstream dieser Effekt verwendet wird. Audio ist nicht verfügbar. |
|  HologramCompositionEnabled  |  boolean  |  TRUE  |  Flag zum Aktivieren oder Deaktivieren von Hologrammen in der Videoaufnahme. |
|  RecordingIndicatorEnabled  |  boolean  |  TRUE  |  Flag zum Aktivieren oder Deaktivieren des Aufzeichnungsindikators auf dem Bildschirm während der Hologrammerfassung. |
|  VideoStabilizationEnabled  |  boolean  |  FALSE  |  Flag zum Aktivieren oder Deaktivieren der videoaktivierung, die von der HoloLens-Tracker unterstützt wird. |
|  VideoStabilizationBufferLength  |  UINT32  |  0  |  Legen Sie fest, wie viele Verlaufsframes für die Videointeressierung verwendet werden. 0 ist eine Latenz von 0 und im Hinblick auf Leistung und Leistung nahezu "kostenlos". 15 wird für höchste Qualität empfohlen (auf Kosten von 15 Frames mit Latenz und Arbeitsspeicher). |
|  GlobalOpacityCoefficient  |  float  |  0.9 (HoloLens) 1.0 (immersives Headset)  |  Legen Sie den globalen Deckkraftkoeffizienten des Hologramms im Bereich von 0,0 (vollständig transparent) bis 1,0 (vollständig deckend) fest. |
|  BlankOnProtectedContent  |  boolean  |  FALSE  |  Flag zum Aktivieren oder Deaktivieren der Rückgabe eines leeren Frames, wenn eine 2D-UWP-App geschützten Inhalt anzeigt. Wenn dieses Flag FALSE ist und eine 2D-UWP-App geschützte Inhalte anzeigt, wird die 2d-UWP-App durch eine geschützte Inhaltstextur sowohl im Headset als auch in der Mixed Reality-Erfassung ersetzt. |
|  ShowHiddenMesh  |  boolean  |  FALSE  |  Flag zum Aktivieren oder Deaktivieren der Anzeige des verborgenen Bereichsgitters und des benachbarten Inhalts der holografischen Kamera. |
| OutputSize | Size | 0, 0 | Legen Sie die gewünschte Ausgabegröße nach dem Zuschneiden für die Videostabilisierung fest. Eine Standard zugeschnittene Größe wird ausgewählt, wenn 0 oder eine ungültige Ausgabegröße angegeben wird. |
| PreferredHologramPerspective | UINT32 | **Rendern über die Kameraeinstellung** im Windows-Geräteportal | Enumeration, die verwendet wird, um anzugeben, welche Holografische Kameraansichtskonfiguration erfasst werden soll: 0 (Anzeige) bedeutet, dass die App nicht aufgefordert wird, von der Foto-/Videokamera zu rendern. 1 (PhotoVideoCamera) fordert die App auf, von der Foto-/Videokamera zu rendern (sofern die App dies unterstützt). Nur auf HoloLens 2 unterstützt |

>[!NOTE]
> Sie können den Standardwert von **PreferredHologramPerspective** im Windows-Geräteportal ändern, indem Sie zur [Seite Mixed Reality-Aufnahme](using-the-windows-device-portal.md#mixed-reality-capture) wechseln und Render **from Camera** deaktivieren. Die Einstellung ist standardmäßig **auf 1 (PhotoVideoCamera)** festgelegt, kann jedoch deaktiviert werden, um sie auf **0 (Anzeige)** festzulegen.
>
> Der Standardwert von **PreferredHologramPerspective** war **0 (Anzeige)** vor dem Update vom Juni 2020 (Windows Holographic, Version 2004 Build 19041.1106 und Windows Holographic, Version 1903 Build 18362.1064).

MRC Audio Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)

| Eigenschaftsname | Typ | Standardwert | BESCHREIBUNG |
|----------|----------|----------|----------|
| MixerMode | UINT32 | 2 (Mikrofon- und Systemaudio) | Enumeration, die angibt, welche Audioquellen verwendet werden sollen: 0 (nur Mikrofonaudio), 1 (nur Systemaudio), 2 (Mikrofon- und Systemaudio) |
| LoopbackGain | float | **Einstellung "App-Audiogewinn"** im Windows-Geräteportal | Sie erhalten eine Anwendung auf die Systemaudiolautstärke. Liegt zwischen 0,0 und 5,0. Nur auf HoloLens 2 unterstützt |
| MicrophoneGain | float | **Einstellung "Mikrofonaudiogewinn"** im Windows-Geräteportal | Sie erhalten, um sie auf die Mikrofonlautstärke anzuwenden. Liegt zwischen 0,0 und 5,0. Nur auf HoloLens 2 unterstützt |

>[!NOTE]
> Sie können den Standardwert von **LoopbackGain** oder **MicrophoneGain** im Windows-Geräteportal ändern, indem Sie zur [seite Mixed Reality-Aufnahme](using-the-windows-device-portal.md#mixed-reality-capture) wechseln und den Schieberegler neben den jeweiligen Einstellungen anpassen. Beide Einstellungen sind standardmäßig auf **1,0** festgelegt, können jedoch auf einen beliebigen Wert zwischen **0,0** und **5,0** festgelegt werden.
>
> Die Verwendung von Windows-Geräteportal zum Konfigurieren der Standardgewinnwerte wurde mit dem Update vom Juni 2020 hinzugefügt (Windows Holographic, Version 2004 Build 19041.1106 und Windows Holographic, Version 1903 Build 18362.1064).

### <a name="simultaneous-mrc-limitations"></a>Gleichzeitige MRC-Einschränkungen

Sie müssen bestimmte Einschränkungen beachten, wenn mehrere Apps gleichzeitig auf MRC zugreifen.

#### <a name="photovideo-camera-access"></a>Foto-/Videokamerazugriff

Auf HoloLens 1 kann MRC kein Foto oder Video aufnehmen, während ein Prozess das Video oder das Aufnehmen eines Fotos aufzeichnet. Das Gegenteil ist auch richtig: Wenn MRC ausgeführt wird, erhält die Anwendung keinen Zugriff auf die Kamera. 

Mit HoloLens 2 können Sie den Zugriff auf die Kamera freigeben. Wenn Sie keine direkte Steuerung der Auflösung oder Framerate benötigen, können Sie MediaCapture mithilfe der [SharedMode-Eigenschaft](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041) mit SharedReadOnly initialisieren.  

##### <a name="built-in-mrc-photovideo-camera-access"></a>Integrierter MRC-Foto-/Videokamerazugriff

MRC-Funktionalität, die in Windows 10 integriert ist (über Cortana, Startmenü, Hardwareverknüpfungen, Miracast, Windows-Geräteportal):

* Wird standardmäßig mit ExclusiveControl ausgeführt.

Dem MRC-Subsystem wurde jedoch Unterstützung für den Betrieb in einem freigegebenen Modus hinzugefügt: 

* Wenn eine App ExclusiveControl-Zugriff auf die Foto-/Videokamera anfordert, beendet das integrierte MRC automatisch die Verwendung der Foto-/Videokamera, sodass die Anforderung der App erfolgreich ist. 
* Wenn das integrierte MRC gestartet wird, während eine App über ExclusiveControl verfügt, wird das integrierte MRC im SharedReadOnly-Modus ausgeführt. 

Diese Funktionalität im gemeinsam genutzten Modus weist bestimmte Einschränkungen auf:

* Foto über Cortana, Hardwareverknüpfungen oder Startmenü: Erfordert die Windows 10 April 2018 Update (oder höher)
* Video über Cortana, Hardwareverknüpfungen oder Startmenü: Erfordert die Windows 10 April 2018 Update (oder höher)
* Streaming-MRC über Miracast: Erfordert die Windows 10 October 2018 Update (oder höher)
* Streaming-MRC über Windows-Geräteportal oder über die HoloLens-Begleit-App: Erfordert HoloLens 2

>[!NOTE]
> Die Auflösung und Bildfrequenz der integrierten MRC-Kamerabenutzeroberfläche kann von den normalen Werten reduziert werden, wenn eine andere App die Foto-/Videokamera verwendet.

#### <a name="mrc-access-for-developers"></a>MRC-Zugriff für Entwickler

Es wird empfohlen, immer die exklusive Steuerung für die Kamera anzufordern, wenn Sie MRC verwenden. Dadurch wird sichergestellt, dass Ihre Anwendung die vollständige Kontrolle über die Einstellungen für die Kamera hat, solange Sie die oben aufgeführten Einschränkungen kennen. 

* Erstellen eines Medienerfassungsobjekts mithilfe der [Initialisierungseinstellungen](/uwp/api/windows.media.capture.mediacaptureinitializationsettings?view=winrt-19041)
* Legen Sie die [SharingMode-Eigenschaft](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041#Windows_Media_Capture_MediaCaptureInitializationSettings_SharingMode) auf **exclusive** fest.

> [!CAUTION]
> Lesen Sie unbedingt die [SharingMode-Hinweise](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041#remarks) sorgfältig durch, bevor Sie fortfahren.

* Richten Sie Ihre Kamera so ein, wie Sie sie wünschen.
* Starten der App, Erfassen von Videoframes mit der Start-API und Aktivieren von MRC

> [!CAUTION]
> Wenn Sie MRC starten, bevor Sie Ihre App starten, können wir nicht garantieren, dass das Feature wie erwartet funktioniert.

Ein vollständiges Beispiel des obigen Prozesses finden Sie im [Holographic Face Tracking-Beispiel.](/samples/microsoft/windows-universal-samples/holographicfacetracking)

> [!NOTE]
> Vor dem Windows 10 April 2018 Update hat sich der benutzerdefinierte MRC-Aufzeichnungs-Bezeichner einer App mit dem System-MRC (Erfassen von Fotos, Aufzeichnen von Videos oder Streamen aus dem Windows-Geräteportal) gegenseitig ausschließen.

## <a name="see-also"></a>Siehe auch

* [Mixed-Reality-Aufnahme](/hololens/holographic-photos-and-videos)
* [Spectator View](spectator-view.md)
* [Übersicht über die Unity-Entwicklung](../unity/unity-development-overview.md)
* [Ureal-Entwicklung – Übersicht](../unreal/unreal-development-overview.md)
