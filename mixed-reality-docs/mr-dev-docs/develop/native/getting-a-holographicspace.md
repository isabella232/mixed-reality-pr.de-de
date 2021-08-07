---
title: Abrufen eines HolographicSpace-Objekts
description: Erfahren Sie, wie Sie die HolographicSpace-API für holografisches Rendering und räumliche Eingabe in Ihren Mixed Reality-Apps verwenden.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, HolographicSpace, CoreWindow, spatial input, rendering, swap chain, holographic frame, update loop, game loop, frame of reference, locatability, sample code, walkthrough, mixed reality headset, windows mixed reality headset, virtual reality headset
ms.openlocfilehash: 986ccdc6e81d1ac7c7b401a427da548218a68eb0352a0057bf7d7aba3c1d6d6a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212168"
---
# <a name="getting-a-holographicspace"></a>Abrufen eines HolographicSpace-Objekts

> [!NOTE]
> Dieser Artikel bezieht sich auf die älteren nativen WinRT-APIs.  Für neue native App-Projekte wird die Verwendung der **[OpenXR-API empfohlen.](openxr-getting-started.md)**

Die <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace-Klasse</a> ist Ihr Portal in der holografischen Welt. Sie steuert immersives Rendering, stellt Kameradaten zur Auswahl und bietet Zugriff auf RÄUMLICHE BEGRÜNDUNG-APIs. Sie erstellen einen für <a href="/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> Ihrer UWP-App oder den HWND Ihrer Win32-App.

## <a name="set-up-the-holographic-space"></a>Einrichten des holografischen Raums

Das Erstellen des holografischen Raumobjekts ist der erste Schritt beim Erstellen ihrer Windows Mixed Reality App. Herkömmliche Windows-Apps werden in einer Direct3D-Austauschkette gerendert, die für das Hauptfenster ihrer Anwendungsansicht erstellt wurde. Diese Austauschkette wird in einer Tafel auf der holografischen Benutzeroberfläche angezeigt. Um ihre Anwendungsansicht holografische statt einer 2D-Tafel zu machen, erstellen Sie einen holografischen Raum für das Kernfenster anstelle einer Austauschkette. Die Darstellung holografischer Frames, die von diesem holografischen Raum erstellt werden, versetzt Ihre App in den Vollbildrenderingmodus.

Suchen Sie für **eine UWP-App** ab der [Vorlage *Holographic DirectX 11 App (Universal Windows)*](creating-a-holographic-directx-project.md)in der **SetWindow-Methode** in AppView.cpp nach diesem Code:

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

Wenn Sie eine **Win32-App** erstellen, die mit dem [Win32-Beispiel *BasicHologram*](creating-a-holographic-directx-project.md#creating-a-win32-project)beginnt, finden Sie unter **App::CreateWindowAndHolographicSpace** ein HWND-Beispiel. Sie können sie dann in ein immersives HWND konvertieren, indem Sie einen zugeordneten <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace erstellen:</a>

```cpp
void App::CreateWindowAndHolographicSpace(HINSTANCE hInstance, int nCmdShow)
{
    // Store the instance handle in our class variable.
    m_hInst = hInstance;

    // Create the window for the HolographicSpace.
    hWnd = CreateWindowW(
        m_szWindowClass, 
        m_szTitle,
        WS_VISIBLE,
        CW_USEDEFAULT, 
        0, 
        CW_USEDEFAULT, 
        0, 
        nullptr, 
        nullptr, 
        hInstance, 
        nullptr);

    if (!hWnd)
    {
        winrt::check_hresult(E_FAIL);
    }

    {
        // Use WinRT factory to create the holographic space.
        using namespace winrt::Windows::Graphics::Holographic;
        winrt::com_ptr<IHolographicSpaceInterop> holographicSpaceInterop =
            winrt::get_activation_factory<HolographicSpace, IHolographicSpaceInterop>();
        winrt::com_ptr<ABI::Windows::Graphics::Holographic::IHolographicSpace> spHolographicSpace;
        winrt::check_hresult(holographicSpaceInterop->CreateForWindow(
            hWnd, __uuidof(ABI::Windows::Graphics::Holographic::IHolographicSpace),
            winrt::put_abi(spHolographicSpace)));

        if (!spHolographicSpace)
        {
            winrt::check_hresult(E_FAIL);
        }

        // Store the holographic space.
        m_holographicSpace = spHolographicSpace.as<HolographicSpace>();
    }

    // The DeviceResources class uses the preferred DXGI adapter ID from the holographic
    // space (when available) to create a Direct3D device. The HolographicSpace
    // uses this ID3D11Device to create and manage device-based resources such as
    // swap chains.
    m_deviceResources->SetHolographicSpace(m_holographicSpace);

    // The main class uses the holographic space for updates and rendering.
    m_main->SetHolographicSpace(hWnd, m_holographicSpace);

    // Show the window. This will activate the holographic view and switch focus
    // to the app in Windows Mixed Reality.
    ShowWindow(hWnd, nCmdShow);
    UpdateWindow(hWnd);
}
```

Nachdem Sie einen HolographicSpace für UWP CoreWindow oder Win32 HWND erhalten haben, kann HolographicSpace holografische Kameras verarbeiten, Koordinatensysteme erstellen und holografisches Rendering ermöglichen. Der aktuelle holografische Raum wird an mehreren Stellen in der DirectX-Vorlage verwendet:
* Die **DeviceResources-Klasse** muss einige Informationen aus dem HolographicSpace-Objekt erhalten, um das Direct3D-Gerät zu erstellen. Dies ist die DXGI-Adapter-ID, die der holografischen Anzeige zugeordnet ist. Die <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace-Klasse</a> verwendet das Direct3D 11-Gerät Ihrer App, um gerätebasierte Ressourcen zu erstellen und zu verwalten, z. B. die Hintergrundpuffer für jede holografische Kamera. Wenn Sie wissen möchten, was diese Funktion im Blick hat, finden Sie sie in DeviceResources.cpp.
* Die **Funktion DeviceResources::InitializeUsingHolographicSpace** veranschaulicht, wie sie den Adapter durch Suchen der LUID abrufen und einen Standardadapter auswählen, wenn kein bevorzugter Adapter angegeben ist.
* Die Hauptklasse der App verwendet den holografischen Raum aus **AppView::SetWindow** oder **App::CreateWindowAndHolographicSpace** für Updates und Rendering.

>[!NOTE]
>Während in den folgenden Abschnitten Funktionsnamen aus der Vorlage wie **AppView::SetWindow** erwähnt werden, die davon ausgehen, dass Sie mit der holografischen UWP-App-Vorlage begonnen haben, gelten die angezeigten Codeausschnitte gleichermaßen für UWP- und Win32-Apps.

Als Nächstes erfahren Sie mehr über den Setupprozess, für den **SetHolographicSpace** in der AppMain-Klasse verantwortlich ist.

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a>Abonnieren von Kameraereignissen, Erstellen und Entfernen von Kameraressourcen

Der holografische Inhalt Ihrer App befindet sich im holografischen Raum und wird über eine oder mehrere holografische Kameras angezeigt, die unterschiedliche Perspektiven der Szene darstellen. Nachdem Sie nun über den holografischen Raum verfügen, können Sie Daten für holografische Kameras empfangen.

Ihre App muss auf **CameraAdded-Ereignisse** reagieren, indem sie ressourcenspezifische Ressourcen für diese Kamera erstellt. Ein Beispiel für eine solche Ressource ist die Renderzielansicht des Hintergrundpuffers. Sie können diesen Code in der **Funktion DeviceResources::SetHolographicSpace** sehen, die von **AppView::SetWindow** aufgerufen wird, bevor die App holografische Frames erstellt:

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

Ihre App muss auch auf **CameraRemoved-Ereignisse** reagieren, indem sie Ressourcen frei gibt, die für diese Kamera erstellt wurden.

Über **DeviceResources::SetHolographicSpace:**

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

Die Ereignishandler müssen einige Arbeiten abschließen, damit holografisches Rendering reibungslos verläuft und Ihre App überhaupt gerendert wird. Lesen Sie den Code und die Kommentare für die Details: Sie können in Ihrer Hauptklasse nach **OnCameraAdded** und **OnCameraRemoved** suchen, um zu verstehen, wie die **m_cameraResources-Karte** von **DeviceResources** behandelt wird.

Im Moment konzentrieren wir uns auf AppMain und das Setup, mit dem Ihre App holografische Kameras kennenlernen kann. Vor diesem Hintergrund ist es wichtig, die folgenden beiden Anforderungen zu beachten:

1. Für den **CameraAdded-Ereignishandler** kann die App asynchron arbeiten, um die Erstellung von Ressourcen und das Laden von Ressourcen für die neue holografische Kamera fertig zu stellen. Apps, die mehr als einen Frame für diese Arbeit verwenden, sollten eine Verzögerung anfordern und die Verzögerung nach dem asynchronen Laden abschließen. Eine [PPL-Aufgabe](/cpp/parallel/concrt/parallel-patterns-library-ppl) kann für asynchrone Aufgaben verwendet werden. Ihre App muss sicherstellen, dass sie sofort auf diese Kamera gerendert werden kann, wenn sie den Ereignishandler beendet oder die Verzögerung abgeschlossen hat. Durch Beenden des Ereignishandlers oder Abschließen der Verzögerung wird dem System angezeigt, dass Ihre App jetzt bereit ist, holografische Frames mit dieser Kamera zu empfangen.

2. Wenn die App ein **CameraRemoved-Ereignis** empfängt, muss sie alle Verweise auf den Hintergrundpuffer frei geben und die Funktion sofort beenden. Dies schließt Renderzielansichten und alle anderen Ressourcen ein, die einen Verweis auf [IDXGIResource enthalten können.](/windows/desktop/api/dxgi/nn-dxgi-idxgiresource) Die App muss außerdem sicherstellen, dass der Hintergrundpuffer nicht als Renderziel angefügt wird, wie in **CameraResources::ReleaseResourcesForBackBuffer gezeigt.** Um Dies zu beschleunigen, kann Ihre App den Hintergrundpuffer wieder frei geben und dann eine Aufgabe starten, um alle anderen Abfahrarbeiten für die Kamera asynchron auszuführen. Die holografische App-Vorlage enthält eine PPL-Aufgabe, die Sie für diesen Zweck verwenden können.

>[!NOTE]
>Wenn Sie ermitteln möchten, wann eine hinzugefügte oder entfernte Kamera auf dem Frame angezeigt wird, verwenden Sie die **Eigenschaften HolographicFrame** [AddedCameras](/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) und [RemovedCameras.](/uwp/api/windows.graphics.holographic.holographicframe.removedcameras)

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a>Erstellen eines Referenzframes für Ihren holografischen Inhalt

Der Inhalt Ihrer App muss in [](coordinate-systems-in-directx.md) einem Raumkoordinatensystem positioniert werden, um im HolographicSpace gerendert zu werden. Das System bietet zwei primäre Bezugsrahmen, mit denen Sie ein Koordinatensystem für Ihre Hologramme einrichten können.

Es gibt zwei Arten von Referenzframes in Windows Holographic: an das Gerät angefügte Referenzframes und Referenzframes, die während der Bewegung des Geräts durch die Umgebung des Benutzers unverändert bleiben. Die holografische App-Vorlage verwendet standardmäßig einen stationären Referenzrahmen. dies ist eine der einfachsten Möglichkeiten, um weltweit gesperrte Hologramme zu rendern.

Stationäre Referenzrahmen sind so konzipiert, dass positionen in der Nähe des aktuellen Standorts des Geräts stabilisiert werden. Dies bedeutet, dass die Weiterkoordinaten des Geräts relativ zur Umgebung des Benutzers leicht abdriften können, wenn das Gerät mehr über den Raum um das Gerät lernt. Es gibt zwei Möglichkeiten, einen fest stehenden Bezugsrahmen zu erstellen: das Koordinatensystem aus der räumlichen Phase zu erhalten [oder](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)den Standardmäßigen <a href="/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator zu verwenden.</a> Wenn Sie eine app-Windows Mixed Reality immersive Headsets erstellen, ist der empfohlene Ausgangspunkt die [räumliche Phase](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage). Die räumliche Stufe bietet auch Informationen über die Funktionen des immersiven Headsets, das vom Player unterstützt wird. Hier wird gezeigt, wie der <a href="/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator-Standardwert verwendet wird.</a>

Der räumliche Locator stellt Windows Mixed Reality Gerät dar, verfolgt die Bewegung des Geräts und stellt Koordinatensysteme zur Verfügung, die relativ zu seiner Position verstanden werden können.

Von **AppMain::OnHolographicDisplayIsAvailableChanged:**

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

Erstellen Sie den stillen Referenzrahmen einmal, wenn die App gestartet wird. Dies entspricht der Definition eines Weltkoordinatensystems, bei dem der Ursprung beim Start der App an der Geräteposition platziert wird. Dieser Referenzrahmen wird nicht mit dem Gerät bewegt.

Von **AppMain::SetHolographicSpace:**

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

Alle Referenzframes sind schwerkraftbündig ausgerichtet, was bedeutet, dass die y-Achse in Bezug auf die Umgebung des Benutzers "nach oben" zeigt. Da Windows "rechtshändige" Koordinatensysteme verwendet, stimmt die Richtung der –z-Achse mit der "vorwärts"-Richtung überein, auf die das Gerät beim Erstellen des Referenzrahmens zu sehen ist.

>[!NOTE]
>Wenn Ihre App eine genaue Platzierung einzelner Hologramme erfordert, verwenden Sie <a href="/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">einen SpatialAnchor,</a> um das einzelne Hologramm an einer Position in der realen Welt zu verankern. Verwenden Sie beispielsweise einen Raumanker, wenn der Benutzer angibt, dass ein Punkt von besonderem Interesse ist. Ankerpositionen driften nicht ab, können aber angepasst werden. Wenn ein Anker angepasst wird, vereinfacht er standardmäßig seine Position gegenüber den nächsten frames, nachdem die Korrektur erfolgt ist. Je nach Anwendung sollten Sie die Anpassung in diesem Fall auf andere Weise verarbeiten (z. B. durch Zurückstellung, bis das Hologramm nicht mehr angezeigt wird). Die <a href="/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem-Eigenschaft</a> <a href="/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">und die RawCoordinateSystemAdjusted-Ereignisse</a> ermöglichen diese Anpassungen.

## <a name="respond-to-locatability-changed-events"></a>Reagieren auf Ereignisse mit geänderter Verkettbarkeit

Das Rendern von weltweit gesperrten Hologrammen erfordert, dass sich das Gerät auf der Welt befindet. Dies ist möglicherweise nicht immer aufgrund von Umgebungsbedingungen möglich. Wenn dies der Fall ist, erwartet der Benutzer möglicherweise einen visuellen Hinweis auf die Nachverfolgungsunterbrechung. Diese visuelle Anzeige muss mithilfe von Referenzframes gerendert werden, die an das Gerät angefügt sind, anstatt stationär auf der Welt zu sein.

Ihre App kann anfordern, dass sie benachrichtigt wird, wenn die Nachverfolgung aus irgendeinem Grund unterbrochen wird. Registrieren Sie sich für das LocatabilityChanged-Ereignis, um zu erkennen, wann sich die Fähigkeit des Geräts ändert, sich in der Welt zu finden. Von **AppMain::SetHolographicSpace:**

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

Verwenden Sie dann dieses Ereignis, um zu bestimmen, wann Hologramme nicht zur Welt gerendert werden können.

## <a name="see-also"></a>Siehe auch
* [Rendern in DirectX](rendering-in-directx.md)
* [Koordinatensysteme in DirectX](coordinate-systems-in-directx.md)