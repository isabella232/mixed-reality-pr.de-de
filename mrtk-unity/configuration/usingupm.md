---
title: Verwenden des Unity-Paket-Managers
description: Verwenden von MRTK in Unity Paket-Manager
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK-Pakete,
ms.openlocfilehash: 524783c48b82722aec26648ea54477a6c7bcd4ae
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177322"
---
# <a name="using-the-unity-package-manager"></a><span data-ttu-id="6fccd-104">Verwenden des Unity-Paket-Managers</span><span class="sxs-lookup"><span data-stu-id="6fccd-104">Using the Unity Package Manager</span></span>

<span data-ttu-id="6fccd-105">Ab Version 2.5.0 kann das Microsoft Mixed Reality Toolkit mithilfe des [Mixed Reality Feature Tools](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)in unity Paket-Manager (UPM) integriert werden, wenn Unity 2019.4 und höher verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="6fccd-105">Starting with version 2.5.0, using the [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool), the Microsoft Mixed Reality Toolkit integrates with the Unity Package Manager (UPM) when using Unity 2019.4 and newer.</span></span>

## <a name="using-the-mixed-reality-feature-tool"></a><span data-ttu-id="6fccd-106">Verwenden des Mixed Reality-Featuretools</span><span class="sxs-lookup"><span data-stu-id="6fccd-106">Using the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="6fccd-107">Wie unter [Willkommen beim Mixed Reality Feature-Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) beschrieben, können Sie das Tool über diesen [Link](https://aka.ms/MRFeatureTool)herunterladen.</span><span class="sxs-lookup"><span data-stu-id="6fccd-107">As described in [Welcome to the Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) you can download the tool using [this link](https://aka.ms/MRFeatureTool).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6fccd-108">Wenn das Manifest des Projekts über einen `Microsoft Mixed Reality` Eintrag im `scopedRegistries` Abschnitt verfügt, wird empfohlen, es zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="6fccd-108">If the project's manifest has a `Microsoft Mixed Reality` entry in the `scopedRegistries` section, it is recommended that it be removed.</span></span>
>
> <span data-ttu-id="6fccd-109">Um eine konfigurierte Bereichsregistrierung zu entfernen, gehen Sie zu `Edit`  >  `Project Settings`  >  `Package Manager` .</span><span class="sxs-lookup"><span data-stu-id="6fccd-109">To remove a configured scoped registry, please to to `Edit` > `Project Settings` > `Package Manager`.</span></span>
>
> ![Entfernen einer bereichsbegrenzten Registrierung](../features/images/packaging/RemoveScopedRegistry.png)

<span data-ttu-id="6fccd-111">MRTK-Pakete werden beim Ermitteln von Features unter der `Mixed Reality Toolkit` Überschrift angezeigt.</span><span class="sxs-lookup"><span data-stu-id="6fccd-111">MRTK packages appear under the `Mixed Reality Toolkit` heading when discovering features.</span></span>

![Entdecken von Features](../features/images/packaging/DiscoverFeatures.png)

<span data-ttu-id="6fccd-113">Wenn Sie Features auswählen, müssen Sie sich nicht um erforderliche Abhängigkeiten kümmern. Das Tool lädt sie automatisch herunter und integriert sie in das Projekt.</span><span class="sxs-lookup"><span data-stu-id="6fccd-113">When selecting features, there is no need to be concerned with required dependencies, the tool will automatically download and integrate them into the project.</span></span>

![Erforderliche Abhängigkeiten](../features/images/packaging/RequiredDependencies.png)

## <a name="managing-mixed-reality-features-with-the-unity-package-manager"></a><span data-ttu-id="6fccd-115">Verwalten Mixed Reality Features mit dem Unity-Paket-Manager</span><span class="sxs-lookup"><span data-stu-id="6fccd-115">Managing Mixed Reality features with the Unity Package Manager</span></span>

<span data-ttu-id="6fccd-116">Nachdem dem Paketmanifest ein Mixed Reality Toolkit-Paket hinzugefügt wurde, kann es über die Benutzeroberfläche von Unity Paket-Manager verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="6fccd-116">Once a Mixed Reality Toolkit package has been added to the package manifest, it can be managed using the Unity Package Manager user interface.</span></span>

![MRTK Foundation UPM-Paket](../features/images/packaging/MRTK_FoundationUPM.png)

> [!NOTE]
> <span data-ttu-id="6fccd-118">Wenn ein Mixed Reality Toolkit-Paket mithilfe des Unity-Paket-Manager entfernt wird, muss es mithilfe der [zuvor beschriebenen Schritte](#using-the-mixed-reality-feature-tool)erneut hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="6fccd-118">If a Mixed Reality Toolkit package is removed using the Unity Package Manager, it will have to be re-added using the [previously described steps](#using-the-mixed-reality-feature-tool).</span></span>

### <a name="using-mixed-reality-toolkit-examples"></a><span data-ttu-id="6fccd-119">Verwenden von Beispielen für Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="6fccd-119">Using Mixed Reality Toolkit examples</span></span>

<span data-ttu-id="6fccd-120">Im Gegensatz zur Verwendung von Assetpaketdateien (UNITYPACKAGE) `com.microsoft.mixedreality.toolkit.examples` und importieren Sie die `com.microsoft.mixedreality.toolkit.handphysicsservice` Beispielszenen und Objekte nicht automatisch.</span><span class="sxs-lookup"><span data-stu-id="6fccd-120">Unlike when using asset package (.unitypackage) files, `com.microsoft.mixedreality.toolkit.examples` and `com.microsoft.mixedreality.toolkit.handphysicsservice` do not automatically import the example scenes and assets.</span></span>

<span data-ttu-id="6fccd-121">Führen Sie die folgenden Schritte aus, um eines oder mehrere der Beispiele zu verwenden:</span><span class="sxs-lookup"><span data-stu-id="6fccd-121">To utilize one or more of the examples, please use the following steps:</span></span>

1. <span data-ttu-id="6fccd-122">Navigieren Sie im Unity-Editor zu . `Window` > `Package Manager`</span><span class="sxs-lookup"><span data-stu-id="6fccd-122">In the Unity Editor, navigate to `Window` > `Package Manager`</span></span>
1. <span data-ttu-id="6fccd-123">Wählen Sie in der Liste der Pakete folgende Option aus: `Mixed Reality Toolkit Examples`</span><span class="sxs-lookup"><span data-stu-id="6fccd-123">In the list of packages, select `Mixed Reality Toolkit Examples`</span></span>
1. <span data-ttu-id="6fccd-124">Suchen Sie die gewünschten Stichproben in der `Samples` Liste.</span><span class="sxs-lookup"><span data-stu-id="6fccd-124">Locate the desired sample(s) in the `Samples` list</span></span>
1. <span data-ttu-id="6fccd-125">Klicken Sie auf `Import into Project`.</span><span class="sxs-lookup"><span data-stu-id="6fccd-125">Click `Import into Project`</span></span>

![Importieren von Beispielen](../features/images/packaging/MRTK_ExamplesUpm.png)

<span data-ttu-id="6fccd-127">Wenn ein Beispielpaket aktualisiert wird, bietet Unity die Option zum Aktualisieren importierter Beispiele.</span><span class="sxs-lookup"><span data-stu-id="6fccd-127">When an example package is updated, Unity provides the option to update imported samples.</span></span>

> [!NOTE]
> <span data-ttu-id="6fccd-128">Beim Aktualisieren eines importierten Beispiels werden alle Änderungen überschrieben, die an diesem Beispiel und den zugehörigen Ressourcen vorgenommen wurden.</span><span class="sxs-lookup"><span data-stu-id="6fccd-128">Updating an imported sample will overwrite any changes that have been made to that sample and the associated assets.</span></span>

## <a name="see-also"></a><span data-ttu-id="6fccd-129">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="6fccd-129">See Also</span></span>

- [<span data-ttu-id="6fccd-130">Mixed Reality Toolkit-Pakete</span><span class="sxs-lookup"><span data-stu-id="6fccd-130">Mixed Reality Toolkit packages</span></span>](../packages/mrtk-packages.md)
