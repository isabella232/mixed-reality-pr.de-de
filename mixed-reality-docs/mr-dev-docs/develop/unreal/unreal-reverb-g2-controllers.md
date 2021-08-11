---
title: HP Reverb G2-Controller in Unreal
description: Erfahren Sie, wie Sie die neuen HP Reverb G2-Controller in OpenXR und SteamVR für Unreal Mixed Reality-Anwendungen verwenden.
author: hferrone
ms.author: jacksonf
ms.date: 10/9/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, Reverb, Reverb G2, HP Reverb G2, Mixed Reality, Entwicklung, Motion Controller, Benutzereingabe, Features, neues Projekt, Emulator, Dokumentation, Leitfäden, Features, Hologramme, Spieleentwicklung, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: b287a5c7de1ea086b76228d9109cc07a4e1569f5f926cb42dc3e37cc2a3bb916
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115204208"
---
# <a name="hp-reverb-g2-controllers-in-unreal"></a>HP Reverb G2-Controller in Unreal 

## <a name="getting-started"></a>Erste Schritte

> [!IMPORTANT]
> Unreal Engine 4.26 und entweder OpenXR oder SteamVR sind für den Zugriff auf das HP Motion Controller-Plug-In erforderlich, das Sie für die Arbeit mit den HP Reverb G2-Controllern benötigen.

[!INCLUDE[](includes/tabs-g2-controllers-in-unreal.md)]

## <a name="porting-an-existing-openxr-app"></a>Portieren einer vorhandenen OpenXR-App 

Wenn für den HP Mixed Reality Controller keine Controllerbindungen vorhanden sind, versucht die OpenXR-Runtime, vorhandene Bindungen dem aktiven Controller neu zuzuordnungen.  In diesem Fall verfügt das Spiel über Oculus Touch-Bindungen und keine HP Mixed Reality Controller-Bindungen.

![Neuverbinden vorhandener Bindungen, wenn keine Controllerbindungen vorhanden sind](images/reverb-g2-img-04.png)

Die Ereignisse werden weiterhin angezeigt, aber wenn das Spiel controllerspezifische Bindungen wie die rechte Menüschaltfläche verwenden muss, muss das HP Mixed Reality-Interaktionsprofil verwendet werden.  Es können mehrere Controllerbindungen pro Aktion angegeben werden, um verschiedene Geräte besser zu unterstützen.
   
![Verwenden mehrerer Controllerbindungen](images/reverb-g2-img-05.png)

## <a name="adding-input-action-mappings"></a>Hinzufügen von Eingabeaktionszuordnungen 

Definieren Sie eine neue Aktion, und ordnen Sie sie einem der Tastendrucker im Abschnitt HP Mixed Reality Controller zu.

![Definieren neuer Aktionen und Zuordnungen](images/reverb-g2-img-02.png)

Der HP Reverb G2-Controller verfügt auch über einen analogen Regler, der in den Achsenzuordnungen mit der Bindung "Achsenachse" verwendet werden kann.  Es gibt eine separate Binding -Bindung, die für Aktionszuordnungen verwendet werden sollte, wenn die Greiftaste vollständig gedrückt ist. 

![Verwenden der Achsenbindungen "Axis"](images/reverb-g2-img-03.png)

## <a name="adding-input-events"></a>Hinzufügen von Eingabeereignissen

Klicken Sie mit der rechten Maustaste auf eine Blaupause, und suchen Sie nach den neuen Aktionsnamen aus dem Eingabesystem, um Ereignisse für diese Aktionen hinzuzufügen.  Hier reagiert die Blaupause auf die Ereignisse mit einer Druckzeichenfolge, die den aktuellen Schaltflächen- und Achsenstatus ausgibt.

![Blaupause, die auf Ereignisse reagiert und den aktuellen Schaltflächen- und Achsenstatus aus gibt](images/reverb-g2-img-06.png)

### <a name="using-input"></a>Verwenden der Eingabe 

[!INCLUDE[](includes/tabs-g2-controller-mapping-in-unreal.md)]

## <a name="see-also"></a>Siehe auch
* [SteamVR-Eingabe](https://docs.unrealengine.com/Platforms/VR/SteamVR/HowTo/SteamVRInput/index.html)
* [Verwenden von SteamVR mit Windows Mixed Reality](/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)
* [Unreal Player Camera](https://docs.unrealengine.com/Programming/Tutorials/PlayerCamera/3/index.html)