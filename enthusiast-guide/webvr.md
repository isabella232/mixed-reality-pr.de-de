---
title: Verwenden von webvr mit gemischter Windows-Realität
description: Beschreibt webvr und erläutert, wie Sie mit Microsoft Edge auf Windows Mixed Reality-Headsets verwendet werden.
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, Mr, webvr, Edge, Microsoft Edge, Webbrowser
ms.openlocfilehash: e57ad060a1a539e90631d1b9f1808d1e8466e669
ms.sourcegitcommit: 5eb27475f8616c9d4f95b4b386a5bd0d22f41125
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "92174342"
---
# <a name="using-webvr-with-windows-mixed-reality"></a>Verwenden von webvr mit gemischter Windows-Realität

>[!IMPORTANT] 
>Die meisten modernen Webbrowser haben die Unterstützung von webvr zugunsten von webxr, dem neuen Standard zum Erstellen von immersiven Webumgebungen für VR-Headsets, als veraltet markiert. Installieren Sie [den neuen Microsoft Edge](using-microsoft-edge.md) für webxr-Support.

## <a name="what-is-webvr"></a>Was ist WebVR?

[Webvr](https://webvr.info) ist eine offene Spezifikation, die es ermöglicht, VR in Ihrem Browser zu erleben. Wenn eine Website die webvr-Unterstützung implementiert und 3D-Inhalte bereitstellt, können Sie mit der Zustimmung des Benutzers immersive Inhalte im Headset anzeigen.

## <a name="what-is-the-difference-between-webvr-and-browsing-the-web-in-vr"></a>Worin besteht der Unterschied zwischen webvr und dem Durchsuchen des Internets in VR?

Webvr ist eine Technologie, die es einem Website Autor ermöglicht, eine VR-Funktionalität zu einer Seite hinzuzufügen. Die webvr-API wird von einer Seite verwendet, um 3D-Inhalte (z. b. 360-Grad-Video oder 3D-Modell oder 3D-Spiel) mit dem gesamten Headset anzuzeigen. **Beispiel:** Anzeigen eines 360-Videos auf [CNN.com/VR](http://cnn.com/vr). Wenn eine Seite webvr unterstützt, wird eine Schaltfläche oder ein anderes UI-Element hinzugefügt, auf das Sie klicken können, um VR einzugeben.

Das Durchsuchen des Internets in VR bedeutet, dass Sie den Edge-Browser verwenden, während Sie Ihr Headset verwenden, als 2D-App-Slate innerhalb von cliffhouse.

## <a name="do-all-websites-support-webvr"></a>Unterstützen alle Websites webvr?

Nein. Website Autoren müssen sich für die Verwendung von webvr entscheiden. Außerdem können Sie Websites erstellen, die für bestimmte Browser, Headsets und Controller optimiert sind. Einige webvr-Inhalte sind z. b. nur für Mobile VR-Geräte optimiert. Beachten Sie auch, dass Websites den webvr-Inhalt explizit erstellen und bereitstellen müssen. Die Anzahl von Standorten, an denen einige webvr-kompatible Inhalte vorhanden sind, wächst jeden Tag.

## <a name="can-i-use-my-viveoculus-etc-to-view-webvr-content-in-microsoft-edge"></a>Kann ich mit "Vive/Oculus" usw. webvr-Inhalte in Microsoft Edge anzeigen?

Nein. Sie müssen ein Windows Mixed Reality-Headset verwenden, um webvr in Edge zu verwenden. Allerdings können Sie in einem anderen Browser auf webvr-Inhalte zugreifen. eine komplette Liste der kompatiblen Geräte und Browser finden Sie unter: [webvr. Rocks](http://webvr.rocks/).

## <a name="where-can-i-find-the-webvr-developer-documentation"></a>Wo finde ich die webvr-Entwicklerdokumentation?

Die Entwicklerdokumentation finden Sie hier: [webvr-Entwicklerdokumentation](https://docs.microsoft.com/microsoft-edge/webvr/).

## <a name="ive-found-a-website-with-webvr-that-doesnt-work-in-windows-mixed-reality-what-do-i-do"></a>Ich habe eine Website mit webvr gefunden, die in Windows Mixed Reality nicht funktioniert. Wie gehe ich vor?

Sie können fehlerhafte Websites direkt an das Microsoft Edge-Browser Team in der [Problem](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/)Verfolgung oder per Twitter über [#EdgeBug hashtag](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/)Berichten.

Fehler können auch mithilfe der Windows-Feedback-Hub-App Unterkategorie protokolliert werden:

Probleme mit der Microsoft Edge->-Website

## <a name="what-is-a-good-page-to-test-if-webvr-is-working"></a>Was ist eine gute Seite, um zu testen, ob webvr funktioniert?

Siehe [webvr.info Samples](http://webvr.info/samples/XX-vr-controllers.html).

## <a name="how-do-i-set-up-webvr"></a>Gewusst wie webvr einrichten?

Um webvr-Inhalte auf einem Windows Mixed Reality-Headset (mit Hardware oder Simulation) zu erleben, müssen Sie folgende Schritte ausführen:
1. Stellen Sie sicher, dass Ihr Headset angeschlossen ist.
2. Starten Sie Microsoft Edge entweder auf dem Desktop oder in gemischter Realität.
3. Navigieren Sie zu einer webvr-aktivierten Seite.
4. Klicken Sie auf der Seite auf die Schaltfläche Enter VR eingeben (der Speicherort und die visuelle Darstellung dieser Schaltfläche können je nach Website variieren). Dies könnte etwa wie folgt aussehen: \
   ![VR-Brillen Bild](images/75px-enter-vr.png)
5. Wenn Sie zum ersten Mal versuchen, VR in eine bestimmte Domäne einzugeben, fordert der Browser die Zustimmung zur Verwendung der immersiven Ansicht an. Klicken Sie dann auf Ja: ![Benutzeroberfläche für Zustimmung, die beim ersten Versuch angezeigt wird, VR in eine bestimmte Domäne einzugeben](images/1053px-Webvr-consent-ui.png)
6. Ihr Headset sollte mit dem Anzeigen der webvr-Inhalte beginnen.


## <a name="see-also"></a>Weitere Informationen

* [Problembehandlung > webvr](webvr-questions.md)
* [Vorgehensweise beim Einstieg in Ihre erste webvr-Benutzer Darstellung](using-games-and-apps-in-windows-mixed-reality.md#how-to-get-into-your-first-webvr-experience)
* [Verwenden von spielen und apps in Windows Mixed Reality](using-games-and-apps-in-windows-mixed-reality.md)
* [Ihre gemischte Reality-Startseite](your-mixed-reality-home.md)
* [Überwachungs System](tracking-system.md)
* [Motion-Controller](controllers-in-wmr.md)
* [SteamVR](using-steamvr-with-windows-mixed-reality.md)
* [Einreichen von Feedback](filing-feedback.md)
