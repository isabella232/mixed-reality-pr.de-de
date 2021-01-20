---
title: WinRT in Unreal
description: Erfahren Sie, wie Sie benutzerdefinierte WinRT-Funktionen in Unreal Mixed Reality-Apps für hololens-Geräte schreiben und verwalten.
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, hololens, hololens 2, Streaming, Remoting, Mixed Reality, Development, Getting Started, Features, New Project, Emulator, Documentation, Guides, Features, holograms, Game Development, Mixed Reality Headset, Windows Mixed Reality Headset, Virtual Reality Headset, WinRT, dll
ms.openlocfilehash: f32b5b3ddbee2e24e61d08b0a1b887b7b06e6da4
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580407"
---
# <a name="winrt-in-unreal"></a>WinRT in Unreal

Im Verlauf der hololens-Entwicklung müssen Sie möglicherweise eine Funktion mit WinRT schreiben. Wenn Sie z. b. eine Datei Dialogfeld in einer hololens-Anwendung öffnen, benötigen Sie die filesavepicker in der Header Datei WinRT/Windows. Storage. Pickers. h. WinRT wird im Buildsystem von Unreal ab Version 4,26 unterstützt.

[!INCLUDE[](includes/tabs-winRT.md)]

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie der Unity-Entwicklungs-Journey folgen, die wir entworfen haben, befinden Sie sich mitten im Kennenlernen der Mixed Reality-Plattformfunktionen und APIs. Von hier aus können Sie mit jedem [Thema](unreal-development-overview.md#3-advanced-features) fortfahren oder direkt zum Bereitstellen Ihrer APP auf einem Gerät oder Emulator wechseln.

> [!div class="nextstepaction"]
> [Bereitstellung auf Gerät](unreal-deploying.md)

## <a name="see-also"></a>Weitere Informationen

* [C++/WinRT-APIs](/windows/uwp/cpp-and-winrt-apis/)
* [Filesavepicker-Klasse](/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [Unreal-Bibliotheken von Drittanbietern](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html)