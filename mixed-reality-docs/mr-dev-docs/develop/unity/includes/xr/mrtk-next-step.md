---
ms.openlocfilehash: dbaace96246f28050ff6fb189d9b626be6b0ec9e
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603714"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

Beginnen Sie mit Schritt 2 im MRTK-Tutorial, um mit einem neuen **Unity-Projekt** mit MRTK zu beginnen:

> [!div class="nextstepaction"]
> [Einrichten eines neuen OpenXR-Projekts mit MRTK](../../tutorials/mr-learning-base-02.md?tabs=openxr)

Wenn Sie ein vorhandenes **MRTK-Projekt auf OpenXR** aktualisieren, sollten Sie zuerst ein Upgrade von MRTK-Unity auf die neueste Version (Version 2.7.2 oder höher) durchführen, um wichtige Fehlerbehebungen für die Kompatibilität mit dem Mixed Reality OpenXR-Plug-In zu erhalten.  Verwenden Sie [das Mixed Reality-Featuretool,](../../welcome-to-mr-feature-tool.md) um ein Upgrade auf die neueste Version von MRTK zu durchführen, und führen Sie dann die schritte zum manuellen [OpenXR-Setup unter aus.](#manual-setup-without-mrtk) In der MRTK-Dokumentation finden Sie detailliertere Informationen zum Migrieren eines vorhandenen [MRTK-Projekts zu OpenXR.](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)

> [!NOTE]
> Stellen Sie beim Upgrade von einer früheren Version von MRTK vor **2.5.3** sicher, dass sich die folgende Zeile in der Datei **Assets/MixedRealityToolkit.Generated/link.xml** befindet:
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> Diese Zeile wird standardmäßig hinzugefügt, wenn Sie mit MRTK 2.5.4 oder neuer begonnen haben.

# <a name="windows-xr"></a>[Windows Xr](#tab/windowsxr)

Beginnen Sie mit Schritt 2 im MRTK-Tutorial, um mit einem neuen **Unity-Projekt** mit MRTK zu beginnen:

> [!div class="nextstepaction"]
> [Einrichten eines neuen XR Windows projekts mit MRTK](../../tutorials/mr-learning-base-02.md?tabs=winxr)

# <a name="legacy-xr"></a>[Legacy-XR](#tab/legacy)

Beginnen Sie mit Schritt 2 im MRTK-Tutorial, um mit einem neuen **Unity-Projekt** mit MRTK zu beginnen:

> [!div class="nextstepaction"]
> [Einrichten eines neuen Legacy-XR-Projekts mit MRTK](../../tutorials/mr-learning-base-02.md?tabs=wsa)