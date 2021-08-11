---
title: 'HoloLens (1. Generation) und Azure 304: Gesichtserkennung'
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, Tutorial, API, Gesichtserkennung, HoloLens, immersive, vr, Windows 10, Visual Studio
ms.openlocfilehash: 2547b61669884c524fdd605240322dc9d568039b5a202d0a411317b0e83bd547
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219483"
---
# <a name="hololens-1st-gen-and-azure-304-face-recognition"></a>HoloLens (1. Generation) und Azure 304: Gesichtserkennung

<br>

>[!NOTE]
>Die Tutorials der Mixed Reality Academy wurden im Hinblick auf HoloLens (1. Gen.) und immersive Mixed Reality-Headsets entworfen.  Daher halten wir es für wichtig, diese Tutorials für Entwickler verfügbar zu halten, die noch nach Anleitung beim Entwickeln für diese Geräte suchen.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für HoloLens 2 verwendet werden.  Sie werden gewartet, um weiterhin auf den unterstützten Geräten zu funktionieren. Es wird eine neue Reihe von Tutorials geben, die in Zukunft veröffentlicht werden, die veranschaulichen, wie Sie für die entwicklung HoloLens 2.  Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn sie veröffentlicht werden.

<br>

![Ergebnis des Abschlusses dieses Kurses](images/AzureLabs-Lab4-00.png)

In diesem Kurs erfahren Sie, wie Sie einer Mixed Reality-Anwendung mithilfe von Azure Cognitive Services mit der Microsoft-Gesichtserkennungs-API Gesichtserkennungsfunktionen hinzufügen.

*Die Azure-Gesichtserkennungs-API* ist ein Microsoft-Dienst, der Entwicklern die fortgeschrittensten Gesichtserkennungsalgorithmen in der Cloud zur Verfügung stellt. Die *Gesichtserkennungs-API* verfügt über zwei Hauptfunktionen: Gesichtserkennung mit Attributen und Gesichtserkennung. Dadurch können Entwickler einfach eine Gruppe von Gruppen für Gesichter festlegen und dann später Abfragebilder an den Dienst senden, um zu bestimmen, zu wem ein Gesicht gehört. Weitere Informationen finden Sie auf der [Seite zur Azure-Gesichtserkennung.](https://azure.microsoft.com/services/cognitive-services/face/)

Nachdem Sie diesen Kurs abgeschlossen haben, verfügen Sie über eine Mixed Reality HoloLens Anwendung, die Folgendes tun kann:

1. Verwenden Sie eine **Tippbewegung,** um die Aufnahme eines Bilds mithilfe der kamerabasierten HoloLens zu initiieren. 
2. Senden Sie das erfasste Bild an den *Azure-Gesichtserkennungs-API-Dienst.*
3. Empfangen sie die Ergebnisse des *Gesichtserkennungs-API-Algorithmus.*
4. Verwenden Sie eine Benutzeroberfläche, um den Namen der übereinstimmenden Personen anzuzeigen.

Hier erfahren Sie, wie Sie die Ergebnisse aus dem Gesichtserkennungs-API-Dienst in Ihre Unity-basierte Mixed Reality-Anwendung abrufen.

In Ihrer Anwendung liegt es an Ihnen, wie Sie die Ergebnisse in Ihren Entwurf integrieren. Dieser Kurs soll Ihnen beibringen, wie Sie einen Azure-Dienst in Ihre Unity-Project. Es ist Ihre Aufgabe, das Wissen aus diesem Kurs zu nutzen, um Ihre Mixed Reality-Anwendung zu verbessern.

## <a name="device-support"></a>Geräteunterstützung

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td> MR und Azure 304: Gesichtserkennung</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Während sich dieser Kurs hauptsächlich auf HoloLens konzentriert, können Sie das, was Sie in diesem Kurs lernen, auch auf immersive Headsets (VR) Windows Mixed Reality anwenden. Da immersive Headsets (VR) keine zugänglichen Kameras haben, benötigen Sie eine externe Kamera, die mit Ihrem PC verbunden ist. Im Verlauf des Kurses finden Sie Hinweise zu allen Änderungen, die Sie möglicherweise vornehmen müssen, um immersive Headsets (VR) zu unterstützen.

## <a name="prerequisites"></a>Voraussetzungen

> [!NOTE]
> Dieses Tutorial ist für Entwickler konzipiert, die über grundlegende Erfahrung mit Unity und C# verfügen. Beachten Sie auch, dass die Voraussetzungen und die geschriebenen Anweisungen in diesem Dokument darstellen, was zum Zeitpunkt der Erstellung (Mai 2018) getestet und überprüft wurde. Sie können die neueste Software verwenden, [](../../install-the-tools.md) wie im Artikel Installieren der Tools aufgeführt. Es sollte jedoch nicht davon ausgegangen werden, dass die Informationen in diesem Kurs perfekt mit der neueren Software übereinstimmen, als unten aufgeführt.

Für diesen Kurs wird die folgende Hardware und Software empfohlen:

- Ein Entwicklungs-PC, [der mit Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) für die Entwicklung immersiver Headsets (VR) kompatibel ist
- [Windows 10 Fall Creators Update (oder höher) mit aktivierter Entwicklermodus](../../install-the-tools.md)
- [Das neueste Windows 10 SDK](../../install-the-tools.md)
- [Unity 2017.4](../../install-the-tools.md)
- [Visual Studio 2017](../../install-the-tools.md)
- Ein [Windows Mixed Reality immersives Headset (VR)](../../../discover/immersive-headset-hardware-details.md) oder [ein](/hololens/hololens1-hardware) Microsoft HoloLens mit aktivierten Entwicklermodus
- Eine mit Ihrem PC verbundene Kamera (für die Entwicklung immersiver Headsets)
- Internetzugriff für Azure-Setup und Abruf der Gesichtserkennungs-API

## <a name="before-you-start"></a>Vorbereitung

1.  Um Probleme beim Erstellen dieses Projekts zu vermeiden, wird dringend empfohlen, das in diesem Tutorial erwähnte Projekt in einem Stamm- oder Near-Root-Ordner zu erstellen (lange Ordnerpfade können zur Buildzeit Probleme verursachen).
2.  Einrichten und Testen Ihrer HoloLens. Wenn Sie Unterstützung beim Einrichten Ihrer HoloLens benötigen, lesen Sie den Artikel HoloLens [Setup.](/hololens/hololens-setup) 
3.  Es ist eine gute Idee, die Kalibrierung und Sensoroptimierung durchzuführen, wenn Sie mit der Entwicklung einer neuen HoloLens-App beginnen (manchmal kann es helfen, diese Aufgaben für jeden Benutzer auszuführen). 

Hilfe zur Kalibrierung finden Sie unter diesem [Link zum Artikel HoloLens Kalibrierung.](/hololens/hololens-calibration#hololens-2)

Hilfe zur Sensoroptimierung finden Sie unter diesem [Link zum Artikel HoloLens Sensoroptimierung.](/hololens/hololens-updates)

## <a name="chapter-1---the-azure-portal"></a>Kapitel 1: Das Azure-Portal

Um den *Gesichtserkennungs-API-Dienst* in Azure verwenden zu können, müssen Sie eine Instanz des Diensts konfigurieren, die für Ihre Anwendung verfügbar gemacht wird.

1.  Melden Sie sich zunächst beim [Azure-Portal an.](https://portal.azure.com) 

    > [!NOTE]
    > Wenn Sie noch nicht über ein Azure-Konto verfügen, müssen Sie eines erstellen. Wenn Sie dieses Tutorial in einer Classroom- oder Lab-Situation durch verwenden, bitten Sie Ihren Dozenten oder einen der Proktoren um Hilfe beim Einrichten Ihres neuen Kontos.

2.  Klicken Sie nach der Anmeldung in der linken oberen Ecke auf **Neu,** suchen Sie nach *Gesichtserkennungs-API,* und drücken Sie die **EINGABETASTE.**

    ![Suche nach Gesichtserkennungs-API](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > Das Wort **Neu** wurde in neueren Portalen möglicherweise durch **Ressource** erstellen ersetzt.

3.  Die neue Seite enthält eine Beschreibung des *Gesichtserkennungs-API-Diensts.* Wählen Sie unten links in dieser Eingabeaufforderung die Schaltfläche **Erstellen** aus, um eine Zuordnung zu diesem Dienst zu erstellen.

    ![Informationen zur Gesichtserkennungs-API](images/AzureLabs-Lab4-02.png)

4.  Nachdem Sie auf Erstellen geklickt **haben:**

    1. Fügen Sie den gewünschten Namen für diese Dienstinstanz ein.

    2. Wählen Sie ein Abonnement aus.

    3. Wählen Sie den für Sie geeigneten Tarif aus. Wenn Sie zum ersten Mal einen Gesichtserkennungs-API-Dienst erstellen, sollte ihnen ein kostenloser Tarif (F0) zur Verfügung stehen.

    4. Wählen Sie eine **Ressourcengruppe aus,** oder erstellen Sie eine neue. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, Steuern des Zugriffs, Bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. B. diesen Labs) zugeordnet sind, unter einer gemeinsamen Ressourcengruppe zu halten. 

        > Weitere Informationen zu Azure-Ressourcengruppen finden Sie im Artikel [zu Ressourcengruppen.](/azure/azure-resource-manager/resource-group-portal)

    5. Die UWP-App **Person Maker,** die Sie später verwenden, erfordert die Verwendung von "USA, Westen" für den Standort.

    6. Sie müssen auch bestätigen, dass Sie die auf diesen Dienst angewendeten Geschäftsbedingungen verstanden haben.

    7. Wählen Sie **Erstellen* aus.**

        ![Erstellen eines Gesichtserkennungs-API-Diensts](images/AzureLabs-Lab4-03.png)

5.  Nachdem Sie auf **Erstellen*** geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. Dies kann eine Minute dauern.

6.  Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.

    ![Benachrichtigung zur Diensterstellung](images/AzureLabs-Lab4-04.png)

7.  Klicken Sie auf die Benachrichtigungen, um Ihre neue Dienstinstanz zu untersuchen.

    ![Zur Ressourcenbenachrichtigung wechseln](images/AzureLabs-Lab4-05.png)

8.  Wenn Sie bereit sind, klicken Sie in der **Benachrichtigung** auf die Schaltfläche Zu Ressource wechseln, um Ihre neue Dienstinstanz zu untersuchen.

    ![Zugreifen auf Api-Schlüssel für die Gesichtserkennung](images/AzureLabs-Lab4-06.png)

9.  In diesem Tutorial muss Ihre Anwendung Aufrufe an Ihren Dienst tätigen. Dies erfolgt über die Verwendung des Abonnementschlüssels Ihres Diensts. Auf der *Seite Schnellstart* Ihres Gesichtserkennungs-API-Diensts ist der erste Punkt Nummer 1, um *Ihre Schlüssel zu greifen.* 

10. Wählen Sie auf der  Seite Dienst entweder den blauen Schlüssellink  (falls auf der Seite Schnellstart) oder den Link Schlüssel im Navigationsmenü der Dienste aus (links durch das Symbol "Schlüssel" gekennzeichnet), um Ihre Schlüssel anzuzeigen. 

    > [!NOTE] 
    > Notieren Sie sich einen der Schlüssel, und schützen Sie ihn, da Sie ihn später benötigen.

## <a name="chapter-2---using-the-person-maker-uwp-application"></a>Kapitel 2: Verwenden der UWP-Anwendung "Person Maker"

Stellen Sie sicher, dass Sie die vordefinierte UWP-Anwendung namens [Person Maker herunterladen.](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip) Diese App ist nicht das Endprodukt für diesen Kurs, sondern lediglich ein Tool, mit dem Sie Ihre Azure-Einträge erstellen können, auf die sich das spätere Projekt verlassen wird.

**Mit Person Maker** können Sie Azure-Einträge erstellen, die Personen und Personengruppen zugeordnet sind. Die Anwendung fügt alle erforderlichen Informationen in ein Format ein, das später von der FaceAPI verwendet werden kann, um die Gesichter von Personen zu erkennen, die Sie hinzugefügt haben. 

> [WICHTIG] **Person Maker** verwendet eine grundlegende Drosselung, um sicherzustellen, dass Sie die Anzahl der Dienstanrufe pro Minute für den kostenlosen **Abonnementebene nicht überschreiten.** Der grüne Text oben ändert sich in Rot und wird bei einer Drosselung als "AKTIV" aktualisiert. Wenn dies der Fall ist, warten Sie einfach auf die Anwendung (sie wartet, bis sie als Nächstes auf den Gesichtserkennungsdienst zugreifen kann, und aktualisieren Sie sie als "IN-ACTIVE", wenn Sie sie wieder verwenden können).

Diese Anwendung verwendet die *Microsoft.ProjectOxford.Face-Bibliotheken,* mit denen Sie die Gesichtserkennungs-API vollständig nutzen können. Diese Bibliothek ist kostenlos als Paket NuGet verfügbar. Weitere Informationen zu diesen und ähnlichen APIs finden Sie im [API-Referenzartikel.](/azure/cognitive-services/face/apireference)

> [!NOTE] 
> Dies sind nur die erforderlichen Schritte. Anweisungen dazu finden Sie weiter unten im Dokument. Die **Person Maker-App** ermöglicht Folgendes:
>
> - Erstellen Sie eine *Personengruppe,* bei der es sich um eine Gruppe handelt, die aus mehreren Personen besteht, die Sie ihr zuordnen möchten. Mit Ihrem Azure-Konto können Sie mehrere Personengruppen hosten.
>
> - Erstellen Sie eine *Person,* die Mitglied einer Personengruppe ist. Jeder Person sind eine Reihe von *Gesichtsbildern* zugeordnet.
>
> -  Weisen Sie einer *Person* *Gesichtsbilder* zu, damit Ihr Azure-Gesichtserkennungs-API-Dienst eine *Person* anhand des entsprechenden *Gesichts* erkennen kann.
>
> -  *Trainieren Sie* Ihren *Azure-Gesichtserkennungs-API-Dienst.*

Beachten Sie, dass Sie zum Trainieren dieser App zur Erkennung von Personen zehn (10) Nahaufnahmen jeder Person benötigen, die Sie Ihrer Personengruppe hinzufügen möchten. Die Windows 10 App kann Ihnen dabei helfen, diese zu nutzen. Sie müssen sicherstellen, dass jedes Foto klar ist (vermeiden Sie unscharf, verdeckt oder zu weit vom Betreff entfernt), dass das Foto im JPG- oder PNG-Dateiformat vorliegt, wobei die Größe der Bilddatei nicht größer **als 4 MB** und nicht kleiner als **1 KB** ist.

> [!NOTE]
> Wenn Sie diesem Tutorial folgen, verwenden Sie nicht Ihr eigenes Gesicht für das Training. Wenn Sie die HoloLens einlegen, können Sie sich nicht selbst ansehen. Verwenden Sie das Gesicht eines Kollegen oder Studenten.

Running **Person Maker**:

1.  Öffnen Sie den Ordner **PersonMaker,** und doppelklicken Sie auf die *PersonMaker-Projektmappe,* um ihn mit *Visual Studio* zu öffnen.

2.  Sobald die *PersonMaker-Projektmappe* geöffnet ist, stellen Sie Folgendes sicher:

    1. Die *Projektmappenkonfiguration* ist auf **Debuggen** festgelegt.

    2. Die *Lösungsplattform* ist auf **x86** festgelegt.

    3. Die *Zielplattform* ist **lokaler Computer.**

    4.  Möglicherweise müssen Sie auch *NuGet Pakete wiederherstellen* (klicken Sie mit der rechten Maustaste auf die *Projektmappe,* und wählen Sie **Wiederherstellen NuGet Pakete) aus.**

3.  Klicken Sie auf *Lokaler Computer,* und die Anwendung wird gestartet. Beachten Sie, dass auf kleineren Bildschirmen möglicherweise nicht alle Inhalte sichtbar sind, obwohl Sie weiter nach unten scrollen können, um sie anzuzeigen.

    ![Benutzeroberfläche des Personenerstellers](images/AzureLabs-Lab4-07.png)

4.  Fügen Sie Ihren **Azure-Authentifizierungsschlüssel**, den Sie verwenden sollten, aus Ihrem *Gesichtserkennungs-API-Dienst* in Azure ein.

5.  Insert (Einfügen):

    1. Die *ID,* die Sie der *Personengruppe* zuweisen möchten. Die ID muss klein geschrieben sein und darf keine Leerzeichen enthalten. Notieren Sie sich diese ID, da sie später in Ihrem Unity-Projekt erforderlich ist.
    2. Der *Name,* den Sie der *Personengruppe* zuweisen möchten (kann Leerzeichen enthalten).


6.  Klicken Sie auf die Schaltfläche **Personengruppe erstellen.** Unterhalb der Schaltfläche sollte eine Bestätigungsmeldung angezeigt werden.

> [!NOTE]
> Wenn der Fehler "Zugriff verweigert" auftritt, überprüfen Sie den Speicherort, den Sie für Ihren Azure-Dienst festgelegt haben. Wie oben erwähnt, ist diese App für "USA, Westen" konzipiert.

> [!IMPORTANT]
> Sie werden feststellen, dass Sie auch auf die Schaltfläche **Bekannte Gruppe abrufen** klicken können: Dies gilt für , wenn Sie bereits eine Personengruppe erstellt haben und diese verwenden möchten, anstatt eine neue zu erstellen. Wenn Sie auf *Personengruppe* mit einer bekannten Gruppe erstellen klicken, wird auch eine Gruppe abgerufen.

7.  Fügen Sie den *Namen* der *Person* ein, die Sie erstellen möchten.

    1. Klicken Sie auf die Schaltfläche **Person erstellen.**

    2. Unterhalb der Schaltfläche sollte eine Bestätigungsmeldung angezeigt werden.

    3. Wenn Sie eine zuvor erstellte Person löschen möchten, können Sie den Namen in das Textfeld schreiben und Person **löschen** drücken.

8.  Stellen Sie sicher, dass Sie den Standort von zehn (10) Fotos der Person kennen, die Sie Ihrer Gruppe hinzufügen möchten.

9.  Klicken Sie auf **Ordner erstellen und öffnen,** um Windows Explorer für den Ordner zu öffnen, der der Person zugeordnet ist. Fügen Sie die zehn (10) Bilder im Ordner hinzu. Diese müssen das *JPG-* oder *PNG-Dateiformat* aufweisen.

10. Klicken Sie auf **An Azure übermitteln.** Ein Leistungsindikator zeigt den Status der Übermittlung an, gefolgt von einer Nachricht, wenn sie abgeschlossen ist.

11. Nachdem der Leistungsindikator abgeschlossen und eine Bestätigungsmeldung angezeigt wurde, klicken Sie auf **Trainieren,** um Ihren Dienst zu trainieren.

Sobald der Prozess abgeschlossen ist, können Sie zu Unity wechseln.

## <a name="chapter-3---set-up-the-unity-project"></a>Kapitel 3: Einrichten des Unity-Projekts

Im Folgenden finden Sie eine typische Einrichtung für die Entwicklung mit Mixed Reality und ist daher eine gute Vorlage für andere Projekte.

1.  Öffnen Sie *Unity,* und klicken Sie auf **Neu.** 

    ![Starten Sie ein neues Unity-Projekt.](images/AzureLabs-Lab4-08.png)

2.  Sie müssen nun einen Unity-Project Namen angeben. Fügen Sie **MR_FaceRecognition** ein. Stellen Sie sicher, dass der Projekttyp auf **3D** festgelegt ist. Legen Sie den **Speicherort** auf einen für Sie geeigneten Speicherort fest (denken Sie daran, dass näher an den Stammverzeichnissen besser ist). Klicken Sie dann auf **Projekt erstellen.**

    ![Geben Sie Details für das neue Unity-Projekt an.](images/AzureLabs-Lab4-09.png)

3.  Wenn Unity geöffnet ist, sollten Sie überprüfen, ob der **Standardskript-Editor** auf **Visual Studio** festgelegt ist. Navigieren Sie zu **Bearbeiten > Einstellungen,** und navigieren Sie dann im neuen Fenster zu **Externe Tools**. Ändern Sie **den externen Skript-Editor** in **Visual Studio 2017**. Schließen Sie das Fenster **Einstellungen.**

    ![Aktualisieren Sie die Einstellung des Skript-Editors.](images/AzureLabs-Lab4-10.png)

4.  Wechseln Sie als Nächstes zu **Datei > Build Einstellungen,** und wechseln Sie die Plattform zu **Universal Windows Platform,** indem Sie auf die Schaltfläche **Plattform wechseln** klicken.

    ![Erstellen Sie Einstellungen Fenster, und wechseln Sie zur Plattform zu UWP.](images/AzureLabs-Lab4-11.png)

5.  Wechseln Sie zu **Datei > Build Einstellungen,** und stellen Sie Sicher, dass:

    1. **Zielgerät** ist auf **HoloLens**

        > Legen Sie für die immersiven Headsets **Zielgerät** auf *Beliebiges Gerät* fest.

    2. **Buildtyp** ist auf **D3D** festgelegt
    3. **SDK** ist auf **Latest installed (Neueste Installation)** festgelegt.
    4. **Visual Studio Version** ist auf **Latest installed (Neueste installiert)** festgelegt.
    5. **Build und Ausführung** ist auf **Lokaler Computer** festgelegt.
    6. Speichern Sie die Szene, und fügen Sie sie dem Build hinzu. 

        1. Wählen Sie hierzu **Öffnende Szenen hinzufügen aus.** Ein Speicherfenster wird angezeigt.

            ![Klicken Sie auf die Schaltfläche "Offene Szenen hinzufügen".](images/AzureLabs-Lab4-12.png)

        2. Wählen Sie die Schaltfläche **Neuer Ordner** aus, um einen neuen Ordner zu erstellen, und nennen Sie ihn **Scenes**.

            ![Erstellen eines neuen Skriptordners](images/AzureLabs-Lab4-13.png)

        3. Öffnen Sie den neu erstellten Ordner **Scenes,** und geben Sie dann im Textfeld **Dateiname**: **FaceRecScene** ein, und klicken Sie dann auf **Speichern.**

            ![Geben Sie der neuen Szene einen Namen.](images/AzureLabs-Lab4-14.png)

    7. Die übrigen Einstellungen in *Build Einstellungen* sollten vorerst als Standard festgelegt werden.

6. Klicken *Sie* im Fenster Build Einstellungen auf die Schaltfläche **Player Einstellungen.** Dadurch wird der zugehörige Bereich in dem Bereich geöffnet, in dem sich der *Inspektor* befindet. 

    ![Öffnen Sie die Playereinstellungen.](images/AzureLabs-Lab4-15.png)

7. In diesem Bereich müssen einige Einstellungen überprüft werden:

    1. Auf der Registerkarte **Andere Einstellungen:**

        1. **Die Skriptlaufzeitversion**  muss **experimentell** sein (.NET 4.6-Entsprechung). Wenn Sie dies ändern, muss der Editor neu gestartet werden.
        2. **Skript-Back-End** sollte **.NET** sein
        3. **Der API-Kompatibilitätsgrad** sollte **.NET 4.6** sein.

            ![Aktualisieren Sie andere Einstellungen.](images/AzureLabs-Lab4-16.png)
      
    2. Aktivieren **Sie** auf der Registerkarte Veröffentlichen Einstellungen unter **Funktionen** Folgendes:

        - **InternetClient**
        - **Webcam**

            ![Aktualisieren der Veröffentlichungseinstellungen.](images/AzureLabs-Lab4-17.png)

    3. Aktivieren Sie weiter unten im Bereich in **XR Einstellungen** (finden Sie unter **Veröffentlichen Einstellungen**), aktivieren Sie Virtual Reality **Supported (Virtual Reality Unterstützt),** und stellen Sie sicher, dass das **Windows Mixed Reality SDK** hinzugefügt wird.

        ![Aktualisieren Sie die X R-Einstellungen.](images/AzureLabs-Lab4-18.png)

8.  Zurück in *Build Einstellungen* ist **Unity C#-Projekte** nicht mehr abgeblendet. Aktivieren Sie das Kontrollkästchen daneben. 
9.  Schließen Sie das Fenster „Build Settings“ (Buildeinstellungen).
10. Speichern Sie Ihre Szene und Project (**DATEI > SZENE SPEICHERN/DATEI > PROJEKT SPEICHERN**).

## <a name="chapter-4---main-camera-setup"></a>Kapitel 4: Einrichtung der Hauptkamera

> [!IMPORTANT]
> Wenn Sie die *Unity Set up-Komponente* dieses Kurses überspringen und direkt mit dem Code fortfahren möchten, können Sie [dieses UNITYPACKAGE herunterladen](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage)und als [benutzerdefiniertes Paket](https://docs.unity3d.com/Manual/AssetPackages.html)in Ihr Projekt importieren. Beachten Sie, dass dieses Paket auch den Import der *Newtonsoft DLL* enthält, die in [Kapitel 5](#chapter-5--import-the-newtonsoftjson-library)behandelt wird. Mit diesem importierten Können Sie mit [Kapitel 6](#chapter-6---create-the-faceanalysis-class)fortfahren.

1.  Wählen Sie im *Hierarchiebereich* die **Hauptkamera** aus.

2.  Nach der Auswahl von werden alle Komponenten der **Hauptkamera** im *Inspektorbereich angezeigt.*

    1. Das **Camera-Objekt** muss **hauptkamera** genannt werden (beachten Sie die Schreibweise!)

    2. Das **Hauptkameratag** muss auf **MainCamera** festgelegt werden (beachten Sie die Schreibweise!)

    3. Stellen Sie sicher, dass **die Transformationsposition** auf **0, 0, 0** festgelegt ist.

    4. Legen Sie **Clear Flags (Flags** löschen) auf **Volltonfarbe fest.**

    5. Legen Sie die **Hintergrundfarbe** der Kamerakomponente auf **Schwarz, Alpha 0 (Hexadezimalcode: #00000000) fest.**

        ![Einrichten von Kamerakomponenten](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a>Kapitel 5: Importieren der Newtonsoft.Jsin die Bibliothek

> [!IMPORTANT]
> Wenn Sie das ".unitypackage" im [letzten Kapitel](#chapter-4---main-camera-setup)importiert haben, können Sie dieses Kapitel überspringen.

Um Sie beim Deserialisieren und Serialisieren von Objekten zu unterstützen, die an die Bot Service empfangen und gesendet werden, müssen Sie die *Newtonsoft.Jsin* die Bibliothek herunterladen. In dieser [Unity-Paketdatei](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage)finden Sie eine kompatible Version, die bereits mit der richtigen Unity-Ordnerstruktur organisiert ist. 

So importieren Sie die Bibliothek:

1.  Laden Sie das Unity-Paket herunter.
2.  Klicken Sie auf **Assets**, **Import Package**, **Custom Package**.

    ![Importieren Newtonsoft.Jsein](images/AzureLabs-Lab4-20.png)

3.  Suchen Sie nach dem unity-Paket, das Sie heruntergeladen haben, und klicken Sie auf Öffnen.
4.  Stellen Sie sicher, dass alle Komponenten des Pakets aktiviert sind, und klicken Sie auf **Importieren.**

    ![Importieren der Newtonsoft.Jsfür Ressourcen](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a>Kapitel 6: Erstellen der FaceAnalysis-Klasse

Der Zweck der FaceAnalysis-Klasse besteht darin, die Methoden zu hosten, die für die Kommunikation mit Ihrem Azure-Gesichtserkennungsdienst erforderlich sind. 

- Nachdem dem Dienst ein Erfassungsbild gesendet wurde, analysiert er es, identifiziert die Darin angezeigten Gesichter und ermittelt, ob es zu einer bekannten Person gehört. 
- Wenn eine bekannte Person gefunden wird, zeigt diese Klasse ihren Namen als Benutzeroberflächentext in der Szene an.

So erstellen Sie die *FaceAnalysis-Klasse:*

 1. Klicken Sie im Project Bereich mit der rechten Maustaste auf den *Ordner Assets,* und klicken Sie dann auf Ordner **erstellen.**  >   Rufen Sie den Ordner **Skripts auf.** 

    ![Erstellen Sie die FaceAnalysis-Klasse.](images/AzureLabs-Lab4-22.png)

2.  Doppelklicken Sie auf den soeben erstellten Ordner, um ihn zu öffnen. 
3.  Klicken Sie mit der rechten Maustaste in den Ordner, und klicken **Sie** dann auf  >  **C#-Skript erstellen.** Rufen Sie das Skript *FaceAnalysis auf.* 
4.  Doppelklicken Sie auf das neue *FaceAnalysis-Skript,* um es mit Visual Studio 2017 zu öffnen.
5.  Geben Sie die folgenden Namespaces oberhalb der *FaceAnalysis-Klasse* ein:

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  Sie müssen nun alle Objekte hinzufügen, die für die Deserialisierung verwendet werden. Diese Objekte müssen **außerhalb** des *FaceAnalysis-Skripts* (unterhalb der unteren geschweiften Klammer) hinzugefügt werden. 

    ```csharp
        /// <summary>
        /// The Person Group object
        /// </summary>
        public class Group_RootObject
        {
            public string personGroupId { get; set; }
            public string name { get; set; }
            public object userData { get; set; }
        }

        /// <summary>
        /// The Person Face object
        /// </summary>
        public class Face_RootObject
        {
            public string faceId { get; set; }
        }

        /// <summary>
        /// Collection of faces that needs to be identified
        /// </summary>
        public class FacesToIdentify_RootObject
        {
            public string personGroupId { get; set; }
            public List<string> faceIds { get; set; }
            public int maxNumOfCandidatesReturned { get; set; }
            public double confidenceThreshold { get; set; }
        }

        /// <summary>
        /// Collection of Candidates for the face
        /// </summary>
        public class Candidate_RootObject
        {
            public string faceId { get; set; }
            public List<Candidate> candidates { get; set; }
        }

        public class Candidate
        {
            public string personId { get; set; }
            public double confidence { get; set; }
        }

        /// <summary>
        /// Name and Id of the identified Person
        /// </summary>
        public class IdentifiedPerson_RootObject
        {
            public string personId { get; set; }
            public string name { get; set; }
        }
    ```
7. Die *Methoden Start()* und *Update()* werden nicht verwendet, daher löschen Sie sie jetzt. 

8.  Fügen Sie in der *FaceAnalysis-Klasse* die folgenden Variablen hinzu:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static FaceAnalysis Instance;

        /// <summary>
        /// The analysis result text
        /// </summary>
        private TextMesh labelText;

        /// <summary>
        /// Bytes of the image captured with camera
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// Path of the image captured with camera
        /// </summary>
        internal string imagePath;

        /// <summary>
        /// Base endpoint of Face Recognition Service
        /// </summary>
        const string baseEndpoint = "https://westus.api.cognitive.microsoft.com/face/v1.0/";

        /// <summary>
        /// Auth key of Face Recognition Service
        /// </summary>
        private const string key = "- Insert your key here -";

        /// <summary>
        /// Id (name) of the created person group 
        /// </summary>
        private const string personGroupId = "- Insert your group Id here -";
    ```

    > [!NOTE]
    > Ersetzen Sie den **Schlüssel** und die **personGroupId** durch Ihren Dienstschlüssel und die ID der Zuvor erstellten Gruppe.

9.  Fügen Sie die *Awake()-Methode* hinzu, die die -Klasse initialisiert, der Hauptkamera die *ImageCapture-Klasse* hinzufügt und die Label-Erstellungsmethode aufruft:

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;

            // Add the ImageCapture Class to this Game Object
            gameObject.AddComponent<ImageCapture>();

            // Create the text label in the scene
            CreateLabel();
        }
    ```

10. Fügen Sie die *CreateLabel()-Methode* hinzu, die das *Label-Objekt* erstellt, um das Analyseergebnis anzuzeigen:

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private void CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Attach the label to the Main Camera
            newLabel.transform.parent = gameObject.transform;
            
            // Resize and position the new cursor
            newLabel.transform.localScale = new Vector3(0.4f, 0.4f, 0.4f);
            newLabel.transform.position = new Vector3(0f, 3f, 60f);

            // Creating the text of the Label
            labelText = newLabel.AddComponent<TextMesh>();
            labelText.anchor = TextAnchor.MiddleCenter;
            labelText.alignment = TextAlignment.Center;
            labelText.tabSize = 4;
            labelText.fontSize = 50;
            labelText.text = ".";       
        }
    ```

11. Fügen Sie die *Methoden DetectFacesFromImage()* und *GetImageAsByteArray()* hinzu. Erstere fordert den Gesichtserkennungsdienst auf, alle möglichen Gesichter im übermittelten Bild zu erkennen, während letzteres erforderlich ist, um das erfasste Bild in ein Bytearray zu konvertieren:

    ```csharp
        /// <summary>
        /// Detect faces from a submitted image
        /// </summary>
        internal IEnumerator DetectFacesFromImage()
        {
            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}detect";

            // Change the image into a bytes array
            imageBytes = GetImageAsByteArray(imagePath);

            using (UnityWebRequest www = 
                UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/octet-stream");
                www.uploadHandler.contentType = "application/octet-stream";
                www.uploadHandler = new UploadHandlerRaw(imageBytes);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Face_RootObject[] face_RootObject = 
                    JsonConvert.DeserializeObject<Face_RootObject[]>(jsonResponse);

                List<string> facesIdList = new List<string>();
                // Create a list with the face Ids of faces detected in image
                foreach (Face_RootObject faceRO in face_RootObject)
                {
                    facesIdList.Add(faceRO.faceId);
                    Debug.Log($"Detected face - Id: {faceRO.faceId}");
                }
                
                StartCoroutine(IdentifyFaces(facesIdList));
            }
        }

        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

12. Fügen Sie die *IdentifyFaces()-Methode* hinzu, die den *Gesichtserkennungsdienst* anfordert, alle bekannten Gesichter zu identifizieren, die zuvor im übermittelten Bild erkannt wurden. Die Anforderung gibt eine ID der identifizierten Person zurück, jedoch nicht den Namen:

    ```csharp
        /// <summary>
        /// Identify the faces found in the image within the person group
        /// </summary>
        internal IEnumerator IdentifyFaces(List<string> listOfFacesIdToIdentify)
        {
            // Create the object hosting the faces to identify
            FacesToIdentify_RootObject facesToIdentify = new FacesToIdentify_RootObject();
            facesToIdentify.faceIds = new List<string>();
            facesToIdentify.personGroupId = personGroupId;
            foreach (string facesId in listOfFacesIdToIdentify)
            {
                facesToIdentify.faceIds.Add(facesId);
            }
            facesToIdentify.maxNumOfCandidatesReturned = 1;
            facesToIdentify.confidenceThreshold = 0.5;

            // Serialize to Json format
            string facesToIdentifyJson = JsonConvert.SerializeObject(facesToIdentify);
            // Change the object into a bytes array
            byte[] facesData = Encoding.UTF8.GetBytes(facesToIdentifyJson);

            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}identify";

            using (UnityWebRequest www = UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/json");
                www.uploadHandler.contentType = "application/json";
                www.uploadHandler = new UploadHandlerRaw(facesData);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                Candidate_RootObject [] candidate_RootObject = JsonConvert.DeserializeObject<Candidate_RootObject[]>(jsonResponse);

                // For each face to identify that ahs been submitted, display its candidate
                foreach (Candidate_RootObject candidateRO in candidate_RootObject)
                {
                    StartCoroutine(GetPerson(candidateRO.candidates[0].personId));
                    
                    // Delay the next "GetPerson" call, so all faces candidate are displayed properly
                    yield return new WaitForSeconds(3);
                }           
            }
        }
    ```

13. Fügen Sie die *GetPerson()-Methode* hinzu. Durch Die Angabe der Personen-ID fordert diese Methode dann den *Gesichtserkennungsdienst* auf, den Namen der identifizierten Person zurückzugeben:

    ```csharp
        /// <summary>
        /// Provided a personId, retrieve the person name associated with it
        /// </summary>
        internal IEnumerator GetPerson(string personId)
        {
            string getGroupEndpoint = $"{baseEndpoint}persongroups/{personGroupId}/persons/{personId}?";
            WWWForm webForm = new WWWForm();

            using (UnityWebRequest www = UnityWebRequest.Get(getGroupEndpoint))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                IdentifiedPerson_RootObject identifiedPerson_RootObject = JsonConvert.DeserializeObject<IdentifiedPerson_RootObject>(jsonResponse);

                // Display the name of the person in the UI
                labelText.text = identifiedPerson_RootObject.name;
            }
        }
    ```

14.  Denken Sie daran, die Änderungen zu **speichern,** bevor Sie zum Unity-Editor zurückkehren.
15.  Ziehen Sie im Unity-Editor das FaceAnalysis-Skript aus dem Ordner Skripts im bereich Project in das Objekt Hauptkamera im *Hierarchiebereich*. Die neue Skriptkomponente wird der Hauptkamera hinzugefügt. 

![Platzieren von FaceAnalysis auf der Hauptkamera](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a>Kapitel 7: Erstellen der ImageCapture-Klasse

Der Zweck der *ImageCapture-Klasse* besteht darin, die Methoden zu hosten, die für die Kommunikation mit Ihrem *Azure-Gesichtserkennungsdienst* erforderlich sind, um das zu erfassende Bild zu analysieren, Gesichter darin zu identifizieren und zu bestimmen, ob es zu einer bekannten Person gehört. Wenn eine bekannte Person gefunden wird, zeigt diese Klasse ihren Namen als Benutzeroberflächentext in der Szene an.

So erstellen Sie die *ImageCapture-Klasse:*
 
1.  Klicken Sie mit der rechten Maustaste in den Ordner **Skripts,** den Sie zuvor erstellt haben, und klicken Sie dann auf **Erstellen**, **C#-Skript**. Rufen Sie das Skript *ImageCapture* auf. 
2.  Doppelklicken Sie auf das neue *ImageCapture-Skript,* um es mit Visual Studio 2017 zu öffnen.
3.  Geben Sie die folgenden Namespaces oberhalb der ImageCapture-Klasse ein:

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  Fügen Sie in der *ImageCapture-Klasse* die folgenden Variablen hinzu:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture instance;

        /// <summary>
        /// Keeps track of tapCounts to name the captured images 
        /// </summary>
        private int tapsCount;

        /// <summary>
        /// PhotoCapture object used to capture images on HoloLens 
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// HoloLens class to capture user gestures
        /// </summary>
        private GestureRecognizer recognizer;
    ```

5.  Fügen Sie die Methoden *"Awake()"* und *"Start()"* hinzu, die erforderlich sind, um die Klasse zu initialisieren und dem HoloLens das Erfassen der Gesten des Benutzers zu ermöglichen:

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Called right after Awake
        /// </summary>
        void Start()
        {
            // Initialises user gestures capture 
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

6.  Fügen Sie den *TapHandler()* hinzu, der aufgerufen wird, wenn der Benutzer eine *Tippbewegung* ausführt:

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            tapsCount++;
            ExecuteImageCaptureAndAnalysis();
        }
    ```

7.  Fügen Sie die *ExecuteImageCaptureAndAnalysis()-Methode* hinzu, die den Prozess der Bilderfassung startet:

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Computer Vision service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters c = new CameraParameters();
                c.hologramOpacity = 0.0f;
                c.cameraResolutionWidth = targetTexture.width;
                c.cameraResolutionHeight = targetTexture.height;
                c.pixelFormat = CapturePixelFormat.BGRA32;

                captureObject.StartPhotoModeAsync(c, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    // Set the image path on the FaceAnalysis class
                    FaceAnalysis.Instance.imagePath = filePath;

                    photoCaptureObject.TakePhotoAsync
                    (filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
                });
            });
        }
    ```

8.  Fügen Sie die Handler hinzu, die aufgerufen werden, wenn der Fotoaufnahmeprozess abgeschlossen wurde:

    ```csharp
        /// <summary>
        /// Called right after the photo capture process has concluded
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Request image caputer analysis
            StartCoroutine(FaceAnalysis.Instance.DetectFacesFromImage());
        }
    ```

9. Denken Sie daran, die Änderungen zu **speichern,** bevor Sie zum Unity-Editor zurückkehren.

## <a name="chapter-8---building-the-solution"></a>Kapitel 8: Erstellen der Lösung

Um einen gründlichen Test Ihrer Anwendung durchzuführen, müssen Sie sie auf Ihre HoloLens querladen.

Stellen Sie zuvor Sicher, dass:

-   Alle in Kapitel 3 erwähnten Einstellungen sind ordnungsgemäß festgelegt. 
-   Das Skript *FaceAnalysis* ist an das Hauptkameraobjekt angefügt. 
-   Sowohl der **Authentifizierungsschlüssel** als auch die **Gruppen-ID** wurden im *FaceAnalysis-Skript* festgelegt.

An diesem Punkt können Sie die Projektmappe erstellen. Sobald die Lösung erstellt wurde, können Sie Ihre Anwendung bereitstellen.

So starten Sie den Buildprozess:

1.  Speichern Sie die aktuelle Szene, indem Sie auf Datei, Speichern klicken.
2.  Wechseln Sie zu Datei, Erstellen Einstellungen, und klicken Sie auf Offene Szenen hinzufügen.
3.  Stellen Sie sicher, dass Sie Unity C#-Projekte aktivieren.

    ![Bereitstellen der Visual Studio-Lösung](images/AzureLabs-Lab4-24.png)

4.  Klicken Sie auf Erstellen. Anschließend startet Unity ein Datei-Explorer-Fenster, in dem Sie erstellen und dann einen Ordner auswählen müssen, in dem die App erstellt werden soll. Erstellen Sie diesen Ordner jetzt innerhalb des Unity-Projekts, und nennen Sie ihn App. Klicken Sie dann bei ausgewähltem App-Ordner auf Ordner auswählen. 
5.  Unity beginnt mit der Erstellung Ihres Projekts im Ordner App. 
6.  Sobald die Erstellung von Unity abgeschlossen ist (dies kann einige Zeit dauern), wird ein Datei-Explorer-Fenster am Speicherort Ihres Builds geöffnet.

    ![Bereitstellen der Lösung über Visual Studio](images/AzureLabs-Lab4-25.png)

7.  Öffnen Sie Ihren Ordner App, und öffnen Sie dann die neue Project Projektmappe (wie oben MR_FaceRecognition.sln).


## <a name="chapter-9---deploying-your-application"></a>Kapitel 9: Bereitstellen Ihrer Anwendung

So stellen Sie auf HoloLens bereit:

1.  Sie benötigen die IP-Adresse Ihrer HoloLens (für Remote Deploy) und stellen sicher, dass sich Ihre HoloLens im **Entwicklermodus befindet.** Aufgabe:

    1. Öffnen Sie während der HoloLens die **Einstellungen**.
    2. Wechseln Sie zu **Netzwerk & Internet > Wi-Fi > Erweiterte Optionen.**
    3. Notieren Sie sich die **IPv4-Adresse.**
    4. Navigieren Sie als Nächstes zurück zu **Einstellungen** und dann zu **& Security > For Developers aktualisieren.** 
    5. Legen Sie den Entwicklermodus auf Ein fest.

2.  Navigieren Sie zu Ihrem neuen Unity-Build (dem *Ordner App),* und öffnen Sie die Projektmappendatei mit *Visual Studio*.
3.  Wählen Sie in der Projektmappenkonfiguration **debuggen** aus.
4.  Wählen Sie in der Projektmappenplattform **x86**, **Remotecomputer aus.** 

    ![Ändern der Lösungskonfiguration](images/AzureLabs-Lab4-26.png)
 
5.  Wechseln Sie zum **Menü Erstellen,** und klicken Sie auf **Projektmappe bereitstellen**, um die Anwendung in Ihre HoloLens zu querladen.
6.  Ihre App sollte nun in der Liste der installierten Apps auf Ihrem HoloLens angezeigt werden, damit sie gestartet werden kann.

> [!NOTE]
> Legen Sie zum Bereitstellen auf einem immersiven Headset die **Projektmappenplattform** auf *Lokaler Computer* und die **Konfiguration** auf *Debuggen* fest, wobei *x86* als **Plattform verwendet wird.** Stellen Sie dann auf dem lokalen Computer bereit, indem Sie im **Menü Erstellen** die Option *Projektmappe bereitstellen* auswählen. 


## <a name="chapter-10---using-the-application"></a>Kapitel 10: Verwenden der Anwendung

1.  Starten Sie die App, um die HoloLens zu verwenden.
2.  Sehen Sie sich die Person an, die Sie bei der *Gesichtserkennungs-API* registriert haben. Stellen Sie Folgendes sicher:

    -  Das Gesicht der Person ist nicht zu weit entfernt und deutlich sichtbar.
    -  Die Umgebungsbeleuchtung ist nicht zu dunkel.

3.  Verwenden Sie die Tippbewegung, um das Bild der Person zu erfassen.
4.  Warten Sie, bis die App die Analyseanforderung sendet und eine Antwort empfängt.
5.  Wenn die Person erfolgreich erkannt wurde, wird der Name der Person als Benutzeroberflächentext angezeigt.
6.  Sie können den Erfassungsprozess mithilfe der Tippbewegung alle paar Sekunden wiederholen.

## <a name="your-finished-azure-face-api-application"></a>Ihre fertige Azure-Gesichtserkennungs-API-Anwendung

Herzlichen Glückwunsch! Sie haben eine Mixed Reality-App erstellt, die den Azure-Gesichtserkennungsdienst nutzt, um Gesichter in einem Bild zu erkennen und bekannte Gesichter zu identifizieren.

![Ergebnis des Abschlusses dieses Kurses](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a>Zusatzübungen

### <a name="exercise-1"></a>Übung 1

Die **Azure-Gesichtserkennungs-API** ist leistungsfähig genug, um bis zu 64 Gesichter in einem einzelnen Bild zu erkennen. Erweitern Sie die Anwendung, sodass sie unter vielen anderen Personen zwei oder drei Gesichter erkennen kann.

### <a name="exercise-2"></a>Übung 2

Die **Azure-Gesichtserkennungs-API** kann auch alle Arten von Attributinformationen bereitstellen. Integrieren Sie diese in die Anwendung. Dies kann in Kombination mit der [Emotionen-API](https://azure.microsoft.com/services/cognitive-services/emotion/)noch interessanter sein.