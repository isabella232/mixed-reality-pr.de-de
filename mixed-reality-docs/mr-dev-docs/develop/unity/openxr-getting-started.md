---
title: Verwenden des Mixed Reality OpenXR-Plug-Ins für Unity
description: Erfahren Sie, wie Sie das Mixed Reality OpenXR-Plug-In für Unity-Projekte aktivieren.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, Augmented Reality, Virtual Reality, Mixed Reality-Headsets, Lernen, Tutorial, Erste Schritte
ms.openlocfilehash: 4c220deeca13c6807857375b71640207823b94ed
ms.sourcegitcommit: 95fbb851336b6c5977a2ce4d4ac10f0eeb0df31f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2021
ms.locfileid: "107944661"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a>Verwenden des Mixed Reality OpenXR-Plug-Ins für Unity

Ab Unity Version 2020.2 ist das Microsoft Mixed Reality OpenXR-Plug-In-Paket mit dem Mixed Reality [Feature Tool verfügbar.](welcome-to-mr-feature-tool.md)

## <a name="prerequisites"></a>Voraussetzungen

* Unity 2020.3 LTS oder höher
* Unity OpenXR-Plug-In 1.1.1 oder höher
* Visual Studio 2019 oder höher
* Installieren **der UWP-Plattformunterstützung** in Unity für HoloLens 2 Apps

> [!NOTE]
> Wenn Sie VR-Anwendungen auf einem Windows-PC erstellen, ist Mixed Reality OpenXR-Plug-In nicht unbedingt erforderlich. Sie sollten das Plug-In jedoch installieren, wenn Sie die Controllerzuordnung für HP Reverb G2-Controller anpassen oder Apps erstellen, die sowohl auf HoloLens 2- als auch auf VR-Headsets funktionieren.

## <a name="setting-up-your-project-with-mrtk"></a>Einrichten Ihres Projekts mit MRTK

MRTK für Unity bietet ein plattformübergreifendes Eingabesystem, Grundlagenkomponenten und gemeinsame Bausteine für räumliche Interaktionen. MRTK, Version 2, soll die Anwendungsentwicklung für Microsoft HoloLens, für immersive Windows Mixed Reality-Headsets (VR) und für die OpenVR-Plattform beschleunigen. Das Projekt ist darauf ausgerichtet, die Einstiegshürden zum Erstellen von Mixed Reality-Anwendungen zu verringern, und einen Beitrag für die Community auf diesem stetig wachsenden Gebiet zu leisten.

> [!div class="nextstepaction"]
> [Einrichten Ihres Projekts mit MRTK](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=openxr)

Weitere Details zu Features finden Sie in der [MRTK-Dokumentation](/windows/mixed-reality/mrtk-unity).

## <a name="manual-setup-without-mrtk"></a>Manuelle Einrichtung ohne MRTK

Installieren Sie das OpenXR-Plug-In mit der neuen Mixed Reality Feature Tool-Anwendung. Befolgen Sie [die Installations- und Verwendungsanweisungen,](welcome-to-mr-feature-tool.md) und wählen Sie **Mixed Reality OpenXR-Plug-In-Paket** in der Kategorie Mixed Reality Toolkit aus:

![Mixed Reality fenster feature tool packages with open xr plugin (Öffnen des XR-Plug-Ins hervorgehoben)](images/feature-tool-openxr.png)

## <a name="setting-your-build-target"></a>Festlegen des Buildziels

Wenn Sie Desktop VR als Ziel verwenden möchten, empfehlen wir die Verwendung der eigenständigen PC-Plattform, die standardmäßig für ein neues Unity-Projekt ausgewählt ist:

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor mit hervorgehobener eigenständiger &-Plattform](images/wmr-config-img-3.png)

Wenn Sie HoloLens 2 als Ziel haben, müssen Sie zum Universelle Windows-Plattform wechseln:

1.  Wählen Sie **Datei > Buildeinstellungen... aus.**
2.  Wählen Sie **Universelle Windows-Plattform** in der Liste Plattform und dann **Plattform wechseln** aus.
3.  Legen Sie **Architektur** auf **ARM 64** fest
4.  Legen Sie **Zielgerät** auf **HoloLens** fest
5.  Legen Sie **Buildtyp** auf **D3D** fest
6.  Legen Sie **UWP SDK** auf **Zuletzt installiert** fest
7.  Legen Sie **Buildkonfiguration** auf **Release** fest, da beim Debuggen bekannte Leistungsprobleme auftreten.

![Screenshot: Fenster "Buildeinstellungen" im Unity-Editor mit hervorgehobener Universelle Windows-Plattform](images/wmr-config-img-4.png)

Nachdem Sie Ihre Plattform festgelegt haben, müssen Sie Unity mitteilen, dass beim Exportieren eine [immersive Ansicht](../../design/app-views.md) anstelle einer 2D-Ansicht erstellt werden soll.

## <a name="configuring-xr-plugin-management-for-openxr"></a>Konfigurieren der XR-Plug-In-Verwaltung für OpenXR

So legen Sie OpenXR als Runtime in Unity fest:

1. Navigieren Sie im Unity-Editor zu **> Projekteinstellungen bearbeiten.**
2. Wählen Sie in der Liste der Einstellungen die Option **XR-Plug-In-Verwaltung** aus.
3. Aktivieren Sie die Felder **XR beim Start initialisieren** und **OpenXR.**
4. Wenn Sie HoloLens 2 als Ziel verwenden, stellen Sie sicher, dass Sie sich auf der UWP-Plattform befindet, und wählen Sie **Microsoft HoloLens Featuresatz aus.**

![Screenshot des im Unity-Editor geöffneten Bereichs "Projekteinstellungen" mit hervorgehobener XR-Plug-In-Verwaltung](images/openxr-img-05.png)

## <a name="optimization"></a>Optimization

Wenn Sie für HoloLens 2 entwickeln, navigieren Sie zu **Mixed Reality> OpenXR > Empfohlene Projekteinstellungen für HoloLens 2** anwenden, um eine bessere App-Leistung zu erzielen.

![Screenshot: Geöffnetes Mixed Reality-Menüelement mit ausgewählter Option "OpenXR"](images/openxr-img-08.png)

> [!IMPORTANT]
> Wenn neben **OpenXR-Plug-In** ein rotes Warnsymbol angezeigt wird, klicken Sie auf das Symbol, und wählen **Sie Alle korrigieren** aus, bevor Sie fortfahren. Der Unity-Editor muss möglicherweise neu gestartet werden, damit die Änderungen wirksam werden.

![Screenshot des Fensters "OpenXR-Projektvalidierung"](images/openxr-img-06.png)

Sie können nun mit der Entwicklung mit OpenXR in Unity beginnen!  Fahren Sie mit dem nächsten Abschnitt fort, um zu erfahren, wie Sie die OpenXR-Beispiele verwenden.

## <a name="try-out-the-unity-sample-scenes"></a>Probieren Sie die Unity-Beispielszenen aus.

### <a name="hololens-2-samples"></a>HoloLens 2 Beispiele

1. Navigieren Sie im Unity-Editor zu **Fenster > Paket-Manager**
2. Wählen Sie in der Liste der Pakete Mixed Reality **OpenXR-Plug-In aus.**
3. Suchen Sie das Beispiel in der Liste **Beispiele,** und wählen Sie **Importieren aus.**

![Screenshot: Unity-Paket-Manager im Unity-Editor geöffnet, Mixed Reality OpenXR-Plug-In ausgewählt und schaltfläche "Beispiele importieren" hervorgehoben](images/openxr-img-03.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> Wenn ein Paket aktualisiert wird, bietet Unity die Option zum Aktualisieren importierter Beispiele.  Durch das Aktualisieren eines importierten Beispiels werden alle Änderungen überschrieben, die am Beispiel und den zugehörigen Ressourcen vorgenommen wurden.

## <a name="using-mrtk-with-openxr-support"></a>Verwenden von MRTK mit OpenXR-Unterstützung

MRTK-Unity unterstützt das Mixed Reality OpenXR-Plug-In ab Version 2.5.3.

1. Öffnen Sie [Mixed Reality Featuretool erneut,](welcome-to-mr-feature-tool.md) um das Mixed Reality Toolkit zu installieren, sofern noch nicht vorhanden. OpenXR-Unterstützung ist im **Foundation-Paket** enthalten.
2. Wechseln Sie im Inspector zum MixedReality Toolkit-Komponentenskript, und wechseln Sie zum **Profil DefaultOpenXRConfigurationProfile:**

    ![Screenshot: Wechseln der MRTK-Konfiguration in der Mixed Reality Toolkit-Komponente im Inspektor](images/openxr-img-11.png)

    1. Weitere ausführliche Informationen zur Migration zu OpenXR finden Sie in der [MRTK-Dokumentation.](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)

> [!NOTE]
> Stellen Sie beim Upgrade von einer früheren Version von MRTK sicher, dass sich die folgende Zeile in der Datei **Assets/MixedRealityToolkit.Generated/link.xml** befindet:
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> Diese Zeile wird standardmäßig hinzugefügt, wenn Sie mit MRTK 2.5.4 oder neuer begonnen haben.

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie Ihr Projekt für OpenXR konfiguriert haben und Zugriff [](openxr-supported-features.md) auf Beispiele haben, sehen Sie sich an, welche Features derzeit in unserem OpenXR-Plug-In unterstützt werden.

## <a name="have-feedback"></a>Haben Sie Feedback?

OpenXR ist immer noch experimentell, daher freuen wir uns über jedes Feedback, das Sie uns geben können, um es besser zu machen. Sie finden uns in den [Unity-Foren,](https://aka.ms/unityforums) indem Sie Ihren Forumbeitrag mit **Microsoft**  +  **OpenXR** markieren und **entweder** HoloLens 2 oder **Windows Mixed Reality.**

## <a name="see-also"></a>Weitere Informationen:

* [Konfigurieren von Projekten ohne MRTK](configure-unity-project.md)
* [Empfohlene Einstellungen für Unity](recommended-settings-for-unity.md)
* [Leistungsempfehlungen für Unity](performance-recommendations-for-unity.md#how-to-profile-with-unity)
