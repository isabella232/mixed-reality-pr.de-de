---
title: HP-Reverb-G2-Controller in Unreal
description: Erfahren Sie, wie Sie die neuen HP-Hall-G2-Controller in openxr und steamvr für Unreal Mixed Reality-Anwendungen verwenden.
author: hferrone
ms.author: jacksonf
ms.date: 10/9/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, Reverb, Reverb G2, HP-Simulator G2, gemischte Realität, Entwicklung, Bewegungs Controller, Benutzereingaben, Features, neues Projekt, Emulator, Dokumentation, Handbücher, Features, holograms, Spieleentwicklung, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 006c70208ec0eaa45447caecf39f799c4be1bfeb
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582686"
---
# <a name="hp-reverb-g2-controllers-in-unreal"></a>HP-Reverb-G2-Controller in Unreal 

## <a name="getting-started"></a>Erste Schritte

> [!IMPORTANT]
> Unreal Engine 4,26 und openxr oder steamvr sind für den Zugriff auf das HP Motion Controller-Plug-in erforderlich, um mit den HP-Reverb-Controllern arbeiten zu können.

[!INCLUDE[](includes/tabs-g2-controllers-in-unreal.md)]

## <a name="porting-an-existing-openxr-app"></a>Portieren einer vorhandenen openxr-App 

Wenn im Spiel für den HP Mixed Reality-Controller keine Controller Bindungen vorhanden sind, versucht die openxr-Laufzeit, vorhandene Bindungen dem aktiven Controller zuzuordnen.  In diesem Fall verfügt das Spiel über eine Oculus-Berührungs Bindung und keine HP Mixed Reality Controller-Bindungen.

![Neuzuordnen vorhandener Bindungen, wenn keine Controller Bindungen vorhanden sind](images/reverb-g2-img-04.png)

Die Ereignisse werden weiterhin ausgelöst, aber wenn das Spielcontroller spezifische Bindungen verwenden muss, wie die Rechte Menü Schaltfläche, muss das HP Mixed Reality-Interaktions Profil verwendet werden.  Mehrere Controller Bindungen können pro Aktion angegeben werden, um unterschiedliche Geräte besser zu unterstützen.
   
![Verwenden mehrerer Controller Bindungen](images/reverb-g2-img-05.png)

## <a name="adding-input-action-mappings"></a>Hinzufügen von Eingabe Aktions Zuordnungen 

Definieren Sie eine neue Aktion, und ordnen Sie Sie einem der Tastendruck im HP Mixed Reality Controller-Abschnitt zu.

![Definieren neuer Aktionen und Zuordnungen](images/reverb-g2-img-02.png)

Der HP-Reverb-G2-Controller verfügt auch über einen analogen Zieh Punkt, der in den Achsen Zuordnungen mit der Bindung "Achsen Achse" verwendet werden kann.  Es gibt eine separate Press-Bindung, die für Aktions Zuordnungen verwendet werden sollte, wenn die Zieh Fläche gedrückt wird. 

![Verwenden der Zuordnungs Achsen Bindungen](images/reverb-g2-img-03.png)

## <a name="adding-input-events"></a>Hinzufügen von Eingabe Ereignissen

Klicken Sie mit der rechten Maustaste auf einen Blueprint, und suchen Sie im Eingabe System nach den neuen Aktions Namen, um Ereignisse für diese Aktionen hinzuzufügen.  Hier antwortet der Blueprint auf die Ereignisse mit einer Druck Zeichenfolge, die die aktuelle Schaltfläche und den Achsen Zustand ausstellt.

![Blaupause, die auf Ereignisse reagiert und den aktuellen Schaltflächen-und Achsen Zustand ausstellt](images/reverb-g2-img-06.png)

### <a name="using-input"></a>Verwenden von Eingaben 

[!INCLUDE[](includes/tabs-g2-controller-mapping-in-unreal.md)]

## <a name="see-also"></a>Weitere Informationen
* [Steamvr-Eingabe](https://docs.unrealengine.com/Platforms/VR/SteamVR/HowTo/SteamVRInput/index.html)
* [Verwenden von "steamvr" mit Windows Mixed Reality](/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)
* [Unreal Player Kamera](https://docs.unrealengine.com/Programming/Tutorials/PlayerCamera/3/index.html)