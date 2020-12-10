---
title: Verwaltetes Debuggen mit Unity IL2CPP
description: In diesem Artikel wird beschrieben, wie Sie einen verwalteten Debugger in Ihrem Unity IL2CPP-UWP-Projekt ausführen.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: Unity, Visual Studio, Debugging, il2cpp, hololens, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, UWP
ms.openlocfilehash: 4b21e4888e467e6bd5f1938024a1b8312d8ecbcb
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010241"
---
# <a name="managed-debugging-with-unity-il2cpp"></a>Verwaltetes Debuggen mit Unity IL2CPP

Führen Sie die folgenden Schritte aus, um einen verwalteten Debugger an Ihren Unity IL2CPP UWP-Build für hololens und hololens 2 anzufügen.

1. Sie müssen sich in einem Netzwerk befinden, das [Multicast](https://en.wikipedia.org/wiki/Multicast)unterstützt.
2. Wechseln Sie zu den Funktionen für die **UWP-Veröffentlichungs Einstellungen** , und überprüfen Sie **internetclientserver** und **privatenetworkclientserver**:

    ![Funktionen der UWP-Veröffentlichungs Einstellungen](images/il2cpp-debugging-capabilities.png)

3. Konfigurieren Sie die Unity-UWP-Buildeinstellungen:
    - Development Build
    - Skriptdebugging
    - Auf verwalteten Debugger warten (optional)

    ![UWP-Buildeinstellungen](images/il2cpp-debugging-build.png)

4. Erstellen Sie in Unity.
5. Erstellen Sie die Visual Studio-Projekt Mappe, und stellen Sie Sie auf Ihrem Gerät bereit. Sie sollten mit den **Debug** -oder **Releasekonfigurationen** erstellen. Die **Master** Konfiguration deaktiviert den Unity-Profiler und kann ein optimales Debuggen verhindern. Überprüfen Sie optional das **Internet (Client & Server)** und **private Netzwerke (Client & Server)** in der Liste der Funktionen in "Package. appxmanifest" in der Projekt Mappe.
6. Stellen Sie sicher, dass Ihr Gerät mit dem gleichen Netzwerk wie Ihr PC verbunden ist, und starten Sie die APP auf Ihrem Gerät.
7. Stellen Sie sicher, dass das Gerät nicht über USB mit dem PC verbunden **ist** .
8. Doppelklicken Sie auf eines Ihrer Skripts in Unity, und wechseln Sie zur Visual Studio-Projekt Mappe, die geöffnet wird, um Sie anzuzeigen und zu bearbeiten.
9. Debug-> Unity-Debugger anfügen.

    ![Unity-Debugger anhängen](images/il2cpp-debugging-attach.png)

10. Wählen Sie in der Liste Ihr Gerät aus, und klicken Sie auf "OK"

    ![Geräteliste](images/il2cpp-debugging-machines.png)
