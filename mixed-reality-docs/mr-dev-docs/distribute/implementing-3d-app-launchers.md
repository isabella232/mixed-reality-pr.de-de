---
title: Implementieren von 3D-App-Startprogrammen (UWP-Apps)
description: Erfahren Sie, wie Sie 3D-App-Start- und Logos für Windows Mixed Reality UWP-Apps und -Spiele auf HoloLens- und VR-Headsets erstellen.
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, Logo, Symbol, Modellierung, Startfeld, 3D-Startfeld, Kachel, Livecube, Deep Link, sekundäre Kachel, sekundäre Kachel, UWP, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, XML, Begrenzungsfeld, Unity
ms.openlocfilehash: b0ccff2aaba9c4693f58b134cdb3af9190b59befec0b31851273ed6a3bc1fc04
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196420"
---
# <a name="implement-3d-app-launchers-uwp-apps"></a>Implementieren von 3D-App-Startprogrammen (UWP-Apps)

> [!NOTE]
> Dieses Feature wurde im Rahmen des Fall Creators Update 2017 (RS3) für immersive Headsets hinzugefügt und wird von HoloLens mit dem update Windows 10 April 2018 unterstützt. Stellen Sie sicher, dass Ihre Anwendung auf eine Version des Windows SDK ausgerichtet ist, die größer oder gleich 10.0.16299 auf immersiven Headsets und 10.0.17125 auf HoloLens ist. Die neueste Windows SDK finden Sie [hier.](https://developer.microsoft.com/windows/downloads/windows-10-sdk)

Das [Windows Mixed Reality Home](../discover/navigating-the-windows-mixed-reality-home.md) ist der Ausgangspunkt, an dem Benutzer vor dem Starten von Anwendungen landen. Beim Erstellen einer UWP-Anwendung für Windows Mixed Reality werden Apps standardmäßig als 2D-Slates mit dem Logo ihrer App gestartet. Beim Entwickeln von Benutzererfahrungen für Windows Mixed Reality kann optional ein 3D-Starter definiert werden, um das Standardmäßige 2D-Starter für Ihre Anwendung außer Kraft zu setzen. Im Allgemeinen werden 3D-Startfelder empfohlen, um immersive Anwendungen zu starten, die Benutzer aus der Windows Mixed Reality Starten bringen. Das 2D-Standardstarter wird bevorzugt, wenn die App aktiviert wird. Sie können auch einen [3D-Deep Link (secondaryTile)](#3d-deep-links-secondarytiles) als 3D-Starter für Inhalte in einer 2D-UWP-App erstellen.

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a>Erstellungsprozess des 3D-App-Starters

Es gibt drei Schritte zum Erstellen eines 3D-App-Starters:
1. [Entwerfen und Konzeptieren](3d-app-launcher-design-guidance.md)
2. [Modellieren und Exportieren](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. Integrieren in Ihre Anwendung (dieser Artikel)

3D-Ressourcen, die als Startstarts für Ihre Anwendung verwendet werden sollen, sollten mithilfe der [Windows Mixed Reality Erstellungsrichtlinien](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) erstellt werden, um die Kompatibilität sicherzustellen. Objekte, die diese Erstellungsspezifikation nicht erfüllen, werden im Windows Mixed Reality Home nicht gerendert.

## <a name="configuring-the-3d-launcher"></a>Konfigurieren des 3D-Starters

Wenn Sie ein neues Projekt in Visual Studio erstellen, wird eine einfache Standardkachel erstellt, die den Namen und das Logo Ihrer App anzeigt. Um diese 2D-Darstellung durch ein benutzerdefiniertes 3D-Modell zu ersetzen, bearbeiten Sie das App-Manifest Ihrer Anwendung so, dass es das MixedRealityModel-Element als Teil Ihrer Standardkacheldefinition enthält. Um zum 2D-Startprogramm zurückzukehren, entfernen Sie einfach die MixedRealityModel-Definition aus dem Manifest.

### <a name="xml"></a>XML

Suchen Sie zunächst das App-Paketmanifest in Ihrem aktuellen Projekt. Standardmäßig erhält das Manifest den Namen Package.appxmanifest. Wenn Sie Visual Studio verwenden, klicken Sie im Projektmappen-Viewer mit der rechten Maustaste auf das Manifest, und wählen **Sie Quelle anzeigen** aus, um die XML-Datei zur Bearbeitung zu öffnen. 

Fügen Sie am Anfang des Manifests das uap5-Schema hinzu, und fügen Sie es als ignorierbaren Namespace ein:

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

Geben Sie als Nächstes "MixedRealityModel" in der Standardkachel für Ihre Anwendung an:

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

Das MixedRealityModel-Element akzeptiert einen Dateipfad, der auf ein in Ihrem App-Paket gespeichertes 3D-Medienobjekt verweist. Derzeit werden nur 3D-Modelle unterstützt, die mithilfe des GLB-Dateiformats bereitgestellt und anhand Windows Mixed Reality [Anweisungen zur Erstellung von 3D-Medienobjekten](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) erstellt wurden. Ressourcen müssen im App-Paket gespeichert werden, und Animationen werden derzeit nicht unterstützt. Wenn der Parameter "Path" leer gelassen wird, Windows zeigt die 2D-Slate anstelle des 3D-Startfelds an. **Hinweis:** Das GLB-Medienobjekt muss in ihren Buildeinstellungen als "Inhalt" gekennzeichnet werden, bevor Ihre App erstellt und ausgeführt wird.


![Wählen Sie im Projektmappen-Explorer die GLB-Datei aus, und markieren Sie sie im Abschnitt properties in den Buildeinstellungen als "Inhalt".](images/buildsetting-content-300px.png)<br>
*Wählen Sie im Projektmappen-Explorer die GLB-Datei aus, und markieren Sie sie im Abschnitt properties in den Buildeinstellungen als "Inhalt".*

### <a name="bounding-box"></a>Begrenzungsrahmen

Ein Begrenzungsfeld kann verwendet werden, um optional einen zusätzlichen Pufferbereich um das Objekt hinzuzufügen. Der begrenzungsfeld wird mithilfe eines Mittelpunkts und von Erweiterungen angegeben, die den Abstand zwischen der Mitte des begrenzungsfelds und seinen Rändern entlang jeder Achse angeben. Einheiten für den Begrenzungsfeld können 1 Einheit = 1 Meter zugeordnet werden. Wenn kein Begrenzungsfeld angegeben wird, wird einer automatisch an das Gittermodell des Objekts angepasst. Wenn der angegebene Begrenzungsfeld kleiner als das Modell ist, wird die Größe an das Gittermodell angepasst.

Die Unterstützung für das Begrenzungsfeldattribut wird mit dem Windows RS4-Update als Eigenschaft für das MixedRealityModel-Element unterstützt. Um zuerst oben im App-Manifest ein Begrenzungsfeld zu definieren, fügen Sie das uap6-Schema hinzu und fügen es als ignorierbare Namespaces ein:

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
Legen Sie als Nächstes im MixedRealityModel die SpatialBoundingBox-Eigenschaft fest, um das umgebende Feld zu definieren: 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a>Verwendung von Unity

Bei der Arbeit mit Unity muss das Projekt in Visual Studio erstellt und geöffnet werden, bevor das App-Manifest bearbeitet werden kann. 

>[!NOTE]
>Das 3D-Startprogramm muss beim Erstellen und Bereitstellen einer neuen Visual Studio-Lösung von Unity im Manifest neu definiert werden.

## <a name="3d-deep-links-secondarytiles"></a>3D Deep Links (secondaryTiles)

> [!NOTE]
> Dieses Feature wurde im Rahmen des Fall Creators Update 2017 (RS3) für immersive Headsets (VR) und als Teil des April 2018 Update (RS4) für HoloLens hinzugefügt. Stellen Sie sicher, dass Ihre Anwendung eine Version des Windows SDK anzielt, die größer oder gleich 10.0.16299 auf immersiven Headsets (VR) und 10.0.17125 auf HoloLens ist. Die neueste Windows SDK finden Sie [hier.](https://developer.microsoft.com/windows/downloads/windows-10-sdk)

>[!IMPORTANT]
>3D Deep Links (secondaryTiles) funktionieren nur mit 2D-UWP-Apps. Sie können jedoch einen [3D-App-Starter](implementing-3d-app-launchers.md) erstellen, um eine exklusive App über die Windows Mixed Reality Startseite zu starten.

Ihre 2D-Anwendungen können für Windows Mixed Reality verbessert werden, indem Sie die Möglichkeit hinzufügen, 3D-Modelle aus Ihrer App im [Windows Mixed Reality Home](../discover/navigating-the-windows-mixed-reality-home.md) als DeepLinks zu Inhalten in Ihrer 2D-App zu platzieren, genau wie [sekundäre 2D-Kacheln](/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) auf dem Windows Startmenü. Beispielsweise können Sie 360°-Fotospheres erstellen, die direkt mit einer 360°-Foto-Viewer-App verknüpft sind, oder Benutzern ermöglichen, 3D-Inhalte aus einer Sammlung von Ressourcen zu platzieren, die eine Detailseite zum Autor öffnen. Dies sind nur einige Möglichkeiten, um die Funktionalität Ihrer 2D-Anwendung mit 3D-Inhalten zu erweitern.

### <a name="creating-a-3d-secondarytile"></a>Erstellen eines 3D-"secondaryTile"

Sie können 3D-Inhalte aus Ihrer Anwendung mit "secondaryTiles" platzieren, indem Sie zur Erstellungszeit ein Mixed Reality-Modell definieren. Mixed Reality-Modelle werden erstellt, indem sie auf ein 3D-Medienobjekt in Ihrem App-Paket verweisen und optional einen Begrenzungsfeld definieren. 

> [!NOTE]
> Das Erstellen von "secondaryTiles" aus einer exklusiven Sicht wird derzeit nicht unterstützt.

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

### <a name="bounding-box"></a>Begrenzungsrahmen

Ein Begrenzungsfeld kann verwendet werden, um einen zusätzlichen Pufferbereich um das Objekt hinzuzufügen. Der begrenzungsfeld wird mithilfe eines Mittelpunkts und von Erweiterungen angegeben, die den Abstand zwischen der Mitte des begrenzungsfelds und seinen Rändern entlang jeder Achse angeben. Einheiten für den Begrenzungsfeld können 1 Einheit = 1 Meter zugeordnet werden. Wenn kein Begrenzungsfeld angegeben wird, wird dieses automatisch an das Gittermodell des Objekts angepasst. Wenn der angegebene Begrenzungsfeld kleiner als das Modell ist, wird die Größe an das Gittermodell angepasst.

### <a name="activation-behavior"></a>Aktivierungsverhalten

> [!NOTE]
> Dieses Feature wird ab dem Windows RS4-Update unterstützt. Stellen Sie sicher, dass Ihre Anwendung auf eine Version des Windows SDK ausgerichtet ist, die größer oder gleich 10.0.17125 ist, wenn Sie dieses Feature verwenden möchten.

Sie können das Aktivierungsverhalten für ein sekundäres 3D-Tile definieren, um zu steuern, wie es reagiert, wenn ein Benutzer es auswählt. Dies kann verwendet werden, um 3D-Objekte im Mixed Reality Haus zu platzieren, die rein informativ oder zierlich sind. Die folgenden Aktivierungsverhaltenstypen werden unterstützt:
1. Standardeinstellung: Wenn ein Benutzer das sekundäre 3D-Kontrollkästchen auswählt, wird die App aktiviert.
2. Keine: Wenn der Benutzer das sekundäre 3D-Kontrollkästchen auswählt, geschieht nichts, und die App wird nicht aktiviert.

### <a name="obtaining-and-updating-an-existing-secondarytile"></a>Abrufen und Aktualisieren eines vorhandenen "secondaryTile"

Entwickler können eine Liste ihrer vorhandenen sekundären Kacheln abrufen, die die zuvor angegebenen Eigenschaften enthält. Sie können die Eigenschaften auch aktualisieren, indem sie den Wert ändern und dann UpdateAsync() aufrufen.

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

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a>Überprüfen, ob sich der Benutzer in Windows Mixed Reality

3D Deep Links (secondaryTiles) können nur erstellt werden, während die Ansicht in einem Windows Mixed Reality Headset angezeigt wird. Wenn Ihre Ansicht nicht in einem Windows Mixed Reality Headset angezeigt wird, wird empfohlen, dies ordnungsgemäß zu behandeln, indem Sie entweder den Einstiegspunkt ausblenden oder eine Fehlermeldung anzeigen. Sie können dies überprüfen, indem Sie [IsCurrentViewPresentedOnHolographic()](/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_)abfragen.

## <a name="tile-notifications"></a>Kachelbenachrichtigungen

Kachelbenachrichtigungen unterstützen derzeit nicht das Senden eines Updates mit einem 3D-Medienobjekt. Dies bedeutet, dass Entwickler folgende Schritte nicht ausführen können:

* Pushbenachrichtigungen
* Regelmäßige Abrufe
* Geplante Benachrichtigungen

Weitere Informationen zu den anderen Kachelfeatures und -attributen und deren Verwendung für 2D-Kacheln finden Sie in der [Dokumentation Kacheln für UWP-Apps.](/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles)

## <a name="see-also"></a>Siehe auch

* [Mixed Reality-Modellbeispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) mit einem 3D-App-Starter.
* [Entwurfsanleitung für 3D-App-Startprogramm](3d-app-launcher-design-guidance.md)
* [Erstellen von 3D-Modellen für die Verwendung im Windows Mixed Reality Home](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Implementieren von 3D-App-Startern (Win32-Apps)](implementing-3d-app-launchers-win32.md)
* [Navigieren auf der Startseite von Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md)