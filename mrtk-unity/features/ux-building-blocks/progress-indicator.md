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
# <a name="progress-indicators"></a>Statusindikatoren

![Statusindikatoren](../images/progress-indicator/MRTK_ProgressIndicator_Main.png)

## <a name="example-scene"></a>Beispielszene

Beispiele für die Verwendung von Fortschrittsindikatoren finden Sie in der `ProgressIndicatorExamples` Szene. In dieser Szene werden alle im SDK enthaltenen Statusindikator-Prefabs veranschaulicht. Außerdem wird veranschaulicht, wie Fortschrittsindikatoren in Verbindung mit einigen gängigen asynchronen Aufgaben wie dem Laden von Szenen verwendet werden.

<img src="../images/progress-indicator/MRTK_ProgressIndicator_Examples.png" alt="Progress Indicator Examples 1">

## <a name="example-open-update--close-a-progress-indicator"></a>Beispiel: Öffnen, Aktualisieren & Schließen einer Statusanzeige

Statusindikatoren implementieren die [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) -Schnittstelle. Diese Schnittstelle kann mithilfe von aus einem GameObject abgerufen `GetComponent` werden.

```c#
[SerializedField]
private GameObject indicatorObject;
private IProgressIndicator indicator;

private void Start()
{
    indicator = indicatorObject.GetComponent<IProgressIndicator>();
}
```

Die `IProgressIndicator.OpenAsync()` Methoden und geben Tasks `IProgressIndicator.CloseAsync()` [zurück.](xref:System.Threading.Tasks.Task) Es wird empfohlen, auf diese Aufgaben in einer asynchronen Methode zu warten.

Die Standard-Statusanzeige-Prefabs des MRTK sollten inaktiv sein, wenn sie in einer Szene platziert werden. Wenn ihre `IProgressIndicator.OpenAsync()` Methoden aufgerufen werden, aktivieren und deaktivieren die Statusindikatoren ihre Gameobjects automatisch. (Dieses Muster ist keine Anforderung der IProgressIndicator-Schnittstelle.)

Legen Sie die -Eigenschaft `Progress` des Indikators auf einen Wert zwischen 0 und 1 fest, um den angezeigten Status zu aktualisieren. Legen Sie die `Message` -Eigenschaft fest, um die angezeigte Meldung zu aktualisieren. Dieser Inhalt kann in verschiedenen Implementierungen auf unterschiedliche Weise angezeigt werden.

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

## <a name="indicator-states"></a>Indikatorzustände

Die -Eigenschaft eines `State` Indikators bestimmt, welche Vorgänge gültig sind. Wenn Sie eine ungültige Methode aufrufen, wird der Indikator in der Regel einen Fehler melden und keine Aktion ergreifen.

Zustand | Gültige Vorgänge
--- | ---
`ProgressIndicatorState.Opening` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Open` | `CloseAsync()`
`ProgressIndicatorState.Closing` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Closed` | `OpenAsync()`

`AwaitTransitionAsync()` kann verwendet werden, um sicherzustellen, dass ein Indikator vollständig geöffnet oder geschlossen ist, bevor er verwendet wird.

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
