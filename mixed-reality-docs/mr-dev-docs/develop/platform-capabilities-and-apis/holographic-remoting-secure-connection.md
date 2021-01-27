---
title: Aktivieren der Verbindungssicherheit für Holographic-Remoting
description: Auf dieser Seite wird erläutert, wie Sie Holographic Remoting so konfigurieren, dass verschlüsselte und authentifizierte Verbindungen zwischen Player-und Remote-Apps verwendet werden.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: Hololens, Remoting, Holographic Remoting, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Sicherheit, Authentifizierung, Server-zu-Client
ms.openlocfilehash: ea00565580fdbc850a11d103520351be53cb37b5
ms.sourcegitcommit: 63b7f6d5237327adc51486afcd92424b79e6118b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2021
ms.locfileid: "98810117"
---
# <a name="enabling-connection-security-for-holographic-remoting"></a>Aktivieren der Verbindungssicherheit für Holographic-Remoting

>[!IMPORTANT]
>Diese Anleitung gilt speziell für Holographic-Remoting auf hololens 2.

Auf dieser Seite erhalten Sie einen Überblick über die Netzwerksicherheit für Holographic Remoting. Hier finden Sie Informationen zu

* Sicherheit im Kontext von Holographic-Remoting und warum Sie es möglicherweise benötigen
* Empfohlene Measures, die auf verschiedenen Anwendungsfällen basieren
* Implementieren der Sicherheit in ihrer Holographic-Remoting-Lösung

## <a name="holographic-remoting-security"></a>Holografische Remoting-Sicherheit

Holographic Remoting tauscht Informationen über ein Netzwerk aus. Wenn keine Sicherheitsmaßnahmen vorhanden sind, können Angreifer im selben Netzwerk die Integrität der Kommunikation beeinträchtigen oder auf vertrauliche Informationen zugreifen.

Die Beispiel-apps und der Holographic-Remoting-Player im Windows Store sind mit der Sicherheit deaktiviert. Dadurch lassen sich die Beispiele leichter verstehen. Außerdem hilft es Ihnen, schneller mit der Entwicklung zu beginnen.

Für Test-oder Produktionsumgebungen wird dringend empfohlen, die Sicherheit in ihrer Holographic Remoting-Lösung zu aktivieren.

Die Sicherheit in Holographic Remoting bietet Ihnen die folgenden Garantien, wenn Sie für Ihren Anwendungsfall ordnungsgemäß eingerichtet ist:

* **Authentizität:** sowohl Player als auch Remote-app können sicher sein, dass es sich bei der anderen Seite um
* **Vertraulichkeit:** Drittanbieter können die zwischen Player und Remote-app ausgetauschten Informationen nicht lesen.
* **Integrität:** Player und Remote können alle Übertragung von Änderungen an ihrer Kommunikation erkennen.

>[!IMPORTANT]
>Um Sicherheitsfeatures verwenden zu können, müssen Sie sowohl einen [benutzerdefinierten Player](holographic-remoting-create-player.md) als auch eine benutzerdefinierte Remote-App mithilfe von [Windows Mixed Reality](holographic-remoting-create-remote-wmr.md) oder [openxr](holographic-remoting-create-remote-openxr.md) -APIs implementieren.

>[!NOTE]
> Ab Version [2.4.0](holographic-remoting-version-history.md#v2.4.0) können Remote-apps, die die [openxr-API](../native/openxr.md) verwenden, erstellt werden. Eine Übersicht über das Einrichten einer sicheren Verbindung in einer openxr-Umgebung finden Sie [unten](#secure-connection-using-the-openxr-api).

## <a name="planning-the-security-implementation"></a>Planen der Sicherheits Implementierung

Wenn Sie die Sicherheit in Holographic Remoting aktivieren, aktiviert die remotingbibliothek automatisch Verschlüsselungs-und Integritätsprüfungen für alle über das Netzwerk ausgetauschten Daten.

Um sicherzustellen, dass die richtige Authentifizierung erforderlich ist Was genau Sie tun müssen, hängt von Ihrem Anwendungsfall ab, und im weiteren Verlauf dieses Abschnitts werden die erforderlichen Schritte erläutert.

>[!IMPORTANT]
> Dieser Artikel bietet nur einen allgemeinen Leitfaden. Wenn Sie sich nicht sicher sind, sollten Sie sich an einen Sicherheitsexperten wenden, der Ihnen Anleitungen für Ihren Anwendungsfall bietet.

Erste Terminologie: beim Beschreiben von Netzwerkverbindungen werden die Begriffe _Client_ und _Server_ verwendet. Der Server lauscht auf eingehende Verbindungen mit einer bekannten Endpunkt Adresse, und der Client ist der Server, der eine Verbindung mit dem Endpunkt des Servers herstellt.

>[!NOTE]
> Die Client-und-Server Rollen sind nicht daran gebunden, ob eine App als Player oder als Remote fungiert. Obwohl die Beispiele den Player in der Server Rolle aufweisen, ist es einfach, die Rollen umzukehren, wenn Sie für Ihren Anwendungsfall besser geeignet sind.

### <a name="planning-the-server-to-client-authentication"></a>Planen der Server-zu-Client-Authentifizierung

Der Server verwendet digitale Zertifikate, um die Identität des Clients nachzuweisen. Der Client überprüft das Serverzertifikat während der Verbindungs Hand Shake Phase. Wenn der Client den Server nicht als vertrauenswürdig einstuft, wird die Verbindung an dieser Stelle beendet.

Wie der Client das Serverzertifikat überprüft und welche Arten von Server Zertifikaten verwendet werden können, hängt von Ihrem Anwendungsfall ab.

**Anwendungsfall 1:** Der Server Hostname ist nicht korrigiert, oder der Server wird nicht durch den Hostnamen adressiert.

In diesem Anwendungsfall ist es nicht praktikabel (oder sogar möglich), ein Zertifikat für den Hostnamen des Servers auszugeben. Es wird empfohlen, stattdessen den Fingerabdruck des Zertifikats zu überprüfen. Wie bei einem Menschen Fingerabdruck identifiziert der Fingerabdruck ein Zertifikat eindeutig.

Es ist wichtig, den Fingerabdruck out-of-Band an den Client zu übermitteln. Dies bedeutet, dass Sie Sie nicht über die gleiche Netzwerkverbindung, die für Remoting verwendet wird, senden können. Stattdessen können Sie Sie manuell in die Konfiguration des Clients eingeben oder den Client einen QR-Code Scannen lassen.

**Anwendungsfall 2:** Der Server kann über einen stabilen Hostnamen erreicht werden.

In diesem Anwendungsfall verfügt der Server über einen bestimmten Hostnamen, und Sie wissen, dass sich dieser Name wahrscheinlich nicht ändert. Sie können dann ein Zertifikat verwenden, das für den Hostnamen des Servers ausgestellt wurde. Basierend auf dem Hostnamen und der Vertrauenskette des Zertifikats wird die Vertrauensstellung eingerichtet.

Wenn Sie diese Option auswählen, muss der Client den Hostnamen des Servers und das Stamm Zertifikat im Voraus kennen.

### <a name="planning-the-client-to-server-authentication"></a>Planen der Client-zu-Server-Authentifizierung

Clients authentifizieren sich mit einem frei Form Token für den Server. Was dieses Token enthalten sollte, hängt wieder von Ihrem Anwendungsfall ab:

**Anwendungsfall 1:** Sie müssen nur die Identität der Client-App überprüfen.

In diesem Anwendungsfall kann ein gemeinsamer geheimer Schlüssel ausreichen. Dieser geheime Schlüssel muss komplex genug sein, damit er nicht erraten werden kann.

Ein guter gemeinsamer geheimer Schlüssel ist eine zufällige GUID, die manuell in der Konfiguration des Servers und des Clients eingegeben wird. Zum Erstellen eines solchen können Sie z. b. den `New-Guid` Befehl in PowerShell verwenden.

Stellen Sie sicher, dass dieser gemeinsame geheime Schlüssel nie über unsichere Kanäle kommuniziert. Die Remoting-Bibliothek stellt sicher, dass der gemeinsame geheime Schlüssel immer verschlüsselt und nur an vertrauenswürdige Peers gesendet wird.

**Anwendungsfall 2:** Außerdem müssen Sie die Identität des Benutzers der Client-App überprüfen.

Ein gemeinsamer geheimer Schlüssel reicht nicht aus, um diesen Anwendungsfall abzudecken. Stattdessen können Sie Token verwenden, die von einem Identitäts Anbieter erstellt wurden. Ein Authentifizierungs Workflow, der einen Identitäts Anbieter verwendet, sieht wie folgt aus:

* Der Client autorisiert sich für den Identitäts Anbieter und fordert ein Token an.
* Der Identitäts Anbieter generiert ein Token und sendet es an den Client.
* Der Client sendet dieses Token über Holographic Remoting an den Server.
* Der Server überprüft das Client Token anhand des Identitäts Anbieters.

Ein Beispiel für einen Identitäts Anbieter ist die [Microsoft Identity Platform](/azure/active-directory/develop/).

Stellen Sie wie im vorherigen Anwendungsfall sicher, dass diese Token nicht über unsichere Kanäle gesendet werden oder anderweitig verfügbar gemacht werden.

## <a name="implementing-holographic-remoting-security"></a>Implementieren von Holographic Remoting Security

Denken Sie daran, dass Sie benutzerdefinierte Remote-und Player-apps implementieren müssen, wenn Sie die Verbindungssicherheit aktivieren möchten. Sie können die bereitgestellten Beispiele als Ausgangspunkte für Ihre eigenen Apps verwenden.

Um die Sicherheit zu aktivieren, wird `ListenSecure()` anstelle von `Listen()` und `ConnectSecure()` anstelle von aufgerufen, `Connect()` um die Remoting-Verbindung herzustellen.

Diese Aufrufe erfordern, dass Sie Implementierungen bestimmter Schnittstellen bereitstellen, um sicherheitsrelevante Informationen bereitzustellen und zu überprüfen:

* Der Server muss einen Zertifikat Anbieter und ein Authentifizierungs Validierungs Steuerelement implementieren.
* Der Client muss einen Authentifizierungs Anbieter und ein zertifikatvalidator implementieren.

Alle Schnittstellen verfügen über eine Funktion, die Sie anfordert, Maßnahmen zu ergreifen, die ein Rückruf Objekt als Parameter empfängt. Mithilfe dieses Objekts können Sie die asynchrone Verarbeitung der Anforderung problemlos implementieren. Behalten Sie einen Verweis auf dieses Objekt bei, und nennen Sie die Vervollständigungsfunktion, wenn die asynchrone Aktion abgeschlossen ist. Die Vervollständigungsfunktion kann von jedem Thread aufgerufen werden.

>[!TIP]
>Das Implementieren von WinRT-Schnittstellen kann problemlos mithilfe von C++ erfolgen./WinRT. Im Kapitel " [Autoren-APIs mit C++/WinRT](/windows/uwp/cpp-and-winrt-apis/author-apis) " wird dies ausführlich beschrieben.

>[!IMPORTANT]
>Der `build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl` im nuget-Paket enthält eine ausführliche Dokumentation für die API, die sich auf sichere Verbindungen bezieht.

### <a name="implementing-a-certificate-provider"></a>Implementieren eines Zertifikat Anbieters

Zertifikat Anbieter stellen die Serveranwendung mit dem zu verwendenden Zertifikat bereit. Die-Implementierung besteht aus zwei Teilen:

1) Ein Zertifikat Objekt, das die- `ICertificate` Schnittstelle implementiert:

    * `GetCertificatePfx()` sollte den binären Inhalt eines `PKCS#12` Zertifikat Speicher zurückgeben. Eine `.pfx` Datei enthält `PKCS#12` Daten, sodass Ihr Inhalt direkt hier verwendet werden kann.
    * `GetSubjectName()` Gibt den anzeigen Amen zurück, der das zu verwendende Zertifikat identifiziert. Wenn dem Zertifikat kein Anzeige Name zugewiesen ist, sollte diese Funktion den Antragsteller Namen des Zertifikats zurückgeben.
    * `GetPfxPassword()` Gibt das Kennwort zurück, das zum Öffnen des Zertifikat Speicher erforderlich ist (oder eine leere Zeichenfolge, wenn kein Kennwort erforderlich ist).

2) Ein Zertifikat Anbieter, der die- `ICertificateProvider` Schnittstelle implementiert:
    * `GetCertificate()` sollte ein Zertifikat Objekt erstellen und durch Aufrufen von `CertificateReceived()` für das Rückruf Objekt zurückgeben.

### <a name="implementing-an-authentication-validator"></a>Implementieren eines Authentifizierungs Validierungs Steuer Elements

Authentifizierungs Validierungs Steuerelemente empfangen das vom Client gesendete Authentifizierungs Token und Antworten mit dem Überprüfungs Ergebnis.

Implementieren Sie die- `IAuthenticationReceiver` Schnittstelle wie folgt:

* `GetRealm()` sollte den Namen des Authentifizierungs Bereichs (ein HTTP-Bereich, der während des Remoting-verbindungshandshakes verwendet wird) zurückgeben.
* `ValidateToken()` sollte das Client Authentifizierungs Token überprüfen und `ValidationCompleted()` für das Rückruf Objekt mit dem Validierungs Ergebnis aufgerufen werden.

### <a name="implementing-an-authentication-provider"></a>Implementieren eines Authentifizierungs Anbieters

Authentifizierungs Anbieter generieren oder rufen das Authentifizierungs Token ab, das an den Server gesendet werden soll.

Implementieren Sie die- `IAuthenticationProvider` Schnittstelle wie folgt:

* `GetToken()` soll das zu sendende Authentifizierungs Token generieren oder abrufen. Wenn das Token bereit ist, rufen Sie die- `TokenReceived()` Methode für das Rückruf Objekt auf.

### <a name="implementing-a-certificate-validator"></a>Implementieren eines zertifikatvalidator

Zertifikat Validierungs Steuerelemente empfangen die vom Server gesendete Zertifikatskette und ermitteln, ob der Server vertrauenswürdig ist.

Zum Überprüfen von Zertifikaten können Sie die Validierungs Logik des zugrunde liegenden Systems verwenden. Diese Systemvalidierung kann entweder Ihre eigene Validierungs Logik unterstützen oder Sie vollständig ersetzen. Wenn Sie Ihr eigenes Zertifikat Validierungs Steuerelement nicht übergeben, wenn Sie eine sichere Verbindung anfordern, wird die Systemvalidierung automatisch verwendet.

Unter Windows prüft die Systemvalidierung Folgendes:

* Integrität der Zertifikat Kette: die Zertifikate bilden eine konsistente Kette, die auf einem vertrauenswürdigen Stamm Zertifikat endet.
* Gültigkeit des Zertifikats: das Zertifikat des Servers liegt innerhalb seines Gültigkeits Zeitraums und wird für die Server Authentifizierung ausgegeben.
* Sperrung: das Zertifikat wurde nicht widerrufen.
* Namens Übereinstimmung: der Hostname des Servers stimmt mit einem der Hostnamen überein, für die das Zertifikat ausgestellt wurde.

Implementieren Sie die- `ICertificateValidator` Schnittstelle wie folgt:

 * `PerformSystemValidation()` sollte zurückgeben, `true` Wenn eine Systemvalidierung wie oben beschrieben ausgeführt werden soll. In diesem Fall wird das Ergebnis der Systemvalidierung als Eingabe an die-Methode übermittelt `ValidateCertificate()` .
* `ValidateCertificate()` Überprüfen Sie die Zertifikat Kette, und rufen Sie dann `CertificateValidated()` für den übergebenen Rückruf mit dem abschließenden Validierungs Ergebnis auf. Diese Methode akzeptiert die Zertifikatskette, den Namen des Servers, mit dem die Verbindung hergestellt wird, und gibt an, ob eine Sperr Überprüfung erzwungen werden soll. Wenn die Zertifikat Kette mehrere Zertifikate enthält, ist die erste Zertifikat Kette das Zertifikat des Antragstellers.

>[!NOTE]
>Wenn Ihr Anwendungsfall eine andere Form der Überprüfung erfordert (siehe #1 oben), umgehen Sie die Systemvalidierung vollständig. Verwenden Sie stattdessen eine beliebige API oder Bibliothek, mit der die-codierten X. 509-Zertifikate verarbeitet werden können, um die Zertifikat Kette zu decodieren und die für Ihren Anwendungsfall erforderlichen Überprüfungen auszuführen.

## <a name="secure-connection-using-the-openxr-api"></a>Sichere Verbindung mithilfe der openxr-API

Wenn Sie die [openxr-API](../native/openxr.md) verwenden, ist die gesamte sichere verbindungsbezogene API als Teil der `XR_MSFT_holographic_remoting` openxr-Erweiterung verfügbar.

>[!IMPORTANT]
>Weitere Informationen zur API für die Holographic Remoting openxr-Erweiterung finden Sie in der [Spezifikation](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html) , die im [GitHub-Repository "Holographic Remoting Samples](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)" zu finden ist.

Die wichtigsten Elemente für eine sichere Verbindung mit der `XR_MSFT_holographic_remoting` openxr-Erweiterung sind die folgenden Rückrufe.
- `xrRemotingRequestAuthenticationTokenCallbackMSFT`, generiert oder ruft das zu sendende Authentifizierungs Token ab.
- `xrRemotingValidateServerCertificateCallbackMSFT`, überprüft die Zertifikat Kette.
- `xrRemotingValidateAuthenticationTokenCallbackMSFT`überprüft das Client Authentifizierungs Token.
- `xrRemotingRequestServerCertificateCallbackMSFT`, stellen Sie die Serveranwendung mit dem zu verwendenden Zertifikat bereit.

Diese Rückrufe können für die Remoting openxr Runtime über und bereitgestellt werden `xrRemotingSetSecureConnectionClientCallbacksMSFT` `xrRemotingSetSecureConnectionServerCallbacksMSFT` . Außerdem muss die sichere Verbindung über den secureconnection-Parameter für die `XrRemotingConnectInfoMSFT` Struktur oder die Struktur aktiviert werden, abhängig davon, `XrRemotingListenInfoMSFT` ob Sie `xrRemotingConnectMSFT` oder verwenden `xrRemotingListenMSFT` .

Diese API ähnelt der IDL-basierten API, die unter [Implementieren von Holographic Remoting Security](#implementing-holographic-remoting-security)beschrieben wird. Anstatt Schnittstellen zu implementieren, sollten Sie jedoch Rückruf Implementierungen bereitstellen. Ein ausführliches Beispiel finden Sie in der [openxr](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)-Beispiel-app.

## <a name="see-also"></a>Weitere Informationen
* [Schreiben einer Holographic Remoting-Remote-app mit Windows Mixed Reality-APIs](holographic-remoting-create-remote-wmr.md)
* [Schreiben einer Holographic Remoting-Remote-App mithilfe von openxr-APIs](holographic-remoting-create-remote-openxr.md)
* [Schreiben einer benutzerdefinierten Holographic Remoting Player-App](holographic-remoting-create-player.md)
* [Problembehandlung und Einschränkungen für Holographic Remoting](holographic-remoting-troubleshooting.md)
* [Holographic Remoting-Software – Lizenzbedingungen](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Datenschutzerklärung von Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)