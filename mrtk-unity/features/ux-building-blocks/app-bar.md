---
title: App-Leiste
description: Übersicht über die App-Leiste im MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, App-Leiste,
ms.openlocfilehash: 3c8633d91b2c26f8bdc774a98b2cb48ffb276720
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175688"
---
# <a name="app-bar"></a><span data-ttu-id="7e578-104">App-Leiste</span><span class="sxs-lookup"><span data-stu-id="7e578-104">App bar</span></span>

![App-Leiste](../images/app-bar/MRTK_AppBar_Main.png)

<span data-ttu-id="7e578-106">Die App-Leiste ist eine Benutzeroberflächenkomponente, die zusammen mit dem [Steuerelementskript für Begrenzungen verwendet](bounds-control.md) wird.</span><span class="sxs-lookup"><span data-stu-id="7e578-106">App bar is a UI component that is used together with the [bounds control](bounds-control.md) script.</span></span> <span data-ttu-id="7e578-107">Es fügt einem Objekt Schaltflächensteuerelemente mit der Absicht hinzu, es zu bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="7e578-107">It adds button controls to an object with the intent to manipulate it.</span></span> <span data-ttu-id="7e578-108">Mithilfe der Schaltfläche "Anpassen" kann die Begrenzungssteuerschnittstelle für ein Objekt de-/activated werden.</span><span class="sxs-lookup"><span data-stu-id="7e578-108">Using the 'Adjust' button, the bounds control interface for an object can be de- / activated.</span></span> <span data-ttu-id="7e578-109">Die Schaltfläche "Entfernen" sollte das Objekt aus der Szene entfernen.</span><span class="sxs-lookup"><span data-stu-id="7e578-109">The "Remove" button should remove the object from the scene.</span></span>

## <a name="how-to-use-app-bar"></a><span data-ttu-id="7e578-110">Verwenden der App-Leiste</span><span class="sxs-lookup"><span data-stu-id="7e578-110">How to use app bar</span></span>

<span data-ttu-id="7e578-111">Ziehen Sie `AppBar` (Assets/MRTK/SDK/Features/UX/Prefabs/AppBar/AppBar.prefab) in die Szenenhierarchie.</span><span class="sxs-lookup"><span data-stu-id="7e578-111">Drag and drop `AppBar` (Assets/MRTK/SDK/Features/UX/Prefabs/AppBar/AppBar.prefab) into the scene hierarchy.</span></span> <span data-ttu-id="7e578-112">Weisen Sie im Inspektorbereich der Komponente ein beliebiges  Objekt mit einem Begrenzungssteuerelement als Zielgrenze zu, um die App-Leiste hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="7e578-112">In the inspector panel of the component, assign any object with a bounds control as the *Target Bounding Box* to add the app bar to it.</span></span>

<span data-ttu-id="7e578-113">**Wichtig:** Die Aktivierungsoption für die Begrenzungssteuerung für das Zielobjekt sollte "Manuell aktivieren" sein.</span><span class="sxs-lookup"><span data-stu-id="7e578-113">**Important:** The bounds control activation option for the target object should be 'Activate Manually'.</span></span>

<img src="../images/app-bar/MRTK_AppBar_Setup1.png" width="450" alt="Setup 1">

<img src="../images/app-bar/MRTK_AppBar_Setup2.png" width="450" alt="Set up 2">
