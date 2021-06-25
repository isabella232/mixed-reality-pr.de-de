---
title: Verwenden des Windows XR-Plug-Ins
description: Erfahren Sie, wie Sie Ihre Unity-Projekte mit und ohne MRTK mithilfe der Windows XR-Unterstützung einrichten.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, Mixed Reality, Entwicklung, erste Schritte, neues Projekt, Windows Mixed Reality, UWP, XR, Leistung, Legacy, Mrtk, Fenster
ms.openlocfilehash: 5d2d27a7ac5ea30515907a08eab6f6bfe70e6686
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906956"
---
# <a name="using-windows-xr-plugin"></a>Verwenden des Windows XR-Plug-Ins

Für Entwickler, die Unity 2020 als Ziel verwenden, ermöglicht das Windows XR-Plug-In den Zugriff auf Mixed Reality-Features auf HoloLens 2 und Windows Mixed Reality Headsets.  Dieses Plug-In wird auch in Unity 2019 unterstützt, obwohl es einige bekannte Inkompatibilitäten mit Azure Spatial Anchors gibt, wenn dieses Plug-In für diese Version verwendet wird.

Microsoft und die Community haben OpenSource-Tools wie das [Mixed Reality Toolkit (MRTK)](/windows/mixed-reality/mrtk-unity/configuration/usingupm) erstellt, mit denen die WMR-Umgebung automatisch eingerichtet wird, aber viele Entwickler möchten ihre Erfahrungen von Grund auf neu erstellen.  In der folgenden Dokumentation wird veranschaulicht, wie Sie ein Projekt ordnungsgemäß für die entwicklung Mixed Reality, unabhängig davon, ob Sie MRTK verwenden oder nicht.  Die Einstellungen, die Sie ändern müssen, sind in zwei Kategorien unterteilt: Projektspezifische Einstellungen und Szenenspezifische Einstellungen.

## <a name="setting-up-your-project-with-mrtk"></a>Einrichten Ihres Projekts mit MRTK

MRTK für Unity bietet ein plattformübergreifendes Eingabesystem, Grundlagenkomponenten und gemeinsame Bausteine für räumliche Interaktionen. MRTK, Version 2, soll die Anwendungsentwicklung für Microsoft HoloLens, für immersive Windows Mixed Reality-Headsets (VR) und für die OpenVR-Plattform beschleunigen. Das Projekt ist darauf ausgerichtet, die Einstiegshürden zum Erstellen von Mixed Reality-Anwendungen zu verringern, und einen Beitrag für die Community auf diesem stetig wachsenden Gebiet zu leisten.

> [!div class="nextstepaction"]
> [Probieren Sie unsere MRTK-Tutorials aus](./tutorials/mr-learning-base-02.md?tabs=winxr)

Weitere Details zu Features finden Sie in der [MRTK-Dokumentation](/windows/mixed-reality/mrtk-unity).

## <a name="manual-setup-without-mrtk"></a>Manuelle Einrichtung ohne MRTK

Wenn Sie Desktop VR als Ziel verwenden möchten, empfehlen wir die Verwendung der eigenständigen PC-Plattform, die standardmäßig für ein neues Unity-Projekt ausgewählt ist:

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor mit hervorgehobener eigenständiger &-Plattform](images/wmr-config-img-3.png)

Wenn Sie auf HoloLens 2 möchten, müssen Sie zum folgenden Universelle Windows-Plattform:

1.  Wählen **Sie Datei > Buildeinstellungen... aus.**
2.  Wählen **Universelle Windows-Plattform** in der Liste Plattform aus, und wählen Sie **Plattform wechseln aus.**
3.  Legen Sie **Architektur** auf **ARM 64** fest
4.  Legen Sie **Zielgerät** auf **HoloLens** fest
5.  Legen Sie **Buildtyp** auf **D3D** fest
6.  Legen Sie **UWP SDK** auf **Zuletzt installiert** fest
7.  Legen Sie **Buildkonfiguration** auf **Release** fest, da beim Debuggen bekannte Leistungsprobleme auftreten.

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor mit hervorgehobener Universelle Windows-Plattform](images/wmr-config-img-4.png)

Nachdem Sie Ihre Plattform festlegen, müssen Sie [](../../design/app-views.md) Unity darüber informieren, dass beim Exportieren eine immersive Ansicht anstelle einer 2D-Ansicht erstellt werden soll:

1. Navigieren Sie im Unity-Editor zu Bearbeiten > **Projekteinstellungen,** und wählen Sie **XR-Plug-In-Verwaltung aus.**

2. Wählen Sie **XR-Plug-In-Verwaltung installieren aus.**

![Screenshot des Fensters "Projekteinstellungen" im Unity-Editor mit hervorgehobener XR-Plug-In-Verwaltung](images/wmr-config-img-5.png)

3. Wählen **Sie XR beim Start initialisieren und Windows Mixed Reality** 

![Screenshot des Fensters "Projekteinstellungen" im Unity-Editor mit hervorgehobener XR-Plug-In-Verwaltung](images/wmr-config-img-7.png)

4. Erweitern Sie den **Abschnitt XR-Plug-In-Verwaltung,** und wählen Sie die Registerkarte **"Einstellungen für die Windows-Plattform"** aus.
5. Wenn Sie Unity 2020 oder höher verwenden, sehen Sie die Optionen zum Überprüfen von **OpenXR** **oder Windows Mixed Reality**. 
    * Sie können eine der beiden Laufzeiten auswählen.  Wenn Sie speziell für die HoloLens 2 oder HP Reverb G2 entwickeln und sich entschließen, **OpenXR** auszuprobieren, wählen Sie das Feld OpenXR aus, und sehen Sie sich unseren Leitfaden unter Verwenden des Mixed Reality OpenXR-Plug-Ins für [Unity](./xr-project-setup.md) an, um sich für diese Geräte ordnungsgemäß einrichten zu lassen, bevor Sie zu diesem Tutorial zurückkehren.

> [!NOTE]
> Ab Unity 2020 LTS geht Microsoft von der Entwicklung mit OpenXR aus.  Bei der Migration zu diesem Pfad wird in Unity 2021.1 das Windows XR-Plug-In veraltet sein und in 2021.2 entfernt, wodurch OpenXR der einzige unterstützte Pfad ist. Weitere Informationen finden Sie unter [Verwenden des Mixed Reality OpenXR-Plug-Ins.](./xr-project-setup.md)

6. Wenn Sie sich für das **Windows Mixed Reality-Plug-In** entscheiden, aktivieren Sie alle Kontrollkästchen, und legen Sie **tiefenübermittlungsmodus** auf Tiefe **16 Bit fest.**

![Screenshot: Fenster "Projekteinstellungen" im Unity-Editor geöffnet, Windows Mixed Reality abschnitt hervorgehoben](images/wmr-config-img-8.png)