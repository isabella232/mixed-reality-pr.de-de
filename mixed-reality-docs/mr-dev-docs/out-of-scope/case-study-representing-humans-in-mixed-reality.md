---
title: 'Fallstudie: Darstellen von Menschen in Mixed Reality'
description: Welche Möglichkeiten ergeben sich, wenn wir nicht nur großartige Elemente erstellen, sondern die realistischsten Erfassungen von Umgebungen, Objekten und Personen in Mixed Reality nutzen können?
author: mavitazk
ms.author: jemccull
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Menschen, Avatar, Mixed Reality-Aufnahme, volumetrischen Video
ms.openlocfilehash: db21b6b02ce76403c2c59e37384c1c1602d8a63e003a8b5b6601c5daf7b9c2a7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228527"
---
# <a name="case-study---representing-humans-in-mixed-reality"></a>Fallstudie: Darstellen von Menschen in Mixed Reality

James Tuchef entwirft mit Licht. Das Einarbeiten in seine Arbeit verwischt das Gefühl von Tiefe und Fokus. Wände scheinen nah und unendlich zu sein, Helligkeit weht Schatten. Unbekannte Wahrnehmungen, die durch sorgfältigen Ausgleich von Farbe und Glühbirnen des Lichts entworfen wurden. [Tu nutzungsbeschreibt](https://www.sculpture.org/documents/scmag02/nov02/turrell/turrell.shtml) diese Beiden als "Gefühl mit den *Augen",* eine Möglichkeit, das Verständnis der Realität zu erweitern. Welten der Welten, die wie Tu nach möglichkeit leistungsfähiger sind, sind leistungsstarke Tools, um unsere Sinne zu nutzen, nicht im Gegensatz zu den heutigen immersiven Umgebungen von Mixed Reality.

![Wide Out – James Tuchef (1998)](../develop/platform-capabilities-and-apis/images/wide-out-james-turrell.jpg)

## <a name="how-do-you-represent-complex-real-world-environments-in-mixed-reality"></a>Wie stellen Sie komplexe reale Umgebungen in Mixed Reality dar?

Die Darstellung der Arbeit von Tuchef in einer immersiven Umgebung stellt eine überzeugende Herausforderung dar. Beleuchtung, Skalierung und räumliche Audiowiedergabe bieten Möglichkeiten, seine Arbeit zu repräsentieren. Während die geometrische Umgebung des Exponenten eine relativ einfache 3D-Modellierung erfordern würde, sind sie dem Fokus des Interpreten sekundär: der Auswirkung des Lichts auf die Sinne.

Tuchefs starker, minimaler Minimalismus ist das Merkmal seiner Arbeit, aber was wäre, wenn wir ein Exponent mit komplexeren Materialien in Mixed Reality darstellen möchten?

![Ai Weiwei (2013)](../develop/platform-capabilities-and-apis/images/bang-ai-weiwie.jpg)

Im Jahr 2013 hat der Interpret [](https://www.designboom.com/art/ai-weiwei-bang-installation-at-venice-art-biennale-2013/) Ai Weiwei ein verwirrendes Werk mit 886 500 Tafeltools in der Hotel-Bibliothek Von DerEdener 2013 mit 886 Tafeln eniert. Jeder Strich stammt aus einer Zeit, in der die chinesische Zeugung sehr geschätzt wurde, in der diese Tools zwischen generationenlangen Generationen weitergegeben worden wären. Die Tools selbst – die Feinheiten des Wood, die Genauigkeit der Teile, ihre sorgfältige Platzierung – sind entscheidend für die Ki-Intelligenz in der modernen Kultur.

Die Tools der Eltern stellen die Nachricht des Interpreten durch ihre Authentizität zur Verfügung. Ihre realistische Darstellung ist wichtig für die Erfahrung und stellt eine technische Herausforderung dar: Die handschriftliche Gestaltung jedes der 886-Tools wäre sehr umfassend und teuer. Wie lange würde es dauern, modellieren und positionieren? Wie würden Sie die Authentizität des Materials bewahren? Diese Objekte von Grund auf neu zu erstellen, wird in vielerlei Hinsicht zu einer Interpretation der Grafik selbst. Wie können Sie die Absicht des Interpreten beibehalten?

## <a name="methods-of-capturing-mixed-reality-assets"></a>Methoden zum Erfassen von Mixed Reality-Ressourcen

Die Alternative zum Erstellen von etwas von Grund auf ist die Erfassung des tatsächlichen Dings. Durch einen ständig weiterentwickelnden Satz von Erfassungsmethoden können wir authentifizierte Darstellungen der einzelnen Kernobjekttypen entwickeln, die in Mixed Reality (Umgebungen, Objekte und Personen) gefunden werden.

Die breiten Kategorien reichen von gut etablierten 2D-Videos bis zu den neuesten Formen volumetrischen Videos. Im Fall des Ai Weiwei-Exponenten könnte das Scannen (häufig durch seine grundlegende Technik, Fotogrammetrie bezeichnet), während der Erstellung des Exponenten verwendet werden, indem jeder der Tools selbst gescannt wird. Die 360°-Foto- und Videoaufnahme ist eine weitere Methode zum Virtualisieren der Erfahrung mithilfe einer hochwertigen omnidirektionalen Kamera, die im gesamten Exponent positioniert ist. Mit diesen Techniken beginnt man, den Sinn der Skalierung zu verstehen, idealerweise mit genügend Details, um das Verständnis der einzelnen Schritte zu erkennen. All dies ist in einer digitalen Form vorhanden, die neue Vistas und Perspektiven ermöglicht, die in der Realität nicht möglich sind.

![2D zu Volumetrischen Video](../develop/platform-capabilities-and-apis/images/2d-to-volumetric-video.png)

Welche Möglichkeiten ergeben sich, wenn wir nicht nur großartige Elemente erstellen, sondern die realistischsten Erfassungen von Umgebungen, Objekten und Personen in Mixed Reality nutzen können? Die Untersuchung der Überlappung zwischen diesen Methoden hilft dabei, die Richtung des Mediums zu untersuchen.

Für Umgebungen und Objekte wird die 360°-Bildverarbeitungssoftware so weiterentwickelt, dass sie Elemente der Fotogrammetrie enthält. Fortgeschrittene 360°-Videos isolieren Tiefeninformationen von Szenen und tragen dazu bei, das Gefühl zu mindern, dass Der Kopf beim Umhersuchen in einer virtuellen Szene in einem Fishbowl hängen bleibt.

Für Menschen entstehen neue Methoden, die Bewegungserfassung und -scannen kombinieren und erweitern: Motion Capture war die Grundlage dafür, detaillierte menschliche Bewegungen zu visuellen Effekten und vergitterten Zeichen zu bringen, während das Scannen erweitert wurde, um detaillierte menschliche Visuals wie Gesichter und Hände zu erfassen. Mit der Weiterentwicklung der Renderingtechnologie baut eine neue Methode namens volumetrischen Videos auf diesen Techniken auf und kombiniert visuelle und tiefen Informationen, um die nächste Generation von 3D-menschlichen Erfassungen zu erstellen.

## <a name="volumetric-video-and-the-pursuit-of-authentic-human-capture"></a>Volumetrischen Video und die Aufnahme von Menschen

Menschen sind ein zentraler Ort für das Geschichtenerzählen – im literalsten Sinn: menschensprechend, leistunglich oder als Subjekt der Geschichte. Einige der immersiven und augenaufdingendsten Augenblicke der heutigen frühen immersiven Erfahrungen sind soziale Medien. Von der gemeinsamen Nutzung einer Mixed Reality-Umgebung in Ihrem Zimmer bis zum Sehen Ihrer Freunde in neuen Umgebungen. Das menschliche Element macht sogar die realitätsreichste Realität, eine Realität.

![Mindshow in VR](../develop/platform-capabilities-and-apis/images/mindshow-in-vr-640px.jpg)

Avatare in immersiven Umgebungen ermöglichen eine neue Art von Verkörperung im Storys. Die neuesten Apps überdenken das Konzept des Besitzes virtueller Körper und setzen einen Generationssprung ein, um die Entfernung zwischen Personen zu beseitigen. Unternehmen wie [Mindshow entwickeln](https://mindshow.com/) kreative Tools, die Avatare nutzen, damit Benutzer völlig neue Personas und Zeichen übernehmen können. Andere untersuchen [Methoden des menschlichen Ausdrucks,](https://en.wikipedia.org/wiki/Uncanny_valley)eine potenziell unbegrenzte schaffende Möglichkeit, die Natur (und Notwendigkeit) von menschlichen Attributen zu untersuchen. Heutzutage hilft dieses Fehlen [](https://en.wikipedia.org/wiki/Uncanny_valley) von Realismus dabei, das unkehrlich-menschlichen Veralten zusammen mit einer Vielzahl von technischen Problemen für alltägliche Entwickler zu vermeiden. Aus diesen (und mehr) Gründen ist es sehr wahrscheinlich, dass nicht realistische Avatare für die zukünftige Zukunft zur Standardeinstellung werden. Und obwohl Realismus eine enorme Herausforderung für Mixed Reality darstellt, gibt es wichtige Szenarien, die eine echte Darstellung von Menschen *im 3D-Raum erfordern.*

Bei Microsoft hat ein kleines Team, das sich aus Microsoft Research entwickelt hat, in den letzten Jahren eine Methode entwickelt, um Menschen mithilfe von volumetrischen Videos zu erfassen. Der Prozess ähnelt heute der Videoproduktion: Anstatt Bewegung auf ein sculptiertes Objekt zu anwenden, handelt es sich um eine vollständige 3D-Aufzeichnung. Die Leistung und das Bild werden in Echtzeit erfasst– es ist nicht die Arbeit eines Interpreten, sondern eine authentic-Darstellung. Und während die Technologie gerade erst mit der Erweiterung auf kommerzielle Anwendungen beginnt, sind die Auswirkungen volumetrischer Videos für die Vision von Microsoft von [More Personal Computing von entscheidender Bedeutung.](https://www.youtube.com/watch?v=tcyj-_IEWt8)

![Volumetrischen Video SIGGRAPH 2015](../develop/platform-capabilities-and-apis/images/volumetric-video-siggraph-2015.gif)

Authentic Human Capture entsperrt neue einzigartige Kategorien von Erfahrungen in Mixed Reality. Wenn Sie erkennen, ob es sich um einen Prominenten, einen Kollegen oder einen 100- oder einen 14-Mal-Prominenten geht, entsteht in einem digitalen Medium nie zuvor eine Tiefe der Intimität. Ihr Gesicht, ihre Ausdrücke, die Nuancierung in ihren Bewegungen gehören alle dazu, wer sie sind. Welche Möglichkeiten eröffnen sich, wenn wir diese menschlichen Qualitäten im 3D-Raum erfassen können?

Heute geht das Team die Grenzen des volumetrischen Videos weiter, indem es sich [](https://www.youtube.com/watch?v=BwWueXlsOrA) auf Sektoren wie Unterhaltung und Bildung konzentriert: [Actiongram](https://www.microsoft.com/p/actiongram/9nblggh5ftmt) bietet kreative Figuren und Prominente, um Mixed Reality-Storys zu erstellen. [Ziel: Das Mars-Exponent](https://www.jpl.nasa.gov/news/news.php?feature=6220), das sich jetzt im Space Center der NASA befindet, enthält ein volumetrischen Video des Astronauten Aldrin. Mit dieser Erfahrung können Besucher die Marsoberfläche mit Rover durch die Umgebung führen, während er die menschlichen Doppelpunkte auf dem Mars einfing.

## <a name="humans-are-fundamental-to-mixed-reality"></a>Menschen sind für Mixed Reality von grundlegender Bedeutung

Das Entwerfen von Möglichkeiten, diese Videos natürlich erscheinen zu lassen, stellt eine Herausforderung dar, bei der das Team jedoch ein enormes Potenzial erkennt. Und diese Möglichkeiten werden sich erweitern, wenn die Technologie zugänglicher wird und von Aufzeichnungen zur Echtzeiterfassung wechselt.

[Holoportation ist](https://www.microsoft.com/research/project/holoportation-3/) ein Forschungsaufwand, der auf derselben grundlegenden Technologie aufbaut, visuelle und tiefen Informationen authentifiziert erfasst und das Ergebnis in Echtzeit rendert. Das Team geht es um die Möglichkeiten einer realistischen menschlichen Darstellung für die Zukunft von Konversationen und gemeinsamen Erfahrungen. Was geschieht, wenn eine dreidimensionale Erfassung von jemandem von überall auf der Welt zu Ihrer Umgebung hinzugefügt werden kann?

![Zukunft der Konversation](../develop/platform-capabilities-and-apis/images/girl-with-dress.jpg)

Von der Überschichtung einer neuen Ebene des Immersions in alltägliche Apps wie Skype bis zur grundlegenden Neugestaltung des Konzepts von digitalen Besprechungen und Geschäftsreise – volumetrischen Videos eröffnen einzigartige Szenarien: Ein Experte trainiert praktisch Ärzte auf einem weit entfernten Kontinent oder digitale Freunde, die auf den Couchs liegen und in Ihrem Leben leben. Das Hinzufügen von echten menschlichen Darstellungen zu Mixed Reality-Erfahrungen wird das Konzept von digitalen Besprechungen und Geschäftsreise grundlegend umgestalten.

Genau wie die abstrakten Bilder von James Tuchef und der kritische Realismus von Ai Weiwei ihre eigenen einzigartigen technischen Herausforderungen bieten, auch die Methoden, um Menschen als kreative Avatare und realistische Erfassungen zu darstellen. Eines kann nicht im Lichte des anderen ignoriert werden, und die Untersuchung des Potenzials jedes einzelnen kann uns helfen, die Interaktion zwischen Menschen in diesem neuen Raum zu verstehen.

## <a name="about-the-author"></a>Informationen zum Autor

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Mark Vitazko" width="60" height="60" src="images/mark-vitazko.jpg"></td>
<td style="border-style: none"><b>Mark Sollzko</b><br>UX-Designer @Microsoft</td>
</tr>
</table>
