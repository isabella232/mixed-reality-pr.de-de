---
title: Verwaltetes Debuggen mit Unity
description: In diesem Artikel wird beschrieben, wie Sie einen verwalteten Debugger in Ihrem Unity IL2CPP-UWP-Projekt ausführen.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: Unity, Visual Studio, Debuggen, il2cpp, HoloLens, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, UWP
ms.openlocfilehash: 92b730768b6402b356e550d8f01d85e654832aef1ac382d8f992df615a9ce1b4
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196542"
---
# <a name="managed-debugging-with-unity"></a>Verwaltetes Debuggen mit Unity

Führen Sie diese Schritte aus, um einen verwalteten Debugger an Ihren Unity IL2CPP-UWP-Build für HoloLens und HoloLens 2 anzufügen.

1. Sie müssen sich in einem Netzwerk befinden, das [Multicast](https://en.wikipedia.org/wiki/Multicast)unterstützt.
2. Wechseln Sie zu **UWP Publishing Einstellungen Capabilities (UWP-Veröffentlichungsfunktionen),** und aktivieren Sie **InternetClientServer** und **PrivateNetworkClientServer:**

    ![Funktionen für die UWP-Veröffentlichung Einstellungen](images/il2cpp-debugging-capabilities.png)

3. Konfigurieren Sie die Unity UWP-Buildeinstellungen:
    - Development Build
    - Skriptdebugging
    - Warten auf verwalteten Debugger (optional)

    ![UWP Build Einstellungen](images/il2cpp-debugging-build.png)

4. Erstellen Sie in Unity.
5. Erstellen und Bereitstellen über die Visual Studio-Lösung auf Ihrem Gerät Sie sollten mit den **Debug-** oder **Releasekonfigurationen** erstellen. Die **Masterkonfiguration** deaktiviert den Unity-Profiler und kann ein optimales Debuggen verhindern. Überprüfen Sie optional **Internet (Client & Server)** und **Private Netzwerke (Client & Server)** in der Liste der Funktionen in Package.appxmanifest in der Lösung.
6. Stellen Sie sicher, dass Ihr Gerät mit demselben Netzwerk wie Ihr PC verbunden ist, und starten Sie die App auf Ihrem Gerät.
7. Stellen Sie sicher, dass das Gerät nicht über USB mit Ihrem PC verbunden **ist.**
8. Doppelklicken Sie auf eines Ihrer Skripts in Unity, und wechseln Sie zur Visual Studio Projektmappe, die zum Anzeigen und Bearbeiten geöffnet wird.
9. Debuggen > Anfügen des Unity-Debuggers.

    ![Unity-Debugger anhängen](images/il2cpp-debugging-attach.png)

10. Wählen Sie Ihr Gerät in der Liste aus, und klicken Sie auf "OK", um es anzufügen.

    ![Geräteliste](images/il2cpp-debugging-machines.png)

## <a name="see-also"></a>Siehe auch 

* [C#-Debuggen](/visualstudio/get-started/csharp/tutorial-debugger)
