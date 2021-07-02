---
title: MRTK und verwaltetes Codestriping
description: Codestriping in MRTK und Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 8b8e0f4488a6e955e599084c0b59d8c80f553a78
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176295"
---
# <a name="mrtk-and-managed-code-stripping"></a>MRTK und verwaltetes Codestriping

Wenn Sie das IL2CPP-Skript-Back-End von Unity verwenden (optional in Unity 2018.4, erforderlich in 2019 und [neuer),](https://docs.unity3d.com/Manual/ManagedCodeStripping.html) wird verwalteter Code entfernt.
Der Unity-Linker führt diesen Prozess aus, um die Binärgröße zu reduzieren und die Buildzeiten zu verringern.

Das Mixed Reality Toolkit verwendet die Datei , um zu beeinflussen, wie der `link.xml` Unity-Linker MRTK-Assemblys verarbeitet. Diese Datei, die vollständig in der [Unity-Dokumentation](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML)beschrieben wird, bietet dem Linker Anweisungen zum Beibehalten von Code, wenn seine Verwendung nicht abgeleitet werden kann (z. B. über Reflektion).

Als flexible und anpassbare Plattform erstellt MRTK die Datei beim Import in , wenn sie nicht `link.xml` `Assets/MixedRealityToolkit.Generated` vorhanden ist. Bereits vorhandene link.xml werden nicht überschrieben. Es wird empfohlen, `link.xml` und `link.xml.meta` der Versionskontrolle hinzugefügt zu werden. Entwickler können die Anpassungen an `Assets/MixedRealityToolkit.Generated/link.xml` die Anforderungen des Projekts anpassen.

Standardmäßig behält die link.xml MRTK erstellte Datei die gesamte Assembly bei, die in den folgenden Daten gezeigt wird.

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

Weitere Informationen zum formatierten link.xml finden Sie in der Unity-Dokumentation.

## <a name="see-also"></a>Siehe auch

- [Unity: Beschriftung von verwaltetem Code](https://docs.unity3d.com/Manual/ManagedCodeStripping.html)
- [Unity: Verknüpfen der XML-Datei](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML)
