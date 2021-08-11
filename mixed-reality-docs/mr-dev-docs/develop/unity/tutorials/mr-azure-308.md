---
title: 'HoloLens (1. Generation) und Azure 308: Geräteübergreifende Benachrichtigungen'
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie Azure Notification Hubs, Azure Functions und Azure Storage und Tabellen in einer Mixed Reality-Anwendung implementieren.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, Tutorial, API, Benachrichtigung, Funktionen, Tabellen, Notification Hubs, HoloLens, immersive, VR, Windows 10, Visual Studio
ms.openlocfilehash: 01d096297a9fbe25d39b2846acd2ee89b50edcfd26456f3f20ccd2c9bc26b514
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115205532"
---
# <a name="hololens-1st-gen-and-azure-308-cross-device-notifications"></a>HoloLens (1. Generation) und Azure 308: Geräteübergreifende Benachrichtigungen

<br>

>[!NOTE]
>Die Tutorials der Mixed Reality Academy wurden im Hinblick auf HoloLens (1. Gen.) und immersive Mixed Reality-Headsets entworfen.  Daher halten wir es für wichtig, diese Tutorials für Entwickler verfügbar zu halten, die noch nach Anleitung beim Entwickeln für diese Geräte suchen.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für HoloLens 2 verwendet werden.  Sie werden gewartet, um weiterhin auf den unterstützten Geräten zu funktionieren. Es wird eine neue Reihe von Tutorials geben, die in Zukunft veröffentlicht werden, die veranschaulichen, wie sie für HoloLens 2 entwickelt werden.  Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn sie veröffentlicht werden.

<br>

![final product -start](images/AzureLabs-Lab8-00.png)

In diesem Kurs erfahren Sie, wie Sie einer Mixed Reality-Anwendung mithilfe von Azure Notification Hubs, Azure-Tabellen und Azure Functions Notification Hubs Funktionen hinzufügen.

**Azure Notification Hubs** ist ein Microsoft-Dienst, mit dem Entwickler gezielte und personalisierte Pushbenachrichtigungen an jede Plattform senden können, die alle in der Cloud unterstützt werden. Dies kann Entwicklern je nach Szenario effektiv die Kommunikation mit Endbenutzern oder sogar die Kommunikation zwischen verschiedenen Anwendungen ermöglichen. Weitere Informationen finden Sie auf der **Seite azure Notification Hubs** [.](/azure/notification-hubs/notification-hubs-push-notification-overview)

**Azure Functions** ist ein Microsoft-Dienst, mit dem Entwickler kleine Codeteile ( "Functions") in Azure ausführen können. Dies bietet eine Möglichkeit, Arbeit an die Cloud zu delegieren, anstatt an Ihre lokale Anwendung, was viele Vorteile haben kann. **Azure Functions** unterstützt mehrere Entwicklungssprachen, einschließlich \# C, \# F, Node.js, Java und PHP. Weitere Informationen finden Sie auf der **Azure Functions** [Seite](/azure/azure-functions/functions-overview).

**Azure Tables** ist ein Microsoft-Clouddienst, mit dem Entwickler strukturierte, nicht SQL Daten in der Cloud speichern können, sodass sie überall leicht zugänglich sind. Der Dienst zeichnet sich durch ein schemaloses Design aus, das die Weiterentwicklung von Tabellen nach Bedarf ermöglicht und daher sehr flexibel ist. Weitere Informationen finden Sie auf der [Seite](/azure/cosmos-db/table-storage-overview) **Azure-Tabellen.**

Nach Abschluss dieses Kurses verfügen Sie über eine immersive Mixed Reality-Headsetanwendung und eine Desktop-PC-Anwendung, die folgende Schritte ausführen kann:

1. Die Desktop-PC-App ermöglicht dem Benutzer das Verschieben eines Objekts im 2D-Raum (X und Y) mit der Maus.

2. Die Bewegung von Objekten innerhalb der PC-App wird mithilfe von JSON an die Cloud gesendet, das in Form einer Zeichenfolge mit einer Objekt-ID, typ- und transformationsinformationen (X- und Y-Koordinaten) vorkommt. 

3. Die Mixed Reality-App, die über eine identische Szene wie die Desktop-App verfügt, empfängt Benachrichtigungen zur Objektbewegung vom Notification Hubs Dienst (der gerade von der Desktop-PC-App aktualisiert wurde). 

4. Nach dem Empfang einer Benachrichtigung, die die Objekt-ID, den Typ und die Transformationsinformationen enthält, wendet die Mixed Reality-App die empfangenen Informationen auf ihre eigene Szene an.

In Ihrer Anwendung liegt es an Ihnen, wie Sie die Ergebnisse in Ihren Entwurf integrieren. In diesem Kurs erfahren Sie, wie Sie einen Azure-Dienst in Ihre Unity-Project integrieren. Es ist Ihre Aufgabe, das Wissen, das Sie aus diesem Kurs gewinnen, zu nutzen, um Ihre Mixed Reality-Anwendung zu verbessern. Dieser Kurs ist ein eigenständiges Tutorial, das keine anderen Mixed Reality Labs direkt umfasst.

## <a name="device-support"></a>Geräteunterstützung

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td> MR und Azure 308: Geräteübergreifende Benachrichtigungen</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
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
- Internetzugriff für Azure-Setup und zugriff auf Notification Hubs

## <a name="before-you-start"></a>Vorbereitung

- Um Probleme bei der Erstellung dieses Projekts zu vermeiden, wird dringend empfohlen, das in diesem Tutorial erwähnte Projekt in einem Stammordner oder in einem Ordner in der Nähe des Stammordners zu erstellen (lange Ordnerpfade können zur Buildzeit Probleme verursachen).
- Sie müssen der Besitzer Ihres Microsoft-Entwickler-Portals und Ihres Anwendungsregistrierungsportals sein. Andernfalls verfügen Sie in [Kapitel 2](#chapter-2---retrieve-your-new-apps-credentials)nicht über die Berechtigung für den Zugriff auf die App.

## <a name="chapter-1---create-an-application-on-the-microsoft-developer-portal"></a>Kapitel 1: Erstellen einer Anwendung im Microsoft-Entwickler-Portal

Um den **Azure Notification Hubs-Dienst** zu verwenden, müssen Sie eine Anwendung im Microsoft-Entwickler-Portal erstellen, da Ihre Anwendung registriert werden muss, damit sie Benachrichtigungen senden und empfangen kann.

1.  Melden Sie sich beim [Microsoft-Entwickler-Portal](https://developer.microsoft.com/dashboard)an.

    > Sie müssen sich bei Ihrem Microsoft-Konto anmelden.

2.  Klicken Sie im Dashboard auf **Neue App erstellen.**

    ![Erstellen einer App](images/AzureLabs-Lab8-01.png)

3.  Es wird ein Popupfenster angezeigt, in dem Sie einen Namen für Ihre neue App reservieren müssen. Fügen Sie in das Textfeld einen entsprechenden Namen ein. Wenn der ausgewählte Name verfügbar ist, wird rechts neben dem Textfeld ein Teilstrich angezeigt. Nachdem Sie einen verfügbaren Namen eingefügt haben, klicken Sie unten links im Popup auf die Schaltfläche **Produktname reservieren.**

    ![Einen Namen umkehren](images/AzureLabs-Lab8-02.png)

4.  Nachdem die App nun erstellt wurde, können Sie mit dem nächsten Kapitel fortschreiten.

## <a name="chapter-2---retrieve-your-new-apps-credentials"></a>Kapitel 2: Abrufen der Anmeldeinformationen für neue Apps

Melden Sie sich beim Anwendungsregistrierungsportal an, in dem Ihre neue App aufgeführt wird, und rufen Sie die Anmeldeinformationen ab, die zum Einrichten des **Notification Hubs-Diensts** im **Azure-Portal** verwendet werden.

1.  Navigieren Sie zum [Anwendungsregistrierungsportal.](https://apps.dev.microsoft.com)

    ![Anwendungsregistrierungsportal](images/AzureLabs-Lab8-03.png)

    > [!WARNING] 
    > Sie müssen Ihr Microsoft-Konto für die Anmeldung verwenden.  
    > Dies **muss** das Microsoft-Konto sein, das Sie im vorherigen [Kapitel](#chapter-1---create-an-application-on-the-microsoft-developer-portal)mit dem Windows Store Entwicklerportal verwendet haben.

2.  Sie finden Ihre App im Abschnitt **Meine Anwendungen.** Sobald Sie es gefunden haben, klicken Sie darauf, und Sie werden zu einer neuen Seite mit dem App-Namen und **der Registrierung** gelangen.

    ![Ihre neu registrierte App](images/AzureLabs-Lab8-04.png)

3.  Scrollen Sie auf der Registrierungsseite nach unten, um den Abschnitt **"Anwendungsgeheimnisse"** und die **Paket-SID** für Ihre App zu finden. Kopieren Sie beides für die Einrichtung des **Azure Notification Hubs-Diensts** im nächsten Kapitel.

    ![Anwendungsgeheimnisse](images/AzureLabs-Lab8-05.png)

## <a name="chapter-3---setup-azure-portal-create-notification-hubs-service"></a>Kapitel 3: Einrichten des Azure-Portals: Erstellen eines Notification Hubs-Diensts

Wenn Ihre App-Anmeldeinformationen abgerufen wurden, müssen Sie zum Azure-Portal wechseln, in dem Sie einen Azure Notification Hubs-Dienst erstellen.

1.  Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

    > [!NOTE] 
    > Wenn Sie noch nicht über ein Azure-Konto verfügen, müssen Sie eins erstellen. Wenn Sie dieses Tutorial in einer Classroom- oder Lab-Situation durchgehen, bitten Sie Ihren Dozenten oder einen der Proctors um Hilfe beim Einrichten Ihres neuen Kontos.

2.  Klicken Sie nach der Anmeldung oben links auf **Neu,** suchen Sie nach **Notification Hub,** und drücken **_Sie die EINGABETASTE._**

    ![Suchen nach Notification Hub](images/AzureLabs-Lab8-06.png)

    > [!NOTE] 
    > Das Wort ***Neu** _ wurde in neueren Portalen möglicherweise durch _*Ressource erstellen** ersetzt.

3.  Die neue Seite enthält eine  Beschreibung des Notification Hubs-Diensts. Wählen Sie unten links in dieser Eingabeaufforderung die Schaltfläche **Erstellen** aus, um eine Zuordnung zu diesem Dienst zu erstellen.

    ![Erstellen einer Notification Hubs-Instanz](images/AzureLabs-Lab8-07.png)

4.  Nachdem Sie auf ***Erstellen*** geklickt haben:

    1.  Fügen Sie den gewünschten Namen für diese Dienstinstanz ein.

    2.  Geben Sie einen **Namespace** an, den Sie dieser App zuordnen können.

    3.  Wählen Sie einen **Standort aus.**

    4.  Wählen Sie eine **Ressourcengruppe** aus, oder erstellen Sie eine neue. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, Steuern des Zugriffs, Bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt zugeordnet sind (z. B. diese Labs), in einer gemeinsamen Ressourcengruppe zu speichern.

        > Weitere Informationen zu Azure-Ressourcengruppen finden Sie unter diesem [Link zum Verwalten einer Ressourcengruppe.](/azure/azure-resource-manager/resource-group-portal) 

    5.  Wählen Sie ein **geeignetes Abonnement aus.**

    6.  Sie müssen auch bestätigen, dass Sie die für diesen Dienst geltenden Geschäftsbedingungen verstanden haben.

    7. Klicken Sie auf **Erstellen**.

        ![Ausfüllen von Dienstdetails](images/AzureLabs-Lab8-08.png)

5.  Nachdem Sie auf **Erstellen** geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. Dies kann eine Minute dauern.

6.  Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.

    ![Benachrichtigung](images/AzureLabs-Lab8-09.png)

7.  Klicken Sie in **der Benachrichtigung auf die** Schaltfläche Zu Ressource wechseln, um Ihre neue Dienstinstanz zu untersuchen. Sie werden zu Ihrer neuen **Notification Hub-Dienstinstanz** aufgenommen.

    ![Zu Ressource wechseln](images/AzureLabs-Lab8-10.png)
    
8.  Klicken Sie auf der Übersichtsseite in der Mitte der Seite **auf Windows (WNS).** Im Bereich auf der rechten Seite werden zwei Textfelder angezeigt, für die Ihre **Paket-SID** und der Sicherheitsschlüssel aus der zuvor eingerichteten App erforderlich sind.

    ![Neu erstellter Hubdienst](images/AzureLabs-Lab8-11.png)

9. Nachdem Sie die Details in die richtigen Felder kopiert haben, klicken Sie auf Speichern, und Sie erhalten eine Benachrichtigung, wenn der Notification Hub erfolgreich aktualisiert wurde. 

    ![Kopieren von Sicherheitsdetails](images/AzureLabs-Lab8-12.png)

## <a name="chapter-4---setup-azure-portal-create-table-service"></a>Kapitel 4: Einrichten des Azure-Portals: Erstellen eines Tabellendiensts

Navigieren Sie nach Notification Hubs-Dienstinstanz zurück zu Ihrem Azure-Portal, in dem Sie einen Azure-Tabellendienst erstellen, indem Sie eine Storage erstellen.

1.  Wenn Sie sich noch nicht angemeldet haben, melden Sie sich beim [Azure-Portal an.](https://portal.azure.com)

2.  Klicken Sie nach der Anmeldung **in** der linken oberen Ecke auf Neu, suchen Sie Storage **Konto,** und geben Sie **ein.**

    > [!NOTE] 
    > Das Wort ***New** _ wurde in neueren Portalen möglicherweise durch _*Create a resource** ersetzt.

3.  Wählen Storage in der Liste die Option Konto – **Blob, Datei, Tabelle,** Warteschlange aus.

    ![Nach Speicherkonto suchen](images/AzureLabs-Lab8-13.png)

4.  Die neue Seite enthält eine Beschreibung des **Storage Kontodiensts.** Wählen Sie unten links in dieser Eingabeaufforderung die Schaltfläche **Erstellen** aus, um eine Instanz dieses Diensts zu erstellen.

    ![Erstellen einer Speicherinstanz](images/AzureLabs-Lab8-14.png)

5.  Nachdem Sie auf Erstellen **geklickt** haben, wird ein Bereich angezeigt:

    1. Fügen Sie den gewünschten **Namen für** diese Dienstinstanz ein (muss nur Kleinbuchstaben sein).

    2. Klicken **Sie unter Bereitstellungsmodell** auf **Ressourcen-Manager.**

    3.  Wählen **Sie für Kontoart** im Dropdownmenü Storage **(Allgemein v1) aus.**

    4. Wählen Sie einen geeigneten **Speicherort aus.**
    
    5.  Wählen Sie **im Dropdownmenü** Replikation die Option Georedundanten Speicher mit Lesezugriff **(RA-GRS) aus.**

    6.  Klicken **Sie unter Leistung** auf **Standard.**

    7.  Wählen Sie **im Abschnitt Sichere Übertragung erforderlich** die Option Deaktiviert **aus.**

    8.  Wählen Sie **im Dropdownmenü** Abonnement ein entsprechendes Abonnement aus.

    9.  Wählen Sie eine **Ressourcengruppe aus,** oder erstellen Sie eine neue. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, Steuern des Zugriffs, Bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. B. diesen Labs) zugeordnet sind, unter einer gemeinsamen Ressourcengruppe zu halten.

        > Wenn Sie mehr über Azure-Ressourcengruppen erfahren möchten, folgen Sie diesem Link zum Verwalten [einer Ressourcengruppe.](/azure/azure-resource-manager/resource-group-portal)

    10. Lassen **Sie Virtuelle Netzwerke** **deaktiviert,** wenn dies eine Option für Sie ist.

    11. Klicken Sie auf **Erstellen**.

        ![Ausfüllen von Speicherdetails](images/AzureLabs-Lab8-15.png)

6.  Nachdem Sie auf **Erstellen** geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. Dies kann eine Minute dauern.

7.  Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt. Klicken Sie auf die Benachrichtigungen, um Ihre neue Dienstinstanz zu untersuchen.

    ![Neue Speicherbenachrichtigung](images/AzureLabs-Lab8-16.png)

8.  Klicken Sie in **der Benachrichtigung auf die** Schaltfläche Zu Ressource wechseln, um Ihre neue Dienstinstanz zu untersuchen. Sie werden zur neuen Übersichtsseite für Storage Service-Instanz weiter.

    ![Zu Ressource wechseln](images/AzureLabs-Lab8-17.PNG)

9. Klicken Sie auf der Übersichtsseite auf der rechten Seite auf **Tabellen**.
    
    ![](images/AzureLabs-Lab8-18.PNG)

10. Der Bereich auf der rechten Seite ändert sich so, dass die **Tabellendienstinformationen** angezeigt werden, in denen Sie eine neue Tabelle hinzufügen müssen. Klicken Sie hierzu oben links auf die Schaltfläche **+**  Tabelle.

    ![Tabellen öffnen](images/AzureLabs-Lab8-19.png)

11. Eine neue Seite wird angezeigt, auf der Sie einen **Tabellennamen eingeben müssen.** Dies ist der Name, mit dem Sie in späteren Kapiteln auf die Daten in Ihrer Anwendung verweisen. Fügen Sie einen entsprechenden Namen ein, und klicken Sie **auf OK.**

    ![Erstellen einer neuen Tabelle](images/AzureLabs-Lab8-20.png)    

12. Nachdem die neue Tabelle erstellt wurde, wird sie  auf der Seite Tabellendienst (unten) angezeigt.

    ![Neue Tabelle erstellt](images/AzureLabs-Lab8-21.png)
    

## <a name="chapter-5---completing-the-azure-table-in-visual-studio"></a>Kapitel 5: Abschließen der Azure-Tabelle in Visual Studio

Nachdem Ihr **Speicherkonto für den** Tabellenspeicherdienst eingerichtet wurde, ist es an der Zeit, ihm Daten hinzuzufügen, die zum Speichern und Abrufen von Informationen verwendet werden. Die Bearbeitung Ihrer Tabellen kann über **Visual Studio.**

1.  Öffnen Sie **Visual Studio**.

2.  Klicken Sie im Menü auf **Ansicht**  >  **Cloud-Explorer**.

    ![Öffnen des Cloud-Explorers](images/AzureLabs-Lab8-22.png)

3.  Die **Cloud-Explorer** wird als angedocktes Element geöffnet (da das Laden einige Zeit dauern kann).

    > [!NOTE] 
    > Wenn das Abonnement, das  Sie zum Erstellen Ihrer Storage-Konten verwendet haben, nicht sichtbar ist, stellen Sie sicher, dass Sie über Die folgenden Informationen verfügen: 
    > - Sie sind bei demselben Konto angemeldet wie das Konto, das Sie für das Azure-Portal verwendet haben.
    > - Wählen Sie Auf der Seite Kontoverwaltung Ihr Abonnement aus (möglicherweise müssen Sie einen Filter aus Ihren Kontoeinstellungen anwenden):  
    >
    >   ![Abonnement suchen](images/AzureLabs-Lab8-22-5.png)

4.  Ihre Azure-Clouddienste werden angezeigt. Suchen **Storage Konten,** und klicken Sie auf den Pfeil links davon, um Ihre Konten zu erweitern.

    ![Öffnen von Speicherkonten](images/AzureLabs-Lab8-23.png)

5.  Nach der Erweiterung sollte Ihr neu **erstelltes Storage verfügbar** sein. Klicken Sie auf den Pfeil links neben Ihrem Speicher,  und suchen Sie nach dem Erweitern  nach Tabellen, und klicken Sie auf den Pfeil daneben, um die Tabelle zu öffnen, die Sie im letzten Kapitel erstellt haben. Doppelklicken Sie auf die **Tabelle**.

    ![Tabelle mit geöffneten Szenenobjekten](images/AzureLabs-Lab8-24.png)

6.  Die Tabelle wird in der Mitte des Fensters Visual Studio geöffnet. Klicken Sie auf das Tabellensymbol mit **+** dem (Pluszeichen) darauf.

    ![Hinzufügen einer neuen Tabelle](images/AzureLabs-Lab8-25.png)

7.  Es wird ein Fenster angezeigt, in dem Sie aufgefordert werden, *entität hinzuzufügen.* Sie erstellen insgesamt drei Entitäten mit jeweils mehreren Eigenschaften. Sie werden feststellen, *dass PartitionKey* und *RowKey* bereits bereitgestellt wurden, da diese von der Tabelle verwendet werden, um Ihre Daten zu finden. 

    ![Partition und Zeilenschlüssel](images/AzureLabs-Lab8-26.png)

8. Aktualisieren Sie *den Wert* von **PartitionKey** und **RowKey** wie folgt (denken Sie daran, dies für jede hinzugefügte Zeileneigenschaft zu tun, aber erhöhen Sie den RowKey jedes Mal):

    ![Hinzufügen der richtigen Werte](images/AzureLabs-Lab8-26-5.png)

9.  Klicken **Sie auf Eigenschaft hinzufügen,** um zusätzliche Datenzeilen hinzuzufügen. Stellen Sie sicher, dass Ihre erste leere Tabelle mit der folgenden Tabelle übereinstimmen soll.

10. Klicken Sie anschließend auf **OK**.

    ![Klicken Sie auf OK, wenn Sie fertig sind.](images/AzureLabs-Lab8-27.png)

    > [!WARNING] 
    > Stellen Sie sicher, dass Sie **den Typ der Einträge** **X,** **Y** und **Z** in Double **geändert haben.** 

11. Sie werden feststellen, dass Ihre Tabelle jetzt eine Datenzeile enthält. Klicken Sie erneut **+** auf das Symbol (Pluszeichen), um eine weitere Entität hinzuzufügen.

    ![erste Zeile](images/AzureLabs-Lab8-27-5.png)

12. Erstellen Sie eine zusätzliche Eigenschaft, und legen Sie dann die Werte der neuen Entität so fest, dass sie den unten gezeigten werten.

    ![Hinzufügen eines Cubes](images/AzureLabs-Lab8-28.png)

13. Wiederholen Sie den letzten Schritt, um eine weitere Entität hinzuzufügen. Legen Sie die Werte für diese Entität auf die unten gezeigten fest.

    ![Zylinder hinzufügen](images/AzureLabs-Lab8-29.png)

14. Ihre Tabelle sollte nun wie die folgende aussehen.

    ![Tabelle abgeschlossen](images/AzureLabs-Lab8-30.png)

15. Sie haben dieses Kapitel abgeschlossen. Stellen Sie sicher, dass Sie speichern.

## <a name="chapter-6---create-an-azure-function-app"></a>Kapitel 6: Erstellen einer Azure-Funktions-App

Erstellen Sie eine Azure-Funktions-App, die von  der Desktopanwendung aufgerufen wird, um den Tabellendienst zu aktualisieren und eine Benachrichtigung über den **Notification Hub zu senden.**

Zunächst müssen Sie eine Datei erstellen, mit der Ihre Azure-Funktion die benötigten Bibliotheken laden kann.

1.  Öffnen **Editor** (drücken Sie Windows, und geben Sie Editor ein).

    ![Editor öffnen](images/AzureLabs-Lab8-31.png)

2.  Wenn Editor geöffnet ist, fügen Sie die json-Struktur darunter ein. Nachdem Sie dies getan haben, speichern Sie es auf Ihrem Desktop alsproject.js **auf**. Es ist wichtig, dass die Benennung richtig ist: Stellen Sie sicher, dass sie **KEINE** .txthat. Diese Datei definiert die Bibliotheken, die Ihre Funktion verwendet, wenn Sie NuGet wird ihnen vertraut vorkommen.

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "7.0.0",
            "Microsoft.Azure.NotificationHubs" : "1.0.9",
            "Microsoft.Azure.WebJobs.Extensions.NotificationHubs" :"1.1.0"
        }
        }
    }
    }
    ```

3.  Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

4.  Klicken Sie nach der Anmeldung in der linken oberen Ecke auf **Neu,** suchen Sie nach **Funktions-App,** und drücken Sie die **EINGABETASTE.**

    ![Nach Funktions-App suchen](images/AzureLabs-Lab8-32.png)

    > [!NOTE] 
    > Das Wort **Neu** wurde in neueren Portalen möglicherweise durch **Ressource** erstellen ersetzt.

5.  Die neue Seite enthält eine Beschreibung des **Funktions-App-Diensts.** Wählen Sie unten links in dieser Eingabeaufforderung die Schaltfläche **Erstellen** aus, um eine Zuordnung zu diesem Dienst zu erstellen.

    ![Funktions-App-Instanz](images/AzureLabs-Lab8-33.png)

6.  Nachdem Sie auf Erstellen **geklickt** haben, geben Sie Folgendes ein:

    1. Fügen **Sie für App-Name** den gewünschten Namen für diese Dienstinstanz ein.

    2. Wählen Sie ein **Abonnement** aus.

    3. Wählen Sie den für Sie geeigneten Tarif aus. Wenn Sie zum ersten Mal eine Funktion App Service **erstellen,** sollte ihnen ein free-Tarif zur Verfügung stehen.

    4. Wählen Sie eine **Ressourcengruppe aus,** oder erstellen Sie eine neue. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, Steuern des Zugriffs, Bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. B. diesen Labs) zugeordnet sind, unter einer gemeinsamen Ressourcengruppe zu halten.

        > Wenn Sie mehr über Azure-Ressourcengruppen erfahren möchten, folgen Sie diesem Link zum [Verwalten einer Ressourcengruppe.](/azure/azure-resource-manager/resource-group-portal)

    5. Klicken **Sie für** betriebssystem auf Windows, da dies die vorgesehene Plattform ist.

    6. Wählen Sie einen **Hostingplan** aus (in diesem Tutorial wird ein **Verbrauchsplan verwendet).**

    7. Wählen Sie einen **Standort** aus (wählen Sie den gleichen Speicherort wie den Speicher aus, den **Sie im vorherigen Schritt erstellt haben).**

    8. Im Abschnitt **Storage** müssen Sie den Storage Service auswählen, den Sie **im vorherigen Schritt erstellt haben.**

    9. Sie benötigen keine *Anwendungs-Insights* in dieser App, daher können Sie sie aus **lassen.**

    10. Klicken Sie auf **Erstellen**.

        ![Erstellen einer neuen Instanz](images/AzureLabs-Lab8-34.png)

7.  Nachdem Sie auf Erstellen **geklickt** haben, müssen Sie warten, bis der Dienst erstellt wurde. Dies kann eine Minute dauern.

8.  Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.

    ![Neue Benachrichtigung](images/AzureLabs-Lab8-35.png)

9.  Klicken Sie auf die Benachrichtigungen, um Ihre neue Dienstinstanz zu untersuchen.

10. Klicken Sie in **der Benachrichtigung auf die** Schaltfläche Zu Ressource wechseln, um Ihre neue Dienstinstanz zu untersuchen. 

    ![Zu Ressource wechseln](images/AzureLabs-Lab8-36.png)

11. Klicken Sie **+** auf das Symbol (Pluszeichen) neben *Functions*, um ein neues *zu erstellen.*

    ![Neue Funktion hinzufügen](images/AzureLabs-Lab8-37.png)

12. Im zentralen Bereich wird das Fenster **Funktionserstellung** angezeigt. Ignorieren Sie die Informationen in der oberen Hälfte des Bereichs, und klicken Sie auf Benutzerdefinierte **Funktion,** die sich im unteren Bereich befindet (im blauen Bereich wie unten).

    ![Benutzerdefinierte Funktion](images/AzureLabs-Lab8-38.png)

13. Auf der neuen Seite im Fenster werden verschiedene Funktionstypen angezeigt. Scrollen Sie nach unten, um die violetten Typen zu sehen, und klicken Sie **auf HTTP PUT-Element.**

    ![http put link](images/AzureLabs-Lab8-39.png)

    > [!IMPORTANT]
    > Möglicherweise müssen Sie weiter nach unten auf der Seite scrollen (und dieses Bild sieht möglicherweise nicht genau gleich aus, wenn Azure-Portal-Updates stattgefunden haben), aber Sie suchen nach einem Element namens *HTTP PUT*.

14. Das **HTTP PUT-Fenster** wird angezeigt, in dem Sie die Funktion konfigurieren müssen (siehe abbildung unten).

    1.  Wählen **Sie für Sprache** im Dropdownmenü C \# aus.

    2.  Geben **Sie unter Name** einen entsprechenden Namen ein.

    3.  Wählen Sie im **Dropdownmenü Authentifizierungsebene** die Option **Funktion aus.**

    4.  Für den **Abschnitt Tabellenname** müssen Sie den genauen  Namen verwenden, den Sie zuvor zum Erstellen Des Tabellendiensts verwendet haben (einschließlich desselben Buchstabens).

    5.  Verwenden Sie **Storage Abschnitt Kontoverbindung** das Dropdownmenü, und wählen Sie dort Ihr Speicherkonto aus. Wenn er nicht dort  ist, klicken Sie neben dem Abschnittstitel auf den Link Neu, um einen weiteren Bereich zu zeigen, in dem Ihr Speicherkonto aufgeführt werden soll.

        ![Neuer Speicher](images/AzureLabs-Lab8-40.png)

15. Klicken **Sie auf** Erstellen, und Sie erhalten eine Benachrichtigung, dass Ihre Einstellungen erfolgreich aktualisiert wurden.

    ![create-Funktion](images/AzureLabs-Lab8-41.png)

16. Nachdem Sie auf **Erstellen** geklickt haben, werden Sie zum Funktions-Editor umgeleitet.

    ![Funktionscode aktualisieren](images/AzureLabs-Lab8-42.png)

17. Fügen Sie den folgenden Code in den Funktions-Editor ein (ersetzen Sie den Code in der Funktion):

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Microsoft.Azure.NotificationHubs;
    using Newtonsoft.Json;

    public static async Task Run(UnityGameObject gameObj, CloudTable table, IAsyncCollector<Notification> notification, TraceWriter log)
    {
        //RowKey of the table object to be changed
        string rowKey = gameObj.RowKey;

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<UnityGameObject>("UnityPartitionKey", rowKey); 

        TableResult result = table.Execute(operation);

        //Create a UnityGameObject so to set its parameters
        UnityGameObject existingGameObj = (UnityGameObject)result.Result; 

        existingGameObj.RowKey = rowKey;
        existingGameObj.X = gameObj.X;
        existingGameObj.Y = gameObj.Y;
        existingGameObj.Z = gameObj.Z;

        //Replace the table appropriate table Entity with the value of the UnityGameObject
        operation = TableOperation.Replace(existingGameObj); 

        table.Execute(operation);

        log.Verbose($"Updated object position");

        //Serialize the UnityGameObject
        string wnsNotificationPayload = JsonConvert.SerializeObject(existingGameObj);
        
        log.Info($"{wnsNotificationPayload}");

        var headers = new Dictionary<string, string>();

        headers["X-WNS-Type"] = @"wns/raw";

        //Send the raw notification to subscribed devices
        await notification.AddAsync(new WindowsNotification(wnsNotificationPayload, headers)); 

        log.Verbose($"Sent notification");
    }

    // This UnityGameObject represent a Table Entity
    public class UnityGameObject : TableEntity
    {
        public string Type { get; set; }
        public double X { get; set; }
        public double Y { get; set; }
        public double Z { get; set; }
        public string RowKey { get; set; }
    }
    ```

    > [!NOTE]
    > Mithilfe der enthaltenen Bibliotheken empfängt die Funktion den Namen und speicherort des Objekts, das in der Unity-Szene verschoben wurde (als C#-Objekt namens **UnityGameObject**). Dieses Objekt wird dann verwendet, um die Objektparameter in der erstellten Tabelle zu aktualisieren. Anschließend wird von der Funktion der erstellte Notification Hub-Dienst aufruft, der alle abonnierten Anwendungen benachrichtigt.

18. Klicken Sie nach dem Code auf **Speichern.**

19. Klicken Sie als Nächstes auf das Symbol (Pfeil) auf der rechten **\<** Seite der Seite.

    ![Öffnen des Uploadbereichs](images/AzureLabs-Lab8-43.png)

20. Ein Bereich wird von rechts ein- und einschieben. Klicken Sie in diesem Bereich **auf Hochladen**, und ein Dateibrowser wird angezeigt.

21. Navigieren Sie zur Datei  , und klicken Sie aufproject.jsDatei, die Sie **zuvor** in Editor erstellt haben, und klicken Sie dann auf **die Schaltfläche** Öffnen. Diese Datei definiert die Bibliotheken, die Ihre Funktion verwendet.

    ![JSON hochladen](images/AzureLabs-Lab8-44.png)

22. Wenn die Datei hochgeladen wurde, wird sie im Bereich auf der rechten Seite angezeigt. Wenn Sie darauf klicken, wird es im **Funktions-Editor** geöffnet. Er muss **genau wie** das nächste Bild (unter Schritt 23) aussehen.

23. Klicken Sie dann im Bereich auf der linken Seite unter **Functions** auf den **Link** Integrieren.

    ![integrate-Funktion](images/AzureLabs-Lab8-45.png)

24. Klicken Sie auf der nächsten Seite in der oberen rechten Ecke auf **Erweiterter Editor** (wie unten dargestellt).

    ![erweiterten Editor öffnen](images/AzureLabs-Lab8-46.png)

25. Ein **function.js** datei wird im zentrierten Bereich geöffnet, der durch den folgenden Codeausschnitt ersetzt werden muss. Dies definiert die Funktion, die Sie erstellen, und die Parameter, die an die Funktion übergeben werden.

    ```json
    {
    "bindings": [
        {
        "authLevel": "function",
        "type": "httpTrigger",
        "methods": [
            "get",
            "post"
        ],
        "name": "gameObj",
        "direction": "in"
        },
        {
        "type": "table",
        "name": "table",
        "tableName": "SceneObjectsTable",
        "connection": "mrnothubstorage_STORAGE",
        "direction": "in"
        },
        {
        "type": "notificationHub",
        "direction": "out",
        "name": "notification",
        "hubName": "MR_NotHub_ServiceInstance",
        "connection": "MRNotHubNS_DefaultFullSharedAccessSignature_NH",
        "platform": "wns"
        }
    ]
    }
    ```

26. Ihr Editor sollte nun wie in der folgenden Abbildung aussehen:

    ![Zurück zum Standard-Editor](images/AzureLabs-Lab8-47.png)

27. Möglicherweise stellen Sie fest, dass die Eingabeparameter, die Sie gerade eingefügt haben, möglicherweise nicht mit Ihren Tabellen- und Speicherdetails übereinstimmen und daher mit Ihren Informationen aktualisiert werden müssen. **Gehen Sie hier nicht vor,** da dies als Nächstes behandelt wird. Klicken Sie einfach **auf den Link Standard-Editor** in der oberen rechten Ecke der Seite, um zurück zu wechseln.

28. Klicken Sie im **Standard-Editor** unter Eingaben **auf Azure Table Storage (Tabelle)**.  
    
    ![Tabelleneingaben](images/AzureLabs-Lab8-47-5.png)

29. Stellen Sie sicher, dass die **folgende Übereinstimmung mit Ihren** Informationen besteht, da sie sich unterscheiden können (unter den folgenden Schritten befindet sich ein Bild):

    1.  **Tabellenname:** Der Name der Tabelle, die Sie in Ihrem Azure Storage Tabellendienst erstellt haben.

    2.  **Storage Kontoverbindung: Klicken** Sie auf **neu,** das neben dem Dropdownmenü angezeigt wird, und rechts neben dem Fenster wird ein Bereich angezeigt.

        ![Neuer Speicher](images/AzureLabs-Lab8-48.png)

        1.  Wählen Sie **Storage Konto aus,** das Sie zuvor zum Hosten der **Funktions-Apps erstellt haben.**

        2. Sie werden feststellen, dass **Storage Kontoverbindungswert** erstellt wurde.

        3. Klicken Sie auf **Speichern,** sobald Sie fertig sind.

    3.  Die **Seite Eingaben** sollte nun mit der unten angegebenen Seite übereinstimmen, auf der **Ihre Informationen angezeigt** werden.

        ![Eingaben abgeschlossen](images/AzureLabs-Lab8-49.png)

30. Klicken Sie als Nächstes unter Ausgaben auf **Azure Notification Hub (Benachrichtigung).**  Stellen Sie sicher, dass Folgendes mit Ihren **Informationen** übereinstimmen, da sie sich unterscheiden können (unter den folgenden Schritten befindet sich ein Bild):

    1.  **Notification Hub-Name:** Dies ist der Name Ihrer Notification Hub-Dienstinstanz, die Sie zuvor erstellt haben. 

    2.  **Notification Hubs Namespaceverbindung:** Klicken Sie **auf neu,** das neben dem Dropdownmenü angezeigt wird.

        ![Überprüfen von Ausgaben](images/AzureLabs-Lab8-50.png)

    3. Das Popupfenster **Verbindung** wird angezeigt (siehe Abbildung unten), in dem Sie den **Namespace** des **Notification Hubs** auswählen müssen, den Sie zuvor eingerichtet haben.

    4. Wählen Sie im mittleren Dropdownmenü Ihren **Notification Hub-Namen** aus.

    5.  Legen Sie das Dropdownmenü **Richtlinie** auf **DefaultFullSharedAccessSignature** fest.

    6. Klicken Sie auf die Schaltfläche **Auswählen,** um zurückzugehen.

        ![Ausgabeupdate](images/AzureLabs-Lab8-51.png)

31.  Die Seite Ausgaben sollte jetzt mit den unten **angegebenen** Übereinstimmen, aber stattdessen mit **Ihren** Informationen übereinstimmen. Klicken Sie unbedingt auf **Speichern.**

> [!WARNING]
> *Bearbeiten Sie den Notification Hub-Namen nicht direkt* (dies sollte alles mithilfe des **Erweiterter Editor** erfolgen, vorausgesetzt, Sie haben die vorherigen Schritte ordnungsgemäß ausgeführt.

![Ausgaben abgeschlossen](images/AzureLabs-Lab8-50.png)

32. An diesem Punkt sollten Sie die Funktion testen, um sicherzustellen, dass sie funktioniert. Aufgabe: 

    1. Navigieren Sie noch einmal zur Funktionsseite:

        ![Ausgaben abgeschlossen](images/AzureLabs-Lab8-50-1.png)

    2. Klicken Sie auf der Funktionsseite ganz rechts auf die Registerkarte **Test,** um das Blatt *Test* zu öffnen:

        ![Ausgaben abgeschlossen](images/AzureLabs-Lab8-50-2.png)

    3. Fügen Sie im Textfeld **Anforderungstext** des Blatts den folgenden Code ein:

        ```
        {  
            "Type":null,
            "X":3,
            "Y":0,
            "Z":1,
            "PartitionKey":null,
            "RowKey":"Obj2",
            "Timestamp":"0001-01-01T00:00:00+00:00",
            "ETag":null
        }
        ```

    4. Wenn der Testcode vorhanden ist, klicken Sie unten rechts auf die Schaltfläche **Ausführen,** und der Test wird ausgeführt. Die Ausgabeprotokolle des Tests werden im Konsolenbereich unter ihrem Funktionscode angezeigt.

        ![Ausgaben abgeschlossen](images/AzureLabs-Lab8-50-3.png)

    > [!WARNING]
    > Wenn der obige Test fehlschlägt, müssen Sie überprüfen, ob Sie die obigen Schritte genau ausgeführt haben, insbesondere die Einstellungen im **Integrationsbereich.** 

## <a name="chapter-7---set-up-desktop-unity-project"></a>Kapitel 7: Einrichten von Unity-Desktop Project

> [!IMPORTANT]
> Die Desktopanwendung, die Sie jetzt erstellen, funktioniert im Unity-Editor **nicht.** Sie muss außerhalb des Editors ausgeführt werden, indem sie dem Erstellen der Anwendung folgt und Visual Studio (oder die bereitgestellte Anwendung) verwendet. 

Im Folgenden finden Sie eine typische Einrichtung für die Entwicklung mit Unity und Mixed Reality und ist daher eine gute Vorlage für andere Projekte.

Richten Sie Ihr immersives Mixed Reality-Headset ein, und testen Sie es.

> [!NOTE] 
> Für diesen Kurs benötigen Sie **keine** Motion Controllers. Wenn Sie Unterstützung beim Einrichten des immersiven Headsets benötigen, folgen Sie diesem [Link, um Windows Mixed Reality einzurichten.](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)

1.  Öffnen Sie **Unity,** und klicken Sie auf **Neu.**

    ![Neues Unity-Projekt](images/AzureLabs-Lab8-52.png)

2.  Sie müssen einen Unity-Project Namen angeben und **UnityDesktopNotifHub** einfügen. Stellen Sie sicher, dass der Projekttyp auf **3D** festgelegt ist. Legen Sie den **Speicherort** auf einen für Sie geeigneten Ort fest (denken Sie daran, dass näher an den Stammverzeichnissen besser ist). Klicken Sie dann auf **Projekt erstellen.**

    ![Erstellen des Projekts](images/AzureLabs-Lab8-53.png)

3.  Wenn Unity geöffnet ist, sollten Sie überprüfen, ob der **Standardskript-Editor** auf **Visual Studio** festgelegt ist. Navigieren **Sie** zu  >  **Einstellungen** bearbeiten, und navigieren Sie dann im neuen Fenster zu **Externe Tools.** Ändern Sie **den externen Skript-Editor** in **Visual Studio 2017**. Schließen Sie das Fenster **Einstellungen.**

    ![Festlegen externer VS-Tools](images/AzureLabs-Lab8-54.png)

4.  Wechseln Sie als Nächstes zu  >  **Dateibuild Einstellungen,** wählen Sie **Universelle Windows Plattform** aus, und klicken Sie dann auf die Schaltfläche **Plattform wechseln,** um Ihre Auswahl anzuwenden.

    ![switch platforms](images/AzureLabs-Lab8-55.png)

5.  Stellen Sie im  >  **Dateibuild Einstellungen** sicher, dass:

    1.  **Zielgerät** ist auf **Beliebiges Gerät** festgelegt

        > Diese Anwendung ist für Ihren Desktop vorgesehen, muss also **ein beliebiges Gerät** sein.

    2.  **Buildtyp** ist auf **D3D** festgelegt

    3.  **SDK** ist auf **Latest installed (Neueste Installation)** festgelegt.

    4.  **Visual Studio Version** ist auf **Latest installed (Neueste installiert)** festgelegt.

    5.  **Build und Ausführung** ist auf **Lokaler Computer** festgelegt.

    6.  Hier lohnt es sich, die Szene zu speichern und sie dem Build hinzuzufügen.

        1. Wählen Sie hierzu **Öffnende Szenen hinzufügen aus.** Ein Speicherfenster wird angezeigt.

            ![Hinzufügen von offenen Szenen](images/AzureLabs-Lab8-56.png)

        2. Erstellen Sie einen neuen Ordner für diese und jede zukünftige Szene, und wählen Sie dann die Schaltfläche **Neuer Ordner** aus, um einen neuen Ordner zu erstellen, und nennen Sie ihn **Szenen**.

            ![Ordner "neue Szenen"](images/AzureLabs-Lab8-57.png)

        3. Öffnen Sie den neu erstellten Ordner **Scenes,** und geben Sie dann im Textfeld **Dateiname:** **NH Desktop \_ \_ Scene** ein, und klicken Sie dann auf **Speichern.**

            ![neue NH_Desktop_Scene](images/AzureLabs-Lab8-58.png)

    7.  Die übrigen Einstellungen in **Build Einstellungen** sollten vorerst als Standard festgelegt werden.

6.  Klicken Sie im gleichen Fenster auf die Schaltfläche **Player Einstellungen.** Dadurch wird der zugehörige Bereich in dem Bereich geöffnet, in dem sich der **Inspektor** befindet.

7.  In diesem Bereich müssen einige Einstellungen überprüft werden:

    1.  Auf der Registerkarte **Andere Einstellungen:**

        1.  **Skriptlaufzeitversion** muss **experimentell sein (.NET 4.6-Entsprechung)**

        2. **Skript-Back-End** sollte **.NET** sein

        3. **Der API-Kompatibilitätsgrad** sollte **.NET 4.6** sein.

            ![Net-Version 4.6](images/AzureLabs-Lab8-59.png)

    2.  Aktivieren **Sie** auf der Registerkarte Veröffentlichen Einstellungen unter **Funktionen** Folgendes:

        - **InternetClient**

            ![Tick-Internetclient](images/AzureLabs-Lab8-60.png)

8.  Zurück in **Build Einstellungen** Unity *C \# Projects* ist nicht mehr abgeblendet. Aktivieren Sie das Kontrollkästchen daneben.

9.  Schließen Sie das Fenster **Buildeinstellungen**.

10. Speichern Sie Ihre Szene, und Project **Datei**  >  **speichern Szene/Datei**  >  **speichern Project**.

    > [!IMPORTANT]
    > Wenn Sie die *Unity Set up-Komponente* für dieses Projekt (Desktop-App) überspringen und direkt mit dem Code fortfahren möchten, können Sie [dieses UNITYPACKAGE herunterladen,](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage)als [**benutzerdefiniertes Paket**](https://docs.unity3d.com/Manual/AssetPackages.html)in Ihr Projekt importieren und dann mit Kapitel [9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)fortfahren.  Sie müssen weiterhin die Skriptkomponenten hinzufügen.

## <a name="chapter-8---importing-the-dlls-in-unity"></a>Kapitel 8: Importieren der DLLs in Unity

Sie verwenden Azure Storage für Unity (das selbst das .NET SDK für Azure nutzt). Weitere Informationen zu Azure Storage für Unity unter diesem [Link.](/sandbox/gamedev/unity/azure-storage-unity)

Derzeit gibt es ein bekanntes Problem in Unity, bei dem Plug-Ins nach dem Import neu konfiguriert werden müssen. Diese Schritte (4 bis 7 in diesem Abschnitt) sind nicht mehr erforderlich, nachdem der Fehler behoben wurde.

Um das SDK in Ihr eigenes Projekt zu importieren, stellen Sie sicher, dass Sie das neueste [**UNITYPACKAGE**](https://aka.ms/azstorage-unitysdk) von GitHub heruntergeladen haben. Gehen Sie nun wie folgt vor:

1.  Fügen Sie **unitypackage** mithilfe der Menüoption **Assets Import Package Custom Package \> \> (Benutzerdefiniertes Paket importieren)** zu Unity hinzu.

2.  Im daraufhin angezeigten Feld **Unity-Paket importieren** können Sie alles unter **_Plug-In_ \> *Storage** auswählen.  Deaktivieren Sie alle anderen Informationen, da sie für diesen Kurs nicht benötigt werden.

    ![Importieren in ein Paket](images/AzureLabs-Lab8-61.png)

3.  Klicken Sie auf die Schaltfläche ***Importieren,*** um die Elemente ihrem Projekt hinzuzufügen.

4.  Wechseln Sie in der **Ansicht Project** zum Ordner Storage unter **Plug-Ins,** und wählen Sie *nur* die folgenden Plug-Ins aus:

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

![Deaktivieren Sie Alle Plattformen.](images/AzureLabs-Lab8-62.png)

5.  Deaktivieren Sie bei auswahl *dieser spezifischen Plug-Ins* die Option  **Beliebige Plattform,** **deaktivieren** Sie **WSAPlayer,** und klicken Sie dann auf **Anwenden.**

    ![Anwenden von Plattform-DLL-Dateien](images/AzureLabs-Lab8-63.png)

    > [!NOTE] 
    > Wir markieren diese speziellen Plug-Ins so, dass sie nur im Unity-Editor verwendet werden. Dies liegt daran, dass es verschiedene Versionen der gleichen Plug-Ins im WSA-Ordner gibt, die verwendet werden, nachdem das Projekt aus Unity exportiert wurde.

6.  Wählen Sie im Ordner **Storage** Plug-Ins nur Folgendes aus:

    -   Microsoft.Data.Services.Client

        ![set don't process for dlls](images/AzureLabs-Lab8-64.png)

7.  Aktivieren Sie unter Plattform **Einstellungen** das Kontrollkästchen **Nicht verarbeiten,** und klicken Sie auf **_Anwenden._**

    ![Keine Verarbeitung anwenden](images/AzureLabs-Lab8-65.png)

    > [!NOTE] 
    > Wir markieren dieses Plug-In als "Nicht verarbeiten", da der Unity-Assemblypatcher Schwierigkeiten bei der Verarbeitung dieses Plug-Ins hat. Das Plug-In funktioniert auch dann, wenn es nicht verarbeitet wird.

## <a name="chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project"></a>Kapitel 9: Erstellen der TableToScene-Klasse im Desktop Unity-Projekt

Sie müssen nun die Skripts erstellen, die den Code zum Ausführen dieser Anwendung enthalten.

Das erste Skript, das Sie erstellen müssen, ist **TableToScene,** das für Folgendes zuständig ist:

-   Lesen von Entitäten in der Azure-Tabelle.
-   Bestimmen Sie mithilfe der Tabellendaten, welche Objekte erstellt werden und an welcher Position.

Das zweite Skript, das Sie erstellen müssen, ist **CloudScene,** das für Folgendes zuständig ist:

-   Registrieren des Linksklick-Ereignisses, damit der Benutzer Objekte um die Szene ziehen kann.
-   Serialisieren der Objektdaten aus dieser Unity-Szene und Senden an die Azure-Funktions-App.

So erstellen Sie diese Klasse:

1.  Klicken Sie mit der rechten Maustaste auf **den Assetordner** im Project **Bereich** Ordner  >  **erstellen.** Nennen Sie den Ordner **Scripts**.

    ![Ordner "Skripts erstellen"](images/AzureLabs-Lab8-66.png)

    ![Ordner "Skripts erstellen" 2](images/AzureLabs-Lab8-67.png)

2.  Doppelklicken Sie auf den soeben erstellten Ordner, um ihn zu öffnen.

3.  Klicken Sie mit der rechten Maustaste in **den Ordner Skripts,** und klicken **Sie auf**  >  **C#-Skript erstellen.** Nennen Sie das **Skript TableToScene**.

    ![Neues C#-Skript ](images/AzureLabs-Lab8-68.png)
     ![ TableToScene umbenennen](images/AzureLabs-Lab8-69.png)

4.  Doppelklicken Sie auf das Skript, um es im Visual Studio 2017 zu öffnen.

5.  Fügen Sie die folgenden Namespaces hinzu:

    ```csharp
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Auth;
    using Microsoft.WindowsAzure.Storage.Table;
    using UnityEngine;
    ```

6.  Fügen Sie innerhalb der -Klasse die folgenden Variablen ein:

    ```csharp
        /// <summary>    
        /// allows this class to behave like a singleton
        /// </summary>    
        public static TableToScene instance;

        /// <summary>    
        /// Insert here you Azure Storage name     
        /// </summary>    
        private string accountName = " -- Insert your Azure Storage name -- ";

        /// <summary>    
        /// Insert here you Azure Storage key    
        /// </summary>    
        private string accountKey = " -- Insert your Azure Storage key -- ";
    ```
    
    > [!NOTE] 
    > Ersetzen Sie **den Wert accountName** durch Ihren Azure Storage-Dienstnamen und **accountKey-Wert** durch den Schlüsselwert aus dem Azure Storage-Dienst im Azure-Portal (siehe Abbildung unten). 
    >
    > ![Abrufen des Kontoschlüssels](images/AzureLabs-Lab8-70.png)

7.  Fügen Sie nun die **Methoden Start() und** **Awake() hinzu,** um die -Klasse zu initialisieren.

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {  
            // Call method to populate the scene with new objects as 
            // pecified in the Azure Table
            PopulateSceneFromTableAsync();
        }
    ```

8.  Fügen Sie in der **TableToScene-Klasse** die Methode hinzu, die die Werte aus der Azure-Tabelle abruft und sie verwendet, um die entsprechenden Primitive in der Szene zu erstellen.

    ```csharp
        /// <summary>    
        /// Populate the scene with new objects as specified in the Azure Table    
        /// </summary>    
        private async void PopulateSceneFromTableAsync()
        {
            // Obtain credentials for the Azure Storage
            StorageCredentials creds = new StorageCredentials(accountName, accountKey);

            // Storage account
            CloudStorageAccount account = new CloudStorageAccount(creds, useHttps: true);
            
            // Storage client
            CloudTableClient client = account.CreateCloudTableClient(); 
            
            // Table reference
            CloudTable table = client.GetTableReference("SceneObjectsTable");

            TableContinuationToken token = null;

            // Query the table for every existing Entity
            do
            {
                // Queries the whole table by breaking it into segments
                // (would happen only if the table had huge number of Entities)
                TableQuerySegment<AzureTableEntity> queryResult = await table.ExecuteQuerySegmentedAsync(new TableQuery<AzureTableEntity>(), token); 

                foreach (AzureTableEntity entity in queryResult.Results)
                {
                    GameObject newSceneGameObject = null;
                    Color newColor;

                    // check for the Entity Type and spawn in the scene the appropriate Primitive
                    switch (entity.Type)
                    {
                        case "Cube":
                            // Create a Cube in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                            newColor = Color.blue;
                            break;

                        case "Sphere":
                            // Create a Sphere in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                            newColor = Color.red;
                            break;

                        case "Cylinder":
                            // Create a Cylinder in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                            newColor = Color.yellow;
                            break;
                        default:
                            newColor = Color.white;
                            break;
                    }

                    newSceneGameObject.name = entity.RowKey;

                    newSceneGameObject.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
                    {
                        color = newColor
                    };

                    //check for the Entity X,Y,Z and move the Primitive at those coordinates
                    newSceneGameObject.transform.position = new Vector3((float)entity.X, (float)entity.Y, (float)entity.Z);
                }

                // if the token is null, it means there are no more segments left to query
                token = queryResult.ContinuationToken;
            }

            while (token != null);
        }
    ```

9.  Außerhalb der **TableToScene-Klasse** müssen Sie die Klasse definieren, die von der Anwendung zum Serialisieren und Deserialisieren der Tabellenentitäten **verwendet wird.**

    ```csharp
        /// <summary>
        /// This objects is used to serialize and deserialize the Azure Table Entity
        /// </summary>
        [System.Serializable]
        public class AzureTableEntity : TableEntity
        {
            public AzureTableEntity(string partitionKey, string rowKey)
                : base(partitionKey, rowKey) { }

            public AzureTableEntity() { }
            public string Type { get; set; }
            public double X { get; set; }
            public double Y { get; set; }
            public double Z { get; set; }
        }
    ```

10. Stellen Sie sicher, **dass Sie speichern,** bevor Sie zum Unity-Editor zurückkommen.

11. Klicken Sie **im Bereich Hierarchie** auf die **Hauptkamera,** damit ihre Eigenschaften im **Inspektor angezeigt werden.**

12. Wenn der **Ordner Skripts** geöffnet ist, wählen Sie das Skript **TableToScene aus,** und ziehen Sie es auf **die Hauptkamera.** Das Ergebnis sollte wie folgt sein:

    ![Hinzufügen eines Skripts zur Hauptkamera](images/AzureLabs-Lab8-71.png)

## <a name="chapter-10---create-the-cloudscene-class-in-the-desktop-unity-project"></a>Kapitel 10: Erstellen der CloudScene-Klasse im Desktop Unity-Project

Das zweite Skript, das Sie erstellen müssen, ist **CloudScene,** das für Folgendes zuständig ist:

-   Registrieren des Linksklick-Ereignisses, damit der Benutzer Objekte um die Szene ziehen kann.

-   Serialisieren der Objektdaten aus dieser Unity-Szene und Senden an die Azure-Funktions-App.

So erstellen Sie das zweite Skript:

1.  Klicken Sie mit der rechten Maustaste in **den Ordner Skripts,** und klicken **Sie auf Erstellen**, C **\# Script**. Nennen Sie das **Skript CloudScene.**
    
    ![Neues C#-Skript: ](images/AzureLabs-Lab8-72.png)
     ![ Umbenennen von CloudScene](images/AzureLabs-Lab8-73.png)

2.  Fügen Sie die folgenden Namespaces hinzu:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using System.Threading.Tasks;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

3.  Fügen Sie die folgenden Variablen ein:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CloudScene instance;

        /// <summary>
        /// Insert here you Azure Function Url
        /// </summary>
        private string azureFunctionEndpoint = "--Insert here you Azure Function Endpoint--";

        /// <summary>
        /// Flag for object being moved
        /// </summary>
        private bool gameObjHasMoved;

        /// <summary>
        /// Transform of the object being dragged by the mouse
        /// </summary>
        private Transform gameObjHeld;

        /// <summary>
        /// Class hosted in the TableToScene script
        /// </summary>
        private AzureTableEntity azureTableEntity;
    ```

4.  Ersetzen Sie **den Wert azureFunctionEndpoint** durch Ihre Azure-Funktions-App-URL, die Sie im Azure-App Service im Azure-Portal finden, wie in der folgenden Abbildung dargestellt:

    ![Get-Funktions-URL](images/AzureLabs-Lab8-74.png)

5.  Fügen Sie nun die **Methoden Start() und** **Awake() hinzu,** um die -Klasse zu initialisieren.

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // initialise an AzureTableEntity
            azureTableEntity = new AzureTableEntity();
        }
    ```

6.  Fügen Sie **in der Update()-Methode** den folgenden Code hinzu, der die Mauseingabe erkennt und zieht, wodurch wiederum GameObjects in der Szene bewegt wird. Wenn der Benutzer ein Objekt gezogen und gelöscht hat, werden der Name und die Koordinaten des Objekts an die **Methode UpdateCloudScene()** übergeben, die den Azure-Funktions-App-Dienst aufruft, wodurch die Azure-Tabelle aktualisiert und die Benachrichtigung ausgelöst wird.

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            //Enable Drag if button is held down
            if (Input.GetMouseButton(0))
            {
                // Get the mouse position
                Vector3 mousePosition = new Vector3(Input.mousePosition.x, Input.mousePosition.y, 10);

                Vector3 objPos = Camera.main.ScreenToWorldPoint(mousePosition);

                Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);

                RaycastHit hit;

                // Raycast from the current mouse position to the object overlapped by the mouse
                if (Physics.Raycast(ray, out hit))
                {
                    // update the position of the object "hit" by the mouse
                    hit.transform.position = objPos;

                    gameObjHasMoved = true;

                    gameObjHeld = hit.transform;
                }
            }

            // check if the left button mouse is released while holding an object
            if (Input.GetMouseButtonUp(0) && gameObjHasMoved)
            {
                gameObjHasMoved = false;

                // Call the Azure Function that will update the appropriate Entity in the Azure Table
                // and send a Notification to all subscribed Apps
                Debug.Log("Calling Azure Function");

                StartCoroutine(UpdateCloudScene(gameObjHeld.name, gameObjHeld.position.x, gameObjHeld.position.y, gameObjHeld.position.z));
            }
        }
    ```

7.  Fügen Sie nun **die UpdateCloudScene()-Methode** wie folgt hinzu:

    ```csharp
        private IEnumerator UpdateCloudScene(string objName, double xPos, double yPos, double zPos)
        {
            WWWForm form = new WWWForm();

            // set the properties of the AzureTableEntity
            azureTableEntity.RowKey = objName;

            azureTableEntity.X = xPos;

            azureTableEntity.Y = yPos;

            azureTableEntity.Z = zPos;

            // Serialize the AzureTableEntity object to be sent to Azure
            string jsonObject = JsonConvert.SerializeObject(azureTableEntity);

            using (UnityWebRequest www = UnityWebRequest.Post(azureFunctionEndpoint, jsonObject))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(jsonObject);

                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.uploadHandler.contentType = "application/json";

                www.downloadHandler = new DownloadHandlerBuffer();

                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                string response = www.responseCode.ToString();
            }
        }
    ```

8.  Speichern Sie den Code, und kehren Sie zu Unity zurück.

9.  Ziehen Sie **das CloudScene-Skript** auf die **Hauptkamera.** 

    1. Klicken Sie **im Bereich Hierarchie** auf die **Hauptkamera,** damit ihre Eigenschaften im **Inspektor angezeigt werden.** 

    2. Wenn der **Ordner Skripts** geöffnet ist, wählen Sie das **Skript CloudScene** aus, und ziehen Sie es auf **die Hauptkamera.** Das Ergebnis sollte wie folgt sein:

        > ![Ziehen eines Cloudskripts auf die Hauptkamera](images/AzureLabs-Lab8-75.png)

## <a name="chapter-11---build-the-desktop-project-to-uwp"></a>Kapitel 11: Erstellen der Desktop-Project für UWP

Alles, was für den Unity-Abschnitt dieses Projekts erforderlich ist, wurde nun abgeschlossen.

1.  Navigieren Sie **zu Build Einstellungen** (**File**  >  **Build Einstellungen**).

2.  Klicken Sie **im Fenster Build Einstellungen** auf **Erstellen.**

    ![Buildprojekt](images/AzureLabs-Lab8-76.png)

3.  Ein **Fenster des Datei-Explorers** wird angezeigt, in dem Sie aufgefordert werden, einen Speicherort für den Build zu erstellen. Erstellen Sie einen neuen Ordner (indem Sie **oben** links auf Neuer Ordner klicken), und nennen Sie ihn **BUILDS**.

    ![Neuer Ordner für Build](images/AzureLabs-Lab8-77.png)

    1.  Öffnen Sie den neuen **Ordner BUILDS,** erstellen Sie einen weiteren Ordner (verwenden Sie erneut **Neuer** Ordner), und nennen Sie ihn **NH Desktop \_ \_ App**.

        ![Ordnername NH_Desktop_App](images/AzureLabs-Lab8-78.png)

    2.  Mit **ausgewählter NH \_ \_ Desktop-App.** Klicken Sie **auf Ordner auswählen.** Die Erstellung des Projekts nimmt eine Minute in Dauern.

4.  Nach dem Build **wird der Datei-Explorer** mit dem Speicherort Des neuen Projekts angezeigt. Sie müssen sie jedoch nicht öffnen, da Sie zuerst das andere Unity-Projekt in den nächsten Kapiteln erstellen müssen.


## <a name="chapter-12---set-up-mixed-reality-unity-project"></a>Kapitel 12: Einrichten Mixed Reality Unity-Project

Im Folgenden finden Sie eine typische Einrichtung für die Entwicklung mit Mixed Reality und daher eine gute Vorlage für andere Projekte.

1.  Öffnen Sie **Unity,** und klicken Sie **auf Neu.**

    ![Neues Unity-Projekt](images/AzureLabs-Lab8-79.png)

2.  Sie müssen nun einen Unity-Project angeben und **UnityMRNotifHub einfügen.** Stellen Sie sicher, dass der Projekttyp auf **3D festgelegt ist.** Legen Sie **den Speicherort** auf einen für Sie geeigneten Speicherort fest (denken Sie daran, dass die Nähe zu Stammverzeichnissen besser ist). Klicken Sie dann auf **Projekt erstellen.**

    ![Name UnityMRNotifHub](images/AzureLabs-Lab8-80.png)

3.  Wenn Unity geöffnet ist, sollten Sie überprüfen, ob der **Standardskript-Editor** auf **Visual Studio.** Wechseln Sie **zu**  >  **Einstellungen** bearbeiten, und navigieren Sie dann im neuen Fenster zu **Externe Tools.** Ändern **Sie den editor für externe** **Skripts in Visual Studio 2017**. Schließen Sie das **Fenster Einstellungen.**

    ![Festlegen des externen Editors auf VS](images/AzureLabs-Lab8-81.png)

4.  Wechseln Sie als Nächstes **zu Datei** Einstellungen, und wechseln Sie zur  >   Universelle **Windows-Plattform,** indem Sie auf die **Schaltfläche Plattform wechseln** klicken.

    ![Wechseln von Plattformen zu UWP](images/AzureLabs-Lab8-82.png)

5.  Wechseln Sie **zu**  >  **Datei Einstellungen,** und stellen Sie Sicher, dass:

    1.  **Zielgerät** ist auf **Beliebiges Gerät festgelegt.**

        > Legen Sie für Microsoft HoloLens **Zielgerät auf** *HoloLens.*

    2.  **Buildtyp** ist auf **D3D festgelegt**

    3.  **SDK** ist auf **Latest installed (Neueste installiert) festgelegt.**

    4.  **Visual Studio version** ist auf **Latest installed (Neueste installiert) festgelegt.**

    5.  **Erstellen und Ausführen** ist auf Lokaler **Computer festgelegt.**

    6.  Hier ist es sinnvoll, die Szene zu speichern und dem Build hinzufügen.

        1. Wählen Sie hierzu Geöffnete Szenen **hinzufügen aus.** Ein Speicherfenster wird angezeigt.

            ![Hinzufügen von offenen Szenen](images/AzureLabs-Lab8-83.png)

        2. Erstellen Sie einen neuen Ordner für diesen und jede  zukünftige Szene, und wählen Sie dann die Schaltfläche Neuer Ordner aus, um einen neuen Ordner zu erstellen, und nennen Sie **ihn Scenes**.

            ![Ordner "Neue Szenen"](images/AzureLabs-Lab8-84.png)

        3. Öffnen Sie den neu erstellten **Ordner Scenes,** und geben Sie dann im Textfeld **Dateiname:** **NH MR \_ \_ Scene** ein, und klicken Sie dann **auf Speichern.**

            ![neue Szene – NH_MR_Scene](images/AzureLabs-Lab8-85.png)

    7.  Die restlichen Einstellungen in **Build Einstellungen** sollten vorerde als Standardeinstellung be übrig bleiben.

6.  Klicken Sie im gleichen Fenster auf die **Schaltfläche Player Einstellungen,** um den entsprechenden Bereich in dem Bereich zu öffnen, in dem sich der **Inspektor** befindet.    

    ![Öffnen von Playereinstellungen](images/AzureLabs-Lab8-86.png)

7.  In diesem Bereich müssen einige Einstellungen überprüft werden:

    1.  Führen Sie **auf Einstellungen** Registerkarte Andere Optionen aus:

        1.  **Skriptlaufzeitversion muss** **experimentell sein** (.NET 4.6-Entsprechung)
        2.  **Das Skript-Back-End** sollte **_.NET sein._**
        3.  **Der API-Kompatibilitätsgrad** sollte **.NET 4.6 sein.**

            ![API-Kompatibilität](images/AzureLabs-Lab8-87.png)

    2.  Aktivieren Sie weiter unten im Bereich in **XR Einstellungen** (unter Publish **Einstellungen)** **(Virtual Reality** unterstützt), und stellen Sie sicher, dass das Windows Mixed Reality **SDK** hinzugefügt wird.

        ![Aktualisieren von xr-Einstellungen](images/AzureLabs-Lab8-88.png)        

    3.  Klicken Sie **auf Einstellungen** Registerkarte Publishing Einstellungen unter Capabilities ( **Funktionen**) auf :

        - **InternetClient**           

            ![Tick-Internetclient](images/AzureLabs-Lab8-89.png)

8.  Im **Build-Einstellungen** ist **Unity C#-Projekte** nicht mehr abgegraut: Aktivieren Sie das Kontrollkästchen daneben.

9.  Schließen Sie nach Abschluss dieser Änderungen das Fenster Build Einstellungen Erstellen.

10. Speichern Sie Ihre Szene, und Project **Datei**  >  **speichern Scene/File** Save  >  **Project.**

    > [!IMPORTANT]
    > Wenn Sie die *Unity Set up-Komponente* für dieses Projekt (Mixed Reality-App) überspringen und direkt mit dem Code fortfahren [](https://docs.unity3d.com/Manual/AssetPackages.html)möchten, können Sie dieses [UNITYPACKAGE](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage)herunterladen, als benutzerdefiniertes Paket in Ihr Projekt importieren und dann mit Kapitel [14 fortfahren.](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project) Sie müssen weiterhin die Skriptkomponenten hinzufügen.

### <a name="chapter-13---importing-the-dlls-in-the-mixed-reality-unity-project"></a>Kapitel 13: Importieren der DLLs im Mixed Reality Unity-Project

Sie verwenden die Azure Storage Unity-Bibliothek (die das .NET SDK für Azure verwendet). Folgen Sie diesem [Link zur Verwendung von Azure Storage mit Unity.](/sandbox/gamedev/unity/azure-storage-unity)
Derzeit gibt es ein bekanntes Problem in Unity, bei dem Plug-Ins nach dem Import neu konfiguriert werden müssen. Diese Schritte (4 bis 7 in diesem Abschnitt) sind nicht mehr erforderlich, nachdem der Fehler behoben wurde.

Um das SDK in Ihr eigenes Projekt zu importieren, stellen Sie sicher, dass Sie das neueste [.unitypackage heruntergeladen haben.](https://aka.ms/azstorage-unitysdk) Gehen Sie nun wie folgt vor:

1.  Fügen Sie unitypackage, das Sie oben heruntergeladen haben, mithilfe der Menüoption **Assets** Import Package Custom Package (Benutzerdefiniertes Paket importieren) zu Unity  >    >   hinzu.

2.  Im **angezeigten Feld Unity-Paket** importieren können Sie alles unter **Plug-In**  >  Storage.

    ![Importpaket](images/AzureLabs-Lab8-90.png)

3.  Klicken Sie auf **die Schaltfläche** Importieren, um dem Projekt die Elemente hinzuzufügen.

4.  Wechseln Sie in **der Storage** unter **Plug-Ins** zum Ordner Project, und wählen Sie nur die folgenden Plug-Ins *aus:*

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

    ![Auswählen von Plug-Ins](images/AzureLabs-Lab8-91.png)

5.  Wenn *diese spezifischen Plug-Ins* ausgewählt sind, deaktivieren **Sie** **Alle Plattformen,** und deaktivieren  **Sie WSAPlayer,** und klicken Sie dann **auf Anwenden.**

    ![Anwenden von Plattformänderungen](images/AzureLabs-Lab8-92.png)

    > [!NOTE] 
    > Sie markieren diese bestimmten Plug-Ins so, dass sie nur im Unity-Editor verwendet werden. Dies liegt daran, dass es verschiedene Versionen der gleichen Plug-Ins im WSA-Ordner gibt, die verwendet werden, nachdem das Projekt aus Unity exportiert wurde.

6.  Wählen Sie **Storage** Plug-In-Ordner nur Aus:

    -   Microsoft.Data.Services.Client

        ![Auswählen des Datendienstclients](images/AzureLabs-Lab8-93.png)

7.  Aktivieren Sie **das Kontrollkästchen Nicht verarbeiten unter** **Plattform Einstellungen** und klicken Sie **auf Übernehmen.**

    ![nicht verarbeiten](images/AzureLabs-Lab8-94.png)

    > [!NOTE] 
    > Sie markieren dieses Plug-In als "Nicht verarbeiten", da der Unity-Assemblypatcher Schwierigkeiten bei der Verarbeitung dieses Plug-Ins hat. Das Plug-In funktioniert auch dann, wenn es nicht verarbeitet wird.

## <a name="chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project"></a>Kapitel 14: Erstellen der TableToScene-Klasse im Mixed Reality-Unity-Projekt

Die **TableToScene-Klasse** ist identisch mit der in Kapitel [9 erläuterten.](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project) Erstellen Sie dieselbe Klasse in der Mixed Reality-Unity Project wie in Kapitel [9 erläutert.](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)

Nachdem Sie dieses Kapitel abgeschlossen haben, wird diese Klasse für beide **Unity-Projekte** auf der Hauptkamera eingerichtet.

## <a name="chapter-15---creating-the-notificationreceiver-class-in-the-mixed-reality-unity-project"></a>Kapitel 15: Erstellen der NotificationReceiver-Klasse im Mixed Reality Unity-Project

Das zweite Skript, das Sie erstellen müssen, ist **NotificationReceiver,** das für Folgendes zuständig ist:

-   Registrieren der App beim Notification Hub bei der Initialisierung.
-   Lauschen auf Benachrichtigungen vom Notification Hub.
-   Deserialisieren der Objektdaten aus empfangenen Benachrichtigungen.
-   Verschieben Sie die GameObjects in der Szene basierend auf den deserialisierten Daten.

So erstellen Sie **das NotificationReceiver-Skript:**

1.  Klicken Sie mit der rechten Maustaste in **den Ordner Skripts,** und klicken **Sie auf Erstellen**, C **\# Script**. Nennen Sie das **Skript NotificationReceiver**.

    ![Create new c# script ](images/AzureLabs-Lab8-95.png)
     ![ name it NotificationReceiver (Neues C#-Skript erstellen)](images/AzureLabs-Lab8-96.png)

2.  Doppelklicken Sie auf das Skript, um es zu öffnen.

3.  Fügen Sie die folgenden Namespaces hinzu:

    ```csharp
    //using Microsoft.WindowsAzure.Messaging;
    using Newtonsoft.Json;
    using System;
    using System.Collections;
    using UnityEngine;

    #if UNITY_WSA_10_0 && !UNITY_EDITOR
    using Windows.Networking.PushNotifications;
    #endif
    ```

4.  Fügen Sie die folgenden Variablen ein:

    ```csharp
        /// <summary>
        /// allows this class to behave like a singleton
        /// </summary>
        public static NotificationReceiver instance;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        Vector3 newObjPosition;

        /// <summary>
        /// Value set by the notification, object name
        /// </summary>
        string gameObjectName;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        bool notifReceived;

        /// <summary>
        /// Insert here your Notification Hub Service name 
        /// </summary>
        private string hubName = " -- Insert the name of your service -- ";

        /// <summary>
        /// Insert here your Notification Hub Service "Listen endpoint"
        /// </summary>
        private string hubListenEndpoint = "-Insert your Notification Hub Service Listen endpoint-";
    ```

5.  Ersetzen Sie **den Wert hubName** durch den Namen Ihres Notification Hub-Diensts und den **Wert hubListenEndpoint** durch den Endpunktwert auf der Registerkarte Zugriffsrichtlinien , Azure Notification Hub-Dienst, im Azure-Portal (siehe Abbildung unten).

    ![Einfügen eines Notification Hubs-Richtlinienendpunkts](images/AzureLabs-Lab8-97.png)

6.  Fügen Sie nun die **Methoden Start() und** **Awake() hinzu,** um die -Klasse zu initialisieren.

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Register the App at launch
            InitNotificationsAsync();

            // Begin listening for notifications
            StartCoroutine(WaitForNotification());
        }
    ```

7.  Fügen Sie die **WaitForNotification-Methode** hinzu, damit die App Benachrichtigungen von der Notification Hub-Bibliothek empfangen kann, ohne dass ein Konflikt mit dem Hauptthread besteht:

    ```csharp
        /// <summary>
        /// This notification listener is necessary to avoid clashes 
        /// between the notification hub and the main thread   
        /// </summary>
        private IEnumerator WaitForNotification()
        {
            while (true)
            {
                // Checks for notifications each second
                yield return new WaitForSeconds(1f);

                if (notifReceived)
                {
                    // If a notification is arrived, moved the appropriate object to the new position
                    GameObject.Find(gameObjectName).transform.position = newObjPosition;

                    // Reset the flag
                    notifReceived = false;
                }
            }
        }
    ```

8.  Die folgende Methode, **InitNotificationAsync()**, registriert die Anwendung bei der Initialisierung beim Notification Hub-Dienst. Der Code ist auskommentiert, da Unity das Projekt nicht erstellen kann. Sie entfernen die Kommentare, wenn Sie das Azure Messaging NuGet-Paket in Visual Studio.

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            // PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            // NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            // Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            // if (result.RegistrationId != null)
            // {
            //     Debug.Log($"Registration Successful: {result.RegistrationId}");
            //     channel.PushNotificationReceived += Channel_PushNotificationReceived;
            // }
        }
    ```

9.  Der folgende Handler, **Channel \_ PushNotificationReceived()**, wird jedes Mal ausgelöst, wenn eine Benachrichtigung empfangen wird. Die Benachrichtigung wird deserialisiert. Dabei handelt es sich um die Azure-Tabellenentität, die in der Desktopanwendung verschoben wurde, und anschließend wird das entsprechende GameObject in der MR-Szene an die gleiche Position verschoben. 
    
    > [!IMPORTANT]
    > Der Code wird auskommentiert, da der Code auf die Azure Messaging-Bibliothek verweist, die Sie nach dem Erstellen des Unity-Projekts mithilfe der NuGet-Paket-Manager in Visual Studio. Daher kann das Unity-Projekt nur dann erstellen, wenn es auskommentiert ist. Beachten Sie, dass Sie diesen Code erneut kommentieren müssen, wenn Sie Ihr Projekt erstellen und dann zu Unity **zurückkehren** möchten.

    ```csharp
        ///// <summary>
        ///// Handler called when a Push Notification is received
        ///// </summary>
        //private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)    
        //{
        //    Debug.Log("New Push Notification Received");
        //
        //    if (args.NotificationType == PushNotificationType.Raw)
        //    {
        //        //  Raw content of the Notification
        //        string jsonContent = args.RawNotification.Content;
        //
        //        // Deserialise the Raw content into an AzureTableEntity object
        //        AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);
        //
        //        // The name of the Game Object to be moved
        //        gameObjectName = ate.RowKey;          
        //
        //        // The position where the Game Object has to be moved
        //        newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);
        //
        //        // Flag thats a notification has been received
        //        notifReceived = true;
        //    }
        //}
    ```

10. Denken Sie daran, Ihre Änderungen zu speichern, bevor Sie zum Unity-Editor zurückwechseln.

11. Klicken Sie **im Bereich Hierarchie** auf die **Hauptkamera,** damit ihre Eigenschaften im **Inspektor angezeigt werden.**

12. Wenn der **Ordner Skripts** geöffnet ist, wählen Sie das **Skript NotificationReceiver** aus, und ziehen Sie es auf die **Hauptkamera.** Das Ergebnis sollte wie folgt sein:

    ![Benachrichtigungsempfängerskript auf Kamera ziehen](images/AzureLabs-Lab8-98.png)

    > [!NOTE]
    > Wenn Sie dies für die Microsoft HoloLens entwickeln, müssen Sie die  Kamerakomponente der Hauptkamera aktualisieren, sodass:
    > - Flags löschen: Volltonfarbe
    > - Hintergrund: Schwarz

## <a name="chapter-16---build-the-mixed-reality-project-to-uwp"></a>Kapitel 16: Erstellen der Mixed Reality Project für UWP

Dieses Kapitel ist identisch mit dem Buildprozess für das vorherige Projekt. Alles, was für den Unity-Abschnitt dieses Projekts erforderlich ist, wurde abgeschlossen, daher ist es an der Zeit, es aus Unity zu erstellen.

1.  Navigieren Sie **zu Build Einstellungen** ( **File**  >  **Build Einstellungen** ).

2.  Vergewissern **Sie sich** Einstellungen Menü Build Einstellungen, dass Unity C# Projects * **(Unity C#-Projekte*** ) markiert ist (damit Sie die Skripts in diesem Projekt nach dem Build bearbeiten können).

3.  Klicken Sie anschließend auf **Erstellen.**

    ![Buildprojekt](images/AzureLabs-Lab8-99.png)

4.  Ein **Fenster des Datei-Explorers** wird angezeigt, in dem Sie aufgefordert werden, einen Speicherort für den Build zu erstellen. Erstellen Sie einen neuen Ordner (indem Sie **oben** links auf Neuer Ordner klicken), und nennen Sie ihn **BUILDS**.

    ![Ordner "Builds erstellen"](images/AzureLabs-Lab8-100.png)

    1.  Öffnen Sie den neuen **Ordner BUILDS,** erstellen Sie einen weiteren Ordner (verwenden Sie erneut **Neuer** Ordner), und nennen Sie ihn **NH MR \_ \_ App**.

        ![Erstellen NH_MR_Apps Ordners](images/AzureLabs-Lab8-101.png)

    2.  Mit **ausgewählter NH \_ \_ MR-App.** Klicken Sie **auf Ordner auswählen.** Die Erstellung des Projekts nimmt eine Minute in Dauern.

5.  Nach dem Build wird ein **Datei-Explorer-Fenster** am Speicherort Des neuen Projekts geöffnet.



## <a name="chapter-17---add-nuget-packages-to-the-unitymrnotifhub-solution"></a>Kapitel 17: Hinzufügen NuGet Paketen zur UnityMRNotifHub-Lösung

> [!WARNING] 
> Denken Sie daran, dass nach dem Hinzufügen der folgenden NuGet-Pakete (und dem Auskommentieren des Codes im nächsten Kapitel) der Code, wenn er innerhalb der Unity-Project erneut geöffnet wird, Fehler enthält. [](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class) Wenn Sie die Bearbeitung im Unity-Editor fortsetzen möchten, müssen Sie diesen errosomen Code kommentieren und die Auskommentierung später erneut Visual Studio. 

Navigieren Sie nach Abschluss des Mixed Reality-Build zu dem Mixed Reality-Projekt, das Sie erstellt haben, und doppelklicken Sie auf die Projektmappendatei (SLN) in diesem Ordner, um Ihre Projektmappe mit Visual Studio 2017 zu öffnen.
Sie müssen nun das Paket **WindowsAzure.Messaging.managed** NuGet hinzufügen. dies ist eine Bibliothek, die zum Empfangen von Benachrichtigungen vom Notification Hub verwendet wird.

So importieren Sie NuGet Paket:

1.  Klicken Sie **im Projektmappen-Explorer** mit der rechten Maustaste auf Ihre Projektmappe.

2.  Klicken Sie **auf Manage NuGet Packages (Pakete verwalten).**

    ![Öffnen des NuGet-Managers](images/AzureLabs-Lab8-102.png)

3.  Wählen Sie die Registerkarte ***Durchsuchen** _ aus, und suchen Sie nach _*WindowsAzure.Messaging.managed**.

    ![Suchen des Windows Azure-Messagingpakets](images/AzureLabs-Lab8-103.png)

4.  Wählen Sie das Ergebnis aus (wie unten dargestellt), und aktivieren Sie im Fenster auf der rechten Seite das Kontrollkästchen **neben Project.** Dadurch wird im Kontrollkästchen neben **Project** ein Häkchen neben dem Kontrollkästchen neben dem **Projekt Assembly-CSharp** und **UnityMRNotifHub** angezeigt.

    ![Alle Projekte markieren](images/AzureLabs-Lab8-104.png)

5.  Die ursprünglich bereitgestellte **Version ist möglicherweise** nicht mit diesem Projekt kompatibel. Klicken Sie daher auf das Dropdownmenü neben **Version**, und klicken Sie auf **Version 0.1.7.9** und dann **auf Installieren.**

6.  Sie haben die Installation des Pakets NuGet abgeschlossen. Suchen Sie den kommentierten Code, den Sie in der **NotificationReceiver-Klasse eingegeben haben,** und entfernen Sie die Kommentare.



## <a name="chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class"></a>Kapitel 18: Bearbeiten der UnityMRNotifHub-Anwendung, NotificationReceiver-Klasse

Nachdem Sie die NuGet **Packages hinzugefügt** haben,  müssen Sie die Auskommentierung für einen Teil des Codes innerhalb der **NotificationReceiver-Klasse** auskommentieren.

Dies schließt Folgendes ein:

1. Der Namespace oben:

    ```csharp
    using Microsoft.WindowsAzure.Messaging;
    ```

2. Der ganze Code in der **InitNotificationsAsync()-Methode:**

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            if (result.RegistrationId != null)
            {
                Debug.Log($"Registration Successful: {result.RegistrationId}");
                channel.PushNotificationReceived += Channel_PushNotificationReceived;
            }
        }
    ```

> [!WARNING]
> Der obige Code enthält einen Kommentar: Stellen Sie  sicher, dass Sie die Auskommentierung dieses Kommentars nicht versehentlich auskommentiert haben (da der Code nicht kompiliert wird, wenn Sie haben!).

3. Und schließlich das **Channel_PushNotificationReceived** Ereignis:

    ```csharp
        /// <summary>
        /// Handler called when a Push Notification is received
        /// </summary>
        private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)
        {
            Debug.Log("New Push Notification Received");

            if (args.NotificationType == PushNotificationType.Raw)
            {
                //  Raw content of the Notification
                string jsonContent = args.RawNotification.Content;

                // Deserialize the Raw content into an AzureTableEntity object
                AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);

                // The name of the Game Object to be moved
                gameObjectName = ate.RowKey;

                // The position where the Game Object has to be moved
                newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);

                // Flag thats a notification has been received
                notifReceived = true;
            }
        }
    ```

Stellen Sie bei auskommentierten Auskommentierung sicher, dass Sie speichern, und fahren Sie dann mit dem nächsten Kapitel fort.

## <a name="chapter-19---associate-the-mixed-reality-project-to-the-store-app"></a>Kapitel 19: Zuordnen des Mixed Reality-Projekts zur Store App

Nun müssen Sie das **Mixed Reality-Projekt** der Store-App zuordnen, die Sie zu Beginn des Labs erstellt haben.

1.  Öffnen Sie die Projektmappe.

2.  Klicken Sie im Projektmappen-Explorer-Bereich mit der rechten Maustaste auf die UWP Project-App, wechseln Sie zu **Store**, und ordnen Sie die App dem **Store... .**

    ![Open Store-Zuordnung](images/AzureLabs-Lab8-105.png)

3.  Ein neues Fenster mit dem Namen **Ordnen Sie Ihre App dem Windows Store.** Klicken Sie auf **Weiter**.

    ![Zum nächsten Bildschirm wechseln](images/AzureLabs-Lab8-106.png)

4.  Alle Anwendungen, die dem angemeldeten Konto zugeordnet sind, werden geladen. Wenn Sie nicht bei Ihrem Konto angemeldet sind, können Sie **sich auf** dieser Seite anmelden.

5.  Suchen Sie **Store App-Namen,** den Sie zu Beginn dieses Tutorials erstellt haben, und wählen Sie ihn aus. Klicken Sie dann auf **Weiter**.

    ![Suchen und Auswählen des Geschäftsnamens](images/AzureLabs-Lab8-107.png)

6.  Klicken Sie **auf Zuordnen.**

    ![Zuordnen der App](images/AzureLabs-Lab8-108.png)

7.  Ihre App ist jetzt **der app-Store** zugeordnet. Dies ist erforderlich, um Benachrichtigungen zu aktivieren.

## <a name="chapter-20---deploy-unitymrnotifhub-and-unitydesktopnotifhub-applications"></a>Kapitel 20: Bereitstellen von UnityMRNotifHub- und UnityDesktopNotifHub-Anwendungen

Dieses Kapitel ist möglicherweise einfacher mit zwei Personen, da das Ergebnis sowohl ausgeführte Apps umfasst, eine auf Ihrem Computer Desktop und die andere in Ihrem immersiven Headset.

Die Immersive Headset-App wartet darauf, Änderungen an der Szene zu empfangen (Positionsänderungen der lokalen GameObjects), und die Desktop-App ändert ihre lokale Szene (Positionsänderungen), die für die MR-App freigegeben werden. Es ist sinnvoll, zuerst die MR-App und dann die Desktop-App bereitzustellen, damit der Empfänger mit dem Lauschen beginnen kann.

So stellen Sie die **UnityMRNotifHub-App** auf Ihrem lokalen Computer zur Verfügung:

1.  Öffnen Sie die Projektmappendatei Ihrer **UnityMRNotifHub-App** in **Visual Studio 2017**.

2.  Wählen Sie **auf der Projektmappenplattform** **x86, Lokaler Computer aus.**

3.  Wählen Sie in **der Projektmappenkonfiguration** **Debuggen aus.**

    ![Festlegen der Projektkonfiguration](images/AzureLabs-Lab8-109.png)

4.  Wechseln Sie zum **Menü Erstellen,** und klicken Sie **auf Projektmappe bereitstellen,** um die Anwendung auf Ihren Computer zu laden.

5.  Ihre App sollte nun in der Liste der installierten Apps angezeigt werden, die zum Start bereit sind.

So stellen Sie die **UnityDesktopNotifHub-App** auf dem lokalen Computer zur Verfügung:

1.  Öffnen Sie die Projektmappendatei Ihrer **UnityDesktopNotifHub-App** in **Visual Studio 2017**.

2.  Wählen Sie **auf der Projektmappenplattform** **x86, Lokaler Computer aus.**

3.  Wählen Sie in **der Projektmappenkonfiguration** **Debuggen aus.**

    ![Festlegen der Projektkonfiguration](images/AzureLabs-Lab8-110.png)

4.  Wechseln Sie zum **Menü Erstellen,** und klicken Sie **auf Projektmappe bereitstellen,** um die Anwendung auf Ihren Computer zu laden.

5.  Ihre App sollte nun in der Liste der installierten Apps angezeigt werden, die zum Start bereit sind.

6.  Starten Sie die Mixed Reality-Anwendung, gefolgt von der Desktopanwendung.

Wenn beide Anwendungen ausgeführt werden, verschieben Sie ein Objekt in der Desktopszene (mit der linken Maustaste). Diese Positionsänderungen werden lokal vorgenommen, serialisiert und an den Funktions-App-Dienst gesendet. Der Funktions-App-Dienst aktualisiert dann die Tabelle zusammen mit dem Notification Hub. Nachdem der Notification Hub ein Update erhalten hat, sendet er die aktualisierten Daten direkt an alle registrierten Anwendungen (in diesem Fall die Immersive Headset-App), die dann die eingehenden Daten deserialisieren und die neuen Positionsdaten auf die lokalen Objekte anwenden und sie in die Szene verschieben.


## <a name="your-finished-your-azure-notification-hubs-application"></a>Ihre fertige Azure Notification Hubs Anwendung
 
Herzlichen Glückwunsch! Sie haben eine Mixed Reality-App erstellt, die den Azure Notification Hubs Service nutzt und die Kommunikation zwischen Apps ermöglicht.
 
![Final Product -end](images/AzureLabs-Lab8-00.png)
 
## <a name="bonus-exercises"></a>Zusatzübungen

### <a name="exercise-1"></a>Übung 1

Können Sie herausarbeiten, wie Sie die Farbe der GameObjects ändern und diese Benachrichtigung an andere Apps senden, die die Szene anzeigen?

### <a name="exercise-2"></a>Übung 2

Können Sie Ihrer MR-App Bewegungen der GameObjects hinzufügen und die aktualisierte Szene in Ihrer Desktop-App sehen?