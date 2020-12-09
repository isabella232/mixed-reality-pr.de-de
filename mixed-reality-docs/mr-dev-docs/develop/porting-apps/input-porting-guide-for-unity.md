---
title: Leitfaden für Eingabeportierung für Unity
description: Erfahren Sie, wie Sie Eingaben für Windows Mixed Reality in Unity verarbeiten.
author: thetuvix
ms.author: alexturn
ms.date: 12/9/2020
ms.topic: article
keywords: Eingabe, Unity, portieren
ms.openlocfilehash: 053918ec62f83c74655b0d4bb09a2b45b62bfc53
ms.sourcegitcommit: f2782d0925b2075fdaa0a4ecdef3dd4f0b4e1e99
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96925873"
---
# <a name="input-porting-guide-for-unity"></a>Leitfaden für Eingabeportierung für Unity

Sie können Ihre Eingabe Logik in Windows Mixed Reality portieren. verwenden Sie dazu einen von zwei Ansätzen: die allgemeinen Eingabe. getbutton/getaxis-APIs von Unity, die sich über mehrere Plattformen erstrecken, oder den Windows-spezifischen XR. WSA. Eingabe-APIs, die umfangreichere Daten speziell für Bewegungs Controller und hololens-Hände bieten.

## <a name="general-inputgetbuttongetaxis-apis"></a>Allgemeine Eingabe. getbutton/getaxis-APIs

Unity verwendet derzeit die allgemeinen Input. getbutton/Input. getaxis-APIs, um Eingaben für [das Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html) und [das openvr SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html)verfügbar zu machen. Wenn Ihre apps bereits diese APIs für die Eingabe verwenden, ist dies der einfachste Weg zur Unterstützung von Bewegungs Controllern in Windows Mixed Reality: Sie müssen nur Schaltflächen und Achsen im Eingabe-Manager neu zuordnen.

Weitere Informationen finden Sie in der [Unity-Schaltflächen-/Achsen-Mapping-Tabelle](../unity/gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) und [in der Übersicht über die gemeinsamen Unity-APIs](../unity/gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis).

## <a name="windows-specific-xrwsainput-apis"></a>Windows-spezifischer XR. WSA. Eingabe-APIs

Wenn Ihre APP bereits eine benutzerdefinierte Eingabe Logik für jede Plattform erstellt hat, können Sie die Windows-spezifischen räumlichen Eingabe-APIs im Namespace **unityengine. XR. WSA. Input** verwenden. Auf diese Weise können Sie auf zusätzliche Informationen zugreifen, wie z. b. Die Positionsgenauigkeit oder die quellart, sodass Sie die Hände und Controller auf hololens aufteilen können.

Weitere Informationen finden Sie in der [Übersicht über die unityengine. XR. WSA. Input-APIs](../unity/gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xrwsainput).

## <a name="grip-pose-vs-pointing-pose"></a>Ziehpunkt im Vergleich zu Zeige darstellen

Windows Mixed Reality unterstützt Bewegungs Controller in einer Vielzahl von Formfaktoren, wobei sich der Entwurf des Controllers in seiner Beziehung zwischen der Handposition des Benutzers und der natürlichen Vorwärtsrichtung unterscheidet, die von den apps beim Rendern des Controllers verwendet werden sollen.

Um diese Controller besser darstellen zu können, gibt es zwei Arten von Posen, die Sie für die einzelnen Interaktions Quellen untersuchen können:

* Die Zieh Punkt Darstellung, die den Speicherort der von einem hololens erkannten **Hand, oder** die Palme mit einem Bewegungs Controller darstellt.
    * Bei immersiven Headsets eignet sich diese Pose am besten zum Rendering **der Benutzer Hand** oder **eines Objekts, das in der Hand des Benutzers gehalten** wird, z. b. ein Schwert oder eine Waffe.
    * Die Zieh **Punktposition**: der Palmen Schwerpunkt bei der natürlichen Aufbewahrung des Controllers, nach links oder rechts, um die Position im Ziehpunkt zu zentrieren.
    * Die **Rechte Achse** der Ziehpunkt Ausrichtung: Wenn Sie Ihre Hand vollständig geöffnet haben, um eine flache 5-Finger-Darstellung zu bilden, ist das Strahl-Ray, das normal ist (vorwärts von links nach links, rückwärts von rechter Palme).
    * Die **Forward-Achse** der Ziehpunkt Ausrichtung: Wenn Sie die Hand teilweise schließen (wie beim Halten des Controllers), wird der Strahl, der durch das durch ihre nicht-Thumb-Finger formatierte Rohr auf "Vorwärts" zeigt.
    * Die **aufwärts Achse** der Ziehpunkt Ausrichtung: die aufwärts Achse, die durch die Rechte-und vorwärts Definitionen impliziert wird.
    * Sie können auf die Ziehpunkt-Pose über die Anbieter übergreifende Eingabe-API von Unity (XR) zugreifen **[. Inputtracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). Getlocalposition/Rotation**) oder über die Windows-spezifische API (**SourceState. sourcepose. trygetposition/Rotation**, Anfordern der Ziehpunkt-Pose).
* Die **Zeiger** Darstellung, die die Spitze des Controllers darstellt, der vorwärts zeigt.
    * Diese Pose eignet sich am besten für raycast, wenn Sie **auf die Benutzeroberfläche zeigen** , wenn Sie das Controller Modell selbst rendern.
    * Derzeit ist die Zeiger Pose nur über die Windows-spezifische API (**SourceState. sourcepose. trygetposition/Rotation**) verfügbar, die die Zeiger Pose anfordert.

Diese posikoordinaten werden alle in Unity-Weltkoordinaten ausgedrückt.

## <a name="see-also"></a>Weitere Informationen
* [Bewegungs Controller]().. /.. /design/motion-controllers.md)
* [Gesten und Motion-Controller in Unity](../unity/gestures-and-motion-controllers-in-unity.md)
* [Unityengine. XR. WSA. Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [Unityengine. XR. inputtracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [Portierungsleitfäden](porting-guides.md)
