---
title: The Making of Kippy es Escape
description: Lassen Sie sich bei der Entwicklung der Mixed Reality-Anwendung Escape von Kippy für HoloLens 2 Unreal Engine mit uns führen.
author: sw5813
ms.author: suwu
ms.date: 9/4/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Bereitstellen auf gerät, PC, Dokumentation, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
appliesto:
- HoloLens 2
ms.openlocfilehash: 353df2f2f5bc9a1d70fc354fd3014f10c0ba95d9
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757112"
---
# <a name="the-making-of-kippys-escape"></a>Das Machen von Kippys Escape
![Kippys Escape-Herobild](images/KippysEscape_1920.jpg)

Kippy der Roboter reaktiviert, um sich auf einer Insel zu finden. Es liegt an Ihnen, Ihre Problembehebung zu lösen, damit sie einen Pfad zurück zu ihrem Raketenangriff finden kann. Besen Sie sich [HoloLens 2,](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) und laden Sie die [](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) App aus dem Microsoft Store, oder klonen Sie das Repository von GitHub und holen Sie sich Kippy home safe!  

> [!IMPORTANT]
> Stellen Sie sicher, dass **Sie Unreal Engine 4.25** oder höher verwenden, wenn Sie Kippys Escape aus dem repository GitHub erstellen.

Kippys Escape ist eine [](/hololens/hololens2-hardware) Open-Source-HoloLens 2-Beispiel-App, die mit Unreal Engine 4 und Mixed Reality [UX Tools für Unreal erstellt wurde.](https://github.com/microsoft/MixedReality-UXTools-Unreal) In diesem Beitrag werden wir Sie durch unseren Prozess von den ersten Prinzipien und dem visuellen Entwurf bis hin zur Implementierung und Optimierung der Begehungserfahrungen gehen. Weitere Informationen zum Entwickeln von Mixed Reality mit MRTK-UX-Tools finden Sie in der [Unreal-Entwicklungsübersicht.](unreal-development-overview.md)

## <a name="download-app-from-microsoft-store-in-hololens-2"></a>Laden Sie die App Microsoft Store in HoloLens 2
Wenn Sie über HoloLens 2 verfügen, können Sie die App direkt herunterladen und auf Ihrem Gerät installieren.

<a href='//www.microsoft.com/store/apps/9nbd7gl86vkd?cid=storebadge&ocid=badge'><img src='https://developer.microsoft.com/store/badges/images/English_get-it-from-MS.png' alt='English badge' width="284px" height="104px" style='width: 284px; height: 104px;'/></a>


## <a name="first-principles"></a>Erste Prinzipien 

Unser Ziel bei der Erstellung von Kippys Escape war es, eine Umgebung zu erstellen, die die HoloLens 2-Unterstützung der [Unreal Engine,](https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html)die Funktionen von HoloLens 2 und das Mixed Reality Toolkit hervorheben würde. Wir wollten Entwickler dazu inspiriert, sich vorzustellen, was sie mit Unreal und HoloLens 2.  

Wir haben drei Leitprinzipien für die Erfahrung festgelegt: dass sie spaßig, interaktiv und eine niedrige Einstiegsbarriere haben muss. Wir wollten, dass die Benutzeroberfläche intuitiv genug ist, damit selbst ein erstmaliger Mixed Reality-Benutzer kein Tutorial benötigt, um es durchgehen zu können.  

## <a name="designing-the-game"></a>Entwerfen des Spiels 

Der HoloLens 2 hat Zugriff auf Designfeatures, die heutzutage noch nicht im Spiele-Bereich gefunden wurden. Objekte können direkt mit ihren Händen oder per Eyetracking per Push oder manipulationsgefeilt werden. Diese wichtigen Features befinden sich hinter einigen Derzmomenten, die wir in Kippys Escape erstellt haben.  

Mithilfe der HoloLens 2 Features als Leitfaden für unser Spieldesign haben wir einige kleine Umgebungsszenarien beschrieben. Inseln waren sinnvoll, da sie an verschiedene Spielerhöhen angepasst werden können, und boten einige unterschiedliche Brückenideen. Wir haben uns mit dem Thema "Science-Science-Technologie" und dem Thema "2017" und "Sci-Fi-Technologie" mit der Idee ausdingt, dass jemand Maschinen über Denkanlagen mit einer ungewöhnlichen Energie aus jeder Insel erstellt hat. Die Inseln haben jeweils ein eigenes Aussehen und Gefühl erhalten, ein Detail, das dazu beigeholen hat, visuelles Interesse zu schaffen. Ein gutes Gleichgewicht zwischen Modellierung und Texturierung würde zeichnen-Aufrufe für die Renderingleistung niedrig halten, sodass ein stilisiertes Design vor diesem Hintergrund entworfen wurde. 

![Frühe Spielentwurfs skizziert ](images/kippys-escape/kippys-escape-img-01.png)
 *Einige frühe Sketche, wie die Erfahrung aussehen könnte*

![Renderings der zweiten Insel ](images/kippys-escape/kippys-escape-img-02.png)
 *Renderings der zweiten Insel*

Um unseren kurzen Produktionszeitplan einzuhalten, stimmten wir zu, dass ein Gleitkomma ohne strenge Animationszyklen Absichten und Emotionen erfassen kann. Und so wurde Kippy zur Welt gekommen! Sie emuliert einige verschiedene Ausdrücke durch die Augen und durch die topathischen Soundeffekte, um den Spieler während der gesamten Erfahrung zu unterstützen. 

![Kippy mit verschiedenen Ausdrücken über die Augen](images/kippys-escape/kippys-escape-img-03.gif)

*Kippy mit verschiedenen Ausdrücken über die Augen*

![Wenn der Benutzer zu lange dauert, um ein Problem zu lösen, gibt Kippy dem Benutzer einen Hinweis.](images/kippys-escape/kippys-escape-img-04.gif)

*Wenn der Benutzer zu lange dauert, um ein Problem zu lösen, gibt Kippy dem Benutzer einen Hinweis.*

Über den Zeichen- und Umgebungsentwurf hinaus haben wir uns sehr um das Spiel gespürt. Eyetracking ermöglichte es uns, Material- und Soundattribute zu deaktivieren, die wichtige Teile des Spiels hervorgehoben haben. Räumliche Audiodaten haben dazu beigetragen, dass sich die Ebenen in der Umgebung des Players zu Hause anfühlten. Die Möglichkeit, Objekte zu greifen, Schaltflächen zu drücken und Schieberegler zu bearbeiten, fördert innovative Spielerbindungen. Es war wichtig sicherzustellen, dass diese Verbindungspunkte natürlich sind. 

![Das Ende des Brückenkabels leuchtet, wenn sich die Hand des Benutzers dem Kabel nähert.](images/kippys-escape/kippys-escape-img-05.gif)

*Das Ende des Brückenkabels leuchtet, wenn sich die Hand des Benutzers dem Kabel nähert.*

## <a name="building-the-game-mechanics"></a>Erstellen der Spielmechanismen 

Kippys Escape basiert stark auf Mixed Reality UX Tools-Komponenten, um das Spiel interaktiv zu gestalten– nämlich Handinteraktions-Actors, Begrenzungssteuerelemente, Manipulatoren, Schieberegler und Schaltflächen.   

Der [Handinteraktionsakteur](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/HandInteraction.html) ermöglicht sowohl die direkte als auch die ferne Manipulation von Hologrammen. Zu Beginn von Kippys Escape erhält der Benutzer die Möglichkeit, den Speicherort des Spiels zu festlegen. Handbalken, die sich von der Handfläche des Benutzers erstrecken, machen es einfach, große Hologramme zu bearbeiten, die weit entfernt sind, wie im gif unten zu sehen.  

![Handinteraktionsakteur GIF](images/kippys-escape/kippys-escape-img-06.gif)

Die Platzhalterszene selbst kann mithilfe der Begrenzungssteuerungskomponente von UX Tools [gezogen und gedreht](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/BoundsControl.html) werden.  

Auf der zweiten Insel muss der Benutzer Gems auswählen und in den entsprechenden Slots platzieren. An die Gems [sind Manipulatoren](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Manipulator.html) angefügt, die es dem Benutzer ermöglichen, sie hoch- und abzuordnen. 

![Manipulatorbeispiel gif](images/kippys-escape/kippys-escape-img-07.gif)

Eine [druckbare Schaltfläche](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/PressableButton.html) ist der Schlüssel zum Aufbringen von Knopfen für die Verwendung auf der dritten Insel.  

![Beispiel für eine bedruckbare Schaltfläche gif](images/kippys-escape/kippys-escape-img-08.gif)

Auf [der vierten Insel](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/PinchSlider.html) wird eine Schiebereglerkomponente angezeigt, die auslöst, dass die letzte Brücke ausgelöst wird.  

![Beispiel für Schiebereglerkomponente gif](images/kippys-escape/kippys-escape-img-09.gif) 

## <a name="optimizing-for-hololens-2"></a>Optimieren für HoloLens 2 

Bei jeder Erfahrung, die für die Ausführung auf einem mobilen Gerät erstellt wurde, ist es wichtig, die Leistung im Auge zu behalten. Unreal 4.25 enthält ein wichtiges Update zur Unterstützung mobiler Mehrfachansichten, das den Renderingaufwand erheblich reduziert und die Bildfrequenz erhöht. Es wird empfohlen, unsere anderen [empfohlenen Leistungseinstellungen](performance-recommendations-for-unreal.md) für HoloLens 2 entwicklung mit Unreal zu überprüfen, wenn Sie die Optimierung vornehmen.  

Physikalische Objekte bleiben weiterhin kostenintensiv für die Leistung, sodass einige clevere Problemumgehungen verwendet wurden. Für die dritte "Brücke" ist es beispielsweise erforderlich, eine gewisse Blockierung der Sperre zu beseitigen. Anstatt eine Force-Impact-Auswirkung auf die Steine als physikalische Objekte zu haben, löst die Detonation einen Tausch aus und schaltt die statische Rausche um, um einen explodierenden Partikeleffekt zu erzielen. 

![Optimiertes Beispiel für HoloLens 2 GIF](images/kippys-escape/kippys-escape-img-10.gif) 

Wir haben auch unsere Zeichnen-Aufrufe von über 400 auf ~260 gekürzt, indem wir: 
* Reduzieren der Gitternetzkomplexität
* Kombinieren von Gitternetzen
* Entfernen einiger unserer anfänglichen dynamischen Beleuchtungselemente

Wir hätten wahrscheinlich mehr tun können, aber wir waren der Ansicht, dass ein gutes Gleichgewicht zwischen Leistung und visueller Qualität besteht.  

## <a name="try-it-out"></a>Probieren Sie es aus! 

Starten Sie Ihre [HoloLens 2,](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) und laden Sie die App aus [](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) dem Microsoft Store herunter, oder klonen Sie das Repository aus GitHub und erstellen Sie die App selbst!  

## <a name="about-the-team"></a>Informationen zum Team

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Jack Caron" width="60" height="60" src="images/kippys-escape/jack-caron.jpg"></td>
<td style="border-style: none"><b>Jack Caron</b><br><i>Lead Game Designer</i><br>Jack arbeitet derzeit an Mixed Reality-Funktionen für Microsoft, einschließlich HoloLens 2-Projekten und AltspaceVR und war zuvor designer im HoloLens-Plattformteam.</td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Summer Wu" width="60" height="60" src="images/kippys-escape/summer-wu.jpg"></td>
<td style="border-style: none"><b>Sommer Wu</b><br><i>Producer</i><br>Der Sommer arbeitet auf der Mixed Reality-Entwicklerplattform und leitet die Unreal Engine-bezogenen Bemühungen des Teams.</td>
</tr>
</table>

Besonderer Dank an unsere Freunde bei [Framestore,](https://www.framestore.com/) die uns dabei helfen, Kippys Escape zum Leben zu bringen. Von der Zeichenentwicklung über das Assetdesign bis zur Spieleprogrammierung war die Zusammenarbeit an diesem Projekt entscheidend.