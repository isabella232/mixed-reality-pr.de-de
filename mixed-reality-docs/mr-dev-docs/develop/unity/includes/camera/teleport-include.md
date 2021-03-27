---
ms.openlocfilehash: daf81bcd6ce215d908ce6b4028effcdc2ed38328
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636371"
---
# <a name="mrtk"></a>[<span data-ttu-id="b7858-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="b7858-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="b7858-102">Mrtk bietet ein in-Box- [teleportsystem](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) , das automatisch über Handgelenke und Controller hinweg funktioniert.</span><span class="sxs-lookup"><span data-stu-id="b7858-102">MRTK provides an in-box [teleport system](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) which automatically works across articulated hands and controllers.</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="b7858-103">XR SDK</span><span class="sxs-lookup"><span data-stu-id="b7858-103">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="b7858-104">Es wird empfohlen, die-Implementierung von mrtk zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="b7858-104">We recommend using MRTK's teleportation implementation.</span></span>
<span data-ttu-id="b7858-105">Wenn Sie mrtk nicht verwenden möchten, stellt Unity im [XR-Interaktions Toolkit](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html)eine Teleportations-Implementierung bereit.</span><span class="sxs-lookup"><span data-stu-id="b7858-105">If you choose not to use MRTK, Unity provides a teleportation implementation in the [XR Interaction Toolkit](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html).</span></span>
<span data-ttu-id="b7858-106">Wenn Sie sich für die Implementierung Ihrer eigenen entscheiden, sollten Sie Bedenken, dass Sie die Kamera nicht direkt verschieben können.</span><span class="sxs-lookup"><span data-stu-id="b7858-106">If you choose to implement your own, it's good to keep in mind that you can't move the camera directly.</span></span> <span data-ttu-id="b7858-107">Aufgrund der Unity-Kontrolle der Kamera für die Head-Nachverfolgung müssen Sie der Kamera ein übergeordnetes Element in der Hierarchie übergeben und stattdessen das gameobject verschieben.</span><span class="sxs-lookup"><span data-stu-id="b7858-107">Due to Unity's control of the camera for head tracking, you'll need to give the camera a parent in the hierarchy and move that GameObject instead.</span></span> <span data-ttu-id="b7858-108">Dies entspricht dem Playspace von mrtk.</span><span class="sxs-lookup"><span data-stu-id="b7858-108">This is the equivalent of MRTK's Playspace.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="b7858-109">Legacy-WSA</span><span class="sxs-lookup"><span data-stu-id="b7858-109">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="b7858-110">Es wird empfohlen, die-Implementierung von mrtk zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="b7858-110">We recommend using MRTK's teleportation implementation.</span></span>
<span data-ttu-id="b7858-111">Wenn Sie sich für die Implementierung Ihrer eigenen entscheiden, sollten Sie Bedenken, dass Sie die Kamera nicht direkt verschieben können.</span><span class="sxs-lookup"><span data-stu-id="b7858-111">If you choose to implement your own, it's good to keep in mind that you can't move the camera directly.</span></span> <span data-ttu-id="b7858-112">Aufgrund der Unity-Kontrolle der Kamera für die Head-Nachverfolgung müssen Sie der Kamera ein übergeordnetes Element in der Hierarchie übergeben und stattdessen das gameobject verschieben.</span><span class="sxs-lookup"><span data-stu-id="b7858-112">Due to Unity's control of the camera for head tracking, you'll need to give the camera a parent in the hierarchy and move that GameObject instead.</span></span> <span data-ttu-id="b7858-113">Dies entspricht dem Playspace von mrtk.</span><span class="sxs-lookup"><span data-stu-id="b7858-113">This is the equivalent of MRTK's Playspace.</span></span>