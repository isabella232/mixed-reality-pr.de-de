---
title: Hand Physics Extension Service
description: description Hand Physics-Erweiterungsdienste.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 401a9d31ed3fbbe0c3e02cb95ffebb024f882fd9
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143438"
---
# <a name="hand-physics-extension-services"></a>Hand-Physikalische Erweiterungsdienste

Der Hand-Physikalische Dienst ermöglicht feste Körperkollisionsereignisse und Interaktionen mit artikulierten Händen.

## <a name="getting-started-with-hand-physics-extension-service"></a>Erste Schritte mit dem Erweiterungsdienst für die Handmechanik

Fügen Sie der Liste der Erweiterungsdienste den Hand-Physikalischen Dienst hinzu, und verwenden Sie das Standardprofil.

Verwenden Sie nach der Aktivierung die IsTrigger-Eigenschaft eines Colliders, um Kollisionsereignisse von allen 10 Ziffern (und Handflächen, wenn sie aktiviert sind) zu empfangen.

### <a name="prerequisites"></a>Voraussetzungen

- Aktivieren des Erweiterungsdiensts
- Weisen Sie dem Finger/Handflächen-Fugen ein geeignetes Prefab zu.

## <a name="recommendations"></a>Empfehlungen

Der Dienst verwendet standardmäßig die Standardebene, es wird jedoch empfohlen, eine separate Ebene für HandPhysics-Objekte zu verwenden. Andernfalls kann es zu unerwünschten Kollisionen und/oder ungenauen Raycasts kommen.
