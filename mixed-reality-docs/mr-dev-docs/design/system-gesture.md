---
title: Start Geste
description: Erfahren Sie, wie Sie mit der Start Bewegung das Startmenü auf hololens und in Windows Mixed Reality-immersiven Headsets aufzurufen.
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: Gemischte Realität, Gesten, Interaktion, Entwurf, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens, mrtk, Mixed Reality Toolkit, Bloom
ms.openlocfilehash: 9e29d483375db103cebc30be9117e40899a9f81f
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009430"
---
# <a name="start-gesture"></a>Start Geste

Die Start Geste ist eine Handbewegung, mit der das Startmenü aufgerufen wird. Dies entspricht dem Drücken der Windows-Taste auf den Tastaturen, der Xbox-Schaltfläche auf Xbox-Controllern oder der Windows-Schaltfläche auf immersiven Headset-Motion-Controllern. Achten Sie besonders auf die Gesten der reservierten Systeme auf jedem gemischten Reality-Gerät, um Konflikte beim Entwerfen von Interaktionen zu vermeiden.

## <a name="device-support"></a>Geräteunterstützung

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Feature</strong></td>
        <td><a href="../hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
    </tr>
     <tr>
        <td>Blüte</td>
        <td>✔️</td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td>Handgelenk Taste</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
    <tr>
        <td>Eye-und Palmen Pfeil nach oben</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a>Blüte

Wir haben "Bloom" entworfen, um das Startmenü in hololens (1st Gen) aufzurufen. Dies ist eine symbolische Geste, die eine Blüten Blüte imitiert. Es ist eine besondere Interaktion, eine einfache Verwendung und eine schnelle Erinnerung. Wenn Sie die Geste verwenden möchten, halten Sie Ihre Hand an Ihre Hand, um die Hand zu öffnen, und öffnen Sie dann die Hand, indem Sie Ihre Finger verteilen.

:::row:::
    :::column:::
        ![Schließen der Blüte](images/bloom-close.png)<br>
        **Schritt 1: überschreiten der Hand.**<br>
    :::column-end:::
    :::column:::
        ![Geöffnet, geöffnet](images/bloom-open.png)<br>
        **Schritt 2: überschreiten der handbreiten Verteilung**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="start-gesture"></a>Start Geste

In hololens 2 wurde die Blüte Bewegung durch eine virtuelle Handgelenk Schaltfläche ersetzt, die für Benutzer besser instanzieller ist. Wenn die Benutzer die Schaltfläche auf dem Handgelenk anzeigt, können Sie sie intuitiv erreichen und mit der anderen Seite drücken.

:::row:::
    :::column:::
        ![Handgelenk Taste](images/wrist-button-ready.png)<br>
        **Schritt 1: Palme zum Anzeigen der Schaltfläche "Handgelenk"**<br>
    :::column-end:::
    :::column:::
        ![Handgelenk Taste drücken](images/wrist-button-press.png)<br>
        **Schritt 2: Klicken Sie auf das Handgelenk.**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="one-handed-start-gesture"></a>Einstufige Start Geste

> [!IMPORTANT]
> Damit die einstufige Start Geste funktioniert:
>
> 1. Sie müssen ein Update auf das Update von November 2019 (Build 18363,1039) oder höher durch haben.
> 1. Die Augen müssen auf dem Gerät so kalibriert werden, dass die Eye-Nachverfolgung ordnungsgemäß funktioniert. Wenn Sie keine Umkreis Punkte um das Start Symbol sehen, wenn Sie es betrachten, werden die Augen nicht auf dem Gerät gekalibriert.

Sie können auch die Start Geste nur mit einer Hand verwenden. Halten Sie Ihre Hand mit Ihrer Hand, und sehen Sie sich das **Start Symbol** auf Ihrem inneren Handgelenk an. **Wenn Sie das Symbol gedrückt halten**, können Sie den Ziehpunkt und den Finger des Indexes zusammenhalten.<br>
:::row:::
    :::column:::
        ![Handgelenk Taste](images/wrist-button-ready.png)<br>
        **Schritt 1: Palme zum Anzeigen der Schaltfläche "Handgelenk"**<br>
    :::column-end:::
    :::column:::
        ![Handgelenk Schaltfläche](images/wrist-button-pinch.png)<br>
        **Schritt 2: Augenblick auf die Schaltfläche und dann auf die Schaltfläche**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a>Siehe auch

* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Augenblick](eye-tracking.md)
* [Spracheingabe](voice-input.md)
