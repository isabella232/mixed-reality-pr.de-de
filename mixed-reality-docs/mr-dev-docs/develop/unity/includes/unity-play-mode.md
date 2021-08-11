---
ms.openlocfilehash: f579cb73389d23be5959d212d4243361f00a27b8475ce74a16acc2bffa7a192b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192181"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 und OpenXR](#tab/openxr)

1. Wechseln Sie HoloLens-App zum **Microsoft Store,** und installieren Sie die **[Holographic Remoting Player-App.](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)**
1. Starten Sie HoloLens Ihrem Computer die **Holographic Remoting Player-App.**
1. Wechseln Sie in Unity zum Menü **Bearbeiten,** und wählen Sie **Project Einstellungen.**
1. Wählen Sie **XR Plug-In Management (XR-Plug-In-Verwaltung) aus.**
1. Stellen Sie **sicher, Windows** registerkarte Eigenständig ausgewählt ist, suchen Sie in der Liste **nach OpenXR** und **Windows Mixed Reality** Featuresatz, und aktivieren Sie deren Kontrollkästchen.
1. Wechseln Sie als Nächstes zum Menü **Fenster,** erweitern Sie das **XR-Untermenü,** und wählen Sie **OpenXR-Editor-Remoting aus.**

    ![Screenshot des Im Unity-Editor geöffneten Fensters "Projekteinstellungen" mit hervorgehobener XR-Plug-In-Verwaltung](../images/openxr-features-img-02.png)

1. Klicken Sie **auf Editor-Remoting aktivieren.**

    ![Screenshot des Im Unity-Editor geöffneten Fensters "Projekteinstellungen" mit hervorgehobenen Features](../images/openxr-features-img-03.png)

1. Wenn die **Schaltfläche Fehlende Abhängigkeiten aktivieren** angezeigt wird, klicken Sie auch darauf. Das Fehlerfeld über der Schaltfläche beschreibt die Funktionen, die es ermöglicht, und warum.
1. Geben **Sie unter Remotehostname** die IP-Adresse Ihrer HoloLens.
   1. Ändern Sie nach Bedarf andere Einstellungen.
   1. Der Editor versucht, eine Verbindung herzustellen, nachdem der Wiedergabemodus gestartet wurde.
1. Wählen Sie die **Schaltfläche Wiedergabe** aus, um den Wiedergabemodus zu starten und die App in Ihrem HoloLens. Um C#-Skripts im Wiedergabemodus zu debuggen, fügen Sie [Visual Studio Unity an.](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows)

> [!NOTE]
> Ab Version 0.1.0 unterstützt die Holographic Remoting-Runtime keine Anchors, und ARAnchorManager-Funktionen funktionieren nicht über Remoting.  Dieses Feature wird in zukünftigen Versionen veröffentlicht.

# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 und Windows-XR-Plugin](#tab/winxr)

1. Wechseln Sie HoloLens-App zum **Microsoft Store,** und installieren Sie die **[Holographic Remoting Player-App.](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)**
1. Starten Sie HoloLens Ihrem Computer die **Holographic Remoting Player-App.**
1. Wechseln Sie in Unity zum Menü **Bearbeiten,** und wählen Sie **Project Einstellungen.**
1. Wählen Sie **XR Plug-In Management (XR-Plug-In-Verwaltung) aus.**
1. Stellen Sie sicher, dass die Registerkarte **PC, Mac & Linux Standalone** ausgewählt ist, suchen Sie Windows Mixed Reality in der Liste, und aktivieren Sie das Kontrollkästchen. 
1. Wechseln Sie als Nächstes zum Menü **Fenster,** erweitern Sie das **XR-Untermenü,** und wählen Sie Windows **XR-Plug-In-Remoting aus.**
1. Legen **Sie den Emulationsmodus** auf **Remote auf Gerät fest.**
1. Geben **Sie unter Remotecomputer** die IP-Adresse Ihrer HoloLens.
1. So stellen Sie eine Der beiden:
   1. Um manuell eine Verbindung herzustellen, deaktivieren Sie **Verbinden wiederzugeben,** und wählen Sie **Verbinden.** Der Verbindungsstatus **sollte in** Verbunden geändert **werden,** und der Bildschirm wird im HoloLens.
   1. Um automatisch eine Verbindung herzustellen, aktivieren Sie **Verbinden wieder.** Der Editor versucht, eine Verbindung herzustellen, nachdem der Wiedergabemodus gestartet wurde.
1. Wählen Sie die **Schaltfläche Wiedergabe** aus, um den Wiedergabemodus zu starten und die App in Ihrem HoloLens. Um C#-Skripts im Wiedergabemodus zu debuggen, fügen Sie [Visual Studio Unity an.](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows)

# <a name="legacy-wsa"></a>[Legacy-WSA](#tab/wsa)

1. Wechseln Sie HoloLens-App zum **Microsoft Store,** und installieren Sie die **[Holographic Remoting Player-App.](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)**
1. Starten Sie HoloLens Ihrem Computer die **Holographic Remoting Player-App.**
1. Wechseln Sie in  Unity zum Menü Fenster, erweitern Sie das **XR-Untermenü,** und wählen Sie **Holographic Emulation** (in Unity 2019 als veraltet markiert) aus.
1. Legen **Sie den Emulationsmodus** auf **Remote auf Gerät fest.**
1. Legen **Sie Die Geräteversion** entsprechend fest, wenn Sie ein Gerät der ersten Generation HoloLens oder ein HoloLens 2.
1. Geben **Sie unter Remotecomputer** die IP-Adresse Ihrer HoloLens.
1. Wählen Sie **Verbinden** aus. Der Verbindungsstatus **sollte in** Verbunden geändert **werden,** und der Bildschirm wird im HoloLens.
1. Wählen Sie die **Schaltfläche Wiedergabe** aus, um den Wiedergabemodus zu starten und die App in Ihrem HoloLens. Um C#-Skripts im Wiedergabemodus zu debuggen, fügen Sie [Visual Studio Unity an.](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows)
