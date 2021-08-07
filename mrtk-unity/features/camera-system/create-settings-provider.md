---
title: Erstellen eines Anbieters für Kameraeinstellungen
description: Datenanbieter für Kameraeinstellungen im MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 5efab728905cd9885bf49f54b1939f3957cc5815af00dc816a4044a3f659b3bb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210700"
---
# <a name="creating-a-camera-settings-provider"></a>Erstellen eines Anbieters für Kameraeinstellungen

Das Kamerasystem ist ein erweiterbares System zur Bereitstellung von Unterstützung für plattformspezifische Kamerakonfigurationen. Um Unterstützung für eine neue Kamerakonfiguration hinzuzufügen, ist möglicherweise ein benutzerdefinierter Einstellungsanbieter erforderlich.

> [!NOTE]
> Den vollständigen Quellcode, der in diesem Beispiel verwendet wird, finden Sie im Ordner **MRTK/Providers/UnityAR.**

## <a name="namespace-and-folder-structure"></a>Namespace- und Ordnerstruktur

Datenanbieter können auf zwei Arten verteilt werden:

1. Drittanbieter-Add-Ons
1. Teil des Microsoft Mixed Reality Toolkits

Der Genehmigungsprozess für Übermittlungen neuer Datenanbieter an das MRTK variiert von Fall zu Fall und wird zum Zeitpunkt des ersten Vorschlags kommuniziert. Vorschläge können übermittelt werden, indem ein neues Problem mit dem [ *Funktionsanforderungstyp* erstellt wird.](https://github.com/microsoft/MixedRealityToolkit-Unity/issues)

### <a name="third-party-add-ons"></a>Drittanbieter-Add-Ons

**Namespace**

Datenanbieter müssen über einen Namespace verfügen, um potenzielle Namenskollisionen zu minimieren. Es wird empfohlen, dass der -Namespace die folgenden Komponenten enthält.

- Unternehmensname, der das Add-On erzeugt
- Featurebereich

Ein Kameraeinstellungsanbieter, der vom Unternehmen Contoso erstellt und ausgeliefert wird, kann *beispielsweise "Contoso.MixedReality.Toolkit.Camera" sein.*

**Ordnerstruktur**

Es wird empfohlen, den Quellcode für Datenanbieter in einer Ordnerhierarchie zu erstellen, wie in der folgenden Abbildung dargestellt.

![Beispiel für die Paketordnerstruktur](../images/camera-system/ExampleProviderFolderStructure.png)

Enthält der *Ordner ContosoCamera* die Implementierung des Datenanbieters, enthält der *Ordner Editor* den Inspektor (und jeden anderen spezifischen Code des Unity-Editors), und der Ordner *Profiles* enthält mindestens ein vorgefertigtes Profil, für das Skripts erstellt werden können.

### <a name="mrtk-submission"></a>MRTK-Übermittlung

**Namespace**

Wenn ein Kameraeinstellungsanbieter an [das Mixed Reality Toolkit-Repository](https://github.com/Microsoft/MixedRealityToolkit-Unity)  übermittelt wird, muss der Namespace mit Microsoft.MixedReality.Toolkit beginnen (z.B. *Microsoft.MixedReality.Toolkit.CameraSystem*).

**Ordnerstruktur**

Der code muss sich in einem Ordner unter MRTK/Providers befinden (z.B. MRTK/Providers/UnityAR).

## <a name="define-the-camera-settings-object"></a>Definieren des Kameraeinstellungsobjekts

Der erste Schritt beim Erstellen eines Kameraeinstellungsanbieters besteht in der Bestimmung des Datentyps (z. B. Gitternetze oder Ebenen), die er für Anwendungen bereitstellen wird.

Alle räumlichen Datenobjekte müssen die -Schnittstelle [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) implementieren.

## <a name="implement-the-settings-provider"></a>Implementieren des Einstellungsanbieters

### <a name="specify-interface-andor-base-class-inheritance"></a>Angeben der Vererbung von Schnittstellen und/oder Basisklassen

Alle Kameraeinstellungsanbieter müssen die -Schnittstelle implementieren, die die für das Kamerasystem erforderliche [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) Mindestfunktionalität angibt. Die MRTK-Grundlage enthält die [`BaseCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider) -Klasse, die eine Standardimplementierung der erforderlichen Funktionalität bietet.

```c#
namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    public class UnityARCameraSettings : BaseCameraSettingsProvider
    { }
}
```

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a>Anwenden des MixedRealityDataProvider-Attributs

Ein wichtiger Schritt beim Erstellen eines Kameraeinstellungsanbieters ist das Anwenden des [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) -Attributs auf die -Klasse. Dieser Schritt ermöglicht das Festlegen des Standardprofils und der Plattform(en) für den Datenanbieter, wenn es im Profil Kamerasystem ausgewählt ist, sowie name, folder path und mehr.

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

Nachdem die Klasse definiert wurde, besteht der nächste Schritt im Bereitstellen der Implementierung der [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) -Schnittstelle.

> [!NOTE]
> Die [`BaseDataProvider`](xref:Microsoft.MixedReality.Toolkit.BaseDataProvider`1) -Klasse stellt über [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) die -Klasse leere Implementierungen für Methoden [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) zur Anwendung. Die Details dieser Methoden sind im Allgemeinen datenanbieterspezifisch.

Die Methoden, die vom Datenanbieter implementiert werden sollten, sind:

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

## <a name="create-the-profile-and-inspector"></a>Erstellen des Profils und Inspektors

Im Mixed Reality Toolkit werden Datenanbieter mithilfe der Profile [konfiguriert.](../profiles/profiles.md)

### <a name="define-the-profile"></a>Definieren des Profils

Der Profilinhalt sollte die von Entwicklern auswählbaren Konfigurationsoptionen spiegeln. Alle vom Benutzer konfigurierbaren Eigenschaften, die in jeder Schnittstelle definiert sind, sollten ebenfalls im Profil enthalten sein.

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

Das -Attribut kann auf die Profilklasse angewendet werden, damit Kunden mithilfe des Menüs Ressourcen erstellen Mixed Reality `CreateAssetMenu`   >    >  **Toolkitprofile eine Profilinstanz**  >  **erstellen** können.

### <a name="implement-the-inspector"></a>Implementieren des Inspektors

Profilinspektoren sind die Benutzeroberfläche zum Konfigurieren und Anzeigen von Profilinhalten. Jeder Profilinspektor sollte die -Klasse [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) erweitern.

Das `CustomEditor` -Attribut informiert Unity über den Typ des Assets, auf das der Inspektor angewendet wird.

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

Es wird empfohlen, Assemblydefinitionsdateien für alle Datenanbieter und deren Editor-Komponenten zu erstellen.

Bei Verwendung [der Ordnerstruktur](#namespace-and-folder-structure) im früheren Beispiel gibt es zwei ASMDEF-Dateien für den ContosoCamera-Datenanbieter.

Die erste Assemblydefinition ist für den Datenanbieter. In diesem Beispiel heißt sie ContosoCamera und befindet sich im Ordner *ContosoCamera des Beispiels.* Diese Assemblydefinition muss eine Abhängigkeit von Microsoft.MixedReality.Toolkit und allen anderen Assemblys angeben, von denen sie abhängt.

Die Assemblydefinition ContosoCameraEditor gibt den Profilinspektor und jeden editorspezifischen Code an. Diese Datei muss sich im Stammordner des Editorcodes befinden. In diesem Beispiel befindet sich die Datei im Ordner *ContosoCamera\Editor.* Diese Assemblydefinition enthält einen Verweis auf die ContosoCamera-Assembly sowie:

- Microsoft.MixedReality.Toolkit
- Microsoft.MixedReality.Toolkit.Editor.Inspectors
- Microsoft.MixedReality.Toolkit.Editor.Utilities

## <a name="register-the-data-provider"></a>Registrieren des Datenanbieters

Nach derEntstellung kann der Datenanbieter beim Kamerasystem registriert werden, das in der Anwendung verwendet werden soll.

![Auswählen des Kameraeinstellungsanbieters](../images/camera-system/SelectUnityArSettings.png)

## <a name="packaging-and-distribution"></a>Verpacken und Verteilen

Datenanbieter, die als Komponenten von Drittanbietern verteilt werden, haben die spezifischen Details der Paketierung und Verteilung nach Wunsch des Entwicklers. Die wahrscheinlichste Lösung besteht in der Generierung eines UNITYPACKAGE und der Verteilung über das Unity-Store.

Wenn ein Datenanbieter als Teil des Microsoft Mixed Reality Toolkit-Pakets übermittelt und akzeptiert wird, packt und verteilt das Microsoft MRTK-Team es im Rahmen der MRTK-Angebote.

## <a name="see-also"></a>Siehe auch

- [Kamerasystemübersicht](camera-system-overview.md)
- [`BaseCameraSettingsProvider`-Klasse](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider)
- [`IMixedRealityCameraSettingsProvider` Schnittstelle](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider)
- [`IMixedRealityDataProvider` Schnittstelle](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
