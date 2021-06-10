---
title: Shader-Updatetool
description: Dokumentation zum Aktualisieren von MRTK-Standard-Shadern
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 1f943d8ac7050b8607ae3a85af0a377a7460eb3b
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647100"
---
# <a name="updating-shaders"></a>Aktualisieren von Shadern

Ab Version 2.6.0 werden die MRTK-Shader über das MRTK versioniert. Shaders.sentinel-Datei. Beim Upgrade auf eine neue Version von MRTK wird möglicherweise die folgende Meldung angezeigt.

![Aktualisieren der Shader-Eingabeaufforderung](../images/tools/UpdateShaderPrompt.png)

Durch Auswahl **von Ja** wird MRTK angewiesen, den Inhalt von  >  **Assets MRTK-Shadern** mit der neuesten Version zu  >   überschreiben. Wenn Sie **Nein auswählen,** werden die aktuellen Dateien beibehalten. **Ignore** erstellt eine Datei ( `IgnoreUpdateCheck.sentinel` ) in **Assets**  >  **MRTK** Shaders, die zukünftige  >  Überprüfungen von Shaderupdates unterdrückt.

> [!IMPORTANT]
> Beim Überschreiben der Shaderdateien gehen alle benutzerdefinierten Änderungen verloren. Stellen Sie sicher, dass Sie alle geänderten Shaderdateien vor dem Upgrade sichern.
>
> Wenn das Projekt für die Verwendung der Universal Render Pipeline (URP) – früher Lightweight Render Pipeline (LWRP) konfiguriert wurde, führen Sie **Mixed Reality** > **Toolkit** > **Utilities** >
>  **Upgrade MRTK Standard Shader for Lightweight Render Pipeline** erneut aus.

Unter ist auch jederzeit möglich, mithilfe von **Mixed Reality** Toolkit Utilities Check for Shader Updates (Überprüfen auf Shaderupdates) in der Menüleiste des  >    >    >  Unity-Editors nach **Shaderupdates** zu suchen.

![Überprüfen auf Shaderupdates](../images/tools/ShaderUpdateMenu.png)

**Bei der Überprüfung auf Shaderupdates** wird die Datei `IgnoreUpdateCheck.sentinel` ignoriert, und die Aktualisierung des shaders wird bei Bedarf ermöglicht.

> [!NOTE]
> Eine Überprüfung auf Shaderupdates ist beim Importieren der MRTK-UNITYPACKAGE-Dateien nicht erforderlich.
