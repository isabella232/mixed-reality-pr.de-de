---
title: HP-Reverb-G2-Controller in Unity
description: Anweisungen zur Verwendung der HP-Reverb-G2-Controller in steamvr und Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 10/14/2020
ms.topic: article
keywords: Unity, Reverb, Reverb G2, HP-Simulator G2, gemischte Realität, Entwicklung, Motion Controller, Benutzereingaben, Features, neues Projekt, Emulator, Dokumentation, Anleitungen, Features, Hologramme, Spieleentwicklung
ms.openlocfilehash: 3add2ae52fbaba087da257212e1d8ddfdffe702a
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638387"
---
# <a name="hp-reverb-g2-controllers-in-unity"></a>HP-Reverb-G2-Controller in Unity

## <a name="getting-started"></a>Erste Schritte

Es ist kein zusätzliches Setup erforderlich, um den HP-Reverb-G2-Controller zu verwenden, wenn Sie für steamvr entwickeln oder die Windows Mixed Reality-Eingabe-API (XR) verwenden. WSA. Eingabe). Allerdings sind die Schaltflächen A, B, X, Y und der squeeze-Trigger zurzeit über den Eingabe-Manager nicht zugänglich, es sei denn, Sie verwenden steamvr. Unterstützung für die zusätzlichen Reverb-G2-Eingaben ist in naher Zukunft verfügbar. Achten Sie also darauf, dass Sie die Überprüfung wirklich durchführt!

## <a name="porting-existing-applications"></a>Portieren vorhandener Anwendungen

Wenn Sie bereits über eine vorhandene App verfügen, die Sie für Windows Mixed Reality-immersive Headsets entwickeln, sehen Sie sich die Abschnitte [Portierungs Handbuch](../porting-apps/porting-guides.md) und [Projekteinstellungen](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project#unity-porting-guidance) an, um allgemeine Vorschläge zu erhalten.

## <a name="mapping-input"></a>Zuordnung von Eingaben

Wenn Sie bereit sind, Ihre Eingabe Zuordnung für Ihre neuen Controller einzurichten und in Betrieb zu nehmen, beginnen Sie mit dem Abschnitt [Eingabe Zuordnung](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input#unity-porting-guidance) des immersiven portieren-Handbuchs. Anweisungen zum Konfigurieren von Eingaben in Unity finden Sie in [Gesten und Bewegungs Controllern](gestures-and-motion-controllers-in-unity.md)sowie eine vollständige [Schaltfläche und eine Tabellen Zuordnung](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) .

## <a name="see-also"></a>Weitere Informationen
* [Aktualisierung für SteamVR](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)