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
# <a name="scene-types"></a><span data-ttu-id="20a1e-104">Szenentypen</span><span class="sxs-lookup"><span data-stu-id="20a1e-104">Scene types</span></span>

<span data-ttu-id="20a1e-105">Szenen wurden in drei Typen unterteilt, und jeder Typ hat eine andere Funktion.</span><span class="sxs-lookup"><span data-stu-id="20a1e-105">Scenes have been divided into three types, and each type has a different function.</span></span>

![Szenensystem in der Hierarchie](../images/scene-system/MRTK_SceneSystemEditorSceneHierarchy.PNG)

## <a name="content-scenes"></a><span data-ttu-id="20a1e-107">Inhaltsszenen</span><span class="sxs-lookup"><span data-stu-id="20a1e-107">Content scenes</span></span>

<span data-ttu-id="20a1e-108">Dies sind die Szenen, die Sie gewohnt sind.</span><span class="sxs-lookup"><span data-stu-id="20a1e-108">These are the scenes you're used to dealing with.</span></span> <span data-ttu-id="20a1e-109">Alle Arten von Inhalten können in ihnen gespeichert werden, und sie können in beliebiger Kombination geladen oder entladen werden.</span><span class="sxs-lookup"><span data-stu-id="20a1e-109">Any kind of content can be stored in them, and they can be loaded or unloaded in any combination.</span></span>

<span data-ttu-id="20a1e-110">Inhaltsszenen sind standardmäßig aktiviert.</span><span class="sxs-lookup"><span data-stu-id="20a1e-110">Content scenes are enabled by default.</span></span> <span data-ttu-id="20a1e-111">Alle Szenen, die im Array Ihres Profils enthalten sind, können vom Dienst `Content Scenes` geladen/entladen werden.</span><span class="sxs-lookup"><span data-stu-id="20a1e-111">Any scenes included in your profile's `Content Scenes` array can be loaded / unloaded by the service.</span></span>

___

## <a name="manager-scenes"></a><span data-ttu-id="20a1e-112">Manager-Szenen</span><span class="sxs-lookup"><span data-stu-id="20a1e-112">Manager scenes</span></span>

<span data-ttu-id="20a1e-113">Eine einzelne Szene mit einer erforderlichen MixedRealityToolkit-Instanz.</span><span class="sxs-lookup"><span data-stu-id="20a1e-113">A single scene with a required MixedRealityToolkit instance.</span></span> <span data-ttu-id="20a1e-114">Diese Szene wird zuerst beim Start geladen und bleibt für die Lebensdauer der App geladen.</span><span class="sxs-lookup"><span data-stu-id="20a1e-114">This scene will be loaded first on launch and will remain loaded for the lifetime of the app.</span></span> <span data-ttu-id="20a1e-115">Die Manager-Szene kann auch andere Objekte hosten, die nie zerstört werden sollten.</span><span class="sxs-lookup"><span data-stu-id="20a1e-115">The manager scene can also host other objects that should never be destroyed.</span></span> <span data-ttu-id="20a1e-116">Dies ist die bevorzugte Alternative zu DontDestroyOnLoad.</span><span class="sxs-lookup"><span data-stu-id="20a1e-116">This is the preferred alternative to DontDestroyOnLoad.</span></span>

<span data-ttu-id="20a1e-117">Um dieses Feature zu aktivieren, `Use Manager Scene` checken Sie Ihr Profil ein, und ziehen Sie ein Szenenobjekt in das `Manager Scene` Feld.</span><span class="sxs-lookup"><span data-stu-id="20a1e-117">To enable this feature, check `Use Manager Scene` in your profile and drag a scene object into the `Manager Scene` field.</span></span>

___

## <a name="lighting-scenes"></a><span data-ttu-id="20a1e-118">Beleuchtungsszenen</span><span class="sxs-lookup"><span data-stu-id="20a1e-118">Lighting scenes</span></span>

<span data-ttu-id="20a1e-119">Eine Reihe von Szenen, in denen Beleuchtungsinformationen und Beleuchtungsobjekte gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="20a1e-119">A set of scenes which store lighting information and lighting objects.</span></span> <span data-ttu-id="20a1e-120">Es kann immer nur eine geladen werden, und ihre Einstellungen können während der Auslastung für reibungslose Beleuchtungsübergänge kombiniert werden.</span><span class="sxs-lookup"><span data-stu-id="20a1e-120">Only one can be loaded at a time, and their settings can be blended during loads for smooth lighting transitions.</span></span>

<span data-ttu-id="20a1e-121">Die Beleuchtungseinstellungen von Unity – Umgebungslicht, Skyboxes usw. – können bei verwendung von additivem Laden schwierig zu verwalten sein, da sie an einzelne Szenen gebunden sind und das Überschreibungsverhalten nicht einfach ist.</span><span class="sxs-lookup"><span data-stu-id="20a1e-121">Unity's lighting settings - ambient light, skyboxes, etc - can be tricky to manage when using additive loading because they're tied to individual scenes and override behavior is not straightforward.</span></span> <span data-ttu-id="20a1e-122">In der Praxis kann dies zu Verwirrung führen, wenn Objekte in Beleuchtungsbedingungen erstellt werden, die zur Laufzeit nicht erhalten werden.</span><span class="sxs-lookup"><span data-stu-id="20a1e-122">In practice this can cause confusion when assets are authored in lighting conditions that don't obtain at runtime.</span></span>

![Szenensystem-Beleuchtungseinstellungen](../images/scene-system/MRTK_SceneSystemLightingSettings.PNG)

<span data-ttu-id="20a1e-124">Das Szenensystem verwendet Beleuchtungsszenen, um sicherzustellen, dass diese Einstellungen konsistent bleiben, unabhängig davon, welche Szenen geladen oder aktiv sind, sowohl im Bearbeitungsmodus als auch im Wiedergabemodus.</span><span class="sxs-lookup"><span data-stu-id="20a1e-124">The Scene System uses lighting scenes to ensure that these settings remain consistent regardless of what scenes are loaded or active, both in edit mode and in play mode.</span></span>

<span data-ttu-id="20a1e-125">Um dieses Feature zu aktivieren, `Use Lighting Scene` checken Sie Ihr Profil ein, und füllen Sie das `Lighting Scenes` Array auf.</span><span class="sxs-lookup"><span data-stu-id="20a1e-125">To enable this feature, check `Use Lighting Scene` in your profile and populate the `Lighting Scenes` array.</span></span>

### <a name="cached-lighting-settings"></a><span data-ttu-id="20a1e-126">Zwischengespeicherte Beleuchtungseinstellungen</span><span class="sxs-lookup"><span data-stu-id="20a1e-126">Cached lighting settings</span></span>

<span data-ttu-id="20a1e-127">Ihr Profil speichert zwischengespeicherte Kopien der Beleuchtungseinstellungen, die in Ihren Beleuchtungsszenen gespeichert sind.</span><span class="sxs-lookup"><span data-stu-id="20a1e-127">Your profile stores cached copies of the lighting settings kept in your lighting scenes.</span></span> <span data-ttu-id="20a1e-128">Wenn sich diese Einstellungen in Ihren Beleuchtungsszenen ändern, müssen Sie Ihren Cache aktualisieren, um sicherzustellen, dass die Beleuchtung im Wiedergabemodus erwartungsgemäß angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="20a1e-128">If those settings change in your lighting scenes, you will need to update your cache to ensure lighting appears as expected in play mode.</span></span> <span data-ttu-id="20a1e-129">Ihr Profil zeigt eine Warnung an, wenn es vermutet, dass Ihre zwischengespeicherten Einstellungen veraltet sind.</span><span class="sxs-lookup"><span data-stu-id="20a1e-129">Your profile will display a warning when it suspects your cached settings are out of date.</span></span> <span data-ttu-id="20a1e-130">Wenn Sie auf `Update Cached Lighting Settings` klicken, werden die einzelnen Beleuchtungsszenen geladen, ihre Einstellungen extrahiert und dann in Ihrem Profil gespeichert.</span><span class="sxs-lookup"><span data-stu-id="20a1e-130">Clicking `Update Cached Lighting Settings` will load each of your lighting scenes, extract their settings, then store them in your profile.</span></span>

![Zwischengespeicherte Beleuchtungseinstellungen des Szenensystems](../images/scene-system/MRTK_SceneSystemCachedLightingSettings.PNG)

### <a name="editor-behavior"></a><span data-ttu-id="20a1e-132">Editor-Verhalten</span><span class="sxs-lookup"><span data-stu-id="20a1e-132">Editor behavior</span></span>

<span data-ttu-id="20a1e-133">Ein Vorteil der Verwendung von Beleuchtungsszenen besteht darin, zu wissen, dass Ihre Inhalte während der Bearbeitung richtig angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="20a1e-133">One benefit of using lighting scenes is knowing your content is lit correctly while editing.</span></span> <span data-ttu-id="20a1e-134">Zu diesem Zweck hält der Szenendienst eine Beleuchtungsszene jederzeit geladen und kopiert die Beleuchtungseinstellungen dieser Szene in die aktuelle aktive Szene.\*</span><span class="sxs-lookup"><span data-stu-id="20a1e-134">To this end, the Scene Service will keep a lighting scene loaded at all times, and will copy that scene's lighting settings to the current active scene.\*</span></span>

<span data-ttu-id="20a1e-135">Sie können ändern, welche Beleuchtungsszene geladen wird, indem Sie den Dienstinspektor des Szenensystems [öffnen.](../../configuration/mixed-reality-configuration-guide.md#editor-utilities)</span><span class="sxs-lookup"><span data-stu-id="20a1e-135">You can change which lighting scene is loaded by opening the Scene System's [service inspector.](../../configuration/mixed-reality-configuration-guide.md#editor-utilities)</span></span> <span data-ttu-id="20a1e-136">Im Bearbeitungsmodus können Sie sofort zwischen Beleuchtungsszenen wechseln.</span><span class="sxs-lookup"><span data-stu-id="20a1e-136">In edit mode you can instantaneously transition between lighting scenes.</span></span> <span data-ttu-id="20a1e-137">Im Wiedergabemodus können Sie Übergänge in der Vorschau anzeigen.</span><span class="sxs-lookup"><span data-stu-id="20a1e-137">In play mode, you can preview transitions.</span></span>

![Szenensysteminspektor](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)

<span data-ttu-id="20a1e-139">\**Hinweis: In der Regel bestimmt die aktive Szene Ihre Beleuchtungseinstellungen im Editor. Wir möchten dieses Feature jedoch nicht verwenden, um Beleuchtungseinstellungen zu erzwingen, da die aktive Szene auch dort ist, wo neu erstellte Objekte standardmäßig platziert werden und Beleuchtungsszenen nur Beleuchtungskomponenten enthalten dürfen. Stattdessen werden die Einstellungen der aktuellen Beleuchtungsszene automatisch in die Einstellungen der aktiven Szene kopiert. Beachten Sie, dass dies dazu führt, dass die Beleuchtungseinstellungen Ihrer Inhaltsszene übergeschrieben werden.*</span><span class="sxs-lookup"><span data-stu-id="20a1e-139">\**Note: Typically the active scene determines your lighting settings in editor. However we choose not to use this feature to enforce lighting settings, because the active scene is also where newly created objects are placed by default, and lighting scenes are only permitted to contain lighting components. Instead, the current lighting scene's settings are automatically copied to the active scene's settings instead. Keep in mind that this will result in your content scene's lighting settings being over-written.*</span></span>
