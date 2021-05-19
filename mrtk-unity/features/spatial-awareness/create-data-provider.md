---
title: Erstellen eines räumlichen Bewusstseins Datenanbieter
description: beschreibt, wie benutzerdefinierte Datenanbieter in MRTK erstellt werden.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 04a0cdbd18f666b6a99c120eb28966234cc8c92d
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145152"
---
# <a name="creating-a-spatial-awareness-system-data-provider"></a>Erstellen eines Systemdatenanbieters für räumliche Wahrnehmung

Das Spatial Awareness-System ist ein erweiterbares System zum Bereitstellen von Daten zu realen Umgebungen für Anwendungen. Um Unterstützung für eine neue Hardwareplattform oder eine neue Form von Spatial Awareness-Daten hinzuzufügen, ist möglicherweise ein benutzerdefinierter Datenanbieter erforderlich.

In diesem Artikel wird beschrieben, wie [Sie](../../architecture/systems-extensions-providers.md)benutzerdefinierte Datenanbieter ( auch räumliche Beobachter genannt) für das Spatial Awareness-System erstellen. Der hier gezeigte Beispielcode ist aus der -Klassenimplementierung, die zum Laden von [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) [3D-Gitternetzdaten im Editor nützlich ist.](spatial-object-mesh-observer.md)

> [!NOTE]
> Den vollständigen Quellcode, der in diesem Beispiel verwendet wird, finden Sie im `Assets/MRTK/Providers/ObjectMeshObserver` Ordner .

## <a name="namespace-and-folder-structure"></a>Namespace- und Ordnerstruktur

Datenanbieter können auf zwei Arten verteilt werden:

1. Drittanbieter-Add-Ons
1. Teil des Microsoft Mixed Reality Toolkits

Der Genehmigungsprozess für die Übermittlung neuer Datenanbieter an das MRTK variiert von Fall zu Fall und wird zum Zeitpunkt des ersten Vorschlags kommuniziert. Vorschläge können übermittelt werden, indem ein neues Problem mit dem [ *Funktionsanforderungstyp* erstellt wird.](https://github.com/microsoft/MixedRealityToolkit-Unity/issues)

### <a name="third-party-add-on"></a>Drittanbieter-Add-On

**Namespace**

Datenanbieter müssen über einen Namespace verfügen, um potenzielle Namenskollisionen zu minimieren. Es wird empfohlen, dass der -Namespace die folgenden Komponenten enthält.

- Unternehmensname, der das Add-On erzeugt
- Featurebereich

Ein Vom Unternehmen Contoso erstellter und ausgelieferter Spatial Awareness-Datenanbieter kann beispielsweise *"Contoso.MixedReality.Toolkit.SpatialAwareness" sein.*

**Ordnerstruktur**

Es wird empfohlen, den Quellcode für Datenanbieter in einer Ordnerhierarchie zu erstellen, wie in der folgenden Abbildung dargestellt.

![Beispiel für die Paketordnerstruktur](../images/spatial-awareness/ExampleProviderFolderStructure.png)

Wenn der Ordner *ContosoSpatialAwareness* die Implementierung des Datenanbieters enthält, enthält der *Ordner Editor* den Inspektor (und jeden anderen codespezifischen Code des Unity-Editors), und der Ordner *Profile* enthält ein oder mehrere vorgefertigte Profile, die skriptfähig sind.

### <a name="mrtk-submission"></a>MRTK-Übermittlung

**Namespace**

Wenn ein Systemdatenanbieter für räumliche Wahrnehmung an das [Mixed Reality Toolkit-Repository](https://github.com/Microsoft/MixedRealityToolkit-Unity)übermittelt wird, **muss** der Namespace mit Microsoft.MixedReality.Toolkit (z.B. *Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver)* beginnen.

 und der Code sollte sich in einem Ordner unter MRTK/Providers (z.B. *MRTK/Providers/ObjectMeshObserver)* befinden.

**Ordnerstruktur**

Der gesamte Code sollte sich in einem Ordner unter MRTK/Providers (z. B. MRTK/Providers/ObjectMeshObserver) befinden.

## <a name="define-the-spatial-data-object"></a>Definieren des räumlichen Datenobjekts

Der erste Schritt beim Erstellen eines Datenanbieters für räumliche Wahrnehmung ist die Bestimmung des Datentyps (z. B. Gitternetze oder Ebenen), die für Anwendungen zur Verfügung stehen.

Alle räumlichen Datenobjekte müssen die [`IMixedRealitySpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject) -Schnittstelle implementieren.

Die Mixed Reality Toolkit-Grundlage stellt die folgenden räumlichen Objekte bereit, die in neuen Datenanbietern verwendet oder erweitert werden können.

- [`BaseSpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialAwarenessObject)
- [`SpatialAwarenessMeshObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessMeshObject)
- [`SpatialAwarenessPlanarObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessPlanarObject)

## <a name="implement-the-data-provider"></a>Implementieren des Datenanbieters

### <a name="specify-interface-andor-base-class-inheritance"></a>Angeben der Schnittstellen- und/oder Basisklassenvererbung

Alle Spatial Awareness-Datenanbieter müssen die [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) -Schnittstelle implementieren, die die minimal erforderliche Funktionalität des Spatial Awareness-Systems angibt. Die MRTK-Grundlage enthält die [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) -Klasse, die eine Standardimplementierung dieser erforderlichen Funktionalität bereitstellt.

```c#
public class SpatialObjectMeshObserver :
    BaseSpatialObserver,
    IMixedRealitySpatialAwarenessMeshObserver,
    IMixedRealityCapabilityCheck
{ }
```

> [!NOTE]
> Die [`IMixedRealityCapabilityCheck`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck) -Schnittstelle wird von der [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) -Klasse verwendet, um anzugeben, dass sie Unterstützung für die SpatialAwarenessMesh-Funktion bereitstellt.

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a>Anwenden des MixedRealityDataProvider-Attributs

Ein wichtiger Schritt beim Erstellen eines Datenanbieters für räumliche Wahrnehmung ist das Anwenden des [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) -Attributs auf die -Klasse. Mit diesem Schritt können Sie das Standardprofil und die Plattformen für den Datenanbieter festlegen, wenn sie im Profil räumliche Wahrnehmung sowie name, folder path usw. ausgewählt sind.

```c#
[MixedRealityDataProvider(
    typeof(IMixedRealitySpatialAwarenessSystem),
    SupportedPlatforms.WindowsEditor | SupportedPlatforms.MacEditor | SupportedPlatforms.LinuxEditor,
    "Spatial Object Mesh Observer",
    "ObjectMeshObserver/Profiles/DefaultObjectMeshObserverProfile.asset",
    "MixedRealityToolkit.Providers")]
public class SpatialObjectMeshObserver :
    BaseSpatialObserver,
    IMixedRealitySpatialAwarenessMeshObserver,
    IMixedRealityCapabilityCheck
{ }
```

### <a name="implement-the-imixedrealitydataprovider-methods"></a>Implementieren der IMixedRealityDataProvider-Methoden

Nachdem die -Klasse definiert wurde, besteht der nächste Schritt darin, die Implementierung der [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) -Schnittstelle bereitzustellen.

> [!NOTE]
> Die [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) -Klasse stellt über die [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) -Klasse nur leere Implementierungen für [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) -Methoden bereit. Die Details dieser Methoden sind im Allgemeinen datenanbieterspezifisch.

Folgende Methoden sollten vom Datenanbieter implementiert werden:

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

### <a name="implement-the-data-provider-logic"></a>Implementieren der Datenanbieterlogik

Der nächste Schritt besteht darin, die Logik des Datenanbieters hinzuzufügen, indem die spezifische Datenanbieterschnittstelle implementiert wird, z. [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) B. . Dieser Teil des Datenanbieters ist in der Regel plattformspezifisch.

### <a name="observation-change-notifications"></a>Benachrichtigungen zu Beobachtungsänderungen

Damit Anwendungen auf Änderungen im Verständnis der Umgebung des Geräts reagieren können, löst der Datenanbieter Benachrichtigungsereignisse aus, wie in der [`IMixedRealitySpatialAwarenessObservationtHandler<T>`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObservationHandler`1) -Schnittstelle definiert.

- `OnObservationAdded()`
- `OnObservationRemoved()`
- `OnObservationUpdated()`

 Der folgende Code aus den Beispielen veranschaulicht das [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) Auslösen und Ereignis, wenn Meshdaten hinzugefügt werden.

```c#
// The data to be sent when mesh observation events occur.
// This member variable is initialized as part of the Initialize() method.
private MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> meshEventData = null;

/// <summary>
/// Sends the observations using the mesh data contained within the configured 3D model.
/// </summary>
private void SendMeshObjects()
{
    if (!sendObservations) { return; }

    if (spatialMeshObject != null)
    {
        MeshFilter[] meshFilters = spatialMeshObject.GetComponentsInChildren<MeshFilter>();
        for (int i = 0; i < meshFilters.Length; i++)
        {
            SpatialAwarenessMeshObject meshObject = SpatialAwarenessMeshObject.Create(
                meshFilters[i].sharedMesh,
                MeshPhysicsLayer,
                $"Spatial Object Mesh {currentMeshId}",
                currentMeshId,
                ObservedObjectParent);

            meshObject.GameObject.transform.localPosition = meshFilters[i].transform.position;
            meshObject.GameObject.transform.localRotation = meshFilters[i].transform.rotation;

            ApplyMeshMaterial(meshObject);

            meshes.Add(currentMeshId, meshObject);

            // Initialize the meshEventData variable with data for the added event.
            meshEventData.Initialize(this, currentMeshId, meshObject);
            // Raise the event via the spatial awareness system.
            SpatialAwarenessSystem?.HandleEvent(meshEventData, OnMeshAdded);

            currentMeshId++;
        }
    }

    sendObservations = false;
}
```

> [!NOTE]
> Die [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) -Klasse gibt keine `OnObservationUpdated` Ereignisse aus, da das 3D-Modell nur einmal geladen wird. Die Implementierung in der -Klasse stellt ein Beispiel für das [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) Auslösen eines `OnObservationUpdated` Ereignisses für ein beobachtetes Gitternetz bereit.

### <a name="add-unity-profiler-instrumentation"></a>Hinzufügen der Unity Profiler-Instrumentierung

Leistung ist in Mixed Reality-Anwendungen von entscheidender Bedeutung. Jede Komponente erhöht den Mehraufwand, den Anwendungen berücksichtigen müssen. Zu diesem Zweck ist es wichtig, dass alle Anbieter räumlicher Wahrnehmungsdaten die Unity Profiler-Instrumentierung in inneren Schleifen und häufig verwendeten Codepfaden enthalten.

Es wird empfohlen, das Muster zu implementieren, das vom MRTK beim Instrumentieren benutzerdefinierter Anbieter verwendet wird.

```c#
        private static readonly ProfilerMarker UpdateObserverPerfMarker = new ProfilerMarker("[MRTK] WindowsMixedRealitySpatialMeshObserver.UpdateObserver");

        /// <summary>
        /// Requests updates from the surface observer.
        /// </summary>
        private void UpdateObserver()
        {
            using (UpdateObserverPerfMarker.Auto())
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

### <a name="define-the-profile"></a>Definieren des Profils

Der Profilinhalt sollte die zugänglichen Eigenschaften des Datenanbieters spiegeln (z. B. Updateintervall). Alle vom Benutzer konfigurierbaren Eigenschaften, die in jeder Schnittstelle definiert sind, sollten im Profil enthalten sein.

Basisklassen werden empfohlen, wenn ein neuer Datenanbieter einen vorhandenen Anbieter erweitert. Beispielsweise erweitert das , um Kunden die Bereitstellung eines [`SpatialObjectMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserverProfile) [`MixedRealitySpatialAwarenessMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessMeshObserverProfile) 3D-Modells zu ermöglichen, das als Umgebungsdaten verwendet werden soll.

```c#
[CreateAssetMenu(
    menuName = "Mixed Reality Toolkit/Profiles/Spatial Object Mesh Observer Profile",
    fileName = "SpatialObjectMeshObserverProfile",
    order = 100)]
public class SpatialObjectMeshObserverProfile : MixedRealitySpatialAwarenessMeshObserverProfile
{
    [SerializeField]
    [Tooltip("The model containing the desired mesh data.")]
    private GameObject spatialMeshObject = null;

    /// <summary>
    /// The model containing the desired mesh data.
    /// </summary>
    public GameObject SpatialMeshObject => spatialMeshObject;
}
```

Das -Attribut kann auf die Profilklasse angewendet werden, damit Kunden über das Menü Create Assets Mixed Reality Toolkit Profiles (Erstellen von Ressourcen `CreateAssetMenu`   >    >  **Mixed Reality Toolkitprofile)** eine Profilinstanz erstellen  >   können.

### <a name="implement-the-inspector"></a>Implementieren des Inspektors

Profilinspektoren sind die Benutzeroberfläche zum Konfigurieren und Anzeigen von Profilinhalten. Jeder Profilinspektor sollte die -Klasse [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) erweitern.

Das `CustomEditor` -Attribut informiert Unity über den Typ des Assets, auf das der Inspektor angewendet wird.

```c#
[CustomEditor(typeof(SpatialObjectMeshObserverProfile))]
public class SpatialObjectMeshObserverProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

## <a name="create-assembly-definitions"></a>Erstellen von Assemblydefinitionen

Das Mixed Reality Toolkit verwendet Assemblydefinitionsdateien[(ASMDEF-Dateien),](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)um Abhängigkeiten zwischen Komponenten anzugeben und Unity bei der Reduzierung der Kompilierungszeit zu unterstützen.

Es wird empfohlen, Assemblydefinitionsdateien für alle Datenanbieter und deren Editor-Komponenten zu erstellen.

Bei Verwendung [der Ordnerstruktur](#namespace-and-folder-structure) im früheren Beispiel gibt es zwei ASMDEF-Dateien für den Datenanbieter ContosoSpatialAwareness.

Die erste Assemblydefinition ist für den Datenanbieter. In diesem Beispiel heißt sie ContosoSpatialAwareness und befindet sich im Ordner *ContosoSpatialAwareness des Beispiels.* Diese Assemblydefinition muss eine Abhängigkeit von Microsoft.MixedReality.Toolkit und allen anderen Assemblys angeben, von denen sie abhängt.

Die ContosoInputEditor-Assemblydefinition gibt den Profilinspektor und jeden editorspezifischen Code an. Diese Datei muss sich im Stammordner des Editorcodes befinden. In diesem Beispiel befindet sich die Datei im Ordner *ContosoSpatialAwareness\Editor.* Diese Assemblydefinition enthält einen Verweis auf die ContosoSpatialAwareness-Assembly sowie:

- Microsoft.MixedReality.Toolkit
- Microsoft.MixedReality.Toolkit.Editor.Inspectors
- Microsoft.MixedReality.Toolkit.Editor.Utilities

## <a name="register-the-data-provider"></a>Registrieren des Datenanbieters

Nach der Erstellung kann der Datenanbieter beim Spatial Awareness-System registriert werden, das in der Anwendung verwendet werden soll.

![Auswählen des Raumobjektgittermodell-Beobachters](../images/spatial-awareness/SelectObjectObserver.png)

## <a name="packaging-and-distribution"></a>Verpacken und Verteilen

Datenanbieter, die als Drittanbieterkomponenten verteilt werden, verfügen über die spezifischen Details der Paketierung und Verteilung, die dem Entwickler überlassen werden. Wahrscheinlich ist die gängigste Lösung die Generierung eines UNITY-Pakets und die Verteilung über den Unity Asset Store.

Wenn ein Datenanbieter als Teil des Microsoft Mixed Reality Toolkit-Pakets übermittelt und akzeptiert wird, packt und verteilt das Microsoft MRTK-Team ihn im Rahmen der MRTK-Angebote.

## <a name="see-also"></a>Weitere Informationen

- [System für die räumliche Wahrnehmung](spatial-awareness-getting-started.md)
- [`IMixedRealitySpatialAwarenessObject` Schnittstelle](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject)
- [`BaseSpatialAwarenessObject`-Klasse](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialAwarenessObject)
- [`SpatialAwarenessMeshObject`-Klasse](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessMeshObject)
- [`SpatialAwarenessPlanarObject`-Klasse](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessPlanarObject)
- [`IMixedRealitySpatialAwarenessObserver` Schnittstelle](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
- [`BaseSpatialObserver`-Klasse](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
- [`IMixedRealitySpatialAwarenessMeshObserver` Schnittstelle](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
- [`IMixedRealityDataProvider` Schnittstelle](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [`IMixedRealityCapabilityCheck` Schnittstelle](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
