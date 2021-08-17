---
title: Holographic Remoting-Player
description: Erfahren Sie mehr über den Holographic Remoting Player und das Streamen holografischer Inhalte von einem PC HoloLens in Echtzeit über WLAN.
author: florianbagarmicrosoft
ms.author: v-vtieto
ms.date: 07/30/2021
ms.topic: article
keywords: HoloLens, Remoting, Holographic Remoting, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Diagnose, Leistung
ms.openlocfilehash: c5574017c33379248f4bf412cb5b046fdf309d72
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184661"
---
# <a name="holographic-remoting-player"></a>Holographic Remoting-Player

>[!TIP]
>[Erlernen der Grundlagen von Holographic Remoting.](holographic-remoting-overview.md)

>[!IMPORTANT]
>Holographic Remoting für HoloLens 2 ist eine wichtige Versionsänderung. [Remoteanwendungen für **HoloLens (1. Generation)**](add-holographic-remoting.md) müssen NuGet-Paketversion **1.x.x und** Remoteanwendungen für [ **HoloLens 2**](holographic-remoting-create-remote-wmr.md) **2.x.x verwenden.** Dies bedeutet, dass Remoteanwendungen, die für HoloLens 2 geschrieben wurden, nicht mit HoloLens (1. Generation) und umgekehrt kompatibel sind.

Der [Holographic Remoting Player](https://www.microsoft.com/p/holographic-remoting-player/9nblggh4sv40) ist eine Begleit-App, die eine Verbindung mit PC-Apps und -Spielen herstellt, die Holographic Remoting unterstützen. Der Player ist sowohl für HoloLens (erste Generation) als auch für HoloLens 2.  PC-Apps, die Holographic Remoting mit HoloLens unterstützt haben, müssen aktualisiert werden, um Holographic Remoting mit HoloLens 2. Wenden Sie sich an Ihren App-Anbieter, wenn Sie Fragen zu den unterstützten Versionen haben.

>[!TIP]
>Ab Version [2.2.0](holographic-remoting-version-history.md#v2.2.0) ist der Holographic Remoting-Player auch für Windows PCs verfügbar, auf denen [Windows Mixed Reality.](../../discover/navigating-the-windows-mixed-reality-home.md)

>[!TIP]
>Ab Version [2.4.0](holographic-remoting-version-history.md#v2.4.0) können Remote-Apps mit der [OpenXR-API](../native/openxr.md) erstellt werden. Informationen zu den ersten Schritte finden Sie [unter Writing a Holographic Remoting remote app using OpenXR APIs (Schreiben einer Holographic Remoting-Remote-App mithilfe von OpenXR-APIs).](holographic-remoting-create-remote-openxr.md)

## <a name="connecting-to-the-holographic-remoting-player"></a>Herstellen einer Verbindung mit dem Holographic Remoting Player

Befolgen Sie die Anweisungen Ihrer App, um eine Verbindung mit dem Holographic Remoting Player herzustellen. Sie müssen die IP-Adresse Ihres HoloLens-Geräts wie folgt eingeben, die Sie auf dem Hauptbildschirm des Remoting-Players sehen können:

![Holographic Remoting-Player](images/holographicremotingplayer.png)

Wenn der Hauptbildschirm angezeigt wird, wissen Sie, dass keine App verbunden ist.

Die holografische Remotingverbindung ist **nicht verschlüsselt.** Sie sollten Holographic Remoting immer über eine sichere Wi-Fi verbindung verwenden, der Sie vertrauen.

## <a name="quality-and-performance"></a>Qualität und Leistung

Die Qualität und Leistung Ihrer Erfahrung variiert basierend auf drei Faktoren:
* **Die holografische Erfahrung, die Sie** ausführen: Apps, die hochauflösende oder hochgradig detaillierte Inhalte rendern, erfordern möglicherweise einen schnelleren PC oder eine schnellere Drahtlosverbindung.
* **Hardware Ihres PCs:** Ihr PC muss mit 60 Frames pro Sekunde ausgeführt und codiert werden können. Für eine Grafikkarte empfehlen wir in der Regel geForce GTX 970 oder AMD Amd R9 290 oder besser. Auch hier ist möglicherweise eine Karte mit einem höheren oder niedrigeren Ende erforderlich.
* **Ihre Wi-Fi verbindung:** Ihr holografisches Erlebnis wird über WLAN gestreamt. Verwenden Sie ein schnelles Netzwerk mit geringer Überlastung, um die Qualität zu maximieren. Die Verwendung eines PCs, der über ein Ethernet-Kabel anstelle von WLAN verbunden ist, kann auch die Qualität verbessern.

## <a name="diagnostics"></a>Diagnose

Um die Qualität Ihrer Verbindung zu messen, sagen **Sie "Diagnose aktivieren"** auf dem Hauptbildschirm des Holographic Remoting Player. Wenn die Diagnose aktiviert ist, **HoloLens (erste Generation)** die App Ihnen:

* **FPS:** Die durchschnittliche Anzahl gerenderter Frames, die der Remoting-Player pro Sekunde empfängt und rendert. Das Ideal ist 60 FPS.
* **Latenz:** Die durchschnittliche Zeit, die ein Frame benötigt, um von Ihrem PC zum computerbasierten HoloLens. Desto niedriger, desto besser. Dies hängt größtenteils von Ihrem Wi-Fi ab.

Auf **HoloLens 2** zeigt die App Ihnen:

![Holographic Remoting Player-Diagnose](images/holographicremotingplayer-diag.png)

* **Rendern:** Die Anzahl der Frames, die der Remoting-Player in der letzten Sekunde gerendert hat. Beachten Sie, dass dies unabhängig von der Anzahl der Frames ist, die über das Netzwerk eingetroffen sind (siehe **Videoframes**). Die durchschnittliche/maximale Renderingdeltazeit in Millisekunden über die letzte Sekunde zwischen gerenderten Frames wird angezeigt.

* **Videoframes:** Die erste angezeigte Zahl besteht aus übersprungenen Videoframes, die zweite sind wiederverwendete Videoframes, und die dritte wird als Videoframes empfangen. Alle Zahlen stellen die Anzahl über die letzte Sekunde dar.
    * ```Received frames``` ist die Anzahl der Videoframes, die in der letzten Sekunde eingetroffen sind. Unter normalen Bedingungen sollte dies 60 sein, aber wenn dies nicht der Fall ist, ist dies ein Hinweis darauf, dass beide Frames aufgrund von Netzwerkproblemen gelöscht werden oder dass die Remote-/Remoteseite keine Frames mit der erwarteten Rate erzeugt.
    * ```Reused frames``` ist die Anzahl von Videoframes, die in der letzten Sekunde mehr als einmal verwendet wurden. Wenn Videoframes beispielsweise zu spät eintreffen, rendert die Renderingschleife  des Players weiterhin einen Frame, muss jedoch den Videoframe wiederverwenden, den er bereits für den vorherigen Frame verwendet hat.
    * ```Skipped frames``` ist die Anzahl der Videoframes, die nicht von der Renderingschleife des Players verwendet wurden. Netzwerk-Jitter kann z. B. dazu kommen, dass videoframes, die eintreffen, nicht mehr gleichmäßig verteilt werden. Wenn einige beispielsweise zu spät sind und andere rechtzeitig eintreffen, haben sie kein Delta von 16,66 Millisekunden mehr, wenn sie mit 60 Hz ausgeführt werden. Es kann vorkommen, dass mehr als ein Frame zwischen zwei Ticks der Renderschleife des Players eintrifft. In diesem Fall überspringt *der* Player einen oder mehrere Frames, da er immer den zuletzt empfangenen Videoframe anzeigen soll.

    >[!NOTE]
    >Bei Netzwerk-Jitter sind übersprungene und wiederverwendete Frames in der Regel ungefähr gleich. Wenn ihnen dagegen nur übersprungene Frames angezeigt werden, ist dies ein Indikator dafür, dass der Player die Zielbildrate nicht erreicht. In diesem Fall sollten Sie die maximale Renderingdeltazeit beim Diagnostizieren von Problemen im Auge behalten.

* **Videoframedelta:** Das minimale/maximale Delta zwischen empfangenen Videoframes in der letzten Sekunde. Diese Zahl korreliert in der Regel mit übersprungenen/wiederverwendeten Frames, falls Probleme durch Netzwerk-Jitter verursacht werden.
* **Latenz:** Die durchschnittliche Bearbeitung in Millisekunden in der letzten Sekunde. Die Verarbeitung in diesem Kontext bedeutet die Zeit vom Senden von Posen-/Sensordaten vom HoloLens an die Remote-/Remoteseite bis zur Anzeige des Videoframes für diese Posen-/Telemetriedaten auf HoloLens Anzeige.
* **Verworfene Videoframes:** Die Anzahl der verworfenen Videoframes in der letzten Sekunde und seit dem Herstellen einer Verbindung. Die Hauptursache für verworfene Videoframes ist, wenn ein Videoframe nicht in der Reihenfolge eintrifft und aus diesem Grund verworfen werden muss, da bereits ein neuerer Videoframe vorhanden ist. Dies ähnelt *verworfenen Frames,* aber die Ursache liegt auf einer niedrigeren Ebene im Remotingstapel. Verworfene Videoframes werden nur unter schlechten Netzwerkbedingungen erwartet.

Auf dem Hauptbildschirm können Sie "Diagnose **deaktivieren" sagen, um** die Diagnose zu deaktivieren.

## <a name="pc-system-requirements"></a>PC-Systemanforderungen
* Auf Ihrem **PC muss** das Windows 10 Anniversary Update oder neuer ausgeführt werden.
* Es wird empfohlen, eine GeForce GTX 970- oder AMD Amd R9 290 oder eine bessere Grafikkarte zu verwenden.
* Es wird empfohlen, ihren PC über Ethernet mit Ihrem Netzwerk zu verbinden, um die Anzahl von Funkhops zu reduzieren.

## <a name="see-also"></a>Weitere Informationen
* [Übersicht über Holographic Remoting](holographic-remoting-overview.md)
* [HoloLens (erste Generation): Holographic Remoting hinzufügen](add-holographic-remoting.md)
* [Schreiben einer Holographic Remoting-Remote-App mithilfe Windows Mixed Reality APIs](holographic-remoting-create-remote-wmr.md)
* [Schreiben einer Holographic Remoting-Remote-App mit OpenXR-APIs](holographic-remoting-create-remote-openxr.md)
* [Holographic Remoting-Software – Lizenzbedingungen](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Datenschutzerklärung von Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)