---
title: Verwenden von Visual Studio zum Bereitstellen und Debuggen
description: Erfahren Sie, wie Sie Apps für HoloLens und Windows Mixed Reality mithilfe von Visual Studio erstellen, debuggen und bereitstellen.
author: pbarnettms
ms.author: pbarnett
ms.date: 09/15/2021
ms.topic: article
ms.localizationpriority: high
keywords: Visual Studio, HoloLens, Mixed Reality, debuggen, bereitstellen
ms.openlocfilehash: 948ec52dcfe738a28316e9906d473b32454f6d59
ms.sourcegitcommit: 7dad5bde71d429bb23c72a4074e60b6668a7f091
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2021
ms.locfileid: "127857509"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a>Verwenden von Visual Studio zum Bereitstellen und Debuggen

Unabhängig davon, ob Sie DirectX oder Unity zur Entwicklung ihrer Mixed Reality-App verwenden, Visual Studio ist Ihr Tool der Wahl zum Debuggen und Bereitstellen. In diesem Abschnitt wird Folgendes erläutert:
* Bereitstellen von Anwendungen auf Ihrer HoloLens oder Ihrem immersiven Windows Mixed Reality-Headset mithilfe von Visual Studio.
* Verwenden des in Visual Studio integrierten HoloLens-Emulators.
* Debuggen von Mixed Reality-Apps.

## <a name="prerequisites"></a>Voraussetzungen

1. Installationsanweisungen finden Sie unter [Installieren der Tools](../../develop/install-the-tools.md#installation-checklist).
2. Erstellen Sie ein neues Projekt für Universelle Windows-Apps in Visual Studio.  Verwenden Sie für HoloLens (1. Gen.) Visual Studio 2017 oder höher.  Verwenden Sie für HoloLens 2 Visual Studio 2019 16.2 oder höher. C# und C++ werden unterstützt. (Oder befolgen Sie die Anweisungen zum [Erstellen einer App in Unity](../../develop/unity/tutorials/holograms-100.md).)

## <a name="enabling-developer-mode"></a>Aktivieren des Entwicklermodus

Aktivieren Sie zunächst den **Entwicklermodus** auf Ihrem Gerät, damit Visual Studio eine Verbindung damit herstellen kann.

### <a name="hololens"></a>HoloLens

1. Schalten Sie die HoloLens ein, und setzen Sie sie auf.
2. Verwenden Sie die [Startgeste](../../design/system-gesture.md), um das Hauptmenü zu starten.
3. Wählen Sie die Kachel **Einstellungen** aus, um die App in Ihrer Umgebung zu starten.
4. Wählen Sie das Menüelement **Aktualisieren** aus.
5. Wählen Sie das Menüelement **Für Entwickler** aus.
6. Aktivieren Sie **Use developer feature** (Entwicklerfunktion verwenden), um auf Ihrer HoloLens Apps aus Visual Studio bereitzustellen. Wenn auf Ihrem Gerät Windows Holographic, Version 21H1 oder höher ausgeführt wird, aktivieren Sie außerdem **Device Discovery** (Geräteermittlung).
7. Optional: Scrollen Sie nach unten, und aktivieren Sie auch das **Geräteportal**, mit dem Sie sich über einen Webbrowser mit dem [Windows-Geräteportal](using-the-windows-device-portal.md) auf Ihrer HoloLens verbinden können.

### <a name="windows-pc"></a>Windows PC

Wenn Sie mit einem Windows Mixed Reality-Headset arbeiten, das mit dem PC verbunden ist, müssen Sie den **Entwicklermodus** auf dem PC aktivieren.
1. Navigieren Sie zu **Einstellungen**
2. Wählen Sie **Update und Sicherheit** aus
3. Wählen Sie **Für Entwickler** aus
4. Aktivieren Sie den **Entwicklermodus**, lesen Sie den Haftungsausschluss für die ausgewählte Einstellung, und wählen Sie dann „Ja“ aus, um die Änderung zu übernehmen.

## <a name="deploying-a-hololens-app-over-wi-fi"></a>Bereitstellen einer HoloLens-App über WLAN 

Konfigurieren Sie Ihr Visual Studio-Projekt mit den folgenden Eigenschaften:

1. Wählen Sie die Optionen für die Kompilierung von Apps aus
    * Wählen Sie für Unity-Projekte entweder **Release** oder **Master** aus 
    * Wählen Sie für alle anderen Projekte **Release** aus

> [!NOTE]
> Umfassende Definitionen für jede der Kompilierungsoptionen finden Sie unter [Exportieren und Entwickeln von Visual Studio-Projektmappen](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).

2. Wählen Sie Ihre Buildkonfiguration ausgehend von Ihrem Gerät aus.

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. Wählen Sie im Dropdownmenü für das Bereitstellungsziel **Remotecomputer** aus

![Bereitstellungsziel „Remotecomputer“ in Visual Studio](images/remotemachinesetting_arm64.png)

Als nächstes müssen Sie die Remoteverbindung festlegen. Navigieren Sie für C++- und JavaScript-Projekte zu **Projekt > Eigenschaften > Konfigurationseigenschaften > Debuggen**. Wenn Sie in einem C#-Projekt arbeiten, sollte automatisch ein Dialogfeld angezeigt werden.

> [!NOTE]
> Wenn das Dialogfeld für die Remoteverbindung nicht in Ihrem C#-Projekt angezeigt wird, können Sie es manuell über **Eigenschaften > Debuggen** öffnen.

1. Geben Sie die IP-Adresse Ihres Geräts im Feld **Adresse** oder **Computername** ein. 
    * Sie finden die IP-Adresse Ihrer HoloLens unter **Einstellungen > Netzwerk und Internet > Erweiterte Optionen**
    * Wir empfehlen, die IP-Adresse immer manuell einzugeben, statt sich auf die Funktion zur automatischen Erkennung zu verlassen.

2. Legen Sie den **Authentifizierungsmodus** auf **Universell (Unverschlüsseltes Protokoll)** fest.

  ![Dialogfeld „Remoteverbindung“ in Visual Studio](images/remotedeploy.png)

3. Sie können Ihre App ganz nach Ihren Anforderungen erstellen, bereitstellen und debuggen.
    * Wählen Sie **Debuggen > Debuggen starten** aus, um Ihre App bereitzustellen und den Debugvorgang zu starten.
    * Wählen Sie **Erstellen > Bereitstellen** aus, um eine Erstellung und Bereitstellung ohne Debuggen auszuführen.

![Starten ohne Debuggen in Visual Studio](images/deploywithdebugging.png)

4. Beim erstmaligen Bereitstellen einer App in Ihrer HoloLens von Ihrem Computer aus werden Sie zur Eingabe einer PIN aufgefordert. Befolgen Sie die Anweisungen unten zum **Koppeln Ihres Geräts**.

## <a name="deploying-a-hololens-app-over-usb"></a>Bereitstellen einer HoloLens-App über USB 

<br>

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Deploying-your-HoloLens-2-application/player?format=ny]

1. Wählen Sie die Optionen für die Kompilierung von Apps aus
    * Wählen Sie für Unity-Projekte entweder **Release** oder **Master** aus 
    * Wählen Sie für alle anderen Projekte **Release** aus

> [!NOTE]
> Umfassende Definitionen für jede der Kompilierungsoptionen finden Sie unter [Exportieren und Entwickeln von Visual Studio-Projektmappen](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).

2. Wählen Sie Ihre Buildkonfiguration ausgehend von Ihrem Gerät aus.

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. Wählen Sie im Dropdownmenü für das Bereitstellungsziel **Gerät** aus

![Gerätebereitstellung in Visual Studio](images/buildsettingsusbdeploy_arm64.png)

4. Sie können Ihre App ganz nach Ihren Anforderungen erstellen, bereitstellen und debuggen.
    * Wählen Sie **Debuggen > Debuggen starten** aus, um Ihre App bereitzustellen und den Debugvorgang zu starten.
    * Wählen Sie **Erstellen > Bereitstellen** aus, um eine Erstellung und Bereitstellung ohne Debuggen auszuführen.

![Starten ohne Debuggen in Visual Studio](images/deploywithdebugging.png)</br>

5. Beim erstmaligen Bereitstellen einer App in Ihrer HoloLens von Ihrem Computer aus werden Sie zur Eingabe einer PIN aufgefordert. Befolgen Sie die Anweisungen unten zum **Koppeln Ihres Geräts**.

## <a name="deploying-an-app-to-the-hololens-1st-gen-emulator"></a>Bereitstellen einer App auf dem HoloLens-Emulator (1. Gen.)

1. Vergewissern Sie sich, dass Sie **[den HoloLens-Emulator installiert](../install-the-tools.md)** haben.
2. Wählen Sie eine **x86**-Buildkonfiguration für Ihre App aus.</br>
![x86-Buildkonfiguration in Visual Studio](images/x86setting.png)</br>
3. Wählen Sie im Dropdownmenü für das Bereitstellungsziel **HoloLens-Emulator** aus.</br>
![Ziel „Emulator“ in Visual Studio](images/deployemulator.png)</br>
4. Wählen Sie **Debuggen > Debuggen starten** aus, um Ihre App bereitzustellen und den Debugvorgang zu starten.</br>
![Starten ohne Debuggen in Visual Studio](images/deploywithdebugging.png)</br>

## <a name="deploying-an-app-to-the-hololens-2-emulator"></a>Bereitstellen einer App auf dem HoloLens 2-Emulator

1. Vergewissern Sie sich, dass Sie **[den HoloLens-Emulator installiert](../install-the-tools.md)** haben.
2. Wählen Sie eine **x86**- oder **x64**-Buildkonfiguration für Ihre App aus.</br>
![x86-Buildkonfiguration in Visual Studio](images/x86setting.png)</br>
3. Wählen Sie im Dropdownmenü für das Bereitstellungsziel **HoloLens 2-Emulator** aus.</br>
![Ziel „Emulator“ in der Visual Studio-Anwendung](images/deployemulator2.png)</br>
4. Wählen Sie **Debuggen > Debuggen starten** aus, um Ihre App bereitzustellen und den Debugvorgang zu starten.</br>
![Starten ohne Debuggen in Visual Studio](images/deploywithdebugging.png)</br>

## <a name="deploying-a-vr-app-to-your-local-pc"></a>Bereitstellen einer VR-App auf Ihrem lokalen PC 

Zum Verwenden eines immersiven Windows Mixed Reality-Headsets, das eine Verbindung mit Ihrem PC oder dem [Mixed Reality-Simulator](using-the-windows-mixed-reality-simulator.md) herstellt:
1. Wählen Sie eine **x86**- oder **x64**-Buildkonfiguration aus
2. Wählen Sie im Dropdownmenü für das Bereitstellungsziel **Lokaler Computer** aus
3. Sie können Ihre App ganz nach Ihren Anforderungen erstellen, bereitstellen und debuggen.
    * Wählen Sie **Debuggen > Debuggen starten** aus, um Ihre App bereitzustellen und den Debugvorgang zu starten.
    * Wählen Sie **Erstellen > Bereitstellen** aus, um eine Erstellung und Bereitstellung ohne Debuggen auszuführen.

## <a name="pairing-your-device"></a>Koppeln Ihres Geräts

Beim erstmaligen Bereitstellen einer App aus Visual Studio in Ihrer HoloLens werden Sie zur Eingabe einer PIN aufgefordert. Generieren Sie auf der HoloLens eine PIN, indem Sie die Einstellungs-App starten, zu **Update > Für Entwickler** navigieren und auf **Koppeln** tippen. Wenn die PIN auf Ihrer HoloLens angezeigt wird, geben Sie sie in Visual Studio ein. Tippen Sie nach dem vollzogenen Koppeln in Ihrer HoloLens auf **Fertig**, um das Dialogfeld zu schließen. Dieser PC ist nun mit der HoloLens gekoppelt, und Sie können Apps automatisch bereitstellen. Wiederholen Sie diese Schritte für jeden PC, der zum Bereitstellen von Apps auf Ihrer HoloLens verwendet wird.

So heben Sie die Kopplung Ihrer HoloLens mit allen gekoppelten Computern auf:
* Starten Sie die App **Einstellungen**, navigieren Sie zu **Aktualisieren > Für Entwickler**, und tippen Sie auf **Löschen**.

## <a name="graphics-debugger-for-hololens-1st-gen"></a>Grafikdebugger für HoloLens (1. Gen.)

Die Visual Studio-Grafikdiagnose-Tools sind beim Schreiben und Optimieren einer holografischen App nützlich. Ausführliche Informationen finden Sie unter [Visual Studio-Grafikdiagnose auf MSDN](/previous-versions/visualstudio/visual-studio-2015/debugger/visual-studio-graphics-diagnostics).

**So starten Sie den Grafikdebugger**
1. Befolgen Sie die Anweisungen oben, um ein Gerät oder einen Emulator als Ziel festzulegen.
2. Navigieren Sie zu **Debuggen > Grafik > Diagnose starten**
3. Wenn Sie die Diagnose zum ersten Mal auf einer HoloLens starten, wird möglicherweise ein Fehler „Zugriff verweigert“ angezeigt. Starten Sie die HoloLens neu, damit die aktualisierten Berechtigungen wirksam werden, und wiederholen Sie den Vorgang.

## <a name="profiling"></a>Profilerstellung

Die Visual Studio-Tools zur Profilerstellung ermöglichen Ihnen das Analysieren von Leistung und Ressourcennutzung Ihrer App. Dies beinhaltet Tools zur Optimierung von CPU-, Arbeitsspeicher-, Grafik- und Netzwerkauslastung. Ausführliche Informationen finden Sie unter [Ausführen von Diagnosetools ohne Debuggen auf MSDN](/previous-versions/visualstudio/visual-studio-2015/profiling/profiling-tools).

**So starten Sie die Profilerstellungstools in HoloLens**
1. Befolgen Sie die Anweisungen oben, um ein Gerät oder einen Emulator als Ziel festzulegen.
2. Navigieren Sie zu **Debuggen > Diagnosetools ohne Debuggen starten...**
3. Wählen Sie die Tools aus, die Sie verwenden möchten.
4. Wählen Sie **Start** aus.
5. Wenn Sie die Diagnose zum ersten Mal auf einer HoloLens ohne Debuggen starten, wird möglicherweise ein Fehler „Zugriff verweigert“ angezeigt. Starten Sie die HoloLens neu, damit die aktualisierten Berechtigungen wirksam werden, und wiederholen Sie den Vorgang.

## <a name="debugging-an-installed-or-running-app"></a>Debuggen einer installierten oder aktuell laufenden App

Sie können Visual Studio verwenden, um eine installierte Universelle Windows-App zu debuggen, ohne sie aus einem Visual Studio-Projekt bereitzustellen. Dies ist nützlich, wenn Sie ein installiertes App-Paket oder eine App debuggen möchten, die bereits ausgeführt wird.
1. Navigieren Sie zu **Debuggen > Andere Debugziele > Installiertes App-Paket debuggen**
2. Wählen Sie das Ziel **Remotecomputer** für HoloLens oder **Lokaler Computer** für immersive Headsets aus.
3. Geben Sie die **IP-Adresse** Ihres Geräts ein.
4. Wählen Sie den Authentifizierungsmodus **Universell** aus.
5. Im Fenster werden sowohl ausgeführte als auch inaktive Apps angezeigt. Suchen Sie die App aus, die Sie debuggen möchten.
6. Wählen Sie den zu debuggenden Codetyp aus (Verwaltet, Nativ, Gemischt)
7. Wählen Sie **Anfügen** oder **Start** aus.

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie dem Weg der Unity-Entwicklungsprüfpunkte folgen, den wir entworfen haben, befinden Sie sich in der Mitte der Bereitstellungsphase. Von hier aus können Sie mit dem nächsten Thema fortfahren:

> [!div class="nextstepaction"]
> [Bereitstellen im HoloLens-Emulator](using-the-hololens-emulator.md)

Oder fahren Sie direkt mit dem Hinzufügen erweiterter Dienste fort:

> [!div class="nextstepaction"]
> [Erweiterte Dienste](../../develop/unity/unity-development-overview.md#5-adding-services)

Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) zurückkehren.

## <a name="see-also"></a>Siehe auch
* [Installieren der Tools](../install-the-tools.md)
* [Verwendung des HoloLens-Emulators](using-the-hololens-emulator.md)
* [Bereitstellen und Debuggen von UWP (Universelle Windows-Plattform)-Apps](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps)
* [Aktivieren Ihres Geräts für die Entwicklung](/windows/uwp/get-started/enable-your-device-for-development)
