---
title: Übersicht über das Kamerasystem
description: Landing page for camera system in MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Kamera,
ms.openlocfilehash: cfb40b00d81133ad40e0e4d7a7b2ad87ee645e36
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177043"
---
# <a name="camera-system-overview"></a>Übersicht über das Kamerasystem

Das Kamerasystem ermöglicht es dem Microsoft Mixed Reality Toolkit, die Kamera der Anwendung für die Verwendung in Mixed Reality-Anwendungen zu konfigurieren und zu optimieren. Mithilfe des Kamerasystems können Anwendungen geschrieben werden, um sowohl nicht transparente (z. B. virtual reality) als auch transparente (z. B. Microsoft HoloLens) Geräte zu unterstützen, ohne Code schreiben zu müssen, um zwischen den einzelnen Anzeigetypen zu unterscheiden und diese zu berücksichtigen.

## <a name="enabling-the-camera-system"></a>Aktivieren des Kamerasystems

Das Kamerasystem wird vom MixedRealityToolkit-Objekt (oder einer anderen Dienstregistrierungskomponente) verwaltet.

Die folgenden Schritte setzen die Verwendung des MixedRealityToolkit-Objekts voraus. Die für andere Dienstregistrierungsstellen erforderlichen Schritte können unterschiedlich sein.

1. Wählen Sie das MixedRealityToolkit-Objekt in der Szenenhierarchie aus.

    ![KONFIGURIERTE MRTK-Szenenhierarchie](../images/MRTK_ConfiguredHierarchy.png)

2. Navigieren Sie im Bereich Inspector zum Abschnitt kamerasystem, und stellen Sie sicher, dass **Kamerasystem aktivieren** aktiviert ist.

    ![Aktivieren des Kamerasystems](../images/camera-system/EnableCameraSystem.png)

3. Wählen Sie die Kamerasystemimplementierung aus. Die vom MRTK bereitgestellte Standardklassenimplementierungen sind `MixedRealityCameraSystem` .

    ![Auswählen der Kamerasystemimplementierung](../images/camera-system/SelectCameraSystemType.png)

4. Auswählen des gewünschten Konfigurationsprofils

    ![Auswählen des Kamerasystemprofils](../images/camera-system/SelectCameraProfile.png)

## <a name="configuring-the-camera-system"></a>Konfigurieren des Kamerasystems

### <a name="settings-providers"></a>Einstellungen-Anbieter

![Kamera-Einstellungen-Anbieter](../images/camera-system/CameraSettingsProviders.png)

Anbieter von Kameraeinstellungen ermöglichen die plattformspezifische Konfiguration der Kamera. Diese Einstellungen können benutzerdefinierte Konfigurationsschritte und/oder Komponenten enthalten.

Anbieter können hinzugefügt werden, indem Sie auf die Schaltfläche **Kamera Einstellungen Anbieter hinzufügen** klicken. Sie können entfernt werden, indem Sie rechts neben **-** dem Anbieternamen auf die Schaltfläche klicken.

> [!Note]
> Nicht für alle Plattformen ist ein Anbieter für Kameraeinstellungen erforderlich. Wenn es keine Anbieter gibt, die mit der Plattform kompatibel sind, auf der die Anwendung ausgeführt wird, wendet das Microsoft Mixed Reality Toolkit grundlegende Standardwerte an.

### <a name="display-settings"></a>Anzeigeeinstellungen

![Kameraanzeige Einstellungen](../images/camera-system/CameraDisplaySettings.png)

Anzeigeeinstellungen werden sowohl für nicht transparente (z. B. Virtual Reality) als auch für transparente (z. B. Microsoft HoloLens) Anzeigen angegeben. Die Kamera wird zur Laufzeit mithilfe dieser Einstellungen konfiguriert.

**Near Clip**

Die nahe Clipebene ist in Metern die nächstgelegene, die ein virtuelles Objekt zur Kamera haben und dennoch gerendert werden kann. Für den größtmöglichen Benutzerfreundlichkeit wird empfohlen, diesen Wert größer als 0 (null) zu machen. Die vorherige Abbildung enthält Werte, die sich auf einer Vielzahl von Geräten als vertraut erwiesen haben.

**Far Clip**

Die weit entfernte Clipebene ist in Metern die am weitesten entfernte, die ein virtuelles Objekt für die Kamera sein und weiterhin gerendert werden kann. Für transparente Geräte wird empfohlen, dass dieser Wert relativ nahe beieinander liegt, da er den realen Raum nicht übermäßig überschreitet und die immersiven Qualitäten der Anwendung unterbricht.

**Flags löschen**

Der Wert clear flags gibt an, wie die Anzeige beim Zeichnen gelöscht wird. Für Virtual Reality-Umgebungen wird dieser Wert am häufigsten auf Skybox festgelegt. Für transparente Anzeigen wird empfohlen, diese auf Farbe festzulegen.

**Hintergrundfarbe**

Wenn die clear-Flags nicht auf Skybox festgelegt sind, wird die Eigenschaft für die Hintergrundfarbe angezeigt.

**Quality Einstellungen**

Der Wert der Qualitätseinstellungen gibt die Grafikqualität an, die Unity beim Rendern der Szene verwenden soll. Die Qualitätsstufe ist eine Einstellung auf Projektebene und nicht spezifisch für eine Kamera. Weitere Informationen finden Sie im Artikel [Qualität](https://docs.unity3d.com/Manual/class-QualitySettings.html) in der Unity-Dokumentation.

## <a name="see-also"></a>Siehe auch

- [Dokumentation zur Kamerasystem-API](xref:Microsoft.MixedReality.Toolkit.CameraSystem)
- [Erstellen eines Kamera-Einstellungen-Anbieters](create-settings-provider.md)
