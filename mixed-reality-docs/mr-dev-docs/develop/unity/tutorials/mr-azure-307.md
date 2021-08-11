---
title: HoloLens (1. Generation) und Azure 307 – Machine Learning
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie Azure Machine Learning Studio (klassisch) in einer Mixed Reality-Anwendung implementieren.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, Tutorial, API, Machine Learning, ML, Machine Learning Studio, HoloLens, immersive, VR, Windows 10, Visual Studio
ms.openlocfilehash: 062be48afb69bf2c4fa2eddcd816070d4d2575da7f06fe4464fa87f85676796b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115199016"
---
# <a name="hololens-1st-gen-and-azure-307-machine-learning"></a>HoloLens (1. Generation) und Azure 307: Machine Learning

<br>

>[!NOTE]
>Die Tutorials der Mixed Reality Academy wurden im Hinblick auf HoloLens (1. Gen.) und immersive Mixed Reality-Headsets entworfen.  Daher halten wir es für wichtig, diese Tutorials für Entwickler verfügbar zu halten, die noch nach Anleitung beim Entwickeln für diese Geräte suchen.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für HoloLens 2 verwendet werden.  Sie werden gewartet, um weiterhin auf den unterstützten Geräten zu funktionieren. Es wird eine neue Reihe von Tutorials geben, die in Zukunft veröffentlicht werden, die veranschaulichen, wie sie für HoloLens 2 entwickelt werden.  Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn sie veröffentlicht werden.

<br>

![final product -start](images/AzureLabs-Lab7-0.png)

In diesem Kurs erfahren Sie, wie Sie einer Mixed Reality-Anwendung mithilfe von Azure Machine Learning Studio (klassisch) Machine Learning -Funktionen (ML) hinzufügen.

*Azure Machine Learning Studio (klassisch)* ist ein Microsoft-Dienst, der Entwicklern eine große Anzahl von Machine Learning-Algorithmen bereitstellt, die bei der Eingabe, Ausgabe, Vorbereitung und Visualisierung von Daten hilfreich sein können. Anhand dieser Komponenten ist es dann möglich, ein Predictive Analytics-Experiment zu entwickeln, es zu iterieren und es zum Trainieren Ihres Modells zu verwenden. Nach dem Training können Sie Ihr Modell in der Azure-Cloud betriebsbereit machen, damit es dann neue Daten bewertet. Weitere Informationen finden Sie auf der [Seite Azure Machine Learning Studio (klassisch).](https://azure.microsoft.com/services/machine-learning-studio/)

Nach Abschluss dieses Kurses verfügen Sie über eine Immersive Headset-Mixed Reality-Anwendung und haben gelernt, wie Sie folgende Schritte ausführen:

1.  Stellen Sie eine Tabelle mit Umsatzdaten für das *(klassische) Azure Machine Learning Studio-Portal* bereit, und entwerfen Sie einen Algorithmus, um zukünftige Verkäufe beliebter Artikel vorherzusagen.
2.  Erstellen Sie eine **Unity-Project**, die Vorhersagedaten vom ML-Dienst empfangen und interpretieren kann.
3.  Zeigen Sie die Prädikationsdaten visuell im **Unity-Project** an, indem Sie die beliebtesten Verkaufsartikel in einem Verkaufsregal bereitstellen.

In Ihrer Anwendung liegt es an Ihnen, wie Sie die Ergebnisse in Ihren Entwurf integrieren. In diesem Kurs erfahren Sie, wie Sie einen Azure-Dienst in Ihre Unity-Project integrieren. Es ist Ihre Aufgabe, das Wissen, das Sie aus diesem Kurs gewinnen, zu nutzen, um Ihre Mixed Reality-Anwendung zu verbessern.

Dieser Kurs ist ein eigenständiges Tutorial, das keine anderen Mixed Reality Labs direkt umfasst.

## <a name="device-support"></a>Geräteunterstützung

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td> MR und Azure 307: Maschinelles Lernen</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Während sich dieser Kurs hauptsächlich auf Windows Mixed Reality immersiven Headsets (VR) konzentriert, können Sie auch das, was Sie in diesem Kurs lernen, auf Microsoft HoloLens anwenden. Während Sie den Kurs durchgehen, werden Ihnen Hinweise zu allen Änderungen angezeigt, die Sie ggf. zur Unterstützung HoloLens verwenden müssen. Wenn Sie HoloLens verwenden, können Sie während der Spracherfassung ein Echo bemerken.

## <a name="prerequisites"></a>Voraussetzungen

> [!NOTE]
> Dieses Tutorial richtet sich an Entwickler, die grundlegende Erfahrung mit Unity und C# haben. Beachten Sie auch, dass die Voraussetzungen und die geschriebenen Anweisungen in diesem Dokument darstellen, was zum Zeitpunkt der Erstellung (Mai 2018) getestet und überprüft wurde. Sie können die neueste Software verwenden, wie im [Artikel installieren der Tools](../../install-the-tools.md)aufgeführt. Es sollte jedoch nicht davon ausgegangen werden, dass die Informationen in diesem Kurs perfekt mit dem übereinstimmen, was Sie in neuerer Software finden als die unten aufgeführten.

Für diesen Kurs wird die folgende Hardware und Software empfohlen:

- Ein Entwicklungs-PC, [der mit Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) für die Entwicklung immersiver Headsets (VR) kompatibel ist
- [Windows 10 Fall Creators Update (oder höher) mit aktivierter Option "Entwicklermodus"](../../install-the-tools.md#installation-checklist)
- [Das neueste Windows 10 SDK](../../install-the-tools.md#installation-checklist)
- [Unity 2017.4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- Ein [Windows Mixed Reality immersives Headset (VR)](../../../discover/immersive-headset-hardware-details.md) oder [ein Microsoft HoloLens](/hololens/hololens1-hardware) mit aktiviertem Entwicklermodus
- Internetzugriff für Azure-Setup und ML Datenabruf

## <a name="before-you-start"></a>Vorbereitung

Um Probleme bei der Erstellung dieses Projekts zu vermeiden, wird dringend empfohlen, das in diesem Tutorial erwähnte Projekt in einem Stammordner oder in einem Ordner in der Nähe des Stammordners zu erstellen (lange Ordnerpfade können zur Buildzeit Probleme verursachen). 

## <a name="chapter-1---azure-storage-account-setup"></a>Kapitel 1: Einrichten des Azure Storage-Kontos

Um die Azure Translator-API verwenden zu können, müssen Sie eine Instanz des Diensts so konfigurieren, dass sie Ihrer Anwendung zur Verfügung gestellt wird.
1.  Melden Sie sich beim  [Azure-Portal](https://portal.azure.com)an.

    > [!NOTE]
    > Wenn Sie noch nicht über ein Azure-Konto verfügen, müssen Sie eins erstellen. Wenn Sie dieses Tutorial in einer Classroom- oder Lab-Situation durchgehen, bitten Sie Ihren Dozenten oder einen der Proctors um Hilfe beim Einrichten Ihres neuen Kontos.

2.  Nachdem Sie angemeldet sind, klicken Sie im linken Menü auf **Storage Konten.**

    ![Azure Storage Kontoeinrichtung](images/AzureLabs-Lab7-1.png)

    > [!NOTE]
    > Das Wort **Neu** wurde möglicherweise in neueren Portalen durch **Ressource erstellen** ersetzt.

3.  Klicken Sie auf der Registerkarte **Storage Konten** auf **Hinzufügen.**

    ![Azure Storage Kontoeinrichtung](images/AzureLabs-Lab7-2.png)

4.  Im Bereich **Storage Konto erstellen:**

    1.  Fügen Sie einen **Namen** für Ihr Konto ein. Beachten Sie, dass dieses Feld nur Zahlen und Kleinbuchstaben akzeptiert.
    2.  Wählen Sie unter **Bereitstellungsmodell die** Option **Resource Manager** aus.
    3.  Wählen Sie unter **Kontoart** die Option **Storage (Allgemein v1)** aus.
    4.  Wählen Sie für **Leistung** die Option **Standard** aus.
    5.  Wählen Sie unter **Replikation** die Option **Georedundanter Speicher mit Lesezugriff (RA-GRS)** aus.
    6.  Belassen Sie **Sichere Übertragung erforderlich** als **Deaktiviert.**
    7.  Wählen Sie ein **Abonnement** aus.
    4. Wählen Sie eine **Ressourcengruppe** aus, oder erstellen Sie eine neue. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, Steuern des Zugriffs, Bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt zugeordnet sind (z. B. diese Labs), in einer gemeinsamen Ressourcengruppe zu speichern.

        > Weitere Informationen zu Azure-Ressourcengruppen finden Sie [im Artikel zu Ressourcengruppen.](/azure/azure-resource-manager/resource-group-portal)
    
    5.  Bestimmen Sie den **Speicherort** für Ihre Ressourcengruppe (wenn Sie eine neue Ressourcengruppe erstellen). Der Standort befindet sich idealerweise in der Region, in der die Anwendung ausgeführt wird. Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.

5.  Sie müssen auch bestätigen, dass Sie die für diesen Dienst geltenden Geschäftsbedingungen verstanden haben.

    ![Azure Storage Kontoeinrichtung](images/AzureLabs-Lab7-3.png)

6.  Nachdem Sie auf **Erstellen** geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. Dies kann eine Minute dauern.

7.  Sobald die Dienstinstanz erstellt wurde, wird eine Benachrichtigung im Portal angezeigt.

    ![Azure Storage Kontoeinrichtung](images/AzureLabs-Lab7-4.png)

## <a name="chapter-2---the-azure-machine-learning-studio--classic"></a>Kapitel 2: Die Azure Machine Learning Studio (klassisch)

Um die *Azure Machine Learning* verwenden zu können, müssen Sie eine Instanz des Machine Learning-Diensts konfigurieren, die ihrer Anwendung zur Verfügung gestellt wird.

1.  Klicken Sie im Azure-Portal oben links auf **Neu,** und suchen Sie **nach Machine Learning Studio-Arbeitsbereich,** und drücken Sie die **EINGABETASTE.**

    ![Die Azure Machine Learning Studio (klassisch)](images/AzureLabs-Lab7-5.png)

2.  Die neue Seite enthält eine Beschreibung des **Machine Learning Studio-Arbeitsbereichsdiensts.** Klicken Sie unten links in dieser Eingabeaufforderung auf die Schaltfläche **Erstellen,** um eine Zuordnung zu diesem Dienst zu erstellen.

3.  Nachdem Sie auf **Erstellen** geklickt haben, wird ein Bereich angezeigt, in dem Sie einige Details zu Ihrem neuen **Machine Learning Studio-Dienst** angeben müssen:

    1.  Fügen Sie den gewünschten **Arbeitsbereichsnamen** für diese Dienstinstanz ein.

    2.  Wählen Sie ein **Abonnement** aus.

    3. Wählen Sie eine **Ressourcengruppe** aus, oder erstellen Sie eine neue. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, Steuern des Zugriffs, Bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt zugeordnet sind (z. B. diese Labs), in einer gemeinsamen Ressourcengruppe zu speichern. 

        > Weitere Informationen zu Azure-Ressourcengruppen finden Sie [im Artikel zu Ressourcengruppen.](/azure/azure-resource-manager/resource-group-portal)

    4.  Bestimmen Sie den **Speicherort** für Ihre Ressourcengruppe (wenn Sie eine neue Ressourcengruppe erstellen). Der Standort befindet sich idealerweise in der Region, in der die Anwendung ausgeführt wird. Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar. Sie sollten dieselbe Ressourcengruppe verwenden, die Sie im vorherigen Kapitel zum Erstellen der Azure Storage verwendet haben.

    5.  Klicken Sie für den Abschnitt **Storage Konto** auf **Vorhandene verwenden,** klicken Sie dann auf das Dropdownmenü und dann auf das **Storage Konto,** das Sie im letzten Kapitel erstellt haben.

    6.  Wählen Sie im Dropdownmenü den entsprechenden **Tarif** für Arbeitsbereich aus.

    7.  Klicken Sie im Abschnitt **Webdienstplan** auf Neu **erstellen,** **und** fügen Sie dann einen Namen dafür in das Textfeld ein.

    8.  Wählen Sie im Abschnitt Tarif des **Webdienstplans** den gewünschten Tarif aus. Eine Entwicklungstestebene mit dem Namen **DEVTEST Standard** sollte Ihnen kostenlos zur Verfügung stehen.

    9.  Sie müssen auch bestätigen, dass Sie die für diesen Dienst geltenden Geschäftsbedingungen verstanden haben.

    10. Klicken Sie auf **Erstellen**.

        ![Die Azure Machine Learning Studio (klassisch)](images/AzureLabs-Lab7-6.png)

4.  Nachdem Sie auf **Erstellen** geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. Dies kann eine Minute dauern.

5.  Sobald die Dienstinstanz erstellt wurde, wird eine Benachrichtigung im Portal angezeigt.

    ![Die Azure Machine Learning Studio (klassisch)](images/AzureLabs-Lab7-7.png)

6.  Klicken Sie auf die Benachrichtigung, um Ihre neue Dienstinstanz zu untersuchen.

    ![Die Azure Machine Learning Studio (klassisch)](images/AzureLabs-Lab7-8.png)

7.  Klicken Sie in der Benachrichtigung auf die Schaltfläche **Zu Ressource** wechseln, um Ihre neue Dienstinstanz zu untersuchen.

8.  Klicken Sie auf der angezeigten Seite im Abschnitt **Zusätzliche Links** auf Launch Machine Learning **Studio (Starten Machine Learning Studio),** um Ihren Browser zum **Machine Learning Studio-Portal** weiterzuleiten.

    ![Die Azure Machine Learning Studio (klassisch)](images/AzureLabs-Lab7-9.png)

9.  Verwenden Sie die Schaltfläche **Anmelden** oben rechts oder in der Mitte, um sich bei Ihrem Machine Learning Studio (klassisch) anzumelden.

    ![Die Azure Machine Learning Studio (klassisch)](images/AzureLabs-Lab7-10.png)


## <a name="chapter-3---the-machine-learning-studio-classic-dataset-setup"></a>Kapitel 3 : Die Machine Learning Studio (klassisch): Dataseteinrichtung

Eine der Möglichkeiten Machine Learning Algorithmen besteht darin, vorhandene Daten zu analysieren und dann zu versuchen, zukünftige Ergebnisse basierend auf dem vorhandenen Dataset vorherzusagen. Dies bedeutet im Allgemeinen, dass der Algorithmus bei der Vorhersage zukünftiger Ergebnisse je mehr daten vorhanden sind, desto besser.

Für diesen Kurs wird Eine Beispieltabelle mit dem Namen [ProductsTableCSV](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip)bereitgestellt und kann hier heruntergeladen werden.

> [!IMPORTANT]
> Die oben .zip-Datei enthält sowohl die **ProductsTableCSV** als auch das **UNITYPACKAGE,** die Sie in [Kapitel 6](#chapter-6---importing-the-mlproducts-unity-package)benötigen. Dieses Paket wird auch in diesem Kapitel bereitgestellt, jedoch getrennt von der CSV-Datei.

Dieses Beispieldatensatz enthält einen Datensatz der Best Selling-Objekte zu jeder Stunde jedes Tages des Jahres 2017.
        
![Die Machine Learning Studio (klassisch): Dataseteinrichtung](images/AzureLabs-Lab7-11.png)

Beispiel: Am 1. Tag 2017 um 13:00 Uhr (Stunde 13) waren Salt und Peperika das meistverkaufte Element.

Diese Beispieltabelle enthält 9998 Einträge.

1.  Kehren Sie zum **(klassischen) Machine Learning Studio-Portal** zurück, und fügen Sie diese Tabelle als **Dataset** für Ihre ML hinzu. Klicken Sie hierzu in der unteren linken Ecke des Bildschirms auf die Schaltfläche **+ Neu.**

    ![Die Machine Learning Studio (klassisch): Dataseteinrichtung](images/AzureLabs-Lab7-12.png)

2.  Ein Abschnitt wird von unten nach oben angezeigt, und in diesem befindet sich der Navigationsbereich auf der linken Seite. Klicken Sie auf **Dataset** und dann rechts davon auf **Aus lokaler Datei.**

    ![Die Machine Learning Studio (klassisch): Dataseteinrichtung](images/AzureLabs-Lab7-13.png)

3.  Hochladen Sie das neue **Dataset** wie folgt vor:

    1. Das Uploadfenster wird angezeigt, in dem Sie Ihre Festplatte für das neue Dataset **durchsuchen** können.

        ![Die Machine Learning Studio (klassisch): Dataseteinrichtung](images/AzureLabs-Lab7-14.png)

    2.  Lassen Sie das Kontrollkästchen nach der Auswahl und zurück im Uploadfenster nicht mehr aktiviert.

    3.  Geben Sie im folgenden Textfeld **ProductsTableCSV.csv** als Namen für das Dataset ein (sollte jedoch automatisch hinzugefügt werden).

    4.  Wählen Sie im Dropdownmenü für **Typ** die Option **Generische CSV-Datei mit einem Header (.csv)** aus.

    5.  Drücken Sie unten rechts im Uploadfenster den Tick, und Ihr **Dataset** wird hochgeladen.

## <a name="chapter-4---the-machine-learning-studio-classic-the-experiment"></a>Kapitel 4 : The Machine Learning Studio (classic): The Experiment (Kapitel 4– Die Machine Learning Studio (klassisch): Das Experiment

Bevor Sie Ihr Machine Learning-System erstellen können, müssen Sie ein Experiment erstellen, um Ihre Theorie zu Ihren Daten zu überprüfen. Mit den Ergebnissen wissen Sie, ob Sie mehr Daten benötigen oder ob es keine Korrelation zwischen den Daten und einem möglichen Ergebnis gibt.

So beginnen Sie mit der Erstellung eines Experiments:

1.  Klicken Sie unten links auf der Seite erneut auf die Schaltfläche **+ Neu,** und klicken Sie dann auf   >  **Experiment Blank Experiment**.

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-15.png)

2.  Eine neue Seite wird mit einem leeren Experiment angezeigt:

3.  Erweitern Sie im Bereich auf der linken Seite Saved Datasets My **Datasets (Gespeicherte**  >  **Datasets Meine Datasets),** und ziehen Sie **productsTableCSV** auf den **Experimentbereich**.

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-16.png)

4.  Erweitern Sie im Bereich auf der linken Seite **datentransformationsbeispiel**  >  **und teilen.** Ziehen Sie dann das Element **Split Data (Daten aufteilen)** in den **Experimentbereich**. Das Element Daten aufteilen teilt das Dataset in zwei Teile auf. Ein Teil, den Sie zum Trainieren des Machine Learning-Algorithmus verwenden. Der zweite Teil wird verwendet, um die Genauigkeit des generierten Algorithmus auszuwerten.

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-17.png)

5.  Bearbeiten Sie im rechten Bereich (während das Element Daten aufteilen im Zeichenbereich ausgewählt ist) den **Anteil der Zeilen im ersten Ausgabedataset** auf **0,7.** Dadurch werden die Daten in zwei Teile aufgeteilt, der erste Teil ist 70 % der Daten, und der zweite Teil ist der restliche Teil 30 %. Um sicherzustellen, dass die Daten nach dem Zufallsprinzip aufgeteilt werden, stellen Sie sicher, dass das Kontrollkästchen **Zufällige Aufteilung** aktiviert bleibt.

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-18.png)

6.  Ziehen Sie eine Verbindung von der Basis des **Elements ProductsTableCSV** im Zeichenbereich an den Anfang des Elements Daten aufteilen. Dadurch werden die Elemente verbunden und die Ausgabe des **Datasets ProductsTableCSV** (die Daten) an die Eingabe Split Data gesendet.  

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-19.png)

7.  Erweitern Sie im Bereich **Experimente** auf der linken Seite **Machine Learning**  >  **Trainieren.** Ziehen Sie das Element **Train Model (Modell trainieren)** in den Experimentbereich. Ihr Zeichenbereich sollte wie unten dargestellt aussehen.

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-20.png)

8.  Ziehen Sie vom ***unteren linken** _ des Elements _ *Split Data** eine Verbindung nach **oben rechts** des **Train Model-Elements.** Die erste Aufteilung von 70 % aus dem Dataset wird vom Train Model zum Trainieren des Algorithmus verwendet.

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-21.png)

9.  Wählen Sie im Zeichenbereich das Element **Train Model (Modell trainieren)** aus, und klicken Sie im **Bereich Eigenschaften** (rechts im Browserfenster) auf die Schaltfläche Launch **column selector (Spaltenauswahl starten).**

10. Geben Sie im Textfeld **product** ein, und drücken Sie dann die **EINGABETASTE.** *Das Produkt* wird als Spalte zum Trainieren von Vorhersagen festgelegt. Klicken Sie anschließend auf den **Teilstrich** in der unteren rechten Ecke, um das Auswahldialogfeld zu schließen.

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-22.png)

11. Sie trainieren einen **Multiklassenalgorithmus** für die logistische Regression, um das am häufigsten verkaufte **Produkt** basierend auf der Tageszeit und dem Datum vorherzusagen. Es geht über den Rahmen dieses Dokuments hinaus, die Details der verschiedenen Algorithmen zu erläutern, die vom Azure Machine Learning Studio bereitgestellt werden. Weitere Informationen finden Sie jedoch im [Machine Learning Algorithm Cheat Sheet.](/azure/machine-learning/studio/algorithm-cheat-sheet)

12. Erweitern Sie im Bereich mit den Experimentelementen auf der linken Seite **Machine Learning**  >    >  **Modellklassifizierung** initialisieren, und ziehen Sie das Element **Multiclass Logistic Regression** auf den Experimentbereich.

13. Verbinden die Ausgabe vom unteren Rand der **logistischen Regression** mit mehreren Klassen bis zur Eingabe oben links des Elements Train Model **(Modell trainieren).**

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-23.png)

14. Erweitern Sie in der Liste der Experimentelemente im Bereich auf der linken Seite **Machine Learning**  >  **Score**, und ziehen Sie das Element **Score Model** auf den Zeichenbereich.

15. Verbinden die Ausgabe vom unteren Rand des **Train Model**-Werts bis zur Eingabe oben links des Score **Model -Werts.**

16. Verbinden die Ausgabe unten rechts von **Split Data (Daten aufteilen)** in die eingabe oben rechts des Elements **Score Model (Modellbewertung)** ein.

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-24.png)

17. Erweitern Sie in der Liste der **Experimentelemente** im Bereich auf der linken Seite **Machine Learning**  >  **Evaluate**, und ziehen Sie das Element **Evaluate Model (Modell auswerten)** in den Zeichenbereich.

18. Verbinden die Ausgabe von **Score Model** in die eingabe oben links von **Evaluate Model**.

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-25.png)

19. Sie haben Ihr erstes Machine Learning Experiment erstellt. Sie können das Experiment jetzt speichern und ausführen. Klicken Sie im Menü am unteren Rand der Seite auf die Schaltfläche **Speichern,** um Das Experiment zu speichern, und klicken Sie dann auf **Ausführen,** um das Experiment zu starten.

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-26.png)

20. Sie können den **Status** des Experiments oben rechts im Zeichenbereich anzeigen. Warten Sie einen Moment, bis das Experiment abgeschlossen ist.

    > Wenn Sie über ein großes (echtes) Dataset verfügen, kann es wahrscheinlich Stunden dauern, bis das Experiment ausgeführt wird.

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-27.png)

21. Klicken Sie im Zeichenbereich mit der rechten Maustaste auf das Element **Modell auswerten,** zeigen Sie im Kontextmenü mit der Maus auf **Auswertungsergebnisse,** und wählen Sie dann **Visualisieren** aus.

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-28.png)

22. Die Auswertungsergebnisse werden mit den vorhergesagten Ergebnissen und den tatsächlichen Ergebnissen angezeigt. Dabei werden die 30 % des ursprünglichen Datasets, das zuvor geteilt wurde, für die Auswertung des Modells verwendet. Sie können sehen, dass die Ergebnisse nicht hervorragend sind. Im Idealfall ist die höchste Zahl in jeder Zeile das hervorgehobene Element in den Spalten.

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-29.png)

23. Schließen Sie die **Ergebnisse**.

24. Um Ihr neu trainiertes Machine Learning Modell zu verwenden, müssen Sie es als **Webdienst** verfügbar machen. Klicken Sie hierzu im Menü am unteren Rand der Seite auf das Menüelement **Webdienst einrichten,** und klicken Sie auf **Predictive Web Service**.

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-30.png)

25. Es wird eine neue Registerkarte erstellt, und das Trainingsmodell wird zusammengeführt, um den neuen Webdienst zu erstellen. 

26. Klicken Sie im Menü am unteren Rand der Seite auf **Speichern** und dann auf **Ausführen.** Der Status wird in der oberen rechten Ecke des Experimentbereichs aktualisiert.

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-31.png)

27. Sobald die Ausführung abgeschlossen ist, wird unten auf der Seite die Schaltfläche **Webdienst bereitstellen** angezeigt. Sie können den Webdienst bereitstellen. Klicken Sie im Menü unten auf der Seite auf Deploy Web Service (Classic) **(Webdienst** bereitstellen (klassisch)).

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-32.png)

    > Ihr Browser fordert Sie möglicherweise auf, ein Popupfenster zuzulassen, das Sie **zulassen** sollten, obwohl Sie möglicherweise erneut auf **Deploy Web Service (Webdienst** bereitstellen) klicken müssen, wenn die Bereitstellungsseite nicht angezeigt wird. 

28. Nachdem das Experiment erstellt wurde, werden Sie zu einer **Dashboardseite** weitergeleitet, auf der Ihr **API-Schlüssel** angezeigt wird. Kopieren Sie ihn für den Moment in einen Editor. Sie benötigen ihn in Kürze in Ihrem Code. Nachdem Sie Ihren API-Schlüssel notiert haben, klicken Sie im Abschnitt **Standardendpunkt** unter dem Schlüssel auf die Schaltfläche **ANFORDERUNG/ANTWORT.**

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-33.png)

    > [!NOTE] 
    > Wenn Sie auf dieser Seite auf Testen klicken, können Sie Eingabedaten eingeben und die Ausgabe anzeigen. Geben Sie den **Tag** und die **Stunde** ein. Lassen Sie den **Produkteintrag** leer. Klicken Sie dann auf die Schaltfläche **Bestätigen.** Die Ausgabe am unteren Rand der Seite zeigt den JSON-Code an, der die Wahrscheinlichkeit darstellt, dass jedes Produkt die Wahl ist.

29. Eine neue Webseite wird geöffnet, auf der die Anweisungen und einige Beispiele zur Anforderungsstruktur angezeigt werden, die für die Machine Learning Studio (klassisch) erforderlich ist. Kopieren Sie den auf dieser Seite angezeigten **Anforderungs-URI** in Ihren Editor.

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-34.png)

Sie haben nun ein Machine Learning-System erstellt, das das wahrscheinlichste Produkt bereitstellt, das basierend auf historischen Kaufdaten verkauft werden kann, korreliert mit der Tages- und Tageszeit des Jahres.

Um den Webdienst aufzurufen, benötigen Sie die URL für den Dienstendpunkt und einen API-Schlüssel für den Dienst. Klicken Sie im oberen Menü auf die Registerkarte **Nutzen.**

Auf der Seite **Verbrauchsinformationen** werden die Informationen angezeigt, die Sie benötigen, um den Webdienst aus Ihrem Code aufzurufen. Erstellen Sie eine Kopie des **Primärschlüssels** und der **Anforderung-Antwort-URL.** Diese benötigen Sie im nächsten Kapitel.

## <a name="chapter-5---setting-up-the-unity-project"></a>Kapitel 5: Einrichten der Unity-Project

Richten Sie Ihr Mixed Reality Immersive Headset ein, und testen Sie es.

> [!NOTE]
>  Für diesen Kurs benötigen Sie **keine** Motion Controllers. Wenn Sie Unterstützung beim Einrichten des immersiven Headsets benötigen, klicken Sie [hier.](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)

1.  Öffnen Sie **Unity,** und erstellen Sie eine neue Unity-Project namens **MR \_ MachineLearning.** Stellen Sie sicher, dass der Projekttyp auf **3D** festgelegt ist.

2.  Wenn Unity geöffnet ist, sollten Sie überprüfen, ob der **Standardskript-Editor** auf **Visual Studio** festgelegt ist. Navigieren **Sie** zu  >  **Einstellungen** bearbeiten, und navigieren Sie dann im neuen Fenster zu **Externe Tools.** Ändern Sie **den externen Skript-Editor** in **Visual Studio 2017**. Schließen Sie das Fenster **Einstellungen.**

3.  Wechseln Sie als Nächstes zu  >  **Dateibuild Einstellungen,** und wechseln Sie die Plattform zu **Universal Windows Platform,** indem Sie auf die Schaltfläche Plattform **_wechseln_** klicken.

4.  Stellen Sie außerdem Sicher, dass:

    1.  **Zielgerät** ist auf **Beliebiges Gerät** festgelegt.

        > Legen Sie für die Microsoft HoloLens **Zielgerät** auf *HoloLens* fest.

    2.  **Buildtyp** ist auf **D3D** festgelegt.

    3.  **Das SDK** ist auf **Neueste installierte** festgelegt.

    4.  **Visual Studio Version** ist auf **Neueste installiert festgelegt.**

    5.  **Build und Ausführung** ist auf **Lokaler Computer** festgelegt.

    6.  Machen Sie sich keine Gedanken über das Einrichten von **Szenen,** da diese später bereitgestellt werden.

    7.  Die übrigen Einstellungen sollten vorerst als Standard festgelegt werden.

        ![Einrichten der Unity-Project](images/AzureLabs-Lab7-35.png)

5.  Klicken **Sie** im Fenster Build Einstellungen auf die Schaltfläche **Player Einstellungen.** Dadurch wird der zugehörige Bereich in dem Bereich geöffnet, in dem sich der **Inspektor** befindet. 

6. In diesem Bereich müssen einige Einstellungen überprüft werden:

    1.  Auf der Registerkarte **Andere Einstellungen:**

        1.  **Skriptlaufzeitversion**  muss **experimentell** sein (.NET 4.6-Entsprechung)

        2. **Skript-Back-End** sollte **_.NET_ sein**

        3. **Der API-Kompatibilitätsgrad** sollte **.NET 4.6** sein.

            ![Einrichten der Unity-Project](images/AzureLabs-Lab7-36.png)

    2.  Aktivieren **Sie** auf der Registerkarte Veröffentlichen Einstellungen unter **Funktionen** Folgendes:

        - **InternetClient**

            ![Einrichten der Unity-Project](images/AzureLabs-Lab7-37.png)

    3.  Aktivieren Sie weiter unten im Bereich in **XR Einstellungen** (finden Sie unter **Veröffentlichen Einstellungen**), aktivieren Sie Virtual Reality **Supported (Virtual Reality Unterstützt),** und stellen Sie sicher, dass das **Windows Mixed Reality SDK** hinzugefügt wurde.

        ![Einrichten der Unity-Project](images/AzureLabs-Lab7-38.png)

    

6.  Zurück in **Build Einstellungen** *Unity C#-Projekte* ist nicht mehr abgeblendet. Aktivieren Sie das Kontrollkästchen daneben. 

7.  Schließen Sie das Fenster „Build Settings“ (Buildeinstellungen).

8.  Speichern Sie Ihre Project (**DATEI > PROJEKT SPEICHERN**).

## <a name="chapter-6---importing-the-mlproducts-unity-package"></a>Kapitel 6: Importieren des MLProducts-Unity-Pakets

Für diesen Kurs müssen Sie ein Unity-Ressourcenpaket mit dem Namen [**Azure-MR-307.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage)herunterladen. Dieses Paket umfasst eine Szene mit allen Objekten in diesem vordefinierten , sodass Sie sich darauf konzentrieren können, dass alles funktioniert. Das **ShelfKeeper-Skript** wird bereitgestellt, enthält jedoch nur die öffentlichen Variablen für die Szeneneinrichtungsstruktur. Sie müssen alle anderen Abschnitte durchführen. 

So importieren Sie dieses Paket:

1.  Wenn Sie das Unity-Dashboard vor sich haben, klicken Sie im Menü oben auf dem Bildschirm auf **Assets** und dann auf **Paket importieren, benutzerdefiniertes Paket.**

    ![Importieren des MLProducts Unity-Pakets](images/AzureLabs-Lab7-39.png)

2.  Verwenden Sie die Dateiauswahl, um das Paket **Azure-MR-307.unitypackage** auszuwählen, und klicken Sie auf **Öffnen.**

3.  Ihnen wird eine Liste der Komponenten für dieses Medienobjekt angezeigt. Bestätigen Sie den Import, indem Sie auf **Importieren** klicken.

    ![Importieren des MLProducts Unity-Pakets](images/AzureLabs-Lab7-40.png)

4.  Sobald der Import abgeschlossen ist, werden Sie feststellen, dass einige neue Ordner in Ihrem Unity **Project Panel** angezeigt wurden. Dies sind die 3D-Modelle und die entsprechenden Materialien, die Teil der vorgefertigten Szene sind, an der Sie arbeiten werden. Sie schreiben den Großteil des Codes in diesem Kurs.

    ![Importieren des MLProducts Unity-Pakets](images/AzureLabs-Lab7-41.png)

5.  Klicken Sie im **ordner Project Panel (Bereich)** auf den Ordner **Scenes (Szenen),** und doppelklicken Sie auf die Szene innerhalb von **(MR_MachineLearningScene**). Die Szene wird geöffnet (siehe Abbildung unten). Wenn die roten Rauten fehlen, klicken Sie einfach oben rechts im **Spielbereich** auf die Schaltfläche **"Editionsmos".**

    ![Importieren des MLProducts Unity-Pakets](images/AzureLabs-Lab7-44.png)

## <a name="chapter-7---checking-the-dlls-in-unity"></a>Kapitel 7: Überprüfen der DLLs in Unity

Um die Verwendung von JSON-Bibliotheken zu nutzen (die zum Serialisieren und Deserialisieren verwendet werden), wurde eine Newtonsoft-DLL mit dem paket implementiert, das Sie eingefügt haben. Die Bibliothek sollte über die richtige Konfiguration verfügen, es ist jedoch sinnvoll, dies zu überprüfen (insbesondere, wenn Probleme mit Code auftreten, der nicht funktioniert). 

Gehen Sie folgendermaßen vor:

-  Klicken Sie mit der linken Maustaste auf die Datei Newtonsoft im Ordner Plug-Ins, und sehen Sie sich den **Bereich Inspector an.** Stellen Sie sicher, dass **Alle Plattformen** aktiviert ist. Wechseln Sie zur **Registerkarte UWP,** und stellen Sie außerdem sicher, dass **Nicht verarbeiten** aktiviert ist.

    ![Importieren der DLLs in Unity](images/AzureLabs-Lab7-48.png)

## <a name="chapter-8---create-the-shelfkeeper-class"></a>Kapitel 8: Erstellen der Klasse "ShelfKeeper"

Die **ShelfKeeper-Klasse** hostet Methoden, die die Benutzeroberfläche und die in der Szene ausgelösten Produkte steuern.

Als Teil des importierten Pakets erhalten Sie diese Klasse, obwohl sie unvollständig ist. Es ist nun an der Zeit, diese Klasse abzuschließen:

1.  Doppelklicken Sie im Ordner **Scripts** auf das **Skript ShelfKeeper,** um es mit **Visual Studio 2017** zu öffnen.

2.  Ersetzen Sie den gesamten im Skript vorhandenen Code durch den folgenden Code, der die Uhrzeit und das Datum festlegt und über eine -Methode zum Anzeigen eines Produkts verfügt.

    ```csharp
    using UnityEngine;

    public class ShelfKeeper : MonoBehaviour
    {
        /// <summary>
        /// Provides this class Singleton-like behavior
        /// </summary>
        public static ShelfKeeper instance;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for data
        /// </summary>
        public TextMesh dateText;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for time
        /// </summary>
        public TextMesh timeText;

        /// <summary>
        /// Provides references to the spawn locations for the products prefabs
        /// </summary>
        public Transform[] spawnPoint;

        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Set the text of the date in the scene
        /// </summary>
        public void SetDate(string day, string month)
        {
            dateText.text = day + " " + month;
        }

        /// <summary>
        /// Set the text of the time in the scene
        /// </summary>
        public void SetTime(string hour)
        {
            timeText.text = hour + ":00";
        }

        /// <summary>
        /// Spawn a product on the shelf by providing the name and selling grade
        /// </summary>
        /// <param name="name"></param>
        /// <param name="sellingGrade">0 being the best seller</param>
        public void SpawnProduct(string name, int sellingGrade)
        {
            Instantiate(Resources.Load(name),
                spawnPoint[sellingGrade].transform.position, spawnPoint[sellingGrade].transform.rotation);
        }
    }
    ```

3.  Speichern Sie Ihre Änderungen in **Visual Studio,** bevor Sie zu **Unity** zurückkehren.

4.  Überprüfen Sie im Unity-Editor, ob die **Klasse ShelfKeeper** wie folgt aussieht:

    ![Erstellen der ShelfKeeper-Klasse](images/AzureLabs-Lab7-51.png)

    > [!IMPORTANT]
    > Wenn Ihr Skript nicht über die Verweisziele (d. h. *Date (Text Mesh) )* verfügt, ziehen Sie einfach die entsprechenden Objekte aus dem **Hierarchiebereich** in die Zielfelder. Im Folgenden finden Sie eine Erläuterung, falls erforderlich:
    > 
    > 1.  Öffnen Sie **das Spawn Point-Array** innerhalb des ShelfKeeper-Komponentenskripts, indem Sie mit der linken Maustaste darauf klicken.  Ein Unterabschnitt mit dem Namen Size wird **angezeigt,** der die Größe des Arrays angibt. Geben **Sie 3** in das Textfeld neben **Größe** ein, und drücken Sie die **EINGABETASTE,** und unterhalb werden drei Slots erstellt.
    > 2. Erweitern Sie **innerhalb der** Hierarchie das **Objekt Zeitanzeige** (indem Sie mit der linken Maustaste auf den Pfeil daneben klicken). Klicken Sie als Nächstes **_innerhalb der_ _Hierarchy** auf die Hauptkamera _ , damit der **Inspektor** seine Informationen zeigt.
    > 3. Wählen Sie **im Hierarchiebereich die** **Hauptkamera aus.** Ziehen Sie  **die Datums-** und  Uhrzeitobjekte  aus dem **Hierarchiebereich** in die Textslots Datumstext und Uhrzeit innerhalb des Inspektors der Hauptkamera **in** der **ShelfKeeper-Komponente.** 
    > 4. Ziehen Sie die **Spawn Points (Spawn Points)** aus dem **Hierarchiebereich** (unterhalb des *Shelf-Objekts)* auf die **3**  Elementverweisziele unter das **Spawn** Point-Array, wie in der Abbildung dargestellt.
    > 
    >     ![Erstellen der ShelfKeeper-Klasse](images/AzureLabs-Lab7-52.png)

## <a name="chapter-9---create-the-productprediction-class"></a>Kapitel 9: Erstellen der ProductPrediction-Klasse

Die nächste Klasse, die Sie erstellen, ist die **ProductPrediction-Klasse.**

Diese Klasse ist für Folgendes verantwortlich:

-   Abfragen der **Machine Learning-Dienstinstanz** mit Angabe des aktuellen Datums und der aktuellen Uhrzeit.

-   Deserialisieren der JSON-Antwort in nutzbare Daten.

-   Interpretieren der Daten, Abrufen der drei empfohlenen Produkte.

-   Aufrufen der **Methoden der ShelfKeeper-Klasse,** um die Daten in der Szene anzuzeigen.

So erstellen Sie diese Klasse:

1.  Wechseln Sie zum **Ordner Skripts** im Project **Bereich**.

2.  Klicken Sie mit der rechten Maustaste in den Ordner **Create**  >  **C# Script (C#-Skript erstellen).** Rufen Sie das **Skript ProductPrediction auf.**

3.  Doppelklicken Sie auf das neue **Skript ProductPrediction,** um es mit Visual Studio **2017 zu öffnen.**

4.  Wenn das **Dialogfeld Dateiänderung erkannt angezeigt** wird, klicken Sie auf **_Projektmappe neu laden._*

5.  Fügen Sie am Anfang der ProductPrediction-Klasse die folgenden Namespaces hinzu:

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using System.Linq;
    using Newtonsoft.Json;
    using UnityEngine.Networking;
    using System.Runtime.Serialization;
    using System.Collections;
    ```

6.  Fügen Sie **in der ProductPrediction-Klasse** die folgenden beiden Objekte ein, die aus einer Reihe von geschachtelten Klassen bestehen. Diese Klassen werden verwendet, um den JSON-Code für den Machine Learning zu serialisieren und zu deserialisieren.

    ```csharp
        /// <summary>
        /// This object represents the Prediction request
        /// It host the day of the year and hour of the day
        /// The product must be left blank when serialising
        /// </summary>
        public class RootObject
        {
            public Inputs Inputs { get; set; }
        }

        public class Inputs
        {
            public Input1 input1 { get; set; }
        }

        public class Input1
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

    ```csharp
        /// <summary>
        /// This object containing the deserialised Prediction result
        /// It host the list of the products
        /// and the likelihood of them being sold at current date and time
        /// </summary>
        public class Prediction
        {
            public Results Results { get; set; }
        }

        public class Results
        {
            public Output1 output1;
        }

        public class Output1
        {
            public string type;
            public Value value;
        }

        public class Value
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

7.  Fügen Sie dann die folgenden Variablen über dem vorherigen Code hinzu (sodass sich der JSON-bezogene Code am Ende des Skripts befindet, unterhalb des anderen Codes und nicht so weit):

    ```csharp
        /// <summary>
        /// The 'Primary Key' from your Machine Learning Portal
        /// </summary>
        private string authKey = "-- Insert your service authentication key here --";

        /// <summary>
        /// The 'Request-Response' Service Endpoint from your Machine Learning Portal
        /// </summary>
        private string serviceEndpoint = "-- Insert your service endpoint here --";

        /// <summary>
        /// The Hour as set in Windows
        /// </summary>
        private string thisHour;

        /// <summary>
        /// The Day, as set in Windows
        /// </summary>
        private string thisDay;

        /// <summary>
        /// The Month, as set in Windows
        /// </summary>
        private string thisMonth;

        /// <summary>
        /// The Numeric Day from current Date Conversion
        /// </summary>
        private string dayOfTheYear;

        /// <summary>
        /// Dictionary for holding the first (or default) provided prediction 
        /// from the Machine Learning Experiment
        /// </summary>    
        private Dictionary<string, string> predictionDictionary;

        /// <summary>
        /// List for holding product prediction with name and scores
        /// </summary>
        private List<KeyValuePair<string, double>> keyValueList;
    ```

    > [!IMPORTANT]
    > Stellen Sie sicher, dass Sie den **Primärschlüssel und** den **Anforderung-Antwort-Endpunkt** aus dem Machine Learning-Portal in die hier angegebenen Variablen einfügen. Die folgenden Abbildungen zeigen, woher Sie den Schlüssel und endpunkt genommen hätten. 
    >  
    > ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-53-1.png)
    >
    > ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-53-2.png)

8.  Fügen Sie diesen Code in die **Start()-Methode** ein. Die **Start()-Methode** wird aufgerufen, wenn die -Klasse initialisiert wird:

    ```csharp
        void Start()
        {
            // Call to get the current date and time as set in Windows
            GetTodayDateAndTime();

            // Call to set the HOUR in the UI
            ShelfKeeper.instance.SetTime(thisHour);

            // Call to set the DATE in the UI
            ShelfKeeper.instance.SetDate(thisDay, thisMonth);

            // Run the method to Get Predication from Azure Machine Learning
            StartCoroutine(GetPrediction(thisHour, dayOfTheYear));
        }
    ```

9.  Im Folgenden finden Sie die -Methode, die das Datum und die Uhrzeit von Windows sammelt und in ein Format konvertiert, das unser Machine Learning-Experiment zum Vergleichen mit den in der Tabelle gespeicherten Daten verwenden kann.

    ```csharp
        /// <summary>
        /// Get current date and hour
        /// </summary>
        private void GetTodayDateAndTime()
        {
            // Get today date and time
            DateTime todayDate = DateTime.Now;

            // Extrapolate the HOUR
            thisHour = todayDate.Hour.ToString();

            // Extrapolate the DATE
            thisDay = todayDate.Day.ToString();
            thisMonth = todayDate.ToString("MMM");

            // Extrapolate the day of the year
            dayOfTheYear = todayDate.DayOfYear.ToString();
        }
    ```

10. Sie können **die** **Update()-Methode** löschen, da diese Klasse sie nicht verwendet.

11. Fügen Sie die folgende Methode hinzu, die das aktuelle Datum und die aktuelle Uhrzeit an den Machine Learning-Endpunkt übermittelt und eine Antwort im JSON-Format erhält.

    ```csharp
        private IEnumerator GetPrediction(string timeOfDay, string dayOfYear)
        {
            // Populate the request object 
            // Using current day of the year and hour of the day
            RootObject ro = new RootObject
            {
                Inputs = new Inputs
                {
                    input1 = new Input1
                    {
                        ColumnNames = new List<string>
                        {
                            "day",
                            "hour",
                        "product"
                        },
                        Values = new List<List<string>>()
                    }
                }
            };

            List<string> l = new List<string>
            {
                dayOfYear,
                timeOfDay,
                ""
            };

            ro.Inputs.input1.Values.Add(l);

            Debug.LogFormat("Score request built");

            // Serialize the request
            string json = JsonConvert.SerializeObject(ro);

            using (UnityWebRequest www = UnityWebRequest.Post(serviceEndpoint, "POST"))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(json);
                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + authKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.SetRequestHeader("Accept", "application/json");

                yield return www.SendWebRequest();
                string response = www.downloadHandler.text;

                // Deserialize the response
                DataContractSerializer serializer;
                serializer = new DataContractSerializer(typeof(string));
                DeserialiseJsonResponse(response);
            }
        }
    ```

12. Fügen Sie die folgende Methode hinzu, die für die Deserialisierung der JSON-Antwort und die Kommunikation des Ergebnisses der Deserialisierung an die **ShelfKeeper-Klasse zuständig** ist. Dieses Ergebnis sind die Namen der drei Artikel, die vorhergesagt werden, dass sie zum aktuellen Datum und zur aktuellen Uhrzeit am meisten verkauft werden. Fügen Sie den folgenden Code in die **ProductPrediction-Klasse** unterhalb der vorherigen Methode ein.

    ```csharp
        /// <summary>
        /// Deserialize the response received from the Machine Learning portal
        /// </summary>
        public void DeserialiseJsonResponse(string jsonResponse)
        {
            // Deserialize JSON
            Prediction prediction = JsonConvert.DeserializeObject<Prediction>(jsonResponse);
            predictionDictionary = new Dictionary<string, string>();

            for (int i = 0; i < prediction.Results.output1.value.ColumnNames.Count; i++)
            {
                if (prediction.Results.output1.value.Values[0][i] != null)
                {
                    predictionDictionary.Add(prediction.Results.output1.value.ColumnNames[i], prediction.Results.output1.value.Values[0][i]);
                }
            }

            keyValueList = new List<KeyValuePair<string, double>>();

            // Strip all non-results, by adding only items of interest to the scoreList
            for (int i = 0; i < predictionDictionary.Count; i++)
            {
                KeyValuePair<string, string> pair = predictionDictionary.ElementAt(i);
                if (pair.Key.StartsWith("Scored Probabilities"))
                {
                    // Parse string as double then simplify the string key so to only have the item name
                    double scorefloat = 0f;
                    double.TryParse(pair.Value, out scorefloat);
                    string simplifiedName =
                        pair.Key.Replace("\"", "").Replace("Scored Probabilities for Class", "").Trim();
                    keyValueList.Add(new KeyValuePair<string, double>(simplifiedName, scorefloat));
                }
            }

            // Sort Predictions (results will be lowest to highest)
            keyValueList.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Spawn the top three items, from the keyValueList, which we have sorted
            for (int i = 0; i < 3; i++)
            {
                ShelfKeeper.instance.SpawnProduct(keyValueList[i].Key, i);
            }

            // Clear lists in case of reuse
            keyValueList.Clear();
            predictionDictionary.Clear();
        }
    ```

13. Speichern **Visual Studio,** und lehnen Sie Unity **ab.**

14. Ziehen Sie **das Klassenskript ProductPrediction** aus dem **Ordner Skript** auf das **Objekt Hauptkamera.**

15. Speichern Sie Die Szene und das Projekt **Datei**  >  **speichern Szene/Datei**  >  **speichern Project**.

## <a name="chapter-10---build-the-uwp-solution"></a>Kapitel 10: Erstellen der UWP-Lösung

Jetzt ist es an der Zeit, Ihr Projekt als UWP-Projektmappe zu erstellen, damit es als eigenständige Anwendung ausgeführt werden kann.

So erstellen Sie:

1.  Speichern Sie die aktuelle Szene, indem Sie auf **File**  >  **Save Scenes klicken.**

2.  Wechseln Sie **zu**  >  **Datei Einstellungen**

3.  Aktivieren Sie das Kontrollkästchen **Unity C#-Projekte** (dies ist wichtig, da Sie die Klassen bearbeiten können, nachdem der Build abgeschlossen ist).

4.  Klicken Sie auf **Add Open Scenes (Offene Szenen hinzufügen).**

5.  Klicken Sie auf **Erstellen**.

    ![Erstellen der UWP-Lösung](images/AzureLabs-Lab7-54.png)

6.  Sie werden aufgefordert, den Ordner auszuwählen, in dem Sie die Projektmappe erstellen möchten.

7.  Erstellen Sie **einen ORDNER BUILDS,** und erstellen Sie in diesem Ordner einen weiteren Ordner mit einem geeigneten Namen Ihrer Wahl.

8.  Klicken Sie auf Ihren neuen Ordner und dann **auf Ordner auswählen,** um den Build an diesem Speicherort zu starten.

    ![Erstellen der UWP-Lösung](images/AzureLabs-Lab7-55.png)

    ![Erstellen der UWP-Lösung](images/AzureLabs-Lab7-56.png)

9.  Sobald Unity die Erstellung abgeschlossen hat (dies kann einige Zeit dauern), wird ein **Datei-Explorer-Fenster** am Speicherort Ihres Buildfensters geöffnet (überprüfen Sie Ihre Taskleiste, da sie möglicherweise nicht immer über Ihren Fenstern angezeigt wird, sondern Sie über das Addition eines neuen Fensters benachrichtigt).

## <a name="chapter-11---deploy-your-application"></a>Kapitel 11: Bereitstellen Ihrer Anwendung

So stellen Sie Ihre Anwendung

1.  Navigieren Sie zu Ihrem neuen Unity-Build (dem **Ordner App),** und öffnen Sie die Projektmappendatei mit **Visual Studio.**

2.  Wenn Visual Studio geöffnet ist, müssen Sie NuGet-Pakete wiederherstellen. Dies kann durch Klicken mit der rechten Maustaste auf ihre MachineLearningLab_Build-Projektmappe über den Projektmappen-Explorer (rechts von Visual Studio) erfolgen, und klicken Sie dann auf NuGet-Pakete wiederherstellen:

    ![Hinzufügen von NuGet-Paketen](images/AzureLabs-Lab7-57.png)

3.  Wählen Sie in der Projektmappenkonfiguration **Debuggen aus.**

4.  Wählen Sie auf der Projektmappenplattform **x86**, **Lokaler Computer aus.** 

    > Für die Microsoft HoloLens ist es möglicherweise einfacher, dies auf *Remotecomputer* zu setzen, damit Sie nicht an Ihren Computer geentert werden. Sie müssen jedoch auch die folgenden Schritte unternehmen:
    > - Kennen Sie **die IP-Adresse** Ihres HoloLens, die sie im Einstellungen > Network & Internet > Wi-Fi > *Finden.* IPv4 ist die Adresse, die Sie verwenden sollten. 
    > - Stellen Sie **sicher, dass der Entwicklermodus** **aktiviert ist.** finden Sie *Einstellungen > Update & Security > Für Entwickler.*

    ![Hinzufügen von NuGet-Paketen](images/AzureLabs-Lab7-58.png)

5.  Wechseln Sie zum **Menü Erstellen,** und klicken Sie **auf Projektmappe bereitstellen,** um die Anwendung auf Ihren PC zu laden.

6.  Ihre App sollte nun in der Liste der installierten Apps angezeigt werden, die zum Start bereit sind.

Wenn Sie die Mixed Reality-Anwendung ausführen, sehen Sie die Bank, die in Ihrer Unity-Szene eingerichtet wurde. Bei der Initialisierung werden die daten abgerufen, die Sie in Azure eingerichtet haben. Die Daten werden in Ihrer Anwendung deserialisiert, und die drei wichtigsten Ergebnisse für Ihr aktuelles Datum und Ihre aktuelle Uhrzeit werden visuell bereitgestellt, als drei Modelle auf der Bank.


## <a name="your-finished-machine-learning-application"></a>Ihre fertige Machine Learning Anwendung
 
Herzlichen Glückwunsch! Sie haben eine Mixed Reality-App erstellt, die die Azure Machine Learning nutzt, um Datenvorhersagen zu treffen und in Ihrer Szene anzuzeigen.

![Hinzufügen von NuGet-Paketen](images/AzureLabs-Lab7-0.png)

## <a name="exercise"></a>Übung

**Übung 1**

Experimentieren Sie mit der Sortierreihenfolge Ihrer Anwendung, und stellen Sie sicher, dass die drei unten genannten Vorhersagen im Regal angezeigt werden, da diese Daten möglicherweise ebenfalls nützlich sind.

**Übung 2**

Mithilfe **von Azure-Tabellen** wird eine neue Tabelle mit Wetterinformationen aufgefüllt, und mit den Daten wird ein neues Experiment erstellt.