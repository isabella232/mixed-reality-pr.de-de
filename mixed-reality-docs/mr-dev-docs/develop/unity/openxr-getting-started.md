---
title: Verwenden des Mixed Reality OpenXR-Plug-Ins
description: Erfahren Sie, wie Sie das Mixed Reality OpenXR-Plug-In für Unity-Projekte aktivieren.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, Augmented Reality, Virtual Reality, Mixed Reality-Headsets, Lernen, Tutorial, Erste Schritte
ms.openlocfilehash: 65b79aadeb52db6be61edcc90a5d4a44c12384a1
ms.sourcegitcommit: 5617575cf550dd03fba0bfd5263e97972dcc646b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547038"
---
# <a name="using-the-mixed-reality-openxr-plugin"></a>Verwenden des Mixed Reality OpenXR-Plug-Ins

Für Entwickler, die Unity 2020 zum Erstellen von HoloLens 2- oder Mixed Reality-Anwendungen verwenden, kann das OpenXR-Plug-In anstelle des WindowsXR-Plug-Ins verwendet werden, um plattformübergreifende Kompatibilität zu verbessern.  Das Mixed Reality OpenXR-Plug-In funktioniert auch gut mit dem neuesten Mixed Reality [Toolkit 2.7.](/windows/mixed-reality/mrtk-unity)

## <a name="prerequisites"></a>Voraussetzungen

* Neueste Version von Unity 2020.3 LTS (wir empfehlen 2020.3.8f1 oder höher)
* Neuestes Unity OpenXR-Plug-In (wir empfehlen 1.2 oder höher)
* Neueste [Tools für HoloLens 2 Entwicklung](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)
* Neuestes MRTK (optional), (wir empfehlen Version 2.7 oder höher)
* Neueste Mixed Reality OpenXR-Plug-In, (wir empfehlen Version 1.0.0-preview.1 oder höher)

![Screenshot des offenen xr unity basic-Beispiels, das auf einer HoloLens ausgeführt wird](images/openxr-example.png)

> [!NOTE]
> Wenn Sie VR-Anwendungen auf einem Windows-PC erstellen, ist Mixed Reality OpenXR-Plug-In nicht unbedingt erforderlich. Sie sollten das Plug-In jedoch installieren, wenn Sie die Controllerzuordnung für HP Reverb G2-Controller anpassen oder Apps erstellen, die sowohl auf HoloLens 2- als auch auf VR-Headsets funktionieren.

## <a name="setting-up-your-project-with-mrtk"></a>Einrichten Ihres Projekts mit MRTK

MRTK für Unity bietet ein plattformübergreifendes Eingabesystem, Grundlagenkomponenten und gemeinsame Bausteine für räumliche Interaktionen. MRTK, Version 2, soll die Anwendungsentwicklung für Microsoft HoloLens, für immersive Windows Mixed Reality-Headsets (VR) und für die OpenVR-Plattform beschleunigen. Das Projekt ist darauf ausgerichtet, die Einstiegshürden zum Erstellen von Mixed Reality-Anwendungen zu verringern, und einen Beitrag für die Community auf diesem stetig wachsenden Gebiet zu leisten.

> [!div class="nextstepaction"]
> [Einrichten Ihres Projekts mit MRTK](./tutorials/mr-learning-base-02.md?tabs=openxr)

Weitere Details zu Features finden Sie in der [MRTK-Dokumentation](/windows/mixed-reality/mrtk-unity).

## <a name="manual-setup-without-mrtk"></a>Manuelle Einrichtung ohne MRTK

Installieren Sie das OpenXR-Plug-In mit der neuen Mixed Reality-Featuretoolanwendung. Befolgen Sie [die Installations- und Nutzungsanweisungen,](welcome-to-mr-feature-tool.md) und wählen Sie **Mixed Reality OpenXR-Plug-In-Paket** in der Kategorie Mixed Reality Toolkit aus:

![Mixed Reality fenster feature tool packages with open xr plugin (Öffnen des XR-Plug-Ins hervorgehoben)](images/feature-tool-openxr.png)

## <a name="setting-your-build-target"></a>Festlegen des Buildziels

Wenn Sie Desktop VR als Ziel verwenden möchten, empfehlen wir die Verwendung der eigenständigen PC-Plattform, die standardmäßig für ein neues Unity-Projekt ausgewählt ist:

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor mit hervorgehobener eigenständiger &-Plattform](images/wmr-config-img-3.png)

Wenn Sie auf HoloLens 2 möchten, müssen Sie zum folgenden Universelle Windows-Plattform:

1. Wählen **Sie Datei > Buildeinstellungen... aus.**
2. Wählen **Universelle Windows-Plattform** in der Liste Plattform aus, und wählen Sie **Plattform wechseln aus.**
3. Legen Sie **Architektur** auf **ARM 64** fest
4. Legen Sie **Zielgerät** auf **HoloLens** fest
5. Legen Sie **Buildtyp** auf **D3D** fest
6. Legen Sie **UWP SDK** auf **Zuletzt installiert** fest

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor mit hervorgehobener Universelle Windows-Plattform](images/wmr-config-img-4.png)

## <a name="configuring-xr-plugin-management-for-openxr"></a>Konfigurieren der XR-Plug-In-Verwaltung für OpenXR

So legen Sie OpenXR als Runtime in Unity fest:

1. Navigieren Sie im Unity-Editor zu **Bearbeiten > Projekteinstellungen.**
2. Wählen Sie in der Liste der Einstellungen **XR-Plug-In-Verwaltung aus.**
3. Aktivieren Sie die **Kontrollkästchen XR beim Start initialisieren** und **OpenXR.**
4. Wenn Sie HoloLens 2 auswählen, stellen Sie sicher, dass Sie auf der UWP-Plattform sind, und wählen **Sie Microsoft HoloLens Feature Set (Featuresatz) aus.**

![Screenshot des im Unity-Editor geöffneten Projekteinstellungspanels mit hervorgehobener XR-Plug-In-Verwaltung](images/openxr-img-05.png)

## <a name="optimization"></a>Optimization

Wenn Sie für HoloLens 2 entwickeln, navigieren Sie zu Mixed Reality> **OpenXR >** Empfohlene Projekteinstellungen für HoloLens 2 anwenden, um eine bessere App-Leistung zu erzielen.

![Screenshot des geöffneten Mixed Reality-Menüelements mit ausgewählter Option "OpenXR"](images/openxr-img-08.png)

> [!IMPORTANT]
> Wenn neben Dem OpenXR-Plug-In ein rotes **Warnsymbol** angezeigt wird, klicken Sie auf das Symbol, und wählen **Sie Alles korrigieren aus,** bevor Sie fortfahren. Der Unity-Editor muss möglicherweise neu gestartet werden, damit die Änderungen wirksam werden.

![Screenshot des OpenXR-Projektüberprüfungsfensters](images/openxr-img-06.png)

Sie können nun mit der Entwicklung mit OpenXR in Unity beginnen.  Fahren Sie mit dem nächsten Abschnitt fort, um zu erfahren, wie Sie die OpenXR-Beispiele verwenden.

## <a name="unity-sample-projects-for-openxr-and-hololens-2"></a>Unity-Beispielprojekte für OpenXR und HoloLens 2

Sehen Sie sich das [Repository mit OpenXR](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) Mixed Reality-Beispielen für Unity-Beispielprojekte an, in dem gezeigt wird, wie Sie Unity-Anwendungen für HoloLens 2- oder Mixed Reality-Headsets mithilfe des Mixed Reality OpenXR-Plug-Ins erstellen.

## <a name="using-mrtk-with-openxr-support"></a>Verwenden von MRTK mit OpenXR-Unterstützung

MRTK für Unity Version 2.7 unterstützt jetzt offiziell das Mixed Reality OpenXR-Plug-In.

Öffnen Sie [Mixed Reality Featuretool erneut,](welcome-to-mr-feature-tool.md) um das Mixed Reality Toolkit zu installieren, sofern noch nicht vorhanden. OpenXR-Unterstützung ist im **Foundation-Paket** enthalten.

![Featuretool "Mixed Reality" – Fenster "Features entdecken" mit hervorgehobenen Standardressourcen](images/mrft-install-openxr.png)

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

## <a name="see-also"></a>Siehe auch

* [Konfigurieren von Projekten ohne MRTK](configure-unity-project.md)
* [Empfohlene Einstellungen für Unity](recommended-settings-for-unity.md)
* [Leistungsempfehlungen für Unity](performance-recommendations-for-unity.md#how-to-profile-with-unity)
