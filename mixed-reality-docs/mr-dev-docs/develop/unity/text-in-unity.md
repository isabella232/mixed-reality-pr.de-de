---
title: Text in Unity
description: 'Zum Anzeigen von Text in Unity können Sie zwei Arten von Textkomponenten verwenden: UI-Text und 3D-Textgitternetz.'
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality, Design, Steuerelemente, Schriftart, Typografie, Ui, ux, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 3e5f296e9526e62bde7d03a0fee7847f4664e4a67187fcda1e66e22aa03053b4
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207936"
---
# <a name="text-in-unity"></a>Text in Unity

Text ist eine der wichtigsten Komponenten in holografischen Apps. Zum Anzeigen von Text in Unity können Sie drei Arten von Textkomponenten verwenden: UI-Text, 3D-Textgitternetz und Textgitternetz Pro. Standardmäßig erscheinen Benutzeroberflächentext und 3D-Textgitternetz unscharf und sind zu groß. Das Ändern einiger Variablen führt zu einem schärferen Text mit höherer Qualität und einer verwaltbaren Größe in HoloLens. Sie können eine bessere Renderingqualität erzielen, indem Sie einen Skalierungsfaktor anwenden, um die richtigen Dimensionen zu erhalten, wenn Sie die Komponenten UI-Text und 3D-Textgitternetz verwenden.

![Abrufen von spitzem und ansprechendem Text](images/hug-text-02-640px.png)<br>
*Unscharfer Standardtext in Unity*

## <a name="working-with-unitys-3d-text-text-mesh-and-ui-text"></a>Arbeiten mit 3D-Text (Textgitternetz) und Benutzeroberflächentext von Unity

Unity geht davon aus, dass alle neuen Elemente, die einer Szene hinzugefügt werden, eine Unity-Einheit in der Größe oder eine Transformationsskala von 100 % sind. Eine Unity-Einheit wird auf HoloLens in etwa 1 Meter übersetzt. Bei Schriftarten ist das Begrenzungsfeld für eine 3D-Textmesh standardmäßig bei etwa einer Meter Höhe enthalten.

![Arbeiten mit Schriftarten in Unity](images/640px-hug-text-03.png)<br>
*Standardmäßiger Unity-3D-Text (Textmesh) belegt eine Unity-Einheit(1 Meter).*

<br>

Die meisten visuellen Designer verwenden Punkte, um Schriftgrade in der realen Welt zu definieren. Es gibt etwa 2835 (2.834,645666399962) Punkte in einer Verbrauchsmessung. Basierend auf der Punktsystemkonvertierung in eine Verbrauchseinheit und dem Standardmäßigen Text mesh-Schriftgrad von Unity von 13 entspricht die einfache Berechnung von 13 geteilt durch 2835 0,0046 (0,004586111116), was eine gute Standardskala für den Anfang bietet (einige möchten möglicherweise auf 0,005 runden). Das Skalieren des Textobjekts oder Containers auf diese Werte ermöglicht nicht nur die 1:1-Konvertierung von Schriftgraden in einem Entwurfsprogramm, sondern bietet auch einen Standard, sodass Sie die Konsistenz während ihrer gesamten Erfahrung beibehalten können.

![Skalierungswerte für unity-3D-Text und UI-Text](images/Text_In_Unity_Measurements1.png)<br>
*Skalierungswerte für unity-3D-Text und UI-Text*

<br>

![Unity 3D-Textgitternetz mit optimierten Werten](images/hug-text-05-1000px.png)<br>
*Unity 3D-Textgitternetz mit optimierten Werten*

<br>

Beim Hinzufügen eines Benutzeroberflächen- oder Canvas-basierten Textelements zu einer Szene ist die Größenunterschiede immer noch größer. Die Unterschiede in den beiden Größen betragen etwa 1000 %, wodurch der Skalierungsfaktor für benutzeroberflächenbasierte Textkomponenten auf 0,00046 (0,0004586111116) oder 0,0005 für den gerundeten Wert erhöht wird.

![Unity UI Text with optimized values (Text der Unity-Benutzeroberfläche mit optimierten Werten)](images/hug-text-04-1000px.png)<br>
*Unity UI Text with optimized values (Text der Unity-Benutzeroberfläche mit optimierten Werten)*

<br>

>[!NOTE]
>Der Standardwert einer beliebigen Schriftart kann von der Texturgröße dieser Schriftart oder davon beeinflusst werden, wie die Schriftart in Unity importiert wurde. Diese Tests wurden basierend auf der Arial-Standardschriftart in Unity sowie auf einer anderen importierten Schriftart ausgeführt.

## <a name="working-with-text-mesh-pro"></a>Arbeiten mit Text Mesh Pro

Mit der Text Mesh-Pro von Unity können Sie die Qualität des Textrenderings sichern. Mithilfe der [SDF-Technik (Signed Distance Field)](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf) werden klartextgliederungen unabhängig vom Abstand unterstützt. Mit der gleichen Berechnungsmethode, die wir oben für das 3D-Textgitternetz und den Benutzeroberflächentext verwendet haben, können wir die richtigen Skalierungswerte für herkömmliche typografische Punkte finden. Da das standardmäßige 3D-Textgitter Pro Schriftart mit der Größe 36 eine Begrenzungsgröße von 2,5 Unity-Einheiten (2,5 m) hat, können wir einen Skalierungswert von 0,005 verwenden, um die Punktgröße abzurufen. Die Textgitternetz-Pro im Menü der Benutzeroberfläche hat eine standardmäßige Begrenzungsgröße von 25 Unity-Einheiten (25 m). Dadurch erhalten wir 0,0005 für den Skalierungswert.

![Skalierungswerte für unity-3D-Text und -Benutzeroberfläche](images/Text_In_Unity_Measurements2.png)<br>
*Skalierungswerte für unity-3D-Text und -Benutzeroberfläche*

## <a name="recommended-text-size"></a>Empfohlene Textgröße

Wie Sie erwarten können, sehen Typgrößen, die wir auf einem PC oder Tabletgerät verwenden (in der Regel zwischen 12 und 32t), bei einer Entfernung von 2 Metern klein aus. Dies hängt von den Merkmalen der einzelnen Schriftarten ab, aber im Allgemeinen liegen der empfohlene minimale Anzeigewinkel und die Schrifthöhe für die Lesbarkeit bei etwa 0,35°-0,4°/12,21-13,97 mm, basierend auf unseren Forschungsstudien der Benutzer. Es ist etwa 35-40 pt mit dem oben eingeführten Skalierungsfaktor.

Für die Nahinteraktion bei 0,45 m (45 cm) beträgt der Anzeigewinkel der mindestens lesbaren Schriftart und die Höhe 0,4°-0,5° / 3,14–3,9mm. Dies entspricht etwa 9 bis 12 pt mit dem oben beschriebenen Skalierungsfaktor.

![Near and far interaction range ](images/typography-distance-1000px.jpg)
 *Content at near and far interaction range*

### <a name="the-minimum-legible-font-size"></a>Der mindestens lesbare Schriftgrad

| Entfernung | Betrachtungswinkel | Texthöhe | Schriftgrad |
|---------|---------|---------|---------|
| 45 cm (direkter Bearbeitungsabstand) | 0.4°-0.5° | 3.14–3.9mm | 8.9–11.13pt |
| 2 m | 0.35°-0.4° | 12.21–13.97mm | 34.63-39.58 pt |


### <a name="the-comfortably-legible-font-size"></a>Der lesbare Schriftgrad

| Entfernung | Betrachtungswinkel | Texthöhe | Schriftgrad |
|---------|---------|---------|---------|
| 45 cm (direkter Bearbeitungsabstand) | 0.65°-0.8° | 5,1 bis 6,3 mm | 14.47-17.8 pt |
| 2 m | 0.6°-0.75° | 20,9-26,2 mm | 59.4-74.2 pt |

Segoe UI (die Standardschriftart für Windows) funktioniert in den meisten Fällen gut. Vermeiden Sie jedoch die Verwendung von einfachen oder halb hellen Schriftfamilien in kleiner Größe, da schlanke vertikale Striche vibrieren und die Lesbarkeit beeinträchtigen. Moderne Schriftarten mit ausreichender Strichstärke funktionieren gut. Beispielsweise sehen Helvetica und Arial gut aussehend aus und sind in HoloLens mit regulären oder fett formatierbaren Gewichtungen lesbar.

![Anzeigewinkel ](images/Text_In_Unity_ViewingAngle.jpg)
 *Anzeigeabstand, Winkel und Texthöhe*

## <a name="text-with-mixed-reality-toolkit-v2"></a>Text mit Mixed Reality Toolkit v2

### <a name="sharp-text-rendering-quality-with-proper-dimension"></a>Hohe Textrenderingqualität mit richtiger Dimension

Basierend auf diesen Skalierungsfaktoren haben wir [Textpräfabs mit Benutzeroberflächentext und 3D-Textgitternetz](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Prefabs/Text)erstellt. Entwickler können diese Prefabs verwenden, um einen starken Text und einen konsistenten Schriftgrad zu erhalten.

![Hohe Textrenderingqualität mit richtiger Dimension](images/hug-text-06-1000px.png)<br>
*Hohe Textrenderingqualität mit richtiger Dimension*

### <a name="shader-with-occlusion-support"></a>Shader mit Verdeckungsunterstützung

Das Standardschriftmaterial von Unity unterstützt keine Verdeckung. Aus diesem Grund wird der Text hinter den Objekten standardmäßig angezeigt. Wir haben einen einfachen [Shader hinzugefügt, der die Verdeckung unterstützt.](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/StandardAssets/Shaders/Text3DShader.shader) Die folgende Abbildung zeigt den Text mit Standardschriftartmaterial (links) und den Text mit korrekter Verdeckung (rechts).

![Shader mit Verdeckungsunterstützung](images/hug-text-07-1000px.png)<br>
*Shader mit Verdeckungsunterstützung*

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie die von uns festgelegte Unity-Entwicklungsreise verfolgen, befinden Sie sich in der Mitte der MRTK-Kernbausteine. Von hier aus können Sie mit dem nächsten Baustein fortfahren:

> [!div class="nextstepaction"]
> [Spracheingabe](voice-input-in-unity.md)

Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:

> [!div class="nextstepaction"]
> [Gemeinsame Erfahrung](shared-experiences-in-unity.md)

Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#2-core-building-blocks) zurückkehren.

## <a name="see-also"></a>Siehe auch

* [Textprefab im MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Prefabs/Text)
* [Typografie](../../design/typography.md)
