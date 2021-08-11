---
title: 'HoloLens (1. Generation) und Azure 301: Sprachübersetzung'
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie die Azure Translator Text-API in einer Mixed Reality-Anwendung implementieren.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, Tutorial, API, Textübersetzung, HoloLens, immersive, VR, Sprachübersetzung, Windows 10, Visual Studio
ms.openlocfilehash: 8eeeab45c6e7d93c1b04afa4db811f220b0c2f9c85400fc93a81ac413164a6b7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115229590"
---
# <a name="hololens-1st-gen-and-azure-301-language-translation"></a>HoloLens (1. Generation) und Azure 301: Sprachübersetzung

<br>

>[!NOTE]
>Die Tutorials der Mixed Reality Academy wurden im Hinblick auf HoloLens (1. Gen.) und immersive Mixed Reality-Headsets entworfen.  Daher halten wir es für wichtig, diese Tutorials für Entwickler verfügbar zu halten, die noch nach Anleitung beim Entwickeln für diese Geräte suchen.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für HoloLens 2 verwendet werden.  Sie werden gewartet, um weiterhin auf den unterstützten Geräten zu funktionieren. Es wird eine neue Reihe von Tutorials geben, die in Zukunft veröffentlicht werden, die veranschaulichen, wie sie für HoloLens 2 entwickelt werden.  Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn sie veröffentlicht werden.

<br>

In diesem Kurs erfahren Sie, wie Sie einer Mixed Reality-Anwendung mithilfe von Azure Cognitive Services mit der Translator Text-API Übersetzungsfunktionen hinzufügen.

![Endgültiges Produkt](images/AzureLabs-Lab1-00.png)

Die Translator Text-API ist ein Übersetzungsdienst, der nahezu in Echtzeit funktioniert. Der Dienst ist cloudbasiert, und mithilfe eines REST-API-Aufrufs kann eine App die neuronale maschinelle Übersetzungstechnologie nutzen, um Text in eine andere Sprache zu übersetzen. Weitere Informationen finden Sie auf der [Seite azure Translator Text-API.](https://azure.microsoft.com/services/cognitive-services/translator-text-api/)

Nach Abschluss dieses Kurses verfügen Sie über eine Mixed Reality-Anwendung, die folgende Schritte ausführen kann:

1.  Der Benutzer spricht in ein Mikrofon, das mit einem immersiven (VR)-Headset (oder dem integrierten Mikrofon von HoloLens) verbunden ist.
2.  Die App erfasst das Diktat und sendet es an die Azure Translator Text-API.
3.  Das Übersetzungsergebnis wird in einer einfachen Benutzeroberflächengruppe in der Unity-Szene angezeigt.

In diesem Kurs erfahren Sie, wie Sie die Ergebnisse des Translator-Diensts in eine Unity-basierte Beispielanwendung integrieren. Sie müssen diese Konzepte auf eine benutzerdefinierte Anwendung anwenden, die Sie möglicherweise erstellen.

## <a name="device-support"></a>Geräteunterstützung

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td> MR und Azure 301: Sprachübersetzung</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Während sich dieser Kurs hauptsächlich auf Windows Mixed Reality immersiven Headsets (VR) konzentriert, können Sie auch das, was Sie in diesem Kurs lernen, auf Microsoft HoloLens anwenden. Während Sie den Kurs durchgehen, werden Ihnen Hinweise zu allen Änderungen angezeigt, die Sie ggf. zur Unterstützung HoloLens verwenden müssen. Wenn Sie HoloLens verwenden, können Sie während der Spracherfassung ein Echo bemerken.

## <a name="prerequisites"></a>Voraussetzungen

> [!NOTE]
> Dieses Tutorial richtet sich an Entwickler, die grundlegende Erfahrung mit Unity und C# haben. Beachten Sie auch, dass die Voraussetzungen und die geschriebenen Anweisungen in diesem Dokument darstellen, was zum Zeitpunkt der Erstellung (Mai 2018) getestet und überprüft wurde. Sie können die neueste Software verwenden, wie im Artikel [installieren der Tools](../../install-the-tools.md) aufgeführt. Es sollte jedoch nicht davon ausgegangen werden, dass die Informationen in diesem Kurs perfekt mit dem übereinstimmen, was Sie in neuerer Software finden als die unten aufgeführten.

Für diesen Kurs wird die folgende Hardware und Software empfohlen:

- Ein Entwicklungs-PC, [der mit Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) für die Entwicklung immersiver Headsets (VR) kompatibel ist
- [Windows 10 Fall Creators Update (oder höher) mit aktivierter Option "Entwicklermodus"](../../install-the-tools.md#installation-checklist)
- [Das neueste Windows 10 SDK](../../install-the-tools.md#installation-checklist)
- [Unity 2017.4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- Ein [Windows Mixed Reality immersives Headset (VR)](../../../discover/immersive-headset-hardware-details.md) oder [ein Microsoft HoloLens](/hololens/hololens1-hardware) mit aktiviertem Entwicklermodus
- Eine Reihe von Mikrofonen mit einem integrierten Mikrofon (wenn das Headset nicht über ein integriertes Mikrofon und Lautsprecher verfügt)
- Internetzugriff für Azure-Setup und -Übersetzungsabruf

## <a name="before-you-start"></a>Vorbereitung

- Um Probleme bei der Erstellung dieses Projekts zu vermeiden, wird dringend empfohlen, das in diesem Tutorial erwähnte Projekt in einem Stammordner oder in einem Ordner in der Nähe des Stammordners zu erstellen (lange Ordnerpfade können zur Buildzeit Probleme verursachen).
- Mit dem Code in diesem Tutorial können Sie von dem Standard-Mikrofongerät aufzeichnen, das mit Ihrem PC verbunden ist. Stellen Sie sicher, dass das Standardmäßige Mikrofongerät auf das Gerät festgelegt ist, das Sie zum Erfassen Ihrer Stimme verwenden möchten.
- Damit Ihr PC das Diktieren aktivieren kann, wechseln Sie zu **Einstellungen > Privacy > Speech, öffnen Sie & eingaben,** und wählen Sie die Schaltfläche **Sprachdienste aktivieren und Vorschläge eingeben** aus.
- Wenn Sie ein Mikrofon verwenden und mit Ihrem Headset verbunden sind (oder mit diesem integriert sind), stellen Sie sicher, dass die Option "Wenn ich mein Headset trägt, zum Headset-Mikrofon wechseln" in **Einstellungen > Mixed Reality > Audio und Sprache** aktiviert ist.

   ![Mixed Reality-Einstellungen](images/AzureLabs-Lab1-00-5.png)

   ![Mikrofoneinstellung](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> Beachten Sie, dass bei der Entwicklung für ein immersives Headset für dieses Lab möglicherweise Probleme mit dem Audioausgabegerät auftreten. Dies ist auf ein Problem mit Unity zurückzuführen, das in späteren Versionen von Unity (Unity 2018.2) behoben wurde. Das Problem verhindert, dass Unity das Standardaudioausgabegerät zur Laufzeit ändert. Um dieses Problem zu umgehen, stellen Sie sicher, dass Sie die oben genannten Schritte ausgeführt haben, und schließen Sie den Editor, und öffnen Sie den Editor erneut, wenn dieses Problem angezeigt wird.

## <a name="chapter-1--the-azure-portal"></a>Kapitel 1: Das Azure-Portal

Um die Azure Translator-API zu verwenden, müssen Sie eine Instanz des Diensts so konfigurieren, dass sie Ihrer Anwendung zur Verfügung gestellt wird.

1.  Melden Sie sich beim  [Azure-Portal](https://portal.azure.com)an.

    > [!NOTE]
    > Wenn Sie noch nicht über ein Azure-Konto verfügen, müssen Sie eins erstellen. Wenn Sie dieses Tutorial in einer Classroom- oder Lab-Situation durchgehen, bitten Sie Ihren Dozenten oder einen der Proctors um Hilfe beim Einrichten Ihres neuen Kontos.

2.  Klicken Sie nach der Anmeldung oben links auf **Neu,** und suchen Sie nach "Translator Text-API". Drücken Sie die **EINGABETASTE**.

    ![Neue Ressource](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > Das Wort **Neu** wurde möglicherweise in neueren Portalen durch **Ressource erstellen** ersetzt.

3.  Die neue Seite enthält eine Beschreibung des *Translator Text-API-Diensts.* Wählen Sie unten links auf dieser Seite die Schaltfläche **Erstellen** aus, um eine Zuordnung zu diesem Dienst zu erstellen.

    ![Erstellen Translator Text-API-Diensts](images/AzureLabs-Lab1-03.png)

4.  Nachdem Sie auf **Erstellen** geklickt haben:

    1. Fügen Sie den gewünschten **Namen** für diese Dienstinstanz ein.
    2. Wählen Sie ein **geeignetes Abonnement aus.**
    3. Wählen Sie den für Sie geeigneten **Tarif** aus. Wenn Sie zum ersten Mal einen *Translator Textdienst* erstellen, sollte Ihnen ein kostenloser Tarif (mit dem Namen F0) zur Verfügung stehen.
    4. Wählen Sie eine **Ressourcengruppe** aus, oder erstellen Sie eine neue. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, Steuern des Zugriffs, Bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt zugeordnet sind (z. B. diese Labs), in einer gemeinsamen Ressourcengruppe zu speichern.

        > Weitere Informationen zu Azure-Ressourcengruppen finden Sie [im Artikel zu Ressourcengruppen.](/azure/azure-resource-manager/resource-group-portal)

    5. Bestimmen Sie den **Speicherort** für Ihre Ressourcengruppe (wenn Sie eine neue Ressourcengruppe erstellen). Der Standort befindet sich idealerweise in der Region, in der die Anwendung ausgeführt wird. Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.
    6. Sie müssen auch bestätigen, dass Sie die für diesen Dienst geltenden Geschäftsbedingungen verstanden haben.
    7. Klicken Sie auf **Erstellen**.

        ![Klicken Sie auf die Schaltfläche Erstellen.](images/AzureLabs-Lab1-04.png)

5.  Nachdem Sie auf **Erstellen** geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. Dies kann eine Minute dauern.
6.  Sobald die Dienstinstanz erstellt wurde, wird eine Benachrichtigung im Portal angezeigt. 

    ![Benachrichtigung zur Azure-Diensterstellung](images/AzureLabs-Lab1-05.png)

7.  Klicken Sie auf die Benachrichtigung, um Ihre neue Dienstinstanz zu untersuchen. 

    ![Wechseln Sie zum Ressourcen-Popupfenster.](images/AzureLabs-Lab1-06.png)

8.  Klicken Sie in der Benachrichtigung auf die Schaltfläche **Zu Ressource** wechseln, um Ihre neue Dienstinstanz zu untersuchen. Sie gelangen zu Ihrer neuen Translator Text-API-Dienstinstanz. 

    ![Translator Seite "Text-API-Dienst"](images/AzureLabs-Lab1-07.png)

9.  In diesem Tutorial muss Ihre Anwendung Aufrufe an Ihren Dienst tätigen. Dies erfolgt über die Verwendung des Abonnementschlüssels Ihres Diensts. 
10. Navigieren Sie auf der *Schnellstartseite* Ihres *Translator-Textdiensts* zum ersten Schritt, Greifen Sie *Ihre Schlüssel,* und klicken Sie auf **Schlüssel** ( Sie können dies auch erreichen, indem Sie auf den blauen Link Schlüssel klicken, der sich im Navigationsmenü Dienste befindet, der durch das Schlüsselsymbol gekennzeichnet ist). Dadurch werden Ihre *Dienstschlüssel angezeigt.*
11. Erstellen Sie eine Kopie eines der angezeigten Schlüssel, da Sie diese später in Ihrem Projekt benötigen. 

## <a name="chapter-2--set-up-the-unity-project"></a>Kapitel 2: Einrichten des Unity-Projekts

Richten Sie Ihr immersives Mixed Reality-Headset ein, und testen Sie es.

> [!NOTE]
> Für diesen Kurs benötigen Sie keine Motion-Controller. Wenn Sie Unterstützung beim Einrichten eines immersiven Headsets benötigen, führen Sie [die folgenden Schritte aus.](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)

Im Folgenden finden Sie eine typische Einrichtung für die Entwicklung mit Mixed Reality und als solche eine gute Vorlage für andere Projekte:

1.  Öffnen Sie *Unity,* und klicken Sie auf **Neu.** 

    ![Starten Sie ein neues Unity-Projekt.](images/AzureLabs-Lab1-08.png)

2.  Sie müssen nun einen Unity-Project angeben. Fügen **Sie MR_Translation** ein. Stellen Sie sicher, dass der Projekttyp auf **3D festgelegt ist.** Legen Sie *den Speicherort* auf einen für Sie geeigneten Speicherort fest (denken Sie daran, dass die Nähe zu Stammverzeichnissen besser ist). Klicken Sie dann auf **Projekt erstellen.**

    ![Geben Sie Details für das neue Unity-Projekt an.](images/AzureLabs-Lab1-09.png)

3.  Wenn Unity geöffnet ist, sollte überprüft werden, ob der **Standardskript-Editor** auf **Visual Studio.** Wechseln Sie **zu > Bearbeiten,** und navigieren Sie dann im neuen Fenster zu **Externe Tools.** Ändern **Sie den editor für externe** **Skripts in Visual Studio 2017**. Schließen Sie das **Fenster Einstellungen.**

    ![Skript-Editor-Einstellung aktualisieren.](images/AzureLabs-Lab1-10.png)

4.  Wechseln Sie als Nächstes zu **Datei > Build Einstellungen** und wechseln Sie zur **universellen Windows-Plattform,** indem Sie auf **die Schaltfläche Plattform wechseln** klicken.

    ![Erstellen Einstellungen Fensters, Wechseln der Plattform zu UWP.](images/AzureLabs-Lab1-11.png)

5.  Wechseln Sie **zu Datei > Build Einstellungen,** und stellen Sie Sicher, dass:

    1. **Das Zielgerät** ist auf Any **Device (Beliebiges Gerät) festgelegt.**

        > Legen Microsoft HoloLens Zielgerät **auf** *HoloLens.*

    2. **Buildtyp** ist auf **D3D festgelegt**
    3. **SDK** ist auf **Latest installed (Neueste installiert) festgelegt.**
    4. **Visual Studio version** ist auf **Latest installed (Neueste installiert) festgelegt.**
    5. **Erstellen und Ausführen** ist auf Lokaler **Computer festgelegt.**
    6. Speichern Sie die Szene, und fügen Sie sie dem Build hinzu.

        1. Wählen Sie hierzu Geöffnete Szenen **hinzufügen aus.** Ein Speicherfenster wird angezeigt.

            ![Klicken Sie auf die Schaltfläche "Geöffnete Szenen hinzufügen".](images/AzureLabs-Lab1-12.png)

        2. Erstellen Sie einen neuen Ordner für diesen und jede  zukünftige Szene, und wählen Sie dann die Schaltfläche Neuer Ordner aus, um einen neuen Ordner zu erstellen, und nennen Sie **ihn Scenes**.

            ![Erstellen eines neuen Skriptordners](images/AzureLabs-Lab1-13.png)

        3. Öffnen Sie den neu erstellten **Ordner Scenes,** und geben Sie dann im Feld Dateiname *:* text MR_TranslationScene **ein,** und klicken Sie dann **auf Speichern.**

            ![Benennen Sie die neue Szene.](images/AzureLabs-Lab1-14.png)

            > Beachten Sie, dass Sie Ihre Unity-Szenen im Ordner *Assets* speichern müssen, da sie dem Unity-Project. Das Erstellen des Szenenordners (und anderer ähnlicher Ordner) ist eine typische Methode zum Strukturieren eines Unity-Projekts.

    7. Die restlichen Einstellungen in *Build Einstellungen* sollten vorerde als Standardeinstellung bef bleiben.

6. Klicken Sie *im Fenster Build Einstellungen* auf die Schaltfläche Player **Einstellungen,** um den entsprechenden Bereich in dem Bereich zu öffnen, in dem sich der *Inspektor* befindet. 

    ![Öffnen Sie die Playereinstellungen.](images/AzureLabs-Lab1-15.png)

7. In diesem Bereich müssen einige Einstellungen überprüft werden:

    1. Führen Sie **auf Einstellungen** Registerkarte Andere Optionen aus:

        1. **Die Skriptlaufzeitversion** sollte **stabil** sein (.NET 3.5-Entsprechung).
        2. **Das Skript-Back-End** sollte **.NET sein.**
        3. **Der API-Kompatibilitätsgrad** sollte **.NET 4.6 sein.**

            ![Aktualisieren Sie andere Einstellungen.](images/AzureLabs-Lab1-16.png)
      
    2. Aktivieren Sie **auf Einstellungen** Registerkarte Publishing Einstellungen unter **Capabilities (Funktionen)** die folgenden Optionen:

        1. **InternetClient**
        2. **Mikrofon**

            ![Aktualisieren der Veröffentlichungseinstellungen.](images/AzureLabs-Lab1-17.png)

    3. Aktivieren Sie weiter unten im Bereich in **XR Einstellungen** (unter Publish **Einstellungen)** **(Virtual Reality** unterstützt), und stellen Sie sicher, dass das Windows Mixed Reality **SDK** hinzugefügt wird.

        ![Aktualisieren Sie die X R-Einstellungen.](images/AzureLabs-Lab1-18.png)

8.  Im **Build-Einstellungen** ist *Unity C#-Projekte* nicht mehr ausgegraut. aktivieren Sie das Kontrollkästchen daneben. 
9.  Schließen Sie das Fenster „Build Settings“ (Buildeinstellungen).
10. Speichern Sie Ihre Szene und Project (**FILE > SAVE SCENE/FILE > SAVE PROJECT**).

## <a name="chapter-3--main-camera-setup"></a>Kapitel 3 : Einrichtung der Hauptkamera

> [!IMPORTANT]
> Wenn Sie die Unity Set *up-Komponente* dieses Kurses überspringen und direkt mit dem Code fortfahren möchten, können [](https://docs.unity3d.com/Manual/AssetPackages.html)Sie dieses [UNITYPACKAGE](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage)herunterladen, als benutzerdefiniertes Paket in Ihr Projekt importieren und dann aus Kapitel [5](#chapter-5--create-the-results-class)fortfahren. Sie müssen weiterhin eine Unity-Project.

1.  Im *Hierarchiebereich finden* Sie ein Objekt namens **Hauptkamera.** Dieses Objekt stellt Ihren "Kopfpunkt" dar, sobald Sie sich in Ihrer Anwendung befinden.
2.  Wählen Sie vor dem Unity-Dashboard das **GameObject Hauptkamera aus.** Sie werden feststellen, dass der Inspektorbereich *(im* Allgemeinen auf der rechten Seite im Dashboard) die verschiedenen Komponenten dieses *GameObject* zeigt, mit *Transformation* oben, gefolgt von *Camera* und einigen anderen Komponenten. Sie müssen die Transformation der Hauptkamera zurücksetzen, damit sie richtig positioniert ist.
3.  Wählen Sie hierzu das Zahnradsymbol neben  der Komponente Transformieren der Kamera aus, und wählen Sie **Zurücksetzen aus.**  

    ![Setzen Sie die Hauptkameratransformation zurück.](images/AzureLabs-Lab1-19.png)
 
4.  Die *Transformationskomponente* sollte dann wie die folgenden aussehen:

    1. Die *Position* ist auf **0, 0, 0 festgelegt.**
    2. *Die Drehung* ist **auf 0, 0, 0 festgelegt.**
    3. Die *Skalierung* ist auf **1, 1, 1 festgelegt.**

        ![Transformieren von Informationen für die Kamera](images/AzureLabs-Lab1-20.png)

5.  Wenn Sie als Nächstes das **Objekt Hauptkamera** ausgewählt haben, sehen Sie sich die Schaltfläche **Add Component** (Komponente hinzufügen) ganz unten im *Inspektorbereich an.* 
6.  Wählen Sie diese Schaltfläche aus, und suchen Sie (indem Sie entweder *Audioquelle* in das Suchfeld eingeben oder in den Abschnitten navigieren) nach der Komponente **Audioquelle,** wie unten dargestellt, und wählen Sie sie aus (drücken Sie die EINGABETASTE).
7.  Wie *unten gezeigt,* wird der Hauptkamera eine **Audioquelle-Komponente** hinzugefügt.

    ![Fügen Sie eine Audioquellenkomponente hinzu.](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > Für Microsoft HoloLens müssen Sie auch Folgendes ändern, die Teil der **Camera-Komponente** ihrer **Hauptkamera sind:**
    > - **Flags löschen:** Volltonfarbe.
    > - **Hintergrund** "Black, Alpha 0": Hexadezimale Farbe: #00000000.

## <a name="chapter-4--setup-debug-canvas"></a>Kapitel 4 – Einrichten des Debugbereichs

Um die Ein- und Ausgabe der Übersetzung anzuzeigen, muss eine einfache Benutzeroberfläche erstellt werden. In diesem Kurs erstellen Sie ein Canvas-Benutzeroberflächenobjekt mit mehreren Textobjekten, um die Daten anzuzeigen.

1.  Klicken Sie mit der rechten Maustaste in einen leeren Bereich des *Hierarchiebereichs,* und fügen Sie unter **der Benutzeroberfläche** einen **Zeichenbereich hinzu.**

    ![Fügen Sie ein neues Canvas-Benutzeroberflächenobjekt hinzu.](images/AzureLabs-Lab1-22.png)

2.  Ändern Sie bei ausgewähltem Canvas-Objekt im *Inspektorbereich* (innerhalb der Canvas-Komponente) den **Rendermodus in** **World Space**. 
3.  Ändern Sie als Nächstes die folgenden Parameter in der *Rect-Transformation des Inspektorbereichs:*

    1. *POS*  -   **X** 0 **Y** 0 **Z** 40
    2. *Breite:* 500
    3. *Höhe:* 300
    4. *Skalieren*  -  **X** 0.13 **Y** 0.13 **Z** 0.13

        ![Aktualisieren Sie die Rect-Transformation für den Zeichenbereich.](images/AzureLabs-Lab1-23.png)
 
4.  Klicken Sie im Hierarchiebereich **unter der** Benutzeroberfläche mit der rechten Maustaste auf die *Canvas,* **und** fügen Sie einen **Bereich hinzu.** Dieser **Bereich** stellt einen Hintergrund für den Text zur Verfügung, den Sie in der Szene anzeigen.
5.  Klicken Sie mit der rechten Maustaste **auf den** Bereich im *Hierarchiebereich* unter **der Benutzeroberfläche,** und fügen Sie ein **Textobjekt hinzu.** Wiederholen Sie den gleichen Vorgang, bis Sie insgesamt vier Textobjekte der Benutzeroberfläche erstellt haben (Hinweis: Wenn Sie das erste Textobjekt ausgewählt haben, können Sie einfach **"STRG" + "D"** drücken, um es zu duplizieren, bis sie insgesamt vier haben). 
6.  Wählen Sie **für jedes Textobjekt** dies aus, und verwenden Sie die folgenden Tabellen, um die Parameter im *Inspektorbereich zu festlegen.*

    1. Für die *Rect Transform-Komponente:*

        | Name                   | Transformieren – *Position*             | Breite      | Höhe    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | MicrophoneStatusLabel  | **X** -80 **Y** 90 **Z** 0         | 300        | 30        |
        | AzureResponseLabel     | **X** -80 **Y** 30 **Z** 0         | 300        | 30        |
        | DictationLabel         | **X** -80 **Y** -30 **Z** 0        | 300        | 30        |
        | TranslationResultLabel | **X** -80 **Y** -90 **Z** 0        | 300        | 30        |


    2. Für die **Komponente Text (Skript):**


        | Name                   | Text               | Schriftgrad    |
        |:----------------------:|:------------------:|:------------:|
        | MicrophoneStatusLabel  | Mikrofonstatus: | 20           |
        | AzureResponseLabel     | Azure-Webantwort | 20           |
        | DictationLabel         |   Sie haben soeben gesagt:   | 20           |
        | TranslationResultLabel |    Übersetzung:    | 20           |

        ![Geben Sie die entsprechenden Werte für die Benutzeroberflächenbezeichnungen ein.](images/AzureLabs-Lab1-24.png)

    3. Machen Sie außerdem den Schriftschnitt **fett formatiert.** Dies erleichtert das Lesen des Texts.

        ![Fett formatierte Schriftart.](images/AzureLabs-Lab1-25.png)

7.  Erstellen Sie für jedes in [Kapitel 5](#chapter-5--create-the-results-class)erstellte *Benutzeroberflächentextobjekt* ein neues *untergeordnetes* **Benutzeroberflächentextobjekt.** Diese untergeordneten Elemente zeigen die Ausgabe der Anwendung an. Erstellen Sie *untergeordnete* Objekte, indem Sie mit der rechten Maustaste auf das gewünschte übergeordnete Element klicken (z. B. *MicrophoneStatusLabel),* und wählen Sie dann **benutzeroberfläche** und dann **Text** aus.
8.  Wählen Sie sie für jedes dieser untergeordneten Elemente aus, und verwenden Sie die folgenden Tabellen, um die Parameter im Inspektorbereich festzulegen.

    1. Für die **Rect Transform-Komponente:**

        | Name                  | Transformieren – *Position* | Breite      | Höhe    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | MicrophoneStatusText  | X 0 Y -30 Z 0          | 300        | 30        |
        | AzureResponseText     | X 0 Y -30 Z 0          | 300        | 30        |
        | DictationText         | X 0 Y -30 Z 0          | 300        | 30        |
        | TranslationResultText | X 0 Y -30 Z 0          | 300        | 30        |

    2. Für die **Komponente Text (Skript):**

        | Name                  | Text          | Schriftgrad    |
        |:---------------------:|:-------------:|:------------:|
        | MicrophoneStatusText  |      ??       | 20           |
        | AzureResponseText     |      ??       | 20           |
        | DictationText         |      ??       | 20           |
        | TranslationResultText |      ??       | 20           |

9. Wählen Sie als Nächstes die Ausrichtungsoption "Center" für jede Textkomponente aus:

    ![Ausrichten von Text.](images/AzureLabs-Lab1-26.png)

10. Um sicherzustellen, dass die text-Objekte der **untergeordneten Benutzeroberfläche** leicht lesbar sind, ändern Sie ihre *Farbe*. Klicken Sie dazu auf die Leiste (derzeit "Schwarz") neben *Farbe*. 

    ![Geben Sie entsprechende Werte für die Benutzeroberflächentextausgaben ein.](images/AzureLabs-Lab1-27.png)
 
11. Ändern Sie dann im neuen *Fenster* Farbe die *Hexadezimalfarbe* in **0032EAFF.**

    ![Aktualisieren Sie die Farbe in Blau.](images/AzureLabs-Lab1-28.png)
 
12. Unten sehen Sie, wie die **Benutzeroberfläche** aussehen sollte.
    1.  Im *Hierarchiebereich:*

        ![Sie verfügen über eine Hierarchie in der bereitgestellten Struktur.](images/AzureLabs-Lab1-29.png)

    2.  In der *Szenen-* und *Spielansicht:*

        ![Weisen Sie die Szenen- und Spielansichten in der gleichen Struktur auf.](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a>Kapitel 5 – Erstellen der Results-Klasse

Das erste Skript, das Sie erstellen müssen, ist die *Results-Klasse,* die dafür verantwortlich ist, eine Möglichkeit zum Anzeigen der Ergebnisse der Übersetzung bereitzustellen. In der -Klasse wird Folgendes gespeichert und angezeigt: 

- Das Antwortergebnis von Azure.
- Der Mikrofonstatus. 
- Das Ergebnis des Diktats (Sprach-zu-Text).
- Das Ergebnis der Übersetzung.

So erstellen Sie diese Klasse: 

1.  Klicken Sie mit der rechten Maustaste in den *Project Bereich,* und **erstellen Sie dann > Ordner**. Nennen Sie den Ordner **Skripts**. 
 
    ![Erstellen Sie den Ordner skripts.](images/AzureLabs-Lab1-31.png)

    ![Öffnen Sie den Ordner scripts.](images/AzureLabs-Lab1-32.png)
 
2.  Doppelklicken Sie beim Erstellen des **Ordners Scripts** darauf, um ihn zu öffnen. Klicken Sie dann in diesem Ordner mit der rechten Maustaste, und wählen **Sie erstellen >** dann **C#-Skript** aus. Nennen Sie das Skript *Ergebnisse*. 

    ![Erstellen Sie das erste Skript.](images/AzureLabs-Lab1-33.png)
 
3.  Doppelklicken Sie auf das neue *Ergebnisskript,* um es mit **Visual Studio** zu öffnen.
4.  Fügen Sie die folgenden Namespaces ein:

    ```cs
        using UnityEngine;
        using UnityEngine.UI;
    ```

5.  Fügen Sie in der Klasse die folgenden Variablen ein:

    ```cs
        public static Results instance;
   
        [HideInInspector] 
        public string azureResponseCode;
   
        [HideInInspector] 
        public string translationResult;
   
        [HideInInspector] 
        public string dictationResult;
   
        [HideInInspector] 
        public string micStatus;
   
        public Text microphoneStatusText;
   
        public Text azureResponseText;
   
        public Text dictationText;
   
        public Text translationResultText;
    ```

6.  Fügen Sie dann die *"Awake()"-Methode* hinzu, die aufgerufen wird, wenn die Klasse initialisiert wird. 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  Fügen Sie abschließend die Methoden hinzu, die für die Ausgabe der verschiedenen Ergebnisinformationen auf der Benutzeroberfläche verantwortlich sind. 

    ```csharp
        /// <summary>
        /// Stores the Azure response value in the static instance of Result class.
        /// </summary>
        public void SetAzureResponse(string result)
        {
            azureResponseCode = result;
            azureResponseText.text = azureResponseCode;
        }
   
        /// <summary>
        /// Stores the translated result from dictation in the static instance of Result class. 
        /// </summary>
        public void SetDictationResult(string result)
        {
            dictationResult = result;
            dictationText.text = dictationResult;
        }
   
        /// <summary>
        /// Stores the translated result from Azure Service in the static instance of Result class. 
        /// </summary>
        public void SetTranslatedResult(string result)
        {
            translationResult = result;
            translationResultText.text = translationResult;
        }
   
        /// <summary>
        /// Stores the status of the Microphone in the static instance of Result class. 
        /// </summary>
        public void SetMicrophoneStatus(string result)
        {
            micStatus = result;
            microphoneStatusText.text = micStatus;
        }
    ```

8.  Speichern Sie Ihre Änderungen in *Visual Studio,* bevor Sie zu *Unity* zurückkehren.

## <a name="chapter-6--create-the-microphonemanager-class"></a>Kapitel 6 – Erstellen der *MicrophoneManager-Klasse*

Die zweite Klasse, die Sie erstellen, ist *der MicrophoneManager.*

Diese Klasse ist für Folgendes verantwortlich:

- Erkennen des Aufzeichnungsgeräts, das an das Headset oder den Computer angeschlossen ist (je nachdem, was die Standardeinstellung ist).
- Erfassen Sie das Audio (Sprache), und verwenden Sie das Diktat, um es als Zeichenfolge zu speichern.
- Sobald die Stimme angehalten wurde, übermitteln Sie das Diktat an die Translator Klasse.
- Hosten Sie eine Methode, die die Spracherfassung bei Wunsch beenden kann.

So erstellen Sie diese Klasse: 
1.  Doppelklicken Sie auf den **Ordner Skripts,** um ihn zu öffnen. 
2.  Klicken Sie mit der rechten Maustaste in **den Ordner Skripts,** und klicken Sie **> C#-Skript erstellen.** Nennen Sie das *Skript MicrophoneManager*. 
3.  Doppelklicken Sie auf das neue Skript, um es mit dem Visual Studio.
4.  Aktualisieren Sie die Namespaces so, dass sie am Anfang der *MicrophoneManager-Klasse* mit den folgenden identisch sind:

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  Fügen Sie dann die folgenden Variablen in der *MicrophoneManager-Klasse* hinzu:

    ```csharp
        // Help to access instance of this object 
        public static MicrophoneManager instance; 
     
        // AudioSource component, provides access to mic 
        private AudioSource audioSource; 
   
        // Flag indicating mic detection 
        private bool microphoneDetected; 
   
        // Component converting speech to text 
        private DictationRecognizer dictationRecognizer; 
    ```

6.  Code für die *Methoden "Awake()"* und *"Start()"* muss nun hinzugefügt werden. Diese werden aufgerufen, wenn die -Klasse initialisiert wird:

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this; 
        } 
    
        void Start() 
        { 
            //Use Unity Microphone class to detect devices and setup AudioSource 
            if(Microphone.devices.Length > 0) 
            { 
                Results.instance.SetMicrophoneStatus("Initialising..."); 
                audioSource = GetComponent<AudioSource>(); 
                microphoneDetected = true; 
            } 
            else 
            { 
                Results.instance.SetMicrophoneStatus("No Microphone detected"); 
            } 
        } 
    ```

7.  Sie können *die* *Update()-Methode* löschen, da diese Klasse sie nicht verwendet.
8.  Nun benötigen Sie die Methoden, die die App zum Starten und  Beenden der Spracherfassung verwendet, und übergeben sie an die Translator-Klasse, die Sie in Kürze erstellen werden. Kopieren Sie den folgenden Code, und fügen Sie ihn unterhalb der *Start()-Methode* ein.

    ```csharp
        /// <summary> 
        /// Start microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StartCapturingAudio() 
        { 
            if(microphoneDetected) 
            {               
                // Start dictation 
                dictationRecognizer = new DictationRecognizer(); 
                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult; 
                dictationRecognizer.Start(); 
    
                // Update UI with mic status 
                Results.instance.SetMicrophoneStatus("Capturing..."); 
            }      
        } 
 
        /// <summary> 
        /// Stop microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StopCapturingAudio() 
        { 
            Results.instance.SetMicrophoneStatus("Mic sleeping"); 
            Microphone.End(null); 
            dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult; 
            dictationRecognizer.Dispose(); 
        }
    ```

    > [!TIP]
    > Obwohl diese Anwendung sie nicht nutzt, wurde hier auch die *StopCapturingAudio()-Methode* bereitgestellt, wenn Sie die Möglichkeit implementieren möchten, die Erfassung von Audiodaten in Ihrer Anwendung zu beenden.

9.  Sie müssen nun einen Diktathandler hinzufügen, der aufgerufen wird, wenn die Stimme beendet wird. Diese Methode über gibt dann den diktierten Text an *die* Translator weiter.

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// Debugging message is delivered to the Results class.
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Results.instance.SetDictationResult(text);
   
            // Start the coroutine that process the dictation through Azure 
            StartCoroutine(Translator.instance.TranslateWithUnityNetworking(text));   
        }
    ```

10. Achten Sie darauf, dass Sie Ihre Änderungen in Visual Studio, bevor Sie zu Unity zurückkehren.

> [!WARNING]  
> An diesem Punkt wird im *Unity-Editor-Konsolenbereich* ein Fehler angezeigt ("Der Name "Translator" ist nicht vorhanden..."). Dies liegt daran, dass der Code auf die *Translator* verweist, die Sie im nächsten Kapitel erstellen werden.

## <a name="chapter-7--call-to-azure-and-translator-service"></a>Kapitel 7: Aufrufen von Azure und des Übersetzungsdiensts

Das letzte Skript, das Sie erstellen müssen, ist die *Translator* Klasse. 

Diese Klasse ist für Folgendes verantwortlich:

-   Authentifizieren der App bei *Azure* im Austausch gegen ein **Authentifizierungstoken**.
-   Verwenden Sie **das Authentifizierungstoken,** um zu übersetzenden Text zu übermitteln (empfangen von der *MicrophoneManager-Klasse).*
-   Empfangen Sie das übersetzte Ergebnis, und übergeben Sie es an die *Ergebnisklasse,* die auf der Benutzeroberfläche visualisiert werden soll.

So erstellen Sie diese Klasse: 
1.  Wechseln Sie zum **Ordner Skripts,** den Sie zuvor erstellt haben. 
2.  Klicken Sie mit der rechten Maustaste in **Project Bereich**, erstellen **> C#-Skript.** Rufen Sie das Skript *Translator.*
3.  Doppelklicken Sie auf das *neue* Translator, um es mit **dem Visual Studio.**
4.  Fügen Sie am Anfang der Datei die folgenden Namespaces hinzu:

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  Fügen Sie dann die folgenden Variablen innerhalb der *Translator* hinzu:

    ```csharp
        public static Translator instance; 
        private string translationTokenEndpoint = "https://api.cognitive.microsoft.com/sts/v1.0/issueToken"; 
        private string translationTextEndpoint = "https://api.microsofttranslator.com/v2/http.svc/Translate?"; 
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key"; 
    
        //Substitute the value of authorizationKey with your own Key 
        private const string authorizationKey = "-InsertYourAuthKeyHere-"; 
        private string authorizationToken; 
    
        // languages set below are: 
        // English 
        // French 
        // Italian 
        // Japanese 
        // Korean 
        public enum Languages { en, fr, it, ja, ko }; 
        public Languages from = Languages.en; 
        public Languages to = Languages.it; 
    ```

    > [!NOTE]
    > - Die Sprachen, die in die **Sprachenenum eingefügt werden,** sind nur Beispiele. Wenn Sie möchten, können Sie weitere hinzufügen. Die [API unterstützt mehr als 60 Sprachen](/azure/cognitive-services/translator/languages) (einschließlich Klingon).
    > - Es gibt [](https://www.microsoft.com/translator/business/languages/)eine interaktivere Seite, die die verfügbaren Sprachen behandelt. Beachten Sie jedoch, dass die Seite nur dann zu funktionieren scheint, wenn die Standortsprache auf "" festgelegt ist (und die Microsoft-Website wahrscheinlich zu Ihrer nativen Sprache umleitet). Sie können die Websitesprache am unteren Rand der Seite oder durch Ändern der URL ändern.
    > - Der **wert authorizationKey** im obigen Codeausschnitt muss  der Schlüssel sein, den Sie beim Abonnieren der Azure *Translator Text-API erhalten haben.* Dies wurde in [Kapitel 1 behandelt.](#chapter-1--the-azure-portal)

6.  Code für die *Methoden "Awake()"* und *"Start()"* muss nun hinzugefügt werden. 
7.  In diesem Fall wird azure mithilfe des Autorisierungsschlüssels vom Code zum Abrufen eines Tokens *aufruft.* 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton  
            instance = this; 
        } 
    
        // Use this for initialization  
        void Start() 
        { 
            // When the application starts, request an auth token 
            StartCoroutine("GetTokenCoroutine", authorizationKey); 
        }
    ```

    > [!NOTE]
    > Das Token läuft nach 10 Minuten ab. Je nach Szenario für Ihre App müssen Sie möglicherweise mehrmals denselben Coroutinenaufruf erstellen.

8.  Die Coroutine zum Abrufen des Tokens ist wie folgt:

    ```csharp
        /// <summary> 
        /// Request a Token from Azure Translation Service by providing the access key. 
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        private IEnumerator GetTokenCoroutine(string key)
        {
            if (string.IsNullOrEmpty(key))
            {
                throw new InvalidOperationException("Authorization key not set.");
            }

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(translationTokenEndpoint, string.Empty))
            {
                unityWebRequest.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;

                // Update the UI with the response code 
                Results.instance.SetAzureResponse(responseCode.ToString());

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Results.instance.azureResponseText.text = unityWebRequest.error;
                    yield return null;
                }
                else
                {
                    authorizationToken = unityWebRequest.downloadHandler.text;
                }
            }

            // After receiving the token, begin capturing Audio with the MicrophoneManager Class 
            MicrophoneManager.instance.StartCapturingAudio();
        }
    ```

    > [!WARNING]
    > Wenn Sie den Namen der IEnumerator-Methode **GetTokenCoroutine()** bearbeiten, müssen Sie die Aufrufzeichenfolgenwerte *StartCoroutine* und *StopCoroutine* im obigen Code aktualisieren. [Wie in der Unity-Dokumentation](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html)beschrieben, müssen Sie zum Beenden einer bestimmten *Coroutine* die Zeichenfolgenwertmethode verwenden.

9.  Fügen Sie als Nächstes die Coroutine (mit der Streammethode "support" direkt darunter) hinzu, um die Übersetzung des Von der *MicrophoneManager-Klasse* empfangenen Texts zu erhalten. Dieser Code erstellt eine Abfragezeichenfolge, die an die *Azure Translator-Text-API* gesendet werden soll, und verwendet dann die interne UnityWebRequest-Klasse, um einen "Get"-Aufruf an den Endpunkt mit der Abfragezeichenfolge auszuführen. Das Ergebnis wird dann verwendet, um die Übersetzung in Ihrem Results-Objekt zu setzen. Der folgende Code zeigt die Implementierung:

    ```csharp
        /// <summary> 
        /// Request a translation from Azure Translation Service by providing a string.  
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        public IEnumerator TranslateWithUnityNetworking(string text)
        {
            // This query string will contain the parameters for the translation 
            string queryString = string.Concat("text=", Uri.EscapeDataString(text), "&from=", from, "&to=", to);

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(translationTextEndpoint + queryString))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + authorizationToken);
                unityWebRequest.SetRequestHeader("Accept", "application/xml");
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                    yield return null;
                }

                // Parse out the response text from the returned Xml
                string result = XElement.Parse(unityWebRequest.downloadHandler.text).Value;
                Results.instance.SetTranslatedResult(result);
            }
        }
    ```

10. Achten Sie darauf, dass Sie Ihre Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity zurückkehren.*

## <a name="chapter-8--configure-the-unity-scene"></a>Kapitel 8: Konfigurieren der Unity-Szene

1.  Klicken Sie im Unity-Editor auf  die *Ergebnisklasse,* und ziehen Sie sie aus dem Ordner **Skripts** auf das **Objekt Hauptkamera** im *Hierarchiebereich.*
2.  Klicken Sie auf die **Hauptkamera,** und sehen Sie sich den *Inspektorbereich an.* Sie werden feststellen, dass innerhalb der neu hinzugefügten *Skriptkomponente* vier Felder mit leeren Werten enthalten sind. Dies sind die Ausgabeverweise auf die Eigenschaften im Code. 
3.  Ziehen Sie die entsprechenden **Textobjekte** aus dem *Hierarchiebereich* auf diese vier Slots, wie in der folgenden Abbildung dargestellt.

    ![Aktualisieren Sie Zielverweise mit angegebenen Werten.](images/AzureLabs-Lab1-34.png)
  
4.  Klicken Sie anschließend auf die Translator-Klasse, und *ziehen* Sie sie aus dem **Ordner Skripts** in das **Objekt Hauptkamera** im *Hierarchiebereich*. 
5.  Klicken Sie dann auf die *Klasse MicrophoneManager,* und ziehen Sie sie aus dem **Ordner Skripts** in das **Objekt Hauptkamera** im *Hierarchiebereich*. 
6.  Klicken Sie abschließend auf die **Hauptkamera, und** sehen Sie sich den *Inspektorbereich an.* Sie werden feststellen, dass es in dem Skript, das Sie gezogen haben, zwei Dropdownfelder gibt, mit denen Sie die Sprachen festlegen können.
 
    ![Stellen Sie sicher, dass die vorgesehenen Übersetzungssprachen eingegeben werden.](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a>Kapitel 9 – Testen in Mixed Reality

An diesem Punkt müssen Sie testen, ob die Szene ordnungsgemäß implementiert wurde.

Stellen Sie Folgendes sicher:

- Alle in Kapitel [1 erwähnten](#chapter-1--the-azure-portal) Einstellungen sind ordnungsgemäß festgelegt. 
- Die *Skripts* Results , *Translator* und *MicrophoneManager* werden an das **Main Camera-Objekt** angefügt. 
- Sie haben Ihren *Azure Translator Text-API-Dienstschlüssel* in der **AuthorizationKey-Variablen** im Translator *platziert.*   
- Alle Felder im Hauptkamerainspektorbereich *sind* ordnungsgemäß zugewiesen.
- Ihr Mikrofon funktioniert beim Ausführen Ihrer Szene (falls nicht,  überprüfen Sie, ob das angeschlossene Mikrofon das Standardgerät ist und Sie es innerhalb von Windows) eingerichtet [haben.](https://support.microsoft.com/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)

Sie können das immersive Headset testen, indem Sie im **Unity-Editor** auf die *Schaltfläche Wiedergabe klicken.*
Die App sollte über das angeschlossene immersive Headset funktionieren.

> [!WARNING]  
> Wenn in der Unity-Konsole ein Fehler beim Ändern des Standardaudiogeräts angezeigt wird, funktioniert die Szene möglicherweise nicht wie erwartet. Dies liegt an der Art und Weise, wie das Mixed Reality-Portal mit integrierten Mikrofonen für Headsets, die über diese verfügen, zu tun hat. Wenn dieser Fehler angezeigt wird, beenden Sie einfach die Szene, und starten Sie sie erneut, und die Dinge sollten erwartungsgemäß funktionieren.

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a>Kapitel 10 : Erstellen der UWP-Lösung und Sideload auf dem lokalen Computer

Alles, was für den Unity-Abschnitt dieses Projekts erforderlich ist, wurde abgeschlossen, daher ist es an der Zeit, es aus Unity zu erstellen.

1.  Navigieren Sie **zu Build Einstellungen**: File > Build **Einstellungen...**
2.  Klicken Sie **im Fenster Build Einstellungen** auf **Erstellen.**

    ![Erstellen Sie die Unity-Szene.](images/AzureLabs-Lab1-36.png)
  
3.  Wenn nicht bereits, aktivieren Sie **Unity C#-Projekte**.
4.  Klicken Sie auf **Erstellen**. Unity startet ein *Datei-Explorer-Fenster,* in dem Sie einen Ordner erstellen und dann einen Ordner auswählen müssen, in dem die App erstellt werden soll. Erstellen Sie diesen Ordner jetzt, und nennen Sie ihn *App*. Wenn Sie dann den *Ordner App ausgewählt* haben, klicken Sie auf Ordner **auswählen.** 
5.  Unity beginnt damit, Ihr Projekt im Ordner *App zu* erstellen. 
6.  Sobald Unity die Erstellung abgeschlossen hat (dies kann einige Zeit dauern), wird ein *Datei-Explorer-Fenster* am Speicherort Ihres Buildfensters geöffnet (überprüfen Sie Ihre Taskleiste, da sie möglicherweise nicht immer über Ihren Fenstern angezeigt wird, aber Sie werden über das Neue-Fenster benachrichtigt).

## <a name="chapter-11--deploy-your-application"></a>Kapitel 11 – Bereitstellen Ihrer Anwendung

So stellen Sie Ihre Anwendung bereitstellen:

1.  Navigieren Sie zu Ihrem neuen Unity-Build (dem *Ordner App),* und öffnen Sie die Projektmappendatei mit *Visual Studio.*
2.  Wählen Sie in der Projektmappenkonfiguration **Debuggen aus.**
3.  Wählen Sie auf der Projektmappenplattform **x86**, **Lokaler Computer aus.** 

    > Für die Microsoft HoloLens ist es möglicherweise einfacher, dies auf *Remotecomputer* zu setzen, damit Sie nicht an Ihren Computer geentert werden. Sie müssen jedoch auch die folgenden Schritte unternehmen:
    > - Kennen Sie **die IP-Adresse** Ihrer HoloLens, die sie im Einstellungen > *Network & Internet > Wi-Fi > Finden.* IPv4 ist die Adresse, die Sie verwenden sollten. 
    > - Stellen Sie *sicher, dass der Entwicklermodus* **aktiviert ist.** finden Sie *Einstellungen > Update & Security > Für Entwickler.*

    ![Stellen Sie die Lösung über Visual Studio.](images/AzureLabs-Lab1-37.png)
    
 
4.  Wechseln Sie zum **Menü Erstellen,** und klicken Sie **auf Projektmappe bereitstellen,** um die Anwendung auf Ihren PC zu laden.
5.  Ihre App sollte nun in der Liste der installierten Apps angezeigt werden, die zum Start bereit sind.
6.  Nach dem Start werden Sie von der App aufgefordert, den Zugriff auf das Mikrofon zu autorisieren. Achten Sie darauf, auf die **Schaltfläche JA zu** klicken.
7.  Sie können jetzt mit der Übersetzung beginnen!

## <a name="your-finished-translation-text-api-application"></a>Ihre fertige Übersetzungstext-API-Anwendung

Herzlichen Glückwunsch! Sie haben eine Mixed Reality-App erstellt, die die Azure-Textübersetzungs-API nutzt, um Sprache in übersetzten Text zu konvertieren.

![Endgültiges Produkt.](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises&quot;></a>Zusatzübungen

### <a name=&quot;exercise-1&quot;></a>Übung 1

Können Sie der App Text-zu-Sprache-Funktionalität hinzufügen, damit der zurückgegebene Text gesprochen wird?

### <a name=&quot;exercise-2&quot;></a>Übung 2

Ermöglichen Sie es dem Benutzer, die Quell- und Ausgabesprachen (&quot;von&quot; und &quot;in") innerhalb der App selbst zu ändern, sodass die App nicht jedes Mal neu erstellt werden muss, wenn Sie die Sprachen ändern möchten.