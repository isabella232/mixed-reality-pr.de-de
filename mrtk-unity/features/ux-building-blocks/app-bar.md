---
title: App-Leiste
description: Übersicht über die App-Leiste im MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, App-Leiste,
ms.openlocfilehash: 3c8633d91b2c26f8bdc774a98b2cb48ffb276720
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175688"
---
# <a name="app-bar"></a>App-Leiste

![App-Leiste](../images/app-bar/MRTK_AppBar_Main.png)

Die App-Leiste ist eine Benutzeroberflächenkomponente, die zusammen mit dem [Steuerelementskript für Begrenzungen verwendet](bounds-control.md) wird. Es fügt einem Objekt Schaltflächensteuerelemente mit der Absicht hinzu, es zu bearbeiten. Mithilfe der Schaltfläche "Anpassen" kann die Begrenzungssteuerschnittstelle für ein Objekt de-/activated werden. Die Schaltfläche "Entfernen" sollte das Objekt aus der Szene entfernen.

## <a name="how-to-use-app-bar"></a>Verwenden der App-Leiste

Ziehen Sie `AppBar` (Assets/MRTK/SDK/Features/UX/Prefabs/AppBar/AppBar.prefab) in die Szenenhierarchie. Weisen Sie im Inspektorbereich der Komponente ein beliebiges  Objekt mit einem Begrenzungssteuerelement als Zielgrenze zu, um die App-Leiste hinzuzufügen.

**Wichtig:** Die Aktivierungsoption für die Begrenzungssteuerung für das Zielobjekt sollte "Manuell aktivieren" sein.

<img src="../images/app-bar/MRTK_AppBar_Setup1.png" width="450" alt="Setup 1">

<img src="../images/app-bar/MRTK_AppBar_Setup2.png" width="450" alt="Set up 2">
