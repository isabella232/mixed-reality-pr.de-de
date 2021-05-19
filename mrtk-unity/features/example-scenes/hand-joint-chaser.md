---
title: Handgelenksverfolgung
description: Hand-Joint-Verfolger in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: f9db1c4a2ca1959a35c541e87c9a4a01bc41637e
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144624"
---
# <a name="hand-joint-chaser-example"></a>Beispiel für Hand-Fugen-Verfolger

![Hand-Joint-Verfolger In dieser Beispielszene wird veranschaulicht, wie Solver verwendet wird, um Objekte ](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) an die Handgelenke zu anfügen.

## <a name="example-scene"></a>Beispielszene

Sie finden die Beispielszene **HandJointChaserExample-Szene** im `Assets/MRTK/Examples` Ordner unter `Demos/Input/Scenes/` .

## <a name="solver-handler"></a>Solver-Handler

Klicken Sie **auf Nachverfolgte Objekte, auf die verwiesen werden soll,** und wählen Sie **Hand joint left oder** Hand Joint Right **aus.** Die Dropdownliste **Tracked Hand Joint (Tracked Hand Joint) wird** angezeigt. In der Dropdownliste können Sie ein bestimmtes nachverfolgungsspezifisches Joint auswählen. In dieser Beispielszene wird der Radial View Solver verwendet, damit ein Objekt dem Zielobjekt folgt. Weitere Informationen finden Sie auf der Seite [Solver.](../ux-building-blocks/solvers/solver.md)

![Hand-Joint-Solver](../images/hand-joint-chaser/MRTK_Solver_HandJoint.jpg)
