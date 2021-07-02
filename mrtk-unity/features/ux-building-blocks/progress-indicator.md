---
title: Statusanzeige
description: Übersicht über den Fortschrittsindikator im MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 268d13d00bc0bcf1d522eaa6809dab9892624e11
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176575"
---
# <a name="progress-indicator"></a><span data-ttu-id="964d8-104">Statusanzeige</span><span class="sxs-lookup"><span data-stu-id="964d8-104">Progress indicator</span></span>

![Statusindikatoren](../images/progress-indicator/MRTK_ProgressIndicator_Main.png)

## <a name="example-scene"></a><span data-ttu-id="964d8-106">Beispielszene</span><span class="sxs-lookup"><span data-stu-id="964d8-106">Example scene</span></span>

<span data-ttu-id="964d8-107">Beispiele für die Verwendung von Statusindikatoren finden Sie in der `ProgressIndicatorExamples` Szene.</span><span class="sxs-lookup"><span data-stu-id="964d8-107">Examples of how to use progress indicators can be found in the `ProgressIndicatorExamples` scene.</span></span> <span data-ttu-id="964d8-108">Diese Szene veranschaulicht die einzelnen Prefabs der Statusanzeige, die im SDK enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="964d8-108">This scene demonstrates each of the progress indicator prefabs included in the SDK.</span></span> <span data-ttu-id="964d8-109">Außerdem wird veranschaulicht, wie Statusindikatoren in Verbindung mit einigen häufigen asynchronen Aufgaben wie dem Laden von Szenen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="964d8-109">It also demonstrates how to use progress indicators in conjunction with some common asynchronous tasks like scene loading.</span></span>

<img src="../images/progress-indicator/MRTK_ProgressIndicator_Examples.png" alt="Progress Indicator Examples 1">

## <a name="example-open-update--close-a-progress-indicator"></a><span data-ttu-id="964d8-110">Beispiel: Öffnen, Aktualisieren & Schließen einer Statusanzeige</span><span class="sxs-lookup"><span data-stu-id="964d8-110">Example: Open, update & close a progress indicator</span></span>

<span data-ttu-id="964d8-111">Statusindikatoren implementieren die [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) -Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="964d8-111">Progress indicators implement the [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) interface.</span></span> <span data-ttu-id="964d8-112">Diese Schnittstelle kann mithilfe von aus einem GameObject abgerufen `GetComponent` werden.</span><span class="sxs-lookup"><span data-stu-id="964d8-112">This interface can be retrieved from a GameObject using `GetComponent`.</span></span>

```c#
[SerializedField]
private GameObject indicatorObject;
private IProgressIndicator indicator;

private void Start()
{
    indicator = indicatorObject.GetComponent<IProgressIndicator>();
}
```

<span data-ttu-id="964d8-113">Die `IProgressIndicator.OpenAsync()` Methoden und geben `IProgressIndicator.CloseAsync()` [Tasks](xref:System.Threading.Tasks.Task)zurück.</span><span class="sxs-lookup"><span data-stu-id="964d8-113">The `IProgressIndicator.OpenAsync()` and `IProgressIndicator.CloseAsync()` methods return [Tasks](xref:System.Threading.Tasks.Task).</span></span> <span data-ttu-id="964d8-114">Es wird empfohlen, auf diese Aufgaben in einer asynchronen Methode zu warten.</span><span class="sxs-lookup"><span data-stu-id="964d8-114">We recommend awaiting these Tasks in an async method.</span></span>

<span data-ttu-id="964d8-115">Die Standardpräfabs der MRTK-Statusanzeige sollten inaktiv sein, wenn sie in einer Szene platziert werden.</span><span class="sxs-lookup"><span data-stu-id="964d8-115">The MRTK's default progress indicator prefabs should be inactive when placed in a scene.</span></span> <span data-ttu-id="964d8-116">Wenn ihre `IProgressIndicator.OpenAsync()` Methoden aufgerufen werden, werden die Statusindikatoren automatisch aktiviert und deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="964d8-116">When their `IProgressIndicator.OpenAsync()` methods are called the progress indicators will activate and deactivate their gameobjects automatically.</span></span> <span data-ttu-id="964d8-117">(Dieses Muster ist keine Anforderung der IProgressIndicator-Schnittstelle.)</span><span class="sxs-lookup"><span data-stu-id="964d8-117">(This pattern is not a requirement of the IProgressIndicator interface.)</span></span>

<span data-ttu-id="964d8-118">Legen Sie die -Eigenschaft des Indikators `Progress` auf einen Wert zwischen 0 und 1 fest, um den angezeigten Fortschritt zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="964d8-118">Set the indicator's `Progress` property to a value from 0-1 to update its displayed progress.</span></span> <span data-ttu-id="964d8-119">Legen Sie die `Message` -Eigenschaft fest, um die angezeigte Meldung zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="964d8-119">Set its `Message` property to update its displayed message.</span></span> <span data-ttu-id="964d8-120">Unterschiedliche Implementierungen können diesen Inhalt auf unterschiedliche Weise anzeigen.</span><span class="sxs-lookup"><span data-stu-id="964d8-120">Different implementations may display this content in different ways.</span></span>

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

## <a name="indicator-states"></a><span data-ttu-id="964d8-121">Indikatorzustände</span><span class="sxs-lookup"><span data-stu-id="964d8-121">Indicator states</span></span>

<span data-ttu-id="964d8-122">Die -Eigenschaft eines `State` Indikators bestimmt, welche Vorgänge gültig sind.</span><span class="sxs-lookup"><span data-stu-id="964d8-122">An indicator's `State` property determines which operations are valid.</span></span> <span data-ttu-id="964d8-123">Das Aufrufen einer ungültigen Methode bewirkt in der Regel, dass der Indikator einen Fehler meldet und keine Aktion vornimmt.</span><span class="sxs-lookup"><span data-stu-id="964d8-123">Calling an invalid method will typically cause the indicator to report an error and take no action.</span></span>

<span data-ttu-id="964d8-124">State</span><span class="sxs-lookup"><span data-stu-id="964d8-124">State</span></span> | <span data-ttu-id="964d8-125">Gültige Vorgänge</span><span class="sxs-lookup"><span data-stu-id="964d8-125">Valid Operations</span></span>
--- | ---
`ProgressIndicatorState.Opening` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Open` | `CloseAsync()`
`ProgressIndicatorState.Closing` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Closed` | `OpenAsync()`

<span data-ttu-id="964d8-126">`AwaitTransitionAsync()` kann verwendet werden, um sicherzustellen, dass ein Indikator vollständig geöffnet oder geschlossen ist, bevor er verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="964d8-126">`AwaitTransitionAsync()` can be used to be sure an indicator is fully opened or closed before using it.</span></span>

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
