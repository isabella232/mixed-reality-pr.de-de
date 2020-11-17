---
title: Exportieren und Erstellen einer Unity-Projektmappe für Visual Studio
description: In diesem Artikel wird beschrieben, wie Sie Ihr Mixed Reality-Projekt aus Unity exportieren, sodass Sie in Visual Studio erstellen und bereitstellen können.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, Visual Studio, Export, Build, Bereitstellung, hololens, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, UWP, Bereitstellung
ms.openlocfilehash: 29415fa7d561cab1aec5f0c2c9344fa24b0e8293
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677559"
---
# <a name="exporting-and-building-a-unity-visual-studio-solution"></a>Exportieren und Erstellen einer Unity-Projektmappe für Visual Studio

Wenn Sie die System Tastatur nicht in Ihrer Anwendung verwenden möchten, wird empfohlen, *D3D* zu verwenden, da Ihre Anwendung etwas weniger Arbeitsspeicher beansprucht und eine etwas schnellere Startzeit hat. Wenn Sie die touchscreenkeyboard-API in Ihrem Projekt verwenden, um die System Tastatur zu verwenden, müssen Sie als *XAML* exportieren.

## <a name="how-to-export-from-unity"></a>Exportieren aus Unity

![Unity-Buildeinstellungen](images/unitybuildsettings-300px.png)<br>
*Unity-Buildeinstellungen*

1. Wenn Sie bereit sind, Ihr Projekt aus Unity zu exportieren, öffnen Sie das Menü **Datei** , und wählen Sie Buildeinstellungen aus **.**
2. Klicken Sie auf **offene Szenen hinzufügen** , um die Szene dem Build hinzuzufügen.
3. Wählen Sie im Dialogfeld " **Buildeinstellungen** " die folgenden Optionen für den Export in hololens aus:
   * **Plattform:** *universelle Windows-Plattform* , und stellen Sie sicher, dass Sie **Switch Platform** auswählen, damit die Auswahl wirksam wird.
   * **SDK:** *Universal 10*.
   * **UWP-Buildtyp:** *D3D*.
4. **Optional**: **Unity c#-Projekte:** aktiviert.

>[!NOTE]
>Wenn Sie dieses Kontrollkästchen aktivieren, können Sie Folgendes ausführen:
>* Debuggen Sie Ihre APP im Visual Studio Remote Debugger.
>* Bearbeiten Sie Skripts im Unity-c#-Projekt, während Sie IntelliSense für WinRT-APIs verwenden.

5. Öffnen Sie im Fenster " **Buildeinstellungen** " die **Player-Einstellungen...**
6. Wählen Sie die **Einstellungen für universelle Windows-Plattform** Registerkarte aus.
7. Erweitern Sie die Gruppe **XR-Einstellungen**.
8. Aktivieren Sie im Abschnitt " **XR-Einstellungen** " das Kontrollkästchen " **Virtual Reality supported** ", um eine neue **Virtual Reality-Geräte** Liste hinzuzufügen, und vergewissern Sie sich, dass **Windows Mixed Reality** als unterstütztes Gerät aufgeführt ist.
9. Kehren Sie zum Dialogfeld " **Buildeinstellungen** " zurück.
10. Wählen Sie **Build** aus.
11. Erstellen Sie im daraufhin angezeigten Dialogfeld Windows-Explorer einen neuen Ordner, der die Buildausgabe von Unity enthalten soll. Im allgemeinen benennen wir den Ordner "App".
12. Wählen Sie den neu erstellten Ordner aus, und klicken Sie auf **Ordner auswählen**.
13. Nachdem die Erstellung von Unity abgeschlossen ist, wird ein Windows-Explorer-Fenster für das Projektstamm Verzeichnis geöffnet. Navigieren Sie in den neu erstellten Ordner.
14. Öffnen Sie die generierte Visual Studio-Projektmappendatei in diesem Ordner.

## <a name="when-to-re-export-from-unity"></a>Wann sollten Sie den erneuten Export aus Unity durch Schreiben?

Durch Aktivieren des Kontrollkästchens "c#-Projekte" beim Exportieren Ihrer APP aus Unity wird eine Visual Studio-Projekt Mappe erstellt, die alle Ihre Unity-Skriptdateien enthält Dies ermöglicht es Ihnen, Ihre Skripts zu durchlaufen, ohne den erneuten Export aus Unity durchzusetzen. Wenn Sie jedoch Änderungen an Ihrem Projekt vornehmen möchten, die nicht nur den Inhalt von Skripts ändern, müssen Sie einen erneuten Export aus Unity durchführen. Es folgen einige Beispiele für den erneuten Export von Unity:
* Sie fügen der Registerkarte Projekt Objekte hinzu oder entfernen diese.
* Sie ändern alle Werte auf der Registerkarte Inspektor.
* Objekte werden der Registerkarte Hierarchie hinzugefügt oder daraus entfernt.
* Sie ändern alle Unity-Projekteinstellungen.

## <a name="building-and-deploying-a-unity-visual-studio-solution"></a>Entwickeln und Bereitstellen einer Unity-Visual Studio-Projekt Mappe

Der Rest der Bereitstellung und Bereitstellung von apps erfolgt in [Visual Studio](../platform-capabilities-and-apis/using-visual-studio.md). Sie müssen eine Unity-Buildkonfiguration angeben. Die Benennungs Konventionen von Unity unterscheiden sich möglicherweise von dem, was in Visual Studio normalerweise verwendet wird:

|  Konfiguration  |  Erklärung | 
|----------|----------|
|  Debug  |  Alle Optimierungen und der Profiler werden aktiviert. Dient zum Debuggen von Skripts | 
|  Master  |  Alle Optimierungen sind aktiviert, und der Profiler ist deaktiviert. Wird verwendet, um apps an den Store zu übermitteln. | 
|  Freigabe  |  Alle Optimierungen sind aktiviert, und der Profiler ist aktiviert. Dient zum Auswerten der APP-Leistung. | 

Beachten Sie, dass es sich bei der obigen Liste um eine Teilmenge der allgemeinen Trigger handelt, die bewirken, dass das Visual Studio-Projekt generiert werden muss. Im Allgemeinen ist es für das Bearbeiten von CS-Dateien in Visual Studio nicht erforderlich, dass das Projekt in Unity neu generiert wird.

## <a name="troubleshooting"></a>Problembehandlung

Wenn Sie feststellen, dass Änderungen an den CS-Dateien nicht in Ihrem Visual Studio-Projekt erkannt werden, stellen Sie sicher, dass "Unity c#-Projekte" aktiviert ist, wenn Sie das vs-Projekt über das Menü "Build" von Unity generieren.
