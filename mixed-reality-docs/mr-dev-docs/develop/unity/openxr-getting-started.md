---
title: Verwenden des gemischten Reality openxr-Plug-Ins für Unity
description: Erfahren Sie, wie Sie das gemischte Open-Plug-in für Unity für Unity-Projekte aktivieren.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, Mixed Reality, mrtk, Mixed Reality Toolkit, Augmented Reality, Virtual Reality, Mixed Reality-Headsets, erlernen, Tutorial, Getting Started
ms.openlocfilehash: c5d312161b7d0f4f832e8d09dbacf5af700ffd8d
ms.sourcegitcommit: aa29b68603721e909f08f352feed24c65d2e505e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/12/2021
ms.locfileid: "98108881"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a>Verwenden des gemischten Reality openxr-Plug-Ins für Unity

Ab Unity, Version 2020,2, ist das gemischte openxr-Plug-in-Paket von Microsoft mit dem Unity-Paket-Manager (UPM) verfügbar.

## <a name="prerequisites"></a>Voraussetzungen

* Unity 2020,2 oder höher
* Unity openxr-Plug-in 0.1.2 oder höher
* Visual Studio 2019 oder höher
* Installieren der **UWP** -Platt Form Unterstützung in Unity für hololens 2-apps

> [!NOTE]
> Wenn Sie VR-Anwendungen auf einem Windows-PC entwickeln, ist das gemischte openxr-Plug-in für die gemischte Realität nicht unbedingt erforderlich. Sie sollten das Plug-in jedoch installieren, wenn Sie die Controller Zuordnung für HP-Reverb-G2-Controller anpassen oder apps entwickeln, die sowohl für hololens 2-als auch für VR-Headsets geeignet sind.

## <a name="installing-the-mixed-reality-openxr-plugin"></a>Installieren des Mixed Reality openxr-Plug-ins

Das Projekt muss das **openxr** -Plug-in und das **Management** Pack für den Wenn Sie diese bereits installiert haben, ist es toll! Wenn dies nicht der Fall ist, werden Sie beim Installieren des Plug-Ins für gemischte Realität automatisch als Abhängigkeiten installiert:

1. Navigieren Sie im Unity-Editor zum **Bearbeiten > Projekteinstellungen > Paket-Manager** .
2. Erweitern Sie den Bereich Bereichs bezogene **Registrierungen** , geben Sie die folgenden Informationen ein, und klicken Sie dann auf **Speichern**:
    * Legen Sie **Name** auf **Microsoft Mixed Reality** fest.
    * **URL** festlegen auf **https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/**
    * **Bereich (e)** auf **com. Microsoft. mixedreality** festlegen

3. Wählen Sie unter **Erweiterte Einstellungen** die Option **Vorschau Pakete aktivieren** aus.

![Screenshot des Fensters "Unity-Paket-Manager" in den Projekteinstellungen](images/openxr-img-01.png)

Der Unity-Paket-Manager verwendet eine Manifestressource mit dem Namen *manifest.json* , um zu bestimmen, welche Pakete installiert werden müssen und welche Registrierungen Sie installieren können.

> [!IMPORTANT]
> Openxr ist in Unity immer noch experimentell, und dieser Prozess kann sich im Laufe der Zeit ändern, da wir arbeiten, um die Entwickler Oberfläche zu optimieren.

### <a name="registering-the-mixed-reality-dependency"></a>Registrieren der Mixed Reality-Abhängigkeit

Nachdem die Microsoft Mixed Reality-Bereichs bezogene Registrierung dem Manifest hinzugefügt wurde, kann das openxr-Paket angegeben werden.

So fügen Sie das openxr-Paket hinzu:

1. Öffnen Sie **[projectroot]/Packages/manifest.js** in einem Text-Editor wie Visual Studio Code
    1. Klicken Sie dazu im linken Bereich des Projekt Fensters mit der rechten Maustaste auf **Pakete** . Klicken Sie dann **auf in Explorer anzeigen**.
    ![Screenshot der Paket Auflistung im Projektfenster](images/packages.png)
1. Ändern Sie den Abschnitt "Abhängigkeiten" der *Pakete/manifest.jsin* der Datei wie folgt:

    > [!IMPORTANT]
    > In ihrer Manifest-Datei sind möglicherweise weitere Abhängigkeiten vorhanden, die hier nicht aufgeführt sind. Löschen Sie keines dieser Elemente, und fügen Sie der Liste einfach die openxr-Abhängigkeit hinzu.

    ``` json
      "dependencies": {
        "com.microsoft.mixedreality.openxr": "0.1.2",
      }
    ```

1. Speichern Sie die Datei, wechseln Sie zurück zum Unity-Editor, und öffnen Sie den **Paket-Manager** , um die Installation des Plug-ins zu bestätigen:

    ![Screenshot des Unity-Paket-Managers, geöffnet im Unity-Editor mit hervorgehobenem gemischtes openxr-Plug-in](images/openxr-img-03.png)

    > [!Note]
    > Wenn das openxr-Paket mit dem Unity-Paket-Manager entfernt wird, müssen Sie es mithilfe der zuvor beschriebenen Schritte erneut hinzufügen.

## <a name="configuring-xr-plugin-management-for-openxr"></a>Konfigurieren der XR-Plug-in-Verwaltung für openxr

So legen Sie openxr als Lauf Zeit Modul in Unity fest:

1. Navigieren Sie im Unity-Editor zu **Bearbeiten > Projekteinstellungen** .
2. Wählen Sie in der Liste der Einstellungen die Option " **XR Plugin Management** "
3. Aktivieren Sie die Kontrollkästchen " **XR beim Start** " und " **openxr (Vorschau)** initialisieren"
4. Wenn Sie auf hololens 2 abzielen, stellen Sie sicher, dass Sie sich auf der UWP-Plattform befinden, und wählen Sie " **Microsoft hololens Feature**

![Screenshot des Bereichs "Projekteinstellungen" im Unity-Editor mit hervorgehobener XR-Plug-in-Verwaltung](images/openxr-img-05.png)

> [!IMPORTANT]
> Wenn ein rotes Warnsymbol neben **openxr-Plug-in (Vorschau)** angezeigt wird, klicken Sie auf das Symbol, und wählen Sie **alle korrigieren** , bevor Sie fortfahren. Der Unity-Editor muss möglicherweise neu gestartet werden, damit die Änderungen wirksam werden.

![Screenshot des Fensters "openxr Project Validation"](images/openxr-img-06.png)

Sie sind nun bereit, mit der Entwicklung mit openxr in Unity zu beginnen!  Fahren Sie mit dem nächsten Abschnitt fort, um zu erfahren, wie Sie die openxr-Beispiele verwenden.

## <a name="optimization"></a>Optimization

Wenn Sie für hololens 2 entwickeln, navigieren Sie zu **gemischte Realität> openxr > die empfohlenen Projekteinstellungen für hololens 2 anwenden** , um eine bessere App-Leistung zu erzielen.

![Screenshot des Menü Elements mit gemischter Realität geöffnet mit ausgewähltem openxr](images/openxr-img-08.png)

## <a name="try-out-the-unity-sample-scenes"></a>Ausprobieren der Unity-Beispiel Szenen

Wenn Sie eines oder mehrere der Beispiele verwenden möchten, installieren Sie [arfoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) und höher über den **Paket-Manager**:

![Screenshot: Öffnen des Unity-Paket-Managers im Unity-Editor mit hervorgehobener AR Foundation](images/openxr-img-09.png)

### <a name="hololens-2-samples"></a>Hololens 2-Beispiele

1. Navigieren Sie im Unity-Editor zu **Fenster > Paket-Manager** .
2. Wählen Sie in der Liste der Pakete **gemischte Realität openxr-Plug** -in aus.
3. Suchen Sie das Beispiel in der Liste **Samples** , und wählen Sie **importieren** aus.

![Screenshot: Öffnen des Unity-Paket-Managers im Unity-Editor mit aktiviertem aktiviertem openxr-Plug-in](images/openxr-img-03.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> Wenn ein Paket aktualisiert wird, bietet Unity die Option zum Aktualisieren importierter Beispiele.  Durch das Aktualisieren eines importierten Beispiels werden alle Änderungen überschrieben, die an dem Beispiel und den zugehörigen Assets vorgenommen wurden.

## <a name="using-mrtk-with-openxr-support"></a>Verwenden von mrtk mit openxr-Unterstützung

Mrtk Unity unterstützt das Mixed Reality openxr-Plug-in, beginnend mit der 2.5.3-Version.  Mrtk-Plug-Ins können aus den gleichen Bereichs bezogenen Registrierungen installiert werden, die Sie bei [der Installation des Mixed Reality openxr-Plug](#installing-the-mixed-reality-openxr-plugin)-ins eingerichtet haben. Ausführlichere Informationen finden Sie in der [Dokumentation zu mrtk](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/usingupm.html#registering-the-mixed-reality-component-server).

1. Fügen Sie die folgenden Pakete in Ihrem **[projectroot]/Packages/-manifest.jsfür** die Datei hinzu:

```json
"dependencies": {
    "com.microsoft.mixedreality.toolkit.foundation": "2.5.3",
    "com.microsoft.mixedreality.toolkit.tools": "2.5.3",
    "com.microsoft.mixedreality.toolkit.examples": "2.5.3",
    …
}
```

2. Wechseln Sie zum Skript "mixedreality Toolkit-Komponente" im Inspektor, und wechseln Sie zum Profil " **defaultoperxrconfigurationprofile** ":

![Screenshot: Wechseln der mrtk-Konfiguration in der Mixed Reality Toolkit-Komponente im Inspektor](images/openxr-img-11.png)

### <a name="known-issues"></a>Bekannte Probleme 

Fügen Sie in der Datei **Assets/mixedrealitytoolkit. generated/link.xml** die folgende Zeile hinzu, wenn Sie das Hand Verfolgungs Feature verwenden:

```
<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
```

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie Ihr Projekt für openxr konfiguriert haben und Zugriff auf Beispiele haben, sehen Sie sich an, welche [Features](openxr-supported-features.md) derzeit in unserem openxr-Plug-in unterstützt werden.

## <a name="have-feedback"></a>Haben Sie Feedback?

Openxr ist noch immer experimentell. Wir freuen uns über jedes Feedback, das Sie uns zur Verbesserung der IT-Unterstützung bieten können. Sie finden uns in den [Unity-Foren](https://aka.ms/unityforums) , indem Sie Ihren Forumsbeitrag mit **Microsoft**  +  **openxr** und entweder **hololens 2** oder **Windows Mixed Reality** markieren.

## <a name="see-also"></a>Weitere Informationen

* [Konfigurieren von Projekten ohne MRTK](configure-unity-project.md)
* [Empfohlene Einstellungen für Unity](recommended-settings-for-unity.md)
* [Leistungsempfehlungen für Unity](performance-recommendations-for-unity.md#how-to-profile-with-unity)
