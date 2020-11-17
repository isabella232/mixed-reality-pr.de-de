---
title: Verwaltetes Debuggen mit Unity IL2CPP
description: In diesem Artikel wird beschrieben, wie Sie einen verwalteten Debugger in Ihrem Unity IL2CPP-UWP-Projekt ausführen.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: Unity, Visual Studio, Debugging, il2cpp, hololens, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, UWP
ms.openlocfilehash: 96a2c21fc6f8b2bdab199e65c9b1a31ffb6e029b
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678589"
---
# <a name="managed-debugging-with-unity-il2cpp"></a>Verwaltetes Debuggen mit Unity IL2CPP

Führen Sie die folgenden Schritte aus, um einen verwalteten Debugger an Ihren Unity IL2CPP UWP-Build anzufügen. Dieses Handbuch wurde ursprünglich für hololens und hololens 2 entwickelt.

1. Sie müssen sich in einem Netzwerk befinden, das [Multicast](https://en.wikipedia.org/wiki/Multicast)unterstützt.
1. Stellen Sie sicher, dass **internetclientserver** und **privatenetworkclientserver** in Unity unter den Funktionen der UWP-Veröffentlichungs Einstellungen eingeglichen werden.

    ![Funktionen der UWP-Veröffentlichungs Einstellungen](images/il2cpp-debugging-capabilities.png)

1. Konfigurieren Sie die Unity-UWP-Buildeinstellungen:
    - Development Build
    - Skriptdebugging
    - Auf verwalteten Debugger warten (optional)

    ![UWP-Buildeinstellungen](images/il2cpp-debugging-build.png)

1. Erstellen Sie in Unity.
1. Erstellen Sie die Visual Studio-Projekt Mappe, und stellen Sie Sie auf Ihrem Gerät bereit. Sie sollten mit den **Debug** -oder **Releasekonfigurationen** erstellen. Die **Master** Konfiguration deaktiviert den Unity-Profiler und kann ein optimales Debuggen verhindern. Überprüfen Sie optional das **Internet (Client & Server)** und **private Netzwerke (Client & Server)** in der Liste der Funktionen in "Package. appxmanifest" in der Projekt Mappe.
1. Starten Sie die APP auf Ihrem Gerät. Stellen Sie sicher, dass das Gerät mit dem Netzwerk verbunden ist, das mit dem PC verbunden ist.
1. Stellen Sie sicher, dass das Gerät nicht über USB mit dem PC verbunden **ist** .
1. Wechseln Sie zur Visual Studio-Projekt Mappe, die erstellt wird, wenn Sie auf ein Skript in Unity doppelklicken, in dem Sie die c#-Skripts anzeigen und bearbeiten können.
1. Debug-> Unity-Debugger anfügen.

    ![Unity-Debugger anhängen](images/il2cpp-debugging-attach.png)

1. Wählen Sie in der Liste Ihr Gerät aus, und klicken Sie auf "OK"

    ![Geräteliste](images/il2cpp-debugging-machines.png)
