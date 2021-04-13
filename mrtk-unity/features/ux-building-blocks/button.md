---
title: Schaltflächen
description: Übersicht über Schaltflächen in mrtk
author: cre8ivepark
ms.author: dongpark
ms.date: 01/12/2021
keywords: Unity, hololens, hololens 2, Mixed Reality, Development, mrtk, mrtk-Schaltflächen
ms.openlocfilehash: 43570c225f25b9ea73c9d1fc4cc9b6c92b8c2dfc
ms.sourcegitcommit: 848b4b7bb8514c2e088a3a55512b1a8075d29093
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/07/2021
ms.locfileid: "107003109"
---
# <a name="button"></a>Schaltfläche

![Schaltfläche Main](../images/button/MRTK_Button_Main.png)

Eine Schaltfläche ermöglicht dem Benutzer das unmittelbare Auslösen einer Aktion. Es ist eine der grundlegenden Komponenten in gemischter Realität. Mrtk bietet verschiedene Typen von Schaltflächen-Prefabs.

## <a name="button-prefabs-in-mrtk"></a>Schaltfläche "Prefabs" in mrtk

Beispiele für die Schaltflächen "Prefabs" unter " ``MRTK/SDK/Features/UX/Interactable/Prefabs`` Folder"

### <a name="unity-ui-imagegraphic-based-buttons"></a>Unity-Benutzeroberflächen Bild/Grafik basierte Schaltflächen

* `UnityUIInteractableButton.prefab`
* `PressableButtonUnityUI.prefab`
* `PressableButtonUnityUICircular.prefab`
* `PressableButtonHoloLens2UnityUI.prefab`

### <a name="collider-based-buttons"></a>Auf Collider basierende Schaltflächen

:::row:::
    :::column:::
    ![PressableButtonHoloLens2](../images/button/MRTK_Button_Prefabs_HoloLens2.png) PressableButtonHoloLens2 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Unplated](../images/button/MRTK_Button_Prefabs_HoloLens2Unplated.png) PressableButtonHoloLens2Unplated 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Circular](../images/button/MRTK_Button_Prefabs_HoloLens2Circular.png) PressableButtonHoloLens2Circular 
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    Die shellstil-Schaltfläche von hololens 2 mit Backplate, die verschiedene visuelle Feedback wie Border Light, near Light und Compressed Front Plate unterstützt.
    :::column-end:::
    :::column:::
    Schaltfläche im shellstil von hololens 2 ohne Backplate
    :::column-end:::
    :::column:::
    Schaltfläche im shellstil von hololens 2 mit Zirkel Form
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    ![PressableButtonHoloLens2_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_32x96.png) **PressableButtonHoloLens2_32x96**
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Bar3H ](../images/button/MRTK_Button_Prefabs_HoloLens2BarH.png) **PressableButtonHoloLens2Bar3H**
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Bar3V ](../images/button/MRTK_Button_Prefabs_HoloLens2BarV.png) **PressableButtonHoloLens2Bar3V**
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    Shell-Stil-Schaltfläche "Wide hololens 2", 32 x 96mm
    :::column-end:::
    :::column:::
    Horizontale hololens 2-Schaltflächen Leiste mit frei gegebener Backplate
    :::column-end:::
    :::column:::
    Vertikale hololens 2-Schaltflächen Leiste mit frei gegebener Backplate
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    ![PressableButtonHoloLens2ToggleCheckBox_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox.png) **PressableButtonHoloLens2ToggleCheckBox_32x32** 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2ToggleSwitch_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch.png) **PressableButtonHoloLens2ToggleSwitch_32x32**
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2ToggleRadio_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio.png) **PressableButtonHoloLens2ToggleRadio_32x32**
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    Kontrollkästchen für das shellformat von hololens 2 im shellstil 32x32mm
    :::column-end:::
    :::column:::
    Shellstil-Switch von hololens 2 32x32mm 
    :::column-end:::
    :::column:::
    "Hololens 2" im shellstil "Radio 32x32mm"
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    ![PressableButtonHoloLens2ToggleCheckBox_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox_32x96.png) **PressableButtonHoloLens2ToggleCheckBox_32x96**
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2ToggleSwitch_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch_32x96.png) **PressableButtonHoloLens2ToggleSwitch_32x96** 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2ToggleRadio_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio_32x96.png) **PressableButtonHoloLens2ToggleRadio_32x96** 
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    Kontrollkästchen für das Shell-Format von hololens 2 im shellstil 32x96mm
    :::column-end:::
    :::column:::
    Shellstil-Switch von hololens 2 32x96mm
    :::column-end:::
    :::column:::
    Im shellstil von hololens 2 im Shell-Stil 32x96mm
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    ![Radialer ](../images/button/MRTK_Button_Radial.png) **radialer**
    :::column-end:::
    :::column:::
    ![Kontrollkästchen](../images/button/MRTK_Button_Checkbox.png) **Kontrollkästchen**
    :::column-end:::
    :::column:::
    ![Umggleswitch ](../images/button/MRTK_Button_ToggleSwitch.png)  -Schalter
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    Radiale Schaltfläche 
    :::column-end:::
    :::column:::
    Checkbox 
    :::column-end:::
    :::column:::
    Umschalter
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    ![ButtonHoloLens1 ](../images/button/MRTK_Button_HoloLens1.png) **ButtonHoloLens1**
    :::column-end:::
    :::column:::
    ![Pressableroundbutton ](../images/button/MRTK_Button_Round.png) **pressableroundbutton** 
    :::column-end:::
    :::column:::
    ![Schaltfläche ](../images/button/MRTK_Button_Base.png) **für** Schaltfläche
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    Schraffurschaltfläche "hololens 1. gen"
    :::column-end:::
    :::column:::
    Schaltfläche "Round Form"
    :::column-end:::
    :::column:::
    Basic-Schaltfläche
    :::column-end:::
:::row-end:::

Der `Button` (Assets/mrtk/SDK/Features/UX/interactable/Prefabs/Button. Prefab) basiert auf dem [interactable](interactable.md) -Konzept, um einfache UI-Steuerelemente für Schaltflächen oder andere Typen interaktiver Oberflächen bereitzustellen. Die Schaltfläche Baseline unterstützt alle verfügbaren Eingabemethoden, einschließlich der Handgelenk Eingabe für die Near-Interaktionen sowie den Blick auf den Blick und den Mauszeiger für die weit entfernten Interaktionen. Sie können auch den Voice-Befehl verwenden, um die Schaltfläche zu aktivieren.

`PressableButtonHoloLens2` (Assets/mrtk/SDK/Features/UX/interactable/Prefabs/PressableButtonHoloLens2. Prefab) ist die shellstilschaltfläche "hololens 2", die die genaue Bewegung der Schaltfläche für die Eingabe der direkt Hand Nachverfolgung unterstützt. Es kombiniert `Interactable` Skripts mit `PressableButton` Skripts.

Bei hololens 2 wird empfohlen, Schaltflächen mit einem nicht transparenten Backplate zu verwenden. Transparente Schaltflächen werden aufgrund dieser Nutzbarkeits-und Stabilitätsprobleme nicht empfohlen:

* Symbol und Text sind schwer zu lesen mit der physischen Umgebung.
* Es ist schwer nachzuvollziehen, wenn das Ereignis ausgelöst wird.
* Holograms, die über eine transparente Ebene angezeigt werden, können mit der tiefen LSR-Stabilisierung von hololens 2 instabil werden.

![Schaltfläche](../images/button/MRTK_Button_UsePlated.png)

## <a name="how-to-use-pressable-buttons"></a>Verwenden von druckbaren Schaltflächen

### <a name="unity-ui-based-buttons"></a>Auf Unity-UI basierende Schaltflächen

Erstellen Sie einen Canvas in Ihrer Szene (gameobject-> UI-> Canvas). Im Inspektor-Panel für Ihren Zeichenbereich:

* Klicken Sie auf "in mrtk-Canvas konvertieren".
* Klicken Sie auf "nearinteraktiontouchableunityui hinzufügen".
* Legen Sie die X-, Y-und Z-Skala der Rect-Transformations Komponente auf 0,001 fest.

Ziehen Sie dann `PressableButtonUnityUI` (Assets/mrtk/SDK/Features/UX/interactable/Prefabs/pressablebuttonunityui). Prefab), `PressableButtonUnityUICircular` (Assets/mrtk/SDK/Features/UX/interactable/Prefabs/pressablebuttonunityuizirkel. Prefab) oder `PressableButtonHoloLens2UnityUI` (Assets/mrtk/SDK/Features/UX/interactable/Prefabs/PressableButtonHoloLens2UnityUI. Prefab) auf der Canvas.

### <a name="collider-based-buttons"></a>Auf Collider basierende Schaltflächen

Ziehen Sie einfach `PressableButtonHoloLens2` (Assets/mrtk/SDK/Features/UX/interactable/Prefabs/PressableButtonHoloLens2. Prefab) oder `PressableButtonHoloLens2Unplated` (Assets/mrtk/SDK/Features/UX/interactable/Prefabs/PressableButtonHoloLens2Unplated. Prefab) in die Szene. Diese Schaltflächen-Prefabs sind bereits so konfiguriert, dass Sie audiovisuelles Feedback für die verschiedenen Typen von Eingaben haben, einschließlich Hand Eingaben und Blick auf die Hand.

Die Ereignisse, die in der vorfab selbst und der [interactable](interactable.md) -Komponente verfügbar gemacht werden, können verwendet werden, um zusätzliche Aktionen zu initiieren. Die druckbaren Schaltflächen in der [handinteraktionexample-Szene](../example-scenes/hand-interaction-examples.md) verwenden das *OnClick* -Ereignis von interactable, um eine Änderung in der Farbe eines Cubes auslöst. Dieses Ereignis wird für verschiedene Typen von Eingabemethoden ausgelöst, z. b. "Blick", "Air-Tap", "Hand Strahl" und "physische Schaltflächen" über das Schaltflächen Skript.

<img src="../images/button/MRTK_Button_HowToUse_Interactable.png" width="450" alt="How to Use Interactable">

Sie können konfigurieren, wann das *OnClick* -Ereignis über die Schaltfläche `PhysicalPressEventRouter` auf der Schaltfläche ausgelöst wird. Beispielsweise können Sie festlegen, dass " *OnClick* " ausgelöst wird, wenn die Schaltfläche zum ersten Mal gedrückt wird, anstatt gedrückt und freigegeben zu werden, indem Sie *interactable beim Klicken* auf das *Ereignis beim Drücken* festlegen.

<img src="../images/button/MRTK_Button_HowTo_Events.png" width="450" alt="How to use events">

Um bestimmte Informationen zum Hand Eingabe Zustand zu nutzen, können Sie Druck Bare Schaltflächen Ereignisse verwenden: *Berührungs Anfang*, *Berührungs Ende*, Schaltfläche, *gedrückt*, *Schaltfläche losgelassen*. Diese Ereignisse werden jedoch nicht als Reaktion auf Luft tippen-, Hand Strahl-oder Augen Eingaben ausgelöst. **Zur Unterstützung von Near-und Far-Interaktionen wird empfohlen, das *OnClick* -Ereignis der interactable zu verwenden.**

<img src="../images/button/MRTK_Button_HowTo_PressableButton.png" width="450"  alt="How to use Pressable Buttons">

## <a name="interaction-states"></a>Interaktions Zustände

Im Leerlaufzustand ist die Vorderseite der Schaltfläche nicht sichtbar. Wenn eine Fingereingabe oder ein Cursor von der Blick Eingabe auf die Oberfläche abzielt, wird der leuchtende Rahmen der Vorderseite sichtbar. Es gibt zusätzliche Hervorhebung der Fingertip-Position auf der Vorderseite der Oberplatte. Bei einem Fingerabdruck wird die Vorderseite mit dem Fingertipp bewegt. Wenn sich der Fingertipp auf die Oberfläche der Vorderseite auswirkt, wird ein feiner Impuls Effekt angezeigt, um dem TouchPoint ein visuelles Feedback zu geben.

In der Schaltfläche "hololens 2 Shell-Style" gibt es viele visuelle Hinweise und Kosten, um das Vertrauen des Benutzers auf die Interaktion zu erhöhen.

|  ![Near Light](../images/button/ux_button_affordance_proximitylight.jpg) | ![Fokus Hervorhebung](../images/button/ux_button_affordance_focushighlight.jpg)  | ![Komprimieren von Cage](../images/button/ux_button_affordance_compression.jpg) | ![Pulse on-Triggern](../images/button/ux_button_affordance_pulse.jpg) |
|:--- | :--- | :--- | :--- |
| Near Light | Fokus Hervorhebung | Komprimieren von Cage | Pulse on-Triggern |

Der feine Pulse-Effekt wird durch die Schaltfläche zum Drücken der Schaltfläche ausgelöst, die nach dem aktuell interagierenden Zeiger, der nach dem aktuell interagierenden Zeiger ist *, nach "* ". Wenn Näherungs Lichter gefunden werden, wird die- `ProximityLight.Pulse` Methode aufgerufen, die Shader-Parameter automatisch animiert, um einen Impuls anzuzeigen.

## <a name="inspector-properties"></a>Inspektor-Eigenschaften

![Schaltflächen Struktur](../images/button/MRTK_Button_Structure.png)

**Box-Collider** 
 `Box Collider` für die Vorderseite der Schaltfläche.

**Schaltfläche zum Komprimieren** Die Logik für die Schaltflächen Bewegung mit der Hand Press Interaktion.

**Physischer Press-Ereignis Router** Dieses Skript sendet Ereignisse von der Hand Press Interaktion an [interactable](interactable.md).

**Interactable** 
 [Interactable](interactable.md) behandelt verschiedene Typen von Interaktions Zuständen und-Ereignissen. Hololens, Eingaben, Gesten und Spracheingabe und immersive Headset-Bewegung Controller Eingaben werden direkt von diesem Skript behandelt.

**Audioquelle** Unity-Audioquelle für die Audiofeedback-Clips.

" *Nearinteraktiontouchable. cs* " ist erforderlich, damit ein beliebiges Objekt mit einer Handgelenk Eingabe touchfähig ist.

## <a name="prefab-layout"></a>Vorfab-Layout

Das *buttoncontent* -Objekt enthält Front Plate, Text Bezeichnung und Symbol. Die *frontplate* antwortet mit dem *Button_Box* -Shader auf die Nähe des Index fingerabbilds. Es zeigt leuchtende Rahmen, Näherungs Licht und einen Impuls Effekt bei der Berührung. Die Bezeichnung Text wird mit textmesh pro erstellt. Die Sichtbarkeit von " *mineitsayitlabel*" wird durch das Design der [interactable](interactable.md)gesteuert.

![Schaltflächen Layout](../images/button/MRTK_Button_Layout.png)

## <a name="how-to-change-the-icon-and-text"></a>Ändern von Symbol und Text

Mrtk-Schaltflächen verwenden eine `ButtonConfigHelper` Komponente, um das Symbol, den Text und die Bezeichnung der Schaltfläche zu ändern. (Beachten Sie, dass einige Felder möglicherweise fehlen, wenn Elemente nicht auf der ausgewählten Schaltfläche vorhanden sind.)

![Schaltflächen Konfigurations Hilfsprogramm](../images/button/MRTK_Button_Config_Helper.png)

### <a name="creating-and-modifying-icon-sets"></a>Erstellen und Ändern von Symbol Sätzen

Ein **Symbolsatz** ist ein frei gegebener Satz von Symbol Ressourcen, die von der Komponente verwendet werden `ButtonConfigHelper` . Drei Symbol *Stile* werden unterstützt.

* **Quad** -Symbole werden mithilfe eines auf einem Quad gerendert `MeshRenderer` . Dies ist der standardmäßige Symbol Stil.
* **Sprite** -Symbole werden mithilfe von gerendert `SpriteRenderer` . Dies ist hilfreich, wenn Sie Ihre Symbole lieber als Sprite-Tabelle importieren möchten, oder wenn Sie möchten, dass Ihre Symbol Objekte mit Unity-UI-Komponenten gemeinsam genutzt werden. Um dieses Format zu verwenden, müssen Sie das Sprite-Editor **-Paket (Windows-> Package Manager-> 2D Sprite) installieren.**
* **Char** -Symbole werden mithilfe einer-Komponente gerendert `TextMeshPro` . Dies ist nützlich, wenn Sie lieber eine Symbol Schriftart verwenden möchten. Wenn Sie die hololens-Symbol Schriftart verwenden möchten, müssen Sie ein `TextMeshPro` Schriftart Objekt erstellen.

Um den Stil der Schaltfläche zu ändern, erweitern Sie die Dropdown Liste *Symbole* in der Schaltfläche buttonconfighelper, und wählen Sie aus der Dropdown Liste *Icon Style* aus.

Sie können mit dem Asset-Menü ein neues Schaltflächen Symbol erstellen: **Erstellen Sie > Mixed Reality Toolkit > Symbolsatz.** Um Quad-und Sprite-Symbole hinzuzufügen, ziehen Sie Sie einfach in ihre jeweiligen Arrays. Um char-Symbole hinzuzufügen, müssen Sie zuerst ein Schriftart Objekt erstellen und zuweisen.

In mrtk 2,4 und höher wird empfohlen, benutzerdefinierte Symbol Texturen in ein Iconset zu verschieben.
Um die Assets auf allen Schaltflächen in einem Projekt auf das neue empfohlene Format zu aktualisieren, verwenden Sie den buttonconfighelpermigrationhandler.
(Mixed Reality Toolkit-> Utilities-> Migrations Fenster-> Migrations handlerauswahl-> Microsoft. mixedreality. Toolkit. Utilities. buttonconfighelpermigrationhandler)

Importieren des Microsoft. mixedrealitytoolkit. Unity. Tools-Pakets, das zum Aktualisieren der Schaltflächen erforderlich ist.

![Dialog](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

Wenn ein Symbol bei der Migration nicht im Standard Symbol festgelegt wurde, wird ein benutzerdefiniertes Symbol in mixedrealitytoolkit. generated/customiensets erstellt. In einem Dialogfeld wird angezeigt, dass dies stattfindet.

![Benachrichtigung über benutzerdefinierte Symbole](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

### <a name="creating-a-hololens-icon-font-asset"></a>Erstellen eines hololens-Symbol Schriftart-Assets

Importieren Sie zunächst die Symbol Schriftart in Unity. Auf Windows-Computern finden Sie die Standard Schriftart hololens in *Windows/Fonts/holomdl2. ttf.* Kopieren Sie diese Datei, und fügen Sie Sie in den Ordner Assets ein.

Öffnen Sie als nächstes den textmeschpro-schriftstellerersteller über **Fenster > textmeshpro > Schriftart Asset Creator.** Hier finden Sie die empfohlenen Einstellungen für die Erstellung eines hololens-Schriftart Atlas. Fügen Sie den folgenden Unicode-Bereich in das Feld *Zeichenfolge* ein, um alle Symbole einzuschließen:

```c#
E700-E702,E706,E70D-E70E,E710-E714,E718,E71A,E71D-E71E,E720,E722,E728,E72A-E72E,E736,E738,E73F,E74A-E74B,E74D,E74F-E752,E760-E761,E765,E767-E769,E76B-E76C,E770,E772,E774,E777,E779-E77B,E782-E783,E785-E786,E799,E7A9-E7AB,E7AF-E7B1,E7B4,E7C8,E7E8-E7E9,E7FC,E80F,E821,E83F,E850-E859,E872-E874,E894-E895,E8A7,E8B2,E8B7,E8B9,E8D5,E8EC,E8FB,E909,E91B,E92C,E942,E95B,E992-E995,E9E9-E9EA,EA37,EA40,EA4A,EA55,EA96,EB51-EB52,EB65,EB9D-EBB5,EBCB-EBCC,EBCF-EBD3,EC03,EC19,EC3F,EC7A,EC8E-EC98,ECA2,ECD8-ECDA,ECE0,ECE7-ECEB,ED17,EE93,EFA9,F114-F120,F132,F181,F183-F186
```

![Schaltflächen Erstellung 1](../images/button/MRTK_Font_Asset_Creation_1.png)

Nachdem das Schriftart Objekt generiert wurde, speichern Sie es in Ihrem Projekt, und weisen Sie es dem Symbol *Schriftart* Feldzeichen für Symbolsatz zu. Die Dropdown Liste *verfügbare Symbole* wird nun aufgefüllt. Um ein Symbol für die Verwendung durch eine Schaltfläche verfügbar zu machen, klicken Sie darauf. Sie wird der Dropdown Liste *ausgewählte Symbole* hinzugefügt und wird jetzt im angezeigt `ButtonConfigHelper.` . Optional können Sie dem Symbol ein Tag geben. Dadurch kann das Symbol zur Laufzeit festgelegt werden.

![Schaltflächen Erstellung 3](../images/button/MRTK_Font_Asset_Creation_3.png)

![Schaltflächen Erstellung 2](../images/button/MRTK_Font_Asset_Creation_2.png)

```c#
public void SetButtonToAdjust()
{
    ButtonConfigHelper buttonConfigHelper = gameObject.GetComponent<ButtonConfigHelper>();
    buttonConfigHelper.SetCharIconByName("AppBarAdjust");
}
```

Um das Symbol festzulegen, wählen Sie eine Schaltfläche aus, erweitern Sie das Dropdown Feldsymbole in der, `ButtonConfigHelper` und weisen Sie es dem Feld *Symbolsatz* zu.

![Schaltflächen Symbolsatz](../images/button/MRTK_Button_Icon_Set_Assign.png)

## <a name="how-to-change-the-size-of-a-button"></a>Ändern der Größe einer Schaltfläche

Die Größe der Schaltfläche im shellstil von hololens 2 beträgt 32 x 32mm. Um die Dimension anzupassen, ändern Sie die Größe dieser Objekte in der Schaltfläche Prefab:

1. **Frontplate**
2. **Quad** unter "Backplate"
3. **Box-Collider** im Stamm

Klicken Sie dann im "nearinteraktiontouchable"-Skript, das sich im Stammverzeichnis der Schaltfläche befindet, auf die Schaltfläche " **Begrenzungen reparieren** "

Aktualisieren Sie die Größe der frontplate- ![ Schaltflächen Größenanpassung 1.](../images/button/MRTK_Button_SizeCustomization1.png)

Aktualisieren der Größe der Größenanpassung von Quad- ![ Schaltflächen 2](../images/button/MRTK_Button_SizeCustomization2.png)

Aktualisieren der Größe der Schaltfläche für die ![ Größe der Schaltfläche der Schaltfläche für das Feld](../images/button/MRTK_Button_SizeCustomization3.png)

Klicken Sie auf die Schaltfläche "Korrektur Begrenzungen" ![ Schaltflächen Größe 4](../images/button/MRTK_Button_SizeCustomization4.png)

## <a name="voice-command-see-it-say-it&quot;></a>Sprachbefehl (&quot;See-it, Say-it")

**Spracheingabe Handler** Das [interactable](interactable.md) -Skript in der druckbaren Schaltfläche implementiert bereits `IMixedRealitySpeechHandler` . Ein sprach Befehls Schlüsselwort kann hier festgelegt werden.

<img src="../images/button/MRTK_Button_Speech1.png" width="450" alt="Buttons Speech">

**Spracheingabe Profil** Außerdem müssen Sie das sprach Befehls Schlüsselwort im Profil für globale *Sprachbefehle* registrieren.

<img src="../images/button/MRTK_Button_Speech2.png" width="450" alt="Button speech 2">

**Siehe die Bezeichnung** . Die Prefab-Schaltflächen-Prefab hat eine Platzhalter textmesh pro-Bezeichnung unter dem *seeitsayitlabel* -Objekt. Mit dieser Bezeichnung können Sie dem Benutzer das Voice-Befehls Schlüsselwort für die Schaltfläche mitteilen.

<img src="../images/button/MRTK_Button_Speech3.png" width="450" alt="Button Speech 3">

## <a name="how-to-make-a-button-from-scratch"></a>So erstellen Sie eine Schaltfläche von Grund auf

Die Beispiele für diese Schaltflächen können Sie in der **pressablebuttonexample** -Szene finden.

<img src="../images/button/MRTK_PressableButtonCube0.png" alt="Pressable button cube 0">

### <a name="1-creating-a-pressable-button-with-cube-near-interaction-only"></a>1. Erstellen einer druckbaren Schaltfläche mit Cube (nur in naher Interaktion)

1. Erstellen eines Unity-Cubes (gameobject > 3D-Objekt > Cube)
2. Skript hinzufügen `PressableButton.cs`
3. Skript hinzufügen `NearInteractionTouchable.cs`

`PressableButton`Weisen Sie im Bereich Inspektor das Cube-Objekt den visuellen Elementen der Verschieb **enden Schaltfläche** zu.

<img src="../images/button/MRTK_PressableButtonCube3.png" width="450" alt="pressable button cube 3">

Wenn Sie den Cube auswählen, werden mehrere farbige Ebenen für das Objekt angezeigt. Dadurch werden die Entfernungs Werte unter " **Einstellungen**" angezeigt. Mithilfe der Handles können Sie konfigurieren, wann Sie mit dem Drücken der Taste (Verschieben des Objekts) und dem Zeitpunkt des Auslösers eines Ereignisses beginnen.

<img src="../images/button/MRTK_PressableButtonCube1.jpg" width="450" alt="Pressable Buton cube 1">

<img src="../images/button/MRTK_PressableButtonCube2.png" width="450" alt="Pressable button cube 2">

Wenn Sie auf die Schaltfläche klicken, werden die richtigen Ereignisse, die im Skript verfügbar gemacht werden, wie z. b. `PressableButton.cs` touchbegin (), touchend (), ButtonPressed (), buttonreleased (), verschoben und generiert.

<img src="../images/button/MRTK_PressableButtonCubeRun1.jpg" alt="Pressable button cube run 1">

#### <a name="troubleshooting"></a>Problembehandlung

Wenn die Schaltfläche eine Doppel Taste ausführt, stellen Sie sicher, dass die Eigenschaft " **Front Push erzwingen** " aktiv ist und die **Start-pushentfernungsebene** vor der **touchfähigen** Ebene der Near-Interaktion platziert wird. Die **touchable** -Ebene der Near-Interaktion wird durch die blaue Ebene angezeigt, die vor dem Ursprung des weißen Pfeils in der GIF unten platziert wird:

![Druck Bare Schaltflächen Skript Komponente mit hervorgehobener Front-Push-Eigenschaft](../images/button/MRTK_Button_Enforce_Push.png)

![Animiertes Beispiel für das Verschieben der Start-Push-Distanz vor der touchfähigen Ebene der Near-Interaktion](../images/button/MRTK_Button_Front_Touch.gif)

### <a name="2-adding-visual-feedback-to-the-basic-cube-button"></a>2. Hinzufügen von visuellem Feedback zur grundlegenden Cube-Schaltfläche

Der mrtk-Standard-Shader bietet verschiedene Funktionen, die das Hinzufügen von visuellem Feedback erleichtern. Erstellen Sie ein Material, und wählen Sie Shader aus `Mixed Reality Toolkit/Standard` . Oder Sie können eines der vorhandenen Materialien unter verwenden oder duplizieren `/SDK/StandardAssets/Materials/` , das den mrtk-Standard-Shader verwendet.

<img src="../images/button/MRTK_PressableButtonCube4.png" width="450" alt="Pressable button cube 4">

Überprüfen Sie `Hover Light` und `Proximity Light` unter den Optionen für **fließend**. Dies ermöglicht visuelles Feedback sowohl für Near-Light-Interaktionen (Näherungs Licht) als auch für Fern Zeiger (Hover Light).

<img src="../images/button/MRTK_PressableButtonCube5.png" width="450" alt="pressable button cube 5">

<img src="../images/button/MRTK_PressableButtonCubeRun2.jpg" alt="pressable button cube run 2">

### <a name="3-adding-audio-feedback-to-the-basic-cube-button"></a>3. Hinzufügen von Audiofeedback zur grundlegenden Cube-Schaltfläche

Da `PressableButton.cs` Skripts Ereignisse wie touchbegin (), touchend (), ButtonPressed (), buttonreleased () verfügbar machen, können wir einfach Audiofeedback zuweisen. Fügen Sie einfach Unity `Audio Source` zum Cube-Objekt hinzu, und weisen Sie dann Audioclips zu, indem Sie audiosource. playoneshot () auswählen. Sie können MRTK_Select_Main und MRTK_Select_Secondary Audioclips unter `/SDK/StandardAssets/Audio/` Ordner verwenden.

<img src="../images/button/MRTK_PressableButtonCube7.png" width="450" alt="pressable button cube 7">

<img src="../images/button/MRTK_PressableButtonCube6.png" width="450" alt="Pressable Button Cube 6">

### <a name="4-adding-visual-states-and-handle-far-interaction-events"></a>4. Hinzufügen von visuellen Zuständen und behandeln von weitem Interaktions Ereignissen

[Interactable](interactable.md) ist ein Skript, mit dem Sie einen visuellen Zustand für die verschiedenen Typen von Eingabe Interaktionen leicht erstellen können. Es verarbeitet außerdem weit entfernte Interaktions Ereignisse. Fügen Sie `Interactable.cs` das Cube-Objekt hinzu, und ziehen Sie es in das Feld **Ziel** unter **profile**. Erstellen Sie dann ein neues Design mit dem Typ **scaleoffsetcolortheme**. Unter diesem Thema können Sie die Farbe des-Objekts für die spezifischen Interaktions Zustände angeben, z. b. **Fokus** und **gedrückt**. Sie können auch die Skalierung und den Offset steuern. Aktivieren **Sie** die Beschleunigungs-und festgelegte Dauer, um den visuellen Übergang reibungslos zu gestalten.

![Profildesign auswählen](../images/button/mrtk_button_profiles.gif)

Sie sehen, dass das-Objekt auf den weit entfernten (Hand Strahl-oder Cursor Cursor) und Near-Interaktionen (Hand) antwortet.

<img src="../images/button/MRTK_PressableButtonCubeRun3.jpg" alt="Pressable Button Cube Run 3">
<img src="../images/button/MRTK_PressableButtonCubeRun4.jpg" alt="Pressable Button Cube Run 4">

## <a name="custom-button-examples"></a>Benutzerdefinierte Schaltflächen Beispiele

In der [handinteraktionexample-Szene](../example-scenes/hand-interaction-examples.md)finden Sie die Beispiele für das Klavier und die roundschaltfläche, die beide verwenden `PressableButton` .

<img src="../images/button/MRTK_Button_Custom1.png" width="450" alt="Pressable Custom1">

<img src="../images/button/MRTK_Button_Custom2.png" width="450" alt="Pressable Custom2">

Jedem Klavierschlüssel ist ein `PressableButton` -und ein- `NearInteractionTouchable` Skript zugewiesen. Es ist wichtig, zu überprüfen, ob die *lokale vorwärts* Richtung `NearInteractionTouchable` korrekt ist. Sie wird durch einen weißen Pfeil im Editor dargestellt. Stellen Sie sicher, dass der Pfeil von der Vorderseite der Schaltfläche entfernt wird:

<img src="../images/button/MRTK_Button_Custom3.png" width="450" alt="Pressable Custom3">

## <a name="see-also"></a>Weitere Informationen

* [Interaktionsfähig](interactable.md)
* [Visuelle Designs](visual-themes.md)
