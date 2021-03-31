---
title: Verwenden der integrierten Unterstützung von XR
description: Erfahren Sie, wie Sie Ihre Unity-Projekte mit und ohne mrtk mithilfe der vordefinierten Unterstützung von XR einrichten.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, gemischte Realität, Entwicklung, Einstieg, neues Projekt, Windows Mixed Reality, UWP, XR, Leistung, Legacy, mrtk
ms.openlocfilehash: 0860154034a63d5058da09a3b842e70bc3775dc5
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2021
ms.locfileid: "105938137"
---
# <a name="using-legacy-built-in-xr-support"></a>Verwenden der integrierten Unterstützung von XR

## <a name="setting-up-your-project-with-mrtk"></a>Einrichten Ihres Projekts mit mrtk

MRTK für Unity bietet ein plattformübergreifendes Eingabesystem, Grundlagenkomponenten und gemeinsame Bausteine für räumliche Interaktionen. MRTK, Version 2, soll die Anwendungsentwicklung für Microsoft HoloLens, für immersive Windows Mixed Reality-Headsets (VR) und für die OpenVR-Plattform beschleunigen. Das Projekt ist darauf ausgerichtet, die Einstiegshürden zum Erstellen von Mixed Reality-Anwendungen zu verringern, und einen Beitrag für die Community auf diesem stetig wachsenden Gebiet zu leisten.

> [!div class="nextstepaction"]
> [Testen Sie unsere mrtk-Tutorials](tutorials/mr-learning-base-01.md)

Weitere Featuredetails finden Sie in [der Dokumentation zu mrtk](/windows/mixed-reality/mrtk-unity) .

## <a name="manual-setup-without-mrtk"></a>Manuelles Setup ohne mrtk

Wenn Sie auf Desktop VR abzielen, empfiehlt es sich, die eigenständige PC-Plattform zu verwenden, die für ein neues Unity-Projekt standardmäßig ausgewählt ist:

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor mit PC, Mac & eigenständige Plattform hervorgehoben](images/wmr-config-img-3.png)

Wenn Sie hololens 2 als Ziel verwenden, müssen Sie zum universelle Windows-Plattform wechseln:

1.  **Datei > Buildeinstellungen auswählen...**
2.  Wählen Sie in der Platt Form Liste **universelle Windows-Plattform** aus, und wählen Sie **Plattform wechseln**
3.  **Architektur** auf **Arm 64** festlegen
4.  **Zielgerät** auf **hololens** festlegen
5.  **Buildtyp** auf **D3D** festlegen
6.  **UWP SDK** auf **Letztes installiert** festlegen
7.  **Buildkonfiguration** auf **Release** festlegen, da beim Debuggen bekannte Leistungsprobleme auftreten

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor öffnen mit hervorgehobener universelle Windows-Plattform](images/wmr-config-img-4.png)

Nachdem Sie Ihre Plattform festgelegt haben, müssen Sie Unity mitteilen, dass Sie beim Exportieren eine [immersive Ansicht](../../design/app-views.md) anstelle einer 2D-Ansicht erstellen soll.

> [!CAUTION]
> Legacy XR ist in Unity 2019 veraltet und wurde in Unity 2020 entfernt.

1. **Player Einstellungen** öffnen... aus den **Buildeinstellungen... Fenster** und erweitern Sie die Gruppe " **XR-Einstellungen** ".
2. Wählen Sie im Abschnitt " **XR-Einstellungen** " die Option **virtuelle Realität unterstützt** aus, um die Liste Virtual Reality-Geräte
3. Festlegen des **tiefen Formats** auf eine **16-Bit-Tiefe** und Aktivieren der **tiefen Puffer Freigabe**
4. Festlegen des **Stereo Renderingmodus** auf eine **Einzel Pass Instanz**
5. Wählen Sie **WSA Holographic Remoting unterstützt** aus, wenn Sie Holographic Remoting verwenden möchten. 

![Screenshot des Fensters "Projekteinstellungen" im Unity-Editor mit hervorgehobenem Abschnitt "Player Einstellungen"](images/wmr-config-img-9.png)