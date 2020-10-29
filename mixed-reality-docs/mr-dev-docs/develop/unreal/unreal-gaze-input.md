---
title: Blick Eingabe in Unreal
description: Tutorial zum Einrichten von Blick Eingaben für hololens und Unreal Engine
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, holograms, hololens 2, Eye Tracking, Blick Eingaben, Head-eingebundene Anzeige, Unreal Engine
ms.openlocfilehash: 477fbdc9c7ddb3b4e890e62150651d9227d4c19e
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2020
ms.locfileid: "91684859"
---
# <a name="gaze-input"></a>Blick Eingabe

## <a name="overview"></a>Übersicht

Das [Windows Mixed Reality-Plug](https://docs.unrealengine.com/Platforms/VR/WMR/index.html) -in bietet keine integrierten Funktionen für die Überblicks Eingabe, aber hololens 2 unterstützt die Eye-Nachverfolgung. Die eigentlichen Überwachungsfunktionen werden von Unreal mit den von Unreal bereitgestellten **Anzeige** -und **Eye Tracking** -APIs bereitgestellt und umfassen Folgendes:

- Geräteinformationen
- Nach Verfolgungs Sensoren
- Ausrichtung und Position
- Clipping-Bereiche
- Daten-und Überwachungsinformationen für den Blick

Die vollständige Liste der Features finden Sie in [der Dokumentation zu](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) den Köpfen in der Head-bereit [Stellung](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) von Unreal.

Zusätzlich zu den Unreal-APIs sehen Sie sich die Dokumentation zu den [Augenblick-basierten Interaktionen](../../design/eye-gaze-interaction.md) für hololens 2 an, und informieren Sie sich darüber, wie die [Augen Verfolgung auf hololens 2](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) funktioniert.

> [!IMPORTANT]
> Die Eye-Nachverfolgung wird nur auf hololens 2 unterstützt.

## <a name="enabling-eye-tracking"></a>Aktivieren der Eye-Überwachung
Die Überblicks Eingabe muss in den hololens-Projekteinstellungen aktiviert werden, bevor Sie eine der Unreal-APIs verwenden können. Wenn die Anwendung gestartet wird, wird im folgenden Screenshot eine Zustimmungsaufforderung angezeigt.

- Wählen Sie **Ja** aus, um die Berechtigung festzulegen, und erhalten Sie Zugriff auf die Eingaben. Wenn Sie diese Einstellung jederzeit ändern müssen, finden Sie Sie in der App " **Einstellungen** ".

![Eye-Eingabe Berechtigungen](images/unreal/eye-input-permissions.png)

> [!NOTE] 
> Hololens Eye Tracking in Unreal hat nur einen einzelnen Blick Strahl für beide Augen und nicht die zwei Strahlen, die für die Stereoskopie erforderlich sind, was nicht unterstützt wird.

Das ist alles, was Sie tun müssen, um Ihre hololens 2-apps in Unreal mit Blick Eingaben zu versehen. Weitere Informationen zu Blick Eingaben und deren Auswirkungen auf Benutzer in gemischter Realität finden Sie unter den folgenden Links. Berücksichtigen Sie diese bei der Erstellung interaktiver Umgebungen.

## <a name="next-development-checkpoint"></a>Nächster Entwicklungs Prüfpunkt

Wenn Sie die unechte Development Checkpoint Journey befolgen, sind Sie in der Mitte, dass Sie die mrtk Core-Bausteine erkunden. Von hier aus können Sie mit dem nächsten Baustein fortfahren: 

> [!div class="nextstepaction"]
> [Handtracking](unreal-hand-tracking.md)

Oder springen Sie zu den Funktionen und APIs der Mixed Reality-Plattform:

> [!div class="nextstepaction"]
> [HoloLens-Kamera](unreal-hololens-camera.md)

Sie können jederzeit jederzeit zu den [unechten Entwicklungs Prüfpunkten](unreal-development-overview.md#2-core-building-blocks) zurückkehren.

## <a name="see-also"></a>Weitere Informationen
* [Kalibrierung](../../calibration.md)
* [Komfort](../../design/comfort.md)
* [Anvisieren und Ausführen](../../design/gaze-and-commit.md)
* [Spracheingabe](../../out-of-scope/voice-design.md)
