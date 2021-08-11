---
title: Shader-Updatetool
description: Dokumentation zum Aktualisieren von MRTK-Standard-Shadern
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 9ed8a1e439b2bf911d8144a90259d99bf38b12e0404d9ad3365152bed633042c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197068"
---
# <a name="updating-shaders"></a>Aktualisieren von Shadern

Ab Version 2.6.0 werden die MRTK-Shader über das MRTK versioniert. Shaders.sentinel-Datei. Beim Upgrade auf eine neue Version von MRTK wird möglicherweise die folgende Meldung angezeigt.

![Aufforderung zum Aktualisieren von Shadern](../images/tools/UpdateShaderPrompt.png)

Wenn **Sie Ja** auswählen, wird MRTK angewiesen, den Inhalt von   >  **Assets-MRTK-Shadern** mit der neuesten Version zu überschreiben.  >   Wenn **Sie Nein** auswählen, werden die aktuellen Dateien beibehalten. **Ignore** erstellt eine Datei ( `IgnoreUpdateCheck.sentinel` ) in **Assets**  >  **MRTK**  >  **Shader ,** die zukünftige Shaderupdateüberprüfungen unterdrücken.

> [!IMPORTANT]
> Beim Überschreiben der Shaderdateien geht jede benutzerdefinierte Änderung verloren. Stellen Sie sicher, dass Sie alle geänderten Shaderdateien sichern, bevor Sie ein Upgrade durchführen.
>
> Wenn das Projekt für die Verwendung der Universal Render Pipeline (URP) – ehemals Lightweight Render Pipeline (LWRP) konfiguriert wurde, führen Sie **Mixed Reality** > **Toolkit** > **Utilities** >
>  **Upgrade MRTK Standard Shader for Lightweight Render Pipeline (MRTK-Standard-Shader für Lightweight-Renderpipeline)** erneut aus.

Unter ist es auch möglich, jederzeit mit **Mixed Reality**  >  **Toolkit**  >  **Utilities**  >  **Check for Shader Updates (Suchen nach Shaderupdates)** auf der Menüleiste des Unity-Editors nach Shaderupdates zu suchen.

![Suchen nach Shaderupdates](../images/tools/ShaderUpdateMenu.png)

**Bei der Überprüfung auf Shaderupdates** wird die Datei ignoriert, und die `IgnoreUpdateCheck.sentinel` Aktualisierung des bedarfsbasierten Shaders wird ermöglicht.

> [!NOTE]
> Beim Importieren der MRTK-UNITYPACKAGE-Dateien ist keine Überprüfung auf Shaderupdates erforderlich.
