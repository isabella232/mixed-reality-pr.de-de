---
title: Einstellungen für die Benutzererfahrung
description: Dokumentation zu den verschiedenen Benutzererfahrungseinstellungen für MRTK
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 19d812ccfa9c0317e40dee2b7d03220848782cef955ba859a150b4f4adc8aa99
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203246"
---
# <a name="experience-settings"></a>Einstellungen für die Benutzererfahrung

Eine der Herausforderungen beim Erstellen der Benutzeroberfläche für Mixed Reality ist die Ausrichtung auf verschiedene Benutzeroberflächen. Mit MRTK können Sie und für Ihre Szene festlegen und konfigurieren Folgendes, um sich entsprechend der `Target Experience Scale` `Content Offset` Zielskala zu verhalten.

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

Dieser Parameter gibt die Höhe über [](scene-content.md) dem Boden an, um Mixed Reality Szeneninhalt zu versatzen, wenn **Ausrichtungstyp** auf Ausrichtung mit **Erfahrungsskala festgelegt ist.**
