---
title: Text-Prefab
description: Übersicht über TextPrefab in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, TMP,
ms.openlocfilehash: 1969bc9e3054fec509e9f7d536cbfe4b97e43563e26ba5476601e78e65ad24f9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209057"
---
# <a name="text-prefab"></a>Text-Prefab

Diese Prefabs sind für die Renderingqualität in Windows Mixed Reality optimiert. Weitere Informationen finden Sie [in](/windows/mixed-reality/text-in-unity) der Richtlinie Text in Unity auf Microsoft Windows Dev Center.

## <a name="prefabs"></a>Prefabs

### <a name="3dtextprefab"></a>3DTextPrefab

3D-Textmesh-Prefab (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) mit optimiertem Skalierungsfaktor bei einer Entfernung von 2 Metern. (Lesen Sie die folgenden Anweisungen.)

### <a name="uitextprefab"></a>UITextPrefab

Ui Text Mesh prefab (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) with optimized scaling factor at 2-meter distance(Ui-Textmesh-Prefab (Assets/MRTK/SDK/StandardAssets/Prefabs/Text)) mit optimiertem Skalierungsfaktor bei einer Entfernung von 2 Metern. (Lesen Sie die folgenden Anweisungen.)

## <a name="fonts"></a>Schriftarten

Open-Source-Schriftarten (Assets/MRTK/Core/StandardAssets/Fonts), die in Mixed Reality Toolkit enthalten sind.

> [!IMPORTANT]
> Text Prefab verwendet die Open Source-Schriftart "Selawik". Um text prefab mit einer anderen Schriftart zu verwenden, importieren Sie die Schriftartdatei, und befolgen Sie die folgenden Anweisungen. Das folgende Beispiel zeigt die Verwendung der Schriftart "Segoe UI" mit Text prefab.

![Importieren Segoe UI Schriftartdatei](../images/text-prefab/TextPrefabInstructions01.png)

1. Weisen Sie die Schrifttextur dem Material 3DTextSegoeUI.mat zu.

    ![Zuweisen der Schrifttextur](../images/text-prefab/TextPrefabInstructions02.png)

1. Wählen Sie auf dem Material 3DTextSegoeUI.mat den Shader Custom/3DTextShader.shader aus.

    ![Zuweisen eines Shaders](../images/text-prefab/TextPrefabInstructions03.png)

1. Weisen Sie den Textkomponenten in den Prefabs Segoe UI Schriftart und 3DTextSegoeUI-Material zu.

    ![Zuweisen von Schriftartdatei und -material](../images/text-prefab/TextPrefabInstructions04.png)

### <a name="working-with-fonts-in-unity"></a>Arbeiten mit Schriftarten in Unity

Beim Hinzufügen einer neuen 3D-Textmesh zu einer Szene in Unity gibt es zwei Probleme, die visuell offensichtlich sind. Eine, die Schriftart wird sehr groß und zwei, die Schriftart erscheint sehr unscharf. Es ist auch interessant zu beachten, dass der Standardmäßige Schriftgradwert im Inspector auf 0 (null) festgelegt ist. Wenn Sie diesen Nullwert durch 13 ersetzen, wird kein Größenunterschied angezeigt, da 13 tatsächlich der Standardwert ist.

Unity geht davon aus, dass alle neuen Elemente, die einer Szene hinzugefügt werden, eine Unity-Einheit oder eine 100%ige Transformationsskala aufweisen, was auf der HoloLens etwa eine Meter groß ist. Bei Schriftarten ist das Begrenzungsfeld für eine 3D-Textmesh standardmäßig bei etwa einer Meter Höhe enthalten.

### <a name="font-scale-and-font-sizes"></a>Schriftgrad und Schriftgrade

Die meisten visuellen Designer verwenden Punkte, um Schriftgrade in der realen Welt sowie ihre Entwurfsprogramme zu definieren. Es gibt etwa 2835 (2.834,645666399962) Punkte in einer Verbrauchsmessung. Basierend auf der Punktsystemkonvertierung in 1 Meter und dem Standardmäßigen TextMesh-Schriftgrad von Unity von 13 bietet die einfache Berechnung von 13 geteilt durch 2835 gleich 0,0046 (0,004586111116, um genau zu sein) eine gute Standardskala, mit der begonnen werden kann, obwohl einige möglicherweise auf 0,005 runden möchten.

In beiden Fällen ermöglicht die Skalierung des Textobjekts oder Containers auf diese Werte nicht nur die 1:1-Konvertierung von Schriftgraden aus einem Entwurfsprogramm, sondern bietet auch einen Standard, um die Konsistenz während der gesamten Anwendung oder des Spiels beizubehalten.

### <a name="ui-text"></a>Text der Benutzeroberfläche

Wenn Sie einer Szene ein benutzeroberflächen- oder canvasbasiertes Text-Element hinzufügen, ist die Größenunterschiede immer noch größer. Die Unterschiede in den beiden Größen betragen etwa 1000 %, wodurch der Skalierungsfaktor für benutzeroberflächenbasierte Textkomponenten auf 0,00046 (0,0004586111116) oder 0,0005 für den gerundeten Wert erhöht würde.

**Haftungsausschluss:** Der Standardwert einer beliebigen Schriftart kann durch die Texturgröße dieser Schriftart oder die Art und Weise, wie die Schriftart in Unity importiert wurde, beeinträchtigt werden. Diese Tests wurden basierend auf der Arial-Standardschriftart in Unity sowie auf einer anderen importierten Schriftart ausgeführt.

![Schriftgrad mit Skalierungsfaktoren](../images/text-prefab/TextPrefabInstructions07.png)

### <a name="text3dselawikmat"></a>[Text3DSelawik.mat](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/StandardAssets/Materials/)

Material für 3DTextPrefab mit Occlusion-Unterstützung. Erfordert 3DTextShader.shader

![Standardschriftartmaterial im Vergleich zu 3DTextSegoeUI-Material](../images/text-prefab/TextPrefabInstructions06.png)

### <a name="text3dshadershader"></a>[Text3DShader.shader](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/StandardAssets/Shaders)

Shader für 3DTextPrefab mit Occlusion-Unterstützung.
