---
title: Windows Mixed Reality-Kameraeinstellungen
description: Dokumentation zur Verwendung Windows Mixed Reality Kameraeinstellungen im MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Kamera,
ms.openlocfilehash: 6d0231c070cd001d7e01b4a82ab66c2a9c5c115240b03e28b7d49a14de1753f1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212690"
---
# <a name="windows-mixed-reality-camera-settings-provider"></a>Windows Mixed Reality Anbieter von Kameraeinstellungen

Der Windows Mixed Reality Anbieter von Kameraeinstellungen bestimmt den Gerätetyp, auf dem die Anwendung ausgeführt wird, und wendet die entsprechenden Konfigurationseinstellungen basierend auf der Anzeige (transparent oder nicht transparent) an.

## <a name="enabling-the-windows-mixed-reality-camera-settings-provider"></a>Aktivieren des anbieters Windows Mixed Reality Kameraeinstellungen

In den folgenden Schritten wird davon ausgegangen, dass das MixedRealityToolkit-Objekt verwendet wird. Die für andere Dienstregistrierungsstellen erforderlichen Schritte können unterschiedlich sein.

1. Wählen Sie das MixedRealityToolkit-Objekt in der Szenenhierarchie aus.

    ![KONFIGURIERTE MRTK-Szenenhierarchie](../images/MRTK_ConfiguredHierarchy.png)

2. Navigieren Sie im Bereich Inspector (Inspektor) zum Abschnitt Camera system (Kamerasystem), und erweitern Sie den Abschnitt **Camera Einstellungen Providers (Anbieter** für Kamera Einstellungen).

    ![Erweitern von Einstellungsanbietern](../images/camera-system/ExpandProviders.png)

3. Klicken Sie auf **Kamera hinzufügen Einstellungen Anbieter,** und erweitern Sie den neu hinzugefügten Eintrag **Neue Kameraeinstellungen.**

    ![Erweitern des neuen Einstellungsanbieters](../images/camera-system/ExpandNewProvider.png)

4. Wählen Sie den anbieter Windows Mixed Reality Camera Einstellungen aus.

    ![Auswählen Windows Mixed Reality Einstellungsanbieters](../images/camera-system/SelectWindowsMixedRealitySettings.png)

> [!NOTE]
> Wenn Sie die Standardprofile des Microsoft Mixed Reality Toolkits verwenden, ist der Anbieter Windows Mixed Reality Kameraeinstellungen bereits aktiviert und konfiguriert.

## <a name="configuring-the-windows-mixed-reality-camera-settings-provider"></a>Konfigurieren des Anbieters für Windows Mixed Reality Kameraeinstellungen

Die Windows Mixed Reality Camera Einstellungen unterstützt auch ein Profil. Dieses Profil bietet die folgenden Optionen:

![Konfiguration Windows Mixed Reality Kameraeinstellungen](../images/camera-system/WMRCameraSettingsProfile.png)

### <a name="render-mixed-reality-capture-from-the-photovideo-camera"></a>Rendern der Mixed Reality-Aufnahme von der Foto-/Videokamera

Mit dieser Einstellung für HoloLens 2 können Sie die Hologrammausrichtung in Ihren Mixed Reality-Erfassungen aktivieren. Wenn diese Option aktiviert ist, stellt die Plattform eine zusätzliche HolographicCamera für die App bereit, wenn ein Mixed Reality-Aufnahmefoto oder -video aufgenommen wird. Diese HolographicCamera stellt Ansichtsmatrizen bereit, die der Position der Foto-/Videokamera entsprechen, und stellt Projektionsmatrizen mithilfe des Bild-/Videokamerafelds bereit. Dadurch wird sichergestellt, dass Hologramme wie Handgitternetze in der Videoausgabe sichtbar ausgerichtet bleiben.

### <a name="hololens-2-reprojection-method"></a>HoloLens 2 Reprojection-Methode

Legt die anfängliche Methode für HoloLens 2 Neuprojektion fest. Die Standardempfehlung ist die Verwendung der Tiefenreprojektion, da alle Teile der Szene unabhängig von ihrer Entfernung zum Benutzer stabil sind. Wenn Hologramme weiterhin instabil erscheinen, stellen Sie sicher, dass alle Objekte ihre Tiefe ordnungsgemäß an den Tiefenpuffer übermittelt haben. Dies ist manchmal eine Shadereinstellung. Wenn die Tiefe ordnungsgemäß übermittelt zu sein scheint und die Instabilität weiterhin vorhanden ist, versuchen Sie die automatische Stabilisierung, die den Tiefenpuffer verwendet, um eine Stabilisierungsebene zu berechnen. Wenn eine App nicht genügend Tiefendaten übermitteln kann, damit eine dieser Optionen verwendet werden kann, wird eine planare Neuprojektion als Fallback bereitgestellt. Diese Methode basiert auf den von einer App bereitgestellten Fokuspunktdaten über [SetFocusPointForFrame.](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.SetFocusPointForFrame.html)

Um die Reprojection-Methode zur Laufzeit zu aktualisieren, greifen Sie wie folgt auf `WindowsMixedRealityReprojectionUpdater` zu:

```c#
var reprojectionUpdater = CameraCache.Main.EnsureComponent<WindowsMixedRealityReprojectionUpdater>();
reprojectionUpdater.ReprojectionMethod = HolographicDepthReprojectionMethod.AutoPlanar;
```

Dies muss nur einmal aktualisiert werden, und der Wert wird für alle nachfolgenden Frames wiederverwendet. Wenn die Methode häufig aktualisiert wird, wird empfohlen, das Ergebnis zwischenzuspeichern, `EnsureComponent` anstatt sie häufig aufzurufen.

## <a name="see-also"></a>Siehe auch

- [Übersicht über das Kamerasystem](camera-system-overview.md)
- [Erstellen eines Kamera-Einstellungen-Anbieters](create-settings-provider.md)
- [Rendern Mixed Reality-Aufnahme von der PV-Kamera](/windows/mixed-reality/mixed-reality-capture-for-developers#render-from-the-pv-camera-opt-in)
- [Holografische Neuprojektion](/windows/mixed-reality/hologram-stability#reprojection)