---
title: Windows Mixed Reality-Kameraeinstellungen
description: Dokumentation zur Verwendung Windows Mixed Reality Kamera im MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Kamera,
ms.openlocfilehash: 94e00f47dc565af0824ef6acf5c08a9e99d4529f
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145166"
---
# <a name="windows-mixed-reality-camera-settings-provider"></a>Windows Mixed Reality Anbieter von Kameraeinstellungen

Der Windows Mixed Reality Anbieter von Kameraeinstellungen bestimmt den Gerätetyp, auf dem die Anwendung ausgeführt wird, und wendet die entsprechenden Konfigurationseinstellungen basierend auf der Anzeige (transparent oder nicht transparent) an.

## <a name="enabling-the-windows-mixed-reality-camera-settings-provider"></a>Aktivieren des Anbieters für Windows Mixed Reality Kameraeinstellungen

In den folgenden Schritten wird davon ausgegangen, dass das MixedRealityToolkit-Objekt verwendet wird. Die für andere Dienstregistrierungsstellen erforderlichen Schritte können unterschiedlich sein.

1. Wählen Sie das MixedRealityToolkit-Objekt in der Szenenhierarchie aus.

    ![KONFIGURIERTE MRTK-Szenenhierarchie](../images/MRTK_ConfiguredHierarchy.png)

2. Navigieren Sie im Bereich Inspektor zum Abschnitt Kamerasystem, und erweitern Sie den Abschnitt Anbieter für **Kameraeinstellungen.**

    ![Erweitern von Einstellungsanbietern](../images/camera-system/ExpandProviders.png)

3. Klicken Sie auf **Kameraeinstellungsanbieter hinzufügen,** und erweitern Sie den neu hinzugefügten Eintrag **Neue Kameraeinstellungen.**

    ![Erweitern des neuen Einstellungsanbieters](../images/camera-system/ExpandNewProvider.png)

4. Wählen Sie den Anbieter Windows Mixed Reality Kameraeinstellungen aus.

    ![Auswählen Windows Mixed Reality Einstellungsanbieters](../images/camera-system/SelectWindowsMixedRealitySettings.png)

> [!NOTE]
> Wenn Sie die Standardprofile des Microsoft Mixed Reality Toolkits verwenden, ist der Anbieter Windows Mixed Reality Kameraeinstellungen bereits aktiviert und konfiguriert.

## <a name="configuring-the-windows-mixed-reality-camera-settings-provider"></a>Konfigurieren des Anbieters für Windows Mixed Reality Kameraeinstellungen

Die Windows Mixed Reality Kameraeinstellungen unterstützt auch ein Profil. Dieses Profil bietet die folgenden Optionen:

![Konfiguration der kameraeinstellungen Windows Mixed Reality](../images/camera-system/WMRCameraSettingsProfile.png)

### <a name="render-mixed-reality-capture-from-the-photovideo-camera"></a>Rendern der Mixed Reality-Aufnahme von der Foto-/Videokamera

Mit dieser Einstellung auf HoloLens 2 können Sie hologrammausrichtung in Ihren Mixed Reality-Erfassungen aktivieren. Wenn diese Option aktiviert ist, stellt die Plattform der App eine zusätzliche HolographicCamera zur Verfügung, wenn ein Mixed Reality-Aufnahmefoto oder -video aufgenommen wird. Diese HolographicCamera bietet Ansichtsmatrizen, die der Position der Foto-/Videokamera entspricht, und stellt Projektionsmatrizen mithilfe des Sichtfelds der Foto-/Videokamera zur Anwendung. Dadurch wird sichergestellt, dass Hologramme, z. B. Handgitter, in der Videoausgabe sichtbar ausgerichtet bleiben.

### <a name="hololens-2-reprojection-method"></a>HoloLens 2-Methode für die Neuprojektion

Legt die anfängliche Methode für die HoloLens 2 fest. Die Standardempfehlung ist die Verwendung einer Tiefenumprojektion, da alle Teile der Szene unabhängig voneinander basierend auf ihrer Entfernung vom Benutzer stabilisiert werden. Wenn Hologramme weiterhin instabil erscheinen, stellen Sie sicher, dass alle Objekte ihre Tiefe ordnungsgemäß an den Tiefenpuffer übermittelt haben. Dies ist manchmal eine Shadereinstellung. Wenn die Tiefe ordnungsgemäß übermittelt zu werden scheint und die Instabilität weiterhin vorhanden ist, versuchen Sie die automatische planare Stabilität, die den Tiefenpuffer verwendet, um eine Stabilitätsebene zu berechnen. Wenn eine App nicht genügend Tiefendaten übermitteln kann, damit eine dieser Optionen verwendet werden kann, wird eine planare Neuprojektion als Fallback bereitgestellt. Diese Methode basiert auf den von einer App bereitgestellten Fokuspunktdaten über [SetFocusPointForFrame.](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.SetFocusPointForFrame.html)

Um die Neuprojektionsmethode zur Laufzeit zu aktualisieren, greifen Sie wie `WindowsMixedRealityReprojectionUpdater` hier beschrieben auf zu:

```c#
var reprojectionUpdater = CameraCache.Main.EnsureComponent<WindowsMixedRealityReprojectionUpdater>();
reprojectionUpdater.ReprojectionMethod = HolographicDepthReprojectionMethod.AutoPlanar;
```

Dies muss nur einmal aktualisiert werden, und der Wert wird für alle nachfolgenden Frames wiederverwendet. Wenn die Methode häufig aktualisiert wird, empfiehlt es sich, das Ergebnis zwischenspeichern anstatt `EnsureComponent` es häufig auf aufruft.

## <a name="see-also"></a>Weitere Informationen

- [Kamerasystemübersicht](camera-system-overview.md)
- [Erstellen eines Kameraeinstellungsanbieters](create-settings-provider.md)
- [Rendern Mixed Reality-Aufnahme von der PV-Kamera](/windows/mixed-reality/mixed-reality-capture-for-developers#render-from-the-pv-camera-opt-in)
- [Holografische Neuprojektion](/windows/mixed-reality/hologram-stability#reprojection)