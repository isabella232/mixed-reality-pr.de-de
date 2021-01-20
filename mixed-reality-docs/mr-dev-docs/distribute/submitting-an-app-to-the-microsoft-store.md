---
title: Senden einer App an den Microsoft Store
description: Erläutert den Prozess der Paket Erstellung, dem Testen und der Übermittlung Ihrer Mixed Reality-apps an den Microsoft Store.
author: hferrone
ms.author: mazeller
ms.date: 11/13/2020
ms.topic: article
keywords: Microsoft Store, hololens, immersive Headsets, APP, UWP, einreichen, Übermittlung, Filter, Metadaten, Systemanforderungen, Schlüsselwörter, Wack, Zertifizierung, Package, AppX, Merchandising, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 8597526d35aa7ac7afadec0dd33fd23ef82d668a
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583887"
---
# <a name="submitting-an-app-to-the-microsoft-store"></a>Senden einer App an den Microsoft Store

> [!IMPORTANT]
> Wenn Sie eine Unreal-Anwendung übermitteln, stellen Sie sicher, dass Sie den **[Veröffentlichungs Anweisungen](../develop/unreal/unreal-publishing-to-store.md)** folgen, bevor Sie fortfahren.

## <a name="prerequisites"></a>Voraussetzungen

Sowohl [hololens](/hololens/hololens1-hardware) als auch der Windows 10-PC, der Ihr [immersives Headset](../discover/immersive-headset-hardware-details.md) antreibt, werden universelle Windows-Plattform-apps ausgeführt. Unabhängig davon, ob Sie eine APP übermitteln, die hololens, PCs oder beides unterstützt, wird die APP-Übermittlung über das [Partner Center](https://partner.microsoft.com/dashboard)übermittelt.

Wenn Sie noch nicht über ein Partner Center-Entwicklerkonto verfügen, [registrieren Sie sich](https://developer.microsoft.com/store/register) für ein Konto, bevor Sie fortfahren. Weitere Informationen zu Übermittlungs Richtlinien und Prüf Listen finden Sie in diesem [Artikel](/windows/uwp/publish/app-submissions)zur Übermittlung von apps.

> [!IMPORTANT]
> Sie können keine Anwendungen an den Microsoft Store übermitteln, wenn Ihr Partner Center-Entwicklerkonto die Überprüfung der Überprüfung nicht besteht. Weitere Informationen erhalten Sie vom Partner Center- [Support Team](https://developer.microsoft.com/windows/support) .

## <a name="packaging-a-mixed-reality-app"></a>Verpacken einer Mixed Reality-App

Es gibt mehrere Schritte zum Packen einer gemischten Reality-Anwendung, einschließlich der folgenden:

* Ordnungsgemäße Vorbereitung aller Image Assets
* Auswählen des Kachel Bilds, das im Startmenü "hololens" angezeigt wird
* Festlegen der Ziel-und Windows-Mindestversion für die APP
* Festlegen der Zielgeräte Familien in den App-Abhängigkeiten
* Hinzufügen von Metadaten zum Zuordnen der APP zum Microsoft Store
* Erstellen eines Uploadpakets

Jede dieser Übermittlungs Stufen wird unten in einem eigenen Abschnitt behandelt. Wir empfehlen Ihnen, Sie nacheinander zu durchlaufen, wenn Sie den ersten Übermittlungs Versuch nicht verlassen.

### <a name="prepare-image-assets-included-in-the-appx"></a>Vorbereiten von Image Assets, die in AppX enthalten sind

Die folgenden Image Ressourcen sind für die AppX-Buildtools erforderlich, um Ihre Anwendung in ein AppX-Paket zu erstellen, das für die Übermittlung an den Microsoft Store erforderlich ist. Weitere Informationen zu den [Richtlinien für Kachel-und Symbol Ressourcen](/windows/uwp/app-resources/images-tailored-for-scale-theme-contrast) finden Sie auf der MSDN-Website.

| Erforderliches Asset | Empfohlene Skalierung | Bildformat | Wo wird das Medienobjekt angezeigt? | 
|----------|----------|----------|------------------|
| Quadratisches Logo 71x71 | Any |  PNG | Nicht zutreffend | 
| Quadratisches Logo 150x150 | 150x150 (100% Skala) oder 225 x 225 (150% Skalierung) | PNG | Start-Pins und alle apps (wenn 310x310 nicht bereitgestellt wird), Store-Suchvorschläge, Store-Listenseite, Store-durchsuchen, Store-Suche | 
|  Breites 310x150-Logo |  Any  |  PNG  |  Nicht zutreffend | 
|  Store-Logo |  75x75 (150% Skalierung)  |  PNG  |  Partner Center, Berichts-APP, Schreiben einer Überprüfung, meine Bibliothek | 
|  Begrüßungsbildschirm |  930x450 (150% Skalieren)  |  PNG  |  2D-App-Startfeld (Slate) | 

Wenn Sie für hololens entwickeln, gibt es weitere empfohlene Ressourcen, die Sie nutzen können:

| Empfohlene Assets | Empfohlene Skalierung | Wo wird das Medienobjekt angezeigt? | 
|----------|----------|----------|
|  Quadratisches Logo 310x310 |  310x310 (150% Skalieren) |  Start-Pins und alle apps | 

### <a name="live-tile-requirements"></a>Live-Kachel Anforderungen

Im Startmenü von hololens wird standardmäßig das größte enthaltene quadratische Kachel Bild verwendet. Von Microsoft veröffentlichte apps verfügen über ein optionales 3D-Start Programm, das Sie Ihrer APP hinzufügen können, indem Sie die Implementierungs Anweisungen für das [3D-App-](implementing-3d-app-launchers.md) Startfeld befolgen

### <a name="specifying-target-and-minimum-version-of-windows"></a>Angeben von Ziel-und Mindestversion von Windows

Wenn Ihre Mixed Reality-App Features enthält, die für eine Windows-Version spezifisch sind, ist es wichtig, die unterstützten Ziel-und mindestplattformversionen anzugeben.

**Achten Sie besonders auf apps, die auf [Windows Mixed Reality-immersive Headsets](../discover/immersive-headset-hardware-details.md)abzielen, die mindestens das Windows 10 Fall Creators Update erfordern (10,0; Build 16299), um ordnungsgemäß zu funktionieren.**

Wenn Sie in Visual Studio ein neues universelles Windows-Projekt erstellen, werden Sie aufgefordert, die Ziel-und Mindestversion von Windows festzulegen. Für vorhandene Projekte können Sie diese Einstellung im Menü **Projekt** ändern, indem Sie<die **> Eigenschaften Ihres App-namens** unten im Dropdown Menü auswählen.

![Festlegen der Versionen der minimal-und Zielplattform in Visual Studio 2019](images/visual-studio-min-version-500px.png)<br>
*Festlegen der Standard-und Ziel Platt Form Versionen in Visual Studio*

### <a name="specifying-target-device-families"></a>Angeben von Zielgeräte Familien

Windows Mixed Reality-Anwendungen (für [hololens](/hololens/hololens1-hardware) und [immersive Headsets](../discover/immersive-headset-hardware-details.md)) sind Teil der universelle Windows-Plattform, sodass jedes app-Paket mit einer **Windows. Universal** - [Zielgeräte Familie](/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily) auf hololens-oder Windows 10-PCs mit immersiven Headsets ausgeführt werden kann. Wenn Sie keine Zielgeräte Familie in Ihrem App-Manifest angeben, können Sie Ihre APP versehentlich auf unbeabsichtigten Windows 10-Geräten öffnen. Führen Sie die folgenden Schritte aus, um die gewünschte Windows 10-Gerätefamilie anzugeben, und [Überprüfen Sie dann, ob Sie die richtigen Gerätefamilien festgelegt haben, wenn Sie das App-Paket im Partner Center hochladen, um Microsoft Store einzureichen.](submitting-an-app-to-the-microsoft-store.md#submitting-your-mixed-reality-app-to-the-store)

* Um dieses Feld in Visual Studio festzulegen, klicken Sie mit der rechten Maustaste auf " **Package. appxmanifest** ", und wählen Sie **Code anzeigen** aus, und suchen Sie dann nach dem Feld **targetdevicefamily Name** . Standardmäßig sollte Sie wie folgt aussehen:

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

* Wenn Sie eine **hololens** -app erstellen, können Sie sicherstellen, dass Sie nur auf hololens installiert ist, indem Sie die Zielgeräte Familie auf **Windows. Holographic** festlegen: 

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

* Wenn Ihre APP **hololens 2** -Funktionen erfordert, wie z. b. Eye oder Hand Verfolgung, können Sie sicherstellen, dass Sie auf Windows-Versionen 18362 oder höher ausgerichtet ist, indem Sie die Zielgeräte Familie auf **Windows. Holographic** mit einer **MinVersion** von 10.0.18362.0 festlegen:

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.18362.0" MaxVersionTested="10.0.18362.0" />
</Dependencies>
```

* Wenn Ihre APP für **Windows Mixed Reality-immersive Headsets** erstellt wurde, können Sie sicherstellen, dass Sie nur auf Windows 10-PCs mit dem Windows 10 Fall Creators Update installiert ist (erforderlich für Windows Mixed Reality), indem Sie die Zielgeräte Familie auf **Windows. Desktop** mit einer **MinVersion** von 10.0.16299.0 festlegen:

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
</Dependencies>
```

* Wenn Ihre APP schließlich sowohl auf **hololens** -als auch in **Windows Mixed Reality-immersiven Headsets** ausgeführt werden soll, können Sie sicherstellen, dass die app nur für diese beiden Gerätefamilien verfügbar ist, und gleichzeitig sicherstellen, dass jedes Ziel über die richtige Mindestversion von Windows verfügt, indem Sie eine Zeile für jede Zielgeräte Familie mit der jeweiligen MinVersion einschließen:

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

Weitere Informationen zur Zielgruppe von Gerätefamilien finden Sie in der [Dokumentation zu targetdevicefamily UWP](/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily).

### <a name="associate-app-with-the-store"></a>App mit Store verknüpfen

Wenn Sie die APP mit der Microsoft Store verknüpfen, werden die folgenden Werte in die aktuelle Projektdatei für das lokale App-Manifest heruntergeladen:

* Anzeigename des Pakets
* Paketname
* Herausgeber-ID
* Anzeigename des Herausgebers
* Version

Wenn Sie die Standarddatei "Package. appxmanifest" mit ihrer eigenen benutzerdefinierten XML-Datei überschreiben, können Sie Ihre APP nicht mit der Microsoft Store verknüpfen. Das Zuordnen einer benutzerdefinierten Manifest-Datei zum Speicher führt zu einer Fehlermeldung.

Sie können auch Kauf-und Benachrichtigungs Szenarien testen, indem Sie zu Ihrer Visual Studio-Projekt Mappe navigieren und **Project > Store auswählen, um die APP dem Store zuzuordnen >**.

### <a name="creating-an-upload-package"></a>Erstellen eines Uploadpakets

Befolgen Sie die Richtlinien unter [Verpacken von universellen Windows-Apps für Windows 10](/previous-versions/windows/apps/hh454036(v=vs.140)#Anchor_2).

Der letzte Schritt beim Erstellen eines Uploadpakets ist das Überprüfen des Pakets mit dem [zertifizierungskit für Windows-apps](#windows-app-certification-kit).

Wenn Sie einem vorhandenen Produkt, das auf anderen Windows 10-Gerätefamilien verfügbar ist, ein hololens-spezifisches Paket hinzufügen, achten Sie auf Folgendes: 

* [Wie sich Versionsnummern auf die Übermittlung von Paketen an bestimmte Kunden auswirken können](/windows/uwp/publish/package-version-numbering)
* [Verteilen von Paketen an verschiedene Betriebssysteme](/windows/uwp/publish/guidance-for-app-package-management)

Die allgemeine Anleitung besteht darin, dass das Paket mit der höchsten Versionsnummer für ein Gerät das Paket ist, das vom Speicher verteilt wird.

In einem Szenario, in dem ein **Windows** . Universal-Paket und ein **Windows. Holographic** -Paket vorhanden sind und das Windows. Universal-Paket eine höhere Versionsnummer aufweist, wird ein hololens-Benutzer die höhere Versionsnummer Windows. Universal Package anstelle des Windows. Holographic-Pakets herunterladen. 

In Fällen, in denen das obige Szenario nicht das gesuchte Ergebnis ist, gibt es mehrere verfügbare Lösungen:

* Stellen Sie sicher, dass Ihre plattformspezifischen Pakete, wie z. b. Windows. Holographic, immer eine höhere Versionsnummer haben als ihre plattformunabhängigen Pakete wie Windows. Universal
* Packen Sie apps nicht als Windows. Universal, wenn Sie auch plattformspezifische Pakete verwenden, und Verpacken Sie stattdessen das Windows. Universal-Paket für die Plattformen, auf denen es verfügbar sein soll.
* Erstellen Sie ein einzelnes Windows. Universal-Paket, das auf allen Plattformen funktioniert. Die Unterstützung für diese Option ist zurzeit nicht groß, da die oben genannten Lösungen empfohlen werden.

>[!NOTE]
> Zur Unterstützung Ihrer APP auf hololens (1. Gen) und hololen 2 müssen Sie zwei App-Pakete hochladen. eine, die x86 für hololens (1. Gen) enthält, und eine, die Arm oder ARM64 für hololens 2 enthält. 
> 
> Wenn Sie sowohl Arm als auch ARM64 in das Paket einschließen, wird die ARM64-Version auf hololens 2 verwendet. 

>[!NOTE]
> Sie können ein einzelnes Paket deklarieren, das auf mehrere Zielgeräte Familien anwendbar ist.

## <a name="testing-your-app"></a>Testen der App

### <a name="windows-app-certification-kit"></a>Zertifizierungskit für Windows-Apps

Wenn Sie App-Pakete erstellen, die über Visual Studio an Partner Center gesendet werden sollen, werden Sie vom Assistenten zum Erstellen von App-Paketen aufgefordert, das zertifizierungskit für Windows-Apps für die erstellten Pakete auszuführen. Um einen reibungslosen Übermittlungs Prozess für den Speicher zu bieten, sollten Sie sicherstellen, dass die lokale Kopie Ihrer APP die [Tests des Zertifizierungs Kits für Windows-apps](/previous-versions/windows/apps/jj657973(v=win.10)) übergibt, bevor Sie Sie an den Store übermitteln. Das Ausführen des zertifizierungskit für Windows-apps auf einem Remote hololens wird derzeit nicht unterstützt

### <a name="run-on-all-targeted-device-families"></a>Auf allen Zielgeräte Familien ausführen

Mit der universellen Windows-Plattform können Sie eine einzelne Anwendung erstellen, die auf allen Windows 10-Gerätefamilien ausgeführt wird. Es ist jedoch nicht gewährleistet, dass universelle Windows-Apps nur für alle Gerätefamilien funktionieren. Es ist wichtig, dass Sie [Ihre APP](../develop/platform-capabilities-and-apis/testing-your-app-on-hololens.md) auf den einzelnen ausgewählten Gerätefamilien testen, um eine gute Leistung zu gewährleisten.

## <a name="submitting-your-mixed-reality-app-to-the-store"></a>Übermitteln Ihrer Mixed Reality-APP an den Store

Wenn Sie eine Mixed Reality-App übermitteln, die auf einem Unity-Projekt basiert, sehen Sie sich dieses [Video](https://channel9.msdn.com/Blogs/One-Dev-Minute/How-to-publish-your-Unity-game-as-a-UWP-app) zuerst an.

Im Allgemeinen ist das Senden einer Windows Mixed Reality-APP, die auf hololens oder immersiven Headsets funktioniert, genauso wie das Übermitteln einer beliebigen UWP-APP an den Microsoft Store. Nachdem Sie [Ihre APP durch reservieren Ihres Namens erstellt](/windows/uwp/publish/create-your-app-by-reserving-a-name)haben, befolgen Sie die [Checkliste für die UWP-Übermittlung](/windows/uwp/publish/app-submissions).

Eine der ersten Schritte ist die [Auswahl einer Kategorie und Unterkategorie](/windows/uwp/publish/category-and-subcategory-table) für ihre gemischte Realität. Es ist wichtig, dass Sie **die genaueste Kategorie für Ihre App auswählen**. Kategorien helfen Ihnen, Ihre Anwendung in die richtigen Store-Kategorien zu stellen und sicherzustellen, dass Sie mithilfe relevanter Such Abfragen angezeigt wird. Das **auflisten Ihres VR-Titels als Spiel führt nicht zu einer besseren Aufmerksamkeit für Ihre APP** und kann verhindern, dass Sie in Kategorien angezeigt wird, die besser geeignet und weniger überfüllt sind.

Es gibt jedoch vier wichtige Bereiche im Übermittlungs Prozess, in denen Sie gemischte Reality-spezifische Auswahl treffen möchten:
1. Im Abschnitt **[Produkt Deklarationen](submitting-an-app-to-the-microsoft-store.md#mixed-reality-product-declarations)** unter [Eigenschaften](/windows/uwp/publish/enter-app-properties).
2. Im Abschnitt " **[System Anforderungen](submitting-an-app-to-the-microsoft-store.md#mixed-reality-system-requirements)** " unter " [Eigenschaften](/windows/uwp/publish/enter-app-properties)".
3. Im Abschnitt **[Gerätefamilien Verfügbarkeit](submitting-an-app-to-the-microsoft-store.md#device-family-availability)** unter [Pakete](/windows/uwp/publish/upload-app-packages).
4. In einigen der Seiten Felder der **[Store-Auflistung](submitting-an-app-to-the-microsoft-store.md#store-listing-page)** .

### <a name="mixed-reality-product-declarations"></a>Mixed Reality-Produkt Deklarationen

Auf der Seite **[Eigenschaften](/windows/uwp/publish/enter-app-properties)** des App-Übermittlungs Prozesses finden Sie im Abschnitt **[Produkt Deklarationen](/windows/uwp/publish/app-declarations)** mehrere Optionen im Zusammenhang mit Mixed Reality.

![Mixed Reality-Produkt Deklarationen](images/product-declarations-900px.png)<br>
Mixed Reality-Produkt Deklarationen

Zunächst müssen Sie die Gerätetypen identifizieren, für die Ihre APP eine gemischte Realität bietet. Die Identifizierung von Gerätetypen stellt sicher, dass Ihre APP in Windows Mixed Reality-Auflistungen im Store enthalten ist.

Neben "Diese Darstellung ist für Windows Mixed Reality konzipiert auf:"
* Aktivieren Sie das Kontrollkästchen **PC** , wenn Ihre APP eine VR-Darstellung bietet, wenn ein immersives Headset mit dem PC des Benutzers verbunden ist. Es wird empfohlen, dieses Kontrollkästchen zu aktivieren, unabhängig davon, ob Ihre APP ausschließlich auf einem immersiven Headset ausgeführt wird oder ob es sich um ein Standard-PC-Spiel oder eine APP handelt, das einen gemischten Reality-Modus oder einen Bonus Inhalt anbietet, wenn ein
* Aktivieren Sie das Feld **hololens** nur dann, wenn Ihre APP in hololens eine holografische Darstellung bietet.
* Aktivieren Sie **beide** Kontrollkästchen, wenn Ihre APP für beide Gerätetypen eine gemischte Realität bietet.

Wenn Sie oben "PC" ausgewählt haben, empfiehlt es sich, das Setup für die gemischte Realität (Aktivitäts Ebene) festzulegen. Dies gilt nur für Umgebungen mit gemischter Realität, die auf PCs ausgeführt werden, die mit immersiven Headsets verbunden sind, da gemischte Reality-apps auf hololens weltweit skaliert sind und der Benutzer während des Setups keine Grenze definiert.
* Wählen Sie **sitzend und stehend** aus, wenn Sie Ihre APP so entworfen haben, dass der Benutzer an einer anderen Position bleiben muss. Beispielsweise in einem Spiel, in dem Sie die Kontrolle über ein Flugzeug Cockpit haben.
* Wählen Sie **alle Erfahrungen** aus, wenn Ihre APP mit der Absicht entworfen wurde, dass der Benutzer innerhalb einer festgelegten Grenze, die während des Setups definiert ist, herumläuft Beispielsweise könnte ein Spiel sein, in dem Sie sich gegen Angriffe gegen Angriffe durchlaufen lassen.

### <a name="mixed-reality-system-requirements"></a>Systemanforderungen für gemischte Realität

Auf der **[Eigenschaften](/windows/uwp/publish/enter-app-properties)** Seite des App-Übermittlungs Vorgangs finden Sie im Abschnitt " **[System Anforderungen](/windows/uwp/publish/enter-app-properties#system-requirements)** " mehrere Optionen im Zusammenhang mit Mixed Reality.

![Systemanforderungen](images/system-reqs-800px.png)<br>
Systemanforderungen

In diesem Abschnitt identifizieren Sie die minimale (erforderliche) Hardware und die empfohlene (optionale) Hardware für Ihre Mixed Reality-app.

**Eingabe Hardware:**

Verwenden Sie die Kontrollkästchen, um potenziellen Kunden mitzuteilen, ob Ihre APP **Mikrofon** für [Spracheingaben](../design/voice-input.md)unterstützt), **[Xbox Controller-oder Gamepad](../discover/hardware-accessories.md#bluetooth-gamepads)**-oder **[Windows Mixed Reality Motion-Controller](../design/motion-controllers.md)**. Diese Informationen werden auf der Produktdetailseite Ihrer APP im Store angezeigt und helfen Ihrer APP, in die entsprechenden App-/spielauflistungen aufgenommen zu werden. Beispielsweise kann eine Sammlung für alle Spiele vorhanden sein, die Motion-Controller unterstützen.

Beachten Sie, dass Sie Kontrollkästchen für "Minimale Hardware" oder "Empfohlene Hardware" für Eingabetypen auswählen. 

Beispiel: 
* Wenn das Spiel Bewegungs Controller erfordert, aber eine Spracheingabe über Mikrofon akzeptiert, aktivieren Sie das Kontrollkästchen "Minimale Hardware" neben "Windows Mixed Reality Motion Controllers", aber das Kontrollkästchen "Empfohlene Hardware" neben "Mikrofon". 
* Wenn Ihr Spiel entweder mit einem Xbox-Controller, Gamepad oder Bewegungs Controllern abgespielt werden kann, aktivieren Sie das Kontrollkästchen "Minimale Hardware" neben "Xbox Controller" oder "Gamepad", und aktivieren Sie das Kontrollkästchen "Empfohlene Hardware" neben "Windows Mixed Reality Motion Controllers", da Bewegungs Controller wahrscheinlich eine Schritt-für-Schritt-Anleitung aus dem Gamepad anbieten.

**Immersives Headset für Windows Mixed Reality:**

Die Angabe, ob ein immersives Headset zur Verwendung Ihrer APP erforderlich ist oder optional ist, ist wichtig für Kundenzufriedenheit und Bildungseinrichtungen.

Wenn Ihre APP *nur* über ein immersives Headset verwendet werden kann, aktivieren Sie das Kontrollkästchen "Minimale Hardware" neben "Windows Mixed Reality-immersives Headset". Dies wird auf der Produktdetailseite Ihrer APP im Store als Warnung über der Schaltfläche "kaufen" angezeigt, sodass Kunden nicht glauben, dass Sie eine APP kaufen, die auf Ihrem PC funktioniert, wie eine herkömmliche Desktop-App.

Wenn Ihre APP auf dem Desktop wie eine herkömmliche PC-app ausgeführt wird, aber eine VR-Benutzer Darstellung bietet, wenn ein immersives Headset verbunden ist (unabhängig davon, ob der vollständige Inhalt Ihrer app verfügbar oder nur ein Teil ist), aktivieren Sie das Kontrollkästchen "Empfohlene Hardware" neben "Windows Mixed Reality-immersives Headset". Über der Schaltfläche kaufen auf der Produktdetailseite Ihrer APP wird keine Warnung angezeigt, wenn Ihre APP als herkömmliche Desktop-App fungiert, ohne dass ein immersives Headset angeschlossen ist.

**PC-Spezifikationen:**

Wenn Sie möchten, dass Ihre APP so viele Windows Mixed Reality-immersive Headset-Benutzer wie möglich erreicht, [richten](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) Sie die PC-Spezifikationen für [Windows Mixed Reality-PCs mit integrierten Grafiken](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)ein.

Unabhängig davon, ob Ihre Mixed Reality-APP die Mindestanforderungen für Windows Mixed Reality-PCs erfüllt oder eine bestimmte PC-Konfiguration benötigt, wie z. b. die dedizierte GPU eines [Windows Mixed Reality Ultra PC] () https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines , sollten Sie die relevanten PC-Spezifikationen in der Spalte "Minimale Hardware" hinzufügen.

Wenn Ihre Mixed Reality-App auf eine bessere Leistung ausgelegt ist oder Grafiken mit höherer Auflösung auf einer bestimmten PC-Konfiguration oder Grafikkarte bietet, sollten Sie die relevanten PC-Spezifikationen in die Spalte "Empfohlene Hardware" einschließen.

Dies gilt nur, wenn Ihre Mixed Reality-App ein immersives Headset verwendet, das mit einem PC verbunden ist. Wenn Ihre Mixed Reality-app nur auf hololens ausgeführt wird, müssen Sie keine PC-Spezifikationen angeben, da hololens nur eine Hardwarekonfiguration aufweist.

### <a name="device-family-availability"></a>Verfügbarkeit von Gerätefamilien

Wenn Sie Ihre APP in Visual Studio [ordnungsgemäß verpackt](https://docs.microsoft.com/windows/uwp/publish/app-package-requirements) haben, sollte das Hochladen auf der Seite Pakete eine Tabelle mit den verfügbaren Gerätefamilien durchführen.

![Verfügbarkeits Tabelle der Gerätefamilie](images/device-family-table-900px.png)<br>
Verfügbarkeits Tabelle der Gerätefamilie

Wenn Ihre Mixed Reality-App auf immersiven Headsets funktioniert, sollte mindestens "Windows 10 Desktop" in der Tabelle ausgewählt werden. Wenn Ihre Mixed Reality-App auf hololens funktioniert, sollte mindestens "Windows 10 Holographic" ausgewählt werden. Wenn Ihre APP in Windows Mixed Reality-Headset-Typen ausgeführt wird, sollten sowohl "Windows 10 Desktop" als auch "Windows 10 Holographic" ausgewählt werden.

>[!TIP]
>Viele Entwickler treten beim Hochladen des App-Pakets im Zusammenhang mit Konflikten zwischen dem Paket Manifest und ihren App-/Herausgeber-Kontoinformationen in Partner Center Fehler auf. Diese Fehler können häufig vermieden werden, indem Sie sich bei Visual Studio mit demselben Konto anmelden, das mit Ihrem Windows-Entwicklerkonto verknüpft ist (das Konto, das Sie zum Anmelden bei Partner Center verwenden). Wenn Sie dasselbe Konto verwenden, können Sie Ihre APP mit ihrer Identität in der Microsoft Store verknüpfen, bevor Sie Sie Verpacken.

![Verknüpfen Sie die APP mit der Microsoft Store](images/associate-your-app-700px.png)<br>
Zuordnen der APP zum Microsoft Store in Visual Studio

### <a name="store-listing-page"></a>Store-Listenseite

Auf der Seite [Store-Auflistung](/windows/uwp/publish/create-app-store-listings) des App-Übermittlungs Vorgangs können Sie nützliche Informationen zu ihrer Mixed Reality-app hinzufügen.

>[!IMPORTANT]
>Um sicherzustellen, dass Ihre APP ordnungsgemäß vom Store kategorisiert und für Windows Mixed Reality-Kunden auffindbar ist, sollten Sie **"Windows Mixed Reality"** als einen ihrer "Suchbegriffe" für die APP hinzufügen (durch Erweitern des Abschnitts "freigegebene Felder" können Sie Suchbegriffe finden).

![Hinzufügen von Windows Mixed Reality zu Suchbegriffen](images/search-terms-800px.png)<br>
Zu Suchbegriffen "Windows Mixed Reality" hinzufügen

## <a name="offering-a-free-trial-for-your-game-or-app"></a>Kostenlose Testversion für Ihr Spiel oder Ihre APP

In vielen Fällen sind die Kunden auf die virtuelle Realität beschränkt, bevor Sie ein Windows Mixed Reality-immersives Headset erwerben. Sie wissen möglicherweise nicht, was Sie von intensiven Spielen erwarten oder mit Ihrem eigenen Komfort Schwellenwert in immersiven Erfahrungen vertraut sein sollten. Viele Kunden können auch ein Windows Mixed Reality-immersives Headset auf PCs testen, die nicht als [Windows Mixed Reality-PCs](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)gebadelt sind. Aus diesen Gründen wird dringend empfohlen, eine [Kostenlose Testversion](/windows/uwp/publish/set-app-pricing-and-availability#free-trial) für Ihre kostenpflichtige Mixed Reality-APP oder Ihr Spiel zu bieten.

## <a name="see-also"></a>Weitere Informationen
* [Was ist Mixed Reality?](../discover/mixed-reality.md)
* [Entwicklung – Übersicht](../develop/development.md)
* [App-Ansichten](../design/app-views.md)
* [Grundlegendes zur Leistung für gemischte Realität](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Empfehlungen zur Leistung für Unity](../develop/unity/performance-recommendations-for-unity.md)
* [Testen Ihrer App auf HoloLens](../develop/platform-capabilities-and-apis/testing-your-app-on-hololens.md)
* [Windows Mixed Reality-Mindestanforderungen für die PC-Hardware Kompatibilität](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)