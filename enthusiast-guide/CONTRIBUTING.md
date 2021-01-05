---
title: Beitragende Anweisungen
description: Erfahren Sie mehr über die grundlegenden Schritte und Richtlinien für den Beitrag zum Windows Mixed Reality-Enthusiasten-Handbuch. Wir freuen uns über Ihr Feedback, Änderungen, Ergänzungen und Hilfe.
author: mattwojo
ms.author: mattwoj
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, Mr, Feedback, Feedback-Hub, Fehler
appliesto:
- Windows 10
ms.openlocfilehash: afb559937c2bde06d3c74c1c572aefec50502884
ms.sourcegitcommit: 9a93c9e9b3b088da942ac4386813ecf263c2e324
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2021
ms.locfileid: "97865435"
---
# <a name="contributing-to-the-mixed-reality-enthusiast-guide"></a>Beitrag zum Mixed Reality-Enthusiasten-Leitfaden

Vielen Dank für Ihr Interesse am begeisterten Leitfaden. Wir freuen uns über Ihr Feedback, Änderungen, Ergänzungen und Hilfe bei der Verbesserung unserer Dokumente. Auf dieser Seite werden die grundlegenden Schritte und Richtlinien für den Beitrag behandelt.

> [!IMPORTANT]
> Für alle Repositorys, die in „docs.microsoft.com“ veröffentlichen, gilt der [Microsoft Open Source-Verhaltenskodex](https://opensource.microsoft.com/codeofconduct/). Weitere Informationen finden Sie in den [häufig gestellten Fragen zum Verhaltenskodex](https://opensource.microsoft.com/codeofconduct/faq/). Sie können sich mit Ihren Fragen oder Kommentaren auch an [opencode@microsoft.com](mailto:opencode@microsoft.com) wenden.<br>
>
> Für kleinere Korrekturen oder Klarstellungen zu Dokumentation und Codebeispielen in öffentlichen Repositorys gelten die [Nutzungsbestimmungen zu docs.microsoft.com](https://docs.microsoft.com/legal/termsofuse). Neue oder signifikante Änderungen haben einen Kommentar im Pull Request zur Folge, in dem wir Sie bitten, online eine Lizenzvereinbarung für Beiträge (Contribution License Agreement, CLA) zu übermitteln. Dies gilt, wenn Sie kein Mitarbeiter von Microsoft sind. Sie müssen das Onlineformular ausfüllen, damit wir Ihren Pull Request annehmen können.

## <a name="before-you-start"></a>Vorbereitung

Wenn Sie noch nicht über ein Konto verfügen, müssen Sie [ein GitHub-Konto erstellen](https://github.com/join).

>[!NOTE]
>Wenn Sie ein Microsoft-Mitarbeiter sind, verknüpfen Sie Ihr GitHub-Konto mit Ihrem Microsoft-Alias im [Open-Source-Portal von Microsoft](https://repos.opensource.microsoft.com/). Treten Sie den Organisationen **"Microsoft"** und **"microsoftdocs"** bei.

Wenn Sie Ihr GitHub-Konto einrichten, werden auch diese Sicherheitsvorkehrungen empfohlen:
- Erstellen Sie ein sicheres [Kennwort für Ihr GitHub-Konto](https://github.com/settings/admin).
- Aktivieren Sie die [zweistufige Authentifizierung](https://github.com/settings/two_factor_authentication/configure).
- Speichern Sie Ihre [Wiederherstellungs Codes](https://github.com/settings/auth/recovery-codes) an einem sicheren Ort.
- Aktualisieren Sie die Einstellungen für das [öffentliche Profil](https://github.com/settings/profile).
   - Legen Sie Ihren Namen fest, und legen Sie fest, dass Ihre *öffentliche e-Mail* - *Adresse nicht angezeigt* werden soll.
   - Es wird empfohlen, ein Profilbild hochzuladen, da eine Miniaturansicht auf den Dokumentationsseiten angezeigt wird, zu denen Sie beitragen.
- Wenn Sie beabsichtigen, die Befehlszeile zu verwenden, sollten Sie die Einrichtung [von git Credential Manager für Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest)in Erwägung gezogen haben. Auf diese Weise müssen Sie Ihr Kennwort nicht jedes Mal eingeben, wenn Sie einen Beitrag leisten.

Das Veröffentlichungs System ist an GitHub gebunden, sodass diese Schritte wichtig sind. Sie werden entweder als Autor oder Mitwirkender für jeden Artikel mithilfe Ihres GitHub-Alias aufgeführt.

## <a name="how-to-make-a-change"></a>So nehmen Sie eine Änderung vor

| Führe diese Schritte aus, um eine Änderung an den Dokumenten vorzuschlagen: | Screenshots |
| :------------------- | :--------: |
| 1. Wenn Sie eine docs.Microsoft.com-Seite anzeigen, klicken Sie oben rechts auf der Seite auf die Schaltfläche **Bearbeiten** .  Du wirst zur entsprechenden Markdown-Quelldatei im [GitHub-Repository](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide) geleitet. | ![Bearbeitungs Schaltfläche](images/edit_button.jpg) |
| 2. Wenn Sie noch nicht über ein GitHub-Konto verfügen, klicken Sie oben rechts auf **registrieren** , und erstellen Sie ein neues Konto. | ![Schaltfläche "Anmelden"](images/signup-for-github-button.png)|
| 3. Klicken Sie auf der entsprechenden GitHub-Seite, die geöffnet wird, auf Bearbeiten (das Stift Symbol). | ![Stift Schaltfläche](images/pencil_button.jpg)|
| 4. aktualisieren Sie im Bereich "Datei bearbeiten" [die Metadaten der Dateien](#updating-metadata) , und verwenden Sie die markdown-Sprache, um den Inhalt zu ändern. ([Schreiben von markdown](https://help.github.com/articles/basic-writing-and-formatting-syntax/))| ![Datei bearbeiten](images/edit-in-github.png)|
| 5. Klicken Sie auf Vorschau der Änderungen, um sicherzustellen, dass die Formatierung erwartungsgemäß aussieht | ![Vorschau der Änderungen](images/edit-in-github.png)|
| 6. Wenn Sie fertig sind, Scrollen Sie zum unteren Rand der Seite, und klicken Sie auf "Datei Änderung vorschlagen". Daraufhin wird die Seite "Änderungen werden verglichen" angezeigt, auf der Sie Ihre Änderungen überprüfen können. Klicken Sie dann auf die Schaltfläche "Create Pull Request", um die Änderungen zu übermitteln. An diesem Punkt sind Sie fertig! | ![Änderung vorschlagen](images/propose.jpg)|

Nachdem Sie Änderungen (über eine Pull Request) übermittelt haben, werden Sie von einem Mitglied des Dokumentationsteams geprüft. Wenn Ihre Anforderung akzeptiert wird, werden Updates in veröffentlicht [https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide) .

* Zur internen Überprüfung können Sie Ihre Änderungen unter sehen [https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide](https://review.docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/?branch=master) .

### <a name="updating-metadata"></a>Aktualisieren von Metadaten

Aktualisieren Sie die Metadaten am Anfang jedes Artikels:
   * **Title**: der Seitentitel, der auf der Registerkarte Browser angezeigt wird, wenn der Artikel angezeigt wird. Seitentitel werden für SEO und Indizierung verwendet. ändern Sie also den Titel nur dann, wenn dies erforderlich ist (obwohl dies weniger kritisch ist, bevor die Dokumentation öffentlich wird).
   * **Beschreibung**: Schreiben Sie eine kurze Beschreibung des Inhalts des Artikels, wodurch die SEO und die Ermittlung erhöht werden.
   * **Autor**: Wenn Sie der primäre Besitzer der Seite sind, fügen Sie hier Ihren GitHub-Alias hinzu.
   * **ms. Author**: Wenn Sie der primäre Besitzer der Seite sind, fügen Sie hier Ihren Microsoft-Alias hinzu (Sie benötigen nicht @microsoft.com , sondern nur den Alias).
   * **ms. Date**: Aktualisieren Sie das Datum, wenn Sie der Seite größere Inhalte hinzufügen, aber nicht für Korrekturen wie die Klärung, Formatierung, Grammatik oder Rechtschreibung.
   * **Schlüsselwörter**: Unterstützung von Schlüsselwörtern in SEO (Suchmaschinenoptimierung). Fügen Sie Schlüsselwörter, getrennt durch ein Komma und ein Leerzeichen, ein, die für den Artikel spezifisch sind, jedoch keine Interpunktions Zeichen nach dem letzten Schlüsselwort in der Liste. Sie müssen keine globalen Schlüsselwörter hinzufügen, die für alle Artikel gelten, da diese an anderer Stelle verwaltet werden. 

### <a name="renaming-or-deleting-an-existing-article"></a>Umbenennen oder Löschen eines vorhandenen Artikels

Wenn die Änderung einen vorhandenen Artikel umbenennen oder löschen soll, müssen Sie eine Umleitung hinzufügen. Auf diese Weise wird jeder Benutzer mit einem Link zum vorhandenen Artikel immer noch an der richtigen Stelle angezeigt. Umleitungen werden von der .openpublishing.redirection.jsfür die Datei im Stammverzeichnis des Repository verwaltet.

Fügen Sie dem-Array einen Eintrag hinzu, um eine Umleitung zu .openpublishing.redirection.jshinzuzufügen `redirections` :

```json
{
    "redirections": [
        {
            "source_path": "mixed-reality-docs/enthusiast-guide/old-article.md",
            "redirect_url": "new-article#section-about-old-topic",
            "redirect_document_id": false
        },
```

- Der `source_path` ist der relative Repository-Pfad zu dem alten Artikel, den Sie entfernen. Stellen Sie sicher, dass der Pfad mit beginnt `mixed-reality-docs/enthusiast-guide` und mit endet `.md` .
- `redirect_url`Ist die relative öffentliche URL aus dem alten Artikel zum neuen Artikel. Stellen Sie sicher, dass diese URL **nicht** `mixed-reality-docs/enthusiast-guide` oder enthält `.md` , da Sie auf die öffentliche URL und nicht auf den Repository-Pfad verweist. Das Verknüpfen mit einem Abschnitt innerhalb des neuen Artikels mit `#section` ist zulässig. Sie können bei Bedarf auch einen absoluten Pfad zu einer anderen Website verwenden.
- `redirect_document_id` Gibt an, ob Sie die Dokument-ID aus der vorherigen Datei beibehalten möchten. Der Standardwert ist `false`. Verwenden `true` Sie, wenn Sie den `ms.documentid` Attribut Wert aus dem umgeleiteten Artikel beibehalten möchten. Wenn Sie die Dokument-ID beibehalten, werden Daten, wie z. b. Seitenaufrufe und Rang folgen, in den Ziel Artikel übertragen. Dies ist der Fall, wenn die Umleitung primär eine Umbenennung ist, und kein Zeiger auf einen anderen Artikel, der nur einen Teil desselben Inhalts behandelt.

Wenn Sie eine Umleitung hinzufügen, achten Sie darauf, dass Sie auch die alte Datei löschen.

### <a name="creating-a-new-article"></a>Erstellen eines neuen Artikels

Verwenden Sie den folgenden Workflow, um *neue Artikel* im Dokumentations Repository über GitHub in einem Webbrowser zu erstellen:

1. Erstellen Sie eine Verzweigung aus dem Branch "microsoftdocs/Mixed-Reality/Tree/docs/Enthusiast-Guide ' Master '" (mithilfe der Schaltfläche **Fork** in der oberen rechten Ecke).

   ![Verzweigen Sie den masterb Ranch.](images/forkbranch.png)
2. Wählen Sie im Ordner "Mixed-Reality/Enthusiast-Guide" in der oberen rechten Ecke **neue Datei erstellen** aus.
3. Erstellen Sie einen Seitennamen für den Artikel (verwenden Sie Bindestriche anstelle von Leerzeichen, verwenden Sie keine Interpunktions Zeichen oder Apostrophe), und fügen Sie ". MD" an.

   ![Benennen Sie die neue Seite.](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   >Stellen Sie sicher, dass Sie den neuen Artikel aus dem Ordner "Mixed-Reality-docs/Enthusiast" erstellen. Sie können dies überprüfen, indem Sie in der Zeile neuer Dateiname nach "/Mixed-Reality-docs/Enthusiast-Guide" suchen.

4. Fügen Sie am oberen Rand der neuen Seite den folgenden Metadatenblock hinzu:

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

5. Füllen Sie die relevanten Metadatenfelder gemäß den Anweisungen im [obigen Abschnitt](#updating-metadata)aus.
6. Schreiben Sie Artikel Inhalte mithilfe von [markdown-Grundlagen](#markdown-basics).
7. Fügen Sie `## See also` am Ende des Artikels einen Abschnitt mit Links zu anderen relevanten Artikeln hinzu.
8. Wenn Sie fertig sind, wählen Sie **Commit New File** aus.
9. Wählen Sie **neu Pull Request** aus, und führen Sie den masterb Ranch der Verzweigung in microsoftdocs/Mixed-Reality/Enthusiast-Guide ' Master ' aus (stellen Sie sicher, dass der Pfeil auf die richtige Weise zeigt).

   ![Erstellen Sie Pull Request aus Ihrem Fork in microsoftdocs/Mixed-Reality/Enthusiast-Guide](images/pr_to_master.PNG)

## <a name="working-with-branches"></a>Arbeiten mit Verzweigungen

Das [GitHub-Repository für gemischte Realität](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide) verwendet zwei übergeordnete Haupt Verzweigungen: [Master](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/tree/master), dieser Inhalt kann auf der [Stagingsite](https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide)überprüft werden und [Live](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/tree/live), um Inhalte zu erhalten, die auf der [Live Website](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide)angezeigt werden.

Wenn Sie Beiträge leisten, senden Sie Ihren Pull Request (PR) an den **masterb** Ranch. Diese Verzweigung kann auf der Stagingsite angezeigt werden und sollte nur Beiträge enthalten, die für die Liveveröffentlichung bereit sind. Sie können auch einen Branch mit Ihrem eigenen eindeutigen branchnamen erstellen und übermitteln, der in der Stagingsite ausgewählt und angezeigt werden kann. (Die **Live** Verzweigung ist nur für die Verwendung durch die Inhalts Administratoren zulässig.)

## <a name="markdown-basics"></a>Grundlegendes zu Markdown

Die folgenden Ressourcen helfen Ihnen, zu erfahren, wie Sie die Dokumentation mit der markdown-Sprache bearbeiten:

- [Markdown-Grundlagen](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [Markdown-Referenz Poster mit einem Blick](images/MarkdownPoster.pdf)
- [Zusätzliche Ressourcen zum Schreiben von markdown für docs.Microsoft.com](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a>Hinzufügen von Tabellen

Aufgrund der Art und Weise, in der docs.Microsoft.com Stile Tabellen haben, haben Sie keine Rahmen oder benutzerdefinierten Stile, auch wenn Sie das Inline-CSS ausprobieren. Es scheint für einen kurzen Zeitraum zu funktionieren, aber schließlich entfernt die Plattform das Formatieren aus der Tabelle. Planen Sie also voraus, und halten Sie die Tabellen einfach. [Im folgenden finden Sie eine Website, mit der markdown-Tabellen einfach](https://www.tablesgenerator.com/markdown_tables)werden.

Die [docs markdown-Erweiterung für Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) erleichtert auch die Tabellen Generierung, wenn Sie [Visual Studio Code (siehe unten)](#using-visual-studio-code) verwenden, um die Dokumentation zu bearbeiten.

### <a name="adding-images"></a>Hinzufügen von Bildern

Sie müssen Ihre Images in den Ordner "Mixed-Reality-docs/Images" im Repository hochladen und entsprechend im Artikel darauf verweisen. Bilder werden automatisch in voller Größe angezeigt, d. h., große Bilder füllen die gesamte Breite des Artikels aus. Es wird empfohlen, die Abbilder vor dem Hochladen vorab zu dimensionieren. Die empfohlene Breite liegt zwischen 600 und 700 Pixel. Sie sollten jedoch die Größe nach oben oder unten verkleinern, wenn es sich um einen dichten Screenshot oder einen Bruchteil eines Screenshots handelt.

>[!IMPORTANT]
>Vor dem Zusammenführen können Sie nur Bilder in Ihr verzweigtes Repository hochladen. Wenn Sie also einem Artikel Bilder hinzufügen möchten, müssen Sie [Visual Studio Code verwenden](#using-visual-studio-code) , um die Bilder zunächst dem Ordner "Images" ihrer Verzweigung hinzuzufügen, oder sicherstellen, dass Sie die folgenden Schritte in einem Webbrowser ausgeführt haben:
>
>1. Verzweigt das Repository "microsoftdocs/Mixed-Reality".
>2. Der Artikel in der Verzweigung wurde bearbeitet.
>3. Die Bilder, auf die Sie verweisen, werden in Ihrem Artikel in den Ordner "Mixed-Reality-docs/Images" in ihrer Verzweigung hochgeladen.
>4. Es wurde ein **Pull Request** erstellt, um Ihre Verzweigung mit dem Branch "Master" microsoftdocs/Mixed-Reality zusammenzuführen.
>
>Um zu erfahren, wie Sie ein eigenes verzweigtes Repository einrichten, befolgen Sie die Anweisungen zum [Erstellen eines neuen Artikels](#creating-a-new-article).

## <a name="previewing-your-work"></a>Anzeigen einer Vorschau der Arbeit

Während der Bearbeitung in GitHub über einen Webbrowser können Sie die Registerkarte **Vorschau** im oberen Bereich der Seite auswählen, um die Arbeit vor dem Commit in einer Vorschau anzuzeigen. 

>[!NOTE]
>Die Vorschau der Änderungen auf review.docs.Microsoft.com ist nur für Microsoft-Mitarbeiter verfügbar.

Microsoft-Mitarbeiter: Nachdem Ihre Beiträge in der Verzweigung "Master" zusammengeführt wurden, können Sie den Inhalt überprüfen, bevor er in der Öffentlichkeit veröffentlicht wird https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide?branch=master . Suchen Sie Ihren Artikel mithilfe des Inhaltsverzeichnisses in der linken Spalte.

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a>Bearbeiten im Browser und bearbeiten mit einem Desktop Client

Das Bearbeiten im Browser ist die einfachste Möglichkeit, schnelle Änderungen vorzunehmen, es gibt jedoch einige Nachteile:

- Sie erhalten keine Rechtschreibprüfung.
- Sie erhalten keine intelligenten Verknüpfungen mit anderen Artikeln (Sie müssen den Dateinamen des Artikels manuell eingeben).
- Das Hochladen und verweisen auf Bilder kann ein Problem sein.

Wenn Sie diese Probleme nicht beheben können, verwenden Sie einen Desktop Client wie [Visual Studio Code](https://code.visualstudio.com/) mit einigen [hilfreichen Erweiterungen](#useful-extensions) , wenn Sie mitwirken.

## <a name="using-visual-studio-code"></a>Verwendung von Visual Studio Code

Aus den [oben](#editing-in-the-browser-vs-editing-with-a-desktop-client)aufgeführten Gründen empfiehlt es sich, anstelle eines Webbrowsers einen Desktop Client zum Bearbeiten der Dokumentation zu verwenden. Es wird empfohlen, [Visual Studio Code](https://code.visualstudio.com/)zu verwenden.

### <a name="setup"></a>Einrichten

Führen Sie die folgenden Schritte aus, um Visual Studio Code für die Verwendung dieses Repository zu konfigurieren:

1. In einem Webbrowser:
    1. Installieren [Sie git für Ihren PC](https://git-scm.com/downloads).
    2. Installieren Sie [Visual Studio Code](https://code.visualstudio.com/).
    3. [Verzweigung microsoftdocs/Mixed-Reality](#creating-a-new-article) , wenn Sie dies noch nicht getan haben.
    4. Wählen Sie in der Verzweigung **Klonen oder herunterladen** aus, und kopieren Sie die URL.
2. Erstellen Sie in Visual Studio Code einen lokalen Klon Ihrer Verzweigung:
    1. Wählen Sie im Menü **Ansicht** die Option **Befehls Palette** aus.
    2. Geben Sie "git: Clone" ein.
    3. Fügen Sie die kopierte URL ein.
    4. Wählen Sie aus, wo der Klon auf Ihrem PC gespeichert werden soll.
    5. Wählen Sie im Popup Repository **Open** Repository aus.

### <a name="editing-documentation"></a>Bearbeiten der Dokumentation

Verwenden Sie den folgenden Workflow, um Änderungen an der Dokumentation mit Visual Studio Code vorzunehmen:

>[!NOTE]
>Alle Anleitungen zum [Bearbeiten](#how-to-make-a-change) und [Erstellen](#creating-a-new-article) von Artikeln und die [Grundlagen der Bearbeitung von markdown](#markdown-basics), die oben beschrieben werden, gelten auch für die Verwendung von Visual Studio Code.

1. Stellen Sie sicher, dass Ihre geklonte Verzweigung mit dem offiziellen Repository auf dem neuesten Stand ist.
   1. Erstellen Sie in einem Webbrowser eine Pull Request, um aktuelle Änderungen von anderen Mitwirkenden in microsoftdocs/Mixed-Reality ' Master ' mit ihrer Verzweigung zu synchronisieren (stellen Sie sicher, dass der Pfeil auf die richtige Weise zeigt).
      
      ![Synchronisieren von Änderungen von microsoftdocs/Mixed-Reality mit ihrer Verzweigung](images/sync_repos.PNG)
   2. Wählen Sie in Visual Studio Code die Schaltfläche synchronisieren aus, um die neu aktualisierte Verzweigung mit dem lokalen Klon zu synchronisieren.
      
      ![Klicken Sie auf die Schaltfläche Sync](images/sync_clone.png)
2. Erstellen oder bearbeiten Sie Artikel in Ihrem geklonten Repository mithilfe von Visual Studio Code.
   1. Bearbeiten von mindestens einem Artikel (Hinzufügen von Bildern zu "Bilder", falls erforderlich).
   2. **Speichern** Sie die Änderungen im **Explorer**.
      
      ![Wählen Sie im Explorer "Alle speichern" aus.](images/explorer_save.png)
   3. **Commit für alle** Änderungen in der **Quell** Code Verwaltung Commit (Schreib Commit-Nachricht bei entsprechender Aufforderung).
      
      !["Commit für alle" in der Quell Code Verwaltung auswählen](images/source_control_commit.png)
   4. Wählen Sie die Schaltfläche **Synchronisieren** , um Ihre Änderungen wieder mit dem Ursprung zu synchronisieren (Ihre Verzweigung auf GitHub).
      
      ![Klicken Sie auf die Schaltfläche synchronisieren](images/sync_back.png)
3. Erstellen Sie in einem Webbrowser eine Pull Request, um neue Änderungen in der Verzweigung wieder mit microsoftdocs/Mixed-Reality ' Master ' zu synchronisieren (stellen Sie sicher, dass der Pfeil auf die richtige Weise zeigt).

   ![Erstellen von Pull Request aus Ihrem Fork in microsoftdocs/Mixed-Reality](images/pr_to_master.PNG)

### <a name="useful-extensions"></a>Nützliche Erweiterungen

Die folgenden Visual Studio Code Erweiterungen sind beim Bearbeiten der Dokumentation nützlich:

- [Docs markdown-Erweiterung für Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) : Verwenden Sie **ALT + M** , um ein Menü mit Dokument Erstellungs Optionen wie den folgenden anzuzeigen:
   - Such-und Referenz Images, die Sie hochgeladen haben.
   - Fügen Sie Formatierungen wie Listen, Tabellen und docs-spezifische aufrufsouts wie hinzu `>[!NOTE]` .
   - Suchen und verweisen auf interne Links und Lesezeichen (Links zu bestimmten Abschnitten innerhalb einer Seite).
   - Formatierungs Fehler sind hervorgehoben (zeigen Sie mit der Maus auf den Fehler, um weitere Informationen zu erhalten).
- [Code Rechtschreib](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) Prüfung: falsch geschriebene Wörter werden unterstrichen. Klicken Sie mit der rechten Maustaste auf ein falsch geschriebenes Wort, um es zu ändern oder im Wörterbuch zu speichern.

## <a name="using-issues-to-provide-feedback-on-windows-mixed-reality-enthusiast-guide"></a>Verwenden von Problemen zur Bereitstellung von Feedback zum Windows Mixed Reality-Enthusiasten-Leitfaden

Wenn Sie Feedback bereitstellen oder auf ein Problem hinweisen möchten, anstatt die eigentlichen Dokumentationsseiten direkt zu ändern, [Erstellen Sie ein Problem](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/issues) , und die Besitzer der Inhalte können das Problem rechtzeitig beheben.

Stellen Sie sicher, dass Sie den Thementitel und die URL einschließen, wenn Sie ein Problem in Bezug auf eine bestimmte Seite erstellen.

Vielen Dank für Ihre Unterstützung für diesen Inhalt!
