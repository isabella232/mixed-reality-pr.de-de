---
title: Verwenden von räumlichem Sound in Mixed Reality-Anwendungen
description: Räumlicher Sound ist ein leistungsstarkes Tool für Immersion, Barrierefreiheit und UX-Design in Mixed Reality-Anwendungen.
author: kegodin
ms.author: v-hferrone
ms.date: 11/02/2019
ms.topic: article
keywords: Windows Mixed Reality, Räumlicher Sound, Design, Stil, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit, Gesten, Interaktionen, Dämpfung
ms.openlocfilehash: 687811f23e11cadf6e75129098c9feb0393009f819eb961cf2f55a3208cc5f96
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208960"
---
# <a name="how-to-use-sound-in-mixed-reality-applications"></a>Verwenden von Sound in Mixed Reality-Anwendungen

Sie können sound verwenden, um das mentale Modell des Anwendungszustands des Benutzers zu informieren und zu verstärken. Verwenden Sie ggf. die Raumaufbewahrung, um Sounds in der Mixed Reality-Welt zu platzieren. Wenn Sie den Prüfer und das Visual auf diese Weise verbinden, vertiefen Sie die intuitive Art der Interaktionen und erhöhen das Vertrauen der Benutzer.
<br><br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="when-to-add-sounds"></a>Wann sollen Sounds hinzugefügt werden?

Mixed Reality-Anwendungen benötigen häufig mehr Sound als 2D-Apps, da keine taktilen Schnittstellen zur Verfügung stehen. Fügen Sie Sounds hinzu, wenn sie den Benutzer informieren oder Interaktionen verstärken.

### <a name="inform-and-reinforce"></a>Informieren und verstärken

* Verwenden Sie für Ereignisse, die nicht vom Benutzer initiiert werden, z. B. Benachrichtigungen, Sound, um den Benutzer darüber zu informieren, dass eine Änderung aufgetreten ist.
* Interaktionen können mehrere Phasen aufweisen. Verwenden Sie Sound, um Phasenübergänge zu verstärken.

Sehen Sie sich die folgenden Beispiele für Interaktionen, Ereignisse und vorgeschlagene Soundmerkmale an.

### <a name="exercise-restraint"></a>Übungsübungen

Benutzer verfügen nicht über eine unbegrenzte Kapazität für Audioinformationen.
* Jeder Sound sollte spezifische, wertvolle Informationen kommunizieren.
* Wenn Ihre App einen Sound abgibt, um den Benutzer zu informieren, verringern Sie vorübergehend die Lautstärke anderer Sounds.
* Fügen Sie für Schaltflächen-Hoversounds (siehe die folgenden Informationen) eine Zeitverzögerung hinzu, um übermäßiges Auslösen von Sound zu verhindern.

### <a name="dont-rely-solely-on-sounds"></a>Verlassen Sie sich nicht ausschließlich auf Sounds.

Gut verwendete Sounds sind für Ihre Benutzer von Nutzen. Stellen Sie jedoch sicher, dass Ihre Anwendung auch bei deaktiviertem Sound verwendet werden kann.
* Benutzer können hörgeschädigt sein.
* Ihre Anwendung kann in einer lauten Umgebung verwendet werden.
* Benutzer haben möglicherweise Datenschutzbedenken oder andere Gründe zum Deaktivieren von Geräteaudiodaten.

## <a name="how-to-sonify-interactions"></a>Vereinheitlichen von Interaktionen

Zu den Interaktionstypen in Mixed Reality gehören Geste, direkte Bearbeitung und Stimme. Verwenden Sie die folgenden vorgeschlagenen Merkmale, um Sounds für diese Interaktionen auszuwählen oder zu entwerfen.

### <a name="gesture-interactions"></a>Gesteninteraktionen

In Mixed Reality können Benutzer mit der Maus mit Schaltflächen interagieren. Schaltflächenaktionen treten in der Regel auf, wenn der Benutzer die Schaltfläche freigibt, anstatt sie zu drücken, um dem Benutzer die Möglichkeit zu geben, die Interaktion abzubrechen. Verwenden Sie Sounds, um diese Phasen zu verstärken. Um Benutzer bei der Ausrichtung entfernter Schaltflächen zu unterstützen, sollten Sie auch die Verwendung eines Zeigerzeiger-Hover-Sounds in Betracht ziehen.
* Das Drücken von Schaltflächen sollte ein kurzer, taktiler "Klick" sein.<br/>Beispiel: [MRTK_ButtonPress.wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* Button-"unpress"-Sounds sollten ein ähnliches taktiles Gefühl aufweisen. Eine höhere Tonhöhe als der Pressenton verstärkt das Gefühl der Vervollständigung.<br/>Beispiel: [MRTK_ButtonUnpress.wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonUnpress.wav)
* Ziehen Sie für Hover-Sounds in Betracht, einen dezenten und nicht-akustischen Sound zu verwenden, z. B. einen low-frequency-Schläger oder -Stoßen.

### <a name="direct-manipulation"></a>Direkte Manipulation

Auf HoloLens 2 unterstützt die artikulierte Handverfolgung die direkte Bearbeitung von Elementen der Benutzeroberfläche. Sounds sind wichtig, wenn kein anderes physisches Feedback vorhanden ist.

Ein *Tastendruck* ist wichtig, da der Benutzer keine andere Anzeige erhält, wenn er den unteren Rand des Tastenstrichs erreicht. Soundindikatoren für den Schlüsselweg können klein, dezent und okkudiert sein. Wie bei Gesteninteraktionen sollten Tastendrucke einen kurzen, taktilen Sound wie einen Klick erhalten. Unerzungen sollten einen ähnlichen Klickton aufweisen, jedoch mit erhöhter Tonhöhe.
* Beispiel: [MRTK_ButtonPress.wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* Beispiel: [MRTK_ButtonUnpress.wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonUnpress.wav)

Es ist schwierig, eine Aktion zum Greifen oder Freigeben visuell zu bestätigen. Die Hand des Benutzers ist häufig jedem visuellen Effekt im Weg, und hartkörperige Objekte verfügen nicht über ein echtes visuelles Analogon von "Greifen". Sounds können effektiv erfolgreiche Interaktionen zum Greifen und Freigeben kommunizieren.
* Grab-Aktionen sollten einen kurzen, etwas muffigen taktilen Sound aufweisen, der die Idee des Schließens von Fingern um ein Objekt auslöst. Manchmal gibt es auch einen "Whoosh"-Sound, der bis zum Greifenton führt, um die Bewegung der Hand zu kommunizieren.<br/>Beispiel: [MRTK_Move_Start.wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_Move_Start.wav)
* Releaseaktionen sollten einen ähnlich kurzen und taktilen Sound erhalten. Es ist in der Regel niedriger als der Grab-Sound und in umgekehrter Reihenfolge, mit einer Auswirkung und dann einem "Whoosh", um zu kommunizieren, dass sich das Objekt an seiner Position befindet.<br/>Beispiel: [MRTK_Move_End.wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_Move_End.wav)

Eine  Zeichnungsinteraktion sollte einen beständigen Schleifenton mit Lautstärke erhalten, der durch die Handbewegung des Benutzers bestimmt wird. Es sollte still sein, wenn die Hand des Benutzers noch immer ist, und am lautesten, wenn sich die Hand schnell bewegt.

### <a name="voice-interactions"></a>Sprachinteraktionen

Sprachinteraktionen weisen häufig dezente visuelle Elemente auf. Verwenden Sie Sounds, um Interaktionsphasen zu verstärken. Möglicherweise möchten Sie mehr tonale Sounds verwenden, um sie von Gesten- und direkten Bearbeitungsgeräuschen zu unterscheiden.

* Verwenden Sie einen positiv klingenden Ton für *Sprachbefehlsbestätigungen.* Töne und wichtige Intervalle sind effektiv.
* Verwenden Sie einen kürzeren, weniger positiv klingenden Ton für *Sprachbefehlsfehler.* Vermeiden Sie negative Sounds. Verwenden Sie stattdessen einen percussiven, neutralen Sound, um zu kommunizieren, dass die Anwendung von der Interaktion fortgeht.
* Wenn Ihre Anwendung über ein Aktivierungswort verfügt, verwenden Sie einen kurzen, farbigen Ton, wenn das Gerät mit dem *Lauschen beginnt.* Verwenden Sie einen dezenten Schleifenton, während die *Anwendung* lauscht.

### <a name="notifications"></a>Benachrichtigungen

Benachrichtigungen signalisieren Änderungen des Anwendungszustands und andere Ereignisse, die der Benutzer nicht initiiert hat. Zustandsänderungen können Prozessabschluss, Nachrichten und Telefonanrufe umfassen.

In Mixed Reality bewegen sich Objekte manchmal aus dem Sichtfeld des Benutzers. Koppeln von *bewegten animierten Objekten* mit einem räumlichen Sound, der vom Objekttyp und der Geschwindigkeit der Bewegung abhängt.
* Es hilft, einen räumlichen Sound am Ende einer Animation wiederzuspielen, um den Benutzer über die neue Position des Objekts zu informieren.
* Bei allmählichen Bewegungen hilft ein "Whoosh"-Sound während der Bewegung dem Benutzer, das Objekt nachzuverfolgen.

*Nachrichtenbenachrichtigungsgeräusche* können wiederholt, manchmal in schneller Folge, gehört werden. Es ist wichtig, dass sie nicht heraus- oder klingend wirken. Positive Tonlaute im mittleren Bereich sind effektiv.

* Eingehende Anrufgeräusche sollten ähnliche Qualitäten wie ein Mobiltelefonrington aufweisen. Diese Sounds sind schleifende Phrasen, die wiedergegeben werden, bis der Benutzer den Anruf beantwortet.
* Sprachkommunikationsverbindung und Trennung sollten einen kurzen tonalen Sound aufweisen. Der Verbindungston sollte ein positiver Ton sein, um auf eine erfolgreiche Verbindung hinzuweisen. Der Trenngeräusch sollte ein neutraler Sound sein, um den Abschluss des Aufrufs anzugeben.

## <a name="handle-spatialization"></a>Behandeln der Räumlichen Verräumigung

Bei der Räumlichen Raumisierung werden Stereo- oder Lautsprecher verwendet, um Sounds in der Mixed Reality-Welt zu platzieren.

### <a name="which-sounds-to-spatialize"></a>Welche Sounds zu raumen sind

Ein Sound sollte spatialisiert werden, wenn er einem Ereignis zugeordnet ist, das über eine räumliche Position verfügt. Dies schließt ui, verkörperte KI-Stimmen und visuelle Indikatoren ein.

Spatialize *user interface* elements to help declutter the user es sonic "space" by limiting the number of stereo sounds that they hear. Manipulationsinteraktionen wie Touchieren, Greifen und Freigeben wirken natürlicher, wenn Audiofeedback räumlich verräumt wird. Beachten Sie die folgenden Informationen zur Abstandsdämpfung für diese Elemente.

Visualisieren Sie *visuelle Indikatoren* und *dargestellte KI-Stimmen,* um Benutzer intuitiv zu informieren, wenn sich diese Dinge außerhalb des Sichtfelds befinden.
    
Vermeiden Sie im Gegensatz dazu die Räumlicherisierung für *gesichtslose KI-Stimmen* und andere Elemente, die keine klar definierte räumliche Position haben. Die Räumliche Darstellung ohne ein verwandtes visuelles Element kann Benutzer dazu bringen, zu denken, dass es ein visuelles Element gibt, das sie nicht finden können.

Bei der Räumlichen Raumisierung fallen einige CPU-Kosten an. In vielen Anwendungen werden höchstens zwei Sounds gleichzeitig wiedergegeben. Die Räumlichen Kosten sind in diesem Fall wahrscheinlich vernachlässigbar. Sie können den MRTK-Bildfrequenzmonitor verwenden, um die Auswirkungen des Hinzufügens von Räumlicher Raumisierung zu beurteilen.

### <a name="when-and-how-to-apply-distance-based-attenuation"></a>Wann und wie wird die entfernungsbasierte Dämpfung angewendet?

In der physischen Welt sind die Töne, die weiter entfernt sind, stiller. Ihre Audio-Engine kann diese Dämpfung basierend auf dem Quellabstand modellieren. Verwenden Sie die entfernungsbasierte Dämpfung, wenn relevante Informationen übermittelt werden.

Die Abstände zu *visuellen Indikatoren,* *animierten Hologrammen* und anderen informativen Sounds sind für den Benutzer relevant. Verwenden Sie die entfernungsbasierte Dämpfung, um intuitive Hinweise bereitzustellen.

Passen Sie die Dämpfungskurve für jede Quelle an die Größe ihrer Mixed Reality-Räume an. Die Standardkurve Ihrer Audio-Engine ist häufig für große (bis zu halbe Kilometer) Leerzeichen vorgesehen.

Sounds, die die *progressiven Phasen von Schaltflächenaktionen* und anderen Interaktionen verstärken, sollten nicht Dämpfung angewendet werden. Die effekteren Effekte dieser Sounds sind wichtiger als die Kommunikation des Abstands zur Schaltfläche. Variationen können ablenkend sein, insbesondere bei Tastaturen, wenn viele Schaltflächenklicks nacheinander gehört werden können.

### <a name="which-spatialization-technology-to-use"></a>Welche Raumisierungstechnologie verwendet werden soll

Verwenden Sie mit Dennern oder den HoloLens Sprechern hrtf-basierte Raumtechnologien (Head-Related Transfer Function). Diese Technologien modellieren die Soundweitergabe um den Kopf in der physischen Welt. Selbst wenn sich eine Soundquelle auf der fernen Seite des Kopfes befindet, wird der Sound mit etwas Dämpfung und Verzögerung an das entfernte Gehör weitergegeben. Das Schwenken des Sprechers basiert nur auf der Dämpfung und wendet die gesamte Dämpfung im linken Gehör an, wenn sich die Töne auf der rechten Seite befinden, und umgekehrt. Diese Technik kann für "normales Hören" und für Listener mit Hörbehinderung an einem Hörgerät unzugänglich sein.

## <a name="next-steps"></a>Nächste Schritte

* [Verwenden von räumlichem Sound in Unity](../develop/unity/spatial-sound-in-unity.md)
* [Fallstudie zu Roboraid](case-study-using-spatial-sound-in-roboraid.md)
* [Fallstudie zu HoloTour](case-study-spatial-sound-design-for-holotour.md)
