---
title: WinRT in Unreal
description: Erfahren Sie, wie Sie benutzerdefinierte WinRT-Features in Unreal Mixed Reality-Apps für HoloLens verwalten.
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Streaming, Remoting, Mixed Reality, Entwicklung, erste Schritte, Features, neues Projekt, Emulator, Dokumentation, Leitfäden, Features, Hologramme, Spieleentwicklung, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, WinRT, DLL
ms.openlocfilehash: b00886908f51804650220b6dbb7b3bfe4184cf33b505e3bd278327d1669c5067
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198380"
---
# <a name="winrt-in-unreal"></a>WinRT in Unreal

Im Laufe ihrer HoloLens müssen Sie möglicherweise ein Feature mit WinRT schreiben. Wenn Sie z. B. ein Dateidialogfeld in einer HoloLens Anwendung öffnen, benötigen Sie fileSavePicker in winrt/Windows. Storage. Pickers.h-Headerdatei. WinRT wird ab Version 4.26 im Unreal-Buildsystem unterstützt.

[!INCLUDE[](includes/tabs-winRT.md)]

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie der Unity-Entwicklungs-Journey folgen, die wir entworfen haben, befinden Sie sich mitten im Kennenlernen der Mixed Reality-Plattformfunktionen und APIs. Von hier aus können Sie mit jedem [Thema](unreal-development-overview.md#3-advanced-features) fortfahren oder direkt zur Bereitstellung Ihrer App auf einem Gerät oder Emulator springen.

> [!div class="nextstepaction"]
> [Bereitstellung auf Gerät](unreal-deploying.md)

## <a name="see-also"></a>Siehe auch

* [C++/WinRT-APIs](/windows/uwp/cpp-and-winrt-apis/)
* [FileSavePicker-Klasse](/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [Unreal-Bibliotheken von Drittanbietern](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html)