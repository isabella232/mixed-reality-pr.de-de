---
title: Mit Entwerfen und Prototyping beginnen
description: Wenn Sie bereit sind, etwas zu erstellen, lernen Sie die grundlegenden Konzepte kennen, die Sie für den Einstieg in Entwerfen und Prototyping benötigen.
author: grbury
ms.author: grbury
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, Entdecken, Verteilen, Index, Einstiegsseite, Entwurf, Entwicklung, Tutorials, Beispiel-Apps, Grundlagen, Fallstudien, Ressourcen, HoloLens-Vorgehensweise, Open-Source-Projekte, Kernkonzepte, Interaktion, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: d106b295b72a3087461ccbe8818a7cc23c311f46e3ae20a748c8ce22ec4f89b9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213303"
---
# <a name="start-designing-and-prototyping"></a>Mit Entwerfen und Prototyping beginnen

![Zusammenfassung Mixed Reality-Design](images/design-hero-image.png)

Mixed Reality-Anwendungen sind mit nichts zu vergleichen, was aktuell in der Welt existiert, und sie zu entwerfen, ist harte Arbeit. Sie müssen nicht nur die neuen Kombinationen aus realen und virtuellen Welten berücksichtigen, die Sie erschaffen, sondern auch die neuen Benutzererfahrungen, die sie hervorbringen. Da Mixed Reality ein weites Feld ist, haben wir wichtige Punkte aus dem Gesamtspektrum des Entwerfens ausgewählt und sie unten in Form einer Reihe von Prüfpunkten aufgefächert. Diese sind bauen aufeinander auf, wenn Sie aber bereits praktische Erfahrungen haben, lassen Sie sich nicht abhalten, zu einem der folgenden Abschnitte zu springen. 

Sehen Sie sich zum Einstieg unser Übersichtsvideo zum Entwerfen an:

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4LhlW]

## <a name="design-checkpoints"></a>Prüfpunkte für den Entwurf

Nutzen Sie die folgenden Prüfpunkte, um Ihre Ideen und Konzepte für Anwendungen in eine Mixed Reality-Welt einzubringen.

### <a name="1-getting-started"></a>1. Erste Schritte

Wie alle Reisen beginnt Ihr Abenteuer im Entwerfen von Mixed Reality-Anwendungen mit den Grundlagen. Wir empfehlen Ihnen, sich mit den Artikeln [Was ist Mixed Reality?](../discover/mixed-reality.md) und [Was ist ein Hologramm?](../discover/hologram.md) vertraut zu machen, um Ihren Verstand auf immersives Entwerfen vorzubereiten. Nachdem Sie Ihre Lektüre beendet haben, sind Sie bereit, Ihren Weg in das Gebiet des Mixed Reality-Entwurfs anzutreten.

![Gif-Grafik „Getting started“ (Erste Schritte) aus der App zum Entwerfen von Hologrammen](images/HandTracking2.gif)

|  Prüfpunkt  |  Ergebnis  |
| --- | --- |
| [Erweitern Ihres Entwurfsprozesses](../discover/case-study-expanding-the-design-process-for-mixed-reality.md) | Erhalten Sie aus erster Hand Einblick in einen Entwurfsprozess für Mixed Reality, der bei Entwicklern bei und außerhalb von Microsoft zusammengetragen wurde. |
| [Typen von Mixed Reality-Apps](types-of-mixed-reality-apps.md) | Entscheiden Sie, wo im Mixed Reality-Spektrum das Erlebnis mit Ihrer App angesiedelt sein soll |
| [App zum Entwerfen von Hologrammen](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd) | Lernen Sie die Grundlagen des Mixed Reality-UX-Designs durch eigene Erfahrung, indem Sie in die Verhaltensweisen, Tipps und Empfehlungen zum Erstellen verblüffender HoloLens-Apps eintauchen (steht zum Download im Microsoft Store in HoloLens 2 zur Verfügung) |
| [MRTK-Beispiele-Hub](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4) | Kennenlernen gängiger räumlicher Interaktionen und UX-Bausteine für Mixed Reality (zum Download verfügbar im Microsoft Store in HoloLens 2) |
| **Optional** [Herunterladen des Figma-Toolkit](figma-toolkit.md) | Das Figma-Toolkit enthält Ressourcen, die Sie verwenden können, um ausgehend von den im MRTK verfügbaren Komponenten die Benutzeroberfläche zu entwerfen und zu layouten. |

### <a name="2-core-concepts"></a>2. Kernkonzepte

Unabhängig davon, ob Sie für VR oder AR entwickeln, gibt es einige grundlegende Konzepte, die für das Entwerfen von kontinuierlichen immersiven Erfahrungen gelten. Den Blickpunkts des Benutzers zu verstehen, Objekte zu positionieren und sicherzustellen, dass alle sich wohl und sicher fühlen, haben an diesem Punkt Ihres Wegs die höchste Priorität. Am Ende dieses Abschnitts haben Sie eine solide Grundlage, die Sie in den Entwurf der Interaktion einbringen können.

![Abbildung eines Kernkonzeptbeispiels](images/fragments-750px.jpg)

|  Konzept  |  Ergebnis  |
| --- | --- |
| [Holografischer Rahmen](holographic-frame.md) | Verstehen Sie, wie Benutzer beim Tragen ihrer Headsets Ihre Inhalte als Überlagerung der realen Welt sehen |
| [Koordinatensysteme](coordinate-systems.md) | Lernen Sie, Hologramme an sinnvollen Positionen in der Welt zu platzieren, sei es im physischen Raum oder in einem virtuellen Bereich, den Sie geschaffen haben. |
| [Räumliche Abbildung](spatial-mapping.md) | Verankern Sie Objekte in der Welt des Benutzers, und nutzen Sie die physischen Oberflächen der realen Welt. |
| [Komfortaspekte](comfort.md) | Sorgen Sie für Benutzerkomfort und Sicherheit, indem Sie immersive Inhalte auf eine Weise erstellen und präsentieren, die die natürliche Welt nachahmt. |

### <a name="3-interaction-design"></a>3. Interaktionsgestaltung

Ganz gleich, wie schön und immersiv eine virtuelle Erfahrung ist, ohne Interaktion ist sie nutzlos. In diesem Abschnitt werden die grundlegenden Interaktionsmodelle, Hand- und Motion Controller, Spracheingaben und das Erfassen von Eyetracking-Daten von Ihren Benutzern erläutert. Am Ende dieses Abschnitts sind Sie bereit, das letzte große Thema auf Ihrem Entwurfsweg anzugehen: die Benutzererfahrung.

![Faktoren der Interaktionsgestaltung](images/UX_Hero_Manipulation.jpg)

|  Konzept  |  Ergebnis  |
| --- | --- |
| [Interaktionsmodelle](interaction-fundamentals.md) | Stellen Sie durch Hand-, Augen- und Spracheingabe instinktive Interaktionen für Ihre Benutzer zur Verfügung |
| [Hände und Motion-Controller](hands-and-tools.md) | Erfahren Sie, wie Sie mit Hologrammen im Nahbereich – mit den Händen des Benutzers – oder im Fernbereich präzise interagieren können |
| [Spracheingabe](voice-input.md) | Verwenden Sie Sprachbefehle als Eingabe in Ihren immersiven Apps, um die umgebenden Hologramme und Umgebungen zu steuern  |
| [Eyetracking](eye-tracking.md) | Verleihen Sie einer holografischen Benutzererfahrung ein ganz anderes Niveau von Kontext und menschlichem Verständnis, indem Sie Informationen darüber nutzen, was Ihre Benutzer ansehen |

### <a name="4-user-experience-elements"></a>4. Elemente der Benutzererfahrung

Da Sie jetzt die grundlegenden Interaktionen beherrschen, können Sie sich auf subtilere Elemente der Benutzererfahrung konzentrieren und sie für die einzigartigen Umgebungen anpassen, die Mixed Reality bieten kann. Beim Gestalten einer intuitiven Benutzererfahrung befassen Sie sich mit allgemeinen Verhaltensweisen, dem Design von Medienobjekten, der Skalierung von Objekten und Typografie. Diese Abschnitt markiert das Ende der offiziellen Reise in die Welt des Mixed Reality-Entwurfs, im Abschnitt [Wie geht es weiter?](#whats-next) gibt es aber weitere Ressourcen – die Aufgaben gehen Ihnen nicht aus.

![UX-Elemente](images/UX_Hero_BoundingBox.jpg)

|  Konzept  |  Ergebnis  |
| --- | --- |
| [Allgemeine Steuerelemente und Verhaltensweisen](app-patterns-landingpage.md) | Erfahren Sie mehr über häufig verwendete räumliche Interaktionen und UI-Bausteine. |
| [Farbe, Licht und Materialien](color-light-and-materials.md) | Entwerfen Sie hochwertige Medienobjekte für Mixed Reality, die Farbe, Beleuchtung und Materialien berücksichtigen. |
| [Objektmaßstab](scale.md) | Beziehen Sie so viele visuelle Hinweise wie möglich ein, die Ihren Benutzern helfen, zu verstehen, wo sich Objekte befinden, wie groß sie sind und woraus sie bestehen. |
| [Typografie](typography.md) | Verwenden Sie klaren, lesbaren Text im dreidimensionalen Raum, um Ihren Benutzern die wichtigen Informationen zu geben, die sie benötigen. |

## <a name="whats-next"></a>Wie geht es weiter?

Die Arbeit eines Entwerfers ist nie getan, insbesondere wenn es darum geht, immersive Erfahrungen unter einem neuen Paradigma zu schaffen. Die folgenden Abschnitte führen Sie aus dem Bereich des Anfängermaterials für Entwerfer hinaus, das Sie bereits durchgearbeitet haben, hinein in die Welt der Mixed Reality-Entwicklung. Diese Themen und Ressourcen weisen keine bestimmte Reihenfolge auf, tauchen Sie also ruhig ein!

### <a name="choose-a-prototyping-option"></a>Auswählen einer Prototypingoption  

:::row:::   
    :::column:::    
        [![MRTK Figma-Toolkit](images/74-13.png)](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)<br>
        **[Figma-Toolkit](figma-toolkit.md)**<br>   
        Das Figma-Toolkit stellt die Ressourcen bereit, die zum Skizzieren und Layouten der Benutzeroberfläche verwendet werden können. Alle Benutzeroberflächensteuerelemente basieren auf den im MRTK verfügbaren Komponenten.
    :::column-end:::        
    :::column:::    
       [![Erlernen von Unity](../images/Final_unity_logo.png)](https://learn.unity.com/)<br>
        **[Erlernen von Unity](https://learn.unity.com/)**<br>
        Erfahren Sie, wie Sie mit Unity interaktive Erlebnisse erstellen können. Lernen durch Handeln, von Anfang bis Ende.
    :::column-end:::    
    :::column:::    
        [![Mixed Reality-Toolkit (MRTK)](images/74-12.png)](https://github.com/Microsoft/MixedRealityToolkit-Unity)<br>
        **[Mixed Reality-Toolkit (MRTK)](/windows/mixed-reality/mrtk-unity/)**<br>  
        Mit räumlicher Interaktion und Bausteinen für die Benutzeroberfläche starten Sie Ihren Mixed Reality-Entwurf und Ihre Entwicklung mit Unity.   
    :::column-end:::
    :::column:::    
        [![Microsoft Maquette](images/74-14.png)](https://www.maquette.ms/)<br>
        **[Microsoft Maquette](https://www.maquette.ms/)**<br>  
        Entwurf für VR. Microsoft Maquette gestaltet das räumliche Prototyping einfach, schnell und immersiv. 
    :::column-end:::    
:::row-end:::

<br>

---

### <a name="other-resources"></a>Weitere Ressourcen

:::row:::
    :::column:::
       [![Verstehen der Grundlagen](images/74-15.png)](../discover/get-started-with-mr.md#understand-the-basics)<br>
        **[Verstehen der Grundlagen](../discover/get-started-with-mr.md#understand-the-basics)**<br>
        Erhalten Sie ein besseres Verständnis dafür, was Mixed Reality ausmacht und wie es genutzt wird.
    :::column-end:::
    :::column:::
        [![Eine Veranstaltung besuchen](images/74-16.png)](../whats-new/sf-academy-events.md)<br>
         **[Eine Veranstaltung besuchen](../whats-new/sf-academy-events.md)**<br>
        Sehen Sie die Hardware, und lassen Sie sich durch ein praktisches Lernprogramm beim Erstellen Ihrer ersten HoloLens 2-Anwendung führen.
    :::column-end:::
    :::column:::
        [![Tools installieren](images/74-17.png)](../develop/install-the-tools.md)<br>
         **[Tools installieren](../develop/install-the-tools.md)**<br>
        Verwenden Sie die Checkliste für die Installation, um die erforderlichen Tools für die Erstellung von Apps für HoloLens und Mixed Reality zu erhalten.
    :::column-end:::
    :::column:::
        [![In die Entwicklung einsteigen](images/74-18.png)](../develop/development.md)<br>
        **[In die Entwicklung einsteigen](../develop/development.md)**<br>
        Wählen Sie auf der Grundlage Ihrer Kenntnissen, Ihres Arbeitsstils oder Ihrer Plattform einen Entwicklungspfad aus.
    :::column-end:::
:::row-end:::

<br>

<br>
