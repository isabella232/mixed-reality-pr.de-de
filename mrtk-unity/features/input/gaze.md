---
title: Anvisieren
description: Docummentation on types of Gaze in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, Mixed Reality, Development, MRTK, Gaze,
ms.openlocfilehash: a9d97ef73a7014a46001cbd42281c5ab28f6cf425dfd7605ce5b3c8c7fc45198
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208432"
---
# <a name="gaze"></a>Anvisieren

[Anving](/windows/mixed-reality/gaze) ist eine Form der Eingabe, die mit der Welt interagiert, je nach Dem, wo der Benutzer sucht. Anvisiertes Anvisiertes gibt es in zwei verschiedenen Varianten.

## <a name="head-gaze"></a>Anvisieren mit dem Kopf

Diese Art des Anvings basiert auf der Richtung, die der Kopf/die Kamera anviert. Das Anvieren mit dem Kopf ist auf Systemen aktiv, die das Anvieren mit [](eye-tracking/eye-tracking-basic-setup.md#eye-tracking-requirements-checklist) den Augen nicht unterstützen, oder in Fällen, in denen die Hardware das Anvieren mit den Augen unterstützen kann, aber der richtige Berechtigungssatz und die richtige Einrichtung nicht durchgeführt wurden.

Das Anvieren mit dem Kopf ist HoloLens 1-Stilinteraktionen zugeordnet, bei denen das Objekt durch Platzieren in der Mitte des holografischen Rahmens und anschließendes Ausführen der Tippbewegung in die Luft betrachtet wird.

## <a name="eye-gaze"></a>Anvisieren mit den Augen

Diese Art des Anvings basiert darauf, wo die Augen des Benutzers aussehen. Das Anvieren mit den Augen ist nur auf Systemen vorhanden, die eye tracking unterstützen. Weitere Informationen [zur Verwendung des](eye-tracking/eye-tracking-main.md) Anvings mit den Augen finden Sie in der Eyetrackingdokumentation.

## <a name="gazeprovider"></a>GazeProvider

Die Anvitätsfunktion (sowohl mit dem Kopf als auch mit dem Auge) wird vom [GazeProvider bereitgestellt.](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider) Dieser Anbieter kann im  Abschnitt Zeiger des Eingabesystemprofils konfiguriert werden:

![Einstiegspunkt für die Konfiguration des Anvings](../images/input/GazeConfigurationEntrypoint.png)

Wie andere Eingabequellen interagiert der Anvinganbieter mit Objekten in der Szene mithilfe eines Zeigers (Informationen zu Zeigern finden Sie [in diesem Dokument).](../../architecture/controllers-pointers-and-focus.md)
Im Fall des Anvitator wird sein Zeiger über implementiert und nicht `InternalGazePointer` über ein Profil konfiguriert.

Es ist möglich, den anvisierten GazeProvider  durch eine alternative Implementierung zu ersetzen, indem Sie den Typ des Anvisierten Anbieters ändern, um auf eine andere Klasse zu verweisen, die [IMixedRealityProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider) und [IMixedRealityEyeProvider implementiert.](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider)
Im Allgemeinen wird empfohlen, den Anvisierungsanbieter (und das Melden von Problemen beim Auffinden von Fehlern) zu verwenden, da die erneute Implementierung von GazeProvider nicht trivial ist.

### <a name="alternative-platform-provided-gaze-poses"></a>Alternative von der Plattform bereitgestellte Anv gaze-Posen

Standardmäßig verwendet der MRTK GazeProvider die Mitte des Kamerarahmens als Anving-Ursprung. Einige Plattformen, z. B. Windows Mixed Reality auf HoloLens 2, bieten eine alternativ definierte Anvingpose. Dies wird über die `Use Head Gaze Override` Einstellung in den Einstellungen für das Anvingen verwaltet. Wenn diese Option aktiviert ist, wird die Außerkraftsetzung des alternativen Anvings verwendet. Wenn diese Deaktiviert ist, wird der Standard-Frame center-Ursprung verwendet. Insbesondere für HoloLens 2 wird der Anvierungswinkel um mehrere Grad erhöht, um den Komfort des Benutzers bei der Verwendung des Kopfs für die Zieladressierung zu berücksichtigen.

## <a name="usage"></a>Verbrauch

### <a name="how-get-the-current-gaze-target"></a>So erhalten Sie das aktuelle Anvingziel

In diesem Beispiel wird gezeigt, wie Sie das aktuelle Spielobjekt erhalten, das vom Anvitäts-Ziel des Benutzers verwendet wird.

```c#
void LogCurrentGazeTarget()
{
    if (CoreServices.InputSystem.GazeProvider.GazeTarget)
    {
        Debug.Log("User gaze is currently over game object: "
            + CoreServices.InputSystem.GazeProvider.GazeTarget)
    }
}
```

### <a name="how-to-get-the-current-gaze-direction-and-origin"></a>How to get the current gaze direction and origin (So erhalten Sie die aktuelle Anvingrichtung und den Ursprung)

In diesem Beispiel wird gezeigt, wie Sie den Vector3 erhalten, der die Richtung des Anvisierungs-Ziels des Benutzers und den Ursprung (den Punkt, von dem die Richtung aus geht) darstellt.

```c#
void LogGazeDirectionOrigin()
{
    Debug.Log("Gaze is looking in direction: "
        + CoreServices.InputSystem.GazeProvider.GazeDirection);

    Debug.Log("Gaze origin is: "
        + CoreServices.InputSystem.GazeProvider.GazeOrigin);
}
```
