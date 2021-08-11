---
title: Handphysikdienst
description: Dokumentation zur Verwendung des Erweiterungsdiensts "Hand physics" im MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: f54f8dabddba03bc279a090bf1c62b25656e64109b3b5671a4ed50d070445f14
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221726"
---
# <a name="hand-physics-service"></a>Handphysikdienst

![Hand Physics Extension Service](../images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)

Der Hand-Physikalische Dienst ermöglicht feste Körperkollisionsereignisse und Interaktionen mit artikulierten Händen.

## <a name="enabling-the-extension"></a>Aktivieren der Erweiterung

Um die Erweiterung zu aktivieren, öffnen Sie Ihr RegisteredServiceProvider-Profil. Klicken Sie `Register a new Service Provider` auf diese Schaltfläche, um eine neue Konfiguration hinzuzufügen. Wählen Sie im Feld Komponententyp die Option HandPhysicsService aus. Wählen Sie im Feld Konfigurationsprofil das in der Erweiterung enthaltene Standardprofil für die Handmechanik aus.

## <a name="profile-options"></a>Profiloptionen

### <a name="hand-physics-layer"></a>Hand-Physikalische Schicht

Steuert die Ebene, zu der die instanziierten Handverbindungen gelangen.

Während der Dienst standardmäßig die "Standardebene" (0) verwendet, wird empfohlen, eine separate Ebene für Objekte der Handmechanik zu verwenden. Andernfalls kann es zu unerwünschten Kollisionen und/oder ungenauen Raycasts kommen.

### <a name="finger-tip-kinematic-body-prefab"></a>Finger tip kinematic body prefab

Steuert, welches Prefab auf Fingerspitzen instanziiert wird. Damit der Dienst wie erwartet funktioniert, erfordert das Prefab Folgendes:

- Eine starre Komponente, bei der isKinematic aktiviert ist
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

Verwenden Sie nach der Aktivierung die -Eigenschaft eines beliebigen Colliders, `IsTrigger` um Kollisionsereignisse von allen 10 Ziffern (und Handflächen, wenn sie aktiviert sind) zu empfangen.
