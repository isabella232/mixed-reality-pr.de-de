---
title: Willkommen beim Mixed Reality-Featuretool
description: Lernen Sie die Grundlagen des MR-Featuretools für die HoloLens- und VR-Entwicklung kennen.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: Aktuell, Tools, Erste Schritte, Grundlagen, Unity, Visual Studio, Toolkit, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Installation, Windows, HoloLens, Emulator, Unreal, OpenXR
ms.openlocfilehash: b9d54edb251cfe22d4f5fbea6fa8c923f6ff2d69
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2021
ms.locfileid: "99243956"
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

Nachdem Sie Ihre Umgebung eingerichtet haben:

* Laden Sie die neueste Version des Mixed Reality-Featuretools aus dem [Microsoft Download Center](https://aka.ms/MRFeatureTool) herunter.
* Wenn der Download abgeschlossen ist, entpacken Sie die Datei, und speichern Sie sie auf Ihrem Desktop.
    * Es empfiehlt sich, für den schnelleren Zugriff eine Verknüpfung zur ausführbaren Datei zu erstellen

## <a name="1-getting-started"></a>1. Erste Schritte

Starten Sie das Mixed Reality-Featuretool aus der ausführbaren Datei, das beim ersten Start die Startseite anzeigt:

![Erste Schritte](images/FeatureToolStart.png)

Auf der Startseite können Sie Folgendes ausführen:

* [Konfigurieren](configuring-feature-tool.md) der Tooleinstellungen mithilfe der Schaltfläche mit dem **Zahnradsymbol**
* Verwenden der Schaltfläche mit dem **Fragezeichen** zum Starten des Webbrowsers und Anzeigen unserer Dokumentation
* Auswähle von **Start**, um mit dem Ermitteln von Featurepaketen zu beginnen

## <a name="2-discovering-and-acquiring-feature-packages"></a>2. Ermitteln und Erwerben von Featurepaketen

Der Katalog der Featurepakete wird abgerufen, sobald Sie auf „Start“ klicken. Die Features sind zur besseren Orientierung nach Kategorien gruppiert. Beispielsweise weist die **Mixed Reality-Toolkit**-Kategorie mehrere Features auf, unter denen Sie wählen können:

![Ermittlung und Erwerb](images/FeatureToolDiscovery.png)

Sobald Sie Ihre Wahl getroffen haben, wählen Sie **Get features** (Features abrufen) aus, um alle benötigten Pakete aus dem Katalog abzurufen. Weitere Informationen finden Sie unter [discovering and acquiring features](discovering-features.md) (Ermitteln und Erwerben von Features).

## <a name="3-importing-feature-packages"></a>3. Importieren von Featurepaketen

Nach dem Erwerb wird der gesamte Satz von Paketen zusammen mit einer Liste der erforderlichen Abhängigkeiten angezeigt. Wenn Sie die Auswahl eines Features oder Pakets ändern müssen, ist dies der richtige Zeitpunkt:

![Importieren von Paketen](images/FeatureToolImport.png)

Wir empfehlen dringend, die Schaltfläche **Validate** (Überprüfen) zu verwenden, um sicherzustellen, dass das Unity-Projekt die ausgewählten Features erfolgreich importieren kann. Nach der Überprüfung wird ein Popupdialogfeld mit einer Erfolgsmeldung oder einer Liste der identifizierten Probleme angezeigt.

Ferner müssen Sie vor dem Importieren noch den Speicherort des Unity-Zielprojekts festlegen. Verwenden Sie die Schaltfläche mit dem **Auslassungszeichen** auf der linken Seite des Projektpfadfelds zum Durchsuchen. Wenn Sie die Navigation in Ihrem Dateisystem abgeschlossen haben, öffnen Sie den Ordner, der Ihr Unity-Zielprojekt enthält.

> [!NOTE]
> Das Dialogfeld, das angezeigt wird, wenn Sie das Dateisystem nach dem Unity-Projektordner durchsuchen, enthält '_' als den Dateinamen. Es muss ein Wert für den Dateinamen vorhanden sein, um die Auswahl des Ordners zu ermöglichen.

Wählen Sie **Importieren** aus, um fortzufahren.

> [!NOTE]
> Sollten nach dem Klicken auf die Schaltfläche **Import** noch Probleme bestehen, wird eine einfache Meldung angezeigt. Es wird empfohlen, auf „Nein“ zu klicken und die Schaltfläche **Validate** (Überprüfen) zu verwenden, um die Probleme anzuzeigen und zu beheben.

Weitere Informationen finden Sie unter [Importieren von Features](importing-features.md).

## <a name="4-reviewing-and-approving-project-changes"></a>4. Überprüfen und Genehmigen von Projektänderungen

Der letzte Schritt besteht im Überprüfen und Genehmigen der vorgeschlagenen Änderungen an den Manifest- und Projektdateien:

* Die vorgeschlagenen Änderungen am Manifest werden auf der linken Seite angezeigt
* Die Dateien, die dem Projekt hinzugefügt werden sollen, werden auf der rechten Seite angezeigt
* Mit der Schaltfläche **Compare** (Vergleichen) können Sie das aktuelle Manifest und die vorgeschlagenen Änderungen nebeneinander anzeigen

![Authorization](images/FeatureToolApprovalRequest.png)

Weitere Informationen finden Sie unter [Überprüfen und Genehmigen von Projektänderungen](reviewing-changes.md).

## <a name="5-project-updated"></a>5. Projekt aktualisiert

Wenn die vorgeschlagenen Änderungen genehmigt werden, wird Ihr Unity-Zielprojekt aktualisiert, um auf die ausgewählten Mixed Reality-Features zu verweisen:

![Projekt aktualisiert](images/FeatureToolProjectUpdated.png)

Der Ordner **Packages** (Pakete) des Unity-Projekts enthält jetzt einen Unterordner **MixedReality** mit den Dateien der Featurepakete, und das Manifest enthält die entsprechenden Verweise.

Kehren Sie zu Unity zurück, warten Sie auf das Laden der neu ausgewählten Features, und beginnen Sie mit dem Erstellen!

## <a name="see-also"></a>Siehe auch

- [Konfigurieren des Featuretools](configuring-feature-tool.md)
- [Ermittlung und Erwerb](discovering-features.md)
- [Anzeigen von Details zu Featurepaketen](viewing-package-details.md)
- [Importieren ausgewählter Pakete](importing-features.md)
- [Überprüfen und Genehmigen von Projektänderungen](reviewing-changes.md)
