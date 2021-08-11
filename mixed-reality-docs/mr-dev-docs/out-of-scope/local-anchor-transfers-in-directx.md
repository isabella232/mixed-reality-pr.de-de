---
title: Lokale Ankerübertragungen in DirectX
description: Erfahren Sie, wie Sie zwei HoloLens synchronisieren, indem Sie Raumanker übertragen, exportieren und serialisieren.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, Synchronisieren, Raumanker, Übertragung, Multiplayer, Ansicht, Szenario, exemplarische Vorgehensweise, Beispielcode, Übertragung, lokale Ankerübertragung, Ankerexport, Ankerimport
ms.openlocfilehash: df00e323267aa398ba45cfd7a7234c04ce8eca85f2ff3be9b6c9ddee67264085
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115195664"
---
# <a name="local-anchor-transfers-in-directx"></a>Lokale Ankerübertragungen in DirectX

In Situationen, in denen Sie <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>nicht verwenden können, ermöglichen lokale Ankerübertragungen einem HoloLens-Gerät, einen Anker zu exportieren, der von einem zweiten Gerät HoloLens wird.

>[!NOTE]
>Lokale Ankerübertragungen bieten weniger stabile Ankerrückrufe als <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, und iOS- und Android-Geräte werden von diesem Ansatz nicht unterstützt.

>[!NOTE]
>Die Codeausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung von C++/CX anstelle von C++17-kompatiblem C++/WinRT, wie in der holografischen C++-Projektvorlage [verwendet.](../develop/native/creating-a-holographic-directx-project.md)  Die Konzepte sind für ein C++/WinRT-Projekt gleichwertig, obwohl Sie den Code übersetzen müssen.

## <a name="transferring-spatial-anchors"></a>Übertragen von Raumankern

Sie können Raumanker zwischen Windows Mixed Reality übertragen, indem Sie [SpatialAnchorTransferManager verwenden.](/uwp/api/Windows.Perception.Spatial.SpatialAnchorTransferManager) Mit dieser API können Sie einen Anker mit allen unterstützenden Sensordaten bündeln, die benötigt werden, um genau diesen Ort auf der Welt zu finden, und dieses Paket dann auf ein anderes Gerät importieren. Nachdem die App auf dem zweiten Gerät diesen Anker importiert hat, kann jede App Hologramme mithilfe des Koordinatensystems dieses gemeinsamen Raumanker rendern, das dann an derselben Stelle in der realen Welt angezeigt wird.

Beachten Sie, dass Raumanker nicht zwischen verschiedenen Gerätetypen übertragen werden können, z. B. kann ein HoloLens raumanker mit einem immersiven Headset möglicherweise nicht verkettet werden.  Übertragene Anker sind auch nicht mit iOS- oder Android-Geräten kompatibel.

## <a name="set-up-your-app-to-use-the-spatialperception-capability"></a>Einrichten Ihrer App für die Verwendung der spatialPerception-Funktion

Ihrer App muss die Berechtigung zum Verwenden der SpatialPerception-Funktion erteilt werden, bevor sie [SpatialAnchorTransferManager verwenden kann.](/uwp/api/Windows.Perception.Spatial.SpatialAnchorTransferManager) Dies ist erforderlich, da die Übertragung eines Raumankers das Freigeben von Sensorbildern umfasst, die im Laufe der Zeit in der Nähe dieses Ankers gesammelt wurden, was vertrauliche Informationen enthalten kann.

Deklarieren Sie diese Funktion in der Datei package.appxmanifest für Ihre App. Ein Beispiel:

```
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

Die Funktion stammt aus dem **uap2-Namespace.** Um Zugriff auf diesen Namespace in Ihrem Manifest zu erhalten, fügen Sie ihn als *xlmns-Attribut* in das &lt; Package> ein. Ein Beispiel:

```
<Package
    xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap mp"
    >
```

**HINWEIS:** Ihre App muss die Funktion zur Laufzeit anfordern, bevor sie auf SpatialAnchor-Export-/Import-APIs zugreifen kann. Siehe [RequestAccessAsync](/uwp/api/Windows.Perception.Spatial.SpatialAnchorTransferManager) in den folgenden Beispielen.

## <a name="serialize-anchor-data-by-exporting-it-with-the-spatialanchortransfermanager"></a>Serialisieren von Ankerdaten durch Exportieren mit SpatialAnchorTransferManager

Eine Hilfsfunktion ist im Codebeispiel enthalten, um [SpatialAnchor-Daten](/uwp/api/Windows.Perception.Spatial.SpatialAnchor) zu exportieren (zu serialisieren). Diese Export-API serialisiert alle Anker in einer Sammlung von Schlüssel-Wert-Paaren, die Zeichenfolgen Ankern zuordnen.

```
// ExportAnchorDataAsync: Exports a byte buffer containing all of the anchors in the given collection.
//
// This function will place data in a buffer using a std::vector<byte>. The ata buffer contains one or more
// Anchors if one or more Anchors were successfully imported; otherwise, it is ot modified.
//
task<bool> SpatialAnchorImportExportHelper::ExportAnchorDataAsync(
    vector<byte>* anchorByteDataOut,
    IMap<String^, SpatialAnchor^>^ anchorsToExport
    )
{
```

Zunächst müssen wir den Datenstrom einrichten. Dies ermöglicht es uns, 1 zu erhalten.) Verwenden Sie TryExportAnchorsAsync, um die Daten in einen Puffer zu setzen, der sich im Besitz der App befindet, und 2.) Liest Daten aus dem exportierten Bytepufferstream ( ein WinRT-Datenstrom) in unseren eigenen Speicherpuffer, bei dem es sich um ein std::vector-Byte->. &lt;

```
// Create a random access stream to process the anchor byte data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor byte stream.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
```

Wir müssen die Berechtigung für den Zugriff auf räumliche Daten erfragen, einschließlich Ankern, die vom System exportiert werden.

```
// Request access to spatial data.
auto accessRequestedTask = create_taskSpatialAnchorTransferManager::RequestAccessAsync()).then([anchorsToExport, utputStream](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
        // Export the indicated set of anchors.
        return create_task(SpatialAnchorTransferManager::TryExportAnchorsAsync(
            anchorsToExport,
            outputStream
            ));
    }
    else
    {
        // Access is denied.
        return task_from_result<bool>(false);
    }
});
```

Wenn wir die Berechtigung erhalten und Anker exportiert werden, können wir den Datenstrom lesen. Hier wird auch gezeigt, wie Sie den DataReader und InputStream erstellen, den wir zum Lesen der Daten verwenden.

```
// Get the input stream for the anchor byte stream.
IInputStream^ inputStream = stream->GetInputStreamAt(0);
// Create a DataReader, to get bytes from the anchor byte stream.
DataReader^ reader = ref new DataReader(inputStream);
return accessRequestedTask.then([anchorByteDataOut, stream, reader](bool nchorsExported)
{
    if (anchorsExported)
    {
        // Get the size of the exported anchor byte stream.
        size_t bufferSize = static_cast<size_t>(stream->Size);
        // Resize the output buffer to accept the data from the stream.
        anchorByteDataOut->reserve(bufferSize);
        anchorByteDataOut->resize(bufferSize);
        // Read the exported anchor store into the stream.
        return create_task(reader->LoadAsync(bufferSize));
    }
    else
    {
        return task_from_result<size_t>(0);
    }
```

Nachdem Wir Bytes aus dem Stream gelesen haben, können wir sie in unserem eigenen Datenpuffer speichern.

```
}).then([anchorByteDataOut, reader](size_t bytesRead)
{
    if (bytesRead > 0)
    {
        // Read the bytes from the stream, into our data output buffer.
        reader->ReadBytes(Platform::ArrayReference<byte>(&(*anchorByteDataOut)[0], bytesRead));
        return true;
    }
    else
    {
        return false;
    }
});
};
```

## <a name="deserialize-anchor-data-by-importing-it-into-the-system-using-the-spatialanchortransfermanager"></a>Deserialisieren von Ankerdaten durch Importieren in das System mit spatialAnchorTransferManager

Eine Hilfsfunktion ist im Codebeispiel enthalten, um zuvor exportierte Daten zu laden. Diese Deserialisierungsfunktion stellt eine Sammlung von Schlüssel-Wert-Paaren zur Verfügung, die dem von SpatialAnchorStore zur Verfügung stellen, mit der Ausnahme, dass wir diese Daten aus einer anderen Quelle, z. B. einem Netzwerksocket, erhalten haben. Sie können diese Daten vor dem Offlinespeichern mithilfe des In-App-Arbeitsspeichers oder (falls zutreffend) des SpatialAnchorStore Ihrer App verarbeiten und eine Begründung dafür erstellen.

```
// ImportAnchorDataAsync: Imports anchors from a byte buffer that was previously exported.
//
// This function will import all anchors from a data buffer into an in-memory ollection of key, value
// pairs that maps String objects to SpatialAnchor objects. The Spatial nchorStore is not affected by
// this function unless you provide it as the target collection for import.
//
task<bool> SpatialAnchorImportExportHelper::ImportAnchorDataAsync(
    std::vector<byte>& anchorByteDataIn,
    IMap<String^, SpatialAnchor^>^ anchorMapOut
    )
{
```

Zunächst müssen Wir Streamobjekte erstellen, um auf die Ankerdaten zu zugreifen. Wir schreiben die Daten aus unserem Puffer in einen Systempuffer. Daher erstellen wir einen DataWriter, der in einen In-Memory-Datenstrom schreibt, um unser Ziel zu erreichen, Anker aus einem Bytepuffer als SpatialAnchors in das System zu übertragen.

```
// Create a random access stream for the anchor data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor data.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
// Create a writer, to put the bytes in the stream.
DataWriter^ writer = ref new DataWriter(outputStream);
```

Auch hier müssen wir sicherstellen, dass die App über die Berechtigung zum Exportieren von Raumankerdaten verfügt, die private Informationen über die Umgebung des Benutzers enthalten können.

```
// Request access to transfer spatial anchors.
return create_task(SpatialAnchorTransferManager::RequestAccessAsync()).then(
    [&anchorByteDataIn, writer](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
```

Wenn der Zugriff zulässig ist, können Wir Bytes aus dem Puffer in einen Systemdatenstrom schreiben.

```
// Write the bytes to the stream.
        byte* anchorDataFirst = &anchorByteDataIn[0];
        size_t anchorDataSize = anchorByteDataIn.size();
        writer->WriteBytes(Platform::ArrayReference<byte>(anchorDataFirst, anchorDataSize));
        // Store the stream.
        return create_task(writer->StoreAsync());
    }
    else
    {
        // Access is denied.
        return task_from_result<size_t>(0);
    }
```

Wenn das Speichern von Bytes im Datenstrom erfolgreich war, können wir versuchen, diese Daten mit spatialAnchorTransferManager zu importieren.

```
}).then([writer, stream](unsigned int bytesWritten)
{
    if (bytesWritten > 0)
    {
        // Try to import anchors from the byte stream.
        return create_task(writer->FlushAsync())
            .then([stream](bool dataWasFlushed)
        {
            if (dataWasFlushed)
            {
                // Get the input stream for the anchor data.
                IInputStream^ inputStream = stream->GetInputStreamAt(0);
                return create_task(SpatialAnchorTransferManager::TryImportAnchorsAsync(inputStream));
            }
            else
            {
                return task_from_result<IMapView<String^, SpatialAnchor^>^>(nullptr);
            }
        });
    }
    else
    {
        return task_from_result<IMapView<String^, SpatialAnchor^>^>(nullptr);
    }
```

Wenn die Daten importiert werden können, erhalten wir eine Kartenansicht von Schlüssel-Wert-Paaren, die Zeichenfolgen Ankern zuordnen. Wir können dies in unsere eigene In-Memory-Datensammlung laden und diese Sammlung verwenden, um nach Ankern zu suchen, die wir verwenden möchten.

```
}).then([anchorMapOut](task<Windows::Foundation::Collections::IMapView<String^, SpatialAnchor^>^>  previousTask)
{
    try
    {
        auto importedAnchorsMap = previousTask.get();
        // If the operation was successful, we get a set of imported anchors.
        if (importedAnchorsMap != nullptr)
        {
            for each (auto& pair in importedAnchorsMap)
            {
                // Note that you could look for specific anchors here, if you know their key values.
                auto const& id = pair->Key;
                auto const& anchor = pair->Value;
                // Append "Remote" to the end of the anchor name for disambiguation.
                std::wstring idRemote(id->Data());
                idRemote += L"Remote";
                String^ idRemoteConst = ref new String (idRemote.c_str());
                // Store the anchor in the current in-memory anchor map.
                anchorMapOut->Insert(idRemoteConst, anchor);
            }
            return true;
        }
    }
    catch (Exception^ exception)
    {
        OutputDebugString(L"Error: Unable to import the anchor data buffer bytes into the in-memory anchor collection.\n");
    }
    return false;
});
}
```

**HINWEIS:** Nur weil Sie einen Anker importieren können, bedeutet dies nicht unbedingt, dass Sie ihn sofort verwenden können. Der Anker kann sich in einem anderen Raum oder an einem anderen physischen Ort befinden. Der Anker ist erst wieder verwendbar, wenn das empfangene Gerät über genügend visuelle Informationen über die Umgebung verfügt, in der der Anker erstellt wurde, um die Position des Ankers relativ zur bekannten aktuellen Umgebung wiederherzustellen. Die Clientimplementierung sollte versuchen, den Anker relativ zu Ihrem lokalen Koordinatensystem oder Referenzframe zu suchen, bevor sie weiter versucht, ihn für Liveinhalte zu verwenden. Versuchen Sie beispielsweise, den Anker relativ zu einem aktuellen Koordinatensystem in regelmäßigen Abständen zu finden, bis der Anker zu verfügbar wird.

## <a name="special-considerations"></a>Besondere Überlegungen

Mit [der TryExportAnchorsAsync-API](/uwp/api/Windows.Perception.Spatial.SpatialAnchorTransferManager) können mehrere [SpatialAnchors](/uwp/api/Windows.Perception.Spatial.SpatialAnchor) in dasselbe nicht transparente binäre Blob exportiert werden. Es gibt jedoch einen feinen Unterschied in den Daten, die das Blob enthält, je nachdem, ob ein einzelner SpatialAnchor oder mehrere SpatialAnchors in einem einzigen Aufruf exportiert werden.

### <a name="export-of-a-single-spatialanchor"></a>Exportieren eines einzelnen SpatialAnchor

Das Blob enthält eine Darstellung der Umgebung in der Nähe des SpatialAnchor, sodass die Umgebung auf dem Gerät erkannt werden kann, das SpatialAnchor importiert. Nach Abschluss des Imports ist der neue SpatialAnchor für das Gerät verfügbar. Wenn sich der Benutzer vor Kurzem in der Nähe des Ankers befindet, ist er verwendbar, und hologramme, die an spatialAnchor angefügt sind, können gerendert werden. Diese Hologramme werden an derselben physischen Position angezeigt wie auf dem ursprünglichen Gerät, das spatialAnchor exportiert hat.

![Exportieren eines einzelnen SpatialAnchor](images/singleanchor.png)

### <a name="export-of-multiple-spatialanchors"></a>Export mehrerer SpatialAnchors

Wie beim Export eines einzelnen SpatialAnchor enthält das Blob eine Darstellung der Umgebung in der Nähe aller angegebenen SpatialAnchors. Darüber hinaus enthält das Blob Informationen zu den Verbindungen zwischen den enthaltenen SpatialAnchors, wenn sie sich im gleichen physischen Raum befinden. Dies bedeutet, dass ein Hologramm, das an den zweiten *SpatialAnchor* angefügt ist, beim Importieren von zwei spatialanchors in der Nähe auch dann nicht mehr zu finden ist, wenn das Gerät nur die Umgebung um den ersten *SpatialAnchor* erkennt, da genügend Daten zum Berechnen der Transformation zwischen den beiden SpatialAnchors im Blob enthalten waren. Wenn die beiden SpatialAnchors einzeln exportiert wurden (zwei separate Aufrufe von TryExportSpatialAnchors), sind möglicherweise nicht genügend Daten im Blob enthalten, damit Hologramme, die an den zweiten SpatialAnchor angefügt sind, beim ersten gefunden werden können.

![Mehrere Anker, die mit einem einzigen TryExportAnchorsAsync-Aufruf exportiert wurden](images/multipleanchors.png) ![Mehrere Anker, die mit einem separaten TryExportAnchorsAsync-Aufruf für jeden Anker exportiert wurden](images/separateanchors.png)

## <a name="example-send-anchor-data-using-a-windowsnetworkingstreamsocket"></a>Beispiel: Senden von Ankerdaten mithilfe Windows::Networking::StreamSocket

Hier finden Sie ein Beispiel für die Verwendung exportierter Ankerdaten, indem sie über ein TCP-Netzwerk gesendet werden. Dies ist aus dem HolographicSpatialAnchorTransferSample.

Die WinRT StreamSocket-Klasse verwendet die PPL-Aufgabenbibliothek. Bei Netzwerkfehlern wird der Fehler mithilfe einer erneut ausgelösten Ausnahme an die nächste Aufgabe in der Kette zurückgegeben. Die Ausnahme enthält ein HRESULT, das den Fehlerstatus angibt.

### <a name="use-a-windowsnetworkingstreamsocketlistener-with-tcp-to-send-exported-anchor-data"></a>Verwenden eines Windows::Networking::StreamSocketListener mit TCP zum Senden exportierter Ankerdaten

Erstellen Sie eine Serverinstanz, die auf eine Verbindung lausiert.

```
void SampleAnchorTcpServer::ListenForConnection()
{
    // Make a local copy to avoid races with Closed events.
    StreamSocketListener^ streamSocketListener = m_socketServer;
    if (streamSocketListener == nullptr)
    {
        OutputDebugString(L"Server listening for client.\n");
        // Create the web socket connection.
        streamSocketListener = ref new StreamSocketListener();
        streamSocketListener->Control->KeepAlive = true;
        streamSocketListener->BindEndpointAsync(
            SampleAnchorTcpCommon::m_serverHost,
            SampleAnchorTcpCommon::m_tcpPort
            );
        streamSocketListener->ConnectionReceived +=
            ref new Windows::Foundation::TypedEventHandler<StreamSocketListener^, StreamSocketListenerConnectionReceivedEventArgs^>(
                std::bind(&SampleAnchorTcpServer::OnConnectionReceived, this, _1, _2)
                );
        m_socketServer = streamSocketListener;
    }
    else
    {
        OutputDebugString(L"Error: Stream socket listener not created.\n");
    }
}
```

Wenn eine Verbindung empfangen wird, verwenden Sie die Clientsocketverbindung, um Ankerdaten zu senden.

```
void SampleAnchorTcpServer::OnConnectionReceived(StreamSocketListener^ listener, StreamSocketListenerConnectionReceivedEventArgs^ args)
{
    m_socketForClient = args->Socket;
    if (m_socketForClient != nullptr)
    {
        // In this example, when the client first connects, we catch it up to the current state of our anchor set.
        OutputToClientSocket(m_spatialAnchorHelper->GetAnchorMap());
    }
}
```

Nun können wir mit dem Senden eines Datenstroms beginnen, der die exportierten Ankerdaten enthält.

```
void SampleAnchorTcpServer::OutputToClientSocket(IMap<String^, SpatialAnchor^>^ anchorsToSend)
{
    m_anchorTcpSocketStreamWriter = ref new DataWriter(m_socketForClient->OutputStream);
    OutputDebugString(L"Sending stream to client.\n");
    SendAnchorDataStream(anchorsToSend).then([this](task<bool> previousTask)
    {
        try
        {
            bool success = previousTask.get();
            if (success)
            {
                OutputDebugString(L"Anchor data sent!\n");
            }
            else
            {
                OutputDebugString(L"Error: Anchor data not sent.\n");
            }
        }
        catch (Exception^ exception)
        {
            HandleException(exception);
            OutputDebugString(L"Error: Anchor data was not sent.\n");
        }
    });
}
```

Bevor wir den Stream selbst senden können, müssen wir zuerst ein Headerpaket senden. Dieses Headerpaket muss eine feste Länge haben und auch die Länge des Variablenarrays von Bytes angeben, das der Ankerdatenstrom ist. Im Fall dieses Beispiels müssen keine anderen Headerdaten gesendet werden, sodass unser Header 4 Bytes lang ist und eine 32-Bit-Ganzzahl ohne Vorzeichen enthält.

```
Concurrency::task<bool> SampleAnchorTcpServer::SendAnchorDataLengthMessage(size_t dataStreamLength)
{
    unsigned int arrayLength = dataStreamLength;
    byte* data = reinterpret_cast<byte*>(&arrayLength);
    m_anchorTcpSocketStreamWriter->WriteBytes(Platform::ArrayReference<byte>(data, SampleAnchorTcpCommon::c_streamHeaderByteArrayLength));
    return create_task(m_anchorTcpSocketStreamWriter->StoreAsync()).then([this](unsigned int bytesStored)
    {
        if (bytesStored > 0)
        {
            OutputDebugString(L"Anchor data length stored in stream; Flushing stream.\n");
            return create_task(m_anchorTcpSocketStreamWriter->FlushAsync());
        }
        else
        {
            OutputDebugString(L"Error: Anchor data length not stored in stream.\n");
            return task_from_result<bool>(false);
        }
    });
}
Concurrency::task<bool> SampleAnchorTcpServer::SendAnchorDataStreamIMap<String^, SpatialAnchor^>^ anchorsToSend)
{
    return SpatialAnchorImportExportHelper::ExportAnchorDataAsync(
        &m_exportedAnchorStoreBytes,
        anchorsToSend
        ).then([this](bool anchorDataExported)
    {
        if (anchorDataExported)
        {
            const size_t arrayLength = m_exportedAnchorStoreBytes.size();
            if (arrayLength > 0)
            {
                OutputDebugString(L"Anchor data was exported; sending data stream length message.\n");
                return SendAnchorDataLengthMessage(arrayLength);
            }
        }
        OutputDebugString(L"Error: Anchor data was not exported.\n");
        // No data to send.
        return task_from_result<bool>(false);
```

Nachdem die Streamlänge in Bytes an den Client gesendet wurde, können wir mit dem Schreiben des Datenstroms selbst in den Socketstream fortfahren. Dadurch werden die Bytes des Ankerspeichers an den Client gesendet.

```
}).then([this](bool dataLengthSent)
    {
        if (dataLengthSent)
        {
            OutputDebugString(L"Data stream length message sent; writing exported anchor store bytes to stream.\n");
            m_anchorTcpSocketStreamWriter->WriteBytes(Platform::ArrayReference<byte>(&m_exportedAnchorStoreBytes[0], m_exportedAnchorStoreBytes.size()));
            return create_task(m_anchorTcpSocketStreamWriter->StoreAsync());
        }
        else
        {
            OutputDebugString(L"Error: Data stream length message not sent.\n");
            return task_from_result<size_t>(0);
        }
    }).then([this](unsigned int bytesStored)
    {
        if (bytesStored > 0)
        {
            PrintWstringToDebugConsole(
                std::to_wstring(bytesStored) +
                L" bytes of anchor data written and stored to stream; flushing stream.\n"
                );
        }
        else
        {
            OutputDebugString(L"Error: No anchor data bytes were written to the stream.\n");
        }
        return task_from_result<bool>(false);
    });
}
```

Wie weiter oben in diesem Thema erwähnt, müssen wir darauf vorbereitet sein, Ausnahmen zu behandeln, die Netzwerkfehlerstatusmeldungen enthalten. Bei Fehlern, die nicht erwartet werden, können wir die Ausnahmeinformationen in die Debugkonsole schreiben. Dies gibt uns einen Hinweis darauf, was passiert ist, wenn unser Codebeispiel die Verbindung nicht abschließen kann oder das Senden der Ankerdaten nicht abgeschlossen werden kann.

```
void SampleAnchorTcpServer::HandleException(Exception^ exception)
{
    PrintWstringToDebugConsole(
        std::wstring(L"Connection error: ") +
        exception->ToString()->Data() +
        L"\n"
        );
}
```

### <a name="use-a-windowsnetworkingstreamsocket-with-tcp-to-receive-exported-anchor-data"></a>Verwenden eines Windows::Networking::StreamSocket mit TCP zum Empfangen exportierter Ankerdaten

Zunächst müssen wir eine Verbindung mit dem Server herstellen. In diesem Codebeispiel wird gezeigt, wie Sie ein StreamSocket erstellen und konfigurieren und einen DataReader erstellen, mit dem Sie Netzwerkdaten über die Socketverbindung erhalten können.

**HINWEIS:** Wenn Sie diesen Beispielcode ausführen, stellen Sie sicher, dass Sie den Server konfigurieren und starten, bevor Sie den Client starten.

```
task<bool> SampleAnchorTcpClient::ConnectToServer()
{
    // Make a local copy to avoid races with Closed events.
    StreamSocket^ streamSocket = m_socketClient;
    // Have we connected yet?
    if (m_socketClient == nullptr)
    {
        OutputDebugString(L"Client is attempting to connect to server.\n");
        EndpointPair^ endpointPair = ref new EndpointPair(
            SampleAnchorTcpCommon::m_clientHost,
            SampleAnchorTcpCommon::m_tcpPort,
            SampleAnchorTcpCommon::m_serverHost,
            SampleAnchorTcpCommon::m_tcpPort
            );
        // Create the web socket connection.
        m_socketClient = ref new StreamSocket();
        // The client connects to the server.
        return create_task(m_socketClient->ConnectAsync(endpointPair, SocketProtectionLevel::PlainSocket)).then([this](task<void> previousTask)
        {
            try
            {
                // Try getting all exceptions from the continuation chain above this point.
                previousTask.get();
                m_anchorTcpSocketStreamReader = ref new DataReader(m_socketClient->InputStream);
                OutputDebugString(L"Client connected!\n");
                m_anchorTcpSocketStreamReader->InputStreamOptions = InputStreamOptions::ReadAhead;
                WaitForAnchorDataStream();
                return true;
            }
            catch (Exception^ exception)
            {
                if (exception->HResult == 0x80072741)
                {
                    // This code sample includes a very simple implementation of client/server
                    // endpoint detection: if the current instance tries to connect to itself,
                    // it is determined to be the server.
                    OutputDebugString(L"Starting up the server instance.\n");
                    // When we return false, we'll start up the server instead.
                    return false;
                }
                else if ((exception->HResult == 0x8007274c) || // connection timed out
                    (exception->HResult == 0x80072740)) // connection maxed at server end
                {
                    // If the connection timed out, try again.
                    ConnectToServer();
                }
                else if (exception->HResult == 0x80072741)
                {
                    // No connection is possible.
                }
                HandleException(exception);
                return true;
            }
        });
    }
    else
    {
        OutputDebugString(L"A StreamSocket connection to a server already exists.\n");
        return task_from_result<bool>(true);
    }
}
```

Sobald eine Verbindung besteht, können wir warten, bis der Server Daten sendet. Rufen Sie hierzu LoadAsync für den Streamdatenreader auf.

Die erste Menge von Bytes, die wir empfangen, sollte immer das Headerpaket sein, das die Bytelänge des Ankerdatenstroms angibt, wie im vorherigen Abschnitt beschrieben.

```
void SampleAnchorTcpClient::WaitForAnchorDataStream()
{
    if (m_anchorTcpSocketStreamReader == nullptr)
    {
        // We have not connected yet.
        return;
    }
    OutputDebugString(L"Waiting for server message.\n");
    // Wait for the first message, which specifies the byte length of the string data.
    create_task(m_anchorTcpSocketStreamReader->LoadAsync(SampleAnchorTcpCommon::c_streamHeaderByteArrayLength)).then([this](unsigned int numberOfBytes)
    {
        if (numberOfBytes > 0)
        {
            OutputDebugString(L"Server message incoming.\n");
            return ReceiveAnchorDataLengthMessage();
        }
        else
        {
            OutputDebugString(L"0-byte async task received, awaiting server message again.\n");
            WaitForAnchorDataStream();
            return task_from_result<size_t>(0);
        }
```

...

```
task<size_t> SampleAnchorTcpClient::ReceiveAnchorDataLengthMessage()
{
    byte data[4];
    m_anchorTcpSocketStreamReader->ReadBytes(Platform::ArrayReference<byte>(data, SampleAnchorTcpCommon::c_streamHeaderByteArrayLength));
    unsigned int lengthMessageSize = *reinterpret_cast<unsigned int*>(data);
    if (lengthMessageSize > 0)
    {
        OutputDebugString(L"One or more anchors to be received.\n");
        return task_from_result<size_t>(lengthMessageSize);
    }
    else
    {
        OutputDebugString(L"No anchors to be received.\n");
        ConnectToServer();
    }
    return task_from_result<size_t>(0);
}
```

Nachdem wir das Headerpaket erhalten haben, wissen wir, wie viele Bytes an Ankerdaten erwartet werden sollten. Wir können mit dem Lesen dieser Bytes aus dem Stream fortfahren.

```
}).then([this](size_t dataStreamLength)
    {
        if (dataStreamLength > 0)
        {
            std::wstring debugMessage = std::to_wstring(dataStreamLength);
            debugMessage += L" bytes of anchor data incoming.\n";
            OutputDebugString(debugMessage.c_str());
            // Prepare to receive the data stream in one or more pieces.
            m_anchorStreamLength = dataStreamLength;
            m_exportedAnchorStoreBytes.clear();
            m_exportedAnchorStoreBytes.resize(m_anchorStreamLength);
            OutputDebugString(L"Loading byte stream.\n");
            return ReceiveAnchorDataStream();
        }
        else
        {
            OutputDebugString(L"Error: Anchor data size not received.\n");
            ConnectToServer();
            return task_from_result<bool>(false);
        }
    });
}
```

Hier ist unser Code zum Empfangen des Ankerdatenstroms. Auch hier laden wir zuerst die Bytes aus dem Stream. Dieser Vorgang kann einige Zeit dauern, da StreamSocket darauf wartet, diese Bytemenge aus dem Netzwerk zu empfangen.

Wenn der Ladevorgang abgeschlossen ist, können wir diese Anzahl von Bytes lesen. Wenn wir die Anzahl der Bytes erhalten haben, die wir für den Ankerdatenstrom erwarten, können wir die Ankerdaten importieren. Wenn dies nicht der Fehler ist, muss ein Fehler aufgetreten sein. Dies kann beispielsweise passieren, wenn die Serverinstanz beendet wird, bevor sie das Senden des Datenstroms beenden kann, oder wenn das Netzwerk ausläuft, bevor der gesamte Datenstrom vom Client empfangen werden kann.

```
task<bool> SampleAnchorTcpClient::ReceiveAnchorDataStream()
{
    if (m_anchorStreamLength > 0)
    {
        // First, we load the bytes from the network socket.
        return create_task(m_anchorTcpSocketStreamReader->LoadAsync(m_anchorStreamLength)).then([this](size_t bytesLoadedByStreamReader)
        {
            if (bytesLoadedByStreamReader > 0)
            {
                // Once the bytes are loaded, we can read them from the stream.
                m_anchorTcpSocketStreamReader->ReadBytes(Platform::ArrayReference<byte>(&m_exportedAnchorStoreBytes[0],
                    bytesLoadedByStreamReader));
                // Check status.
                if (bytesLoadedByStreamReader == m_anchorStreamLength)
                {
                    // The whole stream has arrived. We can process the data.
                    // Informational message of progress complete.
                    std::wstring infoMessage = std::to_wstring(bytesLoadedByStreamReader);
                    infoMessage += L" bytes read out of ";
                    infoMessage += std::to_wstring(m_anchorStreamLength);
                    infoMessage += L" total bytes; importing the data.\n";
                    OutputDebugStringW(infoMessage.c_str());
                    // Kick off a thread to wait for a new message indicating another incoming anchor data stream.
                    WaitForAnchorDataStream();
                    // Process the data for the stream we just received.
                    return SpatialAnchorImportExportHelper::ImportAnchorDataAsync(m_exportedAnchorStoreBytes, m_spatialAnchorHelper->GetAnchorMap());
                }
                else
                {
                    OutputDebugString(L"Error: Fewer than expected anchor data bytes were received.\n");
                }
            }
            else
            {
                OutputDebugString(L"Error: No anchor bytes were received.\n");
            }
            return task_from_result<bool>(false);
        });
    }
    else
    {
        OutputDebugString(L"Warning: A zero-length data buffer was sent.\n");
        return task_from_result<bool>(false);
    }
}
```

Auch hier müssen wir darauf vorbereitet sein, unbekannte Netzwerkfehler zu behandeln.

```
void SampleAnchorTcpClient::HandleException(Exception^ exception)
{
    std::wstring error = L"Connection error: ";
    error += exception->ToString()->Data();
    error += L"\n";
    OutputDebugString(error.c_str());
}
```

Das ist alles! Nun sollten Sie über genügend Informationen verfügen, um zu versuchen, die über das Netzwerk empfangenen Anker zu finden. Beachten Sie auch hier, dass der Client über genügend visuelle Nachverfolgungsdaten verfügen muss, damit der Raum den Anker erfolgreich finden kann. Wenn es nicht sofort funktioniert, versuchen Sie, eine Weile zu laufen. Wenn dies immer noch nicht funktioniert, müssen Sie vom Server weitere Anker senden und die Netzwerkkommunikation verwenden, um sich auf einen für den Client zu einigen. Sie können dies ausprobieren, indem Sie HolographicSpatialAnchorTransferSample herunterladen, Ihre Client- und Server-IP-Dateien konfigurieren und auf Client- und Servergeräten HoloLens bereitstellen.

## <a name="see-also"></a>Siehe auch
* [Parallel Patterns Library (PPL)](/cpp/parallel/concrt/parallel-patterns-library-ppl)
* [Windows. Networking.StreamSocket](/uwp/api/Windows.Networking.Sockets.StreamSocket)
* [Windows. Networking.StreamSocketListener](/uwp/api/Windows.Networking.Sockets.StreamSocketListener)