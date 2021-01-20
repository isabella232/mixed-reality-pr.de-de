---
title: Das Erstellen von Kippy-Escapezeichen
description: Sehen Sie sich die folgenden Informationen an, während wir die Erstellung der "Kippy"-Escapezeichen Mixed Reality-Anwendung für hololens 2 in der Unreal Engine erkunden.
author: sw5813
ms.author: suwu
ms.date: 9/4/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, hololens, hololens 2, Mixed Reality, bereitstellen auf Geräten, PCs, Dokumentationen, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
appliesto:
- HoloLens 2
ms.openlocfilehash: 7302e6c8d5de866b652ec4741fbef128eca616e0
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580817"
---
# <a name="the-making-of-kippys-escape"></a>Das Erstellen von Kippy-Escapezeichen

Kippy der Roboter wird reaktiviert, um sich auf einer Insel zu finden. Es liegt an Ihnen, dass Sie sich mit dem Problem lösen können, dass Sie einen Pfad zurück zu seiner raketenlieferung finden! Halten Sie Ihre hololens 2 an, und [Laden Sie die APP](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) aus dem Microsoft Store herunter, oder Klonen Sie das [Repository](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) von GitHub, und holen Sie sich Kippy Home Safe!  

> [!IMPORTANT]
> Stellen Sie sicher, dass Sie **Unreal Engine 4,25 oder** höher verwenden, wenn Sie Kippy-Escapezeichen aus dem GitHub-Repository erstellen.

Die Escapezeichen-Escapesequenz ist eine Open Source-Beispiel-App mit [hololens 2](/hololens/hololens2-hardware) für Unreal Engine 4 und [Mixed Reality UX Tools für Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal). In diesem Beitrag wird der Prozess von den ersten Prinzipien und dem visuellen Entwurf bis hin zur Implementierung und Optimierung der-Funktion erläutert. Weitere Informationen zum entwickeln gemischter Reality-Anwendungen mit mrtk-UX-Tools finden Sie in der [Übersicht über die Unreal-Entwicklung](unreal-development-overview.md).

## <a name="first-principles"></a>Erste Prinzipien 

Beim Einrichten der Escapezeichen-Escapesequenz war unser Ziel das Erstellen einer Umgebung, die den [hololens 2-Support von Unreal Engine](https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html), die Funktionen von hololens 2 und das Mixed Reality Toolkit hervorhebt. Wir wollten Entwicklern vorstellen, was Sie mit Unreal und hololens 2 erstellen konnten.  

Wir haben drei Leitlinien für die-Funktion veröffentlicht: Es musste Spaß und interaktiv sein, und es ist eine geringe Barriere für die Eingabe erforderlich. Wir wollten, dass die Benutzeroberflächen intuitiv genug sind, dass auch ein erst maligerweise gemischter Reality-Benutzer kein Tutorial benötigt, um es durchzugehen.  

## <a name="designing-the-game"></a>Entwerfen des Spiels 

Hololens 2 hat heute Zugang zu Design Features, die noch nicht im Spiel spielen. Objekte können mithilfe ihrer Hände direkt per pushübertragung oder mit der Augen Verfolgung manipuliert werden. Diese wichtigen Features befinden sich hinter einigen der Spaß Zeiten, die wir in Kippy-Escapezeichen entwickelt haben.  

Mithilfe der einzigartigen hololens 2-Features als Leitfaden für den Spiel Entwurf haben wir einige kleine Umgebungs Szenarien erweitert. Inseln sind sinnvoll, da Sie für verschiedene Player Höhen angepasst werden können und einige unterhaltsame Brücken Ideen bereitgestellt haben. Wir haben uns auf das Design der antiken Zivilisation ausgewirkt, das auf die Technologie von Sci-Fi trifft, mit der Idee, dass jemand einen Mechanismus über Ruinen erstellt hat, der eine seltsame Energie für jede Insel nutzt. Die Inseln erhielten jeweils ein eigenes Erscheinungsbild, ein Detail, das bei der Erstellung von visuellem Interesse half. Ein ausgewogenes Gleichgewicht zwischen Modellierung und Texturierung würde zu einer geringen Darstellung von Zeichnungs aufrufen für die Renderingleistung führen, sodass ein stilisiertes Aussehen mit dem Hintergrund entworfen wurde. 

![Der frühe Spiel Entwurf skizziert ](images/kippys-escape/kippys-escape-img-01.png)
 *einige frühe Skizzen für das Aussehen der* Darstellung.

![Renderings der zweiten Insel ](images/kippys-escape/kippys-escape-img-02.png)
 *Renderings der zweiten Insel*

Um den kurzen Produktions Zeitplan beizubehalten, haben wir uns zugestimmt, dass ein unverankertes Zeichen Absicht und Emotionen ohne strenge Animations Zyklen erfassen könnte. Und daher wurde Kippy! Es werden einige unterschiedliche Ausdrücke durch die Augen und durch minimalistische, stimmungsvolle Klänge optimiert, die den Player im Laufe der Umgebung unterstützen. 

![Kippy zeigt unterschiedliche Ausdrücke über die Augen](images/kippys-escape/kippys-escape-img-03.gif)

*Kippy zeigt unterschiedliche Ausdrücke über die Augen*

![Wenn der Benutzer zu lange braucht, um ein Rätsel zu beheben, gibt Kippy dem Benutzer einen Hinweis.](images/kippys-escape/kippys-escape-img-04.gif)

*Wenn der Benutzer zu lange braucht, um ein Rätsel zu beheben, gibt Kippy dem Benutzer einen Hinweis.*

Über den Zeichen-und Umgebungs Entwurf hinaus haben wir einen konzertierten Aufwand unternommen, um das Spiel Spaß zu machen. Mit der Augen Verfolgung konnten wir Material-und audioattribute auslösen, die die wichtigsten Teile des Spiels hervorgehoben haben. Mit räumlichem Audioinhalt können die Ebenen zu Hause in der Umgebung des Players werden. Durch das Erfassen von Objekten, durch Drücken von Schaltflächen und das Bearbeiten von Schiebereglern werden innovative Player Engagements gesteuert. Es war wichtig, sicherzustellen, dass diese Verbindungspunkte in natürlicher Bedeutung waren. 

![Das Ende des Brücken Kabels wird ausgeblendet, wenn der Benutzer die Hand anspricht.](images/kippys-escape/kippys-escape-img-05.gif)

*Das Ende des Brücken Kabels wird ausgeblendet, wenn der Benutzer die Hand anspricht.*

## <a name="building-the-game-mechanics"></a>Entwickeln der Spielmechanik 

Der Escapezeichen-Escapezeichen basiert stark auf den Komponenten der Mixed Reality-UX-Tools, um das Spiel interaktiv zu gestalten, d.h. Hand Interaktionen, Steuerelemente, Manipulatoren, Schieberegler und Schaltflächen.   

Der [Actor für die Hand Interaktion](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/HandInteraction.html) ermöglicht die direkte und lange Bearbeitung von holograms. Zu Beginn der "Kippy"-Escapesequenz erhält der Benutzer die Möglichkeit, den Speicherort des Spiels festzulegen. Hand Balken, die sich aus der Benutzer Palme erstrecken, erleichtern es Ihnen, große Hologramme zu bearbeiten, die weit entfernt sind, wie im folgenden GIF dargestellt.  

![Hand Interaktion Actor GIF](images/kippys-escape/kippys-escape-img-06.gif)

Die Platzhalter Szene selbst kann mithilfe der [bounds-Steuerungs](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/BoundsControl.html) Komponente der UX-Tools gezogen und gedreht werden.  

Auf der zweiten Insel muss der Benutzer Edelsteine abrufen und in den entsprechenden Slots platzieren. In den Edelsteinen sind [Manipulatoren](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/Manipulator.html) angefügt, die es dem Benutzer ermöglichen, diese auszuwählen und zu platzieren. 

![Manipulatorbeispiel GIF](images/kippys-escape/kippys-escape-img-07.gif)

Eine [Schaltfläche](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/PressableButton.html) , die Sie verwenden können, ist der Schlüssel, um Bomben zur Verwendung auf der dritten Insel aufzubringen.  

![Beispiel für eine Schaltfläche zum Komprimieren](images/kippys-escape/kippys-escape-img-08.gif)

Auf [](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/PinchSlider.html) der vierten Insel wird eine Schiebereglerkomponente angezeigt, die die endgültige Bridge auslöst, die ausgelöst werden soll.  

![Beispiel für Schieberegler-Komponente GIF](images/kippys-escape/kippys-escape-img-09.gif) 

## <a name="optimizing-for-hololens-2"></a>Optimieren von hololens 2 

Mit jeder für die Ausführung auf einem mobilen Gerät erstellten Darstellung ist die Leistung kritisch. Unreal 4,25 enthält ein wichtiges Update zur Unterstützung mobiler MultiView-Funktionen, wodurch der renderingaufwand erheblich reduziert und die Framerate erhöht werden. Wir empfehlen Ihnen, die anderen [empfohlenen Leistungseinstellungen](performance-recommendations-for-unreal.md) für die hololens 2-Entwicklung mit Unreal zu prüfen, wenn Sie optimieren.  

Die Leistung von Physik Objekten bleibt weiterhin teuer, daher wurden einige clevere Problem Umgehungen verwendet. Beispielsweise erfordert die dritte "Bridge" das Aufblasen einiger Trümmer, die die Treppe blockieren. Anstatt eine Force als Physik Objekte zu verwenden, löst die Bomben-Detonation einen Austausch aus und schaltet die statischen Steine auf einen explodierenden Partikeleffekt. 

![Optimiertes Beispiel für hololens 2 GIF](images/kippys-escape/kippys-escape-img-10.gif) 

Wir haben auch unsere Draw-Aufrufe von über 400 bis ~ 260 durch Folgendes reduziert: 
* Reduzieren der Mesh-Komplexität
* Kombinieren von Netzen
* Entfernen einiger unserer anfänglichen dynamischen Beleuchtungselemente

Obwohl es wahrscheinlich noch mehr möglich wäre, wäre es ein gutes Gleichgewicht zwischen Leistung und visueller Qualität.  

## <a name="try-it-out"></a>Probieren Sie es aus! 

Starten Sie die hololens 2, und laden Sie die APP aus dem Microsoft Store [herunter](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) , oder Klonen Sie das [Repository](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) von GitHub, und erstellen Sie die APP selbst.  

## <a name="about-the-team"></a>Informationen zum Team

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Jack Caron" width="60" height="60" src="images/kippys-escape/jack-caron.jpg"></td>
<td style="border-style: none"><b>Jack Caron</b><br><i>Lead Spiel-Designer</i><br>Jack funktioniert derzeit in gemischten Umgebungen für Microsoft, einschließlich hololens 2-Projekten und altspacevr, und war zuvor ein Designer des hololens Platform-Teams.</td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Summer Wu" width="60" height="60" src="images/kippys-escape/summer-wu.jpg"></td>
<td style="border-style: none"><b>Sommer Wu</b><br><i>Producer</i><br>Der Sommer arbeitet auf der Mixed Reality-Entwicklerplattform und leitet die Unreal Engine-bezogenen Anstrengungen des Teams ein.</td>
</tr>
</table>

Vielen Dank an unsere Freunde bei [Framestore](https://www.framestore.com/) , um uns dabei zu unterstützen, das Escapezeichen in den Leben zu bringen. Von der Zeichen Entwicklung bis hin zum Asset-Design und zur Spielprogrammierung war die Zusammenarbeit mit diesem Projekt entscheidend.