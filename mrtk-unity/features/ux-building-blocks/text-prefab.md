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
# <a name="text-prefab"></a>Text prefab

Diese Prefabs sind für die Renderingqualität in der Windows Mixed Reality. Weitere Informationen finden Sie in der Richtlinie [Text in Unity](/windows/mixed-reality/text-in-unity) auf Microsoft Windows Dev Center.

## <a name="prefabs"></a>Prefabs

### <a name="3dtextprefab"></a>3DTextPrefab

3D Text Mesh-Prefab (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) mit optimiertem Skalierungsfaktor bei 2-Meter-Entfernung. (Lesen Sie die anweisungen unten.)

### <a name="uitextprefab"></a>UITextPrefab

Ui Text Mesh Prefab (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) mit optimiertem Skalierungsfaktor bei 2 Meter Entfernung. (Lesen Sie die anweisungen unten.)

## <a name="fonts"></a>Schriftarten

Open-Source-Schriftarten (Assets/MRTK/Core/StandardAssets/Fonts), die im Mixed Reality sind.

> [!IMPORTANT]
> Text Prefab verwendet die Open Source-Schriftart "Sewikik". Um Text Prefab mit einer anderen Schriftart zu verwenden, importieren Sie die Schriftartdatei, und befolgen Sie die folgenden Anweisungen. Das folgende Beispiel zeigt, wie Sie die Schriftart "Segoe UI" mit text prefab verwenden.

![Importieren Segoe UI Schriftartdatei](../images/text-prefab/TextPrefabInstructions01.png)

1. Weisen Sie dem Material 3DTextSegoeUI.mat eine Schriftarttextur zu.

    ![Zuweisen der Schriftarttextur](../images/text-prefab/TextPrefabInstructions02.png)

1. Wählen Sie auf dem Material 3DTextSegoeUI.mat den Shader Custom/3DTextShader.shader aus.

    ![Zuweisen eines Shaders](../images/text-prefab/TextPrefabInstructions03.png)

1. Weisen Sie den Textkomponenten in den Prefabs Segoe UI Schriftart und 3DTextSegoeUI-Material zu.

    ![Zuweisen von Schriftartdatei und -material](../images/text-prefab/TextPrefabInstructions04.png)

### <a name="working-with-fonts-in-unity"></a>Arbeiten mit Schriftarten in Unity

Beim Hinzufügen einer neuen 3D-Textmesh zu einer Szene in Unity gibt es zwei Probleme, die visuell offensichtlich sind. Eine, die Schriftart wird sehr groß und zwei, die Schriftart erscheint sehr unscharf. Es ist auch interessant zu beachten, dass der Standardmäßige Schriftgradwert im Inspector auf 0 (null) festgelegt ist. Das Ersetzen dieses Nullwerts durch 13 zeigt keinen Größenunterschied, da 13 tatsächlich der Standardwert ist.

Unity geht davon aus, dass alle neuen Elemente, die einer Szene hinzugefügt werden, eine Unity-Einheit oder eine 100%ige Transformationsskala aufweisen, was auf der HoloLens etwa eine Meter groß ist. Bei Schriftarten ist das Begrenzungsfeld für eine 3D-Textmesh standardmäßig bei etwa einer Meter Höhe enthalten.

### <a name="font-scale-and-font-sizes"></a>Schriftgrad und Schriftgrade

Die meisten visuellen Designer verwenden Punkte, um Schriftgrade in der realen Welt sowie ihre Entwurfsprogramme zu definieren. Es gibt etwa 2835 (2.834,645666399962) Punkte in einer Verbrauchsmessung. Basierend auf der Punktsystemkonvertierung in 1 Meter und dem Standardmäßigen TextMesh-Schriftgrad von Unity von 13 bietet die einfache Berechnung von 13 geteilt durch 2835 gleich 0,0046 (0,004586111116, um genau zu sein) eine gute Standardskala, mit der begonnen werden kann, obwohl einige möglicherweise auf 0,005 runden möchten.

In beiden Fällen ermöglicht die Skalierung des Textobjekts oder Containers auf diese Werte nicht nur die 1:1-Konvertierung von Schriftgraden aus einem Entwurfsprogramm, sondern bietet auch einen Standard, um die Konsistenz während der gesamten Anwendung oder des Spiels beizubehalten.

### <a name="ui-text"></a>Text der Benutzeroberfläche

Wenn Sie einer Szene ein Benutzeroberflächen- oder Canvas-basiertes Textelement hinzufügen, ist die Größenunterschiede immer noch größer. Die Unterschiede in den beiden Größen sind etwa 1000 %, wodurch der Skalierungsfaktor für benutzeroberflächenbasierte Textkomponenten auf 0,00046 (0,0004586111116) oder 0,0005 für den gerundeten Wert erhöht würde.

**Haftungsausschluss:** Der Standardwert einer beliebigen Schriftart kann durch die Texturgröße dieser Schriftart oder die Art und Weise, wie die Schriftart in Unity importiert wurde, beeinträchtigt werden. Diese Tests wurden basierend auf der standardmäßigen Arial-Schriftart in Unity sowie auf einer anderen importierten Schriftart durchgeführt.

![Schriftgrad mit Skalierungsfaktoren](../images/text-prefab/TextPrefabInstructions07.png)

### <a name="text3dselawikmat"></a>[Text3DSewikik.mat](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/StandardAssets/Materials/)

Material für 3DTextPrefab mit Okklusionsunterstützung. Erfordert 3DTextShader.shader

![Standardschriftart im Vergleich zu 3DTextSegoeUI-Material](../images/text-prefab/TextPrefabInstructions06.png)

### <a name="text3dshadershader"></a>[Text3DShader.shader](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/StandardAssets/Shaders)

Shader für 3DTextPrefab mit Okklusionsunterstützung.