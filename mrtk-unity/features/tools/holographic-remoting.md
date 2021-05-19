---
title: Holographic Remoting
description: 'Dokumentation: Holographic Remoting MRTK'
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 637f68e5ad5f360aea4b5c0603a682d61d152a89
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144582"
---
# <a name="holographic-remoting"></a>Holographic Remoting

Holographic Remoting streamt holografische Inhalte in Echtzeit über eine Wi-Fi- oder USB-Kabelverbindung von einem PC an Ihren Microsoft HoloLens. Dieses Feature kann die Produktivität von Entwicklern bei der Entwicklung von Mixed Reality-Anwendungen erheblich steigern.

Das XR SDK bezieht sich wie unten erwähnt auf die [neue XR-Pipeline von Unity in Unity 2019.3 und darüber hinaus.](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) Weitere Informationen zur Verwendung des XR SDK mit MRTK finden Sie [hier.](../../configuration/getting-started-with-mrtk-and-xrsdk.md) Legacy-XR bezieht sich auf die vorhandene XR-Pipeline, die in Unity 2018 enthalten ist, in Unity 2019.3 veraltet ist und in Unity 2020 entfernt wurde.

## <a name="initial-setup"></a>Erste Einrichtung

Um Remoting für eine HoloLens zu aktivieren, müssen Sie sicherstellen, dass das Projekt die neuesten Remotingkomponenten verwendet.

1. > Paket-Manager **"Fenster öffnen"**
    - Bei Verwendung von Legacy-XR: Überprüfen Sie, ob die neueste Version des **Windows Mixed Reality** Pakets installiert ist.
    - Bei Verwendung des XR SDK: Überprüfen Sie, ob die neueste Version des **Windows XR-Plug-In-Pakets** installiert ist.
1. Stellen Sie sicher, dass die neueste Holographic Remoting-Anwendung auf der HoloLens über die Microsoft Store installiert ist.

Fahren Sie mit [Legacy-XR-Setupanweisungen](#legacy-xr-setup-instructions) oder [XR SDK-Setupanweisungen](#xr-sdk-setup-instructions) fort, je nachdem, welche Pipeline im Projekt verwendet wird.

## <a name="legacy-xr-setup-instructions"></a>Legacy-XR-Setupanweisungen

Die folgenden Anweisungen gelten nur für Remoting mit HoloLens 2. Wenn Sie nur Remoting mit HoloLens (1. Generation) ausführen, fahren Sie mit [Herstellen einer Verbindung mit HoloLens mit WLAN](#connecting-to-the-hololens-with-wi-fi)weiter.

Bei Verwendung eines HoloLens 2 wurde MRTK Unterstützung für Remoting von Hand- und Blickverfolgungsdaten hinzugefügt. Um diese Funktionen zu aktivieren, führen Sie die Schritte aus, die unter [Importieren von DotNetWinRT in das Projekt](#import-dotnetwinrt-into-the-project)dokumentiert sind.

Nach dem Importieren besteht der nächste Schritt darin, **Mixed Reality**  >  **Toolkit-Hilfsprogramme**  >  **Windows Mixed Reality**  >  **Konfiguration überprüfen** auszuwählen. In diesem Schritt wird eine Skripterstellungs-Definition hinzugefügt, die die DotNetWinRT-Abhängigkeit aktiviert.

> [!NOTE]
> Bei Verwendung von Unity 2019.4 und neuer ist es nicht erforderlich, das Hilfsprogramm Konfiguration überprüfen auszuführen.

Führen Sie die Schritte in den Abschnitten Debuggen HoloLens 2 **Remoting** per Unity-Paketimport und verwandten Abschnitten aus, um die Nachverfolgung von Handgelenken und Eyetracking zu aktivieren.

### <a name="debugging-hololens-2-remoting-via-unity-package-import"></a>Debuggen HoloLens 2 remoting per Unity-Paketimport

Wenn HoloLens 2 Hand- und Eyetracking nicht über Remoting arbeiten, gibt es einige häufige Probleme. Sie sind unten in der Reihenfolge aufgeführt, in der sie überprüft werden sollten.

Diese Probleme sind besonders relevant, wenn sie unter **Unity 2019.3 oder** höher ausgeführt werden.

#### <a name="import-dotnetwinrt-into-the-project"></a>Importieren von DotNetWinRT in das Projekt

1. Herunterladen des [Mixed Reality Featuretools](https://aka.ms/MRFeatureTool)

1. Wählen Sie **in der Ansicht** Features entdecken Mixed Reality *WinRT-Projektionen aus.*

    ![Auswählen des DotNetWinRT-Pakets](../images/tools/remoting/SelectDotNetWinRT.png)

1. Klicken **Sie auf Features erhalten,** und fahren Sie mit dem Importieren des [Pakets fort.](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#3-importing-feature-packages)

#### <a name="dotnetwinrt_present-define-written-into-player-settings"></a>DOTNETWINRT_PRESENT definition written into player settings (In Playereinstellungen geschriebene Definition)

> [!NOTE]
> Bei Verwendung von Unity 2019.4 und neuer ist die DOTNETWINRT_PRESENT-Definition in den entsprechenden ASMDEF-Dateien und nicht in den Unity Player-Einstellungen enthalten. Der Schritt Konfiguration überprüfen ist nicht erforderlich.

Ab MRTK Version 2.5.0 wird diese #define aus Leistungsgründen nicht mehr automatisch festgelegt. Um dieses Flag zu aktivieren, verwenden Sie Mixed Reality Toolkit-Hilfsprogramme  >    >  **Windows Mixed Reality**  >  **Menüelement Konfiguration** überprüfen.

> [!Note]
> Das Element Konfiguration überprüfen zeigt keine Bestätigung an. Um zu bestätigen, dass die Definition festgelegt wurde, navigieren Sie zu unity player settings (Unity-Playereinstellungen). Überprüfen Sie dort auf der Registerkarte UWP unter Weitere Einstellungen die Skripterstellung Symbole definieren. Stellen Sie sicher, DOTNETWINRT_PRESENT ordnungsgemäß in diese Liste geschrieben ist. Wenn dies der Fall ist, war dieser Schritt erfolgreich.

![DotNetWinRT Present](../images/tools/remoting/DotNetWinRTPresent.png)

### <a name="removing-hololens-2-specific-remoting-support"></a>Entfernen HoloLens 2-spezifischer Remotingunterstützung

Wenn aufgrund des Vorhandenseins des DotNetWinRT-Adapters Konflikte oder andere Probleme auftreten, wenden Sie [sich an eine unserer Hilferessourcen.](../../index.md#getting-help)

## <a name="xr-sdk-setup-instructions"></a>Setupanweisungen für das XR SDK

Befolgen Sie die [Windows Mixed Reality Setupanweisungen auf der Seite Erste Schritte mit MRTK und XR SDK,](../../configuration/getting-started-with-mrtk-and-xrsdk.md#windows-mixed-reality) und stellen Sie sicher, dass Sie den für HoloLens-Remoting im Editor erforderlichen Schritt ausführen.

## <a name="connecting-to-the-hololens-with-wi-fi"></a>Herstellen einer Verbindung mit HoloLens mit Wi-Fi

Nachdem das Projekt konfiguriert wurde, kann eine Verbindung mit der HoloLens hergestellt werden.

1. Stellen Sie **unter Datei > Buildeinstellungen** sicher, dass der Projektbuildtyp auf **Universelle Windows-Plattform**
1. Starten Sie auf der HoloLens die **Holographic Remoting-Anwendung.**
1. Wählen Sie in Unity **Window > XR > Holographic Emulation (bei Verwendung von Legacy-XR) /Windows XR-Plug-In-Remoting (bei Verwendung des XR SDK) aus.**

    ![Starten der Holographic Emulation](../images/tools/remoting/StartHolographicEmulation.png)

1. Legen Sie **emulation mode (Emulationsmodus)** auf **Remote auf Device (Gerät) fest.**

    ![Festlegen des Emulationsmodus](../images/tools/remoting/SelectEmulationMode.png)

1. (**_Gilt nur für legacy XR_**) Wählen Sie die **Geräteversion aus.**

    ![Auswählen der Geräteversion](../images/tools/remoting/SelectDeviceVersion.png)

1. Legen Sie mithilfe der IP-Adresse, die von der Holographic Remoting Player-Anwendung angezeigt wird, das Feld **Remotecomputer** fest.

    ![Geben Sie die IP-Adresse ein.](../images/tools/remoting/EnterIPAddress.png)

1. Klicken Sie auf **Verbinden**.

> [!NOTE]
> Wenn Sie keine Verbindung herstellen können, stellen Sie sicher, dass Ihr HoloLens 2 nicht an Ihren PC angeschlossen ist, und starten Sie Unity neu.

## <a name="connecting-to-the-hololens-with-usb-cable"></a>Herstellen einer Verbindung mit der HoloLens per USB-Kabel

Usb-Kabelverbindung bietet eine bessere Renderingqualität und Stabilität. Um die USB-Kabelverbindung zu verwenden, trennen Sie die HoloLens Wi-Fi in den HoloLens-Einstellungen, und starten Sie die Holographic Remoting Player-App. Es wird eine IP-Adresse angezeigt, die mit 169 beginnt. Verwenden Sie diese IP-Adresse in der Holographic Emulation-Einstellung von Unity, um eine Verbindung herzustellen. Nachdem die IP-Adresse für das USB-Kabel identifiziert wurde, ist es sicher, die HoloLens wieder mit Wi-Fi verbinden.

## <a name="starting-a-remoting-session"></a>Starten einer Remotingsitzung

Wenn Unity mit der HoloLens verbunden ist, wechseln Sie im Editor in den Wiedergabemodus.

Wenn die Sitzung abgeschlossen ist, beenden Sie den Wiedergabemodus.

> [!NOTE]
> Es gibt ein bekanntes Problem mit einigen Versionen von Unity, bei dem der Editor während einer Remotingsitzung beim Wechseln in den Wiedergabemodus hängen bleibt. Dieses Problem kann sich manifestieren, wenn das Holographic-Fenster geöffnet ist, wenn das Projekt geladen wird. Um sicherzustellen, dass dieses Problem nicht auftritt, schließen Sie immer den Holographic-Dialog, bevor Sie Unity beenden.

## <a name="see-also"></a>Weitere Informationen

- [Problembehandlung und Einschränkungen bei Holographic Remoting](/windows/mixed-reality/holographic-remoting-troubleshooting)
- [Microsoft Holographic Remoting-Softwarelizenzbedingungen](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)