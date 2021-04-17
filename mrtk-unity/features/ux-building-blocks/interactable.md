---
title: Interaktionsfähig
description: Übersicht über die Interaktionsfähige Skriptkomponente in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Interactable, Events,
ms.openlocfilehash: f141a394ec9395e0a27cc964caeb66654fb6fe08
ms.sourcegitcommit: 47c402dc8e588817ce60229bf019170fa36f3045
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2021
ms.locfileid: "107581562"
---
# <a name="interactable"></a>Interaktionsfähig

![Interaktionsfähig](../images/interactable/InteractableExamples.png)

Die [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) Komponente ist ein All-in-One-Container, damit jedes Objekt problemlos *interagierbar* und reaktionsfähig für Eingaben ist. Interaktiv fungiert als Catch-All für alle Arten von Eingaben, einschließlich Berührung, Handlicht, Sprache usw. und trichtert diese Interaktionen in [Ereignisse](#events) und [visuelle Designantworten.](visual-themes.md) Diese Komponente bietet eine einfache Möglichkeit, Schaltflächen zu erstellen, die Farbe von Objekten mit Fokus zu ändern und vieles mehr.

## <a name="how-to-configure-interactable"></a>Konfigurieren von Interactable

Die -Komponente ermöglicht drei hauptteilliche Konfigurationsabschnitte:

1) [Allgemeine Eingabekonfiguration](#general-input-settings)
1) [Visuelle Designs](visual-themes.md) für mehrere GameObjects
1) [Ereignishandler](#events)

### <a name="general-input-settings"></a>Allgemeine Eingabeeinstellungen

![Allgemeine interaktivierbare Einstellungen](../images/interactable/InputFeatures_short.png)

**Status**

*States* ist ein [ScriptableObject-Parameter,](https://docs.unity3d.com/Manual/class-ScriptableObject.html) der die Interaktionsphasen definiert, z. B. drücken oder beobachtet, für [interaktivierbare Profile](#interactable-profiles) und [visuelle Designs](visual-themes.md).

**DefaultInteractableStates** (Assets/MRTK/SDK/Features/UX/Interactable/States/DefaultInteractableStates.asset) ist standardmäßig im MRTK enthalten und ist der Standardparameter für *interaktivierbare* Komponenten.

![StatusskriptableObject-Beispiel im Inspektor](../images/interactable/DefaultInteractableStates.png)

Das *DefaultInteractableStates-Medienobjekt* enthält vier Zustände und verwendet die [`InteractableStates`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableStates) Zustandsmodellimplementierungen.

* **Standard:** Es geschieht nichts, dies ist der isolierteste Basiszustand.

* **Focus:** Auf das Objekt wird gezeigt. Dies ist ein einzelner Zustand, es sind derzeit keine anderen Zustände festgelegt, aber der Rang Standard wird nicht festgelegt.

* **Drücken** Sie : Auf das Objekt wird gezeigt, und es wird eine Schaltfläche oder Hand gedrückt. Der Status "Press" (Drücken) rangiert auf den Plätzen Default (Standard) und Focus (Fokus). Dieser Zustand wird auch als Fallback auf Physisches Drücken festgelegt.

* **Deaktiviert:** Die Schaltfläche sollte nicht interaktiv sein, und das visuelle Feedback gibt dem Benutzer auf, ob diese Schaltfläche aus irgendeinem Grund derzeit nicht verwendet werden kann. Theoretisch könnte der Deaktiviert-Zustand alle anderen Zustände enthalten, aber wenn Aktiviert deaktiviert ist, wird der Status Deaktiviert für alle anderen Zustände deaktiviert.

Abhängig von der Reihenfolge in der Liste wird dem Zustand ein Bitwert (#) zugewiesen.

> [!NOTE]
> Im Allgemeinen wird empfohlen, **defaultInteractableStates** (Assets/MRTK/SDK/Features/UX/Interactable/States/DefaultInteractableStates.asset) beim Erstellen von *Interactable-Komponenten* zu verwenden.
>
> Es sind jedoch 17 Interaktionsfähige Zustände verfügbar, die zum Erstellen von Designs verwendet werden können, obwohl einige von anderen Komponenten gesteuert werden sollen. Im Folgenden finden Sie eine Liste mit integrierten Funktionen.
>
> * Visited(Besucht): Es wurde auf "Interactable" geklickt.
> * Umschalten: Die Schaltfläche befindet sich in einem umschalten Zustand, oder der Dimensionsindex ist eine ungerade Zahl.
> * Geste: Die Hand oder der Controller wurde gedrückt und von der ursprünglichen Position verschoben.
> * VoiceCommand: Ein Sprachbefehl wurde verwendet, um interactable auszulösen.
> * PhysicalTouch: Derzeit wird eine Toucheingabe erkannt, die zum Aktivieren [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) verwendet wird.
> * Greifen: Eine Hand greift derzeit in die Begrenzungen des Objekts, verwenden Sie , [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) um zu aktivieren.

**Aktiviert**

Umschalten, ob ein Interactable-Gerät aktiviert wird oder nicht. Dies entspricht dem [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) im Code.

Die *aktivierte Eigenschaft eines Interactable-Objekts* ist anders als die aktivierte Eigenschaft, die über GameObject/Component konfiguriert wurde (d. h. SetActive usw.). Wenn Sie GameObject oder *Interactable* MonoBehaviour deaktivieren, wird die Ausführung aller Elemente in der Klasse deaktiviert, einschließlich Eingaben, visuellen Designs, Ereignissen usw. Wenn Sie über [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) deaktivieren, wird die meisten Eingabebehandlungen deaktiviert, und die zugehörigen Eingabezustände werden zurücksetzungen. Die -Klasse wird jedoch weiterhin jeden Frame ausführen und Eingabeereignisse empfangen, die ignoriert werden. Dies ist nützlich, um interactable in einem deaktivierten Zustand anzuzeigen, der über visuelle Designs erfolgen kann. Ein typisches Beispiel hierfür wäre eine Schaltfläche zum Übermitteln, die darauf wartet, dass alle erforderlichen Eingabefelder abgeschlossen sind.

**Eingabeaktionen**

Wählen Sie die [Eingabeaktion](../input/input-actions.md) aus der Eingabekonfiguration oder dem Controllerzuordnungsprofil aus, auf die die *interaktivierbare* Komponente reagieren soll.

Diese Eigenschaft kann zur Laufzeit im Code über konfiguriert [`Interactable.InputAction`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.InputAction) werden.

**IsGlobal**

True gibt an, dass die Komponente als globaler Eingabelistener für die ausgewählte [Eingabeaktion](../input/input-actions.md)markiert wird. Das Standardverhalten ist false, wodurch die Eingabe auf diesen *interaktivierbaren* Collider/GameObject beschränkt wird.

Diese Eigenschaft kann zur Laufzeit im Code über konfiguriert [`Interactable.IsGlobal`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsGlobal) werden.

**Speech-Befehl**

[Speech-Befehl](../input/speech.md)aus dem MRTK Speech Commands Profile, um ein OnClick-Ereignis für die Sprachinteraktion auszulösen.

Diese Eigenschaft kann zur Laufzeit im Code über konfiguriert [`Interactable.VoiceCommand`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceCommand) werden.

**Erfordert Fokus**

True gibt an, dass der Sprachbefehl die *Interaktivierbare* nur aktiviert, wenn sie bereits den Fokus von einem Zeiger hat. False gibt an, dass *interactable* als globaler Listener für den ausgewählten Sprachbefehl fungiert. Das Standardverhalten ist true, da es schwierig sein kann, mehrere globale Sprachlistener in einer Szene zu organisieren.

Diese Eigenschaft kann zur Laufzeit im Code über konfiguriert [`Interactable.VoiceRequiresFocus`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceRequiresFocus) werden.

**Auswahlmodus**

Diese Eigenschaft definiert die Auswahllogik. Wenn auf *interaktivierbar* geklickt wird, wird es in eine nächste *Dimensionsebene* iteriert. *Dimensionen* ähneln dem Rang und definieren einen Zustand außerhalb von Eingaben (d. h. Fokus, Drücken usw.). Sie sind nützlich zum Definieren von Umschaltzuständen oder anderen Zuständen mit mehreren Rang, die einer Schaltfläche zugeordnet sind. Die aktuelle Dimensionsebene wird von `Interactable.DimensionIndex` nachverfolgt.

Die verfügbaren Auswahlmodi sind:

* **Schaltfläche**  -  *Dimensionen* = 1, einfach klickbar *Interagierbar*
* **Umschalten**  -  *Dimensionen* = 2, *Interagierbare Alternativen* zwischen on  / *off-Status*
* **Mehrere Dimensionen**  -  *Dimensionen* >= 3, jeder Klick erhöht die aktuelle Dimensionsebene + 1. Nützlich zum Definieren eines Schaltflächenzustands für eine Liste usw.

*Interagierbar* ermöglicht es auch, mehrere Designs pro Dimension *zu definieren.* Wenn z. B. *SelectionMode=Toggle* verwendet wird,  kann ein Design angewendet werden, wenn die Auswahl von *Interactable* aufgehoben wird, und ein anderes Design, wenn die Komponente *ausgewählt wird.*

Der aktuelle Auswahlmodus kann zur Laufzeit über abgefragt [`Interactable.ButtonMode`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.ButtonMode) werden. Sie können den Modus zur Laufzeit aktualisieren, indem Sie die  [`Interactable.Dimensions`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.Dimensions) -Eigenschaft auf die gewünschte Funktionalität festlegen. Darüber hinaus kann über auf die aktuelle Dimension zugegriffen werden, die für *den Umschaltmodus* und *den Mehrdimensionsmodus* nützlich [`Interactable.CurrentDimension`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.CurrentDimension) ist.

### <a name="interactable-profiles"></a>Interagierbare Profile

*Profile* sind Elemente, die eine Beziehung zwischen einem GameObject und einem [visuellen Design erstellen.](visual-themes.md) Das Profil definiert, welche Inhalte von einem Design bearbeitet werden, wenn eine [Zustandsänderung auftritt.](#general-input-settings)

Designs funktionieren ähnlich wie Materialien. Sie sind skriptfähige Objekte, die eine Liste von Eigenschaften enthalten, die einem Objekt basierend auf dem aktuellen Zustand zugewiesen werden. Designs sind ebenfalls wiederverfetzbar und können mehreren *Interactable* UX-Objekten zugewiesen werden.

**Reset On Destroy**

Visuelle Designs ändern verschiedene Eigenschaften für ein zielorientiertes GameObject, abhängig von der ausgewählten Klasse und dem Typ der Design-Engine. Wenn *Reset On Destroy true* ist, wenn die Interactable-Komponente zerstört wird, setzt die Komponente alle geänderten Eigenschaften von aktiven Designs auf ihre ursprünglichen Werte zurück. Andernfalls belässt die interaktivierbare Komponente alle geänderten Eigenschaften bei ihrer Zerstörung. In diesem letzteren Fall bleibt der letzte Zustand von Werten erhalten, es sei denn, er wird von einer anderen externen Komponente geändert. Die Standardeinstellung ist „false“.

<img src="../images/interactable/Profiles_Themes.png" width="450" alt="Profile theams">

## <a name="events"></a>Events

Jede *interaktivierbare* Komponente verfügt über ein *OnClick-Ereignis,* das ausgelöst wird, wenn die Komponente einfach ausgewählt wird. *Interactable* kann jedoch verwendet werden, um andere Eingabeereignisse als *nur OnClick* zu erkennen.

Klicken Sie auf die Schaltfläche *Ereignis hinzufügen,* um einen neuen Typ der Ereignisempfängerdefinition hinzuzufügen. Wählen Sie nach dem Hinzufügen den gewünschten Ereignistyp aus.

![Beispiel für Ereignisse](../images/interactable/Events.png))

Es gibt verschiedene Arten von Ereignisempfängern, um auf verschiedene Eingabetypen zu reagieren. MRTK wird mit den folgenden Empfängern ausgeliefert.

* [`InteractableAudioReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableAudioReceiver)
* [`InteractableOnClickReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnClickReceiver)
* [`InteractableOnFocusReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver)
* [`InteractableOnGrabReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnGrabReceiver)
* [`InteractableOnHoldReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnHoldReceiver)
* [`InteractableOnPressReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnPressReceiver)
* [`InteractableOnToggleReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnToggleReceiver)
* [`InteractableOnTouchReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnTouchReceiver)

Ein benutzerdefinierter Empfänger kann erstellt werden, indem eine neue Klasse erstellt wird, die [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) erweitert.

![Beispiel für ereignis umschaltende Empfänger](../images/interactable/Event_toggle.png)

*Beispiel für einen Toggle-Ereignisempfänger*

### <a name="interactable-receivers"></a>Interaktivierbare Empfänger

 Mit der [`InteractableReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiver) -Komponente können Ereignisse außerhalb der *Interaktionsquelle* definiert werden. *InteractableReceiver* lauscht auf einen gefilterten Ereignistyp, der von einem anderen *interaktivierbaren* ausgelöst wird. Wenn die *Interactable-Eigenschaft* nicht direkt zugewiesen ist, definiert die *Search Scope-Eigenschaft* die Richtung, in der *InteractableReceiver* auf Ereignisse lauscht, die sich entweder auf sich selbst, in einem übergeordneten Element oder in einem untergeordneten GameObject-Objekt befindet.

[`InteractableReceiverList`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiverList) verhält sich auf ähnliche Weise, aber für eine Liste übereinstimmender Ereignisse.

<img src="../images/interactable/InteractableReceiver.png" width="450" alt="Interactable reciver">

### <a name="create-custom-events"></a>Erstellen benutzerdefinierter Ereignisse

Wie [visuelle Designs](visual-themes.md#custom-theme-engines)können Ereignisse erweitert werden, um beliebige Zustandsmuster zu erkennen oder Funktionen verfügbar zu machen.

Benutzerdefinierte Ereignisse können auf zwei Arten erstellt werden:

1) Erweitern Sie [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) die -Klasse, um ein benutzerdefiniertes Ereignis zu erstellen, das in der Dropdownliste der Ereignistypen angezeigt wird. Standardmäßig wird ein Unity-Ereignis bereitgestellt, es können jedoch weitere Unity-Ereignisse hinzugefügt oder das Ereignis so festgelegt werden, dass Unity-Ereignisse ausblendet werden. Diese Funktionalität ermöglicht es einem Designer, mit einem Techniker an einem Projekt zu arbeiten, um ein benutzerdefiniertes Ereignis zu erstellen, das der Designer im Editor einrichten kann.

1) Erweitern Sie [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) die -Klasse, um eine vollständig benutzerdefinierte Ereigniskomponente zu erstellen, die sich im *Interactable-Objekt* oder einem anderen -Objekt befinden kann. verweist [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) auf *interactable,* um Zustandsänderungen zu erkennen.

#### <a name="example-of-extending-receiverbase"></a>Beispiel für die Erweiterung `ReceiverBase`

Die -Klasse zeigt Statusinformationen zu einem Interactable-Ereignis an und ist ein Beispiel für das Erstellen eines [`CustomInteractablesReceiver`](xref:Microsoft.MixedReality.Toolkit.UI) benutzerdefinierten Ereignisempfängers. 

```c#
public CustomInteractablesReceiver(UnityEvent ev) : base(ev, "CustomEvent")
{
    HideUnityEvents = true; // hides Unity events in the receiver - meant to be code only
}
```

Die folgenden Methoden sind nützlich, um beim Erstellen eines benutzerdefinierten Ereignisempfängers zu überschreiben/zu implementieren. [`ReceiverBase.OnUpdate()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) ist eine abstrakte Methode, die verwendet werden kann, um Zustandsmuster/Übergänge zu erkennen. Darüber hinaus sind die [`ReceiverBase.OnVoiceCommand()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) Methoden und [`ReceiverBase.OnClick()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) nützlich, um benutzerdefinierte Ereignislogik zu erstellen, wenn *Interactable* ausgewählt ist.

```c#
public override void OnUpdate(InteractableStates state, Interactable source)
{
    if (state.CurrentState() != lastState)
    {
        // the state has changed, do something new
        lastState = state.CurrentState();
        ...
    }
}

public virtual void OnVoiceCommand(InteractableStates state, Interactable source,
                                    string command, int index = 0, int length = 1)
{
    base.OnVoiceCommand(state, source, command, index, length);
    // voice command called, perform some action
}  

public virtual void OnClick(InteractableStates state,
                            Interactable source,
                            IMixedRealityPointer pointer = null)
{
    base.OnClick(state, source);
    // click called, perform some action
}
```

##### <a name="displaying-custom-event-receiver-fields-in-the-inspector"></a>Anzeigen benutzerdefinierter Ereignisempfängerfelder im Inspektor

*ReceiverBase-Skripts* [`InspectorField`](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.InspectorField) verwenden Attribute, um benutzerdefinierte Eigenschaften im Inspektor verfügbar zu machen. Hier sehen Sie ein Beispiel für Vector3, eine benutzerdefinierte Eigenschaft mit QuickInfo und Bezeichnungsinformationen. Diese Eigenschaft wird im Inspektor als konfigurierbar angezeigt, wenn ein *Interactable* GameObject ausgewählt ist und der zugeordnete *Ereignisempfängertyp* hinzugefügt wird.

```c#
[InspectorField(Label = "<Property label>",Tooltip = "<Insert tooltip info>",Type = InspectorField.FieldTypes.Vector3)]
public Vector3 EffectOffset = Vector3.zero;
```

## <a name="how-to-use-interactable"></a>Verwenden von Interactable

### <a name="building-a-simple-button"></a>Erstellen einer einfachen Schaltfläche

Sie können eine einfache Schaltfläche erstellen, indem Sie die *Interactable-Komponente* einem GameObject hinzufügen, das für den Empfang von Eingabeereignissen konfiguriert ist. Es kann ein Collider darauf oder auf einem untergeordneten -Paar zum Empfangen von Eingaben verfügen. Wenn Sie *Interactable mit* einem auf der Unity-Benutzeroberfläche basierenden GameObjects verwenden, sollte es sich unter dem Canvas GameObject-Objekt befindet.

Gehen Sie mit der Schaltfläche noch einen Schritt weiter, indem Sie ein neues Profil erstellen, das GameObject selbst zuweisen und ein neues Design erstellen. Verwenden Sie darüber hinaus das *OnClick-Ereignis,* um etwas zu bewirken.

> [!NOTE]
> Damit eine [Schaltfläche gedrückt werden kann,](button.md) ist die [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) Komponente erforderlich. Darüber hinaus wird die [`PhysicalPressEventRouter`](xref:Microsoft.MixedReality.Toolkit.PhysicalPressEventRouter) -Komponente benötigt, um Ereignisse zur *Interaktivierbaren* Komponente zu trichtern.

### <a name="creating-toggle-and-multi-dimension-buttons"></a>Erstellen von Umschaltflächen und Schaltflächen mit mehreren Dimensionen

#### <a name="toggle-button"></a>Umschalter

Um eine Schaltfläche umschaltfähig zu machen, ändern Sie das [`Selection Mode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) Feld in den Typ `Toggle` . Im Abschnitt *Profile* wird ein neues umgeschaltetes Design für jedes Profil hinzugefügt, das verwendet wird, wenn *interaktivierbar* eingeschaltet wird.

Während auf [`SelectionMode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) Umschalten festgelegt ist, kann das *Kontrollkästchen IsToggled* verwendet werden, um den Standardwert des Steuerelements bei der Laufzeitinitialisierung festzulegen.

*CanSelect* bedeutet, dass *interactable* von *aus* zu *eins* wechseln kann, während *CanDeselect* die Umkehrung bedeutet.

![Beispiel für visuelle Designs zum Umschalten von Profilen](../images/interactable/Profile_toggle.png)

Entwickler können die [`SetToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) Schnittstellen und [`IsToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) verwenden, um den Umschaltzustand eines *Interaktivierbaren* über Code abzurufen bzw. festzulegen.

```c#
// If using SelectionMode = Toggle (i.e Dimensions == 2)

// Make the Interactable selected and toggled on
myInteractable.IsToggled = true;

// Get whether the Interactable is selected or not
bool isSelected = myInteractable.IsToggled;
```

##### <a name="toggle-button-collection"></a>Schaltflächensammlung umschalten

Es ist üblich, eine Liste von Umschaltflächen zu verwenden, bei denen nur eine zu einem bestimmten Zeitpunkt aktiv sein kann. Dies wird auch als radiale Gruppe oder Optionsfelder usw. bezeichnet.

Verwenden Sie die [`InteractableToggleCollection`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableToggleCollection) -Komponente, um diese Funktionalität zu aktivieren. Dieses Steuerelement stellt sicher, dass immer nur ein *Interaktivierbarer* eingeschaltet wird. *RadialSet* (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/RadialSet.prefab) ist ebenfalls ein idealer Ausgangspunkt.

So erstellen Sie eine benutzerdefinierte radiale Schaltflächengruppe:

1) Erstellen mehrerer *interaktivierbarer* GameObjects/Schaltflächen
1) Legen Sie jedes *Interaktivierbare* mit *SelectionMode* = Umschalten, *CanSelect* = true und *CanDeselect* = false fest.
1) Erstellen Sie ein leeres übergeordnetes GameObject für alle *Interactables,* und fügen Sie die *InteractableToggleCollection-Komponente* hinzu.
1) Hinzufügen aller *Interaktivierbaren* zu *ToggleList* in *interactableToggleCollection*
1) Legen Sie die *InteractableToggleCollection.CurrentIndex-Eigenschaft* fest, um zu bestimmen, welche Schaltfläche beim Start standardmäßig ausgewählt ist.

<img src="../images/interactable/InteractableToggleCollection.png" width="450" alt="Toggle collection">

#### <a name="multi-dimensional-button"></a>Mehrdimensionale Schaltfläche

Der Auswahlmodus für mehrere Dimensionen wird verwendet, um sequenzielle Schaltflächen oder eine Schaltfläche mit mehr als zwei Schritten zu erstellen, z. B. das Steuern der Geschwindigkeit mit drei Werten, Fast (1x), Faster (2x) oder Fastest (3x).

Wenn Dimensionen ein numerischer Wert sind, können bis zu 9 Designs hinzugefügt werden, um die Textbezeichnung oder Textur der Schaltfläche für jede Geschwindigkeitseinstellung mit einem anderen Design für jeden Schritt zu steuern.

Jedes Klickereignis bewegt sich zur Laufzeit `DimensionIndex` um 1, bis `Dimensions` der Wert erreicht ist. Anschließend wird der Zyklus auf 0 zurückgesetzt.

![Beispiel für ein mehrdimensionales Profil](../images/interactable/Profile_multiDimensions.png)

Entwickler können bewerten, [`DimensionIndex`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) um zu bestimmen, welche Dimension derzeit aktiv ist.

```c#
// If using SelectionMode = Multi-dimension (i.e Dimensions >= 3)

//Access the current DimensionIndex
int currentDimension = myInteractable.CurrentDimension;

//Set the current DimensionIndex to 2
myInteractable.CurrentDimension = 2;

// Promote Dimension to next level
myInteractable.IncreaseDimension();
```

### <a name="create-interactable-at-runtime"></a>Erstellen von Interactable zur Laufzeit

*Interactable* kann jedem GameObject zur Laufzeit problemlos hinzugefügt werden. Im folgenden Beispiel wird veranschaulicht, wie ein Profil mit einem visuellen [Design zugewiesen wird.](visual-themes.md)

```c#
var interactableObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
var interactable = interactableObject.AddComponent<Interactable>();

// Get the default configuration for the Theme engine InteractableColorTheme
var newThemeType = ThemeDefinition.GetDefaultThemeDefinition<InteractableColorTheme>().Value;

// Define a color for every state in our Default Interactable States
newThemeType.StateProperties[0].Values = new List<ThemePropertyValue>()
{
    new ThemePropertyValue() { Color = Color.black},  // Default
    new ThemePropertyValue() { Color = Color.black}, // Focus
    new ThemePropertyValue() { Color = Random.ColorHSV()},   // Pressed
    new ThemePropertyValue() { Color = Color.black},   // Disabled
};

interactable.Profiles = new List<InteractableProfileItem>()
{
    new InteractableProfileItem()
    {
        Themes = new List<Theme>()
        {
            Interactable.GetDefaultThemeAsset(new List<ThemeDefinition>() { newThemeType })
        },
        Target = interactableObject,
    },
};

// Force the Interactable to be clicked
interactable.TriggerOnClick()
```

### <a name="interactable-events-via-code"></a>Interagierbare Ereignisse über Code

Mit dem folgenden Beispiel können Sie dem [`Interactable.OnClick`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.OnClick) Basisereignis über Code eine Aktion hinzufügen.

```c#
public static void AddOnClick(Interactable interactable)
{
    interactable.OnClick.AddListener(() => Debug.Log("Interactable clicked"));
}
```

Verwenden Sie [`Interactable.AddReceiver<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) die -Funktion, um Ereignisempfänger dynamisch zur Laufzeit hinzuzufügen.

Der folgende Beispielcode veranschaulicht, wie Ein [InteractableOnFocusReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver)hinzugefügt wird, der auf fokusfähige Eingabe/Beendigung lausiert und darüber hinaus Aktionscode definiert, der beim Auftreten der Ereignisinstanzen verwendet werden soll.

```c#
public static void AddFocusEvents(Interactable interactable)
{
    var onFocusReceiver = interactable.AddReceiver<InteractableOnFocusReceiver>();

    onFocusReceiver.OnFocusOn.AddListener(() => Debug.Log("Focus on"));
    onFocusReceiver.OnFocusOff.AddListener(() => Debug.Log("Focus off"));
}
```

Der folgende Beispielcode veranschaulicht, wie ein [InteractableOnToggleReceiver-Element](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver)hinzugefügt wird, das auf ausgewählte/deaktivierte Zustandsübergänge für umschaltbare *Interactables-Elemente* lauselt und darüber hinaus aktionscode definiert, der beim Auftreten der Ereignisinstanzen durchzuführen ist.

```c#
public static void AddToggleEvents(Interactable interactable)
{
    var toggleReceiver = interactable.AddReceiver<InteractableOnToggleReceiver>();

    // Make the interactable have toggle capability, from code.
    // In the gui editor it's much easier
    interactable.Dimensions = 2;
    interactable.CanSelect = true;
    interactable.CanDeselect  = true;

    toggleReceiver.OnSelect.AddListener(() => Debug.Log("Toggle selected"));
    toggleReceiver.OnDeselect.AddListener(() => Debug.Log("Toggle un-selected"));
}
```

## <a name="see-also"></a>Weitere Informationen

* [Visuelle Designs](visual-themes.md)
* [Eingabeaktionen](../input/input-actions.md)
* [Speech-Befehle](../input/speech.md)
* [Schaltflächen](button.md)
* [MRTK-Standard-Shader](../rendering/MRTK-standard-shader.md)
