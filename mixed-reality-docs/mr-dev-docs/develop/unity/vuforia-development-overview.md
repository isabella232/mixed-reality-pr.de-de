---
title: Verwenden von Vuforia mit Unity
description: Verwenden Sie vuforia, um Windows Mixed Reality-Anwendungen in Unity zu erstellen.
author: thetuvix
ms.author: alexturn
ms.date: 12/20/2019
ms.topic: article
keywords: Vuforia, Marker, Koordinaten, Frame der Referenz, Überwachung, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Unity, hololens, Geräteüberwachung, Leistungsmodus, vuforia-Entwickler Portal
ms.openlocfilehash: ecacf4036bfab38eb90782a194c445a83ca623ba
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010561"
---
# <a name="using-vuforia-engine-with-unity"></a>Verwenden der vuforia-Engine mit Unity

Die vuforia-Engine bringt hololens eine wichtige Funktion ein – die Strom Umgebung, um eine Verbindung zwischen aren Erfahrungen und bestimmten Bildern und Objekten in der Umgebung herzustellen. Sie können diese Funktion verwenden, um eine Schritt-für-Schritt-Anleitung für das Industrieunternehmen zu überlagern oder digitale Features und Erfahrungen zu einem physischen Produkt oder Spiel hinzuzufügen.

Die vuforia-Engine bietet eine große Bandbreite an Features und Zielen, um Ihren aren Entwicklungsprozess flexibler zu gestalten. Eine unserer neuesten Features, vuforia-Modell Ziele, ist eine wichtige Funktion für gewerbliche und Industrieanwendungen. Mithilfe von Modell Zielen können Anwendungen physische Objekte wie Computer, Automobile oder Toys erkennen und basierend auf einem CAD-oder Digital 3D-Modell verfolgen. Bei Industrieanwendungen kann dieses Feature assemblyarbeitsthreads und Dienst Technikern eine ausführliche Arbeitsanleitung und Anleitungen für die Bereitstellung in der Factory und im Außendienst bereitstellen.

Vorhandene vuforia-Engine-apps, die für Smartphones und Tablets erstellt wurden, können problemlos in Unity zur unter hololens-Konfiguration konfiguriert werden. Sie können die vuforia-Engine sogar verwenden, um Ihre neue hololens-App auf Windows 10-Tablets wie Surface pro und Surface Book zu übernehmen.


## <a name="get-the-tools"></a>Tools herunterladen

[Installieren Sie die empfohlenen Versionen](../install-the-tools.md) von Visual Studio und Unity, und konfigurieren Sie Unity so, dass Visual Studio und die bevorzugte IDE und der Compiler verwendet werden. 

Stellen Sie bei der Installation von Unity sicher, dass Sie das "Windows Store IL2CPP Scripting Backend" installieren.

Fügen Sie das Paket "vuforia Engine" wie hier beschrieben hinzu [.](https://library.vuforia.com/content/vuforia-library/en/articles/Solution/vuforia-engine-package-hosting-for-unity.html)

## <a name="getting-started-with-vuforia-engine"></a>Einstieg in die vuforia-Engine

Der beste Ausgangspunkt für das Erlernen von vuforia Engine und hololens ist das [Beispiel der vuforia-Engine hololens](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) (verfügbar im Unity-Ressourcen Speicher). Das Beispiel enthält ein umfassendes hololens-Projekt, das vorkonfigurierte Szenen umfasst, die in einem hololens bereitgestellt werden können.

In den Kulissen wird gezeigt, wie Sie mithilfe von vuforia-Bild Zielen ein Bild erkennen und mit digitalen Inhalten in einer hololens-Funktionalität erweitern können. Das Beispiel der vuforia-Engine hololens enthält auch eine Szene, in der die Verwendung von Modell Zielen und vgargs in hololens gezeigt wird. Sie können Ihren eigenen Inhalt problemlos in den Kulissen austauschen, um mit der Erstellung von hololens-apps zu experimentieren, die die vuforia-Engine verwenden.



## <a name="configuring-a-vuforia-app-for-hololens"></a>Konfigurieren einer vuforia-App für hololens

Das Entwickeln einer vuforia-Engine-App für hololens ist im Grunde das gleiche wie das Entwickeln von vuforia-Engine-Apps für andere Geräte. Anschließend können Sie die im Abschnitt unten beschriebenen Buildeinstellungen und Konfigurationen anwenden. Das ist alles, was erforderlich ist, um die vuforia-Engine für die Zusammenarbeit mit der räumlichen Zuordnung von hololens und den Systemen mit Positionsüberwachung zu aktivieren.

## <a name="build-and-run-the-vuforia-engine-sample-for-hololens"></a>Erstellen und Ausführen des Beispiels "vuforia Engine" für hololens
1.  Laden Sie das [Beispiel für die vuforia-Engine für hololens](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) aus dem Unity-Asset Store herunter.
2.  Anwenden der [empfohlenen Unity-Engine-Optionen auf Leistung und Leistung](performance-recommendations-for-unity.md)
3.  Fügen Sie die Beispiel Szenen zu **Szenen** in **Build hinzu.**
4.  Wechseln Sie in den **Buildeinstellungen** zu **UWP** , und klicken Sie auf die Schaltfläche **offene Szenen hinzufügen** .
![image](https://user-images.githubusercontent.com/45470042/89573103-173daa80-d7f8-11ea-9284-931a7b6c913d.png)
5.  Wählen Sie die Schaltfläche **Player Einstellungen** aus.  
   * Wählen Sie das **UWP** -Symbol aus, und erweitern Sie den Abschnitt **XR-Einstellungen** .
   * Stellen Sie sicher, dass **Virtual Reality unterstützt** aktiviert ist.    
   * Unter **Virtual Reality-sdert** stellen Sie Folgendes sicher:
     * Die **Fenster gemischte Realität** ist in der Liste enthalten, und die Aktivierung der **tiefen Puffer** Freigabe ist aktiviert. 
     * Das **tiefen Format** wird auf eine **16-Bit-Tiefe** festgelegt. 
   * Stellen Sie sicher, dass der **Stereo Renderingmodus** auf **Single Pass-instanziierten** eingestellt ist
6.  Erweitern Sie den Abschnitt **Veröffentlichungs Einstellungen** .
   * Stellen Sie unter " **Funktionen** " sicher, dass **Internet Client, Webcam, Mikrofon** und **spatialperception** ausgewählt sind.
   * **Hinweis: spatialperception** sollte nur ausgewählt werden, wenn Sie beabsichtigen, die Surface Observer-API zu verwenden.
   * Stellen Sie sicher, dass unter **unterstützte Gerätefamilien** die Option **Holographic** ausgewählt ist. 
7.  Erweitern Sie den Abschnitt **Auflösung und Präsentation** .
   * Deaktivieren Sie **im Hintergrund ausführen** , sodass die vuforia-Engine angehalten wird, wenn die APP im Hintergrund abgelegt wird, und dann erneut auf die Kamera zugreifen kann, wenn die APP fortgesetzt wird. 
   * Stellen Sie sicher, dass in der Dropdown Liste **Default Orientation** die Option **Landscape Left** ausgewählt ist.
8.  Wechseln Sie zum Fenster mit den **Buildeinstellungen** , und wählen Sie **Erstellen** , um ein Visual Studio-Projekt zu generieren
9.  Erstellen Sie die ausführbare Datei aus Visual Studio, und installieren Sie Sie auf Ihren hololens.

## <a name="the-vuforia-developer-portal"></a>Das vuforia-Entwickler Portal

Entwickler, die ihre eigenen aren Erfahrungen mit der vuforia-Engine und hololens erstellen möchten, sollten sich bei unserem vuforia-Entwickler Portal unter [Developer.vuforia.com](https://developer.vuforia.com/)anmelden. Im Portal haben Entwickler Zugriff auf die [vuforia-Engine-Foren](https://developer.vuforia.com/forum) , in denen Sie Communitydiskussionen beitreten können, eine [Bibliothek](https://library.vuforia.com/) mit ausführlichen Dokumentationen zu allen Features der vuforia-Engine und der [vuforia-Ziel-Manager](https://developer.vuforia.com/target-manager) , in dem Benutzer ihre eigenen benutzerdefinierten Ziele erstellen können. Entwickler können sich mit dem [vuforia-Lizenz-Manager](https://developer.vuforia.com/license-manager)auch für eine kostenlose Entwicklerlizenz registrieren.

## <a name="device-tracking-with-vuforia"></a>Geräte Nachverfolgung mit vuforia

Die [Geräte Nachverfolgung](https://library.vuforia.com/features/environments/device-tracker-overview.html) verwaltet die Nachverfolgung, auch wenn ein Ziel nicht mehr angezeigt wird. Sie wird automatisch für alle Ziele aktiviert, wenn die Protokollierung für Positions Geräte aktiviert ist. Bei hololens-Anwendungen wird die Positional-Geräte Protokollierung automatisch in Unity gestartet.

Die vuforia-Engine verbindet die Posen automatisch von der Kamera Verfolgung und der räumlichen Nachverfolgung von hololens, um stabile Ziele bereitzustellen, unabhängig davon, ob das Ziel von der Kamera erkannt wird oder nicht.

Da der Prozess automatisch verarbeitet wird, ist keine Programmierung durch den Entwickler erforderlich.


**Im folgenden finden Sie eine allgemeine Beschreibung des Prozesses:**
1. Der Ziel-Tracker von vuforia erkennt das Ziel.
2. Die Ziel Überwachung wird initialisiert.
3. Die Position und die Drehung des Ziels werden analysiert, um eine robuste positätsschätzung für die hololens bereitzustellen.
4. Die gestellungsweb-Engine wandelt die Pose des Ziels in das hololens Spatial Mapping-Koordinaten Bereich um.
5. Hololens übernimmt die Überwachung, wenn das Ziel nicht mehr in der Ansicht angezeigt wird. Wenn Sie sich das Ziel erneut ansehen, verfolgt vuforia die Bilder und Objekte weiterhin korrekt.

Ziele, die erkannt werden, aber nicht mehr in der Ansicht angezeigt werden, werden als EXTENDED_TRACKED gemeldet. In diesen Fällen rendern das defaulttrackableeventhandler-Skript, das für alle Ziele verwendet wird, den Erweiterungs Inhalt weiter. Der Entwickler kann dieses Verhalten steuern, indem er ein benutzerdefiniertes Skript für einen ausführbaren Ereignishandler implementiert.

## <a name="performance-mode-with-vuforia-engine"></a>Leistungsmodus mit der vuforia-Engine 

Es ist möglich, dass die vuforia-Engine die Leistung auf den hololens verwaltet, um die Benutzerfreundlichkeit zu beeinträchtigen und die Arbeitsauslastung auf der CPU zu verringern. Die vuforia-Engine bietet drei Modi, die ausgewählt werden können: Standard, zur Optimierung der Geschwindigkeit und zur Optimierung der Qualität. 

*   Mit MODE_OPTIMIZE_SPEED können Sie die Arbeitsauslastung auf dem hololens-Gerät minimieren und eignen sich hervorragend für die Erweiterung von aren Erfahrungen. Wir empfehlen für Situationen, in denen die APP statische Objekte/Ziele nachverfolgt.
*   MODE_DEFAULT ist der normale Modus, der in den meisten Szenarien verwendet werden kann.
*   MODE_OPTIMIZE_QUALITY eignet sich besser für die Nachverfolgung von verschiebbaren Zielen oder Modell Zielen, die Sie erwarten.

**Festlegen des Modus**

Wenn Sie den Leistungsmodus in Unity ändern möchten, navigieren Sie zu "vuforia Configuration" (STRG + UMSCHALT + v/cmd + UMSCHALT + v), die sich im arcamera-gameobject als Komponente befindet. 
*   Wählen Sie das Dropdown Menü für den Kamerageräte Modus aus, und wählen Sie eine der drei Optionen aus.


## <a name="see-also"></a>Siehe auch
* [Installieren der Tools](../install-the-tools.md)
* [Koordinatensysteme](../../design/coordinate-systems.md)
* [Räumliche Abbildung](../../design/spatial-mapping.md)
* [Kamera in Unity](camera-in-unity.md)
* [Exportieren und Erstellen einer Unity-Projektmappe für Visual Studio](exporting-and-building-a-unity-visual-studio-solution.md)
* [Vuforia-Dokumentation: entwickeln für Windows 10 in Unity](https://library.vuforia.com/articles/Solution/Developing-for-Windows-10-in-Unity)
* [Vuforia-Dokumentation: Installieren der vuforia Unity-Erweiterung](https://library.vuforia.com/articles/Solution/Installing-the-Unity-Extension)
* [Vuforia-Dokumentation: Arbeiten mit dem hololens-Beispiel in Unity](https://library.vuforia.com/articles/Solution/Working-with-the-HoloLens-sample-in-Unity)
* [Vuforia-Dokumentation: Geräte Nachverfolgung in vuforia](https://library.vuforia.com/features/environments/device-tracker-overview.html)
* [Vuforia-Dokumentation: Framerate und Leistungsoptimierung](https://library.vuforia.com/content/vuforia-library/en/articles/Solution/Framerate-Optimization-for-Mixed-Reality-Apps.html)
