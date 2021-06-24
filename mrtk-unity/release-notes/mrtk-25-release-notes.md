---
title: 'MRTK 2.5: Anmerkungen zu dieser Version'
description: Versionshinweise für MRTK Version 2.5
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 536a37b56b4c7de9875ce1e1642922bd363fecb1
ms.sourcegitcommit: f7839221c9549e60a2c3ac2dbd39f07a6851dcd2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/23/2021
ms.locfileid: "112562490"
---
# <a name="microsoft-mixed-reality-toolkit-25-release-notes"></a>Versionshinweise Mixed Reality Microsoft Mixed Reality Toolkit 2.5

> [!IMPORTANT]
> Es gibt ein bekanntes Compilerproblem, das anwendungen betrifft, die für Microsoft HoloLens 2 mit ARM64 erstellt wurden. Dieses Problem wird behoben, indem Visual Studio 2019 auf Version 16.8 oder höher aktualisiert wird. Wenn sie nicht aktualisiert werden Visual Studio, importieren Sie das `com.microsoft.mixedreality.toolkit.tools` Paket, um eine Problemumgehung anzuwenden.

## <a name="whats-new-in-254"></a>Neues in 2.5.4

### <a name="fixes-a-bug-with-oculus-integration-when-using-upm"></a>Behebt einen Fehler bei der Oculus-Integration bei Verwendung von UPM

Bei Verwendung von UPM würden die [Prefabs](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9160)von OculusXRSDKDeviceManagerProfile beim Start immer auf Keine festgelegt. Dieses Release konfiguriert die Geräte-Manager, um beim Start auf einen funktionierenden Satz von Prefabs zu verweisen.

### <a name="fixes-an-issue-with-openxr-via-upm"></a>Behebt ein Problem mit OpenXR über UPM

Behebt ein Problem, bei dem die OpenXR-Anbieter standardmäßig nicht zum link.xml hinzugefügt wurden, sodass neue Projekte nicht auf dem Gerät ausgeführt werden können, wenn OpenXR und MRTK über die Unity-Paket-Manager. Für vorhandene Projekte, für die ein Upgrade durchgeführt wird, muss dies weiterhin manuell hinzugefügt werden.

## <a name="whats-new-in-253"></a>Neues in 2.5.3

### <a name="fixes-a-regression-with-oculus-introduced-in-252"></a>Korrektur einer Regression mit Oculus, die in 2.5.2 eingeführt wurde

2.5.2 führte zu einem Buildproblem bei der [Integration des Oculus SDK](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9083). Dieses Problem wird in diesem Release wie zurückgewendet.

## <a name="whats-new-in-252"></a>Neues in 2.5.2

### <a name="add-support-for-openxr"></a>Unterstützung für OpenXR hinzugefügt

Die erste Unterstützung für das OpenXR-Vorschaupaket von Unity und das OpenXR Mixed Reality Paket von Microsoft wurde hinzugefügt. Weitere Informationen finden Sie auf der Seite [MRTK/XRSDK getting started (Erste Schritte mit MRTK/XRSDK),](../configuration/getting-started-with-mrtk-and-xrsdk.md)im [Unity-Forumbeitrag](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/)oder in der [Microsoft-Dokumentation.](/windows/mixed-reality/develop/unity/openxr-getting-started)

> [!IMPORTANT]
> OpenXR in Unity wird nur unter Unity 2020.3 und höher unterstützt.
> Außerdem werden nur x64-, ARM- und ARM64-Builds unterstützt.

### <a name="boundary-visualization-errors-fixed"></a>Behobene Fehler bei der Begrenzungsvisualisierung

Begrenzungsvisualisierungen, z. B. der Boden oder die Wand, werden jetzt ordnungsgemäß konfiguriert und zur Laufzeit entsprechend dem Begrenzungsprofil angezeigt.

### <a name="msbuild-for-unity-support"></a>Unterstützung von MSBuild für Unity

Die Unterstützung für MSBuild für Unity wurde ab Version 2.5.2 entfernt, um sie an die neuen Paketanleitungen von [Unity auszurichten.](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/)

## <a name="whats-new-in-251"></a>Neues in 2.5.1

### <a name="package-dependency-errors-fixed"></a>Behobene Paketabhängigkeitsfehler

Dieses Release behebt falsche Abhängigkeiten zwischen Paketdateien (z. B.: Dateien in Standardressourcen verweisen nicht mehr falsch auf Dateien in Foundation). Version 2.5.1 fügt auch eine explizite Abhängigkeit von Text Mesh Pro hinzu.

### <a name="standard-assets-package-shaders-copied-to-assetsmrtkshaders"></a>In Assets/MRTK/Shaders kopierte Standard Assets-Paket-Shader

Wenn das Standardressourcenpaket über UPM installiert wird, werden die Shader in den Ordner Assets/MRTK/Shaders kopiert, damit sie nicht mehr unveränderlich sind. Dadurch wird das Problem behoben, dass Shader, die für die universelle Renderpipeline (UNIVERSAL Render Pipeline, URP) aktualisiert wurden, das Legacyverhalten beim nächsten Laden des Projekts rückgängig machen.

### <a name="fixed-teleport-cursor-sticking-to-hands"></a>Fest, dass der Teleportcursor an den Händen bleibt

Dieses Release behebt ein [Problem,](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8755) bei dem der Zielcursor des Teleports an Handvisu visuals bleiben kann.

## <a name="whats-new-in-250"></a>Neues in 2.5.0

### <a name="unity-package-manager-upm-support"></a>Unity-Paket-Manager (UPM)

Das Mixed Reality Toolkit kann jetzt mithilfe des Unity-Tools Paket-Manager.

![MRTK Foundation UPM-Paket](../features/images/packaging/MRTK_FoundationUPM.png)

> [!NOTE]
> Es sind einige manuelle Schritte erforderlich, um die MRTK-UPM-Pakete zu importieren. Weitere Informationen [finden Mixed Reality Toolkit und Unity Paket-Manager](../configuration/usingupm.md) Unity-Tools.

### <a name="oculus-quest-xr-sdk-support"></a>Oculus Quest XR SDK-Unterstützung

MRTK unterstützt jetzt die Ausführung von Oculus Quest-Headsets und -Controllern mithilfe der nativen XR SDK-Pipeline. Handtracking wird dank [eric Provenchers](https://twitter.com/prvncher) Arbeit an MRTK-Quest auch mit dem [Oculus Integration Unity-Paket](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) unterstützt.

Anweisungen zum Bereitstellen Ihres Geräts auf der Oculus Quest mithilfe der neuen Pipeline finden Sie im [Oculus Quest Setup Guide (Oculus Quest-Setuphandbuch).](../supported-devices/oculus-quest-mrtk.md)

### <a name="scrolling-object-collection"></a>Scrolling-Objektsammlung

Die MRTK-UX-Komponente wurde von einem experimentellen Feature aktualisiert und bietet mehr Freiheit beim Layout von 3D-Inhalten unterschiedlicher Größe mit zusätzlicher Unterstützung für Objekte, an die keine Collider angefügt sind. Eine neue Option zum Deaktivieren der Inhaltsmaskierung wurde ebenfalls hinzugefügt, wodurch die Prototyperstellung vereinfacht wird.

Weitere [Informationen finden Sie unter Scrollen der](../features/ux-building-blocks/scrolling-object-collection.md) Objektsammlung.

![Scrolling-Objektsammlung](https://user-images.githubusercontent.com/16922045/94465118-51537900-01b7-11eb-8f8b-bf864a8fee03.gif)

### <a name="teleport-pointer-animation-handling-and-sound-improvements"></a>Verbesserungen bei Animation, Verarbeitung und Sound von Teleportzeigern

Der Teleportzeiger verfügt jetzt über verbesserte Animationen und Audiofeedback. Wir haben auch die Handhabung des Teleportzeigers verbessert, sodass er beim Übergang vom Zeigen auf nahe gelegenen Oberflächen zu weiter entfernten Oberflächen reibungsloser verarbeitet wird.

### <a name="input-simulation-cheat-sheet"></a>Cheat Sheet für die Eingabesimulation

Die HandInteractionExamples-Szene verfügt jetzt über eine konfigurierbare Verknüpfung, um eine Hilfeseite für die Eingabesimulation anzuzeigen.

![Cheat Sheet für die Eingabesimulation](https://user-images.githubusercontent.com/13754172/93232433-dea8cd80-f7b4-11ea-8500-eaee202f606f.png)

### <a name="input-simulation-eye-gaze-with-mouse"></a>Eingabesimulation: Anvschauen mit dem Mauszeiger

Benutzer können jetzt die Maus verwenden, um eye tracking zu simulieren. Sehen Sie sich `Eye Simulation Mode` das Feld im Eingabesimulationsprofil an, und legen Sie es auf Maus fest. Dadurch wird das vorherige Feld `Simulate Eye Position` ersetzt.

![Eye Gaze Mouse](https://user-images.githubusercontent.com/39840334/87720928-892b5280-c76a-11ea-9411-73ab69fc756c.gif)

### <a name="input-simulation-motion-controller-in-editor-play-mode"></a>Eingabesimulations-Bewegungscontroller im Editor-Wiedergabemodus

Benutzer können nun den Bewegungscontroller genau wie Hände im Editor-Wiedergabemodus simulieren. Die Trigger-, Greif- und Menüschaltflächen werden derzeit unterstützt.

### <a name="conical-grab-pointer"></a>Conical-Greifzeiger

Greifze0er können jetzt so konfiguriert werden, dass sie objekte in der Nähe abfragen, indem ein Kegel vom Greifpunkt anstelle einer Kugel verwendet wird. Dies ähnelt eher dem Verhalten der standarden HoloLens 2-Schnittstelle, die objekte in der Nähe mithilfe eines Kegels abfragt. Das DefaultHoloLens2InputSystemProfile wurde ebenfalls angepasst, um das neue zu `ConicalGrabPointer` verwenden.

![Conical Grab-Zeiger](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

### <a name="testutilities-package"></a>Paket "TestUtilities"

Es gibt jetzt ein Paket (Microsoft.MixedReality.Toolkit.Unity.TestUtilities.2.5.0.unitypackage), das die PlayMode- und TestMode-Testinfrastruktur enthält, die das MRTK zum Erstellen von End-to-End-Tests verwendet. Diese Infrastruktur war für das MRTK-Team selbst äußerst praktisch, und wir freuen uns, dass Dies von den Kunden zum Hinzufügen von Testabdeckung zu ihren eigenen Projekten verwendet wird.

Der folgende Code zeigt, wie Sie eine Testhand erstellen, sie an einer bestimmten Position anzeigen, verschieben und dann einheften und öffnen.

```csharp
TestHand leftHand = new TestHand(Handedness.Left);
yield return leftHand.Show(new Vector3(-0.1f, -0.1f, 0.5f));
yield return leftHand.SetGesture(ArticulatedHandPose.GestureId.Pinch);
yield return leftHand.Move(new Vector3(0.2f, 0.2f, 0));
yield return leftHand.SetGesture(ArticulatedHandPose.GestureId.Open);
```

Anweisungen zum Schreiben eines Tests mithilfe dieser TestUtilities finden Sie in diesem Abschnitt zum [Schreiben von Tests.](../contributing/unit-tests.md#writing-tests)

Beispiele für vorhandene Tests, die diese Infrastruktur verwenden, finden Sie unter [PlayModeTests des MRTK.](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Tests/PlayModeTests)

### <a name="support-for-the-leap-motion-451-unity-modules"></a>Unterstützung für die Leap Motion 4.5.1 Unity-Module

Unterstützung für die Leap Motion Unity Modules Version 4.5.1 wurde hinzugefügt, und die Unterstützung für die 4.4.0-Objekte wurde entfernt. Die aktuellen unterstützten Versionen der Leap Motion Unity-Module sind 4.5.0 und 4.5.1.

Es gibt auch einen zusätzlichen Schritt für die anfängliche Leap Motion-Integration. Weitere Informationen finden Sie unter How to Configure the Leap Motion Hand Tracking in MRTK (Konfigurieren der [Leap Motion Hand Tracking in MRTK).](../supported-devices/leap-motion-mrtk.md)

### <a name="spatial-awareness-mesh-observer-better-handles-customization-of-materials"></a>Spatial Awareness Mesh Observer übernimmt die Anpassung von Materialien besser

Mit diesem Release haben `Windows Mixed Reality Spatial Mesh Observer` die - und `Generic XR SDK Spatial Mesh Observer` -Komponenten die Verarbeitung visueller Materialien verbessert. Materialien werden jetzt beibehalten, wenn ein Gitternetz vom Beobachter aktualisiert wurde, wobei sie zuvor auf den Standardwert VisibleMaterial zurückgesetzt wurden, wie im Profil konfiguriert.

Dadurch können Entwickler das Gitternetzmaterial ändern und die Änderungen nicht unerwartet überschreiben lassen.

### <a name="linkxml-created-in-the-mixedrealitytoolkitgenerated-folder"></a>Link.xml im Ordner MixedRealityToolkit.Generated erstellt

Mit der Einführung von Unity Package Manager MRTK schreibt MRTK jetzt eine Datei in den `link.xml` `Assets/MixedRealityToolkit.Generated` Ordner, sofern keine vorhanden ist. Es wird empfohlen, diese Datei (und `link.xml.meta` ) der Quellcodeverwaltung hinzuzufügen. Link.xml wird verwendet, um die [Funktionalität](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML) des Unity-Linkers für verwaltetes Codestriping zu beeinflussen.

Weitere Informationen zur MRTK-link.xml finden Sie im Artikel [ZUM MRTK](../updates-deployment/mrtk-and-managed-code-stripping.md) und zum Berenken von verwaltetem Code.

### <a name="unity-20193-mrtk-configuration-dialog-no-longer-attempts-to-enable-legacy-xr-support"></a>Unity 2019.3+: MRTK-Konfigurationsdialogfeld versucht nicht mehr, Legacy-XR-Unterstützung zu aktivieren

Um potenzielle Konflikte bei der Verwendung der XR-Plattform von Unity zu vermeiden, wurde die Option zum Aktivieren der Legacy-XR-Unterstützung aus dem MRTK-Konfigurationsdialogfeld entfernt. Bei Wunsch kann die Legacy-XR-Unterstützung in Unity 2019 mithilfe von **Edit**  >  **Project Settings**  >
 **Player**  >  **XR Settings** Virtual Reality Supported aktiviert  >  **werden.**

### <a name="reduction-in-initializeonload-overhead"></a>Reduzierung des InitializeOnLoad-Aufwands

Wir haben daran arbeitet, die Menge an Arbeit zu reduzieren, die in InitializeOnLoad-Handlern ausgeführt wird, was zu Verbesserungen bei der Entwicklungsgeschwindigkeit der inneren Schleife führen sollte. InitializeOnLoad-Handler werden jedes Mal ausgeführt, wenn ein Skript kompiliert wird, bevor sie in den Wiedergabemodus wechseln, und auch beim Start des Editors. Diese Handler werden jetzt in deutlich weniger Fällen ausgeführt, was zu allgemeinen Verbesserungen der Reaktionsfähigkeit von Unity führt.

In einigen Fällen musste ein Kompromiss getroffen werden:

- Den [zusätzlichen Integrationsschritt finden Sie](../supported-devices/leap-motion-mrtk.md) unter Leap Motion Hand Tracking Configuration (Leap Motion Hand Tracking-Konfiguration).
- Für Diejenigen, die ARFoundation verwenden, gibt es nun einen zusätzlichen manuellen Schritt in den Schritten für die ersten Schritte.
  Die neuen Schritte finden Sie unter [ARFoundation.](../supported-devices/using-ar-foundation.md#install-required-packages)
- Für Diejenigen, die [Holographic Remoting mit legacy-XR-Pipeline](../features/tools/holographic-remoting.md#legacy-xr-setup-instructions) auf HoloLens 2 verwenden, ist jetzt ein [manueller Schritt](../features/tools/holographic-remoting.md#dotnetwinrt_present-define-written-into-player-settings) erforderlich.

### <a name="bounds-control-graduated"></a>Begrenzungssteuerelement gestaffelt

![Begrenzungssteuerelement](../features/images/bounds-control/MRTK_BoundsControl_Main.png)

[Die Begrenzungssteuerung](../features/ux-building-blocks/bounds-control.md) wurde aus experimentellen Funktionen herausgestuft und verfügt über eine Reihe neuer Features und unmengen von Fehlerbehebungen.
Hier finden Sie eine Liste der Highlights dieses Updates:

- -Eigenschaften werden in Konfigurationen aufgeteilt, wodurch das Einrichten des Begrenzungssteuerelements vereinfacht wird.
- Konfigurationen können über skriptfähige Objekte freigegeben werden.
- Jede Eigenschaft/skriptfähige Eigenschaft kann zur Laufzeit konfiguriert werden.
- bounds control rig wird bei Eigenschaftenänderungen nicht mehr neu erstellt.
- Unterstützung von Übersetzungshandles
- Vollständige Einschränkungsunterstützung über den Einschränkungs-Manager
- Systemintegration für elastische Datenbanken (experimentell)

Der alte Begrenzungsfeld ist jetzt veraltet, und vorhandene Spielobjekte, die begrenzungsfeld verwenden, können [mit dem Migrationstool](../features/tools/migration-window.md) oder dem [Begrenzungsfeldinspektor](../features/ux-building-blocks/bounding-box.md#migrating-to-bounds-control)aktualisiert werden.

### <a name="constraint-manager-component"></a>Einschränkungs-Manager-Komponente

Einschränkungen können jetzt sowohl vom Begrenzungssteuerelement als auch vom Objektmanipulator über die neue [Einschränkungs-Manager-Komponente](../features/ux-building-blocks/constraint-manager.md)verwendet werden. Beide Komponenten erstellen einen Einschränkungs-Manager pro Standard und verarbeiten alle angefügten Einschränkungen automatisch.

Zusätzlich zum automatischen Verhaltenseinschränkungs-Manager ist auch ein manueller Modus enthalten, mit dem Benutzer entscheiden können, welche Einschränkung verarbeitet werden soll.
Aus diesem Grund hat sich die Art und Weise, wie Einschränkungen im Eigenschafteninspektor angezeigt werden, etwas geändert.

<img src="../features/images/constraint-manager/ManualSelection.png" width="600" alt="Inspector view showing manual constraint manager selection">

Die Einschränkungen, die auf die Komponente angewendet werden, werden jetzt als Liste in der Einschränkungs-Manager-Komponente angezeigt, während die Komponente, die den Einschränkungs-Manager verwendet (entweder [Begrenzungssteuerelement](../features/ux-building-blocks/bounds-control.md#constraint-system) oder [Objektmanipulator),](../features/ux-building-blocks/object-manipulator.md#constraint-manager)nun den ausgewählten Einschränkungs-Manager und -Modus (automatisch oder manuell) zeigt.
Weitere Informationen finden Sie im Abschnitt [Einschränkungs-Manager](../features/ux-building-blocks/constraint-manager.md) in unserer Dokumentation.

### <a name="hololens-2-button-material-update"></a>Materialaktualisierung für HoloLens 2 Schaltflächen

Das Vordermaterial HoloLens 2 Schaltfläche wurde aktualisiert, um die schwarze Farbe in MRC zu entfernen.

![Materialaktualisierung für HoloLens 2 Schaltflächen](https://user-images.githubusercontent.com/13754172/94341269-dcf7c900-0042-11eb-9028-e55abd2ead67.png)

### <a name="description-panel-update-movable-example-scene"></a>Aktualisierung des Beschreibungsbereichs, bewegliche Beispielszene

Der Beschreibungsbereich wurde aktualisiert. (SceneDescriptionPanelRev.prefab) Neues Design bietet eine ziehbare obere Leiste, die es dem Benutzer ermöglicht, die gesamte Szene anzupassen/zu verschieben.

![Aktualisierung des Beschreibungsbereichs](https://user-images.githubusercontent.com/13754172/91176366-28a21480-e71d-11ea-9e80-7e219595de9c.png)

### <a name="spatial-mesh-visualization---pulse-on-air-tap"></a>Visualisierung des räumlichen Gitternetzes – Pulse beim Tippen in die Luft

Das Pulse-Shader-Beispiel für das räumliche Gitternetz wurde aktualisiert, damit es dem Shellverhalten HoloLens 2 entspricht.

![Pulse on air-tap (Pulse beim Tippen in die Luft)](https://user-images.githubusercontent.com/13754172/90310153-d0536180-df29-11ea-939a-e9572d4f5670.gif)

### <a name="elastic-system-experimental"></a>Elastisches System (experimentell)

![Elastic System2](../features/images/elastics/Elastics_Main.gif)

MRTK verfügt jetzt über ein [elastisches Simulationssystem,](../features/elastics/elastic-system.md) das eine Vielzahl von erweiterbaren und flexiblen Unterklassen enthält und Bindungen für 4-dimensionale Quaternionsmaße, 3-dimensionale Volumenmaße und einfache lineare Springsysteme bietet.

Derzeit können die folgenden MRTK-Komponenten, die den [Elastics Manager](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) unterstützen, die Funktionalität für elastische Datenbanken nutzen:

- [Begrenzungssteuerelement](../features/ux-building-blocks/bounds-control.md#elastics-experimental)
- [Objektmanipulator](../features/ux-building-blocks/object-manipulator.md#elastics-experimental)

<img src="https://user-images.githubusercontent.com/5544935/88151572-568cba00-cbaf-11ea-91c2-d6b51829b638.gif" width="38%" alt="Expanding an elastic menu">
<img src="https://user-images.githubusercontent.com/5544935/88151578-58567d80-cbaf-11ea-8f96-d24f2cf0d6e9.gif" width="45.7%" alt="Grabbing an elastic coffee cup">

### <a name="joystick-experimental"></a>Schalter (experimentell)

Ein Beispiel für eine Schnittstelle, die ein großes Zielobjekt steuern kann.

![Joystick](https://user-images.githubusercontent.com/43013191/86156887-769ef100-babb-11ea-85be-ed6a6aed89d2.png)

### <a name="color-picker-experimental"></a>Farbauswahl (experimentell)

Ein experimentelles Steuerelement, das es einfach macht, Materialfarben für jedes Objekt zur Laufzeit zu ändern.

![Drei verschiedene Methoden des Farbauswahl-Steuerelements](https://user-images.githubusercontent.com/43013191/85468370-3b536e00-b561-11ea-812c-b3f7d43dd999.png)

![Vier verschiedene Methoden des Farbauswahl-Steuerelements](https://user-images.githubusercontent.com/43013191/85468994-fa0f8e00-b561-11ea-89f2-0810d1998518.png)

## <a name="breaking-changes"></a>Aktuelle Änderungen

### <a name="assembly-definition-files-changes"></a>Änderungen an Assemblydefinitionsdateien

Einige Asmdef-Dateien werden geändert und unterstützen jetzt nur Unity 2018.4.13f1 oder höher. Kompilierungsfehler werden beim Aktualisieren auf MRTK 2.5 in früheren Versionen von Unity angezeigt. Dies kann behoben werden, indem Sie im Projektfenster zu gehen `Assets\MRTK\Providers\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.asmdef` und den fehlenden Verweis im Inspektor entfernen. Wiederholen Sie diese Schritte mit `Assets\MRTK\Providers\Oculus\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.Oculus.asmdef` und `Assets\MRTK\Providers\WindowsMixedReality\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.WMR.asmdef` . Beachten Sie, dass Sie die Änderungen rückgängig machen müssen, indem Sie diese drei Asmdef-Dateien beim Upgrade auf Unity 2019 durch originale (d. h. unveränderte) Dateien ersetzen.

### <a name="imixedrealitypointermediator"></a>IMixedRealityPointerMediator

Diese Schnittstelle wurde aktualisiert, um eine neue Funktion zu erhalten:

```csharp
void SetPointerPreferences(IPointerPreferences pointerPreferences);
```

Wenn Sie über einen benutzerdefinierten Zeigermediator verfügen, der keine DefaultPointerMediator-Unterklasse enthält, müssen Sie diese neue Funktion implementieren. Weitere Hintergrundinformationen dazu, warum dies hinzugefügt wurde, finden Sie in [diesem Problem.](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8243) Dies wurde hinzugefügt, um sicherzustellen, dass Zeigereinstellungen explizit an den Vermittler übergeben werden, anstatt sie implizit basierend auf dem Vorhandensein eines Konstruktors vorzunehmen, der IPointerPreferences verwendet hat.

### <a name="rest--device-portal-api"></a>REST-/Geräteportal-API

Die `UseSSL` statische Eigenschaft wurde von zu `Rest` `DevicePortal` verschoben.

Wenn Sie dies zuvor getan haben...

```csharp
Rest.UseSSL = true
```

Tun Sie dies jetzt...

```csharp
DevicePortal.UseSSL = true
```

### <a name="linkxml"></a>Link.xml

Wenn eine Anwendung zuvor die NuGet-Verteilung des MRTK verwendet hat, wurde die `link.xml` Datei aus dem Foundation-Paket entfernt. Zum Wiederherstellen von Regeln für die Beibehaltung von Code wird beim einmaligen Öffnen des Projekts in Unity eine `link.xml` Standarddatei in `Assets/MixedRealityToolkit.Generated` erstellt. Es wird empfohlen, diese Datei (und `link.xml.meta` ) der Quellcodeverwaltung hinzuzufügen.

### <a name="transform-constraint-changes"></a>Transformationseinschränkungsänderungen

Die TargetTransform-Eigenschaft wurde als veraltet markiert, da sie nicht vom Einschränkungssystem verwendet wurde. Die Einschränkungslogik basiert auf der Transformation, die an die Methoden Initialize und Apply übergeben wird. Abgeleitete Benutzereinschränkungen, die auf dieser Eigenschaft basieren, können targetTransform in ihrer Implementierung zwischenspeichern, indem die Transformation der Einschränkungskomponente gespeichert wird, um das gleiche Verhalten zu erzielen.

Der `worldPoseOnManipulationStart` gespeicherte anfängliche World Pose-Datentyp wurde von MixedRealityPose in MixedRealityTransform geändert, der den lokalen Skalierungswert des bearbeiteten Objekts enthält. Mit dieser Änderung ist es nicht mehr erforderlich, anfängliche Skalierungswerte separat zwischenzuspeichern.

### <a name="new-property-in-imixedrealitydictationsystem"></a>Neue Eigenschaft in IMixedRealityDictationSystem

Der `AudioClip` IMixedRealityDictationSystem-Schnittstelle wurde eine neue Eigenschaft hinzugefügt. Die `AudioClip` -Eigenschaft ermöglicht den Zugriff auf den Audioclip, der der aktuellen Diktatsitzung zugeordnet ist. Benutzer müssen die -Eigenschaft in ihren Skripts implementieren, die die -Schnittstelle implementieren.

### <a name="service-facades-turn-down"></a>Dienstfronten fallen aus

Dienstfronten werden in 2.5 ausgeschaltet. Dieses Feature wurde ursprünglich hinzugefügt, um die Konfiguration der MRTK-Profile zu vereinfachen (durch Erstellen von gefälschten GameObjects in der Szene, die die einzelnen MRTK-Dienste darstellten). Auf lange Sicht möchten wir verhindern, dass gefälschte In-Game-Objekte erstellt werden, und versuchen, sie synchron zu halten (da Datensynchronisierungs- und "Source of Truth"-Probleme schwierig zu skalieren und richtig zu werden sind).

In Version 2.5 werden die Dienstfronthandler beibehalten, um sicherzustellen, dass das Projektupgrade reibungslos verläuft. Alle im Projekt vorhandenen Fassaden werden vom Service-Fassadenhandler gelöscht, um sicherzustellen, dass in 2.5 geöffnete Szenen automatisch korrigiert werden.

Der verbleibende Code, der der Dienstfrontfunktion zugeordnet ist, wird in einer zukünftigen Version entfernt.

### <a name="addition-of-motion-controller-to-input-simulation-service"></a>Hinzufügen eines Bewegungscontrollers zum Eingabesimulationsdienst

Die Motion Controller-Simulation wird jetzt im Editor-Wiedergabemodus parallel zur vorhandenen Handsimulation angeboten. Um diese Änderung zu ermöglichen, sind viele aktuelle Funktionen/Felder/Eigenschaften jetzt als veraltet markiert, `InputSimulationService.cs` und es werden die wichtigsten Änderungen `MixedRealityInputSimulationProfile.cs` vorgenommen. Die Logik und das Verhalten des relevanten Codes bleiben größtenteils unverändert, und der Großteil der veralteten Funktionen usw. bezieht sich auf das Ersetzen des Verweises auf "Hand" auf den allgemeineren Begriff "Controller" (z. B. von `DefaultHandSimulationMode` zu `DefaultControllerSimulationMode` ). Neben dem Abrufen neuer Namen wird der Rückgabetyp bestimmter neuer Funktionen aktualisiert, um der Namens-/Verhaltensänderung zu entsprechen (z. B. `GetControllerDevice` wird basierend auf dem ursprünglichen jetzt anstelle von `GetHandDevice` `BaseController` `SimulatedHand` zurückgegeben).

`IInputSimulationService` verfügt jetzt über neue Eigenschaften `MotionControllerDataLeft` und `MotionControllerDataRight` . `MixedRealityInputSimulationProfile` enthält jetzt neue Felder für die Tastaturzuordnung bestimmter Motion Controller-Schaltflächen.

## <a name="known-issues"></a>Bekannte Probleme

### <a name="cameracache-may-create-a-new-camera-on-shutdown"></a>CameraCache kann beim Herunterfahren eine neue Kamera erstellen

In einigen Situationen (z. B. bei Verwendung des LeapMotion-Anbieters im Unity-Editor) ist es möglich, dass CameraCache die MainCamera beim Herunterfahren neu erstellt. Weitere Informationen finden Sie in [diesem Problem.](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459)

### <a name="filenotfoundexception-when-examples-are-imported-via-unity-package-manager"></a>FileNotFoundException beim Importieren von Beispielen über Unity Paket-Manager

Je nach Länge des Projektpfads können beim Importieren von Beispielen über Unity Paket-Manager FileNotFoundException-Meldungen in der Unity-Konsole generiert werden. Die Ursache hierfür ist der Pfad zur fehlenden Datei, die länger als MAX_PATH (256 Zeichen) ist. Verkürzen Sie zum Auflösen die Länge des Projektpfads.

### <a name="no-spatializer-was-specified-the-application-will-not-support-spatial-sound"></a>Es wurde kein Spatializer angegeben. Die Anwendung unterstützt keinen räumlichen Sound.

Wenn kein Audio spatializer konfiguriert ist, wird die Warnung "No spatializer was specified" (Kein Spatializer wurde angegeben) angezeigt. Dies kann auftreten, wenn kein XR-Paket installiert ist, da Unity Spatializer in diese Pakete einschließt.

Stellen Sie zum Beheben dieser Probleme Sicher, dass:

- **Fenster**  >  **Paket-Manager** mindestens ein XR-Paket installiert ist
- **Mixed Reality Toolkit**  >  **Hilfsprogramme**  >  **Konfigurieren des Unity-Projekts** und Treffen einer Auswahl für **Audio Spatializer**

  ![Auswählen von Audio Spatializer](images/SpatializerSelection.png)

### <a name="nullreferenceexception-object-reference-not-set-to-an-instance-of-an-object-scenetransitionserviceinitialize"></a>NullReferenceException: Objektverweis ist nicht auf eine Instanz eines Objekts festgelegt (SceneTransitionService.Iniinitialisieren)

In einigen Situationen kann das `EyeTrackingDemo-00-RootScene` Öffnen eine NullReferenceException in der Initialize-Methode der SceneTransitionService-Klasse verursachen.
Dieser Fehler liegt daran, dass das Konfigurationsprofil des Scene Transition Service nicht konfiguriert ist. Führen Sie die folgenden Schritte aus, um das Problem zu beheben:

- Navigieren Sie zum `MixedRealityToolkit` -Objekt in der Hierarchie.
- Wählen Sie im Inspektorfenster die Option aus. `Extensions`
- Erweitern Sie diese Erweiterung, wenn sie nicht erweitert ist. `Scene Transition Service`
- Legen Sie den Wert von `Configuration Profile` auf **MRTKExamplesHubSceneTransitionServiceProfile fest.**

![Korrektur des Szenenübergangs](images/FixSceneTransitionProfile.png)

### <a name="oculus-quest"></a>Oculus Quest

Derzeit gibt es ein bekanntes Problem bei der Verwendung des [Oculus XR-Plug-Ins mit für eigenständige Plattformen.](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/) Informationen zu Updates finden Sie unter Oculus bug tracker/forums/release notes (Oculus-Fehlerverfolgung/Foren/Versionshinweise).

Der Fehler wird mit dem folgenden Satz von drei Fehlern bezeichnet:

![Oculus XR-Plug-In-Fehler](https://forum.unity.com/attachments/erori-unity-png.644204/)

### <a name="unityui-and-textmeshpro"></a>UnityUI und TextMeshPro

Es gibt ein bekanntes Problem für neuere Versionen von TextMeshPro (1.5.0+ oder 2.1.1+), bei dem der Standardschriftgrad für Dropdownlisten und fett formatierten Schriftzeichenabstand geändert wurde.

![TMP-Image](https://user-images.githubusercontent.com/68253937/93158069-4d582f00-f6c0-11ea-87ad-94d0ba3ba6e5.png)

Dies kann durch ein Downgrade auf eine frühere Version von TextMeshPro umgearbeitet werden. Weitere [Informationen finden #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) Probleminformationen.
