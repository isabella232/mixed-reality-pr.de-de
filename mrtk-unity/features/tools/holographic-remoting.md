---
title: Holographic Remoting
description: 'Dokumentation: Holographic Remoting MRTK'
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 0fbde863185a9f51b53192a338e9403dc79248db
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176647"
---
# <a name="holographic-remoting"></a>Holographic Remoting

Holographic Remoting streamt holografische Inhalte von einem PC Microsoft HoloLens in Echtzeit mithilfe einer Wi-Fi oder USB-Kabelverbindung an Ihren Computer. Dieses Feature kann die Entwicklerproduktivität bei der Entwicklung von Mixed Reality-Anwendungen erheblich steigern.

Das XR SDK, wie unten erwähnt, bezieht sich auf die neue XR-Pipeline von [Unity in Unity 2019.3 und darüber hinaus.](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) Weitere [Informationen](../../configuration/getting-started-with-mrtk-and-xrsdk.md) zur Verwendung des XR SDK mit MRTK finden Sie hier. Legacy-XR bezieht sich auf die vorhandene XR-Pipeline, die in Unity 2018 enthalten ist, in Unity 2019.3 veraltet und in Unity 2020 entfernt wurde.

## <a name="initial-setup"></a>Erste Einrichtung

Um Remoting für eine HoloLens zu aktivieren, ist es wichtig sicherzustellen, dass das Projekt die neuesten Remotingkomponenten verwendet.

1. Fenster **öffnen > Paket-Manager**
    - Bei Verwendung von Legacy-XR: Überprüfen Sie, ob die neueste Version des Windows Mixed Reality **installiert** ist.
    - Bei Verwendung des XR SDK: Überprüfen Sie, ob die neueste Version des Windows **XR-Plug-In-Pakets** installiert ist.
1. Stellen Sie sicher, dass die neueste Holographic Remoting-Anwendung über die HoloLens installiert Microsoft Store.

Fahren Sie mit [den Legacy-XR-Setupanweisungen](#legacy-xr-setup-instructions) oder [XR](#xr-sdk-setup-instructions) SDK-Setupanweisungen fort, je nachdem, welche Pipeline im Projekt verwendet wird.

## <a name="legacy-xr-setup-instructions"></a>Legacy-XR-Setupanweisungen

Die folgenden Anweisungen gelten nur für Remoting mit HoloLens 2. Wenn Sie remoting nur mit HoloLens (1. Generation) ausführen, fahren Sie mit Herstellen einer Verbindung mit dem HoloLens [mit WLAN ab.](#connecting-to-the-hololens-with-wi-fi)

Wenn Sie eine HoloLens 2 verwenden, wurde dem MRTK Unterstützung für remoting artikulierte Hand- und Eyetrackingdaten hinzugefügt. Um diese Features zu aktivieren, führen Sie die schritte aus, die unter [Importieren von DotNetWinRT in das Projekt dokumentiert sind.](#import-dotnetwinrt-into-the-project)

Nach dem Importieren wählen Sie im nächsten Schritt Mixed Reality Toolkit-Hilfsprogramme  >    >    >  **Windows Mixed Reality**  >  **Konfiguration überprüfen aus.** In diesem Schritt wird eine Skripterstellungs definieren, die die DotNetWinRT-Abhängigkeit aktiviert.

> [!NOTE]
> Bei Verwendung von Unity 2019.4 und einer neueren Version ist es nicht erforderlich, das Hilfsprogramm Konfiguration überprüfen ausführen.

Führen Sie die Schritte in den Abschnitten Debuggen HoloLens 2 **Remoting** per Unity-Paketimport und verwandten Abschnitten aus, um die Nachverfolgung von Handgelenken und Eyetracking zu aktivieren.

### <a name="debugging-hololens-2-remoting-via-unity-package-import"></a>Debuggen HoloLens 2 Remoting über den Unity-Paketimport

Wenn HoloLens 2 Hand- und Eyetracking nicht über Remoting arbeiten, gibt es einige häufige Probleme. Sie sind unten in der Reihenfolge aufgeführt, in der sie überprüft werden sollten.

Diese Probleme sind besonders relevant, wenn sie unter **Unity 2019.3 oder** höher ausgeführt werden.

#### <a name="import-dotnetwinrt-into-the-project"></a>Importieren von DotNetWinRT in das Projekt

1. Herunterladen des [Mixed Reality Featuretools](https://aka.ms/MRFeatureTool)

1. Wählen Sie **in der Ansicht** Features entdecken Mixed Reality *WinRT-Projektionen aus.*

    ![Auswählen des DotNetWinRT-Pakets](../images/tools/remoting/SelectDotNetWinRT.png)

1. Klicken **Sie auf Features erhalten,** und fahren Sie mit dem Importieren des [Pakets fort.](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#3-importing-feature-packages)

#### <a name="dotnetwinrt_present-define-written-into-player-settings"></a>DOTNETWINRT_PRESENT definition written into player settings (In Playereinstellungen geschriebene Definition)

> [!NOTE]
> Bei Verwendung von Unity 2019.4 und neuer ist die DOTNETWINRT_PRESENT-Definition in den entsprechenden ASMDEF-Dateien enthalten und nicht in der Unity Player-Einstellungen. Der Schritt Konfiguration überprüfen ist nicht erforderlich.

Ab MRTK Version 2.5.0 wird diese #define aus Leistungsgründen nicht mehr automatisch festgelegt. Um dieses Flag zu aktivieren, verwenden Sie Mixed Reality Toolkit-Hilfsprogramme  >    >  **Windows Mixed Reality**  >  **Menüelement Konfiguration** überprüfen.

> [!Note]
> Das Element Konfiguration überprüfen zeigt keine Bestätigung an. Um zu bestätigen, dass die Definition festgelegt wurde, navigieren Sie zum Unity Player-Einstellungen. Überprüfen Sie dort auf der Registerkarte UWP unter Andere Einstellungen Skripterstellungssymbole definieren. Stellen Sie sicher, DOTNETWINRT_PRESENT ordnungsgemäß in diese Liste geschrieben ist. Wenn dies der Fall ist, war dieser Schritt erfolgreich.

![DotNetWinRT vorhanden](../images/tools/remoting/DotNetWinRTPresent.png)

### <a name="removing-hololens-2-specific-remoting-support"></a>Entfernen HoloLens 2 spezifischen Remotingunterstützung

Wenn Konflikte oder andere Probleme aufgrund des Vorhandenseins des DotNetWinRT-Adapters auftreten, wenden Sie sich an eine unserer [Hilferessourcen.](../../index.md#getting-help)

## <a name="xr-sdk-setup-instructions"></a>Setupanweisungen für das XR SDK

Befolgen Sie die Windows Mixed Reality-Setupanweisungen auf der Seite Erste Schritte mit [MRTK und XR SDK,](../../configuration/getting-started-with-mrtk-and-xrsdk.md#windows-mixed-reality) und stellen Sie sicher, dass Sie den schritt ausführen, der für remoting im Editor HoloLens ist.

## <a name="connecting-to-the-hololens-with-wi-fi"></a>Herstellen einer Verbindung mit dem HoloLens mit Wi-Fi

Nachdem das Projekt konfiguriert wurde, kann eine Verbindung mit dem Projekt hergestellt HoloLens.

1. Stellen **Sie > Build Einstellungen** sicher, dass der Projekt-Buildtyp auf Universal Windows Platform festgelegt **ist.**
1. Starten Sie HoloLens die **Holographic Remoting-Anwendung.**
1. Wählen Sie in Unity **Window > XR > Holographic Emulation (bei Verwendung von Legacy-XR) /Windows XR-Plug-In-Remoting (bei** Verwendung des XR SDK) aus.

    ![Starten der Holographic Emulation](../images/tools/remoting/StartHolographicEmulation.png)

1. Legen **Sie den Emulationsmodus** auf **Remote auf Gerät fest.**

    ![Festlegen des Emulationsmodus](../images/tools/remoting/SelectEmulationMode.png)

1. (**_Gilt nur für legacy XR_**) Wählen Sie die **Geräteversion aus.**

    ![Auswählen der Geräteversion](../images/tools/remoting/SelectDeviceVersion.png)

1. Legen Sie mithilfe der IP-Adresse, die von der Holographic Remoting Player-Anwendung angezeigt wird, das **Feld Remotecomputer** fest.

    ![Ip-Adresse eingeben](../images/tools/remoting/EnterIPAddress.png)

1. Klicken Sie auf **Verbinden**.

> [!NOTE]
> Wenn Sie keine Verbindung herstellen können, stellen Sie sicher, HoloLens 2 nicht an Ihren PC angeschlossen ist, und starten Sie Unity neu.

## <a name="connecting-to-the-hololens-with-usb-cable"></a>Herstellen einer Verbindung mit dem HoloLens über ein USB-Kabel

Die USB-Kabelverbindung bietet eine bessere Renderingqualität und -stabilität. Um die USB-Kabelverbindung zu verwenden, trennen Sie die Verbindung HoloLens von Wi-Fi im HoloLens des Einstellungen, und starten Sie die Holographic Remoting Player-App. Es wird eine IP-Adresse angezeigt, die mit 169 beginnt. Verwenden Sie diese IP-Adresse in der Holographic Emulation-Einstellung von Unity, um eine Verbindung herzustellen. Nachdem die IP-Adresse für das USB-Kabel identifiziert wurde, ist es sicher, die Ip HoloLens wieder Wi-Fi verbinden.

## <a name="starting-a-remoting-session"></a>Starten einer Remotingsitzung

Wenn Unity mit dem HoloLens verbunden ist, wechseln Sie im Editor in den Wiedergabemodus.

Wenn die Sitzung abgeschlossen ist, beenden Sie den Wiedergabemodus.

> [!NOTE]
> Es gibt ein bekanntes Problem mit einigen Versionen von Unity, bei dem der Editor während einer Remotingsitzung beim Wechseln in den Wiedergabemodus hängen bleibt. Dieses Problem kann sich manifestieren, wenn das Holographic-Fenster geöffnet ist, wenn das Projekt geladen wird. Um sicherzustellen, dass dieses Problem nicht auftritt, schließen Sie immer den Holographic-Dialog, bevor Sie Unity beenden.

## <a name="see-also"></a>Siehe auch

- [Problembehandlung und Einschränkungen bei Holographic Remoting](/windows/mixed-reality/holographic-remoting-troubleshooting)
- [Microsoft Holographic Remoting-Softwarelizenzbedingungen](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
