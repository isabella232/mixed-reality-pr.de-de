---
title: Schreiben eines benutzerdefinierten Holographic Remoting-Players
description: Erstellen Sie eine benutzerdefinierte hologaphic-Remoting-App zum Anzeigen von Inhalten, die auf einem Remote Computer auf den hololens 2 gerendert werden
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: Hololens, Remoting, Holographic Remoting, nuget, App-Manifest, Player Kontext, Remote-app, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: b6a0d65b8ec1f07f7ebaae17b9921d48105474a4
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581243"
---
# <a name="writing-a-custom-holographic-remoting-player-app"></a>Schreiben einer benutzerdefinierten Holographic Remoting Player-App

>[!IMPORTANT]
>In diesem Dokument wird die Erstellung einer benutzerdefinierten Player Anwendung für hololens 2 beschrieben. Für hololens 2 geschriebene benutzerdefinierte Player sind nicht mit Remote Anwendungen kompatibel, die für hololens 1 geschrieben wurden. Dies bedeutet, dass beide Anwendungen das nuget-Paketversion **2. x. x** verwenden müssen.

Indem Sie eine benutzerdefinierte Holographic Remoting Player-App erstellen, können Sie eine benutzerdefinierte Anwendung erstellen, die die [immersiven Sichten](../../design/app-views.md) von auf einem Remote Computer auf den hololens 2 anzeigen kann. Sämtlicher Code auf dieser Seite und in den Arbeitsprojekten finden Sie im [GitHub-Repository "Holographic Remoting Samples](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)".

Ein Holographic Remoting Player ermöglicht Ihrer APP das Anzeigen von Holographic-Inhalten, die auf einem Desktop-PC oder einem UWP-Gerät wie der Xbox One mit Zugriff auf mehr Systemressourcen [gerendert](rendering.md) werden. Eine Holographic Remoting Player-App streamt Eingabedaten an eine Holographic Remoting-Remote Anwendung und empfängt eine immersive Ansicht als Video-und Audiodatenstrom. Die Verbindung wird mithilfe von Standard-Wi-Fi hergestellt. Um eine Player-App zu erstellen, verwenden Sie ein nuget-Paket, um der UWP-App Holographic Remoting hinzuzufügen. Dann schreiben Sie Code, um die Verbindung zu verarbeiten und eine immersive Ansicht anzuzeigen. 

## <a name="prerequisites"></a>Voraussetzungen

Ein guter Ausgangspunkt ist eine funktionierende DirectX-basierte UWP-APP, die bereits auf die Windows Mixed Reality-API abzielt. Weitere Informationen finden Sie unter [Übersicht über die DirectX-Entwicklung](../native/directx-development-overview.md). Wenn Sie keine vorhandene APP haben und von Grund auf neu beginnen möchten, ist die [Projektvorlage C++ Holographic](../native/creating-a-holographic-directx-project.md) ein guter Ausgangspunkt.

>[!IMPORTANT]
>Jede APP, die Holographic Remoting verwendet, sollte für die Verwendung eines [Multithread-Apartment](//windows/win32/com/multithreaded-apartments)erstellt werden. Die Verwendung eines [Single Thread-Apartment](//windows/win32/com/single-threaded-apartments) wird unterstützt, führt jedoch zu einer nicht optimalen Leistung und kann während der Wiedergabe möglicherweise zu einem stutor werden. Bei Verwendung von C++/WinRT [WinRT:: init_apartment](//windows/uwp/cpp-and-winrt-apis/get-started) ist ein Multithread-Apartment der Standard.

## <a name="get-the-holographic-remoting-nuget-package"></a>Holen Sie sich das Holographic Remoting-nuget-Paket.

Die folgenden Schritte sind erforderlich, um das nuget-Paket einem Projekt in Visual Studio hinzuzufügen.
1. Öffnen Sie das Projekt in Visual Studio.
2. Klicken Sie mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie **nuget-Pakete verwalten aus.**
3. Wählen Sie im angezeigten Bereich **Durchsuchen** aus, und suchen Sie dann nach "Holographic Remoting".
4. Wählen Sie **Microsoft. Holographic. Remoting** aus, stellen Sie sicher, dass die neueste Version **2. x. x** ausgewählt ist, und wählen Sie **Installieren** aus.
5. Wenn das Dialogfeld **Vorschau** angezeigt wird, klicken Sie auf **OK**.
6. Wählen Sie **Ich akzeptiere** aus, wenn das Dialogfeld Lizenzvertrag angezeigt wird.

>[!IMPORTANT]
><a name="idl"></a>Der ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` im nuget-Paket enthält eine ausführliche Dokumentation für die API, die von Holographic Remoting verfügbar gemacht wird.

## <a name="modify-the-packageappxmanifest-of-the-application"></a>Ändern Sie die Datei "Package. appxmanifest" der Anwendung.

Um die Anwendung auf die vom nuget-Paket hinzugefügten Microsoft.Holographic.AppRemoting.dll aufmerksam zu machen, müssen die folgenden Schritte für das Projekt ausgeführt werden:

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf die Datei " **Package. appxmanifest** ", und wählen Sie **Öffnen mit...**
2. **XML (Text)-Editor** auswählen und **OK** auswählen
3. Fügen Sie der Datei die folgenden Zeilen hinzu, und speichern Sie Sie.
```xml
  </Capabilities>

  <!--Add lines below -->
  <Extensions>
    <Extension Category="windows.activatableClass.inProcessServer">
      <InProcessServer>
        <Path>Microsoft.Holographic.AppRemoting.dll</Path>
        <ActivatableClass ActivatableClassId="Microsoft.Holographic.AppRemoting.PlayerContext" ThreadingModel="both" />
      </InProcessServer>
    </Extension>
  </Extensions>
  <!--Add lines above -->

</Package>
```
## <a name="create-the-player-context"></a>Erstellen des Player Kontexts

Als ersten Schritt sollte die Anwendung einen Player Kontext erstellen.

```cpp
// class declaration:

#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
// PlayerContext used to connect with a Holographic Remoting remote app and display remotely rendered frames
winrt::Microsoft::Holographic::AppRemoting::PlayerContext m_playerContext = nullptr;
```


```cpp
// class implementation:

// Create the player context
// IMPORTANT: This must be done before creating the HolographicSpace (or any other call to the Holographic API).
m_playerContext = winrt::Microsoft::Holographic::AppRemoting::PlayerContext::Create();

```

>[!WARNING]
>Holographic Remoting funktioniert durch das Ersetzen der Windows Mixed Reality-Laufzeit, die Teil von Windows ist, durch eine Remoting-spezifische Laufzeit. Dies erfolgt während der Erstellung des Player Kontexts. Aus diesem Grund kann jeder beliebige Windows Mixed Reality-API-Aufrufe vor dem Erstellen des Player Kontexts zu unerwartetem Verhalten führen. Die empfohlene Vorgehensweise besteht darin, den Player Kontext so früh wie möglich zu erstellen, bevor Sie mit jeder gemischten Reality-API interagieren. Erstellen oder Abrufen von Objekten, die über eine Windows Mixed Reality-API erstellt oder abgerufen wurden, vor dem aufgerufenen ```PlayerContext::Create``` von Objekten, die später erstellt oder abgerufen werden

Als nächstes kann der holographicspace durch Aufrufen von [holographicspace. createforcorewindow](//uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow)erstellt werden.

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-remote-app"></a>Herstellen einer Verbindung mit der Remote-app

Sobald die Player-App zum Rendern von Inhalten bereit ist, kann eine Verbindung mit der Remote-app hergestellt werden.

Die Verbindung kann auf eine der folgenden Arten hergestellt werden:
1) Die Player-App auf hololens 2 stellt eine Verbindung mit der Remote-app her.
2) Die Remote-app stellt eine Verbindung mit der Player-App her, die auf hololens 2 ausgeführt wird

Um eine Verbindung zwischen der Player-App und der Remote-app herzustellen, wird die- ```Connect``` Methode im Player Kontext aufgerufen, um den Hostnamen und den Port anzugeben. Der Standardport ist **8265**.

```cpp
try
{
    m_playerContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    // Failed to connect. Get an error details via e.code() and e.message()
}
```

>[!IMPORTANT]
>Wie bei jeder C++/WinRT-API ```Connect``` könnte eine WinRT:: hresult_error ausgelöst werden, die behandelt werden muss.

Das Lauschen auf eingehende Verbindungen für die Player-App kann durch Aufrufen der- ```Listen``` Methode erfolgen. Der Handshake-Port und der Transporttyp können während dieses Aufrufes angegeben werden. Der Handshake-Port wird für den ersten Handshake verwendet. Die Daten werden dann über den transportport gesendet. Standardmäßig werden Portnummer **8265** und **8266** verwendet.

```cpp
try
{
    m_playerContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    // Failed to listen. Get an error details via e.code() and e.message()
}
```


## <a name="handling-connection-related-events"></a>Behandeln Verbindungs bezogener Ereignisse

Der Macht ```PlayerContext``` drei Ereignisse verfügbar, um den Status der Verbindung zu überwachen.
1) Onconnected: wird ausgelöst, wenn eine Verbindung mit der Remote-app erfolgreich hergestellt wurde.
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) Ongetrennte: wird ausgelöst, wenn eine etablierte Verbindung beendet oder eine Verbindung nicht hergestellt werden konnte.
```cpp
m_onDisconnectedEventToken = m_playerContext.OnDisconnected([](ConnectionFailureReason failureReason)
{
    switch (failureReason)
    {
        // Handle connection failed or terminated.
        // See ConnectionFailureReason for possible reasons.
    }
}
```
>[!NOTE]
>Mögliche ```ConnectionFailureReason``` Werte sind in der ```Microsoft.Holographic.AppRemoting.idl``` [Datei](#idl)dokumentiert.

3) Onlistening: beim lauschen auf eingehende Verbindungen wird gestartet.
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

Außerdem kann der Verbindungsstatus mithilfe der- ```ConnectionState``` Eigenschaft im Player Kontext abgefragt werden.
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a>Remote gerenderten Frame anzeigen

Um den Remote gerenderten Inhalt anzuzeigen, aufrufen Sie, ```PlayerContext::BlitRemoteFrame``` während Sie einen [holographicframe](//uwp/api/windows.graphics.holographic.holographicframe)rendern. 

```BlitRemoteFrame``` erfordert, dass der Hintergrund Puffer für den aktuellen holographicframe als Renderziel gebunden ist. Der Hintergrund Puffer kann von [holographiccamer-deringparameters](//uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) über die [Direct3D11BackBuffer](//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) -Eigenschaft empfangen werden.

Wenn Sie aufgerufen wird, wird ```BlitRemoteFrame``` der letzte empfangene Frame aus der Remote Anwendung in den BackBuffer von holographicframe kopiert. Außerdem wird der Fokus Punktsatz festgelegt, wenn die Remote Anwendung während des Renderings des Remote Frames einen Fokuspunkt angegeben hat.

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
>```PlayerContext::BlitRemoteFrame``` überschreibt möglicherweise den Fokuspunkt für den aktuellen Frame. 
>- Um einen Fall Back Fokuspunkt anzugeben, nennen Sie [holographiccamerarenderingparameters:: setfocuspoint](//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) vor ```PlayerContext::BlitRemoteFrame``` . 
>- Um den Remote Fokuspunkt zu überschreiben, wenden Sie [holographiccamer-deringparameters:: setfocuspoint](//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)  nach an ```PlayerContext::BlitRemoteFrame``` .

Bei Erfolg wird ```BlitRemoteFrame``` zurückgegeben ```BlitResult::Success_Color``` . Andernfalls wird die Fehlerursache zurückgegeben:
- ```BlitResult::Failed_NoRemoteFrameAvailable```: Fehlgeschlagen, da kein Remote Rahmen verfügbar ist.
- ```BlitResult::Failed_NoCamera```: Fehlgeschlagen, da keine Kamera vorhanden ist.
- ```BlitResult::Failed_RemoteFrameTooOld```: Fehlgeschlagen, da der Remote Rahmen zu alt ist (siehe playercontext:: blitremoteframetimeout-Eigenschaft).

>[!IMPORTANT]
> Ab Version [2.1.0](holographic-remoting-version-history.md#v2.1.0) ist es möglich, dass ein benutzerdefinierter Player die Tiefe Reprojektion über Holographic Remoting verwendet.

```BlitResult``` kann auch ```BlitResult::Success_Color_Depth``` unter den folgenden Bedingungen zurückgeben:

- Die Remote-app hat einen tiefen Puffer über [holographiccamerarenderingparameters. CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)committet.
- Die benutzerdefinierte Player-App hat einen gültigen tiefen Puffer vor dem Aufrufen von gebunden ```BlitRemoteFrame``` .

Wenn diese Bedingungen erfüllt sind, ```BlitRemoteFrame``` wird die Remote Tiefe in den aktuell gebundenen lokalen tiefen Puffer bliert. Sie können dann zusätzlichen lokalen Inhalt rendern, der eine Tiefe Überschneidung mit dem Remote gerenderten Inhalt hat. Darüber hinaus können Sie den lokalen tiefen Puffer über [holographiccamer-deringparameters. CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) im benutzerdefinierten Player übertragen, um eine Tiefe neuprojektion für Remote-und lokal gerenderten Inhalt zu erhalten. Weitere Informationen finden Sie unter [Tiefe Reprojektion](hologram-stability.md#reprojection) .

### <a name="projection-transform-mode"></a>Projektions Transformations Modus

Ein Problem, das bei der Verwendung der tiefen neuprojektion über Holographic Remoting auftritt, besteht darin, dass der Remote Inhalt mit einer anderen Projektions Transformation gerendert werden kann als lokale Inhalte, die von Ihrer benutzerdefinierten Player-App direkt gerendert Ein gängiger Anwendungsfall besteht darin, verschiedene Werte für die Near-und Far-Ebene (über [holographiccamera:: setnearplanedistance](/uwp/api/windows.graphics.holographic.holographiccamera.setnearplanedistance) und [holographiccamera:: setfarplanedistance](/uwp/api/windows.graphics.holographic.holographiccamera.setfarplanedistance)) auf der Player-Seite und der Remote Seite anzugeben. In diesem Fall ist es nicht klar, ob die Projektions Transformation auf der Player Seite die Remote Abstände der nächsten bzw. fernen Ebene oder die lokalen Entfernungen widerspiegeln soll.

Ab Version [2.1.0](holographic-remoting-version-history.md#v2.1.0) können Sie den Projektions Transformations Modus über Steuern ```PlayerContext::ProjectionTransformConfig``` . Diese Werte werden unterstützt:

- ```Local``` - [Holographiccamerapose::P rojectiontransform](/uwp/api/windows.graphics.holographic.holographiccamerapose.projectiontransform) gibt eine Projektions Transformation zurück, die die von Ihrer benutzerdefinierten Player-App auf der holographiccamera festgelegten Abstände in der Nähe der nächsten Ebene widerspiegelt.
- ```Remote``` -Die Transformation für Projektion spiegelt die von der Remote-app festgelegten Abstände in der Nähe der Nähe und der entfernten
- ```Merged``` -In der Nähe von Ihrer Remote-app und Ihrer benutzerdefinierten Player-App werden Near-und Far-Ebenen-Abstände Standardmäßig wird dies erreicht, indem die Mindestabstände der Near-Ebene und der Höchstwert für die Abstände auf der Ebenen der Ebene erreicht werden. Wenn die Remote-oder die lokale Seite invertiert ist (z. & # < in der Nähe), werden die Remote Abstände der nahen/fernen Ebene gekippt.

## <a name="optional-set-blitremoteframetimeout"></a>Optional: Set blitremoteframetimeout <a name="BlitRemoteFrameTimeout"></a>
>[!IMPORTANT]
> ```PlayerContext::BlitRemoteFrameTimeout``` wird ab Version [2.0.9](holographic-remoting-version-history.md#v2.0.9)unterstützt. 

Die- ```PlayerContext::BlitRemoteFrameTimeout``` Eigenschaft gibt die Zeitspanne an, für die ein Remote Rahmen wieder verwendet wird, wenn kein neuer Remote Rahmen empfangen wird. 

Ein gängiger Anwendungsfall besteht darin, das blitremoteframe-Timeout zu aktivieren, um einen leeren Bildschirm anzuzeigen, wenn für einen bestimmten Zeitraum keine neuen Frames empfangen werden. Wenn aktiviert, kann der Rückgabetyp der ```BlitRemoteFrame``` Methode auch verwendet werden, um zu einem lokal gerenderten Fall Back Inhalt zu wechseln. 

Um das Timeout zu aktivieren, legen Sie den-Eigenschafts Wert auf eine Dauer gleich oder größer als 100 MS fest. Um das Timeout zu deaktivieren, legen Sie die-Eigenschaft auf die Dauer NULL fest. Wenn das Timeout aktiviert ist und für die festgelegte Dauer kein Remote Rahmen empfangen wird, schlägt blitremoteframe fehl und wird zurückgegeben, ```Failed_RemoteFrameTooOld``` bis ein neuer Remote Rahmen empfangen wird.

```cpp
using namespace std::chrono_literals;

// Set the BlitRemoteFrame timeout to 0.5s
m_playerContext.BlitRemoteFrameTimeout(500ms);
```

## <a name="optional-get-statistics-about-the-last-remote-frame"></a>Optional: Statistiken zum letzten Remote Rahmen erhalten

Zum Diagnostizieren von Leistungs-oder Netzwerkproblemen können Statistiken über den letzten Remote Rahmen über die- ```PlayerContext::LastFrameStatistics``` Eigenschaft abgerufen werden. Statistiken werden während des Aufrufes [holographicframe aktualisiert::P "Ressentiments usingcurrentvorhersage](//uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction)".

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

Weitere Informationen finden Sie in der- ```PlayerFrameStatistics``` Dokumentation in der- ```Microsoft.Holographic.AppRemoting.idl``` [Datei](#idl).

## <a name="optional-custom-data-channels"></a>Optional: benutzerdefinierte Datenkanäle

Benutzerdefinierte Datenkanäle können zum Senden von Benutzerdaten über die bereits festgelegte Remote Verbindung verwendet werden. Weitere Informationen finden Sie unter [benutzerdefinierte Datenkanäle](holographic-remoting-custom-data-channels.md) .

## <a name="see-also"></a>Weitere Informationen
* [Schreiben einer Holographic Remoting-Remote-app mit Windows Mixed Reality-APIs](holographic-remoting-create-remote-wmr.md)
* [Schreiben einer Holographic Remoting-Remote-App mithilfe von openxr-APIs](holographic-remoting-create-remote-openxr.md)
* [Benutzerdefinierte Holographic Remoting-Datenkanäle](holographic-remoting-custom-data-channels.md)
* [Einrichten einer sicheren Verbindung mit Holographic Remoting](holographic-remoting-secure-connection.md)
* [Problembehandlung und Einschränkungen für Holographic Remoting](holographic-remoting-troubleshooting.md)
* [Holographic Remoting-Software – Lizenzbedingungen](//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Datenschutzerklärung von Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)