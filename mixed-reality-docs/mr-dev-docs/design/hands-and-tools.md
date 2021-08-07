---
title: Hand- und Bewegungscontroller
description: Erfahren Sie mehr über Interaktionsmodelle für Hände und Motion-Controller, die die Grenze zwischen dem virtuellen und dem physischen entfernen können.
author: shengkait
ms.author: shentan
ms.date: 04/26/2019
ms.topic: article
keywords: Mixed Reality, Hände, Motion-Controller, Interaktion, Design, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 3a54d707260a3e5aebd83a53b62098504c86c9fea7b2ecbb49d3dbd8b72400dd
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213696"
---
# <a name="hands-and-motion-controllers"></a>Hand- und Bewegungscontroller

## <a name="scenarios"></a>Szenarien

Nachdem Sie die [Übersicht über](interaction-fundamentals.md)die Interaktion gelesen haben, wählen Sie das Interaktionsmodell hand und motion controller aus. Dies bedeutet, dass Sie eine Anwendung entwickeln, die erfordert, dass Benutzer zwei Hände verwenden müssen, um mit der holografischen Welt zu interagieren. Ihre Anwendung wird das Ziel erreichen, die Grenze zwischen virtuellem und physischem Netzwerk zu entfernen.

Einige spezifische Szenarien können sein:
* Bereitstellen von virtuellen 2D-Bildschirmen für Information Worker mit Angeboten zum Anzeigen und Steuern von Inhalten auf der Benutzeroberfläche
* Bereitstellen von Tutorials und Leitfäden für Fertigungslinien
* Entwickeln von professionellen Werkzeugen für die Unterstützung und Ausbildung von Medizinern  
* Verwenden von virtuellen 3D-Objekten zum Schmücken der Realwelt oder zum Erstellen einer zweiten Welt 
* Erstellen von standortbezogenen Diensten und Spielen, die die Realwelt als Hintergrund verwenden

<br>

---

## <a name="hands-and-motion-controllers-modalities"></a>Hände und Bewegungssteuerungen

:::row:::
    :::column:::
       [![Direkte Manipulation mit den Händen](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)<br>
       ### <a name="direct-manipulation-with-handsbr"></a>[Direkte Manipulation mit den Händen](direct-manipulation.md)<br>
       Modales Anwenden der Macht von Händen, die Benutzer verwenden können, um Hologramme zu berühren und zu bearbeiten. Durch die Verwendung von alltäglichen Erfahrungen und die Bereitstellung geeigneter visueller Möglichkeiten können Benutzer die gleiche Art und Weise verwenden, reale Objekte zu bearbeiten, um mit virtuellen Objekten zu interagieren.
    :::column-end:::
    :::column:::
       [![Zeigen und Ausführen mit den Händen](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)<br>
        ### <a name="point-and-commit-with-handsbr"></a>[Zeigen und Ausführen mit den Händen](point-and-commit.md)<br>
        Diese Variante ermöglicht es Benutzern, mit Hologrammen in einer Entfernung zu interagieren. Sie ermöglicht es Benutzern, die Umgebung optimal zu nutzen. Benutzer können Hologramme überall platzieren und trotzdem aus beliebiger Entfernung darauf zugreifen. Die mentalen Modelle und Gesten zum Steuern und Bearbeiten von 2D- und 3D-Hologrammen sind stark mit denen der direkten Manipulation synchronisiert.
    :::column-end:::
    :::column:::
       [![Bewegungscontroller](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)<br>
       ### <a name="motion-controllersbr"></a>[Motion-Controller](motion-controllers.md)<br>
       Motion-Controller erweitern die physischen Funktionen des Benutzers mit präzisen Interaktionen über einen Bereich von Entfernungen, während eine oder beide Hände verwendet werden. Dieses Hardwareaccessement bietet Verknüpfungen zu vielen häufig verwendeten Interaktionen und bietet sicheres, taktiles Feedback für verschiedene Aktionen. Motion-Controller sind derzeit nur für WMR-Szenarien (Windows Mixed Reality) verfügbar. 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a>Siehe auch
* [Anvisieren mit dem Kopf und Ausführen](gaze-and-commit.md)
* [Anvisieren mit dem Kopf und Verweilen](gaze-and-dwell.md)
* [Direkte Manipulation mit den Händen](direct-manipulation.md)
* [Zeigen und Ausführen mit den Händen](point-and-commit.md)
* [Freihändig](hands-free.md)
