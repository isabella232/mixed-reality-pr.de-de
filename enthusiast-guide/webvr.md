---
title: Verwenden von WebVR mit Windows Mixed Reality
description: Erfahren Sie mehr über die Grundlagen von WebVR, die Verwendung mit Microsoft Edge auf Windows Mixed Reality Headsets und häufige Problembehandlung.
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, WebVR, Edge, Microsoft Edge, Webbrowsen
ms.openlocfilehash: f61fff3c8d5083236c10d79d3824c489111f8d2be2138984f5613f295849bdf2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214124"
---
# <a name="using-webvr-with-windows-mixed-reality"></a>Verwenden von WebVR mit Windows Mixed Reality

>[!IMPORTANT]
>Die meisten modernen Webbrowser haben die Unterstützung von WebVR zugunsten von WebXR eingestellt, dem neuen Standard für die Erstellung immersiver Weberfahrungen für VR-Headsets. Installieren Sie [die neue Microsoft Edge](using-microsoft-edge.md) für die WebXR-Unterstützung.

## <a name="what-is-webvr"></a>Was ist WebVR?

[WebVR](https://webvr.info) ist eine offene Spezifikation, mit der Sie VR direkt in einem Browser erleben können. Wenn eine Website WebVR-Unterstützung implementiert und 3D-Inhalte bereitstellt, kann sie mit Zustimmung des Benutzers immersive Inhalte im Headset anzeigen.

## <a name="what-is-the-difference-between-webvr-and-browsing-the-web-in-vr"></a>Was ist der Unterschied zwischen WebVR und dem Durchsuchen des Webs in VR?

WebVR ist eine Technologie, die es einem Websiteautor ermöglicht, einer Seite VR-Funktionen hinzuzufügen. Die WebVR-API wird von einer Seite verwendet, um 3D-Inhalte (z. B. 360-Grad-Video, ein 3D-Modell oder ein 3D-Spiel) für das gesamte Headset anzuzeigen. **Beispiel:** Anzeigen eines 360-Videos auf [cnn.com/vr](http://cnn.com/vr). Wenn eine Seite WebVR unterstützt, wird eine Schaltfläche oder ein anderes Benutzeroberflächenelement hinzugefügt, das Sie auswählen können, um VR einzugeben.

Das Durchsuchen des Webs in VR bedeutet, dass Sie den Edge-Browser verwenden, während Sie Ihr Headset als 2D-App-Slate imHouse verwenden.

## <a name="do-all-websites-support-webvr"></a>WebVR wird von allen Websites unterstützt.

Nein. Websiteautoren müssen sich für die Verwendung von WebVR entscheiden und können optimierte Websites für bestimmte Browser, Headsets und Controller erstellen. Einige WebVR-Inhalte sind nur für mobile VR-Geräte optimiert. Beachten Sie außerdem, dass Websites WebVR-Inhalte explizit erstellen und bereitstellen müssen. Die Anzahl der Websites mit webVR-kompatiblen Inhalten nimmt täglich zu.

## <a name="can-i-use-my-viveoculus-etc-to-view-webvr-content-in-microsoft-edge"></a>Kann ich meine Vive/Oculus usw. verwenden, um WebVR-Inhalte in Microsoft Edge

Nein. Für die Verwendung von WebVR in Edge ist ein Windows Mixed Reality Headset erforderlich. Sie können jedoch in einem anderen Browser auf WebVR-Inhalte zugreifen. Die vollständige Liste der kompatiblen Geräte und Browser finden Sie unter: [WebVR.rocks](http://webvr.rocks/).

## <a name="where-can-i-find-the-webvr-developer-documentation"></a>Wo finde ich die WebVR-Entwicklerdokumentation?

Die Entwicklerdokumentation finden Sie hier: [WebVR-Entwicklerdokumentation.](/microsoft-edge/webvr/)

## <a name="ive-found-a-website-with-webvr-that-doesnt-work-in-windows-mixed-reality-what-do-i-do"></a>Ich habe eine Website mit WebVR gefunden, die in Windows Mixed Reality nicht funktioniert. Was soll ich tun

Sie können fehlerhafte Websites direkt an das Microsoft Edge Browserteam in der [Problemverfolgung](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/)oder über Twitter melden, indem [Sie #EdgeBug Hashtag verwenden.](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/)

Sie können Fehler auch mithilfe der Windows-Feedback-Hub-App in der Kategorie protokollieren:

Probleme mit Microsoft Edge ->-Website

## <a name="what-is-a-good-page-to-test-if-webvr-is-working"></a>Was ist eine gute Seite zum Testen, ob WebVR funktioniert?

Siehe [webvr.info Beispiele.](http://webvr.info/samples/XX-vr-controllers.html)

## <a name="how-do-i-set-up-webvr"></a>Gewusst wie Einrichten von WebVR

Um WebVR-Inhalte auf einem Windows Mixed Reality Headset (mit Hardware oder Simulation) zu erleben, müssen Sie:

1. Stellen Sie sicher, dass Ihr Headset verbunden ist.
2. Starten Sie Microsoft Edge entweder auf dem Desktop oder innerhalb Mixed Reality.
3. Navigieren Sie zu einer WebVR-fähigen Seite.
4. Wählen Sie auf der Seite die Schaltfläche VR eingeben aus (die Position und die visuelle Darstellung dieser Schaltfläche können je nach Website variieren). Dies kann in etwa wie hier aussehen:
   ![VR Goggles-Bild](images/75px-enter-vr.png)
5. Wenn Sie zum ersten Mal versuchen, VR in einer bestimmten Domäne einzugeben, fordert der Browser die Zustimmung zur Verwendung der immersiven Ansicht an. Wählen Sie Ja aus: ![Zustimmungs-Benutzeroberfläche, die beim ersten Versuch angezeigt wird, VR für eine bestimmte Domäne einzugeben](images/1053px-Webvr-consent-ui.png)
6. Ihr Headset sollte mit der Anzeige des WebVR-Inhalts beginnen.

## <a name="see-also"></a>Siehe auch

* [Problembehandlung für > WebVR](webvr-questions.md)
* [Erste WebVR-Erfahrung](using-games-and-apps-in-windows-mixed-reality.md#how-to-get-into-your-first-webvr-experience)
* [Verwenden von Spielen und Apps in Windows Mixed Reality](using-games-and-apps-in-windows-mixed-reality.md)
* [Ihre Mixed Reality Home](your-mixed-reality-home.md)
* [Nachverfolgungssystem](tracking-system.md)
* [Motion Controllers](controllers-in-wmr.md)
* [SteamVR](using-steamvr-with-windows-mixed-reality.md)
* [Senden von Feedback](filing-feedback.md)