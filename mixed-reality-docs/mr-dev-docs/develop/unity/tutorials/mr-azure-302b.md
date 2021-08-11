---
title: 'HoloLens (1. Generation) und Azure 302b: Benutzerdefiniertes Sehen'
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie ein Machine Learning-Modell trainieren und dann das trainierte Modell verwenden, um ähnliche Objekte in einer Mixed Reality-Anwendung zu erkennen.
author: drneil
ms.author: jemccull
ms.date: 07/03/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, Tutorial, API, custom vision, hololens, immersive, vr, Windows 10, Visual Studio
ms.openlocfilehash: 25f07dddf53cf8c279f99d230d1bd4d206a663eba884abc0dd32313bce4b7b43
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217582"
---
# <a name="hololens-1st-gen-and-azure-302b-custom-vision"></a>HoloLens (1. Generation) und Azure 302b: Custom Vision

<br>

>[!NOTE]
>Die Tutorials der Mixed Reality Academy wurden im Hinblick auf HoloLens (1. Gen.) und immersive Mixed Reality-Headsets entworfen.  Daher halten wir es für wichtig, diese Tutorials für Entwickler verfügbar zu halten, die noch nach Anleitung beim Entwickeln für diese Geräte suchen.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für HoloLens 2 verwendet werden.  Sie werden gewartet, um weiterhin auf den unterstützten Geräten zu funktionieren. Es wird eine neue Reihe von Tutorials geben, die in Zukunft veröffentlicht werden, die veranschaulichen, wie sie für HoloLens 2 entwickelt werden.  Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn sie veröffentlicht werden.

<br>


In diesem Kurs erfahren Sie, wie Sie benutzerdefinierte visuelle Inhalte in einem bereitgestellten Bild mithilfe von Azure Custom Vision-Funktionen in einer Mixed Reality-Anwendung erkennen.

Mit diesem Dienst können Sie ein Machine Learning-Modell mithilfe von Objektbildern trainieren. Anschließend verwenden Sie das trainierte Modell, um ähnliche Objekte zu erkennen, wie durch die Kameraerfassung von Microsoft HoloLens oder eine Kamera, die mit Ihrem PC für immersive Headsets (VR) verbunden ist.

![Kursergebnis](images/AzureLabs-Lab302b-00.png)

Azure Custom Vision ist ein Microsoft Cognitive Service, mit dem Entwickler benutzerdefinierte Bildklassifizierungen erstellen können. Diese Klassifizierer können dann mit neuen Bildern verwendet werden, um Objekte in diesem neuen Bild zu erkennen oder zu klassifizieren. Der Dienst bietet ein einfaches, benutzerfreundliches Onlineportal, um den Prozess zu optimieren. Weitere Informationen finden Sie auf der [Seite Azure Custom Vision-Dienst.](/azure/cognitive-services/custom-vision-service/home)

Nach Abschluss dieses Kurses verfügen Sie über eine Mixed Reality-Anwendung, die in zwei Modi funktionieren kann:

-   **Analysemodus:** Manuelles Einrichten des Custom Vision-Diensts durch Hochladen von Bildern, Erstellen von Tags und Trainieren des Diensts zum Erkennen verschiedener Objekte (in diesem Fall Maus und Tastatur). Anschließend erstellen Sie eine HoloLens-App, die Bilder mithilfe der Kamera erfasst und versucht, diese Objekte in der realen Welt zu erkennen.

-   **Trainingsmodus:** Sie implementieren Code, der einen "Trainingsmodus" in Ihrer App aktiviert. Im Trainingsmodus können Sie Bilder mithilfe der Kamera des HoloLens erfassen, die erfassten Bilder in den Dienst hochladen und das Custom Vision-Modell trainieren.

In diesem Kurs erfahren Sie, wie Sie die Ergebnisse des Custom Vision-Diensts in eine Unity-basierte Beispielanwendung integrieren. Sie müssen diese Konzepte auf eine benutzerdefinierte Anwendung anwenden, die Sie möglicherweise erstellen.

## <a name="device-support"></a>Geräteunterstützung

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td> MR und Azure 302b: Custom Vision</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Während sich dieser Kurs in erster Linie auf HoloLens konzentriert, können Sie auch das in diesem Kurs gelernte Lernen auf immersive Headsets (VR) Windows Mixed Reality. Da immersive Headsets (VR) nicht über barrierefreie Kameras verfügen, benötigen Sie eine externe Kamera, die mit Ihrem PC verbunden ist. Während Sie dem Kurs folgen, werden Ihnen Hinweise zu allen Änderungen angezeigt, die Sie ggf. verwenden müssen, um immersive Headsets (VR) zu unterstützen.

## <a name="prerequisites"></a>Voraussetzungen

> [!NOTE]
> Dieses Tutorial richtet sich an Entwickler, die grundlegende Erfahrung mit Unity und C# haben. Beachten Sie auch, dass die Voraussetzungen und die geschriebenen Anweisungen in diesem Dokument darstellen, was zum Zeitpunkt der Erstellung (Juli 2018) getestet und überprüft wurde. Sie können die neueste Software verwenden, wie im Artikel [installieren der Tools](../../install-the-tools.md) aufgeführt. Es sollte jedoch nicht davon ausgegangen werden, dass die Informationen in diesem Kurs perfekt mit dem übereinstimmen, was Sie in neuerer Software finden, als unten aufgeführt.

Für diesen Kurs wird die folgende Hardware und Software empfohlen:

- Ein Entwicklungs-PC, [der mit Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) für die Entwicklung immersiver Headsets (VR) kompatibel ist
- [Windows 10 Fall Creators Update (oder höher) mit aktivierter Option "Entwicklermodus"](../../install-the-tools.md#installation-checklist)
- [Das neueste Windows 10 SDK](../../install-the-tools.md#installation-checklist)
- [Unity 2017.4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- Ein [Windows Mixed Reality immersives Headset (VR)](../../../discover/immersive-headset-hardware-details.md) oder [ein Microsoft HoloLens](/hololens/hololens1-hardware) mit aktiviertem Entwicklermodus
- Eine Kamera, die mit Ihrem PC verbunden ist (für die Entwicklung immersiver Headsets)
- Internetzugriff für Azure-Setup und Custom Vision API-Abruf
- Eine Reihe von mindestens fünf (5) Bildern (zehn (10) empfohlen) für jedes Objekt, das der Custom Vision Dienst erkennen soll. Wenn Sie möchten, können Sie die Bilder verwenden, [die bereits in diesem Kurs bereitgestellt wurden (eine Computermaus und eine Tastatur). ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip)

## <a name="before-you-start"></a>Vorbereitung

1.  Um Probleme bei der Erstellung dieses Projekts zu vermeiden, wird dringend empfohlen, das in diesem Tutorial erwähnte Projekt in einem Stammordner oder in einem Ordner in der Nähe des Stammordners zu erstellen (lange Ordnerpfade können zur Buildzeit Probleme verursachen).
2.  Richten Sie Ihre HoloLens ein, und testen Sie sie. Wenn Sie Unterstützung beim Einrichten Ihrer HoloLens benötigen, [besuchen Sie unbedingt den Artikel HoloLens Setup.](/hololens/hololens-setup) 
3.  Es ist eine gute Idee, Kalibrierung und Sensoroptimierung durchzuführen, wenn Sie mit der Entwicklung einer neuen HoloLens-App beginnen (manchmal kann es hilfreich sein, diese Aufgaben für jeden Benutzer auszuführen). 

Hilfe zur Kalibrierung finden Sie unter diesem [Link zum HoloLens Kalibrierungsartikel](/hololens/hololens-calibration#hololens-2).

Hilfe zur Sensoroptimierung finden Sie unter diesem [Link zum artikel HoloLens Sensoroptimierung.](/hololens/hololens-updates)

## <a name="chapter-1---the-custom-vision-service-portal"></a>Kapitel 1: Das Custom Vision-Dienstportal

Um den *Custom Vision-Dienst* in Azure zu verwenden, müssen Sie eine Instanz des Diensts so konfigurieren, dass sie Ihrer Anwendung zur Verfügung gestellt wird.

1.  Navigieren Sie zunächst [zur *Hauptseite des Custom Vision-Diensts.*](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)

2.  Klicken Sie auf die Schaltfläche **Erste Schritte.**

    ![Erste Schritte mit Custom Vision Service](images/AzureLabs-Lab302b-01.png)

3.  Melden Sie sich beim *Custom Vision-Dienstportal* an.

    ![Anmelden beim Portal](images/AzureLabs-Lab302b-02.png)

    > [!NOTE]
    > Wenn Sie noch nicht über ein Azure-Konto verfügen, müssen Sie eins erstellen. Wenn Sie dieses Tutorial in einer Classroom- oder Lab-Situation durchgehen, bitten Sie Ihren Dozenten oder einen der Proctors um Hilfe beim Einrichten Ihres neuen Kontos.

4.  Sobald Sie zum ersten Mal angemeldet sind, werden Sie im Bereich *Nutzungsbedingungen* aufgefordert. Klicken Sie auf das Kontrollkästchen, um den Bedingungen zuzustimmen. Klicken Sie dann auf **Ich stimme zu.**

    ![Vertragsbedingungen](images/AzureLabs-Lab302b-03.png)

5.  Nachdem Sie den Bedingungen zugestimmt haben, werden Sie zum Abschnitt *Projekte* des Portals navigiert. Klicken Sie auf **Neu Project**.

    ![Erstellen eines neuen Projekts](images/AzureLabs-Lab302b-04.png)

6.  Auf der rechten Seite wird eine Registerkarte angezeigt, auf der Sie aufgefordert werden, einige Felder für das Projekt anzugeben.

    1.  Fügen Sie einen *Namen* für Ihr Projekt ein.

    2.  Fügen Sie eine *Beschreibung* für Ihr Projekt ein *(optional).*

    3.  Wählen Sie eine *Ressourcengruppe* aus, oder erstellen Sie eine neue. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, Steuern des Zugriffs, Bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt zugeordnet sind (z. B. diese Kurse), einer gemeinsamen Ressourcengruppe zuzuordnen.

    4. Festlegen der *Project-Typen* auf **Klassifizierung**
    
    5. Legen Sie *die Domänen* auf **Allgemein** fest.

        ![Festlegen der Domänen](images/AzureLabs-Lab302b-05.png)

        > Weitere Informationen zu Azure-Ressourcengruppen finden Sie [im Artikel zu Ressourcengruppen.](/azure/azure-resource-manager/resource-group-portal)

7.  Wenn Sie fertig sind, klicken Sie auf **Projekt erstellen**. Sie werden zur Seite Custom Vision Service, project (Dienst, Projekt) umgeleitet.

## <a name="chapter-2---training-your-custom-vision-project"></a>Kapitel 2: Trainieren Ihres Custom Vision-Projekts

Sobald Sie sich im Custom Vision-Portal befinden, besteht Ihr primäres Ziel darin, Ihr Projekt so zu trainieren, dass bestimmte Objekte in Bildern erkannt werden. Sie benötigen mindestens fünf (5) Bilder, obwohl zehn (10) für jedes Objekt bevorzugt werden, das ihre Anwendung erkennen soll. [Sie können die in diesem Kurs bereitgestellten Bilder (Computermaus und Tastatur) verwenden.](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip) 

So trainieren Sie Ihr Custom Vision Service-Projekt:

1.  Klicken Sie auf die **+** Schaltfläche neben **Tags.**

    ![Hinzufügen eines neuen Tags](images/AzureLabs-Lab302b-06.png)

2.  Fügen Sie den **Namen** des Objekts hinzu, das Sie erkennen möchten. Klicken Sie auf **Speichern**.

    ![Hinzufügen des Objektnamens und Speichern](images/AzureLabs-Lab302b-07.png)

3.  Sie werden feststellen, dass Ihr **Tag** hinzugefügt wurde (Möglicherweise müssen Sie Die Seite neu laden, damit sie angezeigt wird). Klicken Sie neben dem neuen Tag auf das Kontrollkästchen, falls es noch nicht aktiviert ist.

    ![Neues Tag aktivieren](images/AzureLabs-Lab302b-08.png)

4.  Klicken Sie in der Mitte der Seite auf **Bilder hinzufügen.**

    ![Hinzufügen von Bildern](images/AzureLabs-Lab302b-09.png)

5.  Klicken Sie auf **Lokale Dateien durchsuchen,** suchen Sie nach den Bildern, die Sie hochladen möchten, und wählen Sie dann die Bilder aus, wobei der Mindestwert fünf (5) ist. Denken Sie daran, dass alle diese Bilder das Objekt enthalten sollten, das Sie trainieren.

    > [!NOTE]
    >  Sie können mehrere Bilder gleichzeitig auswählen, um sie hochzuladen.

6.  Sobald die Bilder auf der Registerkarte angezeigt werden, wählen Sie das entsprechende Tag im Feld **Meine Tags aus.**

    ![Auswählen von Tags](images/AzureLabs-Lab302b-10.png)

7.  Klicken Sie auf **Hochladen Dateien**. Die Dateien beginnen mit dem Hochladen. Nachdem Sie die Bestätigung des Uploads erhalten haben, klicken Sie auf **Fertig.**

    ![Hochladen von Dateien](images/AzureLabs-Lab302b-11.png)

8.  Wiederholen Sie den gleichen Vorgang, um ein neues **Tag** namens **Tastatur** zu erstellen und die entsprechenden Fotos dafür hochzuladen. Deaktivieren Sie  Maus, *nachdem* Sie die neuen Tags erstellt haben, um das Fenster *Bilder hinzufügen* anzuzeigen.

9.  Nachdem Sie beide Tags eingerichtet haben, klicken Sie auf **Trainieren,** und die erste Trainingsiteration beginnt mit der Erstellung.

    ![Aktivieren der Trainingsiteration](images/AzureLabs-Lab302b-12.png)

10. Sobald sie erstellt wurde, können Sie zwei Schaltflächen mit dem Namen **Make default (Standard festlegen)** und **prediction URL (Vorhersage-URL)** sehen. Klicken Sie zuerst auf **Standardwert festlegen** und dann auf **Vorhersage-URL.**

    ![Festlegen der Standard- und Vorhersage-URL](images/AzureLabs-Lab302b-13.png)

    > [!NOTE] 
    > Die Endpunkt-URL, die von diesem bereitgestellt wird, wird auf festgelegt, je nachdem, welche *Iteration* als Standard markiert wurde. Wenn Sie also später eine neue *Iteration* erstellen und als Standard aktualisieren, müssen Sie Ihren Code nicht ändern.

11. Nachdem Sie auf *Vorhersage-URL* geklickt haben, öffnen Sie *Editor*, kopieren Sie die **URL** und den **Vorhersageschlüssel,** und fügen Sie sie ein, damit Sie sie später im Code abrufen können, wenn Sie sie benötigen.

    ![Kopieren und Einfügen von URL und Prediction-Key](images/AzureLabs-Lab302b-14.png)

12. Klicken Sie oben rechts auf dem Bildschirm auf das **Zahnrad.**

    ![Klicken Sie auf das Zahnradsymbol, um die Einstellungen zu öffnen.](images/AzureLabs-Lab302b-15.png)

13. Kopieren Sie den **Trainingsschlüssel,** und fügen Sie ihn zur späteren Verwendung in eine *Editor* ein.

    ![Kopieren des Trainingsschlüssels](images/AzureLabs-Lab302b-16.png)

14. Kopieren Sie außerdem Ihre **Project-ID,** und fügen Sie sie zur späteren Verwendung in Ihre *Editor-Datei* ein.

    ![Kopieren der Projekt-ID](images/AzureLabs-Lab302b-16a.png)

## <a name="chapter-3---set-up-the-unity-project"></a>Kapitel 3: Einrichten des Unity-Projekts

Im Folgenden finden Sie eine typische Einrichtung für die Entwicklung mit Mixed Reality und ist daher eine gute Vorlage für andere Projekte.

1.  Öffnen Sie *Unity,* und klicken Sie auf **Neu.**

    ![Erstellen eines neuen Unity-Projekts](images/AzureLabs-Lab302b-17.png)

2.  Sie müssen nun einen Unity-Projektnamen angeben. Fügen Sie **AzureCustomVision ein.** Stellen Sie sicher, dass die Projektvorlage auf **3D** festgelegt ist. Legen Sie den **Speicherort** auf einen für Sie geeigneten Speicherort fest (denken Sie daran, dass näher an den Stammverzeichnissen besser ist). Klicken Sie dann auf **Projekt erstellen.**

    ![Konfigurieren von Projekteinstellungen](images/AzureLabs-Lab302b-18.png)

3.  Wenn Unity geöffnet ist, sollten Sie überprüfen, ob der **Standardskript-Editor** auf **Visual Studio** festgelegt ist. Navigieren Sie zu * >  *Einstellungen* *bearbeiten,** und navigieren Sie dann im neuen Fenster zu **Externe Tools**. Ändern Sie **den externen Skript-Editor** in **Visual Studio 2017**. Schließen Sie das Fenster **Einstellungen.**

    ![Konfigurieren externer Tools](images/AzureLabs-Lab302b-19.png)

4.  Wechseln Sie als Nächstes zu **Datei > Build Einstellungen,** wählen Sie **Universelle Windows Plattform** aus, und klicken Sie dann auf die Schaltfläche **Plattform wechseln,** um Ihre Auswahl anzuwenden.

    ![Konfigurieren von Buildeinstellungen ](images/AzureLabs-Lab302b-20.png)

5.  Stellen Sie im **Datei-> Build Einstellungen,** und stellen Sie Sicher, dass:

    1.  **Zielgerät** ist auf **HoloLens**

        > Legen Sie für die immersiven Headsets **Zielgerät** auf *Beliebiges Gerät* fest.
        
    2.  **Buildtyp** ist auf **D3D** festgelegt
    3.  **SDK** ist auf **Latest installed (Neueste Installation)** festgelegt.
    4.  **Visual Studio Version** ist auf **Neueste installiert** festgelegt.
    5.  **Build und Ausführung** ist auf **Lokaler Computer** festgelegt.
    6.  Speichern Sie die Szene, und fügen Sie sie dem Build hinzu. 

        1. Wählen Sie hierzu **Öffnende Szenen hinzufügen aus.** Ein Speicherfenster wird angezeigt.

            ![Hinzufügen einer offenen Szene zur Buildliste](images/AzureLabs-Lab302b-21.png)

        2. Erstellen Sie einen neuen Ordner für diese und jede zukünftige Szene, und wählen Sie dann die Schaltfläche **Neuer Ordner** aus, um einen neuen Ordner zu erstellen, und nennen Sie ihn **Szenen**.

            ![Erstellen eines neuen Szenenordners](images/AzureLabs-Lab302b-22.png)

        3. Öffnen Sie den neu erstellten Ordner **Scenes,** und geben Sie dann im Textfeld *Dateiname:* **CustomVisionScene** ein, und klicken Sie dann auf **Speichern.**

            ![Benennen einer neuen Szenendatei](images/AzureLabs-Lab302b-23.png)

            > Beachten Sie, dass Sie Ihre Unity-Szenen im Ordner *Assets* speichern müssen, da sie dem Unity-Projekt zugeordnet sein müssen. Das Erstellen des Ordners scenes (und anderer ähnlicher Ordner) ist eine typische Methode zum Strukturieren eines Unity-Projekts.
            
    7.  Die übrigen Einstellungen in *Build Einstellungen* sollten vorerst als Standard verwendet werden.

        ![Standardbuildeinstellungen](images/AzureLabs-Lab302b-24.png)

6.  Klicken *Sie* im Fenster Build Einstellungen auf die Schaltfläche **Player Einstellungen.** Dadurch wird der zugehörige Bereich in dem Bereich geöffnet, in dem sich der *Inspektor* befindet.

7. In diesem Bereich müssen einige Einstellungen überprüft werden:

    1.  Auf der Registerkarte **Andere Einstellungen:**

        1.  **Die Skriptruntimeversion** sollte **experimentell (.NET 4.6-Entsprechung)** sein, wodurch der Editor neu gestartet werden muss.

        2. **Skript-Back-End** sollte **.NET** sein

        3. **Der API-Kompatibilitätsgrad** sollte **.NET 4.6** sein.

        ![Api-Kompantiblität festlegen](images/AzureLabs-Lab302b-25.png)

    2.  Aktivieren **Sie** auf der Registerkarte Veröffentlichen Einstellungen unter **Funktionen** Folgendes:

        1. **InternetClient**

        2.  **Webcam**

        3. **Mikrofon**

        ![Konfigurieren von Veröffentlichungseinstellungen](images/AzureLabs-Lab302b-26.png)

    3.  Aktivieren Sie weiter unten im Bereich in **XR Einstellungen** (finden Sie unter **Veröffentlichen Einstellungen**), aktivieren Sie Virtual Reality **Supported (Virtual Reality Unterstützt),** und stellen Sie sicher, dass das **Windows Mixed Reality SDK** hinzugefügt wurde.

    ![Konfigurieren von XR-Einstellungen](images/AzureLabs-Lab302b-27.png)

8.  Zurück in *Build Einstellungen* Unity *C \# Projects* ist nicht mehr abgeblendet. Aktivieren Sie das Kontrollkästchen daneben.

9.  Schließen Sie das Fenster „Build Settings“ (Buildeinstellungen).

10.  Speichern Sie Ihre Szene und Ihr Projekt (**DATEI > SZENE SPEICHERN/DATEI > PROJEKT SPEICHERN**).


## <a name="chapter-4---importing-the-newtonsoft-dll-in-unity"></a>Kapitel 4: Importieren der Newtonsoft-DLL in Unity

> [!IMPORTANT]
> Wenn Sie die *Unity Set up-Komponente* dieses Kurses überspringen und direkt mit dem Code fortfahren möchten, können Sie dieses [Azure-MR-302b.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage)herunterladen, es als [**benutzerdefiniertes Paket**](https://docs.unity3d.com/Manual/AssetPackages.html)in Ihr Projekt importieren und dann mit Kapitel [6](#chapter-6---create-the-customvisionanalyser-class)fortfahren.

Dieser Kurs erfordert die Verwendung der **Newtonsoft-Bibliothek,** die Sie Ihren Assets als DLL hinzufügen können. Das Paket, das diese Bibliothek enthält, [kann von diesem Link heruntergeladen werden.](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage)
Um die Newtonsoft-Bibliothek in Ihr Projekt zu importieren, verwenden Sie das Unity-Paket, das in diesem Kurs enthalten ist.

1.  Fügen Sie *unitypackage* mithilfe der Menüoption *Assets Import Package Custom Package  >   >  *(Benutzerdefiniertes* *Paket* *importieren)** zu Unity hinzu.

2.  Stellen Sie im daraufhin angezeigten Feld **Unity-Paket importieren** sicher, dass alles unter **Plug-Ins** (einschließlich) ausgewählt ist.

    ![Importieren aller Paketelemente](images/AzureLabs-Lab302b-28.png)

3.  Klicken Sie auf die Schaltfläche **Importieren,** um die Elemente ihrem Projekt hinzuzufügen.

4.  Wechseln Sie in der Projektansicht unter **Plug-Ins** zum Ordner **Newtonsoft,** und wählen Sie die *Newtonsoft.Jsauf Plug-In* aus.

    ![Wählen Sie Newtonsoft-Plug-In aus.](images/AzureLabs-Lab302b-29.png)

5.  Stellen Sie bei ausgewähltem *Newtonsoft.Json-Plug-In* sicher, dass **Alle Plattformen** **deaktiviert** ist. Stellen Sie dann sicher, dass **WSAPlayer** ebenfalls **deaktiviert** ist, und klicken Sie dann auf **Übernehmen.** Dies dient lediglich zur Bestätigung, dass die Dateien ordnungsgemäß konfiguriert sind.

    ![Konfigurieren des Newtonsoft-Plug-Ins](images/AzureLabs-Lab302b-30.png)

    > [!NOTE]
    > Durch Das Markieren dieser Plug-Ins werden sie so konfiguriert, dass sie nur im Unity-Editor verwendet werden. Im WSA-Ordner gibt es einen anderen Satz von ihnen, der verwendet wird, nachdem das Projekt aus Unity exportiert wurde.

6.  Als Nächstes müssen Sie den **Ordner WSA** im Ordner **Newtonsoft** öffnen. Es wird eine Kopie der gleichen Datei angezeigt, die Sie soeben konfiguriert haben. Wählen Sie die Datei aus, und stellen Sie dann im Inspektor sicher, dass
    -   **Alle Plattformen** sind **deaktiviert.** 
    -   **nur** **WSAPlayer** **ist aktiviert**
    -   **Der Nichtprozess** ist **aktiviert.**

    ![Konfigurieren von Einstellungen für die Newtonsoft-Plug-In-Plattform](images/AzureLabs-Lab302b-31.png)

## <a name="chapter-5---camera-setup"></a>Kapitel 5: Kameraeinrichtung

1.  Wählen Sie im Hierarchiebereich die *Hauptkamera* aus.

2.  Nach der Auswahl von werden alle Komponenten der *Hauptkamera* im *Inspektorbereich angezeigt.*

    1.  Das *Kameraobjekt* muss **hauptkamera** genannt werden (beachten Sie die Schreibweise!)

    2.  Das **Hauptkameratag** muss auf **MainCamera** festgelegt werden (beachten Sie die Schreibweise!)

    3.  Stellen Sie sicher, dass **die Transformationsposition** auf **0, 0, 0** festgelegt ist.

    4.  Legen Sie **Clear Flags** auf **Volltonfarbe** fest (ignorieren Sie dies für immersive Headsets).

    5.  Legen Sie die **Hintergrundfarbe** der Kamerakomponente auf **Schwarz, Alpha 0 (Hexadezimalcode: #00000000)** fest (ignorieren Sie dies für immersive Headsets).

    ![Konfigurieren von Kamerakomponenteneigenschaften](images/AzureLabs-Lab302b-32.png)


## <a name="chapter-6---create-the-customvisionanalyser-class"></a>Kapitel 6: Erstellen der CustomVisionAnalyser-Klasse.

An diesem Punkt können Sie Code schreiben.

Sie beginnen mit der *CustomVisionAnalyser-Klasse.*

> [!NOTE]
> Die Aufrufe des **Custom Vision-Diensts,** die im unten gezeigten Code erfolgen, werden mithilfe der **Custom Vision REST-API** ausgeführt. Dadurch erfahren Sie, wie Sie diese API implementieren und nutzen (nützlich für das Verständnis, wie Sie etwas Ähnliches selbst implementieren können). Beachten Sie, dass Microsoft ein **Custom Vision Service SDK** anbietet, das auch für Aufrufe des Diensts verwendet werden kann. Weitere Informationen finden Sie im Artikel [Custom Vision Service SDK.](https://github.com/Microsoft/Cognitive-CustomVision-Windows/)

Diese Klasse ist für Dies ist verantwortlich für:

-   Laden des neuesten Images, das als Bytearray erfasst wurde.

-   Senden des Bytearrays an Ihre Azure *Custom Vision Service-Instanz* zur Analyse.

-   Empfangen der Antwort als JSON-Zeichenfolge.

-   Deserialisieren der Antwort und Übergeben der resultierenden *Vorhersage* an die *SceneOrganiser-Klasse,* die die Anzeige der Antwort übernimmt.

So erstellen Sie diese Klasse:

1.  Klicken Sie mit der rechten Maustaste auf den *Medienobjektordner* im *Project Bereich,* und klicken Sie dann auf **> Ordner erstellen.** Rufen Sie den Ordner **Skripts auf.**

    ![Ordner "Skripts erstellen"](images/AzureLabs-Lab302b-33.png)

2.  Doppelklicken Sie auf den soeben erstellten Ordner, um ihn zu öffnen.

3.  Klicken Sie mit der rechten Maustaste in den Ordner, und klicken **Sie** dann auf  >  **\# C-Skript** erstellen. Nennen Sie das Skript *CustomVisionAnalyser*.

4.  Doppelklicken Sie auf das neue *CustomVisionAnalyser-Skript,* um es mit **Visual Studio** zu öffnen.

5.  Aktualisieren Sie die Namespaces am Anfang der Datei so, dass sie den folgenden Entsprechen entsprechen:

    ```csharp
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    using Newtonsoft.Json;
    ```

6.  Fügen Sie in der *CustomVisionAnalyser-Klasse* die folgenden Variablen hinzu:

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your Prediction Key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > Stellen Sie sicher, dass Sie Ihren **Vorhersageschlüssel** in die Variable **predictionKey** und den **Vorhersageendpunkt** in die Variable **predictionEndpoint** einfügen. Sie haben diese in *Editor* weiter oben im Kurs kopiert.

7.  Code für **Awake()** muss jetzt hinzugefügt werden, um die Instanzvariable zu initialisieren:

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  Löschen Sie die Methoden **Start()** und **Update().**

9.  Fügen Sie als Nächstes die Coroutine hinzu (mit der statischen **GetImageAsByteArray()-Methode** darunter), die die Ergebnisse der Analyse des von der *ImageCapture-Klasse* erfassten Bilds erhält.

    > [!NOTE]
    > In der **AnalyseImageCapture-Coroutine** gibt es einen Aufruf der *SceneOrganiser-Klasse,* die Sie noch erstellen müssen. Lassen **Sie daher diese Zeilen vorerst auskommentiert.**

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(predictionEndpoint, webForm))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);

                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader("Prediction-Key", predictionKey);

                // The upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                // The download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return unityWebRequest.SendWebRequest();

                string jsonResponse = unityWebRequest.downloadHandler.text;

                // The response will be in JSON format, therefore it needs to be deserialized    
    
                // The following lines refers to a class that you will build in later Chapters
                // Wait until then to uncomment these lines

                //AnalysisObject analysisObject = new AnalysisObject();
                //analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
                //SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
            }
        }

        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);

            BinaryReader binaryReader = new BinaryReader(fileStream);

            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

10.  Speichern Sie Ihre Änderungen in **Visual Studio,** bevor Sie zu **Unity** zurückkehren.

## <a name="chapter-7---create-the-customvisionobjects-class"></a>Kapitel 7: Erstellen der CustomVisionObjects-Klasse

Die Klasse, die Sie jetzt erstellen, ist die *CustomVisionObjects-Klasse.*

Dieses Skript enthält eine Reihe von -Objekten, die von anderen Klassen zum Serialisieren und Deserialisieren der Aufrufe an den *Custom Vision-Dienst* verwendet werden.

> [!WARNING]
> Beachten Sie unbedingt den Endpunkt, den der Custom Vision-Dienst bereitstellt, da die folgende JSON-Struktur für die Arbeit mit [*Custom Vision Prediction v2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290)eingerichtet wurde. Wenn Sie über eine andere Version verfügen, müssen Sie möglicherweise die folgende Struktur aktualisieren.

So erstellen Sie diese Klasse:

1.  Klicken Sie mit der rechten Maustaste in den Ordner **Skripts,** und klicken Sie dann auf   >  **\# C-Skript** erstellen. Rufen Sie das Skript *CustomVisionObjects auf.*

2.  Doppelklicken Sie auf das neue **CustomVisionObjects-Skript,** um es mit **Visual Studio** zu öffnen.

3.  Fügen Sie am Anfang der Datei die folgenden Namespaces hinzu:

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  Löschen Sie die **Methoden Start()** und **Update()** innerhalb der *CustomVisionObjects-Klasse.* Diese Klasse sollte jetzt leer sein.

5.  Fügen Sie die folgenden Klassen **außerhalb** der *CustomVisionObjects-Klasse* hinzu. Diese Objekte werden von der *Newtonsoft-Bibliothek* verwendet, um die Antwortdaten zu serialisieren und zu deserialisieren:

    ```csharp
    // The objects contained in this script represent the deserialized version
    // of the objects used by this application 

    /// <summary>
    /// Web request object for image data
    /// </summary>
    class MultipartObject : IMultipartFormSection
    {
        public string sectionName { get; set; }

        public byte[] sectionData { get; set; }

        public string fileName { get; set; }

        public string contentType { get; set; }
    }

    /// <summary>
    /// JSON of all Tags existing within the project
    /// contains the list of Tags
    /// </summary> 
    public class Tags_RootObject
    {
        public List<TagOfProject> Tags { get; set; }
        public int TotalTaggedImages { get; set; }
        public int TotalUntaggedImages { get; set; }
    }

    public class TagOfProject
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public string Description { get; set; }
        public int ImageCount { get; set; }
    }

    /// <summary>
    /// JSON of Tag to associate to an image
    /// Contains a list of hosting the tags,
    /// since multiple tags can be associated with one image
    /// </summary> 
    public class Tag_RootObject
    {
        public List<Tag> Tags { get; set; }
    }

    public class Tag
    {
        public string ImageId { get; set; }
        public string TagId { get; set; }
    }

    /// <summary>
    /// JSON of Images submitted
    /// Contains objects that host detailed information about one or more images
    /// </summary> 
    public class ImageRootObject
    {
        public bool IsBatchSuccessful { get; set; }
        public List<SubmittedImage> Images { get; set; }
    }

    public class SubmittedImage
    {
        public string SourceUrl { get; set; }
        public string Status { get; set; }
        public ImageObject Image { get; set; }
    }

    public class ImageObject
    {
        public string Id { get; set; }
        public DateTime Created { get; set; }
        public int Width { get; set; }
        public int Height { get; set; }
        public string ImageUri { get; set; }
        public string ThumbnailUri { get; set; }
    }

    /// <summary>
    /// JSON of Service Iteration
    /// </summary> 
    public class Iteration
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public bool IsDefault { get; set; }
        public string Status { get; set; }
        public string Created { get; set; }
        public string LastModified { get; set; }
        public string TrainedAt { get; set; }
        public string ProjectId { get; set; }
        public bool Exportable { get; set; }
        public string DomainId { get; set; }
    }

    /// <summary>
    /// Predictions received by the Service after submitting an image for analysis
    /// </summary> 
    [Serializable]
    public class AnalysisObject
    {
        public List<Prediction> Predictions { get; set; }
    }

    [Serializable]
    public class Prediction
    {
        public string TagName { get; set; }
        public double Probability { get; set; }
    }
    ```

## <a name="chapter-8---create-the-voicerecognizer-class"></a>Kapitel 8: Erstellen der VoiceRecognizer-Klasse

Diese Klasse erkennt die Spracheingabe des Benutzers.

So erstellen Sie diese Klasse:

1.  Klicken Sie mit der rechten Maustaste in den Ordner **Skripts,** und klicken Sie dann auf   >  **\# C-Skript** erstellen. Rufen Sie das Skript *VoiceRecognizer auf.*

2.  Doppelklicken Sie auf das neue **VoiceRecognizer-Skript,** um es mit **Visual Studio** zu öffnen.

3.  Fügen Sie die folgenden Namespaces über der *VoiceRecognizer-Klasse* hinzu:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.Windows.Speech;
    ```

4.  Fügen Sie dann die folgenden Variablen in der *VoiceRecognizer-Klasse* oberhalb der *Start()-Methode* hinzu:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static VoiceRecognizer Instance;

        /// <summary>
        /// Recognizer class for voice recognition
        /// </summary>
        internal KeywordRecognizer keywordRecognizer;

        /// <summary>
        /// List of Keywords registered
        /// </summary>
        private Dictionary<string, Action> _keywords = new Dictionary<string, Action>();
    ```

5.  Fügen Sie die **Methoden "Awake()"** und **"Start()"** hinzu. Letztere richten die *Benutzerschlüsselwörter* ein, die beim Zuordnen eines Tags zu einem Bild erkannt werden:

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start ()
        {

            Array tagsArray = Enum.GetValues(typeof(CustomVisionTrainer.Tags));

            foreach (object tagWord in tagsArray)
            {
                _keywords.Add(tagWord.ToString(), () =>
                {
                    // When a word is recognized, the following line will be called
                    CustomVisionTrainer.Instance.VerifyTag(tagWord.ToString());
                });
            }

            _keywords.Add("Discard", () =>
            {
                // When a word is recognized, the following line will be called
                // The user does not want to submit the image
                // therefore ignore and discard the process
                ImageCapture.Instance.ResetImageCapture();
                keywordRecognizer.Stop();
            });

            //Create the keyword recognizer 
            keywordRecognizer = new KeywordRecognizer(_keywords.Keys.ToArray());

            // Register for the OnPhraseRecognized event 
            keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        }
    ```

6.  Löschen Sie die **Update()-Methode.**

7.  Fügen Sie den folgenden Handler hinzu, der immer dann aufgerufen wird, wenn die Spracheingabe erkannt wird:

    ```csharp    
        /// <summary>
        /// Handler called when a word is recognized
        /// </summary>
        private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
        {
            Action keywordAction;
            // if the keyword recognized is in our dictionary, call that Action.
            if (_keywords.TryGetValue(args.text, out keywordAction))
            {
                keywordAction.Invoke();
            }
        }
    ```

8.  Speichern Sie Ihre Änderungen in **Visual Studio,** bevor Sie zu **Unity** zurückkehren.

> [!NOTE]
> Machen Sie sich keine Gedanken über Code, der möglicherweise einen Fehler aufweist, da Sie in Kürze weitere Klassen bereitstellen werden, die diese beheben.

## <a name="chapter-9---create-the-customvisiontrainer-class"></a>Kapitel 9: Erstellen der CustomVisionVertrieb-Klasse

Diese Klasse verkettet eine Reihe von Webaufrufen, um den *Custom Vision Service* zu trainieren. Jeder Aufruf wird direkt über dem Code ausführlich erläutert.

So erstellen Sie diese Klasse:

1.  Klicken Sie mit der rechten Maustaste in den Ordner **Skripts,** und klicken Sie dann auf   >  **\# C-Skript** erstellen. Rufen Sie das Skript *CustomVisionVertrieb* auf.

2.  Doppelklicken Sie auf das neue *CustomVisionWeb-Skript,* um es mit **Visual Studio** zu öffnen.

3.  Fügen Sie die folgenden Namespaces über der *CustomVisionMulti-Klasse* hinzu:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Collections.Generic;
    using System.IO;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  Fügen Sie dann über der **Start()-Methode** die folgenden Variablen in der *CustomVisionVertrieb-Klasse* hinzu. 

    > [!NOTE]
    > Die hier verwendete Trainings-URL wird in der *Custom Vision Training 1.2-Dokumentation* bereitgestellt und weist folgende Struktur auf: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/  
    > Weitere Informationen finden Sie in der [*Referenz-API für Custom Vision Training v1.2.*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f)

    > [!WARNING]
    > Beachten Sie unbedingt den Endpunkt, den der Custom Vision-Dienst für den Trainingsmodus bereitstellt, da die verwendete JSON-Struktur (innerhalb der **CustomVisionObjects-Klasse)** für [*Custom Vision Training v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f)eingerichtet wurde. Wenn Sie über eine andere Version verfügen, müssen Sie möglicherweise die *Objects-Struktur* aktualisieren.

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CustomVisionTrainer Instance;

        /// <summary>
        /// Custom Vision Service URL root
        /// </summary>
        private string url = "https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/";

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string trainingKey = "- Insert your key here -";

        /// <summary>
        /// Insert your Project Id here
        /// </summary>
        private string projectId = "- Insert your Project Id here -";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// The Tags accepted
        /// </summary>
        internal enum Tags {Mouse, Keyboard}

        /// <summary>
        /// The UI displaying the training Chapters
        /// </summary>
        private TextMesh trainingUI_TextMesh;
    ```

    > [!IMPORTANT]
    > Stellen Sie sicher, dass Sie Ihren **Dienstschlüsselwert (Trainingsschlüssel)** und **Project ID-Wert** hinzufügen, den Sie sich zuvor notiert haben. Dies sind die Werte, die Sie [zuvor im Kurs (Kapitel 2, Schritt 10 oder früher) im Portal gesammelt haben.](#chapter-2---training-your-custom-vision-project)

5.  Fügen Sie die folgenden **Start()-** und **Awake()-Methoden** hinzu. Diese Methoden werden bei der Initialisierung aufgerufen und enthalten den Aufruf zum Einrichten der Benutzeroberfläche:

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        private void Start()
        { 
            trainingUI_TextMesh = SceneOrganiser.Instance.CreateTrainingUI("TrainingUI", 0.04f, 0, 4, false);
        }
    ```

6.  Löschen Sie die **Update()-Methode.** Diese Klasse benötigt sie nicht.

7.  Fügen Sie die **RequestTagSelection()-Methode** hinzu. Diese Methode ist die erste Methode, die aufgerufen wird, wenn ein Bild erfasst und auf dem Gerät gespeichert wurde. Sie kann nun an den *Custom Vision Service* übermittelt werden, um es zu trainieren. Diese Methode zeigt auf der Trainingsoberfläche einen Satz von Schlüsselwörtern an, mit denen der Benutzer das erfasste Bild markieren kann. Außerdem wird die *VoiceRecognizer-Klasse* benachrichtigt, damit der Benutzer auf Spracheingaben lauscht.

    ```csharp
        internal void RequestTagSelection()
        {
            trainingUI_TextMesh.gameObject.SetActive(true);
            trainingUI_TextMesh.text = $" \nUse voice command \nto choose between the following tags: \nMouse\nKeyboard \nor say Discard";

            VoiceRecognizer.Instance.keywordRecognizer.Start();
        }
    ```

8.  Fügen Sie die **VerifyTag()-Methode** hinzu. Diese Methode empfängt die spracheingabe, die von der **VoiceRecognizer-Klasse** erkannt wird, überprüft ihre Gültigkeit und beginnt dann mit dem Trainingsprozess.

    ```csharp
        /// <summary>
        /// Verify voice input against stored tags.
        /// If positive, it will begin the Service training process.
        /// </summary>
        internal void VerifyTag(string spokenTag)
        {
            if (spokenTag == Tags.Mouse.ToString() || spokenTag == Tags.Keyboard.ToString())
            {
                trainingUI_TextMesh.text = $"Tag chosen: {spokenTag}";
                VoiceRecognizer.Instance.keywordRecognizer.Stop();
                StartCoroutine(SubmitImageForTraining(ImageCapture.Instance.filePath, spokenTag));
            }
        }
    ```

9.  Fügen Sie die **SubmitImageForTraining()-Methode** hinzu. Mit dieser Methode wird der Custom Vision Service-Trainingsprozess gestartet. Der erste Schritt besteht darin, die **Tag-ID** aus dem Dienst abzurufen, die der überprüften Spracheingabe des Benutzers zugeordnet ist. Die **Tag-ID** wird dann zusammen mit dem Bild hochgeladen.

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to submit the image.
        /// </summary>
        public IEnumerator SubmitImageForTraining(string imagePath, string tag)
        {
            yield return new WaitForSeconds(2);
            trainingUI_TextMesh.text = $"Submitting Image \nwith tag: {tag} \nto Custom Vision Service";
            string imageId = string.Empty;
            string tagId = string.Empty;

            // Retrieving the Tag Id relative to the voice input
            string getTagIdEndpoint = string.Format("{0}{1}/tags", url, projectId);
            using (UnityWebRequest www = UnityWebRequest.Get(getTagIdEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Tags_RootObject tagRootObject = JsonConvert.DeserializeObject<Tags_RootObject>(jsonResponse);

                foreach (TagOfProject tOP in tagRootObject.Tags)
                {
                    if (tOP.Name == tag)
                    {
                        tagId = tOP.Id;
                    }             
                }
            }

            // Creating the image object to send for training
            List<IMultipartFormSection> multipartList = new List<IMultipartFormSection>();
            MultipartObject multipartObject = new MultipartObject();
            multipartObject.contentType = "application/octet-stream";
            multipartObject.fileName = "";
            multipartObject.sectionData = GetImageAsByteArray(imagePath);
            multipartList.Add(multipartObject);

            string createImageFromDataEndpoint = string.Format("{0}{1}/images?tagIds={2}", url, projectId, tagId);

            using (UnityWebRequest www = UnityWebRequest.Post(createImageFromDataEndpoint, multipartList))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);           

                //unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                www.SetRequestHeader("Training-Key", trainingKey);

                // The upload handler will help uploading the byte array with the request
                www.uploadHandler = new UploadHandlerRaw(imageBytes);

                // The download handler will help receiving the analysis from Azure
                www.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                ImageRootObject m = JsonConvert.DeserializeObject<ImageRootObject>(jsonResponse);
                imageId = m.Images[0].Image.Id;
            }
            trainingUI_TextMesh.text = "Image uploaded";
            StartCoroutine(TrainCustomVisionProject());
        }
    ```

10. Fügen Sie die **TrainCustomVisionProject()-Methode** hinzu. Nachdem das Bild übermittelt und markiert wurde, wird diese Methode aufgerufen. Es wird eine neue Iteration erstellt, die mit allen vorherigen Bildern trainiert wird, die an den Dienst übermittelt wurden, sowie mit dem soeben hochgeladenen Bild. Sobald das Training abgeschlossen ist, ruft diese Methode eine Methode auf, um die neu erstellte **Iteration** auf **Default** festzulegen, sodass der Endpunkt, den Sie für die Analyse verwenden, die neueste trainierte Iteration ist.

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to train the Service.
        /// It will generate a new Iteration in the Service
        /// </summary>
        public IEnumerator TrainCustomVisionProject()
        {
            yield return new WaitForSeconds(2);

            trainingUI_TextMesh.text = "Training Custom Vision Service";

            WWWForm webForm = new WWWForm();

            string trainProjectEndpoint = string.Format("{0}{1}/train", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Post(trainProjectEndpoint, webForm))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Training - JSON Response: {jsonResponse}");

                // A new iteration that has just been created and trained
                Iteration iteration = new Iteration();
                iteration = JsonConvert.DeserializeObject<Iteration>(jsonResponse);

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Custom Vision Trained";

                    // Since the Service has a limited number of iterations available,
                    // we need to set the last trained iteration as default
                    // and delete all the iterations you dont need anymore
                    StartCoroutine(SetDefaultIteration(iteration)); 
                }
            }
        }
    ```

11. Fügen Sie die **SetDefaultIteration()-Methode** hinzu. Diese Methode legt die zuvor erstellte und trainierte Iteration auf *Standard* fest. Nach Abschluss dieses Schritts muss diese Methode die vorherige Iteration löschen, die im Dienst vorhanden ist. Zum Zeitpunkt der Erstellung dieses Kurses gibt es eine Beschränkung von maximal zehn (10) Iterationen, die gleichzeitig im Dienst vorhanden sein dürfen.

    ```csharp
        /// <summary>
        /// Set the newly created iteration as Default
        /// </summary>
        private IEnumerator SetDefaultIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);
            trainingUI_TextMesh.text = "Setting default iteration";

            // Set the last trained iteration to default
            iteration.IsDefault = true;

            // Convert the iteration object as JSON
            string iterationAsJson = JsonConvert.SerializeObject(iteration);
            byte[] bytes = Encoding.UTF8.GetBytes(iterationAsJson);

            string setDefaultIterationEndpoint = string.Format("{0}{1}/iterations/{2}", 
                                                            url, projectId, iteration.Id);

            using (UnityWebRequest www = UnityWebRequest.Put(setDefaultIterationEndpoint, bytes))
            {
                www.method = "PATCH";
                www.SetRequestHeader("Training-Key", trainingKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Default iteration is set \nDeleting Unused Iteration";
                    StartCoroutine(DeletePreviousIteration(iteration));
                }
            }
        }
    ```

12. Fügen Sie **die DeletePreviousIteration()-Methode** hinzu. Diese Methode findet und löscht die vorherige nicht standardmäßige Iteration:

    ```csharp
        /// <summary>
        /// Delete the previous non-default iteration.
        /// </summary>
        public IEnumerator DeletePreviousIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);

            trainingUI_TextMesh.text = "Deleting Unused \nIteration";

            string iterationToDeleteId = string.Empty;

            string findAllIterationsEndpoint = string.Format("{0}{1}/iterations", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Get(findAllIterationsEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                // The iteration that has just been trained
                List<Iteration> iterationsList = new List<Iteration>();
                iterationsList = JsonConvert.DeserializeObject<List<Iteration>>(jsonResponse);

                foreach (Iteration i in iterationsList)
                {
                    if (i.IsDefault != true)
                    {
                        Debug.Log($"Cleaning - Deleting iteration: {i.Name}, {i.Id}");
                        iterationToDeleteId = i.Id;
                        break;
                    }
                }
            }

            string deleteEndpoint = string.Format("{0}{1}/iterations/{2}", url, projectId, iterationToDeleteId);

            using (UnityWebRequest www2 = UnityWebRequest.Delete(deleteEndpoint))
            {
                www2.SetRequestHeader("Training-Key", trainingKey);
                www2.downloadHandler = new DownloadHandlerBuffer();
                yield return www2.SendWebRequest();
                string jsonResponse = www2.downloadHandler.text;

                trainingUI_TextMesh.text = "Iteration Deleted";
                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "Ready for next \ncapture";

                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "";
                ImageCapture.Instance.ResetImageCapture();
            }
        }
    ```

13. Die letzte Methode, die in dieser Klasse hinzugefügt werden soll, ist die **GetImageAsByteArray()-Methode,** die für die Webaufrufe verwendet wird, um das erfasste Bild in ein Bytearray zu konvertieren.

    ```csharp
        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

14. Stellen Sie sicher, dass Sie Ihre Änderungen **in** Visual Studio speichern, bevor Sie zu **Unity zurückkehren.**

## <a name="chapter-10---create-the-sceneorganiser-class"></a>Kapitel 10: Erstellen der SceneOrganiser-Klasse

Diese Klasse wird:

-   Erstellen  Sie ein Cursor-Objekt, das an die Hauptkamera angefügt werden soll.

-   Erstellen Sie **ein Label-Objekt,** das angezeigt wird, wenn der Dienst die realen Objekte erkennt.

-   Richten Sie die Hauptkamera ein, indem Sie die entsprechenden Komponenten anfügen.

-   Erstellen **Sie** im Analysemodus die Bezeichnungen zur Laufzeit im entsprechenden Raum relativ zur Position der Hauptkamera, und zeigen Sie die vom Custom Vision Service empfangenen Daten an.

-   Erstellen Sie **im Trainingsmodus** die Benutzeroberfläche, auf der die verschiedenen Phasen des Trainingsprozesses angezeigt werden.

So erstellen Sie diese Klasse:

1.  Klicken Sie mit der rechten Maustaste in **den Ordner Skripts,** und klicken Sie dann **auf**  >  **\# C-Skript erstellen.** Nennen Sie das *Skript SceneOrganiser*.

2.  Doppelklicken Sie auf das neue *SceneOrganiser-Skript,* um es mit **Visual Studio.**

3.  Sie benötigen nur einen Namespace. Entfernen Sie die anderen über der *SceneOrganiser-Klasse:*

    ```csharp
    using UnityEngine;
    ```

4.  Fügen Sie dann die folgenden Variablen in der *SceneOrganiser-Klasse* über der **Start()-Methode** hinzu:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        internal GameObject label;

        /// <summary>
        /// Object providing the current status of the camera.
        /// </summary>
        internal TextMesh cameraStatusIndicator;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.5f;
    ```

5.  Löschen Sie **die Methoden Start()** **und Update().**

6.  Fügen Sie direkt unterhalb der Variablen die **Methode "Awake()"** hinzu, mit der die Klasse initialisiert und die Szene eingerichtet wird.

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this GameObject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this GameObject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionTrainer class to this GameObject
            gameObject.AddComponent<CustomVisionTrainer>();

            // Add the VoiceRecogniser class to this GameObject
            gameObject.AddComponent<VoiceRecognizer>();

            // Add the CustomVisionObjects class to this GameObject
            gameObject.AddComponent<CustomVisionObjects>();

            // Create the camera Cursor
            cursor = CreateCameraCursor();

            // Load the label prefab as reference
            label = CreateLabel();

            // Create the camera status indicator label, and place it above where predictions
            // and training UI will appear.
            cameraStatusIndicator = CreateTrainingUI("Status Indicator", 0.02f, 0.2f, 3, true);

            // Set camera status indicator to loading.
            SetCameraStatus("Loading");
        }
    ```

7.  Fügen Sie nun die **CreateCameraCursor()-Methode** hinzu, die den Hauptkameracursor erstellt und positioniert, und die **CreateLabel()-Methode,** die das **Analysis Label-Objekt** erstellt.

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private GameObject CreateCameraCursor()
        {
            // Create a sphere as new cursor
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Attach it to the camera
            newCursor.transform.parent = gameObject.transform;

            // Resize the new cursor
            newCursor.transform.localScale = new Vector3(0.02f, 0.02f, 0.02f);

            // Move it to the correct position
            newCursor.transform.localPosition = new Vector3(0, 0, 4);

            // Set the cursor color to red
            newCursor.GetComponent<Renderer>().material = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<Renderer>().material.color = Color.green;

            return newCursor;
        }

        /// <summary>
        /// Create the analysis label object
        /// </summary>
        private GameObject CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Resize the new cursor
            newLabel.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);

            // Creating the text of the label
            TextMesh t = newLabel.AddComponent<TextMesh>();
            t.anchor = TextAnchor.MiddleCenter;
            t.alignment = TextAlignment.Center;
            t.fontSize = 50;
            t.text = "";

            return newLabel;
        }
    ```

8. Fügen Sie **die SetCameraStatus()-Methode** hinzu, die Nachrichten verarbeitet, die für das Textgitternetz bestimmt sind und den Status der Kamera bereitstellen.

    ```csharp
        /// <summary>
        /// Set the camera status to a provided string. Will be coloured if it matches a keyword.
        /// </summary>
        /// <param name="statusText">Input string</param>
        public void SetCameraStatus(string statusText)
        {
            if (string.IsNullOrEmpty(statusText) == false)
            {
                string message = "white";

                switch (statusText.ToLower())
                {
                    case "loading":
                        message = "yellow";
                        break;

                    case "ready":
                        message = "green";
                        break;

                    case "uploading image":
                        message = "red";
                        break;

                    case "looping capture":
                        message = "yellow";
                        break;

                    case "analysis":
                        message = "red";
                        break;
                }

                cameraStatusIndicator.GetComponent<TextMesh>().text = $"Camera Status:\n<color={message}>{statusText}..</color>";
            }
        }
    ```

9. Fügen Sie **die Methoden PlaceAnalysisLabel()** und **SetTagsToLastLabel()** hinzu, die die Daten aus dem Custom Vision Service in der Szene erstellen und anzeigen.

    ```csharp
        /// <summary>
        /// Instantiate a label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
        }

        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void SetTagsToLastLabel(AnalysisObject analysisObject)
        {
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

            if (analysisObject.Predictions != null)
            {
                foreach (Prediction p in analysisObject.Predictions)
                {
                    if (p.Probability > 0.02)
                    {
                        lastLabelPlacedText.text += $"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}";
                        Debug.Log($"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}");
                    }
                }
            }
        }
    ```

10. Fügen Sie abschließend die **CreateTrainingUI()-Methode** hinzu, die die Benutzeroberfläche mit den mehreren Phasen des Trainingsprozesses zeigt, wenn sich die Anwendung im Trainingsmodus befindet. Diese Methode wird auch zum Erstellen des Kamerastatusobjekts genutzt.

    ```csharp
        /// <summary>
        /// Create a 3D Text Mesh in scene, with various parameters.
        /// </summary>
        /// <param name="name">name of object</param>
        /// <param name="scale">scale of object (i.e. 0.04f)</param>
        /// <param name="yPos">height above the cursor (i.e. 0.3f</param>
        /// <param name="zPos">distance from the camera</param>
        /// <param name="setActive">whether the text mesh should be visible when it has been created</param>
        /// <returns>Returns a 3D text mesh within the scene</returns>
        internal TextMesh CreateTrainingUI(string name, float scale, float yPos, float zPos, bool setActive)
        {
            GameObject display = new GameObject(name, typeof(TextMesh));
            display.transform.parent = Camera.main.transform;
            display.transform.localPosition = new Vector3(0, yPos, zPos);
            display.SetActive(setActive);
            display.transform.localScale = new Vector3(scale, scale, scale);
            display.transform.rotation = new Quaternion();
            TextMesh textMesh = display.GetComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            return textMesh;
        }
    ```

11. Stellen Sie sicher, dass Sie Ihre Änderungen **in** Visual Studio speichern, bevor Sie zu **Unity zurückkehren.**

> [!IMPORTANT]
> Bevor Sie fortfahren, öffnen Sie die **CustomVisionAnalyser-Klasse,** und entrücken Sie in der **AnalyseLastImageCaptured()-Methode** die Auskommentierung *der* folgenden Zeilen:
>
> ```csharp
>   AnalysisObject analysisObject = new AnalysisObject();
>   analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
>   SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
> ```

## <a name="chapter-11---create-the-imagecapture-class"></a>Kapitel 11: Erstellen der ImageCapture-Klasse

Die nächste Klasse, die Sie erstellen, ist die *ImageCapture-Klasse.*

Diese Klasse ist für Folgendes verantwortlich:

-   Erfassen eines Bilds mithilfe HoloLens Kamera und Speichern im *App-Ordner.*

-   Behandeln von Tippgesten des Benutzers.

-   Beibehalten des *Enum-Werts,* der bestimmt, ob die Anwendung im *Analyse- oder* *Trainingsmodus ausgeführt* wird.

So erstellen Sie diese Klasse:

1.  Wechseln Sie zum **Ordner Skripts,** den Sie zuvor erstellt haben.

2.  Klicken Sie mit der rechten Maustaste in den Ordner, und klicken Sie dann **> \# C-Skript .** Nennen Sie das *Skript ImageCapture*.

3.  Doppelklicken Sie auf das neue **ImageCapture-Skript,** um es **mit** Visual Studio.

4.  Ersetzen Sie die Namespaces am Anfang der Datei durch Folgendes:

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  Fügen Sie dann die folgenden Variablen in der *ImageCapture-Klasse* über der **Start()-Methode** hinzu:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture Instance;

        /// <summary>
        /// Keep counts of the taps for image renaming
        /// </summary>
        private int captureCount = 0;

        /// <summary>
        /// Photo Capture object
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// Allows gestures recognition in HoloLens
        /// </summary>
        private GestureRecognizer recognizer;

        /// <summary>
        /// Loop timer
        /// </summary>
        private float secondsBetweenCaptures = 10f;

        /// <summary>
        /// Application main functionalities switch
        /// </summary>
        internal enum AppModes {Analysis, Training }
        
        /// <summary>
        /// Local variable for current AppMode
        /// </summary>
        internal AppModes AppMode { get; private set; }

        /// <summary>
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  Code für **die Methoden "Awake()"** und **"Start()"** muss nun hinzugefügt werden:

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;

            // Change this flag to switch between Analysis Mode and Training Mode 
            AppMode = AppModes.Training;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Clean up the LocalState folder of this application from all photos stored
            DirectoryInfo info = new DirectoryInfo(Application.persistentDataPath);
            var fileInfo = info.GetFiles();
            foreach (var file in fileInfo)
            {
                try
                {
                    file.Delete();
                }
                catch (Exception)
                {
                    Debug.LogFormat("Cannot delete file: ", file.Name);
                }
            } 

            // Subscribing to the HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();

            SceneOrganiser.Instance.SetCameraStatus("Ready");
        }
    ```

7.  Implementieren Sie einen Handler, der aufgerufen wird, wenn eine Tippbewegung auftritt.

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            switch (AppMode)
            {
                case AppModes.Analysis:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;
                        
                        // Update camera status to looping capture.
                        SceneOrganiser.Instance.SetCameraStatus("Looping Capture");

                        // Begin the capture loop
                        InvokeRepeating("ExecuteImageCaptureAndAnalysis", 0, secondsBetweenCaptures);
                    }
                    else
                    {
                        // The user tapped while the app was analyzing 
                        // therefore stop the analysis process
                        ResetImageCapture();
                    }
                    break;

                case AppModes.Training:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Call the image capture
                        ExecuteImageCaptureAndAnalysis();

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                        // Update camera status to uploading image.
                        SceneOrganiser.Instance.SetCameraStatus("Uploading Image");
                    }              
                    break;
            }     
        }
    ```

    > [!NOTE] 
    > Im *Analysemodus* fungiert die **TapHandler-Methode** als Schalter zum Starten oder Beenden der Fotoaufnahmeschleife.
    >
    > Im *Trainingsmodus* wird ein Bild von der Kamera erfasst.
    >
    > Wenn der Cursor grün ist, bedeutet dies, dass die Kamera für die Aufnahme des Bilds verfügbar ist.
    >
    > Wenn der Cursor rot ist, bedeutet dies, dass die Kamera ausgelastet ist.

8.  Fügen Sie die Methode hinzu, die die Anwendung verwendet, um den Bilderfassungsprozess zu starten und das Bild zu speichern.

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Update camera status to analysis.
            SceneOrganiser.Instance.SetCameraStatus("Analysis");

            // Create a label in world space using the SceneOrganiser class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 0.0f,
                    cameraResolutionWidth = targetTexture.width,
                    cameraResolutionHeight = targetTexture.height,
                    pixelFormat = CapturePixelFormat.BGRA32
                };

                // Capture the image from the camera and save it in the App internal folder
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", captureCount);
                    filePath = Path.Combine(Application.persistentDataPath, filename);          
                    captureCount++;              
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);              
                });
            });   
        }
    ```

9.  Fügen Sie die Handler hinzu, die aufgerufen werden, wenn das Foto erfasst wurde und wann es für die Analyse bereit ist. Das Ergebnis wird dann je nach Modus, in dem der Code festgelegt ist, an *CustomVisionAnalyser* oder *CustomVisionVisionVision* übergeben.

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }


        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            switch (AppMode)
            {
                case AppModes.Analysis:
                    // Call the image analysis
                    StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath));
                    break;

                case AppModes.Training:
                    // Call training using captured image
                    CustomVisionTrainer.Instance.RequestTagSelection();
                    break;
            }
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Update camera status to ready.
            SceneOrganiser.Instance.SetCameraStatus("Ready");

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. Stellen Sie sicher, dass Sie Ihre Änderungen **in** Visual Studio speichern, bevor Sie zu **Unity zurückkehren.**

11. Nachdem alle Skripts abgeschlossen wurden, wechseln Sie zurück in den Unity-Editor, klicken Sie dann auf die **SceneOrganiser-Klasse,** und ziehen Sie sie aus dem Ordner **Skripts** auf das **Objekt Hauptkamera** im *Hierarchiebereich*.

## <a name="chapter-12---before-building"></a>Kapitel 12 – Vor dem Erstellen

Um ihre Anwendung gründlich zu testen, müssen Sie sie auf die HoloLens.

Bevor Sie dies tun, stellen Sie Sicher, dass:

- Alle in Kapitel [2 erwähnten Einstellungen](#chapter-2---training-your-custom-vision-project) sind ordnungsgemäß festgelegt.

- Alle Felder in der **Hauptkamera** und im Inspektorbereich sind ordnungsgemäß zugewiesen.

- Das Skript **SceneOrganiser** ist an das **Hauptkameraobjekt** angefügt.

- Stellen Sie sicher, dass Sie Ihren **Vorhersageschlüssel** in die **Variable predictionKey** einfügen.

- Sie haben Ihren **Vorhersageendpunkt in** die Variable **predictionEndpoint** eingefügt.

- Sie haben Ihren **Trainingsschlüssel** in die **Variable trainingKey** der *CustomVisionKey-Klasse* eingefügt.

- Sie haben Ihre **Project-ID** in die **Variable projectId** der *CustomVisionTraining-Klasse* eingefügt.

## <a name="chapter-13---build-and-sideload-your-application"></a>Kapitel 13: Erstellen und Sideloaden Ihrer Anwendung

So starten Sie *den Buildprozess:*

1.  Wechseln Sie **zu Datei > Build Einstellungen**.

2.  Ticken **Sie Unity C \# Projects**.

3.  Klicken Sie auf **Erstellen**. Unity startet ein **Datei-Explorer-Fenster,** in dem Sie einen Ordner erstellen und dann einen Ordner auswählen müssen, in dem die App erstellt werden soll. Erstellen Sie diesen Ordner jetzt, und nennen Sie ihn **App**. Klicken Sie dann bei ausgewähltem **App-Ordner** auf **Ordner auswählen.**

4.  Unity beginnt damit, Ihr Projekt im Ordner **App zu** erstellen.

5.  Sobald Unity die Erstellung abgeschlossen hat (dies kann einige Zeit dauern), wird ein **Datei-Explorer-Fenster** am Speicherort Ihres Buildfensters geöffnet (überprüfen Sie Ihre Taskleiste, da sie möglicherweise nicht immer über Ihren Fenstern angezeigt wird, sondern Sie über das Addition eines neuen Fensters benachrichtigt).

So stellen Sie auf HoloLens:

1.  Sie benötigen die IP-Adresse Ihres HoloLens (für Remote Deploy) und um sicherzustellen, dass sich HoloLens im **Entwicklermodus befindet.** Aufgabe:

    1.  Öffnen Sie die HoloLens, während Sie **Einstellungen.**

    2.  Wechseln Sie **zu "& Internet**  >  **Wi-Fi Advanced** Options" (Erweiterte Optionen für Netzwerk- und &  >  **Wlan).**

    3.  Notieren Sie sich **die IPv4-Adresse.**

    4.  Navigieren Sie als Nächstes zurück **zu Einstellungen**, und navigieren Sie dann zu Update **& Security** For  >  **Developers (Sicherheit** für Entwickler aktualisieren).

    5.  Legen Sie **den Entwicklermodus auf fest.**

2.  Navigieren Sie zu Ihrem neuen Unity-Build (dem **Ordner App),** und öffnen Sie die Projektmappendatei mit **Visual Studio.**

3.  Wählen Sie in *der Projektmappenkonfiguration* **Debuggen aus.**

4.  Wählen Sie *auf der Projektmappenplattform* **x86, Remotecomputer aus.** Sie werden aufgefordert, die **IP-Adresse** eines Remotegeräts (in diesem HoloLens, das Sie notiert haben) einfügungen.

    ![Festlegen der IP-Adresse](images/AzureLabs-Lab302b-34.png)

5. Wechseln Sie zum **Menü Erstellen,** und klicken Sie **auf Projektmappe bereitstellen,** um die Anwendung per Sideload in Ihre HoloLens.

6. Ihre App sollte jetzt in der Liste der installierten Apps auf Ihrer HoloLens angezeigt werden, die zum Start bereit sind!

> [!NOTE]
> Legen Sie zum Bereitstellen für immersive Headsets die  **Projektmappenplattform** auf Lokaler Computer und die Konfiguration auf *Debuggen* mit *x86* als Plattform **fest.** Stellen Sie dann auf dem lokalen Computer mithilfe des **Menüelements Erstellen** die Option *Projektmappe bereitstellen aus.* 

## <a name="to-use-the-application"></a>So verwenden Sie die Anwendung:

Um die App-Funktionalität  zwischen  Trainingsmodus und Vorhersagemodus zu ändern, müssen Sie die **AppMode-Variable** aktualisieren, die sich in der **Methode "Awake()"** befindet, die sich in der *ImageCapture-Klasse* befindet.

```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Training;
```
oder
```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Analysis;
```

Im *Trainingsmodus:*

- Sehen Sie sich **Maus oder** **Tastatur an,** und verwenden Sie die **Tippgeste**.

- Als Nächstes wird Text angezeigt, in dem Sie aufgefordert werden, ein -Tag zu geben.

- Geben Sie entweder **Maus oder** **Tastatur an.**


Im *Vorhersagemodus:*

- Sehen Sie sich ein Objekt an, und verwenden Sie die **Tippgeste**.

- Text wird angezeigt, wenn das erkannte Objekt mit der höchsten Wahrscheinlichkeit (dies wird normalisiert) angegeben wird.

## <a name="chapter-14---evaluate-and-improve-your-custom-vision-model"></a>Kapitel 14: Auswerten und Verbessern Ihres Custom Vision Modells

Um Ihren Dienst genauer zu machen, müssen Sie das für die Vorhersage verwendete Modell weiter trainieren. Dies wird erreicht, indem Sie  Ihre  neue Anwendung sowohl mit dem Trainings- als auch mit dem Vorhersagemodus verwenden. Letzteres erfordert, dass Sie das Portal besuchen. Dies wird in diesem Kapitel behandelt. Bereiten Sie sich darauf vor, Ihr Portal mehrmals erneut zu besuchen, um Ihr Modell kontinuierlich zu verbessern.

1. Gehen Sie erneut zu Ihrem Azure Custom Vision-Portal, und wählen  Sie die Registerkarte Vorhersagen (in der oberen Mitte der Seite) aus, sobald Sie sich in Ihrem Projekt befinden:

    ![Registerkarte "Vorhersagen auswählen"](images/AzureLabs-Lab302b-35.png)

2. Sie sehen alle Images, die an Ihren Dienst gesendet wurden, während Ihre Anwendung ausgeführt wurde. Wenn Sie auf die Bilder zeigen, erhalten Sie die Vorhersagen, die für dieses Bild getroffen wurden:

    ![Liste der Vorhersagebilder](images/AzureLabs-Lab302b-36.png)

3. Wählen Sie eines Ihrer Bilder aus, um es zu öffnen. Nach dem Öffnen werden die vorhersagen, die für dieses Bild auf der rechten Seite getroffen wurden. Wenn Die Vorhersagen richtig waren und Sie dieses Bild dem Trainingsmodell Ihres Diensts hinzufügen möchten, klicken Sie auf das Eingabefeld Meine *Tags,* und wählen Sie das Tag aus, das Sie zuordnen möchten. Wenn Sie fertig sind, klicken Sie *unten* rechts auf die Schaltfläche Speichern und schließen, und fahren Sie mit dem nächsten Bild fort.

    ![Bild auswählen, das geöffnet werden soll](images/AzureLabs-Lab302b-37.png)

4. Sobald Sie zum Raster der Bilder zurückkommen, werden Sie feststellen, dass die Bilder, denen Sie Tags hinzugefügt (und gespeichert) haben, entfernt werden. Wenn Sie Bilder finden, von denen Sie glauben, dass ihr markiertes Element nicht enthalten ist, können Sie sie löschen, indem Sie auf das Häkchen dieses Bilds klicken (kann dies für mehrere Bilder tun) und dann *in* der oberen rechten Ecke der Rasterseite auf Löschen klicken. Im folgenden Popupfenster können Sie entweder auf  *Ja,* löschen oder Nein klicken, um den Löschvorgang zu bestätigen oder abzubricht. 

    ![Löschen von Images](images/AzureLabs-Lab302b-38.png)

5. Wenn Sie bereit sind, fortzufahren, klicken Sie oben rechts auf die grüne Schaltfläche Trainieren.  Ihr Dienstmodell wird mit allen Images trainiert, die Sie jetzt bereitgestellt haben (wodurch es genauer wird). Klicken Sie nach Abschluss des Trainings erneut auf die Schaltfläche Make *default* (Standard festlegen), damit Ihre Vorhersage-URL weiterhin die aktuelle Iteration Ihres Diensts verwendet. 

    ![Dienstmodell starten Wählen ](images/AzureLabs-Lab302b-39.png) ![ Sie die Option "Standard festlegen" aus.](images/AzureLabs-Lab302b-40.png)

## <a name="your-finished-custom-vision-api-application"></a>Ihre fertige Custom Vision-API-Anwendung

Herzlichen Glückwunsch! Sie haben eine Mixed Reality-App erstellt, die die Azure Custom Vision-API nutzt, um reale Objekte zu erkennen, das Dienstmodell zu trainieren und vertrauen zu können, was gesehen wurde.

![Fertiges Projektbeispiel](images/AzureLabs-Lab302b-00.png)

## <a name="bonus-exercises"></a>Zusatzübungen

### <a name="exercise-1"></a>Übung 1

Trainieren Sie **Ihren Custom Vision Service,** um weitere Objekte zu erkennen.

### <a name="exercise-2"></a>Übung 2

Führen Sie die folgenden Übungen aus, um das Gelernte zu erweitern:

Gibt einen Sound wieder, wenn ein Objekt erkannt wird.

### <a name="exercise-3"></a>Übung 3

Verwenden Sie die API, um Ihren Dienst mit den gleichen Bildern neu zu trainieren, die Ihre App analysiert, um den Dienst genauer zu machen (Vorhersage und Training gleichzeitig ausführen).