---
title: Senden einer App an den Microsoft Store
description: Hier erfahren Sie mehr über den Prozess des Verpackens, Testens und Übermittelns Ihrer Mixed Reality-Apps an Microsoft Store.
author: hferrone
ms.author: mazeller
ms.date: 11/13/2020
ms.topic: article
keywords: Microsoft Store, HoloLens, immersive Headsets, App, UWP, Übermitteln, Übermitteln, Filter, Metadaten, Systemanforderungen, Schlüsselwörter, Wack, Zertifizierung, Paket, Appx, Bluetooth, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 5ea0d48b96ff91f51ff565c652d5ec294e994692dcc7881e626ea7817b05d876
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197721"
---
# <a name="submitting-an-app-to-the-microsoft-store"></a>Senden einer App an den Microsoft Store

> [!IMPORTANT]
> Wenn Sie eine Unreal-Anwendung übermitteln, stellen Sie sicher, dass Sie die Veröffentlichungsanweisungen **[befolgen,](../develop/unreal/unreal-publishing-to-store.md)** bevor Sie fortfahren.

## <a name="prerequisites"></a>Voraussetzungen

Sowohl [HoloLens](/hololens/hololens1-hardware) als auch der Windows 10 PC, der Ihr [immersives Headset](../discover/immersive-headset-hardware-details.md) an stromt, führen Universelle Windows Plattform-Apps aus. Unabhängig davon, ob Sie eine App übermitteln, die HoloLens, PC oder beides unterstützt, wird die [App-Übermittlung](https://partner.microsoft.com/dashboard)Partner Center.

Wenn Sie noch kein Entwicklerkonto Partner Center [haben,](https://developer.microsoft.com/store/register) registrieren Sie sich für ein Konto, bevor Sie mit dem Projekt arbeiten. Weitere Informationen zu Übermittlungsrichtlinien und Prüflisten finden Sie in diesem Artikel [zu App-Übermittlungen.](/windows/uwp/publish/app-submissions)

> [!IMPORTANT]
> Sie können keine Anwendungen an die Microsoft Store übermitteln, wenn Ihr Partner Center-Entwicklerkonto die Überprüfung der Überprüfung des Arbeitsplatzes nicht abfing. Wenden Sie sich an Partner Center [Supportteam,](https://developer.microsoft.com/windows/support) um weitere Informationen zu erhalten.

## <a name="packaging-a-mixed-reality-app"></a>Packen einer Mixed Reality-App

Es gibt mehrere Schritte zum Packen einer Mixed Reality Anwendung, darunter:

* Korrektes Vorbereiten aller Imageressourcen
* Auswählen des kachelbilds, das in der HoloLens Startmenü
* Festlegen des Ziels und der Windows für die App
* Festlegen der Zielgerätefamilien in den App-Abhängigkeiten
* Hinzufügen von Metadaten zum Zuordnen der App zum Microsoft Store
* Erstellen eines Uploadpakets

Jede dieser Übermittlungsphasen wird in einem eigenen Abschnitt weiter unten behandelt. Es wird empfohlen, sie sequenziell zu durchlaufen, damit Sie bei Ihrem ersten Übermittlungsversuch keine Auslassungsversuche machen.

### <a name="prepare-image-assets-included-in-the-appx"></a>Vorbereiten von Imageressourcen, die in appx enthalten sind

Die folgenden Imageressourcen sind erforderlich, damit die AppX-Erstellungstools Ihre Anwendung in einem AppX-Paket erstellen können, das für die Übermittlung an die Microsoft Store. Weitere Informationen zu Richtlinien für [Kachel- und Symbolressourcen](/windows/uwp/app-resources/images-tailored-for-scale-theme-contrast) finden Sie auf MSDN.

| Erforderliches Asset | Empfohlene Skalierung | Bildformat | Wo wird das Objekt angezeigt? | 
|----------|----------|----------|------------------|
| Square 71x71-Logo | Beliebig |  PNG | – | 
| Square 150x150 Logo | 150 x 150 (100 % Skalierung) oder 225 x 225 (150 % Skalierung) | PNG | Startpins und Alle Apps (wenn 310x310 nicht angegeben ist), Store Suchvorschläge, Store Listing Page, Store Browse, Store Search | 
|  Wide 310x150 Logo |  Beliebig  |  PNG  |  – | 
|  Store-Logo |  75 x 75 (150 % Skalierung)  |  PNG  |  Partner Center, Berichts-App, Schreiben einer Überprüfung, Meine Bibliothek | 
|  Begrüßungsbildschirm |  930 x 450 (150 % Skalierung)  |  PNG  |  2D-App-Startfeld (Slate) | 

Wenn Sie für die Entwicklung HoloLens, gibt es weitere empfohlene Ressourcen, die Sie nutzen können:

| Empfohlene Ressourcen | Empfohlene Skalierung | Wo wird das Objekt angezeigt? | 
|----------|----------|----------|
|  Square 310x310 Logo |  310 x 310 (150 % Skalierung) |  Startpins und Alle Apps | 

### <a name="live-tile-requirements"></a>Live-Kachel Anforderungen

Der Startmenü auf HoloLens verwendet standardmäßig das größte enthaltene Quadratkachelbild. Von Microsoft veröffentlichte Apps verfügen über ein optionales 3D-Startfeld, das Sie Ihrer App hinzufügen können, indem Sie die Implementierungsanweisungen für [das 3D-App-Startfeld](implementing-3d-app-launchers.md) befolgen.

### <a name="specifying-target-and-minimum-version-of-windows"></a>Angeben der Ziel- und Mindestversion Windows

Wenn Ihre Mixed Reality-App Features enthält, die für eine Windows-Version spezifisch sind, ist es wichtig, die unterstützten Ziel- und Mindestversionen der Plattform anzugeben.

**Achten Sie besonders auf Apps, die Windows Mixed Reality [immersive Headsets](../discover/immersive-headset-hardware-details.md)verwenden, die mindestens die Windows 10 Fall Creators Update (10.0; Build 16299), um ordnungsgemäß zu funktionieren.**

Sie werden aufgefordert, das Ziel und die Mindestversion von Windows festlegen, wenn Sie eine neue universelle Windows Project in Visual Studio. Für vorhandene Projekte können Sie diese Einstellung im **Menü Project**  ändern, indem Sie unten im Dropdownmenü die<>-Eigenschaften Ihres App-Namens auswählen.

![Festlegen von Mindest- und Zielplattformversionen in Visual Studio 2019](images/visual-studio-min-version-500px.png)<br>
*Festlegen von Mindest- und Zielplattformversionen in Visual Studio*

### <a name="specifying-target-device-families"></a>Angeben von Zielgerätefamilien

Windows Mixed Reality -Anwendungen (sowohl für [HoloLens](/hololens/hololens1-hardware) als auch [für immersive Headsets)](../discover/immersive-headset-hardware-details.md)sind Teil der universellen Windows-Plattform, sodass jedes App-Paket mit einem **Windows. Die universelle** [Zielgerätefamilie](/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily) kann auf virtuellen HoloLens oder Windows 10 mit immersiven Headsets ausgeführt werden. Wenn Sie in Ihrem App-Manifest keine Zielgerätefamilie angeben, können Sie Ihre App versehentlich bis zu unbeabsichtigten Windows 10 öffnen. Führen Sie die folgenden Schritte aus, um die beabsichtigte Windows 10-Gerätefamilie anzugeben. Überprüfen Sie dann, ob Sie die richtigen Gerätefamilien festgelegt haben, wenn Sie Ihr [App-Paket in Partner Center](submitting-an-app-to-the-microsoft-store.md#submitting-your-mixed-reality-app-to-the-store) für die Microsoft Store hochladen.

* Um dieses Feld in Visual Studio, klicken Sie mit der rechten Maustaste auf **Package.appxmanifest,** wählen Sie Code anzeigen **aus,** und suchen Sie dann nach dem Feld **TargetDeviceFamily Name.** Standardmäßig sollte sie wie der folgende Eintrag aussehen:

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

* Wenn Sie eine  HoloLens-App erstellen, können Sie sicherstellen, dass sie nur auf HoloLens installiert ist, indem Sie die Zielgerätefamilie auf **Windows. Holographic**: 

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

* Wenn Ihre  App eine HoloLens 2-Funktionalität erfordert, z. B. Augen- oder Handverfolgung, können Sie sicherstellen, dass sie auf Windows-Versionen 18362 oder höher ausgerichtet ist, indem Sie die Zielgerätefamilie auf **Windows. Holographic** mit **einer MinVersion** von 10.0.18362.0:

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.18362.0" MaxVersionTested="10.0.18362.0" />
</Dependencies>
```

* Wenn Ihre App für Windows Mixed Reality immersive **Headsets** erstellt wird, können Sie sicherstellen, dass sie nur auf Windows 10-PCs mit dem Windows 10 Fall Creators Update installiert ist (für Windows Mixed Reality erforderlich), indem Sie die Zielgerätefamilie auf **Windows. Desktop** mit **einer MinVersion** von 10.0.16299.0:

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
</Dependencies>
```

* Wenn Ihre App auf immersiven **Headsets** von HoloLens und **Windows Mixed Reality** ausgeführt werden soll, können Sie sicherstellen, dass die App nur für diese beiden Gerätefamilien verfügbar ist, und gleichzeitig sicherstellen, dass jedes Ziel über die richtige mindeste Windows-Version verfügt, indem Sie eine Zeile für jede Zielgerätefamilie mit der jeweiligen MinVersion verwenden:

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

Weitere Informationen zur Ausrichtung auf Gerätefamilien finden Sie in der [UWP-Dokumentation zu TargetDeviceFamily.](/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily)

### <a name="associate-app-with-the-store"></a>Zuordnen der App zum Store

Wenn Sie Ihre App dem -Microsoft Store zuordnen, werden die folgenden Werte in die manifestdatei der aktuellen lokalen App heruntergeladen:

* Anzeigename des Pakets
* Paketname
* Herausgeber-ID
* Anzeigename des Herausgebers
* Version

Wenn Sie die Standarddatei package.appxmanifest mit Ihrer eigenen benutzerdefinierten .xml-Datei überschreiben, können Sie Ihre App nicht dem Microsoft Store. Das Zuordnen einer benutzerdefinierten Manifestdatei zum Store führt zu einer Fehlermeldung.

Sie können Kauf- und Benachrichtigungsszenarien auch testen, indem Sie zu Ihrer Visual Studio-Lösung Project > Store > App **dem** Store.

### <a name="creating-an-upload-package"></a>Erstellen eines Uploadpakets

Befolgen Sie die Richtlinien [unter Packaging Universal Windows apps for Windows 10](/previous-versions/windows/apps/hh454036(v=vs.140)#Anchor_2).

Der letzte Schritt beim Erstellen eines Uploadpakets ist die Validierung des Pakets mit dem [Windows App Certification Kit](#windows-app-certification-kit).

Wenn Sie ein HoloLens-spezifisches Paket zu einem vorhandenen Produkt hinzufügen, das in anderen Windows 10-Gerätefamilien verfügbar ist, achten Sie auf: 

* [Wie sich Versionsnummern auf die Pakete auswirken können, die an bestimmte Kunden übermittelt werden](/windows/uwp/publish/package-version-numbering)
* [Verteilen von Paketen auf verschiedene Betriebssysteme](/windows/uwp/publish/guidance-for-app-package-management)

Die allgemeine Anleitung ist, dass das Paket mit der höchsten Versionsnummer für ein Gerät das Paket ist, das von der Store.

In einem Szenario, in dem es eine **Windows. Universelles** Paket und **ein Windows. Holographic-Paket** und Windows. Universal package has a higher version number, a HoloLens user will download the higher version number Windows. Universelles Paket anstelle des Windows. Holographic-Paket. 

In Fällen, in denen das oben genannte Szenario nicht das Ergebnis ist, das Sie suchen, gibt es mehrere verfügbare Lösungen:

* Stellen Sie sicher, dass Ihre plattformspezifischen Pakete, z. B. Windows. Holographic, haben immer eine höhere Versionsnummer als Ihre plattformunabhängigen Pakete wie Windows. Universal
* Verpacken Sie Apps nicht als Windows. Universell, wenn Sie auch plattformspezifische Pakete haben, verpacken Sie stattdessen die Windows. Universelles Paket für die spezifischen Plattformen, auf der es verfügbar sein soll
* Erstellen Sie eine einzelne Windows. Universelles Paket, das auf allen Plattformen funktioniert. Die Unterstützung für diese Option ist derzeit nicht gut, daher werden die oben genannten Lösungen empfohlen.

>[!NOTE]
> Um Ihre App sowohl auf HoloLens (1. Generation) als auch auf HoloLen 2 zu unterstützen, müssen Sie zwei App-Pakete hochladen. eine mit x86 für HoloLens (1. Generation) und eine mit ARM oder ARM64 für HoloLens 2. 
> 
> Wenn Sie sowohl ARM als auch ARM64 in Ihr Paket einschließen, wird die ARM64-Version auf HoloLens 2 verwendet. 

>[!NOTE]
> Sie können ein einzelnes Paket deklarieren, das auf mehrere Zielgerätefamilien anwendbar ist.

## <a name="testing-your-app"></a>Testen der App

### <a name="windows-app-certification-kit"></a>Zertifizierungskit für Windows-Apps

Wenn Sie App-Pakete erstellen, die über Visual Studio an Partner Center übermittelt werden sollen, werden Sie vom Assistenten zum Erstellen von App-Paketen aufgefordert, das Windows App Certification Kit für die erstellten Pakete auszuführen. Um einen reibungslosen Übermittlungsprozess an den Store zu erhalten, ist es am besten, zu überprüfen, ob die lokale Kopie Ihrer App die Tests des [Windows App Certification Kit](/previous-versions/windows/apps/jj657973(v=win.10)) bestanden hat, bevor sie an den Store übermittelt werden. Das Ausführen des Windows App Certification Kit auf einem Remote-HoloLens wird derzeit nicht unterstützt.

### <a name="run-on-all-targeted-device-families"></a>Ausführung auf allen Zielgerätefamilien

Mit dem Windows Universal Platform können Sie eine einzelne Anwendung erstellen, die in allen Windows 10 Gerätefamilien ausgeführt wird. Es garantiert jedoch nicht, dass universelle Windows-Apps nur für alle Gerätefamilien funktionieren. Es ist wichtig, Ihre App für jede ihrer ausgewählten Gerätefamilien zu [testen,](../develop/platform-capabilities-and-apis/testing-your-app-on-hololens.md) um eine gute Erfahrung zu gewährleisten.

## <a name="submitting-your-mixed-reality-app-to-the-store"></a>Übermitteln Ihrer Mixed Reality-App an den Store

Wenn Sie eine Mixed Reality-App übermitteln, die auf einem Unity-Projekt basiert, sehen Sie sich zuerst dieses [Video](https://channel9.msdn.com/Blogs/One-Dev-Minute/How-to-publish-your-Unity-game-as-a-UWP-app) an.

Im Allgemeinen entspricht das Übermitteln einer Windows Mixed Reality-App, die auf HoloLens oder immersiven Headsets funktioniert, der Übermittlung einer beliebigen UWP-App an die Microsoft Store. Nachdem Sie [Ihre App erstellt](/windows/uwp/publish/create-your-app-by-reserving-a-name)haben, indem Sie ihren Namen reserviert haben, befolgen Sie die Checkliste für die [UWP-Übermittlung.](/windows/uwp/publish/app-submissions)

Eine der ersten Dinge, die Sie tun, ist die [Auswahl einer Kategorie und Unterkategorie](/windows/uwp/publish/category-and-subcategory-table) für Ihre Mixed Reality Erfahrung. Es ist wichtig, dass Sie **die genaueste Kategorie für Ihre App auswählen.** Kategorien helfen Dabei, Ihre Anwendung in den richtigen Store Kategorien zu unterteilen und sicherzustellen, dass sie mit relevanten Suchabfragen angezeigt wird. **Das Auflisten Ihres VR-Titels als Spiel führt nicht zu einer besseren Gefährdung Für Ihre App** und verhindert möglicherweise, dass sie in Kategorien angezeigt wird, die besser geeignet und weniger ungenannt sind.

Es gibt jedoch vier wichtige Bereiche im Übermittlungsprozess, in denen Sie Mixed Reality spezifische Auswahl treffen möchten:
1. Im Abschnitt **[Produktdeklarationen](submitting-an-app-to-the-microsoft-store.md#mixed-reality-product-declarations)** unter [Eigenschaften](/windows/uwp/publish/enter-app-properties).
2. Im Abschnitt **[Systemanforderungen](submitting-an-app-to-the-microsoft-store.md#mixed-reality-system-requirements)** unter [Eigenschaften](/windows/uwp/publish/enter-app-properties).
3. Im Abschnitt Verfügbarkeit der **[Gerätefamilie](submitting-an-app-to-the-microsoft-store.md#device-family-availability)** unter [Pakete](/windows/uwp/publish/upload-app-packages).
4. In mehreren der **[Store Auflisten von Seitenfeldern.](submitting-an-app-to-the-microsoft-store.md#store-listing-page)**

### <a name="mixed-reality-product-declarations"></a>Mixed Reality Produktdeklarationen

Auf der Seite **[Eigenschaften](/windows/uwp/publish/enter-app-properties)** des App-Übermittlungsprozesses finden Sie mehrere Optionen im Zusammenhang mit Mixed Reality im Abschnitt **[Produktdeklarationen.](/windows/uwp/publish/app-declarations)**

![Mixed Reality Produktdeklarationen](images/product-declarations-900px.png)<br>
Mixed Reality Produktdeklarationen

Zunächst müssen Sie die Gerätetypen identifizieren, für die Ihre App eine Mixed Reality bietet. Durch die Identifizierung von Gerätetypen wird sichergestellt, dass Ihre App in Windows Mixed Reality Sammlungen im Store enthalten ist.

Neben "This experience is designed for Windows Mixed Reality on:"
* Aktivieren Sie das **Kontrollkästchen PC,** wenn Ihre App eine VR-Erfahrung bietet, wenn ein immersives Headset mit dem PC des Benutzers verbunden ist. Es wird empfohlen, dieses Kontrollkästchen zu aktivieren, ob Ihre App ausschließlich auf einem immersiven Headset ausgeführt werden soll oder ob es sich um ein PC-Standardspiel oder eine App handelt, die einen Mixed Reality Modus oder Bonusinhalte anbietet, wenn ein Headset verbunden ist.
* Aktivieren Sie das **Kontrollkästchen HoloLens** nur, wenn Ihre App eine holografische Erfahrung bietet, wenn sie auf HoloLens ausgeführt wird.
* Aktivieren Sie **beide** Kontrollkästchen, wenn Ihre App auf beiden Gerätetypen eine Mixed Reality bietet.

Wenn Sie oben "PC" ausgewählt haben, sollten Sie "Mixed Reality Setup" (Aktivitätsebene) festlegen. Dies gilt nur für Mixed Reality Funktionen, die auf PCs ausgeführt werden, die mit immersiven Headsets verbunden sind, da Mixed Reality Apps auf HoloLens weltweit ausgeführt werden und der Benutzer während des Setups keine Grenze definiert.
* Wählen Sie **Seated + standing (Gesetzt + stehend)** aus, wenn Sie Ihre App so entworfen haben, dass der Benutzer an einer Position bleibt. Beispielsweise in einem Spiel, in dem Sie die Kontrolle über ein Flugzeug-Cockpit haben.
* Wählen Sie **Alle Benutzeroberflächen** aus, wenn Ihre App mit der Absicht entworfen wurde, dass der Benutzer innerhalb einer festgelegten Grenze durchläuft, die während des Setups definiert wurde. Dies kann beispielsweise ein Spiel sein, bei dem Sie angriffesbehinderend und entschüben.

### <a name="mixed-reality-system-requirements"></a>Mixed Reality Systemanforderungen

Auf der Seite **[Eigenschaften](/windows/uwp/publish/enter-app-properties)** des App-Übermittlungsprozesses finden Sie im Abschnitt **[Systemanforderungen](/windows/uwp/publish/enter-app-properties#system-requirements)** mehrere Optionen im Zusammenhang mit Mixed Reality.

![Systemanforderungen](images/system-reqs-800px.png)<br>
Systemanforderungen

In diesem Abschnitt identifizieren Sie mindestens erforderliche Hardware und empfohlene (optionale) Hardware für Ihre Mixed Reality-App.

**Eingabehardware:**

Verwenden Sie die Kontrollkästchen, um potenziellen Kunden mitzuteilen, ob Ihre App **Mikrofon** für [Spracheingaben,](../design/voice-input.md) **[Xbox-Controller oder Gamepad](../discover/hardware-accessories.md#bluetooth-gamepads)** oder **[Windows Mixed Reality Motion-Controller](../design/motion-controllers.md)** unterstützt. Diese Informationen werden auf der Produktdetailseite Ihrer App im Store angezeigt und helfen Ihrer App, in die entsprechenden App-/Spielsammlungen aufgenommen zu werden. Beispielsweise kann eine Sammlung für alle Spiele vorhanden sein, die Motion-Controller unterstützen.

Denken Sie daran, Kontrollkästchen für "Mindesthardware" oder "empfohlene Hardware" für Eingabetypen auszuwählen. 

Beispiel: 
* Wenn Ihr Spiel Motion-Controller erfordert, aber Spracheingaben per Mikrofon akzeptiert, aktivieren Sie das Kontrollkästchen "Mindesthardware" neben "Windows Mixed Reality Motion Controllers", aber das Kontrollkästchen "empfohlene Hardware" neben "Mikrofon". 
* Wenn Ihr Spiel entweder mit einem Xbox-Controller, einem Gamepad oder einem Motion-Controller wiedergegeben werden kann, können Sie das Kontrollkästchen "Mindesthardware" neben "Xbox-Controller oder Gamepad" aktivieren und das Kontrollkästchen "empfohlene Hardware" neben "Windows Mixed Reality Motion Controllers" aktivieren, da Motion-Controller wahrscheinlich einen Schritt nach oben im Gamepad bieten.

**Windows Mixed Reality immersive Headset:**

Die Angabe, ob ein immersives Headset für die Verwendung Ihrer App erforderlich oder optional ist, ist für die Kundenzufriedenheit und Bildung entscheidend.

Wenn Ihre App *nur* über ein immersives Headset verwendet werden kann, aktivieren Sie das Kontrollkästchen "Mindesthardware" neben "Windows Mixed Reality immersives Headset". Dies wird auf der Produktdetailseite Ihrer App in Store als Warnung über der Schaltfläche "Kaufen" angezeigt, damit Kunden nicht glauben, dass sie eine App kaufen, die auf ihrem PC wie eine herkömmliche Desktop-App funktioniert.

Wenn Ihre App wie eine herkömmliche PC-App auf dem Desktop ausgeführt wird, aber eine VR-Erfahrung bietet, wenn ein immersives Headset verbunden ist (unabhängig davon, ob der vollständige Inhalt Ihrer App verfügbar ist oder nur ein Teil), aktivieren Sie das Kontrollkästchen "Empfohlene Hardware" neben "Windows Mixed Reality immersives Headset". Über der Schaltfläche "Kaufen" auf der Produktdetailseite Ihrer App wird keine Warnung angezeigt, wenn Ihre App als herkömmliche Desktop-App ohne verbundenes immersives Headset fungiert.

**PC-Spezifikationen:**

Wenn Sie möchten, dass Ihre App so viele Windows Mixed Reality Immersive Headset-Benutzer wie möglich erreicht, [richten](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) Sie die PC-Spezifikationen für [Windows Mixed Reality PCs mit integrierter Grafik](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)an.

Unabhängig davon, ob Ihre Mixed Reality-App auf die Mindestanforderungen Windows Mixed Reality PC abzielt oder eine bestimmte PC-Konfiguration wie die dedizierte GPU eines [Windows Mixed Reality Ultra-PCs]( https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines benötigt, sollten Sie die relevanten PC-Spezifikationen in der Spalte "Mindesthardware" hinzufügen.

Wenn Ihre Mixed Reality-App für eine bessere Leistung konzipiert ist oder Grafiken mit höherer Auflösung auf einer bestimmten PC-Konfiguration oder -Grafikkarte bietet, sollten Sie die relevanten PC-Spezifikationen in die Spalte "Empfohlene Hardware" einfügen.

Dies gilt nur, wenn Ihre Mixed Reality-App ein immersives Headset verwendet, das mit einem PC verbunden ist. Wenn Ihre Mixed Reality-App nur auf HoloLens ausgeführt wird, müssen Sie keine PC-Spezifikationen angeben, da HoloLens nur über eine Hardwarekonfiguration verfügt.

### <a name="device-family-availability"></a>Verfügbarkeit von Gerätefamilien

Wenn Sie [Ihre App ordnungsgemäß](https://docs.microsoft.com/windows/uwp/publish/app-package-requirements) in Visual Studio gepackt haben, sollte beim Hochladen auf der Seite Pakete eine Tabelle mit den verfügbaren Gerätefamilien erzeugt werden.

![Verfügbarkeitstabelle der Gerätefamilie](images/device-family-table-900px.png)<br>
Verfügbarkeitstabelle der Gerätefamilie

Wenn Ihre Mixed Reality-App auf immersiven Headsets funktioniert, sollte mindestens "Windows 10 Desktop" in der Tabelle ausgewählt werden. Wenn Ihre Mixed Reality-App auf HoloLens funktioniert, sollte mindestens "Windows 10 Holographic" ausgewählt werden. Wenn Ihre App sowohl auf Windows Mixed Reality Headsettypen ausgeführt wird, sollten sowohl "Windows 10 Desktop" als auch "Windows 10 Holographic" ausgewählt werden.

>[!TIP]
>Vielen Entwicklern treten Fehler auf, wenn sie das Paket ihrer App hochladen, was auf Nichtübereinstimmungen zwischen dem Paketmanifest und Ihren App-/Herausgeberkontoinformationen in Partner Center. Diese Fehler können häufig vermieden werden, indem Sie sich bei Visual Studio mit demselben Konto anmelden, das Ihrem Windows Entwicklerkonto zugeordnet ist (das Konto, das Sie zum Anmelden bei Partner Center verwenden). Wenn Sie dasselbe Konto verwenden, können Sie Ihre App ihrer Identität im Microsoft Store zuordnen, bevor Sie sie packen.

![Zuordnen Ihrer App zum Microsoft Store](images/associate-your-app-700px.png)<br>
Zuordnen Ihrer App zum Microsoft Store in Visual Studio

### <a name="store-listing-page"></a>Store-Auflistungsseite

Auf der [Store-Auflistungsseite](/windows/uwp/publish/create-app-store-listings) des App-Übermittlungsprozesses gibt es mehrere Stellen, an denen Sie nützliche Informationen zu Ihrer Mixed Reality-App hinzufügen können.

>[!IMPORTANT]
>Um sicherzustellen, dass Ihre App ordnungsgemäß vom Store kategorisiert und für Windows Mixed Reality Kunden erkennbar gemacht wird, sollten Sie **"Windows Mixed Reality"** als einen Ihrer "Suchbegriffe" für die App hinzufügen (Sie finden Suchbegriffe, indem Sie den Abschnitt "Freigegebene Felder" erweitern).

![Hinzufügen Windows Mixed Reality zu Suchbegriffen](images/search-terms-800px.png)<br>
Hinzufügen von "Windows Mixed Reality" zu Suchbegriffen

## <a name="offering-a-free-trial-for-your-game-or-app"></a>Anbieten einer kostenlosen Testversion für Ihr Spiel oder Ihre App

In vielen Fällen verfügen Ihre Kunden nur über eine begrenzte Erfahrung mit virtual reality, bevor sie ein Windows Mixed Reality immersive Headset kaufen. Sie wissen möglicherweise nicht, was sie von intensiven Spielen erwarten sollten, oder sie sind mit ihrem eigenen Komfortschwellenwert in immersiven Erfahrungen vertraut. Viele Kunden können auch ein Windows Mixed Reality immersive Headset auf PCs ausprobieren, die nicht als [Windows Mixed Reality PCs](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)bezeichnet werden. Aus diesem Grund wird dringend empfohlen, eine [kostenlose Testversion](/windows/uwp/publish/set-app-pricing-and-availability#free-trial) für Ihre kostenpflichtige Mixed Reality App oder Ihr Spiel anzubieten.

## <a name="see-also"></a>Siehe auch
* [Was ist Mixed Reality?](../discover/mixed-reality.md)
* [Entwicklung – Übersicht](../develop/development.md)
* [App-Ansichten](../design/app-views.md)
* [Grundlegendes zur Leistung für Mixed Reality](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Leistungs-Empfehlungen für Unity](../develop/unity/performance-recommendations-for-unity.md)
* [Testen Ihrer App auf HoloLens](../develop/platform-capabilities-and-apis/testing-your-app-on-hololens.md)
* [Windows Mixed Reality Mindestrichtlinien für die PC-Hardwarekompatibilität](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)