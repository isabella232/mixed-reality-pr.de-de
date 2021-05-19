---
title: 'Szenensystem: Szenentypen'
description: Dokumentation zu verschiedenen Szenentypen in MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 06bfd1dbad3986044f099510c2de4d36cda50fc0
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144573"
---
# <a name="scene-types"></a>Szenentypen

Szenen wurden in drei Typen unterteilt, und jeder Typ hat eine andere Funktion.

![Szenensystem in der Hierarchie](../images/scene-system/MRTK_SceneSystemEditorSceneHierarchy.PNG)

## <a name="content-scenes"></a>Inhaltsszenen

Dies sind die Szenen, die Sie gewohnt sind. Alle Arten von Inhalten können in ihnen gespeichert werden, und sie können in beliebiger Kombination geladen oder entladen werden.

Inhaltsszenen sind standardmäßig aktiviert. Alle Szenen, die im Array Ihres Profils enthalten sind, können vom Dienst `Content Scenes` geladen/entladen werden.

___

## <a name="manager-scenes"></a>Manager-Szenen

Eine einzelne Szene mit einer erforderlichen MixedRealityToolkit-Instanz. Diese Szene wird zuerst beim Start geladen und bleibt für die Lebensdauer der App geladen. Die Manager-Szene kann auch andere Objekte hosten, die nie zerstört werden sollten. Dies ist die bevorzugte Alternative zu DontDestroyOnLoad.

Um dieses Feature zu aktivieren, `Use Manager Scene` checken Sie Ihr Profil ein, und ziehen Sie ein Szenenobjekt in das `Manager Scene` Feld.

___

## <a name="lighting-scenes"></a>Beleuchtungsszenen

Eine Reihe von Szenen, in denen Beleuchtungsinformationen und Beleuchtungsobjekte gespeichert werden. Es kann immer nur eine geladen werden, und ihre Einstellungen können während der Auslastung für reibungslose Beleuchtungsübergänge kombiniert werden.

Die Beleuchtungseinstellungen von Unity – Umgebungslicht, Skyboxes usw. – können bei verwendung von additivem Laden schwierig zu verwalten sein, da sie an einzelne Szenen gebunden sind und das Überschreibungsverhalten nicht einfach ist. In der Praxis kann dies zu Verwirrung führen, wenn Objekte in Beleuchtungsbedingungen erstellt werden, die zur Laufzeit nicht erhalten werden.

![Szenensystem-Beleuchtungseinstellungen](../images/scene-system/MRTK_SceneSystemLightingSettings.PNG)

Das Szenensystem verwendet Beleuchtungsszenen, um sicherzustellen, dass diese Einstellungen konsistent bleiben, unabhängig davon, welche Szenen geladen oder aktiv sind, sowohl im Bearbeitungsmodus als auch im Wiedergabemodus.

Um dieses Feature zu aktivieren, `Use Lighting Scene` checken Sie Ihr Profil ein, und füllen Sie das `Lighting Scenes` Array auf.

### <a name="cached-lighting-settings"></a>Zwischengespeicherte Beleuchtungseinstellungen

Ihr Profil speichert zwischengespeicherte Kopien der Beleuchtungseinstellungen, die in Ihren Beleuchtungsszenen gespeichert sind. Wenn sich diese Einstellungen in Ihren Beleuchtungsszenen ändern, müssen Sie Ihren Cache aktualisieren, um sicherzustellen, dass die Beleuchtung im Wiedergabemodus erwartungsgemäß angezeigt wird. Ihr Profil zeigt eine Warnung an, wenn es vermutet, dass Ihre zwischengespeicherten Einstellungen veraltet sind. Wenn Sie auf `Update Cached Lighting Settings` klicken, werden die einzelnen Beleuchtungsszenen geladen, ihre Einstellungen extrahiert und dann in Ihrem Profil gespeichert.

![Zwischengespeicherte Beleuchtungseinstellungen des Szenensystems](../images/scene-system/MRTK_SceneSystemCachedLightingSettings.PNG)

### <a name="editor-behavior"></a>Editor-Verhalten

Ein Vorteil der Verwendung von Beleuchtungsszenen besteht darin, zu wissen, dass Ihre Inhalte während der Bearbeitung richtig angezeigt werden. Zu diesem Zweck hält der Szenendienst eine Beleuchtungsszene jederzeit geladen und kopiert die Beleuchtungseinstellungen dieser Szene in die aktuelle aktive Szene.\*

Sie können ändern, welche Beleuchtungsszene geladen wird, indem Sie den Dienstinspektor des Szenensystems [öffnen.](../../configuration/mixed-reality-configuration-guide.md#editor-utilities) Im Bearbeitungsmodus können Sie sofort zwischen Beleuchtungsszenen wechseln. Im Wiedergabemodus können Sie Übergänge in der Vorschau anzeigen.

![Szenensysteminspektor](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)

\**Hinweis: In der Regel bestimmt die aktive Szene Ihre Beleuchtungseinstellungen im Editor. Wir möchten dieses Feature jedoch nicht verwenden, um Beleuchtungseinstellungen zu erzwingen, da die aktive Szene auch dort ist, wo neu erstellte Objekte standardmäßig platziert werden und Beleuchtungsszenen nur Beleuchtungskomponenten enthalten dürfen. Stattdessen werden die Einstellungen der aktuellen Beleuchtungsszene automatisch in die Einstellungen der aktiven Szene kopiert. Beachten Sie, dass dies dazu führt, dass die Beleuchtungseinstellungen Ihrer Inhaltsszene übergeschrieben werden.*
