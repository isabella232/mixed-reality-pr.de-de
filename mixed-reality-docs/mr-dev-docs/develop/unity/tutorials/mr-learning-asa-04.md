---
title: Anzeigen von Azure Spatial Anchors-Feedback
description: In diesem Kurs erfahren Sie, wie Sie Feedback von Azure Spatial Anchors in einer Mixed Reality-Anwendung anzeigen.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, MRTK, Mixed Reality Toolkit, UWP, Azure Spatial Anchors, Sitzungen, Feedbackelemente
ms.localizationpriority: high
ms.openlocfilehash: 65a814019909ecacffdd454171075c68497dae1b2123804e07ced1d7e100fdd8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115215668"
---
# <a name="4-displaying-feedback-from-azure-spatial-anchors"></a>4. Anzeigen des Feedbacks von Azure Spatial Anchors

In diesem Tutorial erfahren Sie, wie Sie Feedback zur Ankerermittlung, zu Ereignissen und zum Status bei der Verwendung von Azure Spatial Anchors (ASA) für Benutzer bereitstellen.

## <a name="objectives"></a>Ziele

* Erlernen des Einrichtens eines Bereichs der Benutzeroberfläche, in dem grundlegende Informationen über die aktuelle ASA-Sitzung angezeigt werden
* Kennenlernen und Untersuchen der Feedbackelemente, die Benutzern vom ASA SDK zur Verfügung gestellt werden

## <a name="setting-up-asa-feedback-panel"></a>Einrichten des ASA-Feedbackbereichs

Klicken Sie im Hierarchiefenster mit der rechten Maustaste auf das Objekt **Instructions** > **TextContent**. Wählen Sie **3D Object** > **Text - TextMeshPro** (3D-Objekt > Text – TextMeshPro) aus, um ein Textobjekt von TextMeshPro als untergeordnetes Element des Objekts „Instructions > TextContent“ zu erstellen:

![Unity mit neu erstelltem, ausgewähltem TextMeshPro-Objekt](images/mr-learning-asa/asa-04-section1-step1-1.png)

> [!TIP]
> Um das Arbeiten mit Ihrer Szene zu erleichtern, legen Sie die <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> (Sichtbarkeit in der Szene) für das ParentAnchor-Objekt auf „Aus“ fest, indem Sie links neben dem Objekt auf das Augensymbol klicken. Dadurch wird das Objekt im Szenenfenster ausgeblendet, ohne seine Sichtbarkeit im Spiel zu ändern.

Benennen Sie das neu erstellte Textobjekt (TMP) **Feedback**, und ändern Sie dann im Inspektorfenster seine Position und Größe so, dass es ordentlich unter dem Anweisungstext platziert ist, beispielsweise:

* Ändern Sie die **Pos Y** (Y-Position) der Rect Transform-Komponente in -0,24.
* Ändern Sie die **Width** (Breite) der Rect Transform-Komponente in 0,555.
* Ändern Sie die **Height** (Höhe) der Rect Transform-Komponente in 0,1.

Wählen Sie dann die Schriftarteigenschaften so, dass der Text gut in den Textbereich passt, beispielsweise:

* Ändern Sie den **Font Style** (Schriftschnitt) der TextMeshPro – Text-Komponente in Fett.
* Ändern Sie die **Font Size** (Schriftgrad) der TextMeshPro – Text-Komponente in 0,17.
* Ändern Sie das **Alignment** (Ausrichtung) der TextMeshPro – Text-Komponente in „Zentriert“ und „Mitte“.

![Unity mit konfiguriertem Feedback-Objekt](images/mr-learning-asa/asa-04-section1-step1-2.png)

Wählen Sie im Hierarchiefenster das **Feedback**-Objekt aus, verwenden Sie dann im Inspektorfenster die Schaltfläche **Add Component** (Komponente hinzufügen), um die Komponente **Anchor Feedback Script (Script)** hinzuzufügen, und konfigurieren Sie sie wie folgt:

* Weisen Sie das **Feedback**-Objekt selbst dem Feld **Feedbacktext** der **Anchor Feedback Script (Script)** -Komponente zu.

![Unity mit konfigurierter Anchor Feedback Script-Komponente](images/mr-learning-asa/asa-04-section1-step1-3.png)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie gelernt, wie Sie einen Benutzeroberflächenbereich erstellen. Er zeigt den aktuellen Status der Azure Spatial Anchor-Erfahrung an, um Benutzern Feedback in Echtzeit zu geben.

> [!div class="nextstepaction"]
> [Nächstes Tutorial: 5. Azure Spatial Anchors für Android und iOS](mr-learning-asa-05.md)
