---
title: Implementieren von 3D-App-Startprogrammen (UWP-Apps)
description: Erfahren Sie, wie Sie 3D-App-Launcher und-Logos für Windows Mixed Reality UWP-apps und-Spiele (verteilt durch die Microsoft Store) auf hololens-und immersive-Headsets (VR) erstellen können.
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, Logo, Symbol, Modellierung, Start Programm, 3D-Start Programm, Kachel, Live Cube, Deep-Link, secondarytile, Sekundär Kachel, UWP, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, XML, Begrenzungsfeld, Unity
ms.openlocfilehash: 38f0932f20e3660c91b87de7bcb9d66799d9a51a
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757495"
---
# <a name="implement-3d-app-launchers-uwp-apps"></a><span data-ttu-id="686b4-104">Implementieren von 3D-App-Startprogrammen (UWP-Apps)</span><span class="sxs-lookup"><span data-stu-id="686b4-104">Implement 3D app launchers (UWP apps)</span></span>

> [!NOTE]
> <span data-ttu-id="686b4-105">Diese Funktion wurde als Teil des 2017 Fall Creators Updates (RS3) für immersive Headsets hinzugefügt und wird von hololens mit dem Windows 10-Update vom April 2018 unterstützt.</span><span class="sxs-lookup"><span data-stu-id="686b4-105">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive headsets and is supported by HoloLens with the  Windows 10 April 2018 Update.</span></span> <span data-ttu-id="686b4-106">Stellen Sie sicher, dass Ihre Anwendung auf eine Version des Windows SDK ist, die größer als oder gleich 10.0.16299 auf immersiven Headsets und 10.0.17125 auf hololens ist.</span><span class="sxs-lookup"><span data-stu-id="686b4-106">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive Headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="686b4-107">Die neuesten Windows SDK finden Sie [hier](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span><span class="sxs-lookup"><span data-stu-id="686b4-107">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

<span data-ttu-id="686b4-108">Der [Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md) -Startpunkt ist der Ausgangspunkt, an dem Benutzer vor dem Starten von Anwendungen landen.</span><span class="sxs-lookup"><span data-stu-id="686b4-108">The [Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="686b4-109">Beim Erstellen einer UWP-Anwendung für Windows Mixed Reality werden apps standardmäßig als 2D-Slate mit dem Logo Ihrer APP gestartet.</span><span class="sxs-lookup"><span data-stu-id="686b4-109">When creating a UWP application for Windows Mixed Reality, by default, apps are launched as 2D slates with their app's logo.</span></span> <span data-ttu-id="686b4-110">Beim Entwickeln von Umgebungen für Windows Mixed Reality kann optional ein 3D-Start Programm definiert werden, um das standardmäßige 2D-Start Programm für Ihre Anwendung zu überschreiben.</span><span class="sxs-lookup"><span data-stu-id="686b4-110">When developing experiences for Windows Mixed Reality, a 3D launcher can optionally be defined to override the default 2D launcher for your application.</span></span> <span data-ttu-id="686b4-111">Im Allgemeinen werden 3D-Launcher zum Starten von immersiven Anwendungen empfohlen, die Benutzer aus der Windows Mixed Reality-Startseite machen.</span><span class="sxs-lookup"><span data-stu-id="686b4-111">In general, 3D launchers are recommended for launching immersive applications that take users out of the Windows Mixed Reality home.</span></span> <span data-ttu-id="686b4-112">Das standardmäßige 2D-Start Programm wird bevorzugt, wenn die APP direkt aktiviert wird.</span><span class="sxs-lookup"><span data-stu-id="686b4-112">The default 2D launcher is preferred when the app is activated in place.</span></span> <span data-ttu-id="686b4-113">Sie können auch einen [3D-Deep-Link (secondarytile)](#3d-deep-links-secondarytiles) als 3D-Start Programm für Inhalte innerhalb einer 2D-UWP-app erstellen.</span><span class="sxs-lookup"><span data-stu-id="686b4-113">You can also create a [3D deep link (secondaryTile)](#3d-deep-links-secondarytiles) as a 3D launcher to content within a 2D UWP app.</span></span>

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="686b4-114">Erstellung eines 3D-App-Start Programms</span><span class="sxs-lookup"><span data-stu-id="686b4-114">3D app launcher creation process</span></span>

<span data-ttu-id="686b4-115">Zum Erstellen eines 3D-App-Start Programms sind drei Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="686b4-115">There are three steps to creating a 3D app launcher:</span></span>
1. [<span data-ttu-id="686b4-116">Entwurf und Konzept</span><span class="sxs-lookup"><span data-stu-id="686b4-116">Designing and concepting</span></span>](3d-app-launcher-design-guidance.md)
2. [<span data-ttu-id="686b4-117">Modellieren und exportieren</span><span class="sxs-lookup"><span data-stu-id="686b4-117">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="686b4-118">Integration in Ihre Anwendung (dieser Artikel)</span><span class="sxs-lookup"><span data-stu-id="686b4-118">Integrating it into your application (this article)</span></span>

<span data-ttu-id="686b4-119">3D-Ressourcen, die als Launcher für Ihre Anwendung verwendet werden sollen, sollten mithilfe der [Windows Mixed Reality Authoring Guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) erstellt werden, um die Kompatibilität zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="686b4-119">3D assets to be used as launchers for your application should be authored using the [Windows Mixed Reality authoring guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) to ensure compatibility.</span></span> <span data-ttu-id="686b4-120">Assets, die diese Erstellungs Spezifikation nicht erfüllen, werden nicht in der Windows Mixed Reality-Startseite gerendert.</span><span class="sxs-lookup"><span data-stu-id="686b4-120">Assets that fail to meet this authoring specification won't be rendered in the Windows Mixed Reality home.</span></span>

## <a name="configuring-the-3d-launcher"></a><span data-ttu-id="686b4-121">Konfigurieren des 3D-Start Programms</span><span class="sxs-lookup"><span data-stu-id="686b4-121">Configuring the 3D launcher</span></span>

<span data-ttu-id="686b4-122">Wenn Sie ein neues Projekt in Visual Studio erstellen, wird eine einfache Standardkachel erstellt, die den Namen und das Logo Ihrer App anzeigt.</span><span class="sxs-lookup"><span data-stu-id="686b4-122">When you create a new project in Visual Studio, it creates a simple default tile that displays your app's name and logo.</span></span> <span data-ttu-id="686b4-123">Um diese 2D-Darstellung durch ein benutzerdefiniertes 3D-Modell zu ersetzen, bearbeiten Sie das App-Manifest der Anwendung so, dass das "mixedrealitymodel"-Element als Teil Ihrer Standard Kachel Definition enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="686b4-123">To replace this 2D representation with a custom 3D model edit the app manifest of your application to include the “MixedRealityModel” element as part of your default tile definition.</span></span> <span data-ttu-id="686b4-124">Um zum 2D-Start Programm zurückzukehren, entfernen Sie einfach die mixedrealitymodel-Definition aus dem Manifest.</span><span class="sxs-lookup"><span data-stu-id="686b4-124">To revert to the 2D launcher just remove the MixedRealityModel definition from the manifest.</span></span>

### <a name="xml"></a><span data-ttu-id="686b4-125">XML</span><span class="sxs-lookup"><span data-stu-id="686b4-125">XML</span></span>

<span data-ttu-id="686b4-126">Suchen Sie zuerst das App-Paket Manifest in Ihrem aktuellen Projekt.</span><span class="sxs-lookup"><span data-stu-id="686b4-126">First, locate the app package manifest in your current project.</span></span> <span data-ttu-id="686b4-127">Standardmäßig wird das Manifest "Package. appxmanifest" genannt.</span><span class="sxs-lookup"><span data-stu-id="686b4-127">By default, the manifest will be named Package.appxmanifest.</span></span> <span data-ttu-id="686b4-128">Wenn Sie Visual Studio verwenden, klicken Sie mit der rechten Maustaste auf das Manifest in Ihrem projektmappenviewer, und wählen Sie **Quelle anzeigen** , um den XML-Code zum Bearbeiten zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="686b4-128">If you're using Visual Studio, then right-click the manifest in your solution viewer and select **View source** to open the xml for editing.</span></span> 

<span data-ttu-id="686b4-129">Fügen Sie am Anfang des Manifests das uap5-Schema hinzu, und fügen Sie es als Ignorable-Namespace ein:</span><span class="sxs-lookup"><span data-stu-id="686b4-129">At the top of the manifest, add the uap5 schema and include it as an ignorable namespace:</span></span>

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

<span data-ttu-id="686b4-130">Geben Sie als nächstes "mixedrealitymodel" in der Standard Kachel für Ihre Anwendung an:</span><span class="sxs-lookup"><span data-stu-id="686b4-130">Next specify the "MixedRealityModel" in the default tile for your application:</span></span>

```xml
<Applications>
    <Application Id="App"
      Executable="$targetnametoken$.exe"
      EntryPoint="ExampleApp.App">
      <uap:VisualElements
        DisplayName="ExampleApp"
        Square150x150Logo="Assets\Logo.png"
        Square44x44Logo="Assets\SmallLogo.png"
        Description="ExampleApp"
        BackgroundColor="#464646">
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb" />
        </uap:DefaultTile>
        <uap:SplashScreen Image="Assets\SplashScreen.png" />
      </uap:VisualElements>
    </Application>
</Applications>
```

<span data-ttu-id="686b4-131">Das mixedrealitymodel-Element akzeptiert einen Dateipfad, der auf ein 3D-Asset verweist, das in Ihrem App-Paket gespeichert ist.</span><span class="sxs-lookup"><span data-stu-id="686b4-131">The MixedRealityModel element accepts a file path pointing to a 3D asset stored in your app package.</span></span> <span data-ttu-id="686b4-132">Zurzeit werden nur 3D-Modelle unter Verwendung des. GLB-Datei Formats bereitgestellt, die für die [Windows Mixed Reality 3D Asset Authoring-Anweisungen](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) erstellt wurden.</span><span class="sxs-lookup"><span data-stu-id="686b4-132">Currently only 3D models delivered using the .glb file format and authored against the [Windows Mixed Reality 3D asset authoring instructions](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) are supported.</span></span> <span data-ttu-id="686b4-133">Assets müssen im App-Paket gespeichert werden, und die Animation wird derzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="686b4-133">Assets must be stored in the app package and animation isn't currently supported.</span></span> <span data-ttu-id="686b4-134">Wenn der Parameter "Path" leer gelassen wird, zeigt Windows das 2D-Slate anstelle des 3D-Start Programms an.</span><span class="sxs-lookup"><span data-stu-id="686b4-134">If the “Path” parameter is left blank Windows will show the 2D slate instead of the 3D launcher.</span></span> <span data-ttu-id="686b4-135">**Hinweis:** das. GLB-Asset muss in ihren Buildeinstellungen als "Inhalt" gekennzeichnet werden, bevor Sie Ihre APP erstellen und ausführen.</span><span class="sxs-lookup"><span data-stu-id="686b4-135">**Note:** the .glb asset must be marked as "Content" in your build settings before building and running your app.</span></span>


<span data-ttu-id="686b4-136">![Wählen Sie im Projektmappen-Explorer die GLB-Datei aus, und markieren Sie Sie mithilfe des Abschnitts Eigenschaften als "Inhalt" in den Buildeinstellungen.](images/buildsetting-content-300px.png)</span><span class="sxs-lookup"><span data-stu-id="686b4-136">![Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings](images/buildsetting-content-300px.png)</span></span><br>
<span data-ttu-id="686b4-137">*Wählen Sie im Projektmappen-Explorer die GLB-Datei aus, und markieren Sie Sie mithilfe des Abschnitts Eigenschaften als "Inhalt" in den Buildeinstellungen.*</span><span class="sxs-lookup"><span data-stu-id="686b4-137">*Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings*</span></span>

### <a name="bounding-box"></a><span data-ttu-id="686b4-138">Begrenzungsrahmen</span><span class="sxs-lookup"><span data-stu-id="686b4-138">Bounding box</span></span>

<span data-ttu-id="686b4-139">Ein Begrenzungs Rahmen kann verwendet werden, um optional einen zusätzlichen Pufferbereich um das Objekt hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="686b4-139">A bounding box can be used to optionally add an extra buffer region around the object.</span></span> <span data-ttu-id="686b4-140">Das umgebende Feld wird mithilfe eines Mittelpunkts und von Blöcken angegeben, die den Abstand zwischen der Mitte des umgebenden Felds und seinen Rändern entlang der Achse angeben.</span><span class="sxs-lookup"><span data-stu-id="686b4-140">The bounding box is specified using a center point and extents, which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="686b4-141">Die Einheiten für das Begrenzungsfeld können 1 Einheit = 1 Meter zugeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="686b4-141">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="686b4-142">Wenn kein Begrenzungsfeld angegeben wird, wird eine automatisch an das Mesh des Objekts angepasst.</span><span class="sxs-lookup"><span data-stu-id="686b4-142">If a bounding box isn't provided, then one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="686b4-143">Wenn das angegebene Begrenzungsfeld kleiner als das Modell ist, wird es in die Größe geändert, damit es an das Mesh angepasst ist.</span><span class="sxs-lookup"><span data-stu-id="686b4-143">If the provided bounding box is smaller than the model, then it will be resized to fit the mesh.</span></span>

<span data-ttu-id="686b4-144">Die Unterstützung für das Begrenzungsfeld Attribut wird mit dem Windows-Update-Update als Eigenschaft für das mixedrealitymodel-Element erreicht.</span><span class="sxs-lookup"><span data-stu-id="686b4-144">Support for the bounding box attribute will come with the Windows RS4 update as a property on the MixedRealityModel element.</span></span> <span data-ttu-id="686b4-145">Fügen Sie zum Definieren eines Begrenzungs Rahmens zuerst am oberen Rand des App-Manifests das uap6-Schema hinzu, und fügen Sie es als Ignorable Namespaces ein:</span><span class="sxs-lookup"><span data-stu-id="686b4-145">To define a bounding box first at the top of the app manifest add the uap6 schema and include it as ignorable namespaces:</span></span>

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
<span data-ttu-id="686b4-146">Legen Sie als nächstes auf dem mixedrealitymodel die spatialboundingbox-Eigenschaft auf das Begrenzungsfeld fest:</span><span class="sxs-lookup"><span data-stu-id="686b4-146">Next, on the MixedRealityModel set the SpatialBoundingBox property to define the bounding box:</span></span> 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a><span data-ttu-id="686b4-147">Verwendung von Unity</span><span class="sxs-lookup"><span data-stu-id="686b4-147">Using Unity</span></span>

<span data-ttu-id="686b4-148">Beim Arbeiten mit Unity muss das Projekt in Visual Studio erstellt und geöffnet werden, bevor das App-Manifest bearbeitet werden kann.</span><span class="sxs-lookup"><span data-stu-id="686b4-148">When working with Unity the project must be built and opened in Visual Studio before the App Manifest can be edited.</span></span> 

>[!NOTE]
><span data-ttu-id="686b4-149">Das 3D-Start Programm muss im Manifest neu definiert werden, wenn eine neue Visual Studio-Projekt Mappe aus Unity aufgebaut und bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="686b4-149">The 3D launcher must be redefined in the manifest when building and deploying a new Visual Studio solution from Unity.</span></span>

## <a name="3d-deep-links-secondarytiles"></a><span data-ttu-id="686b4-150">3D Deep-Links (secondarytiles)</span><span class="sxs-lookup"><span data-stu-id="686b4-150">3D deep links (secondaryTiles)</span></span>

> [!NOTE]
> <span data-ttu-id="686b4-151">Diese Funktion wurde als Teil des 2017 Fall Creators Update (RS3) für immersive (VR)-Headsets und im Rahmen des Updates vom April 2018 (RS4) für hololens hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="686b4-151">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive (VR) headsets and as part of the April 2018 Update (RS4) for HoloLens.</span></span> <span data-ttu-id="686b4-152">Stellen Sie sicher, dass Ihre Anwendung auf eine Version des Windows SDK ist, das größer als oder gleich 10.0.16299 on immersive (VR)-Headsets und 10.0.17125 auf hololens ist.</span><span class="sxs-lookup"><span data-stu-id="686b4-152">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive (VR) headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="686b4-153">Die neuesten Windows SDK finden Sie [hier](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span><span class="sxs-lookup"><span data-stu-id="686b4-153">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

>[!IMPORTANT]
><span data-ttu-id="686b4-154">3D-Deep-Links (secondarytiles) funktionieren nur mit 2D-UWP-apps.</span><span class="sxs-lookup"><span data-stu-id="686b4-154">3D deep links (secondaryTiles) only work with 2D UWP apps.</span></span> <span data-ttu-id="686b4-155">Sie können jedoch ein [3D-App-](implementing-3d-app-launchers.md) Startfeld erstellen, um eine exklusive App aus dem Windows Mixed Reality-Start Programm zu starten.</span><span class="sxs-lookup"><span data-stu-id="686b4-155">You can, however, create a [3D app launcher](implementing-3d-app-launchers.md) to launch an exclusive app from the Windows Mixed Reality home.</span></span>

<span data-ttu-id="686b4-156">Ihre 2D-Anwendungen können für die gemischte Realität von Windows erweitert werden, indem Sie die Möglichkeit zum Platzieren von 3D-Modellen aus Ihrer [App als tiefe](../discover/navigating-the-windows-mixed-reality-home.md) Links zu Inhalten in ihrer 2D-app hinzufügen, wie z. b. zwei [sekundäre Kacheln](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) im Windows-Startmenü.</span><span class="sxs-lookup"><span data-stu-id="686b4-156">Your 2D applications can be enhanced for Windows Mixed Reality by adding the ability to place 3D models from your app into the [Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md) as deep links to content within your 2D app, just like [2D secondary tiles](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) on the Windows Start menu.</span></span> <span data-ttu-id="686b4-157">Sie können z. b. 360 °-photosphären erstellen, die direkt in eine 360 °-Foto-Viewer-App verweisen, oder Benutzern das Platzieren von 3D-Inhalten aus einer Sammlung von Objekten ermöglichen, die eine Detailseite zum Autor öffnet.</span><span class="sxs-lookup"><span data-stu-id="686b4-157">For example, you can create 360° photospheres that link directly into a 360° photo viewer app, or let users place 3D content from a collection of assets that opens a details page about the author.</span></span> <span data-ttu-id="686b4-158">Dies sind nur einige Möglichkeiten, die Funktionalität Ihrer 2D-Anwendung mit 3D-Inhalten zu erweitern.</span><span class="sxs-lookup"><span data-stu-id="686b4-158">These are just a couple ways to expand the functionality of your 2D application with 3D content.</span></span>

### <a name="creating-a-3d-secondarytile"></a><span data-ttu-id="686b4-159">Erstellen einer 3D-"secondarytile"</span><span class="sxs-lookup"><span data-stu-id="686b4-159">Creating a 3D “secondaryTile”</span></span>

<span data-ttu-id="686b4-160">Sie können 3D-Inhalte mithilfe von "secondarytiles" aus der Anwendung platzieren, indem Sie zum Zeitpunkt der Erstellung ein gemischtes Reality-Modell definieren.</span><span class="sxs-lookup"><span data-stu-id="686b4-160">You can place 3D content from your application using “secondaryTiles” by defining a mixed reality model at creation time.</span></span> <span data-ttu-id="686b4-161">Gemischte Reality-Modelle werden erstellt, indem auf ein 3D-Medienobjekt in Ihrem App-Paket verwiesen und optional ein Begrenzungsfeld definiert wird.</span><span class="sxs-lookup"><span data-stu-id="686b4-161">Mixed reality models are created by referencing a 3D asset in your app package and optionally defining a bounding box.</span></span> 

> [!NOTE]
> <span data-ttu-id="686b4-162">Das Erstellen von "secondarytiles" aus einer exklusiven Ansicht wird derzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="686b4-162">Creating “secondaryTiles” from within an exclusive view is not currently supported.</span></span>

```cs
using Windows.UI.StartScreen;
using Windows.Foundation.Numerics;
using Windows.Perception.Spatial;

// Initialize the tile
SecondaryTile tile = new SecondaryTile("myTileId")
{
    DisplayName = "My Tile",
    Arguments = "myArgs"
};

tile.VisualElements.Square150x150Logo = new Uri("ms-appx:///Assets/MyTile/Square150x150Logo.png");

//Assign 3D model (only ms-appx and ms-appdata are allowed)
TileMixedRealityModel model = tile.VisualElements.MixedRealityModel;
model.Uri = new Uri("ms-appx:///Assets/MyTile/MixedRealityModel.glb");
model.ActivationBehavior = TileMixedRealityModelActivationBehavior.Default;
model.BoundingBox = new SpatialBoundingBox
{
    Center = new Vector3 { X = 1, Y = 0, Z = 0 },
    Extents = new Vector3 { X = 3, Y = 5, Z = 4 }
};

// And place it
await tile.RequestCreateAsync();
```

### <a name="bounding-box"></a><span data-ttu-id="686b4-163">Begrenzungsrahmen</span><span class="sxs-lookup"><span data-stu-id="686b4-163">Bounding box</span></span>

<span data-ttu-id="686b4-164">Zum Hinzufügen eines zusätzlichen Puffer Bereichs um das Objekt kann ein Begrenzungs Rahmen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="686b4-164">A bounding box can be used to add an extra buffer region around the object.</span></span> <span data-ttu-id="686b4-165">Das umgebende Feld wird mithilfe eines Mittelpunkts und von Blöcken angegeben, die den Abstand zwischen der Mitte des umgebenden Felds und seinen Rändern entlang der Achse angeben.</span><span class="sxs-lookup"><span data-stu-id="686b4-165">The bounding box is specified using a center point and extents, which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="686b4-166">Die Einheiten für das Begrenzungsfeld können 1 Einheit = 1 Meter zugeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="686b4-166">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="686b4-167">Wenn kein Begrenzungsfeld angegeben wird, wird eines automatisch an das Mesh des Objekts angepasst.</span><span class="sxs-lookup"><span data-stu-id="686b4-167">If a bounding box isn't provided, one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="686b4-168">Wenn das angegebene Begrenzungsfeld kleiner als das Modell ist, wird die Größe angepasst, damit es an das Mesh angepasst wird.</span><span class="sxs-lookup"><span data-stu-id="686b4-168">If the provided bounding box is smaller than the model, it will be resized to fit the mesh.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="686b4-169">Aktivierungs Verhalten</span><span class="sxs-lookup"><span data-stu-id="686b4-169">Activation behavior</span></span>

> [!NOTE]
> <span data-ttu-id="686b4-170">Diese Funktion wird ab dem Windows-Update "RS4" unterstützt.</span><span class="sxs-lookup"><span data-stu-id="686b4-170">This feature will be supported as of the Windows RS4 update.</span></span> <span data-ttu-id="686b4-171">Stellen Sie sicher, dass Ihre Anwendung auf eine Version der Windows SDK, die größer als oder gleich 10.0.17125 ist, wenn Sie beabsichtigen, dieses Feature zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="686b4-171">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.17125 if you plan to use this feature</span></span>

<span data-ttu-id="686b4-172">Sie können das Aktivierungs Verhalten für eine 3D-secondarytile definieren, um zu steuern, wie Sie reagiert, wenn ein Benutzer Sie auswählt.</span><span class="sxs-lookup"><span data-stu-id="686b4-172">You can define the activation behavior for a 3D secondaryTile to control how it reacts when a user selects it.</span></span> <span data-ttu-id="686b4-173">Dies kann verwendet werden, um 3D-Objekte in die gemischte Realität zu platzieren, die rein informativ oder dekorativ sind.</span><span class="sxs-lookup"><span data-stu-id="686b4-173">This can be used to place 3D objects in the Mixed Reality home that are purely informative or decorative.</span></span> <span data-ttu-id="686b4-174">Die folgenden Aktivierungs Verhaltenstypen werden unterstützt:</span><span class="sxs-lookup"><span data-stu-id="686b4-174">The following activation behavior types are supported:</span></span>
1. <span data-ttu-id="686b4-175">Standard: Wenn ein Benutzer die 3D-secondarytile auswählt, wird die App aktiviert.</span><span class="sxs-lookup"><span data-stu-id="686b4-175">Default: When a user selects the 3D secondaryTile the app is activated</span></span>
2. <span data-ttu-id="686b4-176">Keine: Wenn der Benutzer die 3D-secondarytile auswählt, geschieht nichts, und die APP ist nicht aktiviert.</span><span class="sxs-lookup"><span data-stu-id="686b4-176">None: When the user selects the 3D secondaryTile nothing happens and the app isn't activated.</span></span>

### <a name="obtaining-and-updating-an-existing-secondarytile"></a><span data-ttu-id="686b4-177">Abrufen und Aktualisieren einer vorhandenen "secondarytile"</span><span class="sxs-lookup"><span data-stu-id="686b4-177">Obtaining and updating an existing “secondaryTile”</span></span>

<span data-ttu-id="686b4-178">Entwickler können eine Liste Ihrer vorhandenen sekundären Kacheln zurückerhalten, einschließlich der Eigenschaften, die Sie zuvor angegeben haben.</span><span class="sxs-lookup"><span data-stu-id="686b4-178">Developers can get back a list of their existing secondary tiles, which includes the properties that they previously specified.</span></span> <span data-ttu-id="686b4-179">Sie können die Eigenschaften auch aktualisieren, indem Sie den Wert ändern und dann UpdateAsync () aufrufen.</span><span class="sxs-lookup"><span data-stu-id="686b4-179">They can also update the properties by changing the value and then calling UpdateAsync().</span></span>

```cs
// Grab the existing secondary tile
SecondaryTile tile = (await SecondaryTile.FindAllAsync()).First();

Uri updatedUri = new Uri("ms-appdata:///local/MixedRealityUpdated.glb");

// See if the model needs updating
if (!tile.VisualElements.MixedRealityModel.Uri.Equals(updatedUri))
{
    // Update it
    tile.VisualElements.MixedRealityModel.Uri = updatedUri;

    // And apply the changes
    await tile.UpdateAsync();
}
```

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a><span data-ttu-id="686b4-180">Überprüfen, ob der Benutzer in der gemischten Realität von Windows ist</span><span class="sxs-lookup"><span data-stu-id="686b4-180">Checking that the user is in Windows Mixed Reality</span></span>

<span data-ttu-id="686b4-181">3D Deep-Links (secondarytiles) können nur erstellt werden, während die Ansicht in einem Windows Mixed Reality-Headset angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="686b4-181">3D deep links (secondaryTiles) can only be created while the view is being displayed in a Windows Mixed Reality headset.</span></span> <span data-ttu-id="686b4-182">Wenn Ihre Ansicht nicht in einem Windows Mixed Reality-Headset angezeigt wird, empfiehlt es sich, dies zu behandeln, indem Sie entweder den Einstiegspunkt ausblenden oder eine Fehlermeldung anzeigen.</span><span class="sxs-lookup"><span data-stu-id="686b4-182">When your view isn't being presented in a Windows Mixed Reality headset, we recommend gracefully handling this by either hiding the entry point or showing an error message.</span></span> <span data-ttu-id="686b4-183">Sie können dies überprüfen, indem Sie [iscurrentviewpresentedonholographic ()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_)Abfragen.</span><span class="sxs-lookup"><span data-stu-id="686b4-183">You can check this by querying [IsCurrentViewPresentedOnHolographic()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).</span></span>

## <a name="tile-notifications"></a><span data-ttu-id="686b4-184">Kachel Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="686b4-184">Tile notifications</span></span>

<span data-ttu-id="686b4-185">Bei Kachel Benachrichtigungen wird das Senden eines Updates mit einem 3D-Medienobjekt derzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="686b4-185">Tile notifications don't currently support sending an update with a 3D asset.</span></span> <span data-ttu-id="686b4-186">Dies bedeutet, dass Entwickler nicht folgende Aktionen ausführen können:</span><span class="sxs-lookup"><span data-stu-id="686b4-186">This means that developers can't do the following:</span></span>

* <span data-ttu-id="686b4-187">Pushbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="686b4-187">Push Notifications</span></span>
* <span data-ttu-id="686b4-188">Periodische Abruf Vorgänge</span><span class="sxs-lookup"><span data-stu-id="686b4-188">Periodic Polling</span></span>
* <span data-ttu-id="686b4-189">Geplante Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="686b4-189">Scheduled Notifications</span></span>

<span data-ttu-id="686b4-190">Weitere Informationen zu den anderen Kacheln Features und Attributen und deren Verwendung für 2D-Kacheln finden Sie in der [Dokumentation Kacheln für UWP-apps](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).</span><span class="sxs-lookup"><span data-stu-id="686b4-190">For more information on the other tiles features and attributes and how they're used for 2D tiles, see the [Tiles for UWP Apps documentation](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).</span></span>

## <a name="see-also"></a><span data-ttu-id="686b4-191">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="686b4-191">See also</span></span>

* <span data-ttu-id="686b4-192">[Gemischtes Reality-Modell Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) mit einem 3D-App-Start Programm.</span><span class="sxs-lookup"><span data-stu-id="686b4-192">[Mixed reality model sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) containing a 3D app launcher.</span></span>
* [<span data-ttu-id="686b4-193">Entwurfsanleitung für 3D-App-Startprogramm</span><span class="sxs-lookup"><span data-stu-id="686b4-193">3D app launcher design guidance</span></span>](3d-app-launcher-design-guidance.md)
* [<span data-ttu-id="686b4-194">Erstellen von 3D-Modellen für die Verwendung in der Windows Mixed Reality-Startseite</span><span class="sxs-lookup"><span data-stu-id="686b4-194">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="686b4-195">Implementieren von 3D-App-launchern (Win32-Apps)</span><span class="sxs-lookup"><span data-stu-id="686b4-195">Implementing 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
* [<span data-ttu-id="686b4-196">Navigieren auf der Startseite von Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="686b4-196">Navigating the Windows Mixed Reality home</span></span>](../discover/navigating-the-windows-mixed-reality-home.md)
