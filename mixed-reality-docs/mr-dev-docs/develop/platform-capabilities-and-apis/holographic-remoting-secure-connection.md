---
title: Aktivieren der Verbindungssicherheit für Holographic Remoting
description: Auf dieser Seite wird erläutert, wie Holographic Remoting für die Verwendung verschlüsselter und authentifizierter Verbindungen zwischen Player- und Remote-Apps konfiguriert wird.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, Remoting, Holographic Remoting, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Sicherheit, Authentifizierung, Server-zu-Client
ms.openlocfilehash: fa23994ff4ab49d313fe24a67974bf4d90454e511658e0663c61d7b129b10f9e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223580"
---
# <a name="enabling-connection-security-for-holographic-remoting"></a>Aktivieren der Verbindungssicherheit für Holographic Remoting

>[!IMPORTANT]
>Dieser Leitfaden gilt speziell für Holographic Remoting auf HoloLens 2.

Auf dieser Seite erhalten Sie eine Übersicht über die Netzwerksicherheit für Holographic Remoting. Hier finden Sie Informationen zu

* Sicherheit im Kontext von Holographic Remoting und warum Sie es möglicherweise benötigen
* Empfohlene Maßnahmen basierend auf verschiedenen Anwendungsfällen
* Implementieren von Sicherheit in Ihrer Holographic Remoting-Lösung

## <a name="holographic-remoting-security"></a>Holographic Remoting-Sicherheit

Holographic Remoting tauscht Informationen über ein Netzwerk aus. Wenn keine Sicherheitsmaßnahmen vorhanden sind, können Dies die Integrität der Kommunikation beeinträchtigen oder auf vertrauliche Informationen zugreifen.

Die Beispiel-Apps und der Holographic Remoting Player im Windows Store mit deaktivierter Sicherheit. Dies erleichtert das Verständnis der Beispiele. Außerdem können Sie schneller mit der Entwicklung beginnen.

Für Feldtests oder Die Produktion wird dringend empfohlen, die Sicherheit in Ihrer Holographic Remoting-Lösung zu aktivieren.

Die Sicherheit in Holographic Remoting bietet Ihnen bei ordnungsgemäßer Einrichtung für Ihren Anwendungsfall die folgenden Garantien:

* **Authentizität:** Sowohl die Player- als auch die Remote-App können sicher sein, dass die andere Seite die ist, die sie als
* **Vertraulichkeit:** Kein Drittanbieter kann die Informationen lesen, die zwischen Player und Remote-App ausgetauscht werden.
* **Integrität:** Player und Remote können änderungen an der Kommunikation während der Übertragung erkennen.

>[!IMPORTANT]
>Um Sicherheitsfeatures verwenden zu können, müssen Sie sowohl einen [benutzerdefinierten Player](holographic-remoting-create-player.md) als auch eine benutzerdefinierte Remote-App [mithilfe von Windows Mixed Reality](holographic-remoting-create-remote-wmr.md) oder [OpenXR-APIs](holographic-remoting-create-remote-openxr.md) implementieren.

>[!NOTE]
> Ab Version [2.4.0](holographic-remoting-version-history.md#v2.4.0) können Remote-Apps mit der [OpenXR-API](../native/openxr.md) erstellt werden. Eine Übersicht über das Herstellen einer sicheren Verbindung in einer OpenXR-Umgebung finden Sie [unter](#secure-connection-using-the-openxr-api).

## <a name="planning-the-security-implementation"></a>Planen der Sicherheitsimplementierung

Wenn Sie die Sicherheit in Holographic Remoting aktivieren, aktiviert die Remotingbibliothek automatisch Verschlüsselungs- und Integritätsprüfungen für alle Daten, die über das Netzwerk ausgetauscht werden.

Die Sicherstellung einer ordnungsgemäßen Authentifizierung erfordert jedoch zusätzlichen Aufwand. Was Genau Sie tun müssen, hängt von Ihrem Anwendungsfall ab, und im restlichen Teil dieses Abschnitts geht es darum, die erforderlichen Schritte zu finden.

>[!IMPORTANT]
> Dieser Artikel kann nur allgemeine Anleitungen enthalten. Wenn Sie unsicher sind, ziehen Sie in Betracht, einen Sicherheitsexperten zu konsultieren, der Ihnen spezifische Anleitungen für Ihren Anwendungsfall geben kann.

Zunächst einige Terminologie: Bei der Beschreibung von Netzwerkverbindungen werden die Begriffe _Client_ und _Server_ verwendet. Der Server ist die Seite, die auf eingehende Verbindungen an einer bekannten Endpunktadresse lauscht, und der Client ist der Client, der eine Verbindung mit dem Endpunkt des Servers herstellt.

>[!NOTE]
> Die Client- und Serverrollen sind nicht daran gebunden, ob eine App als Player oder remote fungiert. Während die Beispiele den Player in der Serverrolle haben, ist es einfach, die Rollen umzukehren, wenn sie besser zu Ihrem Anwendungsfall passen.

### <a name="planning-the-server-to-client-authentication"></a>Planen der Server-zu-Client-Authentifizierung

Der Server verwendet digitale Zertifikate, um seine Identität gegenüber dem Client nachzuweisen. Der Client überprüft das Serverzertifikat während der Verbindungshandshakephase. Wenn der Client dem Server nicht vertraut, wird die Verbindung zu diesem Zeitpunkt beendet.

Wie der Client das Serverzertifikat überprüft und welche Arten von Serverzertifikaten verwendet werden können, hängt von Ihrem Anwendungsfall ab.

**Anwendungsfall 1:** Der Serverhostname ist nicht festgelegt, oder der Server wird überhaupt nicht anhand des Hostnamens adressiert.

In diesem Anwendungsfall ist es nicht praktikabel (oder sogar möglich), ein Zertifikat für den Hostnamen des Servers auszustellen. Es wird empfohlen, stattdessen den Fingerabdruck des Zertifikats zu überprüfen. Wie ein menschlicher Fingerabdruck identifiziert der Fingerabdruck ein Zertifikat eindeutig.

Es ist wichtig, den Fingerabdruck out-of-band an den Client zu übermitteln. Das bedeutet, dass Sie sie nicht über dieselbe Netzwerkverbindung senden können, die für Remoting verwendet wird. Stattdessen können Sie ihn manuell in die Clientkonfiguration eingeben oder den QR-Code vom Client scannen lassen.

**Anwendungsfall 2:** Der Server kann über einen stabilen Hostnamen erreicht werden.

In diesem Anwendungsfall hat der Server einen bestimmten Hostnamen, und Sie wissen, dass sich dieser Name wahrscheinlich nicht ändern wird. Anschließend können Sie ein Zertifikat verwenden, das für den Hostnamen des Servers ausgestellt wurde. Die Vertrauensstellung wird basierend auf dem Hostnamen und der Vertrauenskette des Zertifikats eingerichtet.

Wenn Sie diese Option auswählen, muss der Client den Hostnamen des Servers und das Stammzertifikat im Voraus kennen.

### <a name="planning-the-client-to-server-authentication"></a>Planen der Client-zu-Server-Authentifizierung

Clients authentifizieren sich mithilfe eines Freiformtokens beim Server. Was dieses Token enthalten sollte, hängt wieder von Ihrem Anwendungsfall ab:

**Anwendungsfall 1:** Sie müssen nur die Identität der Client-App überprüfen.

In diesem Anwendungsfall kann ein gemeinsames Geheimnis ausreichen. Dieses Geheimnis muss so komplex sein, dass es nicht erraten werden kann.

Ein gutes gemeinsames Geheimnis ist eine zufällige GUID, die sowohl in der Konfiguration des Servers als auch des Clients manuell eingegeben wird. Sie können z. B. den Befehl in PowerShell verwenden, um einen zu `New-Guid` erstellen.

Stellen Sie sicher, dass dieses gemeinsame Geheimnis nie über unsichere Kanäle kommuniziert wird. Die Remotingbibliothek stellt sicher, dass das gemeinsame Geheimnis immer verschlüsselt und nur an vertrauenswürdige Peers gesendet wird.

**Anwendungsfall 2:** Sie müssen auch die Identität des Benutzers der Client-App überprüfen.

Ein gemeinsames Geheimnis reicht nicht aus, um diesen Anwendungsfall abzudecken. Stattdessen können Sie Token verwenden, die von einem Identitätsanbieter erstellt wurden. Ein Authentifizierungsworkflow mit einem Identitätsanbieter würde wie folgt aussehen:

* Der Client autorisiert für den Identitätsanbieter und fordert ein Token an.
* Der Identitätsanbieter generiert ein Token und sendet es an den Client.
* Der Client sendet dieses Token über Holographic Remoting an den Server.
* Der Server überprüft das Clienttoken anhand des Identitätsanbieters.

Ein Beispiel für einen Identitätsanbieter ist die [Microsoft Identity Platform](/azure/active-directory/develop/).

Stellen Sie wie im vorherigen Anwendungsfall sicher, dass diese Token nicht über unsichere Kanäle gesendet oder anderweitig verfügbar gemacht werden.

## <a name="implementing-holographic-remoting-security"></a>Implementieren von Holographic Remoting-Sicherheit

Denken Sie daran, dass Sie benutzerdefinierte Remote- und Player-Apps implementieren müssen, wenn Sie die Verbindungssicherheit aktivieren möchten. Sie können die bereitgestellten Beispiele als Ausgangspunkte für Ihre eigenen Apps verwenden.

Rufen Sie zum Aktivieren der Sicherheit `ListenSecure()` anstelle von und anstelle von `Listen()` `ConnectSecure()` `Connect()` auf, um die Remotingverbindung herzustellen.

Für diese Aufrufe müssen Sie Implementierungen bestimmter Schnittstellen bereitstellen, um sicherheitsrelevante Informationen bereitzustellen und zu überprüfen:

* Der Server muss einen Zertifikatanbieter und ein Authentifizierungsüberprüfungs-Validierungszeichen implementieren.
* Der Client muss einen Authentifizierungsanbieter und ein Zertifikatsüberprüfungszeichen implementieren.

Alle Schnittstellen verfügen über eine Funktion, die Sie auffordert, Maßnahmen zu ergreifen, die ein Rückrufobjekt als Parameter empfängt. Mit diesem Objekt können Sie problemlos eine asynchrone Verarbeitung der Anforderung implementieren. Behalten Sie einen Verweis auf dieses Objekt bei, und rufen Sie die Vervollständigungsfunktion auf, wenn die asynchrone Aktion abgeschlossen ist. Die Vervollständigungsfunktion kann von einem beliebigen Thread aufgerufen werden.

>[!TIP]
>Die Implementierung von WinRT-Schnittstellen kann problemlos mit C++/WinRT erfolgen. Dies wird im Kapitel Erstellen von [APIs mit C++/WinRT](/windows/uwp/cpp-and-winrt-apis/author-apis) ausführlich beschrieben.

>[!IMPORTANT]
>Die `build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl` im NuGet Paket enthält eine ausführliche Dokumentation für die API im Zusammenhang mit sicheren Verbindungen.

### <a name="implementing-a-certificate-provider"></a>Implementieren eines Zertifikatanbieters

Zertifikatanbieter stellen der Serveranwendung das zu verwendende Zertifikat bereit. Die Implementierung besteht aus zwei Teilen:

1) Ein Zertifikatobjekt, das die `ICertificate` -Schnittstelle implementiert:

    * `GetCertificatePfx()` sollte den binären Inhalt eines `PKCS#12` Zertifikatspeichers zurückgeben. Eine `.pfx` Datei enthält `PKCS#12` Daten, sodass ihr Inhalt direkt hier verwendet werden kann.
    * `GetSubjectName()` sollte den Anzeigenamen zurückgeben, der das zu verwendende Zertifikat identifiziert. Wenn dem Zertifikat kein Anzeigename zugewiesen ist, sollte diese Funktion den Antragstellernamen des Zertifikats zurückgeben.
    * `GetPfxPassword()` sollte das Kennwort zurückgeben, das zum Öffnen des Zertifikatspeichers erforderlich ist (oder eine leere Zeichenfolge, wenn kein Kennwort erforderlich ist).

2) Ein Zertifikatanbieter, der die `ICertificateProvider` Schnittstelle implementiert:
    * `GetCertificate()` sollte ein Zertifikatobjekt erstellen und zurückgeben, indem für das Rückrufobjekt aufgerufen `CertificateReceived()` wird.

### <a name="implementing-an-authentication-validator"></a>Implementieren eines Validierungsüberprüfungszeichens für die Authentifizierung

Authentifizierungsvalidierungen empfangen das vom Client gesendete Authentifizierungstoken und antworten mit dem Validierungsergebnis.

Implementieren Sie die `IAuthenticationReceiver` -Schnittstelle wie folgt:

* `GetRealm()` sollte den Namen des Authentifizierungsbereichs zurückgeben (ein HTTP-Bereich, der während des Remotingverbindungshandshakes verwendet wird).
* `ValidateToken()` sollte das Clientauthentifizierungstoken überprüfen und für `ValidationCompleted()` das Rückrufobjekt mit dem Überprüfungsergebnis aufrufen.

### <a name="implementing-an-authentication-provider"></a>Implementieren eines Authentifizierungsanbieters

Authentifizierungsanbieter generieren oder rufen das Authentifizierungstoken ab, das an den Server gesendet werden soll.

Implementieren Sie `IAuthenticationProvider` die -Schnittstelle wie folgt:

* `GetToken()` sollte das zu gesendete Authentifizierungstoken generieren oder abrufen. Sobald das Token bereit ist, rufen Sie die `TokenReceived()` -Methode für das Rückrufobjekt auf.

### <a name="implementing-a-certificate-validator"></a>Implementieren eines Zertifikats-Validierungszertifikats

Zertifikat-Validierungszertifikate empfangen die vom Server gesendete Zertifikatkette und bestimmen, ob der Server als vertrauenswürdig eingestuft werden kann.

Zum Überprüfen von Zertifikaten können Sie die Validierungslogik des zugrunde liegenden Systems verwenden. Diese Systemvalidierung kann entweder Ihre eigene Validierungslogik unterstützen oder vollständig ersetzen. Wenn Sie beim Anfordern einer sicheren Verbindung kein eigenes Zertifikatvalidierungs-Validierungszertifikat übergeben, wird die Systemüberprüfung automatisch verwendet.

Bei Windows wird bei der Systemvalidierung Nach folgenden Überprüfungen überprüft:

* Integrität der Zertifikatkette: Die Zertifikate bilden eine konsistente Kette, die auf ein vertrauenswürdiges Stammzertifikat endet.
* Zertifikatgültigkeit: Das Zertifikat des Servers liegt innerhalb seiner Gültigkeitsdauer und wird für die Serverauthentifizierung ausgestellt.
* Sperrung: Das Zertifikat wurde nicht widerrufen.
* Name match: Der Hostname des Servers entspricht einem der Hostnamen, für die das Zertifikat ausgestellt wurde.

Implementieren Sie `ICertificateValidator` die -Schnittstelle wie folgt:

 * `PerformSystemValidation()` sollte `true` zurückgeben, wenn eine Systemvalidierung wie oben beschrieben ausgeführt werden soll. In diesem Fall wird das Systemvalidierungsergebnis als Eingabe an die -Methode `ValidateCertificate()` übergeben.
* `ValidateCertificate()` sollte die Zertifikatkette überprüfen und dann für den übergebenen Rückruf mit `CertificateValidated()` dem abschließenden Überprüfungsergebnis aufrufen. Diese Methode akzeptiert die Zertifikatkette, den Namen des Servers, mit dem die Verbindung hergestellt wird, und ob eine Sperrüberprüfung erzwungen werden soll. Wenn die Zertifikatkette mehrere Zertifikate enthält, ist das erste Zertifikat das Zertifikat des Betreffs.

>[!NOTE]
>Wenn Ihr Fall eine andere Form der Validierung erfordert (siehe Zertifikatsnutzungsfall #1), umgehen Sie die Systemvalidierung vollständig. Verwenden Sie stattdessen eine beliebige API oder Bibliothek, die DER-codierte X.509-Zertifikate verarbeiten kann, um die Zertifikatkette zu decodieren und die für Ihren Fall erforderlichen Überprüfungen durchzuführen.

## <a name="secure-connection-using-the-openxr-api"></a>Sichern der Verbindung mithilfe der OpenXR-API

Bei Verwendung der [OpenXR-API](../native/openxr.md) ist alle sichere verbindungsbezogene API als Teil der `XR_MSFT_holographic_remoting` OpenXR-Erweiterung verfügbar.

>[!IMPORTANT]
>Weitere Informationen zur OpenXR-Erweiterungs-API für Holographic Remoting finden Sie in der Spezifikation im [GitHub-Repository für Holographic Remoting-Beispiele.](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples) [](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html)

Die wichtigsten Elemente für die sichere Verbindung mithilfe der `XR_MSFT_holographic_remoting` OpenXR-Erweiterung sind die folgenden Rückrufe.
- `xrRemotingRequestAuthenticationTokenCallbackMSFT`, generiert oder ruft das zu gesendete Authentifizierungstoken ab.
- `xrRemotingValidateServerCertificateCallbackMSFT`überprüft die Zertifikatkette.
- `xrRemotingValidateAuthenticationTokenCallbackMSFT`überprüft das Clientauthentifizierungstoken.
- `xrRemotingRequestServerCertificateCallbackMSFT`, geben Sie der Serveranwendung das zu verwendende Zertifikat an.

Diese Rückrufe können für die Remoting-OpenXR-Runtime über und `xrRemotingSetSecureConnectionClientCallbacksMSFT` bereitgestellt `xrRemotingSetSecureConnectionServerCallbacksMSFT` werden. Darüber hinaus muss die sichere Verbindung über den secureConnection-Parameter für die -Struktur oder die -Struktur aktiviert werden, je nachdem, ob Sie `XrRemotingConnectInfoMSFT` `XrRemotingListenInfoMSFT` oder `xrRemotingConnectMSFT` `xrRemotingListenMSFT` verwenden.

Diese API ähnelt der IDL-basierten API, die unter [Implementieren der holografischen Remotingsicherheit beschrieben wird.](#implementing-holographic-remoting-security) Anstatt Schnittstellen zu implementieren, sollten Sie jedoch Rückrufimplementierungen bereitstellen. Ein ausführliches Beispiel finden Sie in der [OpenXR-Beispiel-App](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

## <a name="see-also"></a>Weitere Informationen
* [Schreiben einer Holographic Remoting-Remote-App mit Windows Mixed Reality APIs](holographic-remoting-create-remote-wmr.md)
* [Schreiben einer Holographic Remoting-Remote-App mit OpenXR-APIs](holographic-remoting-create-remote-openxr.md)
* [Schreiben einer benutzerdefinierten Holographic Remoting Player-App](holographic-remoting-create-player.md)
* [Problembehandlung und Einschränkungen bei Holographic Remoting](holographic-remoting-troubleshooting.md)
* [Holographic Remoting-Software – Lizenzbedingungen](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Datenschutzerklärung von Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)