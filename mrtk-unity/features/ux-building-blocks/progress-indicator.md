---
title: Statusanzeige
description: Übersicht über den Fortschrittsindikator im MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: b5147e5c592b80ab100a7cf7ce2487d971299832fec11f7ca57b1fdeef530900
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202586"
---
# <a name="progress-indicator"></a>Statusanzeige

![Statusindikatoren](../images/progress-indicator/MRTK_ProgressIndicator_Main.png)

## <a name="example-scene"></a>Beispielszene

Beispiele für die Verwendung von Statusindikatoren finden Sie in der `ProgressIndicatorExamples` Szene. Diese Szene veranschaulicht die einzelnen Prefabs der Statusanzeige, die im SDK enthalten sind. Außerdem wird veranschaulicht, wie Statusindikatoren in Verbindung mit einigen häufigen asynchronen Aufgaben wie dem Laden von Szenen verwendet werden.

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

Die `IProgressIndicator.OpenAsync()` Methoden und geben `IProgressIndicator.CloseAsync()` [Tasks](xref:System.Threading.Tasks.Task)zurück. Es wird empfohlen, auf diese Aufgaben in einer asynchronen Methode zu warten.

Die Standardpräfabs der MRTK-Statusanzeige sollten inaktiv sein, wenn sie in einer Szene platziert werden. Wenn ihre `IProgressIndicator.OpenAsync()` Methoden aufgerufen werden, werden die Statusindikatoren automatisch aktiviert und deaktiviert. (Dieses Muster ist keine Anforderung der IProgressIndicator-Schnittstelle.)

Legen Sie die -Eigenschaft des Indikators `Progress` auf einen Wert zwischen 0 und 1 fest, um den angezeigten Fortschritt zu aktualisieren. Legen Sie die `Message` -Eigenschaft fest, um die angezeigte Meldung zu aktualisieren. Unterschiedliche Implementierungen können diesen Inhalt auf unterschiedliche Weise anzeigen.

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

Die -Eigenschaft eines Indikators `State` bestimmt, welche Vorgänge gültig sind. Das Aufrufen einer ungültigen Methode bewirkt in der Regel, dass der Indikator einen Fehler meldet und keine Aktion vornimmt.

State | Gültige Vorgänge
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
