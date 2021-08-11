---
title: 'HoloLens (1. Generation) Räumlich 220: Raumklang'
description: Befolgen Sie diese exemplarische Vorgehensweise für die Codierung mitHilfe von Unity, Visual Studio und HoloLens, um die Details der Räumlichen Soundkonzepte zu erlernen.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, academy, tutorial, spatial sound, HoloLens, Mixed Reality Academy, unity, mixed reality headset, windows mixed reality headset, virtual reality headset, Windows 10
ms.openlocfilehash: d53b449916405d8bf42bb8dd63cc1d3cb5d6127bbf9b2989ce7cb09c3762a6e6
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200375"
---
# <a name="hololens-1st-gen-spatial-220-spatial-sound"></a>HoloLens (1. Generation) Spatial 220: Spatial sound

>[!IMPORTANT]
>Die Mixed Reality Academy-Tutorials wurden im Hinblick auf HoloLens (1. Generation), Unity 2017 und Mixed Reality Immersive Headsets entworfen.  Daher halten wir es für wichtig, diese Tutorials für Entwickler verfügbar zu halten, die noch nach Anleitung beim Entwickeln für diese Geräte suchen. Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für HoloLens 2 verwendet werden, und sind möglicherweise nicht mit neueren Versionen von Unity kompatibel.  Sie werden gewartet, um weiterhin auf den unterstützten Geräten zu funktionieren. [Es wurde eine neue Reihe von Tutorials](mrlearning-base.md) für HoloLens 2 veröffentlicht.

[Räumlicher Sound](../../../design/spatial-sound.md) verkörpert das Leben in Hologramme und gibt ihnen Präsenz in unserer Welt. Hologramme bestehen aus Licht und Sound, und wenn Sie Ihre Hologramme aus den Augen verlieren, kann räumlicher Sound Ihnen helfen, sie zu finden. Räumlicher Sound entspricht nicht dem typischen Sound, den Sie im Radio hören würden, es ist ein Sound, der im 3D-Raum positioniert ist. Mit räumlichem Sound können Sie Hologramme so klingen lassen, wie sie sich hinter Ihnen, neben Ihnen oder sogar auf dem Kopf befindet! In diesem Kurs werden Sie:

* Konfigurieren Sie Ihre Entwicklungsumgebung für die Verwendung von Microsoft Spatial Sound.
* Verwenden Sie räumlichen Sound, um Interaktionen zu verbessern.
* Verwenden Sie räumlichen Sound in Verbindung mit [spatial mapping](../../../design/spatial-mapping.md).
* Grundlegendes zum Sounddesign und zum Kombinieren bewährter Methoden.
* Verwenden Sie Sound, um spezielle Effekte zu verbessern und den Benutzer in die Mixed Reality Welt zu bringen.

## <a name="device-support"></a>Geräteunterstützung

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td>MR räumlich 220: Raumklang</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Vorbereitung

### <a name="prerequisites"></a>Voraussetzungen

* Ein Windows 10 PC, der mit den [richtigen installierten Tools](../../../develop/install-the-tools.md)konfiguriert ist.
* Einige grundlegende C#-Programmierfähigkeiten.
* Sie sollten [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md)abgeschlossen haben.
* Ein HoloLens Gerät, das für die [Entwicklung konfiguriert ist.](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)

### <a name="project-files"></a>Projektdateien

* Laden Sie die [dateien](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) herunter, die für das Projekt erforderlich sind. Erfordert Unity 2017.2 oder höher.
  * Wenn Sie weiterhin Unity 5.6-Unterstützung benötigen, verwenden Sie [dieses Release.](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip) Dieses Release ist möglicherweise nicht mehr auf dem neuesten Stand.
  * Wenn Sie weiterhin Unity 5.5-Unterstützung benötigen, verwenden Sie [dieses Release.](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip) Dieses Release ist möglicherweise nicht mehr auf dem neuesten Stand.
  * Wenn Sie weiterhin Unity 5.4-Unterstützung benötigen, verwenden Sie [dieses Release.](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip) Dieses Release ist möglicherweise nicht mehr auf dem neuesten Stand.
* Aufheben der Archivierung der Dateien auf Ihrem Desktop oder an einem anderen leicht erreichbaren Speicherort.

>[!NOTE]
>Wenn Sie den Quellcode vor dem Herunterladen durchsehen möchten, ist er [auf GitHub verfügbar.](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound)

### <a name="errata-and-notes"></a>Errata und Hinweise

* "Enable Nur eigenen Code" muss in Visual Studio unter Tools->Options->Debugging deaktiviert *(deaktiviert)* werden, um Breakpoints im Code zu erhalten.

## <a name="chapter-1---unity-setup"></a>Kapitel 1: Unity-Setup

### <a name="objectives"></a>Ziele

* Ändern Sie die Soundkonfiguration von Unity so, dass Microsoft Spatial Sound verwendet wird.
* Fügen Sie einem Objekt in Unity 3D-Sound hinzu.

### <a name="instructions"></a>Anweisungen

* Starten Sie Unity.
* Wähle **Öffnen** aus.
* Navigieren Sie zu Ihrem Desktop, und suchen Sie den Ordner, den Sie zuvor nicht archiviert haben.
* Klicken Sie auf den Ordner **Starting\Decibel,** und klicken Sie dann auf die Schaltfläche **Ordner auswählen.**
* Warten Sie, bis das Projekt in Unity geladen wurde.
* Öffnen **Sie** im bereich Project **Scenes\Decibel.unity**.
* Erweitern Sie im **Hierarchiebereich** **HologramCollection,** und wählen Sie **P0LY** aus.
* Erweitern Sie im Inspector den Bereich **AudioSource,** und beachten Sie, dass kein **Kontrollkästchen Spatialize** vorhanden ist.

Standardmäßig lädt Unity kein Spatializer-Plug-In. Mit den folgenden Schritten wird Spatial Sound im Projekt aktiviert.

* Wechseln Sie im oberen Menü von Unity zu **Bearbeiten > Project Einstellungen > Audio**.
* Suchen Sie die Dropdownliste **Spatializer-Plug-In,** und wählen Sie **MS HRTF Spatializer** aus.
* Wählen Sie im **Hierarchiebereich** **HologramCollection > P0LY** aus.
* Suchen Sie im Bereich **Inspector (Inspektor)** nach der Komponente **Audio source (Audioquelle).**
* Aktivieren Sie das **Kontrollkästchen Spatialize** .
* Ziehen Sie den Schieberegler **Spatial Blend** bis hin zu **3D,** oder geben Sie **1** in das Bearbeitungsfeld ein.

Wir erstellen nun das Projekt in Unity und konfigurieren die Projektmappe in Visual Studio.

1. Wählen Sie in Unity **Datei > Build Einstellungen** aus.
2. Klicken Sie auf **Offene Szenen** hinzufügen, um die Szene hinzuzufügen.
3. Wählen Sie in der Liste **Plattform** die Option **Universal Windows Platform** aus, und klicken Sie auf Plattform **wechseln.**
4. Wenn Sie speziell für HoloLens entwickeln, legen **Sie Zielgerät** auf **HoloLens** fest. Andernfalls belassen Sie es auf **Beliebiges Gerät.**
5. Stellen Sie sicher, dass **build type (Buildtyp)** auf **D3D** und **SDK** auf **Latest installed (Neueste Installation)** festgelegt ist (sdk 16299 oder neuer).
6. Klicken Sie auf **Erstellen**.
7. Erstellen Sie einen **neuen Ordner** mit dem Namen "App".
8. Klicken Sie mit nur einem Klick auf den Ordner **App.**
9. Klicken **Sie auf Ordner auswählen.**

Wenn Unity abgeschlossen ist, wird ein Datei-Explorer-Fenster angezeigt.

1. Öffnen Sie den Ordner **App.**
2. Öffnen Sie die **Projektmappe Decibel Visual Studio**.

Bei Bereitstellung in HoloLens:

1. Ändern Sie mithilfe der oberen Symbolleiste in Visual Studio das Ziel von Debuggen in **Release** und von ARM in **x86.**
2. Klicken Sie auf den Dropdownpfeil neben der Schaltfläche Lokaler Computer, und wählen Sie **Remotecomputer** aus.
3. Geben Sie **Ihre HoloLens Geräte-IP-Adresse** ein, und legen Sie den Authentifizierungsmodus auf **Universell (Unverschlüsseltes Protokoll)** fest. Klicken Sie auf **Auswählen**. Wenn Sie Die IP-Adresse Ihres Geräts nicht kennen, suchen Sie in **Einstellungen > Network & Internet > Erweiterte Optionen.**
4. Klicken Sie in der oberen Menüleiste auf **Debuggen -> Ohne Debuggen starten,** oder drücken **Sie STRG+F5.** Wenn dies die erste Bereitstellung auf Ihrem Gerät ist, müssen Sie [es mit Visual Studio koppeln.](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device)

Bei Der Bereitstellung auf einem immersiven Headset:

1. Ändern Sie mithilfe der oberen Symbolleiste in Visual Studio das Ziel von Debuggen in **Release** und von ARM in **x64.**
2. Stellen Sie sicher, dass das Bereitstellungsziel auf **Lokaler Computer** festgelegt ist.
3. Klicken Sie in der oberen Menüleiste auf **Debuggen -> Ohne Debuggen starten,** oder drücken **Sie STRG+F5.**

## <a name="chapter-2---spatial-sound-and-interaction"></a>Kapitel 2: Räumlicher Sound und Interaktion

### <a name="objectives"></a>Ziele

* Verbessern der Hologramm-Realität mithilfe von Sound.
* Leiten Sie das Anvieren des Benutzers mithilfe von Sound.
* Bereitstellen von Gestenfeedback mithilfe von Sound.

### <a name="part-1---enhancing-realism"></a>Teil 1: Verbessern der Realität

#### <a name="key-concepts"></a>Wichtige Konzepte

* Raumbezogene Hologrammsounds.
* Soundquellen sollten an einer geeigneten Position auf dem Hologramm platziert werden.

Die geeignete Position für den Sound hängt vom Hologramm ab. Wenn das Hologramm z. B. ein Mensch ist, sollte sich die Soundquelle in der Nähe der Brille und nicht in der Nähe der Fuße befinden.

#### <a name="instructions"></a>Anweisungen

Mit den folgenden Anweisungen wird ein spatialisierter Sound an ein Hologramm angefügt.

* Erweitern Sie **im Bereich Hierarchie** den Bereich **HologramCollection,** und wählen **Sie P0LY aus.**
* Klicken Sie **im Bereich Inspector** in der **AudioSource** auf den Kreis neben **AudioClip,** und wählen Sie im Popupfenster **PolyHover** aus.
* Klicken Sie auf den Kreis neben **Ausgabe,** und wählen Sie im Popupfenster **SoundEffects** aus.

Project Decbel verwendet eine Unity **AudioMixer-Komponente,** um die Anpassung der Soundebenen für Soundgruppen zu ermöglichen. Durch das Gruppieren von Sounds auf diese Weise kann die Gesamtmenge angepasst werden, während die relative Lautstärke der einzelnen Sounds beibehalten wird.

* Erweitern Sie **in AudioSource** den **3D-Sound Einstellungen**.
* Legen **Sie die Dopplerebene** auf **0 fest.**

Wenn Sie die Doppler-Ebene auf 0 (null) festlegen, werden Änderungen der Tonhöhe deaktiviert, die durch Bewegung (entweder des Hologramms oder des Benutzers) verursacht werden. Ein klassisches Beispiel für Doppler ist ein schnell bewegtes Auto. Wenn sich das Auto einem fest stehenden Listener nähert, steigt die Tonhöhe des Triebwerks. Wenn er den Listener übergibt, wird die Tonhöhe mit der Entfernung nach unten gesenkt.

### <a name="part-2---directing-the-users-gaze"></a>Teil 2: Anvieren des Anvierens des Benutzers

#### <a name="key-concepts"></a>Wichtige Konzepte

* Verwenden Sie Sound, um wichtige Hologramme zu beachten.
* Die Augen helfen dabei, den Ort zu richten, an dem die Augen aussehen sollen.
* Das Gehirn hat einige gelernte Erwartungen.

Ein Beispiel für erlernte Erwartungen ist, dass Dies ist in der Regel über den Kopf von Menschen. Wenn ein Benutzer einen Tönen von einem Tier hören soll, ist die erste Reaktion darauf, nach oben zu suchen. Das Platzieren eines Brillen unterhalb des Benutzers kann dazu führen, dass er die richtige Richtung des Sounds sieht, aber das Hologramm nicht finden kann, basierend auf der Erwartung, dass er nachschauen muss.

#### <a name="instructions"></a>Anweisungen

Die folgenden Anweisungen ermöglichen es P0LY, sich hinter Ihnen auszublenden, damit Sie das Hologramm mit sound suchen können.

* Wählen Sie **im Bereich** Hierarchie die Option **Manager aus.**
* Suchen Sie **im Bereich Inspector** nach Speech Input **Handler**.
* Erweitern Sie **im Spracheingabehandler** den Bereich **Go Hide (Ausblenden).**
* Ändern **Sie No Function** in **PolyActions.GoHide**.

![Schlüsselwort: Ausblenden](images/gohide.png)

### <a name="part-3---gesture-feedback"></a>Teil 3: Gestenfeedback

#### <a name="key-concepts"></a>Wichtige Konzepte

* Bereitstellen einer positiven Gestenbestätigung für den Benutzer mithilfe von Sound
* Benutzer nicht überfordern – zu laute Töne werden im Weg
* Dezente Sounds funktionieren am besten – überschatten Sie die Erfahrung nicht.

#### <a name="instructions"></a>Anweisungen

* Erweitern Sie **im Bereich** Hierarchie den Bereich **HologramCollection.**
* Erweitern **Sie EnergyHub,** und wählen Sie **Basis aus.**
* Klicken Sie im **Bereich Inspector** (Inspektor) auf Add **Component (Komponente** hinzufügen), und fügen **Sie Gesture Sound Handler (Gestensoundhandler) hinzu.**
* Klicken **Sie im Gestenklanghandler** auf den Kreis neben **Navigation Gestartet** Clip und Navigation Updated **Clip,** und wählen **Sie rotateClick** aus dem Popupfenster für beide aus.
* Doppelklicken Sie auf "GestureSoundHandler", um die Visual Studio.

Der Gestenklanghandler führt die folgenden Aufgaben aus:

* Erstellen und konfigurieren Sie eine **AudioSource.**
* Platzieren Sie **AudioSource** am Speicherort des entsprechenden **GameObject.**
* Gibt den **AudioClip wieder,** der der Geste zugeordnet ist.

#### <a name="build-and-deploy"></a>Erstellen und Bereitstellen

1. Wählen Sie in Unity **Datei > Build Einstellungen.**
2. Klicken Sie auf **Erstellen**.
3. Klicken Sie mit nur einem Klick **auf den Ordner App.**
4. Klicken Sie **auf Ordner auswählen.**

Überprüfen Sie, ob auf der Symbolleiste "Release", "x86" oder "x64" und "Remotegerät" angezeigt werden. Wenn dies nicht der Fall ist, ist dies die Codierungsinstanz Visual Studio. Möglicherweise müssen Sie die Projektmappe über den Ordner App erneut öffnen.

* Laden Sie die Projektdateien erneut, wenn Sie dazu aufgefordert werden.
* Stellen Sie wie zuvor eine Bereitstellung über Visual Studio.

Nach der Bereitstellung der Anwendung:

* Beobachten Sie, wie sich der Sound ändert, während Sie P0LY bewegen.
* Sagen *Sie "Go Hide",* um P0LY an einen Speicherort hinter Ihnen zu verschieben. Suchen Sie nach dem Sound.
* Sehen Sie sich die Basis des Energy Hubs an. Tippen und ziehen Sie nach links oder rechts, um das Hologramm zu drehen, und sehen Sie, wie der klickende Sound die Geste bestätigt.

Hinweis: Es gibt einen Textbereich, der zusammen mit Ihnen tagt. Dies enthält die verfügbaren Sprachbefehle, die Sie in diesem Kurs verwenden können.

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a>Kapitel 3: Raumklang und räumliche Zuordnung

### <a name="objectives"></a>Ziele

* Bestätigen Sie die Interaktion zwischen Hologrammen und der realen Welt mithilfe von Sound.
* Verdecken Sie Sound mithilfe der physischen Welt.

### <a name="part-1---physical-world-interaction"></a>Teil 1: Physische Weltinteraktion

#### <a name="key-concepts"></a>Wichtige Konzepte

* Physische Objekte machen in der Regel einen Sound, wenn sie auf eine Oberfläche oder ein anderes Objekt stoßen.
* Sounds sollten innerhalb der Erfahrung kontextgerecht sein.

Beispielsweise sollte das Festlegen eines Bechers auf einer Tabelle einen stilleren Sound als das Ablegen einer Tafel auf einem Stück Metal machen.

#### <a name="instructions"></a>Anweisungen

* Erweitern Sie **im Bereich** Hierarchie den Bereich **HologramCollection.**
* Erweitern **Sie EnergyHub,** und wählen Sie **Basis aus.**
* Klicken Sie im **Bereich Inspector** (Inspektor) auf Add Component (Komponente **hinzufügen),** und fügen **Sie Tap To Place With Sound (Mit Sound platzieren) und Action (Aktion) hinzu.**
* Tippen Sie auf To Place With Sound and Action (Tippen Auf **Platzieren mit Sound und Aktion):**
  * Aktivieren **Sie Übergeordnetes Element auf tippen.**
  * Legen Sie **Placement Sound auf** Place **fest.**
  * Legen Sie **Pickup Sound auf** Pickup **fest.**
  * Drücken Sie unten rechts unter On **Pickup Action (Aktion zur Abholung)** und **On Placement Action (Bei Platzierungsaktion) die Taste +.** Ziehen Sie EnergyHub aus der Szene in **die Felder None (Object) (Keine (Objekt)).**
    * Klicken **Sie unter On Pickup Action**(Aktion zur Abholung) auf No Function EnergyHubBase ResetAnimation (Keine **Funktion**  ->  **EnergyHubBase**  ->  **ResetAnimation).**
    * Klicken **Sie unter On Placement Action**(Bei Platzierungsaktion) auf No Function EnergyHubBase OnSelect (No **Function**  ->  **EnergyHubBase**  ->  **OnSelect).**

![Tippen Sie auf To Place with Sound and Action (Mit Sound und Aktion platzieren)](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a>Teil 2: Okklusion von Sound

#### <a name="key-concepts"></a>Wichtige Konzepte

* Sound kann, wie licht, verblendet werden.

Ein klassisches Beispiel ist eine Concert Hall. Wenn ein Listener außerhalb der Hall steht und die Tür geschlossen ist, klingt die Musik gemischt. In der Regel kommt es auch zu einer Verringerung des Volumens. Wenn die Tür geöffnet wird, wird das gesamte Spektrum des Sounds auf der tatsächlichen Lautstärke gehört. Töne mit hoher Frequenz werden in der Regel häufiger als niedrige Frequenzen aufgenommen.

#### <a name="instructions"></a>Anweisungen

* Erweitern Sie **im Bereich Hierarchie** den Bereich **HologramCollection,** und wählen **Sie P0LY aus.**
* Klicken Sie im **Bereich Inspector** (Inspektor) auf **Add Component** (Komponente hinzufügen), und fügen Sie Audio **Emitter (Audioemitter) hinzu.**

Die Audio Emitter-Klasse bietet die folgenden Features:

* Stellt alle Änderungen am Volume von **AudioSource wieder auf.**
* Führt **ein Physics.RaycastNonAlloc-Objekt** aus der Position des Benutzers in Richtung des **GameObject** aus, an das **der AudioEmitter** angefügt ist.

Die RaycastNonAlloc-Methode wird als Leistungsoptimierung verwendet, um Zuordnungen sowie die Anzahl der zurückgegebenen Ergebnisse zu begrenzen.

* Ruft für jeden **gefundenen IAudioInfluencer** die **ApplyEffect-Methode** auf.
* Rufen Sie für jeden vorherigen **IAudioInfluencer,** der nicht mehr gefunden wird, die **RemoveEffect-Methode** auf.

Beachten Sie, dass AudioEmitter-Updates auf menschlichen Zeitskalen und nicht pro Frame aktualisiert werden. Dies geschieht, da Menschen sich im Allgemeinen nicht schnell genug bewegen, damit der Effekt häufiger als jede Quartals- oder Halb sekunde aktualisiert werden muss. Hologramme, dass die Teleports schnell von einem Standort an einen anderen übertragen werden, kann dies die Vorstellungen unterbrechen.

* Erweitern **Sie** im Bereich Hierarchie den Bereich **HologramCollection**.
* Erweitern Sie **EnergyHub,** und wählen Sie **BlobOutside aus.**
* Klicken Sie im Bereich **Inspector (Inspektor)** auf **Add Component (Komponente hinzufügen),** und fügen Sie **Audio Occluder (Audio occluder)** hinzu.
* Legen Sie **in Audio Occluder** die **Cutoff Frequency** auf **1500** fest.

Durch diese Einstellung werden die AudioSource-Frequenzen auf 1.500 Hz und darunter beschränkt.

* Legen Sie **Volume Pass Through** auf **0,9** fest.

Diese Einstellung reduziert die Lautstärke der AudioSource auf 90 % ihrer aktuellen Ebene.

Audio Occluder implementiert IAudioInfluencer für:

* Wenden Sie einen Verdeckungseffekt mit einem **AudioLowPassFilter** an, der an die verwaltete **AudioSource** angefügt wird, und kaufen Sie den **AudioEmitter**.
* Wendet volume attenuation auf die AudioSource an.
* Deaktiviert den Effekt, indem eine neutrale Cutoffhäufigkeit festgelegt und der Filter deaktiviert wird.

Die als neutral verwendete Frequenz beträgt 22 kHz (22.000 Hz). Diese Frequenz wurde ausgewählt, da sie über der nominalen maximalen Frequenz liegt, die vom menschlichen Hörhören gehört werden kann. Dies hat keine erkennbaren Auswirkungen auf den Sound.

* Wählen Sie im **Bereich Hierarchie** die Option **SpatialMapping** aus.
* Klicken Sie im Bereich **Inspector (Inspektor)** auf **Add Component (Komponente hinzufügen),** und fügen Sie **Audio Occluder (Audio occluder)** hinzu.
* Legen Sie **in Audio Occluder** die **Cutoff Frequency** auf **750** fest.

Wenn sich mehrere Verdeckungen im Pfad zwischen dem Benutzer und dem **AudioEmitter** befinden, wird die niedrigste Häufigkeit auf den Filter angewendet.

* Legen Sie **Volume Pass Through** auf **0,75** fest.

Wenn sich mehrere Verdeckungen im Pfad zwischen dem Benutzer und dem **AudioEmitter** befinden, wird die Volumeübergabe additiv angewendet.

* Wählen Sie im **Bereich Hierarchie** die Option **Manager** aus.
* Erweitern Sie im Bereich **Inspector (Inspektor)** die Erweiterung **Speech Input Handler (Spracheingabehandler).**
* Erweitern Sie unter **Spracheingabehandler** den Eintrag **Go Charge**.
* Ändern Sie **No Function** in **PolyActions.GoCharge**.

![Schlüsselwort: Go Charge](images/gocharge.png)

* Erweitern **Sie Hier kommen.**
* Ändern Sie **No Function** in **PolyActions.ComeBack**.

![Schlüsselwort: Come Here](images/comehere.png)

#### <a name="build-and-deploy"></a>Erstellen und Bereitstellen

* Erstellen Sie wie zuvor das Projekt in Unity, und stellen Sie es in Visual Studio bereit.

Nach der Bereitstellung der Anwendung:

* Sagen Sie *"Go Charge",* damit P0LY in den Energy Hub eintritt.

Beachten Sie die Änderung im Sound. Es sollte muffig und etwas stiller klingen. Wenn Sie sich mit einer Wand oder einem anderen Objekt zwischen Ihnen und dem Energy Hub positionieren können, sollten Sie aufgrund der Verdeckung durch die reale Welt eine weitere Muffling des Sounds bemerken.

* Sagen *Sie "Come Here",* damit P0LY den Energy Hub verlässt und sich vor Ihnen positioniert.

Beachten Sie, dass die Soundverdeckung entfernt wird, sobald P0LY den Energy Hub verlässt. Wenn Sie immer noch Verdeckung hören, kann P0LY von der realen Welt verdeckt werden. Versuchen Sie, zu verschieben, um sicherzustellen, dass Sie eine klare Sichtlinie zu P0LY haben.

### <a name="part-3---room-models"></a>Teil 3: Raummodelle

#### <a name="key-concepts"></a>Wichtige Konzepte

* Die Größe des Speicherplatzes stellt unterschwellige Warteschlangen bereit, die zur soundlokalen Lokalisierung beitragen.
* Raummodelle werden pro **AudioSource** festgelegt.
* Das [MixedRealityToolkit für Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) stellt Code zum Festlegen des Raummodells bereit.
* Wählen Sie für Mixed Reality Erfahrungen das Raummodell aus, das am besten zum realen Raum passt.

Wenn Sie ein Virtual Reality-Szenario erstellen, wählen Sie das Raummodell aus, das am besten zur virtuellen Umgebung passt.

## <a name="chapter-4---sound-design"></a>Kapitel 4: Sounddesign

### <a name="objectives"></a>Ziele

* Grundlegendes zu Überlegungen für einen effektiven Soundentwurf.
* Lernen Sie das Kombinieren von Techniken und Richtlinien kennen.

### <a name="part-1---sound-and-experience-design"></a>Teil 1: Design von Sound und Erfahrung

In diesem Abschnitt werden wichtige Überlegungen und Richtlinien zum Design von Sound und Erfahrung erläutert.

#### <a name="normalize-all-sounds"></a>Normalisieren aller Sounds

Dies vermeidet die Notwendigkeit von Sonderfallcode zum Anpassen der Lautstärkestufen pro Sound, was zeitaufwändig sein kann und die Möglichkeit zum einfachen Aktualisieren von Sounddateien einschränkt.

#### <a name="design-for-an-untethered-experience"></a>Entwurf für eine nicht weiter ergänzte Benutzeroberfläche

HoloLens ist ein vollständig eigenständiger holografischer Computer. Ihre Benutzer können und werden Ihre Erfahrungen während der Bewegung nutzen. Stellen Sie sicher, dass Sie Ihre Audiomischung testen, indem Sie durchgehen.

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a>Ausgeben von Sound von logischen Positionen auf Ihren Hologrammen

In der realen Welt schweift ein Hund nicht von seinem Ende ab, und die Stimme eines Menschen kommt nicht von seinen Beinen. Vermeiden Sie, dass Ihre Sounds von unerwarteten Teilen Ihrer Hologramme ausgeben.

Bei kleinen Hologrammen ist es sinnvoll, eine Tondaten aus der Mitte der Geometrie auszugeben.

#### <a name="familiar-sounds-are-most-localizable"></a>Vertraute Sounds sind am lokalisierbarsten

Menschliche Stimme und Musik lassen sich sehr einfach lokalisieren. Wenn jemand Ihren Namen aufruft, können Sie sehr genau bestimmen, aus welcher Richtung die Stimme stammt und wie weit sie entfernt ist. Kurze, unbekannte Sounds sind schwieriger zu lokalisieren.

#### <a name="be-cognizant-of-user-expectations"></a>Die Erwartungen der Benutzer erfüllen

Die Lebenserfahrung spielt eine Rolle bei unserer Fähigkeit, die Position eines Sounds zu identifizieren. Dies ist ein Grund, warum die menschliche Stimme besonders einfach zu lokalisieren ist. Es ist wichtig, dass Sie sich der erlernten Erwartungen Ihrer Benutzer bewusst sein, wenn Sie Ihre Sounds platzieren.

Wenn jemand z. B. ein Vogellied hören kann, sieht er in der Regel nach oben, da Sichten in der Regel über der Sichtlinie (Luft oder in einem Baum) befinden. Es ist nicht ungewöhnlich, dass sich ein Benutzer in die richtige Richtung eines Sounds bewegt, aber in der falschen vertikalen Richtung sucht und verwirren oder frustriert wird, wenn er das Hologramm nicht finden kann.

#### <a name="avoid-hidden-emitters"></a>Vermeiden von ausgeblendeten Emittern

In der realen Welt können wir, wenn wir einen Sound hören, im Allgemeinen das Objekt identifizieren, das den Sound aussendet. Dies sollte auch in Ihren Erfahrungen zutreffen. Es kann sehr verwirrend sein, dass Benutzer einen Sound hören, wissen, woher der Sound stammt und ein Objekt nicht sehen kann.

Es gibt einige Ausnahmen für diese Richtlinie. Umgebungsgeräusche wie z. B. Blenden in einem Feld müssen beispielsweise nicht sichtbar sein. Die Erfahrung im Leben vermittelt uns Vertrautheit mit der Quelle dieser Sounds, ohne sie sehen zu müssen.

### <a name="part-2---sound-mixing"></a>Teil 2: Mischen von Sound

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a>Richten Sie Ihre Mischung auf 70 % Volume auf der HoloLens

Mixed Reality Können Hologramme in der realen Welt sichtbar sein. Sie sollten auch das Hören von echten Sounds ermöglichen. Ein Volumenziel von 70 % ermöglicht es dem Benutzer, die Welt um sie herum zusammen mit dem Sound Ihrer Erfahrung zu hören.

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a>HoloLens bei einer Lautstärke von 100 % sollten externe Sounds überlaufen.

Ein Volumen von 100 % ähnelt einer Virtual Reality-Umgebung. Visuell wird der Benutzer in eine andere Welt versetzt. Dies sollte auch hörbar sein.

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a>Verwenden von Unity AudioMixer zum Anpassen von Soundkategorien

Beim Entwerfen Ihrer Mischung ist es oft hilfreich, Soundkategorien zu erstellen und die Möglichkeit zu haben, ihre Lautstärke als Einheit zu erhöhen oder zu verringern. Dies behält die relativen Ebenen jedes Sounds bei und ermöglicht gleichzeitig schnelle und einfache Änderungen an der Gesamtmischung. Allgemeine Kategorien sind: Soundeffekte, Stimmung, Voice overs und Hintergrund musik.

#### <a name="mix-sounds-based-on-the-users-gaze"></a>Mischen von Sounds basierend auf dem Anvischen des Benutzers

Es kann häufig hilfreich sein, die Soundmischung in Ihrer Benutzeroberfläche zu ändern, je nach dem Ort, an dem ein Benutzer sucht (oder nicht). Eine häufige Verwendung dieses Verfahrens besteht darin, die Lautstärke für Hologramme zu reduzieren, die sich außerhalb des Holographic Frame befinden, um es dem Benutzer zu erleichtern, sich auf die ihm vorgeschalteten Informationen zu konzentrieren. Eine weitere Verwendung besteht darin, die Lautstärke eines Sounds zu erhöhen, um die Aufmerksamkeit des Benutzers auf ein wichtiges Ereignis zu lenken.

#### <a name="building-your-mix"></a>Erstellen Ihrer Mischung

Wenn Sie Ihre Mischung erstellen, empfiehlt es sich, mit dem Hintergrundaudio Ihrer Erfahrung zu beginnen und Basierend auf der Wichtigkeit Ebenen hinzuzufügen. Häufig führt dies dazu, dass jede Ebene lauter als die vorherige ist.

Wenn Sie sich Ihre Mischung als invertierten Trichter mit den am wenigsten wichtigen (und im Allgemeinen stillsten) Sounds am unteren Rand vorstellen, empfiehlt es sich, ihre Mischung ähnlich wie im folgenden Diagramm zu strukturieren.

![Struktur der Soundmischung](images/soundlevels.png)

Voice overs sind ein interessantes Szenario. Basierend auf der Benutzeroberfläche, die Sie erstellen, möchten Sie möglicherweise einen Stereoton (nicht lokalisiert) haben oder Ihre Stimme verräumlichen. Zwei von Microsoft veröffentlichte Erfahrungen veranschaulichen hervorragende Beispiele für jedes Szenario.

[HoloTour](https://www.microsoft.com/store/p/holotour/9nblggh5pj87) verwendet eine Stereostimme. Wenn die Sprachausgabe den angezeigten Standort beschreibt, ist der Sound konsistent und variiert nicht basierend auf der Position des Benutzers. Dies ermöglicht es der Sprachausgabe, die Szene zu beschreiben, ohne die räumlichen Sounds der Umgebung zu wegzunehmen.

[Fragmente](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) verwenden eine räumliche Stimme in Form eines Detectives. Die Stimme des Detectives wird verwendet, um die Aufmerksamkeit des Benutzers auf einen wichtigen Hinweis zu lenken, als befinde sich ein tatsächlicher Mensch im Raum. Dies ermöglicht einen noch besseren Einblick in die Erfahrung des Lösens der Therde.

### <a name="part-3--performance"></a>Teil 3 : Leistung

#### <a name="cpu-usage"></a>CPU-Auslastung

Bei Verwendung von Spatial Sound verbrauchen 10 bis 12 Emitter ungefähr 12 % der CPU.

#### <a name="stream-long-audio-files"></a>Lange Audiodateien streamen

Audiodaten können groß sein, insbesondere bei allgemeinen Abtastraten (44,1 und 48 kHz). Eine allgemeine Regel ist, dass Audiodateien, die länger als 5 bis 10 Sekunden sind, gestreamt werden sollten, um die Auslastung des Anwendungsspeichers zu reduzieren.

In Unity können Sie eine Audiodatei für das Streaming in den Importeinstellungen der Datei markieren.

![Einstellungen für den Audioimport](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a>Kapitel 5: Sondereffekte

### <a name="objectives"></a>Ziele

* Fügen Sie "Magic Windows" Tiefe hinzu.
* Bringen Sie den Benutzer in die virtuelle Welt ein.

### <a name="magic-windows"></a>Magic Windows

#### <a name="key-concepts"></a>Wichtige Konzepte

* Das Erstellen von Ansichten in einer verborgenen Welt ist visuell überzeugend.
* Verbessern Sie die Realität, indem Sie Audioeffekte hinzufügen, wenn sich ein Hologramm oder der Benutzer in der Nähe der verborgenen Welt befindet.

#### <a name="instructions"></a>Anweisungen

* Erweitern Sie im **Hierarchiebereich** **HologramCollection,** und wählen Sie **Underworld** aus.
* Erweitern Sie **Underworld,** und wählen Sie **VoiceSource aus.**
* Klicken Sie im Bereich **Inspector** auf **Add Component (Komponente hinzufügen),** und fügen Sie **User Voice Effect (Benutzerstimmeneffekt)** hinzu.

**VoiceSource** wird eine **AudioSource-Komponente** hinzugefügt.

* Legen Sie in **AudioSource** **die Ausgabe** auf **UserVoice (Mixer)** fest.
* Aktivieren Sie das **Kontrollkästchen Spatialize** .
* Ziehen Sie den Schieberegler **Spatial Blend** bis hin zu **3D,** oder geben Sie **1** in das Bearbeitungsfeld ein.
* Erweitern Sie **3D-Sound Einstellungen**.
* Legen Sie **doppler level** auf **0** fest.
* Legen Sie unter **User Voice Effect (Benutzerstimmeneffekt)** **das übergeordnete Objekt** auf **underworld** aus der Szene fest.
* Legen Sie **Max Distance (Maximaler Abstand)** auf **1** fest.

Durch Festlegen der **maximalen Entfernung** wird **dem Benutzerstimmeneffekt** mitgeteilt, wie nah der Benutzer am übergeordneten Objekt sein muss, bevor der Effekt aktiviert wird.

* Erweitern Sie unter **User Voice Effect (Benutzerstimmeneffekt)** den Parameter **Chorus**.
* Legen Sie **Tiefe** auf **0,1** fest.
* Legen **Sie Tippen Sie auf 1 Volume,** **tippen Sie auf 2 Volume** und tippen Sie auf **3 Volume** auf **0,8**.
* Legen Sie **Original Sound Volume** auf **0,5** fest.

Mit den vorherigen Einstellungen werden die Parameter von Unity **AudioChorusFilter** konfiguriert, die verwendet werden, um der Stimme des Benutzers einen Mehrwert zu verleihen.

* Erweitern Sie unter **User Voice Effect (Benutzerstimmeneffekt)** die Erweiterung **Echoparameter**.
* Legen Sie **Delay** auf **300 fest.**
* Legen Sie **Decay Ratio (Verfallsverhältnis)** auf **0,2** fest.
* Legen Sie **Original Sound Volume** auf **0** fest.

Mit den vorherigen Einstellungen werden die Parameter von Unity **AudioEchoFilter** konfiguriert, mit deren Hilfe die Stimme des Benutzers wiederholt wird.

Das User Voice Effect-Skript ist für Folgendes verantwortlich:

* Messen des Abstands zwischen dem Benutzer und dem **GameObject,** an das das Skript angefügt ist.
* Bestimmen, ob der Benutzer mit dem **GameObject**-Objekt konfrontiert ist oder nicht.

Der Benutzer muss unabhängig von der Entfernung mit dem GameObject konfrontiert sein, damit der Effekt aktiviert wird.

* Anwenden und Konfigurieren eines **AudioChorusFilter** und eines **AudioEchoFilter** auf die **AudioSource**.
* Deaktivieren des Effekts durch Deaktivieren der Filter.

User Voice Effect verwendet die Mic Stream Selector-Komponente aus dem [MixedRealityToolkit für Unity,](https://github.com/Microsoft/MixedRealityToolkit-Unity)um den qualitativ hochwertigen Sprachstream auszuwählen und an das Audiosystem von Unity weiterzuleiten.

* Wählen Sie im **Bereich Hierarchie** die Option **Manager** aus.
* Erweitern Sie im Bereich **Inspector (Inspektor)** die Erweiterung **Speech Input Handler (Spracheingabehandler).**
* Erweitern Sie unter **Spracheingabehandler** den Eintrag **Unterwelt anzeigen.**
* Ändern Sie **No Function** in **UnderworldBase.OnEnable**.

![Schlüsselwort: Unterwelt anzeigen](images/showunderworld.png)

* Erweitern Sie **Unterwelt ausblenden.**
* Ändern Sie **No Function** in **UnderworldBase.OnDisable**.

![Schlüsselwort: Underworld ausblenden](images/hideunderworld.png)

#### <a name="build-and-deploy"></a>Erstellen und Bereitstellen

* Erstellen Sie wie zuvor das Projekt in Unity, und stellen Sie es in Visual Studio bereit.

Nach der Bereitstellung der Anwendung:

* Stellen Sie sich einer Oberfläche (Wand, Boden, Tabelle) gegenüber, und sagen *Sie "Show Underworld" (Unterwelt anzeigen).*

Die Unterwelt wird angezeigt, und alle anderen Hologramme werden ausgeblendet. Wenn die Unterwelt nicht angezeigt wird, stellen Sie sicher, dass Sie mit einer realen Oberfläche konfrontiert sind.

* Nähern Sie sich innerhalb eines Meters des Unterwelt hologramms, und beginnen Sie mit der Unterhaltung.

Es gibt jetzt Audioeffekte, die auf Ihre Stimme angewendet werden!

* Wenden Sie sich von der Unterwelt ab, und beachten Sie, dass der Effekt nicht mehr angewendet wird.
* Sagen *Sie "Underworld ausblenden",* um die Unterwelt auszublenden.

Die Unterwelt wird ausgeblendet, und die zuvor ausgeblendeten Hologramme werden wieder angezeigt.

## <a name="the-end"></a>Das Ende

Herzlichen Glückwunsch! Sie haben mr **spatial 220: Spatial sound (MR Spatial 220: Räumlicher Sound)** abgeschlossen.

Hören Sie auf die Welt, und bringen Sie Ihre Erfahrungen mit Sound zum Leben!