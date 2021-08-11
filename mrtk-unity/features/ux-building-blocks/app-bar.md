---
title: App-Leiste
description: Übersicht über die App-Leiste im MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, App-Leiste,
ms.openlocfilehash: 1ecb43d25a4353ff4c3bd8350efaab877900a5b979cd42d2c8d1cb91ce32ae0c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198274"
---
# <a name="app-bar"></a>App-Leiste

![App-Leiste](../images/app-bar/MRTK_AppBar_Main.png)

Die App-Leiste ist eine Benutzeroberflächenkomponente, die zusammen mit dem [Steuerelementskript für Begrenzungen verwendet](bounds-control.md) wird. Sie fügt einem Objekt Schaltflächensteuerelemente mit der Absicht hinzu, es zu bearbeiten. Mithilfe der Schaltfläche "Anpassen" kann die Begrenzungssteuerschnittstelle für ein Objekt de-/activated werden. Die Schaltfläche "Entfernen" sollte das Objekt aus der Szene entfernen.

## <a name="how-to-use-app-bar"></a>Verwenden der App-Leiste

Ziehen Sie `AppBar` (Assets/MRTK/SDK/Features/UX/Prefabs/AppBar/AppBar.prefab) in die Szenenhierarchie. Weisen Sie im Inspektorbereich der Komponente ein beliebiges  Objekt mit einem Begrenzungssteuerelement als Zielgrenze zu, um die App-Leiste hinzuzufügen.

**Wichtig:** Die Aktivierungsoption für die Begrenzungssteuerung für das Zielobjekt sollte "Manuell aktivieren" sein.

<img src="../images/app-bar/MRTK_AppBar_Setup1.png" width="450" alt="Setup 1">

<img src="../images/app-bar/MRTK_AppBar_Setup2.png" width="450" alt="Set up 2">
