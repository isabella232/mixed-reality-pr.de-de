---
title: Profilerstellung mit Unreal Insights
description: Erfahren Sie, wie Sie Unreal Insights auf hololens 2 verwenden.
author: sajidfarooq
ms.author: v-hferrone
ms.date: 12/10/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, hololens, hololens 2, Development, profling, Unreal Insights, Dokumentation, Guides, Features, holograms, Spieleentwicklung, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: b41d36679adfb35b5cc3561b8d5e7734654e7fb5
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580838"
---
# <a name="profiling-with-unreal-insights"></a>Profilerstellung mit Unreal Insights 

[Unreal Insights](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html) ist ein Profil Erstellungs System, das Daten von Unreal Engine sammelt, analysiert und visualisiert. Das Profil Erstellungs System kann Sie bei der Suche nach Optimierungs Engpässen und Bereichen unterstützen, in denen die Leistung von apps eine Erhöhung der Anwendungen Normalerweise aktivieren Sie Unreal Insights direkt aus dem Editor, aber für hololens 2 müssen Sie die Befehlszeile verwenden.  

## <a name="setup"></a>Einrichten

Unreal ermöglicht es Ihnen, ein "benutzerdefiniertes Profil" im hololens-Start Programm mit den Befehlszeilen Parametern zu erstellen und zu konfigurieren, die Unreal Insights ermöglichen.

1.  Suchen Sie die IP-Adresse Ihres Computers mithilfe des Befehls " **ipconfig** " an der Eingabeaufforderung. Die IP-Adresse ist die von ipconfig aufgelistete IPv4-Adresse. Beachten Sie dies für den späteren Zeitpunkt, wenn Sie Befehlszeilenparameter festlegen.

> [!IMPORTANT]
> Wenn Sie sich hinter einem VPN befinden, müssen Sie möglicherweise die IP-Adresse angeben, die über das VPN bereitgestellt wird.

![Screenshot der Befehlszeilen Ergebnisse für den Befehl "ipconfig"](images/unreal-insights-img-01.png)

2.  Wechseln Sie zum oberen Rand des Unreal Engine-Panels, und öffnen Sie **Geräte-Manager** unter der Schaltfläche " **starten** ":

![Screenshot der Startoptionen mit hervorgehobenem Geräte-Manager](images/unreal-insights-img-02.png)

3.  Wählen Sie im Geräte-Manager die **Option nicht aufgelistetes Gerät hinzufügen** aus:

![Screenshot des geöffneten Geräte-Managers in der Unreal-Engine](images/unreal-insights-img-03.png)

4. Klicken Sie auf **Plattform auswählen** , und wählen Sie **hololens** aus:

![Screenshot der Dropdown Liste "nicht aufgelisteten Gerät hinzufügen" mit hervorgehobenem hololens](images/unreal-insights-img-04.png)

5.  Wenn Sie ipoverusb verwenden, geben Sie 127.0.0.1:10080 als Geräte Bezeichner ein. Geben Sie Ihren hololens-Benutzer und das Kennwort in die entsprechenden Felder ein, und füllen Sie den **anzeigen Amen** wie gewünscht aus.

> [!IMPORTANT]
> Der Geräte Bezeichner ist die IP-Adresse der hololens und nicht der Computer, auf dem Unreal Insights ausgeführt wird, den Sie in Schritt 1 gefunden haben.

![Screenshot der Geräte Details des hololens in Device Manager](images/unreal-insights-img-05.png)

6.  Wählen Sie **Hinzufügen** aus, und ihre hololens sollte in der Geräteliste des Geräte-Managers angezeigt werden:

![Screenshot der der Geräteliste hinzugefügten hololens](images/unreal-insights-img-06.png)

## <a name="launch"></a>Starten

1. Öffnen Sie das **Projekt** **Startfeld** über den Bereich UE4 unter der Schaltfläche starten:

![Screenshot der Startoptionen mit hervorgehobenem Projekt Starter](images/unreal-insights-img-07.png)

2. Wählen Sie die **+** Schaltfläche zum Erstellen eines benutzerdefinierten Profils unter **benutzerdefinierte Start profile** aus. Nach der Erstellung können Sie dieses Profil später jederzeit bearbeiten:

![Screenshot: Projektstart Programm mit hervorgehobenem benutzerdefinierten Start Profilen](images/unreal-insights-img-08.png)

3. Wählen Sie im benutzerdefinierten Start Profil hololens die Schaltfläche **Profil bearbeiten** aus, und konfigurieren Sie Folgendes:
    * Wählen Sie für **das Buch die** Option **Kochen** aus, um das Kopieren auf das Gerät
    * Sie sollten die Option "möchten **Sie archivieren?** " im Abschnitt " **Archive** " aktivieren, um die generierte. appxbundle-Datei beizubehalten, anstatt Sie zu löschen, um Speicherplatz zu sparen. Geben Sie einen Speicherort für die appxbundle-Datei an, und wechseln Sie bei Bedarf zu einem entwicklungbuild.

![Screenshot der Koch Optionen in der Profil Konfiguration mit dem Buch "Cook" und "hololens" hervorgehoben](images/unreal-insights-img-09.png)

4. Legen **Sie fest, wie soll der Build** bereitgestellt werden soll? auf das **Gerät zu kopieren** , um den **Startbereich** der Benutzeroberfläche zu aktivieren:

![Screenshot des Projektstart Programms mit den Bereitstellungs Optionen mit hervorgehobener Kopie auf Gerät](images/unreal-insights-img-10.png)

5. Legen Sie **Zusätzliche Befehlszeilenparameter** im **Startbereich** fest. Die Parameter werden in eine ue4commandline.txt Datei geschrieben, in das Bündel gepackt und beim Start verwendet. 
    <!-- TODO: Need more detail on what this parameter does and where to find others. -->
    * Probieren Sie die folgenden Schritte aus: **-tracehost = IP_OF_YOUR_PC-Trace = Log, Bookmark, Frame, CPU, GPU, loadtime, File, NET**
    * Eine komplette Liste der verfügbaren Startparameter finden Sie in der [Unreal Insights-Referenz Dokumentation](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html).

> [!NOTE]
> "IP_OF_YOUR_PC" ist die IP-Adresse, die in Schritt 1 gefunden wurde. Dabei handelt es sich um die IP-Adresse des Computers, auf dem Unreal Insights ausgeführt wird, nicht um die IP-Adresse der hololens.

> [!IMPORTANT]
> Ablauf Verfolgungen können sehr schnell groß werden. Aktivieren Sie nur die Kanäle, die Sie benötigen, um die Ablauf Verfolgungs Größe zu beschränken.

![Screenshot der Start Konfigurationsoptionen](images/unreal-insights-img-11.png)

6. Starten Sie vor dem Starten der APP Unreal Insights, sonst ist Unreal Insights nicht in der Lage, vor der APP ordnungsgemäß zu initialisieren:
    * Die ausführbare Datei von Unreal Insights wird im Ordner Binärdateien-Engine gespeichert, in der Regel wie folgt: "c:\programme\epic Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe"

![Screenshot der ausführbaren Datei "Unreal Insights"](images/unreal-insights-img-12.png)

6.  Wählen Sie **zurück** , um zum Stamm des Dialog Felds für das **Projekt** Startfeld zurückzukehren.
7.  Klicken Sie im Editor auf **Start** im benutzerdefinierten Start Profil.

![Bildschirm Abbildung von benutzerdefinierten Start Profilen](images/unreal-insights-img-13.png)

8.  Sehen Sie sich an, wie Ihr Projekt verpackt, auf Ihrem Gerät installiert und gestartet wird.

## <a name="profiling"></a>Profilerstellung

Zurück in Unreal Insights: Wählen Sie die **Live** Verbindung zum Gerät aus, um die Profilerstellung zu starten.

Das benutzerdefinierte Profil wird von Projekten gemeinsam genutzt. Von hier aus können Sie das von Ihnen erstellte benutzerdefinierte Profil verwenden, anstatt jedes Mal dies zu tun. Sie müssen die Verbindung mit dem Gerät nur bei jedem Start von Unreal mit den Schritten 3 bis 6 im [Abschnitt Setup](#setup)neu erstellen.

## <a name="see-also"></a>Weitere Informationen
* [Unreal Insights-Dokumentation](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/index.html)

