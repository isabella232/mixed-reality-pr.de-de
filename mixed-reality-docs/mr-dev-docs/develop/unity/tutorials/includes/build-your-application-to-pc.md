---
ms.openlocfilehash: 2886a9ad26ff38a2051d4ea6961286e1e190588128a2f045ae39841470113157
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198030"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 und OpenXR](#tab/openxr)

### <a name="1-switching-build-platform"></a>1. Wechseln der Buildplattform

Wählen Sie im Unity-Menü „File > Build Settings“ (Datei > Buildeinstellungen) aus, um das Fenster „Build Settings“ (Buildeinstellungen) zu öffnen.

Wählen Sie im Fenster „Build Settings“ (Buildeinstellungen) die Plattform **PC, Mac & Linux Standalone** aus, und klicken Sie auf die Schaltfläche **Switch Platform** (Plattform wechseln), um die Buildplattform zu ändern:

![Wechseln der Buildplattform](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-1.PNG)

Wenn Unity den Plattformwechsel abgeschlossen hat, klicken Sie auf das x-Symbol, um das Fenster mit den Buildeinstellungen zu schließen.

### <a name="2-set-the-project-settings"></a>2. Festlegen der Projekteinstellungen

Wählen Sie im Unity-Menü **Edit** > **Project Settings** > **XR Plug-In Management** aus, stellen Sie sicher, dass Sie sich auf der Registerkarte „Windows Standalone“ (Windows eigenständig) befinden, und aktivieren Sie das Kontrollkästchen **OpenXR** und **Windows Mixed Reality Feature set** (Windows Mixed Reality-Featuresatz).

![Aktivieren von OpenXR und Windows Mixed Reality-Featuresatz](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-2.PNG)

Wählen Sie im Fenster „Project Settings“ (Projekteinstellungen) **OpenXR** aus, und stellen Sie sicher, dass Sie sich auf der Registerkarte „Windows Standalone“ (Windows eigenständig) befinden, und ändern Sie den **Depth sumission mode** (Tiefenübermittlungsmodus) von „None“ (Ohne) in **Depth 16 Bit** (16 Bit Tiefe).

Fügen Sie auf der Registerkarte „Interaction profiles“ (Interaktionsprofile) das **Eye Gaze Interaction Profile** („Anvisieren mit den Augen“-Interaktionsprofil) und das **Microsoft Hand Interaction Profile** (Microsoft-Handinteraktions-Profil) hinzu, indem Sie auf das Symbol „+“ klicken.

![Hinzufügen des Interaktionsprofils „Anvisieren mit den Augen" und des Microsoft-Handinteraktionsprofils](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-3.PNG)

Aktivieren Sie unter **Open XR feature groups** > **All features** (XR-Featuregruppen öffnen > Alle Features) das Kontrollkästchen **Holographic App Remoting**.

![Aktivieren von Holographic App Remoting](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-4.PNG)

Aktivieren Sie als Nächstes das Kontrollkästchen **Windows Mixed Reality**, und aktivieren Sie unter der Gruppe „Windows Mixed Reality“ das Kontrollkästchen **Holographic App Remoting**.

![Aktivieren von Windows Mixed Reality Holographic App Remoting](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-5.PNG)

### <a name="3-build-the-unity-project"></a>3. Erstellen des Unity-Projekts

Wählen Sie im Unity-Menü „File > Build Settings“ (Datei > Buildeinstellungen) aus, um das Fenster „Build Settings“ (Buildeinstellungen) zu öffnen.

Klicken Sie im Fenster „Build Settings“ (Buildeinstellungen) auf die Schaltfläche ***Add Open Scenes** _ (Geöffnete Szenen hinzufügen), um den Szenen die aktuelle Szene hinzuzufügen. Klicken Sie in der Build-Liste dann auf die Schaltfläche _ *Build**:

![Unity-Fenster „Build Settings“ mit hinzugefügter Szene](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-6.PNG)

Wählen Sie einen geeigneten Speicherort zum Speichern Ihres Builds aus, z. B. „Documents\MixedRealityLearning“. Erstellen Sie einen neuen Ordner, und geben Sie ihm einen geeigneten Namen, z. B. „PCHolographicRemoting“. Klicken Sie dann auf die Schaltfläche ***Select Folder*** (Ordner auswählen), um den Buildprozess zu starten:

![Unity-Fenster „Build Settings“ mit Aufforderungsfenster zum Auswählen eines Ordners](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-7.png)

Warten Sie, bis Unity den Buildvorgang abgeschlossen hat.

![Unity: Buildvorgang wird ausgeführt](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-8.png)

Doppelklicken Sie auf die ausführbare Datei, um die PC Holographic Remoting-Anwendung auf Ihrem PC zu öffnen.

> [!NOTE]
> Aufgrund einiger bekannter Probleme in der als UWP erstellten Holographic Remoting für PC-App erstellen wir die PC-App als Windows Standalone für OpenXR.


# <a name="legacy-wsa"></a>[Legacy-WSA](#tab/wsa)

### <a name="1-set-the-player-settings"></a>1. Festlegen der Playereinstellungen

Aktivieren Sie im Abschnitt **XR Settings** (XR-Einstellungen) das Kontrollkästchen **WSA Holographic Remoting Supported** (WSA Holographic Remoting unterstützt), und aktivieren Sie Holographic Remoting.

![Unity-Fenster XR-Einstellungen mit aktiviertem „WSA Holographic Remoting Supported“](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step1-1.png)

### <a name="2-build-the-unity-project"></a>2. Erstellen des Unity-Projekts

Wählen Sie im Unity-Menü „File > Build Settings“ (Datei > Buildeinstellungen) aus, um das Fenster „Build Settings“ (Buildeinstellungen) zu öffnen.

Klicken Sie im Fenster „Build Settings“ (Buildeinstellungen) auf die Schaltfläche ***Add Open Scenes** _ (Geöffnete Szenen hinzufügen), um den Szenen die aktuelle Szene hinzuzufügen. Klicken Sie in der Liste „Build“ auf die Schaltfläche _ *_Build_**, um das Fenster „Build Universal Windows Platform“ (Universelle Windows-Plattform erstellen) zu öffnen:

![Unity-Fenster „Build Settings“ mit hinzugefügter Szene](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-1.png)

Wählen Sie im Fenster „Build Universal Windows Platform“ einen passenden Speicherort zum Speichern Ihres Builds aus, z. B. „Documents\MixedRealityLearning“. Erstellen Sie einen neuen Ordner, und geben Sie ihm einen geeigneten Namen, z. B. „PCHolographicRemoting“. Klicken Sie dann auf die Schaltfläche ***Select Folder*** (Ordner auswählen), um den Buildprozess zu starten:

![Unity-Fenster „Build Settings“ mit Aufforderungsfenster zum Auswählen eines Ordners](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-2.png)

Warten Sie, bis Unity den Buildvorgang abgeschlossen hat.

![Unity: Buildvorgang wird ausgeführt](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-3.png)

### <a name="3-build-and-deploy-the-application"></a>3. Erstellen und Bereitstellen der Anwendung

Wenn der Buildvorgang abgeschlossen ist, fordert Unity den Windows Datei-Explorer auf, den Speicherort zu öffnen, in dem Sie den Build gespeichert haben. Navigieren Sie im Ordner, und doppelklicken Sie auf die SLN-Datei, um sie in Visual Studio zu öffnen:

![Windows-Explorer mit neu erstellter, ausgewählter Visual Studio-Projektmappe](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-1.png)

> [!NOTE]
> Wenn Sie von Visual Studio zur Installation neuer Komponenten aufgefordert werden, nehmen Sie sich einen Moment Zeit, um zu überprüfen, ob alle erforderlichen Komponenten (wie in der Dokumentation „Installieren der Tools“ angegeben) installiert sind.

Konfigurieren Sie Visual Studio für den PC, indem Sie die Releasekonfiguration, die x64-Architektur und einen lokalen Computer als Ziel auswählen:

![Visual Studio, konfiguriert für den lokalen Computer](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-2.png)

Klicken Sie auf die Schaltfläche ***Lokaler Computer***. Die Anwendung wird auf Ihrem PC erstellt und bereitgestellt. Die Anwendung wird standardmäßig auf Ihrem PC installiert.
