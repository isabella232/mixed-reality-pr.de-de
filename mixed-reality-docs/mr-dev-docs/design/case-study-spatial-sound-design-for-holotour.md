---
title: Fallstudie – Raumklangentwurf für HoloTour
description: Um eine wirklich immersive virtuelle 3D-Tour für Microsoft HoloLens zu erstellen, sind die beeindruckenden Videos und holografischen Landschaften nur Teil der Formel.
author: jsyltebo
ms.author: jsylte
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, HoloTour, räumlicher Sound, Fallstudie, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit, Audio
ms.openlocfilehash: b398ea7b3ddd85db85018da1852ed0c5ae410f625ff88bdda286e750a517d260
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196449"
---
# <a name="case-study-spatial-sound-design-for-holotour"></a>Fallstudie: Räumlicher Soundentwurf für HoloTour

Ansprechende Videos und holografische Landschaften sind nur Teil der Formel für eine immersive Microsoft HoloLens Tour. In diesem Artikel wird beschrieben, wie Sound verwendet wurde, damit Sie das Gefühl haben, dass Sie sich tatsächlich an jedem HoloTour-Standort befinden.

## <a name="the-tech"></a>Die Technologie

Die ansprechenden Bilder und holografischen Szenen, die In HoloTour zu sehen sind, sind nur ein Teil einer wahrnehmbaren Mixed Reality-Erfahrung. Obwohl Hologramme nur vor einem Benutzer angezeigt werden, können HoloLens [räumlichen Sound](spatial-sound.md) aus allen Richtungen bereitstellen, was eine umfassendere sensorische Erfahrung bietet.

Räumlicher Sound bietet Hinweise, um eine Richtung anzugeben, die der Benutzer drehen soll, oder um den Benutzer darüber zu informieren, dass es mehr Hologramme gibt, die in ihrem Raum angezeigt werden können. Wir können einen Sound auch direkt an ein Hologramm anfügen und kontinuierlich die Richtung und entfernung des Hologramms vom Benutzer aktualisieren. Diese Technik macht es so, als ob der Sound direkt von diesem Objekt stammt.

Für HoloTour wollten wir die räumlichen Soundfunktionen von HoloLens nutzen. Daher haben wir eine Umgebung mit 360 Grad erstellt, die mit dem Video synchronisiert wird, um die akustischen Highlights bestimmter Orte zu zeigen.

## <a name="behind-the-scenes"></a>Abläufe im Hintergrund

Wir haben HoloTour-Umgebungen von zwei verschiedenen Orten erstellt: Rome und Bed Sichte. Damit sich diese Sounds authentifikatorlich und überzeugend anfühlen, wollten wir Audio von den Orten erfassen, an denen wir gedreht haben, anstatt generische Sounds zu verwenden.

### <a name="capturing-the-audio"></a>Erfassen der Audiodaten

In unserer [Fallstudie zum Erfassen des visuellen Inhalts für HoloTour](../out-of-scope/case-study-capturing-and-creating-content-for-holotour.md)wird das Design unseres Kamerageräts besprochen. Es bestand aus 14 GoPro-Kameras in einem 3D-gedruckten Gehäuse, das für das Stativ entworfen wurde. Zum Erfassen von Audiodaten haben wir ein Quad-Mikrofonarray unterhalb der Kameras hinzugefügt. Der Sound wird in eine kompakte Aufzeichnungseinheit mit vier Kanälen an der Basis des Stativs eingespeist. Wir haben Mikrofone ausgewählt, die gut funktioniert haben, aber klein genug waren, um Beeinträchtigungen der Kameras zu vermeiden.

![Benutzerdefinierte Kamera und Mikrofonplattform](images/camera-rig-microphones-300px.png)<br>
*Benutzerdefinierte Kamera und Mikrofonplattform*

Dieses Setup erfasst Sound in vier Richtungen. Wir haben genügend Informationen aufgezeichnet, um ein 3D-aurales Panorama von räumlichem Sound zu erstellen, das später mit dem 360-Grad-Video synchronisiert werden konnte.

Eine Herausforderung des Audios des Kameraarrays besteht darin, dass Sie sich an der Aufnahme von Off-Camera-Sounds wie z.B. Rauschenen, Flugzeugen oder hohen Winden sind. Um sicherzustellen, dass wir alle benötigten Soundelemente hatten, haben wir mobile Stereo- und Mono-Aufzeichnungen verwendet, um asynchronen Ambient-Sound an bestimmten Points of Interest an jedem Ort zu erfassen. Diese Aufzeichnungen geben dem Sound-Designer sauberen Inhalt, um Interesse zu schaffen und die Direktionalität in der Postproduktion zu verbessern.

Jeder Erfassungstag generiert viele Dateien. Daher war es wichtig, ein System zu entwickeln, um nachzuverfolgen, welche Dateien einem bestimmten Ort oder einer kameraspezifischen Aufnahme entsprechen. Unsere Aufzeichnungseinheit wurde so eingerichtet, dass Dateien automatisch nach Datum und "Take"-Nummer benennen. Am Ende jedes Tages haben wir Dateien auf externen Laufwerken gesichert. Wir haben auch festgestellt, dass es wichtig ist, den Anfang der Audioaufzeichnungen zu vererzen. Diese Vorsichtsmaßnahme ermöglicht eine einfache kontextbezogene Identifizierung des Inhalts im Fall von Dateinamenproblemen. Es war auch wichtig, die Aufnahme des Kamerageräts visuell zu verfälschen, da das Video und die Audiodaten als separate Medien aufgezeichnet wurden und während der Nachbearbeitung synchronisiert werden mussten.

### <a name="editing-the-audio"></a>Bearbeiten der Audiodaten

Im Studio nach der Aufzeichnungsreise besteht der erste Schritt beim Zusammenbau einer richtungs- und immersiven Auralerfahrung darin, alle erfassten Audiodaten für einen Ort zu überprüfen. Wir wählen die besten Sätze aus und identifizieren Highlights, die während der Integration angewendet werden können. Die Audiodaten werden dann bearbeitet und bereinigt. Beispielsweise kann ein Fahrzeuggeiler, das etwa eine Sekunde dauert und mehrmals wiederholt wird, durch ein stilleres Umgebungsaudio aus derselben Aufzeichnungssitzung ersetzt werden.

Nachdem die Videobearbeitung für einen Speicherort festgelegt wurde, kann der Sound-Designer die entsprechenden Audiodaten synchronisieren. An diesem Punkt bewerten wir sowohl die Aufnahme von Kamerageräten als auch mobile Soundaufnahmen, um zu entscheiden, welche Elemente die beste immersive Audioszene erstellen würden. Es war hilfreich, alle Soundelemente in einen Audio-Editor zu integrieren und schnelle lineare Mockups zu erstellen, um mit verschiedenen Mischungsideen zu experimentieren. Dieser Schritt hat uns fundiertere Ideen gegeben, wann es an der Zeit war, die eigentlichen HoloTour-Szenen zu erstellen.

### <a name="assembling-the-scene"></a>Zusammenbau der Szene

Der erste Schritt zum Erstellen einer 3D-Ambient-Szene besteht darin, ein Bett mit allgemeinen Hintergrund-Ambient-Schleifensounds zu erstellen, die andere Features und interaktive Soundelemente in einer Szene unterstützen. Wir verfolgen einen ganzheitlichen Ansatz für die Implementierung, der durch die Entwurfskriterien für eine bestimmte Szene bestimmt wird. Einige Szenen können sich für die Verwendung der synchronisierten Kameraaufnahme indizieren. Für mehr "heiterische" Augenblicke ist möglicherweise ein zusammengestellter Ansatz erforderlich, der auf diskret platzierten Sounds, interaktiven Elementen und Musik basiert.

Bei der Indizierung der Kameraaufnahmeaudiodaten wurden raumklangfähige Umgebungsaudioemitter platziert, die der richtungsbezogenen Ausrichtung der Kameras entsprachen. Die Nordkameraansicht gibt Audiodaten aus dem Mikrofon "North" und ebenso für die anderen Kardinalrichtungen wieder. Diese Emitter sind weltweit gesperrt, was bedeutet, dass sich der Sound ändert, wenn Benutzer den Kopf drehen. Diese Technik modelliert effektiv den Ton des Stehens an dieser Position. Lauschen Sie sich bei Szenen, die eine gute Mischung aus von der Kamera erfassten Audiodaten verwenden, an Der Pantheon oder Dem Pantheon.

Bei einem anderen Ansatz wird manchmal eine Stereo-Schleifenentsprechung mit raumbezogenen Soundemittern wiedergegeben, die um die Szene herum platziert werden. Diese Emitter geben einmalige Sounds mit zufälliger Lautstärke, Tonhöhe und Triggerhäufigkeit wieder. Diese Technik sorgt für Stimmungen, die ein besseres Gefühl der Richtungsrichtung haben. In LoussAles können Sie z. B. hören, wie jeder Quadrant des Panoramas über bestimmte Emitter verfügt, die bestimmte Bereiche der Geografie hervorheben, aber zusammenarbeiten, um eine allgemeine immersive Stimmung zu schaffen.

## <a name="tips-and-tricks"></a>Tipps und Tricks

Es gibt noch weitere Möglichkeiten, die Richtungsrichtung hervorzuheben und die Immersion zu verbessern, um die räumlichen Soundfunktionen von HoloLens voll zu nutzen. Wir haben hier eine Liste bereitgestellt. Lauschen Sie beim nächsten HoloTour-Versuch auf diese Effekte.
* **Suchziele:** Diese Sounds werden ausgelöst, wenn Sie ein bestimmtes Objekt oder einen Bereich des holografischen Frames betrachten. Sehen Sie sich z. B. den straßenseitigen Dom in Roms "Dom-Navona" an, um Rauschen mit stark ausgelasteten Restaurants dezent auszulösen.
* **Lokales Sehen:** Die Reise durch HoloTour enthält bestimmte "Takte", bei denen Ihr Tourguide, unterstützt von Hologrammen, ein Thema ausführlich untersucht. Wenn z. B. die Fassade des Pantheon sich auflöst, um die Oculus zu erkennen, wird der Benutzer beim Hallen von Audiodaten, die als 3D-Emitter innerhalb des Pantheon platziert wurden, dazu aufgefordert, das Innere zu untersuchen.
* **Verbesserte Direktionalität:** Innerhalb vieler Szenen haben wir Sounds auf verschiedene Weise platziert, um die Richtungsrichtung zu erweitern. In der Pantheon-Szene wurde z. B. der Sound des Strahls als separater Emitter platziert, der dem Benutzer so nahe war, dass er ein Gefühl von "sonic parallax" erhalten konnte, während er durch den Spielbereich läuft. In der Maras-Szene von Maras wurden die Sounds einzelner kleiner Streams als separate Emitter platziert, um eine immersive umgebungsfreundlichere Umgebung zu erstellen, die den Benutzer mit den authentifikatorischen Tönen dieses Orts umgibt.
* **Spline-Emitter:** Diese Emitter bewegen sich im 3D-Raum basierend auf der visuellen Position des Objekts, an das sie angefügt sind. Ein Beispiel hierfür ist der Training in Dersser, bei dem wir einen Splineemitter verwendet haben, um ein eindeutiges Gefühl für Richtungs- und Bewegungsrichtung zu vermitteln.
* **Musik und SFX:** Bestimmte Aspekte von HoloTour, die einen stilisierteren oder holistischeren Ansatz darstellen, verwenden Musik- und Soundeffekte, um die emotionalen Auswirkungen zu erhöhen. Beispielsweise verwendet das Spiel am Ende der Rom-Tour spezielle Effekte wie Whooshes und Stingers, um die Wirkung von Bezeichnungen zu verstärken, die in den Szenen vorkommen.

## <a name="see-also"></a>Siehe auch

* [Raumklang](spatial-sound.md)
* [Raumklangentwurf](spatial-sound-design.md)
* [Raumklang in Unity](../develop/unity/spatial-sound-in-unity.md)
* [Video: Microsoft HoloLens: HoloTour](https://www.youtube.com/watch?v=pLd9WPlaMpY)
