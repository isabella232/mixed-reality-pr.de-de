---
title: Inhaltsobjekt-Erstellungsprozess
description: Erfahren Sie, wie Sie Ressourcen für Mixed Reality-Erfahrungen erstellen, kaufen und portieren.
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: Asset, Erstellung, Prozess, Budget, Polygone, Texturen, Shader, Leistung, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit, Ressourcen
ms.openlocfilehash: 5c5dcdbe24a8028bb8a3c57e57b9d95079f9e832954d12aa31421dd75f1b6982
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214108"
---
# <a name="asset-creation-process"></a>Inhaltsobjekt-Erstellungsprozess

Windows Mixed Reality basiert auf den seit Jahrzehnten erfolgten Investitionen, die Microsoft in DirectX investiert hat. Alle Erfahrungen und Fähigkeiten, die Entwickler mit dem Erstellen von 3D-Grafiken haben, sind mit der Entwicklung HoloLens.

Die Objekte, die Sie für ein Projekt erstellen, sind in vielen Formen und Formen erhältlich. Sie können aus einer Reihe von Texturen/Bildern, Audio, Video, 3D-Modellen und Animationen bestehen. Wir können nicht alle Tools abdecken, die verfügbar sind, um die verschiedenen Typen von Ressourcen zu erstellen, die in einem Projekt verwendet werden. In diesem Artikel konzentrieren wir uns auf Methoden zum Erstellen von 3D-Ressourcen.

![Konzept, Erstellung, Integration und Iterationsablauf](images/concept-creation-integration-iteration-flow-640px.jpg)<br>
*Konzept, Erstellung, Integration und Iterationsablauf*

## <a name="things-to-consider"></a>Zu beachtende Aspekte

Wenn Sie sich die Benutzererfahrung ansind, die  Sie erstellen möchten, stellen Sie sich dies als Budget vor, das Sie ausgeben können, um zu versuchen, die beste Erfahrung zu schaffen. Es gibt nicht unbedingt harte Grenzwerte für die Anzahl von **Polygonen** oder Materialtypen, **die** Sie in Ihren Ressourcen verwenden können. Stellen Sie sich dies eher als budgetierten Satz von Kompromissen vor.

Im Folgenden finden Sie ein Beispielbudget für Ihre Erfahrung. Die Leistung ist kein Single Point of Failure, sondern der Tod um tausend Schnitte.
<br>

<table style="float:right; margin-left: 10px;">
<tr>
<th style="text-align:left;"><b>Medienobjekte</b></th><th style="text-align:right;"> CPU</th><th> GPU</th><th> Arbeitsspeicher</th>
</tr><tr>
<td> Polygone</td><td> 0 %</td><td> 5 %</td><td> 10 %</td>
</tr><tr>
<td> Texturen</td><td> 5 %</td><td> 15 %</td><td>25 %</td>
</tr><tr>
<td> Shader</td><td> 15 %</td><td> 35 %</td><td> 0 %</td>
</tr><tr>
<td> <b>Dynamics</b></td><td></td><td></td><td></td>
</tr><tr>
<td> Physische Effekte</td><td> 5 %</td><td> 15 %</td><td> 0 %</td>
</tr><tr>
<td> Beleuchtung in Echtzeit</td><td> 10 %</td><td> 0 %</td><td> 0 %</td>
</tr><tr>
<td> Medien (Audio/Video)</td><td> -</td><td> 15 %</td><td> 25 %</td>
</tr><tr>
<td> Skript/Logik</td><td> 25 %</td><td> 0 %</td><td> 5 %</td>
</tr><tr>
<td> Allgemeiner Mehraufwand</td><td> 5 %</td><td> 5 %</td><td> 5 %</td>
</tr><tr>
<td> <b>Gesamt</b></td><td> <b>65%</b></td><td> <b>90%</b></td><td> <b>70 %</b></td>
</tr>
</table>

**Gesamtanzahl der Ressourcen**
* Wie viele Ressourcen sind in der Szene aktiv?

**Komplexität von Ressourcen**
* Wie viele Dreiecke/Polygone?
* Wie komplex ist der Shader? Wenn Sie das Mixed Reality Toolkit verwenden, wird empfohlen, den [Mixed Reality Toolkit Standard-Shader](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md) zu verwenden, um die Shaderkomplexität zu reduzieren.

Sowohl Entwickler als auch Grafiker müssen die Funktionen des Geräts und der Grafik-Engine berücksichtigen. Microsoft HoloLens verfügt über alle in das Gerät integrierten Berechnungs- und Grafikressourcen. Sie teilt die Funktionen, die Entwickler auf einer mobilen Plattform finden würden.

Der Erstellungsprozess für Mediengeräte ist identisch, unabhängig davon, ob Ihre Erfahrung auf [ein holografisches oder ein immersives Gerät zielt.](../discover/mixed-reality.md#the-mixed-reality-spectrum) Beachten Sie vor allem die Gerätefunktion und -skalierung. Sie können die reale Welt in Mixed Reality sehen, daher sollten Sie die richtige Skalierung basierend auf der Erfahrung verwalten.

## <a name="authoring-assets"></a>Erstellen von Ressourcen

Wir beginnen mit den Möglichkeiten, Ressourcen für Ihr Projekt zu erhalten:
1. Erstellen von Objekten (Erstellungstools und Objekterfassung)
2. Erwerb von Assets (Onlinekauf von Assets)
3. Portieren von Ressourcen (Verwenden vorhandener Ressourcen)
4. Assets von Überlagerungen (Importieren von Assets von Drittanbietern)

### <a name="creating-assets"></a>Erstellen von Ressourcen

**Erstellungstools**<br>
Zunächst können Sie ihre eigenen Ressourcen auf verschiedene Arten erstellen. 3D-Menschen verwenden verschiedene Anwendungen und Tools, um Modelle zu erstellen, die aus Gittermodellen, **Texturen** und Materialien **bestehen.** Dieser wird dann in einem Dateiformat gespeichert, das von der von der App verwendeten Grafik-Engine importiert oder verwendet werden kann, z. **B. . FBX** oder **. OBJ**. Jedes Tool, das ein Modell generiert, das von der ausgewählten Grafik-Engine unterstützt wird, funktioniert auf **HoloLens.** Unter den 3D-Frauen entscheiden sich viele für die Verwendung von [Autodesks Maya,](https://www.youtube.com/watch?v=q0K3n0Gf8mA) da sie HoloLens, um die Art und Weise zu transformieren, wie Ressourcen erstellt werden. Wenn Sie schnell etwas erhalten möchten, [](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) können Sie auch die 3D Builder verwenden, die im Windows zum Exportieren von ist. OBJ für die Verwendung in Ihrer Anwendung.

**Objekterfassung**<br>
Es gibt auch die Option zum Erfassen von Objekten in 3D. Das Erfassen von unanimierten Objekten in 3D und deren Bearbeitung mit Software zur Erstellung digitaler Inhalte wird mit dem 3D-Druck immer beliebter. Mit dem **Kinect 2-Sensor** und 3D Builder Können Sie mithilfe des Erfassungsfeatures Objekte aus realen Objekten erstellen. [](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) Dies ist auch eine [Reihe von](https://en.wikipedia.org/wiki/Comparison_of_photogrammetry_software) Tools, um dies bei der **Fotogrammetrie** zu erreichen, indem mehrere Bilder verarbeitet werden, um zusammengehefte und Gitter- und Texturen zu gittern.

### <a name="purchasing-assets"></a>Erwerb von Ressourcen

Eine weitere hervorragende Option ist der Erwerb von Ressourcen für Ihre Erfahrung. Es gibt eine Reihe von Ressourcen, die über Dienste wie [unity asset Store](https://www.assetstore.unity3d.com/) oder [TurboSquid](https://www.turbosquid.com/) verfügbar sind.

Wenn Sie Ressourcen von einem Drittanbieter erwerben, sollten Sie immer die folgenden Eigenschaften überprüfen:
* **Was ist die Polyanzahl?**
  * Passt sie in Ihr Budget?
* **Gibt es Detailebenen (LODs) für das Modell?**
  * Mit der Detailebene "Modelle" können Sie die Details eines Modells für die Leistung skalieren.
* **Ist die Quelldatei verfügbar?**
  * Nicht im [Unity Asset Store,](https://www.assetstore.unity3d.com/) aber immer in Diensten wie [TurboSquid enthalten.](https://www.turbosquid.com/)
  * Ohne die Quelldatei können Sie das Asset nicht ändern.
  * Stellen Sie sicher, dass die bereitgestellte Quelldatei von Ihren 3D-Tools importiert werden kann.
* **Wissen, was Sie erhalten**
  * Werden Animationen bereitgestellt?
  * Überprüfen Sie die Inhaltsliste der Ressource, die Sie erwerben.

### <a name="porting-assets"></a>Portieren von Ressourcen

In einigen Fällen werden Ihnen vorhandene Ressourcen übergeben, die ursprünglich für andere Geräte und verschiedene Apps erstellt wurden. In den meisten Fällen können diese Objekte in Formate konvertiert werden, die mit der Grafik-Engine kompatibel sind, die ihre App verwendet.

Beim Portieren von Ressourcen zur Verwendung in Ihrer HoloLens-Anwendung sollten Sie die folgenden Fragen stellen:
* **Können Sie direkt importieren oder müssen sie in ein anderes Format konvertiert werden?** Überprüfen Sie das Format, das Sie mit der verwendeten Grafik-Engine importieren.
* **Wenn die Konvertierung in ein kompatibles Format verloren geht?** Manchmal können Details verloren gehen, oder der Import kann dazu führen, dass Artefakte in einem 3D-Erstellungstool bereinigt werden müssen.
* **Wie lautet die Dreiecks-/Polygonanzahl für das Medienobjekt?** Basierend auf dem Budget für Ihre Anwendung können Sie [Simplygon](https://www.simplygon.com/) oder ähnliche Tools verwenden, um die ursprüngliche Ressource entsprechend Ihrem Anwendungsbudget zu dezimieren (prozedural oder manuell die Polyanzahl zu reduzieren).

### <a name="outsourcing-assets"></a>Assets des Assets "Assets"

Eine weitere Option für größere Projekte, die mehr Ressourcen erfordern, als Ihr Team erstellen kann, ist das Auslagern der Ressourcenerstellung. Der Prozess des Auslagerns umfasst die Suche nach dem richtigen Studio oder der richtigen Agentur, die auf Asset-Assets spezialisiert ist. Dies kann die teuerste Option, aber auch die flexibelste lösungsfähig sein.
* **Definieren Sie eindeutig, was Sie anfordern.**
  * Geben Sie so viele Details wie möglich an.
  * Front-, Side- und Back-Konzeptbilder
  * Referenzgrafik zum Anzeigen von Medienobjekten im Kontext
  * Skalierung des Objekts (in der Regel in Centimetern angegeben)
* **Bereitstellen eines Budgets**
  * Polyanzahlbereich
  * Anzahl der Texturen
  * Typ des Shaders (für Unity und HoloLens sollten Sie immer zuerst mobile Shader verwenden)
* **Grundlegendes zu den Kosten**
  * Wie sieht die Richtlinie für das Auslagern von Änderungsanforderungen aus?

Das Auslagern kann basierend auf ihrer Projektzeitachse gut funktionieren, erfordert jedoch mehr Überwachung, um sicherzustellen, dass Sie die richtigen Ressourcen erhalten, die Sie beim ersten Mal benötigen.
