---
title: Verwenden des gemischten Reality openxr-Plug-Ins für Unity
description: Erfahren Sie, wie Sie das gemischte Open-Plug-in für Unity für Unity-Projekte aktivieren.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, Mixed Reality, mrtk, Mixed Reality Toolkit, Augmented Reality, Virtual Reality, Mixed Reality-Headsets, erlernen, Tutorial, Getting Started
ms.openlocfilehash: 1adfb979cfc22be5da18ed990c9db55e6bad97f3
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2021
ms.locfileid: "99238124"
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

## <a name="installing-openxr-with-the-mixed-reality-feature-tool"></a>Installieren von openxr mit dem Feature-Tool Mixed Reality

Installieren Sie das openxr-Plug-in mit der neuen Anwendung Mixed Reality Feature Tool. Befolgen Sie die [Installations-und Verwendungs Anweisungen](welcome-to-mr-feature-tool.md) , und wählen Sie das **gemischte openxr-Plug** -in in der Kategorie Mixed Reality-Toolkit aus:

![Fenster "Mixed Reality Feature Tool Packages" mit hervorgehobenem Open XR](images/feature-tool-openxr.png)

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

Mrtk Unity unterstützt das Mixed Reality openxr-Plug-in, beginnend mit der 2.5.3-Version.  

1. Öffnen Sie das [Mixed Reality Feature-Tool](welcome-to-mr-feature-tool.md) erneut, und wählen Sie das **gemischte openxr-Plug** -in in der Kategorie Platt Form Unterstützung aus.

<!-- MRTK plugins can be installed from the same scoped registries as you set up when [installing the Mixed Reality OpenXR plugin](#installing-the-mixed-reality-openxr-plugin). You can find more detailed information in the [MRTK documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/usingupm.html#registering-the-mixed-reality-component-server).

1. Add following packages in your **[projectRoot]/Packages/manifest.json** file:

```json
"dependencies": {
    "com.microsoft.mixedreality.toolkit.foundation": "2.5.3",
    "com.microsoft.mixedreality.toolkit.tools": "2.5.3",
    "com.microsoft.mixedreality.toolkit.examples": "2.5.3",
    …
}
``` -->

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

## <a name="see-also"></a>Siehe auch

* [Konfigurieren von Projekten ohne MRTK](configure-unity-project.md)
* [Empfohlene Einstellungen für Unity](recommended-settings-for-unity.md)
* [Leistungsempfehlungen für Unity](performance-recommendations-for-unity.md#how-to-profile-with-unity)
