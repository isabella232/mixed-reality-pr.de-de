---
title: Startgeste
description: Erfahren Sie, wie Sie die Startgeste verwenden, um das Startmenü auf HoloLens und Windows Mixed Reality immersiven Headsets aufzurufen.
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: Mixed Reality, Gesten, Interaktion, Design, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit, Bloom
ms.openlocfilehash: f3ad9309c7232f20a25060b1d98d7374272ceea00f24be18d7263b8ec7002fb3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213740"
---
# <a name="start-gesture"></a>Startgeste

Die Startgeste ist eine Handgeste, die zum Aufrufen des Startmenüs verwendet wird. Dies entspricht dem Drücken der Windows-Taste auf Tastaturen, der Xbox-Taste auf Xbox-Controllern oder der Windows-Taste auf immersiven Headset-Motion-Controllern. Achten Sie besonders auf reservierte Systemgesten auf jedem Mixed Reality Gerät, um Konflikte beim Entwerfen von Interaktionen zu vermeiden.

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
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1. Generation)</strong></a></td>
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
        <td>Handflächenschaltfläche</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
    <tr>
        <td>Anvisieren mit den Augen und Anheften der Handfläche</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a>Blüte

Wir haben "Bloom" entwickelt, um das Startmenü in HoloLens (1. Generation) zu öffnen. Dabei handelt es sich um eine symbolische Geste, die eine Blume imitiert. Sie ist einzigartig für eine sichere Interaktion, einfache Verwendung und schnelle Rückrufe. Um die Geste zu verwenden, halten Sie ihre Hand mit der Handfläche und den Fingerspitzen zusammen, und öffnen Sie ihre Hand, indem Sie ihre Finger verteilen.

:::row:::
    :::column:::
        ![Bloom close](images/bloom-close.png)<br>
        **Schritt 1: Handfläche nach oben mit fingertips together**<br>
    :::column-end:::
    :::column:::
        ![Bloom open](images/bloom-open.png)<br>
        **Schritt 2: Handfläche nach oben mit fingertips spread**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="start-gesture"></a>Startgeste

In HoloLens 2 haben wir die Geste "Bloom" durch eine virtuelle Handschaltfläche ersetzt, die für Benutzer instinktiver ist. Indem sie Benutzern die Schaltfläche auf dem Handband zeigen, können sie intuitiv auf die Hand stoßen und sie mit der anderen Hand drücken.

:::row:::
    :::column:::
        ![Handschaltfläche bereit](images/wrist-button-ready.png)<br>
        **Schritt 1: Handfläche nach oben, um die Handfläche anzuzeigen**<br>
    :::column-end:::
    :::column:::
        ![Schaltfläche "Handdruck" drücken](images/wrist-button-press.png)<br>
        **Schritt 2: Drücken der Handfläche**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="one-handed-start-gesture"></a>Einhändige Startgeste

> [!IMPORTANT]
> Voraussetzungen, damit die einhändige Startgeste funktioniert:
>
> 1. Sie müssen auf das Update vom November 2019 (Build 18363.1039) oder höher aktualisieren.
> 1. Ihre Augen müssen auf dem Gerät kalibriert sein, damit die Blickverfolgung ordnungsgemäß funktioniert. Wenn Sie beim Betrachten des Startsymbols keine umlaufenden Punkte sehen, sind Ihre Augen nicht für das Gerät kalibriert.

Sie können die Startgeste auch nur mit einer Hand verwenden. Halten Sie Ihre Hand mit der Hand, und sehen Sie sich das **Startsymbol** auf Ihrem inneren Handband an. **Während Sie das Symbol im Auge behalten**, führen Sie Daumen und Zeigefinger zusammen.<br>
:::row:::
    :::column:::
        ![Handschaltfläche bereit](images/wrist-button-ready.png)<br>
        **Schritt 1: Handfläche nach oben, um die Handfläche anzuzeigen**<br>
    :::column-end:::
    :::column:::
        ![Handdruckknöpfe](images/wrist-button-pinch.png)<br>
        **Schritt 2: Anvisieren mit den Augen auf die Schaltfläche und anschließendes Drücken**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a>Siehe auch

* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Anväuten mit den Augen](eye-tracking.md)
* [Spracheingabe](voice-input.md)