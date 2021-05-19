---
title: Übersicht über den Hand physics-Dienst
description: Dokumentation zur Verwendung des Hand-Physics-Erweiterungsdiensts in MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 751aec148d3a40da4728d2fdd60a60402b59a4de
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145082"
---
# <a name="hand-physics-extension-service"></a>Hand physikalischer Erweiterungsdienst

![Hand Physics Extension Service](../images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)

Der Hand physikalischer Dienst ermöglicht feste Körperkollisionsereignisse und Interaktionen mit artikulierten Händen.

## <a name="enabling-the-extension"></a>Aktivieren der Erweiterung

Um die Erweiterung zu aktivieren, öffnen Sie Ihr RegisteredServiceProvider-Profil. Klicken `Register a new Service Provider` Sie auf diese Schaltfläche, um eine neue Konfiguration hinzuzufügen. Wählen Sie im Feld Komponententyp die Option HandPhysicsService aus. Wählen Sie im Feld Konfigurationsprofil das standardmäßige Hand-Physics-Profil aus, das in der Erweiterung enthalten ist.

## <a name="profile-options"></a>Profiloptionen

### <a name="hand-physics-layer"></a>Hand physics layer (Hand-Physik-Schicht)

Steuert die Ebene, zu der die instanziierten Handgelenke wechseln.

Während der Dienst standardmäßig auf die "Standardebene" (0) festgelegt ist, wird empfohlen, eine separate Ebene für Handkörperobjekte zu verwenden. Andernfalls kann es zu unerwünschten Kollisionen und/oder ungenauen Raycasts gekommen sein.

### <a name="finger-tip-kinematic-body-prefab"></a>Kinematisches Körper-Prefab für Fingerspitzen

Steuert, welches Prefab an Fingerspitzen instanziiert wird. Damit der Dienst wie erwartet funktioniert, erfordert das Prefab:

- Eine Festkörperkomponente, bei der isKinematic aktiviert ist
- Ein Collider
- `JointKinematicBody`-Komponente

### <a name="use-palm-kinematic-body"></a>Verwenden des kinematischen Handflächenkörpers

Steuert, ob der Dienst versucht, ein Prefab auf der Handfläche zu instanziieren.

### <a name="palm-kinematic-body-prefab"></a>Wad kinematic body prefab

Wenn `UsePalmKinematicBody` aktiviert ist, ist dies das Prefab, das instanziiert wird. Genau wie `FingerTipKinematicBodyPrefab` erfordert dieses Prefab:

- Eine starre Komponente, bei der isKinematic aktiviert ist
- Ein Collider
- `JointKinematicBody`-Komponente

## <a name="how-to-use-the-service"></a>Verwenden des Diensts

Verwenden Sie nach der Aktivierung die -Eigenschaft eines Colliders, `IsTrigger` um Kollisionsereignisse von allen 10 Ziffern (und Handflächen, wenn sie aktiviert sind) zu empfangen.
