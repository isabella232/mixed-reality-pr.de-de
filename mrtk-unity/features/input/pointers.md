---
title: Zeiger
description: Dokumentation zu Zeigern in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Zeiger,
ms.openlocfilehash: 9fec02e7866aaf867c7145491bfd84f727e039cdd7a4323ace9c65f74e49480a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115190978"
---
# <a name="pointers"></a>Zeiger

![Zeiger](../images/pointers/MRTK_Pointer_Main.png)

In diesem Artikel wird erläutert, wie Zeigereingaben in der Praxis im Vergleich zur [Zeigerarchitektur](../../architecture/controllers-pointers-and-focus.md) konfiguriert und darauf reagiert werden.

Zeiger werden zur Laufzeit automatisch instanziert, wenn ein neuer Controller erkannt wird. An einen Controller können mehrere Zeiger angefügt werden. Beispielsweise erhalten Windows Mixed Reality Controller mit dem Standardzeigerprofil sowohl eine Linie als auch einen parabolischen Zeiger für die normale Auswahl bzw. Teleportierung.

## <a name="pointer-configuration"></a>Zeigerkonfiguration

Zeiger werden als Teil des Eingabesystems in MRTK über eine [`MixedRealityPointerProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile) konfiguriert. Dieser Profiltyp wird einem [`MixedRealityInputSystemProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSystemProfile) im MRTK-Konfigurationsinspektor zugewiesen. Das Zeigerprofil bestimmt den Cursor, typen von Zeigern, die zur Laufzeit verfügbar sind, und wie diese Zeiger miteinander kommunizieren, um zu entscheiden, welcher aktiv ist.

- *Zeigender Umfang:* Definiert den maximalen Abstand, für den ein Zeiger mit einem GameObject interagieren kann.

- *Verweisen auf Raycast-Ebenenmasken: Dies* ist ein priorisiertes Array von LayerMasks, um zu bestimmen, mit welchen möglichen GameObjects ein beliebiger Zeiger interagieren kann, und die Reihenfolge der Interaktion, die versucht werden soll. Dies kann hilfreich sein, um sicherzustellen, dass Zeiger zuerst vor anderen Szenenobjekten mit Benutzeroberflächenelementen interagieren.
![Beispiel für Zeigerprofil](../images/input/pointers/PointerProfile.PNG)

### <a name="pointer-options-configuration"></a>Konfiguration von Zeigeroptionen

Die STANDARDMÄßIGE MRTK-Zeigerprofilkonfiguration umfasst die folgenden Zeigerklassen und zugeordneten Prefabs standardmäßig. Die Liste der Zeiger, die zur Laufzeit für das System verfügbar sind, wird unter *Zeigeroptionen* im Zeigerprofil definiert. Entwickler können diese Liste verwenden, um vorhandene Zeiger neu zu konfigurieren, neue Zeiger hinzuzufügen oder einen zu löschen.

![Beispiel für Zeigeroptionenprofil](../images/input/pointers/PointerOptionsProfile.PNG)

Jeder Zeigereintrag wird durch den folgenden Satz von Daten definiert:

- *Controllertyp:* Die Gruppe von Controllern, für die ein Zeiger gültig ist.
  - So ist beispielsweise *Der Zunftpunkter* für das "Zeichnen" von Objekten mit einem Finger verantwortlich und standardmäßig als nur für die Unterstützung des artikulierten Handcontrollertyps gekennzeichnet. Zeiger werden nur instanziiert, wenn ein Controller verfügbar wird und insbesondere der *Controllertyp* definiert, mit welchen Controllern dieses Zeigerpräfab erstellt werden kann.

- *Handkraft:* Ermöglicht, dass ein Zeiger auf nur für eine bestimmte Hand instanziiert wird (links/rechts).

> [!NOTE]
> Wenn Sie die *Eigenschaft "Handkraft"* eines Zeigereintrags auf *"None"* festlegen, wird sie im System als Alternative zum Entfernen dieses Zeigers aus der Liste deaktiviert.

- *Zeigerpräfab:* Dieses Prefab-Medienobjekt wird instanziiert, wenn ein Controller, der dem angegebenen Controllertyp entspricht, und die Übergabe nachverfolgt wird.

Es ist möglich, einem Controller mehrere Zeiger zuzuordnen. Beispiel: In `DefaultHoloLens2InputSystemProfile` (Assets/MRTK/SDK/Profiles/HoloLens2/) ist der artikulierte Handcontroller mit dem *Zusteller*, dem *GrabPointer* und dem *DefaultControllerPointer* (d.h. Handlichtstrahl).

> [!NOTE]
> MRTK stellt einen Satz von Zeigerpräfabs in *Assets/MRTK/SDK/Features/UX/Prefabs/Pointers bereit.* Ein neues benutzerdefiniertes Prefab kann erstellt werden, solange es eines der Zeigerskripts in *Assets/MRTK/SDK/Features/UX/Scripts/Pointers* oder ein anderes Skript enthält, das [`IMixedRealityPointer`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer) implementiert.

### <a name="default-pointer-classes"></a>Standardzeigerklassen

Die folgenden Klassen sind die standardmäßig verfügbaren MRTK-Zeiger, die im oben beschriebenen *MRTK-Standardzeigerprofil* definiert sind. Jedes unter *Assets/MRTK/SDK/Features/UX/Prefabs/Pointers bereitgestellte Zeiger-Prefab* enthält eine der angefügten Zeigerkomponenten.

![MRTK-Standardzeiger](../images/input/pointers/MRTK_Pointers.png)

#### <a name="far-pointers"></a>Fernzeiger

##### [`LinePointer`](xref:Microsoft.MixedReality.Toolkit.Input.LinePointer)

 *LinePointer*, eine Basiszeigerklasse, zeichnet eine Linie aus der Quelle der Eingabe (d. h. dem Controller) in Zeigerrichtung und unterstützt einen einzelnen Strahl in dieser Richtung. Im Allgemeinen werden untergeordnete Klassen wie und [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) die Teleportzeiger instanziiert und verwendet (die auch Linien zeichnen, um anzugeben, wo die Teleportierung enden wird) anstatt dieser Klasse, die in erster Linie allgemeine Funktionen bereitstellt.

Bei Motion-Controllern wie Oculus, Vive und Windows Mixed Reality entspricht die Drehung der Drehung des Controllers. Bei anderen Controllern wie HoloLens 2 artikulierten Händen entspricht die Drehung der vom System bereitgestellten zeigenden Position der Hand.

<img src="../images/pointers/MRTK_Pointers_Line.png" width="400" alt="MRTK Pointer Line">

##### [`CurvePointer`](xref:Microsoft.MixedReality.Toolkit.Input.CurvePointer)

*CurvePointer* erweitert die *LinePointer-Klasse,* indem mehrstufige Raycasts entlang einer Kurve ermöglicht werden. Diese Basiszeigerklasse eignet sich für gekrümmte Instanzen, z. B. Teleportierungszeiger, bei denen die Linie konsistent in eine Parabel zerrend wird.

##### [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer)

Die Implementierung von *ShellHandRayPointer*, die von erweitert [`LinePointer`](xref:Microsoft.MixedReality.Toolkit.Input.MousePointer) wird, wird als Standard für das *MRTK-Zeigerprofil* verwendet. Das *DefaultControllerPointer-Prefab* implementiert die [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) -Klasse.

##### [`GGVPointer`](xref:Microsoft.MixedReality.Toolkit.Input.GGVPointer)

Der GGVPointer wird auch als *GGV-Zeiger (Gaze/Gesture/Voice)* bezeichnet und unterstützt HoloLens 1-seitigen Look-and-Tap-Interaktionen, hauptsächlich über Anvisieren und Tippen in die Luft oder Interaktion mit Anvisieren und Sprachauswahl. Position und Richtung des GGV-Zeigers werden durch die Position und Drehung des Kopfs gesteuert.

##### [`TouchPointer`](xref:Microsoft.MixedReality.Toolkit.Input.TouchPointer)

*TouchPointer* ist für die Arbeit mit der Unity Touch-Eingabe (d.h. Touchscreen) verantwortlich. Dies sind "ferne Interaktionen", da durch das Berühren des Bildschirms ein Strahl von der Kamera in eine potenziell weit entfernte Position in der Szene geworfen wird.

##### [`MousePointer`](xref:Microsoft.MixedReality.Toolkit.Input.MousePointer)

Der *MousePointer* treibt einen Bildschirm für Ferninteraktionen, aber für Maus anstelle von Toucheingabe zum World Raycast.

![Mauszeiger](../images/pointers/MRTK_MousePointer.png)

> [!NOTE]
> Mausunterstützung ist im MRTK standardmäßig nicht verfügbar, kann jedoch aktiviert werden, indem dem MRTK-Eingabeprofil eine neue *Eingabe-Datenanbieter* vom Typ hinzugefügt [`MouseDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) und dem Datenanbieter zugewiesen [`MixedRealityMouseInputProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityMouseInputProfile) wird.

#### <a name="near-pointers"></a>Zeiger in der Nähe

##### [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer)

*[Der PointePointer](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer)* wird verwendet, um mit Spielobjekten zu interagieren, die "nah anstreifbare Interaktionen" unterstützen. Dies sind GameObjects, die über ein angefügtes [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) Skript verfügen. Im Fall von UnityUI sucht dieser Zeiger nach NearInteractionTouchableUnityUIs.  Der BedePointer verwendet einen SphereCast, um das nächstgelegene touchierbare Element zu bestimmen, und wird verwendet, um Dinge wie die drückbaren Schaltflächen zu schalten.

 Stellen Sie beim Konfigurieren des GameObject-Objekts mit der [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) -Komponente sicher, dass Sie den *localForward-Parameter* so konfigurieren, dass er auf die Vorderseite der Schaltfläche oder auf ein anderes Objekt verweist, das anstreifbar gemacht werden soll. Stellen Sie außerdem sicher, dass die *Begrenzungen* des touchierbaren Objekts mit den Begrenzungen des touchierbaren Objekts übereinstimmen.

Nützliche Eigenschaften des Zeigerzeigers:

- *TouchableDistance:* Maximaler Abstand, in dem eine touchierbare Oberfläche interagiert werden kann
- *Visuals:* Spielobjekt, das zum Rendern von Fingertippvisuals verwendet wird (standardmäßig der Ring am Finger).
- *Linie:* Optionale Linie, die von der Fingerspitze auf die aktive Eingabeoberfläche gezeichnet werden soll.
- *Layer Masks* :Ein priorisiertes Array von LayerMasks, um zu bestimmen, mit welchen möglichen GameObjects der Zeiger interagieren kann, und die Reihenfolge der Interaktion, die versucht werden soll. Beachten Sie, dass ein GameObject auch über eine -Komponente verfügen `NearInteractionTouchable` muss, um mit einem Mauszeiger zu interagieren.

<img src="../images/pointers/MRTK_PokePointer.png" width="400" alt="Poke Pointer">

##### [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer)

*[SpherePointer](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer)* verwendet [UnityEngine.Physics.OverlapSphere,](https://docs.unity3d.com/ScriptReference/Physics.OverlapSphere.html) um das nächstgelegene Objekt für die Interaktion zu identifizieren. Dies [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) ist nützlich für "greifbare" Eingaben wie `ManipulationHandler` . Ähnlich wie beim [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) / [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) Funktionspaar muss das Spielobjekt eine Komponente enthalten, die das Skript ist, um mit dem Kugelzeiger interagieren zu [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) können.

<img src="../images/pointers/MRTK_GrabPointer.jpg" width="400" alt="Grab Pointer">

Nützliche Sphere-Zeigereigenschaften:

- *Kugel-Umwandlungsradius:* Der Radius für die Kugel, die zum Abfragen von gierbaren Objekten verwendet wird.
- *Near Object Margin (Nahes Objektrand):* Der Abstand über dem Kugel-Umwandlungsradius, der abgefragt werden soll, um zu ermitteln, ob sich ein Objekt in der Nähe des Zeigers befindet. Erkennungsradius des gesamten near-Objekts entspricht Sphere Cast Radius + Near Object Margin
- *Near Object Sector Angle*:Der Winkel um die Vorwärtsachse des Zeigers zum Abfragen von Objekten in der Nähe. Macht die `IsNearObject` Abfragefunktion wie einen Kegel. Dies ist standardmäßig auf 66 Grad festgelegt, um dem Hololens 2-Verhalten zu entsprechen.

![Kugelzeiger geändert, um nur Objekte in Vorwärtsrichtung abzufragen](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

- *Near Object Smoothing Factor*: Glättungsfaktor für die Near Object-Erkennung. Wenn ein Objekt im Near Object Radius erkannt wird, wird der abgefragte Radius zu Near Object Radius * (1 + Near Object Smoothing Factor), um die Empfindlichkeit zu reduzieren und es für ein Objekt schwieriger zu machen, den Erkennungsbereich zu verlassen.
- *Grab Layer Masks* : Ein priorisiertes Array von LayerMasks, um zu bestimmen, mit welchen möglichen GameObjects der Zeiger interagieren kann, und die Reihenfolge der Interaktion, die versucht werden soll. Beachten Sie, dass ein GameObject auch über ein -Objekt verfügen `NearInteractionGrabbable` muss, um mit einem SpherePointer zu interagieren.
    > [!NOTE]
    > Die Spatial Awareness-Ebene ist im standardmäßigen GrabPointer-Prefab deaktiviert, das vom MRTK bereitgestellt wird. Dies wird durchgeführt, um die Auswirkungen einer Kugelüberlappungsabfrage mit dem räumlichen Gitternetz auf die Leistung zu reduzieren. Sie können dies aktivieren, indem Sie das GrabPointer-Prefab ändern.
- *Collider ignorieren Nicht in FOV:* Gibt an, ob Collider ignoriert werden sollen, die sich möglicherweise in der Nähe des Zeigers, aber nicht tatsächlich im visuellen FOV-Bereich befindet.
Dies kann versehentliches Greifen verhindern und das Einschalten von Handlicht ermöglichen, wenn Sie sich möglicherweise in der Nähe eines Grabbings, aber nicht sehen können. *Visual FOV* wird aus Leistungsgründen über einen Kegel anstelle des typischen Frustums definiert. Dieser Kegel ist zentriert und gleich ausgerichtet wie das Frustum der Kamera mit einem Radius, der der halben Anzeigehöhe (oder vertikalen FOV) entspricht.

<img src="../images/input/pointers/SpherePointer_VisualFOV.png" width="200" alt="Sphere Pointer">

#### <a name="teleport-pointers"></a>Teleportzeiger

- [`TeleportPointer`](xref:Microsoft.MixedReality.Toolkit.Teleport.TeleportPointer) wird eine Teleportanforderung auslösen, wenn eine Aktion ausgeführt wird (d.h. Die Teleportschaltfläche wird gedrückt), um den Benutzer zu verschieben.
- [`ParabolicTeleportPointer`](xref:Microsoft.MixedReality.Toolkit.Teleport.ParabolicTeleportPointer) wird eine Teleportanforderung auslösen, wenn eine Aktion ausgeführt wird (d.h. die Teleportschaltfläche gedrückt wird) mit einem Parabollinien-Raycast, um den Benutzer zu verschieben.

<img src="../images/pointers/MRTK_Pointers_Parabolic.png" width="400" alt="Pointer Parabolic">

## <a name="pointer-support-for-mixed-reality-platforms"></a>Zeigerunterstützung für Mixed Reality-Plattformen

In der folgenden Tabelle sind die Zeigertypen aufgeführt, die in der Regel für die gängigen Plattformen im MRTK verwendet werden. HINWEIS: Es ist möglich, diesen Plattformen verschiedene Zeigertypen hinzuzufügen. Sie können z. B. einen Zeiger vom Tarif "Zeiger" oder "Kugel" zu VR hinzufügen. Darüber hinaus können VR-Geräte mit einem Gamepad den GGV-Zeiger verwenden.

|       Zeiger              | OpenVR  | Windows Mixed Reality | HoloLens 1 | HoloLens 2 |
|---------------------|---------|-----------------------|------------|------------|
| ShellHandRayPointer | Gültig   | Gültig                 |            | Gültig      |
| TeleportPointer     | Gültig   | Gültig                 |            |            |
| GGVPointer          |         |                       | Gültig      |            |
| SpherePointer       |         |                       |            | Gültig      |
| PointePointer         |         |                       |            | Gültig      |

## <a name="pointer-interactions-via-code"></a>Zeigerinteraktionen über Code

### <a name="pointer-event-interfaces"></a>Zeigerereignisschnittstellen

MonoBehaviours, die eine oder mehrere der folgenden Schnittstellen implementieren und einem GameObject mit einem zugewiesen sind, `Collider` empfangen Zeigerinteraktionen, wie von der zugeordneten Schnittstelle definiert.

| Ereignis | Beschreibung | Handler |
| --- | --- | --- |
| Vor der Änderung des Fokus/Fokus geändert | Wird sowohl für das Spielobjekt ausgelöst, das den Fokus verliert, als auch für das Objekt, das den Fokus jedes Mal erhält, wenn ein Zeiger den Fokus ändert. | [`IMixedRealityFocusChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusChangedHandler) |
Fokuseingabe/-beendigung | Wird ausgelöst, wenn das Spielobjekt den Fokus erhält, wenn der erste Zeiger in ihn eintritt, und auf den, der den Fokus verliert, wenn der letzte Zeiger ihn verlässt. | [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler)
Zeiger nach unten/gezogen/nach oben/Klick | Wird ausgelöst, um den Berichtszeiger zu drücken, ziehen Und loslassen. | [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler)
Toucheingabe gestartet/aktualisiert/abgeschlossen | Wird von touchfähigen Zeigern wie [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) ausgelöst, um Touchaktivitäten zu melden. | [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)

> [!NOTE]
> [`IMixedRealityFocusChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusChangedHandler) und [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler) sollten in den Objekten behandelt werden, für die sie ausgelöst werden. Es ist möglich, Fokusereignisse global zu empfangen, aber im Gegensatz zu anderen Eingabeereignissen blockiert der globale Ereignishandler den Empfang von Ereignissen nicht basierend auf dem Fokus (das Ereignis wird sowohl vom globalen Handler als auch von einem entsprechenden Objekt im Fokus empfangen).

#### <a name="pointer-input-events-in-action"></a>Zeigereingabeereignisse in Aktion

Zeigereingabeereignisse werden vom MRTK-Eingabesystem auf ähnliche Weise erkannt und behandelt wie [reguläre Eingabeereignisse.](input-events.md#input-events-in-action) Der Unterschied ist, dass Zeigereingabeereignisse nur vom GameObject im Fokus vom Zeiger, der das Eingabeereignis ausgelöst hat, sowie von allen globalen Eingabehandlern behandelt werden. Reguläre Eingabeereignisse werden von GameObjects im Fokus für alle aktiven Zeiger behandelt.

1. Das MRTK-Eingabesystem erkennt, dass ein Eingabeereignis aufgetreten ist.
1. Das MRTK-Eingabesystem löst die relevante Schnittstellenfunktion für das Eingabeereignis für alle registrierten globalen Eingabehandler aus.
1. Das Eingabesystem bestimmt, welches GameObject sich im Fokus für den Zeiger befindet, der das Ereignis ausgelöst hat.
    1. Das Eingabesystem verwendet das [Unity-Ereignissystem,](https://docs.unity3d.com/Manual/EventSystem.html) um die relevante Schnittstellenfunktion für alle übereinstimmenden Komponenten auf dem fokussierten GameObject auszuspielen.
    1. Wenn ein Eingabeereignis zu einem beliebigen Zeitpunkt [als verwendet markiert](input-events.md#how-to-stop-input-events)wurde, wird der Prozess beendet, und keine weiteren GameObjects erhalten Rückrufe.
        - Beispiel: Komponenten, die die Schnittstelle [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) implementieren, werden nach einem GameObject gesucht, das den Fokus erhält oder verliert.
        - Hinweis: Das Unity-Ereignissystem führt eine Blase durch, um das übergeordnete GameObject zu durchsuchen, wenn im aktuellen GameObject keine Komponenten gefunden werden, die der gewünschten Schnittstelle entsprechen.
1. Wenn keine globalen Eingabehandler registriert sind und kein GameObject mit einer übereinstimmenden Komponente/Schnittstelle gefunden wird, ruft das Eingabesystem jeden registrierten Fallbackeingabehandler auf.

#### <a name="example"></a>Beispiel

Im Folgenden finden Sie ein Beispielskript, das die Farbe des angefügten Renderers ändert, wenn ein Zeiger den Fokus übernimmt oder verlässt oder wenn ein Zeiger das Objekt auswählt.

```c#
public class ColorTap : MonoBehaviour, IMixedRealityFocusHandler, IMixedRealityPointerHandler
{
    private Color color_IdleState = Color.cyan;
    private Color color_OnHover = Color.white;
    private Color color_OnSelect = Color.blue;
    private Material material;

    private void Awake()
    {
        material = GetComponent<Renderer>().material;
    }

    void IMixedRealityFocusHandler.OnFocusEnter(FocusEventData eventData)
    {
        material.color = color_OnHover;
    }

    void IMixedRealityFocusHandler.OnFocusExit(FocusEventData eventData)
    {
        material.color = color_IdleState;
    }

    void IMixedRealityPointerHandler.OnPointerDown(
         MixedRealityPointerEventData eventData) { }

    void IMixedRealityPointerHandler.OnPointerDragged(
         MixedRealityPointerEventData eventData) { }

    void IMixedRealityPointerHandler.OnPointerClicked(MixedRealityPointerEventData eventData)
    {
        material.color = color_OnSelect;
    }
}
```

### <a name="query-pointers"></a>Abfragezeiger

Es ist möglich, alle aktuell aktiven Zeiger zu erfassen, indem Sie die verfügbaren Eingabequellen durchlaufen (d. h. Controller und Eingaben verfügbar), um zu ermitteln, welche Zeiger an sie angefügt sind.

```c#
var pointers = new HashSet<IMixedRealityPointer>();

// Find all valid pointers
foreach (var inputSource in CoreServices.InputSystem.DetectedInputSources)
{
    foreach (var pointer in inputSource.Pointers)
    {
        if (pointer.IsInteractionEnabled && !pointers.Contains(pointer))
        {
            pointers.Add(pointer);
        }
    }
}
```

#### <a name="primary-pointer"></a>Primärer Zeiger

Entwickler können das FocusProviders PrimaryPointerChanged-Ereignis abonnieren, um benachrichtigt zu werden, wenn sich der primäre Zeiger im Fokus geändert hat. Dies kann äußerst nützlich sein, um zu ermitteln, ob der Benutzer derzeit über Anvieren, Handstrahl oder eine andere Eingabequelle mit einer Szene interagiert.

```c#
private void OnEnable()
{
    var focusProvider = CoreServices.InputSystem?.FocusProvider;
    focusProvider?.SubscribeToPrimaryPointerChanged(OnPrimaryPointerChanged, true);
}

private void OnPrimaryPointerChanged(IMixedRealityPointer oldPointer, IMixedRealityPointer newPointer)
{
    ...
}

private void OnDisable()
{
    var focusProvider = CoreServices.InputSystem?.FocusProvider;
    focusProvider?.UnsubscribeFromPrimaryPointerChanged(OnPrimaryPointerChanged);

    // This flushes out the current primary pointer
    OnPrimaryPointerChanged(null, null);
}
```

Die `PrimaryPointerExample` Szene (Assets/MRTK/Examples/Demos/Input/Scenes/PrimaryPointer) zeigt, wie sie für Ereignisse verwendet, [`PrimaryPointerChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.PrimaryPointerChangedHandler) um auf einen neuen primären Zeiger zu reagieren.

<img src="../images/pointers/PrimaryPointerExample.png" style="max-width:100%;" alt="Primary Pointer Example">

### <a name="pointer-result"></a>Zeigerergebnis

Die [`Result`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer.Result) Zeigereigenschaft enthält das aktuelle Ergebnis für die Szenenabfrage, die verwendet wird, um das Objekt mit Fokus zu bestimmen. Für einen Raycastzeiger, wie bei den standardmäßig für Motion-Controller erstellten, Anvisieren-Eingaben und Handlichtlichten, enthält er die Position und die Normalität des Raycasttreffers.

```c#
private void IMixedRealityPointerHandler.OnPointerClicked(MixedRealityPointerEventData eventData)
{
    var result = eventData.Pointer.Result;
    var spawnPosition = result.Details.Point;
    var spawnRotation = Quaternion.LookRotation(result.Details.Normal);
    Instantiate(MyPrefab, spawnPosition, spawnRotation);
}
```

Die `PointerResultExample` Szene (Assets/MRTK/Examples/Demos/Input/Scenes/PointerResult/PointerResultExample.unity) zeigt, wie der Zeiger [`Result`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer.Result) verwendet wird, um ein Objekt an der Trefferposition zu erstellen.

<img src="../images/input/PointerResultExample.png" style="max-width:100%;" alt="Pointer Result">

### <a name="disable-pointers"></a>Deaktivieren von Zeigern

Um Zeiger zu aktivieren und zu deaktivieren (z. B. um den Handstrahl zu deaktivieren), legen Sie [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) für einen bestimmten Zeigertyp über [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) fest.

```c#
// Disable the hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff);

// Disable hand rays for the right hand only
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Right);

// Disable the gaze pointer
PointerUtils.SetGazePointerBehavior(PointerBehavior.AlwaysOff);

// Set the behavior to match HoloLens 1
// Note, if on HoloLens 2, you must configure your pointer profile to make the GGV pointer show up for articulated hands.
public void SetHoloLens1()
{
    PointerUtils.SetPokePointerBehavior(PointerBehavior.AlwaysOff, Handedness.Any);
    PointerUtils.SetGrabPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Any);
    PointerUtils.SetRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Any);
    PointerUtils.SetGGVBehavior(PointerBehavior.Default);
}
```

Weitere Beispiele finden Sie [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) unter und [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) .

## <a name="pointer-interactions-via-editor"></a>Zeigerinteraktionen über den Editor

Für Zeigerereignisse, die von behandelt [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) werden, bietet MRTK zusätzlichen Komfort in Form der [`PointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.PointerHandler) -Komponente, die die direkte Behandlung von Zeigerereignissen über Unity-Ereignisse ermöglicht.

<img src="../images/pointers/PointerHandler.png" style="max-width:100%;" alt="Pointer Handler">

## <a name="pointer-extent"></a>Zeigerausdehnung

Far-Zeiger verfügen über Einstellungen, die einschränken, wie weit sie raycasten und mit anderen Objekten in der Szene interagieren.
Standardmäßig ist dieser Wert auf 10 Meter festgelegt. Dieser Wert wurde ausgewählt, um mit dem Verhalten der HoloLens Shell konsistent zu bleiben.

Dies kann durch Aktualisieren der Felder der `DefaultControllerPointer` [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) Prefab-Komponente geändert werden:

*Zeigerausdehnung:* Steuert den maximalen Abstand, mit dem Zeiger interagieren.

*Standardzeigerumfang:* Steuert die Länge des Zeigerstrahls/der Zeigerlinie, die gerendert wird, wenn der Zeiger nicht mit etwas interagiert.

## <a name="see-also"></a>Siehe auch

- [Zeigerarchitektur](../../architecture/controllers-pointers-and-focus.md)
- [Eingabeereignisse](input-events.md)
