---
title: HP-Reverb-G2-Controller in Unity
description: Anweisungen zur Verwendung der HP-Reverb-G2-Controller in steamvr und Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 10/14/2020
ms.topic: article
keywords: Unity, Reverb, Reverb G2, HP-Simulator G2, gemischte Realität, Entwicklung, Motion Controller, Benutzereingaben, Features, neues Projekt, Emulator, Dokumentation, Anleitungen, Features, Hologramme, Spieleentwicklung
ms.openlocfilehash: 3add2ae52fbaba087da257212e1d8ddfdffe702a
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638387"
---
# <a name="hp-reverb-g2-controllers-in-unity"></a><span data-ttu-id="7fae3-104">HP-Reverb-G2-Controller in Unity</span><span class="sxs-lookup"><span data-stu-id="7fae3-104">HP Reverb G2 Controllers in Unity</span></span>

## <a name="getting-started"></a><span data-ttu-id="7fae3-105">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="7fae3-105">Getting started</span></span>

<span data-ttu-id="7fae3-106">Es ist kein zusätzliches Setup erforderlich, um den HP-Reverb-G2-Controller zu verwenden, wenn Sie für steamvr entwickeln oder die Windows Mixed Reality-Eingabe-API (XR) verwenden. WSA. Eingabe).</span><span class="sxs-lookup"><span data-stu-id="7fae3-106">There's no additional setup required to use the HP Reverb G2 controller if you're developing for SteamVR or using the Windows Mixed Reality Input API (XR.WSA.Input).</span></span> <span data-ttu-id="7fae3-107">Allerdings sind die Schaltflächen A, B, X, Y und der squeeze-Trigger zurzeit über den Eingabe-Manager nicht zugänglich, es sei denn, Sie verwenden steamvr.</span><span class="sxs-lookup"><span data-stu-id="7fae3-107">However, the A, B, X, Y buttons and the squeeze trigger are not currently accessible through the Input Manager unless you're using SteamVR.</span></span> <span data-ttu-id="7fae3-108">Unterstützung für die zusätzlichen Reverb-G2-Eingaben ist in naher Zukunft verfügbar. Achten Sie also darauf, dass Sie die Überprüfung wirklich durchführt!</span><span class="sxs-lookup"><span data-stu-id="7fae3-108">Support for the extra Reverb G2 inputs will be available in the near future, so be sure to check back!</span></span>

## <a name="porting-existing-applications"></a><span data-ttu-id="7fae3-109">Portieren vorhandener Anwendungen</span><span class="sxs-lookup"><span data-stu-id="7fae3-109">Porting existing applications</span></span>

<span data-ttu-id="7fae3-110">Wenn Sie bereits über eine vorhandene App verfügen, die Sie für Windows Mixed Reality-immersive Headsets entwickeln, sehen Sie sich die Abschnitte [Portierungs Handbuch](../porting-apps/porting-guides.md) und [Projekteinstellungen](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project#unity-porting-guidance) an, um allgemeine Vorschläge zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="7fae3-110">If you already have an existing app that you're developing for Windows Mixed Reality immersive headsets, check out our [porting guide](../porting-apps/porting-guides.md) and [project settings](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project#unity-porting-guidance) sections for general suggestions.</span></span>

## <a name="mapping-input"></a><span data-ttu-id="7fae3-111">Zuordnung von Eingaben</span><span class="sxs-lookup"><span data-stu-id="7fae3-111">Mapping input</span></span>

<span data-ttu-id="7fae3-112">Wenn Sie bereit sind, Ihre Eingabe Zuordnung für Ihre neuen Controller einzurichten und in Betrieb zu nehmen, beginnen Sie mit dem Abschnitt [Eingabe Zuordnung](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input#unity-porting-guidance) des immersiven portieren-Handbuchs.</span><span class="sxs-lookup"><span data-stu-id="7fae3-112">When you're ready to get your input mapping up and running for your new controllers, start at the [input mapping](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input#unity-porting-guidance) section of the immersive porting guide.</span></span> <span data-ttu-id="7fae3-113">Anweisungen zum Konfigurieren von Eingaben in Unity finden Sie in [Gesten und Bewegungs Controllern](gestures-and-motion-controllers-in-unity.md)sowie eine vollständige [Schaltfläche und eine Tabellen Zuordnung](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) .</span><span class="sxs-lookup"><span data-stu-id="7fae3-113">Instructions on how to configure inputs in Unity is detailed in [Gestures and motion controllers](gestures-and-motion-controllers-in-unity.md), along with a full [button and axis mapping table](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) for reference.</span></span>

## <a name="see-also"></a><span data-ttu-id="7fae3-114">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="7fae3-114">See also</span></span>
* [<span data-ttu-id="7fae3-115">Aktualisierung für SteamVR</span><span class="sxs-lookup"><span data-stu-id="7fae3-115">Updating for SteamVR</span></span>](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)