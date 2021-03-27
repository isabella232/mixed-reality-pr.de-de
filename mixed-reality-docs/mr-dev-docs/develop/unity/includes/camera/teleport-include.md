---
ms.openlocfilehash: daf81bcd6ce215d908ce6b4028effcdc2ed38328
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636371"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Mrtk bietet ein in-Box- [teleportsystem](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/teleport-system/teleport-system) , das automatisch über Handgelenke und Controller hinweg funktioniert.

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Es wird empfohlen, die-Implementierung von mrtk zu verwenden.
Wenn Sie mrtk nicht verwenden möchten, stellt Unity im [XR-Interaktions Toolkit](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@1.0/manual/locomotion.html)eine Teleportations-Implementierung bereit.
Wenn Sie sich für die Implementierung Ihrer eigenen entscheiden, sollten Sie Bedenken, dass Sie die Kamera nicht direkt verschieben können. Aufgrund der Unity-Kontrolle der Kamera für die Head-Nachverfolgung müssen Sie der Kamera ein übergeordnetes Element in der Hierarchie übergeben und stattdessen das gameobject verschieben. Dies entspricht dem Playspace von mrtk.

# <a name="legacy-wsa"></a>[Legacy-WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Es wird empfohlen, die-Implementierung von mrtk zu verwenden.
Wenn Sie sich für die Implementierung Ihrer eigenen entscheiden, sollten Sie Bedenken, dass Sie die Kamera nicht direkt verschieben können. Aufgrund der Unity-Kontrolle der Kamera für die Head-Nachverfolgung müssen Sie der Kamera ein übergeordnetes Element in der Hierarchie übergeben und stattdessen das gameobject verschieben. Dies entspricht dem Playspace von mrtk.