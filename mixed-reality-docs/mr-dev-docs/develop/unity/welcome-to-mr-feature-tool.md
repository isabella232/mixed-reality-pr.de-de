---
title: Willkommen beim Mixed Reality-Featuretool
description: Lernen Sie die Grundlagen des MR-Featuretools für die HoloLens- und VR-Entwicklung kennen.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: Aktuell, Tools, Erste Schritte, Grundlagen, Unity, Visual Studio, Toolkit, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Installation, Windows, HoloLens, Emulator, Unreal, OpenXR
ms.openlocfilehash: 4e822f2dda2a314ce06bc394a4d92b1aa6953af3
ms.sourcegitcommit: 943489923c69c3a28bc152f1cb516dcdcea2880a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2021
ms.locfileid: "111772413"
---
# <a name="welcome-to-the-mixed-reality-feature-tool"></a>Willkommen beim Mixed Reality-Featuretool

![Mixed Reality-Featuretool-Bannerbild](images/feature-tool-banner.png)

> [!IMPORTANT]
> Das Mixed Reality-Featuretool ist zurzeit nur für Unity verfügbar. Wenn Sie in Unreal entwickeln, finden Sie weitere Informationen in der Dokumentation zur [Toolinstallation](../install-the-tools.md).

Das Mixed Reality-Featuretool ist eine neue Möglichkeit für Entwickler, Mixed Reality-Featurepakete in Unity-Projekten zu ermitteln, zu aktualisieren und hinzuzufügen. Sie können Pakete vor dem Importieren nach Name oder Kategorie durchsuchen, ihre Abhängigkeiten anzeigen und sogar Änderungsvorschläge für Ihre Projektmanifestdatei anzeigen. Für den Fall dass Sie noch nie mit einer Manifestdatei gearbeitet haben: Es handelt sich um eine JSON-Datei, die alle Ihre Projektpakete enthält. Nachdem Sie die gewünschten Pakete überprüft haben, lädt das Mixed Reality-Featuretool sie in das Projekt Ihrer Wahl herunter.

## <a name="system-requirements"></a>Systemanforderungen

Damit Sie das Mixed Reality-Featuretool ausführen können, benötigen Sie Folgendes:

* [.NET 5.0 Runtime](https://dotnet.microsoft.com/download/dotnet/5.0)
* [Windows 10](https://www.microsoft.com/software-download/windows10ISO)

> [!NOTE]
> Das Mixed Reality-Featuretool kann zurzeit nur unter Windows ausgeführt werden, MacOS-Unterstützung wird aber in Kürze verfügbar sein.

## <a name="download"></a>Download

Nachdem Sie Ihre Umgebung eingerichtet haben:

* [Laden Sie die neueste Version des Mixed Reality-Featuretools](https://aka.ms/MRFeatureTool) aus dem Microsoft Download Center herunter.
* Wenn der Download abgeschlossen ist, entpacken Sie die Datei, und speichern Sie sie auf Ihrem Desktop.
    * Es empfiehlt sich, für den schnelleren Zugriff eine Verknüpfung zur ausführbaren Datei zu erstellen

> [!NOTE]
> Wenn Sie noch keine Erfahrung mit der Verwendung des Unity-Paket-Managers haben, befolgen Sie unsere [UPM-Anweisungen](/windows/mixed-reality/mrtk-unity/configuration/usingupm#managing-mixed-reality-features-with-the-unity-package-manager).

## <a name="changes-in-this-release"></a>Änderungen in diesem Release

Version 1.0.2103 Beta enthält die folgenden Fehlerkorrekturen:

* Verbesserungen bei der Erkennung von Downloadfehlern.
* Aktualisierungen an der Art, in der Manifeste geschrieben werden, um Fehler bei der korrekten Aktualisierung zu vermeiden.
* Die Verwendung von Escapezeichen wurde aus Dateipfaden im Projektmanifest entfernt.

Dieses Release wurde um die folgenden Features erweitert:

* Der Featurekatalog wird jetzt zwischengespeichert. Um nach neuen Features und Updates zu suchen, verwenden Sie die Schaltfläche „Aktualisieren“ in „Discovery“ (Ermittlung).
* Die Projektauswahl wurde aus dem Importschritt vor die Ermittlung verschoben.
* Verfügbare Pakete werden nach der angegebenen Unity-Version des Projekts gefiltert.
* In der Ermittlungsansicht werden jetzt die aktuell installierten Pakete angezeigt.

## <a name="1-getting-started"></a>1. Erste Schritte

Starten Sie das Mixed Reality-Featuretool aus der ausführbaren Datei, das beim ersten Start die Startseite anzeigt:

![Erste Schritte](images/FeatureToolStart.png)

Auf der Startseite können Sie Folgendes ausführen:

* [Konfigurieren](configuring-feature-tool.md) der Tooleinstellungen mithilfe der Schaltfläche mit dem **Zahnradsymbol**
* Verwenden der Schaltfläche mit dem **Fragezeichen** zum Starten des Webbrowsers und Anzeigen unserer Dokumentation
* Auswähle von **Start**, um mit dem Ermitteln von Featurepaketen zu beginnen

## <a name="2-selecting-your-unity-project"></a>2. Auswählen Ihres Unity-Projekts

Um sicherzustellen, dass alle ermittelten Features in der Unity-Version Ihres Projekts unterstützt werden, besteht der erste Schritt darin, das Mixed Reality-Featuretool mithilfe der Schaltfläche mit den **Auslassungszeichen** (rechts neben dem Feld „Projektpfad“) auf Ihr Projekt zu verweisen.

![Auswählen des Unity-Projekts](images/FeatureToolSelectUnityProject.png)

> [!NOTE]
> Das Dialogfeld, das angezeigt wird, wenn Sie das Dateisystem nach dem Unity-Projektordner durchsuchen, enthält '_' als den Dateinamen. Es muss ein Wert für den Dateinamen vorhanden sein, um die Auswahl des Ordners zu ermöglichen.

Wenn Sie den Ordner Ihres Projekts gefunden haben, klicken Sie auf die Schaltfläche „Öffnen“, um zum Mixed Reality-Featuretool zurückzukehren.

> [!IMPORTANT]
> Das Mixed Reality-Featuretool führt eine Überprüfung durch, um sicherzustellen, dass die Weiterleitung an einen Unity-Projektordner erfolgt. Der Ordner muss die Ordner `Assets`, `Packages` und `Project Settings` enthalten.

## <a name="3-discovering-and-acquiring-feature-packages"></a>3. Ermitteln und Erwerben von Featurepaketen

> [!NOTE]
> Version 1.0.2103 Beta speichert jetzt den Inhalt des Featurekatalogs zwischen, wenn auf den Server zugegriffen wird. Diese Änderung ermöglicht den schnellen Zugriff auf verfügbare Features auf Kosten der Anzeige der absolut neuesten Daten. Verwenden Sie zum Aktualisieren des Katalogs die Schaltfläche **Aktualisieren**.

Die Features sind zur besseren Orientierung nach Kategorien gruppiert. Beispielsweise weist die **Mixed Reality-Toolkit**-Kategorie mehrere Features auf, unter denen Sie wählen können:

![Ermittlung und Erwerb](images/FeatureToolDiscovery.png)

Wenn das Mixed Reality-Featuretool zuvor importierte Features erkennt, zeigt es für jedes eine Benachrichtigung an.

![Benachrichtigung über importiertes Features](images/feature-tool-imported-note.png)


Sobald Sie Ihre Wahl getroffen haben, wählen Sie **Get features** (Features abrufen) aus, um alle benötigten Pakete aus dem Katalog abzurufen. Weitere Informationen finden Sie unter [discovering and acquiring features](discovering-features.md) (Ermitteln und Erwerben von Features).

## <a name="4-importing-feature-packages"></a>4. Importieren von Featurepaketen

Nach dem Erwerb wird der gesamte Satz von Paketen zusammen mit einer Liste der erforderlichen Abhängigkeiten angezeigt. Wenn Sie die Auswahl eines Features oder Pakets ändern müssen, ist dies der richtige Zeitpunkt:

![Importieren von Paketen](images/FeatureToolImport.png)

Wir empfehlen dringend, die Schaltfläche **Validate** (Überprüfen) zu verwenden, um sicherzustellen, dass das Unity-Projekt die ausgewählten Features erfolgreich importieren kann. Nach der Überprüfung wird ein Popupdialogfeld mit einer Erfolgsmeldung oder einer Liste der identifizierten Probleme angezeigt.

Wählen Sie **Importieren** aus, um fortzufahren.

> [!NOTE]
> Sollten nach dem Klicken auf die Schaltfläche **Import** noch Probleme bestehen, wird eine einfache Meldung angezeigt. Es wird empfohlen, auf „Nein“ zu klicken und die Schaltfläche **Validate** (Überprüfen) zu verwenden, um die Probleme anzuzeigen und zu beheben.

Weitere Informationen finden Sie unter [Importieren von Features](importing-features.md).

## <a name="5-reviewing-and-approving-project-changes"></a>5. Überprüfen und Genehmigen von Projektänderungen

Der letzte Schritt besteht im Überprüfen und Genehmigen der vorgeschlagenen Änderungen an den Manifest- und Projektdateien:

* Die vorgeschlagenen Änderungen am Manifest werden auf der linken Seite angezeigt
* Die Dateien, die dem Projekt hinzugefügt werden sollen, werden auf der rechten Seite angezeigt
* Mit der Schaltfläche **Compare** (Vergleichen) können Sie das aktuelle Manifest und die vorgeschlagenen Änderungen nebeneinander anzeigen

![Authorization](images/FeatureToolApprovalRequest.png)

Weitere Informationen finden Sie unter [Überprüfen und Genehmigen von Projektänderungen](reviewing-changes.md).

## <a name="6-project-updated"></a>6. Projekt aktualisiert

Wenn die vorgeschlagenen Änderungen genehmigt wurden, wird Ihr Unity-Zielprojekt so aktualisiert, dass es auf die ausgewählten Mixed Reality-Features verweist.

![Projekt aktualisiert](images/FeatureToolProjectUpdated.png)

Der Ordner **Packages** (Pakete) des Unity-Projekts enthält jetzt einen Unterordner **MixedReality** mit den Dateien der Featurepakete, und das Manifest enthält die entsprechenden Verweise.

Kehren Sie zu Unity zurück, warten Sie auf das Laden der neu ausgewählten Features, und beginnen Sie mit dem Erstellen!

## <a name="see-also"></a>Siehe auch

- [Konfigurieren des Featuretools](configuring-feature-tool.md)
- [Ermittlung und Erwerb](discovering-features.md)
- [Anzeigen von Details zu Featurepaketen](viewing-package-details.md)
- [Importieren ausgewählter Pakete](importing-features.md)
- [Überprüfen und Genehmigen von Projektänderungen](reviewing-changes.md)