---
title: ProgressIndicator
description: Übersicht über den Statusindikator im MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 9170a376812901cb063038a5513d4fbf79ad0a28
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110121"
---
# <a name="progress-indicators"></a><span data-ttu-id="5b270-104">Statusindikatoren</span><span class="sxs-lookup"><span data-stu-id="5b270-104">Progress Indicators</span></span>

![Statusindikatoren](../images/progress-indicator/MRTK_ProgressIndicator_Main.png)

## <a name="example-scene"></a><span data-ttu-id="5b270-106">Beispielszene</span><span class="sxs-lookup"><span data-stu-id="5b270-106">Example scene</span></span>

<span data-ttu-id="5b270-107">Beispiele für die Verwendung von Fortschrittsindikatoren finden Sie in der `ProgressIndicatorExamples` Szene.</span><span class="sxs-lookup"><span data-stu-id="5b270-107">Examples of how to use progress indicators can be found in the `ProgressIndicatorExamples` scene.</span></span> <span data-ttu-id="5b270-108">In dieser Szene werden alle im SDK enthaltenen Statusindikator-Prefabs veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="5b270-108">This scene demonstrates each of the progress indicator prefabs included in the SDK.</span></span> <span data-ttu-id="5b270-109">Außerdem wird veranschaulicht, wie Fortschrittsindikatoren in Verbindung mit einigen gängigen asynchronen Aufgaben wie dem Laden von Szenen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="5b270-109">It also demonstrates how to use progress indicators in conjunction with some common asynchronous tasks like scene loading.</span></span>

<img src="../images/progress-indicator/MRTK_ProgressIndicator_Examples.png" alt="Progress Indicator Examples 1">

## <a name="example-open-update--close-a-progress-indicator"></a><span data-ttu-id="5b270-110">Beispiel: Öffnen, Aktualisieren & Schließen einer Statusanzeige</span><span class="sxs-lookup"><span data-stu-id="5b270-110">Example: Open, update & close a progress indicator</span></span>

<span data-ttu-id="5b270-111">Statusindikatoren implementieren die [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) -Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="5b270-111">Progress indicators implement the [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) interface.</span></span> <span data-ttu-id="5b270-112">Diese Schnittstelle kann mithilfe von aus einem GameObject abgerufen `GetComponent` werden.</span><span class="sxs-lookup"><span data-stu-id="5b270-112">This interface can be retrieved from a GameObject using `GetComponent`.</span></span>

```c#
[SerializedField]
private GameObject indicatorObject;
private IProgressIndicator indicator;

private void Start()
{
    indicator = indicatorObject.GetComponent<IProgressIndicator>();
}
```

<span data-ttu-id="5b270-113">Die `IProgressIndicator.OpenAsync()` Methoden und geben Tasks `IProgressIndicator.CloseAsync()` [zurück.](xref:System.Threading.Tasks.Task)</span><span class="sxs-lookup"><span data-stu-id="5b270-113">The `IProgressIndicator.OpenAsync()` and `IProgressIndicator.CloseAsync()` methods return [Tasks](xref:System.Threading.Tasks.Task).</span></span> <span data-ttu-id="5b270-114">Es wird empfohlen, auf diese Aufgaben in einer asynchronen Methode zu warten.</span><span class="sxs-lookup"><span data-stu-id="5b270-114">We recommend awaiting these Tasks in an async method.</span></span>

<span data-ttu-id="5b270-115">Die Standard-Statusanzeige-Prefabs des MRTK sollten inaktiv sein, wenn sie in einer Szene platziert werden.</span><span class="sxs-lookup"><span data-stu-id="5b270-115">The MRTK's default progress indicator prefabs should be inactive when placed in a scene.</span></span> <span data-ttu-id="5b270-116">Wenn ihre `IProgressIndicator.OpenAsync()` Methoden aufgerufen werden, aktivieren und deaktivieren die Statusindikatoren ihre Gameobjects automatisch.</span><span class="sxs-lookup"><span data-stu-id="5b270-116">When their `IProgressIndicator.OpenAsync()` methods are called the progress indicators will activate and deactivate their gameobjects automatically.</span></span> <span data-ttu-id="5b270-117">(Dieses Muster ist keine Anforderung der IProgressIndicator-Schnittstelle.)</span><span class="sxs-lookup"><span data-stu-id="5b270-117">(This pattern is not a requirement of the IProgressIndicator interface.)</span></span>

<span data-ttu-id="5b270-118">Legen Sie die -Eigenschaft `Progress` des Indikators auf einen Wert zwischen 0 und 1 fest, um den angezeigten Status zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="5b270-118">Set the indicator's `Progress` property to a value from 0-1 to update its displayed progress.</span></span> <span data-ttu-id="5b270-119">Legen Sie die `Message` -Eigenschaft fest, um die angezeigte Meldung zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="5b270-119">Set its `Message` property to update its displayed message.</span></span> <span data-ttu-id="5b270-120">Dieser Inhalt kann in verschiedenen Implementierungen auf unterschiedliche Weise angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="5b270-120">Different implementations may display this content in different ways.</span></span>

```c#
private async void OpenProgressIndicator()
{
    await indicator.OpenAsync();

    float progress = 0;
    while (progress < 1)
    {
        progress += Time.deltaTime;
        indicator.Message = "Loading...";
        indicator.Progress = progress;
        await Task.Yield();
    }

    await indicator.CloseAsync();
}
```

## <a name="indicator-states"></a><span data-ttu-id="5b270-121">Indikatorzustände</span><span class="sxs-lookup"><span data-stu-id="5b270-121">Indicator states</span></span>

<span data-ttu-id="5b270-122">Die -Eigenschaft eines `State` Indikators bestimmt, welche Vorgänge gültig sind.</span><span class="sxs-lookup"><span data-stu-id="5b270-122">An indicator's `State` property determines which operations are valid.</span></span> <span data-ttu-id="5b270-123">Wenn Sie eine ungültige Methode aufrufen, wird der Indikator in der Regel einen Fehler melden und keine Aktion ergreifen.</span><span class="sxs-lookup"><span data-stu-id="5b270-123">Calling an invalid method will typically cause the indicator to report an error and take no action.</span></span>

<span data-ttu-id="5b270-124">Zustand</span><span class="sxs-lookup"><span data-stu-id="5b270-124">State</span></span> | <span data-ttu-id="5b270-125">Gültige Vorgänge</span><span class="sxs-lookup"><span data-stu-id="5b270-125">Valid Operations</span></span>
--- | ---
`ProgressIndicatorState.Opening` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Open` | `CloseAsync()`
`ProgressIndicatorState.Closing` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Closed` | `OpenAsync()`

<span data-ttu-id="5b270-126">`AwaitTransitionAsync()` kann verwendet werden, um sicherzustellen, dass ein Indikator vollständig geöffnet oder geschlossen ist, bevor er verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="5b270-126">`AwaitTransitionAsync()` can be used to be sure an indicator is fully opened or closed before using it.</span></span>

```c#
private async void ToggleIndicator(IProgressIndicator indicator)
{
    await indicator.AwaitTransitionAsync();

    switch (indicator.State)
    {
        case ProgressIndicatorState.Closed:
            await indicator.OpenAsync();
            break;

        case ProgressIndicatorState.Open:
            await indicator.CloseAsync();
            break;
        }
    }
```
