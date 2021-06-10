---
ms.openlocfilehash: 0a4f6f1262bcaa69a8755223d738bbd88bd7a6a8
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748443"
---
# <a name="mrtk"></a>[<span data-ttu-id="5e2ee-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="5e2ee-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="5e2ee-102">MRTK bietet ein [In-Box-Teleportsystem,](/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) das automatisch für artikulierte Hände und Controller funktioniert.</span><span class="sxs-lookup"><span data-stu-id="5e2ee-102">MRTK provides an in-box [teleport system](/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) which automatically works across articulated hands and controllers.</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="5e2ee-103">XR SDK</span><span class="sxs-lookup"><span data-stu-id="5e2ee-103">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="5e2ee-104">Es wird empfohlen, die Teleportierungsimplementierung des MRTK zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="5e2ee-104">We recommend using MRTK's teleportation implementation.</span></span>
<span data-ttu-id="5e2ee-105">Wenn Sie MRTK nicht verwenden möchten, stellt Unity eine Teleportierungsimplementierung im [XR Interaction Toolkit bereit.](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html)</span><span class="sxs-lookup"><span data-stu-id="5e2ee-105">If you choose not to use MRTK, Unity provides a teleportation implementation in the [XR Interaction Toolkit](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html).</span></span>
<span data-ttu-id="5e2ee-106">Wenn Sie sich dafür entscheiden, Ihre eigene zu implementieren, sollten Sie bedenken, dass Sie die Kamera nicht direkt verschieben können.</span><span class="sxs-lookup"><span data-stu-id="5e2ee-106">If you choose to implement your own, it's good to keep in mind that you can't move the camera directly.</span></span> <span data-ttu-id="5e2ee-107">Aufgrund der Kontrolle von Unity über die Kamera für die Kopfverfolgung müssen Sie der Kamera ein übergeordnetes Element in der Hierarchie zuweisen und stattdessen dieses GameObject verschieben.</span><span class="sxs-lookup"><span data-stu-id="5e2ee-107">Due to Unity's control of the camera for head tracking, you'll need to give the camera a parent in the hierarchy and move that GameObject instead.</span></span> <span data-ttu-id="5e2ee-108">Dies entspricht dem Playspace des MRTK.</span><span class="sxs-lookup"><span data-stu-id="5e2ee-108">This is the equivalent of MRTK's Playspace.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="5e2ee-109">Legacy-WSA</span><span class="sxs-lookup"><span data-stu-id="5e2ee-109">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="5e2ee-110">Es wird empfohlen, die Teleportierungsimplementierung des MRTK zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="5e2ee-110">We recommend using MRTK's teleportation implementation.</span></span>
<span data-ttu-id="5e2ee-111">Wenn Sie sich dafür entscheiden, Ihre eigene zu implementieren, sollten Sie bedenken, dass Sie die Kamera nicht direkt verschieben können.</span><span class="sxs-lookup"><span data-stu-id="5e2ee-111">If you choose to implement your own, it's good to keep in mind that you can't move the camera directly.</span></span> <span data-ttu-id="5e2ee-112">Aufgrund der Kontrolle von Unity über die Kamera für die Kopfverfolgung müssen Sie der Kamera ein übergeordnetes Element in der Hierarchie zuweisen und stattdessen dieses GameObject verschieben.</span><span class="sxs-lookup"><span data-stu-id="5e2ee-112">Due to Unity's control of the camera for head tracking, you'll need to give the camera a parent in the hierarchy and move that GameObject instead.</span></span> <span data-ttu-id="5e2ee-113">Dies entspricht dem Playspace des MRTK.</span><span class="sxs-lookup"><span data-stu-id="5e2ee-113">This is the equivalent of MRTK's Playspace.</span></span>