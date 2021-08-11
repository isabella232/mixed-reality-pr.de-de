---
title: Verwenden der integrierten Legacy-XR-Unterstützung
description: Erfahren Sie, wie Sie Ihre Unity-Projekte mit und ohne MRTK mithilfe der integrierten Legacy-XR-Unterstützung einrichten.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, Mixed Reality, Entwicklung, erste Schritte, neues Projekt, Windows Mixed Reality, UWP, XR, Leistung, Legacy, mrtk
ms.openlocfilehash: 534df0b9c4efbe62b00af6cccb74f4203c1557e9479b2101320bab3bbdb5e565
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192056"
---
# <a name="using-legacy-built-in-xr-support"></a>Verwenden der integrierten Legacy-XR-Unterstützung

## <a name="setting-up-your-project-with-mrtk"></a>Einrichten Ihres Projekts mit MRTK

MRTK für Unity bietet ein plattformübergreifendes Eingabesystem, Grundlagenkomponenten und gemeinsame Bausteine für räumliche Interaktionen. MRTK, Version 2, soll die Anwendungsentwicklung für Microsoft HoloLens, für immersive Windows Mixed Reality-Headsets (VR) und für die OpenVR-Plattform beschleunigen. Das Projekt ist darauf ausgerichtet, die Einstiegshürden zum Erstellen von Mixed Reality-Anwendungen zu verringern, und einen Beitrag für die Community auf diesem stetig wachsenden Gebiet zu leisten.

> [!div class="nextstepaction"]
> [Probieren Sie unsere MRTK-Tutorials aus](./tutorials/mr-learning-base-02.md?tabs=wsa)

Weitere Details zu Features finden Sie in der [MRTK-Dokumentation](/windows/mixed-reality/mrtk-unity).

## <a name="manual-setup-without-mrtk"></a>Manuelle Einrichtung ohne MRTK

Wenn Sie desktop VR als Ziel verwenden möchten, empfehlen wir, die pc Standalone Platform zu verwenden, die standardmäßig für ein neues Unity-Projekt ausgewählt ist:

![Screenshot des Fensters "Build Einstellungen", das im Unity-Editor geöffnet ist, wobei PC, Mac & eigenständige Plattform hervorgehoben ist](images/wmr-config-img-3.png)

Wenn Sie HoloLens 2 als Ziel verwenden, müssen Sie zur universellen Windows-Plattform wechseln:

1.  Wählen Sie **Datei > Build Einstellungen... aus.**
2.  Wählen Sie in der Liste Plattform die Option **Universal Windows Platform** und dann Plattform **wechseln** aus.
3.  Legen Sie **Architektur** auf **ARM 64** fest
4.  Legen Sie **Zielgerät** auf **HoloLens** fest
5.  Legen Sie **Buildtyp** auf **D3D** fest
6.  Legen Sie **UWP SDK** auf **Zuletzt installiert** fest
7.  Legen Sie **Buildkonfiguration** auf **Release** fest, da beim Debuggen bekannte Leistungsprobleme auftreten.

![Screenshot des Fensters "Build Einstellungen" im Unity-Editor mit hervorgehobener "Universal Windows Platform"](images/wmr-config-img-4.png)

Nachdem Sie Ihre Plattform festgelegt haben, müssen Sie Unity mitteilen, dass beim Exportieren eine [immersive Ansicht](../../design/app-views.md) anstelle einer 2D-Ansicht erstellt werden soll.

> [!CAUTION]
> Legacy-XR ist in Unity 2019 veraltet und wurde in Unity 2020 entfernt.

1. Öffnen Sie **Player Einstellungen...** aus dem **Build Einstellungen... fenster** und erweitern Sie die **Gruppe XR Einstellungen**
2. Wählen Sie im Abschnitt **XR Einstellungen** virtual **reality supported (Virtual Reality unterstützt)** aus, um die Liste Virtual Reality-Geräte hinzuzufügen.
3. Festlegen des **Tiefenformats** auf **16-Bit-Tiefe** und Aktivieren der **Tiefenpufferfreigabe**
4. Festlegen **des Stereorenderingmodus** auf **eine Einzeldurchlaufinstanz**
5. Wählen Sie **WSA Holographic Remoting Supported (Unterstütztes WSA Holographic Remoting)** aus, wenn Sie Holographic Remoting verwenden möchten. 

![Screenshot des fensters "Project"-Einstellungen, das im Unity-Editor geöffnet ist, wobei der Abschnitt "Playereinstellungen" hervorgehoben ist](images/wmr-config-img-9.png)