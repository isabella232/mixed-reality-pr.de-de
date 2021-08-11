---
title: Mixed Reality-Erfassung für Entwickler
description: Erfahren Sie mehr über die bewährten Methoden zum Aktivieren, Verwenden und Rendern von Mixed Reality-Erfassung für Entwickler.
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: mrc, photo, video, capture, camera
ms.openlocfilehash: af585cd212ba8f2ddc3ea812c1fff2a5da8603bff0e77d8fc2ad794486821685
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192101"
---
# <a name="mixed-reality-capture-for-developers"></a>Mixed Reality-Erfassung für Entwickler

> [!NOTE]
> Eine Anleitung zu einer neuen MRC-Funktion für HoloLens 2 finden Sie weiter unten unter [Rendern von der PV-Kamera.](#render-from-the-pv-camera-opt-in)

Sie können jederzeit ein MRC-Foto oder -Video [(Mixed Reality Capture)](/hololens/holographic-photos-and-videos) aufnehmen, aber es gibt einige Dinge, die Sie bei der Entwicklung Ihrer Anwendung beachten sollten. Dies umfasst bewährte Methoden für die VISUELLE MRC-Qualität und reaktionsfähige Reaktion auf Systemänderungen, während MRCs erfasst werden.

Entwickler können Mixed Reality-Erfassung und -Einfügung auch nahtlos in ihre Apps integrieren.

MRC auf HoloLens (erste Generation) unterstützt Videos und Fotos mit einer Auflösung von bis zu 720p, mrc on HoloLens 2 unterstützt Videos mit einer Auflösung von bis zu 1080p und Fotos mit einer Auflösung von bis zu 4K.

## <a name="the-importance-of-quality-mrc"></a>Die Wichtigkeit von Qualitäts-MRC

Unabhängig davon, ob es sich um Mixed Reality-Screenshots auf Ihrer Microsoft Store-Seite oder um andere Benutzer handelt, die Inhalte in sozialen Netzwerken freigeben, ist Mixed Reality-Aufnahme Medien häufig ein Benutzer, der ihre App zum ersten Mal zugänglich macht. Sie können MRC verwenden, um Ihre App zu demonstimieren, Benutzer zu schulen, Benutzer dazu zu ermutigen, ihre Interaktionen in der gemischten Welt zu teilen, und um benutzerorientierte Untersuchungen und Problemlösungen zu ermöglichen.

## <a name="how-mrc-impacts-your-app"></a>Auswirkungen von MRC auf Ihre App

### <a name="enabling-mrc-in-your-app"></a>Aktivieren von MRC in Ihrer App

Standardmäßig muss eine App nichts tun, damit Benutzer Mixed Reality-Erfassungen aufnehmen können.

### <a name="enabling-improved-alignment-for-mrc-in-your-app"></a>Aktivieren einer verbesserten Ausrichtung für MRC in Ihrer App

Standardmäßig kombiniert Mixed Reality Capture die holografische Ausgabe des rechten Auges mit der Foto-/Videokamera (PV). Diese beiden Quellen werden mithilfe des Fokuspunkts kombiniert, der von der aktuell ausgeführten immersiven App festgelegt wird.

Dies bedeutet, dass Hologramme außerhalb der Fokusebene aufgrund des physischen Abstands zwischen der PV-Kamera und der rechten Anzeige nicht ausgerichtet werden.

#### <a name="set-the-focus-point"></a>Festlegen des Fokuspunkts

Immersive Apps (auf HoloLens) sollten den [Fokuspunkt](../unity/focus-point-in-unity.md) festlegen, an dem sich ihre Stabilisierungsebene befinden soll. Dadurch wird die optimale Ausrichtung sowohl im Headset als auch in der Mixed Reality-Erfassung sichergestellt.

Wenn kein Fokuspunkt festgelegt ist, wird die Stabilisierungsebene standardmäßig auf 2 Meter festgelegt.

#### <a name="render-from-the-pv-camera-opt-in"></a>Rendern von der PV-Kamera (Opt-In)

HoloLens 2 bietet einer immersiven App die Möglichkeit, von **der PV-Kamera** zu rendern, während die Mixed Reality-Erfassung ausgeführt wird. Um sicherzustellen, dass die App das zusätzliche Rendern ordnungsgemäß unterstützt, muss die App diese Funktion aktivieren.

Rendern über die PV-Kamera bietet gegenüber der MRC-Standarderfahrung die folgenden Verbesserungen:
* Die Ausrichtung des Hologramms an Ihre physische Umgebung und die Hände für Nahinteraktionen sollten in allen Entfernungen genau sein. Vermeiden Sie einen Offset in anderen Entfernungen als dem Fokuspunkt, wie sie möglicherweise im Standard-MRC angezeigt werden.
* Das rechte Auge im Headset wird nicht beeinträchtigt, da es nicht zum Rendern der Hologramme für die MRC-Ausgabe verwendet wird.

Es gibt drei Schritte zum Aktivieren des Renderings von der PV-Kamera:
1. Aktivieren der PhotoVideoCamera HolographicViewConfiguration
2. Behandeln des zusätzlichen HolographicCamera-Renders
3. Überprüfen Sie, ob Ihre Shader und Der Code ordnungsgemäß über diese zusätzliche HolographicCamera gerendert werden.

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-directx"></a>Aktivieren der PhotoVideoCamera HolographicViewConfiguration in DirectX

Um das Rendering von der PV-Kamera zu ermöglichen, aktiviert eine App einfach die [HolographicViewConfiguration](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration)von PhotoVideoCamera:
```csharp
var display = Windows.Graphics.Holographic.HolographicDisplay.GetDefault();
var view = display.TryGetViewConfiguration(Windows.Graphics.Holographic.HolographicViewConfigurationKind.PhotoVideoCamera);
if (view != null)
{
    view.IsEnabled = true;
}
```

##### <a name="handle-the-additional-holographiccamera-render-in-directx"></a>Behandeln des zusätzlichen HolographicCamera-Renders in DirectX

Wenn sich die App für das Rendern über die PV-Kamera entschieden hat und die Mixed Reality-Erfassung beginnt:
1. Das CameraAdded-Ereignis von HolographicSpace wird ausgelöst. Dieses Ereignis kann zurückgestellt werden, wenn die App die Kamera derzeit nicht verarbeiten kann.
2. Sobald das Ereignis ohne ausstehende Zurückstellung abgeschlossen wurde, wird die HolographicCamera in der nächsten Liste HinzugefügteCameras von HolographicFrame angezeigt.

Wenn die Mixed Reality-Erfassung beendet wird (oder wenn die App die Ansichtskonfiguration deaktiviert, während die Mixed Reality-Erfassung ausgeführt wird): Die HolographicCamera wird in der Nächsten RemovedCameras-Liste von HolographicFrame angezeigt, und das CameraRemoved-Ereignis von HolographicSpace wird ausgelöst.

HolographicCamera wurde eine [ViewConfiguration-Eigenschaft](/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration) hinzugefügt, um die Konfiguration zu identifizieren, zu der eine Kamera gehört.

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-unity"></a>Aktivieren der PhotoVideoCamera HolographicViewConfiguration in Unity

> [!NOTE]
> Wenn Sie Unity 2018 verwenden, ist **hierfür Unity 2018.4.13f1** oder neuer erforderlich. Wenn Sie Unity 2019 verwenden, erfordert dies **Unity 2019.4** oder eine neuere.

Aktivieren Sie zum Aktivieren des Renderings von der PV-Kamera bei Verwendung des [Mixed Reality Toolkits](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)den [Anbieter Windows Mixed Reality Camera Einstellungen,](/windows/mixed-reality/mrtk-unity/features/camera-system/windows-mixed-reality-camera-settings) und aktivieren **Sie Render from PV Camera (Von PV-Kamera rendern).**

Wenn Sie das Mixed Reality Toolkit nicht verwenden, können Sie eine Komponente verwenden, um sich wie oben für DirectX beschrieben [manuell zu anmelden.](#enable-the-photovideocamera-holographicviewconfiguration-in-directx)

##### <a name="handle-the-additional-holographiccamera-render-in-unity"></a>Behandeln des zusätzlichen HolographicCamera-Renderns in Unity

Dies wird von Unity automatisch für Sie durchgeführt.

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-unreal"></a>Aktivieren der PhotoVideoCamera HolographicViewConfiguration in Unreal

> [!NOTE]
> Dafür ist **Unreal Engine 4.25** oder höher erforderlich.

So abonnieren Sie das Rendering von der FV-Kamera:

1. Rufen Sie **SetEnabledMixedRealityCamera** und **ResizeMixedRealityCamera** auf.
    * Verwenden Sie die Werte **Size X** (Größe X) und **Size Y** (Größe Y), um die Videoabmessungen festzulegen.

![Dritte Kamera](images/unreal-camera-3rd.PNG)

##### <a name="handle-the-additional-holographiccamera-render-in-unreal"></a>Behandeln des zusätzlichen HolographicCamera-Renders in Unreal

Dies wird von Unreal automatisch für Sie durchgeführt.

##### <a name="verify-shaders-and-code-support-additional-cameras"></a>Überprüfen, ob Shader und Code zusätzliche Kameras unterstützen

Führen Sie eine Mixed Reality-Erfassung aus, und überprüfen Sie, ob ungewöhnliche Ausrichtungen, fehlende Inhalte oder Leistungsprobleme auftreten. Aktualisieren Sie Shader und Code nach Bedarf.

Wenn es bestimmte Szenen gibt, die das Rendern für eine zusätzliche Kamera nicht unterstützen können, können Sie die HolographicViewConfiguration von PhotoVideoCamera deaktivieren.

### <a name="disabling-mrc-in-your-app"></a>Deaktivieren von MRC in Ihrer App

#### <a name="2d-app"></a>2D-App

2D-Apps können auswählen, dass ihre visuellen Inhalte verdeckt werden, wenn Mixed Reality Capture ausgeführt wird:
* Mit dem [flag DXGI_PRESENT_RESTRICT_TO_OUTPUT](/windows/desktop/direct3ddxgi/dxgi-present) vorhanden
* Erstellen der Auslagerungskette der App mit dem [flag DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag)
* Legen Sie mit dem Windows 10 May 2019 Update ["IsScreenCaptureEnabled"](/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled) von ApplicationView fest.

#### <a name="immersive-app"></a>Immersive App

Immersive Apps können auswählen, ob ihre visuellen Inhalte aus der Mixed Reality-Erfassung ausgeschlossen werden sollen:
* Festlegen von ["IsContentProtectionEnabled"](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled) von HolographicCameraRenderingParameter zum Deaktivieren der Mixed Reality-Erfassung für den zugehörigen Frame
* Festlegen von [IsHardwareContentProtectionEnabled](/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled) von HolographicCamera zum Deaktivieren der Mixed Reality-Erfassung für die zugehörige holografische Kamera

#### <a name="password-keyboard"></a>Kennworttastatur

Mit dem Windows 10 May 2019 Update werden visuelle Inhalte automatisch aus der Mixed Reality-Erfassung ausgeschlossen, wenn ein Kennwort oder eine Stecknadeltastatur sichtbar ist.

### <a name="knowing-when-mrc-is-active"></a>Wissen, wann MRC aktiv ist

Die [AppCapture-Klasse](/uwp/api/Windows.Media.Capture.AppCapture) kann von einer App verwendet werden, um zu wissen, wann die Mixed Reality-Systemerfassung ausgeführt wird (für Audio oder Video).

>[!NOTE]
>Die [GetForCurrentView-API](/uwp/api/windows.media.capture.appcapture.getforcurrentview) von AppCapture kann NULL zurückgeben, wenn die Mixed Reality-Erfassung auf dem Gerät nicht verfügbar ist. Es ist auch wichtig, die Registrierung des CaptureingChanged-Ereignisses aufzuheben, wenn Ihre App angehalten wird. Andernfalls kann MRC in einen blockierten Zustand gelangen.

### <a name="best-practices-hololens-specific"></a>Bewährte Methoden (HoloLens spezifisch)

ES wird erwartet, dass MRC ohne zusätzlichen Entwicklungsaufwand funktioniert, aber es gibt einige Dinge, die Sie beachten sollten, wenn Sie die beste Mixed Reality-Erfassungserfahrung bereitstellen.

**MRC verwendet den Alphakanal des Hologramms, um sich mit den [Kamerabildern](locatable-camera.md) zu überblenden.**

Der wichtigste Schritt besteht darin, sicherzustellen, dass Ihre App in transparentes Schwarz anstatt in nicht transparentes Schwarz löscht. In Unity erfolgt dies standardmäßig mit dem MixedRealityToolkit. Wenn Sie in Nicht-Unity entwickeln, müssen Sie möglicherweise eine Zeilenänderung vornehmen.

Im Folgenden finden Sie einige Artefakte, die möglicherweise im MRC angezeigt werden, wenn Ihre App nicht in transparentes Schwarz löscht:

**Beispielfehler:** Schwarze Kanten um den Inhalt (wird nicht in transparentes Schwarz gelöscht)

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

**Beispielfehler:** Die gesamte Hintergrundszene des Hologramms wird schwarz angezeigt. Das Festlegen eines Alphawerts im Hintergrund führt zu einem schwarzen Hintergrund.

![Das Festlegen eines Alphahintergrundwerts von 1 führt zu einem schwarzen Hintergrund.](images/clearopaqueblack-300px.png)

**Erwartetes Ergebnis:** Hologramme werden ordnungsgemäß mit der realen Welt kombiniert (erwartetes Ergebnis, wenn das Löschen in transparentes Schwarz erfolgt)

![Erwartetes Ergebnis beim Löschen in transparentes Schwarz](images/cleartransparentblack-300px.png)

**Lösung**:
* Ändern Sie alle Inhalte, die als nicht transparent schwarz angezeigt werden, so, dass sie den Alphawert 0 aufweisen.
* Stellen Sie sicher, dass die App in transparentes Schwarz löscht.
* Unity löscht standardmäßig automatisch mit dem MixedRealityToolkit, aber wenn es sich um eine Nicht-Unity-App handelt, sollten Sie die farbe ändern, die mit ID3D11DeiceContext::ClearRenderTargetView() verwendet wird. Sie möchten sicherstellen, dass Sie transparent schwarz (0,0,0,0) anstelle von deckend schwarz (0,0,0,1) verwenden.

Sie können jetzt die Alphawerte Ihrer Ressourcen optimieren, wenn Sie möchten, dies ist jedoch in der Regel nicht erforderlich. In den meisten Jahren sehen MRCs gut aus. MRC geht von vor multiplizierten Alphas aus. Die Alphawerte wirken sich nur auf die MRC-Erfassung aus.

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a>Was sie erwartet, wenn MRC für HoloLens aktiviert ist

Folgendes gilt sowohl für HoloLens (erste Generation) als auch für HoloLens 2, sofern nicht anders angegeben:

* Das System drosselt die Anwendung auf das 30-Hz-Rendering. Dadurch entsteht ein gewisses Maß an Zeit für die Ausführung von MRC, sodass die App keine konstante Budgetreserve beibehalten muss und auch der MRC-Videoaufzeichnungsframerate von 30 FPS entspricht.
* Hologramminhalte im rechten Auge des Geräts können beim Aufzeichnen/Streamen von MRC "sparkle" erscheinen: Text kann schwieriger zu lesen sein, und Hologrammränder erscheinen möglicherweise verzweigt (die Dritte Kamera wird auf **HoloLens 2** vermeidet diese Kompromittierung).
* MRC-Fotos und -Videos berücksichtigen den [Fokuspunkt](../unity/focus-point-in-unity.md) der Anwendung, wenn die Anwendung sie aktiviert hat, wodurch sichergestellt wird, dass Hologramme korrekt positioniert sind. Bei Videos wird der Fokuspunkt geglättet, sodass Hologramme langsam abdriften können, wenn sich die Fokuspunkttiefe erheblich ändert. Hologramme, die sich in unterschiedlichen Tiefen vom Fokuspunkt befinden, können von der realen Welt versetzt erscheinen (siehe Beispiel unten, in dem der Fokuspunkt auf 2 Meter festgelegt ist, das Hologramm jedoch bei 1 Meter positioniert ist).

![Hologramme bei 2 Metern wird perfekt für die Welt registriert angezeigt. Hologramme bei nahem oder fernen Abstand kann leicht versetzt werden.](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a>Integrieren von MRC-Funktionen aus Ihrer App

Ihre Mixed Reality-App kann MRC-Foto- oder -Videoaufnahmen innerhalb der App starten, und der erfasste Inhalt wird Ihrer App zur Verfügung gestellt, ohne im "Kameraroll" des Geräts gespeichert zu werden. Sie können einen benutzerdefinierten MRC-Aufzeichnungsgerät erstellen oder die integrierte Kameraerfassungsbenutzeroberfläche nutzen. 

### <a name="mrc-with-built-in-camera-ui"></a>MRC mit integrierter Kamerabenutzeroberfläche

Entwickler können die *[Kameraaufnahme-UI-API](/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* verwenden, um ein vom Benutzer erfasstes Mixed Reality-Foto oder -Video mit nur wenigen Codezeilen zu erhalten.

Diese API startet die integrierte MRC-Kamerabenutzeroberfläche, auf der Benutzer ein Foto oder Video aufnehmen und die resultierende Aufnahme an Ihre App zurücksenden können. Sie können einen benutzerdefinierten Mixed Reality-Aufnahme-Aufzeichnungsgerät erstellen, wenn Sie Eine eigene Kamerabenutzeroberfläche oder zugriff auf eine niedrigere Ebene zum Erfassen von Datenströmen hinzufügen müssen.

### <a name="creating-a-custom-mrc-recorder"></a>Erstellen eines benutzerdefinierten MRC-Aufzeichnungsgeräts

Während der Benutzer immer ein Foto oder Video mithilfe des MRC-Erfassungsdiensts des Systems auslösen kann, kann eine Anwendung eine benutzerdefinierte Kamera-App erstellen, die Hologramme wie MRC in den Kameradatenstrom einschließt. Dadurch kann die Anwendung Erfassungen aus Benutzereingaben starten, eine benutzerdefinierte Aufzeichnungsoberfläche erstellen oder MRC-Einstellungen anpassen, um einige Beispiele zu nennen.

**HoloStudio fügt eine benutzerdefinierte MRC-Kamera mit MRC-Effekten hinzu.**

![HoloStudio fügt eine benutzerdefinierte MRC-Kamera mit MRC-Effekten hinzu.](images/cameraiconholostudio-300px.jpg)

Unity-Anwendungen sollten [Locatable_camera_in_Unity](../unity/locatable-camera-in-unity.md) für die -Eigenschaft sehen, um Hologramme zu aktivieren.

Andere Anwendungen können dies erreichen, indem sie die [Windows Media Capture-APIs](/uwp/api/Windows.Media.Capture.MediaCapture) verwenden, um die Kamera zu steuern und einen MRC-Effekt für Video und Audio hinzuzufügen, um virtuelle Hologramme und Anwendungsaudiodaten in Stills und Videos einzubeziehen.

Anwendungen haben zwei Optionen, um den Effekt hinzuzufügen:
* Die ältere API: [Windows. Media.Capture.MediaCapture.AddEffectAsync()](/uwp/api/windows.media.capture.mediacapture.addeffectasync)
* Die neue von Microsoft empfohlene API (gibt ein Objekt zurück, sodass dynamische Eigenschaften bearbeitet werden können): [Windows. Media.Capture.MediaCapture.AddVideoEffectAsync()](/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync)  /  [Windows. Media.Capture.MediaCapture.AddAudioEffectAsync(),](/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) für die die App eine eigene Implementierung von [IVideoEffectDefinition](/uwp/api/Windows.Media.Effects.IVideoEffectDefinition) und [IAudioEffectDefinition](/uwp/api/windows.media.effects.iaudioeffectdefinition)erstellen muss. Beispiele finden Sie in der [MRC-Beispiel-App.](https://github.com/microsoft/Windows-universal-samples/tree/master/Samples/HolographicMixedRealityCapture)

>[!NOTE]
> Die Windows. Der Media.MixedRealityCapture-Namespace wird von Visual Studio nicht erkannt, die Zeichenfolgen sind jedoch weiterhin gültig.

MRC Video Effect (**Windows. Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)

|  Eigenschaftsname  |  Typ  |  Standardwert  |  Beschreibung |
|----------|----------|----------|----------|
|  StreamType  |  UINT32 ([MediaStreamType](/uwp/api/Windows.Media.Capture.MediaStreamType))  |  1 (VideoRecord)  |  Beschreiben Sie, für welchen Erfassungsstream dieser Effekt verwendet wird. Audio ist nicht verfügbar. |
|  HologramCompositionEnabled  |  boolean  |  TRUE  |  Flag zum Aktivieren oder Deaktivieren von Hologrammen in der Videoaufnahme. |
|  RecordingIndicatorEnabled  |  boolean  |  TRUE  |  Flag zum Aktivieren oder Deaktivieren des Aufzeichnungsindikators auf dem Bildschirm während der Hologrammerfassung. |
|  VideoStabilizationEnabled  |  boolean  |  FALSE  |  Flag zum Aktivieren oder Deaktivieren der videoaktivierung, die von der HoloLens Tracker unterstützt wird. |
|  VideoStabilizationBufferLength  |  UINT32  |  0  |  Legen Sie fest, wie viele Verlaufsframes für die Videointeressierung verwendet werden. 0 ist eine Latenz von 0 und im Hinblick auf Leistung und Leistung nahezu "kostenlos". 15 wird für höchste Qualität empfohlen (auf Kosten von 15 Frames mit Latenz und Arbeitsspeicher). |
|  GlobalOpacityCoefficient  |  float  |  0.9 (HoloLens) 1.0 (immersives Headset)  |  Legen Sie den globalen Deckkraftkoeffizienten des Hologramms im Bereich von 0,0 (vollständig transparent) bis 1,0 (vollständig deckend) fest. |
|  BlankOnProtectedContent  |  boolean  |  FALSE  |  Flag zum Aktivieren oder Deaktivieren der Rückgabe eines leeren Frames, wenn eine 2D-UWP-App geschützten Inhalt anzeigt. Wenn dieses Flag FALSE ist und eine 2D-UWP-App geschützte Inhalte anzeigt, wird die 2d-UWP-App durch eine geschützte Inhaltstextur sowohl im Headset als auch in der Mixed Reality-Erfassung ersetzt. |
|  ShowHiddenMesh  |  boolean  |  FALSE  |  Flag zum Aktivieren oder Deaktivieren der Anzeige des verborgenen Bereichsgitters und des benachbarten Inhalts der holografischen Kamera. |
| OutputSize | Size | 0, 0 | Legen Sie die gewünschte Ausgabegröße nach dem Zuschneiden für die Videostabilisierung fest. Eine Standard zugeschnittene Größe wird ausgewählt, wenn 0 oder eine ungültige Ausgabegröße angegeben wird. |
| PreferredHologramPerspective | UINT32 | **Rendern über die Kameraeinstellung** im Windows Geräteportal | Enumeration, die verwendet wird, um anzugeben, welche Holografische Kameraansichtskonfiguration erfasst werden soll: 0 (Anzeige) bedeutet, dass die App nicht aufgefordert wird, von der Foto-/Videokamera zu rendern. 1 (PhotoVideoCamera) fordert die App auf, von der Foto-/Videokamera zu rendern (sofern die App dies unterstützt). Nur auf HoloLens 2 unterstützt |

>[!NOTE]
> Sie können den Standardwert von **PreferredHologramPerspective** im Windows Geräteportal ändern, indem Sie zur [Seite Mixed Reality-Aufnahme](using-the-windows-device-portal.md#mixed-reality-capture) wechseln und Render **from Camera** deaktivieren. Die Einstellung ist standardmäßig **auf 1 (PhotoVideoCamera)** festgelegt, kann jedoch deaktiviert werden, um sie auf **0 (Anzeige)** festzulegen.
>
> Der Standardwert von **PreferredHologramPerspective** war **0 (Anzeige)** vor dem Update vom Juni 2020 (Windows Holographic, Version 2004 Build 19041.1106 und Windows Holographic, Version 1903 Build 18362.1064).

MRC Audio Effect (**Windows. Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)

| Eigenschaftsname | Typ | Standardwert | Beschreibung |
|----------|----------|----------|----------|
| MixerMode | UINT32 | 2 (Mikrofon- und Systemaudio) | Enumeration, die angibt, welche Audioquellen verwendet werden sollen: 0 (nur Mikrofonaudio), 1 (nur Systemaudio), 2 (Mikrofon- und Systemaudio) |
| LoopbackGain | float | **Einstellung "App-Audiogewinn"** im Windows Geräteportal | Sie erhalten eine Anwendung auf die Systemaudiolautstärke. Liegt zwischen 0,0 und 5,0. Nur auf HoloLens 2 unterstützt |
| MicrophoneGain | float | **Einstellung "Mikrofonaudiogewinn"** im Windows Geräteportal | Sie erhalten, um sie auf die Mikrofonlautstärke anzuwenden. Liegt zwischen 0,0 und 5,0. Nur auf HoloLens 2 unterstützt |

>[!NOTE]
> Sie können den Standardwert von **LoopbackGain** oder **MicrophoneGain** im Windows Geräteportal ändern, indem Sie zur [seite Mixed Reality-Aufnahme](using-the-windows-device-portal.md#mixed-reality-capture) wechseln und den Schieberegler neben den jeweiligen Einstellungen anpassen. Beide Einstellungen sind standardmäßig auf **1,0** festgelegt, können jedoch auf einen beliebigen Wert zwischen **0,0** und **5,0** festgelegt werden.
>
> Die Verwendung von Windows Geräteportal zum Konfigurieren der Standardgewinnwerte wurde mit dem Update vom Juni 2020 hinzugefügt (Windows Holographic, Version 2004 Build 19041.1106 und Windows Holographic, Version 1903 Build 18362.1064).

### <a name="simultaneous-mrc-limitations"></a>Gleichzeitige MRC-Einschränkungen

Sie müssen bestimmte Einschränkungen beachten, wenn mehrere Apps gleichzeitig auf MRC zugreifen.

#### <a name="photovideo-camera-access"></a>Foto-/Videokamerazugriff

Bei HoloLens 1 kann MRC kein Foto oder Video aufnehmen, während ein Prozess das Video oder das Aufnehmen eines Fotos aufzeichnet. Das Gegenteil gilt auch: Wenn MRC ausgeführt wird, erhält die Anwendung keinen Zugriff auf die Kamera. 

Mit HoloLens 2 können Sie den Zugriff auf die Kamera freigeben. Wenn Sie keine direkte Steuerung der Auflösung oder Framerate benötigen, können Sie MediaCapture mithilfe der [SharedMode-Eigenschaft](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041) mit SharedReadOnly initialisieren.  

##### <a name="built-in-mrc-photovideo-camera-access"></a>Integrierter MRC-Foto-/Videokamerazugriff

In Windows 10 integrierte MRC-Funktionalität (über Cortana, Startmenü, Hardwareverknüpfungen, Miracast, Windows Geräteportal):

* Wird standardmäßig mit ExclusiveControl ausgeführt.

Dem MRC-Subsystem wurde jedoch Unterstützung für den Betrieb im freigegebenen Modus hinzugefügt: 

* Wenn eine App ExclusiveControl-Zugriff auf die Foto-/Videokamera anfordert, beendet das integrierte MRC automatisch die Verwendung der Foto-/Videokamera, sodass die Anforderung der App erfolgreich ist. 
* Wenn das integrierte MRC gestartet wird, während eine App über ExclusiveControl verfügt, wird das integrierte MRC im SharedReadOnly-Modus ausgeführt. 

Diese Funktionalität im gemeinsam genutzten Modus weist bestimmte Einschränkungen auf:

* Foto über Cortana, Hardwareverknüpfungen oder Startmenü: Erfordert das Update für Windows 10 April 2018 (oder höher)
* Video über Cortana, Hardwareverknüpfungen oder Startmenü: Erfordert das update Windows 10 April 2018 (oder höher)
* Streaming-MRC über Miracast: Erfordert die Windows 10 October 2018 Update (oder höher)
* Streaming-MRC über Windows Geräteportal oder über die HoloLens Begleit-App: Erfordert HoloLens 2

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

Ein vollständiges Beispiel des oben genannten Prozesses finden Sie im [Holographic Face Tracking-Beispiel.](/samples/microsoft/windows-universal-samples/holographicfacetracking)

> [!NOTE]
> Vor dem Windows 10 Update vom April 2018 hat sich der benutzerdefinierte MRC-Recorder einer App mit dem MRC des Systems (Erfassen von Fotos, Aufzeichnen von Videos oder Streamen aus dem Windows Geräteportal) gegenseitig ausschließen.

## <a name="see-also"></a>Siehe auch

* [Mixed-Reality-Aufnahme](/hololens/holographic-photos-and-videos)
* [Spectator View](spectator-view.md)
* [Übersicht über die Unity-Entwicklung](../unity/unity-development-overview.md)
* [Ureal-Entwicklung – Übersicht](../unreal/unreal-development-overview.md)
