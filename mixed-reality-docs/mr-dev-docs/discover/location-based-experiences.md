---
title: Location based Entertainment mit Windows Mixed Reality
description: Erfahren Sie mehr über Windows Mixed Reality für Location based Entertainment – Hardware, Rucksack PCs, Nachverfolgung, Konfiguration und Support.
author: jessemcculloch
ms.author: ishitak
ms.date: 08/03/2020
ms.topic: article
keywords: Mixed Reality, VR, LBE, Location, Mixed Reality Headset, Windows Mixed Reality Headset, Virtual Reality Headset, Hardware, hololens, Multi-Player, Cloud Services, Azure
ms.openlocfilehash: 323981d49c99f5cb175b71645851496bfa1f268c
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757828"
---
# <a name="location-based-entertainment-with-windows-mixed-reality"></a>Location based Entertainment mit Windows Mixed Reality

In den letzten Jahren haben wir eine unglaubliche Menge an Wachstum und Innovation in der Location based Entertainment-Kategorie gesehen. Herkömmliche Veranstaltungsorte wie Design Parks und Theater haben mit der Bereitstellung von immersiven multiplayererlebnissen für vorhandene Fahrten und Installationen begonnen. Neue Operatoren und Veranstaltungsorte bieten einzigartige Umgebungen mit mehreren sensorischen und mehr Spielern zu einem attraktiven Preis. Alle diese Möglichkeiten übertragen den Umschlag für das, was mit gemischter Realität möglich ist.

Dieses Dokument ist ein Leitfaden für die ersten Schritte mit Windows Mixed Reality in der Kategorie Location based Entertainment. Die nachfolgenden Anleitungen können zusätzlich auf standortbasierte Erfahrungen über Unterhaltung, wie z. b. Schulungen, Produkt Entwurf und andere Anwendungsfälle, angewendet werden.

## <a name="engineering-faq"></a>Technische FAQ

### <a name="hardware"></a>Hardware

**F: welche Hardware ist von Microsoft und seinen Partnern verfügbar, die ich in meinem Setup verwenden kann?**

A: Microsoft und seine OEM-Partner bieten ein überzeugendes Portfolio von Geräten, aus denen Sie abhängig von Ihren Anforderungen wählen können.  

Wenn die Benutzeroberflächen, die Sie Ihren Kunden bereitstellen, ein Virtual Reality-Headset benötigen, sind die marktfähigen Headsets von HP, Samsung und Acer eine gute Sache. Jedes Headset hat seine eigenen differenzierten Attribute. Weitere Details finden Sie unten.

HP-Reverb: [Details](https://hp.com/go/Reverbpro)

Samsung Odyssey +: [Details](https://www.samsung.com/us/computing/hmd/windows-mixed-reality/hmd-odyssey-windows-mixed-reality-headset-xe800zba-hc1us/)

Acer: [Details](https://www.acer.com/ac/en/US/content/model/VD.R05AP.002)

Wenn sich Ihr Standort auf gemischte oder erweiterte Reality-Erfahrungen mit See-Through-Headsets spezialisiert hat, sehen Sie sich die Microsoft hololens 2 an.  

Hololens 2: [Anordnen von Interesse](https://www.microsoft.com//hololens/buy)

Wenn Sie mit Erfahrungen experimentieren, die erweiterte Maschinelles sehen-, sprach-und Body-Nachverfolgung verwenden, ist das Azure kinect-DK gut geeignet.  

Azure kinect: [Details](https://azure.microsoft.com//services/kinect-dk/)

**F: Was ist das Portfolio von Rucksack-PCs, die ich verwenden kann, um meine PC-Tethering-VR-Erfahrungen auszuführen?**

Unsere OEMs bieten eine unglaubliche Auswahl von Rucksack-PCs, die genau für diese Anforderungen erstellt wurden.

HP hat soeben seinen HP VR-Rucksack G2 gestartet, der weltweit leistungsfähigste tragbaren PC – optimiert für die kostenlose Roaming-Umgebung, die jetzt 30% mehr Leistung mit einer RTX 2080-GPU in hat. [Details](https://www8.hp.com/us/en/vr/vr-backpack.html)

### <a name="setup"></a>Einrichten

**F: Wie kann ich das Setup leichter konfigurieren und das Mixed Reality-Portal für LBE anpassen?**

>[!NOTE]
>Diese Funktion erfordert eine Version 2000.19061.1011.0 oder höher.  

Möglicherweise stellen Sie fest, dass Sie eine bessere Anpassung des gemischten Reality-Portals benötigen, als normalerweise über die APP zur Bereitstellung von Apps für Kiosk-oder angepasste Benutzeroberflächen verfügbar ist Das letzte Update des Mixed Reality-Portals von Juli unterstützt mehrere erweiterte Einstellungen, die Sie über eine Konfigurationsdatei festlegen können:  

Fehlgeschlagene Systemüberprüfungen zulassen – normalerweise prüft der Setup Prozess den PC auf Kompatibilität mit Windows Mixed Reality, bevor das Setup abgeschlossen wird. Das umgehen von Kompatibilitäts Prüfungen kann zu Problemen führen, wenn Sie versuchen, Windows Mixed Reality auszuführen, wenn Kompatibilitätsprobleme vorliegen.  

Geräte-Begleit-App überspringen – die DCA bietet für den Hersteller bereitgestellte, vom Hersteller bereitgestellte, vom Hersteller bereitgestellte und aktualisierbare Aktualisierungs Schritte.  

Raumeinrichtung überspringen – anstatt zum Erstellen einer Raum Begrenzung aufgefordert zu werden, können Sie direkt in den Modus "sitzend/stehend" wechseln.  

Installieren von Apps aus dem Store überspringen: beim normalen Setup werden mehrere Store-Apps installiert, einschließlich des 3D-Viewers und des Edge 360 Viewer-Add-on. Dadurch wird die Installation dieser apps übersprungen, möglicherweise fehlen jedoch Gerätefunktionen.  

Vorschau anzeigen im Vollbild – im Mixed Reality-Portal wird standardmäßig die Headset-Vorschau im Vollbildmodus auf dem Desktop-PC angezeigt, während das Headset verwendet wird.  

Die Option "neu" im Bereich "Seite" – verhindert, dass die neue für den Bereich beim Starten des gemischten Reality-Portals erweitert wird.  

#### <a name="how-to-configure"></a>Vorgehensweise zur Konfiguration:  

Um diese Konfigurationen festzulegen, müssen Sie in diesem Verzeichnis eine Datei namens _UserConfig.json_ erstellen: _$ENV: localappdata\packages\ Microsoft.MixedReality.Portal_8wekyb3d8bbwe \localstate \\_

Für die meisten Benutzer sieht dies wie folgt aus: _c:\Users \<username> \appdata\local\packages\ Microsoft.mixedreality.portal_8wekyb3d8bbwe \localstate \\_

Die JSON-Datei sollte den folgenden Inhalt aufweisen, wenn "true" für eine der oben genannten Einstellungen festgelegt ist, die Sie aktivieren möchten:  

```
{

  "shouldAllowFailedSystemChecks": true,

  "shouldSkipDcaApp": true,

  "shouldSkipRoomSetup": true,

  "shouldSkipStoreAppInstall": true,

  "shouldShowPreviewFullScreen": true,

  "shouldHideEngagementPane": true

}
```
 
**F: gibt es Hinweise zum Konfigurieren des Playspace?**

A: das Konfigurieren eines Playspace sollte wie bei der Benutzer Einrichtung durch den Consumer erfolgen. Mit dem Einrichtungs Vorgang für Räume können Sie auch Ihre Raum Grenzen definieren. Weitere Informationen zum Konfigurieren von Raum Begrenzungen finden Sie [hier](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary).

Wie bereits im obigen Dokument erläutert, liegt der maximal zulässige Wert für die einfache Koordinate bei etwa 5mx5m. Wenn Sie über einen größeren Bereich verfügen möchten, können Sie die Funktion räumlicher Anker im Windows Holographic-API-Stapel verwenden. Die Verwendung dieser API erfordert eine benutzerdefinierte Entwicklung in den Erfahrungen, die Sie erzeugen.  

Weitere Informationen zum Optimieren von Inhalten für verschiedene Speicherplatz Größen finden Sie [hier](https://docs.microsoft.com//windows/mixed-reality/coordinate-systems).
 

**F: der Speicherplatz ist zu groß, und es treten Fehler auf, wenn ich versuche, eine bestehende Funktion mit Grenzen einzurichten. Was soll ich tun, um meine große kostenlose Roaming-Arbeit einzurichten?**

A: Wenn Sie einen größeren Speicherplatz als ~ 18x18ft einrichten möchten, können Sie die vom System bereitgestellte Begrenzungs Funktion nicht verwenden.  Die Begrenzungs Systeme basieren auf einer einzelnen Fixed-Koordinate "Anker", die instabil werden kann, wenn ein Benutzer zu weit vom Anker der Mittelstufe entfernt ist. 

Sie können den Modus "sitzend" einrichten, in dem die Grenze nicht angezeigt wird, oder Sie können keine Stufen Begrenzungen oder einen Playspace konfigurieren.  Sie müssen mehrere räumliche Anker innerhalb der App konfigurieren, um auf physische Begrenzungs Bereiche zu verweisen. 

Der Anwendungsentwickler ist dafür verantwortlich, die erforderlichen Sicherheitsvorkehrungen anzuzeigen, damit Benutzer nicht mit der physischen Umgebung in Konflikt stehen.  Dabei kann es sich um digitale Wände innerhalb der Darstellung oder um ein angepasstes visuelles Spielelement handeln. 

Anleitungen zum Einrichten der Raumgrenze mit WMR finden Sie [hier](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary).

**F: wo befindet sich der Ursprung des Playspace?**

A: der Ursprung des Playspace wird durch die Einrichtung des Raums festgelegt, genauer gesagt die Position des HMD, wenn während des Setups die Schaltfläche "Mittelpunkt" gedrückt wird. 

### <a name="multi-player-setup"></a>Einrichtung von mehreren Playern

**F: Ich lege in meinem Veranstaltungsort eine Multiplayer-Funktionalität bereit. Wird dies unter Windows Mixed Reality unterstützt?**

A: Wenn Sie sich für den Build von Windows 20h1 oder höher über unser Insider-Programm entscheiden, können Sie auf eine neue Schnittstelle für die Karten Freigabe zugreifen. Diese neue Funktionalität ist über die [Map Manager](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) -Schnittstelle des Windows-Geräte Portals verfügbar. Führen Sie die folgenden Schritte aus, um dieses Tool zu verwenden:
* Stellen Sie sicher, dass Sie 2019 für 20h1 oder höher angemeldet sind. Dies bedeutet, dass das Insider Programm verwendet wird.
* Aktivieren Sie das Windows-Geräte Portal (WDP) mithilfe dieser [Anweisungen](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-desktop) .
* Einbinden eines Windows Mixed Reality-HMD, bei dem Sie entweder eine vorhandene Karte herunterladen oder eine neue Karte importieren möchten
* Navigieren Sie im Browser Ihrer Wahl zum WDP, und verwenden Sie dabei die URL, die auf dem Bildschirm Einstellungen angegeben ist.
    * Navigieren Sie anschließend zum Abschnitt "Mixed Reality", und wählen Sie "Map Manager" aus.
    * Sie können jetzt die Schaltfläche "herunterladen" verwenden, um eine vorhandene Karte vom Computer zu exportieren.
    * Sie können die Schaltfläche "Hochladen einer Zuordnungs Datei" verwenden, um eine Zuordnung aus einem vorherigen Export (vielleicht auf einem anderen Computer) zu importieren.
    * Sie können "Importieren" verwenden, um das System für die Verwendung dieser Zuordnung für dieses HMD auf diesem Computer zu aktivieren.

> [!NOTE] 
> Bisher war es möglich, das Tool "Spatial Data Packager" zu verwenden. dieses Tool wurde jedoch ursprünglich als nicht unterstützt veröffentlicht und ist nun offiziell als veraltet markiert und nicht mehr in 20h1 funktionsfähig. Verwenden Sie stattdessen das Posteingangs Zuordnungs- [Manager](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) -Tool, wie oben beschrieben. 

### <a name="tracking"></a>Paletten

F: wie funktioniert die nach Verfolgungs Technologie in den Windows Mixed Reality-Headsets?  

Gemischte Realität nutzt dieselbe nach Verfolgungs Technologie wie hololens. Weitere Informationen zum in-out-nach Verfolgungs [System finden Sie in der Dokumentation.](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/tracking-system)

Eine Beschreibung der Funktionsweise des räumlichen Zuordnungs Systems auf höherer Ebene finden Sie [hier](../design/spatial-mapping.md).

**F: gibt es bewährte Methoden, um ein zuverlässiges nach Verfolgungs Volume zu erhalten?**

Zum optimalen Konfigurieren der Umgebung für die erfolgreiche Überwachung können Sie die bewährten Methoden in diesem [Beitrag](../environment-considerations-for-hololens.md)lesen.

**F: gibt es bestimmte Nuancen bei der Nachverfolgung von Speicherplätzen oder Optimierungen, die in Erwägung gezogen werden sollen?**

A: mithilfe der folgenden Vorgehensweisen können Sie ein zuverlässigeres nach Verfolgungs Volume erzielen:  

Wenn Sie verschiedene Funktionen im Raum bereitstellen, die sich an mehreren Positionen überlappen, kann das Überwachungssystem eine solide Sperre erhalten. Stellen Sie sich die zufälligen Zeichnungs-Splatter und Schraffuren vor, anstelle von Solid-Contour-stillinien. 

Minimieren Sie möglichst den dynamischen Bereich der Beleuchtung in Ihrem Bereich. Die Überwachungskameras in den Mixed Reality-HMDs sind nicht HDR und verfügen über AGC (automatischer Gewinn) und AEC (automatische verfügbar machung) für die unterschiedliche Beleuchtung. Abhängig von der Verteilung von Oberflächen Licht, Mustern und Kontrast kann es sein, dass entweder "AGC" oder "AEC" sich in einem viel weißen Raum oder in einem schwarzen Raum befindet, wodurch ihre Features, die sich möglicherweise in der gegenüberliegenden "Farbe" befinden, ausgeblendet werden. Wenn Sie versuchen, ein inneres Bild vor einem äußeren Fenster mit heller Sommerzeit zu machen, und Sie die Verfügbarkeit anpassen, sodass Sie Details außerhalb von sehen können, ist alles im Inneren nicht verfügbar und schwarz. Wenn Sie in festgelegt ist, wird alles außen nun überlastet und weiß.  

Gibt einen Raum (auch mehr Aufwand) aus, der angezeigt wird, wenn Überwachungskameras manchmal Täter sind, was die AEC/AGC der Überwachungskameras verwirrt. Die flache/Diffused-Beleuchtung ist hilfreich.  

### <a name="mixed-reality-cloud-services-and-azure"></a>Gemischte Realität Cloud Services und Azure 

**F: Wie kann Microsoft Azure meiner geschäftlichen Skalierbarkeit helfen?**

A: Azure-basierte und Remote Verwaltung können Ihrem Unternehmen helfen, Daten gesteuert zu werden, Betriebskosten zu senken und die Bereitstellung über vorhandene und neue Standorte hinweg zu skalieren. Azure-Clouddienste wie Azure Storage, Azure Functions, App Service, Azure-Netzwerke und IOT Hub können bei den folgenden Anwendungsfällen hilfreich sein:  

Remote Geräte Bereitstellung & Verwaltung 

Analyse von Real-Time vor Ort 

Intelligent anpassbares LBE-Spiel 

Streaming und Bereitstellung von LBE-Inhalten 

Heatmap für LBE-Player-Vorlieben 

LBE-Reservierungs-und-Reservierungs System 

**F: Ich entwickle eine räumliche MMOG für die Bereitstellung über einen riesigen Speicherbedarf. Alle Dienste, die mir helfen, meine Inhalte und Objekt Persistenz zu verwalten?**

A: räumliche Azure-Anker sind ein neuer gemischter Reality-Dienst, der mehr Benutzer, räumlich unterstützende gemischte Reality-Umgebungen auf hololens-, IOS-und Android-Geräten ermöglicht. Weitere Informationen zu räumlichen Azure-Ankern finden Sie [hier](https://azure.microsoft.com//services/spatial-anchors/).

**Q1. Unser Veranstaltungsort ist auf Erfahrung mit mehreren Playern spezialisiert, und ich möchte unsere Entwicklungszeit auf Inhalte und die Front-End-Entwicklung konzentrieren. Gibt es Angebote, die mir helfen können, die Back-End-Entwicklung zu Bootstrap oder auszulagern?**

A: Azure playfab ist eine umfassende Back-End-Plattform für Live Spiele. Weitere Informationen hierzu finden Sie [hier](https://playfab.com/).

### <a name="misc"></a>Sonstiges

**F: Ich verwende "steamvr", um meine Erfahrungen bereitzustellen. Funktioniert Windows Mixed Reality mit steamvr?**

A: Windows Mixed Reality für steamvr ermöglicht Benutzern das Ausführen von steamvr-Erfahrungen auf Windows Mixed Reality-immersiven Headsets. Weitere Informationen zu "steamvr" mit WMR [finden Sie hier](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality).

### <a name="support-and-community"></a>Support und Community  

Wir haben einige hilfreiche Ressourcen, die Ihnen helfen, sich mit Fachleuten in unserem Team in Verbindung zu setzen, Support bei der Problembehandlung zu erhalten und zur umfassenderen Community dev Community beizutragen.  

Wenn Sie Probleme mit öffentlich veröffentlichten Features haben, melden Sie einen Fehler mit dem Feedback-Hub. eine Anleitung finden Sie auf dieser [Seite](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/filing-feedback).

Wenn Sie weitere Hilfe zur Problembehandlung bei WMR benötigen, können Sie eine [Supportanfrage](https://support.microsoft.com//supportforbusiness/productselection?sapId=96bfb202-bc79-741b-bf7a-774d8b767782) an unser Kundensupport Team einreichen.

Treten Sie unserem holodevelopers Slack-Channel bei, um sich mit den gemischten Reality-Entwicklern und Fachleuten zu befassen: [aka.ms/holodevelopers](https://aka.ms/holodevelopers)

Twitter: Befolgen Sie unser Mixed Reality-Entwickler Beziehungs Team für Neuigkeiten, Veranstaltungen und Updates. @MxdRealityDev 

Wenn Sie sich in der Nähe von San Francisco befinden, gibt es immer etwas, das im Microsoft-Reaktor passiert. Sie können den Kalender der Ereignisse [hier](https://developer.microsoft.com//reactor/Location/San%20Francisco)sehen.
