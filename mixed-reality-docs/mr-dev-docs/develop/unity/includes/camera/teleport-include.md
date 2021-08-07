---
ms.openlocfilehash: 879d8083f832e716389e4b4598aa0fffe6930ff1c06d7a07fe9e4dacc98e7937
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212313"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK bietet ein [in-box-Teleportsystem, das](/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) automatisch über artikulierte Hände und Controller hinweg funktioniert.

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Es wird empfohlen, die Teleportierungsimplementierung von MRTK zu verwenden.
Wenn Sie mrtk nicht verwenden möchten, stellt Unity eine Teleportierungsimplementierung im [XR Interaction Toolkit bereit.](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html)
Wenn Sie ihre eigene implementieren möchten, sollten Sie bedenken, dass Sie die Kamera nicht direkt verschieben können. Aufgrund der Steuerung der Kamera durch Unity für die Kopfverfolgung müssen Sie der Kamera ein übergeordnetes Element in der Hierarchie geben und stattdessen dieses GameObject verschieben. Dies entspricht dem Playspace des MRTK.

# <a name="legacy-wsa"></a>[Legacy-WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Es wird empfohlen, die Teleportierungsimplementierung von MRTK zu verwenden.
Wenn Sie ihre eigene implementieren möchten, sollten Sie bedenken, dass Sie die Kamera nicht direkt verschieben können. Aufgrund der Steuerung der Kamera durch Unity für die Kopfverfolgung müssen Sie der Kamera ein übergeordnetes Element in der Hierarchie geben und stattdessen dieses GameObject verschieben. Dies entspricht dem Playspace des MRTK.