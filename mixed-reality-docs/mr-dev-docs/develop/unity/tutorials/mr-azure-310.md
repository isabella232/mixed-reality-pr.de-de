---
title: 'HoloLens (1. Generation) und Azure 310: Objekterkennung'
description: In diesem Kurs erfahren Sie, wie Sie ein Machine Learning-Modell trainieren und verwenden, um ähnliche Objekte und ihre Position in der realen Welt zu erkennen.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Custom Vision, Objekterkennung, Mixed Reality, Academy, Unity, Tutorial, API, HoloLens, Windows 10, Visual Studio
ms.openlocfilehash: b152aaebbd3858140b79133a8f8e551aab06b4f3
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2021
ms.locfileid: "121905739"
---
# <a name="hololens-1st-gen-and-azure-310-object-detection"></a>HoloLens (1. Generation) und Azure 310: Objekterkennung

>[!NOTE]
>Die Tutorials der Mixed Reality Academy wurden im Hinblick auf HoloLens (1. Gen.) und immersive Mixed Reality-Headsets entworfen.  Daher halten wir es für wichtig, diese Tutorials für Entwickler verfügbar zu halten, die noch nach Anleitung beim Entwickeln für diese Geräte suchen.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für HoloLens 2 verwendet werden.  Sie werden gewartet, um weiterhin auf den unterstützten Geräten zu funktionieren. Es wird eine neue Reihe von Tutorials geben, die in Zukunft veröffentlicht werden, die veranschaulichen, wie Sie für die Entwicklung HoloLens 2.  Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn sie veröffentlicht werden.

<br>

In diesem Kurs erfahren Sie, wie Sie benutzerdefinierte visuelle Inhalte und deren räumliche Position innerhalb eines bereitgestellten Bilds erkennen, indem Sie azure Custom Vision Funktionen zur Objekterkennung in einer Mixed Reality-Anwendung verwenden.

Mit diesem Dienst können Sie ein Machine Learning-Modell mithilfe von Objektbildern trainieren. Anschließend verwenden Sie das trainierte Modell, um ähnliche Objekte zu erkennen und deren Position in der realen Welt zu ungefähren, wie durch die Kameraaufnahme von Microsoft HoloLens bereitgestellt, oder eine Kamera stellt eine Verbindung mit einem PC für immersive Headsets (VR) dar.

![Kursergebnis](images/AzureLabs-Lab310-00.png)

**Azure Custom Vision ist die Objekterkennung** ein Microsoft-Dienst, mit dem Entwickler benutzerdefinierte Bildklassifizierungen erstellen können. Diese Klassifizierer können dann mit neuen Bildern verwendet werden, um Objekte innerhalb dieses neuen Bilds zu erkennen, indem **Box-Grenzen** innerhalb des Bilds selbst zur Verfügung stellt. Der Dienst bietet ein einfaches, einfach zu verwendende Onlineportal, um diesen Prozess zu optimieren. Weitere Informationen finden Sie unter den folgenden Links:

* [Seite "Azure Custom Vision"](/azure/cognitive-services/custom-vision-service/home)
* [Grenzwerte und Kontingente](/azure/cognitive-services/custom-vision-service/limits-and-quotas)

Nach Abschluss dieses Kurses verfügen Sie über eine Mixed Reality-Anwendung, die Folgendes tun kann:

1. Der Benutzer kann auf ein Objekt *blicken,* das er mit dem Azure Custom Vision Service, Objekterkennung trainiert hat.
2. Der Benutzer verwendet die Geste *Tippen,* um ein Bild davon zu erfassen, was er betrachtet.
3. Die App sendet das Image an den Azure Custom Vision Service.
4. Es wird eine Antwort vom Dienst angezeigt, in der das Ergebnis der Erkennung als Text im Raum angezeigt wird. Dies wird erreicht, indem die räumliche Nachverfolgung von Microsoft HoloLens verwendet wird, um die Weltposition des erkannten Objekts zu verstehen, und dann das *Tag* zu verwenden, das dem im Bild erkannten Tag zugeordnet ist, um den Bezeichnungstext zur Verfügung zu stellen.

In diesem Kurs wird auch das manuelle Hochladen von Bildern, das Erstellen von Tags und das Trainieren des Diensts zum Erkennen verschiedener Objekte (im bereitgestellten Beispiel ein Becher) durch Festlegen der *Boundary Box* innerhalb des von Ihnen übermittelten Bilds durchgeführt.

> [!IMPORTANT]
> Nach der Erstellung und Verwendung der App sollte der Entwickler zurück zum Azure Custom Vision-Dienst navigieren, die vom Dienst getroffenen Vorhersagen identifizieren und ermitteln, ob sie korrekt waren (durch Markieren von etwas, was der Dienst übersehen hat, und Anpassen der Begrenzungsfelder). Der Dienst kann dann erneut trainiert werden, was die Wahrscheinlichkeit erhöht, dass er reale Objekte erkennt.

In diesem Kurs erfahren Sie, wie Sie die Ergebnisse des Azure Custom Vision-Diensts Objekterkennung in einer Unity-basierten Beispielanwendung erhalten. Sie müssen diese Konzepte auf eine benutzerdefinierte Anwendung anwenden, die Sie möglicherweise erstellen.

## <a name="device-support"></a>Geräteunterstützung

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td> MR und Azure 310: Objekterkennung</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>Voraussetzungen

> [!NOTE]
> Dieses Tutorial ist für Entwickler konzipiert, die über grundlegende Erfahrung mit Unity und C# verfügen. Beachten Sie auch, dass die Voraussetzungen und die geschriebenen Anweisungen in diesem Dokument darstellen, was zum Zeitpunkt der Erstellung (Juli 2018) getestet und überprüft wurde. Sie können die neueste Software verwenden, [](../../install-the-tools.md) wie im Artikel Installieren der Tools aufgeführt. Es sollte jedoch nicht davon ausgegangen werden, dass die Informationen in diesem Kurs perfekt mit dem übereinstimmen, was Sie in neuerer Software finden, als unten aufgeführt.

Für diesen Kurs wird die folgende Hardware und Software empfohlen:

- Ein Entwicklungs-PC
- [Windows 10 Fall Creators Update (oder höher) mit aktivierter Entwicklermodus](../../install-the-tools.md#installation-checklist-for-hololens)
- [Das neueste Windows 10 SDK](../../install-the-tools.md#installation-checklist-for-hololens)
- [Unity 2017.4 LTS](../../install-the-tools.md#installation-checklist-for-hololens)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist-for-hololens)
- Ein [Microsoft HoloLens](/windows/mixed-reality/hololens-hardware-details) mit aktivierten Entwicklermodus
- Internetzugriff für azure setup and Custom Vision Service retrieval
-  Eine Reihe von mindestens 15 Bildern (15) ist für jedes Objekt erforderlich, das von der Custom Vision werden soll. Wenn Sie möchten, können Sie die Bilder verwenden, die bereits in diesem Kurs bereitgestellt wurden, [eine Reihe von Bechern](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).

## <a name="before-you-start"></a>Vorbereitung

1.  Um Probleme beim Erstellen dieses Projekts zu vermeiden, wird dringend empfohlen, das in diesem Tutorial erwähnte Projekt in einem Stamm- oder Near-Root-Ordner zu erstellen (lange Ordnerpfade können zur Buildzeit Probleme verursachen).
2.  Einrichten und Testen Ihrer HoloLens. Wenn Sie dafür Unterstützung benötigen, besuchen [Sie den Artikel HoloLens Setup.](/hololens/hololens-setup)
3.  Es ist eine gute Idee, die Kalibrierung und Sensoroptimierung durchzuführen, wenn Sie mit der Entwicklung einer neuen HoloLens-App beginnen (manchmal kann es helfen, diese Aufgaben für jeden Benutzer auszuführen).

Hilfe zur Kalibrierung finden Sie unter diesem [Link zum Artikel HoloLens Kalibrierung.](/hololens/hololens-calibration#hololens-2)

Hilfe zur Sensoroptimierung finden Sie unter diesem [Link zum Artikel HoloLens Sensoroptimierung.](/hololens/hololens-updates)

## <a name="chapter-1---the-custom-vision-portal"></a>Kapitel 1: Das Custom Vision Portal

Um den **Azure Custom Vision Service** zu verwenden, müssen Sie eine Instanz des Diensts konfigurieren, die für Ihre Anwendung verfügbar gemacht wird.

1.  Navigieren [Sie zur **Custom Vision-Dienst-Hauptseite.**](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)

2.  Klicken Sie **auf Erste Schritte**.

    ![](images/AzureLabs-Lab310-01.png)

3.  Melden Sie sich beim Custom Vision Portal an.

    ![](images/AzureLabs-Lab310-02.png)

4.  Wenn Sie noch nicht über ein Azure-Konto verfügen, müssen Sie eines erstellen. Wenn Sie dieses Tutorial in einer Classroom- oder Lab-Situation durch verwenden, bitten Sie Ihren Dozenten oder einen der Proktoren um Hilfe beim Einrichten Ihres neuen Kontos.

5.  Sobald Sie zum ersten Mal angemeldet sind, werden Sie zum Bereich Nutzungsbedingungen *aufgefordert.* Aktivieren Sie das Kontrollkästchen, um *den Bedingungen zu zustimmen.* Klicken Sie dann auf **Ich stimme zu.**

    ![](images/AzureLabs-Lab310-03.png)

6.  Nachdem Sie den Bedingungen zugestimmt haben, befinden Sie sich jetzt im *Abschnitt Meine Projekte.* Klicken Sie **auf New Project**.

    ![](images/AzureLabs-Lab310-04.png)

7.  Auf der rechten Seite wird eine Registerkarte angezeigt, auf der Sie aufgefordert werden, einige Felder für das Projekt anzugeben.

    1.  Einfügen eines Namens für Ihr Projekt

    2.  Fügen Sie eine Beschreibung für Ihr Projekt ein (**optional**).

    3.  Wählen Sie eine **Ressourcengruppe aus,** oder erstellen Sie eine neue. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, Steuern des Zugriffs, Bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt zugeordnet sind (z. B. diese Kurse), unter einer gemeinsamen Ressourcengruppe zu halten.

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > Wenn Sie mehr über [Azure-Ressourcengruppen erfahren möchten, navigieren Sie zur zugehörigen Dokumentation.](/azure/azure-resource-manager/resource-group-portal)

    4.  Legen Sie **Project-Typen** auf **Objekterkennung (Vorschau) fest.**

8.  Wenn Sie fertig sind, klicken Sie auf Projekt **erstellen,** und Sie werden zur Seite Custom Vision Service-Projekt umgeleitet.


## <a name="chapter-2---training-your-custom-vision-project"></a>Kapitel 2: Trainieren Ihres Custom Vision Projekts

Sobald Sie sich im Custom Vision-Portal befindet, besteht Ihr Hauptziel darin, Ihr Projekt so zu trainieren, dass es bestimmte Objekte in Bildern erkennt.

Sie benötigen mindestens 15 Bilder für jedes Objekt, das ihre Anwendung erkennen soll. Sie können die in diesem Kurs bereitgestellten Bilder[(eine Reihe von Bechern) verwenden.](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)

So trainieren Sie Custom Vision Projekt:

1.  Klicken Sie auf **+** die Schaltfläche neben **Tags**.

    ![](images/AzureLabs-Lab310-06.png)

2.  Fügen Sie **einen Namen** für das Tag hinzu, das zum Zuordnen Ihrer Bilder verwendet wird. In diesem Beispiel verwenden wir Bilder von Bechern für die Erkennung, daher haben wir das Tag für diesen benannt, **Cup**. Klicken Sie **nach Abschluss auf** Speichern.

    ![](images/AzureLabs-Lab310-07.png)

3.  Sie werden feststellen, **dass Ihr Tag** hinzugefügt wurde (Möglicherweise müssen Sie Ihre Seite neu laden, damit sie angezeigt wird). 

    ![](images/AzureLabs-Lab310-08.png)

4.  Klicken Sie **in der** Mitte der Seite auf Bilder hinzufügen.

    ![](images/AzureLabs-Lab310-09.png)

5.  Klicken Sie **auf Lokale Dateien durchsuchen,** und navigieren Sie zu den Bildern, die Sie für ein Objekt hochladen möchten, mit mindestens 15 Bildern.

    > [!TIP]
    >  Sie können mehrere Bilder gleichzeitig auswählen, um sie hochzuladen.

    ![](images/AzureLabs-Lab310-10.png)

6.  Drücken **Hochladen Dateien,** nachdem Sie alle Bilder ausgewählt haben, mit der Sie das Projekt trainieren möchten. Die Dateien werden hochgeladen. Nachdem Sie den Upload bestätigt haben, klicken Sie auf **Fertig.**

    ![](images/AzureLabs-Lab310-11.png)

7.  An diesem Punkt werden Ihre Bilder hochgeladen, aber nicht markiert.

    ![](images/AzureLabs-Lab310-12.png)

8.  Verwenden Sie die Maus, um Ihre Bilder zu markieren. Wenn Sie mit dem Zeigen auf ihr Bild zeigen, können Sie eine Auswahlherde auswählen, indem Sie automatisch eine Auswahl um Ihr Objekt zeichnen. Wenn sie nicht genau ist, können Sie ihre eigenen zeichnen. Dies wird erreicht, indem mit der linken Maustaste auf die Maus geklickt und der Auswahlbereich gezogen wird, um Ihr Objekt zu umfassen. 

    ![](images/AzureLabs-Lab310-13.png) 

9. Nach der Auswahl Ihres Objekts im Bild werden Sie in einer kleinen Eingabeaufforderung aufgefordert, *Das Regionstag hinzuzufügen.* Wählen Sie ihr zuvor erstelltes Tag ("Cup" im obigen Beispiel) aus. Wenn Sie weitere Tags hinzufügen, geben Sie dieses in ein, und klicken Sie auf die Schaltfläche **+ (Plus).**

    ![](images/AzureLabs-Lab310-14.png) 

10. Um das nächste Bild zu markieren, können Sie auf den Pfeil rechts neben dem Blatt klicken oder das Tagblatt schließen (indem Sie in der oberen rechten Ecke des Blatts auf das **X** klicken) und dann auf das nächste Bild klicken. Nachdem Sie das nächste Image fertig haben, wiederholen Sie das gleiche Verfahren. Gehen Sie für alle hochgeladenen Bilder so lange vor, bis sie alle mit Tags versehen sind. 

    > [!NOTE]
    >  Sie können mehrere Objekte im gleichen Bild auswählen, wie in der folgenden Abbildung: 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. Nachdem Sie sie alle markiert haben, klicken Sie auf die **markierte** Schaltfläche auf der linken Seite des Bildschirms, um die markierten Bilder anzuzeigen. 

    ![](images/AzureLabs-Lab310-16.png)

12. Nun können Sie Ihren Dienst trainieren. Klicken Sie auf die Schaltfläche **Trainieren,** und die erste Trainingsiteration beginnt.

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. Sobald sie erstellt wurde, werden zwei Schaltflächen mit dem Namen **Make default** und **Prediction URL angezeigt.** Klicken Sie zuerst auf **Standardwert festlegen** und dann auf **Vorhersage-URL.**

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > Der Endpunkt, der von diesem bereitgestellt wird, wird auf die *Iteration* festgelegt, die als Standard markiert wurde. Wenn Sie also später eine neue *Iteration* erstellen und diese als Standard aktualisieren, müssen Sie ihren Code nicht ändern.

14. Nachdem Sie auf **Vorhersage-URL** geklickt haben, öffnen Sie *Editor*, kopieren Sie die **URL** (auch als **Vorhersageendpunkt** bezeichnet) und den **Dienstvorhersageschlüssel,** damit Sie sie später im Code abrufen können, wenn Sie sie benötigen.

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a>Kapitel 3: Einrichten des Unity-Projekts

Im Folgenden finden Sie eine typische Einrichtung für die Entwicklung mit Mixed Reality und ist daher eine gute Vorlage für andere Projekte.

1.  Öffnen Sie **Unity,** und klicken Sie auf **Neu.**

    ![](images/AzureLabs-Lab310-21.png)

2.  Sie müssen nun einen Unity-Projektnamen angeben. Fügen Sie **CustomVisionObjDetection ein.** Stellen Sie sicher, dass der Projekttyp auf **3D** festgelegt ist, und legen Sie den **Speicherort** an einem für Sie geeigneten Ort fest (denken Sie daran, dass näher an den Stammverzeichnissen besser ist). Klicken Sie dann auf **Projekt erstellen.**

    ![](images/AzureLabs-Lab310-22.png)

3.  Wenn Unity geöffnet ist, sollten Sie überprüfen, ob der **Standardskript-Editor** auf **Visual Studio** festgelegt ist. Navigieren Sie zu * >  *Einstellungen* *bearbeiten,** und navigieren Sie dann im neuen Fenster zu **Externe Tools**. Ändern Sie **den externen Skript-Editor** in **Visual Studio**. Schließen Sie das Fenster **Einstellungen.**

    ![](images/AzureLabs-Lab310-23.png)

4.  Wechseln Sie als Nächstes zu **Datei > Build Einstellungen,** wechseln Sie von **Plattform** zu *Universelle Windows Plattform,* und klicken Sie dann auf die Schaltfläche **Plattform wechseln.**

    ![](images/AzureLabs-Lab310-24.png)

5.  Stellen Sie im gleichen Fenster **Build Einstellungen** sicher, dass Folgendes festgelegt ist:

    1.  **Zielgerät** ist auf **HoloLens**        
    2.  **Buildtyp** ist auf **D3D** festgelegt
    3.  **SDK** ist auf **Latest installed (Neueste Installation)** festgelegt.
    4.  **Visual Studio Version** ist auf **Latest installed (Neueste installiert)** festgelegt.
    5.  **Build und Ausführung** ist auf **Lokaler Computer** festgelegt.            
    6.  Die übrigen Einstellungen in **Build Einstellungen** sollten vorerst als Standard festgelegt werden.

        ![](images/AzureLabs-Lab310-25.png)

6.  Klicken Sie im gleichen Fenster **Build Einstellungen** auf die Schaltfläche **Player Einstellungen.** Dadurch wird der zugehörige Bereich in dem Bereich geöffnet, in dem sich der **Inspektor** befindet.

7. In diesem Bereich müssen einige Einstellungen überprüft werden:

    1.  Auf der Registerkarte **Andere Einstellungen:**

        1.  **Die Skriptruntimeversion** sollte **experimentell** sein (.NET 4.6-Entsprechung), wodurch der Editor neu gestartet werden muss.

        2. **Das Skript-Back-End** sollte **.NET** sein.

        3. **Der API-Kompatibilitätsgrad** sollte **.NET 4.6** sein.

            ![](images/AzureLabs-Lab310-26.png)

    2.  Aktivieren **Sie** auf der Registerkarte Veröffentlichen Einstellungen unter **Funktionen** Folgendes:

        1. **InternetClient**

        2.  **Webcam**

        3. **SpatialPerception**

            ![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)

    3.  Aktivieren Sie weiter unten im Bereich in **XR Einstellungen** (finden Sie unter **Veröffentlichen Einstellungen**), aktivieren Sie Virtual Reality **Supported (Virtual Reality Unterstützt),** und stellen Sie sicher, dass das **Windows Mixed Reality SDK** hinzugefügt wird.

        ![](images/AzureLabs-Lab310-29.png)

8.  Zurück in **Build Einstellungen** ist Unity *C \# Projects* nicht mehr abgeblendet: Aktivieren Sie das Kontrollkästchen daneben.

9.  Schließen Sie das Fenster **Buildeinstellungen**.

10. Klicken Sie im **Editor** auf   >  **Project Einstellungen**  >  **Grafiken** bearbeiten.

    ![](images/AzureLabs-Lab310-30.png)

11. Im **Inspektorbereich** wird die *grafik Einstellungen* geöffnet. Scrollen Sie nach unten, bis ein Array mit dem Namen **Always Include-Shader angezeigt** wird. Fügen Sie einen Slot hinzu, indem Sie die **Variable Größe** um eins erhöhen (in diesem Beispiel war es 8, also haben wir sie 9 erstellt). Ein neuer Slot wird an der letzten Position des Arrays angezeigt, wie unten dargestellt:

    ![](images/AzureLabs-Lab310-31.png)

12. Klicken Sie im Slot auf den kleinen Zielkreis neben dem Slot, um eine Liste mit Shadern zu öffnen. Suchen Sie nach **legacy shaders/transparent/diffuse** shader, und doppelklicken Sie darauf. 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a>Kapitel 4: Importieren des Unity-Pakets CustomVisionObjDetection

Für diesen Kurs erhalten Sie ein Unity-Ressourcenpaket mit dem Namen **Azure-MR-310.unitypackage.** 

> [TIPP] Alle von Unity unterstützten Objekte, einschließlich vollständiger Szenen, können in eine **UNITYPACKAGE-Datei** gepackt und in andere Projekte exportiert/importiert werden. Es ist die sicherste und effizienteste Möglichkeit, Ressourcen zwischen verschiedenen **Unity-Projekten** zu verschieben.

Sie finden das [Azure-MR-310-Paket, das Sie hier herunterladen müssen.](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage)

1.  Klicken Sie mit dem Unity-Dashboard oben auf dem Bildschirm im Menü auf **Assets** und dann auf Import Package > Custom Package ( **Paket importieren > Benutzerdefiniertes Paket).**

    ![](images/AzureLabs-Lab310-33.png)

2.  Verwenden Sie die Dateiauswahl, um das Paket **Azure-MR-310.unitypackage** auszuwählen, und klicken Sie auf **Öffnen.** Ihnen wird eine Liste der Komponenten für dieses Medienobjekt angezeigt. Bestätigen Sie den Import, indem Sie auf die Schaltfläche **Importieren** klicken.

    ![](images/AzureLabs-Lab310-34.png)

3.  Sobald der Import abgeschlossen ist, werden Sie feststellen, dass Ordner aus dem Paket nun ihrem Ordner **Assets** hinzugefügt wurden. Diese Art von Ordnerstruktur ist typisch für ein Unity-Projekt.

    ![](images/AzureLabs-Lab310-35.png)

    1.  Der Ordner **Materials** enthält das Material, das vom **Gaze Cursor** verwendet wird. 

    2.  Der Ordner **Plugins** enthält die Newtonsoft-DLL, die vom Code zum Deserialisieren der Service-Webantwort verwendet wird. Die beiden (2) verschiedenen Versionen, die im Ordner und im Unterordner enthalten sind, sind erforderlich, damit die Bibliothek sowohl vom Unity-Editor als auch vom UWP-Build verwendet und erstellt werden kann. 

    3.  Der Ordner **Prefabs** enthält die in der Szene enthaltenen Prefabs. Dazu zählen:

        1.  **GazeCursor**, der in der Anwendung verwendete Cursor. Arbeitet mit dem SpatialMapping-Prefab zusammen, um in der Szene auf physischen Objekten platziert zu werden.
        2.  Die **Bezeichnung**, bei der es sich um das Benutzeroberflächenobjekt handelt, das bei Bedarf zum Anzeigen des Objekttags in der Szene verwendet wird.
        3.  **SpatialMapping** ist das Objekt, das es der Anwendung ermöglicht, mithilfe der räumlichen Nachverfolgung des Microsoft HoloLens eine virtuelle Karte zu erstellen.

    4.  Der Ordner **Scenes,** der derzeit die vorgefertigte Szene für diesen Kurs enthält.

4.  Öffnen Sie den Ordner **Scenes** im **Project Panel**, und doppelklicken Sie auf **ObjDetectionScene**, um die Szene zu laden, die Sie für diesen Kurs verwenden werden.

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  **Es ist kein Code enthalten.** Sie schreiben den Code anhand dieses Kurses.

## <a name="chapter-5---create-the-customvisionanalyser-class"></a>Kapitel 5: Erstellen der CustomVisionAnalyser-Klasse.

An diesem Punkt können Sie Code schreiben. Sie beginnen mit der **CustomVisionAnalyser-Klasse.**

> [!NOTE]
> Die Aufrufe des **Custom Vision-Diensts,** die im unten gezeigten Code erfolgen, werden mithilfe der **Custom Vision REST-API** ausgeführt. Dadurch erfahren Sie, wie Sie diese API implementieren und nutzen (nützlich für das Verständnis, wie Sie etwas Ähnliches selbst implementieren können). Beachten Sie, dass Microsoft ein **Custom Vision SDK** anbietet, das auch zum Aufrufen des Diensts verwendet werden kann. Weitere Informationen finden Sie im [artikel Custom Vision SDK.](https://github.com/Microsoft/Cognitive-CustomVision-Windows/)

Diese Klasse ist für Dies ist verantwortlich für:

- Laden des neuesten Images, das als Bytearray erfasst wurde.

- Senden des Bytearrays an Ihre Azure **Custom Vision Service-Instanz** zur Analyse.

- Empfangen der Antwort als JSON-Zeichenfolge.

- Deserialisieren der Antwort und Übergeben der resultierenden **Vorhersage** an die **SceneOrganiser-Klasse,** die die Anzeige der Antwort übernimmt.

So erstellen Sie diese Klasse:

1.  Klicken Sie mit der rechten Maustaste in den **Medienobjektordner**, der sich im **Project Bereich** befindet, und klicken Sie dann auf Ordner   >  erstellen. Rufen Sie den Ordner **Skripts auf.**

    ![](images/AzureLabs-Lab310-37.png)

2.  Doppelklicken Sie auf den neu erstellten Ordner, um ihn zu öffnen.

3.  Klicken Sie mit der rechten Maustaste in den Ordner, und klicken **Sie** dann auf  >  **\# C-Skript** erstellen. Nennen Sie das Skript **CustomVisionAnalyser.**

4.  Doppelklicken Sie auf das neue **CustomVisionAnalyser-Skript,** um es mit Visual Studio zu **öffnen.**

5.  Stellen Sie sicher, dass am Anfang der Datei auf die folgenden Namespaces verwiesen wird:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  Fügen Sie in der **CustomVisionAnalyser-Klasse** die folgenden Variablen hinzu:

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Bite array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > Stellen Sie sicher, dass Sie Ihren **Dienstvorhersageschlüssel** in die Variable **predictionKey** und Ihren **Prediction-Endpoint** in die Variable **predictionEndpoint** einfügen. Sie haben diese [in Editor weiter oben in Kapitel 2, Schritt 14,](#chapter-2---training-your-custom-vision-project)kopiert.

7.  Code für **Awake()** muss jetzt hinzugefügt werden, um die Instanzvariable zu initialisieren:

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  Fügen Sie die Coroutine (mit der statischen **GetImageAsByteArray()-Methode darunter)** hinzu, die die Ergebnisse der Analyse des Bilds erhält, die von der **ImageCapture-Klasse** erfasst werden.

    > [!NOTE]
    > In der **AnalyseImageCapture-Coroutine** gibt es einen Aufruf der **SceneOrganiser-Klasse,** die Sie noch erstellen müssen. Lassen **Sie daher diese Zeilen vorerst auskommentiert.**

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            Debug.Log("Analyzing...");

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

                Debug.Log("response: " + jsonResponse);

                // Create a texture. Texture size does not matter, since
                // LoadImage will replace with the incoming image size.
                //Texture2D tex = new Texture2D(1, 1);
                //tex.LoadImage(imageBytes);
                //SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);

                // The response will be in JSON format, therefore it needs to be deserialized
                //AnalysisRootObject analysisRootObject = new AnalysisRootObject();
                //analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);

                //SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
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

9. Löschen Sie die **Methoden Start()** und **Update(),** da sie nicht verwendet werden. 

10.  Speichern Sie Ihre Änderungen in **Visual Studio**, bevor Sie zu **Unity** zurückkehren.

> [!IMPORTANT]
> Wie bereits erwähnt, machen Sie sich keine Gedanken über Code, der möglicherweise einen Fehler aufweist, da Sie in Kürze weitere Klassen bereitstellen werden, die diese beheben.

## <a name="chapter-6---create-the-customvisionobjects-class"></a>Kapitel 6: Erstellen der CustomVisionObjects-Klasse

Die Klasse, die Sie jetzt erstellen, ist die **CustomVisionObjects-Klasse.**

Dieses Skript enthält eine Reihe von Objekten, die von anderen Klassen zum Serialisieren und Deserialisieren der Aufrufe an den Custom Vision-Dienst verwendet werden.

So erstellen Sie diese Klasse:

1.  Klicken Sie mit der rechten Maustaste in den Ordner **Skripts,** und klicken Sie dann auf   >  **\# C-Skript** erstellen. Rufen Sie das Skript **CustomVisionObjects auf.**

2.  Doppelklicken Sie auf das neue **CustomVisionObjects-Skript,** um es mit Visual Studio zu **öffnen.**

3.  Stellen Sie sicher, dass am Anfang der Datei auf die folgenden Namespaces verwiesen wird:

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  Löschen Sie die **Methoden Start()** und **Update()** innerhalb der **CustomVisionObjects-Klasse.** Diese Klasse sollte jetzt leer sein.

    > [!WARNING]
    > Es ist wichtig, dass Sie die nächste Anweisung sorgfältig befolgen. Wenn Sie die neuen Klassendeklarationen in die **CustomVisionObjects-Klasse** setzen, erhalten Sie Kompilierungsfehler in [Kapitel 10,](#chapter-10---create-the-imagecapture-class)die angeben, dass **AnalysisRootObject** und **BoundingBox** nicht gefunden werden.

5.  Fügen Sie die folgenden Klassen *außerhalb* der **CustomVisionObjects-Klasse** hinzu. Diese Objekte werden von der **Newtonsoft-Bibliothek** verwendet, um die Antwortdaten zu serialisieren und zu deserialisieren:

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
    /// JSON of images submitted
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
    /// Predictions received by the Service
    /// after submitting an image for analysis
    /// Includes Bounding Box
    /// </summary>
    public class AnalysisRootObject
    {
        public string id { get; set; }
        public string project { get; set; }
        public string iteration { get; set; }
        public DateTime created { get; set; }
        public List<Prediction> predictions { get; set; }
    }

    public class BoundingBox
    {
        public double left { get; set; }
        public double top { get; set; }
        public double width { get; set; }
        public double height { get; set; }
    }

    public class Prediction
    {
        public double probability { get; set; }
        public string tagId { get; set; }
        public string tagName { get; set; }
        public BoundingBox boundingBox { get; set; }
    }
    ```

6.  Speichern Sie Ihre Änderungen in **Visual Studio**, bevor Sie zu **Unity** zurückkehren.

## <a name="chapter-7---create-the-spatialmapping-class"></a>Kapitel 7: Erstellen der SpatialMapping-Klasse

Diese Klasse legt den **Spatial Mapping Collider** in der Szene fest, um Konflikte zwischen virtuellen Objekten und realen Objekten erkennen zu können.

So erstellen Sie diese Klasse:

1.  Klicken Sie mit der rechten Maustaste in den Ordner **Skripts,** und klicken Sie dann auf   >  **\# C-Skript** erstellen. Rufen Sie das Skript **SpatialMapping auf.**

2.  Doppelklicken Sie auf das neue **SpatialMapping-Skript,** um es mit Visual Studio zu **öffnen.**

3.  Stellen Sie sicher, dass Sie über die folgenden Namespaces verfügen, auf die oberhalb der **SpatialMapping-Klasse** verwiesen wird:

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  Fügen Sie dann die folgenden Variablen in der **SpatialMapping-Klasse** oberhalb der **Start()-Methode** hinzu:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SpatialMapping Instance;

        /// <summary>
        /// Used by the GazeCursor as a property with the Raycast call
        /// </summary>
        internal static int PhysicsRaycastMask;

        /// <summary>
        /// The layer to use for spatial mapping collisions
        /// </summary>
        internal int physicsLayer = 31;

        /// <summary>
        /// Creates environment colliders to work with physics
        /// </summary>
        private SpatialMappingCollider spatialMappingCollider;
    ```

5.  Fügen Sie **die Daten "Awake()"** und **"Start()"** hinzu:

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Initialize and configure the collider
            spatialMappingCollider = gameObject.GetComponent<SpatialMappingCollider>();
            spatialMappingCollider.surfaceParent = this.gameObject;
            spatialMappingCollider.freezeUpdates = false;
            spatialMappingCollider.layer = physicsLayer;

            // define the mask
            PhysicsRaycastMask = 1 << physicsLayer;

            // set the object as active one
            gameObject.SetActive(true);
        }
    ```

6.  Löschen Sie die **Update()-Methode.**

7.  Speichern Sie Ihre Änderungen in **Visual Studio**, bevor Sie zu **Unity** zurückkehren.


## <a name="chapter-8---create-the-gazecursor-class"></a>Kapitel 8: Erstellen der GazeCursor-Klasse

Diese Klasse ist für das Einrichten des Cursors an der richtigen Position im realen Raum verantwortlich, indem das im vorherigen Kapitel erstellte **SpatialMappingCollider** verwendet wird.

So erstellen Sie diese Klasse:

1.  Klicken Sie mit der rechten Maustaste in den Ordner **Skripts,** und klicken Sie dann auf   >  **\# C-Skript** erstellen. Aufrufen des Skripts **GazeCursor**

2.  Doppelklicken Sie auf das neue **GazeCursor-Skript,** um es mit Visual Studio zu **öffnen.**

3.  Stellen Sie sicher, dass sie über der **GazeCursor-Klasse** auf den folgenden Namespace verweisen:

    ```csharp
    using UnityEngine;
    ```

4.  Fügen Sie dann die folgende Variable in der **GazeCursor-Klasse** oberhalb der **Start()-Methode** hinzu. 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  Aktualisieren Sie die **Start()-Methode** mit dem folgenden Code:

    ```csharp
        /// <summary>
        /// Runs at initialization right after the Awake method
        /// </summary>
        void Start()
        {
            // Grab the mesh renderer that is on the same object as this script.
            meshRenderer = gameObject.GetComponent<MeshRenderer>();

            // Set the cursor reference
            SceneOrganiser.Instance.cursor = gameObject;
            gameObject.GetComponent<Renderer>().material.color = Color.green;

            // If you wish to change the size of the cursor you can do so here
            gameObject.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);
        }
    ```

6.  Aktualisieren Sie die **Update()-Methode** mit dem folgenden Code:

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            // Do a raycast into the world based on the user's head position and orientation.
            Vector3 headPosition = Camera.main.transform.position;
            Vector3 gazeDirection = Camera.main.transform.forward;

            RaycastHit gazeHitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out gazeHitInfo, 30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // If the raycast hit a hologram, display the cursor mesh.
                meshRenderer.enabled = true;
                // Move the cursor to the point where the raycast hit.
                transform.position = gazeHitInfo.point;
                // Rotate the cursor to hug the surface of the hologram.
                transform.rotation = Quaternion.FromToRotation(Vector3.up, gazeHitInfo.normal);
            }
            else
            {
                // If the raycast did not hit a hologram, hide the cursor mesh.
                meshRenderer.enabled = false;
            }
        }
    ```

    > [!NOTE]
    > Machen Sie sich keine Gedanken darüber, dass der Fehler für die **SceneOrganiser-Klasse** nicht gefunden wird. Sie erstellen ihn im nächsten Kapitel.

7. Speichern Sie Ihre Änderungen in **Visual Studio**, bevor Sie zu **Unity** zurückkehren.

## <a name="chapter-9---create-the-sceneorganiser-class"></a>Kapitel 9: Erstellen der SceneOrganiser-Klasse

Diese Klasse führt Dies durch:

-   Richten Sie die *Hauptkamera* ein, indem Sie die entsprechenden Komponenten anfügen.

-   Wenn ein Objekt erkannt wird, ist es dafür verantwortlich, seine Position in der realen Welt zu berechnen und eine **Tagbezeichnung** mit dem entsprechenden **Tagnamen** daneben zu platzieren.    

So erstellen Sie diese Klasse:

1.  Klicken Sie mit der rechten Maustaste in den Ordner **Skripts,** und klicken Sie dann auf   >  **\# C-Skript** erstellen. Nennen Sie das Skript **SceneOrganiser**.

2.  Doppelklicken Sie auf das neue **SceneOrganiser-Skript,** um es mit Visual Studio zu **öffnen.**

3.  Stellen Sie sicher, dass Sie über die folgenden Namespaces verfügen, auf die oberhalb der **SceneOrganiser-Klasse** verwiesen wird:

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  Fügen Sie dann die folgenden Variablen in der **SceneOrganiser-Klasse** oberhalb der **Start()-Methode** hinzu:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the Main Camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        public GameObject label;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.8f;

        /// <summary>
        /// The quad object hosting the imposed image captured
        /// </summary>
        private GameObject quad;

        /// <summary>
        /// Renderer of the quad object
        /// </summary>
        internal Renderer quadRenderer;
    ```

5.  Löschen Sie die **Methoden Start()** und **Update().**

6.  Fügen Sie unterhalb der Variablen die **Awake()-Methode** hinzu, die die -Klasse initialisiert und die Szene eingibt.

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this Gameobject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this Gameobject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionObjects class to this Gameobject
            gameObject.AddComponent<CustomVisionObjects>();
        }
    ```

7.  Fügen Sie die **PlaceAnalysisLabel()-Methode** hinzu, die die Bezeichnung in der Szene *instanziiert* (die an diesem Punkt für den Benutzer unsichtbar ist). Außerdem wird das Quader (auch unsichtbar) an der Stelle platziert, an der das Bild platziert wird, und es überschneidet sich mit der realen Welt. Dies ist wichtig, da die vom Dienst nach der Analyse abgerufenen Boxkoordinaten in diesem Quader zurückverfolgt werden, um die ungefähre Position des Objekts in der realen Welt zu bestimmen. 

    ```csharp
        /// <summary>
        /// Instantiate a Label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
            lastLabelPlacedText.text = "";
            lastLabelPlaced.transform.localScale = new Vector3(0.005f,0.005f,0.005f);

            // Create a GameObject to which the texture can be applied
            quad = GameObject.CreatePrimitive(PrimitiveType.Quad);
            quadRenderer = quad.GetComponent<Renderer>() as Renderer;
            Material m = new Material(Shader.Find("Legacy Shaders/Transparent/Diffuse"));
            quadRenderer.material = m;

            // Here you can set the transparency of the quad. Useful for debugging
            float transparency = 0f;
            quadRenderer.material.color = new Color(1, 1, 1, transparency);

            // Set the position and scale of the quad depending on user position
            quad.transform.parent = transform;
            quad.transform.rotation = transform.rotation;

            // The quad is positioned slightly forward in font of the user
            quad.transform.localPosition = new Vector3(0.0f, 0.0f, 3.0f);

            // The quad scale as been set with the following value following experimentation,  
            // to allow the image on the quad to be as precisely imposed to the real world as possible
            quad.transform.localScale = new Vector3(3f, 1.65f, 1f);
            quad.transform.parent = null;
        }
    ```

8.  Fügen Sie die **Methode "LabelLabel()"** hinzu. IISConfigurator ist für Folgendes zuständig:

    *   Festlegen des *Bezeichnungstexts* mit dem *Tag* der Vorhersage mit der höchsten Zuverlässigkeit.
    *   Aufrufen der Berechnung  des Begrenzungsfelds für das quad-Objekt, das zuvor positioniert wurde, und Platzieren der Bezeichnung in der Szene.
    *   Anpassen der Bezeichnungstiefe mithilfe eines Raycasts in Richtung der *Begrenzungsbox,* die mit dem Objekt in der realen Welt kollidieren sollte.
    * Zurücksetzen des Erfassungsprozesses, damit der Benutzer ein anderes Image erfassen kann.

    ```csharp
        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void FinaliseLabel(AnalysisRootObject analysisObject)
        {
            if (analysisObject.predictions != null)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
                // Sort the predictions to locate the highest one
                List<Prediction> sortedPredictions = new List<Prediction>();
                sortedPredictions = analysisObject.predictions.OrderBy(p => p.probability).ToList();
                Prediction bestPrediction = new Prediction();
                bestPrediction = sortedPredictions[sortedPredictions.Count - 1];

                if (bestPrediction.probability > probabilityThreshold)
                {
                    quadRenderer = quad.GetComponent<Renderer>() as Renderer;
                    Bounds quadBounds = quadRenderer.bounds;

                    // Position the label as close as possible to the Bounding Box of the prediction 
                    // At this point it will not consider depth
                    lastLabelPlaced.transform.parent = quad.transform;
                    lastLabelPlaced.transform.localPosition = CalculateBoundingBoxPosition(quadBounds, bestPrediction.boundingBox);

                    // Set the tag text
                    lastLabelPlacedText.text = bestPrediction.tagName;

                    // Cast a ray from the user's head to the currently placed label, it should hit the object detected by the Service.
                    // At that point it will reposition the label where the ray HL sensor collides with the object,
                    // (using the HL spatial tracking)
                    Debug.Log("Repositioning Label");
                    Vector3 headPosition = Camera.main.transform.position;
                    RaycastHit objHitInfo;
                    Vector3 objDirection = lastLabelPlaced.position;
                    if (Physics.Raycast(headPosition, objDirection, out objHitInfo, 30.0f,   SpatialMapping.PhysicsRaycastMask))
                    {
                        lastLabelPlaced.position = objHitInfo.point;
                    }
                }
            }
            // Reset the color of the cursor
            cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the analysis process
            ImageCapture.Instance.ResetImageCapture();        
        }
    ```

9.  Fügen Sie die **CalculateBoundingBoxPosition()-Methode** hinzu, die eine Reihe von Berechnungen hostet, die erforderlich sind, um die vom Dienst abgerufenen *Begrenzungsfeldkoordinaten* zu übersetzen und proportional auf dem Quader neu zu erstellen.

    ```csharp
        /// <summary>
        /// This method hosts a series of calculations to determine the position 
        /// of the Bounding Box on the quad created in the real world
        /// by using the Bounding Box received back alongside the Best Prediction
        /// </summary>
        public Vector3 CalculateBoundingBoxPosition(Bounds b, BoundingBox boundingBox)
        {
            Debug.Log($"BB: left {boundingBox.left}, top {boundingBox.top}, width {boundingBox.width}, height {boundingBox.height}");

            double centerFromLeft = boundingBox.left + (boundingBox.width / 2);
            double centerFromTop = boundingBox.top + (boundingBox.height / 2);
            Debug.Log($"BB CenterFromLeft {centerFromLeft}, CenterFromTop {centerFromTop}");

            double quadWidth = b.size.normalized.x;
            double quadHeight = b.size.normalized.y;
            Debug.Log($"Quad Width {b.size.normalized.x}, Quad Height {b.size.normalized.y}");

            double normalisedPos_X = (quadWidth * centerFromLeft) - (quadWidth/2);
            double normalisedPos_Y = (quadHeight * centerFromTop) - (quadHeight/2);

            return new Vector3((float)normalisedPos_X, (float)normalisedPos_Y, 0);
        }
    ```

10. Speichern Sie Ihre Änderungen in **Visual Studio**, bevor Sie zu **Unity** zurückkehren.

    > [!IMPORTANT]
    > Öffnen Sie vor dem Fortfahren die **CustomVisionAnalyser-Klasse,** und entpacken Sie in der **AnalyseLastImageCaptured()-Methode** die *Auskommentierung* der folgenden Zeilen:
    >
    >   ```csharp
    >   // Create a texture. Texture size does not matter, since 
    >   // LoadImage will replace with the incoming image size.
    >   Texture2D tex = new Texture2D(1, 1);
    >   tex.LoadImage(imageBytes);
    >   SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);
    >
    >   // The response will be in JSON format, therefore it needs to be deserialized
    >   AnalysisRootObject analysisRootObject = new AnalysisRootObject();
    >   analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);
    >
    >   SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
    >   ```

> [!NOTE]
> Machen Sie sich keine Gedanken über die Meldung "Could not be found" der **ImageCapture-Klasse.** Sie erstellen sie im nächsten Kapitel.


## <a name="chapter-10---create-the-imagecapture-class"></a>Kapitel 10: Erstellen der ImageCapture-Klasse

Die nächste Klasse, die Sie erstellen, ist die **ImageCapture-Klasse.**

Diese Klasse ist für Dies ist verantwortlich für:

*   Erfassen eines Bilds mithilfe der HoloLens Kamera und Speichern im Ordner *App.*
*   Verarbeiten von *Tippgesten* vom Benutzer.

So erstellen Sie diese Klasse:

1.  Wechseln Sie zum Ordner **Skripts,** den Sie zuvor erstellt haben.

2.  Klicken Sie mit der rechten Maustaste in den Ordner, und klicken **Sie** dann auf  >  **\# C-Skript** erstellen. Nennen Sie das Skript **ImageCapture**.

3.  Doppelklicken Sie auf das neue **ImageCapture-Skript,** um es mit Visual Studio zu **öffnen.**

4.  Ersetzen Sie die Namespaces am Anfang der Datei durch Folgendes:

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  Fügen Sie dann die folgenden Variablen in der **ImageCapture-Klasse** oberhalb der **Start()-Methode** hinzu:

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

            // Subscribing to the Microsoft HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  Implementieren Sie einen Handler, der aufgerufen wird, wenn eine Tippbewegung auftritt:

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            if (!captureIsActive)
            {
                captureIsActive = true;

                // Set the cursor color to red
                SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                // Begin the capture loop
                Invoke("ExecuteImageCaptureAndAnalysis", 0);
            }
        }
    ```

    > [!IMPORTANT]
    > Wenn der Cursor **grün** ist, bedeutet dies, dass die Kamera zum Aufnehmen des Bilds verfügbar ist. Wenn der Cursor **rot** ist, bedeutet dies, dass die Kamera ausgelastet ist.

8.  Fügen Sie die Methode hinzu, die die Anwendung verwendet, um den Imageerfassungsprozess zu starten und das Image zu speichern:

    ```csharp
        /// <summary>
        /// Begin process of image capturing and send to Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Create a label in world space using the ResultsLabel class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(true, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 1.0f,
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

9.  Fügen Sie die Handler hinzu, die aufgerufen werden, wenn das Foto erfasst wurde und wann es analysiert werden kann. Das Ergebnis wird dann zur Analyse an **CustomVisionAnalyser** übergeben.

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            try
            {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
            }
            catch (Exception e)
            {
                Debug.LogFormat("Exception capturing photo to disk: {0}", e.Message);
            }
        }

        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the image analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Call the image analysis
            StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath)); 
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. Speichern Sie Ihre Änderungen in **Visual Studio**, bevor Sie zu **Unity** zurückkehren.

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a>Kapitel 11: Einrichten der Skripts in der Szene

Nachdem Sie nun den gesamten für dieses Projekt erforderlichen Code geschrieben haben, ist es an der Zeit, die Skripts in der Szene und auf den Prefabs einzurichten, damit sie sich ordnungsgemäß verhalten.

1.  Wählen Sie im **Unity-Editor** im **Hierarchiebereich** die **Hauptkamera** aus.
2.  Klicken Sie im **Inspektorbereich** mit ausgewählter **Hauptkamera** auf **Add Component (Komponente hinzufügen),** suchen Sie nach **SceneOrganiser script (SceneOrganiser-Skript),** und doppelklicken Sie darauf, um es hinzuzufügen.

    ![](images/AzureLabs-Lab310-38.png)

3.  Öffnen **Sie** im Project Bereich den **Ordner Prefabs**, ziehen Sie das Label-Prefab in den Eingabebereich Label empty reference target (Leeres Referenzziel *bezeichnen)* im **SceneOrganiser-Skript,** das Sie gerade der *Hauptkamera* hinzugefügt haben, wie in der folgenden Abbildung dargestellt: 

    ![](images/AzureLabs-Lab310-39.png)

4.  Wählen Sie im **Hierarchiebereich** das untergeordnete **GazeCursor-Element** der **Hauptkamera** aus.
5.  Klicken Sie im **Inspektorbereich** mit ausgewähltem **GazeCursor** auf **Komponente hinzufügen,** suchen Sie nach **GazeCursor-Skript,** und doppelklicken Sie darauf, um es hinzuzufügen.

    ![](images/AzureLabs-Lab310-40.png)

6.  Wählen Sie erneut im **Hierarchiebereich** das untergeordnete **SpatialMapping-Element** der **Hauptkamera** aus.
7.  Klicken Sie im **Inspektorbereich** mit **ausgewähltem SpatialMapping** auf **Komponente hinzufügen,** suchen Sie nach **SpatialMapping-Skript,** und doppelklicken Sie darauf, um es hinzuzufügen.

    ![](images/AzureLabs-Lab310-41.png)

Die verbleibenden Skripts, die Sie nicht festgelegt haben, werden während der Laufzeit vom Code im **SceneOrganiser-Skript** hinzugefügt.

## <a name="chapter-12---before-building"></a>Kapitel 12 : Vor dem Erstellen

Um einen gründlichen Test Ihrer Anwendung durchzuführen, müssen Sie sie auf Ihre Microsoft HoloLens querladen.

Stellen Sie zuvor Sicher, dass:

-  Alle in Kapitel [3](#chapter-3---set-up-the-unity-project) erwähnten Einstellungen sind ordnungsgemäß festgelegt.
- Das Skript **SceneOrganiser** wird an das **Main Camera-Objekt** angefügt.
- Das Skript **GazeCursor** ist an das **GazeCursor-Objekt** angefügt.
- Das Skript **SpatialMapping** ist an das **SpatialMapping-Objekt** angefügt.
- In [Kapitel 5](#chapter-5---create-the-customvisionanalyser-class), Schritt 6:

    - Stellen Sie sicher, dass Sie Ihren **Dienstvorhersageschlüssel** in die Variable **predictionKey** einfügen.
    - Sie haben Ihren **Vorhersageendpunkt** in die **predictionEndpoint-Klasse** eingefügt.

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a>Kapitel 13: Erstellen der UWP-Lösung und Querladen Ihrer Anwendung

Nun können Sie Ihre Anwendung als UWP-Lösung erstellen, auf der Sie auf dem Microsoft HoloLens bereitstellen können. So starten Sie den Buildprozess:

1.  Wechseln Sie zu **Datei > Build Einstellungen**.

2.  Aktivieren Sie **Unity \# C-Projekte.**

3.  Klicken Sie auf **Offene Szenen hinzufügen.** Dadurch wird dem Build die derzeit geöffnete Szene hinzugefügt.

    ![](images/AzureLabs-Lab310-42.png)

4.  Klicken Sie auf **Erstellen**. Unity startet ein *Datei-Explorer-Fenster,* in dem Sie erstellen und dann einen Ordner auswählen müssen, in dem die App erstellt werden soll. Erstellen Sie diesen Ordner jetzt, und nennen Sie ihn **App**. Klicken Sie dann bei ausgewähltem **App-Ordner** auf **Ordner auswählen.**

5.  Unity beginnt mit dem Erstellen Ihres Projekts im Ordner **App.**

6.  Sobald Unity die Erstellung abgeschlossen hat (es kann einige Zeit dauern), wird am Speicherort des Builds ein **Datei-Explorer-Fenster** geöffnet (überprüfen Sie die Taskleiste, da sie möglicherweise nicht immer über Ihren Fenstern angezeigt wird, Sie aber über das Hinzufügen eines neuen Fensters benachrichtigt werden).

7.  Für die Bereitstellung auf Microsoft HoloLens benötigen Sie die IP-Adresse dieses Geräts (für Remote Deploy) und stellen sicher, dass auch der **Entwicklermodus** festgelegt ist. Dazu ist Folgendes erforderlich:

    1.  Öffnen Sie während der HoloLens die **Einstellungen**.

    2.  Wechseln Sie zu **Network & Internet**  >  **WI-Fi** Advanced  >  **Options (Erweiterte Wlan-Optionen** für Netzwerk & Internet).

    3.  Notieren Sie sich die **IPv4-Adresse.**

    4.  Navigieren Sie als Nächstes zurück zu **Einstellungen** und dann zu Update & Security For Developers **(Sicherheit**  >  **für Entwickler** aktualisieren).

    5.  Legen Sie **den Entwicklermodus** *auf fest.*

8.  Navigieren Sie zu Ihrem neuen Unity-Build (dem Ordner **App),** und öffnen Sie die Projektmappendatei mit **Visual Studio**.

9.  Wählen Sie in der Projektmappenkonfiguration **debuggen** aus.

10. Wählen Sie in der Projektmappenplattform **x86, Remotecomputer aus.** Sie werden aufgefordert, die **IP-Adresse** eines Remotegeräts einzufügen (in diesem Fall die Microsoft HoloLens, die Sie notiert haben).

    ![](images/AzureLabs-Lab310-43.png)

11. Wechseln Sie zum Menü **Erstellen,** und klicken Sie auf **Projektmappe bereitstellen,** um die Anwendung in Ihre HoloLens zu querladen.

12. Ihre App sollte nun in der Liste der installierten Apps auf Ihrem Microsoft HoloLens angezeigt werden, damit sie gestartet werden kann.

### <a name="to-use-the-application"></a>So verwenden Sie die Anwendung:

* Sehen Sie sich ein Objekt an, das Sie mit Ihrem **Azure Custom Vision-Dienst, Objekterkennung** trainiert haben, und verwenden Sie die **Tippgeste**.
* Wenn das Objekt erfolgreich erkannt wird, wird ein *Bezeichnungstext* im Raum mit dem Tagnamen angezeigt.

> [!IMPORTANT]
> Jedes Mal, wenn Sie ein Foto aufnehmen und an den Dienst senden, können Sie zur Seite Dienst zurückkehren und den Dienst mit den neu erfassten Bildern erneut trainieren. Am Anfang müssen Sie wahrscheinlich auch die *Begrenzungsfelder* korrigieren, um genauer zu sein, und den Dienst erneut trainieren.

> [!NOTE]
> Der platzierte Bezeichnungstext wird möglicherweise nicht in der Nähe des Objekts angezeigt, wenn die Microsoft HoloLens Sensoren und/oder spatialTrackingComponent in Unity die entsprechenden Collider nicht platzieren können, relativ zu den realen Objekten. Versuchen Sie, die Anwendung auf einer anderen Oberfläche zu verwenden, wenn dies der Fall ist.

## <a name="your-custom-vision-object-detection-application"></a>Ihre Custom Vision, Objekterkennungsanwendung

Herzlichen Glückwunsch! Sie haben eine Mixed Reality-App erstellt, die die Azure Custom Vision, Objekterkennungs-API, nutzt, die ein Objekt aus einem Bild erkennen und dann eine ungefähre Position für dieses Objekt im 3D-Raum bereitstellen kann.

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a>Zusatzübungen

### <a name="exercise-1"></a>Übung 1

Fügen Sie zur Textbezeichnung hinzu, und verwenden Sie einen halbtransparenten Cube, um das echte Objekt in einem *3D-Begrenzungsfeld* zu umschließen.

### <a name="exercise-2"></a>Übung 2

Trainieren Sie Ihren Custom Vision Service, um weitere Objekte zu erkennen.

### <a name="exercise-3"></a>Übung 3

Gibt einen Sound wieder, wenn ein Objekt erkannt wird.

### <a name="exercise-4"></a>Übung 4

Verwenden Sie die API, um Ihren Dienst mit den gleichen Bildern neu zu trainieren, die Ihre App analysiert, um den Dienst genauer zu gestalten (Vorhersage und Training gleichzeitig durchführen).
