---
title: Erstellen eines Anbieters für Kameraeinstellungen
description: Datenanbieter für Kameraeinstellungen in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 2151887a6162239e993634d5d346065362f1c428
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2021
ms.locfileid: "114282033"
---
# <a name="creating-a-camera-settings-provider"></a>Erstellen eines Anbieters für Kameraeinstellungen

Das Kamerasystem ist ein erweiterbares System für die Unterstützung plattformspezifischer Kamerakonfigurationen. Um Unterstützung für eine neue Kamerakonfiguration hinzuzufügen, ist möglicherweise ein benutzerdefinierter Einstellungsanbieter erforderlich.

> [!NOTE]
> Den vollständigen Quellcode, der in diesem Beispiel verwendet wird, finden Sie im Ordner **MRTK/Providers/UnityAR.**

## <a name="namespace-and-folder-structure"></a>Namespace- und Ordnerstruktur

Datenanbieter können auf zwei Arten verteilt werden:

1. Add-Ons von Drittanbietern
1. Teil des Microsoft Mixed Reality Toolkit

Der Genehmigungsprozess für die Übermittlung neuer Datenanbieter an das MRTK variiert von Fall zu Fall und wird zum Zeitpunkt des ursprünglichen Vorschlags kommuniziert. Vorschläge können übermittelt werden, indem ein neues Problem vom Typ [ *Featureanforderung*](https://github.com/microsoft/MixedRealityToolkit-Unity/issues)erstellt wird.

### <a name="third-party-add-ons"></a>Add-Ons von Drittanbietern

**Namespace**

Datenanbieter müssen über einen Namespace verfügen, um potenzielle Namenskonflikte zu minimieren. Es wird empfohlen, dass der Namespace die folgenden Komponenten enthält.

- Firmenname, der das Add-On erzeugt
- Featurebereich

Ein Anbieter für Kameraeinstellungen, der vom Contoso-Unternehmen erstellt und ausgeliefert wird, kann beispielsweise *"Contoso.MixedReality.Toolkit.Camera" sein.*

**Ordnerstruktur**

Es wird empfohlen, den Quellcode für Datenanbieter in einer Ordnerhierarchie zu erstellen, wie in der folgenden Abbildung dargestellt.

![Beispiel für die Paketordnerstruktur](../images/camera-system/ExampleProviderFolderStructure.png)

Wenn der Ordner *ContosoCamera* die Implementierung des Datenanbieters enthält, enthält der *Ordner Editor* den Inspektor (und jeglichen anderen Unity-Editor-spezifischen Code), und der Ordner *Profile* enthält ein oder mehrere vorgefertigte Profile, die skriptfähig sind.

### <a name="mrtk-submission"></a>MRTK-Übermittlung

**Namespace**

Wenn ein Kameraeinstellungsanbieter an das [Mixed Reality Toolkit-Repository](https://github.com/Microsoft/MixedRealityToolkit-Unity)übermittelt wird, **muss** der Namespace mit Microsoft.MixedReality.Toolkit (z.B. *Microsoft.MixedReality.Toolkit.CameraSystem)* beginnen.

**Ordnerstruktur**

Der gesamte Code muss sich in einem Ordner unter MRTK/Providers (z.B. MRTK/Providers/UnityAR) befinden.

## <a name="define-the-camera-settings-object"></a>Definieren des Kameraeinstellungsobjekts

Der erste Schritt beim Erstellen eines Kameraeinstellungsanbieters besteht darin, den Typ der Daten (z. B. Gitternetze oder Ebenen) zu bestimmen, die für Anwendungen zur Verfügung stehen.

Alle räumlichen Datenobjekte müssen die [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) -Schnittstelle implementieren.

## <a name="implement-the-settings-provider"></a>Implementieren des Einstellungsanbieters

### <a name="specify-interface-andor-base-class-inheritance"></a>Angeben der Schnittstellen- und/oder Basisklassenvererbung

Alle Kameraeinstellungsanbieter müssen die [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) -Schnittstelle implementieren, die die mindest erforderliche Funktionalität des Kamerasystems angibt. Die MRTK-Grundlage enthält die [`BaseCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider) -Klasse, die eine Standardimplementierung der erforderlichen Funktionalität bereitstellt.

```c#
namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    public class UnityARCameraSettings : BaseCameraSettingsProvider
    { }
}
```

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a>Anwenden des MixedRealityDataProvider-Attributs

Ein wichtiger Schritt beim Erstellen eines Kameraeinstellungsanbieters besteht darin, das [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) -Attribut auf die -Klasse anzuwenden. Mit diesem Schritt können Sie das Standardprofil und die Plattformen für den Datenanbieter festlegen, wenn sie im Kamerasystemprofil ausgewählt sind, sowie Name, Ordnerpfad usw.

```c#
    [MixedRealityDataProvider(
        typeof(IMixedRealityCameraSystem),
        SupportedPlatforms.Android | SupportedPlatforms.IOS,
        "Unity AR Foundation Camera Settings",
        "UnityAR/Profiles/DefaultUnityARCameraSettingsProfile.asset",
        "MixedRealityToolkit.Providers")]
    public class UnityARCameraSettings : BaseCameraSettingsProvider
    { }
```

### <a name="implement-the-imixedrealitydataprovider-methods"></a>Implementieren der IMixedRealityDataProvider-Methoden

Nachdem die -Klasse definiert wurde, besteht der nächste Schritt darin, die Implementierung der [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) -Schnittstelle bereitzustellen.

> [!NOTE]
> Die [`BaseDataProvider`](xref:Microsoft.MixedReality.Toolkit.BaseDataProvider`1) -Klasse stellt über die [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) -Klasse leere Implementierungen für [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) Methoden bereit. Die Details dieser Methoden sind im Allgemeinen datenanbieterspezifisch.

Der Datenanbieter sollte folgende Methoden implementieren:

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

> [!NOTE]
> Nicht alle Einstellungsanbieter erfordern Implementierungen für alle diese Methoden. Es wird dringend empfohlen, `Destroy()` dass und mindestens implementiert `Initialize()` werden.

### <a name="implement-the-data-provider-logic"></a>Implementieren der Datenanbieterlogik

Im nächsten Schritt fügen Sie die Logik des Einstellungsanbieters hinzu, indem Sie [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) implementieren. Dieser Teil des Datenanbieters ist in der Regel kamerakonfigurationsspezifisch.

## <a name="create-the-profile-and-inspector"></a>Erstellen des Profils und des Inspektors

Im Mixed Reality Toolkit werden Datenanbieter mithilfe von [Profilen](../profiles/profiles.md)konfiguriert.

### <a name="define-the-profile"></a>Definieren des Profils

Profilinhalte sollten die vom Entwickler auswählbaren Konfigurationsoptionen widerspiegeln. Alle vom Benutzer konfigurierbaren Eigenschaften, die in jeder Schnittstelle definiert sind, sollten auch im Profil enthalten sein.

```c#
using UnityEngine.SpatialTracking;

namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    [CreateAssetMenu(
        menuName = "Mixed Reality Toolkit/Profiles/Unity AR Camera Settings Profile",
        fileName = "UnityARCameraSettingsProfile",
        order = 100)]
    public class UnityARCameraSettingsProfile : BaseCameraSettingsProfile
    {
        [SerializeField]
        [Tooltip("The portion of the device (ex: color camera) from which to read the pose.")]
        private ArTrackedPose poseSource = TrackedPoseDriver.TrackedPose.ColorCamera;

        /// <summary>
        /// The portion of the device (ex: color camera) from which to read the pose.
        /// </summary>
        public ArTrackedPose PoseSource => poseSource;

        [SerializeField]
        [Tooltip("The type of tracking (position and/or rotation) to apply.")]
        private ArTrackingType trackingType = TrackedPoseDriver.TrackingType.RotationAndPosition;

        /// <summary>
        /// The type of tracking (position and/or rotation) to apply.
        /// </summary>
        public ArTrackingType TrackingType => trackingType;

        [SerializeField]
        [Tooltip("Specifies when (during Update and/or just before rendering) to update the tracking of the pose.")]
        private ArUpdateType updateType = TrackedPoseDriver.UpdateType.UpdateAndBeforeRender;

        /// <summary>
        /// Specifies when (during Update and/or just before rendering) to update the tracking of the pose.
        /// </summary>
        public ArUpdateType UpdateType => updateType;
    }
}
```

Das `CreateAssetMenu` -Attribut kann auf die Profilklasse angewendet werden, damit Kunden mithilfe des  >  Menüs **Objekte**  >  **Mixed Reality Toolkitprofile** erstellen eine Profilinstanz erstellen  >   können.

### <a name="implement-the-inspector"></a>Implementieren des Inspektors

Profilinspektoren sind die Benutzeroberfläche zum Konfigurieren und Anzeigen von Profilinhalten. Jeder Profilinspektor sollte die [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) -Klasse erweitern.

Das `CustomEditor` -Attribut informiert Unity über den Typ des Medienobjekts, für das der Inspektor gilt.

```c#
namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    [CustomEditor(typeof(UnityARCameraSettingsProfile))]
    public class UnityARCameraSettingsProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
    { }
}
```

## <a name="create-assembly-definitions"></a>Erstellen von Assemblydefinitionen

Das Mixed Reality Toolkit verwendet Assemblydefinitionsdateien[(ASMDEF-Dateien),](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)um Abhängigkeiten zwischen Komponenten anzugeben und Unity bei der Reduzierung der Kompilierungszeit zu unterstützen.

Es wird empfohlen, Assemblydefinitionsdateien für alle Datenanbieter und deren Editorkomponenten zu erstellen.

Wenn Sie die [Ordnerstruktur](#namespace-and-folder-structure) im vorherigen Beispiel verwenden, gibt es zwei ASMDEF-Dateien für den ContosoCamera-Datenanbieter.

Die erste Assemblydefinition ist für den Datenanbieter. In diesem Beispiel heißt sie ContosoCamera und befindet sich im Ordner *ContosoCamera* des Beispiels. Diese Assemblydefinition muss eine Abhängigkeit von Microsoft.MixedReality.Toolkit und allen anderen Assemblys angeben, von denen sie abhängt.

Die Assemblydefinition ContosoCameraEditor gibt den Profilinspektor und jeden editorspezifischen Code an. Diese Datei muss sich im Stammordner des Editorcodes befinden. In diesem Beispiel befindet sich die Datei im Ordner *ContosoCamera\Editor.* Diese Assemblydefinition enthält einen Verweis auf die ContosoCamera-Assembly sowie:

- Microsoft.MixedReality.Toolkit
- Microsoft.MixedReality.Toolkit.Editor.Inspectors
- Microsoft.MixedReality.Toolkit.Editor.Utilities

## <a name="register-the-data-provider"></a>Registrieren des Datenanbieters

Nach der Erstellung kann der Datenanbieter beim Kamerasystem registriert werden, das in der Anwendung verwendet werden soll.

![Auswählen des Anbieters für Kameraeinstellungen](../images/camera-system/SelectUnityArSettings.png)

## <a name="packaging-and-distribution"></a>Verpacken und Verteilen

Datenanbieter, die als Drittanbieterkomponenten verteilt werden, verfügen über die spezifischen Details der Paketierung und Verteilung, die dem Entwickler überlassen werden. Wahrscheinlich ist die gängigste Lösung die Generierung eines UNITYPACKAGE-Pakets und das Verteilen über das Unity-Medienobjekt Store.

Wenn ein Datenanbieter als Teil des Microsoft Mixed Reality Toolkit-Pakets übermittelt und akzeptiert wird, packt und verteilt das Microsoft MRTK-Team ihn im Rahmen der MRTK-Angebote.

## <a name="see-also"></a>Weitere Informationen

- [Übersicht über das Kamerasystem](camera-system-overview.md)
- [`BaseCameraSettingsProvider`-Klasse](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider)
- [`IMixedRealityCameraSettingsProvider` Schnittstelle](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider)
- [`IMixedRealityDataProvider` Schnittstelle](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
