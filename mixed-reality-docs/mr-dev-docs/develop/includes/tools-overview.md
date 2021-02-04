---
ms.openlocfilehash: c205e3b812eeb7a85bfe361d4fd83f9aec7b7999
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2021
ms.locfileid: "99244949"
---
# <a name="unity"></a>[Unity](#tab/unity)

![Unity-Logobanner](../images/unity_logo_banner.png)<br>

### <a name="1-download-the-latest-version"></a>1. Herunterladen der aktuellen Version

Wir empfehlen den [Unity LTS-Stream (Long Term Support)](https://unity3d.com/unity/qa/lts-releases) als beste Version, um neue Projekte zu starten und auf die neueste Version zu aktualisieren, um die neuesten stabilen Korrekturen zu erhalten.
* Die aktuelle Empfehlung lautet, **[Unity 2019.4 LTS](https://unity3d.com/unity/qa/lts-releases?version=2019.4)** zu verwenden, wobei es sich um den LTS-Build handelt, der unten für MRTK v2 erforderlich ist.
* Wenn Sie aus bestimmten Gründen eine andere Version von Unity verwenden müssen, unterstützt Unity parallele Installationen unterschiedlicher Versionen.

### <a name="2-install-the-mixed-reality-feature-tool"></a>2. Installieren des Mixed Reality-Featuretools

Das [Mixed Reality-Featuretool](../unity/welcome-to-mr-feature-tool.md) ist eine neue Möglichkeit für Entwickler, Mixed Reality-Featurepakete in Unity-Projekten zu ermitteln und hinzuzufügen. 

Sie können Pakete vor dem Importieren nach Name oder Kategorie durchsuchen, ihre Abhängigkeiten anzeigen und sogar Änderungsvorschläge für Ihre Projektmanifestdatei anzeigen. Nachdem Sie die gewünschten Pakete überprüft haben, lädt das Mixed Reality-Featuretool sie in das Projekt Ihrer Wahl herunter.

#### <a name="importing-the-mixed-reality-toolkit"></a>Importieren des Mixed Reality-Toolkits

![MRTK](../../design/images/MRTK_UX_Hero.png)

Das [Mixed Reality-Toolkit](../unity/mrtk-getting-started.md) (MRTK) ist ein plattformübergreifendes Open-Source-Entwicklungskit für Mixed Reality-Anwendungen. 

* Installieren Sie das Mixed Reality Toolkit-Paket, indem Sie den [Installations- und Verwendungsanweisungen](../unity/welcome-to-mr-feature-tool.md#system-requirements) folgen und das **Mixed Reality Toolkit Foundation**-Paket auswählen.

Wir empfehlen, den Abschnitt „Erste Schritte“ in unserer zusammengestellten [HoloLens](../unity/unity-development-overview.md#1-getting-started)- oder [VR](../unity/unity-development-wmr-overview.md#1-getting-started)-Entwicklungsreise auszuführen. Wenn Sie sich bereits auf der Unity für HoloLens-Entwicklungsreise befinden, beenden Sie die unten aufgelisteten restlichen Setupschritte, und fahren sie mit den [HoloLens 2-Einstiegstutorials](../unity/tutorials/mr-learning-base-01.md) fort.

> [!IMPORTANT]
> Beachten Sie, dass die Installationsanleitungen sich auf die neueste stabile Kombination aus MRTK- und Unity-Releases beziehen, das sind zurzeit **MRTK 2.5.1** und **Unity 2019.4 LTS**.

> [!NOTE]
> Wenn Sie MRTK für Unity nicht verwenden möchten, müssen Sie [für alle Interaktionen und Verhaltensweisen selber Skripts erstellen](../unity/configure-unity-project.md).

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity-Banner](../images/MRTK-Unity-Banner.png)<br>**Mixed Reality-Toolkit – Unity (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

#### <a name="other-tools-optional"></a>Weitere Tools [optional]
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a>: Codebits und Komponenten, die möglicherweise nicht direkt auf HoloLens- oder immersive Headsets (VR) ausgeführt, sondern stattdessen mit ihnen gekoppelt werden, um Erfahrungen mit Windows Mixed Reality zu sammeln.
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit – Common (GitHub)</a>: eine Sammlung freigegebener Skripts und Komponenten.

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a>3. Einrichten Ihres PCs für die Mixed Reality-Entwicklung

Das Windows SDK funktioniert am besten unter dem Betriebssystem Windows 10. Das SDK wird auch unter folgenden Betriebssystemen unterstützt: Windows 8.1, Windows 8, Windows 7, Windows Server 2012 und Windows Server 2008 R2. Beachten Sie, dass nicht alle Tools unter älteren Betriebssystemen unterstützt werden.

> [!NOTE]
> Sie können Ihre Apps für HoloLens, für immersive Headsets (VR) oder beides entwickeln und bereitstellen. Stellen Sie sicher, dass Sie die unten aufgeführten Anforderungen abhängig von Ihren Anforderungen erfüllen.

#### <a name="for-hololens-development"></a>HoloLens-Entwicklung

Wenn Sie Ihren Entwicklungs-PC für die HoloLens-Entwicklung einrichten, stellen Sie sicher, dass er die Systemanforderungen sowohl für <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> als auch für <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> erfüllt. Wenn Sie Ihre App auf einem HoloLens-Gerät ausführen möchten, müssen Sie die [Einrichtungsanweisungen im Windows-Geräteportal](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal) befolgen. Wenn Sie planen, den [HoloLens-Emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md) zu verwenden, sollten Sie sicherstellen, dass Ihr PC auch die [Systemanforderungen des HoloLens-Emulators](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) erfüllt.

Informationen zu den ersten Schritten mit dem HoloLens-Emulator finden Sie unter [Verwendung des HoloLens-Emulators](../platform-capabilities-and-apis/using-the-hololens-emulator.md).

Wenn Sie planen, sowohl für HoloLens als auch für immersive Windows Mixed Reality-Headsets (VR) zu entwickeln, verwenden Sie die Systemempfehlungen und Anforderungen im folgenden Abschnitt.

#### <a name="hololens-troubleshooting"></a>HoloLens-Problembehandlung

##### <a name="setting-developer-mode-is-grayed-out"></a>Einstellung „Entwicklermodus“ ist abgeblendet

Wenn beim Aktivieren des Entwicklermodus auf Ihrem Gerät Probleme auftreten, sind Sie möglicherweise nicht der [Gerätebesitzer](/hololens/security-adminless-os). Im Mehrbenutzermodus ist die Person, die das Gerät als Erster verwendet, der Gerätebesitzer. Alle nachfolgenden Benutzer verfügen nicht über die erforderlichen Berechtigungen, um den Entwicklermodus zu aktivieren oder andere Konfigurationsänderungen vorzunehmen. Es gibt jedoch eine Ausnahme, bei der der erste Benutzer in einer Autopilot-Umgebung möglicherweise nicht der Besitzer des Geräts ist, die detailliert in der [HoloLens-Sicherheitsdokumentation](/hololens/security-adminless-os#device-owner) beschrieben ist.

Folgende Lösungen sind möglich:

* Bitten Sie den Gerätebesitzer, den Entwicklermodus zu aktivieren, bevor das Gerät an andere Benutzer oder Entwickler übergeben wird.
* Schlagen Sie vor, dass Ihr IT-/MDM-Administrator die CSP-[Richtlinie ApplicationManagement/ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) für das spezifische Gerät oder eine Entwicklergerätegruppe aktiviert. 
    * Diese Richtlinie kann über [Bereitstellungspakete](/hololens/hololens-provisioning) oder über [MDM für HoloLens-Geräte](/hololens/hololens-mdm-configure) festgelegt werden.
* Verwenden des [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery) (Begleiter für erweiterte Wiederherstellung)

> [!NOTE]
> Weitere Informationen zur Geräteverwaltung finden Sie in der Übersicht der **[HoloLens-Geräteverwaltung](/hololens/hololens-csp-policy-overview)** .

##### <a name="i-cant-deploy-over-usb"></a>Bereitstellen über USB nicht möglich

Wenn Sie eine Anwendung nicht direkt über USB bereitstellen können, stellen Sie sicher, dass Sie alle oben aufgeführten Installationsanforderungen erfüllt haben, und befolgen Sie unsere [schrittweise Anleitung](../unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2).

#### <a name="immersive-vr-headset-requirements"></a>Anforderungen an immersive Headsets (VR)

>[!NOTE]
>Die folgenden Richtlinien sind die derzeit empfohlenen Mindestanforderungen und Spezifikationen für Ihren *Entwicklungs-PC* für immersive Headsets (VR) und werden regelmäßig aktualisiert.

>[!WARNING]
>Verwechseln Sie dies nicht mit den [Richtlinien zur minimalen PC-Hardwarekompatibilität](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), die die *Spezifikationen von Consumer-PCs* umreißen, auf die Sie Ihre immersive Headset-App (VR) oder Ihr Spiel ausrichten sollten.

Wenn Ihr Entwicklungs-PC für immersive Headsets nicht über vollwertige HDMI- und/oder USB 3.0-Anschlüsse verfügt, benötigen Sie [Adapter](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs), um Ihr Headset anzuschließen.

Es gibt derzeit [bekannte Probleme](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) bei einigen Hardwarekonfigurationen, insbesondere bei Notebooks mit Hybridgrafik.

<table>
<tr>
<th></th><th> Minimum</th><th> Empfohlen</th>
</tr><tr>
<td> Prozessor</td><td> <b>Notebook:</b> Intel Mobile Core i5-CPU der 7. Generation, Dual-Core mit Hyperthreading <b>Desktop:</b> Intel Desktop i5-CPU der 6. Generation, Dual-Core mit Hyperthreading <b>ODER</b> AMD FX4350 mit 4,2 GHz und vier Kernen</td><td> <b>Desktop:</b> Intel Desktop i7 der 6. Generation (6 Kerne) <b>ODER</b> AMD Ryzen 5 1600 (6 Kerne, 12 Threads)</td>
</tr><tr>
<td> GPU</td><td> <b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2 GB) – gleichwertig oder höher, DX12-fähige GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2 GB) – gleichwertig oder höher, DX12-fähige GPU</td><td><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2 GB) – gleichwertig oder höher, DX12-fähige GPU</td>
</tr><tr>
<td> GPU-Treiber (WDDM-Version)</td><td colspan="2"> WDDM 2.2-Treiber</td>
</tr><tr>
<td> Wärmeleistung</td><td colspan="2"> 15 W oder höher</td>
</tr><tr>
<td> Anschlüsse der Grafikanzeige</td><td colspan="2"> Ein verfügbarer Grafikanzeigeanschluss für&#160;Headset (HDMI 1.4 oder DisplayPort 1.2 für Headsets mit 60 Hz, HDMI 2.0 oder DisplayPort 1.2 für Headsets mit 90 Hz)</td>
</tr><tr>
<td> Anzeigeauflösung</td><td colspan="2"> Auflösung: SVGA (800 x 600) oder höhere Bittiefe: Farbe: 32 Bit pro Pixel</td>
</tr><tr>
<td> Memory</td><td> 8&#160;GB RAM oder mehr</td><td> 16 GB RAM oder mehr</td>
</tr><tr>
<td> Speicher</td><td colspan="2"> &gt;10 GB zusätzlicher freier Speicherplatz</td>
</tr><tr>
<td> USB-Anschlüsse</td><td colspan="2"> Ein verfügbare USB-Anschluss für Headset (USB-3.0 Type-A) <b>Hinweis: USB muss mindestens 900 mA bereitstellen</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0 (für den Anschluss von Zubehör)</td>
</tr>
</table>

Wenn Sie neu in die MRTK-Entwicklung mit Unity einsteigen, empfehlen wir, unserer zusammengestellten Unity-Entwicklungsreise zu folgen:

> [!div class="nextstepaction"]
> [Ihre Unity für HoloLens-Journey starten](../unity/unity-development-overview.md)

> [!div class="nextstepaction"]
> [Ihre Unity for VR-Journey starten](../unity/unity-development-wmr-overview.md)

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie der Unity für HoloLens-Journey entlang der Entwicklungsprüfpunkte folgen, die wir zusammengestellt haben, besteht Ihre nächste Aufgabe darin, sich durch unsere HoloLens 2-Tutorialreihe hindurch zu arbeiten.

> [!div class="nextstepaction"]
> [Hololens 2-Tutorialreihe](../unity/tutorials/mr-learning-base-01.md)

Wenn Sie der Unity für VR-Journey folgen, besteht Ihre nächste Aufgabe darin, das Projekt einzurichten.

> [!div class="nextstepaction"]
> [Konfigurieren Ihres Projekts für WMR](../unity/configure-unity-project.md)

Sie können jederzeit zu den Prüfpunkten für die Unity-Entwicklung für [HoloLens](../unity/unity-development-overview.md#1-getting-started) und [VR](../unity/unity-development-wmr-overview.md#1-getting-started) zurückkehren.

# <a name="unreal"></a>[Unreal](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

### <a name="1-download-the-latest-version"></a>1. Herunterladen der aktuellen Version

Es wird empfohlen, die [Unreal-Engine, Version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) oder höher, zu installieren, um die integrierte Unterstützung von HoloLens in vollem Umfang nutzen zu können.

### <a name="2-import-mixed-reality-toolkit-mrtk"></a>2. Importieren des Mixed Reality-Toolkits (MRTK)
![MRTK](../../design/images/MRTK_UX_Hero.png)

Mixed Reality Toolkit (MRTK) ist ein plattformübergreifendes Open Source-Entwicklungskit für Mixed Reality-Anwendungen. MRTK bietet ein plattformübergreifendes Eingabesystem, Grundlagenkomponenten und gemeinsame Bausteine für räumliche Interaktionen. Das Toolkit soll die Entwicklung von Anwendungen für Microsoft HoloLens, für immersive Windows Mixed Reality-Headsets (VR) und für die OpenVR-Plattform beschleunigen.

Für die Installation empfehlen wir, den Abschnitt [Erste Schritte](../unreal/unreal-development-overview.md#1-getting-started) Ihrer zusammengestellten [Unreal-Entwicklungsreise](../unreal/unreal-development-overview.md) auszuführen. Wenn Sie sich bereits auf der Unreal-Entwicklungsreise befinden, beenden Sie die unten aufgelisteten restlichen Setupschritte, und fahren sie mit den [HoloLens 2-Einstiegstutorials](../unreal/tutorials/unreal-uxt-ch1.md) fort.

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity-Logobild](../images/MRTK-Unreal-Banner.png)<br>**Mixed Reality Toolkit-Unreal (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> Wenn Sie MRTK für Unreal nicht verwenden möchten, müssen Sie für alle Interaktionen und Verhaltensweisen selber Skripts erstellen.

#### <a name="other-tools-optional"></a>Weitere Tools [optional]
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a>: Codebits und Komponenten, die möglicherweise nicht direkt auf HoloLens- oder immersive Headsets (VR) ausgeführt, sondern stattdessen mit ihnen gekoppelt werden, um Erfahrungen mit Windows Mixed Reality zu sammeln.
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality-Toolkit – Common (GitHub)</a>: eine Sammlung freigegebener Skripts und Komponenten.

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a>3. Einrichten Ihres PCs für die Mixed Reality-Entwicklung

Das Windows SDK funktioniert am besten unter dem Betriebssystem Windows 10. Das SDK wird auch unter folgenden Betriebssystemen unterstützt: Windows 8.1, Windows 8, Windows 7, Windows Server 2012 und Windows Server 2008 R2. Beachten Sie, dass nicht alle Tools unter älteren Betriebssystemen unterstützt werden.

> [!NOTE]
> Sie können Ihre Apps für HoloLens, für immersive Headsets (VR) oder beides entwickeln und bereitstellen. Stellen Sie sicher, dass Sie die unten aufgeführten Anforderungen abhängig von Ihren Anforderungen erfüllen.

#### <a name="for-hololens-development"></a>HoloLens-Entwicklung

Wenn Sie Ihren Entwicklungs-PC für die HoloLens-Entwicklung einrichten, stellen Sie sicher, dass er die Systemanforderungen sowohl für [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) als auch für <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> erfüllt. Wenn Sie Ihre App auf einem HoloLens-Gerät ausführen möchten, müssen Sie die [Einrichtungsanweisungen im Windows-Geräteportal](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal) befolgen. Wenn Sie planen, den [HoloLens-Emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md) zu verwenden, sollten Sie sicherstellen, dass Ihr PC auch die [Systemanforderungen des HoloLens-Emulators](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) erfüllt.

Wenn Sie planen, sowohl für HoloLens als auch für immersive Windows Mixed Reality-Headsets (VR) zu entwickeln, verwenden Sie die Systemempfehlungen und Anforderungen im folgenden Abschnitt.

#### <a name="hololens-troubleshooting"></a>HoloLens-Problembehandlung

##### <a name="setting-developer-mode-is-grayed-out"></a>Einstellung „Entwicklermodus“ ist abgeblendet

Wenn beim Aktivieren des Entwicklermodus auf Ihrem Gerät Probleme auftreten, sind Sie möglicherweise nicht der [Gerätebesitzer](/hololens/security-adminless-os). Im Mehrbenutzermodus ist die Person, die das Gerät als Erster verwendet, der Gerätebesitzer. Alle nachfolgenden Benutzer verfügen nicht über die erforderlichen Berechtigungen, um den Entwicklermodus zu aktivieren oder andere Konfigurationsänderungen vorzunehmen. Es gibt jedoch eine Ausnahme, bei der der erste Benutzer in einer Autopilot-Umgebung möglicherweise nicht der Besitzer des Geräts ist, die detailliert in der [HoloLens-Sicherheitsdokumentation](/hololens/security-adminless-os#device-owner) beschrieben ist.

Folgende Lösungen sind möglich:

* Bitten Sie den Gerätebesitzer, den Entwicklermodus zu aktivieren, bevor das Gerät an andere Benutzer oder Entwickler übergeben wird.
* Schlagen Sie vor, dass Ihr IT-/MDM-Administrator die CSP-[Richtlinie ApplicationManagement/ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) für das spezifische Gerät oder eine Entwicklergerätegruppe aktiviert. 
    * Diese Richtlinie kann über [Bereitstellungspakete](/hololens/hololens-provisioning) oder über [MDM für HoloLens-Geräte](/hololens/hololens-mdm-configure) festgelegt werden.
* Verwenden des [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery) (Begleiter für erweiterte Wiederherstellung)

> [!NOTE]
> Weitere Informationen zur Geräteverwaltung finden Sie in der Übersicht der **[HoloLens-Geräteverwaltung](/hololens/hololens-csp-policy-overview)** .

##### <a name="i-cant-deploy-over-usb"></a>Bereitstellen über USB nicht möglich

Wenn Sie eine Anwendung nicht direkt über USB bereitstellen können, stellen Sie sicher, dass Sie alle oben aufgeführten Installationsanforderungen erfüllt haben, und befolgen Sie unsere [schrittweise Anleitung](../unreal/tutorials/unreal-uxt-ch6.md).

#### <a name="immersive-vr-headset-requirements"></a>Anforderungen an immersive Headsets (VR)

>[!NOTE]
>Die folgenden Richtlinien sind die derzeit empfohlenen Mindestanforderungen und Spezifikationen für Ihren *Entwicklungs-PC* für immersive Headsets (VR) und werden regelmäßig aktualisiert.

>[!WARNING]
>Verwechseln Sie dies nicht mit den [Richtlinien zur minimalen PC-Hardwarekompatibilität](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), die die *Spezifikationen von Consumer-PCs* umreißen, auf die Sie Ihre immersive Headset-App (VR) oder Ihr Spiel ausrichten sollten.

Wenn Ihr Entwicklungs-PC für immersive Headsets nicht über vollwertige HDMI- und/oder USB 3.0-Anschlüsse verfügt, benötigen Sie [Adapter](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs), um Ihr Headset anzuschließen.

Es gibt derzeit [bekannte Probleme](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) bei einigen Hardwarekonfigurationen, insbesondere bei Notebooks mit Hybridgrafik.

<table>
<tr>
<th></th><th> Minimum</th><th> Empfohlen</th>
</tr><tr>
<td> Prozessor</td><td> <b>Notebook:</b> Intel Mobile Core i5-CPU der 7. Generation, Dual-Core mit Hyperthreading <b>Desktop:</b> Intel Desktop i5-CPU der 6. Generation, Dual-Core mit Hyperthreading <b>ODER</b> AMD FX4350 mit 4,2 GHz und vier Kernen</td><td> <b>Desktop:</b> Intel Desktop i7 der 6. Generation (6 Kerne) <b>ODER</b> AMD Ryzen 5 1600 (6 Kerne, 12 Threads)</td>
</tr><tr>
<td> GPU</td><td> <b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2 GB) – gleichwertig oder höher, DX12-fähige GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2 GB) – gleichwertig oder höher, DX12-fähige GPU</td><td><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2 GB) – gleichwertig oder höher, DX12-fähige GPU</td>
</tr><tr>
<td> GPU-Treiber (WDDM-Version)</td><td colspan="2"> WDDM 2.2-Treiber</td>
</tr><tr>
<td> Wärmeleistung</td><td colspan="2"> 15 W oder höher</td>
</tr><tr>
<td> Anschlüsse der Grafikanzeige</td><td colspan="2"> Ein verfügbarer Grafikanzeigeanschluss für&#160;Headset (HDMI 1.4 oder DisplayPort 1.2 für Headsets mit 60 Hz, HDMI 2.0 oder DisplayPort 1.2 für Headsets mit 90 Hz)</td>
</tr><tr>
<td> Anzeigeauflösung</td><td colspan="2"> Auflösung: SVGA (800 x 600) oder höhere Bittiefe: Farbe: 32 Bit pro Pixel</td>
</tr><tr>
<td> Memory</td><td> 8&#160;GB RAM oder mehr</td><td> 16 GB RAM oder mehr</td>
</tr><tr>
<td> Speicher</td><td colspan="2"> &gt;10 GB zusätzlicher freier Speicherplatz</td>
</tr><tr>
<td> USB-Anschlüsse</td><td colspan="2"> Ein verfügbare USB-Anschluss für Headset (USB-3.0 Type-A) <b>Hinweis: USB muss mindestens 900 mA bereitstellen</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0 (für den Anschluss von Zubehör)</td>
</tr>
</table>

Wenn Sie neu in die MRTK-Entwicklung mit Unreal einsteigen, empfehlen wir, unserer zusammengestellten Unreal-Entwicklungsreise zu folgen:

> [!div class="nextstepaction"]
> [Antreten Ihrer Unreal-Journey](../unreal/unreal-development-overview.md)

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie der Unreal-Reise entlang der Entwicklungsprüfpunkte folgen, die wir zusammengestellt haben, besteht Ihre nächste Aufgabe darin, sich durch unsere HoloLens 2-Tutorialreihe hindurch zu arbeiten.

> [!div class="nextstepaction"]
> [Hololens 2-Tutorialreihe](../unreal/tutorials/unreal-uxt-ch1.md)

Sie können jederzeit zu den [Prüfpunkten für die Unreal-Entwicklung](../unreal/unreal-development-overview.md#1-getting-started) zurückkehren.

# <a name="native-openxr"></a>[Nativ (OpenXR)](#tab/native)

 ![Entwicklung nativer Apps](../images/native_logo_banner.png)

Die native OpenXR-Entwicklung verfügt über keine Engine, die Sie herunterladen können. Alles, was Sie benötigen, um mit der Entwicklung zu beginnen, finden Sie im Dokument [Erste Schritte mit OpenXR](../native/openxr-getting-started.md).

### <a name="1-set-up-your-pc-for-mixed-reality-development"></a>1. Einrichten Ihres PCs für die Mixed Reality-Entwicklung

Das Windows SDK funktioniert am besten unter dem Betriebssystem Windows 10. Das SDK wird auch unter folgenden Betriebssystemen unterstützt: Windows 8.1, Windows 8, Windows 7, Windows Server 2012 und Windows Server 2008 R2. Beachten Sie, dass nicht alle Tools unter älteren Betriebssystemen unterstützt werden.

#### <a name="for-hololens-development"></a>HoloLens-Entwicklung

Wenn Sie Ihren Entwicklungs-PC für die HoloLens-Entwicklung einrichten, stellen Sie sicher, dass er die Systemanforderungen für <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> erfüllt. Wenn Sie Ihre App auf einem HoloLens-Gerät ausführen möchten, müssen Sie die [Einrichtungsanweisungen im Windows-Geräteportal](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal) befolgen. Wenn Sie planen, den [HoloLens-Emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md) zu verwenden, sollten Sie sicherstellen, dass Ihr PC auch die [Systemanforderungen des HoloLens-Emulators](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) erfüllt.

Wenn Sie planen, sowohl für HoloLens als auch für immersive Windows Mixed Reality-Headsets (VR) zu entwickeln, verwenden Sie die Systemempfehlungen und Anforderungen im folgenden Abschnitt.

> [!NOTE]
> Sie können Ihre Apps für HoloLens, für immersive Headsets (VR) oder beides entwickeln und bereitstellen. Stellen Sie sicher, dass Sie die unten aufgeführten Anforderungen abhängig von Ihren Anforderungen erfüllen.

#### <a name="hololens-troubleshooting"></a>HoloLens-Problembehandlung

##### <a name="setting-developer-mode-is-grayed-out"></a>Einstellung „Entwicklermodus“ ist abgeblendet

Wenn beim Aktivieren des Entwicklermodus auf Ihrem Gerät Probleme auftreten, sind Sie möglicherweise nicht der [Gerätebesitzer](/hololens/security-adminless-os). Im Mehrbenutzermodus ist die Person, die das Gerät als Erster verwendet, der Gerätebesitzer. Alle nachfolgenden Benutzer verfügen nicht über die erforderlichen Berechtigungen, um den Entwicklermodus zu aktivieren oder andere Konfigurationsänderungen vorzunehmen. Es gibt jedoch eine Ausnahme, bei der der erste Benutzer in einer Autopilot-Umgebung möglicherweise nicht der Besitzer des Geräts ist, die detailliert in der [HoloLens-Sicherheitsdokumentation](/hololens/security-adminless-os#device-owner) beschrieben ist.

Folgende Lösungen sind möglich:

* Bitten Sie den Gerätebesitzer, den Entwicklermodus zu aktivieren, bevor das Gerät an andere Benutzer oder Entwickler übergeben wird.
* Schlagen Sie vor, dass Ihr IT-/MDM-Administrator die CSP-[Richtlinie ApplicationManagement/ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) für das spezifische Gerät oder eine Entwicklergerätegruppe aktiviert. 
    * Diese Richtlinie kann über [Bereitstellungspakete](/hololens/hololens-provisioning) oder über [MDM für HoloLens-Geräte](/hololens/hololens-mdm-configure) festgelegt werden.
* Verwenden des [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery) (Begleiter für erweiterte Wiederherstellung)

> [!NOTE]
> Weitere Informationen zur Geräteverwaltung finden Sie in der Übersicht der **[HoloLens-Geräteverwaltung](/hololens/hololens-csp-policy-overview)** .

#### <a name="immersive-vr-headset-requirements"></a>Anforderungen an immersive Headsets (VR)

>[!NOTE]
>Die folgenden Richtlinien sind die derzeit empfohlenen Mindestanforderungen und Spezifikationen für Ihren *Entwicklungs-PC* für immersive Headsets (VR) und werden regelmäßig aktualisiert.

>[!WARNING]
>Verwechseln Sie dies nicht mit den [Richtlinien zur minimalen PC-Hardwarekompatibilität](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), die die *Spezifikationen von Consumer-PCs* umreißen, auf die Sie Ihre immersive Headset-App (VR) oder Ihr Spiel ausrichten sollten.

Wenn Ihr Entwicklungs-PC für immersive Headsets nicht über vollwertige HDMI- und/oder USB 3.0-Anschlüsse verfügt, benötigen Sie [Adapter](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs), um Ihr Headset anzuschließen.

Es gibt derzeit [bekannte Probleme](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) bei einigen Hardwarekonfigurationen, insbesondere bei Notebooks mit Hybridgrafik.

<table>
<tr>
<th></th><th> Minimum</th><th> Empfohlen</th>
</tr><tr>
<td> Prozessor</td><td> <b>Notebook:</b> Intel Mobile Core i5-CPU der 7. Generation, Dual-Core mit Hyperthreading <b>Desktop:</b> Intel Desktop i5-CPU der 6. Generation, Dual-Core mit Hyperthreading <b>ODER</b> AMD FX4350 mit 4,2 GHz und vier Kernen</td><td> <b>Desktop:</b> Intel Desktop i7 der 6. Generation (6 Kerne) <b>ODER</b> AMD Ryzen 5 1600 (6 Kerne, 12 Threads)</td>
</tr><tr>
<td> GPU</td><td> <b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2 GB) – gleichwertig oder höher, DX12-fähige GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2 GB) – gleichwertig oder höher, DX12-fähige GPU</td><td><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2 GB) – gleichwertig oder höher, DX12-fähige GPU</td>
</tr><tr>
<td> GPU-Treiber (WDDM-Version)</td><td colspan="2"> WDDM 2.2-Treiber</td>
</tr><tr>
<td> Wärmeleistung</td><td colspan="2"> 15 W oder höher</td>
</tr><tr>
<td> Anschlüsse der Grafikanzeige</td><td colspan="2"> Ein verfügbarer Grafikanzeigeanschluss für&#160;Headset (HDMI 1.4 oder DisplayPort 1.2 für Headsets mit 60 Hz, HDMI 2.0 oder DisplayPort 1.2 für Headsets mit 90 Hz)</td>
</tr><tr>
<td> Anzeigeauflösung</td><td colspan="2"> Auflösung: SVGA (800 x 600) oder höhere Bittiefe: Farbe: 32 Bit pro Pixel</td>
</tr><tr>
<td> Memory</td><td> 8&#160;GB RAM oder mehr</td><td> 16 GB RAM oder mehr</td>
</tr><tr>
<td> Speicher</td><td colspan="2"> &gt;10 GB zusätzlicher freier Speicherplatz</td>
</tr><tr>
<td> USB-Anschlüsse</td><td colspan="2"> Ein verfügbare USB-Anschluss für Headset (USB-3.0 Type-A) <b>Hinweis: USB muss mindestens 900 mA bereitstellen</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0 (für den Anschluss von Zubehör)</td>
</tr>
</table>

Wenn Sie neu in die native Entwicklung mit MRTK einsteigen, empfehlen wir, unserer zusammengestellten nativen Entwicklungsreise zu folgen:

> [!div class="nextstepaction"]
> [Antreten Ihrer nativen Journey](../native/directx-development-overview.md)

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie der Prüfpunktreise zur nativen Entwicklung folgen, die wir zusammengestellt haben, besteht Ihre nächste Aufgabe darin, Ihre Entwicklungsumgebung für HoloLens 2 zu konfigurieren.

> [!div class="nextstepaction"]
> [Setup für HoloLens 2](../native/openxr-getting-started.md#getting-started-with-openxr-for-hololens-2)

Sie können jederzeit zu den [Prüfpunkten für die native Entwicklung](../native/directx-development-overview.md#1-getting-started) zurückkehren.