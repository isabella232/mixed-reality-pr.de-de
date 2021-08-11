---
title: 'HoloLens (1. Generation) und Azure 306: Streamen von Video'
description: In diesem Kurs erfahren Sie, wie Sie Azure Media Services in einer Mixed Reality-Anwendung implementieren.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, Tutorial, API, Media Services, Videostreaming, 360, immersive, vr, Windows 10, Visual Studio
ms.openlocfilehash: 3f3567c140c3162258475c28c2ef149039e3c40ed418ed2801ac8c40dda00a8f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224215"
---
# <a name="hololens-1st-gen-and-azure-306-streaming-video"></a>HoloLens (1. Generation) und Azure 306: Streaming von Videos

<br>

>[!NOTE]
>Die Tutorials der Mixed Reality Academy wurden im Hinblick auf HoloLens (1. Gen.) und immersive Mixed Reality-Headsets entworfen.  Daher halten wir es für wichtig, diese Tutorials für Entwickler verfügbar zu halten, die noch nach Anleitung beim Entwickeln für diese Geräte suchen.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für HoloLens 2 verwendet werden.  Sie werden gewartet, um weiterhin auf den unterstützten Geräten zu funktionieren. Es wird eine neue Reihe von Tutorials geben, die in Zukunft veröffentlicht werden, die veranschaulichen, wie Sie für die entwicklung HoloLens 2.  Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn sie veröffentlicht werden.

<br> 

![final product -start ](images/AzureLabs-Lab6-00.png)
 ![ final product -start](images/AzureLabs-Lab6-01.png)

In diesem Kurs erfahren Sie, wie Sie Ihre Azure Media Services mit einer Windows Mixed Reality VR-Umgebung verbinden, um das Streaming der Videowiedergabe mit 360 Grad auf immersiven Headsets zu ermöglichen. 

**Azure Media Services** sind eine Sammlung von Diensten, die Ihnen Videostreamingdienste in Broadcastqualität bieten, um größere Zielgruppen auf den beliebtesten mobilen Geräten von heute zu erreichen. Weitere Informationen finden Sie auf der Azure Media Services [Seite](https://azure.microsoft.com/services/media-services).

Nachdem Sie diesen Kurs abgeschlossen haben, verfügen Sie über eine Mixed Reality-Anwendung für immersive Headsets, die Folgendes tun kann:

1. Rufen Sie ein 360-Grad-Video aus **einem** Azure Storage über **Azure Media Service ab.**

2. Zeigen Sie das abgerufene 360-Grad-Video innerhalb einer Unity-Szene an.

3. Navigieren Sie zwischen zwei Szenen mit zwei verschiedenen Videos.

In Ihrer Anwendung liegt es an Ihnen, wie Sie die Ergebnisse in Ihren Entwurf integrieren. Dieser Kurs soll Ihnen beibringen, wie Sie einen Azure-Dienst in Ihre Unity-Project. Es ist Ihre Aufgabe, das Wissen aus diesem Kurs zu nutzen, um Ihre Mixed Reality-Anwendung zu verbessern.

## <a name="device-support"></a>Geräteunterstützung

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td> MR und Azure 306: Streamen von Video</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>Voraussetzungen

> [!NOTE]
> Dieses Tutorial ist für Entwickler konzipiert, die über grundlegende Erfahrung mit Unity und C# verfügen. Beachten Sie auch, dass die Voraussetzungen und die geschriebenen Anweisungen in diesem Dokument darstellen, was zum Zeitpunkt der Erstellung (Mai 2018) getestet und überprüft wurde. Sie können die neueste Software verwenden, [](../../install-the-tools.md)wie im Artikel Installieren des Tools aufgeführt. Es sollte jedoch nicht davon ausgegangen werden, dass die Informationen in diesem Kurs perfekt mit der neueren Software übereinstimmen, als unten aufgeführt.

Für diesen Kurs wird die folgende Hardware und Software empfohlen:

- Ein Entwicklungs-PC, [der mit Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) für die Entwicklung immersiver Headsets (VR) kompatibel ist
- [Windows 10 Fall Creators Update (oder höher) mit aktivierter Entwicklermodus](../../install-the-tools.md#installation-checklist)
- [Das neueste Windows 10 SDK](../../install-the-tools.md#installation-checklist)
- [Unity 2017.4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- Ein [Windows Mixed Reality immersives Headset (VR)](../../../discover/immersive-headset-hardware-details.md)
- Internetzugriff für Azure-Setup und Datenabruf
- Zwei 360-Grad-Videos im MP4-Format (lizenzfreie Videos finden Sie [auf dieser Downloadseite).](https://www.mettle.com/360vr-master-series-free-360-downloads-page)

## <a name="before-you-start"></a>Vorbereitung

1.  Um Probleme beim Erstellen dieses Projekts zu vermeiden, wird dringend empfohlen, das in diesem Tutorial erwähnte Projekt in einem Stamm- oder Near-Root-Ordner zu erstellen (lange Ordnerpfade können zur Buildzeit Probleme verursachen).
2.  Richten Sie Ihr immersives Headset Mixed Reality und testen Sie es.

    > [!NOTE]
    > Für diesen **Kurs** sind keine Motion Controller erforderlich. Wenn Sie Unterstützung beim Einrichten des immersiven Headsets benötigen, klicken Sie auf den Link [zum Einrichten Windows Mixed Reality](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).

## <a name="chapter-1---the-azure-portal-creating-the-azure-storage-account"></a>Kapitel 1: Das Azure-Portal: Erstellen des Azure Storage Kontos

Um den **Azure Storage-Dienst zu** verwenden, müssen Sie ein **Storage-Konto** in der Azure-Portal.

1.  Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

    > [!NOTE]
    > Wenn Sie noch nicht über ein Azure-Konto verfügen, müssen Sie eines erstellen. Wenn Sie dieses Tutorial in einer Classroom- oder Lab-Situation durch verwenden, bitten Sie Ihren Dozenten oder einen der Proktoren um Hilfe beim Einrichten Ihres neuen Kontos.

2.  Wenn Sie angemeldet sind, klicken Sie im **linken Storage** auf Storage Konten.

    ![Azure Storage Kontoeinrichtung](images/AzureLabs-Lab6-02.png)

3.  Klicken Sie **Storage Registerkarte Konten** auf **Hinzufügen.**

    ![Azure Storage Kontoeinrichtung](images/AzureLabs-Lab6-03.png)

4.  Führen Sie auf **der Registerkarte Speicherkonto erstellen die folgenden** Optionen aus:

    1.  Fügen Sie **einen Namen** für Ihr Konto ein. Beachten Sie, dass dieses Feld nur Zahlen und Kleinbuchstaben akzeptiert.

    2.  Wählen **Sie unter Bereitstellungsmodell die** Option Resource Manager **aus.**

    3.  Wählen **Sie für Kontoart** Storage **(Allgemein v1) aus.**

    4.  Wählen **Sie unter** Leistung die Option **Standard* aus.**

    5.  Wählen **Sie für** Replikation die Option Lokal **redundanter Speicher (LRS) aus.**

    6.  Lassen **Sie Sichere Übertragung erforderlich** **deaktiviert.**

    7.  Wählen Sie ein **Abonnement** aus.

    8.  Wählen Sie eine **Ressourcengruppe aus,** oder erstellen Sie eine neue. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, Steuern des Zugriffs, Bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.

    9.  Bestimmen Sie **den Standort** für Ihre Ressourcengruppe (wenn Sie eine neue Ressourcengruppe erstellen). Der Standort befindet sich idealerweise in der Region, in der die Anwendung ausgeführt wird. Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.

5.  Sie müssen bestätigen, dass Sie die auf diesen Dienst angewendeten Geschäftsbedingungen verstanden haben.

    ![Azure Storage Kontoeinrichtung](images/AzureLabs-Lab6-04.png)

6.  Nachdem Sie auf **Erstellen** geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. Dies kann eine Minute dauern.

7.  Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.

    ![Azure Storage Kontoeinrichtung](images/AzureLabs-Lab6-05.png)

8.  An diesem Punkt müssen Sie der Ressource nicht folgen, sondern einfach zum nächsten Kapitel wechseln.

## <a name="chapter-2---the-azure-portal-creating-the-media-service"></a>Kapitel 2: Das Azure-Portal: Erstellen des Mediendiensts

Um Azure Media Service verwenden zu können, müssen Sie eine Instanz des Diensts konfigurieren, die ihrer Anwendung zur Verfügung gestellt wird (wobei der Kontoinhaber ein Administrator sein muss).

1.  Klicken Sie im Azure-Portal oben links auf Ressource erstellen, suchen Sie nach **Media Service, und** drücken Sie die **EINGABETASTE.**  Die Ressource, die Sie wünschen, verfügt derzeit über ein rosafarbenes Symbol. Klicken Sie hier, um eine neue Seite anzuzeigen.

    ![Das Azure-Portal](images/AzureLabs-Lab6-06.png)

2.  Die neue Seite enthält eine Beschreibung des **Media Service.** Klicken Sie unten links in dieser Eingabeaufforderung auf die **Schaltfläche Erstellen,** um eine Zuordnung zu diesem Dienst zu erstellen.

    ![Das Azure-Portal](images/AzureLabs-Lab6-07.png)

3.  Nachdem Sie auf Erstellen geklickt **haben,** wird ein Bereich angezeigt, in dem Sie einige Details zu Ihrem neuen Media Service bereitstellen müssen:

    1.  Fügen Sie den gewünschten **Kontonamen für** diese Dienstinstanz ein.

    2.  Wählen Sie ein **Abonnement** aus.

    3. Wählen Sie eine **Ressourcengruppe aus,** oder erstellen Sie eine neue. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, Steuern des Zugriffs, Bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. B. diesen Labs) zugeordnet sind, unter einer gemeinsamen Ressourcengruppe zu halten. 
    
    > Wenn Sie mehr über Azure-Ressourcengruppen erfahren möchten, folgen Sie diesem Link [zum Verwalten von Azure-Ressourcengruppen.](/azure/azure-resource-manager/resource-group-portal)

    4.  Bestimmen Sie **den Standort** für Ihre Ressourcengruppe (wenn Sie eine neue Ressourcengruppe erstellen). Der Standort befindet sich idealerweise in der Region, in der die Anwendung ausgeführt wird. Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.

    5.  Klicken Sie **Storage** Abschnitt Konto auswählen auf den Abschnitt Please  **select...** (Bitte auswählen...) und dann auf das Storage-Konto, das Sie im letzten Kapitel erstellt haben.

    6.  Sie müssen auch bestätigen, dass Sie die auf diesen Dienst angewendeten Geschäftsbedingungen verstanden haben.

    7.  Klicken Sie auf **Erstellen**.

        ![Das Azure-Portal](images/AzureLabs-Lab6-08.png)

4.  Nachdem Sie auf **Erstellen** geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. Dies kann eine Minute dauern.

5.  Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.

    ![Das Azure-Portal](images/AzureLabs-Lab6-09.png)

6.  Klicken Sie auf die Benachrichtigung, um Ihre neue Dienstinstanz zu untersuchen.

    ![Das Azure-Portal](images/AzureLabs-Lab6-10.png)

7.  Klicken Sie in der Benachrichtigung auf die Schaltfläche **Zu Ressource** wechseln, um Ihre neue Dienstinstanz zu untersuchen.

8.  Klicken Sie auf der neuen Seite Media Service im Bereich auf der linken Seite auf den Link **Assets** (medienaktiv), der ungefähr in der Mitte nach unten angezeigt wird.

9.  Klicken Sie auf der nächsten Seite in der oberen linken Ecke der Seite auf **Hochladen**.

    ![Das Azure-Portal](images/AzureLabs-Lab6-11.png)

10. Klicken Sie auf das **Ordnersymbol,** um Ihre Dateien zu durchsuchen, und wählen Sie das erste 360 Video aus, das Sie streamen möchten. 
    
    > Sie können diesem [Link folgen, um ein Beispielvideo herunterzuladen.](https://vimeo.com/214401712)

    ![Das Azure-Portal](images/AzureLabs-Lab6-12.png)

> [!WARNING]
> Lange Dateinamen können ein Problem mit dem Encoder verursachen: Um sicherzustellen, dass Videos keine Probleme haben, sollten Sie die Länge Ihrer Videodateinamen verkürzen.

11. Die Statusanzeige wird grün, wenn der Upload des Videos abgeschlossen ist.

    ![Das Azure-Portal](images/AzureLabs-Lab6-13.png)

12. Klicken Sie auf den obigen Text (**IhrServicename – Objekte**), um zur Seite **Assets** zurückzukehren.

13. Sie werden feststellen, dass Ihr Video erfolgreich hochgeladen wurde. Klicken Sie darauf.

    ![Das Azure-Portal](images/AzureLabs-Lab6-14.png)

14. Auf der Seite, zu der Sie umgeleitet werden, werden ausführliche Informationen zu Ihrem Video angezeigt. Um Ihr Video verwenden zu können, müssen Sie es codieren, indem Sie oben links auf der Seite auf die Schaltfläche **Codieren** klicken.

    ![Das Azure-Portal](images/AzureLabs-Lab6-15.png)

15. Rechts wird ein neuer Bereich angezeigt, in dem Sie Codierungsoptionen für Ihre Datei festlegen können. Legen Sie die folgenden Eigenschaften fest (einige sind bereits standardmäßig festgelegt):

    1.  **Name des Medienencoders *Media Encoder Standard***

    2.  **Codierungsvoreinstellung *Content Adaptive Multiple Bitrate MP4***

    3.  **Auftragsname *Media Encoder Standard Verarbeitung von Video1.mp4***

    4.  **Name des *AusgabemedienobjektsVideo1.mp4 – Media Encoder Standard codiert***

        ![Das Azure-Portal](images/AzureLabs-Lab6-16.png)

16. Klicken Sie auf die Schaltfläche **Erstellen**.

17. Sie werden eine Leiste mit **hinzugefügten Codierungsauftrag** bemerken. Klicken Sie auf diese Leiste, und ein Bereich mit dem angezeigten Codierungsfortschritt wird angezeigt.

    ![Das Azure-Portal](images/AzureLabs-Lab6-17.png)

    ![Das Azure-Portal](images/AzureLabs-Lab6-18.png)

18. Warten Sie, bis der Auftrag abgeschlossen ist. Sobald dies abgeschlossen ist, können Sie den Bereich mit dem "X" oben rechts in diesem Bereich schließen.

    ![Das Azure-Portal](images/AzureLabs-Lab6-19.png)

    ![Das Azure-Portal](images/AzureLabs-Lab6-20.png)

    > [!IMPORTANT]
    > Wie lange dies dauert, hängt von der Dateigröße Ihres Videos ab. Dieser Vorgang kann einige Zeit in Anspruch nehmen.

19. Nachdem die codierte Version des Videos erstellt wurde, können Sie sie veröffentlichen, um sie zugänglich zu machen. Klicken Sie hierzu auf den blauen Link **Assets** , um zur Seite "Assets" zurückzukehren.

    ![Das Azure-Portal](images/AzureLabs-Lab6-21.png)

20. Ihr Video wird zusammen mit einem anderen angezeigt, das vom **Medienobjekttyp _Multi-Bitrate MP4_** ist.

    ![Das Azure-Portal](images/AzureLabs-Lab6-22.png)

    > [!NOTE] 
    > Möglicherweise stellen Sie fest, dass das neue Medienobjekt neben Ihrem ersten Video *Unbekannt* ist und "0" Bytes für die **Größe** aufwies. Aktualisieren Sie einfach Ihr Fenster, damit es aktualisiert werden kann.

21. Klicken Sie auf dieses neue Medienobjekt.

    ![Das Azure-Portal](images/AzureLabs-Lab6-23.png)

22. Es wird ein ähnliches Panel wie das zuvor verwendete angezeigt. Dies ist lediglich ein anderes Medienobjekt. Klicken Sie oben in der Mitte der Seite auf die Schaltfläche **Veröffentlichen.**

    ![Das Azure-Portal](images/AzureLabs-Lab6-24.png)

23. Sie werden aufgefordert, einen **Locator**( den Einstiegspunkt) auf Datei/s in Ihren Assets festzulegen. Legen Sie für Ihr Szenario die folgenden Eigenschaften fest:

    1.  **Locatortyp**  >  **Progressive .**

    2.  **Datum** und **Uhrzeit** werden von Ihrem aktuellen Datum bis zu einer Uhrzeit in der Zukunft (in diesem Fall 100 Jahre) für Sie festgelegt. Lassen Sie unverändert, oder ändern Sie es entsprechend.

    > [!NOTE]
    > Weitere Informationen zu Locators und ihren Auswahlsmöglichkeiten finden Sie in der [Azure Media Services-Dokumentation.](/azure/media-services/media-services-concepts)

24. Klicken Sie unten in diesem Bereich auf die Schaltfläche **Hinzufügen.**

    ![Das Azure-Portal](images/AzureLabs-Lab6-25.png)

25. Ihr Video ist jetzt veröffentlicht und kann mithilfe seines Endpunkts gestreamt werden. Weiter unten auf der Seite befindet sich ein Abschnitt **Dateien.** Hier werden die verschiedenen codierten Versionen Ihres Videos angezeigt. Wählen Sie die höchstmögliche Auflösung aus (in der Abbildung darunter befindet sich die Datei 1920x960), und dann wird ein Bereich auf der rechten Seite angezeigt. Dort finden Sie eine **Download-URL.** Kopieren Sie diesen **Endpunkt,** da Sie ihn später in Ihrem Code verwenden.

    ![Das Azure-Portal](images/AzureLabs-Lab6-26.png)    

    ![Das Azure-Portal](images/AzureLabs-Lab6-27.png)

    > [!NOTE] 
    > Sie können auch auf die Schaltfläche **Wiedergeben** klicken, um Ihr Video wiederzuspielen und zu testen.

26. Sie müssen nun das zweite Video hochladen, das Sie in diesem Lab verwenden werden. Führen Sie die obigen Schritte aus, und wiederholen Sie dabei den gleichen Prozess für das zweite Video. Stellen Sie sicher, dass Sie auch den zweiten **Endpunkt** kopieren. Verwenden Sie den folgenden [Link, um ein zweites Video herunterzuladen.](https://vimeo.com/214402865)

27. Nachdem beide Videos veröffentlicht wurden, können Sie mit dem nächsten Kapitel fortschreiten.

## <a name="chapter-3---setting-up-the-unity-project"></a>Kapitel 3: Einrichten der Unity-Project

Im Folgenden finden Sie eine typische Einrichtung für die Entwicklung mit dem Mixed Reality und ist daher eine gute Vorlage für andere Projekte.

1.  Öffnen Sie **Unity,** und klicken Sie auf **Neu.** 

    ![Das Azure-Portal](images/AzureLabs-Lab6-28.png)

2.  Sie müssen nun einen Unity-Project Namen angeben und **MR \_ 360VideoStreaming einfügen.** Stellen Sie sicher, dass der Projekttyp auf **3D** festgelegt ist. Legen Sie den Speicherort auf einen für Sie geeigneten Ort fest (denken Sie daran, dass näher an den Stammverzeichnissen besser ist). Klicken Sie dann auf **Projekt erstellen.**

    ![Das Azure-Portal](images/AzureLabs-Lab6-29.png)

3.  Wenn Unity geöffnet ist, sollten Sie überprüfen, ob der **Standardskript-Editor** auf Visual Studio festgelegt **ist.** Navigieren Sie zu **_Einstellungen bearbeiten,_** und navigieren Sie dann im neuen Fenster zu **Externe Tools.** Ändern Sie **den externen Skript-Editor** in **Visual Studio 2017**. Schließen Sie das Fenster **Einstellungen.**

    ![Das Azure-Portal](images/AzureLabs-Lab6-30.png)

4.  Wechseln Sie als Nächstes zu ***Dateibuild* *Einstellungen,*** und wechseln Sie die Plattform zu **Universal Windows Platform,** indem Sie auf die Schaltfläche Plattform **wechseln** klicken.

5.  Stellen Sie außerdem Sicher, dass:

    1. **Zielgerät** ist auf **Beliebiges Gerät festgelegt.**
    
    2.  **Buildtyp** ist auf **D3D festgelegt.**

    3.  **Das SDK** ist auf **Latest installed (Neueste installiert) festgelegt.**

    4.  **Visual Studio Version** ist auf **Neueste installiert festgelegt.**

    5.  **Build und Ausführung** ist auf **Lokaler Computer festgelegt.**

    6.  Machen Sie sich keine Gedanken über das Einrichten von **Szenen,** da Sie diese später einrichten werden.

    7.  Die übrigen Einstellungen sollten vorerst als Standard festgelegt werden.

        ![Einrichten der Unity-Project](images/AzureLabs-Lab6-31.png)

6.  Klicken **Sie** im Fenster Build Einstellungen auf die Schaltfläche **Player Einstellungen.** Dadurch wird der zugehörige Bereich in dem Bereich geöffnet, in dem sich der **Inspektor** befindet. 

7. In diesem Bereich müssen einige Einstellungen überprüft werden:

    1.  Auf der Registerkarte **Andere Einstellungen:**

        1.  **Die Skriptlaufzeitversion**  sollte **stabil** sein (.NET 3.5-Entsprechung).

        2. **Das Skript-Back-End** sollte **.NET sein.**

        3. **Der API-Kompatibilitätsgrad** sollte **.NET 4.6 sein.**

            ![Einrichten der Unity-Project](images/AzureLabs-Lab6-32.png)

    2.  Aktivieren Sie weiter unten im Bereich in **XR Einstellungen** (finden Sie unter **Veröffentlichen Einstellungen**), aktivieren Sie Virtual Reality **Supported (Virtual Reality Unterstützt),** und stellen Sie sicher, dass das **Windows Mixed Reality SDK** hinzugefügt wurde.

        ![Einrichten der Unity-Project](images/AzureLabs-Lab6-33.png)

    3.  Aktivieren **Sie** auf der Registerkarte Veröffentlichen Einstellungen unter **Funktionen** Folgendes:

        - **InternetClient**

            ![Einrichten der Unity-Project](images/AzureLabs-Lab6-34.png)

8.  Nachdem Sie diese Änderungen vorgenommen haben, schließen Sie das Fenster **Build Einstellungen.**

9.  Speichern Sie Ihre Project **Datei* *Project speichern**.



## <a name="chapter-4---importing-the-insideoutsphere-unity-package"></a>Kapitel 4: Importieren des InsideOutSphere Unity-Pakets

> [!IMPORTANT]
> Wenn Sie die *Unity Set up-Komponente* dieses Kurses überspringen und direkt mit dem Code fortfahren möchten, können Sie dieses [Unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage)herunterladen, es als [**benutzerdefiniertes Paket**](https://docs.unity3d.com/Manual/AssetPackages.html)in Ihr Projekt importieren und dann mit **Kapitel 5** fortfahren. Sie müssen weiterhin eine Unity-Project erstellen.

Für diesen Kurs müssen Sie ein Unity-Ressourcenpaket mit dem Namen [**InsideOutSphere.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage)herunterladen.

Importieren des **Unitypackage:**

1.  Wenn Das Unity-Dashboard vor Ihnen angezeigt wird, klicken Sie im Menü oben auf dem Bildschirm auf **Assets** und dann auf Import Package > Custom Package ( **Paket importieren > Benutzerdefiniertes Paket).**

    ![Importieren des InsideOutSphere Unity-Pakets](images/AzureLabs-Lab6-35.png)

2.  Verwenden Sie die Dateiauswahl, um das Paket **InsideOutSphere.unitypackage** auszuwählen, und klicken Sie auf **Öffnen.** Ihnen wird eine Liste der Komponenten für dieses Medienobjekt angezeigt. Bestätigen Sie den Import, indem Sie auf **Importieren** klicken.

    ![Importieren des InsideOutSphere Unity-Pakets](images/AzureLabs-Lab6-36.png)

3.  Sobald der Import abgeschlossen ist, werden Sie feststellen, dass ihrem Ordner **Assets** drei neue Ordner hinzugefügt wurden: **Materials**, **Models** und **Prefabs**. Diese Art von Ordnerstruktur ist typisch für ein Unity-Projekt.

    ![Importieren des InsideOutSphere Unity-Pakets](images/AzureLabs-Lab6-37.png)

    1.  Öffnen Sie den Ordner **Modelle,** und Sie sehen, dass das **InsideOutSphere-Modell** importiert wurde.

    2.  Im Ordner **Materials (Materialien)** finden Sie das **InsideOutSpheres-Material**  *lambert1* sowie ein Material namens *ButtonMaterial,* das vom GazeButton verwendet wird und demnächst angezeigt wird.

    3.  Der Ordner **Prefabs** enthält das **InsideOutSphere-Prefab,** das sowohl das **InsideOutSphere-Modell**  als auch *gazeButton* enthält.

    4.  **Es ist kein Code enthalten.** Sie schreiben den Code anhand dieses Kurses.


4.  Wählen Sie in der **Hierarchie** das **Objekt Hauptkamera** aus, und aktualisieren Sie die folgenden Komponenten:

    1.  **Transformieren**

        1.  Position = **X**: 0, **Y**: 0, **Z**: 0.

        2. Rotation = **X**: 0, **Y**: 0, **Z**: 0.

        3. Scale **X**: 1, **Y**: 1, **Z**: 1.

    2.  **Kamera**

        1. **Flags löschen:** Volltonfarbe.

        2.  **Clipping Planes**: Near: 0.1, Far: 6.

            ![Importieren des InsideOutSphere Unity-Pakets](images/AzureLabs-Lab6-38.png)

5.  Navigieren Sie zum Ordner **Prefab,** und ziehen Sie das **InsideOutSphere-Prefab** in den **Hierarchiebereich.**

    ![Importieren des InsideOutSphere Unity-Pakets](images/AzureLabs-Lab6-39.png)

6.  Erweitern Sie das **InsideOutSphere-Objekt** innerhalb der **Hierarchie,** indem Sie auf den kleinen Pfeil daneben klicken. Darunter wird ein **untergeordnetes** Objekt namens **GazeButton** angezeigt. Dies wird verwendet, um Szenen und somit Videos zu ändern.

    ![Importieren des InsideOutSphere Unity-Pakets](images/AzureLabs-Lab6-40.png)

7.  Klicken Sie im Inspektorfenster auf die Komponente Transform von **InsideOutSphere,** und stellen Sie sicher, dass die folgenden Eigenschaften festgelegt sind:

    |            |    TRANSFORM – POSITION   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |    TRANSFORM – ROTATION   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** -50        |  **Z** 0  |

    |            |     TRANSFORM – SKALIEREN     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

    ![Importieren des InsideOutSphere Unity-Pakets](images/AzureLabs-Lab6-41.png)

8.  Klicken Sie auf das untergeordnete **GazeButton-Objekt,** und legen Sie dessen **Transformation** wie folgt fest:

    |            |    TRANSFORM – POSITION   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 3.6|          **Y** 1.3        |  **Z** 0  |

    |            |    TRANSFORM – ROTATION   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     TRANSFORM – SKALIEREN     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

    ![Importieren des InsideOutSphere Unity-Pakets](images/AzureLabs-Lab6-42.png)


## <a name="chapter-5---create-the-videocontroller-class"></a>Kapitel 5: Erstellen der VideoController-Klasse

Die **VideoController-Klasse** hostet die beiden Videoendpunkte, die zum Streamen der Inhalte aus Azure Media Service verwendet werden.

So erstellen Sie diese Klasse:

1.  Klicken Sie mit der rechten Maustaste in den **Medienobjektordner**, der sich im **Project Bereich** befindet, und klicken Sie auf **> Ordner erstellen.** Nennen Sie den Ordner **Skripts**.

    ![Erstellen der VideoController-Klasse](images/AzureLabs-Lab6-43.png)

    ![Erstellen der VideoController-Klasse](images/AzureLabs-Lab6-44.png)

2.  Doppelklicken Sie auf den Ordner **Skripts,** um ihn zu öffnen.

3.  Klicken Sie mit der rechten Maustaste in den Ordner, und klicken Sie dann auf **> \# C-Skript erstellen.** Nennen Sie das Skript **VideoController**.

    ![Erstellen der VideoController-Klasse](images/AzureLabs-Lab6-45.png)

4.  Doppelklicken Sie auf das neue **VideoController-Skript,** um es mit **Visual Studio 2017** zu öffnen.

    ![Erstellen der VideoController-Klasse](images/AzureLabs-Lab6-46.png)

5.  Aktualisieren Sie die Namespaces am Anfang der Codedatei wie folgt:

    ```csharp
    using System.Collections;
    using UnityEngine;
    using UnityEngine.SceneManagement;
    using UnityEngine.Video;
    ```

6.  Geben Sie die folgenden Variablen in der **VideoController-Klasse** zusammen mit der **Awake()-Methode** ein:

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static VideoController instance; 
        
        /// <summary> 
        /// Reference to the Camera VideoPlayer Component.
        /// </summary> 
        private VideoPlayer videoPlayer; 
        
        /// <summary>
        /// Reference to the Camera AudioSource Component.
        /// </summary> 
        private AudioSource audioSource; 
        
        /// <summary> 
        /// Reference to the texture used to project the video streaming 
        /// </summary> 
        private RenderTexture videoStreamRenderTexture;

        /// <summary>
        /// Insert here the first video endpoint
        /// </summary>
        private string video1endpoint = "-- Insert video 1 Endpoint here --";

        /// <summary>
        /// Insert here the second video endpoint
        /// </summary>
        private string video2endpoint = "-- Insert video 2 Endpoint here --";

        /// <summary> 
        /// Reference to the Inside-Out Sphere. 
        /// </summary> 
        public GameObject sphere;

        void Awake()
        {
            instance = this;
        }
    ```

7.  Nun ist es an der Zeit, die Endpunkte aus Ihren Azure Media Service-Videos einzugeben:

    1.  Die erste in der Variablen *video1endpoint.*
    
    2.  Die zweite in der *Video2endpoint-Variablen.*

    > [!WARNING]
    > Es gibt ein bekanntes Problem bei der Verwendung von *HTTPS* in Unity mit Version 2017.4.1f1. Wenn die Videos bei der Wiedergabe einen Fehler enthalten, versuchen Sie stattdessen, "http" zu verwenden.

8.  Als Nächstes muss die **Start()-Methode** bearbeitet werden. Diese Methode wird jedes Mal ausgelöst, wenn der Benutzer die Szene wechselt (also das Video wechselt), indem er sich die Schaltfläche Anvieren ansieht.

    ```csharp
        // Use this for initialization
        void Start()
        {
            Application.runInBackground = true;
            StartCoroutine(PlayVideo());
        }
    ```

9.  Fügen Sie nach der **Start()-Methode** die *IEnumerator-Methode* **PlayVideo()** ein, die verwendet wird, um Videos nahtlos zu starten (sodass kein Stutter zu sehen ist).

    ```csharp
        private IEnumerator PlayVideo()
        {
            // create a new render texture to display the video 
            videoStreamRenderTexture = new RenderTexture(2160, 1440, 32, RenderTextureFormat.ARGB32);

            videoStreamRenderTexture.Create();

            // assign the render texture to the object material 
            Material sphereMaterial = sphere.GetComponent<Renderer>().sharedMaterial;

            //create a VideoPlayer component 
            videoPlayer = gameObject.AddComponent<VideoPlayer>();

            // Set the video to loop. 
            videoPlayer.isLooping = true;

            // Set the VideoPlayer component to play the video from the texture 
            videoPlayer.renderMode = VideoRenderMode.RenderTexture;

            videoPlayer.targetTexture = videoStreamRenderTexture;

            // Add AudioSource 
            audioSource = gameObject.AddComponent<AudioSource>();

            // Pause Audio play on Awake 
            audioSource.playOnAwake = true;
            audioSource.Pause();

            // Set Audio Output to AudioSource 
            videoPlayer.audioOutputMode = VideoAudioOutputMode.AudioSource;
            videoPlayer.source = VideoSource.Url;

            // Assign the Audio from Video to AudioSource to be played 
            videoPlayer.EnableAudioTrack(0, true);
            videoPlayer.SetTargetAudioSource(0, audioSource);

            // Assign the video Url depending on the current scene 
            switch (SceneManager.GetActiveScene().name)
            {
                case "VideoScene1":
                    videoPlayer.url = video1endpoint;
                    break;

                case "VideoScene2":
                    videoPlayer.url = video2endpoint;
                    break;

                default:
                    break;
            }

            //Set video To Play then prepare Audio to prevent Buffering 
            videoPlayer.Prepare();

            while (!videoPlayer.isPrepared)
            {
                yield return null;
            }

            sphereMaterial.mainTexture = videoStreamRenderTexture;

            //Play Video 
            videoPlayer.Play();

            //Play Sound 
            audioSource.Play();

            while (videoPlayer.isPlaying)
            {
                yield return null;
            }
        }
    ```

10. Die letzte Methode, die Sie für diese Klasse benötigen, ist die **ChangeScene()-Methode,** die zum Austauschen zwischen Szenen verwendet wird.

    ```csharp
        public void ChangeScene()
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name == "VideoScene1" ? "VideoScene2" : "VideoScene1");
        }
    ```

    > [!TIP] 
    > Die **ChangeScene()-Methode** verwendet ein praktisches \# C-Feature, das als *bedingter Operator* bezeichnet wird. Dies ermöglicht die Überprüfung von Bedingungen und anschließende Rückgabe von Werten basierend auf dem Ergebnis der Überprüfung innerhalb einer einzelnen Anweisung. Folgen Sie diesem [Link, um mehr über den bedingten Operator zu erfahren.](/dotnet/csharp/language-reference/operators/conditional-operator)

11. Speichern Sie Ihre Änderungen in Visual Studio, bevor Sie zu Unity zurückkehren.

12. Klicken Sie im Unity-Editor zurück, und ziehen Sie die **VideoController-Klasse** [von]{.underline} des **Ordners Scripts** in das **Objekt Hauptkamera** im **Hierarchiebereich.**

13. Klicken Sie auf die **Hauptkamera,** und sehen Sie sich den **Inspektorbereich an.** Sie werden feststellen, dass in der neu hinzugefügten Skriptkomponente ein Feld mit einem leeren Wert vorhanden ist. Dies ist ein Verweisfeld, das auf die öffentlichen Variablen in Ihrem Code ausgerichtet ist.

14. Ziehen Sie das **InsideOutSphere-Objekt** aus dem **Hierarchiebereich** in den **Sphere-Slot,** wie in der folgenden Abbildung dargestellt.

    ![Erstellen der VideoController-Klasse ](images/AzureLabs-Lab6-47.png)
     ![ Erstellen der VideoController-Klasse](images/AzureLabs-Lab6-48.png)

## <a name="chapter-6---create-the-gaze-class"></a>Kapitel 6: Erstellen der Gaze-Klasse

Diese Klasse ist für die Erstellung eines **Raycasts** verantwortlich, der von der **Hauptkamera** nach vorne projiziert wird, um zu erkennen, welches Objekt der Benutzer ansieht. In diesem Fall muss **raycast** ermitteln, ob der Benutzer das **GazeButton-Objekt** in der Szene betrachtet und ein Verhalten auslöst.

So erstellen Sie diese Klasse:

1.  Wechseln Sie zum Ordner **Skripts,** den Sie zuvor erstellt haben.

2.  Klicken Sie mit der rechten Maustaste in den **Project** Bereich ***C-Skript* \# erstellen**. Nennen Sie das Skript **Gaze**.

3.  Doppelklicken Sie auf das neue ***Gaze** _-Skript, um es mit _ *Visual Studio 2017* zu öffnen.*

4.  Stellen Sie sicher, dass sich der folgende Namespace am Anfang des Skripts befindet, und entfernen Sie alle anderen:

    ```csharp
    using UnityEngine;
    ```

5.  Fügen Sie dann die folgenden Variablen in der **Gaze-Klasse** hinzu:

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static Gaze instance;

        /// <summary> 
        /// Provides a reference to the object the user is currently looking at. 
        /// </summary> 
        public GameObject FocusedGameObject { get; private set; }

        /// <summary> 
        /// Provides a reference to compare whether the user is still looking at 
        /// the same object (and has not looked away). 
        /// </summary> 
        private GameObject oldFocusedObject = null;

        /// <summary> 
        /// Max Ray Distance 
        /// </summary> 
        float gazeMaxDistance = 300;

        /// <summary> 
        /// Provides whether an object has been successfully hit by the raycast. 
        /// </summary> 
        public bool Hit { get; private set; }
    ```

6.  Code für die **Methoden "Awake()"** und **"Start()"** muss nun hinzugefügt werden.

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton 
            instance = this;
        }

        void Start()
        {
            FocusedGameObject = null;
        }
    ```

7.  Fügen Sie den folgenden Code in der **Update()-Methode** hinzu, um einen Raycast zu pro projectieren und den Zieltreffer zu erkennen:

    ```csharp
        void Update()
        {
            // Set the old focused gameobject. 
            oldFocusedObject = FocusedGameObject;
            RaycastHit hitInfo;

            // Initialise Raycasting. 
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, gazeMaxDistance);

            // Check whether raycast has hit. 
            if (Hit == true)
            {
                // Check whether the hit has a collider. 
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at. 
                    FocusedGameObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null. 
                    FocusedGameObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;
            }

            // Check whether the previous focused object is this same 
            // object (so to stop spamming of function). 
            if (FocusedGameObject != oldFocusedObject)
            {
                // Compare whether the new Focused Object has the desired tag we set previously. 
                if (FocusedGameObject.CompareTag("GazeButton"))
                {
                    FocusedGameObject.SetActive(false);
                    VideoController.instance.ChangeScene();
                }
            }
        }
    ```

8.  Speichern Sie Ihre Änderungen in Visual Studio, bevor Sie zu Unity zurückkehren.

9.  Klicken Sie auf die **Klasse Anvisierung,** und ziehen Sie sie aus dem Ordner Skripts in das Objekt Hauptkamera im **Hierarchiebereich.**

## <a name="chapter-7---setup-the-two-unity-scenes"></a>Kapitel 7: Einrichten der beiden Unity-Szenen

Der Zweck dieses Kapitels besteht darin, die beiden Szenen einzurichten, die jeweils ein Video zum Streamen hosten. Sie duplizieren die Szene, die Sie bereits erstellt haben, sodass Sie sie nicht erneut einrichten müssen. Sie bearbeiten dann jedoch die neue Szene, sodass sich das *GazeButton-Objekt* an einem anderen Ort befindet und eine andere Darstellung hat. Dies soll zeigen, wie zwischen Szenen gewechselt werden kann.

1.  Gehen Sie dazu zu **Datei > Szene speichern als...**. Ein Speicherfenster wird angezeigt. Klicken Sie auf die Schaltfläche **Neuer Ordner.**

    ![Kapitel 7: Einrichten der beiden Unity-Szenen](images/AzureLabs-Lab6-49.png)

2.  Nennen Sie den Ordner **Scenes**.

3.  Das Fenster **Szene speichern** ist weiterhin geöffnet. Öffnen Sie den neu erstellten Ordner **Scenes.**

4.  Geben Sie im Textfeld **Dateiname:** **videoScene1 ein,** und klicken Sie dann auf **Speichern.**

5.  Öffnen Sie in Unity den Ordner **Scenes,** und klicken Sie mit der linken Maustaste auf Ihre **VideoScene1-Datei.** Verwenden Sie Ihre Tastatur, und drücken Sie **STRG+D,** um diese Szene zu duplizieren.

    > [!TIP]
    > Der Befehl **Duplizieren** kann auch ausgeführt werden, indem Sie zu **Bearbeiten > Duplizieren** navigieren.

6.  Unity erhöht automatisch die Anzahl der Szenennamen, überprüft sie jedoch trotzdem, um sicherzustellen, dass sie mit dem zuvor eingefügten Code übereinstimmt.

    >  Sie sollten **über VideoScene1** und **VideoScene2 verfügen.**

7.  Wechseln Sie in ihren beiden Szenen zu **Datei > Build Einstellungen**. Wenn das Fenster **Build Einstellungen** geöffnet ist, ziehen Sie Ihre Szenen in den Abschnitt Szenen **im Build.**

    ![Kapitel 7: Einrichten der beiden Unity-Szenen](images/AzureLabs-Lab6-50.png)

    > [!TIP] 
    > Sie können beide Szenen in Ihrem Ordner **Szenen** auswählen, indem Sie die **STRG-Taste** gedrückt halten und dann mit der linken Maustaste auf jede Szene klicken und schließlich beides ziehen.

8.  Schließen Sie das Fenster **Build Einstellungen,** und doppelklicken Sie auf **VideoScene2**.

9.  Wenn die zweite Szene geöffnet ist, klicken Sie auf das untergeordnete **GazeButton-Objekt** von **InsideOutSphere,** und legen Sie dessen Transformation wie folgt fest:

    |            |    TRANSFORM – POSITION   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |         **Y** 1.3         | **Z** 3.6 |

    |            |    TRANSFORM – ROTATION   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     TRANSFORM – SKALIERUNG     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

10. Wenn das untergeordnete **GazeButton-Element** noch ausgewählt ist, sehen Sie sich den **Inspector** und den **Gitternetzfilter** an. Klicken Sie auf das kleine Ziel neben dem **Gitternetzverweisfeld:**

    ![Kapitel 7: Einrichten der beiden Unity-Szenen](images/AzureLabs-Lab6-51.png)

11. Ein Popupfenster **Gitternetz auswählen** wird angezeigt. Doppelklicken Sie in der Liste der **Objekte** auf das **Cubegitternetz.**

    ![Kapitel 7: Einrichten der beiden Unity-Szenen](images/AzureLabs-Lab6-52.png)

12. Der **Gitternetzfilter** wird aktualisiert und ist jetzt ein **Cube.** Klicken Sie nun auf das **Zahnradsymbol** neben **Sphere Collider** und dann auf **Komponente entfernen**, um den Collider aus diesem Objekt zu löschen.

    ![Kapitel 7: Einrichten der beiden Unity-Szenen](images/AzureLabs-Lab6-53.png)

13. Wenn **GazeButton** weiterhin ausgewählt ist, klicken Sie unten im **Inspektor** auf die Schaltfläche **Komponente hinzufügen.** Geben Sie im Suchfeld **feld** ein, und **Box Collider** ist eine Option. Klicken Sie darauf, um Ihrem **GazeButton-Objekt** einen **Box Collider** hinzuzufügen.

    ![Kapitel 7: Einrichten der beiden Unity-Szenen](images/AzureLabs-Lab6-54.png)

14. **GazeButton** wurde nun teilweise aktualisiert, sodass es anders aussieht. Sie erstellen nun jedoch ein neues **Material,** sodass es völlig anders aussieht und einfacher als ein anderes Objekt zu erkennen ist als das Objekt in der ersten Szene.

15. Navigieren Sie im Project **Bereich** zu Ihrem Ordner **Materials** . Duplizieren Sie das **ButtonMaterial** Material (drücken Sie **STRG** D auf der Tastatur, oder klicken Sie mit der linken Maustaste auf material , und  +   wählen Sie dann im Menü Datei **bearbeiten** die Option **Duplizieren** aus). 

    ![Kapitel 7 – Einrichten der beiden Unity-Szenen ](images/AzureLabs-Lab6-55.png)
     ![ Kapitel 7 – Einrichten der beiden Unity-Szenen](images/AzureLabs-Lab6-56.png)

16. Wählen Sie das neue **ButtonMaterial** Material (hier **ButtonMaterial 1** genannt) aus, und klicken Sie im **Inspektor** auf das **Farbfenster Albedo.** Es wird ein Popupfenster angezeigt, in dem Sie eine andere Farbe auswählen können (wählen Sie die gewünschte Farbe aus), und schließen Sie das Popup. Das Material ist eine eigene Instanz und unterscheidet sich vom Original.

    ![Kapitel 7: Einrichten der beiden Unity-Szenen](images/AzureLabs-Lab6-57.png)

17. Ziehen Sie das neue **Material** auf das untergeordnete **GazeButton-Element,** um nun sein Aussehen vollständig zu aktualisieren, sodass es leicht von der Ersten Szenenschaltfläche unterschieden werden kann.

    ![Kapitel 7: Einrichten der beiden Unity-Szenen](images/AzureLabs-Lab6-58.png)

18. An diesem Punkt können Sie das Projekt im Editor testen, bevor Sie das UWP-Projekt erstellen.

    -  Klicken Sie im **Editor** auf die Schaltfläche **Wiedergabe,** und tragen Sie Ihr Headset.

        ![Kapitel 7: Einrichten der beiden Unity-Szenen](images/AzureLabs-Lab6-59.png)

19. Sehen Sie sich die beiden **GazeButton-Objekte** an, um zwischen dem ersten und zweiten Video zu wechseln.

## <a name="chapter-8---build-the-uwp-solution"></a>Kapitel 8: Erstellen der UWP-Lösung

Nachdem Sie sichergestellt haben, dass der Editor keine Fehler aufweist, können Sie erstellen.

So erstellen Sie:

1.  Speichern Sie die aktuelle Szene, indem Sie auf **Datei > Speichern** klicken.

2.  Aktivieren Sie das Kontrollkästchen **Unity C \# Projects** (dies ist wichtig, da Sie die Klassen nach Abschluss des Builds bearbeiten können).

3.  Wechseln Sie zu **Datei > Build Einstellungen**, und klicken Sie auf **Erstellen.**

4.  Sie werden aufgefordert, den Ordner auszuwählen, in dem Sie die Projektmappe erstellen möchten.

5.  Erstellen Sie einen **ORDNER BUILDS,** und erstellen Sie in diesem Ordner einen anderen Ordner mit einem geeigneten Namen Ihrer Wahl.

6.  Klicken Sie auf Ihren neuen Ordner und dann auf **Ordner auswählen,** um diesen Ordner auszuwählen, um den Build an diesem Speicherort zu starten.

    ![Kapitel 8 – Erstellen der UWP-Lösung ](images/AzureLabs-Lab6-60.png)
     ![ Kapitel 8 – Erstellen der UWP-Lösung](images/AzureLabs-Lab6-61.png)

7.  Sobald die Erstellung von Unity abgeschlossen ist (dies kann einige Zeit dauern), wird ein **Datei-Explorer-Fenster** am Speicherort Ihres Builds geöffnet.

## <a name="chapter-9---deploy-on-local-machine"></a>Kapitel 9: Bereitstellen auf einem lokalen Computer

Sobald der Build abgeschlossen ist, wird ein **Datei-Explorer-Fenster** am Speicherort Ihres Builds angezeigt. Öffnen Sie den Ordner, den Sie benannt und erstellt haben, und doppelklicken Sie dann auf die Projektmappendatei (SLN) in diesem Ordner, um Ihre Projektmappe mit Visual Studio 2017 zu öffnen.

Sie müssen ihre App nur noch auf Ihrem Computer (oder auf dem *lokalen Computer)* bereitstellen.

So stellen Sie auf dem lokalen Computer bereit:

1.  Öffnen **Sie in Visual Studio 2017** die soeben erstellte Projektmappendatei.

2.  Wählen Sie in der **Projektmappenplattform** die Option **x86, Lokaler Computer aus.**

3.  Wählen Sie in der **Projektmappenkonfiguration** **debuggen** aus.

    ![Kapitel 9 : Bereitstellen auf einem lokalen Computer](images/AzureLabs-Lab6-62.png)

4.  Sie müssen jetzt alle Pakete in Ihrer Projektmappe wiederherstellen. Klicken Sie mit der rechten Maustaste auf Ihre **Projektmappe,** und klicken Sie auf **NuGet Pakete für Projektmappe wiederherstellen...**

    > [!NOTE] 
    > Dies geschieht, da die Pakete, die Unity erstellt hat, für die Arbeit mit verweisenden lokalen Computern verwendet werden müssen.

5.  Wechseln Sie zum **Menü Erstellen,** und klicken Sie auf **Lösung bereitstellen,** um die Anwendung auf Ihren Computer zu querladen. Visual Studio erstellt zuerst Ihre Anwendung und stellt sie dann bereit.

6.  Ihre App sollte nun in der Liste der installierten Apps angezeigt werden, die gestartet werden können.

    ![Kapitel 9 : Bereitstellen auf einem lokalen Computer](images/AzureLabs-Lab6-63.png)

Wenn Sie die Mixed Reality Anwendung ausführen, befinden Sie sich innerhalb des **InsideOutSphere-Modells,** das Sie in Ihrer App verwendet haben. In dieser Kugel wird das Video gestreamt und bietet eine 360-Grad-Ansicht des eingehenden Videos (das für diese Art von Perspektive gedreht wurde). Keine Überraschung, wenn das Laden des Videos einige Sekunden dauert, ihre App ihrer verfügbaren Internetgeschwindigkeit unterliegt, da das Video abgerufen und dann heruntergeladen werden muss, um in Ihre App zu streamen.
Wenn Sie bereit sind, wechseln Sie die Szenen, und öffnen Sie Ihr zweites Video, indem Sie auf die rote Kugel dürfen! Kehren Sie dann zurück, indem Sie den blauen Würfel in der zweiten Szene verwenden!

## <a name="your-finished-azure-media-service-application"></a>Ihre fertige Azure Media Service-Anwendung
 
Herzlichen Glückwunsch! Sie haben eine Mixed Reality-App erstellt, die Azure Media Service zum Streamen von 360 Videos nutzt.

![Labergebnis](images/AzureLabs-Lab6-00.png)

![Labergebnis](images/AzureLabs-Lab6-01.png)

## <a name="bonus-exercises"></a>Bonusübungen

**Übung 1**

Es ist durchaus möglich, nur eine einzelne Szene zu verwenden, um Videos in diesem Tutorial zu ändern. Experimentieren Sie mit Ihrer Anwendung, und schaffen Sie es in eine einzige Szene! Fügen Sie der Mischung vielleicht sogar ein weiteres Video hinzu.

**Übung 2**

Experimentieren Sie mit Azure und Unity, und versuchen Sie, die Möglichkeit zu implementieren, dass die App je nach Stärke einer Internetverbindung automatisch ein Video mit einer anderen Dateigröße auswählt.