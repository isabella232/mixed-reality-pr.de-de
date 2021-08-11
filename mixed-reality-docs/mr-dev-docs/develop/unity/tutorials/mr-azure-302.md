---
title: 'HoloLens (1. Generation) und Azure 302: Maschinelles Sehen'
description: In diesem Kurs erfahren Sie, wie Sie visuelle Inhalte in einem bereitgestellten Bild erkennen, indem Sie Azure maschinelles Sehen in einer Mixed Reality-Anwendung verwenden.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, tutorial, api, computer vision, hololens, immersive, vr, Windows 10, Visual Studio
ms.openlocfilehash: 5cac40c2613187776ea9ec5ba1268f1422a084d32322e9c4aca6742ed75d05b2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115225960"
---
# <a name="hololens-1st-gen-and-azure-302-computer-vision"></a>HoloLens (1. Generation) und Azure 302: Bildverarbeitung

<br>

>[!NOTE]
>Die Tutorials der Mixed Reality Academy wurden im Hinblick auf HoloLens (1. Gen.) und immersive Mixed Reality-Headsets entworfen.  Daher halten wir es für wichtig, diese Tutorials für Entwickler verfügbar zu halten, die noch nach Anleitung beim Entwickeln für diese Geräte suchen.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für HoloLens 2 verwendet werden.  Sie werden gewartet, um weiterhin auf den unterstützten Geräten zu funktionieren. Es wird eine neue Reihe von Tutorials geben, die in Zukunft veröffentlicht werden, die veranschaulichen, wie Sie für die entwicklung HoloLens 2.  Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn sie veröffentlicht werden.

<br>

In diesem Kurs erfahren Sie, wie Sie visuelle Inhalte in einem bereitgestellten Bild erkennen, indem Sie Azure maschinelles Sehen in einer Mixed Reality-Anwendung verwenden.

Erkennungsergebnisse werden als beschreibende Tags angezeigt. Sie können diesen Dienst verwenden, ohne ein Machine Learning-Modell trainieren zu müssen. Wenn Ihre Implementierung ein Machine Learning-Modell trainieren muss, finden Sie weitere Informationen [unter MR und Azure 302b](mr-azure-302b.md).

![Labergebnis](images/AzureLabs-Lab2-000.png)

Microsoft maschinelles Sehen ist eine Reihe von APIs, die entwicklern Bildverarbeitung und -analyse (mit Rückgabeinformationen) mithilfe erweiterter Algorithmen aus der Cloud bereitstellen. Entwickler laden ein Bild oder eine Bild-URL hoch, und die Microsoft maschinelles Sehen-API-Algorithmen analysieren den visuellen Inhalt basierend auf Eingaben, die der Benutzer ausgewählt hat. Diese können dann Informationen zurückgeben, einschließlich der Identifizierung von Typ und Qualität eines Bilds, erkennen menschlicher Gesichter (Zurückgeben ihrer Koordinaten) und Markieren oder Kategorisieren von Bildern. Weitere Informationen finden Sie auf der [Azure maschinelles Sehen-API-Seite.](https://azure.microsoft.com/services/cognitive-services/computer-vision/)

Nachdem Sie diesen Kurs abgeschlossen haben, verfügen Sie über eine Mixed Reality HoloLens Anwendung, die Folgendes tun kann:

1.  Mithilfe der Tippbewegung erfasst die Kamera des HoloLens Bilds.
2.  Das Image wird an den Azure maschinelles Sehen-API-Dienst gesendet. 
3.  Die erkannten Objekte werden in einer einfachen Benutzeroberflächengruppe aufgeführt, die in der Unity-Szene positioniert ist.

In Ihrer Anwendung liegt es an Ihnen, wie Sie die Ergebnisse in Ihren Entwurf integrieren. Dieser Kurs soll Ihnen beibringen, wie Sie einen Azure-Dienst in Ihr Unity-Projekt integrieren. Es ist Ihre Aufgabe, das Wissen aus diesem Kurs zu nutzen, um Ihre Mixed Reality-Anwendung zu verbessern.

## <a name="device-support"></a>Geräteunterstützung

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td> MR und Azure 302: Maschinelles Sehen</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Während sich dieser Kurs hauptsächlich auf HoloLens konzentriert, können Sie das, was Sie in diesem Kurs lernen, auch auf immersive Headsets (VR) Windows Mixed Reality anwenden. Da immersive Headsets (VR) keine zugänglichen Kameras haben, benötigen Sie eine externe Kamera, die mit Ihrem PC verbunden ist. Im Verlauf des Kurses finden Sie Hinweise zu allen Änderungen, die Sie möglicherweise vornehmen müssen, um immersive Headsets (VR) zu unterstützen.

## <a name="prerequisites"></a>Voraussetzungen

> [!NOTE]
> Dieses Tutorial ist für Entwickler konzipiert, die über grundlegende Erfahrung mit Unity und C# verfügen. Beachten Sie auch, dass die Voraussetzungen und die geschriebenen Anweisungen in diesem Dokument darstellen, was zum Zeitpunkt der Erstellung (Mai 2018) getestet und überprüft wurde. Sie können die neueste Software verwenden, [](../../install-the-tools.md) wie im Artikel Installieren der Tools aufgeführt. Es sollte jedoch nicht davon ausgegangen werden, dass die Informationen in diesem Kurs perfekt mit der neueren Software übereinstimmen, als unten aufgeführt.

Für diesen Kurs wird die folgende Hardware und Software empfohlen:

- Ein Entwicklungs-PC, [der mit Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) für die Entwicklung immersiver Headsets (VR) kompatibel ist
- [Windows 10 Fall Creators Update (oder höher) mit aktivierter Entwicklermodus](../../install-the-tools.md#installation-checklist)
- [Das neueste Windows 10 SDK](../../install-the-tools.md#installation-checklist)
- [Unity 2017.4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- Ein [Windows Mixed Reality immersives Headset (VR)](../../../discover/immersive-headset-hardware-details.md) oder [ein](/hololens/hololens1-hardware) Microsoft HoloLens mit aktivierten Entwicklermodus
- Eine mit Ihrem PC verbundene Kamera (für die Entwicklung immersiver Headsets)
- Internetzugriff für azure setup and maschinelles Sehen API retrieval

## <a name="before-you-start"></a>Vorbereitung

1.  Um Probleme beim Erstellen dieses Projekts zu vermeiden, wird dringend empfohlen, das in diesem Tutorial erwähnte Projekt in einem Stamm- oder Near-Root-Ordner zu erstellen (lange Ordnerpfade können zur Buildzeit Probleme verursachen).
2.  Einrichten und Testen Ihrer HoloLens. Wenn Sie Unterstützung beim Einrichten Ihrer HoloLens benötigen, lesen Sie den Artikel HoloLens [Setup.](/hololens/hololens-setup) 
3.  Es ist eine gute Idee, die Kalibrierung und Sensoroptimierung durchzuführen, wenn Sie mit der Entwicklung einer neuen HoloLens-App beginnen (manchmal kann es helfen, diese Aufgaben für jeden Benutzer auszuführen). 

Hilfe zur Kalibrierung finden Sie unter diesem [Link zum Artikel HoloLens Kalibrierung.](/hololens/hololens-calibration#hololens-2)

Hilfe zur Sensoroptimierung finden Sie unter diesem [Link zum Artikel HoloLens Sensoroptimierung.](/hololens/hololens-updates)

## <a name="chapter-1--the-azure-portal"></a>Kapitel 1: Das Azure-Portal

Um den *maschinelles Sehen-API-Dienst* in Azure zu verwenden, müssen Sie eine Instanz des Diensts konfigurieren, die für Ihre Anwendung verfügbar gemacht wird.

1.  Melden Sie sich zunächst beim [Azure-Portal an.](https://portal.azure.com) 

    > [!NOTE]
    > Wenn Sie noch nicht über ein Azure-Konto verfügen, müssen Sie eines erstellen. Wenn Sie dieses Tutorial in einer Classroom- oder Lab-Situation durch verwenden, bitten Sie Ihren Dozenten oder einen der Proktoren um Hilfe beim Einrichten Ihres neuen Kontos.

2.  Klicken Sie nach der Anmeldung **in** der linken oberen Ecke auf Neu, suchen Sie nach *maschinelles Sehen-API,* und geben Sie **ein.**

    ![Erstellen einer neuen Ressource in Azure](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > Das Wort **Neu** wurde in neueren Portalen möglicherweise durch **Ressource** erstellen ersetzt.
 
3.  Auf der neuen Seite finden Sie eine Beschreibung des maschinelles Sehen *API-Diensts.* Wählen Sie unten links auf  dieser Seite die Schaltfläche Erstellen aus, um eine Zuordnung zu diesem Dienst zu erstellen.

    ![Informationen zum Api-Dienst für das sehende Sehen](images/AzureLabs-Lab2-01.png)
 
4.  Nachdem Sie auf Erstellen geklickt **haben:**

    1. Fügen Sie den gewünschten **Namen für** diese Dienstinstanz ein.
    2. Wählen Sie ein **Abonnement** aus.
    3. Wählen Sie **den für** Sie geeigneten Tarif aus. Wenn Sie zum ersten Mal einen *maschinelles Sehen-API-Dienst* erstellen, sollte ihnen ein Free-Tarif (mit dem Namen F0) zur Verfügung stehen.
    4. Wählen Sie eine **Ressourcengruppe aus,** oder erstellen Sie eine neue. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, Steuern des Zugriffs, Bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. B. diesen Labs) zugeordnet sind, unter einer gemeinsamen Ressourcengruppe zu halten. 

        > Weitere Informationen zu Azure-Ressourcengruppen finden Sie im Artikel [zu Ressourcengruppen.](/azure/azure-resource-manager/resource-group-portal)

    5. Bestimmen Sie den Standort für Ihre Ressourcengruppe (wenn Sie eine neue Ressourcengruppe erstellen). Der Standort befindet sich idealerweise in der Region, in der die Anwendung ausgeführt wird. Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.

    6. Sie müssen auch bestätigen, dass Sie die auf diesen Dienst angewendeten Geschäftsbedingungen verstanden haben.
    7. Klicken Sie auf „Erstellen“.

        ![Informationen zur Diensterstellung](images/AzureLabs-Lab2-02.png)

5.  Nachdem Sie auf **Erstellen** geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. Dies kann eine Minute dauern.
6.  Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.

    ![Sehen Sie sich die neue Benachrichtigung für Ihren neuen Dienst an.](images/AzureLabs-Lab2-03.png) 
 
7.  Klicken Sie auf die Benachrichtigung, um Ihre neue Dienstinstanz zu untersuchen. 

    ![Wählen Sie die Schaltfläche Zu Ressource wechseln aus.](images/AzureLabs-Lab2-04.png)
 
8. Klicken Sie in **der Benachrichtigung auf die** Schaltfläche Zu Ressource wechseln, um Ihre neue Dienstinstanz zu untersuchen. Sie werden zu Ihrer neuen api maschinelles Sehen-Dienstinstanz. 

    ![Ihr neues maschinelles Sehen-API-Dienstimage](images/AzureLabs-Lab2-05.png)
 
9.  In diesem Tutorial muss Ihre Anwendung Aufrufe an Ihren Dienst tätigen. Dies erfolgt über die Verwendung des Abonnementschlüssels Ihres Diensts.
10. Navigieren  Sie auf der Seite Schnellstart Ihres *maschinelles Sehen-API-Diensts* zum ersten *Schritt,* Schlüssel abrufen, und klicken Sie auf Schlüssel **(** Sie können dies auch erreichen, indem Sie im Navigationsmenü der Dienste auf den blauen Link Schlüssel klicken, der durch das Schlüsselsymbol gekennzeichnet ist). Dadurch werden Ihre Dienstschlüssel *preisgaben.*
11. Erstellen Sie eine Kopie eines der angezeigten Schlüssel, da Sie diese später in Ihrem Projekt benötigen. 

12. Wechseln Sie zurück zur *Seite Schnellstart,* und rufen Sie ihren Endpunkt ab. Beachten Sie, dass Ihre je nach Region unterschiedlich sein kann (in diesem Beispiel müssen Sie ihren Code später ändern). Nehmen Sie eine Kopie dieses Endpunkts zur späteren Verwendung:

    ![Ihr neuer maschinelles Sehen-API-Dienst](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > Sie können hier überprüfen, was die verschiedenen Endpunkte [sind.](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa) 

## <a name="chapter-2--set-up-the-unity-project"></a>Kapitel 2: Einrichten des Unity-Projekts

Das folgende Beispiel ist eine typische Einrichtung für die Entwicklung mit Mixed Reality und ist daher eine gute Vorlage für andere Projekte.

1.  Öffnen Sie *Unity,* und klicken Sie **auf Neu.** 

    ![Starten Sie ein neues Unity-Projekt.](images/AzureLabs-Lab2-06.png)

2.  Sie müssen nun einen Unity-Project angeben. Fügen **Sie MR_ComputerVision** ein. Stellen Sie sicher, dass der Projekttyp auf **3D festgelegt ist.** Legen Sie **den Speicherort** auf einen für Sie geeigneten Speicherort fest (denken Sie daran, dass die Nähe zu Stammverzeichnissen besser ist). Klicken Sie dann auf **Projekt erstellen.**

    ![Geben Sie Details für das neue Unity-Projekt an.](images/AzureLabs-Lab2-07.png)

3.  Wenn Unity geöffnet ist, sollten Sie überprüfen, ob der **Standardskript-Editor** auf **Visual Studio.** Wechseln Sie **zu > Bearbeiten,** und navigieren Sie dann im neuen Fenster zu **Externe Tools.** Ändern **Sie den editor für externe** **Skripts in Visual Studio 2017**. Schließen Sie das **Fenster Einstellungen.**

    ![Skript-Editor-Einstellung aktualisieren.](images/AzureLabs-Lab2-08.png)

4.  Wechseln Sie als Nächstes zu **Datei > Build Einstellungen,** wählen Sie **Universelle Windows-Plattform** aus, und klicken Sie dann auf die Schaltfläche Plattform wechseln, um Ihre Auswahl anzuwenden. 

    ![Erstellen Einstellungen Fensters, Wechseln der Plattform zu UWP.](images/AzureLabs-Lab2-10.png)

5.  Vergewissern Sie **sich, dass > Datei Einstellungen** erstellen, und stellen Sie Sicher, dass:

    1. **Das Zielgerät** ist **auf** HoloLens

        > Legen Sie für die immersiven Headsets **Zielgerät auf** *Beliebiges Gerät fest.*

    2. **Buildtyp** ist auf **D3D festgelegt**
    3. **SDK** ist auf **Latest installed (Neueste installiert) festgelegt.**
    4. **Visual Studio version** ist auf **Latest installed (Neueste installiert) festgelegt.**
    5. **Erstellen und Ausführen** ist auf Lokaler **Computer festgelegt.**
    6. Speichern Sie die Szene, und fügen Sie sie dem Build hinzu.

        1. Wählen Sie hierzu Geöffnete Szenen **hinzufügen aus.** Ein Speicherfenster wird angezeigt.
        
            ![Klicken Sie auf die Schaltfläche "Geöffnete Szenen hinzufügen".](images/AzureLabs-Lab2-11.png)

        2. Erstellen Sie einen neuen Ordner für diesen und jede  zukünftige Szene, und wählen Sie dann die Schaltfläche Neuer Ordner aus, um einen neuen Ordner zu erstellen, und nennen Sie **ihn Scenes**.

            ![Erstellen eines neuen Skriptordners](images/AzureLabs-Lab2-12.png)

        3. Öffnen Sie den neu erstellten **Ordner Scenes,** und geben Sie dann im Feld Dateiname *:* Text MR_ComputerVisionScene **ein,** und klicken Sie dann **auf Speichern.**

            ![Benennen Sie die neue Szene.](images/AzureLabs-Lab2-13.png)

            > Beachten Sie, dass Sie Ihre Unity-Szenen im Ordner *Assets* speichern müssen, da sie dem Unity-Project. Das Erstellen des Szenenordners (und anderer ähnlicher Ordner) ist eine typische Methode zum Strukturieren eines Unity-Projekts.

    7. Die restlichen Einstellungen in *Build Einstellungen* sollten vorerde als Standardeinstellung be übrig bleiben.

6. Klicken Sie *im Fenster Build Einstellungen* auf die Schaltfläche Player **Einstellungen,** um den entsprechenden Bereich in dem Bereich zu öffnen, in dem sich der *Inspektor* befindet. 

    ![Öffnen Sie die Playereinstellungen.](images/AzureLabs-Lab2-14.png)

7. In diesem Bereich müssen einige Einstellungen überprüft werden:

    1. Führen Sie **auf Einstellungen** Registerkarte Andere Optionen aus:

        1. **Die Skriptlaufzeitversion** sollte **stabil** sein (.NET 3.5 Equivalent).
        2. **Das Skript-Back-End** sollte **.NET sein.**
        3. **Der API-Kompatibilitätsgrad** sollte **.NET 4.6 sein.**

            ![Aktualisieren Sie andere Einstellungen.](images/AzureLabs-Lab2-15.png)
      
    2. Aktivieren Sie **auf Einstellungen** Registerkarte Publishing Einstellungen unter **Capabilities (Funktionen)** Die folgenden Optionen:

        1. **InternetClient**
        2. **Webcam**

            ![Aktualisieren der Veröffentlichungseinstellungen.](images/AzureLabs-Lab2-16.png)

    3. Aktivieren Sie weiter unten im Bereich in **XR Einstellungen** (unter Publish **Einstellungen)** **(Virtual Reality** unterstützt), und stellen Sie sicher, dass das Windows Mixed Reality **SDK** hinzugefügt wird.

        ![Aktualisieren Sie die X R-Einstellungen.](images/AzureLabs-Lab2-17.png)

8.  Zurück in *Build Einstellungen* _Unity C#-Projekte_ ist nicht mehr ausgegraut. aktivieren Sie das Kontrollkästchen daneben. 
9.  Schließen Sie das Fenster „Build Settings“ (Buildeinstellungen).
10. Speichern Sie Ihre Szene und Project (**FILE > SAVE SCENE/FILE > SAVE PROJECT**).

## <a name="chapter-3--main-camera-setup"></a>Kapitel 3 : Einrichtung der Hauptkamera

> [!IMPORTANT]
> Wenn Sie die Unity Set *up-Komponente* dieses Kurses überspringen und direkt mit dem Code fortfahren möchten, können [](https://docs.unity3d.com/Manual/AssetPackages.html)Sie dieses [UNITYPACKAGE](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage)herunterladen, als benutzerdefiniertes Paket in Ihr Projekt importieren und dann mit Kapitel [5](#chapter-5--create-the-resultslabel-class)fortfahren.

1.  Wählen Sie *im Hierarchiebereich* die **Hauptkamera aus.** 
2.  Nach der Auswahl können Sie alle Komponenten der **Hauptkamera** im *Inspektorbereich sehen.*

    1. Das **Camera-Objekt** muss den Namen **Hauptkamera haben** (beachten Sie die Schreibweise!)
    2. Das **Hauptkameratag muss** auf **MainCamera** festgelegt werden (beachten Sie die Schreibweise!)
    3. Stellen Sie **sicher, dass die Transformationsposition** auf **0, 0, 0 festgelegt ist.**
    4. Legen **Sie Clear Flags auf** Solid **Color** fest (ignorieren Sie dies für immersive Headsets).
    5. Legen Sie **die Hintergrundfarbe** der Kamerakomponente auf **Schwarz, Alpha 0 (Hexadezimaler Code: #00000000)** fest (ignorieren Sie dies für immersive Headsets).

        ![Aktualisieren von Kamerakomponenten.](images/AzureLabs-Lab2-18.png)
 
3.  Als Nächstes müssen Sie ein einfaches Cursorobjekt erstellen, das an die Hauptkamera angefügt ist. Dies hilft Ihnen, die Ausgabe der Bildanalyse zu positionieren, wenn die Anwendung ausgeführt wird.  Dieser Cursor bestimmt den Mittelpunkt des Kamerafokus.

So erstellen Sie den Cursor:

1.  Klicken Sie *im Hierarchiebereich* mit der rechten Maustaste auf die **Hauptkamera**. Klicken **Sie unter 3D-Objekt** auf **Sphere**.

    ![Wählen Sie das Cursorobjekt aus.](images/AzureLabs-Lab2-19.png)
 
2.  Benennen Sie die **Kugel** in **Cursor** um (doppelklicken Sie auf das Cursorobjekt, oder drücken Sie die Taste "F2" mit dem ausgewählten Objekt), und stellen Sie sicher, dass es sich als untergeordnetes Element der **Hauptkamera befindet.**

3.  Klicken Sie *im Hierarchiebereich* mit der linken Maustaste auf **den Cursor**. Passen Sie bei ausgewähltem Cursor im Inspektorbereich die *folgenden Variablen an:*

    1. Legen Sie *die Transformationsposition* **auf 0, 0, 5 fest.**
    2. Legen Sie *die Skalierung* auf **0,02, 0,02, 0,02 fest.**

        ![Aktualisieren Sie die Transformationsposition und die Skalierung.](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a>Kapitel 4– Einrichten des Bezeichnungssystems

Nachdem Sie ein Bild mit der Kamera des HoloLens erfasst haben, wird dieses Bild zur Analyse an Ihre *Azure maschinelles Sehen API* Service-Instanz gesendet. 

Die Ergebnisse dieser Analyse sind eine Liste erkannter Objekte mit dem Namen **Tags**. 

Sie verwenden Bezeichnungen (als 3D-Text im Weltraum), um diese Tags an der Stelle anzuzeigen, an der das Foto aufgenommen wurde.

In den folgenden Schritten wird gezeigt, wie Sie das **Label-Objekt** einrichten.

1.  Klicken Sie mit der rechten Maustaste auf eine beliebige Stelle im Hierarchiebereich (die Position spielt an diesem Punkt keine Rolle), und fügen Sie unter **3D-Objekt** einen **3D-Text hinzu.** Nennen Sie ihn **LabelText**.

    ![Erstellen Sie ein 3D-Textobjekt.](images/AzureLabs-Lab2-21.png)
 
2.  Klicken Sie *im Hierarchiebereich* mit der linken Maustaste auf **LabelText**. Wenn **LabelText ausgewählt** ist, passen Sie die folgenden Variablen im *Inspektorbereich an:*

    1. Legen Sie **position** auf **0,0,0 fest.**
    2. Legen Sie **die Skalierung** auf **0,01, 0,01, 0,01 fest.**
    3. In der Komponente **Text Mesh:**
    4. Ersetzen Sie den text-Text in **Text** durch "..."        
    5. Legen Sie den **Anker** auf **Mittlere Mitte fest.**
    6. Festlegen der **Ausrichtung auf** **"Zentriert"**
    7. Legen Sie die **Registerkartengröße** auf **4 fest.**
    8. Legen Sie **den Schriftgrad auf** **50 fest.**
    9. Legen Sie **die Farbe** auf **#FFFFFFFF**

    ![Textkomponente](images/AzureLabs-Lab2-21-5.png)

3.  Ziehen Sie **LabelText** aus dem *Hierarchiebereich* in den *Objektordner* in Project *Bereich*. Dadurch wird **labelText zu** einem Prefab, sodass es im Code instanziiert werden kann.

    ![Erstellen Sie ein Prefab des LabelText-Objekts.](images/AzureLabs-Lab2-22.png)
 
4.  Sie sollten **LabelText aus dem** *Hierarchiebereich löschen,* damit es nicht in der öffnenden Szene angezeigt wird. Da es sich jetzt um ein Prefab handelt, das Sie für einzelne Instanzen aus Ihrem Ordner Assets aufrufen, ist es nicht notwendig, es innerhalb der Szene zu behalten. 
5.  Die endgültige Objektstruktur im *Hierarchiebereich* sollte der in der folgenden Abbildung gezeigten strukturieren:

    ![Endgültige Struktur des Hierarchiebereichs.](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a>Kapitel 5: Erstellen der ResultsLabel-Klasse

Das erste Skript, das Sie erstellen müssen, ist die *ResultsLabel-Klasse,* die für Folgendes zuständig ist: 

- Erstellen der Bezeichnungen im entsprechenden Weltraum relativ zur Position der Kamera.
- Anzeigen der Tags aus dem Bild-Anaysis.

So erstellen Sie diese Klasse: 

1.  Klicken Sie mit der rechten Maustaste in den *Project Bereich,* und **erstellen Sie dann > Ordner**. Nennen Sie den Ordner **Skripts**. 

    ![Erstellen Sie den Ordner skripts.](images/AzureLabs-Lab2-24.png)

2.  Doppelklicken Sie beim Erstellen des **Ordners Scripts** darauf, um ihn zu öffnen. Klicken Sie dann in diesem Ordner mit der rechten Maustaste, und wählen **Sie erstellen >** dann **C#-Skript** aus. Nennen Sie das Skript *ResultsLabel*. 

3.  Doppelklicken Sie auf das neue *ResultsLabel-Skript,* um es mit **Visual Studio** zu öffnen.

4.  Fügen Sie in der Klasse den folgenden Code in die *ResultsLabel-Klasse* ein:

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;

        public class ResultsLabel : MonoBehaviour
        {   
            public static ResultsLabel instance;

            public GameObject cursor;

            public Transform labelPrefab;

            [HideInInspector]
            public Transform lastLabelPlaced;

            [HideInInspector]
            public TextMesh lastLabelPlacedText;

            private void Awake()
            {
                // allows this instance to behave like a singleton
                instance = this;
            }

            /// <summary>
            /// Instantiate a Label in the appropriate location relative to the Main Camera.
            /// </summary>
            public void CreateLabel()
            {
                lastLabelPlaced = Instantiate(labelPrefab, cursor.transform.position, transform.rotation);

                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // Change the text of the label to show that has been placed
                // The final text will be set at a later stage
                lastLabelPlacedText.text = "Analysing...";
            }

            /// <summary>
            /// Set the Tags as Text of the last Label created. 
            /// </summary>
            public void SetTagsToLastLabel(Dictionary<string, float> tagsDictionary)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // At this point we go through all the tags received and set them as text of the label
                lastLabelPlacedText.text = "I see: \n";

                foreach (KeyValuePair<string, float> tag in tagsDictionary)
                {
                    lastLabelPlacedText.text += tag.Key + ", Confidence: " + tag.Value.ToString("0.00 \n");
                }    
            }
        }
    ```

6.  Speichern Sie Ihre Änderungen in *Visual Studio,* bevor Sie zu *Unity* zurückkehren.
7.  Klicken Sie im *Unity-Editor* zurück, und ziehen Sie die *ResultsLabel-Klasse* aus dem Ordner **Scripts** in das **Objekt Main Camera** im *Hierarchiebereich*.
8.  Klicken Sie auf die **Hauptkamera,** und sehen Sie sich den *Inspektorbereich an.*

Sie werden feststellen, dass es aus dem Skript, das Sie gerade in die Kamera gezogen haben, zwei Felder gibt: **Cursor** und **Label Prefab**.

9.  Ziehen Sie das Objekt **cursor** aus dem *Hierarchiebereich* in den Slot **cursor**, wie in der folgenden Abbildung dargestellt.
10. Ziehen Sie das Objekt **labelText** aus dem *Ordner Assets* im *Project Panel* in den Slot **Label Prefab**, wie in der folgenden Abbildung dargestellt. 

    ![Legen Sie die Verweisziele in Unity fest.](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a>Kapitel 6 : Erstellen der ImageCapture-Klasse

Die nächste Klasse, die Sie erstellen werden, ist die *ImageCapture-Klasse.* Diese Klasse ist für Dies ist verantwortlich für:

-   Erfassen eines Bilds mithilfe der HoloLens Kamera und Speichern im App-Ordner.
-   Erfassen von Tippgesten vom Benutzer.

So erstellen Sie diese Klasse: 

1.  Wechseln Sie zum Ordner **Skripts,** den Sie zuvor erstellt haben. 
2.  Klicken Sie mit der rechten Maustaste in den Ordner **Create > C#-Skript.** Rufen Sie das Skript *ImageCapture* auf. 
3.  Doppelklicken Sie auf das neue *ImageCapture-Skript,* um es mit **Visual Studio** zu öffnen.
4.  Fügen Sie am Anfang der Datei die folgenden Namespaces hinzu:

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  Fügen Sie dann die folgenden Variablen in der *ImageCapture-Klasse* oberhalb der *Start()-Methode* hinzu:

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
Die **Variable tapsCount** speichert die Anzahl der tippgesten, die vom Benutzer erfasst wurden. Diese Zahl wird bei der Benennung der erfassten Bilder verwendet.

6.  Code für *die Methoden "Awake()"* und *"Start()"* muss jetzt hinzugefügt werden. Diese werden aufgerufen, wenn die -Klasse initialisiert wird:

    ```csharp
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            // subscribing to the HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  Implementieren Sie einen Handler, der aufgerufen wird, wenn eine Tippbewegung auftritt. 

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            // Only allow capturing, if not currently processing a request.
            if(currentlyCapturing == false)
            {
                currentlyCapturing = true;
            
                // increment taps count, used to name images when saving
                tapsCount++;

                // Create a label in world space using the ResultsLabel class
                ResultsLabel.instance.CreateLabel();

                // Begins the image capture and analysis procedure
                ExecuteImageCaptureAndAnalysis();
            }
        }
    ```
 
Die *TapHandler()-Methode* erhöht die Anzahl der vom Benutzer erfassten Tippen und verwendet die aktuelle Cursorposition, um zu bestimmen, wo eine neue Bezeichnung positioniert werden soll.

Diese Methode ruft dann die *ExecuteImageCaptureAndAnalysis()-Methode* auf, um die Kernfunktionalität dieser Anwendung zu starten.

8.  Sobald ein Image erfasst und gespeichert wurde, werden die folgenden Handler aufgerufen. Wenn der Prozess erfolgreich ist, wird das Ergebnis zur Analyse an den *VisionManager* übergeben (den Sie noch erstellen müssen).

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin 
        /// the Image Analysis process.
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            // Call StopPhotoMode once the image has successfully captured
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            // Dispose from the object in memory and request the image analysis 
            // to the VisionManager class
            photoCaptureObject.Dispose();
            photoCaptureObject = null;
            StartCoroutine(VisionManager.instance.AnalyseLastImageCaptured()); 
        }
    ```
 
9.  Fügen Sie dann die Methode hinzu, die die Anwendung verwendet, um den Imageerfassungsprozess zu starten und das Image zu speichern.

    ```csharp    
        /// <summary>    
        /// Begin process of Image Capturing and send To Azure     
        /// Computer Vision service.   
        /// </summary>    
        private void ExecuteImageCaptureAndAnalysis()  
        {    
            // Set the camera resolution to be the highest possible    
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();    

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
    
            // Begin capture process, set the image format    
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)    
            {    
                photoCaptureObject = captureObject;    
                CameraParameters camParameters = new CameraParameters();    
                camParameters.hologramOpacity = 0.0f;    
                camParameters.cameraResolutionWidth = targetTexture.width;    
                camParameters.cameraResolutionHeight = targetTexture.height;    
                camParameters.pixelFormat = CapturePixelFormat.BGRA32;
    
                // Capture the image from the camera and save it in the App internal folder    
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {    
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
    
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    VisionManager.instance.imagePath = filePath;
    
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);

                    currentlyCapturing = false;
                });   
            });    
        }
    ```
 
> [!WARNING] 
> An diesem Punkt wird im *Konsolenbereich des Unity-Editors* ein Fehler angezeigt. Dies liegt daran, dass der Code auf die *VisionManager-Klasse* verweist, die Sie im nächsten Kapitel erstellen werden.

## <a name="chapter-7--call-to-azure-and-image-analysis"></a>Kapitel 7– Aufrufen von Azure und Bildanalyse

Das letzte Skript, das Sie erstellen müssen, ist die *VisionManager-Klasse.* 

Diese Klasse ist für Dies ist verantwortlich für:

-   Laden des neuesten Images, das als Bytearray erfasst wurde.
-   Senden des Bytearrays an Ihre *Azure maschinelles Sehen API Service-Instanz* zur Analyse.
-   Empfangen der Antwort als JSON-Zeichenfolge.
-   Deserialisieren der Antwort und Übergeben der resultierenden Tags an die *ResultsLabel-Klasse.*
 
So erstellen Sie diese Klasse:

1.  Doppelklicken Sie auf den Ordner **Skripts,** um ihn zu öffnen. 
2.  Klicken Sie mit der rechten Maustaste in den Ordner **Skripts,** und klicken Sie auf **> C#-Skript erstellen.** Nennen Sie das Skript *VisionManager*. 
3.  Doppelklicken Sie auf das neue Skript, um es mit Visual Studio zu öffnen.
4.  Aktualisieren Sie die Namespaces am Anfang der *VisionManager-Klasse* so, dass sie den folgenden entsprechen:

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  Am Anfang Ihres Skripts *innerhalb* der *VisionManager-Klasse* (oberhalb der *Start()-Methode)* müssen Sie nun zwei *Klassen* erstellen, die die deserialisierte JSON-Antwort von Azure darstellen:

    ```csharp
        [System.Serializable]
        public class TagData
        {
            public string name;
            public float confidence;
        }

        [System.Serializable]
        public class AnalysedObject
        {
            public TagData[] tags;
            public string requestId;
            public object metadata;
        }
    ```

    > [!NOTE] 
    > Für die *Klassen TagData* und *Analyseobjekt* muss das *Attribut [System.Serializable]* vor der Deklaration hinzugefügt werden, damit sie mit den Unity-Bibliotheken deserialisiert werden kann.

6.  In der VisionManager-Klasse sollten Sie die folgenden Variablen hinzufügen:

    ```csharp
        public static VisionManager instance;

        // you must insert your service key here!    
        private string authorizationKey = "- Insert your key here -";    
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key";
        private string visionAnalysisEndpoint = "https://westus.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags";   // This is where you need to update your endpoint, if you set your location to something other than west-us.
  
        internal byte[] imageBytes;

        internal string imagePath;
    ```

    > [!WARNING] 
    > Stellen Sie sicher, dass Sie Ihren **Authentifizierungsschlüssel** in die **Variable authorizationKey** einfügen. Sie haben ihren **Authentifizierungsschlüssel** zu Beginn dieses Kurses, [Kapitel 1,](#chapter-1--the-azure-portal)notiert.

    > [!WARNING] 
    > Die **visionAnalysisEndpoint-Variable** kann sich von der in diesem Beispiel angegebenen unterscheiden. Usa, **Westen** bezieht sich ausschließlich auf Dienstinstanzen, die für die Region "USA, Westen" erstellt wurden. Aktualisieren Sie dies mit Ihrer [Endpunkt-URL.](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa) Hier sind einige Beispiele dafür aufgeführt, wie dies aussehen kann:
    > - Europa, Westen: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - Südostasien: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - Australien, Osten: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`

7.  Code für "Awake" muss jetzt hinzugefügt werden. 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  Fügen Sie als Nächstes die Coroutine hinzu (mit der statischen Streammethode darunter), die die Ergebnisse der Analyse des von der *ImageCapture-Klasse* erfassten Bilds erhält. 

    ```csharp
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured()
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(visionAnalysisEndpoint, webForm))
            {
                // gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);
                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader(ocpApimSubscriptionKeyHeader, authorizationKey);

                // the download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // the upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;     

                try
                {
                    string jsonResponse = null;
                    jsonResponse = unityWebRequest.downloadHandler.text;

                    // The response will be in Json format
                    // therefore it needs to be deserialized into the classes AnalysedObject and TagData
                    AnalysedObject analysedObject = new AnalysedObject();
                    analysedObject = JsonUtility.FromJson<AnalysedObject>(jsonResponse);

                    if (analysedObject.tags == null)
                    {
                        Debug.Log("analysedObject.tagData is null");
                    }
                    else
                    {
                        Dictionary<string, float> tagsDictionary = new Dictionary<string, float>();

                        foreach (TagData td in analysedObject.tags)
                        {
                            TagData tag = td as TagData;
                            tagsDictionary.Add(tag.name, tag.confidence);                            
                        }

                        ResultsLabel.instance.SetTagsToLastLabel(tagsDictionary);
                    }
                }
                catch (Exception exception)
                {
                    Debug.Log("Json exception.Message: " + exception.Message);
                }

                yield return null;
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        private static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }  
    ```

9.  Speichern Sie Ihre Änderungen in *Visual Studio,* bevor Sie zu *Unity* zurückkehren.
10. Klicken Sie im Unity-Editor zurück, und ziehen Sie die Klassen *VisionManager* und *ImageCapture* aus dem Ordner **Scripts** in das **Objekt Hauptkamera** im *Hierarchiebereich.* 

## <a name="chapter-8--before-building"></a>Kapitel 8 – Vor dem Erstellen

Um einen gründlichen Test Ihrer Anwendung durchzuführen, müssen Sie sie auf Ihre HoloLens querladen.
Stellen Sie zuvor Sicher, dass:

-   Alle in [Kapitel 2](#chapter-2--set-up-the-unity-project) erwähnten Einstellungen sind ordnungsgemäß festgelegt. 
-   Alle Skripts werden an das **Hauptkameraobjekt** angefügt. 
-   Alle Felder im *Hauptbereich des Kamerainspektors* sind ordnungsgemäß zugewiesen.
-   Stellen Sie sicher, dass Sie Ihren **Authentifizierungsschlüssel** in die **Variable authorizationKey** einfügen.
-   Stellen Sie sicher, dass Sie ihren Endpunkt auch in Ihrem *VisionManager-Skript* überprüft haben und dass er an *Ihrer* Region ausgerichtet ist (in diesem Dokument wird standardmäßig *west-us* verwendet).

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a>Kapitel 9: Erstellen der UWP-Lösung und Querladen der Anwendung
Alles, was für den Unity-Abschnitt dieses Projekts erforderlich ist, wurde nun abgeschlossen, daher ist es an der Zeit, es aus Unity zu erstellen.

1.  Navigieren Sie zu *Build Einstellungen* File >  -  **Build Einstellungen...**
2.  Klicken *Sie* im Fenster Build Einstellungen auf **Erstellen.**

    ![Erstellen der App aus Unity](images/AzureLabs-Lab2-26.png)

3.  Falls nicht bereits, aktivieren Sie **Unity C#-Projekte.**
4.  Klicken Sie auf **Erstellen**. Unity startet ein *Datei-Explorer-Fenster,* in dem Sie erstellen und dann einen Ordner auswählen müssen, in dem die App erstellt werden soll. Erstellen Sie diesen Ordner jetzt, und nennen Sie ihn *App*. Wenn Sie dann den Ordner *App* ausgewählt haben, klicken Sie auf **Ordner auswählen.** 
5.  Unity beginnt mit dem Erstellen Ihres Projekts im Ordner *App.* 
6.  Sobald Unity die Erstellung abgeschlossen hat (es kann einige Zeit dauern), öffnet es ein *Datei-Explorer-Fenster* am Speicherort Ihres Builds (überprüfen Sie die Taskleiste, da sie möglicherweise nicht immer über Ihren Fenstern angezeigt wird, Sie aber über das Hinzufügen eines neuen Fensters benachrichtigt werden).

## <a name="chapter-10--deploy-to-hololens"></a>Kapitel 10 – Bereitstellen in HoloLens

So stellen Sie auf HoloLens bereit:

1.  Sie benötigen die IP-Adresse Ihrer HoloLens (für Remote Deploy) und stellen sicher, dass sich Ihre HoloLens im **Entwicklermodus befindet.** Aufgabe:

    1. Öffnen Sie während der HoloLens die **Einstellungen**.
    2. Wechseln Sie zu **Netzwerk & Internet > Wi-Fi > Erweiterte Optionen.**
    3. Notieren Sie sich die **IPv4-Adresse.**
    4. Navigieren Sie als Nächstes zurück zu **Einstellungen** und dann zu **& Security > For Developers aktualisieren.** 
    5. Legen Sie den Entwicklermodus auf Ein fest.

2.  Navigieren Sie zu Ihrem neuen Unity-Build (dem *Ordner App),* und öffnen Sie die Projektmappendatei mit *Visual Studio*.
3.  Wählen Sie in der Projektmappenkonfiguration **Debuggen aus.**
4.  Wählen Sie auf der Projektmappenplattform **x86**, **Remotecomputer aus.** 

    ![Stellen Sie die Lösung über Visual Studio.](images/AzureLabs-Lab2-27.png)
 
5.  Wechseln Sie zum **Menü Erstellen,** und klicken Sie auf **Projektmappe bereitstellen,** um die Anwendung in Ihre HoloLens.
6.  Ihre App sollte nun in der Liste der installierten Apps auf Ihrer HoloLens angezeigt werden, die zum Start bereit sind!

> [!NOTE]
> Legen Sie zum Bereitstellen für immersive Headsets die  **Projektmappenplattform** auf *Lokaler* Computer und die Konfiguration auf *Debuggen* mit *x86* als Plattform **fest.** Stellen Sie dann auf dem lokalen Computer mithilfe des **Menüs Erstellen die** Option *Projektmappe bereitstellen aus.* 

## <a name="your-finished-computer-vision-api-application"></a>Ihre fertige maschinelles Sehen-API-Anwendung

Herzlichen Glückwunsch! Sie haben eine Mixed Reality-App erstellt, die die Azure maschinelles Sehen-API nutzt, um reale Objekte zu erkennen und Dies zu zeigen, was sie gesehen haben.

![Labergebnis](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a>Zusatzübungen

### <a name="exercise-1"></a>Übung 1

Erweitern Sie die App so, wie Sie  den *Tags-Parameter* verwendet haben (wie innerhalb des endpunkts, der in *VisionManager* verwendet wird), um andere Informationen zu erkennen. Sehen Sie sich an, welche anderen Parameter Sie zugriff auf [HERE haben.](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)

### <a name="exercise-2"></a>Übung 2

Zeigen Sie die zurückgegebenen Azure-Daten konversations- und lesbarer an, und verbergen Sie möglicherweise die Zahlen. Als würde ein Bot mit dem Benutzer sprechen.