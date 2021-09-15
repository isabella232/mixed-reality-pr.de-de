---
title: Profilerstellung mit Unreal Insights
description: Erfahren Sie, wie Sie Unreal Insights auf HoloLens 2.
author: sajidfarooq
ms.author: v-hferrone
ms.date: 12/10/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Entwicklung, profling, Unreal Insights, Dokumentation, Leitfäden, Features, Hologramme, Spieleentwicklung, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: a77d7795cd7e8c281ebaa2ef89bb6bc9152f5f9c
ms.sourcegitcommit: 5d13ff165f4d08a3b028935fb39539a45a30f7e8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/15/2021
ms.locfileid: "127779385"
---
# <a name="profiling-with-unreal-insights"></a>Profilerstellung mit Unreal Insights

[Unreal Insights](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html) ist ein Profilerstellungssystem, das Daten von der Unreal Engine sammelt, analysiert und visualisiert. Das Profilerstellungssystem kann Ihnen helfen, Optimierungsengpässe und Bereiche zu finden, in denen die Leistung Ihrer Apps einen Schub nutzen könnte. Normalerweise aktivieren Sie unreal Insights direkt über den Editor, aber für HoloLens 2 müssen Sie die Befehlszeile verwenden.

## <a name="setup"></a>Einrichten

Mit Unreal können Sie ein "benutzerdefiniertes Profil" im HoloLens-Startfeld mit den Befehlszeilenparametern erstellen und konfigurieren, die unreal Insights.

1. Suchen Sie die IP-Adresse Ihres Computers mithilfe des **Befehls ipconfig** an der Eingabeaufforderung. Die IP-Adresse ist die IPv4-Adresse, die von ipconfig aufgelistet wird. Beachten Sie dies zu einem späteren Zeitpunkt, wenn Sie Befehlszeilenparameter festlegen.

> [!IMPORTANT]
> Wenn Sie sich hinter einem VPN befingen, müssen Sie möglicherweise stattdessen die über das VPN bereitgestellte IP-Adresse angeben.

![Screenshot der Befehlszeilenergebnisse für den Befehl "ipconfig"](images/unreal-insights-img-01.png)

2. Öffnen **Project Einstellungen** der Symbolleiste "Bearbeiten" im Haupt-Editor-Fenster.

![Screenshot der Dropdownliste "Bearbeiten" mit Project Einstellungen hervorgehoben](images/unreal-insights-img-15.png)

3. Scrollen Sie im linken Bereich nach unten, bis Sie den **Header Plattformen** finden, und wählen **Sie HoloLens.**

![Screenshot des Abschnitts "Plattformen" im linken Project Einstellungen mit hervorgehobener HoloLens](images/unreal-insights-img-15.png)

4. Vergewissern Sie **sich, dass** im Abschnitt Funktionen die Option "Internetclient", "Internetclientserver" und "Clientserver für private Netzwerke" ausgewählt sind.

![Screenshot der Optionen "Funktionen" mit ausgewählter Option "Internetclient", "Internetclientserver" und "Clientserver für private Netzwerke"](images/unreal-insights-img-14.png)

## <a name="launch"></a>Starten

1. Öffnen **Project Startprogramm** im UE4-Bereich unter der **Schaltfläche Starten:**

![Screenshot der Startoptionen mit hervorgehobener Projektstarter](images/unreal-insights-img-07.png)

2. Wählen Sie die **+** Schaltfläche aus, um unter Benutzerdefinierte Startprofile ein **benutzerdefiniertes Profil zu erstellen.** Nach dem Erstellen können Sie dieses Profil später immer bearbeiten:

![Screenshot des Projektstarters mit hervorgehobenen benutzerdefinierten Startprofilen](images/unreal-insights-img-08.png)

3. Wählen **Sie im benutzerdefinierten** Startprofil HoloLens Schaltfläche Profil bearbeiten aus. Aktivieren Sie **im Abschnitt Build** das Kontrollkästchen Build **UAT,** und legen Sie **zusätzliche Befehlszeilenparameter fest.**
   - Probieren Sie die folgenden Schritte aus: **-tracehost=IP_OF_YOUR_PC -trace=Log,Bookmark,Frame,CPU,GPU,LoadTime,File,Net**
   - Eine vollständige Liste der verfügbaren Startparameter finden Sie in der [Unreal-Insights Referenzdokumentation.](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html)

> [!NOTE]
> "IP_OF_YOUR_PC" ist die IP-Adresse, die wir in Schritt 1 gefunden haben. Dies ist die IP-Adresse des Computers, auf dem Unreal Insights, NICHT die IP-Adresse des HoloLens.

> [!IMPORTANT]
> Ablaufverfolgungen können sehr schnell groß werden. Aktivieren Sie nur die Kanäle, die Sie benötigen, um die Größe der Ablaufverfolgung gering zu halten.

![Screenshot der Buildoptionen in der Profilkonfiguration](images/unreal-insights-img-17.png)

4. Wählen **Sie Cook** to By the Book **(Nach dem Buch)** aus, um das Kopieren auf das Gerät zu aktivieren. Vergewissern Sie sich, dass Ihre Karten in **Der Karten.**

![Screenshot der Cookoptionen in der Profilkonfiguration mit "cook" im Buch und HoloLens hervorgehoben](images/unreal-insights-img-09.png)

5. Legen **Sie Wie möchten Sie den Build packen?** auf Paket & lokal **fest.** Notieren Sie sich den dateipfad, den Sie auswählen, da Sie diesen später benötigen.

![Screenshot der Paketoptionen in der Profilkonfiguration, die auf "Lokal verpacken" und "lokal speichern" festgelegt sind](images/unreal-insights-img-18.png)

6. Legen **Sie Wie möchten Sie den Build bereitstellen?** auf Nicht bereitstellen **fest.**

![Screenshot der Bereitstellungsoptionen in der Profilkonfiguration, bei der die Bereitstellung auf "Nicht bereitstellen" festgelegt ist](images/unreal-insights-img-19.png)

8. Wählen **Sie Zurück** aus, um zum Stammverzeichnis des Dialogfelds Project Startprogramm werden. 
9. Klicken Sie im Editor auf **Starten für Ihr** benutzerdefiniertes Startprofil.

![Screenshot von benutzerdefinierten Startprofilen](images/unreal-insights-img-13.png)

10. Sehen Sie sich an, wie Ihr Projekt erstellt wird, und stellen Sie dann appxbundle (im Paketpfad aus Schritt 5) über das Geräteportal HoloLens App-App bereit.

11. Starten Sie unreal Insights. Die ausführbare Insights unreal-Datei wird im Ordner der Binärdateien-Engine gespeichert, in der Regel wie folgt: "C:\Programme\Epic Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe"

![Screenshot der ausführbaren Unreal Insights-Datei, die ausgeführt wird](images/unreal-insights-img-12.png)

12. Starten Sie die App auf Ihrem HoloLens.

## <a name="profiling"></a>Profilerstellung

Wählen Sie in unreal Insights die **Liveverbindung** mit Ihrem Gerät aus, um die Profilerstellung zu starten.

Das benutzerdefinierte Profil wird von Projekten gemeinsam genutzt. Von hier aus können Sie das von Ihnen erstellte benutzerdefinierte Profil verwenden, anstatt dies jedes Mal tun zu müssen. Sie müssen die Verbindung mit dem Gerät nur bei jedem Start von Unreal mit den Schritten 3 bis 6 im [Setupabschnitt neu erstellen.](#setup)

## <a name="see-also"></a>Weitere Informationen

- [Unreal Insights Dokumentation](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/index.html)
