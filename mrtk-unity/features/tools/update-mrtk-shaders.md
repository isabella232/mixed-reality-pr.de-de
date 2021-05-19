---
title: Shader-Updatetool
description: Dokumentation zum Aktualisieren von MRTK-Standard-Shadern
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: ed9f9fa5e6337850f31ecce9d07bc82a8ea12060
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145130"
---
# <a name="updating-shaders"></a><span data-ttu-id="38072-104">Aktualisieren von Shadern</span><span class="sxs-lookup"><span data-stu-id="38072-104">Updating Shaders</span></span>

<span data-ttu-id="38072-105">Ab Version 2.6.0 werden die MRTK-Shader über das MRTK versioniert. Shaders.sentinel-Datei.</span><span class="sxs-lookup"><span data-stu-id="38072-105">Starting with version 2.6.0, the MRTK shaders are being versioned via the MRTK.Shaders.sentinel file.</span></span> <span data-ttu-id="38072-106">Beim Upgrade auf eine neue Version von MRTK wird möglicherweise die folgende Meldung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="38072-106">When upgrading to a new version of MRTK, the following message may appear.</span></span>

![Aufforderung zum Aktualisieren von Shadern](../images/tools/UpdateShaderPrompt.png)

<span data-ttu-id="38072-108">Wenn **Sie Ja** auswählen, wird MRTK angewiesen, den Inhalt von   >  **Assets-MRTK-Shadern** mit der neuesten Version zu überschreiben.  >  </span><span class="sxs-lookup"><span data-stu-id="38072-108">Selecting **Yes** instructs MRTK to overwrite the contents of **Assets** > **MRTK** > **Shaders** with the latest version.</span></span> <span data-ttu-id="38072-109">Wenn **Sie Nein** auswählen, werden die aktuellen Dateien beibehalten.</span><span class="sxs-lookup"><span data-stu-id="38072-109">Selecting **No** will preserve the current files.</span></span> <span data-ttu-id="38072-110">**Ignore** erstellt eine Datei ( `IgnoreUpdateCheck.sentinel` ) in **Assets**  >  **MRTK**  >  **Shader ,** die zukünftige Shaderupdateüberprüfungen unterdrücken.</span><span class="sxs-lookup"><span data-stu-id="38072-110">**Ignore** will create a file (`IgnoreUpdateCheck.sentinel`) in **Assets** > **MRTK** > **Shaders**, which will suppress future shader update checks.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38072-111">Beim Überschreiben der Shaderdateien geht jede benutzerdefinierte Änderung verloren.</span><span class="sxs-lookup"><span data-stu-id="38072-111">When overwriting the shader files, any custom modifications will be lost.</span></span> <span data-ttu-id="38072-112">Stellen Sie sicher, dass Sie alle geänderten Shaderdateien sichern, bevor Sie ein Upgrade durchführen.</span><span class="sxs-lookup"><span data-stu-id="38072-112">Be sure to backup any modified shader files before upgrading.</span></span>
>
> <span data-ttu-id="38072-113">Wenn das Projekt für die Verwendung der Universal Render Pipeline (URP) – ehemals Lightweight Render Pipeline (LWRP) konfiguriert wurde, führen Sie **Mixed Reality Toolkit** > **Utilities** >
>  **Upgrade MRTK Standard Shader for Lightweight Render Pipeline (MRTK-Standard-Shader für Lightweight-Renderpipeline)** erneut aus.</span><span class="sxs-lookup"><span data-stu-id="38072-113">If the project has been configured to use the Universal Render Pipeline (URP) - formerly Lightweight Render Pipeline (LWRP), please re-run **Mixed Reality Toolkit** > **Utilities** >
**Upgrade MRTK Standard Shader for Lightweight Render Pipeline**.</span></span>

<span data-ttu-id="38072-114">Unter ist es auch möglich, jederzeit mit **Mixed Reality Toolkit**  >  **Utilities** Check for  >  **Shader Updates (Überprüfen auf Shaderupdates)** in der Menüleiste des Unity-Editors nach Shaderupdates zu suchen.</span><span class="sxs-lookup"><span data-stu-id="38072-114">At is also possible to check for shader updates at any time using **Mixed Reality Toolkit** > **Utilities** > **Check for Shader Updates** on the Unity Editor's menu bar.</span></span>

![Suchen nach Shaderupdates](../images/tools/ShaderUpdateMenu.png)

<span data-ttu-id="38072-116">**Bei der Überprüfung auf Shaderupdates** wird die Datei ignoriert, und die `IgnoreUpdateCheck.sentinel` Aktualisierung des bedarfsbasierten Shaders wird ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="38072-116">**Check for Shader Updates** disregards the `IgnoreUpdateCheck.sentinel` file and allows on-demand shader updating.</span></span>

> [!NOTE]
> <span data-ttu-id="38072-117">Beim Importieren der MRTK-UNITYPACKAGE-Dateien ist keine Überprüfung auf Shaderupdates erforderlich.</span><span class="sxs-lookup"><span data-stu-id="38072-117">Checking for shader updates is not required when importing the MRTK .unitypackage files.</span></span>
