---
title: Einstellungen für die Benutzererfahrung
description: Dokumentation zu den verschiedenen Benutzererfahrungseinstellungen für MRTK
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: ab3a449b064d4a1c8f2bf76154f7a25c688693e1
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177357"
---
# <a name="experience-settings"></a>Einstellungen für die Benutzererfahrung

Eine der Herausforderungen beim Erstellen einer Benutzeroberfläche für Mixed Reality ist die Ausrichtung auf verschiedene Benutzeroberflächen. Mit MRTK können Sie und für Ihre Szene festlegen und konfigurieren Folgendes, um sich entsprechend der `Target Experience Scale` `Content Offset` Zielskala zu verhalten.

- Mixed Reality Szeneninhalt
- Begrenzungssystem

  ![Erfahrung Einstellungen im MRTK-Konfigurationsprofil](../images/experience-settings/ExperienceSettings.png)

## <a name="target-experience-scale"></a>Skalierung der Zielerfahrung

Die **Zielumgebungsskala** gibt die Umgebung an, für die die Umgebung entworfen wurde. Sie kann die folgenden Werte übernehmen.

* *OrientationOnly:* Eine Erfahrung, bei der nur die Headsetausrichtung verwendet und die Schwerkraft ausgerichtet ist. Der Ursprung des Koordinatensystems befindet sich auf Der Kopfebene.
* *"Seated":* Eine Beerfahrung, die für die Verwendung mit dem Platz konzipiert ist. Der Ursprung des Koordinatensystems befindet sich auf Bodenebene.
* *Stehend:* Eine Erfahrung, die für den standfesten Einsatz konzipiert ist. Der Ursprung des Koordinatensystems befindet sich auf Bodenebene.
* *Raum:* Eine Erfahrung, die entwickelt wurde, um Bewegungen in einem Raum zu unterstützen. Der Ursprung des Koordinatensystems befindet sich auf Bodenebene.
* *Welt:* Eine Erfahrung, die dafür konzipiert ist, die physische Welt zu nutzen und sich durch diese zu bewegen. Der Ursprung des Koordinatensystems befindet sich auf Der Kopfebene.

## <a name="content-offset"></a>Inhaltsoffset

Dieser Parameter gibt die Höhe über [](scene-content.md) dem Boden an, um Mixed Reality Szeneninhalt zu versatzen, wenn **Ausrichtungstyp** auf Ausrichtung an Der **Erfahrungsskala ausgerichtet ist.**
