---
title: Von openxr-Plug-in unterstützte Funktionen in Unity
description: Entdecken Sie die Features, die openxr für die Entwicklung gemischter Realität in Unity unterstützt.
author: hferrone
ms.author: alexturn
ms.date: 12/15/2020
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, Mixed Reality, mrtk, Mixed Reality Toolkit, Augmented Reality, Virtual Reality, Mixed Reality-Headsets, erlernen, Tutorial, Getting Started
ms.openlocfilehash: 5db08dee6b26de6fa3f44d92709e4903bb90a44c
ms.sourcegitcommit: 7595db7438398b5c78cec41a6f8ab625711bf8ec
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2020
ms.locfileid: "97664418"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a>Gemischte Funktionen von openxr unterstützten Funktionen in Unity

Das **gemischte openxr-Plug** -in für die Realität ist eine Erweiterung des Unity **openxr-Plug** -ins und unterstützt eine Reihe von Features für hololens 2-und Windows Mixed Reality-Headsets. Bevor Sie fortfahren, stellen Sie sicher, dass Sie **Unity 2020,2** oder höher, **openxr Plugin, Version 0.1.1** oder höher, installiert haben und Ihr Unity-Projekt [für openxr konfiguriert](openxr-getting-started.md)ist.

## <a name="whats-supported"></a>Unterstützte Funktionen

Die folgenden Funktionen werden derzeit unterstützt:

* Unterstützt sowohl UWP-Anwendungen für hololens 2-als auch Win32-VR-Anwendungen für Windows Mixed Reality-Headsets.
* Optimiert das UWP-Paket und die corewindow-Interaktion für hololens 2-Anwendungen.
* Welt weite Nachverfolgung mithilfe von Ankern und unbeschränktes Raum.
* Anker-Speicher-API zum Beibehalten von Ankern an hololens 2 lokalen Speicher.
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

## <a name="motion-controller-and-hand-interactions"></a>Bewegungs Controller und Hand Interaktionen
Informationen zu den Grundlagen von Mixed Reality-Interaktionen in Unity finden Sie in der [Unity-Anleitung für](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html)Unity. In dieser Unity-Dokumentation werden die Zuordnungen von Controller spezifischen Eingaben zu stärker verallgemeinerbaren en, die Art und Weise, wie `InputFeatureUsage` Verfügbare XR-Eingaben identifiziert und kategorisiert werden können, das Lesen von Daten aus diesen Eingaben und vieles mehr behandelt. 
 
Das Mixed Reality openxr-Plug-in bietet zusätzliche Eingabe Interaktions Profile, die Standard `InputFeatureUsage` s wie unten beschrieben zugeordnet sind: 
 
| `InputFeatureUsage` | HP-Reverb-G2-Controller (openxr) | Hololens-Hand (openxr) |
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

#### <a name="haptics"></a>Haptik
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
