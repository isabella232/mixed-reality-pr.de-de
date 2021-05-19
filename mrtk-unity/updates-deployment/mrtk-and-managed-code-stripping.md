---
title: MRTK und Entfernen von verwaltetem Code
description: Code stripping in MRTK und Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 09e5140fd9585c19eacac5ba937eaf4ea8f2a8ea
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143737"
---
# <a name="mrtk-and-unity-managed-code-stripping"></a>MRTK- und Unity-Stripping für verwalteten Code

Bei Verwendung des IL2CPP-Skript-Back-Ends von Unity (optional in Unity 2018.4, erforderlich ab 2019) erfolgt das Stripping von [verwaltetem Code.](https://docs.unity3d.com/Manual/ManagedCodeStripping.html)
Der Linker von Unity führt diesen Prozess aus, um die Binärgröße zu reduzieren und die Buildzeiten zu verkürzen.

Das Mixed Reality Toolkit verwendet eine Datei, `link.xml` , um zu beeinflussen, wie der Linker von Unity MRTK-Assemblys verarbeitet. Diese Datei, die vollständig in der [Unity-Dokumentation](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML)beschrieben ist, stellt dem Linker Anweisungen zum Beibehalten von Code bereit, wenn seine Verwendung nicht abgeleitet werden kann (z. B. über Reflektion verwendet).

Als flexible und anpassbare Plattform erstellt MRTK die `link.xml` Datei beim Import in , wenn sie nicht vorhanden `Assets/MixedRealityToolkit.Generated` ist. Bereits vorhandene link.xml Dateien werden nicht überschrieben. Es wird empfohlen, `link.xml` und `link.xml.meta` der Versionskontrolle hinzuzufügen. Entwickler sollten sich gerne an die Anforderungen des Projekts anpassen `Assets/MixedRealityToolkit.Generated/link.xml` lassen.

Standardmäßig behält die von MRTK erstellte link.xml-Datei die gesamten Assemblys bei, die in den folgenden Daten angezeigt werden.

``` xml
<linker> 
  <!-- 
    This link.xml file is provided to prevent MRTK code from being optimized away 
    during IL2CPP builds.More details on when this is needed and why this is needed 
    can be found here: https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5273 
    If your application doesn't use some specific services (for example, if teleportation system is 
    disabled in the profile), it is possible to remove their corresponding lines down 
    below(in the previous example, we would remove the TeleportSystem below). 
    It's recommended to start with this list and narrow down if you want to ensure 
    specific bits of code get optimized away. 
  --> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.SDK" preserve="all"/> 
  <!-- Core systems --> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.BoundarySystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.CameraSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.DiagnosticsSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.InputSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.SceneSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.SpatialAwarenessSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.TeleportSystem" preserve="all"/> 
  <!-- Data providers --> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.LeapMotion" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenVR" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.UnityAR" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.WindowsMixedReality.Shared" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.WindowsMixedReality" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.XRSDK.WindowsMixedReality" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.WindowsVoiceInput" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.XRSDK" preserve="all"/> 
  <!-- Extension services --> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Extensions.HandPhysics" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Extensions.Tracking" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Extensions.SceneTransitionService" preserve="all"/> 
</linker>
```

Weitere Informationen zum link.xml-Dateiformat finden Sie in der Unity-Dokumentation.

## <a name="see-also"></a>Weitere Informationen

- [Unity: Stripping von verwaltetem Code](https://docs.unity3d.com/Manual/ManagedCodeStripping.html)
- [Unity: LINK-XML-Datei](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML)
