---
title: Spectator View
description: Visualisieren Sie Hologramme von einem externen Gerät, um ein Mixed-Reality-Erlebnis auf einem externen Display zu darzustellen oder aufzunehmen.
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Spectator View, iPhone, iOS, iPad, OpenCV, Kamera, ARKit, HoloLens, Mixed Reality, MixedRealityToolkit, Demo, aufzeichnen
ms.openlocfilehash: 1f61d2094ec2762ab22576d2eac85ed6bf81d5c7
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008610"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a>Spectator View für HoloLens und HoloLens 2

![Marker](images/SpecViewPhoneHero.jpg)

Wenn Sie eine HoloLens tragen, vergessen Sie leicht, dass eine Person ohne HoloLens nicht dieselben Wunder erleben kann, die Sie sehen. Mit Spectator View können andere sehen, was ein HoloLens-Benutzer auf einem 2D-Bildschirm sieht. Es ist außerdem ein schneller und kostengünstiger Ansatz, um Hologramme in HD mit mobilen Geräten aufzunehmen und mit Videokameras Aufnahmen von Hologrammen in hoher Qualität zu erhalten.

## <a name="key-resources"></a>Wichtige Ressourcen

* [**Spectator View auf GitHub**](https://github.com/microsoft/MixedReality-SpectatorView)
* [**Spectator View-Dokumentation**](https://microsoft.github.io/MixedReality-SpectatorView/README.html)
* [**Spectator View-Beispiele**](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)

## <a name="use-cases"></a>Anwendungsfälle

* Sie können ein Mixed Reality-Erlebnis mithilfe eines iPhone- oder Android-Geräts aufzeichnen. Zeichnen Sie in Full-HD auf, und wenden Sie Anti-Aliasing auf Hologramme und Schatten an – eine kostengünstige und schnelle Möglichkeit, Videos von Hologrammen aufzunehmen.
* Streamen Sie von Ihrem iPhone oder iPad verzögerungsfrei Mixed Reality-Erlebnisse live auf ein Apple TV!
* Teilen Sie das Erlebnis mit Gästen: Lassen Sie Benutzer ohne HoloLens Hologramme direkt auf Ihren Smartphones oder Tablets erleben.

## <a name="current-features"></a>Aktuelle Features

* Synchronisierung von Hologrammen im Raum, sodass alle die Hologramme an genau der gleichen Stelle sehen.
* Unterstützung für iOS- (ARKit-fähige Geräte) und Android-Geräte (ARCore-fähige Geräte).
Mehrere iOS-Gäste.
Aufzeichnung von Video + Hologrammen + Raumklang + Hologrammklang.
Freigabeblatt, auf dem Sie Videos speichern, sie per E-Mail senden oder sie mit anderen unterstützten Apps teilen können.

![Marker](images/SpecViewPhoneDemo.jpg)
![Marker](images/hololensspectatorview-500px.jpg) ![Marker](images/spectatorview-300px.png)

In der folgenden Tabelle sind verschiedene Funktionen von Spectator View aufgeführt. Wählen Sie die Option aus, die Ihren Anforderungen an Videoaufzeichnung am besten entspricht:

|      Funktionalität                                | Mobile                  |                    Videokamera              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| HD-Qualität                           |         Full HD         |        Filmen in professioneller Qualität (durch die Videokamera bestimmt)      |
| Einfache Kamerabewegung                 |            ✔            |                      ✔                      |
| Third-Person-Ansicht                    |            ✔            |                      ✔                      |
| Kann auf Bildschirme gestreamt werden           |            ✔            |                      ✔                      |
| Portabel                             |            ✔            |                                             |
| Drahtlos                             |            ✔            |                                             |
| Zusätzlich erforderliche Hardware         |     Android-Smartphone, iPhone    | HoloLens + Rig + Stativ + Videokamera + PC + Unity |
| Hardwareinvestition                  |           Niedrig            |                     Hoch                    |
| Plattformübergreifend                       |           Android, iOS   |                                             |
| Synchronisierte Inhalte                 |            ✔            |                      ✔                      |
| Dauer des Runtime-Setups               |         Sofort          |                     Langsam                    |
## <a name="see-also"></a>Siehe auch

* [Mixed-Reality-Aufnahme](../../mixed-reality-capture.md) 
* [Mixed Reality-Aufnahme für Entwickler](mixed-reality-capture-for-developers.md)
* [Gemeinsame Erlebnisse in Mixed Reality](shared-experiences-in-mixed-reality.md)
