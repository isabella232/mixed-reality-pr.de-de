---
title: Von openxr-Plug-in unterstützte Funktionen in Unity
description: Entdecken Sie die Features, die openxr für die Entwicklung gemischter Realität in Unity unterstützt.
author: hferrone
ms.author: alexturn
ms.date: 12/15/2020
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, Mixed Reality, mrtk, Mixed Reality Toolkit, Augmented Reality, Virtual Reality, Mixed Reality-Headsets, erlernen, Tutorial, Getting Started
ms.openlocfilehash: 1cbe9dd1ffb493bcc9da76e70dec9720f2d10340
ms.sourcegitcommit: 4bbf2f802117a9a3788b2b0e3b0a2f58e187f6ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2020
ms.locfileid: "97665358"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a>Gemischte Funktionen von openxr unterstützten Funktionen in Unity

Das **gemischte openxr-Plug** -in für die Realität ist eine Erweiterung des Unity **openxr-Plug** -ins und unterstützt eine Reihe von Features für hololens 2-und Windows Mixed Reality-Headsets. Bevor Sie fortfahren, stellen Sie sicher, dass Sie **Unity 2020,2** oder höher, **openxr Plugin, Version 0.1.1** oder höher, installiert haben und Ihr Unity-Projekt [für openxr konfiguriert](openxr-getting-started.md)ist.

## <a name="whats-supported"></a>Unterstützte Funktionen

Die folgenden Funktionen werden derzeit unterstützt:

* Unterstützt sowohl UWP-Anwendungen für hololens 2-als auch Win32-VR-Anwendungen für Windows Mixed Reality-Headsets.
* Optimiert das UWP-Paket und die corewindow-Interaktion für hololens 2-Anwendungen.
* Welt weite Nachverfolgung mithilfe von Ankern und unbeschränktes Raum.
* [Anker-Speicher-API zum Beibehalten von Ankern](#anchors-and-anchor-persistence) an hololens 2 lokalen Speicher.
* [Motion Controller und Hand Interaktionen](#motion-controller-and-hand-interactions), einschließlich des neuen HP-Reverb-G2-Controllers.
* Handgelenk Verfolgung mithilfe von 26 Gelenken und gemeinsamen RADIUS-Eingaben.
* Interaktion mit Blick auf hololens 2.
* Auffinden von Foto/Video-Kamera (PV) auf hololens 2.
* Transformation für gemischte Realität mithilfe von Dritt-Rendering durch PV-Kamera.
* Unterstützt ["Play" in hololens 2 mit der Holographic Remoting-App](#holographic-remoting-in-unity-editor-play-mode), sodass Entwickler Skripts debuggen können, ohne auf dem Gerät zu entwickeln und bereitzustellen.
* Kompatibel mit mrtk Unity 2.5.2 durch mrtk openxr-Adapter Paket. <missing link>
* Kompatibel mit Unity [arfoundation 4,0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) oder höher

## <a name="holographic-remoting-in-unity-editor-play-mode"></a>Holographic-Remoting im Unity-Editor-Wiedergabemodus

Das Erstellen eines UWP Unity-Projekts in Visual Studio Project und das anschließende Verpacken und Bereitstellen des Projekts auf einem hololens 2-Gerät kann einige Zeit in Anspruch nehmen. Eine Lösung besteht darin, den Holographic Editor-Remoting zu aktivieren, mit dem Sie Ihr c#-Skript mit dem Modus "Wiedergabe" direkt auf ein hololens 2-Gerät über Ihr Netzwerk Debuggen können. In diesem Szenario wird der Aufwand für das entwickeln und Bereitstellen eines UWP-Pakets auf dem Remote Gerät vermieden.

1. Zunächst müssen Sie [die Holographic Remoting Player-App aus dem](https://www.microsoft.com/store/productId/9NBLGGH4SV40) Store auf Ihren hololens 2 installieren.  
2. Führen Sie die Holographic Remoting Player-App auf hololens 2 aus, und Sie sehen die Versionsnummer und IP-Adresse, mit der Sie eine Verbindung herstellen.
    * Sie benötigen v 2.4 oder höher, um mit dem openxr-Plug-in zu arbeiten.

![Screenshot des Holographic-Remoting-Players, der in den hololens ausgeführt wird](images/openxr-features-img-01.png)

3. Öffnen Sie die **Projekteinstellungen für die > bearbeiten**, navigieren Sie zu der **XR-Plug-in-Verwaltung**, und aktivieren Sie das Kontrollkästchen **Windows Mixed Reality Feature Set** :

![Screenshot des Bereichs "Projekteinstellungen" im Unity-Editor mit hervorgehobener XR-Plug-in-Verwaltung](images/openxr-features-img-02.png)

4. Erweitern Sie unter **openxr** den Abschnitt **Features** , und wählen Sie **Alle anzeigen** aus.
5. Aktivieren Sie das Kontrollkästchen "Remoting" für das **Holographic Editor** , und geben Sie die IP-Adresse ein, die Sie aus der Holographic Remoting

![Screenshot des Bereichs "Projekteinstellungen" im Unity-Editor mit hervorgehobenen Features](images/openxr-features-img-03.png)

Nun können Sie auf die Schaltfläche "Wiedergabe" klicken, um Ihre Unity-app in der Holographic Remoting-App auf Ihren hololens wiederzugeben. Sie können auch [Visual Studio an Unity anfügen](https://docs.microsoft.com/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) , um c#-Skripts im Wiedergabemodus zu debuggen.

> [!NOTE]
> Ab Version 0.1.0 das Holographic-Remoting und die Common Language Runtime unterstützt keine Anker Funktion, und aranchormanager-Funktionen können nicht durch Remoting verwendet werden.  Diese Funktion wird in zukünftigen Versionen veröffentlicht.

## <a name="anchors-and-anchor-persistence"></a>Anker und Anker Persistenz

Das Mixed Reality openxr-Plug-in stellt grundlegende Anker Funktionen durch eine Implementierung von Unity **aranchormanager** bereit. Informationen zu den Grundlagen von **aranchor** s in arfoundation finden Sie unter [arfoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html). Ab Version 0.1.0 unterstützt dieses Plug-in alle aranchormanager-Funktionen außer der Erstellung von Ankern, die mit einer Ebene verbunden sind, die in einer zukünftigen Version verfügbar ist.

### <a name="anchor-persistence-and-the-xranchorstore"></a>Anker Persistenz und xranchorstore

Eine zusätzliche API mit dem Namen " **xranchorstore** " ermöglicht, dass Anker zwischen Sitzungen beibehalten werden. Der xranchorstore ist eine Darstellung der gespeicherten Anker auf Ihrem Gerät. Anker können von **aranchor** in der Unity-Szene persistent gespeichert, aus dem Speicher in neue **aranchor** geladen oder aus dem Speicher gelöscht werden.

> [!NOTE]
> Diese Anker müssen auf demselben Gerät gespeichert und geladen werden. Der Geräte übergreifende Anker Speicher wird in einer zukünftigen Version durch Azure Spatial Anchor unterstützt.

``` cs
public class Microsoft.MixedReality.ARSubsystems.XRAnchorStore
{
    // A list of all persisted anchors, which can be loaded.
    public IReadOnlyList<string> PersistedAnchorNames { get; }

    // Clear all persisted anchors
    public void Clear();

    // Load a single persisted anchor by name. The ARAnchorManager will create this new anchor and report it in
    // the ARAnchorManager.anchorsChanged event. The TrackableId returned here is the same TrackableId the 
    // ARAnchor will have when it is instantiated.
    public TrackableId LoadAnchor(string name);

    // Attempts to persist an existing ARAnchor with the given TrackableId to the local store. Returns true if 
    // the storage is successful, false otherwise.
    public bool TryPersistAnchor(string name, TrackableId trackableId);

    // Removes a single persisted anchor from the anchor store. This will not affect any ARAnchors in the Unity
    // scene, only the anchors in storage.
    public void UnpersistAnchor(string name);
}
```

Zum Laden von xranchorstore stellt das Plug-in eine Erweiterungsmethode für das xranchorsubsystem bereit, das Subsystem von aranchormanager:

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

Um diese Erweiterungsmethode zu verwenden, greifen Sie über das Subsystem von aranchormanager wie folgt auf Sie zu:
 
``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>(); 
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync(); 
```

Ein vollständiges Beispiel für das beibehalten/beibehalten von Ankern finden Sie unter Anker-> Anker Sample gameobject und AnchorsSample.cs Script in the [Mixed Reality openxr Plugin Sample Scene](openxr-getting-started.md#hololens-2-samples):

![Screenshot des Bereichs "Hierarchie" im Unity-Editor mit hervorgehobenem Anker Beispiel](images/openxr-features-img-04.png)

![Screenshot des Bereichs "Inspector" im Unity-Editor mit hervorgehobenem Anker Beispielskript](images/openxr-features-img-05.png)

## <a name="motion-controller-and-hand-interactions"></a>Bewegungs Controller und Hand Interaktionen

Informationen zu den Grundlagen von Mixed Reality-Interaktionen in Unity finden Sie in der [Unity-Anleitung für](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html)Unity. In dieser Unity-Dokumentation werden die Zuordnungen von Controller spezifischen Eingaben zu stärker verallgemeinerbaren **inputfeatureusage** s behandelt, und es wird erläutert, wie verfügbare XR-Eingaben identifiziert und kategorisiert werden können, wie Daten aus diesen Eingaben gelesen werden und vieles mehr. 
 
Das Mixed Reality openxr-Plug-in bietet zusätzliche Eingabe Interaktions Profile, die Standard **inputfeatureusage** s zugeordnet sind, wie im folgenden beschrieben: 
 
| Input featureusage | HP-Reverb-G2-Controller (openxr) | Hololens-Hand (openxr) |
| ---- | ---- | ---- |
| primary2DAxis | Steuern | |
| primary2DAxisClick | Joystick Klick | |
| Trigger (trigger) | Trigger  | |
| Hand | Hand | Luft tippen oder drücken |
| primarybutton | [X/A]-drücken | In die Luft tippen |
| secondarybutton | [J/B]-drücken | |
| gripbutton | Ziehpunkt-drücken | |
| Triggerbutton | Auslösung: Drücken Sie | |
| -menubutton- | Menü | |

### <a name="aim-and-grip-poses"></a>Ziele und Zieh Punkt

Sie haben Zugriff auf zwei Gruppen von Posen durch openxr-Eingabe Interaktionen: 
* Der Ziehpunkt für das Rendern von Objekten in der Hand.
* Das Ziel für den Verweis auf die Welt. 

Weitere Informationen zu diesem Entwurf und den Unterschieden zwischen den beiden Posen finden Sie in den [unter Pfaden für openxr Specification-Input](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).

Die von den inputfeatureages **deviceposition**, **devicerotations**, **de vicevelocity** und **deviceangularvelocity** bereitgestellten Posen stellen die openxr-Zieh Punkt **Darstellung dar.** Inputfeatureverwendungen im Zusammenhang mit Ziehpunkt-Posen werden in Unity- [Common-Ages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)definiert.

Die von der Eingabe **Funktion "pointerposition**", " **pointerrotation**", " **pointervelocity**" und " **pointerangularvelocity** " bereitgestellten Posen stellen das openxr- **Ziel** dar. Diese inputfeatureusages sind nicht in enthaltenen c#-Dateien definiert, daher müssen Sie Ihre eigene inputfeatureusages wie folgt definieren:

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a>Haptik

Informationen zur Verwendung von Haptik im XR-Eingabe System von Unity finden Sie im [Unity-Handbuch für Unity-Eingabe-und-Haptik](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics). 

## <a name="whats-coming-soon"></a>Bald verfügbar

Die folgenden Probleme und fehlenden Features sind mit der **Version 0.1.0** des openxr-Plug-ins von Mixed Reality bekannt. Wir arbeiten an diesen und veröffentlichen Korrekturen und neue Features in zukünftigen Versionen.

* **Arplanesubsystem** wird noch nicht unterstützt. **Arplanemanager**, **arraycastmanager** und verwandte APIs wie **aranchormanager. attachanchor** werden auf hololens 2 ebenfalls nicht unterstützt.
* **Anker** wird noch nicht von Holographic Remoting unterstützt, wird jedoch in naher Zukunft angezeigt.
* **Hand Mesh** -Nachverfolgung, **QR-Codes** und **xrmeshsubsystem** werden noch nicht unterstützt.
* Die Unterstützung von **räumlichen Azure-Ankern** wird in einer zukünftigen Version angezeigt.
* **ARM64** ist die einzige unterstützte Plattform für hololens 2-apps. Die **Arm** -Plattform wird in einer zukünftigen Version angezeigt.

## <a name="troubleshooting"></a>Problembehandlung 

Wenn Sie eine Unity-App auf hololens 2 aussetzen und fortsetzen, kann die APP nicht ordnungsgemäß fortgesetzt werden, was zu vier Drehungs Punkten in der hololens-Ansicht führt. 
* Festlegen des tiefen Übermittlungs **Modus** auf " **None** " in den openxr-Projekteinstellungen als Problem Umgehung
