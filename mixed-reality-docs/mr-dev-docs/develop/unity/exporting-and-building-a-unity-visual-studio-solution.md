---
title: Exportieren und Erstellen einer Unity-Projektmappe für Visual Studio
description: In diesem Artikel wird beschrieben, wie Sie Ihr Mixed Reality-Projekt aus Unity exportieren, damit Sie in unity erstellen und Visual Studio.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, Visual Studio, Exportieren, Erstellen, Bereitstellen, HoloLens, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, UWP, Bereitstellen
ms.openlocfilehash: 78410da352b1cce1377b35737376437608f3017c00334c1a489ede26d5170d2d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203609"
---
# <a name="exporting-and-building-a-unity-visual-studio-solution"></a>Exportieren und Erstellen einer Unity-Projektmappe für Visual Studio

Wenn Ihre App die Systemtastatur nicht benötigt, wird empfohlen, *D3D* zu verwenden, damit Ihre App etwas weniger Arbeitsspeicher und eine schnellere Startzeit benötigt. Wenn Sie jedoch die Systemtastatur über die TouchScreenKeyboard-API verwenden, müssen Sie das Projekt als *XAML exportieren.*

## <a name="how-to-export-from-unity"></a>Exportieren aus Unity

![Unity-Buildeinstellungen](images/unitybuildsettings-300px.png)<br>
*Buildeinstellungen im Unity-Editor*

1. Wenn Sie bereit sind, Ihr Projekt aus Unity zu exportieren, öffnen Sie das Menü **Datei,** und wählen Sie **Build Einstellungen...**
2. Wählen **Sie Open Scenes hinzufügen** aus, um Ihre Szene dem Build hinzuzufügen.
3. Wählen Sie **im Dialogfeld Build Einstellungen** die folgenden Optionen aus, die Sie für die HoloLens:
   * **Plattform:** *Windows Universelle Plattform,* und wählen Sie Plattform **wechseln** aus, damit Ihre Auswahl wirksam wird.
   * **SDK:** *Universal 10*.
   * **UWP-Buildtyp:** *D3D*.
4. **Optional:** **Unity C#-Projekte:** Überprüft.

>[!NOTE]
>Wenn Sie dieses Kontrollkästchen aktivieren, können Sie:
>* Debuggen Sie Ihre App im Visual Studio Remotedebugger.
>* Bearbeiten Sie Skripts im Unity C#-Projekt, während Sie IntelliSense für WinRT-APIs verwenden.

5. Öffnen Sie **player Einstellungen...** im Fenster **Build Einstellungen...**
6. Wählen Sie **die Einstellungen Universelle Windows Plattform aus.**
7. Erweitern Sie die Gruppe **XR-Einstellungen**.
8. Aktivieren Sie **im Abschnitt XR Einstellungen** das Kontrollkästchen Virtual Reality Supported (Virtual **Reality** unterstützt), um eine neue Liste mit **Virtual Reality-Geräten** hinzuzufügen, und vergewissern Sie sich, dass **"Windows Mixed Reality"** als unterstütztes Gerät aufgeführt ist.
9. Kehren Sie zum **Dialogfeld Build Einstellungen** zurück.
10. Wählen Sie **Build** aus.
11. Erstellen Sie Windows angezeigten Dialogfeld "Explorer" einen neuen Ordner, der die Buildausgabe von Unity enthält. Im Allgemeinen nennen wir den Ordner "App".
12. Wählen Sie den neu erstellten Ordner und dann **Ordner auswählen aus.**
13. Sobald Unity die Entwicklung abgeschlossen hat, wird ein Windows Explorer-Fenster mit dem Stammverzeichnis des Projekts geöffnet. Navigieren Sie zum neu erstellten Ordner.
14. Öffnen Sie die generierte Visual Studio Projektmappendatei, die sich in diesem Ordner befindet.

## <a name="when-to-re-export-from-unity"></a>Wann aus Unity erneut exportiert werden soll

Wenn Sie **das Kontrollkästchen C#-Projekte** aktivieren, wenn Sie Ihre App aus Unity exportieren, wird eine Visual Studio-Projektmappe erstellt, die alle Ihre Unity-Skriptdateien enthält. Wenn Sie all Ihre Skripts an einem Ort haben, können Sie iterieren, ohne erneut aus Unity zu exportieren. Wenn Sie jedoch Änderungen an Ihrem Projekt vornehmen, die nicht nur den Inhalt von Skripts ändern, müssen Sie aus Unity erneut exportieren. Einige Beispiele für Zeiten, die Sie erneut aus Unity exportieren müssen, sind:
* Sie können Objekte auf der Registerkarte "Project hinzufügen oder entfernen.
* Sie ändern einen beliebigen Wert auf der Registerkarte Inspektor.
* Sie können Objekte auf der Registerkarte Hierarchie hinzufügen oder entfernen.
* Sie ändern alle Unity-Projekteinstellungen.

## <a name="building-and-deploying-a-unity-visual-studio-solution"></a>Erstellen und Bereitstellen einer Unity-Visual Studio Lösung

Der Rest des Erstellens und Bereitstellens von Apps erfolgt in [Visual Studio.](../platform-capabilities-and-apis/using-visual-studio.md) Sie müssen eine Unity-Buildkonfiguration angeben. Die Namenskonventionen von Unity können sich von denen unterscheiden, die Sie in der Visual Studio:

|  Konfiguration  |  Erläuterung | 
|----------|----------|
|  Debuggen  |  Alle Optimierungen deaktiviert, und der Profiler ist aktiviert. Wird zum Debuggen von Skripts verwendet. | 
|  Master  |  Alle Optimierungen sind aktiviert, und der Profiler ist deaktiviert. Wird zum Übermitteln von Apps an die Store. | 
|  Freigabe  |  Alle Optimierungen sind aktiviert, und der Profiler ist aktiviert. Wird zum Auswerten der App-Leistung verwendet. | 

Beachten Sie, dass die obige Liste eine Teilmenge der allgemeinen Trigger ist, die dazu führen, dass Visual Studio Projekt generiert werden muss. Im Allgemeinen erfordert das Bearbeiten von CS-Dateien Visual Studio innerhalb von Unity nicht, dass das Projekt neu generiert wird.

## <a name="troubleshooting"></a>Problembehandlung

Wenn Sie feststellen, dass Änderungen an Ihren CS-Dateien in Ihrem Visual Studio-Projekt nicht erkannt werden, stellen Sie sicher, dass **Unity C#-Projekte** beim Generieren des VS-Projekts über das Unity-Menü Erstellen überprüft wird.
