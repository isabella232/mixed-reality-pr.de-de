---
title: 'OpenXR: Problembehandlung'
description: Beheben Sie Probleme in ihren openxr-Anwendungen.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: Openxr, Khronos, basicxrapp, DirectX, Native, Native APP, benutzerdefinierte Engine, Middleware, Problembehandlung
ms.openlocfilehash: ddfe548d689d84576ad0ac06bda46d7c2757859c
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2020
ms.locfileid: "97612934"
---
# <a name="openxr-troubleshooting"></a><span data-ttu-id="85d3e-104">OpenXR: Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="85d3e-104">OpenXR troubleshooting</span></span>

<span data-ttu-id="85d3e-105">Im folgenden finden Sie einige Tipps zur Problembehandlung bei der Entwicklung einer openxr-App mithilfe der Windows Mixed Reality openxr-Laufzeit.</span><span class="sxs-lookup"><span data-stu-id="85d3e-105">Here are some troubleshooting tips when developing an OpenXR app using the Windows Mixed Reality OpenXR Runtime.</span></span>  <span data-ttu-id="85d3e-106">Wenn Sie weitere Fragen zur <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">openxr 1,0-Spezifikation</a>haben, besuchen Sie die <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos openxr-Foren</a> oder <a href="https://khr.io/slack" target="_blank">Slack #openxr Channel</a>.</span><span class="sxs-lookup"><span data-stu-id="85d3e-106">If you have any other questions about the <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 specification</a>, visit the <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR Forums</a> or <a href="https://khr.io/slack" target="_blank">Slack #openxr channel</a>.</span></span>

>[!NOTE]
><span data-ttu-id="85d3e-107">In der aktuellen Windows Mixed Reality openxr-Laufzeit mit x86-apps sind bekannte Probleme aufgetreten.</span><span class="sxs-lookup"><span data-stu-id="85d3e-107">There are known issues in the current Windows Mixed Reality OpenXR runtime with x86 apps.</span></span>  <span data-ttu-id="85d3e-108">Sie sollten momentan openxr-Desktop-Apps für x64 erstellen.</span><span class="sxs-lookup"><span data-stu-id="85d3e-108">You should build desktop OpenXR apps for x64 at the moment.</span></span>

### <a name="openxr-app-not-starting-windows-mixed-reality"></a><span data-ttu-id="85d3e-109">Openxr-App startet nicht Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="85d3e-109">OpenXR app not starting Windows Mixed Reality</span></span>

<span data-ttu-id="85d3e-110">Wenn Ihre openxr-APP nicht Windows Mixed Reality startet, wenn Sie Sie ausführen, kann die openxr-Laufzeit von Windows Mixed Reality nicht als aktive Laufzeit festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="85d3e-110">If your OpenXR app isn't starting Windows Mixed Reality when you run it, the Windows Mixed Reality OpenXR Runtime may not be set as the active runtime.</span></span> <span data-ttu-id="85d3e-111">Befolgen Sie die Anweisungen für den [Einstieg in openxr für Windows Mixed Reality-Headsets](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) , um das Problem zu beheben.</span><span class="sxs-lookup"><span data-stu-id="85d3e-111">Follow the instructions for [getting started with OpenXR for Windows Mixed Reality headsets](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) to fix the issue.</span></span>

<span data-ttu-id="85d3e-112">Sie können auch das [openxr-Entwicklertools für Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) ausführen, um Hilfe zur Problembehandlung für den Zustand ihrer Systeme Windows Mixed Reality openxr Runtime zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="85d3e-112">You can also run the [OpenXR Developer Tools for Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) to get troubleshooting help on the state of your systems Windows Mixed Reality OpenXR Runtime.</span></span>