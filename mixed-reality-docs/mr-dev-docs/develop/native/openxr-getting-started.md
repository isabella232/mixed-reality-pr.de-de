---
title: Erste Schritte mit OpenXR
description: Erste Schritte mit dem portablen OpenXR-API-Standard Windows Mixed Reality und HoloLens 2 Headsets.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, BasicXRApp, Windows Mixed Reality, OpenXR Entwicklertools, DirectX, native, native App, benutzerdefinierte Engine, Middleware, erste Schritte, 101, Vorschauerweiterungen, OpenXR-Runtimeversion, Systemstatus
ms.openlocfilehash: 6d334b491d231ab5987dd1bc6a3eb43f5e0fe30a82c6525bca1935fbf1cd83bb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189152"
---
# <a name="getting-started-with-openxr"></a>Erste Schritte mit OpenXR

Sie können mit OpenXR auf einem immersiven HoloLens 2- oder Windows Mixed Reality-Headset auf dem Desktop entwickeln.  Wenn Sie keinen Zugriff auf ein Headset haben, können Sie stattdessen das HoloLens 2 Emulator oder den Windows Mixed Reality Simulator verwenden.

## <a name="getting-started-with-openxr-for-hololens-2"></a>Erste Schritte mit OpenXR für HoloLens 2

So beginnen Sie mit der Entwicklung von OpenXR-Anwendungen für HoloLens 2:

1. Richten Sie einen HoloLens 2 ein, oder befolgen Sie die Anweisungen zum Installieren einer aktuellen Version des HoloLens 2 [Emulators.](../platform-capabilities-and-apis/using-the-hololens-emulator.md) OpenXR 1.0 sollte bereits einsatzbereit sein, wenn Sie ein aktuelles Emulatorimage verwenden oder das Gerät sein Betriebssystem aktualisiert hat.
2. Stellen Sie sicher, dass Sie über die [](openxr.md#roadmap) neueste OpenXR-Runtime mit allen verfügbaren Erweiterungen Store über das Gerät oder den Emulator. 
    * Öffnen Sie das Menü in der oberen rechten Ecke, wählen Sie **Downloads und Updates** und dann Updates herunterladen **aus.**  

> [!NOTE]
> Wenn Sie den Emulator verwenden, wird das Emulatorimage jedes Mal zurückgesetzt, wenn Sie es starten. Daher ist es am besten, nur sicherzustellen, dass Sie über die neueste Version des HoloLens 2-Emulatorimages [verfügen.](../platform-capabilities-and-apis/using-the-hololens-emulator.md)

## <a name="getting-started-with-openxr-for-windows-mixed-reality-headsets"></a>Erste Schritte mit OpenXR für Windows Mixed Reality Headsets

So beginnen Sie mit der Entwicklung von OpenXR-Anwendungen für immersive Windows Mixed Reality Headsets:

1. Stellen Sie sicher, dass Sie mindestens den Windows 10 May 2019 Update (1903) ausführen. Dies ist die Mindestanforderung, Windows Mixed Reality Endbenutzer OpenXR-Anwendungen ausführen müssen.  Wenn Sie eine frühere Version von Windows 10, können Sie ein Upgrade mithilfe des Windows 10 <a href="https://www.microsoft.com/software-download/windows10" target="_blank">Update-Assistenten durchführen.</a>
2. Richten Sie ein Windows Mixed Reality Headset ein, oder befolgen Sie die Anweisungen zum [Aktivieren des Windows Mixed Reality Simulators.](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

Das ist alles!  Die Windows Mixed Reality OpenXR-Runtime wird installiert und für alle Benutzer automatisch Windows Mixed Reality werden.  Der Microsoft Store hält dann die Laufzeit auf dem neuesten Stand.

Um die Windows Mixed Reality OpenXR Runtime erneut zu aktivieren, starten Sie Mixed Reality-Portal im Startmenü, und wählen Sie oben im Fenster "Korrigieren" aus.  Wenn diese Schaltfläche fehlt, ist die OpenXR-Runtime bereits aktiv.<br>

## <a name="getting-the-openxr-developer-tools-for-windows-mixed-reality"></a>Abrufen der OpenXR-Entwicklertools für Windows Mixed Reality

Zum Testen der Windows Mixed Reality OpenXR Runtime können Sie die <a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">OpenXR-Entwicklertools für Windows Mixed Reality installieren.</a>  Diese App bietet eine Demo verschiedener OpenXR-Features sowie eine Seite "Systemstatus" mit wichtigen Informationen zur aktiven Laufzeit und zum aktuellen Headset.

Wenn Sie den HoloLens 2-Emulator verwenden, können Sie openXR Entwicklertools für Windows Mixed Reality am einfachsten über [die](../platform-capabilities-and-apis/using-the-windows-device-portal.md)Windows Geräteportal. Navigieren Sie zur Seite "OpenXR", und klicken Sie dann unter "Entwicklerfeatures" auf die Schaltfläche "Installieren", was auch auf physischen HoloLens 2 funktioniert.

![OpenXR-Entwicklertools für Windows Mixed Reality-App](images/mixed-reality-openxr-developer-tools.png)

## <a name="building-a-sample-openxr-app"></a>Erstellen einer OpenXR-Beispiel-App

Stellen Sie [sicher, dass Sie die Tools](../install-the-tools.md) installieren, die Sie für die OpenXR-Entwicklung benötigen, sofern noch nicht vorhanden.

Das <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp-Projekt</a> zeigt ein einfaches OpenXR-Beispiel mit Win32- und UWP-HoloLens 2-Projektdateien in Visual Studio. Da die Projektmappe ein HoloLens UWP-Projekt enthält, muss die Workload Entwicklung für universelle [Windows-Plattform](../install-the-tools.md#installation-checklist) in Visual Studio installiert sein, um sie vollständig zu öffnen.

Obwohl die Win32- und UWP-Projektdateien aufgrund von Unterschieden bei der Paketierung und Bereitstellung getrennt sind, ist der App-Code in jedem Projekt fast identisch!

Nachdem Sie eine OpenXR Win32-Desktop-.EXE erstellt haben, können Sie sie mit einem VR-Headset auf jeder Desktop-VR-Plattform verwenden, die OpenXR unabhängig vom Headsettyp unterstützt.

Nachdem Sie ein OpenXR-UWP-App-Paket erstellt haben, können Sie dieses Paket entweder auf einem HoloLens 2-Gerät oder HoloLens 2 Emulator. [](../platform-capabilities-and-apis/using-visual-studio.md)

## <a name="learning-the-openxr-api"></a>Learning der OpenXR-API

Einen Tour durch die OpenXR-API finden Sie in diesem 60-minütigen Video des <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp-Beispiels</a> in Visual Studio.  Das Video zeigt, wie jede der Hauptkomponenten der OpenXR-API in Ihrer eigenen Engine verwendet werden kann, und zeigt auch einige der Anwendungen, die heute auf OpenXR erstellt wurden:

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/OpenXR-Cross-platform-native-mixed-reality/player?format=ny]

## <a name="integrate-the-openxr-loader-into-a-project"></a>Integrieren des OpenXR-Laders in ein Projekt

Um mit OpenXR in einem vorhandenen Projekt zu beginnen, fügen Sie das OpenXR-Lader ein.  Das Lademodul entdeckt die aktive OpenXR-Runtime auf dem Gerät und bietet Zugriff auf die Kernfunktionen und Erweiterungsfunktionen, die es implementiert.

Sie können [auf das offizielle OpenXR-NuGet-Paket](#reference-official-openxr-nuget-package) aus Ihrem Visual Studio-Projekt verweisen oder die offizielle [OpenXR-Laderquelle](#include-official-openxr-loader-source) aus dem Repository des GitHub enthalten.  Bei beiden Ansätzen erhalten Sie Zugriff auf OpenXR 1.0-Kernfeatures sowie auf veröffentlichte `KHR` `EXT` Erweiterungen und `MSFT` .

Wenn Sie auch mit Erweiterungen experimentieren möchten, können Sie `MSFT_preview` [OpenXR-Header](#using-preview-extensions) in der Vorschauversion aus dem Mixed Reality GitHub kopieren.

### <a name="reference-official-openxr-nuget-package"></a>Referenz zum offiziellen OpenXR NuGet Paket

Das <a href="https://www.nuget.org/packages/OpenXR.Loader/" target="_blank"> **OpenXR.Loader NuGet paket**</a> ist die einfachste Möglichkeit, auf ein vordefiniertes OpenXR-Lader-.DLL in Ihrer C++-Projektmappe Visual Studio verweisen.  Dadurch erhalten Sie Zugriff auf OpenXR 1.0-Kernfeatures sowie auf veröffentlichte `KHR` Erweiterungen `EXT` und `MSFT` .

So fügen Sie einen OpenXR.Loader-NuGet Paketverweis zu Ihrer C++Visual Studio Lösung hinzu:
1. Klicken **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, das OpenXR verwenden soll, und wählen **Sie Manage NuGet Packages... (Pakete NuGet verwalten...) aus.**
2. Wechseln Sie zur **Registerkarte Durchsuchen,** und suchen Sie **nach OpenXR.Loader.**
3. Wählen Sie das **OpenXR.Loader-Paket** aus, und wählen Sie im Detailbereich auf der rechten Seite Installieren aus.
4. Wählen Sie OK aus, um die Änderungen an Ihrem Projekt zu akzeptieren.
5. Fügen `#include <openxr/openxr.h>` Sie einer Quelldatei hinzu, um mit der Verwendung der OpenXR-API zu beginnen.

Ein Beispiel für die OpenXR-API in Aktion finden Sie in der <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp-Beispiel-App.</a>

### <a name="include-official-openxr-loader-source"></a>Include official OpenXR loader source (Offizielle OpenXR-Laderquelle enthalten)

Wenn Sie das Lader selbst erstellen möchten, z. B. um das zusätzliche Lader-.DLL zu vermeiden, können Sie die offiziellen Sourcen des OpenXR-Laders von Allemos in Ihr Projekt pullen.  Dadurch erhalten Sie Zugriff auf OpenXR 1.0-Kernfeatures sowie auf veröffentlichte `KHR` Erweiterungen `EXT` und `MSFT` .

Um hier zu beginnen, befolgen Sie die Anweisungen im <a href="https://github.com/KhronosGroup/OpenXR-SDK" target="_blank">OpenXR-SDK-Repository von Gegen GitHub.</a>  Das Projekt ist für die Erstellung mit CMake eingerichtet. Wenn Sie MSBuild verwenden, müssen Sie den Code in Ihr eigenes Projekt kopieren.

## <a name="using-preview-extensions"></a>Verwenden von Vorschauerweiterungen

Bei den erweiterungsbezogenen Erweiterungen handelt es sich um experimentelle Anbietererweiterungen, die in der Vorschau `MSFT_preview` angezeigt werden, um Feedback zu erhalten. [](openxr.md#roadmap)  Diese Erweiterungen sind nur für Entwicklergeräte und werden entfernt, wenn die echte Erweiterung im Versand ist.

Wenn Sie die verfügbaren Erweiterungen ausprobieren `MSFT_preview` möchten, führen Sie die folgenden Schritte aus, um Ihr Projekt zu aktualisieren:
1. Befolgen Sie einen der oben genannten Ansätze, um ein OpenXR-Lader in Ihr Projekt zu integrieren.
2. Ersetzen Sie die OpenXR-Standardheader in Ihrem Projekt durch die Vorschauheader aus dem Mixed Reality <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/openxr_preview/include/openxr" target="_blank">OpenXR-Repository auf GitHub.</a>

So aktivieren Sie die Unterstützung der Vorschauerweiterung auf Ihrem Zielcomputer HoloLens 2 Desktop-PC:
  1. Um sicherzustellen, dass Sie die neueste OpenXR-Runtime mit allen erweiterungen vorhanden haben, starten Sie die **Store-App** auf dem Zielgerät oder Emulator, öffnen Sie das Menü in der oberen rechten Ecke, wählen Sie **Downloads** und Updates und dann **Updates herunterladen aus.** [](openxr.md#roadmap)
  2. Installieren Sie <a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">die OpenXR Entwicklertools for Windows Mixed Reality-App</a> aus Microsoft Store auf dem Zielgerät, und führen Sie sie aus.
  3. Navigieren Sie zur **Registerkarte Developer Einstellungen,** und aktivieren Sie Use latest preview OpenXR runtime (Neueste **Vorschauversion der OpenXR-Runtime verwenden).**  Dadurch wird die Vorschaulaufzeit auf Ihrem Gerät aktiviert, auf dem Vorschauerweiterungen aktiviert sind.
     ![Registerkarte "OpenXR Entwicklertools for Windows Mixed Reality app Developer Einstellungen"](images/mixed-reality-openxr-developer-tools-settings.png)
  4. Vergewissern Sie **sich,** dass die runtime-Version, die auf der Registerkarte **Systemstatus** des [OpenXR Entwicklertools for Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) angezeigt wird, der erforderlichen Version der Vorschauerweiterungen entspricht, die Sie ausprobieren möchten.  Wenn ja, sollte die Erweiterung in der Liste **Erweiterungen angezeigt** werden.  Sobald eine stabile Erweiterung verfügbar ist, wird die Vorschauerweiterung entfernt.<br />
     ![OpenXR Entwicklertools für Windows Mixed Reality-App – Registerkarte "Systemstatus"](images/mixed-reality-openxr-developer-tools-status.png)

Die Dokumentation <a href="https://github.com/microsoft/OpenXR-MixedReality#openxr-preview-extensions" target="_blank">Mixed Reality Vorschauerweiterungen</a> und Beispiele für deren Verwendung finden Sie im OpenXR-Repository.

## <a name="troubleshooting"></a>Problembehandlung

Wenn Sie Probleme beim Einrichten und Ausführen der OpenXR-Entwicklung haben, lesen Sie unsere Tipps [zur Problembehandlung.](openxr-troubleshooting.md)