---
title: Anleitungen für Mitwirkende
description: Erfahren Sie mehr über die grundlegenden Schritte und Richtlinien für die Mitwirkung am Windows Mixed Reality-Guide. Wir freuen uns über Ihr Feedback, Ihre Bearbeitungen, Ergänzungen und Hilfe.
author: mattwojo
ms.author: mattwoj
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Feedback, Feedback-Hub, Fehler
appliesto:
- Windows 10
ms.openlocfilehash: fd47e806a1ac14d85f503d7d4f799b232cbd3e102c3d4494d5704082bf0e08ea
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188170"
---
# <a name="contributing-to-the-mixed-reality-enthusiast-guide"></a>Mitwirken am Mixed Reality-Guide

Vielen Dank für Ihr Interesse am Leitfaden für Sehenswürdigkeiten. Wir freuen uns über Ihr Feedback, Ihre Bearbeitungen, Ergänzungen und Hilfe bei der Verbesserung unserer Dokumentation. Auf dieser Seite werden die grundlegenden Schritte und Richtlinien für Beiträge behandelt.

> [!IMPORTANT]
> Für alle Repositorys, die in „docs.microsoft.com“ veröffentlichen, gilt der [Microsoft Open Source-Verhaltenskodex](https://opensource.microsoft.com/codeofconduct/). Weitere Informationen finden Sie in den [häufig gestellten Fragen zum Verhaltenskodex](https://opensource.microsoft.com/codeofconduct/faq/). Sie können sich mit Ihren Fragen oder Kommentaren auch an [opencode@microsoft.com](mailto:opencode@microsoft.com) wenden.<br>
>
> Für kleinere Korrekturen oder Klarstellungen zu Dokumentation und Codebeispielen in öffentlichen Repositorys gelten die [Nutzungsbestimmungen zu docs.microsoft.com](/legal/termsofuse). Neue oder signifikante Änderungen haben einen Kommentar im Pull Request zur Folge, in dem wir Sie bitten, online eine Lizenzvereinbarung für Beiträge (Contribution License Agreement, CLA) zu übermitteln. Dies gilt, wenn Sie kein Mitarbeiter von Microsoft sind. Sie müssen das Onlineformular ausfüllen, damit wir Ihren Pull Request annehmen können.

## <a name="before-you-start"></a>Vorbereitung

Wenn Sie noch nicht über ein Konto verfügen, müssen Sie [ein GitHub Konto erstellen.](https://github.com/join)

>[!NOTE]
>Wenn Sie Microsoft-Mitarbeiter sind, verknüpfen Sie Ihr GitHub-Konto mit Ihrem Microsoft-Alias im [Microsoft Open Source-Portal.](https://repos.opensource.microsoft.com/) Treten Sie den Organisationen **"Microsoft"** und **"MicrosoftDocs"** bei.

Beim Einrichten Ihres GitHub-Kontos empfehlen wir auch die folgenden Sicherheitsvorkehrungen:
- Erstellen Sie ein [sicheres Kennwort für Ihr GitHub-Konto.](https://github.com/settings/admin)
- Aktivieren Sie [die zweistufige Authentifizierung.](https://github.com/settings/two_factor_authentication/configure)
- Speichern Sie Ihre [Wiederherstellungscodes](https://github.com/settings/auth/recovery-codes) an einem sicheren Ort.
- Aktualisieren Sie die Einstellungen ihres [öffentlichen Profils.](https://github.com/settings/profile)
   - Legen Sie Ihren Namen fest, und legen Sie ihre *öffentliche E-Mail-Adresse* auf *Meine E-Mail-Adresse nicht anzeigen* fest.
   - Es wird empfohlen, ein Profilbild hochzuladen, da eine Miniaturansicht auf Dokumentationsseiten angezeigt wird, zu der sie beitragen.
- Wenn Sie die Befehlszeile verwenden möchten, sollten Sie [git Anmeldeinformationsverwaltung für Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest)einrichten. Auf diese Weise müssen Sie nicht jedes Mal Ihr Kennwort eingeben, wenn Sie einen Beitrag leisten.

Das Veröffentlichungssystem ist an GitHub gebunden, daher sind diese Schritte wichtig. Sie werden entweder als Autor oder Mitwirkender für jeden Artikel mit Ihrem GitHub-Alias aufgeführt.

## <a name="how-to-make-a-change"></a>Vornehmen einer Änderung

| Führe diese Schritte aus, um eine Änderung an den Dokumenten vorzuschlagen: | Screenshots |
| :------------------- | :--------: |
| 1. Wenn Sie eine Docs.microsoft.com Seite anzeigen, klicken Sie oben rechts auf der Seite auf die Schaltfläche **Bearbeiten.**  Du wirst zur entsprechenden Markdown-Quelldatei im [GitHub-Repository](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide) geleitet. | ![Schaltfläche "Bearbeiten"](images/edit_button.jpg) |
| 2. Wenn Sie noch nicht über ein GitHub Konto verfügen, klicken Sie oben rechts auf **Registrieren,** und erstellen Sie ein neues Konto. | ![Schaltfläche "Registrierung"](images/signup-for-github-button.png)|
| 3. Klicken Sie auf der entsprechenden GitHub Seite, die geöffnet wird, auf Bearbeiten (Stiftsymbol). | ![Stiftschaltfläche](images/pencil_button.jpg)|
| 4. Aktualisieren Sie im Bereich Datei bearbeiten [die Metadaten der Dateien,](#updating-metadata) und ändern Sie den Inhalt mithilfe der Markdownsprache. ([Schreiben von Markdown.](https://help.github.com/articles/basic-writing-and-formatting-syntax/))| ![Datei bearbeiten](images/edit-in-github.png)|
| 5. Klicken Sie auf Vorschau der Änderungen, um zu überprüfen, ob die Formatierung wie erwartet aussieht. | ![Vorschau der Änderungen](images/edit-in-github.png)|
| 6. Wenn Sie fertig sind, scrollen Sie zum unteren Rand der Seite, und klicken Sie auf "Dateiänderung vorschlagen". Daraufhin wird die Seite "Änderungen vergleichen" angezeigt, auf der Sie Ihre Änderungen überprüfen können. Klicken Sie dann auf die Schaltfläche "Pull Request erstellen", um Ihre Änderungen zu übermitteln. An diesem Punkt sind Sie fertig! | ![Vorschlagen einer Änderung](images/propose.jpg)|

Nachdem Sie Änderungen (über einen Pull Request) übermittelt haben, werden sie von einem Mitglied des Dokumentationsteams überprüft. Wenn Ihre Anforderung akzeptiert wird, werden Updates in [https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide](/windows/mixed-reality/enthusiast-guide) veröffentlicht.

*Nur für die interne Überprüfung werden Ihre Änderungen unter [https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide](https://review.docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/?branch=master) angezeigt.

### <a name="updating-metadata"></a>Aktualisieren von Metadaten

Aktualisieren Sie die Metadaten am Anfang jedes Artikels:
   * **title:** Seitentitel, der auf der Browserregisterkarte angezeigt wird, wenn der Artikel angezeigt wird. Seitentitel werden für SEO und Indizierung verwendet. Ändern Sie den Titel daher nur, wenn dies erforderlich ist (obwohl dies weniger wichtig ist, bevor die Dokumentation veröffentlicht wird).
   * **description:** Schreiben Sie eine kurze Beschreibung der Inhalte des Artikels, die SEO und Discovery verstärken.
   * **author:** Wenn Sie der primäre Besitzer der Seite sind, fügen Sie hier Ihren GitHub Alias hinzu.
   * **ms.author:** Wenn Sie der primäre Besitzer der Seite sind, fügen Sie hier Ihren Microsoft-Alias hinzu (Sie benötigen nicht @microsoft.com , nur den Alias).
   * **ms.date:** Aktualisieren Sie das Datum, wenn Sie der Seite Hauptinhalte hinzufügen, jedoch nicht für Korrekturen wie Erläuterungen, Formatierung, Grammatik oder Rechtschreibung.
   * **keywords:** Schlüsselwörter helfen bei der SUCHMASCHINENOPTIMIERUNG (Suchmaschinenoptimierung). Fügen Sie Schlüsselwörter hinzu, die durch ein Komma und ein Leerzeichen getrennt sind, die für Ihren Artikel spezifisch sind, aber keine Interpunktion nach dem letzten Schlüsselwort in Der Liste. Sie müssen keine globalen Schlüsselwörter hinzufügen, die für alle Artikel gelten, da diese an anderer Stelle verwaltet werden. 

### <a name="renaming-or-deleting-an-existing-article"></a>Umbenennen oder Löschen eines vorhandenen Artikels

Wenn Ihre Änderung einen vorhandenen Artikel umbenennen oder löschen wird, müssen Sie eine Umleitung hinzufügen. Auf diese Weise werden alle Benutzer, die einen Link zum vorhandenen Artikel haben, immer noch am richtigen Ort sein. Umleitungen werden vom .openpublishing.redirection.jsin der Datei im Stammverzeichnis des Repositorys verwaltet.

Um eine Umleitung zu .openpublishing.redirection.jshinzuzufügen, fügen Sie dem Array einen Eintrag `redirections` hinzu:

```json
{
    "redirections": [
        {
            "source_path": "mixed-reality-docs/enthusiast-guide/old-article.md",
            "redirect_url": "new-article#section-about-old-topic",
            "redirect_document_id": false
        },
```

- `source_path`ist der relative Repositorypfad zum alten Artikel, den Sie entfernen. Stellen Sie sicher, dass der Pfad mit beginnt `mixed-reality-docs/enthusiast-guide` und mit `.md` endet.
- ist `redirect_url` die relative öffentliche URL aus dem alten Artikel zum neuen Artikel. Stellen Sie sicher, dass diese URL **nicht** `mixed-reality-docs/enthusiast-guide` oder `.md` enthält, da sie auf die öffentliche URL und nicht auf den Repositorypfad verweist. Das Verknüpfen mit einem Abschnitt innerhalb des neuen Artikels mit `#section` ist zulässig. Sie können hier bei Bedarf auch einen absoluten Pfad zu einer anderen Website verwenden.
- `redirect_document_id` gibt an, ob Sie die Dokument-ID aus der vorherigen Datei beibehalten möchten. Der Standardwert lautet `false`. Verwenden `true` Sie , wenn Sie den `ms.documentid` Attributwert aus dem umgeleiteten Artikel beibehalten möchten. Wenn Sie die Dokument-ID beibehalten, werden Daten wie Seitenaufrufe und Rangfolgen an den Zielartikel übertragen. Legen Sie das so fest, wenn die Umleitung in erster Linie eine Umbenennung und kein Zeiger auf einen anderen Artikel ist, der nur einen Teil desselben Inhalts abdeckt.

Wenn Sie eine Umleitung hinzufügen, löschen Sie auch die alte Datei.

### <a name="creating-a-new-article"></a>Erstellen eines neuen Artikels

Verwenden Sie den folgenden Workflow, um neue Artikel im Dokumentations-Repository über GitHub in einem Webbrowser zu *erstellen:*

1. Erstellen Sie eine Verzweigung des Branchs "master" von MicrosoftDocs/mixed-reality/tree/docs/fan-guide (mithilfe der **Verzweigungsschaltfläche** oben rechts).

   ![Fork der Masterverzweigung.](images/forkbranch.png)
2. Wählen Sie im Ordner "mixed-reality/fan-guide" oben rechts die Option **Neue Datei erstellen** aus.
3. Erstellen Sie einen Seitennamen für den Artikel (verwenden Sie Bindestriche anstelle von Leerzeichen und keine Interpunktion oder Apostrophe), und fügen Sie ".md" an.

   ![Benennen Sie Ihre neue Seite.](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   >Stellen Sie sicher, dass Sie den neuen Artikel im Ordner "mixed-reality-docs/fan" erstellen. Sie können dies bestätigen, indem Sie in der neuen Dateinamenzeile nach "/mixed-reality-docs/fan-guide" suchen.

4. Fügen Sie oben auf der neuen Seite den folgenden Metadatenblock hinzu:

   ```md
   ---
   title:
   description:
   author:
   ms.author:
   ms.date:
   ms.topic: article
   keywords:
   ---
   ```

5. Füllen Sie die relevanten Metadatenfelder gemäß den Anweisungen im [Obigen Abschnitt aus.](#updating-metadata)
6. Schreiben von Artikelinhalten mit [markdown-Grundlagen.](#markdown-basics)
7. Fügen Sie am Ende des Artikels einen `## See also` Abschnitt mit Links zu anderen relevanten Artikeln hinzu.
8. Wenn Sie fertig sind, wählen Sie **Commit new file (Neue Datei committen)** aus.
9. Wählen Sie **Neuer Pull Request** aus, und führen Sie den Branch "master" Ihres Forks in MicrosoftDocs/mixed-reality/fan-guide 'master' zusammen (stellen Sie sicher, dass der Pfeil den richtigen Weg zeigt).

   ![Erstellen eines Pull Requests aus Ihrer Verzweigung in MicrosoftDocs/mixed-reality/fan-guide](images/pr_to_master.PNG)

## <a name="working-with-branches"></a>Arbeiten mit Verzweigungen

Das [Mixed Reality-Handbuch für Sports GitHub-Repository](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide) verwendet zwei übergeordnete Hauptbranches: [Master,](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/tree/master)dieser Inhalt kann auf der [Stagingwebsite](https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide)und [Live](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/tree/live)auf Inhalte überprüft werden, die auf der [Livewebsite](/windows/mixed-reality/enthusiast-guide)angezeigt werden.

Wenn Sie Beiträge leisten, übermitteln Sie Ihren  Pull Request (PR) an den Master-Branch. Diese Verzweigung kann auf der Stagingsite angezeigt werden und sollte nur Beiträge enthalten, die für die Liveveröffentlichung bereit sind. Sie können auch einen Branch mit Ihrem eigenen eindeutigen Branchnamen erstellen und übermitteln, der auf der Stagingwebsite ausgewählt und angezeigt werden kann. (Der **Live-Branch** ist nur für die Verwendung durch inhaltsadministratoren zulässig.)

## <a name="markdown-basics"></a>Grundlegendes zu Markdown

In den folgenden Ressourcen erfahren Sie, wie Sie die Dokumentation mithilfe der Markdownsprache bearbeiten:

- [Markdown-Grundlagen](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [Markdown-at-a-Glance-Referenzposter](images/MarkdownPoster.pdf)
- [Zusätzliche Ressourcen zum Schreiben von Markdown für docs.microsoft.com](/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a>Hinzufügen von Tabellen

Aufgrund der Art und Weise, wie Tabellen formatiert docs.microsoft.com, haben sie keine Rahmen oder benutzerdefinierten Stile, auch wenn Sie INLINE-CSS ausprobieren. Es scheint für einen kurzen Zeitraum zu funktionieren, aber schließlich entfernt die Plattform den Stil aus der Tabelle. Planen Sie also voraus, und halten Sie Ihre Tabellen einfach. [Hier ist eine Website, die Markdowntabellen einfach macht.](https://www.tablesgenerator.com/markdown_tables)

Die [Docs Markdown-Erweiterung für Visual Studio Code](/teamblog/docs-extension) vereinfacht auch die Tabellengenerierung, wenn Sie Visual Studio Code verwenden [(siehe unten),](#using-visual-studio-code) um die Dokumentation zu bearbeiten.

### <a name="adding-images"></a>Hinzufügen von Bildern

Sie müssen Ihre Bilder in den Ordner "mixed-reality-docs/images" im Repository hochladen und dann im Artikel entsprechend darauf verweisen. Bilder werden automatisch in voller Größe angezeigt, was bedeutet, dass große Bilder die gesamte Breite des Artikels ausfüllen. Es wird empfohlen, die Größe Ihrer Bilder vorab zu dimensionieren, bevor Sie sie hochladen. Die empfohlene Breite liegt zwischen 600 und 700 Pixel. Sie sollten die Größe jedoch nach oben oder unten anpassen, wenn es sich um einen dichten Screenshot bzw. einen Bruchteil eines Screenshots handelt.

>[!IMPORTANT]
>Sie können Bilder nur vor dem Zusammenführen in Ihr gezweigtes Repository hochladen. Wenn Sie also einem Artikel Bilder hinzufügen möchten, müssen Sie [Visual Studio Code verwenden,](#using-visual-studio-code) um die Bilder zuerst dem Ordner "images" Ihrer Verzweigung hinzuzufügen, oder stellen Sie sicher, dass Sie folgende Schritte in einem Webbrowser ausgeführt haben:
>
>1. Forked the MicrosoftDocs/mixed-reality repo.
>2. Der Artikel in Ihrer Verzweigung wurde bearbeitet.
>3. Laden Sie die Bilder, auf die Sie in Ihrem Artikel verweisen, in den Ordner "mixed-reality-docs/images" in Ihrer Verzweigung hoch.
>4. Es wurde ein **Pull Request** erstellt, um Ihre Verzweigung mit dem MicrosoftDocs/Mixed Reality-Branch "master" zusammenzuführen.
>
>Um zu erfahren, wie Sie Ihr eigenes gezweigtes Repository einrichten, befolgen Sie die Anweisungen zum [Erstellen eines neuen Artikels](#creating-a-new-article).

## <a name="previewing-your-work"></a>Anzeigen einer Vorschau Ihrer Arbeit

Beim Bearbeiten in GitHub über einen Webbrowser können Sie die Registerkarte **Vorschau** oben auf der Seite auswählen, um eine Vorschau Ihrer Arbeit anzuzeigen, bevor Sie einen Commit ausführen. 

>[!NOTE]
>Die Vorschau Ihrer Änderungen auf review.docs.microsoft.com ist nur für Microsoft-Mitarbeiter verfügbar.

Microsoft-Mitarbeiter: Nachdem Ihre Beiträge mit dem Branch "master" zusammengeführt wurden, können Sie den Inhalt überprüfen, bevor er unter veröffentlicht https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide?branch=master wird. Suchen Sie Ihren Artikel mithilfe des Inhaltsverzeichnisses in der linken Spalte.

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a>Bearbeiten im Browser im Vergleich zur Bearbeitung mit einem Desktopclient

Die Bearbeitung im Browser ist die einfachste Möglichkeit, schnelle Änderungen vorzunehmen. Es gibt jedoch einige Nachteile:

- Sie erhalten keine Rechtschreibprüfung.
- Sie erhalten keine intelligente Verknüpfung mit anderen Artikeln (Sie müssen den Dateinamen des Artikels manuell eingeben).
- Es kann sehr mühsam sein, Bilder hochzuladen und darauf zu verweisen.

Wenn Sie diese Probleme nicht behandeln möchten, verwenden Sie einen Desktopclient wie [Visual Studio Code](https://code.visualstudio.com/) mit einigen [hilfreichen Erweiterungen,](#useful-extensions) wenn Sie mitwirken.

## <a name="using-visual-studio-code"></a>Verwendung von Visual Studio Code

Aus den [oben](#editing-in-the-browser-vs-editing-with-a-desktop-client)aufgeführten Gründen bevorzugen Sie möglicherweise die Verwendung eines Desktopclients zum Bearbeiten der Dokumentation anstelle eines Webbrowsers. Wir empfehlen die Verwendung von [Visual Studio Code](https://code.visualstudio.com/).

### <a name="setup"></a>Setup

Führen Sie die folgenden Schritte aus, um Visual Studio Code für die Arbeit mit diesem Repository zu konfigurieren:

1. In einem Webbrowser:
    1. Installieren Sie [Git für Ihren PC.](https://git-scm.com/downloads)
    2. Installieren Sie [Visual Studio Code](https://code.visualstudio.com/).
    3. [Forken Sie MicrosoftDocs/Mixed Reality,](#creating-a-new-article) falls noch nicht erfolgt.
    4. Wählen Sie in Ihrer Verzweigung **Klonen oder herunterladen** aus, und kopieren Sie die URL.
2. Erstellen Sie einen lokalen Klon Ihrer Verzweigung in Visual Studio Code:
    1. Wählen **Sie** im Menü Ansicht die **Option Befehlspalette** aus.
    2. Geben Sie "Git: Clone" ein.
    3. Fügen Sie die kopierte URL ein.
    4. Wählen Sie aus, wo der Klon auf Ihrem PC gespeichert werden soll.
    5. Wählen Sie im Popupfenster **Repository öffnen** aus.

### <a name="editing-documentation"></a>Bearbeiten der Dokumentation

Verwenden Sie den folgenden Workflow, um änderungen an der Dokumentation mit Visual Studio Code vorzunehmen:

>[!NOTE]
>Alle Anleitungen zum [Bearbeiten](#how-to-make-a-change) und [Erstellen von](#creating-a-new-article) Artikeln sowie die Grundlagen der Bearbeitung [von Markdown](#markdown-basics)von oben gelten auch bei Verwendung von Visual Studio Code.

1. Stellen Sie sicher, dass Ihr geklonter Fork mit dem offiziellen Repository auf dem neuesten Stand ist.
   1. Erstellen Sie in einem Webbrowser einen Pull Request, um aktuelle Änderungen von anderen Mitwirkenden in MicrosoftDocs/mixed-reality "master" mit Ihrem Fork zu synchronisieren (stellen Sie sicher, dass der Pfeil nach rechts zeigt).
      
      ![Synchronisieren von Änderungen von MicrosoftDocs/Mixed Reality mit Ihrer Verzweigung](images/sync_repos.PNG)
   2. Wählen Sie in Visual Studio Code die Schaltfläche sync aus, um Ihre neu aktualisierte Verzweigung mit dem lokalen Klon zu synchronisieren.
      
      ![Klicken Sie auf das Bild der Synchronisierungsschaltfläche.](images/sync_clone.png)
2. Erstellen oder bearbeiten Sie Artikel in Ihrem geklonten Repository mithilfe Visual Studio Code.
   1. Bearbeiten Sie einen oder mehrere Artikel (fügen Sie bei Bedarf Bilder zum Ordner "images" hinzu).
   2. **Speichern Sie** die Änderungen im **Explorer.**
      
      ![Auswählen von "Alle speichern" im Explorer](images/explorer_save.png)
   3. **Committen Sie alle** Änderungen in der **Quellcodeverwaltung** (schreiben Sie eine Commitnachricht, wenn Sie dazu aufgefordert werden).
      
      ![Auswählen von "Commit all" in der Quellcodeverwaltung](images/source_control_commit.png)
   4. Wählen Sie die **Synchronisierungsschaltfläche** aus, um Ihre Änderungen wieder mit dem Ursprung zu synchronisieren (Ihre Verzweigung auf GitHub).
      
      ![Klicken Sie auf die Schaltfläche "Synchronisieren".](images/sync_back.png)
3. Erstellen Sie in einem Webbrowser einen Pull Request, um neue Änderungen in Ihrer Verzweigung mit MicrosoftDocs/mixed-reality "master" zu synchronisieren (stellen Sie sicher, dass der Pfeil auf die richtige Weise zeigt).

   ![Erstellen eines Pull Requests aus Ihrer Verzweigung in MicrosoftDocs/Mixed-Reality](images/pr_to_master.PNG)

### <a name="useful-extensions"></a>Nützliche Erweiterungen

Die folgenden Visual Studio Code Erweiterungen sind beim Bearbeiten der Dokumentation nützlich:

- [Docs Markdown Extension for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) - Use **ALT+M** to bring up a menu of docs authoring options wie:
   - Suchen Sie bilder, die Sie hochgeladen haben, und verweisen Sie darauf.
   - Fügen Sie Formatierungen wie Listen, Tabellen und dokumentationsspezifische Aufrufe wie `>[!NOTE]` hinzu.
   - Suchen und Verweisen auf interne Links und Lesezeichen (Links zu bestimmten Abschnitten auf einer Seite).
   - Formatierungsfehler werden hervorgehoben (zeigen Sie mit der Maus auf den Fehler, um mehr zu erfahren).
- [Code spell checker ( Rechtschreibprüfung](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) für Code): Falsch geschriebene Wörter werden unterstrichen. Klicken Sie mit der rechten Maustaste auf ein falsch geschriebenes Wort, um es zu ändern oder im Wörterbuch zu speichern.

## <a name="using-issues-to-provide-feedback-on-windows-mixed-reality-enthusiast-guide"></a>Verwenden von Problemen, um Feedback zu Windows Mixed Reality Guide zu geben

Um Feedback zu geben oder auf ein Problem hinzuweisen, anstatt die tatsächlichen Dokumentationsseiten direkt zu ändern, [erstellen Sie ein Problem,](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/issues) und die Inhaltsbesitzer tun ihr Bestes, um das Problem rechtzeitig zu beheben.

Geben Sie unbedingt den Titel des Themas und die URL an, wenn Sie ein Problem mit einer bestimmten Seite erstellen.

Vielen Dank, dass Sie diesen Inhalt unterstützt haben!