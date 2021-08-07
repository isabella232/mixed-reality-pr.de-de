---
title: Aktualisieren von früheren Versionen
description: Dokumentation für die Migration von einer niedrigeren Version des MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 04/19/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: a5d1e914fcbc44572e06c1fc3cbaba7ea0363287b9e670a423a4e63b17cb20a6
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210622"
---
# <a name="updating-from-earlier-versions"></a>Aktualisieren von früheren Versionen

- [Upgrade auf eine neue Version des MRTK](#upgrading-to-a-new-version-of-mrtk)
- [2.3.0 bis 2.4.0](#updating-230-to-240)
- [2.2.0 bis 2.3.0](#updating-220-to-230)
- [2.1.0 bis 2.2.0](#updating-210-to-220)
- [2.0.0 bis 2.1.0](#updating-200-to-210)
- [RC2 bis 2.0.0](#updating-rc2-to-200)

## <a name="finding-the-current-version"></a>Suchen der aktuellen Version 

Befolgen Sie diese Anweisungen, um herauszufinden, welche Version des MRTK Sie derzeit verwenden:

1. Öffnen Ihres MRTK-Projekts in Unity
2. Navigieren Sie zum Ordner "MixedRealityToolkit" in Ihrem Project Fenster.
3. Öffnen Sie die Datei mit dem Namen "Version".

Wenn die oben genannte Datei und der Ordner nicht vorhanden sind, verwenden Sie eine neuere Version des MRTK. Versuchen Sie in diesem Fall Folgendes:

1. Navigieren Sie zum Ordner "Mixed Reality Toolkit Foundation".
2. Klicken Sie auf "package.json", um eine Vorschau in Unity anzuzeigen, oder öffnen Sie sie mit einem Text-Editor.
3. Suchen Sie nach der Zeile mit dem Wort "version:". 

## <a name="upgrading-to-a-new-version-of-mrtk"></a>Upgrade auf eine neue Version des MRTK

*Es wird dringend [](../features/tools/migration-window.md) empfohlen,* das Migrationstool nach dem Abrufen des MRTK-Updates zum automatischen Beheben und Aktualisieren veralteter Komponenten und zum Anpassen an Breaking Changes ausführen. Das Migrationstool ist Teil des **Tools-Pakets.**

Die folgenden Anweisungen beschreiben den Upgradepfad von 2.4.0 auf 2.5.0. Wenn Ihr Projekt 2.3.0 oder früher installiert [](#updating-230-to-240) ist, lesen Sie die Änderungen zwischen [](https://microsoft.github.io/MixedRealityToolkit-Unity/version/releases/2.4.0/Documentation/Updating.html) den Versionen, um den Upgradepfad zu verstehen, oder lesen Sie die Anweisungen des vorherigen Release, um ein Versionsupgrade vorzunehmen.

### <a name="mixed-reality-feature-tool"></a>Mixed Reality Feature-Tool
Die einfachste Möglichkeit, MRTK auf eine neuere Version des MRTK zu aktualisieren, ist die Verwendung des [Mixed Reality Feature Tools,](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) um die neuesten Pakete herunterzuladen und sie direkt in Ihr Unity-Projekt zu laden.

Wenn das Projekt zuvor Unity-Ressourcendateien (UNITYPACKAGE) verwendet hat, lesen Sie [diese Anweisungen.](#switching-from-unity-asset-files-to-mixed-reality-feature-tool) 

### <a name="unity-asset-unitypackage-files"></a>Unity-Assetdateien (.unitypackage)

Ein weiterer Upgradepfad ist das manuelle Herunterladen von MRTK-Unity-Paketen und deren Anwendung auf Ihr Projekt. Sehen Sie sich die folgenden Schritte an:

1. Speichern Sie eine Kopie Ihres aktuellen Projekts, falls Sie zu einem beliebigen Zeitpunkt in den Upgradeschritten auf Dies treffen.
1. Schließen von Unity
1. Löschen Sie *im* Ordner Assets die folgenden **MRTK-Ordner** zusammen mit ihren META-Dateien (das Projekt enthält möglicherweise nicht alle aufgelisteten Ordner).
    - MRTK/Core
    - MRTK/Beispiele
    - MRTK/Erweiterungen
    - MRTK/Providers
    - MRTK/SDK
    - MRTK/Dienste
    - MRTK/StandardAssets
    > [!IMPORTANT]
    > Wenn Änderungen an den MRTK-Shadern vorgenommen wurden, erstellen Sie eine lokale Sicherung, bevor Sie den Ordner MRTK/StandardAssets löschen.
    - MRTK/Tools
    > [!IMPORTANT]
    > Löschen Sie NICHT den **Ordner MixedRealityToolkit.Generated** oder dessen META-Datei.
1. Löschen des **Bibliotheksordners**
    > [!IMPORTANT]
    > Einige Unity-Tools wie Unity Collab speichern Konfigurationsinformationen im Ordner Bibliothek. Wenn Sie dazu ein Tool verwenden, kopieren Sie zunächst den Datenordner des Tools aus der Bibliothek, bevor Sie ihn löschen, und stellen Sie ihn nach der erneuten Bibliothekswiederherstellung wieder wieder auf.
1. Erneutes Öffnen des Projekts in Unity
1. Importieren der neuen Unity-Pakete
    - Foundation: _Importieren Sie zuerst dieses Paket._
    - Tools
    - (Optional) Erweiterungen
    > [!NOTE]
    > Wenn zusätzliche Erweiterungen installiert wurden, müssen sie möglicherweise erneut importiert werden.
    - (Optional) Beispiele
1. Schließen Sie Unity, und löschen Sie **den Ordner Bibliothek** (lesen Sie zuerst den Hinweis unten!). Dieser Schritt ist erforderlich, um Unity zu zwingen, seine Ressourcendatenbank zu aktualisieren und vorhandene benutzerdefinierte Profile abgleichen.
1. Starten Sie Unity und für jede Szene im Projekt.
    - Löschen **Sie MixedRealityToolkit** und **MixedRealityPlayspace**, sofern vorhanden, aus der Hierarchie. Dadurch wird die Hauptkamera gelöscht, sie wird jedoch im nächsten Schritt neu erstellt. Wenn Eigenschaften der Hauptkamera manuell geändert wurden, müssen diese manuell erneut angewendet werden, sobald die neue Kamera erstellt wurde.
    - Wählen **Sie MixedRealityToolkit -> Zu Szene hinzufügen und konfigurieren aus.**
    - Wählen **Sie MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles** (nur einmal erforderlich) aus. Dadurch werden alle benutzerdefinierten Controllerzuordnungsprofile mit aktualisierten Achsen und Daten aktualisiert, während Ihre benutzerdefinierten Eingabeaktionen intakt bleiben.
1. Führen Sie [das Migrationstool aus,](../features/tools/migration-window.md) und führen Sie das Tool auf dem Project aus, um sicherzustellen, dass ihr gesamten Code auf den neuesten Stand gebracht wird. 
   Das Migrationsfenster enthält eine Reihe verschiedener Migrationshandler, die jeweils selbst ausgeführt werden müssen. Dieser Schritt umfasst:
   - Wählen Sie in der Dropdownliste **Migrationshandlerauswahl** den ersten Migrationshandler aus.
   - Klicken Sie auf die Schaltfläche "Full Project".
   - Klicken Sie auf die Schaltfläche "Add full project for migration" (Vollständiges Projekt für Migration hinzufügen). Dadurch wird das gesamte Projekt auf zu migrierende Objekte überprüft.
   - Klicken Sie auf die Schaltfläche "Migrieren", die aktiviert werden sollte, wenn migrierte Objekte gefunden wurden.
   - Wiederholen Sie die vorherigen drei Schritte für jeden Migrationshandler in der Dropdownliste.
     (Weitere Informationen [finden Sie in](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8552) diesem Problem, in dem die Arbeit behandelt wird, die zur Vereinfachung dieses Migrationsprozesses in einer zukünftigen Version durchgeführt werden kann.)

### <a name="switching-from-unity-asset-files-to-mixed-reality-feature-tool"></a>Wechseln von Unity-Ressourcendateien zum Mixed Reality Featuretool

Der Wechsel von Unity-Ressourcendateien zu Mixed Reality FeatureTool-Paketen bietet eine Reihe von Vorteilen:

- Einfacheres Aktualisieren
- Schnellere Kompilierungszeiten
- Weniger Projekte in der Visual Studio Projektmappe

Für die Verwendung des Mixed Reality Featuretools ist ein einmaliger Satz manueller Schritte erforderlich.

1. Speichern Sie eine Kopie Ihres aktuellen Projekts.
1. Schließen von Unity
1. Löschen Sie *im* Ordner Assets die folgenden **MRTK-Ordner** zusammen mit ihren META-Dateien (das Projekt enthält möglicherweise nicht alle aufgelisteten Ordner).
    - MRTK/Core
    - MRTK/Beispiele
    - MRTK/Erweiterungen
    - MRTK/Providers
    - MRTK/SDK
    - MRTK/Dienste
    - MRTK/StandardAssets
    > [!IMPORTANT]
    > Wenn Änderungen an den MRTK-Shadern vorgenommen wurden, erstellen Sie eine lokale Sicherung, bevor Sie den Ordner MRTK/StandardAssets löschen.
    - MRTK/Tools
    > [!IMPORTANT]
    > Löschen Sie NICHT den **Ordner MixedRealityToolkit.Generated** oder dessen META-Datei.
1. Löschen des **Bibliotheksordners**
    > [!IMPORTANT]
    > Einige Unity-Tools wie Unity Collab speichern Konfigurationsinformationen im Ordner Bibliothek. Wenn Sie dazu ein Tool verwenden, kopieren Sie zunächst den Datenordner des Tools aus der Bibliothek, bevor Sie ihn löschen, und stellen Sie ihn nach der erneuten Bibliothekswiederherstellung wieder wieder auf.
1. Erneutes Öffnen des Projekts in Unity

Nachdem die vorherigen Schritte ausgeführt wurden, führen Sie das [Mixed Reality Feature Tool aus,](#mixed-reality-feature-tool) und importieren Sie die gewünschte Version des Mixed Reality Toolkits.

## <a name="updating-230-to-240"></a>Aktualisieren von 2.3.0 auf 2.4.0

[Ordnerbenennungen](#folder-renames-in-240) 
 [API-Änderungen](#api-changes-in-240)

### <a name="folder-renames-in-240"></a>Ordnerbenennungen in 2.4.0

Die MixedRealityToolkit-Ordner wurden umbenannt und in Version 2.4 in eine gemeinsame Hierarchie verschoben. Wenn eine Anwendung hart codierte Pfade zu MRTK-Ressourcen verwendet, müssen sie gemäß der folgenden Tabelle aktualisiert werden.

| Vorheriger Ordner | Neuer Ordner |
| --- | --- |
| MixedRealityToolkit | MRTK/Core |
| MixedRealityToolkit.Examples | MRTK/Beispiele |
| MixedRealityToolkit.Extensions | MRTK/Erweiterungen |
| MixedRealityToolkit.Providers | MRTK/Providers |
| MixedRealityToolkit.SDK | MRTK/SDK |
| MixedRealityToolkit.Services | MRTK/Dienste |
| MixedRealityToolkit.Tests | MRTK/Tests |
| MixedRealityToolkit.Tools | MRTK/Tools |

> [!IMPORTANT]
> Enthält `MixedRealityToolkit.Generated` vom Kunden generierte Dateien und bleibt unverändert.

### <a name="eye-gaze-setup-in-240"></a>Einrichtung des Anvings mit den Augen in 2.4.0

Diese Version des MRTK ändert die schritte, die für die Einrichtung des Anvismus mit den Augen erforderlich sind. Das _Kontrollkästchen "IsEyeTrackingEnabled"_ finden Sie in den Anvitierungseinstellungen des Eingabezeigerprofils. Wenn Sie dieses Kontrollkästchen aktivieren, wird das blickbasierte Anving statt des standardmäßigen kopfbasierten Anvings aktiviert.

Weitere Informationen zu diesen Änderungen und vollständige Anweisungen für die Einrichtung der Eyetracking finden Sie im [Artikel Eyetracking.](../features/input/eye-tracking/eye-tracking-basic-setup.md)

### <a name="eye-gaze-pointer-behavior-in-240"></a>Verhalten des Anvingzeigers mit den Augen in 2.4.0

Das Standardzeigerverhalten für das Anvieren mit den Augen wurde so geändert, dass es dem Standardzeigerverhalten des Anvierens mit dem Kopf angepasst wird. Ein Anvitätszeiger mit den Augen wird automatisch unterdrückt, sobald eine Hand erkannt wird. Der Anvitätszeiger mit den Augen wird wieder sichtbar, nachdem er "Auswählen" gesagt hat.

Details zu Anving und Handeinrichtung finden Sie im Artikel [zu Augen und Händen.](../features/input/eye-tracking/eye-tracking-eyes-and-hands.md#how-to-keep-gaze-pointer-always-on)

### <a name="api-changes-in-240"></a>API-Änderungen in 2.4.0

**Benutzerdefinierte Controllerklassen**

Benutzerdefinierte Controllerklassen mussten zuvor `SetupDefaultInteractions(Handedness)` definieren. Diese Methode wurde in Version 2.4 veraltet gemacht, da der Übergabeparameter mit der eigenen Übergabe der Controllerklasse redundant war. Die neue Methode verfügt über keine Parameter. Darüber hinaus haben viele Controllerklassen dies auf die gleiche Weise definiert ( ), sodass der vollständige Aufruf in umgestaltet und eine optionale Außerkraftsetzung anstelle von `AssignControllerMappings(DefaultInteractions);` `BaseController` erforderlich gemacht wurde.

**Eigenschaften des Anvings mit den Augen**

Die `UseEyeTracking` -Eigenschaft `GazeProvider` aus der Implementierung von wurde in `IMixedRealityEyeGazeProvider` `IsEyeTrackingEnabled` umbenannt.

Wenn Sie dies zuvor getan haben...

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.UseEyeTracking = true;
}
```

Machen Sie dies jetzt...

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.IsEyeTrackingEnabled = true;
}
```

**WindowsApiChecker-Eigenschaften**

Die folgenden WindowsApiChecker-Eigenschaften wurden als veraltet markiert. Verwenden Sie `IsMethodAvailable` , `IsPropertyAvailable` oder `IsTypeAvailable` .

- UniversalApiContractV8_IsAvailable
- UniversalApiContractV7_IsAvailable
- UniversalApiContractV6_IsAvailable
- UniversalApiContractV5_IsAvailable
- UniversalApiContractV4_IsAvailable
- UniversalApiContractV3_IsAvailable

Es ist nicht geplant, WindowsApiChecker Eigenschaften für zukünftige API-Vertragsversionen hinzuzufügen.

**GltfMeshPrimitiveAttributes schreibgeschützt**

Die primitiven gltf mesh-Attribute, die früher festgelegt werden können, sind jetzt schreibgeschützt. Ihre Werte werden einmal festgelegt, wenn sie deserialisiert werden.

### <a name="custom-button-icon-migration"></a>Migration benutzerdefinierter Schaltflächensymbole

Zuvor mussten benutzerdefinierte Schaltflächensymbole dem Quadrenderer der Schaltfläche ein neues Material zuweisen. Dies ist nicht mehr erforderlich, und es wird empfohlen, benutzerdefinierte Symboltexturen in ein IconSet zu verschieben. Vorhandene benutzerdefinierte Materialien und Symbole werden beibehalten. Allerdings sind sie bis zum Upgrade weniger optimal.
Verwenden Sie ButtonConfigHelperMigrationHandler, um die Objekte auf allen Schaltflächen im Projekt auf das neue empfohlene Format zu aktualisieren.
(Mixed Reality Toolkit -> Utilities -> Migration Window -> Migration Handler Selection -> Microsoft.MixedReality.Toolkit.Utilities.ButtonConfigHelperMigrationHandler)

![Upgradefensterdialog](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

Wenn während der Migration kein Symbol im Standardsymbolsatz gefunden wird, wird in MixedRealityToolkit.Generated/CustomIconSets ein benutzerdefinierter Symbolsatz erstellt. Ein Dialogfeld gibt an, dass dies erfolgt ist.

![Benutzerdefinierte Symbolbenachrichtigung](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

## <a name="updating-220-to-230"></a>Aktualisieren von 2.2.0 auf 2.3.0

- [API-Änderungen](#api-changes-in-230)

### <a name="api-changes-in-230"></a>API-Änderungen in 2.3.0

**ControllerPoseSynchronizer**

Das private Feld ControllerPoseSynchronizer.handedness wurde als veraltet markiert. Dies sollte nur minimale Auswirkungen auf Anwendungen haben, da das Feld außerhalb seiner Klasse nicht sichtbar ist.

Der Setter der öffentlichen ControllerPoseSynchronizer.Handedness-Eigenschaft wurde entfernt ([#7012](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7012)).

**MSBuild für Unity**

Diese Version des MRTK verwendet eine neuere Version von MSBuild für Unity als frühere Versionen. Wenn die ältere Version während des Ladens des Projekts im Unity-Paket-Manager-Manifest aufgeführt ist, wird das Konfigurationsdialogfeld mit aktivierter Option Enable MSBuild for Unity (MSBuild für Unity aktivieren) angezeigt. Wenn Sie anwenden, wird ein Upgrade durchführen.

**ScriptingUtilities**

Die ScriptingUtilities-Klasse wurde als veraltet markiert und durch ScriptUtilities in der Assembly Microsoft.MixedReality.Toolkit.Editor.Utilities ersetzt. Die neue Klasse verfeinert das vorherige Verhalten und fügt Unterstützung für das Entfernen von Skriptdefinitionen hinzu.

Während vorhandener Code weiterhin in Version 2.3.0 funktioniert, wird empfohlen, auf die neue Klasse zu aktualisieren.

**ShellHandRayPointer**

Die LineRendererSelected- und lineRendererNoTarget-Member der ShellHandRayPointer-Klasse wurden durch lineMaterialSelected bzw. lineMaterialNoTarget ersetzt ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6863)).

Ersetzen Sie lineRendererSelected durch lineMaterialSelected und/oder lineRendererNoTarget durch lineMaterialNoTarget, um Kompilierungsfehler zu beheben.

**Raumbeobachter StartupBehavior**

Raumbeobachter, die auf der -Klasse erstellt wurden, verwenden jetzt den `BaseSpatialObserver` Wert von StartupBehavior, wenn sie wieder aktiviert werden ([#6919](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6919)).

Es sind keine Änderungen erforderlich, um diese Korrektur zu nutzen.

**UX-Steuerelement-Prefabs aktualisiert, um PressableButton zu verwenden**

Die folgenden Prefabs verwenden jetzt die PressableButton-Komponente anstelle von TouchHandler für die nahezue Interaktion ([7070](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7070)).

- AnimationButton
- Schaltfläche
- ButtonHoloLens1
- ButtonHoloLens1Toggle
- CheckBox
- RadialSet
- ToggleButton
- ToggleSwitch
- UnityUIButton
- UnityUICheckboxButton
- UnityUIRadialButton
- UnityUIToggleButton

Aufgrund dieser Änderung muss der Anwendungscode möglicherweise aktualisiert werden.

**WindowsMixedRealityUtilities-Namespace**

Der Namespace von WindowsMixedRealityUtilities wurde von Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input in Microsoft.MixedReality.Toolkit.WindowsMixedReality ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6989)) geändert.

Aktualisieren Sie #using Anweisungen, um Kompilierungsfehler zu beheben.

## <a name="updating-210-to-220"></a>Aktualisieren von 2.1.0 auf 2.2.0

- [API-Änderungen](#api-changes-in-220)

### <a name="api-changes-in-220"></a>API-Änderungen in 2.2.0

**IMixedRealityBoundarySystem.Contains**

Diese Methode hat zuvor eine bestimmte, von Unity definierte experimentelle Enumeration verwendet. Sie nimmt jetzt eine MRTK-definierte Enumeration an, die mit der Unity-Enumeration identisch ist. Diese Änderung hilft bei der Vorbereitung des MRTK für die zukünftigen Begrenzungs-APIs von Unity.

**MixedRealityServiceProfileAttribute**

Um die Anforderungen für die Unterstützung eines Profils besser zu beschreiben, wurde das MixedRealityServiceProfileAttribute aktualisiert, um eine optionale Auflistung ausgeschlossener Typen hinzuzufügen. Im Rahmen dieser Änderung wurde die ServiceType-Eigenschaft von Type in Type[] geändert und in RequiredTypes umbenannt.

Eine zweite Eigenschaft, ExcludedTypes, wurde ebenfalls hinzugefügt.

## <a name="updating-200-to-210"></a>Aktualisieren von 2.0.0 auf 2.1.0

- [API-Änderungen](#api-changes-in-210)
- [Profiländerungen](#profile-changes-in-210)

### <a name="api-changes-in-210"></a>API-Änderungen in 2.1.0

**BaseNearInteractionTouchable**

Wurde `BaseNearInteractionTouchable` geändert, um die `OnValidate` -Methode als virtuell zu markieren. Klassen, die erweitert `BaseNearInteractionTouchable` werden (z. B. `NearInteractionTouchableUnityUI` ), wurden aktualisiert, um diese Änderung widerzuspiegeln.

**ColliderNearInteractionTouchable**

Die `ColliderNearInteractionTouchable`-Klasse ist veraltet. Aktualisieren Sie die Codeverweise, um zu `BaseNearInteractionTouchable` verwenden.

**IMixedRealityMouseDeviceManager**

**_Hinzugefügt_**

`IMixedRealityMouseDeviceManager` wurden `CursorSpeed` die Eigenschaften und `WheelSpeed` hinzugefügt. Mit diesen Eigenschaften können Anwendungen einen Multiplikatorwert angeben, mit dem die Geschwindigkeit des Cursors bzw. des Rads skaliert wird.

Dies ist eine Breaking Change und erfordert, dass vorhandene Implementierungen des Mausgeräte-Managers geändert werden.

>[!NOTE]
>Diese Änderung ist nicht abwärtskompatibel mit Version 2.0.0.

**_Veraltet_**

Die `MouseInputProfile` Eigenschaft wurde als veraltet markiert und wird aus einer zukünftigen Version des Microsoft Mixed Reality Toolkits entfernt. Es wird empfohlen, dass anwendungscode diese Eigenschaft nicht mehr verwendet.

**Interaktionsfähig**

Die folgenden Methoden und Eigenschaften sind veraltet und werden aus einer zukünftigen Version des Microsoft Mixed Reality Toolkits entfernt. Es wird empfohlen, den Anwendungscode gemäß den Anweisungen zu aktualisieren, die im Obsolete-Attribut enthalten sind und in der Konsole angezeigt werden.

- `public bool Enabled`
- `public bool FocusEnabled`
- `public void ForceUpdateThemes()`
- `public bool IsDisabled`
- `public bool IsToggleButton`
- `public int GetDimensionIndex()`
- `public State[] GetStates()`
- `public bool RequiresFocus`
- `public void ResetBaseStates()`
- `public virtual void SetCollision(bool collision)`
- `public virtual void SetCustom(bool custom)`
- `public void SetDimensionIndex(int index)`
- `public virtual void SetDisabled(bool disabled)`
- `public virtual void SetFocus(bool focus)`
- `public virtual void SetGesture(bool gesture)`
- `public virtual void SetGestureMax(bool gesture)`
- `public virtual void SetGrab(bool grab)`
- `public virtual void SetInteractive(bool interactive)`
- `public virtual void SetObservation(bool observation)`
- `public virtual void SetObservationTargeted(bool targeted)`
- `public virtual void SetPhysicalTouch(bool touch)`
- `public virtual void SetPress(bool press)`
- `public virtual void SetTargeted(bool targeted)`
- `public virtual void SetToggled(bool toggled)`
- `public virtual void SetVisited(bool visited)`
- `public virtual void SetVoiceCommand(bool voice)`

**NearInteractionTouchableSurface**

Die `NearInteractionTouchableSurface` -Klasse wurde hinzugefügt und dient jetzt als Basisklasse für `NearInteractionTouchable` und `NearInteractionTouchableUnityUI` .

### <a name="profile-changes-in-210"></a>Profiländerungen in 2.1.0

**Handtrackingprofil**

Das Handgitternetz und die gemeinsamen Visualisierungen verfügen jetzt über separate Editor- und Playereinstellungen. Das Handtrackingprofil wurde aktualisiert, sodass diese Visualisierungen auf festgelegt werden können. Nothing, Everything, Editor oder Player.

![Handvisualisierungsmodi](../release-notes/images/HandTrackingVisualizationModes.png)

Benutzerdefinierte Handtrackingprofile müssen möglicherweise aktualisiert werden, damit sie mit Version 2.1.0 ordnungsgemäß funktionieren.

>[!NOTE]
>Diese Änderung ist nicht abwärtskompatibel mit Version 2.0.0.

**Eingabesimulationsprofil**

Das Eingabesimulationssystem wurde aktualisiert, wodurch einige Einstellungen im Eingabesimulationsprofil geändert werden. Einige Änderungen können nicht automatisch migriert werden, und Benutzer stellen möglicherweise fest, dass Profile Standardwerte verwenden.

1. Alle KeyCode- und Maustastenbindungen im Profil wurden durch eine generische `KeyBinding` Struktur ersetzt, die den Bindungstyp (Taste oder Maus) sowie den tatsächlichen Bindungscode (KeyCode bzw. Die Nummer der Maustaste) speichert. Die Struktur verfügt über einen eigenen Inspektor, der eine einheitliche Anzeige ermöglicht und ein Tool zur automatischen Bindung bietet, mit dem Tastenbindungen schnell festgelegt werden können, indem die entsprechende Taste gedrückt wird, anstatt aus einer großen Dropdownliste auszuwählen.

    - FastControlKey
    - ToggleLeftHandKey
    - ToggleRightHandKey
    - LeftHandManipulationKey
    - RightHandManipulationKey

1. `MouseLookToggle` war zuvor in der `MouseLookButton` Enumeration als `InputSimulationMouseButton.Focused` enthalten. Es handelt sich jetzt um eine separate Option. Wenn diese Option aktiviert ist, wird die Kamera nach dem Loslassen der Schaltfläche mit der Maus rotiert, bis die Escapetaste gedrückt wird.
1. `HandDepthMultiplier` Der Standardwert wurde von 0,1 auf 0,03 gesenkt, um einige Änderungen an der Eingabesimulation zu berücksichtigen. Wenn die Kamera beim Scrollen zu schnell bewegt wird, versuchen Sie, diesen Wert zu verringern.
1. Tasten zum Drehen von Händen wurden entfernt, die Handdrehung wird jetzt auch mit der Maus gesteuert. Wenn Sie `HandRotateButton` (STRG) zusammen mit der Bearbeitungstaste links/rechts (LShift/Space) halten, wird die Handrotation ermöglicht.
1. Eine neue Achse "UpDown" wurde in die Eingabeachsenliste eingeführt. Dadurch wird die Kamerabewegung in der Vertikalen gesteuert, und standardmäßig werden Q/E-Schlüssel sowie die Controllertriggerschaltflächen verwendet.

Weitere Informationen zu diesen Änderungen finden Sie im Artikel [zum Eingabesimulationsdienst.](../features/input-simulation/input-simulation-service.md)

**Mausdatenanbieterprofil**

Das Mausdatenanbieterprofil wurde aktualisiert, um die neuen Eigenschaften und verfügbar zu `CursorSpeed` `WheelSpeed` machen. Für vorhandene benutzerdefinierte Profile werden automatisch Standardwerte bereitgestellt. Wenn das Profil gespeichert wird, werden diese neuen Werte beibehalten.

**Controllerzuordnungsprofil**

Einige Achsen und Eingabetypen wurden in Version 2.1.0 aktualisiert, insbesondere rund um die OpenVR-Plattform. Achten Sie darauf, dass Sie beim Upgrade **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles (MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles)** auswählen. Dadurch werden alle benutzerdefinierten Controllerzuordnungsprofile mit den aktualisierten Achsen und Daten aktualisiert, während Ihre benutzerdefinierten zugewiesenen Eingabeaktionen intakt bleiben.

## <a name="updating-rc2-to-200"></a>Aktualisieren von RC2 auf 2.0.0

Zwischen den Releases RC2 und 2.0.0 des Microsoft Mixed Reality Toolkits wurden Änderungen vorgenommen, die sich auf vorhandene Projekte auswirken können. In diesem Dokument werden diese Änderungen und das Aktualisieren von Projekten auf version 2.0.0 beschrieben.

- [API-Änderungen](#api-changes-in-200)
- [Änderungen des Assemblynamens](#assembly-name-changes-in-200)

### <a name="api-changes-in-200"></a>API-Änderungen in 2.0.0

Seit der Veröffentlichung von RC2 gibt es eine Reihe von API-Änderungen, einschließlich einiger, die vorhandene Projekte unterbrechen können. In den folgenden Abschnitten werden die Änderungen beschrieben, die zwischen den Releases RC2 und 2.0.0 aufgetreten sind.

**MixedRealityToolkit**

Die folgenden öffentlichen Eigenschaften für das MixedRealityToolkit-Objekt sind veraltet.

- `RegisteredMixedRealityServices` enthält nicht mehr die Auflistung registrierter Erweiterungsdienste und Datenanbieter.

Verwenden Sie , um auf Erweiterungsdienste `MixedRealityServiceRegistry.TryGetService<T>` zuzugreifen. Um auf Datenanbieter zuzugreifen, umwandlungen Sie die Dienstinstanz in [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) , und verwenden Sie `GetDataProvider<T>` .

Verwenden Sie [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) stattdessen oder [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) für die folgenden veralteten Eigenschaften.

- `ActiveSystems`
- `InputSystem`
- `BoundarySystem`
- `CameraSystem`
- `SpatialAwarenessSystem`
- `TeleportSystem`
- `DiagnosticsSystem`
- `SceneSystem`

**CoreServices**

Die [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) -Klasse ist die Ersetzung für die statischen Systemaccessoren (z. B. BoundarySystem), die im -Objekt gefunden `MixedRealityToolkit` wurden.

>[!IMPORTANT]
>Die `MixedRealityToolkit` Systemaccessoren sind in Version 2.0.0 veraltet und werden in einer zukünftigen Version des MRTK entfernt.

Das folgende Codebeispiel veranschaulicht das alte und das neue Muster.

``` c#
// Old
GameObject playAreaVisualization = MixedRealityToolkit.BoundarySystem?.GetPlayAreaVisualization();

// New
GameObject playAreaVisualization = CoreServices.BoundarySystem?.GetPlayAreaVisualization();
```

Durch die Verwendung der neuen CoreSystem-Klasse wird sichergestellt, dass ihr Anwendungscode nicht aktualisiert werden muss, wenn Sie die Anwendung so ändern, dass eine andere Dienstregistrierungsstelle verwendet wird (z. B. einer der experimentellen Dienst-Manager).

**IMixedRealityRaycastProvider**

Durch das Hinzufügen von IMixedRealityRaycastProvider wurde das Konfigurationsprofil des Eingabesystems geändert. Wenn Sie über ein benutzerdefiniertes Profil verfügen, erhalten Sie möglicherweise die Fehler in der folgenden Abbildung, wenn Sie Ihre Anwendung ausführen.

![Auswählen des Raycastanbieters 1](../release-notes/images/UnableToRegisterRaycastProvider.png)

Um diese Probleme zu beheben, fügen Sie Ihrem Eingabesystemprofil eine IMixedRealityRaycastProvider-Instanz hinzu.

![Auswählen des Raycastanbieters 2](../release-notes/images/SelectRaycastProvider.png)

**Ereignissystem**

- Die `IMixedRealityEventSystem` alten API-Methoden `Register` und wurden als veraltet `Unregister` markiert. Sie werden aus Gründen der Abwärtskompatibilität beibehalten.
- `InputSystemGlobalListener` wurde als veraltet markiert. Seine Funktionalität hat sich nicht geändert.
- `BaseInputHandler` Die Basisklasse wurde von `InputSystemGlobalListener` in `InputSystemGlobalHandlerListener` geändert. Dies ist eine Breaking Change für alle Nachfolger von `BaseInputHandler` .

**_Motivation hinter der Änderung_**

Die alte Ereignissystem-API `Register` und kann möglicherweise mehrere Probleme in der Laufzeit `Unregister` verursachen, hauptsächlich:

- Wenn sich eine Komponente für globale Ereignisse registriert, empfängt sie globale Eingabeereignisse *aller* Typen.
- Wenn sich eine der Komponenten eines Objekts für globale Eingabeereignisse registriert, empfangen alle Komponenten dieses Objekts globale Eingabeereignisse *aller* Typen.
- Wenn sich zwei Komponenten im selben Objekt bei globalen Ereignissen registrieren und dann eine zur Laufzeit deaktiviert ist, empfängt die zweite keine globalen Ereignisse mehr.

Neue API `RegisterHandler` und `UnregisterHandler` :

- Stellt eine explizite und präzise Steuerung bereit, auf welche Eingabeereignisse global gelescht werden soll und welche fokussiert sein sollten.
- Ermöglicht es mehreren Komponenten desselben Objekts, unabhängig voneinander auf globale Ereignisse zu lauschen.

**_Vorgehensweise zum Migrieren_**

- Wenn Sie die API bereits direkt zuvor aufgerufen `Register` / `Unregister` haben, ersetzen Sie diese Aufrufe durch Aufrufe von `RegisterHandler` / `UnregisterHandler` . Verwenden Sie Handlerschnittstellen, die Sie als generische Parameter implementieren. Wenn Sie mehrere Schnittstellen implementieren und mehrere von ihnen auf globale Eingabeereignisse lauschen, rufen Sie `RegisterHandler` mehrmals auf.
- Wenn Sie von geerbt `InputSystemGlobalListener` haben, ändern Sie die Vererbung in `InputSystemGlobalHandlerListener` . Implementieren `RegisterHandlers` und `UnregisterHandlers` abstrahieren Sie Methoden. Rufen Sie im Implementierungsaufruf `inputSystem.RegisterHandler` ( `inputSystem.UnregisterHandler` ) auf, um sich für alle Handlerschnittstellen zu registrieren, auf die Sie globale Ereignisse lauschen möchten.
- Wenn Sie von geerbt `BaseInputHandler` haben, implementieren `RegisterHandlers` Sie und abstrakte `UnregisterHandlers` Methoden (wie bei `InputSystemGlobalListener` ).

**_Beispiele für die Migration_**

```c#
// Old
class SampleHandler : MonoBehaviour, IMixedRealitySourceStateHandler, IMixedRealityHandJointHandler
{
    private void OnEnable()
    {
        InputSystem?.Register(gameObject);
    }

    private void OnDisable()
    {
        InputSystem?.Unregister(gameObject);
    }
}

// Migrated
class SampleHandler : MonoBehaviour, IMixedRealitySourceStateHandler, IMixedRealityHandJointHandler
{
    private void OnEnable()
    {
        InputSystem?.RegisterHandler<IMixedRealitySourceStateHandler>(this);
        InputSystem?.RegisterHandler<IMixedRealityHandJointHandler>(this);
    }

    private void OnDisable()
    {
        InputSystem?.UnregisterHandler<IMixedRealitySourceStateHandler>(this);
        InputSystem?.UnregisterHandler<IMixedRealityHandJointHandler>(this);
    }
}
```

```c#
// Old
class SampleHandler2 : InputSystemGlobalListener, IMixedRealitySpeechHandler
{
}

// Migrated
class SampleHandler2 : InputSystemGlobalHandlerListener, IMixedRealitySpeechHandler
{
    private void RegisterHandlers()
    {
        InputSystem?.RegisterHandler<IMixedRealitySpeechHandler>(this);
    }

    private void UnregisterHandlers()
    {
        InputSystem?.UnregisterHandler<IMixedRealitySpeechHandler>(this);
    }
}

// Alternative migration
class SampleHandler2 : MonoBehaviour, IMixedRealitySpeechHandler
{
    private void OnEnable()
    {
        IMixedRealityInputSystem inputSystem;
        if (MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
        {
            inputSystem?.RegisterHandler<IMixedRealitySpeechHandler>(this);
        }
    }

    private void OnDisable()
    {
        IMixedRealityInputSystem inputSystem;
        if (MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
        {
            inputSystem?.UnregisterHandler<IMixedRealitySpeechHandler>(this);
        }
    }
}
```

**Räumliche Wahrnehmung**

Die Schnittstellen IMixedRealitySpatialAwarenessSystem und IMixedRealitySpatialAwarenessObserver haben wie unten beschrieben mehrere Breaking Changes vorgenommen.

**_Änderungen_**

Die folgenden Methoden wurden umbenannt, um ihre Verwendung besser zu beschreiben.

- `IMixedRealitySpatialAwarenessSystem.CreateSpatialObjectParent` wurde in `IMixedRealitySpatialAwarenessSystem.CreateSpatialAwarenessObservationParent` umbenannt, um deren Verwendung zu verdeutlichen.

**_Erweiterungen_**

Basierend auf Kundenfeedback wurde Unterstützung für die einfache Entfernung zuvor beobachteter Räumlicher Wahrnehmungsdaten hinzugefügt.

- `IMixedRealitySpatialAwarenessSystem.ClearObservations()`
- `IMixedRealitySpatialAwarenessSystem.ClearObservations<T>(string name)`
- `IMixedRealitySpatialAwarenessObserver.ClearObservations()`

**Solver**

Einige Solverkomponenten und die SolverHandler-Managerklasse wurden geändert, um verschiedene Fehler zu beheben und eine intuitivere Verwendung zu ermöglichen.

**_SolverHandler_**

- Die -Klasse erweitert nicht mehr von `ControllerFinder`
- `TrackedObjectToReference` Public Property ist veraltet und wurde in umbenannt. `TrackedTargetType`
- `TrackedObjectType` ist veraltet & rechten Controllerwerten. Verwenden Sie stattdessen `MotionController` die Werte oder , und aktualisieren Sie die neue `HandJoint` `TrackedHandedness` Eigenschaft, um die Nachverfolgung auf den linken oder rechten Controller zu beschränken.

**_InBetween_**

- `TrackedObjectForSecondTransform` Public Property ist veraltet und wurde in umbenannt. `SecondTrackedObjectType`
- `AttachSecondTransformToNewTrackedObject()` wurde entfernt. Um den Solver zu aktualisieren, ändern Sie die öffentlichen Eigenschaften (d.h. `SecondTrackedObjectType`)

**_SurfaceMagnetism_**

- `MaxDistance` Public Property ist veraltet und wurde in umbenannt. `MaxRaycastDistance`
- `CloseDistance` Public Property ist veraltet und wurde in umbenannt. `ClosestDistance`
- Der Standardwert für `RaycastDirectionMode` ist `TrackedTargetForward` jetzt, welcher Raycast in Richtung der nachverfolgten Zieltransformation vorwärts geht.
- `OrientationMode`Enumerationswerte und `Vertical` `Full` wurden in `TrackedTarget` bzw. umbenannt. `SurfaceNormal`
- `KeepOrientationVertical` Die public-Eigenschaft wurde hinzugefügt, um zu steuern, ob die Ausrichtung des zugeordneten GameObject vertikal bleibt.

**Schaltflächen**

- [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) hat die -Eigenschaft jetzt `DistanceSpaceMode` auf den Standardwert `Local` festgelegt. Dadurch können Schaltflächen skaliert werden, während sie weiterhin gedrückt werden können.

**Clipping Sphere**

Die ClippingSphere-Schnittstelle wurde geändert, um die APIs in ClippingBox und ClippingPlane zu spiegeln.

Die Radius-Eigenschaft von ClippingSphere wird jetzt implizit basierend auf der Transformationsskala berechnet. Bevor Entwickler den Radius der ClippingSphere im Inspektor angeben müssten. Wenn Sie den Radius ändern möchten, aktualisieren Sie einfach die Transformationsskala der Transformation wie gewohnt.

**NearInteractionTouchable und Der PointePointer**

- NearInteractionTouchable verarbeitet die Canvas der Unity-Benutzeroberfläche nicht mehr. Die NearInteractionTouchableUnityUI-Klasse muss jetzt für Benutzeroberfläche-Touchables von Unity verwendet werden.
- ColliderNearInteractionTouchable ist die neue Basisklasse für Touchables, die auf Collidern basieren, d.h. alle touchierbaren Mit Ausnahme von NearInteractionTouchableUnityUI.
- "BaseNearInteractionTouchable.DistFront" wurde verschoben und in "Hexadepointer.TouchableDistance" umbenannt. Dies ist die Entfernung, mit der der Hexadepointer mit touchables interagieren kann. Bisher hatte jedes touchierbare eine eigene maximale Interaktionsdistanz, aber jetzt ist dies in Der Zustreichpunkter definiert, der eine bessere Optimierung ermöglicht.
- "BaseNearInteractionTouchable.DistBack" wurde in "HexadeThreshold" umbenannt. Dadurch wird deutlich, dass Es sich bei "Hexadethreshold" um das Pendant zu "DebounceThreshold" handelt. Ein touchierbarer wird aktiviert, wenn der "MsieThreshold" überschritten wird, und wird freigegeben, wenn DebutnceThreshold überschritten wird.

**ReadOnlyAttribute**

Der `Microsoft.MixedReality.Toolkit` Namespace wurde zu , und `ReadOnlyAttribute` `BeginReadOnlyGroupAttribute` `EndReadOnlyGroupAttribute` hinzugefügt.

**PointerClickHandler**

Die `PointerClickHandler`-Klasse ist veraltet. `PointerHandler`Stattdessen sollte verwendet werden, es bietet die gleiche Funktionalität.

**HoloLens Clicker-Unterstützung**

Die Controllerzuordnungen des HoloLens-Clickers wurden von einem nicht behandelten [`WindowsMixedRealityController`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityController) zu einem nicht behandelten [`WindowsMixedRealityGGVHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityGGVHand) geändert. Um dies zu berücksichtigen, wird ein automatischer Updater ausgeführt, wenn Sie Ihr ControllerMapping-Profil zum ersten Mal öffnen. Öffnen Sie alle benutzerdefinierten Profile mindestens einmal nach dem Upgrade auf 2.0.0, um diesen einmaligen Migrationsschritt auszulösen.

**InteractableHighlight**

Die `InteractableHighlight`-Klasse ist veraltet. `InteractableOnFocus`Stattdessen sollten die Klasse und `FocusInteractableStates` das Medienobjekt verwendet werden. Um ein neues `Theme` Medienobjekt für zu `InteractableOnFocus` erstellen, klicken Sie mit der rechten Maustaste in das Projektfenster, und wählen *Sie Create* Mixed Reality Toolkit Interactable Theme  >    >  *(Interaktivierbares*  >  *Design* des Toolkits erstellen) aus.

**HandInteractionPanZoom**

`HandInteractionPanZoom` wurde in den Ui-Namespace verschoben, da es sich nicht um eine Eingabekomponente handelt. `HandPanEventData` wurde auch in diesen Namespace verschoben und vereinfacht, um anderen Benutzeroberflächenereignisdaten zu entsprechen.

### <a name="assembly-name-changes-in-200"></a>Änderungen des Assemblynamens in 2.0.0

In Release 2.0.0 wurden alle offiziellen Mixed Reality Toolkit-Assemblynamen und die zugehörigen Assemblydefinitionsdateien (ASMDEF) aktualisiert, damit sie dem folgenden Muster entsprechen.

```c#
Microsoft.MixedReality.Toolkit[.<name>]
```

In einigen Fällen wurden mehrere Assemblys zusammengeführt, um eine bessere Einheitlichkeit ihrer Inhalte zu erreichen. Wenn Ihr Projekt benutzerdefinierte ASMDEF-Dateien verwendet, müssen sie möglicherweise aktualisiert werden.

In den folgenden Tabellen wird beschrieben, wie die ASMDEF-Dateinamen rc2 dem Release 2.0.0 zugeordnet werden. Alle Assemblynamen entsprechen dem Asmdef-Dateinamen.

**MixedRealityToolkit**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit.asmdef | Microsoft.MixedReality.Toolkit.asmdef |
| MixedRealityToolkit.Core.BuildAndDeploy.asmdef | Microsoft.MixedReality.Toolkit.Editor.BuildAndDeploy.asmdef |
| MixedRealityToolkit.Core.Definitions.Utilities.Editor.asmdef | Entfernen Sie microsoft.MixedReality.Toolkit.Editor.Utilities.asmdef. |
| MixedRealityToolkit.Core.Extensions.EditorClassExtensions.asmdef | Microsoft.MixedReality.Toolkit.Editor.ClassExtensions.asmdef
| MixedRealityToolkit.Core.Inspectors.asmdef | Microsoft.MixedReality.Toolkit.Editor.Inspectors.asmdef |
| MixedRealityToolkit.Core.Inspectors.ServiceInspectors.asmdef | Microsoft.MixedReality.Toolkit.Editor.ServiceInspectors.asmdef |
| MixedRealityToolkit.Core.UtilitiesAsync.asmdef | Microsoft.MixedReality.Toolkit.Async.asmdef |
| MixedRealityToolkit.Core.Utilities.Editor.asmdef | Microsoft.MixedReality.Toolkit.Editor.Utilities.asmdef |
| MixedRealityToolkit.Utilities.Gltf.asmdef | Microsoft.MixedReality.Toolkit.Gltf.asmdef |
| MixedRealityToolkit.Utilities.Gltf.Importers.asmdef | Microsoft.MixedReality.Toolkit.Gltf.Importers.asmdef |

**MixedRealityToolkit.Providers**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit.Providers.OpenVR.asmdef | Microsoft.MixedReality.Toolkit.Providers.OpenVR.asmdef |
| MixedRealityToolkit.Providers.WindowsMixedReality.asmdef | Microsoft.MixedReality.Toolkit.Providers.WindowsMixedReality.asmdef |
| MixedRealityToolkit.Providers.WindowsVoiceInput.asmdef | Microsoft.MixedReality.Toolkit.Providers.WindowsVoiceInput.asmdef |

**MixedRealityToolkit.Services**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit.Services.BoundarySystem.asmdef | Microsoft.MixedReality.Toolkit.Services.BoundarySystem.asmdef |
| MixedRealityToolkit.Services.CameraSystem.asmdef | Microsoft.MixedReality.Toolkit.Services.CameraSystem.asmdef |
| MixedRealityToolkit.Services.DiagnosticsSystem.asmdef | Microsoft.MixedReality.Toolkit.Services.DiagnosticsSystem.asmdef |
| MixedRealityToolkit.Services.InputSimulation.asmdef | Microsoft.MixedReality.Toolkit.Services.InputSimulation.asmdef |
| MixedRealityToolkit.Services.InputSimulation.Editor.asmdef | Microsoft.MixedReality.Toolkit.Services.InputSimulation.Editor.asmdef |
| MixedRealityToolkit.Services.InputSystem.asmdef | Microsoft.MixedReality.Toolkit.Services.InputSystem.asmdef |
| MixedRealityToolkit.Services.Inspectors.asmdef | Microsoft.MixedReality.Toolkit.Services.InputSystem.Editor.asmdef |
| MixedRealityToolkit.Services.SceneSystem.asmdef | Microsoft.MixedReality.Toolkit.Services.SceneSystem.asmdef |
| MixedRealityToolkit.Services.SpatialAwarenessSystem.asmdef | Microsoft.MixedReality.Toolkit.Services.SpatialAwarenessSystem.asmdef |
| MixedRealityToolkit.Services.TeleportSystem.asmdef | Microsoft.MixedReality.Toolkit.Services.TeleportSystem.asmdef |

**MixedRealityToolkit.SDK**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit.SDK.asmdef | Microsoft.MixedReality.Toolkit.SDK.asmdef |
| MixedRealityToolkit.SDK.Inspectors.asmdef | Microsoft.MixedReality.Toolkit.SDK.Inspectors.asmdef |

**MixedRealityToolkit.Examples**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit.Examples.asmdef | Microsoft.MixedReality.Toolkit.Examples.asmdef |
| MixedRealityToolkit.Examples.Demos.Gltf.asmdef | Microsoft.MixedReality.Toolkit.Demos.Gltf.asmdef |
| MixedRealityToolkit.Examples.Demos.StandardShader.Inspectors.asmdef | Microsoft.MixedReality.Toolkit.Demos.StandardShader.Inspectors.asmdef |
| MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.asmdef | Microsoft.MixedReality.Toolkit.Demos.InspectorFields.asmdef |
| MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.Inspectors.asmdef | Microsoft.MixedReality.Toolkit.Demos.InspectorFields.Inspectors.asmdef |
| MixedRealityToolkit.Examples.Demos.UX.Interactables.asmdef | Microsoft.MixedReality.Toolkit.Demos.UX.Interactables.asmdef |
