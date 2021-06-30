---
title: Windows Mixed Reality der Kameraeinstellungen
description: Dokumentation zur Verwendung Windows Mixed Reality Kameraeinstellungen in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Kamera,
ms.openlocfilehash: 49b178b7ebd1fbcdaab9648baeaa6abfa9e885ea
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121638"
---
# <a name="windows-mixed-reality-camera-settings-provider"></a>Windows Mixed Reality des Kameraeinstellungsanbieters

Der Windows Mixed Reality-Kameraeinstellungsanbieter bestimmt den Gerätetyp, auf dem die Anwendung ausgeführt wird, und wendet die entsprechenden Konfigurationseinstellungen basierend auf der Anzeige an (transparent oder nicht transparent).

## <a name="enabling-the-windows-mixed-reality-camera-settings-provider"></a>Aktivieren des Windows Mixed Reality Kameraeinstellungsanbieters

Die folgenden Schritte setzen die Verwendung des MixedRealityToolkit-Objekts voraus. Die für andere Dienstregistrierungen erforderlichen Schritte können unterschiedlich sein.

1. Wählen Sie das MixedRealityToolkit-Objekt in der Szenenhierarchie aus.

    ![MRTK– Konfigurierte Szenenhierarchie](../images/MRTK_ConfiguredHierarchy.png)

2. Navigieren Sie im Inspektorbereich zum Abschnitt Kamerasystem, und erweitern Sie den Abschnitt **Kameraeinstellungsanbieter.**

    ![Erweitern von Einstellungsanbietern](../images/camera-system/ExpandProviders.png)

3. Klicken **Sie auf Kameraeinstellungsanbieter hinzufügen,** und erweitern Sie den neu hinzugefügten Eintrag **Neue Kameraeinstellungen.**

    ![Erweitern des neuen Einstellungsanbieters](../images/camera-system/ExpandNewProvider.png)

4. Auswählen des Windows Mixed Reality Kameraeinstellungsanbieters

    ![Auswählen Windows Mixed Reality Einstellungsanbieters](../images/camera-system/SelectWindowsMixedRealitySettings.png)

> [!NOTE]
> Wenn Sie die Standardprofile des Microsoft Mixed Reality Toolkits verwenden, ist Windows Mixed Reality Kameraeinstellungsanbieter bereits aktiviert und konfiguriert.

## <a name="configuring-the-windows-mixed-reality-camera-settings-provider"></a>Konfigurieren des Windows Mixed Reality Kameraeinstellungsanbieters

Die Windows Mixed Reality Kameraeinstellungen unterstützt auch ein Profil. Dieses Profil bietet die folgenden Optionen:

![Windows Mixed Reality konfiguration der Kameraeinstellungen](../images/camera-system/WMRCameraSettingsProfile.png)

### <a name="render-mixed-reality-capture-from-the-photovideo-camera"></a>Rendern der Mixed Reality-Aufnahme von der Foto-/Videokamera

Mit dieser Einstellung auf HoloLens 2 können Sie hologrammausrichtung in Ihren Mixed Reality-Erfassungen aktivieren. Wenn diese Option aktiviert ist, stellt die Plattform der App eine zusätzliche HolographicCamera zur Verfügung, wenn ein Mixed Reality-Aufnahmefoto oder -video aufgenommen wird. Diese HolographicCamera bietet Ansichtsmatrizen, die der Position der Foto-/Videokamera entspricht, und stellt Projektionsmatrizen mithilfe des Sichtfelds der Foto-/Videokamera zur Anwendung. Dadurch wird sichergestellt, dass Hologramme, z. B. Handgitter, in der Videoausgabe sichtbar ausgerichtet bleiben.

### <a name="hololens-2-reprojection-method"></a>HoloLens 2-Methode für die Neuprojektion

Legt die anfängliche Methode für das HoloLens 2 fest. Die Standardempfehlung ist die Verwendung einer Tiefenumprojektion, da alle Teile der Szene unabhängig voneinander basierend auf ihrer Entfernung vom Benutzer stabilisiert werden. Wenn Hologramme weiterhin instabil erscheinen, stellen Sie sicher, dass alle Objekte ihre Tiefe ordnungsgemäß an den Tiefenpuffer übermittelt haben. Dies ist manchmal eine Shadereinstellung. Wenn die Tiefe ordnungsgemäß übermittelt zu werden scheint und die Instabilität weiterhin vorhanden ist, versuchen Sie die automatische planare Stabilität, die den Tiefenpuffer verwendet, um eine Stabilitätsebene zu berechnen. Wenn eine App nicht genügend Tiefendaten übermitteln kann, damit eine dieser Optionen verwendet werden kann, wird eine planare Neuprojektion als Fallback bereitgestellt. Diese Methode basiert auf den von einer App bereitgestellten Fokuspunktdaten über [SetFocusPointForFrame.](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.SetFocusPointForFrame.html)

Um die Neuprojektionsmethode zur Laufzeit zu aktualisieren, greifen Sie wie `WindowsMixedRealityReprojectionUpdater` hier beschrieben auf zu:

```c#
var reprojectionUpdater = CameraCache.Main.EnsureComponent<WindowsMixedRealityReprojectionUpdater>();
reprojectionUpdater.ReprojectionMethod = HolographicDepthReprojectionMethod.AutoPlanar;
```

Dies muss nur einmal aktualisiert werden, und der Wert wird für alle nachfolgenden Frames wiederverwendet. Wenn die Methode häufig aktualisiert wird, empfiehlt es sich, das Ergebnis zwischenspeichern anstatt `EnsureComponent` es häufig auf aufruft.

## <a name="see-also"></a>Siehe auch

- [Kamerasystemübersicht](camera-system-overview.md)
- [Erstellen eines Kameraeinstellungsanbieters](create-settings-provider.md)
- [Rendern Mixed Reality-Aufnahme von der PV-Kamera](/windows/mixed-reality/mixed-reality-capture-for-developers#render-from-the-pv-camera-opt-in)
- [Holografische Neuprojektion](/windows/mixed-reality/hologram-stability#reprojection)