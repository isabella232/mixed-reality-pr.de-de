---
title: Profilerstellung mit Unreal Insights
description: Erfahren Sie, wie Sie Unreal Insights auf HoloLens 2 verwenden.
author: sajidfarooq
ms.author: v-hferrone
ms.date: 12/10/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Entwicklung, Anstößige, unreale Einblicke, Dokumentation, Leitfäden, Features, Hologramme, Spieleentwicklung, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: a13655f394b4d2531ab2ae99ee21ebe9185ebe227ef07a16e3ca54eae9375ee2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228598"
---
# <a name="profiling-with-unreal-insights"></a>Profilerstellung mit Unreal Insights 

[Unreal Insights](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html) ist ein Profilerstellungssystem, das Daten von der Unreal-Engine sammelt, analysiert und visualisiert. Das Profilerstellungssystem kann Ihnen dabei helfen, Optimierungsengpässe und Bereiche zu finden, in denen die Leistung Ihrer Apps einen Leistungsschub erzielen kann. Normalerweise aktivieren Sie Unreal Insights direkt über den Editor, aber für HoloLens 2 müssen Sie die Befehlszeile verwenden.  

## <a name="setup"></a>Setup

Mit Unreal können Sie ein benutzerdefiniertes Profil im starter HoloLens mit den Befehlszeilenparametern erstellen und konfigurieren, die Unreal Insights aktivieren.

1.  Suchen Sie die IP-Adresse Ihres Computers mithilfe des Befehls **ipconfig** an der Eingabeaufforderung. Die IP-Adresse ist die IPv4-Adresse, die von ipconfig aufgelistet wird. Beachten Sie dies für einen späteren Zeitpunkt, wenn Sie Befehlszeilenparameter festlegen.

> [!IMPORTANT]
> Wenn Sie sich hinter einem VPN befindet, müssen Sie möglicherweise stattdessen die ip-Adresse angeben, die über das VPN bereitgestellt wird.

![Screenshot der Befehlszeilenergebnisse für den Befehl "ipconfig"](images/unreal-insights-img-01.png)

2.  Wechseln Sie zum oberen Rand des Unreal Engine-Bereichs, und öffnen **Sie Geräte-Manager** unter der Schaltfläche **Starten:**

![Screenshot der Startoptionen mit hervorgehobener Option "Geräte-Manager"](images/unreal-insights-img-02.png)

3.  Wählen Sie im Geräte-Manager die Option **Nicht aufgelistetes Gerät hinzufügen** aus:

![Screenshot: Geöffneter Geräte-Manager in der Unreal-Engine](images/unreal-insights-img-03.png)

4. Klicken Sie auf **Plattform auswählen,** und wählen Sie **HoloLens** aus:

![Screenshot der Dropdownliste "Nicht aufgelistetes Gerät hinzufügen" mit hervorgehobener HoloLens](images/unreal-insights-img-04.png)

5.  Wenn Sie IPoverUSB verwenden, geben Sie 127.0.0.1:10080 als Gerätebezeichner ein. Geben Sie Ihren HoloLens Benutzer und ihr Kennwort in die entsprechenden Felder ein, und geben Sie **den Anzeigenamen** nach Belieben ein.

> [!IMPORTANT]
> Der Gerätebezeichner ist die IP-Adresse des HoloLens, NICHT des Computers, auf dem Unreal ausgeführt wird, Insights Sie in Schritt 1 gefunden haben.

![Screenshot von HoloLens Gerätedetails im Geräte-Manager](images/unreal-insights-img-05.png)

6.  Wählen Sie **Hinzufügen** aus, und Ihre HoloLens sollte in der Geräteliste des Geräte-Managers angezeigt werden:

![Screenshot: HoloLens der Geräteliste hinzugefügt](images/unreal-insights-img-06.png)

## <a name="launch"></a>Starten

1. Öffnen **Sie Project Startprogramm** im Bereich UE4 unter der Schaltfläche **Starten:**

![Screenshot der Startoptionen mit hervorgehobener Projektstartoption](images/unreal-insights-img-07.png)

2. Wählen Sie die **+** Schaltfläche aus, um unter **Benutzerdefinierte Startprofile** ein benutzerdefiniertes Profil zu erstellen. Nach der Erstellung können Sie dieses Profil später jederzeit bearbeiten:

![Screenshot des Projektstarters mit hervorgehobenen benutzerdefinierten Startprofilen](images/unreal-insights-img-08.png)

3. Wählen Sie auf dem HoloLens benutzerdefinierten Startprofil die Schaltfläche **Profil bearbeiten** aus, und konfigurieren Sie Folgendes:
    * Wählen Sie **Cook** to **By the Book** aus, um das Kopieren auf das Gerät zu aktivieren.
    * Möglicherweise sollten Sie im Abschnitt **Archiv** die Überprüfung **Möchten Sie archivieren?** aktivieren, um die generierte APPXBUNDLE-Datei beizubehalten, anstatt sie zu löschen, um Speicherplatz zu sparen. Geben Sie einen Speicherort für die APPXBUNDLE-Datei an, und wechseln Sie bei Bedarf zu einem Entwicklungsbuild.

![Screenshot der Cookoptionen in der Profilkonfiguration mit Cook durch das Buch und hervorgehobener HoloLens](images/unreal-insights-img-09.png)

4. Legen **Sie Wie möchten Sie den Build bereitstellen?** auf Auf Gerät kopieren **fest,** um den Abschnitt **Starten** der Benutzeroberfläche zu aktivieren:

![Screenshot des Projektstarters mit hervorgehobenen Bereitstellungsoptionen mit hervorgehobener Option "Auf Gerät kopieren"](images/unreal-insights-img-10.png)

5. Legen Sie **zusätzliche Befehlszeilenparameter** im Abschnitt **Launch** fest. Die Parameter werden in eine ue4commandline.txt-Datei geschrieben, in das Paket gepackt und beim Start verwendet. 
    <!-- TODO: Need more detail on what this parameter does and where to find others. -->
    * Probieren Sie diese zunächst aus: **-tracehost=IP_OF_YOUR_PC -trace=Log,Bookmark,Frame,CPU,GPU,LoadTime,File,Net**
    * Eine vollständige Liste der verfügbaren Startparameter finden Sie in der Referenzdokumentation zu [Unreal Insights](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html).

> [!NOTE]
> "IP_OF_YOUR_PC" ist die IP-Adresse, die wir in Schritt 1 gefunden haben. Dies ist die IP-Adresse des Computers, auf dem Unreal Insights ausgeführt wird, NICHT die IP-Adresse des HoloLens.

> [!IMPORTANT]
> Ablaufverfolgungen können sehr schnell groß werden. Aktivieren Sie nur die Kanäle, die Sie benötigen, um die Größe der Ablaufverfolgung gering zu halten.

![Screenshot der Startkonfigurationsoptionen](images/unreal-insights-img-11.png)

6. Starten Sie Unreal Insights VOR dem Start der App, andernfalls kann Unreal Insights nicht ordnungsgemäß vor der App initialisiert werden:
    * Die ausführbare Datei unreal Insights wird im Ordner der Binärdateien-Engine gespeichert, in der Regel wie folgt: "C:\Programme\Epic Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe"

![Screenshot der ausführbaren Unreal Insights-Datei, die ausgeführt wird](images/unreal-insights-img-12.png)

6.  Wählen Sie **Zurück** aus, um zum Stamm des **Dialogfelds "Project Startprogramm"** zurückzukehren.
7.  Klicken Sie im Editor im benutzerdefinierten Startprofil auf **Starten.**

![Screenshot von benutzerdefinierten Startprofilen](images/unreal-insights-img-13.png)

8.  Sehen Sie sich an, wie Ihr Projekt gepackt, auf Ihrem Gerät installiert und gestartet wird.

## <a name="profiling"></a>Profilerstellung

Wählen Sie in Unreal Insights die **Liveverbindung** mit Ihrem Gerät aus, um die Profilerstellung zu starten.

Das benutzerdefinierte Profil wird von Projekten gemeinsam genutzt. Von hier aus können Sie das von Ihnen erstellte benutzerdefinierte Profil verwenden, anstatt dies jedes Mal tun zu müssen. Sie müssen die Verbindung mit dem Gerät nur jedes Mal neu erstellen, wenn Sie Unreal mit den Schritten 3 bis 6 im [Setupabschnitt](#setup)starten.

## <a name="see-also"></a>Siehe auch
* [Unreal Insights-Dokumentation](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/index.html)

