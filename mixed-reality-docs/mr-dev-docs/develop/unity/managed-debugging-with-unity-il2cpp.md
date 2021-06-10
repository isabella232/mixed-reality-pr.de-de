---
title: Verwaltetes Debuggen mit Unity
description: In diesem Artikel wird beschrieben, wie Sie einen verwalteten Debugger in Ihrem Unity IL2CPP-UWP-Projekt ausführen.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: Unity, Visual Studio, Debuggen, il2cpp, HoloLens, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, UWP
ms.openlocfilehash: 8e3967971220fa453f4e60639bd08f2554a8dd7e
ms.sourcegitcommit: 5617575cf550dd03fba0bfd5263e97972dcc646b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547079"
---
# <a name="managed-debugging-with-unity"></a>Verwaltetes Debuggen mit Unity

Führen Sie die folgenden Schritte aus, um einen verwalteten Debugger an Ihren Unity IL2CPP-UWP-Build für HoloLens HoloLens 2.

1. Sie müssen sich in einem Netzwerk mit [Multicast unterstützen.](https://en.wikipedia.org/wiki/Multicast)
2. Wechseln Sie zu **UWP Publishing Settings Capabilities (Funktionen für UWP-Veröffentlichungseinstellungen),** und aktivieren Sie **InternetClientServer** und **PrivateNetworkClientServer:**

    ![Funktionen für UWP-Veröffentlichungseinstellungen](images/il2cpp-debugging-capabilities.png)

3. Konfigurieren Sie die Unity-UWP-Buildeinstellungen:
    - Development Build
    - Skriptdebugging
    - Warten auf verwalteten Debugger (optional)

    ![UWP-Buildeinstellungen](images/il2cpp-debugging-build.png)

4. Erstellen Sie in Unity.
5. Erstellen Und bereitstellen Sie über die Visual Studio Lösung auf Ihrem Gerät. Sie sollten mit den Debug- **oder** **Releasekonfigurationen** erstellen. Die **Masterkonfiguration** deaktiviert den Unity-Profiler und kann ein optimales Debuggen verhindern. Überprüfen Sie optional **internet (Client & Server)** und **private Netzwerke (Client & Server)** in der Liste der Funktionen in Package.appxmanifest in der Lösung.
6. Stellen Sie sicher, dass Ihr Gerät mit demselben Netzwerk wie Ihr PC verbunden ist, und starten Sie die App auf Ihrem Gerät.
7. Stellen Sie sicher, dass **das Gerät nicht** über USB mit Ihrem PC verbunden ist.
8. Doppelklicken Sie auf eines Ihrer Skripts in Unity, und wechseln Sie zur Visual Studio, die zum Anzeigen und Bearbeiten geöffnet wird.
9. Debuggen – > Unity-Debugger anfügen.

    ![Unity-Debugger anhängen](images/il2cpp-debugging-attach.png)

10. Wählen Sie Ihr Gerät in der Liste aus, und klicken Sie zum Anfügen auf "OK".

    ![Geräteliste](images/il2cpp-debugging-machines.png)
