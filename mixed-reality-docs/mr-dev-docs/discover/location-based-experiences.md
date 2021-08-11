---
title: Location Based Unterhaltung mit Windows Mixed Reality
description: Erfahren Sie mehr über Windows Mixed Reality für Location Based Unterhaltung– Hardware, PCs, Nachverfolgung, Konfiguration und Support.
author: jessemcculloch
ms.author: ishitak
ms.date: 08/03/2020
ms.topic: article
keywords: Mixed Reality, VR, LBE, Standort, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Hardware, HoloLens, Multiplayer, Clouddienste, Azure
ms.openlocfilehash: e9cff1184ca60f4b64be5346a187666e7b401aab06fee87c179917e300aa07f3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196784"
---
# <a name="location-based-entertainment-with-windows-mixed-reality"></a>Location Based Unterhaltung mit Windows Mixed Reality

In den letzten Jahren haben wir ein enormes Maß an Wachstum und Innovation in der Kategorie Location Based Unterhaltung gesehen. Traditionelle Veranstaltungsorte wie Design- und Veranstaltungen haben damit begonnen, immersive Multiplayererfahrungen als ergänzende Erfahrungen für vorhandene Fahrten und Installationen anzubieten. Neue Betreiber und Veranstaltungsorte bringen einzigartige multisensorische Multiplayererfahrungen zu einem attraktiven Preis für die Massen. All diese Erfahrungen schieben den Umschlag für das, was mit Mixed Reality möglich ist.

Dieses Dokument ist ein Leitfaden für die ersten Schritte mit Windows Mixed Reality in der Kategorie Location Based Unterhaltung. Die nachstehende Anleitung kann zusätzlich für standortbasierte Umgebungen gelten, die über Unterhaltung hinausgehen, z. B. Training, Produktdesign und andere Anwendungsfälle.

## <a name="engineering-faq"></a>Häufig gestellte Fragen zu Engineering

### <a name="hardware"></a>Hardware

**F: Welche Hardware steht von Microsoft und seinen Partnern zur Verfügung, die ich in meinem Setup verwenden kann?**

A: Microsoft und seine OEM-Partner bieten je nach Ihren Anforderungen ein überzeugendes Portfolio von Geräten zur Auswahl.  

Wenn die Umgebungen, die Sie Ihren Kunden bereitstellen, ein Virtual Reality-Headset benötigen, eignen sich in der Markteinführungs-Headsets von HP, Samsung und Acer hervorragend. Jedes Headset verfügt über eigene differenzierte Attribute. Ausführlichere Informationen zu den einzelnen Untenstehenden.

HP Reverb: [Details](https://hp.com/go/Reverbpro)

Samsung Odyssey+: [Details](https://www.samsung.com/us/computing/hmd/windows-mixed-reality/hmd-odyssey-windows-mixed-reality-headset-xe800zba-hc1us/)

Acer: [Details](https://www.acer.com/ac/en/US/content/model/VD.R05AP.002)

Wenn Ihr Standort auf Mixed- oder Augmented Reality-Erfahrungen mit Durchseh-Headsets spezialisiert ist, sehen Sie sich die Microsoft HoloLens 2 an.  

HoloLens 2: [Vorbestell-Zins](https://www.microsoft.com//hololens/buy)

Wenn Sie mit Erfahrungen experimentieren, die erweitertes Sehen, Sprache und Body Tracking verwenden, ist azure Kinect DK gut geeignet.  

Azure Kinect: [Details](https://azure.microsoft.com//services/kinect-dk/)

**F: Welches Portfolio von PCs kann ich verwenden, um meine PC-bezogenen VR-Umgebungen auszuführen?**

Für PC-tethered VR-Umgebungen bieten unsere OEMs eine einzigartige Auswahl an PCs, die genau für diese Zwecke erstellt wurden.

HP hat soeben den HP VR-G2 eingeführt, den weltweit leistungsstärksten wearable PC– optimiert für Free-Roaming-Umgebungen, jetzt mit 30 % mehr Leistung mit einer RTX 2080-GPU. [Details](https://www8.hp.com/us/en/vr/vr-backpack.html)

### <a name="setup"></a>Setup

**F: Wie kann ich das Setup einfacher konfigurieren und die Mixed Reality-Portal für LBE anpassen?**

>[!NOTE]
>Für dieses Feature ist Version 2000.19061.1011.0 oder höher erforderlich.  

Möglicherweise benötigen Sie mehr Anpassungen der Mixed Reality-Portal, als normalerweise über die App für die Bereitstellung von Apps in Kiosken oder benutzerdefinierten Benutzererlebnissen verfügbar sind. Das neueste Juli-Update von Mixed Reality-Portal unterstützt mehrere erweiterte Einstellungen, die Sie über eine Konfigurationsdatei festlegen können:  

Fehlgeschlagene Systemüberprüfungen zulassen: Normalerweise überprüft der Setupprozess den PC vor Abschluss des Setups auf Kompatibilität mit Windows Mixed Reality. Das Umgehen von Kompatibilitätsprüfungen kann zu Problemen beim Versuch führen, Windows Mixed Reality auszuführen, wenn Kompatibilitätsprobleme vorliegen.  

Gerätebegleitungs-App überspringen: Die DCA stellt headsetspezifische Setupschritte bereit, die vom Hersteller bereitgestellt werden, und ermöglicht das Aktualisieren der Firmware des Headsets.  

Raumeinrichtung überspringen: Anstatt aufgefordert zu werden, eine Raumgrenze zu erstellen, können Sie direkt mit dem Headset im Modus "Seated/Standing" fortfahren.  

Überspringen der Installation von Apps aus dem Store: Bei der normalen Installation werden mehrere Store-Apps installiert, einschließlich 3D-Viewer und des Edge 360 Viewer-Add-Ons. Dadurch wird die Installation dieser Apps übersprungen, aber möglicherweise fehlen Ihnen die Gerätefunktionen.  

Vorschau im Vollbildmodus anzeigen: Mixed Reality-Portal zeigt die Headsetvorschau standardmäßig im Vollbildmodus auf dem Desktop-PC an, während das Headset verwendet wird.  

Neues für Ihren Seitenbereich ausblenden: Verhindert, dass der Bereich Neu für Sie beim Start von Mixed Reality-Portal erweitert wird.  

#### <a name="how-to-configure"></a>Vorgehensweise zur Konfiguration:  

Um eine dieser Konfigurationen festzulegen, müssen Sie eine Datei namens _UserConfig.js_ unter diesem Verzeichnis erstellen: _$env:LOCALAPPDATA\Packages\Microsoft.MixedReality.Portal_8wekyb3d8bbwe\LocalState \\_

Für die meisten Benutzer sieht dies wie folgt aus: _C:\Users \<username> \AppData\Local\Packages\microsoft.mixedreality.portal_8wekyb3d8bbwe\LocalState \\_

Für die JSON-Datei sollte der folgende Inhalt mit "true" für alle oben genannten Einstellungen festgelegt sein, die Sie aktivieren möchten:  

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
 
**F: Gibt es Anleitungen zum Konfigurieren des Playspaces?**

A: Die Konfiguration eines Playspace sollte wie bei der Einrichtung eines Consumers erfolgen. Mit dem Raumeinrichtungsprozess können Sie auch Ihre Raumgrenzen definieren. Weitere Informationen zum Konfigurieren von Raumgrenzen finden Sie [hier.](/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary)

Wie im obigen Dokument erläutert, beträgt der maximal sinnvolle Playspace mit einer einzelnen Koordinate ca. 5 mx5 m. Wenn Sie einen größeren Bereich haben möchten, können Sie die Spatial Anchors-Funktion im Windows Holographic-API-Stapel nutzen. Die Verwendung dieser API erfordert benutzerdefiniertes Engineering in den Von Ihnen erzeugten Erfahrungen.  

Weitere Informationen zum Optimieren Ihrer Inhalte für verschiedene Speicherplatzgrößen finden Sie [hier.](/windows/mixed-reality/coordinate-systems)
 

**F: Mein Speicherplatz ist zu groß, und es treten Fehler auf, wenn ich versuche, eine ständige Erfahrung mit Grenzen einzurichten. Was muss ich tun, um meine umfangreiche Kostenlose-Roaming-Erfahrung einzurichten?**

A: Um einen größeren Speicherplatz als ~18 x 18ft einzurichten, können Sie die vom System bereitgestellte Begrenzungserfahrung nicht verwenden.  Die Begrenzungssysteme basieren auf einem einzelnen festen Koordinatenanker, der instabil werden kann, wenn ein Benutzer zu weit vom Mittelpunktanker entfernt ist. 

Sie können den modus "seated" einrichten, der weder die Grenze anzeigt noch eine Stufenbegrenzung oder einen Playspace konfiguriert.  Sie müssen mehrere Raumanker innerhalb der App konfigurieren, um auf physische Begrenzungsbereiche zu verweisen. 

Der Anwendungsentwickler ist dafür verantwortlich, die erforderlichen Sicherheitsvorkehrungen anzuzeigen, damit Benutzer nicht mit der physischen Umgebung kollidieren.  Dabei kann es sich um digitale Wände innerhalb der Benutzeroberfläche oder um ein angepasstes Spielbegrenzungsvisual handelt. 

Eine Anleitung zum Einrichten der Raumgrenze mit WMR finden Sie [hier.](/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary)

**F: Wo ist der Ursprung des Playspaces?**

A: Der Ursprung des Playspace wird durch die Raumeinrichtung bestimmt, genauer gesagt durch die HMD-Position, wenn während des Setups die Schaltfläche "Center" gedrückt wird. 

### <a name="multi-player-setup"></a>SETUP FÜR MEHRERE PLAYER

**F: Ich stelle eine Multiplayererfahrung in an meinem Veranstaltungsort bereit. Wird dies auf Windows Mixed Reality unterstützt?**

A: Wenn Sie den Windows 20H1 oder höher über unser Insider-Programm nutzen, können Sie auf eine neue Schnittstelle für die Kartenfreigabe zugreifen. Diese neue Funktion ist über die [Map Manager-Schnittstelle](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) des Windows-Geräteportals verfügbar. Führen Sie die folgenden Schritte aus, um dieses Tool zu verwenden:
* Stellen Sie sicher, dass Sie für 20H1 oder höher aktiviert sind– nach September 2019 bedeutet dies, dass Sie unser Insider-Programm verwenden.
* Aktivieren Sie die Windows Geräteportal (WDP) mithilfe dieser [Anweisungen.](/windows/uwp/debug-test-perf/device-portal-desktop)
* Schließen Sie eine Windows Mixed Reality HMD an, von der Sie entweder eine vorhandene Karte herunterladen oder eine neue Karte importieren möchten.
* Navigieren Sie in Ihrem Browser Ihrer Wahl zu WDP, indem Sie die URL verwenden, die auf dem Bildschirm mit den Einstellungen angegeben ist.
    * Navigieren Sie dort zum Abschnitt "Mixed Reality", und wählen Sie "Karten-Manager" aus.
    * Sie können jetzt die Schaltfläche "Herunterladen" verwenden, um eine vorhandene Karte vom Computer zu exportieren.
    * Sie können die Schaltfläche "Hochladen einer Zuordnungsdatei" verwenden, um eine Karte aus einem vorherigen Export (möglicherweise auf einem anderen Computer) zu importieren.
    * Sie können "Import" verwenden, um dem System die Verwendung dieser Zuordnung für diese HMD auf diesem Computer zu ermöglichen.

> [!NOTE] 
> Zuvor war es möglich, das Spatial Data Packager-Tool zu verwenden. Dieses Tool wurde jedoch ursprünglich als nicht unterstützt veröffentlicht und ist jetzt offiziell veraltet und funktioniert nicht mehr auf 20H1. Verwenden Sie stattdessen das [Karten-Manager-Tool](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) im Posteingang, wie oben beschrieben. 

### <a name="tracking"></a>Tracking

F: Wie funktioniert die Nachverfolgungstechnologie in den Windows Mixed Reality Headsets?  

Mixed Reality nutzt dieselbe Nachverfolgungstechnologie wie die HoloLens. Weitere Informationen zum Inside-Out-Nachverfolgungssystem finden Sie in der Dokumentation [hier.](/windows/mixed-reality/enthusiast-guide/tracking-system)

Eine Beschreibung der Funktionsweise des räumlichen Zuordnungssystems auf höherer Ebene finden Sie [hier.](../design/spatial-mapping.md)

**F: Gibt es bewährte Methoden zum Abrufen eines zuverlässigen Nachverfolgungsvolumes?**

Informationen zum optimalen Konfigurieren der Umgebung für die Erfolgreiche Nachverfolgung finden Sie in diesem [Beitrag.](/hololens/hololens-environment-considerations)

**F: Gibt es bestimmte Feinheiten bei der Nachverfolgung in Lagerskalierungsbereichen oder Optimierungen, die berücksichtigt werden müssen?**

A: Die folgenden Methoden können dabei helfen, ein zuverlässigeres Nachverfolgungsvolume zu erhalten:  

Die Bereitstellung verschiedener Features im Raum, die sich an mehreren Positionen überschneiden, hilft dem Nachverfolgungssystem, eine feste Sperre zu erhalten. Stellen Sie sich zufällige Farbsplatter und Schraffur vor, anstatt durchgehende Konturstillinien zu verwenden. 

Minimieren Sie nach Möglichkeit den dynamischen Beleuchtungsbereich in Ihrem Bereich. Die Überwachungskameras auf unseren Mixed Reality HMDs sind nicht HDR und verfügen über AGC (auto gain) und AEC (auto exposure) für unterschiedliche Beleuchtung. Je nach Verteilung des Oberflächenlichts, der Muster und des Kontrasts können AGC oder AEC zu dem Schluss kommen, dass Sie sich in einem viel weißen oder schwarzen Raum befinden, der Ihre Features ausdrücken kann, die sich in der entgegengesetzten "Farbe" befinden können. Wenn Sie versuchen, ein inneres Bild vor einem äußeren Fenster mit hellem Sommerlicht zu erstellen und die Belichtung so anzupassen, dass Sie Details außerhalb sehen können, ist alles im Inneren unterbelichtet und schwarz. Wenn sie für "inside" festgelegt ist, ist alles außerhalb jetzt überbelichtet und weiß.  

Spotlights in einem Raum (sogar Mehraufwand), die angezeigt werden, wenn Überwachungskameras manchmal Fehler darstellen können, was die AEC/AGC der Überwachungskameras verwirren kann. Flache/diffuse Beleuchtung ist hilfreich.  

### <a name="mixed-reality-cloud-services-and-azure"></a>MIXED REALITY-CLOUDDIENSTE UND AZURE 

**F: Wie kann Microsoft Azure mein Unternehmen bei der Skalierung unterstützen?**

A: Azure-basierte Standort- und Remoteverwaltung kann Ihrem Unternehmen helfen, datengesteuert zu sein, Betriebskosten zu senken und die Bereitstellung an vorhandenen und neuen Standorten zu skalieren. Azure-Clouddienste wie Azure Storage, Azure Functions, App Service, Azure-Netzwerk und IOT Hub können bei den folgenden Anwendungsfällen hilfreich sein:  

Remotegerätebereitstellung & Verwaltung 

Real-Time Onsite Analytics 

Intelligent Adaptable LBE Gaming 

LBE-Inhaltsstreaming und -bereitstellung 

LBE Player Preference Heatmap 

LBE-Reservierungs- und -Reservierungssystem 

**F: Ich entwickele ein räumliches MMOG für die Bereitstellung über einen großen Speicherbedarf. Welche Dienste helfen mir bei der Verwaltung meiner Inhalte und Objektpersistenz?**

A: Azure Spatial Anchors ist ein neuer Mixed Reality-Dienst, der Mixed Reality-Benutzeroberflächen mit mehreren Benutzern auf HoloLens-, iOS- und Android-Geräten ermöglicht. Weitere Informationen zu Azure Spatial Anchors finden Sie [hier.](https://azure.microsoft.com//services/spatial-anchors/)

**Q. Unser Veranstaltungsort ist auf Multiplayererfahrungen spezialisiert, und ich möchte unsere Entwicklungszeit auf Inhalte und Front-End-Entwicklung konzentrieren. Gibt es Angebote, mit denen ich die Back-End-Entwicklung starten oder auslagern kann?**

A: Azure PlayFab ist eine vollständige Back-End-Plattform für Live-Spiele. Weitere Informationen dazu finden Sie [hier.](https://playfab.com/)

### <a name="misc"></a>Sonstiges

**F: Ich verwende SteamVR, um meine Erfahrungen bereitzustellen. Funktioniert Windows Mixed Reality mit SteamVR?**

A: Windows Mixed Reality für SteamVR ermöglicht Benutzern das Ausführen von SteamVR-Erfahrungen auf Windows Mixed Reality immersiven Headsets. Weitere Informationen zu SteamVR mit WMR finden Sie [hier.](/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)

### <a name="support-and-community"></a>Support und Community  

Wir verfügen über einige hilfreiche Ressourcen, die Sie bei der Zusammenarbeit mit Experten in unserem Team unterstützen, Unterstützung bei der Problembehandlung erhalten und zur umfassenderen Mixed Reality-Entwicklercommunity beitragen können.  

Wenn Probleme mit öffentlich veröffentlichten Features auftreten, melden Sie einen Fehler mit Feedback-Hub. Eine Anleitung finden Sie auf dieser [Seite.](/windows/mixed-reality/enthusiast-guide/filing-feedback)

Um weitere Hilfe bei der Problembehandlung bei WMR zu erhalten, stellen Sie eine [Supportanfrage](https://support.microsoft.com//supportforbusiness/productselection?sapId=96bfb202-bc79-741b-bf7a-774d8b767782) an unser Kundensupportteam.

Treten Sie unserem HoloDevelopers Slack-Kanal bei, um mit den Mixed Reality-Entwicklern und Experten zu interagieren: [aka.ms/holodevelopers](https://aka.ms/holodevelopers)

Twitter: Folgen Sie unserem Mixed Reality Developer Relations-Team, um Neuigkeiten, Ereignisse und Updates zu erhalten. @MxdRealityDev 

Wenn Sie sich in oder um San Francisco bewegen, ist beim Microsoft Reactor immer etwas los. Unseren Kalender mit Ereignissen finden Sie [hier.](https://developer.microsoft.com//reactor/Location/San%20Francisco)
