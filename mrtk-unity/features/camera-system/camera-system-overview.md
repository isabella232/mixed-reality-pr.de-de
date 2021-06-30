---
title: Kamerasystemübersicht
description: Landing Page für kamerasystem in MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Kamera,
ms.openlocfilehash: e3b7caacaa9baa67fd81f6d32f3fd8c9f123e66d
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121288"
---
# <a name="camera-system"></a>Kamerasystem

Das Kamerasystem ermöglicht es dem Microsoft Mixed Reality Toolkit, die Kamera der Anwendung für die Verwendung in Mixed Reality-Anwendungen zu konfigurieren und zu optimieren. Mithilfe des Kamerasystems können Anwendungen geschrieben werden, um sowohl nicht transparente (z. B. virtuelle Realität) als auch transparente (z.B. Microsoft HoloLens)-Geräte zu unterstützen, ohne Code schreiben zu müssen, um zwischen den einzelnen Anzeigetypen zu unterscheiden und diese zu unterstützen.

## <a name="enabling-the-camera-system"></a>Aktivieren des Kamerasystems

Das Kamerasystem wird vom MixedRealityToolkit-Objekt (oder einer anderen Dienstregistrierungskomponente) verwaltet.

Die folgenden Schritte setzen die Verwendung des MixedRealityToolkit-Objekts voraus. Die für andere Dienstregistrierungen erforderlichen Schritte können unterschiedlich sein.

1. Wählen Sie das MixedRealityToolkit-Objekt in der Szenenhierarchie aus.

    ![MRTK– Konfigurierte Szenenhierarchie](../images/MRTK_ConfiguredHierarchy.png)

2. Navigieren Sie im Inspektorbereich zum Abschnitt Kamerasystem, und stellen Sie sicher, dass **Kamerasystem** aktivieren aktiviert ist.

    ![Aktivieren des Kamerasystems](../images/camera-system/EnableCameraSystem.png)

3. Wählen Sie die Implementierung des Kamerasystems aus. Die vom MRTK bereitgestellte Standardklassenimplementierung ist `MixedRealityCameraSystem` .

    ![Auswählen der Kamerasystemimplementierung](../images/camera-system/SelectCameraSystemType.png)

4. Auswählen des gewünschten Konfigurationsprofils

    ![Auswählen des Kamerasystemprofils](../images/camera-system/SelectCameraProfile.png)

## <a name="configuring-the-camera-system"></a>Konfigurieren des Kamerasystems

### <a name="settings-providers"></a>Einstellungsanbieter

![Kameraeinstellungsanbieter](../images/camera-system/CameraSettingsProviders.png)

Kameraeinstellungsanbieter ermöglichen die plattformspezifische Konfiguration der Kamera. Diese Einstellungen können benutzerdefinierte Konfigurationsschritte und/oder Komponenten umfassen.

Anbieter können hinzugefügt werden, indem Sie auf die **Schaltfläche Add Camera Settings Provider (Anbieter für Kameraeinstellungen hinzufügen)** klicken. Sie können entfernt werden, indem Sie auf die Schaltfläche rechts vom **-** Anbieternamen klicken.

> [!Note]
> Nicht für alle Plattformen ist ein Kameraeinstellungsanbieter erforderlich. Wenn es keine Anbieter gibt, die mit der Plattform kompatibel sind, auf der die Anwendung ausgeführt wird, werden vom Microsoft Mixed Reality Toolkit grundlegende Standardwerte angewendet.

### <a name="display-settings"></a>Anzeigeeinstellungen

![Kameraanzeigeeinstellungen](../images/camera-system/CameraDisplaySettings.png)

Anzeigeeinstellungen werden sowohl für nicht transparente (z.B. Virtual Reality) als auch für transparente (z. B. Microsoft HoloLens) Anzeige angegeben. Die Kamera wird zur Laufzeit mithilfe dieser Einstellungen konfiguriert.

**Near Clip**

Die nahe Clipebene ist die nächstgelegene ( in Metern) , die ein virtuelles Objekt der Kamera am nächsten liegt und weiterhin gerendert werden kann. Für einen größtmöglichen Benutzerfreundlichkeit empfiehlt es sich, diesen Wert größer als 0 (null) zu machen. Das vorherige Bild enthält Werte, die sich auf einer Vielzahl von Geräten als bewertigend herausbilden.

**Far Clip**

Die entfernte Clipebene ist die weiteste in Metern, die ein virtuelles Objekt für die Kamera sein und noch gerendert werden kann. Für transparente Geräte wird empfohlen, dass dieser Wert relativ nahe ist, um den realen Raum nicht zu überschreiten und die immersiven Qualitäten der Anwendung zu unterbricht.

**Flags löschen**

Der Clear Flags-Wert gibt an, wie die Anzeige beim Gezeichneten gezeichnet wird. Bei Virtual Reality-Erfahrungen wird dieser Wert am häufigsten auf Skybox festgelegt. Bei transparenten Anzeigen wird empfohlen, dies auf Color (Farbe) zu setzen.

**Hintergrundfarbe**

Wenn die Clear-Flags nicht auf Skybox festgelegt sind, wird die Hintergrundfarbeigenschaft angezeigt.

**Qualitätseinstellungen**

Der Wert für die Qualitätseinstellungen gibt die Grafikqualität an, die Unity beim Rendern der Szene verwenden soll. Die Qualitätsstufe ist eine Einstellung auf Projektebene und nicht spezifisch für eine Kamera. Weitere Informationen finden Sie im Artikel [Qualität](https://docs.unity3d.com/Manual/class-QualitySettings.html) in der Unity-Dokumentation.

## <a name="see-also"></a>Siehe auch

- [Dokumentation zur Kamerasystem-API](xref:Microsoft.MixedReality.Toolkit.CameraSystem)
- [Erstellen eines Kameraeinstellungsanbieters](create-settings-provider.md)
