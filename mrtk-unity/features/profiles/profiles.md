---
title: Profiles
description: Dokumentationsprofile in MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Profile,
ms.openlocfilehash: 785d402e924a534627dfd1d742d2019d9ce9dd5a
ms.sourcegitcommit: 2f69fb62eb81f91e655d7b55306b0550a1162496
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/10/2021
ms.locfileid: "111908239"
---
# <a name="profiles"></a>Profiles

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Introduction-to-MRTK-Profiles/player]

Eins der wichtigsten Verfahren, mit denen das MRTK konfiguriert wird, findet sich in Form der Profile, die im Foundation-Paket zur Verfügung stehen. Das [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit)-Hauptobjekt in einer Szene verfügt über das aktive Profil, bei dem es sich um ein ScriptableObject handelt. Das MRTK-Konfigurationsprofil auf oberster Ebene enthält Unterprofildaten für jeden Kern der primären Kernsysteme, die jeweils so konzipiert sind, dass sie das Verhalten der entsprechenden Teilsysteme konfigurieren. Darüber hinaus stellen diese Unterprofile ihrerseits ScriptableObjects dar und können daher Verweise auf andere Profilobjekte enthalten, die sich eine Ebene unterhalb befinden. Im Wesentlichen steht eine ganze Baumstruktur miteinander verbundener Profile zur Verfügung, aus denen sich die Konfigurationsinformationen zum Initialisieren der MRTK-Teilsysteme und -Funktionen zusammensetzen.

Beispielsweise wird das Verhalten des Eingabesystems durch ein Eingabesystemprofil gesteuert, wie etwa dem `DefaultMixedRealityInputSystemProfile` (Assets/MRTK/SDK/Profiles).

<img src="../images/profiles/input_profile.png" width="650px" alt="Input profile" style="display:block;">
<sup>Profil-Inspektor</sup>

## <a name="background"></a>Hintergrund

Profile dienen hauptsächlich dazu, bestimmte Szenarien übergreifend auf mehreren Geräten zu unterstützen, und ihre Verwaltung liegt bei den Datenanbietern. Auf diese Weise kann eine App möglichst geräteunabhängig entworfen werden, und dem MRTK und den Datenanbietern des Profils wird die plattformübergreifende Unterstützung überlassen.

Es gibt auch Profile, die für die Eingabefeatures bestimmter Geräte erstellt werden, z. B. das Profil HoloLens 1, bei dem standardmäßig GGV-artige Interaktionen verwendet werden.

## <a name="xr-sdk"></a>XR SDK

::: moniker range=">= mrtkunity-2021-05"
Verwenden Sie eines der MRTK-Standardprofile, die alle über die XR-Pipelines von Unity konfiguriert sind. Die vorherigen "DefaultOpenXRConfigurationProfile" und "DefaultXRSDKConfigurationProfile" sind jetzt veraltet.
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
Zurzeit werden zwei Profile für das XR SDK bereitgestellt, `DefaultXRSDKConfigurationProfile` und `DefaultHoloLens2XRSDKConfigurationProfile`. Das hat zur Folge, dass aufgrund von szenen- und szenariospezifischen Konfigurationen nicht alle Beispielszenen in vollem Umfang unterstützt werden. Alle Beispiele, die `DefaultMixedRealityToolkitConfigurationProfile` und `DefaultHoloLens2ConfigurationProfile` verwenden, _können_ auf ihre entsprechenden XR SDK-Profile umgestellt werden. Wenn Sie OpenXR mit XR SDK verwenden, nutzen Sie stattdessen das `DefaultOpenXRConfigurationProfile`.

Zusätzliche Arbeiten werden durchgeführt, um die Konfiguration zu vereinfachen und alle Beispielszenen zu unterstützen, sodass sowohl das Legacy-XR als auch das XR SDK parallel konfiguriert werden können. Sie können dies unter Problem [#9419](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9419) nachverfolgen.
::: moniker-end

Weitere Informationen zur Konvertierung von Profilen zwischen dem Legacy-XR und dem XR SDK finden Sie unter [Konfigurieren von MRTK für die XR-SDK-Pipeline](../../configuration/getting-started-with-mrtk-and-xrsdk.md#configuring-mrtk-for-the-xr-sdk-pipeline).

## <a name="default-profile"></a>Standardprofil

Das MRTK bietet eine Reihe von Standardprofilen, mit denen die meisten vom MRTK unterstützten Plattformen und Szenarien abgedeckt werden. Wenn Sie z. B. das `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles) auswählen, können Sie Szenarien auf VR (OpenVR, WMR) und HoloLens (1 und 2) ausprobieren.

Beachten Sie, dass es sich hierbei um ein Profil für die allgemeine Nutzung handelt, das daher nicht für einen bestimmten Anwendungsfall optimiert ist. Wenn Sie über leistungsfähigere/spezifischere Einstellungen verfügen möchten, die auf anderen Plattformen besser geeignet sind, sehen Sie sich die anderen unten aufgeführten Profile an, die leicht optimiert wurden, um auf ihren jeweiligen Plattformen eine bessere Leistung zu erzielen.

## <a name="hololens-2-profile"></a>HoloLens 2-Profil

Das MRTK bietet außerdem ein Standardprofil, das für Bereitstellungen und Tests auf der HoloLens 2 optimiert ist: `DefaultHoloLens2ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens2).

Wenn Sie aufgefordert werden, ein Profil für das MixedRealityToolkit-Objekt auszuwählen, verwenden Sie dieses Profil anstelle des ausgewählten Standardprofils.

Dies sind die wichtigsten Unterschiede zwischen dem HoloLens 2-Profil und dem Standardprofil:

**Deaktivierte** Features:

- [Begrenzungssystem](../boundary/boundary-system-getting-started.md)
- [Teleportiersystem](../teleport-system/teleport-system.md)
- [System für die räumliche Wahrnehmung](../spatial-awareness/spatial-awareness-getting-started.md)
- [Hand Mesh-Visualisierung](../input/hand-tracking.md) (aufgrund des Leistungsmehrbedarfs)

**Aktivierte** Systeme:

- Der [Eyetracking-Anbieter](../input/eye-tracking/eye-tracking-main.md)
- Augeneingabesimulation

Die Einstellungen des Kameraprofils werden übereinstimmend festgelegt, sodass die Qualität im Editor und im Player gleich ist. Dies unterscheidet sich vom Standardkameraprofil, bei dem für nicht transparente Anzeigen eine höhere Qualität festgelegt ist. Diese Einstellung bedeutet, dass die Qualität im Editor geringer ist, was näher an der Darstellung liegt, die auf dem Gerät ausgegeben wird.

> [!NOTE]
> Das System für die räumliche Wahrnehmung ist aufgrund von Kundenfeedback standardmäßig deaktiviert – es stellt zunächst eine interessante Visualisierung dar, wird aber normalerweise deaktiviert, um die visuelle Ablenkung und den zusätzlichen Leistungsbedarf bei seiner Ausführung zu vermeiden. Das System kann anhand [dieser Anweisungen](../spatial-awareness/spatial-awareness-getting-started.md) wieder aktiviert werden.
