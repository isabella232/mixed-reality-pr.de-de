---
title: Skalieren
description: Ein wichtiger Aspekt bei der realistischen Wirkung von holografisch dargestellten Inhalten ist das möglichst genaue Nachahmen der visuellen Statistik der echten Welt.
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Stil, Design, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, Skalierung, Hologramme
ms.openlocfilehash: 0b643b7f4b53795afa6bac9b54e55565233ac1d96a6a58d5389a8a4b7db8d7cc
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223006"
---
# <a name="scale"></a>Skalieren

Der Schlüssel zum Anzeigen realistischer holografischer Inhalte besteht darin, die visuellen Statistiken der realen Welt so genau wie möglich zu imitieren. Integrieren Sie visuelle Hinweise, damit Benutzer in der praxisorientierten Welt verstehen können, wo sich Objekte befinden, wie groß sie sind und woraus sie bestehen. Die Skalierung eines Objekts ist einer der wichtigsten visuellen Hinweise, da es dem Betrachter ein Gefühl für die Größe der Objekte und Hinweise zu seiner Position gibt. Darüber hinaus ist das Anzeigen von Objekten in großem Maßstab einer der wichtigsten Unterscheidungsmerkmale für Mixed Reality im Allgemeinen – etwas, das bei der vorherigen bildschirmbasierten Anzeige nicht möglich war.

<br>

---

## <a name="how-to-suggest-the-scale-of-objects-and-environments"></a>Vorschlagen der Skalierung von Objekten und Umgebungen

Es gibt viele Möglichkeiten, die Skalierung eines Objekts vorzuschlagen, von denen einige mögliche Auswirkungen auf andere Wahrnehmungsfaktoren haben. Der wichtigste Schritt besteht darin, Objekte in einer "echten" Größe anzuzeigen und diese realistische Größe beizubehalten, wenn sich Benutzer bewegen. Hologramme nimmt einen anderen visuellen Winkel eines Benutzers in Anspruch, wenn er sich näher oder weiter entfernt, genauso wie echte Objekte.

### <a name="use-the-distance-of-objects-as-theyre-presented-to-the-user"></a>Verwenden der Entfernung von Objekten, wie sie dem Benutzer angezeigt werden

Eine gängige Methode besteht darin, die Entfernung von Objekten zu verwenden, wie sie dem Benutzer angezeigt werden. Erwägen Sie beispielsweise, ein großes Familienauto vor dem Benutzer zu visualisieren. Wenn sich das Auto innerhalb der Länge des Arms direkt davor befindet, wäre es zu groß, um in das Sichtfeld des Benutzers zu passen. Schließende Objekte erfordern, dass der Benutzer kopf- und textbewegt ist, um die Gesamtheit des Objekts zu verstehen. Wenn das Auto weiter entfernt (im Raum) platziert wird, kann der Benutzer ein Gefühl der Skalierung schaffen, indem er das gesamte Objekt in seiner Ansichtsansicht sieht. Benutzer könnten sich dann näher an das Objekt bewegen, um eine ausführlichere Überprüfung zu ermöglichen.

:::row:::
    :::column:::
        **[Dieses Verfahren wurde verwendet, um eine Oberfläche](https://www.youtube.com/watch?v=DilzwF90vec)** für ein neues Auto zu schaffen, indem die Skala des holografischen Autos für den Benutzer realistisch und intuitiv gehalten wurde. Die Erfahrung beginnt mit dem Fahrzeug hologramm auf einer physischen Tabelle, sodass der Benutzer die Gesamtgröße und Form des Modells verstehen kann. Später wird das Fahrzeug auf eine Skala erweitert, die über die Größe des Anzeigefelds des Geräts hinausgeht. Da der Benutzer bereits einen Bezugsrahmen vom kleineren Modell erhalten hat, kann er angemessen durch die Features des Autos navigieren.<br>
        <br>
        *Abbildung: Autos-Benutzeroberfläche für HoloLens*
    :::column-end:::
        :::column:::
       ![Autos-Benutzeroberfläche für HoloLens](images/volvo-cars-microsoft-hololens-experience01-640px.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---

### <a name="use-holograms-to-modify-the-users-real-space"></a>Verwenden von Hologrammen zum Ändern des realen Raumes des Benutzers

Eine andere Methode besteht darin, Hologramme zu verwenden, um den realen Raum des Benutzers zu ändern, die vorhandenen Wände oder Decken durch Umgebungen zu ersetzen oder "Löcher" oder "Fenster" anzufügen. Dadurch können Objekte mit überdimensioniertem Format scheinbar den physischen Raum "durchbrechen". Beispielsweise passt eine große Struktur möglicherweise nicht in die Lebensräume der meisten Benutzer, aber wenn sie einen virtuellen Sky an der Obergrenze setzen, wird der physische Raum in den virtuellen Raum erweitert. Dies ermöglicht es dem Benutzer, die Basis der virtuellen Struktur zu umgehen und ein Gefühl für Skalierung und reale Darstellung zu sammeln. Benutzer können dann nachschlagen, um zu sehen, dass sie weit über den physischen Raum des Raumes hinausgehen.

:::row:::
    :::column:::
        **[Minecraft ein Konzept mit](https://minecraft.net/)** einer ähnlichen Technik entwickelt. Durch Hinzufügen eines virtuellen Fensters zu einer physischen Oberfläche werden die vorhandenen Objekte im Raum im Kontext einer deutlich größeren Umgebung platziert, die über die physischen Skalierungseinschränkungen des Raumes hinausgeht.<br>
        <br>
        *Abbildung: Minecraft Konzept für HoloLens*
    :::column-end:::
        :::column:::
       ![Minecraft Konzepterfahrung für HoloLens](images/800px-minecraftwindow-640px.jpg)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="experimenting-with-scale"></a>Experimentieren mit Skalierung

Designer haben mit dem Ändern der Skala experimentiert, indem sie die angezeigte "echte" Größe des Objekts geändert haben. Gleichzeitig behalten sie eine einzelne Objektposition bei, um ein Objekt anzunähern, das sich ohne tatsächliche Bewegung zum Viewer bewegt. Dies wurde in einigen Fällen als Möglichkeit getestet, um die Nahaufnahme von Elementen zu simulieren und gleichzeitig potenzielle Komforteinschränkungen beim Anzeigen virtueller Inhalte zu berücksichtigen, die näher an der "Komfortzone" liegen würden.

Dies kann jedoch einige mögliche Artefakte in der Benutzeroberfläche erstellen:
* Bei virtuellen Objekten, die ein Objekt mit einer "bekannten" Größe für den Viewer darstellen, führt das Ändern der Skala ohne Änderung der Position zu in Konflikt stehenden visuellen Hinweisen. Die Augen "sehen" das Objekt möglicherweise immer noch in einer bestimmten Tiefe aufgrund von Füssigkeitshinweisen. Weitere Informationen finden Sie im Artikel [Komfort.](comfort.md) Die Größe fungiert als monokularer Hinweis, dass das Objekt näher kommt. Diese widersprüchlichen Hinweise führen zu verwirrenden Wahrnehmungen– Betrachter sehen das Objekt häufig als unverändert (aufgrund des konstanten Tiefenhinweises), wachsen aber schnell.
* In einigen Fällen wird eine Skalierungsänderung stattdessen als "abwegiger" Hinweis angesehen, bei dem das Objekt von einem Viewer möglicherweise oder nicht erkannt wird, um die Skalierung zu ändern, aber scheinbar direkt zu den Augen des Betrachters bewegt wird (was ein Rädchen sein kann).
* Bei Vergleichsoberflächen in der realen Welt werden solche Skalierungsänderungen manchmal als Änderung der Position entlang mehrerer Achsen betrachtet– Objekte scheinen niedriger zu fallen, anstatt sich näher zu bewegen (in einigen Fällen ähnlich in einer 2D-Projektion von 3D-Bewegungen).
* Für Objekte ohne bekannte "reale" Größe (z. B. beliebige Formen mit beliebigen Größen, Benutzeroberflächenelementen usw.) kann das Ändern der Skalierung funktional als Möglichkeit dienen, Entfernungsänderungen zu imitieren. Viewer verfügen nicht über so viele vorab vorhandene Top-Down-Hinweise, um die tatsächliche Größe oder Position des Objekts zu verstehen, sodass die Skalierung als wichtigere Hinweise verarbeitet werden kann.

<br>

---

## <a name="see-also"></a>Siehe auch
* [Farbe, Licht und Materialien](./color-light-and-materials.md)
* [Typografie](typography.md)
* [Raumklangentwurf](spatial-sound-design.md)