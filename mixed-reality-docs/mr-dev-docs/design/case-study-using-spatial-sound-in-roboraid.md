---
title: 'Fallstudie: Verwenden von räumlichem Sound in roboraid'
description: Räumlicher Sound ist eines der interessantesten Features von Microsoft hololens, mit dem Benutzer erkennen können, was Sie passiert, wenn Objekte nicht mehr im Blick sind.
author: mattzmsft
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, hololens, roboraid, Spatial Sound, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens, mrtk, Mixed Reality Toolkit, CPU
ms.openlocfilehash: 95650ea7097f16d257c80c11443b84936bece435
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847545"
---
# <a name="case-study---using-spatial-sound-in-roboraid"></a>Fallstudie: Verwenden von räumlichem Sound in roboraid

In diesem Artikel werden die Herausforderungen des Microsoft hololens-Teams bei der Erstellung von Audiodaten für die First-Person-Anwendung [roboraid](https://www.microsoft.com/p/roboraid/9nblggh5fv3j) Mixed-Reality beschrieben.

## <a name="the-tech"></a>Die Technologie

[Räumlicher Sound](spatial-sound.md) ist eines der interessantesten Features von Microsoft hololens, mit dem Benutzer die möglichen Informationen erkennen können, wenn Objekte nicht in der Sicht enthalten sind.

In roboraid besteht die offensichtlichste und effektivste Verwendung des räumlichen Sounds darin, den Player vor der Peripherie Vision zu warnen. Beispielsweise kann der breacher von einem der überprüften Wände im Raum eingeben. Wenn Sie nicht mit dem Speicherort des Orts vertraut sind, können Sie ihn übersehen. Um Sie bei dieser Invasion zu warnen, hören Sie ein unterschiedliches Audiostück, von dem aus der breacher wechselt, sodass Sie schnell reagieren müssen, um es zu verhindern.

## <a name="behind-the-scenes"></a>Abläufe im Hintergrund

Das Erstellen räumlicher Sounds für hololens-Apps ist so neu und einzigartig, dass Probleme schwer zu lösen sind, da keine früheren Projekte vorhanden sind, auf die verwiesen werden kann. Hoffentlich helfen Ihnen diese Beispiele für die audioherausforderungen bei der Erstellung von roboraid bei der Erstellung von Audiodaten für Ihre eigenen apps.

### <a name="be-mindful-of-taxing-the-cpu"></a>Berücksichtigen der CPU-Auslastung

Räumlicher Sound kann auf der CPU anspruchsvoll sein. Für eine ausgelastete Umgebung wie roboraid war es entscheidend, die Anzahl räumlicher Sound Instanzen zu einem beliebigen Zeitpunkt unter acht zu halten. In der Regel war es so einfach, das Limit von Instanzen für verschiedene Audioereignisse festzulegen. Alle Instanzen, die nach Erreichen des Limits auftreten, werden abgebrochen. Wenn beispielsweise Drohnen ausgegeben werden, sind Ihre Screams auf drei Instanzen zu einem beliebigen Zeitpunkt beschränkt. Wenn nur ungefähr vier Drohnen gleichzeitig erzeugt werden können, sind drei scremes ausreichend, da das Gehirn nicht so viele ähnlich klingende Audioereignisse verfolgen kann. Dadurch wurden Ressourcen für andere räumliche Audioereignisse freigegeben, wie z. b. feindliche Explosionen oder Feinde, die sich auf das Schießen vorbereiten

### <a name="rewarding-a-successful-dodge"></a>Belohnen eines erfolgreichen ausweichen

Der Dodging-Mechaniker ist eine der wichtigsten Spielmechanismen in roboraid, und auch etwas, das wir uns fühlen, war für die hololens-Umgebung wirklich einzigartig. Daher wollten wir die erfolgreichen Dodges für den Player sehr lohnend gestalten. Wir haben den Doppler "Whizz-by" ("Whizz-by") in die Entwicklung gebracht. Anfänglich war der Plan, eine Schleife zu verwenden und Sie in Echtzeit mithilfe von Volume, Tonhöhe und Filter zu manipulieren. Die Implementierung hierfür war sehr aufwendig. Vor dem committen von Ressourcen für die Erstellung haben wir einen kostengünstigen Prototyp mit einem Asset erstellt Unsere begabten Entwickler haben es so gestaltet, dass dieses Whizz-by-Asset genau 0,7 Sekunden wiedergegeben würde, bevor die Projekt Kachel vom Player gereicht wird und die Ergebnisse erstaunlich sind! Natürlich haben wir die komplexere Lösung unterzogen und den Prototyp implementiert.

*(Weitere Informationen zum Erstellen eines audioassets mit dem integrierten Doppler-Effekt finden Sie unter [100 whooshes in 2 Minuten](http://designingsound.org/2010/02/26/charles-deenen-special-100-whooshes-in-2-minutes/).)* 
<br>
![Durch das erfolgreiche Dodging eines "projectile" eines Feindes wird der Spieler durch einen Sound zufriedenstellend.](images/successful-dodge-roboraid-500px.jpg)

### <a name="ditching-ineffective-sounds"></a>Abrufen von ineffektiven Sounds

Ursprünglich wollten wir einen explodierenden Sound hinter dem Player abspielen, nachdem Sie den feindlichen projectile erfolgreich angedochelt haben, aber wir haben uns entschieden, dies aus verschiedenen Gründen zu verwerfen. Erstens war das nicht so effektiv wie das von SFX, das wir für den Dodge verwendet haben. Zu dem Zeitpunkt, an dem die Projekt Kachel auf eine Wand hinter Ihnen stößt, wäre im Spiel etwas anderes passiert, das diesen Sound maskieren würde. Zweitens haben wir keine Kollision im Boden gefunden, deshalb konnten wir die Explosion nicht wiedergeben, wenn die "projectile"-Kachel anstelle der Wände auf den Fußboden trifft. Und schließlich gab es die CPU-Kosten des räumlichen Sounds. Der Elite-Skorpion (einer, der sich innerhalb der Wand durchforsten kann) hat einen besonderen Angriff, der etwa acht Projekt Kacheln durchsucht. Dies führte nicht nur zu einem großen Chaos in der Mischung, sondern führte auch zu einer sehr großen Überlastung, da die CPU zu schwierig war.

### <a name="communicating-a-hit"></a>Kommunizieren eines Treffer

Ein interessantes Problem in den hololens war, wie schwierig es war, effektiv zu kommunizieren, dass ein Spieler getroffen wurde. Eine gemischte Realität führt zu einer erfolgreichen Darstellung der Geschichte. Dies bedeutet, dass Sie glauben müssen, dass Sie eine fremde Roboter-Invasion in Ihrem eigenen Wohn Raum bekämpfen.

Spieler fühlen sich offensichtlich nichts, wenn Sie auf Sie stoßen. Daher mussten wir eine Möglichkeit finden, den Player zu überzeugen, dass etwas Böses passiert ist. In herkömmlichen spielen wird möglicherweise eine Animation angezeigt, mit der Sie wissen, dass Ihr Zeichen einen Treffer ausgelöst hat, oder der Bildschirm ist rot, und Ihr Zeichen ist möglicherweise ein wenig. Da diese Arten von Hinweisen nicht in gemischter Realität funktionieren, haben wir uns entschieden, den visuellen Hinweis mit einem übertriebenen Sound zu kombinieren, der angibt, dass Sie Schäden verursacht haben. Ich habe einen großen Sound erstellt und ihn so hervorgehoben, dass er in der Mischung alles hervorgehoben hat. Um den Code noch weiter zu machen, haben wir eine kurze Warnmeldung mit dem Hinweis hinzugefügt, dass eine atomarische Untermenge nicht versinkt. 
<br>
![Wenn ein Player in roboraid erreicht wird, sehen Sie einen visuellen Hinweis, Sie erhalten aber auch einen übertriebenen audiohinweis, der Sie darüber informiert, dass Sie Schaden anrichten.](images/player-hit-roboraid-500px.jpg)

### <a name="getting-big-sound-from-small-speakers"></a>Holen Sie sich einen großen Sound von kleinen Referenten

Hololens-Sprecher sind klein und leicht, um den Anforderungen des Geräts gerecht zu werden, sodass Sie nicht zu viel tiefstschluss erwarten. Ähnlich wie bei der Entwicklung für Smartphones oder Hand Held Spielgeräte müssen Sounddesigner und-Komponisten den Frequenz Inhalt Ihrer Audiodaten berücksichtigen. Ich erstelle immer Sounds oder schreibe Musik mit vollständigem Frequenzbereich, da das Übertragen von Kopfhörern eine Option für die Benutzer ist. Um jedoch die Kompatibilität mit den Referenten von hololens sicherzustellen, führe ich gelegentlich einen Test durch, indem ich einen EQ in den Master einer beliebigen DAW Stelle setze, in der ich arbeite. Die EQ-Einstellung besteht aus einem High-Pass-Filter zwischen 600 Hz und 700 Hz (nicht zu steil) und einem Tiefpass Filter bei ungefähr 10K (steil). Dadurch erhalten Sie eine ungefähre Vorstellung von der Wiedergabe ihrer Sounds auf dem Gerät.

Wenn Sie sich auf den Bass verlassen, um den Eindruck zu gewinnen, dass Sie sich in ihrer Musik ändern, werden Sie möglicherweise feststellen, dass Ihre Musik den Grund für den Stamm verliert, wenn Sie diese EQ-Einstellung anwenden. Um dieses Problem zu beheben, habe ich dem Bass eine andere Ebene hinzugefügt, die eine Oktave höher (mit einigen umfangreichen Harmonisierungen) ist, und Sie gemischt, um den Grund für den Stamm wieder zu verstehen. Manchmal wird durch die Verwendung von Verzerrung zum Einrichten der Harmonisierungen ausreichend Häufigkeits Inhalt im oberen Bereich angezeigt, damit das Gehirn der Ansicht ist, dass es etwas darunter gibt. Dies gilt für SFX, wie z. b. Auswirkungen, Explosionen oder Sounds, wie z. b. die Super-Angriffe eines Chefs. Sie können sich nicht auf das niedrige Ende verlassen, um dem Player einen Eindruck von Auswirkung oder Gewichtung zu verschaffen. Wie bei Musik ist die Verwendung von "Verzerrung", um etwas zu erreichen, definitiv hilfreich.

### <a name="making-your-audio-cues-stand-out"></a>Stellen Sie Ihre Audiohinweise bereit

Natürlich wünschte sich jede Person im Team bombastische Musik, laute Gewehre und verrückte Explosionen. Sie wollten aber auch in der Lage sein, VoiceOver oder andere Spiel kritische Audiohinweise zu hören.

Bei einem Konsolenspiel mit vollständigem Frequenzbereich haben Sie mehr Optionen, um die Häufigkeit abhängig von der Bedeutung des Sounds zu unterteilen. Für roboraid war ich auf die Anzahl der Häufigkeits Bereiche beschränkt, die ich aus Sounds herausfiltern konnte. Wenn Sie einen Tiefpass-Filter verwenden und sich am oberen Ende des Spektrums zu stark auslagern, haben Sie im Sound keine weiteren Informationen, da es nicht viel zu niedrig ist.

Um roboraid so groß wie möglich auf dem Gerät zu machen, mussten wir den dynamischen Bereich der gesamten Umgebung verringern und eine umfassende Verwendung von Ducking durchführen, indem wir eine klare Hierarchie von Wichtigkeit für verschiedene Arten von Sounds erstellt haben. Abhängig von der Wichtigkeit wird das Ducking von-2 dB auf-6 dB festgelegt. Ich persönlich weiß nicht, dass ich mich in spielen in spielen, also habe ich viel Zeit damit verbracht, die Einblend-/Ausgabezeit und den Umfang der volumedämpfung zu optimieren. Wir richten separate Busse für räumliche Audiodaten, nicht räumliche Sounds, VO und Dry Bus ein, ohne für Musik zu Hall. Anschließend haben wir hohe Prioritäts-, kritische und nicht kritische Busse erstellt, sodass die Assets so eingerichtet wurden, dass Sie in die entsprechenden Busse gelangen.

Ich hoffe, dass Audiofachleute es so viel Spaß machen und mit der Arbeit an Ihren eigenen apps arbeiten, da ich mich an roboraid gearbeitet habe. Ich kann nicht abwarten (und hören!), was die talentierten Menschen außerhalb von Microsoft für hololens finden.

## <a name="do-it-yourself"></a>Aufzeichnung in Eigenregie

Ein von mir ermittelter Trick, mit dem bestimmte Ereignisse (z. b. Explosionen) "größer" sind – wie Sie den Raum Auffüllen – bestand darin, ein Mono-Medienobjekt für den räumlichen Ton zu erstellen und es mit einem 2D-Stereo Asset zu mischen, das in 3D wiedergegeben werden sollte. Es wird eine gewisse Optimierung durchführen, da zu viele Informationen in den Stereo Inhalten die Direktionalität der Mono-Assets verringern werden. Allerdings führt das Erreichen des Saldo Recht zu sehr großen Sounds, mit denen sich die Spieler in der richtigen Richtung drehen können.

Sie können große Sounds selbst ausprobieren, indem Sie die folgenden Audioressourcen verwenden:

**Szenario 1**
1. Laden Sie [roboraid_enemy_explo_mono. wav](images/roboraid-enemy-explo-mono.wav) herunter, und legen Sie fest, dass Sie den räumlichen Sound wiedergeben und einem Ereignis zuweisen.
2. Laden Sie [roboraid_enemy_explo_stereo. wav](images/roboraid-enemy-explo-stereo.wav) herunter, und legen Sie für die Wiedergabe in 2D Stereo fest, und weisen Sie dem gleichen Ereignis wie oben zu. Da diese Assets in Unity normalisiert werden, können Sie die Menge beider Assets dämpfen, damit Sie nicht abruft.
3. Wiedergeben beide Sounds. Bewegen Sie sich den Kopf, um zu erfahren, wie räumliche IT klingen.

**Szenario 2**
1. Laden Sie [roboraid_enemy_explo_summed. wav](images/roboraid-enemy-explo-summed.wav) herunter, und legen Sie fest, dass Sie den räumlichen Sound wiedergeben und einem Ereignis zuweisen.
2. Diese Ressource selbst wiedergeben und dann mit dem Ereignis aus Szenario 1 vergleichen.
3. Probieren Sie ein anderes Gleichgewicht von Mono-und Stereo Dateien aus.

## <a name="see-also"></a>Weitere Informationen

* [Raumklang](spatial-sound.md)
* [Roboraid für Microsoft hololens](https://www.microsoft.com/p/roboraid/9nblggh5fv3j)
