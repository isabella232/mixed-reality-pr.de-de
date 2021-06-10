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
# <a name="updating-shaders"></a><span data-ttu-id="760fb-104">Aktualisieren von Shadern</span><span class="sxs-lookup"><span data-stu-id="760fb-104">Updating Shaders</span></span>

<span data-ttu-id="760fb-105">Ab Version 2.6.0 werden die MRTK-Shader über das MRTK versioniert. Shaders.sentinel-Datei.</span><span class="sxs-lookup"><span data-stu-id="760fb-105">Starting with version 2.6.0, the MRTK shaders are being versioned via the MRTK.Shaders.sentinel file.</span></span> <span data-ttu-id="760fb-106">Beim Upgrade auf eine neue Version von MRTK wird möglicherweise die folgende Meldung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="760fb-106">When upgrading to a new version of MRTK, the following message may appear.</span></span>

![Aktualisieren der Shader-Eingabeaufforderung](../images/tools/UpdateShaderPrompt.png)

<span data-ttu-id="760fb-108">Durch Auswahl **von Ja** wird MRTK angewiesen, den Inhalt von  >  **Assets MRTK-Shadern** mit der neuesten Version zu  >   überschreiben.</span><span class="sxs-lookup"><span data-stu-id="760fb-108">Selecting **Yes** instructs MRTK to overwrite the contents of **Assets** > **MRTK** > **Shaders** with the latest version.</span></span> <span data-ttu-id="760fb-109">Wenn Sie **Nein auswählen,** werden die aktuellen Dateien beibehalten.</span><span class="sxs-lookup"><span data-stu-id="760fb-109">Selecting **No** will preserve the current files.</span></span> <span data-ttu-id="760fb-110">**Ignore** erstellt eine Datei ( `IgnoreUpdateCheck.sentinel` ) in **Assets**  >  **MRTK** Shaders, die zukünftige  >  Überprüfungen von Shaderupdates unterdrückt.</span><span class="sxs-lookup"><span data-stu-id="760fb-110">**Ignore** will create a file (`IgnoreUpdateCheck.sentinel`) in **Assets** > **MRTK** > **Shaders**, which will suppress future shader update checks.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="760fb-111">Beim Überschreiben der Shaderdateien gehen alle benutzerdefinierten Änderungen verloren.</span><span class="sxs-lookup"><span data-stu-id="760fb-111">When overwriting the shader files, any custom modifications will be lost.</span></span> <span data-ttu-id="760fb-112">Stellen Sie sicher, dass Sie alle geänderten Shaderdateien vor dem Upgrade sichern.</span><span class="sxs-lookup"><span data-stu-id="760fb-112">Be sure to backup any modified shader files before upgrading.</span></span>
>
> <span data-ttu-id="760fb-113">Wenn das Projekt für die Verwendung der Universal Render Pipeline (URP) – früher Lightweight Render Pipeline (LWRP) konfiguriert wurde, führen Sie **Mixed Reality** > **Toolkit** > **Utilities** >
>  **Upgrade MRTK Standard Shader for Lightweight Render Pipeline** erneut aus.</span><span class="sxs-lookup"><span data-stu-id="760fb-113">If the project has been configured to use the Universal Render Pipeline (URP) - formerly Lightweight Render Pipeline (LWRP), please re-run **Mixed Reality** > **Toolkit** > **Utilities** >
**Upgrade MRTK Standard Shader for Lightweight Render Pipeline**.</span></span>

<span data-ttu-id="760fb-114">Unter ist auch jederzeit möglich, mithilfe von **Mixed Reality** Toolkit Utilities Check for Shader Updates (Überprüfen auf Shaderupdates) in der Menüleiste des  >    >    >  Unity-Editors nach **Shaderupdates** zu suchen.</span><span class="sxs-lookup"><span data-stu-id="760fb-114">At is also possible to check for shader updates at any time using **Mixed Reality** > **Toolkit** > **Utilities** > **Check for Shader Updates** on the Unity Editor's menu bar.</span></span>

![Überprüfen auf Shaderupdates](../images/tools/ShaderUpdateMenu.png)

<span data-ttu-id="760fb-116">**Bei der Überprüfung auf Shaderupdates** wird die Datei `IgnoreUpdateCheck.sentinel` ignoriert, und die Aktualisierung des shaders wird bei Bedarf ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="760fb-116">**Check for Shader Updates** disregards the `IgnoreUpdateCheck.sentinel` file and allows on-demand shader updating.</span></span>

> [!NOTE]
> <span data-ttu-id="760fb-117">Eine Überprüfung auf Shaderupdates ist beim Importieren der MRTK-UNITYPACKAGE-Dateien nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="760fb-117">Checking for shader updates is not required when importing the MRTK .unitypackage files.</span></span>
