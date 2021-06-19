---
title: Verwenden des Mixed Reality OpenXR-Plug-Ins
description: Erfahren Sie, wie Sie das Mixed Reality OpenXR-Plug-In für Unity-Projekte aktivieren.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, Augmented Reality, Virtual Reality, Mixed Reality Headsets, Learn, Tutorial, Erste Schritte
ms.openlocfilehash: ffec0cbe2ea9fd87cbb5f38010dad2d64e2e82ee
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392678"
---
# <a name="using-the-mixed-reality-openxr-plugin"></a>Verwenden des Mixed Reality OpenXR-Plug-Ins

Für Entwickler, die Unity 2020 als Ziel haben, um HoloLens 2 oder Mixed Reality Anwendungen zu erstellen, kann das OpenXR-Plug-In anstelle des WindowsXR-Plug-Ins verwendet werden, um plattformübergreifende Kompatibilität zu verbessern.  Das Mixed Reality OpenXR-Plug-In funktioniert auch gut mit dem neuesten [Mixed Reality FeatureTool.](welcome-to-mr-feature-tool.md)

## <a name="prerequisites"></a>Voraussetzungen

* Die neueste Version von Unity 2020.3 LTS empfiehlt 2020.3.6f1 oder höher.
* Neuestes Unity OpenXR-Plug-In, empfohlen 1.2 oder höher
* Neueste [Tools für HoloLens 2 Entwicklung](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)
* Neuestes MRTK (optional), empfohlene Version 2.6 oder höher
* Neueste Mixed Reality OpenXR-Plug-In, empfohlene Version 0.9.5 oder höher

> [!NOTE]
> Wenn Sie VR-Anwendungen auf einem Windows-PC erstellen, ist das Mixed Reality OpenXR-Plug-In nicht unbedingt erforderlich. Sie sollten das Plug-In jedoch installieren, wenn Sie die Controllerzuordnung für HP Reverb G2-Controller anpassen oder Apps erstellen, die sowohl auf HoloLens 2- als auch auf VR-Headsets funktionieren.

## <a name="setting-up-your-project-with-mrtk"></a>Einrichten Ihres Projekts mit MRTK

MRTK für Unity bietet ein plattformübergreifendes Eingabesystem, Grundlagenkomponenten und gemeinsame Bausteine für räumliche Interaktionen. MRTK, Version 2, soll die Anwendungsentwicklung für Microsoft HoloLens, für immersive Windows Mixed Reality-Headsets (VR) und für die OpenVR-Plattform beschleunigen. Das Projekt ist darauf ausgerichtet, die Einstiegshürden zum Erstellen von Mixed Reality-Anwendungen zu verringern, und einen Beitrag für die Community auf diesem stetig wachsenden Gebiet zu leisten.

> [!div class="nextstepaction"]
> [Einrichten Ihres Projekts mit mrtk](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=openxr)

Weitere Details zu Features finden Sie in der [MRTK-Dokumentation](/windows/mixed-reality/mrtk-unity).

## <a name="manual-setup-without-mrtk"></a>Manuelle Einrichtung ohne MRTK

Installieren Sie das OpenXR-Plug-In mit der neuen Anwendung Mixed Reality Feature Tool. Befolgen Sie die [Installations- und Nutzungsanweisungen,](welcome-to-mr-feature-tool.md) und wählen Sie das **Mixed Reality OpenXR-Plug-In-Paket** in der Kategorie Mixed Reality Toolkit aus:

![Mixed Reality Fenster "Featuretoolpakete" mit hervorgehobener "xr-Plug-In öffnen"](images/feature-tool-openxr.png)

## <a name="setting-your-build-target"></a>Festlegen des Buildziels

Wenn Sie desktop VR als Ziel verwenden möchten, empfehlen wir, die pc Standalone Platform zu verwenden, die standardmäßig für ein neues Unity-Projekt ausgewählt ist:

![Screenshot des Fensters "Buildeinstellungen", das im Unity-Editor geöffnet ist, wobei PC, Mac & eigenständige Plattform hervorgehoben ist](images/wmr-config-img-3.png)

Wenn Sie HoloLens 2 als Ziel haben, müssen Sie zum Universelle Windows-Plattform wechseln:

1. Wählen Sie **Datei > Buildeinstellungen... aus.**
2. Wählen Sie **Universelle Windows-Plattform** in der Liste Plattform und dann **Plattform wechseln** aus.
3. Legen Sie **Architektur** auf **ARM 64** fest
4. Legen Sie **Zielgerät** auf **HoloLens** fest
5. Legen Sie **Buildtyp** auf **D3D** fest
6. Legen Sie **UWP SDK** auf **Zuletzt installiert** fest

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor mit hervorgehobener Universelle Windows-Plattform](images/wmr-config-img-4.png)

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

## <a name="unity-sample-projects-for-openxr-and-hololens-2"></a>Unity-Beispielprojekte für OpenXR und HoloLens 2

Sehen Sie sich das Repository mit [OpenXR-Mixed Reality-Beispielen](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) für Unity-Beispielprojekte an, die zeigen, wie Unity-Anwendungen für HoloLens 2 oder Mixed Reality Headsets mithilfe des Mixed Reality OpenXR-Plug-Ins erstellt werden.

## <a name="using-mrtk-with-openxr-support"></a>Verwenden von MRTK mit OpenXR-Unterstützung

MRTK-Unity unterstützt das Mixed Reality OpenXR-Plug-In ab Version 2.5.3.

1. Öffnen Sie das [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) erneut, um das Mixed Reality Toolkit zu installieren, sofern noch nicht erfolgt. OpenXR-Unterstützung ist im **Foundation-Paket** enthalten.
2. Wechseln Sie im Inspector zum MixedReality Toolkit-Komponentenskript, und wechseln Sie zum Profil **DefaultOpenXRConfigurationProfile:**

    ![Screenshot: Wechseln der MRTK-Konfiguration in der Mixed Reality Toolkit-Komponente im Inspektor](images/openxr-img-11.png)

    1. [Ausführlichere Informationen zur Migration zu OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)finden Sie in der MRTK-Dokumentation.

> [!NOTE]
> Stellen Sie beim Upgrade von einer früheren Version von MRTK sicher, dass sich die folgende Zeile in der Datei **Assets/MixedRealityToolkit.Generated/link.xml** befindet:
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> Diese Zeile wird standardmäßig hinzugefügt, wenn Sie mit MRTK 2.5.4 oder neuer gestartet haben.

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie Ihr Projekt für OpenXR konfiguriert haben und Zugriff auf Beispiele haben, sehen Sie sich an, welche [Features](openxr-supported-features.md) derzeit in unserem OpenXR-Plug-In unterstützt werden.

## <a name="have-feedback"></a>Haben Sie Feedback?

OpenXR ist noch experimentell, daher würden wir uns über feedback freuen, das Sie uns geben können, um es zu verbessern. Sie finden uns in den [Unity-Foren,](https://aka.ms/unityforums) indem Sie Ihren Forumbeitrag mit **Microsoft**  +  **OpenXR** markieren und entweder **HoloLens 2** oder **Windows Mixed Reality.**

## <a name="see-also"></a>Siehe auch

* [Konfigurieren von Projekten ohne MRTK](configure-unity-project.md)
* [Empfohlene Einstellungen für Unity](recommended-settings-for-unity.md)
* [Leistungsempfehlungen für Unity](performance-recommendations-for-unity.md#how-to-profile-with-unity)