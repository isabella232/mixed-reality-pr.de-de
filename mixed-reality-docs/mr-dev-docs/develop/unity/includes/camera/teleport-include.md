---
ms.openlocfilehash: 0a4f6f1262bcaa69a8755223d738bbd88bd7a6a8
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748443"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK bietet ein [In-Box-Teleportsystem,](/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) das automatisch für artikulierte Hände und Controller funktioniert.

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Es wird empfohlen, die Teleportierungsimplementierung des MRTK zu verwenden.
Wenn Sie MRTK nicht verwenden möchten, stellt Unity eine Teleportierungsimplementierung im [XR Interaction Toolkit bereit.](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html)
Wenn Sie sich dafür entscheiden, Ihre eigene zu implementieren, sollten Sie bedenken, dass Sie die Kamera nicht direkt verschieben können. Aufgrund der Kontrolle von Unity über die Kamera für die Kopfverfolgung müssen Sie der Kamera ein übergeordnetes Element in der Hierarchie zuweisen und stattdessen dieses GameObject verschieben. Dies entspricht dem Playspace des MRTK.

# <a name="legacy-wsa"></a>[Legacy-WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Es wird empfohlen, die Teleportierungsimplementierung des MRTK zu verwenden.
Wenn Sie sich dafür entscheiden, Ihre eigene zu implementieren, sollten Sie bedenken, dass Sie die Kamera nicht direkt verschieben können. Aufgrund der Kontrolle von Unity über die Kamera für die Kopfverfolgung müssen Sie der Kamera ein übergeordnetes Element in der Hierarchie zuweisen und stattdessen dieses GameObject verschieben. Dies entspricht dem Playspace des MRTK.