---
title: Fallstudie– Verwenden von Raumklang in RoboRaid
description: Räumlicher Sound ist eines der interessantesten Features von Microsoft HoloLens, mit denen Benutzer erkennen können, was um sie herum passiert, wenn Objekte nicht mehr in Sicht sind.
author: mattzmsft
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, RoboRaid, Raumklang, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit, CPU
ms.openlocfilehash: f4a47fe119dffbd32d264cc8e21ae2b3ade7cfcccef8e7e18fbb4491783d0542
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208998"
---
# <a name="case-study---using-spatial-sound-in-roboraid"></a>Fallstudie– Verwenden von Raumklang in RoboRaid

In diesem Artikel werden die Herausforderungen Microsoft HoloLens Experience Team beim Erstellen von Audiodaten für den [RoboRaid](https://www.microsoft.com/p/roboraid/9nblggh5fv3j) Mixed Reality-First-Person-Moderator beschrieben.

## <a name="the-tech"></a>Die Technologie

[Räumlicher](spatial-sound.md) Sound ist eines der interessantesten Features von Microsoft HoloLens, bei dem Benutzer erkennen können, was um sie herum passiert, wenn sich Objekte nicht in der Sichtlinie befinden.

In RoboRaid besteht die offensichtlichste und effektivste Verwendung von raumbezogenem Sound in der Warnung des Spielers, dass etwas außerhalb des Peripheriebilds geschieht. Der Breacher kann z. B. von jeder gescannten Wand im Raum eingeben. Wenn Der Ort, an dem er sich befindet, nicht zu sehen ist, wird er möglicherweise übersehen. Um Sie über diese Warnung zu informieren, hören Sie ein bestimmtes Audio, das von dem Ort kommt, an dem der Breacher eintritt, was Sie darüber informiert, dass Sie schnell reagieren müssen, um ihn zu beenden.

## <a name="behind-the-scenes"></a>Abläufe im Hintergrund

Das Erstellen von raumbezogenem Sound für HoloLens-Apps ist so neu und einzigartig, dass Probleme schwierig zu lösen sein können, da es keine früheren Projekte gibt, auf die verwiesen werden kann. Hoffentlich helfen Ihnen diese Beispiele für die Audioherausforderungen, die wir beim Erstellen von RoboRaid bewältigen mussten, Ihnen beim Erstellen von Audiodaten für Ihre eigenen Apps.

### <a name="be-mindful-of-taxing-the-cpu"></a>Beachten Sie, dass sie die CPU-Auslastung steuern müssen.

Räumlicher Sound kann für die CPU sehr anspruchsvoll sein. Für eine ausgelastete Erfahrung wie RoboRaid war es entscheidend, die Anzahl der Raumklanginstanzen zu einem bestimmten Zeitpunkt auf unter acht zu halten. In der Regel war es so einfach wie das Festlegen des Grenzwerts für Instanzen für verschiedene Audioereignisse. Alle Instanzen, die nach Erreichen des Grenzwerts geschehen, werden nicht mehr möglich. Wenn beispielsweise Drohnen spucken, sind ihre Drohnen zu einem bestimmten Zeitpunkt auf drei Instanzen beschränkt. Wenn nur etwa vier Drohnen gleichzeitig gezischt werden können, sind drei 1000 Töne ausreichend, da ihr Gehirn diese vielen ähnlich klingenden Audioereignisse nicht nachverfolgen kann. Dadurch wurden Ressourcen für andere Raumklangereignisse frei, z. B. für ungnische Explosionen oder für die Vorbereitung auf die Heiterung.

### <a name="rewarding-a-successful-dodge"></a>Belohnung für eine erfolgreiche Dodge

Die Dodging-Mechanik ist eine der wichtigsten Spielmechaniken in RoboRaid, und auch etwas, das wir als einzigartig für die HoloLens haben. Daher wollten wir erfolgreiche Dodges für den Spieler sehr besingend machen. Wir haben das Doppler-"Whizz-by" zu beginn der Entwicklung ziemlich überzeugend klingen lassen. Ursprünglich war mein Plan, eine Schleife zu verwenden und in Echtzeit mithilfe von Lautstärke, Tonhöhe und Filter zu bearbeiten. Die Implementierung dafür sollte sehr ausführlich sein. Bevor wir Ressourcen für die Erstellung dieses Erstellens committet haben, haben wir einen kostengünstigen Prototyp mithilfe eines Assets erstellt, in dem der Doppler-Effekt gebacken wurde, um herauszufinden, wie es sich entwickelt hat. Unser talentierter Entwickler hat es so gemacht, dass dieses Whizz-by-Asset genau 0,7 Sekunden zurückklang, bevor das Projektil am Nasen des Spielers übergeben wurde und die Ergebnisse toll waren! Selbstverständlich haben wir die komplexere Lösung verdringt und den Prototyp implementiert.

*(Weitere Informationen zum Erstellen eines Audio asset mit integriertem Doppler-Effekt finden Sie unter [100 Whooshes in 2 Minutes](http://designingsound.org/2010/02/26/charles-deenen-special-100-whooshes-in-2-minutes/).)* 
<br>
![Die erfolgreiche Doddierung des Projektils eines Lässig-Spielers honoriert den Spieler mit einem zufriedenstellenden Whizz-by-Sound.](images/successful-dodge-roboraid-500px.jpg)

### <a name="ditching-ineffective-sounds"></a>Ineffektive Verdringungsgeräusche

Ursprünglich wollten wir hinter dem Spieler einen Explosionssound wieder geben, nachdem er das 1000-Projektil erfolgreich ausgelassen hat, aber wir entschieden uns aus verschiedenen Gründen, dies zu verdringen. Erstens hat es sich nicht so effektiv an gefühlt wie das Whizz-by-SFX, das wir für den Dodge verwendet haben. Wenn das Projektil auf eine Wand hinter Ihnen trifft, wäre im Spiel etwas anderes passiert, das diesen Sound maskieren würde. Zweitens: Es gab keine Kollision auf dem Boden, sodass wir die Explosion nicht zum Spielen bekommen konnten, wenn das Projektil auf den Boden anstatt auf die Wände trifft. Und schließlich gab es die CPU-Kosten für räumlichen Sound. Die (in der Wand durchforstungsgeforstete)ItrigeItäre von Denen hat einen speziellen Angriff, der etwa acht Projektile versiert. Dies führte nicht nur zu einem großen Durcheinander in der Mischung, sondern führte auch zu einer beschämenden Kniffe, da die CPU zu stark getroffen wurde.

### <a name="communicating-a-hit"></a>Kommunizieren eines Treffers

Ein interessantes Problem, auf das wir HoloLens, war, wie schwierig es war, effektiv zu kommunizieren, dass ein Spieler getroffen wurde. Was eine Mixed Reality-Erfahrung erfolgreich macht, ist das Gefühl, dass ihnen die Geschichte passiert. Das bedeutet, dass Sie der Meinung sein müssen, dass Sie in Ihrem eigenen Zimmer gegen einen roboterartigen Roboter anknirden.

Spieler werden offensichtlich nichts fühlen, wenn sie getroffen werden, daher mussten wir eine Möglichkeit finden, den Spieler davon zu überzeugen, dass etwas Schlechtes für sie passiert ist. In herkömmlichen Spielen sehen Sie möglicherweise eine Animation, die Sie darüber informiert, dass Ihr Zeichen einen Treffer gemacht hat, oder der Bildschirm blinkt rot, und Ihr Zeichen kann ein wenig grunt sein. Da diese Arten von Hinweise in einer Mixed Reality-Erfahrung nicht funktionieren, haben wir uns entschieden, den visuellen Hinweis mit einem vertonten Sound zu kombinieren, der angibt, dass Sie Schaden genommen haben. Ich habe einen großen Sound erstellt und ihn in der Mischung so hervorstechen lassen, dass alles heruntergefahren wurde. Um dies noch besser zu machen, haben wir dann einen kurzen Warnsound hinzugefügt, als ob ein untergeordnetes Untersystem versinkt. 
<br>
![Wenn ein Spieler in RoboRaid getroffen wird, wird ein visueller Hinweis angezeigt, aber es wird auch ein audio-Hinweis angezeigt, der darauf hinweist, dass er Schaden genommen hat.](images/player-hit-roboraid-500px.jpg)

### <a name="getting-big-sound-from-small-speakers"></a>Abrufen von großem Sound von kleinen Lautsprechern

HoloLens lautsprecher sind klein und hell, um die Anforderungen des Geräts zu erfüllen, sodass Sie nicht erwarten können, zu viel Low-End zu hören. Ähnlich wie bei der Entwicklung für Smartphones oder Gaminggeräte für Gaminggeräte müssen Sounddesigner und -composer die Häufigkeit des Audioinhalts beachten. Ich entwerfen immer Sounds oder schreibe Musik mit einem vollständigen Frequenzbereich, da enzugehörige Mikrofone eine Option für die Benutzer sind. Um jedoch die Kompatibilität mit HoloLens sprechern zu gewährleisten, kann ich gelegentlich einen Test ausführen, indem ich einen EQ in den Master aller DAW-Daten einarbeite, in denen ich zufällig arbeite. Die EQ-Einstellung besteht aus einem Filter mit hohem Durchgang von etwa 600 Hz bis 700 Hz (nicht zu stark) und einem Tiefpassfilter bei etwa 10.000 (10.000 Hz). Dies sollte Ihnen einen ungefähren Überblick darüber geben, wie Ihre Sounds auf dem Gerät wiederklängen.

Wenn Sie sich darauf verlassen, dass sich ihre Musik ändert, werden Sie feststellen, dass Ihre Musik das Gefühl des Stamms vollständig verliert, wenn Sie diese EQ-Einstellung anwenden. Um dies zu beheben, habe ich eine weitere Schicht zum 2000er-2016-2016 hinzugefügt, die eine Oktave höher (mit einigen reichen Reichern) ist, und sie gemischt, um das Gefühl der Stammwurzel wieder zu erhalten. Manchmal gibt die Verwendung von Verzerrung zur Verstärkung der Bänder genügend Häufigkeitsinhalt im oberen Bereich, damit unser Gehirn denken kann, dass etwas darunter ist. Dies gilt für SFX wie Schläge, Explosionen oder Sounds für besondere Augenblicke, z. B. Superangriffe eines Vorgesetzten. Sie können sich nicht auf das low-end verlassen, um dem Spieler ein Gefühl von Auswirkung oder Gewichtung zu geben. Wie bei musik auch, hat die Verwendung von Verzerrung, um etwas Crunch zu geben, definitiv dazu beigetragen.

### <a name="making-your-audio-cues-stand-out"></a>Heraussingen Ihrer Audio-Hinweise

Natürlich wollten alle Im team-Mitarbeiter musikartigen Musik, laute Schläge und 4000er-Explosionen; sie wollten aber auch Voiceover oder andere spielkritische Audioanrufe hören können.

Bei einem Konsolenspiel mit vollständigem Frequenzbereich haben Sie mehr Optionen, um Frequenzen je nach Wichtigkeit des Sounds nach oben zu unterteilen. Für RoboRaid war ich in der Anzahl der Frequenzbereiche eingeschränkt, die ich aus Sounds herauskurven konnte. Wenn Sie den LowPass-Filter verwenden und zu viel vom höheren Ende des Spektrums herauskurven, bleibt nichts mehr auf dem Sound übrig, da es nicht viel low-end gibt.

Um RoboRaid so groß wie möglich auf dem Gerät zu gestalten, mussten wir den dynamischen Bereich der gesamten Erfahrung senken und das Abhören umfassend nutzen, indem wir eine klare Hierarchie von Wichtigkeit für verschiedene Arten von Sounds erstellt haben. Je nach Wichtigkeit habe ich die Gewichtung von -2 dB auf -6 dB festgelegt. Ich persönlich mag das offensichtliche Ein- und Ausblenden von Spielen nicht, daher habe ich viel Zeit damit verbracht, das Ein-/Ausblenden und die Menge der Volumendämpfung zu optimieren. Wir richten separate Buss für Raumklang, nicht räumlichen Sound, VO und Probebus ohne Hall für Musik ein. Anschließend haben wir wichtige und nicht kritische Buslinien mit hoher Priorität erstellt, sodass die Ressourcen so eingerichtet wurden, dass sie zu den entsprechenden Buss gehen.

Ich hoffen, dass Audioexperten dort so viel Spaß und Spaß haben werden, an ihren eigenen Apps zu arbeiten, wie ich an RoboRaid arbeitet. Ich kann nicht warten, um zu sehen (und zu hören), was die talentierten Menschen außerhalb von Microsoft für ihre HoloLens.

## <a name="do-it-yourself"></a>Aufzeichnung in Eigenregie

Ein Trick, den ich entdeckt habe, um bestimmte Ereignisse (z. B. Explosionen) "größer" zu gestalten – wie sie den Raum füllen – war das Erstellen eines Mono-Assets für den räumlichen Sound und die Mischung mit einem 2D-Stereo-Objekt, das in 3D wiedergespielt werden soll. Dies nimmt einige Optimierungen in Dies ist wichtig, da zu viele Informationen im Stereoinhalt die Direktionalität der Mono-Objekte mindern. Das richtige Gleichgewicht führt jedoch zu riesigen Sounds, die spieler dazu bringen, den Kopf in die richtige Richtung zu drehen.

Sie können große Sounds selbst ausprobieren, indem Sie die folgenden Audioressourcen verwenden:

**Szenario 1**
1. Laden [Sie roboraid_enemy_explo_mono.wav herunter,](images/roboraid-enemy-explo-mono.wav) und legen Sie fest, um räumlichen Sound wieder zu spielen, und weisen Sie es einem Ereignis zu.
2. Laden [sie roboraid_enemy_explo_stereo.wav herunter,](images/roboraid-enemy-explo-stereo.wav) und legen Sie fest, dass sie in 2D-Stereo wiederklangen und dem gleichen Ereignis wie oben zuweisen. Da diese Ressourcen in Unity normalisiert werden, sollten Sie die Menge beider Objekte so abdämpfen, dass sie nicht abgeschnitten werden.
3. Geben Sie beide Sounds gemeinsam wieder. Bewegen Sie den Kopf, um zu sehen, wie räumlich es klingt.

**Szenario 2**
1. Laden [roboraid_enemy_explo_summed.wav herunter, und](images/roboraid-enemy-explo-summed.wav) legen Sie fest, um räumlichen Sound wieder zu spielen und einem Ereignis zu zuweisen.
2. Spielen Sie dieses Asset selbst ab, und vergleichen Sie es dann mit dem Ereignis aus Szenario 1.
3. Probieren Sie ein anderes Gleichgewicht zwischen Mono- und Stereodateien aus.

## <a name="see-also"></a>Siehe auch

* [Raumklang](spatial-sound.md)
* [RoboRaid für Microsoft HoloLens](https://www.microsoft.com/p/roboraid/9nblggh5fv3j)
