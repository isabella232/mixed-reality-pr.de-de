---
title: 'HoloLens (1. Generation) und Azure 303 : Verstehen natürlicher Sprache (LUIS)'
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie Azure Language Understanding Intelligence Service (LUIS) in einer Mixed Reality-Anwendung implementieren.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, Tutorial, API, Language Understanding Intelligence Service, Luis, HoloLens, immersive, vr, Windows 10, Visual Studio
ms.openlocfilehash: 443b5f2c186fbbb0a3e979b48ccc20b4c3d3b4f0bd9c93950e27e1f86d610c07
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115218083"
---
# <a name="hololens-1st-gen-and-azure-303-natural-language-understanding-luis"></a>HoloLens (1. Generation) und Azure 303: Verstehen natürlicher Sprache (LUIS)

<br>

>[!NOTE]
>Die Tutorials der Mixed Reality Academy wurden im Hinblick auf HoloLens (1. Gen.) und immersive Mixed Reality-Headsets entworfen.  Daher halten wir es für wichtig, diese Tutorials für Entwickler verfügbar zu halten, die noch nach Anleitung beim Entwickeln für diese Geräte suchen.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für HoloLens 2 verwendet werden.  Sie werden gewartet, um weiterhin auf den unterstützten Geräten zu funktionieren. Es wird eine neue Reihe von Tutorials geben, die in Zukunft veröffentlicht werden, die veranschaulichen, wie sie für HoloLens 2 entwickelt werden.  Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn sie veröffentlicht werden.

<br>

In diesem Kurs erfahren Sie, wie Sie Language Understanding mithilfe von Azure Cognitive Services mit der Language Understanding-API in eine Mixed Reality-Anwendung integrieren.

![Labergebnis](images/AzureLabs-Lab3-000.png)

*Language Understanding (LUIS)* ist ein Microsoft Azure-Dienst, der Anwendungen die Möglichkeit bietet, aus Benutzereingaben eine Bedeutung zu machen, z. B. durch Extrahieren des gewünschten Ziels einer Person in eigenen Worten. Dies wird durch maschinelles Lernen erreicht, das die Eingabeinformationen versteht und lernt und dann mit detaillierten, relevanten Informationen antworten kann. Weitere Informationen finden Sie auf der [Seite azure Language Understanding (LUIS).](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/)

Nach Abschluss dieses Kurses verfügen Sie über eine Immersive Headset-Mixed Reality-Anwendung, die folgende Schritte ausführen kann:

1.  Erfassen Sie die Benutzereingabesprache mithilfe des Mikrofons, das an das immersive Headset angefügt ist. 
2.  Senden Sie das erfasste Diktat an *azure Language Understanding Intelligent Service* (*LUIS*). 
3.  Lassen Sie LUIS die Bedeutung aus den Sendeinformationen extrahieren, die analysiert werden, und versuchen Sie, die Absicht der Anforderung des Benutzers zu bestimmen.

Die Entwicklung umfasst die Erstellung einer App, bei der der Benutzer die Größe und Farbe der Objekte in der Szene mithilfe von Sprache und/oder Anvieren ändern kann. Die Verwendung von Motion-Controllern wird nicht abgedeckt.

In Ihrer Anwendung liegt es an Ihnen, wie Sie die Ergebnisse in Ihren Entwurf integrieren. In diesem Kurs erfahren Sie, wie Sie einen Azure-Dienst in Ihre Unity-Project integrieren. Es ist Ihre Aufgabe, das Wissen, das Sie aus diesem Kurs gewinnen, zu nutzen, um Ihre Mixed Reality-Anwendung zu verbessern.

Bereiten Sie sich darauf vor, LUIS mehrmals zu trainieren. Dies wird in [Kapitel 12](#chapter-12--improving-your-luis-service)behandelt. Je häufiger LUIS trainiert wurde, desto bessere Ergebnisse erhalten Sie.

## <a name="device-support"></a>Geräteunterstützung

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td>MR und Azure 303: Verstehen natürlicher Sprache (LUIS)</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Während sich dieser Kurs hauptsächlich auf Windows Mixed Reality immersiven Headsets (VR) konzentriert, können Sie auch das, was Sie in diesem Kurs lernen, auf Microsoft HoloLens anwenden. Während Sie den Kurs durchgehen, werden Ihnen Hinweise zu allen Änderungen angezeigt, die Sie ggf. zur Unterstützung HoloLens verwenden müssen. Wenn Sie HoloLens verwenden, können Sie während der Spracherfassung ein Echo bemerken.

## <a name="prerequisites"></a>Voraussetzungen

> [!NOTE]
> Dieses Tutorial richtet sich an Entwickler, die grundlegende Erfahrung mit Unity und C# haben. Beachten Sie auch, dass die Voraussetzungen und die geschriebenen Anweisungen in diesem Dokument darstellen, was zum Zeitpunkt der Erstellung (Mai 2018) getestet und überprüft wurde. Sie können die neueste Software verwenden, wie im Artikel [installieren der Tools](../../install-the-tools.md) aufgeführt. Es sollte jedoch nicht davon ausgegangen werden, dass die Informationen in diesem Kurs perfekt mit dem übereinstimmen, was Sie in neuerer Software finden als die unten aufgeführten.

Für diesen Kurs wird die folgende Hardware und Software empfohlen:

- Ein Entwicklungs-PC, [der mit Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) für die Entwicklung immersiver Headsets (VR) kompatibel ist
- [Windows 10 Fall Creators Update (oder höher) mit aktivierter Option "Entwicklermodus"](../../install-the-tools.md)
- [Das neueste Windows 10 SDK](../../install-the-tools.md)
- [Unity 2017.4](../../install-the-tools.md)
- [Visual Studio 2017](../../install-the-tools.md)
- Ein [Windows Mixed Reality immersives Headset (VR)](../../../discover/immersive-headset-hardware-details.md) oder [ein Microsoft HoloLens](/hololens/hololens1-hardware) mit aktiviertem Entwicklermodus
- Eine Reihe von Mikrofonen mit einem integrierten Mikrofon (wenn das Headset nicht über ein integriertes Mikrofon und Lautsprecher verfügt)
- Internetzugriff für Azure-Setup und LUIS-Abruf

## <a name="before-you-start"></a>Vorbereitung

1.  Um Probleme bei der Erstellung dieses Projekts zu vermeiden, wird dringend empfohlen, das in diesem Tutorial erwähnte Projekt in einem Stammordner oder in einem Ordner in der Nähe des Stammordners zu erstellen (lange Ordnerpfade können zur Buildzeit Probleme verursachen). 
2.  Damit Ihr Computer das Diktieren aktivieren kann, wechseln Sie zu **Windows Einstellungen > Datenschutz > Speech, Inking & Eingabe,** und drücken Sie die Schaltfläche **Sprachdienste aktivieren und Vorschläge eingeben.**
3.  Mit dem Code in diesem Tutorial können Sie auf Ihrem Computer über das **Standard-Mikrofongerät** aufzeichnen. Stellen Sie sicher, dass das Standard-Mikrofongerät als das Gerät festgelegt ist, das Sie zum Erfassen Ihrer Stimme verwenden möchten.
4.  Wenn Ihr Headset über ein integriertes Mikrofon verfügt, stellen Sie sicher, dass die Option *"When I wear my headset, switch to headset mic" (Wenn ich mein Headset verschleiße, zum Headset-Mikrofon wechseln)* in den *einstellungen der Mixed Reality-Portal* aktiviert ist.

    ![Einrichten des immersiven Headsets](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a>Kapitel 1: Einrichten des Azure-Portals

Um den *Language Understanding-Dienst* in Azure zu verwenden, müssen Sie eine Instanz des Diensts konfigurieren, die Ihrer Anwendung zur Verfügung gestellt wird.

1.  Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

    > [!NOTE]
    > Wenn Sie noch nicht über ein Azure-Konto verfügen, müssen Sie eins erstellen. Wenn Sie dieses Tutorial in einer Classroom- oder Lab-Situation durchgehen, bitten Sie Ihren Dozenten oder einen der Proctors um Hilfe beim Einrichten Ihres neuen Kontos.

2.  Klicken Sie nach der Anmeldung oben links auf **Neu,** suchen Sie *nach Language Understanding*, und drücken Sie **die EINGABETASTE.** 

    ![Erstellen einer LUIS-Ressource](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > Das Wort **Neu** wurde möglicherweise in neueren Portalen durch **Ressource erstellen** ersetzt.
 
3.  Die neue Seite auf der rechten Seite enthält eine Beschreibung des Language Understanding-Diensts. Wählen Sie unten links auf dieser Seite die Schaltfläche **Erstellen** aus, um eine Instanz dieses Diensts zu erstellen.

    ![Erstellung des LUIS-Diensts – rechtliche Hinweise](images/AzureLabs-Lab3-02.png)
 
4.  Nachdem Sie auf Erstellen geklickt haben:

    1. Fügen Sie den gewünschten **Namen** für diese Dienstinstanz ein.
    2. Wählen Sie ein **Abonnement** aus.
    3. Wählen Sie den für Sie geeigneten **Tarif** aus. Wenn Sie zum ersten Mal einen *LUIS-Dienst* erstellen, sollte Ihnen ein Free-Tarif (mit dem Namen F0) zur Verfügung stehen. Die kostenlose Zuordnung sollte für diesen Kurs mehr als ausreichend sein.
    4. Wählen Sie eine **Ressourcengruppe** aus, oder erstellen Sie eine neue. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, Steuern des Zugriffs, Bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt zugeordnet sind (z. B. diese Kurse), in einer gemeinsamen Ressourcengruppe zu speichern. 

        > Weitere Informationen zu Azure-Ressourcengruppen finden Sie [im Artikel zu Ressourcengruppen.](/azure/azure-resource-manager/resource-group-portal)

    5. Bestimmen Sie den **Speicherort** für Ihre Ressourcengruppe (wenn Sie eine neue Ressourcengruppe erstellen). Der Standort befindet sich idealerweise in der Region, in der die Anwendung ausgeführt wird. Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.
    6. Sie müssen auch bestätigen, dass Sie die für diesen Dienst geltenden Geschäftsbedingungen verstanden haben.
    7. Klicken Sie auf **Erstellen**.

        ![Erstellen eines LUIS-Diensts – Benutzereingabe](images/AzureLabs-Lab3-03.png)
 
5.  Nachdem Sie auf **Erstellen** geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. Dies kann eine Minute dauern.
6.  Sobald die Dienstinstanz erstellt wurde, wird eine Benachrichtigung im Portal angezeigt. 
 
    ![Neues Azure-Benachrichtigungsimage](images/AzureLabs-Lab3-04.png)

7.  Klicken Sie auf die Benachrichtigung, um Ihre neue Dienstinstanz zu untersuchen.

    ![Benachrichtigung zur erfolgreichen Ressourcenerstellung](images/AzureLabs-Lab3-05.png)
 
8.  Klicken Sie in der Benachrichtigung auf die Schaltfläche **Zu Ressource** wechseln, um Ihre neue Dienstinstanz zu untersuchen. Sie gelangen zu Ihrer neuen LUIS-Dienstinstanz. 
 
    ![Zugreifen auf LUIS-Schlüssel](images/AzureLabs-Lab3-06.png)

9.  In diesem Tutorial muss Ihre Anwendung Aufrufe an Ihren Dienst tätigen. Dies erfolgt über den Abonnementschlüssel Ihres Diensts.
10. Navigieren Sie auf der *Schnellstartseite* Ihres *LUIS-API-Diensts* zum ersten Schritt, Greifen Sie *Ihre Schlüssel,* und klicken Sie auf **Schlüssel** ( Sie können dies auch erreichen, indem Sie auf den blauen Link Schlüssel klicken, der sich im Navigationsmenü der Dienste befindet, das durch das Schlüsselsymbol gekennzeichnet ist). Dadurch werden Ihre *Dienstschlüssel angezeigt.*
11. Erstellen Sie eine Kopie eines der angezeigten Schlüssel, da Sie diese später in Ihrem Projekt benötigen. 
12. Klicken Sie auf der Seite *Dienst* auf *Language Understanding Portal,* um auf die Webseite umgeleitet zu werden, die Sie zum Erstellen Ihres neuen Diensts in der LUIS-App verwenden. 

## <a name="chapter-2--the-language-understanding-portal"></a>Kapitel 2 : Das Language Understanding-Portal

In diesem Abschnitt erfahren Sie, wie Sie eine LUIS-App im LUIS-Portal erstellen. 

> [!IMPORTANT]
> Beachten Sie, dass das Einrichten der *Entitäten,* Absichten und *Äußerungen* in diesem Kapitel nur der erste Schritt beim Erstellen Ihres LUIS-Diensts ist: Sie müssen den Dienst auch *mehrmals* neu trainieren, um ihn genauer zu machen. Das erneute Training Ihres Diensts wird im [letzten Kapitel](#chapter-12--improving-your-luis-service) dieses Kurses behandelt. Stellen Sie daher sicher, dass Sie ihn abschließen.

1.  Wenn Sie das *Language Understanding-Portal* erreichen, müssen Sie sich möglicherweise mit den gleichen Anmeldeinformationen wie bei Ihrem Azure-Portal anmelden, sofern sie noch nicht vorhanden sind. 

    ![LUIS-Anmeldeseite](images/AzureLabs-Lab3-07.png)
 
2.  Wenn Sie LUIS zum ersten Mal verwenden, müssen Sie zum unteren Rand der Willkommensseite scrollen, um die Schaltfläche LUIS-App erstellen zu suchen **und zu** klicken.

    ![Seite "LUIS-App erstellen"](images/AzureLabs-Lab3-08.png)
 
3.  Klicken Sie nach der Anmeldung **auf Meine Apps** (wenn Sie sich derzeit nicht in diesem Abschnitt befinden). Sie können dann auf Create **new app (Neue App erstellen) klicken.**

    ![LUIS – Image "Meine Apps"](images/AzureLabs-Lab3-09.png)
 
4.  Geben Sie Ihrer App einen *Namen.*
5.  Wenn Ihre App eine andere Sprache als Englisch verstehen soll, sollten Sie die *Kultur* in die entsprechende Sprache ändern.
6.  Hier können Sie auch eine Beschreibung *Ihrer* neuen LUIS-App hinzufügen.

    ![LUIS: Erstellen einer neuen App](images/AzureLabs-Lab3-10.png)

7.  Sobald Sie auf **Fertig klicken,** geben Sie die *Seite Erstellen* Ihrer neuen *LUIS-Anwendung* ein.
8.  Hier sind einige wichtige Konzepte zu verstehen:

    -   *Absicht*: Stellt die Methode dar, die nach einer Abfrage des Benutzers aufgerufen wird. Eine *ABSICHT* kann eine oder mehrere *ENTITÄTen enthalten.*
    -   *Die Entität* ist eine Komponente der Abfrage, die informationen beschreibt, die für die *ABSICHT relevant sind.*
    -   *Äußerungen sind* Beispiele für Abfragen, die vom Entwickler bereitgestellt werden und mit denen LUIS sich selbst trainiert.

Wenn diese Konzepte nicht ganz klar sind, machen Sie sich keine Sorgen, da sie in diesem Kurs in diesem Kapitel weiter erläutert werden.

Zunächst erstellen Sie die *Entitäten, die* zum Erstellen dieses Kurses erforderlich sind.

9.  Klicken Sie links auf der Seite auf *Entitäten* und dann auf **Neue Entität erstellen.**

    ![Erstellen einer neuen Entität](images/AzureLabs-Lab3-11.png)

10. Rufen Sie die neue *Entitätsfarbe auf,* legen Sie ihren Typ auf *Einfach fest,* und klicken Sie dann **auf Fertig.**

    ![Erstellen einer einfachen Entität – Farbe](images/AzureLabs-Lab3-12.png)
 
11. Wiederholen Sie diesen Vorgang, um drei weitere einfache Entitäten mit dem Namen zu erstellen:

    -   *Upsizing*
    -   *Verkleinern*
    -   *Ziel*

Das Ergebnis sollte wie in der folgenden Abbildung aussehen:

![Ergebnis der Entitätserstellung](images/AzureLabs-Lab3-13.png)
 
An diesem Punkt können Sie mit dem Erstellen von *Absichten beginnen.* 

> [!WARNING]
> Löschen Sie die Absicht **Keine** nicht.

12. Klicken Sie links auf der Seite auf **Intents (Absichten)** und dann **auf Create new intent (Neue Absicht erstellen).**

    ![Erstellen neuer Absichten](images/AzureLabs-Lab3-14.png)

13. Rufen Sie die neue *Absicht* **ChangeObjectColor auf.**

    > [!IMPORTANT]
    > Dieser *Absichtsname* wird später in diesem Kurs im Code verwendet. Verwenden Sie diesen Namen also genau wie angegeben, um optimale Ergebnisse zu erzielen.

Nachdem Sie den Namen bestätigt haben, werden Sie zur Seite "Absichten" geleitet.

![LUIS – Seite "Absichten"](images/AzureLabs-Lab3-15.png)

Sie werden feststellen, dass es ein Textfeld gibt, in dem Sie aufgefordert werden, 5 oder mehr verschiedene *Äußerungen ein.*

> [!NOTE]
> LUIS konvertiert alle Äußerungen in Klein klein.

14. Fügen Sie die folgende *Äußerung* in das obere Textfeld ein (derzeit mit dem Text *Geben Sie ca. 5 Beispiele ein...* ), und drücken Sie **die EINGABETASTE:**

```
The color of the cylinder must be red
```

Sie werden feststellen, dass die neue *Äußerung* in einer Liste darunter angezeigt wird.

Fügen Sie nach dem gleichen Prozess die folgenden sechs (6) Äußerungen ein:

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

Für jede äußerung, die Sie erstellt haben, müssen Sie identifizieren, welche Wörter von LUIS als Entitäten verwendet werden sollen. In diesem Beispiel müssen Sie alle  Farben als Farbentität und alle möglichen Verweise auf ein Ziel als *Zielentität beschriften.*

15. Klicken Sie dazu in der ersten Äußerung auf den *Wortkopf,* und wählen Sie *ziel aus.*

    ![Identifizieren von Äußerungszielen](images/AzureLabs-Lab3-16.png)
 
16. Klicken Sie nun in der ersten Äußerung auf das Wort *Rot,* und wählen Sie farbe *aus.*

    ![Identifizieren von Äußerungsentitäten](images/AzureLabs-Lab3-17.png)
 
17. Beschriften Sie auch die nächste Zeile, wobei *cube* ein Ziel *sein* soll, *und schwarz* sollte eine Farbe *sein.* Beachten Sie auch die Verwendung der Wörter *"this",* *"it"* und *"this object",* die wir bereitstellen, damit auch nicht spezifische Zieltypen verfügbar sind. 

18. Wiederholen Sie den oben genannten Vorgang, bis für alle Äußerungen die Bezeichnung Entitäten angegeben ist. Wenn Sie Hilfe benötigen, sehen Sie sich die folgende Abbildung an.

    > [!TIP]
    > Wenn Sie Wörter auswählen, um sie als Entitäten zu beschriften, gelten folgende Regeln:
    > - Klicken Sie für einzelne Wörter einfach darauf.
    > - Für einen Satz von zwei oder mehr Wörtern klicken Sie am Anfang und dann am Ende des Sets.

    > [!NOTE]
    > Sie können die *Umschaltfläche Tokenansicht* verwenden, um zwischen **Entitäten-/Tokenansicht zu wechseln.**

19. Die Ergebnisse sollten wie in den folgenden Abbildungen zu sehen sein, die die **Entitäten-/Tokenansicht zeigen:**

    ![Token & Entitätsansichten](images/AzureLabs-Lab3-18.png)
  
20. Klicken Sie an diesem **Punkt** rechts oben auf der Seite auf die Schaltfläche Trainieren, und warten Sie, bis der kleine runde Indikator darauf grün wird. Dies gibt an, dass LUIS erfolgreich trainiert wurde, um diese Absicht zu erkennen.

    ![Trainieren von LUIS](images/AzureLabs-Lab3-19.png)
 
21. Erstellen Sie als Übung für Sie eine neue Absicht namens **ChangeObjectSize,** indem Sie das Entitätsziel *verwenden,* *upsize* und *downsize verwenden.*
22. Fügen Sie nach dem gleichen Prozess wie bei der vorherigen Absicht die folgenden acht (8) Äußerungen für *größenänderung* ein:

    ```
    increase the dimensions of that

    reduce the size of this

    i want the sphere smaller

    make the cylinder bigger

    size down the sphere

    size up the cube

    decrease the size of that object

    increase the size of this object
    ```

23. Das Ergebnis sollte wie in der folgenden Abbildung aussehen:

    ![Einrichten der ChangeObjectSize-Token/-Entitäten](images/AzureLabs-Lab3-20.png) 

24. Nachdem beide Absichten, **ChangeObjectColor** und **ChangeObjectSize,** erstellt und  trainiert wurden, klicken Sie oben auf der Seite auf die Schaltfläche VERÖFFENTLICHEN.

    ![Veröffentlichen des LUIS-Diensts](images/AzureLabs-Lab3-21.png)

25. Auf der *Seite* Veröffentlichen finalisieren und veröffentlichen Sie Ihre LUIS-App, damit Ihr Code darauf zugreifen kann.

    1. Legen Sie die Dropdownliste *Publish To (Veröffentlichen in)* als **Production (Produktion) fest.**
    2. Legen Sie *die Zeitzone auf* Ihre Zeitzone fest.
    3. Aktivieren Sie das Kontrollkästchen Include all predicted intent scores (Alle **vorhergesagten Absichtsergebnisse enthalten).**
    4. Klicken Sie **auf Im Produktionsslot veröffentlichen.**

        ![Veröffentlichungseinstellungen](images/AzureLabs-Lab3-22.png)

26. Im Abschnitt *Ressourcen und Schlüssel:*

    1.  Wählen Sie im Azure-Portal die Region aus, die Sie für die Dienstinstanz festlegen.
    2.  Sie werden feststellen, **Starter_Key** unten ein Element enthält. Ignorieren Sie es.
    3.  Klicken Sie **auf Schlüssel hinzufügen,** und fügen Sie den *Schlüssel ein,* den Sie beim Erstellen Ihrer Dienstinstanz im Azure-Portal erhalten haben. Wenn Azure und das LUIS-Portal beim gleichen Benutzer angemeldet sind, werden Ihnen Dropdownmenüs für  Mandantenname, Abonnementname und den Schlüssel bereitgestellt, den Sie verwenden möchten (hat den gleichen Namen wie zuvor im Azure-Portal). 

    > [!IMPORTANT] 
    > Erstellen Sie *unter Endpunkt* eine Kopie des Endpunkts, der dem von Ihnen eingefügten Schlüssel entspricht. Sie werden ihn in Kürze in Ihrem Code verwenden.
 
## <a name="chapter-3--set-up-the-unity-project"></a>Kapitel 3: Einrichten des Unity-Projekts

Im Folgenden finden Sie eine typische Einrichtung für die Entwicklung mit Mixed Reality und daher eine gute Vorlage für andere Projekte.

1.  Öffnen Sie *Unity,* und klicken Sie **auf Neu.** 

    ![Starten Sie ein neues Unity-Projekt.](images/AzureLabs-Lab3-24.png)

2.  Sie müssen nun einen Unity-Project angeben und **MR_LUIS.** Stellen Sie sicher, dass der Projekttyp auf **3D festgelegt ist.** Legen Sie **den Speicherort** auf einen für Sie geeigneten Speicherort fest (denken Sie daran, dass die Nähe zu Stammverzeichnissen besser ist). Klicken Sie dann auf **Projekt erstellen.**

    ![Geben Sie Details für das neue Unity-Projekt an.](images/AzureLabs-Lab3-25.png)
 
3.  Wenn Unity geöffnet ist, sollten Sie überprüfen, ob der **Standardskript-Editor** auf **Visual Studio.** Wechseln Sie zu > Bearbeiten, und navigieren Sie dann im neuen Fenster zu **Externe Tools.** Ändern **Sie den editor für externe** **Skripts in Visual Studio 2017**. Schließen Sie das **Fenster Einstellungen.**

    ![Skript-Editor-Einstellung aktualisieren.](images/AzureLabs-Lab3-26.png)
 
4.  Wechseln Sie als Nächstes zu **Datei > Build Einstellungen** und wechseln Sie zur **universellen Windows-Plattform,** indem Sie auf **die Schaltfläche Plattform wechseln** klicken.

    ![Erstellen Einstellungen Fensters, Wechseln der Plattform zu UWP.](images/AzureLabs-Lab3-27.png)
 
5.  Wechseln Sie **zu Datei > Build Einstellungen,** und stellen Sie Sicher, dass:

    1. **Zielgerät** ist auf **Beliebiges Gerät festgelegt.**

        > Legen Sie für Microsoft HoloLens **Zielgerät auf** *HoloLens.*

    2. **Buildtyp** ist auf **D3D festgelegt**
    3. **SDK** ist auf **Latest installed (Neueste installiert) festgelegt.**
    4. **Visual Studio version** ist auf **Latest installed (Neueste installiert) festgelegt.**
    5. **Erstellen und Ausführen** ist auf Lokaler **Computer festgelegt.**
    6. Speichern Sie die Szene, und fügen Sie sie dem Build hinzu.

        1. Wählen Sie hierzu Geöffnete Szenen **hinzufügen aus.** Ein Speicherfenster wird angezeigt.
        
            ![Klicken Sie auf die Schaltfläche "Geöffnete Szenen hinzufügen".](images/AzureLabs-Lab3-28.png)

        2. Erstellen Sie einen neuen Ordner für diesen und jede  zukünftige Szene, und wählen Sie dann die Schaltfläche Neuer Ordner aus, um einen neuen Ordner zu erstellen, und nennen Sie **ihn Scenes**.

            ![Erstellen eines neuen Skriptordners](images/AzureLabs-Lab3-29.png)

        3. Öffnen Sie den neu erstellten **Ordner Scenes,** und geben Sie dann im Feld Dateiname *:* Text MR_LuisScene **ein,** und klicken Sie dann **auf Speichern.**

            ![Benennen Sie die neue Szene.](images/AzureLabs-Lab3-30.png)

    7. Die restlichen Einstellungen in *Build Einstellungen* sollten vorerde als Standardeinstellung be übrig bleiben.

6. Klicken Sie *im Fenster Build Einstellungen* auf die Schaltfläche Player **Einstellungen,** um den entsprechenden Bereich in dem Bereich zu öffnen, in dem sich der *Inspektor* befindet. 

    ![Öffnen Sie die Playereinstellungen.](images/AzureLabs-Lab3-31.png) 
 
7. In diesem Bereich müssen einige Einstellungen überprüft werden:

    1. Führen Sie **auf Einstellungen** Registerkarte Andere Optionen aus:

        1. **Die Skriptlaufzeitversion** sollte **stabil** sein (.NET 3.5 Equivalent).
        2. **Das Skript-Back-End** sollte **.NET sein.**
        3. **Der API-Kompatibilitätsgrad** sollte **.NET 4.6 sein.**

            ![Aktualisieren Sie andere Einstellungen.](images/AzureLabs-Lab3-32.png)
      
    2. Aktivieren Sie **auf Einstellungen** Registerkarte Publishing Einstellungen unter **Capabilities (Funktionen)** die folgenden Optionen:

        1. **InternetClient**
        2. **Mikrofon**

            ![Aktualisieren der Veröffentlichungseinstellungen.](images/AzureLabs-Lab3-33.png)

    3. Aktivieren Sie weiter unten im Bereich in **XR Einstellungen** (unter Publish **Einstellungen)** **(Virtual Reality** unterstützt), und stellen Sie sicher, dass das Windows Mixed Reality **SDK** hinzugefügt wird.

        ![Aktualisieren Sie die X R-Einstellungen.](images/AzureLabs-Lab3-34.png)

8.  Zurück in *Build Einstellungen* _Unity C#-Projekte_ ist nicht mehr ausgegraut. aktivieren Sie das Kontrollkästchen daneben. 
9.  Schließen Sie das Fenster „Build Settings“ (Buildeinstellungen).
10. Speichern Sie Ihre Szene und Project (**FILE > SAVE SCENE/FILE > SAVE PROJECT**).

## <a name="chapter-4--create-the-scene"></a>Kapitel 4: Erstellen der Szene

> [!IMPORTANT]
> Wenn Sie die Unity Set *up-Komponente* dieses Kurses überspringen und direkt mit dem Code fortfahren möchten, können [](https://docs.unity3d.com/Manual/AssetPackages.html)Sie dieses [UNITYPACKAGE](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage)herunterladen, als benutzerdefiniertes Paket in Ihr Projekt importieren und dann mit Kapitel [5](#chapter-5--create-the-microphonemanager-class)fortfahren. 

1.  Klicken Sie mit der rechten Maustaste in einen leeren Bereich des *Hierarchiebereichs,* und fügen Sie unter **3D-Objekt** eine **Ebene hinzu.**

    ![Erstellen Sie eine Ebene.](images/AzureLabs-Lab3-35.png)

2.  Beachten Sie, dass das ausgewählte  Objekt das übergeordnete Objekt des neuen Objekts ist, wenn Sie mit der rechten Maustaste erneut in die Hierarchie klicken, um weitere Objekte zu erstellen, wenn Sie noch das letzte Objekt ausgewählt haben. Vermeiden Sie dieses Klicken mit der linken Maustaste in einem leeren Bereich innerhalb der Hierarchie, und klicken Sie dann mit der rechten Maustaste.

3.  Wiederholen Sie das oben beschriebene Verfahren, um die folgenden Objekte hinzuzufügen:

    1. *Sphere*
    2. *Zylinder*
    3. *Cube*
    4. *3D-Text*

4.  Die resultierende *Szenenhierarchie* sollte der Hierarchie in der folgenden Abbildung ähnlich sein:

    ![Einrichtung der Szenenhierarchie.](images/AzureLabs-Lab3-36.png)
 
5.  Klicken Sie mit der linken Maustaste auf  **die Hauptkamera,** um sie auszuwählen. Im Inspektorbereich sehen Sie das Kameraobjekt mit allen Komponenten.
6.  Klicken Sie ganz **unten im Inspektorbereich** auf die Schaltfläche *Add Component (Komponente hinzufügen).*

    ![Hinzufügen einer Audioquelle](images/AzureLabs-Lab3-37.png)
 
7.  Suchen Sie wie oben gezeigt *nach der Komponente Audioquelle.*
8.  Stellen Sie außerdem sicher, dass die *Komponente* Transformieren der Hauptkamera auf (0,0,0) festgelegt ist. Klicken Sie hierzu auf das Zahnradsymbol neben der Komponente Transformieren der Kamera, und wählen Sie **Zurücksetzen aus.**   Die *Komponente Transformieren* sollte dann wie die folgenden aussehen:

    1.  *Position* ist auf **0, 0, 0 festgelegt.**
    2.  *Die Drehung* ist **auf 0, 0, 0 festgelegt.**

    > [!NOTE] 
    > Für die Microsoft HoloLens müssen Sie auch Folgendes ändern, die Teil der **Camera-Komponente** sind, die sich auf Ihrer **Hauptkamera befindet:**
    > - **Flags löschen:** Volltonfarbe.
    > - **Hintergrund** 'Schwarz, Alpha 0' – Hexadezimale Farbe: #00000000.

9.  Klicken Sie mit der linken Maustaste **auf die Ebene,** um sie auszuwählen. Legen Sie *im Inspektorbereich* die *Komponente Transformieren* mit den folgenden Werten fest:

    |   X-Achse    | Y-Achse |   Z-Achse    |
    |:-----:|:----------------------:|:-----:|
    | 0     | -1                     | 0     |


10. Klicken Sie mit der linken Maustaste **auf die Kugel,** um sie auszuwählen. Legen Sie *im Inspektorbereich* die *Komponente Transformieren* mit den folgenden Werten fest:

    |   X-Achse    | Y-Achse |   Z-Achse    |
    |:-----:|:----------------------:|:-----:|
    | 2     | 1                      | 2     |

11. Klicken Sie mit der linken **Maustaste auf den Zylinder,** um ihn auszuwählen. Legen Sie *im Inspektorbereich* die *Komponente Transformieren* mit den folgenden Werten fest:

    |   X-Achse    | Y-Achse |   Z-Achse    |
    |:-----:|:----------------------:|:-----:|
    | -2    | 1                      | 2     |

12. Klicken Sie mit der linken Maustaste **auf den Cube,** um ihn auszuwählen. Legen Sie *im Inspektorbereich* die *Komponente Transformieren* mit den folgenden Werten fest:

    |        | Transformieren – *Position* |       |  \| |       | Transformieren – *Drehung* |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | **X** | **J**                   | **Z** |  \| | **X** | **J**                  | **Z** |
    | 0     | 1                       | 4     |  \| | 45    | 45                     | 0     | 

13. Klicken Sie mit der linken Maustaste **auf das Objekt Neuer Text,** um es auszuwählen. Legen Sie *im Inspektorbereich* die *Komponente Transformieren* mit den folgenden Werten fest:

    |       | Transformieren – *Position* |       |  \| |       | Transformieren – *Skalieren* |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | **X** | **J**                  | **Z** |  \| | **X** | **J**               | **Z** |
    | -2    | 6                      | 9     |  \| | 0.1   | 0.1                 | 0.1   | 

14. Ändern **Sie den Schriftgrad** in der **Text Mesh-Komponente** in **50.**
15. Ändern Sie *den Namen* des **Text Mesh-Objekts** in **Dictation Text**.

    ![Erstellen eines 3D-Textobjekts](images/AzureLabs-Lab3-38.png)
 
16. Die Struktur des Hierarchiebereichs sollte nun wie hier aussehen:

    ![Textgitternetz in der Szenenansicht](images/AzureLabs-Lab3-38b.png)


17. Die letzte Szene sollte wie die folgende Abbildung aussehen:

    ![Die Szenenansicht.](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a>Kapitel 5: Erstellen der MicrophoneManager-Klasse

Das erste Skript, das Sie erstellen, ist die *MicrophoneManager-Klasse.* Im Anschluss erstellen Sie die *LuisManager-Klasse,* die *Verhaltensklasse* und schließlich die *Gaze-Klasse* (sie können jetzt alle erstellen, obwohl sie behandelt werden, wenn Sie jedes Kapitel erreichen).

Die *MicrophoneManager-Klasse* ist für Folgendes verantwortlich:

-   Erkennen des Aufzeichnungsgeräts, das an das Headset oder den Computer angeschlossen ist (je nachdem, welches das Standardgerät ist).
-   Erfassen Sie die Audiodatei (Stimme), und verwenden Sie das Diktat, um sie als Zeichenfolge zu speichern.
-   Sobald die Stimme angehalten wurde, übermitteln Sie das Diktat an die *LuisManager-Klasse.* 

So erstellen Sie diese Klasse: 

1.  Klicken Sie mit der rechten Maustaste in *Project Bereich*, erstellen **> Ordner**. Rufen Sie den Ordner **Scripts auf.** 

    ![Ordner "Skripts erstellen".](images/AzureLabs-Lab3-40.png)
 
2.  Doppelklicken Sie **nach** dem Erstellen des Ordners Skripts darauf, um ihn zu öffnen. Klicken Sie dann in diesem Ordner mit der rechten Maustaste auf **Create > C#-Skript.** Nennen Sie das *Skript MicrophoneManager*. 

3.  Doppelklicken Sie auf *MicrophoneManager,* um es mit dem *Visual Studio.*
4.  Fügen Sie am Anfang der Datei die folgenden Namespaces hinzu:

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  Fügen Sie dann die folgenden Variablen in der *MicrophoneManager-Klasse* hinzu:

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  Code für *die Methoden "Awake()"* und *"Start()"* muss nun hinzugefügt werden. Diese werden aufgerufen, wenn die -Klasse initialisiert wird:

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            if (Microphone.devices.Length > 0)
            {
                StartCapturingAudio();
                Debug.Log("Mic Detected");
            }
        }
    ```
 
7.  Nun benötigen Sie die Methode, die die App zum Starten und Beenden der Spracherfassung verwendet, und übergeben Sie sie an die *LuisManager-Klasse,* die Sie in Kürze erstellen werden. 

    ```csharp
        /// <summary>
        /// Start microphone capture, by providing the microphone as a continual audio source (looping),
        /// then initialise the DictationRecognizer, which will capture spoken words
        /// </summary>
        public void StartCapturingAudio()
        {
            if (dictationRecognizer == null)
            {
                dictationRecognizer = new DictationRecognizer
                {
                    InitialSilenceTimeoutSeconds = 60,
                    AutoSilenceTimeoutSeconds = 5
                };

                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
                dictationRecognizer.DictationError += DictationRecognizer_DictationError;
            }
            dictationRecognizer.Start();
            Debug.Log("Capturing Audio...");
        }

        /// <summary>
        /// Stop microphone capture
        /// </summary>
        public void StopCapturingAudio()
        {
            dictationRecognizer.Stop();
            Debug.Log("Stop Capturing Audio...");
        }
    ```

8.  Fügen Sie *einen Diktathandler hinzu,* der aufgerufen wird, wenn die Stimme angehalten wird. Diese Methode überträgt den Diktattext an die *LuisManager-Klasse.*

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// This method will stop listening for audio, send a request to the LUIS service 
        /// and then start listening again.
        /// </summary>
        private void DictationRecognizer_DictationResult(string dictationCaptured, ConfidenceLevel confidence)
        {
            StopCapturingAudio();
            StartCoroutine(LuisManager.instance.SubmitRequestToLuis(dictationCaptured, StartCapturingAudio));
            Debug.Log("Dictation: " + dictationCaptured);
            dictationText.text = dictationCaptured;
        }

        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            Debug.Log("Dictation exception: " + error);
        }
    ```
 
    > [!IMPORTANT]
    > Löschen Sie *die Update()-Methode,* da diese Klasse sie nicht verwendet.

9.  Achten Sie darauf, dass Sie Ihre Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity zurückkehren.*

    > [!NOTE]
    > An diesem Punkt wird im *Unity-Editor-Konsolenbereich ein Fehler angezeigt.* Dies liegt daran, dass der Code auf die *LuisManager-Klasse* verweist, die Sie im nächsten Kapitel erstellen.

## <a name="chapter-6--create-the-luismanager-class"></a>Kapitel 6: Erstellen der LUISManager-Klasse

Es ist an der Zeit, dass Sie die *LuisManager-Klasse* erstellen, die den Aufruf des Azure LUIS-Diensts durchführen wird. 

Der Zweck dieser Klasse ist es, den Diktattext von der *MicrophoneManager-Klasse* zu empfangen und an die *Azure Language Understanding-API* zu senden, die analysiert werden soll.

Diese Klasse deserialisiert die *JSON-Antwort* und aufruft die entsprechenden Methoden der *Verhaltensklasse,* um eine Aktion auszulösen.

So erstellen Sie diese Klasse: 

1.  Doppelklicken Sie auf den **Ordner Skripts,** um ihn zu öffnen. 
2.  Klicken Sie mit der rechten Maustaste in **den Ordner Skripts,** und klicken Sie **> C#-Skript erstellen.** Nennen Sie das *Skript LuisManager*. 
3.  Doppelklicken Sie auf das Skript, um es mit dem Visual Studio.
4.  Fügen Sie am Anfang der Datei die folgenden Namespaces hinzu:

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  Zunächst erstellen Sie drei  Klassen innerhalb der *LuisManager-Klasse* (innerhalb derselben Skriptdatei über der *Start()-Methode),* die die deserialisierte JSON-Antwort von Azure darstellen.

    ```csharp
        [Serializable] //this class represents the LUIS response
        public class AnalysedQuery
        {
            public TopScoringIntentData topScoringIntent;
            public EntityData[] entities;
            public string query;
        }

        // This class contains the Intent LUIS determines 
        // to be the most likely
        [Serializable]
        public class TopScoringIntentData
        {
            public string intent;
            public float score;
        }

        // This class contains data for an Entity
        [Serializable]
        public class EntityData
        {
            public string entity;
            public string type;
            public int startIndex;
            public int endIndex;
            public float score;
        }
    ```

6.  Fügen Sie als Nächstes die folgenden Variablen in der *LuisManager-Klasse* hinzu:
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  Stellen Sie sicher, dass Sie Ihren LUIS-Endpunkt jetzt in platzieren (den Sie über Ihr LUIS-Portal haben werden).

8.  Code für die *"Awake()"-Methode* muss nun hinzugefügt werden. Diese Methode wird aufgerufen, wenn die -Klasse initialisiert wird:

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  Nun benötigen Sie die Methoden, die diese Anwendung verwendet, um das von der *MicrophoneManager-Klasse* empfangene Diktat an *LUIS* zu senden und dann die Antwort zu empfangen und zu deserialisieren. 
10. Nachdem der Wert der Absicht und der zugeordneten Entitäten bestimmt wurde, werden sie an die Instanz der *Verhaltensklasse* übergeben, um die beabsichtigte Aktion auszulösen.

    ```csharp
        /// <summary>
        /// Call LUIS to submit a dictation result.
        /// The done Action is called at the completion of the method.
        /// </summary>
        public IEnumerator SubmitRequestToLuis(string dictationResult, Action done)
        {
            string queryString = string.Concat(Uri.EscapeDataString(dictationResult));

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(luisEndpoint + queryString))
            {
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                }
                else
                {
                    try
                    {
                        AnalysedQuery analysedQuery = JsonUtility.FromJson<AnalysedQuery>(unityWebRequest.downloadHandler.text);

                        //analyse the elements of the response 
                        AnalyseResponseElements(analysedQuery);
                    }
                    catch (Exception exception)
                    {
                        Debug.Log("Luis Request Exception Message: " + exception.Message);
                    }
                }

                done();
                yield return null;
            }
        }
    ```
 
11. Erstellen Sie eine neue Methode namens *AnalyseResponseElements(),* die die resultierende *Analyseabfrage* liest und die Entitäten bestimmt. Nachdem diese Entitäten bestimmt wurden, werden sie an die Instanz der *Verhaltensklasse* übergeben, die in den Aktionen verwendet werden soll.

    ```csharp
        private void AnalyseResponseElements(AnalysedQuery aQuery)
        {
            string topIntent = aQuery.topScoringIntent.intent;

            // Create a dictionary of entities associated with their type
            Dictionary<string, string> entityDic = new Dictionary<string, string>();

            foreach (EntityData ed in aQuery.entities)
            {
                entityDic.Add(ed.type, ed.entity);
            }

            // Depending on the topmost recognized intent, read the entities name
            switch (aQuery.topScoringIntent.intent)
            {
                case "ChangeObjectColor":
                    string targetForColor = null;
                    string color = null;

                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForColor = pair.Value;
                        }
                        else if (pair.Key == "color")
                        {
                            color = pair.Value;
                        }
                    }

                    Behaviours.instance.ChangeTargetColor(targetForColor, color);
                    break;

                case "ChangeObjectSize":
                    string targetForSize = null;
                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForSize = pair.Value;
                        }
                    }

                    if (entityDic.ContainsKey("upsize") == true)
                    {
                        Behaviours.instance.UpSizeTarget(targetForSize);
                    }
                    else if (entityDic.ContainsKey("downsize") == true)
                    {
                        Behaviours.instance.DownSizeTarget(targetForSize);
                    }
                    break;
            }
        }
    ```
 
    > [!IMPORTANT]
    > Löschen Sie *die Methoden Start()* und *Update(),* da diese Von dieser Klasse nicht verwendet werden.

12. Achten Sie darauf, dass Sie Ihre Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity zurückkehren.*

> [!NOTE]
> An diesem Punkt werden Sie feststellen, dass im *Unity-Editor-Konsolenbereich mehrere Fehler angezeigt werden.* Dies liegt daran, dass der Code auf die *Verhaltensklasse* verweist, die Sie im nächsten Kapitel erstellen werden.

## <a name="chapter-7--create-the-behaviours-class"></a>Kapitel 7: Erstellen der Verhaltensklasse

Die *Verhaltensklasse* löst die Aktionen mithilfe der Entitäten aus, die von der *LuisManager-Klasse bereitgestellt* werden.

So erstellen Sie diese Klasse: 

1.  Doppelklicken Sie auf den **Ordner Skripts,** um ihn zu öffnen. 
2.  Klicken Sie mit der rechten Maustaste in **den Ordner Skripts,** und klicken Sie **> C#-Skript erstellen.** Geben Sie dem Skript *den Namen Verhaltensverhalten.* 
3.  Doppelklicken Sie auf das Skript, um es mit *Visual Studio.*
4.  Fügen Sie dann die folgenden Variablen in der *Verhaltensklasse* hinzu:

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  Fügen Sie den *Methodencode "Awake()"* hinzu. Diese Methode wird aufgerufen, wenn die -Klasse initialisiert wird:

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  Die folgenden Methoden werden von der *LuisManager-Klasse* aufgerufen (die Sie zuvor erstellt haben), um zu bestimmen, welches Objekt das Ziel der Abfrage ist, und dann die entsprechende Aktion auszulösen.

    ```csharp
        /// <summary>
        /// Changes the color of the target GameObject by providing the name of the object
        /// and the name of the color
        /// </summary>
        public void ChangeTargetColor(string targetName, string colorName)
        {
            GameObject foundTarget = FindTarget(targetName);
            if (foundTarget != null)
            {
                Debug.Log("Changing color " + colorName + " to target: " + foundTarget.name);

                switch (colorName)
                {
                    case "blue":
                        foundTarget.GetComponent<Renderer>().material.color = Color.blue;
                        break;

                    case "red":
                        foundTarget.GetComponent<Renderer>().material.color = Color.red;
                        break;

                    case "yellow":
                        foundTarget.GetComponent<Renderer>().material.color = Color.yellow;
                        break;

                    case "green":
                        foundTarget.GetComponent<Renderer>().material.color = Color.green;
                        break;

                    case "white":
                        foundTarget.GetComponent<Renderer>().material.color = Color.white;
                        break;

                    case "black":
                        foundTarget.GetComponent<Renderer>().material.color = Color.black;
                        break;
                }          
            }
        }

        /// <summary>
        /// Reduces the size of the target GameObject by providing its name
        /// </summary>
        public void DownSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale -= new Vector3(0.5F, 0.5F, 0.5F);
        }

        /// <summary>
        /// Increases the size of the target GameObject by providing its name
        /// </summary>
        public void UpSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale += new Vector3(0.5F, 0.5F, 0.5F);
        }
    ```
 
7.  Fügen Sie *die FindTarget()-Methode* hinzu, um zu bestimmen, welches *der GameObjects* das Ziel der aktuellen Absicht ist. Bei dieser Methode wird das Ziel standardmäßig auf das *GameObject* festgelegt, das "anviert" wird, wenn kein explizites Ziel in den Entitäten definiert ist.

    ```csharp
        /// <summary>
        /// Determines which object reference is the target GameObject by providing its name
        /// </summary>
        private GameObject FindTarget(string name)
        {
            GameObject targetAsGO = null;

            switch (name)
            {
                case "sphere":
                    targetAsGO = sphere;
                    break;

                case "cylinder":
                    targetAsGO = cylinder;
                    break;

                case "cube":
                    targetAsGO = cube;
                    break;

                case "this": // as an example of target words that the user may use when looking at an object
                case "it":  // as this is the default, these are not actually needed in this example
                case "that":
                default: // if the target name is none of those above, check if the user is looking at something
                    if (gazedTarget != null) 
                    {
                        targetAsGO = gazedTarget;
                    }
                    break;
            }
            return targetAsGO;
        }
    ```
 
    > [!IMPORTANT]
    > Löschen Sie *die Methoden Start()* und *Update(),* da diese Von dieser Klasse nicht verwendet werden.

8.  Achten Sie darauf, dass Sie Ihre Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity zurückkehren.*

## <a name="chapter-8--create-the-gaze-class"></a>Kapitel 8 – Erstellen der Gaze-Klasse

Die letzte Klasse, die Sie zum Abschließen dieser App benötigen, ist die *Gaze-Klasse.* Diese Klasse aktualisiert den Verweis auf das *GameObject,* das sich derzeit im visuellen Fokus des Benutzers befindet.

So erstellen Sie diese Klasse: 

1.  Doppelklicken Sie auf den **Ordner Skripts,** um ihn zu öffnen. 
2.  Klicken Sie mit der rechten Maustaste in **den Ordner Skripts,** und klicken Sie **> C#-Skript erstellen.** Nennen Sie das Skript *Gaze*. 
3.  Doppelklicken Sie auf das Skript, um es mit *Visual Studio.*
4.  Fügen Sie den folgenden Code für diese Klasse ein:

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {        
            internal GameObject gazedObject;
            public float gazeMaxDistance = 300;

            void Update()
            {
                // Uses a raycast from the Main Camera to determine which object is gazed upon.
                Vector3 fwd = gameObject.transform.TransformDirection(Vector3.forward);
                Ray ray = new Ray(Camera.main.transform.position, fwd);
                RaycastHit hit;
                Debug.DrawRay(Camera.main.transform.position, fwd);

                if (Physics.Raycast(ray, out hit, gazeMaxDistance) && hit.collider != null)
                {
                    if (gazedObject == null)
                    {
                        gazedObject = hit.transform.gameObject;

                        // Set the gazedTarget in the Behaviours class
                        Behaviours.instance.gazedTarget = gazedObject;
                    }
                }
                else
                {
                    ResetGaze();
                }         
            }

            // Turn the gaze off, reset the gazeObject in the Behaviours class.
            public void ResetGaze()
            {
                if (gazedObject != null)
                {
                    Behaviours.instance.gazedTarget = null;
                    gazedObject = null;
                }
            }
        }
    ```
 
5.  Achten Sie darauf, dass Sie Ihre Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity zurückkehren.*

## <a name="chapter-9--completing-the-scene-setup"></a>Kapitel 9: Abschließen der Szeneneinrichtung

1.  Um die Einrichtung der Szene abzuschließen, ziehen Sie jedes erstellte  Skript aus dem Ordner Skripts auf das Objekt Hauptkamera im *Hierarchiebereich*.
2.  Wählen Sie **die Hauptkamera** aus, und sehen Sie sich den Inspektorbereich an. Sie sollten jedes angefügte Skript sehen können, und Sie werden feststellen, dass es parameter für jedes Skript gibt, die noch festgelegt werden müssen. 

    ![Festlegen der Kameraverweisziele.](images/AzureLabs-Lab3-41.png)

3.  Führen Sie die folgenden Anweisungen aus, um diese Parameter richtig zu setzen:

    1. *MicrophoneManager:*

        - Ziehen Sie *im Hierarchiebereich* das **Objekt Dictation Text (Diktattext)** in das Feld Dictation Text parameter value (Wert des **Diktattextparameters).**

    2. *Verhaltensweisen* aus dem *Hierarchiebereich:*

        - Ziehen Sie das **Sphere-Objekt** in das Feld Sphere-Verweisziel. 
        - Ziehen Sie **den Zylinder** in das Feld Ziel *des Zylinderverweises.*
        - Ziehen Sie **den Cube** in das *Feld Cubeverweisziel.*

    3. *Anvistik:*

        - Legen Sie *die maximale Entfernung anviert* **auf 300** fest (sofern noch nicht vorhanden). 

4.  Das Ergebnis sollte wie in der folgenden Abbildung aussehen:

    ![Kameraverweisziele anzeigen, jetzt festgelegt.](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a>Kapitel 10 – Testen im Unity-Editor

Testen Sie, ob das Szenensetup ordnungsgemäß implementiert ist.

Stellen Sie Folgendes sicher:

-   Alle Skripts werden an das **Hauptkameraobjekt** angefügt. 
-   Alle Felder im Hauptkamerainspektorbereich *sind* ordnungsgemäß zugewiesen.

1.  Klicken Sie **im Unity-Editor** auf die *Schaltfläche Wiedergabe.* Die App sollte innerhalb des angeschlossenen immersiven Headsets ausgeführt werden.

2.  Probieren Sie einige Äußerungen aus, z. B.:

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > Wenn in der Unity-Konsole ein Fehler beim Ändern des Standardaudiogeräts angezeigt wird, funktioniert die Szene möglicherweise nicht wie erwartet. Dies liegt an der Art und Weise, wie das Mixed Reality-Portal mit integrierten Mikrofonen für Headsets handelt, die diese haben. Wenn dieser Fehler angezeigt wird, beenden Sie einfach die Szene, und starten Sie sie erneut, und die Dinge sollten erwartungsgemäß funktionieren.

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a>Kapitel 11: Erstellen und Sideloaden der UWP-Projektmappe

Nachdem Sie sichergestellt haben, dass die Anwendung im Unity-Editor funktioniert, können Sie erstellen und bereitstellen.

So erstellen Sie:

1.  Speichern Sie die aktuelle Szene, indem Sie auf **Datei > speichern.**
2.  Wechseln Sie **zu Datei > Build Einstellungen**.
3.  Aktivieren Sie das Kontrollkästchen **Unity C#-Projekte** (nützlich zum Sehen und Debuggen Ihres Codes, sobald das UWP-Projekt erstellt wurde).
4.  Klicken Sie **auf Open Scenes hinzufügen** und dann auf **Erstellen.**

    ![Fenster Einstellungen Build](images/AzureLabs-Lab3-43.png)

4.  Sie werden aufgefordert, den Ordner auszuwählen, in dem Sie die Projektmappe erstellen möchten. 

5.  Erstellen Sie *einen ORDNER BUILDS,* und erstellen Sie in diesem Ordner einen weiteren Ordner mit einem geeigneten Namen Ihrer Wahl. 
6.  Klicken **Sie auf Ordner auswählen,** um den Build an diesem Speicherort zu starten.
 
    ![Ordner "Builds ](images/AzureLabs-Lab3-44.png)
     ![ erstellen" Auswählen des Ordners "Builds"](images/AzureLabs-Lab3-45.png)
 
7.  Sobald Unity die Erstellung abgeschlossen hat (dies kann einige Zeit dauern), sollte ein **Datei-Explorer-Fenster** am Speicherort Ihres Buildfensters geöffnet werden.

So stellen Sie auf dem lokalen Computer

1.  Öffnen *Visual Studio* die Projektmappendatei, die im vorherigen Kapitel [erstellt wurde.](#chapter-10--test-in-the-unity-editor)
2.  Wählen Sie **auf der Projektmappenplattform** **x86**, **Lokaler Computer aus.**
3.  Wählen Sie in **der Projektmappenkonfiguration** **Debuggen aus.**

    > Für die Microsoft HoloLens ist es möglicherweise einfacher, dies auf *Remotecomputer* zu setzen, damit Sie nicht an Ihren Computer geentert werden. Sie müssen jedoch auch die folgenden Schritte unternehmen:
    > - Kennen Sie **die IP-Adresse** Ihres HoloLens, die sie im Einstellungen > Network & Internet > Wi-Fi > *Finden.* IPv4 ist die Adresse, die Sie verwenden sollten. 
    > - Stellen Sie **sicher, dass der Entwicklermodus** **aktiviert ist.** finden Sie *Einstellungen > Update & Security > Für Entwickler.*

    ![Bereitstellen der App](images/AzureLabs-Lab3-46.png)
 
4.  Wechseln Sie zum **Menü Erstellen, und** klicken Sie **auf Projektmappe bereitstellen,** um die Anwendung auf Ihren Computer zu laden.
5.  Ihre App sollte nun in der Liste der installierten Apps angezeigt werden, die zum Start bereit sind!
6.  Nach dem Start werden Sie von der App aufgefordert, den Zugriff auf das Mikrofon zu _autorisieren._ Verwenden Sie *die Motion Controllers*, oder Voice *Input*, oder die *Tastatur,* um die **Schaltfläche JA zu** drücken. 

## <a name="chapter-12--improving-your-luis-service"></a>Kapitel 12 – Verbessern ihres LUIS-Diensts

>[!IMPORTANT] 
> Dieses Kapitel ist äußerst wichtig und muss möglicherweise mehrmals durch iteriert werden, da es zur Verbesserung der Genauigkeit Ihres LUIS-Diensts beitragen kann: Stellen Sie sicher, dass Sie dies abschließen.

Um das von LUIS bereitgestellte Verständnis zu verbessern, müssen Sie neue Äußerungen erfassen und verwenden, um Ihre LUIS-App neu zu trainieren.

Sie haben z. B. LUIS trainiert, "Erhöhen" und "Upsize" zu verstehen, aber möchten Sie nicht, dass Ihre App auch Wörter wie "Vergrößern" versteht?

Sobald Sie Ihre Anwendung mehrmals verwendet haben, wird alles, was Sie gesagt haben, von LUIS gesammelt und im LUIS-PORTAL verfügbar.

1.  Wechseln Sie unter diesem LINK zu Ihrer [Portalanwendung,](https://www.luis.ai/home)und melden Sie sich an.
2.  Nachdem Sie sich mit Ihren MS-Anmeldeinformationen angemeldet haben, klicken Sie auf Ihren *App-Namen.*
3.  Klicken Sie **links auf der Seite** auf die Schaltfläche Endpunkt-Äußerungen überprüfen.

    ![Überprüfen von Äußerungen](images/AzureLabs-Lab3-47.png)
 
4.  Ihnen wird eine Liste der Äußerungen angezeigt, die von Ihrer Mixed Reality-Anwendung an LUIS gesendet wurden.

    ![Liste der Äußerungen](images/AzureLabs-Lab3-48.png)
 
Sie werden einige hervorgehobene *Entitäten bemerken.* 

Indem Sie auf jedes hervorgehobene Wort bewegen, können Sie jede Äußerung überprüfen und bestimmen, welche Entität richtig erkannt wurde, welche Entitäten falsch sind und welche Entitäten übersehen werden.

Im obigen Beispiel wurde festgestellt, dass das Wort "spear" als Ziel hervorgehoben wurde. Daher war es erforderlich, den Fehler zu beheben, indem Sie mit der Maus auf das Wort bewegen und auf **Bezeichnung entfernen klicken.**

![Überprüfen von Äußerungen ](images/AzureLabs-Lab3-49.png)
 ![ Entfernen eines Bezeichnungsbilds](images/AzureLabs-Lab3-50.png)
 
5.  Wenn Sie Äußerungen finden, die vollständig falsch sind, können Sie sie mithilfe der Schaltfläche Löschen auf der rechten Seite des Bildschirms löschen. 

    ![Löschen falscher Äußerungen](images/AzureLabs-Lab3-51.png)

6.  Wenn Sie der Meinung sind, dass LUIS die Äußerung richtig interpretiert hat, können Sie ihr Verständnis mithilfe der Schaltfläche Add To Aligned Intent (Zu ausgerichteter **Absicht hinzufügen)** überprüfen.

    ![Hinzufügen zur ausgerichteten Absicht](images/AzureLabs-Lab3-52.png)

7.  Nachdem Sie alle angezeigten Äußerungen sortiert haben, versuchen Sie, die Seite neu zu laden, um zu sehen, ob weitere verfügbar sind.
8.  Es ist sehr wichtig, diesen Prozess so oft wie möglich zu wiederholen, um Ihr Anwendungsverständnis zu verbessern. 

**Viel Spaß!**

## <a name="your-finished-luis-integrated-application"></a>Ihre fertige integrierte LUIS-Anwendung

Herzlichen Glückwunsch! Sie haben eine Mixed Reality-App erstellt, die den Azure Language Understanding Intelligence Service nutzt, um zu verstehen, was ein Benutzer sagt, und auf diese Informationen zu handeln.

![Labergebnis](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a>Zusatzübungen

### <a name="exercise-1"></a>Übung 1

Wenn Sie diese Anwendung verwenden, stellen Sie möglicherweise fest, dass dies der Fall ist, wenn Sie auf das Floor-Objekt blicken und bitten, seine Farbe zu ändern. Können Sie herausarbeiten, wie Sie verhindern können, dass Ihre Anwendung die Farbe "Floor" ändert?

### <a name="exercise-2"></a>Übung 2

Versuchen Sie, die LUIS- und App-Funktionen zu erweitern, und fügen Sie zusätzliche Funktionen für Objekte in der Szene hinzu. Erstellen Sie beispielsweise neue Objekte am Anvits-Trefferpunkt, je nachdem, was der Benutzer sagt, und können sie dann zusammen mit aktuellen Szenenobjekten mit den vorhandenen Befehlen verwenden.