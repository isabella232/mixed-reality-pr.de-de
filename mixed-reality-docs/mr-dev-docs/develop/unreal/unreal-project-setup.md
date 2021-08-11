---
title: Einrichten Ihres Unreal-Projekts
description: Erfahren Sie, wie Sie Ihr Projekt mit der neuesten Version der Unreal-Engine und dem Mixed Reality-Featuretool einrichten.
author: hferrone
ms.author: v-hferrone
ms.date: 4/28/2021
ms.topic: tutorial
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, Mixed Reality, Entwicklung, Features, neues Projekt, Emulator, Dokumentation, Leitfäden, Hologramme, Spieleentwicklung, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 546dcbac09600402b50408e016507b4d15fac22c58be8c1b3d68331dc5320252
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115225406"
---
# <a name="setting-up-your-unreal-project"></a>Einrichten Ihres Unreal-Projekts

Es wird empfohlen, die [Unreal-Engine, Version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) oder höher, zu installieren, um die integrierte Unterstützung von HoloLens in vollem Umfang nutzen zu können.

Wechseln Sie im Epic Games-Startprogramm zur Registerkarte **Bibliothek**, klicken Sie neben **Starten** auf den Dropdownpfeil und dann auf **Optionen**. Wählen Sie unter **Target Platforms** (Zielplattformen) **HoloLens 2** aus, und klicken Sie auf **Apply** (Übernehmen).
![HoloLens 2-Installationsoption für Unreal](../images/Unreal_Install_Option_HoloLens2.png)

## <a name="import-mixed-reality-toolkit-for-unreal"></a>Importieren des Mixed Reality-Toolkits für Unreal

![MRTK](../../design/images/MRTK_UX_Hero.png)

Mixed Reality Toolkit (MRTK) ist ein plattformübergreifendes Open Source-Entwicklungskit für Mixed Reality-Anwendungen. MRTK bietet ein plattformübergreifendes Eingabesystem, Grundlagenkomponenten und gemeinsame Bausteine für räumliche Interaktionen. Das Toolkit soll die Entwicklung von Anwendungen für Microsoft HoloLens, für immersive Windows Mixed Reality-Headsets (VR) und für die OpenVR-Plattform beschleunigen.

Für die Installation empfehlen wir, den Abschnitt [Erste Schritte](unreal-development-overview.md#1-getting-started) Ihrer zusammengestellten [Unreal-Entwicklungsreise](unreal-development-overview.md) auszuführen. Wenn Sie sich bereits auf der Unreal-Entwicklungsreise befinden, beenden Sie die unten aufgelisteten restlichen Setupschritte, und fahren sie mit den [HoloLens 2-Einstiegstutorials](tutorials/unreal-uxt-ch1.md) fort.

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity-Logobild](../images/MRTK-Unreal-Banner.png)<br>**Mixed Reality Toolkit-Unreal (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> Wenn Sie MRTK für Unreal nicht verwenden möchten, müssen Sie für alle Interaktionen und Verhaltensweisen selber Skripts erstellen.