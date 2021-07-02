---
title: Anvisieren
description: Docummentation on types of Gaze in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, Mixed Reality, Development, MRTK, Gaze,
ms.openlocfilehash: 95dad85ca8154d35f73906b53019d3a52ced546f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176913"
---
# <a name="gaze"></a><span data-ttu-id="3944a-104">Anvisieren</span><span class="sxs-lookup"><span data-stu-id="3944a-104">Gaze</span></span>

<span data-ttu-id="3944a-105">[Anving](/windows/mixed-reality/gaze) ist eine Form der Eingabe, die mit der Welt interagiert, je nach Dem, wo der Benutzer sucht.</span><span class="sxs-lookup"><span data-stu-id="3944a-105">[Gaze](/windows/mixed-reality/gaze) is a form of input that interacts with the world based on where the user is looking.</span></span> <span data-ttu-id="3944a-106">Anvisierte Anvisierte sind in zwei verschiedenen Varianten vorhanden.</span><span class="sxs-lookup"><span data-stu-id="3944a-106">Gaze exists in two different flavors</span></span>

## <a name="head-gaze"></a><span data-ttu-id="3944a-107">Anvisieren mit dem Kopf</span><span class="sxs-lookup"><span data-stu-id="3944a-107">Head gaze</span></span>

<span data-ttu-id="3944a-108">Diese Art des Anvings basiert auf der Richtung, die der Kopf/die Kamera anviert.</span><span class="sxs-lookup"><span data-stu-id="3944a-108">This type of gaze is based on the direction that the head/camera is looking at.</span></span> <span data-ttu-id="3944a-109">Das Anvieren mit dem Kopf ist auf Systemen aktiv, die das Anvieren mit [](eye-tracking/eye-tracking-basic-setup.md#eye-tracking-requirements-checklist) den Augen nicht unterstützen, oder in Fällen, in denen die Hardware das Anvieren mit den Augen unterstützen kann, aber der richtige Berechtigungssatz und die richtige Einrichtung nicht durchgeführt wurden.</span><span class="sxs-lookup"><span data-stu-id="3944a-109">Head gaze is active on systems that don't support eye gaze, or in cases where the hardware may support eye gaze, but the right set of [permissions and setup](eye-tracking/eye-tracking-basic-setup.md#eye-tracking-requirements-checklist) has not been performed.</span></span>

<span data-ttu-id="3944a-110">Das Anvieren mit dem Kopf ist HoloLens 1-Stilinteraktionen zugeordnet, bei denen das Objekt durch Platzieren in der Mitte des holografischen Rahmens und anschließendes Ausführen der Tippbewegung in die Luft betrachtet wird.</span><span class="sxs-lookup"><span data-stu-id="3944a-110">Head gaze is usually associated with HoloLens 1 style interactions involving looking at object by placing it in the center of the Holographic Frame and then performing the air tap gesture.</span></span>

## <a name="eye-gaze"></a><span data-ttu-id="3944a-111">Anvisieren mit den Augen</span><span class="sxs-lookup"><span data-stu-id="3944a-111">Eye gaze</span></span>

<span data-ttu-id="3944a-112">Diese Art des Anvings basiert darauf, wo die Augen des Benutzers aussehen.</span><span class="sxs-lookup"><span data-stu-id="3944a-112">This type of gaze is based on where the user's eyes are looking.</span></span> <span data-ttu-id="3944a-113">Das Anvieren mit den Augen ist nur auf Systemen vorhanden, die Eyetracking unterstützen.</span><span class="sxs-lookup"><span data-stu-id="3944a-113">Eye gaze is only present on systems that support eye tracking.</span></span> <span data-ttu-id="3944a-114">Weitere Informationen [zur Verwendung des](eye-tracking/eye-tracking-main.md) Anvings mit den Augen finden Sie in der Eyetrackingdokumentation.</span><span class="sxs-lookup"><span data-stu-id="3944a-114">See the [eye tracking documentation](eye-tracking/eye-tracking-main.md) for more details on how to use eye gaze.</span></span>

## <a name="gazeprovider"></a><span data-ttu-id="3944a-115">GazeProvider</span><span class="sxs-lookup"><span data-stu-id="3944a-115">GazeProvider</span></span>

<span data-ttu-id="3944a-116">Die Anvitätsfunktion (sowohl mit dem Kopf als auch mit dem Auge) wird vom [GazeProvider bereitgestellt.](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider)</span><span class="sxs-lookup"><span data-stu-id="3944a-116">Gaze functionality (both head and eye) is provided by the [GazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider).</span></span> <span data-ttu-id="3944a-117">Dieser Anbieter kann im  Abschnitt Zeiger des Eingabesystemprofils konfiguriert werden:</span><span class="sxs-lookup"><span data-stu-id="3944a-117">This provider can be configured in the *Pointer* section of the input system profile:</span></span>

![Einstiegspunkt für die Konfiguration des Anvings](../images/input/GazeConfigurationEntrypoint.png)

<span data-ttu-id="3944a-119">Wie andere Eingabequellen interagiert der Anvinganbieter mit Objekten in der Szene mithilfe eines Zeigers (Informationen zu Zeigern finden Sie [in diesem Dokument).](../../architecture/controllers-pointers-and-focus.md)</span><span class="sxs-lookup"><span data-stu-id="3944a-119">Like other sources of input, the gaze provider interacts with objects in the scene through use of a pointer [(see this document for information on pointers)](../../architecture/controllers-pointers-and-focus.md).</span></span>
<span data-ttu-id="3944a-120">Im Fall des Anvitator wird sein Zeiger über implementiert und nicht `InternalGazePointer` über ein Profil konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="3944a-120">In the case of the gaze provider, its pointer is implemented via `InternalGazePointer` and is not configured through a profile.</span></span>

<span data-ttu-id="3944a-121">Es ist möglich, den anvisierten GazeProvider  durch eine alternative Implementierung zu ersetzen, indem Sie den Typ des Anvisierten Anbieters ändern, um auf eine andere Klasse zu verweisen, die [IMixedRealityProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider) und [IMixedRealityEyeProvider implementiert.](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider)</span><span class="sxs-lookup"><span data-stu-id="3944a-121">It is possible to replace the stock GazeProvider with an alternate implementation by changing *Gaze Provider Type* to reference a different class that implements [IMixedRealityGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider) and [IMixedRealityEyeGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider).</span></span>
<span data-ttu-id="3944a-122">Es wird im Allgemeinen empfohlen, den Anvisierungsanbieter (und das Melden von Problemen beim Auffinden von Fehlern) zu verwenden, da die erneute Implementierung von GazeProvider nicht trivial ist.</span><span class="sxs-lookup"><span data-stu-id="3944a-122">It's generally recommended to use the stock GazeProvider (and filing issues in when finding bugs) as re-implementing the GazeProvider is non-trivial.</span></span>

### <a name="alternative-platform-provided-gaze-poses"></a><span data-ttu-id="3944a-123">Alternative von der Plattform bereitgestellte Anv gaze-Posen</span><span class="sxs-lookup"><span data-stu-id="3944a-123">Alternative platform-provided gaze poses</span></span>

<span data-ttu-id="3944a-124">Standardmäßig verwendet der MRTK GazeProvider die Mitte des Kamerarahmens als Anving-Ursprung.</span><span class="sxs-lookup"><span data-stu-id="3944a-124">By default, the MRTK GazeProvider uses the center of the camera's frame as the gaze origin.</span></span> <span data-ttu-id="3944a-125">Einige Plattformen, z. B. Windows Mixed Reality auf HoloLens 2, bieten eine alternativ definierte Anvingpose.</span><span class="sxs-lookup"><span data-stu-id="3944a-125">Some platforms, like Windows Mixed Reality on HoloLens 2, provide an alternatively defined gaze pose.</span></span> <span data-ttu-id="3944a-126">Dies wird über die `Use Head Gaze Override` Einstellung in den Einstellungen für das Anvingen verwaltet.</span><span class="sxs-lookup"><span data-stu-id="3944a-126">This is managed via the `Use Head Gaze Override` setting in the gaze settings.</span></span> <span data-ttu-id="3944a-127">Wenn diese Option aktiviert ist, wird die Außerkraftsetzung des alternativen Anvings verwendet.</span><span class="sxs-lookup"><span data-stu-id="3944a-127">When enabled, the alternative gaze override will be used.</span></span> <span data-ttu-id="3944a-128">Wenn diese Deaktiviert ist, wird der Standard-Frame center-Ursprung verwendet.</span><span class="sxs-lookup"><span data-stu-id="3944a-128">When disabled, the default frame center origin will be used.</span></span> <span data-ttu-id="3944a-129">Insbesondere für HoloLens 2 wird der Anvierungswinkel um mehrere Grad erhöht, um den Komfort des Benutzers bei der Verwendung des Kopfs für die Zieladressierung zu berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="3944a-129">Specifically, for HoloLens 2, the gaze angle will be raised several degrees to account for user comfort in using their head for targeting.</span></span>

## <a name="usage"></a><span data-ttu-id="3944a-130">Verwendung</span><span class="sxs-lookup"><span data-stu-id="3944a-130">Usage</span></span>

### <a name="how-get-the-current-gaze-target"></a><span data-ttu-id="3944a-131">So erhalten Sie das aktuelle Anvingziel</span><span class="sxs-lookup"><span data-stu-id="3944a-131">How get the current gaze target</span></span>

<span data-ttu-id="3944a-132">In diesem Beispiel wird gezeigt, wie Sie das aktuelle Spielobjekt erhalten, das vom Anvitäts-Ziel des Benutzers verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="3944a-132">This sample shows how to get the current game object that is targeted by the user gaze.</span></span>

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

### <a name="how-to-get-the-current-gaze-direction-and-origin"></a><span data-ttu-id="3944a-133">How to get the current gaze direction and origin (So erhalten Sie die aktuelle Anvingrichtung und den Ursprung)</span><span class="sxs-lookup"><span data-stu-id="3944a-133">How to get the current gaze direction and origin</span></span>

<span data-ttu-id="3944a-134">In diesem Beispiel wird gezeigt, wie Sie den Vector3 erhalten, der die Richtung des Anvisierungs-Ziels des Benutzers und den Ursprung (den Punkt, von dem die Richtung aus geht) darstellt.</span><span class="sxs-lookup"><span data-stu-id="3944a-134">This sample shows how to get the Vector3 representing the direction of the user gaze and the origin (the point from which the direction is going).</span></span>

```c#
void LogGazeDirectionOrigin()
{
    Debug.Log("Gaze is looking in direction: "
        + CoreServices.InputSystem.GazeProvider.GazeDirection);

    Debug.Log("Gaze origin is: "
        + CoreServices.InputSystem.GazeProvider.GazeOrigin);
}
```
