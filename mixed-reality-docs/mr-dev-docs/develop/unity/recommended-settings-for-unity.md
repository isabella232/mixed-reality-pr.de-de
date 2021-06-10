---
title: Empfohlene Einstellungen für Unity
description: Erfahren Sie mehr über die Leistung und das Veröffentlichungsverhalten von Unity für Mixed Reality-Apps, die über Projekteinstellungen umgeschaltet werden können.
author: hferrone
ms.author: v-hferrone
ms.date: 07/29/2020
ms.topic: article
keywords: Unity, Einstellungen, Mixed Reality, HoloLens, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Leistung, Qualitätseinstellungen, Beleuchtungseinstellungen, Tiefenpuffer, xr, Nachverfolgungsverlust
ms.openlocfilehash: 7516ec89c49a12e7cb143d7e53d00efde0e44c4e
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743379"
---
# <a name="recommended-settings-for-unity"></a>Empfohlene Einstellungen für Unity

Unity bietet eine Reihe von Standardoptionen, die im Allgemeinen der durchschnittliche Fall für alle Plattformen sind. Unity bietet jedoch einige für Mixed Reality spezifische Verhaltensweisen, die über Projekteinstellungen umgeschaltet werden können.

## <a name="performant-environment-set-up"></a>Einrichten einer performanten Umgebung

### <a name="low-quality-settings"></a>Einstellungen mit niedriger Qualität

Es ist wichtig, die **Unity-Qualitätseinstellungen** in **Sehr niedrig** zu ändern, damit Ihre Anwendung ausgeführt wird und mit der entsprechenden Framerate gut funktioniert, insbesondere für die HoloLens-Entwicklung. Für die Entwicklung von immersiven Headsets kann je nach den Spezifikationen des Desktops, der die VR-Umgebung anstreichen, immer noch eine Framerate ohne die Parameter der niedrigsten Qualität erzielt werden.

In Unity 2019 LTS+ können Sie die Qualitätsstufe des Projekts festlegen, indem **Sie** zu  >  **Projekteinstellungsqualität** bearbeiten  >   und **standard** festlegen, indem Sie auf den Pfeil nach unten auf die Ebene **Sehr niedrige Qualität" klicken.

### <a name="lighting-settings"></a>Beleuchtungseinstellungen

Ähnlich wie bei Quality-Szeneneinstellungen ist es wichtig, optimale Beleuchtungseinstellungen für Ihre Mixed Reality-Anwendung festzulegen. In Unity ist die Beleuchtungseinstellung, die in der Regel die größten Auswirkungen auf die Leistung Ihrer Szene hat, **Realtime Global Lighting**. Sie können die globale Beleuchtung deaktivieren, indem Sie zu  >  **Fensterrendering-Beleuchtungseinstellungen**  >    >  **In Echtzeit globaler Beleuchtung gehen.**

Es gibt eine weitere Beleuchtungseinstellung, **Baked Global Lighting**. Diese Einstellung kann leistungs- und visuell ansprechende Ergebnisse auf immersiven Headsets liefern, ist aber nicht für die HoloLens-Entwicklung anwendbar. **Baked GlobalOas** wird nur für statische GameObjects berechnet, die in HoloLens-Szenen aufgrund der Natur einer unbekannten und sich ändernden Umgebung nicht gefunden werden.

Weitere Informationen finden Sie [unter Global Auslese aus Unity.](https://docs.unity3d.com/Manual/GIIntro.html) 

>[!NOTE]
> **Realtime Global Scene** wird pro Szene festgelegt, und daher müssen Entwickler diese Eigenschaft für jede **Unity-Szene** in ihrem Projekt speichern.

### <a name="single-pass-instancing-rendering-path"></a>Renderingpfad für Einzeldurchlaufinstanzierung

In Mixed Reality Anwendungen wird die Szene zweimal gerendert, einmal für jedes Auge des Benutzers. Im Vergleich zur herkömmlichen 3D-Entwicklung verdoppelt sich dadurch effektiv der Arbeitsaufwand, der berechnet werden muss. Es ist wichtig, den effizientesten Renderingpfad in Unity auszuwählen, um cpu- und GPU-Zeit zu sparen. Single-Pass-Instanzrendering optimiert die Unity-Renderingpipeline für Mixed Reality-Apps, und es wird empfohlen, diese Einstellung standardmäßig für jedes Projekt zu aktivieren.

Aktivieren dieser Funktion in Ihrem Unity-Projekt

1)  Öffnen Sie die **Player XR Settings** (Player XR-Einstellungen) (navigieren Sie zu **Edit** > **Project Settings** > **Player** > **XR Settings** („Bearbeiten > Projekteinstellungen > Player > XR-Einstellungen))
2) Wählen Sie im Dropdownmenü **Stereo Rendering Method** (Stereo-Renderingmethode) **Single Pass Instanced** (Single-Pass-Instanz) aus (das Kontrollkästchen **Virtual Reality Supported** (Virtuelle Realität unterstützt) muss aktiviert sein)

Weitere Informationen zu diesem Renderingansatz finden Sie in den folgenden Artikeln von Unity.

- [How to maximize AR and VR performance with advanced stereo rendering](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/) (Maximieren der AR- und VR-Leistung mit erweitertem Stereorendering)
- [Single Pass Instancing](https://docs.unity3d.com/Manual/SinglePassInstancing.html) (Single-Pass-Instanziierung)

>[!NOTE]
> Ein häufiges Problem beim Single-Pass-Instanzrendering tritt auf, wenn Entwickler bereits vorhandene benutzerdefinierte Shader einsetzen, die noch nicht für die Instanziierung geschrieben wurden. Nach dem Aktivieren dieses Features stellen die Entwickler möglicherweise fest, dass manche Spielobjekte nur für ein Auge gerendert werden. Dies hat den Grund, dass die zugeordneten benutzerdefinierten Shader nicht die geeigneten Eigenschaften für die Instanziierung aufweisen.
>
> Informationen zum Beheben dieses Problems finden Sie unter [Single Pass Stereo Rendering for HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) (Single-Pass-Stereorendering für HoloLens) von Unity

### <a name="enable-depth-buffer-sharing"></a>Aktivieren der Tiefenpufferfreigabe

Um eine bessere Hologrammstabilität aus der Wahrnehmung des Benutzers zu erzielen, wird empfohlen, die **Eigenschaft Tiefenpufferfreigabe** in Unity zu aktivieren. Wenn Sie dies aktivieren, teilt Unity die von Ihrer Anwendung erzeugte Tiefenzuordnung mit der Windows Mixed Reality-Plattform. Die Plattform kann dann die Hologrammstabilität speziell für Ihre Szene für jeden frame verbessern, der von Ihrer Anwendung gerendert wird.

Aktivieren dieser Funktion in Ihrem Unity-Projekt

1) Öffnen Sie die **Player XR Settings** (Player XR-Einstellungen) (navigieren Sie zu **Edit** > **Project Settings** > **Player** > **XR Settings** („Bearbeiten > Projekteinstellungen > Player > XR-Einstellungen))
2) Aktivieren Sie das Kontrollkästchen **Tiefenpufferfreigabe aktivieren** unter **Virtual Reality SDKs**  >  **Windows Mixed Reality** Erweiterung ( Das Kontrollkästchen **Virtual Reality unterstützt** muss aktiviert sein).

Darüber hinaus wird empfohlen, in diesem Bereich unter der Einstellung **Tiefenformat** die **16-Bit-Tiefe** auszuwählen, insbesondere für die HoloLens-Entwicklung. Die Auswahl von 16-Bit im Vergleich zu 24-Bit reduziert die Bandbreitenanforderungen erheblich, da weniger Daten verschoben/verarbeitet werden müssen.

Damit die Windows Mixed Reality Plattform die Hologrammstabilität optimieren kann, muss der Tiefenpuffer genau sein und mit allen gerenderten Hologrammen auf dem Bildschirm übereinstimmen. Daher ist es bei der Tiefenpufferfreigabe beim Rendern von Farben wichtig, auch die Tiefe zu rendern. In Unity rendern die meisten nicht transparenten oder TransparentCutout-Materialien standardmäßig die Tiefe, aber transparente und Textobjekte rendern die Tiefe nicht, obwohl dies shaderabhängig ist usw.

Bei Verwendung des [Mixed Reality Toolkit Standard-Shaders](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)zum Rendern der Tiefe für transparente Objekte:

1) Wählen Sie das transparente Material aus, das den MRTK Standard-Shader verwendet, und öffnen Sie das Inspektor-Editorfenster.
2) Wählen Sie in der Warnung für die Tiefenpufferfreigabe die Schaltfläche **Jetzt korrigieren** aus. Dies kann auch manuell erfolgen, indem Sie den **Renderingmodus** auf **Benutzerdefiniert** festlegen. legen Sie dann **Modus** auf **Transparent** und schließlich **Tiefenschreibvorgang** auf **Ein** fest.

> [!IMPORTANT]
> Entwickler sollten sich vor Z-Fighting schützen, wenn sie diese Werte zusammen mit den Einstellungen der Nah-/Fernebene der Kamera ändern. Z-Fighting tritt auf, wenn zwei Gameobjects versuchen, auf dasselbe Pixel und aufgrund von Genauigkeitsbeschränkungen des Tiefenpuffers zu rendern (d.h. z Tiefe), Unity kann nicht erkennen, welches Objekt sich vor dem anderen befindet. Entwickler werden ein Flackern zwischen zwei Spielobjekten bemerken, während *sie* auf denselben Z-Tiefenwert blättern. Dies kann durch Wechseln zum 24-Bit-Tiefenformat gelöst werden, da für jedes Objekt ein größerer Wertebereich für die Z-Tiefe der Kamera berechnet werden soll.
>
> Es wird jedoch insbesondere für die HoloLens-Entwicklung empfohlen, stattdessen die Nah- und Fernebenen der Kamera in einen kleineren Bereich zu ändern und das 16-Bit-Tiefenformat beizubehalten. Die Z-Tiefe wird nicht linear dem Wertebereich entlang der nah- und fernen Kameraebenen zugeordnet. Dies kann geändert werden, indem Sie die *Hauptkamera* in Ihrer Szene auswählen und unter **Inspektor** die Werte **near & Far Clipping Plane** ändern, um ihren Bereich zu verringern (d. h. von 1000m bis 100m oder einem anderen x-Wert usw.)

>[!IMPORTANT]
> [Unity erstellt keinen Schablonenpuffer,](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) wenn das 16-Bit-Tiefenformat verwendet wird. Daher funktionieren einige Unity-Ui-Effekte und andere Schablonen-erforderliche Effekte nur, wenn das 24-Bit-Tiefenformat ausgewählt ist, das einen [8-Bit-Schablonenpuffer](https://docs.unity3d.com/Manual/SL-Stencil.html)erstellt.

### <a name="building-for-il2cpp"></a>Erstellen für IL2CPP

Unity verfügt über veraltete Unterstützung für das .NET-Skript-Back-End und empfiehlt entwicklern daher, **IL2CPP** für ihre UWP-Visual Studio-Builds zu verwenden. Obwohl dies verschiedene Vorteile bietet, kann die Erstellung Ihrer Visual Studio-Projektmappe aus Unity für **IL2CPP** langsamer sein als die alte .NET-Methode. Daher wird dringend empfohlen, die bewährten Methoden zum Erstellen von **IL2CPP** zu befolgen, um die Iterationszeit der Entwicklung zu sparen.

1) Nutzen Sie inkrementelles Erstellen, indem Sie Ihr Projekt jedes Mal im selben Verzeichnis erstellen und die vorgefertigten Dateien dort wiederverwenden.
2) Deaktivieren von Antischadsoftwarescans für Ihr Projekt & Buildordner
   - Öffnen **Sie Virus & Threat Protection** unter Ihrer App mit den Windows 10-Einstellungen.
   - Wählen Sie unter Einstellungen für **Viren & Bedrohungsschutz die Option** Einstellungen **verwalten** aus.
   - Wählen Sie im Abschnitt **Ausschlüsse** die Option **Ausschlüsse hinzufügen oder entfernen** aus.
   - Wählen **Sie Ausschluss hinzufügen** aus, und wählen Sie den Ordner mit Ihrem Unity-Projektcode und den Buildausgaben aus.
3) Verwenden einer SSD zum Erstellen

Weitere Informationen finden Sie unter [Optimieren der Buildzeiten für IL2CPP.](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)

> [!NOTE]
> Darüber hinaus es kann vorteilhaft sein, besonders für Unity-Projekte mit sehr vielen Ressourcen (mit Ausnahme von Skriptdateien) oder ständig wechselnden Szenen/Ressourcen, einen [Cacheserver](https://docs.unity3d.com/Manual/CacheServer.html) einzurichten. Beim Öffnen eines Projekts speichert Unity die qualifizierenden Ressourcen in einem internen Cacheformat auf dem Entwicklercomputer. Bei Änderungen müssen die Elemente neu importiert und daher neu verarbeitet werden. Dieser Prozess kann einmal durchgeführt, in einem Cacheserver gespeichert und anschließend für andere Entwickler freigegeben werden, damit diese Zeit sparen und den erneuten Import der Änderungen nicht mehr einzeln und lokal verarbeiten müssen.

## <a name="publishing-properties"></a>Veröffentlichen von Eigenschaften

### <a name="holographic-splash-screen"></a>Holografischer Begrüßungsbildschirm

HoloLens verfügt über eine CPU und GPU der mobilen Klasse, was bedeutet, dass das Laden von Apps etwas länger dauern kann. Während die App geladen wird, werden Benutzer nur schwarz angezeigt, sodass sie sich möglicherweise fragen, was passiert. Um sie während des Ladens zu bestärken, können Sie einen holografischen Begrüßungsbildschirm hinzufügen.

So schalten Sie den holografischen Begrüßungsbildschirm um:

1) Wechseln Sie zur Seite **Projekteinstellungen bearbeiten**  >    >  **Player.**
2) Wählen Sie die Registerkarte **Windows Store** aus, und öffnen Sie den Abschnitt **Begrüßungsbild.**
3) Wenden Sie Ihr Bild unter der **Windows Holographic > Holographic Splash Image-Eigenschaft** an.
    - Durch Das Umschalten der Option **Unity-Begrüßungsbildschirm anzeigen** wird der Begrüßungsbildschirm mit Unity-Marke aktiviert oder deaktiviert. Wenn Sie nicht über eine Unity Pro-Lizenz verfügen, wird immer der Begrüßungsbildschirm mit Unity-Branding angezeigt.
    - Wenn ein **Holographic Splash-Bild** angewendet wird, wird es immer angezeigt, unabhängig davon, ob das Kontrollkästchen Unity-Begrüßungsbildschirm anzeigen aktiviert oder deaktiviert ist. Die Angabe eines benutzerdefinierten holografischen Begrüßungsbilds ist nur für Entwickler mit einer Unity Pro-Lizenz verfügbar.

|  Unity-Begrüßungsbildschirm anzeigen  |  Holographic Splash Image  |  Verhalten |
|----------|----------|----------|
|  Ein  |  Keine  |  Anzeigen des Standardmäßigen Unity-Begrüßungsbildschirms für 5 Sekunden oder bis zum Laden der App, je nachdem, welcher Wert länger ist. |
|  Ein  |  Benutzerdefiniert  |  Anzeigen eines benutzerdefinierten Begrüßungsbildschirms für 5 Sekunden oder bis zum Laden der App, je nachdem, welcher Wert länger ist. |
|  Aus  |  Keine  |  Zeigen Sie transparent schwarz (nichts) an, bis die App geladen wird. |
|  Aus  |  Benutzerdefiniert  |  Anzeige des benutzerdefinierten Begrüßungsbildschirms für 5 Sekunden oder bis zum Laden der App, je nach längerer Anzeige. |

Weitere Informationen finden Sie in der Dokumentation zum Begrüßungsbildschirm von [Unity.](https://docs.unity3d.com/Manual/class-PlayerSettingsSplashScreen.html)

### <a name="tracking-loss"></a>Verlust der Nachverfolgung

Ein Mixed [Reality-Headset](coordinate-systems-in-unity.md)hängt davon ab, wie die Umgebung um es herum zu sehen ist, um weltweit gesperrte Koordinatensysteme zu erstellen, mit denen Hologramme in Position bleiben können. Wenn sich das Headset nicht auf der Welt finden kann, wird das Headset als *verlorene Nachverfolgung bezeichnet.* In diesen Fällen funktionieren Funktionen, die von weltgesperrten Koordinatensystemen abhängig sind, z. B. räumliche Phasen, Raumanker und räumliche Abbildung, nicht.

Wenn ein Verlust der Nachverfolgung auftritt, besteht das Standardverhalten von [](https://docs.unity3d.com/Manual/ExecutionOrder.html)Unity im Beenden des Renderns von Hologrammen, Anhalten der Spielschleife und Anzeigen einer Benachrichtigung zum Verlust der Nachverfolgung, die dem Anvitätsverhalten des Benutzer folgt. Benutzerdefinierte Benachrichtigungen können auch in Form eines Nachverfolgungsverlustbilds bereitgestellt werden. Für Apps, die von der Nachverfolgung für ihre gesamte Erfahrung abhängig sind, ist es ausreichend, Unity dies vollständig verarbeiten zu lassen, bis die Nachverfolgung wiedererlangt wird. Entwickler können ein benutzerdefiniertes Image zur Verfügung geben, das während des Verlusts der Nachverfolgung angezeigt wird.

So passen Sie das Nachverfolgungsbild für verloren gegangene Bilder an:

1) Wechseln Sie zur **Seite Edit** Project Settings Player  >  **(Projekteinstellungen**  >  **bearbeiten).**
2) Wählen Sie auf der **Registerkarte Windows Store aus,** und öffnen Sie den **Abschnitt Begrüßungsbild.**
3) Wenden Sie Ihr Bild unter der **Eigenschaft Windows Holographic > Tracking Loss Image (Bild für Nachverfolgungsverlust)** an.

#### <a name="opt-out-of-automatic-pause"></a>Deaktivieren der automatischen Pause

Einige Apps erfordern möglicherweise keine Nachverfolgung (z. [B.](coordinate-systems-in-unity.md) Apps mit ausschließlicher Ausrichtung, z. B. Videoanzeigen mit 360 Grad), oder sie müssen die Verarbeitung ohne Unterbrechung fortsetzen, während die Nachverfolgung verloren geht. Sie können den standardmäßigen Verlust des Nachverfolgungsverhaltens deaktivieren, aber Sie sind für das Ausblenden/Deaktivieren von Objekten verantwortlich, die in einem Szenario mit Nachverfolgungsverlust nicht ordnungsgemäß gerendert werden würden. In den meisten Fällen ist der einzige Inhalt, der in diesem Fall gerendert werden sollte, der textgesperrte Inhalt, der um die Hauptkamera zentriert ist.

So deaktivieren Sie das automatische Pausenverhalten:

1) Wechseln Sie zur Seite **Edit** Project Settings Player  >  **(Projekteinstellungsplayer**  >   bearbeiten).
2) Wählen Sie die **Registerkarte Windows Store** aus, und öffnen Sie den Abschnitt **Begrüßungsbild.**
3) Ändern Sie **das Kontrollkästchen Windows Holographic > On Tracking Loss Pause and Show Image (Windows Holographic > Bei Nachverfolgungsverlust anhalten und Bild** anzeigen).

#### <a name="tracking-loss-events"></a>Nachverfolgen von Verlustereignissen

Um benutzerdefiniertes Verhalten zu definieren, wenn die Nachverfolgung verloren geht, behandeln Sie die globalen [Nachverfolgungsverlustereignisse.](tracking-loss-in-unity.md)

### <a name="capabilities"></a>Funktionen

Damit eine App bestimmte Funktionen nutzen kann, muss sie die entsprechenden Funktionen im Manifest deklarieren. Die Manifestdeklarationen können in Unity vorgenommen werden, damit sie in jedem zukünftigen Projektexport enthalten sind.

Funktionen können für eine Mixed Reality aktiviert werden, indem:

1) Wechseln Sie zur **Seite Edit** Project Settings Player  >  **(Projekteinstellungen**  >  **bearbeiten).**
2) Wählen Sie die **Registerkarte Windows Store** aus, öffnen Sie den Abschnitt **Veröffentlichungseinstellungen,** und suchen Sie nach der **Liste Funktionen.**

Die anwendbaren Funktionen zum Aktivieren der häufig verwendeten APIs für Holographic-Apps sind:
<br>

|  Funktion  |  APIs, die Funktionen erfordern |
|----------|----------|
|  SpatialPerception  |  SurfaceObserver |
|  Webcam  |  PhotoCapture und VideoCapture |
|  PicturesLibrary/VideosLibrary  |  PhotoCapture bzw. VideoCapture (beim Speichern des erfassten Inhalts) |
|  Mikrofon  |  VideoCapture (beim Erfassen von Audio), DictationRecognizer, GrammarRecognizer und KeywordRecognizer |
|  InternetClient  |  DictationRecognizer (und zur Verwendung des Unity Profilers) |

## <a name="see-also"></a>Siehe auch

* [Unity-Entwicklung – Übersicht](unity-development-overview.md)
* [Grundlegendes zur Leistung für Mixed Reality](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Leistungsempfehlungen für Unity](performance-recommendations-for-unity.md)