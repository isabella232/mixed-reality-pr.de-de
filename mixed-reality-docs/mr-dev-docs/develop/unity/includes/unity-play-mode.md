---
ms.openlocfilehash: 17719d2547aa10981e7b8cdf0d2c7d56823e6da5
ms.sourcegitcommit: bb9f54f3e872a5464a5d9ba88b7ab5b8896efd82
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2021
ms.locfileid: "110345108"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 und OpenXR](#tab/openxr)

1. Wechseln Sie auf Ihrer HoloLens zum **Microsoft Store,** und installieren Sie die **[Holographic Remoting](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** Player-App.
1. Starten Sie auf Ihrer HoloLens die **Holographic Remoting** Player-App.
1. Wechseln Sie in Unity zum Menü **Bearbeiten,** und wählen Sie **Projekteinstellungen aus.**
1. Wählen Sie **XR-Plug-In-Verwaltung aus.**
1. Stellen Sie sicher, dass die Registerkarte **Windows Standalone** ausgewählt ist, suchen Sie in der Liste nach **OpenXR** und **Windows Mixed Reality Featuresatz,** und aktivieren Sie deren Kontrollkästchen.
1. Wechseln Sie als Nächstes zum Menü **Fenster,** erweitern Sie das **XR-Untermenü,** und wählen Sie **OpenXR Editor Remoting** aus.
1. Klicken Sie auf **Editorremoting aktivieren.**
1. Wenn die Schaltfläche **Fehlende Abhängigkeiten aktivieren** angezeigt wird, klicken Sie auch darauf. Im Fehlerfeld über der Schaltfläche werden die aktivierten Features und die Gründe beschrieben.
1. Geben Sie unter **Remotehostname** die IP-Adresse Ihrer HoloLens ein.
   1. Ändern Sie nach Bedarf andere Einstellungen.
   1. Der Editor versucht, eine Verbindung herzustellen, nachdem der Wiedergabemodus gestartet wurde.
1. Wählen Sie die Schaltfläche **Wiedergeben** aus, um den Wiedergabemodus zu starten und die App auf Ihrer HoloLens zu erleben.

# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 und Windows-XR-Plugin](#tab/winxr)

1. Wechseln Sie auf Ihrer HoloLens zum **Microsoft Store,** und installieren Sie die **[Holographic Remoting](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** Player-App.
1. Starten Sie auf Ihrer HoloLens die **Holographic Remoting** Player-App.
1. Wechseln Sie in Unity zum Menü **Bearbeiten,** und wählen Sie **Projekteinstellungen aus.**
1. Wählen Sie **XR-Plug-In-Verwaltung aus.**
1. Stellen Sie sicher, dass die Registerkarte **Windows Standalone** ausgewählt ist, suchen **Sie Windows Mixed Reality** in der Liste, und aktivieren Sie das Kontrollkästchen.
1. Wechseln Sie als Nächstes zum Menü **Fenster,** erweitern Sie das **XR-Untermenü,** und wählen Sie Windows **XR-Plug-In-Remoting** aus.
1. Legen Sie **emulation mode (Emulationsmodus)** auf **Remote auf Device (Gerät) fest.**
1. Geben Sie unter **Remotecomputer** die IP-Adresse Ihrer HoloLens ein.
1. So stellen Sie eine Verbindung her:
   1. Um eine manuelle Verbindung herzustellen, deaktivieren Sie Verbinden in **Play,** und wählen **Sie Verbinden** aus. Es sollte angezeigt werden, dass sich **der Verbindungsstatus** in **Verbunden** ändert und der Bildschirm in der HoloLens leer ist.
   1. Um automatisch eine Verbindung herzustellen, aktivieren **Sie Verbinden bei Play**. Der Editor versucht, eine Verbindung herzustellen, nachdem der Wiedergabemodus gestartet wurde.
1. Wählen Sie die Schaltfläche **Wiedergeben** aus, um den Wiedergabemodus zu starten und die App auf Ihrer HoloLens zu erleben.

# <a name="legacy-wsa"></a>[Legacy-WSA](#tab/wsa)

1. Wechseln Sie auf Ihrer HoloLens zum **Microsoft Store,** und installieren Sie die **[Holographic Remoting](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** Player-App.
1. Starten Sie auf Ihrer HoloLens die **Holographic Remoting** Player-App.
1. Wechseln Sie in Unity zum Menü **Fenster,** erweitern Sie das **XR-Untermenü,** und wählen Sie **Holographic Emulation** (in Unity 2019 als veraltet markiert) aus.
1. Legen Sie **emulation mode (Emulationsmodus)** auf **Remote auf Device (Gerät) fest.**
1. Legen Sie **geräteversion** entsprechend fest, wenn Sie eine HoloLens der ersten Generation oder eine HoloLens 2 verwenden.
1. Geben Sie unter **Remotecomputer** die IP-Adresse Ihrer HoloLens ein.
1. Wählen Sie **Verbinden** aus. Es sollte angezeigt werden, dass sich **der Verbindungsstatus** in **Verbunden** ändert und der Bildschirm in der HoloLens leer ist.
1. Wählen Sie die Schaltfläche **Wiedergeben** aus, um den Wiedergabemodus zu starten und die App auf Ihrer HoloLens zu erleben.
