---
title: Erste Schritte mit OpenXR
description: Beginnen Sie mit der Verwendung des portablen openxr-API-Standards für Windows Mixed Reality und hololens 2-Headsets.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: Openxr, Khronos, basicxrapp, Windows Mixed Reality, openxr Entwicklertools, DirectX, Native, Native APP, Custom Engine, Middleware, Getting Started, 101, Preview Extensions, openxr Runtime Version, Systemstatus
ms.openlocfilehash: a641512bf36f2d791c009e6dfa83c1f9bd797547
ms.sourcegitcommit: c199872c11adae7de24929ed043ea90dea087b3e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903143"
---
# <a name="getting-started-with-openxr"></a>Erste Schritte mit OpenXR

Sie können mit OpenXR auf einem immersiven HoloLens 2- oder Windows Mixed Reality-Headset auf dem Desktop entwickeln.  Wenn Sie keinen Zugriff auf ein Headset haben, können Sie stattdessen den hololens 2-Emulator oder den Windows Mixed Reality-Simulator verwenden.

## <a name="getting-started-with-openxr-for-hololens-2"></a>Getting Started with openxr for hololens 2

So beginnen Sie mit der Entwicklung von openxr-Anwendungen für hololens 2:

1. Richten Sie einen hololens 2 ein, oder befolgen Sie die Anweisungen, um [eine aktuelle Version des hololens 2-Emulators zu installieren](../platform-capabilities-and-apis/using-the-hololens-emulator.md).  Wenn Ihr Gerät vor kurzem aktualisiert wurde oder wenn Sie ein Aktuelles emulatorimage verwenden, sollte openxr 1,0 bereits einsatzbereit sein.
1. Um sicherzustellen, dass Sie über die neueste openxr-Laufzeit mit allen vorhandenen [Erweiterungen](openxr.md#roadmap) verfügen, starten Sie die **Store** -APP innerhalb des Geräts oder Emulators, öffnen Sie das Menü in der oberen rechten Ecke, klicken Sie auf **Downloads und Updates** , und klicken Sie auf **Updates erhalten** .  Dadurch wird sichergestellt, dass die openxr-Laufzeit auf den hololens auf dem neuesten Stand ist.  Beachten Sie Folgendes: Wenn Sie den Emulator verwenden, wird das Emulatorbild jedes Mal zurückgesetzt, wenn Sie es starten. Daher sollten Sie sicherstellen, dass Sie über [die neueste Version des hololens 2-Emulatorbilds](../platform-capabilities-and-apis/using-the-hololens-emulator.md)verfügen.

## <a name="getting-started-with-openxr-for-windows-mixed-reality-headsets"></a>Einstieg in openxr für Windows Mixed Reality-Headsets

So beginnen Sie mit der Entwicklung von openxr-Anwendungen für immersive Windows Mixed Reality-Headsets:

1. Stellen Sie sicher, dass mindestens das Windows 10-Update von Mai 2019 (1903) ausgeführt wird. Dies ist die Mindestanforderung für Endbenutzer von Windows Mixed Reality, openxr-Anwendungen auszuführen.  Wenn Sie eine frühere Version von Windows 10 verwenden, können Sie ein Upgrade mit dem <a href="https://www.microsoft.com/software-download/windows10" target="_blank">Windows 10 Update Assistant</a>durchführen.
2. Richten Sie ein Windows Mixed Reality-Headset ein, oder befolgen Sie die Anweisungen zum [Aktivieren des Windows Mixed Reality-Simulators](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md).

Das ist alles!  Die Windows Mixed Reality openxr-Laufzeit wird installiert und automatisch für alle Windows Mixed Reality-Benutzer aktiviert.  Der Microsoft Store speichert die Laufzeit dann auf dem neuesten Stand.

Wenn Sie die Windows Mixed Reality openxr-Laufzeit erneut aktivieren müssen, starten Sie das Mixed Reality-Portal über das Startmenü, und klicken Sie im Banner am oberen Rand des Fensters auf "reparieren".  Wenn diese Schaltfläche fehlt, ist die openxr-Laufzeit bereits aktiv.<br>

## <a name="getting-the-openxr-developer-tools-for-windows-mixed-reality"></a>Die openxr-Entwicklertools für die gemischte Realität von Windows

Um die Windows Mixed Reality openxr-Laufzeit auszuprobieren, können Sie die <a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">openxr-Entwicklertools für die Windows Mixed Reality-App</a>installieren.  Diese APP bietet eine Demo Szene, die verschiedene Features von openxr sowie eine Seite mit dem System Status ausführt, die wichtige Informationen zur aktiven Laufzeit und zum aktuellen Headset bereitstellt.

Wenn Sie den hololens 2-Emulator verwenden, ist die einfachste Möglichkeit zum Installieren des openxr-Entwicklertools für Windows Mixed Reality die Verwendung des [Windows-Geräte Portals](../platform-capabilities-and-apis/using-the-windows-device-portal.md), indem Sie zur Seite "openxr" navigieren und dann unter "Entwickler Features" auf die Schaltfläche "installieren" klicken. (dies funktioniert auch auf einem physischen hololens 2-Gerät.)

![Openxr Entwicklertools für Windows Mixed Reality-App](images/mixed-reality-openxr-developer-tools.png)

## <a name="building-a-sample-openxr-app"></a>Aufbauen einer openxr-Beispiel-App

Stellen Sie sicher, dass Sie [die Tools installieren, die](../install-the-tools.md) Sie für die openxr-Entwicklung benötigen, sofern noch nicht geschehen.

Das <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a>-Projekt zeigt ein einfaches OpenXR-Beispiel mit zwei Visual Studio-Projektdateien, eine für eine Win32-Desktop-App und eine für eine UWP HoloLens 2-App.  Da die Projekt Mappe ein hololens-UWP-Projekt enthält, benötigen Sie die [Arbeitsauslastung der universelle Windows-Plattform Entwicklung](../install-the-tools.md#installation-checklist) , die in Visual Studio installiert ist, um Sie vollständig zu öffnen.

Beachten Sie, dass die Win32-und UWP-Projektdateien aufgrund von Unterschieden bei der Paket Erstellung und der Bereitstellung getrennt sind. der app-Code in jedem Projekt ist jedoch fast identisch.

Nach dem Aufbau eines openxr Win32-Desktops. EXE, Sie können es mit einem VR-Headset auf jeder Desktop-VR-Plattform verwenden, die openxr unterstützt, unabhängig davon, ob es sich um ein Windows Mixed Reality-Headset oder ein anderes Headset handelt.

Nachdem Sie ein openxr UWP-App-Paket aufgebaut haben, können Sie [Dieses Paket](../platform-capabilities-and-apis/using-visual-studio.md) entweder auf einem hololens 2-Gerät oder auf dem hololens 2-Emulator bereitstellen.

## <a name="learning-the-openxr-api"></a>Erlernen der openxr-API

Eine Tour durch die openxr-API finden Sie in diesem 60-minütigen Video, das den Code des <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">basicxrapp</a> -Beispiels in Visual Studio erläutert.  Das Video zeigt, wie die einzelnen Hauptkomponenten der openxr-API in ihrer eigenen Engine verwendet werden können, und es werden auch einige der Anwendungen veranschaulicht, die heute auf openxr basieren:
>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/OpenXR-Cross-platform-native-mixed-reality/player?format=ny]

## <a name="integrate-the-openxr-loader-into-a-project"></a>Integrieren des openxr-Lade Moduls in ein Projekt

Für den Einstieg in openxr in einem vorhandenen Projekt fügen Sie das openxr-Lade Modul ein.  Das Lade Modul ermittelt die aktive openxr-Laufzeit auf dem Gerät und ermöglicht den Zugriff auf die Kernfunktionen und Erweiterungsfunktionen, die es implementiert.

Sie können entweder auf [das offizielle openxr nuget-Paket](#reference-official-openxr-nuget-package) aus Ihrem Visual Studio-Projekt verweisen oder [die offizielle openxr-Lade Programmquelle](#include-official-openxr-loader-source)  aus dem GitHub-Repository Khronos einschließen.  Beide Ansätze erhalten Zugriff auf openxr 1,0 Core-Features sowie veröffentlichte `KHR` `EXT` `MSFT` Erweiterungen und Erweiterungen.

Wenn Sie auch mit Erweiterungen experimentieren möchten `MSFT_preview` , können Sie die Vorschau von [openxr-Headern](#using-preview-extensions) aus dem GitHub-Repository mit gemischter Realität kopieren.

### <a name="reference-official-openxr-nuget-package"></a>Verweis auf das offizielle openxr-nuget-Paket

Das <a href="https://www.nuget.org/packages/OpenXR.Loader/" target="_blank"> **openxr. Loader** -nuget-Paket</a> ist die einfachste Möglichkeit, auf ein vorab erstelltes openxr-Lade Modul zu verweisen. DLL in Ihrer Visual Studio C++-Lösung.  Dadurch erhalten Sie Zugriff auf openxr 1,0 Core-Features sowie veröffentlichte `KHR` `EXT` `MSFT` Erweiterungen und Erweiterungen.

So fügen Sie eine openxr. Loader-nuget-Paket Referenz zu Ihrer Visual Studio C++-Projekt Mappe hinzu:
1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, das openxr verwendet, und wählen Sie **nuget-Pakete verwalten...** aus.
1. Wechseln Sie zur Registerkarte **Durchsuchen** , und suchen Sie nach **openxr. Loader** .
1. Wählen Sie das Paket **openxr. Loader** aus, und klicken Sie im Detailbereich auf der rechten Seite auf installieren.
1. Klicken Sie auf OK, um die Änderungen am Projekt zu übernehmen.
1. Fügen Sie `#include <openxr/openxr.h>` einer Quelldatei hinzu, um mit der Verwendung der openxr-API zu beginnen.

Ein Beispiel für die openxr-API in Aktion finden Sie in der <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">basicxrapp</a> -Beispiel-app.

### <a name="include-official-openxr-loader-source"></a>Offizielle openxr-Ladedienst Quelle einbeziehen

Wenn Sie das Lade Modul selbst erstellen möchten, z. b. um das zusätzliche Lade Modul zu vermeiden. DLL, Sie können die offiziellen Khronos openxr-Lade Quell Quellen in Ihr Projekt abrufen.  Dadurch erhalten Sie Zugriff auf openxr 1,0 Core-Features sowie veröffentlichte `KHR` `EXT` `MSFT` Erweiterungen und Erweiterungen.

Befolgen Sie zum Einstieg die Anweisungen im Repository " <a href="https://github.com/KhronosGroup/OpenXR-SDK" target="_blank">Khronos openxr-SDK" auf GitHub</a>.  Das Projekt ist so eingerichtet, dass es mit CMake erstellt wird. Wenn Sie MSBuild verwenden, müssen Sie den Code in Ihr eigenes Projekt kopieren.

## <a name="using-preview-extensions"></a>Verwenden von Vorschau Erweiterungen

Die `MSFT_preview` Erweiterungen in der [Erweiterungs Roadmap](openxr.md#roadmap) sind experimentelle Lieferanten Erweiterungen, die in der Vorschau angezeigt werden, um Feedback zu sammeln.  Diese Erweiterungen gelten nur für Entwickler Geräte und werden entfernt, wenn die echte Erweiterung ausgeliefert wird.

Wenn Sie die verfügbaren Erweiterungen testen möchten, führen Sie `MSFT_preview` die folgenden Schritte aus, um Ihr Projekt zu aktualisieren:
1. Befolgen Sie einen der oben genannten Vorgehensweisen, um ein openxr-Lade Modul in Ihr Projekt zu integrieren.
1. Ersetzen Sie die openxr-Standard Header in Ihrem Projekt durch die <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/openxr_preview/include/openxr" target="_blank">Vorschau Header aus dem Mixed Reality openxr-Repository auf GitHub</a>.

So aktivieren Sie die Vorschau Erweiterungs Unterstützung auf ihren Ziel-hololens 2 oder auf dem Desktop-PC:
  1. Um sicherzustellen, dass Sie über die neueste openxr-Laufzeit mit allen vorhandenen [Erweiterungen](openxr.md#roadmap) verfügen, starten Sie die Store-App aus dem Zielgerät oder Emulator, öffnen Sie das Menü in der oberen rechten Ecke, klicken Sie auf **Downloads und Updates** , und klicken Sie auf **Updates** herunter **Laden** .
  1. Installieren Sie die <a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">openxr-Entwicklertools für die Windows Mixed Reality-App</a> vom Microsoft Store auf dem Zielgerät, und führen Sie Sie aus.
  1. Navigieren Sie zur Registerkarte **Entwicklereinstellungen** , und aktivieren Sie **neueste Vorschauversion openxr Runtime verwenden** .  Dadurch wird die Vorschau Laufzeit auf Ihrem Gerät aktiviert, für die Vorschau Erweiterungen aktiviert sind.
     ![Openxr Entwicklertools für Windows Mixed Reality-App Developer Settings-Registerkarte](images/mixed-reality-openxr-developer-tools-settings.png)
  1. Vergewissern Sie sich, dass die auf der Registerkarte **System Status** des [openxr-Entwicklertools für Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) angezeigte **Laufzeitversion** nun mit der erforderlichen Version der Vorschau Erweiterungen übereinstimmt, die Sie ausprobieren möchten.  Wenn dies der Fall ist, sollte die Erweiterung in der Liste **Erweiterungen** angezeigt werden.  Beachten Sie, dass die Vorschau Erweiterung entfernt wird, sobald eine stabile Erweiterung verfügbar ist.<br />
     ![Openxr Entwicklertools für Windows Mixed Reality-app System Status (Registerkarte)](images/mixed-reality-openxr-developer-tools-status.png)

Eine Dokumentation zu diesen Vorschau Erweiterungen und Beispielen zur Verwendung finden Sie im Repository " <a href="https://github.com/microsoft/OpenXR-MixedReality#openxr-preview-extensions" target="_blank">Mixed Reality openxr</a> ".

## <a name="troubleshooting"></a>Problembehandlung

Wenn Sie Probleme mit der openxr-Entwicklung haben, sehen Sie sich unsere [Tipps zur Problem](openxr-troubleshooting.md)Behandlung an.