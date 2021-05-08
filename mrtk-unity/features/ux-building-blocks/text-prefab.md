---
title: TextPrefab
description: Übersicht über TextPrefab in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, TMP,
ms.openlocfilehash: 7d50a35e3761cf2313a43fcc6ad43ed5bd3064a1
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489290"
---
# <a name="text-prefab"></a><span data-ttu-id="5f2ee-104">Text prefab</span><span class="sxs-lookup"><span data-stu-id="5f2ee-104">Text prefab</span></span>

<span data-ttu-id="5f2ee-105">Diese Prefabs sind für die Renderingqualität in der Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="5f2ee-105">These prefabs are optimized for the rendering quality in Windows Mixed Reality.</span></span> <span data-ttu-id="5f2ee-106">Weitere Informationen finden Sie in der Richtlinie [Text in Unity](/windows/mixed-reality/text-in-unity) auf Microsoft Windows Dev Center.</span><span class="sxs-lookup"><span data-stu-id="5f2ee-106">For more information, please read the guideline [Text in Unity](/windows/mixed-reality/text-in-unity) on Microsoft Windows Dev Center.</span></span>

## <a name="prefabs"></a><span data-ttu-id="5f2ee-107">Prefabs</span><span class="sxs-lookup"><span data-stu-id="5f2ee-107">Prefabs</span></span>

### <a name="3dtextprefab"></a><span data-ttu-id="5f2ee-108">3DTextPrefab</span><span class="sxs-lookup"><span data-stu-id="5f2ee-108">3DTextPrefab</span></span>

<span data-ttu-id="5f2ee-109">3D Text Mesh-Prefab (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) mit optimiertem Skalierungsfaktor bei 2-Meter-Entfernung.</span><span class="sxs-lookup"><span data-stu-id="5f2ee-109">3D Text Mesh prefab (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) with optimized scaling factor at 2-meter distance.</span></span> <span data-ttu-id="5f2ee-110">(Lesen Sie die anweisungen unten.)</span><span class="sxs-lookup"><span data-stu-id="5f2ee-110">(Please read the instructions below)</span></span>

### <a name="uitextprefab"></a><span data-ttu-id="5f2ee-111">UITextPrefab</span><span class="sxs-lookup"><span data-stu-id="5f2ee-111">UITextPrefab</span></span>

<span data-ttu-id="5f2ee-112">Ui Text Mesh Prefab (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) mit optimiertem Skalierungsfaktor bei 2 Meter Entfernung.</span><span class="sxs-lookup"><span data-stu-id="5f2ee-112">UI Text Mesh prefab (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) with optimized scaling factor at 2-meter distance.</span></span> <span data-ttu-id="5f2ee-113">(Lesen Sie die anweisungen unten.)</span><span class="sxs-lookup"><span data-stu-id="5f2ee-113">(Please read the instructions below)</span></span>

## <a name="fonts"></a><span data-ttu-id="5f2ee-114">Schriftarten</span><span class="sxs-lookup"><span data-stu-id="5f2ee-114">Fonts</span></span>

<span data-ttu-id="5f2ee-115">Open-Source-Schriftarten (Assets/MRTK/Core/StandardAssets/Fonts), die im Mixed Reality sind.</span><span class="sxs-lookup"><span data-stu-id="5f2ee-115">Open-source fonts (Assets/MRTK/Core/StandardAssets/Fonts) included in Mixed Reality Toolkit.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5f2ee-116">Text Prefab verwendet die Open Source-Schriftart "Sewikik".</span><span class="sxs-lookup"><span data-stu-id="5f2ee-116">Text Prefab uses the open source font 'Selawik'.</span></span> <span data-ttu-id="5f2ee-117">Um Text Prefab mit einer anderen Schriftart zu verwenden, importieren Sie die Schriftartdatei, und befolgen Sie die folgenden Anweisungen.</span><span class="sxs-lookup"><span data-stu-id="5f2ee-117">To use Text Prefab with a different font, please import the font file and follow the instructions below.</span></span> <span data-ttu-id="5f2ee-118">Das folgende Beispiel zeigt, wie Sie die Schriftart "Segoe UI" mit text prefab verwenden.</span><span class="sxs-lookup"><span data-stu-id="5f2ee-118">Below example shows how to use 'Segoe UI' font with Text Prefab.</span></span>

![Importieren Segoe UI Schriftartdatei](../images/text-prefab/TextPrefabInstructions01.png)

1. <span data-ttu-id="5f2ee-120">Weisen Sie dem Material 3DTextSegoeUI.mat eine Schriftarttextur zu.</span><span class="sxs-lookup"><span data-stu-id="5f2ee-120">Assign font texture to 3DTextSegoeUI.mat material.</span></span>

    ![Zuweisen der Schriftarttextur](../images/text-prefab/TextPrefabInstructions02.png)

1. <span data-ttu-id="5f2ee-122">Wählen Sie auf dem Material 3DTextSegoeUI.mat den Shader Custom/3DTextShader.shader aus.</span><span class="sxs-lookup"><span data-stu-id="5f2ee-122">On 3DTextSegoeUI.mat material, select the shader Custom/3DTextShader.shader.</span></span>

    ![Zuweisen eines Shaders](../images/text-prefab/TextPrefabInstructions03.png)

1. <span data-ttu-id="5f2ee-124">Weisen Sie den Textkomponenten in den Prefabs Segoe UI Schriftart und 3DTextSegoeUI-Material zu.</span><span class="sxs-lookup"><span data-stu-id="5f2ee-124">Assign Segoe UI font and 3DTextSegoeUI material to the text components in the prefabs.</span></span>

    ![Zuweisen von Schriftartdatei und -material](../images/text-prefab/TextPrefabInstructions04.png)

### <a name="working-with-fonts-in-unity"></a><span data-ttu-id="5f2ee-126">Arbeiten mit Schriftarten in Unity</span><span class="sxs-lookup"><span data-stu-id="5f2ee-126">Working with Fonts in Unity</span></span>

<span data-ttu-id="5f2ee-127">Beim Hinzufügen einer neuen 3D-Textmesh zu einer Szene in Unity gibt es zwei Probleme, die visuell offensichtlich sind.</span><span class="sxs-lookup"><span data-stu-id="5f2ee-127">When adding a new 3D TextMesh to a scene in Unity there are two issues that are visually apparent.</span></span> <span data-ttu-id="5f2ee-128">Eine, die Schriftart wird sehr groß und zwei, die Schriftart erscheint sehr unscharf.</span><span class="sxs-lookup"><span data-stu-id="5f2ee-128">One, the font appears very large and two, the font appears very blurry.</span></span> <span data-ttu-id="5f2ee-129">Es ist auch interessant zu beachten, dass der Standardmäßige Schriftgradwert im Inspector auf 0 (null) festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="5f2ee-129">It is also interesting to notice that the default Font Size value is set to zero in the Inspector.</span></span> <span data-ttu-id="5f2ee-130">Das Ersetzen dieses Nullwerts durch 13 zeigt keinen Größenunterschied, da 13 tatsächlich der Standardwert ist.</span><span class="sxs-lookup"><span data-stu-id="5f2ee-130">Replacing this zero value with 13 will show no difference in size, because 13 is actually the default value.</span></span>

<span data-ttu-id="5f2ee-131">Unity geht davon aus, dass alle neuen Elemente, die einer Szene hinzugefügt werden, eine Unity-Einheit oder eine 100%ige Transformationsskala aufweisen, was auf der HoloLens etwa eine Meter groß ist.</span><span class="sxs-lookup"><span data-stu-id="5f2ee-131">Unity assumes all new elements added to a scene is 1 Unity Unit in size, or 100%  Transform scale, which translates to about 1 meter on the HoloLens.</span></span> <span data-ttu-id="5f2ee-132">Bei Schriftarten ist das Begrenzungsfeld für eine 3D-Textmesh standardmäßig bei etwa einer Meter Höhe enthalten.</span><span class="sxs-lookup"><span data-stu-id="5f2ee-132">In the case of fonts, the bounding box for a 3D TextMesh comes in, by default at about 1 meter in height.</span></span>

### <a name="font-scale-and-font-sizes"></a><span data-ttu-id="5f2ee-133">Schriftgrad und Schriftgrade</span><span class="sxs-lookup"><span data-stu-id="5f2ee-133">Font Scale and Font Sizes</span></span>

<span data-ttu-id="5f2ee-134">Die meisten visuellen Designer verwenden Punkte, um Schriftgrade in der realen Welt sowie ihre Entwurfsprogramme zu definieren.</span><span class="sxs-lookup"><span data-stu-id="5f2ee-134">Most visual designers use Points to define font sizes in the real world, as well as their design programs.</span></span> <span data-ttu-id="5f2ee-135">Es gibt etwa 2835 (2.834,645666399962) Punkte in einer Verbrauchsmessung.</span><span class="sxs-lookup"><span data-stu-id="5f2ee-135">There are about 2835 (2,834.645666399962) points in 1 meter.</span></span> <span data-ttu-id="5f2ee-136">Basierend auf der Punktsystemkonvertierung in 1 Meter und dem Standardmäßigen TextMesh-Schriftgrad von Unity von 13 bietet die einfache Berechnung von 13 geteilt durch 2835 gleich 0,0046 (0,004586111116, um genau zu sein) eine gute Standardskala, mit der begonnen werden kann, obwohl einige möglicherweise auf 0,005 runden möchten.</span><span class="sxs-lookup"><span data-stu-id="5f2ee-136">Based on the point system conversion to 1 meter and Unity's default TextMesh Font Size of 13, the simple math of 13 divided by 2835 equals 0.0046 (0.004586111116 to be exact) provides a good standard scale to start with, though some may wish to round to 0.005.</span></span>

<span data-ttu-id="5f2ee-137">In beiden Fällen ermöglicht die Skalierung des Textobjekts oder Containers auf diese Werte nicht nur die 1:1-Konvertierung von Schriftgraden aus einem Entwurfsprogramm, sondern bietet auch einen Standard, um die Konsistenz während der gesamten Anwendung oder des Spiels beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="5f2ee-137">Either way, scaling the Text object or container to these values will not only allow for the 1:1 conversion of font sizes from a design program, but also provides a standard to maintain consistency throughout the application or game.</span></span>

### <a name="ui-text"></a><span data-ttu-id="5f2ee-138">Text der Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="5f2ee-138">UI Text</span></span>

<span data-ttu-id="5f2ee-139">Wenn Sie einer Szene ein Benutzeroberflächen- oder Canvas-basiertes Textelement hinzufügen, ist die Größenunterschiede immer noch größer.</span><span class="sxs-lookup"><span data-stu-id="5f2ee-139">When adding a UI or canvas based Text element to a scene, the size disparity is greater still.</span></span> <span data-ttu-id="5f2ee-140">Die Unterschiede in den beiden Größen sind etwa 1000 %, wodurch der Skalierungsfaktor für benutzeroberflächenbasierte Textkomponenten auf 0,00046 (0,0004586111116) oder 0,0005 für den gerundeten Wert erhöht würde.</span><span class="sxs-lookup"><span data-stu-id="5f2ee-140">The differences in the two sizes is about 1000%, which would bring the scale factor for UI based Text components to 0.00046 (0.0004586111116 to be exact) or 0.0005 for the rounded value.</span></span>

<span data-ttu-id="5f2ee-141">**Haftungsausschluss:** Der Standardwert einer beliebigen Schriftart kann durch die Texturgröße dieser Schriftart oder die Art und Weise, wie die Schriftart in Unity importiert wurde, beeinträchtigt werden.</span><span class="sxs-lookup"><span data-stu-id="5f2ee-141">**Disclaimer**: The default value of any font may be effected by the texture size of that font or how the font was imported into Unity.</span></span> <span data-ttu-id="5f2ee-142">Diese Tests wurden basierend auf der standardmäßigen Arial-Schriftart in Unity sowie auf einer anderen importierten Schriftart durchgeführt.</span><span class="sxs-lookup"><span data-stu-id="5f2ee-142">These tests were performed based on the default Arial font in Unity, as well as one other imported font.</span></span>

![Schriftgrad mit Skalierungsfaktoren](../images/text-prefab/TextPrefabInstructions07.png)

### <a name="text3dselawikmat"></a>[<span data-ttu-id="5f2ee-144">Text3DSewikik.mat</span><span class="sxs-lookup"><span data-stu-id="5f2ee-144">Text3DSelawik.mat</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/StandardAssets/Materials/)

<span data-ttu-id="5f2ee-145">Material für 3DTextPrefab mit Okklusionsunterstützung.</span><span class="sxs-lookup"><span data-stu-id="5f2ee-145">Material for 3DTextPrefab with occlusion support.</span></span> <span data-ttu-id="5f2ee-146">Erfordert 3DTextShader.shader</span><span class="sxs-lookup"><span data-stu-id="5f2ee-146">Requires 3DTextShader.shader</span></span>

![Standardschriftart im Vergleich zu 3DTextSegoeUI-Material](../images/text-prefab/TextPrefabInstructions06.png)

### <a name="text3dshadershader"></a>[<span data-ttu-id="5f2ee-148">Text3DShader.shader</span><span class="sxs-lookup"><span data-stu-id="5f2ee-148">Text3DShader.shader</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/StandardAssets/Shaders)

<span data-ttu-id="5f2ee-149">Shader für 3DTextPrefab mit Okklusionsunterstützung.</span><span class="sxs-lookup"><span data-stu-id="5f2ee-149">Shader for 3DTextPrefab with occlusion support.</span></span>