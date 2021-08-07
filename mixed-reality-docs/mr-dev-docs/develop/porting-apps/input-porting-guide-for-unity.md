---
title: Leitfaden für Eingabeportierung für Unity
description: Erfahren Sie, wie Sie Eingaben für Windows Mixed Reality in Unity behandeln.
author: thetuvix
ms.author: alexturn
ms.date: 12/9/2020
ms.topic: article
keywords: input, unity, porting
ms.openlocfilehash: b2c328152d681a4c8753e29babf0f3ece6bdc0d3f21f9df6dd8de150c3fb47f0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212078"
---
# <a name="input-porting-guide-for-unity"></a>Leitfaden für Eingabeportierung für Unity

Sie können Ihre Eingabelogik portieren, um Windows Mixed Reality einem von zwei Ansätzen zu verwenden. Die erste besteht in der Verwendung der allgemeinen Input.GetButton/GetAxis-APIs von Unity, die sich über mehrere Plattformen erstrecken. Die zweite ist Windows XR-spezifische XR. WSA. Eingabe-APIs, die umfangreiche Daten speziell für Motion Controller und HoloLens bieten.

## <a name="general-inputgetbuttongetaxis-apis"></a>Allgemeine Input.GetButton/GetAxis-APIs

Unity verwendet derzeit seine allgemeinen Input.GetButton/Input.GetAxis-APIs, um Eingaben für das [Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html) und das [OpenVR SDK verfügbar zu machen.](https://docs.unity3d.com/Manual/OpenVRControllers.html) Wenn Ihre Apps diese APIs bereits für die Eingabe verwenden, sind die Input.GetButton/Input.GetAxis-APIs die einfachsten Pfade zur Unterstützung von Bewegungscontrollern in Windows Mixed Reality. Sie müssen nur Schaltflächen und Achsen im Eingabe-Manager neu zuzuordnungen.

Weitere Informationen finden Sie in der [Unity-Schaltflächen-/Achsenzuordnungstabelle](../unity/motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) und in der Übersicht [über die allgemeinen Unity-APIs.](../unity/motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis)

## <a name="windows-specific-xrwsainput-apis"></a>Windows XR-spezifische xr. WSA. Eingabe-APIs

Wenn Ihre App bereits benutzerdefinierte Eingabelogik für jede Plattform erstellt, können Sie die Windows-spezifischen APIs für räumliche Eingaben im **UnityEngine.XR.WSA.Input-Namespace** verwenden. Von dort aus greifen Sie auf zusätzliche Informationen zu, z. B. die Positionsgenauigkeit oder die Quellart, damit Sie Hände und Controller bei der HoloLens.

Weitere Informationen finden Sie in der [Übersicht über die UnityEngine.XR.WSA.Input-APIs.](../unity/motion-controllers-in-unity.md#windows-specific-apis-xrwsainput)

## <a name="grip-pose-vs-pointing-pose"></a>Greifpose im Vergleich zu zeigenden Posen

Windows Mixed Reality unterstützt Bewegungscontroller in verschiedenen Formfaktoren. Der Entwurf jedes Controllers unterscheidet sich in seiner Beziehung zwischen der Handposition des Benutzers und der natürlichen "Vorwärtsrichtung", die Apps verwenden sollten, um beim Rendern des Controllers zu zeigen.

Um diese Controller besser darstellen zu können, gibt es zwei Arten von Posen, die Sie für jede Interaktionsquelle untersuchen können:

* Die **Greifhaltung,** die entweder die Position der Handfläche darstellt, die von einem Zweig erkannt HoloLens oder der Handfläche, die einen Bewegungscontroller hält.
    * Bei immersiven Headsets wird diese  Pose am besten verwendet, um die Hand des Benutzers oder ein **Objekt in** der Hand des Benutzers zu rendern, z. B. eine Brille oder eine Brille.
    * Die **Greifposition:** Der Handflächenschwerpunkt, wenn der Controller natürlich hält, nach links oder rechts angepasst, um die Position innerhalb des Greifs zu zentriert.
    * Die **rechte** Achse der Greifausrichtung: Wenn Sie Ihre Hand vollständig öffnen, um eine flache 5-Finger-Pose zu bilden, den Strahl, der normal zu Ihrer Handfläche ist (vorwärts von der linken Handfläche, rückwärts von der rechten Handfläche).
    * Die **Vorwärtsachse** der Greifausrichtung: Wenn Sie die Hand teilweise schließen, als würde sie den Controller halten, wird der Strahl, der durch die von Denkfingern gebildete Achse "vorwärts" zeigt.
    * Die **Nach-oben-Achse** der Greifausrichtung: Die up-Achse, die durch die Definitionen "Right" und "Forward" impliziert wird.
    * Sie können über die anbieterübergreifende Eingabe-API **(XR) von Unity auf die Greifpose [zugreifen. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation**) oder über die Windows-spezifische API (**sourceState.sourcePose.TryGetPosition/Rotation**, anfordern der Greifposition).
* Der **Zeiger stellt die Spitze** des Controllers darstellt, der nach vorn zeigen soll.
    * Diese Darstellung wird am besten  für Raycast verwendet, wenn Sie auf die Benutzeroberfläche zeigen, wenn Sie das Controllermodell selbst rendern.
    * Derzeit ist die Zeigerposition nur über die Windows-spezifische API verfügbar (**sourceState.sourcePose.TryGetPosition/Rotation**, anfordern der Zeigerposition).

Diese Posenkoordinaten werden alle in Unity-Weltkoordinaten ausgedrückt.

## <a name="see-also"></a>Siehe auch
* [Motion controllers]().. /.. /design/motion-controllers.md)
* [Motion-Controller in Unity](../unity/motion-controllers-in-unity.md)
* [UnityEngine.XR.WSA.Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine.XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [Portierungsleitfäden](porting-guides.md)
