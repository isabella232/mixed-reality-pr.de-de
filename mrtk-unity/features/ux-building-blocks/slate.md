---
title: Filmklappe
description: Dokumentation zu Slate in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Slate,
ms.openlocfilehash: 6bc1f18c71367ce05aadae0ff3f8aa51fd17d10c943022525fc5043d8d7989a2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224024"
---
# <a name="slate"></a>Filmklappe

![Filmklappe](../images/slate/MRTK_Slate_Main.png)

Das Slate-Prefab bietet ein schlankes Fensterformat-Steuerelement zum Anzeigen von 2D-Inhalten, z. B. Nur-Text oder Artikel einschließlich Medien. Sie bietet eine fähige Titelleiste sowie die Funktionen *Follow Me* und *Close.* Das Inhaltsfenster kann über eine artikulierte Handeingabe gescrollt werden.

## <a name="how-to-use-a-slate-control"></a>Verwenden eines Slate-Steuerelements

Ein Slate-Steuerelement besteht aus den folgenden Elementen:

* **TitleBar:** Die gesamte Titelleiste auf der Schieferleiste.
* **Titel:** Der Titelbereich auf der linken Seite der Titelleiste.
* **Schaltflächen:** Der Schaltflächenbereich auf der rechten Seite der Titelleiste.
* **BackPlate:** Die Rückseite der Schiefer.
* **ContentQuad:** Inhalt wird als Material zugewiesen. Im Beispiel wird das Beispielmaterial "PanContent" verwendet.

<img src="../images/slate/MRTK_SlateStructure.jpg" width="650" alt="Slate Structure in the Unity editor">

## <a name="bounds-control"></a>Begrenzungssteuerelement

Ein Slate-Steuerelement enthält ein Begrenzungssteuerelementskript zum Skalieren und Rotieren. Weitere Informationen zum Begrenzungssteuerelement finden Sie auf der Seite [begrenzungssteuerelement.](bounds-control.md)

<img src="../images/slate/MRTK_Slate_BB.jpg" width="650" alt="Slate BB">

## <a name="buttons"></a>Schaltflächen

Eine Standardslate bietet oben rechts auf der Titelleiste standardmäßig zwei Schaltflächen:

* **Folgen Sie mir:** Schaltet eine Orbital-Solverkomponente um, damit das Slate-Objekt dem Benutzer folgt.
* **Schließen:** Deaktiviert das Slate-Objekt.

<img src="../images/slate/MRTK_Slate_Buttons.jpg" width="650" alt="Slate Button">

## <a name="scripts"></a>Skripts

Im Allgemeinen muss das `NearInteractionTouchable.cs` Skript an jedes Objekt angefügt werden, das touch-Ereignisse von empfangen `IMixedRealityTouchHandler` soll.

<img src="../images/slate/MRTK_Slate_Scripts.png" alt="Slate Structure">

* `HandInteractionPan.cs` Dieses Skript verarbeitet die artikulierten Handeingaben zum Berühren und Verschieben des Inhalts auf *contentQuad* des Schiefers.

* `HandInteractionPanZoom.cs`: Zusätzlich zur Schwenkinteraktion unterstützt dieses Skript das zweihändige Zoomen.

<img src="../images/slate/MRTK_Slate_PanZoom.png" width="500" alt="Slate Pan Zooming">
