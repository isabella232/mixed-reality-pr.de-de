---
title: Handgelenksverfolgung
description: Hand-Joint-Verfolger im MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 376dcd0e1ff01d6e9020aedf35ed2bb2b7b39fa8a119d125aa8c3a96bf0024fe
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189562"
---
# <a name="hand-joint-chaser"></a>Handgelenksverfolgung

![Hand-Joint-Verfolger ](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) In dieser Beispielszene wird veranschaulicht, wie Sie solver verwenden, um Objekte an die Handverbindungen anzufügen.

## <a name="example-scene"></a>Beispielszene

Sie finden die Beispielszene **HandJointChaserExample-Szene** im `Assets/MRTK/Examples` Ordner unter `Demos/Input/Scenes/` .

## <a name="solver-handler"></a>Solverhandler

Klicken Sie auf **Nachverfolgtes Objekt, auf das verwiesen werden soll,** und wählen Sie **Hand Joint Left** oder Hand Joint **Right** aus. Die Dropdown-Dropdown-Seite **Tracked Hand Joint (Nachverfolgte Handverbindungen)** wird angezeigt. In der Dropdownliste können Sie bestimmte gemeinsame Verbindungen auswählen, die nachverfolgt werden sollen. In dieser Beispielszene wird der Radial View Solver verwendet, damit ein Objekt dem Zielobjekt folgt. Weitere Informationen finden Sie auf der Seite ["Solver".](../ux-building-blocks/solvers/solver.md)

![Hand-Gemeinsam-Solver](../images/hand-joint-chaser/MRTK_Solver_HandJoint.jpg)
