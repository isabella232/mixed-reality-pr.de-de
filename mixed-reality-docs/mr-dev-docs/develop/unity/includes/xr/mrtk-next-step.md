---
ms.openlocfilehash: 695db2d7e6765d3584c9e9a6459071ab537c1f003d13461ce5736481b98b7495
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202753"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

Beginnen Sie mit Schritt 2 im MRTK-Tutorial, um mit einem **neuen Unity-Projekt** mit MRTK zu beginnen:

> [!div class="nextstepaction"]
> [Einrichten eines neuen OpenXR-Projekts mit MRTK](../../tutorials/mr-learning-base-02.md?tabs=openxr)

Wenn Sie ein **vorhandenes MRTK-Projekt auf OpenXR** aktualisieren, sollten Sie zunächst MRTK-Unity auf die neueste Version (Version 2.7.2 oder höher) aktualisieren, um wichtige Fehlerbehebungen für die Kompatibilität mit dem Mixed Reality OpenXR-Plug-In zu erhalten.  Verwenden Sie das [Mixed Reality Feature-Tool,](../../welcome-to-mr-feature-tool.md) um ein Upgrade auf die neueste Version von MRTK durchzuführen, und führen Sie dann die [manuellen OpenXR-Setupschritte unter aus.](#manual-setup-without-mrtk) Ausführlichere Informationen zum [Migrieren eines vorhandenen MRTK-Projekts zu OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)finden Sie in der MRTK-Dokumentation.

> [!NOTE]
> Stellen Sie beim Upgrade von einer früheren Version von MRTK vor **2.5.3** sicher, dass sich die folgende Zeile in der Datei **Assets/MixedRealityToolkit.Generated/link.xml** befindet:
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> Diese Zeile wird standardmäßig hinzugefügt, wenn Sie mit MRTK 2.5.4 oder neuer gestartet haben.

# <a name="windows-xr"></a>[Windows Xr](#tab/windowsxr)

Beginnen Sie mit Schritt 2 im MRTK-Tutorial, um mit einem **neuen Unity-Projekt** mit MRTK zu beginnen:

> [!div class="nextstepaction"]
> [Einrichten eines neuen Windows XR-Projekts mit MRTK](../../tutorials/mr-learning-base-02.md?tabs=winxr)

# <a name="legacy-xr"></a>[Legacy-XR](#tab/legacy)

Beginnen Sie mit Schritt 2 im MRTK-Tutorial, um mit einem **neuen Unity-Projekt** mit MRTK zu beginnen:

> [!div class="nextstepaction"]
> [Einrichten eines neuen Legacy-XR-Projekts mit MRTK](../../tutorials/mr-learning-base-02.md?tabs=wsa)