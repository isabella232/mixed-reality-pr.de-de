---
title: 'Fallstudie: Lektionen aus der Lowe-Kita'
description: Das HoloLens-Team möchte einige der bewährten Methoden teilen, die aus dem HoloLens-Projekt von Lowe abgeleitet wurden.
author: brandonbray
ms.author: kevincol
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Lowe es, HoloLens, Tee, Fallstudie
ms.openlocfilehash: f2428a23e07d62156d38f43dfd5d6ddda20d57340d17908cf326ca9f37d223b9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210390"
---
# <a name="case-study---lessons-from-the-lowes-kitchen"></a>Fallstudie: Lektionen aus der Lowe-Kita

Das HoloLens-Team möchte einige der bewährten Methoden teilen, die aus dem HoloLens-Projekt von Lowe abgeleitet wurden. Im Folgenden finden Sie ein Video von lowes HoloLens, das auf der Satya-Ignite-Konferenz 2016 projiziert wird.
<br>
>[!VIDEO https://www.youtube.com/embed/gC_4JxF0e_k]

## <a name="lowes-hololens-best-practices"></a>Lowes HoloLens Bewährte Methoden

In den beiden Videos werden bewährte Methoden behandelt, die vom lowes HoloLens Pilot abgeleitet wurden, der sich seit April 2016 in zwei Lowe-Filialen befand. Die wichtigsten Themen sind:
* Maximieren der Leistung für ein mobiles Gerät
* Erstellen von UX-Methoden mit einem vollständigen holografischen Frame (2. Talk)
* Genauigkeitsausrichtung (2. Talk)
* Gemeinsame holografische Erfahrungen (2. Talk)
* Interagieren mit Kunden (2. Gespräch)

## <a name="video-1"></a>Video 1

**Maximieren der Leistung für ein mobiles Gerät** HoloLens ist ein nicht eigenständiges Gerät, wobei die gesamte Verarbeitung auf dem Gerät erfolgt. Dies erfordert eine mobile Plattform und eine Mentalität ähnlich der Erstellung mobiler Anwendungen. Microsoft empfiehlt, dass Ihre HoloLens-Anwendung 60FPS verwaltet, um Ihren Benutzern ein gutes Erlebnis zu bieten. Niedrige FPS können zu instabilen Hologrammen führen.

Einige der wichtigsten Punkte, die bei der Entwicklung auf HoloLens zu betrachten sind, sind die Ressourcenoptimierung/-dezimation mit benutzerdefinierten Shadern (kostenlos im [HoloLens Toolkit](https://github.com/Microsoft/HoloToolkit-Unity)verfügbar). Ein weiterer wichtiger Aspekt ist die Messung der Bildfrequenz von Anfang an Ihres Projekts. Je nach Projekt kann die Reihenfolge, in der Ihre Ressourcen angezeigt werden, auch ein großer Mitwirkender sein.
<br>
>[!VIDEO https://www.youtube.com/embed/o0QIPwgiP9A]

## <a name="video-2"></a>Video 2

**Erstellen von UX-Methoden mit einem vollständigen holografischen Frame** Es ist wichtig, die Platzierung von Hologrammen in einer physischen Welt zu verstehen. Mit Lowe es werden verschiedene UX-Methoden behandelt, mit denen Benutzer Hologramme aus nächster Nähe erleben und gleichzeitig die größere Umgebung von Hologrammen sehen können.

**Genauigkeitsausrichtung** Für das Lowe-Szenario war es von entscheidender Bedeutung, dass die Genauigkeit der Hologramme an der physischen Luft ausgerichtet ist. Wir erläutern Techniken, mit denen sichergestellt werden kann, dass Benutzer davon überzeugt werden, dass sich ihre physische Umgebung geändert hat.

**Gemeinsame holografische Erfahrungen** Dies ist die primäre Art und Weise, wie die Lowe-Erfahrung genutzt wird. Eine Person kann die Arbeitsfläche ändern, und die andere Person sieht die Änderungen. Wir haben dies als "gemeinsame Erfahrungen" bezeichnet.

**Interagieren mit Kunden** Die Designer von Lowe verwenden keine HoloLens, müssen aber sehen, was die Kunden sehen. Wir zeigen, wie Sie erfassen, was dem Kunden in einer UWP-Anwendung angezeigt wird.
<br>
>[!VIDEO https://www.youtube.com/embed/LceMdyKZ4PI]
