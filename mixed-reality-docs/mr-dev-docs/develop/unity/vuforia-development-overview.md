---
title: Verwenden von Vuforia mit Unity
description: Verwenden Sie Vuforia, um Windows Mixed Reality Anwendungen in Unity zu erstellen.
author: thetuvix
ms.author: alexturn
ms.date: 12/20/2019
ms.topic: article
keywords: Vuforia, Marker, Koordinaten, Bezugsrahmen, Nachverfolgung, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Unity, HoloLens, Gerätenachverfolgung, Leistungsmodus, Vuforie Entwicklerportal
ms.openlocfilehash: 1a21f4bb441a1ab0706b5916feaac0d691486626
ms.sourcegitcommit: 7160843723ccd6567490e2f4222219603f184d76
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232170"
---
# <a name="using-vuforia-engine-with-unity"></a>Verwenden der Vuforien-Engine mit Unity

Die Vuforien-Engine bietet eine wichtige Funktion für HoloLens– die Leistungsfähigkeit, AR-Umgebungen mit bestimmten Bildern und Objekten in der Umgebung zu verbinden. Sie können diese Funktion verwenden, um Schritt-für-Schritt-Anleitungen über Maschinen für das Industrieunternehmen zu überlagern oder einem physischen Produkt oder Spiel digitale Features und Erfahrungen hinzuzufügen.

Die Vuforien-Engine bietet eine Vielzahl von Features und Zielen, um Ihren AR-Entwicklungsprozess flexibler zu gestalten. Eines unserer neuesten Features, Vuforie-Modellziele, ist eine wichtige Funktion sowohl für kommerzielle als auch für industriell genutzte Anwendungen. Modellziele ermöglichen Es Anwendungen, physische Objekte wie Computer, Autos oder Spielzeug zu erkennen und anhand eines CAD- oder digitalen 3D-Modells nachzuverfolgen. Bei industriell verwendeten Anwendungen kann dieses Feature Assemblymitarbeitern und Servicetechnikern AR-Arbeitsanweisungen und anleitungsbezogene Anleitungen bereitstellen, während sie sich in der Fabrik oder außerhalb des Bereichs auf dem Gebiet ausführen.

Vorhandene Vuf engine-Apps, die für Smartphones und Tablets erstellt wurden, können in Unity problemlos für die Ausführung auf HoloLens konfiguriert werden. Sie können sogar die Vuforien-Engine verwenden, um Ihre neue HoloLens-App auf Windows 10 Tablets wie die Surface Pro und Surface Book zu bringen.


## <a name="get-the-tools"></a>Tools herunterladen

[Installieren Sie die empfohlenen Versionen](../install-the-tools.md) von Visual Studio und Unity, und konfigurieren Sie Dann Unity für die Verwendung von Visual Studio und der bevorzugten IDE und des bevorzugten Compilers. 

Achten Sie beim Installieren von Unity darauf, das "Windows Store IL2CPP Scripting Backend" zu installieren.

Fügen Sie das Vuf engine-Paket wie hier beschrieben [hinzu.](https://library.vuforia.com/content/vuforia-library/en/articles/Solution/vuforia-engine-package-hosting-for-unity.html)

## <a name="getting-started-with-vuforia-engine"></a>Erste Schritte mit der Vuforien-Engine

Der beste Ausgangspunkt für das Erlernen der Vuforien-Engine und HoloLens ist das Beispiel für die [Vuforien-Engine HoloLens](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) (verfügbar im Unity Asset Store). Das Beispiel enthält ein vollständiges HoloLens Projekt, einschließlich vorkonfigurierten Szenen, die in einem HoloLens bereitgestellt werden können.

Die Szenen zeigen, wie Sie mithilfe von Vuforie-Bildzielen ein Bild erkennen und mit digitalen Inhalten in einer HoloLens erweitern. Die Vuforien-Engine HoloLens Sample enthält auch eine Szene, die die Verwendung von Modellzielen und VuMarks auf HoloLens zeigt. Sie können ganz einfach Ihre eigenen Inhalte in den Szenen ersetzen, um mit der Erstellung von HoloLens Apps zu experimentieren, die die Vuf engine verwenden.



## <a name="configuring-a-vuforia-app-for-hololens"></a>Konfigurieren einer Vuforie-App für HoloLens

Die Entwicklung einer Vuf engine-App für HoloLens entspricht im Wesentlichen der Entwicklung von Vuf engine-Apps für andere Geräte. Anschließend können Sie die im abschnitt unten beschriebenen Buildeinstellungen und Konfigurationen anwenden. Dies ist alles, was erforderlich ist, damit die Vuforia-Engine mit den HoloLens Systemen für räumliche Zuordnung und Positionsnachverfolgung arbeiten kann.

## <a name="build-and-run-the-vuforia-engine-sample-for-hololens"></a>Erstellen und Ausführen des Vuf engine-Beispiels für HoloLens
1.  Laden Sie das Beispiel für die [Vuf engine für HoloLens](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) aus dem Unity-Medienobjekt Store
2.  Anwenden der [empfohlenen Unity-Engine-Optionen für Leistung und Leistung](performance-recommendations-for-unity.md)
3.  Fügen Sie die Beispielszenen zu **Szenen** im **Build hinzu.**
4.  Wechseln **Sie unter Build Einstellungen** auf build platform to UWP (Buildplattform zu **UWP),** indem Sie auf die Schaltfläche Offene Szenen **hinzufügen** klicken.
![image](https://user-images.githubusercontent.com/45470042/89573103-173daa80-d7f8-11ea-9284-931a7b6c913d.png)
5.  Wählen Sie die Schaltfläche **Player Einstellungen** aus.  
   * Wählen Sie das **UWP-Symbol** aus, und erweitern Sie den **Abschnitt XR Einstellungen.**
   * Stellen Sie sicher, dass **Virtual Reality Supported** aktiviert ist.    
   * Stellen Sie unter **Virtual Reality SDKs** Sicher, dass:
     * **Fenster Mixed Reality** ist in der Liste enthalten, und die **Option Tiefenpufferfreigabe aktivieren** ist aktiviert. 
     * Das **Tiefenformat** ist auf **16-Bit-Tiefe festgelegt.** 
   * Stellen Sie sicher, dass der **Stereo-Renderingmodus** auf **Single Pass Instanced** festgelegt ist.
6.  Erweitern Sie den Abschnitt **Veröffentlichen Einstellungen.**
   * Stellen Sie unter **Funktionen** sicher, dass **Internetclient, WebCam, Mikrofon** und **SpatialPerception** ausgewählt sind.
   * **HINWEIS: SpatialPerception** sollte nur ausgewählt werden, wenn Sie die Surface Observer-API verwenden möchten.
   * Stellen Sie unter **Unterstützte Gerätefamilien** sicher, dass **Holographic** ausgewählt ist. 
7.  Erweitern Sie den Abschnitt **Auflösung und Präsentation.**
   * Deaktivieren Sie **Im Hintergrund ausführen,** damit die Vuforien-Engine angehalten wird, wenn die App in den Hintergrund gestellt wird, und wieder auf die Kamera zugreifen kann, wenn die App fortgesetzt wird. 
   * Stellen Sie in der Dropdownliste **Standardausrichtung** sicher, dass **Querformat Links** ausgewählt ist.
8.  Kehren **Sie** zum Fenster Build Einstellungen zurück, und wählen Sie **Erstellen** aus, um ein Visual Studio Projekt zu generieren.
9.  Erstellen Sie die ausführbare Datei aus Visual Studio, und installieren Sie sie auf Ihrem HoloLens.

## <a name="the-vuforia-developer-portal"></a>Die Vuforia-Entwicklerportal

Entwickler, die ihre eigenen AR-Erfahrungen mit der Vuf engine und HoloLens erstellen möchten, sollten sich auf unserer Vuforia-Entwicklerportal unter [developer.vuforia.com](https://developer.vuforia.com/)registrieren. Im Portal haben Entwickler Zugriff auf die [Vuf engine-Foren,](https://developer.vuforia.com/forum) in denen sie an Community-Diskussionen teilnehmen können, eine [Bibliothek](https://library.vuforia.com/) mit ausführlicher Dokumentation zu allen Features der Vufoa-Engine und den [Vuforie-Ziel-Manager,](https://developer.vuforia.com/target-manager) in dem Benutzer ihre eigenen benutzerdefinierten Ziele erstellen können. Entwickler können sich auch mit dem [Vufori](https://developer.vuforia.com/license-manager)License Manager für eine kostenlose Entwicklerlizenz registrieren.

## <a name="device-tracking-with-vuforia"></a>Gerätenachverfolgung mit Vuforia

[Die Gerätenachverfolgung](https://library.vuforia.com/features/environments/device-tracker-overview.html) verwaltet die Nachverfolgung auch dann, wenn ein Ziel nicht mehr angezeigt wird. Sie wird automatisch für alle Ziele aktiviert, wenn die Positionsgerätenachverfolgung aktiviert ist. Für HoloLens Anwendungen wird die Positionsgeräteverfolgung automatisch in Unity gestartet.

Die Vuforien-Engine verbindet die Posen automatisch aus der Kameraverfolgung und der räumlichen Nachverfolgung HoloLens, um stabile Zielhaltungen bereitzustellen, unabhängig davon, ob das Ziel von der Kamera gesehen wird oder nicht.

Da der Prozess automatisch verarbeitet wird, ist keine Programmierung durch den Entwickler erforderlich.


**Im Folgenden wird der Prozess auf hoher Ebene beschrieben:**
1. Der Ziel-Tracker von Vuforia erkennt das Ziel.
2. Die Zielnachverfolgung wird dann initialisiert.
3. Die Position und Drehung des Ziels werden analysiert, um eine stabile Schätzung der Position für die HoloLens
4. Die Vuforien-Engine transformiert die Darstellung des Ziels in den HoloLens raumbezogenen Zuordnungskoordinatenraum.
5. HoloLens übernimmt die Nachverfolgung, wenn das Ziel nicht mehr angezeigt wird. Wenn Sie das Ziel erneut betrachten, verfolgt Vuforia die Bilder und Objekte weiterhin genau.

Ziele, die erkannt, aber nicht mehr angezeigt werden, werden als EXTENDED_TRACKED gemeldet. In diesen Fällen rendert das DefaultTrackableEventHandler-Skript, das für alle Ziele verwendet wird, weiterhin Augmentationsinhalt. Der Entwickler kann dieses Verhalten steuern, indem er ein benutzerdefiniertes nachverfolgbares Ereignishandlerskript implementiert.

## <a name="performance-mode-with-vuforia-engine"></a>Leistungsmodus mit Vuforien-Engine 

Es ist möglich, die Leistung auf der HoloLens über die Vuforien-Engine zu verwalten, um ar-Funktionen zu verbessern und die Workload auf der CPU zu reduzieren. Die Vuforien-Engine bietet drei Modi, die ausgewählt werden können: standard, für die Optimierung der Geschwindigkeit und für die Optimierung der Qualität. 

*   mit MODE_OPTIMIZE_SPEED können Sie die Arbeitsauslastung auf dem HoloLens Gerät minimieren und eignet sich hervorragend für die Erweiterung von AR-Funktionen. Es wird empfohlen, in Situationen, in denen die App statische Objekte/Ziele nachverfolgung.
*   MODE_DEFAULT ist der normale Modus, der in den meisten Szenarien verwendet werden kann.
*   MODE_OPTIMIZE_QUALITY eignet sich besser für die Nachverfolgung von verschiebbaren Zielen oder Modellzielen, die Voraussichtlich übernommen werden.

**Festlegen des Modus**

Um den Leistungsmodus in Unity zu ändern, navigieren Sie zu Vuforia-Konfiguration (STRG+UMSCHALT+V /CMD+UMSCHALT+V), die sich als Komponente im ARCamera GameObject befindet. 
*   Wählen Sie das Dropdownmenü für Kameragerätemodus aus, und wählen Sie eine der drei Optionen aus.


## <a name="see-also"></a>Siehe auch
* [Installieren der Tools](../install-the-tools.md)
* [Koordinatensysteme](../../design/coordinate-systems.md)
* [Räumliche Abbildung](../../design/spatial-mapping.md)
* [Kamera in Unity](camera-in-unity.md)
* [Exportieren und Erstellen einer Unity-Projektmappe für Visual Studio](exporting-and-building-a-unity-visual-studio-solution.md)
* [Vuforia-Dokumentation: Erste Schritte mit der Vuforien-Engine für Windows 10-Entwicklung](https://library.vuforia.com/articles/Training/Getting-Started-with-Vuforia-for-Windows-10-Development.html)
* [Vuforia-Dokumentation: Erste Schritte mit der Vuforien-Engine in Unity](https://library.vuforia.com/articles/Training/getting-started-with-vuforia-in-unity.html)
* [Vuforia-Dokumentation: Arbeiten mit dem HoloLens-Beispiel in Unity](https://library.vuforia.com/articles/Solution/Working-with-the-HoloLens-sample-in-Unity.html)
* [Vuforie-Dokumentation: Gerätenachverfolgung in Vuforia](https://library.vuforia.com/features/environments/device-tracker-overview.html)
* [Vuforia-Dokumentation: Framerate und Leistungsoptimierung](https://library.vuforia.com/content/vuforia-library/en/articles/Solution/Framerate-Optimization-for-Mixed-Reality-Apps.html)
