---
title: Dialog
description: Beschreibung für Dialogsteuerelemente.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 729c3f6a6b9bc63a498c5d76205a0730f52c678a
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489190"
---
# <a name="dialog"></a><span data-ttu-id="5ba49-104">Dialog</span><span class="sxs-lookup"><span data-stu-id="5ba49-104">Dialog</span></span>

![Dialog](../images/dialog/MRTK_UX_Dialog_Main.png)

<span data-ttu-id="5ba49-106">Dialogsteuerelemente sind Benutzeroberflächenüberlagerungen, die kontextbezogene App-Informationen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="5ba49-106">Dialog controls are UI overlays that provide contextual app information.</span></span> <span data-ttu-id="5ba49-107">Sie verlangen häufig eine Aktion vom Benutzer.</span><span class="sxs-lookup"><span data-stu-id="5ba49-107">They often request some kind of action from the user.</span></span> <span data-ttu-id="5ba49-108">Verwenden Sie Dialogfelder, um Benutzern wichtige Informationen mitzuteilen oder deren Bestätigung bzw. zusätzliche Informationen anzufordern, bevor eine Aktion abgeschlossen werden kann.</span><span class="sxs-lookup"><span data-stu-id="5ba49-108">Use dialogs to notify users of important information or to request confirmation or additional info before an action can be completed.</span></span>

## <a name="example-scene"></a><span data-ttu-id="5ba49-109">Beispielszene</span><span class="sxs-lookup"><span data-stu-id="5ba49-109">Example scene</span></span>

<span data-ttu-id="5ba49-110">Beispiele finden Sie in der **DialogExample-Szene** unter: [MRTK/Examples/Demo/UX/Dialog](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/UX/Dialog)</span><span class="sxs-lookup"><span data-stu-id="5ba49-110">You can find examples in the **DialogExample** scene under: [MRTK/Examples/Demo/UX/Dialog](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/UX/Dialog)</span></span>

## <a name="how-to-use-dialog-control"></a><span data-ttu-id="5ba49-111">Verwenden des Dialogsteuerelements</span><span class="sxs-lookup"><span data-stu-id="5ba49-111">How to use Dialog control</span></span>

<span data-ttu-id="5ba49-112">MRTK stellt drei Dialogpräfabs bereit:</span><span class="sxs-lookup"><span data-stu-id="5ba49-112">MRTK provides three Dialog prefabs:</span></span>

- <span data-ttu-id="5ba49-113">DialogSmall_192x96.prefab</span><span class="sxs-lookup"><span data-stu-id="5ba49-113">DialogSmall_192x96.prefab</span></span>
- <span data-ttu-id="5ba49-114">DialogMedium_192x128.prefab</span><span class="sxs-lookup"><span data-stu-id="5ba49-114">DialogMedium_192x128.prefab</span></span>
- <span data-ttu-id="5ba49-115">DialogLarge_192x192.prefab</span><span class="sxs-lookup"><span data-stu-id="5ba49-115">DialogLarge_192x192.prefab</span></span>

<span data-ttu-id="5ba49-116">Verwenden Sie Dialog.Open(), um ein neues Dialogfeld zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="5ba49-116">Use Dialog.Open() to open a new dialog.</span></span> <span data-ttu-id="5ba49-117">Geben Sie das Prefab des Dialogfelds, die Anzahl der Schaltflächen, den Titeltext, den Meldungstext, die Platzierungsentfernung (nah oder fern) und zusätzliche Variablen an.</span><span class="sxs-lookup"><span data-stu-id="5ba49-117">Specify the dialog prefab, number of buttons, title text, message text, placement distance(near or far), additional variables).</span></span> <span data-ttu-id="5ba49-118">Das Dialogfeld enthält die Dialogfeldoptionen "Confirmation(single button)" und "Choice(two-buttons)".</span><span class="sxs-lookup"><span data-stu-id="5ba49-118">Dialog provides 'Confirmation(single button)' and 'Choice(two-buttons)' dialog options.</span></span>

```c#
public static Dialog Open(GameObject dialogPrefab, DialogButtonType buttons, string title, string message, bool placeForNearInteraction, System.Object variable = null)
```

### <a name="example-of-opening-a-large-dialog-with-a-single-ok-button-placed-at-far-interaction-range-gaze-hand-ray-motion-controller"></a><span data-ttu-id="5ba49-119">Beispiel für das Öffnen eines großen Dialogfelds mit einer einzelnen SCHALTFLÄCHE "OK", die im fernen Interaktionsbereich platziert wird (Anvieren, Handstrahl, Motion Controller)</span><span class="sxs-lookup"><span data-stu-id="5ba49-119">Example of opening a Large dialog with a single 'OK' button, placed at far interaction range (gaze, hand ray, motion controller)</span></span>

```c#
Dialog.Open(DialogPrefabLarge, DialogButtonType.OK, "Confirmation Dialog, Large, Far", "This is an example of a large dialog with only one button, placed at far interaction range", false);
```

### <a name="example-of-opening-a-small-dialog-containing-a-choice-message-for-the-user-placed-at-near-interaction-range-direct-hand-interaction"></a><span data-ttu-id="5ba49-120">Beispiel für das Öffnen eines kleinen Dialogfelds, das eine Auswahlnachricht für den Benutzer enthält, die sich in der Nähe des Interaktionsbereichs befindet (direkte Handinteraktion).</span><span class="sxs-lookup"><span data-stu-id="5ba49-120">Example of opening a Small dialog containing a choice message for the user, placed at near interaction range (direct hand interaction)</span></span>

```c#
Dialog.Open(DialogPrefabSmall, DialogButtonType.Yes | DialogButtonType.No, "Confirmation Dialog, Small, Near", "This is an example of a small dialog with a choice message, placed at near interaction range", true);
```

<span data-ttu-id="5ba49-121">Weitere Informationen finden Sie `DialogExampleController.cs` in der DialogExample.unity-Szene.</span><span class="sxs-lookup"><span data-stu-id="5ba49-121">For more details, please see `DialogExampleController.cs` in DialogExample.unity scene.</span></span>
