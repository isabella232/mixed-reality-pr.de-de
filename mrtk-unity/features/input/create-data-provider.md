---
title: Erstellen eines Eingabesystem-Datenanbieters
description: Dokumentation zum Erstellen eines Eingabesystems und eines Datenanbieters in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 391aa477bb09fa2dec2b3bcb26bad813c715ee03eeb0dc03dcbc9048ae318295
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223988"
---
# <a name="creating-an-input-system-data-provider"></a>Erstellen eines Eingabesystem-Datenanbieters

Das Mixed Reality Toolkit-Eingabesystem ist ein erweiterbares System zum Aktivieren der Eingabegeräteunterstützung. Um Unterstützung für eine neue Hardwareplattform hinzuzufügen, ist möglicherweise ein benutzerdefinierter Eingabedatenanbieter erforderlich.

In diesem Artikel wird beschrieben, wie Sie benutzerdefinierte Datenanbieter, auch als Geräte-Manager bezeichnet, für das Eingabesystem erstellen. Der hier gezeigte Beispielcode ist aus dem [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) .

> Den vollständigen Code, der in diesem Beispiel verwendet wird, finden Sie im Ordner MRTK/Providers/WindowsMixedReality.

## <a name="namespace-and-folder-structure"></a>Namespace- und Ordnerstruktur

Datenanbieter können als Drittanbieter-Add-On oder als Teil des Microsoft Mixed Reality Toolkits verteilt werden. Der Genehmigungsprozess für Übermittlungen neuer Datenanbieter an das MRTK variiert von Fall zu Fall und wird zum Zeitpunkt des ersten Vorschlags kommuniziert.

> [!Important]
> Wenn ein Eingabesystemdatenanbieter an das [Mixed Reality Toolkit-Repository](https://github.com/Microsoft/MixedRealityToolkit-Unity)übermittelt  wird, muss der Namespace mit Microsoft.MixedReality.Toolkit (z.B. Microsoft.MixedReality.Toolkit.WindowsMixedReality) beginnen, und der Code sollte sich in einem Ordner unter MRTK/Providers (z.B. MRTK/Providers/WindowsMixedReality) befinden.

### <a name="namespace"></a>Namespace

Datenanbieter müssen über einen Namespace verfügen, um potenzielle Namenskollisionen zu minimieren. Es wird empfohlen, dass der -Namespace die folgenden Komponenten enthält.

- Unternehmensname
- Featurebereich

Ein Eingabedatenanbieter, der vom Unternehmen Contoso erstellt wurde, kann beispielsweise "Contoso.MixedReality.Toolkit.Input" sein.

### <a name="recommended-folder-structure"></a>Empfohlene Ordnerstruktur

Es wird empfohlen, den Quellcode für Datenanbieter in einer Ordnerhierarchie zu erstellen, wie in der folgenden Abbildung dargestellt.

![Beispiel für die Paketordnerstruktur](../images/input/ExampleProviderFolderStructure.png)

Wenn ContosoInput die Implementierung des Datenanbieters enthält, enthält der Ordner Editor den Inspektor (und anderen spezifischen Code des Unity-Editors), der Ordner Texturen enthält Bilder der unterstützten Controller und Profile ein oder mehrere vorgefertigte Profile.

> [!Note]
> Einige gängige Controllerbilder finden Sie im Ordner MixedRealityToolkit\StandardAssets\Textures.

## <a name="implement-the-data-provider"></a>Implementieren des Datenanbieters

### <a name="specify-interface-andor-base-class-inheritance"></a>Angeben der Vererbung von Schnittstellen und/oder Basisklassen

Alle Eingabesystemdatenanbieter müssen die -Schnittstelle implementieren, die die für das Eingabesystem erforderliche [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) Mindestfunktionalität angibt. Die MRTK-Grundlage enthält die [`BaseInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) -Klasse, die eine Standardimplementierung dieser erforderlichen Funktionalität bietet. Für Geräte, die auf der UInput-Klasse von Unity aufbauen, kann die -Klasse [`UnityJoystickManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) als Basisklasse verwendet werden.

> [!Note]
> Die `BaseInputDeviceManager` Klassen und stellen die erforderliche Implementierung zur `UnityJoystickManager` `IMixedRealityInputDeviceManager` Verfügung.

```c#
public class WindowsMixedRealityDeviceManager :
    BaseInputDeviceManager,
    IMixedRealityCapabilityCheck
{ }
```

> `IMixedRealityCapabilityCheck` wird von verwendet, um anzugeben, dass es Unterstützung für eine Reihe von Eingabefunktionen bietet, insbesondere für artikulierte Hände, Hände mit Blickgesten, Spracheingaben `WindowsMixedRealityDeviceManager` und Motion-Controller.

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a>Anwenden des MixedRealityDataProvider-Attributs

Ein wichtiger Schritt beim Erstellen eines Eingabesystemdatenanbieters besteht in der Anwendung des [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) -Attributs auf die -Klasse. Dieser Schritt ermöglicht das Festlegen des Standardprofils und der Plattform(en) für den Anbieter, wenn es im Eingabesystemprofil ausgewählt ist.

```c#
[MixedRealityDataProvider(
    typeof(IMixedRealityInputSystem),
    SupportedPlatforms.WindowsUniversal,
    "Windows Mixed Reality Device Manager")]
public class WindowsMixedRealityDeviceManager :
    BaseInputDeviceManager,
    IMixedRealityCapabilityCheck
{ }
```

### <a name="implement-the-imixedrealitydataprovider-methods"></a>Implementieren der IMixedRealityDataProvider-Methoden

Nachdem die Klasse definiert wurde, besteht der nächste Schritt im Bereitstellen der Implementierung der [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) -Schnittstelle.

> [!Note]
> Die `BaseInputDeviceManager` -Klasse stellt über `BaseService` die -Klasse nur leere Implementierungen für -Methoden `IMixedRealityDataProvider` zur Anwendung. Die Details dieser Methoden sind im Allgemeinen datenanbieterspezifisch.

Die Methoden, die vom Datenanbieter implementiert werden sollten, sind:

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

### <a name="implement-the-data-provider-logic"></a>Implementieren der Datenanbieterlogik

Der nächste Schritt besteht im Hinzufügen der Logik zum Verwalten der Eingabegeräte, einschließlich aller zu unterstützenden Controller.

### <a name="implement-the-controller-classes"></a>Implementieren der Controllerklassen

 Im Beispiel von werden `WindowsMixedRealityDeviceManager` die folgenden Controllerklassen definiert und implementiert.

> Den Quellcode für jede dieser Klassen finden Sie im Ordner MRTK/Providers/WindowsMixedReality.

- WindowsMixedRealityArticulatedHand.cs
- WindowsMixedRealityController.cs
- WindowsMixedRealityGGVHand.cs

> [!Note]
> Nicht alle Geräte-Manager unterstützen mehrere Controllertypen.

#### <a name="apply-the-mixedrealitycontroller-attribute"></a>Anwenden des MixedRealityController-Attributs

Wenden Sie als Nächstes [`MixedRealityController`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityControllerAttribute) das -Attribut auf die -Klasse an. Dieses Attribut gibt den Typ des Controllers (z. B. artikulierte Hand), die Übergabe (z. B. links oder rechts) und ein optionales Controllerimage an.

```c#
[MixedRealityController(
    SupportedControllerType.WindowsMixedReality,
    new[] { Handedness.Left, Handedness.Right },
    "StandardAssets/Textures/MotionController")]
{ }
```

#### <a name="configure-the-interaction-mappings"></a>Konfigurieren der Interaktionszuordnungen

Im nächsten Schritt wird der Satz von Interaktionszuordnungen definiert, die vom Controller unterstützt werden. Für Geräte, die ihre Daten über die [](../tools/controller-mapping-tool.md) Eingabeklasse von Unity empfangen, ist das Controllerzuordnungstool eine hilfreiche Ressource, um die richtigen Achsen- und Schaltflächenzuordnungen zu bestätigen, die Interaktionen zugewiesen werden sollen.

Das folgende Beispiel wird von der -Klasse abgekürzt, die sich im Ordner `GenericOpenVRController` MRTK/Providers/OpenVR befindet.

```c#
public override MixedRealityInteractionMapping[] DefaultLeftHandedInteractions => new[]
{
    // Controller Pose
    new MixedRealityInteractionMapping(0, "Spatial Pointer", AxisType.SixDof, DeviceInputType.SpatialPointer, MixedRealityInputAction.None),
    // Left Trigger Squeeze
    new MixedRealityInteractionMapping(1, "Trigger Position", AxisType.SingleAxis, DeviceInputType.Trigger, ControllerMappingLibrary.AXIS_9),
    // Left Trigger Press (Select)
    new MixedRealityInteractionMapping(2, "Trigger Press (Select)", AxisType.Digital, DeviceInputType.TriggerPress, KeyCode.JoystickButton14),
};
```

>[!Note]
>Die [`ControllerMappingLibrary`](xref:Microsoft.MixedReality.Toolkit.Input.ControllerMappingLibrary) -Klasse stellt symbolische Konstanten für die Unity-Eingabeachsen- und Schaltflächendefinitionen dar.

### <a name="raise-notification-events"></a>Benachrichtigungsereignisse

Damit Anwendungen auf Eingaben des Benutzers reagieren können, löst der Datenanbieter Benachrichtigungsereignisse aus, die den In den Schnittstellen und definierten Controllerzustandsänderungen [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) entsprechend sind.

Für digitale Steuerelemente vom Typ (Schaltfläche) können Sie die Ereignisse OnInputDown und OnInputUp aktivieren.

```c#
// inputAction is the input event that is to be raised.
if (interactionSourceState.touchpadPressed)
{
    InputSystem?.RaiseOnInputDown(InputSource, ControllerHandedness, inputAction);
}
else
{
    InputSystem?.RaiseOnInputUp(InputSource, ControllerHandedness, inputAction);
}
```

Für analoge Steuerelemente (z. B. Touchpadposition) sollte das InputChanged-Ereignis ausgelöst werden.

```c#
InputSystem?.RaisePositionInputChanged(InputSource, ControllerHandedness, interactionMapping.MixedRealityInputAction, interactionSourceState.touchpadPosition);
```

### <a name="add-unity-profiler-instrumentation"></a>Hinzufügen der Unity Profiler-Instrumentierung

Die Leistung ist in Mixed Reality-Anwendungen von entscheidender Bedeutung. Jede Komponente erhöht den Mehraufwand, den Anwendungen berücksichtigen müssen. Zu diesem Zweck ist es wichtig, dass alle Eingabedatenanbieter die Unity Profiler-Instrumentierung in einer inneren Schleife und häufig genutzten Codepfaden enthalten.

Es wird empfohlen, das muster zu implementieren, das vom MRTK beim Instrumentieren benutzerdefinierter Anbieter verwendet wird.

```c#
        private static readonly ProfilerMarker GetOrAddControllerPerfMarker = new ProfilerMarker("[MRTK] WindowsMixedRealityDeviceManager.GetOrAddController");

        private async void GetOrAddController(InteractionSourceState interactionSourceState)
        {
            using (GetOrAddControllerPerfMarker.Auto())
            {
                // Code to be measured.
            }
        }
```

> [!Note]
> Der Name, der zum Identifizieren des Profilermarkers verwendet wird, ist willkürlich. Das MRTK verwendet das folgende Muster.
>
> "[product] className.methodName – optionaler Hinweis"
>
> Es wird empfohlen, dass benutzerdefinierte Datenanbieter ein ähnliches Muster befolgen, um die Identifizierung bestimmter Komponenten und Methoden bei der Analyse von Ablaufverfolgungen zu vereinfachen.

## <a name="create-the-profile-and-inspector"></a>Erstellen des Profils und Inspektors

Im Mixed Reality Toolkit werden Datenanbieter mithilfe der Profile [konfiguriert.](../profiles/profiles.md)

Datenanbieter mit zusätzlichen Konfigurationsoptionen (z. B. [InputSimulationService](../input-simulation/input-simulation-service.md)) sollten ein Profil und einen Inspektor erstellen, damit Kunden das Verhalten so ändern können, dass es den Anforderungen der Anwendung am besten entspricht.

> Den vollständigen Code für das Beispiel in diesem Abschnitt finden Sie im MRTK. Ordner "Services/InputSimulation".

### <a name="define-the-profile"></a>Definieren des Profils

Der Profilinhalt sollte die zugänglichen Eigenschaften des Beobachters spiegeln (z. B. Updateintervall). Alle vom Benutzer konfigurierbaren Eigenschaften, die in jeder Schnittstelle definiert sind, sollten im Profil enthalten sein.

```c#
[CreateAssetMenu(
    menuName = "Mixed Reality Toolkit/Profiles/Mixed Reality Simulated Input Profile",
    fileName = "MixedRealityInputSimulationProfile",
    order = (int)CreateProfileMenuItemIndices.InputSimulation)]
public class MixedRealityInputSimulationProfile : BaseMixedRealityProfile
{ }
```

Das -Attribut kann auf die Profilklasse angewendet werden, damit Kunden über das Menü Create > Assets > Mixed Reality Toolkit > Profiles eine `CreateAssetMenu` **Profilinstanz erstellen können.**

### <a name="implement-the-inspector"></a>Implementieren des Inspektors

Profilinspektoren sind die Benutzeroberfläche zum Konfigurieren und Anzeigen von Profilinhalten. Jeder Profilinspektor sollte die [Klasse "BaseMixedRealityToolkitConfigurationProfileInspector"](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) erweitern.

```c#
[CustomEditor(typeof(MixedRealityInputSimulationProfile))]
public class MixedRealityInputSimulationProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

Das `CustomEditor` -Attribut informiert Unity über den Typ des Assets, auf das der Inspektor angewendet wird.

## <a name="create-assembly-definitions"></a>Erstellen von Assemblydefinitionen

Das Mixed Reality Toolkit verwendet Assemblydefinitionsdateien[(ASMDEF-Dateien),](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)um Abhängigkeiten zwischen Komponenten anzugeben und Unity bei der Reduzierung der Kompilierungszeit zu unterstützen.

Es wird empfohlen, Assemblydefinitionsdateien für alle Datenanbieter und deren Editor-Komponenten zu erstellen.

Bei Verwendung [der Ordnerstruktur](#recommended-folder-structure) im früheren Beispiel gibt es zwei ASMDEF-Dateien für den ContosoInput-Datenanbieter.

Die erste Assemblydefinition ist für den Datenanbieter. In diesem Beispiel heißt sie ContosoInput und befindet sich im Ordner ContosoInput des Beispiels.
Diese Assemblydefinition muss eine Abhängigkeit von Microsoft.MixedReality.Toolkit und allen anderen Assemblys angeben, von denen sie abhängt.

Die ContosoInputEditor-Assemblydefinition gibt den Profilinspektor und jeden editorspezifischen Code an. Diese Datei muss sich im Stammordner des Editorcodes befinden. In diesem Beispiel befindet sich die Datei im Ordner ContosoInput\Editor. Diese Assemblydefinition enthält einen Verweis auf die ContosoInput-Assembly sowie:

- Microsoft.MixedReality.Toolkit
- Microsoft.MixedReality.Toolkit.Editor.Inspectors
- Microsoft.MixedReality.Toolkit.Editor.Utilities

## <a name="register-the-data-provider"></a>Registrieren des Datenanbieters

Nach derEntstellung kann der Datenanbieter beim Eingabesystem registriert und in der Anwendung verwendet werden.

![Registrierte Eingabesystemdatenanbieter](../images/input/RegisteredServiceProviders.PNG)

## <a name="packaging-and-distribution"></a>Verpacken und Verteilen

Datenanbieter, die als Drittanbieterkomponenten verteilt werden, haben die spezifischen Details der Paketierung und Verteilung nach Wunsch des Entwicklers. Wahrscheinlich ist die gängigste Lösung die Generierung eines UNITYPACKAGE-Pakets und das Verteilen über das Unity-Medienobjekt Store.

Wenn ein Datenanbieter als Teil des Microsoft Mixed Reality Toolkit-Pakets übermittelt und akzeptiert wird, packt und verteilt das Microsoft MRTK-Team ihn im Rahmen der MRTK-Angebote.

## <a name="see-also"></a>Siehe auch

- [Eingabesystem](overview.md)
- [`BaseInputDeviceManager`-Klasse](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager)
- [`IMixedRealityInputDeviceManager` Schnittstelle](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager)
- [`IMixedRealityInputHandler` Schnittstelle](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler)
- [`IMixedRealityInputHandler<T>` Schnittstelle](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1)
- [`IMixedRealityDataProvider` Schnittstelle](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [`IMixedRealityCapabilityCheck` Schnittstelle](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [Controllerzuordnungstool](../tools/controller-mapping-tool.md)
