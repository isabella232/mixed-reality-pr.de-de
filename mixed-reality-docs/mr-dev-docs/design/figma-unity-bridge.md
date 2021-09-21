---
title: MRTK Figma Bridge für Unity
description: MRTK Figma Bridge for Unity ermöglicht es Ihnen, das Layout aus dem Figma Toolkit in Unity zu integrieren.
author: dongpark
ms.author: dongpark
ms.date: 03/29/2021
ms.topic: article
keywords: Figma, Sketch, Adobe XD, Design, Designer, Designdatei, UX-Design, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: d21caa796907ebc7ea1fb46ce940cf210e9fc49d
ms.sourcegitcommit: 9431e9d6d7e959954ab3e18ecc0e420a3583d1a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/21/2021
ms.locfileid: "128053808"
---
# <a name="mrtk-figma-bridge-for-unity-beta"></a>MRTK Figma Bridge für Unity (Beta)

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWKiO4]

MRTK Figma Bridge for Unity ermöglicht es Ihnen, das Layout aus dem Figma Toolkit in Unity zu integrieren. Die Bridge kann das mit dem MRTK Figma Toolkit erstellte Benutzeroberflächenlayout importieren und anschließend entsprechende MRTK-Prefabs mit der richtigen Position und Größe instanziieren. Figma Bridge unterstützt Sie beim Entwerfen des Integrationsprozesses und der Zusammenarbeit zwischen Designern und Entwicklern.


Auf der Seite [MRTK Figma Toolkit](figma-toolkit.md) erfahren Sie mehr über figma Toolkit, die Entwurfsdatei mit HoloLens 2 Ui-Bibliothek.

## <a name="prerequisites"></a>Voraussetzungen
- Weitere Informationen finden Sie unter [Installieren der Tools](/windows/mixed-reality/develop/install-the-tools) für die erforderliche Software für Mixed Reality Entwicklung.
- Unity 2019 oder höher
- [MRTK-Unity 2.7.0 oder höher](/windows/mixed-reality/mrtk-unity/)

> [!IMPORTANT]
> **Erfordert MRTK-Unity 2.7.0 oder höher**
> 
> Da Figma Toolkit und Figma Bridge auf MRTK 2.7.0-Prefabs basieren, ist MRTK 2.7.0 oder höher erforderlich. Bei Verwendung mit einer niedrigeren Version von MRTK werden einige Komponenten nicht ordnungsgemäß übersetzt.

## <a name="how-to-use-mrtk-figma-bridge"></a>Verwenden von MRTK Figma Bridge

### <a name="1-installation"></a>1. Installation

Figma Unity Bridge kann über [Mixed Reality FeatureTool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)installiert werden. Laden Sie Mixed Reality Featuretool herunter, und führen Sie es aus.

Wählen Sie auf der Seite **Features entdecken** im Abschnitt Mixed Reality **Toolkit** die Option **MRTK Figma Unity Bridge** aus. Führen Sie die Schritte aus, um das MR-Featuretool fertig zu stellen, und kehren Sie zu Ihrem Unity-Projekt zurück. Unity importiert das Paket für MRTK Figma Bridge.

### <a name="2-open-figma-bridge-window"></a>2. Öffnen des Figma Bridge-Fensters

Sobald der Importvorgang abgeschlossen ist, finden Sie Figma Bridge im Menü **Mixed Reality > Toolkit > Figma Bridge.**

<img src="images/FigmaToolkit/FigmaBridge_Menu.png" width="500px" alt="Figma Bridge - Menu"><br>

### <a name="3-generate-and-enter-your-figma-token"></a>3. Generieren und Eingeben Ihres Figma-Tokens

Klicken Sie auf der Figma-Website in der oberen linken Ecke auf das Figma-Menü, und öffnen Sie Hilfe und Konto > Kontoeinstellungen. Generieren Sie im Abschnitt "Persönliche Zugriffstoken" ein neues persönliches Zugriffstoken.

<img src="images/FigmaToolkit/FigmaToolkit_Token.png" width="500px" alt="Figma Bridge - Get Token"><br>

<img src="images/FigmaToolkit/FigmaBridge_Token.png" width="500px" alt="Figma Bridge - Enter Token"><br>


### <a name="4-enter-id-for-a-figma-document"></a>4. Geben Sie die ID für ein Figma-Dokument ein.
Jedes Figma-Dokument verfügt über eine eindeutige ID in der URL. Kopieren Sie diese ID, und fügen Sie sie in Figma Bridge ein.

<img src="images/FigmaToolkit/FigmaToolkit_DocID.png" alt="Figma Bridge - Doc ID"><br>

Klicken Sie auf **Datei abrufen,** um die Figma-Datei herunterzuladen. Sie können andere Figma-Dateien herunterladen, indem Sie eine neue ID eingeben.

Klicken Sie auf **Datei laden,** um eine Figma-Datei zu öffnen.

<img src="images/FigmaToolkit/FigmaBridge_Files.png" width="500px" alt="Figma Bridge - Files"><br>

### <a name="5-build-a-page"></a>5. Erstellen einer Seite

Figma Bridge zeigt die Liste der Seiten in der Figma-Datei an. Überprüfen Sie seiten, die Sie in Unity erstellen möchten. Klicken Sie auf die Schaltfläche **Seiten erstellen.**

<img src="images/FigmaToolkit/FigmaBridge_Pages.png" width="500px" alt="Figma Bridge - Pages"><br>

<img src="images/FigmaToolkit/FigmaBridge_Result.png" alt="Figma Bridge - Result"><br>

### <a name="6-refresh-a-document-for-changes"></a>6. Aktualisieren eines Dokuments auf Änderungen

Sie können die Figma-Datei im Web (oder mithilfe des Desktop-Editors) ändern und auf **Aktualisieren** klicken, um Änderungen abzurufen. Klicken Sie auf **Build pages (Buildseiten),** um mit Updates zu erstellen. Auf diese Weise können Sie Ihren Entwurf problemlos in Figma iterieren und in Unity sehen.



## <a name="see-also"></a>Siehe auch
* [Figma-Toolkit](figma-toolkit.md)
* [Cursor](cursors.md)
* [Handstrahl](point-and-commit.md)
* [Schaltfläche](button.md)
* [Interaktionsfähiges Objekt](interactable-object.md)
* [Begrenzungsrahmen und App-Leiste](app-bar-and-bounding-box.md)
* [Manipulation](direct-manipulation.md)
* [Handmenü](hand-menu.md)
* [Nähemenü](near-menu.md)
* [Objektsammlung](object-collection.md)
* [Sprachbefehl](voice-input.md)
* [Tastatur](keyboard.md)
* [QuickInfo](tooltip.md)
* [Filmklappe](slate.md)
* [Schieberegler](slider.md)
* [Shader](shader.md)
* [Billboarding und Tag-along](billboarding-and-tag-along.md)
* [Anzeigen des Fortschritts](progress.md)
* [Oberflächenmagnetismus](surface-magnetism.md)
