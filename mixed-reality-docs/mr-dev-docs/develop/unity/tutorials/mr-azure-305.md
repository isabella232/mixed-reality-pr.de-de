---
title: 'HoloLens (1. Generation) und Azure 305: Funktionen und Speicher'
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie sie Azure Storage und Funktionen in einer Mixed Reality-Anwendung implementieren.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, Tutorial, API, Funktionen, Speicher, HoloLens, immersive, VR, Windows 10, Visual Studio
ms.openlocfilehash: 337b1d3fb23450325805237a6ba975861260760b7d37028b8d717bad99b9d233
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193945"
---
# <a name="hololens-1st-gen-and-azure-305-functions-and-storage"></a>HoloLens (1. Generation) und Azure 305: Funktionen und Speicher

<br>

>[!NOTE]
>Die Tutorials der Mixed Reality Academy wurden im Hinblick auf HoloLens (1. Gen.) und immersive Mixed Reality-Headsets entworfen.  Daher halten wir es für wichtig, diese Tutorials für Entwickler verfügbar zu halten, die noch nach Anleitung beim Entwickeln für diese Geräte suchen.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für HoloLens 2 verwendet werden.  Sie werden gewartet, um weiterhin auf den unterstützten Geräten zu funktionieren. Es wird eine neue Reihe von Tutorials geben, die in Zukunft veröffentlicht werden, die veranschaulichen, wie sie für HoloLens 2 entwickelt werden.  Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn sie veröffentlicht werden.

<br> 

![final product -start](images/AzureLabs-Lab5-00.png)

In diesem Kurs erfahren Sie, wie Sie Azure Functions erstellen und verwenden und Daten mit einer Azure Storage Ressource in einer Mixed Reality-Anwendung speichern.

*Azure Functions* ist ein Microsoft-Dienst, mit dem Entwickler kleine Codeteile ( "Functions") in Azure ausführen können. Dies bietet eine Möglichkeit, Arbeit an die Cloud zu delegieren, anstatt an Ihre lokale Anwendung, was viele Vorteile haben kann. *Azure Functions* unterstützt mehrere Entwicklungssprachen, einschließlich \# C, \# F, Node.js, Java und PHP. Weitere Informationen finden Sie im [Azure Functions Artikel](/azure/azure-functions/functions-overview).

*Azure Storage* ist ein Microsoft-Clouddienst, der Es Entwicklern ermöglicht, Daten zu speichern, mit der Versicherungslösung, dass sie hochverfükbar, sicher, dauerhaft, skalierbar und redundant sein werden. Dies bedeutet, dass Microsoft alle Wartungsaufgaben und kritischen Probleme für Sie übernimmt. Weitere Informationen finden Sie im [Azure Storage Artikel](/azure/storage/common/storage-introduction).

Nach Abschluss dieses Kurses verfügen Sie über eine Immersive Headset-Mixed Reality-Anwendung, die folgende Schritte ausführen kann:

1.  Erlauben Sie dem Benutzer, eine Szene zu betrachten.
2.  Lösen Sie das Erstellen von Objekten aus, wenn der Benutzer eine 3D-Schaltfläche anviert.
3.  Die ausgelösten Objekte werden von einer Azure-Funktion ausgewählt.
4.  Wenn jedes Objekt entsteht, speichert die Anwendung den Objekttyp in einer *Azure-Datei,* die sich in *Azure Storage* befindet.
5.  Beim zweiten Laden werden die *Azure-Dateidaten* abgerufen und verwendet, um die erzeugten Aktionen aus der vorherigen Instanz der Anwendung wiederzugeben.

In Ihrer Anwendung liegt es an Ihnen, wie Sie die Ergebnisse in Ihren Entwurf integrieren. In diesem Kurs erfahren Sie, wie Sie einen Azure-Dienst in Ihre Unity-Project integrieren. Es ist Ihre Aufgabe, das Wissen zu nutzen, das Sie aus diesem Kurs gewinnen, um Ihre Mixed Reality-Anwendung zu verbessern.

## <a name="device-support"></a>Geräteunterstützung

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td>MR und Azure 305: Funktionen und Speicher</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Während sich dieser Kurs hauptsächlich auf Windows Mixed Reality immersiven Headsets (VR) konzentriert, können Sie auch das, was Sie in diesem Kurs lernen, auf Microsoft HoloLens anwenden. Während Sie den Kurs durchgehen, werden Ihnen Hinweise zu allen Änderungen angezeigt, die Sie ggf. zur Unterstützung HoloLens verwenden müssen.

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
- Ein Abonnement für ein Azure-Konto zum Erstellen von Azure-Ressourcen
- Internetzugriff für Azure-Setup und Datenabruf

## <a name="before-you-start"></a>Vorbereitung

Um Probleme bei der Erstellung dieses Projekts zu vermeiden, wird dringend empfohlen, das in diesem Tutorial erwähnte Projekt in einem Stammordner oder in einem Ordner in der Nähe des Stammordners zu erstellen (lange Ordnerpfade können zur Buildzeit Probleme verursachen).

## <a name="chapter-1---the-azure-portal"></a>Kapitel 1: Das Azure-Portal

Um den **Azure Storage-Dienst** zu verwenden, müssen Sie im Azure-Portal ein **Storage-Konto** erstellen und konfigurieren.

1.  Melden Sie sich beim  [Azure-Portal](https://portal.azure.com)an.

    > [!NOTE]
    > Wenn Sie noch nicht über ein Azure-Konto verfügen, müssen Sie eins erstellen. Wenn Sie dieses Tutorial in einer Classroom- oder Lab-Situation durchgehen, bitten Sie Ihren Dozenten oder einen der Proctors um Hilfe beim Einrichten Ihres neuen Kontos.

2.  Klicken Sie nach der Anmeldung oben links auf **Neu,** suchen Sie *nach Storage Konto,* und drücken **Sie die EINGABETASTE.**

    ![Azure Storage-Suche](images/AzureLabs-Lab5-01.png)

    > [!NOTE]
    > Das Wort **Neu** wurde in neueren Portalen möglicherweise durch **Ressource erstellen** ersetzt.

3.  Die neue Seite enthält eine Beschreibung des *Azure Storage-Kontodiensts.* Wählen Sie unten links in dieser Eingabeaufforderung die Schaltfläche **Erstellen** aus, um eine Zuordnung zu diesem Dienst zu erstellen.

    ![Erstellen eines Diensts](images/AzureLabs-Lab5-02.png)

4.  Nachdem Sie auf **Erstellen** geklickt haben:

    1.  Fügen Sie einen *Namen* für Ihr Konto ein. Beachten Sie, dass dieses Feld nur Zahlen und Kleinbuchstaben akzeptiert.

    2.  Wählen Sie unter *Bereitstellungsmodell* die Option **Resource Manager** aus.

    3.  Wählen Sie unter *Kontoart* die Option **Storage (Allgemein v1)** aus.

    4.  Bestimmen Sie den *Speicherort* für Ihre Ressourcengruppe (wenn Sie eine neue Ressourcengruppe erstellen). Der Standort befindet sich idealerweise in der Region, in der die Anwendung ausgeführt wird. Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.

    5.  Wählen Sie unter *Replikation* die Option **Georedundanter Speicher mit Lesezugriff (RA-GRS)** aus.

    6.  Wählen Sie für *Leistung* die Option **Standard** aus.

    7.  Belassen Sie *Sichere Übertragung erforderlich* als **Deaktiviert.**

    8.  Wählen Sie ein *Abonnement* aus.

    9. Wählen Sie eine *Ressourcengruppe* aus, oder erstellen Sie eine neue. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, Steuern des Zugriffs, Bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt zugeordnet sind (z. B. diese Labs), in einer gemeinsamen Ressourcengruppe zu speichern. 

        > Weitere Informationen zu Azure-Ressourcengruppen finden Sie [im Artikel zu Ressourcengruppen.](/azure/azure-resource-manager/resource-group-portal)

    10. Sie müssen auch bestätigen, dass Sie die für diesen Dienst geltenden Geschäftsbedingungen verstanden haben.

    11. Klicken Sie auf **Erstellen**.

        ![Eingabedienstinformationen](images/AzureLabs-Lab5-03.png)

5.  Nachdem Sie auf **Erstellen** geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. Dies kann eine Minute dauern.

6.  Sobald die Dienstinstanz erstellt wurde, wird eine Benachrichtigung im Portal angezeigt.

    ![Neue Benachrichtigung im Azure-Portal](images/AzureLabs-Lab5-04.png)

7.  Klicken Sie auf die Benachrichtigungen, um Ihre neue Dienstinstanz zu untersuchen.

    ![Zu Ressource wechseln](images/AzureLabs-Lab5-05.png)

8.  Klicken Sie in der Benachrichtigung auf die Schaltfläche **Zu Ressource** wechseln, um Ihre neue Dienstinstanz zu untersuchen. Sie werden zu Ihrer neuen *Storage-Kontodienstinstanz* gebracht.

    ![Zugriffsschlüssel](images/AzureLabs-Lab5-06.png)

9.  Klicken Sie auf *Zugriffsschlüssel*, um die Endpunkte für diesen Clouddienst offenzulegen. Verwenden Sie *Editor* oder ähnliches, um einen Ihrer Schlüssel zur späteren Verwendung zu kopieren. Beachten Sie außerdem den Wert *der Verbindungszeichenfolge,* da er in der *AzureServices-Klasse* verwendet wird, die Sie später erstellen.

    ![Kopieren der Verbindungszeichenfolge](images/AzureLabs-Lab5-07.png)

## <a name="chapter-2---setting-up-an-azure-function"></a>Kapitel 2: Einrichten einer Azure-Funktion

Sie schreiben jetzt eine  **Azure-Funktion** in den Azure-Dienst.

Sie können eine **Azure-Funktion** verwenden, um nahezu alles zu tun, was Sie mit einer klassischen Funktion in Ihrem Code tun würden. Der Unterschied ist, dass jede Anwendung, die über Anmeldeinformationen für den Zugriff auf Ihr Azure-Konto verfügt, auf diese Funktion zugreifen kann.

So erstellen Sie eine Azure-Funktion:

1.  Klicken Sie im *Azure-Portal* oben links auf **Neu,** suchen Sie nach *Funktions-App,* und drücken **Sie die EINGABETASTE.**

    ![Erstellen einer Funktions-App](images/AzureLabs-Lab5-08.png)

    > [!NOTE]
    > Das Wort **Neu** wurde in neueren Portalen möglicherweise durch **Ressource erstellen** ersetzt.

2.  Die neue Seite enthält eine Beschreibung des *Azure-Funktions-App-Diensts.* Wählen Sie unten links in dieser Eingabeaufforderung die Schaltfläche **Erstellen** aus, um eine Zuordnung zu diesem Dienst zu erstellen.

    ![Funktions-App-Informationen](images/AzureLabs-Lab5-09.png)

3.  Nachdem Sie auf Erstellen geklickt **haben:**

    1.  Geben Sie einen *App-Namen an.* Hier können nur Buchstaben und Zahlen verwendet werden (Groß- oder Kleinbuchstaben sind zulässig).

    2.  Wählen Sie Ihr bevorzugtes *Abonnement aus.*

    3. Wählen Sie eine *Ressourcengruppe aus,* oder erstellen Sie eine neue. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, Steuern des Zugriffs, Bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. B. diesen Labs) zugeordnet sind, unter einer gemeinsamen Ressourcengruppe zu halten. 

        > Weitere Informationen zu Azure-Ressourcengruppen finden Sie im Artikel [zu Ressourcengruppen.](/azure/azure-resource-manager/resource-group-portal)

    4.  Wählen Sie für diese *Übung* Windows als ausgewähltes Betriebssystem **aus.**

    5.  Wählen Sie *unter Hostingplan* die Option **Verbrauchsplan aus.**

    6.  Bestimmen Sie *den Standort* für Ihre Ressourcengruppe (wenn Sie eine neue Ressourcengruppe erstellen). Der Standort befindet sich idealerweise in der Region, in der die Anwendung ausgeführt wird. Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar. Um eine optimale Leistung zu erzielen, wählen Sie dieselbe Region wie das Speicherkonto aus.

    7.  Wählen *Storage* vorhandene **verwenden** aus, und suchen Sie dann über das Dropdownmenü nach Dem zuvor erstellten Speicher.

    8.  Lassen *Sie Insights* für diese Übung deaktiviert.

        ![Details der Eingabefunktions-App](images/AzureLabs-Lab5-10.png)

4.  Klicken Sie auf die Schaltfläche **Erstellen**.

5.  Nachdem Sie auf **Erstellen** geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. Dies kann eine Minute dauern.

6.  Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.

    ![Benachrichtigung über das neue Azure-Portal](images/AzureLabs-Lab5-11.png)

7.  Klicken Sie auf die Benachrichtigungen, um Ihre neue Dienstinstanz zu untersuchen. 

    ![Zur Ressourcenfunktions-App wechseln](images/AzureLabs-Lab5-12.png)

8.  Klicken Sie in **der Benachrichtigung auf die** Schaltfläche Zu Ressource wechseln, um Ihre neue Dienstinstanz zu untersuchen. Sie werden zu Ihrer neuen Instanz des *Funktions-App-Diensts* aufgenommen.

9.  Bewegen Sie *auf dem Dashboard* der Funktions-App den Mauszeiger auf *Functions*, die sich im Bereich auf der linken Seite finden, und klicken Sie dann auf das Symbol **+ (Pluszeichen).**

    ![Erstellen einer neuen Funktion](images/AzureLabs-Lab5-13.png)

10. Stellen Sie auf der nächsten Seite sicher, dass **Webhook + API** ausgewählt ist, und wählen Sie für Sprache auswählen die Option **CSharp** aus, da dies die Sprache *ist,* die für dieses Tutorial verwendet wird. Klicken Sie abschließend auf die **Schaltfläche Diese Funktion** erstellen.

    ![Webhook-Csharp auswählen](images/AzureLabs-Lab5-14.png)

11. Sie sollten zur Codepage (run.csx) übergeführt werden. Falls nicht, klicken Sie in der Liste Funktionen im Bereich auf der linken Seite auf die neu erstellte Funktion.

    ![Neue Funktion öffnen](images/AzureLabs-Lab5-15.png)

12. Kopieren Sie den folgenden Code in Ihre Funktion. Diese Funktion gibt einfach eine zufällige ganze Zahl zwischen 0 und 2 zurück, wenn sie aufgerufen wird. Machen Sie sich keine Gedanken über den vorhandenen Code. Fügen Sie ihn ganz oben ein.

    ```csharp
        using System.Net;
        using System.Threading.Tasks;

        public static int Run(CustomObject req, TraceWriter log)
        {
            Random rnd = new Random();
            int randomInt = rnd.Next(0, 3);
            return randomInt;
        }

        public class CustomObject
        {
            public String name {get; set;}
        }
    ```

13. Wählen Sie **Speichern** aus.

14. Das Ergebnis sollte wie in der folgenden Abbildung aussehen.

15. Klicken Sie auf **Funktions-URL erhalten,** und notieren Sie sich den *angezeigten* Endpunkt. Sie müssen sie in die *AzureServices-Klasse* einfügen, die Sie später in diesem Kurs erstellen.

    ![Funktionsendpunkt erhalten](images/AzureLabs-Lab5-16.png)

    ![Einfügen des Funktionsendpunkts](images/AzureLabs-Lab5-16-5.png)

## <a name="chapter-3---setting-up-the-unity-project"></a>Kapitel 3: Einrichten des Unity-Projekts

Im Folgenden finden Sie eine typische Einrichtung für die Entwicklung mit Mixed Reality und ist daher eine gute Vorlage für andere Projekte.

Richten Sie Ihr immersives Mixed Reality-Headset ein, und testen Sie es.

> [!NOTE]
> Für diesen **Kurs** sind keine Motion Controller erforderlich. Wenn Sie Unterstützung beim Einrichten des immersiven Headsets benötigen, lesen Sie den [Artikel Mixed Reality-Einrichtung.](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)

1.  Öffnen Sie Unity, und klicken Sie **auf Neu.**

    ![Erstellen eines neuen Unity-Projekts](images/AzureLabs-Lab5-17.png)

2.  Sie müssen nun einen Unity-Project angeben. Fügen **Sie MR_Azure_Functions** ein. Stellen Sie sicher, dass der Projekttyp auf **3D festgelegt ist.** Legen Sie *den Speicherort* auf einen für Sie geeigneten Speicherort fest (denken Sie daran, dass die Nähe zu Stammverzeichnissen besser ist). Klicken Sie dann auf **Projekt erstellen.**

    ![Benennen eines neuen Unity-Projekts](images/AzureLabs-Lab5-18.png)

3.  Wenn Unity geöffnet ist, sollte überprüft werden, ob der **Standardskript-Editor** auf **Visual Studio.** Wechseln Sie **zu**  >  **Einstellungen bearbeiten,** und navigieren Sie dann im neuen Fenster zu Externe **Tools.** Ändern **Sie den editor für externe** **Skripts in Visual Studio 2017**. Schließen Sie das **Fenster Einstellungen.**

    ![Festlegen von Visual Studio als Skript-Editor](images/AzureLabs-Lab5-19.png)

4.  Wechseln Sie als Nächstes **zu Datei** Einstellungen, und wechseln Sie zur  >   Universelle **Windows-Plattform,** indem Sie auf die **Schaltfläche Plattform wechseln** klicken.

    ![Wechseln der Plattform zu UWP](images/AzureLabs-Lab5-20.png)

5.  Wechseln Sie **zu**  >  **Datei Einstellungen,** und stellen Sie Sicher, dass:

    1. **Das Zielgerät** ist auf **Beliebiges Gerät festgelegt.**

        > Legen Microsoft HoloLens Zielgerät **auf** *HoloLens.*

    2. **Buildtyp** ist auf **D3D festgelegt**

    3. **SDK** ist auf **Latest installed (Neueste installiert) festgelegt.**

    4. **Visual Studio version** ist auf **Latest installed (Neueste installiert) festgelegt.**

    5. **Erstellen und Ausführen** ist auf Lokaler **Computer festgelegt.**

    6. Speichern Sie die Szene, und fügen Sie sie dem Build hinzu.

        1.  Wählen Sie hierzu Geöffnete Szenen **hinzufügen aus.** Ein Speicherfenster wird angezeigt.

            ![Hinzufügen von offenen Szenen](images/AzureLabs-Lab5-21.png)

        2.  Erstellen Sie einen neuen Ordner für diesen und jede  zukünftige Szene, und wählen Sie dann die Schaltfläche Neuer Ordner aus, um einen neuen Ordner zu erstellen, und nennen Sie **ihn Scenes**.

            ![Ordner "Szenen erstellen"](images/AzureLabs-Lab5-22.png)

        3.  Öffnen Sie den neu erstellten **Ordner Scenes,** und geben Sie dann im Feld **Dateiname:** Text den Namen **FunctionsScene** ein, und klicken Sie dann **auf Speichern.**

            ![Speichern der Funktionsszene](images/AzureLabs-Lab5-23.png)

6.  Die restlichen Einstellungen in **Build Einstellungen** sollten vorerde als Standardeinstellung be übrig bleiben.

    ![Belasse die Standard-Buildeinstellungen.](images/AzureLabs-Lab5-24.png)

7.  Klicken Sie *im Fenster Build Einstellungen* auf die Schaltfläche Player **Einstellungen,** um den entsprechenden Bereich in dem Bereich zu öffnen, in dem sich der *Inspektor* befindet.

    ![Playereinstellungen im Inspektor](images/AzureLabs-Lab5-25.png)

8.  In diesem Bereich müssen einige Einstellungen überprüft werden:

    1.  Führen Sie **auf Einstellungen** Registerkarte Andere Optionen aus:

        1.  **Die Skriptlaufzeitversion** sollte **experimentell** sein (.NET 4.6-Entsprechung), wodurch ein Neustart des Editors ausgelöst wird.
        2.  **Das Skript-Back-End** sollte **.NET sein.**
        3.  **Der API-Kompatibilitätsgrad** sollte **.NET 4.6 sein.**

    2.  Aktivieren Sie **auf Einstellungen** Registerkarte Publishing Einstellungen unter **Capabilities (Funktionen)** Die folgenden Optionen:
        
        -  **InternetClient**

            ![Festlegen von Funktionen](images/AzureLabs-Lab5-26.png)

    3.  Aktivieren Sie weiter unten im Bereich in **XR Einstellungen** (unter Publishing **Einstellungen)** **(Virtual Reality** unterstützt), und stellen Sie sicher, dass das Windows Mixed Reality **SDK** hinzugefügt wird.

        ![Festlegen von XR-Einstellungen](images/AzureLabs-Lab5-27.png)

9.  Zurück in *Build Einstellungen* *Unity C#-Projekte* ist nicht mehr ausgegraut. aktivieren Sie das Kontrollkästchen daneben.

    ![Ticken von c#-Projekten](images/AzureLabs-Lab5-28.png)

10.  Schließen Sie das Fenster „Build Settings“ (Buildeinstellungen).

11. Speichern Sie Ihre Szene und Project (**FILE**  >  **SAVE SCENE /FILE**  >  **SAVE PROJECT**).

## <a name="chapter-4---setup-main-camera"></a>Kapitel 4: Einrichten der Hauptkamera

> [!IMPORTANT]
> Wenn Sie die *Unity-Komponenten* dieses Kurses einrichten überspringen und direkt mit dem Code fortfahren möchten, können Sie dieses [UNITYPACKAGE](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage)herunterladen und als benutzerdefiniertes Paket in Ihr Projekt [importieren.](https://docs.unity3d.com/Manual/AssetPackages.html) Dieser enthält auch die DLLs aus dem nächsten Kapitel. Fahren Sie nach dem Import mit [Kapitel 7 fort.](#chapter-7---create-the-azureservices-class) 

1.  Im *Hierarchiebereich finden* Sie ein Objekt namens **Hauptkamera.** Dieses Objekt stellt Ihren "Kopfpunkt" dar, sobald Sie sich in Ihrer Anwendung befinden.

2.  Wählen Sie vor dem Unity-Dashboard das **Hauptkamera-GameObject aus.** Sie werden feststellen, dass der Inspektorbereich *(im* Allgemeinen auf der rechten Seite im Dashboard) die verschiedenen Komponenten dieses *GameObject* mit *Transformation* oben, gefolgt von *Camera* und einigen anderen Komponenten zeigt. Sie müssen die Transformation der Hauptkamera zurücksetzen, damit sie richtig positioniert ist.

3.  Wählen Sie hierzu das Zahnradsymbol neben  der Komponente Transformieren der Kamera und dann **Zurücksetzen aus.** 

    ![Reset-Transformation](images/AzureLabs-Lab5-29.png)

4.  Aktualisieren Sie dann die **Komponente Transformieren** so, dass sie wie die folgenden aussieht:

    |         |    TRANSFORMIEREN – POSITION   |       |
    | :-----: | :-----------------------: | :----:|
    | **X**   | **J**                     | **Z** |
    | 0       | 1                         | 0     |    

    |       | TRANSFORMIEREN – ROTATION |       |
    | :---: | :------------------: | :----:|
    | **X** | **J**                | **Z** |
    | 0     | 0                    | 0     |

    |       | TRANSFORMIEREN – SKALIEREN |       |
    | :---: | :---------------: | :---: |
    | **X** | **J**             | **Z** |
    | 1     | 1                 | 1     |

    ![Festlegen der Kameratransformation](images/AzureLabs-Lab5-30.png)

## <a name="chapter-5---setting-up-the-unity-scene"></a>Kapitel 5: Einrichten der Unity-Szene

1.  Klicken Sie mit der rechten Maustaste in einen leeren Bereich des *Hierarchiebereichs,* und fügen Sie unter **3D-Objekt** eine **Ebene hinzu.**

    ![Erstellen einer neuen Ebene](images/AzureLabs-Lab5-31.png)

2.  Ändern Sie bei ausgewähltem **Plane-Objekt** die folgenden Parameter im *Inspektorbereich:*

    |       | TRANSFORMIEREN – POSITION |       |
    | :---: | :------------------: | :---: |
    | **X** | **J**                | **Z** |
    | 0     | 0                    | 4     |

    |       | TRANSFORMIEREN – SKALIEREN |       |
    | :---: | :---------------: | :---: |
    | **X** | **J**             | **Z** |
    | 10    | 1                 | 10    |

    ![Festlegen der Ebenenposition und -skalierung](images/AzureLabs-Lab5-32.png)

    ![Szenenansicht der Ebene](images/AzureLabs-Lab5-33.png)

3.  Klicken Sie mit der rechten Maustaste in einen leeren Bereich des *Hierarchiebereichs,* und fügen Sie unter **3D-Objekt** einen **Cube hinzu.**

    1.  Benennen Sie den Cube in **GazeButton** um (wenn der Cube ausgewählt ist, drücken Sie 'F2').

    2.  Ändern Sie die folgenden Parameter im *Inspektorbereich:*

        |       | TRANSFORMIEREN – POSITION |       |
        | :---: | :------------------: |:-----:|
        | **X** | **J**                | **Z** |
        | 0     | 3                    | 5     |


        ![Schaltflächentransformation zum Festlegen des Anvierens](images/AzureLabs-Lab5-34.png)

        ![Szenenansicht mit Anvingschaltfläche](images/AzureLabs-Lab5-35.png)

    3.  Klicken Sie auf die **Dropdownschaltfläche** Tag und dann auf Tag **hinzufügen,** um den Bereich *Tags & Ebenen zu öffnen.*

        ![Neues Tag hinzufügen](images/AzureLabs-Lab5-36.png)

        ![Wählen Sie plus aus.](images/AzureLabs-Lab5-37.png)

    4.  Klicken Sie **auf die Schaltfläche + (Pluszeichen),** geben Sie im Feld Neuer *Tagname* den Namen **GazeButton** ein, und klicken Sie auf **Speichern.**

        ![name new tag](images/AzureLabs-Lab5-38.png)

    5.  Klicken Sie im Hierarchiebereich auf das **GazeButton-Objekt,** und weisen Sie im Inspektorbereich das neu erstellte **GazeButton-Tag** zu.  

        ![Zuweisen der Anvingschaltfläche zum neuen Tag](images/AzureLabs-Lab5-39.png)

4.  Klicken Sie mit der rechten Maustaste auf das **GazeButton-Objekt** im *Hierarchiebereich,* und fügen Sie ein **leeres GameObject** hinzu (das als untergeordnetes *Objekt hinzugefügt* wird).

5.  Wählen Sie das neue Objekt aus, und benennen Sie **es in ShapeSpawnPoint um.**

    1.  Ändern Sie die folgenden Parameter im *Inspektorbereich:*

        |       | TRANSFORMIEREN – POSITION |       |
        | :---: | :------------------: |:----: |
        | **X** |**J**                 | **Z** |
        | 0     | -1                   | 0     |

        ![Aktualisieren der Form der Spawnpunkttransformation](images/AzureLabs-Lab5-40.png)

        ![Form der Punktszenenansicht](images/AzureLabs-Lab5-41.png)

6.  Als Nächstes erstellen Sie ein **3D-Textobjekt,** um Feedback zum Status des Azure-Diensts zu geben.

    Klicken Sie im Hierarchiebereich erneut mit der rechten Maustaste auf **GazeButton,** und fügen Sie ein **3D Object**  >  **3D Text-Objekt** als untergeordnetes *-Objekt hinzu.*

    ![Erstellen eines neuen 3D-Textobjekts](images/AzureLabs-Lab5-42.png)

7.  Benennen Sie das **3D-Textobjekt** in **AzureStatusText um.**

8.  Ändern Sie **die Transformation des AzureStatusText-Objekts** wie folgt:

    |       | TRANSFORMIEREN – POSITION |       |
    | :---: | :------------------: | :---: |
    | **X** | **J**                | **Z** |
    | 0     | 0                    | -0,6  |

    |       | TRANSFORMIEREN – SKALIEREN |       |
    | :---: | :---------------: | :---: |
    | **X** | **J**             | **Z** |
    | 0.1   | 0.1               | 0.1   |


    > [!NOTE]
    > Machen Sie sich keine Gedanken darüber, ob sie sich außerhalb des Mittelpunkts befindet, da dies behoben wird, wenn die unten stehende Textgitternetzkomponente aktualisiert wird.

9.  Ändern Sie die **Textgitternetzkomponente** so, dass sie der folgenden entspricht:

    ![Festlegen der Textgitternetzkomponente](images/AzureLabs-Lab5-43.png)

    > [!TIP]
    > Die ausgewählte Farbe ist hier Hexadezimalfarbe: **000000FF.** Sie können aber auch ihre eigene Farbe auswählen. Stellen Sie sicher, dass sie lesbar ist.

10. Die Struktur des Hierarchiebereichs sollte nun wie folgt aussehen:

    ![Textgitternetz in der Hierarchie](images/AzureLabs-Lab5-43b.png)

10. Ihre Szene sollte nun wie folgt aussehen:

    ![Textgitternetz in der Szenenansicht](images/AzureLabs-Lab5-44.png)


## <a name="chapter-6---import-azure-storage-for-unity"></a>Kapitel 6: Importieren von Azure Storage für Unity

Sie verwenden Azure Storage für Unity (das selbst das .NET SDK für Azure nutzt). Weitere Informationen hierzu finden Sie im [artikel Azure Storage für Unity.](/sandbox/gamedev/unity/azure-storage-unity)

Derzeit gibt es ein bekanntes Problem in Unity, bei dem Plug-Ins nach dem Import neu konfiguriert werden müssen. Diese Schritte (4 bis 7 in diesem Abschnitt) sind nicht mehr erforderlich, nachdem der Fehler behoben wurde.

Um das SDK in Ihr eigenes Projekt zu importieren, stellen Sie sicher, dass Sie das neueste [".unitypackage" aus GitHub](https://aka.ms/azstorage-unitysdk)heruntergeladen haben. Gehen Sie nun wie folgt vor:

1.  Fügen Sie die **UNITYPACKAGE-Datei** mithilfe der Menüoption Assets Import Package Custom Package   >    >  **(Benutzerdefiniertes Paket** importieren) zu Unity hinzu.

2.  Im daraufhin angezeigten Feld **Unity-Paket importieren** können Sie unter **Plug-In** Storage alles  >  auswählen. Deaktivieren Sie alle anderen Informationen, da sie für diesen Kurs nicht benötigt werden.

    ![Importieren in ein Paket](images/AzureLabs-Lab5-45.png)

3.  Klicken Sie auf die Schaltfläche **Importieren,** um die Elemente ihrem Projekt hinzuzufügen.

4.  Wechseln Sie in der Ansicht Project zum Ordner *Storage* unter *Plug-Ins,* und wählen Sie *nur* die folgenden Plug-Ins aus:

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

        ![Deaktivieren Sie Alle Plattformen.](images/AzureLabs-Lab5-46.png)

5.  Deaktivieren Sie bei auswahl *dieser spezifischen Plug-Ins* die Option  *Beliebige Plattform,* **deaktivieren** Sie *WSAPlayer,* und klicken Sie dann auf **Anwenden.**

    ![Anwenden von Plattform-DLL-Dateien](images/AzureLabs-Lab5-47.png)

    > [!NOTE]
    > Wir markieren diese speziellen Plug-Ins so, dass sie nur im Unity-Editor verwendet werden. Dies liegt daran, dass es verschiedene Versionen der gleichen Plug-Ins im WSA-Ordner gibt, die verwendet werden, nachdem das Projekt aus Unity exportiert wurde.

6.  Wählen Sie im Ordner *Storage* Plug-Ins nur Folgendes aus:

    -   Microsoft.Data.Services.Client

        ![set don't process for dlls](images/AzureLabs-Lab5-48.png)

7.  Aktivieren Sie unter Plattform *Einstellungen* das Kontrollkästchen **Nicht verarbeiten,** und klicken Sie auf **Anwenden.**

    ![Keine Verarbeitung anwenden](images/AzureLabs-Lab5-49.png)

    > [!NOTE]
    > Wir markieren dieses Plug-In als "Nicht verarbeiten", da der Unity-Assemblypatcher Schwierigkeiten bei der Verarbeitung dieses Plug-Ins hat. Das Plug-In funktioniert weiterhin, auch wenn es nicht verarbeitet wird.

## <a name="chapter-7---create-the-azureservices-class"></a>Kapitel 7: Erstellen der AzureServices-Klasse

Die erste Klasse, die Sie erstellen, ist die *AzureServices-Klasse.*

Die *AzureServices-Klasse* ist für Folgendes verantwortlich:

-   Speichern von Azure-Kontoanmeldeinformationen.

-   Aufrufen der Azure-App-Funktion.

-   Das Hochladen und Herunterladen der Datendatei in Ihrer Azure Cloud Storage.

So erstellen Sie diese Klasse:

1.  Klicken Sie mit der rechten Maustaste auf den *Medienobjektordner,* der sich im Project Bereich Ordner **erstellen**  >  befindet. Nennen Sie den Ordner **Skripts**.

    ![Neuen Ordner erstellen](images/AzureLabs-Lab5-50.png)

    ![Ordner "call" – Skripts](images/AzureLabs-Lab5-51.png)

2.  Doppelklicken Sie auf den gerade erstellten Ordner, um ihn zu öffnen.

3.  Klicken Sie mit der rechten Maustaste in den Ordner  >  **C#-Skript** erstellen. Rufen Sie das Skript *AzureServices auf.*

4.  Doppelklicken Sie auf die neue *AzureServices-Klasse,* um sie mit *Visual Studio* zu öffnen.

5.  Fügen Sie am Anfang von *AzureServices* die folgenden Namespaces hinzu:

    ```csharp
        using System;
        using System.Threading.Tasks;
        using UnityEngine;
        using Microsoft.WindowsAzure.Storage;
        using Microsoft.WindowsAzure.Storage.File;
        using System.IO;
        using System.Net;
    ```

6.  Fügen Sie die folgenden Inspektorfelder in der *AzureServices-Klasse* hinzu:

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static AzureServices instance;

        /// <summary>
        /// Reference Target for AzureStatusText Text Mesh object
        /// </summary>
        public TextMesh azureStatusText;
    ```

7.  Fügen Sie dann die folgenden Membervariablen in der *AzureServices-Klasse* hinzu:

    ```csharp
        /// <summary>
        /// Holds the Azure Function endpoint - Insert your Azure Function
        /// Connection String here.
        /// </summary>

        private readonly string azureFunctionEndpoint = "--Insert here you AzureFunction Endpoint--";

        /// <summary>
        /// Holds the Storage Connection String - Insert your Azure Storage
        /// Connection String here.
        /// </summary>
        private readonly string storageConnectionString = "--Insert here you AzureStorage Connection String--";

        /// <summary>
        /// Name of the Cloud Share - Hosts directories.
        /// </summary>
        private const string fileShare = "fileshare";

        /// <summary>
        /// Name of a Directory within the Share
        /// </summary>
        private const string storageDirectory = "storagedirectory";

        /// <summary>
        /// The Cloud File
        /// </summary>
        private CloudFile shapeIndexCloudFile;

        /// <summary>
        /// The Linked Storage Account
        /// </summary>
        private CloudStorageAccount storageAccount;

        /// <summary>
        /// The Cloud Client
        /// </summary>
        private CloudFileClient fileClient;

        /// <summary>
        /// The Cloud Share - Hosts Directories
        /// </summary>
        private CloudFileShare share;

        /// <summary>
        /// The Directory in the share that will host the Cloud file
        /// </summary>
        private CloudFileDirectory dir;
    ```

    > [!IMPORTANT]
    > Stellen Sie sicher, dass Sie *die* Endpunkt- und *Verbindungszeichenfolgenwerte* durch die Werte aus Ihrem Azure-Speicher ersetzen, die sie im Azure-Portal finden.

8.  Code für *die Methoden "Awake()"* und *"Start()"* muss jetzt hinzugefügt werden. Diese Methoden werden aufgerufen, wenn die -Klasse initialisiert wird:

    ```csharp
        private void Awake()
        {
            instance = this;
        }

        // Use this for initialization
        private void Start()
        {
            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";
        }

        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {

        }
    ```

    > [!IMPORTANT]
    > Wir werden den Code für *CallAzureFunctionForNextShape()* in einem [zukünftigen Kapitel](#chapter-10---completing-the-azureservices-class)ausfüllen.

9.  Löschen Sie die *Update()-Methode,* da sie von dieser Klasse nicht verwendet wird.

10. Speichern Sie Ihre Änderungen in Visual Studio, und kehren Sie dann zu Unity zurück.

11. Klicken Sie auf die *AzureServices-Klasse,* und ziehen Sie sie aus dem Ordner Scripts in das Objekt Hauptkamera im *Hierarchiebereich*.

12. Wählen Sie die Hauptkamera aus, greifen Sie dann das untergeordnete **AzureStatusText-Objekt** unterhalb des **GazeButton-Objekts,** und platzieren Sie es im **AzureStatusText-Verweiszielfeld** im *Inspector*, um den Verweis auf das *AzureServices-Skript* bereitzustellen.

    ![Zuweisen eines Azure-Statustextverweisziels](images/AzureLabs-Lab5-52.png)

## <a name="chapter-8---create-the-shapefactory-class"></a>Kapitel 8: Erstellen der ShapeFactory-Klasse

Das nächste zu erstellende Skript ist die *ShapeFactory-Klasse.* Die Rolle dieser Klasse besteht darin, auf Anforderung eine neue Form zu erstellen und einen Verlauf der Formen beizubehalten, die in einer *Shape-Verlaufsliste* erstellt wurden. Jedes Mal, wenn eine Form erstellt wird, wird die *Liste Shape-Verlauf* in der *AzureService-Klasse* aktualisiert und dann in Ihrer *Azure Storage* gespeichert. Wenn beim Starten der Anwendung eine gespeicherte Datei in Ihrer *Azure Storage* gefunden wird, wird die *Liste Shape-Verlauf* abgerufen und wiedergegeben. Das **3D-Textobjekt** gibt an, ob die generierte Form aus dem Speicher stammt oder neu ist.

So erstellen Sie diese Klasse:

1.  Wechseln Sie zum Ordner **Skripts,** den Sie zuvor erstellt haben.

2.  Klicken Sie mit der rechten Maustaste in den Ordner  >  **C#-Skript** erstellen. Rufen Sie das Skript *ShapeFactory* auf.

3.  Doppelklicken Sie auf das neue *ShapeFactory-Skript,* um es mit *Visual Studio* zu öffnen.

4.  Stellen Sie sicher, dass die *ShapeFactory-Klasse* die folgenden Namespaces enthält:

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;
    ```

5.  Fügen Sie der *ShapeFactory-Klasse* die unten gezeigten Variablen hinzu, und ersetzen Sie die Funktionen *Start()* und *Awake()* durch die folgenden:

    ```csharp
        /// <summary>
        /// Provide this class Singleton-like behaviour
        /// </summary>
        [HideInInspector]
        public static ShapeFactory instance;

        /// <summary>
        /// Provides an Inspector exposed reference to ShapeSpawnPoint
        /// </summary>
        [SerializeField]
        public Transform spawnPoint;

        /// <summary>
        /// Shape History Index
        /// </summary>
        [HideInInspector]
        public List<int> shapeHistoryList;

        /// <summary>
        /// Shapes Enum for selecting required shape
        /// </summary>
        private enum Shapes { Cube, Sphere, Cylinder }

        private void Awake()
        {
            instance = this;
        }

        private void Start()
        {
            shapeHistoryList = new List<int>();
        }
    ```

6.  Die *CreateShape()-Methode* generiert die primitiven Formen basierend auf dem angegebenen *ganzzahligen* Parameter. Der boolesche Parameter wird verwendet, um anzugeben, ob die derzeit erstellte Form aus dem Speicher stammt oder neu ist. Platzieren Sie den folgenden Code in der *ShapeFactory-Klasse* unterhalb der vorherigen Methoden:

    ```csharp
        /// <summary>
        /// Use the Shape Enum to spawn a new Primitive object in the scene
        /// </summary>
        /// <param name="shape">Enumerator Number for Shape</param>
        /// <param name="storageShape">Provides whether this is new or old</param>
        internal void CreateShape(int shape, bool storageSpace)
        {
            Shapes primitive = (Shapes)shape;
            GameObject newObject = null;
            string shapeText = storageSpace == true ? "Storage: " : "New: ";

            AzureServices.instance.azureStatusText.text = string.Format("{0}{1}", shapeText, primitive.ToString());

            switch (primitive)
            {
                case Shapes.Cube:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                break;

                case Shapes.Sphere:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                break;

                case Shapes.Cylinder:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                break;
            }

            if (newObject != null)
            {
                newObject.transform.position = spawnPoint.position;

                newObject.transform.localScale = new Vector3(0.5f, 0.5f, 0.5f);

                newObject.AddComponent<Rigidbody>().useGravity = true;

                newObject.GetComponent<Renderer>().material.color = UnityEngine.Random.ColorHSV(0f, 1f, 1f, 1f, 0.5f, 1f);
            }
        }
    ```

7.  Speichern Sie Ihre Änderungen unbedingt in Visual Studio, bevor Sie zu Unity zurückkehren.

8.  Klicken Sie im Unity-Editor zurück, und ziehen Sie die *ShapeFactory-Klasse* aus dem Ordner **Scripts** in das **Objekt Hauptkamera** im *Hierarchiebereich*.

9. Wenn die Hauptkamera ausgewählt ist, werden Sie feststellen, dass der *ShapeFactory-Skriptkomponente* der *Spawn Point-Verweis* fehlt. Um dies zu beheben, ziehen Sie das **ShapeSpawnPoint-Objekt** aus dem *Hierarchiebereich* auf das **Spawn Point-Verweisziel.**

    ![Festlegen des Referenzziels für die Shape-Factory](images/AzureLabs-Lab5-53.png)

## <a name="chapter-9---create-the-gaze-class"></a>Kapitel 9: Erstellen der Klasse "Anv"

Das letzte Skript, das  Sie erstellen müssen, ist die Gaze-Klasse.

Diese Klasse ist für die Erstellung eines **Raycasts** verantwortlich, der von der Hauptkamera nach vorne projiziert wird, um zu erkennen, welches Objekt der Benutzer ansieht. In diesem Fall muss raycast ermitteln, ob der Benutzer das **GazeButton-Objekt** in der Szene betrachtet und ein Verhalten auslöst.

So erstellen Sie diese Klasse:

1.  Wechseln Sie zum Ordner **Skripts,** den Sie zuvor erstellt haben.

2.  Klicken **Sie** mit der rechten Maustaste im Project Bereich  >  **C#-Skript** erstellen. Rufen Sie das Skript *Gaze auf.*

3.  Doppelklicken Sie auf das neue *Anverfolgungsskript,* um es mit Visual Studio zu *öffnen.*

4.  Stellen Sie sicher, dass der folgende Namespace am Anfang des Skripts enthalten ist:

    ```csharp
        using UnityEngine;
    ```

5.  Fügen Sie dann die folgenden Variablen in der *Gaze-Klasse* hinzu:

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static Gaze instance;

        /// <summary>
        /// The Tag which the Gaze will use to interact with objects. Can also be set in editor.
        /// </summary>
        public string InteractibleTag = "GazeButton";

        /// <summary>
        /// The layer which will be detected by the Gaze ('~0' equals everything).
        /// </summary>
        public LayerMask LayerMask = ~0;

        /// <summary>
        /// The Max Distance the gaze should travel, if it has not hit anything.
        /// </summary>
        public float GazeMaxDistance = 300;

        /// <summary>
        /// The size of the cursor, which will be created.
        /// </summary>
        public Vector3 CursorSize = new Vector3(0.05f, 0.05f, 0.05f);

        /// <summary>
        /// The color of the cursor - can be set in editor.
        /// </summary>
        public Color CursorColour = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

        /// <summary>
        /// Provides when the gaze is ready to start working (based upon whether
        /// Azure connects successfully).
        /// </summary>
        internal bool GazeEnabled = false;

        /// <summary>
        /// The currently focused object.
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        /// <summary>
        /// The object which was last focused on.
        /// </summary>
        internal GameObject _oldFocusedObject { get; private set; }

        /// <summary>
        /// The info taken from the last hit.
        /// </summary>
        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// The cursor object.
        /// </summary>
        internal GameObject Cursor { get; private set; }

        /// <summary>
        /// Provides whether the raycast has hit something.
        /// </summary>
        internal bool Hit { get; private set; }

        /// <summary>
        /// This will store the position which the ray last hit.
        /// </summary>
        internal Vector3 Position { get; private set; }

        /// <summary>
        /// This will store the normal, of the ray from its last hit.
        /// </summary>
        internal Vector3 Normal { get; private set; }

        /// <summary>
        /// The start point of the gaze ray cast.
        /// </summary>
        private Vector3 _gazeOrigin;

        /// <summary>
        /// The direction in which the gaze should be.
        /// </summary>
        private Vector3 _gazeDirection;
    ```

> [!IMPORTANT]
> Einige dieser Variablen können im *Editor* bearbeitet werden.

6.  Code für die *Methoden "Awake()"* und *"Start()"* muss nun hinzugefügt werden.

    ```csharp
        /// <summary>
        /// The method used after initialization of the scene, though before Start().
        /// </summary>
        private void Awake()
        {
            // Set this class to behave similar to singleton
            instance = this;
        }

        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        private void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  Fügen Sie den folgenden Code hinzu, der zu Beginn ein Cursorobjekt zusammen mit der *Update()-Methode* erstellt, mit der die Raycast-Methode ausgeführt wird und wo der boolesche GazeEnabled-Wert umgeschaltet wird:

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);

            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = CursorSize;

            newCursor.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
            {
                color = CursorColour
            };

            newCursor.name = "Cursor";

            newCursor.SetActive(true);

            return newCursor;
        }

        /// <summary>
        /// Called every frame
        /// </summary>
        private void Update()
        {
            if(GazeEnabled == true)
            {
                _gazeOrigin = Camera.main.transform.position;

                _gazeDirection = Camera.main.transform.forward;

                UpdateRaycast();
            }
        }
    ```

8. Fügen Sie als Nächstes die *UpdateRaycast()-Methode* hinzu, die einen Raycast projiziert und das Trefferziel erkennt.

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;

            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance, LayerMask);

            HitInfo = hitInfo;

            // Check whether raycast has hit.
            if (Hit == true)
            {
                Position = hitInfo.point;

                Normal = hitInfo.normal;

                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedObject = null;

                // Provide default position for cursor.
                Position = _gazeOrigin + (_gazeDirection * GazeMaxDistance);

                // Provide a default normal.
                Normal = _gazeDirection;
            }

            // Lerp the cursor to the given position, which helps to stabilize the gaze.
            Cursor.transform.position = Vector3.Lerp(Cursor.transform.position, Position, 0.6f);

            // Check whether the previous focused object is this same 
            //    object. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();

                if (FocusedObject != null)
                {
                if (FocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                        // Set the Focused object to green - success!
                        FocusedObject.GetComponent<Renderer>().material.color = Color.green;

                        // Start the Azure Function, to provide the next shape!
                        AzureServices.instance.CallAzureFunctionForNextShape();
                    }
                }
            }
        }
    ```

9. Fügen Sie abschließend die *ResetFocusedObject()-Methode* hinzu, die die aktuelle Farbe der GazeButton-Objekte umschaltet und angibt, ob eine neue Form erstellt wird.

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                    // Set the old focused object to red - its original state.
                    _oldFocusedObject.GetComponent<Renderer>().material.color = Color.red;
                }
            }
        }
    ```

10.  Speichern Sie Ihre Änderungen in Visual Studio, bevor Sie zu Unity zurückkehren.

11.  Klicken Sie auf die *Klasse Gaze, und* ziehen Sie sie aus dem Ordner Scripts in das **Objekt Main Camera** im *Hierarchiebereich.*

## <a name="chapter-10---completing-the-azureservices-class"></a>Kapitel 10: Abschließen der AzureServices-Klasse

Mit den anderen Skripts ist es jetzt möglich, die *AzureServices-Klasse zu* vervollständigen.  Dies wird erreicht durch:

1.  Hinzufügen einer neuen Methode mit dem Namen *CreateCloudIdentityAsync()* zum Einrichten der Authentifizierungsvariablen, die für die Kommunikation mit Azure erforderlich sind.

    > Diese Methode überprüft auch das Vorhandensein einer zuvor gespeicherten Datei, die die Formliste enthält.
    >
    > **Wenn die Datei gefunden wird,** wird der Benutzer Gaze deaktiviert, und die Shape-Erstellung wird entsprechend dem Muster der Formen ausgelöst, wie in der Azure Storage **gespeichert.** Dies kann dem Benutzer angezeigt werden, da das **Textgitternetz** je nach Ursprung der Formen die Anzeige "Storage" oder "Neu" bietet.
    >
    > **Wenn keine Datei gefunden wird,** wird das Anvieren *aktiviert,* sodass der Benutzer Formen erstellen kann, wenn er das **GazeButton-Objekt** in der Szene betrachtet.

    ```csharp
        /// <summary>
        /// Create the references necessary to log into Azure
        /// </summary>
        private async void CreateCloudIdentityAsync()
        {
            // Retrieve storage account information from connection string
            storageAccount = CloudStorageAccount.Parse(storageConnectionString);

            // Create a file client for interacting with the file service.
            fileClient = storageAccount.CreateCloudFileClient();

            // Create a share for organizing files and directories within the storage account.
            share = fileClient.GetShareReference(fileShare);

            await share.CreateIfNotExistsAsync();

            // Get a reference to the root directory of the share.
            CloudFileDirectory root = share.GetRootDirectoryReference();

            // Create a directory under the root directory
            dir = root.GetDirectoryReference(storageDirectory);

            await dir.CreateIfNotExistsAsync();

            //Check if the there is a stored text file containing the list
            shapeIndexCloudFile = dir.GetFileReference("TextShapeFile");

            if (!await shapeIndexCloudFile.ExistsAsync())
            {
                // File not found, enable gaze for shapes creation
                Gaze.instance.GazeEnabled = true;

                azureStatusText.text = "No Shape\nFile!";
            }
            else
            {
                // The file has been found, disable gaze and get the list from the file
                Gaze.instance.GazeEnabled = false;

                azureStatusText.text = "Shape File\nFound!";

                await ReplicateListFromAzureAsync();
            }
        }
    ```

2.  Der nächste Codeausschnitt ist innerhalb der *Start()-Methode.* Dabei wird die *CreateCloudIdentityAsync()-Methode* aufgerufen. Sie können ihre aktuelle *Start()-Methode* mit den folgenden Informationen kopieren:

    ```csharp
        private void Start()
        {
            // Disable TLS cert checks only while in Unity Editor (until Unity adds support for TLS)
    #if UNITY_EDITOR
            ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };
    #endif

            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";

            //Creating the references necessary to log into Azure and check if the Storage Directory is empty
            CreateCloudIdentityAsync();
        }
    ```

3.  Geben Sie den Code für die *Methode CallAzureFunctionForNextShape() ein.* Sie verwenden die zuvor erstellte *Azure-Funktions-App,* um einen Formindex an fordern. Sobald die neue Form empfangen wurde, sendet diese Methode die Form an die *ShapeFactory-Klasse,* um die neue Form in der Szene zu erstellen. Verwenden Sie den folgenden Code, um den Text von *CallAzureFunctionForNextShape() zu vervollständigen.*

    ```csharp
        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {
            int azureRandomInt = 0;

            // Call Azure function
            HttpWebRequest webRequest = WebRequest.CreateHttp(azureFunctionEndpoint);

            WebResponse response = await webRequest.GetResponseAsync();

            // Read response as string
            using (Stream stream = response.GetResponseStream())
            {
                StreamReader reader = new StreamReader(stream);

                String responseString = reader.ReadToEnd();

                //parse result as integer
                Int32.TryParse(responseString, out azureRandomInt);
            }

            //add random int from Azure to the ShapeIndexList
            ShapeFactory.instance.shapeHistoryList.Add(azureRandomInt);

            ShapeFactory.instance.CreateShape(azureRandomInt, false);

            //Save to Azure storage
            await UploadListToAzureAsync();
        }
    ```

4.  Fügen Sie eine Methode hinzu, um eine Zeichenfolge zu erstellen, indem Sie die in der Liste des Shape-Verlaufs gespeicherten ganzen Zahlen verketten und in ihrer Azure Storage *speichern.*

    ```csharp
        /// <summary>
        /// Upload the locally stored List to Azure
        /// </summary>
        private async Task UploadListToAzureAsync()
        {
            // Uploading a local file to the directory created above
            string listToString = string.Join(",", ShapeFactory.instance.shapeHistoryList.ToArray());

            await shapeIndexCloudFile.UploadTextAsync(listToString);
        }
    ```

5.  Fügen Sie eine Methode hinzu, um den in der Datei gespeicherten Text abzurufen, der in ihrer *Azure Storage Datei* gespeichert ist, und *deserialisieren* Sie ihn in eine Liste.

6.  Nach Abschluss dieses Vorgangs aktiviert die -Methode das Anvieren erneut, damit der Benutzer der Szene weitere Formen hinzufügen kann.

    ```csharp
        ///<summary>
        /// Get the List stored in Azure and use the data retrieved to replicate 
        /// a Shape creation pattern
        ///</summary>
        private async Task ReplicateListFromAzureAsync()
        {
            string azureTextFileContent = await shapeIndexCloudFile.DownloadTextAsync();

            string[] shapes = azureTextFileContent.Split(new char[] { ',' });

            foreach (string shape in shapes)
            {
                int i;

                Int32.TryParse(shape.ToString(), out i);

                ShapeFactory.instance.shapeHistoryList.Add(i);

                ShapeFactory.instance.CreateShape(i, true);

                await Task.Delay(500);
            }

            Gaze.instance.GazeEnabled = true;

            azureStatusText.text = "Load Complete!";
        }
    ```

7.  Speichern Sie Ihre Änderungen in Visual Studio, bevor Sie zu Unity zurückkehren.

## <a name="chapter-11---build-the-uwp-solution"></a>Kapitel 11: Erstellen der UWP-Lösung

So starten Sie den Buildprozess:

1.  Wechseln Sie **zu Datei**  >  **erstellen Einstellungen**.

    ![Erstellen der App](images/AzureLabs-Lab5-54.png)

2.  Klicken Sie auf **Erstellen**. Unity startet ein *Datei-Explorer-Fenster,* in dem Sie einen Ordner erstellen und dann einen Ordner auswählen müssen, in dem die App erstellt werden soll. Erstellen Sie diesen Ordner jetzt, und nennen Sie ihn *App*. Wenn Sie dann den *Ordner App ausgewählt* haben, klicken Sie auf Ordner **auswählen.**

3.  Unity beginnt damit, Ihr Projekt im Ordner *App zu* erstellen.

4.  Sobald Unity die Erstellung abgeschlossen hat (dies kann einige Zeit dauern), wird ein *Datei-Explorer-Fenster* am Speicherort Ihres Buildfensters geöffnet (überprüfen Sie Ihre Taskleiste, da sie möglicherweise nicht immer über Ihren Fenstern angezeigt wird, sondern Sie über das Addition eines neuen Fensters benachrichtigt).

## <a name="chapter-12---deploying-your-application"></a>Kapitel 12: Bereitstellen Ihrer Anwendung

So stellen Sie Ihre Anwendung

1.  Navigieren Sie zum *Ordner App,* der im letzten [Kapitel erstellt wurde.](#chapter-11---build-the-uwp-solution) Es wird eine Datei mit dem Namen Ihrer Apps mit der Erweiterung ".sln" angezeigt, auf die Sie doppelklicken sollten, um sie *in* Visual Studio.

2.  Wählen Sie **auf der Projektmappenplattform** **x86, Lokaler Computer aus.**

3.  Wählen Sie in **der Projektmappenkonfiguration** **Debuggen aus.**

    > Für die Microsoft HoloLens ist es möglicherweise einfacher, dies auf *Remotecomputer* zu setzen, damit Sie nicht an Ihren Computer geentert werden. Sie müssen jedoch auch die folgenden Schritte unternehmen:
    > - Kennen Sie die **IP-Adresse** Ihres HoloLens, die sie in den erweiterten Optionen für **Einstellungen** Network & Internet  >    >  **Wi-Fi**  >  **finden.** IPv4 ist die Adresse, die Sie verwenden sollten. 
    > - Stellen Sie **sicher, dass der Entwicklermodus** **aktiviert ist.** finden Sie **in Einstellungen**  >  **Update & Sicherheit** für  >  **Entwickler.**

    ![Bereitstellen der Lösung](images/AzureLabs-Lab5-55.png)

4.  Wechseln Sie zum **Menü Erstellen,** und klicken Sie **auf Projektmappe bereitstellen,** um die Anwendung auf Ihren Computer zu laden.

5.  Ihre App sollte nun in der Liste der installierten Apps angezeigt werden, die jetzt gestartet und getestet werden können.

## <a name="your-finished-azure-functions-and-storage-application"></a>Ihre fertige Azure Functions und Storage Anwendung

Herzlichen Glückwunsch! Sie haben eine Mixed Reality-App erstellt, die sowohl die Azure Functions als auch Azure Storage nutzt. Ihre App kann auf gespeicherten Daten basieren und basierend auf diesen Daten eine Aktion bereitstellen.

![Final Product -end](images/AzureLabs-Lab5-00.png)

## <a name="bonus-exercises"></a>Zusatzübungen

### <a name="exercise-1"></a>Übung 1

Erstellen Sie einen zweiten Spawnpunkt, und zeichnen Sie auf, aus welchem Punkt ein Objekt erstellt wurde. Wenn Sie die Datendatei laden, geben Sie die Formen wieder, die von dem Speicherort erzeugt werden, an dem sie ursprünglich erstellt wurden.

### <a name="exercise-2"></a>Übung 2

Erstellen Sie eine Möglichkeit, die App neu zu starten, anstatt sie jedes Mal erneut öffnen zu müssen. **Das Laden von** Szenen ist ein guter Einstieg. Erstellen Sie anschließend eine Möglichkeit, die gespeicherte Liste *in* Azure Storage zu löschen, damit sie problemlos von Ihrer App zurückgesetzt werden kann.