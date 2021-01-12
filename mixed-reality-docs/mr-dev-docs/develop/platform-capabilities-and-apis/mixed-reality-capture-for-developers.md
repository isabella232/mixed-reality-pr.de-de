---
title: Mixed Reality-Aufnahme für Entwickler
description: Erfahren Sie mehr über die bewährten Methoden zum Aktivieren, verwenden und Rendern der Mixed Reality-Erfassung für Entwickler.
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: MRC, Foto, Video, Erfassung, Kamera
ms.openlocfilehash: 40d621133d8aa4c7a58488b80a04ca3b4b46638d
ms.sourcegitcommit: aa29b68603721e909f08f352feed24c65d2e505e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/12/2021
ms.locfileid: "98108863"
---
# <a name="mixed-reality-capture-for-developers"></a>Mixed Reality-Aufnahme für Entwickler

> [!NOTE]
> Unter [Rendering von der folgenden PV-Kamera](#render-from-the-pv-camera-opt-in) finden Sie Anleitungen zu einer neuen MRC-Funktion für hololens 2.

Sie können jederzeit ein Foto oder Video mit [gemischter Realität erfassen](../../mixed-reality-capture.md) , aber es gibt einige Dinge, die Sie beachten sollten, wenn Sie Ihre Anwendung entwickeln. Dies umfasst bewährte Methoden für die visuelle MRC-Qualität und die Reaktion auf Systemänderungen, während mrcs aufgezeichnet werden.

Entwickler können die Erfassung und Einbindung von Mixed Reality auch nahtlos in Ihre apps integrieren.

MRC auf hololens (erste Generation) unterstützt Videos und Fotos bis 720p, während MRC auf hololens 2 Videos bis zu 1080p und Fotos mit einer Auflösung von bis zu 4 KB unterstützt.

## <a name="the-importance-of-quality-mrc"></a>Die Wichtigkeit der Quality MRC

Unabhängig davon, ob es auf Ihrer Microsoft Store Seite oder anderen Benutzern, die Erfassungs Inhalte in sozialen Netzwerken gemeinsam nutzen, Mixed Reality-Screenshots gibt Sie können MRC verwenden, um Ihre APP zu demonstrieren, Benutzer zu informieren, Benutzer zu bitten, ihre gemischten Interaktionen der Welt zu teilen und die Benutzer Forschung und Problembehebung zu lösen.

## <a name="how-mrc-impacts-your-app"></a>Auswirkungen von MRC auf Ihre APP

### <a name="enabling-mrc-in-your-app"></a>Aktivieren von MRC in Ihrer APP

Standardmäßig muss eine APP nichts tun, damit Benutzer gemischte Reality-Erfassungen durchführen können.

### <a name="enabling-improved-alignment-for-mrc-in-your-app"></a>Aktivieren der verbesserten Ausrichtung für MRC in Ihrer APP

Standardmäßig kombiniert Mixed Reality Capture die Holographic-Ausgabe des rechten Auges mit der Photo/Video (PV)-Kamera. Diese beiden Quellen werden mit dem Fokuspunkt kombiniert, der von der derzeit laufenden immersiven App festgelegt wird.

Dies bedeutet, dass holograms außerhalb der Fokusebene aufgrund der physischen Entfernung zwischen der PV-Kamera und der rechten Anzeige nicht ausgerichtet werden.

#### <a name="set-the-focus-point"></a>Festlegen des Fokus Punkts

Immersive Apps (auf hololens) sollten den [Schwerpunkt Punkt](../unity/focus-point-in-unity.md) festlegen, in dem Sie Ihre Stabilisierungs Ebene festlegen möchten. Dadurch wird die beste Ausrichtung sowohl im Headset als auch bei der Erfassung gemischter Realität sichergestellt.

Wenn kein Fokuspunkt festgelegt ist, wird die Stabilisierungs Ebene standardmäßig auf 2 Meter festgelegt.

#### <a name="render-from-the-pv-camera-opt-in"></a>Rendering von der PV-Kamera (Opt-in)

Hololens 2 bietet die Möglichkeit, eine immersive APP **aus der PV-Kamera zu Renderern** , während die gemischte Reality-Erfassung ausgeführt wird. Um sicherzustellen, dass die APP das zusätzliche Rendering ordnungsgemäß unterstützt, muss diese Funktion von der APP übernommen werden.

Das Rendering von der PV-Kamera bietet die folgenden Verbesserungen im Vergleich zum MRC-Standardverhalten:
* Die Ausrichtung von holograms auf die physische Umgebung und die Hände für Near-Interaktionen sollten in allen Abständen genau sein. Vermeiden Sie einen Offset, der nicht mit dem Fokuspunkt in der Entfernung liegt, wie Sie in der MRC-Standardeinstellung sehen können.
* Das richtige Auge im Headset wird nicht beeinträchtigt, da es nicht zum renderingder holograms für die MRC-Ausgabe verwendet wird.

Es gibt drei Schritte, um das Rendering von der PV-Kamera aus zu aktivieren:
1. Aktivieren von "photovideocamera holographicviewconfiguration"
2. Verarbeiten des zusätzlichen holographiccamera-Rendering
3. Überprüfen Sie, ob die Shader und der Code aus diesem zusätzlichen holographiccamera korrekt dargestellt werden.

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-directx"></a>Aktivieren von "photovideocamera holographicviewconfiguration" in DirectX

Um das Rendering von der PV-Kamera zu aktivieren, aktiviert eine APP einfach die [holographicviewconfiguration](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration)von photovideocamera:
```csharp
var display = Windows.Graphics.Holographic.HolographicDisplay.GetDefault();
var view = display.TryGetViewConfiguration(Windows.Graphics.Holographic.HolographicViewConfigurationKind.PhotoVideoCamera);
if (view != null)
{
    view.IsEnabled = true;
}
```

##### <a name="handle-the-additional-holographiccamera-render-in-directx"></a>Verarbeiten des zusätzlichen holographiccamera-Rendering in DirectX

Wenn die APP die Möglichkeit hat, von der PV-Kamera zu Rendering und die Mixed Reality-Erfassung zu starten:
1. Das cameraadded-Ereignis von holographicspace wird ausgelöst. Dieses Ereignis kann verzögert werden, wenn die APP die Kamera zu diesem Zeitpunkt nicht verarbeiten kann.
2. Nachdem das Ereignis ohne ausstehende desystemvorgänge abgeschlossen wurde, wird der holographiccamera in der Liste der addedkameras des nächsten holographicframes angezeigt.

Wenn die gemischte Reality-Erfassung beendet wird (oder wenn die APP die Anzeige Konfiguration deaktiviert, während die gemischte Reality-Erfassung ausgeführt wird): der holographiccamera wird in der removedcameras-Liste des nächsten holographicframes angezeigt, und das Ereignis "cameraremove" wird ausgelöst.

Holographiccamera wurde eine [viewconfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration) -Eigenschaft hinzugefügt, um die Konfiguration zu identifizieren, zu der eine Kamera gehört.

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-unity"></a>Aktivieren von "photovideocamera holographicviewconfiguration" in Unity

> [!NOTE]
> Hierfür ist **Unity 2018.4.13 F1**, **Unity 2019.3.0 F1** oder höher erforderlich.

Aktivieren Sie den [Windows Mixed Reality-Kamera Einstellungs](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/CameraSystem/WindowsMixedRealityCameraSettings.html) Anbieter, und aktivieren Sie Rendering **von der PV-Kamera**, um das Rendering von der PV-Kamera bei Verwendung des [Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)zu aktivieren.

Wenn Sie nicht das Mixed Reality Toolkit verwenden, können Sie eine-Komponente verwenden, um sich wie oben für DirectX beschrieben [manuell zu entscheiden](#enable-the-photovideocamera-holographicviewconfiguration-in-directx) .

##### <a name="handle-the-additional-holographiccamera-render-in-unity"></a>Verarbeiten des zusätzlichen holographiccamera-Rendering in Unity

Dies erfolgt automatisch durch Unity.

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-unreal"></a>Aktivieren von "fotovideocamera holographicviewconfiguration" in Unreal

> [!NOTE]
> Dafür ist **Unreal Engine 4.25** oder höher erforderlich.

So abonnieren Sie das Rendering von der FV-Kamera:

1. Rufen Sie **SetEnabledMixedRealityCamera** und **ResizeMixedRealityCamera** auf.
    * Verwenden Sie die Werte **Size X** (Größe X) und **Size Y** (Größe Y), um die Videoabmessungen festzulegen.

![Dritte Kamera](images/unreal-camera-3rd.PNG)

##### <a name="handle-the-additional-holographiccamera-render-in-unreal"></a>Zusätzliches holographiccamera-Rendering in Unreal behandeln

Dies erfolgt automatisch durch Unreal.

##### <a name="verify-shaders-and-code-support-additional-cameras"></a>Überprüfen von Shadern und Code Unterstützung zusätzlicher Kameras

Führen Sie eine gemischte Reality-Erfassung aus, und überprüfen Sie, ob ungewöhnliche Ausrichtung, fehlende Inhalte oder Leistungsprobleme vorliegen. Aktualisieren Sie Shader und Code entsprechend.

Wenn bestimmte Szenen das Rendern auf eine zusätzliche Kamera nicht unterstützen, können Sie die holographicviewconfiguration von photovideocamera deaktivieren.

### <a name="disabling-mrc-in-your-app"></a>Deaktivieren von MRC in Ihrer APP

#### <a name="2d-app"></a>2D-App

2D-Apps können auswählen, dass Ihre visuellen Inhalte verdeckt werden, wenn die gemischte Reality-Erfassung ausgeführt wird:
* Mit dem [DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-present) -Flag vorhanden
* Erstellen Sie die Swapkette der APP mit dem [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://docs.microsoft.com/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag) -Flag.
* Mit dem Windows 10-Update von Mai 2019, Festlegen von " [isskreendcaptureaktivierte](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled) " von applicationview

#### <a name="immersive-app"></a>Immersive App

Immersive Apps können auswählen, ob Ihre visuellen Inhalte von der gemischten Realität-Erfassung ausgeschlossen werden sollen, indem Sie:
* Festlegen des [iscontentschutzaktivierten](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled) holographiccamerarenderingparameter, um die gemischte Reality-Erfassung für den zugehörigen Frame zu deaktivieren
* Festlegen von " [ishardwarecontentschutzaktivierte](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled) " von holographiccamera zum Deaktivieren der Transformation für gemischte Realität für die zugehörige Holographic-Kamera

#### <a name="password-keyboard"></a>Kenn Wort Tastatur

Mit dem Windows 10-Update von Mai 2019 werden visuelle Inhalte automatisch von Mixed Reality Capture ausgeschlossen, wenn eine Kennwort-oder PIN-Tastatur sichtbar ist.

### <a name="knowing-when-mrc-is-active"></a>Wissen, wenn MRC aktiv ist

Die [appcapture](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.AppCapture) -Klasse kann von einer App verwendet werden, um zu erfahren, wann die gemischte Reality-Erfassung (für Audiodaten oder Videos) ausgeführt wird.

>[!NOTE]
>Die [getforcurrentview](https://docs.microsoft.com/uwp/api/windows.media.capture.appcapture.getforcurrentview) -API von appcapture kann NULL zurückgeben, wenn die gemischte Reality-Erfassung auf dem Gerät nicht verfügbar ist. Es ist auch wichtig, das capturingchanged-Ereignis zu deaktivieren, wenn Ihre APP angehalten wird. andernfalls kann MRC in den Status "blockiert" versetzt werden.

### <a name="best-practices-hololens-specific"></a>Bewährte Methoden (hololens-spezifisch)

MRC funktioniert ohne zusätzlichen Entwicklungsaufwand, aber es gibt einige Dinge, die Sie beachten sollten, wenn Sie die beste Lösung für das umsetzen der Realität bereitstellen.

**MRC verwendet den Alpha-Channel von Hologram, um sich mit den [Kamera](locatable-camera.md) Bildern zu vermischen.**

Der wichtigste Schritt besteht darin, sicherzustellen, dass Ihre APP in transparenter schwarz gelöscht wird, anstatt auf ein undurchsichtiges schwarz zu löschen. In Unity erfolgt dies standardmäßig mit dem mixedrealitytoolkit. Wenn Sie in nicht Unity entwickeln, müssen Sie möglicherweise eine einzelne Zeile ändern.

Im folgenden finden Sie einige der Elemente, die Sie in MRC sehen können, wenn Ihre APP nicht in transparent Black gelöscht wird:

**Beispiel Fehler**: schwarze Ränder um den Inhalt (Fehler beim Löschen in transparente schwarze)

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

**Beispiel Fehler**: die gesamte Hintergrundszene des holograms wird schwarz angezeigt. Das Festlegen eines Hintergrund-Alpha-Werts von einem Ergebnis ist ein schwarzer Hintergrund.

![Das Festlegen eines Hintergrund-Alpha-Werts von 1 ergibt einen schwarzen Hintergrund.](images/clearopaqueblack-300px.png)

**Erwartetes Ergebnis**: holograms werden ordnungsgemäß mit der realen Umgebung gemischt (erwartetes Ergebnis beim Löschen auf transparente schwarze)

![Erwartetes Ergebnis beim Löschen auf transparente schwarze](images/cleartransparentblack-300px.png)

**Lösung**:
* Ändern Sie alle Inhalte, die als undurchsichtiges schwarz angezeigt werden, um einen Alphawert von 0 zu erhalten.
* Stellen Sie sicher, dass die app in transparent Black gelöscht wird.
* Unity wird standardmäßig automatisch mit dem mixedrealitytoolkit gelöscht. wenn es sich jedoch um eine nicht-Unity-App handelt, sollten Sie die mit ID3D11DeiceContext:: clearrendertargetview () verwendete Farbe ändern. Sie möchten sicherstellen, dass Sie transparent Black (0, 0, 0, 0) anstelle von undurchsichtigem schwarz (0, 0, 0, 1) deaktivieren.

Sie können jetzt die Alpha Werte Ihrer Assets optimieren, wenn Sie möchten, aber in der Regel nicht erforderlich sind. In den meisten Fällen sehen die mrcs standardmäßig gut aus. MRC geht davon aus, dass ein prämultipliziertes Alpha Die Alpha Werte wirken sich nur auf die MRC-Erfassung aus.

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a>Was Sie erwartet, wenn MRC auf hololens aktiviert ist

Folgendes gilt für hololens (First-Generation) und hololens 2, sofern nichts anderes angegeben ist:

* Das System drosselt die Anwendung auf das 30-Hz-Rendering. Dadurch wird ein gewisser Spielraum für die MRC-Durchführung geschaffen, sodass die APP keine Konstante Budget Reserve aufbewahren muss und auch mit der MRC-Videodaten Satz Framerate von 30 fps übereinstimmt.
* Der – Hologramm-Inhalt auf der rechten Seite des Geräts wird möglicherweise als "Glanz" angezeigt, wenn Sie MRC aufzeichnen/streamen: Text kann schwieriger zu lesen sein, und – Hologramm-Kanten werden möglicherweise mehr verzweigen angezeigt (bei Dritten Kamera Rendering bei **hololens 2** wird diese Gefährdung vermieden).
* MRC-Fotos und-Videos berücksichtigen den [Schwerpunkt Punkt](../unity/focus-point-in-unity.md) der Anwendung, wenn Sie von der Anwendung aktiviert wurde. Dadurch wird sichergestellt, dass Hologramme genau positioniert werden. Bei Videos wird der Fokuspunkt geglättet, sodass holograms möglicherweise langsam in den Platz wechseln, wenn sich die Fokuspunkt Tiefe erheblich ändert. Holograms, die sich in unterschiedlichen Tiefen vom Fokuspunkt befinden, werden möglicherweise in der realen Welt ausgeglichen (siehe Beispiel unten, wobei der Fokuspunkt auf 2 Meter festgelegt ist, aber – Hologramm auf 1 Meter festgelegt ist).

![Holograms bei 2 Messgeräten werden auf der ganzen Welt hervorragend registriert angezeigt. Holograms in der Nähe oder in weiten Abständen können leicht versetzt werden.](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a>Integrieren von MRC-Funktionen in Ihre APP

Ihre Mixed Reality-App kann die MRC-Foto-oder Video Erfassung in der app starten, und die erfassten Inhalte werden Ihrer APP zur Verfügung gestellt, ohne dass Sie auf der "Kamera-Roll" des Geräts gespeichert werden. Sie können eine benutzerdefinierte MRC-Aufzeichnung erstellen oder die Benutzeroberfläche der integrierten Kamera Erfassung nutzen. 

### <a name="mrc-with-built-in-camera-ui"></a>MRC mit integrierter Kamera-Benutzeroberfläche

Entwickler können die *[API Capture UI API](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* verwenden, um ein vom Benutzer erfasstes gemischtes Reality-Foto oder Video mit nur wenigen Codezeilen zu erhalten.

Diese API gestartet die integrierte MRC-Kamera-Benutzeroberfläche, auf der Benutzer ein Foto oder Video aufnehmen und die resultierende Erfassung an Ihre APP zurückgeben können. Sie können eine benutzerdefinierte Mixed Reality Capture Recorder erstellen, wenn Sie eine eigene Kamera-UI oder einen Zugriff auf niedrigerer Ebene für Erfassungsdaten Ströme hinzufügen müssen.

### <a name="creating-a-custom-mrc-recorder"></a>Erstellen einer benutzerdefinierten MRC-Aufzeichnung

Während der Benutzer immer ein Foto oder Video mit dem System-MRC-Erfassungs Dienst auslöst, möchte eine Anwendung möglicherweise eine benutzerdefinierte Kamera-APP erstellen, die Hologramme in den Kameradaten Strom wie MRC einschließt. Dadurch kann die Anwendung Erfassungen von Benutzereingaben starten, benutzerdefinierte Aufzeichnungs Benutzeroberfläche erstellen oder MRC-Einstellungen anpassen, um einige Beispiele zu nennen.

**Holostudio fügt eine benutzerdefinierte MRC-Kamera mithilfe von MRC-Effekten hinzu**

![Holostudio fügt eine benutzerdefinierte MRC-Kamera mithilfe von MRC-Effekten hinzu](images/cameraiconholostudio-300px.jpg)

Unity-Anwendungen sollten [Locatable_camera_in_Unity](../unity/locatable-camera-in-unity.md) für die-Eigenschaft sehen, um holograms zu aktivieren.

Andere Anwendungen können hierfür die [Windows Media Capture-APIs](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaCapture) verwenden, um die Kamera zu steuern und ein MRC-Video und einen Audioeffekt hinzuzufügen, um virtuelle Hologramme und anwendungaudiodaten in Stills und Videos einzubeziehen.

Anwendungen haben zwei Möglichkeiten, den Effekt hinzuzufügen:
* Die ältere API: [Windows. Media. Capture. mediacapture. addeffectasync ()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addeffectasync)
* Die neue von Microsoft empfohlene API (gibt ein-Objekt zurück, so können Sie dynamische Eigenschaften bearbeiten): [Windows. Media. Capture. mediacapture. addvideoeffectasync ()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync)  /  [Windows. Media. Capture. mediacapture. addaudioeffectasync ()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) , die erfordern, dass die APP eine eigene Implementierung von " [ivideoeffectdefinition](https://docs.microsoft.com/uwp/api/Windows.Media.Effects.IVideoEffectDefinition) " und " [iaudioeffectdefinition](https://docs.microsoft.com/uwp/api/windows.media.effects.iaudioeffectdefinition)" erstellt. Weitere Informationen finden Sie unter MRC [Effekt Beispiel, z. b. Verwendung.

>[!NOTE]
> Der Windows. Media. mixedrealitycapture-Namespace wird von Visual Studio nicht erkannt, aber die Zeichen folgen sind immer noch gültig.

MRC-Video Effekt (**Windows. Media. mixedrealitycapture. mixedrealitycapturevideoeffect**)

|  Eigenschaftenname  |  Typ  |  Standardwert  |  BESCHREIBUNG |
|----------|----------|----------|----------|
|  StreamType  |  UInt32 ([MediaStreamType](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaStreamType))  |  1 (videorecord)  |  Beschreiben Sie den Erfassungsdaten Strom, für den dieser Effekt verwendet wird. Audiodaten sind nicht verfügbar. |
|  Hologramcompositionaktivierte  |  boolean  |  true  |  Flag zum Aktivieren oder Deaktivieren von holograms bei der Video Erfassung. |
|  Recordingindialisioraktiviert  |  boolean  |  true  |  Flag zum Aktivieren oder Deaktivieren des Aufzeichnungs Indikators auf dem Bildschirm während der – Hologramm-Erfassung. |
|  Videostabilizationaktivierte  |  boolean  |  FALSE  |  Flag zum Aktivieren oder Deaktivieren der Videostabilisierung, die von hololens-Tracker unterbunden wird. |
|  Videostabilizationbufferlength  |  UINT32  |  0  |  Legen Sie fest, wie viele historische Frames für die Videostabilisierung verwendet werden. 0 (null): Latenz und nahezu "kostenlos" aus Leistungs-und Leistungs Perspektive. 15 wird für die höchste Qualität empfohlen (auf Kosten von 15 Frames an Latenz und Arbeitsspeicher). |
|  Globalopacitykoeffizienten  |  float  |  0,9 (hololens) 1,0 (immersives Headset)  |  Legen Sie den globalen Deckkraft Koeffizienten von – Hologramm im Bereich von 0,0 (vollständig transparent) auf 1,0 (vollständig deckend) fest. |
|  Blankonprotectedcontent  |  boolean  |  FALSE  |  Flag zum Aktivieren oder Deaktivieren der Rückgabe eines leeren Frames, wenn eine 2D-UWP-App geschützte Inhalte anzeigt. Wenn dieses Flag false ist und eine 2D-UWP-App geschützte Inhalte anzeigt, wird die 2D-UWP-app durch eine geschützte Inhalts Textur sowohl im Headset als auch in der Mixed Reality-Erfassung ersetzt. |
|  Showhiddenmesh  |  boolean  |  FALSE  |  Flag zum Aktivieren oder Deaktivieren der Anzeige des ausgeblendeten Bereichs Netzes der Holographic-Kamera und des benachbarten Inhalts. |
| Outputsize | Size | 0, 0 | Legen Sie die gewünschte Ausgabegröße nach dem Zuschneiden für die Videostabilisierung fest. Eine standardmäßige zuergröße wird ausgewählt, wenn 0 oder eine ungültige Ausgabegröße angegeben wird. |
| Preferredhologrammperspective | UINT32 | **Rendering von der Kamera** Einstellung im Windows-Geräte Portal | Enum, das angibt, welche holografische Kamera Ansichts Konfiguration aufgezeichnet werden soll: 0 (Anzeige) bedeutet, dass die APP nicht zum Rendering von der Foto-/Videokamera aufgefordert wird. 1 (photovideocamera) fordert die APP auf, von der Foto-/Videokamera zu Rendering (sofern Sie von der App unterstützt wird). Wird nur auf hololens 2 unterstützt. |

>[!NOTE]
> Sie können den Standardwert von " **preferredhologramperspective** " im Windows-Geräte Portal ändern, indem Sie zur [Seite "Mixed Reality Capture](using-the-windows-device-portal.md#mixed-reality-capture) " navigieren und die Wiedergabe **von der Kamera** deaktivieren. Die Einstellung ist standardmäßig auf **1 (photovideocamera)** festgelegt, kann jedoch deaktiviert werden, um Sie auf **0 (Anzeige)** festzulegen.
>
> Der Standardwert von **preferredhologramperspective** war vor dem Update vom Juni 2020 (Windows Holographic, Version 2004 Build 19041,1106 und Windows Holographic, Version 1903 Build 18362,1064) der Wert **0 (Display)** .

MRC-Audioeffekt (**Windows. Media. mixedrealitycapture. mixedrealitycaptureaudioeffect**)

| Eigenschaftenname | Typ | Standardwert | BESCHREIBUNG |
|----------|----------|----------|----------|
| Mixermode | UINT32 | 2 (MIC-und systemaudiodatei) | Eine Aufzählung, die verwendet wird, um anzugeben, welche Audioquellen verwendet werden sollen: 0 (nur MIC-Audiodatei), 1 (nur systemaudiodatei), 2 (MIC und systemaudiodatei) |
| Loopbackgewinn | float | Einstellung für **App-audiogewinn** im Windows-Geräte Portal | Auf das systemaudiovolume anwenden. Reicht von 0,0 bis 5,0. Wird nur auf hololens 2 unterstützt. |
| Mikrophonegain | float | Einstellung für **MIC-audiogewinn** im Windows-Geräte Portal | Der auf das MIC-Volume anzuwendende Gewinn. Reicht von 0,0 bis 5,0. Wird nur auf hololens 2 unterstützt. |

>[!NOTE]
> Sie können den Standardwert von **loopbackgewinn** oder " **mikrophonegain** " im Windows-Geräte Portal ändern, indem Sie die [Seite "Mixed Reality Capture](using-the-windows-device-portal.md#mixed-reality-capture) " aufrufen und den Schieberegler neben den jeweiligen Einstellungen anpassen. Beide Einstellungen werden standardmäßig auf **1,0** festgelegt, können jedoch auf einen beliebigen Wert zwischen **0,0** und **5,0** festgelegt werden.
>
> Die Verwendung des Windows-Geräte Portals zum Konfigurieren der Standardwerte für den Gewinn wurde mit dem Update vom Juni 2020 hinzugefügt (Windows Holographic, Version 2004 Build 19041,1106 und Windows Holographic, Version 1903 Build 18362,1064).

### <a name="simultaneous-mrc-limitations"></a>Gleichzeitige MRC-Einschränkungen

Sie müssen bestimmte Einschränkungen beachten, wenn mehrere apps gleichzeitig auf MRC zugreifen.

#### <a name="photovideo-camera-access"></a>Foto-/Videokamera-Zugriff

Bei hololens 1 kann MRC kein Foto aufzeichnen oder Videos aufzeichnen, während ein Prozess das Aufzeichnen von Videos oder das Aufnehmen eines Fotos durchführt. Das Gegenteil gilt auch: Wenn MRC ausgeführt wird, kann die Anwendung keinen Zugriff auf die Kamera erhalten. 

Mit hololens 2 können Sie den Zugriff auf die Kamera freigeben. Wenn Sie keine direkte Steuerung der Auflösung oder der Framerate benötigen, können Sie mediacapture mithilfe der [sharedmode-Eigenschaft](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041) mit sharedreadonly initialisieren.  

##### <a name="built-in-mrc-photovideo-camera-access"></a>Integrierter MRC-Foto-/Videokamer-Zugriff

In Windows 10 integrierte MRC-Funktionalität (über Cortana, Startmenü, Hardware Kombinationen, miracast, Windows-Geräte Portal):

* Wird standardmäßig mit exclusivecontrol ausgeführt

Die Unterstützung des MRC-Subsystems wurde jedoch für den Betrieb in einem freigegebenen Modus hinzugefügt: 

* Wenn eine APP exclusivecontrol-Zugriff auf die Foto-/Videokamera anfordert, wird die integrierte MRC-Datei automatisch mit der Foto-/Videokamera beendet, sodass die App-Anforderung erfolgreich ausgeführt wird. 
* Wenn das integrierte MRC gestartet wird, während eine APP über exclusivecontrol verfügt, wird die integrierte MRC-Datei im sharedreadonly-Modus ausgeführt. 

Diese Funktion für den freigegebenen Modus weist bestimmte Einschränkungen auf:

* Foto über Cortana, Hardware Verknüpfungen oder Startmenü: erfordert Windows 10 April 2018 Update (oder höher)
* Video über Cortana, Hardware Verknüpfungen oder Startmenü: erfordert Windows 10 April 2018 Update (oder höher)
* Streaming von MRC über miracast: erfordert das Windows 10-Update vom Oktober 2018 (oder höher)
* Streaming von MRC über das Windows-Geräte Portal oder über die "hololens Companion"-App: erfordert hololens 2

>[!NOTE]
> Die Auflösung und die Framerate der integrierten MRC-Kamera-Benutzeroberfläche werden möglicherweise von den normalen Werten reduziert, wenn eine andere APP das Foto bzw. die Videokamera verwendet.

#### <a name="mrc-access-for-developers"></a>MRC-Zugriff für Entwickler

Es wird empfohlen, bei der Verwendung von MRC immer exklusive Kontrolle für die Kamera anzufordern. Dadurch wird sichergestellt, dass Ihre Anwendung über die vollständige Kontrolle über die Einstellungen für die Kamera verfügt, solange Sie die oben aufgeführten Einschränkungen kennen. 

* Erstellen eines Medien Erfassungs Objekts mit den [Initialisierungs Einstellungen](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings?view=winrt-19041)
* Festlegen der Eigenschaft " [sharingmode](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041#Windows_Media_Capture_MediaCaptureInitializationSettings_SharingMode) " auf " **exklusiv** "

> [!CAUTION]
> Achten Sie darauf, die [sharingmode-Hinweise](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041#remarks) sorgfältig zu lesen, bevor Sie fortfahren.

* Richten Sie Ihre Kamera auf die gewünschte Weise ein.
* Starten der APP, Aufzeichnen von Video Frames mit der Start-API und anschließendes Aktivieren von MRC

> [!CAUTION]
> Wenn Sie MRC starten, bevor Sie die app starten, können wir nicht garantieren, dass das Feature erwartungsgemäß funktioniert.

Ein vollständiges Beispiel für den oben genannten Prozess finden Sie im [Beispiel für die holografische Gesichts Verfolgung](https://docs.microsoft.com/samples/microsoft/windows-universal-samples/holographicfacetracking).

> [!NOTE]
> Vor dem Windows 10 April 2018-Update war der benutzerdefinierte MRC-Recorder einer APP mit System MRC (Aufzeichnen von Fotos, Erfassen von Videos oder Streaming aus dem Windows-Geräte Portal) gegenseitig exklusiv.

## <a name="see-also"></a>Siehe auch

* [Mixed-Reality-Aufnahme](../../mixed-reality-capture.md)
* [Spectator View](spectator-view.md)
* [Übersicht über Unity-Entwicklung](../unity/unity-development-overview.md)
* [Ureal-Entwicklung – Übersicht](../unreal/unreal-development-overview.md)
