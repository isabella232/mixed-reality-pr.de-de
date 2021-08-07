---
title: 'HoloLens (1. Generation) Räumlich 230: Räumliche Abbildung'
description: Befolgen Sie diese exemplarische Vorgehensweise zum Programmieren mit Unity, Visual Studio und HoloLens, um die Details der Konzepte der räumlichen Zuordnung zu erfahren.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, academy, tutorial, spatial mapping, surface en, mesh, HoloLens, Mixed Reality Academy, unity, mixed reality headset, windows mixed reality headset, virtual reality headset, Windows 10
ms.openlocfilehash: 6806fd8c717d47ff4ea5340e6a2d70ba2c798960af8fe3103daa11d0a8e2bf74
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208710"
---
# <a name="hololens-1st-gen-spatial-230-spatial-mapping"></a>HoloLens (1. Generation) Spatial 230: Spatial mapping

>[!IMPORTANT]
>Die Mixed Reality Academy-Tutorials wurden mit HoloLens (1. Generation), Unity 2017 und Mixed Reality immersive Headsets entworfen.  Daher halten wir es für wichtig, diese Tutorials für Entwickler verfügbar zu halten, die noch nach Anleitung beim Entwickeln für diese Geräte suchen. Diese Tutorials werden **_nicht mit_** den neuesten Toolsets oder Interaktionen aktualisiert, die für HoloLens 2 und sind möglicherweise nicht mit neueren Versionen von Unity kompatibel.  Sie werden gewartet, um weiterhin auf den unterstützten Geräten zu funktionieren. [Es wurde eine neue Reihe von Tutorials](mrlearning-base.md) für HoloLens 2 veröffentlicht.

[Bei der räumlichen](../../../design/spatial-mapping.md) Zuordnung werden die reale und die virtuelle Welt miteinander kombiniert, indem Hologramme über die Umgebung beibringen. In MR Spatial 230 (Project Planet eines Planeten) lernen wir:

* Überprüfen Sie die Umgebung, und übertragen Sie Daten vom HoloLens auf Ihren Entwicklungscomputer.
* Erkunden Sie Shader, und erfahren Sie, wie Sie sie zum Visualisieren Ihres Raums verwenden.
* Unterbricht das Raumgitternetz mithilfe der Gitternetzverarbeitung in einfache Ebenen.
* Gehen Sie über die Platzierungstechniken hinaus, die wir in [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md)gelernt haben, und geben Sie Feedback darüber, wo ein Hologramm in der Umgebung platziert werden kann.
* Untersuchen Sie Okklusionseffekte. Wenn sich Ihr Hologramm also hinter einem realen Objekt befindet, können Sie es weiterhin mit dem X-Ray-Sehen sehen!

>[!VIDEO https://www.youtube.com/embed/NSNYRkUX6Mw]

## <a name="device-support"></a>Geräteunterstützung

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td>MR räumlich 230: Räumliche Abbildung</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Vorbereitung

### <a name="prerequisites"></a>Voraussetzungen

* Ein Windows 10 PC, der mit den richtigen [installierten Tools konfiguriert ist.](../../../develop/install-the-tools.md)
* Einige grundlegende C#-Programmierfunktionen.
* Sie sollten die [MR-Grundlagen 101 abgeschlossen haben.](../../../develop/unity/tutorials/holograms-101.md)
* Ein HoloLens, [das für die Entwicklung konfiguriert ist.](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)

### <a name="project-files"></a>Projektdateien

* Laden Sie [die für](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) das Projekt erforderlichen Dateien herunter. Erfordert Unity 2017.2 oder höher.
  * Wenn Sie weiterhin Unity 5.6-Unterstützung benötigen, verwenden Sie [dieses Release.](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip)
  * Wenn Sie weiterhin Unity 5.5-Unterstützung benötigen, verwenden Sie [dieses Release.](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip)
  * Wenn Sie weiterhin Unity 5.4-Unterstützung benötigen, verwenden Sie [dieses Release.](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip)
* Archivieren Sie die Dateien auf Ihrem Desktop oder an einem anderen leicht erreichbaren Speicherort.

>[!NOTE]
>Wenn Sie den Quellcode vor dem Herunterladen durchschauen möchten, ist er [auf GitHub.](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping)

### <a name="notes"></a>Hinweise

* "Enable Nur eigenen Code" in Visual Studio muss unter Extras > Optionen >*Debugging)* deaktiviert (deaktiviert) werden, um Breakpoints im Code zu finden.

## <a name="unity-setup"></a>Unity-Setup

>[!VIDEO https://www.youtube.com/embed/y2Y4LhK6TEM]

* Starten **Sie Unity**.
* Wählen **Sie Neu** aus, um ein neues Projekt zu erstellen.
* Nennen Sie das **Projekt Planetplan**.
* Überprüfen Sie, ob **die 3D-Einstellung** ausgewählt ist.
* Klicken Sie **auf Project**.
* Sobald Unity gestartet wird, wechseln Sie zu **Bearbeiten > Project Einstellungen > Player**.
* Suchen Sie **im Bereich** Inspector (Inspektor) das grüne Symbol für Windows Store, und wählen **Sie es** aus.
* Erweitern **Sie Andere Einstellungen**.
* Aktivieren Sie **im Abschnitt Rendering** die Option Virtual Reality Supported **(Virtual Reality unterstützt).**
* Vergewissern Sie **Windows, dass holographic** in der Liste der **Virtual Reality SDKs angezeigt wird.** Wenn nicht, wählen Sie die Schaltfläche unten in der Liste aus, **+** und wählen Sie Windows **Holographic aus.**
* Erweitern **Sie Veröffentlichung Einstellungen**.
* Überprüfen Sie **im** Abschnitt Funktionen die folgenden Einstellungen:
    * InternetClientServer
    * PrivateNetworkClientServer
    * Mikrofon
    * SpatialPerception
* Wechseln Sie **zu Edit > Project Einstellungen > Quality (> Project Einstellungen > Qualität).**
* Wählen Sie **im Bereich** Inspektor unter Windows Store Symbol den schwarzen Dropdownpfeil unter der Zeile "Standard" aus, und ändern Sie die Standardeinstellung in **Sehr niedrig.**
* Wechseln Sie **zu Assets > Import Package > Custom Package**.
* Navigieren Sie zum **Ordner ...\HolographicAcademy-Hologramme-230-SpatialMapping\Starting.**
* Klicken Sie **auf Planet planet.unitypackage**.
* Klicken Sie auf **Öffnen**.
* Ein **Fenster Unity-Paket importieren** sollte angezeigt werden, und klicken Sie auf die Schaltfläche **Importieren.**
* Warten Sie, bis Unity alle Ressourcen importiert, die wir zum Abschließen dieses Projekts benötigen.
* Löschen Sie **im Bereich** Hierarchie die **Hauptkamera**.
* Suchen Sie **Project** Bereich **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** das **Objekt Hauptkamera.**
* Drag and drop the **Main Camera** prefab into the **Hierarchy** panel.
* Löschen Sie **im Hierarchiebereich** das **Objekt Directional Light.**
* Suchen Sie **im Project** Ordner **Hologramme** Cursor-Objekt. 
* Ziehen &, um das **Cursor-Prefab** in die Hierarchie **zu verschieben.**
* Wählen Sie **im Bereich** Hierarchie das **Cursorobjekt** aus.
* Klicken Sie **im Inspektorbereich** auf das **Dropdownfeld Ebene,** und wählen Sie **Ebenen bearbeiten... aus.**
* Nennen **Sie User Layer 31** "**SpatialMapping**".
* Speichern Sie die neue Szene: **Datei > Speichern der Szene unter...**
* Klicken Sie **auf Neuer Ordner,** und nennen Sie den Ordner **Scenes**.
* Nennen Sie die Datei **"Planetplan",** und speichern Sie sie im **Ordner Scenes.**

## <a name="chapter-1---scanning"></a>Kapitel 1: Scannen

>[!VIDEO https://www.youtube.com/embed/888oW51z_cE]

**Ziele**

* Erfahren Sie mehr über SurfaceObserver und darüber, wie sich seine Einstellungen auf die Benutzererfahrung und Leistung auswirken.
* Erstellen Sie eine Raumscanerfahrung, um die Gitternetze Ihres Zimmers zu erfassen.

**Anweisungen**

* Suchen Sie **Project** Bereich **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** das **Prefab SpatialMapping.**
* Ziehen & das **SpatialMapping-Prefab** in den **Bereich Hierarchie.**

**Erstellen und Bereitstellen (Teil 1)**

* Wählen Sie in Unity **Datei > Build Einstellungen.**
* Klicken **Sie auf Add Open Scenes** (Offene Szenen hinzufügen), um dem Build die **Planetaritenszene** hinzuzufügen.
* Wählen **Sie universelle Windows Plattform** in der **Liste Plattform aus,** und klicken Sie **auf Plattform wechseln.**
* Legen **Sie DAS SDK** auf Universal **10 und** den **UWP-Buildtyp auf** **D3D fest.**
* Überprüfen Sie **Unity C#-Projekte.**
* Klicken Sie auf **Erstellen**.
* Erstellen Sie **einen neuen Ordner** mit dem Namen "App".
* Klicken Sie mit nur einem Klick **auf den Ordner App.**
* Klicken Sie auf **die Schaltfläche Ordner** auswählen.
* Wenn Unity mit dem Erstellen fertig ist, wird ein Datei-Explorer-Fenster angezeigt.
* Doppelklicken Sie auf den **Ordner App,** um ihn zu öffnen.
* Doppelklicken Sie auf **Planetausgleich.sln,** um das Projekt in Visual Studio.
* Verwenden Visual Studio der oberen Symbolleiste, um die Konfiguration in **Release zu ändern.**
* Ändern Sie die Plattform in **x86.**
* Klicken Sie rechts neben "Lokaler Computer" auf den Dropdownpfeil, und wählen Sie **Remotecomputer aus.**
* Geben [Sie die IP-Adresse Ihres Geräts](/hololens/hololens-network#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) in das Feld Adresse ein, und ändern Sie den Authentifizierungsmodus in **Universell (unverschlüsselte Protokolle).**
* Klicken Sie auf **Debuggen -> Ohne Debuggen starten,** oder drücken **Sie STRG+F5.**
* Sehen Sie sich den **Ausgabebereich** in Visual Studio an, um den Build- und Bereitstellungsstatus anzuzeigen.
* Nachdem Ihre App bereitgestellt wurde, können Sie durch den Raum gehen. Sie sehen die umgebenden Oberflächen, die von schwarzen und weißen Wireframe-Gitternetzen abgedeckt sind.
* Überprüfen Sie Ihre Umgebung. Achten Sie darauf, dass Sie sich die Wände, Decken und Etagen ansehen.

**Erstellen und Bereitstellen (Teil 2)**

Sehen wir uns nun an, wie sich die räumliche Zuordnung auf die Leistung auswirken kann.

* Wählen Sie in Unity **Fenster > Profiler aus.**
* Klicken Sie auf **Profiler hinzufügen > GPU**.
* Klicken Sie auf **Active <Enter IP> Profiler >**.
* Geben Sie die **IP-Adresse** Ihrer HoloLens ein.
* Klicken Sie auf **Verbinden**.
* Beobachten Sie die Anzahl von Millisekunden, die die GPU benötigt, um einen Frame zu rendern.
* Beenden Sie die Ausführung der Anwendung auf dem Gerät.
* Kehren Sie zu Visual Studio zurück, und öffnen Sie **SpatialMappingObserver.cs.** Sie finden sie im Ordner HoloToolkit\SpatialMapping des projekts Assembly-CSharp (Universal Windows).
* Suchen Sie die **Funktion Awake(),** und fügen Sie die folgende Codezeile hinzu: **TrianglesPerCubicMeter = 1200;**
* Stellen Sie das Projekt erneut auf Ihrem Gerät bereit, und stellen Sie dann erneut **eine Verbindung mit dem Profiler her.** Beobachten Sie die Änderung der Anzahl von Millisekunden, um einen Frame zu rendern.
* Beenden Sie die Ausführung der Anwendung auf dem Gerät.

**Speichern und Laden in Unity**

Abschließend speichern wir unser Raumgitternetz und laden es in Unity.

* Kehren Sie zu Visual Studio zurück, und entfernen Sie die **Zeile TrianglesPerCubicMeter,** die Sie im vorherigen Abschnitt in der **Funktion "Awake()"** hinzugefügt haben.
* Stellen Sie das Projekt erneut auf Ihrem Gerät bereit. Wir sollten jetzt mit **500** Dreiecken pro Kubikmeter ausgeführt werden.
* Öffnen Sie einen Browser, und geben Sie ihre HoloLens IPAddress ein, um zum **Windows Geräteportal** zu navigieren.
* Wählen Sie im linken Bereich die Option **3D-Ansicht** aus.
* Wählen Sie unter **Oberfläche neu** die Schaltfläche **Aktualisieren** aus.
* Beobachten Sie, wie die Bereiche, die Sie auf Ihrem HoloLens überprüft haben, im Anzeigefenster angezeigt werden.
* Klicken Sie auf die Schaltfläche **Speichern,** um Ihren Raumscan zu speichern.
* Öffnen Sie den Ordner **Downloads,** um das gespeicherte Raummodell **SRMesh.obj** zu suchen.
* Kopieren Sie **SRMesh.obj** in den Ordner **Assets** Ihres Unity-Projekts.
* Wählen Sie in Unity im **Hierarchiebereich** das **Objekt SpatialMapping** aus.
* Suchen Sie die Komponente **Object Surface Observer (Script).**
* Klicken Sie rechts neben der **Room Model-Eigenschaft** auf den Kreis.
* Suchen Sie nach dem **SRMesh-Objekt,** wählen Sie es aus, und schließen Sie dann das Fenster.
* Überprüfen Sie, ob die **Room Model-Eigenschaft** im **Inspektorbereich** jetzt auf **SRMesh** festgelegt ist.
* Klicken Sie auf die Schaltfläche **Wiedergeben,** um in den Vorschaumodus von Unity zu wechseln.
* Die SpatialMapping-Komponente lädt die Gittermodelle aus dem Modell für gespeicherte Räume, damit Sie sie in Unity verwenden können.
* Wechseln Sie zur **Szenenansicht,** um ihr gesamtes Raummodell mit dem Wireframe-Shader anzuzeigen.
* Drücken Sie erneut die Schaltfläche **Wiedergeben,** um den Vorschaumodus zu beenden.

**HINWEIS:** Wenn Sie das nächste Mal in den Vorschaumodus in Unity wechseln, wird standardmäßig das gespeicherte Raumgitternetz geladen.

## <a name="chapter-2---visualization"></a>Kapitel 2: Visualisierung

>[!VIDEO https://www.youtube.com/embed/RnkvXl-aXD4]

**Ziele**

* Lernen Sie die Grundlagen von Shadern kennen.
* Visualisieren Sie Ihre Umgebung.

**Anweisungen**

* Wählen Sie im **Hierarchiebereich** von Unity das **Objekt SpatialMapping** aus.
* Suchen Sie im Bereich **Inspector (Inspektor)** nach der Komponente **Spatial Mapping Manager (Script) (Raumzuordnungs-Manager (Skript)).**
* Klicken Sie rechts neben der **Eigenschaft Surface Material** auf den Kreis.
* Suchen Sie das **BlueLinesOnWalls-Material,** wählen Sie es aus, und schließen Sie das Fenster.
* Doppelklicken **Sie** im ordner Project Panel **Shaders** auf **BlueLinesOnWalls,** um den Shader in Visual Studio zu öffnen.
* Dies ist ein einfacher Pixelshader (Scheitelpunkt zu Fragment), der die folgenden Aufgaben erfüllt:
    1. Konvertiert die Position eines Scheitelpunkts in den Weltraum.
    2. Überprüft die Normalität des Scheitelpunkts, um zu bestimmen, ob ein Pixel vertikal ist.
    3. Legt die Farbe des Pixels für das Rendering fest.

**Erstellen und Bereitstellen**

* Kehren Sie zu Unity zurück, und drücken **Sie Wiedergabe,** um in den Vorschaumodus zu wechseln.
* Blaue Linien werden auf allen vertikalen Oberflächen des Raumgitternetzes gerendert (das automatisch aus unseren gespeicherten Scandaten geladen wird).
* Wechseln Sie zur Registerkarte **Szene,** um Ihre Ansicht des Raumes anzupassen und zu sehen, wie das gesamte Raumgitternetz in Unity angezeigt wird.
* Suchen **Sie** im Project Bereich nach dem Ordner **Materials** , und wählen Sie das Material **BlueLinesOnWalls** aus.
* Ändern Sie einige Eigenschaften, und sehen Sie sich an, wie die Änderungen im Unity-Editor angezeigt werden.
    * Passen Sie im Bereich **Inspector** den **LineScale-Wert** an, damit die Linien breiter oder schlanker erscheinen.
    * Passen Sie im Bereich **Inspector** den **Wert LinesPerMeter** an, um zu ändern, wie viele Zeilen an jeder Wand angezeigt werden.
* Klicken Sie erneut auf **Wiedergeben,** um den Vorschaumodus zu beenden.
* Erstellen Sie die HoloLens und stellen Sie sie bereit, und beobachten Sie, wie das Shaderrendering auf echten Oberflächen angezeigt wird.

Unity bietet eine hervorragende Vorschau von Materialien, aber es ist immer eine gute Idee, das Rendering auf dem Gerät zu überprüfen.

## <a name="chapter-3---processing"></a>Kapitel 3: Verarbeitung

>[!VIDEO https://www.youtube.com/embed/kaUKiNiDxwY]

**Ziele**

* Lernen Sie Techniken zum Verarbeiten räumlicher Zuordnungsdaten für die Verwendung in Ihrer Anwendung kennen.
* Analysieren Sie räumliche Zuordnungsdaten, um Ebenen zu suchen und Dreiecke zu entfernen.
* Verwenden Sie Ebenen für die Hologrammplatzierung.

**Anweisungen**

* Suchen Sie **im Bereich Project** von Unity **Hologramme** Ordner nach dem **SpatialProcessing-Objekt.**
* Ziehen Sie & das **SpatialProcessing-Objekt** in den **Hierarchiebereich.**

Das SpatialProcessing-Prefab enthält Komponenten für die Verarbeitung der räumlichen Zuordnungsdaten. **SurfaceMeshesToPlanes.cs** sucht und generiert Ebenen basierend auf den räumlichen Zuordnungsdaten. Wir verwenden Ebenen in unserer Anwendung, um Wände, Etagen und Decken darzustellen. Dieses Prefab enthält auch **RemoveSurfaceVertices.cs,** das Scheitelpunkte aus dem Gitternetz für räumliche Zuordnungen entfernen kann. Dies kann verwendet werden, um Löcher im Gitternetz zu erstellen oder überflüssige Dreiecke zu entfernen, die nicht mehr benötigt werden (da stattdessen Ebenen verwendet werden können).

* Suchen Sie **im Bereich Project** von Unity **Hologramme** Ordner nach dem **SpaceCollection-Objekt.**
* Drag and drop the **SpaceCollection** object into the **Hierarchy** panel.
* Wählen Sie im **Hierarchiebereich** das **Objekt SpatialProcessing** aus.
* Suchen Sie im **Inspektorbereich** nach der Komponente **Play Space Manager (Script).**
* Doppelklicken Sie auf **PlaySpaceManager.cs,** um es in Visual Studio zu öffnen.

PlaySpaceManager.cs enthält anwendungsspezifischen Code. Wir fügen diesem Skript Funktionen hinzu, um das folgende Verhalten zu ermöglichen:

1. Die Erfassung räumlicher Zuordnungsdaten wird beendet, nachdem das Überprüfungszeitlimit (10 Sekunden) überschritten wurde.
2. Verarbeiten der räumlichen Zuordnungsdaten:
    1. Verwenden Sie SurfaceMeshesToPlanes, um eine einfachere Darstellung der Welt als Ebenen (Wände, Etagen, Decken usw.) zu erstellen.
    2. Verwenden Sie RemoveSurfaceVertices, um Oberflächendreiecke zu entfernen, die innerhalb der Ebenengrenzen liegen.
3. Generieren Sie eine Sammlung von Hologrammen auf der Welt, und platzieren Sie sie auf Denk- und Bodenebenen in der Nähe des Benutzers.

Führen Sie die in PlaySpaceManager.cs markierten Codierungsübungen aus, oder ersetzen Sie das Skript durch die fertige Lösung aus dem Folgenden:

```cs
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;

/// <summary>
/// The SurfaceManager class allows applications to scan the environment for a specified amount of time 
/// and then process the Spatial Mapping Mesh (find planes, remove vertices) after that time has expired.
/// </summary>
public class PlaySpaceManager : Singleton<PlaySpaceManager>
{
    [Tooltip("When checked, the SurfaceObserver will stop running after a specified amount of time.")]
    public bool limitScanningByTime = true;

    [Tooltip("How much time (in seconds) that the SurfaceObserver will run after being started; used when 'Limit Scanning By Time' is checked.")]
    public float scanTime = 30.0f;

    [Tooltip("Material to use when rendering Spatial Mapping meshes while the observer is running.")]
    public Material defaultMaterial;

    [Tooltip("Optional Material to use when rendering Spatial Mapping meshes after the observer has been stopped.")]
    public Material secondaryMaterial;

    [Tooltip("Minimum number of floor planes required in order to exit scanning/processing mode.")]
    public uint minimumFloors = 1;

    [Tooltip("Minimum number of wall planes required in order to exit scanning/processing mode.")]
    public uint minimumWalls = 1;

    /// <summary>
    /// Indicates if processing of the surface meshes is complete.
    /// </summary>
    private bool meshesProcessed = false;

    /// <summary>
    /// GameObject initialization.
    /// </summary>
    private void Start()
    {
        // Update surfaceObserver and storedMeshes to use the same material during scanning.
        SpatialMappingManager.Instance.SetSurfaceMaterial(defaultMaterial);

        // Register for the MakePlanesComplete event.
        SurfaceMeshesToPlanes.Instance.MakePlanesComplete += SurfaceMeshesToPlanes_MakePlanesComplete;
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        // Check to see if the spatial mapping data has been processed
        // and if we are limiting how much time the user can spend scanning.
        if (!meshesProcessed && limitScanningByTime)
        {
            // If we have not processed the spatial mapping data
            // and scanning time is limited...

            // Check to see if enough scanning time has passed
            // since starting the observer.
            if (limitScanningByTime && ((Time.time - SpatialMappingManager.Instance.StartTime) < scanTime))
            {
                // If we have a limited scanning time, then we should wait until
                // enough time has passed before processing the mesh.
            }
            else
            {
                // The user should be done scanning their environment,
                // so start processing the spatial mapping data...

                /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

                // 3.a: Check if IsObserverRunning() is true on the
                // SpatialMappingManager.Instance.
                if(SpatialMappingManager.Instance.IsObserverRunning())
                {
                    // 3.a: If running, Stop the observer by calling
                    // StopObserver() on the SpatialMappingManager.Instance.
                    SpatialMappingManager.Instance.StopObserver();
                }

                // 3.a: Call CreatePlanes() to generate planes.
                CreatePlanes();

                // 3.a: Set meshesProcessed to true.
                meshesProcessed = true;
            }
        }
    }

    /// <summary>
    /// Handler for the SurfaceMeshesToPlanes MakePlanesComplete event.
    /// </summary>
    /// <param name="source">Source of the event.</param>
    /// <param name="args">Args for the event.</param>
    private void SurfaceMeshesToPlanes_MakePlanesComplete(object source, System.EventArgs args)
    {
        /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

        // Collection of floor and table planes that we can use to set horizontal items on.
        List<GameObject> horizontal = new List<GameObject>();

        // Collection of wall planes that we can use to set vertical items on.
        List<GameObject> vertical = new List<GameObject>();

        // 3.a: Get all floor and table planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'horizontal' list.
        horizontal = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Table | PlaneTypes.Floor);

        // 3.a: Get all wall planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'vertical' list.
        vertical = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Wall);

        // Check to see if we have enough horizontal planes (minimumFloors)
        // and vertical planes (minimumWalls), to set holograms on in the world.
        if (horizontal.Count >= minimumFloors && vertical.Count >= minimumWalls)
        {
            // We have enough floors and walls to place our holograms on...

            // 3.a: Let's reduce our triangle count by removing triangles
            // from SpatialMapping meshes that intersect with our active planes.
            // Call RemoveVertices().
            // Pass in all activePlanes found by SurfaceMeshesToPlanes.Instance.
            RemoveVertices(SurfaceMeshesToPlanes.Instance.ActivePlanes);

            // 3.a: We can indicate to the user that scanning is over by
            // changing the material applied to the Spatial Mapping meshes.
            // Call SpatialMappingManager.Instance.SetSurfaceMaterial().
            // Pass in the secondaryMaterial.
            SpatialMappingManager.Instance.SetSurfaceMaterial(secondaryMaterial);

            // 3.a: We are all done processing the mesh, so we can now
            // initialize a collection of Placeable holograms in the world
            // and use horizontal/vertical planes to set their starting positions.
            // Call SpaceCollectionManager.Instance.GenerateItemsInWorld().
            // Pass in the lists of horizontal and vertical planes that we found earlier.
            SpaceCollectionManager.Instance.GenerateItemsInWorld(horizontal, vertical);
        }
        else
        {
            // We do not have enough floors/walls to place our holograms on...

            // 3.a: Re-enter scanning mode so the user can find more surfaces by
            // calling StartObserver() on the SpatialMappingManager.Instance.
            SpatialMappingManager.Instance.StartObserver();

            // 3.a: Re-process spatial data after scanning completes by
            // re-setting meshesProcessed to false.
            meshesProcessed = false;
        }
    }

    /// <summary>
    /// Creates planes from the spatial mapping surfaces.
    /// </summary>
    private void CreatePlanes()
    {
        // Generate planes based on the spatial map.
        SurfaceMeshesToPlanes surfaceToPlanes = SurfaceMeshesToPlanes.Instance;
        if (surfaceToPlanes != null && surfaceToPlanes.enabled)
        {
            surfaceToPlanes.MakePlanes();
        }
    }

    /// <summary>
    /// Removes triangles from the spatial mapping surfaces.
    /// </summary>
    /// <param name="boundingObjects"></param>
    private void RemoveVertices(IEnumerable<GameObject> boundingObjects)
    {
        RemoveSurfaceVertices removeVerts = RemoveSurfaceVertices.Instance;
        if (removeVerts != null && removeVerts.enabled)
        {
            removeVerts.RemoveSurfaceVerticesWithinBounds(boundingObjects);
        }
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        if (SurfaceMeshesToPlanes.Instance != null)
        {
            SurfaceMeshesToPlanes.Instance.MakePlanesComplete -= SurfaceMeshesToPlanes_MakePlanesComplete;
        }
    }
}
```

**Erstellen und Bereitstellen**

* Drücken Sie vor der Bereitstellung im HoloLens die Schaltfläche **Wiedergeben** in Unity, um in den Wiedergabemodus zu wechseln.
* Nachdem das Raumgitternetz aus der Datei geladen wurde, warten Sie 10 Sekunden, bevor die Verarbeitung im Gitternetz für räumliche Zuordnungen beginnt.
* Wenn die Verarbeitung abgeschlossen ist, scheinen Ebenen den Boden, die Wände, die Decken usw. darzustellen.
* Nachdem alle Ebenen gefunden wurden, sollte ein Solarsystem auf einem Boden in der Nähe der Kamera angezeigt werden.
* Zwei Poster sollten auch an Wänden in der Nähe der Kamera angezeigt werden. Wechseln Sie zur Registerkarte **Szene,** wenn sie im **Spielmodus** nicht angezeigt werden.
* Drücken Sie erneut die Schaltfläche **Wiedergeben,** um den Wiedergabemodus zu beenden.
* Erstellen Sie wie gewohnt die HoloLens, und stellen Sie sie bereit.
* Warten Sie, bis die Überprüfung und Verarbeitung der räumlichen Zuordnungsdaten abgeschlossen ist.
* Sobald Sie Ebenen sehen, versuchen Sie, das Sonnensystem und Poster in Ihrer Welt zu finden.

## <a name="chapter-4---placement"></a>Kapitel 4: Platzierung

>[!VIDEO https://www.youtube.com/embed/Srhtpid1uZc]

**Ziele**

* Bestimmen Sie, ob ein Hologramm auf eine Oberfläche passt.
* Geben Sie dem Benutzer Feedback, wenn ein Hologramm auf eine Oberfläche passen kann/kann.

**Anweisungen**

* Wählen Sie im **Hierarchiebereich** von Unity das **Objekt SpatialProcessing** aus.
* Suchen Sie im Bereich **Inspector (Inspektor)** nach der Komponente **Surface Meshes To Planes (Script) (Surface Meshes To Planes (Script)).**
* Ändern Sie die **Draw Planes-Eigenschaft** in **Nothing,** um die Auswahl zu löschen.
* Ändern Sie die Eigenschaft **Draw Planes** in **Wall**, sodass nur Die Wandebenen gerendert werden.
* Doppelklicken Sie im **bereich Project** Ordner **Scripts** auf **Placeable.cs,** um sie in Visual Studio zu öffnen.

Das **Placeable-Skript** ist bereits an die Poster und das Projektionsfeld angefügt, die nach Abschluss der Ebenensuche erstellt werden. Wir müssen lediglich die Auskommentierung von Code aufheben, und mit diesem Skript wird Folgendes erreicht:

1. Bestimmen Sie, ob ein Hologramm auf eine Oberfläche passt, indem Sie von der Mitte und vier Ecken des umgebenden Cubes raycasten.
2. Überprüfen Sie die Normaloberfläche, um festzustellen, ob sie so reibungslos ist, dass das Hologramm leer ist.
3. Rendert einen umgebenden Würfel um das Hologramm, um seine tatsächliche Größe anzuzeigen, während es platziert wird.
4. Werfen Sie einen Schatten unter/hinter das Hologramm, um zu zeigen, wo es auf dem Boden/der Wand platziert wird.
5. Rendern Sie den Schatten in Rot, wenn das Hologramm nicht auf der Oberfläche platziert werden kann, oder grün, sofern dies dere ist.
6. Richten Sie das Hologramm neu aus, um es an dem Oberflächentyp (vertikal oder horizontal) auszurichten, zu dem es Affinität hat.
7. Platzieren Sie das Hologramm reibungslos auf der ausgewählten Oberfläche, um Sprung- oder Ausrichtungsverhalten zu vermeiden.

Aufheben der Auskommentierung des gesamten Codes in der folgenden Codierungsübung, oder verwenden Sie diese abgeschlossene Projektmappe in **Placeable.cs:**

```cs
using System.Collections.Generic;
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Enumeration containing the surfaces on which a GameObject
/// can be placed.  For simplicity of this sample, only one
/// surface type is allowed to be selected.
/// </summary>
public enum PlacementSurfaces
{
    // Horizontal surface with an upward pointing normal.
    Horizontal = 1,

    // Vertical surface with a normal facing the user.
    Vertical = 2,
}

/// <summary>
/// The Placeable class implements the logic used to determine if a GameObject
/// can be placed on a target surface. Constraints for placement include:
/// * No part of the GameObject's box collider impacts with another object in the scene
/// * The object lays flat (within specified tolerances) against the surface
/// * The object would not fall off of the surface if gravity were enabled.
/// This class also provides the following visualizations.
/// * A transparent cube representing the object's box collider.
/// * Shadow on the target surface indicating whether or not placement is valid.
/// </summary>
public class Placeable : MonoBehaviour
{
    [Tooltip("The base material used to render the bounds asset when placement is allowed.")]
    public Material PlaceableBoundsMaterial = null;

    [Tooltip("The base material used to render the bounds asset when placement is not allowed.")]
    public Material NotPlaceableBoundsMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it allowed.")]
    public Material PlaceableShadowMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it not allowed.")]
    public Material NotPlaceableShadowMaterial = null;

    [Tooltip("The type of surface on which the object can be placed.")]
    public PlacementSurfaces PlacementSurface = PlacementSurfaces.Horizontal;

    [Tooltip("The child object(s) to hide during placement.")]
    public List<GameObject> ChildrenToHide = new List<GameObject>();

    /// <summary>
    /// Indicates if the object is in the process of being placed.
    /// </summary>
    public bool IsPlacing { get; private set; }

    // The most recent distance to the surface.  This is used to 
    // locate the object when the user's gaze does not intersect
    // with the Spatial Mapping mesh.
    private float lastDistance = 2.0f;

    // The distance away from the target surface that the object should hover prior while being placed.
    private float hoverDistance = 0.15f;

    // Threshold (the closer to 0, the stricter the standard) used to determine if a surface is flat.
    private float distanceThreshold = 0.02f;

    // Threshold (the closer to 1, the stricter the standard) used to determine if a surface is vertical.
    private float upNormalThreshold = 0.9f;

    // Maximum distance, from the object, that placement is allowed.
    // This is used when raycasting to see if the object is near a placeable surface.
    private float maximumPlacementDistance = 5.0f;

    // Speed (1.0 being fastest) at which the object settles to the surface upon placement.
    private float placementVelocity = 0.06f;

    // Indicates whether or not this script manages the object's box collider.
    private bool managingBoxCollider = false;

    // The box collider used to determine of the object will fit in the desired location.
    // It is also used to size the bounding cube.
    private BoxCollider boxCollider = null;

    // Visible asset used to show the dimensions of the object. This asset is sized
    // using the box collider's bounds.
    private GameObject boundsAsset = null;

    // Visible asset used to show the where the object is attempting to be placed.
    // This asset is sized using the box collider's bounds.
    private GameObject shadowAsset = null;

    // The location at which the object will be placed.
    private Vector3 targetPosition;

    /// <summary>
    /// Called when the GameObject is created.
    /// </summary>
    private void Awake()
    {
        targetPosition = gameObject.transform.position;

        // Get the object's collider.
        boxCollider = gameObject.GetComponent<BoxCollider>();
        if (boxCollider == null)
        {
            // The object does not have a collider, create one and remember that
            // we are managing it.
            managingBoxCollider = true;
            boxCollider = gameObject.AddComponent<BoxCollider>();
            boxCollider.enabled = false;
        }

        // Create the object that will be used to indicate the bounds of the GameObject.
        boundsAsset = GameObject.CreatePrimitive(PrimitiveType.Cube);
        boundsAsset.transform.parent = gameObject.transform;
        boundsAsset.SetActive(false);

        // Create a object that will be used as a shadow.
        shadowAsset = GameObject.CreatePrimitive(PrimitiveType.Quad);
        shadowAsset.transform.parent = gameObject.transform;
        shadowAsset.SetActive(false);
    }

    /// <summary>
    /// Called when our object is selected.  Generally called by
    /// a gesture management component.
    /// </summary>
    public void OnSelect()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (!IsPlacing)
        {
            OnPlacementStart();
        }
        else
        {
            OnPlacementStop();
        }
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (IsPlacing)
        {
            // Move the object.
            Move();

            // Set the visual elements.
            Vector3 targetPosition;
            Vector3 surfaceNormal;
            bool canBePlaced = ValidatePlacement(out targetPosition, out surfaceNormal);
            DisplayBounds(canBePlaced);
            DisplayShadow(targetPosition, surfaceNormal, canBePlaced);
        }
        else
        {
            // Disable the visual elements.
            boundsAsset.SetActive(false);
            shadowAsset.SetActive(false);

            // Gracefully place the object on the target surface.
            float dist = (gameObject.transform.position - targetPosition).magnitude;
            if (dist > 0)
            {
                gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, targetPosition, placementVelocity / dist);
            }
            else
            {
                // Unhide the child object(s) to make placement easier.
                for (int i = 0; i < ChildrenToHide.Count; i++)
                {
                    ChildrenToHide[i].SetActive(true);
                }
            }
        }
    }

    /// <summary>
    /// Verify whether or not the object can be placed.
    /// </summary>
    /// <param name="position">
    /// The target position on the surface.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the object is to be placed.
    /// </param>
    /// <returns>
    /// True if the target position is valid for placing the object, otherwise false.
    /// </returns>
    private bool ValidatePlacement(out Vector3 position, out Vector3 surfaceNormal)
    {
        Vector3 raycastDirection = gameObject.transform.forward;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            // Raycast from the bottom face of the box collider.
            raycastDirection = -(Vector3.up);
        }

        // Initialize out parameters.
        position = Vector3.zero;
        surfaceNormal = Vector3.zero;

        Vector3[] facePoints = GetColliderFacePoints();

        // The origin points we receive are in local space and we 
        // need to raycast in world space.
        for (int i = 0; i < facePoints.Length; i++)
        {
            facePoints[i] = gameObject.transform.TransformVector(facePoints[i]) + gameObject.transform.position;
        }

        // Cast a ray from the center of the box collider face to the surface.
        RaycastHit centerHit;
        if (!Physics.Raycast(facePoints[0],
                        raycastDirection,
                        out centerHit,
                        maximumPlacementDistance,
                        SpatialMappingManager.Instance.LayerMask))
        {
            // If the ray failed to hit the surface, we are done.
            return false;
        }

        // We have found a surface.  Set position and surfaceNormal.
        position = centerHit.point;
        surfaceNormal = centerHit.normal;

        // Cast a ray from the corners of the box collider face to the surface.
        for (int i = 1; i < facePoints.Length; i++)
        {
            RaycastHit hitInfo;
            if (Physics.Raycast(facePoints[i],
                                raycastDirection,
                                out hitInfo,
                                maximumPlacementDistance,
                                SpatialMappingManager.Instance.LayerMask))
            {
                // To be a valid placement location, each of the corners must have a similar
                // enough distance to the surface as the center point
                if (!IsEquivalentDistance(centerHit.distance, hitInfo.distance))
                {
                    return false;
                }
            }
            else
            {
                // The raycast failed to intersect with the target layer.
                return false;
            }
        }

        return true;
    }

    /// <summary>
    /// Determine the coordinates, in local space, of the box collider face that 
    /// will be placed against the target surface.
    /// </summary>
    /// <returns>
    /// Vector3 array with the center point of the face at index 0.
    /// </returns>
    private Vector3[] GetColliderFacePoints()
    {
        // Get the collider extents.  
        // The size values are twice the extents.
        Vector3 extents = boxCollider.size / 2;

        // Calculate the min and max values for each coordinate.
        float minX = boxCollider.center.x - extents.x;
        float maxX = boxCollider.center.x + extents.x;
        float minY = boxCollider.center.y - extents.y;
        float maxY = boxCollider.center.y + extents.y;
        float minZ = boxCollider.center.z - extents.z;
        float maxZ = boxCollider.center.z + extents.z;

        Vector3 center;
        Vector3 corner0;
        Vector3 corner1;
        Vector3 corner2;
        Vector3 corner3;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            center = new Vector3(boxCollider.center.x, minY, boxCollider.center.z);
            corner0 = new Vector3(minX, minY, minZ);
            corner1 = new Vector3(minX, minY, maxZ);
            corner2 = new Vector3(maxX, minY, minZ);
            corner3 = new Vector3(maxX, minY, maxZ);
        }
        else
        {
            // Placing on vertical surfaces.
            center = new Vector3(boxCollider.center.x, boxCollider.center.y, maxZ);
            corner0 = new Vector3(minX, minY, maxZ);
            corner1 = new Vector3(minX, maxY, maxZ);
            corner2 = new Vector3(maxX, minY, maxZ);
            corner3 = new Vector3(maxX, maxY, maxZ);
        }

        return new Vector3[] { center, corner0, corner1, corner2, corner3 };
    }

    /// <summary>
    /// Put the object into placement mode.
    /// </summary>
    public void OnPlacementStart()
    {
        // If we are managing the collider, enable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = true;
        }

        // Hide the child object(s) to make placement easier.
        for (int i = 0; i < ChildrenToHide.Count; i++)
        {
            ChildrenToHide[i].SetActive(false);
        }

        // Tell the gesture manager that it is to assume
        // all input is to be given to this object.
        GestureManager.Instance.OverrideFocusedObject = gameObject;

        // Enter placement mode.
        IsPlacing = true;
    }

    /// <summary>
    /// Take the object out of placement mode.
    /// </summary>
    /// <remarks>
    /// This method will leave the object in placement mode if called while
    /// the object is in an invalid location.  To determine whether or not
    /// the object has been placed, check the value of the IsPlacing property.
    /// </remarks>
    public void OnPlacementStop()
    {
        // ValidatePlacement requires a normal as an out parameter.
        Vector3 position;
        Vector3 surfaceNormal;

        // Check to see if we can exit placement mode.
        if (!ValidatePlacement(out position, out surfaceNormal))
        {
            return;
        }

        // The object is allowed to be placed.
        // We are placing at a small buffer away from the surface.
        targetPosition = position + (0.01f * surfaceNormal);

        OrientObject(true, surfaceNormal);

        // If we are managing the collider, disable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = false;
        }

        // Tell the gesture manager that it is to resume
        // its normal behavior.
        GestureManager.Instance.OverrideFocusedObject = null;

        // Exit placement mode.
        IsPlacing = false;
    }

    /// <summary>
    /// Positions the object along the surface toward which the user is gazing.
    /// </summary>
    /// <remarks>
    /// If the user's gaze does not intersect with a surface, the object
    /// will remain at the most recently calculated distance.
    /// </remarks>
    private void Move()
    {
        Vector3 moveTo = gameObject.transform.position;
        Vector3 surfaceNormal = Vector3.zero;
        RaycastHit hitInfo;

        bool hit = Physics.Raycast(Camera.main.transform.position,
                                Camera.main.transform.forward,
                                out hitInfo,
                                20f,
                                SpatialMappingManager.Instance.LayerMask);

        if (hit)
        {
            float offsetDistance = hoverDistance;

            // Place the object a small distance away from the surface while keeping 
            // the object from going behind the user.
            if (hitInfo.distance <= hoverDistance)
            {
                offsetDistance = 0f;
            }

            moveTo = hitInfo.point + (offsetDistance * hitInfo.normal);

            lastDistance = hitInfo.distance;
            surfaceNormal = hitInfo.normal;
        }
        else
        {
            // The raycast failed to hit a surface.  In this case, keep the object at the distance of the last
            // intersected surface.
            moveTo = Camera.main.transform.position + (Camera.main.transform.forward * lastDistance);
        }

        // Follow the user's gaze.
        float dist = Mathf.Abs((gameObject.transform.position - moveTo).magnitude);
        gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, moveTo, placementVelocity / dist);

        // Orient the object.
        // We are using the return value from Physics.Raycast to instruct
        // the OrientObject function to align to the vertical surface if appropriate.
        OrientObject(hit, surfaceNormal);
    }

    /// <summary>
    /// Orients the object so that it faces the user.
    /// </summary>
    /// <param name="alignToVerticalSurface">
    /// If true and the object is to be placed on a vertical surface, 
    /// orient parallel to the target surface.  If false, orient the object 
    /// to face the user.
    /// </param>
    /// <param name="surfaceNormal">
    /// The target surface's normal vector.
    /// </param>
    /// <remarks>
    /// The alignToVerticalSurface parameter is ignored if the object
    /// is to be placed on a horizontalSurface
    /// </remarks>
    private void OrientObject(bool alignToVerticalSurface, Vector3 surfaceNormal)
    {
        Quaternion rotation = Camera.main.transform.localRotation;

        // If the user's gaze does not intersect with the Spatial Mapping mesh,
        // orient the object towards the user.
        if (alignToVerticalSurface && (PlacementSurface == PlacementSurfaces.Vertical))
        {
            // We are placing on a vertical surface.
            // If the normal of the Spatial Mapping mesh indicates that the
            // surface is vertical, orient parallel to the surface.
            if (Mathf.Abs(surfaceNormal.y) <= (1 - upNormalThreshold))
            {
                rotation = Quaternion.LookRotation(-surfaceNormal, Vector3.up);
            }
        }
        else
        {
            rotation.x = 0f;
            rotation.z = 0f;
        }

        gameObject.transform.rotation = rotation;
    }

    /// <summary>
    /// Displays the bounds asset.
    /// </summary>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayBounds(bool canBePlaced)
    {
        // Ensure the bounds asset is sized and positioned correctly.
        boundsAsset.transform.localPosition = boxCollider.center;
        boundsAsset.transform.localScale = boxCollider.size;
        boundsAsset.transform.rotation = gameObject.transform.rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = PlaceableBoundsMaterial;
        }
        else
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableBoundsMaterial;
        }

        // Show the bounds asset.
        boundsAsset.SetActive(true);
    }

    /// <summary>
    /// Displays the placement shadow asset.
    /// </summary>
    /// <param name="position">
    /// The position at which to place the shadow asset.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the asset will be placed
    /// </param>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayShadow(Vector3 position,
                            Vector3 surfaceNormal,
                            bool canBePlaced)
    {
        // Rotate and scale the shadow so that it is displayed on the correct surface and matches the object.
        float rotationX = 0.0f;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            rotationX = 90.0f;
            shadowAsset.transform.localScale = new Vector3(boxCollider.size.x, boxCollider.size.z, 1);
        }
        else
        {
            shadowAsset.transform.localScale = boxCollider.size;
        }

        Quaternion rotation = Quaternion.Euler(rotationX, gameObject.transform.rotation.eulerAngles.y, 0);
        shadowAsset.transform.rotation = rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = PlaceableShadowMaterial;
        }
        else
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableShadowMaterial;
        }

        // Show the shadow asset as appropriate.
        if (position != Vector3.zero)
        {
            // Position the shadow a small distance from the target surface, along the normal.
            shadowAsset.transform.position = position + (0.01f * surfaceNormal);
            shadowAsset.SetActive(true);
        }
        else
        {
            shadowAsset.SetActive(false);
        }
    }

    /// <summary>
    /// Determines if two distance values should be considered equivalent. 
    /// </summary>
    /// <param name="d1">
    /// Distance to compare.
    /// </param>
    /// <param name="d2">
    /// Distance to compare.
    /// </param>
    /// <returns>
    /// True if the distances are within the desired tolerance, otherwise false.
    /// </returns>
    private bool IsEquivalentDistance(float d1, float d2)
    {
        float dist = Mathf.Abs(d1 - d2);
        return (dist <= distanceThreshold);
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        // Unload objects we have created.
        Destroy(boundsAsset);
        boundsAsset = null;
        Destroy(shadowAsset);
        shadowAsset = null;
    }
}
```

**Erstellen und Bereitstellen**

* Erstellen Sie wie zuvor das Projekt, und stellen Sie es im HoloLens bereit.
* Warten Sie, bis die Überprüfung und Verarbeitung der räumlichen Zuordnungsdaten abgeschlossen ist.
* Wenn Sie das Solarsystem sehen, sehen Sie sich das projektionsfeld unten an, und führen Sie eine Auswahlgeste aus, um es zu bewegen. Während das Projektionsfeld ausgewählt ist, wird ein umgebender Cube um das Projektionsfeld angezeigt.
* Bewegen Sie den Kopf, um an eine andere Stelle im Raum zu schauen. Das Projektionsfeld sollte Ihrem Anvieren folgen. Wenn der Schatten unter dem Projektionsfeld rot wird, können Sie das Hologramm nicht auf dieser Oberfläche platzieren. Wenn der Schatten unter dem Projektionsfeld grün wird, können Sie das Hologramm platzieren, indem Sie eine weitere Auswahlgeste ausführen.
* Suchen Sie eines der holografischen Poster an einer Wand, und wählen Sie es aus, um es an einen neuen Ort zu verschieben. Beachten Sie, dass Sie das Poster nicht auf dem Boden oder der Obergrenze platzieren können und dass es bei der Bewegung ordnungsgemäß an jeder Wand ausgerichtet bleibt.

## <a name="chapter-5---occlusion"></a>Kapitel 5: Verdeckung

>[!VIDEO https://www.youtube.com/embed/6Xrzh_w-7SE]

**Ziele**

* Bestimmen Sie, ob ein Hologramm vom Gitternetz für räumliche Zuordnungen verdeckt wird.
* Wenden Sie verschiedene Verdeckungstechniken an, um einen interessanten Effekt zu erzielen.

**Anweisungen**

Zunächst lassen wir zu, dass das Gitternetz für räumliche Zuordnungen andere Hologramme verdeckt, ohne die reale Welt zu verdecken:

* Wählen Sie im **Hierarchiebereich** das **Objekt SpatialProcessing** aus.
* Suchen Sie im **Inspektorbereich** nach der Komponente **Play Space Manager (Script).**
* Klicken Sie rechts neben der Eigenschaft **Sekundäres Material** auf den Kreis.
* Suchen Sie nach dem **Occlusion-Material,** wählen Sie es aus, und schließen Sie das Fenster.

Als Nächstes fügen wir der Erde ein besonderes Verhalten hinzu, sodass es immer dann ein blaues Highlight hat, wenn es durch ein anderes Hologramm (z. B. die Erde) oder durch das Gitternetz für räumliche Zuordnungen verdeckt wird:

* Erweitern **Sie** im bereich Project im Ordner **Hologramme** das **Objekt SolarSystem.**
* Klicken Sie auf **Earth**.
* Suchen Sie im **Inspektorbereich** nach dem Erdmaterial (untere Komponente).
* Ändern Sie in der **Dropdown-Dropdown-Shader-Datei** den Shader in **Custom > OcclusionRim**. Dadurch wird ein blaues Highlight um die Erde gerendert, wenn es von einem anderen Objekt verdeckt wird.

Schließlich ermöglichen wir einen Effekt für das X-Ray-Sehen für Planeten in unserem Sonnensystem. Wir müssen **PlanetOcclusion.cs** (im Ordner Scripts\SolarSystem) bearbeiten, um Folgendes zu erreichen:

1. Bestimmen Sie, ob ein Planet durch die SpatialMapping-Schicht (Raumgitternetze und Ebenen) verdeckt wird.
2. Zeigen Sie die Wireframedarstellung eines Planeten immer dann an, wenn er von der SpatialMapping-Ebene verdeckt wird.
3. Blendet die Wireframedarstellung eines Planeten aus, wenn diese nicht durch die SpatialMapping-Schicht blockiert wird.

Führen Sie die Codierungsübung in PlanetOcclusion.cs aus, oder verwenden Sie die folgende Lösung:

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Determines when the occluded version of the planet should be visible.
/// This script allows us to do selective occlusion, so the occlusionObject
/// will only be rendered when a Spatial Mapping surface is occluding the planet,
/// not when another hologram is responsible for the occlusion.
/// </summary>
public class PlanetOcclusion : MonoBehaviour
{
    [Tooltip("Object to display when the planet is occluded.")]
    public GameObject occlusionObject;

    /// <summary>
    /// Points to raycast to when checking for occlusion.
    /// </summary>
    private Vector3[] checkPoints;

    // Use this for initialization
    void Start()
    {
        occlusionObject.SetActive(false);

        // Set the check points to use when testing for occlusion.
        MeshFilter filter = gameObject.GetComponent<MeshFilter>();
        Vector3 extents = filter.mesh.bounds.extents;
        Vector3 center = filter.mesh.bounds.center;
        Vector3 top = new Vector3(center.x, center.y + extents.y, center.z);
        Vector3 left = new Vector3(center.x - extents.x, center.y, center.z);
        Vector3 right = new Vector3(center.x + extents.x, center.y, center.z);
        Vector3 bottom = new Vector3(center.x, center.y - extents.y, center.z);

        checkPoints = new Vector3[] { center, top, left, right, bottom };
    }

    // Update is called once per frame
    void Update()
    {
        /* TODO: 5.a DEVELOPER CODING EXERCISE 5.a */

        // Check to see if any of the planet's boundary points are occluded.
        for (int i = 0; i < checkPoints.Length; i++)
        {
            // 5.a: Convert the current checkPoint to world coordinates.
            // Call gameObject.transform.TransformPoint(checkPoints[i]).
            // Assign the result to a new Vector3 variable called 'checkPt'.
            Vector3 checkPt = gameObject.transform.TransformPoint(checkPoints[i]);

            // 5.a: Call Vector3.Distance() to calculate the distance
            // between the Main Camera's position and 'checkPt'.
            // Assign the result to a new float variable called 'distance'.
            float distance = Vector3.Distance(Camera.main.transform.position, checkPt);

            // 5.a: Take 'checkPt' and subtract the Main Camera's position from it.
            // Assign the result to a new Vector3 variable called 'direction'.
            Vector3 direction = checkPt - Camera.main.transform.position;

            // Used to indicate if the call to Physics.Raycast() was successful.
            bool raycastHit = false;

            // 5.a: Check if the planet is occluded by a spatial mapping surface.
            // Call Physics.Raycast() with the following arguments:
            // - Pass in the Main Camera's position as the origin.
            // - Pass in 'direction' for the direction.
            // - Pass in 'distance' for the maxDistance.
            // - Pass in SpatialMappingManager.Instance.LayerMask as layerMask.
            // Assign the result to 'raycastHit'.
            raycastHit = Physics.Raycast(Camera.main.transform.position, direction, distance, SpatialMappingManager.Instance.LayerMask);

            if (raycastHit)
            {
                // 5.a: Our raycast hit a surface, so the planet is occluded.
                // Set the occlusionObject to active.
                occlusionObject.SetActive(true);

                // At least one point is occluded, so break from the loop.
                break;
            }
            else
            {
                // 5.a: The Raycast did not hit, so the planet is not occluded.
                // Deactivate the occlusionObject.
                occlusionObject.SetActive(false);
            }
        }
    }
}
```

**Erstellen und Bereitstellen**

* Erstellen Sie die Anwendung wie gewohnt in HoloLens, und stellen Sie sie bereit.
* Warten Sie, bis die Überprüfung und Verarbeitung der räumlichen Zuordnungsdaten abgeschlossen ist (es sollten blaue Linien an den Wänden angezeigt werden).
* Suchen Sie nach dem Projektionsfeld des Solarsystems, wählen Sie es aus, und legen Sie es dann neben einer Wand oder hinter einem Zähler fest.
* Sie können die grundlegende Verdeckung anzeigen, indem Sie hinter Oberflächen ausblenden, um ein Peering auf dem Poster oder projektionsfeld zu erstellen.
* Suchen Sie nach der Erde. Es sollte immer dann einen blauen Hervorhebungseffekt geben, wenn sie hinter einem anderen Hologramm oder einer anderen Oberfläche liegt.
* Beobachten Sie, wie sich die Planeten hinter der Wand oder anderen Oberflächen im Raum bewegen. Sie verfügen jetzt über das X-Ray-Sehen und können ihre Wireframe-Skelette sehen!

## <a name="the-end"></a>Das Ende

Herzlichen Glückwunsch! Sie haben mr **spatial 230: Spatial mapping (MR Spatial 230: Räumliche Zuordnung)** abgeschlossen.

* Sie wissen, wie Sie Ihre Umgebung überprüfen und räumliche Zuordnungsdaten in Unity laden.
* Sie kennen die Grundlagen von Shadern und wissen, wie Materialien verwendet werden können, um die Welt erneut zu visualisieren.
* Sie haben neue Verarbeitungstechniken zum Suchen von Ebenen und Entfernen von Dreiecken aus einem Gitternetz kennengelernt.
* Sie konnten Hologramme auf sinnvollen Oberflächen verschieben und platzieren.
* Sie haben verschiedene Verdeckungstechniken kennen gelernt und die Leistungsfähigkeit des X-Ray-Sehens genutzt!