---
title: 'HoloLens (1. Generation) und Azure 309: Application Insights'
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie mithilfe des Azure-Anwendung Insights-Diensts Analysen zum Benutzerverhalten in einer Mixed Reality-Anwendung sammeln.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, Tutorial, API, Application Insights, HoloLens, immersive, vr, Windows 10, Visual Studio
ms.openlocfilehash: 549afbd1e5a3f42bb0540714500d31edf022d36511961e887ac9e927b9af1ea3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115222172"
---
# <a name="hololens-1st-gen-and-azure-309-application-insights"></a>HoloLens (1. Generation) und Azure 309: Application Insights

<br>

>[!NOTE]
>Die Tutorials der Mixed Reality Academy wurden im Hinblick auf HoloLens (1. Gen.) und immersive Mixed Reality-Headsets entworfen.  Daher halten wir es für wichtig, diese Tutorials für Entwickler verfügbar zu halten, die noch nach Anleitung beim Entwickeln für diese Geräte suchen.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für HoloLens 2 verwendet werden.  Sie werden gewartet, um weiterhin auf den unterstützten Geräten zu funktionieren. Es wird eine neue Reihe von Tutorials geben, die in Zukunft veröffentlicht werden, die veranschaulichen, wie sie für HoloLens 2 entwickelt werden.  Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn sie veröffentlicht werden.

<br>

![final product -start](images/AzureLabs-Lab309-00.png)

In diesem Kurs erfahren Sie, wie Sie einer Mixed Reality-Anwendung Application Insights-Funktionen hinzufügen, indem Sie die Azure-Anwendung Insights-API verwenden, um Analysen zum Benutzerverhalten zu sammeln.

Application Insights ist ein Microsoft-Dienst, mit dem Entwickler Analysen aus ihren Anwendungen erfassen und über ein benutzerfreundliches Portal verwalten können. Die Analyse kann von der Leistung bis hin zu benutzerdefinierten Informationen sein, die Sie sammeln möchten. Weitere Informationen finden Sie auf der [Seite Application Insights](https://azure.microsoft.com/services/application-insights/).

Nach Abschluss dieses Kurses verfügen Sie über eine Immersive Headset-Mixed Reality-Anwendung, die folgende Schritte ausführen kann:

1.  Ermöglicht es dem Benutzer, eine Szene anzuvschen und zu bewegen.
2.  Lösen Sie das Senden von Analysen an den *Application Insights Service* aus, indem Sie Anverweise und Nähe zu Objekten in der Szene verwenden.
3.  Die App ruft auch den Dienst auf und ruft innerhalb der letzten 24 Stunden Informationen dazu ab, welches Objekt vom Benutzer am meisten erreicht wurde. Dieses Objekt ändert seine Farbe in Grün.

In diesem Kurs erfahren Sie, wie Sie die Ergebnisse aus application Insights Service in einer Unity-basierten Beispielanwendung abrufen. Sie müssen diese Konzepte auf eine benutzerdefinierte Anwendung anwenden, die Sie möglicherweise erstellen.

## <a name="device-support"></a>Geräteunterstützung

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td> MR und Azure 309: Application Insights</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Während sich dieser Kurs hauptsächlich auf Windows Mixed Reality immersiven Headsets (VR) konzentriert, können Sie auch das, was Sie in diesem Kurs lernen, auf Microsoft HoloLens anwenden. Während Sie den Kurs durchgehen, werden Ihnen Hinweise zu allen Änderungen angezeigt, die Sie ggf. zur Unterstützung HoloLens verwenden müssen. Wenn Sie HoloLens verwenden, können Sie während der Spracherfassung ein Echo bemerken.

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
- Eine Reihe von Mikrofonen mit einem integrierten Mikrofon (wenn das Headset nicht über ein integriertes Mikrofon und Lautsprecher verfügt)
- Internetzugriff für Azure-Setup und Anwendungs-Insights Datenabruf

## <a name="before-you-start"></a>Vorbereitung

Um Probleme bei der Erstellung dieses Projekts zu vermeiden, wird dringend empfohlen, das in diesem Tutorial erwähnte Projekt in einem Stammordner oder in einem Ordner in der Nähe des Stammordners zu erstellen (lange Ordnerpfade können zur Buildzeit Probleme verursachen).

> [!WARNING] 
> Beachten Sie, dass daten, die an *Application Insights* gehen, Zeit in Anspruch nehmen, also seien Sie mit Vorsicht. Wenn Sie überprüfen möchten, ob der Dienst Ihre Daten empfangen hat, lesen Sie [Kapitel 14](#chapter-14---the-application-insights-service-portal), das Ihnen zeigt, wie Sie im Portal navigieren.

## <a name="chapter-1---the-azure-portal"></a>Kapitel 1: Das Azure-Portal

Um *Application Insights* zu verwenden, müssen Sie einen *Application Insights Service* in der Azure-Portal erstellen und konfigurieren.

1.  Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

    > [!NOTE]
    > Wenn Sie noch nicht über ein Azure-Konto verfügen, müssen Sie eins erstellen. Wenn Sie dieses Tutorial in einer Classroom- oder Lab-Situation durchgehen, bitten Sie Ihren Dozenten oder einen der Proctors um Hilfe beim Einrichten Ihres neuen Kontos.

2.  Klicken Sie nach der Anmeldung oben links auf **Neu,** suchen Sie nach *Anwendung Insights*, und drücken Sie **die EINGABETASTE.**

    > [!NOTE]
    > Das Wort **Neu** wurde in neueren Portalen möglicherweise durch **Ressource erstellen** ersetzt.

    ![Azure-Portal](images/AzureLabs-Lab309-01.png)

3.  Die neue Seite auf der rechten  Seite enthält eine Beschreibung des Azure-Anwendung Insights-Diensts. Wählen Sie unten links auf dieser Seite die Schaltfläche **Erstellen** aus, um eine Zuordnung zu diesem Dienst zu erstellen.

    ![Azure-Portal](images/AzureLabs-Lab309-02.png)

4.  Nachdem Sie auf **Erstellen** geklickt haben:

    1.  Fügen Sie den gewünschten **Namen** für diese Dienstinstanz ein.

    2.  Wählen Sie als **Anwendungstyp** die Option **Allgemein** aus.

    3.  Wählen Sie ein **geeignetes Abonnement aus.**

    4.  Wählen Sie eine **Ressourcengruppe** aus, oder erstellen Sie eine neue. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, Steuern des Zugriffs, Bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt zugeordnet sind (z. B. diese Kurse), einer gemeinsamen Ressourcengruppe zuzuordnen.

        > Weitere Informationen zu Azure-Ressourcengruppen finden Sie [im Artikel zu Ressourcengruppen.](/azure/azure-resource-manager/resource-group-portal)

    5.  Wählen Sie einen **Speicherort** aus.

    6.  Sie müssen auch bestätigen, dass Sie die für diesen Dienst geltenden Geschäftsbedingungen verstanden haben.

    7.  Klicken Sie auf **Erstellen**.

        ![Azure-Portal](images/AzureLabs-Lab309-03.png)

5.  Nachdem Sie auf **Erstellen** geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. Dies kann eine Minute dauern.

6.  Sobald die Dienstinstanz erstellt wurde, wird eine Benachrichtigung im Portal angezeigt.

    ![Azure-Portal](images/AzureLabs-Lab309-04.png)

7.  Klicken Sie auf die Benachrichtigungen, um Ihre neue Dienstinstanz zu untersuchen.

    ![Azure-Portal](images/AzureLabs-Lab309-05.png)

8.  Klicken Sie in der Benachrichtigung auf die Schaltfläche **Zu Ressource** wechseln, um Ihre neue Dienstinstanz zu untersuchen. Sie gelangen zu Ihrer neuen *Application Insights Service-Instanz.*

    ![Azure-Portal](images/AzureLabs-Lab309-06.png)

    > [!NOTE]
    >  Lassen Sie diese Webseite geöffnet und leicht zugänglich. Sie kehren hier häufig zurück, um die gesammelten Daten anzuzeigen.

    > [!IMPORTANT]
    > Um Application Insights zu implementieren, müssen Sie drei (3) spezifische Werte verwenden: **Instrumentierungsschlüssel,** **Anwendungs-ID** und **API-Schlüssel.** Im Folgenden erfahren Sie, wie Sie diese Werte von Ihrem Dienst abrufen. Achten Sie darauf, diese Werte auf einer leeren *Editor* Seite zu notieren, da Sie sie in Kürze in Ihrem Code verwenden werden.

9.  Um den **Instrumentierungsschlüssel** zu finden, müssen Sie in der Liste der Dienstfunktionen nach unten scrollen und auf **Eigenschaften** klicken. Auf der angezeigten Registerkarte wird der **Dienstschlüssel** angezeigt.

    ![Azure-Portal](images/AzureLabs-Lab309-07.png)

10. Ein wenig unter **Eigenschaften** finden Sie **API-Zugriff**, auf den Sie klicken müssen. Im Bereich auf der rechten Seite wird die **Anwendungs-ID** Ihrer App angezeigt.

    ![Azure-Portal](images/AzureLabs-Lab309-08.png)

11. Wenn der **Bereich Anwendungs-ID** noch geöffnet ist, klicken Sie auf **API-Schlüssel erstellen,** um den Bereich *API-Schlüssel erstellen* zu öffnen.

    ![Azure-Portal](images/AzureLabs-Lab309-09.png)

12. Geben Sie im jetzt geöffneten Bereich *API-Schlüssel erstellen* eine Beschreibung ein, und **aktivieren Sie die drei Kontrollkästchen**.

13. Klicken Sie auf **Schlüssel generieren.** Ihr **API-Schlüssel** wird erstellt und angezeigt. 

    ![Azure-Portal](images/AzureLabs-Lab309-10.png)
        
    > [!WARNING]
    > Dies ist das einzige Mal, wenn Ihr **Dienstschlüssel** angezeigt wird. Stellen Sie daher sicher, dass Sie jetzt eine Kopie davon erstellen.

## <a name="chapter-2---set-up-the-unity-project"></a>Kapitel 2: Einrichten des Unity-Projekts

Im Folgenden finden Sie eine typische Einrichtung für die Entwicklung mit Mixed Reality und ist daher eine gute Vorlage für andere Projekte.

1.  Öffnen Sie *Unity,* und klicken Sie auf **Neu.**

    ![Einrichten der Unity-Project](images/AzureLabs-Lab309-11.png)

2.  Sie müssen nun einen Unity-Project angeben, **MR \_ Azure Application \_ Insights. \_** Stellen Sie *sicher, dass die* Vorlage auf **3D festgelegt ist.** Legen Sie *den Speicherort* auf einen für Sie geeigneten Speicherort fest (denken Sie daran, dass die Nähe zu Stammverzeichnissen besser ist). Klicken Sie dann auf **Projekt erstellen.**

    ![Einrichten der Unity-Project](images/AzureLabs-Lab309-12.png)

3.  Wenn Unity geöffnet ist, sollten Sie überprüfen, ob der **Standardskript-Editor** auf **Visual Studio.** Wechseln Sie **zu \> Einstellungen bearbeiten,** und navigieren Sie dann im neuen Fenster zu **Externe Tools.** Ändern **Sie den editor für externe** **Skripts in Visual Studio 2017**. Schließen Sie das **Fenster Einstellungen.**

    ![Einrichten der Unity-Project](images/AzureLabs-Lab309-13.png)

4.  Wechseln Sie als Nächstes **zu Datei \> Einstellungen,** und wechseln Sie zur **Universellen Windows-Plattform,** indem Sie auf die **Schaltfläche Plattform wechseln** klicken.

    ![Einrichten der Unity-Project](images/AzureLabs-Lab309-14.png)

5.  Wechseln Sie **zu \> Datei Einstellungen,** und stellen Sie Sicher, dass:

    1.  **Zielgerät** ist auf **Beliebiges Gerät festgelegt.**

        > Legen Sie für Microsoft HoloLens **Zielgerät auf** *HoloLens.*

    2.  **Buildtyp** ist auf **D3D festgelegt**

    3.  **SDK** ist auf **Latest installed (Neueste installiert) festgelegt.**

    4.  **Erstellen und Ausführen** ist auf Lokaler **Computer festgelegt.**

    5.  Speichern Sie die Szene, und fügen Sie sie dem Build hinzu.

        1.  Wählen Sie hierzu Geöffnete Szenen **hinzufügen aus.** Ein Speicherfenster wird angezeigt.

            ![Einrichten der Unity-Project](images/AzureLabs-Lab309-15.png)

        2. Erstellen Sie einen neuen Ordner für diese und  jede zukünftige Szene, und klicken Sie dann auf die Schaltfläche Neuer Ordner, um einen neuen Ordner zu erstellen, und nennen Sie **ihn Scenes**.

            ![Einrichten der Unity-Project](images/AzureLabs-Lab309-16.png)

        3. Öffnen Sie den neu erstellten **Ordner Scenes,** und geben Sie im Textfeld *Dateiname:* **applicationInsightsScene** ein, und klicken Sie dann **auf Speichern.**

            ![Einrichten der Unity-Project](images/AzureLabs-Lab309-17.png)

6.  Die restlichen Einstellungen in **Build Einstellungen** sollten vorerde als Standardeinstellung be übrig bleiben.

7.  Klicken Sie **im Fenster Build Einstellungen** auf die Schaltfläche Player **Einstellungen,** um den entsprechenden Bereich in dem Bereich zu öffnen, in dem sich der **Inspektor** befindet.

    ![Einrichten der Unity-Project](images/AzureLabs-Lab309-18.png)

8. In diesem Bereich müssen einige Einstellungen überprüft werden:

    1.  Führen Sie **auf Einstellungen** Registerkarte Andere Optionen aus:

        1.  **Die** **Skriptlaufzeitversion** sollte **experimentell (.NET 4.6 Equivalent)** sein, wodurch ein Neustart des Editors ausgelöst wird.

        2.  **Das Skript-Back-End** sollte **.NET sein.**

        3.  **Der API-Kompatibilitätsgrad** sollte **.NET 4.6 sein.**

        ![Einrichten der Unity-Project](images/AzureLabs-Lab309-19.png)

    2.  Aktivieren Sie **auf Einstellungen** Registerkarte Publishing Einstellungen unter **Capabilities (Funktionen)** Die folgenden Optionen:

        - **InternetClient**     

            ![Einrichten der Unity-Project](images/AzureLabs-Lab309-20.png)

    3.  Aktivieren Sie weiter unten im Bereich in **XR Einstellungen** (unter Publishing **Einstellungen)** **(Virtual Reality** unterstützt), und stellen Sie sicher, dass das Windows Mixed Reality **SDK** hinzugefügt wird.

        ![Einrichten der Unity-Project](images/AzureLabs-Lab309-21.png)

9.  Im **Build-Einstellungen** ist **Unity C#-Projekte** nicht mehr ausgegraut. aktivieren Sie das Kontrollkästchen daneben.

10.  Schließen Sie das Fenster „Build Settings“ (Buildeinstellungen).

11.  Speichern Sie Ihre Szene und Project (**FILE**  >  **SAVE SCENE /FILE**  >  **SAVE PROJECT**).


## <a name="chapter-3---import-the-unity-package"></a>Kapitel 3: Importieren des Unity-Pakets

> [!IMPORTANT]
> Wenn Sie die *Unity-Komponenten* dieses Kurses einrichten überspringen und direkt mit dem Code fortfahren möchten, können Sie dieses [Azure-MR-309.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage)herunterladen und als benutzerdefiniertes Paket in Ihr Projekt [**importieren.**](https://docs.unity3d.com/Manual/AssetPackages.html) Dieser enthält auch die DLLs aus dem nächsten Kapitel. Fahren Sie nach dem Import mit [**Kapitel 6 fort.**](#chapter-6---create-the-applicationinsightstracker-class)

> [!IMPORTANT]
> Um Application Insights in Unity zu verwenden, müssen Sie die DLL dafür zusammen mit der Newtonsoft-DLL importieren. Derzeit gibt es ein bekanntes Problem in Unity, bei dem Plug-Ins nach dem Import neu konfiguriert werden müssen. Diese Schritte (4 bis 7 in diesem Abschnitt) sind nicht mehr erforderlich, nachdem der Fehler behoben wurde.

Um Application Insights in Ihr eigenes Projekt zu importieren, stellen Sie sicher, dass Sie das Paket [".unitypackage" mit den Plug-Ins heruntergeladen haben.](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage) Gehen Sie nun wie folgt vor:

1.  Fügen Sie **unitypackage mithilfe der** Menüoption **Assets Import Package Custom \> \> Package (Benutzerdefiniertes** Paket importieren) zu Unity hinzu.

2.  Vergewissern Sie sich im angezeigten Feld **Unity-Paket** importieren, dass alles unter (und einschließlich) **Plug-Ins** ausgewählt ist.

    ![Importieren des Unity-Pakets](images/AzureLabs-Lab309-22.png)

3.  Klicken Sie auf **die Schaltfläche** Importieren, um dem Projekt die Elemente hinzuzufügen.

4.  Wechseln Sie in **der Insights** unter **Plug-Ins** zum Ordner Project, und wählen Sie nur die folgenden Plug-Ins *aus:*

    -   Microsoft.ApplicationInsights

    ![Importieren des Unity-Pakets](images/AzureLabs-Lab309-23.png)

5.  Wenn dieses *Plug-In* ausgewählt ist, stellen Sie sicher, dass Alle Plattformen deaktiviert **ist,** und stellen Sie dann sicher, dass **auch WSAPlayer** deaktiviert **ist,** und klicken Sie dann **auf Anwenden.**  Dadurch wird lediglich bestätigt, dass die Dateien ordnungsgemäß konfiguriert sind.

    ![Importieren des Unity-Pakets](images/AzureLabs-Lab309-24.png)

    > [!NOTE]
    > Wenn Sie die Plug-Ins wie diese markieren, werden sie so konfiguriert, dass sie nur im Unity-Editor verwendet werden. Es gibt einen anderen Satz von DLLs im WSA-Ordner, der verwendet wird, nachdem das Projekt aus Unity exportiert wurde.

6.  Als Nächstes müssen Sie den **WSA-Ordner** im **Ordner** Insights öffnen. Sie sehen eine Kopie derselben Datei, die Sie gerade konfiguriert haben. Wählen Sie diese Datei aus, und  stellen Sie dann im Inspektor  sicher, dass Alle Plattformen deaktiviert **ist,** und stellen Sie dann sicher, dass nur **WSAPlayer** **aktiviert ist.** Klicken Sie auf **Anwenden**.

    ![Importieren des Unity-Pakets](images/AzureLabs-Lab309-25.png)

7. Sie müssen nun die Schritte **4 bis 6** ausführen, aber stattdessen für *die Newtonsoft-Plug-Ins.* Im folgenden Screenshot sehen Sie, wie das Ergebnis aussehen sollte.

    ![Importieren des Unity-Pakets](images/AzureLabs-Lab309-25-5.png)    

## <a name="chapter-4---set-up-the-camera-and-user-controls"></a>Kapitel 4: Einrichten der Kamera- und Benutzersteuerelemente

In diesem Kapitel richten Sie die Kamera und die Steuerelemente ein, damit der Benutzer die Szene sehen und sich bewegen kann.

1.  Klicken Sie im Hierarchiebereich mit der rechten Maustaste auf einen leeren Bereich, und klicken Sie dann **auf Leere**  >  **erstellen.**

    ![Einrichten der Kamera und der Benutzersteuerelemente](images/AzureLabs-Lab309-26.png)

2.  Benennen Sie das neue leere GameObject in **Camera Parent um.**

    ![Einrichten der Kamera und der Benutzersteuerelemente](images/AzureLabs-Lab309-27.png)

3.  Klicken Sie mit der rechten Maustaste in einen leeren Bereich im Hierarchiebereich, dann auf **3D-Objekt** und dann auf **Sphere.**

4.  Benennen Sie die Kugel in **rechts um.**

5.  Legen Sie **die Transformationsskala** der rechten Seite auf **0,1, 0,1, 0,1 fest.**

    ![Einrichten der Kamera und der Benutzersteuerelemente](images/AzureLabs-Lab309-28.png)

6.  Entfernen Sie **die Sphere Collider-Komponente** aus der rechten Hand, indem Sie **in** der *Sphere Collider-Komponente* auf das Zahnrad klicken und dann **Komponente entfernen.**

    ![Einrichten der Kamera und der Benutzersteuerelemente](images/AzureLabs-Lab309-29.png)

7.  Ziehen Sie im Hierarchiebereich die **Hauptkamera** und die **rechten** Objekte auf das **übergeordnete Kameraobjekt.**

    ![Einrichten der Kamera und der Benutzersteuerelemente](images/AzureLabs-Lab309-30.png)

8.  Legen Sie **die Transformationsposition** sowohl der **Hauptkamera** als auch des **rechten** Objekts auf **0, 0, 0 fest.**

    ![Einrichten der Kamera und der Benutzersteuerelemente](images/AzureLabs-Lab309-31.png)

    ![Einrichten der Kamera und der Benutzersteuerelemente](images/AzureLabs-Lab309-32.png)

## <a name="chapter-5---set-up-the-objects-in-the-unity-scene"></a>Kapitel 5: Einrichten der Objekte in der Unity-Szene

Sie erstellen nun einige grundlegende Formen für Ihre Szene, mit denen der Benutzer interagieren kann.

1.  Klicken Sie im Hierarchiebereich mit der rechten Maustaste auf einen leeren *Bereich,* klicken Sie dann auf **3D-Objekt,** und wählen Sie dann **Ebene aus.**

2.  Legen Sie die Position **der Ebenentransformation** **auf 0, -1, 0 fest.**

3.  Legen Sie die Ebene **Transform Scale auf** **5, 1, 5 fest.**

    ![Einrichten der Objekte in der Unity-Szene](images/AzureLabs-Lab309-33.png)

4.  Erstellen Sie ein grundlegendes Material, das mit Ihrem **Plane-Objekt verwendet** werden soll, damit die anderen Formen leichter zu erkennen sind. Navigieren Sie zum Project Bereich, klicken Sie mit der rechten Maustaste, und klicken Sie dann auf Erstellen und dann auf **Ordner**, um einen neuen Ordner zu erstellen.  Nennen Sie **es Materials**.

    ![Einrichten der Objekte in der Unity-Szene](images/AzureLabs-Lab309-34.png) ![Einrichten der Objekte in der Unity-Szene](images/AzureLabs-Lab309-35.png)

5.  Öffnen Sie den Ordner **Materials (Materialien),** klicken Sie mit der rechten Maustaste darauf, klicken Sie auf **Erstellen** und dann auf **Material**, um ein neues Material zu erstellen. Nennen Sie es **Blau.**

    ![Einrichten der Objekte in der Unity-Szene](images/AzureLabs-Lab309-36.png) ![Einrichten der Objekte in der Unity-Szene](images/AzureLabs-Lab309-37.png)

6.  Wenn sie das neue **blaue** Material ausgewählt haben, sehen Sie sich den *Inspektor* an, und klicken Sie neben **Albedo** auf das rechteckige Fenster. Wählen Sie eine blaue Farbe aus (die folgende Abbildung ist **Hexadezimalfarbe: \# 3592FFFF**). Klicken Sie auf die Schaltfläche "Schließen", nachdem Sie ausgewählt haben.

    ![Einrichten der Objekte in der Unity-Szene](images/AzureLabs-Lab309-38.png)

7.  Ziehen Sie das neue Material aus dem Ordner **Materials (Materialien)** auf die neu erstellte **Ebene** innerhalb Ihrer Szene (oder legen Sie es im **Objekt Plane** innerhalb der *Hierarchie* ab).

    ![Einrichten der Objekte in der Unity-Szene](images/AzureLabs-Lab309-39.png)

8.  Klicken Sie mit der rechten Maustaste in einen leeren Bereich im *Hierarchiebereich,* und klicken Sie dann auf **3D-Objekt, Kapselung.**

    -  Ändern Sie die  *Transformationsposition* bei ausgewähltem **"10",** **"1", "0".**

9.  Klicken Sie mit der rechten Maustaste in einen leeren Bereich im *Hierarchiebereich,* und klicken Sie dann auf **3D-Objekt, Cube.**

    -  Ändern Sie bei ausgewähltem **Cube** die **Transformationsposition**  in **0, 0, 10.**

10. Klicken Sie mit der rechten Maustaste in einen leeren Bereich im *Hierarchiebereich,* und klicken Sie dann auf **3D-Objekt, Kugel.**

    -  Ändern Sie bei **ausgewähltem Sphere** die **Transformationsposition**  in **10, 0, 0**.

    ![Einrichten der Objekte in der Unity-Szene](images/AzureLabs-Lab309-40.png)

    > [!NOTE]
    > Diese *Positionswerte* sind *Vorschläge.* Sie können die Positionen der Objekte beliebig festlegen, obwohl es für den Benutzer der Anwendung einfacher ist, wenn die Entfernungen der Objekte nicht zu weit von der Kamera entfernt sind.

11. Wenn Ihre Anwendung ausgeführt wird, muss sie in der Lage sein, die Objekte innerhalb der Szene zu identifizieren, um dies zu erreichen, müssen sie markiert werden. Wählen Sie eines der -Objekte aus, und klicken Sie im Bereich *Inspektor* auf **Tag hinzufügen...**, wodurch der *Inspektor* durch den Bereich **Tags & Ebenen** ausgetauscht wird.

    ![Einrichten der Objekte in der Unity-Szene ](images/AzureLabs-Lab309-41.png)![](images/AzureLabs-Lab309-42.png)

12. Klicken Sie auf das Symbol **+ (Pluszeichen),** und geben Sie den Tagnamen als **ObjectInScene** ein.

    ![Einrichten der Objekte in der Unity-Szene](images/AzureLabs-Lab309-43.png)

    > [!WARNING]
    > Wenn Sie einen anderen Namen für Ihr Tag verwenden, müssen Sie sicherstellen, dass diese Änderung auch an den Skripts *DataFromAnalytics,* *ObjectTrigger* und *Gaze* vorgenommen wird, damit Ihre Objekte in Ihrer Szene gefunden und erkannt werden.

13. Nachdem das Tag erstellt wurde, müssen Sie es jetzt auf alle drei Objekte anwenden. Halten Sie in der *Hierarchie* die **UMSCHALTTASTE** gedrückt, und klicken Sie dann auf die Objekte **Kapselung,** **Würfel** und **Kugel**, und klicken Sie dann im *Inspektor* neben **Tag** auf das Dropdownmenü, und klicken Sie dann auf das von Ihnen erstellte *ObjectInScene-Tag.*

    ![Einrichten der Objekte in der Unity-Szene ](images/AzureLabs-Lab309-44.png)![](images/AzureLabs-Lab309-45.png)

## <a name="chapter-6---create-the-applicationinsightstracker-class"></a>Kapitel 6: Erstellen der ApplicationInsightsTracker-Klasse

Das erste Skript, das Sie erstellen müssen, ist **ApplicationInsightsTracker,** das für Folgendes zuständig ist:

1.  Erstellen von Ereignissen basierend auf Benutzerinteraktionen, die an Azure-Anwendung Insights übermittelt werden sollen.

2. Erstellen geeigneter Ereignisnamen, abhängig von der Benutzerinteraktion.

3. Übermitteln von Ereignissen an die Application Insights Service-Instanz.

So erstellen Sie diese Klasse:

1.  Klicken Sie mit der rechten Maustaste im *Project Bereich* und dann auf   >  **Ordner** erstellen. Nennen Sie den Ordner **Skripts**.

    ![Erstellen der ApplicationInsightsTracker-Klasse](images/AzureLabs-Lab309-46.png)  ![Erstellen der ApplicationInsightsTracker-Klasse](images/AzureLabs-Lab309-47.png)

2.  Doppelklicken Sie nach dem Erstellen des **Ordners Scripts** darauf, um ihn zu öffnen. Klicken **Sie** dann in diesem Ordner mit der rechten Maustaste auf  >  **C#-Skript erstellen.** Nennen Sie das Skript **ApplicationInsightsTracker**.

3.  Doppelklicken Sie auf das neue **ApplicationInsightsTracker-Skript,** um es mit **Visual Studio** zu öffnen.

4.  Aktualisieren Sie namespaces am Anfang des Skripts wie folgt:

    ```csharp
        using Microsoft.ApplicationInsights;
        using Microsoft.ApplicationInsights.DataContracts;
        using Microsoft.ApplicationInsights.Extensibility;
        using UnityEngine;
    ```

5.  Fügen Sie in der -Klasse die folgenden Variablen ein:

    ```csharp
        /// <summary>
        /// Allows this class to behavior like a singleton
        /// </summary>
        public static ApplicationInsightsTracker Instance;
        
        /// <summary>
        /// Insert your Instrumentation Key here
        /// </summary>
        internal string instrumentationKey = "Insert Instrumentation Key here";

        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        internal string applicationId = "Insert Application Id here";

        /// <summary>
        /// Insert your API Key here
        /// </summary>
        internal string API_Key = "Insert API Key here";

        /// <summary>
        /// Represent the Analytic Custom Event object
        /// </summary>
        private TelemetryClient telemetryClient;

        /// <summary>
        /// Represent the Analytic object able to host gaze duration
        /// </summary>
        private MetricTelemetry metric;
    ```

    > [!NOTE] 
    > Legen Sie die Werte **instrumentationKey, applicationId und API_Key** entsprechend fest, indem Sie die *Dienstschlüssel* aus dem Azure-Portal verwenden, wie in [Kapitel 1,](#chapter-1---the-azure-portal)Schritt 9 und weiter oben beschrieben.

6.  Fügen Sie dann die **Methoden Start()** und **Awake()** hinzu, die aufgerufen werden, wenn die Klasse initialisiert wird:

    ```csharp
        /// <summary>
        /// Sets this class instance as a singleton
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Instantiate telemetry and metric
            telemetryClient = new TelemetryClient();

            metric = new MetricTelemetry();

            // Assign the Instrumentation Key to the Event and Metric objects
            TelemetryConfiguration.Active.InstrumentationKey = instrumentationKey;

            telemetryClient.InstrumentationKey = instrumentationKey;
        }
    ```

7.  Fügen Sie die Methoden hinzu, die für das Senden der von Ihrer Anwendung registrierten Ereignisse und Metriken verantwortlich sind:

    ```csharp
        /// <summary>
        /// Submit the Event to Azure Analytics using the event trigger object
        /// </summary>
        public void RecordProximityEvent(string objectName)
        {
            telemetryClient.TrackEvent(CreateEventName(objectName));
        }

        /// <summary>
        /// Uses the name of the object involved in the event to create 
        /// and return an Event Name convention
        /// </summary>
        public string CreateEventName(string name)
        {
            string eventName = $"User near {name}";
            return eventName;
        }

        /// <summary>
        /// Submit a Metric to Azure Analytics using the metric gazed object
        /// and the time count of the gaze
        /// </summary>
        public void RecordGazeMetrics(string objectName, int time)
        {
            // Output Console information about gaze.
            Debug.Log($"Finished gazing at {objectName}, which went for <b>{time}</b> second{(time != 1 ? "s" : "")}");

            metric.Name = $"Gazed {objectName}";

            metric.Value = time;

            telemetryClient.TrackMetric(metric);
        }
    ```

8.  Speichern Sie ihre Änderungen in *Visual Studio,* bevor Sie zu *Unity* zurückkehren.

## <a name="chapter-7---create-the-gaze-script"></a>Kapitel 7: Erstellen des Skripts "Anv"

Das nächste skript,  das erstellt werden soll, ist das Gaze-Skript. Dieses Skript ist für die Erstellung eines *Raycasts* verantwortlich, der von der *Hauptkamera* nach vorne projiziert wird, um zu erkennen, welches Objekt der Benutzer ansieht. In diesem Fall muss *raycast* ermitteln, ob der Benutzer ein Objekt mit dem Tag **ObjectInScene** ansieht, und dann zählen, wie lange der Benutzer auf dieses Objekt *anviert.*

1.  Doppelklicken Sie auf den Ordner **Skripts,** um ihn zu öffnen.

2.  Klicken Sie mit der rechten Maustaste in den Ordner **Skripts,** und klicken Sie auf   >  **C#-Skript erstellen.** Nennen Sie das Skript **Gaze**.

3.  Doppelklicken Sie auf das Skript, um es mit Visual Studio zu öffnen.

4.  Ersetzen Sie den vorhandenen Code durch folgenden Code:

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {
            /// <summary>
            /// Provides Singleton-like behavior to this class.
            /// </summary>
            public static Gaze Instance;

            /// <summary>
            /// Provides a reference to the object the user is currently looking at.
            /// </summary>
            public GameObject FocusedGameObject { get; private set; }

            /// <summary>
            /// Provides whether an object has been successfully hit by the raycast.
            /// </summary>
            public bool Hit { get; private set; }

            /// <summary>
            /// Provides a reference to compare whether the user is still looking at 
            /// the same object (and has not looked away).
            /// </summary>
            private GameObject _oldFocusedObject = null;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeMaxDistance = 300;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeTimeCounter = 0;

            /// <summary>
            /// The cursor object will be created when the app is running,
            /// this will store its values. 
            /// </summary>
            private GameObject _cursor;
        }
    ```

5.  Code für die **Methoden "Awake()"** und **"Start()"** muss jetzt hinzugefügt werden.

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton
            Instance = this;
            _cursor = CreateCursor();
        }

        void Start()
        {
            FocusedGameObject = null;
        }

        /// <summary>
        /// Create a cursor object, to provide what the user
        /// is looking at.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()    
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Remove the collider, so it does not block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());

            newCursor.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            newCursor.GetComponent<MeshRenderer>().material.color = 
            Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

            newCursor.SetActive(false);
            return newCursor;
        }
    ```

6.  Fügen Sie in der **Gaze-Klasse** den folgenden Code in der **Update()-Methode** hinzu, um einen *Raycast* zu pro projectieren und den Zieltreffer zu erkennen:

    ```csharp
        /// <summary>
        /// Called every frame
        /// </summary>
        void Update()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedGameObject;

            RaycastHit hitInfo;

            // Initialize Raycasting.
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, _gazeMaxDistance);

            // Check whether raycast has hit.
            if (Hit == true)
            {
                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedGameObject = hitInfo.collider.gameObject;

                    // Lerp the cursor to the hit point, which helps to stabilize the gaze.
                    _cursor.transform.position = Vector3.Lerp(_cursor.transform.position, hitInfo.point, 0.6f);

                    _cursor.SetActive(true);
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedGameObject = null;

                    _cursor.SetActive(false);
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;

                _cursor.SetActive(false);
            }

            // Check whether the previous focused object is this same object. If so, reset the focused object.
            if (FocusedGameObject != _oldFocusedObject)
            {
                ResetFocusedObject();
            }
            // If they are the same, but are null, reset the counter. 
            else if (FocusedGameObject == null && _oldFocusedObject == null)
            {
                _gazeTimeCounter = 0;
            }
            // Count whilst the user continues looking at the same object.
            else
            {
                _gazeTimeCounter += Time.deltaTime;
            }
        }
    ```

7.  Fügen Sie die **ResetFocusedObject()-Methode** hinzu, um Daten an **Application Insights** zu senden, wenn der Benutzer ein Objekt betrachtet hat.

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        public void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                // Only looking for objects with the correct tag.
                if (_oldFocusedObject.CompareTag("ObjectInScene"))
                {
                    // Turn the timer into an int, and ensure that more than zero time has passed.
                    int gazeAsInt = (int)_gazeTimeCounter;

                    if (gazeAsInt > 0)
                    {
                        //Record the object gazed and duration of gaze for Analytics
                        ApplicationInsightsTracker.Instance.RecordGazeMetrics(_oldFocusedObject.name, gazeAsInt);
                    }
                    //Reset timer
                    _gazeTimeCounter = 0;
                }
            }
        }
    ```

8.  Sie haben nun das **Skript "Anv"** abgeschlossen. Speichern Sie Ihre Änderungen in *Visual Studio,* bevor Sie zu *Unity* zurückkehren.

## <a name="chapter-8---create-the-objecttrigger-class"></a>Kapitel 8: Erstellen der ObjectTrigger-Klasse

Das nächste Skript, das Sie erstellen müssen, ist **ObjectTrigger,** das für Folgendes zuständig ist:

- Hinzufügen von Komponenten, die für einen Konflikt zur Hauptkamera erforderlich sind.
- Erkennt, ob sich die Kamera in der Nähe eines Objekts befindet, das als **ObjectInScene** gekennzeichnet ist.

So erstellen Sie das Skript:

1.  Doppelklicken Sie auf den Ordner **Skripts,** um ihn zu öffnen.

2.  Klicken Sie mit der rechten Maustaste in den Ordner **Skripts,** und klicken Sie auf   >  **C#-Skript erstellen.** Nennen Sie das Skript **ObjectTrigger**.

3.  Doppelklicken Sie auf das Skript, um es mit Visual Studio zu öffnen. Ersetzen Sie den vorhandenen Code durch folgenden Code:

    ```csharp
        using UnityEngine;

        public class ObjectTrigger : MonoBehaviour
        {
            private void Start()
            {
                // Add the Collider and Rigidbody components, 
                // and set their respective settings. This allows for collision.
                gameObject.AddComponent<SphereCollider>().radius = 1.5f;

                gameObject.AddComponent<Rigidbody>().useGravity = false;
            }

            /// <summary>
            /// Triggered when an object with a collider enters this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionEnter(Collision collision)
            {
                CompareTriggerEvent(collision, true);
            }

            /// <summary>
            /// Triggered when an object with a collider exits this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionExit(Collision collision)
            {
                CompareTriggerEvent(collision, false);
            }

            /// <summary>
            /// Method for providing debug message, and sending event information to InsightsTracker.
            /// </summary>
            /// <param name="other">Collided object</param>
            /// <param name="enter">Enter = true, Exit = False</param>
            private void CompareTriggerEvent(Collision other, bool enter)
            {
                if (other.collider.CompareTag("ObjectInScene"))
                {
                    string message = $"User is{(enter == true ? " " : " no longer ")}near <b>{other.gameObject.name}</b>";

                    if (enter == true)
                    {
                        ApplicationInsightsTracker.Instance.RecordProximityEvent(other.gameObject.name);
                    }
                    Debug.Log(message);
                }
            }
        }
    ```

4.  Speichern Sie ihre Änderungen in *Visual Studio,* bevor Sie zu *Unity* zurückkehren.

## <a name="chapter-9---create-the-datafromanalytics-class"></a>Kapitel 9: Erstellen der DataFromAnalytics-Klasse

Sie müssen nun das **DataFromAnalytics-Skript** erstellen, das für Folgendes zuständig ist:

- Abrufen von Analysedaten zu dem Objekt, das von der Kamera am meisten erreicht wurde.
- Mithilfe der *Dienstschlüssel*, die die Kommunikation mit Ihrer Azure-Anwendung Insights Service-Instanz ermöglichen.
- Sortieren der Objekte in der Szene, nach denen die höchste Ereignisanzahl hat.
- Ändern der Materialfarbe des am häufigsten angenäherten Objekts in *grün.*

So erstellen Sie das Skript:

1.  Doppelklicken Sie auf den Ordner **Skripts,** um ihn zu öffnen.

2.  Klicken Sie mit der rechten Maustaste in den Ordner **Skripts,** und klicken Sie auf   >  **C#-Skript erstellen.** Nennen Sie das Skript **DataFromAnalytics.**

3.  Doppelklicken Sie auf das Skript, um es mit Visual Studio zu öffnen.

4.  Fügen Sie die folgenden Namespaces ein:

    ```csharp
        using Newtonsoft.Json;
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  Fügen Sie im Skript Folgendes ein:

    ```csharp
        /// <summary>
        /// Number of most recent events to be queried
        /// </summary>
        private int _quantityOfEventsQueried = 10;

        /// <summary>
        /// The timespan with which to query. Needs to be in hours.
        /// </summary>
        private int _timepspanAsHours = 24;

        /// <summary>
        /// A list of the objects in the scene
        /// </summary>
        private List<GameObject> _listOfGameObjectsInScene;

        /// <summary>
        /// Number of queries which have returned, after being sent.
        /// </summary>
        private int _queriesReturned = 0;

        /// <summary>
        /// List of GameObjects, as the Key, with their event count, as the Value.
        /// </summary>
        private List<KeyValuePair<GameObject, int>> _pairedObjectsWithEventCount = new List<KeyValuePair<GameObject, int>>();

        // Use this for initialization
        void Start()
        {
            // Find all objects in scene which have the ObjectInScene tag (as there may be other GameObjects in the scene which you do not want).
            _listOfGameObjectsInScene = GameObject.FindGameObjectsWithTag("ObjectInScene").ToList();

            FetchAnalytics();
        }
    ```

6.  Fügen Sie in der **DataFromAnalytics-Klasse** direkt nach der **Start()-Methode** die folgende Methode namens **FetchAnalytics()** hinzu. Diese Methode ist dafür verantwortlich, die Liste der Schlüsselwertpaare mit einem *GameObject* und einer Platzhalterereignisanzahl aufzufüllen. Anschließend wird die **GetWebRequest()-Coroutine** initialisiert. Die Abfragestruktur des Aufrufs von *Application Insights* finden Sie auch in dieser Methode als *Abfrage-URL-Endpunkt.*

    ```csharp
        private void FetchAnalytics()
        {
            // Iterate through the objects in the list
            for (int i = 0; i < _listOfGameObjectsInScene.Count; i++)
            {
                // The current event number is not known, so set it to zero.
                int eventCount = 0;

                // Add new pair to list, as placeholder, until eventCount is known.
                _pairedObjectsWithEventCount.Add(new KeyValuePair<GameObject, int>(_listOfGameObjectsInScene[i], eventCount));

                // Set the renderer of the object to the default color, white
                _listOfGameObjectsInScene[i].GetComponent<Renderer>().material.color = Color.white;

                // Create the appropriate object name using Insights structure
                string objectName = _listOfGameObjectsInScene[i].name;
 
                // Build the queryUrl for this object.
                string queryUrl = Uri.EscapeUriString(string.Format(
                    "https://api.applicationinsights.io/v1/apps/{0}/events/$all?timespan=PT{1}H&$search={2}&$select=customMetric/name&$top={3}&$count=true",
                    ApplicationInsightsTracker.Instance.applicationId, _timepspanAsHours, "Gazed " + objectName, _quantityOfEventsQueried));


                // Send this object away within the WebRequest Coroutine, to determine it is event count.
                StartCoroutine("GetWebRequest", new KeyValuePair<string, int>(queryUrl, i));
            }
        }
    ```

7.  Fügen Sie direkt unterhalb der **FetchAnalytics()-Methode** eine Methode namens **GetWebRequest()** hinzu, die einen *IEnumerator* zurückgibt. Diese Methode ist dafür verantwortlich, die Anzahl der Aufrufe eines Ereignisses, das einem bestimmten *GameObject* entspricht, innerhalb von *Application Insights* anzufordern. Wenn alle gesendeten Abfragen zurückgegeben wurden, wird die **DetermineWinner()-Methode** aufgerufen.

    ```csharp
        /// <summary>
        /// Requests the data count for number of events, according to the
        /// input query URL.
        /// </summary>
        /// <param name="webQueryPair">Query URL and the list number count.</param>
        /// <returns></returns>
        private IEnumerator GetWebRequest(KeyValuePair<string, int> webQueryPair)
        {
            // Set the URL and count as their own variables (for readability).
            string url = webQueryPair.Key;
            int currentCount = webQueryPair.Value;

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(url))
            {
                DownloadHandlerBuffer handlerBuffer = new DownloadHandlerBuffer();

                unityWebRequest.downloadHandler = handlerBuffer;

                unityWebRequest.SetRequestHeader("host", "api.applicationinsights.io");

                unityWebRequest.SetRequestHeader("x-api-key", ApplicationInsightsTracker.Instance.API_Key);

                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError)
                {
                    // Failure with web request.
                    Debug.Log("<color=red>Error Sending:</color> " + unityWebRequest.error);
                }
                else
                {
                    // This query has returned, so add to the current count.
                    _queriesReturned++;

                    // Initialize event count integer.
                    int eventCount = 0;

                    // Deserialize the response with the custom Analytics class.
                    Analytics welcome = JsonConvert.DeserializeObject<Analytics>(unityWebRequest.downloadHandler.text);

                    // Get and return the count for the Event
                    if (int.TryParse(welcome.OdataCount, out eventCount) == false)
                    {
                        // Parsing failed. Can sometimes mean that the Query URL was incorrect.
                        Debug.Log("<color=red>Failure to Parse Data Results. Check Query URL for issues.</color>");
                    }
                    else
                    {
                        // Overwrite the current pair, with its actual values, now that the event count is known.
                        _pairedObjectsWithEventCount[currentCount] = new KeyValuePair<GameObject, int>(_pairedObjectsWithEventCount[currentCount].Key, eventCount);
                    }

                    // If all queries (compared with the number which was sent away) have 
                    // returned, then run the determine winner method. 
                    if (_queriesReturned == _pairedObjectsWithEventCount.Count)
                    {
                        DetermineWinner();
                    }
                }
            }
        }
    ```

8.  Die nächste Methode ist **DetermineWinner()**, die die Liste der *GameObject-* und *Int-Paare* nach der höchsten Ereignisanzahl sortiert. Anschließend wird die Materialfarbe dieses *GameObject* in *Grün* geändert (als Feedback für die höchste Anzahl). Dadurch wird eine Meldung mit den Analyseergebnissen angezeigt.

    ```csharp
        /// <summary>
        /// Call to determine the keyValue pair, within the objects list, 
        /// with the highest event count.
        /// </summary>
        private void DetermineWinner()
        {
            // Sort the values within the list of pairs.
            _pairedObjectsWithEventCount.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Change its colour to green
            _pairedObjectsWithEventCount.First().Key.GetComponent<Renderer>().material.color = Color.green;

            // Provide the winner, and other results, within the console window. 
            string message = $"<b>Analytics Results:</b>\n " +
                $"<i>{_pairedObjectsWithEventCount.First().Key.name}</i> has the highest event count, " +
                $"with <i>{_pairedObjectsWithEventCount.First().Value.ToString()}</i>.\nFollowed by: ";

            for (int i = 1; i < _pairedObjectsWithEventCount.Count; i++)
            {
                message += $"{_pairedObjectsWithEventCount[i].Key.name}, " +
                    $"with {_pairedObjectsWithEventCount[i].Value.ToString()} events.\n";
            }

            Debug.Log(message);
        }
    ```

9.  Fügen Sie die Klassenstruktur hinzu, die zum Deserialisieren des JSON-Objekts verwendet wird, das von *Application Insights* empfangen wird. Fügen Sie diese Klassen ganz unten in der **DataFromAnalytics-Klassendatei** **außerhalb** der Klassendefinition hinzu.

    ```csharp
        /// <summary>
        /// These classes represent the structure of the JSON response from Azure Insight
        /// </summary>
        [Serializable]
        public class Analytics
        {
            [JsonProperty("@odata.context")]
            public string OdataContext { get; set; }

            [JsonProperty("@odata.count")]
            public string OdataCount { get; set; }

            [JsonProperty("value")]
            public Value[] Value { get; set; }
        }

        [Serializable]
        public class Value
        {
            [JsonProperty("customMetric")]
            public CustomMetric CustomMetric { get; set; }
        }

        [Serializable]
        public class CustomMetric
        {
            [JsonProperty("name")]
            public string Name { get; set; }
        }
    ```

10. Speichern Sie ihre Änderungen in *Visual Studio,* bevor Sie zu *Unity* zurückkehren.

## <a name="chapter-10---create-the-movement-class"></a>Kapitel 10 : Erstellen der Movement-Klasse

Das **Movement-Skript** ist das nächste Skript, das Sie erstellen müssen. IISConfigurator ist für Folgendes zuständig:

- Bewegen der Hauptkamera entsprechend der Richtung, in die die Kamera blickt.
- Hinzufügen aller anderen Skripts zu Szenenobjekten.

So erstellen Sie das Skript:

1.  Doppelklicken Sie auf den **Ordner Skripts,** um ihn zu öffnen.

2.  Klicken Sie mit der rechten Maustaste in **den Ordner Skripts,** und klicken **Sie auf**  >  **C#-Skript erstellen.** Nennen Sie das Skript **Movement**.

3.  Doppelklicken Sie auf das Skript, um es mit *dem* Visual Studio.

4.  Ersetzen Sie den vorhandenen Code durch folgenden Code:

    ```csharp
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;

        public class Movement : MonoBehaviour
        {
            /// <summary>
            /// The rendered object representing the right controller.
            /// </summary>
            public GameObject Controller;

            /// <summary>
            /// The movement speed of the user.
            /// </summary>
            public float UserSpeed;

            /// <summary>
            /// Provides whether source updates have been registered.
            /// </summary>
            private bool _isAttached = false;

            /// <summary>
            /// The chosen controller hand to use. 
            /// </summary>
            private InteractionSourceHandedness _handness = InteractionSourceHandedness.Right;

            /// <summary>
            /// Used to calculate and proposes movement translation.
            /// </summary>
            private Vector3 _playerMovementTranslation;

            private void Start()
            {
                // You are now adding components dynamically 
                // to ensure they are existing on the correct object  

                // Add all camera related scripts to the camera. 
                Camera.main.gameObject.AddComponent<Gaze>();
                Camera.main.gameObject.AddComponent<ObjectTrigger>();
        
                // Add all other scripts to this object.
                gameObject.AddComponent<ApplicationInsightsTracker>();
                gameObject.AddComponent<DataFromAnalytics>();
            }

            // Update is called once per frame
            void Update()
            {
            
            }
        }
    ```

5.  Fügen Sie innerhalb  **der Movement-Klasse** unterhalb der leeren **Update()-Methode** die folgenden Methoden ein, die es dem Benutzer ermöglichen, den Handcontroller zum Verschieben im virtuellen Raum zu verwenden:

    ```csharp
        /// <summary>
        /// Used for tracking the current position and rotation of the controller.
        /// </summary>
        private void UpdateControllerState()
        {
    #if UNITY_WSA && UNITY_2017_2_OR_NEWER
            // Check for current connected controllers, only if WSA.
            string message = string.Empty;

            if (InteractionManager.GetCurrentReading().Length > 0)
            {
                foreach (var sourceState in InteractionManager.GetCurrentReading())
                {
                    if (sourceState.source.kind == InteractionSourceKind.Controller && sourceState.source.handedness == _handness)
                    {
                        // If a controller source is found, which matches the selected handness, 
                        // check whether interaction source updated events have been registered. 
                        if (_isAttached == false)
                        {
                            // Register events, as not yet registered.
                            message = "<color=green>Source Found: Registering Controller Source Events</color>";
                            _isAttached = true;

                            InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
                        }

                        // Update the position and rotation information for the controller.
                        Vector3 newPosition;
                        if (sourceState.sourcePose.TryGetPosition(out newPosition, InteractionSourceNode.Pointer) && ValidPosition(newPosition))
                        {
                            Controller.transform.localPosition = newPosition;
                        }

                        Quaternion newRotation;

                        if (sourceState.sourcePose.TryGetRotation(out newRotation, InteractionSourceNode.Pointer) && ValidRotation(newRotation))
                        {
                            Controller.transform.localRotation = newRotation;
                        }
                    }
                }
            }
            else
            {
                // Controller source not detected. 
                message = "<color=blue>Trying to detect controller source</color>";

                if (_isAttached == true)
                {
                    // A source was previously connected, however, has been lost. Disconnected
                    // all registered events. 

                    _isAttached = false;

                    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;

                    message = "<color=red>Source Lost: Detaching Controller Source Events</color>";
                }
            }

            if(message != string.Empty)
            {
                Debug.Log(message);
            }
    #endif
        }
    ```

    ```csharp
        /// <summary>
        /// This registered event is triggered when a source state has been updated.
        /// </summary>
        /// <param name="obj"></param>
        private void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
        {
            if (obj.state.source.handedness == _handness)
            {
                if(obj.state.thumbstickPosition.magnitude > 0.2f)
                {
                    float thumbstickY = obj.state.thumbstickPosition.y;

                    // Vertical Input.
                    if (thumbstickY > 0.3f || thumbstickY < -0.3f)
                    {
                        _playerMovementTranslation = Camera.main.transform.forward;
                        _playerMovementTranslation.y = 0;
                        transform.Translate(_playerMovementTranslation * UserSpeed * Time.deltaTime * thumbstickY, Space.World);
                    }
                }
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Check that controller position is valid. 
        /// </summary>
        /// <param name="inputVector3">The Vector3 to check</param>
        /// <returns>The position is valid</returns>
        private bool ValidPosition(Vector3 inputVector3)
        {
            return !float.IsNaN(inputVector3.x) && !float.IsNaN(inputVector3.y) && !float.IsNaN(inputVector3.z) && !float.IsInfinity(inputVector3.x) && !float.IsInfinity(inputVector3.y) && !float.IsInfinity(inputVector3.z);
        }

        /// <summary>
        /// Check that controller rotation is valid. 
        /// </summary>
        /// <param name="inputQuaternion">The Quaternion to check</param>
        /// <returns>The rotation is valid</returns>
        private bool ValidRotation(Quaternion inputQuaternion)
        {
            return !float.IsNaN(inputQuaternion.x) && !float.IsNaN(inputQuaternion.y) && !float.IsNaN(inputQuaternion.z) && !float.IsNaN(inputQuaternion.w) && !float.IsInfinity(inputQuaternion.x) && !float.IsInfinity(inputQuaternion.y) && !float.IsInfinity(inputQuaternion.z) && !float.IsInfinity(inputQuaternion.w);
        }   
    ```

6.  Fügen Sie abschließend den Methodenaufruf in der **Update()-Methode** hinzu.

    ```csharp
        // Update is called once per frame
        void Update()
        {
            UpdateControllerState();
        }
    ```

7.  Stellen Sie sicher, dass Sie Ihre Änderungen *in* Visual Studio speichern, bevor Sie zu *Unity zurückkehren.*

## <a name="chapter-11---setting-up-the-scripts-references"></a>Kapitel 11: Einrichten der Skriptverweise

In diesem Kapitel müssen  Sie das Bewegungsskript auf dem übergeordneten **Kamera-Element** platzieren und seine Verweisziele festlegen. Dieses Skript verarbeitet dann das Platzieren der anderen Skripts, wo sie benötigt werden.

1.  Ziehen Sie aus dem Ordner **Skripts** *im* Project-Bereich das Bewegungsskript auf das übergeordnete **Camera-Objekt,** das sich im  *Hierarchiebereich befindet.*

    ![Einrichten der Skriptverweise in der Unity-Szene](images/AzureLabs-Lab309-48.png)

2.  Klicken Sie auf die **übergeordnete Kamera.** Ziehen Sie *im Hierarchiebereich* das Rechte Objekt aus dem *Hierarchiebereich* auf das Verweisziel **Controller** im  *Inspektorbereich.* Legen Sie **die Benutzergeschwindigkeit** auf **5** fest, wie in der folgenden Abbildung dargestellt.

    ![Einrichten der Skriptverweise in der Unity-Szene](images/AzureLabs-Lab309-49.png)

## <a name="chapter-12---build-the-unity-project"></a>Kapitel 12: Erstellen des Unity-Projekts

Alles, was für den Unity-Abschnitt dieses Projekts erforderlich ist, wurde abgeschlossen, daher ist es an der Zeit, es aus Unity zu erstellen.

1.  Navigieren Sie **zu Build Einstellungen**, (**File**  >  **Build Einstellungen**).

2.  Klicken Sie **im Fenster Build Einstellungen** auf **Erstellen.**

    ![Erstellen der Unity-Project zu UWP-Projektmappe](images/AzureLabs-Lab309-50.png)

3.  Ein **Datei-Explorer-Fenster** wird angezeigt, in dem Sie zur Eingabe eines Speicherorts für den Build aufgefordert werden. Erstellen Sie einen neuen Ordner (indem Sie **oben** links auf Neuer Ordner klicken), und nennen Sie ihn **BUILDS**.

    ![Erstellen der Unity-Project zu UWP-Projektmappe](images/AzureLabs-Lab309-51.png)

    1.  Öffnen Sie den neuen **Ordner BUILDS,** erstellen Sie einen weiteren Ordner (verwenden Sie erneut **Neuer** Ordner), und nennen Sie ihn **MR Azure Application \_ \_ \_ Insights**.

        ![Erstellen der Unity-Project zu UWP-Projektmappe](images/AzureLabs-Lab309-52.png)

    2.  Wenn Sie den **Ordner MR Azure Application \_ \_ \_ Insights** ausgewählt haben, klicken Sie **auf Ordner auswählen.** Die Erstellung des Projekts nimmt eine Minute in Dauern.

4.  Nach *dem Build* wird der **Datei-Explorer** mit dem Speicherort Des neuen Projekts angezeigt.

## <a name="chapter-13---deploy-mr_azure_application_insights-app-to-your-machine"></a>Kapitel 13: Bereitstellen MR_Azure_Application_Insights-App auf Ihrem Computer

So stellen Sie die **MR \_ Azure Application \_ \_ Insights-App** auf Ihrem lokalen Computer zur Bereitstellung:

1.  Öffnen Sie die Projektmappendatei Ihrer **MR \_ Azure Application \_ \_ Insights-App** in **Visual Studio.**

2.  Wählen Sie **auf der Projektmappenplattform** **x86, Lokaler Computer aus.**

3.  Wählen Sie in **der Projektmappenkonfiguration** **Debuggen aus.**

    ![Erstellen der Unity-Project zu UWP-Projektmappe](images/AzureLabs-Lab309-53.png)

4.  Wechseln Sie zum **Menü Erstellen,** und klicken Sie **auf Projektmappe bereitstellen,** um die Anwendung auf Ihren Computer zu laden.

5.  Ihre App sollte nun in der Liste der installierten Apps angezeigt werden, die zum Start bereit sind.

6. Starten Sie die Mixed Reality-Anwendung.

7. Bewegen Sie sich in der Szene, nähern Sie sich Objekten, und sehen Sie sich diese an. Wenn *der Azure Insight Service* genügend Ereignisdaten gesammelt hat, wird das Objekt, das am meisten an den Anfang gesetzt wurde, auf Grün festgelegt.

> [!IMPORTANT] 
> Während die durchschnittliche  Wartezeit für die vom Dienst zu sammelnden Ereignisse und Metriken etwa 15 Minuten dauert, kann es in einigen Fällen bis zu 1 Stunde dauern.

## <a name="chapter-14---the-application-insights-service-portal"></a>Kapitel 14: Das Application Insights Service-Portal

Nachdem Sie die Szene umstreift und mehrere Objekte anviert haben, können Sie die im Application *Insights Service-Portal gesammelten Daten* sehen.

1.  Wechseln Sie zurück zu Ihrem Application Insights Service-Portal.

2.  Klicken Sie *auf Metrik-Explorer*.

    ![Blick auf gesammelte Daten](images/AzureLabs-Lab309-54.png)

3.  Es wird auf einer Registerkarte mit dem Diagramm geöffnet, das die Mit Ihrer Anwendung *verbundenen* Ereignisse und Metriken enthält. Wie bereits erwähnt, kann es einige Zeit (bis zu 1 Stunde) dauern, bis die Daten im Diagramm angezeigt werden.

    ![Blick auf gesammelte Daten](images/AzureLabs-Lab309-55.png)

4.  Klicken Sie in der  *Gesamtanzahl der* Ereignisse nach Anwendungsversion auf die Leiste Ereignisse, um eine detaillierte Aufschlüsselung der Ereignisse mit ihren Namen zu erhalten.

    ![Blick auf gesammelte Daten](images/AzureLabs-Lab309-56.png)

## <a name="your-finished-your-application-insights-service-application"></a>Ihre Anwendung "Application Insights Service" wurde abgeschlossen.

Herzlichen Glückwunsch! Sie haben eine Mixed Reality-App erstellt, die den Application Insights Service nutzt, um die Aktivität des Benutzers in Ihrer App zu überwachen.

![Kursergebnis](images/AzureLabs-Lab309-00.png)

## <a name="bonus-exercises"></a>Bonusübungen

**Übung 1**

Versuchen Sie, die ObjectInScene-Objekte zu erzeugen, anstatt sie manuell zu erstellen, und legen Sie ihre Koordinaten auf der Ebene in Ihren Skripts fest. Auf diese Weise könnten Sie Azure fragen, was das am häufigsten verwendete Objekt war (entweder aus Anvitäts- oder Näherungsergebnissen) und ein zusätzliches *dieser* Objekte erstellen.

**Übung 2**

Sortieren Sie ihre Insights ergebnisse nach Zeit, damit Sie die relevantesten Daten erhalten, und implementieren Sie diese zeitsensiblen Daten in Ihrer Anwendung.