---
title: Empfohlene Einstellungen für Unity
description: Erfahren Sie mehr über die Leistung und das Veröffentlichungsverhalten von Unity, die für Mixed Reality-Apps spezifisch sind, die über Projekteinstellungen umschaltet werden können.
author: hferrone
ms.author: v-hferrone
ms.date: 07/29/2020
ms.topic: article
keywords: Unity, Einstellungen, Mixed Reality, HoloLens, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Leistung, Qualitätseinstellungen, Beleuchtungseinstellungen, Tiefenpuffer, xr, Nachverfolgungsverlust
ms.openlocfilehash: 736ec4c1cc967eaae1ff53728d6e912c4f03a1f17ef75450c93e58b1a1f0064d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211838"
---
# <a name="recommended-settings-for-unity"></a>Empfohlene Einstellungen für Unity

Unity bietet eine Reihe von Standardoptionen, die im Allgemeinen die durchschnittliche Case für alle Plattformen sind. Unity bietet jedoch einige Mixed Reality-spezifische Verhaltensweisen, die über Projekteinstellungen umschaltet werden können.

## <a name="performant-environment-set-up"></a>Performante Umgebungsset up

### <a name="low-quality-settings"></a>Einstellungen mit niedriger Qualität

Es ist wichtig, die **Unity Quality-Einstellungen** in **Sehr** niedrig zu ändern, damit Ihre Anwendung ausgeführt wird und mit der richtigen Framerate gut funktioniert, insbesondere für HoloLens Entwicklung. Für die Entwicklung mit immersiven Headsets kann abhängig von den Spezifikationen des Desktops, der die VR-Umgebung unterstützt, weiterhin Framerate ohne die Parameter der niedrigsten Qualität erreicht werden.

In Unity 2019 LTS+ können Sie die Qualitätsstufe des Projekts festlegen, indem Sie zu Project Einstellungen Quality bearbeiten und den Standardwert festlegen, indem Sie auf den Pfeil nach unten auf die Stufe **Sehr niedrige Qualität  >    >   klicken. 

### <a name="lighting-settings"></a>Beleuchtungseinstellungen

Ähnlich wie bei den Einstellungen der Qualitätsszene ist es wichtig, optimale Beleuchtungseinstellungen für Ihre Mixed Reality festlegen. In Unity ist die Einstellung Beleuchtung, die in der Regel die größte Auswirkung auf die Leistung Ihrer Szene hat, **Realtime Global Unity.** Sie können die globale Beleuchtung deaktivieren, indem Sie zu **Window**  >  **Rendering**  >  **Lighting Einstellungen**  >  **Realtime Global Render (Globale Echtzeit-Beleuchtung) gehen.**

Es gibt eine weitere Beleuchtungseinstellung, **Baked Global International**. Diese Einstellung kann für immersive Headsets performante und visuell ansprechende Ergebnisse liefern, ist aber nicht für die entwicklung HoloLens anwendbar. **Globale Baked-Objekte** werden nur für statische GameObjects berechnet, die aufgrund der Art einer unbekannten und sich ändernden Umgebung nicht in HoloLens Szenen gefunden werden.

Weitere [Informationen finden Sie unter Global Unity.](https://docs.unity3d.com/Manual/GIIntro.html) 

>[!NOTE]
> **"Realtime Global Unity"** wird pro Szene festgelegt, daher müssen Entwickler diese Eigenschaft für jede **Unity-Szene** in ihrem Projekt speichern.

### <a name="single-pass-instancing-rendering-path"></a>Renderingpfad für single pass instancing

In Mixed Reality Anwendungen wird die Szene zweimal gerendert, einmal für jedes Auge für den Benutzer. Im Vergleich zur herkömmlichen 3D-Entwicklung verdoppelt dies effektiv die Menge an Arbeit, die berechnet werden muss. Es ist wichtig, den effizientesten Renderingpfad in Unity auszuwählen, um sowohl CPU- als auch GPU-Zeit zu sparen. Single Pass Instanced Rendering optimiert die Unity-Renderingpipeline für Mixed Reality-Apps, und es wird empfohlen, diese Einstellung standardmäßig für jedes Projekt zu aktivieren.

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

Um eine bessere Hologrammstabilität aus der Wahrnehmung des Benutzers zu erzielen, wird empfohlen, die **Eigenschaft Tiefenpufferfreigabe** in Unity zu aktivieren. Wenn Sie dies aktivieren, teilt Unity die von Ihrer Anwendung erzeugte Tiefenzuordnung mit der Windows Mixed Reality Plattform. Die Plattform kann dann die Hologrammstabilität speziell für Ihre Szene für jeden frame optimieren, der von Ihrer Anwendung gerendert wird.

Aktivieren dieser Funktion in Ihrem Unity-Projekt

1) Öffnen Sie die **Player XR Settings** (Player XR-Einstellungen) (navigieren Sie zu **Edit** > **Project Settings** > **Player** > **XR Settings** („Bearbeiten > Projekteinstellungen > Player > XR-Einstellungen))
2) Aktivieren Sie das Kontrollkästchen **Tiefenpufferfreigabe aktivieren** unter Virtual **Reality SDKs**  >  **Windows Mixed Reality** Erweiterung **(Kontrollkästchen Virtual Reality** unterstützt muss aktiviert sein).

Darüber hinaus wird empfohlen, in diesem Bereich unter  der Einstellung Tiefenformat **die Option 16-Bit-Tiefe** auszuwählen, insbesondere für HoloLens Entwicklung. Die Auswahl von 16-Bit im Vergleich zu 24-Bit verringert die Bandbreitenanforderungen erheblich, da weniger Daten verschoben/verarbeitet werden müssen.

Damit die Windows Mixed Reality Hologrammstabilität optimieren kann, muss der Tiefenpuffer genau sein und mit allen gerenderten Hologrammen auf dem Bildschirm übereinstimmen. Daher ist es bei der Tiefenpufferfreigabe beim Rendern der Farbe wichtig, auch die Tiefe zu rendern. In Unity rendern die meisten Opaque- oder TransparentCutout-Materialien standardmäßig die Tiefe, aber transparente Objekte und Textobjekte rendern keine Tiefe, obwohl dies shaderabhängig ist usw.

Wenn Sie den [Mixed Reality Toolkit Standard-Shader](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)verwenden, um die Tiefe für transparente Objekte zu rendern:

1) Wählen Sie das transparente Material aus, das den MRTK Standard-Shader verwendet, und öffnen Sie das Editorfenster des Inspektors.
2) Klicken Sie **in der Warnung zur** Tiefenpufferfreigabe auf die Schaltfläche Fix Now (Jetzt korrigieren). Dies kann auch manuell ausgeführt werden, indem der **Renderingmodus auf** Custom (Benutzerdefiniert) **festlegen.** legen Sie dann **Mode (Modus)** **auf Transparent (Transparent)** und schließlich Depth Write **(Tiefenschreiben)** auf **On (Ein) fest.**

> [!IMPORTANT]
> Entwickler sollten sich vor Z-Fighting beim Ändern dieser Werte sowie der Einstellungen der Nah-/Fernebene der Kamera vor dem Z-Fighting-System verlassen. Z-Fighting tritt auf, wenn zwei Gameobjects versuchen, auf das gleiche Pixel zu rendern, und aufgrund von Einschränkungen der Genauigkeit des Tiefenpuffers (d. h. z depth), kann Unity nicht erkennen, welches Objekt sich vor dem anderen befindet. Entwickler werden ein Flackern zwischen zwei Spielobjekten feststellen, während *sie nach* demselben Z-Tiefe-Wert fingieren. Dies kann durch Wechseln in das 24-Bit-Tiefenformat gelöst werden, da für jedes Objekt ein größerer Wertebereich für die Z-Tiefe der Kamera berechnet werden kann.
>
> Es wird jedoch empfohlen, insbesondere für HoloLens-Entwicklung, die Nah- und Fernebene der Kamera stattdessen in einen kleineren Bereich zu ändern und das 16-Bit-Tiefenformat zu behalten. Die Z-Tiefe wird dem Wertebereich entlang der nah- und fernen Kameraebenen nicht linear zugeordnet. Sie können dies ändern, indem Sie *die* Hauptkamera in Ihrer Szene auswählen und unter Inspector die Near **& Far Clipping Plane-Werte** ändern, um ihren Bereich zu verringern (d. h.  von 1000m bis 100m oder einem anderen x-Wert usw.)

>[!IMPORTANT]
> [Unity erstellt keinen Schablonenpuffer, wenn](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) das 16-Bit-Tiefenformat verwendet wird. Daher funktionieren einige Unity-Benutzeroberflächeneffekte und andere für Schablonen erforderliche Effekte nur, wenn das 24-Bit-Tiefenformat ausgewählt ist, wodurch ein [8-Bit-Schablonenpuffer erstellt wird.](https://docs.unity3d.com/Manual/SL-Stencil.html)

### <a name="building-for-il2cpp"></a>Erstellen für IL2CPP

Unity verfügt über veraltete Unterstützung für das .NET-Skript-Back-End und empfiehlt entwicklern daher, **IL2CPP** für ihre UWP-Visual Studio-Builds zu verwenden. Obwohl dies verschiedene Vorteile mit sich bringt, kann das Erstellen Ihrer Visual Studio-Projektmappe aus Unity für **IL2CPP** langsamer als die alte .NET-Methode sein. Daher wird dringend empfohlen, die bewährten Methoden zum Erstellen von **IL2CPP** zu befolgen, um die Iterationszeit für die Entwicklung zu sparen.

1) Nutzen Sie die inkrementelle Entwicklung, indem Sie Ihr Projekt jedes Mal im gleichen Verzeichnis erstellen und dort die vorgefertigten Dateien wiederverwendnen.
2) Deaktivieren von Ansoftwarescans für Ihre Projekt- & Buildordnern
   - Öffnen **Sie Virenschutz & Bedrohungsschutz** in Ihrer App Windows 10-Einstellungen.
   - Wählen **Sie Einstellungen** Unter **Virenschutzeinstellungen & Bedrohungsschutz verwalten aus.**
   - Wählen **Sie im Abschnitt Ausschlüsse die Option** **Ausschlüsse hinzufügen oder** entfernen aus.
   - Wählen **Sie Ausschluss hinzufügen und dann** den Ordner aus, der Ihren Unity-Projektcode und Ihre Buildausgabe enthält.
3) Verwenden eines SSD-Speichers zum Erstellen

Weitere Informationen finden Sie unter Optimieren der Buildzeiten für [IL2CPP.](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)

> [!NOTE]
> Darüber hinaus es kann vorteilhaft sein, besonders für Unity-Projekte mit sehr vielen Ressourcen (mit Ausnahme von Skriptdateien) oder ständig wechselnden Szenen/Ressourcen, einen [Cacheserver](https://docs.unity3d.com/Manual/CacheServer.html) einzurichten. Beim Öffnen eines Projekts speichert Unity die qualifizierenden Ressourcen in einem internen Cacheformat auf dem Entwicklercomputer. Bei Änderungen müssen die Elemente neu importiert und daher neu verarbeitet werden. Dieser Prozess kann einmal durchgeführt, in einem Cacheserver gespeichert und anschließend für andere Entwickler freigegeben werden, damit diese Zeit sparen und den erneuten Import der Änderungen nicht mehr einzeln und lokal verarbeiten müssen.

## <a name="publishing-properties"></a>Veröffentlichungseigenschaften

### <a name="holographic-splash-screen"></a>Holografischer Begrüßungsbildschirm

HoloLens verfügt über eine CPU- und GPU-Klasse für Mobilgeräte, was bedeutet, dass das Laden von Apps etwas länger dauern kann. Während die App geladen wird, wird Benutzern nur Schwarz angezeigt, und sie fragen sich vielleicht, was passiert. Sie können einen holografischen Begrüßungsbildschirm hinzufügen, um sie beim Laden zu vertuschen.

So können Sie den holografischen Begrüßungsbildschirm umschalten:

1) Wechseln Sie **zur Seite**  >  **Project Einstellungen**  >  **Player** bearbeiten.
2) Wählen Sie die **Windows Store** aus, und öffnen Sie den **Abschnitt Begrüßungsbild.**
3) Wenden Sie Ihr Bild unter der Windows **Holographic > Holographic Splash Image an.**
    - Wenn Sie die Option **Unity-Begrüßungsbildschirm anzeigen** umschalten, wird der Begrüßungsbildschirm mit Unity-Marke aktiviert oder deaktiviert. Wenn Sie nicht über eine Unity-lizenz Pro verfügen, wird immer der Begrüßungsbildschirm mit Unity-Marke angezeigt.
    - Wenn ein **Holographic Splash-Bild** angewendet wird, wird es immer angezeigt, unabhängig davon, ob das Kontrollkästchen Unity-Begrüßungsbildschirm anzeigen aktiviert oder deaktiviert ist. Die Angabe eines benutzerdefinierten holografischen Begrüßungsbilds ist nur für Entwickler mit einer Unity-Lizenz Pro verfügbar.

|  Unity-Begrüßungsbildschirm anzeigen  |  Holographic Splash Image  |  Verhalten |
|----------|----------|----------|
|  Ein  |  Keine  |  Standardmäßigen Unity-Begrüßungsbildschirm für 5 Sekunden oder bis zum Laden der App anzeigen, je nach Dem, was länger ist. |
|  Ein  |  Benutzerdefiniert  |  Anzeige des benutzerdefinierten Begrüßungsbildschirms für 5 Sekunden oder bis zum Laden der App, je nach längerer Anzeige. |
|  Aus  |  Keine  |  Zeigen Sie transparentes Schwarz (nichts) an, bis die App geladen wurde. |
|  Aus  |  Benutzerdefiniert  |  Anzeigen eines benutzerdefinierten Begrüßungsbildschirms für 5 Sekunden oder bis zum Laden der App, je nachdem, welcher Wert länger ist. |

Weitere Informationen finden Sie in [der Unity-Dokumentation zu Begrüßungsbildschirmen.](https://docs.unity3d.com/Manual/class-PlayerSettingsSplashScreen.html)

### <a name="tracking-loss"></a>Verlust der Nachverfolgung

Ein Mixed Reality-Headset hängt davon ab, die Umgebung um es herum zu sehen, um [weltweit gesperrte Koordinatensysteme](coordinate-systems-in-unity.md)zu erstellen, mit denen Hologramme an positioniert bleiben können. Wenn sich das Headset nicht auf der Welt finden kann, hat das Headset die *Nachverfolgung verloren.* In diesen Fällen funktionieren Funktionen, die von weltweit gesperrten Koordinatensystemen wie räumlichen Phasen, Raumankern und räumlicher Zuordnung abhängen, nicht.

Wenn ein Verlust der Nachverfolgung auftritt, besteht das Standardverhalten von Unity darin, das Rendern von Hologrammen zu beenden, die [Spielschleife](https://docs.unity3d.com/Manual/ExecutionOrder.html)anzuhalten und eine Benachrichtigung über verlorene Nachverfolgung anzuzeigen, die dem Anverfolgen der Benutzer folgt. Benutzerdefinierte Benachrichtigungen können auch in Form eines Nachverfolgungsverlustbilds bereitgestellt werden. Für Apps, die für ihre gesamte Erfahrung von der Nachverfolgung abhängig sind, reicht es aus, Unity dies vollständig verarbeiten zu lassen, bis die Nachverfolgung wiedererlangt wird. Entwickler können ein benutzerdefiniertes Image bereitstellen, das während des Nachverfolgungsverlusts angezeigt werden soll.

So passen Sie das Nachverfolgungsimage für verlorene Bilder an:

1) Wechseln Sie zur Seite  >  **"Project Einstellungen**  >  **Player** bearbeiten".
2) Wählen Sie auf der Registerkarte **Windows Store** aus, und öffnen Sie den Abschnitt **Begrüßungsbild.**
3) Wenden Sie Ihr Bild unter der **Eigenschaft Windows Holographic > Tracking Loss Image an.**

#### <a name="opt-out-of-automatic-pause"></a>Deaktivieren der automatischen Pause

Einige Apps erfordern möglicherweise keine Nachverfolgung (z. B. apps [mit ausschließlicher Ausrichtung](coordinate-systems-in-unity.md) wie 360-Grad-Videoanzeigen) oder müssen möglicherweise die Verarbeitung unterbrechungsfrei fortsetzen, während die Nachverfolgung verloren geht. Sie können den standardmäßigen Verlust des Nachverfolgungsverhaltens deaktivieren, aber Sie sind dafür verantwortlich, objekte auszublenden/zu deaktivieren, was in einem Nachverfolgungsverlustszenario nicht ordnungsgemäß gerendert würde. In den meisten Fällen ist der einzige Inhalt, der in diesem Fall gerendert werden sollte, der textgesperrte Inhalt, der um die Hauptkamera zentriert ist.

So deaktivieren Sie das automatische Pausenverhalten:

1) Wechseln **Sie** zur Seite  >  **Project Einstellungen**  >  **Player** bearbeiten.
2) Wählen Sie die Registerkarte **Windows Store** aus, und öffnen Sie den Abschnitt **Begrüßungsbild.**
3) Ändern Sie das **Kontrollkästchen Windows Holographic > On Tracking Loss Pause (Bei Nachverfolgungsverlust anhalten) und Show Image (Bild anzeigen).**

#### <a name="tracking-loss-events"></a>Nachverfolgen von Verlustereignissen

Behandeln Sie die globalen [Nachverfolgungsverlustereignisse,](tracking-loss-in-unity.md)um ein benutzerdefiniertes Verhalten zu definieren, wenn die Nachverfolgung verloren geht.

### <a name="capabilities"></a>Funktionen

Damit eine App bestimmte Funktionen nutzen kann, muss sie die entsprechenden Funktionen in ihrem Manifest deklarieren. Die Manifestdeklarationen können in Unity vorgenommen werden, damit sie in jedem zukünftigen Projektexport enthalten sind.

Funktionen können für eine Mixed Reality Anwendung wie folgt aktiviert werden:

1) Wechseln Sie zur Seite  >  **"Project Einstellungen**  >  **Player** bearbeiten".
2) Wählen Sie die Registerkarte **Windows Store** aus, öffnen Sie den Abschnitt **Veröffentlichen Einstellungen,** und suchen Sie nach der Liste **Funktionen.**

Die geeigneten Funktionen zum Aktivieren der häufig verwendeten APIs für Holographic-Apps sind:
<br>

|  Funktion  |  APIs, die Funktionen erfordern |
|----------|----------|
|  SpatialPerception  |  SurfaceObserver |
|  Webcam  |  PhotoCapture und VideoCapture |
|  PicturesLibrary/VideosLibrary  |  PhotoCapture bzw. VideoCapture (beim Speichern der erfassten Inhalte) |
|  Mikrofon  |  VideoCapture (beim Erfassen von Audio), DictationRecognizer, GrammarRecognizer und KeywordRecognizer |
|  InternetClient  |  DictationRecognizer (und zur Verwendung des Unity Profilers) |

## <a name="see-also"></a>Siehe auch

* [Unity-Entwicklung – Übersicht](unity-development-overview.md)
* [Grundlegendes zur Leistung für Mixed Reality](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Leistungsempfehlungen für Unity](performance-recommendations-for-unity.md)