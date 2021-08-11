---
title: Aktualisieren von 2D UWP-Apps für Windows Mixed Reality
description: In diesem Artikel wird beschrieben, wie Sie Ihre vorhandene 2D Universal Windows Platform-App so aktualisieren, dass sie auf HoloLens immersiven Headsets Windows Mixed Reality wird.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 2D-App, UWP, flache App, HoloLens, immersives Headset, App-Modell, Zurück-Taste, App-Leiste, DPI, Auflösung, Skalierung, Portierung, HoloLens 1. Generation, HoloLens 2, Mixed Reality-Headset, Windows Mixed Reality-Headset, Migration, Windows 10
ms.openlocfilehash: 2b0fa403394432f2cec80e44d27804b07934260e60281f5c70b68c7377d3e55e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115195989"
---
# <a name="updating-2d-uwp-apps-for-windows-mixed-reality"></a>Aktualisieren von 2D UWP-Apps für Windows Mixed Reality

Windows Mixed Reality können Ihre Benutzer Hologramme so sehen, als ob sie sich in der physischen und digitalen Welt direkt um sie herum befingen. Im Kern sind sowohl HoloLens Desktop-PCs, an die Sie immersives Headset-Zubehör anfügen, Windows 10 Geräte. Sie können fast alle UWP-Apps (Universal Windows Platform) in der Store 2D-Apps ausführen.

## <a name="creating-a-2d-uwp-app-for-mixed-reality"></a>Erstellen einer 2D-UWP-App für Mixed Reality

Der erste Schritt beim Übertragen einer 2D-App auf Mixed Reality-Headsets besteht im Ausführen Ihrer App als 2D-Standard-App auf Ihrem Desktopmonitor.

### <a name="building-a-new-2d-uwp-app"></a>Erstellen einer neuen 2D-UWP-App

Um eine neue 2D-App für Mixed Reality zu erstellen, erstellen Sie eine 2D Universal Windows Platform (UWP)-Standard-App. Es sind keine weiteren App-Änderungen erforderlich, damit diese App dann als Slate in Mixed Reality ausgeführt wird.

Informationen zu den ersten Schritte beim Erstellen einer 2D-UWP-App finden Sie im Artikel [Erstellen Ihrer ersten App.](/windows/uwp/get-started/your-first-app)

### <a name="bringing-an-existing-2d-store-app-to-uwp"></a>Verwenden einer vorhandenen 2D-Store-App auf UWP

Wenn Sie bereits über eine 2D-Windows-App im Store verfügen, stellen Sie sicher, dass sie auf die Windows 10 Universal Windows Platform (UWP) abzielen. Im Folgenden finden Sie alle möglichen Ausgangspunkte, die Sie heute mit Ihrer Store-App haben können:
<br>

|  Startpunkt  |  AppX-Manifestplattformziel  |  Wie wird dies universell? | 
|----------|----------|----------|
|  Windows Phone (Silverlight)  |  Silverlight-App-Manifest |  [Migrieren zu WinRT](/previous-versions/windows/apps/dn642486(v=vs.105)) | 
|  Windows Phone 8.1 Universal  |  8.1 AppX-Manifest ohne Plattformziel  |  [Migrieren Ihrer App zur universellen Windows Plattform](/previous-versions/visualstudio/visual-studio-2015/misc/migrate-apps-to-the-universal-windows-platform-uwp) | 
|  Windows Store 8  |  8 AppX-Manifest ohne Plattformziel  |  [Migrieren Ihrer App zur universellen Windows Plattform](/previous-versions/visualstudio/visual-studio-2015/misc/migrate-apps-to-the-universal-windows-platform-uwp) | 
|  Windows Store 8.1 Universal  |  8.1 AppX-Manifest ohne Plattformziel  |  [Migrieren Ihrer App zur universellen Windows Plattform](/previous-versions/visualstudio/visual-studio-2015/misc/migrate-apps-to-the-universal-windows-platform-uwp) | 

Wenn Sie heute über eine 2D-Unity-App **verfügen,** die als Win32-App auf dem PC ( Mac & Linux Standalone Build Target) erstellt wurde, wechseln Sie zum Buildziel der universellen **Windows-Plattform** für Mixed Reality.

Wir werden über Möglichkeiten sprechen, wie Sie Ihre App mithilfe des HoloLens auf Windows. Holographic-Gerätefamilie [unter](#publish-and-maintain-your-universal-app).

### <a name="run-your-2d-app-in-a-windows-mixed-reality-immersive-headset"></a>Ausführen Ihrer 2D-App in einem Windows Mixed Reality immersiven Headset

Wenn Sie Ihre 2D-App auf einem Desktopcomputer bereitgestellt und auf Ihrem Monitor ausprobiert haben, können Sie sie auf einem immersiven Desktop-Headset testen!

Wechseln Sie einfach zum Startmenü im Mixed Reality-Headset, und starten Sie die App von dort aus. Die Desktopshell und die holografische Shell teilen sich denselben Satz von UWP-Apps, sodass die App bereits vorhanden sein sollte, nachdem Sie die Bereitstellung über Visual Studio.

## <a name="targeting-both-immersive-headsets-and-hololens"></a>Ziel sind immersive Headsets und HoloLens

Herzlichen Glückwunsch! Ihre App verwendet jetzt die Windows 10 Universal Windows Platform (UWP).

Ihre App kann jetzt auf den heutigen Windows-Geräten wie Desktop, Mobil, Xbox, Windows Mixed Reality immersive Headsets, HoloLens und zukünftigen geräten ausgeführt Windows werden. Um jedoch alle diese Geräte als Ziel zu verwenden, müssen Sie sicherstellen, dass Ihre App auf die Windows. Universelle Gerätefamilie.

### <a name="change-your-device-family-to-windowsuniversal"></a>Ändern Sie Ihre Gerätefamilie in Windows. Universal

Lassen Sie uns nun in Ihr AppX-Manifest springen, um sicherzustellen, dass Ihre Windows 10 UWP-App auf dem HoloLens:
* Öffnen Sie die Projektmappendatei Ihrer App **mit** Visual Studio und navigieren Sie zum App-Paketmanifest.
* Klicken Sie in Ihrer Projektmappe mit der rechten Maustaste auf die Datei **Package.appxmanifest,** und wechseln Sie **zu Code anzeigen.**<br>
  ![package.appxmanifest in Projektmappen-Explorer](images/openappxmanifest-500px.png)<br>
* Stellen Sie sicher, dass Ihre Zielplattform Windows. Universell im Abschnitt "dependencies"
  ```
  <Dependencies>
    <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
  </Dependencies>
  ```
* Speichern!

Wenn Sie Visual Studio für Ihre Entwicklungsumgebung nicht verwenden, können Sie **AppXManifest.xml** im Text-Editor Ihrer Wahl öffnen, um sicherzustellen, dass Sie die **Windows. Universal** *TargetDeviceFamily*.

### <a name="run-in-the-hololens-emulator"></a>Führen Sie im HoloLens Emulator

Nun, da Ihre UWP-App auf "Windows. Universell" erstellen wir Ihre App und führen sie im [HoloLens Emulator.](../platform-capabilities-and-apis/using-the-hololens-emulator.md)
* Stellen Sie sicher, dass [Sie die -HoloLens Emulator.](../install-the-tools.md)
* Wählen Visual Studio die **x86-Buildkonfiguration** für Ihre App aus.

  ![x86-Buildkonfiguration in Visual Studio](../platform-capabilities-and-apis/images/x86setting.png)<br>
* Wählen Sie im Dropdownmenü für das Bereitstellungsziel **HoloLens-Emulator** aus.

  ![HoloLens Emulator in der Bereitstellungszielliste](images/deployemulator-500px.png)<br>
* Wählen **Sie Debuggen > Debuggen starten** aus, um Ihre App bereitzustellen und mit dem Debuggen zu beginnen.
* Der Emulator startet ihre App und führen sie aus.
* Platzieren Sie Ihre App mit einer Tastatur, maus und einem Xbox-Controller auf der ganzen Welt, um sie zu starten.

  ![HoloLens Emulator mit einem UWP-Beispiel geladen](images/hololensemulatorwithuwpsample-800px.png)<br>

### <a name="next-steps"></a>Nächste Schritte

An diesem Punkt kann eine von zwei Dingen geschehen:
1. Ihre App zeigt ihren Begrüßungsbildschirm an und beginnt mit der Ausführung, nachdem sie in der App platziert Emulator! Prima.
2. Oder nachdem Sie eine Ladeanimation für ein 2D-Hologramm angezeigt haben, wird das Laden nicht mehr angezeigt, und Ihre App wird nur auf dem Begrüßungsbildschirm angezeigt. Dies bedeutet, dass ein Fehler vor sich gegangen ist, und es wird eine weitere Untersuchung dauern, um zu verstehen, wie Sie Ihre App in der Mixed Reality.

Sie müssen debuggen, um zum Stamm der möglichen Probleme zu kommen, die das Starten Ihrer UWP-App HoloLens.

### <a name="running-your-uwp-app-in-the-debugger"></a>Ausführen Ihrer UWP-App im Debugger

Diese Schritte führen Sie durch das Debuggen Ihrer UWP-App mithilfe des Visual Studio Debuggers.
* Wenn Sie dies noch nicht getan haben, öffnen Sie Ihre Lösung in Visual Studio. Ändern Sie das Ziel in die **HoloLens Emulator** und die Buildkonfiguration in **x86.**
* Wählen **Sie Debuggen > Debuggen starten** aus, um Ihre App bereitzustellen und mit dem Debuggen zu beginnen.
* Platzieren Sie die App mit der Maus, der Tastatur oder dem Xbox-Controller auf der Ganzen Welt.
* Visual Studio sollte jetzt an einer anderen Stelle in Ihrem App-Code zu einem Fehler führen.
  - Wenn Ihre App aufgrund eines nicht behandelten Fehlers nicht sofort abstürzt oder in den Debugger einbricht, führen Sie einen Testlauf der Kernfeatures Ihrer App durch, um sicherzustellen, dass alles ausgeführt wird und funktioniert. Möglicherweise werden Fehler wie unten dargestellt angezeigt (interne Ausnahmen, die behandelt werden). Um sicherzustellen, dass Sie keine internen Fehler übersehen, die sich auf die Benutzererfahrung Ihrer App auswirken, führen Sie Ihre automatisierten Tests und Komponententests durch, um sicherzustellen, dass sich alles wie erwartet verhält.

![HoloLens Emulator mit einem UWP-Beispiel geladen, das eine Systemausnahme zeigt](images/hololensemulatorwithuwpsampleexception-800px.png)

## <a name="update-your-ui"></a>Aktualisieren der Benutzeroberfläche

Da Ihre UWP-App nun auf immersiven Headsets ausgeführt wird und HoloLens 2D-Hologramm verwendet wird, stellen wir als Nächstes sicher, dass es gut aussieht. Folgende Punkte sollten berücksichtigt werden:
* Windows Mixed Reality werden alle 2D-Apps mit einer festen Auflösung und einem DPI ausgeführt, die 853 x 480 effektive Pixel entspricht. Überlegen Sie, ob Ihr Entwurf in dieser Größenordnung verfeinern muss, und sehen Sie sich die nachstehenden Entwurfsanleitungen an, um Ihre Erfahrung mit HoloLens immersiven Headsets zu verbessern.
* Windows Mixed Reality [unterstützt keine](../../design/app-model.md) 2D-Livekacheln. Wenn Ihre Kernfunktionalität Informationen auf einer Livekachel zeigt, ziehen Sie in Betracht, diese Informationen wieder in Ihre App zu verschieben oder [3D-App-Startfunktionen zu erkunden.](../../distribute/3d-app-launcher-design-guidance.md)

### <a name="2d-app-view-resolution-and-scale-factor"></a>Auflösung und Skalierungsfaktor der 2D-App-Ansicht

![Vom reaktionsschnellen Design](images/scale-500px.png)

Windows 10 den visuellen Entwurf von echten Bildschirmpixeln in **effektive Pixel verschiebt.** Das bedeutet, dass Entwickler ihre Benutzeroberfläche nach den Windows 10 Human Interface Guidelines für effektive Pixel entwerfen und die Windows-Skalierung sicherstellt, dass diese effektiven Pixel die richtige Größe für die Benutzerfreundlichkeit für Geräte, Auflösungen, DPI und so weiter haben. Weitere Informationen [finden Sie in diesem großartigen Artikel](/windows/uwp/design/layout/screen-sizes-and-breakpoints-for-responsive-design) auf MSDN und in dieser [BUILD-Präsentation.](https://video.ch9.ms/sessions/build/2015/2-63_Build_2015_Windows_Scaling.pptx)

Auch bei der einzigartigen Fähigkeit, Apps in Ihrer Welt in einer Reihe von Entfernungen zu platzieren, werden TV-orientierte Ansichtsentfernungen empfohlen, um die bestmögliche Lesbarkeit und Interaktion mit Anving/Gesten zu erreichen. Daher zeigt eine virtuelle Tafel im Mixed Reality Home Ihre flache UWP-Ansicht an:

**1280 x 720, 150 % DPI** (853 x 480 effektive Pixel)

Diese Lösung hat mehrere Vorteile:
* Dieses effektive Pixellayout hat ungefähr die gleiche Informationsdichte wie ein Tablet oder einen kleinen Desktop.
* Er entspricht dem festen DPI und den effektiven Pixeln für UWP-Apps, die auf Xbox One ausgeführt werden, wodurch eine nahtlose Geräteerfahrung ermöglicht wird.
* Diese Größe sieht gut aus, wenn sie über unsere verschiedenen Betriebsentfernungen für Apps auf der Ganzen Welt hinweg skaliert wird.

### <a name="2d-app-view-interface-design-best-practices"></a>Bewährte Methoden für den Entwurf der 2D-App-Ansichtsschnittstelle

**tun:**
* Befolgen Sie die [Windows 10 Human Interface Guidelines (HIG)](https://dev.windows.com/design) für Stile, Schriftgrade und Schaltflächengrößen. HoloLens übernimmt die Arbeit, um sicherzustellen, dass Ihre App über kompatible App-Muster, lesbare Textgrößen und eine geeignete Trefferzielgröße verfügen wird.
* Stellen Sie sicher, dass Ihre Benutzeroberfläche bewährte Methoden für [reaktionsfähiges Design](/windows/uwp/design/layout/screen-sizes-and-breakpoints-for-responsive-design) befolgt, um die eindeutige Auflösung und DPI HoloLens optimal zu betrachten.
* Verwenden Sie die Empfehlungen für helle Farbdesigns aus Windows.

**Tue nicht:**
* Ändern Sie Ihre Benutzeroberfläche in Mixed Reality zu drastisch, um sicherzustellen, dass Benutzer ein- und aus dem Headset vertraut sind.

### <a name="understand-the-app-model"></a>Grundlegendes zum App-Modell

Das [App-Modell](../../design/app-model.md) für Mixed Reality ist für die Verwendung des Mixed Reality Home konzipiert, in dem viele Apps zusammen leben. Stellen Sie sich dies als Mixed Reality-Entsprechung des Desktops vor, auf dem Sie viele 2D-Apps gleichzeitig ausführen. Dies hat Auswirkungen auf den App-Lebenszyklus, Kacheln und andere wichtige Features Ihrer App.

### <a name="app-bar-and-back-button"></a>App-Leiste und Schaltfläche "Zurück"

2D-Ansichten werden mit einer App-Leiste über ihrem Inhalt versehen. Die App-Leiste verfügt über zwei Punkte der app-spezifischen Personalisierung:

**Titel:** Zeigt den *Anzeigenamen* der Kachel an, die der App-Instanz zugeordnet ist.

**Schaltfläche "Zurück":** Löst das *[BackRequested-Ereignis](/uwp/api/Windows.UI.Core.SystemNavigationManager)* aus, wenn gedrückt wird. Die Sichtbarkeit der Zurück-Schaltfläche wird durch *[SystemNavigationManager.AppViewBackButtonVisibility](/uwp/api/Windows.UI.Core.SystemNavigationManager)* gesteuert.

![Benutzeroberfläche der App-Leiste in der 2D-App-Ansicht](images/12697297-10104100857470613-1470416918759008487-o-500px.jpg)<br>
*Benutzeroberfläche der App-Leiste in der 2D-App-Ansicht*

### <a name="test-your-2d-apps-design"></a>Testen des Entwurfs Ihrer 2D-App

Es ist wichtig, Ihre App zu testen, um sicherzustellen, dass der Text lesbar ist, die Schaltflächen als Ziel angezeigt werden können und die App insgesamt richtig aussieht. Sie [](../platform-capabilities-and-apis/testing-your-app-on-hololens.md) können tests auf einem Desktop-Headset, einem HoloLens, einem Emulator oder einem Touchgerät mit einer Auflösung von 1280 x 720 % @150 durchführen.

## <a name="new-input-possibilities"></a>Neue Eingabemöglichkeiten

HoloLens verwendet erweiterte Tiefensensoren, um die Welt zu sehen und Benutzer zu sehen. Dies ermöglicht erweiterte Handgesten wie [z.B. Licht](../../design/system-gesture.md#bloom) und [Tippen in die Luft.](../../design/gaze-and-commit.md#composite-gestures) Leistungsstarke Mikrofone ermöglichen auch [Spracherlebnisse.](../../design/voice-input.md)

Mit Desktop-Headsets können Benutzer Motion-Controller verwenden, um auf Apps zu zeigen und Maßnahmen zu ergreifen. Sie können auch ein Gamepad verwenden, um Objekte mit ihrem Anvisieren anvisieren zu können.

Windows übernimmt all diese Komplexität für UWP-Apps und übersetzt Ihre [Eingaben für Anvisierung,](../../design/gaze-and-commit.md)Gesten, Stimme und Motion Controller in [Zeigerereignisse,](/windows/uwp/design/input/handle-pointer-input#pointer_events) die den Eingabemechanismus abstrahieren. Ein Benutzer hat z. B. möglicherweise mit der Hand in die Luft tippen oder den Select-Trigger auf einem Motion-Controller gezogen, aber 2D-Anwendungen müssen nicht wissen, woher die Eingabe stammt. Sie sehen lediglich eine 2D-Toucheingabe, als ob sie sich auf einem Touchscreen befänden.

Im Folgenden finden Sie die grundlegenden Konzepte/Szenarien, die Sie für die Eingabe verstehen sollten, wenn Sie Ihre UWP-App HoloLens:
* [Das Anvieren](../../design/gaze-and-commit.md) wird zu Hoverereignissen, die unerwartet Menüs, Flyouts oder andere Elemente der Benutzeroberfläche auslösen können, um einfach durch das Umdrehen Ihrer App aufzublenden.
* Das Anvisieren ist nicht so präzise wie die Mauseingabe. Verwenden Sie trefferziele mit entsprechender Größe für HoloLens, ähnlich wie touchfreundliche mobile Anwendungen. Kleine Elemente in der Nähe der Ränder der App sind besonders schwierig zu interagieren.
* Benutzer müssen die Eingabemodi wechseln, um vom Scrollen zum Ziehen auf das Schwenken mit zwei Fingern zu wechseln. Wenn Ihre App für Toucheingaben konzipiert wurde, sollten Sie sicherstellen, dass keine größeren Funktionen hinter dem Schwenken mit zwei Fingern gesperrt sind. In diesem Falle sollten Sie alternative Eingabemechanismen wie Schaltflächen in Betracht ziehen, die mit zwei Fingern beginnen können. Beispielsweise kann die Karten-App mit zwei Fingern zoomen, verfügt aber über die Schaltfläche "Plus", "Minus" und "Drehen", um die gleichen Zoominteraktionen mit nur einem Klick zu simulieren.

[Die Spracheingabe](../../design/voice-input.md) ist ein wichtiger Bestandteil der Mixed Reality-Erfahrung. Wir haben alle Sprach-APIs aktiviert, die sich in Windows 10 Cortana befinden, wenn ein Headset verwendet wird.

## <a name="publish-and-maintain-your-universal-app"></a>Veröffentlichen und Verwalten Ihrer universellen App

Sobald Ihre App ausgeführt wird, packen Sie Ihre App, um [sie an den Microsoft Store zu übermitteln.](../../distribute/submitting-an-app-to-the-microsoft-store.md)

## <a name="see-also"></a>Siehe auch
* [App-Modell](../../design/app-model.md)
* [Anvisieren mit dem Kopf und Ausführen](../../design/gaze-and-commit.md)
* [Motion-Controller](../../design/motion-controllers.md)
* [Spracheingabe](../../design/voice-input.md)
* [Senden einer App an den Microsoft Store](../../distribute/submitting-an-app-to-the-microsoft-store.md)
* [Verwendung des HoloLens-Emulators](../platform-capabilities-and-apis/using-the-hololens-emulator.md)