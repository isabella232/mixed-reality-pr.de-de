---
title: 'Szenensystem: Szenentypen'
description: Dokumentation zu verschiedenen Szenentypen in MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: be34110c693c749535f6bfcd0411ecbd0bafc3bb48ab2392b3635c2e86a4dfb1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203330"
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

![Beleuchtungseinstellungen des Szenensystems](../images/scene-system/MRTK_SceneSystemLightingSettings.PNG)

Das Szenensystem verwendet Beleuchtungsszenen, um sicherzustellen, dass diese Einstellungen unabhängig davon, welche Szenen geladen oder aktiv sind, sowohl im Bearbeitungs- als auch im Wiedergabemodus konsistent bleiben.

Um dieses Feature zu aktivieren, `Use Lighting Scene` checken Sie Ihr Profil ein, und füllen Sie das `Lighting Scenes` Array auf.

### <a name="cached-lighting-settings"></a>Zwischengespeicherte Beleuchtungseinstellungen

In Ihrem Profil werden zwischengespeicherte Kopien der Beleuchtungseinstellungen gespeichert, die in Ihren Beleuchtungsszenen gespeichert sind. Wenn sich diese Einstellungen in Ihren Beleuchtungsszenen ändern, müssen Sie Ihren Cache aktualisieren, um sicherzustellen, dass die Beleuchtung wie erwartet im Wiedergabemodus angezeigt wird. Ihr Profil zeigt eine Warnung an, wenn es vermuten kann, dass Ihre zwischengespeicherten Einstellungen veraltet sind. Wenn Sie `Update Cached Lighting Settings` auf klicken, werden alle Beleuchtungsszenen geladen, ihre Einstellungen extrahiert und dann in Ihrem Profil gespeichert.

![Zwischengespeicherte Beleuchtungseinstellungen des Szenensystems](../images/scene-system/MRTK_SceneSystemCachedLightingSettings.PNG)

### <a name="editor-behavior"></a>Editor-Verhalten

Ein Vorteil der Verwendung von Beleuchtungsszenen besteht in der Kenntnis, dass Ihre Inhalte während der Bearbeitung richtig angezeigt werden. Zu diesem Zweck hält der Szenendienst eine Beleuchtungsszene jederzeit geladen und kopiert die Beleuchtungseinstellungen dieser Szene in die aktuelle aktive Szene.\*

Sie können ändern, welche Beleuchtungsszene geladen wird, indem Sie den Dienstinspektor des [Szenensystems öffnen.](../../configuration/mixed-reality-configuration-guide.md#editor-utilities) Im Bearbeitungsmodus können Sie sofort zwischen Beleuchtungsszenen wechseln. Im Wiedergabemodus können Sie Übergänge in der Vorschau anzeigen.

![Szenensysteminspektor](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)

\**Hinweis: In der Regel bestimmt die aktive Szene Ihre Beleuchtungseinstellungen im Editor. Wir entscheiden uns jedoch dafür, dieses Feature nicht zum Erzwingen von Beleuchtungseinstellungen zu verwenden, da in der aktiven Szene auch neu erstellte Objekte standardmäßig platziert werden und Beleuchtungsszenen nur Beleuchtungskomponenten enthalten dürfen. Stattdessen werden die Einstellungen der aktuellen Beleuchtungsszene automatisch in die Einstellungen der aktiven Szene kopiert. Beachten Sie, dass dies dazu führt, dass die Beleuchtungseinstellungen Ihrer Inhaltsszene übergeschrieben werden.*
