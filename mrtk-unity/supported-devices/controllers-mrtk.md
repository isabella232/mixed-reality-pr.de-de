---
title: Controller in MRTK
description: Dokumentation zur Verwendung verschiedener Controller mit MRTK
author: RogPodge
ms.author: roliu
ms.date: 05/13/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Controller, HP Reverb, Oculus, UNITY Vive, Hands
ms.openlocfilehash: 953b1cd56dbf7d7a548a3aba8da07ce5875fec74
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145470"
---
# <a name="controllers-in-mrtk"></a>Controller in MRTK

MRTK bietet Unterstützung für viele verschiedene Controller. Viele Controller, wie z. B. BLEND Vive Knuckles und BLEND Vive Wands, funktionieren nativ, sobald eine mit MRTK konstruierte Anwendung auf dem kompatiblen Gerät gestartet wird. Andere Controller, z. B. die artikulierten Hände auf oculus Quest und den HP Reverb G2-Controllern, erfordern zusätzliche Pakete, bevor sie vom MRTK erkannt werden.

In diesem Dokument werden die gängigen Szenarien beschrieben, in denen zusätzliche Pakete installiert werden müssen. Weitere Informationen zu Controllern finden Sie auf der Seite mit den [**Features.**](../features/input/controllers.md) Informationen zum Debuggen von Problemen mit Controllern finden Sie unter [ **Controllerzuordnungstool.**](../features/tools/controller-mapping-tool.md)

## <a name="hp-reverb-g2-controllers"></a>HP Reverb G2-Controller

Führen Sie zum Erkennen und Anzeigen der HP Reverb G2-Controller bei Verwendung des MRTK die folgenden Schritte aus, um das [**Paket Microsoft.MixedReality.Input**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) zu installieren. Nach der Installation dieses Pakets müssen keine weiteren Änderungen an den Standardprofilen vorgenommen werden, damit die Controller auf dem HP Reverb angezeigt werden. 

Um die Controller im Editor anzuzeigen, müssen Sie sicherstellen, dass Sie mit dem [**OpenXR-Plug-In**](/windows/mixed-reality/develop/unity/openxr-getting-started)verwenden.

## <a name="oculus-controllers"></a>Oculus-Controller 

Befolgen Sie die Anweisungen zur Oculus Quest-Bereitstellung, um Oculus-Controllermodelle zu visualisieren. Wenn Sie virtuelle Hände anzeigen möchten, wenn Sie die Controller verwenden, stellen Sie sicher, dass **Render Avatar Hands Instead Of Controllers** unter dem XR SDK Oculus Geräte-Manager aktiviert ist. Deaktivieren Sie andernfalls diese Option.

![OculusDeviceManagerVisualizationSettings](../images/cross-platform/oculus-quest/OculusDeviceManager.png)
