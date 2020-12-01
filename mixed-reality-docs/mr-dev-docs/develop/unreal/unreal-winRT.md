---
title: WinRT in Unreal
description: Übersicht zum Plug-In für räumliche Audiowiedergabe für die Unreal Engine.
author: fieldsJacksonG
ms.author: jacksonf
ms.date: 07/08/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, hololens, hololens 2, Streaming, Remoting, Mixed Reality, Development, Getting Started, Features, New Project, Emulator, Documentation, Guides, Features, holograms, Game Development, Mixed Reality Headset, Windows Mixed Reality Headset, Virtual Reality Headset, WinRT, dll
ms.openlocfilehash: 722add1601013d206ffface84d3a53cf3a9d89f9
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2020
ms.locfileid: "96354443"
---
# <a name="winrt-in-unreal"></a><span data-ttu-id="00fe2-104">WinRT in Unreal</span><span class="sxs-lookup"><span data-stu-id="00fe2-104">WinRT in Unreal</span></span>

<span data-ttu-id="00fe2-105">Im Verlauf der hololens-Entwicklung müssen Sie möglicherweise eine Funktion mit WinRT schreiben.</span><span class="sxs-lookup"><span data-stu-id="00fe2-105">Over the course of your HoloLens development you may need to write a feature using WinRT.</span></span> <span data-ttu-id="00fe2-106">Wenn Sie z. b. eine Datei Dialogfeld in einer hololens-Anwendung öffnen, benötigen Sie die filesavepicker in der Header Datei WinRT/Windows. Storage. Pickers. h.</span><span class="sxs-lookup"><span data-stu-id="00fe2-106">For example, opening a file dialogue in a HoloLens application would need the FileSavePicker in winrt/Windows.Storage.Pickers.h header file.</span></span> <span data-ttu-id="00fe2-107">WinRT wird im Buildsystem von Unreal ab Version 4,26 unterstützt.</span><span class="sxs-lookup"><span data-stu-id="00fe2-107">WinRT is supported in Unreal's build system from version 4.26 onwards.</span></span>

[!INCLUDE[](includes/tabs-winRT.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="00fe2-108">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="00fe2-108">Next Development Checkpoint</span></span>

<span data-ttu-id="00fe2-109">Wenn Sie dem Weg der Unity-Entwicklungsprüfpunkte folgen, den wir entworfen haben, befinden Sie sich mitten im Kennenlernen der Mixed Reality-Plattformfunktionen und APIs.</span><span class="sxs-lookup"><span data-stu-id="00fe2-109">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="00fe2-110">Von hier aus können Sie mit jedem [Thema](unreal-development-overview.md#3-platform-capabilities-and-apis) fortfahren oder direkt zum Bereitstellen Ihrer APP auf einem Gerät oder Emulator wechseln.</span><span class="sxs-lookup"><span data-stu-id="00fe2-110">From here, you can proceed to any [topic](unreal-development-overview.md#3-platform-capabilities-and-apis) or jump directly to deploying your app on a device or emulator.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="00fe2-111">Bereitstellung auf Gerät</span><span class="sxs-lookup"><span data-stu-id="00fe2-111">Deploying to device</span></span>](unreal-deploying.md)

## <a name="see-also"></a><span data-ttu-id="00fe2-112">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="00fe2-112">See also</span></span>
* [<span data-ttu-id="00fe2-113">C++/WinRT-APIs</span><span class="sxs-lookup"><span data-stu-id="00fe2-113">C++/WinRT APIs</span></span>](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/)
* [<span data-ttu-id="00fe2-114">Filesavepicker-Klasse</span><span class="sxs-lookup"><span data-stu-id="00fe2-114">FileSavePicker class</span></span>](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [<span data-ttu-id="00fe2-115">Unreal-Bibliotheken von Drittanbietern</span><span class="sxs-lookup"><span data-stu-id="00fe2-115">Unreal Third-Party Libraries</span></span>](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html) 
